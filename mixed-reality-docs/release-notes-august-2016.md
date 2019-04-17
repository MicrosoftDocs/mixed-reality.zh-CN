---
title: 发行说明-2016 年 8 月
description: HoloLens 的 Windows 10 周年版本 (2016 年秋季) 发行说明
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，发行说明、 操作系统、 平台、 功能、 商业套件
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592753"
---
# <a name="release-notes---august-2016"></a>发行说明-2016 年 8 月

HoloLens 团队正在侦听从开发人员的 Windows 预览体验计划，以确定工作的优先级的反馈。 请继续执行[向我们提供反馈](give-us-feedback.md)反馈中心，通过[开发人员论坛](https://forums.hololens.com)并[通过 Twitter @HoloLens ](https://twitter.com/hololens)。 为 Windows 10 周年更新中，HoloLens 团队令人满意地交付的接受，进一步提高全息版体验。 在此更新中，我们侧重于主要的修补程序、 改进和简介请求由企业和 Microsoft HoloLens 商业套件中提供的功能。

**最新版本：** Windows 全息版 2016 年 8 月更新 (**10.0.14393.0**，Windows 10 周年纪念版)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

向[更新到当前版本](updating-hololens.md)，打开*设置*应用程序中，转到*更新和安全*，然后选择*检查更新*按钮。

## <a name="new-features"></a>新增功能

**附加到进程调试**HoloLens 现在支持附加到进程进行调试。 可以使用 Visual Studio 2015 Update 3 连接到在 HoloLens 上正在运行的应用和[开始调试它](using-visual-studio.md#debugging-an-installed-or-running-app)。 这适用于无需从 Visual Studio 项目中进行部署。

**更新 HoloLens 模拟器**我们还发布了 HoloLens 仿真程序的更新的版本。

**游戏板支持**现在可以搭配使用，并使用 HoloLens 蓝牙游戏板 ！ 新发布的 Xbox 无线控制器 S 可用于播放您最喜欢的游戏板启用游戏和应用程序和功能蓝牙功能。 一个[控制器更新](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)之前你可以使用 HoloLens 连接 Xbox 无线控制器 S 必须应用。 支持 Xbox 无线控制器 S [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx)并[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) Api。 蓝牙控制器的其他模型可能通过访问[Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API。

## <a name="improvements-and-fixes"></a>改进和修复

因此，除了 Hololens 特定的修补程序，您还将接收的全部优势从 Windows 更新以增加平台可靠性和性能，我们已与 Windows 10 周年更新中，其余部分同步。 你的反馈是高值和设置优先级的版本中修复。

我们改进了以下体验：
* 登录体验。
* 加入工作区。
* 设备电源状态转换的电源效率。
* 使用混合现实捕获的稳定性。
* 蓝牙连接的可靠性
* 多应用程序方案中的 hologram 持久性。

我们还修复了以下问题：
* Visual Studio 探查器和图形调试器无法进行连接。
* 照片和文档根本不显示在设备门户中的文件资源管理器中。
* 将光标放置在它在调整模式下时，可以闪烁应用程序栏。
* 在调整模式下，关注的视线移动圆点光标将更改为 4 箭头光标一段时间速度更慢。
* "您好 Cortana 播放音乐"不启动 Groove。
* 上一更新后，说"转到主页"不 pin 面板中正确显示。

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Microsoft HoloLens 商业套件简介

Microsoft HoloLens 商业套件是准备好进行企业部署。 我们添加了多个高度请求[商业功能](commercial-features.md)从我们早期的业务合作伙伴。

请联系您当地的 Microsoft 客户经理以购买 Microsoft HoloLens 商业套件。

### <a name="key-commercial-features"></a>主要的商业功能 

* **展台模式。** HoloLens 展台模式下，您可以限制哪些应用程序运行，以启用演示或展示体验。<br>
  ![展台模式下，HoloLens 直接到所选的应用程序将启动。](images/201608-kioskmode-400px.png)
* **HoloLens 的移动设备管理 (MDM)。** 你的 IT 部门可以管理多个同时使用解决方案，如 Microsoft Intune 的 HoloLens 设备。 你将能够管理设置，选择要安装的应用，并设置根据你的组织需要定制的安全配置。<br>
  ![HoloLens 上的移动设备管理提供了跨多个设备的企业级设备管理。](images/201608-enterprisemanagement-400px.png)
* **适用于企业的 Windows 更新。** 控制设备和对长期服务分支的支持的操作系统更新。
* **数据安全性。** HoloLens 上启用 BitLocker 数据加密来提供相同级别的任何其他 Windows 设备的安全保护。
* **工作单位访问。** 你的组织中的任何人可以远程连接到通过虚拟专用网络上 HoloLens 企业网络。 HoloLens 还可以访问需要凭据的 Wi-fi 网络。
* **企业的 Microsoft Store。** 你的 IT 部门还可以设置企业专用应用商店，其中包含仅适用于特定的 HoloLens 使用公司的应用。 安全地在企业软件分发到所选企业用户组。

### <a name="development-edition-vs-commercial-suite"></a>开发版本 vs。商业套件

<table>
<tr>
<th>功能</th><th>Development Edition</th><th>商业套件</th>
</tr><tr>
<td>设备加密 (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>虚拟专用网络 (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">展台模式</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 管理和部署</th>
</tr><tr>
<td>移动设备管理 (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>阻止取消注册功能</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>基于证书的公司的 Wi-fi 访问权限</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store （使用者）</td><td style="text-align: center;">使用者</td><td style="text-align: center;">通过 MDM 进行筛选</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">业务应用商店门户</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 安全和标识</th>
</tr><tr>
<td>使用 Azure Active Directory (AAD) 的登录名</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>使用 Microsoft 帐户 (MSA) 登录</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>下一代凭据使用 PIN 解锁</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">安全启动</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 服务和支持</th>
</tr><tr>
<td>自动系统更新它们到达时</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">适用于企业的 Windows 更新</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>长期服务分支</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>以前的发行说明
* [发行说明-2016 年 5 月](release-notes-may-2016.md)
* [发行说明-2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>请参阅
* [HoloLens 的已知问题](hololens-known-issues.md)
* [商业特性](commercial-features.md)
* [安装工具](install-the-tools.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
