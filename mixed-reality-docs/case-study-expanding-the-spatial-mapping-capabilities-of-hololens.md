---
title: 案例研究-扩展 HoloLens 的空间映射功能
description: 当创建适用于 Microsoft HoloLens 我们第一个应用，我们急于想看到只是程度我们无法在设备上按空间映射的边界。
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality HoloLens，空间映射
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592552"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>案例研究-扩展 HoloLens 的空间映射功能

当创建适用于 Microsoft HoloLens 我们第一个应用，我们急于想看到只是程度我们无法在设备上按空间映射的边界。 Jeff Evertt，Microsoft Studios 的软件工程师介绍了如何一项新技术已开发出更好地控制如何在用户的实际环境中放置全息的需要。

## <a name="watch-the-video"></a>观看视频

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>超出空间映射

虽然我们正在处理[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)并[Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)、 两个 HoloLens 的第一个游戏，我们发现我们的执行过程放置全息现实生活中，我们需要更高的级别有关用户的环境的了解。 每个游戏都有其自己特定位置的要求：在段落中，例如，我们希望能够区分不同的图面 — 例如 floor 或表，可以将线索置于相关位置。 我们还想要能够识别，坐下来的栩栩如生 holographic 字符无法如 couch 或椅子的图面。 在 Young Conker 我们想 Conker 和他的对手能够引发图面玩家的房间中用作平台。

[Asobo Studios](http://www.asobostudio.com/index.html)，这些游戏，我们开发合作伙伴直接针对遇到此问题并创建一种技术，扩展了 HoloLens 的空间映射功能。 使用此，我们无法分析玩家的空间并确定如墙壁、 表、 椅子和地面图面。 它还会为我们提供的功能优化针对一组限制，以确定 holographic 对象的最佳位置。

## <a name="the-spatial-understanding-code"></a>空间理解代码

我们花费了 Asobo 的原始代码，并创建一个库，它封装此技术。 Microsoft 和 Asobo 具有现在开放源代码的此代码并使其能够在[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) ，以便在您自己的项目中使用。 从而可以根据需求进行自定义和与社区共享您的改进中包含所有源代码都。 代码C++包装到 UWP DLL 解算器和将其公开到使用 Unity [MixedRealityToolkit 中包含的嵌入式预设](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)。

有许多有用的查询包含在 Unity 示例中，您可以找到在墙上的空白空间，将天花板上或在地板上大空间上放置对象、 识别对字符设有和大量的其他空间了解查询的位置。

虽然 HoloLens 由提供的空间映射解决方案专为一般性还不足以满足整个域中问题所在领域的需求，生成空间了解模块来支持这两个特定游戏的需求。 在这种情况下，其解决方案是围绕一个特定的进程和一组假设的结构化：
* **固定大小 playspace**:用户在 init 调用中指定的最大 playspace 大小。
* **一次性扫描进程**:该过程需要离散扫描其中用户走周围的阶段，但定义 playspace。 扫描已完成后，查询函数将无法正常之前。
* **用户驱动的 playspace"绘制"**:在扫描阶段，用户将移动，并查找围绕 playspace，有效地进行绘制的区域应包括。 务必在此阶段提供用户反馈是生成的网格。
* **室内家庭或办公室安装**:查询函数是围绕平面曲面和墙成直角设计的。 这是软限制。 但是，在扫描阶段，主坐标轴分析完成优化主版本号和次的轴的网格分割。

### <a name="room-scanning-process"></a>聊天室扫描进程

当空间了解模块加载时，将执行的第一个操作是扫描你的空间，因此所有可用的图面，如 floor、 ceiling 和墙 — 问题被确定并标记为。 在扫描过程中，你看你的聊天室和"画图应包含在扫描过程中的区域。

在此阶段中所示网格是可让用户知道聊天室的哪些部分正在扫描的可视反馈的重要部分。 空间了解模块的 DLL 在内部存储 playspace 为调整大小的 8 cm voxel 多维数据集的网格。 在扫描的初始阶段，完成主成分分析以确定聊天室的轴。 在内部，它将存储到这些轴对齐其 voxel 空间。 通过从 voxel 卷提取等值面大约每隔一秒生成网格。

![空间映射网格以白色和了解 playspace 网格以绿色](images/spatial-mapping-500px.png)

空间映射网格以白色和了解 playspace 网格以绿色



所包含的 SpatialUnderstanding.cs 文件管理扫描阶段的过程。 它将调用以下函数：
* **SpatialUnderstanding_Init**:开始时调用一次。
* **GeneratePlayspace_InitScan**:指示应开始扫描阶段。
* **GeneratePlayspace_UpdateScan_DynamicScan**:调用每个帧来更新扫描的过程。 照相机位置和方向传入，并且用于 playspace 绘制进程，上面所述。
* **GeneratePlayspace_RequestFinish**:调用以完成 playspace。 这将使用"绘制"扫描阶段的区域来定义和锁定 playspace。 在扫描阶段，以及查询自定义网格提供用户的反馈期间，应用程序可以查询统计信息。
* **Import_UnderstandingMesh**:在扫描期间**SpatialUnderstandingCustomMesh**模块提供和了解预设可放置的行为将定期查询进程生成的自定义的网格。 此外，这是一次后扫描已完成。

扫描的流，由驱动**SpatialUnderstanding**行为将调用**InitScan**，然后**UpdateScan**每个帧。 当统计信息查询报告合理覆盖率时，用户可以 airtap 调用**RequestFinish**指示扫描阶段结束。 **UpdateScan**继续调用之前返回值指示 DLL 已完成处理。

## <a name="the-queries"></a>查询

扫描完成后，你将能够访问三种不同类型的接口中的查询：
* **拓扑查询**:这些是聊天室的基于扫描的拓扑的快速查询。
* **调整查询**:这些利用拓扑查询以查找良好匹配到定义的自定义形状的水平表面的结果。
* **对象放置查询**:这些是更复杂的查询查找基于一组规则和约束对象的最佳的位置。

除了三个主查询中，没有可用于检索标记的图面类型的光线投射的细节接口，并且自定义的那样严密空间网格可以复制出来。

### <a name="topology-queries"></a>拓扑查询

在 DLL 内的拓扑管理器处理环境的标记。 如上所述，大量数据存储在 surfels，包含在 voxel 卷中。 此外， **PlaySpaceInfos**结构用于存储有关 playspace，包括世界对齐方式 （下文更多详细信息）、 floor、 和 ceiling 高度的信息。

启发式方法用于确定 floor、 ceiling 和墙。 例如，与大于 1 m2 图面区域的最大和最小水平的面被视为基底。 请注意在此过程中还使用在扫描过程中的照相机路径。

公开的拓扑结构管理器的查询的子集通过 DLL 公开出。 公开的拓扑查询如下所示：
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

每个查询具有一组特定的查询类型参数。 在以下示例中，用户指定的最小高度和宽度的所需的卷、 更高版本的基底，最少的许可卷的前面放置最小高度。 所有度量值是以米为单位。




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

每个这些查询采用预分配的数组**TopologyResult**结构。 **LocationCount**参数指定传入的数组的长度。 返回值将报告返回位置数。 此数字大于永远不会传入的**locationCount**参数。

**TopologyResult**包含返回的卷、 面向公众的方向 （即正常），并找到空间的维度的中间位置。




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

请注意，在 Unity 示例，这些查询的每个虚拟用户界面面板中的按钮为链接。 硬示例代码的合理值到这些查询每个参数。 请参阅*SpaceVisualizer.cs*中更多示例的示例代码。

### <a name="shape-queries"></a>形状的查询

在 DLL，形状分析器 (**ShapeAnalyzer_W**) 使用拓扑分析器以匹配由用户定义的自定义形状。 Unity 示例有一组预定义的形状选项卡上的查询菜单中显示的形状。

请注意，形状 analysis 工作仅水平图面上。 躺椅，例如，是由平面席位面和平面顶部躺椅上重新定义。 Shape 查询查找与两个表面对齐和连接特定大小、 高度和长宽范围的两个面。 使用 Api 术语，坐在沙发上和躺椅后面的顶部是形状组件和要求的对齐方式形状组件约束。

在 Unity 示例中定义的示例查询 (**ShapeDefinition.cs**)，对于"sittable"对象是按如下所示：




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

每个形状查询由一组形状组件，每个都有一组组件约束和一组形状约束，其中列出了组件之间的依赖关系定义。 （因为只有一个组件），此示例在单个组件定义和组件之间的任何形状约束中包含三个约束。

与此相反，couch 形状具有两个形状组件和四个形状约束。 请注意，由它们在用户的组件列表 （0 和 1 在此示例中） 中的索引标识组件。




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

轻松创建自定义形状定义 Unity 模块中提供了包装器函数。 组件和形状的约束的完整列表可在**SpatialUnderstandingDll.cs**内**ShapeComponentConstraint**并**ShapeConstraint**结构。

![蓝色矩形突出显示了椅子 shape 查询的结果。](images/chair-shape-query-500px.png)

蓝色矩形突出显示了椅子 shape 查询的结果。



### <a name="object-placement-solver"></a>对象放置解算器

可以使用对象放置查询以确定放置您的对象的物理空间中的理想位置。 解算器将查找给定的对象规则和约束的最佳的位置。 此外，对象查询持续，直到使用删除的对象**Solver_RemoveObject**或**Solver_RemoveAllObjects**调用，从而允许约束多重对象位置。

对象放置查询由三部分组成： 参数、 一组规则，与约束的列表的位置类型。 若要运行查询，使用以下 API:




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
此函数采用对象名称、 位置定义和规则和约束的列表。 C#包装器提供构造帮助程序函数来简化规则和约束构造。 放置定义包含查询类型，即以下值之一：




```
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

每个位置类型具有一组唯一的类型参数。 **ObjectPlacementDefinition**结构包含一组用于创建这些定义的静态帮助器函数。 例如，若要查找的地板上放置对象的地方，可以使用以下函数： 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

除了放置类型，可以提供一组规则和约束。 不能违反规则。 然后，满足的类型和规则的可能的放置位置进行了优化选择最佳的放置位置的约束的一组。 提供静态创建函数，可以创建的每个规则和约束。 下面提供了一个示例规则和约束构造函数。




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

下面的对象放置查询寻找一半计量多维数据集放入图面的边缘、 从其他以前放置对象和中心附近的房间。




```
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

如果成功， **ObjectPlacementResult**返回结构，它包含的放置位置、 尺寸和方向。 此外，位置被添加到放置对象的 DLL 的内部列表。 后续放置查询会考虑到此对象。 **LevelSolver.cs** Unity 示例中的文件包含更多的示例查询。

![蓝色方框显示使用"立即从照相机位置"规则的三个位置上 Floor 查询的结果。](images/away-from-camera-position-500px.png)

蓝色方框显示使用"立即从照相机位置"规则的三个位置上 Floor 查询的结果。


**提示：**
* 当解决所需的级别或应用程序方案的多个对象的放置位置，第一个解决不可或缺和大型对象，若要最大化可找到空间的概率。
* 放置顺序非常重要。 如果找不到对象位置，请尝试不太受约束的配置。 具有一组的回退配置对跨多个空间配置支持的功能至关重要。

### <a name="ray-casting"></a>Ray 强制转换

除了三个主查询中，ray 强制转换接口可用于检索标记的图面类型，并且可以复制自定义的那样严密 playspace 网格出空间已经过扫描并最终确定之后, 标签会在内部生成图面，例如floor、 ceiling 和墙。 **PlayspaceRaycast**函数将一条射线并返回如果射线与已知的图面有冲突，如果是这样，该图面中的窗体有关的信息**RaycastResult**。 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

在内部，raycast 计算针对 playspace 的立方计算 8 cm voxel 表示形式。 每个 voxel 包含一组的图面上元素与处理的拓扑数据 (也称为 surfels)。 包含在相交的 voxel 单元格中 surfels 进行比较，用于查看拓扑信息的最佳匹配项。 此拓扑的数据包含标记的形式返回**SurfaceTypes**枚举，以及相交曲面的图面区域。

在 Unity 示例中，游标将一条转换为每个帧。 首先，对 Unity 的碰撞体;其次，对了解模块的世界表示形式;和最后，对 UI 元素。 在此应用程序 UI 获取优先级，然后了解结果，并最后，Unity 的碰撞体。 **SurfaceType**报告为旁的文本。

![Raycast 结果报告与 floor 交集。](images/raycast-result-500px.jpg)

Raycast 结果报告与 floor 交集。


## <a name="get-the-code"></a>获取代码

开放源代码现已推出[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)。 告知我们[HoloLens 开发人员论坛](https://forums.hololens.com/)如果在项目中使用代码。 我们迫不及待地想看到使用它做什么 ！

## <a name="about-the-author"></a>关于作者

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b>是一种软件工程主管，他曾在 HoloLens 上早期阶段，从孵化体验开发。 HoloLens 之前, 他曾在 Xbox Kinect 上并在游戏行业在各种平台和游戏。 Jeff 充满热情 robotics、 图形和转提示音的闪光灯操作。 他喜欢学习新内容，并使用在软件、 硬件，尤其是在两个相交处的空间。</td>
</tr>
</table>



## <a name="see-also"></a>请参阅
* [空间映射](spatial-mapping.md)
* [空间映射设计](spatial-mapping-design.md)
* [聊天室扫描可视化效果](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio:从 HoloLens 开发的一线人员获得的教训](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
