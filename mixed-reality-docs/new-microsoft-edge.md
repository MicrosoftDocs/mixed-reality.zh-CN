---
title: Windows Mixed Reality 和新的 Microsoft Edge
description: 在 Windows Mixed Reality 中准备好新的 Microsoft Edge。 包括对预期的更改、要查找的更新和已知问题。
author: mattzmsft
ms.author: mazeller
ms.date: 07/31/2020
ms.topic: article
keywords: 边缘，新，沉浸式 web，microsoft edge，browser，vr
ms.openlocfilehash: 107b825496cc318042da0e0cd9acdbe482994a69
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476979"
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

### <a name="monitor-and-input-handling-issues"></a>监视和输入处理问题

为 Windows 10 版本1903（或更高版本）采用2020-01 累积更新后，在 Windows Mixed Reality 会话期间，虚拟监视器将在 "**设置" > 系统 > 显示**中显示为一般物理监视器。 有些客户（尤其是那些具有多个物理监视器的客户）可能会注意到桌面布局和输入处理的问题。

**为什么会发生这种情况**

Windows [10 2019 更新](#release-notes-may-2019.md)中引入了对 Windows Mixed Reality 中经典 Win32 应用程序的支持。 若要启用此支持，必须创建虚拟监视器来托管 Win32 应用程序。 每次启动新的 Win32 应用程序时，都必须创建另一个虚拟监视器。 遗憾的是，创建虚拟监视器是一种密集型任务，可能会导致耳机显示短暂冻结。 客户提供了反馈，指出这是一种令人不安且有中断的体验。 由于此反馈，增加了 Win32 应用程序的使用，因此我们决定在 Windows Mixed Reality 启动过程中预分配三个虚拟监视器，以防止这种中断，并使客户能够启动多达三个并发的 Win32 应用程序，而不会遇到耳机显示冻结。

**解决方法**

由于收到一些客户（尤其是那些具有多个物理监视器的客户），因此将更愿意禁用此虚拟监视器预分配。 为了向客户提供控制和选择，我们启用了涉及更改注册表项值的解决方法（适用于 Windows 10 版本2004的2020-07 累积更新）。

>[!NOTE]
>修改注册表项值适用于高级用户。

>[!WARNING]
>如果在 Windows Mixed Reality 中启动 Win32 应用程序（如流、新的 Microsoft Edge 或 Google Chrome），禁用虚拟监视器预分配可能会导致耳机显示短暂的冻结。

若要禁用虚拟监视器预分配：
1. 检查 Windows 10 版本2004的2020-07 累积更新**Windows 更新**，并在可用时安装更新。
2. 启动**注册表编辑器**。
3. 导航到 HKEY_CURRENT_USER \SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\PreallocateVirtualMonitors
4. 将 DWORD 值从1（其默认值）更改为0（零）
    * TRUE-1
    * FALSE-0

当你尝试在 Windows Mixed Reality 而不是预分配中启动 Win32 应用程序时，虚拟监视器现在将进行分配。 若要重置此设置并重新启用虚拟监视器预分配，请将 DWORD 值返回1。

### <a name="additional-known-issues"></a>其他已知问题

-   当混合现实门户关闭时，在 Windows Mixed Reality 中打开的网站将会丢失，但 Microsoft Edge 窗口仍会保留在混合现实中的位置。
- WebXR 体验，包括360查看器扩展，可能无法在具有混合 GPU 设置的电脑上正常启动。 通过选择专用 GPU 作为图形卡软件中的默认 GPU，可以解决此问题。
-   Microsoft Edge windows 中的音频未 spatialized。
-   **修复了360查看器扩展版本 2.3.8**：在 Windows Mixed Reality 中从 YouTube 打开360视频可能会导致耳机上出现视频失真。 重启边缘应在不可见的情况下更新360查看器扩展以解决此问题。 您可以通过 `edge://system/` 在地址栏中输入，然后选择 "扩展" 旁边的**展开**按钮，确认您所拥有的扩展版本。




