# <a name="speech-sdk-learning-module"></a><span data-ttu-id="beb32-101">语音 SDK 学习模块</span><span class="sxs-lookup"><span data-stu-id="beb32-101">Speech SDK Learning Module</span></span>

<span data-ttu-id="beb32-102">在本教程将创建一个混合现实应用程序，探讨如何使用 Azure 认知服务语音 SDK，HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="beb32-102">In this tutorial you will create a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="beb32-103">当完成了本系列教程，你将能够使用你的设备的麦克风转录语音转文本在真实时间中，将语音翻译成其他语言，并利用语音 SDK 的意向功能，若要了解使用语音命令人工智能。</span><span class="sxs-lookup"><span data-stu-id="beb32-103">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

<span data-ttu-id="beb32-104">目标：</span><span class="sxs-lookup"><span data-stu-id="beb32-104">Objectives:</span></span>

- <span data-ttu-id="beb32-105">了解如何将 Azure 语音 SDK 集成到 HoloLens 2 应用程序</span><span class="sxs-lookup"><span data-stu-id="beb32-105">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="beb32-106">了解如何使用语音命令</span><span class="sxs-lookup"><span data-stu-id="beb32-106">Learn how to use voice commands</span></span>
- <span data-ttu-id="beb32-107">了解如何使用语音转文本功能</span><span class="sxs-lookup"><span data-stu-id="beb32-107">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="beb32-108">说明</span><span class="sxs-lookup"><span data-stu-id="beb32-108">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="beb32-109">入门</span><span class="sxs-lookup"><span data-stu-id="beb32-109">Getting Started</span></span>

1. <span data-ttu-id="beb32-110">启动 Unity 并创建一个新的项目。</span><span class="sxs-lookup"><span data-stu-id="beb32-110">Start Unity and create a new project.</span></span> <span data-ttu-id="beb32-111">输入项目名称"语音 SDK 学习模块。"</span><span class="sxs-lookup"><span data-stu-id="beb32-111">Enter the project name “Speech SDK Learning Module.”</span></span> <span data-ttu-id="beb32-112">选择你的项目的保存位置的位置。</span><span class="sxs-lookup"><span data-stu-id="beb32-112">Choose a location for where to save your project.</span></span> <span data-ttu-id="beb32-113">然后单击"创建项目"。</span><span class="sxs-lookup"><span data-stu-id="beb32-113">Then click "Create Project."</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="beb32-115">注意：确保模板将设置为"3D"，在上图中所示。</span><span class="sxs-lookup"><span data-stu-id="beb32-115">Note: Ensure that the template is set to "3D," as shown in the image above.</span></span>

2. <span data-ttu-id="beb32-116">下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage)Unity 包，并在您的 PC 上将其保存到一个文件夹。</span><span class="sxs-lookup"><span data-stu-id="beb32-116">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package and save it to a folder on your PC.</span></span> <span data-ttu-id="beb32-117">将包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="beb32-117">Import the package into your Unity project.</span></span> <span data-ttu-id="beb32-118">有关如何执行此操作的详细说明，请参阅[的基本模块第 1 课](mrlearning-base-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="beb32-118">For detailed instructions on how to do this, please see [base module lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="beb32-119">下载并导入 Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) Unity 资产包。</span><span class="sxs-lookup"><span data-stu-id="beb32-119">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for Unity asset package.</span></span> <span data-ttu-id="beb32-120">通过单击"资产"选择"导入包"然后选择"自定义包。"上导入的语音 SDK 包</span><span class="sxs-lookup"><span data-stu-id="beb32-120">Import the Speech SDK package by clicking on "assets," selecting "import package," then selecting "custom package."</span></span> <span data-ttu-id="beb32-121">查找前面下载的语音 SDK 包和打开它，以开始导入进程。</span><span class="sxs-lookup"><span data-stu-id="beb32-121">Find the Speech SDK package downloaded earlier and open it to begin the importing process.</span></span> 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="beb32-123">在下一步的弹出窗口中，单击"导入"以开始导入的语音 SDK 包。</span><span class="sxs-lookup"><span data-stu-id="beb32-123">In the next pop-up window, click “Import” to begin importing the Speech SDK package.</span></span> <span data-ttu-id="beb32-124">确保选中所有项，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="beb32-124">Ensure all items are checked, as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. <span data-ttu-id="beb32-126">下载[Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage)资产包。</span><span class="sxs-lookup"><span data-stu-id="beb32-126">Download the [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) asset package.</span></span> <span data-ttu-id="beb32-127">Lunarcom 资产包是一系列资产并在本课程系列开发的脚本来展示 Azure 的语音 SDK 的实际用途。</span><span class="sxs-lookup"><span data-stu-id="beb32-127">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="beb32-128">它是最终将与之农历模块程序集体验开发中的语音命令终端[基本模块教程。](mrlearning-base-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="beb32-128">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>
6. <span data-ttu-id="beb32-129">按照类似步骤采用的混合现实工具包和语音 SDK 导入 Lunarcom 资产包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="beb32-129">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="beb32-130">配置混合的现实工具包 (MRTK)。</span><span class="sxs-lookup"><span data-stu-id="beb32-130">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="beb32-131">要执行此操作，在窗口右上角的"混合现实 Toolkit"面板中单击并选择"将添加到场景和配置"。</span><span class="sxs-lookup"><span data-stu-id="beb32-131">To do this, click on the "Mixed Reality Toolkit" panel in the top of your window, and then select "Add to Scene and Configure."</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. <span data-ttu-id="beb32-133">您的场景将现在包含几个新项从 MRTK。</span><span class="sxs-lookup"><span data-stu-id="beb32-133">Your scene will now have several new items in it from the MRTK.</span></span> <span data-ttu-id="beb32-134">保存您的场景通过单击"文件"以其他名称，然后"另存为"和"SpeechScene"命名您的场景。</span><span class="sxs-lookup"><span data-stu-id="beb32-134">Save your scene under a different name by clicking on "file," then "save as" and name your scene “SpeechScene”.</span></span> 

   > <span data-ttu-id="beb32-135">注意：如果 MRTK 添加到项目，并且它不会进入"播放"模式后，可在您的场景中按播放按钮，您可能需要重新启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="beb32-135">Note: If you press the play button on your scene after you add the MRTK to your project, and it doesn't enter the "play" mode, you may need to restart Unity.</span></span> 

9. <span data-ttu-id="beb32-136">"MixedRealityToolkit"选定对象层次结构中，单击"复制和自定义"检查器面板中。</span><span class="sxs-lookup"><span data-stu-id="beb32-136">With the “MixedRealityToolkit" object selected in your hierarchy, click "copy and customize" in the inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="beb32-138">此外在 （与你的层次结构中选择的"MixedRealityToolkit"对象） 的检查器窗格中，通过取消选中"启用诊断 System"右侧的框禁用诊断系统。</span><span class="sxs-lookup"><span data-stu-id="beb32-138">Also in the inspector panel (with the “MixedRealityToolkit" object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of "Enable Diagnostics System."</span></span>

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. <span data-ttu-id="beb32-140">在项目面板中，展开"Lunarcom"文件夹并将"Lunarcom_Base"预设可拖放到你的层次结构。</span><span class="sxs-lookup"><span data-stu-id="beb32-140">In the project panel, expand the "Lunarcom" folder and drag the "Lunarcom_Base" prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. <span data-ttu-id="beb32-142">在层次结构中选择"Lunarcom_Base"对象，并确保该位置设置为 x = 0，y = 0，并且 z = 0，以及旋转将设置为 x = 0，y = 0，并且 z = 0。</span><span class="sxs-lookup"><span data-stu-id="beb32-142">Select the "Lunarcom_Base" object in your hierarchy and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="beb32-143">设置要读取的比例 x = 0.008，y = 0.008 和 z = 0.01。</span><span class="sxs-lookup"><span data-stu-id="beb32-143">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. <span data-ttu-id="beb32-145">单击"添加组件"，搜索并选择"LunarcomController。"</span><span class="sxs-lookup"><span data-stu-id="beb32-145">Click "add component" and search for and select “LunarcomController.”</span></span> <span data-ttu-id="beb32-146">此脚本包含你在步骤 6 中导入 Lunarcom 资产包中。</span><span class="sxs-lookup"><span data-stu-id="beb32-146">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. <span data-ttu-id="beb32-148">我们的应用程序连接到 Azure 认知服务，你必须输入"订阅密钥"也称为"API 密钥"的语音服务。</span><span class="sxs-lookup"><span data-stu-id="beb32-148">To connect our app to Azure Cognitive Services, you must enter a "subscription key" also known as an "API Key" for the Speech Service.</span></span> <span data-ttu-id="beb32-149">按照的说明[此链接](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started)以获取免费订阅密钥。</span><span class="sxs-lookup"><span data-stu-id="beb32-149">Follow the instructions at [this link](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="beb32-150">一旦您获取订阅密钥，请将其输入中的检查器面板中，"LunarcomController"组件的"语音服务 API 密钥"字段中如下图所示。</span><span class="sxs-lookup"><span data-stu-id="beb32-150">Once you obtain the subscription key, enter it into the “Speech Service API Key” field of the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>

15. <span data-ttu-id="beb32-151">输入你注册时选择你的订阅密钥置于"LunarcomController"组件检查器面板中的"语音服务区域"字段的区域。</span><span class="sxs-lookup"><span data-stu-id="beb32-151">Enter the Region that you chose when you signed up for the subscription key into the “Speech Service Region” field of the "LunarcomController" component in the inspector panel.</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. <span data-ttu-id="beb32-153">在层次结构中展开"Lunarcom_Base"对象，通过单击它，左侧的箭头，然后执行它的子对象"终端"，如下图中所示相同的。</span><span class="sxs-lookup"><span data-stu-id="beb32-153">In your hierarchy, expand the "Lunarcom_Base" object by clicking the arrow to the left of it, then do the same for its child object, "Terminal" as shown in the image below.</span></span>

17. <span data-ttu-id="beb32-154">选择"Lunarcom_Base"后，单击并在检查器窗格中，拖动"Lunarcom Text"层次结构中的"输出文本"插槽"LunarcomController"组件中，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="beb32-154">While "Lunarcom_Base" is selected, click and drag “Lunarcom Text” from the hierarchy to the "Output Text" slot in the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>
18. <span data-ttu-id="beb32-155">现在到"终端"槽中，"连接 Light Controller"槽的"连接 Light"对象执行与"终端"的对象相同的操作。</span><span class="sxs-lookup"><span data-stu-id="beb32-155">Now do the same thing with the "Terminal" object into the "terminal" slot and the "Connection Light" object to the "Connection Light Controller" slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. <span data-ttu-id="beb32-157">单击检查器面板中的"LunarcomController"脚本"Lunarcom 按钮"部分旁边的箭头并将大小更改为 3 和键盘上按 Enter 键或 Return 键。</span><span class="sxs-lookup"><span data-stu-id="beb32-157">Click the arrow next to the "Lunarcom Buttons" section of the "LunarcomController" script in the inspector panel and change the size to 3 and press the Enter or Return key on your keyboard.</span></span> <span data-ttu-id="beb32-158">这会导致要显示的三个新"Element"字段。</span><span class="sxs-lookup"><span data-stu-id="beb32-158">This will cause three new "Element" fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. <span data-ttu-id="beb32-160">展开"Lunarcom 按钮"通过单击层次结构中其旁边的箭头，然后使用与上述相同的进程，将分别在组件中的"LunarcomController"组件是 0、 1 和 2 的元素引用到 Mic、 附属和火箭 gameobjects检查器面板。</span><span class="sxs-lookup"><span data-stu-id="beb32-160">Expand the "Lunarcom Buttons" by clicking the arrow next to it in your hierarchy and, using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references respectively in the "LunarcomController" component in the inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. <span data-ttu-id="beb32-162">在层次结构中选择"Lunarcom_Base"对象。</span><span class="sxs-lookup"><span data-stu-id="beb32-162">Select the "Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="beb32-163">检查器面板中单击"添加组件"，搜索并选择"LunarcomWakeWordRecognizer。"</span><span class="sxs-lookup"><span data-stu-id="beb32-163">Click “Add Component” in the inspector panel and search for and select “LunarcomWakeWordRecognizer.”</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. <span data-ttu-id="beb32-165">在"唤醒单词"槽中，键入在"激活终端"。</span><span class="sxs-lookup"><span data-stu-id="beb32-165">In the "Wake Word" slot, type in "Activate Terminal."</span></span> <span data-ttu-id="beb32-166">此外，在"关闭 Word"槽中，键入"解除终端"。</span><span class="sxs-lookup"><span data-stu-id="beb32-166">Also, in the "Dismiss Word" slot, type in "Dismiss Terminal."</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a><span data-ttu-id="beb32-168">祝贺</span><span class="sxs-lookup"><span data-stu-id="beb32-168">Congratulations</span></span>

<span data-ttu-id="beb32-169">已由 Azure 提供支持，在应用程序中设置语音识别 ！</span><span class="sxs-lookup"><span data-stu-id="beb32-169">You've set up voice recognition in your application, powered by Azure!</span></span> <span data-ttu-id="beb32-170">运行应用程序以确保所有函数都正常都工作。</span><span class="sxs-lookup"><span data-stu-id="beb32-170">Run the application to ensure all functions are working properly.</span></span> <span data-ttu-id="beb32-171">开始说步骤 22，"激活终端。"中键入唤醒文字</span><span class="sxs-lookup"><span data-stu-id="beb32-171">Start with saying the wake word you typed in step 22, "Activate Terminal."</span></span> <span data-ttu-id="beb32-172">然后，选择麦克风按钮以启动语音识别，并开始说话。</span><span class="sxs-lookup"><span data-stu-id="beb32-172">Then, select the microphone button to start voice recognition and begin speaking.</span></span> <span data-ttu-id="beb32-173">你将看到您一边说一边转录在终端中的单词。</span><span class="sxs-lookup"><span data-stu-id="beb32-173">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="beb32-174">按第二次的麦克风按钮停止语音识别。</span><span class="sxs-lookup"><span data-stu-id="beb32-174">Press the microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="beb32-175">说"消除终端"若要隐藏 Lunarcom 终端。</span><span class="sxs-lookup"><span data-stu-id="beb32-175">Say "Dismiss Terminal" to hide the Lunarcom terminal.</span></span> <span data-ttu-id="beb32-176">在下一课中，我们将了解如何动态切换到 Azure 的语音 SDK 不是由于处于脱机状态 HoloLens 2 可用的情况下使用提供设备支持语音识别。</span><span class="sxs-lookup"><span data-stu-id="beb32-176">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition, for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="beb32-177">下一课：第 2 课语音 SDK</span><span class="sxs-lookup"><span data-stu-id="beb32-177">Next Lesson: Speech SDK Lesson 2</span></span>](mrlearning-speechSDK-ch2.md)

