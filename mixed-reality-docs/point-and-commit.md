---
title: 点和提交模式以及实践
description: 点和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实，交互、 设计、 hololens、 手，到目前为止，点和提交
ms.openlocfilehash: e69c8ff2091beff7d8fbbde4e6f24d909302290a
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730805"
---
# <a name="point-and-commit-with-hands"></a>点和提交模式以及实践
点和提交模式以及实践是输入的模型，使用户能够为目标、 选择和操作在距离 2D 内容和三维对象。 此"得"交互方法仅适用于混合现实并不是方法人类自然地与现实世界的 intereact。 例如，在超级英雄电影*X 男士*，该字符[磁](https://en.wikipedia.org/wiki/Magneto_(comics))能够联系和操作中使用他的距离的延伸的范围对象。 这不是人类可以在现实中做的事情。 在 HoloLens (AR) 和混合现实 (VR) 中，我们做这神奇功能强大、 用户重大不仅可以具有很不一般吧体验 holographic 内容而且也更有效且高效进行交互的实际的物理约束。

## <a name="device-support"></a>设备支持

输入的模型 | [HoloLens （第 1 代）](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [沉浸式耳机](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
点和提交 （最手动交互） | 不支持的 ❌ | ✔️ 建议 | ✔️ 建议

点和提交，也称为手到目前为止，是利用新的明确的手动跟踪系统的新功能之一。 此输入的模型也是在通过动作控制器使用的沉浸式耳机主输入的模型。

## <a name="hand-rays"></a>手大气

在 HoloLens 2 上，我们将创建从中心 palm 投篮手 ray。 此 ray 视为手形图标的扩展。 圆环图形光标被附加到以指示目标对象与射线相交的位置的射线的末尾。 光标进入的对象然后可以从手接收动作命令。

通过使用拇指和食指来执行以无线方式点击操作触发此基本动作命令。 通过使用手形 ray 可以指向和提交空敲击，用户可以激活的按钮或 web 内容上的超链接。 使用多个复合手势，用户都能够导航 web 内容和操作三维对象一段距离。 手 ray 的可视设计应还应对这些点和提交的状态，如下所示： 

* 在中*指向*状态下，ray 是虚线，光标位于圆环图形状。
* 在中*提交*状态下，ray 将转变为一条实线，光标将缩小到一个点。

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>近和远之间进行转换

而不是使用特定手势，如"使用食指指向"若要指示射线，我们设计出从中心的手掌，释放并保留五个手指的多个操控手势，如捏合而获取的射线。 与此设计中，我们创建一个心理模型，支持一组完全相同的手势的近和远交互。 可以使用相同随取即行手势来处理不同距离处的对象。 射线的调用是自动和邻近基于：

*  在 arm 达到距离 (大约 50 cm) 对象时，将关闭射线自动鼓励近交互。
*  比 50 cm 对象时，会启用射线。 转换应顺畅、 无缝。

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>2D 盖板交互

2D 盖板是 holographic 容器托管 2D 应用内容，如 web 浏览器。 目前与 2D 平板式交互的设计概念是使用手大气目标和 air 点击选择。 面向使用手 ray 之后, 用户可以隔空敲击触发超链接或按钮。 他们可以使用一只手"空中点击和拖动"向上和向下滚动静态内容。 使用两只手空中点击和拖动的相对动作可以放大 in 和 out 静态内容。

面向手动射线边角上的显示最接近功能操作可见性:。 通过"随取即行并将"操作等，用户可以执行统一缩放通过角提示和可以重排通过边缘提供静态图像。 获取和拖动在 2D 静态图像的顶部 holobar 用户可以移动整个静态图像。

![](images/2D-Slate-Interaction-Far-720px.jpg)

用于操作 2D 平板本身：<br>

* 用户点的角部或边缘以显示最近操作功能可见性： 在手射线。 
* 通过功能可见性： 在应用操作手势，用户可以执行角功能可见性： 通过统一缩放和可以重排通过边缘功能可见性： 静态图像。 
* 通过在顶部的 2D 盖板 holobar 上应用操作手势，用户可以移动整个静态图像。<br>

<br>

## <a name="3d-object-manipulation"></a>三维对象操作

在直接操作，有两种用户操作三维对象、 功能可见性： 基于操作和非功能可见性： 基于的操作的方法。 在点和提交模型中，用户都是可达到手大气通过相同的任务。 不需要使用任何其他学习。<br>

### <a name="affordance-based-manipulation"></a>基于功能可见性： 的操作
用户使用手大气进行点，并且显示边界框和操作提供。 要移动整个对象的边界框、 边缘等旋转和上，用户可以应用操作手势 coner 均匀缩放的提示。 <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>非功能可见性： 基于操作
用手大气显示边界框，然后直接对其应用操作手势指向用户。 用一只手平移和旋转的对象将关联到动作和方向的分值。 使用两只手，用户可以转换、 缩放和旋转根据相对两只手的动作。<br>

<br>

## <a name="instinctual-gesturers"></a>Instinctual gesturers
点和提交 instinctual 手势的概念是类似于直接操作。 设计的 UI 提示将指导用户是假设三维对象上执行的笔势。 例如，一个小的控制点可能激励用户捏合用其拇指和食指，而用户可能想要获取使用所有 5 个手指的较大对象。

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>手和 6 DoF 控制器之间的对称设计 
最初，点和提交远端交互的概念已创建并定义为混合现实门户 (MRP)，其中用户戴沉浸式头戴式耳机，并与通过动作控制器三维对象进行交互。 运动控制器投篮机会控制在出大气指向和操作延伸的范围对象。 为进一步提交不同的操作在控制器上有一些按钮。 我们利用大气的交互模型，并附加到两只手。 使用此对称设计时，用户熟悉 MRP 用户无需了解得指向和操作的另一个交互模型，在使用 HoloLen 2 时，反之亦然。    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Instinctual 手势

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>请参阅
* [头部凝视并提交](gaze-and-commit.md)
* [使用手直接操作](direct-manipulation.md)
* [本能交互](interaction-fundamentals.md)

