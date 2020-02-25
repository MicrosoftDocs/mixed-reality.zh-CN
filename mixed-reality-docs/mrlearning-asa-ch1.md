---
title: Azure 空间锚点教程-1。 Azure 空间定位点入门
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 0163b61bfbf8bd583532092581d94f63e1c2a624
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554614"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Azure 空间定位点入门

## <a name="overview"></a>概述

欢迎使用 HoloLens 2 教程的第二个系列。 在此三部分教程系列中，你将了解 Azure 空间锚的基础知识。

在第一个教程中，开始[使用 Azure 空间定位点](mrlearning-asa-ch1.md)，你将浏览启动和停止 azure 会话以及在单个设备上创建、上传和下载 azure 定位所需的各个步骤。

在第二个教程中，[保存、检索和共享 Azure 空间锚](mrlearning-asa-ch2.md)，你将了解如何通过将定位点信息保存到 HoloLens 2 的存储来跨多个应用程序会话保存 Azure 空间锚，以及如何将此锚点信息共享到其他设备进行多设备锚点对齐。

在第三个教程中，[显示 Azure 空间锚点反馈](mrlearning-asa-ch3.md)后，你将了解如何在使用 Azure 空间锚点时向用户提供有关定位点事件和状态的反馈。

## <a name="objectives"></a>目标

* 了解通过 Azure 空间锚点与 HoloLens 2 进行开发的基础知识
* 创建、上传和下载空间锚

## <a name="prerequisites"></a>先决条件

>[!TIP]
>如果尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。

* 一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具
* Windows 10 SDK 10.0.18362.0 或更高版本
* 一些基本的 C# 编程功能
* 一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块
* 完成[快速入门：创建使用 Azure 空间锚点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程中的[创建空间锚定资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分。

> [!IMPORTANT]
> 建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。 这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。

## <a name="creating-the-unity-project"></a>创建 Unity 项目
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

在本部分中，您将创建一个新的 Unity 项目并使其准备好进行 MRTK 开发。

为此，首先请按照[初始化项目和首个应用程序](mrlearning-base-ch1.md)操作，将[应用程序构建给设备](mrlearning-base-ch1.md#build-your-application-to-your-device)说明，其中包括以下步骤：

1. [创建新的 Unity 项目](mrlearning-base-ch1.md#create-new-unity-project)并为其提供一个合适的名称，例如*MRTK 教程*。

2. [为 Windows Mixed Reality 配置 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [导入 TextMesh Pro 基本资源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [配置混合现实工具包的 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [将混合现实工具包添加到 Unity 场景](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit)，并为场景提供一个合适的名称，例如*AzureSpatialAnchors*

然后，按照[如何配置混合现实工具包配置文件（更改空间感知显示选项）](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option)说明将场景的 MRTK 配置文件更改为**DefaultHoloLens2ConfigurationProfile** ，并将空间感知网格的显示选项更改为**封闭**。

> [!CAUTION]
> 如前面链接的[混合现实工具包说明的配置 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)中所述，强烈建议不要启用 MSBuild for Unity。

## <a name="adding-inbuilt-unity-packages"></a>添加内置 Unity 包
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

在本部分中，你将安装 Unity 的内置 AR Foundation 包，因为你将在下一节中导入 Azure 空间定位点 SDK 需要此包。

在 Unity 菜单中，选择 " **Window** > **包管理器**"：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> 可能需要几秒钟时间，才能在列表中显示 AR 基础包。

在 "包管理器" 窗口中，选择 " **AR Foundation** "，然后单击 "**安装**" 按钮安装包：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>导入教程资产

按照**列出的顺序**下载并**导入**下列 Unity 自定义包：

* [AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) （版本2.1.1）
* [MRTK.HoloLens2. GettingStarted. 2.3.0.2. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [MRTK.HoloLens2. AzureSpatialAnchors. 2.3.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> 有关如何导入 Unity 自定义包的提醒，可以参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)说明。

导入教程资产后，项目窗口应如下所示：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>创建和准备场景
<!-- TODO: Consider renaming to 'Preparing the scene' -->

在本部分中，你将通过添加一些教程 prototyping 来准备场景。

在项目窗口中，导航到 "**资产**" > **MRTK "。AzureSpatialAnchors** > **prototyping**文件夹。 按住 CTRL 按钮的同时，单击 " **ButtonParent**"、" **DebugWindow**"、"**说明**" 和 " **ParentAnchor** "，选择四个 prototyping：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

在仍选择四个 prototyping 的情况下，将其拖动到 "层次结构" 窗口中，将其添加到场景：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

若要重点关注场景中的对象，可以双击 ParentAnchor 对象，然后再次缩小：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> 如果您在场景中找到大图标，例如大帧 "t" 图标会分散注意力，则可以通过将<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos 切换</a>到 off 位置来隐藏这些图标。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>配置按钮以操作场景

在本部分中，会将脚本添加到场景中，以创建一系列按钮事件，其中演示了本地锚点和 Azure 空间锚点在应用程序中的行为方式。

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. 配置 Pressable Button Holo Lens 2 （脚本）组件

在 "层次结构" 窗口中，展开**ButtonParent**对象，然后选择名为**StartAzureSession**的第一个子对象：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

在 "检查器" 窗口中，找到 " **Pressable" 按钮 Holo 镜头2（脚本）** 组件，然后单击 " **+** " 图标，将新的事件侦听器添加到**按下按钮（）** 事件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

如果仍在 "层次结构" 窗口中选择 "StartAzureSession" 对象，请在 "层次结构" 窗口中单击 " **ParentAnchor** " 对象并将其从 "层次结构" 窗口中拖放到刚添加的事件侦听器的空 "**无（对象）** " 字段中，以便通过此按钮侦听按钮按下事件：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

单击同一个事件侦听器的 "**不执行函数**" 下拉列表，然后选择 " **AnchorModuleScript** > **StartAzureSession （）** "，将 StartAzureSession （）函数设置为当按钮按下此按钮引发事件时触发的操作：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. 配置种不可交互（脚本）组件

如果仍在 "层次结构" 窗口中选择 "StartAzureSession" 对象，则在 "检查器" 窗口中，找到**种不可交互（脚本）** 组件，并重复与上述步骤1中的**OnClick （）** 事件相同的过程：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. 配置剩余按钮

对于其余的每个按钮，请完成上面的步骤1和步骤2中所述的过程，将函数分配给**按钮按下（）** 和**OnClick （）** 事件：

* 对于**StopAzureSession**对象，请将 AnchorModuleScript > **StopAzureSession （）** 函数。
* 对于**CreateAzureAnchor**对象，将 AnchorModuleScript > **CreateAzureAnchor （）** 函数，
  * 然后将**ParentAnchor**再次拖动到空的 "**无（游戏对象）** " 字段。
* 对于**RemoveLocalAnchor**对象，将 AnchorModuleScript > **RemoveLocalAnchor （）** 函数，
  * 然后将**ParentAnchor**再次拖动到空的 "**无（游戏对象）** " 字段。
* 对于**FindAzureAnchor**对象，请将 AnchorModuleScript > **FindAzureAnchor （）** 函数。
* 对于**DeleteAzureAnchor**对象，请将 AnchorModuleScript > **DeleteAzureAnchor （）** 函数。

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. 将场景连接到 Azure 资源

在 "层次结构" 窗口中，选择 " **ParentAnchor** " 对象，然后在 "检查器" 窗口中，向下滚动到 "**空间锚管理器（脚本）** " 组件。

然后，在 "**凭据**" 部分中，将你创建的空间锚定 Id 和密钥（已在本教程的[先决条件](mrlearning-asa-ch1.md#prerequisites)中创建）粘贴到相应的**空间锚定帐户 Id**和**空间锚定帐户密钥**字段中：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>尝试 Azure 空间锚的基本行为

现在，你的场景已配置为演示 Azure 空间定位点的基本知识，接下来可以部署应用，以便体验 Azure 空间锚亲身。

### <a name="1-add-additional-required-capabilities"></a>1. 添加其他所需的功能

在 Unity 菜单中，选择 "**编辑** > **项目设置 ...** " 以打开 "播放机设置" 窗口：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

在播放机设置窗口中，选择 "**播放机**"，然后单击 "**发布设置**"：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

在 "**发布设置**" 中，向下滚动到 "**功能**" 部分，然后仔细检查是否已启用在教程开头创建项目时启用的**InternetClient**、**麦克风**和**SpatialPerception**功能。 然后，启用**InternetClientServer**、 **PrivateNetworkClientServer**、 **RemovableStorage**和**网络摄像机**功能：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. 将应用部署到 HoloLens 2

Azure 空间锚不能在 Unity 中运行，因此，若要测试 Azure 空间锚定功能，需要将项目部署到设备。

> [!TIP]
> 有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提醒，可以参阅将[应用程序构建到设备](mrlearning-base-ch1.md#build-your-application-to-your-device)说明。

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. 在 HoloLens 2 上运行应用程序并按照应用程序中的说明操作

> [!CAUTION]
> Azure 空间锚点使用 internet 保存和加载定位数据，因此请确保设备已连接到 internet。

当应用程序在你的设备上运行时，请按照 Azure 空间定位点教程说明面板上显示的屏幕说明操作：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>定位体验

在前面的部分中，已了解 Azure 空间锚的基础知识。 我们使用多维数据集来表示父游戏对象并将其与附加锚点可视化。 在本部分中，你将了解如何通过将整个体验作为 ParentAnchor 对象的子项来定位。

### <a name="1-add-the-rocket-launcher-experience"></a>1. 添加火箭启动器体验

在项目窗口中，导航到 "**资产**" > " **MRTK"。GettingStarted** > **Prototyping** > **RocketLauncher**文件夹并选择**RocketLauncher_Complete** prefab：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

在 RocketLauncher_Complete prefab 仍处于选中状态的情况下，将其拖动到层次结构窗口中**ParentAnchor**对象的顶部，使其成为 ParentAnchor 对象的子对象：

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. 重定位火箭启动器体验

定位、旋转**RocketLauncher_Complete**对象并将其缩放到适当的缩放和方向，同时确保**ParentAnchor**对象仍然公开，例如：

* 转换**位置**X = 0，Y = 0，Z = 3.75
* 转换**X** = 0，Y = 90，Z = 0
* 转换**比例**X = 10，Y = 10，Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

在应用程序中，用户现在可以通过移动多维数据集来重新定位整个火箭启动器体验。

> [!TIP]
> 有各种用户体验流程可用于重定位体验，包括使用重定位对象（例如本教程中使用的多维数据集）、使用按钮切换环绕体验的边界框、使用位置和旋转gizmos 等。

## <a name="congratulations"></a>祝贺你

在本教程中，已了解 Azure 空间锚的基础知识。 本教程提供了多个按钮，使你可以浏览启动和停止 Azure 空间锚点会话所需的各种步骤，以及在单个设备上创建、上传和下载 Azure 空间锚。

在下一课中，您将学习如何将 Azure 定位 Id 保存到 HoloLens 2 以便检索，甚至在重新启动应用程序后，以及如何在多个设备之间传输定位 Id 即可实现空间对齐。

[下一课： 2. 保存、检索和共享 Azure 空间锚](mrlearning-asa-ch2.md)
