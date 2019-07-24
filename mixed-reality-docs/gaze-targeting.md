---
title: 注视目标
description: 所有交互的基础都是用户能够将想要与之交互的元素设定为目标，而无论使用何种输入模态。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, 注视, 注视目标, 交互, 设计
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829841"
---
# <a name="gaze-and-dwell"></a>注视和停留
可以通过多种不同的方法来确认_提交_, 如结合使用_声音_或_手写笔势_。
不过, 有几种用户方案, 用户的手可能繁忙或不能被跟踪 (例如, 具有超大重型手套的工厂工作人员)。 由于用户首选项、社交上下文或更高的环境, 语音输入也可能不可用。
作为回退解决方案, 执行_提交_的另一种方法是将起始置于称为_停留_的 UI 元素。
可以使用打印头或眼睛来执行_停留_。 此理念非常简单, 可以在以下阶段分解: 
1. 用户在全息按钮上启动 gazing

2. 在短暂的开始延迟 (例如, 150 ms) 后, 将启动一些视觉反馈动画。 开始延迟用于避免用户通过立即立即弹出反馈来使用户不堪重负。
    - 对于_眼睛眼睛_, 建议对视觉对象的显示内容进行以下设计:
      - **混合 it**:从一开始就是完全不透明地将反馈从几乎可见。 这使得反馈减少了混乱和 overwhleming, 并与系统具有用户真正想要与此按钮进行合作的置信度非常一致。
      - **拉取**:创建视觉反馈, 而不是缩小大小并向目标中心移动, 从而吸引用户的视觉对象。 

3. 预定义停留时间段 (例如, 800 ms) 后, 停留完成, 并触发关联的事件。
    - 提供一些正在完成的听觉或视觉反馈, 使其真正进入当前选择的项。

![停留状态](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>注视目标

所有交互的基础都是用户能够将想要与之交互的元素设定为目标，而无论使用何种输入模态。 在 Windows Mixed Reality 中，通常通过用户凝视来完成此操作。

为了实现成功使用，系统对用户意图的计算理解与用户的实际意图必须尽可能保持一致。 按照系统正确解释用户目标操作的程度，满意度提高，性能提高。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>注视目标</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>目视目标</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> 即将[推出](index.md)特定于 HoloLens 2 的更多指导。

## <a name="target-sizing-and-feedback"></a>目标大小调整和反馈

凝视向量已多次被证明可用于精确设定目标，但通常最适合粗略设定目标（获取较大的目标）。 最小目标尺寸为 1 到 1.5 度时，用户在大多数情况下都可成功执行操作，但目标尺寸为 3 度时通常可更快地设定目标。 请注意，即使对于 3D 元素，用户设定为目标的尺寸实际上也是 2D 区域，3D 元素的投影即是可设定为目标的区域。 提供一些明确的提示来表明一个元素“处于活动状态”（即用户将其设定为目标）非常有用，这可能包括可见的“悬停”效果、音频突出显示或单击，或光标与元素清晰对齐。

![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)<br>
*2 米远处的最佳目标大小*

![突出显示凝视目标对象的示例](images/gazetargeting-highlighting-640px.jpg)<br>
*突出显示凝视目标对象的示例*

## <a name="target-placement"></a>目标位置

用户经常无法找到位于其视野中非常高或非常低的位置的 UI 元素，大部分注意力集中在主要焦点（通常大致是视平线位置）周围的区域。 将大多数目标放在视平线位置附近的某个合理范围内可能有所帮助。 考虑到用户在任何时候都倾向于关注一个相对较小的可视区域（注意力视锥大约为 10 度），通过将 UI 元素分组到在概念上相关的位置，可以在用户的视线通过某个区域时利用各项目之间的注意力链锁作用。 在设计 UI 时，请注意 HoloLens 和沉浸式头戴显示设备之间视野的巨大差异。

![在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例](images/gazetargeting-grouping-1000px.jpg)<br>
*在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例*

## <a name="improving-targeting-behaviors"></a>改进目标设定行为

如果能够确定（或非常近似地确定）用户目标，那么接受“差一点”的交互尝试非常有帮助，就好像它们是正确的目标一样。 有一些成功的方法可以融入混合现实体验中：

### <a name="gaze-stabilization-gravity-wells"></a>注视稳定 ("重力井")

应在大多数/所有时间启用此技术。 此技术消除了用户可能产生的自然头部/颈部抖动。 也可消除因看/说行为导致的运动。

### <a name="closest-link-algorithms"></a>最邻近链接算法

这些方法在交互内容稀少的区域效果最好。 如果你很有可能确定用户要尝试与之交互的内容，那么可以通过简单地假设某种程度的意图来补充其目标设定能力。

### <a name="backdatingpostdating-actions"></a>回溯/推迟操作

此机制非常适合需要快速完成的任务。 当用户通过一系列面向设法使其/激活的速度来快速进行操作时, 可能会有一定的意图, 并允许*错过的步骤*处理用户在点击 (50ms 之前/之后) 略有针对性的目标在早期测试中有效。

### <a name="smoothing"></a>平滑处理

此机制对于路径运动非常有用，可减少由于头部自然运动特征引起的轻微抖动/摆动。 对路径运动进行平滑处理时，根据运动幅度/距离（而非随着时间推移）进行平滑处理

### <a name="magnetism"></a>磁吸

此机制可被视为更通用的“最邻近链接”算法，可绘制靠近目标的光标，或者只是在用户接近可能的目标时增加有效范围（无论是否可见），使用一些交互式布局知识来更好地实现用户意图。 这对于小型目标尤其有用。

### <a name="focus-stickiness"></a>焦点粘性

此机制可在确定要置于焦点的邻近交互元素时，提供其与当前置于焦点的元素的偏差。 这将有助于减少在具有自然噪声的两个元素之间的中点处浮动时的不稳定焦点切换行为。

## <a name="see-also"></a>请参阅
* [手势](gestures.md)
* [语音命令](voice-design.md)
* [光标](cursors.md)
