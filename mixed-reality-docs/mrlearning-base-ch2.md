---
title: 入门教程-3。 创建用户界面并配置混合现实工具包
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 0595010a0b443d88e3f208b785903e3f6cc99295
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926532"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. 创建用户界面并配置混合现实工具包

在上一课中，您已了解到混合现实工具包（MRTK）通过启动适用于 HoloLens 2 的第一个应用程序而必须提供的一些功能。 在下一课中，您将学习如何创建和组织按钮以及 UI 文本面板，并使用默认交互（触摸）与每个按钮进行交互。 此外，本课还会探讨如何添加简单的操作和效果，例如更改对象的大小、声音和颜色。 此模块将介绍有关修改 MRTK 配置文件的基本概念，从关闭[空间映射](spatial-mapping.md)网格可视化效果开始。

## <a name="objectives"></a>目标

* 自定义和配置混合现实工具包配置文件
* 使用 UI 元素和按钮与全息影像交互
* 基本的手动跟踪输入和交互

## <a name="instructions"></a>说明

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何配置混合现实工具包配置文件（更改空间感知显示选项）

在本部分中，你将了解如何通过调整空间感知网格的显示选项来自定义和配置默认的 MRTK 配置文件。 调整 MRTK 配置文件中的任何设置或值时，也可以遵循这些原则。

1. 从 "BaseScene" 层次结构中选择混合现实工具包（MRTK）。 在 "检查器" 面板中，查找混合现实工具包脚本并选择活动配置文件，如下图所示。 双击该配置文件将其打开。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step1.png)

    >[!NOTE]
    >默认情况下，MRTK 配置文件不可编辑。 这些是可以复制和自定义的默认配置文件模板。 自定义项和配置文件有多个层。 因此，在配置一个或多个设置时，可以复制和自定义多个配置文件。
    >
    >若要了解有关 MRTK 配置文件及其体系结构的详细信息，请访问[MRTK 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>)。

2. 创建默认配置文件的副本以对其进行自定义。 首先，单击 "**复制 & 自定义**"。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2a.png)

    这会打开*克隆配置文件*的弹出窗口。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2b.png)

    单击 "**克隆**" 创建 MRTK 配置文件的副本。 现在，可以使用自己的 MRTK 配置文件副本，自定义此配置文件中的任何设置。 还需要对此配置文件下嵌套的任何其他配置文件重复执行复制和自定义步骤，如后续步骤中所述。

3. 禁用空间感知网格的可见性。 为此，请查找空间感知系统设置，如下图所示。 请确保已选中 "**启用空间感知系统**" 选项。 单击空间感知系统配置文件右侧的 "**克隆**" 按钮，以使用可自定义的副本替换默认配置文件。 在出现的弹出窗口中，按下的 "**克隆**" 按钮，如下图所示。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3a.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3b.png)

4. 创建默认混合现实空间网格观察者的自定义副本。 单击 "Windows Mixed Reality 空间网格观察器" 旁的向下箭头以查看其他选项。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4a.png)

    在这些选项中，你将看到处于灰色显示状态的默认混合现实空间网格观察程序（不可编辑）。 必须将此默认配置文件替换为可自定义的副本，以便能够对其进行编辑。 如前文所述，单击 "**克隆**" 按钮，然后在出现的弹出窗口中，按下的 "**克隆**" 按钮，如下图所示。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4b.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4c.png)

5. 接下来，调整带有“遮挡”字样的显示选项的设置。 这会使空间映射网格不可见，但仍会隐藏空间映射网格后面的游戏对象（也称为封闭）。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step5.png)

    >[!NOTE]
    >注意：虽然空间映射网格不可见，但仍存在，你可以与之进行交互。 空间映射网格后面的任何全息影像（如可见墙后的全息图）都不可见，这是因为封闭设置。

恭喜你！ 你已了解如何修改 MRTK 配置文件中的设置。 你知道，若要修改 MRTK 设置，需要创建默认配置文件的副本，以便能够对其进行编辑。 如果你想要使用新设置创建配置文件，或者可以返回到默认配置文件，则始终拥有默认的配置文件，这是不可编辑的。 可以调整大量的设置。 有关 MRTK 配置文件设置的完整引用，请参阅此处的 MRTK 文档： [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>手动跟踪手势和可交互按钮

在本部分中，你将学习如何使用手动跟踪来按 pressable 按钮。

1. 从 "项目" 文件夹中选择 "资产"。

2. 在搜索栏中键入 "PressableButtonHoloLens2"。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step2.png)

3. 将名为 "PressableButtonHoloLens2" 的 prefab （由蓝色框表示）拖到层次结构中，并将位置值设置为 x = 0、y = 0 和 z = 0.2，使该按钮位于相机的前方。 （相机定位于原点）。

    >[!NOTE]
    >如果收到有关 "导入 TMP Essentials" 的消息，请立即导入它。 如果你的项目中尚不包含 TMP Essentials，则在导入 TMP Essentials 后可能需要重复此步骤，否则可能不会出现按钮文本。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step3.png)

4. 将立方体添加到场景。 右键单击 "层次结构" 区域，选择一个3D 对象，然后单击 "多维数据集"。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6a.png)

    现在，你的显示画面中应会包含一个立方体。 它会显得非常大。 您可以调整坐标（在层次结构区域中仍选择 Cube 时）以减小大小。 将刻度值设置为 x = 0.02，y = 0.02，z = 0.02。 请确保将多维数据集放在按钮附近，而不是与其重叠。 在下图中，多维数据集的位置为 x = 0、y = 0.4，z = 0.2。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6b.png)

    >[!NOTE]
    >一般情况下，Unity 中的 1 个单位大致相当于现实生活中的 1 米。 但也存在例外情况，例如，当对象是缩放对象的子级时。

5. 选中 "PressableButtonHoloLens2" 游戏对象后，在检查器中向下滚动，找到 "种不可交互" （脚本）组件的 "事件" 部分。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step4.png)

6. 我们将修改现有事件，以便在推送时为按钮指定响应事件。 如您所见，事件接收器类型设置为 InteractableOnPressReceiver。 这样，在跟踪手按下该按钮时，该按钮会响应按键事件。 此时，您还应将交互筛选器更改为 "近到远处"。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step5.png)

7. 此步骤将立方体设置为在按下按钮时改变颜色。 选择 "BaseScene" 层次结构中的 "PressableButtonHoloLens2"，并将 "多维数据集游戏" 对象从 BaseScene 层次结构拖到 "仅运行时" 字段，如下图所示。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7a.png)

    单击未显示函数的下拉列表。 选择 "MeshRenderer"，然后选择 "材料材料"。 这允许您在按下按钮时更改材料。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7b.png)

    单击 "空白材料" 字段旁边的圆圈，打开 "选择材料" 弹出窗口。 MRTK 包括许多要从中进行选择的材料和颜色。 在此示例中，您将使用通过在 popup 搜索栏中键入 "MRTK_Standard" 找到的材料 MRTK_Standard_Cyan。 选择要填充材料字段的 MRTK_Standard_Cyan 材料。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7c.png)

    现已设置事件。按下按钮时，立方体会根据指定的材料改变颜色。 在本示例中，立方体将更改为青色。

8. 接下来要设置释放操作，以便在释放按钮时，按钮会恢复其默认颜色。 重复上面的步骤7。 但这一次，OnRelease 事件而不是 OnPress MRTK_Standard_LightGray 材料，如下图所示。

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step8.png)

    现在，当按钮被按下时，它将更改为新的颜色蓝绿色。 按钮释放后，它会改回您指定的默认颜色（例如浅灰色）。按屏幕顶部的 "播放" 按钮在编辑器中试用，或将其部署到 HoloLens 2 进行测试。 若要了解有关编辑器内模拟的详细信息（包括手动模拟），请阅读[MRTK 的模拟文档页](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>使用 MRTK 的网格对象集合创建按钮面板

在本部分中，你将了解如何使用 MRTK 的 GridObjectCollection 工具自动将多个按钮对齐到巧妙的用户界面。

1. 复制前一部分中的按钮，直到有五个按钮。 可以通过多种方法执行此操作：-右键单击按钮，然后单击 "复制"。 然后，在按钮下向下并再次右键单击，然后单击 "粘贴"。
    -右键单击按钮，然后单击 "复制"。
    -通过单击多维数据集，然后在键盘上按 Ctrl D 来使用键盘命令。

    重复此操作，直到有五个按钮;请参阅下图中的五个红色箭头。

    ![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 将按钮分组到空的父游戏对象下。 为了使网格集合中的按钮，需要将按钮分组到公共父对象下。 右键单击 hiearachy，然后单击 "创建空"。 随后会创建一个新的空游戏对象用于放置所有按钮。 它显示为 "gameObject"。 右键单击并将其重命名为 ButtonCollection。

    ![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 将所有按钮移入新集合， 为此，请选择层次结构中的所有五个按钮对象，并将其全部拖动到 ButtonCollection 游戏对象下，如下图所示。 提示：按住 Ctrl 键的同时选择项，选择多个项。

    ![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. 将 MRTK 的网格对象集合组件添加到按钮集合。 为此，请选择 "ButtonCollection" 父对象。 从检查器面板中，单击 "添加组件" 按钮。 在搜索栏中搜索 "网格对象集合"，并在列表中显示它时将其选中。

    ![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3-step4.png)

    网格对象集合组件允许您在巧妙的行、列或网格中组织按钮或任何一组对象。 这是 MRTK 提供的构建基块之一，为你提供了一种快速简单的方法来创建具有吸引力的用户界面。

5. 配置网格对象集合。 若要确保所有按钮都面向用户，请选择 "方向类型"。 然后选择 "正面朝上"，如下图所示。 接下来，更改单元格大小以设置按钮之间的间距。 对于单元宽度和单元高度，从0.05 个单位开始，按0.05 单位，如下图所示。 请确保 "距离" 设置为0，"行" 设置为1。 单击 "更新集合"。 场景将如下图所示。

    ![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3-step5.png)

    >[!NOTE]
    >根据子对象或父对象的方向，在将来的项目中可能需要以不同的方式调整方向设置。 此外，根据集合中对象的大小，可能需要以不同的方式定义“单元格宽度”和“单元格高度”字段。

### <a name="adding-text-into-your-scene"></a>将文本添加到场景中

本部分介绍如何将文本添加到混合现实体验以及如何编辑文本。 遵照[此处](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)的说明，确保已在 Unity 中启用 TextMeshPro（如果尚未启用）。

1. 选择 ButtonCollection 父对象，并右键单击该集合。 展开下拉菜单中的 "3D 对象"。 然后选择 "TextMeshPro"。 你应在按钮集合下看到一个 TextMeshPro 对象，如下图所示。

    ![第2课 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![第2课 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. 若要改善可读性的文本大小和位置，请调整 TextMeshPro 组件中的 "字体大小" 字段以更改字体大小。 还需要调整矩形转换位置和缩放比例，如下图所示。 请参阅下面的图像获取用于文本配置的值。 您可以使用这些值作为开始点，进一步提高文本字段的大小和位置。

    ![第2课 Chapter4 步骤3](images/mrlearning-base-ch2-4-step3.png)

3. 在 "检查器" 面板的 "TextMeshPro" 组件的 "文本" 字段中，键入 "Button Collection Text"，并将对齐属性调整为居中和顶端，如下图所示。

    ![第2课 Chapter4 步骤4](images/mrlearning-base-ch2-4-step4.png)

4. 若要修改按钮对象的文本值，请单击任何按钮旁边的箭头将其展开，然后导航到 SeeItSayItLabel 对象。 导航到 TextMeshPro，你可以在其中编辑按钮的文本，如以上步骤中所述。

    ![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>祝贺

在本课中，您学习了如何复制、自定义和配置 MRTK 配置文件设置（例如，空间感知网格可见性）。还了解了如何与按钮交互，以便在 HoloLens 2 上使用跟踪的手触发事件。 最后，你已学习了如何使用 Unity 文本网格专业版和 MRTK 的网格对象集合组件创建简单的 UI 接口。

[下一课： 4. 放置动态内容并使用 solvers](mrlearning-base-ch3.md)
