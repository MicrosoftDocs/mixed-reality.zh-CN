---
title: 安装工具
description: 从这里开始，若要准备用于混合的现实开发。 这篇文章应始终反映最新版本的 Unity、 Visual Studio 中，以及建议用于 HoloLens 和 Windows Mixed Reality 的沉浸式头戴式开发其他工具。
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
keywords: 保持最新工具，开始，基础知识、 unity、 visual studio、 工具包
ms.openlocfilehash: da924d98f6869fadb9736000f666616f1372faa3
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593072"
---
# <a name="install-the-tools"></a>安装工具

获取 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 耳机构建应用程序所需的工具。 没有任何单独的 SDK 的 Windows Mixed Reality 开发;Windows 10 sdk，您将使用 Visual Studio。

没有混合的现实设备？ 你可以安装[HoloLens （第 1 代） 模拟器](using-the-hololens-emulator.md)来测试某些功能而无需 HoloLens 混合的现实应用。 此外可以使用[Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)来测试混合的现实应用程序以通过沉浸式耳机。

> [!NOTE]
> 特定于 HoloLens 2 仿真程序的更多指导[即将推出](index.md#news-and-notes)。

我们建议安装 Unity 游戏引擎，如最简单的方法，以开始创建混合现实应用，但是，您还可以构建针对 DirectX 如果想要使用自定义引擎。

>[!TIP]
>此页加入书签，并检查其定期掌握最新的每个建议混合的现实的开发工具的最新版本。

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>安装核对清单


| Tool | 描述 | 说明 |
|---------|---------|---------|
| ![Windows 徽标](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>（手动安装链接）</a> | 安装最新版本的 Windows 10，因此您的 PC 的操作系统匹配你在为其构建混合的现实应用的平台。 | **安装 Windows 10** <br> <ul><li>在设置或通过创建安装介质 （使用左侧列中的链接），可以安装 Windows 10 通过 Windows Update 的最新版本。<li>请参阅[当前发行说明](release-notes-october-2018.md)有关最新信息与每个版本的 Windows 10 混合现实功能可用。</ul> **启用您的 PC 上的开发人员模式**设置 > 更新和安全 > 面向开发人员。 <br><br> **针对企业和公司管理的电脑的说明：** 如果您的 PC 由你组织的 IT 部门可能需要与他们联系以更新。 <br><br> **N 的 Windows 版本：** 在 n 个版本的 Windows 上不支持 Windows Mixed Reality 沉浸式 (VR) 耳机。 |
| ![Visual Studio 徽标](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>（安装链接）</a> | Windows 和的详细信息的功能完备的集成的开发环境 (IDE)。 将使用 Visual Studio 来编写代码、 调试、 测试和部署。 | **若要安装的工作负荷：** <ul><li>使用的桌面开发C++</li><li>通用 Windows 平台开发</li></ul>**有关 Unity 的说明：** 除非有意尝试为特定目的安装 Unity 的较新 (非 LTS) 版本，否则我们建议*不*作为 Visual Studio 安装的一部分安装的 Unity 工作负载以及改为安装 2018.3 LTSUnity 所指出的下面的流。<br> <br>**注意：** 有一些已知的问题和混合的现实开发 Visual Studio 2019 那一刻。  现在，我们建议你继续使用 Visual Studio 2017。 |
| ![Windows 徽标](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windowsinsiderpreviewSDK" target="_blank">**Windows SDK Insider Preview 18362**<br>（手动安装链接）</a> | 用于生成 HoloLens 2 上的 Windows 10 应用中提供的最新的标头、 库、 元数据和工具。 | 若要构建 HoloLens 2 应用程序，你将需要<a href="https://insider.windows.com">成为 Windows 预览体验</a>并安装 Windows SDK Insider Preview，生成 18362 或更高版本。<br> <br> 如果您仅要开发适用于桌面 Windows Mixed Reality 耳机或 HoloLens 应用 （第 1 代），可以使用 Visual Studio 2017 安装的 Windows SDK。 |
| ![Visual Studio 徽标](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens （第 1 代） 仿真程序和全息版的项目模板**<br>(安装链接：10.0.17763.253)</a> | 该模拟器允许您在 HoloLens 上运行应用 （第 1 代） 而无需物理 HoloLens 的虚拟机映像。<br> <br> 此包还包括用于 Visual Studio 全息版的 DirectX 项目模板。 | 请参阅[使用 HoloLens 模拟器](using-the-hololens-emulator.md)有关如何开始使用仿真程序的详细信息。<br> <br> **您的系统必须支持 HYPER-V**仿真程序安装成功。 请参考下面的详细信息的系统要求部分。 如果需要，您可以选择安装模拟器的情况下的模板。<br> <br> 是特定于 HoloLens 2 仿真程序的更多指导[即将推出](index.md#news-and-notes)。 |
| ![Unity 徽标](images/unity_logo.png)<br><br><a href="https://unity3d.com/get-unity/download" target="_blank">**Unity 2018.3**<br>（安装链接）</a> | Unity 游戏引擎是创建混合的现实体验 Windows Mixed Reality 功能的内置支持的最简单方法。 | 我们通常建议 Unity LTS （长术语支持） 流作为启动新项目，要使用的最佳版本更新到其最新版本以获取最新稳定的修补程序。<br> <br> 目前的建议是使用**Unity 2018.3.x**、 需要的下面，MRTK v2 和这很快就会 Unity 的 2018 LTS 生成。 <br> <br> 一些开发人员可能想要使用的特定原因 Unity 的不同版本。 对于这些情况下，Unity 支持不同版本的并行的安装。 |
| ![MRTK 徽标](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**用于 Unity 的混合的现实工具包 (MRTK v2)**</a> | Unity 的 MRTK v2 是混合的现实应用程序的一个开放源代码跨平台开发工具包。<br><br> MRTK v2 旨在加速开发针对 Microsoft HoloLens，Windows Mixed Reality 沉浸式 (VR) 耳机，以及 OpenVR 平台的应用程序。 项目旨在减少条目来创建混合的现实应用程序和参与到社区，我们都增长。 | 了解有关 MRTK v2 的访问项目的详细<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">GitHub wiki</a>。 |


## <a name="mixed-reality-toolkit"></a>混合的现实工具包

混合现实工具包提供的用于加速开发针对 Microsoft HoloLens，Windows Mixed Reality 耳机，以及 OpenVR 平台的应用程序组件和功能。 项目功能旨在减少到条目创建混合的现实应用程序并提供回社区，随着我们所有的发展的障碍。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit Unity</a> -使用基本的工具包中的代码并使其更轻松地在 Unity 中使用。
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> -bits 和组件可能无法直接在 HoloLens 或沉浸式的 (VR) 耳机运行的代码，但改为要生成与它们对体验面向 Windows Mixed Reality。

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>设置您的 PC 以混合的现实开发

Windows 10 SDK Windows 10 操作系统上运行最佳。 此 SDK 还支持在 Windows 8.1、 Windows 8、 Windows 7、 Windows Server 2012、 Windows Server 2008 R2 上。 请注意，并非所有工具都支持较早的操作系统。 

### <a name="for-hololens-development"></a>有关 HoloLens 开发

在设置用于 HoloLens 开发进行开发的电脑，请确保其满足两个的系统要求<a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a>并<a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>。 如果你打算使用 HoloLens （第 1 代） 仿真程序中，你将想要确保你的 PC 满足[HoloLens 的模拟器系统要求](using-the-hololens-emulator.md#hololens-emulator-system-requirements)也。

若要开始使用 HoloLens （第 1 代） 仿真程序中，请参阅[使用 HoloLens 模拟器](using-the-hololens-emulator.md)。

> [!NOTE]
> HoloLens 2 在仿真程序的更多指导[即将推出](index.md#news-and-notes)。

如果你打算为 HoloLens 和 Windows Mixed Reality 沉浸式的 (VR) 耳机开发，请在下面的部分中使用的系统建议和要求。

### <a name="for-immersive-vr-headset-development"></a>沉浸式 (VR) 耳机开发

>[!NOTE]
>以下准则非常令人着迷的 (VR) 耳机当前的最低和推荐规格*开发 PC*，并且可能会定期更新。

>[!WARNING]
>请勿将此与[最小的 PC 的硬件兼容性指导方针](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)，其中概述了*使用者 PC 规格*应面向沉浸式 (VR) 耳机式应用程序或游戏。

如果您的沉浸式头戴式开发 PC 没有大 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)连接您的头戴式。

目前，有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)某些硬件配置，尤其是对于具有混合图形的笔记本。

<table>
<tr>
<th></th><th> 最低要求</th><th> 推荐</th>
</tr><tr>
<td> 处理器</td><td> <b>Notebook:</b>Intel 移动 Core i5 第 7 个代 CPU，使用超线程的双核<b>桌面：</b>Intel 桌面 i5 第六代 CPU、 了超线程的双核<b>或</b>AMD FX4350 4.2 Ghz 四核等效项</td><td> <b>桌面：</b>桌面 Intel i7 第六代 （6 核）<b>或</b>AMD Ryzen 5 1600 （6 核，12 个线程）</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b>NVIDIA GTX 965 M、 AMD RX 460 M (2GB) 等效或更高版本 DX12 支持 GPU<b>桌面：</b>NVIDIA GTX 960/1050、 AMD Radeon RX 460 (2GB) 等效或更高版本 DX12 支持 GPU</td><td><b>桌面：</b>NVIDIA GTX 980/1060，AMD Radeon RX 480 (2GB) 等效或更高版本 DX12 支持 GPU</td>
</tr><tr>
<td> WDDM 的 GPU 驱动程序版本</td><td colspan="2"> WDDM 2.2 驱动程序</td>
</tr><tr>
<td> 热感设计电源</td><td colspan="2"> 15W 或更高版本</td>
</tr><tr>
<td> 图形显示端口</td><td colspan="2"> 1 个可用的图形显示端口&#160;耳机 （HDMI 1.4 或 60 Hz 耳机，HDMI 2.0 或 90 Hz 耳机的 DisplayPort 1.2 的 DisplayPort 1.2）</td>
</tr><tr>
<td> 显示器分辨率</td><td colspan="2"> 解决方案：SVGA (800 x 600) 或更高版本的位深度：每个像素的 32 位颜色</td>
</tr><tr>
<td> 内存</td><td> 8&#160;GB 的 RAM 或更高版本</td><td> 16 GB 的 RAM 或更高版本</td>
</tr><tr>
<td> 存储</td><td colspan="2"> &gt;10 GB 的额外可用空间</td>
</tr><tr>
<td> USB 端口</td><td colspan="2"> 1 个可用的 USB 耳机 (USB 3.0 Type-A) 的端口<b>注意：USB 必须提供一个最少为 900mA</b></td>
</tr><tr>
<td> 蓝牙</td><td colspan="2"> 蓝牙 4.0 （适用于附件连接）</td>
</tr>
</table>

## <a name="see-also"></a>请参阅

* [开发概述](development-overview.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [使用 Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)
* [Unity 开发概述](unity-development-overview.md)
* [DirectX 开发概述](directx-development-overview.md)
* [HoloLens 仿真器存档](hololens-emulator-archive.md)
