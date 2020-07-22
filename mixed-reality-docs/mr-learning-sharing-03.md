---
title: 多用户功能教程 - 3. 连接多个用户
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 56bd4e251d11e39d5495d3fcaf4e3c5fc4e087de
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304812"
---
# <a name="3-connecting-multiple-users"></a>3.连接多个用户

本教程介绍如何将多个用户连接为实时共享体验的一部分。 在本教程结束时，你将能够在多台设备上运行应用，并让每位用户都能实时看到其他用户的头像移动。

## <a name="objectives"></a>目标

* 了解如何在共享体验中连接多个用户

## <a name="preparing-the-scene"></a>准备场景

在本部分，你将通过添加一些教程预制件来准备场景。

在“项目”窗口中导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “预制件”文件夹，然后单击以下预制件并将其拖动到“层次结构”窗口中，从而将其添加到场景中  ：

* NetworkLobby 预制件
* SharedPlayground 预制件

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

在“项目”窗口中导航到“资产” > “MRTK.Tutorials.AzureSpatialAnchors” > “预制件”文件夹，然后单击以下预制件并将其拖动到“层次结构”窗口中，从而将其添加到场景中  ：

* DebugWindow 预制件

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>创建用户预制件

在本部分中，你将创建一个预制件，用于表示共享体验中的用户。

### <a name="1-create-and-configure-the-user"></a>1.创建和配置用户

在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”将空对象添加到场景中，将该对象命名为“PhotonUser”，并按如下所示对其进行配置：

* 请确保将变换位置设置为 X = 0，Y = 0，Z = 0：

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

在“层次结构”窗口中，选择“PhotonUser”对象，然后在检查器窗口中，使用“添加组件”按钮将“Photon 用户(脚本)”组件添加到 PhotonUser 对象：  

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

在检查器窗口中，使用“添加组件”按钮将“通用网络同步(脚本)”组件添加到 PhotonUser 对象，并按如下所示对其进行配置：

* 选中“是用户”复选框

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

在检查器窗口中，使用“添加组件”按钮将“Photon 视图(脚本)”组件添加到 PhotonUser 对象，并按如下所示对其进行配置：

* 向“观察到的组件”字段分配“通用网络同步(脚本)”组件 

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2.创建头像

在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “StandardAssets” > “材料”文件夹，找到 MRTK 材料    。

然后，在“层次结构”窗口中，右键单击 PhotonUser 对象，然后选择“3D 对象” > “球体”来创建一个球体对象作为 PhotonUser 对象的子项，并按如下所示对它进行配置  ：

* 请确保将变换位置设置为 X = 0，Y = 0，Z = 0
* 将变换标度更改为适当的大小，例如 X = 0.15，Y = 0.15，Z = 0.15
* 在“MeshRenderer”>“材料”>“元素 0”字段中，指定 MRTK_Standard_White 材料 

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3.创建预制件

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹：  

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

在“资源”文件夹仍处于选定状态的情况下，单击“层次结构”窗口中的“PhotonUser”对象并将其拖动到“资源”文件夹，以使 PhotonUser 对象成为预制件：  

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

在“层次结构”窗口中，右键单击“PhotonUser”对象，然后选择“删除”将其从场景中删除：

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>配置 PUN 以将用户预制件实例化

在本部分中，你将配置项目以使用在上一部分中创建的 PhotonUser 预制件。

在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.MultiUserCapabilities” > “资源”文件夹。  

在“层次结构”窗口中，展开“NetworkLobby”对象并选择“NetworkRoom”子对象，然后在检查器窗口中，找到“Photon 房间(脚本)”组件，并按如下所示对其进行配置：

* 向“Photon 用户预制件”字段中分配来自“资源”文件夹的“PhotonUser”预制件

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>尝试包含多个用户的体验

如果现在生成 Unity 项目并将其部署到 HoloLens，然后回到 Unity，并在应用运行于 HoloLens 上时进入“游戏”模式，那么当你来回晃动头部 (HoloLens) 时，你将看到 HoloLens 用户头像移动：

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> 要查看提示了解如何生成 Unity 项目并将其部署到 HoloLens 2，可参阅[在 HoloLens 2 上构建应用](mr-learning-base-02.md#building-your-application-to-your-hololens-2)中的说明。

> [!CAUTION]
> 应用需要连接到 Photon，因此请确保计算机/设备已连接到 Internet。

## <a name="congratulations"></a>祝贺

你已成功将项目配置为允许多个用户连接到相同体验并可看到彼此的移动。 在下一教程中，你将实现功能，以使对象的移动也可以在多个设备之间共享。

[下一教程：4.与多个用户共享对象移动](mr-learning-sharing-04.md)
