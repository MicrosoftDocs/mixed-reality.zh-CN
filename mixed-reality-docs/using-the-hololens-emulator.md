---
title: 使用 HoloLens 仿真程序
description: HoloLens 仿真程序，可测试在您的 PC 而无需物理 HoloLens 混合的现实应用程序。
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、 仿真程序
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592862"
---
# <a name="using-the-hololens-emulator"></a>使用 HoloLens 仿真程序

HoloLens 仿真程序允许您测试您的 PC 而无需物理 HoloLens 上全息版应用，并附带了 HoloLens 开发工具集。 在仿真程序使用的 HYPER-V 虚拟机。 通常会在 HoloLens 上传感器读取的人和环境输入改为模拟使用键盘、 鼠标或 Xbox 控制器。 应用程序无需修改即可在模拟器上运行，并不知道它们不实际 HoloLens 上运行。

如果想要为桌面 Pc 开发 Windows Mixed Reality 沉浸式 (VR) 耳机式应用程序或游戏，请查看[Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)，它可让你改为模拟桌面耳机。

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。

## <a name="installing-the-hololens-emulator"></a>安装 HoloLens 仿真程序

下载[HoloLens （第 1 代） 仿真程序和全息版的项目模板](https://go.microsoft.com/fwlink/?linkid=2065980)。

可以找到较旧版本的 HoloLens 模拟器[HoloLens 仿真器存档](hololens-emulator-archive.md)页。

### <a name="hololens-emulator-system-requirements"></a>HoloLens 的模拟器系统要求

HoloLens 仿真程序依赖于使用 HYPER-V 和使用 RemoteFx 的硬件加速图形。 若要使用模拟器，请确保您的 PC 满足以下硬件要求：
* 64 位 Windows 10 Pro、 Enterprise 或教育版 
    >[!NOTE]
    >Windows 10 家庭版不支持的 HYPER-V 或 HoloLens 仿真程序
* 64 位 CPU
* CPU 具有 4 个核心 （或多个 Cpu 总容量为 4 个核心）
* 8 GB 的 RAM 或更多
* 必须在 BIOS 中，以下功能[支持且启用了](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * 硬件辅助虚拟化
   * 二级地址转换 (SLAT)
   * 基于硬件的数据执行保护 (DEP)
* GPU 要求 （仿真程序可能使用不受支持的 GPU，但会显著变慢）
   * DirectX 11.0 或更高版本
   * WDDM 1.2 驱动程序或更高版本

如果你的系统满足上述要求**请确保你的系统上是否已启用"HYPER-V"功能**通过控制面板-> 程序-> 程序和功能-> 上的启用 Windows 功能或关闭-> 确保"HYPER-V"选择用于仿真程序的安装才能成功。

### <a name="installation-troubleshooting"></a>安装故障排除

在安装所需的仿真程序时，可能会出错 *"Visual Studio 2015 Update 1 和 UWP 工具版本 1.2"*。 有三个可能导致此错误的原因：
* 没有足够新版本的 Visual Studio （Visual Studio 2017 或 Visual Studio 2015 Update 1 或更高版本）。 若要更正此问题，请安装最新版本的 Visual Studio。
* 具有足够新版本的 Visual Studio 中，但不是具有安装了通用 Windows 平台 (UWP) 工具。 这是 Visual Studio 的可选功能。

启用还可能会看到安装仿真程序上非-教育版 PRO/企业版 SKU 的 Windows 错误或如果不具有 HYPER-V 功能。
* 请阅读[系统要求](#hololens-emulator-system-requirements)上面部分的一组完整的要求。
* 请也确保您的系统上启用了 HYPER-V 功能。

## <a name="deploying-apps-to-the-hololens-emulator"></a>将应用部署到 HoloLens 仿真程序

1. 加载 Visual Studio 2015 中的应用解决方案。
    >[!NOTE]
    >在使用 Unity 时，从 Unity 生成项目，然后加载生成的解决方案到 Visual Studio 中像往常一样。
2. 确保将平台设置为**x86**。
3. 选择**HoloLens 模拟器**作为目标设备以进行调试。
4. 转到**调试 > 启动调试**或按**F5**启动仿真程序和部署应用程序进行调试。

在仿真程序可能需要一分钟或更多用于首次启动时启动。 我们建议你将在仿真程序打开在调试会话期间以便可以快速将应用部署到运行的仿真程序。

## <a name="basic-emulator-input"></a>基本仿真程序输入

控制模拟器是与许多常见的 3D 视频游戏非常相似。 可以使用键盘、 鼠标或 Xbox 控制器是输入的选项。 将定向模拟的用户戴上 HoloLens 的操作，从而控制在仿真程序。 你的操作移动周围的模拟的用户并在模拟器中运行的应用程序的响应类似的方式在真实设备上。
* **引导前滚，、 左和右**-使用 W，A、 S 和 D 键键盘，或在 Xbox 控制器上的左记忆棒。
* **查找、 下、 左、 左右**-单击并拖动鼠标、 键盘或 Xbox 控制器上的右记忆棒上使用箭头键。
* **空中手势**-右键单击鼠标、 键盘上按 Enter 键或 Xbox 控制器上使用一个按钮。
* **百花齐放手势**-在键盘上按 Windows 键或 F2 键或 Xbox 控制器上按 B 按钮。
* **将移动滚动**-按住 Alt 键，请按住鼠标右键按钮和向上 / 向下拖动鼠标或 Xbox 控制器中按住正确的触发器和一个按钮并向上和向下移动右。

## <a name="anatomy-of-the-hololens-emulator"></a>HoloLens 仿真程序的剖析

### <a name="main-window"></a>主窗口

当在模拟器启动时，您将看到一个窗口，其中显示 HoloLens OS。

![HoloLens 仿真程序主窗口](images/emulator-890px.png)

### <a name="toolbar"></a>工具栏

在主窗口的右侧，您会发现仿真程序工具栏。 此工具栏包含以下按钮：
* ![关闭图标](images/emulator-close.png)**关闭**:关闭模拟器。
* ![最小化图标](images/emulator-minimize.png)**最小化**:最小化模拟器窗口。
* ![人工输入的图标](images/emulator-control.png)**人工输入**:使用鼠标和键盘以模拟人类[输入到仿真程序](#basic-emulator-input)。
* ![键盘和鼠标输入的图标](images/emulator-input.png)**键盘和鼠标输入**:键盘和鼠标输入直接传递到 HoloLens OS 为键盘和鼠标事件就像连接蓝牙键盘和鼠标。
* ![适应屏幕图标](images/emulator-fit.png)**适合屏幕大小**:适用于到屏幕的仿真程序。
* ![缩放图标](images/emulator-zoom.png)**缩放**:使仿真器大和变小。
* ![帮助图标](images/emulator-help.png)**帮助**:打开模拟器帮助。
* ![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**:为 HoloLens 操作系统在模拟器中打开 Windows Device Portal。
* ![工具图标](images/emulator-tools.png)**工具**:打开**其他工具**窗格。

### <a name="simulation-tab"></a>模拟选项卡

在默认选项卡**其他工具**窗格**模拟**选项卡。

![HoloLens 仿真程序附加工具窗格](images/emulator-simulation-500px.png)

模拟选项卡显示了用于驱动 HoloLens OS 在仿真程序内的模拟传感器的当前状态。 悬停在模拟选项卡中的任何值将提供描述如何控制此值的工具提示。

### <a name="room-tab"></a>聊天室选项卡

仿真程序模拟世界空间映射网格从模拟"聊天室"的形式输入。 此选项卡允许你选择的空间来加载而不是默认聊天室。

![HoloLens 仿真程序聊天室选项卡](images/emulator-room-500px.png)

模拟的聊天室可用于在多个环境中测试您的应用程序。 多个房间都附带了仿真程序和安装后仿真，您将在 %programfiles(x86) %\Program 文件 (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms 中找到它们。 在真实环境中使用 HoloLens 捕获了所有这些聊天室：
* **DefaultRoom.xef** -与电视、 咖啡表和两个 sofas 小客厅。 启动仿真程序时，默认情况下加载。
* **Bedroom1.xef** -向支持小卧室。
* **Bedroom2.xef** -黑桃皇后大小平台、 梳妆台、 nightstands，与 walk-in 密室卧室。
* **GreatRoom.xef** -起居室、 餐桌，与厨房中使用大型的空白空间很好聊天室。
* **LivingRoom.xef** -客厅使用壁炉、 沙发、 摇椅，和具有花瓶咖啡表。

此外可以记录使用的模拟页在仿真程序中使用你自己聊天室[Windows Device Portal](using-the-windows-device-portal.md)在 HoloLens 上。

在仿真程序中，将只能看到全息您呈现，则不会看到模拟背后全息房间。 这是实际 HoloLens 同时看到其中与混合在一起。 如果想要查看模拟的聊天室 HoloLens 仿真程序中，将需要更新你的应用场景中将空间的映射网格渲染。

### <a name="account-tab"></a>“帐户”选项卡

帐户选项卡，可将模拟器配置为使用 Microsoft 帐户登录。 这是用于测试的需要 API 用户能够登录的帐户。 在检查后此页上的框，后续启动仿真程序将要求你登录，就像用户一样首次启动 HoloLens。

## <a name="see-also"></a>请参阅
* [高级的 HoloLens 仿真程序和混合现实模拟器输入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens 模拟器软件历史记录](hololens-emulator-archive.md)
* [在 Unity 中的空间映射](spatial-mapping-in-unity.md)
* [在 DirectX 空间映射](spatial-mapping-in-directx.md)
