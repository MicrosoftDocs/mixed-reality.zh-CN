---
title: 保存和查找文件
description: 如何在 HoloLens 上查找、保存和共享文件。
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 操作方法、文件选取器、文件、照片、视频、图片、OneDrive、存储、文件资源管理器
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524600"
---
# <a name="saving-and-finding-your-files"></a>保存和查找文件

可以通过类似于其他 Windows 10 桌面和移动设备的方式来保存和管理文件:
* 使用文件资源管理器应用程序访问本地文件夹
* 在应用自己的存储中
* 在特殊的已知文件夹 (例如 "视频" 或 "音乐" 库) 中
* 使用包含应用程序和文件选取器 (例如 OneDrive) 的存储服务
* 通过 MTP (媒体传输协议) 支持使用通过 USB 连接到 HoloLens 的台式计算机

## <a name="file-explorer"></a>文件资源管理器

您可以使用文件资源管理器应用程序在 HoloLens 内移动和删除文件。

>[!NOTE]
>如果在文件资源管理器中看不到任何文件, 则 "最近的" 筛选器可能处于活动状态 (时钟图标突出显示在左窗格中)。 若要解决此问题, 请在左窗格中选择 "**此设备**文档" 图标 (在时钟图标下), 或打开菜单并选择 "**此设备**"。

## <a name="files-within-an-app"></a>应用中的文件

如果应用程序将文件保存在你的设备上, 则可以使用该应用程序进行访问。

### <a name="where-are-my-photosvideos"></a>我的照片/视频位于何处？

[混合现实捕获](mixed-reality-capture.md)照片和视频将保存到设备的相机滚动文件夹中。 可以通过[照片应用](see-your-photos.md#photos-app)访问这些。 你可以使用照片应用将你的照片和视频同步到 OneDrive。 你还可以通过[Windows 设备门户](using-the-windows-device-portal.md#mixed-reality-capture)的混合现实捕获页访问你的照片和视频。

### <a name="requesting-files-from-another-app"></a>从其他应用程序请求文件

应用程序可以请求保存文件, 或通过[文件选取](app-model.md#file-pickers)器从另一个应用打开文件。

## <a name="known-folders"></a>已知文件夹

HoloLens 支持多个[已知文件夹](app-model.md#known-folders), 应用程序可以请求访问权限。

## <a name="files-in-a-service"></a>服务中的文件

若要将文件保存到服务 (或从该服务访问文件), 必须安装与该服务关联的应用。 若要将文件保存到 OneDrive 并从 OneDrive 访问文件, 则需要安装[onedrive 应用](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)。

## <a name="mtp-media-transfer-protocol"></a>MTP (媒体传输协议)

类似于其他移动设备, 将 HoloLens 连接到桌面 PC, 并打开电脑上的文件资源管理器, 以便访问你的 HoloLens 库 (照片、视频、文档) 以轻松进行传输。

## <a name="clarifications"></a>澄清

* HoloLens 不支持连接到外部硬盘驱动器或 SD 卡。
* 从 HoloLens 的[Windows 10 2018 年4月版更新 (RS4)](release-notes-april-2018.md)起, hololens 包含用于保存和管理设备上文件的文件资源管理器。 添加文件资源管理器还提供了选择文件选取器 (例如, 将文件保存到设备或 OneDrive) 的功能。
