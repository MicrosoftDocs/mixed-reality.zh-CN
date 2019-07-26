---
title: MR 学习基础模块 - 动态内容放置和求解器
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 401c667ef80042da9182b7f4e065dfd6884cf061
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485689"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4.放置动态内容并使用 solvers

当全息影像直观地跟随用户并且在物理环境中无缝巧妙地参与互动时，它们在 HoloLens 2 中变得真实生动。 在本教程中, 我们将探讨如何使用 MRTK 的可用放置工具 (称为 solvers) 动态放置全息影像, 以解决复杂的空间放置方案。 在 MRTK 中, solvers 是一种脚本和行为的系统, 用于允许 UI 元素跟随你、用户或场景中的其他游戏对象。 它们还可用于快速贴靠到某个位置，使应用程序更加直观。 

## <a name="objectives"></a>目标

* 介绍 MRTK 的求解器
* 使用求解器让一组按钮跟随用户
* 使用求解器使游戏对象跟随用户被追踪的双手

## <a name="instructions"></a>说明

### <a name="location-of-solvers-in-the-mrtk"></a>求解器在 MRTK 中的位置
 要查找项目中的可用求解器，请查看 MRTK SDK 文件夹（MixedRealityToolkit.SDK 文件夹），然后在 utilities 文件夹下，将看到求解器文件夹，如下图所示。

![求解器](images/lesson3_chapter1_step1im.PNG)

>注意:在本课程中, 我们将只介绍 Orbital 求解器和 RadialView 求解器的实现。 要详细了解 MRTK 中的所有求解器，请访问： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>使用求解器跟随用户
本章的目标是增强之前创建的按钮集合, 使其遵循用户的注视方向。 在以前版本的 MRTK 和 HoloToolkit 中, 这称为 tagalong 功能。

1. 从上一节课中选择按钮集合父对象。

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. 在检查器面板中, 单击 "添加组件" 按钮, 然后搜索 "orbital"。 这时应显示环绕组件。 选中它，将环绕组件添加到按钮集合游戏对象。

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>注意:添加该组件时，将注意到系统在检查器选项卡中添加了环绕脚本和求解器处理程序脚本，这是必需的组件。 

3. 若要将按钮集合配置为关注用户, 我们需要实现以下调整 (请参阅下图):
- 在 Orbital 脚本中, 将 "方向类型" 下拉列表设置为 "仅偏航"。 这样，在对象跟随用户时，它只有一个轴在旋转。
- 将所有轴上的局部偏移量设置为 0。 将世界偏移量设置为 x = 0，y = -0.1，z = 0.6。 这样可以锁定对象的移动，当用户改变高度时，对象在物理环境中保持固定高度，同时仍然可以在用户在环境中移动时跟随用户。 可以调整这些值以实现广泛的行为。
- 对于这种情况, 在用户完全关闭用户的 head 后, 只关注用户的视图, 你可以选择 "对全球偏移使用角度单" 复选框 (注意:此标题可能会在某些屏幕上被截断，如下图所示。）例如，要使对象仅在每隔 90 度时跟随用户一次，请将步进数设置为 4（左侧示例中的绿色箭头标记）。 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>使对象跟随跟踪的手

在本节中，我们将使用 RadialView 求解器配置先前创建的立方体游戏对象，以跟随用户被追踪的双手。

1. 在 BaseScene 层次结构中选择立方体对象。 单击 "检查器" 面板中的 "添加组件"。 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. 在 "搜索" 框中键入 RadialView, 然后选择 "RadialView" 组件以将其添加到多维数据集中。 求解器处理程序组件也将自动添加到立方体。

3. 将径向视图更改为不跟随头部，而是跟随左手。 选择要引用的所跟踪对象旁边的下拉菜单。 然后从菜单中选择 "从右到左"。

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. 选择手关节后，可以选择希望立方体跟随的手的某个部分。 对于本示例，我们将使用手腕。 在 "所选的选项" 旁边, 选择下拉菜单, 然后选择 "手腕"。 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. 将最大和最小距离设置为 0，使立方体与用户的手腕之间没有任何距离。 设置后，立方体将与手腕完全对齐。 您还可以调整 "引用方向" 字段以调整多维数据集的方向行为, 例如, 如果您想要允许对象通过将引用方向设置为与被跟踪对象一起旋转来旋转用户的手腕。

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>祝贺
在本教程中, 已学习如何使用 MRTK 的 solvers 让 UI 直观地追随用户。 你还了解了如何将求解器附加到游戏对象（这里是立方体）以跟随用户被追踪的双手。 要详细了解上述求解器以及 MRTK 中包含的其他求解器，请访问 [MRTK 求解器文档页面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。

[下一课：5.  与 3D 对象交互](mrlearning-base-ch4.md)

