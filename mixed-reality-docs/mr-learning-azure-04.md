---
title: Azure 云教程 - 4. 集成 Azure 空间定位点
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens, hololens 2, Azure 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: 468ba0d8e9fca85dc266b662f402f5c956dc94bb
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376439"
---
# <a name="4-integrating-azure-spatial-anchors"></a>4.集成 Azure 空间定位点

在本教程中，你将了解如何使用 Azure 空间定位点。 并将跟踪对象的位置存储为 Azure 空间定位点。 然后，你将查询并向用户显示指向该位置的引导箭头。

## <a name="objectives"></a>目标

* 了解 Azure 空间定位点的基础知识。
* 了解如何将场景设置为使用此项目中的 Azure 空间定位点。
* 了解如何集成存储和查询位置。

## <a name="understanding-azure-spatial-anchors"></a>了解 Azure 空间定位点

 Azure 空间定位点是 Azure 云服务系列的一部分，用于保存定位点位置。 可根据定位点 ID 从云中检索保存的定位点位置。 多种平台的设备（如 HoloLens、iOS 和 Android 设备）均可共享和访问此定位点位置。

详细了解 [Azure 空间定位点](https://docs.microsoft.com/azure/spatial-anchors/overview)。

## <a name="preparing-azure-spatial-anchors"></a>准备 Azure 空间定位点

在开始之前，需要在 Azure 门户中创建一个空间定位点资源。
了解如何创建[空间定位点资源](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)。

## <a name="preparing-the-scene"></a>准备场景

本部分介绍如何配置场景并进行必要的更改。

在“项目”窗口中，依次导航至“资产”>“MRTK.Tutorials.AzureCloudServices”>“预制件”>“管理器”

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

在“管理器”文件夹中，将预制件“定位点管理器”拖放到场景层次结构中 。

在层次结构中选择“空间定位点管理器”GameObject，然后在“检查器”部分找到“空间定位点管理器”（脚本） 。 查找“帐户 ID”和“密钥”字段，并添加在前一阶段的先决条件部分创建的凭据。

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

现在，在场景层次结构中找到 Scene Controller 对象并选择它。 此时将显示“场景控制器”检查器。

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

你将注意到“场景控制器”组件的“定位点管理器”字段为空，此时将“定位点管理器”从场景的层次结构拖放到该字段中，并保存场景  。

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a>生成应用并将其部署到 HoloLens 2

Azure 空间定位点不能在 Unity 中运行，因此，若要测试 Azure 空间定位点功能，需将项目部署到设备。

> [!TIP]
> 有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[在 HoloLens 2 上生成应用程序](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>在 HoloLens 2 上运行该应用，并按照应用中的说明进行操作

### <a name="create-an-anchor-to-store-a-location"></a>创建一个用于存储位置的定位点

本部分介绍如何保存对象位置。

运行应用程序，然后在主菜单中单击“设置对象”。

提供要保存的对象的名称，然后单击“设置对象”以继续 。 若要添加有关对象的详细信息，请选择“图像”，并描述此对象。

若要保存位置，请单击“保存位置”

你将看到一个定位点指针，可以移动它并将其放置到要保存的位置上。 之后，你将看到一个“确认”弹出窗口。 如果要确认并保存位置，请单击“是”；否则，可以通过单击“否”并再次选择位置来更改位置 。

单击“是”确认位置后，该位置和定位点 ID 将保存到 Azure 云存储中。 保存后，定位点中会显示对象标记以及该对象的名称。

现在已成功保存对象位置。

### <a name="query-for-finding-an-anchor-location"></a>用于查找定位点位置的查询

成功保存定位点位置后，即可通过在主菜单中选择“搜索对象”来找到定位点位置。

单击“搜索对象”后，将弹出一个新窗口，需要在该窗口中指定要搜索的对象的名称。

输入对象的名称，然后单击“搜索对象”。 如果以前保存了该对象，并且可在数据库中找到该对象，你会得到对象卡，其中包含之前保存的对象的所有详细信息。

现在可通过单击“显示位置”来查找对象。 单击“显示位置”后，系统将从云存储中查询对象地址。

成功检索位置后，将出现一个箭头，引导你找到对象位置。 按照箭头标记操作，直到找到对象的位置。

找到对象后，对象名称将显示在顶部，箭头标记将消失，现在可以单击“对象标记”，查看对象的详细信息。

## <a name="congratulations"></a>祝贺

在本教程中，你了解了 Azure 空间定位点如何在 Hololense 2 上保存和检索对象位置。

最后一个教程将介绍如何使用 Azure 机器人服务为我们的应用程序添加自然语言作为新的交互方法。

[下一教程：5.将 Azure 机器人服务与 LUIS 集成](mr-learning-azure-05.md)
