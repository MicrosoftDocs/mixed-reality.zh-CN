---
title: 多用户功能教程 - 3. 连接多个用户
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610933"
---
# <a name="2-connecting-multiple-users"></a>2.连接多个用户

本教程介绍如何将多个用户连接为实时共享体验的一部分。 在本教程结束时，你将能够在多个设备上运行应用程序，并让每个用户都能实时看到其他用户的头像移动。

## <a name="objectives"></a>目标

* 了解如何在共享体验中连接多个用户

## <a name="preparing-the-scene"></a>准备场景

在本部分，你将通过添加一些教程预制件来准备场景。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “预制件”文件夹。    在按住 CTRL 按钮的同时，单击“DebugWindow”  、“NetworkLobby”和  “SharedPlayground”，  以便选择这三个预制件：

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

在仍选中了这三个预制件的情况下，将其拖动到“层次结构”窗口中，以将其添加到场景：

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>创建用户预制件

在本部分中，你将创建一个预制件，用于表示共享体验中的用户。

### <a name="1-create-and-configure-the-user"></a>1.创建和配置用户

在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”  将空对象添加到场景中，将该对象命名为“PhotonUser”  ，并按如下所示对其进行配置：

* 请确保将变换位置  设置为 X = 0，Y = 0，Z = 0：

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

在仍选中了“PhotonUser”对象的情况下，在“检查器”窗口中，使用“添加组件”按钮将“Photon 用户(脚本)”组件添加到 PhotonUser 对象：   

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

在“检查器”窗口中，使用“添加组件”  按钮将“通用网络同步(脚本)”  组件添加到 PhotonUser 对象，并按如下所示对其进行配置：

* 选中“是用户”  复选框

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

在“检查器”窗口中，使用“添加组件”  按钮将“Photon 视图(脚本)”  组件添加到 PhotonUser 对象，并按如下所示对其进行配置：

* 向“观察到的组件”  字段中分配“通用网络同步(脚本)”组件

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2.创建头像

在“层次结构”窗口中，右键单击“PhotonUser”  对象，然后选择“3D 对象”   >   “球体”创建一个作为 PhotonUser 对象的子项的球体对象，并按如下所示对其进行配置：

* 请确保将变换位置  设置为 X = 0，Y = 0，Z = 0
* 将变换标度  更改为适当的大小，例如 X = 0.15，Y = 0.15，Z = 0.15

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3.创建预制件

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹：   

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

在“资源”文件夹仍处于选定状态的情况下，单击“层次结构”窗口中的“PhotonUser”对象并将其拖动到“资源”文件夹，以使 PhotonUser 对象成为预制件：   

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

在“层次结构”窗口中，右键单击“PhotonUser”  对象，然后选择“删除”  将其从场景中删除：

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>配置 PUN 以将用户预制件实例化

在本部分中，你将配置项目以使用在上一部分中创建的 PhotonUser 预制件。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。   

在“层次结构”窗口中，展开“NetworkLobby”  对象并选择“NetworkRoom”  子对象，然后在“检查器”窗口中，找到“Photon 房间(脚本)”  组件，并按如下所示对其进行配置：

* 向“Photon 用户预制件”  字段中分配来自“资源”文件夹的“PhotonUser”  预制件

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>尝试包含多个用户的体验

如果现在生成了 Unity 项目并将其部署到 HoloLens，然后返回到 Unity，并且在应用程序运行于 HoloLens 上时按“玩游戏”按钮以进入“游戏”模式，那么，当你来回晃动头部 (HoloLens) 时，你将看到 HoloLens 用户头像移动：

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> 有关如何生成 Unity 项目并将其部署到 HoloLens 2 的提示，可参阅[在设备上生成应用程序](mrlearning-base-ch1.md#build-your-application-to-your-device)中的说明。

> [!CAUTION]
> 应用程序需要连接到 Photon，因此请确保计算机/设备已连接到 Internet。

## <a name="congratulations"></a>祝贺

你已成功将项目配置为允许多个用户连接到相同体验并可看到彼此的移动。 在下一教程中，你将实现功能，以使对象的移动也可以在多个设备之间共享。

[下一教程：2.与多个用户共享对象移动](mrlearning-sharing(photon)-ch3.md)
