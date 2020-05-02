---
title: 入门教程 - 3. 创建用户界面并配置混合现实工具包
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376134"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3.创建用户界面并配置混合现实工具包
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

在前一篇教程中，你已通过启动适用于 HoloLens 2 的第一个应用程序，了解了混合现实工具包 (MRTK) 提供的某些功能。 本教程将会介绍如何创建按钮并在 UI 文本面板中对其进行组织，然后使用默认的交互（触摸）方式来与每个按钮交互。 此外，本课还会探讨如何添加简单的操作和效果，例如更改对象的大小、声音和颜色。 本模块将介绍有关如何修改 MRTK 配置文件的基本概念，首先介绍如何禁用[空间映射](spatial-mapping.md)网格可视化。

## <a name="objectives"></a>目标

* 自定义和配置混合现实工具包配置文件
* 使用 UI 元素和按钮来与全息影像交互
* 基本的手动跟踪输入和交互

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何配置混合现实工具包配置文件（更改空间感知显示选项）
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

本部分介绍如何自定义和配置默认的 MRTK 配置文件。

此特定示例将演示如何通过更改空间网格观察程序的设置来隐藏空间感知网格。 但是，可以按照相同的原则来自定义 MRTK 配置文件中的任何设置或值。

隐藏空间感知网格所要执行的主要步骤如下：

1. 克隆默认的配置配置文件
2. 启用空间感知系统
3. 克隆默认的空间感知系统配置文件
4. 克隆默认的空间感知网格观察程序配置文件
5. 更改空间感知网格的可见性

> [!NOTE]
> 默认情况下，MRTK 配置文件不可编辑。 这是一些默认的配置文件模板，必须先克隆它们，然后才能对其进行编辑。 配置文件有多个嵌套层。 因此，在配置一个或多个设置时，常见的做法是克隆然后编辑多个配置文件。

### <a name="1-clone-the-default-configuration-profile"></a>1.克隆默认的配置配置文件

> [!NOTE]
> 配置配置文件是顶级配置文件。 因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。

在“层次结构”窗口中选择“MixedRealityToolkit”对象后，请在“检查器”窗口中将混合现实工具包“配置配置文件”更改为“DefaultHoloLens2ConfigurationProfile”：   

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

在仍选中了“MixedRealityToolkit”对象的情况下，在“检查器”窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口：  

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

在“克隆配置文件”窗口中，单击“克隆”按钮创建 **DefaultHololens2ConfigurationProfile** 的可编辑副本： 

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

新建的配置配置文件现已分配为场景中的配置配置文件：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

在 Unity 菜单中，选择“文件” > “保存”以保存场景。  

> [!TIP]
> 在学习整篇教程的过程中，请记得保存自己的工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.启用空间感知系统

仍在“层次结构”窗口中选中了“MixedRealityToolkit”对象的情况下，在“检查器”窗口中选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：   

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.克隆默认的空间感知系统配置文件

在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口：  

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

在“克隆配置文件”窗口中，单击“克隆”按钮创建 **DefaultMixedRealitySpatialAwarenessSystemProfile** 的可编辑副本： 

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

新建的空间感知系统配置文件现已自动分配到你的配置配置文件：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.克隆默认的空间感知网格观察程序配置文件

在仍然选中了“空间感知”选项卡的情况下，展开“Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口：   

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

在“克隆配置文件”窗口中，单击“克隆”按钮创建 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可编辑副本： 

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.更改空间感知网格的可见性

在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下保持正常运行：   

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> 尽管空间映射网格不可见，但它依然存在且可正常运行。 例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。

你已了解如何修改 MRTK 配置文件中的设置。 可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。 由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。 若要详细了解 MRTK 配置文件及其体系结构，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[混合现实工具包配置文件配置指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>手动跟踪手势和可交互按钮

本部分介绍如何使用手动跟踪来按下某个按钮并触发事件，以便在按下该按钮时执行某项操作。

此特定示例演示如何在按下按钮时更改立方体的颜色，并在释放按钮时将其更改回原始颜色。 但是，可以按照相同的原则创建其他事件。

更改立方体颜色所要执行的主要步骤如下：

1. 将一个可按按钮预制件添加到场景中
2. 将立方体添加到场景中
3. 配置 InteractableOnPressReceiver 事件类型
4. 将立方体配置为接收 On Press 事件
5. 定义 On Press 事件触发的操作
6. 将立方体配置为接收 On Release 事件
7. 定义 On Release 事件触发的操作
8. 使用编辑器中的模拟功能测试按钮

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1.将一个可按按钮预制件添加到场景中

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">预制件</a>是作为 Unity 资产存储的预配置 GameObject，可在整个项目中重复使用。

在“项目”窗口中，搜索 **PressableButtonHoloLens2** 找到用于本示例的预制件： 

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

在“搜索”结果中，选择“PressableButtonHoloLens2”预制件并将其**拖到**“层次结构”窗口中，以将其添加到场景中：   

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> 若要按下图所示显示场景，请在 "层次结构" 窗口中双击 "PressableButtonHoloLens2" 对象以使其成为焦点，然后使用位于场景窗口右上角的 <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">场景别出心裁</a>，以将查看角度调整为沿正向 Z 轴。

在仍选中了“PressableButtonHoloLens2”对象的情况下，在“检查器”窗口中执行以下操作：  

* 更改此对象的变换**位置**，将其定位在位于原点处的相机的前面，例如，定位到 x = 0，y = 0，z = 0.5

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> 一般情况下，Unity 中的 1 个位置单位大致相当于现实生活中的 1 米。 但也存在例外情况，例如，当对象是缩放对象的子级时。

### <a name="2-add-a-cube-to-the-scene"></a>2.将立方体添加到场景中

在“层次结构”窗口中右键单击某个空白位置，然后选择“3D 对象” > “立方体”将一个立方体添加到场景中：  

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

在仍选中了“Cube”对象的情况下，在“检查器”窗口中执行以下操作：  

* 更改此对象的变换**位置**，将其定位在可按按钮附近，但不要与该按钮重叠，例如，定位到 x = 0，y = 0.04，z = 0.5
* 将其变换**标度**更改为适当的大小，例如 x = 0.02，y = 0.02，z = 0.02

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3.配置 InteractableOnPressReceiver 事件类型

在“层次结构”窗口中选择“PressableButtonHoloLens2”对象，然后在“检查器”窗口的**三横线菜单**中，选择“折叠所有组件”以获取此对象上所有组件的概述：   

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

展开“可交互(脚本)”组件，然后找到并展开“事件” > “接收器”部分：   

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

单击“添加事件”按钮，创建事件接收器类型 **InteractableOnPressReceiver** 的新事件接收器： 

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> 当跟踪手按下按钮时，名为 InteractableOnPressReceiver 的事件接收器类型将允许该按钮响应 pressed 事件。

对于新建的事件接收器，请将“交互筛选器”更改为“近距和远距”：  

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4.将立方体配置为接收 On Press 事件

在“层次结构”窗口中，单击“立方体”并将其**拖放**到“On Press ()”事件的“事件属性”对象字段中，以将 Cube 分配为 On Press () 事件的接收器：   

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5.定义 On Press 事件触发的操作

单击操作下拉列表（当前分配的值为“无函数”），然后选择“MeshRenderer” > “Material 材料”，以设置在触发 On Press () 事件时要更改的立方体材料属性：   

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

单击材料字段（当前填充了“无(材料)”）旁边的小**圆圈**图标，打开“选择材料”窗口： 

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

在“选择材料”窗口中，**搜索** **MRTK_Standard** 并选择合适的材料（例如 **MRTK_Standard_Cyan**），以便在按下按钮时立方体的颜色更改为青色：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6.将立方体配置为接收 On Release 事件

针对 On Release 事件**重复**步骤 4，将 **Cube** 分配为 **On Release ()** 事件的接收器。

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7.定义 On Release 事件触发的操作

针对 On Release 事件**重复**步骤 5，但请选择“MRTK_Standard_LightGray”材料，以便在释放按钮时立方体的颜色恢复为其原始浅灰色： 

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8.使用编辑器中的模拟功能测试按钮

按“播放”按钮进入“游戏”模式，使用编辑器中的输入模拟功能测试新配置的按钮。 

未按下按钮（空格键 + 向后滚动鼠标滚轮）：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

已按下按钮（空格键 + 向前滚动鼠标滚轮）：

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> 若要了解如何使用编辑器中的输入模拟功能，可以参考 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用编辑器中的手写输入模拟来测试场景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>使用 MRTK 的网格对象集合创建按钮面板

本部分介绍如何使用 MRTK 的网格对象集合工具自动对齐多个按钮，使用户界面保持整洁。

此特定示例将演示如何创建一个面板，其中包含五个水平对齐的按钮。 但是，可以按照相同的原则创建其他布局。

若要实现此目的，请执行以下主要步骤：

1. 将按钮对象设为父对象的父级
2. 添加并配置“网格对象集合(脚本)”组件
3. 使用编辑器中的模拟功能测试按钮

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1.将按钮对象设为父对象的父级

在“层次结构”窗口中右键单击某个空白位置，然后选择“创建空对象”： 

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

右键单击新建的对象，然后选择“重命名”并为其指定一个适当的名称，例如 **ButtonCollection**： 

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

选择“PressableButtonHoloLens2”对象，将其**拖放**到“ButtonCollection”对象的顶部，使其成为 ButtonCollection 对象的子级：  

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

右键单击“PressableButtonHoloLens2”对象，然后选择“复制”以创建其副本：  

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

**重复**此步骤四次，直到总共有五个 PressableButtonHoloLens2 对象。

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2.添加并配置“网格对象集合(脚本)”组件

在“层次结构”窗口中选择了 ButtonCollection 对象的情况下，在“检查器”窗口中单击“添加组件”按钮，然后搜索并选择“网格对象集合”，将“网格对象集合(脚本)”组件添加到 ButtonCollection 对象中：  

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

按如下所述配置“网格对象集合(脚本)”：

* 将“行数”更改为 1，使所有按钮在一行中对齐 
* 将“单元格宽度”更改为 0.05，以隔开行中的按钮 

然后单击“更新集合”按钮以应用新配置： 

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> 刚刚应用的配置更改，就是实现在一行中放置所有按钮这一目标最起码需要做出的更改。 但是，在将来的项目中，根据父对象和子对象的方向等因素，你可能需要调整其他设置，例如方向类型。 若要详细了解 MRTK 的网格对象集合，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[对象集合脚本](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)指南。

仍在“层次结构”窗口中选中了 ButtonCollection 对象的情况下，在“检查器”窗口中更改 ButtonCollection 对象的变换**位置**，以将其子按钮对象定位在位于原点处的相机的前面，例如，定位到 x = 0，y = 0，z = 0.5：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> 在前面的[手动跟踪手势和可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)部分中首次将 PressableButtonHoloLens2 预制件添加到场景时，已将其定位在相机的前面。 但是，由于网格对象集合会控制其直属子对象的位置，因此，根据网格对象集合与父级之间的默认距离为 0 这一原则，PressableButtonHoloLens2 子对象的 Z 位置已重置为 0。 正因如此，同时为了在父级/子级之间保持组织有序的位置关系，我们已将父 ButtonCollection 对象的位置前移，而不是通过配置与父级之间的距离值将 PressableButtonHoloLens2 子对象前移。

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3.使用编辑器中的模拟功能测试按钮

按下“播放”按钮进入“游戏”模式，使用编辑器中的输入模拟功能在新建的按钮面板中测试每个按钮：

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> 目前，在按下五个按钮中的任何一个时，立方体颜色将变为青色。 为使体验更有趣，可以运用刚刚学到的知识配置每个按钮，以将立方体更改为不同的颜色。

## <a name="adding-text-into-your-scene"></a>将文本添加到场景中

本部分介绍如何使用 Unity 的 TextMesh Pro 将文本添加到混合现实体验，这些文本是在上一篇教程的[导入 TextMesh Pro 基本资源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)部分中准备的。

在此特定示例中，你将在上一部分创建的按钮集合下面添加一个简单的标签。

右键单击“ButtonCollection”对象，然后选择“3D 对象” > “文本 - TextMeshPro”，以创建一个 TextMeshPro 对象作为 ButtonCollection 对象的子级：  

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

在仍选中了名为 Text (TMP) 的新建 TextMeshPro 对象的情况下，在“检查器”窗口中更改其位置和大小，以将标签整齐放置在按钮集合下面，例如：

* 将矩形变换的“位置 Y”更改为 -0.0425 
* 将矩形变换的“宽度”更改为 0.24 
* 将矩形变换的“高度”更改为 0.024 

然后更新文本以反映标签的用途，并选择字体属性，使文本可以放入标签，例如：

* 将 Text Mesh Pro (Script) 的“文本”更改为“按钮集合” 
* 将 Text Mesh Pro (Script) 的“字体样式”更改为“粗体” 
* 将 Text Mesh Pro (Script) 的“字体大小”更改为 0.2 
* 将 Text Mesh Pro (Script) 的“对齐方式”更改为“居中” 

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>祝贺

本教程已介绍如何克隆、自定义和配置 MRTK 配置文件设置。 此外，还介绍了如何在 HoloLens 2 中使用跟踪手来与触发事件的按钮交互。 最后，介绍了如何使用 MRTK 的“网格对象集合”组件和 Unity 的 Text Mesh Pro 创建一个简单的 UI。

[下一教程：4.放置动态内容并使用求解器](mrlearning-base-ch3.md)
