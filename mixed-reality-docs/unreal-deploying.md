---
title: 在 Unreal 中部署到设备
description: 将 Unreal 中的设备部署到 HoloLens 2 的指南
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal，Unreal 引擎4，UE4，HoloLens，HoloLens 2，mixed reality，部署到设备，PC，文档
appliesto:
- HoloLens 2
ms.openlocfilehash: 2d0cd67db79c1970695334d826fbbaf0f2f92ec0
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408175"
---
# <a name="deploy-to-device-in-unreal"></a>在 Unreal 中部署到设备

## <a name="overview"></a>概述
可通过两种方法将 Unreal 应用程序部署到 HoloLens 2： 
* 直接从 Unreal 编辑器
* 作为通过设备门户上传的包

这两个选项都要求你将 HoloLens 设置为使用[设备门户](using-the-windows-device-portal.md)进行开发。 

## <a name="deploying-to-device-from-the-unreal-editor"></a>从 Unreal 编辑器部署到设备

1. 单击 "**启动**" 按钮旁的下拉箭头。 最初，HoloLens 设备选项将显示为灰色。

![启动下拉选项](images/unreal/launch-dropdown.png)

2. 打开**设备管理器**。 请注意，HoloLens 不会自动显示在设备列表中。

3. 展开 "**添加未列出的设备**" 部分。

4. 选择 " **HoloLens** " 作为**平台**。

5. 输入设备的 IP 地址和端口信息，用冒号分隔作为设备标识符。 例如，"127.0.0.1： 10080" （通过 USB 连接时）。 使用设备门户的用户名和密码凭据。

6. 点击 "**添加**" 并关闭 "设备管理器"。 
    * 如果出现错误（例如错误的地址、用户名或密码），则会在输出日志中打印一条消息。

![添加未列出的设备](images/unreal/add-unlisted-device.png)

7. 再次单击 "**启动**" 按钮旁的下拉箭头，此时应会看到刚刚添加的 HoloLens 设备。 选择要生成并部署到 HoloLens 的 HoloLens 设备。 

>[!NOTE]
>构建设备可能需要重新编译着色器（特别是在首次运行时），这可能需要一些时间。 不要让设备进入睡眠状态，直到应用程序运行（您可能需要磨损它）。 否则，着色器编译将失败！

## <a name="deploying-to-device-via-device-portal"></a>通过设备门户部署到设备

可以在使用 Unreal 教程系列的入门的最后一部分中找到有关[打包和部署应用](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)的详细说明。
