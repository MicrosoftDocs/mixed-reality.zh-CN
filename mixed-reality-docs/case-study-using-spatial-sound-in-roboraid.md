---
title: 案例研究-在 RoboRaid 中使用空间的声音
description: 声音空间是 Microsoft HoloLens，提供用户认为这怎么回事针对这些对象时不可见的行的一种方法的最令人兴奋功能之一。
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality HoloLens，RoboRaid，空间声音
ms.openlocfilehash: 4bb050b4a4051c121c488ea38e150a8973bd7c04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592125"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>案例研究-在 RoboRaid 中使用空间的声音

Charles Sinex，音频 Microsoft HoloLens 体验团队主管，讨论了他创建的音频时遇到的独特挑战[RoboRaid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)，混合的现实第一人称射击。

## <a name="the-tech"></a>技术人员

[空间声音](spatial-sound.md)是 Microsoft HoloLens，提供用户认为这怎么回事针对这些对象时不可见的行的一种方法的最令人兴奋的功能之一。

RoboRaid，最显而易见且最有效利用空间声音是播放机将外部用户的外围视觉发生警报。 例如，Breacher 可以输入从任何扫描墙的协助，但如果不面向进入其中的位置，可能会错过。 提醒你此侵害，你将聆听来自其中输入 Breacher，从中可以了解需要迅速采取措施以将其停止的音频不同位。

## <a name="behind-the-scenes"></a>幕后

创建空间声音 HoloLens 应用的过程是因此全新而独特，过去项目要用于引用缺乏可能会导致大量头划伤时遇到问题。 希望这些示例的音频挑战我们面对而使 RoboRaid 将帮助你在创建音频的你自己的应用。

### <a name="be-mindful-of-taxing-the-cpu"></a>请注意负担很重的 CPU

可以在 CPU 上要求空间声音。 如 RoboRaid 忙体验是重要要保留的空间声音到下在任何给定时间的八个实例。 大多数情况下，很像设置不同的音频事件的实例的限制，以便达到此限制后执行此操作的任何实例将被中止一样简单。 例如，当无人机生成，其 screams 被限制为三个实例在任何给定时间。 假设可以同时生成只有大约四个无人机，三个 screams 的在很多，因为没有您的大脑可以跟踪的方法很多发音相似音频事件。 这释放了资源，对于其他空间声音事件，例如敌人爆炸或投篮机会控制在正在准备的敌人。

### <a name="rewarding-a-successful-dodge"></a>奖励成功避开

Dodging 的机修工保养是游戏玩法 RoboRaid 中的最重要方面，而是，我们认为已真正独特的 HoloLens 体验之一。 在这种情况下，我们想要让成功淡到播放机很有益处。 我们将 Doppler"whizz-通过"来听起来相当在早期开发过程中极具吸引力。 最初，我的计划是使用一个循环并对其进行操作中实时使用音量、 音调、 和筛选器。 此实现将非常复杂，因此提交资源真正开始生成这之前我们创建成本低廉的原型使用的资产的 Doppler 效果提供支持只是为了了解如何在其认为 *。 我们的人才开发了使此 whizz 的资产会播放完全 0.7 秒之前将播放机的 ear 过去 projectile 和结果感觉真了不起 ！ 不用说，我们借助更复杂的解决方案，并实现原型。

* * (如果想要使用内置的 Doppler 效果创建音频资产详细信息，请查看 Charles Deenan 调用声音设计器项目[在 2 分钟 100 Whooshes](http://designingsound.org/2010/02/charles-deenen-special-100-whooshes-in-2-minutes/)。) *
<br>
![已成功逃避敌人的 projectile 奖励有令人满意 whizz 通过声音播放机。](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>抛弃无效声音

最初，我们有想要后它们成功减淡敌人 projectile，但我们决定抛弃这几个原因，爆炸式播放声音播放机后面。 首先，没有可以有效地 whizz 通过 SFX 我们用于避开。 Projectile 碰到墙后端时，其他内容将发生的游戏，将很听起来太多掩码中。 其次，我们没有冲突在地板上，因此我们无法获取播放 projectile 命中而不是墙纸基底时的爆炸式增长。 并且，最后，没有空间声音的 CPU 开销。 Elite Scorpion 敌人 （一个可在墙上插座爬网） 具有投篮大约八个炮弹的特殊攻击。 不仅未，使大量混乱的组合中，它还引入了 awful 噼啪因为它已达到 CPU 太难。

### <a name="communicating-a-hit"></a>通信命中

我们遇到一个有趣的问题号我们认为是唯一的 HoloLens 体验，这是有效地向播放机通信具有已命中的难度。 混合的现实体验的成功之处在于，故事发生的操作，您的感觉。 这意味着您必须要相信您会在您自己的客厅防范外星人机器人侵害。

播放机显然不会感觉就任何内容时它们会命中，因此我们需要找到一种方法真正服播放机坏了 happed 到它们的内容。 在传统的游戏可能会看到可让您了解您的人物花费了一次点击，或屏幕可能会闪烁红色和您的人物的动画可能有点 grunt。 由于混合的现实体验中，这些类型的提示不起作用，我们决定视觉提示结合确实有些夸张的声音，表明你已经损坏。 创建大声音，并使其因此突出其 ducked 下的所有内容的组合中。 然后，以使其突出显示更多，我们添加了短警告声音如同已接收的核 sub。 
<br>
![在播放机获取中 RoboRaid 冲击下，它们提供可视提示，请参阅，但还有一夸张则音频提示，告知他们他们已损坏。](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>从小型扬声器获取大声音

HoloLens 扬声器是设备的小型和浅色以满足需求，因此您不能期望听到过多低端。 类似于面向智能手机或游戏手持设备、 声音的设计器和作曲家一定要注意其音频频率内容的开发。 我始终设计声音或写入完整的频率范围的音乐，因为戴耳机的用户的选项。 但是，若要确保与 HoloLens 发言人的兼容性，我运行测试偶尔通过 EQ 置于我刚好处理任何 DAW 的主机。 EQ 设置包括高反差筛选器大约 600 到 700 Hz （不太陡峭） 和低通筛选在大约 10 K （非常高）。 应让您大致了解的如何将声音将在设备上的播放。

如果需要借助低音让更改音乐的同时按下的了解，可能会发现您的音乐完全失去根的意义上说，应用此 EQ 设置时。 若要解决此问题，我添加另一层到的一个序号更高版本 （与某些丰富谐波） 是低音和混合它，以获得根后在意义。 有时使用向上谐波人群失真将提供足够频率的内容在较高的范围，以使我们的大脑认为它下面的内容。 这适用于 SFX 影响、 爆炸或为特殊时刻的声音等如老板的超级攻击。 确实不能依赖于低端让播放机的影响或权重的了解。 与音乐，利用失真提供很少的危机一定帮助。

### <a name="making-your-audio-cues-stand-out"></a>使您脱颖而出的音频提示

正常情况下，团队中的每个人都想 bombastic 音乐、 嘈杂枪支和疯狂爆炸;但它们还希望能够听到 voiceover 或任何其他游戏关键音频提示。

在完整范围的频率的控制台游戏，可以有根据声音的重要程度划分频率的更多选项。 但是，对于 RoboRaid，我已限制中的我无法从声音曲线的频率范围数。 例如，如果您使用低通滤波器和掉过多内容从更高版本的范围末尾的曲线，无任何内容由于没有更低端中留下的声音。

为了使 RoboRaid 声音可在设备上一样大，我们不得不较低的整体体验的动态范围，并广泛使用了放掉通过创建清晰的层次结构的不同类型的声音的重要性。 我将设置从-2 放掉到-6 dB 根据重要程度。 我个人不喜欢明显放掉在游戏中，因此我花了很多优化淡入淡出输入/输出计时和卷衰减量的时间。 我们设置单独总线空间声音、 非空间声音、 VO，和 dry 总线，而无需混响的音乐，则创建非常高的优先级，关键，和非关键总线。 资产已然后设置转到其相应的总线。

我希望有音频专业人员会尽可能多有趣和兴奋就像我一样正在致力于 RoboRaid 处理其自己的应用。 我迫不及待地想看到 （和听到 ！） 什么 Microsoft 外部的天才人员会提供用于 HoloLens。

## <a name="do-it-yourself"></a>就自己动手

我发现，以使某些事件 （如爆炸） 听起来"较大的"的一个技巧-像它们填满空间 — 是创建空间声音的 mono 资产并将其与 2D 立体声资产，要播放以三维形式。 会占用一些优化，因为立体声内容中具有过多的信息将降低 mono 资产的方向性。 但是，正确平衡会导致将让玩家着头看打开正确的方向的巨大声音。

你可以尝试自己使用下面的音频资产：

**方案 1**
1. 下载[roboraid_enemy_explo_mono.wav](images/roboraid-enemy-explo-mono.wav)和一组通过空间声音播放并将其分配给一个事件。
2. 下载[roboraid_enemy_explo_stereo.wav](images/roboraid-enemy-explo-stereo.wav)和设置为在 2D 立体声设备中播放，并将分配给与上面相同的事件。 因为这些资产被规范化为 Unity 中，以便它不修剪衰减这两个资产的卷。
3. 一起玩这两种声音。 将移动头脑大约感觉如何空间这听起来。

**方案 2**
1. 下载[roboraid_enemy_explo_summed.wav](images/roboraid-enemy-explo-summed.wav)和通过空间声音播放设置并将分配给一个事件。
2. 播放此资产本身，然后将其对事件进行比较从方案 1。
3. 请尝试不同的平衡 mono 和立体声文件。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Charles Sinex" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Charles Sinex</b><br>音频工程师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅
* [空间声音](spatial-sound.md)
* [对于 Microsoft HoloLens RoboRaid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)
