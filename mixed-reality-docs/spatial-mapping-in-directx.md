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
# <a name="spatial-mapping-in-directx"></a>在 DirectX 空间映射

本主题介绍如何实现[空间映射](spatial-mapping.md)DirectX 应用程序中。 这包括使用通用 Windows 平台 SDK 附带的空间映射示例应用程序的详细的说明。

本主题使用来自代码[HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 的代码示例。

>[!NOTE]
>这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。  这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。

## <a name="directx-development-overview"></a>DirectX 开发概述

空间映射的本机应用程序开发使用 Api 下的[Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)命名空间。 这些 Api 提供了空间映射中的功能，以直接类似于的空间的映射公开的 Api 完全控制[Unity](spatial-mapping-in-unity.md)。

### <a name="perception-apis"></a>Perception Api

为空间映射开发提供的主类型如下所示：
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)提供有关应用程序指定的空间中的 SpatialSurfaceInfo 对象形式的用户附近的区域中显示的信息。
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)介绍一个现有空间图面，包括的唯一 ID、 边界卷以及上次更改的时间。 它将提供 SpatialSurfaceMesh 以异步方式根据请求。
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx)包含用于自定义所请求的 SpatialSurfaceInfo SpatialSurfaceMesh 对象参数。
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)表示单一的空间表面的网格数据。 顶点位置、 顶点的法向和三角形索引的数据包含在成员 SpatialSurfaceMeshBuffer 对象。
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx)包装网格数据的单一类型。

在开发时使用这些 Api 的应用程序，使基本程序流将如下所示 （如下面所述的示例应用程序中所示）：
- **设置你 SpatialSurfaceObserver**
  - 调用[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)，以确保在用户给予应用程序以使用设备的空间的映射功能的权限。
  - 实例化 SpatialSurfaceObserver 对象。
  - 调用[SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx)来指定要在其中了解有关空间表面信息的空间的区域。 只需再次调用此函数，可以修改这些区域在将来。 使用指定每个区域[SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)。
  - 注册，以便[ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)事件，该新信息，请查阅你指定的空间的区域中的空间表面时将触发事件。
- **处理 ObservedSurfacesChanged 事件**
  - 在事件处理程序中，调用[GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx)接收 SpatialSurfaceInfo 对象的映射。 使用此映射，可以更新你的记录的空间的图面的[用户的环境中存在](spatial-mapping.md#mesh-caching)。
  - 对于每个 SpatialSurfaceInfo 对象，可能会查询[TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx)若要确定空间的扩展盘区的图面上，以表示[空间坐标系统](coordinate-systems.md)您选择。
  - 如果您想请求空间面的网格，请调用[TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)。 你可能会提供选项指定所需的三角形，密度和返回的网格数据的格式。
- **接收和处理网格**
  - TryComputeLatestMeshAsync 将 aysnchronously 每次调用返回一个 SpatialSurfaceMesh 对象。
  - 从该对象可以访问包含的 SpatialSurfaceMeshBuffer 对象，若要访问的三角形索引、 顶点位置 （如果请求） 和网格的顶点法向。 此数据将会直接与兼容的格式[Direct3D 11 Api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx)用于呈现网格。
  - 从此处你的应用程序可以根据需要执行分析或[处理](spatial-mapping.md#mesh-processing)的网格数据，并将其用于[呈现](spatial-mapping.md#rendering)及物理引擎[光线投射的细节和碰撞](spatial-mapping.md#raycasting-and-collision)。
  - 一个重要的详细信息，请注意是，必须将规模应用于网格顶点位置 （例如在顶点着色器用于呈现网格后），来将它们转换从在其中它们存储在缓冲区中，为优化的整数单位计量。 可以通过调用来检索该刻度[VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)。

### <a name="troubleshooting"></a>疑难解答
* 别忘了缩放在使用返回的小数位数的顶点着色器中的网格顶点位置[SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>空间映射的代码示例演练

[Holographic 空间映射](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)代码示例包括可用于开始加载到您的应用程序，其中包括用于管理基础结构的图面上的网格和呈现图面的网格的代码。

现在，我们了解如何将图面上映射功能添加到 DirectX 应用程序。 您可以将此代码添加到您[Windows 全息版的应用程序模板](creating-a-holographic-directx-project.md)项目，也可以继续浏览上面提到的代码示例。 此代码示例基于的 Windows 全息版的应用程序模板。

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>将您的应用程序设置为使用 spatialPerception 功能

您的应用程序必须能够使用空间的映射功能。 这是环境的必要的因为空间网格是环境的用户中，可能会被视为私有数据的表示形式。 声明此功能在您的应用程序的 package.appxmanifest 文件中。 以下是一个示例：

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

功能是来自**uap2**命名空间。 若要访问此命名空间在清单中，将其作为包含*xlmns*属性中&lt;包 > 元素。 以下是一个示例：

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>检查空间映射功能支持

Windows Mixed Reality 支持范围广泛的设备，包括设备不支持空间映射。 如果您的应用程序可以使用空间的映射，也必须使用空间映射，以提供功能，它应检查以确保在尝试使用它之前受支持空间映射。 例如，如果空间映射为所需的混合的现实应用，它应显示一条消息以示意，如果用户尝试运行而无需空间的映射在设备上。 或者，您的应用程序可能会能够呈现其自身虚拟环境来代替用户的环境中，提供类似于可用空间的映射时，会发生什么情况的体验。 在任何情况下，此 API 允许你的应用需要注意的时它将不获取空间映射的数据并以适当方式做出响应。

若要检查空间映射支持当前的设备，首先请确保 UWP 协定是在级别 4 或更高版本，然后调用 SpatialSurfaceObserver::IsSupported()。 下面是如何执行此操作的上下文中[Holographic 空间映射](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)代码示例。 请求访问权限之前，只需检查支持。

可从 SDK 版本 15063 开始 SpatialSurfaceObserver::IsSupported() API。 如有必要，重新使用此 API 之前到平台版本 15063 项目作为目标。

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

请注意当 UWP 协定级别 4 少于时，应用应继续像该设备是能够执行空间映射。

### <a name="request-access-to-spatial-mapping-data"></a>请求对空间映射数据

您的应用程序需要请求尝试创建任何图面上观察者之前访问空间映射数据的权限。 下面是示例根据我们面映射的代码示例，提供更高版本在此页的更多详细信息：

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

### <a name="create-a-surface-observer"></a>创建图面上观察程序

**Windows::Perception::Spatial::Surfaces**命名空间包括[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)类，该类在指定的一个或多个卷将观察[SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)。 使用[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)实时访问表面网格数据的实例。

从**AppMain.h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

如在上一部分中所述，你必须在您的应用程序可以使用它之前请求对空间映射数据的访问。 HoloLens 上将自动授予此访问权限。

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

接下来，您需要配置要观察特定边界卷的图面上观察程序。 在这里，我们观察到 20 x 20 x 5 米为单位，以在坐标系统的原点为中心的框。

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

请注意，您可以改为设置多个边界的卷。

*这是伪代码：*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

此外可以使用其他边界的形状-例如视图截锥或不是轴的边界框对齐。

*这是伪代码：*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

如果您的应用程序需要执行任何操作以不同的方式，图面上映射数据不可用时，可以编写代码以响应这种情况其中[SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx)不是**允许**-例如，它将不允许在电脑上使用附加，因为这些设备没有空间映射的硬件的沉浸式设备。 对于这些设备，您应改为依赖于用户的环境和设备配置信息的空间阶段。

### <a name="initialize-and-update-the-surface-mesh-collection"></a>初始化和更新的表面网格集合

如果已成功创建图面上观察者，我们可以继续进行初始化我们表面网格的集合。 在这里，我们使用拉模型 API 立即获取当前观察到应用层协议集：

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

此外没有可用于获取表面网格数据推送模型。 你可以自由地设计应用以使用仅拉模型，如果您选择，在这种情况下您将轮询数据经常-说，一次每一帧的或在特定时间段，如游戏安装过程。 如果是这样，上面的代码中为所需内容。

在我们的代码示例中，我们选择演示这两种模型用于教学目的。 在这里，我们订阅一个事件以便接收最新的表面网格数据，只要系统识别更改。

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

我们的代码示例还配置为响应这些事件。 让我们演练一下如何执行此操作。

**注意：** 这可能不是您的应用程序来处理网格数据的最有效方法。 此代码编写为清楚起见，并没有进行优化。

中存储的只读映射提供的表面网格数据[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)对象使用[Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)作为键的值。

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

若要处理此数据，我们首先查找不在我们的集合中的密钥值。 本主题稍后将提供如何将数据存储在我们的示例应用程序的详细信息。

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

我们还必须删除图面上的网格中我们表面网格的集合，但不不再系统集合中。 若要执行此操作，我们需要执行类似的函数相反什么我们只介绍了用于添加和更新网格;我们在我们的应用程序的集合，并检查是否循环**Guid**我们有系统集合中。 如果不是系统集合中，我们可以从我们的愿景删除它。

从我们 AppMain.cpp 中的事件处理程序：

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

网格中 RealtimeSurfaceMeshRenderer.cpp 修剪的实现：

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>获取和使用表面网格数据缓冲区

获得的表面网格信息很简单，只提取的数据集合并处理对该集合的更新。 现在，我们将详细介绍如何使用数据。

在代码示例中，我们选择要用于呈现图面上的网格。 这是实际的图面后面 occluding 全息的常见方案。 此外可以呈现网格、 设置或呈现其处理的版本，若要向用户显示哪些领域的房间扫描之前提供的应用或游戏的功能。

当它收到来自我们在上一部分中所述的事件处理程序表面网格更新时，代码示例启动进程。 此函数中的代码的重要行是调用以更新图面*mesh*： 此时我们已经处理网格的信息，并且我们正准备我们认为适合用于获取顶点和索引数据。

From RealtimeSurfaceMeshRenderer.cpp:

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

设计我们的示例代码，以便数据类， **SurfaceMesh**、 句柄网格数据处理和呈现。 这些网格是什么**RealtimeSurfaceMeshRenderer**实际保留的映射。 每个采用其来源的 SpatialSurfaceMesh 的引用，我们用它任何时候，我们需要访问网格顶点或索引缓冲区，或获取的网格的转换。 现在，我们的标记为需要更新网格。

从 SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

网格要求进行自我绘制下, 一次将首先检查该标志。 如果需要更新，将在 GPU 上更新顶点和索引缓冲区。

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

首先，我们获取原始数据缓冲区：

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

然后，我们使用提供的 HoloLens 网格数据创建 Direct3D 设备缓冲区：

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

**注意：** 上一代码片段中使用 CreateDirectXBuffer 帮助器函数，请参阅图面映射代码示例：SurfaceMesh.cpp，GetDataFromIBuffer.h。 现在设备资源创建操作完成，并在网格视为已加载并准备好进行更新和呈现。

### <a name="update-and-render-surface-meshes"></a>更新和呈现图面上的网格

我们 SurfaceMesh 类有一个专用的更新函数。 每个[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)具有自己的转换，并且我们的示例使用的当前坐标系我们**SpatialStationaryReferenceFrame**获取转换。 然后它会更新在 GPU 上的模型常量缓冲区。

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

时间来呈现图面上的网格时，我们做一些准备工作之前呈现集合。 我们设置当前呈现配置着色器管道和我们设置输入装配器阶段。 请注意，holographic 照相机帮助器类**CameraResources.cpp**已设置了视图/投影常量缓冲区目前为止。

从**RealtimeSurfaceMeshRenderer::Render**:

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

完成此操作后，我们在我们的网格上循环，并告知每个要绘制自身。 **注意：** 此示例代码未被优化为使用任何种类的截锥消除，但应在您的应用程序中包括此功能。

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

单个网格负责设置顶点和索引缓冲区、 stride 和模型转换常量缓冲区。 与 Windows 全息版的应用程序模板的旋转多维数据集，我们呈现到立体缓冲区使用实例化。

从**SurfaceMesh::Draw**:

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

### <a name="rendering-choices-with-surface-mapping"></a>呈现图面映射选项

映射面代码示例提供了代码来仅限封闭的呈现的表面网格数据和屏幕上呈现的表面网格的数据。 你选择哪个路径-或同时-取决于你的应用程序。 我们将通过本文档中的这两种配置。

**Holographic 效果的呈现封闭缓冲区**

首先清除当前的虚拟照相机呈现目标视图。

从 AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

这是"预呈现"传递。 在这里，我们通过要求的网格呈现器呈现仅深度创建封闭缓冲区。 在此配置中，我们不附加呈现目标视图和网格呈现器将像素着色器阶段设置为**nullptr** ，以便在 GPU 不会绘制像素。 几何图形将光栅化到深度缓冲区，并且图形管道将就此止步。

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

我们可以使用一个额外的深度测试针对映射图面封闭缓冲区绘制全息。 在此代码示例中，我们呈现像素在多维数据集中不同的颜色如果它们位于图面。

从 AppMain.cpp:

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

基于从 SpecialEffectPixelShader.hlsl 代码：

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

**注意：** 对于我们**GatherDepthLess**例程，请参阅图面映射代码示例：SpecialEffectPixelShader.hlsl。

**呈现图面上的网格的显示的数据**

我们可以直接绘制到立体声显示缓冲区的图面上的网格。 我们选择了要绘制了照明，完整的人脸，但您可以自由地绘制线框、 处理之前呈现的网格、 应用纹理贴图，等等。

在这里，我们的代码示例指示要绘制集合的网格呈现器。 这一次我们未指定一个仅限深度的传递，因此它将附加像素着色器，并完成呈现管道为当前的虚拟照相机使用我们指定的目标。

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

## <a name="see-also"></a>请参阅
* [创建全息版的 DirectX 项目](creating-a-holographic-directx-project.md)
* [Windows.Perception.Spatial API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
