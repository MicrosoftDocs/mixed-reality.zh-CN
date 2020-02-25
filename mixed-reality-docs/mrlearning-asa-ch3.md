---
title: Azure 空间锚点教程-3。 显示 Azure 空间锚点反馈
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 3d762950ea8e211fd5a8e4cf8af717674d3fe7e1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553919"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. 显示 Azure 空间锚点反馈

在本教程中，你将了解如何在使用 Azure 空间锚（ASA）时向用户提供有关定位点发现、事件和状态的反馈。

## <a name="objectives"></a>目标

* 了解如何设置显示当前 ASA 会话重要信息的 UI 面板
* 了解并探索 ASA SDK 向用户提供的反馈元素

## <a name="set-up-asa-feedback-ui-panel"></a>设置 ASA 反馈 UI 面板

在 "层次结构" 窗口中，右键单击 > **TextContent** "对象的**说明**，然后选择" **3d 对象** > " **TextMeshPro** " 以将 TextMeshPro 文本对象创建为说明 > TextContent 对象的子项，并为其提供一个合适的名称，例如 "**反馈**"：

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> 若要更轻松地使用场景，请通过单击对象左侧的眼睛图标，将 ParentAnchor 对象的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">场景可见性</a>设置为 "关"。 这将隐藏场景窗口中的对象，而无需更改其游戏中的可见性。

当**反馈**对象仍处于选中状态时，在 "检查器" 窗口中更改其位置和大小，以便将它整齐地放置在说明文本下，例如：

* 将矩形转换位置**Y**改为-0.24
* 将矩形转换**宽度**更改为0.555
* 将矩形转换**高度**更改为0。1

然后选择字体属性，使文本在文本区域内非常合适，例如：

* 将文本网格 Pro （脚本）**字体样式**更改为粗体
* 将文本网格 Pro （脚本）**字号**更改为0.17
* 将文本网格 Pro （脚本）**对齐方式**更改为居中和居中

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

如果仍选中 "**反馈**" 对象，则在 "检查器" 窗口中，使用 "**添加组件**" 按钮将**定位点反馈脚本（脚本）** 组件添加到反馈对象：

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

将**反馈**对象本身分配给**定位点反馈脚本（脚本）** 组件的**反馈文本**字段：

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>祝贺你

在本教程中，已学习如何创建 UI 面板来显示 Azure 空间锚体验的当前状态，以便为用户提供实时反馈。
