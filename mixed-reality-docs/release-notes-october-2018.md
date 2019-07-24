---
title: 发行说明-2018 年10月
description: 适用于 Windows 10 十月2018更新的 HoloLens 和 Windows Mixed Reality 发行说明 (也称为 RS5)。
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: 发行说明、版本、windows 10、build、rs5、os
ms.openlocfilehash: 794050910be40e7f98d0a1f67c2e1cf6963305dd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524250"
---
# <a name="release-notes---october-2018"></a>发行说明-2018 年10月

**[Windows 10 2018 10 月版更新](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (也称为 RS5) 包括适用于已连接到 Pc 的 HoloLens 和 Windows Mixed Reality 沉浸式耳机的新功能。 

若要更新到最新版本 (适用于 Windows Mixed Reality 沉浸式 (VR) 耳机), 请打开 "**设置**" 应用, 中转到 "**更新" & 安全**", 然后选择"**检查更新**"按钮。 在 Windows 10 电脑上, 还可以使用[windows media 创建工具](https://www.microsoft.com/software-download/windows10)手动安装 Windows 10 十月2018更新。

**最新版本的桌面:** Windows 10 十月2018更新 (**10.0.17763.107**)<br>
**最新版本的 HoloLens:** Windows 10 十月2018更新 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>适用于 Windows Mixed Reality 沉浸式耳机的新功能

Windows 10 2018 10 月版更新包括对使用台式计算机的 Windows Mixed Reality 沉浸式 (VR) 耳机进行了很多改进。

### <a name="for-everyone"></a>适用于每个人

* **混合现实模式**-在现实世界中打开一个门户来查找键盘、查看附近的某人或查看你的环境, 而无需删除耳机! 你可以从 "开始" 菜单中, 按下移动控制器上的 "Windows + 抓取" 或说 "开/关"。 将控制器指向要查看的内容的方向, 如使用暗色的闪光灯。

    ![混合现实闪光灯](images/mr-flashlight.png)

* **在混合现实主页中启动内容的新应用和方法**
    * 如果将[Windows Mixed Reality 用于 SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality), 则 SteamVR 标题现在会显示在 "开始" 菜单中, 每个标题的应用启动器可放置在混合现实主页中。
    
        ![SteamVR 应用启动器](images/steamvr-launchers.png)
        
    * 新的*360 视频*应用, 用于发现特选选择的360度视频。
    * 新的*WebVR 展示*应用, 用于发现特选的 WebVR 体验的定期选择。
    * 首次 Windows Mixed Reality 客户将进入 Cliff 房子, 并通过3D 应用程序启动器进行预填充, 以实现我们最喜欢的沉浸式应用和游戏 Microsoft Store。
    * Microsoft Edge windows 现在包含一个*共享*按钮。
* "**快速操作" 菜单**-从沉浸式的现实应用程序中, 可以按 "Windows" 按钮访问新的 "快速操作" 菜单, 并轻松访问*SteamVR 菜单*、*照片/视频捕获*、*闪光灯*和*home*。
* **对背包电脑的支持**-Windows Mixed Reality 沉浸式 (VR) 耳机在背包电脑上运行, 在完成安装程序后无需显示模拟器。
* **新增音频功能**-现在可以将音频从 Windows Mixed Reality 体验镜像到耳机中的音频插孔 (或耳机)*以及*连接到电脑的音频设备 (如外部扬声器)。 我们还在头戴显示设备中添加了音量级别的可视指示器。
* **其他改进**
    * 现在, 混合现实门户更新通过 Microsoft Store 提供, 可在主要 Windows 版本之间进行更快的更新。 请注意, 这仅适用于桌面应用程序和 Windows Mixed Reality 耳机体验, 仍会随操作系统一起更新。 
    * 当耳机进入睡眠状态时, Windows Mixed Reality 应用会被挂起, 而不是终止 (直到混合现实门户关闭)。
    
### <a name="for-developers"></a>对于开发人员

* **[QR 代码跟踪](qr-code-tracking.md)** -启用混合现实应用中的 qr 代码跟踪, 允许 Windows mixed reality 沉浸式 (VR) 耳机扫描 QR 码, 并将其报告回感兴趣的应用。
* **对沉浸式应用的硬件 DRM 支持**-即使显示硬件支持, 开发人员现在可以请求受硬件保护的后台缓冲区纹理, 这允许应用程序使用来自 PlayReady 等源的硬件保护内容。
* 将 **[混合现实捕获 Ui 集成到沉浸式应用中](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** -开发人员可以使用内置的 Windows[相机捕获 ui](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) , 只需几行代码即可将混合现实捕获集成到其应用中。

## <a name="new-features-for-hololens"></a>HoloLens 的新功能

Windows 10 2018 10 月版更新可供所有 HoloLens 客户公开使用, 并提供了许多改进, 例如:

### <a name="for-everyone"></a>适用于每个人

* "**快速操作" 菜单**-从一个沉浸式的现实应用程序中, 可以按 "Windows" 按钮访问新的 "快速操作" 菜单, 通过轻松访问*开始录制视频*,*拍摄照片*,*混合现实主页*,*更改卷*和*连接*。
* **从 "开始" 或 "快速操作" 菜单启动/停止视频捕获**-如果从 "开始" 菜单或 "快速操作" 菜单启动视频捕获, 则可以从同一位置停止录制。 (别忘了, 您也可以通过语音命令来执行此操作。)
* **投影到已启用 miracast 的设备**-如果使用启用了 miracast 的显示器或适配器, 则将你的 HoloLens 内容投影到附近的 Surface 设备或电视/显示器。
* **新通知**-在 HoloLens 上查看和响应通知, 就像在电脑上操作一样。  
* **沉浸式现实应用中的有用覆盖**-现在可以在使用沉浸式混合现实应用时看到叠加, 如键盘、对话框、文件选取器等。
* **卷更改的可视指示器**-当你使用 HoloLens 上的 "音量" 或 "下移" 按钮时, 会在耳机中看到音量级别的可视指示器。
* **设备启动的新视觉对象**-在启动过程中添加了一个加载指示器, 以提供系统正在加载的视觉反馈。
* **邻近共享**-Windows 附近共享体验允许你与附近的 windows 设备共享捕获。  
* **从 Microsoft Edge 共享**-microsoft edge 现在包含 "*共享*" 按钮。 

### <a name="for-developers"></a>对于开发人员

* 将 **[混合现实捕获 Ui 集成到沉浸式应用中](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** -开发人员可以使用内置的 Windows[相机捕获 ui](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) , 只需几行代码即可将混合现实捕获集成到其应用中。

### <a name="for-commercial-customers"></a>面向商业客户

* **启用安装后**设置-现在可以使用 "设置" 随时应用运行时预配包。
* **分配了 Azure AD 组的访问权限**, 现在可以使用 Azure AD 组来配置 Windows 分配的访问权限, 以设置单个或多个应用展台配置。
* 在登录屏幕**上从登录屏幕上登录配置文件的 pin**登录屏幕上的 "其他用户" 现在可以使用 pin 登录。 
* **通过 Mdm 读取设备硬件信息**-IT 管理员可以在其 MDM 控制台中按设备序列号查看和跟踪 HoloLens。
* **通过 MDM 设置 hololens 设备名称 (重命名)** -IT 管理员可以在其 MDM 控制台中查看和重命名 hololens 设备。

### <a name="for-international-customers"></a>对于国际客户

你现在可以将 HoloLens 与本地化的用户界面结合使用, 以用于简体中文或日语, 包括本地化的拼音键盘、听写、文本到语音转换 (TTS) 和语音命令。

## <a name="known-issues"></a>已知问题

我们一直在努力提供强大的 Windows Mixed Reality 体验, 但我们仍在跟踪一些已知问题。 如果发现其他人, 请[向我们提供反馈](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)。

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>更新后
在 HoloLens 上使用 Windows 10 十月2018更新时, 可能会注意到以下问题:
* **当应用程序从通知启动时, 应用程序可最终进入登录循环**–当从通知启动时, 某些需要登录的应用程序可能会以无限的登录循环结束。 例如, 从 Microsoft Store 安装 Microsoft 公司门户应用并从安装完成通知启动它后, 就会发生这种情况。
* **应用登录页可以在空白页上完成**–在某些情况下, 当登录提示显示在应用程序上时, 登录页不会关闭, 而是显示空白 (黑色) 页。 可以关闭空白页, 也可以移动它来发现下面的应用程序。 例如, 在通过设置应用进行 MDM 注册期间登录时, 可能会发生这种情况。 

## <a name="provide-feedback-and-report-issues"></a>提供反馈和报告问题

请使用[你的 HoloLens 或 Windows 10 电脑上的反馈中心应用](give-us-feedback.md)提供反馈和报告问题。 使用反馈中心可确保包括所有必要的诊断信息, 以帮助我们的工程师快速调试和解决问题。

>[!NOTE]
>请确保接受询问你是否想要反馈中心访问文档文件夹的提示 (在出现提示时选择 **"是"** )。

## <a name="prior-release-notes"></a>以前的发行说明

* [发行说明 - 2018 年 4 月](release-notes-april-2018.md)
* [发行说明 - 2017 年 10 月](release-notes-october-2017.md)
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>请参阅
* [沉浸式耳机支持 (外部链接)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 支持 (外部链接)](https://support.microsoft.com/products/hololens)
* [安装工具](install-the-tools.md)
* [向我们提供反馈](give-us-feedback.md)

