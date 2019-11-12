---
title: 系统手势
description: 用于调用 "开始" 菜单的系统手势。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实、手势、交互、设计
ms.openlocfilehash: ba543ffe0802d0b95cc539fb0e73c0b4e51fc186
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926730"
---
# <a name="system-gesture"></a>系统手势

系统手势是用于调用 "开始" 菜单的笔势。 它相当于按键盘上的 Windows 键、Xbox 控制器上的 Xbox 按钮或沉浸式耳机运动控制器上的 Windows 按钮。 务必要了解在每个混合现实设备上为系统保留了哪些手势，以防止在设计交互时出现冲突。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>具有</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>布隆</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>手腕按钮</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>眼睛和掌上手掌</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>布隆
若要在 HoloLens 中显示 "开始" 菜单（第一代），我们设计了 "布隆"，这是一个模拟花朵开花的符号手势。 这是 surefooted 交互的独特之处，易于执行，并可快速回调。 若要在 HoloLens （第一代）上执行布隆手势，请将掌托在一起，并将其放在一起，然后将手指向外伸展。

:::row:::
    :::column:::
        ![布隆关闭](images/bloom-close.png)<br>
        **步骤1：将手掌集中到一起**<br>
    :::column-end:::
    :::column:::
        ![布隆打开](images/bloom-open.png)<br>
        **步骤2：掌上手掌**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a>手腕按钮
在 HoloLens 2 中，我们将布隆手势替换为虚拟手腕按钮，该按钮允许更多的 instinctual 交互，无需其他教学。 通过向用户显示手腕上的按钮，用户可以以直观的方式进行访问，并将其与他人一起使用。

:::row:::
    :::column:::
        ![手腕按钮已准备好](images/wrist-button-ready.png)<br>
        **步骤1：掌上以显示 "手腕" 按钮**<br>
    :::column-end:::
    :::column:::
        ![手腕按钮按](images/wrist-button-press.png)<br>
        **步骤2：按 "手腕" 按钮**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a>眼睛和掌上
我们还为 HoloLens 2 中的轻松访问设计了一个直通解决方案。 此手势要求用户可以注视手腕按钮，然后使用同一手来使用拇指和食指执行手掌紧。<br>
:::row:::
    :::column:::
        ![手腕按钮已准备好](images/wrist-button-ready.png)<br>
        **步骤1：掌上以显示 "手腕" 按钮**<br>
    :::column-end:::
    :::column:::
        ![手腕按钮挤压](images/wrist-button-pinch.png)<br>
        **步骤：眼睛按钮，然后捏紧**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>另请参阅

* [本能交互](interaction-fundamentals.md)
* [眼部凝视](eye-tracking.md)
* [语音输入](voice-input.md)
