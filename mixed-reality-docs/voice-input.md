---
title: 语音输入
description: 语音输入是适用于 HoloLens 和 Windows Mixed Reality 沉浸式耳机的核心输入。 语音可用于命令、听写、Cortana 等。
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv、语音、cortana、语音、输入
ms.openlocfilehash: 78ff63f2f794bb2b3a4868e38ccaff0582ccca8c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345697"
---
# <a name="voice-input"></a><span data-ttu-id="05555-105">语音输入</span><span class="sxs-lookup"><span data-stu-id="05555-105">Voice input</span></span>

![语音输入](images/UX/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="05555-107">在 HoloLens 上，语音是重要输入形式之一。</span><span class="sxs-lookup"><span data-stu-id="05555-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="05555-108">它使你可以直接在无需使用[手型手势](gaze-and-commit.md#composite-gestures)的情况下直接执行命令。</span><span class="sxs-lookup"><span data-stu-id="05555-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="05555-109">可以将语音输入作为一种传达意图的自然方式。</span><span class="sxs-lookup"><span data-stu-id="05555-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="05555-110">语音在遍历复杂接口时特别有用，因为它允许用户通过一个命令剪切嵌套菜单。</span><span class="sxs-lookup"><span data-stu-id="05555-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="05555-111">语音输入由支持所有其他_通用 Windows 应用_中的语音的[同一引擎](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx)提供支持。</span><span class="sxs-lookup"><span data-stu-id="05555-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="05555-112">在 HoloLens 上，语音识别将始终在 "设置" 中配置的 Windows 显示语言中工作。</span><span class="sxs-lookup"><span data-stu-id="05555-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="05555-113">语音和注视</span><span class="sxs-lookup"><span data-stu-id="05555-113">Voice and gaze</span></span>

<span data-ttu-id="05555-114">使用语音命令时（head 或眼睛）看起来通常用作目标机制，无论使用的是光标（"select"），还是将命令隐式通道到你要查看的应用程序。</span><span class="sxs-lookup"><span data-stu-id="05555-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="05555-115">为此，可能甚至不需要显示任何看起来像的光标 _（"请参阅它）_"。</span><span class="sxs-lookup"><span data-stu-id="05555-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="05555-116">当然，一些语音命令根本不需要目标，如 "开始" 或 "你好 Cortana"。</span><span class="sxs-lookup"><span data-stu-id="05555-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="05555-117">设备支持</span><span class="sxs-lookup"><span data-stu-id="05555-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05555-118"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="05555-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="05555-119"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="05555-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="05555-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="05555-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="05555-121"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="05555-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05555-122">语音输入</span><span class="sxs-lookup"><span data-stu-id="05555-122">Voice input</span></span></td>
        <td><span data-ttu-id="05555-123">✔️</span><span class="sxs-lookup"><span data-stu-id="05555-123">✔️</span></span></td>
        <td><span data-ttu-id="05555-124">✔️</span><span class="sxs-lookup"><span data-stu-id="05555-124">✔️</span></span></td>
        <td><span data-ttu-id="05555-125">✔️（带有麦克风）</span><span class="sxs-lookup"><span data-stu-id="05555-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="05555-126">"Select" 命令</span><span class="sxs-lookup"><span data-stu-id="05555-126">The "select" command</span></span>

<span data-ttu-id="05555-127">**HoloLens（第一代）**</span><span class="sxs-lookup"><span data-stu-id="05555-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="05555-128">即使不将语音支持专门添加到应用，用户也可以通过口述系统语音命令 "select" 来激活全息影像。</span><span class="sxs-lookup"><span data-stu-id="05555-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="05555-129">此行为与在 HoloLens 上的[点击](gaze-and-commit.md#composite-gestures)，按下[hololens clicker](https://docs.microsoft.com/hololens/hololens1-clicker)上的 "选择" 按钮或在[Windows Mixed Reality 运动控制器](motion-controllers.md)上按下触发器的行为相同。</span><span class="sxs-lookup"><span data-stu-id="05555-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](https://docs.microsoft.com/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="05555-130">你将听到声音，并看到带有 "select" 的工具提示显示为确认。</span><span class="sxs-lookup"><span data-stu-id="05555-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="05555-131">"Select" 是通过低功耗关键字检测算法来实现的，因此，在任何时候，你始终都可以使用它，而不管你在哪一边，你都可以随时使用。</span><span class="sxs-lookup"><span data-stu-id="05555-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="05555-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="05555-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="05555-133">若要在 HoloLens 2 中使用 "选择" 语音命令，首先需要打开 "注视" 光标作为指针。</span><span class="sxs-lookup"><span data-stu-id="05555-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="05555-134">让它变得更容易记住，只需说 "选择"。</span><span class="sxs-lookup"><span data-stu-id="05555-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="05555-135">若要退出此模式，只需通过空中点击，使用手指接近按钮，或使用系统手势再次使用。</span><span class="sxs-lookup"><span data-stu-id="05555-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="05555-136">*图像：说 "选择" 以使用声音命令进行选择*</span><span class="sxs-lookup"><span data-stu-id="05555-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![用户可以将 "选择" 用于所选的语音命令。](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="05555-138">你好小娜</span><span class="sxs-lookup"><span data-stu-id="05555-138">Hey Cortana</span></span>

<span data-ttu-id="05555-139">你还可以说 "你好 Cortana" 来随时显示 Cortana。</span><span class="sxs-lookup"><span data-stu-id="05555-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="05555-140">您无需等待她继续询问她的问题或给她发出说明，例如，尝试说 "你好 Cortana，天气是什么？"。</span><span class="sxs-lookup"><span data-stu-id="05555-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="05555-141">作为单个句子。</span><span class="sxs-lookup"><span data-stu-id="05555-141">as a single sentence.</span></span> <span data-ttu-id="05555-142">有关 Cortana 和你可以执行的操作的详细信息，只需咨询她！</span><span class="sxs-lookup"><span data-stu-id="05555-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="05555-143">说 "你好 Cortana，我该怎么办？"</span><span class="sxs-lookup"><span data-stu-id="05555-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="05555-144">然后，她将获取工作和建议命令的列表。</span><span class="sxs-lookup"><span data-stu-id="05555-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="05555-145">如果已进入 Cortana 应用，还可以单击 " **？** "</span><span class="sxs-lookup"><span data-stu-id="05555-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="05555-146">图标，提取此相同的菜单。</span><span class="sxs-lookup"><span data-stu-id="05555-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="05555-147">**HoloLens 特定的命令**</span><span class="sxs-lookup"><span data-stu-id="05555-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="05555-148">“我可以说什么？”</span><span class="sxs-lookup"><span data-stu-id="05555-148">"What can I say?"</span></span>
* <span data-ttu-id="05555-149">"转到开始"-而不是[布隆](system-gesture.md#bloom)转到 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="05555-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="05555-150">"启动 <app> "</span><span class="sxs-lookup"><span data-stu-id="05555-150">"Launch <app>"</span></span>
* <span data-ttu-id="05555-151">"移动到 <app> 此处"</span><span class="sxs-lookup"><span data-stu-id="05555-151">"Move <app> here"</span></span>
* <span data-ttu-id="05555-152">"拍摄照片"</span><span class="sxs-lookup"><span data-stu-id="05555-152">"Take a picture"</span></span>
* <span data-ttu-id="05555-153">"开始录制"</span><span class="sxs-lookup"><span data-stu-id="05555-153">"Start recording"</span></span>
* <span data-ttu-id="05555-154">"停止录制"</span><span class="sxs-lookup"><span data-stu-id="05555-154">"Stop recording"</span></span>
* <span data-ttu-id="05555-155">"增加亮度"</span><span class="sxs-lookup"><span data-stu-id="05555-155">"Increase the brightness"</span></span>
* <span data-ttu-id="05555-156">"降低亮度"</span><span class="sxs-lookup"><span data-stu-id="05555-156">"Decrease the brightness"</span></span>
* <span data-ttu-id="05555-157">"增加音量"</span><span class="sxs-lookup"><span data-stu-id="05555-157">"Increase the volume"</span></span>
* <span data-ttu-id="05555-158">"降低音量"</span><span class="sxs-lookup"><span data-stu-id="05555-158">"Decrease the volume"</span></span>
* <span data-ttu-id="05555-159">"静音" 或 "取消静音"</span><span class="sxs-lookup"><span data-stu-id="05555-159">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="05555-160">"关闭设备"</span><span class="sxs-lookup"><span data-stu-id="05555-160">"Shut down the device"</span></span>
* <span data-ttu-id="05555-161">"重新启动设备"</span><span class="sxs-lookup"><span data-stu-id="05555-161">"Restart the device"</span></span>
* <span data-ttu-id="05555-162">"进入睡眠状态"</span><span class="sxs-lookup"><span data-stu-id="05555-162">"Go to sleep"</span></span>
* <span data-ttu-id="05555-163">"它是什么时间？"</span><span class="sxs-lookup"><span data-stu-id="05555-163">"What time is it?"</span></span>
* <span data-ttu-id="05555-164">"我有多少电池剩余电量？"</span><span class="sxs-lookup"><span data-stu-id="05555-164">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="05555-165">"看，说它"</span><span class="sxs-lookup"><span data-stu-id="05555-165">"See It, Say It"</span></span><br>
        <span data-ttu-id="05555-166">HoloLens 为语音输入提供了一个 "查看 it，假设 it" 模型，其中按钮上的标签告诉用户他们可以表达的语音命令。</span><span class="sxs-lookup"><span data-stu-id="05555-166">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="05555-167">例如，在 HoloLens （第一代）中查看应用窗口时，用户可以说 "调整" 命令，该命令显示在应用栏中，用于调整应用在世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="05555-167">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="05555-168">*图像：用户可以说 "调整" 命令，该命令显示在应用程序栏中以调整应用的位置*</span><span class="sxs-lookup"><span data-stu-id="05555-168">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="05555-169">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="05555-169">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="05555-170">![查看应用程序窗口或全息图时，用户可以说 "调整" 命令，该命令显示在应用程序栏中，用于调整应用在世界中的位置。](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="05555-170">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="05555-171">当应用遵循此规则时，用户可以轻松地了解要控制系统的内容。</span><span class="sxs-lookup"><span data-stu-id="05555-171">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="05555-172">为加强这一点，当 gazing （第一代）中的按钮时，你将看到一个 "声音停留" 工具提示，如果按钮已启用语音，则会出现一秒钟，并显示 "按下" 命令。</span><span class="sxs-lookup"><span data-stu-id="05555-172">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="05555-173">若要在 HoloLens 2 中显示语音工具提示，请通过说 "选择" 或 "我可以说什么" （请参阅图像）来显示语音光标。</span><span class="sxs-lookup"><span data-stu-id="05555-173">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="05555-174">*图像： "查看它，假设" 命令显示在按钮下方*</span><span class="sxs-lookup"><span data-stu-id="05555-174">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![查看它，假设 "](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="05555-176">用于快速全息影像操作的语音命令</span><span class="sxs-lookup"><span data-stu-id="05555-176">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="05555-177">在 gazing 时，可以使用许多语音命令来快速执行操作任务。</span><span class="sxs-lookup"><span data-stu-id="05555-177">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="05555-178">这些语音命令适用于你在世界上放置的应用程序窗口和3D 对象。</span><span class="sxs-lookup"><span data-stu-id="05555-178">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="05555-179">**全息图操作命令**</span><span class="sxs-lookup"><span data-stu-id="05555-179">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="05555-180">面部</span><span class="sxs-lookup"><span data-stu-id="05555-180">Face me</span></span>
* <span data-ttu-id="05555-181">更大 |完善</span><span class="sxs-lookup"><span data-stu-id="05555-181">Bigger | Enhance</span></span>
* <span data-ttu-id="05555-182">超过</span><span class="sxs-lookup"><span data-stu-id="05555-182">Smaller</span></span>

<span data-ttu-id="05555-183">在 HoloLens 2 上，你还可以结合眼睛创建更自然的交互，从而隐式地提供有关所引用内容的上下文信息。</span><span class="sxs-lookup"><span data-stu-id="05555-183">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="05555-184">例如，您可以简单地查看全息图，说 "放置_此_内容"，然后浏览到要放置它的位置，然后说 "移到_此处_"。</span><span class="sxs-lookup"><span data-stu-id="05555-184">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="05555-185">您也可以在复杂的计算机上查看全息部分，并说： "向我介绍有关_此_的详细信息"。</span><span class="sxs-lookup"><span data-stu-id="05555-185">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="05555-186">发现语音命令</span><span class="sxs-lookup"><span data-stu-id="05555-186">Discovering voice commands</span></span>

<span data-ttu-id="05555-187">某些命令（如上面用于快速操作的命令）可以隐藏。</span><span class="sxs-lookup"><span data-stu-id="05555-187">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="05555-188">若要了解可以使用的命令，请看一看对象并说 "我可以说什么？"。</span><span class="sxs-lookup"><span data-stu-id="05555-188">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="05555-189">将弹出的可能命令的列表。</span><span class="sxs-lookup"><span data-stu-id="05555-189">A list of possible commands pops up.</span></span> <span data-ttu-id="05555-190">你还可以使用打印头的光标来浏览并显示你前面每个按钮的语音工具提示。</span><span class="sxs-lookup"><span data-stu-id="05555-190">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="05555-191">如果需要完整的列表，请随时说 "显示所有命令"。</span><span class="sxs-lookup"><span data-stu-id="05555-191">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="05555-192">听写</span><span class="sxs-lookup"><span data-stu-id="05555-192">Dictation</span></span>

<span data-ttu-id="05555-193">语音听写可以更高效地向应用程序中输入文本，而不是使用[空中点击](gaze-and-commit.md#composite-gestures)。</span><span class="sxs-lookup"><span data-stu-id="05555-193">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="05555-194">这可以极大地加快用户的输入。</span><span class="sxs-lookup"><span data-stu-id="05555-194">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="05555-195">![语音听写开始，选择 "麦克风" 按钮](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="05555-195">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="05555-196">*语音听写开始于选择键盘上的麦克风按钮*</span><span class="sxs-lookup"><span data-stu-id="05555-196">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="05555-197">任何时候在全息键盘处于活动状态时，都可以切换到听写模式，而无需键入。</span><span class="sxs-lookup"><span data-stu-id="05555-197">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="05555-198">选择文本输入框一侧的麦克风即可开始。</span><span class="sxs-lookup"><span data-stu-id="05555-198">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="05555-199">向应用程序添加语音命令</span><span class="sxs-lookup"><span data-stu-id="05555-199">Adding voice commands to your app</span></span>

<span data-ttu-id="05555-200">考虑为生成的任何体验添加语音命令。</span><span class="sxs-lookup"><span data-stu-id="05555-200">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="05555-201">语音是一种功能强大、方便的控制系统和应用的方式。</span><span class="sxs-lookup"><span data-stu-id="05555-201">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="05555-202">由于用户使用各种方言和口音说话，恰当选择语音关键字将确保用户的命令得到清晰的解释。</span><span class="sxs-lookup"><span data-stu-id="05555-202">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="05555-203">最佳实践</span><span class="sxs-lookup"><span data-stu-id="05555-203">Best practices</span></span>

<span data-ttu-id="05555-204">以下是一些有助于流畅语音识别的做法。</span><span class="sxs-lookup"><span data-stu-id="05555-204">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="05555-205">**使用简明命令** - 如果可能的话，选择两个或更多音节的关键词。</span><span class="sxs-lookup"><span data-stu-id="05555-205">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="05555-206">不同口音的人说单音节词时倾向于使用不同的元音。</span><span class="sxs-lookup"><span data-stu-id="05555-206">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="05555-207">示例： "播放视频" 优于 "播放当前选定的视频"</span><span class="sxs-lookup"><span data-stu-id="05555-207">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="05555-208">**使用简单词汇**-示例： "show note" 优于 "show placard"</span><span class="sxs-lookup"><span data-stu-id="05555-208">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="05555-209">**确保命令是非破坏性的** - 确保语音命令可以执行的任何操作都是非破坏性的，并且可以很容易地撤消，以防在用户附近说话的另一个人意外触发命令。</span><span class="sxs-lookup"><span data-stu-id="05555-209">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="05555-210">**避免使用类似的语音命令** - 避免注册多个听起来非常相似的语音命令。</span><span class="sxs-lookup"><span data-stu-id="05555-210">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="05555-211">示例： "显示更多" 和 "显示存储" 的发音可能非常相似。</span><span class="sxs-lookup"><span data-stu-id="05555-211">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="05555-212">**不使用应用时请取消注册应用** - 当应用没有处于特定语音命令有效的状态时，请考虑取消注册应用，使其他命令不会与该命令混淆。</span><span class="sxs-lookup"><span data-stu-id="05555-212">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="05555-213">**使用不同的口音进行测试** - 由具有不同口音的用户测试应用。</span><span class="sxs-lookup"><span data-stu-id="05555-213">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="05555-214">**保持语音命令一致性** - 如果“返回”可转到上一页，请在应用程序中保持此行为。</span><span class="sxs-lookup"><span data-stu-id="05555-214">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="05555-215">**避免使用系统命令** - 系统保留了以下语音命令。</span><span class="sxs-lookup"><span data-stu-id="05555-215">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="05555-216">应用程序不应使用这些命令。</span><span class="sxs-lookup"><span data-stu-id="05555-216">These should not be used by applications.</span></span>
   * <span data-ttu-id="05555-217">“你好小娜”</span><span class="sxs-lookup"><span data-stu-id="05555-217">"Hey Cortana"</span></span>
   * <span data-ttu-id="05555-218">“选择”</span><span class="sxs-lookup"><span data-stu-id="05555-218">"Select"</span></span>
   * <span data-ttu-id="05555-219">"中转到开始"</span><span class="sxs-lookup"><span data-stu-id="05555-219">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="05555-220">语音输入的优点</span><span class="sxs-lookup"><span data-stu-id="05555-220">Advantages of voice input</span></span>

<span data-ttu-id="05555-221">语音输入是传达我们意图的自然方式。</span><span class="sxs-lookup"><span data-stu-id="05555-221">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="05555-222">语音在接口**遍历**上特别不错，因为它可以帮助用户遍历界面的多个步骤（用户在查看网页时可能会说 "返回"，而不是在应用中使用 "后退" 按钮）。</span><span class="sxs-lookup"><span data-stu-id="05555-222">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="05555-223">这一小段节省时间对用户的体验感到**非常强大，** 并为他们提供少量实现超级。</span><span class="sxs-lookup"><span data-stu-id="05555-223">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="05555-224">当我们忙得不可开交或同时处理多项任务时，使用语音也是一种方便的输入方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="05555-224">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="05555-225">对于在键盘上键入很困难的设备，**语音听写**可能是输入文本的一种有效的替代方法。</span><span class="sxs-lookup"><span data-stu-id="05555-225">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="05555-226">最后，在某些情况下，看看注视和手势的**准确性范围**会受到限制，语音有助于消除用户的意图。</span><span class="sxs-lookup"><span data-stu-id="05555-226">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="05555-227">**语音的使用如何让用户受益**</span><span class="sxs-lookup"><span data-stu-id="05555-227">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="05555-228">省时 - 它应该使最终目标更高效。</span><span class="sxs-lookup"><span data-stu-id="05555-228">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="05555-229">最大限度地减少工作量 - 它应该使任务更加流畅和轻松。</span><span class="sxs-lookup"><span data-stu-id="05555-229">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="05555-230">减少认知压力 - 它是直观的，易于学习和记忆。</span><span class="sxs-lookup"><span data-stu-id="05555-230">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="05555-231">它在社会上是可以接受的 - 它应该在行为方面符合社会规范。</span><span class="sxs-lookup"><span data-stu-id="05555-231">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="05555-232">它是常规的 - 语音很容易成为一种习惯行为。</span><span class="sxs-lookup"><span data-stu-id="05555-232">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="05555-233">语音输入的挑战</span><span class="sxs-lookup"><span data-stu-id="05555-233">Challenges for voice input</span></span>

<span data-ttu-id="05555-234">虽然语音输入非常适合于许多不同的应用程序，但它也面临着几个难题。</span><span class="sxs-lookup"><span data-stu-id="05555-234">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="05555-235">了解语音输入的优点和挑战使应用程序开发人员能够更灵活地选择使用语音输入的方式和时间，并为用户提供良好的体验。</span><span class="sxs-lookup"><span data-stu-id="05555-235">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="05555-236">**连续输入控件的语音输入**细粒度控件是其中之一。</span><span class="sxs-lookup"><span data-stu-id="05555-236">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="05555-237">例如，用户可能想要更改其音乐应用中的音量。</span><span class="sxs-lookup"><span data-stu-id="05555-237">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="05555-238">她只是说 "更大"，但并不清楚系统的容量。</span><span class="sxs-lookup"><span data-stu-id="05555-238">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="05555-239">用户可能会说： "让它变得稍大一些"，但很难量化。</span><span class="sxs-lookup"><span data-stu-id="05555-239">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="05555-240">移动或缩放全息影像的方式同样困难。</span><span class="sxs-lookup"><span data-stu-id="05555-240">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="05555-241">**语音输入检测的可靠性**虽然语音输入系统变得更好且更好，但有时它们可能会错误地听到和解释语音命令。</span><span class="sxs-lookup"><span data-stu-id="05555-241">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="05555-242">关键是通过在系统正在侦听时向用户提供反馈，并为系统理解哪些内容来明确理解用户的潜在问题，以解决应用程序中的这一难题。</span><span class="sxs-lookup"><span data-stu-id="05555-242">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="05555-243">**共享空间中的语音输入**在与他人共享的空格中，语音可能无法社交。</span><span class="sxs-lookup"><span data-stu-id="05555-243">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="05555-244">以下是一些示例：</span><span class="sxs-lookup"><span data-stu-id="05555-244">Here are a few examples:</span></span>
* <span data-ttu-id="05555-245">用户可能不想干扰其他人（例如，在安静库或共享办公室中）</span><span class="sxs-lookup"><span data-stu-id="05555-245">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="05555-246">用户可能会很难被视为公开的，</span><span class="sxs-lookup"><span data-stu-id="05555-246">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="05555-247">用户可能会在其他人正在侦听时感觉不舒服</span><span class="sxs-lookup"><span data-stu-id="05555-247">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="05555-248">**语音输入唯一或未知字词**当用户听写可能对系统未知的字词时（如昵称、某些俚语词或缩写），也会出现语音输入问题。</span><span class="sxs-lookup"><span data-stu-id="05555-248">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="05555-249">**学习语音命令**尽管最终目标是自然地与系统进行对话，但有时应用程序仍然依赖于特定的预定义语音命令。</span><span class="sxs-lookup"><span data-stu-id="05555-249">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="05555-250">与大的语音命令集相关的挑战在于如何教授用户，而无需对用户进行重载，以及如何帮助用户保留它们。</span><span class="sxs-lookup"><span data-stu-id="05555-250">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="05555-251">语音反馈状态</span><span class="sxs-lookup"><span data-stu-id="05555-251">Voice feedback states</span></span>

<span data-ttu-id="05555-252">当语音应用正确时，用户了解他们能说什么，并得到清晰的反馈 - 系统正确地听到了用户说的话\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="05555-252">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="05555-253">这两个信号使用户在使用语音作为主要输入方法时充满自信。</span><span class="sxs-lookup"><span data-stu-id="05555-253">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="05555-254">下面的图表显示了识别语音输入时光标发生的情况以及它是如何将信息传达给用户的。</span><span class="sxs-lookup"><span data-stu-id="05555-254">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="05555-255">![1. 常规游标状态](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="05555-255">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="05555-256">**1. 常规游标状态**</span><span class="sxs-lookup"><span data-stu-id="05555-256">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="05555-257">![2. 传达语音反馈，然后消失](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="05555-257">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="05555-258">**2. 传达语音反馈，然后消失**</span><span class="sxs-lookup"><span data-stu-id="05555-258">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="05555-259">![三维空间.</span><span class="sxs-lookup"><span data-stu-id="05555-259">![\*3.</span></span> <span data-ttu-id="05555-260">常规游标状态](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="05555-260">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="05555-261">**3. 返回到常规游标状态**</span><span class="sxs-lookup"><span data-stu-id="05555-261">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="05555-262">在混合现实中，用户应该知道的关于“语音”的重要事项</span><span class="sxs-lookup"><span data-stu-id="05555-262">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="05555-263">在将一个按钮设置为目标时，说“选择”（可以在任何位置使用这种方法来单击按钮）\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="05555-263">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="05555-264">可以在某些应用中通过说出应用栏按钮的标签名称来执行操作\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="05555-264">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="05555-265">例如，在查看应用时，用户可以说“移除”命令以从现实中移除应用（这样可以节省用手单击按钮的时间）。</span><span class="sxs-lookup"><span data-stu-id="05555-265">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="05555-266">说“你好小娜”可以启动 Cortana 侦听\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="05555-266">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="05555-267">你可以向她提问（“你好小娜，埃菲尔铁塔有多高”），告诉她打开应用（“你好小娜，打开 Netflix”），或告诉她调出“开始”菜单（“你好小娜，带我回家”）等等。</span><span class="sxs-lookup"><span data-stu-id="05555-267">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="05555-268">用户对语音的常见问题和关注点</span><span class="sxs-lookup"><span data-stu-id="05555-268">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="05555-269">我可以说什么？</span><span class="sxs-lookup"><span data-stu-id="05555-269">What can I say?</span></span>
* <span data-ttu-id="05555-270">我如何知道系统正确听到了我说的话？</span><span class="sxs-lookup"><span data-stu-id="05555-270">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="05555-271">系统总是理解错误我的语音命令。</span><span class="sxs-lookup"><span data-stu-id="05555-271">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="05555-272">当我发出语音命令时，系统不会做出反应。</span><span class="sxs-lookup"><span data-stu-id="05555-272">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="05555-273">当我发出语音命令时，系统的反应是错误的。</span><span class="sxs-lookup"><span data-stu-id="05555-273">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="05555-274">我如何将我的语音定向到一个特定的应用或应用命令？</span><span class="sxs-lookup"><span data-stu-id="05555-274">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="05555-275">我可以使用语音来对 HoloLens 上的全息帧执行命令吗？</span><span class="sxs-lookup"><span data-stu-id="05555-275">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="05555-276">通信</span><span class="sxs-lookup"><span data-stu-id="05555-276">Communication</span></span>

<span data-ttu-id="05555-277">对于想要利用 HoloLens 提供的自定义音频输入处理选项的应用程序，请务必了解应用程序可使用的各种[音频流类别](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="05555-277">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="05555-278">Windows 10 支持多个不同的流类别，HoloLens 使用这三个类别来启用自定义处理，以优化为语音、通信和其他可用于环境环境音频捕获（即 "摄像机"）方案而定制的麦克风音频质量。</span><span class="sxs-lookup"><span data-stu-id="05555-278">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="05555-279">为呼叫质量和旁白方案自定义 AudioCategory_Communications 流类别，并为客户端提供用户语音的 16kHz 24bit mono 音频流</span><span class="sxs-lookup"><span data-stu-id="05555-279">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="05555-280">为 HoloLens （Windows）语音引擎自定义 AudioCategory_Speech 流类别，并为其提供用户语音的 16kHz 24bit mono 流。</span><span class="sxs-lookup"><span data-stu-id="05555-280">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="05555-281">第三方语音引擎可以根据需要使用此类别。</span><span class="sxs-lookup"><span data-stu-id="05555-281">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="05555-282">为环境环境录音录音自定义 AudioCategory_Other 流类别，并为客户端提供 48kHz 24 位立体声音频流。</span><span class="sxs-lookup"><span data-stu-id="05555-282">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="05555-283">所有这种音频处理都是硬件加速，这意味着功能消耗的电能要比在 HoloLens CPU 上执行相同处理要少得多。</span><span class="sxs-lookup"><span data-stu-id="05555-283">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="05555-284">避免在 CPU 上运行其他音频输入处理，以最大程度地提高系统电池寿命，并利用内置的卸载音频输入处理。</span><span class="sxs-lookup"><span data-stu-id="05555-284">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="05555-285">语言</span><span class="sxs-lookup"><span data-stu-id="05555-285">Languages</span></span>

<span data-ttu-id="05555-286">HoloLens 2[支持多种语言](https://docs.microsoft.com/hololens/hololens2-language-support)。</span><span class="sxs-lookup"><span data-stu-id="05555-286">HoloLens 2 [supports multiple languages](https://docs.microsoft.com/hololens/hololens2-language-support).</span></span> <span data-ttu-id="05555-287">请记住，即使安装了多个键盘或应用尝试使用其他语言创建语音识别器，语音命令也始终会在系统的显示语言中运行。</span><span class="sxs-lookup"><span data-stu-id="05555-287">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="05555-288">故障排除</span><span class="sxs-lookup"><span data-stu-id="05555-288">Troubleshooting</span></span>

<span data-ttu-id="05555-289">如果使用 "选择" 和 "你好 Cortana" 时遇到任何问题，请尝试移动到可取消选择的空间、远离噪音源或说出更大的声音。</span><span class="sxs-lookup"><span data-stu-id="05555-289">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="05555-290">目前，HoloLens 上的所有语音识别都专门针对美国英语的本机扬声器进行优化和优化。</span><span class="sxs-lookup"><span data-stu-id="05555-290">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="05555-291">对于 Windows Mixed Reality Developer Edition 版本2017，音频终结点管理逻辑将在初始 HMD 连接后注销并重新登录到 PC 桌面后正常运行。</span><span class="sxs-lookup"><span data-stu-id="05555-291">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="05555-292">在第一次注销/登录到 WMR 时，用户可能会遇到各种音频功能问题，范围从无音频切换到无音频切换，具体取决于首次连接 HMD 前系统的设置方式。</span><span class="sxs-lookup"><span data-stu-id="05555-292">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="05555-293">适用于 Unity 的 MRTK （混合现实工具包）中的语音输入</span><span class="sxs-lookup"><span data-stu-id="05555-293">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="05555-294">借助**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**，你可以轻松地为任何对象分配语音命令。</span><span class="sxs-lookup"><span data-stu-id="05555-294">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="05555-295">使用 MRTK 的**语音输入配置文件**定义关键字。</span><span class="sxs-lookup"><span data-stu-id="05555-295">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="05555-296">通过分配**SpeechInputHandler**脚本，你可以使任何对象响应语音输入配置文件中定义的关键字。</span><span class="sxs-lookup"><span data-stu-id="05555-296">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="05555-297">SpeechInputHandler 还提供了语音确认标签以提高用户信心。</span><span class="sxs-lookup"><span data-stu-id="05555-297">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="05555-298">MRTK-语音命令</span><span class="sxs-lookup"><span data-stu-id="05555-298">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="05555-299">另请参阅</span><span class="sxs-lookup"><span data-stu-id="05555-299">See also</span></span>
* [<span data-ttu-id="05555-300">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="05555-300">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="05555-301">本能交互</span><span class="sxs-lookup"><span data-stu-id="05555-301">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="05555-302">MR 输入 212：语音</span><span class="sxs-lookup"><span data-stu-id="05555-302">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="05555-303">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="05555-303">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="05555-304">Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="05555-304">Voice input in Unity</span></span>](voice-input-in-unity.md)
