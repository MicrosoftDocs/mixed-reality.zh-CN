---
title: 语音输入
description: 语音输入是 HoloLens 和 Windows Mixed Reality 沉浸式耳机的核心输入。 语音可以用于命令、 听写，Cortana，和的详细信息。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv、 语音、 cortana、 语音、 输入
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829948"
---
# <a name="voice-input"></a>语音输入

语音是输入上 HoloLens 的三种密钥形式之一。 它允许您直接命令而无需使用一张全息图[手势](gestures.md)。 您只需[注视](gaze.md)在一张全息图并把您的命令。 语音输入可以是你的意图进行通信的自然方式。 语音是尤其擅长于遍历复杂的接口，因为它允许用户通过用一个命令的嵌套菜单剪切。

语音输入作为后盾[相同的引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)，支持所有其他通用 Windows 应用中的语音。

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
    </tr>
     <tr>
        <td>语音输入</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ （使用麦克风）</td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select"命令

即使没有专门将语音支持添加到您的应用程序，用户可以只需通过说"选择"激活全息。 此行为与相同[敲击](gestures.md#air-tap)上 HoloLens，按选择按钮上[HoloLens clicker](hardware-accessories.md#hololens-clicker)，或按触发器上[Windows Mixed Reality 运动控制器](motion-controllers.md). 您将听到声音，并查看显示确认为"select"包含的工具提示。 "选择"被启用的低能耗关键字检测算法中，因此始终是可供你说，在任何时间最小电池寿命造成的影响，甚至在您身边手。

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。

!["Select"可以使用语音命令来选择](images/kma-voice-select-00170-800px.png)<br>
*"Select"可以使用语音命令来选择*

## <a name="hey-cortana"></a>Hey Cortana

也可以说"你好，小娜"，以在任何时候显示 Cortana。 无需等待她才会显示继续要求她您的问题，或为她提供一条指令-例如，尝试说"你好，小娜天气是什么？" 作为单个句子。 有关 Cortana 以及可以执行哪些操作的详细信息，只需让她 ！ 说"你好，小娜什么可以说？" 她将提起正在处理和建议的命令的列表。 如果您已在 Cortana 应用还可以单击 **？** 侧栏中请求此相同的菜单上的图标。

**特定于 HoloLens 的命令**
* “我可以说什么？”
* "转到主页"转到开始"-而不是[布隆](gestures.md#bloom)若要获取到[开始菜单](navigating-the-windows-mixed-reality-home.md#start-menu)
* "启动<app>"
* "移动<app>此处"
* "拍摄一张照片"
* "开始记录"
* "停止录制"
* "Increase 亮度"
* "Decrease 亮度"
* "提高音量"
* "降低音量"
* "静音"或者"取消静音"
* "关闭该设备"
* "重新启动设备"
* "转到睡眠状态"
* "什么时候是它？"
* "多少，还剩电池 do？"
* "调用<contact>"（需要 Skype 的 HoloLens）

## <a name="see-it-say-it"></a>"看，说"

HoloLens 具有"来看，说"语音输入模型上按钮的标签位置告知用户他们也可以说什么语音命令。 例如，在查看 2D 应用时，用户可以说出他们看到的应用栏中调整应用程序的世界中的位置的"调整"命令。

![在查看 2D 应用或全息图时，用户可以说他们看到的应用栏中调整应用程序的世界中的位置的"调整"命令](images/microphone-600px.png)

当应用按照此规则时，用户可以轻松了解如何说来控制系统。 为了强调这，一个按钮在观望时，你将看到"语音停留"工具提示出现在一秒钟之后如果按钮是启用语音的将显示要说"按"它的命令。

![查看它，请说命令出现下面的按钮](images/voice-seeitsayit-600px.png)<br>
*"到它，请说"按钮下方显示的命令*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>快速全息图操作的语音命令

此外，还有大量的语音命令可以同时在一张全息图，若要快速执行操作任务观望说。 这些语音命令适用于 2D 应用程序，以及已放置在世界中的三维对象。

**全息图操作命令**
* 人脸我
* 更大 |增强
* 较小

## <a name="dictation"></a>听写

而不是类型化[空气分流点](gestures.md#air-tap)，语音听写可能会更有效，到应用中输入文本。 这可以极大地加快用户更轻松地输入。

![通过选择麦克风按钮来启动语音听写](images/micbuttonfordictation.png)<br>
*选择键盘上的麦克风按钮启动语音听写*

每当 holographic 键盘时处于活动状态，可以切换到无需键入听写模式。 选择的文本输入框，若要开始的一侧的麦克风。

## <a name="communication"></a>通信

对于想要利用的处理选项提供的 HoloLens 的自定义音频输入的应用程序，务必要了解各种[音频流类别](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)可以使用您的应用程序。 Windows 10 支持多个不同的流类别和 HoloLens，可以使用的这三个启用自定义处理，以优化为语音、 通信和其他的可以用于环境的环境音频量身打造的麦克风音频质量捕获 （即"摄像机"） 的方案。
* AudioCategory_Communications 流类别为调用质量和旁白方案自定义，可提供 16 kHz 24 位单声道音频流的用户的语音的客户端
* AudioCategory_Speech 流类别为 HoloLens (Windows) 语音引擎自定义，并为其提供的用户的声音的 16 kHz 24 位 mono 流。 如果需要可以通过第三方语音引擎使用此类别。
* AudioCategory_Other 流类别为环境的环境音频录制自定义，可提供客户端的 48 kHz 24 位立体声音频流。

所有这些音频处理过程是硬件加速这意味着功能释放比如果 HoloLens CPU 上执行相同的过程的少了很多电量。 避免运行上要延长系统电池寿命和充分利用内置的 CPU 的处理其他音频输入中，卸载音频输入的处理。

## <a name="troubleshooting"></a>疑难解答

如果您遇到任何问题使用"选择"和"你好，小娜"，请尝试将移动到更安静的空间，打开离开的干扰，或通过噪音谈到的源。 在此期间，在 HoloLens 上的所有语音识别是优化和优化是特定于的美式英语的母语。

对于 Windows 混合现实 Developer Edition 版本 2017年中，音频终结点管理逻辑将正常显示 （永久） 后到 PC 桌面出并再次在记录之后的初始 HMD 连接。 之前该的第一个登录的扩大/缩小事件 WMR OOBE 完成之后，用户可能会遇到各种范围不包括音频，具体取决于系统已设置在首次连接 HMD 之前切换到无音频的音频功能问题。

## <a name="see-also"></a>请参阅
* [DirectX 中的语音输入](voice-input-in-directx.md)
* [Unity 中的语音输入](voice-input-in-unity.md)
* [MR 输入 212：语音](holograms-212.md)
