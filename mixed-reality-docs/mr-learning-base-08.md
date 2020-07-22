---
title: 入门教程 - 8. 使用眼动跟踪
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 9a9fc7f860e6bf9c5cb3370a9c9ff11e627fe73f
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304744"
---
# <a name="8-using-eye-tracking"></a>8.使用眼动跟踪

## <a name="overview"></a>概述

在本教程中，你将了解如何为 HoloLens 2 启用眼动跟踪，以及在用户查看对象时如何将眼动跟踪添加到对象以触发操作。

> [!NOTE]
> 如果你也要将此项目部署到 HoloLens（第一代），请注意，只有 HoloLens 2 支持眼动跟踪。

## <a name="objectives"></a>目标

* 了解如何为 HoleLens 2 启用眼动跟踪
* 了解如何使用眼动跟踪触发操作

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>确保启用了“眼睛凝视输入”功能

在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用眼睛凝视输入功能”是否灰显   ：

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> 当你在本系列教程开头配置 Unity 项目时，[应用 MRTK 项目配置器设置](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings)指令期间应该已经启用了眼睛凝视输入功能。 但如果未启用此功能，请确保立即启用。

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>在凝视提供者中启用基于眼睛的凝视

在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：

* 克隆 DefaultHoloLens2InputSystemProfile 并为其指定合适的名称，例如 GettingStarted_HoloLens2InputSystemProfile
* 展开“指针”部分
* 克隆 DefaultMixedRealityPointerProfile 并为其指定合适的名称，例如 GettingStarted_MixedRealityPointerProfile
* 找到“凝视设置”部分，并选中“是否启用了眼动跟踪”复选框 

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> 有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>为 Unity 编辑器启用模拟的眼动跟踪

在“层次结构”窗口中，选择“MixedRealityToolkit”对象，然后在“检查器”窗口中，导航到“输入”选项卡，然后执行以下操作 ：

* 展开“输入数据提供者” > “输入模拟服务”部分 
* 克隆 DefaultMixedRealityInputSimulationProfile 并为其指定合适的名称，例如 GettingStarted_MixedRealityInputSimulationProfile
* 找到“眼动模拟”部分，然后选中“模拟眼睛位置”复选框 

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>将眼动跟踪添加到对象

在“层次结构”窗口中，展开“RoverExplorer”>“按钮”对象，然后为三个子按钮对象中的每一个对象展开并选择“SeeItSayItLabel”>“TextMeshPro”对象 ：

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

当“检查器”窗口中的三个“TextMeshPro”对象仍处于选中状态时，请使用“添加组件”按钮将以下组件添加到所有选定对象：

* 盒碰撞体组件
* EyeTrackingTarget 组件

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

在“层次结构”窗口中，选择“提示”>“SeeItSayItLabel”>“TextMeshPro”对象，然后按以下方式配置“EyeTrackingTarget”组件  ：

* 在“On Look At Start ()”事件部分
  * 单击小 + 图标以添加另一个事件
  * 将对象本身（即相同的 TextMeshPro 对象）分配给“无(对象)”字段 
  * 在“无函数”下拉列表中选择“TextMeshPro” > “float fontSize”，以便在触发事件时更新此属性  
  * 将参数设置为 0.06，以将 0.04 的当前字号增加 50%
* 在“On Look Away ()”事件部分
  * 单击小 + 图标以添加另一个事件
  * 将对象本身（即相同的 TextMeshPro 对象）分配给“无(对象)”字段 
  * 在“无函数”下拉列表中选择“TextMeshPro” > “float fontSize”，以便在触发事件时更新此属性  
  * 将参数设置为 0.04 以将字号重置为 0.04

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

对“分解”>“SeeItSayItLabel”>“TextMeshPro”对象和“重置”>“SeeItSayItLabel”>“TextMeshPro”对象重复此步骤    。

如果你现在进入游戏模式，然后按住鼠标右键，同时移动鼠标，直到凝视命中的某个标签出现，你将看到字号增加了 50%，而鼠标移走时字号将重置回其原始大小：

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>祝贺

在本教程中，你了解了如何为 HoloLens 2 启用眼动跟踪，以及在用户查看对象时如何将眼动跟踪添加到对象以触发操作。

[下一教程：9.使用语音命令](mr-learning-base-09.md)