---
title: 安装工具
description: 从此处开始为混合现实开发做准备。 本文始终反映最新版本的 Unity、Visual Studio 以及为进行 HoloLens 和 Windows Mixed Reality 沉浸式头戴显示设备开发推荐的其他工具。
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 最新, 工具, 入门, 基础, Unity, Visual Studio, 工具包
ms.openlocfilehash: 32dcda0eceb8d3717de7b2502d86f03cda975b8f
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66453725"
---
# <a name="install-the-tools"></a>安装工具

获取为 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备生成应用所需的工具。 Windows Mixed Reality 开发没有单独的 SDK；将使用 Visual Studio 和 Windows 10 SDK。

没有混合现实设备？ 可以安装 [HoloLens 仿真器](using-the-hololens-emulator.md)来测试混合现实应用的某些功能，而无需使用 HoloLens。 还可以使用 [Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)来测试用于沉浸式头戴显示设备的混合现实应用。

建议安装 Unity 游戏引擎，这是开始创建混合现实应用的最简单方法，但如果要使用自定义引擎，还可以针对 DirectX 进行生成。

>[!TIP]
>将此页面添加为书签并定期检查，以便及时了解推荐用于混合现实开发的每种工具的最新版本。

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>安装清单


| 工具 | 描述 | 注释 |
|---------|---------|---------|
| ![Windows 徽标](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>（手动安装链接）</a> | 安装最新版本的 Windows 10，以便电脑的操作系统与正在为其生成混合现实应用的平台匹配。 | **安装 Windows 10** <br> <ul><li>可以通过“设置”中的“Windows 更新”或通过创建安装介质（使用左栏中的链接）安装最新版本的 Windows 10。<li>有关每个 Windows 10 版本提供的最新混合现实功能的信息，请参阅[当前发行说明](release-notes-october-2018.md)。</ul> 通过“设置”>“更新和安全”>“对于开发人员”在电脑上启用开发人员模式  。 <br><br> 针对企业和企业托管电脑的注意事项：如果电脑由组织的 IT 部门管理，可能需要与他们联系才能进行更新  。 <br><br> Windows 的“N”版本  ：Windows 的“N”版本不支持 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备。 |
| ![Visual Studio 徽标](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>（安装链接）</a> | 适用于 Windows 等的功能齐全的集成开发环境 (IDE)。 将使用 Visual Studio 来编写代码、调试、测试和部署。 | **要安装的工作负载：** <ul><li>使用 C++ 的桌面开发</li><li>通用 Windows 平台开发</li></ul>**有关 Unity 的说明：** 除非有意出于特定目的安装较新（非 LTS）版本的 Unity，建议不要将 Unity 工作负载作为 Visual Studio 安装的一部分进行安装，而是安装下文所述的 2018.4 LTS Unity 流  。<br> <br>**注意：** 目前，在 Visual Studio 2019 中进行混合现实开发存在一些已知问题。  目前，我们建议继续使用 Visual Studio 2017。 |
| ![Windows 徽标](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>（手动安装链接）</a> | 提供用于在 HoloLens 2 上生成 Windows 10 应用的最新标头、库、元数据和工具。 | 若要生成 HoloLens 2 应用，需要安装 Windows SDK、内部版本 18362 或更高版本。<br> <br> 如果仅针对桌面 Windows Mixed Reality 头戴显示设备或 HoloLens（第 1 代）开发应用，则可以使用 Visual Studio 2017 安装的 Windows SDK。 |
| ![Visual Studio 徽标](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2087187" target="_blank">**HoloLens 2 仿真器**<br>（安装链接：10.0.18362.1005)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens（第 1 代）仿真器**<br>（安装链接：10.0.17763.253)</a> | 使用仿真器，可在没有 HoloLens 的情况下在 HoloLens 虚拟机映像上运行应用。<br> <br> 此安装包还包括适用于 Visual Studio 的全息 DirectX 项目模板。 | 有关如何开始使用仿真器的详细信息，请参阅[使用 HoloLens 仿真器](using-the-hololens-emulator.md)。<br> <br> 系统必须支持 Hyper-V 才能成功安装仿真器  。 有关详细信息，请参阅下面的“系统要求”部分。 如果需要，可以选择仅安装模板而不安装仿真器。<br>|
| ![Unity 徽标](images/unity_logo.png)<br><br><a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">**Unity 2018.4**<br>（安装链接）</a> | 使用 Unity 游戏引擎是创建混合现实体验的最简单方法，它本身即支持 Windows Mixed Reality 功能。 | 通常建议使用 Unity LTS（长期支持）流，它是启动新项目的最佳版本，更新到其最新版本可获取最新的稳定修补程序。<br> <br>目前的建议是使用“Unity 2018.4.x”，这是下文的 MRTK v2 所需的 LTS 版本  。<br> <br>出于特定原因，一些开发人员可能需要使用不同版本的 Unity。 对于这些情况，Unity 支持并行安装不同版本。 |
| ![MRTK 徽标](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**适用于 Unity 的混合现实工具包 (MRTK v2)** </a> | 适用于 Unity 的 MRTK v2 是一款面向混合现实应用程序的开源跨平台开发套件。<br><br> MRTK v2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序的开发。 该项目旨在降低创建混合现实应用程序的门槛，并在我们共同成长的过程中回馈社区。 | 有关 MRTK v2 的详细信息，请访问项目的 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">GitHub wiki</a>。 |


## <a name="mixed-reality-toolkit"></a>混合现实工具包

混合现实工具包提供的组件和功能旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 头戴显示设备和 OpenVR 平台的应用程序的开发。 该项目旨在降低创建混合现实应用程序的门槛，并在我们共同成长的过程中回馈社区。
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit Unity</a> - 使用基本工具包中的代码，使其更易于在 Unity 中使用。
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> -代码位和组件可能无法直接在 HoloLens 或沉浸式 (VR) 头戴显示设备上运行，而可通过与它们配对生成面向 Windows Mixed Reality 的体验。

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>设置电脑以进行混合现实

Windows 10 SDK 在 Windows 10 操作系统上效果最佳。 Windows 8.1、Windows 8、Windows 7、Windows Server 2012、Windows Server 2008 R2 也支持此 SDK。 请注意，并非所有工具都在较早的操作系统上受支持。 

### <a name="for-hololens-development"></a>对于 HoloLens 开发

在为进行 HoloLens 开发设置开发电脑时，请确保该电脑满足 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 和 <a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a> 的系统要求。 如果你打算使用 HoloLens（第 1 代）仿真器，还需要确保电脑满足 [HoloLens 仿真器系统要求](using-the-hololens-emulator.md#hololens-emulator-system-requirements)。

若要开始使用 HoloLens 仿真器，请参阅[使用 HoloLens 仿真器](using-the-hololens-emulator.md)。

如果计划针对 HoloLens 和 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备进行开发，请使用以下部分中的系统建议和要求。

### <a name="for-immersive-vr-headset-development"></a>对于沉浸式 (VR) 头戴显示设备开发

>[!NOTE]
>以下指南是针对沉浸式 (VR) 头戴显示设备开发电脑的当前最低规范和建议规范，可能会定期更新  。

>[!WARNING]
>不要将此与[最低电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)混淆，后者概述了面向沉浸式 (VR) 头戴显示设备应用或游戏时的使用者电脑规范  。

如果沉浸式头戴显示设备开发电脑没有全尺寸 HDMI 和/或 USB 3.0 端口，则需要[适配器](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)才能连接头戴显示设备。

某些硬件配置当前具有[已知问题](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)，尤其是具有混合图形的笔记本。

<table>
<tr>
<th></th><th> 最低配置</th><th> 推荐</th>
</tr><tr>
<td> 处理器</td><td> <b>笔记本：</b>Intel 移动 Core i5 第 7 代 CPU，双核超线程 <b>桌面：</b>Intel 桌面 i5 第 6 代 CPU，双核超线程或<b></b> AMD FX4350 4.2Ghz 四核等效 CPU</td><td> <b>桌面：</b>Intel 桌面 i7 第 6 代（6 核）或<b></b> AMD Ryzen 5 1600（6 核，12 线程）</td>
</tr><tr>
<td> GPU</td><td> <b>笔记本：</b>NVIDIA GTX 965M、AMD RX 460M (2GB) 等效或更高版本支持 DX12 的 GPU <b>桌面：</b>NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) 等效或更高版本支持 DX12 的 GPU</td><td><b>桌面：</b>NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) 等效或更高版本支持 DX12 的 GPU</td>
</tr><tr>
<td> GPU 驱动程序 WDDM 版本</td><td colspan="2"> WDDM 2.2 驱动程序</td>
</tr><tr>
<td> 散热设计功耗</td><td colspan="2"> 15W 或更高</td>
</tr><tr>
<td> 图形显示端口</td><td colspan="2"> 1 个可用于头戴显示设备的图形显示端口（适用于 60Hz 头戴显示设备的 HDMI 1.4 或 DisplayPort 1.2、适用于 90Hz 头戴显示设备的 HDMI 2.0 或 DisplayPort 1.2）</td>
</tr><tr>
<td> 显示器分辨率</td><td colspan="2"> 解决方案：SVGA (800x600) 或更高位深度：每个像素的 32 位颜色</td>
</tr><tr>
<td> 内存</td><td> 8 GB 或更高的 RAM</td><td> 16 GB 或更高的 RAM</td>
</tr><tr>
<td> 存储</td><td colspan="2"> &gt;10 GB 的额外可用空间</td>
</tr><tr>
<td> USB 端口</td><td colspan="2"> 1 个可用于头戴显示设备的 USB 端口 (USB 3.0 Type-A) <b>注意：USB 必须提供至少 900mA</b></td>
</tr><tr>
<td> 蓝牙</td><td colspan="2"> 蓝牙 4.0（用于连接配件）</td>
</tr>
</table>

## <a name="see-also"></a>另请参阅

* [开发概述](development-overview.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [使用 Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)
* [Unity 开发概述](unity-development-overview.md)
* [DirectX 开发概述](directx-development-overview.md)
* [HoloLens 仿真器存档](hololens-emulator-archive.md)
