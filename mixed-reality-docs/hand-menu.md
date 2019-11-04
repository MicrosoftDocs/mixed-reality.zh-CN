---
title: 手动菜单
description: 手动菜单允许用户快速为常用函数获取手动连接的 UI。 这些是我们的最佳实践和建议。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手型、菜单、按钮、快速访问、布局
ms.openlocfilehash: ee958806ac462535b33164bb4faa4bf1aa29e709
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439248"
---
# <a name="hand-menu"></a>手动菜单

![Ulnar 端位置](images/MRTK_UX_HandMenu.png)

手动菜单允许用户快速为常用函数获取手动连接的 UI。 

下面是我们找到的用于手动菜单的最佳实践。 你还可以在[MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)中找到演示菜单的示例场景。

<br>

---

## <a name="behavior-best-practices"></a>行为最佳实践
**答：保持小按钮的数量：** 由于手锁定菜单和眼睛之间的距离接近，而且用户在任何时候都关注相对较小的视觉区域（attentional 的视觉位置约为10度），因此我们建议保持较小的按钮数。 基于我们的浏览，即使用户将其指针移到 FOV 的中心，包含三个按钮的一列也能正常工作。 

**B. 利用 "快速操作" 菜单：** 提起扶手并维持位置可以轻松地引起 arm 疲劳。 对需要短交互的菜单使用手锁定的方法。 如果菜单非常复杂并且需要延长交互时间，请考虑改用世界锁定或正文锁定。 

**C. 按钮/面板角度：** 菜单应以相反的肩和中间点为方向：这允许自然地移动到与菜单的交互，并在触摸按钮. 

**D. 考虑支持单向或无需手动操作：** 不要假设用户的手始终可用。 当一种或两种方法均不可用时，请考虑使用各种上下文，并确保你的设计帐户适用于这些情况。 若要支持右手菜单，可以尝试将菜单位置从 "手动锁定" 切换到 "世界锁定" （向下翻向下）。 对于无需人工使用的方案，请考虑使用语音命令调用手形菜单按钮。

**E. 双重调用：** 如果使用 "上滑作为事件来触发手形菜单"，则它可能会在您不需要时意外出现（误报），因为人们有意（对于通信和对象操作）移动它们和无意。 如果在应用中遇到误报，请考虑添加除手掌事件外的附加步骤，以调用手菜单，如完全打开的手指。

**F. 避免在手腕（系统主页按钮）附近添加按钮：** 如果菜单按钮离 home 按钮太近，则当与 "手形" 菜单交互时，可能会意外触发该按钮。

**G. 测试、测试、测试：** 人们具有不同的正文，并具有不同的阈值，可让人感到 discomfort，等等。请确保在上测试你的设计，并从各种人员那里获取反馈。

<br>

---

## <a name="hand-menu-placement-best-practices"></a>手动菜单布局最佳实践

在人剖析中，ulnar 勇气是在 ulna 骨骼附近运行的勇气。 Ulna 是在 forearm 中找到的一个长骨骼，该骨骼从弯头拉伸到最小手指。

下面是基于我们的探索推荐的2个位置：


:::row:::
    :::column:::
        ![Ulnar 端位置](images/UlnarSideHandMenu.gif)<br>
        **手掌内的 Ulnar**<br>
        此位置是可靠的，因为不会相互重叠。 这对于准确的手动检测和跟踪至关重要。
    :::column-end:::
    :::column:::
        ![Ulnar 端位置](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar 以上的手势**<br>
        此位置对用户非常熟悉，因为他们不需要将其扶手提高到与手形菜单的交互。 建议将菜单**13cm**置于掌上，并在 ulnar 中对齐按钮。 [阅读有关最佳按钮大小的详细信息](interactable-object.md)<br>
        <br>
        出于技术原因，我们建议将此位置用于一个必需实现：一旦用户与之交互，开发人员将需要冻结该菜单。 这将避免 jitteriness 与指针重叠，还允许更快地定位按钮。<br>
        <br>
        HoloLens 2 相机在彼此独立时可以精确地识别。 任何重叠的手势都可以导致手形菜单远离定位点位置。<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>不建议的菜单位置
我们使用不同的菜单布局和位置完成了用户研究，**不建议**使用以下菜单位置，查找下面每个研究的缺点：


:::row:::
    :::column:::
        ![以上 arm](images/AboveArm.gif)<br>
        **Arm 之上**<br>
        1-难以维护良好的手写跟踪<br>
        2-由于非自然位置导致用户疲劳
    :::column-end:::
    :::column:::
        ![上手指](images/AboveFingers.gif)<br>
        **上手指**<br>
        1-由于长时间保留疲劳，<br>
        2-手动跟踪索引和中间指的问题
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![以上中心掌托](images/handCenter.gif)<br>
        **上方-中心掌托**<br>
        1-由于指针重叠而引起的手动跟踪问题<br>
        疲劳，因为为了与菜单进行交互，保留了长时间的手
    :::column-end:::
    :::column:::
        ![Top 手指](images/TopFingerTip.gif) **top 手指**<br>
        1-手写跟踪问题<br>
        双局疲劳，保留高于正常状况<br>
        3-由于手指间的空间有限，导致按下按钮时出现意外的按键
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        Arm ![背面](images/BackOfTheArm.gif)<br>
        **Arm 背面**<br>
        1-可以意外触发主按钮<br>
        2-用户不自然或舒适地
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a>另请参阅

* [可交互对象](interactable-object.md)
* [使用手直接操作](direct-manipulation.md)
* [手和运动控制器](hands-and-tools.md)
