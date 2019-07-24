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
# <a name="saving-and-finding-your-files"></a><span data-ttu-id="3cdb0-104">保存和查找文件</span><span class="sxs-lookup"><span data-stu-id="3cdb0-104">Saving and finding your files</span></span>

<span data-ttu-id="3cdb0-105">可以通过类似于其他 Windows 10 桌面和移动设备的方式来保存和管理文件:</span><span class="sxs-lookup"><span data-stu-id="3cdb0-105">Files can be saved and managed in a similar manner to other Windows 10 Desktop and Mobile devices:</span></span>
* <span data-ttu-id="3cdb0-106">使用文件资源管理器应用程序访问本地文件夹</span><span class="sxs-lookup"><span data-stu-id="3cdb0-106">Using the File Explorer app to access local folders</span></span>
* <span data-ttu-id="3cdb0-107">在应用自己的存储中</span><span class="sxs-lookup"><span data-stu-id="3cdb0-107">Within an app's own storage</span></span>
* <span data-ttu-id="3cdb0-108">在特殊的已知文件夹 (例如 "视频" 或 "音乐" 库) 中</span><span class="sxs-lookup"><span data-stu-id="3cdb0-108">In a special known folder (such as the video or music library)</span></span>
* <span data-ttu-id="3cdb0-109">使用包含应用程序和文件选取器 (例如 OneDrive) 的存储服务</span><span class="sxs-lookup"><span data-stu-id="3cdb0-109">Using a storage service that includes an app and file picker (such as OneDrive)</span></span>
* <span data-ttu-id="3cdb0-110">通过 MTP (媒体传输协议) 支持使用通过 USB 连接到 HoloLens 的台式计算机</span><span class="sxs-lookup"><span data-stu-id="3cdb0-110">Using a desktop PC connected to your HoloLens via USB, via MTP (Media Transfer Protocol) support</span></span>

## <a name="file-explorer"></a><span data-ttu-id="3cdb0-111">文件资源管理器</span><span class="sxs-lookup"><span data-stu-id="3cdb0-111">File Explorer</span></span>

<span data-ttu-id="3cdb0-112">您可以使用文件资源管理器应用程序在 HoloLens 内移动和删除文件。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-112">You can use the File Explorer app to move and delete files from within HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="3cdb0-113">如果在文件资源管理器中看不到任何文件, 则 "最近的" 筛选器可能处于活动状态 (时钟图标突出显示在左窗格中)。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-113">If you don’t see any files in File Explorer, the "Recent" filter may be active (clock icon is highlighted in left pane).</span></span> <span data-ttu-id="3cdb0-114">若要解决此问题, 请在左窗格中选择 "**此设备**文档" 图标 (在时钟图标下), 或打开菜单并选择 "**此设备**"。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-114">To fix this, select the **This Device** document icon in the left pane (beneath the clock icon), or open the menu and select **This Device**.</span></span>

## <a name="files-within-an-app"></a><span data-ttu-id="3cdb0-115">应用中的文件</span><span class="sxs-lookup"><span data-stu-id="3cdb0-115">Files within an app</span></span>

<span data-ttu-id="3cdb0-116">如果应用程序将文件保存在你的设备上, 则可以使用该应用程序进行访问。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-116">If an application saves files on your device, you can use that application to access them.</span></span>

### <a name="where-are-my-photosvideos"></a><span data-ttu-id="3cdb0-117">我的照片/视频位于何处？</span><span class="sxs-lookup"><span data-stu-id="3cdb0-117">Where are my photos/videos?</span></span>

<span data-ttu-id="3cdb0-118">[混合现实捕获](mixed-reality-capture.md)照片和视频将保存到设备的相机滚动文件夹中。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-118">[Mixed reality capture](mixed-reality-capture.md) photos and videos are saved to the device's Camera Roll folder.</span></span> <span data-ttu-id="3cdb0-119">可以通过[照片应用](see-your-photos.md#photos-app)访问这些。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-119">These can be accessed via the [Photos app](see-your-photos.md#photos-app).</span></span> <span data-ttu-id="3cdb0-120">你可以使用照片应用将你的照片和视频同步到 OneDrive。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-120">You can use the Photos app to sync your photos and videos to OneDrive.</span></span> <span data-ttu-id="3cdb0-121">你还可以通过[Windows 设备门户](using-the-windows-device-portal.md#mixed-reality-capture)的混合现实捕获页访问你的照片和视频。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-121">You can also access your photos and videos via the Mixed Reality Capture page of the [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).</span></span>

### <a name="requesting-files-from-another-app"></a><span data-ttu-id="3cdb0-122">从其他应用程序请求文件</span><span class="sxs-lookup"><span data-stu-id="3cdb0-122">Requesting files from another app</span></span>

<span data-ttu-id="3cdb0-123">应用程序可以请求保存文件, 或通过[文件选取](app-model.md#file-pickers)器从另一个应用打开文件。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-123">An application can request to save a file or open a file from another app via [file pickers](app-model.md#file-pickers).</span></span>

## <a name="known-folders"></a><span data-ttu-id="3cdb0-124">已知文件夹</span><span class="sxs-lookup"><span data-stu-id="3cdb0-124">Known folders</span></span>

<span data-ttu-id="3cdb0-125">HoloLens 支持多个[已知文件夹](app-model.md#known-folders), 应用程序可以请求访问权限。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-125">HoloLens supports a number of [known folders](app-model.md#known-folders) that apps can request permission to access.</span></span>

## <a name="files-in-a-service"></a><span data-ttu-id="3cdb0-126">服务中的文件</span><span class="sxs-lookup"><span data-stu-id="3cdb0-126">Files in a service</span></span>

<span data-ttu-id="3cdb0-127">若要将文件保存到服务 (或从该服务访问文件), 必须安装与该服务关联的应用。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-127">To save a file to (or access files from) a service, the app associated with the service has to be installed.</span></span> <span data-ttu-id="3cdb0-128">若要将文件保存到 OneDrive 并从 OneDrive 访问文件, 则需要安装[onedrive 应用](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-128">In order to save files to and access files from OneDrive, you will need to install the [OneDrive app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).</span></span>

## <a name="mtp-media-transfer-protocol"></a><span data-ttu-id="3cdb0-129">MTP (媒体传输协议)</span><span class="sxs-lookup"><span data-stu-id="3cdb0-129">MTP (Media Transfer Protocol)</span></span>

<span data-ttu-id="3cdb0-130">类似于其他移动设备, 将 HoloLens 连接到桌面 PC, 并打开电脑上的文件资源管理器, 以便访问你的 HoloLens 库 (照片、视频、文档) 以轻松进行传输。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-130">Similar to other mobile devices, connect HoloLens to your desktop PC and open File Explorer on the PC to access your HoloLens libraries (photos, videos, documents) for easy transfer.</span></span>

## <a name="clarifications"></a><span data-ttu-id="3cdb0-131">澄清</span><span class="sxs-lookup"><span data-stu-id="3cdb0-131">Clarifications</span></span>

* <span data-ttu-id="3cdb0-132">HoloLens 不支持连接到外部硬盘驱动器或 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-132">HoloLens does not support connecting to external hard drives or SD cards.</span></span>
* <span data-ttu-id="3cdb0-133">从 HoloLens 的[Windows 10 2018 年4月版更新 (RS4)](release-notes-april-2018.md)起, hololens 包含用于保存和管理设备上文件的文件资源管理器。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-133">As of the [Windows 10 April 2018 Update (RS4) for HoloLens](release-notes-april-2018.md), HoloLens includes File Explorer for saving and managing files on-device.</span></span> <span data-ttu-id="3cdb0-134">添加文件资源管理器还提供了选择文件选取器 (例如, 将文件保存到设备或 OneDrive) 的功能。</span><span class="sxs-lookup"><span data-stu-id="3cdb0-134">The addition of File Explorer also gives you the ability to choose your file picker (for example, saving a file to your device or to OneDrive).</span></span>
