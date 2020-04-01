---
title: 入门教程 - 4. 放置动态内容和使用解算器
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362036"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4.放置动态内容和使用解算器
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

当全息影像直观地跟随用户并且在物理环境中无缝巧妙地参与互动时，它们在 HoloLens 2 中会变得真实生动。 本教程探讨如何使用 MRTK 提供的定位工具（称为“解算器”）动态放置全息影像，以解算复杂的空间定位方案。 在 MRTK 中，解算器是一个脚本和行为系统，可让 UI 元素跟随你、用户或场景中的其他游戏对象。 它们还可用于快速贴靠到某个位置，使应用程序更加直观。

## <a name="objectives"></a>目标

* 介绍 MRTK 的解算器
* 使用解算器让一组按钮跟随用户
* 使用解算器使游戏对象跟随用户的跟踪手

## <a name="location-of-solvers-in-the-mrtk"></a>解算器在 MRTK 中的位置

 MRTK 的解算器位于 MRTK SDK 文件夹中。 若要在项目中查看可用的解算器，请在“项目”窗口中，导航到“资产” > “MixedRealityToolkit.SDK” > “功能” > “实用工具” > “解算器”：     

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

本教程将回顾轨道解算器和径向视图解算器的实现。 若要详细了解 MRTK 中提供的各个解算器，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

## <a name="use-a-solver-to-follow-the-user"></a>使用解算器跟随用户
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

在本部分，你将增强在上一篇教程中创建的按钮集合，使其跟随用户的视线方向。 此外，将配置解算器，使按钮集合始终：

* 平行于用户的阅读方向旋转（人们习惯于从左到右阅读）
* 定位在低于用户水平视线的位置，使其不会阻挡稍后要在本教程中添加的其他对象
* 定位在相距用户大约半个手臂长度的位置，以便可以方便地按下按钮

为此，你将使用**轨道解算器**将对象锁定在指定的位置，并与参照对象之间保持一定的偏移量。

### <a name="1-add-the-orbital-solver"></a>1.添加轨道解算器

在“层次结构”窗口中选择“ButtonCollection”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“轨道(脚本)”组件添加到 ButtonCollection 对象。   

> [!NOTE]
> 添加解算器（在本例中为“轨道(脚本)”组件）时，会自动添加“解算器处理程序(脚本)”组件，因为解算器需要该组件。

### <a name="2-configure-the-orbital-solver"></a>2.配置轨道解算器

配置“解算器处理程序(脚本)”组件： 

* 确认“跟踪的目标类型”是否设置为“头部”  

配置“轨道(脚本)”组件： 

* 确认“方向类型”是否设置为“跟随跟踪的对象”  
* 将“本地偏移”重置为 X = 0，Y = 0，Z = 0 
* 将“世界偏移”更改为 X = 0，Y = -0.4，Z = 0.3 

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3.使用编辑器中的模拟功能测试轨道解算器

按“播放”按钮进入“游戏”模式，然后在按住鼠标右键的同时旋转视线方向，此时会注意到以下情况：

* ButtonCollection 的变换位置现在由解算器设置驱动
* 不受解算器影响的立方体保留在同一位置

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> 如果在“场景”窗口中未看到相机光线，请确保已启用调节器菜单。 若要详细了解调节器菜单以及如何使用它来优化场景视图，可以访问 Unity 的<a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">调节器菜单</a>文档。
>
> 若要按上图所示并排显示“场景”和“游戏”窗口，只需将“游戏”窗口拖放到“场景”窗口的右侧。 若要详细了解如何自定义工作区，可以访问 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自定义工作区</a>文档。

## <a name="enabling-objects-to-follow-tracked-hands"></a>使对象跟随跟踪手

在本部分，你将配置在上一篇教程中创建的立方体对象，使其跟随用户的跟踪手，具体而言是右手手腕。 此外，将配置解算器，使立方体：

* 根据用户手部的旋转改变自身的方向
* 定位在用户的手腕上

为此，你将使用**径向视图解算器**使对象保留在参照对象投射的锥形视图范围内。

### <a name="1-add-the-radial-view-solver"></a>1.添加径向视图解算器

在“层次结构”窗口中选择“Cube”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“径向视图(脚本)”组件的 Cube 对象。   

### <a name="2-configure-the-radial-view-solver"></a>2.配置径向视图解算器

配置“解算器处理程序(脚本)”组件： 

* 将“跟踪的目标类型”更改为“手关节”  
* 将“跟踪左手还是右手”更改为“右手”  
* 将“跟踪的手关节”更改为“手腕”  

配置“径向视图(脚本)”组件： 

* 将“参照方向”更改为“对象定向”，然后选中“按参照方向定向”复选框   
* 将“最小距离”和“最大距离”更改为 0  

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3.使用编辑器中的模拟功能测试径向视图解算器

按“播放”按钮进入“游戏”模式，然后在按住空格键的同时抬手。 移动鼠标光标以移动手形，然后在按住鼠标左键的同时旋转手部：

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>祝贺

在本课程中，你已了解如何使用 MRTK 的解算器使 UI 直观地跟随用户。 你还了解了如何将解算器附加到某个对象（这里是立方体）以跟随用户的跟踪手。 若要详细了解上述解算器以及 MRTK 中包含的其他解算器，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

[下一教程：5.与 3D 对象交互](mrlearning-base-ch4.md)
