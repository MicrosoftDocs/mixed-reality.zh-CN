---
title: 3. 设置混合现实项目
description: 教程系列第 3 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 105e817e54f7de12afdcab9fde1dfce0c38ff4a7
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376379"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3.设置混合现实项目

## <a name="overview"></a>概述

在上一个教程中设置了象棋应用项目。 本部分将逐步介绍如何设置此应用，来进行混合现实开发，这意味着要添加 AR 会话。 此任务将使用 ARSessionConfig 数据资产，其中包含大量有用的 AR 设置，如空间映射和遮挡。 若要深入了解，请参阅 Unreal 引擎文档，其中包含有关 [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 资产和 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 类的详细信息。

## <a name="objectives"></a>目标
* 使用 Unreal Engine 的 AR 设置 
* 使用 ARSessionConfig 数据资产
* 设置 Pawn 和游戏模式

## <a name="adding-the-session-asset"></a>添加会话资产
Unreal 中的 AR 会话无法自行发生。 要使用会话，需要借助 ARSessionConfig 数据资产，这就是接下来的任务：

1. 单击“内容浏览器”中的“添加新项 > 杂项 > 数据资产”。  请确保自己处于根 Content 文件夹级别。 
    * 选择“ARSessionConfig”，单击“选择”，然后将资产命名为“ARSessionConfig”。  

![创建数据资产](images/unreal-uxt/3-createasset.PNG)

3. 双击“ARSessionConfig”将其打开，保留所有默认设置，点击“保存”。  返回到主窗口。 

![AR 会话配置](images/unreal-uxt/3-arsessionconfig.PNG)

完成此操作后，下一步是确保在关卡加载时 AR 会话会启动，而在关卡结束时 AR 会话会停止。 幸运的是，Unreal 具有一种叫做“关卡蓝图”的特殊蓝图，它用作关卡范围的全局事件图。 在关卡蓝图中连接 ARSessionConfig 资产，可确保游戏开始时 AR 会话将立即触发。

1. 从编辑器工具栏中单击“蓝图 > 打开关卡蓝图”： 

![打开关卡蓝图](images/unreal-uxt/3-level-blueprint.PNG)

5. 将执行节点（左指箭头图标）拖离 Event BeginPlay 并释放。 搜索“启动 AR 会话”节点，然后按 Enter 键。  
    * 单击“会话配置”下的“选择资产”下拉列表，然后选择“ARSessionConfig”资产。   

![启动 AR 会话](images/unreal-uxt/3-start-ar-session.PNG)

6. 右键单击 EventGraph 中的任意位置，然后创建一个新的 Event EndPlay 节点。 拖动执行 pin 并释放。 搜索“停止 AR 会话”节点，然后按 Enter 键。 如果在关卡结束时 AR 会话未停止，那么在流式传输到头戴显示设备时，如果你重启应用，某些功能可能会停止工作。 
    * 点击“编译”和保存”，然后返回到主窗口。

![停止 AR 会话](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>创建 Pawn
此时，项目仍需要一个玩家对象。 在 Unreal 中，Pawn 表示游戏中的用户，但在本例中它将代表 HoloLens 2 体验。

1. 在 Content 文件夹中单击“添加新项 > 蓝图类”，展开底部的“所有类”部分。   
    * 搜索“DefaultPawn”，单击“选择”，将其命名为“MRPawn”，然后双击资产打开它  。 

![创建从 DefaultPawn 继承的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> 默认情况下，Pawn 具有网格和碰撞组件。 在大多数 Unreal 项目中，Pawn 都是可与其他组件碰撞的固体。 在混合现实中 Pawn 与用户相同，因此需要能够在不发生碰撞的情况下传递全息影像。 

2. 从“组件”面板中选择“CollisionComponent”，向下滚动到“详细信息”面板的“碰撞”部分。    
    * 单击“碰撞预设”下拉列表，将值更改为“NoCollision”。  
    * 对“MeshComponent”执行同样的操作

![调整 Pawn 的碰撞预设](images/unreal-uxt/3-nocollision.PNG)

3. 从“组件”面板中单击“添加组件”>“相机”，然后将其命名为“相机”  。 这样，玩家相机就能随 HoloLens 2 设备一起移动。

4. 编译并保存蓝图 。

从此处完成操作后，返回到主窗口。

## <a name="create-a-game-mode"></a>创建游戏模式
混合现实设置的最后一个部分是游戏模式。 游戏模式决定着游戏或体验的诸多设置，其中包括要使用的默认 Pawn。

1.  在 Content 文件夹中单击“添加新项 > 蓝图类”，展开底部的“所有类”部分。   
    * 搜索“游戏模式基”，将其命名为“MRGameMode”并双击以打开。  

![内容浏览器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  转到“详细信息”面板中的“类”部分，将“默认 Pawn 类”更改为“MRPawn”。   。 
    * 点击“编译”和保存”，然后返回到主窗口。 

![设置默认 Pawn 类](images/unreal-uxt/3-setpawn.PNG)

3.  选择“编辑 > 项目设置”，然后从左侧列表单击“地图和模式”。  
    * 展开“默认模式”，将“默认游戏模式”更改为“MRGameMode”。   
    * 展开“默认地图”，将“EditorStartupMap”和“GameDefaultMap”都设置为“主”。    这样，当你关闭并重新打开编辑器或玩游戏时，将默认选择主地图。

![项目设置 - 映射和模式](images/unreal-uxt/3-mapsandmodes.PNG)

针对混合现实全面设置此项目后，你可以继续学习下一个教程，开始将用户输入添加到场景中。 

[下一节：4.使场景具有交互性](unreal-uxt-ch4.md)