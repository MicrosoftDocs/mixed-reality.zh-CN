---
title: MR 和 Azure 304-人脸识别
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 人脸识别。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure，混合现实、 学院、 unity、 教程、 api、 人脸识别，沉浸式、 hololens、 vr
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592789"
---
>[!NOTE]
><span data-ttu-id="af9fb-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="af9fb-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="af9fb-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="af9fb-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="af9fb-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="af9fb-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="af9fb-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="af9fb-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="af9fb-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="af9fb-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="af9fb-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="af9fb-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="af9fb-110">MR 和 Azure 304:人脸识别</span><span class="sxs-lookup"><span data-stu-id="af9fb-110">MR and Azure 304: Face recognition</span></span>

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="af9fb-112">在本课程中您将了解如何将人脸识别功能添加到混合的现实应用程序，Azure 认知服务，与 Microsoft 人脸 API 结合使用。</span><span class="sxs-lookup"><span data-stu-id="af9fb-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="af9fb-113">*Azure 的人脸 API*是 Microsoft 服务，开发人员提供最先进的人脸算法，所有在云中。</span><span class="sxs-lookup"><span data-stu-id="af9fb-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="af9fb-114">*人脸 API*具有两个主要功能： 人脸属性后，检测和人脸识别。</span><span class="sxs-lookup"><span data-stu-id="af9fb-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="af9fb-115">这允许开发人员只需设置一组人脸的组，然后，查询图像向服务发送更高版本，以确定人脸属于其。</span><span class="sxs-lookup"><span data-stu-id="af9fb-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="af9fb-116">有关详细信息，请访问[Azure 人脸识别页](https://azure.microsoft.com/services/cognitive-services/face/)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="af9fb-117">已完成本课程，您将具有混合的现实 HoloLens 应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="af9fb-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="af9fb-118">使用**点击手势**初始化使用板载 HoloLens 相机的图像的捕获。</span><span class="sxs-lookup"><span data-stu-id="af9fb-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="af9fb-119">发送到捕获的映像*Azure 人脸 API*服务。</span><span class="sxs-lookup"><span data-stu-id="af9fb-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="af9fb-120">收到的结果*人脸 API*算法。</span><span class="sxs-lookup"><span data-stu-id="af9fb-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="af9fb-121">使用简单的用户界面，以显示匹配的人的名称。</span><span class="sxs-lookup"><span data-stu-id="af9fb-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="af9fb-122">这将教您如何将结果从人脸 API 服务到基于 Unity 的混合的现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="af9fb-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="af9fb-123">在您的应用程序，它是取决于您关于如何将与您的设计集成结果。</span><span class="sxs-lookup"><span data-stu-id="af9fb-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="af9fb-124">本课程旨在教您如何将 Azure 服务与你的 Unity 项目集成。</span><span class="sxs-lookup"><span data-stu-id="af9fb-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="af9fb-125">它是作业以使用此课程以增强混合的现实应用程序中获取的知识。</span><span class="sxs-lookup"><span data-stu-id="af9fb-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="af9fb-126">设备支持</span><span class="sxs-lookup"><span data-stu-id="af9fb-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="af9fb-127">课程</span><span class="sxs-lookup"><span data-stu-id="af9fb-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="af9fb-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="af9fb-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="af9fb-129"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="af9fb-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="af9fb-130">MR 和 Azure 304:人脸识别</span><span class="sxs-lookup"><span data-stu-id="af9fb-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="af9fb-131">✔️</span><span class="sxs-lookup"><span data-stu-id="af9fb-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="af9fb-132">✔️</span><span class="sxs-lookup"><span data-stu-id="af9fb-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="af9fb-133">尽管本课程主要专注于 HoloLens，您还可以应用到 Windows Mixed Reality 沉浸式 (VR) 耳机本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="af9fb-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="af9fb-134">因为沉浸式 (VR) 耳机不具有可访问照相机，您将需要连接到您的 PC 外部照相机。</span><span class="sxs-lookup"><span data-stu-id="af9fb-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="af9fb-135">按照课程时，您将看到说明您可能需要使用以支持沉浸式 (VR) 耳机的任何更改。</span><span class="sxs-lookup"><span data-stu-id="af9fb-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="af9fb-136">系统必备</span><span class="sxs-lookup"><span data-stu-id="af9fb-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="af9fb-137">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="af9fb-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="af9fb-138">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="af9fb-139">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.</span><span class="sxs-lookup"><span data-stu-id="af9fb-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="af9fb-140">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="af9fb-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="af9fb-141">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="af9fb-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="af9fb-142">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="af9fb-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="af9fb-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="af9fb-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="af9fb-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="af9fb-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="af9fb-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="af9fb-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="af9fb-146">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="af9fb-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="af9fb-147">照相机连接到您的 PC （适用于沉浸式头戴式开发）</span><span class="sxs-lookup"><span data-stu-id="af9fb-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="af9fb-148">Internet 访问的 Azure 设置和人脸 API 检索</span><span class="sxs-lookup"><span data-stu-id="af9fb-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="af9fb-149">开始之前</span><span class="sxs-lookup"><span data-stu-id="af9fb-149">Before you start</span></span>

1.  <span data-ttu-id="af9fb-150">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="af9fb-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="af9fb-151">设置和测试你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="af9fb-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="af9fb-152">如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="af9fb-153">它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。</span><span class="sxs-lookup"><span data-stu-id="af9fb-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="af9fb-154">有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="af9fb-155">有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="af9fb-156">第 1 章-Azure 门户</span><span class="sxs-lookup"><span data-stu-id="af9fb-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="af9fb-157">若要使用*人脸 API*服务在 Azure 中，你将需要配置要成为可用于应用程序的服务的实例。</span><span class="sxs-lookup"><span data-stu-id="af9fb-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="af9fb-158">首先，登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="af9fb-159">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="af9fb-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="af9fb-160">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="af9fb-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="af9fb-161">你登录后，单击**新建**在左上角，并搜索*人脸 API*，按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![搜索人脸 api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="af9fb-163">单词**新建**可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="af9fb-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="af9fb-164">该新页面将提供的说明*人脸 API*服务。</span><span class="sxs-lookup"><span data-stu-id="af9fb-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="af9fb-165">在左下角此提示符下，选择**创建**按钮，以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="af9fb-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![人脸 api 信息](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="af9fb-167">一旦你单击**创建**:</span><span class="sxs-lookup"><span data-stu-id="af9fb-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="af9fb-168">插入此服务实例所需的名称。</span><span class="sxs-lookup"><span data-stu-id="af9fb-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="af9fb-169">选择一个订阅。</span><span class="sxs-lookup"><span data-stu-id="af9fb-169">Select a subscription.</span></span>

    3. <span data-ttu-id="af9fb-170">选择定价层适合你，如果这是首次创建*人脸 API 服务*，应可供你免费层 （名为 F0）。</span><span class="sxs-lookup"><span data-stu-id="af9fb-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="af9fb-171">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="af9fb-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="af9fb-172">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="af9fb-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="af9fb-173">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="af9fb-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="af9fb-174">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="af9fb-175">UWP 应用后，**人员 Maker**，更高版本，使用该位置需要使用美国西部。</span><span class="sxs-lookup"><span data-stu-id="af9fb-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="af9fb-176">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="af9fb-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="af9fb-177">选择**创建\*。**</span><span class="sxs-lookup"><span data-stu-id="af9fb-177">Select **Create\*.**</span></span>

        ![创建人脸 api 服务](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="af9fb-179">一旦你单击 **创建**\* 必须要等待的时间来创建服务，这可能需要一分钟的时间。</span><span class="sxs-lookup"><span data-stu-id="af9fb-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="af9fb-180">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="af9fb-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![服务创建通知](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="af9fb-182">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="af9fb-182">Click on the notifications to explore your new Service instance.</span></span>

    ![请转到资源通知](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="af9fb-184">准备就绪后，单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="af9fb-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![访问人脸 api 密钥](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="af9fb-186">在本教程中，你的应用程序将需要对你的服务，是通过使用服务的订阅密钥进行调用。</span><span class="sxs-lookup"><span data-stu-id="af9fb-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="af9fb-187">从*快速入门*页上的你*人脸 API*服务，第一个点是为其编号为 1，*捕捉密钥。*</span><span class="sxs-lookup"><span data-stu-id="af9fb-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="af9fb-188">上*服务*页上，选择任一蓝色**密钥**超链接 （如果已打开快速启动页），或**密钥**服务导航菜单中的链接 (位于左侧、 为由键图标)，以显示你的密钥。</span><span class="sxs-lookup"><span data-stu-id="af9fb-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="af9fb-189">请记下的任何一个密钥并保护它，因为稍后将需要它。</span><span class="sxs-lookup"><span data-stu-id="af9fb-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="af9fb-190">第 2 章-使用人员 Maker UWP 应用程序</span><span class="sxs-lookup"><span data-stu-id="af9fb-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="af9fb-191">请务必下载预生成的 UWP 应用程序调用[人员 Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="af9fb-192">此应用不是本课程中，只是一个工具，可帮助您创建在 Azure 的条目，将依赖于更高版本的项目最终产品。</span><span class="sxs-lookup"><span data-stu-id="af9fb-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="af9fb-193">**人员 Maker**允许你创建 Azure 的条目，它们是与人员和人员组相关联。</span><span class="sxs-lookup"><span data-stu-id="af9fb-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="af9fb-194">应用程序会将所有所需的信息，然后更高版本来 FaceAPI，以识别其已添加人员人脸的格式。</span><span class="sxs-lookup"><span data-stu-id="af9fb-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="af9fb-195">[重要]**人员 Maker**使用一些基本的限制，来帮助确保不超过每分钟的服务调用数**免费订阅层**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="af9fb-196">在顶部的绿色文本将变为红色并更新为活动时出现了限制;如果这种情况，只需等待应用程序 （它将等待，直到它接下来可以继续访问该人脸服务，可以再次使用它更新为在活动）。</span><span class="sxs-lookup"><span data-stu-id="af9fb-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="af9fb-197">此应用程序使用*Microsoft.ProjectOxford.Face*库，这样就可以进行完整的人脸 API 使用。</span><span class="sxs-lookup"><span data-stu-id="af9fb-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="af9fb-198">此库是可免费获得作为 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="af9fb-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="af9fb-199">有关详细信息，了解相关信息，以及类似，Api[请务必访问的 API 参考文章](https://docs.microsoft.com/azure/cognitive-services/face/apireference)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="af9fb-200">这些是只是所需的步骤，说明如何执行这些操作是进一步文档。</span><span class="sxs-lookup"><span data-stu-id="af9fb-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="af9fb-201">**人员 Maker**应用将允许您为：</span><span class="sxs-lookup"><span data-stu-id="af9fb-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="af9fb-202">创建*人员组*，后者由一组组成的多个用户想要将与之关联。</span><span class="sxs-lookup"><span data-stu-id="af9fb-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="af9fb-203">使用 Azure 帐户可以托管多个人员组。</span><span class="sxs-lookup"><span data-stu-id="af9fb-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="af9fb-204">创建*人员*，这是一个人员组的成员。</span><span class="sxs-lookup"><span data-stu-id="af9fb-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="af9fb-205">每个人都有大量*人脸*与之关联的映像。</span><span class="sxs-lookup"><span data-stu-id="af9fb-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="af9fb-206">将分配*人脸图像*到*人员*，以允许 Azure 人脸 API 服务以识别*人员*对应*人脸*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="af9fb-207">*训练*你*Azure 人脸 API 服务*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="af9fb-208">注意，因此若要训练此应用程序中识别人，您需要十 （10） 特写照片的每个人员想要将添加到人员组。</span><span class="sxs-lookup"><span data-stu-id="af9fb-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="af9fb-209">Windows 10 网络摄像机，应用可以帮助你为将这些。</span><span class="sxs-lookup"><span data-stu-id="af9fb-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="af9fb-210">必须确保每张照片是清除 （避免模糊、 遮蔽，或使用者正在太远），与没有较大的图像文件大小 jpg 或 png 文件格式，具有照片**4MB**，和不少于**1KB**.</span><span class="sxs-lookup"><span data-stu-id="af9fb-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="af9fb-211">在您按照本教程，请不要用于你自己的人脸的培训，如 HoloLens 时，您不能在您自己。</span><span class="sxs-lookup"><span data-stu-id="af9fb-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="af9fb-212">使用人脸的同事或人员的学生。</span><span class="sxs-lookup"><span data-stu-id="af9fb-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="af9fb-213">运行**人员 Maker**:</span><span class="sxs-lookup"><span data-stu-id="af9fb-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="af9fb-214">打开**PersonMaker**文件夹并双击*PersonMaker 解决方案*以打开其与*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="af9fb-215">一次*PersonMaker 解决方案*打开，请确保：</span><span class="sxs-lookup"><span data-stu-id="af9fb-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="af9fb-216">*解决方案配置*设置为**调试**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="af9fb-217">*解决方案平台*设置为**x86**</span><span class="sxs-lookup"><span data-stu-id="af9fb-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="af9fb-218">*目标平台*是**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="af9fb-219">你还可能需要*还原 NuGet 包*(右键单击*解决方案*，然后选择**还原 NuGet 包**)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="af9fb-220">单击*本地计算机*和应用程序将启动。</span><span class="sxs-lookup"><span data-stu-id="af9fb-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="af9fb-221">注意，在较小屏幕上，所有内容可能不都会显示，尽管您可以滚动进一步向下键查看它。</span><span class="sxs-lookup"><span data-stu-id="af9fb-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![人员 maker 用户界面](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="af9fb-223">插入您**Azure 身份验证密钥**，其中应包含，从你*人脸 API*服务在 Azure 中。</span><span class="sxs-lookup"><span data-stu-id="af9fb-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="af9fb-224">插入：</span><span class="sxs-lookup"><span data-stu-id="af9fb-224">Insert:</span></span>

    1. <span data-ttu-id="af9fb-225">*ID*想要分配给*人员组*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="af9fb-226">ID 必须为小写，且没有空格。</span><span class="sxs-lookup"><span data-stu-id="af9fb-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="af9fb-227">记下此 ID，因为它将在 Unity 项目中的更高版本所必需。</span><span class="sxs-lookup"><span data-stu-id="af9fb-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="af9fb-228">*名称*想要分配给*人员组*（可以包含空格）。</span><span class="sxs-lookup"><span data-stu-id="af9fb-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="af9fb-229">按**创建人员组**按钮。</span><span class="sxs-lookup"><span data-stu-id="af9fb-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="af9fb-230">下面的按钮应显示一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="af9fb-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="af9fb-231">如果有拒绝访问错误，检查设置为 Azure 服务的位置。</span><span class="sxs-lookup"><span data-stu-id="af9fb-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="af9fb-232">如上面所述，此应用专为美国西部。</span><span class="sxs-lookup"><span data-stu-id="af9fb-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af9fb-233">你会注意到，您可以单击**提取已知组**按钮： 如果你已创建一个人使用，而不是创建一个新的组，并且想这是用于。</span><span class="sxs-lookup"><span data-stu-id="af9fb-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="af9fb-234">请注意，如果单击*创建人员组*与已知组，这还将获得一个组。</span><span class="sxs-lookup"><span data-stu-id="af9fb-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="af9fb-235">插入*名称*的*人员*你想要创建。</span><span class="sxs-lookup"><span data-stu-id="af9fb-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="af9fb-236">单击**创建 Person**按钮。</span><span class="sxs-lookup"><span data-stu-id="af9fb-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="af9fb-237">下面的按钮应显示一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="af9fb-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="af9fb-238">如果想要删除一个人之前已创建，你可以编写到文本框，并按名称**删除人**</span><span class="sxs-lookup"><span data-stu-id="af9fb-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="af9fb-239">请确保你知道你想要添加到组的人员的照片十 （10） 的位置。</span><span class="sxs-lookup"><span data-stu-id="af9fb-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="af9fb-240">按**创建和打开文件夹**到关联的人员的文件夹中打开 Windows 资源管理器。</span><span class="sxs-lookup"><span data-stu-id="af9fb-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="af9fb-241">在文件夹中添加十 （10） 映像。</span><span class="sxs-lookup"><span data-stu-id="af9fb-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="af9fb-242">这些必须属于*JPG*或*PNG*文件格式。</span><span class="sxs-lookup"><span data-stu-id="af9fb-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="af9fb-243">单击**提交到 Azure**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="af9fb-244">计数器将显示你的提交，完成后跟一条消息的状态。</span><span class="sxs-lookup"><span data-stu-id="af9fb-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="af9fb-245">单击该计数器已完成并显示确认消息后**训练**来训练你的服务。</span><span class="sxs-lookup"><span data-stu-id="af9fb-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="af9fb-246">过程完成后，已准备好移动到 Unity。</span><span class="sxs-lookup"><span data-stu-id="af9fb-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="af9fb-247">第 3 章 — 设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="af9fb-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="af9fb-248">以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="af9fb-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="af9fb-249">打开*Unity*然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-249">Open *Unity* and click **New**.</span></span> 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="af9fb-251">现在，需要提供 Unity 项目的名称。</span><span class="sxs-lookup"><span data-stu-id="af9fb-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="af9fb-252">插入**MR_FaceRecognition**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="af9fb-253">请确保项目类型设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="af9fb-254">设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="af9fb-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="af9fb-255">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-255">Then, click **Create project**.</span></span>

    ![提供新的 Unity 项目的详细信息。](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="af9fb-257">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="af9fb-258">转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="af9fb-259">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="af9fb-260">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="af9fb-260">Close the **Preferences** window.</span></span>

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="af9fb-262">接下来，请转到**文件 > 生成设置**，并切换到平台**通用 Windows 平台**，单击**切换平台**按钮。</span><span class="sxs-lookup"><span data-stu-id="af9fb-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![生成设置窗口中，切换到 UWP 的平台。](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="af9fb-264">转到**文件 > 生成设置**并确保选中：</span><span class="sxs-lookup"><span data-stu-id="af9fb-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="af9fb-265">**设备为目标**设置为**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="af9fb-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="af9fb-266">对于沉浸式耳机，设置**目标设备**到*任一设备*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="af9fb-267">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="af9fb-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="af9fb-268">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="af9fb-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="af9fb-269">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="af9fb-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="af9fb-270">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="af9fb-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="af9fb-271">保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="af9fb-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="af9fb-272">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="af9fb-273">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="af9fb-273">A save window will appear.</span></span>

            ![单击添加打开场景按钮](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="af9fb-275">选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![创建新的 scripts 文件夹](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="af9fb-277">打开新建**场景**文件夹，然后在**文件名**： 文本字段中，键入**FaceRecScene**，然后按**保存**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![为新的场景提供一个名称。](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="af9fb-279">中的剩余设置，*生成设置*，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="af9fb-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="af9fb-280">在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。</span><span class="sxs-lookup"><span data-stu-id="af9fb-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![打开播放器设置。](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="af9fb-282">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="af9fb-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="af9fb-283">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="af9fb-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="af9fb-284">**脚本编写** **运行时版本**应**实验**（.NET 4.6 等效）。</span><span class="sxs-lookup"><span data-stu-id="af9fb-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="af9fb-285">此更改将触发需要重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="af9fb-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="af9fb-286">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="af9fb-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="af9fb-287">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="af9fb-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他设置。](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="af9fb-289">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="af9fb-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="af9fb-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="af9fb-290">**InternetClient**</span></span>
        - <span data-ttu-id="af9fb-291">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="af9fb-291">**Webcam**</span></span>

            ![正在更新的发布设置。](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="af9fb-293">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。</span><span class="sxs-lookup"><span data-stu-id="af9fb-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新的 X R 设置。](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="af9fb-295">回到*生成设置*， **UnityC#项目**不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="af9fb-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="af9fb-296">关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="af9fb-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="af9fb-297">保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="af9fb-298">第 4 章-主照相机设置</span><span class="sxs-lookup"><span data-stu-id="af9fb-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af9fb-299">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，可以任意[下载此.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)，并将其导入项目中，作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="af9fb-300">请注意，此包还包含在导入*Newtonsoft DLL*中所述[第 5 章：](#chapter-5--import-the-newtonsoft.json-library)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoft.json-library).</span></span> <span data-ttu-id="af9fb-301">与此导入，您可以继续从[第 6 章](#chapter-6-create-the-faceanalysis-class)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-301">With this imported, you can continue from [Chapter 6](#chapter-6-create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="af9fb-302">在中*层次结构*面板中，选择**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="af9fb-303">选择后，你将能够看到的所有组件**Main Camera**中*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="af9fb-304">**相机对象**必须命名为**Main Camera** （请注意拼写 ！）</span><span class="sxs-lookup"><span data-stu-id="af9fb-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="af9fb-305">Main Camera**标记**必须设置为**MainCamera** （请注意拼写 ！）</span><span class="sxs-lookup"><span data-stu-id="af9fb-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="af9fb-306">请确保**转换位置**设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="af9fb-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="af9fb-307">设置**清除标志**到**纯色**</span><span class="sxs-lookup"><span data-stu-id="af9fb-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="af9fb-308">设置**背景**照相机组件到色**黑色、 Alpha 0 (十六进制代码: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="af9fb-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![设置照相机组件](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="af9fb-310">第 5 章-将 Newtonsoft.Json 库导入</span><span class="sxs-lookup"><span data-stu-id="af9fb-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="af9fb-311">如果在中导入.unitypackage'[最后一章](#chapter-4--main-camera-setup)，可以跳过这一章。</span><span class="sxs-lookup"><span data-stu-id="af9fb-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4--main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="af9fb-312">若要帮助您反序列化和序列化对象接收和发送到机器人服务需要下载*Newtonsoft.Json*库。</span><span class="sxs-lookup"><span data-stu-id="af9fb-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="af9fb-313">将查找兼容的版本已具有正确的 Unity 文件夹结构中组织[Unity 包文件](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="af9fb-314">若要导入的库：</span><span class="sxs-lookup"><span data-stu-id="af9fb-314">To import the library:</span></span>

1.  <span data-ttu-id="af9fb-315">下载 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="af9fb-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="af9fb-316">单击**资产**，**导入包**，**自定义包**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![将 Newtonsoft.Json 库导入](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="af9fb-318">查找已下载 Unity 包，然后单击打开。</span><span class="sxs-lookup"><span data-stu-id="af9fb-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="af9fb-319">请确保包的所有组件都勾选，单击**导入**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![将 Newtonsoft.Json 库导入](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="af9fb-321">章 6-创建 FaceAnalysis 类</span><span class="sxs-lookup"><span data-stu-id="af9fb-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="af9fb-322">FaceAnalysis 类旨在托管你的 Azure 人脸识别服务通信所需的方法。</span><span class="sxs-lookup"><span data-stu-id="af9fb-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="af9fb-323">发送后该服务捕获映像，它将分析它，并识别，人脸和确定是否任何属于已知的人员。</span><span class="sxs-lookup"><span data-stu-id="af9fb-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="af9fb-324">如果找到一个已知的人，则此类将显示其名称为场景中的 UI 文本。</span><span class="sxs-lookup"><span data-stu-id="af9fb-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="af9fb-325">若要创建*FaceAnalysis*类：</span><span class="sxs-lookup"><span data-stu-id="af9fb-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="af9fb-326">在中右击*Assets 文件夹*位于项目面板，然后单击**创建** > **文件夹**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="af9fb-327">将该文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-327">Call the folder **Scripts**.</span></span> 

    ![创建 FaceAnalysis 类。](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="af9fb-329">双击刚创建的文件夹，以将其打开。</span><span class="sxs-lookup"><span data-stu-id="af9fb-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="af9fb-330">在文件夹中，右键单击，然后单击**创建** >   **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="af9fb-331">调用脚本*FaceAnalysis*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="af9fb-332">双击新*FaceAnalysis*脚本以使用 Visual Studio 2017 中打开它。</span><span class="sxs-lookup"><span data-stu-id="af9fb-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="af9fb-333">输入以下命名空间上述*FaceAnalysis*类：</span><span class="sxs-lookup"><span data-stu-id="af9fb-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="af9fb-334">现在需要添加的所有对象将用于 deserialising。</span><span class="sxs-lookup"><span data-stu-id="af9fb-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="af9fb-335">这些对象需要添加**外部**的*FaceAnalysis* （下方底部大括号） 的脚本。</span><span class="sxs-lookup"><span data-stu-id="af9fb-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

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
7. <span data-ttu-id="af9fb-336">*Start （)* 并*update （)* 方法不会使用，因此现在将其删除。</span><span class="sxs-lookup"><span data-stu-id="af9fb-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="af9fb-337">内部*FaceAnalysis*类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="af9fb-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

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
    > <span data-ttu-id="af9fb-338">替换**键**并**personGroupId**你的服务密钥和之前创建的组的 Id。</span><span class="sxs-lookup"><span data-stu-id="af9fb-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="af9fb-339">添加*Awake()* 方法，initialises 类，添加*ImageCapture*到 Main Camera 类并调用标签创建方法：</span><span class="sxs-lookup"><span data-stu-id="af9fb-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

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

10. <span data-ttu-id="af9fb-340">添加*CreateLabel()* 方法，用于创建*标签*对象以显示分析结果：</span><span class="sxs-lookup"><span data-stu-id="af9fb-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

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

11. <span data-ttu-id="af9fb-341">添加*DetectFacesFromImage()* 并*GetImageAsByteArray()* 方法。</span><span class="sxs-lookup"><span data-stu-id="af9fb-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="af9fb-342">前者将请求要在已提交的图中，检测任何可能的人脸，而后者是必须要捕获的映像转换为字节数组的人脸识别服务：</span><span class="sxs-lookup"><span data-stu-id="af9fb-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

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

12. <span data-ttu-id="af9fb-343">添加*IdentifyFaces()* 方法，请求*人脸识别服务*来标识以前提交的图像中检测到任何已知人脸。</span><span class="sxs-lookup"><span data-stu-id="af9fb-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="af9fb-344">该请求将返回的 id 标识的用户而不是名称为：</span><span class="sxs-lookup"><span data-stu-id="af9fb-344">The request will return an id of the identified person but not the name:</span></span>

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

13. <span data-ttu-id="af9fb-345">添加*GetPerson()* 方法。</span><span class="sxs-lookup"><span data-stu-id="af9fb-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="af9fb-346">通过提供用户 id，此方法然后请求*人脸识别服务*返回标识的人员的姓名：</span><span class="sxs-lookup"><span data-stu-id="af9fb-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

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

14.  <span data-ttu-id="af9fb-347">请记住**保存**之前追溯到 Unity 编辑器中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="af9fb-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="af9fb-348">在 Unity 编辑器中，将 FaceAnalysis 脚本从项目面板中的 Scripts 文件夹拖动到中的 Main Camera 对象*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="af9fb-349">新脚本组件将因此添加到 Main Camera。</span><span class="sxs-lookup"><span data-stu-id="af9fb-349">The new script component will be so added to the Main Camera.</span></span> 

![将放置到主照相机上 FaceAnalysis](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="af9fb-351">章 7-创建 ImageCapture 类</span><span class="sxs-lookup"><span data-stu-id="af9fb-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="af9fb-352">目的*ImageCapture*类是托管通信所需的方法您*Azure 人脸识别服务*分析将捕获，请确定中它的人脸的图像和确定它是否属于已知的人员。</span><span class="sxs-lookup"><span data-stu-id="af9fb-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="af9fb-353">如果找到一个已知的人，则此类将显示其名称为场景中的 UI 文本。</span><span class="sxs-lookup"><span data-stu-id="af9fb-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="af9fb-354">若要创建*ImageCapture*类：</span><span class="sxs-lookup"><span data-stu-id="af9fb-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="af9fb-355">内右击**脚本**文件夹之前，创建，然后单击**创建**，  **C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="af9fb-356">调用脚本*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="af9fb-357">双击新*ImageCapture*脚本以使用 Visual Studio 2017 中打开它。</span><span class="sxs-lookup"><span data-stu-id="af9fb-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="af9fb-358">输入上面 ImageCapture 类的以下命名空间：</span><span class="sxs-lookup"><span data-stu-id="af9fb-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="af9fb-359">内部*ImageCapture*类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="af9fb-359">Inside the *ImageCapture* class, add the following variables:</span></span>

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

5.  <span data-ttu-id="af9fb-360">添加*Awake()* 并*start （)* 初始化类和允许 HoloLens 以捕获用户的操作所需的方法：</span><span class="sxs-lookup"><span data-stu-id="af9fb-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

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

6.  <span data-ttu-id="af9fb-361">添加*TapHandler()* 用户执行时调用*点击*手势：</span><span class="sxs-lookup"><span data-stu-id="af9fb-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

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

7.  <span data-ttu-id="af9fb-362">添加*ExecuteImageCaptureAndAnalysis()* 方法，它将开始捕获映像的过程：</span><span class="sxs-lookup"><span data-stu-id="af9fb-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

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

8.  <span data-ttu-id="af9fb-363">添加照片捕获进程完成时，将调用处理程序：</span><span class="sxs-lookup"><span data-stu-id="af9fb-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

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

9. <span data-ttu-id="af9fb-364">请记住**保存**之前追溯到 Unity 编辑器中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="af9fb-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="af9fb-365">第 8 章 — 构建解决方案</span><span class="sxs-lookup"><span data-stu-id="af9fb-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="af9fb-366">若要执行全面测试您的应用程序将需要旁加载它到在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="af9fb-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="af9fb-367">执行操作之前，请确保：</span><span class="sxs-lookup"><span data-stu-id="af9fb-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="af9fb-368">第 3 章中所述的所有设置都正确都设置。</span><span class="sxs-lookup"><span data-stu-id="af9fb-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="af9fb-369">该脚本*FaceAnalysis*附加到 Main Camera 对象。</span><span class="sxs-lookup"><span data-stu-id="af9fb-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="af9fb-370">这两个**身份验证密钥**并**组 Id**中设置*FaceAnalysis*脚本。</span><span class="sxs-lookup"><span data-stu-id="af9fb-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="af9fb-371">这为你指出现在即可生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="af9fb-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="af9fb-372">生成解决方案之后, 你将准备好部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="af9fb-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="af9fb-373">若要开始生成过程：</span><span class="sxs-lookup"><span data-stu-id="af9fb-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="af9fb-374">通过在文件中，单击保存当前场景。</span><span class="sxs-lookup"><span data-stu-id="af9fb-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="af9fb-375">转到文件，生成设置，单击添加打开场景。</span><span class="sxs-lookup"><span data-stu-id="af9fb-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="af9fb-376">请确保为时钟周期 UnityC#项目。</span><span class="sxs-lookup"><span data-stu-id="af9fb-376">Make sure to tick Unity C# Projects.</span></span>

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="af9fb-378">按生成。</span><span class="sxs-lookup"><span data-stu-id="af9fb-378">Press Build.</span></span> <span data-ttu-id="af9fb-379">在此过程中，Unity 将启动文件资源管理器窗口中，需要创建，然后选择要生成该应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="af9fb-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="af9fb-380">在 Unity 项目中，现在，创建该文件夹，并对其应用程序。</span><span class="sxs-lookup"><span data-stu-id="af9fb-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="af9fb-381">然后应用文件夹后，按选择文件夹。</span><span class="sxs-lookup"><span data-stu-id="af9fb-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="af9fb-382">Unity 将开始构建您的项目，到应用程序文件夹。</span><span class="sxs-lookup"><span data-stu-id="af9fb-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="af9fb-383">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开文件资源管理器窗口在生成的位置。</span><span class="sxs-lookup"><span data-stu-id="af9fb-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="af9fb-385">打开应用程序文件夹，并打开新的项目解决方案 （如上面 MR_FaceRecognition.sln 所示）。</span><span class="sxs-lookup"><span data-stu-id="af9fb-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="af9fb-386">第 9 章 — 部署应用程序</span><span class="sxs-lookup"><span data-stu-id="af9fb-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="af9fb-387">若要部署在 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="af9fb-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="af9fb-388">你将 （适用于远程部署），需要在 HoloLens IP 地址，以确保你 HoloLens 处于**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="af9fb-389">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="af9fb-389">To do this:</span></span>

    1. <span data-ttu-id="af9fb-390">戴上您 HoloLens，同时打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="af9fb-391">转到**网络和 Internet > 的 Wi-fi > 高级选项**</span><span class="sxs-lookup"><span data-stu-id="af9fb-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="af9fb-392">请注意**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="af9fb-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="af9fb-393">接下来，导航回到**设置**，然后**更新和安全 > 适用于开发人员**</span><span class="sxs-lookup"><span data-stu-id="af9fb-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="af9fb-394">设置开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="af9fb-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="af9fb-395">导航到新的 Unity 生成 (*应用程序*文件夹)，然后打开解决方案文件与*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="af9fb-396">在解决方案配置中，选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="af9fb-397">在解决方案平台中，选择**x86**，**远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="af9fb-399">转到**生成菜单**，然后单击**部署解决方案**旁, 加载到你 HoloLens 应用程序。</span><span class="sxs-lookup"><span data-stu-id="af9fb-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="af9fb-400">在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！</span><span class="sxs-lookup"><span data-stu-id="af9fb-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="af9fb-401">若要将部署到沉浸式头戴式耳机，设置**解决方案平台**到*本地计算机*，并设置**配置**到*调试*，与*x86*作为**平台**。</span><span class="sxs-lookup"><span data-stu-id="af9fb-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="af9fb-402">然后将其部署到本地计算机，使用**生成菜单**，选择*部署解决方案*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="af9fb-403">第 10 章 — 使用应用程序</span><span class="sxs-lookup"><span data-stu-id="af9fb-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="af9fb-404">戴上 HoloLens，启动应用。</span><span class="sxs-lookup"><span data-stu-id="af9fb-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="af9fb-405">看一看使用注册的人员*人脸 API*。</span><span class="sxs-lookup"><span data-stu-id="af9fb-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="af9fb-406">请确保：</span><span class="sxs-lookup"><span data-stu-id="af9fb-406">Make sure that:</span></span>

    -  <span data-ttu-id="af9fb-407">人脸不是太遥远和清楚地显示</span><span class="sxs-lookup"><span data-stu-id="af9fb-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="af9fb-408">环境照明不是太深</span><span class="sxs-lookup"><span data-stu-id="af9fb-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="af9fb-409">使用手势来捕获此人的照片。</span><span class="sxs-lookup"><span data-stu-id="af9fb-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="af9fb-410">等待应用程序将分析请求发送和接收响应。</span><span class="sxs-lookup"><span data-stu-id="af9fb-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="af9fb-411">如果已成功识别用户，该用户的名称将显示为 UI 文本。</span><span class="sxs-lookup"><span data-stu-id="af9fb-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="af9fb-412">可以重复使用每隔几秒钟的点击动作在捕获过程。</span><span class="sxs-lookup"><span data-stu-id="af9fb-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="af9fb-413">完成的 Azure 人脸 API 的应用程序</span><span class="sxs-lookup"><span data-stu-id="af9fb-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="af9fb-414">祝贺你，构建利用 Azure 人脸识别服务来检测对映像中的人脸并识别任何已知的人脸的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="af9fb-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![完成本课程的结果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="af9fb-416">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="af9fb-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="af9fb-417">练习 1</span><span class="sxs-lookup"><span data-stu-id="af9fb-417">Exercise 1</span></span>

<span data-ttu-id="af9fb-418">**Azure 人脸 API**是功能强大，足以检测到单个映像中的最多 64 个的人脸。</span><span class="sxs-lookup"><span data-stu-id="af9fb-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="af9fb-419">扩展应用程序，以便它可以识别两个或三个人脸，在许多其他人之间。</span><span class="sxs-lookup"><span data-stu-id="af9fb-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="af9fb-420">练习 2</span><span class="sxs-lookup"><span data-stu-id="af9fb-420">Exercise 2</span></span>

<span data-ttu-id="af9fb-421">**Azure 人脸 API**它还可以提供返回所有种类的属性信息。</span><span class="sxs-lookup"><span data-stu-id="af9fb-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="af9fb-422">将此集成到应用程序。</span><span class="sxs-lookup"><span data-stu-id="af9fb-422">Integrate this into the application.</span></span> <span data-ttu-id="af9fb-423">这可能是更有趣的内容，再加上[情感 API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)。</span><span class="sxs-lookup"><span data-stu-id="af9fb-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
