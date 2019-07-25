---
title: MR SpeechSDK Module-语音识别和脚本
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: c1ca44ffcaa8dced988b829d9875ebe304f14a12
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460357"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="7c7ae-104">1.集成和使用语音识别与脚本</span><span class="sxs-lookup"><span data-stu-id="7c7ae-104">1. Integrating and using speech recognition and transcription</span></span>

<span data-ttu-id="7c7ae-105">本教程将创建一个混合现实应用程序, 该应用程序探讨如何将 Azure 认知服务语音 SDK 与 HoloLens 2 一起使用。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-105">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="7c7ae-106">完成本系列教程后, 你将能够使用设备的麦克风实时将语音转录到文本, 将语音翻译成其他语言, 并利用语音 SDK 的意图功能理解语音命令人工智能。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-106">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="7c7ae-107">目标</span><span class="sxs-lookup"><span data-stu-id="7c7ae-107">Objectives</span></span>

- <span data-ttu-id="7c7ae-108">了解如何将 Azure Speech SDK 集成到 HoloLens 2 应用程序</span><span class="sxs-lookup"><span data-stu-id="7c7ae-108">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="7c7ae-109">了解如何使用语音命令</span><span class="sxs-lookup"><span data-stu-id="7c7ae-109">Learn how to use voice commands</span></span>
- <span data-ttu-id="7c7ae-110">了解如何使用语音到文本功能</span><span class="sxs-lookup"><span data-stu-id="7c7ae-110">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="7c7ae-111">说明</span><span class="sxs-lookup"><span data-stu-id="7c7ae-111">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="7c7ae-112">入门</span><span class="sxs-lookup"><span data-stu-id="7c7ae-112">Getting Started</span></span>

1. <span data-ttu-id="7c7ae-113">启动 Unity, 并创建一个新项目。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-113">Start Unity, and create a new project.</span></span> <span data-ttu-id="7c7ae-114">输入项目名称语音 SDK 学习模块。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-114">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="7c7ae-115">选择保存项目的位置。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-115">Choose a location for where to save your project.</span></span> <span data-ttu-id="7c7ae-116">然后单击 "创建项目"。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-116">Then click Create Project.</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="7c7ae-118">注意:请确保将模板设置为 "三维", 如上图所示。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-118">Note: Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="7c7ae-119">下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage)Unity 包, 并将其保存到电脑上的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-119">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package, and save it to a folder on your PC.</span></span> <span data-ttu-id="7c7ae-120">将包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-120">Import the package into your Unity project.</span></span> <span data-ttu-id="7c7ae-121">有关如何执行此操作的详细说明, 请参阅[基本模块第1课](mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-121">For detailed instructions on how to do this, please see [Base Module Lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="7c7ae-122">下载并导入用于 Unity 资产包的 Azure [SPEECH SDK](https://aka.ms/csspeech/unitypackage) 。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-122">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="7c7ae-123">通过单击 "资产", 选择 "导入包", 然后选择 "自定义包" 来导入语音 SDK 包。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-123">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="7c7ae-124">找到先前下载的语音 SDK 包, 并打开它以开始导入过程。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-124">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span> 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="7c7ae-127">在下一个弹出窗口中, 单击 "导入" 以开始导入语音 SDK 包。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-127">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="7c7ae-128">请确保选中所有项, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-128">Ensure all items are checked as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. <span data-ttu-id="7c7ae-130">通过单击[此链接](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2), 下载语音 SDK 模块资产包, 也称为 Lunarcom package。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-130">Download the Speech SDK Module asset pack, also know as Lunarcom package by clicking on [this link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span></span> <span data-ttu-id="7c7ae-131">Lunarcom 资产包是为本课系列开发的资产和脚本的集合, 旨在展示 Azure 语音 SDK 的实际使用情况。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-131">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="7c7ae-132">它是一个语音命令终端, 最终将与[基本模块教程](mrlearning-base-ch6.md)中开发的农历模块组装体验进行交互。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-132">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>

6. <span data-ttu-id="7c7ae-133">按照导入混合现实工具包和语音 SDK 所用的类似步骤, 将 Lunarcom 资产包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-133">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="7c7ae-134">配置混合现实工具包 (MRTK)。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-134">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="7c7ae-135">为此, 请在窗口顶部单击 "混合现实工具包" 面板, 然后选择 "添加到场景" 并配置。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-135">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. <span data-ttu-id="7c7ae-139">你的场景现在有多个 MRTK 中的新项。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-139">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="7c7ae-140">单击 "文件", 然后单击 "另存为", 然后将场景命名为 "SpeechScene", 以其他名称保存场景。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-140">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span> 

> <span data-ttu-id="7c7ae-141">注意:如果在将 MRTK 添加到项目中后按下了场景, 而不进入播放模式, 则可能需要重新启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-141">Note: If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span> 

9. <span data-ttu-id="7c7ae-142">在层次结构中选择 MixedRealityToolkit 对象后, 单击 "检查器" 面板中的 "复制" 和 "自定义"。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-142">With the MixedRealityToolkit object selected in your hierarchy, click Copy and Customize in the Inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="7c7ae-144">同时, 在 "检查器" 面板 (在层次结构中选择 MixedRealityToolkit 对象) 中, 通过取消选中 "启用诊断系统" 右侧的框来禁用诊断系统。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-144">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. <span data-ttu-id="7c7ae-146">若要启用语音命令, 请选择要自定义的新创建的 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-146">To enable voice commands, select the newly created MRTK profile to customize.</span></span> <span data-ttu-id="7c7ae-147">在本教程中, 我们将使用用于语音识别和脚本的输入语音命令。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-147">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="7c7ae-148">允许克隆输入配置文件以更改语音设置。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-148">Lets clone the input profile to make changes to speech settings.</span></span>

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. <span data-ttu-id="7c7ae-151">克隆输入配置文件后, 请转到语音命令并克隆语音命令。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-151">Once the input profile is cloned, go to speech commands and clone the speech commands.</span></span>

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. <span data-ttu-id="7c7ae-154">现在, 在 "语音命令" 下, 转到 "常规设置", 并将 "启动行为" 设置为 "手动启动"</span><span class="sxs-lookup"><span data-stu-id="7c7ae-154">Now under speech commands, go to "General Settings" and set "Start Behavior" to "Manual Start"</span></span>

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. <span data-ttu-id="7c7ae-156">在 "项目" 面板中, 展开 "Lunarcom" 文件夹, 然后将 "Lunarcom_Base" prefab 拖到层次结构中。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-156">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. <span data-ttu-id="7c7ae-158">选择层次结构中的 Lunarcom_Base 对象, 并确保将位置设置为 x = 0、y = 0、z = 0, 以及将旋转设置为 x = 0、y = 0 和 z = 0。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-158">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="7c7ae-159">将刻度设置为 read x = 0.008, y = 0.008, z = 0.01。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-159">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="7c7ae-161">单击 "添加组件", 搜索并选择 "LunarcomController"。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-161">Click Add Component, and search for and select LunarcomController.</span></span> <span data-ttu-id="7c7ae-162">此脚本包含在步骤6中导入的 Lunarcom 资产包中。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-162">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="7c7ae-164">若要将应用程序连接到 Azure 认知服务, 必须为语音服务输入订阅密钥 (也称为 API 密钥)。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-164">To connect our applicaiton to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="7c7ae-165">按照[此处](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started)的说明获取免费订阅密钥。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-165">Follow the instructions at [here](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="7c7ae-166">获取订阅密钥后, 请在 "检查器" 面板中的 LunarcomController 组件的 "语音服务 API 密钥" 字段中输入该密钥, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-166">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

18. <span data-ttu-id="7c7ae-167">将订阅密钥注册到 "检查器" 面板中 LunarcomController 组件的 "语音服务区域" 字段时, 请输入所选的区域。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-167">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="7c7ae-168">例如, 对于区域 "美国西部", 键入 "westus"</span><span class="sxs-lookup"><span data-stu-id="7c7ae-168">For example, for the region "West US" type in "westus"</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="7c7ae-170">在层次结构中, 单击 "Lunarcom_Base" 对象左侧的箭头将其展开。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-170">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="7c7ae-171">然后对其子对象 "终端" 执行相同的操作, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-171">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="7c7ae-172">选择 Lunarcom_Base 时, 在 "检查器" 面板中单击 "Lunarcom 文本" 并将其拖到 "LunarcomController" 组件中的 "输出文本" 槽, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-172">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

21. <span data-ttu-id="7c7ae-173">对终端槽执行相同的操作, 并对连接轻型控制器槽执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-173">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="7c7ae-175">单击 "检查器" 面板中 "LunarcomController" 脚本的 "Lunarcom 按钮" 部分旁边的箭头, 将大小更改为3。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-175">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="7c7ae-176">按 Enter 或 Return。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-176">Press Enter or Return.</span></span> <span data-ttu-id="7c7ae-177">这将导致显示三个新元素字段。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-177">This causes three new Element fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="7c7ae-179">在层次结构中单击其旁边的箭头, 展开 "Lunarcom" 按钮, 并使用上述相同过程, 分别将 Mic、卫星和火箭 gameobject 拖到元素0、1和2引用, 并在检查器面板。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-179">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="7c7ae-181">在层次结构中选择 "Lunarcom_Base" 对象。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-181">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="7c7ae-182">单击 "检查器" 面板中的 "添加组件", 搜索并选择 "LunarcomWakeWordRecognizer"。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-182">Click Add Component in the inspector panel, and search for and select LunarcomWakeWordRecognizer.</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="7c7ae-184">在 "唤醒单词" 槽中, 键入 "激活终端"。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-184">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="7c7ae-185">在 "消除字" 槽中, 键入 "消除终端"。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-185">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a><span data-ttu-id="7c7ae-187">在设备上构建应用程序</span><span class="sxs-lookup"><span data-stu-id="7c7ae-187">Build your application to your device</span></span>

1. <span data-ttu-id="7c7ae-188">转到 "文件 > 生成设置", 再次打开 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-188">Open the build settings window again by going to File>Build Settings.</span></span>

![学习 Chapter5 步骤1](images/Lesson1Chapter5Step1.JPG)

2. <span data-ttu-id="7c7ae-190">通过单击“添加打开的场景”按钮，确保要尝试的场景位于“生成中的场景”列表中。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-190">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="7c7ae-191">按“生成”按钮开始生成过程。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-191">Press the Build button to begin the build process.</span></span>

![学习 Chapter5 步骤3](images/Lesson1Chapter5Step3.JPG)

4. <span data-ttu-id="7c7ae-193">为应用程序创建一个新文件夹并为其命名。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-193">Create and name a new folder for your application.</span></span> <span data-ttu-id="7c7ae-194">在下图中，创建了一个名为“应用”的文件夹以包含该应用程序。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-194">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="7c7ae-195">单击“选择文件夹”，开始生成新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-195">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="7c7ae-196">生成完成后，可以关闭 Unity 中的“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-196">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 

![学习 Chapter5 步骤4](images/Lesson1Chapter5Step4.JPG)

> <span data-ttu-id="7c7ae-198">注意：如果生成失败，尝试再次生成或重启 Unity 并再次生成。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-198">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="7c7ae-199">如果看到错误，如“错误：CS0246 = 找不到类型或命名空间名称“XX”（是否缺少 using 指令或程序集引用？）”，可能需要安装 [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span><span class="sxs-lookup"><span data-stu-id="7c7ae-199">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span>

5. <span data-ttu-id="7c7ae-200">生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-200">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="7c7ae-201">双击 ".sln" 解决方案文件, 在 Visual Studio 中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-201">Double click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

> <span data-ttu-id="7c7ae-202">注意:请务必打开新创建的文件夹（即“应用”文件夹，如果遵循前面步骤中的命名约定），因为在该文件夹之外会有一个类似名称的 .sln 文件，不能将其与“生成”文件夹内的 .sln 文件混淆。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-202">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![第 1 课 第 5 章 第 5 步](images/Lesson1Chapter5Step5.JPG)

> <span data-ttu-id="7c7ae-204">注意:如果 Visual Studio 要求你安装新组件，请花一点时间确保按照[“安装工具”页面](install-the-tools.md)中的说明安装所有必备组件</span><span class="sxs-lookup"><span data-stu-id="7c7ae-204">Note: If Visual Studio asks you to install new components, please take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

6. <span data-ttu-id="7c7ae-205">使用 USB 电缆将 HoloLens 2 插入电脑。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-205">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="7c7ae-206">虽然这些课程说明假设你将使用 HoloLens 2 设备部署测试，但你也可以选择部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或选择创建[应用包以进行旁加载](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="7c7ae-206">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="7c7ae-207">在生成到设备之前，请确保设备处于开发者模式。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-207">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="7c7ae-208">如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-208">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="7c7ae-209">如果需要启用开发者模式或与 Visual Studio 配对，请按照[这些说明](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)进行操作。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-209">Please follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="7c7ae-210">通过选择“发布”配置和“ARM”体系结构，配置 Visual Studio 以生成到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-210">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

![学习 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. <span data-ttu-id="7c7ae-212">最后一步是通过选择“调试”>“在不调试的情况下启动”来生成到你的设备。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-212">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="7c7ae-213">选择“在不调试的情况下启动”将导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中显示调试信息。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-213">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="7c7ae-214">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-214">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="7c7ae-215">也可以选择“生成”>“部署解决方案”以部署到你的设备，而无需自动启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-215">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

![学习 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a><span data-ttu-id="7c7ae-217">祝贺</span><span class="sxs-lookup"><span data-stu-id="7c7ae-217">Congratulations</span></span>

<span data-ttu-id="7c7ae-218">你已在应用程序中设置了语音识别, 由 Azure 提供支持。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-218">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="7c7ae-219">运行应用程序以确保所有功能和功能都正常工作。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-219">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="7c7ae-220">首先说到你在步骤22中键入的唤醒字词, 然后激活终端。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-220">Start with saying the wake word you typed in Step 22, Activate Terminal.</span></span> <span data-ttu-id="7c7ae-221">选择麦克风按钮启动语音识别。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-221">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="7c7ae-222">开始说话。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-222">Begin speaking.</span></span> <span data-ttu-id="7c7ae-223">你会在说话时看到你的转录。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-223">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="7c7ae-224">再次按下麦克风按钮以停止语音识别。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-224">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="7c7ae-225">说关闭终端, 隐藏 Lunarcom 终端。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-225">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="7c7ae-226">在下一课中, 我们将学习如何在 Azure 语音 SDK 由于 HoloLens 2 处于脱机状态而无法使用的情况下动态切换到使用设备支持的语音识别。</span><span class="sxs-lookup"><span data-stu-id="7c7ae-226">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="7c7ae-227">下一教程:2.为本地语音到文本翻译添加脱机模式</span><span class="sxs-lookup"><span data-stu-id="7c7ae-227">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)

