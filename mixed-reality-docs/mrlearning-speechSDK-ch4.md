---
title: Azure 语音服务教程-4。 设置意向和自然语言理解
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure Speech SDK。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 8805fa6410e882bce2f0fe8da780dfd5f794cc74
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553987"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="1c627-105">4. 设置意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="1c627-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="1c627-106">在本课中，您将了解 Azure 语音服务的意图功能。</span><span class="sxs-lookup"><span data-stu-id="1c627-106">In this lesson, you will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="1c627-107">使用意向功能，您可以使用 AI 功能的语音命令为应用程序提供支持，用户可以在其中说出非特定的语音命令，并使系统理解其意图。</span><span class="sxs-lookup"><span data-stu-id="1c627-107">The Intent feature allows you to equip our application with AI-powered voice commands, where users can say non-specific voice commands and still have their intent understood by the system.</span></span> <span data-ttu-id="1c627-108">在本课程中，我们将设置 Azure LUIS 门户，设置我们的意向/实体/最谈话，发布我们的意图资源，将我们的 Unity 应用连接到我们的意图资源，并进行第一次意向 API 调用。</span><span class="sxs-lookup"><span data-stu-id="1c627-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="1c627-109">目标</span><span class="sxs-lookup"><span data-stu-id="1c627-109">Objectives</span></span>

- <span data-ttu-id="1c627-110">了解如何在应用程序中设置意向和自然语言理解</span><span class="sxs-lookup"><span data-stu-id="1c627-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="1c627-111">了解如何设置 Azure 的 LUIS 门户</span><span class="sxs-lookup"><span data-stu-id="1c627-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="1c627-112">了解如何在 Azure 上设置意向、实体和最谈话</span><span class="sxs-lookup"><span data-stu-id="1c627-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="1c627-113">说明</span><span class="sxs-lookup"><span data-stu-id="1c627-113">Instructions</span></span>

1. <span data-ttu-id="1c627-114">允许您的计算机启用听写。</span><span class="sxs-lookup"><span data-stu-id="1c627-114">Allow your machine to enable Dictation.</span></span> <span data-ttu-id="1c627-115">为此，请转到 "Windows 设置"，选择 "隐私"，然后选择 "语音"，然后依次单击 "墨迹 & 键入" 和 "输入建议"。</span><span class="sxs-lookup"><span data-stu-id="1c627-115">To do this, go to Windows Settings, select "privacy," then "speech," followed by "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="1c627-119">登录到[Azure 门户](https://portal.azure.com/)。</span><span class="sxs-lookup"><span data-stu-id="1c627-119">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="1c627-120">登录后，单击 "创建资源"，搜索 "语言理解"，然后单击 "Enter"。</span><span class="sxs-lookup"><span data-stu-id="1c627-120">Once you are logged in, click on Create a resource, search for "Language Understanding" and click Enter.</span></span>

    ![mrlearning-speech-ch4-1-step2 .png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="1c627-122">单击 "**创建**" 按钮以创建此服务的实例。</span><span class="sxs-lookup"><span data-stu-id="1c627-122">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-speech-ch4-1-step3a .png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="1c627-124">为资源提供**名称**，例如，*语音-SDK-学习模块*。</span><span class="sxs-lookup"><span data-stu-id="1c627-124">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="1c627-125">对于 "**订阅**"，选择 "即用*即付*" 或 "*免费*"。</span><span class="sxs-lookup"><span data-stu-id="1c627-125">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="1c627-126">接下来，单击 **"新建" 链接创建**新的**资源组**，输入名称（例如，" *HoloLens-2-资源组*"），然后单击 **"确定"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="1c627-126">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and click the **OK** button.</span></span>

    ![mrlearning-speech-ch4-1-step3b .png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="1c627-128">选择**创作位置**和**运行时位置**。</span><span class="sxs-lookup"><span data-stu-id="1c627-128">Select your **Authoring location** and **Runtime location**.</span></span> <span data-ttu-id="1c627-129">出于本教程的目的，请使用 *（美国） "美国西部*"，然后选择 "**创作" 定价层**和 "**运行时" 定价层**的*F0 （每秒5个调用，每月10000个调用）* 。</span><span class="sxs-lookup"><span data-stu-id="1c627-129">For the purpose of this tutorial, use *(US) West US*, then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="1c627-130">最后，单击 "**创建**" 按钮以创建资源，以及新资源组。</span><span class="sxs-lookup"><span data-stu-id="1c627-130">Finally, click the **Create** button to create the resource, as well as the new resource group.</span></span>

    ![mrlearning-speech-ch4-1-step4 .png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="1c627-132">单击 "创建" 按钮后，必须等待创建服务，这可能需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="1c627-132">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

5. <span data-ttu-id="1c627-133">资源创建过程完成后，你将看到**部署已完成**的消息。</span><span class="sxs-lookup"><span data-stu-id="1c627-133">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-speech-ch4-1-step5 .png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="1c627-135">使用相同的用户帐户登录到[语言理解智能服务（LUIS）](https://www.luis.ai/)门户，选择你的国家/地区，并同意使用条款。</span><span class="sxs-lookup"><span data-stu-id="1c627-135">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="1c627-136">到达语言理解门户后，你可能需要登录（如果尚未登录），其凭据与 Azure 门户相同。</span><span class="sxs-lookup"><span data-stu-id="1c627-136">Upon reaching the Language Understanding portal, you may need to log in, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="1c627-137">如果这是你第一次使用 LUIS，则需要向下滚动到 "欢迎" 页的底部，查找并单击 "创建 LUIS" 应用按钮。</span><span class="sxs-lookup"><span data-stu-id="1c627-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the Welcome page to find and click the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="1c627-138">登录后，单击 "我的应用" （如果当前不在该部分中）。</span><span class="sxs-lookup"><span data-stu-id="1c627-138">Once logged in, click My Apps (if you are not currently in that section).</span></span> <span data-ttu-id="1c627-139">然后，可以单击 "创建新应用"。</span><span class="sxs-lookup"><span data-stu-id="1c627-139">You can then click on Create new app.</span></span> <span data-ttu-id="1c627-140">将新应用命名为 "语音 SDK 学习模块"。</span><span class="sxs-lookup"><span data-stu-id="1c627-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="1c627-141">同时将 "语音 SDK 学习模块" 添加到 "说明" 字段。</span><span class="sxs-lookup"><span data-stu-id="1c627-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="1c627-142">然后单击 "完成"。</span><span class="sxs-lookup"><span data-stu-id="1c627-142">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="1c627-145">如果你的应用程序应了解不同于英语的语言，则应将 "Culture" 改为适当的语言。</span><span class="sxs-lookup"><span data-stu-id="1c627-145">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="1c627-146">单击右上方的 "生成"。</span><span class="sxs-lookup"><span data-stu-id="1c627-146">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="1c627-147">在左侧的 "应用资产" 下，选择 "方法"，然后单击 "创建新意向" 并将其命名为 "PressButton"。</span><span class="sxs-lookup"><span data-stu-id="1c627-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="1c627-149">使用本教程中使用的意向和实体的名称很重要，因为 Lunarcom 应用程序将按名称引用它们。</span><span class="sxs-lookup"><span data-stu-id="1c627-149">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="1c627-150">现在应有2个意向-"PressButton" 和 "None"。</span><span class="sxs-lookup"><span data-stu-id="1c627-150">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="1c627-151">在左侧的 "应用资产" 下，选择 "实体"，单击 "新建实体"，将其命名为 "Action"，并将实体类型保留为 "Simple"。</span><span class="sxs-lookup"><span data-stu-id="1c627-151">Under App Assets on the left, select “Entities”, click “Create New Entity”, name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="1c627-153">再次单击 "创建新实体" 并将其命名为 "Target"。</span><span class="sxs-lookup"><span data-stu-id="1c627-153">Click “Create New Entity” again and name it “Target”.</span></span> <span data-ttu-id="1c627-154">将实体类型保留为 "简单"。</span><span class="sxs-lookup"><span data-stu-id="1c627-154">Keep the Entity Type as “Simple”, as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="1c627-156">在左侧的 "应用资产" 下，选择 "方法"，然后单击你在步骤10中创建的 "PressButton" 意向。</span><span class="sxs-lookup"><span data-stu-id="1c627-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="1c627-158">单击右侧的 "查看选项" 下拉列表，然后选择 "显示实体值"。</span><span class="sxs-lookup"><span data-stu-id="1c627-158">Click the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="1c627-160">单击 "输入示例 ..."</span><span class="sxs-lookup"><span data-stu-id="1c627-160">Click the “Enter an example…”</span></span> <span data-ttu-id="1c627-161">文本框中。</span><span class="sxs-lookup"><span data-stu-id="1c627-161">textbox.</span></span> <span data-ttu-id="1c627-162">然后输入以下最谈话：</span><span class="sxs-lookup"><span data-stu-id="1c627-162">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="1c627-164">单击右侧的 "查看选项" 下拉列表，然后选择 "显示实体名称"。</span><span class="sxs-lookup"><span data-stu-id="1c627-164">Click the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="1c627-166">确保10最谈话中的每一个都在以下位置有1个实体标签。）单击网文的词，然后在弹出窗口中选择 "删除标签" 和2。）单击应标记为的单词，然后在弹出窗口中选择相应的标签。</span><span class="sxs-lookup"><span data-stu-id="1c627-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="1c627-168">现在，若要发布模型，请单击右上方的 "训练"。</span><span class="sxs-lookup"><span data-stu-id="1c627-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="1c627-169">完成处理后，单击右上方的 "测试"。</span><span class="sxs-lookup"><span data-stu-id="1c627-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="1c627-171">在文本框中输入 "选择启动按钮"。</span><span class="sxs-lookup"><span data-stu-id="1c627-171">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="1c627-172">我们未将 "select" 添加为最谈话中任何一项的操作，但如果单击 "检查"，则模型被识别为 "选择" 作为操作实体。</span><span class="sxs-lookup"><span data-stu-id="1c627-172">We did not add “select” as an action in any of our Utterances, but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="1c627-174">单击右上方的 "发布"。</span><span class="sxs-lookup"><span data-stu-id="1c627-174">Click "publish" in the top right.</span></span> <span data-ttu-id="1c627-175">确保下拉列表中显示 "生产"，并在弹出窗口中单击 "发布"。</span><span class="sxs-lookup"><span data-stu-id="1c627-175">Ensure the dropdown says “Production” and click "publish" on the popup, as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="1c627-177">发布后，页面顶部会显示一个绿色栏。</span><span class="sxs-lookup"><span data-stu-id="1c627-177">Once published, a green bar should appear at the top of the page.</span></span> <span data-ttu-id="1c627-178">单击绿色条以查看 "管理" 页。</span><span class="sxs-lookup"><span data-stu-id="1c627-178">Click the green bar to view the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="1c627-180">在左侧的 "应用程序设置" 下，单击 "密钥和终结点"。</span><span class="sxs-lookup"><span data-stu-id="1c627-180">Click "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="1c627-181">然后，将下拉 "发布到" 设置为 "生产"。</span><span class="sxs-lookup"><span data-stu-id="1c627-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="1c627-182">设置要匹配的时区，并选中复选框以包括所有预测意向分数。</span><span class="sxs-lookup"><span data-stu-id="1c627-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="1c627-183">最后，单击 "分配资源"。</span><span class="sxs-lookup"><span data-stu-id="1c627-183">Lastly, click "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="1c627-185">从第一个下拉列表中选择 "租户"，然后在 "订阅名称" 下拉列表中选择 "即用即付"。</span><span class="sxs-lookup"><span data-stu-id="1c627-185">Select tenant from the first dropdown and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="1c627-186">在 "LUIS 资源名称" 下，选择前面在步骤1-5 中创建的资源。</span><span class="sxs-lookup"><span data-stu-id="1c627-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="1c627-187">然后，单击 "分配资源"。</span><span class="sxs-lookup"><span data-stu-id="1c627-187">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="1c627-189">请确保复制并保存与我们刚刚分配的资源相关联的终结点 URL，以便在下一部分可以轻松访问该 URL。</span><span class="sxs-lookup"><span data-stu-id="1c627-189">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="1c627-190">对于租户名称，请将为此应用程序创建的公司或配置文件放入其中。</span><span class="sxs-lookup"><span data-stu-id="1c627-190">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="1c627-191">现在，请在 Unity 中打开新应用，并选择层次结构中的 Lunarcom_Base 对象。</span><span class="sxs-lookup"><span data-stu-id="1c627-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="1c627-192">单击 "检查器" 面板中的 "添加组件"，搜索并选择 "LunarcomIntentRecognizer"。</span><span class="sxs-lookup"><span data-stu-id="1c627-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="1c627-194">在 "检查器" 面板中的 "LunarcomIntentRecognizer" 的 "Luis 终结点" 字段中，输入你在步骤21中保存的终结点 URL。</span><span class="sxs-lookup"><span data-stu-id="1c627-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 21.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="1c627-196">在 "检查器" 面板中的 "LunarcomOfflineRecognizer" 组件中，请确保已为 "SimulateOfflineMode" 选择 "禁用"，否则测试程序将不起作用。</span><span class="sxs-lookup"><span data-stu-id="1c627-196">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="1c627-197">在项目窗口中，导航到 "资产" > "MRTK"。GettingStarted > Prototyping > RocketLauncher 文件夹中，将 RocketLauncher_Complete prefab 拖到 "层次结构" 窗口，并将其放置在 Lunarcom_Base 对象的前面。</span><span class="sxs-lookup"><span data-stu-id="1c627-197">In the Project window, navigate to the Assets > MRTK.Tutorials.GettingStarted > Prefabs > RocketLauncher folder, drag the RocketLauncher_Complete prefab into your Hierarchy window, and position it in front of the Lunarcom_Base object.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing01.png)

25. <span data-ttu-id="1c627-199">在 "层次结构" 窗口中，选择 "Lunarcom_Base" 对象并找到 "Lunarcom 意向识别器（脚本）" 组件，然后展开 "RocketLauncher_Complete" > "按钮对象，并将每个按钮对象分配给相应的农历启动器按钮定义域.</span><span class="sxs-lookup"><span data-stu-id="1c627-199">In the Hierarchy window, select the Lunarcom_Base object and locate the Lunarcom Intent Recognizer (Script) component, then expand the RocketLauncher_Complete > Button object and assign each of the button objects to the corresponding Lunar Launcher Buttons field.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing02.png)

26. <span data-ttu-id="1c627-201">按 Unity 编辑器中的 "播放" 按钮，然后单击 "火箭" 按钮，开始意图识别。</span><span class="sxs-lookup"><span data-stu-id="1c627-201">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="1c627-202">Utter "选择启动火箭" 按钮。</span><span class="sxs-lookup"><span data-stu-id="1c627-202">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="1c627-203">应用已识别所需的函数并激活了 "火箭" 按钮。</span><span class="sxs-lookup"><span data-stu-id="1c627-203">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="1c627-205">祝贺你</span><span class="sxs-lookup"><span data-stu-id="1c627-205">Congratulations</span></span>

<span data-ttu-id="1c627-206">在本课中，您学习了如何添加 AI 功能的语音命令。</span><span class="sxs-lookup"><span data-stu-id="1c627-206">In this lesson, you learned how to add AI-powered speech commands.</span></span> <span data-ttu-id="1c627-207">现在，你的程序可以识别用户的意图，即使它们不 utter 精确的语音命令也是如此！</span><span class="sxs-lookup"><span data-stu-id="1c627-207">Now your program can recognize users' intent, even if they do not utter precise voice commands!</span></span>
