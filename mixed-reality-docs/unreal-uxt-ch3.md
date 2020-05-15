---
title: 3. 设置混合现实项目
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 3 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840616"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3.设置混合现实项目

本部分将指导你完成为混合现实开发配置应用的过程。 

## <a name="objectives"></a>目标

* 了解如何使用 ARSessionConfig、Pawn 和 GameMode 设置混合现实项目

## <a name="configure-the-session"></a>配置会话

1. 在“内容浏览器”中，导航回“内容”  文件夹。 单击“新增”>“杂项”>“数据资产”  。 

2. 选择“ARSessionConfig”  作为类，然后单击“选择”  。 将资产命名为“ARSessionConfig”。

![创建数据资产](images/unreal-uxt/3-createasset.PNG)

3. 双击“ARSessionConfig”将其打开。 ARSessionConfig 数据资产包含许多有用的 AR 设置，包括空间映射和封闭。 有关 ARSessionConfig 的更多详细信息，请查看有关 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html)的 Unreal Engine 文档。 对于象棋应用，不需要修改任何设置，只需点击“保存”  并返回到主窗口。 

![AR 会话配置](images/unreal-uxt/3-arsessionconfig.PNG)

4. 在视区上方的工具栏上，单击“蓝图”>“打开关卡蓝图”  。 关卡蓝图是一种特殊蓝图，用作关卡范围的全局事件图。 我们将在此处启动 AR 会话，以便在关卡开头应用 AR 会话配置。  

5. 将执行节点拖离 Event BeginPlay  并释放。 搜索“启动 AR 会话”  节点。 单击“会话配置”  ，然后选择新创建的“ARSessionConfig”  资产。 点击“编译”  ，然后“保存”  。 返回到主窗口。

![启动 AR 会话](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a>创建 Pawn

1.  在“内容”文件夹中，创建一个继承自 DefaultPawn  的新蓝图。 在 Unreal 中，Pawn 表示游戏中的用户，在本例中为 HoloLens 2 体验。 将新 Pawn 重命名为“MRPawn”，并双击“MRPawn”将其打开。 

![创建从 DefaultPawn 继承的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

2.  默认情况下，Pawn 包含网格组件和碰撞组件，因为在大多数 Unreal 项目中，用户控制的 Pawn 是与其他组件碰撞的实体对象。 在这种情况下，由于用户是 Pawn，我们希望能够穿过全息影像，而不会产生碰撞。 在“组件”面板中，选择“CollisionComponent”  。 在“详细信息”面板中，向下滚动到“碰撞”部分，并单击“碰撞预设”旁的下拉菜单。 将此值从“Pawn”更改为“NoCollision”  。 对“MeshComponent”  执行相同操作。 编译  ，然后保存  蓝图。 返回到主窗口。 

![调整 Pawn 的碰撞预设](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a>创建游戏模式

1.  在内容浏览器的“内容”文件夹中，创建一个新的蓝图，其中包含父“游戏模式库”  。 将其命名为“MRGameMode”并双击以打开。 在 Unreal 中，游戏模式决定着游戏或体验的诸多设置，其中包括要使用的默认 Pawn。 

![内容浏览器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  在“详细信息”窗格中，查找“类”部分。 将默认 Pawn 类从“DefaultPawn”更改为刚创建的“MRPawn”  。 点击“编译”  ，然后“保存”  。 返回到主窗口。 

![设置默认 Pawn 类](images/unreal-uxt/3-setpawn.PNG)

3.  设置项目的最后一步是告诉 Unreal 默认为“MRGameMode”。 转到“编辑”>“项目设置”>“映射和模式”  （在“项目”中）部分。 在“默认模式”部分，单击下拉列表，然后选择“MRGameMode”  。 在下面的“默认映射”部分，将“EditorStartupMap”  和“GameDefaultMap”  都更改为“Main”  。 这样，当你关闭并重新打开编辑器时，将默认选择主地图。 同样，当你玩游戏时，主地图为开始关卡。 

![项目设置 - 映射和模式](images/unreal-uxt/3-mapsandmodes.PNG)

[下一节：4.使场景具有交互性](unreal-uxt-ch4.md)