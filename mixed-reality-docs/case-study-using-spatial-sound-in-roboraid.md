---
title: 案例研究-在 RoboRaid 中使用空间音效
description: 空间音效是 Microsoft HoloLens 最令人兴奋的一项功能，它为用户提供了一种方法，让用户了解当对象不见视线时，会发生什么情况。
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，RoboRaid，空间音效
ms.openlocfilehash: 1482c914d261cae698a1460873b217b0683cd16b
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181937"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>案例研究-在 RoboRaid 中使用空间音效

本文介绍 Microsoft HoloLens 体验团队在创建[RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)的音频时遇到的独特挑战，这是一种混合现实的第一员射击。

## <a name="the-tech"></a>技术人员

[空间音效](spatial-sound.md)是 Microsoft HoloLens 最令人兴奋的一项功能，它为用户提供了一种方法，让用户了解当对象不见视线时，会发生什么情况。

在 RoboRaid 中，空间音质最明显且最有效的使用情况是提醒播放机在用户的外围视力之外发生的事情。 例如，Breacher 可以输入房间中的任何扫描壁，但如果不是面对其进入位置，可能会错过。 为了提醒您此 invasion，您将收到 Breacher 进入的位置的不同位音频，这让您知道您需要快速地停止它。

## <a name="behind-the-scenes"></a>幕后

为 HoloLens 应用程序创建空间音效的过程非常新且独一无二，缺少用于引用的过去项目可能会在遇到问题时导致很大的外在优势。 希望在创建 RoboRaid 时，我们所面临的音频挑战的示例可帮助你为自己的应用创建音频。

### <a name="be-mindful-of-taxing-the-cpu"></a>注意 CPU 的负担

在 CPU 上可以要求空间音质。 对于繁忙的体验（如 RoboRaid），在任何给定时间都需要将空间音质的实例保留为小于8。 在大多数情况下，只需设置不同音频事件的实例限制，就可以轻松地终止在达到限制后发生的任何实例。 例如，在无人机生成时，在任何给定时间，其 screams 限制为三个实例。 如果只考虑四个无人机可以一次生成，三个 screams 都非常多，因为您的大脑无法跟踪很多发音相似的音频事件。 这会释放其他空间声音事件的资源，例如敌人爆炸或敌人准备进行拍摄。

### <a name="rewarding-a-successful-dodge"></a>获得成功的减减

Dodging mechanic 是 RoboRaid 中游戏的最重要的一个方面，也是我们认为在 HoloLens 体验中真正唯一的东西。 这种情况下，我们想让 dodges 对播放机取得成功。 在开发中，我们的 Doppler "whizz" 听起来非常引人注目。 最初，我的计划是使用循环并使用卷、间距和筛选器对其进行实时操作。 此操作的实现非常复杂。因此，在提交资源以实际生成之前，我们使用 Doppler 效果融入的资产创建了一种廉价的原型，只是为了找出这种情况。 我们的出色开发人员使得这一 whizz 的资产在玩家的耳内 projectile 之前会播放一则相当于0.7 秒的时间，结果感觉非常惊人！ 不用说，我们借助了更复杂的解决方案并实现了原型。

*（有关创建带有内置 Doppler 效果的音频资产的详细信息，请参阅[100 Whooshes In 2 分钟](http://designingsound.org/2010/02/26/charles-deenen-special-100-whooshes-in-2-minutes/)。）*  
<br>
![成功 dodging 敌人的 projectile 通过一种满意的 whizz 来奖励玩家。](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>抛弃无效声音

最初，我们希望在成功 dodged 敌人 projectile 后，在玩家后面播放一声爆炸形声，但我们决定出于多种原因而 ditch。 首先，这并不像我们用于减减的 whizz。 当 projectile 碰到你后面的一堵墙后，游戏中会出现其他内容，这种情况很容易掩盖声音。 其次，我们在地面上没有冲突，因此当 projectile 到达地面而不是墙壁时，我们无法进行分解。 最后，空间音质会出现 CPU 开销。 精英 Scorpion 敌人（可以在墙壁内进行爬网）有一种特殊的攻击桃约八炮弹。 这不仅会使混合中出现巨大的混乱，而且还引入了一噼啪的噼啪声，因为它会导致 CPU 太难。

### <a name="communicating-a-hit"></a>通信命中

我们遇到了一个有趣的问题，我们认为这对于 HoloLens 体验是唯一的，因此很难有效地与他们所点击的玩家通信。 这会使混合现实体验成功，这就是你觉得故事正在进行。 这意味着您必须相信您在自己的客厅里，invasion 了一个外部机器人。

当玩家遇到问题时，他们很显然不会感觉任何问题，因此我们必须找到一种方法来说服游戏者 happed。 在传统游戏中，你可能会看到一个动画，它可以让你知道你的人物已命中，或者屏幕可能会以红色闪烁，你的人物可能 grunt。 由于这些类型的提示在混合现实体验中不起作用，因此我们决定将视觉提示与一种真正放大的声音组合在一起，这表示您已遭到破坏。 我创建了一个很好的声音，并使其突出，使其 ducked。 那么，为了使其更进一步，我们添加了一条短暂的警告音，就像是一个核 sub。 
<br>
![当播放机在 RoboRaid 中命中时，它们会看到视觉提示，但也会获得一个放大的音频提示，告知他们已损坏。](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>从小扬声器获得大声音

HoloLens 扬声器很小，并且非常适合于设备的需求，因此您无法听到太多的低端。 与开发智能手机或手持游戏设备类似，声音设计人员和作曲者必须注意其音频的频率内容。 我始终设计声音或使用全频率范围写入音乐，因为戴耳机是用户的一个选项。 但是，为了确保与 HoloLens 扬声器的兼容性，我偶尔运行测试，方法是在发生的任何 DAW 的主节点中放置一个 EQ。 EQ 设置包含大约600到 700 Hz 的高传递筛选器（不太陡）和低速传递筛选器（非常严重）。 这会让你大概如何在设备上播放声音。

如果你依赖于低音在音乐中进行更改，则可能会发现，当你应用此 EQ 设置时，音乐完全丢失了 root。 为了弥补这一点，我向低音添加了另一层，其中一个 octave 较高（带有一些丰富的谐波），并将其混合在一起，以获得 root。 有时，使用扭曲来使谐波会在上部范围内提供足够的频率内容，以使大脑认为它下面有一些内容。 这种情况适用于类似于影响、爆炸或声音等一段时间的，例如老板的超级攻击。 你确实不能依赖低端来使玩家了解影响或权重。 与音乐一样，使用扭曲来提供少量捕获。

### <a name="making-your-audio-cues-stand-out"></a>使您的音频提示突出

当然，团队中的每个人都希望 bombastic 音乐、枪支和古怪爆炸;但他们还希望能够听到 voiceover 或任何其他游戏关键的音频提示。

在具有各种频率的控制台游戏上，你可以根据声音的重要性，使用更多的选项来划分频率。 但对于 RoboRaid，我限制了从声音弯曲的频率范围。 例如，如果使用低刀筛选器并使其从较高的范围内弯曲，则不会有任何内容出现在声音上，因为没有太多的低端。

为了使 RoboRaid 的声音在设备上能够正常工作，我们必须通过为不同类型的声音创建清晰的重要性层次结构，来降低整个体验的动态范围并广泛使用放掉。 我根据重要性，将放掉设置为-2 到-6 dB。 我个人不喜欢在游戏中显而易见的放掉，所以我花了很多时间来优化淡入/淡出时间和体积衰减量。 我们为空间音效、非空间音效、VO 和干燥总线设置了单独的总线，无回音用于音乐，然后创建了非常高的优先级、关键和非关键总线。 然后，将这些资产设置为前往适当的总线。

我希望音频专业人员在处理 RoboRaid 时，会在其自己的应用上工作时有很多乐趣和惊喜。 我看不到（听不到！）在 Microsoft 以外的任何人都会提出的 HoloLens。

## <a name="do-it-yourself"></a>自制

我发现了一个使某些事件（如爆炸）听起来更大（例如，填满房间）的技巧，就是为该空间声音创建单声道资产，并将其与2D 立体声资产混合，以三维方式播放。 它确实会进行一些优化，因为立体声内容中的信息过多会降低 mono 资产的方向。 但是，若要获得平衡，将会产生非常大的声音，让玩家按正确的方向。

你可以使用以下音频资产自行尝试：

**应用场景 1**
1. 下载[roboraid_enemy_explo_mono .wav](images/roboraid-enemy-explo-mono.wav) ，并将其设置为通过空间音效播放，并将其分配给某个事件。
2. 下载[roboraid_enemy_explo_stereo .wav](images/roboraid-enemy-explo-stereo.wav) ，并将其设置为在2d 立体声中播放，并将其分配给上述相同的事件。 由于这些资产被规范化为 Unity，因此，这两个资产的衰减量使其不会被剪裁。
3. 同时播放两个声音。 四处移动您的头，看看它的工作方式。

**应用场景 2**
1. 下载[roboraid_enemy_explo_summed .wav](images/roboraid-enemy-explo-summed.wav) ，并将其设置为通过空间音效播放并分配到事件。
2. 单独播放此资产，然后将其与方案1中的事件进行比较。
3. 尝试对 mono 和立体声文件进行不同的平衡。



## <a name="see-also"></a>另请参阅
* [空间音效](spatial-sound.md)
* [RoboRaid for Microsoft HoloLens](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)
