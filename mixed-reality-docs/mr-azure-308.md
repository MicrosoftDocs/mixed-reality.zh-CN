---
title: MR 以及 Azure 308 的跨设备通知
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 通知中心、 Azure Functions 和 Azure 存储和表。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 通知、 函数、 表、 通知中心，沉浸式、 hololens、 vr
ms.openlocfilehash: ed56c936a0498b6e0ac804da15a2c6ec98239d0c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593004"
---
>[!NOTE]
><span data-ttu-id="d4c9b-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d4c9b-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d4c9b-106">这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d4c9b-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d4c9b-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d4c9b-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="d4c9b-110">MR 和 Azure 308:跨设备通知</span><span class="sxs-lookup"><span data-stu-id="d4c9b-110">MR and Azure 308: Cross-device notifications</span></span>

![最终产品-启动](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="d4c9b-112">在本课程中，您将学习如何将通知中心功能添加到使用 Azure 通知中心、 Azure 表和 Azure Functions 的混合的现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="d4c9b-113">**Azure 通知中心**是 Microsoft 服务，这样，开发人员将有针对性的个性化推送通知发送到任何平台上，所有这些都在云中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="d4c9b-114">这可以有效地允许开发人员与最终用户进行通信或甚至各种应用程序，具体取决于方案之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="d4c9b-115">有关详细信息，请访问**Azure 通知中心**[页面](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="d4c9b-116">**Azure Functions**是一个 Microsoft 服务，它允许开发人员运行小段代码，函数，在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="d4c9b-117">这使您能够将工作委托给云，而不是本地应用程序，它可以有许多好处。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="d4c9b-118">**Azure Functions**支持多种开发语言，包括 C\#，F\#，Node.js、 Java 和 PHP。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="d4c9b-119">有关详细信息，请访问**Azure Functions** [页面](https://docs.microsoft.com/azure/azure-functions/functions-overview)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="d4c9b-120">**Azure 表**一个 Microsoft 云服务，它允许开发人员能够在云中存储结构化非 SQL 数据，使其可以轻松访问任意位置。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="d4c9b-121">该服务实现了无架构设计，根据需要允许为表的演变，因此非常灵活。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="d4c9b-122">有关详细信息，请访问**Azure 表**[页](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="d4c9b-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="d4c9b-123">已完成本课程，将具有混合的现实耳机沉浸式应用程序中和一个桌面 PC 应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="d4c9b-124">桌面 PC 应用程序将允许用户在 2D 空间 （X 和 Y） 中移动对象使用鼠标。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="d4c9b-125">移动 PC 应用程序内的对象将发送到云使用 JSON，这将以字符串的形式，其中包含的对象 ID，类型和转换 （X 和 Y 坐标） 的信息。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="d4c9b-126">从通知中心服务 （这只是已通过台式计算机应用更新），混合的现实应用，具有到桌面应用程序相同的场景，将收到有关对象移动的通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="d4c9b-127">收到通知，它将包含对象 ID、 类型和转换的信息，mixed 的 reality 应用将向其自身场景应用收到的信息。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="d4c9b-128">在您的应用程序，它是取决于您关于如何将与您的设计集成结果。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="d4c9b-129">本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="d4c9b-130">它是作业以使用此课程以增强混合的现实应用程序中获取的知识。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="d4c9b-131">此过程是不直接涉及任何其他混合现实实验室的自包含的教程。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="d4c9b-132">设备支持</span><span class="sxs-lookup"><span data-stu-id="d4c9b-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d4c9b-133">课程</span><span class="sxs-lookup"><span data-stu-id="d4c9b-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d4c9b-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d4c9b-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d4c9b-135"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="d4c9b-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d4c9b-136">MR 和 Azure 308:跨设备通知</span><span class="sxs-lookup"><span data-stu-id="d4c9b-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="d4c9b-137">✔️</span><span class="sxs-lookup"><span data-stu-id="d4c9b-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d4c9b-138">✔️</span><span class="sxs-lookup"><span data-stu-id="d4c9b-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="d4c9b-139">尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="d4c9b-140">按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="d4c9b-141">使用 HoloLens，您可能注意到某些 echo 语音捕获过程。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4c9b-142">系统必备</span><span class="sxs-lookup"><span data-stu-id="d4c9b-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="d4c9b-143">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="d4c9b-144">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="d4c9b-145">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.</span><span class="sxs-lookup"><span data-stu-id="d4c9b-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="d4c9b-146">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="d4c9b-147">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="d4c9b-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="d4c9b-148">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="d4c9b-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d4c9b-149">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="d4c9b-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d4c9b-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="d4c9b-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d4c9b-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d4c9b-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="d4c9b-152">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="d4c9b-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="d4c9b-153">为 Azure 设置和访问通知中心的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="d4c9b-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="d4c9b-154">开始之前</span><span class="sxs-lookup"><span data-stu-id="d4c9b-154">Before you start</span></span>

- <span data-ttu-id="d4c9b-155">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="d4c9b-156">您必须是 Microsoft 开发人员门户和你的应用程序注册门户的所有者，否则不会有权访问的应用程序中[第 2 章](#chapter-2---retrieve-your-new-apps-credentials)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="d4c9b-157">第 1 章-Microsoft 开发人员门户中创建应用程序</span><span class="sxs-lookup"><span data-stu-id="d4c9b-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="d4c9b-158">若要使用**Azure 通知中心**服务，你将需要创建应用程序在 Microsoft 开发人员门户中，因为你的应用程序将需要进行注册，以便它可以发送和接收通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="d4c9b-159">登录到[Microsoft 开发人员门户](https://developer.microsoft.com/dashboard)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="d4c9b-160">你将需要登录到你的 Microsoft 帐户。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="d4c9b-161">从仪表板，单击**创建新的应用**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-161">From the Dashboard, click **Create a new app**.</span></span>

    ![创建应用](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="d4c9b-163">将出现一个弹出窗口，其中需要以保留新应用的名称。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="d4c9b-164">在文本框中，插入适当的名称;如果选择的名称不可用，刻度线将显示右侧的文本框中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="d4c9b-165">插入的可用名称后，单击**保留产品名称**弹出框的左下角的按钮。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![反向名称](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="d4c9b-167">现在创建的应用程序，已准备好移动到下一章。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="d4c9b-168">第 2-章中检索新的应用凭据</span><span class="sxs-lookup"><span data-stu-id="d4c9b-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="d4c9b-169">登录到应用程序注册门户，其中新应用程序将列出和检索的凭据将用于记录的安装程序**通知中心服务**内**Azure 门户**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="d4c9b-170">导航到[应用程序注册门户](http://apps.dev.microsoft.com)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![应用程序注册门户](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="d4c9b-172">需要使用你的 Microsoft 帐户登录。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="d4c9b-173">这**必须**是在以前使用 Microsoft 帐户[章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)，与 Windows 应用商店开发人员门户。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="d4c9b-174">您会发现您的应用程序下**我的应用程序**部分。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="d4c9b-175">找到它后, 单击它，将转到新页面具有的应用名加上**注册**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![新注册的应用](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="d4c9b-177">向下注册页面以查找滚动你**应用程序机密**部分并**程序包 SID**为你的应用。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="d4c9b-178">复制用于设置**Azure 通知中心服务**中下一章。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![应用程序机密](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="d4c9b-180">章节 3-安装 Azure 门户： 创建通知中心服务</span><span class="sxs-lookup"><span data-stu-id="d4c9b-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="d4c9b-181">使用你的应用的凭据检索到，你将需要转到 Azure 门户中，将在其中创建 Azure 通知中心服务。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="d4c9b-182">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="d4c9b-183">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="d4c9b-184">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="d4c9b-185">你登录后，单击**新建**在左上角，并搜索**通知中心**，然后单击***Enter***。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![通知中心的搜索](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="d4c9b-187">单词***新建***可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="d4c9b-188">该新页面将提供的说明*通知中心*服务。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="d4c9b-189">在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![创建通知中心实例](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="d4c9b-191">一旦你单击***创建***:</span><span class="sxs-lookup"><span data-stu-id="d4c9b-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="d4c9b-192">插入此服务实例所需的名称。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="d4c9b-193">提供**命名空间**其中你将能够将与此应用相关联。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="d4c9b-194">选择**位置。**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="d4c9b-195">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="d4c9b-196">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="d4c9b-197">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="d4c9b-198">如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="d4c9b-199">选择相应**订阅**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="d4c9b-200">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="d4c9b-201">选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-201">Select **Create**.</span></span>

        ![服务详细信息中填充](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="d4c9b-203">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="d4c9b-204">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![通知](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="d4c9b-206">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="d4c9b-207">你将会转到新**通知中心**服务实例。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![转到资源](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="d4c9b-209">从概述页中，中途页上，单击**Windows (WNS)。**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="d4c9b-210">在右侧面板将更改为显示两个文本字段，这需要你**程序包 SID**并**安全密钥**，从以前设置的应用。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![新创建的中心服务](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="d4c9b-212">一旦到了正确的字段复制的详细信息，请单击**保存**，并已成功更新通知中心时，你将收到通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![复制安全的详细信息](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="d4c9b-214">章 4-设置 Azure 门户： 创建表服务</span><span class="sxs-lookup"><span data-stu-id="d4c9b-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="d4c9b-215">创建通知中心服务实例后，导航回到 Azure 门户中，您将创建的存储资源创建 Azure 表服务。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="d4c9b-216">如果尚未登录，登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="d4c9b-217">登录后，单击**新建**在左上角，并搜索**存储帐户**，然后单击**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="d4c9b-218">单词***新建***可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="d4c9b-219">选择**存储帐户-blob、 文件、 表、 队列**从列表中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![搜索存储帐户](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="d4c9b-221">该新页面将提供的说明**存储帐户**服务。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="d4c9b-222">在左下角此提示符下，选择**创建**按钮，创建此服务的实例。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![创建存储实例](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="d4c9b-224">一旦你单击**创建**，将显示一个面板：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="d4c9b-225">插入所需**名称**（必须全部小写） 此服务实例。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="d4c9b-226">有关**部署模型**，单击**资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="d4c9b-227">有关**帐户类型**，使用下拉列表菜单，选择**存储 (常规用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="d4c9b-228">选择相应**位置**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="d4c9b-229">有关**复制**下拉列表菜单中，选择**读取-访问-异地冗余存储 (RA-GRS)**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="d4c9b-230">有关**性能**，单击**标准**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="d4c9b-231">内**需要安全传输**部分中，选择**禁用**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="d4c9b-232">从**订阅**下拉菜单中，选择相应的订阅。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="d4c9b-233">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="d4c9b-234">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="d4c9b-235">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="d4c9b-236">如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="d4c9b-237">将保留**虚拟网络**作为**禁用**如果这是为你的选项。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="d4c9b-238">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-238">Click **Create**.</span></span>

        ![填写存储详细信息](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="d4c9b-240">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="d4c9b-241">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="d4c9b-242">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-242">Click on the notifications to explore your new Service instance.</span></span>

    ![新的存储通知](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="d4c9b-244">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="d4c9b-245">你将转到新的存储服务实例概述页。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![转到资源](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="d4c9b-247">从概述页上，到右侧，单击**表**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="d4c9b-248">在右侧面板将更改为显示**表服务**其中所需添加一个新表的信息。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="d4c9b-249">执行此操作通过单击**+** **表**左上角的按钮。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![打开表](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="d4c9b-251">将显示一个新页面，其中你需要输入**表名称**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="d4c9b-252">这是将用于指代应用程序中后面的章节中的数据的名称。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="d4c9b-253">插入适当的名称，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-253">Insert an appropriate name and click **OK**.</span></span>

    ![创建新表](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="d4c9b-255">一旦创建新表后，你将能够看到它在**表服务**页 （底部）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![创建新表](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="d4c9b-257">第 5 章-完成 Visual Studio 中的 Azure 表</span><span class="sxs-lookup"><span data-stu-id="d4c9b-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="d4c9b-258">现在，你**表服务**存储帐户已被安装程序，即可将数据添加到它，将用于存储和检索信息。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="d4c9b-259">编辑你的表，可通过完成**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="d4c9b-260">打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="d4c9b-261">从菜单中，单击**视图 > 云资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-261">From the menu, click **View > Cloud Explorer**.</span></span>

    ![打开 cloud explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="d4c9b-263">**云资源管理器**以停靠项 （如加载可能需要时间，则请耐心等待，） 将打开。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="d4c9b-264">如果用于创建订阅你*存储帐户*不可见，请确保您具有：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="d4c9b-265">登录到 Azure 门户使用的同一个帐户。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="d4c9b-266">（您可能需要从你的帐户设置应用筛选器） 在帐户管理页上选择你的订阅：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![查找订阅](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="d4c9b-268">将显示在 Azure 云服务。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="d4c9b-269">查找**存储帐户**，然后单击箭头以展开你的帐户的左侧。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![打开存储帐户](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="d4c9b-271">展开后，新创建**存储帐户**应可用。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="d4c9b-272">单击你的存储，左侧的箭头，然后后，已展开，找到**表**，然后单击箭头旁边的以显示**表**在最后一章中创建。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="d4c9b-273">双击您**表**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-273">Double click your **Table**.</span></span>

    ![打开的场景对象表](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="d4c9b-275">将在 Visual Studio 窗口的中心中打开您的表。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="d4c9b-276">单击与表图标**+** （加上） 在其上。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![添加新表](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="d4c9b-278">你能够将出现一个窗口提示*添加实体*。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="d4c9b-279">总的来说，每个都有多个属性，将创建三个实体。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="d4c9b-280">您会注意*PartitionKey*并*RowKey*已提供了，因为需要使用这些表以查找你的数据。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![分区键和行键](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="d4c9b-282">更新*值*的**PartitionKey**和**RowKey** ，如下所示 (请记住，若要执行此操作的每个行属性添加，但每次递增 RowKey):</span><span class="sxs-lookup"><span data-stu-id="d4c9b-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![添加正确的值](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="d4c9b-284">单击**将属性添加**添加额外的数据行。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="d4c9b-285">使匹配在第一个空表下表。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="d4c9b-286">单击**确定**完成之后。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-286">Click **OK** when you are finished.</span></span>

    ![完成后单击确定](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="d4c9b-288">确保您已更改**类型**的**X**， **Y**，以及**Z**，条目**Double**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="d4c9b-289">您会注意到您的表现在具有一行数据。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="d4c9b-290">单击**+** （+） 图标重新添加另一个实体。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![第一行](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="d4c9b-292">创建附加属性，并设置新的实体，以匹配下面所示的值。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![添加多维数据集](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="d4c9b-294">重复最后一个步骤以添加另一个实体。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="d4c9b-295">将此实体的值设置为下面所示。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-295">Set the values for this entity to those shown below.</span></span>

    ![添加圆柱图](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="d4c9b-297">您的表现在应类似于下面所示。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-297">Your table should now look like the one below.</span></span>

    ![完整的表](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="d4c9b-299">已完成这一章。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-299">You have completed this Chapter.</span></span> <span data-ttu-id="d4c9b-300">请务必保存。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="d4c9b-301">章 6-创建 Azure Function App</span><span class="sxs-lookup"><span data-stu-id="d4c9b-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="d4c9b-302">创建一个 Azure Function App，若要更新的桌面应用程序将调用**表**服务，并发送通过通知**通知中心**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="d4c9b-303">首先，需要创建一个文件，将允许您的 Azure 函数以加载所需的库。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="d4c9b-304">打开**记事本**（按 Windows 键和类型记事本）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![打开记事本](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="d4c9b-306">使用记事本打开，将插入到其中的以下 JSON 结构。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="d4c9b-307">完成后，将其保存为您的桌面上**project.json**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="d4c9b-308">非常重要的是正确的命名： 确保与其**不具有.txt**文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="d4c9b-309">此文件定义的库将使用你的函数，如果你已使用 NuGet 将很熟悉。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="d4c9b-310">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="d4c9b-311">你登录后，单击**新建**在左上角，并搜索**Function App**，按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![搜索函数应用](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="d4c9b-313">单词**新建**可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="d4c9b-314">该新页面将提供的说明**Function App**服务。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="d4c9b-315">在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![function app 实例](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="d4c9b-317">一旦你单击**创建**，填写以下：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="d4c9b-318">有关**应用名称**，插入此服务实例所需的名称。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="d4c9b-319">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="d4c9b-320">选择定价层适合你，如果这是首次创建**Function App 服务**，应可供你免费层。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="d4c9b-321">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="d4c9b-322">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="d4c9b-323">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="d4c9b-324">如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="d4c9b-325">有关**OS**，单击 Windows，因为这是预期的平台。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="d4c9b-326">选择**托管计划**(使用本教程**消耗计划**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="d4c9b-327">选择**位置** **（上一步中选择与已生成的存储相同的位置）**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="d4c9b-328">有关**存储**部分中，**必须选择在上一步中创建的存储服务**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="d4c9b-329">您不需要*Application Insights*在此应用中，所以请随意将其留**关闭**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="d4c9b-330">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-330">Click **Create**.</span></span>

        ![创建新的实例](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="d4c9b-332">一旦你单击**创建**必须要等待的时间来创建服务，这可能需要一分钟的时间。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="d4c9b-333">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新的通知](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="d4c9b-335">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="d4c9b-336">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![转到资源](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="d4c9b-338">单击**+** （加号） 旁边的图标*函数*到*新建*。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![添加新函数](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="d4c9b-340">在中间面板**函数**创建窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="d4c9b-341">忽略在面板的上半部分中的信息，并单击**自定义函数**，位于底部 （在蓝色区域，如下所示）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![自定义函数](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="d4c9b-343">在窗口中的新页面将显示各种函数类型。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="d4c9b-344">向下滚动以查看紫色类型，并单击**HTTP PUT**元素。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![http put 链接](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="d4c9b-346">可能需要进一步向下滚动一页 （和此映像可能不尽相同，如果 Azure 门户更新发生），但是，要查找名为的元素*HTTP PUT*。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="d4c9b-347">**HTTP PUT**窗口将显示，需要配置函数 （请参阅下面的图像）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="d4c9b-348">有关**语言中，** 使用下拉列表菜单中，选择 C\#。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="d4c9b-349">有关**名称，** 输入适当的名称。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="d4c9b-350">在中**身份验证级别**下拉列表菜单中，选择**函数**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="d4c9b-351">有关**表名称**部分中，您需要使用的确切名称，用于创建你**表**服务之前 （包括相同的字母大小写）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="d4c9b-352">内**存储帐户连接**部分中，使用下拉列表菜单，并从此处选择你的存储帐户。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="d4c9b-353">如果不存在，单击**新建**与节标题，以显示另一个面板，其中应列出你的存储帐户的超链接。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![新的存储](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="d4c9b-355">单击**创建**，您将收到通知已成功更新你的设置。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![创建函数](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="d4c9b-357">单击后**创建**，你将重定向到在函数编辑器。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![更新函数代码](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="d4c9b-359">（替换函数中的代码） 在函数编辑器中插入以下代码：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="d4c9b-360">使用包含的库，该函数收到的名称和位置被移动的对象的 Unity 场景中 (作为C#对象，调用**UnityGameObject**)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="d4c9b-361">然后使用此对象来更新对象参数中创建的表。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="d4c9b-362">接着，该函数将为你创建的通知中心服务，这将告知所有已订阅的应用程序调用。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="d4c9b-363">使用的代码中的位置，单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="d4c9b-364">接下来，单击**\<** （箭头） 图标，在页面的右侧。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![打开上传面板](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="d4c9b-366">一个面板，将从右侧滑中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-366">A panel will slide in from the right.</span></span> <span data-ttu-id="d4c9b-367">在该面板中，单击**上传**，并且将显示文件浏览器。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="d4c9b-368">导航到，然后单击， **project.json**中创建的文件**记事本**以前，然后单击**打开**按钮。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="d4c9b-369">此文件定义函数将使用的库。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-369">This file defines the libraries that your function will use.</span></span>

    ![上传 json](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="d4c9b-371">当完成上传文件时，它会在右侧面板中显示。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="d4c9b-372">单击它即可打开它内**函数**编辑器。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="d4c9b-373">它必须看起来**完全**（下面步骤 23） 的下一步映像相同。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="d4c9b-374">然后，在左侧面板下方**函数**，单击**集成**链接。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![将集成函数](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="d4c9b-376">在下一页上，在右上角，单击**高级的编辑器**（如下所示）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![打开高级编辑器](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="d4c9b-378">一个**function.json**文件将在中心窗格中，需要替换为以下代码片段中打开。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="d4c9b-379">这将定义要生成的函数和参数传递到函数。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="d4c9b-380">你的编辑器现在应类似于下图中所示：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-380">Your editor should now look like the image below:</span></span>

    ![返回到标准编辑器](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="d4c9b-382">您可能注意到你刚插入的输入的参数可能与你表和存储的详细信息不匹配，因此将需要使用你的信息进行更新。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="d4c9b-383">**不这样做此处**，如接下来介绍了。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="d4c9b-384">只需单击**标准编辑器**链接，可在页上，若要返回的右上角。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="d4c9b-385">回到**标准编辑器**，单击**Azure 表存储 （表）** 下**输入**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![表输入](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="d4c9b-387">确保与以下匹配**你**信息，因为它们可能是不同 （不存在以下步骤的下面的图像）：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="d4c9b-388">**表名**： 你的 Azure 存储，表服务中创建的表的名称。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="d4c9b-389">**存储帐户连接：** 单击**新**、 将显示此旁的下拉列表菜单，和一个面板将显示在窗口右侧。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![新的存储](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="d4c9b-391">选择你**存储帐户**，到主机之前创建**函数应用。**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="d4c9b-392">您会注意**存储帐户**创建连接值。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="d4c9b-393">请务必按**保存**完成后。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="d4c9b-394">**输入**页现在应与下面显示**您**信息。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![输入完成](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="d4c9b-396">接下来，单击**Azure 通知中心 （通知）** -下**输出**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="d4c9b-397">请确保以下与匹配**你**信息，因为它们可能是不同 （不存在以下步骤的下面的图像）：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="d4c9b-398">**通知中心名称**： 这是名称你**通知中心**之前创建的服务实例。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="d4c9b-399">**通知中心命名空间连接**： 单击**新**，该下拉列表菜单一起出现。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![检查输出](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="d4c9b-401">**连接**弹出窗口将显示 （请参阅下图所示），您需要选择**Namespace**的**通知中心**，以前设置的。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="d4c9b-402">选择你**通知中心**中间的下拉列表菜单中的名称。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="d4c9b-403">设置**策略**下拉列表菜单**DefaultFullSharedAccessSignature**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="d4c9b-404">单击**选择**按钮可返回。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-404">Click the **Select** button to go back.</span></span>

        ![输出更新](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="d4c9b-406">**输出**页现在应与下面，但与**您**信息改为。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="d4c9b-407">请务必按**保存**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="d4c9b-408">*不要直接编辑的通知中心名称*(这应完成使用**高级编辑器**、 提供正确地按照前面的步骤。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![完整的输出](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="d4c9b-410">此时，应测试函数，以确保它正在运行。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="d4c9b-411">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-411">To do this:</span></span> 

    1. <span data-ttu-id="d4c9b-412">一次导航到函数页：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-412">Navigate to the function page once more:</span></span>

        ![完整的输出](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="d4c9b-414">返回在函数页上，单击**测试**页面上，以打开最右侧的选项卡*测试*边栏选项卡：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![完整的输出](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="d4c9b-416">内**请求正文**文本框的边栏选项卡上，粘贴以下代码：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="d4c9b-417">测试代码，然后单击**运行**按钮，位于靠下右对齐，并测试将会运行。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="d4c9b-418">测试的输出日志显示在控制台区域中，下面的函数代码。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![完整的输出](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="d4c9b-420">如果上述测试失败，则需要仔细检查确实如此，遵循上述步骤尤其是中的设置**集成面板**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="d4c9b-421">第 7 章 — 设置桌面 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="d4c9b-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4c9b-422">桌面应用程序，现在要创建，**将不会**在 Unity 编辑器中工作。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="d4c9b-423">它需要外部编辑器，按照使用 Visual Studio 的应用程序 （或已部署的应用程序） 的生成运行。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="d4c9b-424">以下是一组典型使用 Unity 进行开发和混合的现实，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="d4c9b-425">设置和测试您的混合的现实沉浸式头戴式。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="d4c9b-426">你将**不**此课程需要运动控制器。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="d4c9b-427">如果你需要支持沉浸式头戴式设置，请遵循此[k 了解如何设置 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="d4c9b-428">打开**Unity**然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-428">Open **Unity** and click **New**.</span></span>

    ![新的 unity 项目](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="d4c9b-430">需要提供 Unity 项目名称，插入**UnityDesktopNotifHub**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="d4c9b-431">请确保项目类型设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="d4c9b-432">设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="d4c9b-433">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-433">Then, click **Create project**.</span></span>

    ![创建项目](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="d4c9b-435">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="d4c9b-436">转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-436">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="d4c9b-437">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="d4c9b-438">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-438">Close the **Preferences** window.</span></span>

    ![组外部的 VS 工具](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="d4c9b-440">接下来，请转到**文件 > 生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-440">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![交换机平台](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="d4c9b-442">在仍处于**文件 > 生成设置**，请确保：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-442">While still in **File > Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="d4c9b-443">**设备为目标**设置为**任一设备**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="d4c9b-444">此应用程序将为您的桌面，因此必须**任一设备**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="d4c9b-445">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="d4c9b-446">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="d4c9b-447">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="d4c9b-448">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="d4c9b-449">在此，仪表是值得保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="d4c9b-450">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="d4c9b-451">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-451">A save window will appear.</span></span>

            ![添加打开场景](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="d4c9b-453">创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新的场景文件夹](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="d4c9b-455">打开新建**场景**文件夹，然后在**文件名：** 文本字段中，键入**NH\_桌面\_场景**，然后按**保存**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![新 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="d4c9b-457">中的剩余设置，**生成设置**，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="d4c9b-458">在同一窗口中单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="d4c9b-459">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="d4c9b-460">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="d4c9b-461">**脚本运行时版本**应为**实验 （.NET 4.6 等效）**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="d4c9b-462">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="d4c9b-463">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![4.6 的.net 版本](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="d4c9b-465">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="d4c9b-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-466">**InternetClient**</span></span>

            ![刻度线 internet 客户端](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="d4c9b-468">回到**生成设置** *Unity C\#项目*不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="d4c9b-469">关闭**生成设置**窗口。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="d4c9b-470">保存您的场景和项目 \**文件 > 保存场景*/ \* 文件 > 保存项目 \* \*。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-470">Save your Scene and Project \**File > Save Scene* / \*File > Save Project\*\*.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d4c9b-471">如果你想要跳过*Unity 设置*组件为此项目 （桌面应用），并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="d4c9b-472">你将需要添加脚本组件。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="d4c9b-473">第 8 章-导入 Unity 中的 Dll</span><span class="sxs-lookup"><span data-stu-id="d4c9b-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="d4c9b-474">您将使用 Azure 存储于 Unity （其本身使用.Net 的 Azure SDK）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="d4c9b-475">有关详细信息，请遵循此[有关 Unity 的 Azure 存储链接](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="d4c9b-476">这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="d4c9b-477">这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="d4c9b-478">若要导入您自己的项目的 SDK，请确保已下载最新[ **.unitypackage** ](https://aka.ms/azstorage-unitysdk)从 GitHub。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="d4c9b-479">然后，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-479">Then, do the following:</span></span>

1.  <span data-ttu-id="d4c9b-480">添加 **.unitypackage**到使用 Unity**资产\>导入包\>自定义包**菜单选项。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="d4c9b-481">在中**导入 Unity 程序包**框，弹出，你可以选择下的所有内容 \* \**插件* \> \* 存储 \* \* \*。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="d4c9b-482">取消选中其他任何内容，因为它不需要此课程。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![导入包](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="d4c9b-484">单击***导入***按钮将项添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="d4c9b-485">转到**存储**下的文件夹**插件**项目中查看并选择以下插件*仅*:</span><span class="sxs-lookup"><span data-stu-id="d4c9b-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="d4c9b-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="d4c9b-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="d4c9b-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="d4c9b-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="d4c9b-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="d4c9b-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="d4c9b-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="d4c9b-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="d4c9b-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="d4c9b-490">System.Spatial</span></span>

![取消选中任何平台](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="d4c9b-492">与*这些特定插件*选择，**取消选中** **Any 平台**并**取消选中** **WSAPlayer**然后单击**应用**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![应用平台 dll](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="d4c9b-494">我们将会使这些特定的插件，只使用在 Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="d4c9b-495">这是因为存在不同版本的项目会导出从 Unity 后，将使用 WSA 文件夹中的同一个插件。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="d4c9b-496">在中**存储**插件文件夹中，只选择：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="d4c9b-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="d4c9b-497">Microsoft.Data.Services.Client</span></span>

        ![组不处理的 dll](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="d4c9b-499">检查**不进程**框下**平台设置**然后单击***应用***。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![应用不会进行处理](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="d4c9b-501">我们会将标记此插件"不处理"，因为 Unity 程序集 patcher 有处理此插件的难度。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="d4c9b-502">即使未处理，该插件仍将起作用。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="d4c9b-503">章 9-桌面 Unity 项目中创建 TableToScene 类</span><span class="sxs-lookup"><span data-stu-id="d4c9b-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="d4c9b-504">现在需要创建包含要运行此应用程序的代码的脚本。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="d4c9b-505">您需要创建的第一个脚本是**TableToScene**，负责：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="d4c9b-506">读取 Azure 表中的实体。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="d4c9b-507">使用表数据，确定哪些对象来生成，以及在哪个位置。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="d4c9b-508">若要创建所需的第二个脚本是**CloudScene**，负责：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="d4c9b-509">正在注册左键单击事件，以允许用户拖动对象周围场景。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="d4c9b-510">序列化对象数据从此 Unity 场景中，并将其发送到 Azure Function App。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="d4c9b-511">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-511">To create this class:</span></span>

1.  <span data-ttu-id="d4c9b-512">在中右击**资产**文件夹中项目面板中，位于**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-512">Right-click in the **Asset** Folder located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="d4c9b-513">将文件夹命名为**脚本**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-513">Name the folder **Scripts**.</span></span>

    ![创建脚本的文件夹](images/AzureLabs-Lab8-66.png)

    ![创建脚本文件夹 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="d4c9b-516">双击刚创建的文件夹，以将其打开。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="d4c9b-517">内右击**脚本**文件夹中，单击**创建** **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-517">Right-click inside the **Scripts** folder, click **Create** **C\# Script**.</span></span> <span data-ttu-id="d4c9b-518">脚本命名为**TableToScene**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="d4c9b-519">![新的 c# 脚本](images/AzureLabs-Lab8-68.png)
    ![TableToScene 重命名](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="d4c9b-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="d4c9b-520">双击要在 Visual Studio 2017 中打开它的脚本。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="d4c9b-521">添加以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="d4c9b-522">在类中，插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="d4c9b-523">Substitute **accountName**值与你的 Azure 存储服务名称和**accountKey**值与在 Azure 门户 （请参阅下图） 中的 Azure 存储服务中找到的密钥值。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![提取帐户密钥](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="d4c9b-525">现在，添加**start （)** 并**Awake()** 初始化类的方法。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="d4c9b-526">内**TableToScene**类中，添加将从 Azure 表中检索值并使用它们来生成场景中的相应基元的方法。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="d4c9b-527">外侧**TableToScene**类，您需要定义应用程序用于序列化和反序列化的类**表实体**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="d4c9b-528">请确保您**保存**之前追溯到 Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="d4c9b-529">单击**Main Camera**从**层次结构**面板中，以便其属性将显示在**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="d4c9b-530">与**脚本**文件夹中打开，选择的脚本**TableToScene 文件**并将其拖动到**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="d4c9b-531">结果应如下所示：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-531">The result should be as below:</span></span>

    ![将脚本添加到主照相机](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="d4c9b-533">章 10-在桌面 Unity 项目中创建 CloudScene 类</span><span class="sxs-lookup"><span data-stu-id="d4c9b-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="d4c9b-534">若要创建所需的第二个脚本是**CloudScene**，负责：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="d4c9b-535">正在注册左键单击事件，以允许用户拖动对象周围场景。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="d4c9b-536">序列化对象数据从此 Unity 场景中，并将其发送到 Azure Function App。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="d4c9b-537">若要创建第二个脚本：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-537">To create the second script:</span></span>

1.  <span data-ttu-id="d4c9b-538">内右击**脚本**文件夹中，单击**创建**， **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="d4c9b-539">脚本命名为**CloudScene**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="d4c9b-540">![新的 c# 脚本](images/AzureLabs-Lab8-72.png)
    ![重命名 CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="d4c9b-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="d4c9b-541">添加以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="d4c9b-542">插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="d4c9b-543">Substitute **azureFunctionEndpoint**值与你在服务中找到 Azure 函数应用，在 Azure 门户中，如下图中所示的 Azure 函数应用 URL:</span><span class="sxs-lookup"><span data-stu-id="d4c9b-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![获取函数 URL](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="d4c9b-545">现在，添加**start （)** 并**Awake()** 初始化类的方法。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="d4c9b-546">内**update （)** 方法中，添加以下代码，它会检测到鼠标输入并拖动，又将场景中移动 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="d4c9b-547">如果用户具有拖动并删除一个对象，它将向方法传递的名称和对象的坐标**UpdateCloudScene()**，这将调用 Azure 函数应用服务，这将更新 Azure 表和触发器通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="d4c9b-548">现在，添加**UpdateCloudScene()** 方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="d4c9b-549">保存代码，并返回到 Unity</span><span class="sxs-lookup"><span data-stu-id="d4c9b-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="d4c9b-550">拖动**CloudScene**拖动到脚本**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="d4c9b-551">单击**Main Camera**从**层次结构**面板中，以便其属性将显示在**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="d4c9b-552">与**脚本**文件夹中，打开，选择**CloudScene**脚本并将其拖动到**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="d4c9b-553">结果应如下所示：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-553">The result should be as below:</span></span>

        > ![将云脚本拖动到主照相机上](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="d4c9b-555">第 11 章 — 生成桌面到 UWP 项目</span><span class="sxs-lookup"><span data-stu-id="d4c9b-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="d4c9b-556">此项目的 Unity 部分所需的所有内容现在已完成。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="d4c9b-557">导航到**生成设置**(**文件 > 生成设置**)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-557">Navigate to **Build Settings** (**File > Build Settings**).</span></span>

2.  <span data-ttu-id="d4c9b-558">从**生成设置**窗口中，单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-558">From the **Build Settings** window, click **Build**.</span></span>

    ![生成项目](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="d4c9b-560">一个**文件资源管理器**将弹出窗口，提示您输入到生成的位置。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="d4c9b-561">创建一个新文件夹 (通过单击**新文件夹**左上角)，并将其命名**生成**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![生成新的文件夹](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="d4c9b-563">打开新**生成**文件夹，并创建另一个文件夹 (使用**新的文件夹**一次)，并将其命名**NH\_桌面\_应用**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![文件夹名称 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="d4c9b-565">与**NH\_桌面\_应用**选定。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="d4c9b-566">单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-566">click **Select Folder**.</span></span> <span data-ttu-id="d4c9b-567">该项目将花大约一分钟生成。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="d4c9b-568">以下生成，**文件资源管理器**将显示新项目的位置。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="d4c9b-569">无需打开它，尽管根据需要创建其他 Unity 项目首先，在接下来的几个章节。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="d4c9b-570">第 12 章 — 设置混合现实 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="d4c9b-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="d4c9b-571">以下是一组典型使用混合现实中，进行开发，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="d4c9b-572">打开**Unity**然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-572">Open **Unity** and click **New**.</span></span>

    ![新的 unity 项目](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="d4c9b-574">现在将需要提供 Unity 项目的名称，插入**UnityMRNotifHub**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="d4c9b-575">请确保项目类型设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="d4c9b-576">设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="d4c9b-577">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-577">Then, click **Create project**.</span></span>

    ![name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="d4c9b-579">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="d4c9b-580">转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-580">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="d4c9b-581">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="d4c9b-582">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-582">Close the **Preferences** window.</span></span>

    ![vs 设置外部编辑器](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="d4c9b-584">接下来，请转到**文件 > 生成设置**，并切换到平台**通用 Windows 平台**，单击**切换平台**按钮。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-584">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![切换到 UWP 的平台](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="d4c9b-586">转到**文件 > 生成设置**并确保选中：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-586">Go to **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="d4c9b-587">**设备为目标**设置为**任一设备**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="d4c9b-588">对于 Microsoft HoloLens，设置**目标设备**到*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="d4c9b-589">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="d4c9b-590">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="d4c9b-591">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="d4c9b-592">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="d4c9b-593">在此，仪表是值得保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="d4c9b-594">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="d4c9b-595">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-595">A save window will appear.</span></span>

            ![添加打开场景](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="d4c9b-597">创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新的场景文件夹](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="d4c9b-599">打开新建**场景**文件夹，然后在**文件名：** 文本字段中，键入**NH\_MR\_场景**，然后按**保存**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![新的场景-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="d4c9b-601">中的剩余设置，**生成设置**，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="d4c9b-602">在同一窗口中单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![打开播放器设置](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="d4c9b-604">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="d4c9b-605">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="d4c9b-606">**脚本运行时版本**应**实验**（.NET 4.6 等效）</span><span class="sxs-lookup"><span data-stu-id="d4c9b-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="d4c9b-607">**脚本编写后端**应为 ***.NET***</span><span class="sxs-lookup"><span data-stu-id="d4c9b-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="d4c9b-608">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![api 兼容性](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="d4c9b-610">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加</span><span class="sxs-lookup"><span data-stu-id="d4c9b-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![更新 xr 设置](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="d4c9b-612">内**发布设置**选项卡上，在**功能**，为了增加点乐趣：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="d4c9b-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="d4c9b-613">**InternetClient**</span></span>           

            ![刻度线 internet 客户端](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="d4c9b-615">回到**生成设置** *Unity C\#项目*不再灰显： 选中此旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-615">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="d4c9b-616">完成这些更改，关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="d4c9b-617">保存您的场景和项目 **文件**保存场景*/ *文件** 保存项目 \* \*。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-617">Save your Scene and Project \**File* *Save Scene*/ *File* \*Save Project\*\*.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d4c9b-618">如果你想要跳过*Unity 设置*组件为此项目中 （混合现实应用），并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="d4c9b-619">你将需要添加脚本组件。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="d4c9b-620">第 13 章 — 导入混合的现实 Unity 项目中的 Dll</span><span class="sxs-lookup"><span data-stu-id="d4c9b-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="d4c9b-621">您将使用 Azure 存储于 Unity 库 （它使用 azure.Net SDK）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="d4c9b-622">请遵循此[如何配合使用 Unity 和 Azure 存储链接](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="d4c9b-623">这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="d4c9b-624">这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="d4c9b-625">若要导入您自己的项目的 SDK，请确保已下载最新[.unitypackage](https://aka.ms/azstorage-unitysdk)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="d4c9b-626">然后，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-626">Then, do the following:</span></span>

1.  <span data-ttu-id="d4c9b-627">添加从以上下载到使用 Unity.unitypackage**资产 > 导入包 > 自定义包**菜单选项。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="d4c9b-628">在中**导入 Unity 程序包**框，弹出，你可以选择下的所有内容**插件 > 存储**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin > Storage**.</span></span>

    ![导入包](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="d4c9b-630">单击**导入**按钮将项添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="d4c9b-631">转到**存储**下的文件夹**插件**项目中查看并选择以下插件*仅*:</span><span class="sxs-lookup"><span data-stu-id="d4c9b-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="d4c9b-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="d4c9b-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="d4c9b-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="d4c9b-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="d4c9b-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="d4c9b-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="d4c9b-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="d4c9b-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="d4c9b-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="d4c9b-636">System.Spatial</span></span>

    ![选择插件](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="d4c9b-638">与*这些特定插件*选择，**取消选中** **Any 平台**并**取消选中** **WSAPlayer**然后单击**应用**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![应用平台更改](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="d4c9b-640">在标注这些特定的插件，只使用在 Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="d4c9b-641">这是因为存在不同版本的项目会导出从 Unity 后，将使用 WSA 文件夹中的同一个插件。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="d4c9b-642">在中**存储**插件文件夹中，只选择：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="d4c9b-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="d4c9b-643">Microsoft.Data.Services.Client</span></span>

        ![选择数据服务客户端](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="d4c9b-645">检查**不进程**框下**平台设置**然后单击**应用**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![不处理](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="d4c9b-647">您要标记此插件"不处理"因为 Unity 程序集 patcher 有处理此插件的难度。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="d4c9b-648">即使它不会得到处理，该插件仍将起作用。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="d4c9b-649">第 14 章 — 在混合的现实 Unity 项目中创建 TableToScene 类</span><span class="sxs-lookup"><span data-stu-id="d4c9b-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="d4c9b-650">**TableToScene**类是等同于代码中所述[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="d4c9b-651">在混合现实中所述的相同过程在 Unity 项目中创建相同的类[第 9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="d4c9b-652">完成本章节中，这两个后你**Unity 项目**将具有在 Main Camera 上设置了此类。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="d4c9b-653">第 15 章 — 在混合现实 Unity 项目中创建 NotificationReceiver 类</span><span class="sxs-lookup"><span data-stu-id="d4c9b-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="d4c9b-654">若要创建所需的第二个脚本是**NotificationReceiver**，负责：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="d4c9b-655">在初始化通知中心注册该应用。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="d4c9b-656">侦听来自通知中心将通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="d4c9b-657">反序列化中接收通知的对象数据。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="d4c9b-658">在场景中，基于反序列化数据中移动 Gameobject。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="d4c9b-659">若要创建**NotificationReceiver**脚本：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="d4c9b-660">内右击**脚本**文件夹中，单击**创建**， **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="d4c9b-661">脚本命名为**NotificationReceiver**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="d4c9b-662">![创建新的 c# 脚本](images/AzureLabs-Lab8-95.png)
    ![其命名为 NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="d4c9b-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="d4c9b-663">双击该脚本以将其打开。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="d4c9b-664">添加以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="d4c9b-665">插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="d4c9b-666">Substitute **hubName**值替换为通知中心服务名称，并**hubListenEndpoint**值与在 Azure 通知中心服务，的访问策略选项卡中找到的终结点值Azure 门户 （请参阅下图所示）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![插入通知中心策略终结点](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="d4c9b-668">现在，添加**start （)** 并**Awake()** 初始化类的方法。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="d4c9b-669">添加**WaitForNotification**方法，以允许应用程序以从通知中心库接收通知，而无需与主线程冲突：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="d4c9b-670">下面的方法， **InitNotificationAsync()**，将与通知中心服务在初始化时注册该应用程序。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="d4c9b-671">代码注释掉，如 Unity 将不能生成项目。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="d4c9b-672">导入 Visual Studio 中的 Azure 消息传送 Nuget 包时，将删除注释。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="d4c9b-673">下面的处理程序，**通道\_PushNotificationReceived()**，每次收到通知时，将触发。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="d4c9b-674">它将反序列化的通知，它已被移动桌面应用程序，Azure 表实体，然后将相应的 GameObject MR 场景中移动到相同的位置。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="d4c9b-675">代码注释掉，因为该代码引用 Azure 消息传送库，将生成使用 Nuget 包管理器中，Visual Studio 中的 Unity 项目后添加。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="d4c9b-676">在这种情况下，Unity 项目将不能生成，除非它已被注释掉。请注意，是否应生成你的项目，然后希望返回到 Unity，你将需要**重新加上注释**该代码。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="d4c9b-677">请记住之前追溯到 Unity 编辑器中保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="d4c9b-678">单击**Main Camera**从**层次结构**面板中，以便其属性将显示在**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="d4c9b-679">与**脚本**文件夹中，打开，选择**NotificationReceiver**脚本并将其拖动到**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="d4c9b-680">结果应如下所示：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-680">The result should be as below:</span></span>

    ![将通知收件人脚本拖到相机](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="d4c9b-682">如果正在为 Microsoft HoloLens 开发，您需要更新**Main Camera**的*照相机*组件，以便：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="d4c9b-683">清除标志：纯色</span><span class="sxs-lookup"><span data-stu-id="d4c9b-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="d4c9b-684">背景：黑色</span><span class="sxs-lookup"><span data-stu-id="d4c9b-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="d4c9b-685">第 16 章 — 生成混合的现实项目到 UWP</span><span class="sxs-lookup"><span data-stu-id="d4c9b-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="d4c9b-686">此章节都是相同，以生成前一项目的过程。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="d4c9b-687">此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="d4c9b-688">导航到**生成设置**(**文件 > 生成设置...** ).</span><span class="sxs-lookup"><span data-stu-id="d4c9b-688">Navigate to **Build Settings** ( **File > Build Settings...** ).</span></span>

2.  <span data-ttu-id="d4c9b-689">从**生成设置**菜单上，确保**UnityC#项目**\* 勾选了 （这将允许您编辑后生成此项目中的脚本）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="d4c9b-690">此操作完成后，单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-690">After this is done, click **Build**.</span></span>

    ![生成项目](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="d4c9b-692">一个**文件资源管理器**将弹出窗口，提示您输入到生成的位置。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="d4c9b-693">创建一个新文件夹 (通过单击**新文件夹**左上角)，并将其命名**生成**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![创建内部版本文件夹](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="d4c9b-695">打开新**生成**文件夹，并创建另一个文件夹 (使用**新的文件夹**一次)，并将其命名**NH\_MR\_应用**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![创建 NH_MR_Apps 文件夹](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="d4c9b-697">与**NH\_MR\_应用**选定。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="d4c9b-698">单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-698">click **Select Folder**.</span></span> <span data-ttu-id="d4c9b-699">该项目将花大约一分钟生成。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="d4c9b-700">以下生成，**文件资源管理器**窗口将打开新项目的位置。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="d4c9b-701">第 17 章 — 将 NuGet 包添加到 UnityMRNotifHub 解决方案</span><span class="sxs-lookup"><span data-stu-id="d4c9b-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="d4c9b-702">请记住，添加以下 NuGet 包后 (并取消注释在接下来的代码[章](#chapter-18---edit-unitymrnotifhub-application,-notificationreciever-class))，代码，在 Unity 项目中，重新打开时将显示错误。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application,-notificationreciever-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="d4c9b-703">如果你想要返回并继续编辑在 Unity 编辑器中，你将需要注释 errosome 代码，然后，取消注释再次更高版本，一旦您重新登录 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="d4c9b-704">混合的现实生成完成后，导航到混合的现实项目，生成示例，请然后双击该文件夹，以使用 Visual Studio 2017 中打开你的解决方案中的解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="d4c9b-705">现在需要添加**WindowsAzure.Messaging.managed** NuGet 程序包; 这是一个库，用于从通知中心接收通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="d4c9b-706">若要导入 NuGet 包：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="d4c9b-707">在中**解决方案资源管理器**，右键单击你的解决方案</span><span class="sxs-lookup"><span data-stu-id="d4c9b-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="d4c9b-708">单击**管理 NuGet 包**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-708">Click on **Manage NuGet Packages**.</span></span>

    ![打开 nuget 管理器](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="d4c9b-710">选择***浏览***选项卡并搜索**WindowsAzure.Messaging.managed**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![查找 windows azure 消息传送包](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="d4c9b-712">选择结果 （如下所示），并在右侧窗口中，选中的复选框旁边**项目**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="d4c9b-713">这会将一个对勾置于相应的复选框旁边**项目**，以及旁边的复选框**程序集 CSharp**并**UnityMRNotifHub**项目。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![选中所有项目](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="d4c9b-715">最初提供的版本**可能不会**与此项目兼容。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="d4c9b-716">因此，请单击下拉列表菜单旁边**版本**，然后单击**版本 0.1.7.9**，然后单击**安装**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="d4c9b-717">现在，已安装的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="d4c9b-718">查找注释的代码中输入**NotificationReceiver**类，并删除注释...</span><span class="sxs-lookup"><span data-stu-id="d4c9b-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="d4c9b-719">第 18 章 — 编辑 UnityMRNotifHub 应用程序、 NotificationReceiver 类</span><span class="sxs-lookup"><span data-stu-id="d4c9b-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="d4c9b-720">添加了以下**NuGet 包**，你将需要*取消注释*中的代码的一些**NotificationReceiver**类。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="d4c9b-721">这包括：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-721">This includes:</span></span>

1. <span data-ttu-id="d4c9b-722">在顶部命名空间：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="d4c9b-723">中的所有代码**InitNotificationsAsync()** 方法：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="d4c9b-724">上面的代码中有一条注释： 请确保不会意外*取消注释*的注释 （如代码将不会编译有 ！）。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="d4c9b-725">和最后**Channel_PushNotificationReceived**事件：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="d4c9b-726">与这些取消注释中，确保您保存，然后，转到下一章。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="d4c9b-727">第 19 章 — 将关联到应用商店应用程序的混合的现实项目</span><span class="sxs-lookup"><span data-stu-id="d4c9b-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="d4c9b-728">现在需要将相关联**混合现实**到应用商店应用中的实验室之初创建的项目。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="d4c9b-729">打开的解决方案。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-729">Open the solution.</span></span>

2.  <span data-ttu-id="d4c9b-730">右键单击 UWP 应用项目在解决方案资源管理器窗格中，转到**应用商店**，和**将应用与应用商店关联...**.</span><span class="sxs-lookup"><span data-stu-id="d4c9b-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![打开应用商店关联](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="d4c9b-732">将出现一个新窗口调用**将应用与 Windows 应用商店关联**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="d4c9b-733">单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-733">Click **Next**.</span></span>

    ![转到下一个屏幕](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="d4c9b-735">它会加载与已登录的帐户相关联的所有应用程序的运行。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="d4c9b-736">如果您未登录到你的帐户，则可以**日志中**此页上。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="d4c9b-737">查找**应用商店应用程序名称**本教程开始时创建并选择它。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="d4c9b-738">然后，单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-738">Then click **Next**.</span></span>

    ![找到并选择你的存储区名称](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="d4c9b-740">单击**相关联**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-740">Click **Associate**.</span></span>

    ![将应用程序](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="d4c9b-742">您的应用程序现**关联**与应用商店应用程序。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="d4c9b-743">这是必要的通知。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="d4c9b-744">第 20 章 — 部署 UnityMRNotifHub 和 UnityDesktopNotifHub 应用程序</span><span class="sxs-lookup"><span data-stu-id="d4c9b-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="d4c9b-745">根据结果将包括同时运行的应用，桌面，您的计算机上的一个正在运行，另一个在您的沉浸式头戴式，本章可能会更方便中与两个用户。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="d4c9b-746">沉浸式头戴式应用正在等待接收对场景 （的本地 Gameobject 的位置变化）、 更改和桌面应用程序将对其本地场景 （位置的更改），将共享到 MR 应用进行更改。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="d4c9b-747">最好首先部署 MR 应用，以便接收方可以开始侦听跟桌面应用。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="d4c9b-748">若要部署**UnityMRNotifHub**在本地计算机上的应用：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="d4c9b-749">打开解决方案文件的应用**UnityMRNotifHub**中的应用**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="d4c9b-750">在中**解决方案平台**，选择**x86，本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="d4c9b-751">在中**解决方案配置**选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![设置项目配置](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="d4c9b-753">转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="d4c9b-754">你的应用现在应出现在已安装的应用，准备好启动列表中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="d4c9b-755">若要部署**UnityDesktopNotifHub**本地计算机上的应用：</span><span class="sxs-lookup"><span data-stu-id="d4c9b-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="d4c9b-756">打开解决方案文件的应用**UnityDesktopNotifHub**中的应用**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="d4c9b-757">在中**解决方案平台**，选择**x86，本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="d4c9b-758">在中**解决方案配置**选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![设置项目配置](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="d4c9b-760">转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="d4c9b-761">你的应用现在应出现在已安装的应用，准备好启动列表中。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="d4c9b-762">启动混合的现实应用程序，跟在桌面应用程序。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="d4c9b-763">这两个运行的应用程序，桌面 （使用左鼠标按钮） 的场景中移动对象。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="d4c9b-764">这些位置的更改将本地进行，序列化，并发送到函数应用服务。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="d4c9b-765">Function App 服务然后将更新的表和通知中心。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="d4c9b-766">具有收到的更新，通知中心将更新后的数据将直接发送到所有已注册应用程序 （在此情况下沉浸式头戴式应用），然后反序列化传入的数据，并将新的位置数据应用于本地对象，在场景中移动它们。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="d4c9b-767">你完成 Azure 通知中心应用程序</span><span class="sxs-lookup"><span data-stu-id="d4c9b-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="d4c9b-768">祝贺你，构建利用 Azure 通知中心服务，并允许应用程序之间的通信的混合的现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="d4c9b-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![最终产品的最终](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="d4c9b-770">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="d4c9b-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="d4c9b-771">练习 1</span><span class="sxs-lookup"><span data-stu-id="d4c9b-771">Exercise 1</span></span>

<span data-ttu-id="d4c9b-772">您可以推断出如何更改的 GameObjects 颜色并将该通知发送到其他应用查看场景？</span><span class="sxs-lookup"><span data-stu-id="d4c9b-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="d4c9b-773">练习 2</span><span class="sxs-lookup"><span data-stu-id="d4c9b-773">Exercise 2</span></span>

<span data-ttu-id="d4c9b-774">您可以向 MR 应用添加的 GameObjects 移动和桌面应用程序中看到更新的场景？</span><span class="sxs-lookup"><span data-stu-id="d4c9b-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
