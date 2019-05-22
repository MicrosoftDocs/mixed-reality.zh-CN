---
title: MR 和 Azure 306-流式传输视频
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 媒体服务。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api，媒体服务，流式处理视频中，360，令人着迷，vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591606"
---
>[!NOTE]
><span data-ttu-id="2b924-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="2b924-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="2b924-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="2b924-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="2b924-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="2b924-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="2b924-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="2b924-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="2b924-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="2b924-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="2b924-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="2b924-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="2b924-110">MR 和 Azure 306:流式处理视频</span><span class="sxs-lookup"><span data-stu-id="2b924-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="2b924-111">![最终产品-启动](images/AzureLabs-Lab6-00.png)
![最终产品-启动](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="2b924-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="2b924-112">在本课程将了解如何连接到 Windows 混合现实 VR 体验，以允许流式处理在沉浸式耳机 360 度视频播放你的 Azure 媒体服务。</span><span class="sxs-lookup"><span data-stu-id="2b924-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="2b924-113">**Azure 媒体服务**是一系列服务，可提供广播品质视频流式传输服务来访问在当今最受欢迎的移动设备上更广泛的受众。</span><span class="sxs-lookup"><span data-stu-id="2b924-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="2b924-114">有关详细信息，请访问[Azure 媒体服务页](https://azure.microsoft.com/services/media-services)。</span><span class="sxs-lookup"><span data-stu-id="2b924-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="2b924-115">已完成本课程，会创建一个混合的现实沉浸式头戴式应用程序，这将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2b924-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="2b924-116">检索来自的 360 度视频**Azure 存储**，通过**Azure 媒体服务**。</span><span class="sxs-lookup"><span data-stu-id="2b924-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="2b924-117">显示在 Unity 场景中的检索到 360 度视频。</span><span class="sxs-lookup"><span data-stu-id="2b924-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="2b924-118">具有两个不同的视频的两个场景之间进行导航。</span><span class="sxs-lookup"><span data-stu-id="2b924-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="2b924-119">在您的应用程序，它是取决于您关于如何将与您的设计集成结果。</span><span class="sxs-lookup"><span data-stu-id="2b924-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="2b924-120">本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="2b924-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="2b924-121">它是作业以使用此课程以增强混合的现实应用程序中获取的知识。</span><span class="sxs-lookup"><span data-stu-id="2b924-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="2b924-122">设备支持</span><span class="sxs-lookup"><span data-stu-id="2b924-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="2b924-123">课程</span><span class="sxs-lookup"><span data-stu-id="2b924-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="2b924-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="2b924-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="2b924-125"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="2b924-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="2b924-126">MR 和 Azure 306:流式处理视频</span><span class="sxs-lookup"><span data-stu-id="2b924-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="2b924-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2b924-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="2b924-128">系统必备</span><span class="sxs-lookup"><span data-stu-id="2b924-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="2b924-129">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="2b924-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="2b924-130">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。</span><span class="sxs-lookup"><span data-stu-id="2b924-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="2b924-131">你可以随意使用最新的软件，如中所列[安装工具一文](install-the-tools.md)，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.</span><span class="sxs-lookup"><span data-stu-id="2b924-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="2b924-132">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="2b924-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="2b924-133">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="2b924-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="2b924-134">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="2b924-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2b924-135">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="2b924-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2b924-136">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="2b924-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="2b924-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="2b924-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="2b924-138">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="2b924-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="2b924-139">用于 Azure 的安装程序和数据检索的 Internet 访问权限</span><span class="sxs-lookup"><span data-stu-id="2b924-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="2b924-140">两个 mp4 格式的 360 度视频 (可以找到一些免版税的视频[在此下载页面](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="2b924-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="2b924-141">开始之前</span><span class="sxs-lookup"><span data-stu-id="2b924-141">Before you start</span></span>

1.  <span data-ttu-id="2b924-142">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="2b924-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="2b924-143">设置和测试在混合现实沉浸式头戴式。</span><span class="sxs-lookup"><span data-stu-id="2b924-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2b924-144">你将**不**此课程需要运动控制器。</span><span class="sxs-lookup"><span data-stu-id="2b924-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="2b924-145">如果你需要支持沉浸式头戴式设置，请单击[k 了解如何设置 Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)。</span><span class="sxs-lookup"><span data-stu-id="2b924-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="2b924-146">第 1 章-Azure 门户： 创建 Azure 存储帐户</span><span class="sxs-lookup"><span data-stu-id="2b924-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="2b924-147">若要使用**Azure 存储服务**，将需要创建和配置**存储帐户**在 Azure 门户中。</span><span class="sxs-lookup"><span data-stu-id="2b924-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="2b924-148">登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="2b924-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2b924-149">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="2b924-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="2b924-150">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="2b924-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="2b924-151">你登录后，单击**存储帐户**在左侧菜单中。</span><span class="sxs-lookup"><span data-stu-id="2b924-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="2b924-153">上**存储帐户**选项卡上，单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="2b924-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="2b924-155">在中**创建存储帐户**选项卡：</span><span class="sxs-lookup"><span data-stu-id="2b924-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="2b924-156">插入**名称**对于你的帐户，请注意此字段仅接受数字和小写字母。</span><span class="sxs-lookup"><span data-stu-id="2b924-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="2b924-157">有关**部署模型**选择**资源管理器**。</span><span class="sxs-lookup"><span data-stu-id="2b924-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="2b924-158">有关**帐户类型**，选择**存储 (常规用途 v1)**。</span><span class="sxs-lookup"><span data-stu-id="2b924-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="2b924-159">有关**性能**，选择 **标准\*。**</span><span class="sxs-lookup"><span data-stu-id="2b924-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="2b924-160">有关**复制**选择**本地冗余存储 (LRS)**。</span><span class="sxs-lookup"><span data-stu-id="2b924-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="2b924-161">将保留**需要安全传输**作为**禁用**。</span><span class="sxs-lookup"><span data-stu-id="2b924-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="2b924-162">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="2b924-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="2b924-163">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="2b924-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="2b924-164">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="2b924-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="2b924-165">确定**位置**为资源组 （如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="2b924-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="2b924-166">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="2b924-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="2b924-167">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="2b924-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="2b924-168">你需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="2b924-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="2b924-170">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="2b924-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="2b924-171">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="2b924-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 存储帐户设置](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="2b924-173">此时你不需要以按照该资源，只需转到下一章。</span><span class="sxs-lookup"><span data-stu-id="2b924-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="2b924-174">章 2-在 Azure 门户： 创建媒体服务</span><span class="sxs-lookup"><span data-stu-id="2b924-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="2b924-175">若要使用 Azure 媒体服务，你需要配置要成为可用于应用程序 （其中帐户持有者必须是管理员） 的服务的实例。</span><span class="sxs-lookup"><span data-stu-id="2b924-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="2b924-176">在 Azure 门户中，单击**创建资源**在左上角，并搜索**媒体服务**按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="2b924-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="2b924-177">当前所需的资源有一个粉红色的图标;单击此项，以显示新页面。</span><span class="sxs-lookup"><span data-stu-id="2b924-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="2b924-179">该新页面将提供的说明**媒体服务**。</span><span class="sxs-lookup"><span data-stu-id="2b924-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="2b924-180">在左下角此提示，请单击**创建**按钮，以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="2b924-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="2b924-182">一旦你单击**创建**面板将显示您需要提供一些有关新的媒体服务的详细信息：</span><span class="sxs-lookup"><span data-stu-id="2b924-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="2b924-183">插入所需**帐户名**此服务实例。</span><span class="sxs-lookup"><span data-stu-id="2b924-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="2b924-184">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="2b924-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="2b924-185">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="2b924-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="2b924-186">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="2b924-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="2b924-187">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="2b924-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="2b924-188">如果你想要阅读更多有关 Azure 资源组，请遵循此[如何管理 Azure 资源组链接](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="2b924-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="2b924-189">确定**位置**为资源组 （如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="2b924-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="2b924-190">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="2b924-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="2b924-191">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="2b924-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="2b924-192">有关**存储帐户**部分中，单击**请选择...** 部分，然后单击**存储帐户**在最后一章中创建。</span><span class="sxs-lookup"><span data-stu-id="2b924-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="2b924-193">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="2b924-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="2b924-194">单击“创建”。</span><span class="sxs-lookup"><span data-stu-id="2b924-194">Click **Create**.</span></span>

        ![在 Azure 门户](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="2b924-196">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="2b924-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="2b924-197">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="2b924-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="2b924-199">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="2b924-199">Click on the notification to explore your new Service instance.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="2b924-201">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="2b924-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="2b924-202">中新的媒体服务页上，在左侧面板中单击**资产**链接，这是有关中间的列表。</span><span class="sxs-lookup"><span data-stu-id="2b924-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="2b924-203">在下一步页上的页上，在左上角中，单击**上传**。</span><span class="sxs-lookup"><span data-stu-id="2b924-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="2b924-205">单击**文件夹**图标来浏览你的文件，然后选择你想要流式传输的第一次 360 视频。</span><span class="sxs-lookup"><span data-stu-id="2b924-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="2b924-206">你可以按照这[链接以下载示例视频](https://vimeo.com/214401712)。</span><span class="sxs-lookup"><span data-stu-id="2b924-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="2b924-208">长文件名可能会导致出现问题，与编码器： 因此若要确保视频是否有问题，请考虑缩短你的视频文件名称的长度。</span><span class="sxs-lookup"><span data-stu-id="2b924-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="2b924-209">视频完成上传时，进度栏将变为绿色。</span><span class="sxs-lookup"><span data-stu-id="2b924-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="2b924-211">单击上面的文本 (**yourservicename-资产**) 以返回到**资产**页。</span><span class="sxs-lookup"><span data-stu-id="2b924-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="2b924-212">您会注意到你的视频已成功上载。</span><span class="sxs-lookup"><span data-stu-id="2b924-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="2b924-213">单击它。</span><span class="sxs-lookup"><span data-stu-id="2b924-213">Click on it.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="2b924-215">将重定向到的页面将显示有关你的视频的详细信息。</span><span class="sxs-lookup"><span data-stu-id="2b924-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="2b924-216">若要能够使用你需要进行编码，通过单击的视频**编码**页的顶部左侧的按钮。</span><span class="sxs-lookup"><span data-stu-id="2b924-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="2b924-218">一个新的面板将显示右侧，其中你将能够设置编码选项，为你的文件。</span><span class="sxs-lookup"><span data-stu-id="2b924-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="2b924-219">设置以下属性 （一些将已设置默认情况下）：</span><span class="sxs-lookup"><span data-stu-id="2b924-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="2b924-220">**媒体编码器名称\*Media Encoder Standard**\*</span><span class="sxs-lookup"><span data-stu-id="2b924-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="2b924-221">**编码预设\*内容自适应多比特率 MP4**\*</span><span class="sxs-lookup"><span data-stu-id="2b924-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="2b924-222">**作业名称\*Video1.mp4 的 Media Encoder Standard 处理**\*</span><span class="sxs-lookup"><span data-stu-id="2b924-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="2b924-223">**输出媒体资产名称\*Video1.mp4-Media Encoder Standard 编码**\*</span><span class="sxs-lookup"><span data-stu-id="2b924-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![在 Azure 门户](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="2b924-225">单击“创建”按钮。</span><span class="sxs-lookup"><span data-stu-id="2b924-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="2b924-226">你会注意到一个带条**添加的编码作业**、 单击该条形图和一个面板将显示为带有编码进度显示在它。</span><span class="sxs-lookup"><span data-stu-id="2b924-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-17.png)

    ![在 Azure 门户](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="2b924-229">等待作业完成。</span><span class="sxs-lookup"><span data-stu-id="2b924-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="2b924-230">完成后，随时关闭面板中的 X 右上角的该面板。</span><span class="sxs-lookup"><span data-stu-id="2b924-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-19.png)

    ![在 Azure 门户](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="2b924-233">此操作，时间取决于你的视频的文件大小。</span><span class="sxs-lookup"><span data-stu-id="2b924-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="2b924-234">此过程可能需要很长时间。</span><span class="sxs-lookup"><span data-stu-id="2b924-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="2b924-235">现在，已创建编码的视频版本，可以发布它，对其进行访问。</span><span class="sxs-lookup"><span data-stu-id="2b924-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="2b924-236">若要执行此操作，请单击蓝色的链接**资产**以返回到资产页上。</span><span class="sxs-lookup"><span data-stu-id="2b924-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="2b924-238">你将看到你的视频以及其他的 \**资产类型*多比特率 MP4\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b924-238">You will see your video along with another, which is of \*\*Asset Type \*Multi-Bitrate MP4\*\*\*.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="2b924-240">您可能会注意到新的资产，以及初始视频，是*未知*，并且它是具有"0"字节**大小**，只需刷新您的窗口进行更新。</span><span class="sxs-lookup"><span data-stu-id="2b924-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="2b924-241">单击此新资产。</span><span class="sxs-lookup"><span data-stu-id="2b924-241">Click this new asset.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="2b924-243">你将看到一个类似于使用之前，只需这是不同的资产面板。</span><span class="sxs-lookup"><span data-stu-id="2b924-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="2b924-244">单击**发布**按钮位于页的顶部中央。</span><span class="sxs-lookup"><span data-stu-id="2b924-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="2b924-246">将提示您设置**定位器**，这是入口点，在你的资产中文件/秒。</span><span class="sxs-lookup"><span data-stu-id="2b924-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="2b924-247">对于你的方案设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="2b924-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="2b924-248">**定位符类型** > **渐进式**。</span><span class="sxs-lookup"><span data-stu-id="2b924-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="2b924-249">**日期**并**时间**将设置，从当前日期，为将来的时间 （在本例中为 100 个年）。</span><span class="sxs-lookup"><span data-stu-id="2b924-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="2b924-250">将保留原样或将其更改为满足。</span><span class="sxs-lookup"><span data-stu-id="2b924-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2b924-251">有关定位符，并可以选择的详细信息，请访问[Azure 媒体服务文档](https://docs.microsoft.com/azure/media-services/media-services-concepts)。</span><span class="sxs-lookup"><span data-stu-id="2b924-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="2b924-252">在该面板的底部，单击**添加**按钮。</span><span class="sxs-lookup"><span data-stu-id="2b924-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="2b924-254">你的视频现已发布，并可以通过使用其终结点进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="2b924-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="2b924-255">进一步向下的页面**文件**部分。</span><span class="sxs-lookup"><span data-stu-id="2b924-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="2b924-256">这是视频的将不同的编码的版本的位置。</span><span class="sxs-lookup"><span data-stu-id="2b924-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="2b924-257">选择其中一个最高可能的解决方案 （在下图为 1920 x 960 文件），随后会显示右侧面板。</span><span class="sxs-lookup"><span data-stu-id="2b924-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="2b924-258">可以在其中找到**下载 URL**。</span><span class="sxs-lookup"><span data-stu-id="2b924-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="2b924-259">复制这**终结点**因为你将使用它在代码中更高版本。</span><span class="sxs-lookup"><span data-stu-id="2b924-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-26.png)    

    ![在 Azure 门户](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="2b924-262">此外可以按**播放**按钮以播放视频，并对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="2b924-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="2b924-263">现在需要将在此实验室中将使用第二个视频上传。</span><span class="sxs-lookup"><span data-stu-id="2b924-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="2b924-264">按照上面的步骤，为第二个视频重复相同的过程。</span><span class="sxs-lookup"><span data-stu-id="2b924-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="2b924-265">确保复制第二个**终结点**还。</span><span class="sxs-lookup"><span data-stu-id="2b924-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="2b924-266">使用以下[链接以下载第二个视频](https://vimeo.com/214402865)。</span><span class="sxs-lookup"><span data-stu-id="2b924-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="2b924-267">这两个视频已发布，已准备好移动到下一章。</span><span class="sxs-lookup"><span data-stu-id="2b924-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="2b924-268">第 3 章 — 设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="2b924-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="2b924-269">以下是一组典型使用混合现实中，进行开发并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="2b924-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="2b924-270">打开**Unity**然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="2b924-270">Open **Unity** and click **New**.</span></span> 

    ![在 Azure 门户](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="2b924-272">现在将需要提供 Unity 项目的名称，插入**MR\_360VideoStreaming**。</span><span class="sxs-lookup"><span data-stu-id="2b924-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="2b924-273">请确保项目类型设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="2b924-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="2b924-274">将位置设置为适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="2b924-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="2b924-275">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="2b924-275">Then, click **Create project**.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="2b924-277">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="2b924-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="2b924-278">转到***编辑* *首选项*** ，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="2b924-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="2b924-279">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="2b924-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="2b924-280">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="2b924-280">Close the **Preferences** window.</span></span>

    ![在 Azure 门户](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="2b924-282">接下来，请转到***文件* *生成设置*** 并切换到平台**通用 Windows 平台**，通过单击**交换机平台**按钮。</span><span class="sxs-lookup"><span data-stu-id="2b924-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="2b924-283">此外，请确保：</span><span class="sxs-lookup"><span data-stu-id="2b924-283">Also make sure that:</span></span>

    1. <span data-ttu-id="2b924-284">**设备为目标**设置为**任一设备。**</span><span class="sxs-lookup"><span data-stu-id="2b924-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="2b924-285">**生成的类型**设置为**D3D。**</span><span class="sxs-lookup"><span data-stu-id="2b924-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="2b924-286">**SDK**设置为**最新安装。**</span><span class="sxs-lookup"><span data-stu-id="2b924-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="2b924-287">**Visual Studio 版本**设置为**最新安装。**</span><span class="sxs-lookup"><span data-stu-id="2b924-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="2b924-288">**生成并运行**设置为**本地计算机。**</span><span class="sxs-lookup"><span data-stu-id="2b924-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="2b924-289">有关设置的信息，请不要担心**场景**稍后再试，因为您将这些设置更高版本。</span><span class="sxs-lookup"><span data-stu-id="2b924-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="2b924-290">现在，应为默认值保留剩余的设置。</span><span class="sxs-lookup"><span data-stu-id="2b924-290">The remaining settings should be left as default for now.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="2b924-292">在**生成设置**窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。</span><span class="sxs-lookup"><span data-stu-id="2b924-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="2b924-293">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="2b924-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="2b924-294">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="2b924-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="2b924-295">**脚本编写** **运行时版本**应**稳定**（.NET 3.5 等效）。</span><span class="sxs-lookup"><span data-stu-id="2b924-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="2b924-296">**脚本编写后端**应为 **.NET。**</span><span class="sxs-lookup"><span data-stu-id="2b924-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="2b924-297">**API 兼容性级别**应为 **.NET 4.6。**</span><span class="sxs-lookup"><span data-stu-id="2b924-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="2b924-299">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。</span><span class="sxs-lookup"><span data-stu-id="2b924-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![设置 Unity 项目](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="2b924-301">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="2b924-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="2b924-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="2b924-302">**InternetClient**</span></span>

            ![设置 Unity 项目](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="2b924-304">一旦进行这些更改，关闭**生成设置**窗口。</span><span class="sxs-lookup"><span data-stu-id="2b924-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="2b924-305">保存项目 \**文件* \*保存项目\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b924-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="2b924-306">第 4 章-导入 InsideOutSphere Unity 程序包</span><span class="sxs-lookup"><span data-stu-id="2b924-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b924-307">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)，将其导入项目中，作为[ **自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从**第 5 章：**。</span><span class="sxs-lookup"><span data-stu-id="2b924-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="2b924-308">仍需要创建一个 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="2b924-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="2b924-309">为此课程需要先下载 Unity 资产包名为[ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="2b924-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="2b924-310">操作方法导入**unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="2b924-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="2b924-311">准备好 Unity 仪表板中，单击**资产**在屏幕顶部的菜单，然后单击**导入包 > 自定义包**。</span><span class="sxs-lookup"><span data-stu-id="2b924-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="2b924-313">使用文件选取器选择**InsideOutSphere.unitypackage**程序包，再单击**打开**。</span><span class="sxs-lookup"><span data-stu-id="2b924-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="2b924-314">将向你显示此资产的组件的列表。</span><span class="sxs-lookup"><span data-stu-id="2b924-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="2b924-315">通过单击确认导入**导入**。</span><span class="sxs-lookup"><span data-stu-id="2b924-315">Confirm the import by clicking **Import**.</span></span>

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="2b924-317">完成导入后，你会注意到三个新文件夹**材料**，**模型**，并**预设**，已添加到你**资产**文件夹。</span><span class="sxs-lookup"><span data-stu-id="2b924-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="2b924-318">此类文件夹结构是典型的 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="2b924-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="2b924-320">打开**模型**文件夹中，并且你将看到**InsideOutSphere**已导入模型。</span><span class="sxs-lookup"><span data-stu-id="2b924-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="2b924-321">内**材料**文件夹将为您**InsideOutSpheres**材料*lambert1*，以及名为材料*ButtonMaterial*，由 GazeButton，很快你将看到它。</span><span class="sxs-lookup"><span data-stu-id="2b924-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="2b924-322">**预设**文件夹包含**InsideOutSphere**其中同时包含预设**InsideOutSphere** *模型*和*GazeButton*。</span><span class="sxs-lookup"><span data-stu-id="2b924-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="2b924-323">**不不包含任何代码**，将按照本课程中编写的代码。</span><span class="sxs-lookup"><span data-stu-id="2b924-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="2b924-324">内**层次结构**，选择**Main Camera**对象，并更新以下组件：</span><span class="sxs-lookup"><span data-stu-id="2b924-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="2b924-325">**转换**</span><span class="sxs-lookup"><span data-stu-id="2b924-325">**Transform**</span></span>

        1.  <span data-ttu-id="2b924-326">位置 = **X**:0， **Y**:0， **Z**:0.</span><span class="sxs-lookup"><span data-stu-id="2b924-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="2b924-327">旋转 = **X**:0， **Y**:0， **Z**:0.</span><span class="sxs-lookup"><span data-stu-id="2b924-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="2b924-328">规模**X**:1， **Y**:1， **Z**:1.</span><span class="sxs-lookup"><span data-stu-id="2b924-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="2b924-329">**摄像头**</span><span class="sxs-lookup"><span data-stu-id="2b924-329">**Camera**</span></span>

        1. <span data-ttu-id="2b924-330">**清除标志**:纯色。</span><span class="sxs-lookup"><span data-stu-id="2b924-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="2b924-331">**剪裁平面**:附近：0.1，得：6.</span><span class="sxs-lookup"><span data-stu-id="2b924-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="2b924-333">导航到**Prefab**文件夹，然后再拖动**InsideOutSphere**到 prefab**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="2b924-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="2b924-335">展开**InsideOutSphere**对象内**层次结构**通过单击它旁边的小箭头。</span><span class="sxs-lookup"><span data-stu-id="2b924-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="2b924-336">你将看到**子**对象调用它下面**GazeButton**。</span><span class="sxs-lookup"><span data-stu-id="2b924-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="2b924-337">这将用于更改场景，因此视频。</span><span class="sxs-lookup"><span data-stu-id="2b924-337">This will be used to change scenes and thus videos.</span></span>

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="2b924-339">在检查器窗口中单击**InsideOutSphere**的转换组件中，确保设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="2b924-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="2b924-340">转换的位置</span><span class="sxs-lookup"><span data-stu-id="2b924-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="2b924-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-341">**X** 0</span></span>  |          <span data-ttu-id="2b924-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-342">**Y** 0</span></span>          |  <span data-ttu-id="2b924-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="2b924-344">转换的旋转</span><span class="sxs-lookup"><span data-stu-id="2b924-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="2b924-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-345">**X** 0</span></span>  |          <span data-ttu-id="2b924-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="2b924-346">**Y** -50</span></span>        |  <span data-ttu-id="2b924-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="2b924-348">转换-横向</span><span class="sxs-lookup"><span data-stu-id="2b924-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="2b924-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="2b924-349">**X** 1</span></span>   |          <span data-ttu-id="2b924-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="2b924-350">**Y** 1</span></span>          |  <span data-ttu-id="2b924-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="2b924-351">**Z** 1</span></span>  |

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="2b924-353">单击**GazeButton**子对象，并设置其**转换**，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b924-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="2b924-354">转换的位置</span><span class="sxs-lookup"><span data-stu-id="2b924-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="2b924-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="2b924-355">**X** 3.6</span></span>|          <span data-ttu-id="2b924-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="2b924-356">**Y** 1.3</span></span>        |  <span data-ttu-id="2b924-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="2b924-358">转换的旋转</span><span class="sxs-lookup"><span data-stu-id="2b924-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="2b924-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-359">**X** 0</span></span>  |          <span data-ttu-id="2b924-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-360">**Y** 0</span></span>          |  <span data-ttu-id="2b924-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="2b924-362">转换-横向</span><span class="sxs-lookup"><span data-stu-id="2b924-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="2b924-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="2b924-363">**X** 1</span></span>   |          <span data-ttu-id="2b924-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="2b924-364">**Y** 1</span></span>          |  <span data-ttu-id="2b924-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="2b924-365">**Z** 1</span></span>  |

    ![导入 InsideOutSphere Unity 程序包](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="2b924-367">章节 5-创建 VideoController 类</span><span class="sxs-lookup"><span data-stu-id="2b924-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="2b924-368">**VideoController**类承载将使用从 Azure 媒体服务内容进行流式传输的两个视频终结点。</span><span class="sxs-lookup"><span data-stu-id="2b924-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="2b924-369">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="2b924-369">To create this class:</span></span>

1.  <span data-ttu-id="2b924-370">在中右击**资产文件夹**，它位于**项目**面板中，然后单击**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="2b924-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="2b924-371">将文件夹命名为**脚本**。</span><span class="sxs-lookup"><span data-stu-id="2b924-371">Name the folder **Scripts**.</span></span>

    ![创建 VideoController 类](images/AzureLabs-Lab6-43.png)

    ![创建 VideoController 类](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="2b924-374">双击**脚本**文件夹将其打开。</span><span class="sxs-lookup"><span data-stu-id="2b924-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="2b924-375">在文件夹中，右键单击，然后单击**创建 > C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="2b924-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="2b924-376">脚本命名为**VideoController**。</span><span class="sxs-lookup"><span data-stu-id="2b924-376">Name the script **VideoController**.</span></span>

    ![创建 VideoController 类](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="2b924-378">双击新**VideoController**脚本以将其与打开**Visual Studio 2017。**</span><span class="sxs-lookup"><span data-stu-id="2b924-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![创建 VideoController 类](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="2b924-380">更新代码文件顶部的命名空间，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b924-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="2b924-381">输入中的以下变量**VideoController**类，以及与**Awake()** 方法：</span><span class="sxs-lookup"><span data-stu-id="2b924-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

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

7.  <span data-ttu-id="2b924-382">现在是时候从 Azure 媒体服务视频输入终结点：</span><span class="sxs-lookup"><span data-stu-id="2b924-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="2b924-383">到第一个*video1endpoint*变量。</span><span class="sxs-lookup"><span data-stu-id="2b924-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="2b924-384">到第二个*video2endpoint*变量。</span><span class="sxs-lookup"><span data-stu-id="2b924-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="2b924-385">没有使用的已知的问题*https* Unity，并选择版本 2017.4.1f1 内。</span><span class="sxs-lookup"><span data-stu-id="2b924-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="2b924-386">如果视频 play 上提供了错误，请尝试改为使用 http。</span><span class="sxs-lookup"><span data-stu-id="2b924-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="2b924-387">下一步， **start （)** 方法需要对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="2b924-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="2b924-388">每次用户通过查看对此按钮切换 （因此切换视频） 的场景时，将触发此方法。</span><span class="sxs-lookup"><span data-stu-id="2b924-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="2b924-389">遵循**start （)** 方法中，插入**PlayVideo()** *IEnumerator*方法，它将用于启动视频无缝 （以便看到没有出现断断续续的问题）。</span><span class="sxs-lookup"><span data-stu-id="2b924-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

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

10. <span data-ttu-id="2b924-390">最后一种方法需要将此类是**ChangeScene()** 方法，它将用于场景之间交换。</span><span class="sxs-lookup"><span data-stu-id="2b924-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="2b924-391">**ChangeScene()** 方法使用方便 C\#功能调用*条件运算符*。</span><span class="sxs-lookup"><span data-stu-id="2b924-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="2b924-392">这允许要检查的条件，然后值基于返回的这项检查，在单个语句中的所有结果。</span><span class="sxs-lookup"><span data-stu-id="2b924-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="2b924-393">按照这[链接，了解有关条件运算符的详细信息](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)。</span><span class="sxs-lookup"><span data-stu-id="2b924-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="2b924-394">返回到 Unity 之前，Visual Studio 中保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2b924-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="2b924-395">返回在 Unity 编辑器中，单击并拖动**VideoController**类 [通过] {.underline}**脚本**文件夹**Main Camera**对象中**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="2b924-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="2b924-396">单击**Main Camera**并查看**检查器面板**。</span><span class="sxs-lookup"><span data-stu-id="2b924-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="2b924-397">您将注意到，在新添加的脚本组件没有具有空值的字段。</span><span class="sxs-lookup"><span data-stu-id="2b924-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="2b924-398">这是引用字段，以在代码中的公共变量为目标。</span><span class="sxs-lookup"><span data-stu-id="2b924-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="2b924-399">拖动**InsideOutSphere**对象从**层次结构面板**到**球体**槽，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="2b924-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="2b924-400">![创建 VideoController 类](images/AzureLabs-Lab6-47.png)
    ![创建 VideoController 类](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="2b924-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="2b924-401">章 6-创建的视线移动类</span><span class="sxs-lookup"><span data-stu-id="2b924-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="2b924-402">此类负责创建**Raycast** ，将 beprojected 转发从**Main Camera**，以检测用户查看的对象。</span><span class="sxs-lookup"><span data-stu-id="2b924-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="2b924-403">在这种情况下， **Raycast**需要确定如果用户寻求**GazeButton**对象在场景中，并触发一个行为。</span><span class="sxs-lookup"><span data-stu-id="2b924-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="2b924-404">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="2b924-404">To create this Class:</span></span>

1.  <span data-ttu-id="2b924-405">转到**脚本**之前创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2b924-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="2b924-406">在中右击**项目**面板中，\**创建* \*C\# 脚本\*\*。</span><span class="sxs-lookup"><span data-stu-id="2b924-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="2b924-407">脚本命名为**注视**。</span><span class="sxs-lookup"><span data-stu-id="2b924-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="2b924-408">双击新***注视***脚本以将其与打开**Visual Studio 2017。**</span><span class="sxs-lookup"><span data-stu-id="2b924-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="2b924-409">确保以下命名空间顶部的脚本，并删除任何其他人：</span><span class="sxs-lookup"><span data-stu-id="2b924-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="2b924-410">然后添加以下变量内的**注视**类：</span><span class="sxs-lookup"><span data-stu-id="2b924-410">Then add the following variables inside the **Gaze** class:</span></span>

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

6.  <span data-ttu-id="2b924-411">为代码**Awake()** 并**start （)** 方法现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="2b924-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="2b924-412">将以下代码中的添加**update （)** 方法投影 Raycast 和检测对目标的影响：</span><span class="sxs-lookup"><span data-stu-id="2b924-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

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

8.  <span data-ttu-id="2b924-413">返回到 Unity 之前，Visual Studio 中保存所做的更改。</span><span class="sxs-lookup"><span data-stu-id="2b924-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="2b924-414">单击并拖动**注视**从脚本文件夹中的 Main Camera 对象的类**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="2b924-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="2b924-415">第 7 章 — 安装这两个 Unity 场景</span><span class="sxs-lookup"><span data-stu-id="2b924-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="2b924-416">此章节的目的是设置两个场景，每个托管的视频流。</span><span class="sxs-lookup"><span data-stu-id="2b924-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="2b924-417">以便您不需要安装它，同样，尽管将然后编辑新的场景中，将复制已创建的场景，以便*GazeButton*对象处于不同位置且具有不同的外观。</span><span class="sxs-lookup"><span data-stu-id="2b924-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="2b924-418">这是为了演示如何更改之间的场景。</span><span class="sxs-lookup"><span data-stu-id="2b924-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="2b924-419">执行此操作通过转到**文件 > 将场景另存为...**.保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="2b924-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="2b924-420">单击**新文件夹**按钮。</span><span class="sxs-lookup"><span data-stu-id="2b924-420">Click the **New folder** button.</span></span>

    ![第 7 章 — 安装这两个 Unity 场景](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="2b924-422">将文件夹命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="2b924-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="2b924-423">**保存场景**窗口仍为打开状态。</span><span class="sxs-lookup"><span data-stu-id="2b924-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="2b924-424">打开新建**场景**文件夹。</span><span class="sxs-lookup"><span data-stu-id="2b924-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="2b924-425">在中**文件的名称：** 文本字段中，键入**VideoScene1**，然后按**保存**。</span><span class="sxs-lookup"><span data-stu-id="2b924-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="2b924-426">在 Unity 中，打开你**场景**文件夹，再左键单击你**VideoScene1**文件。</span><span class="sxs-lookup"><span data-stu-id="2b924-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="2b924-427">使用键盘，按**Ctrl + D**将复制该场景</span><span class="sxs-lookup"><span data-stu-id="2b924-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="2b924-428">**重复**命令也可以通过导航到**编辑 > 重复**。</span><span class="sxs-lookup"><span data-stu-id="2b924-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="2b924-429">Unity 将自动递增场景名称编号，但不管怎样，检查它以确保它匹配以前插入的代码。</span><span class="sxs-lookup"><span data-stu-id="2b924-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="2b924-430">您应该**VideoScene1**并**VideoScene2**。</span><span class="sxs-lookup"><span data-stu-id="2b924-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="2b924-431">与在两个场景，请转到**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="2b924-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="2b924-432">与**生成设置**窗口中打开，拖动到您的场景**生成中的场景**部分。</span><span class="sxs-lookup"><span data-stu-id="2b924-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="2b924-434">您可以选择这两个从您的场景你**场景**通过持有锁的文件夹**Ctrl**按钮，然后单击鼠标左键每个场景，并最后拖动这两个。</span><span class="sxs-lookup"><span data-stu-id="2b924-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="2b924-435">关闭**生成设置**窗口中，并双击**VideoScene2**。</span><span class="sxs-lookup"><span data-stu-id="2b924-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="2b924-436">使用打开第二个场景中，单击**GazeButton**的子对象**InsideOutSphere**，并将其转换设置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2b924-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="2b924-437">转换的位置</span><span class="sxs-lookup"><span data-stu-id="2b924-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="2b924-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-438">**X** 0</span></span>  |         <span data-ttu-id="2b924-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="2b924-439">**Y** 1.3</span></span>         | <span data-ttu-id="2b924-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="2b924-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="2b924-441">转换的旋转</span><span class="sxs-lookup"><span data-stu-id="2b924-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="2b924-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-442">**X** 0</span></span>  |          <span data-ttu-id="2b924-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-443">**Y** 0</span></span>          |  <span data-ttu-id="2b924-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="2b924-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="2b924-445">转换-横向</span><span class="sxs-lookup"><span data-stu-id="2b924-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="2b924-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="2b924-446">**X** 1</span></span>   |          <span data-ttu-id="2b924-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="2b924-447">**Y** 1</span></span>          |  <span data-ttu-id="2b924-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="2b924-448">**Z** 1</span></span>  |

10. <span data-ttu-id="2b924-449">与**GazeButton**仍处于选中状态，查看在子**Inspector**并在**网格筛选器**。</span><span class="sxs-lookup"><span data-stu-id="2b924-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="2b924-450">单击小目标旁边**Mesh**引用字段：</span><span class="sxs-lookup"><span data-stu-id="2b924-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="2b924-452">一个**选择网格**弹出窗口随即出现。</span><span class="sxs-lookup"><span data-stu-id="2b924-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="2b924-453">双击**多维数据集**从列表中的网格**资产**。</span><span class="sxs-lookup"><span data-stu-id="2b924-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="2b924-455">**网格筛选器**将更新和现在是**多维数据集**。</span><span class="sxs-lookup"><span data-stu-id="2b924-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="2b924-456">现在，单击**齿轮**旁边的图标**球体碰撞体**然后单击**删除组件**，若要删除此对象的碰撞体。</span><span class="sxs-lookup"><span data-stu-id="2b924-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="2b924-458">与**GazeButton**仍处于选中状态，单击**添加组件**底部的按钮**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="2b924-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="2b924-459">在搜索字段中，键入**框**，并**盒状碰撞体**将作为一个选项，单击要添加**盒状碰撞体**到你**GazeButton**对象.</span><span class="sxs-lookup"><span data-stu-id="2b924-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="2b924-461">**GazeButton**是部分更新，现在看起来不同，但是，您现在将创建一个新**材料**，以便它看上去完全不同，并更轻松地识别为不同的对象，比第一个场景中的对象。</span><span class="sxs-lookup"><span data-stu-id="2b924-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="2b924-462">导航到您**材料**文件夹，在**项目面板**。</span><span class="sxs-lookup"><span data-stu-id="2b924-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="2b924-463">重复**ButtonMaterial**材料 (按**Ctrl** + **D**键盘或单击左键上**材料**，然后从**编辑**文件菜单选项，选择**重复**)。</span><span class="sxs-lookup"><span data-stu-id="2b924-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="2b924-464">![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-55.png)
    ![章 7--设置两个 Unity 场景](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="2b924-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="2b924-465">选择新**ButtonMaterial**材料 (此处名为**ButtonMaterial 1**)，并在**检查器**，单击**Albedo**颜色窗口。</span><span class="sxs-lookup"><span data-stu-id="2b924-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="2b924-466">将显示一个弹出窗口，您可以在其中选择另一种颜色 （选择您喜欢的者为准），然后关闭弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="2b924-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="2b924-467">材料将成为其自己的实例，并与其原始版本不同。</span><span class="sxs-lookup"><span data-stu-id="2b924-467">The Material will be its own instance, and different to the original.</span></span>

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="2b924-469">拖动新**材料**拖动到**GazeButton**子，以便轻松区分开来的第一个场景按钮现在完全更新其看起来。</span><span class="sxs-lookup"><span data-stu-id="2b924-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="2b924-471">现在你可以测试项目在编辑器中生成的 UWP 项目之前。</span><span class="sxs-lookup"><span data-stu-id="2b924-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="2b924-472">按**播放**按钮**编辑器**和 wear 应用耳机。</span><span class="sxs-lookup"><span data-stu-id="2b924-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![第 7 章-设置两个 Unity 场景](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="2b924-474">看看这两个**GazeButton**对象第一个和第二个视频之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="2b924-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="2b924-475">第 8 章-生成 UWP 解决方案</span><span class="sxs-lookup"><span data-stu-id="2b924-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="2b924-476">后确保已在编辑器有任何错误，你就可以生成。</span><span class="sxs-lookup"><span data-stu-id="2b924-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="2b924-477">若要生成：</span><span class="sxs-lookup"><span data-stu-id="2b924-477">To Build:</span></span>

1.  <span data-ttu-id="2b924-478">通过单击保存当前场景**文件 > 保存**。</span><span class="sxs-lookup"><span data-stu-id="2b924-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="2b924-479">选中复选框调用**Unity C\#项目**（这是重要因为这可以使您可以编辑类生成完成后）。</span><span class="sxs-lookup"><span data-stu-id="2b924-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="2b924-480">转到**文件 > 生成设置**，单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="2b924-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="2b924-481">系统将提示您选择，您希望对 buildthe 解决方案的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2b924-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="2b924-482">创建**生成**文件夹并在该文件夹中创建另一个文件夹，与所选的适当的名称。</span><span class="sxs-lookup"><span data-stu-id="2b924-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="2b924-483">单击新文件夹，然后单击**选择文件夹**，因此，若要选择该文件夹中，若要开始在该位置的生成。</span><span class="sxs-lookup"><span data-stu-id="2b924-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="2b924-484">![第 8 章-生成 UWP 解决方案](images/AzureLabs-Lab6-60.png)
    ![章 8-生成 UWP 解决方案](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="2b924-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="2b924-485">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置。</span><span class="sxs-lookup"><span data-stu-id="2b924-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="2b924-486">在本地计算机上部署一章 9-</span><span class="sxs-lookup"><span data-stu-id="2b924-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="2b924-487">完成生成后，**文件资源管理器**窗口将出现在生成的位置。</span><span class="sxs-lookup"><span data-stu-id="2b924-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="2b924-488">打开的文件夹名为并生成，然后双击该文件夹，以使用 Visual Studio 2017 中打开你的解决方案中的解决方案 (.sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="2b924-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="2b924-489">一件事要做是将应用部署到您的计算机 (或*本地计算机*)。</span><span class="sxs-lookup"><span data-stu-id="2b924-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="2b924-490">若要将部署到本地计算机：</span><span class="sxs-lookup"><span data-stu-id="2b924-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="2b924-491">在中**Visual Studio 2017**，打开刚刚创建的解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="2b924-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="2b924-492">在中**解决方案平台**，选择**x86，本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="2b924-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="2b924-493">在中**解决方案配置**选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="2b924-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![第 9 章-在本地计算机上部署](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="2b924-495">您现在需要将任何包还原到你的解决方案。</span><span class="sxs-lookup"><span data-stu-id="2b924-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="2b924-496">右键单击你**解决方案**，然后单击**还原解决方案的 NuGet 包...**</span><span class="sxs-lookup"><span data-stu-id="2b924-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="2b924-497">这是因为 Unity 生成的包需要将目标设定为使用你的本地计算机的引用。</span><span class="sxs-lookup"><span data-stu-id="2b924-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="2b924-498">转到**生成菜单**，然后单击**部署解决方案**旁加载到计算机中，应用程序。</span><span class="sxs-lookup"><span data-stu-id="2b924-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="2b924-499">Visual Studio 将首先生成，然后部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="2b924-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="2b924-500">你的应用现在应出现在已安装的应用，准备好启动列表中。</span><span class="sxs-lookup"><span data-stu-id="2b924-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![第 9 章-在本地计算机上部署](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="2b924-502">当您运行混合现实应用程序后，你将在内**InsideOutSphere**应用中使用的模型。</span><span class="sxs-lookup"><span data-stu-id="2b924-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="2b924-503">将此球体将流式传输视频，提供的 360 度视图，传入的视频 （这此种类型的角度来看拍摄许可）。</span><span class="sxs-lookup"><span data-stu-id="2b924-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="2b924-504">不要过于惊讶如果视频需要几秒钟才能加载，您的应用程序受到您可用的 Internet 速度，如视频需要提取并随后下载，因此若要流式传输到您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="2b924-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="2b924-505">准备就绪后，更改场景并打开第二个视频中，通过在红色球体观望 ！</span><span class="sxs-lookup"><span data-stu-id="2b924-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="2b924-506">然后随时返回，在第二个场景中使用蓝色的多维数据集 ！</span><span class="sxs-lookup"><span data-stu-id="2b924-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="2b924-507">完成的 Azure 媒体服务应用程序</span><span class="sxs-lookup"><span data-stu-id="2b924-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="2b924-508">祝贺你，构建利用 Azure 媒体服务来将 360 视频流的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="2b924-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![实验结果](images/AzureLabs-Lab6-00.png)

![实验结果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="2b924-511">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="2b924-511">Bonus Exercises</span></span>

<span data-ttu-id="2b924-512">**练习 1**</span><span class="sxs-lookup"><span data-stu-id="2b924-512">**Exercise 1**</span></span>

<span data-ttu-id="2b924-513">它是完全有可能只使用单个场景更改本教程中的视频。</span><span class="sxs-lookup"><span data-stu-id="2b924-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="2b924-514">试着你的应用程序并使它成为一个场景 ！</span><span class="sxs-lookup"><span data-stu-id="2b924-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="2b924-515">可能是甚至另一个将视频添加到组合。</span><span class="sxs-lookup"><span data-stu-id="2b924-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="2b924-516">**练习 2**</span><span class="sxs-lookup"><span data-stu-id="2b924-516">**Exercise 2**</span></span>

<span data-ttu-id="2b924-517">尝试 Azure 和 Unity，并尝试实现应用程序以自动选择具有不同的文件大小，具体取决于 Internet 连接的强度的视频的功能。</span><span class="sxs-lookup"><span data-stu-id="2b924-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


