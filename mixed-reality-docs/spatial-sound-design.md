---
title: 在混合现实应用程序中使用空间音效
description: 空间音效是一个强大的工具，可用于在混合现实应用程序中进行浸入式、可访问性和 UX 设计。
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality，空间音质，设计，样式
ms.openlocfilehash: 34923e1ebfc8e46ea8e67a4444fe3c2691efd4db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182007"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>如何在混合现实应用程序中使用声音

您可以使用声音来通知和强化用户应用程序状态的心理模型。 如果合适，请使用 spatialization，将声音置于混合现实世界中。 以这种方式连接听觉和视觉对象时，可以加深交互的直观特性并提高用户信心。
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>何时添加声音
混合现实应用程序通常比2D 应用程序需要更高的声音，因为它们缺乏 tactile 接口。 在通知用户或强化交互时添加声音。

### <a name="inform-and-reinforce"></a>通知和强化
* 对于不是由用户启动的事件（例如通知），请使用声音通知用户发生了更改。
* 交互可能有多个阶段。 使用声音强化过渡过渡。

请参阅下面的交互、事件和建议的声音特征的示例。

### <a name="exercise-restraint"></a>运动挡板
用户无限制音频信息。
* 每个声音应传达特定的有价值信息。
* 当应用播放声音以通知用户时，请暂时减少其他声音的音量。
* 对于按钮悬停声音（请参阅以下信息），添加一个时间延迟，以防止过多的声音触发。

### <a name="dont-rely-solely-on-sounds"></a>不要完全依赖于声音
使用良好的声音对于用户非常有用。 但请确保即使关闭声音，应用程序也能使用。
* 用户可能会收到听力障碍。
* 您的应用程序可能会在更高的环境中使用。
* 用户可能会出于隐私目的或其他原因而禁用设备音频。

## <a name="how-to-sonify-interactions"></a>如何 sonify 交互
混合现实中的交互类型包括手势、直接操作和语音。 使用以下建议特征为这些交互选择或设计声音。

### <a name="gesture-interactions"></a>手势交互
在混合现实中，用户可以通过使用鼠标与按钮交互。 通常，当用户释放而不是按下按钮时，按钮操作会让用户有机会取消交互。 使用声音来强化这些阶段。 若要协助用户以较远的按钮为目标，还应考虑使用指针悬停声音。
* 按钮-按下声音应为简短的 tactile "单击"。<br/>示例： [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 按钮-"unpress" 声音应具有类似的 tactile 感觉。 比按下声音更高的跨度强调完成的意义。<br/>示例： [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* 对于 "悬停声音"，请考虑使用细小的和非威胁的声音，如低频率 thud 或凹凸。

### <a name="direct-manipulation"></a>直接操作
在 HoloLens 2 上，已表述的手动跟踪支持直接操作用户界面元素。 当没有其他物理反馈时，声音非常重要。

*按钮按下*声音对于直接操作非常重要，因为当用户到达关键笔画的底部时，用户不会收到任何其他指示。 关键旅行的声音指示器可以是小型、微妙和封闭像素。 与手势交互一样，按钮按下会显示短暂的 tactile 声音，如单击。 Unpresses 应该具有类似的单击声音，但具有凸起的音调。
* 示例： [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 示例： [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

难以直观地确认获取或释放操作。 用户的手常常会受到任何视觉效果的影响，而 expression-bodied 对象却缺乏现实的视觉对象。 声音可以有效地传达成功的获取和释放交互。
* 抓取操作应该具有一个 muffled 的简短 tactile 声音，可唤起围绕对象的抓手。 有时还会有一个 "whoosh" 声音，该声音会导致抓住声音传达手的运动。<br/>示例： [MRTK_Move_Start .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Release 操作应该获得类似的简短和 tactile 的声音。 它通常比抓住声音和反向顺序下的音调更小，但影响，然后使用 "whoosh" 传达对象正在进行的结算。<br/>示例： [MRTK_Move_End .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

*绘图*交互应会获得持久的循环声音，其卷由用户的移动决定。 当用户的手仍在 loudest 时，它应为无提示。

### <a name="voice-interactions"></a>语音交互
语音交互通常具有微妙的视觉元素。 使用声音来强化交互阶段。 您可能想要使用更多的声音，将它们与手势和直接操作声音区分开来。

* 语音命令*确认*使用有正负音。 升高的声音和主要的音乐间隔都是有效的。
* 对于语音命令*失败*，请使用较短的、不太积极的音调。 避免出现负面声音。 相反，请使用更 percussive 的中性声音来传达应用程序正在交互的活动。
* 如果你的应用程序具有唤醒字词，则在设备*开始侦听*时，请使用短暂的短暂音。 在*应用程序侦听时使用*细小循环声音。

### <a name="notifications"></a>通知
通知会传达应用程序状态更改和用户不启动的其他事件（例如进程完成、消息和电话呼叫）。

在混合现实中，对象有时会移出用户的视图字段。 使用依赖于对象类型和运动速度的 spatialized 声音移动*动画对象*。
* 它有助于在动画结束时播放 spatialized 声音，以通知用户对象的新位置。
* 对于逐步运动，移动过程中的 "whoosh" 声音有助于用户跟踪对象。

*消息通知*声音可能会反复听到，有时会迅速继续。 这一点很重要，因为它们不会显得有些问题。 中间的正面色调声音有效。

* 传入呼叫声音对于手机铃声应该具有相似的质量。 通常，它们会循环播放音乐短语，直到用户应答呼叫。
* 语音通信连接和断开连接应具有短暂的色调声音。 连接声音应为正片，指示连接成功。 断开连接声音应该是一种中性声音，指示调用完成。

## <a name="handle-spatialization"></a>处理 spatialization
Spatialization 使用立体声耳机或扬声器将声音置于混合现实世界中。

### <a name="which-sounds-to-spatialize"></a>哪些声音 spatialize
当声音与具有空间位置的事件关联时，应 spatialized。 这包括 UI、包含的 AI 声音和视觉指示器。

Spatialize*用户界面*元素，可通过限制他们听到的立体声声音数量来帮助整理用户的 sonic "space"。 在 spatialized 音频反馈时，处理触摸、抓取和释放感觉更自然的交互。 请考虑以下有关这些元素的距离衰减的信息。

Spatialize*直观的指示器*和三应的*AI 声音*，以直观地通知用户这些东西超出了视图的范围。
    
与此相反，应避免 spatialization 用于*FACELESS AI 声音*，还应避免缺少定义良好的空间位置的其他元素。 如果没有相关的视觉元素，Spatialization 可能会分散用户以为其无法找到的可视元素。

Spatialization 有一定的 CPU 开销。 许多应用程序最多可以同时播放两个声音。 在这种情况下，spatialization 的成本可能会忽略不计。 可以使用 MRTK 帧速率监视器来判断添加 spatialization 的影响。

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>何时以及如何应用基于距离的衰减
在现实生活中，远离远处的声音会更安静。 音频引擎可以根据源距离对此衰减建模。 在传达相关信息时，请使用基于距离的衰减。

与*视觉对象指示器*、*动画影像*和其他信息性声音的距离通常与用户相关。 使用基于距离的衰减直观地提供提示。

调整每个源的衰减曲线，使其适应混合现实世界的空间大小。 音频引擎的默认曲线通常适用于非常大（最多为半 kilometer）空间。

强调按钮操作和其他交互的*渐进式阶段*的声音不应应用衰减。 这些声音的加强效果通常比与按钮通信的重要性更重要。 变体可能会分散注意力，尤其是在键盘上，很多按钮单击时可能会被连续听到。

### <a name="which-spatialization-technology-to-use"></a>使用哪种 spatialization 技术
使用耳机或 HoloLens 扬声器，使用基于 head 的传输功能（HRTF）的 spatialization 技术。 这些技术对现实世界内的声音的传播建模。 即使当某个声源位于一端时，声音仍会传播到远处的耳，同时出现一些衰减和延迟。 相反，发言人摇摄仅依赖于衰减，在左侧的耳（反之亦然）的情况下，会在左侧的耳上应用总衰减。 对于在一条耳中听力有障碍的侦听器，此方法可能不适合 "正常听觉" 侦听器并且无法访问。

## <a name="next-steps"></a>后续步骤
* [在 Unity 中使用空间音效](spatial-sound-in-unity.md)
* [Roboraid 的案例研究](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour 的案例研究](case-study-spatial-sound-design-for-holotour.md)
