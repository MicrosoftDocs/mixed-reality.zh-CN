---
title: 开发概述
description: 本文概述了开发 Windows Mixed Reality 应用的基本构建基块。
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 获取已启动，基础知识，HoloLens，HoloLens 2 沉浸式头戴式耳机、 unity、 visual studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873978"
---
# <a name="development-overview"></a>开发概述

混合的现实应用程序可以使用各种开发人员技术进行开发。  HoloLens 运行使用生成的应用[通用 Windows 平台](https://dev.windows.com/getstarted)。  沉浸式耳机运行通用 Windows 平台应用程序，以及 Win32 应用程序。
通过获取熟悉 Unity 之类的中间件工具，可以开始的构建混合的现实体验今天。  利用开放源代码[混合现实工具包](install-the-tools.md)快速入门。
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">混合现实服务</a>，如<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>，已可以将集成到各种跨平台开发人员技术的 Sdk。

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>混合的现实开发的基础知识

[混合现实](mixed-reality.md)体验之外的环境了解新的 Windows 功能。 这使开发人员能够将放[全息图](hologram.md)在现实生活中，并允许用户按原义的每个步骤有关数字世界的推进。 

以下是混合的现实开发核心构建基块：

<table>
<tr>
<th>Input</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> <a href="gaze.md">Head 的视线移动</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">关注的视线移动</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> 手 /<a href="gestures.md">手势</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">Voice</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">运动控制器</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> 认知和空间功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">世界坐标</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">空间音效</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">空间映射</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



基本交互模型[HoloLens](hololens-hardware-details.md)是[注视](gaze.md)，[手势](gestures.md)，以及[语音](voice-input.md)，有时称为*GGV*. [Windows Mixed Reality 沉浸式耳机](immersive-headset-hardware-details.md)还使用视线移动和语音，但交换[动作控制器](motion-controllers.md)笔势。


到 Windows，包括鼠标、 键盘、 游戏板，和的详细信息，所有基于 Windows 的混合的现实设备受益于可用的输入生态系统。 HoloLens，与[硬件附件](hardware-accessories.md)通过蓝牙连接。 沉浸式耳机，使用附件连接到宿主 PC 通过蓝牙、 USB 和其他支持的协议。

环境了解功能，例如[坐标](coordinate-systems.md)，[空间声音](spatial-sound.md)，并[空间映射](spatial-mapping.md)混合现实提供必要的功能。 空间映射是唯一的 HoloLens，并启用全息与用户和其周围的物理世界进行交互。 坐标系统允许用户的移动，以影响数字世界中的移动。

[全息](hologram.md)发出的光线和声音，后者又依赖于[全息呈现](rendering.md)。 了解放置和持久性的体验，如中所示[Windows Mixed Reality 家庭](navigating-the-windows-mixed-reality-home.md)（有时称为"shell"） 一个不错方法使您自己接地中的用户体验。

## <a name="tools-for-developing-for-mixed-reality"></a>用于混合现实的开发工具

将取决于您使用的工具[样式的应用](app-views.md)你想要生成。
* [使用二维视图应用](building-2d-apps.md)利用工具，用于构建通用 Windows 平台应用程序适用于 Windows Phone、 PC 和平板电脑等环境。 这些应用为 2D 投影置于 Windows Mixed Reality 主页、 方面具有丰富经验，并可以跨多个设备类型 （包括手机和 PC） 工作。
* 沉浸式和全息版的应用需要旨在充分利用 Windows 混合现实 Api 的工具。 我们[建议使用 Unity](unity-development-overview.md)构建混合的现实应用程序。 开发人员热衷于构建他们自己引擎可以[使用 DirectX 和其他 Windows Api](directx-development-overview.md)。

无论您正在构建的应用程序的类型，这些工具有助于您应用的开发体验：
* [Visual Studio 和 Windows SDK](using-visual-studio.md)
* [Windows 设备门户](using-the-windows-device-portal.md)
* [HoloLens 模拟器](using-the-hololens-emulator.md)（即将推出的 HoloLens 2 仿真程序）
* [Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)
* [应用质量标准](app-quality-criteria.md)

## <a name="see-also"></a>请参阅
* [安装工具](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">混合的现实服务</a>
* [混合的现实教程](tutorials.md)
* [开放源代码项目](open-source-projects.md)
* [MR 基础知识 100：Unity 入门](holograms-100.md)
* [Windows Mixed Reality 最小 PC 硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [提交到 Windows 应用商店应用](submitting-an-app-to-the-microsoft-store.md)
