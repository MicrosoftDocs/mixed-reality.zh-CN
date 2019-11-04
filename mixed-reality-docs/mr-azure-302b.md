---
title: MR 和 Azure 302b-自定义构想
description: 完成本课程，了解如何训练机器学习模型，然后使用训练的模型识别混合现实应用程序内的类似对象。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure，混合现实，学院，unity，教程，api，自定义视觉，hololens，沉浸，vr
ms.openlocfilehash: 2c8bd31958cca3b0e27fb0e97839d75fcdebe8c5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438517"
---
>[!NOTE]
><span data-ttu-id="c3cc4-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c3cc4-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c3cc4-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c3cc4-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c3cc4-108">将来会发布一系列新教程，这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c3cc4-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="c3cc4-110">MR 和 Azure 302b：自定义视觉</span><span class="sxs-lookup"><span data-stu-id="c3cc4-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="c3cc4-111">在本课程中，你将了解如何在混合现实应用程序中使用 Azure 自定义视觉功能，识别提供的映像中的自定义视觉对象内容。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="c3cc4-112">此服务允许你使用对象图像训练机器学习模型。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="c3cc4-113">然后，你将使用训练的模型来识别类似对象，这些对象由 Microsoft HoloLens 的相机捕获或连接到你的电脑以用于沉浸式（VR）耳机提供。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![课程结果](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="c3cc4-115">Azure 自定义视觉是一种 Microsoft 认知服务，允许开发人员构建自定义映像分类器。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="c3cc4-116">然后，可以将这些分类器与新图像一起使用，以识别或分类该新图像中的对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="c3cc4-117">此服务提供简单易用的联机门户来简化流程。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="c3cc4-118">有关详细信息，请访问[Azure 自定义影像服务页](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="c3cc4-119">完成本课程后，你将拥有一个混合现实应用程序，可以在两种模式下工作：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="c3cc4-120">**分析模式**：通过上传图像、创建标记以及训练服务来识别不同的对象（在本例中为鼠标和键盘），手动设置自定义影像服务。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="c3cc4-121">然后，将创建一个将使用相机捕获图像的 HoloLens 应用，并尝试识别真实环境中的对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="c3cc4-122">**定型模式**：将实现在应用中启用 "定型模式" 的代码。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="c3cc4-123">训练模式允许使用 HoloLens 相机捕获图像，将捕获的图像上传到服务，并训练自定义视觉模型。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="c3cc4-124">本课程将介绍如何将自定义影像服务中的结果获取到基于 Unity 的示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="c3cc4-125">您可以将这些概念应用到您可能生成的自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="c3cc4-126">设备支持</span><span class="sxs-lookup"><span data-stu-id="c3cc4-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c3cc4-127">摘要</span><span class="sxs-lookup"><span data-stu-id="c3cc4-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c3cc4-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c3cc4-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c3cc4-129"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="c3cc4-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c3cc4-130">MR 和 Azure 302b：自定义视觉</span><span class="sxs-lookup"><span data-stu-id="c3cc4-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3cc4-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c3cc4-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3cc4-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c3cc4-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c3cc4-133">尽管本课程主要侧重于 HoloLens，但你也可以将本课程中学习的内容应用于 Windows Mixed Reality 沉浸（VR）耳机。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="c3cc4-134">由于沉浸式（VR）耳机没有可访问的摄像机，因此需要连接到电脑的外部照相机。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="c3cc4-135">在本课程中，您将看到有关支持沉浸式（VR）耳机时可能需要执行的任何更改的说明。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3cc4-136">必备条件</span><span class="sxs-lookup"><span data-stu-id="c3cc4-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c3cc4-137">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c3cc4-138">另外，请注意，本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容（2018年7月）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="c3cc4-139">你可以随意使用最新的软件（如[安装工具](install-the-tools.md)一文中所述），但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="c3cc4-140">本课程建议采用以下硬件和软件：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c3cc4-141">[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)的开发 PC，用于沉浸式（VR）耳机开发</span><span class="sxs-lookup"><span data-stu-id="c3cc4-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c3cc4-142">Windows 10 秋季创意者更新（或更高版本）已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="c3cc4-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c3cc4-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c3cc4-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c3cc4-144">Unity 2017。4</span><span class="sxs-lookup"><span data-stu-id="c3cc4-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c3cc4-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c3cc4-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="c3cc4-146">启用了开发人员模式的[Windows Mixed Reality 沉浸式（VR）耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="c3cc4-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c3cc4-147">连接到电脑的相机（适用于沉浸式耳机开发）</span><span class="sxs-lookup"><span data-stu-id="c3cc4-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="c3cc4-148">Azure 安装和自定义视觉 API 检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="c3cc4-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="c3cc4-149">对于想要自定义影像服务识别的每个对象，必须有一系列至少五（5）个映像（为10（10））。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="c3cc4-150">如果需要，可以使用[本课程提供的映像（计算机鼠标和键盘） ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c3cc4-151">开始之前</span><span class="sxs-lookup"><span data-stu-id="c3cc4-151">Before you start</span></span>

1.  <span data-ttu-id="c3cc4-152">为避免在生成此项目时遇到问题，强烈建议您在本教程中的根或根文件夹中创建项目（长文件夹路径可能会在生成时导致问题）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="c3cc4-153">设置并测试你的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="c3cc4-154">如果需要支持设置 HoloLens，请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="c3cc4-155">在开始开发新的 HoloLens 应用程序时，最好执行校准和传感器调整（有时它可以帮助为每个用户执行这些任务）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="c3cc4-156">有关校准的帮助信息，请单击此链接，了解[到 HoloLens 校准文章](calibration.md#hololens-2)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="c3cc4-157">有关传感器优化的帮助，请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="c3cc4-158">第1章-自定义影像服务门户</span><span class="sxs-lookup"><span data-stu-id="c3cc4-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="c3cc4-159">若要在 Azure 中使用*自定义影像服务*，你将需要配置服务的实例，使其可用于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="c3cc4-160">首先，[导航到*自定义影像服务*主页](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="c3cc4-161">单击 "**开始**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="c3cc4-162">登录到*自定义影像服务*门户。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="c3cc4-163">如果还没有 Azure 帐户，则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c3cc4-164">如果在课堂或实验室中按照本教程进行学习，请咨询教师或 proctors，以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="c3cc4-165">首次登录后，系统会提示 "*服务*" 面板。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="c3cc4-166">单击相应的复选框以同意条款。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="c3cc4-167">然后单击 "**我同意**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="c3cc4-168">同意这些条款后，你将会导航到门户的 "*项目*" 部分。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="c3cc4-169">单击 "**新建项目**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="c3cc4-170">右侧将显示一个选项卡，该选项卡将提示你为项目指定某些字段。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="c3cc4-171">插入项目的*名称*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="c3cc4-172">为项目插入*说明*（*可选*）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="c3cc4-173">选择一个*资源组*，或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="c3cc4-174">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c3cc4-175">建议将所有与单个项目关联的 Azure 服务（如这些课程）保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="c3cc4-176">将*项目类型*设置为**分类**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="c3cc4-177">将*域*设置为 "**常规**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="c3cc4-178">若要了解有关 Azure 资源组的详细信息，请[访问资源组一文](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="c3cc4-179">完成后，单击 "**创建项目**"，你会被重定向到自定义影像服务，"项目" 页。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="c3cc4-180">第2章-培训自定义视觉项目</span><span class="sxs-lookup"><span data-stu-id="c3cc4-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="c3cc4-181">在自定义视觉门户中，你的主要目标是训练你的项目以识别图像中的特定对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="c3cc4-182">对于你希望应用程序识别的每个对象，你需要至少五（5）个映像，但最好是十（10）个映像。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="c3cc4-183">[您可以使用本课程提供的图像（计算机鼠标和键盘）](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="c3cc4-184">训练自定义影像服务项目：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="c3cc4-185">单击 "标记" 旁边的 " **+** " 按钮 **。**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="c3cc4-186">添加要识别的对象的**名称**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="c3cc4-187">单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="c3cc4-188">你将注意到已添加**标记**（可能需要重新加载页面以使其显示）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="c3cc4-189">单击新标记旁边的复选框（如果尚未选中）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="c3cc4-190">单击页中心的 "**添加图像**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="c3cc4-191">单击 "**浏览本地文件**"，然后选择 "要上传的映像"，然后选择 "最小为五（5）"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="c3cc4-192">请记住，这些映像应该包含您正在训练的对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c3cc4-193">你可以一次选择多个图像来上传。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="c3cc4-194">在选项卡中看到图像后，请在 "**我的标记**" 框中选择相应的标记。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="c3cc4-195">单击 "上**传文件**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-195">Click on **Upload files**.</span></span> <span data-ttu-id="c3cc4-196">文件将开始上传。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-196">The files will begin uploading.</span></span> <span data-ttu-id="c3cc4-197">确认上传后，单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="c3cc4-198">重复相同的过程，创建名为 "**键盘**" 的新**标记**，并为其上传适当的照片。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="c3cc4-199">请确保在创建新标记后\**取消选中\*\*\*鼠标*，以便显示 "*添加映像*" 窗口。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="c3cc4-200">设置两个标记后，单击 "**训练**"，第一次训练迭代将开始生成。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="c3cc4-201">构建后，你将能够看到两个称为 "**创建默认值**和**预测 URL**" 的按钮。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="c3cc4-202">先单击 "**设为默认值**"，然后单击 "**预测 URL**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="c3cc4-203">从此提供的端点 URL 设置为标记为默认值的任何*迭代*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="c3cc4-204">这种情况下，如果您以后生成新的*迭代*并将其更新为默认值，则无需更改代码。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="c3cc4-205">单击 "*预测 URL*" 后，打开 "*记事本*"，复制并粘贴该**url**和**预测密钥**，以便稍后在代码中需要时进行检索。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="c3cc4-206">单击屏幕右上角的**齿轮**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="c3cc4-207">复制**定型密钥**，并将其粘贴到*记事本*中供以后使用。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="c3cc4-208">还应复制**项目 Id**，并将其粘贴到*记事本*文件中供以后使用。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="c3cc4-209">第3章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="c3cc4-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="c3cc4-210">下面是用于使用混合现实进行开发的典型设置，因此，这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c3cc4-211">打开*Unity* ，并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="c3cc4-212">现在需要提供 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="c3cc4-213">插入**AzureCustomVision。**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="c3cc4-214">请确保将项目模板设置为**3d**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="c3cc4-215">将位置设置为合适的**位置**（请记住，更接近根目录更好）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c3cc4-216">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="c3cc4-217">当 Unity 处于打开状态时，有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c3cc4-218">转到 " **编辑* > *首选项** "，然后在新窗口中导航到 "**外部工具**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c3cc4-219">将**外部脚本编辑器**更改为**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c3cc4-220">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="c3cc4-221">接下来，转到 "**文件 > 生成设置**"，选择 "**通用 Windows 平台**"，然后单击 "**切换平台**" 按钮以应用所选内容。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="c3cc4-222">尽管仍处于**文件 > 生成设置**，但请确保：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="c3cc4-223">**目标设备**设置为**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-223">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="c3cc4-224">对于沉浸式耳机，将 "**目标设备**" 设置为 "*任何设备*"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="c3cc4-225">**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="c3cc4-226">**SDK**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="c3cc4-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="c3cc4-227">**Visual Studio 版本**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="c3cc4-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="c3cc4-228">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="c3cc4-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="c3cc4-229">保存场景并将其添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="c3cc4-230">通过选择 "**添加打开的场景**" 来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="c3cc4-231">将显示 "保存" 窗口。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="c3cc4-232">为此创建新文件夹，并为将来的任何场景创建一个新文件夹，然后选择 "**新建文件夹**" 按钮以创建新文件夹，将其命名为**场景**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="c3cc4-233">打开新创建的**场景**文件夹，然后在 "文件名 *：* 文本" 字段中，键入**CustomVisionScene**，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="c3cc4-234">请注意，必须将 Unity 场景保存在 "*资产*" 文件夹中，因为它们必须与 Unity 项目相关联。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="c3cc4-235">创建场景文件夹（以及其他类似文件夹）是构造 Unity 项目的典型方式。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="c3cc4-236">现在，"*生成设置*" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="c3cc4-237">在 "*生成设置*" 窗口中，单击 "**播放机设置**" 按钮，这会在*检查器*所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="c3cc4-238">在此面板中，需要验证几项设置：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="c3cc4-239">在 "**其他设置**" 选项卡中：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="c3cc4-240">**脚本运行时版本**应为试验性的 **（.Net 4.6 等效项）** ，这会触发重新启动编辑器的需要。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="c3cc4-241">**脚本编写后端**应为 **.net**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="c3cc4-242">**API 兼容级别**应为 **.net 4.6**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="c3cc4-243">在 "**发布设置**" 选项卡的 "**功能**" 下，检查：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="c3cc4-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="c3cc4-245">**摄像头**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-245">**Webcam**</span></span>

        3. <span data-ttu-id="c3cc4-246">**十分**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="c3cc4-247">在面板中，在 " **XR" 设置**（位于 "**发布设置**" 下）中，在 "**支持的虚拟现实**" 下，确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="c3cc4-248">返回*生成设置* *Unity C\# 项目*不再灰显;勾选此的旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="c3cc4-249">关闭 "生成设置" 窗口。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="c3cc4-250">保存场景和项目（**file > SAVE 场景/file > SAVE project**）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="c3cc4-251">第4章-导入 Unity 中的 Newtonsoft.json DLL</span><span class="sxs-lookup"><span data-stu-id="c3cc4-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3cc4-252">如果要跳过本课程的*Unity 设置*组件，并继续直接进入代码，请随时下载此[Azure-302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)，将其作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)导入项目，然后从[第6章继续](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="c3cc4-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="c3cc4-253">本课程需要使用**newtonsoft.json**库，可将其作为 DLL 添加到资产中。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="c3cc4-254">[可以从此链接下载包含此库](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)的包。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="c3cc4-255">若要将 Newtonsoft.json 库导入项目，请使用本课程附带的 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="c3cc4-256">使用 " **资产* > *导入* *包* > *自定义* *包** " 菜单选项将*unitypackage*添加到 Unity。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="c3cc4-257">在弹出的 "**导入 Unity 包**" 框中，确保选择了 "所有" （并包括）**插件**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="c3cc4-258">单击 "**导入**" 按钮，将项添加到项目。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="c3cc4-259">在项目视图中，在 "**插件**" 下，单击 " **newtonsoft.json** " 文件夹，然后选择 " *newtonsoft.json" 插件*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="c3cc4-260">选择*newtonsoft.json 插件*后，请确保**未选中** **任何平台**，然后确保还**取消选中** **WSAPlayer** ，并单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="c3cc4-261">这只是为了确认已正确配置文件。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="c3cc4-262">标记这些插件会将它们配置为仅在 Unity 编辑器中使用。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="c3cc4-263">在从 Unity 导出项目后，将使用 WSA 文件夹中的一组不同的组。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="c3cc4-264">接下来，需要在**newtonsoft.json**文件夹中打开**WSA**文件夹。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="c3cc4-265">你将看到刚才配置的同一文件的副本。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="c3cc4-266">选择该文件，然后在 "检查器" 中，确保</span><span class="sxs-lookup"><span data-stu-id="c3cc4-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="c3cc4-267">**未选中** **任何平台**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="c3cc4-268">**仅** **检查** **WSAPlayer**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="c3cc4-269">不**检查** **进程**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="c3cc4-270">第5章-照相机设置</span><span class="sxs-lookup"><span data-stu-id="c3cc4-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="c3cc4-271">在 "层次结构" 面板中，选择 "*摄像机*"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="c3cc4-272">选择后，你将能够在 "*检查器" 面板*中看到*主相机*的所有组件。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="c3cc4-273">*照相机*对象必须命名为 "**主相机**" （请注意拼写正确！）</span><span class="sxs-lookup"><span data-stu-id="c3cc4-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="c3cc4-274">必须将主相机**标记**设置为**MainCamera** （请注意拼写！）</span><span class="sxs-lookup"><span data-stu-id="c3cc4-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="c3cc4-275">请确保将**转换位置**设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="c3cc4-276">将**清除标志**设置为**纯色**（对于沉浸式耳机，请忽略此设置）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="c3cc4-277">将相机组件的**背景**色设置为**黑色、Alpha 0 （十六进制代码： #00000000）** （对沉浸式耳机忽略此颜色）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="c3cc4-278">第6章-创建 CustomVisionAnalyser 类。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="c3cc4-279">此时，您可以编写一些代码。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="c3cc4-280">你将从*CustomVisionAnalyser*类开始。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="c3cc4-281">在下面显示的代码中对**自定义影像服务**所做的调用是使用**自定义视觉 REST API**进行的。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="c3cc4-282">通过使用此功能，您将了解如何实现和使用此 API （对于理解如何实现类似于您自己的操作非常有用）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="c3cc4-283">请注意，Microsoft 提供了一个**自定义影像服务 SDK** ，该 SDK 还可用于对服务进行调用。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="c3cc4-284">有关详细信息，请访问[自定义影像服务 SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)文章。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="c3cc4-285">此类负责：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-285">This class is responsible for:</span></span>

-   <span data-ttu-id="c3cc4-286">加载作为字节数组捕获的最新映像。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="c3cc4-287">将字节数组发送给 Azure*自定义影像服务*实例以进行分析。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="c3cc4-288">接收 JSON 字符串形式的响应。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="c3cc4-289">反序列化响应并将结果*预测*传递给*SceneOrganiser*类，这将负责显示响应的方式。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="c3cc4-290">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-290">To create this class:</span></span>

1.  <span data-ttu-id="c3cc4-291">右键单击位于 "*项目" 面板*中的*资产文件夹*，然后单击 "**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="c3cc4-292">调用文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="c3cc4-293">双击刚创建的文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="c3cc4-294">右键单击文件夹内，然后单击 "**创建** > **C\# 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3cc4-295">将脚本命名为*CustomVisionAnalyser*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="c3cc4-296">双击新的*CustomVisionAnalyser*脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="c3cc4-297">更新文件顶部的命名空间，以匹配以下内容：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="c3cc4-298">在*CustomVisionAnalyser*类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="c3cc4-299">请确保将**预测密钥**插入到**predictionKey**变量中，并将**预测终结点**插入到**predictionEndpoint**变量中。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="c3cc4-300">您在本课程的前面部分将它们复制到*记事本*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="c3cc4-301">现在需要添加用于**唤醒（）** 的代码以初始化实例变量：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="c3cc4-302">删除方法**Start （）** 和**Update （）** 。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="c3cc4-303">接下来，添加协同程序（在其下面带有 static **GetImageAsByteArray （）** 方法），该方法将获得*ImageCapture*类捕获的映像的分析结果。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c3cc4-304">在**AnalyseImageCapture**协同程序中，有一个对你还需要创建的*SceneOrganiser*类的调用。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="c3cc4-305">因此，请**暂时将这些行注释为**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-305">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="c3cc4-306">在返回到**Unity**之前，请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="c3cc4-307">第7章-创建 CustomVisionObjects 类</span><span class="sxs-lookup"><span data-stu-id="c3cc4-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="c3cc4-308">你现在将创建的类是*CustomVisionObjects*类。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="c3cc4-309">此脚本包含其他类用于序列化和反序列化对*自定义影像服务*进行的调用的许多对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="c3cc4-310">请务必记下自定义影像服务提供的终结点，因为下面的 JSON 结构已设置为使用[*自定义视觉预测*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)v2.0。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="c3cc4-311">如果你的版本不同，可能需要更新以下结构。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="c3cc4-312">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-312">To create this class:</span></span>

1.  <span data-ttu-id="c3cc4-313">右键单击 "**脚本**" 文件夹内，然后单击 "**创建** > **C\# 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3cc4-314">调用脚本*CustomVisionObjects*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="c3cc4-315">双击新的**CustomVisionObjects**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3cc4-316">将以下命名空间添加到文件顶部：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="c3cc4-317">删除*CustomVisionObjects*类中的**Start （）** 和**Update （）** 方法;此类现在应为空。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="c3cc4-318">将以下类添加到*CustomVisionObjects*类的**外部**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="c3cc4-319">*Newtonsoft.json*库使用这些对象序列化和反序列化响应数据：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="c3cc4-320">第8章-创建 VoiceRecognizer 类</span><span class="sxs-lookup"><span data-stu-id="c3cc4-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="c3cc4-321">此类将识别用户的语音输入。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="c3cc4-322">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-322">To create this class:</span></span>

1.  <span data-ttu-id="c3cc4-323">右键单击 "**脚本**" 文件夹内，然后单击 "**创建** > **C\# 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3cc4-324">调用脚本*VoiceRecognizer*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="c3cc4-325">双击新的**VoiceRecognizer**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3cc4-326">将以下命名空间添加到*VoiceRecognizer*类的上方：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="c3cc4-327">然后，将以下变量添加到*VoiceRecognizer*类中的*Start （）* 方法之上：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="c3cc4-328">添加**唤醒（）** 和**Start （）** 方法，后者将设置在将标记关联到图像时要识别的用户*关键字*：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="c3cc4-329">删除**Update （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="c3cc4-330">添加以下处理程序，只要识别语音输入，就会调用该处理程序：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="c3cc4-331">在返回到**Unity**之前，请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="c3cc4-332">不要担心可能出现错误的代码，因为您很快就会提供更多的类，这将修复这些问题。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="c3cc4-333">第9章-创建 CustomVisionTrainer 类</span><span class="sxs-lookup"><span data-stu-id="c3cc4-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="c3cc4-334">此类将链接一系列 web 调用以训练*自定义影像服务*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="c3cc4-335">每次调用都将在代码的上方详细说明。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="c3cc4-336">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-336">To create this class:</span></span>

1.  <span data-ttu-id="c3cc4-337">右键单击 "**脚本**" 文件夹内，然后单击 "**创建** > **C\# 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3cc4-338">调用脚本*CustomVisionTrainer*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="c3cc4-339">双击新的*CustomVisionTrainer*脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3cc4-340">将以下命名空间添加到*CustomVisionTrainer*类的上方：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="c3cc4-341">然后，将以下变量添加到*CustomVisionTrainer*类中的**Start （）** 方法之上。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="c3cc4-342">此处使用的训练 URL 在*自定义视觉培训 1.2*文档中提供，并具有以下结构： https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="c3cc4-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="c3cc4-343">有关详细信息，请访问[*自定义视觉培训 v1.0 参考 API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="c3cc4-344">请务必记下自定义影像服务为您提供培训模式的终结点，因为使用的 JSON 结构（在**CustomVisionObjects**类中）已设置为与[*自定义视觉培训*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)v1.0 一起使用。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="c3cc4-345">如果有不同的版本，则可能需要更新*对象*结构。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="c3cc4-346">确保你添加了你之前记下的**服务密钥**（定型密钥）值和**项目 Id**值;这是你[在本课程前面部分中收集的值（第2章、第10章）](#chapter-2---training-your-custom-vision-project)。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-project).</span></span>

5.  <span data-ttu-id="c3cc4-347">添加以下**Start （）** 和**唤醒（）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="c3cc4-348">这些方法在初始化时调用，并包含设置 UI 的调用：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="c3cc4-349">删除**Update （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-349">Delete the **Update()** method.</span></span> <span data-ttu-id="c3cc4-350">此类不需要此类。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-350">This class will not need it.</span></span>

7.  <span data-ttu-id="c3cc4-351">添加**RequestTagSelection （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="c3cc4-352">此方法是在捕获图像并将其存储在设备中，并且现在已准备好提交到*自定义影像服务*的第一个调用。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="c3cc4-353">此方法在定型 UI 中显示一组关键字，用户可以使用这些关键字标记已捕获的映像。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="c3cc4-354">它还提醒*VoiceRecognizer*类开始倾听用户的语音输入。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="c3cc4-355">添加**VerifyTag （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="c3cc4-356">此方法将接收**VoiceRecognizer**类识别的语音输入并验证其有效性，然后开始训练过程。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="c3cc4-357">添加**SubmitImageForTraining （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="c3cc4-358">此方法将开始自定义影像服务训练过程。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="c3cc4-359">第一步是从服务中检索与用户的经验证的语音输入相关联的**标记 Id** 。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="c3cc4-360">**标记 Id**随后将连同图像一起上传。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-360">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="c3cc4-361">添加**TrainCustomVisionProject （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="c3cc4-362">提交并标记该映像后，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="c3cc4-363">它将创建一个新的迭代，该迭代将使用提交到服务的所有之前的图像以及刚刚上传的图像进行训练。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="c3cc4-364">完成训练后，此方法将调用方法将新创建的**迭代**设置为**默认值**，以便用于分析的终结点是最新的定型迭代。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="c3cc4-365">添加**SetDefaultIteration （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="c3cc4-366">此方法会将以前创建和训练的迭代设置为*默认值*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="c3cc4-367">完成后，此方法将不得不删除服务中的上一个迭代。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="c3cc4-368">编写本课程时，在服务中允许同时存在的最大迭代数限制为10（10）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="c3cc4-369">添加**DeletePreviousIteration （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="c3cc4-370">此方法将查找并删除以前的非默认迭代：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-370">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="c3cc4-371">要添加到此类中的最后一个方法是**GetImageAsByteArray （）** 方法，用于在 web 调用上将捕获的图像转换为字节数组。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="c3cc4-372">在返回到**Unity**之前，请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="c3cc4-373">第10章-创建 SceneOrganiser 类</span><span class="sxs-lookup"><span data-stu-id="c3cc4-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="c3cc4-374">此类将：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-374">This class will:</span></span>

-   <span data-ttu-id="c3cc4-375">创建要附加到主相机的**Cursor**对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="c3cc4-376">创建一个**标签**对象，该对象将在服务识别现实世界对象时显示。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="c3cc4-377">通过向主摄像机附加相应的组件来设置它。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="c3cc4-378">在**分析模式**下，将在运行时、相对于主摄像机位置的适当世界空间中生成标签，并显示从自定义影像服务收到的数据。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="c3cc4-379">处于**定型模式**时，将生成 UI，该 UI 将显示训练过程的不同阶段。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="c3cc4-380">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-380">To create this class:</span></span>

1.  <span data-ttu-id="c3cc4-381">右键单击 "**脚本**" 文件夹内，然后单击 "**创建** > **C\# 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c3cc4-382">将脚本命名为*SceneOrganiser*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="c3cc4-383">双击新的*SceneOrganiser*脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3cc4-384">你只需要一个命名空间，并从*SceneOrganiser*类的上方删除其他命名空间：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="c3cc4-385">然后，将以下变量添加到*SceneOrganiser*类中的**Start （）** 方法之上：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="c3cc4-386">删除**Start （）** 和**Update （）** 方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="c3cc4-387">在变量的下方，添加**唤醒（）** 方法，这将初始化类并设置场景。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="c3cc4-388">现在，添加用于创建和定位主照相机光标的**CreateCameraCursor （）** 方法和**CreateLabel （）** 方法，该方法创建**分析标签**对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="c3cc4-389">添加**SetCameraStatus （）** 方法，该方法将处理旨在提供相机状态的文本网格的消息。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="c3cc4-390">添加**PlaceAnalysisLabel （）** 和**SetTagsToLastLabel （）** 方法，该方法将生成数据并将其从自定义影像服务显示到场景中。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="c3cc4-391">最后，添加**CreateTrainingUI （）** 方法，该方法将生成在应用程序处于定型模式时显示训练过程的多个阶段的 UI。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="c3cc4-392">此方法也将伴随创建相机状态对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-392">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="c3cc4-393">在返回到**Unity**之前，请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3cc4-394">继续之前，请打开**CustomVisionAnalyser**类，并在**AnalyseLastImageCaptured （）** 方法中*取消注释*以下行：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="c3cc4-395">第11章-创建 ImageCapture 类</span><span class="sxs-lookup"><span data-stu-id="c3cc4-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="c3cc4-396">要创建的下一个类是*ImageCapture*类。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="c3cc4-397">此类负责：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-397">This class is responsible for:</span></span>

-   <span data-ttu-id="c3cc4-398">使用 HoloLens 相机捕获映像，并将其存储在*App*文件夹中。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="c3cc4-399">处理用户的敲击手势。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="c3cc4-400">维护用于确定应用程序是否将在*分析*模式或*定型*模式下运行的*枚举*值。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="c3cc4-401">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-401">To create this class:</span></span>

1.  <span data-ttu-id="c3cc4-402">中转到前面创建的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="c3cc4-403">右键单击文件夹内，然后单击 "**创建 > C\# 脚本**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="c3cc4-404">将脚本命名为*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="c3cc4-405">双击新的**ImageCapture**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="c3cc4-406">将文件顶部的命名空间替换为以下内容：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="c3cc4-407">然后，将以下变量添加到*ImageCapture*类中的**Start （）** 方法之上：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="c3cc4-408">现在需要添加**唤醒（）** 和**Start （）** 方法的代码：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="c3cc4-409">实现一个处理程序，该处理程序将在出现分流手势时调用。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="c3cc4-410">在*分析*模式下， **TapHandler**方法充当开始或停止照片捕获循环的开关。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="c3cc4-411">在*定型*模式下，它将从相机捕获图像。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="c3cc4-412">如果光标为绿色，则表示相机可用于拍摄映像。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="c3cc4-413">如果光标为红色，则表示相机处于繁忙状态。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="c3cc4-414">添加应用程序用于启动映像捕获过程并存储映像的方法。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="c3cc4-415">添加在捕获照片时要调用的处理程序，并将其添加到已准备好进行分析的时间。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="c3cc4-416">然后，将结果传递给*CustomVisionAnalyser*或*CustomVisionTrainer* ，具体取决于设置了代码的模式。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="c3cc4-417">在返回到**Unity**之前，请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="c3cc4-418">现在，所有脚本都已完成，请返回 Unity 编辑器，然后在 "*层次结构" 面板*中单击 "**脚本**" 文件夹中的**SceneOrganiser**类，并将其拖到**主相机**对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="c3cc4-419">第12章-生成之前</span><span class="sxs-lookup"><span data-stu-id="c3cc4-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="c3cc4-420">若要对应用程序进行全面测试，需要将其旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="c3cc4-421">在执行此操作之前，请确保：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="c3cc4-422">[第2章](#chapter-2---training-your-custom-vision-project)中提到的所有设置都已正确设置。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="c3cc4-423">**主相机**"检查器" 面板中的所有字段均已正确分配。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="c3cc4-424">脚本**SceneOrganiser**已附加到**摄像机主**对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="c3cc4-425">请确保将你的**预测密钥**插入到**predictionKey**变量。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="c3cc4-426">已在**predictionEndpoint**变量中插入了**预测终结点**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="c3cc4-427">已将**定型密钥**插入*CustomVisionTrainer*类的**trainingKey**变量中。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="c3cc4-428">已在*CustomVisionTrainer*类的**projectId**变量中插入了**项目 ID** 。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="c3cc4-429">第13章-构建并旁加载应用程序</span><span class="sxs-lookup"><span data-stu-id="c3cc4-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="c3cc4-430">开始*生成*过程：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="c3cc4-431">请参阅**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="c3cc4-432">勾选**Unity C\# 项目**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="c3cc4-433">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-433">Click **Build**.</span></span> <span data-ttu-id="c3cc4-434">Unity 将启动**文件资源管理器**窗口，在该窗口中，需要创建一个文件夹，然后选择要在其中生成应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="c3cc4-435">立即创建该文件夹并将其命名为**应用**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="c3cc4-436">选择**应用**文件夹后，单击 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="c3cc4-437">Unity 将开始向**应用**文件夹生成项目。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="c3cc4-438">Unity 完成生成（可能需要一些时间）后，它会在生成的位置打开 "**文件资源管理器**" 窗口（检查任务栏，因为它可能不会始终出现在窗口之上，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="c3cc4-439">在 HoloLens 上部署：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="c3cc4-440">你将需要 HoloLens 的 IP 地址（用于远程部署），并确保你的 HoloLens 处于**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="c3cc4-441">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-441">To do this:</span></span>

    1.  <span data-ttu-id="c3cc4-442">在戴上 HoloLens 的同时，请打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="c3cc4-443">中转到**网络 & Internet** > **Wi-fi** > **高级选项**</span><span class="sxs-lookup"><span data-stu-id="c3cc4-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="c3cc4-444">记下**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="c3cc4-445">接下来，导航回 "**设置**"，然后为**开发人员** **更新 & Security** > </span><span class="sxs-lookup"><span data-stu-id="c3cc4-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="c3cc4-446">设置**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="c3cc4-447">导航到新的 Unity 生成（**应用**文件夹），并在**Visual Studio**中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="c3cc4-448">在*解决方案配置*中，选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="c3cc4-449">在*解决方案平台*中，选择 " **X86，远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="c3cc4-450">系统将提示你插入远程设备的**IP 地址**（在本例中，你记下了此项）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="c3cc4-451">中转到 "**生成**" 菜单，然后单击 "**部署解决方案**"，将应用程序旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="c3cc4-452">应用现在应显示在你的 HoloLens 上已安装的应用列表中，可以启动了！</span><span class="sxs-lookup"><span data-stu-id="c3cc4-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="c3cc4-453">若要部署到沉浸式耳机，请将 "**解决方案平台**" 设置为 "*本地计算机*"，并将**配置**设置为 "*调试*"，将 " *x86* " 设置为**平台**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="c3cc4-454">然后，使用 "**生成**" 菜单项选择 "*部署解决方案*"，将部署到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="c3cc4-455">使用应用程序：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-455">To use the application:</span></span>

<span data-ttu-id="c3cc4-456">若要在*定型*模式和*预测*模式间切换应用功能，需要更新位于*ImageCapture*类**中的** **AppMode**变量。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="c3cc4-457">或</span><span class="sxs-lookup"><span data-stu-id="c3cc4-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="c3cc4-458">在*定型*模式下：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-458">In *Training* mode:</span></span>

- <span data-ttu-id="c3cc4-459">查看**鼠标**或**键盘**，并使用**点击手势**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="c3cc4-460">接下来，将显示文本，要求你提供标记。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="c3cc4-461">说**鼠标**或**键盘**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="c3cc4-462">在*预测*模式下：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="c3cc4-463">查看对象并使用**点击动作**。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="c3cc4-464">将显示文本，以提供检测到的对象，最高的概率（这是标准化的）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="c3cc4-465">第14章-评估并改善自定义视觉模型</span><span class="sxs-lookup"><span data-stu-id="c3cc4-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="c3cc4-466">若要使您的服务更准确，需要继续训练用于预测的模型。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="c3cc4-467">这是通过将新应用程序与*培训*和*预测*模式结合使用来实现的，后者要求你访问门户，本章将介绍这一点。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="c3cc4-468">准备多次重新访问您的门户，以不断改善您的模型。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="c3cc4-469">再次转到 Azure 自定义视觉门户，在项目中选择 "*预测*" 选项卡（从页面的顶部中心）：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="c3cc4-470">在应用程序运行时，你将看到所有已发送到服务的映像。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="c3cc4-471">如果你将鼠标悬停在这些图像上，它们将为你提供对该映像进行的预测：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="c3cc4-472">选择其中一个映像，将其打开。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-472">Select one of your images to open it.</span></span> <span data-ttu-id="c3cc4-473">打开后，您将看到对该图像的预测。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="c3cc4-474">如果预测是正确的，并且您希望将此图像添加到服务的训练模型，请单击 "*我的标记*" 输入框，然后选择您要关联的标记。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="c3cc4-475">完成后，单击右下角的 "*保存并关闭*" 按钮，然后继续转到下一张图像。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="c3cc4-476">返回到图像网格后，你会注意到已将标记添加到（和保存）的映像将被删除。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="c3cc4-477">如果你发现你认为没有标记项的任何图像，则可以通过单击该图像上的勾选标记（可以对几个图像执行此操作），然后单击网格页右上角的 "*删除*" 来删除它们。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="c3cc4-478">在下面的弹出窗口中，可以单击 *"是"、"删除*" 或 "*否*" 以确认删除或取消。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="c3cc4-479">准备好继续时，单击右上方的绿色*训练*按钮。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="c3cc4-480">你的服务模型将使用你现在提供的所有映像（这将使其更准确）训练。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="c3cc4-481">训练完成后，请确保再次单击 "设置*默认值*" 按钮，使*预测 URL*继续使用最新的服务迭代。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="c3cc4-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="c3cc4-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="c3cc4-483">已完成的自定义视觉 API 应用程序</span><span class="sxs-lookup"><span data-stu-id="c3cc4-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="c3cc4-484">恭喜，你构建了一个使用 Azure 自定义视觉 API 来识别真实世界对象的混合现实应用，为服务模型定型，并显示对所见内容的信心。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c3cc4-485">额外练习</span><span class="sxs-lookup"><span data-stu-id="c3cc4-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c3cc4-486">练习1</span><span class="sxs-lookup"><span data-stu-id="c3cc4-486">Exercise 1</span></span>

<span data-ttu-id="c3cc4-487">训练**自定义影像服务**来识别更多对象。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c3cc4-488">练习2</span><span class="sxs-lookup"><span data-stu-id="c3cc4-488">Exercise 2</span></span>

<span data-ttu-id="c3cc4-489">若要在了解的情况下进行扩展，请完成以下练习：</span><span class="sxs-lookup"><span data-stu-id="c3cc4-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="c3cc4-490">在识别对象时播放声音。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="c3cc4-491">练习3</span><span class="sxs-lookup"><span data-stu-id="c3cc4-491">Exercise 3</span></span>

<span data-ttu-id="c3cc4-492">使用 API 来重新训练你的服务，使其与你的应用程序正在分析的映像相同，以便使该服务更准确（同时执行预测和定型）。</span><span class="sxs-lookup"><span data-stu-id="c3cc4-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
