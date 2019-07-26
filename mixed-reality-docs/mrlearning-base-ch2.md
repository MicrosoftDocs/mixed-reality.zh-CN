---
title: MR 学习基础模块 - 用户界面、手跟踪和混合现实工具包配置
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 6257b5a4b42127a7f15b235dbdd6b44967684fcb
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485747"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3.创建用户界面并配置混合现实工具包 

在上一课中, 您已了解到混合现实工具包 (MRTK) 通过启动适用于 HoloLens 2 的第一个应用程序而必须提供的一些功能。 在下一课中, 您将学习如何创建和组织按钮以及 UI 文本面板, 并使用默认交互 (触摸) 与每个按钮进行交互。 此外，本课还会探讨如何添加简单的操作和效果，例如更改对象的大小、声音和颜色。 此模块将介绍有关修改 MRTK 配置文件的基本概念, 从关闭空间网格可视化效果开始。 

## <a name="objectives"></a>目标

* 自定义和配置混合现实工具包配置文件
* 使用 UI 元素和按钮与全息影像交互
* 基本的手动跟踪输入和交互

## <a name="instructions"></a>说明

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何配置混合现实工具包配置文件（更改空间感知显示选项）
在本部分中, 你将了解如何通过调整空间感知网格的显示选项来自定义和配置默认的 MRTK 配置文件。 调整 MRTK 配置文件中的任何设置或值时，也可以遵循这些原则。

1. 从 "BaseScene" 层次结构中选择混合现实工具包 (MRTK)。 在 "检查器" 面板中, 查找混合现实工具包脚本并选择活动配置文件, 如下图所示。 双击该配置文件将其打开。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>注意:默认情况下，MRTK 配置文件不可编辑。 这些是可以复制和自定义的默认配置文件模板。 自定义项和配置文件有多个层。 因此, 在配置一个或多个设置时, 可以复制和自定义多个配置文件。
>
>若要了解有关 MRTK 配置文件及其体系结构的详细信息, 请访问[MRTK 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)。

2. 创建默认配置文件的副本以对其进行自定义。 若要复制默认配置文件, 请单击 "复制 & 自定义 (请参阅映像)。 随即会创建 MRTK 配置文件的副本。 现在，可以使用自己的 MRTK 配置文件副本，自定义此配置文件中的任何设置。 还需要对此配置文件下嵌套的任何其他配置文件重复执行复制和自定义步骤, 如后续步骤中所述。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 禁用空间感知网格的可见性。 为此, 请查找空间感知系统设置, 如图所示。 单击空间感知系统配置文件右侧的 "克隆" 按钮, 以使用可自定义的副本替换默认配置文件。 如果弹出窗口出现, 请按下的 "克隆" 按钮, 如下图所示。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 创建默认混合现实空间网格观察者的自定义副本。 单击 "Windows Mixed Reality 空间网格观察器" 旁的向下箭头以查看其他选项。 在这些选项中, 你将看到处于灰色显示状态的默认混合现实空间网格观察程序 (不可编辑)。 必须将此默认配置文件替换为可自定义的副本，以便能够对其进行编辑。 单击右侧的按钮 (由绿色箭头标记) 以克隆副本。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 接下来，调整带有“遮挡”字样的显示选项的设置。 这会使空间网格不可见, 但仍会隐藏空间网格后面的游戏对象 (也称为封闭)。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>注意:尽管空间映射网格不可见，但它依然存在，且可与其交互。 空间映射网格后面的任何全息影像 (如可见墙后的全息图) 都不可见, 这是因为封闭设置。

祝贺你！ 你已了解如何修改 MRTK 配置文件中的设置。 你知道，若要修改 MRTK 设置，需要创建默认配置文件的副本，以便能够对其进行编辑。 如果你想要使用新设置创建配置文件, 或者可以返回到默认配置文件, 则始终拥有默认的配置文件, 这是不可编辑的。 可以调整大量的设置。 有关 MRTK 配置文件设置的完整参考，请参阅 MRTK 文档： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>手动跟踪手势和可交互按钮
在本部分中, 你将学习如何使用手动跟踪来按 pressable 按钮。

1. 从 "项目" 文件夹中选择 "资产"。

2. 在搜索栏中键入“pressablebutton”。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. 将名为“PressableButton”的预制件（以蓝框表示）拖入层次结构。 

   > 注意:如果收到有关 "导入 TMP Essentials" 的消息, 请立即导入它。 如果你的项目中尚不包含 TMP Essentials, 则在导入 TMP Essentials 后可能需要重复此步骤, 否则可能不会出现按钮文本。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 双击 "PressableButton" 游戏对象 (现在应在 BaseScene 层次结构中), 以便在场景中查看该对象, 如下图所示。 您的按钮图形可能会与下面的图像不同。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. 在 "检查器" 面板中, 单击 "添加事件", 为按钮指定在推送时响应的事件。 在出现的选项中, 选择下拉菜单, 然后选择 "InteractableOnPressReciever"。 这样，在跟踪手按下该按钮时，该按钮会响应按键事件。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. 将立方体添加到场景。 右键单击 "层次结构" 区域, 选择一个3D 对象, 然后单击 "多维数据集"。 现在，你的显示画面中应会包含一个立方体。 它会显得非常大。 您可以调整坐标 (在层次结构区域中仍选择 Cube 时) 以减小大小。 将坐标值设置为 x = 0.1，y = 0.1，z = 0.1。 请务必在场景中将该立方体定位在靠近可按按钮的位置，但不要与该按钮重叠。 在下图中，立方体的位置为 x = 0，y = 0.2，z = 1。 

   > 注意:一般情况下，Unity 中的 1 个单位大致相当于现实生活中的 1 米。 但也存在例外情况，例如，当对象是缩放对象的子级时。
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. 此步骤将立方体设置为在按下按钮时改变颜色。 在 "BaseScene" 菜单中选择 "PressableButton"。 从检查器面板的 "选择事件类型" 框下, 单击 "+" 按钮。 将多维数据集从 BaseScene 菜单拖动到 "仅运行时" 框中, 如下图所示

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

单击未显示函数的下拉列表。 选择 "MeshRenderer", 然后选择 "材料材料"。 这允许您在按下按钮时更改材料。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

转到 "项目" 面板, 搜索要将其更改为的材料。 在此示例中, 您将使用材料 MRTK_Standard_Cyan, 通过在 "项目" 选项卡的搜索栏中键入 "青色" 来找到。 (MRTK 包括许多要从中进行选择的材料和颜色。)将材料拖到 MeshRenderer 下面的框中。 可以在“资产”>“MixedRealityToolkit.SDK”>“标准资产”>“材料”中找到 MRTK 材料。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

现已设置事件。按下按钮时，立方体会根据指定的材料改变颜色。 在本示例中，立方体将更改为青色。

8. 接下来要设置释放操作，以便在释放按钮时，按钮会恢复其默认颜色。 重复上面的步骤7。 但这一次, OnRelease 事件而不是 OnPress 事件, 如下图所示。

9.  在 "项目" 面板中, 搜索要在按钮发布时默认为的多维数据集的材料。 在此示例中, 我们选择了 MRTK_Standard_LightGray。 将材料拖到 "MeshRenderer" 字段下面的框中。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

现在, 当按钮被按下时, 它将更改为新的颜色蓝绿色。 按钮释放后, 它会改回您指定的默认颜色 (例如浅灰色)。按屏幕顶部的 "播放" 按钮在编辑器中试用, 或将其部署到 HoloLens 2 进行测试。 若要了解有关编辑器内模拟的详细信息 (包括手动模拟), 请阅读[MRTK 的模拟文档页](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>使用 MRTK 的网格对象集合创建按钮面板

在本部分中, 你将了解如何使用 MRTK 的 GridObjectCollection 工具自动将多个按钮对齐到巧妙的用户界面。

1. 复制前一部分中的按钮, 直到有五个按钮。 可通过多种方式进行复制：
- 右键单击该按钮, 然后单击 "复制"。 然后, 在按钮下向下并再次右键单击, 然后单击 "粘贴"。 
- 右键单击该按钮, 然后单击 "复制"。 
- 通过单击该多维数据集, 然后在键盘上按 Ctrl D 来使用键盘命令。

重复此操作, 直到有五个按钮;请参阅下图中的五个红色箭头。

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 将按钮分组到空的父游戏对象下。 为了使网格集合中的按钮, 需要将按钮分组到公共父对象下。 右键单击 hiearachy, 然后单击 "创建空"。 随后会创建一个新的空游戏对象用于放置所有按钮。 它显示为 "gameObject"。 右键单击并将其重命名为 ButtonCollection。

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 将所有按钮移入新集合， 为此, 请选择层次结构中的所有五个按钮对象, 并将其全部拖动到 ButtonCollection 游戏对象下, 如下图所示。 提示: 按住 Ctrl 键的同时选择项, 选择多个项。

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. 将 MRTK 的网格对象集合组件添加到按钮集合。 为此, 请选择 "ButtonCollection" 父对象。 从检查器面板中, 单击 "添加组件" 按钮。 在搜索栏中搜索 "网格对象集合", 并在列表中显示它时将其选中。

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

网格对象集合组件允许您在巧妙的行、列或网格中组织按钮或任何一组对象。 这是 MRTK 提供的构建基块之一, 为你提供了一种快速简单的方法来创建具有吸引力的用户界面。

5. 配置网格对象集合。 若要确保所有按钮都面向用户, 请选择 "方向类型"。 然后选择 "正面朝上", 如下图所示。 接下来，更改单元格大小以设置按钮之间的间距。 对于单元宽度和单元高度, 从0.12 个单位开始, 按0.12 单位, 如下图所示。 可能需要根据所选的对象和按钮资产调整这些值。 确保 Rows 设置为1。 单击 "更新集合"。 场景将如下图所示。 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>注意:根据子对象或父对象的方向，在将来的项目中可能需要以不同的方式调整方向设置。 此外，根据集合中对象的大小，可能需要以不同的方式定义“单元格宽度”和“单元格高度”字段。

### <a name="adding-text-into-your-scene"></a>将文本添加到场景中

本部分介绍如何将文本添加到混合现实体验以及如何编辑文本。 遵照[此处](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)的说明，确保已在 Unity 中启用 TextMeshPro（如果尚未启用）。

1. 选择 ButtonCollection 父对象, 并右键单击该集合。 展开下拉菜单中的 "3D 对象"。 然后选择 "TextMeshPro"。 你应在按钮集合下看到一个 TextMeshPro 对象, 如下图所示。

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. 若要改善可读性的文本大小和位置, 请调整 TextMeshPro 组件中的 "字体大小" 字段以更改字体大小。 还需要调整矩形转换位置和缩放比例, 如下图所示。 请参阅下面的图像获取用于文本配置的值。 您可以使用这些值作为开始点, 进一步提高文本字段的大小和位置。

![第2课 Chapter4 步骤3](images/Lesson2_Chapter4_Step3.JPG)

3. 在 "检查器" 面板中的 TextMeshPro 组件的文本字段中, 如下所示。 键入 "按钮集合文本"。 该文本显示在场景中, 但会隐藏在按钮和/或大小错误之后。

![第2课 Chapter4 步骤 2](images/Lesson2_Chapter4_Step2.JPG)
![第2课 Chapter4 步骤4](images/Lesson2_Chapter4_Step4.JPG)

4. 若要修改按钮对象的文本值, 请单击任何按钮旁边的箭头将其展开, 然后导航到 SeeItSayItLabel 对象。 导航到 TextMeshPro, 你可以在其中编辑按钮的文本, 如以上步骤中所述。

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>祝贺
在本课中，你已了解如何复制、自定义和配置 MRTK 配置文件设置（即，空间感知网格的可见性）。此外，你已了解如何在 HoloLens 2 中使用跟踪手来与触发事件的按钮交互。 最后，你已了解如何使用 Unity 的 Text Mesh Pro 和 MRTK 的“网格对象集合”组件创建一个简单的 UI。

[下一课：4.放置动态内容并使用求解器](mrlearning-base-ch3.md)

