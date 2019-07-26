---
title: MR 学习基础模块 - 3D 对象交互
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 314af3e1e38e1698943f07dc32f5e1e3e2f36d4f
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485702"
---
# <a name="5-interacting-with-3d-objects"></a>5.与三维对象交互

在本教程中, 我们将了解基本的3D 内容和用户体验。 我们将了解: 
* 将三维对象组织为集合的一部分。
* 基本操作的边界框。
* 近和远交互。
* 通过手动跟踪触摸和抓取手势。 

## <a name="objectives"></a>目标

* 了解如何通过 MRTK 的网格对象集合来组织3D 内容
* 实现边界框
* 为基本操作配置3D 对象--移动、旋转和缩放
* 探索近距和远距交互
* 了解其他手动跟踪手势, 如抓取和触摸

## <a name="instructions"></a>说明

### <a name="organizing-3d-objects-in-a-collection"></a>在集合中组织 3D 对象

1. 右键单击层次结构, 然后选择 "创建空"。 这会创建一个空游戏对象。 将其重命名为3DObjectCollection。 我们的所有 3D 对象将放入其中。 确保集合的位置设置为 x = 0，y = 0，z = 0。

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. 使用与在[学习](mrlearning-base-ch1.md)中概述的自定义包相同的说明导入 BaseModule 资产。 本教程中使用的 BaseModule 资产包括3D 模块和其他有用的脚本。 可在此处找到 BaseModule Unity 包:<https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. 可根据旁边的蓝色立方体识别咖啡杯预制件。 请勿选择蓝色立方体和小白色纸张, 因为这表示原始3D 模型而不是 prefab。) 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. 将所选的 "咖啡杯" prefab 拖到步骤1中的 "3DObjectCollection 游戏" 对象。 现在，该咖啡杯是集合的子级。

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. 接下来，将更多的 3D 对象添加到场景中。 下面是要在本示例中添加的对象列表。 添加对象时, 可能会发现它们以各种大小显示在场景中。 调整检查器面板中 "转换" 设置下每个三维模型的比例。 下面列出了本示例中各个对象的建议调整大小。 在 "项目" 面板的 "搜索" 框中搜索这些字词, 然后将3D 对象 prefab 拖动到类似于上一步的3DObjectCollection 对象中。 你将在资产 > BaseModuleAssets > 基本模块 Prototyping 中找到这些 prototyping 集合
- 搜索 TheModule_BaseModuleIncomplete。 将其拖到场景中。 将坐标设置为 x = 0.03，y = 0.03，z = 0.03。 
- 搜索 Octa_BaseModuleIncomplete。 将其拖到场景中。 将坐标设置为 x = 0.13， y = 0.13，z =0.13。
- 搜索 EarthCore_BaseModuleIncomplete。 将其拖到场景中。 将坐标设置为 x = 50.0，y = 50.0，z = 50.0。
- 搜索 Cheese_BaseModuleIncomplete。 将其拖到场景中。 将坐标设置为 x = 0.05，y = 0.05，z = 0.05。
- 搜索 Model_Platonic_BaseModuleIncomplete。 将其拖到场景中。 将坐标设置为 x = 0.13，y = 0.13，z = 0.13。

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. 将三个多维数据集添加到场景中。 右键单击 "3DObjectCollection" 对象, 选择 "3D 对象", 然后选择 "多维数据集"。 将坐标设置为 x = 0.14，y = 0.14，z = 0.14。 重复此步骤两次, 以创建总计三个多维数据集。 或者, 可以复制多维数据集两次, 共三个多维数据集。 也可以选择使用“资产”>“基础模块资产”>“基础模块预制件”中三个已准备好的立方体预制件，并选择“GreenCube_BaseModuleIncomplete”、“BlueCube_BaseModuleIncomplete”和“OrangeCube_BaseModuleIncomplete”。

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. 参考[第 2 课](mrlearning-base-ch2.md)中所述的过程，使用 MRTK 的网格对象集合组织对象集合，以构成一个网格。 请参考下图，其中通过一个示例演示了如何在 3x3 网格中配置对象。

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>注意:你可能会注意到, 某些对象处于中间中心, 如上图中的对象。 这是因为，预制件或对象可能包含未对齐的子对象。 请对对象位置或子对象位置进行任何必要的调整，以获得适当对齐的网格。


### <a name="manipulating-3d-objects"></a>操作 3D 对象
1. 添加操作立方体的功能。 若要添加操作3D 对象的功能, 请执行以下操作:
-   选择要在层次结构中操作的3D 对象, 即您的某个多维数据集。
-   单击 "添加组件"。 
-   搜索操作。
-   选择 "操作处理程序"。
-   对3DObjectCollection 对象下的所有3D 对象重复此操作, 而不是3DObjectCollection 本身。
-   确保所有三维对象都具有碰撞器或盒碰撞器 (添加组件 > 框碰撞器)。

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>操作处理程序是一个组件, 可用于调整对象在操作时的行为方式的设置。 这包括在特定轴上进行旋转、缩放、移动和约束移动。 

2. 请限制一个立方体，以便只能对它进行缩放。 选择3DObjectCollection 对象中的一个多维数据集。 在 "检查器" 面板中, 在 "两种操作类型" 旁单击下拉菜单, 然后选择 "缩放"。 这样，用户只能更改该立方体的大小。

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 更改每个立方体的颜色，以便可以区分它们。 
-   请访问 "项目" 面板并向下滚动, 直到看到 "MixedRealityToolkit", 然后选择它。
-   选择 "标准资产" 文件夹。
-   单击 "材料" 文件夹。
-   将不同的材料拖放到每个立方体上。 

>注意:可为立方体选择任意颜色。 对于我们的示例, 我们将使用 glowingcyan、glowingorange 和绿色。 请随意尝试不同的颜色。 若要将颜色添加到多维数据集, 请单击想要更改的多维数据集, 然后将该材料拖到多维数据集的 "检查器" 面板中的 "网格呈现器" 材料字段。 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. 选择3DObjectCollection 对象中的其他多维数据集, 然后将其移动限制为固定距离。 为此, 请在 "移动" 标签上的 "约束" 右侧单击下拉菜单, 然后选择 "修复距离"。 这样，用户只能在其视野范围中移动该立方体。 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

接下来的几个步骤的目标是启用抓取并与我们的3D 对象进行交互, 并应用不同的操作设置。

5. 选择奶酪对象, 并单击 "检查器" 面板中的 "添加组件"。 

6. 在搜索框中搜索近交互 Grabbable, 并选择该脚本。 此组件使用户可以通过跟踪的手访问和吸引对象。 对象也可以从远处操作, 除非在下图中以绿色圆圈表示的 "允许远操作" 复选框未被选中。

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 通过对这些对象重复步骤5和步骤 6, 将近交互 Grabbable 添加到八对象、Platonic 对象、地球核心、农历和咖啡杯。

8. 从八面体对象中删除远距操作功能。 为此, 请在层次结构中选择 "八", 并取消选中 "允许远端操作" 复选框 (由绿色圆圈标记)。 这样，用户只能使用跟踪手来直接与八面体交互。

>注意:有关操作处理程序组件及其相关设置的完整文档，请参阅 [MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。

9. 确保将近交互 Grabbable 组件添加到了地球核心、农历模块和咖啡杯上 (请参见步骤 7)。

10. 对于农历模块, 请更改操作处理程序设置, 以使其围绕对象中心围绕近和远交互进行旋转, 如下图所示。

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11：对于地球核心, 将版本行为更改为 "无"。 这样做是为了使地球核心从用户的抓住中释放出来, 而不会继续移动。 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> 注意:在创建可投射的球等场景中，可以使用此设置。 通过保持速度和角度速度, 使其成为一种球后, 它将继续以其释放速度的速度移动, 类似于物理球的行为方式。

### <a name="adding-bounding-boxes"></a>添加边界框
使用边界框可以更方便、更直观地单手操作对象，它支持定向操作（近距交互）和基于光线的操作（远距交互）。边界框提供可用于沿特定轴缩放和旋转对象的句柄。
>注意:在将边界框添加到对象之前, 您首先需要在该对象上创建一个碰撞器 (例如, 盒碰撞器), 就像我们在本课前面介绍的那样。 可通过以下方式添加碰撞体：选择该对象，然后在该对象的检查器面板中选择“添加组件”>“盒碰撞体”。
>

1. 如果地球核心对象尚不存在, 请将其添加到地球核心对象。 如果根据给定的说明使用基本模块资产文件夹中提供的 prefab, 则不需要使用框碰撞器和设置。 对于地球核心, 我们将 box 碰撞器添加到了地球核心下的、node_id30 的对象中, 如下图所示。 从对象的 "检查器" 选项卡中选择 "node_id30", 单击 "添加组件", 然后搜索 box 碰撞器。 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> 注意:请确保将框碰撞器的大小设置为不太大或太小。 其大小应与围绕它的对象（在本示例中为地核）大致相同。 通过选择框碰撞器中的 "编辑碰撞器" 选项, 根据需要调整框碰撞器。 您可以更改 x、y 和 z 值, 也可以在编辑器场景窗口中拖动边界框处理程序。 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 将边界框添加到地球核心的 node_id30 对象。 为此, 请从 "3DObjectCollection" 中选择 "node_id30" 对象。 在 "检查器" 选项卡中, 单击 "添加组件", 然后搜索 "边界框"。 确保边界框、盒碰撞体和操作脚本（操作处理程序、近距交互可抓取对象）都在同一个游戏对象中。

3.  在 "边界框的行为" 部分中, 从 "激活" 下拉列表中选择 "开始时激活"。 若要查看有关各个激活选项和其他边界框选项的更多详细信息，请参阅 [MRTK 的边界框文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *在接下来的几个步骤中, 我们还将通过以下方式更改边界框的显示方式: 调整默认的框材料、在其被抓取时的材料以及角部和侧图柄的可视化。* MRTK 包含多个用于自定义边界框的选项。

4. 在 "项目" 面板中搜索 "boundingbox", 并在搜索结果中看到一个蓝色球体表示的材料列表, 如下图所示。 

5. 将 boundingbox 材料拖动到边界框组件上的盒材料槽。 同时, 抓住 boundingboxgrabbed 材料, 并将其放在边界框组件上的 "将材料槽" 框中。

6. 将 MRTK_BoundingBox_ScaleWidget prefab 拖到边界框组件上的刻度控点 prefab 槽。 

7. 将 MRTK_BoundingBox_RotateWidget prefab 拖到 "捆绑箱" 组件上的旋转控点槽。

![Lesson4 Chapter3 Step4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. 确保边界框针对适当的对象。 在边界框组件中, 有目标对象和边界替代脚本。 请确保将边界框环绕的对象拖放到这两个槽中。 在此示例中, 将 node_id30 对象拖到这两个槽, 如下图所示。

> 启动或播放应用程序时, 对象将被蓝色框架括起来。 可以放心拖动该框的四角，以调整对象的大小。 如果希望缩放控点更大且更可见, 则建议使用默认边界框设置 (避免步骤4到7。) 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. 若要返回到默认边界框可视化效果, 请在边界框的对象的检查器面板中, 选择旋转控点 prefab 并按 Delete。 你将看到与下图类似的边界框可视化。 注意：边界框可视化效果仅在游戏模式下显示。

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>添加触摸效果
本示例将在用手触摸某个对象时播放一段音效。

1. 将音频源组件添加到游戏对象。 选择场景层次结构中的八对象。 在检查器面板中, 单击 "添加组件" 按钮, 搜索并选择 "音频源"。 在稍后的步骤中，我们将使用此音频源播放音效。 

>注意:确保八对象上有一个框碰撞器。

2. 添加 Near 交互可触摸组件。 单击 "检查器" 面板中的 "添加组件" 按钮, 然后搜索 near 交互可触摸。 选择该对象以将它添加到组件。 

>注意:以前, 我们添加了近交互 grabbable。 此交互和近交互可触摸之间的区别在于, grabbable 交互适用于要进行抓取和交互的对象。 可触摸组件适用于要接触的对象。 可以结合使用这两个组件以实现组合式交互。

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. 添加手交互触摸脚本。 请注意, 此脚本包含在作为此演示的一部分导入的 Unity 场景中, 并不包含在原始 MRTK 中。 与上一步一样, 单击 "添加组件", 然后搜索 "手交互触摸" 进行添加。

>请注意, 此脚本有三个选项: 

>   - On Touch 完成:触摸并释放对象时触发
>   - 开始时:接触对象时触发
>   - 更新时:在您的手中触摸对象时定期触发

>   在此示例中, 我们将使用 "按下开始使用" 设置。

4. 单击 "按下 Touch 开始" 选项上的 "+" 按钮, 如下图所示。 将八对象拖到空字段。 

5. 在未显示 "函数 (位于下图中的绿色矩形上方)" 的下拉框中, 选择 "AudioSource-> PlayOneShot"。 使用以下概念将一个音频剪辑添加到此字段：

   - MRTK 提供了一个简短的音频剪辑列表。 请在项目面板中随意浏览这些剪辑。 你将在 MixedRealityToolkit 文件夹下找到它们, 然后在 "标准资产" 文件夹下找到。 此时会显示音频文件夹, 其中包含所有音频剪辑。
   - 在此示例中, 我们将使用 MRTK_Gem 音频剪辑。 
   - 若要添加音频剪辑，只需将项目面板中所需的剪辑拖入检查器面板中的 AudioSource.PlayOneShot（在以上示例中带有绿框标记）。

   现在, 当用户到达并触及八对象时, 将播放音频轨 MRTK_Gem。 触摸时, 手动交互触摸脚本还会调整对象的颜色。 

![Lesson4 Chapter4 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

## <a name="congratulations"></a>祝贺 
在本教程中, 您学习了如何在网格集合中组织3D 对象, 以及如何使用接近的交互 (直接捕获到手) 和远距离交互 (使用看片或手写光线) 来操作三维对象 (缩放、旋转和移动)。 还了解了如何在三维对象周围添加边界框, 并了解了如何使用和自定义边界框中的 gizmos。 最后，你已了解如何在触摸对象时触发事件。

[下一课：6.探索高级输入选项](mrlearning-base-ch5.md)

