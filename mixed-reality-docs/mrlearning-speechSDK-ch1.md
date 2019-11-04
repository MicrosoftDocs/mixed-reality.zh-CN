---
title: Azure Speech Services 教程-1。 集成和使用语音识别与脚本
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 4baef90f8e00e5da1063c708ae24d2057e0dc227
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438373"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="c1e99-105">1. 集成和使用语音识别与脚本</span><span class="sxs-lookup"><span data-stu-id="c1e99-105">1. Integrating and using speech recognition and transcription</span></span>

<span data-ttu-id="c1e99-106">本教程将创建一个混合现实应用程序，该应用程序探讨如何将 Azure 认知服务语音 SDK 与 HoloLens 2 一起使用。</span><span class="sxs-lookup"><span data-stu-id="c1e99-106">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="c1e99-107">完成本系列教程后，你将能够使用设备的麦克风实时将语音转录到文本，将语音翻译成其他语言，并利用语音 SDK 的意图功能理解语音命令人工智能。</span><span class="sxs-lookup"><span data-stu-id="c1e99-107">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="c1e99-108">目标</span><span class="sxs-lookup"><span data-stu-id="c1e99-108">Objectives</span></span>

- <span data-ttu-id="c1e99-109">了解如何将 Azure Speech SDK 集成到 HoloLens 2 应用程序</span><span class="sxs-lookup"><span data-stu-id="c1e99-109">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="c1e99-110">了解如何使用语音命令</span><span class="sxs-lookup"><span data-stu-id="c1e99-110">Learn how to use voice commands</span></span>
- <span data-ttu-id="c1e99-111">了解如何使用语音到文本功能</span><span class="sxs-lookup"><span data-stu-id="c1e99-111">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="c1e99-112">说明</span><span class="sxs-lookup"><span data-stu-id="c1e99-112">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="c1e99-113">入门</span><span class="sxs-lookup"><span data-stu-id="c1e99-113">Getting Started</span></span>

1. <span data-ttu-id="c1e99-114">启动 Unity，并创建一个新项目。</span><span class="sxs-lookup"><span data-stu-id="c1e99-114">Start Unity, and create a new project.</span></span> <span data-ttu-id="c1e99-115">输入项目名称语音 SDK 学习模块。</span><span class="sxs-lookup"><span data-stu-id="c1e99-115">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="c1e99-116">选择保存项目的位置。</span><span class="sxs-lookup"><span data-stu-id="c1e99-116">Choose a location for where to save your project.</span></span> <span data-ttu-id="c1e99-117">然后单击 "创建项目"。</span><span class="sxs-lookup"><span data-stu-id="c1e99-117">Then click Create Project.</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="c1e99-119">注意：请确保将模板设置为3D，如上图中所示。</span><span class="sxs-lookup"><span data-stu-id="c1e99-119">Note: Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="c1e99-120">下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage)Unity 包，并将其保存到电脑上的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c1e99-120">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package, and save it to a folder on your PC.</span></span> <span data-ttu-id="c1e99-121">将包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="c1e99-121">Import the package into your Unity project.</span></span> <span data-ttu-id="c1e99-122">有关如何执行此操作的详细说明，请参阅[基本模块第1课](mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="c1e99-122">For detailed instructions on how to do this, please see [Base Module Lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="c1e99-123">下载并导入用于 Unity 资产包的 Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage) 。</span><span class="sxs-lookup"><span data-stu-id="c1e99-123">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="c1e99-124">通过单击 "资产"，选择 "导入包"，然后选择 "自定义包" 来导入语音 SDK 包。</span><span class="sxs-lookup"><span data-stu-id="c1e99-124">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="c1e99-125">找到先前下载的语音 SDK 包，并打开它以开始导入过程。</span><span class="sxs-lookup"><span data-stu-id="c1e99-125">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span> 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="c1e99-128">在下一个弹出窗口中，单击 "导入" 以开始导入语音 SDK 包。</span><span class="sxs-lookup"><span data-stu-id="c1e99-128">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="c1e99-129">请确保选中所有项，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c1e99-129">Ensure all items are checked as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. <span data-ttu-id="c1e99-131">通过单击[此链接](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)，下载语音 SDK 模块资产包，也称为 Lunarcom package。</span><span class="sxs-lookup"><span data-stu-id="c1e99-131">Download the Speech SDK Module asset pack, also know as Lunarcom package by clicking on [this link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span></span> <span data-ttu-id="c1e99-132">Lunarcom 资产包是为本课系列开发的资产和脚本的集合，旨在展示 Azure 语音 SDK 的实际使用情况。</span><span class="sxs-lookup"><span data-stu-id="c1e99-132">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="c1e99-133">它是一个语音命令终端，最终将与[基本模块教程](mrlearning-base-ch6.md)中开发的农历模块组装体验进行交互。</span><span class="sxs-lookup"><span data-stu-id="c1e99-133">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>

6. <span data-ttu-id="c1e99-134">按照导入混合现实工具包和语音 SDK 所用的类似步骤，将 Lunarcom 资产包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="c1e99-134">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="c1e99-135">配置混合现实工具包（MRTK）。</span><span class="sxs-lookup"><span data-stu-id="c1e99-135">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="c1e99-136">为此，请在窗口顶部单击 "混合现实工具包" 面板，然后选择 "添加到场景" 并配置。</span><span class="sxs-lookup"><span data-stu-id="c1e99-136">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. <span data-ttu-id="c1e99-140">你的场景现在有多个 MRTK 中的新项。</span><span class="sxs-lookup"><span data-stu-id="c1e99-140">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="c1e99-141">单击 "文件"，然后单击 "另存为"，然后将场景命名为 "SpeechScene"，以其他名称保存场景。</span><span class="sxs-lookup"><span data-stu-id="c1e99-141">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span> 

> <span data-ttu-id="c1e99-142">注意：如果在将 MRTK 添加到项目中后按下了场景，但不进入播放模式，则可能需要重新启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="c1e99-142">Note: If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span> 

9. <span data-ttu-id="c1e99-143">在层次结构中选择 MixedRealityToolkit 对象后，单击 "检查器" 面板中的 "复制" 和 "自定义"。</span><span class="sxs-lookup"><span data-stu-id="c1e99-143">With the MixedRealityToolkit object selected in your hierarchy, click Copy and Customize in the Inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="c1e99-145">同时，在 "检查器" 面板（在层次结构中选择 MixedRealityToolkit 对象）中，通过取消选中 "启用诊断系统" 右侧的框来禁用诊断系统。</span><span class="sxs-lookup"><span data-stu-id="c1e99-145">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. <span data-ttu-id="c1e99-147">若要启用语音命令，请选择要自定义的新创建的 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="c1e99-147">To enable voice commands, select the newly created MRTK profile to customize.</span></span> <span data-ttu-id="c1e99-148">在本教程中，我们将使用用于语音识别和脚本的输入语音命令。</span><span class="sxs-lookup"><span data-stu-id="c1e99-148">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="c1e99-149">允许克隆输入配置文件以更改语音设置。</span><span class="sxs-lookup"><span data-stu-id="c1e99-149">Lets clone the input profile to make changes to speech settings.</span></span>

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. <span data-ttu-id="c1e99-152">克隆输入配置文件后，请转到语音命令并克隆语音命令。</span><span class="sxs-lookup"><span data-stu-id="c1e99-152">Once the input profile is cloned, go to speech commands and clone the speech commands.</span></span>

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. <span data-ttu-id="c1e99-155">现在，在 "语音命令" 下，转到 "常规设置"，并将 "启动行为" 设置为 "手动启动"</span><span class="sxs-lookup"><span data-stu-id="c1e99-155">Now under speech commands, go to "General Settings" and set "Start Behavior" to "Manual Start"</span></span>

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. <span data-ttu-id="c1e99-157">在 "项目" 面板中，展开 "Lunarcom" 文件夹，然后将 "Lunarcom_Base" prefab 拖到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="c1e99-157">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. <span data-ttu-id="c1e99-159">选择层次结构中的 Lunarcom_Base 对象，并确保将位置设置为 x = 0、y = 0、z = 0，以及将旋转设置为 x = 0、y = 0 和 z = 0。</span><span class="sxs-lookup"><span data-stu-id="c1e99-159">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="c1e99-160">将刻度设置为 read x = 0.008，y = 0.008，z = 0.01。</span><span class="sxs-lookup"><span data-stu-id="c1e99-160">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="c1e99-162">单击 "添加组件"，搜索并选择 "LunarcomController"。</span><span class="sxs-lookup"><span data-stu-id="c1e99-162">Click Add Component, and search for and select LunarcomController.</span></span> <span data-ttu-id="c1e99-163">此脚本包含在步骤6中导入的 Lunarcom 资产包中。</span><span class="sxs-lookup"><span data-stu-id="c1e99-163">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="c1e99-165">若要将应用程序连接到 Azure 认知服务，必须为语音服务输入订阅密钥（也称为 API 密钥）。</span><span class="sxs-lookup"><span data-stu-id="c1e99-165">To connect our applicaiton to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="c1e99-166">按照[此处](https://docs.microsoft.com//azure/cognitive-services/speech-service/get-started)的说明获取免费订阅密钥。</span><span class="sxs-lookup"><span data-stu-id="c1e99-166">Follow the instructions at [here](https://docs.microsoft.com//azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="c1e99-167">获取订阅密钥后，请在 "检查器" 面板中的 LunarcomController 组件的 "语音服务 API 密钥" 字段中输入该密钥，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c1e99-167">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

18. <span data-ttu-id="c1e99-168">将订阅密钥注册到 "检查器" 面板中 LunarcomController 组件的 "语音服务区域" 字段时，请输入所选的区域。</span><span class="sxs-lookup"><span data-stu-id="c1e99-168">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="c1e99-169">例如，对于区域 "美国西部"，键入 "westus"</span><span class="sxs-lookup"><span data-stu-id="c1e99-169">For example, for the region "West US" type in "westus"</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="c1e99-171">在层次结构中，单击 "Lunarcom_Base" 对象左侧的箭头将其展开。</span><span class="sxs-lookup"><span data-stu-id="c1e99-171">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="c1e99-172">然后对其子对象 "终端" 执行相同的操作，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c1e99-172">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="c1e99-173">选择 Lunarcom_Base 时，在 "检查器" 面板中单击 "Lunarcom 文本" 并将其拖到 "LunarcomController" 组件中的 "输出文本" 槽，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="c1e99-173">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

21. <span data-ttu-id="c1e99-174">对终端槽执行相同的操作，并对连接轻型控制器槽执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="c1e99-174">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="c1e99-176">单击 "检查器" 面板中 "LunarcomController" 脚本的 "Lunarcom 按钮" 部分旁边的箭头，将大小更改为3。</span><span class="sxs-lookup"><span data-stu-id="c1e99-176">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="c1e99-177">按 Enter 或 Return。</span><span class="sxs-lookup"><span data-stu-id="c1e99-177">Press Enter or Return.</span></span> <span data-ttu-id="c1e99-178">这将导致显示三个新元素字段。</span><span class="sxs-lookup"><span data-stu-id="c1e99-178">This causes three new Element fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="c1e99-180">在层次结构中单击其旁边的箭头，展开 "Lunarcom" 按钮，并使用上述相同过程，分别将 Mic、卫星和火箭 gameobject 拖到元素0、1和2引用，并在检查器面板。</span><span class="sxs-lookup"><span data-stu-id="c1e99-180">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="c1e99-182">在层次结构中选择 "Lunarcom_Base" 对象。</span><span class="sxs-lookup"><span data-stu-id="c1e99-182">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="c1e99-183">单击 "检查器" 面板中的 "添加组件"，搜索并选择 "LunarcomWakeWordRecognizer"。</span><span class="sxs-lookup"><span data-stu-id="c1e99-183">Click Add Component in the inspector panel, and search for and select LunarcomWakeWordRecognizer.</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="c1e99-185">在 "唤醒单词" 槽中，键入 "激活终端"。</span><span class="sxs-lookup"><span data-stu-id="c1e99-185">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="c1e99-186">在 "消除字" 槽中，键入 "消除终端"。</span><span class="sxs-lookup"><span data-stu-id="c1e99-186">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a><span data-ttu-id="c1e99-188">在设备上构建应用程序</span><span class="sxs-lookup"><span data-stu-id="c1e99-188">Build your application to your device</span></span>

1. <span data-ttu-id="c1e99-189">转到 "文件 > 生成设置"，再次打开 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="c1e99-189">Open the build settings window again by going to File>Build Settings.</span></span>

![学习 Chapter5 步骤1](images/Lesson1Chapter5Step1.JPG)

2. <span data-ttu-id="c1e99-191">通过单击“添加打开的场景”按钮，确保要尝试的场景位于“生成中的场景”列表中。</span><span class="sxs-lookup"><span data-stu-id="c1e99-191">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>
3. <span data-ttu-id="c1e99-192">按 "播放机设置" 按钮，并单击 "发布设置"。</span><span class="sxs-lookup"><span data-stu-id="c1e99-192">Press the Player Settings button and go to Publishing Settings.</span></span> <span data-ttu-id="c1e99-193">在 "功能" 下，启用： Internet、Internet 客户端服务器、专用网络客户端服务器、麦克风和空间感知。</span><span class="sxs-lookup"><span data-stu-id="c1e99-193">Under Capabilities, enable: Internet, Internet Client Server, Private Network Client Server, Microphone and Spatial Perception.</span></span>
4. <span data-ttu-id="c1e99-194">在相同的播放机设置中，选择 "XR 设置"，并选择 "支持的虚拟现实"。</span><span class="sxs-lookup"><span data-stu-id="c1e99-194">In the same Player Settings, go to XR settings  and select the Virtual Reality Supported to ON.</span></span>
5. <span data-ttu-id="c1e99-195">按“生成”按钮开始生成过程。</span><span class="sxs-lookup"><span data-stu-id="c1e99-195">Press the Build button to begin the build process.</span></span>

![学习 Chapter5 步骤3](images/Lesson1Chapter5Step3.JPG)

6. <span data-ttu-id="c1e99-197">为应用程序创建一个新文件夹并为其命名。</span><span class="sxs-lookup"><span data-stu-id="c1e99-197">Create and name a new folder for your application.</span></span> <span data-ttu-id="c1e99-198">在下图中，创建了一个名为“应用”的文件夹以包含该应用程序。</span><span class="sxs-lookup"><span data-stu-id="c1e99-198">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="c1e99-199">单击“选择文件夹”，开始生成新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c1e99-199">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="c1e99-200">生成完成后，可以关闭 Unity 中的“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="c1e99-200">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 

![学习 Chapter5 步骤4](images/Lesson1Chapter5Step4.JPG)

> <span data-ttu-id="c1e99-202">注意：如果生成失败，请尝试重新生成或重新启动 Unity 并再次生成。</span><span class="sxs-lookup"><span data-stu-id="c1e99-202">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="c1e99-203">如果你看到错误，如 "错误： CS0246 = 无法找到类型或命名空间名称" XX "（是否缺少 using 指令或程序集引用？）"，则你可能需要安装[Windows 10 SDK （10.0.18362.0）](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="c1e99-203">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>)</span></span>

7. <span data-ttu-id="c1e99-204">生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c1e99-204">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="c1e99-205">双击 ".sln" 解决方案文件，在 Visual Studio 中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="c1e99-205">Double click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

> <span data-ttu-id="c1e99-206">注意：请确保打开新创建的文件夹（例如，如果遵循前面步骤中的命名约定，则为 "App" 文件夹），因为在该文件夹之外，不会与 build 文件夹内的 .sln 文件混淆。</span><span class="sxs-lookup"><span data-stu-id="c1e99-206">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![第 1 课 第 5 章 第 5 步](images/Lesson1Chapter5Step5.JPG)

> <span data-ttu-id="c1e99-208">注意：如果 Visual Studio 要求你安装新组件，请花点时间确保按["安装工具" 页中的](install-the-tools.md)指定安装所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="c1e99-208">Note: If Visual Studio asks you to install new components, please take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

8. <span data-ttu-id="c1e99-209">使用 USB 电缆将 HoloLens 2 插入电脑。</span><span class="sxs-lookup"><span data-stu-id="c1e99-209">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="c1e99-210">虽然这些课程说明假设你将使用 HoloLens 2 设备部署测试，但你也可以选择部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或选择创建[应用包以进行旁加载](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="c1e99-210">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>
9. <span data-ttu-id="c1e99-211">在生成到设备之前，请确保设备处于开发者模式。</span><span class="sxs-lookup"><span data-stu-id="c1e99-211">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="c1e99-212">如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。</span><span class="sxs-lookup"><span data-stu-id="c1e99-212">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="c1e99-213">如果需要启用开发者模式或与 Visual Studio 配对，请按照[这些说明](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio)进行操作。</span><span class="sxs-lookup"><span data-stu-id="c1e99-213">Please follow [these instructions](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

10. <span data-ttu-id="c1e99-214">通过选择“发布”配置和“ARM”体系结构，配置 Visual Studio 以生成到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="c1e99-214">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

![学习 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

11. <span data-ttu-id="c1e99-216">最后一步是通过选择“调试”>“在不调试的情况下启动”来生成到你的设备。</span><span class="sxs-lookup"><span data-stu-id="c1e99-216">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="c1e99-217">选择“在不调试的情况下启动”将导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中显示调试信息。</span><span class="sxs-lookup"><span data-stu-id="c1e99-217">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="c1e99-218">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="c1e99-218">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="c1e99-219">也可以选择“生成”>“部署解决方案”以部署到你的设备，而无需自动启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="c1e99-219">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

![学习 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a><span data-ttu-id="c1e99-221">祝贺</span><span class="sxs-lookup"><span data-stu-id="c1e99-221">Congratulations</span></span>

<span data-ttu-id="c1e99-222">你已在应用程序中设置了语音识别，由 Azure 提供支持。</span><span class="sxs-lookup"><span data-stu-id="c1e99-222">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="c1e99-223">运行应用程序以确保所有功能和功能都正常工作。</span><span class="sxs-lookup"><span data-stu-id="c1e99-223">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="c1e99-224">首先说到你在步骤22中键入的唤醒字词，然后激活终端。</span><span class="sxs-lookup"><span data-stu-id="c1e99-224">Start with saying the wake word you typed in Step 22, Activate Terminal.</span></span> <span data-ttu-id="c1e99-225">选择麦克风按钮启动语音识别。</span><span class="sxs-lookup"><span data-stu-id="c1e99-225">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="c1e99-226">开始说话。</span><span class="sxs-lookup"><span data-stu-id="c1e99-226">Begin speaking.</span></span> <span data-ttu-id="c1e99-227">你会在说话时看到你的转录。</span><span class="sxs-lookup"><span data-stu-id="c1e99-227">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="c1e99-228">再次按下麦克风按钮以停止语音识别。</span><span class="sxs-lookup"><span data-stu-id="c1e99-228">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="c1e99-229">说关闭终端，隐藏 Lunarcom 终端。</span><span class="sxs-lookup"><span data-stu-id="c1e99-229">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="c1e99-230">在下一课中，我们将学习如何在 Azure 语音 SDK 由于 HoloLens 2 处于脱机状态而无法使用的情况下动态切换到使用设备支持的语音识别。</span><span class="sxs-lookup"><span data-stu-id="c1e99-230">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="c1e99-231">下一教程： 2. 为本地语音到文本转换添加脱机模式</span><span class="sxs-lookup"><span data-stu-id="c1e99-231">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)

