---
title: MR 和 Azure 304-人脸识别
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 混合现实, 学院, unity, 教程, api, 人脸识别, hololens, 沉浸, vr
ms.openlocfilehash: 7cd2a6683c80279129934c619a9b9cb857badf67
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047186"
---
>[!NOTE]
><span data-ttu-id="914ee-104">混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="914ee-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="914ee-105">因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="914ee-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="914ee-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="914ee-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="914ee-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="914ee-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="914ee-108">将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="914ee-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="914ee-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="914ee-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="914ee-110">MR 和 Azure 304:人脸识别</span><span class="sxs-lookup"><span data-stu-id="914ee-110">MR and Azure 304: Face recognition</span></span>

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="914ee-112">在本课程中, 你将了解如何使用 Azure 认知服务和 Microsoft 人脸 API 将人脸识别功能添加到混合现实应用程序中。</span><span class="sxs-lookup"><span data-stu-id="914ee-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="914ee-113">*Azure 人脸 API*是一项 Microsoft 服务, 它为开发人员提供了最先进的面部算法, 一切都在云中。</span><span class="sxs-lookup"><span data-stu-id="914ee-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="914ee-114">该*人脸 API*有两个主要功能: 具有属性的面部检测和人脸识别。</span><span class="sxs-lookup"><span data-stu-id="914ee-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="914ee-115">这使开发人员可以简单地设置一组人脸, 然后在以后将查询图像发送到该服务, 以确定人脸属于哪个组。</span><span class="sxs-lookup"><span data-stu-id="914ee-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="914ee-116">有关详细信息, 请访问[Azure 面部识别页](https://azure.microsoft.com/services/cognitive-services/face/)。</span><span class="sxs-lookup"><span data-stu-id="914ee-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="914ee-117">完成本课程后, 你将拥有一个混合现实 HoloLens 应用程序, 该应用程序将能够执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="914ee-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="914ee-118">使用 "**点击" 笔势**来启动使用板载 HoloLens 相机捕获映像。</span><span class="sxs-lookup"><span data-stu-id="914ee-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="914ee-119">将捕获的映像发送到*Azure 人脸 API*服务。</span><span class="sxs-lookup"><span data-stu-id="914ee-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="914ee-120">接收*人脸 API*算法的结果。</span><span class="sxs-lookup"><span data-stu-id="914ee-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="914ee-121">使用简单的用户界面, 显示匹配人员的名称。</span><span class="sxs-lookup"><span data-stu-id="914ee-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="914ee-122">这会教你如何将人脸 API 服务的结果获取到基于 Unity 的混合现实应用程序中。</span><span class="sxs-lookup"><span data-stu-id="914ee-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="914ee-123">在您的应用程序中, 您将由您来决定如何将结果与您的设计相集成。</span><span class="sxs-lookup"><span data-stu-id="914ee-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="914ee-124">本课程旨在向您介绍如何将 Azure 服务与 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="914ee-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="914ee-125">您可以使用您在本课程中获得的知识来增强混合现实应用程序的工作。</span><span class="sxs-lookup"><span data-stu-id="914ee-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="914ee-126">设备支持</span><span class="sxs-lookup"><span data-stu-id="914ee-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="914ee-127">摘要</span><span class="sxs-lookup"><span data-stu-id="914ee-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="914ee-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="914ee-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="914ee-129"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="914ee-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="914ee-130">MR 和 Azure 304:人脸识别</span><span class="sxs-lookup"><span data-stu-id="914ee-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="914ee-131">✔️</span><span class="sxs-lookup"><span data-stu-id="914ee-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="914ee-132">✔️</span><span class="sxs-lookup"><span data-stu-id="914ee-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="914ee-133">尽管本课程主要侧重于 HoloLens, 但你也可以将本课程中学习的内容应用于 Windows Mixed Reality 沉浸 (VR) 耳机。</span><span class="sxs-lookup"><span data-stu-id="914ee-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="914ee-134">由于沉浸式 (VR) 耳机没有可访问的摄像机, 因此需要连接到电脑的外部照相机。</span><span class="sxs-lookup"><span data-stu-id="914ee-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="914ee-135">在本课程中, 您将看到有关支持沉浸式 (VR) 耳机时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="914ee-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="914ee-136">先决条件</span><span class="sxs-lookup"><span data-stu-id="914ee-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="914ee-137">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="914ee-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="914ee-138">另外请注意, 本文档中的先决条件和书面说明表明了在编写时已测试和验证的内容 (5 月 2018)。</span><span class="sxs-lookup"><span data-stu-id="914ee-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="914ee-139">您可以随意使用最新的软件 (如[安装工具](install-the-tools.md)一文中所述), 但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="914ee-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="914ee-140">本课程建议采用以下硬件和软件:</span><span class="sxs-lookup"><span data-stu-id="914ee-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="914ee-141">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC, 用于沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="914ee-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="914ee-142">Windows 10 秋季创意者更新 (或更高版本) 已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="914ee-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="914ee-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="914ee-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="914ee-144">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="914ee-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="914ee-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="914ee-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="914ee-146">启用了开发人员模式的[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="914ee-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="914ee-147">连接到电脑的相机 (适用于沉浸式耳机开发)</span><span class="sxs-lookup"><span data-stu-id="914ee-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="914ee-148">Azure 安装和人脸 API 检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="914ee-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="914ee-149">开始之前</span><span class="sxs-lookup"><span data-stu-id="914ee-149">Before you start</span></span>

1.  <span data-ttu-id="914ee-150">为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。</span><span class="sxs-lookup"><span data-stu-id="914ee-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="914ee-151">设置并测试你的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="914ee-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="914ee-152">如果需要支持设置 HoloLens, 请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="914ee-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="914ee-153">在开始开发新的 HoloLens 应用程序时, 最好执行校准和传感器调整 (有时它可以帮助为每个用户执行这些任务)。</span><span class="sxs-lookup"><span data-stu-id="914ee-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="914ee-154">有关校准的帮助信息, 请单击此链接, 了解[到 HoloLens 校准文章](calibration.md#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="914ee-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="914ee-155">有关传感器优化的帮助, 请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="914ee-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="914ee-156">第1章-Azure 门户</span><span class="sxs-lookup"><span data-stu-id="914ee-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="914ee-157">若要在 Azure 中使用*人脸 API*服务, 你将需要配置服务的实例, 使其可用于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="914ee-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="914ee-158">首先, 登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="914ee-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="914ee-159">如果还没有 Azure 帐户, 则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="914ee-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="914ee-160">如果在课堂或实验室中按照本教程进行学习, 请咨询教师或 proctors, 以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="914ee-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="914ee-161">登录后, 单击左上角的 "**新建**", 然后搜索 "*人脸 API*", 按**enter**。</span><span class="sxs-lookup"><span data-stu-id="914ee-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![搜索人脸 api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="914ee-163">在较新的门户中, 可能已将 "**新建**" 一词替换为 "**创建资源**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="914ee-164">新页将提供*人脸 API*服务的说明。</span><span class="sxs-lookup"><span data-stu-id="914ee-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="914ee-165">在此提示符下, 选择 "**创建**" 按钮以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="914ee-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![人脸 api 信息](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="914ee-167">单击 "**创建**" 后:</span><span class="sxs-lookup"><span data-stu-id="914ee-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="914ee-168">为此服务实例插入所需的名称。</span><span class="sxs-lookup"><span data-stu-id="914ee-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="914ee-169">选择订阅。</span><span class="sxs-lookup"><span data-stu-id="914ee-169">Select a subscription.</span></span>

    3. <span data-ttu-id="914ee-170">选择适合你的定价层, 如果这是第一次创建*人脸 API 服务*, 则你应该可以使用免费层 (名为 F0)。</span><span class="sxs-lookup"><span data-stu-id="914ee-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="914ee-171">选择一个**资源组**, 或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="914ee-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="914ee-172">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="914ee-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="914ee-173">建议将所有与单个项目关联的 Azure 服务 (例如这些实验室) 保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="914ee-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="914ee-174">若要了解有关 Azure 资源组的详细信息, 请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="914ee-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="914ee-175">你稍后使用的 UWP 应用 (**人员 Maker**) 要求使用 "美国西部" 作为位置。</span><span class="sxs-lookup"><span data-stu-id="914ee-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="914ee-176">还需要确认是否已了解应用于此服务的条款和条件。</span><span class="sxs-lookup"><span data-stu-id="914ee-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="914ee-177">选择**创建\*。**</span><span class="sxs-lookup"><span data-stu-id="914ee-177">Select **Create\*.**</span></span>

        ![创建人脸 api 服务](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="914ee-179">一旦你单击 **创建**\* 必须要等待的时间来创建服务，这可能需要一分钟的时间。</span><span class="sxs-lookup"><span data-stu-id="914ee-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="914ee-180">创建服务实例后, 门户中将显示一个通知。</span><span class="sxs-lookup"><span data-stu-id="914ee-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![服务创建通知](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="914ee-182">单击通知以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="914ee-182">Click on the notifications to explore your new Service instance.</span></span>

    ![中转到资源通知](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="914ee-184">准备就绪后, 请单击通知中的 "**中转到资源**" 按钮, 以浏览新服务实例。</span><span class="sxs-lookup"><span data-stu-id="914ee-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![访问人脸 api 密钥](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="914ee-186">在本教程中, 你的应用程序将需要调用你的服务, 这是通过使用你的服务的订阅 "密钥" 来完成的。</span><span class="sxs-lookup"><span data-stu-id="914ee-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="914ee-187">从 "*人脸 API*服务" 的 "*快速启动*" 页中, 第一个点为数字 1, 以*获取密钥。*</span><span class="sxs-lookup"><span data-stu-id="914ee-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="914ee-188">在 "*服务*" 页上, 选择 "蓝色**键**" 超链接 (如果在 "快速启动" 页上), 或选择 "服务" 导航菜单中的 "**密钥**" 链接 (位于左侧, 由 "密钥" 图标表示), 以显示你的密钥。</span><span class="sxs-lookup"><span data-stu-id="914ee-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="914ee-189">记下其中一个密钥并对其进行保护, 因为稍后需要用到它。</span><span class="sxs-lookup"><span data-stu-id="914ee-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="914ee-190">第2章-使用 "人员 Maker" UWP 应用程序</span><span class="sxs-lookup"><span data-stu-id="914ee-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="914ee-191">请确保下载名为[Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)的预生成的 UWP 应用程序。</span><span class="sxs-lookup"><span data-stu-id="914ee-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="914ee-192">此应用并不是本课程的最终产品, 只是一种工具, 可帮助你创建 Azure 条目, 后面的项目将依赖于这些条目。</span><span class="sxs-lookup"><span data-stu-id="914ee-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="914ee-193">**人员制造商**允许您创建与人员和人员组相关联的 Azure 条目。</span><span class="sxs-lookup"><span data-stu-id="914ee-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="914ee-194">应用程序会将所需的所有信息以一种格式放置在以后由 FaceAPI 使用的格式, 以便识别已添加的人员的人脸。</span><span class="sxs-lookup"><span data-stu-id="914ee-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="914ee-195">无关紧要**人员 Maker**使用一些基本限制, 以帮助确保没有超过**免费订阅层**每分钟的服务调用数。</span><span class="sxs-lookup"><span data-stu-id="914ee-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="914ee-196">当发生限制时, 顶部的绿色文本将更改为红色, 并更新为 "活动"。如果是这种情况, 只需等待应用程序 (它将等待, 直到接下来可以继续访问面部服务, 并在可以再次使用它时将其更新为 "活动中"。</span><span class="sxs-lookup"><span data-stu-id="914ee-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="914ee-197">此应用程序使用*microsoft.projectoxford.face*库, 可让你充分利用人脸 API。</span><span class="sxs-lookup"><span data-stu-id="914ee-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="914ee-198">此库以 NuGet 包的形式提供。</span><span class="sxs-lookup"><span data-stu-id="914ee-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="914ee-199">有关此情况的详细信息以及类似的 Api, 请[确保访问 api 参考文章](https://docs.microsoft.com/azure/cognitive-services/face/apireference)。</span><span class="sxs-lookup"><span data-stu-id="914ee-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="914ee-200">这些只是所需的步骤, 有关如何执行这些操作的说明, 请查看该文档。</span><span class="sxs-lookup"><span data-stu-id="914ee-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="914ee-201">**人员 Maker**应用允许你:</span><span class="sxs-lookup"><span data-stu-id="914ee-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="914ee-202">创建一个*用户组*, 该组由要与之关联的多个用户组成。</span><span class="sxs-lookup"><span data-stu-id="914ee-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="914ee-203">利用 Azure 帐户, 可以托管多个人员组。</span><span class="sxs-lookup"><span data-stu-id="914ee-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="914ee-204">创建作为人员组成员的*人员*。</span><span class="sxs-lookup"><span data-stu-id="914ee-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="914ee-205">每个人都有多个与之关联的人*脸*图像。</span><span class="sxs-lookup"><span data-stu-id="914ee-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="914ee-206">将人*脸图像*分配给某个*人*, 使 Azure 人脸 API 服务能够按相应的人*脸*识别该*人*。</span><span class="sxs-lookup"><span data-stu-id="914ee-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="914ee-207">*训练* *Azure 人脸 API 服务*。</span><span class="sxs-lookup"><span data-stu-id="914ee-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="914ee-208">请注意, 若要训练此应用以识别用户, 你需要将每个用户的 10 (10) 张近照片照片添加到你的人员组。</span><span class="sxs-lookup"><span data-stu-id="914ee-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="914ee-209">Windows 10 Cam 应用可帮助你获取这些信息。</span><span class="sxs-lookup"><span data-stu-id="914ee-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="914ee-210">您必须确保每张照片清晰 (避免模糊、遮蔽, 或远离使用者), 将照片设置为 jpg 或 png 文件格式, 图像文件大小不能超过**4 MB**, 且不能小于**1 KB**。</span><span class="sxs-lookup"><span data-stu-id="914ee-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="914ee-211">如果按照本教程进行操作, 请不要使用自己的人脸进行定型, 因为当你将 HoloLens 投入使用时, 你将无法亲自寻找。</span><span class="sxs-lookup"><span data-stu-id="914ee-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="914ee-212">使用同事或学生。</span><span class="sxs-lookup"><span data-stu-id="914ee-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="914ee-213">正在运行**人员制造商**:</span><span class="sxs-lookup"><span data-stu-id="914ee-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="914ee-214">打开**PersonMaker**文件夹, 然后双击*PersonMaker 解决方案*以通过*Visual Studio*打开它。</span><span class="sxs-lookup"><span data-stu-id="914ee-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="914ee-215">*PersonMaker 解决方案*打开后, 请确保:</span><span class="sxs-lookup"><span data-stu-id="914ee-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="914ee-216">*解决方案配置*设置为 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="914ee-217">*解决方案平台*设置为**x86**</span><span class="sxs-lookup"><span data-stu-id="914ee-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="914ee-218">*目标平台*为**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="914ee-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="914ee-219">你还可能需要*还原 NuGet 包*(右键单击*解决方案*并选择 "**还原 NuGet 包**")。</span><span class="sxs-lookup"><span data-stu-id="914ee-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="914ee-220">单击 "*本地计算机*", 应用程序将启动。</span><span class="sxs-lookup"><span data-stu-id="914ee-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="914ee-221">请注意, 在较小屏幕上, 所有内容可能都不可见, 不过您可以向下滚动查看。</span><span class="sxs-lookup"><span data-stu-id="914ee-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![人员制造商用户界面](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="914ee-223">从 Azure 中的*人脸 API*服务插入你应该具有的**Azure 身份验证密钥**。</span><span class="sxs-lookup"><span data-stu-id="914ee-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="914ee-224">&</span><span class="sxs-lookup"><span data-stu-id="914ee-224">Insert:</span></span>

    1. <span data-ttu-id="914ee-225">要分配给*人员组*的*ID* 。</span><span class="sxs-lookup"><span data-stu-id="914ee-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="914ee-226">ID 必须是小写, 且不能包含空格。</span><span class="sxs-lookup"><span data-stu-id="914ee-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="914ee-227">记下此 ID, 因为稍后会在 Unity 项目中需要它。</span><span class="sxs-lookup"><span data-stu-id="914ee-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="914ee-228">要分配给*人员组*的*名称*(可以有空格)。</span><span class="sxs-lookup"><span data-stu-id="914ee-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="914ee-229">按 "**创建人员组**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="914ee-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="914ee-230">此按钮下应显示一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="914ee-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="914ee-231">如果出现 "拒绝访问" 错误, 请检查为 Azure 服务设置的位置。</span><span class="sxs-lookup"><span data-stu-id="914ee-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="914ee-232">如上所述, 此应用程序是为 "美国西部" 设计的。</span><span class="sxs-lookup"><span data-stu-id="914ee-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="914ee-233">你会注意到, 你也可以单击 "**提取已知组**" 按钮: 这适用于你是否已创建人员组, 而不是创建新人员组。</span><span class="sxs-lookup"><span data-stu-id="914ee-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="914ee-234">请注意, 如果单击 "创建具有已知组的*人员组*", 则还会提取组。</span><span class="sxs-lookup"><span data-stu-id="914ee-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="914ee-235">插入要创建的*人员*的*名称*。</span><span class="sxs-lookup"><span data-stu-id="914ee-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="914ee-236">单击 "**创建人员**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="914ee-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="914ee-237">此按钮下应显示一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="914ee-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="914ee-238">如果要删除先前创建的用户, 可以将该名称写入 textbox 并按**Delete person**</span><span class="sxs-lookup"><span data-stu-id="914ee-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="914ee-239">请确保知道要添加到组中的用户的 10 (10) 个照片的位置。</span><span class="sxs-lookup"><span data-stu-id="914ee-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="914ee-240">按 "**创建并打开文件夹**", 打开 Windows 资源管理器, 使其与该人员关联。</span><span class="sxs-lookup"><span data-stu-id="914ee-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="914ee-241">在文件夹中添加十 (10) 个图像。</span><span class="sxs-lookup"><span data-stu-id="914ee-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="914ee-242">它们必须是*JPG*或*PNG*文件格式。</span><span class="sxs-lookup"><span data-stu-id="914ee-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="914ee-243">单击 "**提交到 Azure**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="914ee-244">计数器将显示提交状态, 后跟消息完成后的消息。</span><span class="sxs-lookup"><span data-stu-id="914ee-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="914ee-245">计数器完成并显示一条确认消息后, 单击 "**训练**" 以训练你的服务。</span><span class="sxs-lookup"><span data-stu-id="914ee-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="914ee-246">完成此过程后, 就可以开始迁移到 Unity。</span><span class="sxs-lookup"><span data-stu-id="914ee-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="914ee-247">第3章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="914ee-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="914ee-248">下面是用于使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="914ee-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="914ee-249">打开*Unity* , 并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-249">Open *Unity* and click **New**.</span></span> 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="914ee-251">现在需要提供 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="914ee-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="914ee-252">插入**MR_FaceRecognition**。</span><span class="sxs-lookup"><span data-stu-id="914ee-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="914ee-253">请确保 "项目类型" 设置为 " **3d**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="914ee-254">将位置设置为合适的**位置**(请记住, 更接近根目录更好)。</span><span class="sxs-lookup"><span data-stu-id="914ee-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="914ee-255">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-255">Then, click **Create project**.</span></span>

    ![提供新 Unity 项目的详细信息。](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="914ee-257">当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="914ee-258">转到 "**编辑 > 首选项**", 然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="914ee-259">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="914ee-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="914ee-260">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="914ee-260">Close the **Preferences** window.</span></span>

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="914ee-262">接下来, 通过单击 "**切换平台**" 按钮转到 "**文件 > 生成设置**", 并将平台切换到**通用 Windows 平台**。</span><span class="sxs-lookup"><span data-stu-id="914ee-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![生成设置窗口, 将平台切换到 UWP。](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="914ee-264">请参阅**文件 > 生成设置**, 并确保:</span><span class="sxs-lookup"><span data-stu-id="914ee-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="914ee-265">**目标设备**设置为**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="914ee-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="914ee-266">对于沉浸式耳机, 将 "**目标设备**" 设置为 "*任何设备*"。</span><span class="sxs-lookup"><span data-stu-id="914ee-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="914ee-267">**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="914ee-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="914ee-268">**SDK**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="914ee-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="914ee-269">**Visual Studio 版本**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="914ee-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="914ee-270">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="914ee-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="914ee-271">保存场景并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="914ee-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="914ee-272">通过选择 "**添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="914ee-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="914ee-273">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="914ee-273">A save window will appear.</span></span>

            ![单击 "添加打开的场景" 按钮](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="914ee-275">选择 "**新建文件夹**" 按钮, 创建一个新文件夹, 将其命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="914ee-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            !["创建新脚本" 文件夹](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="914ee-277">打开新创建的**场景**文件夹, 然后在 "文件名: 文本" 字段中, 键入**FaceRecScene**, 然后按 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![为新场景指定名称。](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="914ee-279">现在, "*生成设置*" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="914ee-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="914ee-280">在 "*生成设置*" 窗口中, 单击 "**播放机设置**" 按钮, 这会在*检查器*所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="914ee-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![打开播放机设置。](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="914ee-282">在此面板中, 需要验证几项设置:</span><span class="sxs-lookup"><span data-stu-id="914ee-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="914ee-283">在 "**其他设置**" 选项卡中:</span><span class="sxs-lookup"><span data-stu-id="914ee-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="914ee-284">**脚本编写** **运行时版本**应**实验**（.NET 4.6 等效）。</span><span class="sxs-lookup"><span data-stu-id="914ee-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="914ee-285">更改此将触发需要重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="914ee-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="914ee-286">**脚本编写后端**应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="914ee-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="914ee-287">**API 兼容级别**应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="914ee-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他设置。](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="914ee-289">在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:</span><span class="sxs-lookup"><span data-stu-id="914ee-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="914ee-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="914ee-290">**InternetClient**</span></span>
        - <span data-ttu-id="914ee-291">**摄像头**</span><span class="sxs-lookup"><span data-stu-id="914ee-291">**Webcam**</span></span>

            ![正在更新发布设置。](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="914ee-293">在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 在 "**支持的虚拟现实**" 下, 确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="914ee-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新 X R 设置。](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="914ee-295">返回*生成设置*, **Unity C#项目**不再灰显;勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="914ee-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="914ee-296">关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="914ee-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="914ee-297">保存场景和项目 (**file > SAVE 场景/file > SAVE Project**)。</span><span class="sxs-lookup"><span data-stu-id="914ee-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="914ee-298">第4章-照相机设置</span><span class="sxs-lookup"><span data-stu-id="914ee-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="914ee-299">如果希望跳过本课程的*Unity 设置*组件, 并继续直接进入代码, 可以[下载 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), 并将其作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)导入到项目中。</span><span class="sxs-lookup"><span data-stu-id="914ee-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="914ee-300">请注意, 此包还包含[第5章](#chapter-5--import-the-newtonsoftjson-library)中介绍的*newtonsoft.json DLL*的导入。</span><span class="sxs-lookup"><span data-stu-id="914ee-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoftjson-library).</span></span> <span data-ttu-id="914ee-301">导入后, 你可以继续[第6章](#chapter-6---create-the-faceanalysis-class)。</span><span class="sxs-lookup"><span data-stu-id="914ee-301">With this imported, you can continue from [Chapter 6](#chapter-6---create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="914ee-302">在 "*层次结构*" 面板中, 选择 "**摄像机**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="914ee-303">选择后, 你将能够在 "*检查器" 面板*中看到**主相机**的所有组件。</span><span class="sxs-lookup"><span data-stu-id="914ee-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="914ee-304">**照相机对象**必须命名为 "**主相机**" (请注意拼写正确!)</span><span class="sxs-lookup"><span data-stu-id="914ee-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="914ee-305">必须将主相机**标记**设置为**MainCamera** (请注意拼写!)</span><span class="sxs-lookup"><span data-stu-id="914ee-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="914ee-306">请确保将**转换位置**设置为**0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="914ee-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="914ee-307">将**清除标志**设置为**纯色**</span><span class="sxs-lookup"><span data-stu-id="914ee-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="914ee-308">将相机组件的**背景**色设置为**黑色、Alpha 0 (十六进制代码: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="914ee-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![设置照相机组件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="914ee-310">第5章–导入 Newtonsoft.json 库</span><span class="sxs-lookup"><span data-stu-id="914ee-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="914ee-311">如果在[上一章](#chapter-4---main-camera-setup)中导入了 "unitypackage", 则可以跳过本章。</span><span class="sxs-lookup"><span data-stu-id="914ee-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4---main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="914ee-312">若要帮助您反序列化和序列化接收并发送到机器人服务的对象, 您需要下载*newtonsoft.json*库。</span><span class="sxs-lookup"><span data-stu-id="914ee-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="914ee-313">你将发现已使用此[unity 包文件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)中的正确 Unity 文件夹结构组织的兼容版本。</span><span class="sxs-lookup"><span data-stu-id="914ee-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="914ee-314">导入库:</span><span class="sxs-lookup"><span data-stu-id="914ee-314">To import the library:</span></span>

1.  <span data-ttu-id="914ee-315">下载 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="914ee-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="914ee-316">单击 "**资产**、**导入包**、**自定义包**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![导入 Newtonsoft.json 库](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="914ee-318">查找已下载的 Unity 包, 并单击 "打开"。</span><span class="sxs-lookup"><span data-stu-id="914ee-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="914ee-319">确保包的所有组件都是勾选, 并单击 "**导入**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![导入 Newtonsoft.json 库](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="914ee-321">第6章-创建 FaceAnalysis 类</span><span class="sxs-lookup"><span data-stu-id="914ee-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="914ee-322">FaceAnalysis 类的目的是托管与 Azure 面部识别服务进行通信所需的方法。</span><span class="sxs-lookup"><span data-stu-id="914ee-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="914ee-323">在将该服务发送到捕获映像后, 它将分析它并标识中的人脸, 并确定是否有任何一个属于已知人员。</span><span class="sxs-lookup"><span data-stu-id="914ee-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="914ee-324">如果找到了一个已知人员, 此类会将其名称作为 UI 文本显示在场景中。</span><span class="sxs-lookup"><span data-stu-id="914ee-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="914ee-325">若要创建*FaceAnalysis*类:</span><span class="sxs-lookup"><span data-stu-id="914ee-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="914ee-326">右键单击位于 "项目" 面板中的 "*资产" 文件夹*, 然后单击 "**创建** > **文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="914ee-327">调用文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="914ee-327">Call the folder **Scripts**.</span></span> 

    ![创建 FaceAnalysis 类。](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="914ee-329">双击刚创建的文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="914ee-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="914ee-330">右键单击文件夹内, 然后单击 "**创建** >   **C#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="914ee-331">调用脚本*FaceAnalysis*。</span><span class="sxs-lookup"><span data-stu-id="914ee-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="914ee-332">双击新的*FaceAnalysis*脚本以通过 Visual Studio 2017 将其打开。</span><span class="sxs-lookup"><span data-stu-id="914ee-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="914ee-333">在*FaceAnalysis*类上输入以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="914ee-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="914ee-334">现在需要添加用于 deserialising 的所有对象。</span><span class="sxs-lookup"><span data-stu-id="914ee-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="914ee-335">需要将这些对象添加到*FaceAnalysis*脚本**之外**(下花括号下)。</span><span class="sxs-lookup"><span data-stu-id="914ee-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="914ee-336">不会使用*Start ()* 和*Update ()* 方法, 因此请立即将其删除。</span><span class="sxs-lookup"><span data-stu-id="914ee-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="914ee-337">在*FaceAnalysis*类中, 添加以下变量:</span><span class="sxs-lookup"><span data-stu-id="914ee-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="914ee-338">将**密钥**和**personGroupId**替换为你的服务密钥, 并将其 Id 替换为之前创建的组的 Id。</span><span class="sxs-lookup"><span data-stu-id="914ee-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="914ee-339">添加*唤醒 ()* 方法, 该方法 initialises 类, 将*ImageCapture*类添加到主相机并调用标签创建方法:</span><span class="sxs-lookup"><span data-stu-id="914ee-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="914ee-340">添加*CreateLabel ()* 方法, 该方法创建*标签*对象以显示分析结果:</span><span class="sxs-lookup"><span data-stu-id="914ee-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="914ee-341">添加*DetectFacesFromImage ()* 和*GetImageAsByteArray ()* 方法。</span><span class="sxs-lookup"><span data-stu-id="914ee-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="914ee-342">前者会请求面部识别服务检测提交的图像中任何可能的人脸, 而后者则需要将捕获的图像转换为字节数组:</span><span class="sxs-lookup"><span data-stu-id="914ee-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="914ee-343">添加*IdentifyFaces ()* 方法, 该方法请求*面部识别服务*识别以前在提交的图像中检测到的任何已知人脸。</span><span class="sxs-lookup"><span data-stu-id="914ee-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="914ee-344">请求将返回标识的人员的 id, 但不返回名称:</span><span class="sxs-lookup"><span data-stu-id="914ee-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="914ee-345">添加*GetPerson ()* 方法。</span><span class="sxs-lookup"><span data-stu-id="914ee-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="914ee-346">通过提供人员 id, 此方法会请求*面部识别服务*返回标识的人员的姓名:</span><span class="sxs-lookup"><span data-stu-id="914ee-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="914ee-347">请记住在返回到 Unity 编辑器之前**保存**更改。</span><span class="sxs-lookup"><span data-stu-id="914ee-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="914ee-348">在 Unity 编辑器中, 将 "FaceAnalysis" 脚本从 "项目" 面板中的 "脚本" 文件夹拖到 "*层次结构" 面板*中的主相机对象。</span><span class="sxs-lookup"><span data-stu-id="914ee-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="914ee-349">新的脚本组件将添加到主摄像机。</span><span class="sxs-lookup"><span data-stu-id="914ee-349">The new script component will be so added to the Main Camera.</span></span> 

![将 FaceAnalysis 放到主相机上](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="914ee-351">第7章-创建 ImageCapture 类</span><span class="sxs-lookup"><span data-stu-id="914ee-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="914ee-352">*ImageCapture*类的目的是托管与*Azure 面部识别服务*进行通信所需的方法, 以分析要捕获的映像, 确定其面部并确定它是否属于某个已知人员。</span><span class="sxs-lookup"><span data-stu-id="914ee-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="914ee-353">如果找到了一个已知人员, 此类会将其名称作为 UI 文本显示在场景中。</span><span class="sxs-lookup"><span data-stu-id="914ee-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="914ee-354">若要创建*ImageCapture*类:</span><span class="sxs-lookup"><span data-stu-id="914ee-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="914ee-355">在之前创建的**脚本**文件夹中右键单击, 然后单击 "**创建**" 和 "  **C#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="914ee-356">调用脚本*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="914ee-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="914ee-357">双击新的*ImageCapture*脚本以通过 Visual Studio 2017 将其打开。</span><span class="sxs-lookup"><span data-stu-id="914ee-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="914ee-358">在 ImageCapture 类上输入以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="914ee-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="914ee-359">在*ImageCapture*类中, 添加以下变量:</span><span class="sxs-lookup"><span data-stu-id="914ee-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="914ee-360">添加初始化类所需的*唤醒 ()* 和*Start ()* 方法, 并允许 HoloLens 捕获用户的手势:</span><span class="sxs-lookup"><span data-stu-id="914ee-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="914ee-361">添加在用户执行*攻*指操作时调用的*TapHandler ()* :</span><span class="sxs-lookup"><span data-stu-id="914ee-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="914ee-362">添加*ExecuteImageCaptureAndAnalysis ()* 方法, 该方法将开始映像捕获过程:</span><span class="sxs-lookup"><span data-stu-id="914ee-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="914ee-363">添加完成照片捕获过程时调用的处理程序:</span><span class="sxs-lookup"><span data-stu-id="914ee-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="914ee-364">请记住在返回到 Unity 编辑器之前**保存**更改。</span><span class="sxs-lookup"><span data-stu-id="914ee-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="914ee-365">第8章-构建解决方案</span><span class="sxs-lookup"><span data-stu-id="914ee-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="914ee-366">若要对应用程序进行全面测试, 需要将其旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="914ee-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="914ee-367">在执行此操作之前, 请确保:</span><span class="sxs-lookup"><span data-stu-id="914ee-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="914ee-368">第3章中提到的所有设置都已正确设置。</span><span class="sxs-lookup"><span data-stu-id="914ee-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="914ee-369">脚本*FaceAnalysis*已附加到摄像机主对象。</span><span class="sxs-lookup"><span data-stu-id="914ee-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="914ee-370">已在*FaceAnalysis*脚本中设置**身份验证密钥**和**组 Id** 。</span><span class="sxs-lookup"><span data-stu-id="914ee-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="914ee-371">答: 您已准备好生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="914ee-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="914ee-372">构建解决方案后, 就可以开始部署应用程序了。</span><span class="sxs-lookup"><span data-stu-id="914ee-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="914ee-373">开始生成过程:</span><span class="sxs-lookup"><span data-stu-id="914ee-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="914ee-374">单击 "文件"、"保存" 保存当前场景。</span><span class="sxs-lookup"><span data-stu-id="914ee-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="914ee-375">依次单击 "文件"、"生成设置"、"添加打开的场景"。</span><span class="sxs-lookup"><span data-stu-id="914ee-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="914ee-376">请确保对 Unity C#项目进行计时。</span><span class="sxs-lookup"><span data-stu-id="914ee-376">Make sure to tick Unity C# Projects.</span></span>

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="914ee-378">按 "生成"。</span><span class="sxs-lookup"><span data-stu-id="914ee-378">Press Build.</span></span> <span data-ttu-id="914ee-379">完成此操作后, Unity 将启动 "文件资源管理器" 窗口, 需要在其中创建应用程序, 然后选择要将应用程序生成到其中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="914ee-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="914ee-380">现在, 在 Unity 项目中创建该文件夹, 然后调用它应用。</span><span class="sxs-lookup"><span data-stu-id="914ee-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="914ee-381">选择应用文件夹后, 按 "选择文件夹"。</span><span class="sxs-lookup"><span data-stu-id="914ee-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="914ee-382">Unity 将开始生成您的项目, 而不是应用程序文件夹。</span><span class="sxs-lookup"><span data-stu-id="914ee-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="914ee-383">Unity 完成生成后 (可能需要一些时间), 将在生成的位置打开文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="914ee-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="914ee-385">打开应用文件夹, 然后打开新的项目解决方案 (如上所示, MR_FaceRecognition)。</span><span class="sxs-lookup"><span data-stu-id="914ee-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="914ee-386">第9章-部署应用程序</span><span class="sxs-lookup"><span data-stu-id="914ee-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="914ee-387">在 HoloLens 上部署:</span><span class="sxs-lookup"><span data-stu-id="914ee-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="914ee-388">你将需要 HoloLens 的 IP 地址 (用于远程部署), 并确保你的 HoloLens 处于**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="914ee-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="914ee-389">为此，请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="914ee-389">To do this:</span></span>

    1. <span data-ttu-id="914ee-390">在戴上 HoloLens 的同时, 请打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="914ee-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="914ee-391">中转到**网络 & Internet > wi-fi > 高级选项**</span><span class="sxs-lookup"><span data-stu-id="914ee-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="914ee-392">记下**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="914ee-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="914ee-393">接下来, 导航回 "**设置**", 然后为**开发人员更新 & Security >**</span><span class="sxs-lookup"><span data-stu-id="914ee-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="914ee-394">设置开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="914ee-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="914ee-395">导航到新的 Unity 生成 (*应用*文件夹), 并在*Visual Studio*中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="914ee-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="914ee-396">在解决方案配置中, 选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="914ee-397">在解决方案平台中, 选择 " **x86**,**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="914ee-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![从 Visual Studio 部署解决方案。](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="914ee-399">请在 "**生成" 菜单**中, 单击 "**部署解决方案**", 将应用程序旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="914ee-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="914ee-400">应用现在应显示在你的 HoloLens 上已安装的应用列表中, 可以启动了!</span><span class="sxs-lookup"><span data-stu-id="914ee-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="914ee-401">若要部署到沉浸式耳机, 请将 "**解决方案平台**" 设置为 "*本地计算机*", 并将**配置**设置为 "*调试*", 将 " *x86* " 设置为**平台**。</span><span class="sxs-lookup"><span data-stu-id="914ee-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="914ee-402">然后, 使用 "**生成" 菜单**选择 "*部署解决方案*", 将部署到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="914ee-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="914ee-403">第10章-使用应用程序</span><span class="sxs-lookup"><span data-stu-id="914ee-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="914ee-404">戴上 HoloLens, 启动应用。</span><span class="sxs-lookup"><span data-stu-id="914ee-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="914ee-405">查看在*人脸 API*注册的人。</span><span class="sxs-lookup"><span data-stu-id="914ee-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="914ee-406">请确保：</span><span class="sxs-lookup"><span data-stu-id="914ee-406">Make sure that:</span></span>

    -  <span data-ttu-id="914ee-407">人脸不太遥远并且明显可见</span><span class="sxs-lookup"><span data-stu-id="914ee-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="914ee-408">环境照明不太暗</span><span class="sxs-lookup"><span data-stu-id="914ee-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="914ee-409">使用点击手势来捕获人员的照片。</span><span class="sxs-lookup"><span data-stu-id="914ee-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="914ee-410">等待应用发送分析请求并接收响应。</span><span class="sxs-lookup"><span data-stu-id="914ee-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="914ee-411">如果用户已成功识别, 则该人员的名称将显示为 UI 文本。</span><span class="sxs-lookup"><span data-stu-id="914ee-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="914ee-412">可以每隔几秒钟使用点击手势重复捕获过程。</span><span class="sxs-lookup"><span data-stu-id="914ee-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="914ee-413">已完成的 Azure 人脸 API 应用程序</span><span class="sxs-lookup"><span data-stu-id="914ee-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="914ee-414">恭喜, 你构建了一个混合现实应用, 它利用 Azure 面部识别服务检测图像中的人脸, 并识别所有已知的人脸。</span><span class="sxs-lookup"><span data-stu-id="914ee-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="914ee-416">额外练习</span><span class="sxs-lookup"><span data-stu-id="914ee-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="914ee-417">练习1</span><span class="sxs-lookup"><span data-stu-id="914ee-417">Exercise 1</span></span>

<span data-ttu-id="914ee-418">**Azure 人脸 API**的强大功能足以在单个映像中检测到64面。</span><span class="sxs-lookup"><span data-stu-id="914ee-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="914ee-419">扩展应用程序, 使其能够识别多个其他人的两个或三个面。</span><span class="sxs-lookup"><span data-stu-id="914ee-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="914ee-420">练习2</span><span class="sxs-lookup"><span data-stu-id="914ee-420">Exercise 2</span></span>

<span data-ttu-id="914ee-421">**Azure 人脸 API**还可以提供返回各种类型的属性信息。</span><span class="sxs-lookup"><span data-stu-id="914ee-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="914ee-422">将此集成到应用程序中。</span><span class="sxs-lookup"><span data-stu-id="914ee-422">Integrate this into the application.</span></span> <span data-ttu-id="914ee-423">与[情感 API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)结合时, 这可能更加有趣。</span><span class="sxs-lookup"><span data-stu-id="914ee-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
