---
title: MR 和 Azure 309-Application insights
description: 完成本课程，了解如何使用 Azure 应用程序 Insights 服务在混合现实应用程序内收集有关用户行为的分析。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，application insights，hololens，沉浸，vr
ms.openlocfilehash: 481fe3fc16ada06085a64c86867a1a892c76f2ad
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926899"
---
>[!NOTE]
><span data-ttu-id="98bf4-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="98bf4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="98bf4-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="98bf4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="98bf4-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="98bf4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="98bf4-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="98bf4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="98bf4-108">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="98bf4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="98bf4-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="98bf4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="98bf4-110">MR 和 Azure 309： Application insights</span><span class="sxs-lookup"><span data-stu-id="98bf4-110">MR and Azure 309: Application insights</span></span>

![最终产品-启动](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="98bf4-112">在本课程中，您将学习如何使用 Azure 应用程序 Insights API 来收集有关用户行为的分析，将 Application Insights 功能添加到混合现实应用程序中。</span><span class="sxs-lookup"><span data-stu-id="98bf4-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="98bf4-113">Application Insights 是一项 Microsoft 服务，它允许开发人员从其应用程序中收集分析，并从易于使用的门户对其进行管理。</span><span class="sxs-lookup"><span data-stu-id="98bf4-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="98bf4-114">分析可以是从性能到你想要收集的自定义信息。</span><span class="sxs-lookup"><span data-stu-id="98bf4-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="98bf4-115">有关详细信息，请访问[Application Insights 页](https://azure.microsoft.com/services/application-insights/)。</span><span class="sxs-lookup"><span data-stu-id="98bf4-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="98bf4-116">完成本课程后，你将拥有一个混合现实沉浸式耳机应用程序，该应用程序将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="98bf4-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="98bf4-117">允许用户注视并四处移动场景。</span><span class="sxs-lookup"><span data-stu-id="98bf4-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="98bf4-118">通过使用注视并接近场景内对象来触发将分析发送到*Application Insights 服务*。</span><span class="sxs-lookup"><span data-stu-id="98bf4-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="98bf4-119">该应用还将在服务上调用，并在过去24小时内获取有关用户最接近哪个对象的信息。</span><span class="sxs-lookup"><span data-stu-id="98bf4-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="98bf4-120">该对象会将其颜色更改为绿色。</span><span class="sxs-lookup"><span data-stu-id="98bf4-120">That object will change its color to green.</span></span>

<span data-ttu-id="98bf4-121">本课程将介绍如何将 Application Insights 服务的结果获取到基于 Unity 的示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="98bf4-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="98bf4-122">您可以将这些概念应用到您可能生成的自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="98bf4-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="98bf4-123">设备支持</span><span class="sxs-lookup"><span data-stu-id="98bf4-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="98bf4-124">摘要</span><span class="sxs-lookup"><span data-stu-id="98bf4-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="98bf4-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="98bf4-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="98bf4-126"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="98bf4-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="98bf4-127">MR 和 Azure 309： Application insights</span><span class="sxs-lookup"><span data-stu-id="98bf4-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="98bf4-128">✔️</span><span class="sxs-lookup"><span data-stu-id="98bf4-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="98bf4-129">✔️</span><span class="sxs-lookup"><span data-stu-id="98bf4-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="98bf4-130">尽管本课程主要侧重于 Windows Mixed Reality 沉浸（VR）耳机，但你也可以将本课程中学习的内容应用于 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="98bf4-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="98bf4-131">在本课程中，你将看到有关支持 HoloLens 时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="98bf4-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="98bf4-132">使用 HoloLens 时，可能会在语音捕获过程中注意到某些回声。</span><span class="sxs-lookup"><span data-stu-id="98bf4-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="98bf4-133">必备条件</span><span class="sxs-lookup"><span data-stu-id="98bf4-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="98bf4-134">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="98bf4-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="98bf4-135">另外，请注意，本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容（2018年7月）。</span><span class="sxs-lookup"><span data-stu-id="98bf4-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="98bf4-136">你可以随意使用最新的软件（如[安装工具](install-the-tools.md)一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="98bf4-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="98bf4-137">本课程建议采用以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="98bf4-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="98bf4-138">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发</span><span class="sxs-lookup"><span data-stu-id="98bf4-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="98bf4-139">Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="98bf4-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="98bf4-140">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="98bf4-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="98bf4-141">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="98bf4-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="98bf4-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="98bf4-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="98bf4-143">启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="98bf4-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="98bf4-144">带有内置麦克风的一组耳机（如果耳机没有内置麦克风和扬声器）</span><span class="sxs-lookup"><span data-stu-id="98bf4-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="98bf4-145">Azure 安装和 Application Insights 数据检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="98bf4-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="98bf4-146">开始之前</span><span class="sxs-lookup"><span data-stu-id="98bf4-146">Before you start</span></span>

<span data-ttu-id="98bf4-147">为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。</span><span class="sxs-lookup"><span data-stu-id="98bf4-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="98bf4-148">请注意，转到*Application Insights*的数据需要一些时间，因此请耐心等待。</span><span class="sxs-lookup"><span data-stu-id="98bf4-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="98bf4-149">如果要检查服务是否已收到数据，请查看第[14 章](#chapter-14---the-application-insights-service-portal)，其中显示了如何导航门户。</span><span class="sxs-lookup"><span data-stu-id="98bf4-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="98bf4-150">第1章-Azure 门户</span><span class="sxs-lookup"><span data-stu-id="98bf4-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="98bf4-151">若要使用*Application Insights*，你将需要在 Azure 门户中创建和配置*Application Insights 服务*。</span><span class="sxs-lookup"><span data-stu-id="98bf4-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="98bf4-152">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="98bf4-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="98bf4-153">如果还没有 Azure 帐户，则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="98bf4-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="98bf4-154">如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="98bf4-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="98bf4-155">登录后，单击左上角的 "**新建**"，搜索 " *Application Insights*"，然后单击 " **Enter**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="98bf4-156">在较新的门户中，可能已将 "**新建**" 一词替换为 "**创建资源**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="98bf4-158">向右的新页将提供*Azure 应用程序 Insights*服务的说明。</span><span class="sxs-lookup"><span data-stu-id="98bf4-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="98bf4-159">在此页的左下角，选择 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="98bf4-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="98bf4-161">单击 "**创建**" 后：</span><span class="sxs-lookup"><span data-stu-id="98bf4-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="98bf4-162">为此服务实例插入所需的**名称**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="98bf4-163">对于 "**应用程序类型**"，选择 "**常规**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="98bf4-164">选择相应的**订阅**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="98bf4-165">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="98bf4-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="98bf4-166">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="98bf4-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="98bf4-167">建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="98bf4-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="98bf4-168">若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="98bf4-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="98bf4-169">选择一个**位置**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="98bf4-170">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="98bf4-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="98bf4-171">选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="98bf4-171">Select **Create**.</span></span>

        ![Azure 门户](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="98bf4-173">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="98bf4-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="98bf4-174">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="98bf4-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="98bf4-176">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="98bf4-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="98bf4-178">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="98bf4-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="98bf4-179">你将转到新的*Application Insights 服务*实例。</span><span class="sxs-lookup"><span data-stu-id="98bf4-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="98bf4-181">使此网页保持打开状态且易于访问，你会经常回来查看收集的数据。</span><span class="sxs-lookup"><span data-stu-id="98bf4-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="98bf4-182">若要实现 Application Insights，你将需要使用三个（3）个特定值：**检测密钥**、**应用程序 ID**和**API 密钥**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="98bf4-183">下面你将了解如何从服务中检索这些值。</span><span class="sxs-lookup"><span data-stu-id="98bf4-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="98bf4-184">请确保在空白*记事本*页面上记下这些值，因为在代码中不久会用到它们。</span><span class="sxs-lookup"><span data-stu-id="98bf4-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="98bf4-185">若要查找**检测密钥**，你将需要向下滚动服务功能列表，然后单击 "**属性**"，显示的选项卡将显示**服务密钥**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="98bf4-187">下面是一些**属性**，你将发现需要单击的**API 访问权限**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="98bf4-188">右侧面板将提供应用的**应用程序 ID** 。</span><span class="sxs-lookup"><span data-stu-id="98bf4-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="98bf4-190">在**应用程序 ID**面板仍处于打开状态的情况下，单击 "**创建 api 密钥**"，这将打开 "*创建 api 密钥*" 面板。</span><span class="sxs-lookup"><span data-stu-id="98bf4-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="98bf4-192">在现在打开 "*创建 API 密钥*" 面板中，键入说明，并**勾选三个框**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="98bf4-193">单击 "**生成密钥**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-193">Click **Generate Key**.</span></span> <span data-ttu-id="98bf4-194">将创建并显示你的**API 密钥**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure 门户](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="98bf4-196">这是你的**服务密钥**的唯一显示时间，因此请确保现在复制它。</span><span class="sxs-lookup"><span data-stu-id="98bf4-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="98bf4-197">第2章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="98bf4-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="98bf4-198">下面是使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="98bf4-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="98bf4-199">打开*Unity* ，并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-199">Open *Unity* and click **New**.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="98bf4-201">现在需要提供 Unity 项目名称，将**MR\_Azure\_应用程序\_Insights**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="98bf4-202">请确保将*模板*设置为**3d**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="98bf4-203">将位置设置为合适的*位置*（请记住，更接近根目录更好）。</span><span class="sxs-lookup"><span data-stu-id="98bf4-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="98bf4-204">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-204">Then, click **Create project**.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="98bf4-206">当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="98bf4-207">转到 "**编辑 \> 首选项**"，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="98bf4-208">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="98bf4-209">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="98bf4-209">Close the **Preferences** window.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="98bf4-211">接下来，通过单击 "**切换平台**" 按钮转到 "**文件 \> 生成设置**"，并将平台切换到**通用 Windows 平台**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="98bf4-213">请参阅**文件 \> 生成设置**，并确保：</span><span class="sxs-lookup"><span data-stu-id="98bf4-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="98bf4-214">**目标设备**设置为**任何设备**</span><span class="sxs-lookup"><span data-stu-id="98bf4-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="98bf4-215">对于 Microsoft HoloLens，将 "**目标设备**" 设置为 " *hololens*"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="98bf4-216">**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="98bf4-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="98bf4-217">**SDK**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="98bf4-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="98bf4-218">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="98bf4-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="98bf4-219">保存场景并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="98bf4-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="98bf4-220">通过选择 "**添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="98bf4-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="98bf4-221">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="98bf4-221">A save window will appear.</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="98bf4-223">为此创建新的文件夹，并在将来的任何场景中，单击 "**新建文件夹**" 按钮，创建一个新文件夹，将其命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="98bf4-225">打开新创建的**场景**文件夹，然后在 "文件名 *：* 文本" 字段中，键入**ApplicationInsightsScene**，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="98bf4-227">现在，"**生成设置**" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="98bf4-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="98bf4-228">在 "**生成设置**" 窗口中，单击 "**播放机设置**" 按钮，这会在**检查器**所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="98bf4-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="98bf4-230">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="98bf4-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="98bf4-231">在 "**其他设置**" 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="98bf4-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="98bf4-232">**脚本** **运行时版本**应为试验性的 **（.net 4.6 等效项）** ，这会触发重新启动编辑器的需要。</span><span class="sxs-lookup"><span data-stu-id="98bf4-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="98bf4-233">**脚本编写后端**应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="98bf4-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="98bf4-234">**API 兼容级别**应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="98bf4-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="98bf4-236">在 "**发布设置**" 选项卡的 "**功能**" 下，检查：</span><span class="sxs-lookup"><span data-stu-id="98bf4-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="98bf4-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="98bf4-237">**InternetClient**</span></span>     

            ![设置 Unity 项目](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="98bf4-239">在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="98bf4-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="98bf4-241">返回**生成设置**， **Unity C#项目**不再灰显;勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="98bf4-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="98bf4-242">关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="98bf4-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="98bf4-243">保存场景和项目（**file** > **SAVE 场景/FILE** > **save Project**）。</span><span class="sxs-lookup"><span data-stu-id="98bf4-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="98bf4-244">第3章-导入 Unity 包</span><span class="sxs-lookup"><span data-stu-id="98bf4-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98bf4-245">如果要跳过*Unity 设置*本课程的组件，并继续直接进入代码，请随时下载此[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)，并将其作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入到项目中。</span><span class="sxs-lookup"><span data-stu-id="98bf4-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="98bf4-246">这还将包含下一章中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="98bf4-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="98bf4-247">导入后，继续[**第6章**](#chapter-6---create-the-applicationinsightstracker-class)。</span><span class="sxs-lookup"><span data-stu-id="98bf4-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98bf4-248">若要在 Unity 内使用 Application Insights，需要为其导入 DLL 以及 Newtonsoft.json DLL。</span><span class="sxs-lookup"><span data-stu-id="98bf4-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="98bf4-249">当前 Unity 中存在一个已知问题，需要在导入后重新配置插件。</span><span class="sxs-lookup"><span data-stu-id="98bf4-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="98bf4-250">解决 bug 后，将不再需要这些步骤（本部分中的 4-7）。</span><span class="sxs-lookup"><span data-stu-id="98bf4-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="98bf4-251">若要将 Application Insights 导入到自己的项目中，请确保已[下载包含插件的 ". unitypackage"](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="98bf4-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="98bf4-252">然后，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="98bf4-252">Then, do the following:</span></span>

1.  <span data-ttu-id="98bf4-253">使用 "**资产 \> 导入包 \> 自定义包**" 菜单选项将**Unitypackage**添加到 Unity。</span><span class="sxs-lookup"><span data-stu-id="98bf4-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="98bf4-254">在弹出的 "**导入 Unity 包**" 框中，确保选择了 "所有" （并包括）**插件**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![导入 Unity 包](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="98bf4-256">单击 "**导入**" 按钮，将项添加到项目。</span><span class="sxs-lookup"><span data-stu-id="98bf4-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="98bf4-257">在项目视图中，在 "**插件**" 下中转到 " **Insights** " 文件夹，并*仅*选择以下插件：</span><span class="sxs-lookup"><span data-stu-id="98bf4-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="98bf4-258">Applicationinsights.config</span><span class="sxs-lookup"><span data-stu-id="98bf4-258">Microsoft.ApplicationInsights</span></span>

    ![导入 Unity 包](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="98bf4-260">选择此*插件*后，请确保**未选中** **任何平台**，然后确保**WSAPlayer**未被**选中**，然后单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="98bf4-261">这样做只是为了确认正确配置了文件。</span><span class="sxs-lookup"><span data-stu-id="98bf4-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![导入 Unity 包](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="98bf4-263">标记此类插件，将它们配置为仅在 Unity 编辑器中使用。</span><span class="sxs-lookup"><span data-stu-id="98bf4-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="98bf4-264">WSA 文件夹中有一组不同的 Dll，将在从 Unity 导出项目后使用。</span><span class="sxs-lookup"><span data-stu-id="98bf4-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="98bf4-265">接下来，需要在**Insights**文件夹内打开**WSA**文件夹。</span><span class="sxs-lookup"><span data-stu-id="98bf4-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="98bf4-266">你将看到刚才配置的同一文件的副本。</span><span class="sxs-lookup"><span data-stu-id="98bf4-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="98bf4-267">选择此文件，然后在 "检查器" 中，确保**未选中** **任何平台**，然后确保**只** **选中**" **WSAPlayer** "。</span><span class="sxs-lookup"><span data-stu-id="98bf4-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="98bf4-268">单击**应用**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-268">Click **Apply**.</span></span>

    ![导入 Unity 包](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="98bf4-270">你现在需要遵循**步骤 4-6**，但要改为*newtonsoft.json*插件。</span><span class="sxs-lookup"><span data-stu-id="98bf4-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="98bf4-271">若要查看结果，请参阅下面的屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="98bf4-271">See the below screenshot for what the outcome should look like.</span></span>

    ![导入 Unity 包](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="98bf4-273">第4章-设置照相机和用户控件</span><span class="sxs-lookup"><span data-stu-id="98bf4-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="98bf4-274">在本章中，你将设置照相机和控件，以允许用户在场景中查看和移动。</span><span class="sxs-lookup"><span data-stu-id="98bf4-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="98bf4-275">右键单击 "层次结构" 面板中的空白区域，然后在 "**创建** > **空**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![设置照相机和用户控件](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="98bf4-277">将新的空 GameObject 重命名为**相机父项**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![设置照相机和用户控件](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="98bf4-279">右键单击 "层次结构" 面板中的空白区域，然后在 "**三维对象**" 上右键单击，然后单击 "**球面**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="98bf4-280">将球体重命名为**右手**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="98bf4-281">将右侧的**转换比例**设置为**0.1、0.1、0.1**</span><span class="sxs-lookup"><span data-stu-id="98bf4-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![设置照相机和用户控件](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="98bf4-283">单击 "*球碰撞*器" 组件中的**齿轮**，然后单击 "**删除组件**"，从右侧删除**球碰撞**器组件。</span><span class="sxs-lookup"><span data-stu-id="98bf4-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![设置照相机和用户控件](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="98bf4-285">在 "层次结构" 面板中，将**主相机**和**右手**的对象拖到**相机父**对象上。</span><span class="sxs-lookup"><span data-stu-id="98bf4-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![设置照相机和用户控件](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="98bf4-287">将**主相机**和**右侧**对象的**变换位置**设置为**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![设置照相机和用户控件](images/AzureLabs-Lab309-31.png)

    ![设置照相机和用户控件](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="98bf4-290">第5章-在 Unity 场景中设置对象</span><span class="sxs-lookup"><span data-stu-id="98bf4-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="98bf4-291">现在，您将为您的场景创建一些基本形状，使用户能够与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="98bf4-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="98bf4-292">右键单击 "*层次结构" 面板*中的空白区域，然后在**3d 对象**上单击，然后选择 "**平面**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="98bf4-293">将平面**转换位置**设置为**0，-1，0**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="98bf4-294">将平面**转换比例**设置为**5、1、5**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="98bf4-296">创建要用于**飞机**对象的基本材料，以便更易于查看其他形状。</span><span class="sxs-lookup"><span data-stu-id="98bf4-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="98bf4-297">导航到*项目面板*，右键单击，然后选择 "**创建**"，然后单击 "**文件夹**"，创建一个新文件夹。</span><span class="sxs-lookup"><span data-stu-id="98bf4-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="98bf4-298">命名 it**材料**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-298">Name it **Materials**.</span></span>

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-34.png) ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="98bf4-301">打开**材料**文件夹，然后右键单击，单击 "**创建**"，然后单击 "**材料**" 创建新材料。</span><span class="sxs-lookup"><span data-stu-id="98bf4-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="98bf4-302">将其命名为**蓝色**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-302">Name it **Blue**.</span></span>

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-36.png) ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="98bf4-305">选择新的**蓝色**材料后，查看*检查器*，并单击矩形窗口和**Albedo**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="98bf4-306">选择蓝色（下图是**十六进制颜色： \#3592FFFF**）。</span><span class="sxs-lookup"><span data-stu-id="98bf4-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="98bf4-307">选择后，单击 "关闭" 按钮。</span><span class="sxs-lookup"><span data-stu-id="98bf4-307">Click the close button once you have chosen.</span></span>

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="98bf4-309">将新材料从 "**材料**" 文件夹拖到场景内新创建的**平面**上（或将其放置在*层次结构*内的**平面**对象上）。</span><span class="sxs-lookup"><span data-stu-id="98bf4-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="98bf4-311">右键单击 "*层次结构" 面板*中的空白区域，然后在**3d 对象**上单击 "胶囊"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="98bf4-312">选择**胶囊**后，将其\**转换\*\*\*位置*更改为： **-10，1，0**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="98bf4-313">右键单击 "*层次结构" 面板*中的空白区域，然后单击 "**三维对象"、"多维数据集**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="98bf4-314">选择**多维数据集**后，将\**其转换\*\*\*位置*更改为： **0，0，10**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="98bf4-315">右键单击 "*层次结构" 面板*中的空白区域，然后单击 "**三维对象" "球面**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="98bf4-316">选择**球**后，将其\**转换\*\*\*位置*更改为： **10，0，0**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="98bf4-318">这些*位置*值是*建议*。</span><span class="sxs-lookup"><span data-stu-id="98bf4-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="98bf4-319">您可以自由地将对象的位置设置为您想要的任何内容，但如果对象距离离照相机的距离不是太远，那么应用程序的用户会更容易。</span><span class="sxs-lookup"><span data-stu-id="98bf4-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="98bf4-320">当你的应用程序正在运行时，它需要能够识别场景中的对象。若要实现此目的，需要对其进行标记。</span><span class="sxs-lookup"><span data-stu-id="98bf4-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="98bf4-321">选择其中一个对象，然后在 "*检查器*" 面板中，单击 "**添加标记 ...** "，它会将*检查器*与 "**标记" & "层**" 面板。</span><span class="sxs-lookup"><span data-stu-id="98bf4-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="98bf4-322">![在 Unity 场景中设置对象](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="98bf4-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="98bf4-323">单击 " **+" （加号）** 符号，并将标记名称键入为 " **ObjectInScene**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![在 Unity 场景中设置对象](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="98bf4-325">如果为标记使用了不同的名称，则需要确保此更改也会成为*DataFromAnalytics*、 *ObjectTrigger*和*注视*、脚本，以便在场景中找到并检测到你的对象。</span><span class="sxs-lookup"><span data-stu-id="98bf4-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="98bf4-326">创建标记后，现在需要将其应用于所有三个对象。</span><span class="sxs-lookup"><span data-stu-id="98bf4-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="98bf4-327">在*层次结构*中，按住**Shift**键，然后单击**胶囊**、 **Cube**和**球体**、对象，然后在*检查器*中单击下拉菜单和**标记**，然后单击创建的*ObjectInScene*标记。</span><span class="sxs-lookup"><span data-stu-id="98bf4-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="98bf4-328">![在 Unity 场景中设置对象](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="98bf4-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="98bf4-329">第6章-创建 ApplicationInsightsTracker 类</span><span class="sxs-lookup"><span data-stu-id="98bf4-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="98bf4-330">需要创建的第一个脚本是**ApplicationInsightsTracker**，它负责：</span><span class="sxs-lookup"><span data-stu-id="98bf4-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="98bf4-331">基于用户交互创建事件以提交到 Azure 应用程序 Insights。</span><span class="sxs-lookup"><span data-stu-id="98bf4-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="98bf4-332">创建相应的事件名称，具体取决于用户交互。</span><span class="sxs-lookup"><span data-stu-id="98bf4-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="98bf4-333">正在将事件提交到 Application Insights 服务实例。</span><span class="sxs-lookup"><span data-stu-id="98bf4-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="98bf4-334">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="98bf4-334">To create this class:</span></span>

1.  <span data-ttu-id="98bf4-335">右键单击 "*项目" 面板*，然后**创建** > **文件夹**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="98bf4-336">命名文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-336">Name the folder **Scripts**.</span></span>

    ![创建 ApplicationInsightsTracker 类](images/AzureLabs-Lab309-46.png)  ![创建 ApplicationInsightsTracker 类](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="98bf4-339">创建**脚本**文件夹后，双击它以打开。</span><span class="sxs-lookup"><span data-stu-id="98bf4-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="98bf4-340">然后，在该文件夹中，右键单击，**创建** >  **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="98bf4-341">将脚本命名为**ApplicationInsightsTracker**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="98bf4-342">双击新的**ApplicationInsightsTracker**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="98bf4-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="98bf4-343">更新脚本顶部的命名空间，如下所示：</span><span class="sxs-lookup"><span data-stu-id="98bf4-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="98bf4-344">在类中插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="98bf4-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="98bf4-345">按照第[1 章第 1](#chapter-1---the-azure-portal)步中所述，使用 Azure 门户中的*服务密钥*，正确设置**instrumentationKey、applicationId 和 API_Key**值。</span><span class="sxs-lookup"><span data-stu-id="98bf4-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="98bf4-346">然后添加**Start （）** 和**唤醒（）** 方法，在类初始化时将调用该方法：</span><span class="sxs-lookup"><span data-stu-id="98bf4-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="98bf4-347">添加负责发送应用程序注册的事件和度量值的方法：</span><span class="sxs-lookup"><span data-stu-id="98bf4-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="98bf4-348">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="98bf4-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="98bf4-349">第7章-创建注视脚本</span><span class="sxs-lookup"><span data-stu-id="98bf4-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="98bf4-350">要创建的下一个脚本是**注视**脚本。</span><span class="sxs-lookup"><span data-stu-id="98bf4-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="98bf4-351">此脚本负责创建将从*主相机*向前投影的*Raycast* ，以检测用户正在查看的对象。</span><span class="sxs-lookup"><span data-stu-id="98bf4-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="98bf4-352">在这种情况下， *Raycast*需要确定用户是否正在使用**ObjectInScene**标记查看对象，然后计算用户在该对象上的*gazes* 。</span><span class="sxs-lookup"><span data-stu-id="98bf4-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="98bf4-353">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="98bf4-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="98bf4-354">右键单击 "**脚本**" 文件夹中，单击 "**创建** >  **C#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="98bf4-355">将脚本命名为 "**注视**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="98bf4-356">双击脚本以通过 Visual Studio 打开它。</span><span class="sxs-lookup"><span data-stu-id="98bf4-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="98bf4-357">将现有代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="98bf4-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="98bf4-358">现在需要添加**唤醒（）** 和**Start （）** 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="98bf4-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="98bf4-359">在 "**注视**" 类中，将以下代码添加到**Update （）** 方法中以投影*Raycast*并检测目标命中：</span><span class="sxs-lookup"><span data-stu-id="98bf4-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="98bf4-360">添加**ResetFocusedObject （）** 方法，以便在用户查看对象时将数据发送到**Application Insights** 。</span><span class="sxs-lookup"><span data-stu-id="98bf4-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="98bf4-361">你现在已经完成了**注视**脚本。</span><span class="sxs-lookup"><span data-stu-id="98bf4-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="98bf4-362">在返回到*Unity*之前，在*Visual Studio*中保存更改。</span><span class="sxs-lookup"><span data-stu-id="98bf4-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="98bf4-363">第8章-创建 ObjectTrigger 类</span><span class="sxs-lookup"><span data-stu-id="98bf4-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="98bf4-364">需要创建的下一个脚本是**ObjectTrigger**，它负责：</span><span class="sxs-lookup"><span data-stu-id="98bf4-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="98bf4-365">向主相机添加冲突所需的组件。</span><span class="sxs-lookup"><span data-stu-id="98bf4-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="98bf4-366">检测照相机是否位于标记为 " **ObjectInScene**" 的对象附近。</span><span class="sxs-lookup"><span data-stu-id="98bf4-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="98bf4-367">创建脚本：</span><span class="sxs-lookup"><span data-stu-id="98bf4-367">To create the script:</span></span>

1.  <span data-ttu-id="98bf4-368">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="98bf4-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="98bf4-369">右键单击 "**脚本**" 文件夹中，单击 "**创建** >  **C#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="98bf4-370">将脚本命名为**ObjectTrigger**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="98bf4-371">双击脚本以通过 Visual Studio 打开它。</span><span class="sxs-lookup"><span data-stu-id="98bf4-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="98bf4-372">将现有代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="98bf4-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="98bf4-373">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="98bf4-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="98bf4-374">第9章-创建 DataFromAnalytics 类</span><span class="sxs-lookup"><span data-stu-id="98bf4-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="98bf4-375">现在，你将需要创建**DataFromAnalytics**脚本，该脚本负责：</span><span class="sxs-lookup"><span data-stu-id="98bf4-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="98bf4-376">正在获取有关照相机最接近哪个对象的分析数据。</span><span class="sxs-lookup"><span data-stu-id="98bf4-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="98bf4-377">使用*服务密钥*，这允许与 Azure 应用程序 Insights 服务实例通信。</span><span class="sxs-lookup"><span data-stu-id="98bf4-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="98bf4-378">根据具有最高事件计数的场景中的对象进行排序。</span><span class="sxs-lookup"><span data-stu-id="98bf4-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="98bf4-379">将最接近的对象的材料颜色更改为*绿色*。</span><span class="sxs-lookup"><span data-stu-id="98bf4-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="98bf4-380">创建脚本：</span><span class="sxs-lookup"><span data-stu-id="98bf4-380">To create the script:</span></span>

1.  <span data-ttu-id="98bf4-381">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="98bf4-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="98bf4-382">右键单击 "**脚本**" 文件夹中，单击 "**创建** >  **C#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="98bf4-383">将脚本命名为**DataFromAnalytics**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="98bf4-384">双击脚本以通过 Visual Studio 打开它。</span><span class="sxs-lookup"><span data-stu-id="98bf4-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="98bf4-385">插入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="98bf4-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="98bf4-386">在脚本中，插入以下内容：</span><span class="sxs-lookup"><span data-stu-id="98bf4-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="98bf4-387">在**DataFromAnalytics**类中，在**Start （）** 方法的后面添加以下名为**FetchAnalytics （）** 的方法。</span><span class="sxs-lookup"><span data-stu-id="98bf4-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="98bf4-388">此方法负责填充键值对的列表，其中包含*GameObject*和占位符事件计数号。</span><span class="sxs-lookup"><span data-stu-id="98bf4-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="98bf4-389">然后初始化**GetWebRequest （）** 协同程序。</span><span class="sxs-lookup"><span data-stu-id="98bf4-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="98bf4-390">在此方法中，还可以找到对*Application Insights*的调用的查询结构，作为*查询 URL*终结点。</span><span class="sxs-lookup"><span data-stu-id="98bf4-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="98bf4-391">在**FetchAnalytics （）** 方法的下方，添加一个名为**GetWebRequest （）** 的方法，该方法将返回*IEnumerator*。</span><span class="sxs-lookup"><span data-stu-id="98bf4-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="98bf4-392">此方法负责请求在*Application Insights*中调用与特定*GameObject*对应的事件次数。</span><span class="sxs-lookup"><span data-stu-id="98bf4-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="98bf4-393">所有发送的查询都返回后，将调用**DetermineWinner （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="98bf4-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="98bf4-394">下一方法为**DetermineWinner （）** ，该方法根据最大事件计数对*GameObject*和*Int*对的列表进行排序。</span><span class="sxs-lookup"><span data-stu-id="98bf4-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="98bf4-395">然后，它会将该*GameObject*的材料颜色更改为*绿色*（作为其最大计数的反馈）。</span><span class="sxs-lookup"><span data-stu-id="98bf4-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="98bf4-396">这将显示一条包含分析结果的消息。</span><span class="sxs-lookup"><span data-stu-id="98bf4-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="98bf4-397">添加用来反序列化从*Application Insights*接收的 JSON 对象的类结构。</span><span class="sxs-lookup"><span data-stu-id="98bf4-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="98bf4-398">将这些类添加到类定义**之外**的**DataFromAnalytics**类文件的最底部。</span><span class="sxs-lookup"><span data-stu-id="98bf4-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="98bf4-399">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="98bf4-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="98bf4-400">第10章-创建移动类</span><span class="sxs-lookup"><span data-stu-id="98bf4-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="98bf4-401">**移动**脚本是需要创建的下一个脚本。</span><span class="sxs-lookup"><span data-stu-id="98bf4-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="98bf4-402">它负责：</span><span class="sxs-lookup"><span data-stu-id="98bf4-402">It is responsible for:</span></span>

- <span data-ttu-id="98bf4-403">根据相机正在寻找的方向移动主摄像机。</span><span class="sxs-lookup"><span data-stu-id="98bf4-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="98bf4-404">将所有其他脚本添加到场景对象。</span><span class="sxs-lookup"><span data-stu-id="98bf4-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="98bf4-405">创建脚本：</span><span class="sxs-lookup"><span data-stu-id="98bf4-405">To create the script:</span></span>

1.  <span data-ttu-id="98bf4-406">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="98bf4-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="98bf4-407">右键单击 "**脚本**" 文件夹中，单击 "**创建** >  **C#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="98bf4-408">命名脚本**移动**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="98bf4-409">双击脚本以通过*Visual Studio*打开它。</span><span class="sxs-lookup"><span data-stu-id="98bf4-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="98bf4-410">将现有代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="98bf4-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="98bf4-411">在**移动**类中的空**Update （）** 方法*下*，插入以下允许用户使用手形控制器移动到虚拟空间中的方法：</span><span class="sxs-lookup"><span data-stu-id="98bf4-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="98bf4-412">最后，在**Update （）** 方法内添加方法调用。</span><span class="sxs-lookup"><span data-stu-id="98bf4-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="98bf4-413">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="98bf4-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="98bf4-414">第11章-设置脚本引用</span><span class="sxs-lookup"><span data-stu-id="98bf4-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="98bf4-415">在本章中，需要将**移动**脚本放到**相机父节点**上，并设置其引用目标。</span><span class="sxs-lookup"><span data-stu-id="98bf4-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="98bf4-416">然后，该脚本会处理需要的其他脚本。</span><span class="sxs-lookup"><span data-stu-id="98bf4-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="98bf4-417">从 "*项目" 面板*的 "**脚本**" 文件夹中，将**移动**脚本拖到 "*层次结构" 面板*中的 "**相机父**对象"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![设置 Unity 场景中的脚本引用](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="98bf4-419">单击 "**照相机" 父项**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="98bf4-420">在 "*层次结构" 面板*中，将**右侧**对象从 "*层次结构" 面板*拖动到 "*检查器" 面板*中的引用目标**控制器**。</span><span class="sxs-lookup"><span data-stu-id="98bf4-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="98bf4-421">将**用户速度**设置为**5**，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="98bf4-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![设置 Unity 场景中的脚本引用](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="98bf4-423">第12章-生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="98bf4-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="98bf4-424">此项目的 Unity 部分所需的所有内容现在均已完成，因此可以从 Unity 构建它。</span><span class="sxs-lookup"><span data-stu-id="98bf4-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="98bf4-425">导航到 "**生成设置**" （**文件** > **生成设置**）。</span><span class="sxs-lookup"><span data-stu-id="98bf4-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="98bf4-426">在**生成设置**窗口中，单击 "**生成**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-426">From the **Build Settings** window, click **Build**.</span></span>

    ![将 Unity 项目生成到 UWP 解决方案](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="98bf4-428">将弹出一个 "**文件资源管理器**" 窗口，提示你输入生成的位置。</span><span class="sxs-lookup"><span data-stu-id="98bf4-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="98bf4-429">在左上角单击 "**新建文件夹**"，创建一个新文件夹，并将其命名为 "**生成**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![将 Unity 项目生成到 UWP 解决方案](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="98bf4-431">打开 "新建**生成**" 文件夹，并创建另一个文件夹（使用 "**新文件夹**"），并将其命名为 " **MR\_Azure\_application\_Insights**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![将 Unity 项目生成到 UWP 解决方案](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="98bf4-433">选中 "**尊敬的\_Azure\_应用程序\_Insights** " 文件夹，单击 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="98bf4-434">项目将需要一分钟或更长时间才能生成。</span><span class="sxs-lookup"><span data-stu-id="98bf4-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="98bf4-435">以下*生成*将显示**文件资源管理器**，显示新项目的位置。</span><span class="sxs-lookup"><span data-stu-id="98bf4-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a><span data-ttu-id="98bf4-436">第13章-将 MR_Azure_Application_Insights 应用部署到计算机</span><span class="sxs-lookup"><span data-stu-id="98bf4-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="98bf4-437">若要在本地计算机上部署**Azure\_应用程序\_的 MR\_** ，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="98bf4-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="98bf4-438">在**Visual Studio**中打开**Azure\_application\_Insights 应用的 MR\_** 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="98bf4-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="98bf4-439">在**解决方案平台**中，选择 " **X86，本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="98bf4-440">在**解决方案配置**中，选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="98bf4-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![将 Unity 项目生成到 UWP 解决方案](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="98bf4-442">中转到 "**生成" 菜单**，然后单击 "**部署解决方案**"，将应用程序旁加载到计算机上。</span><span class="sxs-lookup"><span data-stu-id="98bf4-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="98bf4-443">应用现在应显示在已安装的应用列表中，可以启动。</span><span class="sxs-lookup"><span data-stu-id="98bf4-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="98bf4-444">启动混合现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="98bf4-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="98bf4-445">在场景中四处移动，接近对象并进行查看，当*Azure 见解服务*收集了足够的事件数据时，它会将最接近绿色的对象设置为最接近绿色的对象。</span><span class="sxs-lookup"><span data-stu-id="98bf4-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="98bf4-446">尽管服务收集*事件和指标*的平均等待时间大约需要15分钟，但在某些情况下，可能需要长达1小时的时间。</span><span class="sxs-lookup"><span data-stu-id="98bf4-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="98bf4-447">第14章-Application Insights 服务门户</span><span class="sxs-lookup"><span data-stu-id="98bf4-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="98bf4-448">漫游场景并在多个对象上 gazed 时，可以看到*Application Insights 服务*门户中收集的数据。</span><span class="sxs-lookup"><span data-stu-id="98bf4-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="98bf4-449">返回 Application Insights 服务门户。</span><span class="sxs-lookup"><span data-stu-id="98bf4-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="98bf4-450">单击*指标资源管理器*。</span><span class="sxs-lookup"><span data-stu-id="98bf4-450">Click on *Metrics Explorer*.</span></span>

    ![查看收集的数据](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="98bf4-452">它将在一个包含关系图的选项卡中打开，该图形表示与应用程序相关的*事件和指标*。</span><span class="sxs-lookup"><span data-stu-id="98bf4-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="98bf4-453">如上所述，在图形中显示数据可能需要一些时间（最长为1小时）</span><span class="sxs-lookup"><span data-stu-id="98bf4-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![查看收集的数据](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="98bf4-455">单击 "按应用程序版本列出的*事件总数*" 中的 "*事件*"，以查看事件及其名称的详细明细。</span><span class="sxs-lookup"><span data-stu-id="98bf4-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![查看收集的数据](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="98bf4-457">已完成 Application Insights 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="98bf4-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="98bf4-458">恭喜，你构建了一个混合现实应用，它利用 Application Insights 服务来监视你的应用中的用户活动。</span><span class="sxs-lookup"><span data-stu-id="98bf4-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![课程结果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="98bf4-460">额外练习</span><span class="sxs-lookup"><span data-stu-id="98bf4-460">Bonus Exercises</span></span>

<span data-ttu-id="98bf4-461">**练习1**</span><span class="sxs-lookup"><span data-stu-id="98bf4-461">**Exercise 1**</span></span>

<span data-ttu-id="98bf4-462">尝试生成，而不是手动创建 ObjectInScene 对象，并在脚本内的平面上设置它们的坐标。</span><span class="sxs-lookup"><span data-stu-id="98bf4-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="98bf4-463">通过这种方式，你可以询问 Azure 最常见的对象是什么（从注视或邻近的结果）并生成一个*额外*的对象。</span><span class="sxs-lookup"><span data-stu-id="98bf4-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="98bf4-464">**练习2**</span><span class="sxs-lookup"><span data-stu-id="98bf4-464">**Exercise 2**</span></span>

<span data-ttu-id="98bf4-465">按时间对 Application Insights 结果进行排序，以便获取最相关的数据，并在应用程序中实现该时间敏感的数据。</span><span class="sxs-lookup"><span data-stu-id="98bf4-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

