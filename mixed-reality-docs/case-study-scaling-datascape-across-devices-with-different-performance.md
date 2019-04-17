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
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>案例研究-缩放 Datascape 跨设备使用不同的性能

Datascape 是内部开发在 Microsoft 我们致力于显示地形数据基础之上的天气数据的其中一个 Windows Mixed Reality 应用程序。 应用程序探讨了独特的用户获得的见解中的发现数据混合现实中通过括起 holographic 数据可视化效果的用户。

有关 Datascape 我们想要针对多个平台的不同的硬件能力无处不在从 Windows Mixed Reality 沉浸式耳机到 Microsoft HoloLens 和低功率的 Pc，到使用高端 GPU 的最新 Pc。 主要的挑战在高的帧速率为执行时呈现场景极具视觉吸引力只需使用完全不同的图形功能在设备上。

本案例研究将引导完成的过程和用于创建多个 GPU 密集型系统，我们遇到的问题以及如何克服其描述的一些技术。

## <a name="transparency-and-overdraw"></a>透明度和过度绘制

我们主要呈现由来已久处理透明度，因为透明度可能很昂贵 GPU 上。

可以从前到后写入到深度缓冲区，停止任何将来的像素为单位位于从被放弃该像素时呈现实体几何。 这可以防止隐藏的像素执行像素着色器，显著加快该过程。 如果几何图形以最佳方式排序，将只有一次绘制在屏幕上的每个像素。

要排序的透明 geometry 需要从后向前，依赖于值混合处理像素着色器在屏幕上的当前像素的输出。 这可能导致要绘制到多个时间每帧，称为过度绘制在屏幕上每个像素。

对于 HoloLens，主流电脑屏幕只能填充少量的时间，从而使透明呈现有问题。

## <a name="introduction-to-datascape-scene-components"></a>Datascape 场景组件简介

我们必须场景; 三个主要组件**UI 中，地图**，并**天气**。 我们知道在早期，我们的天气效果会需要它无法获取的所有 GPU 时间，因此我们特意设计的 UI 和地形会降低任何过度绘制的方式。

我们重新设计 UI 几次以最大程度减少的量过度绘制它会生成。 我们会误更复杂的几何图形而不是叠加透明的艺术效果彼此的组件，如光亮的按钮和映射概述的一侧。

为映射中，我们将使用的自定义着色器会去除标准 Unity 功能，如阴影和复杂的光照，它们替换为简单的单一 sun 照明模型和自定义雾计算。 这会生成简单的像素着色器，并释放 GPU 周期。

我们设法将 UI 并映射到呈现在预算，我们不需要对其具体取决于硬件; 的任何更改但是，天气可视化，尤其是云渲染被证明是更具挑战性 ！

## <a name="background-on-cloud-data"></a>云数据的背景信息

我们的云数据从 NOAA 服务器下载 (http://nomads.ncep.noaa.gov/)和来到我们在三个不同的 2D 图层，每个与在云中的顶部和底部高度，以及在云中为每个单元格网格的密度。 处理的数据获取到云信息纹理，方便用户在 GPU 上纹理的红色、 绿色和蓝色组件中存储每个组件。

## <a name="geometry-clouds"></a>Geometry 云

若要确保我们的低功率计算机无法呈现我们决定首先我们云将使用实体几何尽量减少这种方法，过度绘制。

我们首先尝试通过生成 solid heightmap 网格的每一层使用的每个顶点的云信息纹理的半径生成形状来生成云。 我们使用几何着色器生成的顶点在顶部和在云中生成可靠的云形状的底部。 我们使用从纹理的密度值与为多个密集云较深的颜色的颜色在云中。

**用于创建顶点着色器：**

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

我们引入了一小干扰模式，以获取实际数据基础之上的更多详细信息。 若要生成云倒圆角边缘，我们剪裁像素像素着色器中的内插的半径值命中阈值以放弃近乎实时的值时。

![Geometry 云](images/datascape-geometry-clouds-700px.jpg)

由于云实体几何，它们可以呈现之前地形隐藏下方的任何成本高昂的映射像素为单位来进一步提高帧速率。 此解决方案运行于所有最小值规范中高端图形卡的图形卡以及 HoloLens，由于实体几何呈现方法。

## <a name="solid-particle-clouds"></a>Solid 粒子云

现在我们的备份解决方案，生成的相当不错的表示形式的云数据，但有点不景气"wow"因素中，未提供我们希望我们的高端计算机的容量耗尽感觉。

下一步创建云表示其中约 100,000 粒子，以生成更自然和容量耗尽外观。

如果粒子保持不变，并且排序从前到后，我们仍可以利用的背后以前呈现粒子像素的深度缓冲区消除减少过度绘制。 此外，借助基于粒子的解决方案，我们可以更改用于对目标不同的硬件的粒子的量。 但是，所有像素仍都需要进行深度测试，这将导致更多的开销。

首先，我们在启动时创建体验的中心点围绕粒子位置。 我们分布式更密集地围绕的中心粒子，那么在距离。 我们预先排序从中心向后的所有粒子，以便最接近的粒子将会呈现在第一次。

计算着色器将示例云信息纹理来定位在正确的高度和颜色基于密度的每个粒子。

我们使用了*DrawProcedural*呈现每个粒子允许粒子数据保留在 GPU 上根本四倍。

每个粒子包含高度和半径。 高度基于从云信息纹理采样的云数据和半径基于初始分布，它会进行计算，以便存储到其最近的邻居的水平距离。 四边形会使用此数据来定位自身，以便当用户查看其水平，由高度倾斜高度将会显示，并且用户在其上而下进行查找，将包含一些与其相邻元素之间的区域。

![粒子形状](images/particle-shape-700px.png)

**显示分发的着色器代码：**

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

由于我们对粒子从前到后进行排序，并且我们仍使用 solid 样式为剪辑 (而不是 blend) 透明像素着色器，此方法将处理极其大量的粒子，避免成本高昂的过度绘制，即使在低功率计算机上。

## <a name="transparent-particle-clouds"></a>透明粒子云

Solid 粒子提供良好的有机感觉到形状中的云，但仍需要一些销售的云 fluffiness。 我们决定尝试我们可能会引入透明度的高端图形卡的自定义解决方案。

若要这样做我们只需切换粒子的初始排序顺序，并更改要使用的纹理的 alpha 的着色器。

![Fluffy 云](images/fluffy-clouds-700px.jpg)

但事实证明，为甚至极难解决的机显得体量过于庞大，因为这会导致在呈现每个像素的次数的数百个屏幕上看来很棒 ！

## <a name="render-off-screen-with-lower-resolution"></a>具有较低分辨率屏幕外呈现

为了减少由云呈现的像素数，我们开始呈现它们 （与屏幕相比） 的每个季度解析缓冲区中并拉伸的最终结果将备份到屏幕上所有粒子必须都绘制之后。 这为我们提供大约 4 倍的加速，但附带几个需要注意的问题。

**用于呈现屏幕外的代码：**

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

首先，呈现到屏外缓冲区时, 我们深度的所有信息从都丢失主要场景，导致呈现基于 mountain 山脉背后的粒子。

其次，拉伸缓冲区还引入了项目的更改分辨率是明显我们云边缘上。 接下来两个部分讨论一下我们如何解决这些问题。

## <a name="particle-depth-buffer"></a>粒子深度缓冲区

若要使世界几何图形与共存的粒子 mountain 或对象可能涵盖其背后的粒子，我们填充具有包含主要场景的几何图形的深度缓冲区的屏外缓冲区。 若要生成此类深度缓冲区，我们创建了第二种照相机，呈现实体几何和场景的深度。

我们然后使用新的纹理中的云的像素着色器遮蔽像素为单位。 我们使用相同的纹理来计算到云像素背后的几何图形的距离。 通过使用该距离，并将其应用到像素的 alpha，我们现在有的云淡出，因为它们会接近地形，删除任何硬切割粒子和地形相交处的效果。

![地形到混合云](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>锐化边缘

拉伸向上云看起来几乎与中心的粒子的正常大小的云，或在云边缘其中它们重叠，但显示的某些项目。 否则为锐边会显示模糊和照相机移动时引入了别名效果。

我们来解决这个问题通过屏外缓冲区，以确定大的更改与此相反发生 (1) 上运行简单的着色器。 我们大更改的像素的新模具缓冲区 (2)。 我们然后使用掩码的模具缓冲区出这些高对比度区域回复到屏幕上，应用屏外缓冲区时导致漏洞中和围绕云 (3)。

我们然后呈现所有粒子再次在全屏幕模式下，但这一次使用的所有内容遮住了模具缓冲区但中的最小的像素集而产生的边数 (4)。 命令缓冲区已创建的粒子，因为我们只是不得不再次将其显示为新的照相机。

![呈现云边缘的进度](images/cloud-steps-1-4-700px.jpg)

最终的结果是与云的成本低廉的中心部分锐边。

虽然此举远快于呈现中的所有粒子都全屏，没有与测试以便大量过度绘制仍针对模具缓冲区中，一个像素相关的成本仍附带成本。

## <a name="culling-particles"></a>消除粒子

对于我们风的效果，我们在计算着色器，在世界中创建的风力束生成长三角形条带。 不繁重的填充率生成的窄带由于风效果时，它会生成许多数十万个顶点的顶点着色器导致负载过重。

我们引入了附加计算着色器中，源风力条带线要绘制的子集上的缓冲区。 使用一些简单的视图截锥精选逻辑计算着色器中，我们可以确定 strip 是照相机视图之外，并防止它被添加到推送缓冲区。 这条带线的量显著降低，释放在 GPU 上某些所需的周期。

**演示一个追加的缓冲区的代码：**

*计算着色器：*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#代码：*

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

我们试着云粒子，我们会选择这些数据上的计算着色器，并仅推送可见的粒子要呈现上使用相同的方法。 此方法实际上没有保存我们很大程度上 GPU 因为最大瓶颈是量像素呈现在屏幕上，并不计算顶点的成本。

通过此方法的另一个问题是由于计算粒子，导致已排序的粒子是未排序，从而导致闪烁云粒子其并行化性质的随机顺序填充追加缓冲区。

有方法进行排序的推送缓冲区，但有限的数量的性能提升我们带消除粒子将可能相对偏移量为使用其他排序，因此我们决定不采用这种优化。

## <a name="adaptive-rendering"></a>自适应呈现

若要使用不同的呈现多云 vs 诸如条件清楚地确保稳定的帧速率的应用程序，我们引入自适应呈现到我们的应用程序。

自适应呈现的第一步是测量 GPU。 我们是通过将自定义代码插入到在 GPU 命令缓冲区的开头和结尾的呈现的帧，捕获两者左侧和右侧眼睛屏幕时间。

通过测量呈现并将它与我们的接近程度，我们在其中放置帧的意义上我们所需刷新频率进行比较，所用的时间。

当接近丢失帧，我们调整以更快地使我们呈现。 简单的调整方式更改屏幕上，需要更少的像素为单位获取呈现的视区大小。

通过使用*UnityEngine.XR.XRSettings.renderViewportScale*系统缩小目标视区和备份到适合屏幕的结果将自动伸缩。 按比例少量更改是世界几何图形上几乎可以忽略，0.7 的比例因子需要一半要呈现的像素。

![70%规模，一半的像素](images/datascape-scaling-700px.jpg)

我们检测到我们正准备丢弃的帧我们降低由固定数量的规模并提高其回我们速度不够快再次运行时。

虽然我们决定要使用哪些云技术基于图形的在启动时的硬件功能，可以基于数据的 GPU 测量，以防止系统保持较低的分辨率为很长时间，但这也是我们没有时间 若要在 Datascape 浏览。

## <a name="final-thoughts"></a>最后的几点思考

面向各种硬件一项挑战，并需要进行一些规划。

我们建议你先针对低功率计算机熟悉问题空间和开发将在所有计算机运行的备份解决方案。 设计你的解决方案使用的填充率的一点是，由于像素都将是你最宝贵的资源。 对透明度的目标实体几何。

与备份解决方案，可以然后启动分层详细程度不一的高端机，也可能只是增强您的备份解决方案的解决方法。

为最坏的情况下，设计和也许考虑繁重的情况下使用自适应呈现。

## <a name="about-the-authors"></a>关于作者

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>软件工程师 @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>软件工程师 @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>请参阅
* [混合现实的了解性能](understanding-performance-for-mixed-reality.md)
* [Unity 的性能建议](performance-recommendations-for-unity.md)

 
