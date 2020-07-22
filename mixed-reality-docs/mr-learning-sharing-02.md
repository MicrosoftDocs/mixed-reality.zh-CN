---
title: 多用户功能教程 - 2. 设置 Photon Unity Networking
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: e5817338dbed944232664a86f8b0625bc9d3e1e7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304768"
---
# <a name="2-setting-up-photon-unity-networking"></a>2.设置 Photon Unity Networking

## <a name="overview"></a>概述

在本教程中，你将准备好使用 Photon Unity Networking (PUN) 来创建共享体验。 你将学习如何创建 PUN 应用，如何将 PUN 资产导入到 Unity 项目，以及如何将 Unity 项目连接到 PUN 应用。

## <a name="objectives"></a>目标

* 了解如何创建 PUN 应用
* 了解如何查找和导入 PUN 资产
* 了解如何将 Unity 项目连接到 PUN 应用

## <a name="creating-and-preparing-the-unity-project"></a>创建和准备 Unity 项目

在本部分，你将创建一个新的 Unity 项目，并使其准备好用于 MRTK 开发。

为此，请先执行[初始化项目和部署第一个应用程序](mr-learning-base-02.md)中的以下步骤，但请忽略有关[在设备上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)的说明：

1. [创建 Unity 项目](mr-learning-base-02.md#creating-the-unity-project)并为其指定适当的名称，例如“MRTK 教程”
1. [切换生成平台](mr-learning-base-02.md#configuring-the-unity-project)
1. [导入 TextMeshPro 基本资源](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [导入混合现实工具包](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [配置 Unity 项目](mr-learning-base-02.md#configuring-the-unity-project)
1. [创建和配置场景](mr-learning-base-02.md#creating-and-configuring-the-scene)，并为场景提供适当的名称，例如 MultiUserCapabilities

然后，按照[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)中的说明执行以下操作：

1. 将 MRTK 配置配置文件更改为 DefaultHoloLens2ConfigurationProfile 
1. 将空间感知网格显示选项更改为“遮挡” 。

## <a name="enabling-additional-capabilities"></a>启用附加功能

在 Unity 菜单中，选择“编辑” > “项目设置...”打开“播放器设置”窗口，然后找到“播放器” >  “发布设置”部分：   

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

在“发布设置”中，向下滚动到“功能”部分，仔细检查你在上面的[配置 Unity 项目](mr-learning-base-02.md#configuring-the-unity-project)步骤中启用的“InternetClient”、“Microphone”、“SpatialPerception”和“GazeInput”都已启用     。

然后，启用以下附加功能：

* “InternetClientServer”功能
* “PrivateNetworkClientServer”功能

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a>安装内置 Unity 包

在 Unity 菜单中，选择“窗口” > “包管理器”打开“包管理器”窗口，然后选择“AR Foundation”并单击“安装”按钮以安装包   ：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> 你要安装 AR Foundation 包，因为将在下一部分中导入 Azure Spatial Anchors SDK 必须使用它。

## <a name="importing-the-tutorial-assets"></a>导入教程资产

下载以下 Unity 自定义包，并**按其列出顺序**将其**导入**：

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)（版本 2.2.1）
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

导入教程资产后，“项目”窗口应如下所示：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> 有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)说明。

> [!NOTE]
> 导入 MultiUserCapabilities 教程资产包后，会在控制台窗口中看到几个 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 错误，指出缺少类型或命名空间。 这符合预期，并且会在下一部分中（当你导入 PUN 资产时）解决。

## <a name="importing-the-pun-assets"></a>导入 PUN 资产

在 Unity 菜单中，选择“窗口” > “资产存储”来打开“资产存储”窗口，搜索并选择来自 Exit Games 的“PUN 2 - FREE”，然后单击“下载”按钮，将资产包下载到 Unity 帐户   。

下载完成后，单击“导入”按钮以打开“导入 Unity 包”窗口：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

当 Unity 完成导入过程后，将显示“PUN 向导”窗口，其中加载了“PUN 设置”菜单，此时你可以忽略或关闭此窗口：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a>创建 PUN 应用程序

在本部分中，你将创建一个 Photon 帐户（如果还没有），并创建新的 PUN 应用。

导航到 Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">仪表板</a>，如果你已有想要使用的帐户，请登录；否则，请单击“创建一个”链接并按照说明注册新帐户：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

登录后，单击“创建新应用”按钮：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

在“创建新应用程序”页上，输入以下值：

* 对于 Photon 类型，请选择“PUN”
* 对于“名称”，请输入合适的名称，例如“MRTK 教程”
* 对于“说明”，请选择性地输入适当的说明
* 对于“Url”，请将字段留空

然后，单击“创建”按钮来创建新的应用：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

Photon 完成创建过程后，仪表板上将显示新的 PUN 应用：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>将 Unity 项目连接到 PUN 应用程序

在本部分中，你要将 Unity 项目连接到在上一部分中创建的 PUN 应用。

在 Photon 仪表板上，单击“应用 ID”字段以显示应用 ID，然后将其复制到剪贴板：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

在 Unity 菜单中，选择“窗口” > “Photon Unity Networking” > “PUN 向导”以打开 PUN 向导窗口，然后单击“设置项目”按钮以打开“PUN 设置”菜单，并按如下所示对其进行配置：

* 在“应用 ID 或电子邮件”字段中，粘贴在上一步中复制的 PUN 应用 ID

然后单击“设置项目”按钮，以应用该应用 ID：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

当 Unity 完成 PUN 设置过程后，“PUN 设置”菜单将显示消息“已完成!” 并在“项目”窗口中自动选择“PhotonServerSettings”资产，使其属性显示在检查器窗口中：

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a>祝贺

你已成功创建 PUN 应用并将它连接到了 Unity 项目。 下一步是允许与其他用户建立连接，从而使多个用户可以看到彼此。

[下一教程：3.连接多个用户](mr-learning-sharing-03.md)
