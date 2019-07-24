---
title: 语音输入
description: 语音输入是适用于 HoloLens 和 Windows Mixed Reality 沉浸式耳机的核心输入。 语音可用于命令、听写、Cortana 等。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv、语音、cortana、语音、输入
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829948"
---
# <a name="voice-input"></a>语音输入

Voice 是 HoloLens 上三种关键形式的输入之一。 它使你可以直接在无需使用[手势](gestures.md)的情况下直接执行命令。 只需[注视](gaze.md)一个全息图, 就可以说出命令。 语音输入可以自然地传达意向。 语音在遍历复杂接口时特别有用, 因为它允许用户使用一条命令剪切嵌套菜单。

语音输入由支持所有其他通用 Windows 应用中的语音的[同一引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)提供支持。

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

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
        <td>语音输入</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (带有麦克风)</td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select" 命令

即使不将语音支持专门添加到你的应用, 用户也可以通过说 "选择" 来激活全息影像。 此行为与在 HoloLens 上的[点击](gestures.md#air-tap), 按下[hololens clicker](hardware-accessories.md#hololens-clicker)上的 "选择" 按钮或在[Windows Mixed Reality 运动控制器](motion-controllers.md)上按下触发器的行为相同。 你将听到声音, 并看到带有 "select" 的工具提示显示为确认。 "Select" 是通过低功耗关键字检测算法来实现的, 因此, 在任何时候, 你始终都可以使用它, 而不管你在哪一边, 你都可以随时使用。

> [!NOTE]
> 即将[推出](index.md#news-and-notes)特定于 HoloLens 2 的更多指导。

![说 "选择", 使用语音命令进行选择](images/kma-voice-select-00170-800px.png)<br>
*说 "选择", 使用语音命令进行选择*

## <a name="hey-cortana"></a>Hey Cortana

你还可以说 "你好 Cortana" 来随时显示 Cortana。 您无需等待她继续询问她的问题或给她发出说明, 例如, 尝试说 "你好 Cortana 的天气是什么？"。 作为单个句子。 有关 Cortana 和你可以执行的操作的详细信息, 只需咨询她! 说 "你好, 我可以说什么？"。 然后, 她将获取工作和建议命令的列表。 如果已进入 Cortana 应用, 还可以单击 " **？** " 图标, 提取此相同的菜单。

**HoloLens 特定的命令**
* “我可以说什么？”
* "转到主页" 或 "转到开始"-而不是[布隆](gestures.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)
* "启动<app>"
* "移动<app>到此处"
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
* "呼叫<contact>" (需要 Skype for HoloLens)

## <a name="see-it-say-it"></a>"看, 说它"

HoloLens 为语音输入提供了一个 "查看 it, 假设 it" 模型, 其中按钮上的标签告诉用户他们可以表达的语音命令。 例如, 查看2D 应用程序时, 用户可以说 "调整" 命令, 该命令显示在应用程序栏中, 用于调整应用在世界中的位置。

![查看2D 应用或全息图时, 用户可以说 "调整" 命令, 该命令显示在应用栏中, 用于调整应用在世界中的位置。](images/microphone-600px.png)

当应用遵循此规则时, 用户可以轻松地了解要控制系统的内容。 为此, 在按钮上 gazing 时, 你将看到一个 "声音停留" 工具提示, 如果按钮已启用语音, 则会出现一次, 并显示 "按下" 命令。

![查看它, 假设 "](images/voice-seeitsayit-600px.png)<br>
*"看起来, 说它" 命令显示在按钮下面*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>用于快速全息影像操作的语音命令

在 gazing 时, 还可以使用多个语音命令来快速执行操作任务。 这些语音命令适用于在世界上放置的2D 应用和3D 对象。

**全息图操作命令**
* 面部
* 更大 |完善
* 超过

## <a name="dictation"></a>听写

语音听写可以更高效地向应用程序中输入文本, 而不是使用[空中点击](gestures.md#air-tap)。 这可以极大地加快用户的输入。

![语音听写开始, 选择 "麦克风" 按钮](images/micbuttonfordictation.png)<br>
*语音听写开始于选择键盘上的麦克风按钮*

任何时候在全息键盘处于活动状态时, 都可以切换到听写模式, 而无需键入。 选择文本输入框一侧的麦克风即可开始。

## <a name="communication"></a>通信

对于想要利用 HoloLens 提供的自定义音频输入处理选项的应用程序, 请务必了解应用程序可使用的各种[音频流类别](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)。 Windows 10 支持多种不同的流类别, HoloLens 利用这三个类别来启用自定义处理, 以优化为语音、通信和其他可用于环境环境音频的麦克风音频质量捕获 (即 "摄像机") 方案。
* AudioCategory_Communications 流类别自定义用于调用质量和旁白方案, 并为客户端提供用户语音的 16kHz 24bit mono 音频流
* 为 HoloLens (Windows) 语音引擎自定义 AudioCategory_Speech 流类别, 并为其提供用户语音的 16kHz 24bit mono 流。 第三方语音引擎可以根据需要使用此类别。
* 为环境环境录音录音自定义 AudioCategory_Other 流类别, 并为客户端提供 48kHz 24 位立体声音频流。

所有这种音频处理都是硬件加速, 这意味着功能消耗的电能要比在 HoloLens CPU 上执行相同处理要少得多。 避免在 CPU 上运行其他音频输入处理, 以最大程度地提高系统电池寿命, 并利用内置的卸载音频输入处理。

## <a name="troubleshooting"></a>疑难解答

如果使用 "选择" 和 "你好 Cortana" 时遇到任何问题, 请尝试移动到可取消选择的空间、远离噪音源或说出更大的声音。 目前, HoloLens 上的所有语音识别都专门针对美国英语的本机扬声器进行优化和优化。

对于 Windows Mixed Reality Developer Edition 版本 2017, 音频终结点管理逻辑将在初始 HMD 连接后注销并重新登录到 PC 桌面后正常运行。 在第一次注销/登录到 WMR 时, 用户可能会遇到各种音频功能问题, 范围从无音频切换到无音频切换, 具体取决于首次连接 HMD 前系统的设置方式。

## <a name="see-also"></a>请参阅
* [DirectX 中的语音输入](voice-input-in-directx.md)
* [Unity 中的语音输入](voice-input-in-unity.md)
* [MR 输入 212：语音](holograms-212.md)
