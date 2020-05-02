---
title: Azure 空间定位点教程 - 2. 保存、检索和共享 Azure 空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362008"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2.保存、检索和共享 Azure 空间定位点

本教程将介绍如何通过将定位点 ID 保存到 HoloLens 2 的存储，来保存多个应用会话中的 Azure 空间定位点。 此外，介绍如何与其他设备共享此定位点 ID，以便在多个设备上对齐定位点。

## <a name="objectives"></a>目标

* 了解如何在 HoloLens 2 本地磁盘中保存以及从中检索 Azure 空间定位点 ID，以便在不同的应用会话中持久保留这些 ID。
* 了解如何在多设备方案中的用户之间共享 Azure 空间定位点 ID

## <a name="preparing-the-scene"></a>准备场景

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹。    在按住 CTRL 键的同时单击“ButtonParent_SaveAnchorId”和“ButtonParent_ShareAnchorId”以选择这两个预制件，然后将其拖放到“层次结构”窗口，以将其添加到场景中：  

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>在不同的应用会话中保留 Azure 定位点 - 将定位点 ID 保存到磁盘
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

本部分介绍如何在 HoloLens 2 本地磁盘中保存以及从中检索 Azure 空间定位点 ID。 这样，你便可以在 Azure 中查询不同应用会话使用的同一定位点 ID，使定位点定的全息影像定位在上一个应用会话中所处的同一位置。

在“层次结构”窗口中展开“ButtonParent_SaveAnchorId”对象，该对象包含两个按钮，一个按钮用于将 Azure 定位点 ID 保存到 HoloLens 2 存储，另一个按钮用于从磁盘中检索保存的 ID： 

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

遵循上一篇教程的[配置按钮以操作场景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)说明中的相同步骤，在这两个按钮中的每个按钮上配置“可按按钮 Holo Lens 2 (脚本)”组件“可交互(脚本)”组件：  

* 对于“SaveAzureAnchorIdToDisk”对象，请分配“AnchorModuleScript”>“SaveAzureAnchorIdToDisk ()”函数。  
* 对于“GetAzureAnchorIdFromDisk”对象，请分配“AnchorModuleScript”>“GetAzureAnchorIdFromDisk ()”函数。  

如果在 HoloLens 中生成更新的应用程序，则现在可以通过保存 Azure 定位点 ID 在不同的应用会话中保留 Azure 空间定位点。 若要进行测试，可执行以下步骤：

1. 将“火箭发射器”体验移到所需位置。
2. 启动 Azure 会话。
3. 创建 Azure 定位点（在“火箭发射器”体验位置创建定位点）。
4. 将 Azure 定位点 ID 保存到磁盘。
5. 重启应用程序。
6. 从磁盘中获取 Azure 定位点（加载刚刚保存的定位点 ID）。
7. 启动 Azure 会话。
8. 查找 Azure 定位点（将“火箭发射器”体验定位在步骤 3 所述的位置）。

> [!NOTE]
> 若要完全重启应用程序，在退出沉浸式应用视图之后，需要先关闭混合现实主页中的应用窗口，然后从“开始”菜单重新启动应用程序。 如需更多详细信息，可以参阅[在 HoloLens 上使用应用](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)文档。

## <a name="share-azure-anchors-between-multiple-devices"></a>在多个设备之间共享 Azure 定位点

本部分介绍如何在多个设备之间共享 Azure 定位点 ID。 这样，多个设备便可以在 Azure 中查询同一个定位点 ID，从而可在空间上对齐定位点定的全息影像。 空间对齐（即，在多个设备之间的同一物理位置查看相同的全息影像）是 HoloLens 2 中本地共享体验的关键所在。

可以通过多种方法在设备之间转移 Azure 定位点 ID，包括[多用户功能教程](mrlearning-sharing(photon)-ch1.md)系列中所述的方法。 此示例将使用一个简单的 Web 服务在设备之间上传和下载定位点 ID。

在“层次结构”窗口中展开“ButtonParent_ShareAnchorId”对象，该对象包含两个按钮，一个按钮用于将 Azure 定位点 ID 上传到 Web 服务器，另一个按钮用于从 Web 服务器下载该 ID： 

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

遵循上一篇教程的[配置按钮以操作场景](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene)说明中的相同步骤，在这两个按钮中的每个按钮上配置“可按按钮 Holo Lens 2 (脚本)”组件“可交互(脚本)”组件：  

* 对于“ShareAzureAnchorIdToNetwork”对象，请分配“AnchorModuleScript”>“ShareAzureAnchorIdToNetwork ()”函数。  
* 对于“GetAzureAnchorIdFromNetwork”对象，请分配“AnchorModuleScript”>“GetAzureAnchorIdFromNetwork ()”函数。  

如果在两个 HoloLens 设备上生成更新的应用程序，则现在可以通过共享 Azure 定位点 ID 来实现设备之间的空间对齐。 若要进行测试，可执行以下步骤：

1. 在 HoloLens 设备 1 上：将“火箭发射器”体验移到所需位置。
2. 在 HoloLens 设备 1 上：启动 Azure 会话。
3. 在 HoloLens 设备 1 上：创建 Azure 定位点（在“火箭发射器”体验位置创建定位点）。
4. 在 HoloLens 设备 1 上：在网络中共享 Azure 定位点 ID。
5. 在 HoloLens 设备 2 上：启动应用程序。
6. 在 HoloLens 设备 2 上：从网络中获取共享的定位点 ID（提取刚刚从 HoloLens 设备 1 共享的定位点 ID）。
7. 在 HoloLens 设备 2 上：启动 Azure 会话。
8. 在 HoloLens 设备 2 上：查找 Azure 定位点（将“火箭发射器”体验定位在步骤 3 所述的位置）。

> [!TIP]
> 如果只有一个 HoloLens 设备，仍可以通过重启应用程序来测试该功能，而无需使用另一个 HoloLens 设备。

## <a name="congratulations"></a>祝贺

在本教程中，你已了解如何通过将 Azure 空间定位点 ID 保存到 HoloLens 上的本地磁盘，在不同的应用程序会话中以及每次重启应用程序后保留 Azure 空间定位点。 此外，你还了解了如何在基本多用户静态全息影像共享体验中的多个设备之间共享 Azure 空间定位点。

下一篇教程将会介绍如何为用户提供实时反馈。 此反馈包括有关定位点的创建、环境质量识别以及 Azure 会话状态的信息。 如果没有反馈，用户可能不知道某个定位点是否已成功上传到 Azure，而不管环境质量是足以创建定位点还是处于当前状态。

[下一课：3.显示 Azure 空间定位点反馈](mrlearning-asa-ch3.md)
