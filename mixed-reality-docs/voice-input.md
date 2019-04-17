---
title: 语音输入
description: 语音输入是 HoloLens 和 Windows Mixed Reality 沉浸式耳机的核心输入。 语音可以用于命令、 听写，Cortana，和的详细信息。
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv、 语音、 cortana、 语音、 输入
ms.openlocfilehash: 7fb5618c13ff1ed446241f744b598cfe2484ea45
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592996"
---
# <a name="voice-input"></a><span data-ttu-id="90ad1-105">语音输入</span><span class="sxs-lookup"><span data-stu-id="90ad1-105">Voice input</span></span>

<span data-ttu-id="90ad1-106">语音是输入上 HoloLens 的三种密钥形式之一。</span><span class="sxs-lookup"><span data-stu-id="90ad1-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="90ad1-107">它允许您直接命令而无需使用一张全息图[手势](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="90ad1-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="90ad1-108">您只需[注视](gaze.md)在一张全息图并把您的命令。</span><span class="sxs-lookup"><span data-stu-id="90ad1-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="90ad1-109">语音输入可以是你的意图进行通信的自然方式。</span><span class="sxs-lookup"><span data-stu-id="90ad1-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="90ad1-110">语音是尤其擅长于遍历复杂的接口，因为它允许用户通过用一个命令的嵌套菜单剪切。</span><span class="sxs-lookup"><span data-stu-id="90ad1-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="90ad1-111">语音输入作为后盾[相同的引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)，支持所有其他通用 Windows 应用中的语音。</span><span class="sxs-lookup"><span data-stu-id="90ad1-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="90ad1-112">设备支持</span><span class="sxs-lookup"><span data-stu-id="90ad1-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="90ad1-113">功能</span><span class="sxs-lookup"><span data-stu-id="90ad1-113">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="90ad1-114"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="90ad1-114"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="90ad1-115">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="90ad1-115">HoloLens 2</span></span></th><th style="width:150px"><span data-ttu-id="90ad1-116"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="90ad1-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="90ad1-117">语音输入</span><span class="sxs-lookup"><span data-stu-id="90ad1-117">Voice input</span></span></td><td style="text-align: center;"> <span data-ttu-id="90ad1-118">✔️</span><span class="sxs-lookup"><span data-stu-id="90ad1-118">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="90ad1-119">✔️</span><span class="sxs-lookup"><span data-stu-id="90ad1-119">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="90ad1-120">✔️ （使用麦克风）</span><span class="sxs-lookup"><span data-stu-id="90ad1-120">✔️ (with microphone)</span></span></td>
</tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="90ad1-121">"Select"命令</span><span class="sxs-lookup"><span data-stu-id="90ad1-121">The "select" command</span></span>

<span data-ttu-id="90ad1-122">即使没有专门将语音支持添加到您的应用程序，用户可以只需通过说"选择"激活全息。</span><span class="sxs-lookup"><span data-stu-id="90ad1-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="90ad1-123">此行为与相同[敲击](gestures.md#air-tap)上 HoloLens，按选择按钮上[HoloLens clicker](hardware-accessories.md#hololens-clicker)，或按触发器上[Windows Mixed Reality 运动控制器](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="90ad1-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="90ad1-124">您将听到声音，并查看显示确认为"select"包含的工具提示。</span><span class="sxs-lookup"><span data-stu-id="90ad1-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="90ad1-125">"选择"被启用的低能耗关键字检测算法中，因此始终是可供你说，在任何时间最小电池寿命造成的影响，甚至在您身边手。</span><span class="sxs-lookup"><span data-stu-id="90ad1-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="90ad1-126">特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="90ad1-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="90ad1-127">!["Select"可以使用语音命令来选择](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="90ad1-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="90ad1-128">*"Select"可以使用语音命令来选择*</span><span class="sxs-lookup"><span data-stu-id="90ad1-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="90ad1-129">Hey Cortana</span><span class="sxs-lookup"><span data-stu-id="90ad1-129">Hey Cortana</span></span>

<span data-ttu-id="90ad1-130">也可以说"你好，小娜"，以在任何时候显示 Cortana。</span><span class="sxs-lookup"><span data-stu-id="90ad1-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="90ad1-131">无需等待她才会显示继续要求她您的问题，或为她提供一条指令-例如，尝试说"你好，小娜天气是什么？"</span><span class="sxs-lookup"><span data-stu-id="90ad1-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="90ad1-132">作为单个句子。</span><span class="sxs-lookup"><span data-stu-id="90ad1-132">as a single sentence.</span></span> <span data-ttu-id="90ad1-133">有关 Cortana 以及可以执行哪些操作的详细信息，只需让她 ！</span><span class="sxs-lookup"><span data-stu-id="90ad1-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="90ad1-134">说"你好，小娜什么可以说？"</span><span class="sxs-lookup"><span data-stu-id="90ad1-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="90ad1-135">她将提起正在处理和建议的命令的列表。</span><span class="sxs-lookup"><span data-stu-id="90ad1-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="90ad1-136">如果您已在 Cortana 应用还可以单击 **？**</span><span class="sxs-lookup"><span data-stu-id="90ad1-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="90ad1-137">侧栏中请求此相同的菜单上的图标。</span><span class="sxs-lookup"><span data-stu-id="90ad1-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="90ad1-138">**特定于 HoloLens 的命令**</span><span class="sxs-lookup"><span data-stu-id="90ad1-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="90ad1-139">“我可以说什么？”</span><span class="sxs-lookup"><span data-stu-id="90ad1-139">"What can I say?"</span></span>
* <span data-ttu-id="90ad1-140">"转到主页"转到开始"-而不是[布隆](gestures.md#bloom)若要获取到[开始菜单](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="90ad1-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="90ad1-141">"启动<app>"</span><span class="sxs-lookup"><span data-stu-id="90ad1-141">"Launch <app>"</span></span>
* <span data-ttu-id="90ad1-142">"移动<app>此处"</span><span class="sxs-lookup"><span data-stu-id="90ad1-142">"Move <app> here"</span></span>
* <span data-ttu-id="90ad1-143">"拍摄一张照片"</span><span class="sxs-lookup"><span data-stu-id="90ad1-143">"Take a picture"</span></span>
* <span data-ttu-id="90ad1-144">"开始记录"</span><span class="sxs-lookup"><span data-stu-id="90ad1-144">"Start recording"</span></span>
* <span data-ttu-id="90ad1-145">"停止录制"</span><span class="sxs-lookup"><span data-stu-id="90ad1-145">"Stop recording"</span></span>
* <span data-ttu-id="90ad1-146">"Increase 亮度"</span><span class="sxs-lookup"><span data-stu-id="90ad1-146">"Increase the brightness"</span></span>
* <span data-ttu-id="90ad1-147">"Decrease 亮度"</span><span class="sxs-lookup"><span data-stu-id="90ad1-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="90ad1-148">"提高音量"</span><span class="sxs-lookup"><span data-stu-id="90ad1-148">"Increase the volume"</span></span>
* <span data-ttu-id="90ad1-149">"降低音量"</span><span class="sxs-lookup"><span data-stu-id="90ad1-149">"Decrease the volume"</span></span>
* <span data-ttu-id="90ad1-150">"静音"或者"取消静音"</span><span class="sxs-lookup"><span data-stu-id="90ad1-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="90ad1-151">"关闭该设备"</span><span class="sxs-lookup"><span data-stu-id="90ad1-151">"Shut down the device"</span></span>
* <span data-ttu-id="90ad1-152">"重新启动设备"</span><span class="sxs-lookup"><span data-stu-id="90ad1-152">"Restart the device"</span></span>
* <span data-ttu-id="90ad1-153">"转到睡眠状态"</span><span class="sxs-lookup"><span data-stu-id="90ad1-153">"Go to sleep"</span></span>
* <span data-ttu-id="90ad1-154">"什么时候是它？"</span><span class="sxs-lookup"><span data-stu-id="90ad1-154">"What time is it?"</span></span>
* <span data-ttu-id="90ad1-155">"多少，还剩电池 do？"</span><span class="sxs-lookup"><span data-stu-id="90ad1-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="90ad1-156">"调用<contact>"（需要 Skype 的 HoloLens）</span><span class="sxs-lookup"><span data-stu-id="90ad1-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="90ad1-157">"看，说"</span><span class="sxs-lookup"><span data-stu-id="90ad1-157">"See It, Say It"</span></span>

<span data-ttu-id="90ad1-158">HoloLens 具有"来看，说"语音输入模型上按钮的标签位置告知用户他们也可以说什么语音命令。</span><span class="sxs-lookup"><span data-stu-id="90ad1-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="90ad1-159">例如，在查看 2D 应用时，用户可以说出他们看到的应用栏中调整应用程序的世界中的位置的"调整"命令。</span><span class="sxs-lookup"><span data-stu-id="90ad1-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![在查看 2D 应用或全息图时，用户可以说他们看到的应用栏中调整应用程序的世界中的位置的"调整"命令](images/microphone-600px.png)

<span data-ttu-id="90ad1-161">当应用按照此规则时，用户可以轻松了解如何说来控制系统。</span><span class="sxs-lookup"><span data-stu-id="90ad1-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="90ad1-162">为了强调这，一个按钮在观望时，你将看到"语音停留"工具提示出现在一秒钟之后如果按钮是启用语音的将显示要说"按"它的命令。</span><span class="sxs-lookup"><span data-stu-id="90ad1-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="90ad1-163">![查看它，请说命令出现下面的按钮](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="90ad1-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="90ad1-164">*"到它，请说"按钮下方显示的命令*</span><span class="sxs-lookup"><span data-stu-id="90ad1-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="90ad1-165">快速全息图操作的语音命令</span><span class="sxs-lookup"><span data-stu-id="90ad1-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="90ad1-166">此外，还有大量的语音命令可以同时在一张全息图，若要快速执行操作任务观望说。</span><span class="sxs-lookup"><span data-stu-id="90ad1-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="90ad1-167">这些语音命令适用于 2D 应用程序，以及已放置在世界中的三维对象。</span><span class="sxs-lookup"><span data-stu-id="90ad1-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="90ad1-168">**全息图操作命令**</span><span class="sxs-lookup"><span data-stu-id="90ad1-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="90ad1-169">人脸我</span><span class="sxs-lookup"><span data-stu-id="90ad1-169">Face me</span></span>
* <span data-ttu-id="90ad1-170">更大 |增强</span><span class="sxs-lookup"><span data-stu-id="90ad1-170">Bigger | Enhance</span></span>
* <span data-ttu-id="90ad1-171">较小</span><span class="sxs-lookup"><span data-stu-id="90ad1-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="90ad1-172">听写</span><span class="sxs-lookup"><span data-stu-id="90ad1-172">Dictation</span></span>

<span data-ttu-id="90ad1-173">而不是类型化[空气分流点](gestures.md#air-tap)，语音听写可能会更有效，到应用中输入文本。</span><span class="sxs-lookup"><span data-stu-id="90ad1-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="90ad1-174">这可以极大地加快用户更轻松地输入。</span><span class="sxs-lookup"><span data-stu-id="90ad1-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="90ad1-175">![通过选择麦克风按钮来启动语音听写](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="90ad1-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="90ad1-176">*选择键盘上的麦克风按钮启动语音听写*</span><span class="sxs-lookup"><span data-stu-id="90ad1-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="90ad1-177">每当 holographic 键盘时处于活动状态，可以切换到无需键入听写模式。</span><span class="sxs-lookup"><span data-stu-id="90ad1-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="90ad1-178">选择的文本输入框，若要开始的一侧的麦克风。</span><span class="sxs-lookup"><span data-stu-id="90ad1-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="90ad1-179">通信</span><span class="sxs-lookup"><span data-stu-id="90ad1-179">Communication</span></span>

<span data-ttu-id="90ad1-180">对于想要利用的处理选项提供的 HoloLens 的自定义音频输入的应用程序，务必要了解各种[音频流类别](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)可以使用您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="90ad1-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="90ad1-181">Windows 10 支持多个不同的流类别和 HoloLens，可以使用的这三个启用自定义处理，以优化为语音、 通信和其他的可以用于环境的环境音频量身打造的麦克风音频质量捕获 （即"摄像机"） 的方案。</span><span class="sxs-lookup"><span data-stu-id="90ad1-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="90ad1-182">AudioCategory_Communications 流类别为调用质量和旁白方案自定义，可提供 16 kHz 24 位单声道音频流的用户的语音的客户端</span><span class="sxs-lookup"><span data-stu-id="90ad1-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="90ad1-183">AudioCategory_Speech 流类别为 HoloLens (Windows) 语音引擎自定义，并为其提供的用户的声音的 16 kHz 24 位 mono 流。</span><span class="sxs-lookup"><span data-stu-id="90ad1-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="90ad1-184">如果需要可以通过第三方语音引擎使用此类别。</span><span class="sxs-lookup"><span data-stu-id="90ad1-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="90ad1-185">AudioCategory_Other 流类别为环境的环境音频录制自定义，可提供客户端的 48 kHz 24 位立体声音频流。</span><span class="sxs-lookup"><span data-stu-id="90ad1-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="90ad1-186">所有这些音频处理过程是硬件加速这意味着功能释放比如果 HoloLens CPU 上执行相同的过程的少了很多电量。</span><span class="sxs-lookup"><span data-stu-id="90ad1-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="90ad1-187">避免运行上要延长系统电池寿命和充分利用内置的 CPU 的处理其他音频输入中，卸载音频输入的处理。</span><span class="sxs-lookup"><span data-stu-id="90ad1-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="90ad1-188">疑难解答</span><span class="sxs-lookup"><span data-stu-id="90ad1-188">Troubleshooting</span></span>

<span data-ttu-id="90ad1-189">如果您遇到任何问题使用"选择"和"你好，小娜"，请尝试将移动到更安静的空间，打开离开的干扰，或通过噪音谈到的源。</span><span class="sxs-lookup"><span data-stu-id="90ad1-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="90ad1-190">在此期间，在 HoloLens 上的所有语音识别是优化和优化是特定于的美式英语的母语。</span><span class="sxs-lookup"><span data-stu-id="90ad1-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="90ad1-191">对于 Windows 混合现实 Developer Edition 版本 2017年中，音频终结点管理逻辑将正常显示 （永久） 后到 PC 桌面出并再次在记录之后的初始 HMD 连接。</span><span class="sxs-lookup"><span data-stu-id="90ad1-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="90ad1-192">之前该的第一个登录的扩大/缩小事件 WMR OOBE 完成之后，用户可能会遇到各种范围不包括音频，具体取决于系统已设置在首次连接 HMD 之前切换到无音频的音频功能问题。</span><span class="sxs-lookup"><span data-stu-id="90ad1-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="90ad1-193">请参阅</span><span class="sxs-lookup"><span data-stu-id="90ad1-193">See also</span></span>
* [<span data-ttu-id="90ad1-194">在 DirectX 语音输入</span><span class="sxs-lookup"><span data-stu-id="90ad1-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="90ad1-195">在 Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="90ad1-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="90ad1-196">MR 输入 212:语音</span><span class="sxs-lookup"><span data-stu-id="90ad1-196">MR Input 212: Voice</span></span>](holograms-212.md)
