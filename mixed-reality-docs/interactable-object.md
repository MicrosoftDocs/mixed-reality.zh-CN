---
title: 种交互的对象
description: 一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。 在三维混合的现实世界中，我们无需限制为抽象不再这个世界。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的现实、 控件、 交互、 ui 和 ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592221"
---
# <a name="interactable-object"></a>种交互的对象

一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。 在三维混合的现实世界中，我们无需限制为抽象不再这个世界。 可以是任何内容**种交互对象**触发事件。 种交互的对象可以表示为任何从上表杯咖啡到气球状飘浮在空中。 我们仍进行传统按钮在某些情况下此类如下所示对话框 UI 的使用。 按钮的可视表示形式取决于上下文。

![Interactible 对象英雄形象](images/640px-interactibleobject-hero-640px.jpg)


在中 **[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，我们创建了一系列的 Unity 脚本并将帮助你的预设创建种交互的对象。 可以使用这些来创建任何类型的对象，用户可与之交互，使用这些标准交互状态： 观察，针对，按下。 使用你自己的资产，可以轻松自定义的可视设计。 通过创建和分配相应的动画剪辑中 Unity 的动画控制器的交互状态，或者使用偏移量和规模，可以自定义详细的动画。 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a>有关不同输入的交互状态的可视反馈

混合现实中 holographic 对象相混合现实世界环境后，因为它可能会比较困难，了解这种交互的对象。 你的体验中的任何种交互对象，务必为每个输入状态提供独特的可视反馈。 这有助于用户了解您的体验的哪个部分是种交互，并使用户确信使用一致的交互方法。

任何对象的该用户可以与之交互，我们建议来具有不同的可视反馈，对于这三个输入状态：
* **观察**:对象的默认空闲状态。
* **目标**:当对象被指向附带的视线移动游标时，手指邻近或动画控制器的指针。
* **按下**:对象按下时使用-敲击手势、 手指按或运动控制器的选择按钮。

![Holographic 按钮](images/640px-interactibleobject-holographicbutton-650px.jpg)<br>
*观察状态，目标状态，并按下状态*

在 Windows Mixed Reality，可以找到的可视化开始菜单和应用程序栏按钮上的不同输入的状态的示例。 技术，如突出显示或缩放可用于提供给用户的输入状态的可视反馈。

在 HoloLens 2 中，因为它支持清楚的手动跟踪输入，我们可以提供基于手到邻近的其他提示。 [HoloLens 2 中的按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)显示了此示例。

![Pressable 按钮](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a>种交互的对象示例

### <a name="mesh-button"></a>网格按钮

![网格按钮](images/640px-interactibleobject-meshbutton.jpg)

这些是作为种交互对象中使用基元和导入三维网格之上的示例。 您可以轻松地分配不同的规模、 偏移量和颜色值，以响应每种输入的交互状态。

### <a name="toolbar"></a>工具栏

![工具栏](images/640px-interactibleobject-toolbar.jpg)

工具栏是混合的现实体验中的一种广泛使用的模式。 它是一个简单的按钮与其他行为集合如[Billboarding 和尾随](billboarding-and-tag-along.md)。 此示例使用从 MixedRealityToolkit Billboarding 和尾随的脚本。 您可以控制详细的行为包括距离，移动速度和阈值的值。

### <a name="traditional-button"></a>传统的按钮

![传统的按钮](images/640px-interactibleobject-traditionalbutton.jpg)

此示例演示一个传统的 2D 样式按钮。 每个输入的状态具有略有不同的深度和动画属性。

### <a name="other-examples"></a>其他示例

![下压按钮](images/640px-interactibleobject-pushbutton.jpg)<br>
*下压按钮*
<br>
![真实生活对象](images/640px-interactibleobject-reallifeobject.jpg)<br>
*现实生活对象*

与 HoloLens，您可以利用的物理空间。 假设物理墙上的 holographic 推送按钮。 或如何在实际表杯咖啡？ 使用导入从对软件建模的三维模型，我们可以创建类似于现实生活中对象的种交互对象。 由于它是一个数字的对象，我们可以向其添加神奇的交互。

## <a name="interactable-object-in-mixed-reality-toolkit"></a>混合现实工具包中的种交互对象
您可以找到[混合现实工具包中对象的 Interactable 示例](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)


## <a name="see-also"></a>请参阅
* [在混合的现实工具包 Unity pressable 按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [对象集合](object-collection.md)
* [公告板和尾随](billboarding-and-tag-along.md)
