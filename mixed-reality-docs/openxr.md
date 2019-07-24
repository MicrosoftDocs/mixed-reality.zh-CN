---
title: OpenXR
description: 试用带有混合现实 OpenXR 开发者预览版的临时 OpenXR 0.90 API。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 混合现实 OpenXR 开发者预览版
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039174"
---
# <a name="openxr"></a>OpenXR

OpenXR 是来自[Khronos](https://www.khronos.org/)的开放版税免费标准, 可提供跨[混合现实](mixed-reality.md)范围内多家供应商的各种设备的本机访问权限。

借助 OpenXR, 你可以构建面向全息设备 (如 HoloLens 2) 的应用程序, 该应用程序将数字内容置于真实世界中, 就像它确实如此, 还可以提供沉浸式设备 (如台式计算机的 Windows Mixed Reality 耳机)实物, 并将其替换为数字体验。  OpenXR 可让你编写代码, 然后在各种硬件平台上对其进行迁移。

OpenXR 标准目前处于临时阶段, 为获得反馈而发布了初始 OpenXR 0.90 规范。  有关 OpenXR 的详细信息, 包括对[临时0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)和[标头](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)的访问, 请参阅[Khronos OpenXR 页](https://www.khronos.org/openxr/)。 

可以使用混合现实 OpenXR 开发者预览版在 HoloLens 2 或台式计算机上尝试使用临时的 OpenXR 0.90 API。  此早期运行时使面向 OpenXR 0.90 API 的应用程序可以面向 HoloLens 2 或桌面上的 Windows Mixed Reality 沉浸式耳机。

如果你无权访问耳机, 则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>为 HoloLens 2 设置混合现实 OpenXR 开发人员预览版

若要开始在 HoloLens 2 上进行混合现实 OpenXR 开发者预览版:

1. 设置 HoloLens 2 或按照说明[安装 hololens 2 模拟器](using-the-hololens-emulator.md)。
1. 从设备或模拟器中启动应用商店应用, 并确保更新所有应用。  这将安装混合现实 OpenXR 开发人员预览版, 以用于该设备上的应用。  如果使用模拟器, 你将需要咨询[模拟器输入说明](using-the-hololens-emulator.md#basic-emulator-input), 以帮助你在模拟器内使用应用商店应用。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>为沉浸式桌面耳机设置混合现实 OpenXR 开发人员预览版

若要开始使用台式计算机上的 Mixed Reality OpenXR 开发者预览版:

1. 请确保运行的是 Windows 10 十月2018更新 (1809) 或 Windows 10 可能2019更新 (1903)。  如果你使用的是早期版本的 Windows 10, 则可以使用[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)升级到5月2019更新。
1. 设置 Windows Mixed Reality 耳机, 或按照说明[启用 Windows Mixed reality 模拟器](using-the-windows-mixed-reality-simulator.md)。
1. 安装[混合现实 OpenXR 开发者预览版应用](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。  此应用可用于在 Windows 10 十月2018更新 (1809) 或更高版本上设置预览版 OpenXR runtime。  安装此应用后, Windows 应用商店会使运行时保持最新状态。
1. 从 "开始" 菜单运行 "混合现实 OpenXR" 开发人员预览版应用, 并按照说明操作, 使运行时处于活动状态。  不久, 此应用程序还允许浏览其他 OpenXR 调试信息。

![混合现实 OpenXR 开发者预览版应用](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>支持 Windows 10 十月2018更新

如果你运行的是 Windows 10 2019 更新 (1903), 并遵循上述步骤, 则应该已准备好使用混合现实 OpenXR 开发者预览版!

如果尚未准备好将[台式计算机升级到 "2019 年5月更新](https://www.microsoft.com/en-us/software-download/windows10)", 则可以通过以下步骤继续使用 Windows 10 10 月2018更新 (1809):

1. 按照上述步骤安装混合现实 OpenXR 开发者预览版。
1. 若要将混合现实 OpenXR 开发者预览版设置为系统的活动 OpenXR 运行时, 请安装[混合现实 OpenXR 开发者预览版兼容性包](https://aka.ms/openxr-compat)。

## <a name="building-a-sample-openxr-app"></a>生成示例 OpenXR 应用

[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp)项目演示了一个简单的 OpenXR 示例, 其中包含两个 Visual Studio 项目文件, 一个用于 Win32 桌面应用, 另一个用于 UWP HoloLens 2 应用。  由于解决方案包含一个 HoloLens UWP 项目, 因此需要在 Visual Studio 中安装[通用 Windows 平台开发工作负载](install-the-tools.md#installation-checklist)才能完全打开它。

请注意, 虽然 Win32 和 UWP 项目文件是独立的, 但由于打包和部署的不同, 每个项目中的应用代码都是 100%。

## <a name="feedback"></a>反馈

若要提供有关[OpenXR 临时0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)的反馈, 请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)、可[宽延时间 #openxr 频道](https://khr.io/slack)和[spec 问题跟踪](https://github.com/KhronosGroup/OpenXR-Docs/issues)器。

## <a name="troubleshooting"></a>疑难解答

下面是有关混合现实 OpenXR 开发者预览版的一些故障排除提示。  如果遇到任何其他问题, 请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)或[时差 #openxr 频道](https://khr.io/slack)。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 应用未启动 Windows Mixed Reality

如果 OpenXR 应用在运行时未启动 Windows Mixed Reality, 则混合现实 OpenXR 开发者预览版可能不会设置为活动运行时。  请务必运行混合现实 OpenXR 开发者预览版应用, 并按照说明操作, 使运行时处于活动状态。

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>无法安装混合现实 OpenXR 开发人员预览版应用 

请确保至少运行 Windows 10 十月2018更新 (1809)。  如果使用的是早期版本的 Windows 10, 则可以使用[windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)升级到2019更新 (1903)。

如果混合现实 OpenXR 开发者预览版应用上的 "安装" 按钮在 Windows 10 10 月2018更新上不执行任何操作, 则您的系统可能已缓存了应用的陈旧系统要求。  你可以从命令提示符`wsreset.exe`处运行命令来清除缓存。

## <a name="see-also"></a>请参阅

* [有关 OpenXR 的详细信息](https://www.khronos.org/openxr/)
* [OpenXR 临时0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR 临时 0.90 API 参考](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR 临时0.90 标头](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [OpenXR 临时0.90 快速参考指南](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
