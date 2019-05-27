---
title: OpenXR
description: 尝试临时 OpenXR 0.90 API 与混合现实 OpenXR 开发者预览版。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 混合的现实 OpenXR 开发者预览版
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039174"
---
# <a name="openxr"></a>OpenXR

OpenXR 是开放式的免版税的标准从[Khronos](https://www.khronos.org/)提供对各种设备的时间跨度的许多供应商从本机访问[混合的现实范围](mixed-reality.md)。

使用 OpenXR，您可以构建面向 holographic 设备 （如 HoloLens 2)，将数字内容放置在现实生活中，就好像确实存在，以及隐藏的沉浸式设备 （如桌面 Pc 的 Windows 混合现实耳机） 的应用程序物理世界并替换为数字的体验。  OpenXR 允许你编写代码后，然后可移植对多种硬件平台。

OpenXR 标准当前在临时阶段中，是与发布的反馈意见的初始 OpenXR 0.90 规范。  有关详细信息 OpenXR，包括对访问权限[临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)和[标头](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)，请参阅[Khronos OpenXR 页](https://www.khronos.org/openxr/)。 

您可以试用 HoloLens 2 或使用混合现实 OpenXR 开发者预览版台式计算机上的临时 OpenXR 0.90 API。  此早期的运行时，面向 OpenXR 0.90 API 的应用程序以面向 HoloLens 2 或 Windows Mixed Reality 沉浸式耳机在桌面上。

如果无法访问头戴式耳机，可以改为使用 HoloLens 2 仿真程序或 Windows 混合现实模拟器。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>设置 HoloLens 2 混合现实 OpenXR 开发者预览版

若要开始使用混合现实 OpenXR 开发者预览版 HoloLens 2 上：

1. 设置 HoloLens 2 或按照说明[安装 HoloLens 2 模拟器](using-the-hololens-emulator.md)。
1. 启动应用商店应用程序从设备或仿真程序中的，并确保更新所有应用。  这会使用该设备上的应用程序安装用于混合现实 OpenXR 开发者预览版。  如果使用模拟器，您将需要查阅[仿真程序输入说明](using-the-hololens-emulator.md#basic-emulator-input)可帮助你使用应用商店应用在仿真程序内的。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>设置沉浸式桌面耳机混合现实 OpenXR 开发者预览版

若要开始使用桌面 PC 上混合现实 OpenXR 开发者预览版：

1. 确保运行的 Windows 10 2018 年 10 月更新 (1809) 或 Windows 10 可能 2019年更新 (1903)。  如果您在早期版本的 Windows 10 上，你可以升级到 2019 年 5 使用更新[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)。
1. 设置 Windows 混合现实耳机或按照说明[启用 Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)。
1. 安装[混合的现实 OpenXR 开发人员预览应用](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。  此应用可帮助你使用预览版 OpenXR 运行时上设置 Windows 10 2018 年 10 月更新 (1809) 或更高版本。  安装此应用后，Windows 应用商店将保留在运行时保持最新。
1. 从开始菜单运行混合现实 OpenXR 开发者预览版应用并按照说明进行操作以使运行时处于活动状态。  很快，此应用会让您浏览以及其他 OpenXR 调试信息。

![混合的现实 OpenXR 开发人员预览应用](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>支持 Windows 10 2018 年 10 月更新

如果您在运行 Windows 10 2019 年 5 更新 (1903) 并按照上述步骤，你应该已准备好使用混合现实 OpenXR 开发者预览版 ！

如果您不准备[桌面 PC 升级到 2019 年 5 更新](https://www.microsoft.com/en-us/software-download/windows10)，您可以继续在 Windows 10 2018 年 10 月通过一个步骤来更新 (1809):

1. 按照上述步骤来安装混合现实 OpenXR 开发者预览版。
1. 若要将您的系统活动 OpenXR 运行时设置混合现实 OpenXR 开发者预览版，请安装[混合现实 OpenXR 开发人员预览版兼容性工具包](https://aka.ms/openxr-compat)。

## <a name="building-a-sample-openxr-app"></a>构建示例 OpenXR 应用

[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp)项目演示简单 OpenXR 示例由两个 Visual Studio 项目文件，一个同时 Win32 桌面应用程序，一个用于 UWP HoloLens 2 应用程序。  因为该解决方案包含 HoloLens UWP 项目，你将需要[通用 Windows 平台开发工作负载](install-the-tools.md#installation-checklist)安装在 Visual Studio 以完全将其打开。

请注意，尽管 Win32 和 UWP 项目文件是单独由于打包和部署，每个项目中的应用程序代码之间的差异是 100%相同 ！

## <a name="feedback"></a>反馈

若要提供有关反馈[OpenXR 临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)，请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)， [#openxr Slack 通道](https://khr.io/slack)和[规范问题跟踪程序](https://github.com/KhronosGroup/OpenXR-Docs/issues)。

## <a name="troubleshooting"></a>疑难解答

以下是有关混合现实 OpenXR 开发者预览版的一些故障排除提示。  如果在遇到任何其他问题，请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)或[#openxr Slack 通道](https://khr.io/slack)。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>未启动 Windows Mixed Reality OpenXR 应用

如果 OpenXR 应用未启动 Windows Mixed Reality 在运行时，混合现实 OpenXR 开发者预览版可能不会设置为活动的运行时。  请确保运行混合现实 OpenXR 开发者预览版应用并按照说明进行操作以使运行时处于活动状态。

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>混合的现实 OpenXR 开发者预览版应用无法在安装 

确保你至少运行 Windows 10 2018 年 10 月更新 (1809)。  如果您在早期版本的 Windows 10 上，你可以升级到 2019 年 5 更新 (1903) 使用[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)。

如果安装按钮上的混合现实 OpenXR 开发者预览版应用不会在 Windows 10 2018 年 10 月更新，您的系统已缓存应用程序的过时的系统要求。  可以运行命令`wsreset.exe`在命令提示符下，若要清除的缓存。

## <a name="see-also"></a>请参阅

* [OpenXR 的详细信息](https://www.khronos.org/openxr/)
* [OpenXR 临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR 临时 0.90 API 参考](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR 临时 0.90 标头](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [OpenXR 临时 0.90 快速参考指南](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
