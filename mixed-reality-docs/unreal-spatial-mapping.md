---
title: Unreal 中的空间映射
description: Unreal 中空间映射使用指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间映射
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840076"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal 中的空间映射

若要在 HoloLens 上启用空间映射，请确保在“项目设置”>“平台”>“HoloLens”>“功能”下的 Unreal 编辑器中，选中“空间感知”功能。  

若要选择在 HoloLens 游戏中使用空间映射，请在 ARSessionConfig 中启用“从跟踪几何生成网格数据”。  然后，HoloLens 插件将异步获取空间映射数据，并通过 MRMesh 使其在 Unreal 上显示。 

![空间定位点存储准备就绪](images/unreal-spatialmapping-arsettings.PNG)

若要查看空间映射网格的调试可视化效果，请启用 ARSessionConfig 中的“在线框中渲染网格数据”复选框，以查看 MRMesh 中每个三角形的白色线框轮廓。 

在“项目设置”>“平台”>“HoloLens”>“空间映射”中，可以修改以下参数以更新空间映射的运行时行为： 

![空间定位点项目设置](images/unreal-spatialmapping-projectsettings.PNG)

“每立方米最大三角形”将更新空间映射网格中三角形的密度。  “空间网格体积大小”表示在玩家周围渲染和更新空间映射数据的立方体的大小。  如果预期的应用程序运行时环境很大，那么这个场可能需要很大才能匹配实际空间。  相反，如果应用程序只需要将全息影像直接放置在用户周围的表面上，那么这个场可能会较小。  当用户在世界内走动时，空间映射卷将随之移动。 

若要在运行时获取对 MRMesh 的访问权限，请首先将 AR 可跟踪通知组件添加到蓝图 Actor： 

![空间定位点 AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

然后，访问组件的详细信息，并单击待监视事件的绿色“+”按钮。 

![空间定位点事件](images/unreal-spatialmapping-events.PNG)

在这种情况下，我们会监视“添加跟踪几何”事件，查找对应于空间映射数据的有效世界网格，并更改网格的材料： 

![空间定位点示例](images/unreal-spatialmapping-example.PNG)

在 C++ 中，我们可以订阅 OnTrackableAdded 委托，以便在 ARTrackedGeometry 可用时立即获取它。  已更新和已删除事件具有类似委托：AddOnTrackableUpdatedDelegate_Handle 和 AddOnTrackableRemovedDelegate_Handle。 

![空间定位点示例 C++ 代码](images/unreal-spatialmapping-examplecode.PNG)

项目的 build.cs 必须在 PublicDependencyModuleNames 列表中具有“AugmentedReality”，以包含“ARBlueprintLibrary.h”和“MRMesh”来检查 UARTrackedGeometry 的 MRMesh 组件。 

空间映射不是通过 ARTrackedGeometries 呈现的唯一数据类型，因此我们首先检查 EARObjectClassification 是否为 World，如果是则表明是空间映射几何。 

## <a name="see-also"></a>另请参阅
* [空间映射](spatial-mapping.md)
