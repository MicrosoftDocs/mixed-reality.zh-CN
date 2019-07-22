---
title: MR 和 Azure 309-Application insights
description: 完成此课程以了解如何收集有关在混合的现实应用程序中的用户行为，请使用 Azure Application Insights 服务的分析。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 应用程序见解，沉浸式、 hololens、 vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694562"
---
>[!NOTE]
><span data-ttu-id="1229d-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="1229d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1229d-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="1229d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1229d-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="1229d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1229d-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="1229d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1229d-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="1229d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1229d-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="1229d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="1229d-110">MR 和 Azure 309:应用程序见解</span><span class="sxs-lookup"><span data-stu-id="1229d-110">MR and Azure 309: Application insights</span></span>

![最终产品-启动](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="1229d-112">在本课程中，您将学习如何将 Application Insights 功能添加到混合的现实应用程序，使用 Azure Application Insights API 收集有关用户行为分析。</span><span class="sxs-lookup"><span data-stu-id="1229d-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="1229d-113">Application Insights 是 Microsoft 服务，从而允许开发人员从其应用程序收集分析数据和从易于使用门户管理。</span><span class="sxs-lookup"><span data-stu-id="1229d-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="1229d-114">分析可以是任何内容，从你想要收集的自定义信息的性能。</span><span class="sxs-lookup"><span data-stu-id="1229d-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="1229d-115">有关详细信息，请访问[Application Insights 页](https://azure.microsoft.com/services/application-insights/)。</span><span class="sxs-lookup"><span data-stu-id="1229d-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="1229d-116">已完成本课程，会创建一个混合的现实沉浸式头戴式应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1229d-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="1229d-117">允许用户注视和场景中移动。</span><span class="sxs-lookup"><span data-stu-id="1229d-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="1229d-118">触发的分析，以发送*Application Insights 服务*、 通过使用提供注视和邻近场景中的对象。</span><span class="sxs-lookup"><span data-stu-id="1229d-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="1229d-119">应用还将在提取信息有关的对象已被用户，最接近过去 24 小时内的服务时调用。</span><span class="sxs-lookup"><span data-stu-id="1229d-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="1229d-120">该对象将更改其颜色为绿色。</span><span class="sxs-lookup"><span data-stu-id="1229d-120">That object will change its color to green.</span></span>

<span data-ttu-id="1229d-121">本课程将介绍如何为基于 Unity 的示例应用程序从 Application Insights 服务，获取结果。</span><span class="sxs-lookup"><span data-stu-id="1229d-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="1229d-122">它将取决于您要应用于您可能要构建一个自定义应用程序的这些概念。</span><span class="sxs-lookup"><span data-stu-id="1229d-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="1229d-123">设备支持</span><span class="sxs-lookup"><span data-stu-id="1229d-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1229d-124">课程</span><span class="sxs-lookup"><span data-stu-id="1229d-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1229d-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1229d-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1229d-126"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="1229d-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1229d-127">MR 和 Azure 309:应用程序见解</span><span class="sxs-lookup"><span data-stu-id="1229d-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="1229d-128">✔️</span><span class="sxs-lookup"><span data-stu-id="1229d-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1229d-129">✔️</span><span class="sxs-lookup"><span data-stu-id="1229d-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1229d-130">尽管本课程主要专注于 Windows Mixed Reality 沉浸式 (VR) 耳机，还可以应用到 Microsoft HoloLens 本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="1229d-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="1229d-131">按照课程时，您将看到说明您可能需要使用以支持 HoloLens 的任何更改。</span><span class="sxs-lookup"><span data-stu-id="1229d-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="1229d-132">使用 HoloLens，您可能注意到某些 echo 语音捕获过程。</span><span class="sxs-lookup"><span data-stu-id="1229d-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1229d-133">先决条件</span><span class="sxs-lookup"><span data-stu-id="1229d-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1229d-134">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="1229d-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1229d-135">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。</span><span class="sxs-lookup"><span data-stu-id="1229d-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="1229d-136">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。</span><span class="sxs-lookup"><span data-stu-id="1229d-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="1229d-137">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="1229d-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1229d-138">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="1229d-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1229d-139">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="1229d-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1229d-140">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1229d-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1229d-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="1229d-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1229d-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1229d-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="1229d-143">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="1229d-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="1229d-144">一组的耳机使用内置的麦克风 （如果耳机不具有内置的麦克风和扬声器）</span><span class="sxs-lookup"><span data-stu-id="1229d-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="1229d-145">Internet 访问的 Azure 设置和 Application Insights 数据检索</span><span class="sxs-lookup"><span data-stu-id="1229d-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1229d-146">开始之前</span><span class="sxs-lookup"><span data-stu-id="1229d-146">Before you start</span></span>

<span data-ttu-id="1229d-147">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="1229d-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="1229d-148">请注意，将数据*Application Insights*花费的时间，因此请耐心等待。</span><span class="sxs-lookup"><span data-stu-id="1229d-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="1229d-149">如果你想要检查此服务已收到你的数据，请查看[第 14 章](#chapter-14---the-application-insights-service-portal)，这将向您演示如何在门户中导航。</span><span class="sxs-lookup"><span data-stu-id="1229d-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="1229d-150">第 1 章-Azure 门户</span><span class="sxs-lookup"><span data-stu-id="1229d-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="1229d-151">若要使用*Application Insights*，将需要创建和配置*Application Insights 服务*在 Azure 门户中。</span><span class="sxs-lookup"><span data-stu-id="1229d-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="1229d-152">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="1229d-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="1229d-153">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="1229d-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1229d-154">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="1229d-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1229d-155">你登录后，单击**新建**在左上角，并搜索*Application Insights*，然后单击**Enter**。</span><span class="sxs-lookup"><span data-stu-id="1229d-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1229d-156">单词**新建**可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="1229d-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="1229d-158">向右该新页面将提供的说明*Azure Application Insights*服务。</span><span class="sxs-lookup"><span data-stu-id="1229d-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="1229d-159">在左下角此页上，选择**创建**按钮，以创建与此关联服务。</span><span class="sxs-lookup"><span data-stu-id="1229d-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="1229d-161">一旦你单击**创建**:</span><span class="sxs-lookup"><span data-stu-id="1229d-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="1229d-162">插入所需**名称**此服务实例。</span><span class="sxs-lookup"><span data-stu-id="1229d-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="1229d-163">作为**应用程序类型**，选择**常规**。</span><span class="sxs-lookup"><span data-stu-id="1229d-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="1229d-164">选择相应**订阅**。</span><span class="sxs-lookup"><span data-stu-id="1229d-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="1229d-165">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="1229d-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1229d-166">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="1229d-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1229d-167">建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。</span><span class="sxs-lookup"><span data-stu-id="1229d-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="1229d-168">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="1229d-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="1229d-169">选择**位置**。</span><span class="sxs-lookup"><span data-stu-id="1229d-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="1229d-170">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="1229d-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="1229d-171">选择“创建”  。</span><span class="sxs-lookup"><span data-stu-id="1229d-171">Select **Create**.</span></span>

        ![Azure 门户](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="1229d-173">一旦你单击**创建**，将需要等待要创建的服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="1229d-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="1229d-174">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="1229d-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="1229d-176">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="1229d-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="1229d-178">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="1229d-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="1229d-179">你将会转到新*Application Insights 服务*实例。</span><span class="sxs-lookup"><span data-stu-id="1229d-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="1229d-181">保持此 web 页面打开并且易于访问，你将返回到此处通常以查看收集的数据。</span><span class="sxs-lookup"><span data-stu-id="1229d-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="1229d-182">若要实现 Application Insights，你将需要使用三 （3） 的特定值：**检测密钥**，**应用程序 ID**，和**API 密钥**。</span><span class="sxs-lookup"><span data-stu-id="1229d-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="1229d-183">下面您将了解如何从你的服务中检索这些值。</span><span class="sxs-lookup"><span data-stu-id="1229d-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="1229d-184">请务必记下这些值在空白*记事本*页上，因为在代码中，将很快使用它们。</span><span class="sxs-lookup"><span data-stu-id="1229d-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="1229d-185">若要查找**检测密钥**，将需要向下滚动服务函数列表，然后单击**属性**，显示选项卡将显示**服务密钥**。</span><span class="sxs-lookup"><span data-stu-id="1229d-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="1229d-187">有点下面**属性**，将为您**API 访问**，您需要单击。</span><span class="sxs-lookup"><span data-stu-id="1229d-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="1229d-188">右侧面板将提供**应用程序 ID**的您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="1229d-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="1229d-190">与**应用程序 ID**面板保持打开，单击**创建 API 密钥**，这将打开*创建 API 密钥*面板。</span><span class="sxs-lookup"><span data-stu-id="1229d-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure 门户](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="1229d-192">现在打开内*创建 API 密钥*面板中，键入描述，并**选中三个框**。</span><span class="sxs-lookup"><span data-stu-id="1229d-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="1229d-193">单击**生成密钥**。</span><span class="sxs-lookup"><span data-stu-id="1229d-193">Click **Generate Key**.</span></span> <span data-ttu-id="1229d-194">你**API 密钥**将创建并显示。</span><span class="sxs-lookup"><span data-stu-id="1229d-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure 门户](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="1229d-196">这是唯一一次你**服务密钥**将显示，因此请确保您现在制作一份。</span><span class="sxs-lookup"><span data-stu-id="1229d-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="1229d-197">第 2 章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="1229d-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="1229d-198">以下是一组典型使用混合现实中，进行开发，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="1229d-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1229d-199">打开*Unity*然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="1229d-199">Open *Unity* and click **New**.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="1229d-201">现在将需要提供 Unity 项目的名称，插入**MR\_Azure\_应用程序\_Insights**。</span><span class="sxs-lookup"><span data-stu-id="1229d-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="1229d-202">请确保*模板*设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="1229d-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="1229d-203">设置*位置*到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="1229d-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1229d-204">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="1229d-204">Then, click **Create project**.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="1229d-206">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="1229d-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1229d-207">转到**编辑\>首选项**，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="1229d-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1229d-208">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="1229d-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1229d-209">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="1229d-209">Close the **Preferences** window.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="1229d-211">接下来，请转到**文件\>生成设置**，并切换到平台**通用 Windows 平台**，通过单击**切换平台**按钮。</span><span class="sxs-lookup"><span data-stu-id="1229d-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="1229d-213">转到**文件\>生成设置**并确保选中：</span><span class="sxs-lookup"><span data-stu-id="1229d-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="1229d-214">**设备为目标**设置为**任何设备**</span><span class="sxs-lookup"><span data-stu-id="1229d-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="1229d-215">对于 Microsoft HoloLens，设置**目标设备**到*HoloLens*。</span><span class="sxs-lookup"><span data-stu-id="1229d-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="1229d-216">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="1229d-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="1229d-217">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="1229d-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="1229d-218">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="1229d-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="1229d-219">保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="1229d-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="1229d-220">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="1229d-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1229d-221">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="1229d-221">A save window will appear.</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="1229d-223">为此，和任何将来的场景，创建新文件夹，然后单击**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="1229d-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="1229d-225">打开新建**场景**文件夹，然后在*文件名：* 文本字段中，键入**ApplicationInsightsScene**，然后单击**保存**.</span><span class="sxs-lookup"><span data-stu-id="1229d-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="1229d-227">中的剩余设置，**生成设置**，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="1229d-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="1229d-228">在**生成设置**窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。</span><span class="sxs-lookup"><span data-stu-id="1229d-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![设置 Unity 项目](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="1229d-230">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="1229d-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="1229d-231">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="1229d-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="1229d-232">**脚本编写** **运行时版本**应**实验 （.NET 4.6 等效）** ，这将触发需要重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="1229d-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="1229d-233">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="1229d-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="1229d-234">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="1229d-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="1229d-236">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="1229d-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="1229d-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1229d-237">**InternetClient**</span></span>     

            ![设置 Unity 项目](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="1229d-239">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows Mixed RealitySDK**添加。</span><span class="sxs-lookup"><span data-stu-id="1229d-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="1229d-241">回到**生成设置**， **UnityC#项目**不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="1229d-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="1229d-242">关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="1229d-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="1229d-243">保存您的场景和项目 (**文件** > **保存场景文件** > **保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="1229d-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="1229d-244">第 3 章-导入 Unity 程序包</span><span class="sxs-lookup"><span data-stu-id="1229d-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1229d-245">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[Azure MR 309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)，将其导入项目中，作为[**自定义软件包**](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="1229d-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="1229d-246">这还将包含下一章中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="1229d-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="1229d-247">导入后，继续从[**第 6 章**](#chapter-6---create-the-applicationinsightstracker-class)。</span><span class="sxs-lookup"><span data-stu-id="1229d-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1229d-248">若要使用 Application Insights 在 Unity 中，需要导入 DLL，以及 Newtonsoft DLL。</span><span class="sxs-lookup"><span data-stu-id="1229d-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="1229d-249">这要求要导入后重新配置的插件的 Unity 中目前的已知的问题。</span><span class="sxs-lookup"><span data-stu-id="1229d-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="1229d-250">这些步骤 (4-7 在本部分中) 将不再需要后解决此 bug。</span><span class="sxs-lookup"><span data-stu-id="1229d-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="1229d-251">若要导入到你自己的项目的 Application Insights，请确保你有[下载.unitypackage，包含插件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="1229d-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="1229d-252">然后，执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1229d-252">Then, do the following:</span></span>

1.  <span data-ttu-id="1229d-253">添加 **.unitypackage**到使用 Unity**资产\>导入包\>自定义包**菜单选项。</span><span class="sxs-lookup"><span data-stu-id="1229d-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="1229d-254">在中**导入 Unity 程序包**弹出框、 下 （其中包含） 确保一切**插件**处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="1229d-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![导入 Unity 程序包](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="1229d-256">单击**导入**按钮，将项添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="1229d-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="1229d-257">转到**Insights**下的文件夹**插件**项目中查看并选择以下插件*仅*:</span><span class="sxs-lookup"><span data-stu-id="1229d-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="1229d-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="1229d-258">Microsoft.ApplicationInsights</span></span>

    ![导入 Unity 程序包](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="1229d-260">与此*插件*选择，确保**Any 平台**是**未选中**，然后确保**WSAPlayer**也是**取消选中**，然后单击**应用**。</span><span class="sxs-lookup"><span data-stu-id="1229d-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="1229d-261">执行此操作是只是为了确认正确配置文件。</span><span class="sxs-lookup"><span data-stu-id="1229d-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![导入 Unity 程序包](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="1229d-263">将标记此类的插件，将它们配置为仅使用在 Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="1229d-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="1229d-264">有一组不同的 Dll 从 Unity 项目会导出后，将使用 WSA 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="1229d-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="1229d-265">接下来，您需要打开**WSA**文件夹，在**Insights**文件夹。</span><span class="sxs-lookup"><span data-stu-id="1229d-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="1229d-266">您将看到刚配置的相同文件的副本。</span><span class="sxs-lookup"><span data-stu-id="1229d-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="1229d-267">选择此文件，然后再检查器中，请确保**Any 平台**是**取消选中**，然后确保**仅** **WSAPlayer**是**检查**。</span><span class="sxs-lookup"><span data-stu-id="1229d-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="1229d-268">单击 **“应用”** 。</span><span class="sxs-lookup"><span data-stu-id="1229d-268">Click **Apply**.</span></span>

    ![导入 Unity 程序包](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="1229d-270">现在需要遵循**步骤 4-6**，但对于*Newtonsoft*插件相反。</span><span class="sxs-lookup"><span data-stu-id="1229d-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="1229d-271">请参阅下面的屏幕快照的结果应如下所示。</span><span class="sxs-lookup"><span data-stu-id="1229d-271">See the below screenshot for what the outcome should look like.</span></span>

    ![导入 Unity 程序包](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="1229d-273">第 4 章-设置相机和用户控件</span><span class="sxs-lookup"><span data-stu-id="1229d-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="1229d-274">在这一章中您将设置照相机和控件允许用户查看和在场景中移动。</span><span class="sxs-lookup"><span data-stu-id="1229d-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="1229d-275">右键单击空白区域在层次结构窗格中，然后**创建** > **空**。</span><span class="sxs-lookup"><span data-stu-id="1229d-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![设置相机和用户控件](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="1229d-277">重命名为新的空 GameObject**照相机父**。</span><span class="sxs-lookup"><span data-stu-id="1229d-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![设置相机和用户控件](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="1229d-279">右键单击空白区域在层次结构窗格中，然后**3D 物体**，然后在**球体**。</span><span class="sxs-lookup"><span data-stu-id="1229d-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="1229d-280">重命名为球体**右侧**。</span><span class="sxs-lookup"><span data-stu-id="1229d-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="1229d-281">设置**转换规模**的向右**0.1，0.1，0.1**</span><span class="sxs-lookup"><span data-stu-id="1229d-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![设置相机和用户控件](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="1229d-283">删除**球体碰撞体**组件从通过单击右侧**齿轮**中*球体碰撞体*组件，然后**删除组件**.</span><span class="sxs-lookup"><span data-stu-id="1229d-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![设置相机和用户控件](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="1229d-285">在层次结构面板拖动**Main Camera**并**右下**对象上**照相机父**对象。</span><span class="sxs-lookup"><span data-stu-id="1229d-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![设置相机和用户控件](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="1229d-287">设置**转换位置**两个**Main Camera**并**右侧**对象传递给**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="1229d-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![设置相机和用户控件](images/AzureLabs-Lab309-31.png)

    ![设置相机和用户控件](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="1229d-290">第 5 章-设置在 Unity 场景中的对象</span><span class="sxs-lookup"><span data-stu-id="1229d-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="1229d-291">现在将为您的场景，用户可与之交互创建一些基本形状。</span><span class="sxs-lookup"><span data-stu-id="1229d-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="1229d-292">在中的空白区域中单击右键*层次结构面板*，然后在**3D 物体**，然后选择**平面**。</span><span class="sxs-lookup"><span data-stu-id="1229d-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="1229d-293">设置在平面**转换位置**到**0，-1，0**。</span><span class="sxs-lookup"><span data-stu-id="1229d-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="1229d-294">设置在平面**转换规模**到**5、 1、 5**。</span><span class="sxs-lookup"><span data-stu-id="1229d-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="1229d-296">创建基本材料要用于你**平面**对象，以便更轻松地查看其他形状。</span><span class="sxs-lookup"><span data-stu-id="1229d-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="1229d-297">导航到您*项目面板*，右键单击，然后**创建**后, 跟**文件夹**，以创建新的文件夹。</span><span class="sxs-lookup"><span data-stu-id="1229d-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="1229d-298">其命名为**材料**。</span><span class="sxs-lookup"><span data-stu-id="1229d-298">Name it **Materials**.</span></span>

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-34.png) ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="1229d-301">打开**材料**文件夹，然后右键单击，单击**创建**，然后**材料**，以创建新材料。</span><span class="sxs-lookup"><span data-stu-id="1229d-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="1229d-302">其命名为**蓝色**。</span><span class="sxs-lookup"><span data-stu-id="1229d-302">Name it **Blue**.</span></span>

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-36.png) ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="1229d-305">与新**蓝色**材料，看在选择*Inspector*，然后单击矩形窗口中的以及**Albedo**。</span><span class="sxs-lookup"><span data-stu-id="1229d-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="1229d-306">选择蓝色颜色 (如下一个图是**十六进制颜色：\#3592FFFF**)。</span><span class="sxs-lookup"><span data-stu-id="1229d-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="1229d-307">选择后，请单击关闭按钮。</span><span class="sxs-lookup"><span data-stu-id="1229d-307">Click the close button once you have chosen.</span></span>

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="1229d-309">将从你新材料**材料**文件夹中的，拖动到新创建**平面**，在您的场景中 (或将其放在**平面**对象内*层次结构*)。</span><span class="sxs-lookup"><span data-stu-id="1229d-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="1229d-311">在中的空白区域中单击右键*层次结构面板*，然后在**三维对象、 Capsule**。</span><span class="sxs-lookup"><span data-stu-id="1229d-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="1229d-312">与**Capsule**选择，更改其**转换** *位置*到： **-10、 1、 0**。</span><span class="sxs-lookup"><span data-stu-id="1229d-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="1229d-313">在中的空白区域中单击右键*层次结构面板*，然后在**三维对象、 多维数据集**。</span><span class="sxs-lookup"><span data-stu-id="1229d-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="1229d-314">与**多维数据集**选择，更改其**转换** *位置*到：**0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="1229d-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="1229d-315">在中的空白区域中单击右键*层次结构面板*，然后在**三维对象、 球体**。</span><span class="sxs-lookup"><span data-stu-id="1229d-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="1229d-316">与 **球体** 选择，更改其 **转换** *位置* 到：**10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="1229d-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="1229d-318">这些*位置*的值为*建议*。</span><span class="sxs-lookup"><span data-stu-id="1229d-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="1229d-319">你可以随意设置对象的位置为喜好，但如果对象距离是不与相机距离太远，则应用程序的用户更容易。</span><span class="sxs-lookup"><span data-stu-id="1229d-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="1229d-320">当运行你的应用程序时，它需要能够识别中的场景，来实现此目的的对象，它们需要进行标记。</span><span class="sxs-lookup"><span data-stu-id="1229d-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="1229d-321">选择一个对象，并在*Inspector*面板中，单击**添加标记...** ，这会交换*Inspector*与**标记和分层式**面板。</span><span class="sxs-lookup"><span data-stu-id="1229d-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="1229d-322">![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="1229d-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="1229d-323">单击 **+ （加）** 符号，然后键入标记名称作为**ObjectInScene**。</span><span class="sxs-lookup"><span data-stu-id="1229d-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="1229d-325">如果使用你的标记的不同名称，您需要确保还进行此更改*DataFromAnalytics*， *ObjectTrigger*，并*注视*，更高版本，脚本，以便你对象发现，并检测到，在您的场景。</span><span class="sxs-lookup"><span data-stu-id="1229d-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="1229d-326">使用创建的标记，现在需要将其应用于所有这三个对象。</span><span class="sxs-lookup"><span data-stu-id="1229d-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="1229d-327">从*层次结构*，保存**Shift**键，然后单击**Capsule**，**多维数据集**，并**球体**，对象，然后在*Inspector*，单击旁边的下拉列表菜单**标记**，然后单击*ObjectInScene*标记创建。</span><span class="sxs-lookup"><span data-stu-id="1229d-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="1229d-328">![设置在 Unity 场景中的对象](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="1229d-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="1229d-329">章 6-创建 ApplicationInsightsTracker 类</span><span class="sxs-lookup"><span data-stu-id="1229d-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="1229d-330">您需要创建的第一个脚本是**ApplicationInsightsTracker**，负责：</span><span class="sxs-lookup"><span data-stu-id="1229d-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="1229d-331">创建基于用户交互要提交到 Azure Application Insights 的事件。</span><span class="sxs-lookup"><span data-stu-id="1229d-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="1229d-332">正在创建相应的事件名称，具体取决于用户交互。</span><span class="sxs-lookup"><span data-stu-id="1229d-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="1229d-333">正在提交到 Application Insights 服务实例的事件。</span><span class="sxs-lookup"><span data-stu-id="1229d-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="1229d-334">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="1229d-334">To create this class:</span></span>

1.  <span data-ttu-id="1229d-335">在中右击*项目面板*，然后**创建** > **文件夹**。</span><span class="sxs-lookup"><span data-stu-id="1229d-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="1229d-336">将文件夹命名为**脚本**。</span><span class="sxs-lookup"><span data-stu-id="1229d-336">Name the folder **Scripts**.</span></span>

    ![创建 ApplicationInsightsTracker 类](images/AzureLabs-Lab309-46.png)  ![创建 ApplicationInsightsTracker 类](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="1229d-339">与**脚本**创建文件夹，双击它，以打开。</span><span class="sxs-lookup"><span data-stu-id="1229d-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="1229d-340">然后，在该文件夹中，右键单击，**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="1229d-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="1229d-341">脚本命名为**ApplicationInsightsTracker**。</span><span class="sxs-lookup"><span data-stu-id="1229d-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="1229d-342">双击新**ApplicationInsightsTracker**脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="1229d-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="1229d-343">更新的脚本在顶部的命名空间如下所示：</span><span class="sxs-lookup"><span data-stu-id="1229d-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="1229d-344">在类中插入以下变量：</span><span class="sxs-lookup"><span data-stu-id="1229d-344">Inside the class insert the following variables:</span></span>

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
    > <span data-ttu-id="1229d-345">设置**instrumentationKey，applicationId 和 API_Key**相应地，使用值*服务密钥*从 Azure 门户中所述[第 1 章](#chapter-1---the-azure-portal)，步骤 9及更高版本。</span><span class="sxs-lookup"><span data-stu-id="1229d-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="1229d-346">然后添加**start （)** 并**Awake()** 类初始化时将调用的方法：</span><span class="sxs-lookup"><span data-stu-id="1229d-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="1229d-347">添加负责发送的事件和指标注册你的应用程序的方法：</span><span class="sxs-lookup"><span data-stu-id="1229d-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

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

8.  <span data-ttu-id="1229d-348">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="1229d-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="1229d-349">章 7-创建的视线移动脚本</span><span class="sxs-lookup"><span data-stu-id="1229d-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="1229d-350">要创建的下一步脚本位于**注视**脚本。</span><span class="sxs-lookup"><span data-stu-id="1229d-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="1229d-351">此脚本负责创建*Raycast*会从转发投影的*Main Camera*，以检测用户查看的对象。</span><span class="sxs-lookup"><span data-stu-id="1229d-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="1229d-352">在这种情况下， *Raycast*需要确定如果用户正在查看的对象**ObjectInScene**标记，并将然后计算时间用户*gazes*在该对象。</span><span class="sxs-lookup"><span data-stu-id="1229d-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="1229d-353">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="1229d-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="1229d-354">内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="1229d-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="1229d-355">脚本命名为**注视**。</span><span class="sxs-lookup"><span data-stu-id="1229d-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="1229d-356">双击要使用 Visual Studio 中打开的脚本。</span><span class="sxs-lookup"><span data-stu-id="1229d-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="1229d-357">现有代码替换为以下：</span><span class="sxs-lookup"><span data-stu-id="1229d-357">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="1229d-358">为代码**Awake()** 并**start （)** 方法现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="1229d-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

6.  <span data-ttu-id="1229d-359">内部**注视**类中，添加下面的代码**update （)** 到项目的方法*Raycast*和检测对目标的影响：</span><span class="sxs-lookup"><span data-stu-id="1229d-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

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

7.  <span data-ttu-id="1229d-360">添加**ResetFocusedObject()** 方法，以将数据发送到**Application Insights**时用户已介绍了一个对象。</span><span class="sxs-lookup"><span data-stu-id="1229d-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

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

8.  <span data-ttu-id="1229d-361">现在已完成**注视**脚本。</span><span class="sxs-lookup"><span data-stu-id="1229d-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="1229d-362">保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="1229d-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="1229d-363">章 8-创建 ObjectTrigger 类</span><span class="sxs-lookup"><span data-stu-id="1229d-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="1229d-364">若要创建所需的下一个脚本是**ObjectTrigger**，负责：</span><span class="sxs-lookup"><span data-stu-id="1229d-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="1229d-365">添加到 Main Camera 冲突所需的组件。</span><span class="sxs-lookup"><span data-stu-id="1229d-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="1229d-366">检测相机是否标记为的对象附近**ObjectInScene**。</span><span class="sxs-lookup"><span data-stu-id="1229d-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="1229d-367">若要创建脚本：</span><span class="sxs-lookup"><span data-stu-id="1229d-367">To create the script:</span></span>

1.  <span data-ttu-id="1229d-368">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="1229d-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="1229d-369">内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="1229d-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="1229d-370">脚本命名为**ObjectTrigger**。</span><span class="sxs-lookup"><span data-stu-id="1229d-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="1229d-371">双击要使用 Visual Studio 中打开的脚本。</span><span class="sxs-lookup"><span data-stu-id="1229d-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="1229d-372">现有代码替换为以下：</span><span class="sxs-lookup"><span data-stu-id="1229d-372">Replace the existing code with the following:</span></span>

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

4.  <span data-ttu-id="1229d-373">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="1229d-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="1229d-374">章 9-创建 DataFromAnalytics 类</span><span class="sxs-lookup"><span data-stu-id="1229d-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="1229d-375">您现在需要创建**DataFromAnalytics**脚本，它负责：</span><span class="sxs-lookup"><span data-stu-id="1229d-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="1229d-376">正在提取有关哪些对象具有已接近相机最多的分析数据。</span><span class="sxs-lookup"><span data-stu-id="1229d-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="1229d-377">使用*服务密钥*，允许与 Azure Application Insights 服务实例的通信。</span><span class="sxs-lookup"><span data-stu-id="1229d-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="1229d-378">排序的对象在场景中，根据其具有最高的事件计数。</span><span class="sxs-lookup"><span data-stu-id="1229d-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="1229d-379">为更改材料的颜色，最额对象的*绿色*。</span><span class="sxs-lookup"><span data-stu-id="1229d-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="1229d-380">若要创建脚本：</span><span class="sxs-lookup"><span data-stu-id="1229d-380">To create the script:</span></span>

1.  <span data-ttu-id="1229d-381">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="1229d-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="1229d-382">内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="1229d-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="1229d-383">脚本命名为**DataFromAnalytics**。</span><span class="sxs-lookup"><span data-stu-id="1229d-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="1229d-384">双击要使用 Visual Studio 中打开的脚本。</span><span class="sxs-lookup"><span data-stu-id="1229d-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="1229d-385">插入以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="1229d-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="1229d-386">在脚本内插入以下：</span><span class="sxs-lookup"><span data-stu-id="1229d-386">Inside the script, insert the following:</span></span>

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

6.  <span data-ttu-id="1229d-387">内**DataFromAnalytics**类中，右键后**start （)** 方法中，添加以下方法调用**FetchAnalytics()** 。</span><span class="sxs-lookup"><span data-stu-id="1229d-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="1229d-388">此方法负责使用填充的键/值对列表*GameObject*和占位符事件计数数量。</span><span class="sxs-lookup"><span data-stu-id="1229d-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="1229d-389">然后初始化**GetWebRequest()** 协同例程。</span><span class="sxs-lookup"><span data-stu-id="1229d-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="1229d-390">对调用的查询结构*Application Insights*可在此方法内找到此外，作为*查询 URL*终结点。</span><span class="sxs-lookup"><span data-stu-id="1229d-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

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

7.  <span data-ttu-id="1229d-391">下方**FetchAnalytics()** 方法中，添加一个名为方法**GetWebRequest()** ，它将返回*IEnumerator*。</span><span class="sxs-lookup"><span data-stu-id="1229d-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="1229d-392">此方法负责请求的一个事件，具有特定相对应的次数*GameObject*，已调用内*Application Insights*。</span><span class="sxs-lookup"><span data-stu-id="1229d-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="1229d-393">当发送的所有查询均都返回时， **DetermineWinner()** 调用方法。</span><span class="sxs-lookup"><span data-stu-id="1229d-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
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

8.  <span data-ttu-id="1229d-394">下一个方法是**DetermineWinner()** ，该对的列表进行排序*GameObject*并*Int*对，根据最高的事件计数。</span><span class="sxs-lookup"><span data-stu-id="1229d-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="1229d-395">然后，它更改材料的颜色*GameObject*到*绿色*（作为它是否具有最高的计数的反馈）。</span><span class="sxs-lookup"><span data-stu-id="1229d-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="1229d-396">这将显示包含分析结果的消息。</span><span class="sxs-lookup"><span data-stu-id="1229d-396">This displays a message with the analytics results.</span></span>

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

9.  <span data-ttu-id="1229d-397">添加类结构，用于反序列化 JSON 对象，从收到*Application Insights*。</span><span class="sxs-lookup"><span data-stu-id="1229d-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="1229d-398">在最底部的添加这些类您**DataFromAnalytics**类文件**外部**类定义。</span><span class="sxs-lookup"><span data-stu-id="1229d-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

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

10. <span data-ttu-id="1229d-399">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="1229d-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="1229d-400">章 10-创建移动类</span><span class="sxs-lookup"><span data-stu-id="1229d-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="1229d-401">**移动**脚本是下一步将需要创建的脚本。</span><span class="sxs-lookup"><span data-stu-id="1229d-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="1229d-402">它负责：</span><span class="sxs-lookup"><span data-stu-id="1229d-402">It is responsible for:</span></span>

- <span data-ttu-id="1229d-403">要移动根据方向照相机 Main Camera。</span><span class="sxs-lookup"><span data-stu-id="1229d-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="1229d-404">将所有其他脚本添加到场景对象。</span><span class="sxs-lookup"><span data-stu-id="1229d-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="1229d-405">若要创建脚本：</span><span class="sxs-lookup"><span data-stu-id="1229d-405">To create the script:</span></span>

1.  <span data-ttu-id="1229d-406">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="1229d-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="1229d-407">内右击**脚本**文件夹中，单击**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="1229d-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="1229d-408">脚本命名为**移动**。</span><span class="sxs-lookup"><span data-stu-id="1229d-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="1229d-409">要将其与打开的脚本上双击*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="1229d-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="1229d-410">现有代码替换为以下：</span><span class="sxs-lookup"><span data-stu-id="1229d-410">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="1229d-411">内**移动**类，*如下*空**update （)** 方法中，插入允许用户使用现有控制器移动虚拟空间中的以下方法：</span><span class="sxs-lookup"><span data-stu-id="1229d-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

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

6.  <span data-ttu-id="1229d-412">最后添加的方法调用中**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="1229d-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="1229d-413">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="1229d-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="1229d-414">第 11 章 — 设置脚本引用</span><span class="sxs-lookup"><span data-stu-id="1229d-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="1229d-415">您需要将放在本章**移动**拖到编写脚本**照相机父**，并设置其引用目标。</span><span class="sxs-lookup"><span data-stu-id="1229d-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="1229d-416">然后，该脚本将处理放置他们需要为其他脚本。</span><span class="sxs-lookup"><span data-stu-id="1229d-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="1229d-417">从**脚本**文件夹中的*项目面板*，将**移动**脚本到**照相机父**位于中的对象*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="1229d-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![设置在 Unity 场景中的脚本引用](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="1229d-419">单击**照相机父**。</span><span class="sxs-lookup"><span data-stu-id="1229d-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="1229d-420">中*层次结构面板*，拖动**右下**对象*层次结构面板*引用目标**控制器**中*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="1229d-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="1229d-421">设置**用户速度**到**5**，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="1229d-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![设置在 Unity 场景中的脚本引用](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="1229d-423">第 12 章 — 生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="1229d-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="1229d-424">此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。</span><span class="sxs-lookup"><span data-stu-id="1229d-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="1229d-425">导航到**生成设置**，(**文件** > **生成设置**)。</span><span class="sxs-lookup"><span data-stu-id="1229d-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="1229d-426">从**生成设置**窗口中，单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="1229d-426">From the **Build Settings** window, click **Build**.</span></span>

    ![生成 Unity 项目到 UWP 的解决方案](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="1229d-428">一个**文件资源管理器**窗口将弹出窗口，提示您指定用于生成的位置。</span><span class="sxs-lookup"><span data-stu-id="1229d-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="1229d-429">创建一个新文件夹 (通过单击**新文件夹**左上角)，并将其命名**生成**。</span><span class="sxs-lookup"><span data-stu-id="1229d-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![生成 Unity 项目到 UWP 的解决方案](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="1229d-431">打开新**生成**文件夹，并创建另一个文件夹 (使用**新的文件夹**一次)，并将其命名**MR\_Azure\_应用程序\_Insights**。</span><span class="sxs-lookup"><span data-stu-id="1229d-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![生成 Unity 项目到 UWP 的解决方案](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="1229d-433">与**MR\_Azure\_应用程序\_Insights**文件夹选择，单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="1229d-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="1229d-434">该项目将花大约一分钟生成。</span><span class="sxs-lookup"><span data-stu-id="1229d-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="1229d-435">遵循*构建*，**文件资源管理器**将显示新项目的位置。</span><span class="sxs-lookup"><span data-stu-id="1229d-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="1229d-436">第 13 章 — MR_Azure_Application_Insights 应用部署到你的计算机</span><span class="sxs-lookup"><span data-stu-id="1229d-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="1229d-437">若要部署**MR\_Azure\_应用程序\_Insights**在本地计算机上的应用：</span><span class="sxs-lookup"><span data-stu-id="1229d-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="1229d-438">打开解决方案文件的应用**MR\_Azure\_应用程序\_Insights**中的应用**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="1229d-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="1229d-439">在中**解决方案平台**，选择**x86，本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="1229d-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="1229d-440">在中**解决方案配置**选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="1229d-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![生成 Unity 项目到 UWP 的解决方案](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="1229d-442">转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。</span><span class="sxs-lookup"><span data-stu-id="1229d-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="1229d-443">你的应用现在应出现在已安装的应用，准备好启动列表中。</span><span class="sxs-lookup"><span data-stu-id="1229d-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="1229d-444">启动混合的现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="1229d-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="1229d-445">接近对象并查看它们，场景中移动时*Azure Insight 服务*已收集足够的事件数据，它将设置已接近最大到绿色的对象。</span><span class="sxs-lookup"><span data-stu-id="1229d-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="1229d-446">尽管的平均等待时间*事件和指标*要收集的服务需要大约 15 分钟，在某些场合下，这可能需要最多 1 小时。</span><span class="sxs-lookup"><span data-stu-id="1229d-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="1229d-447">第 14 章 — 在 Application Insights 服务门户</span><span class="sxs-lookup"><span data-stu-id="1229d-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="1229d-448">已在场景周围漫游并在多个对象 gazed 可以看到中收集的数据后*Application Insights 服务*门户。</span><span class="sxs-lookup"><span data-stu-id="1229d-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="1229d-449">请返回到 Application Insights 服务门户。</span><span class="sxs-lookup"><span data-stu-id="1229d-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="1229d-450">单击*指标资源管理器*。</span><span class="sxs-lookup"><span data-stu-id="1229d-450">Click on *Metrics Explorer*.</span></span>

    ![查看收集的数据](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="1229d-452">它将在包含图表示的选项卡中打开*事件和指标*与应用程序相关。</span><span class="sxs-lookup"><span data-stu-id="1229d-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="1229d-453">如上所述，则可能要在图表中显示的数据需要一些时间 （最多 1 小时）</span><span class="sxs-lookup"><span data-stu-id="1229d-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![查看收集的数据](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="1229d-455">单击*事件栏*中*的事件总数*由应用程序版本，若要查看其名称与事件的详细的明细。</span><span class="sxs-lookup"><span data-stu-id="1229d-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![查看收集的数据](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="1229d-457">在完成的 Application Insights 服务应用程序</span><span class="sxs-lookup"><span data-stu-id="1229d-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="1229d-458">祝贺你，构建利用 Application Insights 服务来监视您的应用程序中的用户的活动的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="1229d-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![课程结果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1229d-460">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="1229d-460">Bonus Exercises</span></span>

<span data-ttu-id="1229d-461">**练习 1**</span><span class="sxs-lookup"><span data-stu-id="1229d-461">**Exercise 1**</span></span>

<span data-ttu-id="1229d-462">请尝试生成，而不是手动创建 ObjectInScene 对象并设置其坐标在脚本中的平面。</span><span class="sxs-lookup"><span data-stu-id="1229d-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="1229d-463">这样一来，你也可以要求 Azure 最热门对象时 （不管是从结果中的视线移动或邻近性） 和 spawn*额外*这些对象之一。</span><span class="sxs-lookup"><span data-stu-id="1229d-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="1229d-464">**练习 2**</span><span class="sxs-lookup"><span data-stu-id="1229d-464">**Exercise 2**</span></span>

<span data-ttu-id="1229d-465">在 Application Insights 对结果进行排序的时间，以便获取最相关的数据，并在应用程序中实现该时间敏感数据。</span><span class="sxs-lookup"><span data-stu-id="1229d-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

