---
title: 使用手指向和提交
description: 指向和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实、交互、设计、hololens、手、远、指向和提交
ms.openlocfilehash: 30f85d2bb455abab3a533e0a829b4fba8cea0a7a
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402380"
---
# <a name="point-and-commit-with-hands"></a>使用手指向和提交
用手指向和提交是一种输入模型，使用户对远处的 2D 内容和 3D 对象进行定位、选择和操作。 这种“远程”交互技术是混合现实所独有的，并不是人类与现实世界交互的自然方式。 例如，在超级英雄电影 X-Men  中，角色 [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) 能够伸出手去操控远处的对象。 这是人类在现实中无法做到的。 在 HoloLens (AR) 和混合现实 (VR) 中，我们赋予了用户这种神奇的力量，打破了现实世界的物理约束，不仅能让用户享受到全息内容的愉悦体验，还能让互动更加有效、高效。

## <a name="device-support"></a>设备支持

输入模型 | [HoloLens（第一代）](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [沉浸式头戴显示设备](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
使用手指向和提交 | ❌ 不支持 | ✔️ 推荐 | ✔️ 推荐

指向和提交（也称为远程手）是利用新的铰接式手跟踪系统的新功能之一。 该输入模型也是在沉浸式头戴显示设备上通过使用运动控制器的主要输入模式。

## <a name="hand-rays"></a>手部射线

在 HoloLens 2 上，我们创造了一种从手掌中心射出的手部射线。 该射线被视为手的延伸。 圆环形光标连接到射线的末端，以指示射线与目标对象相交的位置。 然后光标所指向的对象可以接收来自手的手势命令。

通过使用拇指和食指执行隔空敲击动作来触发该基本手势命令。 通过使用手射线指向和隔空敲击以提交，用户可以激活 Web 内容上的按钮或超链接。 借助更多的复合手势，用户可以在 Web 内容中导航，并从远处操纵 3D 对象。 手部射线的视觉设计也应对这些指向和提交状态做出反应，如下所述： 

* 在指向状态下，射线是虚线，光标是圆环形状  。
* 在提交状态下，光线变为实线，光标缩小为点  。

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>在远近之间转换

我们没有使用特定的手势（如“用食指指向”来引导射线），而是设计了射线从手掌中心发出，留出五根手指来做更多的操控性手势，如捏和抓。 通过这种设计，我们只创建了一个心理模型，支持远近交互使用完全相同的一组手势。 可以使用相同的抓取手势来操纵不同距离的对象。 射线的调用是自动的，基于邻近度：

*  当对象在手臂可达距离（大约 50 cm）内时，射线会自动关闭，支持近距离交互。
*  当对象距离超过 50 cm 时，将启用射线。 转换应该顺利无缝。

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>2D 平板电脑交互

2D 平板电脑是装有 Web 浏览器等 2D 应用内容的全息容器。 与 2D 平板电脑进行远距离交互的设计理念是使用手部射线进行瞄准，并隔空敲击以进行选择。 在用手部射线瞄准目标后，用户可以通过隔空敲击来触发超链接或按钮。 他们可以用一只手“隔空敲击并拖动”来上下滚动平板电脑内容。 使用两只手进行隔空敲击和拖动的相对运动可以放大和缩小平板电脑内容。

在角落和边缘处瞄准手部射线可显示最接近的可视操作元素。 通过“抓取和拖动”可视操作元素，用户可通过边角可视操作元素执行统一的缩放，然后通过边缘可视操作元素重排平板电脑。 抓取并拖动 2D 平板电脑顶部的 holobar 可移动整个平板电脑。

![](images/2D-Slate-Interaction-Far-720px.jpg)

操作 2D 平板电脑本身：<br>

* 用户在角落或边缘处指向手部射线可显示最接近的可视操作元素。 
* 通过对可视操作元素应用操作手势，用户可通过边角可视操作元素执行统一的缩放，然后通过边缘可视操作元素重排平板电脑。 
* 通过在 2D 平板电脑顶部的 holobar 上应用操纵手势，用户可以移动整个平板电脑。<br>

<br>

## <a name="3d-object-manipulation"></a>3D 对象操作

在直接操作中，用户可以通过两种方式操纵 3D 对象，基于可视操作元素的操作和不基于可视操作元素的操作。 在指向和提交模型中，用户能够通过手部射线实现完全相同的任务。 不需要额外的学习。<br>

### <a name="affordance-based-manipulation"></a>基于可视操作元素的操作
用户使用手部射线指向并显示边框和可视操作元素。 用户可在边框上应用操作手势来移动整个对象，在边缘可视操作元素上应用操作手势来旋转对象，以及在边角可视操作元素上应用操作手势以进行统一的缩放。 <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>不基于可视操作元素的操作
用户用手部射线指向以显示边界框，然后直接对其应用操作手势。 如果用一只手进行操作，对象的平移和旋转将与手的移动和方向相关联。 如果用两只手进行操作，用户可以根据两只手的相对运动来平移、缩放和旋转对象。<br>

<br>

## <a name="instinctual-gesturers"></a>本能手势
指向和提交的本能手势的概念类似于直接操作的概念。 用户应在 3D 对象上执行的手势是由 UI 可视操作元素的设计指导的。 例如，一个小的控制点可能会促使用户用拇指和食指捏，而用户可能想用所有 5 根手指抓一个较大的对象。

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>手部与 6 DoF 控制器之间的对称设计 
远程交互的指向和提交概念最初是为混合现实门户 (MRP) 创建和定义的，在混合现实门户中，用户戴上沉浸式头戴显示设备，通过运动控制器与 3D 对象进行交互。 运动控制器射出光线来指向和操纵远处的对象。 控制器上有用于进一步提交不同操作的按钮。 我们利用射线的交互模式，并将其与双手关联。 借助这种对称设计，熟悉 MRP 的用户在使用 HoloLen 2 时不需要学习另一种交互模式来进行远距离指向和操纵，反之亦然。    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>本能手势

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>另请参阅
* [头部凝视并提交](gaze-and-commit.md)
* [使用手直接操作](direct-manipulation.md)
* [本能交互](interaction-fundamentals.md)

