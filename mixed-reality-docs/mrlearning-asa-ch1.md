---
title: Azure 空间锚点教程-1。 Azure 空间定位点入门
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 861c42f9449fcb3cf038258af91088fc927941e5
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940925"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="9d420-105">1. Azure 空间定位点入门</span><span class="sxs-lookup"><span data-stu-id="9d420-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="9d420-106">概述</span><span class="sxs-lookup"><span data-stu-id="9d420-106">Overview</span></span>

<span data-ttu-id="9d420-107">欢迎使用 HoloLens 2 教程的第二个系列。</span><span class="sxs-lookup"><span data-stu-id="9d420-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="9d420-108">在此三部分教程系列中，你将了解 Azure 空间锚的基础知识。</span><span class="sxs-lookup"><span data-stu-id="9d420-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="9d420-109">在第一个教程中，开始[使用 Azure 空间定位点](mrlearning-asa-ch1.md)，你将浏览启动和停止 azure 会话以及在单个设备上创建、上传和下载 azure 定位所需的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="9d420-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="9d420-110">在第二个教程中，[保存、检索和共享 Azure 空间锚](mrlearning-asa-ch2.md)，你将了解如何通过将定位点信息保存到 HoloLens 2 的存储来跨多个应用程序会话保存 Azure 空间锚，以及如何将此锚点信息共享到其他设备进行多设备锚点对齐。</span><span class="sxs-lookup"><span data-stu-id="9d420-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="9d420-111">在第三个教程中，[显示 Azure 空间锚点反馈](mrlearning-asa-ch3.md)后，你将了解如何在使用 Azure 空间锚点时向用户提供有关定位点事件和状态的反馈。</span><span class="sxs-lookup"><span data-stu-id="9d420-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="9d420-112">目标</span><span class="sxs-lookup"><span data-stu-id="9d420-112">Objectives</span></span>

* <span data-ttu-id="9d420-113">了解通过 Azure 空间锚点与 HoloLens 2 进行开发的基础知识</span><span class="sxs-lookup"><span data-stu-id="9d420-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="9d420-114">创建、上传和下载空间锚</span><span class="sxs-lookup"><span data-stu-id="9d420-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9d420-115">必备条件</span><span class="sxs-lookup"><span data-stu-id="9d420-115">Prerequisites</span></span>

* <span data-ttu-id="9d420-116">满足[快速入门：创建使用 Azure 空间锚点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程中所[列的要求](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites)。</span><span class="sxs-lookup"><span data-stu-id="9d420-116">Meet the requirements listed in the [Prerequisites](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) section of the  [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="9d420-117">完成[快速入门：创建使用 Azure 空间锚点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程中的[创建空间锚定资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分。</span><span class="sxs-lookup"><span data-stu-id="9d420-117">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="9d420-118">如果尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。</span><span class="sxs-lookup"><span data-stu-id="9d420-118">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="9d420-119">创建 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="9d420-119">Creating the Unity project</span></span>

<span data-ttu-id="9d420-120">在本部分中，将创建一个新的 Unity 项目，并对其进行配置以实现 Windows Mixed Reality。</span><span class="sxs-lookup"><span data-stu-id="9d420-120">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="9d420-121">创建一个 Unity 项目，并为其提供一个合适的名称，例如， _Azure 空间锚，教程_。</span><span class="sxs-lookup"><span data-stu-id="9d420-121">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="9d420-122">为 Windows Mixed Reality 配置 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="9d420-122">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="9d420-123">若要提醒如何创建 Unity 项目并为其配置 Windows Mixed Reality，可以参阅[初始化项目和首个应用程序](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)教程（这是[入门教程](mrlearning-base.md)系列的一部分）中的 "[创建新 Unity 项目](mrlearning-base-ch1.md#create-new-unity-project)" 和 "[为 windows 配置 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)" 部分。</span><span class="sxs-lookup"><span data-stu-id="9d420-123">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="9d420-124">添加内置 Unity 包</span><span class="sxs-lookup"><span data-stu-id="9d420-124">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="9d420-125">在本部分中，将添加将在项目中使用的工具包和 Sdk 所需的内置 Unity 资产和包。</span><span class="sxs-lookup"><span data-stu-id="9d420-125">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="9d420-126">导入 TMP 必要的资源。</span><span class="sxs-lookup"><span data-stu-id="9d420-126">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="9d420-127">我们正在添加此包，因为混合现实工具包需要此包。</span><span class="sxs-lookup"><span data-stu-id="9d420-127">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="9d420-128">在 Unity 菜单中，选择 " **Window** > **TextMeshPro** " > **导入 TMP 基本资源**"。</span><span class="sxs-lookup"><span data-stu-id="9d420-128">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="9d420-130">在 "导入 Unity 包" 弹出窗口中，首先确保通过单击 "**全部**" 按钮选择所有资产，然后单击 "**导入**" 按钮导入资产。</span><span class="sxs-lookup"><span data-stu-id="9d420-130">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="9d420-132">安装 AR Foundation。</span><span class="sxs-lookup"><span data-stu-id="9d420-132">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="9d420-133">我们正在添加此包，因为它是 Azure 空间锚点 SDK 所必需的。</span><span class="sxs-lookup"><span data-stu-id="9d420-133">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="9d420-134">在 Unity 菜单中，选择 " **Window** > **程序包管理器**"。</span><span class="sxs-lookup"><span data-stu-id="9d420-134">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="9d420-136">在 "包管理器" 窗口中，选择 " **AR Foundation** "，然后单击 "**安装**" 按钮安装包。</span><span class="sxs-lookup"><span data-stu-id="9d420-136">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="9d420-137">可能需要几秒钟时间，才能在列表中显示 AR 基础包。</span><span class="sxs-lookup"><span data-stu-id="9d420-137">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9d420-139">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="9d420-139">Importing the tutorial assets</span></span>

<span data-ttu-id="9d420-140">在本部分中，你将下载并导入所有教程资产。</span><span class="sxs-lookup"><span data-stu-id="9d420-140">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="9d420-141">下载资产。</span><span class="sxs-lookup"><span data-stu-id="9d420-141">Download the assets.</span></span>

    * <span data-ttu-id="9d420-142">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) （版本2.0.0）</span><span class="sxs-lookup"><span data-stu-id="9d420-142">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="9d420-143">MixedReality. 2.1.0. unitypackage。</span><span class="sxs-lookup"><span data-stu-id="9d420-143">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="9d420-144">MRTK.HoloLens2. GettingStarted. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="9d420-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="9d420-145">MRTK.HoloLens2. AzureSpatialAnchors. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="9d420-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="9d420-146">导入资产。</span><span class="sxs-lookup"><span data-stu-id="9d420-146">Import the assets.</span></span>

    <span data-ttu-id="9d420-147">在 Unity 菜单中，选择 "**资产** > **导入包** > **自定义包 ...** "。</span><span class="sxs-lookup"><span data-stu-id="9d420-147">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="9d420-149">在导入包 .。。弹出窗口中，选择 " **AzureSpatialAnchors" unitypackage**并单击 "**打开**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="9d420-149">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="9d420-151">在 "导入 Unity 包" 弹出窗口中，首先确保通过单击 "**全部**" 按钮选择所有资产，然后单击 "**导入**" 按钮导入资产。</span><span class="sxs-lookup"><span data-stu-id="9d420-151">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="9d420-153">重复上述步骤以导入其余资产包。</span><span class="sxs-lookup"><span data-stu-id="9d420-153">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="9d420-154">完成后，Unity 项目的 "**资产**" 文件夹应该包含这些子文件夹。</span><span class="sxs-lookup"><span data-stu-id="9d420-154">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="9d420-156">创建和准备场景</span><span class="sxs-lookup"><span data-stu-id="9d420-156">Creating and preparing the scene</span></span>

<span data-ttu-id="9d420-157">在本部分中，将通过添加混合现实工具包和某些教程 prototyping 来创建和准备场景。</span><span class="sxs-lookup"><span data-stu-id="9d420-157">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="9d420-158">创建新场景。</span><span class="sxs-lookup"><span data-stu-id="9d420-158">Create a new scene.</span></span>

    <span data-ttu-id="9d420-159">在 Unity 菜单中，选择 "**文件** > "**新场景**"。</span><span class="sxs-lookup"><span data-stu-id="9d420-159">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="9d420-161">在 Unity 菜单中，选择 "**文件**" > **另存为 ...** "。</span><span class="sxs-lookup"><span data-stu-id="9d420-161">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="9d420-163">在 "保存场景" 弹出窗口中，导航到项目的 "**场景**" 文件夹，为场景提供一个合适的名称（例如_ASATutorialScene_），然后单击 "**保存**" 按钮保存场景。</span><span class="sxs-lookup"><span data-stu-id="9d420-163">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="9d420-165">只要该场景位于项目的 "资产" 文件夹内，你就可以将其保存到任意位置。</span><span class="sxs-lookup"><span data-stu-id="9d420-165">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="9d420-166">但是，若要使项目保持井然有序，通常建议将其保存在项目的场景文件夹中。</span><span class="sxs-lookup"><span data-stu-id="9d420-166">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="9d420-167">添加混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="9d420-167">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="9d420-168">在 Unity 菜单中，选择 "**混合现实工具包**" > **添加到场景并配置 ...** "。</span><span class="sxs-lookup"><span data-stu-id="9d420-168">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="9d420-170">在 "选择 MixedRealityToolkitConfigurationProfile" 弹出窗口中，单击 " **DefaultHoloLens2ConfigurationProfile** "，将其设置为场景的 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="9d420-170">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="9d420-172">在 Unity 菜单中，选择 "**文件**" > **保存**"以保存场景。</span><span class="sxs-lookup"><span data-stu-id="9d420-172">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="9d420-174">您可以使用键盘快捷方式 CTRL + S （macOS 上的命令 + S）在学习本教程时快速保存场景。</span><span class="sxs-lookup"><span data-stu-id="9d420-174">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="9d420-175">添加教程 prototyping。</span><span class="sxs-lookup"><span data-stu-id="9d420-175">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="9d420-176">在 "项目" 面板中，导航到 "**资产**" > **MRTK "。AzureSpatialAnchors** > **prototyping**文件夹。</span><span class="sxs-lookup"><span data-stu-id="9d420-176">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="9d420-177">按住 CTRL 按钮（macOS 上的命令）时，请单击 " **ButtonParent**"、" **DebugWindow**" 和 " **ParentAnchor** " 以选择三个 prototyping。</span><span class="sxs-lookup"><span data-stu-id="9d420-177">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="9d420-179">如果仍选择了三个 prototyping，请将其拖到 "层次结构" 面板中，将它们添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="9d420-179">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="9d420-181">若要重点关注场景中的对象，可以双击 ParentAnchor 对象，然后再次缩小。</span><span class="sxs-lookup"><span data-stu-id="9d420-181">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="9d420-183">如果您在场景中找到大图标，例如大帧 "t" 图标会分散注意力，则可以通过将<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos 切换</a>到 off 位置来隐藏这些图标。</span><span class="sxs-lookup"><span data-stu-id="9d420-183">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="9d420-184">配置按钮以操作场景</span><span class="sxs-lookup"><span data-stu-id="9d420-184">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="9d420-185">在本部分中，会将 prototyping 和脚本添加到场景中，以创建一系列按钮，用于演示本地锚点和 Azure 空间锚点在应用程序中的行为方式。</span><span class="sxs-lookup"><span data-stu-id="9d420-185">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="9d420-186">配置 Pressable 按钮 Holo Lens 2 （脚本）组件。</span><span class="sxs-lookup"><span data-stu-id="9d420-186">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="9d420-187">在 "层次结构" 面板中，展开 " **ButtonParent** " 对象，然后选择名为 " **StartAzureSession**" 的第一个子对象。</span><span class="sxs-lookup"><span data-stu-id="9d420-187">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="9d420-189">在 "检查器" 面板中，向下滚动到 " **Pressable" 按钮 Holo 镜头2（脚本）** 组件，并通过单击 " **+** " 图标向 "**按下" 按钮**添加一个新的事件侦听器。</span><span class="sxs-lookup"><span data-stu-id="9d420-189">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="9d420-191">在 "层次结构" 面板中选择 "StartAzureSession" 对象之后，在 "层次结构" 面板中单击 " **ParentAnchor** " 对象，并将其从 "层次结构" 面板中拖放到刚添加的事件侦听器的空 "**无（对象）** " 字段中，使 ParentAnchor 对象侦听此按钮上按下的按钮</span><span class="sxs-lookup"><span data-stu-id="9d420-191">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="9d420-193">单击同一事件侦听器的 "**不执行函数**" 下拉列表，然后选择 " **AnchorModuleScript** > **StartAzureSession （）** "，将 StartAzureSession （）函数设置为在此按钮上触发按钮按下事件时触发的操作。</span><span class="sxs-lookup"><span data-stu-id="9d420-193">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="9d420-195">配置种不可交互（脚本）组件。</span><span class="sxs-lookup"><span data-stu-id="9d420-195">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="9d420-196">在 "层次结构" 面板中选择 "StartAzureSession" 对象后，在 "检查器" 面板中，向下滚动到 "**种不可交互（脚本）** " 组件，并重复与上述步骤1中的**OnClick （）** 事件相同的过程。</span><span class="sxs-lookup"><span data-stu-id="9d420-196">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="9d420-198">配置剩余按钮</span><span class="sxs-lookup"><span data-stu-id="9d420-198">Configure the remaining buttons</span></span>

    <span data-ttu-id="9d420-199">对于其余的每个按钮，请完成上面的步骤1和步骤2中所述的过程，将函数分配给按下的按钮（）和 OnClick （）事件：</span><span class="sxs-lookup"><span data-stu-id="9d420-199">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="9d420-200">对于**StopAzureSession**对象，请分配**StopAzureSession （）** 函数。</span><span class="sxs-lookup"><span data-stu-id="9d420-200">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="9d420-201">对于**CreateAnchor**对象，分配**CreateAzureAnchor （）** 函数，然后将**ParentAnchor**再次拖动到空的 "**无（游戏对象）** " 字段。</span><span class="sxs-lookup"><span data-stu-id="9d420-201">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="9d420-202">对于 "**开始查找定位点**" 对象，请分配**FindAzureAnchor （）** 函数。</span><span class="sxs-lookup"><span data-stu-id="9d420-202">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="9d420-203">对于 "**删除 Azure 定位**对象" 对象，请分配**DeleteAzureAnchor （）** 函数。</span><span class="sxs-lookup"><span data-stu-id="9d420-203">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="9d420-204">对于 "**删除本地定位点**" 对象，分配**RemoveLocalAnchor （）** 函数，然后将**ParentAnchor**再次拖动到空的 "**无（游戏对象）** " 字段。</span><span class="sxs-lookup"><span data-stu-id="9d420-204">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="9d420-205">将场景连接到 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="9d420-205">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="9d420-206">在 "层次结构" 面板中，选择 " **ParentAnchor** " 对象，然后在 "检查器" 面板中，向下滚动到 "**空间锚管理器（脚本）** " 组件。</span><span class="sxs-lookup"><span data-stu-id="9d420-206">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="9d420-207">然后，在 "**凭据**" 部分中，将空间锚定帐户 Id 和密钥粘贴到相应的**空间锚定帐户 Id**和**空间锚定帐户密钥**字段。</span><span class="sxs-lookup"><span data-stu-id="9d420-207">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="9d420-208">在本教程的[先决条件](mrlearning-asa-ch1.md#prerequisites)中，你已创建了空间锚定帐户 Id 和密钥。</span><span class="sxs-lookup"><span data-stu-id="9d420-208">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="9d420-210">请确保保存场景。</span><span class="sxs-lookup"><span data-stu-id="9d420-210">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="9d420-211">尝试 Azure 空间锚的基本行为</span><span class="sxs-lookup"><span data-stu-id="9d420-211">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="9d420-212">现在，你的场景已配置为演示 Azure 空间定位点的基本知识，接下来可以部署应用，以便体验 Azure 空间锚亲身。</span><span class="sxs-lookup"><span data-stu-id="9d420-212">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="9d420-213">添加其他所需的功能。</span><span class="sxs-lookup"><span data-stu-id="9d420-213">Add additional required capabilities.</span></span>

    <span data-ttu-id="9d420-214">在 Unity 菜单中，选择 "**编辑** > **项目设置 ...** " 以打开 "播放机设置" 面板。</span><span class="sxs-lookup"><span data-stu-id="9d420-214">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="9d420-216">在播放机设置面板中，选择 "**播放机**"，然后单击 "**发布设置**"。</span><span class="sxs-lookup"><span data-stu-id="9d420-216">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="9d420-218">在 "**发布设置**" 中，向下滚动到 "**功能**" 部分，并仔细检查是否已启用在教程开头创建项目时启用的**SpatialPerception**。</span><span class="sxs-lookup"><span data-stu-id="9d420-218">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="9d420-219">然后，启用了**InternetClient**、 **InternetClientServer**、 **PrivateNetworkClientServer**、 **RemovableStorage**、**网络摄像机**和**麦克风**功能。</span><span class="sxs-lookup"><span data-stu-id="9d420-219">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="9d420-221">将应用部署到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="9d420-221">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="9d420-222">有关如何生成 Unity 项目并将其部署到 HoloLens [2 的提醒](mrlearning-base-ch1.md#build-your-application-to-your-device)，请参阅[初始化项目和首个应用程序](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)教程，这是[入门教程](mrlearning-base.md)系列中的一部分。</span><span class="sxs-lookup"><span data-stu-id="9d420-222">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="9d420-223">运行应用程序并按照应用程序中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="9d420-223">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="9d420-224">Azure 空间锚点使用 internet 保存和加载定位数据，因此请确保设备已连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="9d420-224">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="9d420-225">当应用程序在你的设备上运行时，请按照**Azure 空间锚点模块说明**面板上显示的屏幕说明操作。</span><span class="sxs-lookup"><span data-stu-id="9d420-225">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="9d420-227">定位体验</span><span class="sxs-lookup"><span data-stu-id="9d420-227">Anchoring an experience</span></span>

<span data-ttu-id="9d420-228">在前面的部分中，已了解 Azure 空间锚的基础知识。</span><span class="sxs-lookup"><span data-stu-id="9d420-228">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="9d420-229">我们使用多维数据集来表示父游戏对象并将其与附加锚点可视化。</span><span class="sxs-lookup"><span data-stu-id="9d420-229">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="9d420-230">在本部分中，你将了解如何通过将整个体验作为 ParentAnchor 对象的子项来定位。</span><span class="sxs-lookup"><span data-stu-id="9d420-230">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="9d420-231">添加火箭启动器体验。</span><span class="sxs-lookup"><span data-stu-id="9d420-231">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="9d420-232">在 "项目" 面板中，导航到 "**资产**" > **MRTK "。GettingStarted** > **prototyping**文件夹，并选择**火箭 Launcher_Complete** prefab。</span><span class="sxs-lookup"><span data-stu-id="9d420-232">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="9d420-234">在仍选择火箭 Launcher_Complete prefab 的情况下，将其拖动到层次结构面板中**ParentAnchor**对象的顶部，使其成为 ParentAnchor 对象的子对象。</span><span class="sxs-lookup"><span data-stu-id="9d420-234">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="9d420-236">重新定位火箭启动器体验。</span><span class="sxs-lookup"><span data-stu-id="9d420-236">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="9d420-237">将 module**火箭 Launcher_Complete**对象，以便仍公开**ParentAnchor** （多维数据集）。</span><span class="sxs-lookup"><span data-stu-id="9d420-237">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="9d420-239">在应用程序中，用户现在可以通过移动多维数据集来重新定位整个火箭启动器体验。</span><span class="sxs-lookup"><span data-stu-id="9d420-239">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="9d420-240">有各种用户体验流程可用于重定位体验，包括使用重定位对象（例如本教程中使用的多维数据集）、使用按钮切换环绕体验的边界框、使用位置和旋转gizmos 等。</span><span class="sxs-lookup"><span data-stu-id="9d420-240">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9d420-241">祝贺</span><span class="sxs-lookup"><span data-stu-id="9d420-241">Congratulations</span></span>

<span data-ttu-id="9d420-242">在本教程中，已了解 Azure 空间锚的基础知识。</span><span class="sxs-lookup"><span data-stu-id="9d420-242">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="9d420-243">本课程提供多个按钮，使你可以浏览启动和停止 Azure 会话所需的各种步骤，以及在单个设备上创建、上传和下载 azure 锚。</span><span class="sxs-lookup"><span data-stu-id="9d420-243">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="9d420-244">在下一课中，您将学习如何将 Azure 定位 Id 保存到 HoloLens 2 以便检索，甚至在重新启动应用程序后，以及如何在多个设备之间传输定位 Id 即可实现空间对齐。</span><span class="sxs-lookup"><span data-stu-id="9d420-244">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="9d420-245">下一课： 2. 保存、检索和共享 Azure 空间锚</span><span class="sxs-lookup"><span data-stu-id="9d420-245">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
