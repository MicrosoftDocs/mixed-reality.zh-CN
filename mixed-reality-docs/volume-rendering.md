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
# <a name="volume-rendering"></a><span data-ttu-id="dd187-105">批量呈现</span><span class="sxs-lookup"><span data-stu-id="dd187-105">Volume rendering</span></span>

<span data-ttu-id="dd187-106">医疗 MRI 或工程卷，请参阅[Wikipedia 上的卷呈现](https://en.wikipedia.org/wiki/Volume_rendering)。</span><span class="sxs-lookup"><span data-stu-id="dd187-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="dd187-107">这些容量耗尽映像包含丰富的信息与不透明度和颜色的卷，无法轻松地表示为面如整个[多边形网格](https://en.wikipedia.org/wiki/Polygon_mesh)。</span><span class="sxs-lookup"><span data-stu-id="dd187-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="dd187-108">若要提高性能的关键解决方案</span><span class="sxs-lookup"><span data-stu-id="dd187-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="dd187-109">错误：比较天真的方法：显示整个卷，通常运行速度太慢</span><span class="sxs-lookup"><span data-stu-id="dd187-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="dd187-110">很好：切面：显示一个切片的数据量</span><span class="sxs-lookup"><span data-stu-id="dd187-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="dd187-111">很好：剪切子卷：显示仅几个层的数据量</span><span class="sxs-lookup"><span data-stu-id="dd187-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="dd187-112">很好：降低卷呈现的分辨率 （请参阅混合解析场景渲染）</span><span class="sxs-lookup"><span data-stu-id="dd187-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="dd187-113">一定数量的应用程序中对任何特定帧中的屏幕可以传输的信息，这是总内存带宽。</span><span class="sxs-lookup"><span data-stu-id="dd187-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="dd187-114">此外需要转换该数据以供演示文稿任何处理 （或明暗度） 也需要时间。</span><span class="sxs-lookup"><span data-stu-id="dd187-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="dd187-115">执行批量呈现时的主要注意事项是这种情况下：</span><span class="sxs-lookup"><span data-stu-id="dd187-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="dd187-116">屏幕宽度 \* 屏幕高度 \* 屏幕计数 \* 卷的层上-，-像素 = 总-卷-示例-每个帧</span><span class="sxs-lookup"><span data-stu-id="dd187-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="dd187-117">1028 \* 720 \* 2 \* 256 = 378961920 （100%)(完整 res 卷： 太多的示例)</span><span class="sxs-lookup"><span data-stu-id="dd187-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="dd187-118">1028 \* 720 \* 2 \* 1 = 1480320 （完整的 0.3%) (精简切片：顺利运行每个像素，1 示例）</span><span class="sxs-lookup"><span data-stu-id="dd187-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="dd187-119">1028 \* 720 \* 2 \* 10 = 14803200 （完整的 3.9%) (子卷切片：每个像素，10 个示例运行相当顺畅，看起来 3d）</span><span class="sxs-lookup"><span data-stu-id="dd187-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="dd187-120">200 \* 200 \* 2 \* 256 = 20480000 （完整的 5%) (降低 res 卷： 较少的像素为单位，整卷，看起来 3d，但有些 blury)</span><span class="sxs-lookup"><span data-stu-id="dd187-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="dd187-121">表示三维纹理</span><span class="sxs-lookup"><span data-stu-id="dd187-121">Representing 3D Textures</span></span>

<span data-ttu-id="dd187-122">CPU:</span><span class="sxs-lookup"><span data-stu-id="dd187-122">On the CPU:</span></span>

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

<span data-ttu-id="dd187-123">在 GPU:</span><span class="sxs-lookup"><span data-stu-id="dd187-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="dd187-124">明暗度和渐变</span><span class="sxs-lookup"><span data-stu-id="dd187-124">Shading and Gradients</span></span>

<span data-ttu-id="dd187-125">如何添加有用的可视化效果的卷，如 MRI、 阴影。</span><span class="sxs-lookup"><span data-stu-id="dd187-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="dd187-126">主要方法是让明暗度窗口 （最小值和最大） 想要查看强度内，并只需扩展到该空间以查看黑色或白色的强度。</span><span class="sxs-lookup"><span data-stu-id="dd187-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="dd187-127">可应用于该范围内的值和存储为纹理，以便在强度范畴内形成的不同部分可以是不同的阴影的颜色色阶:</span><span class="sxs-lookup"><span data-stu-id="dd187-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="dd187-128">在许多我们我们在原始的强度值和分段 index 我们卷中存储的应用程序 （如划分不同部分皮肤和骨骼，这些段通常由创建专用工具方面的专家）。</span><span class="sxs-lookup"><span data-stu-id="dd187-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="dd187-129">这可以将不同的颜色或甚至不同的颜色为每个段索引的负载增加，上述方法与组合：</span><span class="sxs-lookup"><span data-stu-id="dd187-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="dd187-130">在着色器中切片的卷</span><span class="sxs-lookup"><span data-stu-id="dd187-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="dd187-131">第一个重要步骤是创建"切片面"，可以浏览该卷，切片它，并扫描每个点处的值。</span><span class="sxs-lookup"><span data-stu-id="dd187-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="dd187-132">这假设没有 VolumeSpace 多维数据集，表示此卷将在世界空间中，可以用作引用放置点：</span><span class="sxs-lookup"><span data-stu-id="dd187-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="dd187-133">着色器中的卷跟踪</span><span class="sxs-lookup"><span data-stu-id="dd187-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="dd187-134">如何使用 GPU 进行子卷跟踪 （指导少量 voxels 深度然后层的数据从后向前）：</span><span class="sxs-lookup"><span data-stu-id="dd187-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="dd187-135">整个卷呈现</span><span class="sxs-lookup"><span data-stu-id="dd187-135">Whole Volume Rendering</span></span>

<span data-ttu-id="dd187-136">修改上面的子卷代码，我们得到：</span><span class="sxs-lookup"><span data-stu-id="dd187-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="dd187-137">混合的解析场景渲染</span><span class="sxs-lookup"><span data-stu-id="dd187-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="dd187-138">如何呈现场景中具有较低分辨率的一部分，并将其放回位置：</span><span class="sxs-lookup"><span data-stu-id="dd187-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="dd187-139">设置两个屏外相机，另一个用于遵循更新每个帧每只眼睛</span><span class="sxs-lookup"><span data-stu-id="dd187-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="dd187-140">安装程序两个较低分辨率呈现器目标 (例如大小为 200x200 每个)，照相机呈现到</span><span class="sxs-lookup"><span data-stu-id="dd187-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="dd187-141">设置移动用户四核</span><span class="sxs-lookup"><span data-stu-id="dd187-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="dd187-142">每个帧：</span><span class="sxs-lookup"><span data-stu-id="dd187-142">Each Frame:</span></span>
1. <span data-ttu-id="dd187-143">在较低分辨率绘制每只眼睛的呈现器目标 （卷数据、 昂贵的着色器等）</span><span class="sxs-lookup"><span data-stu-id="dd187-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="dd187-144">绘制场景通常作为完整分辨率 （网格、 UI 等。）</span><span class="sxs-lookup"><span data-stu-id="dd187-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="dd187-145">场景中，通过绘制四呈现给用户，并投影到的低分辨率的呈现。</span><span class="sxs-lookup"><span data-stu-id="dd187-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="dd187-146">使用较低分辨率，但高密度卷数据的高分辨率元素的结果： visual 组合。</span><span class="sxs-lookup"><span data-stu-id="dd187-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>
