---
title: Azure 空间定位点教程 - 3. 显示 Azure 空间定位点反馈
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 62ce1151837a345dea1bea4a8bea275cc851b9bd
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866897"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3.显示 Azure 空间定位点反馈

本教程介绍如何在使用 Azure 空间定位点 (ASA) 时向用户提供有关定位点发现、事件和状态的反馈。

## <a name="objectives"></a>目标

* 了解如何设置一个 UI 面板用于显示有关当前 ASA 会话的重要信息
* 了解并探索 ASA SDK 提供给用户使用的反馈元素

## <a name="set-up-asa-feedback-ui-panel"></a>设置 ASA 反馈 UI 面板

在“层次结构”窗口中，右键单击“Instructions” > “TextContent”对象并选择“3D 对象” **“文本 - TextMeshPro”，以创建一个 TextMeshPro 文本对象作为“Instructions” > “TextContent”对象的子级，并为创建的对象指定适当的名称，例如 **Feedback**：**   

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> 为了更轻松地在场景中操作，请单击“ParentAnchor”对象左侧的眼睛图标，将此对象的“场景可见性”设置为关闭。<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank"></a> 这会在“场景”窗口中隐藏该对象，但在游戏中不会改变其可见性。

在仍选中了“Feedback”对象的情况下，在“检查器”窗口中更改其位置和大小，使其整齐地定位在说明文本下，例如：

* 将矩形变换的“位置 Y”更改为 -0.24
* 将矩形变换的“宽度”更改为 0.555
* 将矩形变换的“高度”更改为 0.1

然后选择字体属性，使文本合体地显示在文本区域中，例如：

* 将 Text Mesh Pro (Script) 的“字体样式”更改为“粗体”
* 将 Text Mesh Pro (Script) 的“字体大小”更改为 0.17
* 将 Text Mesh Pro (Script) 的“对齐方式”更改为“居中”

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

在仍选中了“Feedback”对象的情况下，在“检查器”窗口中，使用“添加组件”按钮将“定位点反馈脚本(脚本)”组件添加到 Feedback 对象：  

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

将“Feedback”对象本身分配到“定位点反馈脚本(脚本)”组件的“反馈文本”字段：  

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>祝贺

在本教程中，你已了解如何创建一个 UI 面板用于显示 Azure 空间定位点体验的当前状态，以便为用户提供实时反馈。

[下一课：4.适用于 Android 和 iOS 的 Azure 空间定位点](mrlearning-asa-ch4.md)
