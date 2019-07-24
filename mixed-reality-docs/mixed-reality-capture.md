---
title: 混合现实捕获
description: 有关使用混合现实捕获的信息。
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: mrc, 混合现实捕获, 照片, 视频, 照相机, 捕获, 使用, 流, livestream, 演示
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694481"
---
# <a name="mixed-reality-capture"></a>混合现实捕获

HoloLens 为用户提供了与数字世界混合现实世界的经验。 混合现实捕获 (MRC) 允许您以照片或视频形式捕获该体验。 这使你可以与他人共享体验, 方法是允许他们在你查看全息影像时查看它们。 此类视频和照片来自第一个用户的观点。 对于第三人的观点, 请使用[spectator 视图](spectator-view.md)。

混合现实捕获的用例不会在社交圈中共享视频。 视频可用于指示他人使用应用。 开发人员可以使用视频或静止图像来改进重现步骤并调试应用体验。

## <a name="live-streaming-from-hololens"></a>HoloLens 的实时流式处理

[Windows 10 十月2018更新](release-notes-october-2018.md)将 Miracast 支持添加到 HoloLens。 选择 "开始" 菜单底部的 "**连接**" 按钮, 为启用了 Miracast 的设备和适配器打开选取器。 选择要开始流式传输的设备。 完成后, 选择 "开始" 菜单底部的 "**断开连接**" 按钮。  "快速操作" 菜单上还提供了 "连接" 和 "**断开** **连接**"。

[Windows 设备门户](using-the-windows-device-portal.md)和[Microsoft HoloLens 辅助应用](https://www.microsoft.com/store/productId/9NBLGGH4QWNX)公开了处于开发人员模式下的设备的实时流式处理选项。

[Dynamics 365 远程协助](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist)支持从 HoloLens 向远程位置的员工实时传输视频。

## <a name="taking-mixed-reality-captures"></a>采用混合现实捕获

![单击 "开始" 菜单底部的相机图标](images/cameraiconinpins-300px.png)<br>
*单击 "开始" 菜单底部的相机图标*

可以通过多种方式启动混合现实捕获:
* 不管当前正在运行的应用, Cortana 始终都可以使用。 只需说 "你好 Cortana, 拍摄照片" 或 "你好 Cortana, 开始录制"。 若要停止视频, 请说 "你好 Cortana, 停止录制"。
* 在 "开始" 菜单上, 选择 "**照相机**" 或 "**视频**"。 使用 "[点击](gestures.md#air-tap)" 打开内置的 "MRC 相机" UI。
* 在 "快速操作" 菜单上, 选择 "**照相机**" 或 "**视频**" 以打开内置的 "MRC 相机" UI。
* 应用程序可以使用自定义的或, 使用自定义的或 (从[Windows 10 年10月2018更新](release-notes-october-2018.md)内置的[MRC 照相机 UI](mixed-reality-capture-for-developers.md)) 公开自己的混合现实捕获的 ui。
* HoloLens 独有: 
    * [Windows 设备门户](using-the-windows-device-portal.md)具有混合现实捕获页面, 可用于拍摄照片、视频、实时流和查看捕获。
    * 同时按**向上**键和**向下移动**按钮以拍摄照片, 而不考虑当前正在运行的应用程序。
    * 将**音量调高**和**调低**按钮三秒钟, 开始录制视频。 若要停止视频, 请同时点击 "**音量调高**" 和 "调**低音量**" 按钮。
* 沉浸式耳机独有: 
    * 使用运动控制器, 按住 " **Windows** " 按钮, 然后点击**触发器**来拍照。 
    * 使用运动控制器, 按住 " **Windows** " 按钮, 然后点击 "**菜单**" 按钮以开始录制视频。 按住**Windows**按钮, 然后点击**触发器**以停止录制视频。
    
>[!NOTE]
>[Windows 10 2018 10 月版更新](release-notes-october-2018.md)会更改布隆和 Windows 按钮的行为方式。 更新之前, 布隆手势或 Windows 按钮将停止记录。 更新之后, 布隆手势或 Windows 按钮将打开 "开始" 菜单 (如果你在应用中, 则打开 "快速操作" 菜单)。 在菜单中, 选择 "**停止视频**" 以停止录制。

### <a name="limitations-of-mixed-reality-capture"></a>混合现实捕获的限制

在 HoloLens 上, 系统会将呈现速率限制为30Hz。 这会为 MRC 创建一些空间, 以使该应用无需保留固定预算预留, 同时还可匹配 (最多) 30fps 的 MRC 视频记录的帧速率。

视频的最大长度为5分钟。

内置的 MRC 照相机 UI 一次仅支持一次 MRC 操作 (拍摄视频与记录视频是互斥的)。

### <a name="file-formats"></a>文件格式

混合现实从 Cortana 中捕获语音命令和 "开始" 菜单工具创建以下格式的文件:

|  type  |  格式  |  扩展  |  分辨率  |  Audio | 
|----------|----------|----------|----------|----------|
|  Photo  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920x1080px (沉浸式耳机) |  不可用 | 
|  视频  |  [MPEG-2](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  30fps 上的 1920x1080px (HoloLens 2)<br> 24fps 上的 1216x684px (HoloLens)<br> 30fps 上的 1632x918px (沉浸式耳机) |  48kHz 立体声 | 

>[!NOTE]
>如果照片/视频相机已被其他应用程序使用、实时流式处理或系统资源不足, 则照片和视频的分辨率会更小。

### <a name="video-stabilization"></a>视频抖动

默认情况下:
* 当通过 Miracast 实时传送视频流时, 将应用零延迟视频稳定性。
* 长时间延迟视频稳定性适用于使用内置 MRC 相机 UI、Cortana 语音命令和 Windows 设备门户捕获的视频。

## <a name="viewing-mixed-reality-captures"></a>查看混合现实捕获

混合现实捕获照片和视频保存到设备的 "相机卷筒" 文件夹中。 可以通过[照片应用程序](see-your-photos.md#photos-app)或文件资源管理器访问这些。

在连接到 HoloLens 的 PC 上, 还可以使用[Windows 设备门户](using-the-windows-device-portal.md#mixed-reality-capture)或电脑的文件资源管理器 ([通过 MTP](release-notes-april-2018.md#new-features-for-hololens))。

如果你安装了[OneDrive 应用](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), 则可以启用**相机上传,** 并且你的 MRC 照片和视频将使用 onedrive 同步到 onedrive 和其他设备。

>[!NOTE]
>从 Windows 10 2018 年4月的更新中, 照片应用不再将您的照片和视频上传到 OneDrive。

## <a name="see-also"></a>请参阅
* [旁观视图](spectator-view.md)
* [可定位相机](locatable-camera.md)
* [面向开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)
* [查看照片](see-your-photos.md)
* [使用 Windows 设备门户](using-the-windows-device-portal.md)
