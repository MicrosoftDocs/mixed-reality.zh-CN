---
title: 在混合现实应用程序中使用声音
description: 空间音效是用于混合现实应用程序中的浸入式、可访问性和 UX 设计的强大工具。
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality，空间音质，设计，样式
ms.openlocfilehash: c069095808eaa9d31b1ffa41dbaa29c9f635837b
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641067"
---
# <a name="using-sound-in-mixed-reality-applications"></a>在混合现实应用程序中使用声音

使用声音通知并强化用户的应用程序状态的心理模型。 如果合适，请使用 spatialization 将声音置于混合世界。 以这种方式连接听觉和视觉对象可使许多交互的直观特性，从而提高用户信心。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-should-i-add-sounds"></a>我应何时添加声音？
由于缺少物理接口，混合现实应用程序通常比二维屏幕上的应用程序需要更高的声音。 应在通知用户或强化交互时添加声音。

### <a name="inform-and-reinforce"></a>通知和强化
* 对于不是由用户启动的事件（例如通知），请考虑添加声音，以通知用户发生了更改。
* 交互可能有多个阶段。 请考虑使用声音来强化阶段转换。

请参阅下面有关交互、事件和建议的声音特征的示例。

### <a name="exercise-restraint"></a>运动挡板
用户无限制音频信息的容量：
* 每个声音应该传递一条特定、有价值的信息，
* 当播放声音以通知用户时，请暂时减少其他声音的音量
* 对于按钮悬停声音（见下文），请添加一个时间延迟，以防止过多的声音触发

### <a name="dont-rely-solely-on-sounds"></a>不要完全依赖于声音
如果用户可以听到声音，则很有价值，但请确保应用程序在声音可用时仍可用。
* 用户可能听力障碍
* 您的应用程序可能会在更高的环境中使用
* 用户可能出于禁用设备音频的隐私或其他原因

## <a name="how-should-i-sonify-interactions"></a>应该如何 sonify 交互？
混合现实中的交互类型包括手势、直接操作和语音。 使用以下建议特征为这些交互选择或设计声音。

### <a name="gesture-interactions"></a>手势交互
在混合现实中，用户可以使用光标与按钮交互。 按钮操作通常在用户已释放按钮而不是按下该按钮时执行，以允许用户有机会取消交互。 使用声音来强化这些阶段。 此外，若要协助用户以较远的按钮为目标，请考虑使用光标悬停声音。
* 按下 "声音" 应具有一个简短的 tactile 单击。 示例： [MRTK_ButtonPress](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 按钮 unpress 的声音应具有类似的 tactile 感觉。 升高的音调与按下的声音，强调完成的意义。 示例： [MRTK_ButtonUnpress](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* 对于 "悬停声音"，请考虑使用细小的和非威胁的声音，如低频率 thud 或凹凸。


### <a name="direct-manipulation"></a>直接操作
在 HoloLens 2 上，已表述的手动跟踪支持直接操作用户界面元素。 声音对于缺少物理反馈很重要。

**按钮按下**声音对于直接操作非常重要，因为用户在到达密钥行进的底部时不需要实际的指示。 关键旅行的直观指示器可以是小型、微妙和封闭像素。 与手势交互一样，按下按钮时，按钮应具有短暂、tactile 的声音（如单击），而 unpresses 应具有类似的单击带有凸起间距。
* 示例： [MRTK_ButtonPress](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 示例： [MRTK_ButtonUnpress](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

确认直接操作中的**抓取**或**发布**很难以直观的方式进行通信。 用户的手常常会受到任何视觉效果的影响，而 expression-bodied 对象却缺乏现实的视觉对象。 与此相反，声音可以有效地传达成功的获取和释放交互。
* 抓取操作应该具有短暂的 muffled tactile 声音，可唤起围绕对象的抓手指。 有时会出现 "whoosh" 声音，这会导致声音在抓取时传达手的运动。 示例： [MRTK_Move_Start](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Release 操作应该具有类似的短暂和 tactile 的声音，通常是从抓住声音倒向下并按相反的顺序进行的，这会产生影响，然后使用 "whoosh" 将对象的状态传达到适当位置。 示例： [MRTK_Move_End](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

**绘图**交互应有一个循环、持久的声音，该声音的音量由用户的手控件控制，当用户的手仍在使用时完全无提示，并且在用户的手中快速移动时，它是完全无提示的。



### <a name="voice-interactions"></a>语音交互
语音交互通常具有微妙的视觉元素。 使用声音强化交互阶段。 请考虑选择更多色调声音，将它们与手势区分开来，并直接操作声音。

* 语音命令**确认**使用有正负音。 增加的声音和最大的音乐间隔在此都有效。
* 使用较短的、不太正值的**语音命令。** 避免否定声音;相反，请使用更 percussive 的中性声音与应用程序进行通信，以进行交互。
* 如果你的应用程序使用唤醒字词，请在设备**开始侦听**时使用一小段短暂的声音，并在应用程序侦听时使用细小的循环声音。 

### <a name="notifications"></a>通知
通知会传达应用程序状态更改和用户不启动的其他事件，如进程完成、消息和调用。

在混合现实中，移动的对象可以移出用户的视图字段。 带有 spatialized 声音的**动画对象**，这些对象依赖于对象和运动速度。
* 它还有助于在动画结束时播放 spatialized 声音，以通知用户新位置
* 对于逐步运动，移动过程中的 "whoosh" 声音将帮助用户跟踪对象

**消息通知**最有可能被听到多次，有时很快就会出现。 这一点很重要，因为它不会显得有些问题。 Mid 正面的声音声音在此处有效。

* 对于手机铃声，调用应具有相似的质量。 它们通常会循环播放音乐短语，直到用户应答呼叫。
* 语音通信连接和断开连接应具有短暂的色调声音。 连接声音应具有一个正负音，指示连接成功，而断开连接声音应为指示调用完成的非特定声音。

## <a name="spatialization"></a>Spatialization
Spatialization 使用立体声耳机或扬声器将声音置于混合世界。

### <a name="which-sounds-should-i-spatialize"></a>我应该 spatialize 哪些声音？
当声音与具有空间位置的事件关联时，应 spatialized。 这包括 UI、包含的 AI 声音和视觉指示器。

Spatializing**用户界面**元素可帮助整理用户的 sonic "space"，方法是将已锁定的立体声声音的数目限制为其打印头。 特别是在直接操作交互中，在 spatialized 音频反馈时，接触、抓取和释放感觉更自然。 但请参阅下面有关这些元素的距离衰减情况。

Spatializing**视觉对象指示器**和所介绍的 **AI 声音**直观地通知用户在视图外的情况。
    
与此相反，应避免 spatialization 用于 **_faceless_ AI 声音**，并避免使用未定义好的空间位置的其他元素。 如果没有相关的视觉元素，Spatialization 可能会分散用户认为有一个视觉元素无法找到。

添加 spatialization 将产生一定的 CPU 开销。 许多应用程序最多可以同时播放两个声音。 在这种情况下，spatialization 的成本可能会忽略不计。 可以使用 MRTK 帧速率监视器来判断添加 spatialization 的影响。 

### <a name="when-and-how-should-i-apply-distance-based-attenuation"></a>何时以及如何应用基于距离的衰减？
在现实生活中，远离远处的声音会更安静。 音频引擎可以根据源距离对此衰减建模。 在传达相关信息时，请使用基于距离的衰减。

与**视觉对象指示器**、**动画影像**和其他信息性声音的距离通常与用户相关。 使用基于距离的衰减直观地提供此提示。
* 调整每个源的衰减曲线，使其适应混合世界空间的大小。 音频引擎的默认曲线通常适用于非常大（最多为半 kilometer）空间。

强调按钮和其他交互的**渐进式阶段**的声音不应应用衰减。 这些声音的加强效果通常比与按钮通信的重要性更重要。 变体可能会让人分散注意力，尤其是在键盘上，很多按钮单击将会连续听到。

### <a name="which-spatialization-technology-should-i-use"></a>我应该使用哪种 spatialization 技术？
使用耳机或 HoloLens 扬声器时，请使用基于 HRTF （head 相关传输函数）的 spatialization 技术。 它们对现实世界内的声音传播建模。 即使在一侧的一侧有一个声音源，也会出现一些衰减和延迟的情况。 相反，发言人摇摄仅依赖于衰减，在右侧的声音（反之亦然）时，它会在左侧的耳中应用总衰减。 对于正常听觉的侦听器，这种情况可能会令人感到不安，对于在一个 ear 中具有听力障碍的侦听器，此情况可能不

## <a name="next-steps"></a>后续步骤
* [在 Unity 中使用空间音效](spatial-sound-in-unity.md)
* [Roboraid 的案例研究](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour 的案例研究](case-study-spatial-sound-design-for-holotour.md)

