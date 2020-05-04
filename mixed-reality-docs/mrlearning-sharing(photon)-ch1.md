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
# <a name="1-setting-up-photon-unity-networking"></a>1.设置 Photon Unity Networking

## <a name="overview"></a>概述

本教程介绍如何使用 Photon Unity Networking (PUN) 来准备创建共享体验。 Photon 是可供混合现实开发人员用来创建共享体验的多个网络选项之一。 你将了解如何创建 Photon PUN 应用程序，如何将 Photon PUN 资产导入到 Unity 项目，以及如何将 Unity 项目连接到 Photon PUN 应用程序。

## <a name="objectives"></a>目标

* 了解如何创建 Photon PUN 应用程序
* 了解如何查找和导入 Photon PUN 资产
* 了解如何将 Unity 项目连接到 Photon PUN 应用程序

## <a name="prerequisites"></a>必备条件

>[!TIP]
>如果你尚未完成[入门教程](mrlearning-base.md)和 [Azure 空间定位点教程](mrlearning-asa-ch1.md)系列，我们建议先完成这些教程。

* 一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一些基本的 C# 编程功能
* 一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块
* 完成以下教程的[创建空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分：[快速入门：创建使用 Azure 空间定位点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)

> [!IMPORTANT]
> 建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。

## <a name="creating-and-preparing-the-unity-project"></a>创建和准备 Unity 项目

在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。

为此，请先执行[初始化项目和第一个应用程序](mrlearning-base-ch1.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)的说明：

1. [创建新的 Unity 项目](mrlearning-base-ch1.md#create-new-unity-project)并为其指定适当的名称，例如 *MRTK Tutorials*

2. [配置用于 Windows Mixed Reality 的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [导入 TextMesh Pro 基本资源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [配置用于混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [将混合现实工具包添加到 Unity 场景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)，并为该场景指定适当的名称，例如“MultiUserCapabilities” 

然后，根据[如何配置混合现实工具包配置文件（更改空间感知显示选项）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)中的说明将场景的 MRTK 配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”，并将空间感知网格的显示选项更改为“遮挡”。  

> [!CAUTION]
> 根据上面链接的[配置用于混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)说明中所述，强烈建议不要为 Unity 启用 MSBuild。

## <a name="configuring-the-capabilities"></a>配置功能

在 Unity 菜单中，选择“编辑” > “项目设置...”打开“播放器设置”窗口，然后找到“播放器” >  “发布设置”部分：    

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

在“发布设置”中，向下滚动到“功能”部分，仔细检查在教程中最初创建项目时启用的“InternetClient”、“Microphone”和“SpatialPerception”功能是否确实已启用。      然后，启用“InternetClientServer”、“PrivateNetworkClientServer”和“RemovableStorage”功能：   

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a>添加内置 Unity 包
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

在本部分，你将安装 Unity 的内置 AR Foundation 包，因为在下一部分要导入的 Azure 空间定位点 SDK 需要此包。

在 Unity 菜单中，选择“窗口” > “包管理器”：  

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> AR Foundation 包可能需要在几秒钟后才显示在列表中。

在“包管理器”窗口中选择“AR Foundation”，然后单击“安装”按钮安装该包：  

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>导入教程资产

下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)（版本 2.1.1）
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)中的说明。

导入教程资产后，“项目”窗口应如下所示：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> 导入 MultiUserCapabilities 教程资产包后，会在控制台窗口中看到几个 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 错误，指出缺少类型或命名空间。 这符合预期，并且会在下一部分中（当你导入 Photon 资产时）解决。

## <a name="importing-the-photon-assets"></a>导入 Photon 资产

在本部分中，你将从 Unity 的资产存储导入 Photon Unity Network (PUN) 资产。

在 Unity 菜单中，选择“窗口”   > “资产存储”  以打开“资产存储”窗口，搜索并选择来自 Exit Games 的“PUN 2 - FREE”  ，然后单击“下载”  按钮将资产包下载到 Unity 帐户：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

下载完成后，单击“导入”  按钮以打开“导入 Unity 包”窗口：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

在“导入 Unity 包”窗口中单击“全部”  按钮，确保选择所有资产，然后单击“导入”  按钮以导入资产：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

当 Unity 完成导入过程后，将显示“PUN 向导”窗口，其中加载了“PUN 设置”菜单，此时你可以忽略或关闭此窗口：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a>设置 Photon

在本部分中，将创建 Photon 帐户（如果还没有帐户），并创建新的 PUN 应用程序。

导航到 Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">仪表板</a>，如果你已有想要使用的帐户，请登录；否则，请单击“创建一个”  链接并按照说明注册新帐户：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

登录后，单击“创建新应用”按钮  ：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

在“创建新应用程序”页上，输入以下值：

* 对于 Photon 类型，请选择“Photon PUN”
* 对于“名称”，请输入合适的名称，例如“MRTK 教程” 
* 对于“说明”，请选择性地输入适当的说明
* 对于“Url”，请将字段留空

然后，单击“创建”按钮创建新的应用程序： 

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

Photon 完成创建过程后，新的 PUN 应用程序将显示在仪表板上：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>将 Unity 项目连接到 PUN 应用程序

在本部分中，你要将 Unity 项目连接到在上一部分中创建的 PUN 应用程序。

在 Photon 仪表板上，单击“应用 ID”  字段以显示应用 ID，然后将其复制到剪贴板：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

在 Unity 菜单中，选择“窗口”   > “Photon Unity Networking”   > “PUN 向导”  以打开 PUN 向导窗口，然后单击“设置项目”  按钮以打开“PUN 设置”菜单，并按如下所示对其进行配置：

* 在“应用 ID 或电子邮件”  字段中，粘贴在上一步中复制的 PUN 应用 ID

然后单击“设置项目”  按钮，以应用该应用 ID：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

当 Unity 完成 PUN 设置过程后，“PUN 设置”菜单将显示消息“已完成!”  并在“项目”窗口中自动选择“PhotonServerSettings”  资产，以使其属性显示在“检查器”窗口中：

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a>祝贺

已成功创建了 Photon PUN 应用程序并将其连接到 Unity 项目。 下一步是允许与其他用户建立连接，从而使多个用户可以看到彼此。

[下一教程：2.连接多个用户](mrlearning-sharing(photon)-ch2.md)
