---
title: Azure 语音服务教程 - 1. 集成并使用语音识别和听录
description: 请完成本课程来了解如何在混合现实应用程序中实施 Azure 语音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 71a6c2124258f05e80e624b940386db72a36070b
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604978"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1.集成并使用语音识别和听录

## <a name="overview"></a>概述


在本教程系列中，你将创建一个混合现实应用程序用于探索如何将 Azure 语音服务与 HoloLens 2 配合使用。 完成本教程系列后，你便可以使用设备的麦克风实时进行语音转文本的听录，将语音翻译成其他语言，并利用意向识别功能通过人工智能来理解语音命令。

## <a name="objectives"></a>目标

* 了解如何将 Azure 语音服务与 HoloLens 2 应用程序相集成
* 了解如何使用语音识别来听录文本

## <a name="prerequisites"></a>必备条件

>[!TIP]
>如果你尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。

* 一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一些基本的 C# 编程功能
* 一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块

> [!IMPORTANT]
> 建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。

## <a name="creating-and-preparing-the-unity-project"></a>创建和准备 Unity 项目

在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。

为此，请先执行[初始化项目和第一个应用程序](mrlearning-base-ch1.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)的说明：

1. [创建新的 Unity 项目](mrlearning-base-ch1.md#create-new-unity-project)并为其指定适当的名称，例如 *MRTK Tutorials*

2. [配置用于 Windows Mixed Reality 的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [导入 TextMesh Pro 基本资源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [配置用于混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [将混合现实工具包添加到 Unity 场景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)，并为该场景指定适当的名称，例如 *AzureSpeechServices*

然后，根据[如何配置混合现实工具包配置文件（更改空间感知显示选项）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡”。  

> [!CAUTION]
> 根据上面链接的[配置用于混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)说明中所述，强烈建议不要为 Unity 启用 MSBuild。

## <a name="configuring-the-speech-commands-start-behavior"></a>配置语音命令的启动行为

由于你要使用语音 SDK 进行语音识别和听录，因此需要配置 MRTK 语音命令，使其不会干扰语音 SDK 的功能。 为此，可将语音命令的启动行为从“自动启动”更改为“手动启动”。

在“层次结构”窗口中选择“MixedRealityToolkit”对象后，在“检查器”窗口中选择“输入”选项卡，克隆“DefaultHoloLens2InputSystemProfile”和“DefaultMixedRealitySpeechCommandsProfile”，然后将语音命令的“启动行为”更改为“手动启动”：      

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> 有关如何克隆和配置 MRTK 配置文件的提示，可参阅[如何配置混合现实工具包配置文件（更改空间感知显示选项）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明。

## <a name="configuring-the-capabilities"></a>配置功能

在 Unity 菜单中，选择“编辑” > “项目设置...”打开“播放器设置”窗口，然后找到“播放器” >  “发布设置”部分：    

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

在“发布设置”中，向下滚动到“功能”部分，仔细检查在教程中最初创建项目时启用的“InternetClient”、“Microphone”和“SpatialPerception”功能是否确实已启用。      然后启用“InternetClientServer”和“PrivateNetworkClientServer”功能：  

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>导入教程资产

下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage)（最新版本）
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)中的说明。

导入教程资产后，“项目”窗口应如下所示：

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a>准备场景

在本部分，你将通过添加教程预制件来准备场景，并配置“Lunarcom 控制器(脚本)”组件来控制场景。

在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpeechServices” > “预制件”文件夹，并将“Lunarcom”预制件拖放到“层次结构”窗口中，以将其添加到场景中：    

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

仍在“层次结构”窗口中选中了“Lunarcom”对象的情况下，在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 控制器(脚本)”组件添加到 Lunarcom 对象中：   

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> MRTK 中未包含“Lunarcom 控制器(脚本)”组件。 本教程的资产中随附了该组件。

在仍选中了“Lunarcom”对象的情况下，将其展开以显示其子对象，然后将“Terminal”对象拖放到“Lunarcom 控制器(脚本)”组件的“终端”字段中：   

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

在仍选中了“Lunarcom”对象的情况下，展开 Terminal 对象以显示其子对象，然后将“ConnectionLight”对象拖放到“Lunarcom 控制器(脚本)”组件的“连接光线”字段中，并将“OutputText”对象拖放到“输出文本”字段中：     

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

在仍选中了“Lunarcom”对象的情况下，展开 Buttons 对象以显示其子对象，然后在“检查器”窗口中展开“按钮”列表，将其“大小”设置为 3，并将“MicButton”、“SatelliteButton”和“RocketButton”对象分别拖放到“元素 0”、“元素 1”和“元素 2”字段中：       

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>将 Unity 项目连接到 Azure 资源

若要使用 Azure 语音服务，需要创建一个 Azure 资源并获取语音服务的 API 密钥。 按照“[免费试用语音服务](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)”中的说明进行操作，并记下服务区域（也称为“位置”）和 API 密钥（也称为“密钥 1”或“密钥 2”）。

在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中找到“Lunarcom 控制器(脚本)”组件的“语音 SDK 凭据”部分，并按如下所述对其进行配置：   

* 在“语音服务 API 密钥”字段中，输入你的 API 密钥（“密钥 1”或“密钥 2”） 
* 在“语音服务区域”字段中，使用小写字母输入不带空格的服务区域（位置） 

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>使用语音识别听录语音

在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 语音识别器(脚本)”组件添加到 Lunarcom 对象中：   

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> MRTK 中未包含“Lunarcom 语音识别器(脚本)”组件。 本教程的资产中随附了该组件。

如果现在进入“游戏”模式，可以先按麦克风按钮来测试语音识别：

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

假设计算机上配备了麦克风，当你讲话时，会在终端面板上听录你的语音：

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> 应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。

## <a name="congratulations"></a>祝贺

现已实现了由 Azure 提供支持的语音识别。 请在设备上运行该应用程序，以确保功能正常。

下一篇教程将介绍如何使用 Azure 语音识别执行命令。

[下一教程：2.使用语音识别执行命令](mrlearning-speechSDK-ch2.md)
