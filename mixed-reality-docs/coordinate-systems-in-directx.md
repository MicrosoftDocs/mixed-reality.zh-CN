---
title: 在 DirectX 的坐标系统
description: 说明如何使用 Windows Mixed Reality 空间定位符、 参考帧、 空间定位点和坐标系统、 如何使用 SpatialStage、 如何处理跟踪丢失、 如何保存和加载的定位点，以及进行图像稳定。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实空间的定位符、 空间的参考框架、 空间坐标系统、 空间阶段中，示例代码、 映像稳定、 空间定位点、 空间定位点应用商店、 跟踪丢失、 演练
ms.openlocfilehash: c8cdb39cbf4634edb4ed0a595381fc70f1388ce4
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593078"
---
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="34944-104">在 DirectX 的坐标系统</span><span class="sxs-lookup"><span data-stu-id="34944-104">Coordinate systems in DirectX</span></span>

<span data-ttu-id="34944-105">[坐标系统](coordinate-systems.md)空间了解提供由 Windows 混合现实 Api 构成的基础。</span><span class="sxs-lookup"><span data-stu-id="34944-105">[Coordinate systems](coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="34944-106">今天的正确安装 VR 或单聊天室 VR 设备建立一个主要的坐标系统来表示其被跟踪的空间。</span><span class="sxs-lookup"><span data-stu-id="34944-106">Today's seated VR or single-room VR devices establish one primary coordinate system to represent their tracked space.</span></span> <span data-ttu-id="34944-107">Windows Mixed Reality 设备如 HoloLens 专为在整个大型未定义环境中，使用与设备发现和了解其周围环境作为用户指导周围。</span><span class="sxs-lookup"><span data-stu-id="34944-107">Windows Mixed Reality devices such as HoloLens are designed to be used throughout large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="34944-108">允许在设备以适应不断改进用户的聊天室，但在将更改其关系为另一个的整个生存期的应用程序的坐标系统中的结果有关的知识。</span><span class="sxs-lookup"><span data-stu-id="34944-108">This allows the device to adapt to continually-improving knowledge about the user's rooms, but results in coordinate systems that will change their relationship to one another through the lifetime of the app.</span></span> <span data-ttu-id="34944-109">Windows Mixed Reality 支持范围广泛的设备，范围在关注沉浸式耳机世界附加参考帧。</span><span class="sxs-lookup"><span data-stu-id="34944-109">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="34944-110">这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="34944-110">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="34944-111">这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。</span><span class="sxs-lookup"><span data-stu-id="34944-111">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="34944-112">在 Windows 中的空间坐标系统</span><span class="sxs-lookup"><span data-stu-id="34944-112">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="34944-113">有关在 Windows 中的实际的坐标系统的原因所使用的核心类型是<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>。</span><span class="sxs-lookup"><span data-stu-id="34944-113">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="34944-114">此类型的实例表示任意的坐标系统，并提供方法以获取可用于转换两个坐标系统，而无需了解每个详细信息之间的转换矩阵。</span><span class="sxs-lookup"><span data-stu-id="34944-114">An instance of this type represents an arbitrary coordinate system and provides a method to get a transformation matrix that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="34944-115">返回表示为点、 大气或用户的环境中的卷的空间信息的方法将接受 SpatialCoordinateSystem 参数，让你确定它是最适用于这些坐标要返回的坐标系。</span><span class="sxs-lookup"><span data-stu-id="34944-115">Methods that return spatial information, represented as points, rays, or volumes in the user's surroundings, will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="34944-116">这些坐标的单位始终会以米为单位。</span><span class="sxs-lookup"><span data-stu-id="34944-116">The units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="34944-117">SpatialCoordinateSystem 具有动态关系与其他坐标系统，包括表示设备的位置。</span><span class="sxs-lookup"><span data-stu-id="34944-117">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="34944-118">在任何时间点，可能无法找到某些坐标系统而不是其他设备。</span><span class="sxs-lookup"><span data-stu-id="34944-118">At any point in time, the device may be able to locate some coordinate systems and not others.</span></span> <span data-ttu-id="34944-119">对于大多数坐标系统中，您的应用程序必须准备好处理一段时间在此期间他们找不到。</span><span class="sxs-lookup"><span data-stu-id="34944-119">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="34944-120">你的应用程序不应创建 SpatialCoordinateSystems 直接-而是应通过 Perception Api 使用它们。</span><span class="sxs-lookup"><span data-stu-id="34944-120">Your application should not create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="34944-121">有三个主要源 Perception Api 中的坐标系统的每个哪些映射到所述的概念[坐标系](coordinate-systems.md)页：</span><span class="sxs-lookup"><span data-stu-id="34944-121">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](coordinate-systems.md) page:</span></span>
* <span data-ttu-id="34944-122">若要固定参考框架，创建<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a>或获取一个从当前<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>。</span><span class="sxs-lookup"><span data-stu-id="34944-122">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="34944-123">若要获取空间定位点，创建<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>。</span><span class="sxs-lookup"><span data-stu-id="34944-123">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="34944-124">若要附加的参考框架，创建<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>。</span><span class="sxs-lookup"><span data-stu-id="34944-124">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="34944-125">所有返回这些对象的坐标系统都是惯用右手，与 + y、 + x 向右和 + z 向后。</span><span class="sxs-lookup"><span data-stu-id="34944-125">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="34944-126">您可以通过指向左侧或右侧的手指在正 x 方向和运行它们到正 y 方向的正 z 轴点记住方向。</span><span class="sxs-lookup"><span data-stu-id="34944-126">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="34944-127">你的拇指指向的方向（无论指向你还是相反方向）就是正 z 轴为坐标系统所指的方向。</span><span class="sxs-lookup"><span data-stu-id="34944-127">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="34944-128">下面的图例显示了这两个坐标系统。</span><span class="sxs-lookup"><span data-stu-id="34944-128">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="34944-129">![左侧和右侧的坐标系统](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="34944-129">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="34944-130">*左侧和右侧的坐标系统*</span><span class="sxs-lookup"><span data-stu-id="34944-130">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="34944-131">若要启动到基于位置 HoloLens SpatialCoordinateSystem，使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>类，以创建任一附加或固定参考框架，如以下各节中所述。</span><span class="sxs-lookup"><span data-stu-id="34944-131">To bootstrap into a SpatialCoordinateSystem based on the position of a HoloLens, use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference, as described in the sections below.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="34944-132">将全息放在世界上使用空间的阶段</span><span class="sxs-lookup"><span data-stu-id="34944-132">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="34944-133">使用静态访问坐标系统的不透明 Windows Mixed Reality 沉浸式耳机<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a>属性。</span><span class="sxs-lookup"><span data-stu-id="34944-133">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="34944-134">此 API 为移动办公了移动，播放机是否提供坐标系统、 有关播放机是否已就位或移动设备的信息、 安全区域的边界和相对值的指示将耳机具有方向性。</span><span class="sxs-lookup"><span data-stu-id="34944-134">This API provides a coordinate system, information about whether the player is seated or mobile, the boundary of a safe area for walking around if the player is mobile, and an indication of whether or not the headset is directional.</span></span> <span data-ttu-id="34944-135">此外，还有空间阶段的更新的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="34944-135">There is also an event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="34944-136">首先，我们获取空间阶段并订阅更新到它：</span><span class="sxs-lookup"><span data-stu-id="34944-136">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="34944-137">为代码**空间阶段初始化**</span><span class="sxs-lookup"><span data-stu-id="34944-137">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="34944-138">在 OnCurrentChanged 方法中，您的应用程序应检查空间阶段并相应地更新播放器体验。</span><span class="sxs-lookup"><span data-stu-id="34944-138">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience accordingly.</span></span> <span data-ttu-id="34944-139">在此示例中，我们提供的可视化效果的阶段边界以及指定的用户和该阶段的范围的视图和移动属性范围的起始位置。</span><span class="sxs-lookup"><span data-stu-id="34944-139">In this example, we provide a visualization of the stage boundary, as well as the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="34944-140">我们还故障回复到我们自己保持静止的坐标系统，不能提供一个阶段时。</span><span class="sxs-lookup"><span data-stu-id="34944-140">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="34944-141">为代码**空间阶段更新**</span><span class="sxs-lookup"><span data-stu-id="34944-141">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="34944-142">以顺时针顺序提供了定义阶段边界的顶点的组。</span><span class="sxs-lookup"><span data-stu-id="34944-142">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="34944-143">Windows Mixed Reality shell 在边界绘制起一道围墙，当用户接近您可能希望为自己的意图 triangularize 移动的区域。</span><span class="sxs-lookup"><span data-stu-id="34944-143">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it; you may wish to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="34944-144">下面的算法可以用于 triangularize 阶段。</span><span class="sxs-lookup"><span data-stu-id="34944-144">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="34944-145">为代码**空间阶段 triangularization**</span><span class="sxs-lookup"><span data-stu-id="34944-145">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="34944-146">将全息放在世界上使用固定参考框架</span><span class="sxs-lookup"><span data-stu-id="34944-146">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="34944-147">[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx)类表示一个帧的引用[保持静止状态](coordinate-systems.md#stationary-frame-of-reference)相对于以用户身份的用户的环境移动。</span><span class="sxs-lookup"><span data-stu-id="34944-147">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="34944-148">此参考框架，优先保留坐标稳定附近的设备。</span><span class="sxs-lookup"><span data-stu-id="34944-148">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="34944-149">SpatialStationaryFrameOfReference 的关键用法是作为基础全局坐标系统内呈现引擎，呈现全息时。</span><span class="sxs-lookup"><span data-stu-id="34944-149">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="34944-150">若要获取 SpatialStationaryFrameOfReference，请使用[SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx)类并调用[CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)。</span><span class="sxs-lookup"><span data-stu-id="34944-150">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="34944-151">从 Windows Holographic 的应用程序模板代码：</span><span class="sxs-lookup"><span data-stu-id="34944-151">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="34944-152">固定参考框架旨在提供相对于总空间的最佳的位置。</span><span class="sxs-lookup"><span data-stu-id="34944-152">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="34944-153">允许在该引用框架内的各个位置稍有偏差。</span><span class="sxs-lookup"><span data-stu-id="34944-153">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="34944-154">这是正常的因为设备了解到有关环境的详细信息。</span><span class="sxs-lookup"><span data-stu-id="34944-154">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="34944-155">当需要精确地放置各个全息时，应使用 SpatialAnchor 锚定到现实生活中的位置的单个全息图-例如，点用户指明特别感兴趣的。</span><span class="sxs-lookup"><span data-stu-id="34944-155">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="34944-156">定位点位置不偏差，但可以更正;定位点将使用从下一步的范围开始发生更正后的已更正的位置。</span><span class="sxs-lookup"><span data-stu-id="34944-156">Anchor positions do not drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="34944-157">将全息放在世界上使用空间的定位点</span><span class="sxs-lookup"><span data-stu-id="34944-157">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="34944-158">[空间的定位点](coordinate-systems.md#spatial-anchors)将全息放置在现实生活中的特定位置的好办法，与系统确保定位点位置保持不变随着时间的推移。</span><span class="sxs-lookup"><span data-stu-id="34944-158">[Spatial anchors](coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="34944-159">本主题说明如何创建和使用定位点，以及如何使用定位点数据。</span><span class="sxs-lookup"><span data-stu-id="34944-159">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="34944-160">您可以在任何位置和方向 SpatialCoordinateSystem 内所选的创建 SpatialAnchor。</span><span class="sxs-lookup"><span data-stu-id="34944-160">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="34944-161">设备必须能够找到目前，该坐标系统，并且系统必须未达到其限制的空间的定位点。</span><span class="sxs-lookup"><span data-stu-id="34944-161">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="34944-162">定义后，SpatialAnchor 坐标系统将持续调整保留的精确位置和方向其初始位置。</span><span class="sxs-lookup"><span data-stu-id="34944-162">Once defined, the coordinate system of a SpatialAnchor adjusts continually to retain the precise position and orientation of its initial location.</span></span> <span data-ttu-id="34944-163">然后可以使用此 SpatialAnchor 来呈现会在该确切位置的用户的环境中显示固定的全息。</span><span class="sxs-lookup"><span data-stu-id="34944-163">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="34944-164">从的定位点增加的距离，距离放大的定位点保存在的位置的调整的效果。</span><span class="sxs-lookup"><span data-stu-id="34944-164">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="34944-165">因此，应避免相对于多个大约 3 米从该定位点的源的定位点呈现内容。</span><span class="sxs-lookup"><span data-stu-id="34944-165">Therefore, you should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="34944-166">[坐标系](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx)属性获取用于将缓动设备调整定位点的精确位置时，应用将相对于定位点，内容坐标系统。</span><span class="sxs-lookup"><span data-stu-id="34944-166">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="34944-167">使用[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx)属性和相应[RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx)要自行管理这些调整事件。</span><span class="sxs-lookup"><span data-stu-id="34944-167">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="34944-168">保留和共享空间的定位点</span><span class="sxs-lookup"><span data-stu-id="34944-168">Persist and share spatial anchors</span></span>

<span data-ttu-id="34944-169">您可以保留使用本地 SpatialAnchor [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)类并将其上相同的 HoloLens 设备的将来应用会话中返回。</span><span class="sxs-lookup"><span data-stu-id="34944-169">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="34944-170">通过使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>，可以从您的应用程序然后可以跨多个 HoloLens、 iOS 和 Android 设备找到本地 SpatialAnchor 创建持久的云定位点。</span><span class="sxs-lookup"><span data-stu-id="34944-170">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="34944-171">通过在多个设备之间共享公共空间定位点，每个用户可以看到呈现相对于同一物理位置中的锚点的内容。</span><span class="sxs-lookup"><span data-stu-id="34944-171">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="34944-172">这样实时共享体验。</span><span class="sxs-lookup"><span data-stu-id="34944-172">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="34944-173">此外可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>异步全息图暂留在 HoloLens、 iOS 和 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="34944-173">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="34944-174">通过共享持久的云空间定位点，多个设备可以观察到相同的持久化全息图随着时间推移，即使这些设备不存在同时在一起。</span><span class="sxs-lookup"><span data-stu-id="34944-174">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="34944-175">若要开始构建 HoloLens 应用程序中的共享的体验，请尝试出 5 分钟<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">快速入门 Azure 空间的定位点 HoloLens</a>。</span><span class="sxs-lookup"><span data-stu-id="34944-175">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="34944-176">你可以在 Azure 空间的定位点与您使用启动并运行，然后<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">创建并在 HoloLens 上找到的定位点</a>。</span><span class="sxs-lookup"><span data-stu-id="34944-176">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="34944-177">演练是可用于<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> ，使您能够共享的所有设备上的同一个定位点。</span><span class="sxs-lookup"><span data-stu-id="34944-177">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="34944-178">创建 SpatialAnchors 全息版的内容</span><span class="sxs-lookup"><span data-stu-id="34944-178">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="34944-179">有关此代码示例，我们修改 Windows 全息版应用模板，以创建锚点何时**Pressed**检测到笔势。</span><span class="sxs-lookup"><span data-stu-id="34944-179">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="34944-180">多维数据集然后，将放置在定位点呈现处理过程。</span><span class="sxs-lookup"><span data-stu-id="34944-180">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="34944-181">帮助器类支持多个定位点，因为我们可以将任意多个多维数据集作为我们想使用此代码示例 ！</span><span class="sxs-lookup"><span data-stu-id="34944-181">Since multiple anchors are supported by the helper class, we can place as many cubes as we want using this code sample!</span></span>

<span data-ttu-id="34944-182">请注意个定位点的 Id 是控制应用程序中的内容。</span><span class="sxs-lookup"><span data-stu-id="34944-182">Note that the IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="34944-183">在此示例中，我们创建了基于当前存储的定位点的应用程序的集合中的定位点数量是有顺序的命名方案。</span><span class="sxs-lookup"><span data-stu-id="34944-183">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="34944-184">以异步方式加载和缓存 SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="34944-184">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="34944-185">让我们了解如何编写一个 SampleSpatialAnchorHelper 类来帮助处理此持久性，包括：</span><span class="sxs-lookup"><span data-stu-id="34944-185">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="34944-186">存储一系列内存中的定位点，由 platform:: string 键编制索引。</span><span class="sxs-lookup"><span data-stu-id="34944-186">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="34944-187">从系统的 SpatialAnchorStore 加载的定位点，这是分开的本地内存中集合。</span><span class="sxs-lookup"><span data-stu-id="34944-187">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="34944-188">当应用程序选择执行此操作时，请将的定位点的本地内存中集合保存到 SpatialAnchorStore。</span><span class="sxs-lookup"><span data-stu-id="34944-188">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="34944-189">下面介绍了如何保存[SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)中的对象[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)。</span><span class="sxs-lookup"><span data-stu-id="34944-189">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="34944-190">类启动时，将以异步方式请求 SpatialAnchorStore。</span><span class="sxs-lookup"><span data-stu-id="34944-190">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="34944-191">这涉及到系统 I/O API 加载定位点存储，以及此 API 可异步 I/O 非阻塞。</span><span class="sxs-lookup"><span data-stu-id="34944-191">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="34944-192">系统会提供可用于保存与标记 SpatialAnchorStore。</span><span class="sxs-lookup"><span data-stu-id="34944-192">You will be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="34944-193">这是将与 SpatialAnchors 数据值的字符串，密钥值相关联 IMapView。</span><span class="sxs-lookup"><span data-stu-id="34944-193">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="34944-194">在示例代码中，我们可通过我们的帮助器类的公共函数访问的私有类成员变量中将此存储。</span><span class="sxs-lookup"><span data-stu-id="34944-194">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="34944-195">别忘了将挂接到要保存和加载定位点应用商店的挂起/继续事件。</span><span class="sxs-lookup"><span data-stu-id="34944-195">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="34944-196">将内容保存到定位点存储</span><span class="sxs-lookup"><span data-stu-id="34944-196">Save content to the anchor store</span></span>

<span data-ttu-id="34944-197">时系统会挂起应用程序，您需要保存到定位点存储空间的定位点。</span><span class="sxs-lookup"><span data-stu-id="34944-197">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="34944-198">发现是所必不可少的应用程序的实现，您还可在其他情况下，保存到定位点存储的定位点。</span><span class="sxs-lookup"><span data-stu-id="34944-198">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="34944-199">如果你已准备好尝试将内存中定位点保存到 SpatialAnchorStore，可以循环访问集合，并尝试保存每个。</span><span class="sxs-lookup"><span data-stu-id="34944-199">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="34944-200">应用程序恢复运行时从定位点存储加载内容</span><span class="sxs-lookup"><span data-stu-id="34944-200">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="34944-201">如果您的应用程序恢复，或在你的应用的 implementaiton 所需的其他任何时间，可以还原以前已保存到 AnchorStore 通过将其从定位点存储 IMapView 传输到您自己的内存中数据库的 SpatialAnchors 的定位点。</span><span class="sxs-lookup"><span data-stu-id="34944-201">When your app resumes, or at any other time necessary for your app's implementaiton, you can restore anchors that were previously saved to the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors.</span></span>

<span data-ttu-id="34944-202">若要从 SpatialAnchorStore 还原的定位点，还原到内存中集合感兴趣的每个。</span><span class="sxs-lookup"><span data-stu-id="34944-202">To restore anchors from the SpatialAnchorStore, restore each one that you are interested in to your own in-memory collection.</span></span>

<span data-ttu-id="34944-203">您需要 SpatialAnchors; 你自己的内存中数据库若要将字符串与你创建 SpatialAnchors 相关联某种方式。</span><span class="sxs-lookup"><span data-stu-id="34944-203">You need your own in-memory database of SpatialAnchors; some way to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="34944-204">在示例代码中，我们选择使用 Windows::Foundation::Collections::IMap 存储的定位点，这样就可以轻松个 SpatialAnchorStore 使用相同的密钥和数据值。</span><span class="sxs-lookup"><span data-stu-id="34944-204">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="34944-205">还原的定位点可能不是可定位立即。</span><span class="sxs-lookup"><span data-stu-id="34944-205">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="34944-206">例如，它可能位于不同房间或在不同构建完全的定位点。</span><span class="sxs-lookup"><span data-stu-id="34944-206">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="34944-207">使用它们之前，应为 locatability 测试从 AnchorStore 中检索到的定位点。</span><span class="sxs-lookup"><span data-stu-id="34944-207">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="34944-208">在此示例代码中，我们从 AnchorStore 检索所有密钥。</span><span class="sxs-lookup"><span data-stu-id="34944-208">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="34944-209">这不是要求;您的应用程序可能也很好选择特定的子集的定位点通过使用对您的实现有意义的字符串键值。</span><span class="sxs-lookup"><span data-stu-id="34944-209">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="34944-210">在需要时清除定位点存储，</span><span class="sxs-lookup"><span data-stu-id="34944-210">Clear the anchor store, when needed</span></span>

<span data-ttu-id="34944-211">有时，您需要以清除应用程序状态并写入新数据。</span><span class="sxs-lookup"><span data-stu-id="34944-211">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="34944-212">下面是如何实现，其[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)。</span><span class="sxs-lookup"><span data-stu-id="34944-212">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="34944-213">使用我们的帮助器类，它是几乎不需要包装清晰的函数。</span><span class="sxs-lookup"><span data-stu-id="34944-213">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="34944-214">我们选择为此，在我们的示例实现，由于我们的帮助器类都提供了拥有 SpatialAnchorStore 实例的责任。</span><span class="sxs-lookup"><span data-stu-id="34944-214">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="34944-215">例如：与定位点坐标系统相关的固定参考框架坐标系统</span><span class="sxs-lookup"><span data-stu-id="34944-215">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="34944-216">假设有一个定位点，并且你想要与你已在使用的大部分其他内容 SpatialStationaryReferenceFrame 相关定位点的坐标系统中的某些内容。</span><span class="sxs-lookup"><span data-stu-id="34944-216">Let's say that you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame that you’re already using for most of your other content.</span></span> <span data-ttu-id="34944-217">可以使用[TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx)才能获取转换定位点的坐标系统中的固定参考框架：</span><span class="sxs-lookup"><span data-stu-id="34944-217">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to obtain a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="34944-218">此过程是有用的两种方式：</span><span class="sxs-lookup"><span data-stu-id="34944-218">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="34944-219">它会告诉您如果两个引用帧可以相对于其他，理解和;</span><span class="sxs-lookup"><span data-stu-id="34944-219">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="34944-220">如果是这样，它提供一个可从一个坐标系统直接转到其他转换。</span><span class="sxs-lookup"><span data-stu-id="34944-220">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="34944-221">使用此信息，必须了解两个参考帧之间的对象之间的空间关系。</span><span class="sxs-lookup"><span data-stu-id="34944-221">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="34944-222">进行呈现，通常可以通过将分组根据其原始的参考框架或定位点的对象中获取更好的结果。</span><span class="sxs-lookup"><span data-stu-id="34944-222">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="34944-223">对于每个组执行单独的绘制过程。</span><span class="sxs-lookup"><span data-stu-id="34944-223">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="34944-224">视图矩阵是更准确的使用最初使用相同的坐标系统创建的模型转换的对象。</span><span class="sxs-lookup"><span data-stu-id="34944-224">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="34944-225">创建使用一个设备附加参考的全息</span><span class="sxs-lookup"><span data-stu-id="34944-225">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="34944-226">有些的时候想要呈现一张全息图时，[仍会附加](coordinate-systems.md#attached-frame-of-reference)到设备的位置，例如具有调试信息性消息，当设备才能够确定自己的方向的面板和而非其位置在空间中。</span><span class="sxs-lookup"><span data-stu-id="34944-226">There are times when you want to render a hologram that [remains attached](coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="34944-227">若要实现此目的，我们使用附加的参考框架。</span><span class="sxs-lookup"><span data-stu-id="34944-227">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="34944-228">SpatialLocatorAttachedFrameOfReference 类定义是相对于该设备，而不是实际的坐标系统。</span><span class="sxs-lookup"><span data-stu-id="34944-228">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="34944-229">该框架具有固定的标题相对于指向方向用户面对的参考框架创建时的用户的环境。</span><span class="sxs-lookup"><span data-stu-id="34944-229">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="34944-230">自此时起，此参考框架中的所有方向都是相对于该固定标题，即使在用户旋转设备。</span><span class="sxs-lookup"><span data-stu-id="34944-230">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="34944-231">对于 HoloLens，此帧的坐标系统的原点位于用户的 head 旋转中心的以便其位置不受头旋转。</span><span class="sxs-lookup"><span data-stu-id="34944-231">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="34944-232">您的应用程序可以指定相对于定位用户全息此点的偏移量。</span><span class="sxs-lookup"><span data-stu-id="34944-232">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="34944-233">若要获取 SpatialLocatorAttachedFrameOfReference，使用 SpatialLocator 类并调用 CreateAttachedFrameOfReferenceAtCurrentHeading。</span><span class="sxs-lookup"><span data-stu-id="34944-233">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="34944-234">请注意，这适用于整个范围的 Windows Mixed Reality 设备。</span><span class="sxs-lookup"><span data-stu-id="34944-234">Note that this applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="34944-235">使用附加到设备的参考帧</span><span class="sxs-lookup"><span data-stu-id="34944-235">Use a reference frame attached to the device</span></span>

<span data-ttu-id="34944-236">以下各节讨论一下我们在 Windows 全息版的应用程序模板，以使附加设备的参考框架使用此 API 中的更改。</span><span class="sxs-lookup"><span data-stu-id="34944-236">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="34944-237">请注意，此"附加"hologram 将是静态的或锚定全息，同时还可以暂时找不到它在世界中的位置设备时使用。</span><span class="sxs-lookup"><span data-stu-id="34944-237">Note that this "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="34944-238">首先，我们更改了要存储而不是 SpatialStationaryFrameOfReference SpatialLocatorAttachedFrameOfReference 的模板：</span><span class="sxs-lookup"><span data-stu-id="34944-238">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="34944-239">从**HolographicTagAlongSampleMain.h**:</span><span class="sxs-lookup"><span data-stu-id="34944-239">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="34944-240">从**HolographicTagAlongSampleMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="34944-240">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="34944-241">在更新期间，我们现在获得从获取与帧预测的时间戳处的坐标系统。</span><span class="sxs-lookup"><span data-stu-id="34944-241">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="34944-242">获取空间指针姿势并按照用户的视线移动</span><span class="sxs-lookup"><span data-stu-id="34944-242">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="34944-243">我们想要跟踪该用户的我们的示例 hologram[注视](gaze.md)，类似于如何 holographic shell 可以按照用户的视线移动。</span><span class="sxs-lookup"><span data-stu-id="34944-243">We want our example hologram to follow the user's [gaze](gaze.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="34944-244">为此，我们需要 SpatialPointerPose 获得相同的时间戳。</span><span class="sxs-lookup"><span data-stu-id="34944-244">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="34944-245">此 SpatialPointerPose 具有所需位置根据全息图的信息[用户的当前标题](gaze,-gestures,-and-motion-controllers-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="34944-245">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze,-gestures,-and-motion-controllers-in-directx.md).</span></span>

<span data-ttu-id="34944-246">由于用户舒适的原因，我们使用线性内插 ("lerp")，以便它的时间段内发生的平滑的位置更改。</span><span class="sxs-lookup"><span data-stu-id="34944-246">For reasons of user comfort, we use linear interpolation ("lerp") to smooth the change in position such that it occurs over a period of time.</span></span> <span data-ttu-id="34944-247">这是用户比锁定到其提供注视全息图更舒服。</span><span class="sxs-lookup"><span data-stu-id="34944-247">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="34944-248">Lerping 尾随 hologram 位置还使我们能够通过抑制移动; 稳定全息图如果我们不进行此抑制，用户会看到由于什么通常被认为是感觉不移动用户的头的抖动全息图。</span><span class="sxs-lookup"><span data-stu-id="34944-248">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement; if we did not do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="34944-249">从**StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="34944-249">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="34944-250">对于调试面板中，您可以选择重新定位到端关闭 hologram 有点以便使它不会不影响您的观看。</span><span class="sxs-lookup"><span data-stu-id="34944-250">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it does not obstruct your view.</span></span> <span data-ttu-id="34944-251">下面是举例说明如何执行的操作。</span><span class="sxs-lookup"><span data-stu-id="34944-251">Here's an example of how you might do that.</span></span>

<span data-ttu-id="34944-252">有关**StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="34944-252">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="34944-253">旋转面临着相机的全息图</span><span class="sxs-lookup"><span data-stu-id="34944-253">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="34944-254">它是不足够简单地定位张全息图，在这种情况下是四;我们还必须旋转要面对用户的对象。</span><span class="sxs-lookup"><span data-stu-id="34944-254">It is not enough to simply position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="34944-255">请注意在世界空间中发生此旋转，这是因为此类型的公告板，全息图保持用户的环境的一部分。</span><span class="sxs-lookup"><span data-stu-id="34944-255">Note that this rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="34944-256">视图空间公告板不甚流畅因为全息图会被锁定到显示方向;在这种情况下，您还必须执行内插之间以获取不会中断立体声呈现的视图空间布告栏转换左侧和右侧的视图矩阵。</span><span class="sxs-lookup"><span data-stu-id="34944-256">View-space billboarding is not as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices in order to acquire a view-space billboard transform that does not disrupt stereo rendering.</span></span> <span data-ttu-id="34944-257">在这里，我们旋转面临着用户的 X 和 Z 轴上。</span><span class="sxs-lookup"><span data-stu-id="34944-257">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="34944-258">从**StationaryQuadRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="34944-258">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="34944-259">呈现附加全息图</span><span class="sxs-lookup"><span data-stu-id="34944-259">Render the attached hologram</span></span>

<span data-ttu-id="34944-260">对于此示例中，我们还选择呈现的全息图 SpatialLocatorAttachedReferenceFrame 的坐标系统中这是我们放置全息图。</span><span class="sxs-lookup"><span data-stu-id="34944-260">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="34944-261">（如果我们决定使用另一个坐标系统来呈现，我们需要获取从设备附加参考帧的坐标系统转换到该坐标系统。）</span><span class="sxs-lookup"><span data-stu-id="34944-261">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="34944-262">从**HolographicTagAlongSampleMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="34944-262">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="34944-263">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="34944-263">That's it!</span></span> <span data-ttu-id="34944-264">全息图将现在"跟踪"是用户的视线移动方向的前面 2 米的位置。</span><span class="sxs-lookup"><span data-stu-id="34944-264">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="34944-265">此示例还会加载更多的内容-请参阅 StationaryQuadRenderer.cpp。</span><span class="sxs-lookup"><span data-stu-id="34944-265">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="34944-266">处理跟踪丢失</span><span class="sxs-lookup"><span data-stu-id="34944-266">Handling tracking loss</span></span>

<span data-ttu-id="34944-267">当设备找不到本身在世界中时，应用内体验"跟踪丢失"。</span><span class="sxs-lookup"><span data-stu-id="34944-267">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="34944-268">Windows Mixed Reality 应用应该能够处理此类中断到位置跟踪系统。</span><span class="sxs-lookup"><span data-stu-id="34944-268">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="34944-269">这些过程中中断，可以观察到，并响应通过默认 SpatialLocator LocatabilityChanged 事件创建。</span><span class="sxs-lookup"><span data-stu-id="34944-269">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="34944-270">从**AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="34944-270">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="34944-271">当您的应用程序收到 LocatabilityChanged 事件时，它可以根据需要更改行为。</span><span class="sxs-lookup"><span data-stu-id="34944-271">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="34944-272">例如，在 PositionalTrackingInhibited 状态下，您的应用程序可以暂停正常操作和呈现[尾随全息图](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference)显示一条警告消息。</span><span class="sxs-lookup"><span data-stu-id="34944-272">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="34944-273">Windows 全息版的应用程序模板提供了已为你创建一个 LocatabilityChanged 处理程序。</span><span class="sxs-lookup"><span data-stu-id="34944-273">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="34944-274">默认情况下，它显示一条警告在调试控制台位置跟踪不可用时。</span><span class="sxs-lookup"><span data-stu-id="34944-274">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="34944-275">可以将代码添加到此处理程序将根据需要从您的应用程序提供的响应。</span><span class="sxs-lookup"><span data-stu-id="34944-275">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="34944-276">从**AppMain.cpp:**</span><span class="sxs-lookup"><span data-stu-id="34944-276">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="34944-277">空间映射</span><span class="sxs-lookup"><span data-stu-id="34944-277">Spatial mapping</span></span>

<span data-ttu-id="34944-278">[空间映射](spatial-mapping-in-directx.md)的 api 使用的坐标系统，以获取模型转换为网格图面。</span><span class="sxs-lookup"><span data-stu-id="34944-278">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="34944-279">请参阅</span><span class="sxs-lookup"><span data-stu-id="34944-279">See also</span></span>
* [<span data-ttu-id="34944-280">坐标系统</span><span class="sxs-lookup"><span data-stu-id="34944-280">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="34944-281">空间的定位点</span><span class="sxs-lookup"><span data-stu-id="34944-281">Spatial anchors</span></span>](spatial-anchors.md)
* <span data-ttu-id="34944-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a></span><span class="sxs-lookup"><span data-stu-id="34944-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="34944-283">提供注视、 手势和 DirectX 中的动作控制器</span><span class="sxs-lookup"><span data-stu-id="34944-283">Gaze, gestures, and motion controllers in DirectX</span></span>](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="34944-284">在 DirectX 空间映射</span><span class="sxs-lookup"><span data-stu-id="34944-284">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
