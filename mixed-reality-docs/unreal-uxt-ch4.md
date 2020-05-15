---
title: 4. 使场景具有交互性
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 4 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 17f7ab1c1126c47e5ac6388d125d45cf3f2c2d87
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851542"
---
# <a name="3-making-your-scene-interactive"></a>3.使场景具有交互性

本部分介绍开放源代码的混合现实工具包 UX Tools 插件，它提供了一组工具来轻松地使场景具有交互性。 本部分结束时，棋子将能响应用户输入。 

## <a name="objectives"></a>目标

* 在项目中纳入混合现实工具包 UX Tools 插件
* 将手势交互 Actor 添加到指尖
* 创建操控器并将其附加到棋盘和棋子 
* 使用输入模拟来验证项目

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a>下载混合现实工具包 UX Tools 插件

1.  从 [UX Tools GitHub 存储库](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)克隆或下载最新版本的 MRTK UX Tools 插件并将其解压缩

2.  在象棋项目根文件夹中，创建一个名为“插件”的新文件夹。 将解压缩的 UXTools 插件复制到此文件夹。 重新启动 Unreal 编辑器。 

![创建项目插件文件夹](images/unreal-uxt/4-plugins.PNG)

3.  重新启动后，如果在源面板中看不到 UXTools 插件内容，则可能需要单击“查看选项”>“显示插件内容”  。 你会看到 UXTools 插件提供了一个包含指针、输入模拟和一个简单按钮的“内容”文件夹，以及一个具有由函数分隔的子文件夹的“C++ 类”文件夹。  

![显示插件内容](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a>生成手势交互 Actor

1.  首先从 MRPawn 中生成手势交互 Actor，这样一来：1) 我们可以将光标放在 Pawn 的食指指尖来使 MRPawn 可视化，2) 可通过 Pawn 提供可表述的手写输入事件（从而直接操纵 Actor），3) 可通过从我们的手掌延伸出的手部光线提供远交互输入事件。 打开“MRPawn”  蓝图，然后导航到“事件图”  。 

2.  将执行引脚从事件 BeginPlay 拖离然后释放，以放置一个新节点。 选择“从类中生成 Actor”  节点。 单击“类”  引脚旁边的下拉列表，并搜索“Uxt 手势交互 Actor”  。 从“SpawnActor Uxt 手势交互”节点中拖出执行引脚，然后释放，并搜索“Uxt Hand Interaction Actor”类中包含的“Set Hand”  函数。 将 SpawnActor 节点的“返回值”连接到“设置手势”节点的“目标”引脚，以将“手势交互 Actor”的手势设置为“向左”  。 生成第二个“Uxt 手势交互 Actor”  ，这一次是将手势设置为“向右”  ，以便在事件开始时，将在每只手上生成一个 Uxt 手势交互 Actor。 

![生成 UXT 手势交互 Actor](images/unreal-uxt/4-spawnactor.PNG)

3.  接下来，我们需要为 Uxt 手势交互 Actor 提供要在其中生成的初始变形和一个所有者。 将该引脚拖离一个“生成变形”  引脚，然后释放，即可放置一个新节点。 搜索“做出变形”  节点。 初始变形其实并不重要，因为手势交互 Actor 会在可见（已在 UX Tools 插件中为我们编写了代码）时立即跳到我们手中，否则将会消失。 但是，SpawnActor 函数需要将 Transform 作为输入来避免编译器错误，因此，我们将按原样保留“做出变形”的默认值。 将“做出变形”的“返回值”  拖到另一只手的“交互 Actor 生成变形”中。 

4.  单击两个 SpawnActor 节点底部的“向下箭头”  ，以显示“所有者”  引脚。 将该引脚拖离一个“所有者”  引脚，然后放开，即可放置一个新节点。 搜索“self”并选择“获取一个 self 引用”  变量。 在 Self 对象引用节点和另一个手势交互 Actor 的“所有者”引脚之间创建链接。 随意拖动节点以使蓝图更易读。 编译  并保存  后返回到主窗口。 

![完成 UXT 手势交互 Actor 设置](images/unreal-uxt/4-fingerptrs.PNG)

有关 MRTK UX Tools 插件中提供的手势交互 Actor 的详细信息，请参阅官方[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)。

## <a name="attach-manipulators"></a>附加操控器

1.  接下来，我们将操控器连接到我们的棋盘和国王 Actor。 操控器是一个组件，它响应可表述的手写输入，并可进行抓取、旋转和平移。通过将操控器变形应用到 Actor 变形，可直接操纵 Actor。 

2.  打开你的棋盘蓝图。 在“组件”  面板中，单击“添加组件”  并搜索“Uxt 通用操控器”  。 在“详细信息”面板中，你会看到一个标题为“通用操控器”  的部分，可在其中设置是要启用单手操纵还是双手操纵、旋转模式以及平滑模式。 可以随意选择所需的模式，然后编译  和保存  棋盘。 

![添加通用操控器](images/unreal-uxt/4-addmanip.PNG)

![设置模式](images/unreal-uxt/4-setrotmode.PNG)

3.  对 WhiteKing Actor 重复以上步骤。

有关 MRTK UX Tools 插件中提供的操控器组件的详细信息，请访问官方[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)。

## <a name="test-out-your-scene-with-simulated-hands"></a>使用模拟手测试场景

1.  在主窗口中，按“开始”  。 应会看到 MRTK UX Tools 插件提供的两个网格手，且从每个手掌延伸出手部光线！ 

![视口中的模拟手](images/unreal-uxt/4-handsim.PNG)

2.  若要控制“右手”  ，请按住左 Alt  按钮。 移动鼠标来移动手。 滚动鼠标滚轮  ，向前  或**向后**移动手。 单击鼠标左键进行拾取  ，单击鼠标中键执行戳  操作。

3.  若要控制左手  ，请按住左 Shift  按钮。 移动左手的控件与移动右手的控件相同。 

4.  现在，请尝试使用模拟手来拿起、移动和放下白棋国王。 你还可以操纵棋盘！ 试验近交互和远交互 - 请注意，当手足够靠近可直接抓住棋盘和国王时，手部光线会消失，取而代之的是指针尖上的手指光标。 

有关 MRTK UX Tools 插件中提供的模拟手功能的详细信息，请访问官方[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)。

[下一节：5.添加按钮并重置棋子位置](unreal-uxt-ch5.md)