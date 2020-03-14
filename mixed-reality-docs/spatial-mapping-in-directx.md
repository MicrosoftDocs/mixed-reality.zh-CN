---
title: DirectX 中的空间映射
description: 介绍如何在 DirectX 应用中实现空间映射。 这包括通用 Windows 平台 SDK 随附的空间映射示例应用程序的详细说明。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed reality，空间映射，环境，交互，directx，winrt，api，示例代码，UWP，SDK，演练
ms.openlocfilehash: 456fcf1c00e23a287a741673e94b3f8d2d2d346c
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375814"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="9b74f-105">DirectX 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="9b74f-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="9b74f-106">本主题介绍如何在 DirectX 应用中实现[空间映射](spatial-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="9b74f-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="9b74f-107">这包括通用 Windows 平台 SDK 随附的空间映射示例应用程序的详细说明。</span><span class="sxs-lookup"><span data-stu-id="9b74f-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="9b74f-108">本主题使用[HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 代码示例中的代码。</span><span class="sxs-lookup"><span data-stu-id="9b74f-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="9b74f-109">本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT，这与全息项目模板中使用的不同。</span><span class="sxs-lookup"><span data-stu-id="9b74f-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="9b74f-110">概念对于C++/WinRT 项目是等效的，但你将需要转换代码。</span><span class="sxs-lookup"><span data-stu-id="9b74f-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="9b74f-111">设备支持</span><span class="sxs-lookup"><span data-stu-id="9b74f-111">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9b74f-112"><strong>具有</strong></span><span class="sxs-lookup"><span data-stu-id="9b74f-112"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="9b74f-113"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="9b74f-113"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="9b74f-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="9b74f-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="9b74f-115"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="9b74f-115"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="9b74f-116">空间映射</span><span class="sxs-lookup"><span data-stu-id="9b74f-116">Spatial mapping</span></span></td>
        <td><span data-ttu-id="9b74f-117">✔️</span><span class="sxs-lookup"><span data-stu-id="9b74f-117">✔️</span></span></td>
        <td><span data-ttu-id="9b74f-118">✔️</span><span class="sxs-lookup"><span data-stu-id="9b74f-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a><span data-ttu-id="9b74f-119">DirectX 开发概述</span><span class="sxs-lookup"><span data-stu-id="9b74f-119">DirectX development overview</span></span>

<span data-ttu-id="9b74f-120">空间映射的本机应用程序开发使用[Windows 感知](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)命名空间下的 api。</span><span class="sxs-lookup"><span data-stu-id="9b74f-120">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="9b74f-121">这些 Api 提供完全控制空间映射功能，其方式与[Unity](spatial-mapping-in-unity.md)公开的空间映射 api 直接类似。</span><span class="sxs-lookup"><span data-stu-id="9b74f-121">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="9b74f-122">感知 Api</span><span class="sxs-lookup"><span data-stu-id="9b74f-122">Perception APIs</span></span>

<span data-ttu-id="9b74f-123">为空间映射开发提供的主要类型如下：</span><span class="sxs-lookup"><span data-stu-id="9b74f-123">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="9b74f-124">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)以 SpatialSurfaceInfo 对象的形式提供与用户附近的应用程序指定区域中的表面相关的信息。</span><span class="sxs-lookup"><span data-stu-id="9b74f-124">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="9b74f-125">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)描述单个存在空间图面，包括唯一 ID、边界量和上次更改时间。</span><span class="sxs-lookup"><span data-stu-id="9b74f-125">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="9b74f-126">它将根据请求异步提供 SpatialSurfaceMesh。</span><span class="sxs-lookup"><span data-stu-id="9b74f-126">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="9b74f-127">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx)包含用于自定义 SpatialSurfaceInfo 中请求的 SpatialSurfaceMesh 对象的参数。</span><span class="sxs-lookup"><span data-stu-id="9b74f-127">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="9b74f-128">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)表示单个空间图面的网格数据。</span><span class="sxs-lookup"><span data-stu-id="9b74f-128">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="9b74f-129">顶点位置、顶点法线和三角索引的数据包含在 member SpatialSurfaceMeshBuffer 对象中。</span><span class="sxs-lookup"><span data-stu-id="9b74f-129">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="9b74f-130">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx)环绕一种类型的网格数据。</span><span class="sxs-lookup"><span data-stu-id="9b74f-130">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="9b74f-131">当使用这些 Api 开发应用程序时，基本程序流将如下所示（如下面所述的示例应用程序所示）：</span><span class="sxs-lookup"><span data-stu-id="9b74f-131">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="9b74f-132">**设置 SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="9b74f-132">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="9b74f-133">调用[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)，以确保用户为应用程序提供了使用设备的空间映射功能的权限。</span><span class="sxs-lookup"><span data-stu-id="9b74f-133">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="9b74f-134">实例化 SpatialSurfaceObserver 对象。</span><span class="sxs-lookup"><span data-stu-id="9b74f-134">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="9b74f-135">调用[SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx)可指定要在其中显示空间图面信息的区域。</span><span class="sxs-lookup"><span data-stu-id="9b74f-135">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="9b74f-136">您可以在以后修改这些区域，只需再次调用此函数。</span><span class="sxs-lookup"><span data-stu-id="9b74f-136">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="9b74f-137">每个区域都是使用[SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)指定的。</span><span class="sxs-lookup"><span data-stu-id="9b74f-137">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="9b74f-138">注册[ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)事件，每当有新信息可用于指定空间区域中的空间图面时，将触发该事件。</span><span class="sxs-lookup"><span data-stu-id="9b74f-138">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="9b74f-139">**处理 ObservedSurfacesChanged 事件**</span><span class="sxs-lookup"><span data-stu-id="9b74f-139">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="9b74f-140">在事件处理程序中，调用[GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx)来接收 SpatialSurfaceInfo 对象的映射。</span><span class="sxs-lookup"><span data-stu-id="9b74f-140">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="9b74f-141">使用此地图，可以更新[用户环境中存在](spatial-mapping.md#mesh-caching)的空间表面的记录。</span><span class="sxs-lookup"><span data-stu-id="9b74f-141">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="9b74f-142">对于每个 SpatialSurfaceInfo 对象，可以通过查询[TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx)来确定图面的空间范围，用所选的[空间坐标系统](coordinate-systems.md)表示。</span><span class="sxs-lookup"><span data-stu-id="9b74f-142">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="9b74f-143">如果决定为空间图面请求网格，请调用[TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9b74f-143">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="9b74f-144">您可以提供选项来指定所需的三角形密度和返回的网格数据的格式。</span><span class="sxs-lookup"><span data-stu-id="9b74f-144">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="9b74f-145">**接收和处理网格**</span><span class="sxs-lookup"><span data-stu-id="9b74f-145">**Receive and process mesh**</span></span>
  - <span data-ttu-id="9b74f-146">对 TryComputeLatestMeshAsync 的每次调用都将 aysnchronously 返回一个 SpatialSurfaceMesh 对象。</span><span class="sxs-lookup"><span data-stu-id="9b74f-146">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="9b74f-147">从此对象，您可以访问包含的 SpatialSurfaceMeshBuffer 对象，以便访问该网格的三角形索引、顶点位置和（如果请求）顶点法线。</span><span class="sxs-lookup"><span data-stu-id="9b74f-147">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="9b74f-148">此数据将采用与用于呈现网格的[Direct3D 11 api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx)直接兼容的格式。</span><span class="sxs-lookup"><span data-stu-id="9b74f-148">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="9b74f-149">从这里，你的应用程序可以选择执行网格数据的分析或[处理](spatial-mapping.md#mesh-processing)，并将其用于[呈现](spatial-mapping.md#rendering)和物理学[raycasting 和冲突](spatial-mapping.md#raycasting-and-collision)。</span><span class="sxs-lookup"><span data-stu-id="9b74f-149">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="9b74f-150">需要注意的一个重要细节是，您必须将一个规模应用于网格顶点位置（例如，在用于呈现网格的顶点着色器中），以便将它们从缓冲区中存储的优化整数单位转换为米。</span><span class="sxs-lookup"><span data-stu-id="9b74f-150">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="9b74f-151">可以通过调用[VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)来检索此缩放。</span><span class="sxs-lookup"><span data-stu-id="9b74f-151">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="9b74f-152">故障排除</span><span class="sxs-lookup"><span data-stu-id="9b74f-152">Troubleshooting</span></span>
* <span data-ttu-id="9b74f-153">别忘了使用 SpatialSurfaceMesh 返回的刻度在顶点着色器中缩放网格顶点位置[。 VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="9b74f-153">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="9b74f-154">空间映射代码示例</span><span class="sxs-lookup"><span data-stu-id="9b74f-154">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="9b74f-155">[全息空间映射](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)代码示例包含可用于开始将 surface 网格加载到应用中的代码，其中包括用于管理和呈现 surface 网格的基础结构。</span><span class="sxs-lookup"><span data-stu-id="9b74f-155">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="9b74f-156">现在，我们将演练如何向 DirectX 应用程序添加 surface 映射功能。</span><span class="sxs-lookup"><span data-stu-id="9b74f-156">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="9b74f-157">您可以将此代码添加到您的[Windows 全息应用程序模板](creating-a-holographic-directx-project.md)项目，也可以通过浏览上面提到的代码示例来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="9b74f-157">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="9b74f-158">此代码示例基于 Windows 全息应用程序模板。</span><span class="sxs-lookup"><span data-stu-id="9b74f-158">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="9b74f-159">设置应用程序以使用 spatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="9b74f-159">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="9b74f-160">您的应用程序必须能够使用空间映射功能。</span><span class="sxs-lookup"><span data-stu-id="9b74f-160">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="9b74f-161">这是必需的，因为空间网格是用户环境的表示形式，该环境可能被视为私有数据。</span><span class="sxs-lookup"><span data-stu-id="9b74f-161">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="9b74f-162">在应用程序的 appxmanifest.xml 文件中声明此功能。</span><span class="sxs-lookup"><span data-stu-id="9b74f-162">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="9b74f-163">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="9b74f-163">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="9b74f-164">此功能来自**uap2**命名空间。</span><span class="sxs-lookup"><span data-stu-id="9b74f-164">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="9b74f-165">若要在清单中获取此命名空间的访问权限，请将其包含为 &lt;包 > 元素中的*xlmns*属性。</span><span class="sxs-lookup"><span data-stu-id="9b74f-165">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="9b74f-166">下面是一个示例：</span><span class="sxs-lookup"><span data-stu-id="9b74f-166">Here's an example:</span></span>

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="9b74f-167">检查空间映射功能支持</span><span class="sxs-lookup"><span data-stu-id="9b74f-167">Check for spatial mapping feature support</span></span>

<span data-ttu-id="9b74f-168">Windows Mixed Reality 支持多种设备，包括不支持空间映射的设备。</span><span class="sxs-lookup"><span data-stu-id="9b74f-168">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="9b74f-169">如果你的应用程序可以使用空间映射，或者必须使用空间映射来提供功能，则在尝试使用空间映射之前应进行检查以确保其受支持。</span><span class="sxs-lookup"><span data-stu-id="9b74f-169">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="9b74f-170">例如，如果你的混合现实应用需要空间映射，则当用户尝试在不使用空间映射的设备上运行该应用程序时，它应会显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="9b74f-170">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="9b74f-171">或者，你的应用程序可能能够呈现自己的虚拟环境来代替用户的环境，提供的体验与在空间映射可用时所发生的情况类似。</span><span class="sxs-lookup"><span data-stu-id="9b74f-171">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="9b74f-172">在任何情况下，此 API 都允许你的应用程序在不获取空间映射数据的情况下进行识别，并以适当的方式做出响应。</span><span class="sxs-lookup"><span data-stu-id="9b74f-172">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="9b74f-173">若要检查当前设备的空间映射支持，请首先确保 UWP 协定处于级别4或更高级别，然后调用 SpatialSurfaceObserver：： IsSupported （）。</span><span class="sxs-lookup"><span data-stu-id="9b74f-173">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="9b74f-174">下面介绍了如何在[全息空间映射](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)代码示例的上下文中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="9b74f-174">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="9b74f-175">请求访问之前，只需检查支持。</span><span class="sxs-lookup"><span data-stu-id="9b74f-175">Support is checked just before requesting access.</span></span>

<span data-ttu-id="9b74f-176">从 SDK 版本15063开始，可以使用 SpatialSurfaceObserver：： IsSupported （） API。</span><span class="sxs-lookup"><span data-stu-id="9b74f-176">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="9b74f-177">如有必要，请在使用此 API 之前将项目重定向到平台15063版。</span><span class="sxs-lookup"><span data-stu-id="9b74f-177">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

<span data-ttu-id="9b74f-178">请注意，当 UWP 协定小于级别4时，应用程序应继续执行，就像设备能够进行空间映射一样。</span><span class="sxs-lookup"><span data-stu-id="9b74f-178">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="9b74f-179">请求访问空间映射数据</span><span class="sxs-lookup"><span data-stu-id="9b74f-179">Request access to spatial mapping data</span></span>

<span data-ttu-id="9b74f-180">在尝试创建任何 surface 观察器之前，应用需要请求访问空间映射数据的权限。</span><span class="sxs-lookup"><span data-stu-id="9b74f-180">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="9b74f-181">下面是一个基于我们的图面映射代码示例的示例，本页面后面提供了更多详细信息：</span><span class="sxs-lookup"><span data-stu-id="9b74f-181">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a><span data-ttu-id="9b74f-182">创建 surface 观察器</span><span class="sxs-lookup"><span data-stu-id="9b74f-182">Create a surface observer</span></span>

<span data-ttu-id="9b74f-183">**Windows：:P erception：：空间：：** surface 命名空间包括[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)类，该类用于观察在[SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)中指定的一个或多个卷。</span><span class="sxs-lookup"><span data-stu-id="9b74f-183">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="9b74f-184">使用[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)实例实时访问 surface 网格数据。</span><span class="sxs-lookup"><span data-stu-id="9b74f-184">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="9b74f-185">从**AppMain**：</span><span class="sxs-lookup"><span data-stu-id="9b74f-185">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="9b74f-186">如前一部分所述，必须先请求对空间映射数据的访问权限，然后应用才能使用。</span><span class="sxs-lookup"><span data-stu-id="9b74f-186">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="9b74f-187">此访问权限是在 HoloLens 上自动授予的。</span><span class="sxs-lookup"><span data-stu-id="9b74f-187">This access is granted automatically on the HoloLens.</span></span>

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

<span data-ttu-id="9b74f-188">接下来，需要配置 surface 观察器来观察特定的边界卷。</span><span class="sxs-lookup"><span data-stu-id="9b74f-188">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="9b74f-189">在这里，我们看到一个20x20x5 计量的框，该框以坐标系统的原点为中心。</span><span class="sxs-lookup"><span data-stu-id="9b74f-189">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

<span data-ttu-id="9b74f-190">请注意，可以改为设置多个范围卷。</span><span class="sxs-lookup"><span data-stu-id="9b74f-190">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="9b74f-191">*这是伪代码：*</span><span class="sxs-lookup"><span data-stu-id="9b74f-191">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="9b74f-192">还可以使用其他边界形状（如视图 "截锥"）或不是轴对齐的边界框。</span><span class="sxs-lookup"><span data-stu-id="9b74f-192">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="9b74f-193">*这是伪代码：*</span><span class="sxs-lookup"><span data-stu-id="9b74f-193">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="9b74f-194">如果你的应用程序在表面映射数据不可用时需要执行任何操作，则可以编写代码来响应不**允许**使用[SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx)的情况，例如，由于这些设备没有用于空间映射的硬件，因此不允许在已连接沉浸设备的电脑上使用它。</span><span class="sxs-lookup"><span data-stu-id="9b74f-194">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="9b74f-195">对于这些设备，你应改用空间阶段来了解有关用户的环境和设备配置的信息。</span><span class="sxs-lookup"><span data-stu-id="9b74f-195">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="9b74f-196">初始化和更新 surface 网格集合</span><span class="sxs-lookup"><span data-stu-id="9b74f-196">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="9b74f-197">如果已成功创建 surface 观察程序，我们可以继续初始化我们的 surface 网格集合。</span><span class="sxs-lookup"><span data-stu-id="9b74f-197">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="9b74f-198">在这里，我们使用提取模型 API 立即获取当前观察到的曲面集：</span><span class="sxs-lookup"><span data-stu-id="9b74f-198">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

<span data-ttu-id="9b74f-199">还有一个可用于获取 surface 网格数据的推送模型。</span><span class="sxs-lookup"><span data-stu-id="9b74f-199">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="9b74f-200">如果你选择，则可以自由地将应用程序设计为仅使用请求模型，在这种情况下，将每隔一帧（例如，每帧一次）或在特定时间段（例如游戏安装期间）轮询数据。</span><span class="sxs-lookup"><span data-stu-id="9b74f-200">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="9b74f-201">如果是这样，则需要用到上述代码。</span><span class="sxs-lookup"><span data-stu-id="9b74f-201">If so, the above code is what you need.</span></span>

<span data-ttu-id="9b74f-202">在我们的代码示例中，我们选择了使用这两种模型来实现除教学之外目的。</span><span class="sxs-lookup"><span data-stu-id="9b74f-202">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="9b74f-203">在这里，我们将订阅事件，以便在系统识别更改时接收最新的 surface 网格数据。</span><span class="sxs-lookup"><span data-stu-id="9b74f-203">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="9b74f-204">我们的代码示例还配置为响应这些事件。</span><span class="sxs-lookup"><span data-stu-id="9b74f-204">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="9b74f-205">我们来看看如何实现此目的。</span><span class="sxs-lookup"><span data-stu-id="9b74f-205">Let's walk through how we do this.</span></span>

<span data-ttu-id="9b74f-206">**注意：** 这可能不是你的应用程序处理网格数据的最有效方法。</span><span class="sxs-lookup"><span data-stu-id="9b74f-206">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="9b74f-207">此代码为清楚起见编写，未进行优化。</span><span class="sxs-lookup"><span data-stu-id="9b74f-207">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="9b74f-208">在存储使用[Platform：： guid](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)作为键值的[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)对象的只读映射中提供了 surface 网格数据。</span><span class="sxs-lookup"><span data-stu-id="9b74f-208">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="9b74f-209">为了处理此数据，我们首先查找集合中不是的键值。</span><span class="sxs-lookup"><span data-stu-id="9b74f-209">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="9b74f-210">本主题稍后将介绍如何将数据存储在示例应用中的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9b74f-210">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

<span data-ttu-id="9b74f-211">我们还必须删除 surface 网格集合中的表面网格，但不再存在于系统集合中。</span><span class="sxs-lookup"><span data-stu-id="9b74f-211">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="9b74f-212">为此，我们需要执行类似于我们刚刚为添加和更新网格而显示的内容的操作;我们会循环访问应用的集合，并查看系统集合中是否存在**Guid** 。</span><span class="sxs-lookup"><span data-stu-id="9b74f-212">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="9b74f-213">如果不在系统集合中，我们会将其删除。</span><span class="sxs-lookup"><span data-stu-id="9b74f-213">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="9b74f-214">通过 AppMain 中的事件处理程序：</span><span class="sxs-lookup"><span data-stu-id="9b74f-214">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="9b74f-215">RealtimeSurfaceMeshRenderer 中的网格修剪实现：</span><span class="sxs-lookup"><span data-stu-id="9b74f-215">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="9b74f-216">获取和使用 surface 网格数据缓冲区</span><span class="sxs-lookup"><span data-stu-id="9b74f-216">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="9b74f-217">获取 surface 网格信息非常简单，只需将数据收集和处理更新到该集合。</span><span class="sxs-lookup"><span data-stu-id="9b74f-217">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="9b74f-218">现在，我们将详细介绍如何使用数据。</span><span class="sxs-lookup"><span data-stu-id="9b74f-218">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="9b74f-219">在我们的代码示例中，我们选择使用 surface 网格进行呈现。</span><span class="sxs-lookup"><span data-stu-id="9b74f-219">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="9b74f-220">这是在真实表面上 occluding 全息影像的常见方案。</span><span class="sxs-lookup"><span data-stu-id="9b74f-220">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="9b74f-221">你还可以呈现网格，或呈现这些网格的已处理版本，以便在开始提供应用或游戏功能之前向用户显示房间的扫描区域。</span><span class="sxs-lookup"><span data-stu-id="9b74f-221">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="9b74f-222">当从我们在上一节中介绍的事件处理程序接收 surface 网格更新时，代码示例将启动进程。</span><span class="sxs-lookup"><span data-stu-id="9b74f-222">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="9b74f-223">此函数中的重要代码行是更新 surface*网格*的调用：这次，我们已经处理了网格信息，我们即将获取用于显示的顶点和索引数据。</span><span class="sxs-lookup"><span data-stu-id="9b74f-223">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="9b74f-224">从 RealtimeSurfaceMeshRenderer：</span><span class="sxs-lookup"><span data-stu-id="9b74f-224">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

<span data-ttu-id="9b74f-225">我们的示例代码旨在使数据类**SurfaceMesh**处理网格数据处理和呈现。</span><span class="sxs-lookup"><span data-stu-id="9b74f-225">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="9b74f-226">这些网格是**RealtimeSurfaceMeshRenderer**实际保存地图的内容。</span><span class="sxs-lookup"><span data-stu-id="9b74f-226">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="9b74f-227">每个帐户都有一个对其来源的 SpatialSurfaceMesh 的引用，我们随时使用它来访问网格顶点或索引缓冲区，或者获取网格的转换。</span><span class="sxs-lookup"><span data-stu-id="9b74f-227">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="9b74f-228">现在，我们将网格标记为需要更新。</span><span class="sxs-lookup"><span data-stu-id="9b74f-228">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="9b74f-229">从 SurfaceMesh：</span><span class="sxs-lookup"><span data-stu-id="9b74f-229">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="9b74f-230">下一次要求网格绘制自身时，它将首先检查标志。</span><span class="sxs-lookup"><span data-stu-id="9b74f-230">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="9b74f-231">如果需要更新，则会在 GPU 上更新顶点和索引缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9b74f-231">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

<span data-ttu-id="9b74f-232">首先，我们获取原始数据缓冲区：</span><span class="sxs-lookup"><span data-stu-id="9b74f-232">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="9b74f-233">然后，使用 HoloLens 提供的网格数据创建 Direct3D 设备缓冲区：</span><span class="sxs-lookup"><span data-stu-id="9b74f-233">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

<span data-ttu-id="9b74f-234">**注意：** 有关上一代码片段中使用的 CreateDirectXBuffer helper 函数，请参阅 Surface 映射代码示例： SurfaceMesh、GetDataFromIBuffer。</span><span class="sxs-lookup"><span data-stu-id="9b74f-234">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="9b74f-235">现在，设备资源创建已完成，并且网格被视为已加载并准备好进行更新和呈现。</span><span class="sxs-lookup"><span data-stu-id="9b74f-235">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="9b74f-236">更新和呈现 surface 网格</span><span class="sxs-lookup"><span data-stu-id="9b74f-236">Update and render surface meshes</span></span>

<span data-ttu-id="9b74f-237">我们的 SurfaceMesh 类具有专用的更新函数。</span><span class="sxs-lookup"><span data-stu-id="9b74f-237">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="9b74f-238">每个[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)都有其自己的转换，我们的示例使用**SpatialStationaryReferenceFrame**的当前坐标系统来获取转换。</span><span class="sxs-lookup"><span data-stu-id="9b74f-238">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="9b74f-239">然后，它会更新 GPU 上的模型常量缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9b74f-239">Then it updates the model constant buffer on the GPU.</span></span>

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

<span data-ttu-id="9b74f-240">当需要呈现 surface 网格时，请在呈现集合之前做一些准备工作。</span><span class="sxs-lookup"><span data-stu-id="9b74f-240">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="9b74f-241">我们为当前呈现配置设置着色器管道，并设置 "输入组装器" 阶段。</span><span class="sxs-lookup"><span data-stu-id="9b74f-241">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="9b74f-242">请注意，全息相机帮助程序类**CameraResources**现在已经设置了视图/投影常量缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9b74f-242">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="9b74f-243">From **RealtimeSurfaceMeshRenderer：： Render**：</span><span class="sxs-lookup"><span data-stu-id="9b74f-243">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

<span data-ttu-id="9b74f-244">完成此操作后，我们将在网格上循环，并告诉每个网格自行绘制。</span><span class="sxs-lookup"><span data-stu-id="9b74f-244">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="9b74f-245">**注意：** 此示例代码未经过优化，无法使用任何种类的截锥剔除，但你应在应用程序中包括此功能。</span><span class="sxs-lookup"><span data-stu-id="9b74f-245">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

<span data-ttu-id="9b74f-246">单个网格负责设置顶点和索引缓冲区、步幅和模型转换常量缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9b74f-246">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="9b74f-247">与 Windows 全息应用程序模板中的旋转多维数据集一样，我们使用实例化来 stereoscopic 缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9b74f-247">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="9b74f-248">From **SurfaceMesh：:D raw**：</span><span class="sxs-lookup"><span data-stu-id="9b74f-248">From **SurfaceMesh::Draw**:</span></span>

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="9b74f-249">用图面映射呈现选项</span><span class="sxs-lookup"><span data-stu-id="9b74f-249">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="9b74f-250">外围应用程序代码示例提供了用于封闭呈现 surface 网格数据的代码，以及用于在屏幕上呈现 surface 网格数据的代码。</span><span class="sxs-lookup"><span data-stu-id="9b74f-250">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="9b74f-251">选择的路径（或两者）取决于应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b74f-251">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="9b74f-252">我们将在本文档中逐步介绍这两种配置。</span><span class="sxs-lookup"><span data-stu-id="9b74f-252">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="9b74f-253">**呈现全息效果的封闭缓冲区**</span><span class="sxs-lookup"><span data-stu-id="9b74f-253">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="9b74f-254">首先，清除当前虚拟摄像机的呈现目标视图。</span><span class="sxs-lookup"><span data-stu-id="9b74f-254">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="9b74f-255">从 AppMain：</span><span class="sxs-lookup"><span data-stu-id="9b74f-255">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="9b74f-256">这是一个 "预渲染" 阶段。</span><span class="sxs-lookup"><span data-stu-id="9b74f-256">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="9b74f-257">在这里，我们将通过请求网格呈现器来仅呈现深度来创建封闭缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9b74f-257">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="9b74f-258">在此配置中，我们不会附加 "呈现目标" 视图，并且网格呈现器会将 "像素着色器" 阶段设置为**nullptr** ，以便 GPU 不必消耗像素。</span><span class="sxs-lookup"><span data-stu-id="9b74f-258">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="9b74f-259">几何将栅格化到深度缓冲区，图形管道将停止。</span><span class="sxs-lookup"><span data-stu-id="9b74f-259">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

<span data-ttu-id="9b74f-260">我们可以使用针对图面映射封闭缓冲区的额外深度测试来绘制全息影像。</span><span class="sxs-lookup"><span data-stu-id="9b74f-260">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="9b74f-261">在此代码示例中，如果多维数据集位于图面后面，则将其呈现为不同的颜色。</span><span class="sxs-lookup"><span data-stu-id="9b74f-261">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="9b74f-262">从 AppMain：</span><span class="sxs-lookup"><span data-stu-id="9b74f-262">From AppMain.cpp:</span></span>

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

<span data-ttu-id="9b74f-263">基于 SpecialEffectPixelShader 中的代码。 hlsl：</span><span class="sxs-lookup"><span data-stu-id="9b74f-263">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

<span data-ttu-id="9b74f-264">**注意：** 对于我们的**GatherDepthLess**例程，请参阅 Surface Mapping 代码示例： SpecialEffectPixelShader. hlsl。</span><span class="sxs-lookup"><span data-stu-id="9b74f-264">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="9b74f-265">**向显示器呈现 surface 网格数据**</span><span class="sxs-lookup"><span data-stu-id="9b74f-265">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="9b74f-266">我们还可以将表面网格绘制到立体声显示缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9b74f-266">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="9b74f-267">我们选择使用光照绘制完全面，但可以自由地绘制线框，在渲染前处理网格，应用纹理地图等。</span><span class="sxs-lookup"><span data-stu-id="9b74f-267">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="9b74f-268">在这里，我们的代码示例告诉网格呈现器绘制集合。</span><span class="sxs-lookup"><span data-stu-id="9b74f-268">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="9b74f-269">这次我们不会指定仅深度传递，因此它会附加像素着色器并使用为当前虚拟摄像机指定的目标来完成呈现管道。</span><span class="sxs-lookup"><span data-stu-id="9b74f-269">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a><span data-ttu-id="9b74f-270">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b74f-270">See also</span></span>
* [<span data-ttu-id="9b74f-271">创建全息 DirectX 项目</span><span class="sxs-lookup"><span data-stu-id="9b74f-271">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="9b74f-272">Windows 感知. 空间 API</span><span class="sxs-lookup"><span data-stu-id="9b74f-272">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
