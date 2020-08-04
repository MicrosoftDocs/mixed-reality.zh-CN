---
title: Azure 云教程 - 5. 将 Azure 机器人服务与 LUIS 集成
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现 Azure 机器人服务和自然语言理解。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, hololens 2, azure 机器人服务, luis, 自然语言, 对话机器人
ms.localizationpriority: high
ms.openlocfilehash: daf97cde1477a84c1776a069ec5b8d1a185b63cc
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376449"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="3af9a-105">5.集成 Azure 机器人服务</span><span class="sxs-lookup"><span data-stu-id="3af9a-105">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="3af9a-106">在本教程中，你将了解如何在 HoloLens 2 演示应用程序中使用 Azure 机器人服务添加语言理解 (LUIS)，并让机器人在搜索被跟踪对象时为用户提供帮助  。</span><span class="sxs-lookup"><span data-stu-id="3af9a-106">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="3af9a-107">本教程分为两部分，在第一部分中，使用 [Bot Composer](https://docs.microsoft.com/composer/introduction) 作为无代码解决方案来创建机器人，并快速浏览为机器人提供所需数据的 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="3af9a-107">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="3af9a-108">在第二部分中，在 Unity 项目中使用“BotManager (脚本)”来利用托管的机器人服务。</span><span class="sxs-lookup"><span data-stu-id="3af9a-108">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="3af9a-109">目标</span><span class="sxs-lookup"><span data-stu-id="3af9a-109">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="3af9a-110">第 1 部分</span><span class="sxs-lookup"><span data-stu-id="3af9a-110">Part 1</span></span>

* <span data-ttu-id="3af9a-111">了解有关 Azure 机器人服务的基础知识</span><span class="sxs-lookup"><span data-stu-id="3af9a-111">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="3af9a-112">了解如何使用 Bot Composer 创建机器人</span><span class="sxs-lookup"><span data-stu-id="3af9a-112">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="3af9a-113">了解如何使用 Azure Functions 从 Azure 存储提供数据</span><span class="sxs-lookup"><span data-stu-id="3af9a-113">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="3af9a-114">第 2 部分</span><span class="sxs-lookup"><span data-stu-id="3af9a-114">Part 2</span></span>

* <span data-ttu-id="3af9a-115">了解如何在此项目中设置场景以使用 Azure 机器人服务</span><span class="sxs-lookup"><span data-stu-id="3af9a-115">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="3af9a-116">了解如何通过与机器人交谈来设置和查找对象</span><span class="sxs-lookup"><span data-stu-id="3af9a-116">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="3af9a-117">了解 Azure 机器人服务</span><span class="sxs-lookup"><span data-stu-id="3af9a-117">Understanding Azure Bot Service</span></span>

<span data-ttu-id="3af9a-118">借助 LUIS，Azure 机器人服务让开发人员能够创建与用户进行自然对话的智能机器人 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-118">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="3af9a-119">对话机器人是扩展用户与应用程序交互的方式的好方法。</span><span class="sxs-lookup"><span data-stu-id="3af9a-119">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="3af9a-120">机器人可以充当具有 [QnA Marker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs) 的知识库，借助[语言理解智能服务 (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp) 功能进行复杂的对话。</span><span class="sxs-lookup"><span data-stu-id="3af9a-120">A Bot can act as a knowledge base with a [QnA Marker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp).</span></span>

<span data-ttu-id="3af9a-121">详细了解 [Azure 机器人服务](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0)。</span><span class="sxs-lookup"><span data-stu-id="3af9a-121">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="3af9a-122">第 1 部分 - 创建机器人</span><span class="sxs-lookup"><span data-stu-id="3af9a-122">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="3af9a-123">在 Unity 应用程序中使用机器人之前，必须首先开发机器人，为其提供数据并将其托管在 Azure 上。</span><span class="sxs-lookup"><span data-stu-id="3af9a-123">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="3af9a-124">机器人的目标是能够说出数据库中存储的被跟踪对象数量，通过被跟踪对象的名称进行查找，以及告诉用户关于被跟踪对象的基本信息 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-124">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="3af9a-125">快速了解被跟踪对象 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="3af9a-125">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="3af9a-126">你即将开始创建机器人，但是要使其变得有用，你需要为其提供资源，以便机器人从中拉取数据。</span><span class="sxs-lookup"><span data-stu-id="3af9a-126">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="3af9a-127">由于机器人能够计算被跟踪对象的数量、通过名称查找特定的被跟踪对象以及告知详细信息，因此可使用可以访问 Azure 表存储的简单 Azure Functions 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-127">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="3af9a-128">下载 Azure Functions 项目：[被跟踪对象 Azure Functions](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)</span><span class="sxs-lookup"><span data-stu-id="3af9a-128">Download the Azure Function Project: [Tracked Objects Azure Function](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)</span></span>

<span data-ttu-id="3af9a-129">此 Azure Functions 具有两个操作（Count 和 Find），你可以通过基本的 HTTP GET 调用来调用这两个操作  。</span><span class="sxs-lookup"><span data-stu-id="3af9a-129">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="3af9a-130">可以在 Visual Studio 中检查代码。</span><span class="sxs-lookup"><span data-stu-id="3af9a-130">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="3af9a-131">详细了解 [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="3af9a-131">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="3af9a-132">Count 函数从表存储查询表中的所有 TrackedObject，这非常简单  。</span><span class="sxs-lookup"><span data-stu-id="3af9a-132">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="3af9a-133">另一方面，Find 函数从 GET 请求中获取名称查询参数，并在表存储中查询匹配的 TrackedObject，然后将 DTO 以 JSON 的形式返回  。</span><span class="sxs-lookup"><span data-stu-id="3af9a-133">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="3af9a-134">可以直接从 Visual Studio 部署此 Azure Functions 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-134">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="3af9a-135">在此处查找有关 [Azure Functions 部署](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml)的所有信息。</span><span class="sxs-lookup"><span data-stu-id="3af9a-135">Find here all information regarding [Azure Function deployment](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml).</span></span>

<span data-ttu-id="3af9a-136">完成部署后，在 Azure 门户中，打开相应的资源，然后单击“设置”部分下的“配置” 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-136">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="3af9a-137">在“应用程序设置”上，需要向存储被跟踪对象的 Azure 存储提供连接字符串 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-137">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="3af9a-138">单击“新应用程序设置”，并使用其名称(AzureStorageConnectionString)，然后提供正确的连接字符串作为值。</span><span class="sxs-lookup"><span data-stu-id="3af9a-138">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="3af9a-139">接下来，单击“保存”，现在 Azure Functions 已准备就绪，可以为接下来要创建的机器人提供服务 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-139">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="3af9a-140">创建对话机器人</span><span class="sxs-lookup"><span data-stu-id="3af9a-140">Creating a conversation Bot</span></span>

<span data-ttu-id="3af9a-141">可以通过多种方式来开发基于 Bot Framework 的对话机器人。</span><span class="sxs-lookup"><span data-stu-id="3af9a-141">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="3af9a-142">本课程将使用 [Bot Framework Composer](https://docs.microsoft.com/composer/) 桌面应用程序，该应用程序是非常适合快速开发的可视化设计器。</span><span class="sxs-lookup"><span data-stu-id="3af9a-142">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="3af9a-143">可以从 [Github 存储库](https://github.com/microsoft/BotFramework-Composer/releases)下载最新版本。</span><span class="sxs-lookup"><span data-stu-id="3af9a-143">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="3af9a-144">它适用于 Windows、Mac 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="3af9a-144">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="3af9a-145">安装 Bot Framework Composer 后，启动应用程序，你应该会看到以下界面：</span><span class="sxs-lookup"><span data-stu-id="3af9a-145">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="3af9a-147">你准备了一个机器人构建器项目，可提供本教程所需的对话和触发器。</span><span class="sxs-lookup"><span data-stu-id="3af9a-147">You have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span>
<span data-ttu-id="3af9a-148">下载项目：[Bot Framework Composer 项目](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)</span><span class="sxs-lookup"><span data-stu-id="3af9a-148">Download the project: [Bot Framework Composer project](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)</span></span>

<span data-ttu-id="3af9a-149">在顶部栏上，单击“打开”，然后选择你下载的 Bot Framework 项目，该项目名为 TrackedObjectsBot 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-149">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="3af9a-150">项目完全加载后，你应该会看到项目已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="3af9a-150">After the project is fully loaded, you should see the project ready.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="3af9a-152">让我们集中在左侧，你可以在其中看到“对话框面板”。</span><span class="sxs-lookup"><span data-stu-id="3af9a-152">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="3af9a-153">左侧有一个名为 TrackedObjectsBot 的对话框，你可以在其中看到几个触发器 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-153">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="3af9a-154">详细了解 [Bot Framework 概念](https://docs.microsoft.com/composer/concept-dialog)。</span><span class="sxs-lookup"><span data-stu-id="3af9a-154">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="3af9a-155">这些触发器执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3af9a-155">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="3af9a-156">问候语</span><span class="sxs-lookup"><span data-stu-id="3af9a-156">Greeting</span></span>

<span data-ttu-id="3af9a-157">这是用户发起对话时聊天机器人的入口 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-157">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="3af9a-159">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="3af9a-159">AskingForCount</span></span>

<span data-ttu-id="3af9a-160">当用户要求计算所有被跟踪对象时，将触发此对话。</span><span class="sxs-lookup"><span data-stu-id="3af9a-160">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="3af9a-161">下面是触发短语：</span><span class="sxs-lookup"><span data-stu-id="3af9a-161">These are the trigger phrases:</span></span>

>* <span data-ttu-id="3af9a-162">全部统计</span><span class="sxs-lookup"><span data-stu-id="3af9a-162">count me all</span></span>
>* <span data-ttu-id="3af9a-163">存储的数量</span><span class="sxs-lookup"><span data-stu-id="3af9a-163">how many are stored</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="3af9a-165">借助 [LUIS](https://docs.microsoft.com/composer/how-to-use-luis)，用户不必以这种确切的方式询问短语，从而允许用户进行自然对话 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-165">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="3af9a-166">在此对话中，机器人还将与 Azure Functions 的“Count”对话，稍后再进行详细介绍。</span><span class="sxs-lookup"><span data-stu-id="3af9a-166">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="3af9a-167">未知意向</span><span class="sxs-lookup"><span data-stu-id="3af9a-167">Unknown Intent</span></span>

<span data-ttu-id="3af9a-168">如果来自用户的输入不符合任何其他触发条件，则会触发此对话，并通过再次尝试提问来响应用户。</span><span class="sxs-lookup"><span data-stu-id="3af9a-168">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="3af9a-170">FindEntity</span><span class="sxs-lookup"><span data-stu-id="3af9a-170">FindEntity</span></span>

<span data-ttu-id="3af9a-171">最后一个对话为数据创建分支并将其存储在机器人内存中，因此更加复杂。</span><span class="sxs-lookup"><span data-stu-id="3af9a-171">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="3af9a-172">它要求用户提供被跟踪对象的名称以便了解详细信息、对 Azure Functions 的“Find”执行查询，并使用响应继续进行对话 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-172">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="3af9a-174">如果未找到被跟踪对象，系统将通知用户并结束对话。</span><span class="sxs-lookup"><span data-stu-id="3af9a-174">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="3af9a-175">找到相关的被跟踪对象后，启动程序将检查可用的属性并报告这些属性。</span><span class="sxs-lookup"><span data-stu-id="3af9a-175">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="3af9a-176">调整机器人</span><span class="sxs-lookup"><span data-stu-id="3af9a-176">Adapting the Bot</span></span>

<span data-ttu-id="3af9a-177">AskingForCount 和 FindEntity 触发器需要与后端通信，这意味着必须添加先前部署的 Azure Functions 的正确 URL  。</span><span class="sxs-lookup"><span data-stu-id="3af9a-177">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="3af9a-178">在对话框面板上，单击“AskingForCount”，然后找到“发送 HTTP 请求”操作，你可以在此处看到字段“URL”，在此字段中，需要为 Count 函数终结点更改正确的 URL 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-178">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="3af9a-180">最后，查找 FindEntity 触发器并找到“发送 HTTP 请求”操作，在 URL 字段中将 URL 更改为 Find 函数终结点 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-180">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="3af9a-182">完成所有设置后，现在即可部署机器人。</span><span class="sxs-lookup"><span data-stu-id="3af9a-182">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="3af9a-183">由于你已经安装了 Bot Framework Composer，因此可以直接从此处发布机器人。</span><span class="sxs-lookup"><span data-stu-id="3af9a-183">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="3af9a-184">详细了解[从 Bot Composer 发布机器人](https://docs.microsoft.com/composer/how-to-publish-bot)。</span><span class="sxs-lookup"><span data-stu-id="3af9a-184">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="3af9a-185">通过添加更多触发短语、新响应或对话分支，可以随时与机器人对话。</span><span class="sxs-lookup"><span data-stu-id="3af9a-185">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="3af9a-186">第 2 部分 - 将所有内容整合到 Unity 中</span><span class="sxs-lookup"><span data-stu-id="3af9a-186">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="3af9a-187">准备场景</span><span class="sxs-lookup"><span data-stu-id="3af9a-187">Preparing the scene</span></span>

<span data-ttu-id="3af9a-188">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureCloudServices” > “预制件” > “管理器”文件夹   。</span><span class="sxs-lookup"><span data-stu-id="3af9a-188">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="3af9a-190">从此处将预制件 ChatBotManager 移到场景层次结构中。</span><span class="sxs-lookup"><span data-stu-id="3af9a-190">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="3af9a-191">将 ChatBotManager 添加到场景后，单击“聊天机器人管理器”组件。</span><span class="sxs-lookup"><span data-stu-id="3af9a-191">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="3af9a-192">在“检查器”中，你将看到一个空的“Direct Line 密钥”字段，需要填写该字段。</span><span class="sxs-lookup"><span data-stu-id="3af9a-192">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="3af9a-193">可以从 Azure 门户中检索密钥，方法是查找在本教程的第一部分中创建的“机器人通道注册”类型的资源。</span><span class="sxs-lookup"><span data-stu-id="3af9a-193">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="3af9a-195">现在，将 ChatBotManager 对象与附加到 ChatBotPanel 对象的 ChatBotController 组件连接起来  。</span><span class="sxs-lookup"><span data-stu-id="3af9a-195">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="3af9a-196">在“层次结构”中，选择“ChatBotPanel”，你将看到一个空的“聊天机器人管理器”字段，从“层次结构”将“ChatBotManager”对象拖动到空的“聊天机器人管理器”字段中   。</span><span class="sxs-lookup"><span data-stu-id="3af9a-196">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="3af9a-198">接下来，你需要通过一种方法打开 ChatBotPanel，以便用户可以与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="3af9a-198">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="3af9a-199">在“场景”窗口中，你可能已经注意到，MainMenu 对象上有一个“聊天机器人”侧按钮，可使用该按钮解决此问题。</span><span class="sxs-lookup"><span data-stu-id="3af9a-199">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="3af9a-200">在“层次结构”中，找到“RootMenu” > “MainMenu” > “SideButtonCollection” > “ButtonChatBot”，然后在“检查器”中找到“ButtonConfigHelper”脚本   。</span><span class="sxs-lookup"><span data-stu-id="3af9a-200">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="3af9a-201">在那里，你将在 OnClick() 事件回调中看到一个空槽。</span><span class="sxs-lookup"><span data-stu-id="3af9a-201">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="3af9a-202">将 ChatBotPanel 拖放到事件槽，从下拉列表中导航到 GameObject，然后在子菜单中选择“SetActive (bool)”并启用复选框 。</span><span class="sxs-lookup"><span data-stu-id="3af9a-202">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="3af9a-204">现在，可以从主菜单启动聊天机器人，并可以使用场景了。</span><span class="sxs-lookup"><span data-stu-id="3af9a-204">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="3af9a-205">对机器人进行测试</span><span class="sxs-lookup"><span data-stu-id="3af9a-205">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="3af9a-206">询问被跟踪对象的数量</span><span class="sxs-lookup"><span data-stu-id="3af9a-206">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="3af9a-207">首先测试如何向机器人询问在数据库中存储的被跟踪对象的数量。</span><span class="sxs-lookup"><span data-stu-id="3af9a-207">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="3af9a-208">这一次必须从 HoloLens 2 运行应用程序，因为你的系统上可能无法使用文本转语音等服务。</span><span class="sxs-lookup"><span data-stu-id="3af9a-208">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="3af9a-209">在 HoloLens 2 上运行应用程序，然后单击主菜单旁边的“聊天机器人”按钮。</span><span class="sxs-lookup"><span data-stu-id="3af9a-209">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="3af9a-210">机器人会问候你，现在询问它“我们有多少个对象？”</span><span class="sxs-lookup"><span data-stu-id="3af9a-210">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="3af9a-211">机器人应会告诉你数量并结束对话。</span><span class="sxs-lookup"><span data-stu-id="3af9a-211">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="3af9a-212">询问被跟踪对象</span><span class="sxs-lookup"><span data-stu-id="3af9a-212">Asking about a tracked object</span></span>

<span data-ttu-id="3af9a-213">现在再次运行应用程序，这次让机器人“查找被跟踪对象”，机器人将询问你名称，你应回答“汽车”或者数据库中已知的其他被跟踪对象的名称。</span><span class="sxs-lookup"><span data-stu-id="3af9a-213">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="3af9a-214">机器人将告诉你详细信息，例如描述以及是否分配了空间定位点。</span><span class="sxs-lookup"><span data-stu-id="3af9a-214">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="3af9a-215">尝试询问不存在的被跟踪对象，并了解机器人的响应方式。</span><span class="sxs-lookup"><span data-stu-id="3af9a-215">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="3af9a-216">祝贺</span><span class="sxs-lookup"><span data-stu-id="3af9a-216">Congratulations</span></span>

<span data-ttu-id="3af9a-217">在本教程中，你了解了如何通过自然语言对话，使用 Azure Bot Framework 与应用程序进行交互。</span><span class="sxs-lookup"><span data-stu-id="3af9a-217">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="3af9a-218">你了解了如何开发自己的机器人，以及使机器人正常运行的移动组件。</span><span class="sxs-lookup"><span data-stu-id="3af9a-218">You learned how to develope your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="3af9a-219">结论</span><span class="sxs-lookup"><span data-stu-id="3af9a-219">Conclusion</span></span>

<span data-ttu-id="3af9a-220">在整个本系列教程中，你体验了 Azure 云服务如何为应用程序引入令人兴奋的新功能。</span><span class="sxs-lookup"><span data-stu-id="3af9a-220">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="3af9a-221">现在，你可以使用 Azure 存储将数据和图像存储在云中、使用 Azure 自定义视觉关联图像和训练模型、使用 Azure 空间定位点将对象引入本地上下文，以及实现由 LUIS 提供支持的 Azure Bot Framework，以添加对话式机器人，从而形成新的自然语言交互模式   。</span><span class="sxs-lookup"><span data-stu-id="3af9a-221">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
