---
title: 发行说明-5 月2020
description: Windows 10 2020 更新的 windows Mixed Reality 发行说明（也称为2004）。
author: tmlyon
ms.author: tmlyon
ms.date: 05/27/2020
ms.topic: article
keywords: 发行说明，版本，windows 10，build，20H1，os，2020，2004
ms.openlocfilehash: ec92259662109001c02cf631eb6b9948d61ba9de
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/27/2020
ms.locfileid: "84124134"
---
# <a name="release-notes---may-2020"></a>发行说明-5 月2020

**Windows 10 （可能为2020更新）（v2004）** 包含 Windows mixed REALITY （VR）耳机的新功能，例如在混合现实总部启动 Win32 应用程序的功能。 HoloLens （第一代）是长期维护服务（LTS），每月发布服务更新。

若要更新到适用于 Windows Mixed Reality 沉浸（VR）耳机的 PC 上的最新版本，请打开 "**设置**" 应用，中转到 "**更新" & 安全**"，然后选择"**检查更新**"按钮。 在 Windows 10 电脑上，你还可以使用[windows media 创建工具](https://www.microsoft.com/software-download/windows10)手动安装**Windows 10 2020 更新**。

**最新版本的桌面**： Windows 10 v2004 （10.0.19041.264）

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 沉浸式耳机更新

### <a name="introducing-the-new-microsoft-edge"></a>推出新的 Microsoft Edge
如前所述[，我们](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge)已在 Windows Mixed Reality 中使用新的 Microsoft Edge 浏览器进行了更好的支持。 新的 Microsoft Edge 采用 Chromium 开源项目为客户创建更好的 web 兼容性，并为所有 web 开发人员创建更少的 web 兼容性。 它还支持 WebXR，这是用于创建用于 VR 耳机的沉浸式 web 体验的新标准，而不是 WebVR。

### <a name="improved-settings-for-wmr"></a>改进的 WMR 设置
感谢你的反馈，我们已添加并阐明了耳机显示页面上的设置：

* 更改这些设置的**视觉质量**仅影响混合现实的主环境（Cliff 房子和 Skyloft）：

* **调整混合现实中的详细程度和质量质量**-这将更改我们在本主页中使用的一些渲染影响。 特别是，将此设置从 "低" 改为 "高" 时，不同材料的视觉质量（木材、具体等）将会缩放。

* **更改应用程序窗口分辨率**-默认情况下，在主启动的大多数2d 窗口均以720p 分辨率启动。 尽管可以在垂直方向上手动 & 调整其大小，但你也可以选择让它们全都以1080p 的方式启动。 以前，此选项在视觉质量下作为非常高（beta）选项提供。 我们已将其正确地拆分为单独的设置。

* **体验选项**-这些选项调整了混合现实体验，降低了硬件可能会因硬件而不受限制的 90 fps 而降低的负载。 您可以选择显式启用或禁用这些附加设置，或者选择 "让 Windows 决定" 并让试探法继续决定何时切换这些设置。

* **解决方法**：如果你有高分辨率的耳机（如 HP 回音），我们支持以其本机分辨率运行，或者出于性能原因，降低分辨率。 先前的耳机（如 Samsung 太空和太空 +）仅支持单一分辨率，因此你将无法在这些耳机上更改此设置。

* **帧速率**-你现在可以手动设置耳机显示的帧速率，或继续允许 Windows 使用其试探法来确定是否更适合 60 hz 或 90 Hz。

* **校准**-与之前一样，你可以在你的耳机支持的情况下调整 IPD （interpupillary 距离）。

* **输入切换**-将输入焦点切换（Win + Y）行为切换为自动（基于状态传感器反馈）或手动。

### <a name="new-cortana-app"></a>新建 Cortana 应用
Windows 的这一更新包括最新版本的 Cortana 应用程序，该应用程序目前仅提供英语版本，不再支持某些特定于混合现实的命令，例如 "拍摄照片" 和 "拍摄视频"。 你仍可以使用新 Cortana 来启动应用，并且它还支持新的工作效率重点命令，如 "我的下一会议是什么时候？" 或 "发送一封电子邮件到 <name> 我的最晚运行。"

#### <a name="please-help-us-improve"></a>请帮助我们改进！
我们会不断改进兼容性。  如果在 Windows Mixed Reality 中发现你最喜欢的经典 Win32 应用程序不能正常工作，请通过我们的[反馈中心](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)提交反馈。

## <a name="prior-release-notes"></a>以前的发行说明

* [发行说明-5 月2019](release-notes-may-2019.md)
* [发行说明 - 2018 年 10 月](release-notes-october-2018.md)
* [发行说明-2018 年4月](release-notes-april-2018.md)
* [发行说明 - 2017 年 10 月](release-notes-october-2017.md)
* [发行说明 - 2016 年 8 月](release-notes-august-2016.md)
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另请参阅
* [沉浸式耳机支持（外部链接）](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens 支持（外部链接）](https://support.microsoft.com/products/hololens)
* [安装工具](install-the-tools.md)
* [向我们提供反馈](give-us-feedback.md)
