---
title: 入门教程-5。 与三维对象交互
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130212"
---
# <a name="5-interacting-with-3d-objects"></a>5. 与三维对象交互

在本教程中，你将了解基本的3D 内容和用户体验，例如将3D 对象组织为集合的一部分、基本操作的边界框、近和远交互，以及使用手动跟踪触摸和获取手势。

## <a name="objectives"></a>目标

* 创建将用于其他学习目标的3D 对象面板
* 实现边界框
* 为基本操作（如移动、旋转和缩放）配置3D 对象
* 探索近距和远距交互
* 了解其他手动跟踪手势，如抓取和触摸

## <a name="importing-the-tutorial-assets"></a>导入教程资产

下载并导入 Unity 自定义包：

* [MRTK.HoloLens2. GettingStarted. 2.2.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

导入教程资产后，项目窗口应如下所示：

![mrlearning](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> 有关如何导入 Unity 自定义包的提醒，可以参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)说明。

## <a name="decluttering-the-scene-view"></a>Decluttering 场景视图

若要更轻松地使用场景，请通过单击对象左侧的**眼睛**图标将 Cube 和 ButtonCollection 对象的**场景可见性**设置为 off。 这将隐藏场景窗口中的对象，而无需更改其游戏中的可见性：

![mrlearning](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> 若要详细了解场景可见性控件以及如何使用它们来优化场景视图和工作流，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">场景可见性</a>文档。

## <a name="organizing-3d-objects-in-a-collection"></a>组织集合中的3D 对象

在本部分中，你将创建一个3D 对象面板，在本教程的以下部分中，你将使用此面板来浏览与3D 对象交互的各种方式。 具体来说，您需要将三维对象配置为置于 3 x 3 网格上。

类似于[创建按钮面板](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)时，执行此操作需要执行的主要步骤如下：

1. 将三维对象作为父对象的父级
2. 添加和配置网格对象集合（脚本）组件

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. 将3D 对象作为父对象的父级

在 "层次结构" 窗口中，**创建一个空的对象**，为其指定一个适当的名称（例如**3DObjectCollection**），并将其放置在合适的位置，例如 X = 0，Y =-0.2，Z = 2。

在项目窗口中，导航到 "**资产**" > **MRTK "。GettingStarted** > **prototyping**，然后将以下 Prototyping**父级**为**3DObjectCollection**：

* 比萨饼
* CoffeeCup
* EarthCore
* 八
* Platonic
* TheModule

![mrlearning](images/mrlearning-base/tutorial4-section3-step1-1.png)

在 "层次结构" 窗口中，**创建三个多维数据集**作为**3DObjectCollection**的子对象，并将其转换**比例**设置为 X = 0.15，Y = 0.15，Z = 0.15：

![mrlearning](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> 有关如何执行上述步骤的提醒，可以参阅[创建用户界面和配置混合现实工具包](mrlearning-base-ch2.md)教程。

重新定位多维数据集，以便可以查看每个多维数据集：

![mrlearning](images/mrlearning-base/tutorial4-section3-step1-3.png)

在 "项目" 窗口中，导航到 "**资产**" > " **MixedRealityToolkit** " > **STANDARDASSETS** > **材料**，查看 MRTK 提供的材料。

**单击并将**适当的材料拖到每个多维数据集的 "网格呈现器**材料**元素 0" 属性，例如：

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green：

![mrlearning](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. 添加和配置网格对象集合（脚本）组件

将**网格对象集合（脚本）** 组件添加到3DObjectCollection 对象，并按如下所示对其进行配置：

* 将**排序类型**更改为子级顺序，以确保子对象按照其置于父对象下的顺序进行排序

然后单击 "**更新集合**" 按钮应用新配置：

![mrlearning](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>操作三维对象

在本部分中，您将添加操作在上一节中创建的面板中的所有3D 对象的功能。 此外，对于 prefab 对象，用户可以通过跟踪来访问和获取这些对象。 然后，您将探索一些可应用于您的对象的操作行为。

为实现此目的需要执行的主要步骤如下：

1. 向所有对象添加操作处理程序（脚本）组件
2. 将 Near 交互 Grabbable （脚本）组件添加到 prefab 对象
3. 配置操作处理程序（脚本）组件

> [!IMPORTANT]
> 为了能够**操作对象**，对象必须具有以下组件：
>
> * **碰撞**器组件，例如，盒碰撞器
> * **操作处理程序（脚本）** 组件
>
> 若要能够**操作**并**抓住跟踪的对象**，对象必须具有以下组件：
>
> * **碰撞**器组件，例如，盒碰撞器
> * **操作处理程序（脚本）** 组件
> * **近交互 Grabbable （脚本）** 组件

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. 将操作处理程序（脚本）组件添加到所有对象

在 "层次结构" 窗口中，选择 "**奶酪**" 对象，按住**Shift**键，然后选择**Cube （）** 对象，并将**操作处理程序（脚本）** 组件添加到所有对象：

![mrlearning](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> 出于本教程的目的，colliders 已添加到 prototyping 中。 对于 Unity 基元（如 Cube 对象），创建对象时，会自动添加碰撞器组件。 在上面的图像中，colliders 表示为绿色的轮廓。 若要了解有关 colliders 的详细信息，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞</a>器文档。

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. 将 Near 交互 Grabbable （脚本）组件添加到 prefab 对象

在 "层次结构" 窗口中，选择 "**奶酪**" 对象，按住**Shift**键，然后选择 " **TheModule** " 对象，并将**Near 交互 Grabbable （脚本）** 组件添加到所有对象：

![mrlearning](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. 配置操作处理程序（脚本）组件

#### <a name="default-manipulation"></a>默认操作

对于**多维数据集**对象，请保留默认的所有属性，以体验默认操作行为：

![mrlearning](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> 若要将组件重置为其默认值，可以选择组件的 "设置" 图标，然后选择 "重置"。

#### <a name="restrict-manipulation-to-scale-only"></a>仅限缩放操作

对于**多维数据集（1）** 对象，将两个正在进行的**操作类型**更改为仅允许用户更改对象的大小：

![mrlearning](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>限制移动与用户的固定距离

对于**Cube （2）** 对象，更改**对移动的约束**以修复与 Head 的距离，以便在移动对象时，它将保持与用户相同的距离：

![mrlearning](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>默认 grabbable 操作

对于**奶酪**、 **CoffeCup**和**EarthCore**对象，请将所有属性都保留为默认值，以体验默认 grabbable 操作行为：

![mrlearning](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>消除远端操作的能力

对于**八**对象，请取消选中 "**允许远端操作**" 复选框，以便用户只能使用跟踪的指针直接与对象交互：

![mrlearning](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>使对象围绕中心旋转

对于**Platonic**对象，请将**一只手旋转模式**更改为近、**一只手旋转模式**，以围绕对象中心旋转，这样当用户用一只手旋转对象时，它就会围绕对象中心旋转：

![mrlearning](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a>在释放对象后阻止移动

对于**TheModule**对象，将**版本行为**更改为 "无"，以便一旦对象从用户的手中释放，就不会继续移动：

![mrlearning](images/mrlearning-base/tutorial4-section4-step3-7.png)

若要了解有关操作处理程序组件及其关联属性的详细信息，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[操作处理程序](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)指南。

## <a name="adding-bounding-boxes"></a>添加边界框

使用边界框，可通过提供可用于缩放和旋转的句柄，更轻松、更直观地处理对象，同时实现近乎交互和远距离交互。

在此示例中，您将向 EarthCore 对象添加一个边界框，以便现在可以使用您在上一节中配置的对象操作与进行交互，并使用边界框控点进行缩放和旋转。

> [!IMPORTANT]
> 若要能够使用**边界框**，对象必须具有以下组件：
>
> * **碰撞**器组件，例如，盒碰撞器
> * **边界框（脚本）** 组件

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. 将边界框（脚本）组件添加到 EarthCore 对象

在 "检查器" 窗口中，选择 " **EarthCore** " 对象，并将**边界框（脚本）** 组件添加到 EarthCore 对象：

![mrlearning](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> 边界框可视化效果是在运行时创建的，因此在进入游戏模式之前不可见。

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. 使用编辑器内模拟来可视化和测试边界框

按 "播放" 按钮进入游戏模式。 然后按住空格键以调出手，并使用鼠标与边界框进行交互：

![mrlearning](images/mrlearning-base/tutorial4-section5-step2-1.png)

若要详细了解边界框组件及其关联的属性，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的 "[边界框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)" 指南。

## <a name="adding-touch-effects"></a>添加触摸效果

在此示例中，你将允许在你用手触摸对象时触发事件。 具体来说，您将配置八对象，使其在用户接触时播放声音效果。

为实现此目的需要执行的主要步骤如下：

1. 向对象中添加音频源组件
2. 将 Near 交互可触摸（脚本）组件添加到对象
3. 将手写交互触摸（脚本）组件添加到对象
4. 实现 On Touch 已开始事件
5. 使用编辑器中的模拟测试触摸交互

> [!IMPORTANT]
> 为了能够**触发触控事件**，对象必须具有以下组件：
>
> * **碰撞**器组件，最好是盒碰撞器
> * **近交互可触摸（脚本）** 组件
> * **手动交互触摸（脚本）** 组件

> [!NOTE]
> 手动交互触摸（脚本）组件不是 MRTK 的一部分。 它已通过本教程的资产导入，最初是 MixedReality 工具包 Unity 示例的一部分。

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. 将音频源组件添加到对象

在 "层次结构" 窗口中，选择 "**八**" 对象，将 "**音频源**" 组件添加到八对象，然后将 "**空间混合**" 更改为1以启用空间音频：

![mrlearning](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. 将 Near 交互可触摸（脚本）组件添加到对象

在仍选择**八**对象的情况下，将**near 交互可触摸（脚本）** 组件添加到八对象，然后单击 "**修复边界**" 和 "**修复中心**" 按钮，更新接近交互可触摸（脚本）的局部中心和边界属性，使之与 BoxCollider 匹配：

![mrlearning](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. 将手形交互触摸（脚本）组件添加到对象

在仍选择**八**对象的情况下，将**手写交互触摸（脚本）** 组件添加到八对象：

![mrlearning](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. 实现 On Touch 已开始事件

在 "手动交互触摸（脚本）" 组件上，单击 "小 **+** " 图标以**在 "Touch 已启动（）"** 事件上创建新的。 然后配置**八**对象以接收事件，并将**AudioSource**定义为要触发的操作：

![mrlearning](images/mrlearning-base/tutorial4-section6-step4-1.png)

导航到 "**资产**" > **MixedRealityToolkit** " > **StandardAssets** >" 材料 "查看与 MRTK 一起提供的音频剪辑，然后将合适的音频剪辑分配到"**音频剪辑**"字段，例如 MRTK_Gem 音频剪辑：

![mrlearning](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> 有关如何实现事件的提醒，可参阅 "[手动跟踪手势" 和 "种不可交互" 按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)说明。

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. 使用编辑器内模拟测试触摸交互

按 "播放" 按钮进入游戏模式。 然后按住空格键以调出手，并使用鼠标来触摸八对象并触发声音效果：

![mrlearning](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> 正如上图中所示，在测试触摸屏交互时，八对象的颜色 pulsated。 此效果硬编码为手动交互触摸（脚本）组件，而不是上面步骤中完成的事件配置的结果。
>
> 如果要禁用此效果，则可以（例如，注释掉或第32行） "TargetRenderer = GetComponentInChildren<Renderer>（）;"，这将导致 TargetRenderer 剩余 null，并且颜色不 pulsating。

## <a name="congratulations"></a>祝贺你

在本教程中，您学习了如何在网格集合中组织3D 对象，以及如何使用接近的交互（直接抓取、旋转和移动）来处理这些对象（使用 "注视" 光线或手写光线）。 还了解了如何在三维对象周围放置边框，并了解了如何使用和自定义边界框中的句柄。 最后，你已了解如何在触摸对象时触发事件。

[下一课： 6. 浏览高级输入选项](mrlearning-base-ch5.md)
