---
title: Unreal 中的空间映射
description: Unreal 中空间映射使用指南
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间映射
ms.openlocfilehash: ffa57749cd96e240ac4812f950f4e13a6dbc68bd
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720403"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal 中的空间映射

## <a name="overview"></a>概述
使用空间映射可以通过向全球展示 HoloLens 来将对象放置在现实生活中的表面上，这使全息影像看起来更真实。 空间映射还可以利用真实的深度提示，在用户世界定位对象。这有助于说服用户这些全息影像实际位于其空间中；在空间中浮动或随用户移动的全息影像并不真实。 你希望尽可能轻松地放置各个项。

可以在[空间映射](spatial-mapping.md)文档中找到有关空间映射质量、位置、封闭、呈现等内容的详细信息。

## <a name="enabling-spatial-mapping"></a>启用空间映射

若要在 HoloLens 上启用空间映射，请执行以下操作：
- 打开“编辑”>“项目设置”，并向下滚动到“平台”部分。    
    + 选择“HoloLens”并检查“空间感知”。

若要选择在 HoloLens 游戏中使用空间映射并调试“MRMesh”，请执行以下操作：
1. 打开“ARSessionConfig”并展开“ARSettings”>“世界映射”部分。 

2. 选中“从跟踪几何生成网格数据”，可指示 HoloLens 插件开始异步获取空间映射数据，并通过 MRMesh 将其呈现给 Unreal。 
3. 选中“在线框中呈现网格数据”，以显示 MRMesh 中每个三角形的白色线框轮廓。 

![空间定位点存储准备就绪](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>运行时的空间映射
可以修改以下参数以更新空间映射运行时行为：

- 打开“编辑”>“项目设置”，向下滚动到“平台”部分，并选择“HoloLens”>“空间映射”  ： 

![空间定位点项目设置](images/unreal-spatialmapping-projectsettings.PNG)

- “每立方米最大三角形”将更新空间映射网格中三角形的密度。  
- “空间网格体积大小”是在玩家周围渲染和更新空间映射数据的立方体的大小。  
    + 如果预期的应用程序运行时环境很大，那么这个值可能需要很大才能匹配实际空间。  另一方面，如果应用程序只需要将全息影像直接放置在用户周围的表面上，那么这个值可能会较小。 当用户在世界内走动时，空间映射卷将随之移动。 

## <a name="working-with-mrmesh"></a>使用 MRMesh
若要在运行时访问 MRMesh，请执行以下操作：
1. 将“ARTrackableNotify”组件添加到蓝图 Actor。 

![空间定位点 AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. 选择“ARTrackableNotify”组件，然后在“详细信息”面板中展开“事件”部分  。 
    - 在要监视的事件上，单击 + 按钮。 

![空间定位点事件](images/unreal-spatialmapping-events.PNG)

在这种情况下，会监视“添加时跟踪几何”事件，这将查找与空间映射数据匹配的有效世界网格。 可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 组件 API 中找到事件的完整列表。 

可以在蓝图事件图或 C++ 中更改网格的材料。 下面的屏幕截图显示蓝图路由： 

![空间定位点示例](images/unreal-spatialmapping-example.PNG)

在 C++ 中，可以订阅 `OnTrackableAdded` 委托，以便在 `ARTrackedGeometry` 可用时立即获取它，如以下代码所示。 

> [!IMPORTANT]
> 项目的 build.cs 文件必须具有 PublicDependencyModuleNames 列表中的 AugmentedReality  。
> - 其中包括 ARBlueprintLibrary.h 和 MRMeshComponent.h，这使你可以检查 UARTrackedGeometry 的 MRMesh组件   。 

![空间定位点示例 C++ 代码](images/unreal-spatialmapping-examplecode.PNG)

空间映射不是通过 ARTrackedGeometries 呈现的唯一数据类型。 可以检查 `EARObjectClassification` 是否为 `World`，这意味着这是空间映射几何。 

已更新和已删除事件具有类似委托： 
- `AddOnTrackableUpdatedDelegate_Handle` 
- `AddOnTrackableRemovedDelegate_Handle`”。 

可以在 [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API 中找到事件的完整列表。

## <a name="see-also"></a>另请参阅
* [空间映射](spatial-mapping.md)
