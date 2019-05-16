---
title: MR 学习基本模块-农历模块程序集示例体验
description: 在本课中，我们将合并多个前面的课程创建唯一示例体验从中学到的概念。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity 中，教程，hololens 混合的现实
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730848"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>MR 学习基本模块-农历模块程序集示例体验

在本课中，我们将合并多个前面的课程创建唯一示例体验从中学到的概念。 我们将创建农历模块程序集应用程序，用户将需要使用跟踪的手选取农历模块的组成部分，并尝试组合农历模块。 我们将使用 pressable 按钮来切换放置提示，要重置我们的经验，并启动我们农历模块到空间 ！ 在将来的教程中，我们将继续基于此体验，包括功能强大多用户的用例，利用 Azure 空间的定位点来实现空间对齐方式。

## <a name="objectives"></a>目标

- 合并多个概念从前面的课程，以创建独特的体验
- 了解如何切换对象
- 触发器复杂的事件，使用 pressable 按钮
- 使用 rigidbody 物理和强制
- 了解如何使用工具提示

## <a name="instructions"></a>说明

### <a name="configuring-the-lunar-module"></a>农历模块的配置

在本章中，我们将创建我们的示例体验所需的各种组件介绍。

1. 向基本场景中添加农历模块程序集预设。 为此，请在你项目的选项卡中，搜索"火箭 Launcher_Tutorial。" 也可以在资产中找到预设可 > BaseModuleAssets > 预设。 你可能会看到两个火箭启动器预设;一个具有名称"教程"，另一个具有名称"完成。 将"火箭 Launcher_Tutorial"预设可拖动到您的基本场景。 随意放置在您的场景预设的位置。
   注意："火箭 Launcher_Complete"预设是已完成的启动器，供参考。 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

如果你在层次结构中展开"火箭 Launcher_Tutorial"游戏对象，并进一步展开"农历模块"对象，你将看到多个对象的子对象的材料，名为"x 射线。" "X 射线"材料允许我们将使用用户为放置提示略有半透明颜色。 

![Lesson6 第 1 章 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)有五个部分农历模块的用户要进行交互，如下图中所示：

1.  漫游存储模块
2.  油箱
3.  能源单元格
4.  在停靠门户 
5.  外部传感器

![Lesson6 第 1 章 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 注意：您看到基本场景层次结构中的游戏对象名称不对应于场景中对象的名称。

步骤 2：将音频源添加到农历模块。 请确保基场景层次结构中选择该农历模块，然后单击"添加组件"。 搜索"音频源"，并将其添加到该对象。 将其留空现在。 我们将使用此播放启动声音更高版本。
 ![Lesson6 第 1 章 Step2im](images/Lesson6_Chapter1_step2im.PNG)步骤 3:添加脚本"切换放置提示"。 单击"添加组件"并搜索"放置提示切换"。 这是一个自定义脚本，您可以打开和关闭之前提到的半透明提示 （使用 x 射线材料的对象）。 
![Lesson6 第 1 章 Step3im](images/Lesson6_Chapter1_step3im.PNG)步骤 4:由于我们有 5 个对象，键入"5"的游戏对象数组大小。 然后应会看到显示的 5 个新元素。 

![Lesson6 第 1 章 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

将每个半透明对象拖入框指出"None （游戏对象）。 从基本场景中的农历模块拖动以下对象： 

• 背包

• GasTank

• Topleftbody

• 鼻子

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

现在已配置的"切换放置提示"的脚本。 这将使我们能够打开和关闭的提示。

步骤 5：添加的"启动农历模块"的脚本。 单击"添加组件"按钮、"启动农历模块"中搜索并选择它。 此脚本将负责启动农历模块。 当我们按配置的按钮时，它会将向上强制添加到农历模块刚体组件，并将导致模块以向上启动。 如果你是室内，农历模块可能会崩溃针对 ceiling 网格。 但如果你是室外，它会飞入到空间无限期。 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

步骤 6：调整一些咄咄逼人以便农历模块会一头向上正常。 请尝试的值为 0.01。 将"Rb"字段留空。 Rb 代表刚体，，将在运行时期间自动填充此字段。

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>农历模块部件概述
农历模块部分父对象是用户交互的对象的集合。 下面的列表中提供的游戏对象名称 （使用场景标记为 paretheses 中的名称）：

- 背包 （油箱）
- GasTank （能源单元格）
- TopLeftBody （Rover 机箱）
- 鼻子 （停靠门户）
- LeftTwirler （外部传感器）

请注意每个对象具有操作处理程序，第 4 课中所述。 与操作处理程序，用户就能够获取和处理对象。 另请注意，"两个提交的操作类型"设置为"移动和旋转。" 这仅允许用户将对象移动并更改其大小，这是程序集应用程序所需的功能。
此外，远端操作没有被选中以仅允许直接交互的模块的组成部分。

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

部分程序集演示脚本 （如上所示） 是管理用户将其放到农历模块的对象脚本。 

"对象到另一个位置"字段是图像的为所选 (n 上面，背包/油箱的大小写) 与它能够连接到的对象的转换。 

"近距离"和"远距离"设置负责确定的邻近到的部分将对齐到位，或被释放。 例如，背包/油箱需要为 0.1 单位距离农历模块来对齐到位。 "远距离"设置对象需要为要分离的农历模块中的位置。 在这种情况下，用户的手必须获取背包/油箱并将其拉出 0.2 单位距离农历模块，将其从重新对齐到位删除。

"工具提示对象"是在场景中的工具提示标签。 当对象会对齐到位时，标签将被禁用。 

将自动获取音频源。 

### <a name="placement-hints-buttons"></a>放置提示按钮
在中[第 2 课](mrlearning-base-ch2.md)，您学习了如何发出及配置按钮来执行诸如更改项的颜色，或将其推送时播放声音。 我们将继续使用这些原则，我们配置用于放置提示切换按钮。 

目标是配置我们的按钮，以便每次用户按位置提示按钮，它将切换半透明放置提示的可见性。 

第 1 步：放置提示对象基本场景层次结构中处于选定状态时，将农历模块移动到检查器面板中的空"仅限运行时"槽。 
 ![Lesson6 第 3 章 Step1im](images/Lesson6_Chapter3_step1im.PNG)步骤 2:现在，单击下拉列表中的状态显示，""没有函数。 转到"TogglePlacementHints，"，该菜单下选择"ToggleGameObjects （）。" 打开和关闭以便每次按下按钮时进行显示或隐藏 ToggleGameObjects() 会切换位置提示。
 ![Lesson6 第 3 章 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>配置重置按钮

将让用户进行了错误的操作或对象，或只是想要体验的 rest 的意外引发的情况。 重置按钮将添加重新启动体验的功能。 

第 1 步：选择重置按钮。 在基本的场景中，它是名为"ResetRoundButton。" 

步骤 2：将农历模块从基本场景的层次结构拖到"按钮按下"下的空槽检查器面板。
 ![Lesson6 第 4 章 Step2im](images/Lesson6_Chapter4_step2im.PNG)

步骤 3:选择下拉列表菜单，指出:"函数"，然后悬停在"LaunchLunarModule。" 现在，选择"resetModule （）。"

![Lesson6 第 4 章 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 注意：你会注意到，默认情况下"GameObject.BroadcastMessage"配置为"ResetPlacement。" 这将广播消息为 RocketLauncher_Tutorial 每个子对象调用"ResetPlacement"。 对于"ResetPlacement()"有一个方法的任何对象将通过重置其位置来响应该消息。 

### <a name="launching-the-lunar-module"></a>启动农历模块
本章我们将配置的启动按钮。 这将允许用户按下按钮，并启动到空间农历模块。

第 1 步：选择启动按钮 （基本场景中它名为"LaunchRoundButton"）。 检查器面板中，将农历模块拖到"触摸结束"下的空槽。
 ![Lesson6 第 5 章 Step1im](images/Lesson6_Chapter5_step1im.PNG)步骤 2:选择下拉列表菜单，指出:"没有函数"。 将鼠标悬停"LaunchLunarModule"，然后选择"StopThruster （）。" 这将控制用户想要向农历模块多少主旨的是。 
 ![Lesson6 第 5 章 Step2im](images/Lesson6_Chapter5_step2im.PNG)步骤 3:在"ButtonPressed()"（单击、 保持状态，并拖动） 将农历模块添加到空槽。 

步骤 4：单击下拉列表菜单，显示"函数"，将鼠标悬停"LaunchLunarModule"并选择"StartThruster （）。" 
 ![Lesson6 第 5 章 Step4im](images/Lesson6_Chapter5_step4im.PNG)步骤 5:将音乐添加到农历模块，以便火箭时，将播放音乐。 若要执行此操作，将农历模块拖放到下一步"按钮 Pressed()"下的空槽。

步骤 6：选择下拉列表菜单，显示"函数"，将鼠标悬停"AudioSource"并选择"PlayOneShot (AudioClip)。" 随意浏览各种 MRTK 中包含的声音。 对于此示例中，我们将继续使用"MRTK_Gem。"
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>恭喜 ！ 
你已完整地配置此应用程序 ！ 现在时按播放，可以完全组装农历模块、 切换提示、 启动农历模块，并重置其再次执行该世界各地。
