---
title: MR 输入 212-语音
description: 按照本演练使用 Unity、 Visual Studio 和 HoloLens 学习语音概念的详细信息进行编码操作。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 学院、 教程中，语音
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590379"
---
>[!NOTE]
>混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。  在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。  这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  它们都将保留在受支持的设备上继续工作。 将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。  在发布时，将使用这些教程的链接更新此通知。

<br>

# <a name="mr-input-212-voice"></a>MR 输入 212:语音

[语音输入](voice-input.md)为我们提供了另一种方法与我们全息进行交互。 语音命令的工作非常自然和简单的方式。 设计你的语音命令，以便它们：

* 自然
* 容易记住
* 适当的上下文
* 充分不同于在同一上下文中的其他选项

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

在中[MR 基础知识 101](holograms-101.md)，我们使用 KeywordRecognizer 来生成两个简单的语音命令。 在 MR 输入 212，我们将深入研究，了解如何：

* 设计针对 HoloLens 语音引擎进行了优化的语音命令。
* 使用户知道哪些语音的命令都可用。
* 确认我们已收到用户的语音命令。
* 了解什么是用户说： 使用听写识别器。
* 使用语法识别器来侦听基于 SRGS 或语音识别语法规范，文件的命令。

在本课程中，我们将再度讨论模型资源管理器，它在我们构建[MR 输入 210](holograms-210.md)并[MR 输入 211](holograms-211.md)。

>[!IMPORTANT]
>使用 Unity 和混合现实工具包的较旧版本记录中的以下章节每个嵌入的视频。 准确且最新的分步说明时，可能会看到脚本和已过期的相应视频中的视觉对象。 保持为长期的视频和因为涵盖了概念仍然适用。


## <a name="device-support"></a>设备支持

<table>
<tr>
<th>课程</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>MR 输入 212:语音</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>先决条件

* 使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。
* 一些基本C#编程功能。
* 您应当已完成[MR 基础知识 101](holograms-101.md)。
* 您应当已完成[MR 输入 210](holograms-210.md)。
* 您应当已完成[MR 输入 211](holograms-211.md)。
* HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。

### <a name="project-files"></a>项目文件

* 下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)所需的项目。 需要 Unity 2017.2 或更高版本。
* 取消存档到您的桌面或其他轻松地访问位置的文件。

>[!NOTE]
>如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)。

### <a name="errata-and-notes"></a>勘误表和说明

* "启用仅我的代码"必须禁用 (*未选中*) 在 Visual Studio 工具-> 选项-> 调试以便你的代码中命中断点。

## <a name="unity-setup"></a>Unity 安装程序

### <a name="instructions"></a>说明

1. 启动 Unity。
2. 选择**打开**。
3. 导航到**HolographicAcademy 全息 212 语音**文件夹你之前未存档。
4. 找到并选择**起始**/**模型资源管理器**文件夹。
5. 单击**选择文件夹**按钮。
6. 在中**项目**面板中，展开**场景**文件夹。
7. 双击**ModelExplorer**场景中，从而在 Unity 中加载它。

### <a name="building"></a>生成

1. 在 Unity 中，选择**文件 > 生成设置**。
2. 如果**场景/ModelExplorer**中未列出**生成中的场景**，单击**添加打开场景**添加场景。
3. 如果您专门为 HoloLens 开发，设置**目标设备**到**HoloLens**。 否则，将其保持打开**任何设备**。
4. 请确保**生成类型**设置为**D3D**并**SDK**设置为**最新安装**（应为 16299 或更高版本的 SDK）。
5. 单击“生成” 。
6. 创建**新文件夹**名为"应用"。
7. 单击一下**应用**文件夹。
8. 按**选择文件夹**和 Unity 将启动 Visual Studio 的生成项目。

Unity 完成操作后，将出现一个文件资源管理器窗口。

1. 打开**应用**文件夹。
2. 打开**ModelExplorer Visual Studio 解决方案**。

如果部署到 HoloLens:

1. 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x86**。
2. 单击向下箭头旁边的本地计算机按钮，然后选择**远程计算机**。
3. 输入**HoloLens 设备 IP 地址**并将身份验证模式设置为**通用 （未加密的协议）**。 单击**选择**。 如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**。
4. 在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。 如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。
5. 当部署应用时，消除**Fitbox**与**选择手势**。

如果部署到沉浸式头戴式：

1. 在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x64**。
2. 请确保部署目标设置为**本地计算机**。
3. 在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。
4. 当部署应用时，消除**Fitbox**拉开运动控制器上的触发器。

>[!NOTE]
>您可能注意到 Visual Studio 错误面板中的某些红色错误。 它可以安全地忽略它们。 切换到输出面板来查看实际生成进度。 输出面板中的错误将要求您的修补程序 （即最常在脚本中的错误，就会出现）。

## <a name="chapter-1---awareness"></a>第 1 章-感知

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>目标

* 了解**注意事项**语音命令设计。
* 使用**KeywordRecognizer**将基于的视线移动语音命令添加。
* 使用户识别语音命令使用游标**反馈**。

### <a name="voice-command-design"></a>语音命令设计

在本章中，您将学习如何设计语音命令。 创建时的语音命令：

#### <a name="do"></a>DO

* 创建简洁的命令。 您不想要使用 *"播放当前所选的视频"*，因为该命令不是简洁并轻松地将用户被遗忘。 相反，应使用：*"播放视频"*，因为它很简洁，并具有多个音节。
* 使用简单的词汇。 始终尝试使用常用词和短语，都可轻松地发现，请记住用户。 例如，如果应用程序出现无法显示或隐藏视图中的说明对象，则不会使用该命令 *"显示布告"*，因为"标牌"是一个很少使用的术语。 相反，您可以使用命令：*"显示说明"*，以显示你的应用程序中的说明。
* 保持一致。 语音命令应保持一致整个应用程序。 假设应用程序中有两个场景，并且这两个场景包含一个用于关闭应用程序的按钮。 如果第一个场景使用命令 *"退出"* 触发按钮，但第二个场景使用该命令 *"关闭应用"*，则用户将感到很困惑。 如果相同的功能在多个场景之间仍然存在，则应使用相同的语音命令来触发它。

#### <a name="dont"></a>不要

* 使用单个音节命令。 例如，如果你已创建语音命令来播放视频，应避免使用简单命令 *"播放"*，因为它仅单音节，可以轻松地被系统遗漏。 相反，应使用：*"播放视频"*，因为它很简洁，并具有多个音节。
* 使用系统命令。 *"选择"* 命令保留的系统来触发当前具有焦点的对象的点击事件。 不要重新使用 *"选择"* 命令中的关键字或短语，，因为它可能不如预期。 例如，如果语音命令用于在你的应用程序中选择多维数据集已 *"选择多维数据集"*，但是，用户看看球体时它们失措命令，则会改为选择球体。 同样应用栏命令都已启用语音。 不在 CoreWindow 视图中使用以下的语音命令：
    1. 回去
    2. 滚动工具
    3. “缩放工具”
    4. 拖动工具
    5. Adjust
    6. Remove
* 使用类似的声音。 尽量避免使用韵文的语音命令。 如果你有一个购物应用程序，支持 *"显示存储区"* 并 *"显示更多"* 作为语音命令，则可以禁用某个命令的其他过程中使用。 例如，可以使用 *"显示存储"* 按钮以打开存储，然后又禁用了该命令时显示在存储区，以便 *"显示更多"* 命令无法用于浏览。

### <a name="instructions"></a>说明

* 在 Unity 中的**层次结构**面板中，使用的搜索工具查找**holoComm_screen_mesh**对象。
* 双击**holoComm_screen_mesh**对象中查看该**场景**。 这是顶级的监视，将会响应我们语音命令。
* 在中**Inspector**面板中，找到**语音输入源 （脚本）** 组件。
* 展开**关键字**部分，以查看受支持的语音命令：**打开 Communicator**。
* 单击到右侧的齿轮图标，然后选择**编辑脚本**。
* 探索**SpeechInputSource.cs**若要了解如何使用**KeywordRecognizer**添加语音命令。

### <a name="build-and-deploy"></a>生成和部署

* 在 Unity 中，使用**文件 > 生成设置**重新生成应用程序。
* 打开**应用**文件夹。
* 打开**ModelExplorer Visual Studio 解决方案**。

（如果你已生成/部署此项目在 Visual Studio 中的在设置过程，然后您可以打开与该实例并单击全部重新加载出现提示时）。

* 在 Visual Studio 中，单击**调试-> 启动不调试**或按**Ctrl + F5**。
* 在应用程序部署到 HoloLens 后，关闭配合的框使用[敲击](gestures.md#air-tap)手势。
* 注视顶级的监视。
* 当监视具有焦点时，验证光标更改为麦克风。 这提供了应用程序正在侦听的语音命令的反馈。
* 验证在手表上显示工具提示。 这有助于用户发现 *"打开 Communicator"* 命令。
* 监视在观望，同时说 *"打开 Communicator"* 打开 communicator 面板。

## <a name="chapter-2---acknowledgement"></a>第 2 章-确认

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>目标

* 记录使用麦克风输入的消息。
* 向应用程序正在侦听到他们的语音的用户提供反馈。

>[!NOTE]
>**麦克风**从麦克风录制的应用必须声明功能。 这是为您已在 MR 输入 212 但记住这一点对于您自己的项目。
>
>1. 在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置
>2. 单击"通用 Windows 平台"选项卡
>3. 在"发布设置 > 功能"部分中，检查**麦克风**功能

### <a name="instructions"></a>说明

* 在 Unity 中的**层次结构**面板中，确认**holoComm_screen_mesh**选择对象。
* 在中**Inspector**面板中，找到**顶级监视 （脚本）** 组件。
* 单击小的蓝色多维数据集上设置的值为**Communicator Prefab**属性。
* 在中**项目**面板中， **Communicator**预设现在应具有焦点。
* 单击**Communicator**预设中**项目**面板以查看在其组件**Inspector**。
* 看看**麦克风管理器 （脚本）** 组件，这将使我们能够记录用户的声音。
* 请注意， **Communicator**对象具有**语音输入处理程序 （脚本）** 组件响应**发送消息**命令。
* 看看**Communicator （脚本）** 组件，然后双击该脚本以在 Visual Studio 中打开它。

Communicator.cs 负责 communicator 设备上设置适当的按钮状态。 这样，我们用于记录一条消息，播放该录制，并将消息发送到顶级的用户。 它还将启动和停止的动画的批窗体，以向用户确认他们的语音已听说过。

* 在中**Communicator.cs**，删除以下行 （81 和 82） 从**启动**方法。 这将使 communicator 上的 Record 按钮。

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>生成和部署

* 在 Visual Studio 中，重新生成应用程序和部署到设备。
* 注视顶级的监视和说 *"打开 Communicator"* 显示 communicator。
* 按**记录**按钮 （麦克风） 若要开始录制的顶级口头消息。
* 开始说话，并验证批动画在 communicator，它提供给用户的反馈其言论被大家听到上播放。
* 按**停止**按钮 （左的正方形），并验证批动画停止运行。
* 按**播放**按钮以播放录制的消息，然后在设备上听到 （直角三角形）。
* 按**停止**按钮 （右正方形） 若要停止播放录制的消息。
* 说 *"发送消息"* 关闭 communicator 并接收来自顶级的消息已接收响应。

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>第 3 章-了解和听写识别器

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>目标

* 使用听写识别器来将用户的语音转换为文本。
* 在 communicator 中显示结果时听写识别器的零假设和最终结果。

在本章中，我们将使用听写识别器为顶级创建一条消息。 在使用时听写识别器，请记住：

* 您必须连接到 WiFi 时听写识别器工作。
* 在一段时间后，会出现超时。 有两个超时，需要注意的：
  * 如果识别器开始，并为第一个 5 秒将不会收听任何音频，就会超时。
  * 如果识别器提供结果，但然后会静默听到 20 秒，就会超时。
* 只有一种类型的识别器 （关键字或听写） 可以运行一次。

>[!NOTE]
>**麦克风**从麦克风录制的应用必须声明功能。 这是为您已在 MR 输入 212 但记住这一点对于您自己的项目。
>
>1. 在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置
>2. 单击"通用 Windows 平台"选项卡
>3. 在"发布设置 > 功能"部分中，检查**麦克风**功能

### <a name="instructions"></a>说明

我们将编辑**MicrophoneManager.cs**使用听写识别器。 这是我们将添加：

1. 当**记录按钮**是按下，我们将**启动 DictationRecognizer**。
2. 显示**假设**DictationRecognizer 理解。
3. 锁定**结果**DictationRecognizer 理解。
4. 检查从 DictationRecognizer 超时。
5. 当**停止按钮**按下时，或 mic 会话超时**停止 DictationRecognizer**。
6. 重新启动**KeywordRecognizer**，将侦听**发送消息**命令。

让我们开始吧。 完成 3.a 中的所有编码练习**MicrophoneManager.cs**，或复制并粘贴下面找到的已完成的代码：

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>生成和部署

* 在 Visual Studio 中重新生成并部署到你的设备。
* 关闭与-敲击手势的适合性的框。
* 注视顶级的监视和说 *"打开 Communicator"*。
* 选择**记录**按钮 （麦克风） 来记录您的消息。
* 开始说话。 **听写识别器**会解释语音，并在 communicator 中显示的零假设的文本。
* 尝试说 *"发送消息"* 时记录一条消息。 请注意，**关键字识别器**不会响应因为**听写识别器**仍处于活动状态。
* 结束说话几秒钟。 观看听写识别器完成其假设，并显示了最终结果。
* 开始说到，然后暂停 20 秒。 这将导致**听写识别器**超时。
* 请注意，**关键字识别器**上述超时后重新启用。 Communicator 现在将响应语音命令。
* 说 *"发送消息"* 若要将消息发送到顶级。

## <a name="chapter-4---grammar-recognizer"></a>第 4 章-语法识别器

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>目标

* 使用语法识别器识别根据 SRGS 或语音识别语法规范，文件的用户的语音。

>[!NOTE]
>**麦克风**从麦克风录制的应用必须声明功能。 这是为您已在 MR 输入 212 但记住这一点对于您自己的项目。
>
>1. 在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置
>2. 单击"通用 Windows 平台"选项卡
>3. 在"发布设置 > 功能"部分中，检查**麦克风**功能

### <a name="instructions"></a>说明

1. 在中**层次结构**面板中，搜索**Jetpack_Center**并将其选中。
2. 寻找**免除操作**中编写脚本**Inspector**面板。
3. 单击右侧的小圆圈**对象到标记沿**字段。
4. 在弹出窗口中，搜索**SRGSToolbox**并从列表中选择它。
5. 看一看**SRGSColor.xml**中的文件**StreamingAssets**文件夹。
* 可以在 W3C 网站上找到 SRGS 设计规范[此处](https://www.w3.org/TR/speech-grammar/)。
* 在我们 SRGS 文件中，我们有三种类型的规则：
  * 规则，它允许你说一种颜色从十二个颜色的列表。
  * 侦听的颜色规则和三个形状之一的组合这三个规则。
  * 根规则，colorChooser，侦听的三个"颜色 + 形状"规则的任意组合。 可以说形状，按任意顺序，并在任意数量只是一到所有这三个。 这是，所侦听的唯一规则，因为它指定为初始中的文件顶部的根规则&lt;语法&gt;标记。

### <a name="build-and-deploy"></a>生成和部署

* 重新生成应用程序在 Unity 中，然后生成并从 Visual Studio 体验 HoloLens 上的应用程序部署。
* 关闭与-敲击手势的适合性的框。
* 注视顶级 jetpack 和执行-敲击手势。
* 开始说话。 **语法识别器**将解释语音和更改基于识别的形状的颜色。 示例命令是"蓝色圆圈，黄色 square"。
* 执行另一个-敲击手势以关闭工具箱。

## <a name="the-end"></a>结束

祝贺你！ 你现在已经完成**MR 输入 212:语音**。

* 您知道的语音命令的注意事项。
* 你已了解如何已使用的工具提示，让用户知道的语音命令。
* 您看到了几种类型的用于确认用户的语音已听说过的反馈。
* 您知道如何切换关键字识别和听写识别器，并且这两个功能如何了解和解释您的声音。
* 您学习了如何在应用程序中的语音识别的使用 SRGS 文件和语法识别器。
