---
title: 案例研究-扩展 HoloLens 的空间映射功能
description: 在创建 Microsoft HoloLens 的第一个应用程序时, 我们渴望知道我们可以在设备上推送空间映射边界。
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 空间映射
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522699"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>案例研究-扩展 HoloLens 的空间映射功能

在创建 Microsoft HoloLens 的第一个应用程序时, 我们渴望知道我们可以在设备上推送空间映射边界。 Jeff Evertt 是 Microsoft 录音室的软件工程师, 介绍了如何开发一项新技术, 以更好地控制如何在用户的实际环境中放置全息影像。

## <a name="watch-the-video"></a>观看视频

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>超出空间映射

尽管我们处理的是[Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)的第一项游戏中的两个, 但我们发现, 当我们在物理世界中进行程序的过程放置时, 我们需要对用户的环境. 每个游戏都有其自己的特定放置需求:例如, 在片段中, 我们希望能够区分不同的图面 (如地面或表格), 以便在相关位置放置线索。 此外, 我们还希望能够确定生活空间内全息字符可能位于的表面, 如床或椅子。 在年轻的 Conker 中, 我们希望 Conker 及其对手能够将播放机房间中凸起的表面用作平台。

[Asobo 工作室](http://www.asobostudio.com/index.html)是这些游戏的开发合作伙伴, 面对这一问题, 并创建了一种可扩展 HoloLens 空间映射功能的技术。 使用此类, 我们可以分析玩家的房间, 并识别面、表、椅子和地面等表面。 它还使我们能够根据一组约束进行优化, 以确定全息对象的最佳位置。

## <a name="the-spatial-understanding-code"></a>空间理解代码

我们采用 Asobo 的原始代码, 并创建了一个封装了此技术的库。 Microsoft 和 Asobo 现在提供了此代码, 并使其在[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping)中可用, 以便你可以在自己的项目中使用。 所有源代码都包含在内, 允许你根据需求进行自定义, 并与社区分享你的改进。 C++规划求解的代码已包装到 UWP DLL 中, 并使用[MixedRealityToolkit 中包含的下拉 prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)向 Unity 公开。

Unity 示例中包含了许多有用的查询, 可用于查找墙壁上的空白空间, 将对象置于天花板上或空间上的较大空间, 确定要放置的字符的位置以及其他许多空间理解查询。

虽然 HoloLens 提供的空间映射解决方案设计为能够满足整个范围内的所有问题, 但构建了空间理解模块, 以支持两个特定游戏的需求。 因此, 其解决方案是围绕特定过程和假设集构造的:
* **固定大小 playspace**:用户指定 init 调用中的最大 playspace 大小。
* **一次性扫描进程**:此过程需要一个独立的扫描阶段, 其中用户会在其中进行操作, 定义 playspace。 在完成扫描后, 查询函数将不起作用。
* **用户驱动的 playspace "painting"** :在扫描阶段, 用户会四处移动并查看 playspace, 从而有效地绘制应包括的区域。 在此阶段, 生成的网格非常重要, 可提供用户反馈。
* **室内家庭或办公设置**:查询函数围绕平整表面和墙壁围绕直角设计。 这是一个软限制。 但是, 在扫描阶段, 将完成主轴分析以按主要轴和次要轴优化网格分割。

### <a name="room-scanning-process"></a>房间扫描过程

当您加载空间理解模块时, 您首先要扫描您的空间, 以便标识并标记所有可用的图面 (如地面、天花板和墙壁)。 在扫描过程中, 你将查找聊天室, 并 "粉刷" 应包括在扫描中的区域。

此阶段中的网格是一项非常重要的视觉反馈, 可让用户知道要扫描的房间的哪些部分。 空间理解模块的 DLL 在内部将 playspace 存储为8cm 大小 voxel 多维数据集的网格。 在扫描的初始部分中, 将完成主要组件分析以确定房间的轴。 在内部, 它存储其 voxel 空间与这些轴对齐。 大约每秒生成一次网格, 方法是从 voxel 卷中提取等值面。

![白色的空间映射网格, 并了解绿色的 playspace 网格](images/spatial-mapping-500px.png)

白色的空间映射网格, 并了解绿色的 playspace 网格



包含的 SpatialUnderstanding.cs 文件管理扫描阶段过程。 它调用以下函数:
* **SpatialUnderstanding_Init**:在开始时调用一次。
* **GeneratePlayspace_InitScan**:指示扫描阶段应开始。
* **GeneratePlayspace_UpdateScan_DynamicScan**:调用每个帧以更新扫描进程。 照相机位置和方向传入并用于 playspace 绘制过程, 如上所述。
* **GeneratePlayspace_RequestFinish**:调用以完成 playspace。 这会在扫描阶段使用 "绘制" 区域来定义和锁定 playspace。 应用程序可以在扫描阶段查询统计信息, 还可以查询自定义网格来提供用户反馈。
* **Import_UnderstandingMesh**:在扫描过程中, 模块提供并置于理解 prefab 上的**SpatialUnderstandingCustomMesh**行为会定期查询由进程生成的自定义网格。 此外, 完成扫描后, 还将执行此操作。

**SpatialUnderstanding**行为驱动的扫描流调用**InitScan**, 然后**UpdateScan**每个帧。 当统计信息查询报告合理的范围时, 用户可以 airtap 调用**RequestFinish**以指示扫描阶段的结束。 继续调用**UpdateScan** , 直到返回值指示 DLL 已完成处理。

## <a name="the-queries"></a>查询

扫描完成后, 你将能够访问接口中的三种不同类型的查询:
* **拓扑查询**:这些是基于扫描房间的拓扑的快速查询。
* **形状查询**:它们利用拓扑查询的结果来查找与您定义的自定义形状非常匹配的水平曲面。
* **对象放置查询**:这些是更复杂的查询, 可基于对象的一组规则和约束查找最佳位置。

除了三个主要查询外, 还提供了一个 raycasting 接口, 该接口可用于检索标记的表面类型和自定义的 watertight 房间网格。

### <a name="topology-queries"></a>拓扑查询

在 DLL 中, 拓扑管理器处理环境的标记。 如上所述, 很多数据存储在 surfels 中, 这些数据包含在 voxel 卷中。 此外, **PlaySpaceInfos**结构用于存储有关 playspace 的信息, 其中包括世界对齐 (有关此内容的更多详细信息)、楼层和天花板高度。

试探法用于确定地面、天花板和墙。 例如, 具有大于1个 m2 面区的最大和最低水平曲面被视为楼层。 请注意, 在此过程中也使用了扫描过程中的照相机路径。

拓扑管理器公开的查询子集通过 DLL 公开。 公开的拓扑查询如下所示:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

每个查询都具有一组特定于查询类型的参数。 在下面的示例中, 用户指定了所需的卷的最小高度 & 宽度、地面上的最小位置高度以及卷前面的最小间隙量。 所有度量都以米为单位。




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

其中每个查询都采用预分配的**TopologyResult**结构数组。 **LocationCount**参数指定传入数组的长度。 返回值报告返回的位置的数量。 此数字绝不会大于传入的**locationCount**参数。

**TopologyResult**包含返回的卷的中心位置、定向方向 (即普通) 以及找到的空间的尺寸。




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

请注意, 在 Unity 示例中, 其中每个查询都链接到 "虚拟 UI" 面板中的某个按钮。 示例将每个查询的参数硬编码为合理的值。 有关更多示例, 请参阅示例代码中的*SpaceVisualizer.cs* 。

### <a name="shape-queries"></a>形状查询

在 DLL 内部, 形状分析器 (**ShapeAnalyzer_W**) 使用拓扑分析器与用户定义的自定义形状相匹配。 Unity 示例包含一组预定义的形状, 它们显示在 "查询" 菜单的 "形状" 选项卡上。

请注意, 形状分析仅适用于水平曲面。 例如, 沙发由平面座位表面和沙发顶部的扁平顶部定义。 形状查询查找特定大小、高度和方位范围的两个图面, 两个图面对齐并连接起来。 使用 Api 术语, 沙发座位和沙发背面的顶部是形状组件, 对齐要求是形状组件约束。

"Sittable" 对象在 Unity 示例 (**ShapeDefinition.cs**) 中定义的示例查询如下所示:




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

每个形状查询都由一组形状组件定义, 每个形状组件都具有一组组件约束和一组形状约束, 其中列出了组件之间的依赖关系。 此示例在单个组件定义中包含三个约束, 组件之间没有任何形状约束 (因为只有一个组件)。

与此相反, 沙发形状具有两个形状组件和四个形状约束。 请注意, 组件由其在用户的组件列表中的索引标识 (在本示例中为0和 1)。




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

在 Unity 模块中提供包装函数以便于创建自定义形状定义。 可以在**ShapeComponentConstraint**和**ShapeConstraint**结构内的**SpatialUnderstandingDll.cs**中找到组件和形状约束的完整列表。

![蓝色矩形突出显示椅子形状查询的结果。](images/chair-shape-query-500px.png)

蓝色矩形突出显示椅子形状查询的结果。



### <a name="object-placement-solver"></a>对象放置规划求解

对象放置查询可用于确定放置对象的物理空间中的理想位置。 规划求解会根据对象规则和约束找到最佳位置。 此外, 对象查询会一直保留, 直到通过**Solver_RemoveObject**或**Solver_RemoveAllObjects**调用移除该对象, 从而允许约束的多对象位置。

对象放置查询由三个部分组成: 具有参数的放置类型、规则列表和约束列表。 若要运行查询, 请使用以下 API:




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
此函数采用对象名称、位置定义和规则和约束列表。 C#包装器提供构造帮助器函数, 可简化规则和约束构造。 "位置" 定义包含查询类型, 即:




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

每个放置类型都具有一组特定于该类型的参数。 **ObjectPlacementDefinition**结构包含一组静态 helper 函数, 用于创建这些定义。 例如, 若要查找在楼层上放置对象的位置, 可以使用以下函数: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

除了放置类型之外, 还可以提供一组规则和约束。 不能违反规则。 然后, 将根据一组约束优化满足类型和规则的位置位置, 以选择最佳放置位置。 每个规则和约束都可以通过提供的静态创建函数来创建。 下面提供了一个示例规则和约束构造函数。




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

下面的对象放置查询正在寻找一个位置, 用于将半米立方体放置在表面的边缘, 远离其他以前放置的对象, 靠近房间的中心。




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

如果成功, 则返回包含放置位置、尺寸和方向的**ObjectPlacementResult**结构。 此外, 放置将添加到 DLL 的已放置对象的内部列表中。 后续的放置查询会将此对象考虑在内。 Unity 示例中的**LevelSolver.cs**文件包含更多的示例查询。

![蓝框显示了三个位置对地面查询的结果, 其 "远离照相机位置" 规则。](images/away-from-camera-position-500px.png)

蓝框显示了三个位置对地面查询的结果, 其 "远离照相机位置" 规则。


**技巧**
* 在为级别或应用程序方案所需的多个对象进行放置位置求解时, 首先要解决不必要的和大型对象, 以最大程度地提高空间的出现概率。
* 放置顺序很重要。 如果找不到对象位置, 请尝试减少不受约束的配置。 具有一组后备配置对于跨许多房间配置支持功能至关重要。

### <a name="ray-casting"></a>Ray 转换

除了三个主要查询外, 还可以使用 ray 强制转换接口检索标记的表面类型, 在扫描并完成空间后, 可以将自定义 watertight playspace 网格复制到楼层、天花板和墙。 **PlayspaceRaycast**函数将使用一条射线, 如果该射线与已知表面冲突, 则返回, 如果是, 则返回**RaycastResult**形式的有关该曲面的信息。 


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

在内部, raycast 是针对 playspace 的计算8cm 立方 voxel 表示法计算的。 每个 voxel 包含一组具有已处理拓扑数据 (也称为 surfels) 的 surface 元素。 将比较交叉 voxel 单元中包含的 surfels 和用于查找拓扑信息的最佳匹配项。 此拓扑数据包含以**SurfaceTypes**枚举形式返回的标签, 以及相交表面的图面区域。

在 Unity 示例中, 游标将每个帧都转换为射线。 首先, 针对 Unity 的 colliders;其次, 针对理解模块的世界表示形式;最后, 针对 UI 元素。 在此应用程序中, UI 获得优先级, 然后是理解结果, 最后是 Unity 的 colliders。 **SurfaceType**将报告为光标旁边的文本。

![Raycast 结果报告与楼层的交集。](images/raycast-result-500px.jpg)

Raycast 结果报告与楼层的交集。


## <a name="get-the-code"></a>获取代码

[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)中提供了开放源代码。 如果你在项目中使用代码, 请在[HoloLens 开发人员论坛](https://forums.hololens.com/)上告知我们。 我们无法等待了解你的操作!

## <a name="about-the-author"></a>关于作者

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b>是从 incubation 到体验开发以来从一天起开始开始工作的软件工程组长。 在 HoloLens 之前, 他在各种平台和游戏的各种平台和游戏中使用了 Xbox Kinect 和游戏行业。 Jeff 是热衷于的机器人、图形和东西, 暴躁会发出嘟嘟声。 他喜欢学习新东西并处理软件、硬件, 尤其是在这两个交叉点的空间中。</td>
</tr>
</table>



## <a name="see-also"></a>请参阅
* [空间映射](spatial-mapping.md)
* [空间映射设计](spatial-mapping-design.md)
* [房间扫描可视化](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio:HoloLens 开发前端的课程](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
