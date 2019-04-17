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
# <a name="voice-input-in-directx"></a>在 DirectX 语音输入

本主题介绍如何实现[语音命令](voice-input.md)，和 Windows Mixed Reality 的 DirectX 应用中的小短语和句子识别。

>[!NOTE]
>这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。  这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>SpeechRecognizer 用于连续语音命令识别

在本部分中，我们介绍如何使用连续语音识别启用应用程序中的语音命令。 本演练使用从代码[HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964)示例。 当运行示例时，把一个已注册的颜色命令来更改旋转多维数据集的颜色的名称。

首先，创建一个新**Windows::Media::SpeechRecognition::SpeechRecognizer**实例。

从*HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

你将需要创建要侦听的识别器的语音命令的列表。 在这里，我们将构造一系列命令来更改一张全息图的颜色。 为了方便起见，我们还创建的数据，我们将更高版本上使用的所有命令。

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

可以使用语音单词可能不在字典中的指定命令：

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

命令列表载入语音识别器的约束列表。 这是通过使用[SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx)对象。

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

订阅[ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx)语音识别器的事件[SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)。 已识别你的命令之一时，此事件将通知您的应用程序。

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

你**OnResultGenerated**事件处理程序接收事件数据中的[SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx)实例。 置信度大于已定义的阈值，如果您的应用程序应注意在事件发生。 保存事件数据，以便可以进行后续更新循环中使用它。

从*HolographicVoiceInputSampleMain.cpp*:

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

请使用但是不适用于你的应用方案的数据。 在我们的示例代码，我们更改旋转全息图多维数据集根据用户的命令的颜色。

从*HolographicVoiceInputSampleMain::Update*:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>使用单步识别的语音短语和句子的听写

你可以配置要侦听的短语或句子讲出用户的语音识别器。 在这种情况下，我们应用告知哪种类型的输入需要的语音识别器 SpeechRecognitionTopicConstraint。 应用工作流如下所示，对于此类型的用例：
1. 您的应用程序创建 SpeechRecognizer，提供了用户界面提示，并开始侦听命令立即朗读。
2. 用户使用短语或句子。
3. 不执行的用户的语音识别，并且结果返回到应用程序。 此时，您的应用程序应提供一个用户界面提示，指示已发生的识别。
4. 具体取决于你想要响应的置信度级别和语音识别结果的置信度级别，您的应用程序可以处理结果，并相应地做出响应。

本部分介绍如何创建 SpeechRecognizer、 编译该约束，以及如何侦听语音输入。

下面的代码编译主题约束，在这种情况下针对 Web 搜索进行了优化。

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

如果编译成功，我们可以继续进行语音识别。

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

然后向应用返回的结果。 如果我们确信在结果中，我们可以处理该命令。 此代码示例至少中等信心十足地处理结果。

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

只要您使用语音识别，你应监视可能表示用户已经关闭了系统的隐私设置麦克风的异常。 这可以在初始化期间或在识别。

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

**注意：** 有几个预定义[SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx)可用于优化语音识别。
* 如果你想要优化的听写，使用听写方案：

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* 当使用语音来执行 Web 搜索，可以按如下所示使用特定于 Web 的方案约束：

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* 使用窗体约束来填写窗体。 在这种情况下，最好将应用用于填充窗体布局优化自己语法。

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* 你可以提供您自己使用 SRGS 格式语法。

## <a name="use-continuous-freeform-speech-dictation"></a>使用连续、 自由格式语音听写

请参阅连续听写方案的 Windows 10 UWP 语音代码示例[此处。](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>处理质量下降

环境中的条件有时会阻止工作的语音识别。 例如，空间可能会过多的干扰或用户可能会说出在过高的卷。 语音识别 API 提供的信息，如有可能，有关导致质量下降的条件。

此信息推送到您的应用程序使用 WinRT 事件。 下面是如何订阅此事件的示例。

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

在我们的代码示例中，我们选择将条件信息写入到调试控制台。 应用程序可能想要通过用户界面、 语音合成等，向用户提供反馈或者它可能需要临时质量下降时中断语音的行为有所不同。

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

如果不使用 ref 类创建您的 DirectX 应用程序，您必须取消订阅事件之前释放或重新创建语音识别器。 HolographicSpeechPromptSample 已停止识别，并取消订阅事件的例程如下所示：

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>使用语音合成，提供声音语音提示

Holographic 语音示例使用语音合成来向用户提供可听见的说明。 本主题将指导完成创建合成的语音示例中，并播放使用 HRTF 音频 Api 的过程。

应提供你自己的语音提示请求短语输入时。 这也会有所帮助的该值指示时可被朗读的语音命令，对于连续识别方案。 下面是如何使用语音合成器; 执行该操作的示例请注意，您也可以使用预先录制的声音剪辑、 可视用户界面或要说，例如在其中提示不是动态的方案中的其他指示符。

首先，创建 SpeechSynthesizer 对象：

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

您还需要与将要合成的文本字符串：

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

以异步方式使用 SynthesizeTextToStreamAsync 合成语音。 在这里，我们开始一个异步任务合成语音。

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

作为字节流发送语音合成。 我们可以初始化该字节流，则使用 XAudio2 语音有关我们的全息版的代码示例，我们播放该录制为 HRTF 音频效果。

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

作为使用语音识别，语音合成将引发异常出现问题时。

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

## <a name="see-also"></a>请参阅
* [语音应用程序设计](https://msdn.microsoft.com/library/dn596121.aspx)
* [在 DirectX 空间声音](spatial-sound-in-directx.md)
* [SpeechRecognitionAndSynthesis 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
