---
title: DirectX 中的空间映射
description: 介绍如何在 DirectX 应用中实现空间映射。 这包括通用 Windows 平台 SDK 随附的空间映射示例应用程序的详细说明。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed reality, 空间映射, 环境, 交互, directx, winrt, api, 示例代码, UWP, SDK, 演练
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550697"
---
# <a name="spatial-mapping-in-directx"></a>DirectX 中的空间映射

本主题介绍如何在 DirectX 应用中实现[空间映射](spatial-mapping.md)。 这包括通用 Windows 平台 SDK 随附的空间映射示例应用程序的详细说明。

本主题使用[HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 代码示例中的代码。

>[!NOTE]
>本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT, 这与全息项目模板中使用的不同。  概念对于C++/WinRT 项目是等效的, 但你将需要转换代码。

## <a name="directx-development-overview"></a>DirectX 开发概述

空间映射的本机应用程序开发使用[Windows 感知](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)命名空间下的 api。 这些 Api 提供完全控制空间映射功能, 其方式与[Unity](spatial-mapping-in-unity.md)公开的空间映射 api 直接类似。

### <a name="perception-apis"></a>感知 Api

为空间映射开发提供的主要类型如下:
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)以 SpatialSurfaceInfo 对象的形式提供与用户附近的应用程序指定区域中的表面相关的信息。
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)描述单个存在空间图面, 包括唯一 ID、边界量和上次更改时间。 它将根据请求异步提供 SpatialSurfaceMesh。
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx)包含用于自定义 SpatialSurfaceInfo 中请求的 SpatialSurfaceMesh 对象的参数。
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)表示单个空间图面的网格数据。 顶点位置、顶点法线和三角索引的数据包含在 member SpatialSurfaceMeshBuffer 对象中。
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx)环绕一种类型的网格数据。

当使用这些 Api 开发应用程序时, 基本程序流将如下所示 (如下面所述的示例应用程序所示):
- **设置 SpatialSurfaceObserver**
  - 调用[RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), 以确保用户为应用程序提供了使用设备的空间映射功能的权限。
  - 实例化 SpatialSurfaceObserver 对象。
  - 调用[SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx)可指定要在其中显示空间图面信息的区域。 您可以在以后修改这些区域, 只需再次调用此函数。 每个区域都是使用[SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)指定的。
  - 注册[ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)事件, 每当有新信息可用于指定空间区域中的空间图面时, 将触发该事件。
- **处理 ObservedSurfacesChanged 事件**
  - 在事件处理程序中, 调用[GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx)来接收 SpatialSurfaceInfo 对象的映射。 使用此地图, 可以更新[用户环境中存在](spatial-mapping.md#mesh-caching)的空间表面的记录。
  - 对于每个 SpatialSurfaceInfo 对象, 可以通过查询[TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx)来确定图面的空间范围, 用所选的[空间坐标系统](coordinate-systems.md)表示。
  - 如果决定为空间图面请求网格, 请调用[TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)。 您可以提供选项来指定所需的三角形密度和返回的网格数据的格式。
- **接收和处理网格**
  - 对 TryComputeLatestMeshAsync 的每次调用都将 aysnchronously 返回一个 SpatialSurfaceMesh 对象。
  - 从此对象, 您可以访问包含的 SpatialSurfaceMeshBuffer 对象, 以便访问该网格的三角形索引、顶点位置和 (如果请求) 顶点法线。 此数据将采用与用于呈现网格的[Direct3D 11 api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx)直接兼容的格式。
  - 从这里, 你的应用程序可以选择执行网格数据的分析或[处理](spatial-mapping.md#mesh-processing), 并将其用于[呈现](spatial-mapping.md#rendering)和物理学[raycasting 和冲突](spatial-mapping.md#raycasting-and-collision)。
  - 需要注意的一个重要细节是, 您必须将一个规模应用于网格顶点位置 (例如, 在用于呈现网格的顶点着色器中), 以便将它们从缓冲区中存储的优化整数单位转换为米。 可以通过调用[VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)来检索此缩放。

### <a name="troubleshooting"></a>疑难解答
* 别忘了使用 SpatialSurfaceMesh 返回的刻度在顶点着色器中缩放网格顶点位置[。 VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>空间映射代码示例

[全息空间映射](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)代码示例包含可用于开始将 surface 网格加载到应用中的代码, 其中包括用于管理和呈现 surface 网格的基础结构。

现在, 我们将演练如何向 DirectX 应用程序添加 surface 映射功能。 您可以将此代码添加到您的[Windows 全息应用程序模板](creating-a-holographic-directx-project.md)项目, 也可以通过浏览上面提到的代码示例来执行此操作。 此代码示例基于 Windows 全息应用程序模板。

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>设置应用程序以使用 spatialPerception 功能

您的应用程序必须能够使用空间映射功能。 这是必需的, 因为空间网格是用户环境的表示形式, 该环境可能被视为私有数据。 在应用程序的 appxmanifest.xml 文件中声明此功能。 以下是一个示例：

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

此功能来自**uap2**命名空间。 若要在清单中获取此命名空间的访问权限, 请将其包含为&lt;包 > 元素中的 xlmns 属性。 以下是一个示例：

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

Windows Mixed Reality 支持多种设备, 包括不支持空间映射的设备。 如果你的应用程序可以使用空间映射, 或者必须使用空间映射来提供功能, 则在尝试使用空间映射之前应进行检查以确保其受支持。 例如, 如果你的混合现实应用需要空间映射, 则当用户尝试在不使用空间映射的设备上运行该应用程序时, 它应会显示一条消息。 或者, 你的应用程序可能能够呈现自己的虚拟环境来代替用户的环境, 提供的体验与在空间映射可用时所发生的情况类似。 在任何情况下, 此 API 都允许你的应用程序在不获取空间映射数据的情况下进行识别, 并以适当的方式做出响应。

若要检查当前设备的空间映射支持, 请首先确保 UWP 协定处于级别4或更高级别, 然后调用 SpatialSurfaceObserver:: IsSupported ()。 下面介绍了如何在[全息空间映射](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)代码示例的上下文中执行此操作。 请求访问之前, 只需检查支持。

从 SDK 版本15063开始, 可以使用 SpatialSurfaceObserver:: IsSupported () API。 如有必要, 请在使用此 API 之前将项目重定向到平台15063版。

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

请注意, 当 UWP 协定小于级别4时, 应用程序应继续执行, 就像设备能够进行空间映射一样。

### <a name="request-access-to-spatial-mapping-data"></a>请求访问空间映射数据

在尝试创建任何 surface 观察器之前, 应用需要请求访问空间映射数据的权限。 下面是一个基于我们的图面映射代码示例的示例, 本页面后面提供了更多详细信息:

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

### <a name="create-a-surface-observer"></a>创建 surface 观察器

**Windows::P erception:: 空间::** surface 命名空间包括[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)类, 该类用于观察在[SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)中指定的一个或多个卷。 使用[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)实例实时访问 surface 网格数据。

从**AppMain**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

如前一部分所述, 必须先请求对空间映射数据的访问权限, 然后应用才能使用。 此访问权限是在 HoloLens 上自动授予的。

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

接下来, 需要配置 surface 观察器来观察特定的边界卷。 在这里, 我们看到一个20x20x5 计量的框, 该框以坐标系统的原点为中心。

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

请注意, 可以改为设置多个范围卷。

*这是伪代码:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

还可以使用其他边界形状 (如视图 "截锥") 或不是轴对齐的边界框。

*这是伪代码:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

如果你的应用程序在表面映射数据不可用时需要执行任何操作, 则可以编写代码来响应不**允许**使用[SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx)的情况 (例如, 在具有沉浸功能的电脑上不允许这样做)。附加设备, 因为这些设备没有用于空间映射的硬件。 对于这些设备, 你应改用空间阶段来了解有关用户的环境和设备配置的信息。

### <a name="initialize-and-update-the-surface-mesh-collection"></a>初始化和更新 surface 网格集合

如果已成功创建 surface 观察程序, 我们可以继续初始化我们的 surface 网格集合。 在这里, 我们使用提取模型 API 立即获取当前观察到的曲面集:

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

还有一个可用于获取 surface 网格数据的推送模型。 如果你选择, 则可以自由地将应用程序设计为仅使用请求模型, 在这种情况下, 将每隔一帧 (例如, 每帧一次) 或在特定时间段 (例如游戏安装期间) 轮询数据。 如果是这样, 则需要用到上述代码。

在我们的代码示例中, 我们选择了使用这两种模型来实现除教学之外目的。 在这里, 我们将订阅事件, 以便在系统识别更改时接收最新的 surface 网格数据。

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

我们的代码示例还配置为响应这些事件。 我们来看看如何实现此目的。

**注意：** 这可能不是你的应用程序处理网格数据的最有效方法。 此代码为清楚起见编写, 未进行优化。

在存储使用[Platform:: guid](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)作为键值的[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)对象的只读映射中提供了 surface 网格数据。

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

为了处理此数据, 我们首先查找集合中不是的键值。 本主题稍后将介绍如何将数据存储在示例应用中的详细信息。

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

我们还必须删除 surface 网格集合中的表面网格, 但不再存在于系统集合中。 为此, 我们需要执行类似于我们刚刚为添加和更新网格而显示的内容的操作;我们会循环访问应用的集合, 并查看系统集合中是否存在**Guid** 。 如果不在系统集合中, 我们会将其删除。

通过 AppMain 中的事件处理程序:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

RealtimeSurfaceMeshRenderer 中的网格修剪实现:

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>获取和使用 surface 网格数据缓冲区

获取 surface 网格信息非常简单, 只需将数据收集和处理更新到该集合。 现在, 我们将详细介绍如何使用数据。

在我们的代码示例中, 我们选择使用 surface 网格进行呈现。 这是在真实表面上 occluding 全息影像的常见方案。 你还可以呈现网格, 或呈现这些网格的已处理版本, 以便在开始提供应用或游戏功能之前向用户显示房间的扫描区域。

当从我们在上一节中介绍的事件处理程序接收 surface 网格更新时, 代码示例将启动进程。 此函数中的重要代码行是更新 surface*网格*的调用: 这次, 我们已经处理了网格信息, 我们即将获取用于显示的顶点和索引数据。

从 RealtimeSurfaceMeshRenderer:

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

我们的示例代码旨在使数据类**SurfaceMesh**处理网格数据处理和呈现。 这些网格是**RealtimeSurfaceMeshRenderer**实际保存地图的内容。 每个帐户都有一个对其来源的 SpatialSurfaceMesh 的引用, 我们随时使用它来访问网格顶点或索引缓冲区, 或者获取网格的转换。 现在, 我们将网格标记为需要更新。

从 SurfaceMesh:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

下一次要求网格绘制自身时, 它将首先检查标志。 如果需要更新, 则会在 GPU 上更新顶点和索引缓冲区。

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

首先, 我们获取原始数据缓冲区:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

然后, 使用 HoloLens 提供的网格数据创建 Direct3D 设备缓冲区:

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

**注意：** 有关上一代码片段中使用的 CreateDirectXBuffer helper 函数, 请参阅 Surface Mapping 代码示例:SurfaceMesh, GetDataFromIBuffer。 现在, 设备资源创建已完成, 并且网格被视为已加载并准备好进行更新和呈现。

### <a name="update-and-render-surface-meshes"></a>更新和呈现 surface 网格

我们的 SurfaceMesh 类具有专用的更新函数。 每个[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx)都有其自己的转换, 我们的示例使用**SpatialStationaryReferenceFrame**的当前坐标系统来获取转换。 然后, 它会更新 GPU 上的模型常量缓冲区。

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

当需要呈现 surface 网格时, 请在呈现集合之前做一些准备工作。 我们为当前呈现配置设置着色器管道, 并设置 "输入组装器" 阶段。 请注意, 全息相机帮助程序类**CameraResources**现在已经设置了视图/投影常量缓冲区。

From **RealtimeSurfaceMeshRenderer:: Render**:

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

完成此操作后, 我们将在网格上循环, 并告诉每个网格自行绘制。 **注意：** 此示例代码未经过优化, 无法使用任何种类的截锥剔除, 但你应在应用程序中包括此功能。

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

单个网格负责设置顶点和索引缓冲区、步幅和模型转换常量缓冲区。 与 Windows 全息应用程序模板中的旋转多维数据集一样, 我们使用实例化来 stereoscopic 缓冲区。

From **SurfaceMesh::D raw**:

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

### <a name="rendering-choices-with-surface-mapping"></a>用图面映射呈现选项

外围应用程序代码示例提供了用于封闭呈现 surface 网格数据的代码, 以及用于在屏幕上呈现 surface 网格数据的代码。 选择的路径 (或两者) 取决于应用程序。 我们将在本文档中逐步介绍这两种配置。

**呈现全息效果的封闭缓冲区**

首先, 清除当前虚拟摄像机的呈现目标视图。

从 AppMain:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

这是一个 "预渲染" 阶段。 在这里, 我们将通过请求网格呈现器来仅呈现深度来创建封闭缓冲区。 在此配置中, 我们不会附加 "呈现目标" 视图, 并且网格呈现器会将 "像素着色器" 阶段设置为**nullptr** , 以便 GPU 不必消耗像素。 几何将栅格化到深度缓冲区, 图形管道将停止。

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

我们可以使用针对图面映射封闭缓冲区的额外深度测试来绘制全息影像。 在此代码示例中, 如果多维数据集位于图面后面, 则将其呈现为不同的颜色。

从 AppMain:

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

基于 SpecialEffectPixelShader 中的代码。 hlsl:

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

**注意：** 对于我们的**GatherDepthLess**例程, 请参阅图:SpecialEffectPixelShader. hlsl。

**向显示器呈现 surface 网格数据**

我们还可以将表面网格绘制到立体声显示缓冲区。 我们选择使用光照绘制完全面, 但可以自由地绘制线框, 在渲染前处理网格, 应用纹理地图等。

在这里, 我们的代码示例告诉网格呈现器绘制集合。 这次我们不会指定仅深度传递, 因此它会附加像素着色器并使用为当前虚拟摄像机指定的目标来完成呈现管道。

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
* [创建全息 DirectX 项目](creating-a-holographic-directx-project.md)
* [Windows 感知. 空间 API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
