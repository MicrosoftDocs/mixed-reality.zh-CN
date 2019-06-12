---
title: MR 学习基础模块 - 登月舱组装示例体验
description: 在本节课中，我们将结合在以前课程中所学的多个概念来创建一个独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730848"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a>MR 学习基础模块 - 登月舱组装示例体验

在本节课中，我们将结合在以前课程中所学的多个概念来创建一个独特的示例体验。 我们将创建一个登月舱组装应用程序，用户需要借助该程序使用被追踪的双手拾起登月舱部件并尝试组装一个登月舱。 我们将使用可按下的按钮切换放置提示，重置我们的体验，并将我们的登月舱发射到太空！ 在以后的教程中，我们将继续以此体验为基础，包括利用 Azure 空间定位点进行空间对齐的强大的多用户用例。

## <a name="objectives"></a>目标

- 结合以前课程中的多个概念来创建一个独特的体验
- 了解如何切换对象
- 使用可按按钮触发复杂事件
- 使用刚体的物理特性和力量
- 探索如何使用工具提示

## <a name="instructions"></a>说明

### <a name="configuring-the-lunar-module"></a>配置登月舱

在本章中，我们将了解创建示例体验所需的各种组件。

1. 将登月舱的预置组件添加到基本场景。 为此，请在项目选项卡中搜索“Rocket Launcher_Tutorial”。 还可以在 Assets>BaseModuleAssets>Prefabs 中找到预制件。 可能会看到两个火箭发射器预制件；一个名为“tutorial”，另一个名为“complete”。 将“Rocket Launcher_Tutorial”预制件拖动至基本场景。 请随意在场景中设置预制块的位置。
   注意：“Rocket Launcher_Complete”预制件是完成的发射器，仅供参考。 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

如果在层次结构中展开“Rocket Launcher_Tutorial”游戏对象，并进一步展开“登月舱”对象，将看到几个子对象，其中包含一个名为“X 射线”的材料。 通过“X 射线”材料，可获取略微半透明的颜色，我们将其用作用户的放置提示。 

![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 登月舱由五个部件组成，用户将与之交互，如下图所示：

1.  探测器外壳
2.  油箱
3.  电池
4.  插接门户 
5.  外部传感器

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> 注意：在基本场景层次结构中看到的游戏对象名称与场景中对象的名称不对应。

步骤 2：为登月舱添加一个音频源。 请确保在你的基本场景层次结构中选中登月舱，然后点击“添加组件”。 搜索"音频源"，并将其添加到对象中。 暂时将其留空。 我们稍后会用它来播放发射声。
 ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 步骤 3：添加脚本“切换放置提示。” 单击“添加组件”并搜索“切换放置提示。” 这是一个自定义脚本，通过该脚本可打开和关闭前面提到的半透明提示（使用 X 射线材料的对象）。 
![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 步骤 4：因为我们有 5 个对象，输入“5”作为游戏对象数组的大小。 然后应会看到显示 5 个新元素。 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

将每个半透明的对象拖到“无（游戏对象）”框中。 从基地场景的登月舱中拖动以下对象： 

•   Backpack

•   GasTank

•   Topleftbody

•   Nose

•   LeftTwirler

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

现已配置“切换放置提示”脚本。 这将允许我们打开和关闭提示。

步骤 5：添加“发射登月舱”脚本。 点击“添加组件”按钮，搜索“发射登月舱”并将其选中。 此脚本将负责发射登月舱。 当我们按下配置的按钮时，它会给登月舱的刚体组件增加一个向上的力，并使登月舱向上发射。 如果你在室内，登月舱可能会撞到你的天花板网。 但如果你在户外，它会无限向上飞入太空。 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

步骤 6：调整推力，使登月舱将顺利地往上飞。 尝试使用值 0.01。 将“Rb”字段留空。 Rb 代表刚体，该字段将在运行时自动填充。

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a>登月舱部件概述
登月舱部件父对象是用户将与之交互的对象的集合。 游戏对象名称（场景名称在括号中标注）如以下列表所示：

- Backpack（油箱）
- GasTank（电池）
- TopLeftBody（探测器外壳）
- Nose（插接门户）
- LeftTwirler（外部传感器）

注意，每个对象都有操作处理程序，如第 4 课所述。 使用操作处理程序，用户可以抓取和操作对象。 另请注意，“双手操纵型”设置为“移动和旋转”。 这只允许用户移动对象而不改变其大小，这是组装应用程序所需的功能。
此外，未选中远程操作，以仅允许直接交互登月舱部件。

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

部件组装演示脚本（如上所示）用于管理用户要在登月舱上放置的对象。 

“要放置的对象”字段是所选择的转换（如上图所示，为 backpack/油箱）和它可以连接到的对象。 

“近距离”和“远距离”设置负责确定某些部件贴靠或释放时的接近度。 例如，backpack/油箱需要离登月舱 0.1 个单位才能贴靠到位。 “远距离”设置了对象从登月舱拆离所需的位置。 在本例中，用户必须用手抓住 backpack/油箱，将它从登月舱拉出 0.2 个单位才能防止它贴靠回原位。

“工具提示对象”是场景中的工具提示标签。 当对象贴靠到位时，标签将被禁用。 

将自动获取音频源。 

### <a name="placement-hints-buttons"></a>放置提示按钮
在[第 2 课](mrlearning-base-ch2.md)中，了解了如何放置和配置按钮，以执行诸如在按下按钮时，更改物品颜色或使其播放声音等操作。 在为切换放置提示配置按钮时，我们将继续使用这些原则。 

我们的目标是配置我们的按钮，这样每当用户按下放置提示按钮时，它就会切换半透明的放置提示的可见性。 

第 1 步：将登月舱移动到检查器面板中“仅运行时”的空槽，同时在基本场景层次结构中选择放置提示对象。 
 ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 步骤 2：现在单击带有“无函数”字样的下拉列表。 转到“TogglePlacementHints”，在菜单下选择“ToggleGameObjects()”。 ToggleGameObjects() 将打开和关闭放置提示，以便每次按下按钮时它们都会显示或隐藏。
 ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a>配置重置按钮

在某些情况下，用户可能会犯错误，或者不小心扔掉了对象，或只是想中止体验。 重置按钮将添加重新启动体验的功能。 

第 1 步：选择重置按钮。 在基本场景中，它被命名为“ResetRoundButton”。 

步骤 2：将登月舱从基本场景层次结构中拖拽到“按下按钮的”检查器面板下的空槽中。
 ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

步骤 3:选择带有“无函数”字样的下拉菜单，并将鼠标悬停在“LaunchLunarModule”上。 现在选择“resetModule ()”。

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> 注意：你会注意到默认情况下“GameObject.BroadcastMessage”被配置为“ResetPlacement”。 这将为 RocketLauncher_Tutorial 的每个子对象广播一条名为“ResetPlacement”的消息。 任何具有“ResetPlacement()”方法的对象都将通过重置位置来响应该消息。 

### <a name="launching-the-lunar-module"></a>发射登月舱
本章我们将配置发射按钮。 这样，用户可以按下按钮，将登月舱发射到太空。

第 1 步：选择发射按钮（在基本场景中名为“LaunchRoundButton”）。 将登月舱拖到检查面板“触摸端”下的空槽。
 ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 步骤 2：选择带有“无函数”字样的下拉菜单。 将鼠标悬停在“LaunchLunarModule”上并选择“StopThruster()”。 这将控制用户想给登月舱多少推力。 
 ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 步骤 3：在“ButtonPressed()”下，将登月舱（单击、按住并拖动）添加到空槽。 

步骤 4：单击带有“无函数”字样的下拉菜单，并将鼠标悬停在“LaunchLunarModule”上并选择“StartThruster ()”。 
 ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 步骤 5：将音乐添加到登月舱，这样当火箭起飞时，音乐就会播放。 为此，请将登月舱拖到“Button Pressed()”下的下一个空槽。

步骤 6：选择带有“无函数”字样的下拉菜单，将鼠标悬停在“AudioSource”上，然后选择“PlayOneShot (AudioClip)”。 随意浏览各种 MRTK 中附带的声音。 对于本例，我们将一直使用“MRTK_Gem”。
 ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)


### <a name="congratulations"></a>祝贺你 
你已经完全配置了这个应用程序！ 现在，当按下播放时，就可以完全组装登月舱、切换提示、发射登月舱，并重置它以重新执行此操作。
