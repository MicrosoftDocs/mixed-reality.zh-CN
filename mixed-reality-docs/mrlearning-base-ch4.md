---
title: 入门教程 - 5. 与 3D 对象交互
description: 了解基本的3D 内容和用户体验，例如，如何组织 3D 对象，以及如何使用边界框执行基本操作。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b807ac7e51e4009d2c44d3b7c67fbdf3488ccbd9
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604988"
---
# <a name="5-interacting-with-3d-objects"></a>5.与 3D 对象交互

本教程介绍基本的 3D 内容和用户体验，例如，将 3D 对象组织为集合的一部分、用于执行基本操作的边界框、近距和远距交互，以及结合手动跟踪的触摸和抓取手势。

## <a name="objectives"></a>目标

* 创建用于其他学习目标的 3D 对象面板
* 实现边界框
* 配置用于基本操作（例如移动、旋转和缩放）的 3D 对象
* 探索近距和远距交互
* 了解其他手动跟踪手势，例如抓取和触摸

## <a name="importing-the-tutorial-assets"></a>导入教程资产

下载并导入 Unity 自定义包：

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)

导入教程资产后，“项目”窗口应如下所示：

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)中的说明。

## <a name="decluttering-the-scene-view"></a>整理场景视图

为了更轻松地在场景中操作，请单击“Cube”和“ButtonCollection”对象左侧的**眼睛**图标，将这些对象的**场景可见性**设置为关闭。   这会在“场景”窗口中隐藏这些对象，但在游戏中不会改变其可见性：

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> 若要详细了解“场景可见性”控件以及如何使用它们来优化场景视图和工作流，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">场景可见性</a>文档。

## <a name="organizing-3d-objects-in-a-collection"></a>在集合中组织 3D 对象

在本部分，你将创建 3D 对象的面板。在本教程的后续部分，你将使用此面板来探索与 3D 对象交互的各种方式。 具体而言，要将 3D 对象配置为定位在 3x3 网格中。

要执行的主要步骤类似于[创建按钮面板](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)，包括：

1. 将 3D 对象设为父对象的父级
2. 添加并配置“网格对象集合(脚本)”组件

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1.将 3D 对象设为父对象的父级

在“层次结构”窗口中**创建一个空对象**，为其指定适当的名称（例如 **3DObjectCollection**），并将其定位在适当的位置，例如 X = 0，Y = -0.2，Z = 2。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”，然后将以下预制件设为 **3DObjectCollection** 的**父级**：   

* Cheese
* CoffeeCup
* EarthCore
* Octa
* Platonic
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

在“层次结构”窗口中，**创建三个立方体**作为 **3DObjectCollection** 的子对象，并将其变换**标度**设置为 X = 0.15，Y = 0.15，Z = 0.15：

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> 有关如何执行上述步骤的提示，可参阅[创建用户界面并配置混合现实工具包](mrlearning-base-ch2.md)教程。

重新定位立方体，以便可以看到每个立方体：

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

在“项目”窗口中，导航到“资产” > “MixedRealityToolkit.SDK” > “StandardAssets” > “材料”查看 MRTK 随附的材料。    

单击某个合适的材料并将其拖放到每个立方体的网格渲染器“材料”元素 0 属性，例如：  

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2.添加并配置“网格对象集合(脚本)”组件

将“网格对象集合(脚本)”组件添加到“3DObjectCollection”对象，并按如下所述配置该组件：  

* 将“排序类型”更改为“子级顺序”，确保按照子对象在父对象下的放置顺序对子对象进行排序  

然后单击“更新集合”按钮以应用新配置： 

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>操作 3D 对象

在本部分，你将添加所需的功能，以便在上一部分创建的面板中操作所有 3D 对象。 此外，对于预制件对象，可让用户使用跟踪手来接触和抓取这些对象。 然后，探索一些可应用于对象的操作行为。

若要实现此目的，请执行以下主要步骤：

1. 将“操作处理程序(脚本)”组件添加到所有对象
2. 将“近距交互可抓取对象(脚本)”组件添加到预制件对象
3. 配置“操作处理程序(脚本)”组件

> [!IMPORTANT]
> 若要**操作某个对象**，该对象必须具有以下组件：
>
> * “碰撞体”组件，例如盒碰撞体 
> * “操作处理程序(脚本)”组件 
>
> 若要使用跟踪手**操作**和**抓取某个对象**，该对象必须具有以下组件：
>
> * “碰撞体”组件，例如盒碰撞体 
> * “操作处理程序(脚本)”组件 
> * “近距交互可抓取对象(脚本)”组件 

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1.将“操作处理程序(脚本)”组件添加到所有对象

在“层次结构”窗口中选择“Cheese”对象，在按住 **Shift** 键的同时选择“Cube () 2”对象，然后将“操作处理程序(脚本)”组件添加到所有对象：   

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> 在本教程中，碰撞体已添加到预制件中。 对于 Unity 基元（例如 Cube 对象），创建对象时会自动添加碰撞体组件。 在上图中，碰撞体由绿色外框表示。 若要详细了解碰撞体，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞体</a>文档。

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2.将“近距交互可抓取对象(脚本)”组件添加到预制件对象

在“层次结构”窗口中选择“Cheese”对象，在按住 **Shift** 键的同时选择“TheModule”对象，然后将“近距交互可抓取对象(脚本)”组件添加到所有对象：   

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3.配置“操作处理程序(脚本)”组件

#### <a name="default-manipulation"></a>默认操作

对于“Cube”对象，请将所有属性保留默认值，以体验默认的操作行为： 

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> 若要将某个组件重置为其默认值，可以选择该组件的“设置”图标，然后选择“重置”。

#### <a name="restrict-manipulation-to-scale-only"></a>将操作限制为缩放

对于“Cube (1)”对象，请将“双手操作类型”更改为“缩放”，以便仅允许用户更改对象的大小：   

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>将用户运动范围约束为固定的距离

对于“Cube (2)”对象，请将“运动约束”更改为“与头部之间的固定距离”，以便在移动该对象时，它与用户保持相同的距离：   

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>默认的可抓取对象操作

对于“Cheese”，“CoffeCup”和“EarthCore”对象，请将所有属性保留默认值，以体验默认的可抓取对象操作行为：   

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>删除远距操作功能

对于“Octa”对象，请取消选中“允许远距操作”复选框，使用户只能直接通过跟踪手来与该对象交互：  

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>使对象围绕中心旋转

对于“Platonic”对象，请将“近距单手旋转模式”和“远距单手旋转模式”更改为“围绕对象中心旋转”，以便在用户单手旋转该对象时，该对象围绕其中心旋转：    

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>释放对象后保持运动

对于“TheModule”对象，请添加一个 **Rigidbody** 组件以启用物理学，然后取消选中“使用重力”复选框，使该对象不受重力的影响：  

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

返回到“操作处理程序(脚本)”组件，检查“释放行为”是否同时设置为“保持速度”和“保持角速度”，以便在从用户手中释放对象后，该对象会继续运动：   

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

若要详细了解“操作处理程序”组件及其相关属性，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[操作处理程序](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)指南。

## <a name="adding-bounding-boxes"></a>添加边界框

边界框提供用于缩放和旋转的控点，在近距和远距交互时，使用边界框可以更轻松、更直观地单手操作对象。

此示例将一个边界框添加到 EarthCore 对象，以便可以使用在上一部分中配置的对象操作来与此对象交互，并使用边界框控点来缩放和旋转此对象。

> [!IMPORTANT]
> 若要使用**边界框**，对象必须具有以下组件：
>
> * “碰撞体”组件，例如盒碰撞体 
> * “边界框(脚本)”组件 

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1.将“边界框(脚本)”组件添加到 EarthCore 对象

在“检查器”窗口中选择“EarthCore”对象，然后将“边界框(脚本)”组件添加到 EarthCore 对象：  

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> 边界框可视化效果是在运行时创建的，因此在进入“游戏”模式之前不可见。

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2.使用编辑器中的模拟功能可视化和测试边界框

按“播放”按钮进入“游戏”模式。 长按空格键显示手形光标，然后使用鼠标来与边界框交互：

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

若要详细了解“边界框”组件及其相关属性，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[边界框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)指南。

## <a name="adding-touch-effects"></a>添加触摸效果

此示例启用在用手触摸对象时要触发的事件。 具体而言，你将配置 Octa 对象，以便在用户触摸它时播放声音效果。

若要实现此目的，请执行以下主要步骤：

1. 将“音频源”组件添加到对象
2. 将“近距交互可触摸对象(脚本)”组件添加到对象
3. 将“手动交互触摸(脚本)”组件添加到对象
4. 实现 On Touch Started 事件
5. 使用编辑器中的模拟功能测试触摸交互

> [!IMPORTANT]
> 若要**触发触摸事件**，对象必须具有以下组件：
>
> * “碰撞体”组件，最好是盒碰撞体 
> * “近距交互可触摸对象(脚本)”组件 
> * “手动交互触摸(脚本)”组件 

> [!NOTE]
> MRTK 中未包含“手动交互触摸(脚本)”组件。 它已连同本教程的资产一起导入，最初包含在混合现实工具包 Unity 示例中。

### <a name="1-add-an-audio-source-component-to-the-object"></a>1.将“音频源”组件添加到对象

在“层次结构”窗口中选择“Octa”对象，将“音频源”组件添加到 Octa 对象，然后将“空间混合”更改为 1，以启用空间音频：   

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2.将“近距交互可触摸对象(脚本)”组件添加到对象

在仍选中了“Octa”对象的情况下，将“近距交互可触摸(脚本)”组件添加到 Octa 对象，然后单击“拟合边界”和“拟合中点”按钮，以更新“近距交互可触摸(脚本)”组件的“局部中点”和“边界”属性，使之与 BoxCollider 匹配：    

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3.将“手动交互触摸(脚本)”组件添加到对象

在仍选中了“Octa”对象的情况下，将“手动交互触摸(脚本)”组件添加到 Octa 对象：  

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4.实现 On Touch Started 事件

在“手动交互触摸(脚本)”组件中，单击 **+** 小图标创建新的 **On Touch Started ()** 事件。  然后将“Octa”对象配置为接收该事件，并将“AudioSource.PlayOneShot”定义为要触发的操作：  

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

导航到“资产” > “MixedRealityToolkit.SDK” > “StandardAssets” > “音频”以查看 MRTK 随附的音频剪辑，然后将适当的音频剪辑（例如 MRTK_Gem 音频剪辑）分配到“音频剪辑”字段：     

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> 有关如何实现事件的提示，可参阅[手动跟踪手势和可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)中的说明。

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5.使用编辑器中的模拟功能测试触摸交互

按“播放”按钮进入“游戏”模式。 长按空格键显示手形光标，然后使用鼠标触摸 Octa 对象并触发声音效果：

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> 如上图所示，在测试触摸交互时，Octa 对象的颜色会有节律性地变化。 此效果已在“手动交互触摸(脚本)”组件中硬编码，而与前面步骤中完成的事件配置无关。
>
> 若要禁用此效果，可以执行相应的操作，例如，注释掉第 32 行“TargetRenderer = GetComponentInChildren<Renderer>();”，使 TargetRenderer 保持为 null，这样颜色就不会呈节律性的变化。

## <a name="congratulations"></a>祝贺

在本教程中，你已了解如何在网格集合中组织 3D 对象，以及如何使用近距交互（使用跟踪手直接抓取）和远距交互（使用视线或手部射线）操作这些对象（缩放、旋转和移动）。 此外，你还了解了如何在 3D 对象的周围放置边界框，以及如何使用和自定义边界框上的控点。 最后，你已了解如何在触摸对象时触发事件。

[下一课：6.探索高级输入选项](mrlearning-base-ch5.md)
