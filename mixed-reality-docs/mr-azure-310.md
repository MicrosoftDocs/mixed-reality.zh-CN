---
title: MR 和 Azure 310-对象检测
description: 完成本课程, 了解如何训练机器学习模型, 然后使用训练的模型从混合现实应用程序内识别类似对象及其在现实中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 自定义视觉, 对象检测, 混合现实, 学院, unity, 教程, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544419"
---
>[!NOTE]
><span data-ttu-id="0e656-104">混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="0e656-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0e656-105">因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="0e656-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0e656-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="0e656-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0e656-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="0e656-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0e656-108">将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="0e656-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0e656-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="0e656-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="0e656-110">Mr 和 Azure 310:对象检测</span><span class="sxs-lookup"><span data-stu-id="0e656-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="0e656-111">在本课程中, 你将了解如何在混合现实应用程序中使用 Azure 自定义视觉 "对象检测" 功能来识别所提供的映像中的自定义视觉对象内容及其空间位置。</span><span class="sxs-lookup"><span data-stu-id="0e656-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="0e656-112">此服务允许你使用对象图像训练机器学习模型。</span><span class="sxs-lookup"><span data-stu-id="0e656-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="0e656-113">然后, 你将使用训练的模型来识别类似对象并大致了解其在现实世界中的位置, 如 Microsoft HoloLens 的相机捕获或相机连接到用于沉浸式 (VR) 耳机的 PC。</span><span class="sxs-lookup"><span data-stu-id="0e656-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![课程结果](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="0e656-115">**Azure 自定义视觉中, 对象检测**是一种 Microsoft 服务, 它允许开发人员构建自定义映像分类器。</span><span class="sxs-lookup"><span data-stu-id="0e656-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="0e656-116">然后, 可以将这些分类器用于新的图像, 通过在图像本身中提供**框边界**来检测该新图像内的对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="0e656-117">此服务提供简单易用的联机门户来简化此过程。</span><span class="sxs-lookup"><span data-stu-id="0e656-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="0e656-118">有关详细信息, 请访问以下链接:</span><span class="sxs-lookup"><span data-stu-id="0e656-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="0e656-119">Azure 自定义视觉页面</span><span class="sxs-lookup"><span data-stu-id="0e656-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="0e656-120">限制和配额</span><span class="sxs-lookup"><span data-stu-id="0e656-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="0e656-121">完成本课程后, 你将拥有一个混合现实应用程序, 该应用程序将能够执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="0e656-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="0e656-122">用户将可以*注视*使用 Azure 自定义影像服务、对象检测训练的对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="0e656-123">用户将使用*点击*手势来捕获所查看内容的图像。</span><span class="sxs-lookup"><span data-stu-id="0e656-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="0e656-124">应用会将映像发送到 Azure 自定义影像服务。</span><span class="sxs-lookup"><span data-stu-id="0e656-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="0e656-125">此时会显示服务的答复, 该服务会将识别结果显示为世界空间文本。</span><span class="sxs-lookup"><span data-stu-id="0e656-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="0e656-126">这将通过利用 Microsoft HoloLens 的空间跟踪来实现, 这是为了了解识别对象的世界位置, 然后使用与图像中检测到的内容关联的*标记*来提供标签文本。</span><span class="sxs-lookup"><span data-stu-id="0e656-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="0e656-127">本课程还介绍了如何手动上传图像、创建标记和培训服务, 通过在提交的图像中设置*边界框*来识别不同的对象 (在提供的示例中为杯)。</span><span class="sxs-lookup"><span data-stu-id="0e656-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="0e656-128">创建和使用应用后, 开发人员应导航回 Azure 自定义影像服务, 并确定该服务所做的预测, 并确定其是否正确 (通过标记服务丢失的任何内容) 和调整*边界框*)。</span><span class="sxs-lookup"><span data-stu-id="0e656-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="0e656-129">然后, 可以对服务进行重新训练, 这会增加识别真实世界对象的可能性。</span><span class="sxs-lookup"><span data-stu-id="0e656-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="0e656-130">本课程将介绍如何从 Azure 自定义影像服务、对象检测到基于 Unity 的示例应用程序中获取结果。</span><span class="sxs-lookup"><span data-stu-id="0e656-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="0e656-131">您可以将这些概念应用到您可能生成的自定义应用程序。</span><span class="sxs-lookup"><span data-stu-id="0e656-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="0e656-132">设备支持</span><span class="sxs-lookup"><span data-stu-id="0e656-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0e656-133">摘要</span><span class="sxs-lookup"><span data-stu-id="0e656-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0e656-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0e656-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0e656-135"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="0e656-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0e656-136">MR 和 Azure 310:对象检测</span><span class="sxs-lookup"><span data-stu-id="0e656-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="0e656-137">✔️</span><span class="sxs-lookup"><span data-stu-id="0e656-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="0e656-138">先决条件</span><span class="sxs-lookup"><span data-stu-id="0e656-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0e656-139">本教程面向具有 Unity 和C#的基本经验的开发人员。</span><span class="sxs-lookup"><span data-stu-id="0e656-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0e656-140">另外, 请注意, 本文档中的先决条件和书面说明表明了撰写时经过测试和验证的内容 (2018 年7月)。</span><span class="sxs-lookup"><span data-stu-id="0e656-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="0e656-141">你可以随意使用最新的软件 (如[安装工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)一文中所述), 但不应假定本课程中的信息将与下面列出的内容完全匹配。</span><span class="sxs-lookup"><span data-stu-id="0e656-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="0e656-142">本课程建议采用以下硬件和软件:</span><span class="sxs-lookup"><span data-stu-id="0e656-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0e656-143">开发 PC</span><span class="sxs-lookup"><span data-stu-id="0e656-143">A development PC</span></span>
- [<span data-ttu-id="0e656-144">Windows 10 秋季创意者更新 (或更高版本) 已启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="0e656-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="0e656-145">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="0e656-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="0e656-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="0e656-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="0e656-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0e656-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="0e656-148">已启用开发人员模式的[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)</span><span class="sxs-lookup"><span data-stu-id="0e656-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="0e656-149">Azure 安装和自定义影像服务检索的 Internet 访问</span><span class="sxs-lookup"><span data-stu-id="0e656-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="0e656-150">对于想要自定义视觉识别的每个对象, 需要一系列至少 15 (15) 个图像。</span><span class="sxs-lookup"><span data-stu-id="0e656-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="0e656-151">如果需要, 可以使用本课程提供的映像,[一系列 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="0e656-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="0e656-152">开始之前</span><span class="sxs-lookup"><span data-stu-id="0e656-152">Before you start</span></span>

1.  <span data-ttu-id="0e656-153">为避免在生成此项目时遇到问题, 强烈建议您在本教程中的根或根文件夹中创建项目 (长文件夹路径可能会在生成时导致问题)。</span><span class="sxs-lookup"><span data-stu-id="0e656-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="0e656-154">设置并测试你的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0e656-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="0e656-155">如果需要支持设置 HoloLens, 请[确保访问 hololens 设置一文](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="0e656-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="0e656-156">在开始开发新的 HoloLens 应用程序时, 最好执行校准和传感器调整 (有时它可以帮助为每个用户执行这些任务)。</span><span class="sxs-lookup"><span data-stu-id="0e656-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="0e656-157">有关校准的帮助信息, 请单击此链接, 了解[到 HoloLens 校准文章](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="0e656-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="0e656-158">有关传感器优化的帮助, 请单击["HoloLens 传感器优化" 一文](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="0e656-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="0e656-159">第1章-自定义视觉门户</span><span class="sxs-lookup"><span data-stu-id="0e656-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="0e656-160">若要使用**Azure 自定义影像服务**, 你将需要配置该应用程序的实例。</span><span class="sxs-lookup"><span data-stu-id="0e656-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="0e656-161">导航[到**自定义影像服务**主页](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。</span><span class="sxs-lookup"><span data-stu-id="0e656-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="0e656-162">单击**入门**。</span><span class="sxs-lookup"><span data-stu-id="0e656-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="0e656-163">登录到自定义视觉门户。</span><span class="sxs-lookup"><span data-stu-id="0e656-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="0e656-164">如果还没有 Azure 帐户, 则需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="0e656-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0e656-165">如果在课堂或实验室中按照本教程进行学习, 请咨询教师或 proctors, 以获得设置新帐户的帮助。</span><span class="sxs-lookup"><span data-stu-id="0e656-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="0e656-166">首次登录后, 系统会提示 "*服务*" 面板。</span><span class="sxs-lookup"><span data-stu-id="0e656-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="0e656-167">单击复选框以*同意条款*。</span><span class="sxs-lookup"><span data-stu-id="0e656-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="0e656-168">然后单击 "**我同意**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="0e656-169">如果同意这些条款, 你现在已在 "*我的项目*" 部分。</span><span class="sxs-lookup"><span data-stu-id="0e656-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="0e656-170">单击 "**新建项目**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="0e656-171">右侧将显示一个选项卡, 该选项卡将提示你为项目指定某些字段。</span><span class="sxs-lookup"><span data-stu-id="0e656-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="0e656-172">插入项目的名称</span><span class="sxs-lookup"><span data-stu-id="0e656-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="0e656-173">为项目插入说明 (**可选**)</span><span class="sxs-lookup"><span data-stu-id="0e656-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="0e656-174">选择一个**资源组**, 或创建一个新的资源组。</span><span class="sxs-lookup"><span data-stu-id="0e656-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0e656-175">资源组提供一种监视、控制访问、预配和管理 Azure 资产集合的计费的方法。</span><span class="sxs-lookup"><span data-stu-id="0e656-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0e656-176">建议将所有与单个项目关联的 Azure 服务 (如这些课程) 保存在一个公共资源组中。</span><span class="sxs-lookup"><span data-stu-id="0e656-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="0e656-177">若要[阅读有关 Azure 资源组的详细信息, 请导航到相关文档](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="0e656-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="0e656-178">将**项目类型**设置为 "**对象检测 (预览版)** "。</span><span class="sxs-lookup"><span data-stu-id="0e656-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="0e656-179">完成后, 单击 "**创建项目**", 将重定向到 "自定义影像服务项目" 页面。</span><span class="sxs-lookup"><span data-stu-id="0e656-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="0e656-180">第2章-培训自定义视觉项目</span><span class="sxs-lookup"><span data-stu-id="0e656-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="0e656-181">在自定义视觉门户中, 你的主要目标是训练你的项目以识别图像中的特定对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="0e656-182">对于希望应用程序识别的每个对象, 至少需要 15 (15) 个映像。</span><span class="sxs-lookup"><span data-stu-id="0e656-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="0e656-183">您可以使用本课程提供的映像 ([一系列 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="0e656-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="0e656-184">训练自定义视觉项目:</span><span class="sxs-lookup"><span data-stu-id="0e656-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="0e656-185">单击 **+** 按钮旁边**标记**。</span><span class="sxs-lookup"><span data-stu-id="0e656-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="0e656-186">添加用于将图像与相关联的标记的**名称**。</span><span class="sxs-lookup"><span data-stu-id="0e656-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="0e656-187">在此示例中, 我们将使用 cup 的图像进行识别, 因此已为此、**杯**命名了标记。</span><span class="sxs-lookup"><span data-stu-id="0e656-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="0e656-188">完成后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="0e656-189">你将注意到已添加**标记**(可能需要重新加载页面以使其显示)。</span><span class="sxs-lookup"><span data-stu-id="0e656-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="0e656-190">单击页中心的 "**添加图像**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="0e656-191">单击 "**浏览本地文件**", 然后浏览到要为一个对象上传的图像, 最小值为 15 (15)。</span><span class="sxs-lookup"><span data-stu-id="0e656-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="0e656-192">你可以一次选择多个图像来上传。</span><span class="sxs-lookup"><span data-stu-id="0e656-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="0e656-193">选择要对项目定型的所有映像后, 按 "**上载文件**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="0e656-194">文件将开始上传。</span><span class="sxs-lookup"><span data-stu-id="0e656-194">The files will begin uploading.</span></span> <span data-ttu-id="0e656-195">确认上传后, 单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="0e656-196">此时, 将上载映像, 但不会对其进行标记。</span><span class="sxs-lookup"><span data-stu-id="0e656-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="0e656-197">若要为图像标记, 请使用鼠标。</span><span class="sxs-lookup"><span data-stu-id="0e656-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="0e656-198">当你将鼠标指针悬停在图像上时, 选择突出显示将帮助你在对象周围自动绘制选定内容。</span><span class="sxs-lookup"><span data-stu-id="0e656-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="0e656-199">如果它不准确, 可以自行绘制。</span><span class="sxs-lookup"><span data-stu-id="0e656-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="0e656-200">为此, 请按住鼠标左键并拖动选择区域以包含您的对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="0e656-201">选择图像中的对象之后, 会出现一个小提示符, 要求你*添加区域标记*。</span><span class="sxs-lookup"><span data-stu-id="0e656-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="0e656-202">选择之前创建的标记 (在上面的示例中为 "杯"), 或者如果要添加更多的标记, 请在中键入, 然后单击 " **+" (加号)** 按钮。</span><span class="sxs-lookup"><span data-stu-id="0e656-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="0e656-203">若要标记下一个图像, 可以单击边栏选项卡右侧的箭头, 或关闭标记边栏选项卡 (单击边栏选项卡右上角的 " **X** "), 然后单击下一个图像。</span><span class="sxs-lookup"><span data-stu-id="0e656-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="0e656-204">下一个映像准备就绪后, 请重复相同的过程。</span><span class="sxs-lookup"><span data-stu-id="0e656-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="0e656-205">对已上传的所有映像执行此操作, 直到所有映像都已标记。</span><span class="sxs-lookup"><span data-stu-id="0e656-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="0e656-206">可以在同一个映像中选择多个对象, 如下图所示:</span><span class="sxs-lookup"><span data-stu-id="0e656-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="0e656-207">标记为 "全部" 后, 单击屏幕左侧的 "**标记**" 按钮, 显示标记的图像。</span><span class="sxs-lookup"><span data-stu-id="0e656-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="0e656-208">你现在已准备好培训你的服务。</span><span class="sxs-lookup"><span data-stu-id="0e656-208">You are now ready to train your Service.</span></span> <span data-ttu-id="0e656-209">单击 "**训练**" 按钮, 将开始第一次训练迭代。</span><span class="sxs-lookup"><span data-stu-id="0e656-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="0e656-210">构建后, 你将能够看到两个称为 "**创建默认值**和**预测 URL**" 的按钮。</span><span class="sxs-lookup"><span data-stu-id="0e656-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="0e656-211">先单击 "**设为默认值**", 然后单击 "**预测 URL**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="0e656-212">从此中提供的终结点设置为标记为默认值的任何*迭代*。</span><span class="sxs-lookup"><span data-stu-id="0e656-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="0e656-213">这种情况下, 如果您以后生成新的*迭代*并将其更新为默认值, 则无需更改代码。</span><span class="sxs-lookup"><span data-stu-id="0e656-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="0e656-214">单击 "**预测 URL**" 后, 打开 "*记事本*", 复制并粘贴该**Url** (也称为**预测终结点**) 和**服务预测密钥**, 以便稍后在代码中需要时进行检索。</span><span class="sxs-lookup"><span data-stu-id="0e656-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="0e656-215">第3章-设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="0e656-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="0e656-216">下面是用于使用混合现实进行开发的典型设置, 因此, 这是其他项目的一个不错的模板。</span><span class="sxs-lookup"><span data-stu-id="0e656-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="0e656-217">打开**Unity** , 并单击 "**新建**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="0e656-218">现在需要提供 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="0e656-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="0e656-219">插入**CustomVisionObjDetection**。</span><span class="sxs-lookup"><span data-stu-id="0e656-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="0e656-220">确保将 "项目类型" 设置为 " **3d**", 并将位置设置为合适的**位置**(请记住, 更接近根目录更好)。</span><span class="sxs-lookup"><span data-stu-id="0e656-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0e656-221">然后单击 "**创建项目**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="0e656-222">当 Unity 处于打开状态时, 有必要选中 "默认**脚本编辑器**" 设置为 " **Visual Studio**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0e656-223">转到 **编辑* > *首选项** ，然后在新窗口中，导航到 **外部工具** 。</span><span class="sxs-lookup"><span data-stu-id="0e656-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0e656-224">将**外部脚本编辑器**更改为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="0e656-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="0e656-225">关闭 "**首选项**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="0e656-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="0e656-226">接下来, 转到 "文件" " **> 生成设置**", 将**平台**切换到 "*通用 Windows 平台*", 然后单击 "**切换平台**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="0e656-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="0e656-227">在相同的 "**生成设置**" 窗口中, 确保已设置以下各项:</span><span class="sxs-lookup"><span data-stu-id="0e656-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="0e656-228">**目标设备**设置为**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="0e656-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="0e656-229">**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="0e656-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="0e656-230">**SDK**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="0e656-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="0e656-231">**Visual Studio 版本**设置为 "**最新安装**"</span><span class="sxs-lookup"><span data-stu-id="0e656-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="0e656-232">"**生成并运行**" 设置为 "**本地计算机**"</span><span class="sxs-lookup"><span data-stu-id="0e656-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="0e656-233">现在, "**生成设置**" 中的其余设置应保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="0e656-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="0e656-234">在相同的**生成设置**窗口中, 单击 "**播放机设置**" 按钮, 这会在**检查器**所在的空间中打开相关面板。</span><span class="sxs-lookup"><span data-stu-id="0e656-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="0e656-235">在此面板中, 需要验证几项设置:</span><span class="sxs-lookup"><span data-stu-id="0e656-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="0e656-236">在 "**其他设置**" 选项卡中:</span><span class="sxs-lookup"><span data-stu-id="0e656-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="0e656-237">**脚本运行时版本**应为**试验**性的 (.net 4.6 等效项), 这会触发重新启动编辑器的需要。</span><span class="sxs-lookup"><span data-stu-id="0e656-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="0e656-238">**脚本编写后端**应为 **.net**。</span><span class="sxs-lookup"><span data-stu-id="0e656-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="0e656-239">**API 兼容级别**应为 **.net 4.6**。</span><span class="sxs-lookup"><span data-stu-id="0e656-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="0e656-240">在 "**发布设置**" 选项卡的 "**功能**" 下, 检查:</span><span class="sxs-lookup"><span data-stu-id="0e656-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="0e656-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="0e656-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="0e656-242">**摄像头**</span><span class="sxs-lookup"><span data-stu-id="0e656-242">**Webcam**</span></span>

        3. <span data-ttu-id="0e656-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="0e656-243">**SpatialPerception**</span></span>

            <span data-ttu-id="0e656-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="0e656-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="0e656-245">在面板中, 在 " **XR" 设置**(位于 "**发布设置**" 下) 中, 在 "**支持的虚拟现实**" 下, 确保已添加**Windows Mixed reality SDK** 。</span><span class="sxs-lookup"><span data-stu-id="0e656-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="0e656-246">返回**生成设置**, *\# Unity C 项目*不再灰显: 勾选此旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="0e656-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="0e656-247">关闭 "**生成设置**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="0e656-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="0e656-248">在**编辑器**中, 单击 "**编辑** > **项目设置** > " "**图形**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="0e656-249">在中 **检查器面板** *图形设置* 则会打开。</span><span class="sxs-lookup"><span data-stu-id="0e656-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="0e656-250">向下滚动, 直到看到一个名为 "**始终包括着色**器" 的数组。</span><span class="sxs-lookup"><span data-stu-id="0e656-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="0e656-251">通过增加**大小**变量来添加槽 (在本例中为 8, 因此我们将其设为 9)。</span><span class="sxs-lookup"><span data-stu-id="0e656-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="0e656-252">新的槽将出现在数组的最后位置, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="0e656-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="0e656-253">在插槽中, 单击槽旁边的小型目标圆圈, 以打开着色器列表。</span><span class="sxs-lookup"><span data-stu-id="0e656-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="0e656-254">查找**旧版着色器/透明/漫射**着色器并双击它。</span><span class="sxs-lookup"><span data-stu-id="0e656-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="0e656-255">第4章-导入 CustomVisionObjDetection Unity 包</span><span class="sxs-lookup"><span data-stu-id="0e656-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="0e656-256">在本课程中, 我们提供了名为 " **unitypackage**" 的 Unity 资产包。</span><span class="sxs-lookup"><span data-stu-id="0e656-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="0e656-257">提示Unity 支持的任何对象 (包括整个场景) 都可以打包到**unitypackage**文件中, 并在其他项目中导出/导入。</span><span class="sxs-lookup"><span data-stu-id="0e656-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="0e656-258">这是在不同的**Unity 项目**之间移动资产的最安全、最有效的方法。</span><span class="sxs-lookup"><span data-stu-id="0e656-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="0e656-259">你可以在[此处找到需要下载的 AZURE 尊敬的310包](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="0e656-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="0e656-260">在您前面的 "Unity" 面板中, 单击屏幕顶部菜单中的 "**资产**", 然后单击 "**导入包 > 自定义包**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="0e656-261">使用文件选取器选择**Azure unitypackage**包, 并单击 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="0e656-262">此时将显示此资产的组件列表。</span><span class="sxs-lookup"><span data-stu-id="0e656-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="0e656-263">单击 "**导**入" 按钮确认导入。</span><span class="sxs-lookup"><span data-stu-id="0e656-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="0e656-264">导入完成后, 你会注意到, 包中的文件夹现在已添加到 "**资产**" 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0e656-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="0e656-265">这种文件夹结构是 Unity 项目的典型类型。</span><span class="sxs-lookup"><span data-stu-id="0e656-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="0e656-266">"**材料**" 文件夹包含**注视光标**使用的材料。</span><span class="sxs-lookup"><span data-stu-id="0e656-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="0e656-267">**插件**文件夹包含代码用于对服务 web 响应进行反序列化的 newtonsoft.json DLL。</span><span class="sxs-lookup"><span data-stu-id="0e656-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="0e656-268">文件夹和子文件夹中包含的两个 (2) 不同版本都是允许在 Unity 编辑器和 UWP 生成中使用和生成库所必需的。</span><span class="sxs-lookup"><span data-stu-id="0e656-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="0e656-269">**Prototyping**文件夹包含场景中包含的 prototyping。</span><span class="sxs-lookup"><span data-stu-id="0e656-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="0e656-270">它们是:</span><span class="sxs-lookup"><span data-stu-id="0e656-270">Those are:</span></span>

        1.  <span data-ttu-id="0e656-271">在应用程序中使用的**GazeCursor**。</span><span class="sxs-lookup"><span data-stu-id="0e656-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="0e656-272">将与 SpatialMapping prefab 一起使用, 以将其放在物理对象顶层的场景中。</span><span class="sxs-lookup"><span data-stu-id="0e656-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="0e656-273">**标签**, 它是用于在需要时在场景中显示对象标记的 UI 对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="0e656-274">**SpatialMapping**, 它是一个对象, 它使应用程序可以使用 Microsoft HoloLens 的空间跟踪来创建虚拟映射。</span><span class="sxs-lookup"><span data-stu-id="0e656-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="0e656-275">当前包含此课程的预建场景的**场景**文件夹。</span><span class="sxs-lookup"><span data-stu-id="0e656-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="0e656-276">打开 "**场景**" 文件夹, 在 "**项目" 面板**中双击 " **ObjDetectionScene**", 加载将用于本课程的场景。</span><span class="sxs-lookup"><span data-stu-id="0e656-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="0e656-277">**不包含任何代码**, 你将按照此课程编写代码。</span><span class="sxs-lookup"><span data-stu-id="0e656-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="0e656-278">第5章-创建 CustomVisionAnalyser 类。</span><span class="sxs-lookup"><span data-stu-id="0e656-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="0e656-279">此时, 您可以编写一些代码。</span><span class="sxs-lookup"><span data-stu-id="0e656-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="0e656-280">你将从**CustomVisionAnalyser**类开始。</span><span class="sxs-lookup"><span data-stu-id="0e656-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="0e656-281">使用**自定义视觉 REST API**, 对在下面所示的代码中所做的**自定义影像服务**调用。</span><span class="sxs-lookup"><span data-stu-id="0e656-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="0e656-282">通过使用此功能, 您将了解如何实现和使用此 API (对于理解如何实现类似于您自己的操作非常有用)。</span><span class="sxs-lookup"><span data-stu-id="0e656-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="0e656-283">请注意, Microsoft 提供了一个**自定义视觉 SDK** , 该 SDK 还可用于对服务进行调用。</span><span class="sxs-lookup"><span data-stu-id="0e656-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="0e656-284">有关详细信息, 请访问[自定义视觉 SDK 文章](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。</span><span class="sxs-lookup"><span data-stu-id="0e656-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="0e656-285">此类负责:</span><span class="sxs-lookup"><span data-stu-id="0e656-285">This class is responsible for:</span></span>

- <span data-ttu-id="0e656-286">加载作为字节数组捕获的最新映像。</span><span class="sxs-lookup"><span data-stu-id="0e656-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="0e656-287">将字节数组发送给 Azure**自定义影像服务**实例以进行分析。</span><span class="sxs-lookup"><span data-stu-id="0e656-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="0e656-288">接收 JSON 字符串形式的响应。</span><span class="sxs-lookup"><span data-stu-id="0e656-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="0e656-289">反序列化响应并将结果**预测**传递给**SceneOrganiser**类, 这将负责显示响应的方式。</span><span class="sxs-lookup"><span data-stu-id="0e656-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="0e656-290">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="0e656-290">To create this class:</span></span>

1.  <span data-ttu-id="0e656-291">右键单击 "资产"**文件夹**, 位于 "**项目" 面板**中, 然后单击 **"创建** > **文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="0e656-292">调用文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="0e656-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="0e656-293">双击新创建的文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="0e656-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="0e656-294">右键单击文件夹内, 然后单击 "**创建** > **C\#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0e656-295">将脚本命名为**CustomVisionAnalyser。**</span><span class="sxs-lookup"><span data-stu-id="0e656-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="0e656-296">双击新的**CustomVisionAnalyser**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="0e656-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="0e656-297">请确保在该文件的顶部引用了以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="0e656-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="0e656-298">在**CustomVisionAnalyser**类中, 添加以下变量:</span><span class="sxs-lookup"><span data-stu-id="0e656-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="0e656-299">请确保将**服务预测密钥**插入到**predictionKey**变量中, 并将**预测终结点**插入到**predictionEndpoint**变量中。</span><span class="sxs-lookup"><span data-stu-id="0e656-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="0e656-300">你之前将它们复制到[记事本, 步骤14中的第2章](#chapter-2---training-your-custom-vision-project)。</span><span class="sxs-lookup"><span data-stu-id="0e656-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="0e656-301">现在需要添加用于**唤醒 ()** 的代码以初始化实例变量:</span><span class="sxs-lookup"><span data-stu-id="0e656-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="0e656-302">添加协同程序 (在其下面带有 static **GetImageAsByteArray ()** 方法), 该方法将获得**ImageCapture**类捕获的映像分析结果。</span><span class="sxs-lookup"><span data-stu-id="0e656-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0e656-303">在**AnalyseImageCapture**协同程序中, 有一个对你还需要创建的**SceneOrganiser**类的调用。</span><span class="sxs-lookup"><span data-stu-id="0e656-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="0e656-304">因此, 请**暂时将这些行注释为**。</span><span class="sxs-lookup"><span data-stu-id="0e656-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. <span data-ttu-id="0e656-305">删除**Start ()** 和**Update ()** 方法, 因为它们不会被使用。</span><span class="sxs-lookup"><span data-stu-id="0e656-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="0e656-306">在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="0e656-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e656-307">如前文所述, 不要担心可能出现错误的代码, 因为您很快就会提供更多的类, 这将修复这些问题。</span><span class="sxs-lookup"><span data-stu-id="0e656-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="0e656-308">第6章-创建 CustomVisionObjects 类</span><span class="sxs-lookup"><span data-stu-id="0e656-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="0e656-309">你现在将创建的类是**CustomVisionObjects**类。</span><span class="sxs-lookup"><span data-stu-id="0e656-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="0e656-310">此脚本包含其他类用于序列化和反序列化对自定义影像服务进行的调用的许多对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="0e656-311">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="0e656-311">To create this class:</span></span>

1.  <span data-ttu-id="0e656-312">右键单击 "**脚本**" 文件夹内, 然后单击 "**创建** > **C\#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0e656-313">调用脚本**CustomVisionObjects。**</span><span class="sxs-lookup"><span data-stu-id="0e656-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="0e656-314">双击新的**CustomVisionObjects**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="0e656-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0e656-315">请确保在该文件的顶部引用了以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="0e656-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="0e656-316">删除**CustomVisionObjects**类中的**Start ()** 和**Update ()** 方法, 此类现在应为空。</span><span class="sxs-lookup"><span data-stu-id="0e656-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="0e656-317">务必认真遵循下一条指令。</span><span class="sxs-lookup"><span data-stu-id="0e656-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="0e656-318">如果将新的类声明放在**CustomVisionObjects**类中, 将会在第[10 章](#chapter-10---create-the-imagecapture-class)中出现编译错误, 指出找不到**AnalysisRootObject**和**BoundingBox** 。</span><span class="sxs-lookup"><span data-stu-id="0e656-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="0e656-319">将以下类添加到**CustomVisionObjects**类的*外部*。</span><span class="sxs-lookup"><span data-stu-id="0e656-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="0e656-320">**Newtonsoft.json**库使用这些对象序列化和反序列化响应数据:</span><span class="sxs-lookup"><span data-stu-id="0e656-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="0e656-321">在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="0e656-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="0e656-322">第7章-创建 SpatialMapping 类</span><span class="sxs-lookup"><span data-stu-id="0e656-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="0e656-323">此类将设置场景中的**空间映射碰撞**器, 以便能够检测虚拟对象与实际对象之间的冲突。</span><span class="sxs-lookup"><span data-stu-id="0e656-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="0e656-324">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="0e656-324">To create this class:</span></span>

1.  <span data-ttu-id="0e656-325">右键单击 "**脚本**" 文件夹内, 然后单击 "**创建** > **C\#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0e656-326">调用脚本**SpatialMapping。**</span><span class="sxs-lookup"><span data-stu-id="0e656-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="0e656-327">双击新的**SpatialMapping**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="0e656-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0e656-328">请确保在**SpatialMapping**类的上面引用了以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="0e656-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="0e656-329">然后, 将以下变量添加到**SpatialMapping**类中的**Start ()** 方法之上:</span><span class="sxs-lookup"><span data-stu-id="0e656-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="0e656-330">添加**唤醒 ()** 和**Start ()** :</span><span class="sxs-lookup"><span data-stu-id="0e656-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="0e656-331">删除**Update ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="0e656-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="0e656-332">在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="0e656-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="0e656-333">第8章-创建 GazeCursor 类</span><span class="sxs-lookup"><span data-stu-id="0e656-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="0e656-334">此类通过使用在前一章节中创建的**SpatialMappingCollider**, 负责在实际空间中的正确位置设置光标。</span><span class="sxs-lookup"><span data-stu-id="0e656-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="0e656-335">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="0e656-335">To create this class:</span></span>

1.  <span data-ttu-id="0e656-336">右键单击 "**脚本**" 文件夹内, 然后单击 "**创建** > **C\#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0e656-337">调用脚本**GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="0e656-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="0e656-338">双击新的**GazeCursor**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="0e656-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0e656-339">请确保在**GazeCursor**类之上引用了以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="0e656-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="0e656-340">然后, 将以下变量添加到**GazeCursor**类中的**Start ()** 方法之上。</span><span class="sxs-lookup"><span data-stu-id="0e656-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="0e656-341">将**Start ()** 方法更新为以下代码:</span><span class="sxs-lookup"><span data-stu-id="0e656-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="0e656-342">将**update ()** 方法更新为以下代码:</span><span class="sxs-lookup"><span data-stu-id="0e656-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="0e656-343">不要担心找不到**SceneOrganiser**类的错误, 您将在下一章中创建它。</span><span class="sxs-lookup"><span data-stu-id="0e656-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="0e656-344">在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="0e656-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="0e656-345">第9章-创建 SceneOrganiser 类</span><span class="sxs-lookup"><span data-stu-id="0e656-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="0e656-346">此类将:</span><span class="sxs-lookup"><span data-stu-id="0e656-346">This class will:</span></span>

-   <span data-ttu-id="0e656-347">通过向*主摄像机*附加相应的组件来设置它。</span><span class="sxs-lookup"><span data-stu-id="0e656-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="0e656-348">当检测到某个对象时, 它将负责计算其在现实世界中的位置, 并在其旁边放置一个**标记标签**和合适的**标记名称**。</span><span class="sxs-lookup"><span data-stu-id="0e656-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="0e656-349">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="0e656-349">To create this class:</span></span>

1.  <span data-ttu-id="0e656-350">右键单击 "**脚本**" 文件夹内, 然后单击 "**创建** > **C\#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0e656-351">将脚本命名为**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="0e656-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="0e656-352">双击新的**SceneOrganiser**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="0e656-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="0e656-353">请确保在**SceneOrganiser**类的上面引用了以下命名空间:</span><span class="sxs-lookup"><span data-stu-id="0e656-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="0e656-354">然后, 将以下变量添加到**SceneOrganiser**类中的**Start ()** 方法之上:</span><span class="sxs-lookup"><span data-stu-id="0e656-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="0e656-355">删除**Start ()** 和**Update ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="0e656-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="0e656-356">在变量的下面添加**唤醒 ()** 方法, 该方法将初始化类并设置场景。</span><span class="sxs-lookup"><span data-stu-id="0e656-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="0e656-357">添加**PlaceAnalysisLabel ()** 方法, 该方法将*实例化*场景中的标签 (此时, 它对用户不可见)。</span><span class="sxs-lookup"><span data-stu-id="0e656-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="0e656-358">它还会放置图像的四个部分 (也不可见), 并与真实环境重叠。</span><span class="sxs-lookup"><span data-stu-id="0e656-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="0e656-359">这一点很重要, 因为在分析后从服务中检索的 box 坐标将追溯到此四个部分, 以确定对象在现实世界中的大致位置。</span><span class="sxs-lookup"><span data-stu-id="0e656-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="0e656-360">添加**FinaliseLabel ()** 方法。</span><span class="sxs-lookup"><span data-stu-id="0e656-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="0e656-361">它负责:</span><span class="sxs-lookup"><span data-stu-id="0e656-361">It is responsible for:</span></span>

    *   <span data-ttu-id="0e656-362">将*标签*文本设置为具有最高置信度的预测*标记*。</span><span class="sxs-lookup"><span data-stu-id="0e656-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="0e656-363">在前面定位的四个对象上调用*边界框*的计算, 并在场景中放置该标签。</span><span class="sxs-lookup"><span data-stu-id="0e656-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="0e656-364">使用 Raycast 向*边界框*调整标签深度, 这应与现实世界中的对象发生冲突。</span><span class="sxs-lookup"><span data-stu-id="0e656-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="0e656-365">正在重置捕获进程, 以允许用户捕获其他映像。</span><span class="sxs-lookup"><span data-stu-id="0e656-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="0e656-366">添加**CalculateBoundingBoxPosition ()** 方法, 该方法托管从服务中检索的*边界框*坐标所需的多种计算, 并在四个部分按比例重新创建它们。</span><span class="sxs-lookup"><span data-stu-id="0e656-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="0e656-367">在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="0e656-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0e656-368">继续之前, 请打开**CustomVisionAnalyser**类, 并在**AnalyseLastImageCaptured ()** 方法中*取消注释*以下行:</span><span class="sxs-lookup"><span data-stu-id="0e656-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="0e656-369">不要担心 "找不到**ImageCapture**类" 消息, 你将在下一章中创建它。</span><span class="sxs-lookup"><span data-stu-id="0e656-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="0e656-370">第10章-创建 ImageCapture 类</span><span class="sxs-lookup"><span data-stu-id="0e656-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="0e656-371">要创建的下一个类是**ImageCapture**类。</span><span class="sxs-lookup"><span data-stu-id="0e656-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="0e656-372">此类负责:</span><span class="sxs-lookup"><span data-stu-id="0e656-372">This class is responsible for:</span></span>

*   <span data-ttu-id="0e656-373">使用 HoloLens 相机捕获映像, 并将其存储在*App*文件夹中。</span><span class="sxs-lookup"><span data-stu-id="0e656-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="0e656-374">处理用户的*敲击*手势。</span><span class="sxs-lookup"><span data-stu-id="0e656-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="0e656-375">若要创建此类:</span><span class="sxs-lookup"><span data-stu-id="0e656-375">To create this class:</span></span>

1.  <span data-ttu-id="0e656-376">中转到前面创建的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="0e656-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="0e656-377">右键单击文件夹内, 然后单击 "**创建** > **C\#脚本**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="0e656-378">将脚本命名为**ImageCapture**。</span><span class="sxs-lookup"><span data-stu-id="0e656-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="0e656-379">双击新的**ImageCapture**脚本以通过**Visual Studio**打开它。</span><span class="sxs-lookup"><span data-stu-id="0e656-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="0e656-380">将文件顶部的命名空间替换为以下内容:</span><span class="sxs-lookup"><span data-stu-id="0e656-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="0e656-381">然后, 将以下变量添加到**ImageCapture**类中的**Start ()** 方法之上:</span><span class="sxs-lookup"><span data-stu-id="0e656-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="0e656-382">现在需要添加**唤醒 ()** 和**Start ()** 方法的代码:</span><span class="sxs-lookup"><span data-stu-id="0e656-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="0e656-383">实现一个处理程序, 该处理程序将在出现分流手势时调用:</span><span class="sxs-lookup"><span data-stu-id="0e656-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="0e656-384">如果光标为**绿色**, 则表示相机可用于拍摄映像。</span><span class="sxs-lookup"><span data-stu-id="0e656-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="0e656-385">如果光标为**红色**, 则表示相机处于繁忙状态。</span><span class="sxs-lookup"><span data-stu-id="0e656-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="0e656-386">添加应用程序用于启动映像捕获过程并存储映像的方法:</span><span class="sxs-lookup"><span data-stu-id="0e656-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  <span data-ttu-id="0e656-387">添加在捕获照片时要调用的处理程序, 并将其添加到已准备好进行分析的时间。</span><span class="sxs-lookup"><span data-stu-id="0e656-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="0e656-388">然后, 将结果传递给**CustomVisionAnalyser**进行分析。</span><span class="sxs-lookup"><span data-stu-id="0e656-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="0e656-389">在返回到**Unity**之前, 请务必保存**Visual Studio**中所做的更改。</span><span class="sxs-lookup"><span data-stu-id="0e656-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="0e656-390">第11章-在场景中设置脚本</span><span class="sxs-lookup"><span data-stu-id="0e656-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="0e656-391">现在, 你已经编写了此项目所需的所有代码, 是在场景中设置脚本的时候, 还是在 prototyping 上设置脚本以使它们正常运行。</span><span class="sxs-lookup"><span data-stu-id="0e656-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="0e656-392">在**Unity 编辑器**中的 "**层次结构" 面板**中, 选择 "**主摄像机**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="0e656-393">在 "**检查器" 面板**中, 选择 "**摄像机**", 单击 "**添加组件**", 然后搜索 " **SceneOrganiser**脚本", 然后双击 "添加"。</span><span class="sxs-lookup"><span data-stu-id="0e656-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="0e656-394">在 "**项目" 面板**中, 打开**prototyping 文件夹**, 将 **"标签**prefab" 拖到 "标签空引用目标输入区域" 的 "*标签*为空引用目标输入区域" 中, 在刚添加到*摄像机*的**SceneOrganiser**脚本中, 如中所示下图:</span><span class="sxs-lookup"><span data-stu-id="0e656-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="0e656-395">在 "**层次结构" 面板**中, 选择**主摄像机**的**GazeCursor**子。</span><span class="sxs-lookup"><span data-stu-id="0e656-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="0e656-396">在 "**检查器" 面板**中, 选择**GazeCursor** , 单击 "**添加组件**", 然后搜索 " **GazeCursor**脚本" 并双击, 以添加它。</span><span class="sxs-lookup"><span data-stu-id="0e656-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="0e656-397">同样, 在 "**层次结构" 面板**中, 选择**主摄像机**的**SpatialMapping**子项。</span><span class="sxs-lookup"><span data-stu-id="0e656-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="0e656-398">在 "**检查器" 面板**中, 选择**SpatialMapping** , 单击 "**添加组件**", 然后搜索 " **SpatialMapping**脚本" 并双击, 以添加它。</span><span class="sxs-lookup"><span data-stu-id="0e656-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="0e656-399">在运行时, **SceneOrganiser**脚本中的代码将添加未设置的其余脚本。</span><span class="sxs-lookup"><span data-stu-id="0e656-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="0e656-400">第12章-生成之前</span><span class="sxs-lookup"><span data-stu-id="0e656-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="0e656-401">若要对应用程序进行全面测试, 需要将其旁加载到 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0e656-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="0e656-402">在执行此操作之前, 请确保:</span><span class="sxs-lookup"><span data-stu-id="0e656-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="0e656-403">[第3章](#chapter-3---set-up-the-unity-project)中提到的所有设置都已正确设置。</span><span class="sxs-lookup"><span data-stu-id="0e656-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="0e656-404">脚本**SceneOrganiser**已附加到**摄像机主**对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="0e656-405">脚本**GazeCursor**附加到**GazeCursor**对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="0e656-406">脚本**SpatialMapping**附加到**SpatialMapping**对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="0e656-407">第[5 章](#chapter-5---create-the-customvisionanalyser-class)步骤 6:</span><span class="sxs-lookup"><span data-stu-id="0e656-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="0e656-408">请确保将**服务预测密钥**插入到**predictionKey**变量。</span><span class="sxs-lookup"><span data-stu-id="0e656-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="0e656-409">已将**预测终结点**插入到**predictionEndpoint**类中。</span><span class="sxs-lookup"><span data-stu-id="0e656-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="0e656-410">第13章-构建 UWP 解决方案并旁加载您的应用程序</span><span class="sxs-lookup"><span data-stu-id="0e656-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="0e656-411">现在, 你可以将应用程序构建为一个 UWP 解决方案, 你将能够将其部署到 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0e656-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="0e656-412">开始生成过程:</span><span class="sxs-lookup"><span data-stu-id="0e656-412">To begin the build process:</span></span>

1.  <span data-ttu-id="0e656-413">请参阅**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="0e656-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="0e656-414">勾选**Unity C\#项目**。</span><span class="sxs-lookup"><span data-stu-id="0e656-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="0e656-415">单击 "**添加打开的场景**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="0e656-416">这会将当前打开的场景添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="0e656-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="0e656-417">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="0e656-417">Click **Build**.</span></span> <span data-ttu-id="0e656-418">Unity 将启动*文件资源管理器*窗口, 在该窗口中, 需要创建一个文件夹, 然后选择要在其中生成应用的文件夹。</span><span class="sxs-lookup"><span data-stu-id="0e656-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="0e656-419">立即创建该文件夹并将其命名为**应用**。</span><span class="sxs-lookup"><span data-stu-id="0e656-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="0e656-420">选择**应用**文件夹后, 单击 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="0e656-421">Unity 将开始向**应用**文件夹生成项目。</span><span class="sxs-lookup"><span data-stu-id="0e656-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="0e656-422">Unity 完成生成 (可能需要一些时间) 后, 它会在生成的位置打开 "**文件资源管理器**" 窗口 (检查任务栏, 因为它可能不会始终出现在窗口之上, 但会通知你添加了一个新窗口)。</span><span class="sxs-lookup"><span data-stu-id="0e656-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="0e656-423">若要部署到 Microsoft HoloLens, 你将需要该设备的 IP 地址 (用于远程部署), 并确保它还设置了**开发人员模式**。</span><span class="sxs-lookup"><span data-stu-id="0e656-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="0e656-424">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="0e656-424">To do this:</span></span>

    1.  <span data-ttu-id="0e656-425">在戴上 HoloLens 的同时, 请打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="0e656-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="0e656-426">中转到**网络 & Internet** > **wi-fi** > **高级选项**</span><span class="sxs-lookup"><span data-stu-id="0e656-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="0e656-427">记下**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="0e656-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="0e656-428">接下来, 导航回 "**设置**", 然后为**开发人员** **更新 & 安全性** > </span><span class="sxs-lookup"><span data-stu-id="0e656-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="0e656-429">设置 **开发人员模式** *上* 。</span><span class="sxs-lookup"><span data-stu-id="0e656-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="0e656-430">导航到新的 Unity 生成 (**应用**文件夹), 并在**Visual Studio**中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="0e656-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="0e656-431">在解决方案配置中, 选择 "**调试**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="0e656-432">在解决方案平台中, 选择 " **x86, 远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="0e656-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="0e656-433">系统将提示你插入远程设备的**IP 地址**(在本例中, 你记下了此项)。</span><span class="sxs-lookup"><span data-stu-id="0e656-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="0e656-434">请在 "**生成**" 菜单中, 单击 "**部署解决方案**", 将应用程序旁加载到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="0e656-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="0e656-435">你的应用现在应显示在 Microsoft HoloLens 上已安装的应用列表中, 可以启动了!</span><span class="sxs-lookup"><span data-stu-id="0e656-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="0e656-436">使用应用程序:</span><span class="sxs-lookup"><span data-stu-id="0e656-436">To use the application:</span></span>

* <span data-ttu-id="0e656-437">查看已使用**Azure 自定义影像服务和对象检测**训练的对象, 并使用**点击手势**。</span><span class="sxs-lookup"><span data-stu-id="0e656-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="0e656-438">如果成功检测到该对象, 则会出现带有标记名称的世界空间*标签文本*。</span><span class="sxs-lookup"><span data-stu-id="0e656-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e656-439">每次捕获照片并将其发送到服务时, 您可以返回到 "服务" 页, 并使用新捕获的映像重新训练服务。</span><span class="sxs-lookup"><span data-stu-id="0e656-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="0e656-440">从一开始, 你可能还需要更正*边界框*, 使其更准确并重新训练服务。</span><span class="sxs-lookup"><span data-stu-id="0e656-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="0e656-441">当 Microsoft HoloLens 传感器和/或 Unity 中的 SpatialTrackingComponent 无法放置合适的 colliders (相对于真实世界对象) 时, 放置的标签文本可能不会出现在对象附近。</span><span class="sxs-lookup"><span data-stu-id="0e656-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="0e656-442">如果出现这种情况, 请尝试在不同的表面上使用该应用程序。</span><span class="sxs-lookup"><span data-stu-id="0e656-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="0e656-443">自定义视觉, 对象检测应用程序</span><span class="sxs-lookup"><span data-stu-id="0e656-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="0e656-444">恭喜, 你构建了一个利用 Azure 自定义视觉、对象检测 API 的混合现实应用, 该 API 可识别图像中的对象, 然后在3D 空间中为该对象提供大致位置。</span><span class="sxs-lookup"><span data-stu-id="0e656-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="0e656-445">额外练习</span><span class="sxs-lookup"><span data-stu-id="0e656-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="0e656-446">练习1</span><span class="sxs-lookup"><span data-stu-id="0e656-446">Exercise 1</span></span>

<span data-ttu-id="0e656-447">若要添加到文本标签, 请使用半透明的多维数据集包装 3D*边界框*中的实际对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="0e656-448">练习2</span><span class="sxs-lookup"><span data-stu-id="0e656-448">Exercise 2</span></span>

<span data-ttu-id="0e656-449">训练自定义影像服务来识别更多对象。</span><span class="sxs-lookup"><span data-stu-id="0e656-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="0e656-450">练习3</span><span class="sxs-lookup"><span data-stu-id="0e656-450">Exercise 3</span></span>

<span data-ttu-id="0e656-451">在识别对象时播放声音。</span><span class="sxs-lookup"><span data-stu-id="0e656-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="0e656-452">练习4</span><span class="sxs-lookup"><span data-stu-id="0e656-452">Exercise 4</span></span>

<span data-ttu-id="0e656-453">使用 API 来重新训练你的服务, 使其与你的应用程序正在分析的映像相同, 以便使该服务更准确 (同时执行预测和定型)。</span><span class="sxs-lookup"><span data-stu-id="0e656-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
