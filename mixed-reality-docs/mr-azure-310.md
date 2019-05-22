---
title: MR 和 Azure 310-对象检测
description: 完成此课程以了解如何定型机器学习模型，以及如何将训练的模型来识别类似对象和混合的现实应用程序中从现实世界中的位置。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure 中，自定义视觉对象检测，混合现实、 学院、 unity、 教程、 api、 hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590124"
---
>[!NOTE]
><span data-ttu-id="6d653-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="6d653-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="6d653-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="6d653-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="6d653-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="6d653-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="6d653-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="6d653-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="6d653-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="6d653-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="6d653-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="6d653-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="6d653-110">Mr 和 Azure 310:对象检测</span><span class="sxs-lookup"><span data-stu-id="6d653-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="6d653-111">在本课程中，您将学习如何识别自定义视觉对象的内容和其空间位置中提供的映像，使用 Azure 自定义影像混合的现实应用程序中的"对象检测"功能。</span><span class="sxs-lookup"><span data-stu-id="6d653-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="6d653-112">此服务将允许你定型机器学习模型，使用对象映像。</span><span class="sxs-lookup"><span data-stu-id="6d653-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="6d653-113">随后将使用经过训练的模型来识别类似对象和大约在现实生活中，其位置提供的 Microsoft HoloLens 相机捕捉或照相机连接到 PC 的沉浸式 (VR) 耳机。</span><span class="sxs-lookup"><span data-stu-id="6d653-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![课程结果](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="6d653-115">**Azure 自定义影像、 对象检测**是 Microsoft 服务，允许开发人员可以构建自定义图像分类器。</span><span class="sxs-lookup"><span data-stu-id="6d653-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="6d653-116">这些分类器可以随后可用于新的映像来检测该新映像中的对象，从而**框边界**于映像自身之中。</span><span class="sxs-lookup"><span data-stu-id="6d653-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="6d653-117">该服务提供一个简单、 易于使用、 在线门户，可简化此过程。</span><span class="sxs-lookup"><span data-stu-id="6d653-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="6d653-118">有关详细信息，请访问以下链接：</span><span class="sxs-lookup"><span data-stu-id="6d653-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="6d653-119">Azure 自定义视觉页</span><span class="sxs-lookup"><span data-stu-id="6d653-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="6d653-120">限制和配额</span><span class="sxs-lookup"><span data-stu-id="6d653-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="6d653-121">完成本课程时，之后您将拥有一个混合的现实应用程序，将能够执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6d653-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="6d653-122">用户将能够*注视*在它们具有经过培训的使用 Azure 自定义影像服务，对象检测的对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="6d653-123">用户将使用*点击*手势来捕获它们正在查看的内容的映像。</span><span class="sxs-lookup"><span data-stu-id="6d653-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="6d653-124">应用程序将映像发送到 Azure 自定义影像服务。</span><span class="sxs-lookup"><span data-stu-id="6d653-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="6d653-125">将会显示为世界空间文本识别结果的服务的答复。</span><span class="sxs-lookup"><span data-stu-id="6d653-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="6d653-126">这将通过利用 Microsoft HoloLens 的空间，作为跟踪的了解已识别的对象，世界位置，然后使用一种方法来实现*标记*与什么检测到在图中，为相关联提供的标签文本。</span><span class="sxs-lookup"><span data-stu-id="6d653-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="6d653-127">课程还将介绍手动上传的映像，创建标记，以及培训服务，可识别不同对象 （在提供的示例中，一杯），通过设置*边界框*提交的映像中。</span><span class="sxs-lookup"><span data-stu-id="6d653-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="6d653-128">以下的创建和使用应用，开发人员应导航回 Azure 自定义影像服务，并识别的预测进行了服务，并确定是否是正确还是不 (通过标记任何服务丢失，和调整*边界框*)。</span><span class="sxs-lookup"><span data-stu-id="6d653-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="6d653-129">该服务可以然后重新训练，这将提高它识别现实世界对象的可能性。</span><span class="sxs-lookup"><span data-stu-id="6d653-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="6d653-130">本课程将介绍如何将结果从 Azure 自定义影像服务，对象检测到基于 Unity 的示例应用程序。</span><span class="sxs-lookup"><span data-stu-id="6d653-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="6d653-131">它将取决于您要应用于您可能要构建一个自定义应用程序的这些概念。</span><span class="sxs-lookup"><span data-stu-id="6d653-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="6d653-132">设备支持</span><span class="sxs-lookup"><span data-stu-id="6d653-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="6d653-133">课程</span><span class="sxs-lookup"><span data-stu-id="6d653-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="6d653-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6d653-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6d653-135"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="6d653-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="6d653-136">MR 和 Azure 310:对象检测</span><span class="sxs-lookup"><span data-stu-id="6d653-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="6d653-137">✔️</span><span class="sxs-lookup"><span data-stu-id="6d653-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="6d653-138">系统必备</span><span class="sxs-lookup"><span data-stu-id="6d653-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="6d653-139">本教程专为开发人员已基本熟悉 Unity 和C#。</span><span class="sxs-lookup"><span data-stu-id="6d653-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="6d653-140">此外需要注意的先决条件和本文档内的书面的说明表示什么已测试并验证在撰写本文时 (2018 年 7 月)。</span><span class="sxs-lookup"><span data-stu-id="6d653-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="6d653-141">你可以随意使用最新的软件，如中所列[安装的工具](https://docs.microsoft.com/windows/mixed-reality/install-the-tools)文章中，但它不应假定本课程中的信息将完全匹配将在较新软件比列中找到的内容下面。</span><span class="sxs-lookup"><span data-stu-id="6d653-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="6d653-142">我们建议以下硬件和软件本课程：</span><span class="sxs-lookup"><span data-stu-id="6d653-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="6d653-143">开发计算机</span><span class="sxs-lookup"><span data-stu-id="6d653-143">A development PC</span></span>
- [<span data-ttu-id="6d653-144">Windows 10 Fall Creators Update （或更高版本） 开发人员模式下启用</span><span class="sxs-lookup"><span data-stu-id="6d653-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="6d653-145">最新的 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="6d653-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="6d653-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="6d653-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="6d653-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="6d653-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="6d653-148">一个[Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)启用开发人员模式</span><span class="sxs-lookup"><span data-stu-id="6d653-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="6d653-149">为 Azure 安装和自定义影像服务检索的 Internet 访问权限</span><span class="sxs-lookup"><span data-stu-id="6d653-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="6d653-150">一系列至少十五 （15） 图像是必需的） 为你想自定义视觉识别每个对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="6d653-151">如果愿意，可以使用与本课程中，已提供的映像[的 cup 的一系列](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="6d653-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="6d653-152">开始之前</span><span class="sxs-lookup"><span data-stu-id="6d653-152">Before you start</span></span>

1.  <span data-ttu-id="6d653-153">若要避免遇到生成此项目的问题，强烈建议您创建在本教程中所述，在根或接近根文件夹中的项目 （长文件夹路径可能会导致在生成时的问题）。</span><span class="sxs-lookup"><span data-stu-id="6d653-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="6d653-154">设置和测试你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6d653-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="6d653-155">如果需要支持设置你 HoloLens[请确保访问 HoloLens 安装文章](https://docs.microsoft.com/hololens/hololens-setup)。</span><span class="sxs-lookup"><span data-stu-id="6d653-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="6d653-156">它是一个好办法开始开发新 HoloLens 应用程序 （有时它可帮助执行这些任务的每个用户） 时执行校准和优化传感器。</span><span class="sxs-lookup"><span data-stu-id="6d653-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="6d653-157">有关校准的帮助，请遵循此[HoloLens 校准文章链接](calibration.md#hololens)。</span><span class="sxs-lookup"><span data-stu-id="6d653-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="6d653-158">有关传感器优化的帮助，请遵循此[HoloLens 传感器优化文章链接](sensor-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="6d653-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="6d653-159">第 1 章-自定义影像门户</span><span class="sxs-lookup"><span data-stu-id="6d653-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="6d653-160">若要使用**Azure 自定义影像服务**，将需要配置它以可供你的应用程序的实例。</span><span class="sxs-lookup"><span data-stu-id="6d653-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="6d653-161">导航[到**自定义影像服务**主页](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)。</span><span class="sxs-lookup"><span data-stu-id="6d653-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="6d653-162">单击**入门**。</span><span class="sxs-lookup"><span data-stu-id="6d653-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="6d653-163">登录到自定义影像门户。</span><span class="sxs-lookup"><span data-stu-id="6d653-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="6d653-164">如果你还没有 Azure 帐户，你需要创建一个。</span><span class="sxs-lookup"><span data-stu-id="6d653-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="6d653-165">如果您按照本教程中在课堂或实验室的情况下，要求教师或新帐户的帮助设置 proctors 之一。</span><span class="sxs-lookup"><span data-stu-id="6d653-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="6d653-166">登录第一次，系统会提示使用*服务条款*面板。</span><span class="sxs-lookup"><span data-stu-id="6d653-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="6d653-167">单击复选框*即表示同意条款*。</span><span class="sxs-lookup"><span data-stu-id="6d653-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="6d653-168">然后单击**我同意**。</span><span class="sxs-lookup"><span data-stu-id="6d653-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="6d653-169">具有同意这些条款，你现在处于*我的项目*部分。</span><span class="sxs-lookup"><span data-stu-id="6d653-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="6d653-170">单击**新的项目**。</span><span class="sxs-lookup"><span data-stu-id="6d653-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="6d653-171">将提示你指定项目的某些字段的右侧将显示一个选项卡。</span><span class="sxs-lookup"><span data-stu-id="6d653-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="6d653-172">插入你的项目的名称</span><span class="sxs-lookup"><span data-stu-id="6d653-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="6d653-173">插入你的项目的说明 (**可选**)</span><span class="sxs-lookup"><span data-stu-id="6d653-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="6d653-174">选择**资源组**或新建一个。</span><span class="sxs-lookup"><span data-stu-id="6d653-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="6d653-175">资源组提供了一种方法来监视、 控制访问，预配和管理 Azure 资产的集合的计费。</span><span class="sxs-lookup"><span data-stu-id="6d653-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="6d653-176">建议尽量与常见的资源组下的单个项目 （例如如这些课程） 相关联的所有 Azure 服务）。</span><span class="sxs-lookup"><span data-stu-id="6d653-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="6d653-177">如果想要对[阅读更多有关 Azure 资源组中，导航到相关联的文档](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="6d653-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="6d653-178">设置**项目类型**作为**对象检测 （预览版）**。</span><span class="sxs-lookup"><span data-stu-id="6d653-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="6d653-179">完成后，单击**创建项目**，并且将重定向到自定义影像服务项目页。</span><span class="sxs-lookup"><span data-stu-id="6d653-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="6d653-180">第 2 章-培训您的自定义视觉项目</span><span class="sxs-lookup"><span data-stu-id="6d653-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="6d653-181">一次在自定义视觉门户中，您的主要目标是训练你的项目以识别图像中的特定对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="6d653-182">你想要识别您应用程序的每个对象需要至少 15 （15） 映像。</span><span class="sxs-lookup"><span data-stu-id="6d653-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="6d653-183">可以使用与本课程提供的映像 ([的 cup 的一系列](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))。</span><span class="sxs-lookup"><span data-stu-id="6d653-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="6d653-184">若要训练你的自定义视觉项目：</span><span class="sxs-lookup"><span data-stu-id="6d653-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="6d653-185">单击 **+** 按钮旁边**标记**。</span><span class="sxs-lookup"><span data-stu-id="6d653-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="6d653-186">添加**名称**将用于将与映像相关联的标记。</span><span class="sxs-lookup"><span data-stu-id="6d653-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="6d653-187">在此示例中我们是用于识别，因此具有称为标记为此，使用的 cup 的映像**杯**。</span><span class="sxs-lookup"><span data-stu-id="6d653-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="6d653-188">单击**保存**一次完成。</span><span class="sxs-lookup"><span data-stu-id="6d653-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="6d653-189">你会注意到您**标记**已添加 （可能需要重新加载它才会显示在页面）。</span><span class="sxs-lookup"><span data-stu-id="6d653-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="6d653-190">单击**将图像添加**中页的中心。</span><span class="sxs-lookup"><span data-stu-id="6d653-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="6d653-191">单击**浏览本地文件**，并浏览到你想要为一个对象，最小正在十五 (15) 上传的映像。</span><span class="sxs-lookup"><span data-stu-id="6d653-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="6d653-192">一次，若要上传，可以选择多个映像。</span><span class="sxs-lookup"><span data-stu-id="6d653-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="6d653-193">按**将文件上传**选择所有映像后你想要训练的项目。</span><span class="sxs-lookup"><span data-stu-id="6d653-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="6d653-194">随即开始将文件上传。</span><span class="sxs-lookup"><span data-stu-id="6d653-194">The files will begin uploading.</span></span> <span data-ttu-id="6d653-195">上传的确认后，单击**完成**。</span><span class="sxs-lookup"><span data-stu-id="6d653-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="6d653-196">此时你的映像上传，但不是会标记。</span><span class="sxs-lookup"><span data-stu-id="6d653-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="6d653-197">若要标记你的映像，使用鼠标。</span><span class="sxs-lookup"><span data-stu-id="6d653-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="6d653-198">将鼠标指针悬停在图像上，选择突出显示将帮助您通过自动绘制围绕你的对象选择。</span><span class="sxs-lookup"><span data-stu-id="6d653-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="6d653-199">如果不准确，则可以绘制自己。</span><span class="sxs-lookup"><span data-stu-id="6d653-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="6d653-200">这一点通过持有鼠标左键单击和拖动所选区域，以包含您的对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="6d653-201">以下图像中对象的所选内容，小提示将要求你能够*添加区域标记*。</span><span class="sxs-lookup"><span data-stu-id="6d653-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="6d653-202">选择你以前创建的标记 （创新杯，在上面的示例），或者如果在添加更多标记，类型中，单击 **+ （加）** 按钮。</span><span class="sxs-lookup"><span data-stu-id="6d653-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="6d653-203">若要标记的下一步的映像，可以单击边栏选项卡中，右侧的箭头，或关闭标记边栏选项卡 (通过单击**X**边栏选项卡的右上角)，然后单击下一幅图像。</span><span class="sxs-lookup"><span data-stu-id="6d653-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="6d653-204">下一步的映像准备就绪后，重复相同的过程。</span><span class="sxs-lookup"><span data-stu-id="6d653-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="6d653-205">已上传，直到它们所有标记的所有映像执行此都操作。</span><span class="sxs-lookup"><span data-stu-id="6d653-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="6d653-206">在同一个映像，类似于下图中，可以选择多个对象：</span><span class="sxs-lookup"><span data-stu-id="6d653-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="6d653-207">一旦已标记所有这些，则单击**标记**按钮左侧的屏幕上，以显示标记的映像。</span><span class="sxs-lookup"><span data-stu-id="6d653-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="6d653-208">现在您就可以训练你的服务。</span><span class="sxs-lookup"><span data-stu-id="6d653-208">You are now ready to train your Service.</span></span> <span data-ttu-id="6d653-209">单击**训练**按钮和第一次训练迭代将开始。</span><span class="sxs-lookup"><span data-stu-id="6d653-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="6d653-210">一旦建立，您将能够看到两个按钮名为**设为默认**并**预测 URL**。</span><span class="sxs-lookup"><span data-stu-id="6d653-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="6d653-211">单击**设为默认**第一次，然后单击**预测 URL**。</span><span class="sxs-lookup"><span data-stu-id="6d653-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="6d653-212">此操作，请从提供的终结点设置为准*迭代*已被标记为默认值。</span><span class="sxs-lookup"><span data-stu-id="6d653-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="6d653-213">同样，如果您更高版本进行的新*迭代*和更新为默认值，不需要更改代码。</span><span class="sxs-lookup"><span data-stu-id="6d653-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="6d653-214">一旦你单击**预测 URL**，打开*记事本*，然后复制并粘贴**URL** (也称为你**预测终结点**)并**服务预测密钥**，以便可在需要更高版本在代码中时进行检索。</span><span class="sxs-lookup"><span data-stu-id="6d653-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="6d653-215">第 3 章 — 设置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="6d653-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="6d653-216">以下是一组典型使用混合现实，进行开发，并在这种情况下，是合适的模板的其他项目。</span><span class="sxs-lookup"><span data-stu-id="6d653-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="6d653-217">打开**Unity**然后单击**新建**。</span><span class="sxs-lookup"><span data-stu-id="6d653-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="6d653-218">现在，需要提供的 Unity 项目名称。</span><span class="sxs-lookup"><span data-stu-id="6d653-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="6d653-219">插入**CustomVisionObjDetection**。</span><span class="sxs-lookup"><span data-stu-id="6d653-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="6d653-220">请确保项目类型设置为**三维**，并设置**位置**到适合于您的某个位置 （请记住，更接近于根目录是更好）。</span><span class="sxs-lookup"><span data-stu-id="6d653-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="6d653-221">然后，单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="6d653-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="6d653-222">使用 Unity 打开，它是值得选择，默认值**脚本编辑器**设置为**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="6d653-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="6d653-223">转到 **编辑* > *首选项** ，然后在新窗口中，导航到 **外部工具** 。</span><span class="sxs-lookup"><span data-stu-id="6d653-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="6d653-224">更改**外部脚本编辑器**到**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="6d653-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="6d653-225">关闭**首选项**窗口。</span><span class="sxs-lookup"><span data-stu-id="6d653-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="6d653-226">接下来，请转到**文件 > 生成设置**，并切换**平台**到*通用 Windows 平台*，然后单击**切换平台**按钮。</span><span class="sxs-lookup"><span data-stu-id="6d653-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="6d653-227">在同一**生成设置**窗口中，确保将以下项设置：</span><span class="sxs-lookup"><span data-stu-id="6d653-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="6d653-228">**设备为目标**设置为**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="6d653-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="6d653-229">**生成的类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="6d653-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="6d653-230">**SDK**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="6d653-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="6d653-231">**Visual Studio 版本**设置为**最新安装**</span><span class="sxs-lookup"><span data-stu-id="6d653-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="6d653-232">**生成并运行**设置为**本地计算机**</span><span class="sxs-lookup"><span data-stu-id="6d653-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="6d653-233">中的剩余设置，**生成设置**，应暂时保留为默认值。</span><span class="sxs-lookup"><span data-stu-id="6d653-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="6d653-234">在同一**生成设置**窗口中，单击**播放器设置**按钮，这将打开相关面板中的空间中的**检查器**所在。</span><span class="sxs-lookup"><span data-stu-id="6d653-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="6d653-235">在此面板中，需要验证几个设置：</span><span class="sxs-lookup"><span data-stu-id="6d653-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="6d653-236">在中**其他设置**选项卡：</span><span class="sxs-lookup"><span data-stu-id="6d653-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="6d653-237">**脚本运行时版本**应**实验**（.NET 4.6 等效），这将触发需要重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="6d653-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="6d653-238">**脚本编写后端**应 **.NET**。</span><span class="sxs-lookup"><span data-stu-id="6d653-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="6d653-239">**API 兼容性级别**应 **.NET 4.6**。</span><span class="sxs-lookup"><span data-stu-id="6d653-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="6d653-240">内**发布设置**选项卡上，在**功能**，检查：</span><span class="sxs-lookup"><span data-stu-id="6d653-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="6d653-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="6d653-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="6d653-242">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="6d653-242">**Webcam**</span></span>

        3. <span data-ttu-id="6d653-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="6d653-243">**SpatialPerception**</span></span>

            <span data-ttu-id="6d653-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="6d653-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="6d653-245">中的后面部分面板**XR 设置**(下面找到**发布设置**)，刻度线**虚拟现实支持**，然后确保**Windows 混合现实 SDK**添加。</span><span class="sxs-lookup"><span data-stu-id="6d653-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="6d653-246">回到**生成设置**， *Unity C\#项目*不再灰显： 选中此旁边的复选框。</span><span class="sxs-lookup"><span data-stu-id="6d653-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="6d653-247">关闭**生成设置**窗口。</span><span class="sxs-lookup"><span data-stu-id="6d653-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="6d653-248">在中**编辑器**，单击**编辑** > **项目设置** > **图形**。</span><span class="sxs-lookup"><span data-stu-id="6d653-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="6d653-249">在中\**检查器面板\*\*\*图形设置*则会打开。</span><span class="sxs-lookup"><span data-stu-id="6d653-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="6d653-250">向下滚动直到您看到名为的数组**始终包括着色器**。</span><span class="sxs-lookup"><span data-stu-id="6d653-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="6d653-251">通过增加添加槽**大小**由一个变量 (在此示例中，它是 8 以便我们进行 9)。</span><span class="sxs-lookup"><span data-stu-id="6d653-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="6d653-252">新的槽将显示，在该数组的最后一个位置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6d653-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="6d653-253">在槽中，单击旁边的槽以打开着色器的列表的较小的目标圆形。</span><span class="sxs-lookup"><span data-stu-id="6d653-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="6d653-254">寻找**旧版着色器/透明/漫射**着色器，然后双击它。</span><span class="sxs-lookup"><span data-stu-id="6d653-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="6d653-255">第 4 章-导入 CustomVisionObjDetection Unity 程序包</span><span class="sxs-lookup"><span data-stu-id="6d653-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="6d653-256">为名为 Unity 资产包向您提供本课程**Azure MR 310.unitypackage**。</span><span class="sxs-lookup"><span data-stu-id="6d653-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="6d653-257">[提示]支持 Unity，包括整个场景的任何对象可以打包到 **.unitypackage**文件，并导出 / 导入在其他项目中。</span><span class="sxs-lookup"><span data-stu-id="6d653-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="6d653-258">它是不同之间移动资产的最安全的且最有效方法**Unity 项目**。</span><span class="sxs-lookup"><span data-stu-id="6d653-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="6d653-259">您可以找到[需要在此处下载 Azure MR 310 包](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)。</span><span class="sxs-lookup"><span data-stu-id="6d653-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="6d653-260">准备好 Unity 仪表板中，单击**资产**在屏幕顶部的菜单，然后单击**导入包 > 自定义包**。</span><span class="sxs-lookup"><span data-stu-id="6d653-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="6d653-261">使用文件选取器选择**Azure MR 310.unitypackage**程序包，再单击**打开**。</span><span class="sxs-lookup"><span data-stu-id="6d653-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="6d653-262">将向你显示此资产的组件的列表。</span><span class="sxs-lookup"><span data-stu-id="6d653-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="6d653-263">通过单击确认导入**导入**按钮。</span><span class="sxs-lookup"><span data-stu-id="6d653-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="6d653-264">完成导入后，会注意到，从包文件夹现在已添加到您**资产**文件夹。</span><span class="sxs-lookup"><span data-stu-id="6d653-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="6d653-265">此类文件夹结构是典型的 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="6d653-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="6d653-266">**材料**文件夹包含由使用的材料**注视游标**。</span><span class="sxs-lookup"><span data-stu-id="6d653-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="6d653-267">**插件**文件夹包含 Newtonsoft DLL 代码用于反序列化服务的 web 响应。</span><span class="sxs-lookup"><span data-stu-id="6d653-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="6d653-268">两个 （2） 不同版本的文件夹和子文件夹中包含所需允许使用和生成的 Unity 编辑器和 UWP 生成的库。</span><span class="sxs-lookup"><span data-stu-id="6d653-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="6d653-269">**预设**文件夹包含在场景中包含预设。</span><span class="sxs-lookup"><span data-stu-id="6d653-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="6d653-270">这些情况包括：</span><span class="sxs-lookup"><span data-stu-id="6d653-270">Those are:</span></span>

        1.  <span data-ttu-id="6d653-271">**GazeCursor**，应用程序中使用的光标。</span><span class="sxs-lookup"><span data-stu-id="6d653-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="6d653-272">将工作以及 SpatialMapping 预设可以基于物理对象在场景中放置。</span><span class="sxs-lookup"><span data-stu-id="6d653-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="6d653-273">**标签**，是用于在需要时在场景中显示的对象标记的用户界面对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="6d653-274">**SpatialMapping**，这是创建虚拟映射中，使用 Microsoft HoloLens ' 空间跟踪使应用程序使用的对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="6d653-275">**场景**文件夹当前包含本课程的预建的场景。</span><span class="sxs-lookup"><span data-stu-id="6d653-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="6d653-276">打开**场景**文件夹，请在**项目面板**，然后双击**ObjDetectionScene**、 要加载的场景的将用于此课程。</span><span class="sxs-lookup"><span data-stu-id="6d653-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="6d653-277">**不不包含任何代码**，将按照本课程中编写的代码。</span><span class="sxs-lookup"><span data-stu-id="6d653-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="6d653-278">章节 5-创建 CustomVisionAnalyser 类。</span><span class="sxs-lookup"><span data-stu-id="6d653-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="6d653-279">此时已准备好编写一些代码。</span><span class="sxs-lookup"><span data-stu-id="6d653-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="6d653-280">您将首先**CustomVisionAnalyser**类。</span><span class="sxs-lookup"><span data-stu-id="6d653-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="6d653-281">对调用**自定义影像服务**，如下所示的代码中，所用**自定义视觉 REST API**。</span><span class="sxs-lookup"><span data-stu-id="6d653-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="6d653-282">通过使用此，您将学会如何实现并使用此 api （适用于了解如何在您自己实现类似的内容）。</span><span class="sxs-lookup"><span data-stu-id="6d653-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="6d653-283">请注意，Microsoft 提供了**自定义视觉 SDK** ，还可用于对服务进行调用。</span><span class="sxs-lookup"><span data-stu-id="6d653-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="6d653-284">有关详细信息，请访问[自定义视觉 SDK 文章](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)。</span><span class="sxs-lookup"><span data-stu-id="6d653-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="6d653-285">此类负责：</span><span class="sxs-lookup"><span data-stu-id="6d653-285">This class is responsible for:</span></span>

- <span data-ttu-id="6d653-286">正在加载最新的映像捕获为一个字节数组。</span><span class="sxs-lookup"><span data-stu-id="6d653-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="6d653-287">将字节数组发送到你的 Azure**自定义影像服务**实例以进行分析。</span><span class="sxs-lookup"><span data-stu-id="6d653-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="6d653-288">接收响应以 JSON 字符串。</span><span class="sxs-lookup"><span data-stu-id="6d653-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="6d653-289">反序列化响应并传递得到**预测**到**SceneOrganiser**类，该类将负责响应的显示方式。</span><span class="sxs-lookup"><span data-stu-id="6d653-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="6d653-290">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="6d653-290">To create this class:</span></span>

1.  <span data-ttu-id="6d653-291">在中右击**资产文件夹**，它位于**项目面板**，然后单击**创建** > **文件夹**。</span><span class="sxs-lookup"><span data-stu-id="6d653-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="6d653-292">将该文件夹**脚本**。</span><span class="sxs-lookup"><span data-stu-id="6d653-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="6d653-293">双击新创建的文件夹，以将其打开。</span><span class="sxs-lookup"><span data-stu-id="6d653-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="6d653-294">在文件夹中，右键单击，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="6d653-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="6d653-295">脚本命名为**CustomVisionAnalyser。**</span><span class="sxs-lookup"><span data-stu-id="6d653-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="6d653-296">双击新**CustomVisionAnalyser**脚本以将其与打开**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="6d653-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="6d653-297">请确保具有以下命名空间引用该文件顶部：</span><span class="sxs-lookup"><span data-stu-id="6d653-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="6d653-298">在中**CustomVisionAnalyser**类中，添加以下变量：</span><span class="sxs-lookup"><span data-stu-id="6d653-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

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
    > <span data-ttu-id="6d653-299">请确保插入你**服务预测密钥**到**predictionKey**变量和你**预测终结点**到**predictionEndpoint**变量。</span><span class="sxs-lookup"><span data-stu-id="6d653-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="6d653-300">复制到[记事本更早版本，在第 2 章，步骤 14](#chapter-2---training-your-custom-vision-project)。</span><span class="sxs-lookup"><span data-stu-id="6d653-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="6d653-301">为代码**Awake()** 现在需要添加初始化该实例变量：</span><span class="sxs-lookup"><span data-stu-id="6d653-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="6d653-302">添加协同程序 (使用静态**GetImageAsByteArray()** 它下面的方法)，这将获取由捕获的图像的分析结果**ImageCapture**类。</span><span class="sxs-lookup"><span data-stu-id="6d653-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6d653-303">在中**AnalyseImageCapture**协同程序，没有调用**SceneOrganiser**尚若要创建的类。</span><span class="sxs-lookup"><span data-stu-id="6d653-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="6d653-304">因此，**保留这些行注释现在**。</span><span class="sxs-lookup"><span data-stu-id="6d653-304">Therefore, **leave those lines commented for now**.</span></span>

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

9. <span data-ttu-id="6d653-305">删除**start （)** 并**update （)** 方法，因为它们不会使用。</span><span class="sxs-lookup"><span data-stu-id="6d653-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="6d653-306">请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="6d653-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d653-307">前面曾提到，不必担心可能显示为具有错误，因为您将进一步提供类，也可解决这些代码。</span><span class="sxs-lookup"><span data-stu-id="6d653-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="6d653-308">章 6-创建 CustomVisionObjects 类</span><span class="sxs-lookup"><span data-stu-id="6d653-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="6d653-309">现在，您将创建的类是**CustomVisionObjects**类。</span><span class="sxs-lookup"><span data-stu-id="6d653-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="6d653-310">此脚本包含多个对象由其他类用于序列化和反序列化对自定义影像服务所做的调用。</span><span class="sxs-lookup"><span data-stu-id="6d653-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="6d653-311">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="6d653-311">To create this class:</span></span>

1.  <span data-ttu-id="6d653-312">内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="6d653-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="6d653-313">调用脚本**CustomVisionObjects。**</span><span class="sxs-lookup"><span data-stu-id="6d653-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="6d653-314">双击新**CustomVisionObjects**脚本以将其与打开**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="6d653-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="6d653-315">请确保具有以下命名空间引用该文件顶部：</span><span class="sxs-lookup"><span data-stu-id="6d653-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="6d653-316">删除**start （)** 并**update （)** 中的方法**CustomVisionObjects**类，该类现在应为空。</span><span class="sxs-lookup"><span data-stu-id="6d653-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="6d653-317">请务必仔细按照下一条指令。</span><span class="sxs-lookup"><span data-stu-id="6d653-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="6d653-318">如果将放在新的类声明**CustomVisionObjects**类，您将在出现编译错误[第 10 章](#chapter-10---create-the-imagecapture-class)，指出该**AnalysisRootObject**和**BoundingBox**找不到。</span><span class="sxs-lookup"><span data-stu-id="6d653-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="6d653-319">添加以下类*外部* **CustomVisionObjects**类。</span><span class="sxs-lookup"><span data-stu-id="6d653-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="6d653-320">这些对象由**Newtonsoft**库进行序列化和反序列化响应数据：</span><span class="sxs-lookup"><span data-stu-id="6d653-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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

6.  <span data-ttu-id="6d653-321">请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="6d653-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="6d653-322">章 7-创建 SpatialMapping 类</span><span class="sxs-lookup"><span data-stu-id="6d653-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="6d653-323">此类将设置**空间映射碰撞体**场景，因此，若要能够检测到虚拟对象与真实的对象之间的冲突中。</span><span class="sxs-lookup"><span data-stu-id="6d653-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="6d653-324">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="6d653-324">To create this class:</span></span>

1.  <span data-ttu-id="6d653-325">内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="6d653-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="6d653-326">调用脚本**SpatialMapping。**</span><span class="sxs-lookup"><span data-stu-id="6d653-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="6d653-327">双击新**SpatialMapping**脚本以将其与打开**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="6d653-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="6d653-328">请确保具有上面引用的以下命名空间**SpatialMapping**类：</span><span class="sxs-lookup"><span data-stu-id="6d653-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="6d653-329">然后，添加以下变量内的**SpatialMapping**类，更高版本**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="6d653-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="6d653-330">添加**Awake()** 并**start （)**:</span><span class="sxs-lookup"><span data-stu-id="6d653-330">Add the **Awake()** and **Start()**:</span></span>

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

6.  <span data-ttu-id="6d653-331">删除**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="6d653-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="6d653-332">请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="6d653-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="6d653-333">章 8-创建 GazeCursor 类</span><span class="sxs-lookup"><span data-stu-id="6d653-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="6d653-334">此类负责在实际空间中，正确的位置设置游标通过利用**SpatialMappingCollider**上一章中创建。</span><span class="sxs-lookup"><span data-stu-id="6d653-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="6d653-335">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="6d653-335">To create this class:</span></span>

1.  <span data-ttu-id="6d653-336">内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="6d653-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="6d653-337">调用脚本**GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="6d653-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="6d653-338">双击新**GazeCursor**脚本以将其与打开**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="6d653-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="6d653-339">请确保具有上面引用的以下命名空间**GazeCursor**类：</span><span class="sxs-lookup"><span data-stu-id="6d653-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="6d653-340">然后添加以下变量内的**GazeCursor**类，更高版本**start （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="6d653-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="6d653-341">更新**start （)** 方法使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="6d653-341">Update the **Start()** method with the following code:</span></span>

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

6.  <span data-ttu-id="6d653-342">更新**update （)** 方法使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="6d653-342">Update the **Update()** method with the following code:</span></span>

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
    > <span data-ttu-id="6d653-343">有关的错误，请不要担心**SceneOrganiser**类找不到，您将在下一章中创建它。</span><span class="sxs-lookup"><span data-stu-id="6d653-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="6d653-344">请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="6d653-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="6d653-345">章 9-创建 SceneOrganiser 类</span><span class="sxs-lookup"><span data-stu-id="6d653-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="6d653-346">将此类：</span><span class="sxs-lookup"><span data-stu-id="6d653-346">This class will:</span></span>

-   <span data-ttu-id="6d653-347">设置*Main Camera*通过附加到适当的组件。</span><span class="sxs-lookup"><span data-stu-id="6d653-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="6d653-348">检测到一个对象时，它将负责计算它的实际和位置中的位置**标记标签**附近使用相应**标记名称**。</span><span class="sxs-lookup"><span data-stu-id="6d653-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="6d653-349">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="6d653-349">To create this class:</span></span>

1.  <span data-ttu-id="6d653-350">内右击**脚本**文件夹，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="6d653-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="6d653-351">脚本命名为**SceneOrganiser**。</span><span class="sxs-lookup"><span data-stu-id="6d653-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="6d653-352">双击新**SceneOrganiser**脚本以将其与打开**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="6d653-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="6d653-353">请确保具有上面引用的以下命名空间**SceneOrganiser**类：</span><span class="sxs-lookup"><span data-stu-id="6d653-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="6d653-354">然后添加以下变量内的**SceneOrganiser**类，更高版本**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="6d653-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="6d653-355">删除**start （)** 并**update （)** 方法。</span><span class="sxs-lookup"><span data-stu-id="6d653-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="6d653-356">变量后下, 添加**Awake()** 方法，它将初始化类并设置场景。</span><span class="sxs-lookup"><span data-stu-id="6d653-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="6d653-357">添加**PlaceAnalysisLabel()** 方法，将*实例化*场景 （即现在用户看不到） 中的标签。</span><span class="sxs-lookup"><span data-stu-id="6d653-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="6d653-358">它还会提供四 （还不可见） 映像放置，以及与现实世界重叠。</span><span class="sxs-lookup"><span data-stu-id="6d653-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="6d653-359">这非常重要，因为分析追溯到此四确定现实世界中的对象的近似位置后，从服务检索框坐标。</span><span class="sxs-lookup"><span data-stu-id="6d653-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

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

8.  <span data-ttu-id="6d653-360">添加**FinaliseLabel()** 方法。</span><span class="sxs-lookup"><span data-stu-id="6d653-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="6d653-361">它负责：</span><span class="sxs-lookup"><span data-stu-id="6d653-361">It is responsible for:</span></span>

    *   <span data-ttu-id="6d653-362">设置*标签*带有文本*标记*的最高的信心十足地预测。</span><span class="sxs-lookup"><span data-stu-id="6d653-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="6d653-363">调用的计算*边界框*以前，定位的四部分对象和将标签放在场景中。</span><span class="sxs-lookup"><span data-stu-id="6d653-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="6d653-364">通过使用针对 Raycast 调整标签深度*边界框*，这应碰撞现实世界中的对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="6d653-365">正在重置，捕获进程才能允许用户以捕获另一个映像。</span><span class="sxs-lookup"><span data-stu-id="6d653-365">Resetting the capture process to allow the user to capture another image.</span></span>

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

9.  <span data-ttu-id="6d653-366">添加**CalculateBoundingBoxPosition()** 方法，它托管的转换所必需的计算数量*边界框*坐标从服务检索和重新创建它们按比例上四。</span><span class="sxs-lookup"><span data-stu-id="6d653-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

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

10. <span data-ttu-id="6d653-367">请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="6d653-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="6d653-368">在继续之前，打开**CustomVisionAnalyser**类，并在**AnalyseLastImageCaptured()** 方法，*取消注释*以下行：</span><span class="sxs-lookup"><span data-stu-id="6d653-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
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
> <span data-ttu-id="6d653-369">不要担心**ImageCapture**类无法找到消息中，你将在下一章中创建它。</span><span class="sxs-lookup"><span data-stu-id="6d653-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="6d653-370">章 10-创建 ImageCapture 类</span><span class="sxs-lookup"><span data-stu-id="6d653-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="6d653-371">要创建的下一步类是**ImageCapture**类。</span><span class="sxs-lookup"><span data-stu-id="6d653-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="6d653-372">此类负责：</span><span class="sxs-lookup"><span data-stu-id="6d653-372">This class is responsible for:</span></span>

*   <span data-ttu-id="6d653-373">捕获映像使用 HoloLens 相机并将其存储在*应用*文件夹。</span><span class="sxs-lookup"><span data-stu-id="6d653-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="6d653-374">处理*点击*用户手势。</span><span class="sxs-lookup"><span data-stu-id="6d653-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="6d653-375">若要创建此类：</span><span class="sxs-lookup"><span data-stu-id="6d653-375">To create this class:</span></span>

1.  <span data-ttu-id="6d653-376">转到**脚本**之前创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6d653-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="6d653-377">在文件夹中，右键单击，然后单击**创建** > **C\#脚本**。</span><span class="sxs-lookup"><span data-stu-id="6d653-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="6d653-378">脚本命名为**ImageCapture**。</span><span class="sxs-lookup"><span data-stu-id="6d653-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="6d653-379">双击新**ImageCapture**脚本以将其与打开**Visual Studio。**</span><span class="sxs-lookup"><span data-stu-id="6d653-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="6d653-380">使用以下内容替换该文件顶部的命名空间：</span><span class="sxs-lookup"><span data-stu-id="6d653-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="6d653-381">然后添加以下变量内的**ImageCapture**类，更高版本**start （)** 方法：</span><span class="sxs-lookup"><span data-stu-id="6d653-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="6d653-382">为代码**Awake()** 并**start （)** 方法现在需要添加：</span><span class="sxs-lookup"><span data-stu-id="6d653-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="6d653-383">实现的点击动作时将调用的处理程序：</span><span class="sxs-lookup"><span data-stu-id="6d653-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

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
    > <span data-ttu-id="6d653-384">当光标位于**绿色**，则意味着照相机是可用于获取映像。</span><span class="sxs-lookup"><span data-stu-id="6d653-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="6d653-385">当光标位于**红色**，这意味着照相机正忙。</span><span class="sxs-lookup"><span data-stu-id="6d653-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="6d653-386">添加应用程序使用启动映像捕获过程并将图像存储的方法：</span><span class="sxs-lookup"><span data-stu-id="6d653-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

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

9.  <span data-ttu-id="6d653-387">添加捕获照片和时准备好对其进行分析将调用处理程序。</span><span class="sxs-lookup"><span data-stu-id="6d653-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="6d653-388">然后将结果传递给**CustomVisionAnalyser**进行分析。</span><span class="sxs-lookup"><span data-stu-id="6d653-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

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

10. <span data-ttu-id="6d653-389">请务必保存中所做的更改**Visual Studio**，然后再返回到**Unity**。</span><span class="sxs-lookup"><span data-stu-id="6d653-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="6d653-390">第 11 章 — 设置场景中的脚本</span><span class="sxs-lookup"><span data-stu-id="6d653-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="6d653-391">现在，您编写所有此项目所必需，是代码的时候若要设置在场景中和在预设，才能正常运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="6d653-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="6d653-392">内**Unity 编辑器**，在**层次结构面板**，选择**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="6d653-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="6d653-393">在中**检查器面板**，使用**Main Camera**上处于选中状态，单击**添加组件**，然后搜索**SceneOrganiser**脚本和双击，以将其添加。</span><span class="sxs-lookup"><span data-stu-id="6d653-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="6d653-394">在**项目面板**，打开**置入 Prefabs 文件夹**，拖动**标签**到 prefab*标签*空引用目标中的输入区域中，**SceneOrganiser**刚添加到脚本*Main Camera*，如下图中所示：</span><span class="sxs-lookup"><span data-stu-id="6d653-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="6d653-395">在中**层次结构面板**，选择**GazeCursor**的子**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="6d653-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="6d653-396">在中**检查器面板**，使用**GazeCursor**上处于选中状态，单击**添加组件**，然后搜索**GazeCursor**脚本和双击，以将其添加。</span><span class="sxs-lookup"><span data-stu-id="6d653-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="6d653-397">同样，在**层次结构面板**，选择**SpatialMapping**的子**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="6d653-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="6d653-398">在中**检查器面板**，使用**SpatialMapping**上处于选中状态，单击**添加组件**，然后搜索**SpatialMapping**脚本然后双击，以将其添加。</span><span class="sxs-lookup"><span data-stu-id="6d653-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="6d653-399">其余的您的脚本具有不会添加组中的代码**SceneOrganiser**脚本，在运行时。</span><span class="sxs-lookup"><span data-stu-id="6d653-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="6d653-400">第 12 章 — 生成前</span><span class="sxs-lookup"><span data-stu-id="6d653-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="6d653-401">若要执行全面测试您的应用程序将需要旁加载它到 Microsoft HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="6d653-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="6d653-402">执行操作之前，请确保：</span><span class="sxs-lookup"><span data-stu-id="6d653-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="6d653-403">中所述的所有设置[第 3 章](#chapter-3---set-up-the-unity-project)正确设置。</span><span class="sxs-lookup"><span data-stu-id="6d653-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="6d653-404">该脚本**SceneOrganiser**附加到**Main Camera**对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="6d653-405">该脚本**GazeCursor**附加到**GazeCursor**对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="6d653-406">该脚本**SpatialMapping**附加到**SpatialMapping**对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="6d653-407">在中[第 5 章：](#chapter-5---create-the-customvisionanalyser-class)，步骤 6:</span><span class="sxs-lookup"><span data-stu-id="6d653-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="6d653-408">请确保插入你**服务预测密钥**成**predictionKey**变量。</span><span class="sxs-lookup"><span data-stu-id="6d653-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="6d653-409">已插入您**预测终结点**成**predictionEndpoint**类。</span><span class="sxs-lookup"><span data-stu-id="6d653-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="6d653-410">章 13-生成的 UWP 解决方案和旁加载应用程序</span><span class="sxs-lookup"><span data-stu-id="6d653-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="6d653-411">现在您就可以生成应用程序作为一个 UWP 解决方案，你将能够部署到 Microsoft HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6d653-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="6d653-412">若要开始生成过程：</span><span class="sxs-lookup"><span data-stu-id="6d653-412">To begin the build process:</span></span>

1.  <span data-ttu-id="6d653-413">转到**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="6d653-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="6d653-414">刻度线**Unity C\#项目**。</span><span class="sxs-lookup"><span data-stu-id="6d653-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="6d653-415">单击**添加打开场景**。</span><span class="sxs-lookup"><span data-stu-id="6d653-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="6d653-416">这将添加到生成的当前打开的场景。</span><span class="sxs-lookup"><span data-stu-id="6d653-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="6d653-417">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="6d653-417">Click **Build**.</span></span> <span data-ttu-id="6d653-418">将启动 unity*文件资源管理器*窗口中，需要创建，然后选择要生成该应用程序的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6d653-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="6d653-419">现在，创建该文件夹并将其命名**应用**。</span><span class="sxs-lookup"><span data-stu-id="6d653-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="6d653-420">然后使用**应用程序**文件夹选择，单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="6d653-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="6d653-421">Unity 将开始构建您的项目**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="6d653-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="6d653-422">一次 Unity 已完成的生成 （它可能需要一些时间），它将打开**文件资源管理器**窗口在生成的位置 （检查任务栏中，因为它可能不总是会显示您的窗口上方，但会通知你添加了一个新窗口）。</span><span class="sxs-lookup"><span data-stu-id="6d653-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="6d653-423">若要部署到 Microsoft HoloLens，都需要该设备的 IP 地址 （适用于远程部署），并且以确保其还具有**开发人员模式**设置。</span><span class="sxs-lookup"><span data-stu-id="6d653-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="6d653-424">要实现此目的，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="6d653-424">To do this:</span></span>

    1.  <span data-ttu-id="6d653-425">戴上您 HoloLens，同时打开**设置**。</span><span class="sxs-lookup"><span data-stu-id="6d653-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="6d653-426">转到**网络和 Internet** > **的 Wi-fi** > **高级选项**</span><span class="sxs-lookup"><span data-stu-id="6d653-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="6d653-427">请注意**IPv4**地址。</span><span class="sxs-lookup"><span data-stu-id="6d653-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="6d653-428">接下来，导航回到**设置**，然后**更新和安全** > **面向开发人员**</span><span class="sxs-lookup"><span data-stu-id="6d653-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="6d653-429">设置\**开发人员模式\*\*\*上*。</span><span class="sxs-lookup"><span data-stu-id="6d653-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="6d653-430">导航到新的 Unity 生成 (**应用程序**文件夹)，然后打开解决方案文件与**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="6d653-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="6d653-431">在解决方案配置中，选择**调试**。</span><span class="sxs-lookup"><span data-stu-id="6d653-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="6d653-432">在解决方案平台中，选择**x86，远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="6d653-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="6d653-433">系统会提示要插入**IP 地址**的远程设备 (Microsoft HoloLens，在这种情况下，记下)。</span><span class="sxs-lookup"><span data-stu-id="6d653-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="6d653-434">转到**构建**菜单，并单击**部署解决方案**旁加载到你 HoloLens 应用程序。</span><span class="sxs-lookup"><span data-stu-id="6d653-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="6d653-435">在准备好启动您 Microsoft HoloLens 上安装的应用列表中，现在应显示你的应用 ！</span><span class="sxs-lookup"><span data-stu-id="6d653-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="6d653-436">若要使用应用程序：</span><span class="sxs-lookup"><span data-stu-id="6d653-436">To use the application:</span></span>

* <span data-ttu-id="6d653-437">看一看一个对象，它使用训练你**Azure 自定义影像服务、 对象检测**，并使用**点击手势**。</span><span class="sxs-lookup"><span data-stu-id="6d653-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="6d653-438">如果该对象已成功检测到，世界空间*标签文本*将显示为带有标记名称。</span><span class="sxs-lookup"><span data-stu-id="6d653-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d653-439">每次捕获照片并将其发送到服务，可以返回到服务页并重新训练新捕获的映像的服务。</span><span class="sxs-lookup"><span data-stu-id="6d653-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="6d653-440">在开始时，您将可能还需要更正*边界框*更准确和重新训练服务。</span><span class="sxs-lookup"><span data-stu-id="6d653-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="6d653-441">放置标签文本可能不会显示附近对象 Microsoft HoloLens 传感器和/或在 Unity 中的 SpatialTrackingComponent 失败将相应的碰撞体，相对于现实世界对象时。</span><span class="sxs-lookup"><span data-stu-id="6d653-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="6d653-442">请尝试使用不同的图面上的应用程序，如果是这种情况。</span><span class="sxs-lookup"><span data-stu-id="6d653-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="6d653-443">你的自定义愿景，对象检测应用程序</span><span class="sxs-lookup"><span data-stu-id="6d653-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="6d653-444">祝贺你，构建利用 Azure 自定义视觉对象检测 API，它可以识别图像中的对象，然后提供在 3D 空间中的近似位置以该对象的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="6d653-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="6d653-445">Bonus 练习</span><span class="sxs-lookup"><span data-stu-id="6d653-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="6d653-446">练习 1</span><span class="sxs-lookup"><span data-stu-id="6d653-446">Exercise 1</span></span>

<span data-ttu-id="6d653-447">将添加到文本标签，使用半透明的多维数据集以将实际对象封装在一个三维*边界框*。</span><span class="sxs-lookup"><span data-stu-id="6d653-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="6d653-448">练习 2</span><span class="sxs-lookup"><span data-stu-id="6d653-448">Exercise 2</span></span>

<span data-ttu-id="6d653-449">训练你自定义影像服务能够识别更多的对象。</span><span class="sxs-lookup"><span data-stu-id="6d653-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="6d653-450">练习 3</span><span class="sxs-lookup"><span data-stu-id="6d653-450">Exercise 3</span></span>

<span data-ttu-id="6d653-451">识别对象时播放声音。</span><span class="sxs-lookup"><span data-stu-id="6d653-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="6d653-452">练习 4</span><span class="sxs-lookup"><span data-stu-id="6d653-452">Exercise 4</span></span>

<span data-ttu-id="6d653-453">若要重新训练你的服务使用相同的图像分析您的应用程序，因此若要使服务更准确地使用 API （执行预测和同时培训）。</span><span class="sxs-lookup"><span data-stu-id="6d653-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
