---
title: 入门教程-4。 放置动态内容并使用 solvers
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 8275d5a97d7827d34ed3926cabe4032cc7f4cfac
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129303"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. 放置动态内容并使用 Solvers
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

当你直观地关注用户并将其放置在物理环境中，使交互方式无缝且精致，就能在 HoloLens 2 中生活。 在本教程中，我们将探讨如何使用 MRTK 的可用放置工具（称为 Solvers）动态放置全息影像，以解决复杂的空间放置方案。 在 MRTK 中，Solvers 是一种脚本和行为的系统，用于允许 UI 元素跟随你、用户或场景中的其他游戏对象。 它们还可用于快速贴靠到某个位置，使应用程序更加直观。

## <a name="objectives"></a>目标

* 介绍 MRTK 的 Solvers
* 使用 Solvers 对用户执行按钮的集合
* 使用 Solvers 使游戏对象跟随用户的跟踪

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK 中 Solvers 的位置

 MRTK 的 Solvers 位于 MRTK SDK 文件夹中。 若要在项目中查看可用的 Solvers，请在 "项目" 窗口中，导航到 "**资产**" > **MixedRealityToolkit** > **功能**" > **实用工具**" > **Solvers**：

![mrlearning](images/mrlearning-base/tutorial3-section1-step1-1.png)

在本教程中，我们将回顾 Orbital 求解器和径向视图规划求解的实现。 若要详细了解 MRTK 中可用的 Solvers 的详细信息，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

## <a name="use-a-solver-to-follow-the-user"></a>使用规划求解来追随用户
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

在本部分中，您将增强在上一教程中创建的按钮集合，使其遵循用户的注视方向。 此外，您还将配置规划求解，使按钮集合始终为：

* 与用户的阅读方向平行旋转，适用于自然从左到右阅读
* 置于稍微低于用户的 "注视" 方向，因此它不会阻碍您稍后将在本教程中添加的其他对象
* 在用户中定位大约一半的 arm 长度，因此可以轻松地按下按钮

为此，你将使用**Orbital 求解**器，它将对象锁定到指定的位置，并与所引用的对象偏移。

### <a name="1-add-the-orbital-solver"></a>1. 添加 Orbital 求解器

在 "层次结构" 窗口中，选择 " **ButtonCollection** " 对象，然后在 "检查器" 窗口中，使用 "**添加组件**" 按钮将**Orbital （脚本）** 组件添加到 ButtonCollection 对象。

> [!NOTE]
> 添加规划求解（在本例中为 Orbital （Script）组件）时，将自动添加 "规划求解处理程序（脚本）" 组件，因为它是求解器所必需的。

### <a name="2-configure-the-orbital-solver"></a>2. 配置 Orbital 求解器

配置**规划求解处理程序（脚本）** 组件：

* 验证**跟踪的目标类型**是否设置为**Head**

配置**Orbital （脚本）** 组件：

* 更改**方向类型**以跟踪**跟踪的对象**
* 将**局部偏移量**重置为 X = 0、Y = 0、Z = 0
* 将**世界偏移量**更改为 X = 0，Y =-0.4，Z = 0。3

![mrlearning](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. 使用编辑器内模拟测试 Orbital 求解器

按下 "播放" 按钮进入游戏模式，然后按住鼠标右键以旋转注视方向，并注意以下事项：

* 现在，ButtonCollection 的转换位置由求解器设置驱动
* 多维数据集不受求解器影响的多维数据集将保持不变

![mrlearning](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> 如果在场景窗口中看不到相机射线，请确保已启用 Gizmos 菜单。 若要详细了解 Gizmos 菜单以及如何使用它来优化场景视图，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos 菜单</a>文档。
>
> 若要在上图中并排显示场景和游戏窗口，只需将游戏窗口拖到场景窗口的右侧。 若要详细了解如何自定义工作区，可访问 Unity<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自定义工作区</a>文档。

## <a name="enabling-objects-to-follow-tracked-hands"></a>使对象跟随跟踪的手

在本部分中，你将配置在上一教程中创建的多维数据集对象，使其跟随用户的跟踪，尤其是右边的手腕。 此外，还会将规划求解配置为多维数据集：

* 更改用户的旋转方向
* 定位在用户的手腕上

为此，您将使用**径向视图规划求解**，使被引用对象在视图锥内转换对象。

### <a name="1-add-the-radial-view-solver"></a>1. 添加径向视图规划求解

在 "层次结构" 窗口中，选择**多维数据集**对象，然后在 "检查器" 窗口中，使用 "**添加组件**" 按钮添加**径向视图（脚本）** 组件多维数据集对象。

### <a name="2-configure-the-radial-view-solver"></a>2. 配置径向视图规划求解

配置**规划求解处理程序（脚本）** 组件：

* 将**跟踪的目标类型**更改为**手动接点**
* 将**跟踪的 Handness**更改为**Right**
* 更改与**手腕**的**接点**

配置**径向视图（脚本）** 组件：

* 更改**面向对象**的**引用方向**，然后选中 "**定向到引用方向**" 复选框
* 更改**最小距离**和**最大距离**为0

![mrlearning](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. 使用编辑器内模拟测试径向视图规划求解

按下 "播放" 按钮进入游戏模式，然后按住空格键以调出手。 将鼠标光标移动到手上，然后单击并按住鼠标左键来旋转手：

![mrlearning](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>祝贺你

在本教程中，已学习如何使用 MRTK 的 solvers 让 UI 直观地追随用户。 还了解了如何将规划求解附加到对象（即多维数据集），以遵循用户的跟踪。 若要详细了解 MRTK 随附的这些和其他 solvers，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

[下一教程： 5. 与三维对象交互](mrlearning-base-ch4.md)
