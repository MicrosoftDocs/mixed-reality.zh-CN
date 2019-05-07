---
title: MR 学习基本模块的用户界面手动跟踪和混合现实工具包配置
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: unity 中，教程，hololens 混合的现实
ms.openlocfilehash: 1530fd1a1ee06d01e8ab0cc009dfba03873c3427
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993636"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR 学习基本模块的用户界面手动跟踪和混合现实工具包配置

在上一课中，您学习了一些 MRTK 必须提供通过启动 HoloLens 2 首个应用程序的功能。 在下一课中，您将学习如何创建和整理以及 UI 文本面板按钮并使用默认的交互 （触控） 来与每个按钮进行交互。 此外将探讨新增的简单操作和效果，如更改声音的大小和对象的颜色。 此模块将介绍如何修改 MRTK 配置文件，从开始关闭空间网格的可视化效果的基本概念。 

## <a name="objectives"></a>目标

* 自定义和配置混合现实工具包配置文件
* 与使用 UI 元素和按钮的全息交互
* 基本手动跟踪输入和交互

## <a name="instructions"></a>说明

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>如何配置混合现实工具包配置文件 （更改空间感知显示选项）
在本部分中将了解如何自定义和配置的默认混合现实工具包配置文件通过调整空间感知的显示选项网格。 可能遵循这些原理同样调整任何设置或 MRTK 配置文件中的值。

1. 从"BaseScene"层次结构中选择混合现实工具包 (MRTK)。 在检查器窗格中，查找"混合现实工具包脚本"并选择"活动配置文件"，如下图中所示。 双击以打开它。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>注意：默认情况下，MRTK 配置文件是不可编辑。 这些是默认配置文件模板可以从其复制并自定义。 有多个层的自定义和配置文件，因此它是标准做法来复制和配置一个或多个设置时，自定义多个配置文件。
>
>若要了解有关 MRTK 配置文件和其体系结构的详细信息，请访问[MRTK 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)。

2. 创建进行自定义的默认配置文件的副本。 若要复制的默认配置文件，单击"复制和自定义"按钮 （请参阅图）。 这将创建一份 MRTK 配置文件。 使用您自己的 MRTK 配置文件的副本，您现在可以自定义此配置文件中的任何设置。 您还需要在后续步骤中所述嵌套在此配置文件，任何其他配置文件的重复副本/自定义步骤。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 禁用空间感知网格的可见性。 若要执行此操作，找到"空间感知系统设置"图中所示。 单击"克隆"按钮右侧的"空间感知系统配置文件"以默认配置文件替换为可自定义的副本。 如果出现一个弹出窗口，按"克隆"按钮，如下面的第二个图像中所示。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 创建自定义默认混合现实空间网格观察者的副本。 单击"Windows 混合现实空间网格观察者"以查看其他选项旁边的向下箭头。 在这些选项中，你将看到"默认混合现实空间网格观察者"会显示灰 （不可编辑）。 因此你可以对其进行编辑，必须将此默认配置文件替换的可自定义的副本。 单击向右 （标记的绿色箭头） 按钮以克隆副本。

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 接下来，将调整说"的阻挡物。"的显示选项的设置 这会使空间网格不可见，但仍隐藏游戏对象背后空间网格 （这称为封闭。）

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>注意：空间映射网格不可见时，仍存在，并可以与之交互。 任何全息背后空间映射网格 （例如一张全息图背后可见墙壁上） 将无法看到由于封闭设置。

祝贺你！ 你刚刚了解了如何修改 MRTK 配置文件中的设置。 如您所见，若要修改 MRTK 设置，需要创建的默认配置文件的副本，以便您可以编辑它们。 您将始终拥有的默认配置文件 （这是不可编辑） 若要返回到，如果你想要使用新的设置创建配置文件或回头参考默认配置文件。 有许多可以调整的设置。 有关为 MRTK 配置文件设置的完整参考，请参阅此处的 MRTK 文档： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>跟踪手势和种交互的按钮
在本部分中，将了解如何使用跟踪来按种交互的按钮的工具。

1. 从项目文件夹中选择"资产"。

2. 键入在搜索栏中，"pressablebutton。"

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. 将名为"PressableButton"预设 （由蓝色框表示） 拖到你的层次结构。 

   > 注意：如果一条消息获取有关"导入 TMP Essentials"请其导入这一次。 如果 TMP Essentials 已不是项目的一部分，您可能需要在导入 TMP Essentials 的服务器，否则按钮文本可能不会显示后重复此步骤。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 双击"PressableButton"游戏对象 （它现在应是 BaseScene 层次结构中） 以查看在您的场景，如图所示 （按钮图形可能会显示不同于下图） 中所示。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. 在检查器窗格中，单击"添加事件"提供的事件响应推送时的按钮。 在显示的选项，选择下拉列表菜单。 选择"InteractableOnPressReciever。" 这样，按钮按下的事件跟踪手的形状按下按钮时响应。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. 将多维数据集添加到场景。 右键单击层次结构区，选择三维对象，然后单击"多维数据集。" 现在，多维数据集应在您的显示器。 它将看上去非常大，因此，调整坐标 （尽管仍在层次结构区域中选择"多维数据集"） 以减小大小。 将缩放值设置为 x = 0.1，y = 0.1 和 z = 0.1。 为确保在将附近 pressable 按钮，将其放在场景中定位该多维数据集，但不是重叠的按钮。 在下图中，多维数据集的位置是 x = 0，y = 0.2 和 z = 1。 

   > 注意：一般情况下，在 Unity 中的 1 个单位是大致相当于现实生活中的 1 米。 有例外情况，例如当对象是扩展对象的子级。
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. 在此步骤中您将设置多维数据集时按下按钮更改颜色。 在"BaseScene"菜单中选择 PressableButton。 在检查器窗格中，在"选择事件类型"框中，单击"+"按钮。 将"多维数据集"从"BaseScene"菜单到"仅限运行时"框中，如下图中所示

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

单击下拉列表显示"没有函数"。 选择"MeshRenderer"然后选择"材料 material。" 这将允许您按下按钮更改材料。 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

请转到项目面板和搜索你想要将其更改为的材料。 您将此示例中使用的材料"MRTK_Standard_Cyan"，找到以"青色"（MRTK 包括很多材料和可供选择的颜色。） 项目选项卡的搜索栏中键入将材料拖到"MeshRenderer.material。"下方的框 可以在资产中找到 MRTK 材料 > MixedRealityToolkit.SDK > StandardAssets > 材料。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

现在设置了事件，以便按下按钮时，多维数据集将更改基于你指定的材料的颜色。 在此示例中，多维数据集将变为青色颜色。

8. 接下来要设置发布操作，以便在版本中，按钮将返回到其默认颜色。 重复步骤 7 （上一步），但这次使用"OnRelease"事件，而不是"OnPress"事件，如下图中所示。

9.  在项目面板中，搜索为默认值在按钮时释放该多维数据集的材料 （在本例中，我们选择了 MRTK_Standard_LightGray。）将材料拖到"MeshRenderer.material"字段下方的框。

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

现在，按下按钮时，它应更改为新的颜色 (例如，蓝绿色) 和释放按钮时应更改回您指定的默认颜色 （例如，浅灰色。）按以在编辑器中试用它或将部署到 HoloLens 2，以测试在屏幕顶部的"播放"按钮 ！ 若要详细了解在编辑器中模拟，包括读取的手动模拟[MRTK 的模拟文档页](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>创建按钮使用 MRTK 的网格对象集合的一个面板

在本部分中，将了解如何自动调整到一个巧妙的用户界面中使用 MRTK GridObjectCollection 工具的多个按钮。

1. 重复上一节中的按钮，直到你具有 5 个按钮。 有几种方法来执行此操作：
- 右键单击的按钮单击"复制，"然后向下按钮下方和再次右键单击然后单击"粘贴"。 
- 右键单击的按钮，然后单击"重复。" 
- 通过单击多维数据集并按"ctrl D"在键盘上的使用的键盘命令。

重复此步骤，直到你具有 5 个总按钮 （请参阅下图中的 5 个红色箭头）。

![Mrlearning 基本 Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 组为空的父游戏对象下的按钮。 为了获得网格集合中的按钮，您需要进行分组你常用的父对象下的按钮。 Hiearachy 中右键单击，然后单击"创建为空。" 这将创建可将所有按钮都放在新的空游戏对象。 它将显示为"gameObject。" 右键单击，然后将它重命名为"ButtonCollection。"

![Mrlearning 基本 Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 将所有按钮都移动到新集合。 执行此操作通过你 heirarch 中选择所有五个按钮对象并将其拖下面"ButtonCollection"游戏对象，对所有，如下图中所示。 提示： 选择项时按住 ctrl 键选择多个项目。

![Mrlearning 基本 Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. 将 MRTK 的"网格对象集合"组件添加到按钮集合。  若要执行此操作，选择"ButtonCollection"父对象，并在检查器窗格中，单击"添加组件"按钮。 并在搜索栏中搜索"网格对象集合"并选择它时它将显示在列表中。

![Mrlearning 基本 Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

网格对象集合组件允许您将按钮或任何巧妙行、 列或网格中的对象集。 这是由你提供了一种快速简单的方式来创建美观的用户界面 MRTK 提供构建基块之一。

5. 配置网格对象集合。 若要确保所有按钮人脸用户，选择"定位类型"，并选择"人脸父向前"（如下图所示。）接下来，更改单元格大小以设置你的按钮之间的空间。 开始按 0.12 单位 0.12 单位的单元格宽度和单元格高度，如下图中所示。 您可能需要调整这些值，具体取决于选择的对象/按钮资产。 请确保"行"设置为 1。 然后单击"更新集合"，场景应外观如下图所示。 


![Mrlearning 基本 Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>注意：具体取决于子对象或父对象的方向，您可能需要调整在将来的项目中以不同方式设置的方向。 单元格宽度和单元格高度字段可能还需要有不同，具体取决于你的集合中的对象大小的定义。

### <a name="adding-text-into-your-scene"></a>将文本添加到您的场景

在本部分中，将了解如何添加和编辑你的混合的现实体验到的文本。 如果你尚未这样做，请确保您具有在 Unity 中的说明启用 TextMeshPro[此处](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)。

1. 选择"ButtonCollection"父对象，右键单击的集合。 在下拉列表菜单中，展开"3D 对象"，然后选择"TextMeshPro-Text"。 下图中所示，您应看到按钮集合中下, 一个 TextMeshPro 对象。

![第 2 课第 4 章 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![第 2 课第 4 章 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. 在 TextMeshPro 组件的文本字段中 （位于检查器面板中，如下所示），键入"按钮集合 Text"。 文本将显示在场景中，但它会隐藏在按钮和/或错误的大小。

![第 2 课第 4 章步骤 2](images/Lesson2_Chapter4_Step2.JPG)

3. 若要提高的文本大小和位置以提高可读性，调整要更改字体大小的 TextMeshPro 组件中的"字体大小"字段。 您还需要调整"Rect 转换"位置和缩放比例，如下图中所示。 请参阅下图中的值用于我们的文本的配置，并随意使用这些值作为起始点以进一步改善的大小和位置的文本字段。

![第 2 课第 4 章 Step3](images/Lesson2_Chapter4_Step3.JPG)
![第 2 课第 4 章步骤 4](images/Lesson2_Chapter4_Step4.JPG)

5. 若要修改的按钮对象上的文本值，单击导航到"SeeItSayItLabel"的对象，并展开任何按钮旁边的箭头，然后导航到"TextMeshPro"，其中可以为你的按钮，如上述步骤中所述编辑文本。

![第 2 课第 4 章步骤 5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>恭喜 ！
在本课程中，您学习了如何复制、 自定义和配置 MRTK 配置文件设置 （即，空间感知网格可见性。）您还学习了如何使用跟踪的手上 HoloLens 2 触发事件的按钮与进行交互。 最后，您学习了如何创建一个简单的 UI 接口使用 Unity 的文本 Mesh Pro MRTK 的网格对象集合组件。

[下一课：动态内容的位置和求解器](mrlearning-base-ch3.md)

