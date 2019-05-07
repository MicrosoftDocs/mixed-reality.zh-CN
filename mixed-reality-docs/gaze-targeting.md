---
title: 目标的视线移动
description: 用户能够针对他们想要进行交互，而不考虑输入模式的元素为基础构建的所有交互。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实、 提供注视、 视线移动目标交互，设计
ms.openlocfilehash: 1ac4f06208a7574fced0a7e27e93469ec93bf6e0
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873923"
---
# <a name="gaze-and-dwell"></a>视线移动和停留
有很多不同的方式，以确认_提交_如结合使用的视线移动_语音_或_传递手势_。
有几种用户方案，在其中的用户的手可能正忙或无法跟踪 （例如，使用过大的重型手套工厂工作进程）。 语音输入可能也不可用，因为用户首选项、 社交上下文或嘈杂的环境。
另一种作为回退解决方案来执行_提交_是只需保留盯住 UI 元素，我们称之为_会仔细斟酌_。
一个_会仔细斟酌_头或关注的视线移动就可以执行。 其思路很简单，可以在以下几个阶段中细分： 
1. 用户启动 holographic 按钮在观望

2. 简要开始延迟 （例如，150 毫秒） 后启动一些可视反馈的动画。 用于开始延迟用于避免庞大用户的方法是立即弹出反馈的时间。
    - 有关_关注的视线移动_，我们建议以下视觉对象的设计会仔细斟酌反馈：
      - **其混合**:顺利 blend 中几乎不能看到在第一次完全不透明的反馈。 这使得反馈更少的分散注意力和 overwhleming，并可以很好地符合系统具有用户真正想要与此按钮的置信度。
      - **拉入**:创建可视反馈，不是减小大小，并将移至目标，提取用户的 visual 注意力的中心。 

3. 预定义的停留时间段 （例如，800 毫秒） 后停留完成并触发关联的事件。
    - 提供一些正在最后完成听觉或可视反馈，以真正使主页的项有现在选择。

![在此再次详述状态](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>目标的视线移动

用户能够针对他们想要进行交互，而不考虑输入模式的元素为基础构建的所有交互。 在 Windows Mixed Reality，通常这是使用用户的视线移动。

若要使用户能够成功使用体验，系统的计算的了解用户的意图和用户的实际目的，必须尽可能接近地对齐。 某种程度上，系统将解释用户的预期的操作正确，满意度增加和性能提高。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> 目标的视线移动</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️ </td>
</tr><tr>
<td> 密切关注面向</td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md)。

## <a name="target-sizing-and-feedback"></a>目标大小调整和反馈

视线移动矢量具有已重复显示可用于面向正常，但通常最适合总目标 （获取稍大些目标）。 1 到 1.5 度为单位的最小目标大小应在 3 个度的目标通常的速度更快，但在大多数情况下，允许用户成功操作。 请注意，用户目标实际上是三维元素-甚至的 2D 区域的大小无论投影面向它们应该是定目标区域。 提供一个元素是"活动"（该用户面向） 一些突出提示会非常有用-这可以包括处理，例如可见"悬停"效果、 音频突出显示或单击，或清除的元素的光标对齐方式。

![2 个计量距离处的最佳目标大小](images/gazetargeting-size-1000px.jpg)<br>
*2 个计量距离处的最佳目标大小*

![突出显示的视线移动目标的对象的一个示例](images/gazetargeting-highlighting-640px.jpg)<br>
*突出显示的视线移动目标的对象的一个示例*

## <a name="target-placement"></a>目标位置

用户将通常无法天线的视野中, 找到很高或极低定位 UI 元素将重点放大部分其关注其主要焦点 （通常大约为水平视线） 周围的区域。 可帮助将大多数目标放入一些合理带围水平视线。 给定用户的情况下往往会将焦点置于将 UI 元素组合在一起的程度上它们从概念上讲相关一个相对较小可视区域上随时 （视觉 attentional 圆锥体约为 10 度），可以利用从关注链接行为项目到项目的用户将其提供注视转到区域。 在设计时用户界面，请记住在 HoloLens 和沉浸式耳机之间的字段的视图可能较大的变化。

![举例说明如何更轻松的视线移动 Galaxy 资源管理器中的目标的分组 UI 元素](images/gazetargeting-grouping-1000px.jpg)<br>
*举例说明如何更轻松的视线移动 Galaxy 资源管理器中的目标的分组 UI 元素*

## <a name="improving-targeting-behaviors"></a>提高目标行为

如果用户的意图以面向内容可以是确定 （或近似密切），它可以接受"near miss"会尝试在交互，就好像它们已正确目标很有帮助。 有了一些可纳入混合的现实体验的成功方法：

### <a name="gaze-stabilization-gravity-wells"></a>提供注视稳定 ("重力 wells")

这应打开大多数/all 的时间。 此方法中删除用户可能有自然的 head 颈部 jit 编译器。 由于查找/谈到的行为也移动。

### <a name="closest-link-algorithms"></a>最接近链接算法

这些效果最佳稀疏的交互式内容与几个方面。 如果没有，您可以确定用户已尝试与之交互的可能性非常高，可以通过简单地假定某一级别的意图进行补充其目标的能力。

### <a name="backdatingpostdating-actions"></a>Backdating/postdating 操作

此机制可在需要速度的任务。 如果某个用户是通过一系列的目标/激活 maneuvers 速度移动，它可用于假定某些目的，并允许*丢失步骤*若要对其用户在具有焦点略有之前或之后的点击 （略有目标执行操作50 毫秒之前/之后为有效的早期测试）。

### <a name="smoothing"></a>平滑处理

此机制可用于的路径移动，减少由于自然磁头运动特征轻微抖动/原因。 通过路径动作，平滑大小/距离的移动而不是随着时间的推移通过平滑处理时

### <a name="magnetism"></a>消除

此机制可以看作"最靠近链接"算法的绘制光标向目标，或只需增加 hitboxes （无论是以可视方式还是不） 的更多常规版本用户达到可能的目标，如使用交互式布局与一些知识更好的方法用户的意图。 这可以是小型的目标对于特别有用。

### <a name="focus-stickiness"></a>焦点粘性

在确定其附近的焦点转至交互式元素，提供对当前已设定焦点的元素偏移。 这将有助于减少不正常时浮点位于自然干扰的两个元素之间的中点的切换行为的焦点。

## <a name="see-also"></a>请参阅
* [手势](gestures.md)
* [语音设计](voice-design.md)
* [光标](cursors.md)
