---
title: 头部凝视和停留
description: 头部凝视和停留输入模型概述
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: 混合现实, 凝视, 停留, 交互, 设计
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439308"
---
# <a name="head-gaze-and-dwell"></a>头部凝视和停留

手拿工具和零件，手势可能是没有意义或无法实现。 语音命令（例如手势）在某些情况下可能不可靠，例如在过度嘈杂的条件下。 此外，使用语音控制计算机并不是普遍常见的，但正日益盛行！ 头部凝视和停留提供最熟悉且易于掌握的机制，可在 HoloLens 上实现抬头操作和解放双手的操作。 此外，头部凝视和停留 100% 可靠，与操作环境中不受噪声干扰和静音约束。

## <a name="scenarios"></a>场景

在人的手忙于处理其他任务的情况下，打印头和停留 transact-sql，而语音没有100% 的可靠性或由于环境或社交限制而无法使用。 一个很好的例子是穿戴 HoloLens 的人在修理汽车发动机时获取参考信息。 倚靠在发动机舱内时，他们的手拿着工具或支撑着身体。 车库空间很大，工具不断敲打声和嘈杂声，难以使用语音命令。 通过打印头和停留，使用 HoloLens 的人员可以放心地浏览其参考材料，而不会中断工作流。 

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>输入模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>头部凝视和停留</td>
        <td>✔️ 推荐</td>
        <td>✔️ 推荐</td>
        <td>✔️ 推荐</td>
    </tr>
</table>


## <a name="design-principles"></a>设计原则

**避免 "注视武器"**

头部凝视和停留需要直观的视觉反馈，但反馈过多会令人焦虑。 反馈应有助于用户了解其目标，但不会根据其意图自动选择。 阅读文本、图标和标签需要额外考虑，以便为客户提供在进行选择之前吸收信息的空间。
    
**查找 Goldilocks 速度**
    
停留交互根据对导航的影响而使用不同的计时器 - 更频繁使用的功能通常将受益于更快的填充时间，而更具重要性的功能可能受益于更长的填充时间。 当使用填充效果来显示这些计时器时，填充颜色的动画曲线可对感知快速填充时间产生正面影响。 应进行仔细考虑，使用户能够基于快速/中速/慢速填充速度覆盖来做出决策。
    
**假设 "无-否" 为 yo-yo 效果**

摇摆不定效应是一种令人不适的头部运动模式，当内容的位置以及头部凝视和停留控制迫使人们不断上下反复看时，即会出现这种效应。 例如，使用底部的 "注视" 和 "停留" 按钮的列表导航到 "停留" 循环，查找结果，查看 "停留" 等。这种结果模式不舒服，应避免将导航控件置于需要更少恢复的集中位置。 相对于效果放置停留按钮对于确保舒适性非常重要。

<br>

---


## <a name="ux-guidelines-and-best-practices"></a>UX 指南和最佳做法

### <a name="target-sizes"></a>目标大小
  为了能够轻松地访问，打印头和停留目标需要足够大，以便能够轻松地查看，并在规定时间的目标位置上保持一头稳定。 建议最小目标大小为2度，以获得最舒适的体验。 

### <a name="visual-feedback"></a>视觉反馈

当使用径向填充来表示停留计时器时，请从按钮中心开始。 与在不同按钮上均采用不同方向相比，一致的响应可减少混淆。 

  * 对于定向交互（例如，向上/向下/向左/向右导航等），可以不遵循此规则。 例如，在 Microsoft Dynamics 365 指南中左右两侧填充“下一步”/“后退”时例外。
  * 考虑从外部反径向填充，例如关闭按钮。 按下按钮的反向效果是一种出色的视觉模式。 

### <a name="progressive-disclosure"></a>渐进式披露

渐进式披露是指只显示与交互的每个阶段相关的详细信息。 对于停留，这意味着停留目标在突出显示时揭露（例如，在列表控件中）。

 ### <a name="oversized-targets"></a>过大的目标
停留区域可以比非活动图标大，以便于使用，例如 Microsoft Dynamics 365 指南中的“后退”按钮。

### <a name="prevent-flickering-with-delayed-feedback"></a>通过延迟反馈防止闪烁
在开始视觉反馈之前使用短暂的延迟，以避免当有人经过停留目标时闪烁。
* 对于按钮经常交互的按钮，保持延迟非常短，使应用程序感觉被动。
* 对于不常交互的按钮，更长的延迟可能适用于避免出现 twitchy 的界面。


<br>

---

## <a name="ui-patterns"></a>UI 模式

### <a name="high-frequency-buttons"></a>高频率按钮

:::row:::
    :::column:::
        高频率按钮是通常在整个应用程序中使用的按钮。 其中一个很好的例子是 Microsoft Dynamics 365 指南中的“下一步”和“后退”按钮。<br>
        <br>
        **针对**<br>
  * 高频率按钮应该很大，更容易碰到打印头
  * 保持近眼睛，以避免人体工学。<br>
        <br>
*图像： Microsoft Dynamics 365 "下一步" 按钮*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 "下一步" 按钮](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>低频率按钮
低频率按钮是整个应用程序中不常与之交互的按钮。 一个很好的例子是用于访问设置菜单的按钮，或用于清除所有工作的按钮。

* 尽量使这些按钮远离频繁进行头部凝视的路径，以避免意外激活。 

<br>

---

### <a name="confirmations"></a>确认

:::row:::
    :::column:::
        当一个动作有重大影响时（如收费、删除工作或启动一个长流程），这对确认要选择按钮非常有用。<br>
        <br>
        **针对**<br>
  * 在主按钮上突出显示选择内容。
  * 在选择内容突出显示的同时显示停留目标。
  * 对于辅助按钮，在头部凝视上显示停留目标。<br>
        <br>
*映像： Microsoft Dynamics 365 指南确认对话框*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南确认对话框](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>切换按钮
切换按钮需要一些细微的逻辑才能正常工作。 当用户停留在切换按钮上并激活它时，他们需要退出该按钮然后返回以重启停留逻辑。 可切换按钮必须具有明确的活动状态与非活动状态。 

<br>

---

### <a name="list-views"></a>列表视图

:::row:::
    :::column:::
        列表视图为打印头和停留输入提供了一个特定的挑战。 用户需要能够浏览内容，而不是感觉必须小心翼翼地绕过停留目标。<br>
        <br>
**针对**<br>
  * 在 gazed 但不开始停留在特定停留目标上时，将整个行突出显示，但不会开始停留。
  * 突出显示行时，仅显示停留目标，以减少视觉干扰。
  * 清楚地与停留目标的位置一致。
  * 不要一次显示所有停留目标，以避免重复的 UI。
  * 尽可能频繁地使用相同的模式，以建立 UX 熟悉。<br>
        <br>
*映像： Microsoft Dynamics 365 指南列表*
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南列表](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>另请参阅
* [注视并提交](gaze-and-commit.md)
* [直接操作](direct-manipulation.md)
* [动手手势](gaze-and-commit.md#composite-gestures)
* [动手并提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [语音输入](voice-input.md)
