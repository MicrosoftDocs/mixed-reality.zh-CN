---
title: 在 DirectX 语音输入
description: 介绍如何为 Windows Mixed Reality DirectX 应用中实现语音命令和较小的短语和句子识别。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 演练、 语音命令、 短语、 识别、 语音、 directx、 平台、 cortana、 windows 混合的现实
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593068"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="44cc6-104">在 DirectX 语音输入</span><span class="sxs-lookup"><span data-stu-id="44cc6-104">Voice input in DirectX</span></span>

<span data-ttu-id="44cc6-105">本主题介绍如何实现[语音命令](voice-input.md)，和 Windows Mixed Reality 的 DirectX 应用中的小短语和句子识别。</span><span class="sxs-lookup"><span data-stu-id="44cc6-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="44cc6-106">这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="44cc6-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="44cc6-107">这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。</span><span class="sxs-lookup"><span data-stu-id="44cc6-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="44cc6-108">SpeechRecognizer 用于连续语音命令识别</span><span class="sxs-lookup"><span data-stu-id="44cc6-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="44cc6-109">在本部分中，我们介绍如何使用连续语音识别启用应用程序中的语音命令。</span><span class="sxs-lookup"><span data-stu-id="44cc6-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="44cc6-110">本演练使用从代码[HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964)示例。</span><span class="sxs-lookup"><span data-stu-id="44cc6-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="44cc6-111">当运行示例时，把一个已注册的颜色命令来更改旋转多维数据集的颜色的名称。</span><span class="sxs-lookup"><span data-stu-id="44cc6-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="44cc6-112">首先，创建一个新**Windows::Media::SpeechRecognition::SpeechRecognizer**实例。</span><span class="sxs-lookup"><span data-stu-id="44cc6-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="44cc6-113">从*HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="44cc6-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="44cc6-114">你将需要创建要侦听的识别器的语音命令的列表。</span><span class="sxs-lookup"><span data-stu-id="44cc6-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="44cc6-115">在这里，我们将构造一系列命令来更改一张全息图的颜色。</span><span class="sxs-lookup"><span data-stu-id="44cc6-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="44cc6-116">为了方便起见，我们还创建的数据，我们将更高版本上使用的所有命令。</span><span class="sxs-lookup"><span data-stu-id="44cc6-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

<span data-ttu-id="44cc6-117">可以使用语音单词可能不在字典中的指定命令：</span><span class="sxs-lookup"><span data-stu-id="44cc6-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="44cc6-118">命令列表载入语音识别器的约束列表。</span><span class="sxs-lookup"><span data-stu-id="44cc6-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="44cc6-119">这是通过使用[SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)对象。</span><span class="sxs-lookup"><span data-stu-id="44cc6-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

<span data-ttu-id="44cc6-120">订阅[ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)语音识别器的事件[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)。</span><span class="sxs-lookup"><span data-stu-id="44cc6-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="44cc6-121">已识别你的命令之一时，此事件将通知您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="44cc6-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="44cc6-122">你**OnResultGenerated**事件处理程序接收事件数据中的[SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)实例。</span><span class="sxs-lookup"><span data-stu-id="44cc6-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="44cc6-123">置信度大于已定义的阈值，如果您的应用程序应注意在事件发生。</span><span class="sxs-lookup"><span data-stu-id="44cc6-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="44cc6-124">保存事件数据，以便可以进行后续更新循环中使用它。</span><span class="sxs-lookup"><span data-stu-id="44cc6-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="44cc6-125">从*HolographicVoiceInputSampleMain.cpp*:</span><span class="sxs-lookup"><span data-stu-id="44cc6-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

<span data-ttu-id="44cc6-126">请使用但是不适用于你的应用方案的数据。</span><span class="sxs-lookup"><span data-stu-id="44cc6-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="44cc6-127">在我们的示例代码，我们更改旋转全息图多维数据集根据用户的命令的颜色。</span><span class="sxs-lookup"><span data-stu-id="44cc6-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="44cc6-128">从*HolographicVoiceInputSampleMain::Update*:</span><span class="sxs-lookup"><span data-stu-id="44cc6-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="44cc6-129">使用单步识别的语音短语和句子的听写</span><span class="sxs-lookup"><span data-stu-id="44cc6-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="44cc6-130">你可以配置要侦听的短语或句子讲出用户的语音识别器。</span><span class="sxs-lookup"><span data-stu-id="44cc6-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="44cc6-131">在这种情况下，我们应用告知哪种类型的输入需要的语音识别器 SpeechRecognitionTopicConstraint。</span><span class="sxs-lookup"><span data-stu-id="44cc6-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="44cc6-132">应用工作流如下所示，对于此类型的用例：</span><span class="sxs-lookup"><span data-stu-id="44cc6-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="44cc6-133">您的应用程序创建 SpeechRecognizer，提供了用户界面提示，并开始侦听命令立即朗读。</span><span class="sxs-lookup"><span data-stu-id="44cc6-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="44cc6-134">用户使用短语或句子。</span><span class="sxs-lookup"><span data-stu-id="44cc6-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="44cc6-135">不执行的用户的语音识别，并且结果返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="44cc6-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="44cc6-136">此时，您的应用程序应提供一个用户界面提示，指示已发生的识别。</span><span class="sxs-lookup"><span data-stu-id="44cc6-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="44cc6-137">具体取决于你想要响应的置信度级别和语音识别结果的置信度级别，您的应用程序可以处理结果，并相应地做出响应。</span><span class="sxs-lookup"><span data-stu-id="44cc6-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="44cc6-138">本部分介绍如何创建 SpeechRecognizer、 编译该约束，以及如何侦听语音输入。</span><span class="sxs-lookup"><span data-stu-id="44cc6-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="44cc6-139">下面的代码编译主题约束，在这种情况下针对 Web 搜索进行了优化。</span><span class="sxs-lookup"><span data-stu-id="44cc6-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="44cc6-140">如果编译成功，我们可以继续进行语音识别。</span><span class="sxs-lookup"><span data-stu-id="44cc6-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

<span data-ttu-id="44cc6-141">然后向应用返回的结果。</span><span class="sxs-lookup"><span data-stu-id="44cc6-141">The result is then returned to the app.</span></span> <span data-ttu-id="44cc6-142">如果我们确信在结果中，我们可以处理该命令。</span><span class="sxs-lookup"><span data-stu-id="44cc6-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="44cc6-143">此代码示例至少中等信心十足地处理结果。</span><span class="sxs-lookup"><span data-stu-id="44cc6-143">This code example processes results with at least Medium confidence.</span></span>

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

<span data-ttu-id="44cc6-144">只要您使用语音识别，你应监视可能表示用户已经关闭了系统的隐私设置麦克风的异常。</span><span class="sxs-lookup"><span data-stu-id="44cc6-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="44cc6-145">这可以在初始化期间或在识别。</span><span class="sxs-lookup"><span data-stu-id="44cc6-145">This can happen during initialization, or during recognition.</span></span>

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

<span data-ttu-id="44cc6-146">**注意：** 有几个预定义[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)可用于优化语音识别。</span><span class="sxs-lookup"><span data-stu-id="44cc6-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="44cc6-147">如果你想要优化的听写，使用听写方案：</span><span class="sxs-lookup"><span data-stu-id="44cc6-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="44cc6-148">当使用语音来执行 Web 搜索，可以按如下所示使用特定于 Web 的方案约束：</span><span class="sxs-lookup"><span data-stu-id="44cc6-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="44cc6-149">使用窗体约束来填写窗体。</span><span class="sxs-lookup"><span data-stu-id="44cc6-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="44cc6-150">在这种情况下，最好将应用用于填充窗体布局优化自己语法。</span><span class="sxs-lookup"><span data-stu-id="44cc6-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="44cc6-151">你可以提供您自己使用 SRGS 格式语法。</span><span class="sxs-lookup"><span data-stu-id="44cc6-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="44cc6-152">使用连续、 自由格式语音听写</span><span class="sxs-lookup"><span data-stu-id="44cc6-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="44cc6-153">请参阅连续听写方案的 Windows 10 UWP 语音代码示例[此处。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="44cc6-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="44cc6-154">处理质量下降</span><span class="sxs-lookup"><span data-stu-id="44cc6-154">Handle degradation in quality</span></span>

<span data-ttu-id="44cc6-155">环境中的条件有时会阻止工作的语音识别。</span><span class="sxs-lookup"><span data-stu-id="44cc6-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="44cc6-156">例如，空间可能会过多的干扰或用户可能会说出在过高的卷。</span><span class="sxs-lookup"><span data-stu-id="44cc6-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="44cc6-157">语音识别 API 提供的信息，如有可能，有关导致质量下降的条件。</span><span class="sxs-lookup"><span data-stu-id="44cc6-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="44cc6-158">此信息推送到您的应用程序使用 WinRT 事件。</span><span class="sxs-lookup"><span data-stu-id="44cc6-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="44cc6-159">下面是如何订阅此事件的示例。</span><span class="sxs-lookup"><span data-stu-id="44cc6-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="44cc6-160">在我们的代码示例中，我们选择将条件信息写入到调试控制台。</span><span class="sxs-lookup"><span data-stu-id="44cc6-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="44cc6-161">应用程序可能想要通过用户界面、 语音合成等，向用户提供反馈或者它可能需要临时质量下降时中断语音的行为有所不同。</span><span class="sxs-lookup"><span data-stu-id="44cc6-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

<span data-ttu-id="44cc6-162">如果不使用 ref 类创建您的 DirectX 应用程序，您必须取消订阅事件之前释放或重新创建语音识别器。</span><span class="sxs-lookup"><span data-stu-id="44cc6-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="44cc6-163">HolographicSpeechPromptSample 已停止识别，并取消订阅事件的例程如下所示：</span><span class="sxs-lookup"><span data-stu-id="44cc6-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="44cc6-164">使用语音合成，提供声音语音提示</span><span class="sxs-lookup"><span data-stu-id="44cc6-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="44cc6-165">Holographic 语音示例使用语音合成来向用户提供可听见的说明。</span><span class="sxs-lookup"><span data-stu-id="44cc6-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="44cc6-166">本主题将指导完成创建合成的语音示例中，并播放使用 HRTF 音频 Api 的过程。</span><span class="sxs-lookup"><span data-stu-id="44cc6-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="44cc6-167">应提供你自己的语音提示请求短语输入时。</span><span class="sxs-lookup"><span data-stu-id="44cc6-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="44cc6-168">这也会有所帮助的该值指示时可被朗读的语音命令，对于连续识别方案。</span><span class="sxs-lookup"><span data-stu-id="44cc6-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="44cc6-169">下面是如何使用语音合成器; 执行该操作的示例请注意，您也可以使用预先录制的声音剪辑、 可视用户界面或要说，例如在其中提示不是动态的方案中的其他指示符。</span><span class="sxs-lookup"><span data-stu-id="44cc6-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="44cc6-170">首先，创建 SpeechSynthesizer 对象：</span><span class="sxs-lookup"><span data-stu-id="44cc6-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="44cc6-171">您还需要与将要合成的文本字符串：</span><span class="sxs-lookup"><span data-stu-id="44cc6-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="44cc6-172">以异步方式使用 SynthesizeTextToStreamAsync 合成语音。</span><span class="sxs-lookup"><span data-stu-id="44cc6-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="44cc6-173">在这里，我们开始一个异步任务合成语音。</span><span class="sxs-lookup"><span data-stu-id="44cc6-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="44cc6-174">作为字节流发送语音合成。</span><span class="sxs-lookup"><span data-stu-id="44cc6-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="44cc6-175">我们可以初始化该字节流，则使用 XAudio2 语音有关我们的全息版的代码示例，我们播放该录制为 HRTF 音频效果。</span><span class="sxs-lookup"><span data-stu-id="44cc6-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

<span data-ttu-id="44cc6-176">作为使用语音识别，语音合成将引发异常出现问题时。</span><span class="sxs-lookup"><span data-stu-id="44cc6-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a><span data-ttu-id="44cc6-177">请参阅</span><span class="sxs-lookup"><span data-stu-id="44cc6-177">See also</span></span>
* [<span data-ttu-id="44cc6-178">语音应用程序设计</span><span class="sxs-lookup"><span data-stu-id="44cc6-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="44cc6-179">在 DirectX 空间声音</span><span class="sxs-lookup"><span data-stu-id="44cc6-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="44cc6-180">SpeechRecognitionAndSynthesis 示例</span><span class="sxs-lookup"><span data-stu-id="44cc6-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
