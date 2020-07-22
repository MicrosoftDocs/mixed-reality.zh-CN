---
title: Azure 空间定位点教程 - 3. 保存、检索和共享 Azure 空间定位点
description: 完成本课程可以了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 25676404a71daf41b6a5c7587fa9bed95ab813f6
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304168"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a>3.保存、检索和共享 Azure 空间定位点

本教程将介绍如何通过将定位点 ID 保存到 HoloLens 2 的存储，来保存多个应用会话中的 Azure 空间定位点。 此外，介绍如何与其他设备共享此定位点 ID，以便在多个设备上对齐定位点。

## <a name="objectives"></a>目标

* 了解如何在多个应用会话之间实现空间对齐。
* 了解如何在多台设备之间实现空间对齐。

## <a name="preparing-the-scene"></a>准备场景

在“层次结构”窗口中，展开“ButtonParent”对象。 选择最后四个子按钮对象。 在“检查器”窗口中，选中“名称”字段旁的复选框以使所有对象处于活动状态。

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-1.png)

在“层次结构”窗口中，选择“ButtonParent”对象。 然后在“检查器”窗口中，找到 GridObjectCollection 组件并单击“更新集合”按钮，以更新所有 ButtonParent 对象的子对象的位置  。

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a>在应用会话之间保留 Azure 空间定位点

本部分介绍如何在 HoloLens 2 本地磁盘中保存以及从中检索 Azure 空间定位点 ID。 通过这些操作，你可以在 Azure 中查询不同应用会话中的同一定位点 ID。 它使定位的全息影像能够位于上一个应用会话中的相同位置。

在“层次结构”窗口中，展开“ButtonParent”对象并找到名为 SaveAzureAnchorIdToDisk 和 GetAzureAnchorIdFromDisk 的两个按钮  ：

![mr-learning-asa](images/mr-learning-asa/asa-03-section2-step1-1.png)

遵循上一篇教程的[配置按钮以操作场景](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene)说明中的相同步骤，在这两个按钮中的每个按钮上配置“可交互(脚本)”组件：

* 对于“SaveAzureAnchorIdToDisk”按钮对象，请分配“AnchorModuleScript”>“SaveAzureAnchorIdToDisk ()”函数。 
* 对于“GetAzureAnchorIdFromDisk”按钮对象，请分配“AnchorModuleScript”>“GetAzureAnchorIdFromDisk ()”函数。 

如果在 HoloLens 中生成更新的应用，则现在可以通过保存 Azure 定位点 ID 在不同的应用会话中保留 Azure 空间定位点。 若要进行测试，可执行以下步骤：

1. 将“漫游者探测器”移到所需位置
2. 启动 Azure 会话
3. 创建 Azure 定位点（在“漫游者探测器”位置创建定位点）
4. 将 Azure 定位点 ID 保存到磁盘
5. 重启应用
6. 从磁盘中获取 Azure 定位点（加载刚刚保存的定位点 ID）
7. 启动 Azure 会话
8. 查找 Azure 定位点（将“漫游者探测器”定位到步骤 3 所述的位置）

> [!NOTE]
> 若要完全重启应用，在退出沉浸式应用视图之后，需要先关闭混合现实主页中的应用窗口，然后从“开始”菜单重新启动应用。 如需更多详细信息，可以参阅[在 HoloLens 上使用应用](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens)文档。

## <a name="sharing-azure-spatial-anchors-between-devices"></a>在设备之间共享 Azure 空间定位点

本部分介绍如何在多个设备之间共享 Azure 定位点 ID。 这样，多个设备便可以在 Azure 中查询同一个定位点 ID，从而可在空间上对齐定位点定的全息影像。 空间对齐（即，在多个设备之间的同一物理位置查看相同的全息影像）是 HoloLens 2 中本地共享体验的关键所在。

可以通过多种方法在设备之间转移 Azure 定位点 ID，包括[多用户功能教程](mr-learning-sharing-02.md)系列中所述的方法。 此示例将使用一个简单的 Web 服务在设备之间上传和下载定位点 ID。

在“层次结构”窗口中，展开“ButtonParent”对象。   找到名为 ShareAzureAnchorIdToNetwork 和 GetAzureAnchorIdFromNetwork 的两个按钮 ：

![mr-learning-asa](images/mr-learning-asa/asa-03-section3-step1-1.png)

遵循上一篇教程的[配置按钮以操作场景](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene)说明中的相同步骤，在这两个按钮中的每个按钮上配置“可交互(脚本)”组件：

* 对于“ShareAzureAnchorIdToNetwork”对象，请分配“AnchorModuleScript”>“ShareAzureAnchorIdToNetwork ()”函数。 
* 对于“GetAzureAnchorIdFromNetwork”对象，请分配“AnchorModuleScript”>“GetAzureAnchorIdFromNetwork ()”函数。 

如果在两个 HoloLens 设备上生成更新的应用，则现在可以通过共享 Azure 定位点 ID 来实现空间对齐。 若要进行测试，可执行以下步骤：

1. 在 HoloLens 设备 1 上：将“漫游者探测器”移到所需位置。
2. 在 HoloLens 设备 1 上：启动 Azure 会话。
3. 在 HoloLens 设备 1 上：创建 Azure 定位点（在“漫游者探测器”位置创建定位点）。
4. 在 HoloLens 设备 1 上：在网络中共享 Azure 定位点 ID。
5. 在 HoloLens 设备 2 上：启动应用。
6. 在 HoloLens 设备 2 上：从网络中获取共享的定位点 ID（提取刚刚从 HoloLens 设备 1 共享的定位点 ID）。
7. 在 HoloLens 设备 2 上：启动 Azure 会话。
8. 在 HoloLens 设备 2 上：查找 Azure 定位点（将“漫游者探测器”定位到步骤 3 所述的位置）。

> [!TIP]
> 如果只有一个 HoloLens 设备，仍可以通过重启应用来测试该功能，而无需使用另一个 HoloLens 设备。

## <a name="congratulations"></a>祝贺

在本教程中，你已了解如何通过将 Azure 空间定位点 ID 保存到 HoloLens 上的本地磁盘，在不同的应用会话中以及每次重启应用后保留 Azure 空间定位点。 此外，你还了解了如何在基本多用户静态全息影像共享体验中的多个设备之间共享 Azure 空间定位点。

下一篇教程将会介绍如何为用户提供实时反馈。 此反馈包括有关定位点的创建、环境质量识别以及 Azure 会话状态的信息。 如果没有反馈，用户可能不知道某个定位点是否已成功上传到 Azure，而不管环境质量是足以创建定位点还是处于当前状态。

[下一教程：4.显示 Azure 空间定位点反馈](mr-learning-asa-04.md)
