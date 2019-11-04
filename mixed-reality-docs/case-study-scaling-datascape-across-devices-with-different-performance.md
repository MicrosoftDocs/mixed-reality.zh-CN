---
title: 案例研究-跨设备扩展 Datascape，性能不同
description: 此案例研究为 Microsoft 开发人员提供了对 Datascape 应用的优化，以便在具有一系列性能功能的设备之间提供引人注目的体验。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 沉浸式耳机，性能优化，VR，案例研究
ms.openlocfilehash: 05f97188c81d85685540be998111ecfc47d9ef9c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436504"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>案例研究-跨设备扩展 Datascape，性能不同

Datascape 是在 Microsoft 内部开发的 Windows Mixed Reality 应用程序，其中重点介绍了如何在地形数据之上显示天气数据。 该应用程序将探讨用户使用全息数据可视化来发现混合现实中的数据，从而实现独特的见解。

对于 Datascape，我们想要针对各种平台，其中包含不同的硬件功能，包括从 Microsoft HoloLens 到 Windows Mixed Reality 沉浸式耳机，以及从较低的 Pc 到使用高端 GPU 的最新 Pc。 主要的难题是，以较高的帧速率进行操作时，以具有不同图形功能的设备为外观呈现场景。

此案例研究将指导您创建一些更多 GPU 密集型系统所用的过程和技术，描述我们遇到的问题以及我们克服了它们的方式。

## <a name="transparency-and-overdraw"></a>透明度和过度绘制

我们的主要呈现由来已久处理透明度，因为透明度在 GPU 上可能会占用大量资源。

在写入深度缓冲区时，可以将实体几何正面向后呈现，停止该像素后面的任何未来像素。 这会阻止隐藏像素执行像素着色器，从而大大加快处理速度。 如果以最佳方式对几何图形进行排序，则屏幕上的每个像素将只绘制一次。

透明几何需要重新排回到前面，并依赖于将像素着色器的输出与屏幕上的当前像素混合。 这可能会导致屏幕上每个像素绘制到每个帧多次（称为过度绘制）。

对于 HoloLens 和主流 Pc，屏幕只能填充少量的时间，从而使透明渲染出现问题。

## <a name="introduction-to-datascape-scene-components"></a>Datascape 场景组件简介

我们有三个主要组件适用于我们的场景;**UI、地图**和**天气**。 我们提前了解到，天气效果会要求其可能获得的所有 GPU 时间，因此我们特意设计了 UI 和地形，从而减少了过度绘制。

我们多次改编 UI，以最大程度地减少它将产生的过度绘制量。 我们观点更复杂的几何图形，而不是针对光亮按钮和地图概述等组件覆盖彼此之上的透明图稿。

对于地图，我们使用了一个自定义着色器来去除标准 Unity 功能，如阴影和复杂照明，使用简单的单光源照明模型和自定义雾化计算来替换它们。 这会生成一个简单的像素着色器并释放 GPU 循环。

我们设法使用户界面和地图都可以在预算内呈现，而不需要根据硬件进行任何更改;不过，天气可视化（特别是云渲染）已证明是一个挑战！

## <a name="background-on-cloud-data"></a>云数据背景

我们的云数据是从 NOAA 服务器下载的（ https://nomads.ncep.noaa.gov/) ，并传入了三个不同的2D 层，每个层都有云的顶部和底部，以及网格每个单元格的云密度。 数据已处理为云信息纹理，其中每个组件都存储在纹理的红色、绿色和蓝色分量中，以便在 GPU 上轻松访问。

## <a name="geometry-clouds"></a>Geometry 云

为了确保较低功耗的计算机能够呈现我们的云，我们决定使用一种方法，即使用实体几何来最大程度地降低过度绘制。

首先，我们尝试使用每个顶点的云信息纹理半径为每个层生成一个实体 heightmap 网格，从而生成云。 我们使用几何着色器来生成实体云形状的顶部和底部的顶点。 我们使用纹理的密度值为云着色，使云的颜色变暗。

**用于创建顶点的着色器：**

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

我们引入了一种小干扰模式，可在真实数据的基础上获得更多详细信息。 若要生成轮 cloud 边缘，当内插的 radius 值达到阈值时，我们将在像素着色器中裁剪像素以放弃接近零值。

![Geometry 云](images/datascape-geometry-clouds-700px.jpg)

由于云是实体几何，因此它们可以在地形之前渲染，以隐藏下面的任何昂贵的地图像素以进一步提高速度。 由于实体几何呈现方法，此解决方案可在最小规格到高端图形卡的所有图形卡和 HoloLens 上正常运行。

## <a name="solid-particle-clouds"></a>固态粒子云

现在，我们有了一个备份解决方案，它为我们的云数据提供了一种更适当的表示形式，但有点 lackluster "wow" 因素，并且没有为高端计算机提供所需的容量耗尽感觉。

下一步是通过用约100000粒子代表它们来创建云，从而生成更随机的容量耗尽。

如果粒子保持稳定并按从前到后的顺序进行排序，则我们仍可以从前面呈现的粒子后面的像素的深度缓冲区剔除中获益，减少过度绘制。 此外，对于基于粒子的解决方案，我们可以更改用于面向不同硬件的粒子量。 但是，所有像素仍需进行深度测试，这会产生额外的开销。

首先，我们在启动时的体验中心点创建了粒子位置。 我们在中心围绕着更多的密集，而不是距离。 我们已将所有粒子从中心开始预先排序到了后面，以便首先呈现最近的粒子。

计算着色器会将云信息纹理采样，将每个粒子置于正确高度，并根据密度对其进行着色。

我们使用*DrawProcedural*来呈现每个粒子的四个四个粒子，使粒子数据始终保持在 GPU 上。

每个粒子都包含高度和半径。 此高度基于从云信息纹理采样的云数据，而 radius 基于初始分布，在这种情况下，将计算它以便将水平距离存储到最近的相邻位置。 四边形将使用此数据来向其方向倾斜高度，以便当用户水平查看时，将显示高度，并且当用户自上而下查看时，将覆盖其相邻区域。

![粒子形状](images/particle-shape-700px.png)

**显示分布的着色器代码：**

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

由于我们对微粒进行排序，并且仍使用纯色着色器来剪裁（而不是混合）透明像素，因此，此方法可处理惊人的粒子量，避免甚至在较低功率的计算机上消耗大量的消耗。

## <a name="transparent-particle-clouds"></a>透明粒子云

实体粒子为云的形状提供了一个很好的外观，但仍需要一些东西来销售云 fluffiness。 我们决定尝试使用高端图形卡的自定义解决方案，在这里我们可以引入透明性。

为此，我们只需切换粒子的初始排序顺序并将着色器更改为使用纹理 alpha。

![Fluffy 云](images/fluffy-clouds-700px.jpg)

它看起来很好，但对于最棘手的计算机来说，这种情况很大，因为它会导致在屏幕上呈现每个像素数百次！

## <a name="render-off-screen-with-lower-resolution"></a>以较低的分辨率呈现屏幕外

若要减少由云呈现的像素数，我们开始在四分之一分辨率缓冲区中呈现它们（与屏幕相比），并在所有粒子绘制完毕后将最终结果拉伸到屏幕上。 这为我们提供了大约4倍的加速，但有几个值得注意的事项。

**用于在屏幕外呈现的代码：**

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

第一种是，当渲染到屏幕外缓冲区时，我们将失去主场景中的所有深度信息，导致山上在山地的顶层。

其次，拉伸缓冲区还会在我们的云边缘上引入了解决变化明显的项目。 接下来的两部分将讨论如何解决这些问题。

## <a name="particle-depth-buffer"></a>粒子深度缓冲区

为了使微粒或对象可以涵盖其背后的微粒，使微粒与世界几何共存，我们用包含主场景几何的深度缓冲区填充了屏幕外缓冲区。 为了生成此类深度缓冲区，我们创建了第二个照相机，只呈现场景的实体几何和深度。

然后，在云的像素着色器中使用新纹理遮蔽像素。 我们使用相同的纹理来计算与云像素后的几何之间的距离。 通过使用该距离并将其应用于像素的 alpha，我们现在可以在接近地形的情况下淡出，并删除粒子和地形满足的任何硬剪切。

![混合到地形的云](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>锐化边缘

向上扩展的云与粒子中心或它们重叠的位置上几乎完全相同，但在云边缘展示了一些项目。 否则，在移动照相机时，锐化边缘会显得模糊，并引入别名效果。

为此，我们通过在离屏缓冲区上运行简单的着色器来确定发生了重大变化的变化（1）。 我们将有重大更改的像素放入新的模具缓冲区（2）。 然后，在将离屏缓冲区应用到屏幕上时，我们使用了模具缓冲区来掩盖这些高对比度区域，从而导致云（3）出现在和周围。

然后，在全屏模式下再次呈现所有粒子，但这一次使用模具缓冲区屏蔽除边缘之外的所有内容，从而导致一组接触的最小像素（4）。 由于已为粒子创建了命令缓冲区，因此，只需将其重新呈现给新的相机。

![呈现云边缘的进度](images/cloud-steps-1-4-700px.jpg)

最终的结果是，云的低价中心部分具有清晰的边缘。

虽然这比以全屏方式呈现所有粒子要快得多，但仍有一项与根据模具缓冲区测试像素相关的成本，因此，大量的过度绘制仍附带了费用。

## <a name="culling-particles"></a>剔除粒子

对于我们的风效果，我们在计算着色器中生成了长三角形条纹，在世界各地创建了许多 wisps。 虽然风效果并不太繁重，因为生成的是瘦的，但它产生了数百个顶点，导致顶点着色器出现繁重的负载。

我们在计算着色器中引入了追加缓冲区，用于馈送要绘制的一小部分。 在计算着色器中，可以通过一些简单的视图以截锥方式剔除逻辑，确定条带是否在相机视图外，并防止将其添加到推送缓冲区。 这大大减少了条纹的数量，从而释放了 GPU 上的一些必要的周期。

**演示追加缓冲区的代码：**

*计算着色器：*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#编写*

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

我们在云粒子上尝试使用相同的方法，我们会在其中精选计算着色器并仅推送要呈现的可见粒子。 此方法实际上不会对 GPU 节省太多时间，因为最大的瓶颈是在屏幕上呈现的像素量，而不是计算顶点的成本。

此方法的另一个问题是：追加缓冲区按随机顺序填充，因为它是计算粒子的并行性，导致已排序的粒子未排序，导致云粒子闪烁。

有一些用于对推送缓冲区进行排序的方法，但是，我们从精选粒子中获得的性能提升量可能会与其他排序偏移，因此我们决定不采用此优化。

## <a name="adaptive-rendering"></a>自适应呈现

为了确保在具有不同渲染条件（如云与清晰视图）的应用上以稳定的帧速率显示，我们在应用程序中引入了自适应呈现功能。

自适应呈现的第一步是测量 GPU。 为此，需要将自定义代码插入到呈现的帧开头和末尾的 GPU 命令缓冲区中，同时捕获左右眼睛屏幕时间。

通过测量渲染所用的时间并将其与我们所需的刷新率进行比较，我们可以大致了解我们的工作方式。

当接近删除帧时，我们将调整呈现以使其更快。 调整屏幕的视区大小是一种简单的方法，它要求呈现的像素更少。

通过使用*XRSettings. renderViewportScale* ，系统会缩小目标视区，并自动拉伸结果以适应屏幕 UnityEngine。 规模的小更改在世界几何上几乎不明显，缩放系数为0.7 需要呈现的像素量的一半。

![70% 的比例，每一半像素](images/datascape-scaling-700px.jpg)

当我们检测到我们将要丢弃的帧时，我们将按固定数值降低规模，并在我们再次运行速度变得更快时再增加。

尽管我们决定了在启动时基于硬件的图形功能要使用什么云技术，但也可以基于 GPU 度量值来防止系统长时间保持较低的分辨率，但这是我们没有时间的事情 若要在 Datascape 中浏览。

## <a name="final-thoughts"></a>最终想法

针对各种硬件具有挑战性，需要进行一些规划。

我们建议你开始针对较低功率的计算机，以熟悉问题空间，并开发将在所有计算机上运行的备份解决方案。 请记住，设计具有填充率的解决方案，因为像素是最宝贵的资源。 透明度上的目标实体几何。

利用备份解决方案，你可以在更大程度上为高端计算机开始分层，或者只是增强你的备份解决方案的分辨率。

针对最糟糕的情况进行设计，并且可能会考虑使用自适应呈现来应对繁重的情况。

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


## <a name="see-also"></a>另请参阅
* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [Unity 性能建议](performance-recommendations-for-unity.md)

 
