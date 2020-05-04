---
title: 多用户功能教程 - 4. 与多个用户共享对象运动
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610635"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a>3.与多个用户共享对象运动

本教程介绍如何共享对象的运动，使共享体验的所有参与者可以展开协作并查看彼此的交互。

## <a name="objectives"></a>目标

* 配置项目以共享对象的运动
* 了解如何生成基本的多用户协作应用程序

## <a name="preparing-the-scene"></a>准备场景

在本部分，你将通过添加教程预制件来准备场景。

在“项目”窗口中，导航到“资产”   > “MRTK.Tutorials.MultiUserCapabilities”   > “预制件”  文件夹，然后将“TableAnchor”  预制件拖动到“层次结构”窗口中“SharedPlayground”  对象的顶部，以将其作为 SharedPlayground 对象的子项添加到场景：

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>配置 PUN 以将对象实例化

在本部分中，你将配置项目以使用在上一部分中创建的 RocketLauncher_Complete_Variant 预制件，并定义要将其实例化的位置。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。   

在“层次结构”窗口中，展开“NetworkLobby”  对象并选择“NetworkRoom”  子对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”  组件，并按如下所示对其进行配置：

* 向“Photon 用户预制件”  字段中分配来自“资源”文件夹的“PhotonUser”  预制件

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

在“NetworkRoom”子对象仍处于选中状态的情况下，在“层次结构”窗口中展开“TableAnchor”对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：   

* 向“火箭发射器位置”  字段中分配来自“层次结构”窗口的“Table”  子对象

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>尝试带有共享对象移动的体验

如果现在生成了 Unity 项目并将其部署到 HoloLens，然后返回到 Unity，并且在应用程序运行于 HoloLens 上时按“玩游戏”按钮以进入“游戏”模式，那么，当你在 HoloLens 中移动对象时，你将看到对象在 Unity 中移动：

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a>祝贺

你已成功配置了项目，因此对象移动已同步，用户可以在其他用户移动对象时看到对象移动。 在下一教程中，你将实现功能，以使共享体验与物理环境相符，使用户在其实际的物理位置中看到彼此，并使对象对所有用户而言都出现在相同的物理位置和旋转角度。

[下一教程：4.将 Azure 空间定位点集成到共享体验中](mrlearning-sharing(photon)-ch4.md)
