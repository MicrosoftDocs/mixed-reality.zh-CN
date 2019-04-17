---
title: 在 Unity 中的空间映射
description: 呈现和与其碰撞周围 Unity 中的实际的几何图形。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 空间映射，呈现器、 碰撞体、 网格、 扫描、 组件
ms.openlocfilehash: f938f5921cb2c06342a9ebcd376d690c10584df9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593079"
---
# <a name="spatial-mapping-in-unity"></a>在 Unity 中的空间映射

本主题介绍如何使用[空间映射](spatial-mapping.md)在 Unity 项目中，检索表示用于放置、 封闭、 空间分析和的详细信息的 HoloLens 设备周围的世界中表面的三角形网格。

Unity 包括对空间映射，按以下方式公开给开发人员的完全支持：
1. 空间映射 MixedRealityToolkit 中可用的组件，其中提供的方便和快速路径入门空间映射
2. 空间映射较低级别 Api，为提供的完全控制并启用更复杂的应用程序特定自定义

若要在应用中使用空间的映射，spatialPerception 功能需要在你的 AppxManifest 中设置。

## <a name="setting-the-spatialperception-capability"></a>设置 SpatialPerception 功能

若要使用空间的映射数据的应用，必须启用 SpatialPerception 功能。

如何启用 SpatialPerception 功能：
1. 在 Unity 编辑器中打开 **"播放器设置"** 窗格 (编辑 > 项目设置 > 播放机)
2. 单击 **"Windows 应用商店"** 选项卡
3. 展开 **"发布设置"** ，并检查 **"SpatialPerception"** 中的功能 **"功能"** 列表

请注意，是否你已向 Visual Studio 解决方案导出你的 Unity 项目，你将需要导出到新文件夹或手动[在 Visual Studio 中的 AppxManifest 中设置此功能](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)。

空间映射还需要至少 10.0.10586.0 MaxVersionTested:
1. 在 Visual Studio 中，右键单击**Package.appxmanifest**在解决方案资源管理器中，选择**查看代码**
2. 查找行指定**TargetDeviceFamily**并将更改**MaxVersionTested ="10.0.10240.0"** 到**MaxVersionTested ="10.0.10586.0"**
3. **保存**Package.appxmanifest。

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>开始使用 Unity 的内置空间映射组件

Unity 提供两个组件： 用于轻松地添加到应用中，空间映射**空间映射呈现器**并**空间映射碰撞体**。

### <a name="spatial-mapping-renderer"></a>空间映射呈现器

空间映射呈现器允许的空间的映射网格的可视化效果。

![空间映射在 Unity 中的呈现器](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>空间映射碰撞体

空间映射碰撞体允许 holographic 内容 （或字符） 交互，如物理引擎，与空间映射网格。

![在 Unity 中的空间映射碰撞体](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>使用内置空间映射组件

如果你想要同时可视化和与物理面进行交互，您可以向您的应用程序中添加这两个组件。

若要在 Unity 应用中使用这两个组件：
1. 选择要在其中检测空间图面上的网格区域的中心在一个 GameObject。
2. 在检查器窗口中，**添加组件** > **XR** > **空间映射碰撞体** 或**空间映射呈现器**。

有关如何使用这些组件在更多详细信息<a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 文档站点</a>。

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>超越内置空间映射组件

这些组件使其拖放轻松开始使用空间的映射。  当你想要更进一步时，有两个主要路径浏览：
* 为你自己的较低级别网格处理，请参阅下面有关的低级别的空间映射脚本 API 的一节。
* 若要进行更高级别的网格分析时，请参阅下面有关 SpatialUnderstanding 库中的一节<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>。

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>使用低级别 Unity 空间映射 API

如果需要更多的控制不是获得的空间映射的呈现器和空间映射碰撞体组件，可以使用低级别的空间映射脚本 Api。

**命名空间：***UnityEngine.XR.WSA*<br>
**类型**:*SurfaceObserver*， *SurfaceChange*， *SurfaceData*， *SurfaceId*

以下是使用空间的映射 Api 的应用程序的建议流程的概述。

### <a name="set-up-the-surfaceobservers"></a>设置 SurfaceObserver(s)

实例化一个 SurfaceObserver 对象的所需空间映射的数据空间的每个应用程序定义的区域。

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

指定每个 SurfaceObserver 对象将通过调用 SetVolumeAsSphere、 SetVolumeAsAxisAlignedBox、 SetVolumeAsOrientedBox 或 SetVolumeAsFrustum 提供数据的空间的区域。 可以通过只需调用这些方法之一来重新定义的空间在将来的区域。

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

当调用 SurfaceObserver.Update() 时，必须提供 SurfaceObserver 的区域的空间映射系统具有的新信息的空间中每个空间表面一个处理程序。 为一个空间表面接收处理程序：

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>处理图面上的更改

有几个主要的情况下，若要处理。 添加和更新其可以使用相同的代码路径并将其删除。
* 在示例中已添加和更新情况下，我们将添加或获取 GameObject 表示，这从字典 mesh、 SurfaceData 结构创建使用所需的组件，然后调用 RequestMeshDataAsync 来填充网格数据 GameObject 和定位在场景中。
* 中已删除的情况下，我们将删除从字典中表示此网格的 GameObject，并将其销毁。

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a>处理数据就绪

OnDataReady 处理程序接收 SurfaceData 对象。 WorldAnchor、 MeshFilter 和 （可选） 的 MeshCollider 对象，它包含反映相关联的空间表面的最新状态。 （可选） 执行分析和/或[处理](spatial-mapping.md#mesh-processing)通过访问 MeshFilter 对象的网格成员的网格数据。 呈现与最新的网格在空间面和 （可选） 将其用于物理冲突和 raycasts。 请务必确认 SurfaceData 内容均不为 null。

### <a name="start-processing-on-updates"></a>开始处理更新

SurfaceObserver.Update() 应该调用延迟，并非每个帧。

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>更高级别的网格分析：SpatialUnderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>是 holographic 开发基于全息版的 Unity Api 有用实用工具代码的集合。

### <a name="spatial-understanding"></a>空间了解

在现实环境中放置全息时是通常需要转超出空间映射网格图面平面。 完成放置后按，更高级别的环境了解最好。 这通常需要决定什么 floor、 ceiling 和墙。 此外，针对到确定 holographic 对象最理想的物理位置的放置约束的一组优化的能力。

在开发期间的 Young Conker 和片段，Asobo Studios 遇到此问题头上，为此开发聊天室解算器。 每个这些游戏具有游戏的特定需求，但它们会共享核心空间了解技术。 库封装这项技术，允许您快速查找在墙上上限，将对象置于空白空间标识 HoloToolkit.SpatialUnderstanding 放置要坐下来，字符和大量其他空间了解查询的时间。

所有是源代码的包括在内，从而可以根据需求进行自定义和与社区共享您的改进。 代码C++包装到 UWP dll 解算器和将其公开到 Unity 中 MixedRealityToolkit 包含预设中会显示下拉。

### <a name="understanding-modules"></a>了解模块

有三个模块公开的主接口： 简单的图面和空间查询、 对象检测的形状和对象放置解算器用于约束基于放置的对象集的拓扑。 下面描述了其中每项功能。 除了三个主模块接口，ray 强制转换接口可用于检索标记的图面类型和自定义的那样严密 playspace 网格可以复制出来。

### <a name="ray-casting"></a>Ray 强制转换

聊天室已经过扫描并完成后，标签会在内部生成对于 floor、 ceiling 和墙等的图面。 "PlayspaceRaycast"函数使用一条射线并返回如果射线与已知的图面有冲突，如果是这样，该图面中的"RaycastResult"窗体有关的信息。

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

在内部，raycast 计算针对 playspace 的立方计算 8 cm voxel 表示形式。 每个 voxel 包含一组的图面上元素与处理的拓扑数据 (也称为 surfels)。 包含在相交的 voxel 单元格中 surfels 进行比较，用于查看拓扑信息的最佳匹配项。 此拓扑的数据包含标记返回"SurfaceTypes"枚举的窗体以及相交曲面的图面区域。

在 Unity 示例中，游标将一条转换为每个帧。 首先，对 Unity 的碰撞体。 其次，对了解模块的世界表示形式。 和最后，再次 UI 元素。 在此应用程序中，UI 将获取优先级，接下来了解结果和最后，Unity 的碰撞体。 SurfaceType 被报告为旁的文本。

![图面上的类型标记旁](images/su-raycastresults-300px.jpg)<br>
*图面上的类型标记旁*

### <a name="topology-queries"></a>拓扑查询

在 DLL 内的拓扑管理器处理环境的标记。 如上所述，surfels，包含在 voxel 卷中存储的大量数据。 此外，"PlaySpaceInfos"结构用于存储有关 playspace，包括世界对齐方式 （下文更多详细信息）、 floor、 和 ceiling 高度信息。 启发式方法用于确定 floor、 ceiling 和墙。 例如，与大于 1 m2 图面区域的最大和最小水平的面被视为基底。 请注意在此过程中还使用在扫描过程中的照相机路径。

公开的拓扑结构管理器的查询的子集通过 dll 公开出。 公开的拓扑查询如下所示。

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

每个查询具有一组特定的查询类型参数。 在以下示例中，用户指定的最小高度和宽度的所需的卷、 更高版本的基底，最少的许可卷的前面放置最小高度。 所有度量值是以米为单位。

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

每个这些查询采用"TopologyResult"结构的预先分配的数组。 "LocationCount"参数指定传入的数组的长度。 返回值将报告返回位置数。 此数字大于永远不会传递"locationCount"参数中。

"TopologyResult"包含返回的卷、 面向公众的方向 （即正常），并找到空间的维度的中间位置。

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

请注意，在 Unity 示例，这些查询的每个虚拟用户界面面板中的按钮为链接。 硬示例代码的合理值到这些查询每个参数。 有关更多示例的示例代码中看到 SpaceVisualizer.cs。

### <a name="shape-queries"></a>形状的查询

在 dll 内形状分析器 ("ShapeAnalyzer_W") 使用拓扑分析器来匹配由用户定义的自定义形状。 Unity 示例定义了一组形状，并公开应用程序内查询菜单上的形状选项卡中，通过输出结果。目的是用户可以定义自己对象的形状查询并使其应用程序所需的使用。

请注意，形状 analysis 工作仅水平图面上。 躺椅，例如，是由平面席位面和平面顶部躺椅上重新定义。 Shape 查询查找与两个表面对齐和连接特定大小、 高度和长宽范围的两个面。 使用 Api 术语，couch 席位和后顶部是形状的组件和对齐要求是形状组件的约束。

在 Unity 示例 (ShapeDefinition.cs) 中为"sittable"对象定义的示例查询如下所示。

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

每个 shape 查询由一组形状组件，每个都有一组组件约束和一组形状约束定义其列出的组件之间的依赖项。 （因为只有一个组件），此示例在单个组件定义和组件之间的任何形状约束中包含三个约束。

与此相反，couch 形状具有两个形状组件和四个形状约束。 请注意，由它们在用户的组件列表 （0 和 1 在此示例中） 中的索引标识组件。

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

轻松创建自定义形状定义 Unity 模块中提供了包装器函数。 可以在"ShapeComponentConstraint"和"ShapeConstraint"结构"SpatialUnderstandingDll.cs"中找到的组件和形状的约束的完整列表。

![此图面上找到矩形形状](images/su-shapequery-300px.jpg)<br>
*此图面上找到矩形形状*

### <a name="object-placement-solver"></a>对象放置解算器

对象放置解算器可以用于确定放置您的对象的物理空间中的理想位置。 解算器将查找最适合给定的对象规则和约束的位置。 此外，对象查询持续，直到使用"Solver_RemoveObject"中删除的对象或"Solver_RemoveAllObjects"调用，从而允许约束多重对象位置。 对象放置查询由三部分组成： 参数、 一组规则，与约束的列表的位置类型。 若要运行查询，使用以下 API。

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

此函数采用对象名称、 位置定义和规则和约束的列表。 C#包装器提供构造帮助器函数来简化规则和约束构造。 放置定义包含查询类型 – 也就是说，以下值之一。

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

每个位置类型具有一组唯一的类型参数。 "ObjectPlacementDefinition"结构包含一组用于创建这些定义的静态帮助器函数。 例如，若要查找的地板上放置对象的地方，可以使用以下函数。 公共静态 ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) 中添加到的位置类型，可以提供一组规则和约束。 不能违反规则。 满足的类型和规则的可能的放置位置然后进行了优化针对的约束的集合，以便选择最佳的放置位置。 提供静态创建函数，可以创建的每个规则和约束。 下面提供了一个示例规则和约束构造函数。

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

对象的下方放置查询将查找一个位置来图面的边缘放置一半计量多维数据集、 远离其他以前放置对象和中心附近的房间。

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

如果成功，包含在中放置的位置的"ObjectPlacementResult"结构尺寸和方向返回。 此外，位置被添加到放置对象的 dll 的内部列表。 后续放置查询会考虑到此对象。 Unity 示例中的"LevelSolver.cs"文件包含更多的示例查询。

![结果的对象放置](images/su-objectplacement-1000px.jpg)<br>
*图 3:蓝色框如何地板上的三个位置，从结果查询与从照相机位置规则*

当解决所需的级别或应用程序方案的多个对象的放置位置，第一个解决到最大化可找到空间的概率的顺序不可或缺的大型对象。 放置顺序非常重要。 如果找不到对象位置，请尝试不太受约束的配置。 具有一组的回退配置对跨多个空间配置支持的功能至关重要。

### <a name="room-scanning-process"></a>聊天室扫描进程

虽然 HoloLens 由提供的空间映射解决方案专为一般性还不足以满足整个域中问题所在领域的需求，生成空间了解模块来支持这两个特定游戏的需求。 其解决方案的结构围绕特定的进程和假设，总结如下。

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

用户驱动的 playspace"绘制"– 在扫描阶段，用户将移动，并查找在播放上发展步伐，有效地进行绘制的区域应包括。 务必在此阶段提供用户反馈是生成的网格。 室内 home 或 office 设置 – 函数围绕平面曲面和墙成直角设计的查询。 这是软限制。 但是，在扫描阶段，主坐标轴分析完成优化主版本号和次的轴的网格分割。 所包含的 SpatialUnderstanding.cs 文件管理扫描阶段的过程。 它将调用以下函数。

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

扫描的流，由"SpatialUnderstanding"行为驱动调用 InitScan，然后 UpdateScan 每个帧。 当统计信息查询报告合理覆盖率时，允许用户为 airtap 调用 RequestFinish 指示扫描阶段结束。 UpdateScan 继续调用之前返回值指示 dll 已完成处理。

### <a name="understanding-mesh"></a>了解网格

了解 dll 在内部存储 playspace 为调整大小的 8 cm voxel 多维数据集的网格。 在扫描的初始阶段，完成主成分分析以确定聊天室的轴。 在内部，它将存储到这些轴对齐其 voxel 空间。 通过从 voxel 卷提取等值面大约每隔一秒生成网格。 

![生成从 voxel 卷生成的网格](images/su-custommesh.jpg)<br>
*生成从 voxel 卷生成的网格*

## <a name="troubleshooting"></a>疑难解答
* 确保已设置[SpatialPerception](#setting-the-spatialperception-capability)功能
* 丢失跟踪时下, 一步 OnSurfaceChanged 事件将删除所有网格。

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>混合的现实工具包中的空间映射
与混合现实 Toolkit v2 使用空间映射的详细信息，请参阅<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">空间感知部分</a>MRTK docs。

## <a name="see-also"></a>请参阅
* [MR 空间 230:空间映射](holograms-230.md)
* [坐标系统](coordinate-systems.md)
* [在 Unity 中的坐标系统](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
