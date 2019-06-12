---
title: 头部凝视和停留
description: 头部凝视和停留输入模型概述
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 凝视, 停留, 交互, 设计
ms.openlocfilehash: 70b25949380679d2edc81b07ab54f24fa20e3f3d
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516007"
---
# <a name="head-gaze-and-dwell"></a>头部凝视和停留

手拿工具和零件，手势可能是没有意义或无法实现。 语音命令（例如手势）在某些情况下可能不可靠，例如在过度嘈杂的条件下。 此外，使用语音控制计算机并不是普遍常见的，但正日益盛行！ 头部凝视和停留提供最熟悉且易于掌握的机制，可在 HoloLens 上实现抬头操作和解放双手的操作。 此外，头部凝视和停留 100% 可靠，与操作环境中不受噪声干扰和静音约束。

## <a name="scenarios"></a>方案

当双手忙于完成其他任务，且由于环境或社交限制而使声音无法 100% 可靠或可用时，头部凝视和停留效果极佳。 一个很好的例子是穿戴 HoloLens 的人在修理汽车发动机时获取参考信息。 倚靠在发动机舱内时，他们的手拿着工具或支撑着身体。 车库空间很大，工具不断敲打声和嘈杂声，难以使用语音命令。 通过头部凝视和停留，HoloLens 使用者可安心浏览参考资料，而无需中断工作流程。 

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>头部凝视和停留</td>
        <td>✔️ 推荐</td>
        <td>✔️ 推荐</td>
        <td>✔️ 推荐</td>
    </tr>
</table>

## <a name="goals"></a>目标

提供完全解放双手的交互机制，无需使用语音。

## <a name="design-principles"></a>设计原则

1. 避免“将凝视作为一种武器”

    头部凝视和停留需要直观的视觉反馈，但反馈过多会令人焦虑。 反馈应有助于用户了解其目标，但不会根据其意图自动选择。 阅读文本、图标和标签需要额外考虑，以便为客户提供在进行选择之前吸收信息的空间。
    
2. 寻求适宜速度
    
    停留交互根据对导航的影响而使用不同的计时器 - 更频繁使用的功能通常将受益于更快的填充时间，而更具重要性的功能可能受益于更长的填充时间。 当使用填充效果来显示这些计时器时，填充颜色的动画曲线可对感知快速填充时间产生正面影响。 应进行仔细考虑，使用户能够基于快速/中速/慢速填充速度覆盖来做出决策。
    
3. 对摇摆不定效应说不

    摇摆不定效应是一种令人不适的头部运动模式，当内容的位置以及头部凝视和停留控制迫使人们不断上下反复看时，即会出现这种效应。 例如，通过底部的头部凝视和停留按钮进行列表导航会产生一个循环，即俯视停留、抬头查看结果，再俯视停留。这种生成模式令人不适，应通过将导航控件放置在需要较少来回操作的集中位置来避免。 相对于效果放置停留按钮对于确保舒适性非常重要。

## <a name="ux-guidelines-and-best-practices"></a>UX 指南和最佳做法

### <a name="target-sizes"></a>目标大小
  为了方便使用，头部凝视和停留目标需要足够大，以便舒适地瞄准目标，并在规定的时间内使头部稳定地保持在目标上。 建议最小目标尺寸为 2 度，以获得最舒适的体验。 

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
* 对于经常与之交互的按钮，请保持非常短的延迟，以便应用程序做出反应。
* 对于不经常交互的按钮，可能适合使用较长的延迟，以避免界面急于做出响应。

## <a name="ui-patterns"></a>UI 模式

### <a name="high-frequency-buttons"></a>高频率按钮
![Microsoft Dynamics 365 指南“下一步”按钮](images/GuideNextButton.png "Microsoft Dynamics 365 指南“下一步”按钮")高频率按钮是在整个应用程序中常用的按钮。 其中一个很好的例子是 Microsoft Dynamics 365 指南中的“下一步”和“后退”按钮。

高频率按钮应...
* 较大，以便更轻松地进行头部凝视
* 保持在视平线附近，以符合人体工程学。

### <a name="low-frequency-buttons"></a>低频率按钮
低频率按钮是整个应用程序中不常与之交互的按钮。 一个很好的例子是用于访问设置菜单的按钮，或用于清除所有工作的按钮。

* 尽量使这些按钮远离频繁进行头部凝视的路径，以避免意外激活。 

### <a name="confirmations"></a>确认
![Microsoft Dynamics 365 指南确认对话框](images/GuidesConfirmation.png "Microsoft Dynamics 365 指南确认对话框")

当一个动作有重大影响时（如收费、删除工作或启动一个长流程），这对确认要选择按钮非常有用。 对于头部凝视和停留 UI，确认对话框有一些模式和注意事项：

  * 在主按钮上突出显示选择内容。
  * 在选择内容突出显示的同时显示停留目标。
  * 对于辅助按钮，在头部凝视上显示停留目标。
        
### <a name="toggle-buttons"></a>切换按钮
切换按钮需要一些细微的逻辑才能正常工作。 当用户停留在切换按钮上并激活它时，他们需要退出该按钮然后返回以重启停留逻辑。 可切换按钮必须具有明确的活动状态与非活动状态。 

### <a name="list-views"></a>列表视图
![Microsoft Dynamics 365 指南确认对话框](images/GuidesListView.png "Microsoft Dynamics 365 指南确认对话框")列表视图为头部凝视和停留输入带来了特殊挑战。 用户需要能够浏览内容，而不是感觉必须小心翼翼地绕过停留目标。 

设计列表视图的一些提示：
* 在头部凝视时突出显示整行，但除非头部凝视在特定的停留目标上，否则不会开始停留。
* 仅在突出显示行时显示停留目标以减少视觉干扰。
* 清晰明了并与停留目标的位置保持一致。
* 不要一次性显示所有停留目标以避免重复 UI
* 尽可能多地重复使用相同的模式以建立熟悉的用户体验
 
 ## <a name="see-also"></a>另请参阅
* [使用手直接操作](direct-manipulation.md)
* [使用手指向和提交](point-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [头部凝视并提交](gaze-and-commit.md)
* [语音命令](voice-design.md)
