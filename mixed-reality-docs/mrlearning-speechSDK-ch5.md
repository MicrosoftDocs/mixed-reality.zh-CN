---
title: MR SpeechSDK Module-语音识别和脚本
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: cf51505cab2db765325c2e7b78a52e4b790845c9
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105953"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a>Speech SDK 学习模块-使用语音命令的火箭启动器控件

在本课程中，我们将使用 Azure 语音服务的意向功能来了解语音的意图。 我们将使用检测到的语音的意图来控制火箭启动器。 在本课程中，我们将导入火箭启动器资产，并将检测到的意向语音命令接口到预定义的控制按钮以控制火箭。

## <a name="objectives"></a>目标

- 了解如何将语音意向连接为语音命令。
- 了解如何使用语音意向语音命令作为火箭控制输入命令。

## <a name="instructions"></a>说明

1. 在本教程中，我们将使用 "BaseModule" 资源将火箭启动器与语音命令集成。 为此，我们需要将资产导入到项目中。 你可以使用此[链接](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)下载 "火箭启动器" 资产。

2. 若要导入资产，请转到 "资产-> 导入包-> 自定义包" > 导航到下载的文件，然后单击 "导入"。

    ![module4chapter5step1](images/module4chapter5step1.PNG)

3. 导入 "基本模块资产" 资产后，在 "基本模块资产" 文件夹中导航 > Prototyping-> 选择 "火箭 Launcher_Complete"，然后将其拖放到现有场景层次结构。

    ![module4chapter5step2](images/module4chapter5step2.PNG)

4. 现在，我们需要将 "火箭启动器" 与我们在上一课中介绍的 LUIS 项目相[集成。](mrlearning-speechSDK-ch4.md) 为此，请在层次结构中展开 "火箭 Launcher_Complete" prefab，并查找 "LaunchRoundButton"、"ResetRoundButton" 和 "位置提示" 按钮。

    ![module4chapter5step3](images/module4chapter5step3.PNG)

5. 选择 "LaunchRoundButton"，然后在 "检查器" 面板中，依次单击 "种不可交互" 和 "事件" OnClick （） "，拖放" LunarModule "prefab。 然后，选择 "函数" 下拉箭头并选择 "LunarModule"，并导航到 "StartThruster （）" 函数并将其选中。

    ![module4chapter5step 3。0](images/module4chapter5step3.0.PNG)

    ![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. 选择 "ResetRoundButton"，然后在 "检查器" 面板中，依次单击 "种不可交互" 和 "事件" OnClick （） "，拖放" LunarModule "prefab。 然后，选择 "函数" 下拉箭头并选择 "LunarModule"，并导航到 "resetModule （）" 函数并将其选中。

    ![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. 选择 "放置提示"，然后在 "检查器" 面板中，选择 "种不可交互"，并在事件 "OnClick （）" 下，拖放 "LunarModule" prefab。 然后，选择 "函数" 下拉箭头并选择 "LunarModule"，并导航到 "TogglePlacementHints" 函数，然后选择 "ToggleGameOBjects （）"。

    ![module4chapter5step3c](images/module4chapter5step3c.PNG)

8. 接下来，选择层次结构中的 Lunarcom_Completed prefab，并导航到检查器中的 "Lunarcom 意向识别器" 脚本，然后将 "LaunchRoundButton"、"ResetRoundButton" 和 "位置提示" 按钮拖放到各自的位置。

    ![module4chapter5step4](images/module4chapter5step4.PNG)

9. 按下 Unity 编辑器中的 "播放" 按钮，然后单击 "火箭" 按钮，然后 utter "推送火箭启动" 按钮、"向我显示放置提示"、"按 rest" 按钮，或与启动、重置或提示的火箭启动器请求相关的任何其他短语。

    ![module4chapter5step5a](images/module4chapter5step5a.PNG)

    ![module4chapter5step5b](images/module4chapter5step5b.PNG)

    ![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a>祝贺

在本课中，我们学习了如何将 AI 功能的语音命令连接到语音命令，以将其用作输入方法。 现在，我们的程序可以使用扬声器意向作为语音命令，为火箭启动器提供输入。
