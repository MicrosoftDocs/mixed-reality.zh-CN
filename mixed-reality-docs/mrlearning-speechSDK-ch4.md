## <a name="lesson-4"></a><span data-ttu-id="e96e2-101">第 4 课</span><span class="sxs-lookup"><span data-stu-id="e96e2-101">Lesson 4</span></span>

<span data-ttu-id="e96e2-102">在第 4 章，我们将探讨意向的语音服务的功能。</span><span class="sxs-lookup"><span data-stu-id="e96e2-102">In chapter 4, we will explore the Speech services Intent feature.</span></span> <span data-ttu-id="e96e2-103">我们将我们 Azure LUIS 门户设置、 设置我们目的/实体/谈话、 发布我们的意图资源，我们 Unity 应用连接到我们的意图资源，并使我们第一次意向 API 调用。</span><span class="sxs-lookup"><span data-stu-id="e96e2-103">We will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

1. <span data-ttu-id="e96e2-104">允许您的计算机以启用听写，以执行此操作，请转到 Windows 设置，选择"隐私"，然后"speech，"并最后"墨迹书写和键入"开启语音服务和键入建议。</span><span class="sxs-lookup"><span data-stu-id="e96e2-104">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> <span data-ttu-id="e96e2-108">注意： 有关如何执行此操作在 Mac/Macbook 上的信息，请单击[此处](linkgoeshere)。</span><span class="sxs-lookup"><span data-stu-id="e96e2-108">note: for information on how to do this on a Mac/Macbook, click [here](linkgoeshere).</span></span>

2. <span data-ttu-id="e96e2-109">登录到[Azure 门户](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="e96e2-109">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="e96e2-110">你登录后，单击创建资源，并搜索"语言理解"，并按 enter。</span><span class="sxs-lookup"><span data-stu-id="e96e2-110">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="e96e2-112">选择创建按钮，以创建此服务的实例。</span><span class="sxs-lookup"><span data-stu-id="e96e2-112">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="e96e2-113">命名你的项目"Speech_SDK_Learning_Module"，然后选择"现用现付。"</span><span class="sxs-lookup"><span data-stu-id="e96e2-113">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="e96e2-116">选择你的区域。</span><span class="sxs-lookup"><span data-stu-id="e96e2-116">Select your Region.</span></span>  <span data-ttu-id="e96e2-117">在本教程中，选择"（美国） West US"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-117">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="e96e2-118">定价层，然后选择"F0"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-118">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="e96e2-119">现在单击"创建"（位于左下角） 来创建资源。</span><span class="sxs-lookup"><span data-stu-id="e96e2-119">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

   >  <span data-ttu-id="e96e2-120">注意： 一旦你单击"创建"，必须要等待的时间来创建服务，这可能需要一分钟的时间。</span><span class="sxs-lookup"><span data-stu-id="e96e2-120">note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="e96e2-121">创建资源后，通知将显示在门户中。</span><span class="sxs-lookup"><span data-stu-id="e96e2-121">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="e96e2-122">单击此通知，然后选择"转到资源。"</span><span class="sxs-lookup"><span data-stu-id="e96e2-122">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="e96e2-123">从"LUIS API"服务的"快速启动"页，导航到第一步，捕捉"密钥"，并单击"密钥"（也可以在此通过单击蓝色的超链接"密钥，"在下图中所示）。</span><span class="sxs-lookup"><span data-stu-id="e96e2-123">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="e96e2-124">此时会显示你的服务，"密钥"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-124">This will reveal your service, "Keys."</span></span> <span data-ttu-id="e96e2-125">保存密钥中的一个的副本，以便可以更高版本的应用中使用它。</span><span class="sxs-lookup"><span data-stu-id="e96e2-125">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="e96e2-127">返回部分 2b 下的"快速启动"页，单击"语言理解门户"（在上图中所示） 重定向到的网页将用来创建新服务，LUIS 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="e96e2-127">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="e96e2-128">注意：一旦达到"语言理解门户"，您可能需要登录后，如果您尚不，使用 Azure 门户相同的凭据。</span><span class="sxs-lookup"><span data-stu-id="e96e2-128">note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="e96e2-129">如果这是你首次使用 LUIS，您需要向下滚动到底部的欢迎页上，要找到并单击"创建 LUIS"应用程序按钮。</span><span class="sxs-lookup"><span data-stu-id="e96e2-129">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="e96e2-130">登录后，单击我的应用 （如果您当前不是那一节中）。</span><span class="sxs-lookup"><span data-stu-id="e96e2-130">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="e96e2-131">然后可以单击创建新应用。</span><span class="sxs-lookup"><span data-stu-id="e96e2-131">You can then click on Create new app.</span></span> <span data-ttu-id="e96e2-132">新应用命名为"语音 SDK 学习模块。"</span><span class="sxs-lookup"><span data-stu-id="e96e2-132">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="e96e2-133">将"语音 SDK 学习模块"添加到描述字段。</span><span class="sxs-lookup"><span data-stu-id="e96e2-133">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="e96e2-134">然后单击"完成"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-134">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="e96e2-137">注意：如果您的应用程序应以了解不同于英语语言，应将"区域性"更改为合适的语言。</span><span class="sxs-lookup"><span data-stu-id="e96e2-137">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="e96e2-138">单击"生成"位于右上角。</span><span class="sxs-lookup"><span data-stu-id="e96e2-138">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="e96e2-139">在左侧的应用程序资产下, 选择"意向"，然后单击"创建新意向"并将其"PressButton。"命名</span><span class="sxs-lookup"><span data-stu-id="e96e2-139">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="e96e2-141">注意： 务必要使用的意图和使用在本教程中，因为 Lunarcom 应用将引用它们的实体按名称的名称。</span><span class="sxs-lookup"><span data-stu-id="e96e2-141">note: it is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>  <span data-ttu-id="e96e2-142">对于其他项目，命名约定可以是你选择的任何内容。</span><span class="sxs-lookup"><span data-stu-id="e96e2-142">For other projects, naming conventions can be whatever you choose.</span></span> 
>
> <span data-ttu-id="e96e2-143">注意： 你现在应当有 2 个意向-"PressButton"和"None。</span><span class="sxs-lookup"><span data-stu-id="e96e2-143">note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="e96e2-144">在左侧的应用程序资产下, 选择"实体"并单击"创建新实体"和其命名为"Action"，保留为"简单"。 实体类型</span><span class="sxs-lookup"><span data-stu-id="e96e2-144">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="e96e2-146">再次单击"创建新实体"和其命名为"目标"，也保留为"简单"实体类型。</span><span class="sxs-lookup"><span data-stu-id="e96e2-146">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="e96e2-148">在左侧的应用程序资产下, 选择"意向"，然后单击你在步骤 10 中创建的"PressButton"目标。</span><span class="sxs-lookup"><span data-stu-id="e96e2-148">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="e96e2-150">在右侧"查看选项"下拉列表中单击并选择"显示实体值"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-150">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="e96e2-152">单击"输入示例..."</span><span class="sxs-lookup"><span data-stu-id="e96e2-152">Click on the “Enter an example…”</span></span> <span data-ttu-id="e96e2-153">文本框中。</span><span class="sxs-lookup"><span data-stu-id="e96e2-153">textbox.</span></span> <span data-ttu-id="e96e2-154">然后，输入以下言辞：</span><span class="sxs-lookup"><span data-stu-id="e96e2-154">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="e96e2-156">在右侧"查看选项"下拉列表中单击并选择"显示实体名称"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-156">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="e96e2-158">确保每 10 个语音样本添加具有以下实体标签在下列位置 1。)单击标记有误的字词，并在弹出窗口中，选择"删除标签"和 2。）单击上应标记为的单词，并在弹出窗口中，选择相应的标签。</span><span class="sxs-lookup"><span data-stu-id="e96e2-158">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="e96e2-160">现在，如果发布模型，单击右上角的"训练"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-160">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="e96e2-161">然后，完成处理后，请在右上角单击"Test"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-161">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="e96e2-163">输入在"选择启动按钮"，在文本框中。</span><span class="sxs-lookup"><span data-stu-id="e96e2-163">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="e96e2-164">注意： 我们没有添加"选择"为一个操作中任何我们语音样本-但如果单击"检查"，该模型识别"选择"为操作实体。</span><span class="sxs-lookup"><span data-stu-id="e96e2-164">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="e96e2-166">现在，单击右上角"发布"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-166">Now, click "publish" in the top right.</span></span> <span data-ttu-id="e96e2-167">确保在下拉列表中显示"生产"，然后单击"发布"上的弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="e96e2-167">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="e96e2-169">发布后的绿色条应出现在页面顶部。</span><span class="sxs-lookup"><span data-stu-id="e96e2-169">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="e96e2-170">单击绿色栏转到"管理"页上。</span><span class="sxs-lookup"><span data-stu-id="e96e2-170">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="e96e2-172">请单击"密钥和终结点上"在"应用程序设置"下的左侧。</span><span class="sxs-lookup"><span data-stu-id="e96e2-172">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="e96e2-173">然后，将下拉列表"发布到"设置为"生产"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-173">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="e96e2-174">设置的时间区域以匹配自己，并选中复选框以包括所有预测的意向评分。</span><span class="sxs-lookup"><span data-stu-id="e96e2-174">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="e96e2-175">最后，单击"分配资源。"</span><span class="sxs-lookup"><span data-stu-id="e96e2-175">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="e96e2-177">从第一个下拉列表中，选择租户和订阅名称下拉列表中选择"即用即付"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-177">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="e96e2-178">在 LUIS 的资源名称，选择我们在步骤 1-5 中创建的资源。</span><span class="sxs-lookup"><span data-stu-id="e96e2-178">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="e96e2-179">然后，单击"分配资源。"</span><span class="sxs-lookup"><span data-stu-id="e96e2-179">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="e96e2-181">注意： 请确保复制并保存与我们只需分配，以便进行下一节的轻松访问的资源关联的终结点 URL。</span><span class="sxs-lookup"><span data-stu-id="e96e2-181">note: ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="e96e2-182">注意： 对于租户名称，将您的公司或创建此应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="e96e2-182">note: for the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="e96e2-183">现在，在 Unity 中打开新的应用，然后选择 Lunarcom_Base 对象层次结构中。</span><span class="sxs-lookup"><span data-stu-id="e96e2-183">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="e96e2-184">检查器面板中单击"添加组件"，搜索并选择"LunarcomIntentRecognizer。"</span><span class="sxs-lookup"><span data-stu-id="e96e2-184">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="e96e2-186">在检查器面板中的"LunarcomIntentRecognizer"Luis 终结点字段中，输入在第 22 步中保存的终结点 URL。</span><span class="sxs-lookup"><span data-stu-id="e96e2-186">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="e96e2-188">注意：在检查器面板中的"LunarcomOfflineRecognizer"组件，请确保"禁用"选择了"SimulateOfflineMode"否则为测试该程序将不起作用。</span><span class="sxs-lookup"><span data-stu-id="e96e2-188">note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="e96e2-189">在 Unity 编辑器中按播放按钮并单击火箭按钮以启动意图识别。</span><span class="sxs-lookup"><span data-stu-id="e96e2-189">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="e96e2-190">说话短语"选择启动火箭按钮"。</span><span class="sxs-lookup"><span data-stu-id="e96e2-190">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="e96e2-191">注意：应用程序识别所需的函数和激活火箭按钮。</span><span class="sxs-lookup"><span data-stu-id="e96e2-191">note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="e96e2-193">祝贺</span><span class="sxs-lookup"><span data-stu-id="e96e2-193">Congratulations</span></span>

<span data-ttu-id="e96e2-194">正式介绍了如何将语音命令添加从该的语音 SDK 程序 ！</span><span class="sxs-lookup"><span data-stu-id="e96e2-194">You officially learned how to add speech commands from the speech SDK program!</span></span> <span data-ttu-id="e96e2-195">现在您的程序可以识别所有类型的变体的语音的命令。</span><span class="sxs-lookup"><span data-stu-id="e96e2-195">Now your program can recognize speech commands of all kinds of variants.</span></span> <span data-ttu-id="e96e2-196">它进行测试和有与它的一些乐趣 ！</span><span class="sxs-lookup"><span data-stu-id="e96e2-196">Test it out and have a little fun with it!</span></span>

[<span data-ttu-id="e96e2-197">下一课：第 5 课语音 SDK</span><span class="sxs-lookup"><span data-stu-id="e96e2-197">Next Lesson: Speech SDK Lesson 5</span></span>](placeholderlink)

