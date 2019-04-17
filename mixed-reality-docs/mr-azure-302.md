---
title: MR 和 Azure 302-计算机视觉
description: 完成此课程以了解如何识别中提供的映像，在混合的现实应用程序中使用 Azure 计算机视觉的可视内容。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 计算机视觉、 沉浸式、 hololens、 vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590172"
---
>[!NOTE]
><span data-ttu-id="56f6c-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="56f6c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="56f6c-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="56f6c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="56f6c-106">这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="56f6c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="56f6c-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="56f6c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="56f6c-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="56f6c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="56f6c-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="56f6c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="56f6c-110">MR 和 Azure 302:计算机视觉</span><span class="sxs-lookup"><span data-stu-id="56f6c-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="56f6c-111">在本课程中，您将学习如何识别可视内容中提供的映像，在混合的现实应用程序中使用 Azure 计算机视觉功能。</span><span class="sxs-lookup"><span data-stu-id="56f6c-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="56f6c-112">识别结果将显示为描述性标记。</span><span class="sxs-lookup"><span data-stu-id="56f6c-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="56f6c-113">可用于此服务而无需定型的机器学习模型。</span><span class="sxs-lookup"><span data-stu-id="56f6c-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="56f6c-114">如果您的实现需要定型的机器学习模型，请参阅[MR 和 Azure 302b](mr-azure-302b.md)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![实验结果](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="56f6c-116">Microsoft 计算机视觉是一组 Api，可让开发人员提供图像处理和分析 （并返回信息），所有这些操作通过在云中使用高级的算法。</span><span class="sxs-lookup"><span data-stu-id="56f6c-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="56f6c-117">开发人员上传图像或图像 URL 和 Microsoft 计算机视觉 API 算法分析视觉内容中，基于所选用户，然后可以返回的信息，请输入包括标识的类型和质量的图像的检测人脸 （返回其坐标），并标记，或对图像分类。</span><span class="sxs-lookup"><span data-stu-id="56f6c-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="56f6c-118">有关详细信息，请访问[Azure 计算机视觉 API 页](https://azure.microsoft.com/services/cognitive-services/computer-vision/)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="56f6c-119">已完成本课程，您将具有混合的现实 HoloLens 应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="56f6c-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="56f6c-120">使用手势，HoloLens 的照相机将捕获映像。</span><span class="sxs-lookup"><span data-stu-id="56f6c-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="56f6c-121">图像将发送到 Azure 的计算机视觉 API 服务。</span><span class="sxs-lookup"><span data-stu-id="56f6c-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="56f6c-122">将在 Unity 场景中定位的简单用户界面组中列出识别的对象。</span><span class="sxs-lookup"><span data-stu-id="56f6c-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="56f6c-123">在您的应用程序，它是取决于您关于如何将与您的设计集成结果。</span><span class="sxs-lookup"><span data-stu-id="56f6c-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="56f6c-124">本课程旨在教您如何将 Azure 服务集成与你的 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="56f6c-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="56f6c-125">它是作业以使用此课程以增强混合的现实应用程序中获取的知识。</span><span class="sxs-lookup"><span data-stu-id="56f6c-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="56f6c-126">设备支持</span><span class="sxs-lookup"><span data-stu-id="56f6c-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="56f6c-127">课程</span><span class="sxs-lookup"><span data-stu-id="56f6c-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="56f6c-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="56f6c-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="56f6c-129"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="56f6c-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="56f6c-130">MR 和 Azure 302:计算机视觉</span><span class="sxs-lookup"><span data-stu-id="56f6c-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="56f6c-131">✔️</span><span class="sxs-lookup"><span data-stu-id="56f6c-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="56f6c-132">✔️</span><span class="sxs-lookup"><span data-stu-id="56f6c-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="56f6c-133">尽管本课程主要专注于 HoloLens，您还可以应用到 Windows Mixed Reality 沉浸式 (VR) 耳机本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="56f6c-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="56f6c-134">因为沉浸式 (VR) 耳机不具有可访问照相机，您将需要连接到您的 PC 外部照相机。</span><span class="sxs-lookup"><span data-stu-id="56f6c-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="56f6c-135">按照课程时，您将看到说明您可能需要使用以支持沉浸式 (VR) 耳机的任何更改。</span><span class="sxs-lookup"><span data-stu-id="56f6c-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56f6c-136">系统必备</span><span class="sxs-lookup"><span data-stu-id="56f6c-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="56f6c-137">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="56f6c-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="56f6c-138">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 5 月)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="56f6c-139">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定在此课程中的信息将完全匹配您会发现在较新的软件比下面列出的内容.</span><span class="sxs-lookup"><span data-stu-id="56f6c-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="56f6c-140">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="56f6c-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="56f6c-141">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="56f6c-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="56f6c-142">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="56f6c-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="56f6c-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="56f6c-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="56f6c-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="56f6c-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="56f6c-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="56f6c-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="56f6c-146">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="56f6c-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="56f6c-147">照相机连接到您的 PC （适用于沉浸式头戴式开发）</span><span class="sxs-lookup"><span data-stu-id="56f6c-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="56f6c-148">Internet 访问的 Azure 设置和计算机视觉 API 检索</span><span class="sxs-lookup"><span data-stu-id="56f6c-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="56f6c-149">开始之前</span><span class="sxs-lookup"><span data-stu-id="56f6c-149">Before you start</span></span>

1.  <span data-ttu-id="56f6c-150">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="56f6c-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="56f6c-151">设置和测试你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="56f6c-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="56f6c-152">如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="56f6c-153">它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。</span><span class="sxs-lookup"><span data-stu-id="56f6c-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="56f6c-154">有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="56f6c-155">有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="56f6c-156">第 1 章 – Azure 门户</span><span class="sxs-lookup"><span data-stu-id="56f6c-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="56f6c-157">若要使用*计算机视觉 API*服务在 Azure 中，你将需要配置要成为可用于应用程序的服务的实例。</span><span class="sxs-lookup"><span data-stu-id="56f6c-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="56f6c-158">首先，登录到[Azure 门户](https://portal.azure.com)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="56f6c-159">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="56f6c-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="56f6c-160">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="56f6c-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="56f6c-161">你登录后，单击**新建**在左上角，并搜索*计算机视觉 API*，然后单击**Enter**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![在 Azure 中创建新的资源](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="56f6c-163">单词**新建**可能已替换**创建资源**，较新的门户网站中。</span><span class="sxs-lookup"><span data-stu-id="56f6c-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="56f6c-164">该新页面将提供的说明*计算机视觉 API*服务。</span><span class="sxs-lookup"><span data-stu-id="56f6c-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="56f6c-165">在左下角此页上，选择**创建**按钮，以创建与此服务的关联。</span><span class="sxs-lookup"><span data-stu-id="56f6c-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![有关计算机视觉 api 服务](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="56f6c-167">一旦你单击**创建**:</span><span class="sxs-lookup"><span data-stu-id="56f6c-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="56f6c-168">插入所需**名称**此服务实例。</span><span class="sxs-lookup"><span data-stu-id="56f6c-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="56f6c-169">选择**订阅**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="56f6c-170">选择**定价层**适合您，如果这是首次创建*计算机视觉 API*服务，应可供你免费层 （名为 F0）。</span><span class="sxs-lookup"><span data-stu-id="56f6c-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="56f6c-171">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="56f6c-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="56f6c-172">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="56f6c-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="56f6c-173">建议尽量与常见的资源组下的单个项目 （例如如这些实验室） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="56f6c-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="56f6c-174">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="56f6c-175">（如果要创建新的资源组） 确定你的资源组的位置。</span><span class="sxs-lookup"><span data-stu-id="56f6c-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="56f6c-176">理想情况下，则位置应为该应用程序将运行的区域中。</span><span class="sxs-lookup"><span data-stu-id="56f6c-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="56f6c-177">某些 Azure 资产在特定区域才可用。</span><span class="sxs-lookup"><span data-stu-id="56f6c-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="56f6c-178">您还需要确认你已了解的条款和条件应用于此服务。</span><span class="sxs-lookup"><span data-stu-id="56f6c-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="56f6c-179">单击创建。</span><span class="sxs-lookup"><span data-stu-id="56f6c-179">Click Create.</span></span>

        ![服务创建信息](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="56f6c-181">一旦你单击**创建**，必须要等待的时间来创建服务，这可能需要一分钟。</span><span class="sxs-lookup"><span data-stu-id="56f6c-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="56f6c-182">创建服务实例后，在门户中将显示一条通知。</span><span class="sxs-lookup"><span data-stu-id="56f6c-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![请参阅您的新服务的新通知](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="56f6c-184">单击通知以了解新的服务实例。</span><span class="sxs-lookup"><span data-stu-id="56f6c-184">Click on the notification to explore your new Service instance.</span></span> 

    ![选择转到资源按钮。](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="56f6c-186">单击**转到资源**通知探索新的服务实例中的按钮。</span><span class="sxs-lookup"><span data-stu-id="56f6c-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="56f6c-187">你将转到新的计算机视觉 API 服务实例。</span><span class="sxs-lookup"><span data-stu-id="56f6c-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![新的计算机视觉 API 服务](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="56f6c-189">在本教程中，你的应用程序将需要对你的服务，通过使用服务的订阅密钥来完成进行调用。</span><span class="sxs-lookup"><span data-stu-id="56f6c-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="56f6c-190">从*快速入门*页上的你*计算机视觉 API*服务，，请导航到的第一步*捕捉密钥*，然后单击**密钥**(也可以在此通过单击蓝色超链接密钥，位于服务导航菜单中，由密钥图标表示）。</span><span class="sxs-lookup"><span data-stu-id="56f6c-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="56f6c-191">此时会显示你的服务*密钥*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="56f6c-192">需要一份某个显示的密钥，因为你将需要此更高版本中您的项目。</span><span class="sxs-lookup"><span data-stu-id="56f6c-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="56f6c-193">返回到*快速入门*页上，并从中提取你的终结点。</span><span class="sxs-lookup"><span data-stu-id="56f6c-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="56f6c-194">请注意您可能会有所不同，具体取决于你的区域 (这是，如果需要更高版本对代码进行更改)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="56f6c-195">获取供以后使用此终结点的副本：</span><span class="sxs-lookup"><span data-stu-id="56f6c-195">Take a copy of this endpoint for use later:</span></span>

    ![新的计算机视觉 API 服务](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="56f6c-197">你可以检查各个终结点是什么[此处](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="56f6c-198">第 2 章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="56f6c-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="56f6c-199">以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="56f6c-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="56f6c-200">打开*Unity*然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-200">Open *Unity* and click **New**.</span></span> 

    ![启动新的 Unity 项目。](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="56f6c-202">现在，需要提供 Unity 项目的名称。</span><span class="sxs-lookup"><span data-stu-id="56f6c-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="56f6c-203">插入**MR_ComputerVision**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="56f6c-204">请确保项目类型设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="56f6c-205">设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="56f6c-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="56f6c-206">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-206">Then, click **Create project**.</span></span>

    ![提供新的 Unity 项目的详细信息。](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="56f6c-208">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="56f6c-209">转到**编辑 > 首选项**，然后在新窗口中，导航到**外部工具**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="56f6c-210">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="56f6c-211">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="56f6c-211">Close the **Preferences** window.</span></span>

    ![更新脚本编辑器首选项。](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="56f6c-213">接下来，请转到**文件 > 生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。</span><span class="sxs-lookup"><span data-stu-id="56f6c-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![生成设置窗口中，切换到 UWP 的平台。](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="56f6c-215">在仍处于**文件 > 生成设置**并确保选中：</span><span class="sxs-lookup"><span data-stu-id="56f6c-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="56f6c-216">**设备为目标**设置为**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="56f6c-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="56f6c-217">对于沉浸式耳机，设置**目标设备**到*任一设备*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="56f6c-218">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="56f6c-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="56f6c-219">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="56f6c-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="56f6c-220">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="56f6c-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="56f6c-221">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="56f6c-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="56f6c-222">保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="56f6c-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="56f6c-223">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="56f6c-224">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="56f6c-224">A save window will appear.</span></span>
        
            ![单击添加打开场景按钮](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="56f6c-226">创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![创建新的 scripts 文件夹](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="56f6c-228">打开新建**场景**文件夹，然后在*文件名*： 文本字段中，键入**MR_ComputerVisionScene**，然后单击**保存**.</span><span class="sxs-lookup"><span data-stu-id="56f6c-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![为新的场景提供一个名称。](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="56f6c-230">请注意，必须将保存您的 Unity 场景中*资产*文件夹中，因为它们必须与 Unity 项目相关联。</span><span class="sxs-lookup"><span data-stu-id="56f6c-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="56f6c-231">创建场景文件夹 （和其他类似的文件夹） 是用于结构化的 Unity 项目的典型方式。</span><span class="sxs-lookup"><span data-stu-id="56f6c-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="56f6c-232">中的剩余设置，*生成设置*，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="56f6c-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="56f6c-233">在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。</span><span class="sxs-lookup"><span data-stu-id="56f6c-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![打开播放器设置。](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="56f6c-235">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="56f6c-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="56f6c-236">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="56f6c-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="56f6c-237">**脚本运行时版本**应**稳定**（.NET 3.5 等效）。</span><span class="sxs-lookup"><span data-stu-id="56f6c-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="56f6c-238">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="56f6c-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="56f6c-239">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="56f6c-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![更新其他设置。](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="56f6c-241">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="56f6c-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="56f6c-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="56f6c-242">**InternetClient**</span></span>
        2. <span data-ttu-id="56f6c-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="56f6c-243">**Webcam**</span></span>

            ![正在更新的发布设置。](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="56f6c-245">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。</span><span class="sxs-lookup"><span data-stu-id="56f6c-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![更新的 X R 设置。](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="56f6c-247">回到*生成设置* _Unity C#_ 项目不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="56f6c-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="56f6c-248">关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="56f6c-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="56f6c-249">保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="56f6c-250">第 3 章 – 主照相机设置</span><span class="sxs-lookup"><span data-stu-id="56f6c-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56f6c-251">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)，将其导入项目中，作为[自定义包](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 5 章：](#chapter-5--create-the-resultslabel-class)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="56f6c-252">在中*层次结构面板*，选择**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="56f6c-253">选择后，你将能够看到的所有组件**Main Camera**中*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="56f6c-254">**相机对象**必须命名为**Main Camera** （请注意拼写 ！）</span><span class="sxs-lookup"><span data-stu-id="56f6c-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="56f6c-255">Main Camera**标记**必须设置为**MainCamera** （请注意拼写 ！）</span><span class="sxs-lookup"><span data-stu-id="56f6c-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="56f6c-256">请确保**转换位置**设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="56f6c-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="56f6c-257">设置**清除标志**到**纯色**（忽略这的沉浸式头戴式耳机）。</span><span class="sxs-lookup"><span data-stu-id="56f6c-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="56f6c-258">设置**背景**照相机组件到色**黑色、 Alpha 0 (十六进制代码: #00000000)** （忽略这的沉浸式头戴式耳机）。</span><span class="sxs-lookup"><span data-stu-id="56f6c-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![更新相机组件。](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="56f6c-260">接下来，需要创建附加到一个简单的"游标"对象**Main Camera**，这将帮助你放置图像分析输出运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="56f6c-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="56f6c-261">此游标将确定摄像机焦点的中心点。</span><span class="sxs-lookup"><span data-stu-id="56f6c-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="56f6c-262">若要创建该游标：</span><span class="sxs-lookup"><span data-stu-id="56f6c-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="56f6c-263">在中*层次结构面板*，右键单击**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="56f6c-264">下**3D 物体**，单击**球体**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![选择光标对象。](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="56f6c-266">重命名**球体**到**光标**（双击光标对象或与所选对象按 F2 键盘按钮），并确保它位于作为子级**Main Camera**.</span><span class="sxs-lookup"><span data-stu-id="56f6c-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="56f6c-267">在中*层次结构面板*，在单击鼠标左键**光标**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="56f6c-268">选择光标，调整中的以下变量*检查器面板*:</span><span class="sxs-lookup"><span data-stu-id="56f6c-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="56f6c-269">设置*转换位置*到**0，0，5**</span><span class="sxs-lookup"><span data-stu-id="56f6c-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="56f6c-270">设置*规模*到**0.02、 0.02、 0.02**</span><span class="sxs-lookup"><span data-stu-id="56f6c-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![更新的转换位置和小数位数。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="56f6c-272">第 4 章-设置标签系统</span><span class="sxs-lookup"><span data-stu-id="56f6c-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="56f6c-273">该映像后使用 HoloLens 的照相机中捕获了映像，将发送到您*Azure 计算机视觉 API*服务实例以进行分析。</span><span class="sxs-lookup"><span data-stu-id="56f6c-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="56f6c-274">该分析的结果将是一系列已识别的对象调用**标记**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="56f6c-275">将使用标签 （作为全局空间中三维文字），要在拍摄照片的位置显示这些标记。</span><span class="sxs-lookup"><span data-stu-id="56f6c-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="56f6c-276">以下步骤将演示如何设置**标签**对象。</span><span class="sxs-lookup"><span data-stu-id="56f6c-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="56f6c-277">在层次结构窗格中 （位置并不重要此时），在任意位置右击**3D 物体**，添加**三维文字**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="56f6c-278">其命名为**LabelText**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-278">Name it **LabelText**.</span></span>

    ![创建三维文本对象。](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="56f6c-280">在中*层次结构面板*，在单击鼠标左键**LabelText**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="56f6c-281">与**LabelText**选择，调整中的以下变量*检查器面板*:</span><span class="sxs-lookup"><span data-stu-id="56f6c-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="56f6c-282">设置**位置**到**0,0,0**</span><span class="sxs-lookup"><span data-stu-id="56f6c-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="56f6c-283">设置**规模**到**0.01，0.01，0.01**</span><span class="sxs-lookup"><span data-stu-id="56f6c-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="56f6c-284">组件中**文本 Mesh**:</span><span class="sxs-lookup"><span data-stu-id="56f6c-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="56f6c-285">替换中的所有文本**文本**，使用"..."</span><span class="sxs-lookup"><span data-stu-id="56f6c-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="56f6c-286">设置**定位点**到**中间 Center**</span><span class="sxs-lookup"><span data-stu-id="56f6c-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="56f6c-287">设置**对齐**到**Center**</span><span class="sxs-lookup"><span data-stu-id="56f6c-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="56f6c-288">设置**选项卡大小**到**4**</span><span class="sxs-lookup"><span data-stu-id="56f6c-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="56f6c-289">设置**字号**到**50**</span><span class="sxs-lookup"><span data-stu-id="56f6c-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="56f6c-290">设置**颜色**到 **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="56f6c-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![文本组件](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="56f6c-292">拖动**LabelText**从*层次结构面板*，为*资产文件夹*，在中*项目面板*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="56f6c-293">这将使**LabelText**预设，因此它可以在代码中实例化。</span><span class="sxs-lookup"><span data-stu-id="56f6c-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![创建 LabelText 对象的预设。](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="56f6c-295">应删除**LabelText**从*层次结构面板*，以便打开场景中将不会显示。</span><span class="sxs-lookup"><span data-stu-id="56f6c-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="56f6c-296">因为它现在是预设，您将从资产文件夹调用的单独实例，没有无需将其保持在场景。</span><span class="sxs-lookup"><span data-stu-id="56f6c-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="56f6c-297">中的最后一个对象结构*层次结构面板*应类似于下图中所示：</span><span class="sxs-lookup"><span data-stu-id="56f6c-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![层次结构面板的最终结构。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="56f6c-299">第 5 章-创建 ResultsLabel 类</span><span class="sxs-lookup"><span data-stu-id="56f6c-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="56f6c-300">您需要创建的第一个脚本是*ResultsLabel*类，该类负责以下：</span><span class="sxs-lookup"><span data-stu-id="56f6c-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="56f6c-301">在适当的世界空间中，相对于照相机的位置中创建标签。</span><span class="sxs-lookup"><span data-stu-id="56f6c-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="56f6c-302">显示从映像解放标记。</span><span class="sxs-lookup"><span data-stu-id="56f6c-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="56f6c-303">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="56f6c-303">To create this class:</span></span> 

1.  <span data-ttu-id="56f6c-304">在中右击*项目面板*，然后**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="56f6c-305">将文件夹命名为**脚本**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-305">Name the folder **Scripts**.</span></span> 

    ![创建脚本的文件夹。](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="56f6c-307">与**脚本**文件夹中创建，双击它打开。</span><span class="sxs-lookup"><span data-stu-id="56f6c-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="56f6c-308">然后在该文件夹，右键单击，并选择**创建 >** 然后**C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="56f6c-309">脚本命名为*ResultsLabel*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="56f6c-310">双击新*ResultsLabel*脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="56f6c-311">在类中插入下面的代码*ResultsLabel*类：</span><span class="sxs-lookup"><span data-stu-id="56f6c-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

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

6.  <span data-ttu-id="56f6c-312">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="56f6c-313">回到*Unity 编辑器*，单击并拖动*ResultsLabel*类**脚本**文件夹**Main Camera**中对象*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="56f6c-314">单击**Main Camera**并查看*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="56f6c-315">您将注意到，您只需拖放到相机的脚本，还有两个字段：**游标**并**标签 Prefab**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="56f6c-316">拖动对象调用**游标**从*层次结构面板*到名为槽**游标**，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="56f6c-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="56f6c-317">拖动对象调用**LabelText**从*Assets 文件夹*中*项目面板*到名为槽**标签 Prefab**，如中所示下图所示。</span><span class="sxs-lookup"><span data-stu-id="56f6c-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![设置在 Unity 中的引用目标。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="56f6c-319">第 6 章-创建 ImageCapture 类</span><span class="sxs-lookup"><span data-stu-id="56f6c-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="56f6c-320">要创建的下一步类是*ImageCapture*类。</span><span class="sxs-lookup"><span data-stu-id="56f6c-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="56f6c-321">此类负责：</span><span class="sxs-lookup"><span data-stu-id="56f6c-321">This class is responsible for:</span></span>

-   <span data-ttu-id="56f6c-322">捕获映像使用 HoloLens 相机并将其存储在应用程序文件夹中。</span><span class="sxs-lookup"><span data-stu-id="56f6c-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="56f6c-323">捕获来自用户的点击手势。</span><span class="sxs-lookup"><span data-stu-id="56f6c-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="56f6c-324">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="56f6c-324">To create this class:</span></span> 

1.  <span data-ttu-id="56f6c-325">转到**脚本**之前创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="56f6c-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="56f6c-326">在文件夹中，右键单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="56f6c-327">调用脚本*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="56f6c-328">双击新*ImageCapture*脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="56f6c-329">将以下命名空间添加到文件顶部：</span><span class="sxs-lookup"><span data-stu-id="56f6c-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="56f6c-330">然后添加以下变量内的*ImageCapture*类，更高版本*start （)* 方法：</span><span class="sxs-lookup"><span data-stu-id="56f6c-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="56f6c-331">**TapsCount**变量将存储捕获来自用户的点击手势的号。</span><span class="sxs-lookup"><span data-stu-id="56f6c-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="56f6c-332">此编号使用命名的捕获的映像中。</span><span class="sxs-lookup"><span data-stu-id="56f6c-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="56f6c-333">为代码*Awake()* 并*start （)* 方法现在需要添加。</span><span class="sxs-lookup"><span data-stu-id="56f6c-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="56f6c-334">类初始化时将会调用：</span><span class="sxs-lookup"><span data-stu-id="56f6c-334">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="56f6c-335">实现的点击动作时将调用的处理程序。</span><span class="sxs-lookup"><span data-stu-id="56f6c-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

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
 
<span data-ttu-id="56f6c-336">*TapHandler()* 方法递增捕获来自用户的点击数，并使用当前光标位置以确定要将新的标签位置。</span><span class="sxs-lookup"><span data-stu-id="56f6c-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="56f6c-337">然后，此方法调用*ExecuteImageCaptureAndAnalysis()* 方法开始此应用程序的核心功能。</span><span class="sxs-lookup"><span data-stu-id="56f6c-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="56f6c-338">一旦已捕获并存储映像，将调用以下处理程序。</span><span class="sxs-lookup"><span data-stu-id="56f6c-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="56f6c-339">如果该过程成功，将结果传递给*VisionManager* （即你尚未创建） 以进行分析。</span><span class="sxs-lookup"><span data-stu-id="56f6c-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

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
 
9.  <span data-ttu-id="56f6c-340">然后添加该应用程序使用启动映像捕获过程并存储映像的方法。</span><span class="sxs-lookup"><span data-stu-id="56f6c-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

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
> <span data-ttu-id="56f6c-341">此时你会注意到出现在错误*Unity 编辑器控制台面板*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="56f6c-342">这是因为该代码引用*VisionManager*将在下一章中创建的类。</span><span class="sxs-lookup"><span data-stu-id="56f6c-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="56f6c-343">第 7 章 – 对 Azure 和图像分析的调用</span><span class="sxs-lookup"><span data-stu-id="56f6c-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="56f6c-344">若要创建所需的最后一个脚本是*VisionManager*类。</span><span class="sxs-lookup"><span data-stu-id="56f6c-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="56f6c-345">此类负责：</span><span class="sxs-lookup"><span data-stu-id="56f6c-345">This class is responsible for:</span></span>

-   <span data-ttu-id="56f6c-346">正在加载最新的映像捕获为一个字节数组。</span><span class="sxs-lookup"><span data-stu-id="56f6c-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="56f6c-347">发送到的字节数组你*Azure 计算机视觉 API*服务实例以进行分析。</span><span class="sxs-lookup"><span data-stu-id="56f6c-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="56f6c-348">接收响应以 JSON 字符串。</span><span class="sxs-lookup"><span data-stu-id="56f6c-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="56f6c-349">反序列化响应并将传递到生成的标记*ResultsLabel*类。</span><span class="sxs-lookup"><span data-stu-id="56f6c-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="56f6c-350">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="56f6c-350">To create this class:</span></span>

1.  <span data-ttu-id="56f6c-351">双击**脚本**文件夹，将其打开。</span><span class="sxs-lookup"><span data-stu-id="56f6c-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="56f6c-352">内右击**脚本**文件夹中，单击**创建 >C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="56f6c-353">脚本命名为*VisionManager*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="56f6c-354">双击要使用 Visual Studio 中打开的新脚本。</span><span class="sxs-lookup"><span data-stu-id="56f6c-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="56f6c-355">更新命名空间，如下所示，在顶部相同*VisionManager*类：</span><span class="sxs-lookup"><span data-stu-id="56f6c-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="56f6c-356">在脚本顶部*内* *VisionManager*类 (上面*start （)* 方法)，现在需要创建两个*类*，将表示 Azure 的反序列化的 JSON 响应：</span><span class="sxs-lookup"><span data-stu-id="56f6c-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

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
    > <span data-ttu-id="56f6c-357">*TagData*并*AnalysedObject*类都必须具有 *[System.Serializable]* 的声明，以便能够使用 Unity 进行反序列化之前添加属性库。</span><span class="sxs-lookup"><span data-stu-id="56f6c-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="56f6c-358">在 VisionManager 类中，应添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="56f6c-358">In the VisionManager class, you should add the following variables:</span></span>

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
    > <span data-ttu-id="56f6c-359">请确保插入你**身份验证密钥**成**authorizationKey**变量。</span><span class="sxs-lookup"><span data-stu-id="56f6c-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="56f6c-360">你将已记下你**身份验证密钥**在本课程中，开头[第 1 章](#chapter-1--the-azure-portal)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="56f6c-361">**VisionAnalysisEndpoint**变量可能不同于在此示例中指定。</span><span class="sxs-lookup"><span data-stu-id="56f6c-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="56f6c-362">**西部-我们**严格地指的是为美国西部区域创建的服务实例。</span><span class="sxs-lookup"><span data-stu-id="56f6c-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="56f6c-363">更新此与您[终结点 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); 此处的一些示例可能如下所示的是：</span><span class="sxs-lookup"><span data-stu-id="56f6c-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="56f6c-364">欧洲西部： `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="56f6c-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="56f6c-365">亚洲东南部： `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="56f6c-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="56f6c-366">澳大利亚东部： `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="56f6c-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="56f6c-367">Awake 现在需要添加代码。</span><span class="sxs-lookup"><span data-stu-id="56f6c-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="56f6c-368">接下来，添加协同程序 （使用其下方的静态流方法），将获取由捕获映像的分析结果*ImageCapture*类。</span><span class="sxs-lookup"><span data-stu-id="56f6c-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

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

9.  <span data-ttu-id="56f6c-369">请务必保存中所做的更改*Visual Studio*才会回到*Unity*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="56f6c-370">返回在 Unity 编辑器中，单击并拖动*VisionManager*并*ImageCapture*类**脚本**文件夹到**Main Camera**中的对象*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="56f6c-371">第 8 章 – 生成前</span><span class="sxs-lookup"><span data-stu-id="56f6c-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="56f6c-372">若要执行全面测试您的应用程序将需要旁加载它到在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="56f6c-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="56f6c-373">执行操作之前，请确保：</span><span class="sxs-lookup"><span data-stu-id="56f6c-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="56f6c-374">中所述的所有设置[第 2 章](#chapter-2--set-up-the-unity-project)正确设置。</span><span class="sxs-lookup"><span data-stu-id="56f6c-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="56f6c-375">所有脚本都附加到**Main Camera**对象。</span><span class="sxs-lookup"><span data-stu-id="56f6c-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="56f6c-376">中的所有字段*主相机检查器面板*正确分配。</span><span class="sxs-lookup"><span data-stu-id="56f6c-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="56f6c-377">请确保插入你**身份验证密钥**成**authorizationKey**变量。</span><span class="sxs-lookup"><span data-stu-id="56f6c-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="56f6c-378">确保具有还检查你的终结点您*VisionManager*脚本，并与对齐*你*区域 (本文档使用*西-我们*默认情况下)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="56f6c-379">章 9 – 生成 UWP 解决方案和旁加载应用程序</span><span class="sxs-lookup"><span data-stu-id="56f6c-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="56f6c-380">此项目的 Unity 部分所需的所有内容现已完成，因此它是从 Unity 生成的时间。</span><span class="sxs-lookup"><span data-stu-id="56f6c-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="56f6c-381">导航到*生成设置* - **文件 > 生成设置...**</span><span class="sxs-lookup"><span data-stu-id="56f6c-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="56f6c-382">从*生成设置*窗口中，单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-382">From the *Build Settings* window, click **Build**.</span></span>

    ![从 Unity 构建应用程序](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="56f6c-384">如果尚不存在，则勾选**UnityC#项目**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="56f6c-385">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="56f6c-385">Click **Build**.</span></span> <span data-ttu-id="56f6c-386">将启动 unity*文件资源管理器*窗口中，需要创建，然后选择要生成该应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="56f6c-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="56f6c-387">现在，创建该文件夹并将其命名*应用*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="56f6c-388">然后使用*应用程序*文件夹选择，按**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="56f6c-389">Unity 将开始构建您的项目*应用*文件夹。</span><span class="sxs-lookup"><span data-stu-id="56f6c-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="56f6c-390">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开*文件资源管理器*窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="56f6c-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="56f6c-391">第 10 章将部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="56f6c-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="56f6c-392">若要部署在 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="56f6c-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="56f6c-393">你将 （适用于远程部署），需要在 HoloLens IP 地址，以确保你 HoloLens 处于**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="56f6c-394">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="56f6c-394">To do this:</span></span>

    1. <span data-ttu-id="56f6c-395">戴上您 HoloLens，同时打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="56f6c-396">转到**网络和 Internet > 的 Wi-fi > 高级选项**</span><span class="sxs-lookup"><span data-stu-id="56f6c-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="56f6c-397">请注意**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="56f6c-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="56f6c-398">接下来，导航回到**设置**，然后**更新和安全 > 适用于开发人员**</span><span class="sxs-lookup"><span data-stu-id="56f6c-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="56f6c-399">设置开发人员模式。</span><span class="sxs-lookup"><span data-stu-id="56f6c-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="56f6c-400">导航到新的 Unity 生成 (*应用程序*文件夹)，然后打开解决方案文件与*Visual Studio*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="56f6c-401">在解决方案配置中，选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="56f6c-402">在解决方案平台中，选择**x86**，**远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![部署从 Visual Studio 解决方案。](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="56f6c-404">转到**生成菜单**，然后单击**部署解决方案**旁, 加载到你 HoloLens 应用程序。</span><span class="sxs-lookup"><span data-stu-id="56f6c-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="56f6c-405">在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！</span><span class="sxs-lookup"><span data-stu-id="56f6c-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="56f6c-406">若要将部署到沉浸式头戴式耳机，设置**解决方案平台**到*本地计算机*，并设置**配置**到*调试*，与*x86*作为**平台**。</span><span class="sxs-lookup"><span data-stu-id="56f6c-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="56f6c-407">然后将其部署到本地计算机，使用**生成菜单**，选择*部署解决方案*。</span><span class="sxs-lookup"><span data-stu-id="56f6c-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="56f6c-408">完成的计算机视觉 API 的应用程序</span><span class="sxs-lookup"><span data-stu-id="56f6c-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="56f6c-409">祝贺你，构建利用 Azure 计算机视觉 API 能够识别现实世界对象，并显示的内容出现的置信度的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="56f6c-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![实验结果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="56f6c-411">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="56f6c-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="56f6c-412">练习 1</span><span class="sxs-lookup"><span data-stu-id="56f6c-412">Exercise 1</span></span>

<span data-ttu-id="56f6c-413">正如您使用过*标记*参数 (如内*终结点*中使用*VisionManager*)，扩展应用程序以检测其他信息; 我们来看一下有权访问的其他参数[此处](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)。</span><span class="sxs-lookup"><span data-stu-id="56f6c-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="56f6c-414">练习 2</span><span class="sxs-lookup"><span data-stu-id="56f6c-414">Exercise 2</span></span>

<span data-ttu-id="56f6c-415">显示返回的 Azure 数据，以更便于交谈，和可读的方式，可能隐藏的数字。</span><span class="sxs-lookup"><span data-stu-id="56f6c-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="56f6c-416">像智能机器人应用程序可能会对用户说话。</span><span class="sxs-lookup"><span data-stu-id="56f6c-416">As though a bot might be speaking to the user.</span></span>
