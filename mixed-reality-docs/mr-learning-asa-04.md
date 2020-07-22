---
title: Azure 空间定位点教程 - 4. 显示 Azure 空间定位点反馈
description: 完成本课程可以了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d221a7e64bda7a6dabf76b60c7bff7c6333666ef
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304171"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4.显示来自 Azure 空间定位点的反馈

在本教程中，你将学习如何使用 Azure 空间定位点 (ASA) 向用户提供有关定位点发现、事件和状态的反馈。

## <a name="objectives"></a>目标

* 了解如何设置一个 UI 面板来显示当前 ASA 会话的相关重要信息
* 了解并探索 ASA SDK 提供给用户使用的反馈元素

## <a name="setting-up-asa-feedback-panel"></a>设置 ASA 反馈面板

在“层次结构”窗口中，右键单击“说明” > “TextContent”对象 。 选择“3D 对象” > “Text - TextMeshPro”，创建作为“说明”>“TextContent 对象”的子级的 TextMeshPro 文本对象： 

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> 为了更轻松地在场景中操作，请单击“ParentAnchor”对象左侧的眼睛图标，将此对象的“场景可见性”设置为关闭。<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank"></a> 这会在“场景”窗口中隐藏该对象，但在游戏中不会改变其可见性。

将新创建的文本 (TMP) 对象重命名为 Feedback，然后在检查器窗口中更改其位置和大小，使其整齐放置在说明文本的下方，例如：

* 将矩形变换组件的位置 Y 更改为 -0.24。
* 将矩形变换组件的宽度更改为 0.555。
* 将矩形变换组件的高度更改为 0.1。

然后，选择字体属性，使文本适当地显示在文本区域中，例如：

* 将 TextMeshPro - Text 组件的字体样式更改为粗体。
* 将 TextMeshPro - Text 组件的字体大小更改为 0.17。
* 将 TextMeshPro - Text 组件的对齐方式更改为“居中”。

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

还是在“层次结构”窗口中选择 Feedback 对象，然后在检查器窗口中，使用“添加组件”按钮添加“定位点反馈脚本(脚本)”组件，并按如下所述配置该组件：  

* 将 Feedback 对象本身分配到“定位点反馈脚本(脚本)”组件的“反馈文本”字段  。

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何创建 UI 面板。 它显示 Azure 空间定位点体验的当前状态，为用户提供实时反馈。

[下一教程：5.适用于 Android 和 iOS 的 Azure 空间定位点](mr-learning-asa-05.md)
