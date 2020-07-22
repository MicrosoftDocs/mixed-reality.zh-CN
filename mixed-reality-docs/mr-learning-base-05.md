---
title: 入门教程 - 5. 使用求解器创建动态内容
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbeaa8b65b7aecc0600294b3739fedfb903e568e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304773"
---
# <a name="5-creating-dynamic-content-using-solvers"></a>5.使用求解器创建动态内容

## <a name="overview"></a>概述

本教程探讨如何使用 MRTK 提供的定位工具（求解器）动态放置全息影像，以解算复杂的空间定位场景。 在 MRTK 中，求解器是一个脚本和行为系统，可让对象跟随你、用户或场景中的其他游戏对象。 它们还可用于贴靠到某些位置，使应用更加直观。

## <a name="objectives"></a>目标

* 介绍 MRTK 的解算器
* 了解如何使用求解器将用户定向到对象
* 了解如何使用求解器重新定位对象

## <a name="location-of-solvers-in-the-mrtk"></a>解算器在 MRTK 中的位置

 MRTK 的解算器位于 MRTK SDK 文件夹中。 若要在项目中查看可用的求解器，请在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “功能” > “实用工具” > “求解器”     ：

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

本教程将回顾方向指示器求解器和点击放置求解器的实现。 若要详细了解 MRTK 中提供的各个求解器，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[求解器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

> [!NOTE]
> 方向指示器求解器不在上面所述的求解器文件夹中，而是在“资产”>“MRTK”>“SDK”>“实验性”>“功能”>“实用工具”文件夹，因为这是一项实验性功能。

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a>使用方向指示器求解器将用户定向到对象

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”文件夹，单击 V 形预制件并将其拖放到“层次结构”窗口中，然后将其“转换”位置设置为 X = 0、Y = 0、Z = 2，使其定位到 RoverExplorer 对象附近    ：

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> 如果在场景中发现相机或任何其他图标隐藏了对象或让人分心，则可以通过<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切换调节器</a>（切换到关闭位置）来隐藏这些图标，如下图所示。 若要详细了解调节器菜单以及如何使用它来优化场景视图，可以参阅 Unity 的<a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">调节器菜单</a>文档。

重命名新添加的 V 形对象指示器，然后在“检查器”窗口中，使用“添加组件”按钮添加 DirectionalIndicator 和“方向指示器控制器(脚本)”组件   ：

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> 添加求解器（在本例中为 DirectionalIndicator 组件）时，系统会自动添加 SolverHandler 组件，因为求解器需要该组件。

> [!NOTE]
> “方向指示器控制器(脚本)”并不是 MRTK 的一部分，而是属于本教程的资源。

按如下所示配置 DirectionalIndicator 和 SolverHandler 组件：

* 验证 SolverHandler 组件的“跟踪的目标类型”是否设置为“头部”  
* 将 RoverExplorer 分配到 DirectionalIndicator 组件的方向目标，具体方法是将其从“层次结构”窗口拖到“无(转换)”字段   
* 将“视图偏移量”更改为 0.2

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

按“播放”按钮进入“游戏”模式，然后在按住鼠标右键的同时在左右移动鼠标以旋转视线方向，此时你会注意到以下情况：

* 当你将视线从 RoverExplorer 对象移开时，将看到 Indicator 对象，它指向 RoverExplorer 对象

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> 如果在“场景”窗口中未看到相机光线，请确保已启用调节器菜单，如上图所示。

> [!TIP]
> 若要了解如何使用编辑器中的输入模拟功能，可以参考 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用编辑器中的手写输入模拟来测试场景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。

> [!TIP]
> 如果计算机有麦克风，你可以使用语音命令“切换诊断”轻松切换游戏窗口中显示的“诊断”面板的活动状态。 或者，你也可以在“MRTK 配置文件”>“诊断”>“启用诊断系统”中禁用它。 但是，我们通常建议你在开发过程中使诊断系统保持活动状态。

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a>使用点击放置求解器重新定位对象

在“层次结构”窗口中依次选择“RoverExplorer”>“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“点击放置(脚本)”组件，并按如下所述配置该组件：  

* 验证 SolverHandler 组件的“跟踪的目标类型”是否设置为“头部”  
* 选中“保持垂直方向”复选框
* 从“磁性界面” > “元素 0”下拉列表中，取消选中除“空间感知”以外的所有选项  

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> 磁性界面设置可确定放置对象时“点击放置(脚本)”组件可以检测的对象。 将设置更改为仅“空间感知”后，“点击放置(脚本)”组件将只能在名为“空间感知”的 Unity 层上放置对象的探测器，默认情况下，它是由 HoloLens 生成的空间感知网格。
>
>若要了解有关层的详细信息，可以参考 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">层</a>文档。

> [!TIP]
> 如果要在 HoloLens 上测试“点击放置”功能时查看空间感知网格，你可以暂时将空间网格观察程序的“显示”选项设置为“可见”。 有关如何更改“显示”选项的提醒，可参考[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)说明。

仍在“层次结构”窗口中选中“RoverAssembly”对象，在“检查器”窗口中找到“On Placing Started ()”事件，然后单击 + 图标以添加新事件 ：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

按如下所示配置事件：

* 将 RoverAssembly 对象指定为“On Placing Started ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 
* 在“无函数”下拉列表中，选择“TapToPlace” > “float SurfaceNormalOffset”，以便在触发事件时更新 SurfaceNormalOffset 属性值  
* 验证参数是否设置为 0

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

在“层次结构”窗口中，右键单击空白区域，然后选择“3D 对象” > “Cube”，创建代表地面的临时对象，并按如下所示配置“转换”组件  ：

* **位置**：X = 0, Y = -1.65, Z = 6
* **旋转**：X = 0, Y = 0, Z = 0
* **缩放**：X = 10, Y = 0.2, Z = 10

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

仍在“层次结构”窗口中选中临时 Cube，在“检查器”窗口中使用“层”下拉列表来更改 Cube 的层设置，使之仅包含“空间感知”层 ：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

按下“播放”按钮进入“游戏”模式，然后在按住鼠标右键的同时向下移动鼠标，直到视线瞄准 RoverAssembly 对象：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

单击鼠标左键以启动“点击放置”过程：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

按住鼠标右键的同时左右移动鼠标以旋转视线方向，对定位感到满意后，单击鼠标左键：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

在“游戏”模式下测试完功能后，右键单击 Cube 对象，然后选择“删除”，以从场景中将其删除：

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何使用 MRTK 的方向指示器求解器让 UI 元素直观地将用户定向到对象。 还了解了如何使用“点击放置”求解器轻松重新定位对象。

若要详细了解上述求解器以及 MRTK 中包含的其他求解器，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[求解器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。

[下一教程：6.创建用户界面](mr-learning-base-06.md)
