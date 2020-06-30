---
title: 4. 使场景具有交互性
description: 教程系列第 4 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 62c0ff839718f7fda34bdc7560eae634fa37d44f
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720333"
---
# <a name="4-making-your-scene-interactive"></a>4.使场景具有交互性

## <a name="overview"></a>概述

在上一个教程中，你添加了 ARSession、Pawn 和游戏模式，以完成针对象棋应用的混合现实设置。 本部分重点介绍如何使用开放源代码的[混合现实工具包 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) 插件，它提供了使场景具有交互性的工具。 本部分结束时，你将能够使用用户输入来移动棋子。 

## <a name="objectives"></a>目标

* 下载混合现实工具包 UX Tools 插件 
* 将手势交互 Actor 添加到指尖
* 创建操控器并将其添加到场景中的对象
* 使用输入模拟来验证项目

## <a name="downloading-the-mrtk-ux-tools-plugin"></a>下载 MRTK UX Tools 插件
在开始使用用户输入之前，需要将插件添加到项目。

1.  从 [GitHub 存储库](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)克隆或下载最新的 MRTK UX Tools 插件并解压缩文件。

2.  在项目的根文件夹中，创建一个名为“插件”的新文件夹。 将解压缩的 UXTools 插件复制到此文件夹中，然后重新启动 Unreal 编辑器。 

![创建项目插件文件夹](images/unreal-uxt/4-plugins.PNG)

3.  UXTools 插件具有一个包含指针、输入模拟和简单按钮的“内容”文件夹，以及一个由函数分隔的“C++ 类”文件夹  。  

> [!NOTE]
> 如果在“内容浏览器”中看不到“UXTools 内容”部分，请单击“视图选项”>“显示插件内容”  。 

![显示插件内容](images/unreal-uxt/4-showplugincontent.PNG)

安全安装插件后，便可以开始使用它所提供的工具，从手势交互 Actor 开始。

## <a name="spawning-hand-interaction-actors"></a>生成手势交互 Actor
与 UX 元素的手势交互是使用手势交互 Actor 执行的，这些手势交互 Actor 为近距和远距交互创建并驱动指针和视觉对象。
- 近距交互是通过缩放食指和拇指之间的元素或使用指尖戳元素来执行的。 
- 远距交互是通过将虚拟手的光线指向元素并同时按住食指和拇指来执行的。

在我们的示例中，将手势交互 Actor 添加到 MRPawn 可达到以下目的：
- 将光标添加到 Pawn 的食指指尖。
- 提供可通过 Pawn 操纵的精确手势输入事件。
- 通过从虚拟手的手掌延伸出的手部光线允许远距交互输入事件。

为了实现这些概念，建议先仔细阅读有关手势交互的[文档](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.8.x/Docs/HandInteraction.md)，然后再继续。 

准备就绪后，打开“MRPawn”蓝图，然后转到“事件图”。 

1. 将执行引脚从事件 BeginPlay 拖离然后释放，以放置一个新节点。 
    * 选择“从类中生成 Actor”，单击“类”引脚旁边的下拉列表，并搜索“UXT 手势交互 Actor”  。 

2. 将执行引脚从“SpawnActor UXT 手势交互”节点拖离然后释放，并搜索“UXT 手势交互 Actor”类中的“设置手势”函数  。 
    * 将 SpawnActor 节点的“返回值”连接到“设置手势”节点的“目标”引脚   。 这会将“手势交互 Actor”的手势设置为“向左”。 

3. 生成第二个“UXT 手势交互 Actor”，这次会将手势设置为“向右”。 事件开始时，将会在每只手上生成 UXT 手势交互 Actor。 

事件图应与以下屏幕截图匹配：

![生成 UXT 手势交互 Actor](images/unreal-uxt/4-spawnactor.PNG)

两个 UXT 手势交互 Actor 均需要所有者和初始变形位置。 初始变形并不重要，因为手势交互 Actor 可见后即可跳转到虚拟手（此行为包含在 UX Tools 插件中）。 但是，`SpawnActor` 函数需要使用变形输入来避免编译器错误，因此你将使用默认值。 

1. 将该引脚拖离一个“生成变形”引脚，然后释放，即可放置一个新节点。 
    * 搜索“进行变形”节点，然后将“返回值”拖到另一个手势的“生成变形”，以便连接两个 SpawnActor 节点   。 

3.  单击两个 SpawnActor 节点底部的“向下箭头”，以显示“所有者”引脚  。    
    * 将该引脚拖离一个“所有者”引脚，然后放开，即可放置一个新节点。 
    * 搜索“自身”并选择“获取对自身的引用”变量，然后在“自身”对象引用节点和另一个手势交互 Actor 的“所有者”引脚之间创建链接   。 
    * 编译并保存后返回到主窗口。 

确保连接与以下屏幕截图匹配，但可随意拖动节点以使蓝图更具可读性

![完成 UXT 手势交互 Actor 设置](images/unreal-uxt/4-fingerptrs.PNG) 

可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)中找到有关 MRTK UX Tools 插件中提供的手势交互 Actor 的详细信息。

现在，项目中的虚拟手可以选择对象，但仍无法对其进行操纵。 测试应用之前的最后一个任务是将操控器组件添加到场景中的 Actor。

## <a name="attaching-manipulators"></a>附加操控器

操控器是一个响应精确手动输入的组件，可进行抓取、旋转和平移。 将操控器的变形应用到 Actor 变形可允许进行直接 Actor 操纵。 

1. 在“组件”面板中，打开“棋盘”蓝图，单击“添加组件”并搜索“UXT 通用操控器”   。

![添加通用操控器](images/unreal-uxt/4-addmanip.PNG)

2. 展开“详细信息”面板中的“通用操控器”部分 。 可以在其中设置单手操纵或双手操纵、旋转模式和平滑模式。 可以随意选择所需的模式，然后编译和保存棋盘。 

![设置模式](images/unreal-uxt/4-setrotmode.PNG)

3. 对 WhiteKing Actor 重复以上步骤。

可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)中找到有关 MRTK UX Tools 插件中提供的操控器组件的详细信息。

## <a name="testing-the-scene"></a>测试场景
好消息！ 你已准备好使用其新的虚拟手和用户输入来测试应用。 在主窗口中按“开始”，应该会看到 MRTK UX Tools 插件提供的两个网格手，且从每个手掌延伸出手部光线。 可以按如下所示控制手势及其交互：
- 按住“左 Alt”键以控制左手，按住“左 Shift”键以控制右手   。 
- 移动鼠标来移动手，并滚动鼠标滚轮，向前或向后移动手  。 
- 单击鼠标左键进行缩放，单击鼠标中键执行戳操作。 

![视口中的模拟手](images/unreal-uxt/4-handsim.PNG)

请尝试使用模拟手来拿起、移动和放下白棋国王并操纵棋盘！ 试验近距交互和远距交互 - 请注意，当手足够靠近可直接抓住棋盘和国王时，手部光线会消失，取而代之的是食指指尖上的手指光标。 

可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)中找到有关 MRTK UX Tools 插件中提供的模拟手功能的详细信息。

现在，你的虚拟手可以与对象交互，接下来可以继续学习下一个教程，并添加用户界面和事件。

[下一节：5.添加按钮并重置棋子位置](unreal-uxt-ch5.md)
