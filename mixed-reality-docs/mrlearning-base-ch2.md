---
title: MR 学习基础模块 - 用户界面、手跟踪和混合现实工具包配置
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730944"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR 学习基础模块 - 用户界面、手跟踪和混合现实工具包配置

在上一课中，你已通过启动适用于 HoloLens 2 的第一个应用程序，了解了 MRTK 提供的某些功能。 本课将会介绍如何创建按钮并在 UI 文本面板中对其进行组织，然后使用默认的交互（触摸）方式来与每个按钮交互。 此外，本课还会探讨如何添加简单的操作和效果，例如更改对象的大小、声音和颜色。 本模块将会介绍有关如何修改 MRTK 配置文件的基本概念，并从禁用空间网格的可视化开始介绍。 

## <a name="objectives"></a>目标

* 自定义和配置混合现实工具包配置文件
* 使用 UI 元素和按钮来与全息影像交互
* 基本的手动跟踪输入和交互

## <a name="instructions"></a>说明

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何配置混合现实工具包配置文件（更改空间感知显示选项）
本部分将介绍如何通过调整空间感知网格的显示选项，来自定义和配置默认的混合现实工具包配置文件。 调整 MRTK 配置文件中的任何设置或值时，也可以遵循这些原则。

1. 从“BaseScene”层次结构中选择“混合现实工具包(MRTK)”。 在检查器面板中，找到“混合现实工具包脚本”并选择“活动的配置文件”，如下图所示。 双击该配置文件将其打开。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>注意：默认情况下，MRTK 配置文件不可编辑。 这是一些可以从中进行复制和自定义的默认配置文件模板。 有多个自定义和配置文件层，因此，标准的做法是，在配置一个或多个设置时复制并自定义多个配置文件。
>
>若要详细了解 MRTK 配置文件及其体系结构，请访问 [MRTK 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)。

2. 创建默认配置文件的副本以对其进行自定义。 若要复制默认的配置文件，请单击“复制和自定义”按钮（参考插图）。 随即会创建 MRTK 配置文件的副本。 现在，可以使用自己的 MRTK 配置文件副本，自定义此配置文件中的任何设置。 对于嵌套在此配置文件下的任何其他配置文件，也需要根据后续步骤中所述，重复复制/自定义步骤。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 禁用空间感知网格的可见性。 为此，请找到“空间感知系统设置”，如图所示。 单击“空间感知系统配置文件”右侧的“克隆”按钮，将默认配置文件替换为可自定义的副本。 如果出现了弹出窗口，请按“克隆”按钮，如下面的第二张插图中所示。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 创建默认混合现实空间网格观察者的自定义副本。 单击“Windows 混合现实空间网格观察者”旁边的向下箭头以查看其他选项。 在这些选项中，可以看到“默认混合现实空间网格观察者”已灰显（不可编辑）。 必须将此默认配置文件替换为可自定义的副本，以便能够对其进行编辑。 单击右侧的按钮（标有绿色箭头）以克隆副本。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 接下来，调整带有“遮挡”字样的显示选项的设置。 此设置会使空间网格不可见，但仍会隐藏空间网格后面的游戏对象（称为遮挡）。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>注意：尽管空间映射网格不可见，但它依然存在，且可与其交互。 由于使用了遮挡设置，空间映射网格后面的所有全息影像（例如可见墙壁后面的全息影像）将不可见。

祝贺你！ 你已了解如何修改 MRTK 配置文件中的设置。 你知道，若要修改 MRTK 设置，需要创建默认配置文件的副本，以便能够对其进行编辑。 想要使用新的设置创建配置文件，或重新引用默认的配置文件时，你始终有留底的默认配置文件（不可编辑）。 可以调整大量的设置。 有关 MRTK 配置文件设置的完整参考，请参阅 MRTK 文档： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>手动跟踪手势和可交互按钮
本部分介绍如何使用手动跟踪来按下某个可交互的按钮。

1. 从“项目”文件夹中选择“资产”。

2. 在搜索栏中键入“pressablebutton”。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. 将名为“PressableButton”的预制件（以蓝框表示）拖入层次结构。 

   > 注意：如果出现了有关“导入 TMP Essentials”的消息，现在请导入 TMP Essentials。 如果 TMP Essentials 尚未包含在项目中，则导入 TMP Essentials 后你可能需要重复此步骤，否则按钮文本可能不显示。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 双击“PressableButton”游戏对象（它现在应在 BaseScene 层次结构中）以在场景中查看它，如图所示（显示的按钮图形可能与下图不同）。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. 在检查器面板中单击“添加事件”，以在按钮中添加一个事件，按下该按钮时会响应该事件。 在显示的选项中，选择下拉菜单。 选择“InteractableOnPressReciever”。 这样，在跟踪手按下该按钮时，该按钮会响应按键事件。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. 将立方体添加到场景。 右键单击层次结构区域，选择 3D 对象，然后单击“立方体”。 现在，你的显示画面中应会包含一个立方体。 该立方体看上去很大，因此，请（在仍已在层次结构区域中选择“立方体”的情况下）调整其坐标，以减小其大小。 将坐标值设置为 x = 0.1，y = 0.1，z = 0.1。 请务必在场景中将该立方体定位在靠近可按按钮的位置，但不要与该按钮重叠。 在下图中，立方体的位置为 x = 0，y = 0.2，z = 1。 

   > 注意：一般情况下，Unity 中的 1 个单位大致相当于现实生活中的 1 米。 但也存在例外情况，例如，当对象是缩放对象的子级时。
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. 此步骤将立方体设置为在按下按钮时改变颜色。 在“BaseScene”菜单中选择“PressableButton”。 在检查器面板中的“选择事件类型”框下，单击“+”按钮。 将“立方体”从“BaseScene”菜单拖入“仅限运行时”框，如下图所示

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

单击带有“无函数”字样的下拉列表。 依次选择“MeshRenderer”、“材料 <材料>”。 这样，就可以在按下按钮时更改材料。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

转到项目面板，搜索要更改到的材料。 本示例将使用材料“MRTK_Standard_Cyan”，在项目选项卡的搜索栏中键入“cyan”即可找到它（MRTK 包括许多可供选择的材料和颜色）。将该材料拖到“MeshRenderer.material”下面的框中。 可以在“资产”>“MixedRealityToolkit.SDK”>“标准资产”>“材料”中找到 MRTK 材料。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

现已设置事件。按下按钮时，立方体会根据指定的材料改变颜色。 在本示例中，立方体将更改为青色。

8. 接下来要设置释放操作，以便在释放按钮时，按钮会恢复其默认颜色。 重复上述步骤 7，但这次请使用“OnRelease”事件而不是“OnPress”事件，如下图所示。

9.  在项目面板中，搜索一个可以在释放按钮时让立方体恢复默认颜色的材料（在本例中，我们选择了“MRTK_Standard_LightGray”）。将该材料拖到“MeshRenderer.material”字段下面的框中。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

现在，在按下按钮时，它应会更改为新颜色（例如青色）；释放按钮时，它应会恢复指定的默认颜色（例如浅灰色）。按屏幕顶部的“播放”按钮，以在编辑器中尝试这种变换，或者将项目部署到 HoloLens 2 进行测试！ 若要详细了解编辑器内部的模拟，包括手部模拟，请阅读 [MRTK 的模拟文档页](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>使用 MRTK 的网格对象集合创建按钮面板

本部分介绍如何使用 MRTK 的 GridObjectCollection 工具将多个按钮自动对齐到一个整洁的用户界面。

1. 复制上一部分创建的按钮，直到有了 5 个按钮。 可通过多种方式进行复制：
- 右键单击该按钮并单击“复制”，然后在该按钮的下方再次右键单击，并单击“粘贴”。 
- 右键单击该按钮并单击“复制”。 
- 使用键盘命令：单击立方体并按键盘上的“Ctrl+D”。

重复此步骤，直到总共有了 5 个按钮（参考下图中 5 个红色箭头）。

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 将按钮分组到空的父游戏对象下。 若要在网格集合中添加按钮，需要将按钮分组到公用父对象下。 右键单击层次结构，然后单击“创建空对象”。 随后会创建一个新的空游戏对象用于放置所有按钮。 此对象显示为“gameObject”。 右键单击，然后将它重命名为“ButtonCollection”。

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 将所有按钮移入新集合， 方法是选择层次结构中的所有五个按钮对象，然后将其全部拖放到“ButtonCollection”游戏对象下面，如下图所示。 提示：若要选择多个项，可以按住 Ctrl 键并选择项。

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. 将 MRTK 的“网格对象集合”组件添加到按钮集合中。  为此，请选择“ButtonCollection”父对象，并在检查器面板中单击“添加组件”按钮。 然后在搜索栏中搜索“网格对象集合”，当其显示在列表中时，请将其选中。

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

使用“网格对象集合”组件可以在整洁的行、列或网格中组织按钮或任何对象集。 这是 MRTK 提供的构建基块之一，可让你快速方便地创建美观的用户界面。

5. 配置网格对象集合。 为了确保所有按钮朝向用户，请选择“定位类型”，然后选择“朝向父级的正面”（如下图所示）。接下来，更改单元格大小以设置按钮之间的间距。 对于“单元格宽度”和“单元格高度”，最初请使用 0.12 x 0.12 个单位，如下图所示。 根据所选的对象/按钮资产，可能需要调整这些值。 请确保“行”设置为 1。 然后单击“更新集合”。场景应如下图所示。 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>注意：根据子对象或父对象的方向，在将来的项目中可能需要以不同的方式调整方向设置。 此外，根据集合中对象的大小，可能需要以不同的方式定义“单元格宽度”和“单元格高度”字段。

### <a name="adding-text-into-your-scene"></a>将文本添加到场景中

本部分介绍如何将文本添加到混合现实体验以及如何编辑文本。 遵照[此处](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)的说明，确保已在 Unity 中启用 TextMeshPro（如果尚未启用）。

1. 选择“ButtonCollection”父对象并右键单击集合。 在下拉菜单中展开“3D 对象”，然后选择“TextMeshPro-Text”。 按钮集合下面应会显示一个 TextMeshPro 对象，如下图所示。

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. 在 TextMeshPro 组件的“文本”字段（位于检查器面板中，如下所示）中，键入“按钮集合文本”。 该文本将显示在场景中，但会隐藏在按钮和/或错误大小的对象下面。

![Lesson2 Chapter4 Step2](images/Lesson2_Chapter4_Step2.JPG)

3. 若要改善文本大小和位置以提高可读性，请调整 TextMeshPro 组件中的“字体大小”字段，以更改字体大小。 还需要如下图所示调整“矩形变换”位置和坐标。 参考下图了解用于文本配置的值，并随意使用这些值作为起点，来进一步改善文本字段的大小和位置。

![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)

5. 若要修改按钮对象上的文本值，请单击任一按钮旁边的箭头展开该按钮，导航到“SeeItSayItLabel”对象，然后导航到“TextMeshPro”，在其中可根据上述步骤中所述编辑按钮中的文本。

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>祝贺
在本课中，你已了解如何复制、自定义和配置 MRTK 配置文件设置（即，空间感知网格的可见性）。此外，你已了解如何在 HoloLens 2 中使用跟踪手来与触发事件的按钮交互。 最后，你已了解如何使用 Unity 的 Text Mesh Pro 和 MRTK 的“网格对象集合”组件创建一个简单的 UI。

[下一课：动态内容放置和求解器](mrlearning-base-ch3.md)

