---
title: 入门教程-5。 与三维对象交互
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 8c60d8291ede123817c93458fff003891169840c
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105969"
---
# <a name="5-interacting-with-3d-objects"></a>5. 与三维对象交互

在本教程中，你将了解基本的3D 内容和用户体验，例如：

* 将三维对象组织为集合的一部分
* 基本操作的边界框
* 近和远交互
* 触摸和获取手动跟踪的手势

## <a name="objectives"></a>目标

* 了解如何通过 MRTK 的网格对象集合来组织3D 内容
* 实现边界框
* 为基本操作配置3D 对象--移动、旋转和缩放
* 探索近距和远距交互
* 了解其他手动跟踪手势，如抓取和触摸

## <a name="instructions"></a>说明

### <a name="organizing-3d-objects-in-a-collection"></a>在集合中组织 3D 对象

1. 右键单击你的层次结构，然后选择 "创建空" 创建一个空游戏对象，将其重命名为 "3DObjectCollection"，并确保其位于 x = 0、y = 0，z = 0。

    ![mrlearning-base-ch4-1-step1 .png](images/mrlearning-base-ch4-1-step1.png)

2. 下载 Unity 包[HoloLens2](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) ，并使用与导入[学习](mrlearning-base-ch1.md)中所述的自定义包相同的说明导入它。 此包包括3D 模型以及在本教程中使用的其他有用资产。

3. 在 "项目" 面板中，导航到 "资产" > BaseModuleAssets > 基本模块 "Prototyping"，然后搜索 "未完成"，我们将使用其中一些 prototyping。

    ![mrlearning-base-ch4-1-step3 .png](images/mrlearning-base-ch4-1-step3.png)

4. 将咖啡杯拖到步骤1中的3DObjectCollection 游戏对象。 现在，该咖啡杯是集合的子级。

    ![mrlearning-base-ch4-1-step4 .png](images/mrlearning-base-ch4-1-step4.png)

5. 接下来，您将按照上一步骤中的相同过程，将更多的3D 对象添加到场景中。 下面是此示例中要添加的对象的列表。 添加这些对象时，可能会发现它们以各种大小显示在场景中。 调整检查器面板中 "转换设置" 下的每个三维模型的比例。 下面列出了本示例中各个对象的建议调整大小。

    * Cheese_BaseModuleIncomplete。 Scale： x = 0.05，y = 0.05，z = 0.05。
    * CoffeeCup_BaseModuleIncomplete。 Scale： x = 0.1，y = 0.1，z = 0.1。
    * EarthCore_BaseModuleIncomplete。 Scale： x = 50.0 y = 50.0，z = 50.0。
    * Model_Platonic_BaseModuleIncomplete。 Scale： x = 0.13，y = 0.13，z = 0.13。
    * Octa_BaseModuleIncomplete。 Scale： x = 0.13。 y = 0.13，z =0.13。
    * TheModule_BaseModuleIncomplete。 Scale： x = 0.03，y = 0.03，z = 0.03。

    ![mrlearning-base-ch4-1-step5 .png](images/mrlearning-base-ch4-1-step5.png)

6. 将三个多维数据集添加到场景中。 右键单击 "3DObjectCollection" 对象，选择 "3D 对象"，然后选择 "多维数据集"。 将坐标设置为 x = 0.14，y = 0.14，z = 0.14。 重复此步骤两次，以创建总计三个多维数据集。 或者，可以复制多维数据集两次，共三个多维数据集。 也可以选择使用“资产”>“基础模块资产”>“基础模块预制件”中三个已准备好的立方体预制件，并选择“GreenCube_BaseModuleIncomplete”、“BlueCube_BaseModuleIncomplete”和“OrangeCube_BaseModuleIncomplete”。

    ![mrlearning-base-ch4-1-step6 .png](images/mrlearning-base-ch4-1-step6.png)

7. 使用 MRTK 的网格对象集合，通过[第2课](mrlearning-base-ch2.md)中所述的过程来组织对象集合，以形成网格。 请参阅下图，以了解在3x3 网格中配置对象的示例。

    ![mrlearning-base-ch4-1-step7 .png](images/mrlearning-base-ch4-1-step7.png)

    >[!NOTE]
    >你可能会注意到，某些对象处于中间中心，如上图中的对象。 这是因为，预制件或对象可能包含未对齐的子对象。 请对对象位置或子对象位置进行任何必要的调整，以获得适当对齐的网格。

### <a name="manipulating-3d-objects"></a>操作 3D 对象

1. 添加操作立方体的功能。 若要添加操作3D 对象的功能，请执行以下操作：
    * 选择要在层次结构中操作的3D 对象（即某个多维数据集）。
    * 单击 "添加组件"
    * 搜索 "操作"
    * 选择操作处理程序
    * 对3DObjectCollection 对象下的所有3D 对象重复此操作，而不是3DObjectCollection 本身。
    * 确保所有三维对象都具有碰撞器或盒碰撞器（添加组件 > 框碰撞器）。

    ![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

    >[!NOTE]
    >操作处理程序是一个组件，可用于调整对象在操作时的行为方式的设置。 这包括在特定轴上进行旋转、缩放、移动和约束移动。

2. 请限制一个立方体，以便只能对它进行缩放。 选择3DObjectCollection 对象中的一个多维数据集。 在 "检查器" 面板中，在 "两种操作类型" 旁单击下拉菜单，然后选择 "缩放"。 这样，用户只能更改该立方体的大小。

    ![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 更改每个立方体的颜色，以便可以区分它们。
    * 请访问 "项目" 面板并向下滚动，直到看到 "MixedRealityToolkit"，然后选择它。
    * 选择 "标准资产" 文件夹。
    * 单击 "材料" 文件夹。
    * 将不同的材料拖放到每个立方体上。

    >[!NOTE]
    >可为立方体选择任意颜色。 在此示例中，使用了 glowingcyan、glowingorange 和绿色。 请随意尝试不同的颜色。 若要将颜色添加到多维数据集，请单击想要更改的多维数据集，然后将该材料拖到多维数据集的 "检查器" 面板中的 "网格呈现器" 材料字段。

    ![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. 选择3DObjectCollection 对象中的其他多维数据集，然后将其移动限制为固定距离。 为此，请在 "移动标签上的约束" 右侧单击下拉菜单，然后选择 "修复距离"。 这会将多维数据集调整到其视觉领域。

    ![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

    下面几个步骤的目标是启用抓取并与我们的3D 对象进行交互，并应用不同的操作设置。

5. 选择奶酪对象，并单击 "检查器" 面板中的 "添加组件"。

6. 在搜索框中搜索近乎交互 Grabbable，并选择该脚本。 此组件使用户可以通过跟踪的手访问和吸引对象。 对象也可以从远处操作，除非在下图中以绿色圆圈表示的 "允许远操作" 复选框未被选中。

    ![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 通过对这些对象重复步骤5和步骤6，将近交互 Grabbable 添加到八对象、Platonic 对象、地球核心、农历和咖啡杯。

8. 从八面体对象中删除远距操作功能。 为此，请选择层次结构中的八，并取消选中 "允许远端操作" 复选框（由绿色圆圈标记）。 这样，用户就只能使用跟踪的手直接与八交互。

    >[!NOTE]
    >有关操作处理程序组件及其相关设置的完整文档，请参阅[MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。

9. 确保将近交互 Grabbable 组件添加到了地球核心、农历模块和咖啡杯上（请参见步骤7）。

10. 对于农历模块，请更改操作处理程序设置，使其围绕对象中心围绕近和远交互进行旋转，如下图所示。

    ![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11. 对于地球核心，将版本行为更改为 "无"。 这样做是为了使地球核心从用户的抓住中释放出来，而不会继续移动。

    ![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

    >[!NOTE]
    >此设置适用于方案，例如创建可引发的球。 保持适当的速度和角度速度，以确保在球发布后，它将继续以其释放速度的速度移动;与物理球的行为方式类似。

### <a name="adding-bounding-boxes"></a>添加边界框

边界框使您可以更轻松、更直观地处理对象，同时可以直接操作（接近交互）和基于光线的操作（远交互）。边界框提供可用于沿特定轴缩放和旋转对象的句柄。

>[!NOTE]
>在将边界框添加到对象之前，您首先需要在该对象上创建一个碰撞器（例如，盒碰撞器），如本课程前面所述。 可以通过选择对象并在对象的 "检查器" 面板中选择 "添加组件 >" 碰撞器来添加 Colliders。

1. 如果地球核心对象尚不存在，请将其添加到地球核心对象。 如果根据给定的说明使用基本模块资产文件夹中提供的 prefab，则不需要使用框碰撞器和设置。 对于地球核心，我们将框碰撞器添加到了地球核心下的、node_id30 的对象，如下图所示。 从对象的 "检查器" 选项卡中选择 "node_id30"，单击 "添加组件"，然后搜索 box 碰撞器。

    ![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

    ![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

    >[!NOTE]
    >请确保将框碰撞器的大小设置为不太大或太小。 其大小应与围绕它的对象（在本示例中为地核）大致相同。 通过选择框碰撞器中的 "编辑碰撞器" 选项，根据需要调整框碰撞器。 您可以更改 x、y 和 z 值，也可以在编辑器场景窗口中拖动边界框处理程序。

    ![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 将边界框添加到地球核心的 node_id30 对象。 为此，请从3DObjectCollection 中选择 "node_id30" 对象。 在 "检查器" 选项卡中，单击 "添加组件"，然后搜索 "边界框"。 确保边界框、盒碰撞体和操作脚本（操作处理程序、近距交互可抓取对象）都在同一个游戏对象中。

3. 在 "边界框的行为" 部分中，从 "激活" 下拉列表中选择 "开始时激活"。 若要查看有关各个激活选项和其他范围框选项的其他详细信息，请参阅[MRTK 的边界框文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

    *在接下来的几个步骤中，我们还将通过以下方式更改边界框的显示方式：调整默认的框材料、在其被抓取时的材料以及角部和侧图柄的可视化。MRTK 包含多个用于自定义边界框的选项。*

4. 在 "项目" 面板中搜索 "boundingbox"，并在搜索结果中看到一个蓝色球体表示的材料列表，如下图所示。

5. 将 boundingbox 材料拖动到边界框组件上的盒材料槽。 另外，还可以获取 boundingboxgrabbed 材料，并将其放在边界框组件上的 "获取材料" 槽。

    ![mrlearning-base-ch4-3-step5 .png](images/mrlearning-base-ch4-3-step5.png)

6. 将 MRTK_BoundingBox_ScaleHandle prefab 拖到 "prefab" 槽中的刻度控点，并将 MRTK_BoundingBox_RotateHandle prefab 拖到 "捆绑箱" 组件上的旋转控点槽。

    ![mrlearning-base-ch4-3-step6 .png](images/mrlearning-base-ch4-3-step6.png)

7. 确保边界框针对适当的对象。 在边界框组件中，有目标对象和边界替代脚本。 将边界框周围的对象拖到这两个槽。 在此示例中，将 node_id30 对象拖到这两个槽，如下图所示。

    ![mrlearning-base-ch4-3-step7 .png](images/mrlearning-base-ch4-3-step7.png)

    >[!NOTE]
    >启动或播放应用程序时，对象将被蓝色框架括起来。 可以放心拖动该框的四角，以调整对象的大小。 如果希望缩放控点更大且更可见，则建议使用默认边界框设置（避免步骤 4-6）。

8. 若要返回到默认边界框可视化效果，请在边界框的对象的检查器面板中，选择旋转控点 prefab，并按 delete 将其删除。 进入播放模式时，wou 会看到类似于下图的边界框可视化。

    ![mrlearning-base-ch4-3-step8 .png](images/mrlearning-base-ch4-3-step8.png)

    >[!NOTE]
    >只有在播放模式下，边界框可视化效果才会显示。

### <a name="adding-touch-effects"></a>添加触摸效果

本示例将在用手触摸某个对象时播放一段音效。

1. 将音频源组件添加到游戏对象。 选择场景层次结构中的八对象。 在检查器面板中，单击 "添加组件" 按钮，搜索并选择 "音频源"。 在稍后的步骤中，我们将使用此音频源播放音效。

    >[!NOTE]
    >确保八对象上有一个框碰撞器。

2. 添加 Near 交互可触摸组件。 单击 "检查器" 面板中的 "添加组件" 按钮，搜索近乎交互可触摸。 选择该对象以将它添加到组件。

    >[!NOTE]
    >以前，我们添加了近交互 grabbable。 此交互和近交互可触摸之间的区别在于，grabbable 交互适用于要进行抓取和交互的对象。 可触摸组件适用于要接触的对象。 可以结合使用这两个组件以实现组合式交互。

    ![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. 添加手交互触摸脚本。 与上一步一样，单击 "添加组件"，然后搜索 "手动交互触摸" 进行添加。

    请注意，此脚本有三个选项：
    * On Touch 完成：触控并释放对象时触发
    * 开始时：接触对象时触发
    * On Touch 更新：在你的手中触摸对象时定期触发

    在此示例中，我们将使用 "按下开始使用" 设置。

    >[!NOTE]
    >此脚本随你在本教程开始时导入的 BaseModuleAssets Unity 包一起提供，并且不包含在原始 MRTK 中。

4. 单击 "按 Touch 开始" 选项上的 "+" 按钮，然后将八对象拖到空字段。

    ![mrlearning-base-ch4-4-step4 .png](images/mrlearning-base-ch4-4-step4.png)

5. 在 "没有函数" 下拉箭头中，选择 "AudioSource > PlayOneShot"。 使用以下概念将一个音频剪辑添加到此字段：

    * MRTK 提供了一个简短的音频剪辑列表。 可以在项目面板中随意浏览这些项。 你会在资产 > MixedRealityToolkit > 标准资产 > 音频文件夹 "下找到它们。
    * 在此示例中，我们将使用 MRTK_Gem 音频剪辑。
    * 若要添加音频剪辑，只需将所需剪辑从 "项目" 面板拖动到 "AudioSource" PlayOneShot 字段。

    ![mrlearning-base-ch4-4-step5 .png](images/mrlearning-base-ch4-4-step5.png)

   现在，当用户到达并接触八对象时，将播放 MRTK_Gem 音频轨。 触摸时，手动交互触摸脚本还会调整对象的颜色。

## <a name="congratulations"></a>祝贺

在本教程中，您学习了如何在网格集合中组织3D 对象，以及如何使用接近的交互（直接抓取、旋转和移动）来处理这些对象（使用 "注视" 光线或手写光线）。 还了解了如何在三维对象周围添加边界框，并了解了如何使用和自定义边界框中的 gizmos。 最后，你已了解如何在触摸对象时触发事件。

[下一课： 6. 浏览高级输入选项](mrlearning-base-ch5.md)
