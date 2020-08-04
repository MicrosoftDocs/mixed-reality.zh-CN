---
title: Azure 空间定位点教程 - 2. Azure 空间定位点入门
description: 完成本课程可以了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d117839e51e586f4b905a20510fffc670d34cd4e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376489"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="e61b1-105">2.Azure 空间定位点入门</span><span class="sxs-lookup"><span data-stu-id="e61b1-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="e61b1-106">概述</span><span class="sxs-lookup"><span data-stu-id="e61b1-106">Overview</span></span>

<span data-ttu-id="e61b1-107">本教程将介绍启动和停止 Azure 空间定位点会话，以及在单个设备上创建、上传和下载 Azure 空间定位点所需的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="e61b1-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="e61b1-108">目标</span><span class="sxs-lookup"><span data-stu-id="e61b1-108">Objectives</span></span>

* <span data-ttu-id="e61b1-109">了解有关使用适用于 HoloLens 2 的 Azure 空间定位点进行开发的基础知识</span><span class="sxs-lookup"><span data-stu-id="e61b1-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="e61b1-110">了解如何创建空间定位点并从 Azure 中获取它们</span><span class="sxs-lookup"><span data-stu-id="e61b1-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="e61b1-111">创建和准备 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="e61b1-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="e61b1-112">在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。</span><span class="sxs-lookup"><span data-stu-id="e61b1-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="e61b1-113">为此，请先执行[初始化项目和部署第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：</span><span class="sxs-lookup"><span data-stu-id="e61b1-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="e61b1-114">[创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="e61b1-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="e61b1-115">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="e61b1-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="e61b1-116">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="e61b1-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="e61b1-117">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="e61b1-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="e61b1-118">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="e61b1-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="e61b1-119">[创建和设置场景](mr-learning-base-02.md#creating-and-configuring-the-scene)，并为场景提供一个合适的名称，例如 AzureSpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="e61b1-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="e61b1-120">然后，按照[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)中的说明执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e61b1-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="e61b1-121">将 MRTK 配置配置文件更改为 DefaultHoloLens2ConfigurationProfile </span><span class="sxs-lookup"><span data-stu-id="e61b1-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="e61b1-122">将空间感知网格显示选项更改为“遮挡” 。</span><span class="sxs-lookup"><span data-stu-id="e61b1-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="e61b1-123">安装内置 Unity 包</span><span class="sxs-lookup"><span data-stu-id="e61b1-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="e61b1-124">在 Unity 菜单中，选择“窗口” > “包管理器”打开“包管理器”窗口，然后选择“AR Foundation”并单击“安装”按钮以安装包   ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e61b1-126">你要安装 AR Foundation 包，因为在下一部分中导入 Azure 空间定位点 SDK 时必须使用它。</span><span class="sxs-lookup"><span data-stu-id="e61b1-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="e61b1-127">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="e61b1-127">Importing the tutorial assets</span></span>

<span data-ttu-id="e61b1-128">下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：</span><span class="sxs-lookup"><span data-stu-id="e61b1-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="e61b1-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)（版本 2.2.1）</span><span class="sxs-lookup"><span data-stu-id="e61b1-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="e61b1-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="e61b1-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="e61b1-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="e61b1-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="e61b1-132">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="e61b1-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="e61b1-134">有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)说明。</span><span class="sxs-lookup"><span data-stu-id="e61b1-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="e61b1-135">准备场景</span><span class="sxs-lookup"><span data-stu-id="e61b1-135">Preparing the scene</span></span>

<span data-ttu-id="e61b1-136">在本部分，你将通过添加一些教程预制件来准备场景。</span><span class="sxs-lookup"><span data-stu-id="e61b1-136">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="e61b1-137">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹，然后单击并将以下预制件拖动到“层次结构”窗口中，以将其添加到场景中  ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="e61b1-138">ButtonParent 预制件</span><span class="sxs-lookup"><span data-stu-id="e61b1-138">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="e61b1-139">DebugWindow 预制件</span><span class="sxs-lookup"><span data-stu-id="e61b1-139">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="e61b1-140">Instructions 预制件</span><span class="sxs-lookup"><span data-stu-id="e61b1-140">**Instructions** prefabs</span></span>
* <span data-ttu-id="e61b1-141">ParentAnchor 预制件</span><span class="sxs-lookup"><span data-stu-id="e61b1-141">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="e61b1-143">如果在场景中看到很大的图标（例如，框住的“T”图标会分散注意力），可以通过<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">将调节器 (Gizmos) 切换</a>到关闭位置来隐藏这些图标，如上图所示。</span><span class="sxs-lookup"><span data-stu-id="e61b1-143">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="e61b1-144">配置按钮以操作场景</span><span class="sxs-lookup"><span data-stu-id="e61b1-144">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="e61b1-145">在本部分，你要将脚本添加到场景，以创建一系列按钮事件，用于演示本地定位点和 Azure 空间定位点在应用中的行为方式的基本原理。</span><span class="sxs-lookup"><span data-stu-id="e61b1-145">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="e61b1-146">在“层次结构”窗口中展开“ButtonParent”对象，然后选择名为“StartAzureSession”的第一个子对象，在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示   ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-146">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="e61b1-147">向“无(对象)”字段分配“ParentAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="e61b1-147">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e61b1-148">从“无函数”下拉列表中，选择“AnchorModuleScript” > “StartAzureSession ()”，将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="e61b1-148">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="e61b1-150">在“层次结构”窗口中选择名为“StopAzureSession”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-150">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="e61b1-151">向“无(对象)”字段分配“ParentAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="e61b1-151">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e61b1-152">从“无函数”下拉列表中，选择“AnchorModuleScript” > “StopAzureSession ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="e61b1-152">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="e61b1-154">在“层次结构”窗口中选择名为“CreateAzureAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-154">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="e61b1-155">向“无(对象)”字段分配“ParentAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="e61b1-155">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e61b1-156">从“无函数”下拉列表中，选择“AnchorModuleScript” > “CreateAzureAnchor ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="e61b1-156">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="e61b1-157">将 ParentAnchor 对象分配到空的“无(游戏对象)”字段，使其成为 CreateAzureAnchor () 函数的参数 </span><span class="sxs-lookup"><span data-stu-id="e61b1-157">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="e61b1-159">在“层次结构”窗口中选择名为“RemoveLocalAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-159">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="e61b1-160">向“无(对象)”字段分配“ParentAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="e61b1-160">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e61b1-161">从“无函数”下拉列表中，选择“AnchorModuleScript” > “RemoveLocalAnchor ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="e61b1-161">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="e61b1-162">将 ParentAnchor 对象分配到空的“无(游戏对象)”字段，使其成为 RemoveLocalAnchor () 函数的参数 </span><span class="sxs-lookup"><span data-stu-id="e61b1-162">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="e61b1-164">在“层次结构”窗口中选择名为“FindAzureAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-164">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="e61b1-165">向“无(对象)”字段分配“ParentAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="e61b1-165">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e61b1-166">从“无函数”下拉列表中，选择“AnchorModuleScript” > “FindAzureAnchor ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="e61b1-166">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="e61b1-168">在“层次结构”窗口中选择名为“DeleteAzureAnchor”的下一个按钮，然后在“检查器”窗口中配置“按钮配置帮助程序(脚本)”组件的“On Click ()”事件，如下所示  ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-168">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="e61b1-169">向“无(对象)”字段分配“ParentAnchor”对象 </span><span class="sxs-lookup"><span data-stu-id="e61b1-169">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="e61b1-170">从“无函数”下拉列表中，选择“AnchorModuleScript” > “DeleteAzureAnchor ()”将此函数设置为触发事件时要执行的操作  </span><span class="sxs-lookup"><span data-stu-id="e61b1-170">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="e61b1-172">将场景连接到 Azure 资源</span><span class="sxs-lookup"><span data-stu-id="e61b1-172">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="e61b1-173">在“层次结构”窗口中选择“ParentAnchor”对象，然后在“检查器”窗口中，找到“空间定位点管理器(脚本)”组件。 </span><span class="sxs-lookup"><span data-stu-id="e61b1-173">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="e61b1-174">使用来自 Azure 空间定位点帐户（该帐户作为本教程系列[必备条件](mr-learning-asa-01.md#prerequisites)的一部分创建）的凭据配置“凭据”部分：</span><span class="sxs-lookup"><span data-stu-id="e61b1-174">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="e61b1-175">在“空间定位点帐户 ID”字段中，粘贴来自你的 Azure 空间定位点帐户的“帐户 ID”</span><span class="sxs-lookup"><span data-stu-id="e61b1-175">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="e61b1-176">在“空间定位点帐户密钥”字段中，粘贴来自你的 Azure 空间定位点帐户的主“访问密钥”或辅助“访问密钥”</span><span class="sxs-lookup"><span data-stu-id="e61b1-176">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="e61b1-178">尝试 Azure 空间定位点的基本行为</span><span class="sxs-lookup"><span data-stu-id="e61b1-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="e61b1-179">Azure 空间定位点不能在 Unity 中运行，因此，若要测试 Azure 空间定位点功能，需生成项目并将应用部署到设备。</span><span class="sxs-lookup"><span data-stu-id="e61b1-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="e61b1-180">有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[在 HoloLens 2 上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。</span><span class="sxs-lookup"><span data-stu-id="e61b1-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="e61b1-181">当应用在设备上运行时，请按照“Azure 空间定位点教程说明”面板上显示的屏幕说明进行操作：</span><span class="sxs-lookup"><span data-stu-id="e61b1-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="e61b1-182">将多维数据集移动至其他位置</span><span class="sxs-lookup"><span data-stu-id="e61b1-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="e61b1-183">启动 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="e61b1-183">Start Azure Session</span></span>
1. <span data-ttu-id="e61b1-184">创建 Azure 定位点（在多维数据集的位置创建定位点）。</span><span class="sxs-lookup"><span data-stu-id="e61b1-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="e61b1-185">停止 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="e61b1-185">Stop Azure Session</span></span>
1. <span data-ttu-id="e61b1-186">删除本地定位点（允许用户移动多维数据集）</span><span class="sxs-lookup"><span data-stu-id="e61b1-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="e61b1-187">将多维数据集移动至其他位置</span><span class="sxs-lookup"><span data-stu-id="e61b1-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="e61b1-188">启动 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="e61b1-188">Start Azure Session</span></span>
1. <span data-ttu-id="e61b1-189">查找 Azure 定位点（将多维数据集定位到步骤 3 所述的位置）</span><span class="sxs-lookup"><span data-stu-id="e61b1-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="e61b1-190">删除 Azure 定位点</span><span class="sxs-lookup"><span data-stu-id="e61b1-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="e61b1-191">停止 Azure 会话</span><span class="sxs-lookup"><span data-stu-id="e61b1-191">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="e61b1-193">Azure 空间定位点将使用 Internet 来保存和加载定位点数据，因此请确保设备已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="e61b1-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="e61b1-194">定位体验</span><span class="sxs-lookup"><span data-stu-id="e61b1-194">Anchoring an experience</span></span>

<span data-ttu-id="e61b1-195">前面的部分已介绍 Azure 空间定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="e61b1-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="e61b1-196">我们已使用一个立方体来表示并可视化了附有定位点的父游戏对象。</span><span class="sxs-lookup"><span data-stu-id="e61b1-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="e61b1-197">本部分将介绍如何通过将整个体验定位为 ParentAnchor 对象的子级，来定位该体验。</span><span class="sxs-lookup"><span data-stu-id="e61b1-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="e61b1-198">在“层次结构”窗口中选择“ParentAnchor”对象，然后在“检查器”窗口中配置“转换”组件，如下所示 ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="e61b1-199">将“比例 X”改为 1.1</span><span class="sxs-lookup"><span data-stu-id="e61b1-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="e61b1-200">将“比例 Z”改为 1.1</span><span class="sxs-lookup"><span data-stu-id="e61b1-200">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="e61b1-202">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件” > 探测器”文件夹，然后单击并将“RoverExplorer_Complete”预制件拖动到“层次结构”窗口中，以将其添加到场景中    ：</span><span class="sxs-lookup"><span data-stu-id="e61b1-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="e61b1-204">在“层次结构”窗口中新添加的 RoverModule_Complete 对象仍处于选中状态的情况下，将其拖动到“ParentAnchor”对象上，使其成为 ParentAnchor 对象的子级：</span><span class="sxs-lookup"><span data-stu-id="e61b1-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="e61b1-206">如果现在重建项目并将应用部署到设备，可以通过移动已调整大小的多维数据集来重新定位整个漫游者探测器。</span><span class="sxs-lookup"><span data-stu-id="e61b1-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="e61b1-207">有多种用户体验流可用于重新定位体验，包括使用重新定位对象（例如本教程中使用的立方体）、使用按钮切换体验周围的边界框、使用定位和旋转调节器，等等。</span><span class="sxs-lookup"><span data-stu-id="e61b1-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e61b1-208">祝贺</span><span class="sxs-lookup"><span data-stu-id="e61b1-208">Congratulations</span></span>

<span data-ttu-id="e61b1-209">在本教程中，你已了解 Azure 空间定位点的基础知识。</span><span class="sxs-lookup"><span data-stu-id="e61b1-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="e61b1-210">本教程提供了多个按钮，让你了解启动和停止 Azure 空间定位点会话所需的各个步骤。</span><span class="sxs-lookup"><span data-stu-id="e61b1-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="e61b1-211">以及如何在单个设备上创建、上传和下载 Azure 空间定位点。</span><span class="sxs-lookup"><span data-stu-id="e61b1-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="e61b1-212">下一教程将介绍如何将 Azure 定位点 ID 保存到 HoloLens 2 以供检索（甚至在重启应用后也可供检索），以及如何在多个设备之间转移定位点 ID，以实现空间对齐。</span><span class="sxs-lookup"><span data-stu-id="e61b1-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="e61b1-213">下一教程：3.保存、检索和共享 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="e61b1-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
