---
title: MR 学习基本模块的动态内容的位置和求解器
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: unity 中，教程，hololens 混合的现实
ms.openlocfilehash: b212812beeff54bb1f92ccbcc923ab9c301945b7
ms.sourcegitcommit: a32f673814a6cd6ff00f936f448885788b3b882c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2019
ms.locfileid: "64929558"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>MR 学习基本模块的动态内容的位置和求解器

全息来自生活 HoloLens 2 中，在直观的用户操作和放置在使交互，无缝且简洁的方式中的物理环境时。 在第 3 课，我们将探讨方法可以动态地将全息使用 MRTK 的可用布局工具，称为"求解器。" 它们被称为"求解器"，它们解决复杂的空间放置算法的方式。 在 MRTK，求解器是系统的脚本和我们使用能够允许 UI 元素跟随你，用户或其他场景中的游戏对象的行为。 它们还可用来对齐到特定位置快速，从而使您的应用程序更直观。 

## <a name="objectives"></a>目标

* 引入 MRTK 求解器
* 使用求解器具有一组按钮的用户操作
* 使用求解器将使游戏对象按照用户的手中跟踪

## <a name="instructions"></a>说明

### <a name="location-of-solvers-in-the-mrtk"></a>在 MRTK 求解器的位置
 要在项目中查找可用求解器，请检查 MRTK SDK 文件夹 （MixedRealityToolkit.SDK 文件夹中），然后在 utilities 文件夹中会求解器文件夹中，如下图中所示。

![求解器](images/lesson3_chapter1_step1im.PNG)

>注意：在本课程中我们只会通过"绕"解算器和"RadialView"解算器的实现。 若要了解有关推出 MRTK 求解器的完整范围的详细信息，请访问： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>使用解算器的用户操作
本章旨在增强我们之前创建，以便它遵循用户的视线移动方向的按钮集合。 在以前版本的 MRTK 和 HoloToolkit，这被称为"taglong"功能。

1. 从上一课中选择按钮集合的父对象。

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. 在检查器窗格中，单击"添加组件"按钮并搜索"绕。" 绕组件应显示。 选择它以将绕组件添加到按钮集合游戏对象。

![Lesson3 第 2 章 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>注意：添加组件时你会注意到系统中检查器选项卡上，这是必需的组件添加绕脚本和解算器处理程序脚本。 

3. 若要配置的按钮集合的用户操作，我们需要实现以下调整 （另请参阅下图所示）：
- 在绕脚本中，将设置为"仅偏航。""方向类型"下拉列表 这样就使该对象，只有一个轴旋转，它如下所示的用户。
- 设置为 0 的所有轴上的本地偏移量。 设置世界偏移量为 x = 0，y =-0.1 和 z = 0.6。 这将锁定对象的移动，以便当用户更改高度，该对象将始终保持固定高度在物理环境中，同时仍允许其用户在将移动有关环境的用户操作。 这些值进行调整，以实现 wade 行为范围之内。
- 对于以下行为，凭此按钮仅按照用户的视图后在用户打开他或她头保持足够距离，可以选择"使用角度单步执行的全局偏移量"复选框 (请注意：此标题可能会被截断某些在屏幕上，因为它是在下图中。）例如，如果希望仅每隔 90 度的用户操作的对象，请将步骤数设置为 4 （由左侧的示例中的绿色箭头标记）。 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>使对象能够按照跟踪的手

在本部分中，我们将配置以前创建遵循使用 RadialView 解算器的用户的被跟踪的手的多维数据集游戏对象。

1. BaseScene 层次结构中选择多维数据集对象。 单击检查器面板中的"添加组件"。 

![Lesson3 第 3 章 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. 在搜索框中键入"RadialView"并选择要将其添加到多维数据集的 RadialView 组件。 解算器处理程序组件将也会自动添加到多维数据集。

3. 更改径向视图以不遵循头，但按照左侧显示。 选择"跟踪对象，以引用"选项旁边的下拉列表菜单。 然后，从菜单选择"将剩余的联合"。

![Lesson3 第 3 章 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. 一旦您选择现有联合，可以选择希望多维数据集遵循手形图标的哪个部分。 对于此示例中，我们将使用手腕。 选项旁边"跟踪的手联合"选择下拉列表菜单，然后选择手腕。 

![Lesson3 第 3 章 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. 设置为 0 的最大和最小距离，以使多维数据集不具有任何它与用户的手腕之间的距离。 完成设置后，该多维数据集将是完全对齐手腕。 您还可以调整"引用方向"字段以调整的方式在多维数据集中的方向 （例如，如果你想要允许的对象要随用户的手腕旋转，请将"定位与跟踪对象"引用方向） 的行为

![Lesson3 第 3 章 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>恭喜 ！
祝贺你！ 在本课程中，您学习了如何使用 MRTK 求解器具有直观的用户操作的用户界面。 您还学习了如何将解算器附加到游戏对象 （即，多维数据集），从而按照用户的被跟踪的手。 若要了解有关这些和其他 MRTK 中包含的求解器的详细信息，可随意访问[MRTK 求解器文档页](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。

[下一课：三维对象交互](mrlearning-base-ch4.md)

