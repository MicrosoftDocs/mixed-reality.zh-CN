---
title: MR SpeechSDK Module-语音识别和脚本
description: 完成本课程, 了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 0cffb9ac8f61f77b77fc5925264b95ba57d94ece
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460347"
---
# <a name="speech-sdk-learning-module---intent-and-natural-language-understanding"></a><span data-ttu-id="1868c-104">语音 SDK 学习模块-意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="1868c-104">Speech SDK Learning Module - Intent and Natural Language Understanding</span></span>

<span data-ttu-id="1868c-105">在本课程中, 我们将探讨 Azure 语音服务的目的功能。</span><span class="sxs-lookup"><span data-stu-id="1868c-105">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="1868c-106">使用意向功能, 我们可以使用 AI 功能的语音命令为应用程序提供支持, 其中用户可以说出非特定的语音命令, 并使系统能够理解其意图。</span><span class="sxs-lookup"><span data-stu-id="1868c-106">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="1868c-107">在本课程中, 我们将设置 Azure LUIS 门户, 设置我们的意向/实体/最谈话, 发布我们的意图资源, 将我们的 Unity 应用连接到我们的意图资源, 并进行第一次意向 API 调用。</span><span class="sxs-lookup"><span data-stu-id="1868c-107">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="1868c-108">目标</span><span class="sxs-lookup"><span data-stu-id="1868c-108">Objectives</span></span>

- <span data-ttu-id="1868c-109">了解如何在应用程序中设置意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="1868c-109">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="1868c-110">了解如何设置 Azure 的 LUIS 门户</span><span class="sxs-lookup"><span data-stu-id="1868c-110">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="1868c-111">了解如何在 Azure 上设置意向、实体和最谈话</span><span class="sxs-lookup"><span data-stu-id="1868c-111">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="1868c-112">说明</span><span class="sxs-lookup"><span data-stu-id="1868c-112">Instructions</span></span>
1. <span data-ttu-id="1868c-113">允许计算机启用听写, 若要执行此操作, 请转到 "Windows 设置", 选择 "隐私", 然后选择 "语音", 最后 "墨迹 & 键入", 然后打开语音服务和键入建议。</span><span class="sxs-lookup"><span data-stu-id="1868c-113">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="1868c-117">登录到[Azure 门户](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="1868c-117">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="1868c-118">登录后, 单击 "创建资源", 搜索 "语言理解", 然后单击 "enter"。</span><span class="sxs-lookup"><span data-stu-id="1868c-118">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="1868c-120">选择 "创建" 按钮, 创建此服务的实例。</span><span class="sxs-lookup"><span data-stu-id="1868c-120">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="1868c-121">将项目命名为 "Speech_SDK_Learning_Module", 并选择 "即用即付"。</span><span class="sxs-lookup"><span data-stu-id="1868c-121">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="1868c-124">选择区域。</span><span class="sxs-lookup"><span data-stu-id="1868c-124">Select your Region.</span></span>  <span data-ttu-id="1868c-125">对于本教程, 请选择 "(美国) 美国西部"。</span><span class="sxs-lookup"><span data-stu-id="1868c-125">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="1868c-126">然后选择 "F0" 作为 "定价层"。</span><span class="sxs-lookup"><span data-stu-id="1868c-126">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="1868c-127">现在, 单击 "创建" (位于左下角) 以创建资源。</span><span class="sxs-lookup"><span data-stu-id="1868c-127">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="1868c-128">注意: 单击 "创建" 后, 必须等待创建服务, 这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="1868c-128">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="1868c-129">创建资源后, 门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="1868c-129">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="1868c-130">单击此通知, 然后选择 "中转到资源"。</span><span class="sxs-lookup"><span data-stu-id="1868c-130">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="1868c-131">从 "LUIS API" 服务的 "快速入门" 页中, 导航到第一步, 获取 "密钥", 然后单击 "密钥" (也可以通过单击下图中显示的蓝色超链接 "键" 来实现此目的)。</span><span class="sxs-lookup"><span data-stu-id="1868c-131">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="1868c-132">这会显示你的服务 "密钥"。</span><span class="sxs-lookup"><span data-stu-id="1868c-132">This will reveal your service, "Keys."</span></span> <span data-ttu-id="1868c-133">保存其中一个密钥的副本, 以便以后可以在应用中使用它。</span><span class="sxs-lookup"><span data-stu-id="1868c-133">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="1868c-135">返回到第2b 节中的 "快速入门" 页, 单击 "语言理解门户" (如上图所示), 将重定向到 LUIS 应用程序中将用于创建新服务的网页。</span><span class="sxs-lookup"><span data-stu-id="1868c-135">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="1868c-136">注意:到达 "语言理解门户" 时, 你可能需要登录 (如果尚未登录), 其凭据与 Azure 门户相同。</span><span class="sxs-lookup"><span data-stu-id="1868c-136">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="1868c-137">如果这是你第一次使用 LUIS, 则需要向下滚动到 "欢迎" 页的底部, 查找并单击 "创建 LUIS" 应用按钮。</span><span class="sxs-lookup"><span data-stu-id="1868c-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="1868c-138">登录后, 单击 "我的应用" (如果当前不在该部分中)。</span><span class="sxs-lookup"><span data-stu-id="1868c-138">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="1868c-139">然后, 可以单击 "创建新应用"。</span><span class="sxs-lookup"><span data-stu-id="1868c-139">You can then click on Create new app.</span></span> <span data-ttu-id="1868c-140">将新应用命名为 "语音 SDK 学习模块"。</span><span class="sxs-lookup"><span data-stu-id="1868c-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="1868c-141">同时将 "语音 SDK 学习模块" 添加到 "说明" 字段。</span><span class="sxs-lookup"><span data-stu-id="1868c-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="1868c-142">然后单击 "完成"。</span><span class="sxs-lookup"><span data-stu-id="1868c-142">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="1868c-145">纪录如果你的应用程序应了解不同于英语的语言, 则应将 "Culture" 改为适当的语言。</span><span class="sxs-lookup"><span data-stu-id="1868c-145">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="1868c-146">单击右上方的 "生成"。</span><span class="sxs-lookup"><span data-stu-id="1868c-146">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="1868c-147">在左侧的 "应用资产" 下, 选择 "方法", 然后单击 "创建新意向" 并将其命名为 "PressButton"。</span><span class="sxs-lookup"><span data-stu-id="1868c-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="1868c-149">注意:使用本教程中使用的意向和实体的名称很重要, 因为 Lunarcom 应用程序将按名称引用它们。</span><span class="sxs-lookup"><span data-stu-id="1868c-149">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="1868c-150">注意: 现在应有2个意向-"PressButton" 和 "None"。</span><span class="sxs-lookup"><span data-stu-id="1868c-150">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="1868c-151">在左侧的 "应用资产" 下, 选择 "实体", 并单击 "创建新实体" 并将其命名为 "Action", 并将实体类型保留为 "Simple"。</span><span class="sxs-lookup"><span data-stu-id="1868c-151">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="1868c-153">再次单击 "创建新实体" 并将其命名为 "Target", 并将实体类型保留为 "简单"。</span><span class="sxs-lookup"><span data-stu-id="1868c-153">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="1868c-155">在左侧的 "应用资产" 下, 选择 "方法", 然后单击你在步骤10中创建的 "PressButton" 意向。</span><span class="sxs-lookup"><span data-stu-id="1868c-155">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="1868c-157">单击右侧的 "查看选项" 下拉列表, 然后选择 "显示实体值"。</span><span class="sxs-lookup"><span data-stu-id="1868c-157">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="1868c-159">单击 "输入示例 ..."</span><span class="sxs-lookup"><span data-stu-id="1868c-159">Click on the “Enter an example…”</span></span> <span data-ttu-id="1868c-160">工具箱.</span><span class="sxs-lookup"><span data-stu-id="1868c-160">textbox.</span></span> <span data-ttu-id="1868c-161">然后输入以下最谈话:</span><span class="sxs-lookup"><span data-stu-id="1868c-161">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="1868c-163">单击右侧的 "查看选项" 下拉列表, 然后选择 "显示实体名称"。</span><span class="sxs-lookup"><span data-stu-id="1868c-163">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="1868c-165">确保10最谈话中的每一个都在以下位置有1个实体标签。)单击网文的词, 然后在弹出窗口中选择 "删除标签" 和2。)单击应标记为的单词, 然后在弹出窗口中选择相应的标签。</span><span class="sxs-lookup"><span data-stu-id="1868c-165">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="1868c-167">现在, 若要发布模型, 请单击右上方的 "训练"。</span><span class="sxs-lookup"><span data-stu-id="1868c-167">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="1868c-168">完成处理后, 单击右上方的 "测试"。</span><span class="sxs-lookup"><span data-stu-id="1868c-168">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="1868c-170">在文本框中输入 "选择启动按钮"。</span><span class="sxs-lookup"><span data-stu-id="1868c-170">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="1868c-171">注意: 我们未将 "select" 添加为最谈话中任何一项操作, 但如果单击 "检查", 则模型将 "select" 识别为操作实体。</span><span class="sxs-lookup"><span data-stu-id="1868c-171">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="1868c-173">现在, 单击右上方的 "发布"。</span><span class="sxs-lookup"><span data-stu-id="1868c-173">Now, click "publish" in the top right.</span></span> <span data-ttu-id="1868c-174">确保下拉列表中显示 "生产", 并在弹出窗口中单击 "发布"。</span><span class="sxs-lookup"><span data-stu-id="1868c-174">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="1868c-176">发布后, 页面顶部会显示一个绿色栏。</span><span class="sxs-lookup"><span data-stu-id="1868c-176">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="1868c-177">单击绿色栏转到 "管理" 页。</span><span class="sxs-lookup"><span data-stu-id="1868c-177">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="1868c-179">在左侧的 "应用程序设置" 下, 单击 "密钥和终结点"。</span><span class="sxs-lookup"><span data-stu-id="1868c-179">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="1868c-180">然后, 将下拉 "发布到" 设置为 "生产"。</span><span class="sxs-lookup"><span data-stu-id="1868c-180">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="1868c-181">设置要匹配的时区, 并选中复选框以包括所有预测意向分数。</span><span class="sxs-lookup"><span data-stu-id="1868c-181">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="1868c-182">最后, 单击 "分配资源"。</span><span class="sxs-lookup"><span data-stu-id="1868c-182">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="1868c-184">从第一个下拉列表中选择 "租户", 然后在 "订阅名称" 下拉列表中选择 "即用即付"。</span><span class="sxs-lookup"><span data-stu-id="1868c-184">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="1868c-185">在 "LUIS 资源名称" 下, 选择前面在步骤1-5 中创建的资源。</span><span class="sxs-lookup"><span data-stu-id="1868c-185">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="1868c-186">然后, 单击 "分配资源"。</span><span class="sxs-lookup"><span data-stu-id="1868c-186">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="1868c-188">注意:请确保复制并保存与我们刚刚分配的资源相关联的终结点 URL, 以便在下一部分可以轻松访问该 URL。</span><span class="sxs-lookup"><span data-stu-id="1868c-188">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="1868c-189">注意:对于租户名称, 请将为此应用程序创建的公司或配置文件放入其中。</span><span class="sxs-lookup"><span data-stu-id="1868c-189">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="1868c-190">现在, 请在 Unity 中打开新应用, 并选择层次结构中的 Lunarcom_Base 对象。</span><span class="sxs-lookup"><span data-stu-id="1868c-190">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="1868c-191">单击 "检查器" 面板中的 "添加组件", 搜索并选择 "LunarcomIntentRecognizer"。</span><span class="sxs-lookup"><span data-stu-id="1868c-191">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="1868c-193">在 "检查器" 面板中的 "LunarcomIntentRecognizer" 的 "Luis 终结点" 字段中, 输入在步骤22中保存的终结点 URL。</span><span class="sxs-lookup"><span data-stu-id="1868c-193">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="1868c-195">注意:在 "检查器" 面板中的 "LunarcomOfflineRecognizer" 组件中, 请确保已为 "SimulateOfflineMode" 选择 "禁用", 否则测试程序将不起作用。</span><span class="sxs-lookup"><span data-stu-id="1868c-195">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="1868c-196">按 Unity 编辑器中的 "播放" 按钮, 然后单击 "火箭" 按钮, 开始意图识别。</span><span class="sxs-lookup"><span data-stu-id="1868c-196">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="1868c-197">Utter "选择启动火箭" 按钮。</span><span class="sxs-lookup"><span data-stu-id="1868c-197">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="1868c-198">注意:应用已识别所需的函数并激活了 "火箭" 按钮。</span><span class="sxs-lookup"><span data-stu-id="1868c-198">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="1868c-200">祝贺</span><span class="sxs-lookup"><span data-stu-id="1868c-200">Congratulations</span></span>

<span data-ttu-id="1868c-201">在本课中, 我们学习了如何添加 AI 功能的语音命令!</span><span class="sxs-lookup"><span data-stu-id="1868c-201">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="1868c-202">即使您的程序没有 utter 精确的语音命令, 也可以识别用户的意图。</span><span class="sxs-lookup"><span data-stu-id="1868c-202">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

