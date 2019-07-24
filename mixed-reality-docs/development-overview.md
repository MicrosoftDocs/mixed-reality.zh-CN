---
title: 开发概述
description: 本文概述了开发 Windows Mixed Reality 应用的基本构建基块。
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 入门, 基础知识, HoloLens, HoloLens 2, 沉浸式耳机, unity, visual studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873978"
---
# <a name="development-overview"></a>开发概述

混合现实应用可以使用多种开发人员技术来开发。  HoloLens 运行通过[通用 Windows 平台](https://dev.windows.com/getstarted)生成的应用。  沉浸式耳机运行通用 Windows 平台应用和 Win32 应用程序。
熟悉 Unity 等中间件工具后, 就可以开始构建混合现实体验了。  利用开源[混合现实工具包](install-the-tools.md)快速入门。
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">混合现实服务</a>(如<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间锚</a>) 具有可集成到各种跨平台开发人员技术的 sdk。

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>混合现实开发基础知识

用于环境理解的 Windows 新功能支持[混合现实](mixed-reality.md)体验。 这使得开发者能够在现实世界中放置[全息影像](hologram.md)，并使用户可以通过实际在四处走动实现在数字世界中的移动。 

以下是混合现实开发的核心构建基块：

<table>
<tr>
<th>Input</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens（第一代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> <a href="gaze.md">头部凝视</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">眼睛凝视</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> 动手/<a href="gestures.md">手势</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">语音</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">手柄</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">运动控制器</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> 感知和空间功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens（第一代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">世界坐标</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">空间音效</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">空间映射</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



[HoloLens](hololens-hardware-details.md) 的基本交互模式是[凝视](gaze.md)、[手势](gestures.md)和[语音](voice-input.md)，有时也称为 GGV。 [Windows Mixed Reality 沉浸式头戴显示设备](immersive-headset-hardware-details.md)还使用凝视和语音，但是将[运动控制器](motion-controllers.md)换成手势。


所有基于 Windows 的混合现实设备都受益于适用于 Windows 的输入生态系统, 包括鼠标、键盘、gamepads 等。 对于 HoloLens，[硬件配件](hardware-accessories.md)通过蓝牙连接。 对于沉浸式头戴显示设备，配件通过蓝牙、USB 和其他受支持的协议连接到主机。

[坐标](coordinate-systems.md)、[空间音效](spatial-sound.md)和[空间映射](spatial-mapping.md)等环境理解特性为混合现实提供了必要的功能。 空间映射是 HoloLens 独有的，通过该映射，全息影像可与用户和周围的现实世界进行交互。 坐标系统支持用户的移动，以影响数字世界中的移动。

[全息影像](hologram.md)由光和声音组成, 它们依赖于[全息渲染](rendering.md)。 理解放置和持久性的体验（如 [Windows Mixed Reality 主页](navigating-the-windows-mixed-reality-home.md)（有时称为“shell”）中所示）是一种很好的体验用户体验的方式。

## <a name="tools-for-developing-for-mixed-reality"></a>开发混合现实的工具

你使用的工具取决于要生成的[应用样式](app-views.md)。
* [具有 2D 视图的应用](building-2d-apps.md)利用工具构建适用于 Windows Phone、电脑和平板电脑等环境的通用 Windows 平台应用。 这些应用在 Windows Mixed Reality 主页中以 2D 投影的形式呈现，可以在多种设备类型（包括手机和电脑）上运行。
* 沉浸式和全息式应用需要使用可以利用 Windows Mixed Reality API 的工具。 我们[推荐使用 Unity](unity-development-overview.md) 生成混合现实应用。 希望生成自己的引擎的开发人员可以[使用 DirectX 和其他 Windows API](directx-development-overview.md)。

无论要生成的应用为何种类型，这些工具都将有助于应用开发体验：
* [Visual Studio 和 Windows SDK](using-visual-studio.md)
* [Windows 设备门户](using-the-windows-device-portal.md)
* [HoloLens 模拟器](using-the-hololens-emulator.md)(HoloLens 2 模拟器即将推出)
* [Windows Mixed Reality 仿真器](using-the-windows-mixed-reality-simulator.md)
* [应用质量标准](app-quality-criteria.md)

## <a name="see-also"></a>请参阅
* [安装工具](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">混合现实服务</a>
* [混合现实教程](tutorials.md)
* [开源项目](open-source-projects.md)
* [MR 基础知识 100：Unity 入门](holograms-100.md)
* [Windows Mixed Reality 最小电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [向 Windows 应用商店提交应用程序](submitting-an-app-to-the-microsoft-store.md)
