---
title: Azure 云教程 - 1. 适用于 HoloLens 2 的 Azure 云服务
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现各种 Azure 服务。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: azure, 混合现实, unity, 教程, hololens, hololens 2, azure blob 存储, azure 表存储, azure 空间定位点, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304179"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="9bd97-105">1.适用于 HoloLens 2 的 Azure 云服务</span><span class="sxs-lookup"><span data-stu-id="9bd97-105">1. Azure Cloud Services for HoloLens 2</span></span>

## <a name="overview"></a><span data-ttu-id="9bd97-106">概述</span><span class="sxs-lookup"><span data-stu-id="9bd97-106">Overview</span></span>

<span data-ttu-id="9bd97-107">欢迎使用这一系列教程，这些教程重点介绍如何将 Azure 云服务引入 HoloLens 2 应用程序 。</span><span class="sxs-lookup"><span data-stu-id="9bd97-107">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="9bd97-108">本系列教程包含五个部分，介绍了如何将多个 Azure 云服务集成到 HoloLens 2 的 Unity 项目中  。</span><span class="sxs-lookup"><span data-stu-id="9bd97-108">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="9bd97-109">在每个连续的章节中，都将添加新的 Azure 云服务，以扩展应用程序功能和用户体验，同时还将介绍每种 Azure 云服务的基础知识 。</span><span class="sxs-lookup"><span data-stu-id="9bd97-109">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="9bd97-110">本系列教程将重点介绍 HoloLens 2，但由于 Unity 具有跨平台的特性，因此大多数知识也适用于桌面和智能手机应用程序。</span><span class="sxs-lookup"><span data-stu-id="9bd97-110">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="9bd97-111">在第一个教程[适用于 HoloLens 2 的 Azure 云服务简介](mr-learning-azure-01.md)中，首先将解释应用程序的目标，简要介绍每个 Azure 云服务并设置 unity 项目。</span><span class="sxs-lookup"><span data-stu-id="9bd97-111">In this first tutorial, [Introducing Azure Cloud Services for HoloLens 2](mr-learning-azure-01.md), you begin by explaining the goals of the application, briefly introduce you to each Azure Cloud service and set up the unity project.</span></span>

<span data-ttu-id="9bd97-112">在第二个教程[集成 Azure 存储](mr-learning-azure-02.md)中，首先将 Azure 存储集成为演示应用程序的持久性解决方案，了解 Blob 存储和表存储之间的区别、准备必要的项目资源、设置场景并验证读取、更新和删除数据操作。</span><span class="sxs-lookup"><span data-stu-id="9bd97-112">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you start off by integrating Azure Storage as the persistence solution for the demo application, learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene and verify the read, update and delete data operations.</span></span>

<span data-ttu-id="9bd97-113">继续学习第三个教程[集成 Azure 自定义视觉](mr-learning-azure-03.md)，你将使用 Azure 自定义视觉在 HoloLens 2 应用程序中训练和检测图像。</span><span class="sxs-lookup"><span data-stu-id="9bd97-113">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="9bd97-114">本章首先设置你自己的 Azure 自定义视觉资源，准备场景组成部分，并通过在应用程序内部训练和检测自己的图像来使之付诸实践。</span><span class="sxs-lookup"><span data-stu-id="9bd97-114">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="9bd97-115">接下来，你将继续学习第四个教程[集成 Azure 空间定位点](mr-learning-azure-04.md)，并了解 Azure 空间定位点服务以保存和查找位置，了解核心概念，准备必要的资源，设置场景并开始在应用程序中使用新功能。</span><span class="sxs-lookup"><span data-stu-id="9bd97-115">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="9bd97-116">借助第五个教程[将 Azure 机器人服务与 LUIS 集成](mr-learning-azure-05.md)，你可以通过为应用程序提供一种新的用户交互方法（即自然语言）来完成操作。</span><span class="sxs-lookup"><span data-stu-id="9bd97-116">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="9bd97-117">此功能将通过结合使用 Azure Bot Framework 和语言理解智能服务 (LUIS) 来实现。</span><span class="sxs-lookup"><span data-stu-id="9bd97-117">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="9bd97-118">最后一章介绍 Azure 机器人服务的基础知识，为加快进程，可使用 Bot Framework Composer 作为零代码解决方案。</span><span class="sxs-lookup"><span data-stu-id="9bd97-118">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="9bd97-119">创建了机器人后，你就可以将其集成到场景中，并在 HoloLens 2 应用程序的最后阶段运行。</span><span class="sxs-lookup"><span data-stu-id="9bd97-119">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="9bd97-120">应用程序目标</span><span class="sxs-lookup"><span data-stu-id="9bd97-120">Application goals</span></span>

<span data-ttu-id="9bd97-121">在本系列教程中，你将构建一个 HoloLens 2 应用程序，该应用程序可检测图像中的对象并找到其空间位置。</span><span class="sxs-lookup"><span data-stu-id="9bd97-121">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="9bd97-122">要设置域语言，请从现在被跟踪对象调用此类实体。</span><span class="sxs-lookup"><span data-stu-id="9bd97-122">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="9bd97-123">用户可以创建被跟踪对象，以通过计算机视觉和/或空间位置来关联一组图像。</span><span class="sxs-lookup"><span data-stu-id="9bd97-123">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="9bd97-124">所有数据都必须保存到云中。</span><span class="sxs-lookup"><span data-stu-id="9bd97-124">All data must be persisted into the cloud.</span></span> <span data-ttu-id="9bd97-125">此外，应用程序的某些方面也可以通过机器人的自然语言来控制。</span><span class="sxs-lookup"><span data-stu-id="9bd97-125">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="9bd97-126">功能</span><span class="sxs-lookup"><span data-stu-id="9bd97-126">Features</span></span>

* <span data-ttu-id="9bd97-127">数据和图像的基本管理</span><span class="sxs-lookup"><span data-stu-id="9bd97-127">Basic managing of data and images</span></span>
* <span data-ttu-id="9bd97-128">图像训练和检测</span><span class="sxs-lookup"><span data-stu-id="9bd97-128">Image training and detection</span></span>
* <span data-ttu-id="9bd97-129">存储空间位置及其指南</span><span class="sxs-lookup"><span data-stu-id="9bd97-129">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="9bd97-130">机器人助手通过自然语言使用某些功能</span><span class="sxs-lookup"><span data-stu-id="9bd97-130">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="9bd97-131">Azure 云服务</span><span class="sxs-lookup"><span data-stu-id="9bd97-131">Azure Cloud services</span></span>

<span data-ttu-id="9bd97-132">若要解决应用程序所需的功能，需要使用以下 Azure 云服务：</span><span class="sxs-lookup"><span data-stu-id="9bd97-132">To solve the required features for the application, you will use these **Azure Cloud** services:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="9bd97-133">Azure 存储</span><span class="sxs-lookup"><span data-stu-id="9bd97-133">Azure Storage</span></span>

<span data-ttu-id="9bd97-134">使用 [Azure 存储](https://azure.microsoft.com/services/storage/)作为持久性解决方案。</span><span class="sxs-lookup"><span data-stu-id="9bd97-134">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="9bd97-135">使用该解决方案，你可以将数据存储在表上并上传大型二进制文件（例如图像）。</span><span class="sxs-lookup"><span data-stu-id="9bd97-135">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="9bd97-136">Azure 自定义视觉</span><span class="sxs-lookup"><span data-stu-id="9bd97-136">Azure Custom Vision</span></span>

<span data-ttu-id="9bd97-137">借助 [Azure 自定义视觉](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)（[Azure 认知服务](https://azure.microsoft.com/services/cognitive-services/)的一部分），你可以将被跟踪对象关联到一组图像、训练集上的机器学习模型并检测被跟踪对象 。</span><span class="sxs-lookup"><span data-stu-id="9bd97-137">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="9bd97-138">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="9bd97-138">Azure Spatial Anchors</span></span>

<span data-ttu-id="9bd97-139">若要存储被跟踪对象的位置，并提供指导说明以找到该位置，请使用 [Azure 空间定位点](https://azure.microsoft.com/services/spatial-anchors/)。</span><span class="sxs-lookup"><span data-stu-id="9bd97-139">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="9bd97-140">Azure 机器人服务</span><span class="sxs-lookup"><span data-stu-id="9bd97-140">Azure Bot Service</span></span>

<span data-ttu-id="9bd97-141">该应用程序主要由传统 UI 提供支持，因此你可以使用 [Azure 机器人服务](https://azure.microsoft.com/services/bot-service/)添加一些个性并充当新的交互方法。</span><span class="sxs-lookup"><span data-stu-id="9bd97-141">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9bd97-142">必备条件</span><span class="sxs-lookup"><span data-stu-id="9bd97-142">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="9bd97-143">如果你尚未完成[入门教程](mr-learning-base-01.md)系列，建议先完成这些教程。</span><span class="sxs-lookup"><span data-stu-id="9bd97-143">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="9bd97-144">一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="9bd97-144">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="9bd97-145">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="9bd97-145">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9bd97-146">一些基本的 C# 编程功能</span><span class="sxs-lookup"><span data-stu-id="9bd97-146">Some basic C# programming ability</span></span>
* <span data-ttu-id="9bd97-147">一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="9bd97-147">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="9bd97-148">一个联网的摄像头（如果要通过 Unity 编辑器进行测试）</span><span class="sxs-lookup"><span data-stu-id="9bd97-148">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="9bd97-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.X 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="9bd97-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="9bd97-150">建议对本系列教程使用 Unity 2019.3.X。</span><span class="sxs-lookup"><span data-stu-id="9bd97-150">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="9bd97-151">这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="9bd97-151">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="9bd97-152">创建和准备 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="9bd97-152">Creating and preparing the Unity project</span></span>

<span data-ttu-id="9bd97-153">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="9bd97-153">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="9bd97-154">为此，请先执行[初始化项目和第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：</span><span class="sxs-lookup"><span data-stu-id="9bd97-154">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="9bd97-155">[创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如 Azure 云教程</span><span class="sxs-lookup"><span data-stu-id="9bd97-155">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="9bd97-156">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="9bd97-156">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="9bd97-157">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="9bd97-157">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="9bd97-158">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="9bd97-158">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="9bd97-159">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="9bd97-159">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="9bd97-160">[创建并设置场景](mr-learning-base-02.md#creating-and-configuring-the-scene)，并为场景提供一个合适的名称，例如 AzureCloudServices</span><span class="sxs-lookup"><span data-stu-id="9bd97-160">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="9bd97-161">然后，根据[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)说明将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡” 。</span><span class="sxs-lookup"><span data-stu-id="9bd97-161">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="9bd97-162">安装内置 Unity 包</span><span class="sxs-lookup"><span data-stu-id="9bd97-162">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="9bd97-163">在 Unity 菜单中，选择“窗口” > “包管理器”打开“包管理器”窗口，然后选择“AR Foundation”并单击“安装”按钮以安装包   ：</span><span class="sxs-lookup"><span data-stu-id="9bd97-163">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9bd97-165">你要安装 AR Foundation 包，因为在下一部分中导入 Azure 空间定位点 SDK 时必须使用它。</span><span class="sxs-lookup"><span data-stu-id="9bd97-165">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9bd97-166">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="9bd97-166">Importing the tutorial assets</span></span>

<span data-ttu-id="9bd97-167">下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：</span><span class="sxs-lookup"><span data-stu-id="9bd97-167">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="9bd97-168">用于 Unity 的 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="9bd97-168">Azure storage for Unity</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="9bd97-169">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="9bd97-169">Azure Spatial Anchors</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [<span data-ttu-id="9bd97-170">MRTK.Tutorials.AzureCloudServices</span><span class="sxs-lookup"><span data-stu-id="9bd97-170">MRTK.Tutorials.AzureCloudServices</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="9bd97-171">有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)中的说明。</span><span class="sxs-lookup"><span data-stu-id="9bd97-171">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="9bd97-172">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="9bd97-172">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="9bd97-174">创建和准备场景</span><span class="sxs-lookup"><span data-stu-id="9bd97-174">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="9bd97-175">在本部分，你将通过添加一些教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="9bd97-175">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="9bd97-176">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureCloudServices” > “预制件” > “管理器”文件夹   。</span><span class="sxs-lookup"><span data-stu-id="9bd97-176">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="9bd97-177">按住 Ctrl 按钮并单击“SceneController”、“RootMenu”和“DataManager”以选择这三个预制件  ：</span><span class="sxs-lookup"><span data-stu-id="9bd97-177">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="9bd97-179">SceneController (预制件)包含两个脚本：SceneController (脚本)和 UnityDispatcher (脚本)  。</span><span class="sxs-lookup"><span data-stu-id="9bd97-179">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="9bd97-180">“SceneController”脚本组件包含多个 UX 函数，并简化了照片捕获功能，而 UnityDispatcher 是一个帮助程序类，允许在 Unity 主线程上执行操作 。</span><span class="sxs-lookup"><span data-stu-id="9bd97-180">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="9bd97-181">“RootMenu (预制件)”是主要的 UI 预制件，它包含通过各种小型脚本组件相互连接的所有 UI 窗口，并控制应用程序的一般 UX 流程。</span><span class="sxs-lookup"><span data-stu-id="9bd97-181">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="9bd97-182">“DataManager (预制件)”负责与 Azure 存储通信，下一教程将进一步介绍此内容。</span><span class="sxs-lookup"><span data-stu-id="9bd97-182">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="9bd97-183">现在，在仍选中了这三个预制件的情况下，将其拖动到“层次结构”窗口中，以将其添加到场景：</span><span class="sxs-lookup"><span data-stu-id="9bd97-183">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="9bd97-185">若要将焦点置于场景中的对象上，可以双击“RootMenu”对象，然后再次稍微缩小：</span><span class="sxs-lookup"><span data-stu-id="9bd97-185">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="9bd97-187">如果在场景中看到很大的图标（例如，框住的“T”图标会分散注意力），可以通过<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">将调节器 (Gizmos) 切换</a>到关闭位置来隐藏这些图标。</span><span class="sxs-lookup"><span data-stu-id="9bd97-187">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="9bd97-188">配置场景</span><span class="sxs-lookup"><span data-stu-id="9bd97-188">Configuring the scene</span></span>

<span data-ttu-id="9bd97-189">在本节中，需要将 SceneManager、DataManager 和 RootMenu 连接在一起，为下面的[集成 Azure 存储](mr-learning-azure-01.md)准备好工作场景  。</span><span class="sxs-lookup"><span data-stu-id="9bd97-189">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="9bd97-190">连接对象</span><span class="sxs-lookup"><span data-stu-id="9bd97-190">Connect the objects</span></span>

<span data-ttu-id="9bd97-191">在“层次结构”窗口中，选择“DataManager”对象：</span><span class="sxs-lookup"><span data-stu-id="9bd97-191">In the Hierarchy window, select the **DataManager** object:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="9bd97-193">在“检查器”窗口中，找到“DataManager (脚本)”组件，你将在“On Data Manager Ready ()”事件上看到一个空槽 。</span><span class="sxs-lookup"><span data-stu-id="9bd97-193">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="9bd97-194">现在，从“层次结构”窗口将“SceneController”对象拖到“On Data Manager Ready ()”事件 。</span><span class="sxs-lookup"><span data-stu-id="9bd97-194">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="9bd97-196">你将注意到该事件的下拉菜单变为活动状态，单击下拉菜单并导航到 SceneController，然后在子菜单中选择“Init ()”选项 ：</span><span class="sxs-lookup"><span data-stu-id="9bd97-196">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="9bd97-198">从“层次结构”窗口选择“SceneController”对象，你将在检查器中找到“SceneController (脚本)”组件 。</span><span class="sxs-lookup"><span data-stu-id="9bd97-198">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="9bd97-200">你将看到有几个未填充的字段，让我们对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="9bd97-200">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="9bd97-201">将 DataManager 对象从层次结构移到“数据管理器”字段，并将 RootMenu GameObject 从层次结构移动到“主菜单”字段。</span><span class="sxs-lookup"><span data-stu-id="9bd97-201">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="9bd97-203">现在，你的场景已经准备就绪，可用于下一个教程。</span><span class="sxs-lookup"><span data-stu-id="9bd97-203">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="9bd97-204">不要忘记将其保存到你的项目中。</span><span class="sxs-lookup"><span data-stu-id="9bd97-204">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="9bd97-205">准备项目生成管道</span><span class="sxs-lookup"><span data-stu-id="9bd97-205">Prepare project build pipeline</span></span>

<span data-ttu-id="9bd97-206">尽管项目尚未填充内容，但你必须执行一些准备工作，以便项目准备好构建 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="9bd97-206">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="9bd97-207">1.添加其他所需功能</span><span class="sxs-lookup"><span data-stu-id="9bd97-207">1. Add additional required capabilities</span></span>

<span data-ttu-id="9bd97-208">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="9bd97-208">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="9bd97-210">在“项目设置”窗口中，依次选择“播放器”、“发布设置” ：</span><span class="sxs-lookup"><span data-stu-id="9bd97-210">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="9bd97-212">在“发布设置”中，向下滚动到“功能”部分，仔细检查在教程中最初创建项目时启用的“InternetClient”、“Microphone”和“SpatialPerception”功能是否确实已启用。    </span><span class="sxs-lookup"><span data-stu-id="9bd97-212">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="9bd97-213">然后启用“InternetClientServer”、“PrivateNetworkClientServer”和“Webcam”功能  ：</span><span class="sxs-lookup"><span data-stu-id="9bd97-213">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="9bd97-215">2.将应用部署到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9bd97-215">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="9bd97-216">并非你将在本系列教程中使用的所有功能都可以在 Unity 编辑器中运行，这意味着你需要熟悉如何将应用程序部署到 HoloLens 2 设备上。</span><span class="sxs-lookup"><span data-stu-id="9bd97-216">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="9bd97-217">有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[入门教程 - 在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="9bd97-217">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="9bd97-218">3.在 HoloLens 2 上运行该应用，并按照应用中的说明进行操作</span><span class="sxs-lookup"><span data-stu-id="9bd97-218">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="9bd97-219">所有 Azure 服务都使用 Internet，因此请确保你的设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="9bd97-219">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="9bd97-220">当应用程序在设备上运行时，请接受对以下请求功能的访问权限：</span><span class="sxs-lookup"><span data-stu-id="9bd97-220">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="9bd97-221">麦克风</span><span class="sxs-lookup"><span data-stu-id="9bd97-221">Microphone</span></span>
* <span data-ttu-id="9bd97-222">照相机</span><span class="sxs-lookup"><span data-stu-id="9bd97-222">Camera</span></span>

<span data-ttu-id="9bd97-223">聊天机器人和自定义视觉等服务需要上述功能才能正常运行 。</span><span class="sxs-lookup"><span data-stu-id="9bd97-223">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9bd97-224">祝贺</span><span class="sxs-lookup"><span data-stu-id="9bd97-224">Congratulations</span></span>

<span data-ttu-id="9bd97-225">本教程介绍了一系列教程，其中介绍了将实现的功能以及如何将 Azure 云服务与 HoloLens 2 应用程序关联。</span><span class="sxs-lookup"><span data-stu-id="9bd97-225">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="9bd97-226">你已将所需的组件添加到项目中，并为系列本教程准备了场景。</span><span class="sxs-lookup"><span data-stu-id="9bd97-226">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="9bd97-227">下一课将使用 Azure 存储作为基于云的持久性解决方案来存储数据和图像。</span><span class="sxs-lookup"><span data-stu-id="9bd97-227">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

[<span data-ttu-id="9bd97-228">下一教程：2.集成 Azure 存储</span><span class="sxs-lookup"><span data-stu-id="9bd97-228">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)
