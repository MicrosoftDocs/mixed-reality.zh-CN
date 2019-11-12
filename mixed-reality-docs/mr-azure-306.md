---
title: MR 和 Azure 306-流式处理视频
description: 完成本课程，了解如何在混合现实应用程序中实现 Azure 媒体服务。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，媒体服务，流视频，360，沉浸，vr
ms.openlocfilehash: e0350d69eed9b922e174bc521107beac7d11b1bc
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926831"
---
>[!NOTE]
><span data-ttu-id="65387-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="65387-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="65387-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="65387-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="65387-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="65387-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="65387-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="65387-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="65387-108">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="65387-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="65387-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="65387-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="65387-110">MR 和 Azure 306：流式处理视频</span><span class="sxs-lookup"><span data-stu-id="65387-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="65387-111">![最终产品-启动](images/AzureLabs-Lab6-00.png)
![最终产品-启动](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="65387-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="65387-112">在本课程中，你将了解如何将 Azure 媒体服务连接到 Windows Mixed Reality VR 体验，以允许在沉浸式耳机上播放流式传输360学位视频。</span><span class="sxs-lookup"><span data-stu-id="65387-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="65387-113">**Azure 媒体服务**是一系列服务，为你提供了广播质量的视频流式处理服务，以便在当前最常见的移动设备上达到更大的受众。</span><span class="sxs-lookup"><span data-stu-id="65387-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="65387-114">有关详细信息，请访问[Azure 媒体服务页](https://azure.microsoft.com/services/media-services)。</span><span class="sxs-lookup"><span data-stu-id="65387-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="65387-115">完成本课程后，你将拥有一个混合现实沉浸式耳机应用程序，该应用程序将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="65387-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="65387-116">通过**Azure 媒体服务**从**azure 存储**检索360度视频。</span><span class="sxs-lookup"><span data-stu-id="65387-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="65387-117">在 Unity 场景中显示检索到的360度视频。</span><span class="sxs-lookup"><span data-stu-id="65387-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="65387-118">在两个场景之间导航，具有两个不同的视频。</span><span class="sxs-lookup"><span data-stu-id="65387-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="65387-119">在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。</span><span class="sxs-lookup"><span data-stu-id="65387-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="65387-120">本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="65387-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="65387-121">您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。</span><span class="sxs-lookup"><span data-stu-id="65387-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="65387-122">设备支持</span><span class="sxs-lookup"><span data-stu-id="65387-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="65387-123">摘要</span><span class="sxs-lookup"><span data-stu-id="65387-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="65387-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="65387-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="65387-125"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="65387-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="65387-126">MR 和 Azure 306：流式处理视频</span><span class="sxs-lookup"><span data-stu-id="65387-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="65387-127">✔️</span><span class="sxs-lookup"><span data-stu-id="65387-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="65387-128">必备条件</span><span class="sxs-lookup"><span data-stu-id="65387-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="65387-129">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="65387-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="65387-130">另外请注意，本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容（5月2018）。</span><span class="sxs-lookup"><span data-stu-id="65387-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="65387-131">您可以随意使用最新的软件（如[安装工具一文](install-the-tools.md)中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="65387-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="65387-132">本课程建议采用以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="65387-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="65387-133">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发</span><span class="sxs-lookup"><span data-stu-id="65387-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="65387-134">Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="65387-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="65387-135">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="65387-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="65387-136">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="65387-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="65387-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="65387-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="65387-138">[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="65387-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="65387-139">Azure 安装和数据检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="65387-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="65387-140">2 360 的视频学位格式（可[在此下载页面](https://www.mettle.com/360vr-master-series-free-360-downloads-page)找到一些免费版税的视频）</span><span class="sxs-lookup"><span data-stu-id="65387-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="65387-141">开始之前</span><span class="sxs-lookup"><span data-stu-id="65387-141">Before you start</span></span>

1.  <span data-ttu-id="65387-142">为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。</span><span class="sxs-lookup"><span data-stu-id="65387-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="65387-143">设置并测试混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="65387-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="65387-144">本课程**不**需要移动控制器。</span><span class="sxs-lookup"><span data-stu-id="65387-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="65387-145">如果需要支持设置沉浸式耳机，请单击["有关如何设置 Windows Mixed Reality" 的链接](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="65387-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="65387-146">第1章-Azure 门户：创建 Azure 存储帐户</span><span class="sxs-lookup"><span data-stu-id="65387-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="65387-147">若要使用**Azure 存储服务**，你将需要在 Azure 门户中创建并配置一个**存储帐户**。</span><span class="sxs-lookup"><span data-stu-id="65387-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="65387-148">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="65387-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="65387-149">如果还没有 Azure 帐户，则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="65387-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="65387-150">如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="65387-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="65387-151">登录后，单击左侧菜单中的 "**存储帐户**"。</span><span class="sxs-lookup"><span data-stu-id="65387-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="65387-153">在 "**存储帐户**" 选项卡上，单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="65387-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="65387-155">在 "**创建存储帐户**" 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="65387-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="65387-156">插入帐户的**名称**，请注意，此字段仅接受数字和小写字母。</span><span class="sxs-lookup"><span data-stu-id="65387-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="65387-157">对于**部署模型，选择 "** **资源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="65387-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="65387-158">对于 "**帐户类型**"，请选择 "**存储（常规用途 v1）** "。</span><span class="sxs-lookup"><span data-stu-id="65387-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="65387-159">对于 "**性能**"，请选择 "**标准"。**</span><span class="sxs-lookup"><span data-stu-id="65387-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="65387-160">对于**复制**，请选择 "**本地冗余存储（LRS）** "。</span><span class="sxs-lookup"><span data-stu-id="65387-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="65387-161">使**安全传输**保持**禁用状态**。</span><span class="sxs-lookup"><span data-stu-id="65387-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="65387-162">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="65387-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="65387-163">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="65387-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="65387-164">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="65387-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="65387-165">确定资源组的**位置**（如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="65387-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="65387-166">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="65387-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="65387-167">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="65387-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="65387-168">你将需要确认你已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="65387-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="65387-170">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="65387-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="65387-171">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="65387-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="65387-173">此时，无需访问资源，只需转到下一章即可。</span><span class="sxs-lookup"><span data-stu-id="65387-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="65387-174">第2章-Azure 门户：创建媒体服务</span><span class="sxs-lookup"><span data-stu-id="65387-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="65387-175">若要使用 Azure 媒体服务，你将需要配置服务的实例，使其可用于你的应用程序（帐户持有者必须是管理员）。</span><span class="sxs-lookup"><span data-stu-id="65387-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="65387-176">在 Azure 门户中，单击左上角的 "**创建资源**"，然后搜索**Media Service，** 按**enter**。</span><span class="sxs-lookup"><span data-stu-id="65387-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="65387-177">当前所需资源的图标为粉红色;单击此，显示新页。</span><span class="sxs-lookup"><span data-stu-id="65387-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="65387-179">新页将提供**媒体服务**的说明。</span><span class="sxs-lookup"><span data-stu-id="65387-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="65387-180">在此提示符的左下方，单击 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="65387-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="65387-182">单击 "**创建**" 后，将显示一个面板，需要在其中提供有关新媒体服务的一些详细信息：</span><span class="sxs-lookup"><span data-stu-id="65387-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="65387-183">为此服务实例插入所需的**帐户名称**。</span><span class="sxs-lookup"><span data-stu-id="65387-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="65387-184">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="65387-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="65387-185">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="65387-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="65387-186">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="65387-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="65387-187">建议将所有与单个项目关联的 Azure 服务（例如这些实验室）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="65387-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="65387-188">若要了解有关 Azure 资源组的详细信息，请参阅此[链接，了解如何管理 Azure 资源组](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="65387-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="65387-189">确定资源组的**位置**（如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="65387-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="65387-190">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="65387-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="65387-191">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="65387-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="65387-192">对于 "**存储帐户**" 部分，单击 "**请选择 ...** " 部分，然后单击在上一章中创建的**存储帐户**。</span><span class="sxs-lookup"><span data-stu-id="65387-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="65387-193">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="65387-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="65387-194">单击**创建**。</span><span class="sxs-lookup"><span data-stu-id="65387-194">Click **Create**.</span></span>

        ![Azure 门户](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="65387-196">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="65387-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="65387-197">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="65387-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="65387-199">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="65387-199">Click on the notification to explore your new Service instance.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="65387-201">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="65387-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="65387-202">在 "新建媒体服务" 页的左侧面板中，单击 "**资产**" 链接，这是大约的一半。</span><span class="sxs-lookup"><span data-stu-id="65387-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="65387-203">在下一页上，在页面的左上角，单击 "**上载**"。</span><span class="sxs-lookup"><span data-stu-id="65387-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="65387-205">单击**文件夹**图标浏览文件，并选择要流式传输的第一个360视频。</span><span class="sxs-lookup"><span data-stu-id="65387-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="65387-206">可以通过以下[链接下载示例视频](https://vimeo.com/214401712)。</span><span class="sxs-lookup"><span data-stu-id="65387-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="65387-208">长文件名可能会导致编码器出现问题：为了确保视频不会出现问题，请考虑缩短视频文件名的长度。</span><span class="sxs-lookup"><span data-stu-id="65387-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="65387-209">视频上传完成后，进度栏将变为绿色。</span><span class="sxs-lookup"><span data-stu-id="65387-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="65387-211">单击上面的文本（**yourservicename**）以返回到 "**资产**" 页。</span><span class="sxs-lookup"><span data-stu-id="65387-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="65387-212">你会注意到你的视频已成功上传。</span><span class="sxs-lookup"><span data-stu-id="65387-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="65387-213">单击它。</span><span class="sxs-lookup"><span data-stu-id="65387-213">Click on it.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="65387-215">要重定向到的页面将显示有关视频的详细信息。</span><span class="sxs-lookup"><span data-stu-id="65387-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="65387-216">若要使用视频，需要对其进行编码，方法是单击页面左上角的 "**编码**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="65387-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="65387-218">此时将在右侧显示一个新面板，您可以在其中设置文件的编码选项。</span><span class="sxs-lookup"><span data-stu-id="65387-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="65387-219">设置以下属性（默认情况下已设置某些属性）：</span><span class="sxs-lookup"><span data-stu-id="65387-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="65387-220">**媒体编码器名称\*Media Encoder Standard**\*</span><span class="sxs-lookup"><span data-stu-id="65387-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="65387-221">**编码预设的\*内容自适应多比特率**\*</span><span class="sxs-lookup"><span data-stu-id="65387-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="65387-222">***Video1 的作业名称 Media Encoder Standard 处理***</span><span class="sxs-lookup"><span data-stu-id="65387-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="65387-223">**输出媒体资产名称\*Video1--Media Encoder Standard 编码**\*</span><span class="sxs-lookup"><span data-stu-id="65387-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Azure 门户](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="65387-225">单击“创建”按钮。</span><span class="sxs-lookup"><span data-stu-id="65387-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="65387-226">你将注意到添加了**编码作业**的栏，单击该栏，此时将显示一个面板，其中显示了编码进度。</span><span class="sxs-lookup"><span data-stu-id="65387-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-17.png)

    ![Azure 门户](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="65387-229">等待作业完成。</span><span class="sxs-lookup"><span data-stu-id="65387-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="65387-230">完成后，可以随意关闭面板右上角的 "X" 面板。</span><span class="sxs-lookup"><span data-stu-id="65387-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-19.png)

    ![Azure 门户](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="65387-233">此操作所花的时间取决于视频文件的大小。</span><span class="sxs-lookup"><span data-stu-id="65387-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="65387-234">此过程可能需要一段时间。</span><span class="sxs-lookup"><span data-stu-id="65387-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="65387-235">现在，已创建视频的编码版本，你可以将其发布以使其可供访问。</span><span class="sxs-lookup"><span data-stu-id="65387-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="65387-236">为此，请单击蓝色链接**资产**，返回到 "资产" 页。</span><span class="sxs-lookup"><span data-stu-id="65387-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="65387-238">你将看到视频以及另一个，它属于**资产类型 "_多比特率_** "。</span><span class="sxs-lookup"><span data-stu-id="65387-238">You will see your video along with another, which is of **Asset Type _Multi-Bitrate MP4_**.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="65387-240">你可能会注意到，新资产与初始视频的结合*未知*，并且其**大小**为 "0" 字节，只需刷新窗口以更新。</span><span class="sxs-lookup"><span data-stu-id="65387-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="65387-241">单击此新资产。</span><span class="sxs-lookup"><span data-stu-id="65387-241">Click this new asset.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="65387-243">你将看到一个类似于你以前使用过的面板，这只是一个不同的资产。</span><span class="sxs-lookup"><span data-stu-id="65387-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="65387-244">单击页面顶部的 "**发布**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="65387-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="65387-246">系统将提示你将**定位符**（即入口点）设置为资产中的文件。</span><span class="sxs-lookup"><span data-stu-id="65387-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="65387-247">对于你的方案，请设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="65387-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="65387-248">**定位符类型** > **渐进式**。</span><span class="sxs-lookup"><span data-stu-id="65387-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="65387-249">**日期**和**时间**将设置为你，从当前日期到将来的某个时间（本例中为100年）。</span><span class="sxs-lookup"><span data-stu-id="65387-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="65387-250">保持原样，或将其更改为 "符合"。</span><span class="sxs-lookup"><span data-stu-id="65387-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="65387-251">有关定位符的详细信息以及可以选择的信息，请访问[Azure 媒体服务文档](https://docs.microsoft.com/azure/media-services/media-services-concepts)。</span><span class="sxs-lookup"><span data-stu-id="65387-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="65387-252">在该面板的底部，单击 "**添加**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="65387-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="65387-254">你的视频现在已发布，可以使用其终结点进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="65387-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="65387-255">页面的后面是**文件**部分。</span><span class="sxs-lookup"><span data-stu-id="65387-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="65387-256">这是视频的不同编码版本的位置。</span><span class="sxs-lookup"><span data-stu-id="65387-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="65387-257">选择可能的最高解决方法（在下面的图像中为1920x960 文件），然后将显示右侧的一个面板。</span><span class="sxs-lookup"><span data-stu-id="65387-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="65387-258">可在此处找到**下载 URL**。</span><span class="sxs-lookup"><span data-stu-id="65387-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="65387-259">复制此**终结点**，因为你将在稍后的代码中使用它。</span><span class="sxs-lookup"><span data-stu-id="65387-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-26.png)    

    ![Azure 门户](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="65387-262">还可以按 "**播放**" 按钮播放视频并对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="65387-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="65387-263">你现在需要上传将在此实验室中使用的第二个视频。</span><span class="sxs-lookup"><span data-stu-id="65387-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="65387-264">按照上述步骤操作，为第二个视频重复相同的过程。</span><span class="sxs-lookup"><span data-stu-id="65387-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="65387-265">请确保同时复制第二个**终结点**。</span><span class="sxs-lookup"><span data-stu-id="65387-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="65387-266">使用以下[链接下载第二个视频](https://vimeo.com/214402865)。</span><span class="sxs-lookup"><span data-stu-id="65387-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="65387-267">一旦发布了这两个视频，就可以转到下一章。</span><span class="sxs-lookup"><span data-stu-id="65387-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="65387-268">第3章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="65387-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="65387-269">下面是使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="65387-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="65387-270">打开**Unity** ，并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="65387-270">Open **Unity** and click **New**.</span></span> 

    ![Azure 门户](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="65387-272">你现在需要提供 Unity 项目名称，插入**MR\_360VideoStreaming**）。</span><span class="sxs-lookup"><span data-stu-id="65387-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="65387-273">请确保 "项目类型" 设置为 " **3d**"。</span><span class="sxs-lookup"><span data-stu-id="65387-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="65387-274">将位置设置为合适的位置（请记住，更接近根目录更好）。</span><span class="sxs-lookup"><span data-stu-id="65387-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="65387-275">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="65387-275">Then, click **Create project**.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="65387-277">当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio"。**</span><span class="sxs-lookup"><span data-stu-id="65387-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="65387-278">转到 " ***编辑* *首选项*** "，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="65387-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="65387-279">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="65387-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="65387-280">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="65387-280">Close the **Preferences** window.</span></span>

    ![Azure 门户](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="65387-282">接下来，转到 " ***文件* *生成设置*** "，并通过单击 "**切换平台**" 按钮将平台切换到**通用 Windows 平台**。</span><span class="sxs-lookup"><span data-stu-id="65387-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="65387-283">另外，请确保：</span><span class="sxs-lookup"><span data-stu-id="65387-283">Also make sure that:</span></span>

    1. <span data-ttu-id="65387-284">"**目标设备**" 设置为 "**任何设备"。**</span><span class="sxs-lookup"><span data-stu-id="65387-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="65387-285">**生成类型**设置为**D3D。**</span><span class="sxs-lookup"><span data-stu-id="65387-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="65387-286">**SDK**设置为 "**最新安装"。**</span><span class="sxs-lookup"><span data-stu-id="65387-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="65387-287">**Visual Studio 版本**设置为 "**最新安装"。**</span><span class="sxs-lookup"><span data-stu-id="65387-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="65387-288">"**生成并运行**" 设置为 "**本地计算机"。**</span><span class="sxs-lookup"><span data-stu-id="65387-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="65387-289">请不要担心现在设置**场景**，因为稍后会设置它们。</span><span class="sxs-lookup"><span data-stu-id="65387-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="65387-290">其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="65387-290">The remaining settings should be left as default for now.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="65387-292">在 "**生成设置**" 窗口中，单击 "**播放机设置**" 按钮，这会在**检查器**所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="65387-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="65387-293">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="65387-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="65387-294">在 "**其他设置**" 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="65387-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="65387-295">**脚本** **运行时版本**应**稳定**（与 .net 3.5 等效）。</span><span class="sxs-lookup"><span data-stu-id="65387-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="65387-296">**脚本编写后端**应为 **.net。**</span><span class="sxs-lookup"><span data-stu-id="65387-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="65387-297">**API 兼容级别**应为 **.net 4.6。**</span><span class="sxs-lookup"><span data-stu-id="65387-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="65387-299">在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="65387-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="65387-301">在 "**发布设置**" 选项卡的 "**功能**" 下，检查：</span><span class="sxs-lookup"><span data-stu-id="65387-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="65387-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="65387-302">**InternetClient**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="65387-304">进行这些更改后，请关闭 "**生成设置**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="65387-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="65387-305">保存项目 **文件** 保存项目 \* \*。</span><span class="sxs-lookup"><span data-stu-id="65387-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="65387-306">第4章-导入 InsideOutSphere Unity 包</span><span class="sxs-lookup"><span data-stu-id="65387-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65387-307">如果希望跳过本课程的*Unity 设置*组件，并继续直接进入代码，可以下载[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)，将其作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后从**第5章**继续。</span><span class="sxs-lookup"><span data-stu-id="65387-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="65387-308">你仍需要创建一个 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="65387-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="65387-309">在本课程中，你将需要下载名为[**InsideOutSphere. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)的 Unity 资产包。</span><span class="sxs-lookup"><span data-stu-id="65387-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="65387-310">如何导入**unitypackage**：</span><span class="sxs-lookup"><span data-stu-id="65387-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="65387-311">在您前面的 "Unity" 面板中，单击屏幕顶部菜单中的 "**资产**"，然后单击 "**导入包 > 自定义包**"。</span><span class="sxs-lookup"><span data-stu-id="65387-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="65387-313">使用文件选取器选择**InsideOutSphere unitypackage**包，并单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="65387-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="65387-314">此时将显示此资产的组件列表。</span><span class="sxs-lookup"><span data-stu-id="65387-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="65387-315">单击 "**导入**" 确认导入。</span><span class="sxs-lookup"><span data-stu-id="65387-315">Confirm the import by clicking **Import**.</span></span>

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="65387-317">导入完成后，你会发现三个新的文件夹、**材料**、**型号**和**Prototyping**已添加到 "**资产**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="65387-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="65387-318">这种文件夹结构是 Unity 项目的典型类型。</span><span class="sxs-lookup"><span data-stu-id="65387-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="65387-320">打开 "**模型**" 文件夹，你将看到已导入**InsideOutSphere**模型。</span><span class="sxs-lookup"><span data-stu-id="65387-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="65387-321">在 "**材料**" 文件夹中，你将找到**InsideOutSpheres**材料*lambert1*，以及一个名为*ButtonMaterial*的材料，你将很快就会看到它。</span><span class="sxs-lookup"><span data-stu-id="65387-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="65387-322">**Prototyping**文件夹包含**InsideOutSphere** Prefab，其中包含**InsideOutSphere** *模型*和*GazeButton*。</span><span class="sxs-lookup"><span data-stu-id="65387-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="65387-323">**不包含任何代码**，你将按照此课程编写代码。</span><span class="sxs-lookup"><span data-stu-id="65387-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="65387-324">在**层次结构**中，选择 "**照相机**" 对象并更新以下组件：</span><span class="sxs-lookup"><span data-stu-id="65387-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="65387-325">**转换**</span><span class="sxs-lookup"><span data-stu-id="65387-325">**Transform**</span></span>

        1.  <span data-ttu-id="65387-326">Position = **X**：0， **Y**：0， **Z**：0。</span><span class="sxs-lookup"><span data-stu-id="65387-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="65387-327">旋转 = **X**：0， **Y**：0， **Z**：0。</span><span class="sxs-lookup"><span data-stu-id="65387-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="65387-328">Scale **X**：1， **Y**：1， **Z**：1。</span><span class="sxs-lookup"><span data-stu-id="65387-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="65387-329">**摄像头**</span><span class="sxs-lookup"><span data-stu-id="65387-329">**Camera**</span></span>

        1. <span data-ttu-id="65387-330">**清除标志**：纯色。</span><span class="sxs-lookup"><span data-stu-id="65387-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="65387-331">**剪辑平面**：接近：0.1，到目前为止：6。</span><span class="sxs-lookup"><span data-stu-id="65387-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="65387-333">导航到 " **Prefab** " 文件夹，然后将 " **InsideOutSphere** " Prefab 拖到 "**层次结构**" 面板中。</span><span class="sxs-lookup"><span data-stu-id="65387-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="65387-335">通过单击其旁边的小箭头，展开**层次结构**中的**InsideOutSphere**对象。</span><span class="sxs-lookup"><span data-stu-id="65387-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="65387-336">你将在其下看到一个名为**GazeButton**的**子**对象。</span><span class="sxs-lookup"><span data-stu-id="65387-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="65387-337">这将用于更改场景和视频。</span><span class="sxs-lookup"><span data-stu-id="65387-337">This will be used to change scenes and thus videos.</span></span>

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="65387-339">在检查器窗口中，单击**InsideOutSphere**的转换组件，确保设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="65387-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="65387-340">转换位置</span><span class="sxs-lookup"><span data-stu-id="65387-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="65387-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="65387-341">**X** 0</span></span>  |          <span data-ttu-id="65387-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="65387-342">**Y** 0</span></span>          |  <span data-ttu-id="65387-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="65387-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="65387-344">转换-旋转</span><span class="sxs-lookup"><span data-stu-id="65387-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="65387-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="65387-345">**X** 0</span></span>  |          <span data-ttu-id="65387-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="65387-346">**Y** -50</span></span>        |  <span data-ttu-id="65387-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="65387-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="65387-348">转换-缩放</span><span class="sxs-lookup"><span data-stu-id="65387-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="65387-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="65387-349">**X** 1</span></span>   |          <span data-ttu-id="65387-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="65387-350">**Y** 1</span></span>          |  <span data-ttu-id="65387-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="65387-351">**Z** 1</span></span>  |

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="65387-353">单击**GazeButton**子对象，并按如下所示设置其**转换**：</span><span class="sxs-lookup"><span data-stu-id="65387-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="65387-354">转换位置</span><span class="sxs-lookup"><span data-stu-id="65387-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="65387-355">**X** 3。6</span><span class="sxs-lookup"><span data-stu-id="65387-355">**X** 3.6</span></span>|          <span data-ttu-id="65387-356">**Y** 1。3</span><span class="sxs-lookup"><span data-stu-id="65387-356">**Y** 1.3</span></span>        |  <span data-ttu-id="65387-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="65387-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="65387-358">转换-旋转</span><span class="sxs-lookup"><span data-stu-id="65387-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="65387-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="65387-359">**X** 0</span></span>  |          <span data-ttu-id="65387-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="65387-360">**Y** 0</span></span>          |  <span data-ttu-id="65387-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="65387-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="65387-362">转换-缩放</span><span class="sxs-lookup"><span data-stu-id="65387-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="65387-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="65387-363">**X** 1</span></span>   |          <span data-ttu-id="65387-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="65387-364">**Y** 1</span></span>          |  <span data-ttu-id="65387-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="65387-365">**Z** 1</span></span>  |

    ![导入 InsideOutSphere Unity 包](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="65387-367">第5章-创建 VideoController 类</span><span class="sxs-lookup"><span data-stu-id="65387-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="65387-368">**VideoController**类托管两个视频终结点，这些终结点将用于从 Azure 媒体服务流式传输内容。</span><span class="sxs-lookup"><span data-stu-id="65387-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="65387-369">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="65387-369">To create this class:</span></span>

1.  <span data-ttu-id="65387-370">右键单击位于 "**项目**" 面板中的 "**资产" 文件夹**，然后单击 "**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="65387-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="65387-371">命名文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="65387-371">Name the folder **Scripts**.</span></span>

    ![创建 VideoController 类](images/AzureLabs-Lab6-43.png)

    ![创建 VideoController 类](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="65387-374">双击 "**脚本**" 文件夹将其打开。</span><span class="sxs-lookup"><span data-stu-id="65387-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="65387-375">右键单击文件夹内，然后单击 "**创建 > C\# 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="65387-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="65387-376">将脚本命名为**VideoController**。</span><span class="sxs-lookup"><span data-stu-id="65387-376">Name the script **VideoController**.</span></span>

    ![创建 VideoController 类](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="65387-378">双击新的**VideoController**脚本以通过**Visual Studio 2017**将其打开。</span><span class="sxs-lookup"><span data-stu-id="65387-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![创建 VideoController 类](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="65387-380">在代码文件的顶部更新命名空间，如下所示：</span><span class="sxs-lookup"><span data-stu-id="65387-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="65387-381">在**VideoController**类中输入以下变量，同时输入**唤醒（）** 方法：</span><span class="sxs-lookup"><span data-stu-id="65387-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="65387-382">现在，可以从 Azure 媒体服务视频输入终结点：</span><span class="sxs-lookup"><span data-stu-id="65387-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="65387-383">*Video1endpoint*变量中的第一个。</span><span class="sxs-lookup"><span data-stu-id="65387-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="65387-384">*Video2endpoint*变量的第二个。</span><span class="sxs-lookup"><span data-stu-id="65387-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="65387-385">在 Unity 内使用*https*时存在一个已知问题，版本2017.4.1 为 f1。</span><span class="sxs-lookup"><span data-stu-id="65387-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="65387-386">如果视频在播放时出现错误，请尝试改用 "http"。</span><span class="sxs-lookup"><span data-stu-id="65387-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="65387-387">接下来，需要编辑**Start （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="65387-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="65387-388">此方法将在用户每次切换场景时（通过查看 "注视" 按钮切换视频）触发。</span><span class="sxs-lookup"><span data-stu-id="65387-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="65387-389">在**start （）** 方法之后，插入**PlayVideo （）** *IEnumerator*方法，该方法将用于无缝启动视频（因此不会出现断断续续）。</span><span class="sxs-lookup"><span data-stu-id="65387-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="65387-390">此类需要的最后一种方法是**ChangeScene （）** 方法，该方法将用于在场景间进行交换。</span><span class="sxs-lookup"><span data-stu-id="65387-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="65387-391">**ChangeScene （）** 方法使用一种简单的 C\# 功能，称为*条件运算符*。</span><span class="sxs-lookup"><span data-stu-id="65387-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="65387-392">这允许检查条件，然后在单个语句中检查基于检查结果返回的值。</span><span class="sxs-lookup"><span data-stu-id="65387-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="65387-393">请单击以下[链接了解有关条件运算符的详细信息](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)。</span><span class="sxs-lookup"><span data-stu-id="65387-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="65387-394">在返回到 Unity 之前，在 Visual Studio 中保存更改。</span><span class="sxs-lookup"><span data-stu-id="65387-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="65387-395">返回 Unity 编辑器，在 "**层次结构**" 面板中单击 " **VideoController** " 类，并将其拖到 "**脚本**" 文件夹中的**主相机**对象。</span><span class="sxs-lookup"><span data-stu-id="65387-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="65387-396">单击**主摄像机**，查看**检查器面板**。</span><span class="sxs-lookup"><span data-stu-id="65387-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="65387-397">你会注意到，在新添加的脚本组件中，有一个值为空的字段。</span><span class="sxs-lookup"><span data-stu-id="65387-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="65387-398">这是一个引用字段，它以代码中的公共变量为目标。</span><span class="sxs-lookup"><span data-stu-id="65387-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="65387-399">将**InsideOutSphere**对象从 "**层次结构" 面板**拖动到**球体**槽，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="65387-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="65387-400">![创建 VideoController 类 ![](images/AzureLabs-Lab6-47.png)
    创建 VideoController 类](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="65387-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="65387-401">第6章-创建注视类</span><span class="sxs-lookup"><span data-stu-id="65387-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="65387-402">此类负责创建将从**主相机**向前投影的**Raycast** ，以检测用户正在查看的对象。</span><span class="sxs-lookup"><span data-stu-id="65387-402">This class is responsible for creating a **Raycast** that will be projected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="65387-403">在这种情况下， **Raycast**需要确定用户是否正在查看场景中的**GazeButton**对象并触发行为。</span><span class="sxs-lookup"><span data-stu-id="65387-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="65387-404">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="65387-404">To create this Class:</span></span>

1.  <span data-ttu-id="65387-405">中转到前面创建的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="65387-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="65387-406">右键单击 "**项目**" 面板，然后选择 "*创建*\* C\# 脚本"。</span><span class="sxs-lookup"><span data-stu-id="65387-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="65387-407">将脚本命名为 "**注视**"。</span><span class="sxs-lookup"><span data-stu-id="65387-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="65387-408">双击新的***注视***脚本以通过**Visual Studio 2017**将其打开。</span><span class="sxs-lookup"><span data-stu-id="65387-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="65387-409">确保以下命名空间位于该脚本的顶部，并删除所有其他命名空间：</span><span class="sxs-lookup"><span data-stu-id="65387-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="65387-410">然后在**注视**类中添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="65387-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="65387-411">现在需要添加**唤醒（）** 和**Start （）** 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="65387-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="65387-412">在**Update （）** 方法中添加以下代码，以投影 Raycast 并检测目标命中：</span><span class="sxs-lookup"><span data-stu-id="65387-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="65387-413">在返回到 Unity 之前，在 Visual Studio 中保存更改。</span><span class="sxs-lookup"><span data-stu-id="65387-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="65387-414">单击 "脚本" 文件夹中的 "**注视**" 类并将其拖到 "**层次结构**" 面板中的主相机对象。</span><span class="sxs-lookup"><span data-stu-id="65387-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="65387-415">第7章-设置两个 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="65387-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="65387-416">本章的目的是设置两个场景，其中每个都托管要流式传输的视频。</span><span class="sxs-lookup"><span data-stu-id="65387-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="65387-417">您将复制您已创建的场景，这样您就不需要再次设置它，不过您将编辑新场景，使*GazeButton*对象位于不同的位置，并且具有不同的外观。</span><span class="sxs-lookup"><span data-stu-id="65387-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="65387-418">这是为了说明如何在场景之间进行更改。</span><span class="sxs-lookup"><span data-stu-id="65387-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="65387-419">为此，请转到 "**文件" > 将场景另存为 ...** "。将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="65387-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="65387-420">单击 "**新建文件夹**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="65387-420">Click the **New folder** button.</span></span>

    ![第7章-设置两个 Unity 场景](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="65387-422">将文件夹命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="65387-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="65387-423">"**保存场景**" 窗口将仍处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="65387-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="65387-424">打开新创建的**场景**文件夹。</span><span class="sxs-lookup"><span data-stu-id="65387-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="65387-425">在 "文件名 **：** 文本" 字段中，键入**VideoScene1**，然后按 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="65387-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="65387-426">返回 Unity，打开**场景**文件夹，然后单击**VideoScene1**文件。</span><span class="sxs-lookup"><span data-stu-id="65387-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="65387-427">使用键盘，并按**Ctrl + D**将复制该场景</span><span class="sxs-lookup"><span data-stu-id="65387-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="65387-428">还可以通过导航到**编辑 > 重复**来执行**重复**的命令。</span><span class="sxs-lookup"><span data-stu-id="65387-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="65387-429">Unity 将自动递增场景名称编号，但仍要检查它，以确保它与以前插入的代码匹配。</span><span class="sxs-lookup"><span data-stu-id="65387-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="65387-430">应该有**VideoScene1**和**VideoScene2**。</span><span class="sxs-lookup"><span data-stu-id="65387-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="65387-431">对于这两个场景，请参阅**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="65387-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="65387-432">在 "**生成设置**" 窗口打开的情况下，将场景拖动到 "生成" 部分中的 "**场景**"。</span><span class="sxs-lookup"><span data-stu-id="65387-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="65387-434">您可以通过按住**Ctrl**按钮并单击每个场景，最后拖动两者，从**场景**文件夹中选择两个场景。</span><span class="sxs-lookup"><span data-stu-id="65387-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="65387-435">关闭 "**生成设置**" 窗口，然后双击 " **VideoScene2**"。</span><span class="sxs-lookup"><span data-stu-id="65387-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="65387-436">在第二个场景打开的情况下，单击**InsideOutSphere**的**GazeButton**子对象，并按如下所示设置其变换：</span><span class="sxs-lookup"><span data-stu-id="65387-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="65387-437">转换位置</span><span class="sxs-lookup"><span data-stu-id="65387-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="65387-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="65387-438">**X** 0</span></span>  |         <span data-ttu-id="65387-439">**Y** 1。3</span><span class="sxs-lookup"><span data-stu-id="65387-439">**Y** 1.3</span></span>         | <span data-ttu-id="65387-440">**Z** 3。6</span><span class="sxs-lookup"><span data-stu-id="65387-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="65387-441">转换-旋转</span><span class="sxs-lookup"><span data-stu-id="65387-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="65387-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="65387-442">**X** 0</span></span>  |          <span data-ttu-id="65387-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="65387-443">**Y** 0</span></span>          |  <span data-ttu-id="65387-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="65387-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="65387-445">转换-缩放</span><span class="sxs-lookup"><span data-stu-id="65387-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="65387-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="65387-446">**X** 1</span></span>   |          <span data-ttu-id="65387-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="65387-447">**Y** 1</span></span>          |  <span data-ttu-id="65387-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="65387-448">**Z** 1</span></span>  |

10. <span data-ttu-id="65387-449">选择**GazeButton**子级后，查看**检查**器和**网格筛选器**。</span><span class="sxs-lookup"><span data-stu-id="65387-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="65387-450">单击 "**网格**引用" 字段旁边的小目标：</span><span class="sxs-lookup"><span data-stu-id="65387-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="65387-452">将显示 "**选择网格**" 弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="65387-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="65387-453">双击**资产**列表中的**多维数据集**网格。</span><span class="sxs-lookup"><span data-stu-id="65387-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="65387-455">**网格筛选器**将更新，现在为**多维数据集**。</span><span class="sxs-lookup"><span data-stu-id="65387-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="65387-456">现在，单击 "**球碰撞**器" 旁边的**齿轮**图标，然后单击 "**删除组件**"，从此对象中删除碰撞器。</span><span class="sxs-lookup"><span data-stu-id="65387-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="65387-458">在**GazeButton**仍处于选中状态的情况下，单击**检查器**底部的 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="65387-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="65387-459">在 "搜索" 字段中，键入**框**和**框碰撞**器将是一个选项，单击此选项可将**框碰撞**器添加到**GazeButton**对象。</span><span class="sxs-lookup"><span data-stu-id="65387-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="65387-461">现在， **GazeButton**已部分更新，但要看起来不同，但现在你将创建新的**材料**，使其看起来完全不同，并且更容易识别为不同于第一个场景中的对象的对象。</span><span class="sxs-lookup"><span data-stu-id="65387-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="65387-462">导航到 "**项目" 面板**中的 "**材料**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="65387-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="65387-463">复制**ButtonMaterial**材料（按下键盘上的**Ctrl** + **D** ，或左键单击**材料**，然后从 "**编辑**文件" 菜单选项中选择 "**复制**"）。</span><span class="sxs-lookup"><span data-stu-id="65387-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="65387-464">![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-55.png)
    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="65387-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="65387-465">选择新的**ButtonMaterial**材料（此处名为**ButtonMaterial 1**），并在**检查器**中单击 " **Albedo**色" 窗口。</span><span class="sxs-lookup"><span data-stu-id="65387-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="65387-466">此时将显示一个弹出窗口，您可以在其中选择其他颜色（选择任何喜欢的颜色），然后关闭弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="65387-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="65387-467">材料将是其自身的实例，并且不同于原始。</span><span class="sxs-lookup"><span data-stu-id="65387-467">The Material will be its own instance, and different to the original.</span></span>

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="65387-469">将新**材料**拖到**GazeButton**子级上，立即完全更新其外观，使其与第一个场景按钮容易区分。</span><span class="sxs-lookup"><span data-stu-id="65387-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="65387-471">此时，可以在生成 UWP 项目之前在编辑器中测试项目。</span><span class="sxs-lookup"><span data-stu-id="65387-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="65387-472">按下**编辑器**中的 "**播放**" 按钮，戴上耳机。</span><span class="sxs-lookup"><span data-stu-id="65387-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![第7章--设置两个 Unity 场景](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="65387-474">查看两个**GazeButton**对象，以便在第一个和第二个视频之间切换。</span><span class="sxs-lookup"><span data-stu-id="65387-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="65387-475">第8章-构建 UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="65387-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="65387-476">确保编辑器没有错误之后，就可以开始生成了。</span><span class="sxs-lookup"><span data-stu-id="65387-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="65387-477">若要生成：</span><span class="sxs-lookup"><span data-stu-id="65387-477">To Build:</span></span>

1.  <span data-ttu-id="65387-478">单击 "**文件" > "保存**"，保存当前场景。</span><span class="sxs-lookup"><span data-stu-id="65387-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="65387-479">选中名为**Unity C\# 项目**的框（这一点很重要，因为它将允许您在生成完成后编辑类）。</span><span class="sxs-lookup"><span data-stu-id="65387-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="65387-480">请参阅**文件 > 生成设置**，单击 "**生成**"。</span><span class="sxs-lookup"><span data-stu-id="65387-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="65387-481">系统将提示您选择要在其中生成解决方案的文件夹。</span><span class="sxs-lookup"><span data-stu-id="65387-481">You will be prompted to select the folder where you want to build the Solution.</span></span>

5.  <span data-ttu-id="65387-482">创建一个**生成**文件夹，在该文件夹中创建另一个文件夹，其中包含所选的适当名称。</span><span class="sxs-lookup"><span data-stu-id="65387-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="65387-483">单击新文件夹，然后单击 "**选择文件夹**"，然后选择该文件夹以在该位置开始生成。</span><span class="sxs-lookup"><span data-stu-id="65387-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="65387-484">![第8章-构建 UWP 解决方案](images/AzureLabs-Lab6-60.png)
    ![第8章-构建 UWP 解决方案](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="65387-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="65387-485">Unity 完成生成后（可能需要一些时间），将在生成的位置打开**文件资源管理器**窗口。</span><span class="sxs-lookup"><span data-stu-id="65387-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="65387-486">第9章-在本地计算机上部署</span><span class="sxs-lookup"><span data-stu-id="65387-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="65387-487">完成生成后，"**文件资源管理器**" 窗口将出现在生成的位置。</span><span class="sxs-lookup"><span data-stu-id="65387-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="65387-488">打开名为的文件夹，然后双击该文件夹中的解决方案（.sln）文件，以通过 Visual Studio 2017 打开解决方案。</span><span class="sxs-lookup"><span data-stu-id="65387-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="65387-489">唯一要做的事情就是将您的应用程序部署到您的计算机（或*本地计算机*）。</span><span class="sxs-lookup"><span data-stu-id="65387-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="65387-490">部署到本地计算机：</span><span class="sxs-lookup"><span data-stu-id="65387-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="65387-491">在**Visual Studio 2017**中，打开刚刚创建的解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="65387-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="65387-492">在**解决方案平台**中，选择 " **X86，本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="65387-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="65387-493">在**解决方案配置**中，选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="65387-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![第9章--在本地计算机上部署](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="65387-495">你现在需要将任何包还原到你的解决方案中。</span><span class="sxs-lookup"><span data-stu-id="65387-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="65387-496">右键单击**解决方案**，然后单击 "**还原解决方案的 NuGet 包 ...** "。</span><span class="sxs-lookup"><span data-stu-id="65387-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="65387-497">完成此操作的原因是，需要以 Unity 构建的目标来处理本地计算机引用。</span><span class="sxs-lookup"><span data-stu-id="65387-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="65387-498">中转到 "**生成" 菜单**，然后单击 "**部署解决方案**"，将应用程序旁加载到计算机上。</span><span class="sxs-lookup"><span data-stu-id="65387-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="65387-499">Visual Studio 将首先生成并部署你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="65387-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="65387-500">应用现在应显示在已安装的应用列表中，可以启动。</span><span class="sxs-lookup"><span data-stu-id="65387-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![第9章--在本地计算机上部署](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="65387-502">运行混合现实应用程序时，会在应用中使用的**InsideOutSphere**模型中。</span><span class="sxs-lookup"><span data-stu-id="65387-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="65387-503">此球体会将视频流式传输到该位置，从而提供一种360度的传入视频（这是 filmed 的一种形式）。</span><span class="sxs-lookup"><span data-stu-id="65387-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="65387-504">如果需要几秒钟时间来加载视频，请不要惊讶，你的应用程序将受到你的可用 Internet 速度的限制，因为需要获取并下载视频，以便流式传输到你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="65387-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="65387-505">准备就绪后，请通过 gazing 在红色球上来更改场景并打开第二个视频！</span><span class="sxs-lookup"><span data-stu-id="65387-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="65387-506">然后，在第二个场景中使用蓝色立方体即可自由返回！</span><span class="sxs-lookup"><span data-stu-id="65387-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="65387-507">已完成的 Azure 媒体服务应用程序</span><span class="sxs-lookup"><span data-stu-id="65387-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="65387-508">恭喜，你构建了一个利用 Azure 媒体服务流式传输360视频的混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="65387-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![实验室结果](images/AzureLabs-Lab6-00.png)

![实验室结果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="65387-511">额外练习</span><span class="sxs-lookup"><span data-stu-id="65387-511">Bonus Exercises</span></span>

<span data-ttu-id="65387-512">**练习1**</span><span class="sxs-lookup"><span data-stu-id="65387-512">**Exercise 1**</span></span>

<span data-ttu-id="65387-513">在本教程中，完全可以仅使用一个场景来更改视频。</span><span class="sxs-lookup"><span data-stu-id="65387-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="65387-514">试验应用程序并将其放入一个场景！</span><span class="sxs-lookup"><span data-stu-id="65387-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="65387-515">甚至可能将其他视频添加到组合。</span><span class="sxs-lookup"><span data-stu-id="65387-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="65387-516">**练习2**</span><span class="sxs-lookup"><span data-stu-id="65387-516">**Exercise 2**</span></span>

<span data-ttu-id="65387-517">试验 Azure 和 Unity，尝试实现此功能，使应用程序能够根据 Internet 连接的强度，自动选择不同文件大小的视频。</span><span class="sxs-lookup"><span data-stu-id="65387-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


