---
title: MR 和 Azure 302b-自定义视觉
description: 完成此课程以了解如何定型机器学习模型，以及如何将训练的模型来识别混合的现实应用程序中的类似对象。
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure 的混合现实、 学院、 unity、 教程、 api、 自定义影像，沉浸式、 hololens、 vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591813"
---
>[!NOTE]
><span data-ttu-id="07950-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="07950-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="07950-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="07950-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="07950-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="07950-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="07950-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="07950-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="07950-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="07950-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="07950-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="07950-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="07950-110">MR 和 Azure 302b:自定义视觉</span><span class="sxs-lookup"><span data-stu-id="07950-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="07950-111">在本课程中，您将学习如何识别自定义可视化内容中提供的映像，在混合的现实应用程序中使用 Azure 自定义视觉功能。</span><span class="sxs-lookup"><span data-stu-id="07950-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="07950-112">此服务将允许你定型机器学习模型，使用对象映像。</span><span class="sxs-lookup"><span data-stu-id="07950-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="07950-113">然后将使用经过训练的模型来识别类似对象，提供的 Microsoft HoloLens 或照相机连接到您的 PC 以沉浸式 (VR) 耳机的相机捕捉。</span><span class="sxs-lookup"><span data-stu-id="07950-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![课程结果](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="07950-115">Azure 自定义影像是一种 Microsoft 认知服务，允许开发人员可以构建自定义图像分类器。</span><span class="sxs-lookup"><span data-stu-id="07950-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="07950-116">这些分类器可以随后可用于新的映像识别，或进行分类、 设置了新的映像中的对象。</span><span class="sxs-lookup"><span data-stu-id="07950-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="07950-117">该服务提供简单、 易于使用、 联机门户以简化过程。</span><span class="sxs-lookup"><span data-stu-id="07950-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="07950-118">有关详细信息，请访问[Azure 自定义影像服务页](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)。</span><span class="sxs-lookup"><span data-stu-id="07950-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="07950-119">完成本课程时，之后您将拥有一个混合的现实应用程序，将能够在两个模式下工作：</span><span class="sxs-lookup"><span data-stu-id="07950-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="07950-120">**分析模式**： 自定义影像服务手动设置通过将映像上传、 创建标记，并训练服务来识别不同 （在此事例的鼠标和键盘） 的对象。</span><span class="sxs-lookup"><span data-stu-id="07950-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="07950-121">然后，您将创建一个 HoloLens 应用，它将捕获映像使用相机，并尝试识别现实生活中的这些对象。</span><span class="sxs-lookup"><span data-stu-id="07950-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="07950-122">**训练模式**： 将实现将启用"培训模式"应用程序中的代码。</span><span class="sxs-lookup"><span data-stu-id="07950-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="07950-123">训练模式将允许您捕获使用 HoloLens 的照相机图像、 将捕获的映像上传到服务，并为自定义影像模型定型。</span><span class="sxs-lookup"><span data-stu-id="07950-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="07950-124">本课程将介绍如何将结果从自定义影像服务到基于 Unity 的示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="07950-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="07950-125">它将取决于您要应用于您可能要构建一个自定义应用程序的这些概念。</span><span class="sxs-lookup"><span data-stu-id="07950-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="07950-126">设备支持</span><span class="sxs-lookup"><span data-stu-id="07950-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="07950-127">课程</span><span class="sxs-lookup"><span data-stu-id="07950-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="07950-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="07950-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="07950-129"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="07950-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="07950-130">MR 和 Azure 302b:自定义视觉</span><span class="sxs-lookup"><span data-stu-id="07950-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="07950-131">✔️</span><span class="sxs-lookup"><span data-stu-id="07950-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="07950-132">✔️</span><span class="sxs-lookup"><span data-stu-id="07950-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="07950-133">尽管本课程主要专注于 HoloLens，您还可以应用到 Windows Mixed Reality 沉浸式 (VR) 耳机本课程中学习的内容。</span><span class="sxs-lookup"><span data-stu-id="07950-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="07950-134">因为沉浸式 (VR) 耳机不具有可访问照相机，您将需要连接到您的 PC 外部照相机。</span><span class="sxs-lookup"><span data-stu-id="07950-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="07950-135">按照课程时，您将看到说明您可能需要使用以支持沉浸式 (VR) 耳机的任何更改。</span><span class="sxs-lookup"><span data-stu-id="07950-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07950-136">系统必备</span><span class="sxs-lookup"><span data-stu-id="07950-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="07950-137">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="07950-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="07950-138">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。</span><span class="sxs-lookup"><span data-stu-id="07950-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="07950-139">你可以随意使用最新的软件，如中所列[安装的工具](install-the-tools.md)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。</span><span class="sxs-lookup"><span data-stu-id="07950-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="07950-140">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="07950-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="07950-141">开发 PC、 一个[与 Windows Mixed Reality 兼容](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)沉浸式 (VR) 耳机开发</span><span class="sxs-lookup"><span data-stu-id="07950-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="07950-142">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="07950-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="07950-143">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="07950-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="07950-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="07950-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="07950-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="07950-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="07950-146">一个[Windows Mixed Reality 沉浸式 (VR) 耳机](immersive-headset-hardware-details.md)或[Microsoft HoloLens](hololens-hardware-details.md)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="07950-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="07950-147">照相机连接到您的 PC （适用于沉浸式头戴式开发）</span><span class="sxs-lookup"><span data-stu-id="07950-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="07950-148">Internet 访问的 Azure 设置和自定义视觉 API 检索</span><span class="sxs-lookup"><span data-stu-id="07950-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="07950-149">一系列的至少五 （5） 图像 （十 （10） 建议） 为你想自定义影像服务识别每个对象。</span><span class="sxs-lookup"><span data-stu-id="07950-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="07950-150">如果您愿意，可以使用[已随附此课程 （计算机鼠标和键盘） 的映像](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。</span><span class="sxs-lookup"><span data-stu-id="07950-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="07950-151">开始之前</span><span class="sxs-lookup"><span data-stu-id="07950-151">Before you start</span></span>

1.  <span data-ttu-id="07950-152">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="07950-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="07950-153">设置和测试你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="07950-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="07950-154">如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="07950-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="07950-155">它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。</span><span class="sxs-lookup"><span data-stu-id="07950-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="07950-156">有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="07950-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="07950-157">有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="07950-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="07950-158">第 1 章-自定义影像服务门户</span><span class="sxs-lookup"><span data-stu-id="07950-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="07950-159">若要使用*自定义影像服务*在 Azure 中，你将需要配置要成为可用于应用程序的服务的实例。</span><span class="sxs-lookup"><span data-stu-id="07950-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="07950-160">首先，[导航到*自定义影像服务*主页](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。</span><span class="sxs-lookup"><span data-stu-id="07950-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="07950-161">单击**开始**按钮。</span><span class="sxs-lookup"><span data-stu-id="07950-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="07950-162">登录到*自定义影像服务*门户。</span><span class="sxs-lookup"><span data-stu-id="07950-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="07950-163">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="07950-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="07950-164">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="07950-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="07950-165">登录第一次，系统会提示使用*服务条款*面板。</span><span class="sxs-lookup"><span data-stu-id="07950-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="07950-166">单击该复选框以同意这些条款。</span><span class="sxs-lookup"><span data-stu-id="07950-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="07950-167">然后单击**我同意**。</span><span class="sxs-lookup"><span data-stu-id="07950-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="07950-168">具有同意这些条款，你将导航至*项目*门户的一部分。</span><span class="sxs-lookup"><span data-stu-id="07950-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="07950-169">单击**新的项目**。</span><span class="sxs-lookup"><span data-stu-id="07950-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="07950-170">将提示你指定项目的某些字段的右侧将显示一个选项卡。</span><span class="sxs-lookup"><span data-stu-id="07950-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="07950-171">插入*名称*为你的项目。</span><span class="sxs-lookup"><span data-stu-id="07950-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="07950-172">插入*描述*为你的项目 (*可选*)。</span><span class="sxs-lookup"><span data-stu-id="07950-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="07950-173">选择*资源组*或新建一个。</span><span class="sxs-lookup"><span data-stu-id="07950-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="07950-174">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="07950-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="07950-175">建议将所有 Azure 服务与常见的资源组下的单个项目 （例如如这些课程））。</span><span class="sxs-lookup"><span data-stu-id="07950-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="07950-176">设置*项目类型*到**分类**</span><span class="sxs-lookup"><span data-stu-id="07950-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="07950-177">设置*域*作为**常规**。</span><span class="sxs-lookup"><span data-stu-id="07950-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="07950-178">如果你想要阅读更多有关 Azure 资源组，请[访问该资源组文章](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)。</span><span class="sxs-lookup"><span data-stu-id="07950-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="07950-179">完成后，单击**创建项目**，你将重定向到自定义影像服务，项目页。</span><span class="sxs-lookup"><span data-stu-id="07950-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="07950-180">第 2 章-培训您的自定义视觉项目</span><span class="sxs-lookup"><span data-stu-id="07950-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="07950-181">一次在自定义视觉门户中，您的主要目标是训练你的项目以识别图像中的特定对象。</span><span class="sxs-lookup"><span data-stu-id="07950-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="07950-182">需要至少五 （5） 映像，但十 （10） 是首选方法，你想要识别您应用程序的每个对象。</span><span class="sxs-lookup"><span data-stu-id="07950-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="07950-183">[可以使用与此课程 （计算机鼠标和键盘） 提供的映像](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)。</span><span class="sxs-lookup"><span data-stu-id="07950-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="07950-184">若要训练你自定义影像服务的项目：</span><span class="sxs-lookup"><span data-stu-id="07950-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="07950-185">单击 **+** 按钮旁边 **标记。**</span><span class="sxs-lookup"><span data-stu-id="07950-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="07950-186">添加**名称**你想要识别的对象。</span><span class="sxs-lookup"><span data-stu-id="07950-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="07950-187">单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="07950-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="07950-188">你会注意到您**标记**已添加 （可能需要重新加载它才会显示在页面）。</span><span class="sxs-lookup"><span data-stu-id="07950-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="07950-189">如果未选中，请单击与你的新标记，该复选框。</span><span class="sxs-lookup"><span data-stu-id="07950-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="07950-190">单击**添加映像**中页的中心。</span><span class="sxs-lookup"><span data-stu-id="07950-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="07950-191">单击**浏览本地文件**，并搜索，然后选择你想要上传，最小为映像五 （5)。</span><span class="sxs-lookup"><span data-stu-id="07950-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="07950-192">请记住所有这些映像应包含将训练的对象。</span><span class="sxs-lookup"><span data-stu-id="07950-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="07950-193">一次，若要上传，可以选择多个映像。</span><span class="sxs-lookup"><span data-stu-id="07950-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="07950-194">一旦您所见的映像的选项卡中，选择中的适当标记**我标记**框。</span><span class="sxs-lookup"><span data-stu-id="07950-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="07950-195">单击**将文件上传**。</span><span class="sxs-lookup"><span data-stu-id="07950-195">Click on **Upload files**.</span></span> <span data-ttu-id="07950-196">随即开始将文件上传。</span><span class="sxs-lookup"><span data-stu-id="07950-196">The files will begin uploading.</span></span> <span data-ttu-id="07950-197">上传的确认后，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="07950-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="07950-198">重复相同的过程来创建新**标记**名为**键盘**并将相应的照片上传它。</span><span class="sxs-lookup"><span data-stu-id="07950-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="07950-199">请确保 **取消选中** *鼠标* 创建新标记，因此，若要显示后 *将映像添加* 窗口。</span><span class="sxs-lookup"><span data-stu-id="07950-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="07950-200">设置这两个标记后，单击**训练**，并第一次训练迭代将开始构建。</span><span class="sxs-lookup"><span data-stu-id="07950-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="07950-201">一旦建立，您将能够看到两个按钮名为**设为默认**并**预测 URL**。</span><span class="sxs-lookup"><span data-stu-id="07950-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="07950-202">单击**设为默认**第一次，然后单击**预测 URL**。</span><span class="sxs-lookup"><span data-stu-id="07950-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="07950-203">此操作，请从提供的终结点 URL 设置为准*迭代*已被标记为默认值。</span><span class="sxs-lookup"><span data-stu-id="07950-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="07950-204">同样，如果您更高版本进行的新*迭代*和更新为默认值，不需要更改代码。</span><span class="sxs-lookup"><span data-stu-id="07950-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="07950-205">一旦你单击*预测 URL*，打开*记事本*，然后复制并粘贴**URL**和**预测密钥**，以便你可以需要在代码中更高版本时进行检索。</span><span class="sxs-lookup"><span data-stu-id="07950-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="07950-206">单击**嵌齿**顶部的屏幕。</span><span class="sxs-lookup"><span data-stu-id="07950-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="07950-207">复制**培训键**将其粘贴到*记事本*，以供将来使用。</span><span class="sxs-lookup"><span data-stu-id="07950-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="07950-208">另外，将复制你**项目 Id**，还将其粘贴到你*记事本*文件，以供将来使用。</span><span class="sxs-lookup"><span data-stu-id="07950-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="07950-209">第 3 章 — 设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="07950-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="07950-210">以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="07950-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="07950-211">打开*Unity*然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="07950-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="07950-212">现在，需要提供的 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="07950-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="07950-213">插入**AzureCustomVision。**</span><span class="sxs-lookup"><span data-stu-id="07950-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="07950-214">请确保项目模板设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="07950-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="07950-215">设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="07950-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="07950-216">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="07950-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="07950-217">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="07950-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="07950-218">转到 **编辑* > *首选项** ，然后在新窗口中，导航到 **外部工具** 。</span><span class="sxs-lookup"><span data-stu-id="07950-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="07950-219">更改**外部脚本编辑器**到**Visual Studio 2017**。</span><span class="sxs-lookup"><span data-stu-id="07950-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="07950-220">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="07950-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="07950-221">接下来，请转到**文件 > 生成设置**，然后选择**通用 Windows 平台**，然后单击**切换平台**按钮以应用你的选择。</span><span class="sxs-lookup"><span data-stu-id="07950-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="07950-222">在仍处于**文件 > 生成设置**并确保选中：</span><span class="sxs-lookup"><span data-stu-id="07950-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="07950-223">**设备为目标**设置为**Hololens**</span><span class="sxs-lookup"><span data-stu-id="07950-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="07950-224">对于沉浸式耳机，设置**目标设备**到*任一设备*。</span><span class="sxs-lookup"><span data-stu-id="07950-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="07950-225">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="07950-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="07950-226">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="07950-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="07950-227">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="07950-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="07950-228">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="07950-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="07950-229">保存场景，并将其添加到生成。</span><span class="sxs-lookup"><span data-stu-id="07950-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="07950-230">选择执行此**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="07950-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="07950-231">保存窗口将显示。</span><span class="sxs-lookup"><span data-stu-id="07950-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="07950-232">创建一个新文件夹，以及任何未来、 场景，然后选择**新文件夹**按钮，创建一个新文件夹，其命名**场景**。</span><span class="sxs-lookup"><span data-stu-id="07950-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="07950-233">打开新建**场景**文件夹，然后在*文件的名称：* 文本字段中，键入**CustomVisionScene**，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="07950-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="07950-234">请注意，必须将保存您的 Unity 场景中*资产*文件夹中，因为它们必须与 Unity 项目相关联。</span><span class="sxs-lookup"><span data-stu-id="07950-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="07950-235">创建场景文件夹 （和其他类似的文件夹） 是用于结构化的 Unity 项目的典型方式。</span><span class="sxs-lookup"><span data-stu-id="07950-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="07950-236">中的剩余设置，*生成设置*，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="07950-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="07950-237">在*生成设置*窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的*检查器*所在。</span><span class="sxs-lookup"><span data-stu-id="07950-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="07950-238">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="07950-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="07950-239">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="07950-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="07950-240">**脚本运行时版本**应**实验 （.NET 4.6 等效）** ，这将触发需要重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="07950-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="07950-241">**脚本编写后端**应为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="07950-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="07950-242">**API 兼容性级别**应为 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="07950-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="07950-243">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="07950-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="07950-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="07950-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="07950-245">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="07950-245">**Webcam**</span></span>

        3. <span data-ttu-id="07950-246">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="07950-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="07950-247">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，请确保**Windows 混合现实 SDK**添加。</span><span class="sxs-lookup"><span data-stu-id="07950-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="07950-248">回到*生成设置* *Unity C\#项目*不再灰显; 选中它旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="07950-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="07950-249">关闭生成设置窗口。</span><span class="sxs-lookup"><span data-stu-id="07950-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="07950-250">保存您的场景和项目 (**文件 > 保存场景文件 > 保存项目**)。</span><span class="sxs-lookup"><span data-stu-id="07950-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="07950-251">第 4 章-导入 Unity 中 Newtonsoft DLL</span><span class="sxs-lookup"><span data-stu-id="07950-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07950-252">如果你想要跳过*Unity 设置*组件的此课程，并继续直接插入代码，欢迎下载这[Azure MR 302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)，将其导入项目中，作为[**自定义包**](https://docs.unity3d.com/Manual/AssetPackages.html)，然后继续从[第 6 章](#chapter-6---create-the-customvisionanalyser-class)。</span><span class="sxs-lookup"><span data-stu-id="07950-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="07950-253">此课程需要使用**Newtonsoft**库，可以作为 DLL 添加到你的资产。</span><span class="sxs-lookup"><span data-stu-id="07950-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="07950-254">包包含[可以从以下链接下载此库](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="07950-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="07950-255">若要 Newtonsoft 库导入到你的项目，使用了随附此课程的 Unity 包。</span><span class="sxs-lookup"><span data-stu-id="07950-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="07950-256">添加 *.unitypackage* 到使用 Unity **资产* > *导入* *包* > *自定义* *包** 菜单选项。</span><span class="sxs-lookup"><span data-stu-id="07950-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="07950-257">在中**导入 Unity 程序包**弹出框、 下 （其中包含） 确保一切**插件**处于选中状态。</span><span class="sxs-lookup"><span data-stu-id="07950-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="07950-258">单击**导入**按钮将项添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="07950-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="07950-259">转到**Newtonsoft**下的文件夹**插件**在项目视图中，选择*Newtonsoft.Json 插件*。</span><span class="sxs-lookup"><span data-stu-id="07950-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="07950-260">与*Newtonsoft.Json 插件*选择，确保**Any 平台**是**未选中**，然后确保**WSAPlayer**也**unchecked**，然后单击**应用**。</span><span class="sxs-lookup"><span data-stu-id="07950-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="07950-261">这只是为了确认正确配置文件。</span><span class="sxs-lookup"><span data-stu-id="07950-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="07950-262">将标记这些插件将它们配置为仅使用在 Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="07950-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="07950-263">有一组不同的它们从 Unity 项目会导出后，将使用 WSA 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="07950-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="07950-264">接下来，您需要打开**WSA**文件夹，在**Newtonsoft**文件夹。</span><span class="sxs-lookup"><span data-stu-id="07950-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="07950-265">您将看到刚配置的相同文件的副本。</span><span class="sxs-lookup"><span data-stu-id="07950-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="07950-266">选择的文件，然后在检查器中，确保的</span><span class="sxs-lookup"><span data-stu-id="07950-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="07950-267">**任何平台**是**未选中状态**</span><span class="sxs-lookup"><span data-stu-id="07950-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="07950-268">**仅** **WSAPlayer**是**检查**</span><span class="sxs-lookup"><span data-stu-id="07950-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="07950-269">**不处理**是**检查**</span><span class="sxs-lookup"><span data-stu-id="07950-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="07950-270">第 5 章-照相机设置</span><span class="sxs-lookup"><span data-stu-id="07950-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="07950-271">在层次结构窗格中，选择*Main Camera*。</span><span class="sxs-lookup"><span data-stu-id="07950-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="07950-272">选择后，你将能够看到的所有组件*Main Camera*中*检查器面板*。</span><span class="sxs-lookup"><span data-stu-id="07950-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="07950-273">*照相机*对象必须命名为**Main Camera** （请注意拼写 ！）</span><span class="sxs-lookup"><span data-stu-id="07950-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="07950-274">Main Camera**标记**必须设置为**MainCamera** （请注意拼写 ！）</span><span class="sxs-lookup"><span data-stu-id="07950-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="07950-275">请确保**转换位置**设置为**0，0，0**</span><span class="sxs-lookup"><span data-stu-id="07950-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="07950-276">设置**清除标志**到**纯色**（忽略这的沉浸式头戴式耳机）。</span><span class="sxs-lookup"><span data-stu-id="07950-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="07950-277">设置**背景**相机的颜色组件**黑色、 Alpha 0 (十六进制代码: #00000000)** （忽略这的沉浸式头戴式耳机）。</span><span class="sxs-lookup"><span data-stu-id="07950-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="07950-278">章 6-创建 CustomVisionAnalyser 类。</span><span class="sxs-lookup"><span data-stu-id="07950-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="07950-279">此时已准备好编写一些代码。</span><span class="sxs-lookup"><span data-stu-id="07950-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="07950-280">您将首先*CustomVisionAnalyser*类。</span><span class="sxs-lookup"><span data-stu-id="07950-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="07950-281">对调用**自定义影像服务**中所示的代码所做下面所用**自定义视觉 REST API**。</span><span class="sxs-lookup"><span data-stu-id="07950-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="07950-282">通过使用此，您将学会如何实现并使用此 api （适用于了解如何在您自己实现类似的内容）。</span><span class="sxs-lookup"><span data-stu-id="07950-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="07950-283">请注意，Microsoft 提供了**自定义影像服务 SDK** ，还可用于对服务进行调用。</span><span class="sxs-lookup"><span data-stu-id="07950-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="07950-284">有关详细信息，请访问[自定义影像服务 SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)一文。</span><span class="sxs-lookup"><span data-stu-id="07950-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="07950-285">此类负责：</span><span class="sxs-lookup"><span data-stu-id="07950-285">This class is responsible for:</span></span>

-   <span data-ttu-id="07950-286">正在加载最新的映像捕获为一个字节数组。</span><span class="sxs-lookup"><span data-stu-id="07950-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="07950-287">将字节数组发送到你的 Azure*自定义影像服务*实例以进行分析。</span><span class="sxs-lookup"><span data-stu-id="07950-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="07950-288">接收响应以 JSON 字符串。</span><span class="sxs-lookup"><span data-stu-id="07950-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="07950-289">反序列化响应并传递得到*预测*到*SceneOrganiser*类，该类将负责响应的显示方式。</span><span class="sxs-lookup"><span data-stu-id="07950-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="07950-290">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="07950-290">To create this class:</span></span>

1.  <span data-ttu-id="07950-291">在中右击*资产文件夹*位于*项目面板*，然后单击**创建 > 文件夹**。</span><span class="sxs-lookup"><span data-stu-id="07950-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="07950-292">将该文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="07950-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="07950-293">双击刚创建的文件夹，以将其打开。</span><span class="sxs-lookup"><span data-stu-id="07950-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="07950-294">在文件夹中，右键单击，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="07950-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="07950-295">脚本命名为*CustomVisionAnalyser*。</span><span class="sxs-lookup"><span data-stu-id="07950-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="07950-296">双击新*CustomVisionAnalyser*脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="07950-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="07950-297">更新你的文件以匹配以下顶部的命名空间：</span><span class="sxs-lookup"><span data-stu-id="07950-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="07950-298">在中*CustomVisionAnalyser*类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="07950-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

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
    > <span data-ttu-id="07950-299">请确保插入你**预测键**到**predictionKey**变量和你**预测终结点**到**predictionEndpoint**变量。</span><span class="sxs-lookup"><span data-stu-id="07950-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="07950-300">复制到*记事本*前面的课程。</span><span class="sxs-lookup"><span data-stu-id="07950-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="07950-301">为代码**Awake()** 现在需要添加初始化该实例变量：</span><span class="sxs-lookup"><span data-stu-id="07950-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="07950-302">删除方法**start （)** 并**update （)** 。</span><span class="sxs-lookup"><span data-stu-id="07950-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="07950-303">接下来，添加协同程序 (使用静态**GetImageAsByteArray()** 它下面的方法)，这将获取由捕获映像的分析结果*ImageCapture*类。</span><span class="sxs-lookup"><span data-stu-id="07950-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="07950-304">在中**AnalyseImageCapture**协同程序，没有调用*SceneOrganiser*尚若要创建的类。</span><span class="sxs-lookup"><span data-stu-id="07950-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="07950-305">因此，**保留这些行注释现在**。</span><span class="sxs-lookup"><span data-stu-id="07950-305">Therefore, **leave those lines commented for now**.</span></span>

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

10.  <span data-ttu-id="07950-306">请务必保存中所做的更改**Visual Studio**才会回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="07950-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="07950-307">章 7-创建 CustomVisionObjects 类</span><span class="sxs-lookup"><span data-stu-id="07950-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="07950-308">现在，您将创建的类是*CustomVisionObjects*类。</span><span class="sxs-lookup"><span data-stu-id="07950-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="07950-309">此脚本包含的对象由其他类用于序列化和反序列化对所做的调用数*自定义影像服务*。</span><span class="sxs-lookup"><span data-stu-id="07950-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="07950-310">非常重要，需要记下的终结点，可自定义影像服务提供，与以下 JSON 结构已设置为使用[*自定义视觉预测 v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)。</span><span class="sxs-lookup"><span data-stu-id="07950-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="07950-311">如果您拥有的不同版本，您可能需要更新以下结构。</span><span class="sxs-lookup"><span data-stu-id="07950-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="07950-312">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="07950-312">To create this class:</span></span>

1.  <span data-ttu-id="07950-313">内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="07950-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="07950-314">调用脚本*CustomVisionObjects*。</span><span class="sxs-lookup"><span data-stu-id="07950-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="07950-315">双击新**CustomVisionObjects**脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="07950-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="07950-316">将以下命名空间添加到文件顶部：</span><span class="sxs-lookup"><span data-stu-id="07950-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="07950-317">删除**start （)** 并**update （)** 中的方法*CustomVisionObjects*类; 此类应为空。</span><span class="sxs-lookup"><span data-stu-id="07950-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="07950-318">添加以下类**外部** *CustomVisionObjects*类。</span><span class="sxs-lookup"><span data-stu-id="07950-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="07950-319">这些对象由*Newtonsoft*库进行序列化和反序列化响应数据：</span><span class="sxs-lookup"><span data-stu-id="07950-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

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

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="07950-320">章 8-创建 VoiceRecognizer 类</span><span class="sxs-lookup"><span data-stu-id="07950-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="07950-321">此类将识别用户的语音输入。</span><span class="sxs-lookup"><span data-stu-id="07950-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="07950-322">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="07950-322">To create this class:</span></span>

1.  <span data-ttu-id="07950-323">内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="07950-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="07950-324">调用脚本*VoiceRecognizer*。</span><span class="sxs-lookup"><span data-stu-id="07950-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="07950-325">双击新**VoiceRecognizer**脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="07950-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="07950-326">添加以下命名空间上述*VoiceRecognizer*类：</span><span class="sxs-lookup"><span data-stu-id="07950-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="07950-327">然后添加以下变量内的*VoiceRecognizer*类，更高版本*start （)* 方法：</span><span class="sxs-lookup"><span data-stu-id="07950-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

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

5.  <span data-ttu-id="07950-328">添加**Awake()** 并**start （)** 方法，后者将设置注册该用户*关键字*能够识别相关联的图像标记时：</span><span class="sxs-lookup"><span data-stu-id="07950-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

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

6.  <span data-ttu-id="07950-329">删除**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="07950-330">添加以下处理程序，每当识别语音输入时调用：</span><span class="sxs-lookup"><span data-stu-id="07950-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

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

8.  <span data-ttu-id="07950-331">请务必保存中所做的更改**Visual Studio**才会回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="07950-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="07950-332">不必担心可能显示为具有错误，将提供进一步的类，可以修复这些代码。</span><span class="sxs-lookup"><span data-stu-id="07950-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="07950-333">章 9-创建 CustomVisionTrainer 类</span><span class="sxs-lookup"><span data-stu-id="07950-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="07950-334">此类将链接的一系列 web 调用来训练*自定义影像服务*。</span><span class="sxs-lookup"><span data-stu-id="07950-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="07950-335">每次调用将代码的正上方的详细信息中所述。</span><span class="sxs-lookup"><span data-stu-id="07950-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="07950-336">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="07950-336">To create this class:</span></span>

1.  <span data-ttu-id="07950-337">内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="07950-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="07950-338">调用脚本*CustomVisionTrainer*。</span><span class="sxs-lookup"><span data-stu-id="07950-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="07950-339">双击新*CustomVisionTrainer*脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="07950-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="07950-340">添加以下命名空间上述*CustomVisionTrainer*类：</span><span class="sxs-lookup"><span data-stu-id="07950-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="07950-341">然后添加以下变量内的*CustomVisionTrainer*类，更高版本**start （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="07950-342">中提供此处使用的培训 URL*自定义视觉训练 1.2*文档，并具有的结构： https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="07950-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="07950-343">有关详细信息，请访问[ *v1.2 引用自定义视觉训练 API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。</span><span class="sxs-lookup"><span data-stu-id="07950-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="07950-344">非常重要，需要注意的自定义影像服务提供培训模式下，为使用的 JSON 结构的终结点 (内**CustomVisionObjects**类) 已设置为使用[ *自定义视觉训练 v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)。</span><span class="sxs-lookup"><span data-stu-id="07950-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="07950-345">如果您拥有的不同版本，您可能需要更新*对象*结构。</span><span class="sxs-lookup"><span data-stu-id="07950-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

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
    > <span data-ttu-id="07950-346">确保添加你**服务密钥**（培训密钥） 值和**项目 Id**值，其下前面记下; 这些都是值您[从前面的课程 （门户收集第 2 章步骤 10 及更高版本）](#chapter-2---training-your-custom-vision-oroject)。</span><span class="sxs-lookup"><span data-stu-id="07950-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="07950-347">添加以下**start （)** 并**Awake()** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="07950-348">这些方法在初始化时调用，并包含调用以设置用户界面：</span><span class="sxs-lookup"><span data-stu-id="07950-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

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

6.  <span data-ttu-id="07950-349">删除**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-349">Delete the **Update()** method.</span></span> <span data-ttu-id="07950-350">此类将不需要它。</span><span class="sxs-lookup"><span data-stu-id="07950-350">This class will not need it.</span></span>

7.  <span data-ttu-id="07950-351">添加**RequestTagSelection()** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="07950-352">此方法是在捕获映像并将其存储在设备时要调用的第一个和现已准备好提交给*自定义影像服务*、 训练它。</span><span class="sxs-lookup"><span data-stu-id="07950-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="07950-353">此方法显示在训练 UI 中，一组用户可以使用标记已捕获映像的关键字。</span><span class="sxs-lookup"><span data-stu-id="07950-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="07950-354">它还会发出警报*VoiceRecognizer*类以开始侦听到用户的语音输入。</span><span class="sxs-lookup"><span data-stu-id="07950-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="07950-355">添加**VerifyTag()** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="07950-356">此方法将接收语音输入识别**VoiceRecognizer**类和验证其有效性，然后开始训练过程。</span><span class="sxs-lookup"><span data-stu-id="07950-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

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

9.  <span data-ttu-id="07950-357">添加**SubmitImageForTraining()** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="07950-358">此方法将开始自定义影像服务训练过程。</span><span class="sxs-lookup"><span data-stu-id="07950-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="07950-359">第一步是检索**标记 Id**从与用户的已验证的语音输入相关联的服务。</span><span class="sxs-lookup"><span data-stu-id="07950-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="07950-360">**标记 Id**然后以及映像上传。</span><span class="sxs-lookup"><span data-stu-id="07950-360">The **Tag Id** will then be uploaded along with the image.</span></span>

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

10. <span data-ttu-id="07950-361">添加**TrainCustomVisionProject()** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="07950-362">一旦已提交并标记该映像，将调用此方法。</span><span class="sxs-lookup"><span data-stu-id="07950-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="07950-363">它将创建新的迭代，将使用提交到服务以及映像的所有以前的图像训练刚上传。</span><span class="sxs-lookup"><span data-stu-id="07950-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="07950-364">完成定型后，此方法将调用一个方法来设置新创建**迭代**作为**默认**，以便将用于分析的终结点是最新的训练的迭代。</span><span class="sxs-lookup"><span data-stu-id="07950-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

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

11. <span data-ttu-id="07950-365">添加**SetDefaultIteration()** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="07950-366">此方法将设置为以前创建并训练迭代*默认*。</span><span class="sxs-lookup"><span data-stu-id="07950-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="07950-367">完成后，此方法必须删除现有服务中的上一个迭代。</span><span class="sxs-lookup"><span data-stu-id="07950-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="07950-368">在编写本课程时，没有最大十 （10） 的迭代的允许在服务中同时存在限制。</span><span class="sxs-lookup"><span data-stu-id="07950-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

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

12. <span data-ttu-id="07950-369">添加**DeletePreviousIteration()** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="07950-370">此方法将查找并删除之前的非默认迭代：</span><span class="sxs-lookup"><span data-stu-id="07950-370">This method will find and delete the previous non-default iteration:</span></span>

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

13. <span data-ttu-id="07950-371">此类中添加的最后一个方法是**GetImageAsByteArray()** 方法，用于在 web 调用要将映像捕获到的字节数组转换。</span><span class="sxs-lookup"><span data-stu-id="07950-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

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

14. <span data-ttu-id="07950-372">请务必保存中所做的更改**Visual Studio**才会回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="07950-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="07950-373">章 10-创建 SceneOrganiser 类</span><span class="sxs-lookup"><span data-stu-id="07950-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="07950-374">将此类：</span><span class="sxs-lookup"><span data-stu-id="07950-374">This class will:</span></span>

-   <span data-ttu-id="07950-375">创建**游标**要附加到 Main Camera 对象。</span><span class="sxs-lookup"><span data-stu-id="07950-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="07950-376">创建**标签**对象，该服务识别出的实际对象时，将显示对象。</span><span class="sxs-lookup"><span data-stu-id="07950-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="07950-377">通过附加到适当的组件设置 Main Camera。</span><span class="sxs-lookup"><span data-stu-id="07950-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="07950-378">在何时**分析模式**、 生成的标签，在运行时，相对于主相机的位置的适当世界空间中并显示从自定义影像服务接收的数据。</span><span class="sxs-lookup"><span data-stu-id="07950-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="07950-379">在何时**培训模式**，生成将显示在定型过程的不同阶段的 UI。</span><span class="sxs-lookup"><span data-stu-id="07950-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="07950-380">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="07950-380">To create this class:</span></span>

1.  <span data-ttu-id="07950-381">内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="07950-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="07950-382">脚本命名为*SceneOrganiser*。</span><span class="sxs-lookup"><span data-stu-id="07950-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="07950-383">双击新*SceneOrganiser*脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="07950-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="07950-384">您只需要一个命名空间，删除上面提供的其他*SceneOrganiser*类：</span><span class="sxs-lookup"><span data-stu-id="07950-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="07950-385">然后添加以下变量内的*SceneOrganiser*类，更高版本**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="07950-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="07950-386">删除**start （)** 并**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="07950-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="07950-387">右下方变量中，添加**Awake()** 方法，它将初始化类并设置场景。</span><span class="sxs-lookup"><span data-stu-id="07950-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="07950-388">现在，添加**CreateCameraCursor()** 方法，用于创建将 Main Camera 光标定位并**CreateLabel()** 方法，用于创建**分析标签**对象.</span><span class="sxs-lookup"><span data-stu-id="07950-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

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

8. <span data-ttu-id="07950-389">添加**SetCameraStatus()** 方法，它将处理适用于文本网格提供的相机的状态消息。</span><span class="sxs-lookup"><span data-stu-id="07950-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

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

9. <span data-ttu-id="07950-390">添加**PlaceAnalysisLabel()** 并**SetTagsToLastLabel()** 方法，这将生成并向场景中显示自定义影像服务中的数据。</span><span class="sxs-lookup"><span data-stu-id="07950-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

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

10. <span data-ttu-id="07950-391">最后，将添加**CreateTrainingUI()** 方法，将生成应用程序时在定型模式下都显示在定型过程的多个阶段的 UI。</span><span class="sxs-lookup"><span data-stu-id="07950-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="07950-392">此方法还会利用创建相机状态对象。</span><span class="sxs-lookup"><span data-stu-id="07950-392">This method will also be harnessed to create the camera status object.</span></span>

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

11. <span data-ttu-id="07950-393">请务必保存中所做的更改**Visual Studio**才会回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="07950-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="07950-394">在继续之前，打开**CustomVisionAnalyser**类，并在**AnalyseLastImageCaptured()** 方法，*取消注释*以下行：</span><span class="sxs-lookup"><span data-stu-id="07950-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="07950-395">章 11-创建 ImageCapture 类</span><span class="sxs-lookup"><span data-stu-id="07950-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="07950-396">要创建的下一步类是*ImageCapture*类。</span><span class="sxs-lookup"><span data-stu-id="07950-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="07950-397">此类负责：</span><span class="sxs-lookup"><span data-stu-id="07950-397">This class is responsible for:</span></span>

-   <span data-ttu-id="07950-398">捕获映像使用 HoloLens 相机并将其存储在*应用*文件夹。</span><span class="sxs-lookup"><span data-stu-id="07950-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="07950-399">处理来自用户的点击手势。</span><span class="sxs-lookup"><span data-stu-id="07950-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="07950-400">维护*Enum*值，该值确定是否运行该应用程序*Analysis*模式或*培训*模式。</span><span class="sxs-lookup"><span data-stu-id="07950-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="07950-401">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="07950-401">To create this class:</span></span>

1.  <span data-ttu-id="07950-402">转到**脚本**之前创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="07950-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="07950-403">在文件夹中，右键单击，然后单击**创建 > C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="07950-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="07950-404">脚本命名为*ImageCapture*。</span><span class="sxs-lookup"><span data-stu-id="07950-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="07950-405">双击新**ImageCapture**脚本以将其与打开**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="07950-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="07950-406">使用以下内容替换该文件顶部的命名空间：</span><span class="sxs-lookup"><span data-stu-id="07950-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="07950-407">然后添加以下变量内的*ImageCapture*类，更高版本**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="07950-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="07950-408">为代码**Awake()** 并**start （)** 方法现在需要添加：</span><span class="sxs-lookup"><span data-stu-id="07950-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="07950-409">实现的点击动作时将调用的处理程序。</span><span class="sxs-lookup"><span data-stu-id="07950-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

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
    > <span data-ttu-id="07950-410">在中*分析*模式下， **TapHandler**方法充当一个开关，用于启动或停止照片捕获循环。</span><span class="sxs-lookup"><span data-stu-id="07950-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="07950-411">在中*培训*模式下，它将从捕获映像照相机。</span><span class="sxs-lookup"><span data-stu-id="07950-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="07950-412">当光标位于绿色时，这意味着照相机是可用于获取映像。</span><span class="sxs-lookup"><span data-stu-id="07950-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="07950-413">当光标位于红色时，这意味着照相机正忙。</span><span class="sxs-lookup"><span data-stu-id="07950-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="07950-414">添加应用程序使用启动映像捕获过程并将图像存储的方法。</span><span class="sxs-lookup"><span data-stu-id="07950-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

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

9.  <span data-ttu-id="07950-415">添加捕获照片和时准备好对其进行分析将调用处理程序。</span><span class="sxs-lookup"><span data-stu-id="07950-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="07950-416">然后将结果传递给*CustomVisionAnalyser*或*CustomVisionTrainer*具体取决于哪种模式上设置的代码。</span><span class="sxs-lookup"><span data-stu-id="07950-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

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

10. <span data-ttu-id="07950-417">请务必保存中所做的更改**Visual Studio**才会回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="07950-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="07950-418">现在，所有脚本都完成后，返回在 Unity 编辑器中，然后单击并拖动**SceneOrganiser**类派生**脚本**文件夹**Main Camera**对象中*层次结构面板*。</span><span class="sxs-lookup"><span data-stu-id="07950-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="07950-419">第 12 章 — 生成前</span><span class="sxs-lookup"><span data-stu-id="07950-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="07950-420">若要执行全面测试您的应用程序将需要旁加载它到在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="07950-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="07950-421">执行操作之前，请确保：</span><span class="sxs-lookup"><span data-stu-id="07950-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="07950-422">中所述的所有设置[第 2 章](#chapter-2---training-your-custom-vision-project)正确设置。</span><span class="sxs-lookup"><span data-stu-id="07950-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="07950-423">中的所有字段**Main Camera**，检查器面板中，正确分配。</span><span class="sxs-lookup"><span data-stu-id="07950-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="07950-424">该脚本**SceneOrganiser**附加到**Main Camera**对象。</span><span class="sxs-lookup"><span data-stu-id="07950-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="07950-425">请确保插入你**预测键**成**predictionKey**变量。</span><span class="sxs-lookup"><span data-stu-id="07950-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="07950-426">已插入您**预测终结点**成**predictionEndpoint**变量。</span><span class="sxs-lookup"><span data-stu-id="07950-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="07950-427">已插入您**培训键**成**trainingKey**变量的*CustomVisionTrainer*类。</span><span class="sxs-lookup"><span data-stu-id="07950-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="07950-428">已插入您**项目 ID**成**projectId**变量的*CustomVisionTrainer*类。</span><span class="sxs-lookup"><span data-stu-id="07950-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="07950-429">第 13 章 — 生成和旁加载应用程序</span><span class="sxs-lookup"><span data-stu-id="07950-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="07950-430">若要开始*生成*过程：</span><span class="sxs-lookup"><span data-stu-id="07950-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="07950-431">转到**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="07950-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="07950-432">刻度线**Unity C\#项目**。</span><span class="sxs-lookup"><span data-stu-id="07950-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="07950-433">单击“生成”  。</span><span class="sxs-lookup"><span data-stu-id="07950-433">Click **Build**.</span></span> <span data-ttu-id="07950-434">将启动 unity**文件资源管理器**窗口中，需要创建，然后选择要生成该应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="07950-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="07950-435">现在，创建该文件夹并将其命名**应用**。</span><span class="sxs-lookup"><span data-stu-id="07950-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="07950-436">然后使用**应用程序**文件夹选择，单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="07950-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="07950-437">Unity 将开始构建您的项目**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="07950-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="07950-438">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="07950-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="07950-439">若要部署在 HoloLens 上：</span><span class="sxs-lookup"><span data-stu-id="07950-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="07950-440">你将 （适用于远程部署），需要在 HoloLens IP 地址，以确保你 HoloLens 处于**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="07950-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="07950-441">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="07950-441">To do this:</span></span>

    1.  <span data-ttu-id="07950-442">戴上您 HoloLens，同时打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="07950-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="07950-443">转到**网络和 Internet** > **的 Wi-fi** > **高级选项**</span><span class="sxs-lookup"><span data-stu-id="07950-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="07950-444">请注意**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="07950-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="07950-445">接下来，导航回到**设置**，然后**更新和安全** > **面向开发人员**</span><span class="sxs-lookup"><span data-stu-id="07950-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="07950-446">设置**上的开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="07950-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="07950-447">导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="07950-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="07950-448">在中*解决方案配置*选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="07950-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="07950-449">在中*解决方案平台*，选择**x86，远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="07950-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="07950-450">系统会提示要插入**IP 地址**的远程设备 (HoloLens，在这种情况下，记下)。</span><span class="sxs-lookup"><span data-stu-id="07950-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="07950-451">转到**构建**菜单，并单击**部署解决方案**旁加载到你 HoloLens 应用程序。</span><span class="sxs-lookup"><span data-stu-id="07950-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="07950-452">在准备好启动在 HoloLens 上安装的应用列表中，现在应显示你的应用 ！</span><span class="sxs-lookup"><span data-stu-id="07950-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="07950-453">若要将部署到沉浸式头戴式耳机，设置**解决方案平台**到*本地计算机*，并设置**配置**到*调试*，与*x86*作为**平台**。</span><span class="sxs-lookup"><span data-stu-id="07950-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="07950-454">然后将其部署到本地计算机，使用**构建**菜单项，选择*部署解决方案*。</span><span class="sxs-lookup"><span data-stu-id="07950-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="07950-455">若要使用应用程序：</span><span class="sxs-lookup"><span data-stu-id="07950-455">To use the application:</span></span>

<span data-ttu-id="07950-456">若要切换之间的应用功能*培训*模式和*预测*模式需要更新**AppMode**变量，它位于**Awake()** 方法对位于*ImageCapture*类。</span><span class="sxs-lookup"><span data-stu-id="07950-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="07950-457">或</span><span class="sxs-lookup"><span data-stu-id="07950-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="07950-458">在中*培训*模式：</span><span class="sxs-lookup"><span data-stu-id="07950-458">In *Training* mode:</span></span>

- <span data-ttu-id="07950-459">看看**鼠标**或**键盘**，并使用**点击手势**。</span><span class="sxs-lookup"><span data-stu-id="07950-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="07950-460">接下来，文本将显示要求你提供一个标记。</span><span class="sxs-lookup"><span data-stu-id="07950-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="07950-461">指示**鼠标**或**键盘**。</span><span class="sxs-lookup"><span data-stu-id="07950-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="07950-462">在中*预测*模式：</span><span class="sxs-lookup"><span data-stu-id="07950-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="07950-463">查看对象，并使用**点击手势**。</span><span class="sxs-lookup"><span data-stu-id="07950-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="07950-464">文本将显示提供检测到，（这规范化的） 的概率最高的对象。</span><span class="sxs-lookup"><span data-stu-id="07950-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="07950-465">14-评估和改进您的自定义影像模型</span><span class="sxs-lookup"><span data-stu-id="07950-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="07950-466">若要使你的服务更准确，您需要继续训练用于预测的模型。</span><span class="sxs-lookup"><span data-stu-id="07950-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="07950-467">这通过使用两个新应用程序，来实现*培训*并*预测*模式下，使用后一种无需访问门户，它是这一章中涵盖的内容。</span><span class="sxs-lookup"><span data-stu-id="07950-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="07950-468">要准备好，若要再次访问你的门户很多时候，可以不断改进您的模型。</span><span class="sxs-lookup"><span data-stu-id="07950-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="07950-469">同样，转到你的 Azure 自定义视觉门户并在项目中后，选择*预测*（从页面的顶部中心） 的选项卡：</span><span class="sxs-lookup"><span data-stu-id="07950-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="07950-470">你将看到所有已发送到你的服务，同时你的应用程序正在运行的映像。</span><span class="sxs-lookup"><span data-stu-id="07950-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="07950-471">如果将鼠标悬停鼠标悬停在图像，他们将您提供有关该映像所做的预测：</span><span class="sxs-lookup"><span data-stu-id="07950-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="07950-472">选择其中一个映像以将其打开。</span><span class="sxs-lookup"><span data-stu-id="07950-472">Select one of your images to open it.</span></span> <span data-ttu-id="07950-473">一旦打开，你将看到右侧进行该图像的预测。</span><span class="sxs-lookup"><span data-stu-id="07950-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="07950-474">如果您预测正确的并且你想要将此映像添加到你的服务的训练模型中，单击*我标记*输入框，然后选择你想要将相关联的标记。</span><span class="sxs-lookup"><span data-stu-id="07950-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="07950-475">完成后，单击*保存并关闭*靠下右对齐，向按钮，然后继续学习下一幅图像。</span><span class="sxs-lookup"><span data-stu-id="07950-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="07950-476">返回到网格的映像后，你会注意到已添加到标记 （并保存），映像将被删除。</span><span class="sxs-lookup"><span data-stu-id="07950-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="07950-477">如果您发现您认为不具有在其中你带标记的项的任何映像，则可以删除它们，通过单击该映像 （可以执行此操作的多个映像） 上的刻度线，然后单击*删除*网格页右上角。</span><span class="sxs-lookup"><span data-stu-id="07950-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="07950-478">在弹出窗口后面，你可以单击*可以，请删除*或*否*，以确认删除，或分别取消。</span><span class="sxs-lookup"><span data-stu-id="07950-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="07950-479">若要继续，准备就绪后，单击绿色*训练*在右上角的按钮。</span><span class="sxs-lookup"><span data-stu-id="07950-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="07950-480">你的服务模型将使用的所有映像现在已提供 （这将使其更准确） 训练。</span><span class="sxs-lookup"><span data-stu-id="07950-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="07950-481">培训完成后，请务必单击*设为默认*次，按钮，以便你*预测 URL*仍会继续使用你的服务的最新迭代。</span><span class="sxs-lookup"><span data-stu-id="07950-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="07950-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="07950-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="07950-483">完成自定义视觉 API 的应用程序</span><span class="sxs-lookup"><span data-stu-id="07950-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="07950-484">祝贺你，构建利用 Azure 自定义视觉 API 能够识别现实世界对象、 训练服务模型，并显示的内容出现的置信度的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="07950-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="07950-485">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="07950-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="07950-486">练习 1</span><span class="sxs-lookup"><span data-stu-id="07950-486">Exercise 1</span></span>

<span data-ttu-id="07950-487">训练你**自定义影像服务**识别更多的对象。</span><span class="sxs-lookup"><span data-stu-id="07950-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="07950-488">练习 2</span><span class="sxs-lookup"><span data-stu-id="07950-488">Exercise 2</span></span>

<span data-ttu-id="07950-489">作为一种方式扩展您学到了什么，完成以下练习：</span><span class="sxs-lookup"><span data-stu-id="07950-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="07950-490">识别对象时播放声音。</span><span class="sxs-lookup"><span data-stu-id="07950-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="07950-491">练习 3</span><span class="sxs-lookup"><span data-stu-id="07950-491">Exercise 3</span></span>

<span data-ttu-id="07950-492">若要重新训练你的服务使用相同的图像分析您的应用程序，因此若要使服务更准确地使用 API （执行预测和同时培训）。</span><span class="sxs-lookup"><span data-stu-id="07950-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
