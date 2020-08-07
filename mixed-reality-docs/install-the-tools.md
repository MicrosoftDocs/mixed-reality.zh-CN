---
title: 安装工具
description: 从此处开始为混合现实开发做准备。 本文始终反映最新版本的 Unity、Visual Studio 以及为进行 HoloLens 和 Windows Mixed Reality 沉浸式头戴显示设备开发推荐的其他工具。
author: thetuvix
ms.author: alexturn
ms.date: 07/31/2020
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, Unity, Visual Studio, 工具包
ms.openlocfilehash: f5c779aa0bb89fe66b53419b03ec1b4d3e6b562b
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476882"
---
# <a name="install-the-tools"></a>安装工具

获取为 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备生成应用程序所需的工具。 Windows Mixed Reality 开发没有单独的 SDK；将使用 Visual Studio 和 Windows 10 SDK。

没有混合现实设备？ 可以安装 [HoloLens 仿真器](using-the-hololens-emulator.md)来测试混合现实应用的某些功能，而无需使用 HoloLens。 还可以使用 [Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)来测试用于沉浸式头戴显示设备的混合现实应用。 如果你使用的是 Unity，则可以使用[混合现实工具包 (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity) 的输入模拟来测试各种类型的输入交互，例如手势跟踪和眼动跟踪输入。

建议安装 Unity 游戏引擎，这是开始创建混合现实应用的最简单方法。 不过，如果你想要使用自定义引擎，则也可以针对 DirectX 生成应用。

>[!TIP]
>将此页面添加为书签并定期检查，以便及时了解推荐用于混合现实开发的每种工具的最新版本。

<br>

## <a name="installation-checklist"></a>安装清单


| 工具 | 注释 |
|---------|---------|
| ![Windows 徽标](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**（手动安装链接）</a><br><br>安装最新版本的 Windows 10，以便电脑的操作系统与正在为其生成混合现实应用程序的平台匹配。  | **安装 Windows 10** <br> 可以通过“设置”中的“Windows 更新”，或者使用左栏中的链接创建安装媒体，来安装最新版本的 Windows 10。 <br><br>有关每个 Windows 10 版本提供的最新混合现实功能的信息，请参阅[当前发行说明](release-notes-october-2018.md)。 通过“设置”>“更新和安全”>“对于开发人员”在电脑上启用开发人员模式。 <br><br> **企业和公司管理电脑的注意事项**<br>如果你的电脑由组织的 IT 部门管理，可能需要与他们联系才能进行更新。 <br><br> **Windows 的“N”版本**<br> Windows 的“N”版本不支持 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备。 |
| ![Visual Studio 徽标](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019（16.2 或更高版本）** （安装链接）</a> <br><br>适用于 Windows 等的功能齐全的集成开发环境 (IDE)。 将使用 Visual Studio 来编写代码、调试、测试和部署。 | 请确保安装以下工作负载： <br><br>**● 使用 C++ 的桌面开发**<br>**● 通用 Windows 平台 (UWP) 开发**<br><br>在 UWP 工作负载内，如果要针对 HoloLens 进行开发，请务必选中以下可选组件：<br><br>**● USB 设备连接**<br><br>**有关 Unity 的注意事项**<br>除非你出于特定目的有意尝试安装较新（非 LTS）版本的 Unity，否则我们建议不要将 Unity 工作负载作为 Visual Studio 安装的一部分进行安装，而是安装下文所述的 Unity 2019 LTS 流。<br><br>**注意**<br>在 Visual Studio 2019 版本16.0 中调试混合现实应用时存在一些已知问题。  请确保更新到 Visual Studio 2019 版本 16.2 或更高版本。 |
| ![Windows 徽标](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** （手动安装链接）</a> <br><br>提供用于在 HoloLens 2 上生成 Windows 10 应用的最新标头、库、元数据和工具。 | **要生成 HoloLens 2 应用，必须安装 Windows SDK 内部版本 18362 或更高版本。**<br> <br> 如果仅针对桌面 Windows Mixed Reality 头戴显示设备或 HoloLens（第 1 代）开发应用程序，则可以使用 Visual Studio 2017 安装的 Windows SDK。 |
| ![Visual Studio 徽标](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2132415" target="_blank">**HoloLens 2 仿真器（Windows 全息版 2004，2020 年 6 月更新）** （安装链接：10.0.19041.1106）</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens（第一代）仿真器**（安装链接：10.0.17763.134）</a> <br><br>使用仿真器可在没有 HoloLens 的情况下在 HoloLens 虚拟机映像上运行应用程序。<br> <br> | 有关如何开始使用仿真器的详细信息，请参阅[使用 HoloLens 仿真器](using-the-hololens-emulator.md)。<br> <br> 系统必须支持 Hyper-V 才能成功安装仿真器。 有关详细信息，请参阅下面的“系统要求”部分。 <br>|

## <a name="choose-your-engine"></a>选择你的引擎

你现在已将 Windows 10、Visual Studio 和 Windows 10 SDK 准备好了，接下来选择一个引擎用于构建。 

[!INCLUDE[](~/includes/tools-overview.md)]
