---
title: Head 注视和停留
description: Head 注视和停留输入模型概述
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实，注视、 停留、 交互，设计
ms.openlocfilehash: 05457b35c13422c8aa6663bdf52a489a4f5afdaa
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65813991"
---
# <a name="head-gaze-and-dwell"></a>Head 注视和停留

时手都与工具和部件被占用，笔势可以是枯燥乏味或不可能。 语音命令，如手势，可以在某些上下文中，例如在过大的情况下不可靠。 此外，使用语音控制计算机并不是普遍常见，但它肯定获得流 ！ Head 注视和停留提供了工作 heads-up 和无 HoloLens 上的最常见和最容易 master 机制。 此外，提供注视 head 和停留是 100%可靠独立的操作环境中的干扰会相互干扰，也不静默约束。

## <a name="scenarios"></a>方案

Head 注视和停留的优越性体现在方案中人的手均忙于处理其他任务，而语音不是 100%可靠或由于环境或社交约束提供。 一个很好示例是一个人戴上 HoloLens 覆盖修复汽车引擎时的参考信息。 太多的事情都在忙于 with tools 或支持其主体，因为它们了解到引擎隔离舱。 与常量进行深入探讨和工具，使语音命令变得困难的嗡嗡声噪音车库空间很大。 Head 注视和停留允许 HoloLens 更有信心地导航而无需 interupting 其参考资料中的人员及其工作流。 

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>输入的模型</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
    </tr>
     <tr>
        <td>Head 注视和停留</td>
        <td>✔️ 建议</td>
        <td>✔️ 建议</td>
        <td>✔️ 建议</td>
    </tr>
</table>

## <a name="goals"></a>目标

提供一种机制来进行完全无需手动交互，而无需使用语音。

## <a name="design-principles"></a>设计原则

1. 避免"作为一武器注视"

    Head 注视和停留需要视觉反馈以直观，但太多的反馈可以引入感到不安。 反馈应帮助用户了解什么他们面向的，但不是自动选择它针对其意图。 读取文本、 图标和标签需要额外的注意事项，以便提供应对所导致的信息，然后选择 person 空间。
    
2. 查找 Goldilocks 速度
    
    停留交互可以具有不同的计时器根据影响导航-更必然函数可能会受益于填充时间较长时，更常用的函数通常将受益于更快的填充时间。 当使用填充效果来显示这些计时器，填充颜色的动画曲线可以积极地影响填充更快的感觉。 不考虑，应采取以启用从快速/medium/速度缓慢的用户决定填充速度重写。
    
3. 说到 yo-yo 效果不允许

    Yo-yo 效果是可以出现时的内容和头注视和停留控件位置强制人去不断地向上和向下重复的磁头运动的令人不舒服模式。 例如，列表的导航栏底部的 head 视线移动并停留按钮与引入循环-看下若要在此再次详述，查找在结果中，查找若要在此再次详述，等等。此生成的模式不舒服，应避免通过将导航控件放入后，包括反复占用更少的集中位置。 放置停留按钮相对于其效果变得重要舒适。

## <a name="ux-guidelines-and-best-practices"></a>UX 准则和最佳做法

### <a name="target-sizes"></a>目标大小
  可以轻松地访问，head 注视和目标需要足够大到 comforatably 目标，在此再次详述按住的 head stabily 在目标上规定的时间。 我们建议的最低目标大小为 2 个度，若要获得最合适的体验。 

### <a name="visual-feedback"></a>视觉反馈

在使用径向填充表示停留计时器，启动从按钮的中心。 一致的响应是减少混淆比在不同的按钮上的所有不同的方向。 

  * 而对于方向交互 （例如，导航栏向上/向下/左/右，等），可以断开此规则。 例如，在下一步/后的异常的 Microsoft Dynamics 365 指南使保持正确填充。
  * 请考虑反转径向填充从外部，于以下情形： 关闭切换按钮。 按下按钮的反感觉是很好的可视模式来维护。 

### <a name="progressive-disclosure"></a>渐进式披露

渐进式披露意味着仅显示在每个交互阶段是相关尽可能详细。 对于停留，这意味着停留目标上突出显示 （例如，在列表控件） 表示在显示。

 ### <a name="oversized-targets"></a>过大的目标
停留区域可能会大于非活动状态的图标，以使其更易于使用，如 Microsoft Dynamics 365 指南中的后退按钮。

### <a name="prevent-flickering-with-delayed-feedback"></a>防止闪烁延迟反馈的问题
使用开始可视反馈之前短暂的延迟以避免当有人通过停留目标上方时闪烁。
* 为按钮 inteacted 使用频繁，保持非常短的延迟，因此应用程序感觉反应。
* 对于与 infrequenctly 交互的按钮更长时间可以是适当以免感觉 twitchy 的接口。

## <a name="ui-patterns"></a>UI 模式

### <a name="high-frequency-buttons"></a>高频率按钮
![Microsoft Dynamics 365 指南下一步按钮](images/GuideNextButton.png "Microsoft Dynamics 365 指南下一步按钮")高频率按钮是整个应用程序通常使用的按钮。 其中一个很好示例是 Microsoft Dynamics 365 指南中的前进和后退按钮。

高频率按钮应...
* 为更大按钮，更轻松地与 head 注视命中
* 请继续关注高度，以避免人机工程学使出附近。

### <a name="low-frequency-buttons"></a>低频率按钮
低频率按钮是不与之交互，定期整个应用程序的按钮。 很好的示例可能是按钮，访问设置菜单或按钮以清除所有工作。

* 尝试保留不频繁的视线移动头的路径，以避免意外激活干扰这些按钮。 

### <a name="confirmations"></a>确认
![Microsoft Dynamics 365 指南确认对话框](images/GuidesConfirmation.png "Microsoft Dynamics 365 指南确认对话框")

时操作中有重大影响，如充电资金、 删除的工作，或启动一个长的过程，它可用于确认一个人要选择一个按钮。 Head 注视和停留存在 Ui 是一些模式和确认对话框时的注意事项：

  * 在主要按钮上显示选择突出显示。
  * 在选择突出显示相同的时间显示停留目标。
  * 对于辅助按钮，显示 head 注视上的停留目标。
        
### <a name="toggle-buttons"></a>切换按钮
切换按钮需要一些细微的逻辑才能正常工作。 当一个人 dwells 上切换按钮和在职员工它时，他们需要退出按钮，然后返回以重启停留逻辑。 可滚动按钮处于非活动状态的状态与具有清除活动至关重要。 

### <a name="list-views"></a>列表视图
![Microsoft Dynamics 365 指南确认对话框](images/GuidesListView.png "Microsoft Dynamics 365 指南确认对话框")列表视图显示 head 视线移动一个特定挑战，输入在此再次详述。 人们需要能够扫描而不 tiptoe 围绕停留目标，这有感觉的内容。 

设计列表视图的一些提示：
* 具有头 gazed 但不开始停留，除非头注视位于特定停留目标时突出显示的整行。
* 仅显示停留目标时突出显示该行以降低视觉干扰。
* 保持清晰一致的停留目标位置。
* 不显示所有在此再次详述目标立即以避免重复 UI
* 建立用户体验您所熟悉的尽可能多地重复使用相同的模式
 
 ## <a name="see-also"></a>请参阅
* [直接操作](direct-manipulation.md)
* [指向并提交](point-and-commit.md)
* [交互基础知识](interaction-fundamentals.md)
* [头部凝视并提交](gaze-and-commit.md)
* [凝视和语音](voice-design.md)
