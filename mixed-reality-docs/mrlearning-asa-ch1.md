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
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Azure 空间定位点入门

## <a name="overview"></a>概述

欢迎使用 HoloLens 2 教程的第二个系列。 在此三部分教程系列中，你将了解 Azure 空间锚的基础知识。

在第一个教程中，开始[使用 Azure 空间定位点](mrlearning-asa-ch1.md)，你将浏览启动和停止 azure 会话以及在单个设备上创建、上传和下载 azure 定位所需的各个步骤。

在第二个教程中，[保存、检索和共享 Azure 空间锚](mrlearning-asa-ch2.md)，你将了解如何通过将定位点信息保存到 HoloLens 2 的存储来跨多个应用程序会话保存 Azure 空间锚，以及如何将此锚点信息共享到其他设备进行多设备锚点对齐。

在第三个教程中，[显示 Azure 空间锚点反馈](mrlearning-asa-ch3.md)后，你将了解如何在使用 Azure 空间锚点时向用户提供有关定位点事件和状态的反馈。

## <a name="objectives"></a>目标

* 了解通过 Azure 空间锚点与 HoloLens 2 进行开发的基础知识
* 创建、上传和下载空间锚

## <a name="prerequisites"></a>必备条件

* 满足[快速入门：创建使用 Azure 空间锚点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程中所[列的要求](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites)。
* 完成[快速入门：创建使用 Azure 空间锚点的 Unity HoloLens 应用](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)教程中的[创建空间锚定资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)部分。
* 如果尚未完成[入门教程](mrlearning-base.md)系列，建议先完成这些教程。

## <a name="creating-the-unity-project"></a>创建 Unity 项目

在本部分中，将创建一个新的 Unity 项目，并对其进行配置以实现 Windows Mixed Reality。

1. 创建一个 Unity 项目，并为其提供一个合适的名称，例如， _Azure 空间锚，教程_。

2. 为 Windows Mixed Reality 配置 Unity 项目。

    >[!TIP]
    >若要提醒如何创建 Unity 项目并为其配置 Windows Mixed Reality，可以参阅[初始化项目和首个应用程序](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)教程（这是[入门教程](mrlearning-base.md)系列的一部分）中的 "[创建新 Unity 项目](mrlearning-base-ch1.md#create-new-unity-project)" 和 "[为 windows 配置 Unity 项目](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)" 部分。

## <a name="adding-inbuilt-unity-packages"></a>添加内置 Unity 包

在本部分中，将添加将在项目中使用的工具包和 Sdk 所需的内置 Unity 资产和包。

1. 导入 TMP 必要的资源。

    >[!NOTE]
    >我们正在添加此包，因为混合现实工具包需要此包。

    在 Unity 菜单中，选择 " **Window** > **TextMeshPro** " > **导入 TMP 基本资源**"。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    在 "导入 Unity 包" 弹出窗口中，首先确保通过单击 "**全部**" 按钮选择所有资产，然后单击 "**导入**" 按钮导入资产。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. 安装 AR Foundation。

    >[!NOTE]
    >我们正在添加此包，因为它是 Azure 空间锚点 SDK 所必需的。

    在 Unity 菜单中，选择 " **Window** > **程序包管理器**"。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    在 "包管理器" 窗口中，选择 " **AR Foundation** "，然后单击 "**安装**" 按钮安装包。

    >[!IMPORTANT]
    >可能需要几秒钟时间，才能在列表中显示 AR 基础包。

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a>导入教程资产

在本部分中，你将下载并导入所有教程资产。

1. 下载资产。

    * [AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) （版本2.0.0）
    * [MixedReality. 2.1.0. unitypackage。](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [MRTK.HoloLens2. GettingStarted. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [MRTK.HoloLens2. AzureSpatialAnchors. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. 导入资产。

    在 Unity 菜单中，选择 "**资产** > **导入包** > **自定义包 ...** "。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    在导入包 .。。弹出窗口中，选择 " **AzureSpatialAnchors" unitypackage**并单击 "**打开**" 按钮。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    在 "导入 Unity 包" 弹出窗口中，首先确保通过单击 "**全部**" 按钮选择所有资产，然后单击 "**导入**" 按钮导入资产。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    重复上述步骤以导入其余资产包。 完成后，Unity 项目的 "**资产**" 文件夹应该包含这些子文件夹。

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a>创建和准备场景

在本部分中，将通过添加混合现实工具包和某些教程 prototyping 来创建和准备场景。

1. 创建新场景。

    在 Unity 菜单中，选择 "**文件** > "**新场景**"。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    在 Unity 菜单中，选择 "**文件**" > **另存为 ...** "。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    在 "保存场景" 弹出窗口中，导航到项目的 "**场景**" 文件夹，为场景提供一个合适的名称（例如_ASATutorialScene_），然后单击 "**保存**" 按钮保存场景。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    >只要该场景位于项目的 "资产" 文件夹内，你就可以将其保存到任意位置。 但是，若要使项目保持井然有序，通常建议将其保存在项目的场景文件夹中。

2. 添加混合现实工具包。

    在 Unity 菜单中，选择 "**混合现实工具包**" > **添加到场景并配置 ...** "。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    在 "选择 MixedRealityToolkitConfigurationProfile" 弹出窗口中，单击 " **DefaultHoloLens2ConfigurationProfile** "，将其设置为场景的 MRTK 配置文件。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    在 Unity 菜单中，选择 "**文件**" > **保存**"以保存场景。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    >您可以使用键盘快捷方式 CTRL + S （macOS 上的命令 + S）在学习本教程时快速保存场景。

3. 添加教程 prototyping。

    在 "项目" 面板中，导航到 "**资产**" > **MRTK "。AzureSpatialAnchors** > **prototyping**文件夹。 按住 CTRL 按钮（macOS 上的命令）时，请单击 " **ButtonParent**"、" **DebugWindow**" 和 " **ParentAnchor** " 以选择三个 prototyping。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    如果仍选择了三个 prototyping，请将其拖到 "层次结构" 面板中，将它们添加到场景中。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    若要重点关注场景中的对象，可以双击 ParentAnchor 对象，然后再次缩小。

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    >如果您在场景中找到大图标，例如大帧 "t" 图标会分散注意力，则可以通过将<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos 切换</a>到 off 位置来隐藏这些图标。

## <a name="configuring-the-buttons-to-operate-the-scene"></a>配置按钮以操作场景

在本部分中，会将 prototyping 和脚本添加到场景中，以创建一系列按钮，用于演示本地锚点和 Azure 空间锚点在应用程序中的行为方式。

1. 配置 Pressable 按钮 Holo Lens 2 （脚本）组件。

    在 "层次结构" 面板中，展开 " **ButtonParent** " 对象，然后选择名为 " **StartAzureSession**" 的第一个子对象。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    在 "检查器" 面板中，向下滚动到 " **Pressable" 按钮 Holo 镜头2（脚本）** 组件，并通过单击 " **+** " 图标向 "**按下" 按钮**添加一个新的事件侦听器。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    在 "层次结构" 面板中选择 "StartAzureSession" 对象之后，在 "层次结构" 面板中单击 " **ParentAnchor** " 对象，并将其从 "层次结构" 面板中拖放到刚添加的事件侦听器的空 "**无（对象）** " 字段中，使 ParentAnchor 对象侦听此按钮上按下的按钮

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    单击同一事件侦听器的 "**不执行函数**" 下拉列表，然后选择 " **AnchorModuleScript** > **StartAzureSession （）** "，将 StartAzureSession （）函数设置为在此按钮上触发按钮按下事件时触发的操作。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. 配置种不可交互（脚本）组件。

    在 "层次结构" 面板中选择 "StartAzureSession" 对象后，在 "检查器" 面板中，向下滚动到 "**种不可交互（脚本）** " 组件，并重复与上述步骤1中的**OnClick （）** 事件相同的过程。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. 配置剩余按钮

    对于其余的每个按钮，请完成上面的步骤1和步骤2中所述的过程，将函数分配给按下的按钮（）和 OnClick （）事件：

    * 对于**StopAzureSession**对象，请分配**StopAzureSession （）** 函数。
    * 对于**CreateAnchor**对象，分配**CreateAzureAnchor （）** 函数，然后将**ParentAnchor**再次拖动到空的 "**无（游戏对象）** " 字段。
    * 对于 "**开始查找定位点**" 对象，请分配**FindAzureAnchor （）** 函数。
    * 对于 "**删除 Azure 定位**对象" 对象，请分配**DeleteAzureAnchor （）** 函数。
    * 对于 "**删除本地定位点**" 对象，分配**RemoveLocalAnchor （）** 函数，然后将**ParentAnchor**再次拖动到空的 "**无（游戏对象）** " 字段。

4. 将场景连接到 Azure 资源

    在 "层次结构" 面板中，选择 " **ParentAnchor** " 对象，然后在 "检查器" 面板中，向下滚动到 "**空间锚管理器（脚本）** " 组件。

    然后，在 "**凭据**" 部分中，将空间锚定帐户 Id 和密钥粘贴到相应的**空间锚定帐户 Id**和**空间锚定帐户密钥**字段。

    >[!NOTE]
    >在本教程的[先决条件](mrlearning-asa-ch1.md#prerequisites)中，你已创建了空间锚定帐户 Id 和密钥。

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    >请确保保存场景。

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>尝试 Azure 空间锚的基本行为

现在，你的场景已配置为演示 Azure 空间定位点的基本知识，接下来可以部署应用，以便体验 Azure 空间锚亲身。

1. 添加其他所需的功能。

    在 Unity 菜单中，选择 "**编辑** > **项目设置 ...** " 以打开 "播放机设置" 面板。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    在播放机设置面板中，选择 "**播放机**"，然后单击 "**发布设置**"。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    在 "**发布设置**" 中，向下滚动到 "**功能**" 部分，并仔细检查是否已启用在教程开头创建项目时启用的**SpatialPerception**。 然后，启用了**InternetClient**、 **InternetClientServer**、 **PrivateNetworkClientServer**、 **RemovableStorage**、**网络摄像机**和**麦克风**功能。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. 将应用部署到 HoloLens 2。

    >[!TIP]
    >有关如何生成 Unity 项目并将其部署到 HoloLens [2 的提醒](mrlearning-base-ch1.md#build-your-application-to-your-device)，请参阅[初始化项目和首个应用程序](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1)教程，这是[入门教程](mrlearning-base.md)系列中的一部分。

3. 运行应用程序并按照应用程序中的说明进行操作。

    >[!CAUTION]
    >Azure 空间锚点使用 internet 保存和加载定位数据，因此请确保设备已连接到 internet。

    当应用程序在你的设备上运行时，请按照**Azure 空间锚点模块说明**面板上显示的屏幕说明操作。

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a>定位体验

在前面的部分中，已了解 Azure 空间锚的基础知识。 我们使用多维数据集来表示父游戏对象并将其与附加锚点可视化。 在本部分中，你将了解如何通过将整个体验作为 ParentAnchor 对象的子项来定位。

1. 添加火箭启动器体验。

    在 "项目" 面板中，导航到 "**资产**" > **MRTK "。GettingStarted** > **prototyping**文件夹，并选择**火箭 Launcher_Complete** prefab。

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    在仍选择火箭 Launcher_Complete prefab 的情况下，将其拖动到层次结构面板中**ParentAnchor**对象的顶部，使其成为 ParentAnchor 对象的子对象。

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. 重新定位火箭启动器体验。

    将 module**火箭 Launcher_Complete**对象，以便仍公开**ParentAnchor** （多维数据集）。

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    在应用程序中，用户现在可以通过移动多维数据集来重新定位整个火箭启动器体验。

    >[!TIP]
    >有各种用户体验流程可用于重定位体验，包括使用重定位对象（例如本教程中使用的多维数据集）、使用按钮切换环绕体验的边界框、使用位置和旋转gizmos 等。

## <a name="congratulations"></a>祝贺

在本教程中，已了解 Azure 空间锚的基础知识。 本课程提供多个按钮，使你可以浏览启动和停止 Azure 会话所需的各种步骤，以及在单个设备上创建、上传和下载 azure 锚。

在下一课中，您将学习如何将 Azure 定位 Id 保存到 HoloLens 2 以便检索，甚至在重新启动应用程序后，以及如何在多个设备之间传输定位 Id 即可实现空间对齐。

[下一课： 2. 保存、检索和共享 Azure 空间锚](mrlearning-asa-ch2.md)
