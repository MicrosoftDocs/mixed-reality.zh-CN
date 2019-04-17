---
title: 在 DirectX 空间映射
description: 介绍如何在 DirectX 应用中实现空间映射。 这包括使用通用 Windows 平台 SDK 附带的空间映射示例应用程序的详细的说明。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows 混合现实、 空间映射、 环境、 交互、 directx、 winrt、 api、 示例代码中，UWP，SDK，演练
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593075"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="08456-105">在 DirectX 空间映射</span><span class="sxs-lookup"><span data-stu-id="08456-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="08456-106">本主题介绍如何实现[空间映射](spatial-mapping.md)DirectX 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="08456-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="08456-107">这包括使用通用 Windows 平台 SDK 附带的空间映射示例应用程序的详细的说明。</span><span class="sxs-lookup"><span data-stu-id="08456-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="08456-108">本主题使用来自代码[HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 的代码示例。</span><span class="sxs-lookup"><span data-stu-id="08456-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="08456-109">这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="08456-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="08456-110">这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。</span><span class="sxs-lookup"><span data-stu-id="08456-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="08456-111">DirectX 开发概述</span><span class="sxs-lookup"><span data-stu-id="08456-111">DirectX development overview</span></span>

<span data-ttu-id="08456-112">空间映射的本机应用程序开发使用 Api 下的[Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)命名空间。</span><span class="sxs-lookup"><span data-stu-id="08456-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="08456-113">这些 Api 提供了空间映射中的功能，以直接类似于的空间的映射公开的 Api 完全控制[Unity](spatial-mapping-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="08456-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="08456-114">Perception Api</span><span class="sxs-lookup"><span data-stu-id="08456-114">Perception APIs</span></span>

<span data-ttu-id="08456-115">为空间映射开发提供的主类型如下所示：</span><span class="sxs-lookup"><span data-stu-id="08456-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="08456-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)提供有关应用程序指定的空间中的 SpatialSurfaceInfo 对象形式的用户附近的区域中显示的信息。</span><span class="sxs-lookup"><span data-stu-id="08456-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="08456-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)介绍一个现有空间图面，包括的唯一 ID、 边界卷以及上次更改的时间。</span><span class="sxs-lookup"><span data-stu-id="08456-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="08456-118">它将提供 SpatialSurfaceMesh 以异步方式根据请求。</span><span class="sxs-lookup"><span data-stu-id="08456-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="08456-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx)包含用于自定义所请求的 SpatialSurfaceInfo SpatialSurfaceMesh 对象参数。</span><span class="sxs-lookup"><span data-stu-id="08456-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="08456-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)表示单一的空间表面的网格数据。</span><span class="sxs-lookup"><span data-stu-id="08456-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="08456-121">顶点位置、 顶点的法向和三角形索引的数据包含在成员 SpatialSurfaceMeshBuffer 对象。</span><span class="sxs-lookup"><span data-stu-id="08456-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="08456-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx)包装网格数据的单一类型。</span><span class="sxs-lookup"><span data-stu-id="08456-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="08456-123">在开发时使用这些 Api 的应用程序，使基本程序流将如下所示 （如下面所述的示例应用程序中所示）：</span><span class="sxs-lookup"><span data-stu-id="08456-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="08456-124">**设置你 SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="08456-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="08456-125">调用[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)，以确保在用户给予应用程序以使用设备的空间的映射功能的权限。</span><span class="sxs-lookup"><span data-stu-id="08456-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="08456-126">实例化 SpatialSurfaceObserver 对象。</span><span class="sxs-lookup"><span data-stu-id="08456-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="08456-127">调用[SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx)来指定要在其中了解有关空间表面信息的空间的区域。</span><span class="sxs-lookup"><span data-stu-id="08456-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="08456-128">只需再次调用此函数，可以修改这些区域在将来。</span><span class="sxs-lookup"><span data-stu-id="08456-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="08456-129">使用指定每个区域[SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)。</span><span class="sxs-lookup"><span data-stu-id="08456-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="08456-130">注册，以便[ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)事件，该新信息，请查阅你指定的空间的区域中的空间表面时将触发事件。</span><span class="sxs-lookup"><span data-stu-id="08456-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="08456-131">**处理 ObservedSurfacesChanged 事件**</span><span class="sxs-lookup"><span data-stu-id="08456-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="08456-132">在事件处理程序中，调用[GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx)接收 SpatialSurfaceInfo 对象的映射。</span><span class="sxs-lookup"><span data-stu-id="08456-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="08456-133">使用此映射，可以更新你的记录的空间的图面的[用户的环境中存在](spatial-mapping.md#mesh-caching)。</span><span class="sxs-lookup"><span data-stu-id="08456-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="08456-134">对于每个 SpatialSurfaceInfo 对象，可能会查询[TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx)若要确定空间的扩展盘区的图面上，以表示[空间坐标系统](coordinate-systems.md)您选择。</span><span class="sxs-lookup"><span data-stu-id="08456-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="08456-135">如果您想请求空间面的网格，请调用[TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)。</span><span class="sxs-lookup"><span data-stu-id="08456-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="08456-136">你可能会提供选项指定所需的三角形，密度和返回的网格数据的格式。</span><span class="sxs-lookup"><span data-stu-id="08456-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="08456-137">**接收和处理网格**</span><span class="sxs-lookup"><span data-stu-id="08456-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="08456-138">TryComputeLatestMeshAsync 将 aysnchronously 每次调用返回一个 SpatialSurfaceMesh 对象。</span><span class="sxs-lookup"><span data-stu-id="08456-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="08456-139">从该对象可以访问包含的 SpatialSurfaceMeshBuffer 对象，若要访问的三角形索引、 顶点位置 （如果请求） 和网格的顶点法向。</span><span class="sxs-lookup"><span data-stu-id="08456-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="08456-140">此数据将会直接与兼容的格式[Direct3D 11 Api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx)用于呈现网格。</span><span class="sxs-lookup"><span data-stu-id="08456-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="08456-141">从此处你的应用程序可以根据需要执行分析或[处理](spatial-mapping.md#mesh-processing)的网格数据，并将其用于[呈现](spatial-mapping.md#rendering)及物理引擎[光线投射的细节和碰撞](spatial-mapping.md#raycasting-and-collision)。</span><span class="sxs-lookup"><span data-stu-id="08456-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="08456-142">一个重要的详细信息，请注意是，必须将规模应用于网格顶点位置 （例如在顶点着色器用于呈现网格后），来将它们转换从在其中它们存储在缓冲区中，为优化的整数单位计量。</span><span class="sxs-lookup"><span data-stu-id="08456-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="08456-143">可以通过调用来检索该刻度[VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)。</span><span class="sxs-lookup"><span data-stu-id="08456-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="08456-144">疑难解答</span><span class="sxs-lookup"><span data-stu-id="08456-144">Troubleshooting</span></span>
* <span data-ttu-id="08456-145">别忘了缩放在使用返回的小数位数的顶点着色器中的网格顶点位置[SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="08456-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="08456-146">空间映射的代码示例演练</span><span class="sxs-lookup"><span data-stu-id="08456-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="08456-147">[Holographic 空间映射](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)代码示例包括可用于开始加载到您的应用程序，其中包括用于管理基础结构的图面上的网格和呈现图面的网格的代码。</span><span class="sxs-lookup"><span data-stu-id="08456-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="08456-148">现在，我们了解如何将图面上映射功能添加到 DirectX 应用程序。</span><span class="sxs-lookup"><span data-stu-id="08456-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="08456-149">您可以将此代码添加到您[Windows 全息版的应用程序模板](creating-a-holographic-directx-project.md)项目，也可以继续浏览上面提到的代码示例。</span><span class="sxs-lookup"><span data-stu-id="08456-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="08456-150">此代码示例基于的 Windows 全息版的应用程序模板。</span><span class="sxs-lookup"><span data-stu-id="08456-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="08456-151">将您的应用程序设置为使用 spatialPerception 功能</span><span class="sxs-lookup"><span data-stu-id="08456-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="08456-152">您的应用程序必须能够使用空间的映射功能。</span><span class="sxs-lookup"><span data-stu-id="08456-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="08456-153">这是环境的必要的因为空间网格是环境的用户中，可能会被视为私有数据的表示形式。</span><span class="sxs-lookup"><span data-stu-id="08456-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="08456-154">声明此功能在您的应用程序的 package.appxmanifest 文件中。</span><span class="sxs-lookup"><span data-stu-id="08456-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="08456-155">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="08456-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="08456-156">功能是来自**uap2**命名空间。</span><span class="sxs-lookup"><span data-stu-id="08456-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="08456-157">若要访问此命名空间在清单中，将其作为包含*xlmns*属性中&lt;包 > 元素。</span><span class="sxs-lookup"><span data-stu-id="08456-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="08456-158">以下是一个示例：</span><span class="sxs-lookup"><span data-stu-id="08456-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="08456-159">检查空间映射功能支持</span><span class="sxs-lookup"><span data-stu-id="08456-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="08456-160">Windows Mixed Reality 支持范围广泛的设备，包括设备不支持空间映射。</span><span class="sxs-lookup"><span data-stu-id="08456-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="08456-161">如果您的应用程序可以使用空间的映射，也必须使用空间映射，以提供功能，它应检查以确保在尝试使用它之前受支持空间映射。</span><span class="sxs-lookup"><span data-stu-id="08456-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="08456-162">例如，如果空间映射为所需的混合的现实应用，它应显示一条消息以示意，如果用户尝试运行而无需空间的映射在设备上。</span><span class="sxs-lookup"><span data-stu-id="08456-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="08456-163">或者，您的应用程序可能会能够呈现其自身虚拟环境来代替用户的环境中，提供类似于可用空间的映射时，会发生什么情况的体验。</span><span class="sxs-lookup"><span data-stu-id="08456-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="08456-164">在任何情况下，此 API 允许你的应用需要注意的时它将不获取空间映射的数据并以适当方式做出响应。</span><span class="sxs-lookup"><span data-stu-id="08456-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="08456-165">若要检查空间映射支持当前的设备，首先请确保 UWP 协定是在级别 4 或更高版本，然后调用 SpatialSurfaceObserver::IsSupported()。</span><span class="sxs-lookup"><span data-stu-id="08456-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="08456-166">下面是如何执行此操作的上下文中[Holographic 空间映射](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)代码示例。</span><span class="sxs-lookup"><span data-stu-id="08456-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="08456-167">请求访问权限之前，只需检查支持。</span><span class="sxs-lookup"><span data-stu-id="08456-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="08456-168">可从 SDK 版本 15063 开始 SpatialSurfaceObserver::IsSupported() API。</span><span class="sxs-lookup"><span data-stu-id="08456-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="08456-169">如有必要，重新使用此 API 之前到平台版本 15063 项目作为目标。</span><span class="sxs-lookup"><span data-stu-id="08456-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="08456-170">请注意当 UWP 协定级别 4 少于时，应用应继续像该设备是能够执行空间映射。</span><span class="sxs-lookup"><span data-stu-id="08456-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="08456-171">请求对空间映射数据</span><span class="sxs-lookup"><span data-stu-id="08456-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="08456-172">您的应用程序需要请求尝试创建任何图面上观察者之前访问空间映射数据的权限。</span><span class="sxs-lookup"><span data-stu-id="08456-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="08456-173">下面是示例根据我们面映射的代码示例，提供更高版本在此页的更多详细信息：</span><span class="sxs-lookup"><span data-stu-id="08456-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="08456-174">创建图面上观察程序</span><span class="sxs-lookup"><span data-stu-id="08456-174">Create a surface observer</span></span>

<span data-ttu-id="08456-175">**Windows::Perception::Spatial::Surfaces**命名空间包括[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)类，该类在指定的一个或多个卷将观察[SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)。</span><span class="sxs-lookup"><span data-stu-id="08456-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="08456-176">使用[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)实时访问表面网格数据的实例。</span><span class="sxs-lookup"><span data-stu-id="08456-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="08456-177">从**AppMain.h**:</span><span class="sxs-lookup"><span data-stu-id="08456-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="08456-178">如在上一部分中所述，你必须在您的应用程序可以使用它之前请求对空间映射数据的访问。</span><span class="sxs-lookup"><span data-stu-id="08456-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="08456-179">HoloLens 上将自动授予此访问权限。</span><span class="sxs-lookup"><span data-stu-id="08456-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="08456-180">接下来，您需要配置要观察特定边界卷的图面上观察程序。</span><span class="sxs-lookup"><span data-stu-id="08456-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="08456-181">在这里，我们观察到 20 x 20 x 5 米为单位，以在坐标系统的原点为中心的框。</span><span class="sxs-lookup"><span data-stu-id="08456-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="08456-182">请注意，您可以改为设置多个边界的卷。</span><span class="sxs-lookup"><span data-stu-id="08456-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="08456-183">*这是伪代码：*</span><span class="sxs-lookup"><span data-stu-id="08456-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="08456-184">此外可以使用其他边界的形状-例如视图截锥或不是轴的边界框对齐。</span><span class="sxs-lookup"><span data-stu-id="08456-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="08456-185">*这是伪代码：*</span><span class="sxs-lookup"><span data-stu-id="08456-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="08456-186">如果您的应用程序需要执行任何操作以不同的方式，图面上映射数据不可用时，可以编写代码以响应这种情况其中[SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx)不是**允许**-例如，它将不允许在电脑上使用附加，因为这些设备没有空间映射的硬件的沉浸式设备。</span><span class="sxs-lookup"><span data-stu-id="08456-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="08456-187">对于这些设备，您应改为依赖于用户的环境和设备配置信息的空间阶段。</span><span class="sxs-lookup"><span data-stu-id="08456-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="08456-188">初始化和更新的表面网格集合</span><span class="sxs-lookup"><span data-stu-id="08456-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="08456-189">如果已成功创建图面上观察者，我们可以继续进行初始化我们表面网格的集合。</span><span class="sxs-lookup"><span data-stu-id="08456-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="08456-190">在这里，我们使用拉模型 API 立即获取当前观察到应用层协议集：</span><span class="sxs-lookup"><span data-stu-id="08456-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="08456-191">此外没有可用于获取表面网格数据推送模型。</span><span class="sxs-lookup"><span data-stu-id="08456-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="08456-192">你可以自由地设计应用以使用仅拉模型，如果您选择，在这种情况下您将轮询数据经常-说，一次每一帧的或在特定时间段，如游戏安装过程。</span><span class="sxs-lookup"><span data-stu-id="08456-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="08456-193">如果是这样，上面的代码中为所需内容。</span><span class="sxs-lookup"><span data-stu-id="08456-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="08456-194">在我们的代码示例中，我们选择演示这两种模型用于教学目的。</span><span class="sxs-lookup"><span data-stu-id="08456-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="08456-195">在这里，我们订阅一个事件以便接收最新的表面网格数据，只要系统识别更改。</span><span class="sxs-lookup"><span data-stu-id="08456-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="08456-196">我们的代码示例还配置为响应这些事件。</span><span class="sxs-lookup"><span data-stu-id="08456-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="08456-197">让我们演练一下如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="08456-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="08456-198">**注意：** 这可能不是您的应用程序来处理网格数据的最有效方法。</span><span class="sxs-lookup"><span data-stu-id="08456-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="08456-199">此代码编写为清楚起见，并没有进行优化。</span><span class="sxs-lookup"><span data-stu-id="08456-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="08456-200">中存储的只读映射提供的表面网格数据[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)对象使用[Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)作为键的值。</span><span class="sxs-lookup"><span data-stu-id="08456-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="08456-201">若要处理此数据，我们首先查找不在我们的集合中的密钥值。</span><span class="sxs-lookup"><span data-stu-id="08456-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="08456-202">本主题稍后将提供如何将数据存储在我们的示例应用程序的详细信息。</span><span class="sxs-lookup"><span data-stu-id="08456-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="08456-203">我们还必须删除图面上的网格中我们表面网格的集合，但不不再系统集合中。</span><span class="sxs-lookup"><span data-stu-id="08456-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="08456-204">若要执行此操作，我们需要执行类似的函数相反什么我们只介绍了用于添加和更新网格;我们在我们的应用程序的集合，并检查是否循环**Guid**我们有系统集合中。</span><span class="sxs-lookup"><span data-stu-id="08456-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="08456-205">如果不是系统集合中，我们可以从我们的愿景删除它。</span><span class="sxs-lookup"><span data-stu-id="08456-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="08456-206">从我们 AppMain.cpp 中的事件处理程序：</span><span class="sxs-lookup"><span data-stu-id="08456-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="08456-207">网格中 RealtimeSurfaceMeshRenderer.cpp 修剪的实现：</span><span class="sxs-lookup"><span data-stu-id="08456-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="08456-208">获取和使用表面网格数据缓冲区</span><span class="sxs-lookup"><span data-stu-id="08456-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="08456-209">获得的表面网格信息很简单，只提取的数据集合并处理对该集合的更新。</span><span class="sxs-lookup"><span data-stu-id="08456-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="08456-210">现在，我们将详细介绍如何使用数据。</span><span class="sxs-lookup"><span data-stu-id="08456-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="08456-211">在代码示例中，我们选择要用于呈现图面上的网格。</span><span class="sxs-lookup"><span data-stu-id="08456-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="08456-212">这是实际的图面后面 occluding 全息的常见方案。</span><span class="sxs-lookup"><span data-stu-id="08456-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="08456-213">此外可以呈现网格、 设置或呈现其处理的版本，若要向用户显示哪些领域的房间扫描之前提供的应用或游戏的功能。</span><span class="sxs-lookup"><span data-stu-id="08456-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="08456-214">当它收到来自我们在上一部分中所述的事件处理程序表面网格更新时，代码示例启动进程。</span><span class="sxs-lookup"><span data-stu-id="08456-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="08456-215">此函数中的代码的重要行是调用以更新图面*mesh*： 此时我们已经处理网格的信息，并且我们正准备我们认为适合用于获取顶点和索引数据。</span><span class="sxs-lookup"><span data-stu-id="08456-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="08456-216">From RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="08456-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="08456-217">设计我们的示例代码，以便数据类， **SurfaceMesh**、 句柄网格数据处理和呈现。</span><span class="sxs-lookup"><span data-stu-id="08456-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="08456-218">这些网格是什么**RealtimeSurfaceMeshRenderer**实际保留的映射。</span><span class="sxs-lookup"><span data-stu-id="08456-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="08456-219">每个采用其来源的 SpatialSurfaceMesh 的引用，我们用它任何时候，我们需要访问网格顶点或索引缓冲区，或获取的网格的转换。</span><span class="sxs-lookup"><span data-stu-id="08456-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="08456-220">现在，我们的标记为需要更新网格。</span><span class="sxs-lookup"><span data-stu-id="08456-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="08456-221">从 SurfaceMesh.cpp:</span><span class="sxs-lookup"><span data-stu-id="08456-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="08456-222">网格要求进行自我绘制下, 一次将首先检查该标志。</span><span class="sxs-lookup"><span data-stu-id="08456-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="08456-223">如果需要更新，将在 GPU 上更新顶点和索引缓冲区。</span><span class="sxs-lookup"><span data-stu-id="08456-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="08456-224">首先，我们获取原始数据缓冲区：</span><span class="sxs-lookup"><span data-stu-id="08456-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="08456-225">然后，我们使用提供的 HoloLens 网格数据创建 Direct3D 设备缓冲区：</span><span class="sxs-lookup"><span data-stu-id="08456-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="08456-226">**注意：** 上一代码片段中使用 CreateDirectXBuffer 帮助器函数，请参阅图面映射代码示例：SurfaceMesh.cpp，GetDataFromIBuffer.h。</span><span class="sxs-lookup"><span data-stu-id="08456-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="08456-227">现在设备资源创建操作完成，并在网格视为已加载并准备好进行更新和呈现。</span><span class="sxs-lookup"><span data-stu-id="08456-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="08456-228">更新和呈现图面上的网格</span><span class="sxs-lookup"><span data-stu-id="08456-228">Update and render surface meshes</span></span>

<span data-ttu-id="08456-229">我们 SurfaceMesh 类有一个专用的更新函数。</span><span class="sxs-lookup"><span data-stu-id="08456-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="08456-230">每个[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)具有自己的转换，并且我们的示例使用的当前坐标系我们**SpatialStationaryReferenceFrame**获取转换。</span><span class="sxs-lookup"><span data-stu-id="08456-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="08456-231">然后它会更新在 GPU 上的模型常量缓冲区。</span><span class="sxs-lookup"><span data-stu-id="08456-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="08456-232">时间来呈现图面上的网格时，我们做一些准备工作之前呈现集合。</span><span class="sxs-lookup"><span data-stu-id="08456-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="08456-233">我们设置当前呈现配置着色器管道和我们设置输入装配器阶段。</span><span class="sxs-lookup"><span data-stu-id="08456-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="08456-234">请注意，holographic 照相机帮助器类**CameraResources.cpp**已设置了视图/投影常量缓冲区目前为止。</span><span class="sxs-lookup"><span data-stu-id="08456-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="08456-235">从**RealtimeSurfaceMeshRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="08456-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="08456-236">完成此操作后，我们在我们的网格上循环，并告知每个要绘制自身。</span><span class="sxs-lookup"><span data-stu-id="08456-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="08456-237">**注意：** 此示例代码未被优化为使用任何种类的截锥消除，但应在您的应用程序中包括此功能。</span><span class="sxs-lookup"><span data-stu-id="08456-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="08456-238">单个网格负责设置顶点和索引缓冲区、 stride 和模型转换常量缓冲区。</span><span class="sxs-lookup"><span data-stu-id="08456-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="08456-239">与 Windows 全息版的应用程序模板的旋转多维数据集，我们呈现到立体缓冲区使用实例化。</span><span class="sxs-lookup"><span data-stu-id="08456-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="08456-240">从**SurfaceMesh::Draw**:</span><span class="sxs-lookup"><span data-stu-id="08456-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="08456-241">呈现图面映射选项</span><span class="sxs-lookup"><span data-stu-id="08456-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="08456-242">映射面代码示例提供了代码来仅限封闭的呈现的表面网格数据和屏幕上呈现的表面网格的数据。</span><span class="sxs-lookup"><span data-stu-id="08456-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="08456-243">你选择哪个路径-或同时-取决于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="08456-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="08456-244">我们将通过本文档中的这两种配置。</span><span class="sxs-lookup"><span data-stu-id="08456-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="08456-245">**Holographic 效果的呈现封闭缓冲区**</span><span class="sxs-lookup"><span data-stu-id="08456-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="08456-246">首先清除当前的虚拟照相机呈现目标视图。</span><span class="sxs-lookup"><span data-stu-id="08456-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="08456-247">从 AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="08456-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="08456-248">这是"预呈现"传递。</span><span class="sxs-lookup"><span data-stu-id="08456-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="08456-249">在这里，我们通过要求的网格呈现器呈现仅深度创建封闭缓冲区。</span><span class="sxs-lookup"><span data-stu-id="08456-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="08456-250">在此配置中，我们不附加呈现目标视图和网格呈现器将像素着色器阶段设置为**nullptr** ，以便在 GPU 不会绘制像素。</span><span class="sxs-lookup"><span data-stu-id="08456-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="08456-251">几何图形将光栅化到深度缓冲区，并且图形管道将就此止步。</span><span class="sxs-lookup"><span data-stu-id="08456-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="08456-252">我们可以使用一个额外的深度测试针对映射图面封闭缓冲区绘制全息。</span><span class="sxs-lookup"><span data-stu-id="08456-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="08456-253">在此代码示例中，我们呈现像素在多维数据集中不同的颜色如果它们位于图面。</span><span class="sxs-lookup"><span data-stu-id="08456-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="08456-254">从 AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="08456-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="08456-255">基于从 SpecialEffectPixelShader.hlsl 代码：</span><span class="sxs-lookup"><span data-stu-id="08456-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="08456-256">**注意：** 对于我们**GatherDepthLess**例程，请参阅图面映射代码示例：SpecialEffectPixelShader.hlsl。</span><span class="sxs-lookup"><span data-stu-id="08456-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="08456-257">**呈现图面上的网格的显示的数据**</span><span class="sxs-lookup"><span data-stu-id="08456-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="08456-258">我们可以直接绘制到立体声显示缓冲区的图面上的网格。</span><span class="sxs-lookup"><span data-stu-id="08456-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="08456-259">我们选择了要绘制了照明，完整的人脸，但您可以自由地绘制线框、 处理之前呈现的网格、 应用纹理贴图，等等。</span><span class="sxs-lookup"><span data-stu-id="08456-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="08456-260">在这里，我们的代码示例指示要绘制集合的网格呈现器。</span><span class="sxs-lookup"><span data-stu-id="08456-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="08456-261">这一次我们未指定一个仅限深度的传递，因此它将附加像素着色器，并完成呈现管道为当前的虚拟照相机使用我们指定的目标。</span><span class="sxs-lookup"><span data-stu-id="08456-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a><span data-ttu-id="08456-262">请参阅</span><span class="sxs-lookup"><span data-stu-id="08456-262">See also</span></span>
* [<span data-ttu-id="08456-263">创建全息版的 DirectX 项目</span><span class="sxs-lookup"><span data-stu-id="08456-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="08456-264">Windows.Perception.Spatial API</span><span class="sxs-lookup"><span data-stu-id="08456-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
