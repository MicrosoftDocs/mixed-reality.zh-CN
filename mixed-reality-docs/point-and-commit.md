---
title: 点和提交
description: 点和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: 混合现实，交互设计
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581307"
---
# <a name="point-and-commit"></a>点和提交
点和提交是输入的模型，用户可以为目标、 选择和操作 2D 内容和三维对象的距离。 此"远处"交互方法是在它们与现实世界的日常交互期间当时的确没有人正在 navel 交互式体验。 例如，在超级英雄电影，磁是能够联系和处理通过手中距离的延伸的范围对象的但用户不能执行此操作在现实中。 在 Microsoft HoloLens (AR) 和 Microsoft 混合现实 (VR) 中，我们做用户这神奇的能力，重大的不只是为了重新燃烧全息版的内容，但若要使交互更高效现实世界的物理约束和高效。

## <a name="device-support"></a>设备支持
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>输入的模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
    </tr>
     <tr>
        <td>点和提交 （最手动交互）</td>
        <td>不支持的 ❌</td>
        <td>✔️ 建议</td>
        <td>✔️ 建议</td>
    </tr>
</table>
<br>
点和提交已在 HoloLens 2 上，利用新的明确的手跟踪系统的主要输入模型之一。 此输入的模型也是在通过动作控制器使用的沉浸式耳机主输入的模型。 点和提交是我们建议将 Head 注视输入的模型，在 HoloLens 上提交 （第 1 代）。 

## <a name="hand-rays"></a>手大气
在 HoloLens 2 上，我们创建手射线从 palm 中心排除。 Ray 将被视为手形图标的扩展。 圆环图形状光标被附加暗示 hitted 对象与射线相交的位置的射线的末尾。 光标进入的对象将手中接收动作命令。 

通过使用拇指和食指来执行以无线方式点击动作触发非常基本的动作命令。 通过使用手形 ray 可以指向和提交空敲击，用户可以激活的按钮或 web 内容上的超链接。 使用多个复合手势，用户都能够导航 web 内容和操作三维对象的距离。 手 ray 的可视设计还应该响应可以指向和提交状态： <br>
* 在指针的状态中，ray 是内联，短划线和光标是圆环图形状。
* 在提交状态，ray 将转变为一条实线，和光标缩小为一个点。<br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a>近和远之间进行转换
而不是使用特定手势，如使用索引手指离开屏幕直接射线，指向我们设计推出 palm，中心的射线释放和保留五个手指的动作的更多操作。 因此，HoloLens 2 支持一组完全相同的手势的近和远交互。 任何其他学习不需要时用户传输从靠近远端交互，反之亦然。 用户可以使用相同的握手势来处理不同距离处的对象。 射线的调用是自动和邻近基于： <br>
* 在 arm 达到距离 (大约 50 cm) 对象时，将关闭射线自动鼓励近交互。 
* 比 50 cm 对象时，会启用射线。

此机制可以顺畅、 无缝的过渡。<br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>2D 盖板交互
2D 盖板是 holographic 容器托管 2D 应用内容，如 web 浏览器。 目前与 2D 平板式交互的设计概念是使用手大气点并敲击提交。<br>

用来与盖板固定的交互：<br>

* 用户可以指向一个超链接或按钮，然后敲击来激活它。 
* 用户可以使用一只手来执行导航笔势向上和向下滚动静态内容。 
* 用户可以使用两只手来执行导航笔势来缩放和静态内容输出。<br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

用于操作 2D 平板本身：<br>

* 用户点的角部或边缘以显示最近操作功能可见性： 在手射线。 
* 通过功能可见性： 在应用操作手势，用户可以执行角功能可见性： 通过统一缩放和可以重排通过边缘功能可见性： 静态图像。 
* 通过在顶部的 2D 盖板 holobar 上应用操作手势，用户可以移动整个静态图像。<br>

<br>

## <a name="3d-object-manipulation"></a>三维对象操作
在直接操作，有两种用户操作三维对象功能可见性： 基于操作和非 affordnace 基于操作的方法。 在点和提交模型中，用户都是可达到手大气通过相同的任务。 不需要使用任何其他学习。<br>

### <a name="affordance-based-manipulation"></a>功能可见性： 基于操作
用户使用手大气进行点，并且显示边界框和操作提供。 要移动整个对象的边界框、 边缘等旋转和上，用户可以应用操作手势 coner 均匀缩放的提示。 <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>非功能可见性： 基于操作
用手大气显示边界框，然后直接对其应用操作手势指向用户。 用一只手平移和旋转的对象将关联到动作和方向的分值。 使用两只手，用户可以转换、 缩放和旋转根据相对两只手的动作。<br>

<br>

## <a name="instinctual-gesturers"></a>Instinctual gesturers
点和提交 instinctual 手势的概念是与同步，以便直接进行操作。 三维对象上执行笔势用户假设是引导式的设计的 UI 提示。 小控制点将激励用户捏合用拇指和食指，虽然大型对象使用户能够使用 5 个手指抓住。

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>手和 6 DoF 控制器之间的对称设计 
首先创建并定义为混合现实门户 (MRP)，其中用户 wear 沉浸式头戴式和 3d 物体运动控制器通过与之交互的远端交互点和提交模型的概念。 运动控制器投篮机会控制在出大气指向和操作延伸的范围对象。 为进一步提交不同功能在控制器上有一些按钮。 我们利用大气的交互模型，并将其附加两只手上。 使用此对称设计时，用户熟悉 MRP 用户无需了解得指向和首次使用 HoloLen 2 时的操作的另一个交互模型，反之亦然。    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a>请参阅
* [视线移动和提交](gaze-and-commit.md)
* [直接操作](direct-manipulation.md)
* [交互基础知识](interaction-fundamentals.md)
