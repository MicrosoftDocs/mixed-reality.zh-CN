---
title: 5. 添加按钮并重置棋子位置
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 5 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 77fe2b59db970a2ac4b531d69efec6794478f7d5
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519989"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5.添加按钮并重置棋子位置

本部分将继续演示混合现实工具包 UX Tools 插件的功能，并构建象棋应用的功能。 你将创建一个新函数，并了解如何将对 Actor 的引用从关卡转换到蓝图中。

## <a name="objectives"></a>目标

* 向你的项目添加一个按钮
* 创建一个新的“Reset Location”函数，该函数将一个棋子发送回其原始位置
* 连接按钮，以在按下时触发新创建的函数

## <a name="create-a-function-to-reset-location"></a>创建一个函数以重置位置

1.  打开“WhiteKing”。 在“我的蓝图”面板中，单击“函数”部分旁的“+”按钮以创建新函数。 将此函数命名为“Reset Location”。 

2.  在新创建的“Reset Location”蓝图中，将执行引脚拖放到蓝图网格上的任意位置，以调用“SetActorRelativeTransform”节点。 此函数可设置 Actor 相对于其父级的变形（位置、旋转和缩放）。 我们将使用此函数来重置棋盘上国王的位置，即使棋盘已从其原始位置移动也无妨。 使用位置 X = -26，Y = 4，Z = 0 创建“做出变形”节点，并将其连接到“新的相对变形”输入。 

![Reset Location 函数](images/unreal-uxt/5-function.PNG)

3.  编译并保存“WhiteKing”。 返回到主窗口。 

## <a name="add-a-button"></a>添加按钮

1.  在“蓝图”文件夹中，创建使 SimpleButton 成为子类的新蓝图。 SimpleButton 是一个 3D 按钮蓝图 Actor，作为 UX Tools 插件的一部分提供。 将此按钮命名为“ResetButton”，然后双击以打开蓝图。 

![从 SimpleButton 为新蓝图建立子类](images/unreal-uxt/5-subclass.PNG)

2.  在“组件”面板中，单击“PressableButton(继承)”。 在“详细信息”面板中滚动，直到看到“事件”部分。 单击“按钮按下时”旁的绿色加号按钮 - 这将向事件图表添加“按钮按下时”事件，按下按钮时将调用该事件。 在此，我们需要调用 WhiteKing 的“Reset Location”函数。 为此，首先需要在我们的关卡中获取对 WhiteKing Actor 的引用。 

3.  在“我的蓝图”面板中，找到“变量”部分，然后单击 + 按钮添加新变量。 将此变量命名为“WhiteKing”。 在“详细信息”面板中，选择“变量类型”旁的下拉列表，搜索“WhiteKing”，然后选择“对象引用”。 最后，选中“实例可编辑”旁的复选框。 这将允许从主关卡设置变量。 

![创建变量](images/unreal-uxt/5-var.PNG)

4.  将 WhiteKing 变量从“我的蓝图”>“变量”拖放到“‘重置’按钮事件图表”中。 选择“获取 WhiteKing”。 

5.  拖动“WhiteKing”输出引脚并释放以放置新节点。 选择“Reset Location”函数。 最后，将传出执行引脚从“按钮按下时”拖放到“重置位置”上的传入执行引脚。 编译和保存 ResetButton 蓝图，然后返回到主窗口。 

![从“按下按钮时”调用“Reset Location”函数](images/unreal-uxt/5-callresetloc.PNG)

6.  将“ResetButton”拖到视区中，并将其位置设置为 X = 50，Y =-25，Z = 10。 在“默认值”下，将 WhiteKing 变量的值设置为“WhiteKing”。

![设置变量](images/unreal-uxt/5-buttonlevel.PNG)

现在，你有了一个混合现实应用，其中包含可抓取的棋子和棋盘，以及一个功能齐全的按钮，该按钮将在按下时重置棋子的位置。 可在 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 上找到到目前已完成的应用。 请随意阅读本教程以外的内容并设置这些棋子的其余部分，以便在用户按下按钮时重置整个棋盘。

![在视口中结束场景](images/unreal-uxt/5-endscene.PNG)

[下一节：6.打包并部署到设备或仿真器](unreal-uxt-ch6.md)
