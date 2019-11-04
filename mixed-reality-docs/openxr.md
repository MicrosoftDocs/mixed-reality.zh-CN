---
title: OpenXR
description: 使用可移植 OpenXR API 标准构建引擎，并将其部署到 Windows Mixed Reality 和 HoloLens 2 耳机。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，Mixed Reality OpenXR 开发人员门户，DirectX，本机，本机应用自定义引擎，中间件
ms.openlocfilehash: cf8795e6fed7db9fd0743d0902ce1585d56fa5e0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438139"
---
# <a name="openxr"></a>OpenXR

OpenXR 是来自<a href="https://www.khronos.org/" target="_blank">Khronos</a>的开放版税免费 API 标准，可提供引擎，可从多个供应商处跨[混合现实频谱](mixed-reality.md)对各种设备进行本机访问。

可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 上的 Windows Mixed 耳机上进行开发。  如果你无权访问耳机，则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。

## <a name="why-openxr"></a>为什么要 OpenXR？

借助 OpenXR，你可以构建面向全息设备（如 HoloLens 2）的引擎，该引擎将数字内容置于真实世界中，就像它确实如此，还可以提供沉浸式设备（如台式计算机的 Windows Mixed Reality 耳机）世界，并将其替换为数字体验。  OpenXR 可让你编写代码，然后在各种硬件平台上对其进行迁移。

OpenXR API 使用加载程序将应用程序直接连接到头戴显示设备的本机平台支持。  这为最终用户提供最大的性能和最小延迟，无论他们使用的是 Windows Mixed Reality 耳机还是其他任何耳机都是如此。

## <a name="what-is-openxr"></a>什么是 OpenXR？

Core OpenXR 1.0 API 提供生成引擎的基本功能，你可以将其作为一种全息设备，如 HoloLens 2 和沉浸式设备，如 Windows Mixed Reality 耳机：
* 系统 + 会话
* 引用空间（视图、本地、暂存）
* 查看配置（单声道、立体声）
* 交换链 + 帧计时
* 组合层
* 输入和 haptics
* 图形 API + 平台集成

若要了解有关 OpenXR API 的信息，请参阅 OpenXR 1.0<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">规范</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 参考</a>和<a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速参考指南</a>。  有关详细信息，请参阅<a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 页</a>。

若要面向一组完整的 HoloLens 2 功能，还将使用跨供应商和供应商特定的 OpenXR 扩展，这些扩展启用 OpenXR 1.0 核心之外的其他功能，例如已表述的手动跟踪、目视跟踪、空间映射和空间锚。  请参阅下面的 "[规划" 部分](openxr.md#roadmap)，了解有关今年晚些扩展的详细信息。

请注意，OpenXR 本身并不是混合现实引擎。  相反，OpenXR 使 Unity 和 Unreal 等引擎可以编写可移植代码一次，这样就可以访问用户的全息或沉浸式设备的本机平台功能，而不管哪个供应商构建了该平台。

## <a name="getting-started-with-openxr-for-hololens-2"></a>针对 HoloLens 2 的 OpenXR 入门

开始开发适用于 HoloLens 2 的 OpenXR 应用程序：

1. 设置 HoloLens 2 或按照说明[安装 hololens 2 模拟器](using-the-hololens-emulator.md)。
1. 从设备或模拟器中启动应用商店应用，并确保更新所有应用。  这将确保你的 HoloLens 上的 OpenXR 运行时更新为 OpenXR 1.0。  如果使用模拟器，你将需要咨询[模拟器输入说明](using-the-hololens-emulator.md#basic-emulator-input)，以帮助你在模拟器内使用应用商店应用。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>OpenXR for Windows Mixed Reality 耳机入门

开始为沉浸式 Windows Mixed Reality 耳机开发 OpenXR 应用程序：

1. 请确保运行 Windows 10 2019 更新（1903），这是 Windows Mixed Reality 最终用户运行 OpenXR 应用程序的最低要求。  如果你使用的是早期版本的 Windows 10，则可以使用<a href="https://www.microsoft.com//software-download/windows10" target="_blank">Windows 10 更新助手</a>升级到5月2019更新。  如果无法更新您的 PC，还可以[使用 Windows 10 10 月2018版（1809）开发 OpenXR 应用程序](openxr.md#developing-on-windows-10-october-2018-update)，不过您可能会遇到性能下降或其他问题。
2. 设置 Windows Mixed Reality 耳机，或按照说明[启用 Windows Mixed reality 模拟器](using-the-windows-mixed-reality-simulator.md)。  设置 Windows Mixed Reality 后，混合现实门户会自动安装 Windows Mixed Reality OpenXR 运行时。  然后，Microsoft Store 会使运行时保持最新状态。
3. 通过从 "开始" 菜单启动混合现实门户，并单击 .。。菜单，然后选择 "设置 OpenXR"。<br>
![在混合现实门户中设置 OpenXR](images/mixed-reality-portal-set-up-openxr.png)

如果需要让 Windows Mixed Reality OpenXR 运行时再次激活，请重复步骤3。

> [!NOTE]
> 系统很快会自动为所有 Windows Mixed Reality 最终用户设置 Windows Mixed Reality OpenXR 运行时。

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>获取混合现实 OpenXR 开发人员门户

若要尝试 Windows Mixed Reality OpenXR 运行时，可以安装<a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">[Mixed Reality OpenXR 开发人员门户应用程序</a>。  此应用程序提供了演示 OpenXR 的各种功能的演示场景，同时提供了一个系统状态页，其中提供了有关活动运行时和当前耳机的关键信息。

![混合现实 OpenXR 开发人员门户应用](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>生成示例 OpenXR 应用

<a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>项目演示了一个简单的 OpenXR 示例，其中包含两个 Visual Studio 项目文件，一个用于 Win32 桌面应用，另一个用于 UWP HoloLens 2 应用。  由于解决方案包含一个 HoloLens UWP 项目，因此需要在 Visual Studio 中安装[通用 Windows 平台开发工作负载](install-the-tools.md#installation-checklist)才能完全打开它。

请注意，虽然 Win32 和 UWP 项目文件是独立的，但由于打包和部署的不同，每个项目中的应用代码都是100%。

## <a name="roadmap"></a>路线图

OpenXR 规范定义了一种扩展机制，它使运行时实现程序能够公开超出<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">基本 OpenXR 1.0 规范</a>中定义的[核心功能](openxr.md#what-is-openxr)的其他功能。

有三种类型的 OpenXR 扩展：
* **供应商扩展（例如 MSFT）：** 启用硬件或软件功能中的每个供应商创新。  任何运行时供应商随时都可以引入和交付供应商扩展。
* **扩展插件：** 多个公司定义和实现的跨供应商扩展。  一组感兴趣的公司随时可以引入扩展扩展。
* **KHR 扩展：** 正式 Khronos 扩展作为核心规范版本的一部分而被批准。  KHR 扩展与核心规范本身具有相同的许可证。

一年结束后，Windows Mixed Reality OpenXR 运行时将支持一组 MSFT 和 EXT 扩展，这些扩展将整套 HoloLens 2 功能引入 OpenXR 应用程序：
* [未绑定的参考空间（全球范围体验）](coordinate-systems.md#building-a-world-scale-experience)
* [空间锚 + 存储](spatial-anchors.md)
* [手型 articulation + 手写网格](hands-and-tools.md)
* [眼睛凝视](eye-tracking.md)
* [辅助视图配置（混合现实捕获）](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [空间映射](spatial-mapping.md)
* 与 Windows SDK Api 互操作

尽管其中一些扩展可能会作为特定于供应商的 MSFT 扩展而开始，但 Microsoft 和其他 OpenXR 运行时供应商正在协同工作，为许多这些功能领域设计跨供应商 EXT 或 KHR 扩展。  这将使你为这些功能编写的代码可在运行时供应商之间移植，就像核心规范一样。

## <a name="troubleshooting"></a>“疑难解答”

下面是一些 Windows Mixed Reality OpenXR 运行时的故障排除提示。  如果你有关于<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>的任何其他问题，请访问<a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 论坛</a>或<a href="https://khr.io/slack" target="_blank">时差 #openxr 频道</a>。

### <a name="developing-on-windows-10-october-2018-update"></a>在 Windows 10 10 月2018更新上进行开发

如果无法将[开发电脑升级到 "2019 年5月更新版" 更新](https://www.microsoft.com//software-download/windows10)，可以通过执行以下一项操作来设置 Windows 10 10 月版2018更新（1809） PC 进行开发：

1. 按照上述步骤开始在台式计算机上 OpenXR。
1. 若要将 Windows Mixed Reality OpenXR 运行时设置为系统的活动 OpenXR 运行时，请安装[Windows Mixed Reality OpenXR Developer 兼容包](https://aka.ms/openxr-compat)。

> [!NOTE]
> 尽管在开发 OpenXR 应用程序时可以使用 Windows 10 十月2018更新（1809），但对于最终用户来说，Windows 10 可能2019更新（1903）是最终用户在 Windows Mixed Reality 中使用 OpenXR 的最低要求。  在 10 2018 月的更新中运行 OpenXR 应用程序时，可能会遇到性能下降或其他问题。  强烈建议将开发 PC 升级到 Windows 10 2019 更新（1903）。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 应用未启动 Windows Mixed Reality

如果 OpenXR 应用在运行时未启动 Windows Mixed Reality，则 Windows Mixed Reality OpenXR 运行时可能不会设置为活动运行时。  请务必遵循上述说明，了解如何[开始 OpenXR For Windows Mixed Reality 耳机](#getting-started-with-openxr-for-windows-mixed-reality-headsets)，使运行时处于活动状态。

还可以运行[混合现实 OpenXR 开发人员门户](#getting-the-mixed-reality-openxr-developer-portal)，以获取有关系统上 Windows Mixed Reality OpenXR 运行时状态的其他故障排除帮助。

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>混合现实门户未显示 "设置 OpenXR" 菜单项

请确保至少运行 Windows 10 十月2018更新（1809）。  如果使用的是早期版本的 Windows 10，则可以使用[windows 10 更新助手](https://www.microsoft.com//software-download/windows10)升级到2019更新（1903）。

如果你的混合现实门户应用的版本较旧，"设置 OpenXR" 菜单项可能不可用。  检查[混合现实门户应用更新](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)以确保具有最新版本。

请注意，如果已安装并激活 Windows Mixed Reality OpenXR 运行时，则不会显示 "设置 OpenXR" 菜单项。  可以安装[混合现实 OpenXR 开发人员门户](#getting-the-mixed-reality-openxr-developer-portal)来确定系统上 OpenXR 运行时的当前状态。

## <a name="see-also"></a>另请参阅

* <a href="https://www.khronos.org/openxr/" target="_blank">有关 OpenXR 的详细信息</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 参考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速参考指南</a>
