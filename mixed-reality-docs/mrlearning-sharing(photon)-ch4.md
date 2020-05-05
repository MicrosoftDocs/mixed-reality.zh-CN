---
title: 多用户功能教程 - 5. 将 Azure 空间定位点集成到共享体验中
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604968"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a>4.将 Azure 空间定位点集成到共享体验中

本教程介绍如何将 Azure 空间定位点 (ASA) 集成到共享体验中。 ASA 允许多台设备具有一个对物理环境的共同引用，从而使用户能够在其实际物理位置看到彼此，并看到同一位置中的共享体验。

## <a name="objectives"></a>目标

* 将 ASA 集成到共享体验，以实现多设备空间配准
* 了解 ASA 在本地共享体验上下文中的基本工作原理

## <a name="preparing-the-scene"></a>准备场景

在“层次结构”窗口中，展开“SharedPlayground”  对象，然后展开“TableAnchor”  对象以公开其子对象：

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

在“项目”窗口中，导航到“资产”   > “MRTK.Tutorials.MultiUserCapabilities”   > “预制件”  文件夹，然后将“Buttons”  预制件拖动到“层次结构”窗口中“TableAnchor”  子对象的顶部，以将其作为 TableAnchor 对象的子项添加到场景：

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>配置按钮以操作场景

在本部分中，你将配置一系列按钮事件，用于演示如何使用 Azure 空间定位点实现共享体验中的空间配准。

在“层次结构”窗口中展开“Button”对象，然后选择名为“StartAzureSession”的第一个子按钮对象：  

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

在“检查器”窗口中，找到“可交互(脚本)”  组件，并按如下所示配置 OnClick ()  事件：

* 向“无(对象)”  字段中分配“TableAnchor”  对象
* 从“无函数”  下拉列表中，选择“AnchorModuleScript”   > “StartAzureSession ()”  函数

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

在“层次结构”窗口中，选择名为“CreateAzureAnchor”  的第二个子按钮对象，然后在“检查器”窗口中，找到“可交互(脚本)”  组件，并按如下所示配置 OnClick ()  事件：

* 向“无(对象)”  字段中分配“TableAnchor”  对象
* 从“无函数”  下拉列表中，选择“AnchorModuleScript”   > “CreateAzureAnchor ()”  函数
* 向出现的新“无(游戏对象)”  字段中分配“TableAnchor”  对象

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

在“层次结构”窗口中，选择名为“ShareAzureAnchor”  的第三个子按钮对象，然后在“检查器”窗口中，找到“可交互(脚本)”  组件，并按如下所示配置 OnClick ()  事件：

* 向“无(对象)”  字段中分配“TableAnchor”  对象
* 从“无函数”  下拉列表中，选择“SharingModuleScript”   > “ShareAzureAnchor ()”  函数

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

在“层次结构”窗口中，选择名为“GetAzureAnchor”  的第四个子按钮对象，然后在“检查器”窗口中，找到“可交互(脚本)”  组件，并按如下所示配置 OnClick ()  事件：

* 向“无(对象)”  字段中分配“TableAnchor”  对象
* 从“无函数”  下拉列表中，选择“SharingModuleScript”   > “GetAzureAnchor ()”  函数

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>将场景连接到 Azure 资源

在“层次结构”窗口中，展开“SharedPlayground”  对象，然后选择“TableAnchor”  对象。 然后，在“检查器”窗口中，找到“空间定位点管理器(脚本)”  组件，并使用来自 Azure 空间定位点帐户（该帐户作为本教程系列[必备条件](mrlearning-sharing(photon)-ch1.md#prerequisites)的一部分创建）的凭据配置“凭据”  部分：

* 在“空间定位点帐户 ID”  字段中，粘贴来自你的 Azure 空间定位点帐户的“帐户 ID” 
* 在“空间定位点帐户密钥”  字段中，  粘贴来自你的 Azure 空间定位点帐户的主“访问密钥”或辅助“访问密钥”

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

在仍选中“TableAnchor”  对象的情况下，在“检查器”窗口中，确保已启用所有脚本组件：

* 选中“空间定位点管理器(脚本)”组件旁边的复选框以启用该组件 
* 选中“空间模块脚本(脚本)”组件旁边的复选框以启用该组件 
* 选中“共享模块脚本(脚本)”组件旁边的复选框以启用该组件 

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>尝试带有空间配准的体验

> [!NOTE]
> Azure 空间定位点不能在 Unity 中运行。 因此，若要测试 Azure 空间定位点功能，需将项目部署到至少两个 HoloLens 设备。

如果现在生成 Unity 项目并将其部署到两个 HoloLens 设备，则可以通过共享 Azure 定位点 ID 在设备之间实现空间配准。 若要进行测试，可执行以下步骤：

1. 在 HoloLens 设备 1 上：**启动应用程序**（火箭发射器已实例化并置于台子上）
2. 在 HoloLens 设备 2 上：**启动应用程序**（这两个用户都看到带有火箭启动器的台子，但是，该台子未出现在同一位置，用户头像未出现在用户所在的位置）
3. 在 HoloLens 设备 1 上：按“启动 Azure 会话”  按钮
4. 在 HoloLens 设备 1 上：按“创建 Azure 定位点”  按钮（在 TableAnchor 对象的位置创建定位点，并将定位点信息存储在 Azure 资源中）。
5. 在 HoloLens 设备 1 上：按“共享 Azure 定位点”  按钮（与其他用户实时共享定位点 ID）
6. 在 HoloLens 设备 2 上：按“启动 Azure 会话”  按钮
7. 在 HoloLens 设备 2 上：按“获取 Azure 定位点”  按钮（连接到 Azure 资源以检索共享定位点 ID 的定位点信息，然后将 TableAnchor 对象移到通过 HoloLens 设备 1 创建定位点的位置）

## <a name="congratulations"></a>祝贺

在本教程中，你已了解如何集成 Azure 中强大的空间定位点功能，以在共享体验中为设备实现空间配准。 这也是此教程系列的总结。在此教程系列中，你已学会了如何设置 Photon 帐户、将 Photon 和 PUN 集成到 Unity 应用程序中、配置用户头像和共享的对象，并最终使用 ASA 来为多个参与者实现空间配准。
