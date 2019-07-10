---
title: 混合现实捕获
description: 使用混合的现实捕获的信息。
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: mrc，混合现实捕获、 照片、 视频、 照相机、 捕获、 使用情况、 流、 流媒体直播、 演示
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694481"
---
# <a name="mixed-reality-capture"></a>混合现实捕获

HoloLens 为用户提供了混合现实世界与数字世界的体验。 混合的现实捕获 (MRC) 允许您为照片或视频捕获这种体验。 这样可以允许用户以查看全息，正如您看到它们，从而与他人共享体验。 此类视频和照片是从第一人称角度。 对于第三个人的角度来看，使用[spectator 视图](spectator-view.md)。

共享社交圈之间的视频超出了混合的现实捕获的用例。 可以使用视频，以指示其他人如何使用应用程序。 开发人员可以使用视频或静止图像来改进重现步骤和调试应用程序体验。

## <a name="live-streaming-from-hololens"></a>实时传送视频流从 HoloLens

[Windows 10 2018 年 10 月更新](release-notes-october-2018.md)将 Miracast 支持添加到 HoloLens。 选择**Connect**开始菜单以显示为已启用 Miracast 的设备和适配器的选取器底部的按钮。 选择你想要开始流式处理的设备。 完成后，选择**断开连接**底部的开始菜单的按钮。  **连接**并**断开连接**快速操作菜单上也有提供。

[Windows Device Portal](using-the-windows-device-portal.md)并[Microsoft HoloLens 辅助应用程序](https://www.microsoft.com/store/productId/9NBLGGH4QWNX)公开实时传送视频流的开发人员模式下的设备的选项。

[Dynamics 365 远程协助](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist)支持实时传送视频流从 HoloLens 到远程位置中的员工。

## <a name="taking-mixed-reality-captures"></a>采用混合的现实捕获

![单击底部的开始菜单的摄像机图标](images/cameraiconinpins-300px.png)<br>
*单击底部的开始菜单的摄像机图标*

有多种方法来启动混合的现实捕获：
* Cortana 可以使用在所有时间不考虑当前正在运行的应用。 只需输入:"你好，小娜，拍摄一张照片"或"你好，小娜，开始记录。" 若要停止视频，请说"你好，小娜停止录制。"
* 在开始菜单上选择任一**照相机**或**视频**。 使用[敲击](gestures.md#air-tap)以打开内置 MRC 相机 UI。
* 在快速操作菜单上选择任一**照相机**或**视频**以打开内置 MRC 相机 UI。
* 应用程序均可公开使用自定义的混合的现实捕获，或在其自己的 UI [Windows 10 2018 年 10 月更新](release-notes-october-2018.md)，[内置 MRC 摄像头 UI](mixed-reality-capture-for-developers.md)。
* 唯一的 HoloLens: 
    * [Windows Device Portal](using-the-windows-device-portal.md)具有一个混合的现实捕获页面，可用来拍摄照片、 视频、 实时流，并查看捕获。
    * 按这两**调高音量**并**调低音量**按钮同时以拍摄照片，不考虑当前正在运行的应用。
    * 保存**调高音量**并**调低音量**三秒，若要开始录制视频的按钮。 若要停止视频，请点击两者**调高音量**并**调低音量**同时按钮。
* 唯一的沉浸式耳机： 
    * 使用 motion 控制器，存放**Windows**按钮，然后点击**触发器**来拍摄照片。 
    * 使用 motion 控制器，存放**Windows**按钮，然后点击**菜单**按钮开始录制视频。 保存**Windows**按钮，然后点击**触发器**到停止录制视频。
    
>[!NOTE]
>[Windows 10 2018 年 10 月更新](release-notes-october-2018.md)更改布隆和 Windows 按钮的行为方式。 在更新前布隆手势或 Windows 按钮会停止记录。 更新后，布隆手势或 Windows 按钮打开开始菜单 （或快速操作菜单上你是否在应用中）。 在菜单中，选择**停止视频**停止录制。

### <a name="limitations-of-mixed-reality-capture"></a>混合的现实捕获的限制

上 HoloLens，系统将限制为 30 Hz 的呈现速率。 这将创建一些空间用于 MRC 运行，因此应用程序不需要保留的常量预算保留，并还将匹配 （最多到） 30 fps MRC 视频记录帧速率。

视频的最大长度为五分钟。

内置 MRC 摄像头 UI 仅支持单个 MRC 操作一次 （拍摄照片是从录制视频互相排斥）。

### <a name="file-formats"></a>文件格式

混合的现实捕获从 Cortana 语音命令和开始菜单工具创建的文件采用以下格式：

|  type  |  格式  |  扩展  |  分辨率  |  Audio | 
|----------|----------|----------|----------|----------|
|  Photo  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920x1080px<br> （沉浸式耳机） |  不可用 | 
|  视频  |  [MPEG 4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920x1080px<br> 以 30 fps (HoloLens 2)<br> 在 24 每秒帧数 (HoloLens) 1216x684px<br> 以 30 fps （沉浸式耳机） 1632x918px |  48khz 立体声 | 

>[!NOTE]
>如果照片/视频摄像机已被另一个应用程序，同时实时传送视频流，或当系统资源不足时，可以较小的照片和视频的分辨率。

### <a name="video-stabilization"></a>视频防抖动

默认情况下：
* 零延迟视频防抖动时实时传送视频流通过 Miracast 应用。
* 长时间延迟视频防抖动应用于使用内置 MRC 摄像头 UI、 Cortana 语音命令和 Windows Device Portal 捕获的视频。

## <a name="viewing-mixed-reality-captures"></a>查看混合的现实捕获

混合的现实捕获照片和视频保存到设备的"本机照片"文件夹中。 可通过访问它们[照片应用](see-your-photos.md#photos-app)或文件资源管理器。

连接到 HoloLens pc，您还可以使用[Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)或你的电脑的文件资源管理器 ([通过 MTP](release-notes-april-2018.md#new-features-for-hololens))。

如果您在安装[OneDrive 应用](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3)，可开启**照相机上传**和 MRC 照片和视频将同步到 OneDrive 和其他设备使用 OneDrive。

>[!NOTE]
>截至 Windows 10 2018 年 4 月更新，照片应用将无法再上传照片和视频到 OneDrive。

## <a name="see-also"></a>请参阅
* [旁观视图](spectator-view.md)
* [可定位相机](locatable-camera.md)
* [面向开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)
* [查看照片](see-your-photos.md)
* [使用 Windows 设备门户](using-the-windows-device-portal.md)
