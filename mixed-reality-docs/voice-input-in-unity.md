---
title: 在 Unity 中的语音输入
description: Unity 公开三种方法添加到 Windows Mixed Reality 应用程序的语音输入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 语音输入、 KeywordRecognizer、 GrammarRecognizer、 麦克风、 听写、 语音
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593011"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="48653-104">在 Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="48653-104">Voice input in Unity</span></span>

<span data-ttu-id="48653-105">Unity 公开三种方法可以添加[语音输入](voice-input.md)到 Unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="48653-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="48653-106">与 KeywordRecognizer （两种类型的 PhraseRecognizers 之一），您的应用程序可以提供字符串命令要侦听的数组。</span><span class="sxs-lookup"><span data-stu-id="48653-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="48653-107">与 GrammarRecognizer （其他类型的 PhraseRecognizer） 中，您的应用程序可以提供定义的特定语法来侦听 SRGS 文件。</span><span class="sxs-lookup"><span data-stu-id="48653-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="48653-108">DictationRecognizer，与您的应用程序可以侦听的任何字词，并向用户提供的注释或其他显示其语音。</span><span class="sxs-lookup"><span data-stu-id="48653-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="48653-109">只有听写或短语识别可以一次性处理。</span><span class="sxs-lookup"><span data-stu-id="48653-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="48653-110">这意味着如果 GrammarRecognizer 或 KeywordRecognizer 处于活动状态，DictationRecognizer 可以不处于活动状态，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="48653-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="48653-111">启用语音功能</span><span class="sxs-lookup"><span data-stu-id="48653-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="48653-112">**麦克风**必须为应用程序以利用语音输入声明功能。</span><span class="sxs-lookup"><span data-stu-id="48653-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="48653-113">在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置</span><span class="sxs-lookup"><span data-stu-id="48653-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="48653-114">单击"Windows 应用商店"选项卡</span><span class="sxs-lookup"><span data-stu-id="48653-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="48653-115">在"发布设置 > 功能"部分中，检查**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="48653-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="48653-116">短语识别</span><span class="sxs-lookup"><span data-stu-id="48653-116">Phrase Recognition</span></span>

<span data-ttu-id="48653-117">若要启用侦听的特定于您的应用程序然后由用户所说的短语执行某些操作，你需要：</span><span class="sxs-lookup"><span data-stu-id="48653-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="48653-118">指定要侦听的使用 KeywordRecognizer 或 GrammarRecognizer 的短语</span><span class="sxs-lookup"><span data-stu-id="48653-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="48653-119">处理 OnPhraseRecognized 事件并采取措施对应识别的短语</span><span class="sxs-lookup"><span data-stu-id="48653-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="48653-120">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="48653-120">KeywordRecognizer</span></span>

<span data-ttu-id="48653-121">**命名空间：** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="48653-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="48653-122">**类型**： *KeywordRecognizer*， *PhraseRecognizedEventArgs*， *SpeechError*， *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="48653-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="48653-123">我们将需要几个 using 语句以保存一些击键：</span><span class="sxs-lookup"><span data-stu-id="48653-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="48653-124">然后让我们将添加到您的类来存储的识别器和关键字的几个字段-> 操作字典：</span><span class="sxs-lookup"><span data-stu-id="48653-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="48653-125">现在将关键字添加到字典 （例如内部的 start （） 方法）。</span><span class="sxs-lookup"><span data-stu-id="48653-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="48653-126">我们在此示例中添加的"激活"关键字：</span><span class="sxs-lookup"><span data-stu-id="48653-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="48653-127">创建关键字识别器，并告诉它我们想要识别：</span><span class="sxs-lookup"><span data-stu-id="48653-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="48653-128">现在注册 OnPhraseRecognized 事件</span><span class="sxs-lookup"><span data-stu-id="48653-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="48653-129">是一个示例处理程序：</span><span class="sxs-lookup"><span data-stu-id="48653-129">An example handler is:</span></span>

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

<span data-ttu-id="48653-130">最后，开始意识到 ！</span><span class="sxs-lookup"><span data-stu-id="48653-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="48653-131">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="48653-131">GrammarRecognizer</span></span>

<span data-ttu-id="48653-132">**命名空间：** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="48653-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="48653-133">**类型**: *GrammarRecognizer*， *PhraseRecognizedEventArgs*， *SpeechError*， *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="48653-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="48653-134">如果要指定使用 SRGS 你识别语法，使用 GrammarRecognizer。</span><span class="sxs-lookup"><span data-stu-id="48653-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="48653-135">如果您的应用程序具有多个只需几个关键字，如果你想要识别更复杂的短语，或者如果你想要轻松地打开和关闭命令集，这可以很有用。</span><span class="sxs-lookup"><span data-stu-id="48653-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="48653-136">请参阅：[创建语法使用 SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx)有关文件格式的信息。</span><span class="sxs-lookup"><span data-stu-id="48653-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="48653-137">一旦有你 SRGS 语法，并且它是在项目中[StreamingAssets 文件夹](http://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="48653-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="48653-138">创建 GrammarRecognizer 并将其传递路径到 SRGS 文件：</span><span class="sxs-lookup"><span data-stu-id="48653-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="48653-139">现在注册 OnPhraseRecognized 事件</span><span class="sxs-lookup"><span data-stu-id="48653-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="48653-140">你将收到包含信息可以适当地处理你 SRGS 语法中指定的回调。</span><span class="sxs-lookup"><span data-stu-id="48653-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="48653-141">将 semanticMeanings 数组中提供的大多数重要信息。</span><span class="sxs-lookup"><span data-stu-id="48653-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="48653-142">最后，开始意识到 ！</span><span class="sxs-lookup"><span data-stu-id="48653-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="48653-143">听写</span><span class="sxs-lookup"><span data-stu-id="48653-143">Dictation</span></span>

<span data-ttu-id="48653-144">**命名空间：** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="48653-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="48653-145">**类型**: *DictationRecognizer*， *SpeechError*， *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="48653-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="48653-146">使用 DictationRecognizer 将用户的语音转换为文本。</span><span class="sxs-lookup"><span data-stu-id="48653-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="48653-147">公开 DictationRecognizer[听写](voice-input.md#dictation)功能和支持注册和侦听的假设和短语完成事件，因此它们讲话时，可以向这两个用户提供反馈和之后。</span><span class="sxs-lookup"><span data-stu-id="48653-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="48653-148">Start （） 和 stop （） 方法分别启用和禁用时听写识别。</span><span class="sxs-lookup"><span data-stu-id="48653-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="48653-149">完成后识别器，它应使用 dispose （） 方法来释放它所使用的资源被释放。</span><span class="sxs-lookup"><span data-stu-id="48653-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="48653-150">它将释放这些资源会自动在其他性能成本的垃圾回收期间如果它们不在此之前，释放。</span><span class="sxs-lookup"><span data-stu-id="48653-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="48653-151">有需要若要开始使用听写仅几个步骤：</span><span class="sxs-lookup"><span data-stu-id="48653-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="48653-152">创建新 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="48653-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="48653-153">句柄听写事件</span><span class="sxs-lookup"><span data-stu-id="48653-153">Handle Dictation events</span></span>
3. <span data-ttu-id="48653-154">启动 DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="48653-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="48653-155">启用听写的功能</span><span class="sxs-lookup"><span data-stu-id="48653-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="48653-156">必须为应用程序以利用听写声明的"Internet 客户端"功能，除了前面所述的"麦克风"功能。</span><span class="sxs-lookup"><span data-stu-id="48653-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="48653-157">在 Unity 编辑器中，转到播放机设置通过导航到"编辑 > 项目设置 > Player"页面</span><span class="sxs-lookup"><span data-stu-id="48653-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="48653-158">单击"Windows 应用商店"选项卡</span><span class="sxs-lookup"><span data-stu-id="48653-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="48653-159">在"发布设置 > 功能"部分中，检查**InternetClient**功能</span><span class="sxs-lookup"><span data-stu-id="48653-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="48653-160">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="48653-160">DictationRecognizer</span></span>

<span data-ttu-id="48653-161">创建 DictationRecognizer 如下所示：</span><span class="sxs-lookup"><span data-stu-id="48653-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="48653-162">有四个听写事件，可以订阅和处理以实现听写行为。</span><span class="sxs-lookup"><span data-stu-id="48653-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="48653-163">DictationResult</span><span class="sxs-lookup"><span data-stu-id="48653-163">DictationResult</span></span>
2. <span data-ttu-id="48653-164">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="48653-164">DictationComplete</span></span>
3. <span data-ttu-id="48653-165">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="48653-165">DictationHypothesis</span></span>
4. <span data-ttu-id="48653-166">DictationError</span><span class="sxs-lookup"><span data-stu-id="48653-166">DictationError</span></span>

<span data-ttu-id="48653-167">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="48653-167">**DictationResult**</span></span>

<span data-ttu-id="48653-168">此事件触发后用户暂停，通常在一个句子末尾。</span><span class="sxs-lookup"><span data-stu-id="48653-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="48653-169">完整识别此处返回字符串。</span><span class="sxs-lookup"><span data-stu-id="48653-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="48653-170">首先，订阅 DictationResult 事件：</span><span class="sxs-lookup"><span data-stu-id="48653-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="48653-171">然后处理 DictationResult 回调：</span><span class="sxs-lookup"><span data-stu-id="48653-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="48653-172">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="48653-172">**DictationHypothesis**</span></span>

<span data-ttu-id="48653-173">用户正在通信时，持续激发此事件。</span><span class="sxs-lookup"><span data-stu-id="48653-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="48653-174">识别器在侦听，它提供的是什么文本听说过到目前为止。</span><span class="sxs-lookup"><span data-stu-id="48653-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="48653-175">首先，订阅 DictationHypothesis 事件：</span><span class="sxs-lookup"><span data-stu-id="48653-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="48653-176">然后处理 DictationHypothesis 回调：</span><span class="sxs-lookup"><span data-stu-id="48653-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="48653-177">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="48653-177">**DictationComplete**</span></span>

<span data-ttu-id="48653-178">激发此事件当识别器停止时，无论是从 stop （） 调用，超时情况或某些其他错误。</span><span class="sxs-lookup"><span data-stu-id="48653-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="48653-179">首先，订阅 DictationComplete 事件：</span><span class="sxs-lookup"><span data-stu-id="48653-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="48653-180">然后处理 DictationComplete 回调：</span><span class="sxs-lookup"><span data-stu-id="48653-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="48653-181">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="48653-181">**DictationError**</span></span>

<span data-ttu-id="48653-182">发生错误时激发此事件。</span><span class="sxs-lookup"><span data-stu-id="48653-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="48653-183">首先，订阅 DictationError 事件：</span><span class="sxs-lookup"><span data-stu-id="48653-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="48653-184">然后处理 DictationError 回调：</span><span class="sxs-lookup"><span data-stu-id="48653-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="48653-185">订阅并处理您关心的听写事件后，开始时听写识别器，若要开始接收事件。</span><span class="sxs-lookup"><span data-stu-id="48653-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="48653-186">如果不再想要保留围绕 DictationRecognizer，需要取消订阅事件并释放 DictationRecognizer。</span><span class="sxs-lookup"><span data-stu-id="48653-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="48653-187">**提示**</span><span class="sxs-lookup"><span data-stu-id="48653-187">**Tips**</span></span>
* <span data-ttu-id="48653-188">Start （） 和 stop （） 方法分别启用和禁用时听写识别。</span><span class="sxs-lookup"><span data-stu-id="48653-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="48653-189">完成后识别器，它必须释放使用 dispose （） 方法来释放它所使用的资源。</span><span class="sxs-lookup"><span data-stu-id="48653-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="48653-190">它将释放这些资源会自动在其他性能成本的垃圾回收期间如果它们不在此之前，释放。</span><span class="sxs-lookup"><span data-stu-id="48653-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="48653-191">在一段时间后，会出现超时。</span><span class="sxs-lookup"><span data-stu-id="48653-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="48653-192">你可以检查这些超时 DictationComplete 事件中。</span><span class="sxs-lookup"><span data-stu-id="48653-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="48653-193">有两个超时，需要注意的：</span><span class="sxs-lookup"><span data-stu-id="48653-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="48653-194">如果识别器开始，并为第一个 5 秒将不会收听任何音频，就会超时。</span><span class="sxs-lookup"><span data-stu-id="48653-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="48653-195">如果识别器提供结果，但然后会静默听到 20 秒，就会超时。</span><span class="sxs-lookup"><span data-stu-id="48653-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="48653-196">使用短语识别和听写</span><span class="sxs-lookup"><span data-stu-id="48653-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="48653-197">如果你想要在应用中使用短语识别和听写，您将需要完全关闭其中一个才能开始另。</span><span class="sxs-lookup"><span data-stu-id="48653-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="48653-198">如果有多个 KeywordRecognizers 运行后, 即可关闭它们全部同时使用：</span><span class="sxs-lookup"><span data-stu-id="48653-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="48653-199">为了将所有的识别器还原到其以前的状态，DictationRecognizer 已停止后，您可以调用：</span><span class="sxs-lookup"><span data-stu-id="48653-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="48653-200">也可以启动 KeywordRecognizer，这将重启 PhraseRecognitionSystem 也。</span><span class="sxs-lookup"><span data-stu-id="48653-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="48653-201">使用麦克风帮助器</span><span class="sxs-lookup"><span data-stu-id="48653-201">Using the microphone helper</span></span>

<span data-ttu-id="48653-202">GitHub 上的混合现实工具包包含一个麦克风帮助器类，以提示在开发人员，如果在系统上没有可用的麦克风。</span><span class="sxs-lookup"><span data-stu-id="48653-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="48653-203">它的一个用途是一个想要检查是否有麦克风系统上的应用程序中显示任何语音交互提示前。</span><span class="sxs-lookup"><span data-stu-id="48653-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="48653-204">可以在找到麦克风帮助程序脚本[输入脚本/实用工具文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)。</span><span class="sxs-lookup"><span data-stu-id="48653-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="48653-205">GitHub 存储库还包含[小型示例](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs)演示了如何使用该帮助器。</span><span class="sxs-lookup"><span data-stu-id="48653-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="48653-206">混合现实工具包中的语音输入</span><span class="sxs-lookup"><span data-stu-id="48653-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="48653-207">在此场景中，可以找到语音输入的示例。</span><span class="sxs-lookup"><span data-stu-id="48653-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="48653-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span><span class="sxs-lookup"><span data-stu-id="48653-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
