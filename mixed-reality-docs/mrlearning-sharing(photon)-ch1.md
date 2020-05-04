---
title: 多用户功能教程 - 1. 设置 Photon Unity Networking
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610726"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="37ca8-105">1.设置 Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="37ca8-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="37ca8-106">概述</span><span class="sxs-lookup"><span data-stu-id="37ca8-106">Overview</span></span>

<span data-ttu-id="37ca8-107">本教程介绍如何使用 Photon Unity Networking (PUN) 来准备创建共享体验。</span><span class="sxs-lookup"><span data-stu-id="37ca8-107">In this tutorial, you will learn how to prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="37ca8-108">Photon 是可供混合现实开发人员用来创建共享体验的多个网络选项之一。</span><span class="sxs-lookup"><span data-stu-id="37ca8-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="37ca8-109">你将了解如何创建 Photon PUN 应用程序，如何将 Photon PUN 资产导入到 Unity 项目，以及如何将 Unity 项目连接到 Photon PUN 应用程序。</span><span class="sxs-lookup"><span data-stu-id="37ca8-109">You will learn how to create a Photon PUN application, import Photon PUN assets into your Unity project, and connect your Unity project to the Photon PUN application.</span></span>

## <a name="objectives"></a><span data-ttu-id="37ca8-110">目标</span><span class="sxs-lookup"><span data-stu-id="37ca8-110">Objectives</span></span>

* <span data-ttu-id="37ca8-111">了解如何创建 Photon PUN 应用程序</span><span class="sxs-lookup"><span data-stu-id="37ca8-111">Learn how to create a Photon PUN application</span></span>
* <span data-ttu-id="37ca8-112">了解如何查找和导入 Photon PUN 资产</span><span class="sxs-lookup"><span data-stu-id="37ca8-112">Learn how to find and import the Photon PUN assets</span></span>
* <span data-ttu-id="37ca8-113">了解如何将 Unity 项目连接到 Photon PUN 应用程序</span><span class="sxs-lookup"><span data-stu-id="37ca8-113">Learn how to connect your Unity project to the Photon PUN application</span></span>

## <a name="prerequisites"></a><span data-ttu-id="37ca8-114">必备条件</span><span class="sxs-lookup"><span data-stu-id="37ca8-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="37ca8-115">如果你尚未完成[入门教程](mrlearning-base.md)和 [Azure 空间定位点教程](mrlearning-asa-ch1.md)系列，我们建议先完成这些教程。</span><span class="sxs-lookup"><span data-stu-id="37ca8-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="37ca8-116">一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="37ca8-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="37ca8-117">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="37ca8-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="37ca8-118">一些基本的 C# 编程功能</span><span class="sxs-lookup"><span data-stu-id="37ca8-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="37ca8-119">一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="37ca8-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="37ca8-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="37ca8-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="37ca8-121">完成以下教程的[创建空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分：[快速入门：创建使用 Azure 空间定位点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)</span><span class="sxs-lookup"><span data-stu-id="37ca8-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>

> [!IMPORTANT]
> <span data-ttu-id="37ca8-122">建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。</span><span class="sxs-lookup"><span data-stu-id="37ca8-122">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="37ca8-123">这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="37ca8-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="37ca8-124">创建和准备 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="37ca8-124">Creating and preparing the Unity project</span></span>

<span data-ttu-id="37ca8-125">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="37ca8-125">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="37ca8-126">为此，请先执行[初始化项目和第一个应用程序](mrlearning-base-ch1.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)的说明：</span><span class="sxs-lookup"><span data-stu-id="37ca8-126">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="37ca8-127">[创建新的 Unity 项目](mrlearning-base-ch1.md#create-new-unity-project)并为其指定适当的名称，例如 *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="37ca8-127">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="37ca8-128">配置用于 Windows Mixed Reality 的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="37ca8-128">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="37ca8-129">导入 TextMesh Pro 基本资源</span><span class="sxs-lookup"><span data-stu-id="37ca8-129">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="37ca8-130">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="37ca8-130">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="37ca8-131">配置用于混合现实工具包的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="37ca8-131">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="37ca8-132">[将混合现实工具包添加到 Unity 场景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)，并为该场景指定适当的名称，例如“MultiUserCapabilities” </span><span class="sxs-lookup"><span data-stu-id="37ca8-132">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="37ca8-133">然后，根据[如何配置混合现实工具包配置文件（更改空间感知显示选项）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡”。  </span><span class="sxs-lookup"><span data-stu-id="37ca8-133">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="37ca8-134">根据上面链接的[配置用于混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)说明中所述，强烈建议不要为 Unity 启用 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="37ca8-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="37ca8-135">配置功能</span><span class="sxs-lookup"><span data-stu-id="37ca8-135">Configuring the capabilities</span></span>

<span data-ttu-id="37ca8-136">在 Unity 菜单中，选择“编辑” > “项目设置...”打开“播放器设置”窗口，然后找到“播放器” >  “发布设置”部分：    </span><span class="sxs-lookup"><span data-stu-id="37ca8-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

<span data-ttu-id="37ca8-138">在“发布设置”中，向下滚动到“功能”部分，仔细检查在教程中最初创建项目时启用的“InternetClient”、“Microphone”和“SpatialPerception”功能是否确实已启用。     </span><span class="sxs-lookup"><span data-stu-id="37ca8-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="37ca8-139">然后，启用“InternetClientServer”、“PrivateNetworkClientServer”和“RemovableStorage”功能：   </span><span class="sxs-lookup"><span data-stu-id="37ca8-139">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **RemovableStorage** capabilities:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="37ca8-141">添加内置 Unity 包</span><span class="sxs-lookup"><span data-stu-id="37ca8-141">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="37ca8-142">在本部分，你将安装 Unity 的内置 AR Foundation 包，因为在下一部分要导入的 Azure 空间定位点 SDK 需要此包。</span><span class="sxs-lookup"><span data-stu-id="37ca8-142">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="37ca8-143">在 Unity 菜单中，选择“窗口” > “包管理器”：  </span><span class="sxs-lookup"><span data-stu-id="37ca8-143">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="37ca8-145">AR Foundation 包可能需要在几秒钟后才显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="37ca8-145">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="37ca8-146">在“包管理器”窗口中选择“AR Foundation”，然后单击“安装”按钮安装该包：  </span><span class="sxs-lookup"><span data-stu-id="37ca8-146">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="37ca8-148">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="37ca8-148">Importing the tutorial assets</span></span>

<span data-ttu-id="37ca8-149">下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：</span><span class="sxs-lookup"><span data-stu-id="37ca8-149">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="37ca8-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)（版本 2.1.1）</span><span class="sxs-lookup"><span data-stu-id="37ca8-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="37ca8-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="37ca8-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="37ca8-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="37ca8-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [<span data-ttu-id="37ca8-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="37ca8-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="37ca8-154">有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)中的说明。</span><span class="sxs-lookup"><span data-stu-id="37ca8-154">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="37ca8-155">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="37ca8-155">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="37ca8-157">导入 MultiUserCapabilities 教程资产包后，会在控制台窗口中看到几个 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 错误，指出缺少类型或命名空间。</span><span class="sxs-lookup"><span data-stu-id="37ca8-157">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="37ca8-158">这符合预期，并且会在下一部分中（当你导入 Photon 资产时）解决。</span><span class="sxs-lookup"><span data-stu-id="37ca8-158">This is to be expected and will be resolved in the next section when you import the Photon assets.</span></span>

## <a name="importing-the-photon-assets"></a><span data-ttu-id="37ca8-159">导入 Photon 资产</span><span class="sxs-lookup"><span data-stu-id="37ca8-159">Importing the Photon assets</span></span>

<span data-ttu-id="37ca8-160">在本部分中，你将从 Unity 的资产存储导入 Photon Unity Network (PUN) 资产。</span><span class="sxs-lookup"><span data-stu-id="37ca8-160">In this section, you will import the Photon Unity Network (PUN) assets from Unity's Asset Store.</span></span>

<span data-ttu-id="37ca8-161">在 Unity 菜单中，选择“窗口”   > “资产存储”  以打开“资产存储”窗口，搜索并选择来自 Exit Games 的“PUN 2 - FREE”  ，然后单击“下载”  按钮将资产包下载到 Unity 帐户：</span><span class="sxs-lookup"><span data-stu-id="37ca8-161">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, and then click the **Download** button to download the asset package to your Unity account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

<span data-ttu-id="37ca8-163">下载完成后，单击“导入”  按钮以打开“导入 Unity 包”窗口：</span><span class="sxs-lookup"><span data-stu-id="37ca8-163">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

<span data-ttu-id="37ca8-165">在“导入 Unity 包”窗口中单击“全部”  按钮，确保选择所有资产，然后单击“导入”  按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="37ca8-165">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

<span data-ttu-id="37ca8-167">当 Unity 完成导入过程后，将显示“PUN 向导”窗口，其中加载了“PUN 设置”菜单，此时你可以忽略或关闭此窗口：</span><span class="sxs-lookup"><span data-stu-id="37ca8-167">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a><span data-ttu-id="37ca8-169">设置 Photon</span><span class="sxs-lookup"><span data-stu-id="37ca8-169">Setting up Photon</span></span>

<span data-ttu-id="37ca8-170">在本部分中，将创建 Photon 帐户（如果还没有帐户），并创建新的 PUN 应用程序。</span><span class="sxs-lookup"><span data-stu-id="37ca8-170">In this section, you will create a Photon account, if you don't already have one, and create a new PUN application.</span></span>

<span data-ttu-id="37ca8-171">导航到 Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">仪表板</a>，如果你已有想要使用的帐户，请登录；否则，请单击“创建一个”  链接并按照说明注册新帐户：</span><span class="sxs-lookup"><span data-stu-id="37ca8-171">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

<span data-ttu-id="37ca8-173">登录后，单击“创建新应用”按钮  ：</span><span class="sxs-lookup"><span data-stu-id="37ca8-173">Once signed in, click the **Create a New App** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

<span data-ttu-id="37ca8-175">在“创建新应用程序”页上，输入以下值：</span><span class="sxs-lookup"><span data-stu-id="37ca8-175">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="37ca8-176">对于 Photon 类型，请选择“Photon PUN”</span><span class="sxs-lookup"><span data-stu-id="37ca8-176">For Photon Type, select Photon PUN</span></span>
* <span data-ttu-id="37ca8-177">对于“名称”，请输入合适的名称，例如“MRTK 教程” </span><span class="sxs-lookup"><span data-stu-id="37ca8-177">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="37ca8-178">对于“说明”，请选择性地输入适当的说明</span><span class="sxs-lookup"><span data-stu-id="37ca8-178">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="37ca8-179">对于“Url”，请将字段留空</span><span class="sxs-lookup"><span data-stu-id="37ca8-179">For Url, leave the field empty</span></span>

<span data-ttu-id="37ca8-180">然后，单击“创建”按钮创建新的应用程序： </span><span class="sxs-lookup"><span data-stu-id="37ca8-180">Then click the **Create** button to create the new application:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

<span data-ttu-id="37ca8-182">Photon 完成创建过程后，新的 PUN 应用程序将显示在仪表板上：</span><span class="sxs-lookup"><span data-stu-id="37ca8-182">Once Photon has finished the creation process, the new PUN application will appear on your dashboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="37ca8-184">将 Unity 项目连接到 PUN 应用程序</span><span class="sxs-lookup"><span data-stu-id="37ca8-184">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="37ca8-185">在本部分中，你要将 Unity 项目连接到在上一部分中创建的 PUN 应用程序。</span><span class="sxs-lookup"><span data-stu-id="37ca8-185">In this section, you will connect your Unity project to the PUN application you created in the previous section.</span></span>

<span data-ttu-id="37ca8-186">在 Photon 仪表板上，单击“应用 ID”  字段以显示应用 ID，然后将其复制到剪贴板：</span><span class="sxs-lookup"><span data-stu-id="37ca8-186">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

<span data-ttu-id="37ca8-188">在 Unity 菜单中，选择“窗口”   > “Photon Unity Networking”   > “PUN 向导”  以打开 PUN 向导窗口，然后单击“设置项目”  按钮以打开“PUN 设置”菜单，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="37ca8-188">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="37ca8-189">在“应用 ID 或电子邮件”  字段中，粘贴在上一步中复制的 PUN 应用 ID</span><span class="sxs-lookup"><span data-stu-id="37ca8-189">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="37ca8-190">然后单击“设置项目”  按钮，以应用该应用 ID：</span><span class="sxs-lookup"><span data-stu-id="37ca8-190">Then click the **Setup Project** button to apply the app ID:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

<span data-ttu-id="37ca8-192">当 Unity 完成 PUN 设置过程后，“PUN 设置”菜单将显示消息“已完成!” </span><span class="sxs-lookup"><span data-stu-id="37ca8-192">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="37ca8-193">并在“项目”窗口中自动选择“PhotonServerSettings”  资产，以使其属性显示在“检查器”窗口中：</span><span class="sxs-lookup"><span data-stu-id="37ca8-193">and automatically select the **PhotonServerSettings** asset in the Project window so its properties are displayed in the Inspector window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="37ca8-195">祝贺</span><span class="sxs-lookup"><span data-stu-id="37ca8-195">Congratulations</span></span>

<span data-ttu-id="37ca8-196">已成功创建了 Photon PUN 应用程序并将其连接到 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="37ca8-196">You have successfully created a Photon PUN application and connected it to your Unity project.</span></span> <span data-ttu-id="37ca8-197">下一步是允许与其他用户建立连接，从而使多个用户可以看到彼此。</span><span class="sxs-lookup"><span data-stu-id="37ca8-197">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

<span data-ttu-id="37ca8-198">[下一教程：2.连接多个用户](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="37ca8-198">[Next tutorial: 2. Connecting multiple users](mrlearning-sharing(photon)-ch2.md)</span></span>
