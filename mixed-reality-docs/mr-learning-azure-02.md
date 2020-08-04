---
title: Azure 云教程 - 2. 集成 Azure 存储
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现 Azure 表存储和 Azure Blob 存储。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, hololens 2, azure 存储
ms.localizationpriority: high
ms.openlocfilehash: a8d91bc55b3ce73d6e1fb46e5d696d853adcf871
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376469"
---
# <a name="2-integrating-azure-storage"></a>2.集成 Azure 存储

本教程将介绍如何将实体数据保存到 Azure 表存储并将缩略图图像保存到 Azure Blob 存储。 通过此功能，可以将跨会话和设备的带数据（例如 ID、名称、缩略图等）的跟踪对象存储到云并进行检索。

## <a name="objectives"></a>目标

* 了解有关 Azure 存储的基础知识
* 了解如何存储、修改和检索表存储中的数据
* 了解如何在 Blob 存储中存储和删除图像

## <a name="understanding-azure-storage"></a>了解 Azure 存储

Azure 存储是云中的 Microsoft 存储解决方案，可适应多种场景和需求。 它可以大规模扩展，并且开发人员也很容易使用它。 所有服务可以在一个 Azure 存储帐户下使用。 对于我们的用例，我们将使用表存储和 Blob 存储 。

了解有关 [Azure 存储服务](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview)的详细信息。

### <a name="azure-table-storage"></a>Azure 表存储

借助此服务，我们能够以 NoSQL 方式存储数据，在此项目中，我们将使用它来存储跟踪对象的相关信息，例如名称、说明、空间定位点 ID 等。

在演示应用程序的上下文中，你需要两个表，一个用于存储有关项目的信息以及有关经训练模型状态的信息（详见[集成 Azure 自定义视觉](mr-learning-azure-03.md)教程），另一个用于存储有关跟踪对象的信息。

了解有关 [Azure 表存储](https://docs.microsoft.com/azure/storage/tables/table-storage-overview)的详细信息。

### <a name="azure-blob-storage"></a>Azure Blob 存储

此服务允许存储大型二进制文件，你将使用它，将为跟踪对象拍摄的照片存储为缩略图。
对于演示应用程序，需要一个 Blob 容器来存储图像。

了解有关 [Azure Blob 存储](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction)的详细信息。

## <a name="preparing-azure-storage"></a>准备 Azure 存储

要使用 Azure 存储服务，需要一个 Azure 存储帐户。 若要创建存储帐户，请参阅[创建存储帐户](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal)。 若要了解有关存储帐户的详细信息，请参阅 [Azure 存储帐户概述](https://docs.microsoft.com/azure/storage/common/storage-account-overview)。

拥有存储帐户后，可从 Azure 门户检索连接字符串，本课程的下一部分将会用到它。

### <a name="optional-azure-storage-explorer"></a>可选 Azure 存储资源管理器

虽然可以从应用程序内的 UI 查看并验证所有数据更改，但建议安装 [Azure 存储资源管理器](https://azure.microsoft.com/features/storage-explorer/)。 此工具可用于直观地查看 Azure 存储中的数据，在调试和学习时很有帮助。

> [!TIP]
> 若要在 Unity 编辑器中进行测试，可以使用本地模拟器：

> * 在 Windows 10 中，可以使用 [Azure 存储模拟器](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)
> * 在 MacOS/Linux 中，可以使用适用于 Docker 的 [Azurite Docker 映像](https://hub.docker.com/_/microsoft-azure-storage-azurite)

## <a name="preparing-the-scene"></a>准备场景

在“层次结构”窗口中，找到“DataManager”对象并选择它。

![mr-learning-azure](images/mr-learning-azure/tutorial2-section4-step1-1.png)

在“检查器”窗口中，你将看到“DataManager(脚本)”组件是存储所有 Azure 存储相关设置的位置 。 所有相关设置均已设置，只需将“连接字符串”字段替换为从 Azure 门户检索的连接字符串即可。 如果使用本地 Azure 存储模拟器解决方案，则可以保留已提供的连接字符串。

“DataManager(脚本)”负责与 UI 组件上的其他控制器脚本使用的表存储和 Blob 存储进行对话  。

## <a name="writing-and-reading-data-from-azure-table-storage"></a>向 Azure 表存储写入和由其读取数据

一切准备就绪后，就可以创建跟踪对象了。

在 HoloLens 上打开应用程序，单击“设置对象”，然后你会在层次结构中看到 EnterObjectName 对象变为活动状态。 在此菜单中，单击搜索栏，然后键入想要赋予跟踪对象的名称 。 提供名称后，单击“设置对象”按钮。 这将在 Azure 表存储上创建跟踪对象，然后你将看到“对象卡”。

该对象卡是跟踪对象的 UI 表示，并将在本系列教程中多次扮演重要角色。

现在，单击描述文本框并键入“汽车”，然后单击“保存”按钮以保存更改。 停止应用程序，然后重新运行它。

现在，单击“搜索对象”，然后在搜索栏中键入之前创建跟踪对象时使用的名称 。 你将看到从 Azure 表存储中检索出了包含所有数据的“对象卡” 。

可随时关闭“对象卡”和创建新的跟踪对象并编辑其数据。

> [!TIP]
> 如果已安装 [Azure 存储资源管理器](https://azure.microsoft.com/features/storage-explorer/)，则查看对象表，其中将显示创建的跟踪对象 。

## <a name="uploading-and-download-image-from-azure-blob-storage"></a>向 Azure Blob 存储上传和由其下载图像

在本部分，你将使用 Azure Blob 存储上传和下载图像，这些图像将用作跟踪对象的缩略图。

> [!NOTE]
> 在本教程中，应用程序将拍摄照片，以将图像上传到 Blob 存储。 如果在 Unity 编辑器中本地运行此应用程序，请确保已将网络摄像头连接到计算机。

在 HoloLens 上打开应用程序，单击“设置对象”，然后在搜索栏中键入名称“汽车”。 现在，应可看到“对象卡”。单击“摄像头”按钮，系统将指示你进行 AirTap 拍照 。 拍照后，将显示一条消息，通知你正在进行上传，不久后图像应显示在占位符之前的位置。

现在，重新运行该应用程序并搜索跟踪对象，并且以前上传的图像应显示为缩略图。

## <a name="deleting-image-from-azure-blob-storage"></a>从 Azure Blob 存储删除图像

在上一部分，你已将新图像上传到 Azure Blob 存储，在本部分，你将删除跟踪对象的图像缩略图。

在 HoloLens 上打开应用程序，单击“设置对象”，然后在搜索栏中键入名称“汽车”。 现在应该会看到带有缩略图的“对象卡”。单击“删除”按钮 。 你会注意到缩略图图像已替换为占位符图像。

现在，重新运行该应用程序并搜索先前删除的缩略图的跟踪对象，此时应仅显示占位符图像。

## <a name="congratulations"></a>祝贺

本教程介绍了如何使用 Azure 存储服务来保持非结构化数据，例如示例中以缩略图图像的形式存储的云中 HoloLens 2 演示应用程序的跟踪对象和二进制文件 。

下一教程将介绍如何使用 Azure 自定义视觉来检测与跟踪对象关联的图像。

[下一教程：3.集成 Azure 自定义视觉](mr-learning-azure-03.md)
