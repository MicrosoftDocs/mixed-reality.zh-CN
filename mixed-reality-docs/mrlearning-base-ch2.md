---
title: 入门教程-3。 创建用户界面并配置混合现实工具包
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 067832a130f130ffbaa8d455007b8e77e1b13671
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130474"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. 创建用户界面并配置混合现实工具包
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

在上一教程中，你已了解到混合现实工具包（MRTK）通过启动适用于 HoloLens 2 的第一个应用程序而必须提供的一些功能。 在本教程中，您将学习如何创建和组织按钮以及 UI 文本面板，并使用默认交互（触摸）与每个按钮进行交互。 此外，本课还会探讨如何添加简单的操作和效果，例如更改对象的大小、声音和颜色。 此模块将介绍有关修改 MRTK 配置文件的基本概念，从关闭[空间映射](spatial-mapping.md)网格可视化效果开始。

## <a name="objectives"></a>目标

* 自定义和配置混合现实工具包配置文件
* 使用 UI 元素和按钮与全息影像交互
* 基本的手动跟踪输入和交互

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何配置混合现实工具包配置文件（更改空间感知显示选项）
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

在本部分中，你将学习如何自定义和配置默认的 MRTK 配置文件。

此特定示例将演示如何通过更改空间网格观察程序的设置来隐藏空间感知网格。 但是，你可以遵循这些相同的原则自定义 MRTK 配置文件中的任何设置或值。

隐藏空间感知网格需要执行的主要步骤如下：

1. 克隆默认配置文件
2. 启用空间感知系统
3. 克隆默认的空间感知系统配置文件
4. 克隆默认的空间感知网格观察程序配置文件
5. 更改空间感知网格的可见性

> [!NOTE]
> 默认情况下，MRTK 配置文件不可编辑。 这些是默认的配置文件模板，你必须先进行克隆，然后才能编辑它们。 配置文件有多个嵌套层。 因此，在配置一个或多个设置时，通常会克隆和编辑多个配置文件。

### <a name="1-clone-the-default-configuration-profile"></a>1. 克隆默认配置文件

> [!NOTE]
> 配置文件是顶级配置文件。 因此，为了能够编辑任何其他配置文件，你必须首先克隆配置文件。

在 "层次结构" 窗口中选择**MixedRealityToolkit**对象后，在 "检查器" 窗口中，单击 "**复制 & 自定义**" 按钮以打开 "克隆配置文件" 窗口：

![mrlearning](images/mrlearning-base/tutorial2-section1-step1-1.png)

在 "克隆配置文件" 窗口中，单击 "**克隆**" 按钮，创建**DefaultHololens2ConfigurationProfile**的可编辑副本：

![mrlearning](images/mrlearning-base/tutorial2-section1-step1-2.png)

新创建的配置文件现已分配为场景的配置文件：

![mrlearning](images/mrlearning-base/tutorial2-section1-step1-3.png)

在 Unity 菜单中，选择 "**文件**" > **保存**"以保存场景。

> [!TIP]
> 请记住在整个教程中保存您的工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2. 启用空间感知系统

仍在 "层次结构" 窗口中选择**MixedRealityToolkit**对象后，在 "检查器" 窗口中，选择 "**空间感知**" 选项卡，然后选中 "**启用空间感知系统**" 复选框：

![mrlearning](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. 克隆默认的空间感知系统配置文件

在 "**空间感知**" 选项卡中，单击 "**克隆**" 按钮打开 "克隆配置文件" 窗口：

![mrlearning](images/mrlearning-base/tutorial2-section1-step3-1.png)

在 "克隆配置文件" 窗口中，单击 "**克隆**" 按钮，创建**DefaultMixedRealitySpatialAwarenessSystemProfile**的可编辑副本：

![mrlearning](images/mrlearning-base/tutorial2-section1-step3-2.png)

新创建的空间感知系统配置文件现在会自动分配给配置文件：

![mrlearning](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. 克隆默认的空间感知网格观察程序配置文件

在仍然选择 "**空间感知**" 选项卡的情况下，展开 " **Windows Mixed Reality 空间网格观察**程序" 部分，然后单击 "**克隆**" 按钮以打开克隆配置文件窗口：

![mrlearning](images/mrlearning-base/tutorial2-section1-step4-1.png)

在 "克隆配置文件" 窗口中，单击 "**克隆**" 按钮，创建**DefaultMixedRealitySpatialAwarenessMeshObserverProfile**的可编辑副本：

![mrlearning](images/mrlearning-base/tutorial2-section1-step4-2.png)

此时，新建的空间感知网格观察程序配置文件会自动分配给空间感知系统配置文件：

![mrlearning](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. 更改空间感知网格的可见性

在**空间网格观察程序设置**中，将**显示选项**更改为**封闭**，使空间映射网格在仍正常运行时不可见：

![mrlearning](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> 虽然空间映射网格不可见，但它仍然存在且正常工作。 例如，空间映射网格后面的任何全息影像（如物理壁后面的全息图）都将不可见。

你已了解如何修改 MRTK 配置文件中的设置。 正如您所看到的，为了自定义 MRTK 设置，您首先需要创建默认配置文件的副本。 因为默认的配置文件是不可编辑的，所以，如果要还原为默认设置，你始终会将它们作为参考。 若要了解有关 MRTK 配置文件及其体系结构的详细信息，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[混合现实工具包配置文件配置指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>手动跟踪手势和种不可交互按钮

在本部分中，你将学习如何使用手动跟踪按下按钮，并在按下按钮时触发事件，从而导致操作。

此特定示例将演示如何在按下按钮时更改多维数据集的颜色，并在释放按钮时将其更改回原始颜色。 但是，您可以遵循这些相同的原则来创建其他事件。

更改多维数据集颜色的主要步骤如下：

1. 将 pressable 按钮 prefab 添加到场景
2. 将多维数据集添加到场景
3. 配置 InteractableOnPressReceiver 事件类型
4. 配置多维数据集以接收按下事件
5. 定义要在按下事件时触发的操作
6. 配置多维数据集以接收 On Release 事件
7. 定义要在发布事件时触发的操作
8. 使用编辑器中的模拟测试按钮

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. 向场景添加 pressable 按钮 prefab

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a>是作为 Unity 资产存储的预配置 GameObject，可在整个项目中重复使用。

在 "**项目" 窗口**中，搜索**PressableButtonHoloLens2**以查找将用于此示例的 prefab：

![mrlearning](images/mrlearning-base/tutorial2-section2-step1-1.png)

在**搜索**结果中，选择**PressableButtonHoloLens2** prefab 并**将其拖**到 "**层次结构**" 窗口中，将其添加到场景：

![mrlearning](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> 若要按下图所示显示场景，请在 "层次结构" 窗口中双击 "PressableButtonHoloLens2" 对象以使其成为焦点，然后使用位于场景窗口右上角的<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">场景别出心裁</a>，将查看角度调整为沿正向 Z 轴。

在 PressableButtonHoloLens2 对象仍处于选中状态的**检查器**窗口中：

* 更改其转换**位置**，使其位于相机前面（例如 x = 0、y = 0 和 z = 0.5）。

![mrlearning](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> 通常，Unity 中的1个位置单位大致相当于物理世界中的1米。 但存在一些例外情况，例如，当对象是缩放对象的子级时。

### <a name="2-add-a-cube-to-the-scene"></a>2. 将多维数据集添加到场景

右键单击 "层次结构" 窗口中的空白点，然后选择 " **3D 对象** > **多维数据集**以将多维数据集添加到场景：

![mrlearning](images/mrlearning-base/tutorial2-section2-step2-1.png)

如果仍选中多维数据集对象，则在 "**检查器**" 窗口中：

* 更改其转换**位置**，使其位于 "pressable" 按钮附近，但不与它重叠，例如 x = 0、y = 0.04 和 z = 0。5
* 将其转换**比例**更改为合适的大小，例如 x = 0.02、y = 0.02 和 z = 0.02

![mrlearning](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. 配置 InteractableOnPressReceiver 事件类型

在 "层次结构" 窗口中选择 "PressableButtonHoloLens2" 对象之后，在 "**检查器**" 窗口**汉堡菜单**中，选择 " **Collaps 所有组件**" 以获取此对象上的所有组件的概述：

![mrlearning](images/mrlearning-base/tutorial2-section2-step3-1.png)

展开**种不可交互（脚本）** 组件，然后找到并展开 "**事件** > **接收**方" 部分：

![mrlearning](images/mrlearning-base/tutorial2-section2-step3-2.png)

对于事件接收器类型**InteractableOnPressReceiver**，请将**交互筛选器**更改为 "**接近" 和 "远**"：

![mrlearning](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> 名为 InteractableOnPressReceiver 的事件接收器类型允许按钮在按下按钮时响应按下的事件。

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. 配置多维数据集以接收按下事件

在 "层次结构" 窗口中，**单击并将** **多维数据集**拖动到 "**按下（）** 事件的**事件属性**对象" 字段中，以便将多维数据集分配为按下（）事件的接收方：

![mrlearning](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. 定义要在按下事件时触发的操作

单击 "操作" 下拉列表，当前未分配 "**函数**"，然后选择 " **MeshRenderer** > **材料材料**，以设置在触发 On 按下（）事件时要更改的多维数据集的材料属性：

![mrlearning](images/mrlearning-base/tutorial2-section2-step5-1.png)

单击 "材料" 字段旁边的小**圆圈**图标（当前填充了 "**无（材料）"）** 以打开 "选择材料" 窗口：

![mrlearning](images/mrlearning-base/tutorial2-section2-step5-2.png)

在 "选择材料" 窗口中，**搜索**" **MRTK_Standard** " 并选择合适的材料，例如**MRTK_Standard_Cyan** ，以便在按下按钮时，多维数据集的颜色更改为 "青色"：

![mrlearning](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. 配置多维数据集以接收 On Release 事件

**重复**"发布时" 事件的步骤4，用于将多维数据集分配为 On Release （）事件的接收方。

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. 定义要在发布事件时触发的操作

**重复**第5步：对于 "发布" 事件，但选择 " **MRTK_Standard_LightGray**材料，以便在按钮被释放时，将多维数据集的颜色恢复为其原始的浅灰色颜色：

![mrlearning](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. 使用编辑器内模拟测试按钮

按 "**播放**" 按钮进入游戏模式，并使用编辑器内输入模拟来测试新配置的按钮。

未按下按钮（向后滚动鼠标滚轮）：

![mrlearning](images/mrlearning-base/tutorial2-section2-step8-1.png)

按下按钮（向前滚动滚轮）：

![mrlearning](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> 若要了解如何使用编辑器内输入模拟，可以参考[使用编辑器内手写输入模拟](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)在[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中测试场景指南。

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>使用 MRTK 的网格对象集合创建按钮面板

在本部分中，你将了解如何使用 MRTK 的网格对象集合工具自动将多个按钮对齐到巧妙的用户界面。

此特定示例将演示如何创建一个面板，该面板具有水平对齐的五个按钮。 但是，您可以遵循这些相同的原则来创建其他布局。

为实现此目的需要执行的主要步骤如下：

1. 父对象的父对象的父对象
2. 添加和配置网格对象集合（脚本）组件
3. 使用编辑器内模拟测试按钮

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. 将 button 对象父对象的父对象

右键单击 "层次结构" 窗口中的空白点，然后选择 "**创建空**项"：

![mrlearning](images/mrlearning-base/tutorial2-section3-step1-1.png)

右键单击新创建的对象，选择 "**重命名**"，并为其指定一个适当的名称，例如**ButtonCollection**：

![mrlearning](images/mrlearning-base/tutorial2-section3-step1-2.png)

选择**PressableButtonHoloLens2**对象并**将其拖**到**ButtonCollection**对象的顶部，使其成为 ButtonCollection 对象的子元素：

![mrlearning](images/mrlearning-base/tutorial2-section3-step1-3.png)

右键单击**PressableButtonHoloLens2**对象，然后选择 "**复制**" 以创建其副本：

![mrlearning](images/mrlearning-base/tutorial2-section3-step1-4.png)

**重复**此步骤四次，直到总共有5个 PressableButtonHoloLens2 对象。

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. 添加和配置网格对象集合（脚本）组件

在 "层次结构" 窗口中选择 "ButtonCollection" 对象之后，在 "检查器" 窗口中，单击 "**添加组件**" 按钮，然后搜索并选择 "**网格对象集合**"，将网格对象集合（脚本）组件添加到 ButtonCollection 对象：

![mrlearning](images/mrlearning-base/tutorial2-section3-step2-1.png)

按如下所示配置网格对象集合（脚本）：

* 将**Num 行**更改为1，使所有按钮在一行上对齐
* 将**单元格宽度**改为0.05，使行中的按钮间距

然后单击 "**更新集合**" 按钮应用新配置：

![mrlearning](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> 刚才应用的配置更改表示实现将按钮置于单个行中的目标所需的最小更改。 但是，在将来的项目中，根据各种因素（例如，父对象和子对象的方向），您可能需要调整其他设置，例如，如方向类型。 若要详细了解 MRTK 的网格对象集合，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[对象集合脚本](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)指南。

如果仍在 "层次结构" 窗口中选择 "ButtonCollection" 对象，则在 "检查器" 窗口中，更改 ButtonCollection 对象的转换**位置**，使其子按钮对象位于相机前面，例如 x = 0、y = 0 和 z = 0.5：

![mrlearning](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> 第一次将 PressableButtonHoloLens2 prefab 添加到上面的 "[手写跟踪手势" 和 "种不可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)" 部分时，会将其放在照相机的前方。 但是，因为网格对象集合控制其直接子对象的位置，所以根据网格对象集合与父值0之间的默认距离，PressableButtonHoloLens2 子对象的 Z 位置被重置为0。 这是为了使父/子位置关系保持井然有序，这是因为我们将父 ButtonCollection 对象的位置向前移动，而不是配置从父值到 PressableButtonHoloLens2 子对象的距离。

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. 使用编辑器内模拟测试按钮

按下 "播放" 按钮进入游戏模式，并使用编辑器内输入模拟在新创建的按钮面板中测试每个按钮：

![mrlearning](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> 目前，当您按下任何五个按钮时，多维数据集颜色将变为青色。 若要使体验更有趣，可使用刚刚了解的内容来配置每个按钮，将多维数据集更改为不同的颜色。

## <a name="adding-text-into-your-scene"></a>向场景中添加文本

在本部分中，你将学习如何使用 Unity 的 TextMesh Pro，并在上一教程的 "[导入 TextMesh Pro 基本资源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)" 部分中准备好如何向混合现实体验添加文本。

在此特定示例中，你将在上一节中创建的按钮集合下添加一个简单标签。

右键单击 "ButtonCollection" 对象，然后选择 " **3D object** > **TextMeshPro** ，将 TextMeshPro 对象创建为 ButtonCollection 对象的子对象：

![mrlearning](images/mrlearning-base/tutorial2-section4-step1-1.png)

在新创建的 TextMeshPro 对象（仍处于选定状态）中，在 "检查器" 窗口中更改其位置和大小，以便将标签整齐放置在按钮集合下，例如：

* 将矩形转换位置**Y**改为-0.0425
* 将矩形转换**宽度**更改为0.24
* 将矩形转换**高度**更改为0.024

然后，更新文本以反映标签的内容，并选择字体属性，使文本适合标签，例如：

* 将文本网格 Pro （脚本）**文本**更改为按钮集合
* 将文本网格 Pro （脚本）**字体样式**更改为粗体
* 将文本网格 Pro （脚本）**字号**更改为0。2
* 将文本网格 Pro （脚本）**对齐方式**更改为居中和居中

![mrlearning](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>祝贺你

本教程介绍了如何克隆、自定义和配置 MRTK 配置文件设置。 还了解了如何与按钮交互，以便在 HoloLens 2 上使用跟踪的动手触发器事件。 最后，你已了解如何使用 MRTK 的网格对象集合组件和 Unity 文本网格 Pro 创建简单的 UI 接口。

[下一教程： 4. 放置动态内容并使用 solvers](mrlearning-base-ch3.md)
