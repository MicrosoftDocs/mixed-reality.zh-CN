---
title: 发行说明-2019 年 5
description: HoloLens 和 Windows Mixed Reality 发行说明适用于 Windows 10 2019年可能会更新 (也称为 19 H 1)。
author: mattzmsft
ms.author: mazeller
ms.date: 05/02/2019
ms.topic: article
keywords: 发行说明、 版本、 windows 10、 生成、 19 小时 1、 os
ms.openlocfilehash: c1fa45eefb0abe702791d34801e84044afe48245
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416468"
---
# <a name="release-notes---may-2019"></a>发行说明-2019 年 5

**[Windows 10 2018 年 10 月更新](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (也称为 RS5) 包括 HoloLens 和 Windows Mixed Reality 沉浸式耳机连接到 Pc 的新功能。 

若要更新到 HoloLens 或电脑上的最新版本 （适用于 Windows Mixed Reality 沉浸式 (VR) 耳机），打开**设置**应用程序中，转到**更新和安全**，然后选择**检查更新**按钮。 在 Windows 10 PC 上，您还可以手动安装 Windows 10 2018 年 10 月更新使用[Windows 媒体创建工具](https://www.microsoft.com/software-download/windows10)。

**面向桌面的最新版本：** Windows 10 2018 年 10 月更新 (**10.0.17763.107**)<br>
**HoloLens 的最新版本：** Windows 10 2018 年 10 月更新 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>用于 Windows Mixed Reality 沉浸式耳机的新功能

Windows 10 2018 年 10 月更新包括有关在使用 Windows Mixed Reality 沉浸式 (VR) 耳机的桌面 PC 很多改进。

### <a name="for-everyone"></a>为每个人

* **混合现实手电筒**-变为现实，若要查找键盘，请参阅人附近，打开门户，也不删除您的头戴式看一看周围的环境 ！ 您可以启用混合现实手电筒从开始菜单中，通过按 Windows + 随取即行在动作在控制器上，或者说"打开/关闭 Flashlight"。 想要查看，如在黑暗中使用手电筒的方向点你的控制器。

    ![混合的现实闪光灯](images/mr-flashlight.png)

* **新的应用程序以及启动主混合现实中的内容的方法**
    * 如果您使用的[SteamVR 为 Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)、 SteamVR 标题现在显示在开始菜单，并为每个应用启动器上可以放入家庭混合现实。
    
        ![SteamVR 应用启动器](images/steamvr-launchers.png)
        
    * 新*360 视频*用于发现的 360 度视频定期特选所选内容的应用。
    * 新*WebVR 展示*用于发现的 WebVR 定期特选所选内容的应用内体验。
    * 首次 Windows Mixed Reality 客户将输入 Cliff 房屋和找到它预填充的 3D 应用程序启动器为一些我们最喜爱的沉浸式应用和 Microsoft Store 的游戏。
    * Microsoft Edge 窗口现在包括*共享*按钮。
* **快速操作菜单**-从在沉浸式混合的现实应用中，您可以按 Windows 按钮，以访问新的快速操作菜单中，轻松地访问*SteamVR 菜单*，*照片/视频捕获*，*手电筒*，并*家庭*。
* **支持的背包 Pc** -Windows Mixed Reality 沉浸式 (VR) 耳机背包电脑运行而无需安装程序完成后显示仿真程序。
* **新的音频功能**-现在可在您的头戴式镜像到同时的音频插孔 （或耳机） 从 Windows Mixed Reality 体验音频*和*音频设备连接到您的 PC （如外部扬声器）。 我们还添加了音量级别的可视指示器耳机的显示中。
* **其他改进**
    * 混合现实门户现在提供更新通过 Microsoft Store 中，启用主要 Windows 版本之间更快的更新。 请注意，这仅适用于桌面应用程序和 Windows Mixed Reality 耳机体验仍使用 OS 更新。 
    * 耳机进入睡眠状态，当 Windows Mixed Reality 应用挂起而不是终止 （直到关闭混合现实门户）。
    
### <a name="for-developers"></a>对于开发人员

* **[跟踪的 QR 码](qr-code-tracking.md)** -回感应用启用 QR 代码在混合的现实应用中，允许 Windows Mixed Reality 沉浸式 (VR) 耳机来扫描 QR 码和报告这些跟踪。
* **硬件 DRM 支持的沉浸式应用程序**-开发人员可以立即请求受硬件保护后台缓冲区纹理受显示硬件，则允许应用程序从源，如 PlayReady 使用受硬件保护的内容。
* **[将混合的现实捕获 UI 集成到沉浸式应用程序](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** -开发人员可以将混合的现实捕获集成到其应用程序中使用内置 Windows[摄像头捕获 UI](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)只需几行代码。

## <a name="new-features-for-hololens"></a>HoloLens 的新功能

Windows 10 2018 年 10 月更新是公开提供给所有 HoloLens 客户，并包括了大量改进，例如：

### <a name="for-everyone"></a>为每个人

* **快速操作菜单**-从在沉浸式混合的现实应用中，您可以按 Windows 按钮，以访问新的快速操作菜单中，轻松地访问*开始录制视频*，*拍摄照片*，*混合现实主页*，*更改音量*，并*Connect*。
* **从开始或快速操作菜单启动/停止视频捕获**-如果从开始菜单或快速操作菜单启动视频捕获，您可以停止录制，从同一位置。 （不要忘记，您可以始终执行此操作通过语音命令过。）
* **项目到支持 Miracast 的设备**-如果使用已启用 Miracast 的显示器或适配器项目附近的 Surface 设备或电视/监视器你 HoloLens 的内容。
* **新的通知**-查看和响应上 HoloLens，就像在 PC 上的通知。  
* **在沉浸式混合的现实应用程序中的有用叠加**-现在将看到如键盘、 对话、 文件选取器覆盖，等时使用沉浸式混合现实应用。
* **卷更改为可视的指示器**-当你用完的卷/向下按钮在 HoloLens 上可以看到耳机的音量级别的可视指示器。
* **为设备启动新的视觉对象**-加载指示器来提供视觉反馈系统正在加载程序在启动过程中已添加。
* **随时随地共享**-Windows 附近共享体验，可与附近的 Windows 设备共享一个捕获。  
* **从 Microsoft Edge 的共享**-现在包括 Microsoft Edge*共享*按钮。 

### <a name="for-developers"></a>对于开发人员

* **[将混合的现实捕获 UI 集成到沉浸式应用程序](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** -开发人员可以将混合的现实捕获集成到其应用程序中使用内置 Windows[摄像头捕获 UI](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)只需几行代码。

### <a name="for-commercial-customers"></a>对于商业客户

* **启用安装后设置**-现在可以应用在任何时候使用设置预配包运行时。
* **使用 Azure AD 组分配访问**-你现在可以使用为其分配访问权限的 Windows 配置 Azure AD 组来设置单个或多应用展台配置。
* **从登录屏幕中的配置文件交换机上固定登录**-PIN 登录现已可供"其他用户"在登录屏幕上。 
* **读取通过 MDM 的设备的硬件信息**-IT 管理员可以看到，并按其 MDM 控制台中的设备序列号跟踪 HoloLens。
* **设置通过 MDM （重命名） 的 HoloLens 设备名称**-IT 管理员可以查看和重命名 HoloLens 设备及其 MDM 控制台中的。

### <a name="for-international-customers"></a>对于国际客户

现在可以为简体中文或日语，包括本地化的拼音键盘、 听写、 文本到语音转换 (TTS) 和语音命令与本地化的用户界面使用 HoloLens。

## <a name="known-issues"></a>已知问题

我们努力工作以提供最佳 Windows Mixed Reality 体验，但我们仍跟踪一些已知的问题。 如果其他人发现，请[向我们提供反馈](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)。

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>更新后
使用 Windows 10 2018 年 10 月更新在 HoloLens 上时，可能会注意到以下问题：
* **应用程序可能会导致从通知启动登录循环**– 某些需要单一登录的应用程序可以最终进入无限登录循环从通知启动。 例如，这可能是从 Microsoft Store 安装 Microsoft 公司门户应用并启动安装完成通知从后。
* **可以使用空白页完成应用登录页**– 在某些情况下，当针对应用程序，在完成登录页不会关闭，改为显示一个空白的 （黑色） 页上显示登录提示。 可以关闭空白页，也可以移动它，以发现下方应用程序。 作为示例，这可以在登录期间 MDM 注册，从设置应用。 

## <a name="provide-feedback-and-report-issues"></a>提供反馈和报告问题

请使用[HoloLens 或 Windows 10 电脑上的反馈中心应用](give-us-feedback.md)提供反馈和报告问题。 使用反馈中心可确保所有必要的诊断信息均包括在内，以帮助我们的工程师快速调试和解决问题。

>[!NOTE]
>请务必接受提示，询问你是否希望反馈中心，以访问您的 Documents 文件夹 (选择**是**出现提示时)。

## <a name="prior-release-notes"></a>以前的发行说明

* [发行说明-2018 年 10 月](release-notes-october-2018.md)
* [发行说明 - 2018 年 4 月](release-notes-april-2018.md)
* [发行说明 - 2017 年 10 月](release-notes-october-2017.md)
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>请参阅
* [沉浸式头戴式支持 （外部链接）](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 支持 （外部链接）](https://support.microsoft.com/products/hololens)
* [安装工具](install-the-tools.md)
* [向我们提供反馈](give-us-feedback.md)

