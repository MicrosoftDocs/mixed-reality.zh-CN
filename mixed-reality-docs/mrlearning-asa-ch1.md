---
title: Azure 空间定位点教程 - 1. Azure 空间定位点入门
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 385b302f3a2b9ad80527387353746947d91e3aa3
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216298"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="6fe7f-105">1.Azure 空间定位点入门</span><span class="sxs-lookup"><span data-stu-id="6fe7f-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="6fe7f-106">概述</span><span class="sxs-lookup"><span data-stu-id="6fe7f-106">Overview</span></span>

<span data-ttu-id="6fe7f-107">欢迎学习 HoloLens 2 教程的第二个系列。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="6fe7f-108">本教学系列由四篇教程构成，本教程介绍 Azure 空间定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-108">In this four-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="6fe7f-109">本第一篇教程 [Azure 空间定位点入门](mrlearning-asa-ch1.md)介绍启动和停止 Azure 会话，以及在单个设备上创建、上传和下载 Azure 定位点所要的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="6fe7f-110">第二篇教程[保存、检索和共享 Azure 空间定位点](mrlearning-asa-ch2.md)将介绍如何通过将定位点信息保存到 HoloLens 2 存储来保存多个应用会话中的 Azure 空间定位点，以及如何与其他设备共享此定位点信息，以对齐多个设备的定位点。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="6fe7f-111">第三篇教程[显示 Azure 空间定位点反馈](mrlearning-asa-ch3.md)将介绍如何在使用 Azure 空间定位点时，向用户提供有关定位点事件和状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="6fe7f-112">在第四篇教程[适用于 Android 和 iOS 的 Azure 空间定位点](mrlearning-asa-ch4.md)介绍了如何生成项目并将其部署到 Android 和 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-112">In the fourth tutorial, [Azure Spatial Anchors for Android and iOS](mrlearning-asa-ch4.md), you will learn how to build and deploy your project to Android and iOS devices.</span></span>

## <a name="objectives"></a><span data-ttu-id="6fe7f-113">目标</span><span class="sxs-lookup"><span data-stu-id="6fe7f-113">Objectives</span></span>

* <span data-ttu-id="6fe7f-114">了解有关使用适用于 HoloLens 2 的 Azure 空间定位点进行开发的基础知识</span><span class="sxs-lookup"><span data-stu-id="6fe7f-114">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="6fe7f-115">创建、上传和下载空间定位点</span><span class="sxs-lookup"><span data-stu-id="6fe7f-115">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6fe7f-116">必备条件</span><span class="sxs-lookup"><span data-stu-id="6fe7f-116">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="6fe7f-117">如果你尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-117">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="6fe7f-118">一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="6fe7f-118">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="6fe7f-119">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="6fe7f-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="6fe7f-120">一些基本的 C# 编程功能</span><span class="sxs-lookup"><span data-stu-id="6fe7f-120">Some basic C# programming ability</span></span>
* <span data-ttu-id="6fe7f-121">[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens（第 1 代）或 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="6fe7f-121">A HoloLens (1st Gen) or HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="6fe7f-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="6fe7f-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="6fe7f-123">完成 [HoloLens 快速入门](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程的[创建空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-123">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [HoloLens quickstart](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

<span data-ttu-id="6fe7f-124">如果打算部署到 Android</span><span class="sxs-lookup"><span data-stu-id="6fe7f-124">If you intend to deploy to Android</span></span>
* <span data-ttu-id="6fe7f-125"><a href="https://developer.android.com/studio/debug/dev-options" target="_blank">开发人员实现</a>且<a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">支持 ARCore</a>的 Android 设备，该设备通过 USB 与 Windows 或 macOS 计算机相连接</span><span class="sxs-lookup"><span data-stu-id="6fe7f-125">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
* <span data-ttu-id="6fe7f-126"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并已添加 Android 生成支持模块</span><span class="sxs-lookup"><span data-stu-id="6fe7f-126"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Android Build Support module added</span></span>

<span data-ttu-id="6fe7f-127">如果打算部署到 iOS</span><span class="sxs-lookup"><span data-stu-id="6fe7f-127">If you intend to deploy to iOS</span></span>
* <span data-ttu-id="6fe7f-128">已安装最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 计算机</span><span class="sxs-lookup"><span data-stu-id="6fe7f-128">A macOS computer with the the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
* <span data-ttu-id="6fe7f-129"><a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">与 ARKit 兼容</a>且通过 USB 连接到 macOS 计算机的 iOS 设备</span><span class="sxs-lookup"><span data-stu-id="6fe7f-129">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
* <span data-ttu-id="6fe7f-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并已添加 iOS 生成支持模块</span><span class="sxs-lookup"><span data-stu-id="6fe7f-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the iOS Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6fe7f-131">建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-131">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="6fe7f-132">这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-132">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="6fe7f-133">创建 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="6fe7f-133">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

<span data-ttu-id="6fe7f-134">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-134">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="6fe7f-135">为此，请先执行[初始化项目和第一个应用程序](mrlearning-base-ch1.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)的说明：</span><span class="sxs-lookup"><span data-stu-id="6fe7f-135">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="6fe7f-136">[创建新的 Unity 项目](mrlearning-base-ch1.md#create-new-unity-project)并为其指定适当的名称，例如 *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="6fe7f-136">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="6fe7f-137">配置用于 Windows Mixed Reality 的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="6fe7f-137">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="6fe7f-138">导入 TextMesh Pro 基本资源</span><span class="sxs-lookup"><span data-stu-id="6fe7f-138">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="6fe7f-139">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="6fe7f-139">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="6fe7f-140">配置用于混合现实工具包的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="6fe7f-140">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="6fe7f-141">[将混合现实工具包添加到 Unity 场景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)，并为该场景指定适当的名称，例如 *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="6fe7f-141">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="6fe7f-142">然后，根据[如何配置混合现实工具包配置文件（更改空间感知显示选项）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡”。 </span><span class="sxs-lookup"><span data-stu-id="6fe7f-142">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="6fe7f-143">根据上面链接的[配置用于混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)说明中所述，强烈建议不要为 Unity 启用 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-143">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="6fe7f-144">添加内置 Unity 包</span><span class="sxs-lookup"><span data-stu-id="6fe7f-144">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="6fe7f-145">在本部分，你将安装 Unity 的内置 AR Foundation 包，因为在下一部分要导入的 Azure 空间定位点 SDK 需要此包。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-145">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="6fe7f-146">在 Unity 菜单中，选择“窗口” > “包管理器”： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-146">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="6fe7f-148">AR Foundation 包可能需要在几秒钟后才显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-148">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="6fe7f-149">在“包管理器”窗口中选择“AR Foundation”，然后单击“安装”按钮安装该包： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-149">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="6fe7f-151">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="6fe7f-151">Importing the tutorial assets</span></span>

<span data-ttu-id="6fe7f-152">下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：</span><span class="sxs-lookup"><span data-stu-id="6fe7f-152">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="6fe7f-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)（版本 2.1.1）</span><span class="sxs-lookup"><span data-stu-id="6fe7f-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="6fe7f-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="6fe7f-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="6fe7f-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="6fe7f-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> <span data-ttu-id="6fe7f-156">有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)中的说明。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-156">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="6fe7f-157">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="6fe7f-157">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="6fe7f-159">创建和准备场景</span><span class="sxs-lookup"><span data-stu-id="6fe7f-159">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="6fe7f-160">在本部分，你将通过添加一些教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-160">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="6fe7f-161">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹。  </span><span class="sxs-lookup"><span data-stu-id="6fe7f-161">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="6fe7f-162">在按住 CTRL 键的同时单击“ButtonParent”、“DebugWindow”、“Instructions”和“ParentAnchor”，以选择这四个预制件：   </span><span class="sxs-lookup"><span data-stu-id="6fe7f-162">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="6fe7f-164">在仍选中了这四个预制件的情况下，将其拖放到“层次结构”窗口中，以将其添加到场景：</span><span class="sxs-lookup"><span data-stu-id="6fe7f-164">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="6fe7f-166">若要将焦点置于场景中的对象上，可以双击“ParentAnchor”对象，然后再次稍微缩小：</span><span class="sxs-lookup"><span data-stu-id="6fe7f-166">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="6fe7f-168">如果在场景中看到很大的图标（例如，框住的“T”图标会分散注意力），可以通过<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">将调节器 (Gizmos) 切换</a>到关闭位置来隐藏这些图标。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-168">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="6fe7f-169">配置按钮以操作场景</span><span class="sxs-lookup"><span data-stu-id="6fe7f-169">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="6fe7f-170">在本部分，你要将脚本添加到场景，以创建一系列按钮事件，用于演示本地定位点和 Azure 空间定位点在应用程序中的行为方式的基本原理。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-170">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="6fe7f-171">1.配置“可按按钮 Holo Lens 2 (脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="6fe7f-171">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="6fe7f-172">在“层次结构”窗口中展开“ButtonParent”对象，然后选择名为“StartAzureSession”的第一个子对象： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-172">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="6fe7f-174">在“检查器”窗口中找到“可按按钮 Holo Lens 2 (脚本)”组件，然后单击 **+** 图标将新的事件侦听器添加到“Button Pressed ()”事件： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-174">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="6fe7f-176">仍在“层次结构”窗口中选中了“StartAzureSession”对象的情况下，单击“层次结构”窗口中的“ParentAnchor”对象并将其拖放到刚刚添加的事件侦听器的空“无(对象)”字段中，使 ParentAnchor 对象侦听此按钮的 button pressed 事件： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-176">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="6fe7f-178">单击同一事件侦听器的“无函数”下拉列表，然后选择“AnchorModuleScript” > “StartAzureSession ()”，将 StartAzureSession () 函数设置为在从此按钮激发 button pressed 事件时要触发的操作：  </span><span class="sxs-lookup"><span data-stu-id="6fe7f-178">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="6fe7f-180">2.配置“可交互(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="6fe7f-180">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="6fe7f-181">仍在“层次结构”窗口中选中了“StartAzureSession”对象的情况下，在“检查器”窗口中找到“可交互(脚本)”组件，然后针对“OnClick ()”事件重复上述步骤 1 中所述的相同过程： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-181">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="6fe7f-183">3.配置剩余的按钮</span><span class="sxs-lookup"><span data-stu-id="6fe7f-183">3. Configure the remaining buttons</span></span>

<span data-ttu-id="6fe7f-184">对于剩余的每个按钮，请完成上述步骤 1 和 2 中所述的过程，将函数分配到“Button Pressed ()”和“OnClick ()”事件： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-184">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="6fe7f-185">对于“StopAzureSession”对象，请分配“AnchorModuleScript”>“StopAzureSession ()”函数。 </span><span class="sxs-lookup"><span data-stu-id="6fe7f-185">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="6fe7f-186">对于“CreateAzureAnchor”对象，请分配“AnchorModuleScript”>“CreateAzureAnchor ()”函数。 </span><span class="sxs-lookup"><span data-stu-id="6fe7f-186">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="6fe7f-187">然后，再次将“ParentAnchor”拖放到空的“无(游戏对象)”字段中。 </span><span class="sxs-lookup"><span data-stu-id="6fe7f-187">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="6fe7f-188">对于“RemoveLocalAnchor”对象，请分配“AnchorModuleScript”>“RemoveLocalAnchor ()”函数。 </span><span class="sxs-lookup"><span data-stu-id="6fe7f-188">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="6fe7f-189">然后，再次将“ParentAnchor”拖放到空的“无(游戏对象)”字段中。 </span><span class="sxs-lookup"><span data-stu-id="6fe7f-189">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="6fe7f-190">对于“FindAzureAnchor”对象，请分配“AnchorModuleScript”>“FindAzureAnchor ()”函数。 </span><span class="sxs-lookup"><span data-stu-id="6fe7f-190">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="6fe7f-191">对于“DeleteAzureAnchor”对象，请分配“AnchorModuleScript”>“DeleteAzureAnchor ()”函数。 </span><span class="sxs-lookup"><span data-stu-id="6fe7f-191">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="6fe7f-192">4.将场景连接到 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="6fe7f-192">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="6fe7f-193">在“层次结构”窗口中选择“ParentAnchor”对象，然后在“检查器”窗口中，向下滚动到“空间定位点管理器(脚本)”组件。 </span><span class="sxs-lookup"><span data-stu-id="6fe7f-193">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="6fe7f-194">然后在“凭据”部分，将在本教程的[先决条件](mrlearning-asa-ch1.md#prerequisites)部分创建的空间定位点帐户 ID 和密钥粘贴到相应的“空间定位点帐户 ID”和“空间定位点帐户密钥”字段中：  </span><span class="sxs-lookup"><span data-stu-id="6fe7f-194">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="6fe7f-196">尝试 Azure 空间定位点的基本行为</span><span class="sxs-lookup"><span data-stu-id="6fe7f-196">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="6fe7f-197">配置用于演示 Azure 空间定位点基本原理的场景后，接下来可以部署应用，以直接体验 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-197">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="6fe7f-198">1.添加其他所需功能</span><span class="sxs-lookup"><span data-stu-id="6fe7f-198">1. Add additional required capabilities</span></span>

<span data-ttu-id="6fe7f-199">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“播放器设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-199">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="6fe7f-201">在“播放器设置”窗口中，依次选择“播放器”、“发布设置”： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-201">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="6fe7f-203">在“发布设置”中，向下滚动到“功能”部分，仔细检查在教程中最初创建项目时启用的“InternetClient”、“Microphone”和“SpatialPerception”功能是否确实已启用。    </span><span class="sxs-lookup"><span data-stu-id="6fe7f-203">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="6fe7f-204">然后，启用“InternetClientServer”、“PrivateNetworkClientServer”、“RemovableStorage”和“Webcam”功能：   </span><span class="sxs-lookup"><span data-stu-id="6fe7f-204">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="6fe7f-206">2.将应用部署到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6fe7f-206">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="6fe7f-207">Azure 空间定位点不能在 Unity 中运行，因此，若要测试 Azure 空间定位点功能，需将项目部署到设备。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-207">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="6fe7f-208">有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)中的说明。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-208">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="6fe7f-209">3.在 HoloLens 2 上运行该应用，并按照应用中的说明进行操作</span><span class="sxs-lookup"><span data-stu-id="6fe7f-209">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="6fe7f-210">Azure 空间定位点将使用 Internet 来保存和加载定位点数据，因此请确保设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-210">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="6fe7f-211">当应用程序在设备上运行时，请按照“Azure 空间定位点教程说明”面板上显示的屏幕说明进行操作：</span><span class="sxs-lookup"><span data-stu-id="6fe7f-211">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="6fe7f-213">定位体验</span><span class="sxs-lookup"><span data-stu-id="6fe7f-213">Anchoring an experience</span></span>

<span data-ttu-id="6fe7f-214">前面的部分已介绍 Azure 空间定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-214">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="6fe7f-215">我们已使用一个立方体来表示并可视化了附有定位点的父游戏对象。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-215">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="6fe7f-216">本部分将介绍如何通过将整个体验定位为 ParentAnchor 对象的子级，来定位该体验。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-216">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="6fe7f-217">1.添加火箭发射器体验</span><span class="sxs-lookup"><span data-stu-id="6fe7f-217">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="6fe7f-218">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件” > “RocketLauncher”文件夹，选择“RocketLauncher_Complete”预制件：    </span><span class="sxs-lookup"><span data-stu-id="6fe7f-218">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="6fe7f-220">在仍选中了 RocketLauncher_Complete 预制件的情况下，将其拖放到“层次结构”窗口中“ParentAnchor”对象的顶部，使其成为 ParentAnchor 对象的子级：</span><span class="sxs-lookup"><span data-stu-id="6fe7f-220">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="6fe7f-222">2.重新定位火箭发射器体验</span><span class="sxs-lookup"><span data-stu-id="6fe7f-222">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="6fe7f-223">根据适当的标度和方向定位、旋转和缩放“RocketLauncher_Complete”对象，同时确保“ParentAnchor”对象仍处于显示状态，例如： </span><span class="sxs-lookup"><span data-stu-id="6fe7f-223">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="6fe7f-224">变换**位置** X = 0，Y = 0，Z = 3.75</span><span class="sxs-lookup"><span data-stu-id="6fe7f-224">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="6fe7f-225">变换**位置** X = 0，Y = 90，Z = 0</span><span class="sxs-lookup"><span data-stu-id="6fe7f-225">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="6fe7f-226">变换**标度** X = 10，Y = 10，Z = 10</span><span class="sxs-lookup"><span data-stu-id="6fe7f-226">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="6fe7f-228">在应用程序中，用户现在可以通过移动立方体来重新定位整个火箭发射器体验。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-228">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="6fe7f-229">有多种用户体验流可用于重新定位体验，包括使用重新定位对象（例如本教程中使用的立方体）、使用按钮切换体验周围的边界框、使用定位和旋转调节器，等等。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-229">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6fe7f-230">祝贺</span><span class="sxs-lookup"><span data-stu-id="6fe7f-230">Congratulations</span></span>

<span data-ttu-id="6fe7f-231">在本教程中，你已了解 Azure 空间定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-231">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="6fe7f-232">本教程提供了多个按钮，让你了解启动和停止 Azure 空间定位点会话，以及在单个设备上创建、上传和下载 Azure 空间定位点所要执行的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-232">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="6fe7f-233">下一课程会介绍如何将 Azure 定位点 ID 保存到 HoloLens 2 以供检索（甚至在重启应用程序后也可供检索），以及如何在多个设备之间转移定位点 ID，以实现空间对齐。</span><span class="sxs-lookup"><span data-stu-id="6fe7f-233">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="6fe7f-234">下一课：2.保存、检索和共享 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="6fe7f-234">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
