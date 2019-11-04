---
title: 发行说明-2016 年8月
description: 适用于 Windows 10 周年纪念版本的 HoloLens 发行说明（秋季为2016）
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，发行说明，os，平台，功能，商业套件
ms.openlocfilehash: dcac64524cd8d1b1f2b0a496c4dcd2ad2fc7b690
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438093"
---
# <a name="release-notes---august-2016"></a>发行说明-2016 年8月

HoloLens 团队正在侦听来自 Windows 预览体验计划中的开发人员的反馈，以确定工作优先级。 请继续通过反馈中心、[开发人员论坛](https://forums.hololens.com)和[Twitter 通过 @HoloLens](https://twitter.com/hololens)[向我们提供反馈](give-us-feedback.md)。 由于 Windows 10 涵盖周年周年更新，因此 HoloLens 团队很乐意更好地提高全息体验。 在此更新中，我们侧重于主要修补程序、改进功能和引入企业请求的功能，并在 Microsoft HoloLens 商业套件中提供。

**最新版本：** Windows 全息8月2016更新（**10.0.14393.0**、Windows 10 周年发布版）

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

若要[更新到当前版本](updating-hololens.md)，请打开 "*设置*" 应用，中转到 "*更新 & 安全性*"，然后选择 "*检查更新*" 按钮。

## <a name="new-features"></a>新功能

**附加到进程调试**HoloLens 现在支持附加到进程调试。 你可以使用 Visual Studio 2015 Update 3 连接到 HoloLens 上正在运行的应用程序并[开始对其进行调试](using-visual-studio.md#debugging-an-installed-or-running-app)。 这无需从 Visual Studio 项目中进行部署。

**已更新 HoloLens 模拟器**我们还发布了 HoloLens 模拟器的更新版本。

**游戏板支持**你现在可以将蓝牙 gamepads 与 HoloLens 配对并使用！ 新发布的 Xbox 无线控制器具有蓝牙功能，可用于播放你最喜欢的启用游戏程序的游戏和应用程序。 必须先应用[控制器更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)，然后才能使用 HoloLens 连接 Xbox 无线控制器。 [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)和[Windows 工作输入](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx)Api 支持 Xbox 无线控制器。 可以通过[Windows. 游戏输入](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx)API 访问其他型号的蓝牙控制器。

## <a name="improvements-and-fixes"></a>改进和修复

我们与 Windows 10 周年更新的其余部分保持同步，因此除了 HoloLens 特定的修补程序，你还可以从 Windows 更新中获得所有性能，以提高平台的可靠性和性能。 你的反馈非常重视，并优先于版本中的修补程序。

我们改进了以下体验：
* 登录体验。
* 工作区加入。
* 设备电源状态转换的能源效率。
* 混合现实捕获的稳定性。
* 蓝牙连接的可靠性
* 多应用场景中的全息影像持久性。

我们修复了以下问题：
* Visual Studio 探查器和图形调试器无法连接。
* 照片 & 文档不会显示在设备门户的文件资源管理器中。
* 当光标位于调整模式下时，应用程序栏可以闪烁。
* 处于调整模式时，眼睛点光标将在一段时间内更改为4箭头光标。
* "你好 Cortana 播放音乐" 不启动 Groove。
* 在上一次更新后，说 "回家 Home" 不会正确显示引脚面板。

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Microsoft HoloLens 商用套件简介

Microsoft HoloLens 商用套件已准备好进行企业部署。 我们已从早期企业合作伙伴添加了多个高请求[商业功能](commercial-features.md)。

请与当地 Microsoft 帐户经理联系以购买 Microsoft HoloLens 商用套件。

### <a name="key-commercial-features"></a>主要商业功能 

* **展台模式。** 使用 HoloLens 展台模式，你可以限制要运行哪些应用来启用演示或展示体验。<br>
  通过展台模式 ![，HoloLens 直接启动到所选的应用。](images/201608-kioskmode-400px.png)
* **适用于 HoloLens 的移动设备管理（MDM）。** 你的 IT 部门可以使用 Microsoft Intune 的解决方案同时管理多个 HoloLens 设备。 你将能够管理设置，选择要安装的应用，并设置根据你的组织需要定制的安全配置。<br>
  ![在 HoloLens 上移动设备管理在多台设备上提供企业级设备管理。](images/201608-enterprisemanagement-400px.png)
* **适用于企业的 Windows 更新。** 受控的操作系统更新到设备和支持长期服务分支。
* **数据安全性。** BitLocker 数据加密在 HoloLens 上启用，以提供与任何其他 Windows 设备相同级别的安全保护。
* **工作访问。** 你的组织中的任何人都可以通过 HoloLens 上的虚拟专用网络远程连接到公司网络。 HoloLens 还可以访问需要凭据的 Wi-fi 网络。
* **适用于企业的 Microsoft Store。** 你的 IT 部门还可以设置企业专用商店，只包含适用于你的特定 HoloLens 用途的公司应用。 将企业软件安全地分发到选定的企业用户组。

### <a name="development-edition-vs-commercial-suite"></a>开发版与商业套件

<table>
<tr>
<th>功能</th><th>开发版</th><th>商业套件</th>
</tr><tr>
<td>设备加密（Bitlocker）</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>虚拟专用网络 (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">展台模式</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 管理和部署</th>
</tr><tr>
<td>移动设备管理 (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>阻止取消注册的功能</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>基于证书的公司 Wi-fi 访问</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store （使用者）</td><td style="text-align: center;">使用</td><td style="text-align: center;">通过 MDM 筛选</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">业务商店门户</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 安全和标识</th>
</tr><tr>
<td>Azure Active Directory 登录（AAD）</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>通过 Microsoft 帐户（MSA）登录</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>带有 PIN 解锁的下一代凭据</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">安全启动</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 服务和支持</th>
</tr><tr>
<td>自动系统更新到达时自动更新</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">适用于企业的 Windows 更新</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>长期服务分支</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>以前的发行说明
* [发行说明 - 2016 年 5 月](release-notes-may-2016.md)
* [发行说明 - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>另请参阅
* [HoloLens 已知问题](hololens-known-issues.md)
* [商业功能](commercial-features.md)
* [安装工具](install-the-tools.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
