---
title: 场景理解
description: 针对 HoloLens 的场景了解功能简介
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 场景了解，空间映射，Windows Mixed Reality，Unity
ms.openlocfilehash: 4b959b7b7ec58fc30ed0fe93b568d123cbe70bb1
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502668"
---
# <a name="scene-understanding"></a><span data-ttu-id="39b60-104">场景理解</span><span class="sxs-lookup"><span data-stu-id="39b60-104">Scene understanding</span></span>

<span data-ttu-id="39b60-105">场景理解为混合现实开发人员提供了一种结构化的高级别环境表示形式，旨在简化环保感知应用程序的开发。</span><span class="sxs-lookup"><span data-stu-id="39b60-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="39b60-106">场景理解通过组合现有混合现实运行时的强大功能来实现此功能，如非常准确的结构化[空间映射](spatial-mapping.md)和新的 AI 驱动的运行时。</span><span class="sxs-lookup"><span data-stu-id="39b60-106">Scene understanding does this by combining the power of existing mixed reality runtimes, such as the highly accurate less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="39b60-107">通过将这些技术相结合，场景理解会生成与你可能已在 Unity 或 ARKit/ARCore 等框架中使用的3D 环境的表示形式。</span><span class="sxs-lookup"><span data-stu-id="39b60-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="39b60-108">场景理解入口点从场景观察器开始，该观察程序由应用程序调用以计算新场景。</span><span class="sxs-lookup"><span data-stu-id="39b60-108">The Scene understanding entry point begins with a Scene Observer, which is called by your application to compute a new scene.</span></span> <span data-ttu-id="39b60-109">目前，该技术可以生成3个不同但相关的对象类别：简化的 watertight 环境网格，这些网格可推断出平面房间结构，而不会产生混乱、我们调用四边形的放置的平面区域，以及与我们所介绍的四边形/Watertight 数据对齐的[空间映射](spatial-mapping.md)网格的快照。</span><span class="sxs-lookup"><span data-stu-id="39b60-109">Today, the technology is capable of generating 3 distinct but related object categories: simplified watertight environment meshes that infer the planar room structure without clutter, plane regions for placement that we call Quads, and a snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface.</span></span>

![空间映射网格，标签平面表面，watertight 网格](images/SUScenarios.png)

<span data-ttu-id="39b60-111">本文档旨在提供方案概述，并阐明场景理解和空间映射共享的关系。</span><span class="sxs-lookup"><span data-stu-id="39b60-111">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="39b60-112">通过场景理解进行开发</span><span class="sxs-lookup"><span data-stu-id="39b60-112">Developing with Scene Understanding</span></span>

<span data-ttu-id="39b60-113">本文仅用于介绍运行时和概念的场景。</span><span class="sxs-lookup"><span data-stu-id="39b60-113">This article only serves to introduce the Scene Understanding runtime and concepts.</span></span> <span data-ttu-id="39b60-114">如果你正在查找有关如何通过场景理解进行开发的文档，你可能对以下内容感兴趣：</span><span class="sxs-lookup"><span data-stu-id="39b60-114">If you are looking for documentation on how to develop with Scene Understanding, you may be interested in the following:</span></span>

[<span data-ttu-id="39b60-115">场景理解 SDK 概述</span><span class="sxs-lookup"><span data-stu-id="39b60-115">Scene Understanding SDK overview</span></span>](scene-understanding-SDK.md)

<span data-ttu-id="39b60-116">可以从示例 GitHub 站点下载场景理解示例应用：</span><span class="sxs-lookup"><span data-stu-id="39b60-116">You can download the Scene Understanding Sample app from the sample GitHub site:</span></span>

[<span data-ttu-id="39b60-117">场景理解示例</span><span class="sxs-lookup"><span data-stu-id="39b60-117">Scene Understanding Sample</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample)

<span data-ttu-id="39b60-118">如果你没有设备，并且想要访问示例场景来尝试场景了解，示例资产文件夹中有一些场景：</span><span class="sxs-lookup"><span data-stu-id="39b60-118">If you do not have a device and wish to access sample scenes to try Scene Understanding out, there are scenes in the sample asset folder:</span></span>

[<span data-ttu-id="39b60-119">场景了解示例场景</span><span class="sxs-lookup"><span data-stu-id="39b60-119">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a><span data-ttu-id="39b60-120">SDK</span><span class="sxs-lookup"><span data-stu-id="39b60-120">SDK</span></span>

<span data-ttu-id="39b60-121">如果你正在寻找有关如何针对场景理解进行开发的特定详细信息，或有关场景理解如何工作的详细信息以及如何针对其进行开发的详细信息，请参阅[场景了解 SDK 概述](scene-understanding-SDK.md)文档。</span><span class="sxs-lookup"><span data-stu-id="39b60-121">If you are looking for specific details on how to develop for Scene Understanding or details on how Scene understanding works and how to develop for it, see the [Scene Understanding SDK overview](scene-understanding-SDK.md) documentation.</span></span>


### <a name="sample"></a><span data-ttu-id="39b60-122">示例</span><span class="sxs-lookup"><span data-stu-id="39b60-122">Sample</span></span>


## <a name="device-support"></a><span data-ttu-id="39b60-123">设备支持</span><span class="sxs-lookup"><span data-stu-id="39b60-123">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="39b60-124"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="39b60-124"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="39b60-125"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="39b60-125"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="39b60-126"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="39b60-126"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="39b60-127"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="39b60-127"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="39b60-128">场景理解</span><span class="sxs-lookup"><span data-stu-id="39b60-128">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="39b60-129">✔️</span><span class="sxs-lookup"><span data-stu-id="39b60-129">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="39b60-130">常见使用方案</span><span class="sxs-lookup"><span data-stu-id="39b60-130">Common usage scenarios</span></span>

<span data-ttu-id="39b60-131">![常见空间映射使用方案的插图：放置、封闭、物理学和导航](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="39b60-131">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="39b60-132">*常见的空间映射使用方案：放置、封闭、物理学和导航。*</span><span class="sxs-lookup"><span data-stu-id="39b60-132">*Common spatial mapping usage scenarios: placement, occlusion, physics and navigation.*</span></span>

<br>

<span data-ttu-id="39b60-133">环境感知应用程序的许多核心方案（放置、封闭、物理学等）都可通过空间映射和场景理解来寻址，本节重点介绍这些差异。</span><span class="sxs-lookup"><span data-stu-id="39b60-133">Many of the core scenarios for environment aware applications (placement, occlusion, physics, etc.) are addressable by both Spatial mapping and Scene understanding, and this section highlights these differences.</span></span> <span data-ttu-id="39b60-134">场景理解和空间映射之间的核心差异是对结构和简易性的最大准确性和延迟的折衷。</span><span class="sxs-lookup"><span data-stu-id="39b60-134">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="39b60-135">如果你的应用程序需要可能的最低延迟，并且网格三角形只需要直接访问空间映射，但要执行更高级别的处理，则可以考虑切换到场景理解模型，因为它应提供你有功能的超集。</span><span class="sxs-lookup"><span data-stu-id="39b60-135">If your application requires the lowest-latency possible and mesh triangles that only you will want to access Spatial Mapping directly but you are performing higher level processing, you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="39b60-136">另请注意，由于场景理解将空间映射网格提供为其表示形式的一部分，因此你始终可以访问最完整且最准确的空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="39b60-136">Also note that because Scene understanding provides the spatial mapping mesh as part of its representation, you will always have access to the most complete and accurate spatial mapping data possible.</span></span>

<span data-ttu-id="39b60-137">以下部分将在新的场景理解 SDK 的上下文中重新访问核心空间映射方案。</span><span class="sxs-lookup"><span data-stu-id="39b60-137">The following sections re-visit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="39b60-138">放置</span><span class="sxs-lookup"><span data-stu-id="39b60-138">Placement</span></span>

<span data-ttu-id="39b60-139">场景理解提供了专门设计用于简化放置方案的新构造。</span><span class="sxs-lookup"><span data-stu-id="39b60-139">Scene understanding provides new constructs specifically designed to simplify placement scenarios.</span></span> <span data-ttu-id="39b60-140">场景可以计算称为 SceneQuads 的基元，它们描述了可放置全息影像的平面面。</span><span class="sxs-lookup"><span data-stu-id="39b60-140">A scene can compute primitives called SceneQuads which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="39b60-141">SceneQuads 专门围绕放置而设计，并介绍了二维图面，并提供了一个用于放置在该表面上的 API。</span><span class="sxs-lookup"><span data-stu-id="39b60-141">SceneQuads have specifically been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="39b60-142">以前，当使用三角形网格来执行放置时，必须扫描四个四个区域并执行孔填充/后处理来识别对象放置的好位置。</span><span class="sxs-lookup"><span data-stu-id="39b60-142">Previously, when using the triangle mesh to perform placement, one had to scan all areas of the quad and perform hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="39b60-143">这并不是始终需要的四边形，因为场景了解运行时能够推断出四个未扫描的四个区域，并使四个不属于图面的区域无效。</span><span class="sxs-lookup"><span data-stu-id="39b60-143">This is not always necessary with Quads, as the Scene understanding runtime is capable of inferring which areas of the quad that were not scanned, and invalidate areas of the quad that are not part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="39b60-144">已禁用推理 ![SceneQuads，并捕获扫描区域的放置区。](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="39b60-144">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="39b60-145">已禁用 SceneQuads 的**图像 #1** ，并捕获扫描区域的放置区。</span><span class="sxs-lookup"><span data-stu-id="39b60-145">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="39b60-146">启用了推理的 ![四边形，放置不再局限于扫描区域。](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="39b60-146">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="39b60-147">**图像 #2** -启用了推理的四边形，放置不再局限于扫描区域。</span><span class="sxs-lookup"><span data-stu-id="39b60-147">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="39b60-148">如果你的应用程序想要将二维或3D 全息图放置在环境的严格结构上，最好是从[空间映射](spatial-mapping.md)网格计算此信息。</span><span class="sxs-lookup"><span data-stu-id="39b60-148">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="39b60-149">有关此主题的更多详细信息，请参阅[场景理解 SDK 参考](scene-understanding-SDK.md)</span><span class="sxs-lookup"><span data-stu-id="39b60-149">For more details on this topic, please see the [Scene understanding SDK reference](scene-understanding-SDK.md)</span></span>

<span data-ttu-id="39b60-150">**注意**对于依赖于空间映射网格的传统放置代码，可以通过设置 EnableWorldMesh 设置与 SceneQuads 一起计算空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="39b60-150">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="39b60-151">如果场景理解 API 不满足应用程序的延迟要求，我们建议继续使用[空间映射 API](spatial-mapping.md#placement)。</span><span class="sxs-lookup"><span data-stu-id="39b60-151">If Scene understanding API does not satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="39b60-152">封闭</span><span class="sxs-lookup"><span data-stu-id="39b60-152">Occlusion</span></span>

<span data-ttu-id="39b60-153">[空间映射封闭](spatial-mapping.md#occlusion)仍是捕获环境的实时状态的最小延迟方式。</span><span class="sxs-lookup"><span data-stu-id="39b60-153">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="39b60-154">虽然这对于在高度动态的场景中提供封闭可能很有用，但出于多种原因，你可能希望考虑到封闭的场景理解。</span><span class="sxs-lookup"><span data-stu-id="39b60-154">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="39b60-155">如果使用通过场景理解生成的空间映射网格，则可以从空间映射请求数据，这些数据不会存储在本地缓存中，因此不能从感知 Api 中获取。</span><span class="sxs-lookup"><span data-stu-id="39b60-155">If you use the spatial mapping mesh generated by Scene Understanding, you can request data from spatial mapping that would not be stored in the local cache and therefore not available to you from the perception APIs.</span></span> <span data-ttu-id="39b60-156">使用封闭和 watertight 网格的空间映射将提供额外的价值，特别是完成未扫描的房间结构。</span><span class="sxs-lookup"><span data-stu-id="39b60-156">Using Spatial Mapping for occlusion alongside watertight meshes will provide additional value, specifically completion of un-scanned room structure.</span></span>

<span data-ttu-id="39b60-157">如果你的要求能够容忍更多的场景理解延迟，应用程序开发人员应考虑使用场景理解 watertight 网格，并使空间映射网格与平面表示形式结合。</span><span class="sxs-lookup"><span data-stu-id="39b60-157">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and presumably the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="39b60-158">这将提供 "这两个领域的最佳" 方案，其中简化的 watertight 封闭可以提供更好的 nonplanar 几何，提供最现实的封闭地图。</span><span class="sxs-lookup"><span data-stu-id="39b60-158">This would provide a "best of both worlds" scenario where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="39b60-159">物理学</span><span class="sxs-lookup"><span data-stu-id="39b60-159">Physics</span></span>

<span data-ttu-id="39b60-160">场景理解会生成 watertight 的网格，这些网格通过语义分解空间，特别是解决空间映射网格施加的物理限制。</span><span class="sxs-lookup"><span data-stu-id="39b60-160">Scene understanding generates watertight meshes that decompose space with semantics, specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="39b60-161">Watertight 结构可确保始终命中物理射线强制转换，通过语义分解可以更简单地生成用于室内导航的导航网格。</span><span class="sxs-lookup"><span data-stu-id="39b60-161">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="39b60-162">如[封闭](#occlusion)上的部分中所述，使用 EnableSceneObjectMeshes 和 EnableWorldMesh 创建场景可能会产生最实际的完整网格。</span><span class="sxs-lookup"><span data-stu-id="39b60-162">As described in the section on [occlusion](#occlusion), creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="39b60-163">环境网格的 watertight 属性将阻止命中测试失败，并且网格数据将确保物理学与场景中的所有对象交互，而不仅仅是与房间结构交互。</span><span class="sxs-lookup"><span data-stu-id="39b60-163">The watertight property of the environment mesh will prevent hit tests from failing to hit surfaces and the mesh data will ensure that physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="39b60-164">导航</span><span class="sxs-lookup"><span data-stu-id="39b60-164">Navigation</span></span>

<span data-ttu-id="39b60-165">按语义类分解的平面网格是用于导航和路径规划的理想构造，可减轻[空间映射导航](spatial-mapping.md#navigation)概述中所述的许多问题。</span><span class="sxs-lookup"><span data-stu-id="39b60-165">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="39b60-166">场景中计算的 SceneMesh 对象已经按表面类型进行了消除，这确保了导航网格的生成仅限于可遍历的图面。</span><span class="sxs-lookup"><span data-stu-id="39b60-166">The SceneMesh objects computed in the scene are already de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="39b60-167">由于楼层结构的简单性，根据实时要求，将根据实时需求，来满足 Unity 中的动态导航网格生成。</span><span class="sxs-lookup"><span data-stu-id="39b60-167">Due to the simplicity of the floor structure, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="39b60-168">生成准确的导航网格目前仍需要后处理，也就是说，应用程序仍然必须将 occluders 到地面上，以确保导航不会经历混乱/表等。实现此目的的最准确方法是在场景是用 EnableWorldMesh 标志计算的情况下，投影所提供的世界网格数据。</span><span class="sxs-lookup"><span data-stu-id="39b60-168">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation does not pass through clutter/tables etc... The most accurate way to accomplish this is to project the world mesh data which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="39b60-169">可视化效果</span><span class="sxs-lookup"><span data-stu-id="39b60-169">Visualization</span></span>

<span data-ttu-id="39b60-170">虽然[空间映射可视化](spatial-mapping.md#visualization)可用于环境的实时反馈，但在很多情况下，平面和 watertight 对象的简单性提供了更高的性能或视觉质量。</span><span class="sxs-lookup"><span data-stu-id="39b60-170">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="39b60-171">如果在四边形或平面 watertight 网格提供的平面表面上投影，则使用空间映射描述的阴影投影和接地技术可能更好。</span><span class="sxs-lookup"><span data-stu-id="39b60-171">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="39b60-172">这对于这样的环境/方案特别适用：由于场景将推断这一事实，完全预扫描并非最佳，而完整的环境和平面假设将最小化项目。</span><span class="sxs-lookup"><span data-stu-id="39b60-172">This is especially true for environments/scenarios where thorough pre-scanning is not optimal due to the fact that the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="39b60-173">此外，空间映射返回的图面总数受内部空间缓存的限制，而场景理解的空间映射网格版本可以访问未缓存的空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="39b60-173">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh is able to access spatial mapping data that is not cached.</span></span> <span data-ttu-id="39b60-174">因此，场景理解更适合捕获更大空间的网格表示形式（例如，大于单个房间）以用于可视化或进一步的网格处理。</span><span class="sxs-lookup"><span data-stu-id="39b60-174">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="39b60-175">使用 EnableWorldMesh 返回的世界网格在整个中具有一致的详细级别，这可能会产生更好的可视化效果（如果以线框形式呈现）。</span><span class="sxs-lookup"><span data-stu-id="39b60-175">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="39b60-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39b60-176">See Also</span></span>

* [<span data-ttu-id="39b60-177">场景理解 SDK</span><span class="sxs-lookup"><span data-stu-id="39b60-177">Scene understanding SDK</span></span>](scene-understanding-SDK.md)
* [<span data-ttu-id="39b60-178">空间映射</span><span class="sxs-lookup"><span data-stu-id="39b60-178">Spatial mapping</span></span>](spatial-mapping.md)
