---
title: DirectX 中的语音输入
description: 介绍如何在适用于 Windows Mixed Reality 的 DirectX 应用程序中实现语音命令和短语识别。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 演练, 语音命令, 短语, 识别, 语音, directx, 平台, cortana, windows mixed reality
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548662"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="a1c26-104">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="a1c26-104">Voice input in DirectX</span></span>

<span data-ttu-id="a1c26-105">本主题介绍如何在适用于 Windows Mixed Reality 的 DirectX 应用程序中实现[语音命令](voice-input.md)和短语识别。</span><span class="sxs-lookup"><span data-stu-id="a1c26-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="a1c26-106">本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT, 这与全息项目模板中使用的不同。</span><span class="sxs-lookup"><span data-stu-id="a1c26-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="a1c26-107">概念对于C++/WinRT 项目是等效的, 但你将需要转换代码。</span><span class="sxs-lookup"><span data-stu-id="a1c26-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="a1c26-108">使用 SpeechRecognizer 来连续识别语音命令</span><span class="sxs-lookup"><span data-stu-id="a1c26-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="a1c26-109">本部分介绍如何使用连续语音识别在应用中启用语音命令。</span><span class="sxs-lookup"><span data-stu-id="a1c26-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="a1c26-110">本演练使用[HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964)示例中的代码。</span><span class="sxs-lookup"><span data-stu-id="a1c26-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="a1c26-111">当示例运行时, 请用一个已注册颜色命令的名称来更改旋转立方体的颜色。</span><span class="sxs-lookup"><span data-stu-id="a1c26-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="a1c26-112">首先, 创建一个新的**Windows:: Media:: SpeechRecognition:: SpeechRecognizer**实例。</span><span class="sxs-lookup"><span data-stu-id="a1c26-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="a1c26-113">From *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="a1c26-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="a1c26-114">你需要创建一个语音命令列表, 供识别器侦听。</span><span class="sxs-lookup"><span data-stu-id="a1c26-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="a1c26-115">在这里, 我们将构造一组命令来更改全息图的颜色。</span><span class="sxs-lookup"><span data-stu-id="a1c26-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="a1c26-116">为方便起见, 我们还创建了以后用于命令的数据。</span><span class="sxs-lookup"><span data-stu-id="a1c26-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="a1c26-117">可以使用不在字典中的拼音词来指定命令:</span><span class="sxs-lookup"><span data-stu-id="a1c26-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="a1c26-118">命令列表将加载到语音识别器的约束列表中。</span><span class="sxs-lookup"><span data-stu-id="a1c26-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="a1c26-119">这是通过使用[SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)对象来完成的。</span><span class="sxs-lookup"><span data-stu-id="a1c26-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="a1c26-120">订阅语音识别器的[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)上的[ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)事件。</span><span class="sxs-lookup"><span data-stu-id="a1c26-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="a1c26-121">此事件将在你已识别到你的某个命令时通知你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a1c26-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="a1c26-122">**OnResultGenerated**事件处理程序接收[SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)实例中的事件数据。</span><span class="sxs-lookup"><span data-stu-id="a1c26-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="a1c26-123">如果置信度大于你定义的阈值, 应用应注意到事件发生。</span><span class="sxs-lookup"><span data-stu-id="a1c26-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="a1c26-124">保存事件数据, 以便您可以在后续的更新循环中使用它。</span><span class="sxs-lookup"><span data-stu-id="a1c26-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="a1c26-125">从*HolographicVoiceInputSampleMain*:</span><span class="sxs-lookup"><span data-stu-id="a1c26-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="a1c26-126">使用适用于应用方案的数据。</span><span class="sxs-lookup"><span data-stu-id="a1c26-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="a1c26-127">在我们的示例代码中, 我们将根据用户的命令更改旋转全息图多维数据集的颜色。</span><span class="sxs-lookup"><span data-stu-id="a1c26-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="a1c26-128">From *HolographicVoiceInputSampleMain:: Update*:</span><span class="sxs-lookup"><span data-stu-id="a1c26-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="a1c26-129">使用听写进行语音短语和句子的一次拍摄识别</span><span class="sxs-lookup"><span data-stu-id="a1c26-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="a1c26-130">你可以配置语音识别器来侦听用户所说的短语或句子。</span><span class="sxs-lookup"><span data-stu-id="a1c26-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="a1c26-131">在这种情况下, 我们将应用 SpeechRecognitionTopicConstraint, 告知语音识别器所需的输入类型。</span><span class="sxs-lookup"><span data-stu-id="a1c26-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="a1c26-132">对于这种类型的用例, 应用工作流如下所示:</span><span class="sxs-lookup"><span data-stu-id="a1c26-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="a1c26-133">你的应用程序将创建 SpeechRecognizer, 提供 UI 提示, 并开始侦听要立即口述的命令。</span><span class="sxs-lookup"><span data-stu-id="a1c26-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="a1c26-134">用户使用一个短语或句子。</span><span class="sxs-lookup"><span data-stu-id="a1c26-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="a1c26-135">执行用户语音识别, 并将结果返回到应用。</span><span class="sxs-lookup"><span data-stu-id="a1c26-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="a1c26-136">此时, 你的应用程序应提供指示已发生识别的 UI 提示。</span><span class="sxs-lookup"><span data-stu-id="a1c26-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="a1c26-137">根据你想要响应的置信度和语音识别结果的置信度, 你的应用程序可以处理结果并相应地做出响应。</span><span class="sxs-lookup"><span data-stu-id="a1c26-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="a1c26-138">本部分介绍如何创建 SpeechRecognizer、编译约束和侦听语音输入。</span><span class="sxs-lookup"><span data-stu-id="a1c26-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="a1c26-139">下面的代码编译主题约束, 这种情况下, 它针对 Web 搜索进行了优化。</span><span class="sxs-lookup"><span data-stu-id="a1c26-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="a1c26-140">如果编译成功, 则可以继续语音识别。</span><span class="sxs-lookup"><span data-stu-id="a1c26-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="a1c26-141">然后, 将结果返回到应用程序。</span><span class="sxs-lookup"><span data-stu-id="a1c26-141">The result is then returned to the app.</span></span> <span data-ttu-id="a1c26-142">如果在结果中可以放心, 我们可以处理该命令。</span><span class="sxs-lookup"><span data-stu-id="a1c26-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="a1c26-143">此代码示例处理至少具有中等置信度的结果。</span><span class="sxs-lookup"><span data-stu-id="a1c26-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="a1c26-144">无论何时使用语音识别, 都应注意到可能表示用户已在系统隐私设置中关闭麦克风的例外情况。</span><span class="sxs-lookup"><span data-stu-id="a1c26-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="a1c26-145">这可能在初始化期间或在识别期间发生。</span><span class="sxs-lookup"><span data-stu-id="a1c26-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="a1c26-146">**注意：** 有几个预定义的[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)可用于优化语音识别。</span><span class="sxs-lookup"><span data-stu-id="a1c26-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="a1c26-147">如果要优化听写, 请使用听写方案:</span><span class="sxs-lookup"><span data-stu-id="a1c26-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="a1c26-148">使用语音执行 Web 搜索时, 可以使用特定于 Web 的方案约束, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="a1c26-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="a1c26-149">使用窗体约束填写表单。</span><span class="sxs-lookup"><span data-stu-id="a1c26-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="a1c26-150">在这种情况下, 最好应用自己的语法, 该语法经过优化, 可用于填写表单。</span><span class="sxs-lookup"><span data-stu-id="a1c26-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="a1c26-151">可以使用 SRGS 格式提供自己的语法。</span><span class="sxs-lookup"><span data-stu-id="a1c26-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="a1c26-152">使用连续的自由语音听写</span><span class="sxs-lookup"><span data-stu-id="a1c26-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="a1c26-153">请参阅此处持续听写方案的 Windows 10 UWP 语音代码示例[。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="a1c26-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="a1c26-154">处理质量降低</span><span class="sxs-lookup"><span data-stu-id="a1c26-154">Handle degradation in quality</span></span>

<span data-ttu-id="a1c26-155">环境中的条件有时会阻止语音识别工作。</span><span class="sxs-lookup"><span data-stu-id="a1c26-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="a1c26-156">例如, 房间可能太大, 或者用户的音量可能过高。</span><span class="sxs-lookup"><span data-stu-id="a1c26-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="a1c26-157">语音识别 API 尽可能地提供信息, 这与导致质量降低的情况有关。</span><span class="sxs-lookup"><span data-stu-id="a1c26-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="a1c26-158">此信息将使用 WinRT 事件推送到应用。</span><span class="sxs-lookup"><span data-stu-id="a1c26-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="a1c26-159">下面是有关如何订阅此事件的示例。</span><span class="sxs-lookup"><span data-stu-id="a1c26-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="a1c26-160">在我们的代码示例中, 我们选择将条件信息写入调试控制台。</span><span class="sxs-lookup"><span data-stu-id="a1c26-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="a1c26-161">应用可能需要通过 UI、语音合成等向用户提供反馈, 或者当语音被暂时降低质量的中断时, 可能需要以不同的方式进行操作。</span><span class="sxs-lookup"><span data-stu-id="a1c26-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="a1c26-162">如果未使用 ref 类创建 DirectX 应用, 则必须先取消对事件的订阅, 然后再释放或重新创建语音识别器。</span><span class="sxs-lookup"><span data-stu-id="a1c26-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="a1c26-163">HolographicSpeechPromptSample 有一个停止识别的例程, 并取消如下事件的订阅:</span><span class="sxs-lookup"><span data-stu-id="a1c26-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="a1c26-164">使用语音合成来提供可听见的语音提示</span><span class="sxs-lookup"><span data-stu-id="a1c26-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="a1c26-165">全息语音示例使用语音合成向用户提供可听见的指令。</span><span class="sxs-lookup"><span data-stu-id="a1c26-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="a1c26-166">本主题将指导你完成创建合成语音示例的过程, 并使用 HRTF 音频 Api 将其播放回来。</span><span class="sxs-lookup"><span data-stu-id="a1c26-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="a1c26-167">请求短语输入时应提供自己的语音提示。</span><span class="sxs-lookup"><span data-stu-id="a1c26-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="a1c26-168">这也有助于指示语音命令可以被口述的时间, 用于持续识别方案。</span><span class="sxs-lookup"><span data-stu-id="a1c26-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="a1c26-169">下面是如何使用语音合成器执行此操作的示例;请注意, 您还可以使用预先录制的语音剪辑、视觉对象或其他指示符, 例如在提示不是动态的情况下。</span><span class="sxs-lookup"><span data-stu-id="a1c26-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="a1c26-170">首先, 创建 SpeechSynthesizer 对象:</span><span class="sxs-lookup"><span data-stu-id="a1c26-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="a1c26-171">还需要一个字符串, 其中包含要合成的文本:</span><span class="sxs-lookup"><span data-stu-id="a1c26-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="a1c26-172">语音使用 SynthesizeTextToStreamAsync 进行异步合成。</span><span class="sxs-lookup"><span data-stu-id="a1c26-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="a1c26-173">在这里, 我们将开始合成语音的异步任务。</span><span class="sxs-lookup"><span data-stu-id="a1c26-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="a1c26-174">语音合成作为字节流发送。</span><span class="sxs-lookup"><span data-stu-id="a1c26-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="a1c26-175">我们可以使用该字节流初始化 XAudio2 语音;对于我们的全息代码示例, 我们将它作为 HRTF 音频效果播放。</span><span class="sxs-lookup"><span data-stu-id="a1c26-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="a1c26-176">与语音识别一样, 如果出现问题, 语音合成会引发异常。</span><span class="sxs-lookup"><span data-stu-id="a1c26-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a1c26-177">请参阅</span><span class="sxs-lookup"><span data-stu-id="a1c26-177">See also</span></span>
* [<span data-ttu-id="a1c26-178">语音应用设计</span><span class="sxs-lookup"><span data-stu-id="a1c26-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="a1c26-179">DirectX 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="a1c26-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="a1c26-180">SpeechRecognitionAndSynthesis 示例</span><span class="sxs-lookup"><span data-stu-id="a1c26-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
