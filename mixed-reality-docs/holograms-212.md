---
title: MR 输入 212-语音
description: 按照此编码演练操作, 使用 Unity、Visual Studio 和 HoloLens 来了解语音概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 学院, 教程, 语音
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522356"
---
>[!NOTE]
>混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。  因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。  这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。  将保留这些设备以继续使用支持的设备。 将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。  此通知将在发布时通过指向这些教程的链接进行更新。

<br>

# <a name="mr-input-212-voice"></a>MR 输入 212:语音

[语音输入](voice-input.md)提供了另一种与全息影像交互的方法。 语音命令的工作方式非常简单。 设计语音命令, 以便:

* 固有
* 易于记住
* 适当上下文
* 与同一上下文中的其他选项完全不同

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

在[先生/女士 101](holograms-101.md)中, 我们使用 KeywordRecognizer 来构建两个简单的语音命令。 在 MR 输入212中, 我们将深入探讨并了解如何:

* 设计针对 HoloLens 语音引擎进行了优化的语音命令。
* 使用户了解可用的语音命令。
* 确认我们听到了用户的语音命令。
* 使用听写识别器了解用户所说的内容。
* 使用语法识别器侦听基于 SRGS 或语音识别语法规范的命令。

在本课程中, 我们将重新访问模型资源管理器, 该资源管理器是在[MR input 210](holograms-210.md)和[mr input 211](holograms-211.md)中构建的。

>[!IMPORTANT]
>以下各章中嵌入的视频使用较旧版本的 Unity 和混合现实工具包记录。 虽然分步说明准确且最新, 但你可能会看到处于过期状态的相应视频中的脚本和视觉对象。 视频仍包含在 posterity 中, 因为涵盖的概念仍适用。


## <a name="device-support"></a>设备支持

<table>
<tr>
<th>摘要</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td>MR 输入 212:语音</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>开始之前

### <a name="prerequisites"></a>先决条件

* 配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。
* 一些基本C#的编程能力。
* 应已完成[尊敬的基本知识 101](holograms-101.md)。
* 应已完成[MR 输入 210](holograms-210.md)。
* 应已完成[MR 输入 211](holograms-211.md)。
* [为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。

### <a name="project-files"></a>项目文件

* 下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)。 需要 Unity 2017.2 或更高版本。
* 取消将文件存档到桌面或其他易于访问的位置。

>[!NOTE]
>如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)找到。

### <a name="errata-and-notes"></a>勘误表和说明

* 需要在 Visual Studio 的 "工具"-"> 选项-> 调试" 中禁用 (*取消选中*) "启用仅我的代码", 以便在代码中命中断点。

## <a name="unity-setup"></a>Unity 设置

### <a name="instructions"></a>说明

1. 启动 Unity。
2. 选择 "**打开**"。
3. 导航到之前未存档的**HolographicAcademy-212**文件夹。
4. 查找并选择 "**启动**/**模型资源管理器**" 文件夹。
5. 单击 "**选择文件夹**" 按钮。
6. 在 "**项目**" 面板中, 展开 "**场景**" 文件夹。
7. 双击 " **ModelExplorer**场景" 将其加载到 Unity。

### <a name="building"></a>生成

1. 在 Unity 中, 选择 "**文件 > 生成设置**"。
2. 如果场景 **/ModelExplorer**未列在 "**生成**" 中, 请单击 "**添加打开的场景**" 添加场景。
3. 如果要专门针对 HoloLens 进行开发, 请将 "**目标设备**" 设置为 " **hololens**"。 否则, 请将其留在**任何设备**上。
4. 确保将 "**生成类型**" 设置为 " **D3D** ", 并将 " **SDK** " 设置为 "**最新安装**的" (应为 SDK 16299 或更高版本)
5. 单击“生成” 。
6. 创建名为 "App" 的**新文件夹**。
7. 单击**应用**文件夹。
8. 按**选择文件夹**, Unity 将开始为 Visual Studio 生成项目。

当 Unity 完成后, 将显示文件资源管理器窗口。

1. 打开**应用程序**文件夹。
2. 打开**ModelExplorer Visual Studio 解决方案**。

如果部署到 HoloLens:

1. 使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x86**"。
2. 单击 "本地计算机" 按钮旁的下拉箭头, 然后选择 "**远程计算机**"。
3. 输入**HoloLens 设备 IP 地址**, 并将身份验证模式设置为**通用 (未加密的协议)** 。 单击 "**选择**"。 如果你不知道设备 IP 地址, 请在 "设置" 中查找 " **> 网络 & Internet > 高级选项**"。
4. 在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。 如果这是首次部署到设备, 则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。
5. 当应用程序已部署后, 使用**选择手势**关闭**Fitbox** 。

如果要部署到沉浸式耳机:

1. 使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x64**"。
2. 确保将部署目标设置为 "**本地计算机**"。
3. 在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。
4. 当应用程序已部署后, 通过将触发器拖到运动控制器上来关闭**Fitbox** 。

>[!NOTE]
>你可能会注意到 Visual Studio 错误面板中出现一些红色错误。 可以放心地忽略它们。 切换到 "输出" 面板以查看实际的生成进度。 "输出" 面板中的错误将要求您进行修复 (通常是由于脚本中的错误而导致的)。

## <a name="chapter-1---awareness"></a>第1章-感知

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>目标

* 了解语音命令设计的**Dos 和不注意事项**。
* 使用**KeywordRecognizer**添加基于注视的语音命令。
* 使用光标**反馈**使用户了解语音命令。

### <a name="voice-command-design"></a>语音命令设计

本章介绍如何设计语音命令。 创建语音命令时:

#### <a name="do"></a>DO

* 创建简洁的命令。 您不想使用 *"播放当前选定的视频"* , 因为该命令不是很简洁, 用户将很容易忘记。 相反, 应使用: *"播放视频"* , 因为它很简洁并且具有多个音节。
* 使用简单词汇。 始终尝试使用便于用户发现和记忆的常见字词和短语。 例如, 如果您的应用程序具有可在视图中显示或隐藏的便笺对象, 则不会使用命令 *"Show Placard"* , 因为 "Placard" 是很少使用的术语。 相反, 您将使用命令: *"显示注释"* , 用于在应用程序中显示注释。
* 保持一致。 语音命令应在应用程序中保持一致。 假设应用程序中有两个场景, 并且两个场景都包含一个用于关闭应用程序的按钮。 如果第一场景使用命令 *"Exit"* 来触发按钮, 但第二个场景使用命令 *"关闭应用"* , 则用户会感到困惑。 如果相同的功能在多个场景中保持不变, 则应使用相同的语音命令来触发它。

#### <a name="dont"></a>不要

* 使用单个音节命令。 例如, 如果你创建了一个声音命令来播放视频, 则应避免使用简单的命令 *"播放"* , 因为它只是一个音节, 系统可以轻松地将其丢失。 相反, 应使用: *"播放视频"* , 因为它很简洁并且具有多个音节。
* 使用系统命令。 系统保留了 *"Select"* 命令, 以触发当前聚焦对象的点击事件。 不要在关键字或短语中重复使用 *"Select"* 命令, 因为它可能不会像预期那样工作。 例如, 如果在应用程序中选择某个多维数据集的语音命令是 *"Select cube"* , 但用户在失措命令时却查看了该球, 则会改为选择球体。 类似的应用程序栏命令启用了语音。 请勿在 CoreWindow 视图中使用以下语音命令:
    1. 回去
    2. 滚动工具
    3. “缩放工具”
    4. 拖动工具
    5. Adjust
    6. Remove
* 使用类似的声音。 尝试避免使用偏偏的语音命令。 如果有支持 *"显示商店"* 和 *"显示更多"* 语音命令的购物应用程序, 则需要禁用其中一个命令, 而另一个命令已被使用。 例如, 你可以使用 *"显示商店"* 按钮打开应用商店, 然后在显示应用商店时禁用该命令, 以便可以使用 *"显示更多"* 命令来浏览。

### <a name="instructions"></a>说明

* 在 Unity 的**层次结构**面板中, 使用搜索工具查找**holoComm_screen_mesh**对象。
* 双击 " **holoComm_screen_mesh** " 对象以在**场景**中查看它。 这是 astronaut 的手表, 它将响应我们的语音命令。
* 在 "**检查器**" 面板中, 找到 "**语音输入源 (脚本)** " 组件。
* 展开**关键字**部分, 查看支持的语音命令:**打开 Communicator**。
* 单击右侧的 "齿轮", 然后选择 "**编辑脚本**"。
* 探索**SpeechInputSource.cs** , 了解它如何使用**KeywordRecognizer**添加语音命令。

### <a name="build-and-deploy"></a>生成和部署

* 在 Unity 中, 使用**File > 生成设置**重新生成应用程序。
* 打开**应用程序**文件夹。
* 打开**ModelExplorer Visual Studio 解决方案**。

(如果在安装过程中已经在 Visual Studio 中生成或部署了此项目, 则可以打开 VS 的实例, 并在出现提示时单击 "全部重新加载")。

* 在 Visual Studio 中, 单击 "**调试"-> "无调试开始**" 或按**Ctrl + F5**。
* 在应用程序部署到 HoloLens 后, 请使用[轻攻敲击](gestures.md#air-tap)手势关闭 "拟合" 框。
* 观看 astronaut 的观看。
* 当监视有焦点时, 验证光标是否更改为麦克风。 这会提供应用程序侦听语音命令的反馈。
* 验证是否在手表上显示工具提示。 这可以帮助用户发现 *"打开 Communicator"* 命令。
* 当 gazing 时, 说 *"打开 communicator"* 即可打开 communicator 面板。

## <a name="chapter-2---acknowledgement"></a>第2章-确认

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>目标

* 使用麦克风输入记录一条消息。
* 向用户提供对应用程序侦听其语音的反馈。

>[!NOTE]
>必须为应用声明**麦克风**功能, 才能从麦克风记录。 此操作已在 MR Input 212 中完成, 但请记住你自己的项目。
>
>1. 在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player", 转到 "播放机" 设置
>2. 单击 "通用 Windows 平台" 选项卡
>3. 在 "发布设置 > 功能" 部分中, 检查**麦克风**功能

### <a name="instructions"></a>说明

* 在 Unity 的 "**层次结构**" 面板中, 验证是否选择了 " **holoComm_screen_mesh** " 对象。
* 在**检查器**面板中, 找到 " **Astronaut Watch (脚本)** " 组件。
* 单击设置为 " **Communicator Prefab** " 属性值的小型蓝色多维数据集。
* 在 "**项目**" 面板中, **Communicator** prefab 现在应具有焦点。
* 单击 "**项目**" 面板中的**Communicator** Prefab, 在**检查器**中查看其组件。
* 查看**麦克风管理器 (脚本)** 组件, 这将允许我们记录用户的语音。
* 请注意, **Communicator**对象具有用于响应 "**发送消息**" 命令的**语音输入处理程序 (脚本)** 组件。
* 查看**Communicator (脚本)** 组件, 然后双击脚本, 在 Visual Studio 中将其打开。

Communicator.cs 负责在 communicator 设备上设置正确的按钮状态。 这将允许我们的用户记录消息, 播放消息, 并将消息发送到 astronaut。 它还将启动和停止动画波形窗体, 以便向用户确认他们的声音被听到。

* 在**Communicator.cs**中, 从**Start**方法中删除以下行 (81 和 82)。 这将启用 communicator 上的 "录制" 按钮。

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>生成和部署

* 在 Visual Studio 中, 重新生成应用程序并将其部署到设备。
* 看看 astronaut 的手表, 说 *"打开 communicator"* 显示 Communicator。
* 按 "**录制**" 按钮 (麦克风) 开始录制 astronaut 的口头消息。
* 开始讲话, 并验证波形动画是否在 communicator 上播放, 这向用户提供了他们的语音声音。
* 按 "**停止**" 按钮 (左方形), 并验证波形动画是否停止运行。
* 按下 "**播放**" 按钮 (右三角形) 播放录制的邮件, 并在设备上听到它。
* 按下 "**停止**" 按钮 (右方形) 以停止播放录制的消息。
* 说 *"发送消息"* 关闭 communicator, 并接收来自 astronaut 的 "消息收到" 响应。

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>第3章-了解和听写识别器

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>目标

* 使用听写识别器将用户的语音转换为文本。
* 显示 communicator 中听写识别器的假设和最终结果。

在本章中, 我们将使用听写识别器来创建 astronaut 的消息。 使用听写识别器时, 请记住:

* 你必须连接到 WiFi 才能让听写识别器正常工作。
* 超时发生在设定的时间段之后。 需要注意两个超时:
  * 如果识别器在前五秒内开始播放并且不听到任何音频, 则会超时。
  * 如果识别器给定了结果, 但随后听到了20秒, 则会超时。
* 一次只能运行一种类型的识别器 (关键字或听写)。

>[!NOTE]
>必须为应用声明**麦克风**功能, 才能从麦克风记录。 此操作已在 MR Input 212 中完成, 但请记住你自己的项目。
>
>1. 在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player", 转到 "播放机" 设置
>2. 单击 "通用 Windows 平台" 选项卡
>3. 在 "发布设置 > 功能" 部分中, 检查**麦克风**功能

### <a name="instructions"></a>说明

我们将编辑**MicrophoneManager.cs**以使用听写识别器。 这就是我们要添加的内容:

1. 按下 "**记录" 按钮**后, 将**启动 DictationRecognizer**。
2. 显示 DictationRecognizer 理解的**假设**。
3. 锁定 DictationRecognizer 理解的**结果**。
4. 检查 DictationRecognizer 中的超时。
5. 按下 "**停止" 按钮**, 或 mic 会话超时时,**停止 DictationRecognizer**。
6. 重新启动**KeywordRecognizer**, 这将侦听 "**发送消息**" 命令。

让我们开始吧。 在**MicrophoneManager.cs**中完成 3. a 的所有编码练习, 或复制并粘贴下面的已完成代码:

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

* 在 Visual Studio 中重新生成并部署到设备。
* 使用 "气攻入点" 消除 "拟合" 框。
* 看看 astronaut 的手表, 说 *"打开 Communicator"* 。
* 选择 "**录制**" 按钮 (麦克风) 以记录您的消息。
* 开始说话。 **听写识别器**将解释您的语音, 并显示 communicator 中的假设文本。
* 录制消息时, 尝试口述 *"发送消息"* 。 请注意, 由于**听写识别器**仍处于活动状态,**关键字识别器**没有响应。
* 停止说几秒钟。 注意听写识别器完成其假设并显示最终结果。
* 开始讲话, 并暂停20秒。 这将导致**听写识别器**超时。
* 请注意, 在上述超时后, 将重新启用**关键字识别器**。 Communicator 现在会响应语音命令。
* 说 *"发送消息"* , 将消息发送到 astronaut。

## <a name="chapter-4---grammar-recognizer"></a>第4章-语法识别器

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>目标

* 使用语法识别器根据 SRGS 或语音识别语法规范 (文件) 识别用户的语音。

>[!NOTE]
>必须为应用声明**麦克风**功能, 才能从麦克风记录。 此操作已在 MR Input 212 中完成, 但请记住你自己的项目。
>
>1. 在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player", 转到 "播放机" 设置
>2. 单击 "通用 Windows 平台" 选项卡
>3. 在 "发布设置 > 功能" 部分中, 检查**麦克风**功能

### <a name="instructions"></a>说明

1. 在 "**层次结构**" 面板中, 搜索**Jetpack_Center**并选择它。
2. 在 "**检查器**" 面板中查找**Tagalong 操作**脚本。
3. 单击要**沿字段标记的对象**右侧的小圆圈。
4. 在弹出的窗口中, 搜索**SRGSToolbox**并从列表中选择它。
5. 查看**StreamingAssets**文件夹中的**SRGSColor**文件。
* 可以在[此处](https://www.w3.org/TR/speech-grammar/)的 W3C 网站上找到 SRGS 设计规范。
* 在 SRGS 文件中, 有三种类型的规则:
  * 一种规则, 它允许您从十二种颜色列表中显示一种颜色。
  * 三个规则用于侦听颜色规则和三个形状中的一个组合。
  * 根规则 colorChooser, 用于侦听三个 "颜色 + 形状" 规则的任意组合。 可以按任何顺序以及从一个到所有三个形状的任意量来表示形状。 这是唯一侦听的规则, 因为它在初始&lt;语法&gt;标记中指定为文件顶部的根规则。

### <a name="build-and-deploy"></a>生成和部署

* 重新生成 Unity 中的应用程序, 然后从 Visual Studio 生成并部署, 以在 HoloLens 上体验应用。
* 使用 "气攻入点" 消除 "拟合" 框。
* 看看 astronaut 的 jetpack, 然后执行 "空气分流" 手势。
* 开始说话。 **语法识别器**将根据识别来解释您的语音并更改形状的颜色。 例如, 命令为 "蓝圆圈, 黄色正方形"。
* 执行另一个轻攻敲击手势来关闭工具箱。

## <a name="the-end"></a>结束

祝贺你！ 你现在已经完成**了 MR 输入 212:语音**。

* 您知道语音命令的 Dos 和不确定。
* 你了解了如何利用工具提示来使用户了解语音命令。
* 你看到了几种类型的反馈, 用来确认用户的语音被听到。
* 您知道如何在关键字识别器和听写识别器之间切换, 这两种功能如何理解和解释您的声音。
* 已了解如何在应用程序中使用 SRGS 文件和用于语音识别的语法识别器。
