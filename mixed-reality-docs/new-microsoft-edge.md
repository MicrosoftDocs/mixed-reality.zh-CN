---
title: Windows Mixed Reality 和新的 Microsoft Edge
description: 在 Windows Mixed Reality 中准备好新的 Microsoft Edge。 包括对预期的更改、要查找的更新和已知问题。
author: mattzmsft
ms.author: mazeller
ms.date: 01/15/2020
ms.topic: article
keywords: 边缘，新，沉浸式 web，microsoft edge，browser，vr
ms.openlocfilehash: d61780045e795850012536a36fde67b9934c76aa
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216228"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality 和新的 Microsoft Edge

[新的 Microsoft Edge 现在可供下载](https://blogs.windows.com/windowsexperience/?p=173496)，但客户也可以在未来的几个月内通过一种经过衡量的推出方法，[等待它安装到 Windows 10 的未来更新中](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)。 

在此新闻中，**我们希望让 Windows Mixed REALITY VR 耳机客户知道从新的 Microsoft Edge 获得的内容，并通知你一些会在 Windows Mixed Reality 中提高你的 web 浏览体验的待定更新**。

## <a name="introducing-the-new-microsoft-edge"></a>推出新的 Microsoft Edge

新的 Microsoft Edge[采用桌面上的 Chromium 开放源代码项目](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/)，为客户创建更好的 web 兼容性，为所有 web 开发人员创建更少的 web 兼容性。 它还支持在启动时 WebXR，这是用于创建用于 VR 耳机的沉浸式 web 体验的新标准，而不是 WebVR。

>[!IMPORTANT]
>当你在最新的 Windows 10 设备上安装 Microsoft Edge 时，它将替换你的电脑上的以前（旧）版本。

## <a name="getting-ready-for-the-new-microsoft-edge"></a>准备好开始新的 Microsoft Edge

如果 Windows Mixed Reality，需要在混合现实总部使用新的 Microsoft Edge 的 windows Mixed Reality，则应**升级到 Windows 10 版本1903或更高版本，以便在混合现实中提供对 Win32 应用程序（例如新的 Microsoft Edge）的本机支持**。 请检查 Windows 更新或[手动安装最新版本的 Windows 10](https://www.microsoft.com/en-us/software-download/windows10)。

为了在混合现实中获得最佳的 Microsoft Edge 体验，我们还建议你等待 windows **10 版本1903（或更高版本）的2020-01 累积更新提供的新 Microsoft edge 的 Windows Mixed reality 优化**，该版本应在1月年底 Windows 更新提供。

>[!IMPORTANT]
>如果你选择在执行这些更新之前下载新的 Microsoft Edge，则在 Windows Mixed Reality 中将会出现一些已知问题（你可以参阅下文）。

## <a name="known-issues"></a>已知问题

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Windows 10 版本1903（或更高版本）的2020-01 累积更新解决的已知问题

- 启动任何 Win32 应用程序（包括新的 Microsoft Edge）都会导致耳机显示暂时冻结。
- Microsoft Edge 磁贴从 Windows Mixed Reality 开始菜单中消失（你可以在 "经典应用" 文件夹中找到它）。
- 以前的 Microsoft Edge 中的 Windows 仍位于混合现实主页，但无法使用。 尝试激活桌面应用内的 windows 启动边缘。
- 选择混合现实中的超链接时，将在桌面上而不是混合现实主页上启动 web 浏览器。
- 尽管不再支持 WebVR，但 WebVR 展示应用存在于混合现实主页中。
- 键盘启动和视觉对象的一般改进。

### <a name="additional-known-issues"></a>其他已知问题

-   当混合现实门户关闭时，在 Windows Mixed Reality 中打开的网站将会丢失，但 Microsoft Edge 窗口仍会保留在混合现实中的位置。
- WebXR 体验，包括360查看器扩展，可能无法在具有混合 GPU 设置的电脑上正常启动。 通过选择专用 GPU 作为图形卡软件中的默认 GPU，可以解决此问题。
-   Microsoft Edge windows 中的音频未 spatialized。
-   **修复了360查看器扩展版本 2.3.8**：在 Windows Mixed Reality 中从 YouTube 打开360视频可能会导致耳机上出现视频失真。 重启边缘应在不可见的情况下更新360查看器扩展以解决此问题。 您可以通过 `edge://system/` 在地址栏中输入，然后选择 "扩展" 旁边的**展开**按钮，确认您所拥有的扩展版本。
-   在 Windows Mixed Reality 会话期间，虚拟监视器将在 "设置" > 系统 > 显示中显示为一般物理监视器。



