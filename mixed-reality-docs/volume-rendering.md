---
title: 卷渲染
description: 容量耗尽映像包含丰富的信息, 这些信息具有不透明度和颜色在整个卷中, 无法轻松地表示为表面。 了解如何在 Windows Mixed Reality 内有效呈现容量耗尽映像。
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 容量耗尽映像, 卷渲染, 性能, 混合现实
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548639"
---
# <a name="volume-rendering"></a>卷渲染

对于医学 MRI 或工程量, 请参阅[维基百科上的卷渲染](https://en.wikipedia.org/wiki/Volume_rendering)。 这些 "容量耗尽 images" 包含丰富的信息, 其中包含在整个卷中不透明度和颜色的颜色, 无法轻松地表示为表面 (如[多边形网格](https://en.wikipedia.org/wiki/Polygon_mesh))。

用于提高性能的关键解决方案
1. DFX简单方法:显示整个卷, 通常运行速度太慢
2. 良好切割平面:仅显示卷的单个切片
3. 良好剪切子卷:只显示卷的几个层
4. 良好降低卷呈现的分辨率 (请参阅 "混合分辨率场景呈现")

只有一定数量的信息可从应用程序传输到屏幕的任何特定帧, 这是总内存带宽。 此外, 转换该数据以供演示所需的任何处理 (或 "底纹") 也需要时间。 执行卷渲染时的主要注意事项如下:
* 屏幕宽度 * 屏幕高度 * 屏幕上的屏幕计数 * 每帧的总容量-每帧样本数
* 1028 * 720 * 2 * 256 = 378961920 (100%)(完全 res 卷: 样本太多)
* 1028 * 720 * 2 * 1 = 1480320 (已满 0.3%) (瘦切片:每个像素1个采样, 顺利运行)
* 1028 * 720 * 2 * 10 = 14803200 (已满 3.9%) (子卷片:每个像素10个样本, 以相当平稳的速度运行, 看起来 3d)
* 200 * 200 * 2 * 256 = 20480000 (全部的 5%) (较小的分辨率量: 更少的像素, 整卷, 看起来是三维但有点 blury)

## <a name="representing-3d-textures"></a>表示三维纹理

在 CPU 上:

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

在 GPU 上:

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

## <a name="shading-and-gradients"></a>底纹和渐变

如何对音量 (如 MRI) 进行着色, 以便进行有用的可视化。 主要方法是在中具有要查看亮度的 "强度窗口" (最小值和最大值), 只需将其缩放到该空间即可查看黑色和白色强度。 然后, 可以将 "颜色斜坡" 应用于该范围内的值, 并将其存储为纹理, 以便强度密度的不同部分可以着色不同的颜色:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

在许多应用程序中, 我们在我们的应用程序中存储了原始强度值和 "分段索引" (用于划分外观和骨骼等不同部分, 这些段通常由专家在专用工具中创建)。 这可以与上述方法结合使用, 为每个段索引放置不同的颜色, 甚至不同的颜色斜坡:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>着色器中的卷切片

第一步是创建一个可在卷上移动的 "切片平面"、"切分它" 以及每个点的扫描值。 这假设有一个 "VolumeSpace" 多维数据集, 该多维数据集表示卷在世界空间中的位置, 可用作放置点的参考:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>着色中的卷跟踪

如何使用 GPU 进行子卷跟踪 (先走一些 voxels, 然后将数据从后到前面):

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

## <a name="whole-volume-rendering"></a>整个卷渲染

修改以上的子卷代码, 获取:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>混合分辨率场景呈现

如何以低分辨率渲染场景的一部分并将其放回原位:
1. 设置两个离线相机, 每个屏幕上都有一个用于更新每个帧的
2. 设置相机呈现到的两个低分辨率呈现器目标 (200x200 大小)
3. 设置在用户前移动的四个

每个帧:
1. 在低分辨率 (卷数据、昂贵的着色器等) 上绘制每个眼睛的渲染目标。
2. 通常将场景绘制为完整分辨率 (网格、UI 等)
3. 在用户面前, 在场景上绘制四个四核, 并在其上绘制低分辨率。
4. 结果: 包含低分辨率但高密度卷数据的完整分辨率元素的直观组合。
