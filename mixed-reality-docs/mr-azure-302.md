---
title: MR 和 Azure 302-计算机视觉
description: 完成本课程，了解如何使用 Azure 计算机视觉在混合现实应用程序中识别所提供的映像中的视觉内容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，计算机视觉，hololens，沉浸，vr
ms.openlocfilehash: 9cc526afdc36b8056afd61948fea5cf98015bb35
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047197"
---
>[!NOTE]
><span data-ttu-id="8a417-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="8a417-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8a417-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="8a417-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8a417-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="8a417-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8a417-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="8a417-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8a417-108">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="8a417-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8a417-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="8a417-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="8a417-110">MR 和 Azure 302：计算机视觉</span><span class="sxs-lookup"><span data-stu-id="8a417-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="8a417-111">在本课程中，你将了解如何在混合现实应用程序中使用 Azure 计算机视觉功能识别所提供的映像中的视觉内容。</span><span class="sxs-lookup"><span data-stu-id="8a417-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="8a417-112">识别结果将显示为描述性标记。</span><span class="sxs-lookup"><span data-stu-id="8a417-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="8a417-113">您可以使用此服务，无需训练机器学习模型。</span><span class="sxs-lookup"><span data-stu-id="8a417-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="8a417-114">如果实现需要训练机器学习模型，请参阅[MR And Azure 302b](mr-azure-302b.md)。</span><span class="sxs-lookup"><span data-stu-id="8a417-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![实验室结果](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="8a417-116">Microsoft 计算机视觉是一组 Api，旨在向开发人员提供使用高级算法的图像处理和分析（使用返回信息），所有这些都来自云。</span><span class="sxs-lookup"><span data-stu-id="8a417-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="8a417-117">开发人员可上传图像或图像 URL，Microsoft 计算机视觉 API 算法将根据输入的输入来分析视觉内容，然后，该用户可以返回信息，包括标识图像的类型和质量、检测人脸（返回它们的坐标）、标记或分类图像。</span><span class="sxs-lookup"><span data-stu-id="8a417-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="8a417-118">有关详细信息，请访问[Azure 计算机视觉 API 页](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。</span><span class="sxs-lookup"><span data-stu-id="8a417-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="8a417-119">完成本课程后，你将拥有一个混合现实 HoloLens 应用程序，该应用程序将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="8a417-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="8a417-120">使用点击手势，HoloLens 的照相机将捕获图像。</span><span class="sxs-lookup"><span data-stu-id="8a417-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="8a417-121">映像将发送到 Azure 计算机视觉 API 服务。</span><span class="sxs-lookup"><span data-stu-id="8a417-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="8a417-122">识别的对象将在位于 Unity 场景中的一个简单 UI 组中列出。</span><span class="sxs-lookup"><span data-stu-id="8a417-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="8a417-123">在您的应用程序中，您将由您来决定如何将结果与您的设计相集成。</span><span class="sxs-lookup"><span data-stu-id="8a417-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="8a417-124">本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="8a417-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="8a417-125">您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。</span><span class="sxs-lookup"><span data-stu-id="8a417-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="8a417-126">设备支持</span><span class="sxs-lookup"><span data-stu-id="8a417-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8a417-127">摘要</span><span class="sxs-lookup"><span data-stu-id="8a417-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8a417-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8a417-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8a417-129"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="8a417-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="8a417-130">MR 和 Azure 302：计算机视觉</span><span class="sxs-lookup"><span data-stu-id="8a417-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="8a417-131">✔️</span><span class="sxs-lookup"><span data-stu-id="8a417-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8a417-132">✔️</span><span class="sxs-lookup"><span data-stu-id="8a417-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="8a417-133">尽管本课程主要侧重于 HoloLens，但你也可以将本课程中学习的内容应用于 Windows Mixed Reality 沉浸（VR）耳机。</span><span class="sxs-lookup"><span data-stu-id="8a417-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="8a417-134">由于沉浸式（VR）耳机没有可访问的摄像机，因此需要连接到电脑的外部照相机。</span><span class="sxs-lookup"><span data-stu-id="8a417-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="8a417-135">在本课程中，您将看到有关支持沉浸式（VR）耳机时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="8a417-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a417-136">先决条件</span><span class="sxs-lookup"><span data-stu-id="8a417-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="8a417-137">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="8a417-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="8a417-138">另外请注意，本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容（5月2018）。</span><span class="sxs-lookup"><span data-stu-id="8a417-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="8a417-139">您可以随意使用最新的软件（如[安装工具](install-the-tools.md)一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="8a417-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="8a417-140">本课程建议采用以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="8a417-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="8a417-141">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发</span><span class="sxs-lookup"><span data-stu-id="8a417-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="8a417-142">Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="8a417-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8a417-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="8a417-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8a417-144">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="8a417-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="8a417-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8a417-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="8a417-146">启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="8a417-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="8a417-147">连接到电脑的相机（适用于沉浸式耳机开发）</span><span class="sxs-lookup"><span data-stu-id="8a417-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="8a417-148">Azure 安装和计算机视觉 API 检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="8a417-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="8a417-149">开始之前</span><span class="sxs-lookup"><span data-stu-id="8a417-149">Before you start</span></span>

1.  <span data-ttu-id="8a417-150">为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。</span><span class="sxs-lookup"><span data-stu-id="8a417-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="8a417-151">设置并测试你的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="8a417-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="8a417-152">如果需要支持设置 HoloLens，请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="8a417-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="8a417-153">在开始开发新的 HoloLens 应用程序时，最好执行校准和传感器调整（有时它可以帮助为每个用户执行这些任务）。</span><span class="sxs-lookup"><span data-stu-id="8a417-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="8a417-154">有关校准的帮助信息，请单击此链接，了解[到 HoloLens 校准文章](calibration.md#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="8a417-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="8a417-155">有关传感器优化的帮助，请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="8a417-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="8a417-156">第1章-Azure 门户</span><span class="sxs-lookup"><span data-stu-id="8a417-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="8a417-157">若要在 Azure 中使用*计算机视觉 API*服务，你将需要配置服务的实例，使其可用于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8a417-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="8a417-158">首先，登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="8a417-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="8a417-159">如果还没有 Azure 帐户，则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="8a417-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="8a417-160">如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="8a417-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="8a417-161">登录后，单击左上角的 "**新建**"，搜索 "*计算机视觉 API*"，然后单击 " **Enter**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![在 Azure 中创建新资源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="8a417-163">在较新的门户中，可能已将 "**新建**" 一词替换为 "**创建资源**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="8a417-164">新页将提供*计算机视觉 API*服务的说明。</span><span class="sxs-lookup"><span data-stu-id="8a417-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="8a417-165">在此页的左下角，选择 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="8a417-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![关于计算机视觉 api 服务](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="8a417-167">单击 "**创建**" 后：</span><span class="sxs-lookup"><span data-stu-id="8a417-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="8a417-168">为此服务实例插入所需的**名称**。</span><span class="sxs-lookup"><span data-stu-id="8a417-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="8a417-169">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="8a417-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="8a417-170">选择适合你的**定价层**，如果这是第一次创建*计算机视觉 API*服务，则你应该可以使用免费层（名为 F0）。</span><span class="sxs-lookup"><span data-stu-id="8a417-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="8a417-171">选择一个**资源组**，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="8a417-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="8a417-172">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="8a417-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="8a417-173">建议将所有与单个项目关联的 Azure 服务（例如这些实验室）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="8a417-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="8a417-174">若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="8a417-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="8a417-175">确定资源组的位置（如果要创建新的资源组）。</span><span class="sxs-lookup"><span data-stu-id="8a417-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="8a417-176">此位置理想情况下会在应用程序运行所在的区域中。</span><span class="sxs-lookup"><span data-stu-id="8a417-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="8a417-177">某些 Azure 资产仅在特定区域提供。</span><span class="sxs-lookup"><span data-stu-id="8a417-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="8a417-178">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="8a417-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="8a417-179">单击 "创建"。</span><span class="sxs-lookup"><span data-stu-id="8a417-179">Click Create.</span></span>

        ![服务创建信息](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="8a417-181">单击 "**创建**" 后，需要等待创建服务，这可能需要一分钟时间。</span><span class="sxs-lookup"><span data-stu-id="8a417-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="8a417-182">创建服务实例后，门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="8a417-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![查看新服务的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="8a417-184">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="8a417-184">Click on the notification to explore your new Service instance.</span></span> 

    ![选择 "中转到资源" 按钮。](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="8a417-186">单击通知中的 "**中转到资源**" 按钮以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="8a417-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="8a417-187">你将转到新的计算机视觉 API 服务实例。</span><span class="sxs-lookup"><span data-stu-id="8a417-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![新的计算机视觉 API 服务](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="8a417-189">在本教程中，你的应用程序将需要调用你的服务，这是通过使用你的服务的订阅密钥来完成的。</span><span class="sxs-lookup"><span data-stu-id="8a417-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="8a417-190">在*计算机视觉 API*服务的 "*快速启动*" 页上，导航到第一步，*获取你的密钥*，然后单击 "**密钥**" （也可以通过单击位于 "服务" 导航菜单中的蓝色超链接项来实现此目的）。由键图标表示）。</span><span class="sxs-lookup"><span data-stu-id="8a417-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="8a417-191">这会显示你的服务*密钥*。</span><span class="sxs-lookup"><span data-stu-id="8a417-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="8a417-192">复制其中一个所显示的密钥，因为稍后会在项目中使用此密钥。</span><span class="sxs-lookup"><span data-stu-id="8a417-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="8a417-193">返回到 "*快速启动*" 页，从该处获取终结点。</span><span class="sxs-lookup"><span data-stu-id="8a417-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="8a417-194">请注意，你可能会有所不同，具体取决于你所在的区域（如果是，你将需要在以后对代码进行更改）。</span><span class="sxs-lookup"><span data-stu-id="8a417-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="8a417-195">获取此终结点的副本供以后使用：</span><span class="sxs-lookup"><span data-stu-id="8a417-195">Take a copy of this endpoint for use later:</span></span>

    ![新的计算机视觉 API 服务](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="8a417-197">可在[此处](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)检查各种终结点。</span><span class="sxs-lookup"><span data-stu-id="8a417-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="8a417-198">第2章–设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="8a417-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="8a417-199">下面是用于使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="8a417-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="8a417-200">打开*Unity* ，并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-200">Open *Unity* and click **New**.</span></span> 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="8a417-202">现在需要提供 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="8a417-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="8a417-203">插入**MR_ComputerVision**。</span><span class="sxs-lookup"><span data-stu-id="8a417-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="8a417-204">请确保 "项目类型" 设置为 " **3d**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="8a417-205">将位置设置为合适的**位置**（请记住，更接近根目录更好）。</span><span class="sxs-lookup"><span data-stu-id="8a417-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="8a417-206">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-206">Then, click **Create project**.</span></span>

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="8a417-208">当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="8a417-209">转到 "**编辑 > 首选项**"，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="8a417-210">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="8a417-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="8a417-211">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="8a417-211">Close the **Preferences** window.</span></span>

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="8a417-213">接下来，转到 "**文件 > 生成设置**"，选择 "**通用 Windows 平台**"，然后单击 "**切换平台**" 按钮以应用所选内容。</span><span class="sxs-lookup"><span data-stu-id="8a417-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![生成设置窗口，将平台切换到 UWP。](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="8a417-215">尽管仍处于**文件 > 生成设置**，但请确保：</span><span class="sxs-lookup"><span data-stu-id="8a417-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="8a417-216">**目标设备**设置为**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="8a417-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="8a417-217">对于沉浸式耳机，将 "**目标设备**" 设置为 "*任何设备*"。</span><span class="sxs-lookup"><span data-stu-id="8a417-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="8a417-218">**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="8a417-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="8a417-219">**SDK**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="8a417-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="8a417-220">**Visual Studio 版本**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="8a417-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="8a417-221">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="8a417-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="8a417-222">保存场景并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="8a417-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="8a417-223">通过选择 "**添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="8a417-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="8a417-224">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="8a417-224">A save window will appear.</span></span>
        
            ![单击 "添加打开的场景" 按钮](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="8a417-226">为此创建新文件夹，并为将来的任何场景创建一个新文件夹，然后选择 "**新建文件夹**" 按钮以创建新文件夹，将其命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="8a417-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            !["创建新脚本" 文件夹](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="8a417-228">打开新创建的**场景**文件夹，然后在 "文件名 *：文本" 字段*中，键入**MR_ComputerVisionScene**，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![为新场景指定名称。](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="8a417-230">请注意，必须将 Unity 场景保存在 "*资产*" 文件夹中，因为它们必须与 Unity 项目相关联。</span><span class="sxs-lookup"><span data-stu-id="8a417-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="8a417-231">创建场景文件夹（以及其他类似文件夹）是构造 Unity 项目的典型方式。</span><span class="sxs-lookup"><span data-stu-id="8a417-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="8a417-232">现在，"*生成设置*" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="8a417-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="8a417-233">在 "*生成设置*" 窗口中，单击 "**播放机设置**" 按钮，这会在*检查器*所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="8a417-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![打开播放机设置。](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="8a417-235">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="8a417-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="8a417-236">在 "**其他设置**" 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="8a417-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="8a417-237">**脚本运行时版本**应**稳定**（与 .net 3.5 等效）。</span><span class="sxs-lookup"><span data-stu-id="8a417-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="8a417-238">**脚本编写后端**应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="8a417-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="8a417-239">**API 兼容级别**应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="8a417-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他设置。](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="8a417-241">在 "**发布设置**" 选项卡的 "**功能**" 下，检查：</span><span class="sxs-lookup"><span data-stu-id="8a417-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="8a417-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="8a417-242">**InternetClient**</span></span>
        2. <span data-ttu-id="8a417-243">**摄像头**</span><span class="sxs-lookup"><span data-stu-id="8a417-243">**Webcam**</span></span>

            ![正在更新发布设置。](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="8a417-245">在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="8a417-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 设置。](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="8a417-247">"返回*生成设置* _" C# Unity_项目不再灰显;勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="8a417-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="8a417-248">关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="8a417-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="8a417-249">保存场景和项目（**file > SAVE 场景/file > SAVE Project**）。</span><span class="sxs-lookup"><span data-stu-id="8a417-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="8a417-250">第3章–照相机设置</span><span class="sxs-lookup"><span data-stu-id="8a417-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a417-251">如果希望跳过本课程的*Unity 设置*组件，并继续直接进入代码，可以下载[unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)，将其作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后从[第5章](#chapter-5--create-the-resultslabel-class)继续。</span><span class="sxs-lookup"><span data-stu-id="8a417-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="8a417-252">在 "*层次结构" 面板*中，选择 "**摄像机**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="8a417-253">选择后，你将能够在 "*检查器" 面板*中看到**主相机**的所有组件。</span><span class="sxs-lookup"><span data-stu-id="8a417-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="8a417-254">**照相机对象**必须命名为 "**主相机**" （请注意拼写正确！）</span><span class="sxs-lookup"><span data-stu-id="8a417-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="8a417-255">必须将主相机**标记**设置为**MainCamera** （请注意拼写！）</span><span class="sxs-lookup"><span data-stu-id="8a417-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="8a417-256">请确保将**转换位置**设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="8a417-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="8a417-257">将**清除标志**设置为**纯色**（对于沉浸式耳机，请忽略此设置）。</span><span class="sxs-lookup"><span data-stu-id="8a417-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="8a417-258">将相机组件的**背景**色设置为**黑色、Alpha 0 （十六进制代码： #00000000）** （对沉浸式耳机忽略此颜色）。</span><span class="sxs-lookup"><span data-stu-id="8a417-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![更新照相机组件。](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="8a417-260">接下来，必须创建一个附加到**主相机**的简单 "Cursor" 对象，这将帮助你在应用程序运行时定位图像分析输出。</span><span class="sxs-lookup"><span data-stu-id="8a417-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="8a417-261">此光标将确定相机焦点的中心点。</span><span class="sxs-lookup"><span data-stu-id="8a417-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="8a417-262">创建游标：</span><span class="sxs-lookup"><span data-stu-id="8a417-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="8a417-263">在 "*层次结构" 面板*中，右键单击**主相机**。</span><span class="sxs-lookup"><span data-stu-id="8a417-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="8a417-264">在 " **3D 对象**" 下，单击 "**球面**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![选择 Cursor 对象。](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="8a417-266">将**球体**重命名为**光标**（双击光标对象或按选定对象的 "F2" 键盘按钮），并确保它位于**主相机**的子项中。</span><span class="sxs-lookup"><span data-stu-id="8a417-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="8a417-267">在 "*层次结构" 面板*中，左键单击**光标**。</span><span class="sxs-lookup"><span data-stu-id="8a417-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="8a417-268">选择光标后，在 "*检查器" 面板*中调整以下变量：</span><span class="sxs-lookup"><span data-stu-id="8a417-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="8a417-269">将*转换位置*设置为**0、0、5**</span><span class="sxs-lookup"><span data-stu-id="8a417-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="8a417-270">将*刻度*设置为**0.02、0.02、0.02**</span><span class="sxs-lookup"><span data-stu-id="8a417-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![更新转换位置和缩放比例。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="8a417-272">第4章–设置标签系统</span><span class="sxs-lookup"><span data-stu-id="8a417-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="8a417-273">使用 HoloLens 相机捕获映像后，该映像将发送到*Azure 计算机视觉 API*服务实例进行分析。</span><span class="sxs-lookup"><span data-stu-id="8a417-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="8a417-274">此分析的结果将是被识别对象（称为**标记**）的列表。</span><span class="sxs-lookup"><span data-stu-id="8a417-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="8a417-275">您将使用标签（作为世界空间中的3D 文本）在拍摄照片的位置显示这些标记。</span><span class="sxs-lookup"><span data-stu-id="8a417-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="8a417-276">以下步骤将演示如何设置**标签**对象。</span><span class="sxs-lookup"><span data-stu-id="8a417-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="8a417-277">右键单击 "层次结构" 面板中的任意位置（此时位置并不重要），在 "**三维对象**" 下添加**3d 文本**。</span><span class="sxs-lookup"><span data-stu-id="8a417-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="8a417-278">将其命名为**LabelText**。</span><span class="sxs-lookup"><span data-stu-id="8a417-278">Name it **LabelText**.</span></span>

    ![创建3D 文本对象。](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="8a417-280">在 "*层次结构" 面板*中，单击**LabelText**。</span><span class="sxs-lookup"><span data-stu-id="8a417-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="8a417-281">选择**LabelText**后，在 "*检查器" 面板*中调整以下变量：</span><span class="sxs-lookup"><span data-stu-id="8a417-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="8a417-282">将**位置**设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="8a417-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="8a417-283">将**刻度**设置为**0.01、0.01、0.01**</span><span class="sxs-lookup"><span data-stu-id="8a417-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="8a417-284">在组件**文本网格**中：</span><span class="sxs-lookup"><span data-stu-id="8a417-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="8a417-285">将**文本**中的所有文本替换为 "..."</span><span class="sxs-lookup"><span data-stu-id="8a417-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="8a417-286">将**定位点**设置为**中间中心**</span><span class="sxs-lookup"><span data-stu-id="8a417-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="8a417-287">将**对齐方式**设置为**居中**</span><span class="sxs-lookup"><span data-stu-id="8a417-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="8a417-288">将**选项卡大小**设置为**4**</span><span class="sxs-lookup"><span data-stu-id="8a417-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="8a417-289">将**字体大小**设置为**50**</span><span class="sxs-lookup"><span data-stu-id="8a417-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="8a417-290">将**颜色**设置为 **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="8a417-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![文本组件](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="8a417-292">将**LabelText**从 "*层次结构" 面板*中拖到 "*资源" 文件夹*内的 "*项目" 面板*中。</span><span class="sxs-lookup"><span data-stu-id="8a417-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="8a417-293">这会将**LabelText**设置为 Prefab，以便可以在代码中对其进行实例化。</span><span class="sxs-lookup"><span data-stu-id="8a417-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![创建 LabelText 对象的 prefab。](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="8a417-295">你应从 "*层次结构" 面板*中删除**LabelText** ，以使其不会在打开场景中显示。</span><span class="sxs-lookup"><span data-stu-id="8a417-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="8a417-296">由于它现在是一个 prefab，你将从资产文件夹中的单个实例上调用，无需将其保存在场景中。</span><span class="sxs-lookup"><span data-stu-id="8a417-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="8a417-297">"*层次结构" 面板*中的最后一个对象结构应类似于下图所示：</span><span class="sxs-lookup"><span data-stu-id="8a417-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![层次结构面板的最终结构。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="8a417-299">第5章–创建 ResultsLabel 类</span><span class="sxs-lookup"><span data-stu-id="8a417-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="8a417-300">需要创建的第一个脚本是*ResultsLabel*类，该类负责以下操作：</span><span class="sxs-lookup"><span data-stu-id="8a417-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="8a417-301">在适当的世界空间中创建标签，相对于照相机的位置。</span><span class="sxs-lookup"><span data-stu-id="8a417-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="8a417-302">显示图像 Analysis 中的标记。</span><span class="sxs-lookup"><span data-stu-id="8a417-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="8a417-303">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="8a417-303">To create this class:</span></span> 

1.  <span data-ttu-id="8a417-304">右键单击 "*项目" 面板*，然后**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="8a417-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="8a417-305">命名文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="8a417-305">Name the folder **Scripts**.</span></span> 

    ![创建脚本文件夹。](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="8a417-307">在 "**脚本**" 文件夹中，双击以打开。</span><span class="sxs-lookup"><span data-stu-id="8a417-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="8a417-308">在该文件夹中，右键单击，然后选择 "**创建 >** 然后**C#** 选择" 脚本 "。</span><span class="sxs-lookup"><span data-stu-id="8a417-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="8a417-309">将脚本命名为*ResultsLabel*。</span><span class="sxs-lookup"><span data-stu-id="8a417-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="8a417-310">双击新的*ResultsLabel*脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="8a417-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="8a417-311">在类中，在*ResultsLabel*类中插入以下代码：</span><span class="sxs-lookup"><span data-stu-id="8a417-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="8a417-312">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="8a417-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="8a417-313">返回*Unity 编辑器*，单击 "**脚本**" 文件夹中的*ResultsLabel*类并将其拖到 "*层次结构" 面板*中的**主相机**对象。</span><span class="sxs-lookup"><span data-stu-id="8a417-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="8a417-314">单击**主摄像机**，查看*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="8a417-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="8a417-315">你会注意到，从刚才拖到摄像机的脚本中，有两个字段：**光标**和**标签 Prefab**。</span><span class="sxs-lookup"><span data-stu-id="8a417-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="8a417-316">将名为**cursor**的对象从 "*层次结构" 面板*拖动到名为 " **cursor**" 的槽中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8a417-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="8a417-317">将名为**LabelText**的对象从 "*项目" 面板*中的 "*资产" 文件夹*拖到名为**Label Prefab**的槽中，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8a417-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![在 Unity 中设置引用目标。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="8a417-319">第6章–创建 ImageCapture 类</span><span class="sxs-lookup"><span data-stu-id="8a417-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="8a417-320">要创建的下一个类是*ImageCapture*类。</span><span class="sxs-lookup"><span data-stu-id="8a417-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="8a417-321">此类负责：</span><span class="sxs-lookup"><span data-stu-id="8a417-321">This class is responsible for:</span></span>

-   <span data-ttu-id="8a417-322">使用 HoloLens 相机捕获映像，并将其存储在 App 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8a417-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="8a417-323">正在捕获用户的点击手势。</span><span class="sxs-lookup"><span data-stu-id="8a417-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="8a417-324">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="8a417-324">To create this class:</span></span> 

1.  <span data-ttu-id="8a417-325">中转到前面创建的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="8a417-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="8a417-326">右键单击文件夹内部，**创建 > C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="8a417-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="8a417-327">调用脚本*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="8a417-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="8a417-328">双击新的*ImageCapture*脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="8a417-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="8a417-329">将以下命名空间添加到文件顶部：</span><span class="sxs-lookup"><span data-stu-id="8a417-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="8a417-330">然后，将以下变量添加到*ImageCapture*类中的*Start （）* 方法之上：</span><span class="sxs-lookup"><span data-stu-id="8a417-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="8a417-331">**TapsCount**变量将存储从用户捕获的攻丝手势的数目。</span><span class="sxs-lookup"><span data-stu-id="8a417-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="8a417-332">此编号用于捕获的映像的命名。</span><span class="sxs-lookup"><span data-stu-id="8a417-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="8a417-333">现在需要添加*唤醒（）* 和*Start （）* 方法的代码。</span><span class="sxs-lookup"><span data-stu-id="8a417-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="8a417-334">当类初始化时，将调用以下内容：</span><span class="sxs-lookup"><span data-stu-id="8a417-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="8a417-335">实现一个处理程序，该处理程序将在出现分流手势时调用。</span><span class="sxs-lookup"><span data-stu-id="8a417-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="8a417-336">*TapHandler （）* 方法会递增从用户捕获的点击次数，并使用当前光标位置确定新标签的位置。</span><span class="sxs-lookup"><span data-stu-id="8a417-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="8a417-337">然后，此方法会调用*ExecuteImageCaptureAndAnalysis （）* 方法来开始此应用程序的核心功能。</span><span class="sxs-lookup"><span data-stu-id="8a417-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="8a417-338">捕获并存储映像后，将调用以下处理程序。</span><span class="sxs-lookup"><span data-stu-id="8a417-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="8a417-339">如果该过程成功，则会将结果传递给要分析的*VisionManager* （尚未创建）。</span><span class="sxs-lookup"><span data-stu-id="8a417-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="8a417-340">然后添加应用程序用于启动映像捕获进程并存储映像的方法。</span><span class="sxs-lookup"><span data-stu-id="8a417-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="8a417-341">此时，你会注意到在*Unity 编辑器控制台面板*中出现错误。</span><span class="sxs-lookup"><span data-stu-id="8a417-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="8a417-342">这是因为代码引用了将在下一章中创建的*VisionManager*类。</span><span class="sxs-lookup"><span data-stu-id="8a417-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="8a417-343">第7章–调用 Azure 和映像分析</span><span class="sxs-lookup"><span data-stu-id="8a417-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="8a417-344">需要创建的最后一个脚本是*VisionManager*类。</span><span class="sxs-lookup"><span data-stu-id="8a417-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="8a417-345">此类负责：</span><span class="sxs-lookup"><span data-stu-id="8a417-345">This class is responsible for:</span></span>

-   <span data-ttu-id="8a417-346">加载作为字节数组捕获的最新映像。</span><span class="sxs-lookup"><span data-stu-id="8a417-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="8a417-347">将字节数组发送给*Azure 计算机视觉 API*服务实例进行分析。</span><span class="sxs-lookup"><span data-stu-id="8a417-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="8a417-348">接收 JSON 字符串形式的响应。</span><span class="sxs-lookup"><span data-stu-id="8a417-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="8a417-349">反序列化响应并将生成的标记传递给*ResultsLabel*类。</span><span class="sxs-lookup"><span data-stu-id="8a417-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="8a417-350">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="8a417-350">To create this class:</span></span>

1.  <span data-ttu-id="8a417-351">双击 "**脚本**" 文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="8a417-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="8a417-352">右键单击 "**脚本**" 文件夹中，单击 "**创建C# > 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="8a417-353">将脚本命名为*VisionManager*。</span><span class="sxs-lookup"><span data-stu-id="8a417-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="8a417-354">双击新脚本以通过 Visual Studio 打开它。</span><span class="sxs-lookup"><span data-stu-id="8a417-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="8a417-355">在*VisionManager*类的顶部，将命名空间更新为与以下相同：</span><span class="sxs-lookup"><span data-stu-id="8a417-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="8a417-356">在脚本的顶部，在*VisionManager*类（位于*Start （）* 方法的上面 *）中，* 现在需要创建两个*类*来表示来自 Azure 的反序列化 JSON 响应：</span><span class="sxs-lookup"><span data-stu-id="8a417-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="8a417-357">*TagData*和*AnalysedObject*类需要添加 *[system.exception]* 特性，然后才能使用 Unity 库反序列化声明。</span><span class="sxs-lookup"><span data-stu-id="8a417-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="8a417-358">在 VisionManager 类中，应添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="8a417-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="8a417-359">请确保将**身份验证密钥**插入到**authorizationKey**变量。</span><span class="sxs-lookup"><span data-stu-id="8a417-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="8a417-360">你将在本课程开头注明**身份验证密钥**，[第1章](#chapter-1--the-azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="8a417-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="8a417-361">**VisionAnalysisEndpoint**变量可能不同于在此示例中指定的变量。</span><span class="sxs-lookup"><span data-stu-id="8a417-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="8a417-362">"**美国西部**" 严格指为 "美国西部" 区域创建的服务实例。</span><span class="sxs-lookup"><span data-stu-id="8a417-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="8a417-363">用[终结点 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)更新此值;下面是一些可能的示例：</span><span class="sxs-lookup"><span data-stu-id="8a417-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="8a417-364">西欧：`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="8a417-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="8a417-365">东南亚：`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="8a417-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="8a417-366">澳大利亚东部：`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="8a417-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="8a417-367">现在需要添加用于唤醒的代码。</span><span class="sxs-lookup"><span data-stu-id="8a417-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="8a417-368">接下来，添加协同程序（使用其下面的静态流方法），该方法将获取*ImageCapture*类捕获的映像的分析结果。</span><span class="sxs-lookup"><span data-stu-id="8a417-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="8a417-369">在返回到*Unity*之前，请务必保存*Visual Studio*中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="8a417-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="8a417-370">返回 Unity 编辑器，单击 "**脚本**" 文件夹中的*VisionManager*和*ImageCapture*类，然后将其拖到*层次结构面板*中的**主相机**对象。</span><span class="sxs-lookup"><span data-stu-id="8a417-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="8a417-371">第8章–生成之前</span><span class="sxs-lookup"><span data-stu-id="8a417-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="8a417-372">若要对应用程序进行全面测试，需要将其旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="8a417-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="8a417-373">在执行此操作之前，请确保：</span><span class="sxs-lookup"><span data-stu-id="8a417-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="8a417-374">[第2章](#chapter-2--set-up-the-unity-project)中提到的所有设置都已正确设置。</span><span class="sxs-lookup"><span data-stu-id="8a417-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="8a417-375">所有脚本都附加到**相机**对象上。</span><span class="sxs-lookup"><span data-stu-id="8a417-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="8a417-376">*主相机检查器面板*中的所有字段均已正确分配。</span><span class="sxs-lookup"><span data-stu-id="8a417-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="8a417-377">请确保将**身份验证密钥**插入到**authorizationKey**变量。</span><span class="sxs-lookup"><span data-stu-id="8a417-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="8a417-378">确保你还在*VisionManager*脚本中检查了你的终结点，并且它与*你*的区域保持一致（本文档默认使用*美国西部*）。</span><span class="sxs-lookup"><span data-stu-id="8a417-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="8a417-379">第9章–构建 UWP 解决方案并旁加载应用程序</span><span class="sxs-lookup"><span data-stu-id="8a417-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="8a417-380">此项目的 Unity 部分所需的所有内容现在均已完成，因此可以从 Unity 构建它。</span><span class="sxs-lookup"><span data-stu-id="8a417-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="8a417-381">导航到 "*生成设置* - "**文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="8a417-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="8a417-382">在*生成设置*窗口中，单击 "**生成**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-382">From the *Build Settings* window, click **Build**.</span></span>

    ![从 Unity 生成应用](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="8a417-384">如果尚未这样做，请勾选**Unity C#项目**。</span><span class="sxs-lookup"><span data-stu-id="8a417-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="8a417-385">单击“生成”。</span><span class="sxs-lookup"><span data-stu-id="8a417-385">Click **Build**.</span></span> <span data-ttu-id="8a417-386">Unity 将启动*文件资源管理器*窗口，在该窗口中，需要创建一个文件夹，然后选择要在其中生成应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="8a417-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="8a417-387">立即创建该文件夹并将其命名为*应用*。</span><span class="sxs-lookup"><span data-stu-id="8a417-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="8a417-388">选择*应用*文件夹后，按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="8a417-389">Unity 将开始向*应用*文件夹生成项目。</span><span class="sxs-lookup"><span data-stu-id="8a417-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="8a417-390">Unity 完成生成（可能需要一些时间）后，它会在生成的位置打开 "*文件资源管理器*" 窗口（检查任务栏，因为它可能不会始终出现在窗口之上，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="8a417-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="8a417-391">第10章–部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="8a417-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="8a417-392">在 HoloLens 上部署：</span><span class="sxs-lookup"><span data-stu-id="8a417-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="8a417-393">你将需要 HoloLens 的 IP 地址（用于远程部署），并确保你的 HoloLens 处于**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="8a417-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="8a417-394">为此，请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="8a417-394">To do this:</span></span>

    1. <span data-ttu-id="8a417-395">在戴上 HoloLens 的同时，请打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="8a417-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="8a417-396">中转到**网络 & Internet > wi-fi > 高级选项**</span><span class="sxs-lookup"><span data-stu-id="8a417-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="8a417-397">记下**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="8a417-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="8a417-398">接下来，导航回 "**设置**"，然后为**开发人员更新 & Security >**</span><span class="sxs-lookup"><span data-stu-id="8a417-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="8a417-399">设置开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="8a417-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="8a417-400">导航到新的 Unity 生成（*应用*文件夹），并在*Visual Studio*中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="8a417-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="8a417-401">在解决方案配置中，选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="8a417-402">在解决方案平台中，选择 " **x86**，**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="8a417-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="8a417-404">请在 "**生成" 菜单**中，单击 "**部署解决方案**"，将应用程序旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="8a417-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="8a417-405">应用现在应显示在你的 HoloLens 上已安装的应用列表中，可以启动了！</span><span class="sxs-lookup"><span data-stu-id="8a417-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="8a417-406">若要部署到沉浸式耳机，请将 "**解决方案平台**" 设置为 "*本地计算机*"，并将**配置**设置为 "*调试*"，将 " *x86* " 设置为**平台**。</span><span class="sxs-lookup"><span data-stu-id="8a417-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="8a417-407">然后，使用 "**生成" 菜单**选择 "*部署解决方案*"，将部署到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="8a417-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="8a417-408">已完成的计算机视觉 API 应用程序</span><span class="sxs-lookup"><span data-stu-id="8a417-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="8a417-409">恭喜，你构建了一个使用 Azure 计算机视觉 API 来识别真实世界对象的混合现实应用，并清楚地显示了所见的内容。</span><span class="sxs-lookup"><span data-stu-id="8a417-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![实验室结果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="8a417-411">额外练习</span><span class="sxs-lookup"><span data-stu-id="8a417-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="8a417-412">练习1</span><span class="sxs-lookup"><span data-stu-id="8a417-412">Exercise 1</span></span>

<span data-ttu-id="8a417-413">正如使用*标记*参数（在*VisionManager*中使用的*终结点*中的出现），扩展应用程序以检测其他信息;查看你可以[访问的其他参数。](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)</span><span class="sxs-lookup"><span data-stu-id="8a417-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="8a417-414">练习2</span><span class="sxs-lookup"><span data-stu-id="8a417-414">Exercise 2</span></span>

<span data-ttu-id="8a417-415">显示返回的 Azure 数据，其显示方式更多，而且可能会隐藏数字。</span><span class="sxs-lookup"><span data-stu-id="8a417-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="8a417-416">如机器人可能对用户讲话。</span><span class="sxs-lookup"><span data-stu-id="8a417-416">As though a bot might be speaking to the user.</span></span>
