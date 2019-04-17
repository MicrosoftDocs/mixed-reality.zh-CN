---
title: 保存和查找文件
description: 如何查找、 保存和共享在 HoloLens 上的文件。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 操作说明、 文件选取器、 文件、 照片、 视频、 图片、 OneDrive、 存储、 文件资源管理器
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592522"
---
# <a name="saving-and-finding-your-files"></a>保存和查找文件

文件可以保存和管理在类似于其他 Windows 10 桌面版和移动设备的方式：
* 使用文件资源管理器应用访问本地文件夹
* 应用自己的存储中
* 在一个特殊的已知文件夹 （如视频或音乐库）
* 使用存储服务，包括 （例如 OneDrive) 应用程序和文件选取器
* 使用台式计算机连接到你通过 USB、 HoloLens 通过 MTP （媒体传输协议） 支持

## <a name="file-explorer"></a>文件资源管理器

文件资源管理器应用可用于移动和删除文件和 HoloLens。

>[!NOTE]
>如果看不到文件资源管理器中的任何文件，则"最近"筛选器可能处于活动状态 （时钟图标在左窗格中将突出显示）。 若要解决此问题，请选择**此设备**文档 （时钟图标），下方的左窗格中的图标或打开的菜单并选择**此设备**。

## <a name="files-within-an-app"></a>应用程序中的文件

如果应用程序将保存你的设备上的文件，您可以使用该应用程序对其进行访问。

### <a name="where-are-my-photosvideos"></a>我的照片/视频在哪里？

[混合现实捕获](mixed-reality-capture.md)照片和视频保存到设备的本机照片文件夹。 可通过访问它们[照片应用](see-your-photos.md#photos-app)。 照片应用可用于同步你的照片和视频到 OneDrive。 您还可以访问你的照片和视频通过的混合现实捕获页[Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)。

### <a name="requesting-files-from-another-app"></a>从另一个应用程序请求文件

应用程序可以请求保存文件或从通过另一个应用打开文件[文件选取器](app-model.md#file-pickers)。

## <a name="known-folders"></a>已知的文件夹

HoloLens 支持多种[已知文件夹](app-model.md#known-folders)应用程序可以请求访问权限。

## <a name="files-in-a-service"></a>在服务中的文件

若要保存到文件 （或访问中的文件） 服务，与服务关联的应用必须在安装。 为了将文件保存到和从 OneDrive 访问文件，你将需要安装[OneDrive 应用](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)。

## <a name="mtp-media-transfer-protocol"></a>MTP （媒体传输协议）

类似于其他移动设备连接到您的桌面 PC 的 HoloLens 和打开文件资源管理器来访问你的 HoloLens 库 （照片、 视频、 文档） 在 PC 上轻松传送。

## <a name="clarifications"></a>说明

* HoloLens 不支持连接到外部硬盘或 SD 卡。
* 在[Windows 10 2018 年 4 月更新 (RS4) HoloLens](release-notes-april-2018.md)，HoloLens 包括用于保存和管理设备的文件的文件资源管理器。 添加的文件资源管理器还提供了可选择文件选取器 （例如，保存到你的设备或 OneDrive 的文件）。
