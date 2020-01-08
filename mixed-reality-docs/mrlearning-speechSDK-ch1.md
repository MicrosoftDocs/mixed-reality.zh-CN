---
title: Azure Speech Services 教程-1。 集成和使用语音识别与脚本
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 05728cf090b2e998e92980816943a2c3bef18dfb
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334290"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="2451a-105">1. 集成和使用语音识别与脚本</span><span class="sxs-lookup"><span data-stu-id="2451a-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="2451a-106">概述</span><span class="sxs-lookup"><span data-stu-id="2451a-106">Overview</span></span>

<span data-ttu-id="2451a-107">本教程将创建一个混合现实应用程序，该应用程序探讨如何将 Azure 认知服务语音 SDK 与 HoloLens 2 一起使用。</span><span class="sxs-lookup"><span data-stu-id="2451a-107">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="2451a-108">完成本系列教程后，你将能够使用设备的麦克风实时转录语音，将语音翻译成其他语言，并利用语音 SDK 的意图功能来理解使用化.</span><span class="sxs-lookup"><span data-stu-id="2451a-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="2451a-109">目标</span><span class="sxs-lookup"><span data-stu-id="2451a-109">Objectives</span></span>

* <span data-ttu-id="2451a-110">了解如何将 Azure Speech SDK 集成到 HoloLens 2 应用程序</span><span class="sxs-lookup"><span data-stu-id="2451a-110">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
* <span data-ttu-id="2451a-111">了解如何使用语音命令</span><span class="sxs-lookup"><span data-stu-id="2451a-111">Learn how to use voice commands</span></span>
* <span data-ttu-id="2451a-112">了解如何使用语音到文本功能</span><span class="sxs-lookup"><span data-stu-id="2451a-112">Learn how to use speech-to-text capabilities</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2451a-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="2451a-113">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="2451a-114">如果尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。</span><span class="sxs-lookup"><span data-stu-id="2451a-114">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="2451a-115">使用安装了正确的[工具](install-the-tools.md)配置的 WINDOWS 10 电脑</span><span class="sxs-lookup"><span data-stu-id="2451a-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="2451a-116">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="2451a-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="2451a-117">一些基本C#编程功能</span><span class="sxs-lookup"><span data-stu-id="2451a-117">Some basic C# programming ability</span></span>
* <span data-ttu-id="2451a-118">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="2451a-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
><span data-ttu-id="2451a-119">本系列教程需要<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a> ，建议的版本是 unity 2019.1.14。</span><span class="sxs-lookup"><span data-stu-id="2451a-119">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="2451a-120">这将取代上述先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="2451a-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="getting-started"></a><span data-ttu-id="2451a-121">入门</span><span class="sxs-lookup"><span data-stu-id="2451a-121">Getting Started</span></span>

1. <span data-ttu-id="2451a-122">启动 Unity，并创建一个新项目。</span><span class="sxs-lookup"><span data-stu-id="2451a-122">Start Unity, and create a new project.</span></span> <span data-ttu-id="2451a-123">输入项目名称语音 SDK 学习模块。</span><span class="sxs-lookup"><span data-stu-id="2451a-123">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="2451a-124">选择保存项目的位置。</span><span class="sxs-lookup"><span data-stu-id="2451a-124">Choose a location for where to save your project.</span></span> <span data-ttu-id="2451a-125">单击 "创建项目"。</span><span class="sxs-lookup"><span data-stu-id="2451a-125">Click Create Project.</span></span>

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    ><span data-ttu-id="2451a-127">请确保将模板设置为 "三维"，如上图所示。</span><span class="sxs-lookup"><span data-stu-id="2451a-127">Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="2451a-128">下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation 包版本 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) 并将其保存到电脑上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2451a-128">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) and save it to a folder on your PC.</span></span> <span data-ttu-id="2451a-129">将包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="2451a-129">Import the package into your Unity project.</span></span> <span data-ttu-id="2451a-130">有关如何执行此操作的详细说明，请参阅[入门教程-第2课。正在初始化项目和首个应用程序](mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="2451a-130">For detailed instructions on how to do this, see the [Getting started tutorials - Lesson 2. Initializing your project and first application](mrlearning-base-ch1.md).</span></span>

3. <span data-ttu-id="2451a-131">下载并导入用于 Unity 资产包的 Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage) 。</span><span class="sxs-lookup"><span data-stu-id="2451a-131">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="2451a-132">通过单击 "资产"，选择 "导入包"，然后选择 "自定义包" 来导入语音 SDK 包。</span><span class="sxs-lookup"><span data-stu-id="2451a-132">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="2451a-133">找到先前下载的语音 SDK 包，并打开它以开始导入过程。</span><span class="sxs-lookup"><span data-stu-id="2451a-133">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span>

    ![mrlearning-speech-ch1-1-step3a .png](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-speech-ch1-1-step3b .png](images/mrlearning-speech-ch1-1-step3b.png)

4. <span data-ttu-id="2451a-136">在下一个弹出窗口中，单击 "导入" 以开始导入语音 SDK 包。</span><span class="sxs-lookup"><span data-stu-id="2451a-136">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="2451a-137">确保选中所有项，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="2451a-137">Ensure all items are checked, as shown in the image below.</span></span>

    ![mrlearning-speech-ch1-1-step4 .png](images/mrlearning-speech-ch1-1-step4.png)

5. <span data-ttu-id="2451a-139">单击[此链接](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)，下载语音 SDK 模块资产包（也称为 Lunarcom 包）。</span><span class="sxs-lookup"><span data-stu-id="2451a-139">Download the Speech SDK Module asset pack, also known as the Lunarcom package, by clicking on [this link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span></span> <span data-ttu-id="2451a-140">Lunarcom 资产包是为本课系列开发的资产和脚本的集合，旨在展示 Azure 语音 SDK 的实际使用情况。</span><span class="sxs-lookup"><span data-stu-id="2451a-140">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="2451a-141">它是一个语音命令终端，最终将与[入门教程-第7课中开发的农历模块组装体验进行交互。创建农历模块示例应用程序](mrlearning-base-ch6.md)。</span><span class="sxs-lookup"><span data-stu-id="2451a-141">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Getting started tutorials - Lesson 7. Creating a Lunar Module sample application](mrlearning-base-ch6.md).</span></span>

6. <span data-ttu-id="2451a-142">按照导入混合现实工具包和语音 SDK 所用的类似步骤，将 Lunarcom 资产包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="2451a-142">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>

7. <span data-ttu-id="2451a-143">配置混合现实工具包（MRTK）。</span><span class="sxs-lookup"><span data-stu-id="2451a-143">Configure the Mixed Reality Toolkit (MRTK).</span></span>

    <span data-ttu-id="2451a-144">为此，请在窗口顶部单击 "混合现实工具包" 面板，然后选择 "添加到场景" 并配置。</span><span class="sxs-lookup"><span data-stu-id="2451a-144">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

    ![mrlearning-speech-ch1-1-step7a .png](images/mrlearning-speech-ch1-1-step7a.png)

    <span data-ttu-id="2451a-146">在出现的弹出窗口中，选择 "DefaultHoloLens2ConfigurationProfile" 以使其成为混合现实工具包的活动配置文件。</span><span class="sxs-lookup"><span data-stu-id="2451a-146">In the popup that appears, select DefaultHoloLens2ConfigurationProfile to make it the Active Profile for the Mixed Reality Toolkit.</span></span>

    ![mrlearning-speech-ch1-1-step7b .png](images/mrlearning-speech-ch1-1-step7b.png)

8. <span data-ttu-id="2451a-148">你的场景现在有多个 MRTK 中的新项。</span><span class="sxs-lookup"><span data-stu-id="2451a-148">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="2451a-149">单击 "文件"，然后单击 "另存为"，然后将场景命名为 "SpeechScene"，以其他名称保存场景。</span><span class="sxs-lookup"><span data-stu-id="2451a-149">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2451a-150">如果在将 MRTK 添加到项目中后按下了场景，而不进入播放模式，则可能需要重新启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="2451a-150">If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span>

9. <span data-ttu-id="2451a-151">在场景层次结构中选择 MixedRealityToolkit 对象后，单击 "检查器" 面板中的 "复制 & 自定义"，以打开 "克隆配置文件" 弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="2451a-151">With the MixedRealityToolkit object selected in your scene hierarchy, click Copy & Customize in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="2451a-152">在 "克隆配置文件" 弹出窗口中，为自定义配置文件输入合适的名称，例如 "自定义 HoloLens2ConfigurationProfile"。</span><span class="sxs-lookup"><span data-stu-id="2451a-152">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2ConfigurationProfile.</span></span> <span data-ttu-id="2451a-153">单击 "克隆" 创建自定义配置文件，并将其设置为活动配置文件。</span><span class="sxs-lookup"><span data-stu-id="2451a-153">Click Clone to create your custom configuration profile and set it as the active profile.</span></span>

    ![mrlearning-speech-ch1-1-step9 .png](images/mrlearning-speech-ch1-1-step9.png)

10. <span data-ttu-id="2451a-155">同时，在 "检查器" 面板（在层次结构中选择 MixedRealityToolkit 对象）中，通过取消选中 "启用诊断系统" 右侧的框来禁用诊断系统。</span><span class="sxs-lookup"><span data-stu-id="2451a-155">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

    ![mrlearning-speech-ch1-1-step10 .png](images/mrlearning-speech-ch1-1-step10.png)

11. <span data-ttu-id="2451a-157">在本教程中，我们将使用用于语音识别和脚本的输入语音命令。</span><span class="sxs-lookup"><span data-stu-id="2451a-157">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="2451a-158">我们会克隆输入配置文件，以更改语音设置。</span><span class="sxs-lookup"><span data-stu-id="2451a-158">Let's clone the input profile to make changes to speech settings.</span></span>

    <span data-ttu-id="2451a-159">在场景层次结构中，MixedRealityToolkit 对象仍处于选中状态，单击 "检查器" 面板中的 "小型克隆" 按钮，打开克隆配置文件弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="2451a-159">With the MixedRealityToolkit object still selected in your scene hierarchy, click the small Clone button in the Inspector panel to open the Clone Profile popup.</span></span> <span data-ttu-id="2451a-160">在 "克隆配置文件" 弹出窗口中，为自定义配置文件输入合适的名称，例如 "自定义 HoloLens2InputSystemProfile"，然后单击 "克隆" 以创建自定义输入系统配置文件，并将其设置为活动配置文件。</span><span class="sxs-lookup"><span data-stu-id="2451a-160">In the Clone Profile popup, enter a suitable name for your custom profile, for example, Custom HoloLens2InputSystemProfile, and then click Clone to create your custom input system profile and set it as the active profile.</span></span>

    ![mrlearning-speech-ch1-1-step11 .png](images/mrlearning-speech-ch1-1-step11.png)

12. <span data-ttu-id="2451a-162">克隆输入配置文件后，展开 "语音" 部分并按照上一步骤中所述的相同过程来克隆语音命令配置文件。</span><span class="sxs-lookup"><span data-stu-id="2451a-162">Once the input profile is cloned, expand the Speech section and follow the same process as in the previous step to clone the speech commands profile.</span></span>

    ![mrlearning-speech-ch1-1-step12 .png](images/mrlearning-speech-ch1-1-step12.png)

13. <span data-ttu-id="2451a-164">在语音部分下，转到 "常规设置"，并将 "开始行为" 更改为手动启动。</span><span class="sxs-lookup"><span data-stu-id="2451a-164">Under the Speech section, go to General Settings and change Start Behavior to Manual Start.</span></span>

    ![mrlearning-speech-ch1-1-step13 .png](images/mrlearning-speech-ch1-1-step13.png)

14. <span data-ttu-id="2451a-166">在 "项目" 面板中，展开 "Lunarcom" 文件夹并将 Lunarcom_Base "prefab" 拖动到场景层次结构。</span><span class="sxs-lookup"><span data-stu-id="2451a-166">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your scene hierarchy.</span></span>

    ![mrlearning-speech-ch1-1-step14 .png](images/mrlearning-speech-ch1-1-step14.png)

15. <span data-ttu-id="2451a-168">选择层次结构中的 Lunarcom_Base 对象，并确保将位置设置为 x = 0、y = 0、z = 0，以及将旋转设置为 x = 0、y = 0 和 z = 0。</span><span class="sxs-lookup"><span data-stu-id="2451a-168">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="2451a-169">将刻度设置为 read x = 0.008，y = 0.008，z = 0.01。</span><span class="sxs-lookup"><span data-stu-id="2451a-169">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="2451a-171">单击 "添加组件"，搜索并选择 "Lunarcom 控制器"。</span><span class="sxs-lookup"><span data-stu-id="2451a-171">Click Add Component, and search for and select Lunarcom Controller.</span></span> <span data-ttu-id="2451a-172">此脚本包含在步骤6中导入的 Lunarcom 资产包中。</span><span class="sxs-lookup"><span data-stu-id="2451a-172">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="2451a-174">若要将应用程序连接到 Azure 认知服务，必须为语音服务输入订阅密钥（也称为 API 密钥）。</span><span class="sxs-lookup"><span data-stu-id="2451a-174">To connect our application to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="2451a-175">按照[此处](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)的说明获取免费订阅密钥。</span><span class="sxs-lookup"><span data-stu-id="2451a-175">Follow the instructions at [here](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="2451a-176">获取订阅密钥后，请在 "检查器" 面板中的 LunarcomController 组件的 "语音服务 API 密钥" 字段中输入该密钥，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="2451a-176">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel, as shown in the image below.</span></span>

18. <span data-ttu-id="2451a-177">将订阅密钥注册到 "检查器" 面板中 LunarcomController 组件的 "语音服务区域" 字段时，请输入所选的区域。</span><span class="sxs-lookup"><span data-stu-id="2451a-177">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="2451a-178">例如，对于美国西部，请在 "westus" 中键入。</span><span class="sxs-lookup"><span data-stu-id="2451a-178">For example, for the region West US type in "westus".</span></span>

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="2451a-180">在层次结构中，通过单击其左侧的箭头展开 "Lunarcom_Base" 对象。</span><span class="sxs-lookup"><span data-stu-id="2451a-180">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="2451a-181">然后对其子对象 "终端" 执行相同的操作，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="2451a-181">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="2451a-182">选择 Lunarcom_Base 时，请在 "检查器" 面板中单击 "Lunarcom"，并将其从层次结构拖到 "LunarcomController" 组件中的 "输出文本" 槽，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="2451a-182">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel, as shown in the image below.</span></span>

21. <span data-ttu-id="2451a-183">对终端槽执行相同的操作，并对连接轻型控制器槽执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="2451a-183">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="2451a-185">单击 "检查器" 面板中 "LunarcomController" 脚本的 "Lunarcom 按钮" 部分旁边的箭头，将大小更改为3。</span><span class="sxs-lookup"><span data-stu-id="2451a-185">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="2451a-186">按 Enter 或 Return。</span><span class="sxs-lookup"><span data-stu-id="2451a-186">Press Enter or Return.</span></span> <span data-ttu-id="2451a-187">这将导致显示三个新元素字段。</span><span class="sxs-lookup"><span data-stu-id="2451a-187">This causes three new Element fields to appear.</span></span>

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="2451a-189">在层次结构中单击其旁边的箭头，展开 "Lunarcom" 按钮，并使用上述相同过程，分别将 Mic、卫星和火箭 gameobject 拖到元素0、1和2引用，并在检查器面板。</span><span class="sxs-lookup"><span data-stu-id="2451a-189">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="2451a-191">选择层次结构中的 Lunarcom_Base "对象。</span><span class="sxs-lookup"><span data-stu-id="2451a-191">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="2451a-192">单击 "检查器" 面板中的 "添加组件"，搜索并选择 Lunarcom 语音识别器。</span><span class="sxs-lookup"><span data-stu-id="2451a-192">Click Add Component in the inspector panel and search for and select Lunarcom Speech Recognizer.</span></span> <span data-ttu-id="2451a-193">重复相同的步骤添加 Lunarcom 唤醒词识别器。</span><span class="sxs-lookup"><span data-stu-id="2451a-193">Repeat the same steps to add Lunarcom Wake Word Recognizer.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="2451a-195">在 "唤醒单词" 槽中，键入 "激活终端"。</span><span class="sxs-lookup"><span data-stu-id="2451a-195">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="2451a-196">在 "消除字" 槽中，键入 "消除终端"。</span><span class="sxs-lookup"><span data-stu-id="2451a-196">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="2451a-198">在设备上构建应用程序</span><span class="sxs-lookup"><span data-stu-id="2451a-198">Build your application to your device</span></span>

1. <span data-ttu-id="2451a-199">转到 "文件 > 生成设置"，再次打开 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="2451a-199">Open the build settings window again by going to File>Build Settings.</span></span>

    ![images/mrlearning-ch1-2-步骤1](images/mrlearning-speach-ch1-2-step1.jpg)

2. <span data-ttu-id="2451a-201">通过单击“添加打开的场景”按钮，确保要尝试的场景位于“生成中的场景”列表中。</span><span class="sxs-lookup"><span data-stu-id="2451a-201">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="2451a-202">按 "播放机设置" 按钮，并单击 "发布设置"。</span><span class="sxs-lookup"><span data-stu-id="2451a-202">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="2451a-203">在 "功能" 下，启用： Internet、Internet 客户端服务器、专用网络客户端服务器、麦克风和空间感知。</span><span class="sxs-lookup"><span data-stu-id="2451a-203">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Microphone and Spatial Perception.</span></span>

4. <span data-ttu-id="2451a-204">在相同的播放机设置中，选择 "XR 设置"，并选择 "支持的虚拟现实"。</span><span class="sxs-lookup"><span data-stu-id="2451a-204">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>

5. <span data-ttu-id="2451a-205">按“生成”按钮开始生成过程。</span><span class="sxs-lookup"><span data-stu-id="2451a-205">Press the Build button to begin the build process.</span></span>

    ![mrlearning-ch1-步骤5](images/mrlearning-speach-ch1-2-step5.jpg)

6. <span data-ttu-id="2451a-207">为应用程序创建一个新文件夹并为其命名。</span><span class="sxs-lookup"><span data-stu-id="2451a-207">Create and name a new folder for your application.</span></span> <span data-ttu-id="2451a-208">在下图中，创建了一个名为“应用”的文件夹以包含该应用程序。</span><span class="sxs-lookup"><span data-stu-id="2451a-208">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="2451a-209">单击“选择文件夹”，开始生成新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2451a-209">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="2451a-210">生成完成后，可以关闭 Unity 中的“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="2451a-210">After the build has completed, you may close the "Build Settings" window in Unity.</span></span>

    ![mrlearning-ch1-步骤6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    ><span data-ttu-id="2451a-212">如果生成失败，尝试再次生成或重启 Unity 并再次生成。</span><span class="sxs-lookup"><span data-stu-id="2451a-212">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="2451a-213">如果你看到错误，如 "错误： CS0246 = 无法找到类型或命名空间名称" XX "（是否缺少 using 指令或程序集引用？）"，你可能需要安装[Windows 10 SDK （10.0.18362.0）](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="2451a-213">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span>

7. <span data-ttu-id="2451a-214">生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2451a-214">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="2451a-215">双击 ".sln" 解决方案文件，在 Visual Studio 中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="2451a-215">Double-click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2451a-216">如果遵循前面步骤中的命名约定，则请确保打开新创建的文件夹（即 "App" 文件夹），因为该文件夹外的命名 .sln 文件与 build 文件夹内的 .sln 文件不同。</span><span class="sxs-lookup"><span data-stu-id="2451a-216">Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is different from the .sln file inside the build folder.</span></span> 

    ![mrlearning-ch1-step7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    ><span data-ttu-id="2451a-218">如果 Visual Studio 要求你安装新组件，请确保按照["安装工具" 页中的](install-the-tools.md)指定安装所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="2451a-218">If Visual Studio asks you to install new components, ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

8. <span data-ttu-id="2451a-219">使用 USB 电缆将 HoloLens 2 插入电脑。</span><span class="sxs-lookup"><span data-stu-id="2451a-219">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="2451a-220">虽然这些课程说明假设你将使用 HoloLens 2 设备部署测试，但你也可以选择部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或选择创建[应用包以进行旁加载](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="2451a-220">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

9. <span data-ttu-id="2451a-221">在生成到设备之前，请确保设备处于开发者模式。</span><span class="sxs-lookup"><span data-stu-id="2451a-221">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="2451a-222">如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。</span><span class="sxs-lookup"><span data-stu-id="2451a-222">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="2451a-223">如果需要启用开发者模式或与 Visual Studio 配对，请按照[这些说明](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)进行操作。</span><span class="sxs-lookup"><span data-stu-id="2451a-223">Please follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

10. <span data-ttu-id="2451a-224">通过选择“发布”配置和“ARM”体系结构，配置 Visual Studio 以生成到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="2451a-224">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

    ![mrlearning-ch1-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. <span data-ttu-id="2451a-226">最后一步是通过选择“调试”>“在不调试的情况下启动”来生成到你的设备。</span><span class="sxs-lookup"><span data-stu-id="2451a-226">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="2451a-227">选择“在不调试的情况下启动”将导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中显示调试信息。</span><span class="sxs-lookup"><span data-stu-id="2451a-227">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="2451a-228">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="2451a-228">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="2451a-229">也可以选择“生成”>“部署解决方案”以部署到你的设备，而无需自动启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="2451a-229">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

    ![mrlearning-ch1-step11.JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a><span data-ttu-id="2451a-231">祝贺</span><span class="sxs-lookup"><span data-stu-id="2451a-231">Congratulations</span></span>

<span data-ttu-id="2451a-232">你已在应用程序中设置了语音识别，由 Azure 提供支持。</span><span class="sxs-lookup"><span data-stu-id="2451a-232">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="2451a-233">运行应用程序以确保所有功能和功能都正常工作。</span><span class="sxs-lookup"><span data-stu-id="2451a-233">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="2451a-234">首先说到你在步骤22中键入的唤醒字词，然后激活终端。</span><span class="sxs-lookup"><span data-stu-id="2451a-234">Start with saying the wake word you typed in Step 22, Activate Terminal.</span></span> <span data-ttu-id="2451a-235">选择麦克风按钮启动语音识别。</span><span class="sxs-lookup"><span data-stu-id="2451a-235">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="2451a-236">开始说话。</span><span class="sxs-lookup"><span data-stu-id="2451a-236">Begin speaking.</span></span> <span data-ttu-id="2451a-237">你会在说话时看到你的转录。</span><span class="sxs-lookup"><span data-stu-id="2451a-237">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="2451a-238">再次按下麦克风按钮以停止语音识别。</span><span class="sxs-lookup"><span data-stu-id="2451a-238">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="2451a-239">说关闭终端，隐藏 Lunarcom 终端。</span><span class="sxs-lookup"><span data-stu-id="2451a-239">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="2451a-240">在下一课中，您将学习如何使用设备支持的语音识别来实现 Azure 语音 SDK 不可用的情况，因为 HoloLens 2 处于脱机状态。</span><span class="sxs-lookup"><span data-stu-id="2451a-240">In the next lesson, you'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="2451a-241">下一教程： 2. 为本地语音到文本转换添加脱机模式</span><span class="sxs-lookup"><span data-stu-id="2451a-241">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)
