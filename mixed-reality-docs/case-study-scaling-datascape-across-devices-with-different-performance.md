---
title: 案例研究-缩放 Datascape 跨设备使用不同的性能
description: 本案例研究提供了解 Microsoft 开发人员如何优化 Datascape 应用可在一系列性能功能的设备提供极具吸引力的体验。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式头戴式耳机，性能优化，VR 案例研究
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593022"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="16799-104">案例研究-缩放 Datascape 跨设备使用不同的性能</span><span class="sxs-lookup"><span data-stu-id="16799-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="16799-105">Datascape 是内部开发在 Microsoft 我们致力于显示地形数据基础之上的天气数据的其中一个 Windows Mixed Reality 应用程序。</span><span class="sxs-lookup"><span data-stu-id="16799-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="16799-106">应用程序探讨了独特的用户获得的见解中的发现数据混合现实中通过括起 holographic 数据可视化效果的用户。</span><span class="sxs-lookup"><span data-stu-id="16799-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="16799-107">有关 Datascape 我们想要针对多个平台的不同的硬件能力无处不在从 Windows Mixed Reality 沉浸式耳机到 Microsoft HoloLens 和低功率的 Pc，到使用高端 GPU 的最新 Pc。</span><span class="sxs-lookup"><span data-stu-id="16799-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="16799-108">主要的挑战在高的帧速率为执行时呈现场景极具视觉吸引力只需使用完全不同的图形功能在设备上。</span><span class="sxs-lookup"><span data-stu-id="16799-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="16799-109">本案例研究将引导完成的过程和用于创建多个 GPU 密集型系统，我们遇到的问题以及如何克服其描述的一些技术。</span><span class="sxs-lookup"><span data-stu-id="16799-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="16799-110">透明度和过度绘制</span><span class="sxs-lookup"><span data-stu-id="16799-110">Transparency and overdraw</span></span>

<span data-ttu-id="16799-111">我们主要呈现由来已久处理透明度，因为透明度可能很昂贵 GPU 上。</span><span class="sxs-lookup"><span data-stu-id="16799-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="16799-112">可以从前到后写入到深度缓冲区，停止任何将来的像素为单位位于从被放弃该像素时呈现实体几何。</span><span class="sxs-lookup"><span data-stu-id="16799-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="16799-113">这可以防止隐藏的像素执行像素着色器，显著加快该过程。</span><span class="sxs-lookup"><span data-stu-id="16799-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="16799-114">如果几何图形以最佳方式排序，将只有一次绘制在屏幕上的每个像素。</span><span class="sxs-lookup"><span data-stu-id="16799-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="16799-115">要排序的透明 geometry 需要从后向前，依赖于值混合处理像素着色器在屏幕上的当前像素的输出。</span><span class="sxs-lookup"><span data-stu-id="16799-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="16799-116">这可能导致要绘制到多个时间每帧，称为过度绘制在屏幕上每个像素。</span><span class="sxs-lookup"><span data-stu-id="16799-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="16799-117">对于 HoloLens，主流电脑屏幕只能填充少量的时间，从而使透明呈现有问题。</span><span class="sxs-lookup"><span data-stu-id="16799-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="16799-118">Datascape 场景组件简介</span><span class="sxs-lookup"><span data-stu-id="16799-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="16799-119">我们必须场景; 三个主要组件**UI 中，地图**，并**天气**。</span><span class="sxs-lookup"><span data-stu-id="16799-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="16799-120">我们知道在早期，我们的天气效果会需要它无法获取的所有 GPU 时间，因此我们特意设计的 UI 和地形会降低任何过度绘制的方式。</span><span class="sxs-lookup"><span data-stu-id="16799-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="16799-121">我们重新设计 UI 几次以最大程度减少的量过度绘制它会生成。</span><span class="sxs-lookup"><span data-stu-id="16799-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="16799-122">我们会误更复杂的几何图形而不是叠加透明的艺术效果彼此的组件，如光亮的按钮和映射概述的一侧。</span><span class="sxs-lookup"><span data-stu-id="16799-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="16799-123">为映射中，我们将使用的自定义着色器会去除标准 Unity 功能，如阴影和复杂的光照，它们替换为简单的单一 sun 照明模型和自定义雾计算。</span><span class="sxs-lookup"><span data-stu-id="16799-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="16799-124">这会生成简单的像素着色器，并释放 GPU 周期。</span><span class="sxs-lookup"><span data-stu-id="16799-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="16799-125">我们设法将 UI 并映射到呈现在预算，我们不需要对其具体取决于硬件; 的任何更改但是，天气可视化，尤其是云渲染被证明是更具挑战性 ！</span><span class="sxs-lookup"><span data-stu-id="16799-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="16799-126">云数据的背景信息</span><span class="sxs-lookup"><span data-stu-id="16799-126">Background on cloud data</span></span>

<span data-ttu-id="16799-127">我们的云数据从 NOAA 服务器下载 (http://nomads.ncep.noaa.gov/)和来到我们在三个不同的 2D 图层，每个与在云中的顶部和底部高度，以及在云中为每个单元格网格的密度。</span><span class="sxs-lookup"><span data-stu-id="16799-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="16799-128">处理的数据获取到云信息纹理，方便用户在 GPU 上纹理的红色、 绿色和蓝色组件中存储每个组件。</span><span class="sxs-lookup"><span data-stu-id="16799-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="16799-129">Geometry 云</span><span class="sxs-lookup"><span data-stu-id="16799-129">Geometry clouds</span></span>

<span data-ttu-id="16799-130">若要确保我们的低功率计算机无法呈现我们决定首先我们云将使用实体几何尽量减少这种方法，过度绘制。</span><span class="sxs-lookup"><span data-stu-id="16799-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="16799-131">我们首先尝试通过生成 solid heightmap 网格的每一层使用的每个顶点的云信息纹理的半径生成形状来生成云。</span><span class="sxs-lookup"><span data-stu-id="16799-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="16799-132">我们使用几何着色器生成的顶点在顶部和在云中生成可靠的云形状的底部。</span><span class="sxs-lookup"><span data-stu-id="16799-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="16799-133">我们使用从纹理的密度值与为多个密集云较深的颜色的颜色在云中。</span><span class="sxs-lookup"><span data-stu-id="16799-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="16799-134">**用于创建顶点着色器：**</span><span class="sxs-lookup"><span data-stu-id="16799-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="16799-135">我们引入了一小干扰模式，以获取实际数据基础之上的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="16799-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="16799-136">若要生成云倒圆角边缘，我们剪裁像素像素着色器中的内插的半径值命中阈值以放弃近乎实时的值时。</span><span class="sxs-lookup"><span data-stu-id="16799-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Geometry 云](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="16799-138">由于云实体几何，它们可以呈现之前地形隐藏下方的任何成本高昂的映射像素为单位来进一步提高帧速率。</span><span class="sxs-lookup"><span data-stu-id="16799-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="16799-139">此解决方案运行于所有最小值规范中高端图形卡的图形卡以及 HoloLens，由于实体几何呈现方法。</span><span class="sxs-lookup"><span data-stu-id="16799-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="16799-140">Solid 粒子云</span><span class="sxs-lookup"><span data-stu-id="16799-140">Solid particle clouds</span></span>

<span data-ttu-id="16799-141">现在我们的备份解决方案，生成的相当不错的表示形式的云数据，但有点不景气"wow"因素中，未提供我们希望我们的高端计算机的容量耗尽感觉。</span><span class="sxs-lookup"><span data-stu-id="16799-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="16799-142">下一步创建云表示其中约 100,000 粒子，以生成更自然和容量耗尽外观。</span><span class="sxs-lookup"><span data-stu-id="16799-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="16799-143">如果粒子保持不变，并且排序从前到后，我们仍可以利用的背后以前呈现粒子像素的深度缓冲区消除减少过度绘制。</span><span class="sxs-lookup"><span data-stu-id="16799-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="16799-144">此外，借助基于粒子的解决方案，我们可以更改用于对目标不同的硬件的粒子的量。</span><span class="sxs-lookup"><span data-stu-id="16799-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="16799-145">但是，所有像素仍都需要进行深度测试，这将导致更多的开销。</span><span class="sxs-lookup"><span data-stu-id="16799-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="16799-146">首先，我们在启动时创建体验的中心点围绕粒子位置。</span><span class="sxs-lookup"><span data-stu-id="16799-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="16799-147">我们分布式更密集地围绕的中心粒子，那么在距离。</span><span class="sxs-lookup"><span data-stu-id="16799-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="16799-148">我们预先排序从中心向后的所有粒子，以便最接近的粒子将会呈现在第一次。</span><span class="sxs-lookup"><span data-stu-id="16799-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="16799-149">计算着色器将示例云信息纹理来定位在正确的高度和颜色基于密度的每个粒子。</span><span class="sxs-lookup"><span data-stu-id="16799-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="16799-150">我们使用了*DrawProcedural*呈现每个粒子允许粒子数据保留在 GPU 上根本四倍。</span><span class="sxs-lookup"><span data-stu-id="16799-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="16799-151">每个粒子包含高度和半径。</span><span class="sxs-lookup"><span data-stu-id="16799-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="16799-152">高度基于从云信息纹理采样的云数据和半径基于初始分布，它会进行计算，以便存储到其最近的邻居的水平距离。</span><span class="sxs-lookup"><span data-stu-id="16799-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="16799-153">四边形会使用此数据来定位自身，以便当用户查看其水平，由高度倾斜高度将会显示，并且用户在其上而下进行查找，将包含一些与其相邻元素之间的区域。</span><span class="sxs-lookup"><span data-stu-id="16799-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![粒子形状](images/particle-shape-700px.png)

<span data-ttu-id="16799-155">**显示分发的着色器代码：**</span><span class="sxs-lookup"><span data-stu-id="16799-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="16799-156">由于我们对粒子从前到后进行排序，并且我们仍使用 solid 样式为剪辑 (而不是 blend) 透明像素着色器，此方法将处理极其大量的粒子，避免成本高昂的过度绘制，即使在低功率计算机上。</span><span class="sxs-lookup"><span data-stu-id="16799-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="16799-157">透明粒子云</span><span class="sxs-lookup"><span data-stu-id="16799-157">Transparent particle clouds</span></span>

<span data-ttu-id="16799-158">Solid 粒子提供良好的有机感觉到形状中的云，但仍需要一些销售的云 fluffiness。</span><span class="sxs-lookup"><span data-stu-id="16799-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="16799-159">我们决定尝试我们可能会引入透明度的高端图形卡的自定义解决方案。</span><span class="sxs-lookup"><span data-stu-id="16799-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="16799-160">若要这样做我们只需切换粒子的初始排序顺序，并更改要使用的纹理的 alpha 的着色器。</span><span class="sxs-lookup"><span data-stu-id="16799-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy 云](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="16799-162">但事实证明，为甚至极难解决的机显得体量过于庞大，因为这会导致在呈现每个像素的次数的数百个屏幕上看来很棒 ！</span><span class="sxs-lookup"><span data-stu-id="16799-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="16799-163">具有较低分辨率屏幕外呈现</span><span class="sxs-lookup"><span data-stu-id="16799-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="16799-164">为了减少由云呈现的像素数，我们开始呈现它们 （与屏幕相比） 的每个季度解析缓冲区中并拉伸的最终结果将备份到屏幕上所有粒子必须都绘制之后。</span><span class="sxs-lookup"><span data-stu-id="16799-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="16799-165">这为我们提供大约 4 倍的加速，但附带几个需要注意的问题。</span><span class="sxs-lookup"><span data-stu-id="16799-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="16799-166">**用于呈现屏幕外的代码：**</span><span class="sxs-lookup"><span data-stu-id="16799-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="16799-167">首先，呈现到屏外缓冲区时, 我们深度的所有信息从都丢失主要场景，导致呈现基于 mountain 山脉背后的粒子。</span><span class="sxs-lookup"><span data-stu-id="16799-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="16799-168">其次，拉伸缓冲区还引入了项目的更改分辨率是明显我们云边缘上。</span><span class="sxs-lookup"><span data-stu-id="16799-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="16799-169">接下来两个部分讨论一下我们如何解决这些问题。</span><span class="sxs-lookup"><span data-stu-id="16799-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="16799-170">粒子深度缓冲区</span><span class="sxs-lookup"><span data-stu-id="16799-170">Particle depth buffer</span></span>

<span data-ttu-id="16799-171">若要使世界几何图形与共存的粒子 mountain 或对象可能涵盖其背后的粒子，我们填充具有包含主要场景的几何图形的深度缓冲区的屏外缓冲区。</span><span class="sxs-lookup"><span data-stu-id="16799-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="16799-172">若要生成此类深度缓冲区，我们创建了第二种照相机，呈现实体几何和场景的深度。</span><span class="sxs-lookup"><span data-stu-id="16799-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="16799-173">我们然后使用新的纹理中的云的像素着色器遮蔽像素为单位。</span><span class="sxs-lookup"><span data-stu-id="16799-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="16799-174">我们使用相同的纹理来计算到云像素背后的几何图形的距离。</span><span class="sxs-lookup"><span data-stu-id="16799-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="16799-175">通过使用该距离，并将其应用到像素的 alpha，我们现在有的云淡出，因为它们会接近地形，删除任何硬切割粒子和地形相交处的效果。</span><span class="sxs-lookup"><span data-stu-id="16799-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![地形到混合云](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="16799-177">锐化边缘</span><span class="sxs-lookup"><span data-stu-id="16799-177">Sharpening the edges</span></span>

<span data-ttu-id="16799-178">拉伸向上云看起来几乎与中心的粒子的正常大小的云，或在云边缘其中它们重叠，但显示的某些项目。</span><span class="sxs-lookup"><span data-stu-id="16799-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="16799-179">否则为锐边会显示模糊和照相机移动时引入了别名效果。</span><span class="sxs-lookup"><span data-stu-id="16799-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="16799-180">我们来解决这个问题通过屏外缓冲区，以确定大的更改与此相反发生 (1) 上运行简单的着色器。</span><span class="sxs-lookup"><span data-stu-id="16799-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="16799-181">我们大更改的像素的新模具缓冲区 (2)。</span><span class="sxs-lookup"><span data-stu-id="16799-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="16799-182">我们然后使用掩码的模具缓冲区出这些高对比度区域回复到屏幕上，应用屏外缓冲区时导致漏洞中和围绕云 (3)。</span><span class="sxs-lookup"><span data-stu-id="16799-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="16799-183">我们然后呈现所有粒子再次在全屏幕模式下，但这一次使用的所有内容遮住了模具缓冲区但中的最小的像素集而产生的边数 (4)。</span><span class="sxs-lookup"><span data-stu-id="16799-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="16799-184">命令缓冲区已创建的粒子，因为我们只是不得不再次将其显示为新的照相机。</span><span class="sxs-lookup"><span data-stu-id="16799-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![呈现云边缘的进度](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="16799-186">最终的结果是与云的成本低廉的中心部分锐边。</span><span class="sxs-lookup"><span data-stu-id="16799-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="16799-187">虽然此举远快于呈现中的所有粒子都全屏，没有与测试以便大量过度绘制仍针对模具缓冲区中，一个像素相关的成本仍附带成本。</span><span class="sxs-lookup"><span data-stu-id="16799-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="16799-188">消除粒子</span><span class="sxs-lookup"><span data-stu-id="16799-188">Culling particles</span></span>

<span data-ttu-id="16799-189">对于我们风的效果，我们在计算着色器，在世界中创建的风力束生成长三角形条带。</span><span class="sxs-lookup"><span data-stu-id="16799-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="16799-190">不繁重的填充率生成的窄带由于风效果时，它会生成许多数十万个顶点的顶点着色器导致负载过重。</span><span class="sxs-lookup"><span data-stu-id="16799-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="16799-191">我们引入了附加计算着色器中，源风力条带线要绘制的子集上的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="16799-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="16799-192">使用一些简单的视图截锥精选逻辑计算着色器中，我们可以确定 strip 是照相机视图之外，并防止它被添加到推送缓冲区。</span><span class="sxs-lookup"><span data-stu-id="16799-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="16799-193">这条带线的量显著降低，释放在 GPU 上某些所需的周期。</span><span class="sxs-lookup"><span data-stu-id="16799-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="16799-194">**演示一个追加的缓冲区的代码：**</span><span class="sxs-lookup"><span data-stu-id="16799-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="16799-195">*计算着色器：*</span><span class="sxs-lookup"><span data-stu-id="16799-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="16799-196">*C#代码：*</span><span class="sxs-lookup"><span data-stu-id="16799-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="16799-197">我们试着云粒子，我们会选择这些数据上的计算着色器，并仅推送可见的粒子要呈现上使用相同的方法。</span><span class="sxs-lookup"><span data-stu-id="16799-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="16799-198">此方法实际上没有保存我们很大程度上 GPU 因为最大瓶颈是量像素呈现在屏幕上，并不计算顶点的成本。</span><span class="sxs-lookup"><span data-stu-id="16799-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="16799-199">通过此方法的另一个问题是由于计算粒子，导致已排序的粒子是未排序，从而导致闪烁云粒子其并行化性质的随机顺序填充追加缓冲区。</span><span class="sxs-lookup"><span data-stu-id="16799-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="16799-200">有方法进行排序的推送缓冲区，但有限的数量的性能提升我们带消除粒子将可能相对偏移量为使用其他排序，因此我们决定不采用这种优化。</span><span class="sxs-lookup"><span data-stu-id="16799-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="16799-201">自适应呈现</span><span class="sxs-lookup"><span data-stu-id="16799-201">Adaptive rendering</span></span>

<span data-ttu-id="16799-202">若要使用不同的呈现多云 vs 诸如条件清楚地确保稳定的帧速率的应用程序，我们引入自适应呈现到我们的应用程序。</span><span class="sxs-lookup"><span data-stu-id="16799-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="16799-203">自适应呈现的第一步是测量 GPU。</span><span class="sxs-lookup"><span data-stu-id="16799-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="16799-204">我们是通过将自定义代码插入到在 GPU 命令缓冲区的开头和结尾的呈现的帧，捕获两者左侧和右侧眼睛屏幕时间。</span><span class="sxs-lookup"><span data-stu-id="16799-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="16799-205">通过测量呈现并将它与我们的接近程度，我们在其中放置帧的意义上我们所需刷新频率进行比较，所用的时间。</span><span class="sxs-lookup"><span data-stu-id="16799-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="16799-206">当接近丢失帧，我们调整以更快地使我们呈现。</span><span class="sxs-lookup"><span data-stu-id="16799-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="16799-207">简单的调整方式更改屏幕上，需要更少的像素为单位获取呈现的视区大小。</span><span class="sxs-lookup"><span data-stu-id="16799-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="16799-208">通过使用*UnityEngine.XR.XRSettings.renderViewportScale*系统缩小目标视区和备份到适合屏幕的结果将自动伸缩。</span><span class="sxs-lookup"><span data-stu-id="16799-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="16799-209">按比例少量更改是世界几何图形上几乎可以忽略，0.7 的比例因子需要一半要呈现的像素。</span><span class="sxs-lookup"><span data-stu-id="16799-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70%规模，一半的像素](images/datascape-scaling-700px.jpg)

<span data-ttu-id="16799-211">我们检测到我们正准备丢弃的帧我们降低由固定数量的规模并提高其回我们速度不够快再次运行时。</span><span class="sxs-lookup"><span data-stu-id="16799-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="16799-212">虽然我们决定要使用哪些云技术基于图形的在启动时的硬件功能，可以基于数据的 GPU 测量，以防止系统保持较低的分辨率为很长时间，但这也是我们没有时间 若要在 Datascape 浏览。</span><span class="sxs-lookup"><span data-stu-id="16799-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="16799-213">最后的几点思考</span><span class="sxs-lookup"><span data-stu-id="16799-213">Final thoughts</span></span>

<span data-ttu-id="16799-214">面向各种硬件一项挑战，并需要进行一些规划。</span><span class="sxs-lookup"><span data-stu-id="16799-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="16799-215">我们建议你先针对低功率计算机熟悉问题空间和开发将在所有计算机运行的备份解决方案。</span><span class="sxs-lookup"><span data-stu-id="16799-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="16799-216">设计你的解决方案使用的填充率的一点是，由于像素都将是你最宝贵的资源。</span><span class="sxs-lookup"><span data-stu-id="16799-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="16799-217">对透明度的目标实体几何。</span><span class="sxs-lookup"><span data-stu-id="16799-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="16799-218">与备份解决方案，可以然后启动分层详细程度不一的高端机，也可能只是增强您的备份解决方案的解决方法。</span><span class="sxs-lookup"><span data-stu-id="16799-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="16799-219">为最坏的情况下，设计和也许考虑繁重的情况下使用自适应呈现。</span><span class="sxs-lookup"><span data-stu-id="16799-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="16799-220">关于作者</span><span class="sxs-lookup"><span data-stu-id="16799-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="16799-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="16799-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="16799-222">软件工程师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="16799-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="16799-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="16799-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="16799-224">软件工程师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="16799-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="16799-225">请参阅</span><span class="sxs-lookup"><span data-stu-id="16799-225">See also</span></span>
* [<span data-ttu-id="16799-226">混合现实的了解性能</span><span class="sxs-lookup"><span data-stu-id="16799-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="16799-227">Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="16799-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
