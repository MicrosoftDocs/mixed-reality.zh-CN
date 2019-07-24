---
title: 语音命令
description: 凝视、手势和语音 (GGV) 是 HoloLens 交互的主要方式。 本文提供有关语音设计的详细指南。
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality、设计、交互、语音
ms.openlocfilehash: 724ef87dae1c731289af51504a518193c20b7d96
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387652"
---
# <a name="voice-commanding"></a><span data-ttu-id="05d9f-105">语音命令</span><span class="sxs-lookup"><span data-stu-id="05d9f-105">Voice commanding</span></span>

<span data-ttu-id="05d9f-106">使用语音命令时，凝视通常用作定位机制，无论是充当指针（“选择”）还是将命令定向到应用程序（“看到它，说出来”），都是如此。</span><span class="sxs-lookup"><span data-stu-id="05d9f-106">When using voice commands, gaze is typically used as the targeting mechaninism, whether as a pointer ("select") or to direct your command to an application ("see it, say it").</span></span> <span data-ttu-id="05d9f-107">当然，有些语音命令根本不需要目标，例如“去开始菜单”或“你好小娜”。</span><span class="sxs-lookup"><span data-stu-id="05d9f-107">Of course, some voice commands don't require a target at all, like "go to start" or "Hey, Cortana."</span></span>


## <a name="device-support"></a><span data-ttu-id="05d9f-108">设备支持</span><span class="sxs-lookup"><span data-stu-id="05d9f-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05d9f-109"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="05d9f-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="05d9f-110"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="05d9f-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="05d9f-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="05d9f-111"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="05d9f-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="05d9f-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05d9f-113">语音命令</span><span class="sxs-lookup"><span data-stu-id="05d9f-113">Voice commanding</span></span></td>
        <td><span data-ttu-id="05d9f-114">✔️</span><span class="sxs-lookup"><span data-stu-id="05d9f-114">✔️</span></span></td>
        <td><span data-ttu-id="05d9f-115">✔️</span><span class="sxs-lookup"><span data-stu-id="05d9f-115">✔️</span></span></td>
        <td><span data-ttu-id="05d9f-116">✔️（配有头戴显示设备）</span><span class="sxs-lookup"><span data-stu-id="05d9f-116">✔️ (with headset attached)</span></span></td>
    </tr>
</table>



## <a name="how-to-use-voice"></a><span data-ttu-id="05d9f-117">如何使用语音</span><span class="sxs-lookup"><span data-stu-id="05d9f-117">How to use voice</span></span>

<span data-ttu-id="05d9f-118">考虑为生成的任何体验添加语音命令。</span><span class="sxs-lookup"><span data-stu-id="05d9f-118">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="05d9f-119">语音是一种功能强大、方便的控制系统和应用的方式。</span><span class="sxs-lookup"><span data-stu-id="05d9f-119">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="05d9f-120">由于用户使用各种方言和口音说话，恰当选择语音关键字将确保用户的命令得到清晰的解释。</span><span class="sxs-lookup"><span data-stu-id="05d9f-120">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="05d9f-121">最佳实践</span><span class="sxs-lookup"><span data-stu-id="05d9f-121">Best practices</span></span>

<span data-ttu-id="05d9f-122">以下是一些有助于流畅语音识别的做法。</span><span class="sxs-lookup"><span data-stu-id="05d9f-122">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="05d9f-123">**使用简明命令** - 如果可能的话，选择两个或更多音节的关键词。</span><span class="sxs-lookup"><span data-stu-id="05d9f-123">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="05d9f-124">不同口音的人说单音节词时倾向于使用不同的元音。</span><span class="sxs-lookup"><span data-stu-id="05d9f-124">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="05d9f-125">例如：“播放视频”优于“播放当前所选视频”</span><span class="sxs-lookup"><span data-stu-id="05d9f-125">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="05d9f-126">**使用简单词汇** - 示例：“显示通知”优于“显示标语牌”</span><span class="sxs-lookup"><span data-stu-id="05d9f-126">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="05d9f-127">**确保命令是非破坏性的** - 确保语音命令可以执行的任何操作都是非破坏性的，并且可以很容易地撤消，以防在用户附近说话的另一个人意外触发命令。</span><span class="sxs-lookup"><span data-stu-id="05d9f-127">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="05d9f-128">**避免使用类似的语音命令** - 避免注册多个听起来非常相似的语音命令。</span><span class="sxs-lookup"><span data-stu-id="05d9f-128">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="05d9f-129">例如：“显示更多”和“显示商店”就非常相似。</span><span class="sxs-lookup"><span data-stu-id="05d9f-129">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="05d9f-130">**不使用应用时请取消注册应用** - 当应用没有处于特定语音命令有效的状态时，请考虑取消注册应用，使其他命令不会与该命令混淆。</span><span class="sxs-lookup"><span data-stu-id="05d9f-130">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="05d9f-131">**使用不同的口音进行测试** - 由具有不同口音的用户测试应用。</span><span class="sxs-lookup"><span data-stu-id="05d9f-131">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="05d9f-132">**保持语音命令一致性** - 如果“返回”可转到上一页，请在应用程序中保持此行为。</span><span class="sxs-lookup"><span data-stu-id="05d9f-132">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="05d9f-133">**避免使用系统命令** - 系统保留了以下语音命令。</span><span class="sxs-lookup"><span data-stu-id="05d9f-133">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="05d9f-134">应用程序不应使用这些命令。</span><span class="sxs-lookup"><span data-stu-id="05d9f-134">These should not be used by applications.</span></span>
   * <span data-ttu-id="05d9f-135">“你好小娜”</span><span class="sxs-lookup"><span data-stu-id="05d9f-135">"Hey Cortana"</span></span>
   * <span data-ttu-id="05d9f-136">“选择”</span><span class="sxs-lookup"><span data-stu-id="05d9f-136">"Select"</span></span>

### <a name="select"></a><span data-ttu-id="05d9f-137">“选择”</span><span class="sxs-lookup"><span data-stu-id="05d9f-137">"Select"</span></span>

<span data-ttu-id="05d9f-138">在任何时候说"选择"将激活凝视光标指向的任何内容。</span><span class="sxs-lookup"><span data-stu-id="05d9f-138">Saying "select" at any time will activate whatever the gaze cursor is pointing at.</span></span> 

><span data-ttu-id="05d9f-139">注意:在 HoloLens 2 中，首先需要通过说出“选择”调用凝视光标。</span><span class="sxs-lookup"><span data-stu-id="05d9f-139">Note: In HoloLens 2, the gaze cursor needs to first be invoked by saying the word "select".</span></span> <span data-ttu-id="05d9f-140">再说一次“选择”以激活。</span><span class="sxs-lookup"><span data-stu-id="05d9f-140">Say, "select" again to activate.</span></span> <span data-ttu-id="05d9f-141">要隐藏凝视光标，只需用手隔空敲击或触摸对象。</span><span class="sxs-lookup"><span data-stu-id="05d9f-141">To hide the gaze cursor, simply use your hands -- airtap or touch an object.</span></span> 

### <a name="see-it-say-it"></a><span data-ttu-id="05d9f-142">看到它，说出来</span><span class="sxs-lookup"><span data-stu-id="05d9f-142">See it, say it</span></span>

<span data-ttu-id="05d9f-143">Windows Mixed Reality 采用了“看到它，说出来”的语音模型，在该模型中，按钮上的标签与相关的语音命令相同。</span><span class="sxs-lookup"><span data-stu-id="05d9f-143">Windows Mixed Reality has employed a "see it, say it" voice model where **labels on buttons are identical to the associated voice commands**.</span></span> <span data-ttu-id="05d9f-144">由于标签和语音命令之间没有任何不一致，用户可以更好地理解应该说什么来控制系统。</span><span class="sxs-lookup"><span data-stu-id="05d9f-144">Because there isn’t any dissonance between the label and the voice command, users can better understand what to say to control the system.</span></span> <span data-ttu-id="05d9f-145">为了加强这一点，在某个按钮上停留时，会显示“语音停留提示”，提示哪些按钮已启用语音功能。</span><span class="sxs-lookup"><span data-stu-id="05d9f-145">To reinforce this, while dwelling on a button, a **"voice dwell tip"** appears to communicate which buttons are voice enabled.</span></span>


![“看到它，说出来”示例 1](images/voice-seeitsayit1-640px.jpg)

<span data-ttu-id="05d9f-147">![“看到它，说出来”示例 2](images/voice-seeitsayit2-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="05d9f-147">![See it say it example 2](images/voice-seeitsayit2-640px.jpg)</span></span><br>
<span data-ttu-id="05d9f-148">*“看到它，说出来”示例*</span><span class="sxs-lookup"><span data-stu-id="05d9f-148">*Examples of "see it, say it"*</span></span>

### <a name="voices-strengths"></a><span data-ttu-id="05d9f-149">语音的优势</span><span class="sxs-lookup"><span data-stu-id="05d9f-149">Voice's strengths</span></span>

<span data-ttu-id="05d9f-150">语音输入是传达我们意图的自然方式。</span><span class="sxs-lookup"><span data-stu-id="05d9f-150">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="05d9f-151">语音特别适合界面遍历，因为它可以帮助用户切入界面的多个步骤（用户可能会在查看网页时说“返回”，而无需在应用中点击“后退”按钮。</span><span class="sxs-lookup"><span data-stu-id="05d9f-151">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at Web page, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="05d9f-152">少量的时间节省对用户的体验感知具有强大的情感效应，并赋予了他们一点超能力。</span><span class="sxs-lookup"><span data-stu-id="05d9f-152">This small time savings has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="05d9f-153">当我们忙得不可开交或同时处理多项任务时，使用语音也是一种方便的输入方法。</span><span class="sxs-lookup"><span data-stu-id="05d9f-153">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="05d9f-154">在难以在键盘上打字的设备上，语音听写可能是一种高效的替代输入方式。</span><span class="sxs-lookup"><span data-stu-id="05d9f-154">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input.</span></span> <span data-ttu-id="05d9f-155">最后，在某些情况下，当凝视和手势的精度范围有限时，语音可能是用户唯一可信的输入方法。</span><span class="sxs-lookup"><span data-stu-id="05d9f-155">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, Voice might be a user’s only trusted method input.</span></span>

<span data-ttu-id="05d9f-156">**语音的使用如何让用户受益**</span><span class="sxs-lookup"><span data-stu-id="05d9f-156">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="05d9f-157">省时 - 它应该使最终目标更高效。</span><span class="sxs-lookup"><span data-stu-id="05d9f-157">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="05d9f-158">最大限度地减少工作量 - 它应该使任务更加流畅和轻松。</span><span class="sxs-lookup"><span data-stu-id="05d9f-158">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="05d9f-159">减少认知压力 - 它是直观的，易于学习和记忆。</span><span class="sxs-lookup"><span data-stu-id="05d9f-159">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="05d9f-160">它在社会上是可以接受的 - 它应该在行为方面符合社会规范。</span><span class="sxs-lookup"><span data-stu-id="05d9f-160">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="05d9f-161">它是常规的 - 语音很容易成为一种习惯行为。</span><span class="sxs-lookup"><span data-stu-id="05d9f-161">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="voices-weaknesses"></a><span data-ttu-id="05d9f-162">语音的劣势</span><span class="sxs-lookup"><span data-stu-id="05d9f-162">Voice's weaknesses</span></span>

<span data-ttu-id="05d9f-163">语音也有一些劣势。</span><span class="sxs-lookup"><span data-stu-id="05d9f-163">Voice also has some weaknesses.</span></span> <span data-ttu-id="05d9f-164">精细控制就是其中之一。</span><span class="sxs-lookup"><span data-stu-id="05d9f-164">Fine-grained control is one of them.</span></span> <span data-ttu-id="05d9f-165">（例如，用户可能会说“大声点”，但不能说出程度。</span><span class="sxs-lookup"><span data-stu-id="05d9f-165">(for example a user might say "louder," but can’t say how much.</span></span> <span data-ttu-id="05d9f-166">“有点”很难量化。</span><span class="sxs-lookup"><span data-stu-id="05d9f-166">"A little" is hard to quantify.</span></span> <span data-ttu-id="05d9f-167">使用语音移动或缩放内容也很困难（语音不提供控制精细度）。</span><span class="sxs-lookup"><span data-stu-id="05d9f-167">Moving or scaling things with voice is also difficult (voice does not offer the granularity of control).</span></span> <span data-ttu-id="05d9f-168">语音也可能是不完美的。</span><span class="sxs-lookup"><span data-stu-id="05d9f-168">Voice can also be imperfect.</span></span> <span data-ttu-id="05d9f-169">有时，语音系统会错误地听到命令或无法听到命令。</span><span class="sxs-lookup"><span data-stu-id="05d9f-169">Sometimes a voice system incorrectly hears a command or fails to hear a command.</span></span> <span data-ttu-id="05d9f-170">从这些错误中恢复对于任何界面而言都是难题。</span><span class="sxs-lookup"><span data-stu-id="05d9f-170">Recovering from such errors is a challenge in any interface.</span></span> <span data-ttu-id="05d9f-171">最后，声音在公共场所可能不被公众所接受。</span><span class="sxs-lookup"><span data-stu-id="05d9f-171">Lastly, voice may not be socially acceptable in public places.</span></span> <span data-ttu-id="05d9f-172">有些话用户不能或不应该说。</span><span class="sxs-lookup"><span data-stu-id="05d9f-172">There are some things that users can’t or shouldn’t say.</span></span> <span data-ttu-id="05d9f-173">这些限制使得语音应用于其最擅长的领域。</span><span class="sxs-lookup"><span data-stu-id="05d9f-173">These cliffs allow speech to be used for what it is best at.</span></span>

### <a name="voice-feedback-states"></a><span data-ttu-id="05d9f-174">语音反馈状态</span><span class="sxs-lookup"><span data-stu-id="05d9f-174">Voice feedback states</span></span>

<span data-ttu-id="05d9f-175">当语音应用正确时，用户了解他们能说什么，并得到清晰的反馈 - 系统正确地听到了用户说的话。</span><span class="sxs-lookup"><span data-stu-id="05d9f-175">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="05d9f-176">这两个信号使用户在使用语音作为主要输入方法时充满自信。</span><span class="sxs-lookup"><span data-stu-id="05d9f-176">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="05d9f-177">下面的图表显示了识别语音输入时光标发生的情况以及它是如何将信息传达给用户的。</span><span class="sxs-lookup"><span data-stu-id="05d9f-177">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>

<span data-ttu-id="05d9f-178">![光标的语音反馈状态](images/voicefeedbackstates.png)</span><span class="sxs-lookup"><span data-stu-id="05d9f-178">![Voice feedback states for cursor](images/voicefeedbackstates.png)</span></span><br>
<span data-ttu-id="05d9f-179">光标的语音反馈状态</span><span class="sxs-lookup"><span data-stu-id="05d9f-179">*Voice feedback states for cursor*</span></span>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="05d9f-180">在混合现实中，用户应该知道的关于“语音”的重要事项</span><span class="sxs-lookup"><span data-stu-id="05d9f-180">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="05d9f-181">在将一个按钮设置为目标时，说“选择”（可以在任何位置使用这种方法来单击按钮）。</span><span class="sxs-lookup"><span data-stu-id="05d9f-181">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="05d9f-182">可以在某些应用中通过说出应用栏按钮的标签名称来执行操作。</span><span class="sxs-lookup"><span data-stu-id="05d9f-182">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="05d9f-183">例如，在查看应用时，用户可以说“移除”命令以从现实中移除应用（这样可以节省用手单击按钮的时间）。</span><span class="sxs-lookup"><span data-stu-id="05d9f-183">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="05d9f-184">说“你好小娜”可以启动 Cortana 侦听。</span><span class="sxs-lookup"><span data-stu-id="05d9f-184">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="05d9f-185">你可以向她提问（“你好小娜，埃菲尔铁塔有多高”），告诉她打开应用（“你好小娜，打开 Netflix”），或告诉她调出“开始”菜单（“你好小娜，带我回家”）等等。</span><span class="sxs-lookup"><span data-stu-id="05d9f-185">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="05d9f-186">用户对语音的常见问题和关注点</span><span class="sxs-lookup"><span data-stu-id="05d9f-186">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="05d9f-187">我可以说什么？</span><span class="sxs-lookup"><span data-stu-id="05d9f-187">What can I say?</span></span>
* <span data-ttu-id="05d9f-188">我如何知道系统正确听到了我说的话？</span><span class="sxs-lookup"><span data-stu-id="05d9f-188">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="05d9f-189">系统总是理解错误我的语音命令。</span><span class="sxs-lookup"><span data-stu-id="05d9f-189">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="05d9f-190">当我发出语音命令时，系统不会做出反应。</span><span class="sxs-lookup"><span data-stu-id="05d9f-190">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="05d9f-191">当我发出语音命令时，系统的反应是错误的。</span><span class="sxs-lookup"><span data-stu-id="05d9f-191">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="05d9f-192">我如何将我的语音定向到一个特定的应用或应用命令？</span><span class="sxs-lookup"><span data-stu-id="05d9f-192">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="05d9f-193">我可以使用语音来对 HoloLens 上的全息帧执行命令吗？</span><span class="sxs-lookup"><span data-stu-id="05d9f-193">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="see-also"></a><span data-ttu-id="05d9f-194">请参阅</span><span class="sxs-lookup"><span data-stu-id="05d9f-194">See also</span></span>
* [<span data-ttu-id="05d9f-195">手势</span><span class="sxs-lookup"><span data-stu-id="05d9f-195">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="05d9f-196">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="05d9f-196">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
