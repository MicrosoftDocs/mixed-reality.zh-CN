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
# <a name="voice-input"></a><span data-ttu-id="21eeb-105">语音输入</span><span class="sxs-lookup"><span data-stu-id="21eeb-105">Voice input</span></span>

<span data-ttu-id="21eeb-106">Voice 是 HoloLens 上三种关键形式的输入之一。</span><span class="sxs-lookup"><span data-stu-id="21eeb-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="21eeb-107">它使你可以直接在无需使用[手势](gestures.md)的情况下直接执行命令。</span><span class="sxs-lookup"><span data-stu-id="21eeb-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="21eeb-108">只需[注视](gaze.md)一个全息图, 就可以说出命令。</span><span class="sxs-lookup"><span data-stu-id="21eeb-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="21eeb-109">语音输入可以自然地传达意向。</span><span class="sxs-lookup"><span data-stu-id="21eeb-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="21eeb-110">语音在遍历复杂接口时特别有用, 因为它允许用户使用一条命令剪切嵌套菜单。</span><span class="sxs-lookup"><span data-stu-id="21eeb-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="21eeb-111">语音输入由支持所有其他通用 Windows 应用中的语音的[同一引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)提供支持。</span><span class="sxs-lookup"><span data-stu-id="21eeb-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="21eeb-112">设备支持</span><span class="sxs-lookup"><span data-stu-id="21eeb-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="21eeb-113"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="21eeb-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="21eeb-114"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="21eeb-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="21eeb-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="21eeb-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="21eeb-116"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="21eeb-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="21eeb-117">语音输入</span><span class="sxs-lookup"><span data-stu-id="21eeb-117">Voice input</span></span></td>
        <td><span data-ttu-id="21eeb-118">✔️</span><span class="sxs-lookup"><span data-stu-id="21eeb-118">✔️</span></span></td>
        <td><span data-ttu-id="21eeb-119">✔️</span><span class="sxs-lookup"><span data-stu-id="21eeb-119">✔️</span></span></td>
        <td><span data-ttu-id="21eeb-120">✔️ (带有麦克风)</span><span class="sxs-lookup"><span data-stu-id="21eeb-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="21eeb-121">"Select" 命令</span><span class="sxs-lookup"><span data-stu-id="21eeb-121">The "select" command</span></span>

<span data-ttu-id="21eeb-122">即使不将语音支持专门添加到你的应用, 用户也可以通过说 "选择" 来激活全息影像。</span><span class="sxs-lookup"><span data-stu-id="21eeb-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="21eeb-123">此行为与在 HoloLens 上的[点击](gestures.md#air-tap), 按下[hololens clicker](hardware-accessories.md#hololens-clicker)上的 "选择" 按钮或在[Windows Mixed Reality 运动控制器](motion-controllers.md)上按下触发器的行为相同。</span><span class="sxs-lookup"><span data-stu-id="21eeb-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="21eeb-124">你将听到声音, 并看到带有 "select" 的工具提示显示为确认。</span><span class="sxs-lookup"><span data-stu-id="21eeb-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="21eeb-125">"Select" 是通过低功耗关键字检测算法来实现的, 因此, 在任何时候, 你始终都可以使用它, 而不管你在哪一边, 你都可以随时使用。</span><span class="sxs-lookup"><span data-stu-id="21eeb-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="21eeb-126">即将[推出](index.md#news-and-notes)特定于 HoloLens 2 的更多指导。</span><span class="sxs-lookup"><span data-stu-id="21eeb-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="21eeb-127">![说 "选择", 使用语音命令进行选择](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="21eeb-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="21eeb-128">*说 "选择", 使用语音命令进行选择*</span><span class="sxs-lookup"><span data-stu-id="21eeb-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="21eeb-129">Hey Cortana</span><span class="sxs-lookup"><span data-stu-id="21eeb-129">Hey Cortana</span></span>

<span data-ttu-id="21eeb-130">你还可以说 "你好 Cortana" 来随时显示 Cortana。</span><span class="sxs-lookup"><span data-stu-id="21eeb-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="21eeb-131">您无需等待她继续询问她的问题或给她发出说明, 例如, 尝试说 "你好 Cortana 的天气是什么？"。</span><span class="sxs-lookup"><span data-stu-id="21eeb-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="21eeb-132">作为单个句子。</span><span class="sxs-lookup"><span data-stu-id="21eeb-132">as a single sentence.</span></span> <span data-ttu-id="21eeb-133">有关 Cortana 和你可以执行的操作的详细信息, 只需咨询她!</span><span class="sxs-lookup"><span data-stu-id="21eeb-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="21eeb-134">说 "你好, 我可以说什么？"。</span><span class="sxs-lookup"><span data-stu-id="21eeb-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="21eeb-135">然后, 她将获取工作和建议命令的列表。</span><span class="sxs-lookup"><span data-stu-id="21eeb-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="21eeb-136">如果已进入 Cortana 应用, 还可以单击 " **？** "</span><span class="sxs-lookup"><span data-stu-id="21eeb-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="21eeb-137">图标, 提取此相同的菜单。</span><span class="sxs-lookup"><span data-stu-id="21eeb-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="21eeb-138">**HoloLens 特定的命令**</span><span class="sxs-lookup"><span data-stu-id="21eeb-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="21eeb-139">“我可以说什么？”</span><span class="sxs-lookup"><span data-stu-id="21eeb-139">"What can I say?"</span></span>
* <span data-ttu-id="21eeb-140">"转到主页" 或 "转到开始"-而不是[布隆](gestures.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="21eeb-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="21eeb-141">"启动<app>"</span><span class="sxs-lookup"><span data-stu-id="21eeb-141">"Launch <app>"</span></span>
* <span data-ttu-id="21eeb-142">"移动<app>到此处"</span><span class="sxs-lookup"><span data-stu-id="21eeb-142">"Move <app> here"</span></span>
* <span data-ttu-id="21eeb-143">"拍摄照片"</span><span class="sxs-lookup"><span data-stu-id="21eeb-143">"Take a picture"</span></span>
* <span data-ttu-id="21eeb-144">"开始录制"</span><span class="sxs-lookup"><span data-stu-id="21eeb-144">"Start recording"</span></span>
* <span data-ttu-id="21eeb-145">"停止录制"</span><span class="sxs-lookup"><span data-stu-id="21eeb-145">"Stop recording"</span></span>
* <span data-ttu-id="21eeb-146">"增加亮度"</span><span class="sxs-lookup"><span data-stu-id="21eeb-146">"Increase the brightness"</span></span>
* <span data-ttu-id="21eeb-147">"降低亮度"</span><span class="sxs-lookup"><span data-stu-id="21eeb-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="21eeb-148">"增加音量"</span><span class="sxs-lookup"><span data-stu-id="21eeb-148">"Increase the volume"</span></span>
* <span data-ttu-id="21eeb-149">"降低音量"</span><span class="sxs-lookup"><span data-stu-id="21eeb-149">"Decrease the volume"</span></span>
* <span data-ttu-id="21eeb-150">"静音" 或 "取消静音"</span><span class="sxs-lookup"><span data-stu-id="21eeb-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="21eeb-151">"关闭设备"</span><span class="sxs-lookup"><span data-stu-id="21eeb-151">"Shut down the device"</span></span>
* <span data-ttu-id="21eeb-152">"重新启动设备"</span><span class="sxs-lookup"><span data-stu-id="21eeb-152">"Restart the device"</span></span>
* <span data-ttu-id="21eeb-153">"进入睡眠状态"</span><span class="sxs-lookup"><span data-stu-id="21eeb-153">"Go to sleep"</span></span>
* <span data-ttu-id="21eeb-154">"它是什么时间？"</span><span class="sxs-lookup"><span data-stu-id="21eeb-154">"What time is it?"</span></span>
* <span data-ttu-id="21eeb-155">"我有多少电池剩余电量？"</span><span class="sxs-lookup"><span data-stu-id="21eeb-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="21eeb-156">"呼叫<contact>" (需要 Skype for HoloLens)</span><span class="sxs-lookup"><span data-stu-id="21eeb-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="21eeb-157">"看, 说它"</span><span class="sxs-lookup"><span data-stu-id="21eeb-157">"See It, Say It"</span></span>

<span data-ttu-id="21eeb-158">HoloLens 为语音输入提供了一个 "查看 it, 假设 it" 模型, 其中按钮上的标签告诉用户他们可以表达的语音命令。</span><span class="sxs-lookup"><span data-stu-id="21eeb-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="21eeb-159">例如, 查看2D 应用程序时, 用户可以说 "调整" 命令, 该命令显示在应用程序栏中, 用于调整应用在世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="21eeb-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![查看2D 应用或全息图时, 用户可以说 "调整" 命令, 该命令显示在应用栏中, 用于调整应用在世界中的位置。](images/microphone-600px.png)

<span data-ttu-id="21eeb-161">当应用遵循此规则时, 用户可以轻松地了解要控制系统的内容。</span><span class="sxs-lookup"><span data-stu-id="21eeb-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="21eeb-162">为此, 在按钮上 gazing 时, 你将看到一个 "声音停留" 工具提示, 如果按钮已启用语音, 则会出现一次, 并显示 "按下" 命令。</span><span class="sxs-lookup"><span data-stu-id="21eeb-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="21eeb-163">![查看它, 假设 "](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="21eeb-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="21eeb-164">*"看起来, 说它" 命令显示在按钮下面*</span><span class="sxs-lookup"><span data-stu-id="21eeb-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="21eeb-165">用于快速全息影像操作的语音命令</span><span class="sxs-lookup"><span data-stu-id="21eeb-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="21eeb-166">在 gazing 时, 还可以使用多个语音命令来快速执行操作任务。</span><span class="sxs-lookup"><span data-stu-id="21eeb-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="21eeb-167">这些语音命令适用于在世界上放置的2D 应用和3D 对象。</span><span class="sxs-lookup"><span data-stu-id="21eeb-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="21eeb-168">**全息图操作命令**</span><span class="sxs-lookup"><span data-stu-id="21eeb-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="21eeb-169">面部</span><span class="sxs-lookup"><span data-stu-id="21eeb-169">Face me</span></span>
* <span data-ttu-id="21eeb-170">更大 |完善</span><span class="sxs-lookup"><span data-stu-id="21eeb-170">Bigger | Enhance</span></span>
* <span data-ttu-id="21eeb-171">超过</span><span class="sxs-lookup"><span data-stu-id="21eeb-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="21eeb-172">听写</span><span class="sxs-lookup"><span data-stu-id="21eeb-172">Dictation</span></span>

<span data-ttu-id="21eeb-173">语音听写可以更高效地向应用程序中输入文本, 而不是使用[空中点击](gestures.md#air-tap)。</span><span class="sxs-lookup"><span data-stu-id="21eeb-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="21eeb-174">这可以极大地加快用户的输入。</span><span class="sxs-lookup"><span data-stu-id="21eeb-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="21eeb-175">![语音听写开始, 选择 "麦克风" 按钮](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="21eeb-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="21eeb-176">*语音听写开始于选择键盘上的麦克风按钮*</span><span class="sxs-lookup"><span data-stu-id="21eeb-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="21eeb-177">任何时候在全息键盘处于活动状态时, 都可以切换到听写模式, 而无需键入。</span><span class="sxs-lookup"><span data-stu-id="21eeb-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="21eeb-178">选择文本输入框一侧的麦克风即可开始。</span><span class="sxs-lookup"><span data-stu-id="21eeb-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="21eeb-179">通信</span><span class="sxs-lookup"><span data-stu-id="21eeb-179">Communication</span></span>

<span data-ttu-id="21eeb-180">对于想要利用 HoloLens 提供的自定义音频输入处理选项的应用程序, 请务必了解应用程序可使用的各种[音频流类别](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="21eeb-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="21eeb-181">Windows 10 支持多种不同的流类别, HoloLens 利用这三个类别来启用自定义处理, 以优化为语音、通信和其他可用于环境环境音频的麦克风音频质量捕获 (即 "摄像机") 方案。</span><span class="sxs-lookup"><span data-stu-id="21eeb-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="21eeb-182">AudioCategory_Communications 流类别自定义用于调用质量和旁白方案, 并为客户端提供用户语音的 16kHz 24bit mono 音频流</span><span class="sxs-lookup"><span data-stu-id="21eeb-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="21eeb-183">为 HoloLens (Windows) 语音引擎自定义 AudioCategory_Speech 流类别, 并为其提供用户语音的 16kHz 24bit mono 流。</span><span class="sxs-lookup"><span data-stu-id="21eeb-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="21eeb-184">第三方语音引擎可以根据需要使用此类别。</span><span class="sxs-lookup"><span data-stu-id="21eeb-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="21eeb-185">为环境环境录音录音自定义 AudioCategory_Other 流类别, 并为客户端提供 48kHz 24 位立体声音频流。</span><span class="sxs-lookup"><span data-stu-id="21eeb-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="21eeb-186">所有这种音频处理都是硬件加速, 这意味着功能消耗的电能要比在 HoloLens CPU 上执行相同处理要少得多。</span><span class="sxs-lookup"><span data-stu-id="21eeb-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="21eeb-187">避免在 CPU 上运行其他音频输入处理, 以最大程度地提高系统电池寿命, 并利用内置的卸载音频输入处理。</span><span class="sxs-lookup"><span data-stu-id="21eeb-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="21eeb-188">疑难解答</span><span class="sxs-lookup"><span data-stu-id="21eeb-188">Troubleshooting</span></span>

<span data-ttu-id="21eeb-189">如果使用 "选择" 和 "你好 Cortana" 时遇到任何问题, 请尝试移动到可取消选择的空间、远离噪音源或说出更大的声音。</span><span class="sxs-lookup"><span data-stu-id="21eeb-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="21eeb-190">目前, HoloLens 上的所有语音识别都专门针对美国英语的本机扬声器进行优化和优化。</span><span class="sxs-lookup"><span data-stu-id="21eeb-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="21eeb-191">对于 Windows Mixed Reality Developer Edition 版本 2017, 音频终结点管理逻辑将在初始 HMD 连接后注销并重新登录到 PC 桌面后正常运行。</span><span class="sxs-lookup"><span data-stu-id="21eeb-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="21eeb-192">在第一次注销/登录到 WMR 时, 用户可能会遇到各种音频功能问题, 范围从无音频切换到无音频切换, 具体取决于首次连接 HMD 前系统的设置方式。</span><span class="sxs-lookup"><span data-stu-id="21eeb-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="21eeb-193">请参阅</span><span class="sxs-lookup"><span data-stu-id="21eeb-193">See also</span></span>
* [<span data-ttu-id="21eeb-194">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="21eeb-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="21eeb-195">Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="21eeb-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="21eeb-196">MR 输入 212：语音</span><span class="sxs-lookup"><span data-stu-id="21eeb-196">MR Input 212: Voice</span></span>](holograms-212.md)
