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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593011"
---
# <a name="voice-input-in-unity"></a>在 Unity 中的语音输入

Unity 公开三种方法可以添加[语音输入](voice-input.md)到 Unity 应用程序。

与 KeywordRecognizer （两种类型的 PhraseRecognizers 之一），您的应用程序可以提供字符串命令要侦听的数组。 与 GrammarRecognizer （其他类型的 PhraseRecognizer） 中，您的应用程序可以提供定义的特定语法来侦听 SRGS 文件。 DictationRecognizer，与您的应用程序可以侦听的任何字词，并向用户提供的注释或其他显示其语音。

>[!NOTE]
>只有听写或短语识别可以一次性处理。 这意味着如果 GrammarRecognizer 或 KeywordRecognizer 处于活动状态，DictationRecognizer 可以不处于活动状态，反之亦然。

## <a name="enabling-the-capability-for-voice"></a>启用语音功能

**麦克风**必须为应用程序以利用语音输入声明功能。
1. 在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置
2. 单击"Windows 应用商店"选项卡
3. 在"发布设置 > 功能"部分中，检查**麦克风**功能

## <a name="phrase-recognition"></a>短语识别

若要启用侦听的特定于您的应用程序然后由用户所说的短语执行某些操作，你需要：
1. 指定要侦听的使用 KeywordRecognizer 或 GrammarRecognizer 的短语
2. 处理 OnPhraseRecognized 事件并采取措施对应识别的短语

### <a name="keywordrecognizer"></a>KeywordRecognizer

**命名空间：***UnityEngine.Windows.Speech*<br>
**类型：***KeywordRecognizer*， *PhraseRecognizedEventArgs*， *SpeechError*， *SpeechSystemStatus*

我们将需要几个 using 语句以保存一些击键：

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

然后让我们将添加到您的类来存储的识别器和关键字的几个字段-> 操作字典：

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

现在将关键字添加到字典 （例如内部的 start （） 方法）。 我们在此示例中添加的"激活"关键字：

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

创建关键字识别器，并告诉它我们想要识别：

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

现在注册 OnPhraseRecognized 事件

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

是一个示例处理程序：

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

最后，开始意识到 ！

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**命名空间：***UnityEngine.Windows.Speech*<br>
**类型**:*GrammarRecognizer*， *PhraseRecognizedEventArgs*， *SpeechError*， *SpeechSystemStatus*

如果要指定使用 SRGS 你识别语法，使用 GrammarRecognizer。 如果您的应用程序具有多个只需几个关键字，如果你想要识别更复杂的短语，或者如果你想要轻松地打开和关闭命令集，这可以很有用。 请参阅：[创建语法使用 SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx)有关文件格式的信息。

一旦有你 SRGS 语法，并且它是在项目中[StreamingAssets 文件夹](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

创建 GrammarRecognizer 并将其传递路径到 SRGS 文件：

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

现在注册 OnPhraseRecognized 事件

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

你将收到包含信息可以适当地处理你 SRGS 语法中指定的回调。 将 semanticMeanings 数组中提供的大多数重要信息。

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

最后，开始意识到 ！

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>听写

**命名空间：***UnityEngine.Windows.Speech*<br>
**类型**:*DictationRecognizer*， *SpeechError*， *SpeechSystemStatus*

使用 DictationRecognizer 将用户的语音转换为文本。 公开 DictationRecognizer[听写](voice-input.md#dictation)功能和支持注册和侦听的假设和短语完成事件，因此它们讲话时，可以向这两个用户提供反馈和之后。 Start （） 和 stop （） 方法分别启用和禁用时听写识别。 完成后识别器，它应使用 dispose （） 方法来释放它所使用的资源被释放。 它将释放这些资源会自动在其他性能成本的垃圾回收期间如果它们不在此之前，释放。

有需要若要开始使用听写仅几个步骤：
1. 创建新 DictationRecognizer
2. 句柄听写事件
3. 启动 DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>启用听写的功能

必须为应用程序以利用听写声明的"Internet 客户端"功能，除了前面所述的"麦克风"功能。
1. 在 Unity 编辑器中，转到播放机设置通过导航到"编辑 > 项目设置 > Player"页面
2. 单击"Windows 应用商店"选项卡
3. 在"发布设置 > 功能"部分中，检查**InternetClient**功能

### <a name="dictationrecognizer"></a>DictationRecognizer

创建 DictationRecognizer 如下所示：

```
dictationRecognizer = new DictationRecognizer();
```

有四个听写事件，可以订阅和处理以实现听写行为。
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

此事件触发后用户暂停，通常在一个句子末尾。 完整识别此处返回字符串。

首先，订阅 DictationResult 事件：

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

然后处理 DictationResult 回调：

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

用户正在通信时，持续激发此事件。 识别器在侦听，它提供的是什么文本听说过到目前为止。

首先，订阅 DictationHypothesis 事件：

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

然后处理 DictationHypothesis 回调：

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

激发此事件当识别器停止时，无论是从 stop （） 调用，超时情况或某些其他错误。

首先，订阅 DictationComplete 事件：

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

然后处理 DictationComplete 回调：

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

发生错误时激发此事件。

首先，订阅 DictationError 事件：

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

然后处理 DictationError 回调：

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

订阅并处理您关心的听写事件后，开始时听写识别器，若要开始接收事件。

```
dictationRecognizer.Start();
```

如果不再想要保留围绕 DictationRecognizer，需要取消订阅事件并释放 DictationRecognizer。

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**提示**
* Start （） 和 stop （） 方法分别启用和禁用时听写识别。
* 完成后识别器，它必须释放使用 dispose （） 方法来释放它所使用的资源。 它将释放这些资源会自动在其他性能成本的垃圾回收期间如果它们不在此之前，释放。
* 在一段时间后，会出现超时。 你可以检查这些超时 DictationComplete 事件中。 有两个超时，需要注意的：
   1. 如果识别器开始，并为第一个 5 秒将不会收听任何音频，就会超时。
   2. 如果识别器提供结果，但然后会静默听到 20 秒，就会超时。

## <a name="using-both-phrase-recognition-and-dictation"></a>使用短语识别和听写

如果你想要在应用中使用短语识别和听写，您将需要完全关闭其中一个才能开始另。 如果有多个 KeywordRecognizers 运行后, 即可关闭它们全部同时使用：

```
PhraseRecognitionSystem.Shutdown();
```

为了将所有的识别器还原到其以前的状态，DictationRecognizer 已停止后，您可以调用：

```
PhraseRecognitionSystem.Restart();
```

也可以启动 KeywordRecognizer，这将重启 PhraseRecognitionSystem 也。

## <a name="using-the-microphone-helper"></a>使用麦克风帮助器

GitHub 上的混合现实工具包包含一个麦克风帮助器类，以提示在开发人员，如果在系统上没有可用的麦克风。 它的一个用途是一个想要检查是否有麦克风系统上的应用程序中显示任何语音交互提示前。

可以在找到麦克风帮助程序脚本[输入脚本/实用工具文件夹](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs)。 GitHub 存储库还包含[小型示例](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs)演示了如何使用该帮助器。

## <a name="voice-input-in-mixed-reality-toolkit"></a>混合现实工具包中的语音输入
在此场景中，可以找到语音输入的示例。

- [HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
