---
title: Unity 中的语音输入
description: Unity 公开了三种向 Windows Mixed Reality 应用程序添加语音输入的方法。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 语音输入, KeywordRecognizer, GrammarRecognizer, 麦克风, 听写, 语音
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548682"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="1ebd8-104">Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="1ebd8-104">Voice input in Unity</span></span>

<span data-ttu-id="1ebd8-105">Unity 公开了三种将[语音输入](voice-input.md)添加到 Unity 应用程序的方法。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="1ebd8-106">使用 KeywordRecognizer (PhraseRecognizers 的两种类型之一), 可以为应用提供一个要侦听的字符串命令数组。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="1ebd8-107">使用 GrammarRecognizer (PhraseRecognizer 的另一种类型), 可以为应用指定一个 SRGS 文件, 用于定义要侦听的特定语法。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="1ebd8-108">使用 DictationRecognizer, 你的应用程序可以侦听任何字词, 并向用户提供其语音的注释或其他显示。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="1ebd8-109">一次只能处理听写或短语识别。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="1ebd8-110">这意味着, 如果 GrammarRecognizer 或 KeywordRecognizer 处于活动状态, 则 DictationRecognizer 不能处于活动状态, 反之亦然。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="1ebd8-111">启用语音功能</span><span class="sxs-lookup"><span data-stu-id="1ebd8-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="1ebd8-112">必须为应用声明**麦克风**功能才能利用语音输入。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="1ebd8-113">在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player", 转到 "播放机" 设置</span><span class="sxs-lookup"><span data-stu-id="1ebd8-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="1ebd8-114">单击 "Windows 应用商店" 选项卡</span><span class="sxs-lookup"><span data-stu-id="1ebd8-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="1ebd8-115">在 "发布设置 > 功能" 部分中, 检查**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="1ebd8-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="1ebd8-116">短语识别</span><span class="sxs-lookup"><span data-stu-id="1ebd8-116">Phrase Recognition</span></span>

<span data-ttu-id="1ebd8-117">若要使你的应用能够侦听用户所说的特定短语, 请采取一些操作, 你需要执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="1ebd8-118">使用 KeywordRecognizer 或 GrammarRecognizer 指定要侦听的短语</span><span class="sxs-lookup"><span data-stu-id="1ebd8-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="1ebd8-119">处理 OnPhraseRecognized 事件并执行与已识别的短语对应的操作</span><span class="sxs-lookup"><span data-stu-id="1ebd8-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="1ebd8-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="1ebd8-120">KeywordRecognizer</span></span>

<span data-ttu-id="1ebd8-121">**命名空间：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="1ebd8-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="1ebd8-122">**类型**： *KeywordRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="1ebd8-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="1ebd8-123">我们需要使用几个语句来保存一些击键:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="1ebd8-124">接下来, 让我们将一些字段添加到类, 以存储识别器和关键字 > 操作字典:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="1ebd8-125">现在, 向字典添加关键字 (例如, 在 Start () 方法中)。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="1ebd8-126">在此示例中, 我们要添加 "activate" 关键字:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="1ebd8-127">创建关键字识别器并告诉它我们要识别的内容:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="1ebd8-128">现在注册 OnPhraseRecognized 事件</span><span class="sxs-lookup"><span data-stu-id="1ebd8-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="1ebd8-129">示例处理程序是:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-129">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="1ebd8-130">最后, 开始识别!</span><span class="sxs-lookup"><span data-stu-id="1ebd8-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="1ebd8-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="1ebd8-131">GrammarRecognizer</span></span>

<span data-ttu-id="1ebd8-132">**命名空间：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="1ebd8-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="1ebd8-133">**类型**: *GrammarRecognizer*、 *PhraseRecognizedEventArgs*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="1ebd8-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="1ebd8-134">如果要使用 SRGS 指定识别语法, 则使用 GrammarRecognizer。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="1ebd8-135">如果你的应用程序包含多个关键字 (如果你想要识别更复杂的短语), 或者如果你想要轻松打开和关闭命令集, 这会很有用。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="1ebd8-136">请参阅：[使用 SRGS XML 创建语法](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx), 以获取文件格式信息。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="1ebd8-137">获得 SRGS 语法后, 在项目中的[StreamingAssets 文件夹](http://docs.unity3d.com/Manual/StreamingAssets.html)中:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="1ebd8-138">创建 GrammarRecognizer 并向其传递 SRGS 文件的路径:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="1ebd8-139">现在注册 OnPhraseRecognized 事件</span><span class="sxs-lookup"><span data-stu-id="1ebd8-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="1ebd8-140">你将获得一个回拨, 其中包含你可以相应处理的 SRGS 语法中指定的信息。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="1ebd8-141">最重要的信息将在 semanticMeanings 数组中提供。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="1ebd8-142">最后, 开始识别!</span><span class="sxs-lookup"><span data-stu-id="1ebd8-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="1ebd8-143">听写</span><span class="sxs-lookup"><span data-stu-id="1ebd8-143">Dictation</span></span>

<span data-ttu-id="1ebd8-144">**命名空间：** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="1ebd8-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="1ebd8-145">**类型**: *DictationRecognizer*、 *SpeechError*、 *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="1ebd8-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="1ebd8-146">使用 DictationRecognizer 将用户的语音转换为文本。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="1ebd8-147">DictationRecognizer 公开[听写](voice-input.md#dictation)功能, 并支持注册和侦听假设和短语完成的事件, 因此, 你可以在用户讲话和之后向用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="1ebd8-148">Start () 和 Stop () 方法分别启用和禁用听写识别。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="1ebd8-149">完成识别器后, 应使用 Dispose () 方法来释放它所使用的资源。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="1ebd8-150">如果未在此之前释放这些资源, 它将在垃圾回收期间自动释放这些资源。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="1ebd8-151">开始使用听写只需几个步骤:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="1ebd8-152">创建新的 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="1ebd8-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="1ebd8-153">处理听写事件</span><span class="sxs-lookup"><span data-stu-id="1ebd8-153">Handle Dictation events</span></span>
3. <span data-ttu-id="1ebd8-154">启动 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="1ebd8-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="1ebd8-155">启用听写功能</span><span class="sxs-lookup"><span data-stu-id="1ebd8-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="1ebd8-156">除了上面提到的 "麦克风" 功能以外, 还必须为应用声明 "Internet 客户端" 功能才能利用听写。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="1ebd8-157">在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player" 页, 转到 "播放机" 设置</span><span class="sxs-lookup"><span data-stu-id="1ebd8-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="1ebd8-158">单击 "Windows 应用商店" 选项卡</span><span class="sxs-lookup"><span data-stu-id="1ebd8-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="1ebd8-159">在 "发布设置 > 功能" 部分中, 查看**InternetClient**功能</span><span class="sxs-lookup"><span data-stu-id="1ebd8-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="1ebd8-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="1ebd8-160">DictationRecognizer</span></span>

<span data-ttu-id="1ebd8-161">创建 DictationRecognizer, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="1ebd8-162">可以订阅和处理四个听写事件, 以实现听写行为。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="1ebd8-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="1ebd8-163">DictationResult</span></span>
2. <span data-ttu-id="1ebd8-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="1ebd8-164">DictationComplete</span></span>
3. <span data-ttu-id="1ebd8-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="1ebd8-165">DictationHypothesis</span></span>
4. <span data-ttu-id="1ebd8-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="1ebd8-166">DictationError</span></span>

<span data-ttu-id="1ebd8-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="1ebd8-167">**DictationResult**</span></span>

<span data-ttu-id="1ebd8-168">此事件在用户暂停之后 (通常是在句子结束时) 触发。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="1ebd8-169">此处返回了已识别的完整字符串。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="1ebd8-170">首先, 订阅 DictationResult 事件:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="1ebd8-171">然后处理 DictationResult 回调:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="1ebd8-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="1ebd8-172">**DictationHypothesis**</span></span>

<span data-ttu-id="1ebd8-173">当用户正在对话时, 将连续触发此事件。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="1ebd8-174">当识别器倾听时, 它提供了到目前为止所听说内容的文本。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="1ebd8-175">首先, 订阅 DictationHypothesis 事件:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="1ebd8-176">然后处理 DictationHypothesis 回调:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="1ebd8-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="1ebd8-177">**DictationComplete**</span></span>

<span data-ttu-id="1ebd8-178">当识别器停止时, 无论是正在调用停止 ()、发生超时还是发生其他错误, 都将激发此事件。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="1ebd8-179">首先, 订阅 DictationComplete 事件:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="1ebd8-180">然后处理 DictationComplete 回调:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="1ebd8-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="1ebd8-181">**DictationError**</span></span>

<span data-ttu-id="1ebd8-182">当发生错误时, 将激发此事件。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="1ebd8-183">首先, 订阅 DictationError 事件:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="1ebd8-184">然后处理 DictationError 回调:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="1ebd8-185">订阅并处理了所关注的听写事件后, 启动听写识别器以开始接收事件。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="1ebd8-186">如果不再想要保留 DictationRecognizer, 则需要取消订阅事件并释放 DictationRecognizer。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="1ebd8-187">**技巧**</span><span class="sxs-lookup"><span data-stu-id="1ebd8-187">**Tips**</span></span>
* <span data-ttu-id="1ebd8-188">Start () 和 Stop () 方法分别启用和禁用听写识别。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="1ebd8-189">完成识别器后, 必须使用 Dispose () 方法来释放它所使用的资源。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="1ebd8-190">如果未在此之前释放这些资源, 它将在垃圾回收期间自动释放这些资源。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="1ebd8-191">超时发生在设定的时间段之后。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="1ebd8-192">可以在 DictationComplete 事件中检查这些超时。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="1ebd8-193">需要注意两个超时:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="1ebd8-194">如果识别器在前五秒内开始播放并且不听到任何音频, 则会超时。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="1ebd8-195">如果识别器给定了结果, 但随后听到了20秒, 则会超时。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="1ebd8-196">使用短语识别和听写</span><span class="sxs-lookup"><span data-stu-id="1ebd8-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="1ebd8-197">如果你想要在应用中同时使用短语识别和听写, 则需要完全关闭一项, 然后才能启动另一个。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="1ebd8-198">如果有多个 KeywordRecognizers 正在运行, 则可以使用以下操作一次性关闭它们:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="1ebd8-199">若要将所有识别器还原到其以前的状态, 在 DictationRecognizer 停止后, 可以调用:</span><span class="sxs-lookup"><span data-stu-id="1ebd8-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="1ebd8-200">还可以只启动 KeywordRecognizer, 这也会重新启动 PhraseRecognitionSystem。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="1ebd8-201">使用麦克风帮助器</span><span class="sxs-lookup"><span data-stu-id="1ebd8-201">Using the microphone helper</span></span>

<span data-ttu-id="1ebd8-202">如果系统上有可用麦克风, 则 GitHub 上的混合现实工具包包含一个麦克风帮助器类, 用于提示开发人员。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="1ebd8-203">其中一种用途是在显示应用程序中的任何语音交互提示之前, 要检查系统上是否有麦克风。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="1ebd8-204">麦克风帮助器脚本可以在 "[输入/脚本/实用工具" 文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)中找到。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="1ebd8-205">GitHub 存储库还包含一[小示例](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs), 演示如何使用帮助程序。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="1ebd8-206">混合现实工具包中的语音输入</span><span class="sxs-lookup"><span data-stu-id="1ebd8-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="1ebd8-207">在此场景中, 可以找到语音输入的示例。</span><span class="sxs-lookup"><span data-stu-id="1ebd8-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="1ebd8-208">HoloToolkit-Examples/Input/场景/SpeechInputSource</span><span class="sxs-lookup"><span data-stu-id="1ebd8-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
