---
title: Azure 空间锚点教程-2。 保存、检索和共享 Azure 空间锚
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250725"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. 保存、检索和共享 Azure 空间锚

在本教程中，你将了解如何通过将定位点 ID 保存到 HoloLens 2 的存储来跨多个应用会话保存 Azure 空间锚。 你还将了解如何将此定位点 ID 共享到其他设备，以实现多设备锚点对齐。

## <a name="objectives"></a>目标

* 了解如何在应用程序会话之间保存和检索 HoloLens 2 本地磁盘的 Azure 空间定位点 Id
* 了解如何在多设备方案中共享用户之间的 Azure 空间锚点 Id

## <a name="preparing-the-scene"></a>准备场景

在项目窗口中，导航到 "**资产**" > **MRTK "。AzureSpatialAnchors** > **prototyping**文件夹。 按住 CTRL，同时单击**ButtonParent_SaveAnchorId**并**ButtonParent_ShareAnchorId**选择两个 prototyping，然后将其拖动到 "层次结构" 窗口中，将其添加到场景：

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>在应用会话之间保留 Azure 锚点-将定位点 ID 保存到磁盘
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

在本部分中，你将了解如何将 Azure 定位 ID 保存和检索到 HoloLens 2 本地磁盘。 这将允许你在 Azure 中查询不同应用会话间的相同锚 ID，从而允许定位的全息影像位于与上一个应用会话相同的位置。

在 "层次结构" 窗口中，展开包含两个按钮的 " **ButtonParent_SaveAnchorId** " 对象，一个按钮用于将 Azure 定位点 ID 保存到 HoloLens 2 存储，另一个用于从磁盘检索保存的 id：

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

按照前面教程中的 "[配置按钮以操作场景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)说明" 中所述的相同步骤，在两个按钮的每个按钮上配置**Pressable 按钮 Holo Lens 2 （脚本）** 组件和**种不可交互（Script）** 组件：

* 对于**SaveAzureAnchorIdToDisk**对象，请将 AnchorModuleScript > **SaveAzureAnchorIdToDisk （）** 函数。
* 对于**GetAzureAnchorIdFromDisk**对象，请将 AnchorModuleScript > **GetAzureAnchorIdFromDisk （）** 函数。

如果将更新后的应用程序生成到 HoloLens，你现在可以通过保存 Azure 定位点 ID 在应用会话之间保持 Azure 空间锚。 若要对其进行测试，你可以执行以下步骤：

1. 将火箭启动器体验移到所需位置。
2. 启动 Azure 会话。
3. 创建 Azure 定位点（在火箭启动器体验位置创建定位点）。
4. 将 Azure 定位 ID 保存到磁盘。
5. 重新启动应用程序。
6. 从磁盘获取 Azure 定位点（加载刚刚保存的定位点 ID）。
7. 启动 Azure 会话。
8. 查找 Azure 定位点（将火箭启动器体验置于步骤3的位置）。

## <a name="share-azure-anchors-between-multiple-devices"></a>在多个设备之间共享 Azure 锚

在本部分中，你将了解如何在多个设备之间共享 Azure 定位 ID。 这将允许多个设备在 Azure 中查询相同的定位点 ID，从而允许锁定的全息影像。 空间对齐，即在多个设备之间的同一物理位置查看相同的全息影像，这是 HoloLens 2 中本地共享体验的关键所在。

可以通过多种方式在设备之间传输 Azure 锚 Id，包括[多用户功能教程](mrlearning-sharing(photon)-ch1.md)系列中所述的方法。 在此示例中，你将使用简单的 web 服务在设备之间上传和下载定位点 Id。

在 "层次结构" 窗口中，展开包含两个按钮的**ButtonParent_ShareAnchorId**对象;一个按钮，用于将 Azure 定位点 ID 上传到 web 服务器，另一个按钮用于从 web 服务器下载 ID：

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

按照前面教程中的 "[配置按钮以操作场景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)说明" 中所述的相同步骤，在两个按钮的每个按钮上配置**Pressable 按钮 Holo Lens 2 （脚本）** 组件和**种不可交互（Script）** 组件：

* 对于**ShareAzureAnchorIdToNetwork**对象，请将 AnchorModuleScript > **ShareAzureAnchorIdToNetwork （）** 函数。
* 对于**GetAzureAnchorIdFromNetwork**对象，请将 AnchorModuleScript > **GetAzureAnchorIdFromNetwork （）** 函数。

如果将更新后的应用程序生成到两个 HoloLens 设备，你现在可以通过共享 Azure 定位 ID 来实现它们之间的空间对齐。 若要对其进行测试，你可以执行以下步骤：

1. 在 HoloLens 设备1上：将火箭启动器体验移到所需的位置。
2. 在 HoloLens 设备1上：启动 Azure 会话。
3. 在 HoloLens 设备1上：创建 Azure 定位点（在火箭启动器体验位置创建定位点）。
4. 在 HoloLens 设备1上：将 Azure 定位 ID 共享到网络。
5. 在 HoloLens 设备2上：重新启动应用程序。
6. 在 HoloLens 设备2：从网络获取共享的定位点 ID （获取刚刚从 HoloLens 设备1共享的定位点 ID）。
7. 在 HoloLens 设备2上：启动 Azure 会话。
8. 在 HoloLens 设备2上：查找 Azure 定位点（将火箭启动器体验置于步骤3的位置）。

> [!TIP]
> 如果只有一个 HoloLens，则仍可通过重新启动应用程序而不是使用第二个 HoloLens 设备来测试该功能。

## <a name="congratulations"></a>祝贺你

在本教程中，你已了解如何在应用程序会话和应用程序重启之间保留 Azure 空间锚点，方法是将 Azure 空间锚 ID 保存到 HoloLens 上的本地磁盘。 还了解了如何在多个设备之间共享 Azure 空间锚，以实现基本的多用户静态全息图共享体验。

在下一教程中，你将学习如何向用户提供实时反馈。 此反馈将包括有关定位点创建、环境理解质量以及 Azure 会话状态的信息。 如果没有反馈，用户可能不知道锚是否已成功上传到 Azure，无论环境质量是否足以用于创建定位点或当前状态。

[下一课： 3. 显示 Azure 空间锚点反馈](mrlearning-asa-ch3.md)
