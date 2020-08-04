---
title: Azure 云教程 - 1. 适用于 HoloLens 2 的 Azure 云服务
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现各种 Azure 服务。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: azure, 混合现实, unity, 教程, hololens, hololens 2, azure blob 存储, azure 表存储, azure 空间定位点, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: d69ce965718e31bb5a261631f3f40217e8f7c7d6
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376479"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1.适用于 HoloLens 2 的 Azure 云服务

## <a name="overview"></a>概述

欢迎使用这一系列教程，这些教程重点介绍如何将 Azure 云服务引入 HoloLens 2 应用程序 。 本系列教程包含五个部分，介绍了如何将多个 Azure 云服务集成到 HoloLens 2 的 Unity 项目中  。 在每个连续的章节中，都将添加新的 Azure 云服务，以扩展应用程序功能和用户体验，同时还将介绍每种 Azure 云服务的基础知识 。

> [!NOTE]
> 本系列教程将重点介绍 HoloLens 2，但由于 Unity 具有跨平台的特性，因此大多数知识也适用于桌面和智能手机应用程序。

在第一个教程[适用于 HoloLens 2 的 Azure 云服务简介](mr-learning-azure-01.md)中，首先将解释应用程序的目标，简要介绍每个 Azure 云服务并设置 unity 项目。

在第二个教程[集成 Azure 存储](mr-learning-azure-02.md)中，首先将 Azure 存储集成为演示应用程序的持久性解决方案，了解 Blob 存储和表存储之间的区别、准备必要的项目资源、设置场景并验证读取、更新和删除数据操作。

继续学习第三个教程[集成 Azure 自定义视觉](mr-learning-azure-03.md)，你将使用 Azure 自定义视觉在 HoloLens 2 应用程序中训练和检测图像。 本章首先设置你自己的 Azure 自定义视觉资源，准备场景组成部分，并通过在应用程序内部训练和检测自己的图像来使之付诸实践。

接下来，你将继续学习第四个教程[集成 Azure 空间定位点](mr-learning-azure-04.md)，并了解 Azure 空间定位点服务以保存和查找位置，了解核心概念，准备必要的资源，设置场景并开始在应用程序中使用新功能。

借助第五个教程[将 Azure 机器人服务与 LUIS 集成](mr-learning-azure-05.md)，你可以通过为应用程序提供一种新的用户交互方法（即自然语言）来完成操作。 此功能将通过结合使用 Azure Bot Framework 和语言理解智能服务 (LUIS) 来实现。 最后一章介绍 Azure 机器人服务的基础知识，为加快进程，可使用 Bot Framework Composer 作为零代码解决方案。 创建了机器人后，你就可以将其集成到场景中，并在 HoloLens 2 应用程序的最后阶段运行。

## <a name="application-goals"></a>应用程序目标

在本系列教程中，你将构建一个 HoloLens 2 应用程序，该应用程序可检测图像中的对象并找到其空间位置。 要设置域语言，请从现在被跟踪对象调用此类实体。
用户可以创建被跟踪对象，以通过计算机视觉和/或空间位置来关联一组图像。 所有数据都必须保存到云中。 此外，应用程序的某些方面也可以通过机器人的自然语言来控制。

### <a name="features"></a>功能

* 数据和图像的基本管理
* 图像训练和检测
* 存储空间位置及其指南
* 机器人助手通过自然语言使用某些功能

## <a name="azure-cloud-services"></a>Azure 云服务

若要解决应用程序所需的功能，需要使用以下 Azure 云服务：

### <a name="azure-storage"></a>Azure 存储

使用 [Azure 存储](https://azure.microsoft.com/services/storage/)作为持久性解决方案。 使用该解决方案，你可以将数据存储在表上并上传大型二进制文件（例如图像）。

### <a name="azure-custom-vision"></a>Azure 自定义视觉

借助 [Azure 自定义视觉](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)（[Azure 认知服务](https://azure.microsoft.com/services/cognitive-services/)的一部分），你可以将被跟踪对象关联到一组图像、训练集上的机器学习模型并检测被跟踪对象 。

### <a name="azure-spatial-anchors"></a>Azure 空间定位点

若要存储被跟踪对象的位置，并提供指导说明以找到该位置，请使用 [Azure 空间定位点](https://azure.microsoft.com/services/spatial-anchors/)。

### <a name="azure-bot-service"></a>Azure 机器人服务

该应用程序主要由传统 UI 提供支持，因此你可以使用 [Azure 机器人服务](https://azure.microsoft.com/services/bot-service/)添加一些个性并充当新的交互方法。

## <a name="prerequisites"></a>必备条件

>[!TIP]
>如果你尚未完成[入门教程](mr-learning-base-01.md)系列，建议先完成这些教程。

* 一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一些基本的 C# 编程功能
* 一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* 一个联网的摄像头（如果要通过 Unity 编辑器进行测试）
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.X 并添加了通用 Windows 平台生成支持模块

> [!CAUTION]
> 建议对本系列教程使用 Unity 2019.3.X。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。

## <a name="creating-and-preparing-the-unity-project"></a>创建和准备 Unity 项目

在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。

为此，请先执行[初始化项目和第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：

1. [创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如 Azure 云教程
2. [切换生成平台](mr-learning-base-02.md#configuring-the-unity-project)
3. [导入 TextMeshPro 基本资源](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [导入混合现实工具包](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [配置 Unity 项目](mr-learning-base-02.md#configuring-the-unity-project)
6. [创建并设置场景](mr-learning-base-02.md#creating-and-configuring-the-scene)，并为场景提供一个合适的名称，例如 AzureCloudServices

然后，根据[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)说明将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡” 。

## <a name="installing-inbuilt-unity-packages"></a>安装内置 Unity 包

在 Unity 菜单中，选择“窗口” > “包管理器”打开“包管理器”窗口，然后选择“AR Foundation”并单击“安装”按钮以安装包   ：

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> 你要安装 AR Foundation 包，因为在下一部分中导入 Azure 空间定位点 SDK 时必须使用它。

## <a name="importing-the-tutorial-assets"></a>导入教程资产

下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：

* [用于 Unity 的 Azure 存储](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [Azure 空间定位点](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [MRTK.Tutorials.AzureCloudServices](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)中的说明。

导入教程资产后，“项目”窗口应如下所示：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>创建和准备场景
<!-- TODO: Consider renaming to 'Preparing the scene' -->

在本部分，你将通过添加一些教程预制件来准备场景。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureCloudServices” > “预制件” > “管理器”文件夹   。 按住 Ctrl 按钮并单击“SceneController”、“RootMenu”和“DataManager”以选择这三个预制件  ：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

SceneController (预制件)包含两个脚本：SceneController (脚本)和 UnityDispatcher (脚本)  。 “SceneController”脚本组件包含多个 UX 函数，并简化了照片捕获功能，而 UnityDispatcher 是一个帮助程序类，允许在 Unity 主线程上执行操作 。

“RootMenu (预制件)”是主要的 UI 预制件，它包含通过各种小型脚本组件相互连接的所有 UI 窗口，并控制应用程序的一般 UX 流程。

“DataManager (预制件)”负责与 Azure 存储通信，下一教程将进一步介绍此内容。

现在，在仍选中了这三个预制件的情况下，将其拖动到“层次结构”窗口中，以将其添加到场景：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

若要将焦点置于场景中的对象上，可以双击“RootMenu”对象，然后再次稍微缩小：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> 如果在场景中看到很大的图标（例如，框住的“T”图标会分散注意力），可以通过<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">将调节器 (Gizmos) 切换</a>到关闭位置来隐藏这些图标。

## <a name="configuring-the-scene"></a>配置场景

在本节中，需要将 SceneManager、DataManager 和 RootMenu 连接在一起，为下面的[集成 Azure 存储](mr-learning-azure-01.md)准备好工作场景  。

### <a name="connect-the-objects"></a>连接对象

在“层次结构”窗口中，选择“DataManager”对象：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

在“检查器”窗口中，找到“DataManager (脚本)”组件，你将在“On Data Manager Ready ()”事件上看到一个空槽 。 现在，从“层次结构”窗口将“SceneController”对象拖到“On Data Manager Ready ()”事件 。

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

你将注意到该事件的下拉菜单变为活动状态，单击下拉菜单并导航到 SceneController，然后在子菜单中选择“Init ()”选项 ：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

从“层次结构”窗口选择“SceneController”对象，你将在检查器中找到“SceneController (脚本)”组件 。

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

你将看到有几个未填充的字段，让我们对其进行更改。 将 DataManager 对象从层次结构移到“数据管理器”字段，并将 RootMenu GameObject 从层次结构移动到“主菜单”字段。

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

现在，你的场景已经准备就绪，可用于下一个教程。 不要忘记将其保存到你的项目中。

## <a name="prepare-project-build-pipeline"></a>准备项目生成管道

尽管项目尚未填充内容，但你必须执行一些准备工作，以便项目准备好构建 HoloLens 2。

### <a name="1-add-additional-required-capabilities"></a>1.添加其他所需功能

在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： 

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

在“项目设置”窗口中，依次选择“播放器”、“发布设置” ：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

在“发布设置”中，向下滚动到“功能”部分，仔细检查在教程中最初创建项目时启用的“InternetClient”、“Microphone”和“SpatialPerception”功能是否确实已启用。     然后启用“InternetClientServer”、“PrivateNetworkClientServer”和“Webcam”功能  ：

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2.将应用部署到 HoloLens 2

并非你将在本系列教程中使用的所有功能都可以在 Unity 编辑器中运行，这意味着你需要熟悉如何将应用程序部署到 HoloLens 2 设备上。

> [!TIP]
> 有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[入门教程 - 在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3.在 HoloLens 2 上运行该应用，并按照应用中的说明进行操作

> [!CAUTION]
> 所有 Azure 服务都使用 Internet，因此请确保你的设备已连接到 Internet。

当应用程序在设备上运行时，请接受对以下请求功能的访问权限：

* 麦克风
* 照相机

聊天机器人和自定义视觉等服务需要上述功能才能正常运行 。

## <a name="congratulations"></a>祝贺

本教程介绍了一系列教程，其中介绍了将实现的功能以及如何将 Azure 云服务与 HoloLens 2 应用程序关联。 你已将所需的组件添加到项目中，并为系列本教程准备了场景。

下一课将使用 Azure 存储作为基于云的持久性解决方案来存储数据和图像。

[下一教程：2.集成 Azure 存储](mr-learning-azure-02.md)
