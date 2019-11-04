---
title: 在 DirectX 中协调系统
description: 介绍如何使用 Windows Mixed Reality 空间定位器、参考框架、空间定位点和坐标系统，如何使用 SpatialStage，如何处理跟踪丢失情况，如何保存和加载定位点，以及如何执行图像稳定性。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实，空间定位器，空间参考框架，空间坐标系统，空间阶段，示例代码，图像稳定，空间锚，空间锚定存储，跟踪丢失，演练
ms.openlocfilehash: a0bce897c1982715af24f0bf7c398cdee10f017f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436225"
---
# <a name="coordinate-systems-in-directx"></a>在 DirectX 中协调系统

[坐标系统](coordinate-systems.md)构成 Windows Mixed Reality api 提供的空间理解的基础。

如今，其原来的 VR 或单一房间的 VR 设备建立一个主坐标系来表示其跟踪的空间。 Windows Mixed Reality 设备（如 HoloLens）设计为在多个未定义的环境中使用，并在用户浏览时查找并了解有关其环境的信息。 这允许设备适应不断改善用户聊天室的知识，但会导致在应用的整个生命周期内，会使坐标系统彼此之间发生变化。 Windows Mixed Reality 支持范围广泛的设备，这些设备包括通过世界附加的参考帧从固定的沉浸式耳机。

>[!NOTE]
>本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT，这与全息项目模板中使用的不同。  概念对于C++/WinRT 项目是等效的，但你将需要转换代码。

## <a name="spatial-coordinate-systems-in-windows"></a>Windows 中的空间坐标系统

用于 Windows 中的实际坐标系统原因的核心类型是<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>。 此类型的实例表示任意坐标系统，并提供一种方法，用于获取可用于在两个坐标系统之间进行转换而不了解每个坐标系统的详细信息的转换矩阵。

返回空间信息的方法（表示为用户的环境中的点、片或卷）将接受 SpatialCoordinateSystem 参数，以使你能够确定最适合要返回的坐标的坐标系统。 这些坐标的单位将始终以米为单位。

SpatialCoordinateSystem 与其他坐标系统（包括表示设备位置的系统）具有动态关系。 在任何时间点，设备都可以定位某些坐标系统而不是其他坐标系。 对于大多数坐标系统，您的应用程序必须准备好处理无法找到的时间段。

应用程序不应直接创建 SpatialCoordinateSystems，而应通过感知 Api 来使用。 感知 Api 中有三个主要的坐标系统源，其中每个源都映射到 "[坐标系统](coordinate-systems.md)" 页上所述的概念：
* 若要获取固定的引用框架，请创建一个<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a>或从当前的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>获取一个引用框架。
* 若要获取空间定位点，请创建一个<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>。
* 若要获取附加的引用框架，请创建一个<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>。

这些对象返回的所有坐标系统都是右手的，其中 + y 向上，+ x 向右，+ z 向后。 您可以通过在正 x 方向上向左或向右箭头，然后将它们运行为 y 方向，来记住哪个 z 轴的方向。 你的拇指指向的方向（无论指向你还是相反方向）就是正 z 轴为坐标系统所指的方向。 下面的图例显示了这两个坐标系统。

![左坐标系统和右坐标系](images/left-hand-right-hand.gif)<br>
*左手和右手坐标系统*

若要基于 HoloLens 的位置启动到 SpatialCoordinateSystem，请使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>类创建附加或固定的引用框架，如以下部分中所述。

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>使用空间暂存在世界中放置全息影像

不透明的 Windows Mixed Reality 沉浸式耳机的坐标系统使用静态<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference：： Current</a>属性进行访问。 此 API 提供了一个坐标系统、有关播放机是否已安装或移动的信息、用于浏览播放机是否为移动设备的安全区域的边界以及耳机是否定向。 对于空间阶段的更新，还有一个事件处理程序。

首先，我们获取空间阶段并订阅其更新： 

**空间阶段初始化**代码

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

在 OnCurrentChanged 方法中，应用应检查空间阶段并相应地更新播放机体验。 在此示例中，我们提供了舞台边界的可视化效果，以及用户指定的起始位置和阶段的视图范围以及移动属性范围。 如果无法提供阶段，我们还会回退到我们自己的固定坐标系统。


**空间阶段更新**代码

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

以顺时针顺序提供定义舞台边界的顶点集。 当用户接近边界时，Windows Mixed Reality shell 在边界处绘制一个围栏;出于自己的目的，你可能希望 triangularize 到不可区域。 以下算法可用于 triangularize 阶段。


**空间阶段 triangularization**的代码

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>使用固定的参考框架在世界中放置全息影像

[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx)类表示一个引用框架，该框架在用户四处移动时相对于用户的环境[保持静止](coordinate-systems.md#stationary-frame-of-reference)。 这一帧参考用于使坐标在设备附近保持稳定。 SpatialStationaryFrameOfReference 的一项关键用途是在渲染全息影像时充当渲染引擎内的基础世界坐标系统。

若要获取 SpatialStationaryFrameOfReference，请使用[SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx)类并调用[CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)。

从 Windows 全息应用模板代码：

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* 固定参考帧旨在提供相对于总体空间的最佳位置。 该引用帧中的各个位置都允许略微偏移。 这是正常现象，因为设备会了解有关环境的详细信息。
* 需要精确放置单独的全息影像时，应使用 SpatialAnchor 将各个全息图锚定到现实世界中的某个位置-例如，用户指示特别感兴趣的点。 定位点位置不会偏移，但可以更正。定位点将使用更正后在下一帧中开始的更正位置。

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>使用空间锚点将全息影像置于世界中

[空间锚点](coordinate-systems.md#spatial-anchors)是在真实世界的特定位置放置全息影像的绝佳方式，系统可确保锚点在一段时间内保持不变。 本主题说明如何创建和使用定位点，以及如何使用定位点数据。

你可以在所选的 SpatialCoordinateSystem 内的任何位置和方向上创建 SpatialAnchor。 设备现在必须能够找到该坐标系，而且系统不得达到其空间锚定的限制。

定义后，SpatialAnchor 的坐标系统将不断调整，以保持其初始位置的精确位置和方向。 然后，你可以使用此 SpatialAnchor 来呈现在该确切位置的用户环境中显示为固定的全息影像。

调整锚点的调整效果将随着锚点增加的距离而放大。 因此，应避免相对于该定位点的源中超过3米的定位点呈现内容。

[坐标系](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx)属性获取一个坐标系统，该系统允许你相对于定位点放置内容，并在设备调整定位点的确切位置时应用缓动。

使用[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx)属性和相应的[RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx)事件自行管理这些调整。

### <a name="persist-and-share-spatial-anchors"></a>保留并共享空间锚

你可以使用[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)类在本地保留 SpatialAnchor，然后在同一 HoloLens 设备上的未来应用会话中恢复它。

通过使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a>，你可以从本地 SpatialAnchor 创建持久的云锚点，你的应用可以在多个 HoloLens、IOS 和 Android 设备上找到它。  通过在多个设备之间共享公用空间定位点，每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。  这可实现实时共享体验。

还可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>在 HoloLens、iOS 和 Android 设备上实现异步全息影像持久性。  通过共享持久的云空间定位点，多个设备可以随着时间推移观察相同的持久全息影像，即使这些设备没有同时出现，也是如此。

若要开始在 HoloLens 应用中构建共享体验，请尝试5分钟的<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空间锚快速入门</a>。

启动并运行 Azure 空间锚点后，可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">在 HoloLens 上创建和查找锚</a>。  演练也适用于<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> ，使你能够在所有设备上共享相同的定位标记。

### <a name="create-spatialanchors-for-holographic-content"></a>为全息内容创建 SpatialAnchors

对于此代码示例，我们修改了 Windows 全息应用程序模板，在检测到**按下**的手势时创建定位点。 然后，在呈现过程中将多维数据集放在定位点上。

由于 helper 类支持多个定位点，因此，我们可以使用此代码示例将所需的多维数据集设置为多个。

请注意，定位点的 Id 是你在应用中控制的内容。 在此示例中，我们创建了一个命名方案，该方案基于当前存储在应用程序的定位点集合中的定位点数。

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>异步加载和缓存，SpatialAnchorStore

我们来看一下如何编写有助于处理此持久性的 SampleSpatialAnchorHelper 类，其中包括：
* 存储内存中定位点的集合，由 Platform：： String 键进行索引。
* 从系统的 SpatialAnchorStore 加载定位点，这与本地内存中集合保持分离。
* 当应用选择执行此操作时，将本地内存中集合的定位点保存到 SpatialAnchorStore。

下面介绍了如何将[SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)对象保存在[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)中。

类启动时，会异步请求 SpatialAnchorStore。 这涉及到 API 加载锚定存储时的系统 i/o，此 API 是异步的，因此 i/o 是非阻塞的。

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

系统将提供一个可用于保存锚的 SpatialAnchorStore。 这是将字符串键值与 SpatialAnchors 的数据值相关联的 IMapView。 在我们的示例代码中，我们将其存储在私有类成员变量中，该变量可通过我们的帮助程序类的公共函数访问。

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>别忘了挂钩暂停/恢复事件，保存并加载定位点存储。

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>将内容保存到定位点存储

当系统挂起应用时，需要将空间锚点保存到锚存储。 你还可以选择在其他时间将定位点保存到定位点存储区，就像你在应用的实现时所需要的那样。

准备尝试将内存中的定位标记保存到 SpatialAnchorStore 时，可以循环遍历集合并尝试保存每个定位点。

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>在应用恢复时从定位点存储加载内容

当你的应用程序恢复，或在应用程序的 implementaiton 所需的任何其他时间，你可以通过将以前保存的定位点从定位点存储区 IMapView 传输到你自己的内存中数据库数据库，来还原以前保存到 AnchorStore 的定位点。

若要从 SpatialAnchorStore 还原定位点，请将你感兴趣的每个定位点还原到自己的内存中集合。

需要 SpatialAnchors 的内存中数据库;将字符串与您创建的 SpatialAnchors 相关联的一种方法。 在我们的示例代码中，我们选择使用 Windows：： Foundation：：集合：： IMap 来存储定位点，这使得为 SpatialAnchorStore 使用相同的密钥和数据值变得简单。

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>可能无法立即定位还原的定位点。 例如，它可能是位于单独房间或不同建筑物中的定位点。 在使用从 AnchorStore 检索到的定位点之前应对其进行测试。

<br>

>[!NOTE]
>在此示例代码中，我们将从 AnchorStore 检索所有定位点。 这不是必需的;您的应用程序也可以选择使用对您的实现有意义的字符串键值，并选择某个定位点。

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>如果需要，请清除锚定存储

有时，您需要清除应用状态并写入新数据。 下面是如何通过[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)执行此操作的方法。

使用我们的帮助器类，几乎不需要包装 Clear 函数。 我们选择在示例实现中执行此操作，因为我们的帮助器类被赋予了拥有 SpatialAnchorStore 实例的责任。

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>示例：将定位坐标系与固定引用帧坐标系统相关联

假设你有一个定位点，并且想要将定位点坐标系统中的某些内容关联到你在大多数其他内容中已使用的 SpatialStationaryReferenceFrame。 您可以使用[TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx)从定位点的坐标系统获取转换为固定参考帧的转换：

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

此过程可通过两种方式来实现：
1. 它告诉你是否可以彼此理解两个引用框架，以及
2. 如果是这样，它将提供一个转换，以便直接从一个坐标系转换到另一个坐标系统。

使用此信息，您可以了解两个引用帧之间对象之间的空间关系。

对于呈现，通常可以根据对象的原始参考框架或锚点对它们进行分组，从而获得更好的结果。 为每个组执行单独的绘图处理。 对于具有最初使用同一坐标系统创建的模型转换的对象，视图矩阵更准确。

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>使用设备附加的参考框架创建全息影像

有时，你想要呈现已[附加](coordinate-systems.md#attached-frame-of-reference)到设备位置的全息影像，例如，当设备只能确定其方向而不能确定其位置时，包含调试信息或信息性消息的面板空间. 为此，我们使用附加的参考框架。

SpatialLocatorAttachedFrameOfReference 类定义相对于设备而不是实际的坐标系统。 此框架的固定标题相对于用户在创建引用框架时面向的方向的用户环境。 接下来，这一帧参考中的所有方向都是相对于该固定标题的，即使用户要旋转设备也是如此。

对于 HoloLens，此帧坐标系统的原点位于用户头部的旋转中心，因此其位置不受 head 旋转的影响。 您的应用程序可以指定与此点相对的偏移量，以将全息影像置于用户的前端。

若要获取 SpatialLocatorAttachedFrameOfReference，请使用 SpatialLocator 类并调用 CreateAttachedFrameOfReferenceAtCurrentHeading。

请注意，这适用于整个范围的 Windows Mixed Reality 设备。

### <a name="use-a-reference-frame-attached-to-the-device"></a>使用附加到设备的引用框架

这些部分讨论了在 Windows 全息应用程序模板中所做的更改，以使用此 API 启用设备附加的引用框架。 请注意，此 "附加" 的全息图将与固定或锚定的全息影像一起工作，并且在设备暂时无法找到其在世界中的位置时也可能会使用。

首先，我们将模板更改为存储 SpatialLocatorAttachedFrameOfReference 而不是 SpatialStationaryFrameOfReference：

从**HolographicTagAlongSampleMain**：

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

从**HolographicTagAlongSampleMain**：

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

在更新过程中，我们会在从帧预测获得的时间戳处获取坐标系统。

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>获取空间指针姿势，并遵循用户的注视

我们希望我们的示例全息图跟随用户的[注视](gaze-and-commit.md)，这与全息 shell 可以遵循用户的注视方式类似。 为此，我们需要从相同的时间戳中获取 SpatialPointerPose。

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

此 SpatialPointerPose 包含根据[用户的当前标题](gaze-in-directx.md)放置全息影像所需的信息。

出于用户舒适的原因，我们使用线性内插（"lerp"）来平滑更改位置，以便在一段时间内进行更改。 这比将全息图锁定到其注视的用户更适合。 Lerping 的影像位置，还可以通过抑制移动来使全息影像稳定;如果未执行此抑制，用户将看到全息影像抖动，因为通常会将其视为让移动用户。

From **StationaryQuadRenderer：:P ositionhologram**：

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>对于调试面板，您可以选择将全息图从一边重定位到一边，使其不会妨碍您的视图。 下面是有关如何执行此操作的示例。

对于**StationaryQuadRenderer：:P ositionhologram**：

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>旋转全息图以面对相机

只需定位全息图（在本例中为四个部分）是不够的;还必须旋转对象，使其面向用户。 请注意，此旋转发生在世界空间中，因为这种类型的 billboarding 允许全息图保留在用户的环境中。 由于全息图锁定为显示方向，因此视图空间 billboarding 并不舒适：在这种情况下，还必须在左视图和右视图矩阵之间进行插值，才能获得不会干扰立体声呈现的视图空间布告栏转换。 在这里，我们将旋转 X 和 Z 轴以面对用户。

From **StationaryQuadRenderer：： Update**：

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>呈现附加全息图

在此示例中，我们还会选择在 SpatialLocatorAttachedReferenceFrame 的坐标系统中呈现全息影像，这是我们放置全息图的位置。 （如果我们决定使用其他坐标系统进行呈现，则需要从设备附加的参考框架的坐标系统到该坐标系统获取转换。）

From **HolographicTagAlongSampleMain：： Render**：

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

就这么简单！ 现在，全息图将 "跟踪" 在用户看看方向上为2米的位置。

>[!NOTE]
>此示例还会加载其他内容-请参阅 StationaryQuadRenderer。

## <a name="handling-tracking-loss"></a>处理跟踪丢失

当设备在世界上找不到自己时，应用程序会遇到 "跟踪丢失" 的情况。 Windows Mixed Reality 应用应能够应对位置跟踪系统的此类中断。 通过使用默认 SpatialLocator 上的 LocatabilityChanged 事件，可以观察到这些中断，并创建响应。

From **AppMain：： SetHolographicSpace：**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

当你的应用收到 LocatabilityChanged 事件时，它可以根据需要更改行为。 例如，在 PositionalTrackingInhibited 状态下，你的应用程序可以暂停正常操作，并呈现显示一条警告消息的[标记](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference)。

Windows 全息应用程序模板附带了一个已为你创建的 LocatabilityChanged 处理程序。 默认情况下，当位置跟踪不可用时，它将在调试控制台中显示警告。 可以向此处理程序添加代码，以根据需要从应用程序中提供响应。

从**AppMain：**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>空间映射

[空间映射](spatial-mapping-in-directx.md)api 使用坐标系统获取 surface 网格的模型转换。

## <a name="see-also"></a>另请参阅
* [坐标系统](coordinate-systems.md)
* [空间定位点](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [DirectX 中的手和运动控制器](hands-and-motion-controllers-in-directx.md)
* [DirectX 中的空间映射](spatial-mapping-in-directx.md)
