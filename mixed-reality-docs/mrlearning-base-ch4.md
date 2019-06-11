---
title: MR 学习基础模块 - 3D 对象交互
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 45e772de0825fe2161f880a165d6c75c755b849e
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730910"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>MR 学习基础模块 - 3D 对象交互

本课介绍基本的 3D 内容和用户体验。 我们将了解如何将 3D 对象组织成集合的一部分、基本操作的边界框、近距和远距交互，以及结合手动跟踪的触摸和抓取手势。 

## <a name="objectives"></a>目标

* 了解如何使用 MRTK 的网格对象集合组织 3D 内容
* 实现边界框
* 配置基本操作（移动、旋转和缩放）的 3D 对象
* 探索近距和远距交互
* 了解其他手动跟踪手势，例如抓取和触摸

## <a name="instructions"></a>说明

### <a name="organizing-3d-objects-in-a-collection"></a>在集合中组织 3D 对象

1. 右键单击层次结构并选择“创建空对象”。 这会创建一个空游戏对象。 将它重命名为“3DObjectCollection”。 我们的所有 3D 对象将放入其中。 确保集合的位置设置为 x = 0，y = 0，z = 0。

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. 遵照相同的说明导入基础模块资产，以导入[第 1 课](mrlearning-base-ch1.md)中所述的自定义包。 基础模块资产包含 3D 模块，以及要在整篇教程中使用的其他有用脚本。 可在此处找到基础模块 unity 包：<https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. 可根据旁边的蓝色立方体识别咖啡杯预制件。 请不要选择带有蓝色立方体和小白纸（表示原始 3D 模型，而不是预制件）的咖啡杯。 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. 将所选的咖啡杯预制件拖入步骤 1 中所述的“3DObjectCollection”游戏对象。 现在，该咖啡杯是集合的子级。

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. 接下来，将更多的 3D 对象添加到场景中。 下面是要在本示例中添加的对象列表。 添加对象时，你可能会发现，它们以不同的大小显示在场景中。 通过检查器面板中的转换设置来调整每个 3D 模型的坐标。 下面列出了本示例中各个对象的建议调整大小。 请在项目面板上的搜索框中搜索这些字词，并像上一步骤中一样，将 3D 对象预制件拖入“3DObjectCollection”对象。 可在“资产”>“基础模块资产”>“基础模块预制件”中找到这些预制件集合
- 搜索“TheModule_BaseModuleIncomplete”。 将其拖到场景中。 将坐标设置为 x = 0.03，y = 0.03，z = 0.03。 
- 搜索“Octa_BaseModuleIncomplete”。 将其拖到场景中。 将坐标设置为 x = 0.13， y = 0.13，z =0.13。
- 搜索“EarthCore_BaseModuleIncomplete”。 将其拖到场景中。 将坐标设置为 x = 50.0，y = 50.0，z = 50.0。
- 搜索“Cheese_BaseModuleIncomplete”。 将其拖到场景中。 将坐标设置为 x = 0.05，y = 0.05，z = 0.05。
- 搜索“Model_Platonic_BaseModuleIncomplete”。 将其拖到场景中。 将坐标设置为 x = 0.13，y = 0.13，z = 0.13。
- 搜索“CoffeeCup_BaseModuleIncomplete”。 将其拖到场景中。

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. 将 3 个立方体添加到场景中。 右键单击“3DObjectCollection”对象，选择“3D 对象”，然后选择“立方体”。 将坐标设置为 x = 0.14，y = 0.14，z = 0.14。 再重复此步骤 2 次，总共创建 3 个立方体。 或者，可以复制该立方体两次，总共获得 3 个立方体。 也可以选择使用“资产”>“基础模块资产”>“基础模块预制件”中三个已准备好的立方体预制件，并选择“GreenCube_BaseModuleIncomplete”、“BlueCube_BaseModuleIncomplete”和“OrangeCube_BaseModuleIncomplete”。

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. 参考[第 2 课](mrlearning-base-ch2.md)中所述的过程，使用 MRTK 的网格对象集合组织对象集合，以构成一个网格。 请参考下图，其中通过一个示例演示了如何在 3x3 网格中配置对象。

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>注意：你可能会注意到，某些对象偏离了中心，例如上图中的对象。 这是因为，预制件或对象可能包含未对齐的子对象。 请对对象位置或子对象位置进行任何必要的调整，以获得适当对齐的网格。


### <a name="manipulating-3d-objects"></a>操作 3D 对象
1. 添加操作立方体的功能。 若要添加操作 3D 对象的功能，必须执行以下操作：
-   在层次结构中选择要操作的 3D 对象（在本示例中为某个立方体）。
-   单击“添加组件”。 
-   搜索“操作”。
-   选择“操作处理程序”。
-   针对“3DObjectCollection”下的所有 3D 对象（但不要对“3DObjectCollection”对象本身）重复此过程。
-   确保所有 3D 对象包含碰撞体或盒碰撞体（“添加组件”>“盒碰撞体”）。

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>操作处理程序组件可让你调整在操作对象时其行为方式的相关设置。 这包括旋转、缩放、移动以及在某些轴上约束运动。 

2. 请限制一个立方体，以便只能对它进行缩放。 在“3DObjectCollection”对象中选择一个立方体。 在检查器面板中的“双手操作类型”旁边，单击下拉菜单并选择“缩放”。 这样，用户只能更改该立方体的大小。

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 更改每个立方体的颜色，以便可以区分它们。 
-   转到项目面板，向下滚动到“MixedRealityToolkit.SDK”并将其选中。
-   选择“Standard Assets”文件夹。
-   单击“材料”文件夹。
-   将不同的材料拖放到每个立方体上。 

>注意：可为立方体选择任意颜色。 本示例使用“glowingcyan”、“glowingorange”和“green”。 请随意尝试不同的颜色。 若要将颜色添加到立方体，请单击要更改颜色的立方体，然后将材料拖放到立方体检查器面板中网格渲染器的材料字段中。 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. 在“3DObjectCollection”对象中选择另一个立方体，并使其运动受限于与头部之间的固定距离。 为此，请在“约束运动”的右侧，单击下拉菜单并选择“与头部之间的固定距离”。 这样，用户只能在其视野范围中移动该立方体。 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

以下几个步骤的目标：实现 3D 对象的抓取和交互。 应用不同的操作设置 

5. 选择奶酪对象，并在检查器面板中单击“添加组件”。 

6. 在搜索框中搜索“近距交互可抓取对象”并选择脚本。 此组件可让用户使用跟踪手伸手抓取对象。 除非已取消选中“允许远距操作”复选框（如下图中绿色圆圈所示），否则还可以在某种距离内操作对象。

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 针对这些对象重复步骤 5 至 6，将“近距交互可抓取对象”添加到八面体、柏拉图对象、地核、登月舱模块和咖啡杯。

8. 从八面体对象中删除远距操作功能。 为此，请在层次结构中选择八面体，并取消选中“允许远距操作”复选框（如绿色圆圈所示）。 这样，用户只能使用跟踪手来直接与八面体交互。

>注意：有关操作处理程序组件及其相关设置的完整文档，请参阅 [MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。

9. 确保已将“近距交互可抓取对象”组件添加到地核、登月舱模块和咖啡杯（请参阅步骤 7）。

10. 对于登月舱模块，请更改操作处理程序设置，以便在近距和远距交互时，该模块会围绕对象的中心旋转，如下图所示。

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11：对于地核，请将释放行为更改为“无”。 这样，在用户释放地核时，它不会继续移动。 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> 注意：在创建可投射的球等场景中，可以使用此设置。 如果保持速度和角速度，在松开该球时，它会按松开时的速度继续运动，就像实物球的行为一样。

### <a name="adding-bounding-boxes"></a>添加边界框
使用边界框可以更方便、更直观地单手操作对象，它支持定向操作（近距交互）和基于光线的操作（远距交互）。边界框提供可抓取的“控点”，用于沿特定的轴缩放和旋转对象。
>注意：在将边界框添加到对象之前，首先需要在该对象上添加一个碰撞体（例如盒碰撞体）。前面在本课中我们已完成此任务。 可通过以下方式添加碰撞体：选择该对象，然后在该对象的检查器面板中选择“添加组件”>“盒碰撞体”。
>

1. 如果某个地核对象不包含盒碰撞体，请向其添加一个盒碰撞体（根据提供的说明，如果使用基础模块资产文件夹中的预制件，则无需添加盒碰撞体和进行设置）。处理地核时，需要将盒碰撞体添加到地核下的“node_id30”对象，如下图所示。 在对象的检查器选项卡中选择“node_id30”，单击“添加组件”，然后搜索“盒碰撞体”。 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> 注意：确保将盒碰撞体可视化，使其不会过大或过小。 其大小应与围绕它的对象（在本示例中为地核）大致相同。 可根据需要，在盒碰撞体中选择“编辑碰撞体”选项来调整盒碰撞体。 可以更改 x、y 和 z 值，或者在编辑器场景窗口中拖动边界框控点。 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 将边界框添加到地核的“node_id30”对象。 为此，请从“3DObjectCollection”中选择“node_id30”对象。 在检查器选项卡中，单击“添加组件”并搜索“边界框”。 确保边界框、盒碰撞体和操作脚本（操作处理程序、近距交互可抓取对象）都在同一个游戏对象中。

3.  在边界框的“行为”部分，从“激活”下拉列表中选择“启动时激活”。 若要查看有关各个激活选项和其他边界框选项的更多详细信息，请参阅 [MRTK 的边界框文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   在接下来的几个步骤中，我们还会通过调整默认的边界框材料、抓取时的材料以及控点的可视化效果（角和边的控点）来更改边界框的外观。  MRTK 包含多个用于自定义边界框的选项。

4. 在项目面板中搜索“boundingbox”，随后会在搜索结果中看到以蓝色球体指示的材料列表，如下图所示。 

5. 将“boundingbox”材料拖放到边界框组件上的边界框材料槽中。 另外，抓取“boundingboxgrabbed”材料，并将其放入边界框组件上的已抓取边界框材料槽中。

6. 将“MRTK_BoundingBox_ScaleWidget”材料拖放到边界框组件上的缩放控点预制件槽中。 

7. 将“MRTK_BoundingBox_RotateWidget”材料拖放到边界框组件上的旋转控点槽中。

![Lesson4 Chapter3 Step4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. 确保边界框针对适当的对象。 边界框组件中包含“目标对象”和“边界重写”脚本。 请确保将边界框环绕的对象拖放到这两个槽中。 在本示例中，请将“node_id30”对象拖放到这两个槽，如下图所示。

> 启动应用程序或在其中游戏时，该对象现在会由蓝框环绕。 可以放心拖动该框的四角，以调整对象的大小。 若要增大缩放控点和旋转控点的大小并使其更清晰，我们建议使用默认的边界框设置（不要执行步骤 4-7）。 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. 若要恢复默认的边界框可视化效果，请在边界框对象的检查器面板中，选择旋转控点预制件并按 Delete 键，随后会看到下图所示的边界框可视化效果。 注意：边界框可视化效果仅在游戏模式下显示。

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>添加触摸效果
本示例将在用手触摸某个对象时播放一段音效。

1. 将音频源组件添加到游戏对象。 在场景层次结构中选择“八面体”对象。 在检查器面板中单击“添加组件”按钮，搜索并选择“音频源”。 在稍后的步骤中，我们将使用此音频源播放音效。 

>注意：确保“八面体”对象包含一个盒碰撞体。

2. 添加“近距交互可触摸对象”组件。 在检查器面板中单击“添加组件”按钮，然后搜索“近距交互可触摸对象”。 选择该对象以将它添加到组件。 注意：需要修正屏幕截图，以突出显示我们要添加组件，并不仅仅是突出显示盒碰撞体。

>注意：前面我们已经添加了“近距交互可抓取对象”。 此对象与“近距交互可触摸对象”之间的差别在于，“可抓取”交互适用于要抓取和交互的对象。 “可触摸”组件适用于要触摸的对象。 可以结合使用这两个组件以实现组合式交互。

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. 加入“手动交互触摸”脚本。 请注意，此脚本已包含在连同此演示包一起导入的 unity 场景中，但未包含在原始 MRTK 中。 与在上一步骤中一样，单击“添加组件”并搜索“手动交互触摸”，以添加该脚本。 
   请注意，该脚本包含 3 个选项： 

   - “触摸完成时”。 触摸并释放对象时会触发此操作。 
   - “开始触摸时”。 触摸对象时会触发此操作。 
   - “更新触摸时”。 用手触摸对象时，会定期触发此操作。 

   对于本示例，我们将使用“开始触摸时”设置。

4. 在“开始触摸时”选项中单击“+”按钮，如下图所示。 将八面体对象拖放到空字段。 

5. 在带有“无函数”字样的下拉列表中（如上图中的绿色矩形所示），选择“AudioSource”>“PlayOneShot”。 使用以下概念将一个音频剪辑添加到此字段：

   - MRTK 提供了一个简短的音频剪辑列表。 请在项目面板中随意浏览这些剪辑。 在“MixedRealityToolkit.SDK”文件夹下的“standard assets”文件夹中可以找到它们。 其中有一个“audio”文件夹包含了所有音频剪辑。
   - 对于本示例，我们将使用“MRTK_Gem”音频剪辑。 
   - 若要添加音频剪辑，只需将项目面板中所需的剪辑拖入检查器面板中的 AudioSource.PlayOneShot（在以上示例中带有绿框标记）。

   现在，当用户伸手触摸八面体对象时，会播放音频曲目“MRTK_Gem”。 触摸对象时，“手动交互触摸”脚本还会调整该对象的颜色。 

![Lesson4 Chapter4 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>祝贺 
在本课中，你已了解如何在网格集合中组织 3D 对象，以及如何使用近距交互（使用跟踪手直接抓取）和远距交互（使用视线或手部跟踪光线）操作 3D 对象（缩放、旋转和移动）。此外，你还了解了如何在 3D 对象的周围放置边界框，以及如何使用和自定义边界框上的变形器 (Gizmo)。 最后，你已了解如何在触摸对象时触发事件。

[下一课：高级输入](mrlearning-base-ch5.md)

