---
title: OpenXR
description: 尝试临时 OpenXR 0.90 API 与混合现实 OpenXR 开发者预览版。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 混合的现实 OpenXR 开发者预览版
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592752"
---
# <a name="openxr"></a>OpenXR

OpenXR 是开放式的免版税的标准从[Khronos](https://www.khronos.org/)提供对各种设备的时间跨度的许多供应商从本机访问[混合的现实范围](mixed-reality.md)。

使用 OpenXR，您可以构建面向 holographic 设备 （如 HoloLens 2)，将数字内容放置在现实生活中，就好像确实存在，以及隐藏的沉浸式设备 （如桌面 Pc 的 Windows 混合现实耳机） 的应用程序物理世界并替换为数字的体验。  OpenXR 允许你编写代码后，然后可移植对多种硬件平台。

OpenXR 标准当前在临时阶段中，是与发布的反馈意见的初始 OpenXR 0.90 规范。  有关详细信息 OpenXR，包括对访问权限[临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)和[标头](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)，请参阅[Khronos OpenXR 页](https://www.khronos.org/openxr/)。

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a>设置混合现实 OpenXR 开发者预览版

您可以尝试立即使用混合现实 OpenXR 开发者预览版临时 OpenXR 0.90 API。  此早期的运行时，定位到桌面上的目标 Windows Mixed Reality 沉浸式耳机 OpenXR 0.90 API 的应用程序。  如果无法访问头戴式耳机，可以改为使用 Windows 混合现实模拟器。

若要开始使用混合现实 OpenXR 开发者预览版：

1. 确保你至少运行 Windows 10 2018 年 10 月更新。  如果您在早期版本的 Windows 10 上，你可以升级到 2018 年 10 月更新使用[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)。  如果您感到大胆，则可以安装[Windows 10 Insider Preview 生成](https://insider.windows.com)。
1. 设置 Windows 混合现实耳机或按照说明[启用 Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)。
1. 安装[混合的现实 OpenXR 开发人员预览应用](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。  此应用可帮助你在 Windows 上使用预览 OpenXR 运行时设置了 10 2018 年 10 月更新或更高版本。  安装此应用后，Windows 应用商店将保留在运行时保持最新。
1. 从开始菜单运行混合现实 OpenXR 开发者预览版应用并按照说明进行操作以使运行时处于活动状态。  很快，此应用会让您浏览以及其他 OpenXR 调试信息。

![混合的现实 OpenXR 开发人员预览应用](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a>支持 Windows 10 2018 年 10 月更新

若要开始使用混合现实 OpenXR 开发者预览版在 Windows 10 2018 年 10 月更新 （Windows 的当前版本），将需要遵循几个步骤：

1. 按照上述步骤来安装混合现实 OpenXR 开发者预览版。
1. 若要将您的系统活动 OpenXR 运行时设置混合现实 OpenXR 开发者预览版，请安装[混合现实 OpenXR 开发人员预览版兼容性工具包](https://aka.ms/openxr-compat)。

## <a name="building-a-test-openxr-app"></a>构建测试 OpenXR 应用

[Hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR 测试应用程序说明如何使用 API 的各个部分。  您可以按照以下[构建说明](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md)，这将生成测试应用程序和 OpenXR 标头本身。

## <a name="feedback"></a>反馈

若要提供有关反馈[OpenXR 临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)，请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)， [#openxr Slack 通道](https://khr.io/slack)和[规范问题跟踪程序](https://github.com/KhronosGroup/OpenXR-Docs/issues)。

## <a name="troubleshooting"></a>疑难解答

以下是有关混合现实 OpenXR 开发者预览版的一些故障排除提示。  如果在遇到任何其他问题，请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)或[#openxr Slack 通道](https://khr.io/slack)。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>未启动 Windows Mixed Reality OpenXR 应用

如果 OpenXR 应用未启动 Windows Mixed Reality 在运行时，混合现实 OpenXR 开发者预览版可能不会设置为活动的运行时。  请确保运行混合现实 OpenXR 开发者预览版应用并按照说明进行操作以使运行时处于活动状态。

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>混合的现实 OpenXR 开发者预览版应用无法在安装 

确保你至少运行 Windows 10 2018 年 10 月更新。  如果您在早期版本的 Windows 10 上，你可以升级到 2018 年 10 月更新使用[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)。

如果安装按钮上的混合现实 OpenXR 开发者预览版应用不会在 Windows 10 2018 年 10 月更新，您的系统已缓存应用程序的过时的系统要求。  可以运行命令`wsreset.exe`在命令提示符下，若要清除的缓存。

## <a name="see-also"></a>请参阅

* [OpenXR 的详细信息](https://www.khronos.org/openxr/)
* [OpenXR 临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR 临时 0.90 API 参考](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR 临时 0.90 标头](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
