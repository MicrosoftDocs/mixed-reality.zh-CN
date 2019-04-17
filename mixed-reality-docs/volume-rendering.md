---
title: 批量呈现
description: 容量耗尽映像包含丰富的信息与不透明度和整个的卷，不能轻松地表示为表面的颜色。 了解如何有效地呈现在 Windows Mixed Reality 容量耗尽图像。
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 容量耗尽映像、 卷呈现、 性能、 混合的现实
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592861"
---
# <a name="volume-rendering"></a>批量呈现

医疗 MRI 或工程卷，请参阅[Wikipedia 上的卷呈现](https://en.wikipedia.org/wiki/Volume_rendering)。 这些容量耗尽映像包含丰富的信息与不透明度和颜色的卷，无法轻松地表示为面如整个[多边形网格](https://en.wikipedia.org/wiki/Polygon_mesh)。

若要提高性能的关键解决方案
1. 错误：比较天真的方法：显示整个卷，通常运行速度太慢
2. 很好：切面：显示一个切片的数据量
3. 很好：剪切子卷：显示仅几个层的数据量
4. 很好：降低卷呈现的分辨率 （请参阅混合解析场景渲染）

一定数量的应用程序中对任何特定帧中的屏幕可以传输的信息，这是总内存带宽。 此外需要转换该数据以供演示文稿任何处理 （或明暗度） 也需要时间。 执行批量呈现时的主要注意事项是这种情况下：
* 屏幕宽度 * 屏幕高度 * 屏幕计数 * 卷的层上-，-像素 = 总-卷-示例-每个帧
* 1028 * 720 * 2 * 256 = 378961920 （100%)(完整 res 卷： 太多的示例)
* 1028 * 720 * 2 * 1 = 1480320 （完整的 0.3%) (精简切片：顺利运行每个像素，1 示例）
* 1028 * 720 * 2 * 10 = 14803200 （完整的 3.9%) (子卷切片：每个像素，10 个示例运行相当顺畅，看起来 3d）
* 200 * 200 * 2 * 256 = 20480000 （完整的 5%) (降低 res 卷： 较少的像素为单位，整卷，看起来 3d，但有些 blury)

## <a name="representing-3d-textures"></a>表示三维纹理

CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

在 GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>明暗度和渐变

如何添加有用的可视化效果的卷，如 MRI、 阴影。 主要方法是让明暗度窗口 （最小值和最大） 想要查看强度内，并只需扩展到该空间以查看黑色或白色的强度。 可应用于该范围内的值和存储为纹理，以便在强度范畴内形成的不同部分可以是不同的阴影的颜色色阶:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

在许多我们我们在原始的强度值和分段 index 我们卷中存储的应用程序 （如划分不同部分皮肤和骨骼，这些段通常由创建专用工具方面的专家）。 这可以将不同的颜色或甚至不同的颜色为每个段索引的负载增加，上述方法与组合：

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>在着色器中切片的卷

第一个重要步骤是创建"切片面"，可以浏览该卷，切片它，并扫描每个点处的值。 这假设没有 VolumeSpace 多维数据集，表示此卷将在世界空间中，可以用作引用放置点：

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>着色器中的卷跟踪

如何使用 GPU 进行子卷跟踪 （指导少量 voxels 深度然后层的数据从后向前）：

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>整个卷呈现

修改上面的子卷代码，我们得到：

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>混合的解析场景渲染

如何呈现场景中具有较低分辨率的一部分，并将其放回位置：
1. 设置两个屏外相机，另一个用于遵循更新每个帧每只眼睛
2. 安装程序两个较低分辨率呈现器目标 (例如大小为 200x200 每个)，照相机呈现到
3. 设置移动用户四核

每个帧：
1. 在较低分辨率绘制每只眼睛的呈现器目标 （卷数据、 昂贵的着色器等）
2. 绘制场景通常作为完整分辨率 （网格、 UI 等。）
3. 场景中，通过绘制四呈现给用户，并投影到的低分辨率的呈现。
4. 使用较低分辨率，但高密度卷数据的高分辨率元素的结果： visual 组合。
