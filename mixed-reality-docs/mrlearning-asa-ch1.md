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
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1.Azure 空间定位点入门

## <a name="overview"></a>概述

欢迎学习 HoloLens 2 教程的第二个系列。 本教学系列由四篇教程构成，本教程介绍 Azure 空间定位点的基础知识。

本第一篇教程 [Azure 空间定位点入门](mrlearning-asa-ch1.md)介绍启动和停止 Azure 会话，以及在单个设备上创建、上传和下载 Azure 定位点所要的各个步骤。

第二篇教程[保存、检索和共享 Azure 空间定位点](mrlearning-asa-ch2.md)将介绍如何通过将定位点信息保存到 HoloLens 2 存储来保存多个应用会话中的 Azure 空间定位点，以及如何与其他设备共享此定位点信息，以对齐多个设备的定位点。

第三篇教程[显示 Azure 空间定位点反馈](mrlearning-asa-ch3.md)将介绍如何在使用 Azure 空间定位点时，向用户提供有关定位点事件和状态的反馈。

在第四篇教程[适用于 Android 和 iOS 的 Azure 空间定位点](mrlearning-asa-ch4.md)介绍了如何生成项目并将其部署到 Android 和 iOS 设备。

## <a name="objectives"></a>目标

* 了解有关使用适用于 HoloLens 2 的 Azure 空间定位点进行开发的基础知识
* 创建、上传和下载空间定位点

## <a name="prerequisites"></a>必备条件

>[!TIP]
>如果你尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。

* 一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一些基本的 C# 编程功能
* [针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens（第 1 代）或 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块
* 完成 [HoloLens 快速入门](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程的[创建空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分。

如果打算部署到 Android
* <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">开发人员实现</a>且<a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">支持 ARCore</a>的 Android 设备，该设备通过 USB 与 Windows 或 macOS 计算机相连接
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并已添加 Android 生成支持模块

如果打算部署到 iOS
* 已安装最新版 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 和 <a href="https://cocoapods.org" target="_blank">CocoaPods</a> 的 macOS 计算机
* <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">与 ARKit 兼容</a>且通过 USB 连接到 macOS 计算机的 iOS 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并已添加 iOS 生成支持模块

> [!IMPORTANT]
> 建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。

## <a name="creating-the-unity-project"></a>创建 Unity 项目
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。

为此，请先执行[初始化项目和第一个应用程序](mrlearning-base-ch1.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)的说明：

1. [创建新的 Unity 项目](mrlearning-base-ch1.md#create-new-unity-project)并为其指定适当的名称，例如 *MRTK Tutorials*

2. [配置用于 Windows Mixed Reality 的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [导入 TextMesh Pro 基本资源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [配置用于混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [将混合现实工具包添加到 Unity 场景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)，并为该场景指定适当的名称，例如 *AzureSpatialAnchors*

然后，根据[如何配置混合现实工具包配置文件（更改空间感知显示选项）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡”。 

> [!CAUTION]
> 根据上面链接的[配置用于混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)说明中所述，强烈建议不要为 Unity 启用 MSBuild。

## <a name="adding-inbuilt-unity-packages"></a>添加内置 Unity 包
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

在本部分，你将安装 Unity 的内置 AR Foundation 包，因为在下一部分要导入的 Azure 空间定位点 SDK 需要此包。

在 Unity 菜单中，选择“窗口” > “包管理器”： 

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> AR Foundation 包可能需要在几秒钟后才显示在列表中。

在“包管理器”窗口中选择“AR Foundation”，然后单击“安装”按钮安装该包： 

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>导入教程资产

下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)（版本 2.1.1）
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)中的说明。

导入教程资产后，“项目”窗口应如下所示：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>创建和准备场景
<!-- TODO: Consider renaming to 'Preparing the scene' -->

在本部分，你将通过添加一些教程预制件来准备场景。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹。   在按住 CTRL 键的同时单击“ButtonParent”、“DebugWindow”、“Instructions”和“ParentAnchor”，以选择这四个预制件：   

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

在仍选中了这四个预制件的情况下，将其拖放到“层次结构”窗口中，以将其添加到场景：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

若要将焦点置于场景中的对象上，可以双击“ParentAnchor”对象，然后再次稍微缩小：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> 如果在场景中看到很大的图标（例如，框住的“T”图标会分散注意力），可以通过<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">将调节器 (Gizmos) 切换</a>到关闭位置来隐藏这些图标。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>配置按钮以操作场景

在本部分，你要将脚本添加到场景，以创建一系列按钮事件，用于演示本地定位点和 Azure 空间定位点在应用程序中的行为方式的基本原理。

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1.配置“可按按钮 Holo Lens 2 (脚本)”组件

在“层次结构”窗口中展开“ButtonParent”对象，然后选择名为“StartAzureSession”的第一个子对象： 

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

在“检查器”窗口中找到“可按按钮 Holo Lens 2 (脚本)”组件，然后单击 **+** 图标将新的事件侦听器添加到“Button Pressed ()”事件： 

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

仍在“层次结构”窗口中选中了“StartAzureSession”对象的情况下，单击“层次结构”窗口中的“ParentAnchor”对象并将其拖放到刚刚添加的事件侦听器的空“无(对象)”字段中，使 ParentAnchor 对象侦听此按钮的 button pressed 事件： 

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

单击同一事件侦听器的“无函数”下拉列表，然后选择“AnchorModuleScript” > “StartAzureSession ()”，将 StartAzureSession () 函数设置为在从此按钮激发 button pressed 事件时要触发的操作：  

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2.配置“可交互(脚本)”组件

仍在“层次结构”窗口中选中了“StartAzureSession”对象的情况下，在“检查器”窗口中找到“可交互(脚本)”组件，然后针对“OnClick ()”事件重复上述步骤 1 中所述的相同过程： 

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3.配置剩余的按钮

对于剩余的每个按钮，请完成上述步骤 1 和 2 中所述的过程，将函数分配到“Button Pressed ()”和“OnClick ()”事件： 

* 对于“StopAzureSession”对象，请分配“AnchorModuleScript”>“StopAzureSession ()”函数。 
* 对于“CreateAzureAnchor”对象，请分配“AnchorModuleScript”>“CreateAzureAnchor ()”函数。 
  * 然后，再次将“ParentAnchor”拖放到空的“无(游戏对象)”字段中。 
* 对于“RemoveLocalAnchor”对象，请分配“AnchorModuleScript”>“RemoveLocalAnchor ()”函数。 
  * 然后，再次将“ParentAnchor”拖放到空的“无(游戏对象)”字段中。 
* 对于“FindAzureAnchor”对象，请分配“AnchorModuleScript”>“FindAzureAnchor ()”函数。 
* 对于“DeleteAzureAnchor”对象，请分配“AnchorModuleScript”>“DeleteAzureAnchor ()”函数。 

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4.将场景连接到 Azure 资源

在“层次结构”窗口中选择“ParentAnchor”对象，然后在“检查器”窗口中，向下滚动到“空间定位点管理器(脚本)”组件。 

然后在“凭据”部分，将在本教程的[先决条件](mrlearning-asa-ch1.md#prerequisites)部分创建的空间定位点帐户 ID 和密钥粘贴到相应的“空间定位点帐户 ID”和“空间定位点帐户密钥”字段中：  

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>尝试 Azure 空间定位点的基本行为

配置用于演示 Azure 空间定位点基本原理的场景后，接下来可以部署应用，以直接体验 Azure 空间定位点。

### <a name="1-add-additional-required-capabilities"></a>1.添加其他所需功能

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“播放器设置”窗口： 

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

在“播放器设置”窗口中，依次选择“播放器”、“发布设置”： 

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

在“发布设置”中，向下滚动到“功能”部分，仔细检查在教程中最初创建项目时启用的“InternetClient”、“Microphone”和“SpatialPerception”功能是否确实已启用。     然后，启用“InternetClientServer”、“PrivateNetworkClientServer”、“RemovableStorage”和“Webcam”功能：   

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2.将应用部署到 HoloLens 2

Azure 空间定位点不能在 Unity 中运行，因此，若要测试 Azure 空间定位点功能，需将项目部署到设备。

> [!TIP]
> 有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)中的说明。

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3.在 HoloLens 2 上运行该应用，并按照应用中的说明进行操作

> [!CAUTION]
> Azure 空间定位点将使用 Internet 来保存和加载定位点数据，因此请确保设备已连接到 Internet。

当应用程序在设备上运行时，请按照“Azure 空间定位点教程说明”面板上显示的屏幕说明进行操作：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>定位体验

前面的部分已介绍 Azure 空间定位点的基础知识。 我们已使用一个立方体来表示并可视化了附有定位点的父游戏对象。 本部分将介绍如何通过将整个体验定位为 ParentAnchor 对象的子级，来定位该体验。

### <a name="1-add-the-rocket-launcher-experience"></a>1.添加火箭发射器体验

在“项目”窗口中导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件” > “RocketLauncher”文件夹，选择“RocketLauncher_Complete”预制件：    

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

在仍选中了 RocketLauncher_Complete 预制件的情况下，将其拖放到“层次结构”窗口中“ParentAnchor”对象的顶部，使其成为 ParentAnchor 对象的子级：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2.重新定位火箭发射器体验

根据适当的标度和方向定位、旋转和缩放“RocketLauncher_Complete”对象，同时确保“ParentAnchor”对象仍处于显示状态，例如： 

* 变换**位置** X = 0，Y = 0，Z = 3.75
* 变换**位置** X = 0，Y = 90，Z = 0
* 变换**标度** X = 10，Y = 10，Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

在应用程序中，用户现在可以通过移动立方体来重新定位整个火箭发射器体验。

> [!TIP]
> 有多种用户体验流可用于重新定位体验，包括使用重新定位对象（例如本教程中使用的立方体）、使用按钮切换体验周围的边界框、使用定位和旋转调节器，等等。

## <a name="congratulations"></a>祝贺

在本教程中，你已了解 Azure 空间定位点的基础知识。 本教程提供了多个按钮，让你了解启动和停止 Azure 空间定位点会话，以及在单个设备上创建、上传和下载 Azure 空间定位点所要执行的各个步骤。

下一课程会介绍如何将 Azure 定位点 ID 保存到 HoloLens 2 以供检索（甚至在重启应用程序后也可供检索），以及如何在多个设备之间转移定位点 ID，以实现空间对齐。

[下一课：2.保存、检索和共享 Azure 空间定位点](mrlearning-asa-ch2.md)
