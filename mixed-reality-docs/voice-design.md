---
title: 语音命令
description: 提供注视、 手势和语音 (GGV) 是在 HoloLens 上交互的主要方式。 本文提供有关语音设计缜密的指南。
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality，设计、 交互、 语音
ms.openlocfilehash: 49fa199b2656db95b15583ccfbee39f33942f180
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730800"
---
# <a name="voice-commanding"></a><span data-ttu-id="42585-105">语音命令</span><span class="sxs-lookup"><span data-stu-id="42585-105">Voice commanding</span></span>

<span data-ttu-id="42585-106">使用语音命令时，注视通常用作目标 mechaninism，是否为指针 （"选择"） 或指示您的应用程序的命令 （"来看，说"）。</span><span class="sxs-lookup"><span data-stu-id="42585-106">When using voice commands, gaze is typically used as the targeting mechaninism, whether as a pointer ("select") or to direct your command to an application ("see it, say it").</span></span> <span data-ttu-id="42585-107">当然，一些语音命令不需要的目标，如"转到以启动"或"您好，Cortana。"</span><span class="sxs-lookup"><span data-stu-id="42585-107">Of course, some voice commands don't require a target at all, like "go to start" or "Hey, Cortana."</span></span>


## <a name="device-support"></a><span data-ttu-id="42585-108">设备支持</span><span class="sxs-lookup"><span data-stu-id="42585-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="42585-109">功能</span><span class="sxs-lookup"><span data-stu-id="42585-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="42585-110"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="42585-110"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="42585-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="42585-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="42585-112"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="42585-112"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td></td><td style="text-align: center;"> <span data-ttu-id="42585-113">✔️</span><span class="sxs-lookup"><span data-stu-id="42585-113">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="42585-114">✔️</span><span class="sxs-lookup"><span data-stu-id="42585-114">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="42585-115">✔️ （具有附加的耳机）</span><span class="sxs-lookup"><span data-stu-id="42585-115">✔️ (with headset attached)</span></span></td>
</tr>
</table>



## <a name="how-to-use-voice"></a><span data-ttu-id="42585-116">如何使用语音</span><span class="sxs-lookup"><span data-stu-id="42585-116">How to use voice</span></span>

<span data-ttu-id="42585-117">请考虑将语音命令添加到生成的任何经验。</span><span class="sxs-lookup"><span data-stu-id="42585-117">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="42585-118">语音是功能强大和方便的方法来控制系统和应用程序。</span><span class="sxs-lookup"><span data-stu-id="42585-118">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="42585-119">因为用户都讲了大量的本地语言和重音符号，适当选择的语音关键字将确保明确解释用户的命令。</span><span class="sxs-lookup"><span data-stu-id="42585-119">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="42585-120">最佳做法</span><span class="sxs-lookup"><span data-stu-id="42585-120">Best practices</span></span>

<span data-ttu-id="42585-121">下面是有助于平滑语音识别中一些实践。</span><span class="sxs-lookup"><span data-stu-id="42585-121">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="42585-122">**使用简洁的命令**-如果可能，请选择两个或多个音节关键字。</span><span class="sxs-lookup"><span data-stu-id="42585-122">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="42585-123">单音节单词倾向于使用不同的元音时所说的不同重音符号的人员。</span><span class="sxs-lookup"><span data-stu-id="42585-123">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="42585-124">例如："播放视频"是优于"播放当前所选的视频"</span><span class="sxs-lookup"><span data-stu-id="42585-124">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="42585-125">**使用简单的词汇**-示例："显示说明"优于"Show 标牌"</span><span class="sxs-lookup"><span data-stu-id="42585-125">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="42585-126">**请确保命令非破坏性**-请确保可以通过语音命令执行任何操作为非破坏性，并很容易就能撤消在另一个人讲附近用户意外触发某个命令的情况下。</span><span class="sxs-lookup"><span data-stu-id="42585-126">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="42585-127">**避免相似的发音命令**-避免注册听起来非常相似的多个语音命令。</span><span class="sxs-lookup"><span data-stu-id="42585-127">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="42585-128">例如："显示更多"和"显示存储区"可以是非常相似的发音。</span><span class="sxs-lookup"><span data-stu-id="42585-128">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="42585-129">**取消注册您的应用程序时不使用**-特定语音命令有效的状态不是您的应用程序时，请考虑取消注册它，以便其他命令不会混淆的一个。</span><span class="sxs-lookup"><span data-stu-id="42585-129">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="42585-130">**测试具有不同重音符号**-测试使用不同的重音符号的用户对应用程序。</span><span class="sxs-lookup"><span data-stu-id="42585-130">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="42585-131">**保持语音命令一致性**-如果"返回"转到前一页中，维护此应用程序中的行为。</span><span class="sxs-lookup"><span data-stu-id="42585-131">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="42585-132">**避免使用系统命令**-为系统保留以下语音命令。</span><span class="sxs-lookup"><span data-stu-id="42585-132">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="42585-133">这些不应由应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="42585-133">These should not be used by applications.</span></span>
   * <span data-ttu-id="42585-134">"您好 Cortana"</span><span class="sxs-lookup"><span data-stu-id="42585-134">"Hey Cortana"</span></span>
   * <span data-ttu-id="42585-135">"选择"</span><span class="sxs-lookup"><span data-stu-id="42585-135">"Select"</span></span>

### <a name="select"></a><span data-ttu-id="42585-136">"选择"</span><span class="sxs-lookup"><span data-stu-id="42585-136">"Select"</span></span>

<span data-ttu-id="42585-137">在任何时候说"选择"将激活的视线移动光标指向任何内容。</span><span class="sxs-lookup"><span data-stu-id="42585-137">Saying "select" at any time will activate whatever the gaze cursor is pointing at.</span></span> 

><span data-ttu-id="42585-138">注意：在 HoloLens 2 中，需要第一次调用通过说一词的视线移动光标"选择"。</span><span class="sxs-lookup"><span data-stu-id="42585-138">Note: In HoloLens 2, the gaze cursor needs to first be invoked by saying the word "select".</span></span> <span data-ttu-id="42585-139">例如，"选择"重新激活。</span><span class="sxs-lookup"><span data-stu-id="42585-139">Say, "select" again to activate.</span></span> <span data-ttu-id="42585-140">若要隐藏的视线移动游标，只需用手-airtap 或触摸对象。</span><span class="sxs-lookup"><span data-stu-id="42585-140">To hide the gaze cursor, simply use your hands -- airtap or touch an object.</span></span> 

### <a name="see-it-say-it"></a><span data-ttu-id="42585-141">来看，比如它</span><span class="sxs-lookup"><span data-stu-id="42585-141">See it, say it</span></span>

<span data-ttu-id="42585-142">Windows Mixed Reality 已经利用了"来看，说"语音模型其中**按钮上的标签是相同的关联的语音命令的**。</span><span class="sxs-lookup"><span data-stu-id="42585-142">Windows Mixed Reality has employed a "see it, say it" voice model where **labels on buttons are identical to the associated voice commands**.</span></span> <span data-ttu-id="42585-143">因为没有任何标签和语音命令之间的矛盾，用户可以更好地了解什么是控制系统。</span><span class="sxs-lookup"><span data-stu-id="42585-143">Because there isn’t any dissonance between the label and the voice command, users can better understand what to say to control the system.</span></span> <span data-ttu-id="42585-144">为了强调此操作，而上一个按钮，抛开 **"语音在此再次详述提示"** 显示哪个按钮是已启用语音通信。</span><span class="sxs-lookup"><span data-stu-id="42585-144">To reinforce this, while dwelling on a button, a **"voice dwell tip"** appears to communicate which buttons are voice enabled.</span></span>


![请参阅它说示例 1](images/voice-seeitsayit1-640px.jpg)

<span data-ttu-id="42585-146">![请参阅它说示例 2](images/voice-seeitsayit2-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="42585-146">![See it say it example 2](images/voice-seeitsayit2-640px.jpg)</span></span><br>
<span data-ttu-id="42585-147">*示例"来看，说它中"*</span><span class="sxs-lookup"><span data-stu-id="42585-147">*Examples of "see it, say it"*</span></span>

### <a name="voices-strengths"></a><span data-ttu-id="42585-148">语音的优势</span><span class="sxs-lookup"><span data-stu-id="42585-148">Voice's strengths</span></span>

<span data-ttu-id="42585-149">语音输入是通信我们意向的自然方式。</span><span class="sxs-lookup"><span data-stu-id="42585-149">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="42585-150">语音是尤其擅长于接口**遍历**因为这可帮助用户降低 （用户可能会说"返回"查找时在网页上，而不是无需完成并点击后退按钮在应用程序） 的接口的多个步骤。</span><span class="sxs-lookup"><span data-stu-id="42585-150">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at Web page, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="42585-151">此较短时间节省了一项强大**情感效果**上用户的体验的角度看，并为他们提供了少量实现超级。</span><span class="sxs-lookup"><span data-stu-id="42585-151">This small time savings has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="42585-152">使用语音时也是一种简便的输入的方法我们我们完整的手臂，或者已**多任务处理**。</span><span class="sxs-lookup"><span data-stu-id="42585-152">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="42585-153">在其中键入键盘上是很困难，设备上**语音听写**可以输入一个有效替代方法。</span><span class="sxs-lookup"><span data-stu-id="42585-153">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input.</span></span> <span data-ttu-id="42585-154">最后，在某些情况下何时**准确性范围**仅受信任的输入方法的限制的视线移动和手势，语音可能是用户的。</span><span class="sxs-lookup"><span data-stu-id="42585-154">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, Voice might be a user’s only trusted method input.</span></span>

<span data-ttu-id="42585-155">**如何使用语音受益用户**</span><span class="sxs-lookup"><span data-stu-id="42585-155">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="42585-156">减少了时间-这可以使最终目标更高效。</span><span class="sxs-lookup"><span data-stu-id="42585-156">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="42585-157">最大程度减少工作量-这可以使任务更流畅、 更轻松。</span><span class="sxs-lookup"><span data-stu-id="42585-157">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="42585-158">减少了认知负载-很直观且易于了解，并记住。</span><span class="sxs-lookup"><span data-stu-id="42585-158">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="42585-159">可接受社交-它应符合社会行为方面的标准。</span><span class="sxs-lookup"><span data-stu-id="42585-159">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="42585-160">它的例程的语音可能随时会变得的角度的行为。</span><span class="sxs-lookup"><span data-stu-id="42585-160">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="voices-weaknesses"></a><span data-ttu-id="42585-161">语音的劣势</span><span class="sxs-lookup"><span data-stu-id="42585-161">Voice's weaknesses</span></span>

<span data-ttu-id="42585-162">语音也有一些缺点。</span><span class="sxs-lookup"><span data-stu-id="42585-162">Voice also has some weaknesses.</span></span> <span data-ttu-id="42585-163">细粒度控制，是其中之一。</span><span class="sxs-lookup"><span data-stu-id="42585-163">Fine-grained control is one of them.</span></span> <span data-ttu-id="42585-164">（例如用户可能会说"噪音，"但不能使用多少。</span><span class="sxs-lookup"><span data-stu-id="42585-164">(for example a user might say "louder," but can’t say how much.</span></span> <span data-ttu-id="42585-165">"有点"很难定义。</span><span class="sxs-lookup"><span data-stu-id="42585-165">"A little" is hard to quantify.</span></span> <span data-ttu-id="42585-166">移动或缩放语音操作也是很难 （语音不提供高粒度的控制）。</span><span class="sxs-lookup"><span data-stu-id="42585-166">Moving or scaling things with voice is also difficult (voice does not offer the granularity of control).</span></span> <span data-ttu-id="42585-167">语音也可以不完美。</span><span class="sxs-lookup"><span data-stu-id="42585-167">Voice can also be imperfect.</span></span> <span data-ttu-id="42585-168">有时语音系统错误听到的是命令或无法听到命令。</span><span class="sxs-lookup"><span data-stu-id="42585-168">Sometimes a voice system incorrectly hears a command or fails to hear a command.</span></span> <span data-ttu-id="42585-169">从这类错误中恢复是任何接口中的一个挑战。</span><span class="sxs-lookup"><span data-stu-id="42585-169">Recovering from such errors is a challenge in any interface.</span></span> <span data-ttu-id="42585-170">最后，语音可能不是社交可接受在公共场合。</span><span class="sxs-lookup"><span data-stu-id="42585-170">Lastly, voice may not be socially acceptable in public places.</span></span> <span data-ttu-id="42585-171">有一些事项，用户不能或不应假设。</span><span class="sxs-lookup"><span data-stu-id="42585-171">There are some things that users can’t or shouldn’t say.</span></span> <span data-ttu-id="42585-172">这些 cliffs 允许用于它是最擅长的语音。</span><span class="sxs-lookup"><span data-stu-id="42585-172">These cliffs allow speech to be used for what it is best at.</span></span>

### <a name="voice-feedback-states"></a><span data-ttu-id="42585-173">语音反馈状态</span><span class="sxs-lookup"><span data-stu-id="42585-173">Voice feedback states</span></span>

<span data-ttu-id="42585-174">用户语音正确应用时，理解**什么它们可以说出并获得明确的反馈**系统**没它们听错**。</span><span class="sxs-lookup"><span data-stu-id="42585-174">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="42585-175">这些两个信号使用户确信在使用语音作为主要的输入。</span><span class="sxs-lookup"><span data-stu-id="42585-175">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="42585-176">下面是一个显示内容的图表发生游标识别语音输入时如何进行的通信向用户。</span><span class="sxs-lookup"><span data-stu-id="42585-176">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>

<span data-ttu-id="42585-177">![游标的语音反馈状态](images/voicefeedbackstates.png)</span><span class="sxs-lookup"><span data-stu-id="42585-177">![Voice feedback states for cursor](images/voicefeedbackstates.png)</span></span><br>
<span data-ttu-id="42585-178">*游标的语音反馈状态*</span><span class="sxs-lookup"><span data-stu-id="42585-178">*Voice feedback states for cursor*</span></span>

## <a name="top-things-users-should-know-about-speech-on-windows-mixed-reality"></a><span data-ttu-id="42585-179">首要工作用户应该了解 Windows Mixed reality"speech"</span><span class="sxs-lookup"><span data-stu-id="42585-179">Top things users should know about "speech" on Windows Mixed Reality</span></span>
* <span data-ttu-id="42585-180">说 **"选择"** 时目标 （您可以使用此任意位置单击一个按钮） 的按钮。</span><span class="sxs-lookup"><span data-stu-id="42585-180">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="42585-181">可以说**的应用程序栏按钮的标签名称**中某些应用程序执行操作。</span><span class="sxs-lookup"><span data-stu-id="42585-181">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="42585-182">例如，同时查看应用程序时，用户可以说出的命令"删除"从世界上删除该应用程序 （这可节省时间无需单击用一只手）。</span><span class="sxs-lookup"><span data-stu-id="42585-182">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="42585-183">你可以启动侦听语 Cortana **"你好，小娜"。**</span><span class="sxs-lookup"><span data-stu-id="42585-183">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="42585-184">可以询问她问题 （"你好，小娜，如何高是 Eiffel tower"），告诉她打开应用 （"你好，小娜，打开 Netflix"），或告诉她以打开开始菜单 （"你好，小娜，我家的 take"） 和的详细信息。</span><span class="sxs-lookup"><span data-stu-id="42585-184">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="42585-185">常见的问题和关注点用户对语音</span><span class="sxs-lookup"><span data-stu-id="42585-185">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="42585-186">我能说什么呢？</span><span class="sxs-lookup"><span data-stu-id="42585-186">What can I say?</span></span>
* <span data-ttu-id="42585-187">如何知道系统没听错正确？</span><span class="sxs-lookup"><span data-stu-id="42585-187">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="42585-188">系统正在我的语音命令错误。</span><span class="sxs-lookup"><span data-stu-id="42585-188">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="42585-189">当我把它语音命令，它不会做出反应。</span><span class="sxs-lookup"><span data-stu-id="42585-189">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="42585-190">当我为它指定语音命令时，它响应错误的处理方式。</span><span class="sxs-lookup"><span data-stu-id="42585-190">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="42585-191">如何针对我的语音到特定的应用程序或应用命令？</span><span class="sxs-lookup"><span data-stu-id="42585-191">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="42585-192">可以在 HoloLens 上使用语音命令之类 holographic 帧的内容？</span><span class="sxs-lookup"><span data-stu-id="42585-192">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="see-also"></a><span data-ttu-id="42585-193">请参阅</span><span class="sxs-lookup"><span data-stu-id="42585-193">See also</span></span>
* [<span data-ttu-id="42585-194">手势</span><span class="sxs-lookup"><span data-stu-id="42585-194">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="42585-195">设定凝视目标</span><span class="sxs-lookup"><span data-stu-id="42585-195">Gaze targeting</span></span>](gaze-targeting.md)
