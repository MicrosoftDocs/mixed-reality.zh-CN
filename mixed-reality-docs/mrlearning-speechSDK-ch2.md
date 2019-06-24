## <a name="lesson-2"></a><span data-ttu-id="d9caf-101">第 2 课</span><span class="sxs-lookup"><span data-stu-id="d9caf-101">Lesson 2</span></span>

<span data-ttu-id="d9caf-102">在第 2 课，我们将添加的脱机模式，将使我们能够时无法连接到 Azure 服务，我们将执行本地语音到文本翻译*模拟*断开连接的状态。</span><span class="sxs-lookup"><span data-stu-id="d9caf-102">In Lesson 2, we will add an Offline mode that will allow us to perform local speech-to-text translation when we are unable to connect to the Azure service and we will *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="d9caf-103">在层次结构中选择"Lunarcom_Base"对象和检查器面板中单击"添加组件"。</span><span class="sxs-lookup"><span data-stu-id="d9caf-103">Select the "Lunarcom_Base" object in the hierarchy and click “Add Component” in the inspector panel.</span></span> <span data-ttu-id="d9caf-104">搜索并选择"Lunarcom 脱机识别。"</span><span class="sxs-lookup"><span data-stu-id="d9caf-104">Search for and select the "Lunarcom Offline Recognition."</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. <span data-ttu-id="d9caf-106">单击"LunarcomOfflineRecognizer"中的下拉列表，然后选择"已启用"。</span><span class="sxs-lookup"><span data-stu-id="d9caf-106">Click the dropdown in the “LunarcomOfflineRecognizer” and select “Enabled.”</span></span> <span data-ttu-id="d9caf-107">此程序将成为用户不具有连接的项目。</span><span class="sxs-lookup"><span data-stu-id="d9caf-107">This will program the project to act like the user doesn't have connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="d9caf-109">现在，按播放在 Unity 编辑器中，并对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="d9caf-109">Now, press play on the Unity Editor and test it.</span></span> <span data-ttu-id="d9caf-110">按场景中左下角中的麦克风并开始说话。</span><span class="sxs-lookup"><span data-stu-id="d9caf-110">Press the microphone in the bottom left hand corner in the scene and begin speaking.</span></span> 

> <span data-ttu-id="d9caf-111">注意： 我们处于脱机状态，因为已禁用唤醒 Word 功能。</span><span class="sxs-lookup"><span data-stu-id="d9caf-111">note: because we’re offline, the Wake Word functionality has been disabled.</span></span> <span data-ttu-id="d9caf-112">因此，需要以物理方式在每次您想要拥有语音识别单击麦克风时脱机。</span><span class="sxs-lookup"><span data-stu-id="d9caf-112">So, you will have to physically click the microphone every time you wish to have your speech recognized while offline.</span></span> 

<span data-ttu-id="d9caf-113">下面是您的场景可能如下所示的示例：</span><span class="sxs-lookup"><span data-stu-id="d9caf-113">Below is an example of what your scene could look like:</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="d9caf-115">祝贺</span><span class="sxs-lookup"><span data-stu-id="d9caf-115">Congratulations</span></span>

<span data-ttu-id="d9caf-116">已启用脱机模式 ！</span><span class="sxs-lookup"><span data-stu-id="d9caf-116">The offline mode has been enabled!</span></span> <span data-ttu-id="d9caf-117">现在当您离开任何形式的 internet，您仍可使用语音 SDK 项目 ！</span><span class="sxs-lookup"><span data-stu-id="d9caf-117">Now when you're away from any form of internet, you can still work on your project with Speech-SDK!</span></span> 

[<span data-ttu-id="d9caf-118">下一课：第 3 课 SpeechSDK</span><span class="sxs-lookup"><span data-stu-id="d9caf-118">Next Lesson: SpeechSDK Lesson 3</span></span>](link placeholder)

