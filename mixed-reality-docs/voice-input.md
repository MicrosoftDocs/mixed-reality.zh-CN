---
title: 语音输入
description: 语音输入是适用于 HoloLens 和 Windows Mixed Reality 沉浸式耳机的核心输入。 语音可用于命令、听写、Cortana 等。
author: Hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv、语音、cortana、语音、输入
ms.openlocfilehash: f2ae18d4063c7c4a63346a1202cacaa7fbbdf959
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723186"
---
# <a name="voice-input"></a>语音输入

![语音输入](images/UX/UX_Hero_VoiceCommand.jpg)

在 HoloLens 上，语音是重要输入形式之一。 它使你可以直接在无需使用[手型手势](gaze-and-commit.md#composite-gestures)的情况下直接执行命令。 可以将语音输入作为一种传达意图的自然方式。 语音在遍历复杂接口时特别有用，因为它允许用户通过一个命令剪切嵌套菜单。

语音输入由支持所有其他_通用 Windows 应用_中的语音的[同一引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)提供支持。 在 HoloLens 上，语音识别将始终在 "设置" 中配置的 Windows 显示语言中工作。 

<br>

## <a name="voice-and-gaze"></a>语音和注视

使用语音命令时（head 或眼睛）看起来通常用作目标机制，无论使用的是光标（"select"），还是将命令隐式通道到你要查看的应用程序。 为此，可能甚至不需要显示任何看起来像的光标 _（"请参阅它）_ "。 当然，一些语音命令根本不需要目标，如 "开始" 或 "你好 Cortana"。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>语音输入</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️（带有麦克风）</td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select" 命令

**HoloLens（第一代）**

即使不将语音支持专门添加到应用，用户也可以通过口述系统语音命令 "select" 来激活全息影像。 此行为与在 HoloLens 上的[点击](gaze-and-commit.md#composite-gestures)，按下[hololens clicker](hardware-accessories.md#hololens-clicker)上的 "选择" 按钮或在[Windows Mixed Reality 运动控制器](motion-controllers.md)上按下触发器的行为相同。 你将听到声音，并看到带有 "select" 的工具提示显示为确认。 "Select" 是通过低功耗关键字检测算法来实现的，因此，在任何时候，你始终都可以使用它，而不管你在哪一边，你都可以随时使用。

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        若要在 HoloLens 2 中使用 "选择" 语音命令，首先需要打开 "注视" 光标作为指针。 让它变得更容易记住，只需说 "选择"。<br><br>
        若要退出此模式，只需通过空中点击，使用手指接近按钮，或使用系统手势再次使用。<br>
        <br>
        *图像：说 "选择" 以使用声音命令进行选择*
    :::column-end:::
        :::column:::
       ![用户可以将 "选择" 用于所选的语音命令。](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a>“你好小娜”

你还可以说 "你好 Cortana" 来随时显示 Cortana。 您无需等待她继续询问她的问题或给她发出说明，例如，尝试说 "你好 Cortana，天气是什么？"。 作为单个句子。 有关 Cortana 和你可以执行的操作的详细信息，只需咨询她！ 说 "你好 Cortana，我该怎么办？" 然后，她将获取工作和建议命令的列表。 如果已进入 Cortana 应用，还可以单击 " **？** " 图标，提取此相同的菜单。

**HoloLens 特定的命令**
* “我可以说什么？”
* "转到开始"-而不是[布隆](system-gesture.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)
* "启动 <app>"
* "移动 <app>
* "拍摄照片"
* "开始录制"
* "停止录制"
* "增加亮度"
* "降低亮度"
* "增加音量"
* "降低音量"
* "静音" 或 "取消静音"
* "关闭设备"
* "重新启动设备"
* "进入睡眠状态"
* "它是什么时间？"
* "我有多少电池剩余电量？"



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"看，说它"<br>
        HoloLens 为语音输入提供了一个 "查看 it，假设 it" 模型，其中按钮上的标签告诉用户他们可以表达的语音命令。 例如，在 HoloLens （第一代）中查看应用窗口时，用户可以说 "调整" 命令，该命令显示在应用栏中，用于调整应用在世界中的位置。<br>
        <br>
        *图像：用户可以说 "调整" 命令，该命令显示在应用程序栏中以调整应用的位置*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![查看应用程序窗口或全息图时，用户可以在应用程序栏中显示 "调整" 命令，以调整应用程序在世界中的位置](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        当应用遵循此规则时，用户可以轻松地了解要控制系统的内容。 为加强这一点，当 gazing （第一代）中的按钮时，你将看到一个 "声音停留" 工具提示，如果按钮已启用语音，则会出现一秒钟，并显示 "按下" 命令。 若要在 HoloLens 2 中显示语音工具提示，请通过说 "选择" 或 "我可以说什么" （请参阅图像）来显示语音光标。 <br>
        <br>
        *图像： "查看它，假设" 命令显示在按钮下方*
    :::column-end:::
        :::column:::
       ![查看它，假设 "](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a>用于快速全息影像操作的语音命令

在 gazing 时，可以使用许多语音命令来快速执行操作任务。 这些语音命令适用于你在世界上放置的应用程序窗口和3D 对象。

**全息图操作命令**
* 面部
* 更大 |完善
* 超过

在 HoloLens 2 上，你还可以结合眼睛创建更自然的交互，从而隐式地提供有关所引用内容的上下文信息。 例如，您可以简单地查看全息图，说 "放置_此_内容"，然后浏览到要放置它的位置，然后说 "移到_此处_"。
您也可以在复杂的计算机上查看全息部分，并说： "向我介绍有关_此_的详细信息"。



## <a name="discovering-voice-commands"></a>发现语音命令

某些命令（如上面用于快速操作的命令）可以隐藏。 若要了解可以使用的命令，请看一看对象并说 "我可以说什么？"。 将弹出的可能命令的列表。 你还可以使用打印头的光标来浏览并显示你前面每个按钮的语音工具提示。 

如果需要完整的列表，请随时说 "显示所有命令"。 


## <a name="dictation"></a>听写

语音听写可以更高效地向应用程序中输入文本，而不是使用[空中点击](gaze-and-commit.md#composite-gestures)。 这可以极大地加快用户的输入。

通过选择麦克风按钮开始 ![语音听写](images/micbuttonfordictation.png)<br>
*语音听写开始于选择键盘上的麦克风按钮*

任何时候在全息键盘处于活动状态时，都可以切换到听写模式，而无需键入。 选择文本输入框一侧的麦克风即可开始。


## <a name="adding-voice-commands-to-your-app"></a>向应用程序添加语音命令

考虑为生成的任何体验添加语音命令。 语音是一种功能强大、方便的控制系统和应用的方式。 由于用户使用各种方言和口音说话，恰当选择语音关键字将确保用户的命令得到清晰的解释。

### <a name="best-practices"></a>最佳实践

以下是一些有助于流畅语音识别的做法。
* **使用简明命令** - 如果可能的话，选择两个或更多音节的关键词。 不同口音的人说单音节词时倾向于使用不同的元音。 示例： "播放视频" 优于 "播放当前选定的视频"
* **使用简单词汇**-示例： "show note" 优于 "show placard"
* **确保命令是非破坏性的** - 确保语音命令可以执行的任何操作都是非破坏性的，并且可以很容易地撤消，以防在用户附近说话的另一个人意外触发命令。
* **避免使用类似的语音命令** - 避免注册多个听起来非常相似的语音命令。 示例： "显示更多" 和 "显示存储" 的发音可能非常相似。
* **不使用应用时请取消注册应用** - 当应用没有处于特定语音命令有效的状态时，请考虑取消注册应用，使其他命令不会与该命令混淆。
* **使用不同的口音进行测试** - 由具有不同口音的用户测试应用。
* **保持语音命令一致性** - 如果“返回”可转到上一页，请在应用程序中保持此行为。
* **避免使用系统命令** - 系统保留了以下语音命令。 应用程序不应使用这些命令。
   * “你好小娜”
   * “选择”
   * "中转到开始"

### <a name="advantages-of-voice-input"></a>语音输入的优点

语音输入是传达我们意图的自然方式。 语音在接口**遍历**上特别不错，因为它可以帮助用户遍历界面的多个步骤（用户在查看网页时可能会说 "返回"，而不是在应用中使用 "后退" 按钮）。 这一小段节省时间对用户的体验感到**非常强大，** 并为他们提供少量实现超级。 当我们忙得不可开交或同时处理多项任务时，使用语音也是一种方便的输入方法。 对于在键盘上键入很困难的设备，**语音听写**可能是输入文本的一种有效的替代方法。 最后，在某些情况下，看看注视和手势的**准确性范围**会受到限制，语音有助于消除用户的意图。 

**语音的使用如何让用户受益**
* 省时 - 它应该使最终目标更高效。
* 最大限度地减少工作量 - 它应该使任务更加流畅和轻松。
* 减少认知压力 - 它是直观的，易于学习和记忆。
* 它在社会上是可以接受的 - 它应该在行为方面符合社会规范。
* 它是常规的 - 语音很容易成为一种习惯行为。

### <a name="challenges-for-voice-input"></a>语音输入的挑战

虽然语音输入非常适合于许多不同的应用程序，但它也面临着几个难题。 了解语音输入的优点和挑战使应用程序开发人员能够更灵活地选择使用语音输入的方式和时间，并为用户提供良好的体验。

**连续输入控件的语音输入**细粒度控件是其中之一。 例如，用户可能想要更改其音乐应用中的音量。 她只是说 "更大"，但并不清楚系统的容量。 用户可能会说： "让它变得稍大一些"，但很难量化。 移动或缩放全息影像的方式同样困难。 

**语音输入检测的可靠性**虽然语音输入系统变得更好且更好，但有时它们可能会错误地听到和解释语音命令。
关键是通过在系统正在侦听时向用户提供反馈，并为系统理解哪些内容来明确理解用户的潜在问题，以解决应用程序中的这一难题。  

**共享空间中的语音输入**在与他人共享的空格中，语音可能无法社交。
以下是几个示例：
* 用户可能不想干扰其他人（例如，在安静库或共享办公室中）
* 用户可能会很难被视为公开的，
* 用户可能会在其他人正在侦听时感觉不舒服

**语音输入唯一或未知字词**当用户听写可能对系统未知的字词时（如昵称、某些俚语词或缩写），也会出现语音输入问题。 

**学习语音命令**尽管最终目标是自然地与系统进行对话，但有时应用程序仍然依赖于特定的预定义语音命令。
与大的语音命令集相关的挑战在于如何教授用户，而无需对用户进行重载，以及如何帮助用户保留它们。 

<br>

---

### <a name="voice-feedback-states"></a>语音反馈状态

当语音应用正确时，用户了解他们能说什么，并得到清晰的反馈 - 系统正确地听到了用户说的话。 这两个信号使用户在使用语音作为主要输入方法时充满自信。 下面的图表显示了识别语音输入时光标发生的情况以及它是如何将信息传达给用户的。


:::row:::
    :::column:::
       ![1。常规游标状态](images/voicefeedbackstates-regular.jpg)<br>
       **1. 常规游标状态**<br>
    :::column-end:::
    :::column:::
       ![2。传达语音反馈，然后消失](images/voicefeedbackstates-voice.jpg)<br>
        **2. 传达语音反馈，然后消失**<br>
    :::column-end:::
    :::column:::
       ![* 3。 常规游标状态](images/voicefeedbackstates-regular.jpg)<br>
       **3. 返回到常规游标状态**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>在混合现实中，用户应该知道的关于“语音”的重要事项
* 在将一个按钮设置为目标时，说“选择”（可以在任何位置使用这种方法来单击按钮）。
* 可以在某些应用中通过说出应用栏按钮的标签名称来执行操作。 例如，在查看应用时，用户可以说“移除”命令以从现实中移除应用（这样可以节省用手单击按钮的时间）。
* 说“你好小娜”可以启动 Cortana 侦听。 你可以向她提问（“你好小娜，埃菲尔铁塔有多高”），告诉她打开应用（“你好小娜，打开 Netflix”），或告诉她调出“开始”菜单（“你好小娜，带我回家”）等等。

## <a name="common-questions-and-concerns-users-have-about-voice"></a>用户对语音的常见问题和关注点
* 我可以说什么？
* 我如何知道系统正确听到了我说的话？
   * 系统总是理解错误我的语音命令。
   * 当我发出语音命令时，系统不会做出反应。
* 当我发出语音命令时，系统的反应是错误的。
* 我如何将我的语音定向到一个特定的应用或应用命令？
* 我可以使用语音来对 HoloLens 上的全息帧执行命令吗？

## <a name="communication"></a>通信

对于想要利用 HoloLens 提供的自定义音频输入处理选项的应用程序，请务必了解应用程序可使用的各种[音频流类别](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)。 Windows 10 支持多种不同的流类别，HoloLens 利用这三个类别来启用自定义处理，以优化为语音、通信和其他可用于环境环境音频的麦克风音频质量捕获（即 "摄像机"）方案。
* 为呼叫质量和旁白方案自定义 AudioCategory_Communications 流类别，并为客户端提供用户语音的 16kHz 24bit mono 音频流
* 为 HoloLens （Windows）语音引擎自定义 AudioCategory_Speech 流类别，并为其提供用户语音的 16kHz 24bit mono 流。 第三方语音引擎可以根据需要使用此类别。
* 为环境环境录音录音自定义 AudioCategory_Other 流类别，并为客户端提供 48kHz 24 位立体声音频流。

所有这种音频处理都是硬件加速，这意味着功能消耗的电能要比在 HoloLens CPU 上执行相同处理要少得多。 避免在 CPU 上运行其他音频输入处理，以最大程度地提高系统电池寿命，并利用内置的卸载音频输入处理。

## <a name="languages"></a>语言

HoloLens 2 还支持其他语言。 请记住，即使安装了多个键盘或应用尝试使用其他语言创建语音识别器，语音命令也始终会在系统的显示语言中运行。

## <a name="troubleshooting"></a>“疑难解答”

如果使用 "选择" 和 "你好 Cortana" 时遇到任何问题，请尝试移动到可取消选择的空间、远离噪音源或说出更大的声音。 目前，HoloLens 上的所有语音识别都专门针对美国英语的本机扬声器进行优化和优化。

对于 Windows Mixed Reality Developer Edition 版本2017，音频终结点管理逻辑将在初始 HMD 连接后注销并重新登录到 PC 桌面后正常运行。 在第一次注销/登录到 WMR 时，用户可能会遇到各种音频功能问题，范围从无音频切换到无音频切换，具体取决于首次连接 HMD 前系统的设置方式。

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>适用于 Unity 的 MRTK （混合现实工具包）中的语音输入
借助 **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，你可以轻松地为任何对象分配语音命令。 使用 MRTK 的**语音输入配置文件**定义关键字。 通过分配**SpeechInputHandler**脚本，你可以使任何对象响应语音输入配置文件中定义的关键字。 SpeechInputHandler 还提供了语音确认标签以提高用户信心。

* [MRTK-语音命令](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a>另请参阅
* [凝视和提交](gaze-and-commit.md)
* [本能交互](interaction-fundamentals.md)
* [MR 输入212：语音](holograms-212.md)
* [DirectX 中的语音输入](voice-input-in-directx.md)
* [Unity 中的语音输入](voice-input-in-unity.md)
