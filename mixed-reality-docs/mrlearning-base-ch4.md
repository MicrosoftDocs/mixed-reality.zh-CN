---
title: MR 学习基本模块的三维对象交互
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity 中，教程，hololens 混合的现实
ms.openlocfilehash: 45e772de0825fe2161f880a165d6c75c755b849e
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730910"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>MR 学习基本模块的三维对象交互

在本课中，我们将介绍基本的三维内容和用户体验。 我们将了解如何将三维对象组织成集合的一部分、 了解边界框的基本操作、 了解近和远交互，并了解触摸和用跟踪一只手获取手势。 

## <a name="objectives"></a>目标

* 了解如何组织使用 MRTK 的网格对象集合的 3D 内容
* 边界框的实现
* 配置三维对象的基本操作 （移动、 旋转、 和规模）
* 探索近和远交互
* 了解更多手动跟踪笔势，例如随取即行和触摸

## <a name="instructions"></a>说明

### <a name="organizing-3d-objects-in-a-collection"></a>组织集合中的三维对象

1. 右键单击你的层次结构和选择，"创建为空。" 这将创建一个空的游戏对象。 它重命名为"3DObjectCollection。" 这是我们将放置所有我们三维对象。 请确保集合的位置设置为 x = 0，y = 0，并且 z = 0。

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. BaseModule 资产使用相同的说明导入自定义包中所述导入[Lesson1](mrlearning-base-ch1.md)。 BaseModule 资产包括 3D 模块和其他有用的脚本将在本教程中使用。 BaseModule unity 包可在此处找到： <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. 它旁边的蓝色多维数据集可以识别咖啡杯预设。 不要选择具有蓝色多维数据集和小白皮书 （即表示原始的三维模型和不预设。） coffee 创新杯 

![Lesson4 第 1 章 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. 将所选的咖啡杯预设可从第 1 步拖到"3DObjectCollection"游戏对象。 咖啡杯现在是集合的子级。

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. 接下来，我们将添加到场景的多个三维对象。 下面是我们要在此示例中添加的对象的列表。 添加对象时可能会发现它们会出现在您的场景中不同的大小。 调整每个 3D 模型检查器面板中的转换设置的小数位数。 建议的调整此示例列出了下面的对象。 项目面板中的搜索框中搜索这些单词，并将 3D 物体预设可拖放到"3DObjectCollection"对象类似于上一步。 您将在资产中找到预设这些集合 > BaseModuleAssets > 基本模块预设
- 搜索"TheModule_BaseModuleIncomplete。" 拖动到场景中。 设置的小数位数为 x = 0.03，y = 0.03，z = 0.03。 
- 搜索"Octa_BaseModuleIncomplete。" 拖动到场景中。 设置的小数位数为 x = 0.13。 y = 0.13, z =0.13.
- 搜索"EarthCore_BaseModuleIncomplete。" 拖动到场景中。 设置的小数位数为 x = 50.0 y = 50.0，z = 50.0。
- 搜索"Cheese_BaseModuleIncomplete。" 拖动到场景中。 设置的小数位数为 x = 0.05，y = 0.05，z = 0.05。
- 搜索"Model_Platonic_BaseModuleIncomplete。" 拖动到场景中。 设置的小数位数为 x = 0.13，y = 0.13，z = 0.13。
- 搜索"CoffeeCup_BaseModuleIncomplete。" 拖动到场景中。

![Lesson4 第 1 章 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. 将 3 个多维数据集添加到您的场景。 右键单击"3DObjectCollection"对象，选择"3D 对象"，然后选择"多维数据集。" 设置的小数位数为 x = 0.14，y = 0.14 和 z = 0.14。 重复此步骤 2 次来创建 3 个多维数据集的总数。 或者，可能会重复两次的总数为 3 个多维数据集的多维数据集。 您还可以选择使用资产中的三个预定义的多维数据集预设 > BaseModuleAssets > 基本模块预设和选择 GreenCube_BaseModuleIncomplete、 BlueCube_BaseModuleIncomplete 和 OrangeCube_BaseModuleIncomplete。

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. 组织以形成一个网格，使用过程中所述的对象的集合[第 2 课](mrlearning-base-ch2.md)使用 MRTK 的网格对象集合。 请参阅下图所示，若要查看的 3 x 3 个网格中配置的对象示例。

![Lesson4 第 1 章 Notebim](images/Lesson4_chapter1_notebim.PNG)

>注意：您可能会注意到某些对象是偏离中心，如在上图中的对象。 这是因为预设或对象可能具有未对齐的子对象。 随意对对象位置或子对象的位置，若要实现良好对齐的网格进行任何必要的调整。


### <a name="manipulating-3d-objects"></a>操作三维对象
1. 添加操作多维数据集的能力。 若要添加操作三维对象的功能必须执行以下操作：
-   选择要进行处理 （在此示例中，一个多维数据集） 在层次结构中的三维对象。
-   单击"添加组件"。 
-   搜索"操作"。
-   选择"操作处理程序。"
-   重复的"3DObjectCollection"对象，但不是"3DObjectCollection"下的所有三维对象本身。
-   确保所有三维对象都有碰撞体或盒状碰撞体 (添加组件 > 框碰撞体)。

![Lesson4 第 2 章 Step1im](images/Lesson4_chapter2_step1im.PNG)

>操作处理程序是一个组件，您可以调整对象时被操作的行为的设置。 这包括旋转、 缩放、 移动和某些轴上的约束移动。 

2. 限制一个多维数据集，以便它仅可以调整。 在"3DObjectCollection"对象中选择一个多维数据集。 在检查器窗格中的"两个提交的操作类型"旁边，单击下拉列表菜单，然后选择"缩放"。 这使得它，以便用户只能更改多维数据集的大小。

![Lesson4 第 2 章 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 更改每个多维数据集的颜色，以便我们可以区分它们。 
-   转到项目面板，并向下滚动，直到看到"MixedRealityToolkit.SDK"，然后选择它。
-   选择"Standard Assets"文件夹。
-   单击"资料"文件夹。
-   将不同材料拖到每个多维数据集上。 

>注意：您可以选择多维数据集的任何颜色。 对于本示例中，我们将使用"glowingcyan，""glowingorange"和"绿色"。 随意尝试不同的颜色。 若要将颜色添加到多维数据集，单击你想要更改的颜色的多维数据集，然后将材料拖动到网格呈现器的多维数据集的检查器面板中的材料字段。 

![Lesson4 第 2 章 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. 在"3DObjectCollection"对象选择另一个多维数据集并使其，以便从开头到修复距离约束及其移动。 为此，请在"约束的移动"的右侧，单击下拉列表菜单，然后选择"修复开头的距离"。 这使得它，以便用户只能移动其视野中的多维数据集。 

![Lesson4 第 2 章 Step4im](images/Lesson4_chapter2_step4im.PNG)

下面的几个步骤的目标：我们将允许随取即行以及与我们的三维对象的交互。 我们将应用不同的操作设置 

5. 选择奶酪对象，并在检查器窗格中，单击"添加组件"。 

6. 在搜索框中的"附近交互 Grabbable"搜索和选择的脚本。 此组件允许用户联系，获取与跟踪手对象。 对象还允许操作从远处，除非"允许最操作"复选框处于未选中状态 （由下图中的绿色圆圈）。

![Lesson4 第 2 章 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 通过重复步骤 5 和 6 对这些对象，将添加"附近交互 Grabbable"到八对象、 柏拉图对象、 地球核心、 农历模块和创新杯咖啡。

8. 从八对象删除的远端操作的功能。 若要执行此操作，在层次结构中，选择八并取消选中"允许最操作"复选框 （用绿色圆圈标记）。 这使得它，以便用户可以仅与直接使用跟踪的手八进行交互。

>注意：有关完整的操作处理程序组件和它的文档具有关联的设置，请参阅[MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。

9. 确保已将"附近交互 Grabbable"组件添加到地球核心、 农历模块和 coffee cup （请参阅第 7 步）。

10. 对于农历模块中，更改操作处理程序设置，以便它将围绕对象的中心附近的两个和最交互，如下图中所示。

![Lesson4 第 2 章 Step10im](images/Lesson4_chapter2_step10im.PNG)

11:对于地球 core 中，更改到的发布行为"nothing"。 这使得它，以便后从用户的掌握中释放地球核心，它不会继续移动。 

![Lesson4 第 2 章 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> 注意：此设置可用于方案，例如创建可能会引发一个球。 通过将方向的速度和角速度可以，以便发布球后它将继续移动的方向的速度是在已发布，类似于物理球会行为方式。

### <a name="adding-bounding-boxes"></a>添加边界框
边界框使它更简单且更直观地操作对象用一只手进行直接操作 （附近交互） 和基于 ray 的操作 （远端交互）。边界框提供了可以获取有关缩放和旋转轴特定对象的"handles"。
>注意：可以将边界框添加到对象之前首先需要具有一个碰撞体的对象 （例如，盒状碰撞体。）与我们以前在本课程中。 选择对象，并选择添加组件的对象的检查器面板中，可以添加碰撞体 > 盒状碰撞体。
>

1. 将盒状碰撞体添加到地球核心对象，如果尚不存在 （盒状碰撞体，并使用预设可提供在基本模块资产文件夹中的每个提供的说明，如果不是必需的安装程序。）在地球核心的情况下，我们将需要将盒状碰撞体添加到地球核心，下面的"node_id30"对象，如下图中所示。 选择 node_id30 和中对象的检查器选项卡上，单击"添加组件"，然后搜索"框的碰撞体"。 

![Lesson4 第 3 章 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 第 3 章 Step2im](images/Lesson4_chapter3_step2im.PNG)

> 注意：请确保你可视化盒状碰撞体，以便它不是太大或太小。 它应为大致与它围绕 （在此示例中，地球核心） 的对象的大小相同。 通过在盒状碰撞体中选择编辑碰撞体选项可以根据需要调整盒状碰撞体。 你可以更改 x、 y 和 z 值或拖动边界框处理程序编辑器场景窗口中。 

![Lesson4 第 3 章 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 将添加到地球 core"node_id30"对象的边界框。 若要执行此操作，请选择"3DObjectCollection。"中的"node_id30"对象 在检查器选项卡中，单击"添加组件"，搜索"边界框"。 请确保边界框、 盒状碰撞体和操作脚本 （附近 grabbable 交互操作处理程序） 都在同一游戏对象。

3.  在边界框的"行为"部分中，选择"启动"从激活激活下拉列表中。 若要查看有关各种激活选项和其他边界框中选项的更多详细信息，请参阅[MRTK 的边界框文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *接下来的几个步骤，我们也将更改通过调整默认框材料、 而正在获取的材料，以及可视化效果的句柄 （角和侧面的句柄） 的边界框的外观。MRTK 包含几个选项用于自定义的边界框。*

4. 中的项目面板中，搜索"boundingbox"和你将看到一系列表示搜索结果中的蓝色球的材料中如下图所示。 

5. 边界框组件上，将"boundingbox"材料拖入框材料槽。 此外获取"boundingboxgrabbed"材料和上边界框组件放入框 grabbed 材料槽。

6. 边界框组件上，将"MRTK_BoundingBox_ScaleWidget"材料拖到缩放句柄 prefab 槽。 

7. 将"MRTK_BoundingBox_RotateWidget"材料拖到旋转句柄槽捆绑框组件上。

![Lesson4 第 3 章第 4 步 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. 请确保边界框所面向的右边的对象。 边界框组件，在没有"目标对象"和"绑定重写"的脚本。 请确保将具有这两种这些槽在其周围的边界框的对象。 在此示例中，"node_id30"将对象拖到这两个这些槽，如下图中所示。

> 在启动或运行该应用程序时，您的对象将现在圈定的蓝色框上。 请别客气拖动以调整对象大小的帧的角。 如果我们想要缩放的句柄和旋转句柄，以进行更大、 更直观，我们建议使用默认值边界框设置 （避免步骤 4-7）。 

![Lesson4 第 3 章 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. 若要返回到默认的边界框的可视化效果，边界框的对象的检查器面板中选择旋转句柄预设并按 delete 键，现在将看到类似于下面的图像的边界框可视化效果。 注意： 仅出现在播放模式下的边界框可视化效果。

![Lesson4 第 3 章 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>添加触摸效果
在此示例中，我们将在与您的手接触对象时播放声音效果。

1. 将音频源组件添加到您的游戏对象。 应用场景的层次结构中选择"八"对象。 在检查器窗格中，单击"添加组件"按钮，搜索并选择"音频源。" 我们将使用此音频源以在稍后的步骤中播放声音效果。 

>注意：请确保"八"对象对其具有盒状碰撞体。

2. "靠近可触摸交互"组件添加。 单击检查器面板和"附近的可触摸交互。"的搜索中的"添加组件"按钮 选择它以添加该组件。 注意： 修复屏幕快照以突出显示，我们将添加该组件，并不只突出显示盒状碰撞体。

>注意：以前，我们添加了"近交互 grabbable。" 区别这之间和"附近可触摸交互"是"grabbable"交互用于获取并与之交互的对象。 "可触摸"组件适用于涉及的对象。 这两个组件可以一起用于交互的组合。

![Lesson4 第 4 章 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. 在"分发交互触摸"脚本中添加。 请注意，使用此演示包的一部分导入 unity 场景包括此脚本，它不包含在原始 MRTK。 只需像上一步骤中，单击"添加组件"并搜索"手动交互接触"以将其添加。 
   请注意，必须使用脚本的 3 个选项： 

   - "上接触已完成的。" 这会触发触摸和释放对象时。 
   - "上触摸已启动。" 这会触发触摸对象时。 
   - "上接触更新的。" 这会定期触发的而您的手接触对象。 

   对于此示例中，我们将使用"上启动的接触"设置。

4. 单击"上启动触摸"选项中的"+"按钮，如下图中所示。 将八对象拖到空的字段。 

5. 在下拉列表显示 （如上图所示的绿色矩形） 所示的"函数"，选择 AudioSource > PlayOneShot。 我们会将音频剪辑添加到此字段使用以下概念：

   - MRTK 确实提供音频剪辑的简短列表。 随意浏览这些项目面板中。 将"MixedRealityToolkit.SDK"文件夹，然后"standard assets"文件夹下找到它们。 您将看到所有音频剪辑所在的"audio"文件夹。
   - 对于此示例中，我们将使用"MRTK_Gem"音频剪辑。 
   - 要添加音频剪辑，只需将您想要的剪辑从项目面板到 AudioSource.PlayOneShot 检查器面板中 （上面的示例中的绿色框标记）。

   现在，当用户访问，并涉及八对象，将播放音频曲目"MRTK_Gem"。 "手动交互触摸"脚本还将调整时涉及的对象的颜色。 

![Lesson4 第 4 章 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>恭喜 ！ 
在本课程中，学习了如何组织网格集合中的三维对象以及如何操作三维对象 （缩放、 旋转和移动） 使用附近 （直接获取与跟踪手） 的交互和远端交互 （使用的视线移动大气或手动大气）。您还学习了如何将三维对象周围的边界框，并介绍了如何使用和自定义的边界框上 gizmos，请。 最后，您学习了如何在触发事件时触摸对象。

[下一课：高级的输入](mrlearning-base-ch5.md)

