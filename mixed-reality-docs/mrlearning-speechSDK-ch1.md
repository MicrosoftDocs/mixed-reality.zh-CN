---
title: Azure 语音服务教程 - 1. 集成并使用语音识别和听录
description: 请完成本课程来了解如何在混合现实应用程序中实施 Azure 语音 SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: a72eb808adbc14df65c55e694ea985d97f9ec24c
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79032461"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="fb76b-105">1.集成并使用语音识别和听录</span><span class="sxs-lookup"><span data-stu-id="fb76b-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="fb76b-106">概述</span><span class="sxs-lookup"><span data-stu-id="fb76b-106">Overview</span></span>


<span data-ttu-id="fb76b-107">在本教程系列中，你将创建一个混合现实应用程序用于探索如何将 Azure 语音服务与 HoloLens 2 配合使用。</span><span class="sxs-lookup"><span data-stu-id="fb76b-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="fb76b-108">完成本教程系列后，你便可以使用设备的麦克风实时进行语音转文本的听录，将语音翻译成其他语言，并利用意向识别功能通过人工智能来理解语音命令。</span><span class="sxs-lookup"><span data-stu-id="fb76b-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="fb76b-109">目标</span><span class="sxs-lookup"><span data-stu-id="fb76b-109">Objectives</span></span>

* <span data-ttu-id="fb76b-110">了解如何将 Azure 语音服务与 HoloLens 2 应用程序相集成</span><span class="sxs-lookup"><span data-stu-id="fb76b-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="fb76b-111">了解如何使用语音识别来听录文本</span><span class="sxs-lookup"><span data-stu-id="fb76b-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fb76b-112">必备条件</span><span class="sxs-lookup"><span data-stu-id="fb76b-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="fb76b-113">如果你尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。</span><span class="sxs-lookup"><span data-stu-id="fb76b-113">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="fb76b-114">一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="fb76b-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="fb76b-115">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="fb76b-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="fb76b-116">一些基本的 C# 编程功能</span><span class="sxs-lookup"><span data-stu-id="fb76b-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="fb76b-117">一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="fb76b-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="fb76b-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="fb76b-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb76b-119">建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。</span><span class="sxs-lookup"><span data-stu-id="fb76b-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="fb76b-120">这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="fb76b-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="fb76b-121">创建和准备 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="fb76b-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="fb76b-122">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="fb76b-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="fb76b-123">为此，请先执行[初始化项目和第一个应用程序](mrlearning-base-ch1.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)的说明：</span><span class="sxs-lookup"><span data-stu-id="fb76b-123">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="fb76b-124">[创建新的 Unity 项目](mrlearning-base-ch1.md#create-new-unity-project)并为其指定适当的名称，例如 *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="fb76b-124">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="fb76b-125">配置用于 Windows Mixed Reality 的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="fb76b-125">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="fb76b-126">导入 TextMesh Pro 基本资源</span><span class="sxs-lookup"><span data-stu-id="fb76b-126">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="fb76b-127">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="fb76b-127">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="fb76b-128">配置用于混合现实工具包的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="fb76b-128">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="fb76b-129">[将混合现实工具包添加到 Unity 场景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)，并为该场景指定适当的名称，例如 *AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="fb76b-129">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="fb76b-130">然后，根据[如何配置混合现实工具包配置文件（更改空间感知显示选项）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡”。  </span><span class="sxs-lookup"><span data-stu-id="fb76b-130">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="fb76b-131">根据上面链接的[配置用于混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)说明中所述，强烈建议不要为 Unity 启用 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="fb76b-131">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="fb76b-132">配置语音命令的启动行为</span><span class="sxs-lookup"><span data-stu-id="fb76b-132">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="fb76b-133">由于你要使用语音 SDK 进行语音识别和听录，因此需要配置 MRTK 语音命令，使其不会干扰语音 SDK 的功能。</span><span class="sxs-lookup"><span data-stu-id="fb76b-133">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="fb76b-134">为此，可将语音命令的启动行为从“自动启动”更改为“手动启动”。</span><span class="sxs-lookup"><span data-stu-id="fb76b-134">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="fb76b-135">在“层次结构”窗口中选择“MixedRealityToolkit”对象后，在“检查器”窗口中选择“输入”选项卡，克隆“DefaultHoloLens2InputSystemProfile”和“DefaultMixedRealitySpeechCommandsProfile”，然后将语音命令的“启动行为”更改为“手动启动”：      </span><span class="sxs-lookup"><span data-stu-id="fb76b-135">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="fb76b-137">有关如何克隆和配置 MRTK 配置文件的提示，可参阅[如何配置混合现实工具包配置文件（更改空间感知显示选项）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明。</span><span class="sxs-lookup"><span data-stu-id="fb76b-137">For a reminder on how to clone and configure MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="fb76b-138">配置功能</span><span class="sxs-lookup"><span data-stu-id="fb76b-138">Configuring the capabilities</span></span>

<span data-ttu-id="fb76b-139">在 Unity 菜单中，选择“编辑” > “项目设置...”打开“播放器设置”窗口，然后找到“播放器” >  “发布设置”部分：    </span><span class="sxs-lookup"><span data-stu-id="fb76b-139">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="fb76b-141">在“发布设置”中，向下滚动到“功能”部分，仔细检查在教程中最初创建项目时启用的“InternetClient”、“Microphone”和“SpatialPerception”功能是否确实已启用。     </span><span class="sxs-lookup"><span data-stu-id="fb76b-141">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="fb76b-142">然后启用“InternetClientServer”和“PrivateNetworkClientServer”功能：  </span><span class="sxs-lookup"><span data-stu-id="fb76b-142">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="fb76b-144">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="fb76b-144">Importing the tutorial assets</span></span>

<span data-ttu-id="fb76b-145">下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：</span><span class="sxs-lookup"><span data-stu-id="fb76b-145">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="fb76b-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage)（最新版本）</span><span class="sxs-lookup"><span data-stu-id="fb76b-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="fb76b-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="fb76b-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="fb76b-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="fb76b-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="fb76b-149">有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)中的说明。</span><span class="sxs-lookup"><span data-stu-id="fb76b-149">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="fb76b-150">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="fb76b-150">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="fb76b-152">准备场景</span><span class="sxs-lookup"><span data-stu-id="fb76b-152">Preparing the scene</span></span>

<span data-ttu-id="fb76b-153">在本部分，你将通过添加教程预制件来准备场景，并配置“Lunarcom 控制器(脚本)”组件来控制场景。</span><span class="sxs-lookup"><span data-stu-id="fb76b-153">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="fb76b-154">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpeechServices” > “预制件”文件夹，并将“Lunarcom”预制件拖放到“层次结构”窗口中，以将其添加到场景中：    </span><span class="sxs-lookup"><span data-stu-id="fb76b-154">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="fb76b-156">仍在“层次结构”窗口中选中了“Lunarcom”对象的情况下，在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 控制器(脚本)”组件添加到 Lunarcom 对象中：   </span><span class="sxs-lookup"><span data-stu-id="fb76b-156">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="fb76b-158">MRTK 中未包含“Lunarcom 控制器(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="fb76b-158">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="fb76b-159">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="fb76b-159">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="fb76b-160">在仍选中了“Lunarcom”对象的情况下，将其展开以显示其子对象，然后将“Terminal”对象拖放到“Lunarcom 控制器(脚本)”组件的“终端”字段中：   </span><span class="sxs-lookup"><span data-stu-id="fb76b-160">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="fb76b-162">在仍选中了“Lunarcom”对象的情况下，展开 Terminal 对象以显示其子对象，然后将“ConnectionLight”对象拖放到“Lunarcom 控制器(脚本)”组件的“连接光线”字段中，并将“OutputText”对象拖放到“输出文本”字段中：     </span><span class="sxs-lookup"><span data-stu-id="fb76b-162">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="fb76b-164">在仍选中了“Lunarcom”对象的情况下，展开 Buttons 对象以显示其子对象，然后在“检查器”窗口中展开“按钮”列表，将其“大小”设置为 3，并将“MicButton”、“SatelliteButton”和“RocketButton”对象分别拖放到“元素 0”、“元素 1”和“元素 2”字段中：       </span><span class="sxs-lookup"><span data-stu-id="fb76b-164">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="fb76b-166">将 Unity 项目连接到 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="fb76b-166">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="fb76b-167">若要使用 Azure 语音服务，需要创建一个 Azure 资源并获取语音服务的 API 密钥。</span><span class="sxs-lookup"><span data-stu-id="fb76b-167">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="fb76b-168">按照“[免费试用语音服务](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)”中的说明进行操作，并记下服务区域（也称为“位置”）和 API 密钥（也称为“密钥 1”或“密钥 2”）。</span><span class="sxs-lookup"><span data-stu-id="fb76b-168">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="fb76b-169">在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中找到“Lunarcom 控制器(脚本)”组件的“语音 SDK 凭据”部分，并按如下所述对其进行配置：   </span><span class="sxs-lookup"><span data-stu-id="fb76b-169">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="fb76b-170">在“语音服务 API 密钥”字段中，输入你的 API 密钥（“密钥 1”或“密钥 2”） </span><span class="sxs-lookup"><span data-stu-id="fb76b-170">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="fb76b-171">在“语音服务区域”字段中，使用小写字母输入不带空格的服务区域（位置） </span><span class="sxs-lookup"><span data-stu-id="fb76b-171">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="fb76b-173">使用语音识别听录语音</span><span class="sxs-lookup"><span data-stu-id="fb76b-173">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="fb76b-174">在“层次结构”窗口中选择“Lunarcom”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“Lunarcom 语音识别器(脚本)”组件添加到 Lunarcom 对象中：   </span><span class="sxs-lookup"><span data-stu-id="fb76b-174">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="fb76b-176">MRTK 中未包含“Lunarcom 语音识别器(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="fb76b-176">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="fb76b-177">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="fb76b-177">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="fb76b-178">如果现在进入“游戏”模式，可以先按麦克风按钮来测试语音识别：</span><span class="sxs-lookup"><span data-stu-id="fb76b-178">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="fb76b-180">假设计算机上配备了麦克风，当你讲话时，会在终端面板上听录你的语音：</span><span class="sxs-lookup"><span data-stu-id="fb76b-180">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="fb76b-182">应用程序需要连接到 Azure，因此请确保计算机/设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="fb76b-182">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="fb76b-183">祝贺</span><span class="sxs-lookup"><span data-stu-id="fb76b-183">Congratulations</span></span>

<span data-ttu-id="fb76b-184">现已实现了由 Azure 提供支持的语音识别。</span><span class="sxs-lookup"><span data-stu-id="fb76b-184">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="fb76b-185">请在设备上运行该应用程序，以确保功能正常。</span><span class="sxs-lookup"><span data-stu-id="fb76b-185">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="fb76b-186">下一篇教程将介绍如何使用 Azure 语音识别执行命令。</span><span class="sxs-lookup"><span data-stu-id="fb76b-186">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

[<span data-ttu-id="fb76b-187">下一教程：2.使用语音识别执行命令</span><span class="sxs-lookup"><span data-stu-id="fb76b-187">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
