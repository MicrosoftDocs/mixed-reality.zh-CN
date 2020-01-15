---
title: 使用手指向和提交
description: 指向和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 交互, 设计, HoloLens, 手, 远, 指向和提交
ms.openlocfilehash: d3f886fd8e892fe34116c3a1d601ae3a87d87a9b
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901531"
---
# <a name="point-and-commit-with-hands"></a>使用手指向和提交

![光标](images/UX/UX_Hero_HandRay.jpg)

“用手指向和提交”是一种输入模型，使用户对无法接触的 2D 内容和 3D 对象进行定位、选择和操作。 这种“远程”交互技术是混合现实所独有的，并不是人类与现实世界交互的自然方式。 例如，在超级英雄电影 *X-Men* 中，角色 [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) 能够伸出手去操控远处的对象。 这是人类在现实中无法做到的。 在 HoloLens (AR) 和混合现实 (MR) 中，我们赋予了用户这种神奇的力量，打破了现实世界的物理约束，不仅能让用户享受到全息内容的愉悦体验，还能让互动更加有效、高效。

## <a name="device-support"></a>设备支持

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>输入模型</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
</tr>
<tr>
     <td>使用手指向和提交</td>
     <td>❌ 不支持</td>
     <td>✔️ 推荐</td>
     <td>✔️ 推荐</td>
</tr>
</table>


“用手指向和提交”是利用新的铰接式手跟踪系统的新功能之一。  该输入模型也是在沉浸式头戴显示设备上通过使用运动控制器的主要输入模式。

<br>

---

## <a name="hand-rays"></a>手部射线

在 HoloLens 2 上，我们创造了一种从用户手掌中心射出的手部射线。 该射线被视为手的延伸。 圆环形光标连接到射线的末端，以指示射线与目标对象相交的位置。 然后光标所指向的对象可以接收来自手的手势命令。

通过使用拇指和食指执行隔空敲击动作来触发该基本手势命令。 通过使用手射线指向和隔空敲击以提交，用户可以激活某个按钮或超链接。 借助更多的复合手势，用户可以在 Web 内容中导航，并从远处操纵 3D 对象。 手部射线的视觉设计也应对这些指向和提交状态做出反应，如下所述： 

:::row:::
    :::column:::
        ![手部射线指向](images/hand-rays-pointing.jpg)<br>
        **“指向”状态**<br>
        在指向状态下，射线是虚线，光标是圆环形状  。
    :::column-end:::
    :::column:::
        ![手部射线提交](images/hand-rays-commit.jpg)<br>
        **“提交”状态**<br>
        在提交状态下，光线变为实线，光标缩小为点  。
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a>在远近之间转换

我们没有使用特定的手势（如“用食指指向”来引导射线），而是设计了射线从手掌中心发出，留出五根手指来做更多的操控性手势，如捏和抓。 通过这种设计，我们只创建了一个心理模型 - 同一组手势用于远交互和近交互。 可以使用相同的抓取手势来操纵不同距离的对象。 射线的调用是自动的，并且基于邻近度，如下所述：

:::row:::
    :::column:::
        ![近操作](images/transition-near-manipulation.jpg)<br>
        **近操作**<br>
        当对象在手臂长度范围（大约 50 cm）内时，射线会自动关闭，支持近距交互。
    :::column-end:::
    :::column:::
        ![远操作](images/transition-far-manipulation.jpg)<br>
        **远操作**<br>
        当对象距离超过 50 cm 时，将启用射线。 转换应该顺利无缝。
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D 盖板交互

2D 盖板是装有 Web 浏览器等 2D 应用内容的全息容器。 与 2D 平板电脑进行远距离交互的设计理念是使用手部射线进行瞄准，并隔空敲击以进行选择。 在用手部射线瞄准目标后，用户可以通过隔空敲击来触发超链接或按钮。 他们可以用一只手“隔空敲击并拖动”来上下滚动盖板内容。 使用两只手进行隔空敲击和拖动的相对运动可以放大和缩小平板电脑内容。

在角落和边缘处瞄准手部射线可显示最接近的可视操作元素。 通过“抓取和拖动”操作视觉元素，用户可通过边角视觉元素执行统一的缩放，然后通过边缘视觉元素重排盖板。 用户可以通过抓取并拖动 2D 盖板顶部的全息条来移动整个盖板。

:::row:::
    :::column:::
       ![2D 盖板交互单击](images/2d-slate-interaction-click.jpg)<br>
       **单击**<br>
    :::column-end:::
    :::column:::
       ![2D 盖板交互滚动](images/2d-slate-interaction-scroll.jpg)<br>
        **滚动**<br>
    :::column-end:::
    :::column:::
       ![2D 盖板交互缩放](images/2d-slate-interaction-zoom.jpg)<br>
       **缩放**<br>
    :::column-end:::
:::row-end:::

<br>

**操作 2D 盖板**<br>

* 用户在角落或边缘处指向手部射线可显示最接近的可视操作元素。 
* 通过对视觉元素应用操作手势，用户可通过边角视觉元素执行统一的缩放，然后通过边缘视觉元素重排盖板。 
* 通过在 2D 盖板顶部的全息条上应用操纵手势，用户可以移动整个盖板。<br>


<br>

---

## <a name="3d-object-manipulation"></a>3D 对象操作

在直接操作中，用户可以通过两种方式操纵 3D 对象：基于视觉元素的操作和非基于视觉元素的操作。 在指向和提交模型中，用户能够通过手部射线实现完全相同的任务。 不需要额外的学习。<br>

### <a name="affordance-based-manipulation"></a>基于可视操作元素的操作
用户使用手部射线指向并显示边框和可视操作元素。 用户可在边框上应用操作手势来移动整个对象，在边缘视觉元素上应用操作手势来旋转对象，以及在边角视觉元素上应用操作手势以进行统一的缩放。 <br>

:::row:::
    :::column:::
       ![3D 对象操作远移动](images/3d-object-manipulation-far-move.jpg)<br>
       **移动**<br>
    :::column-end:::
    :::column:::
       ![3D 对象操作远旋转](images/3d-object-manipulation-far-rotate.jpg)<br>
        **旋转**<br>
    :::column-end:::
    :::column:::
       ![3D 对象操作远缩放](images/3d-object-manipulation-far-scale.jpg)<br>
       **缩放**<br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a>不基于可视操作元素的操作
用户用手部射线指向以显示边界框，然后直接对其应用操作手势。 如果用一只手进行操作，对象的平移和旋转将与手的移动和方向相关联。 如果用两只手进行操作，用户可以根据两只手的相对运动来平移、缩放和旋转对象。<br>

<br>

---

## <a name="instinctual-gestures"></a>本能手势
指向和提交的本能手势的概念类似于[用手直接操作](direct-manipulation.md)的概念。 用户在 3D 对象上执行的手势是由 UI 视觉元素的设计引导的。 例如，一个小的控制点可能会促使用户用拇指和食指捏，而用户可能想用所有 5 根手指抓一个较大的对象。

:::row:::
    :::column:::
       ![本能手势远的小型对象](images/instinctual-gestures-far-smallobject.jpg)<br>
       **小型对象**<br>
    :::column-end:::
    :::column:::
       ![本能手势远的中型对象](images/instinctual-gestures-far-mediumobject.jpg)<br>
        **中型对象**<br>
    :::column-end:::
    :::column:::
       ![本能手势远的大型对象](images/instinctual-gestures-far-largeobject.jpg)<br>
       **大型对象**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>手部与 6 DoF 控制器之间的对称设计 

远程交互的指向和提交概念最初是为混合现实门户 (MRP) 创建和定义的，在混合现实门户中，用户戴上沉浸式头戴显示设备，通过运动控制器与 3D 对象进行交互。 运动控制器射出光线来指向和操纵远处的对象。 控制器上有用于进一步提交不同操作的按钮。 我们利用射线的交互模式，并将其与双手关联。 借助这种对称设计，熟悉 MRP 的用户在使用 HoloLen 2 时不需要学习另一种交互模式来进行远距离指向和操纵，反之亦然。    

:::row:::
    :::column:::
        ![带控制器的射线的对称设计](images/symmetric-design-for-rays-controllers.jpg)<br>
        **控制器射线**<br>
    :::column-end:::
    :::column:::
        ![带手的射线的对称设计](images/symmetric-design-for-rays-hands.jpg)<br>
        **手部射线**<br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 的 MRTK（混合现实工具包）中的手部射线
默认情况下，MRTK 提供一个手部射线 prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers))，其视觉状态与 shell 的系统手部射线相同。 它分配在 MRTK 的输入配置文件的“指针”下。 在沉浸式头戴显示设备中，相同的射线会用于运动控制器。

* [MRTK - 指针配置文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK - 输入系统](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK - 指针](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a>另请参阅
* [使用手直接操作](direct-manipulation.md)
* [凝视和提交](gaze-and-commit.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - 手势](gaze-and-commit.md#composite-gestures)
* [本能交互](interaction-fundamentals.md)
