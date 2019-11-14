---
title: 入门教程-4。 放置动态内容并使用 solvers
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: ade7a839e03a306332bf18f1db49805f59c71429
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064259"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. 放置动态内容并使用 solvers

当你直观地关注用户并将其放置在物理环境中，使交互方式无缝且精致，就能在 HoloLens 2 中生活。 在本教程中，我们将探讨如何使用 MRTK 的可用放置工具（称为 solvers）动态放置全息影像，以解决复杂的空间放置方案。 在 MRTK 中，solvers 是一种脚本和行为的系统，用于允许 UI 元素跟随你、用户或场景中的其他游戏对象。 它们还可用于快速贴靠到某个位置，使应用程序更加直观。

## <a name="objectives"></a>目标

* 介绍 MRTK 的求解器
* 使用求解器让一组按钮跟随用户
* 使用求解器使游戏对象跟随用户被追踪的双手

## <a name="instructions"></a>说明

### <a name="location-of-solvers-in-the-mrtk"></a>求解器在 MRTK 中的位置

 若要在项目中查找可用的 solvers，请查看 MRTK SDK 文件夹（MixedRealityToolkit 文件夹）。 在 "实用程序" 文件夹下，会显示 solvers 文件夹，如下图所示。

![求解器](images/lesson3_chapter1_step1im.PNG)

>[!NOTE]
>在本课中，我们将只回顾 Orbital 求解器和 RadialView 求解器的实现。 若要详细了解 MRTK 中可用的 solvers 的详细信息，请访问： [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

### <a name="use-a-solver-to-follow-the-user"></a>使用求解器跟随用户

本章的目标是增强之前创建的按钮集合，使其遵循用户的注视方向。 在以前版本的 MRTK 和 HoloToolkit 中，这称为 tagalong 功能。

1. 从上一节课中选择按钮集合父对象。

    ![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. 在检查器面板中，单击 "添加组件" 按钮，然后搜索 "orbital"。 应显示 "Orbital" 组件。 选择该按钮，将 Orbital 组件添加到 "按钮集合游戏" 对象。

    ![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

    >[!NOTE]
    >添加 Orbital 组件时，你会注意到，系统还添加了 SolverHandler 组件，这是必需的组件。

3. 若要将按钮集合配置为关注用户，我们需要实现以下调整（请参阅下图）：
    * 在 Orbital 脚本中，将 "方向类型" 下拉列表设置为 "仅偏航"。 这样，在对象跟随用户时，它只有一个轴在旋转。
    * 将所有轴上的局部偏移量设置为 0。 将世界偏移量设置为 x = 0、y =-0.1 和 z = 0.6。 这会锁定对象的移动，以便在用户更改高度时，对象将在物理环境中保持为固定高度，同时在用户移动有关环境的情况下仍允许它跟随用户。 可以调整这些值以实现广泛的行为。
    * 对于这种情况，在用户完全关闭用户的头衔后，只关注用户的视图，你可以选择 "对全球偏移使用角度单" 复选框（注意：在某些屏幕上可能会截断此标题，如下图所示）。例如，若要让对象每隔90度仅关注用户，请设置等于4的步骤数（在下面的示例中，用绿色箭头进行标记）。

    ![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>使对象跟随跟踪的手

在本部分中，我们将配置先前创建的 Cube 游戏对象，以使用 RadialView 求解器按用户跟踪。

1. 选择 BaseScene 层次结构中的多维数据集对象。 单击 "检查器" 面板中的 "添加组件"。 在 "搜索" 框中键入 RadialView，然后选择 "RadialView" 组件以将其添加到多维数据集中。 SolverHandler 组件还将自动添加到多维数据集中。

    ![mrlearning-base-ch3-3-step3 .png](images/mrlearning-base-ch3-3-step1.png)

2. 若要将 RadialView 改为使用一只手而不是标题，请选择 "所跟踪的目标类型" 选项旁边的下拉菜单，然后从菜单中选择 "手动联合"。

    ![mrlearning-base-ch3-3-step2 .png](images/mrlearning-base-ch3-3-step2a.png)

    现在，你将看到两个新选项： "跟踪的 Handness 类型" 和 "已跟踪"。 在此示例中，你将拥有 RadialView 的背面，如下图所示。

    ![mrlearning-base-ch3-3-step2b .png](images/mrlearning-base-ch3-3-step2b.png)

3. 将径向视图的最大和最小距离设置为0，以便使多维数据集不会在其与用户的手腕之间没有任何距离。 设置后，立方体将与手腕完全对齐。 您还可以调整 "引用方向" 字段以调整多维数据集的方向，如您希望允许对象通过设置面向对象的引用方向来与用户的手腕一起旋转。

    ![mrlearning-base-ch3-3-step3 .png](images/mrlearning-base-ch3-3-step3.png)

## <a name="congratulations"></a>祝贺

在本教程中，已学习如何使用 MRTK 的 solvers 让 UI 直观地追随用户。 你还了解了如何将求解器附加到游戏对象（这里是立方体）以跟随用户被追踪的双手。 要详细了解上述求解器以及 MRTK 中包含的其他求解器，请访问 [MRTK 求解器文档页面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。

[下一课： 5. 与三维对象交互](mrlearning-base-ch4.md)
