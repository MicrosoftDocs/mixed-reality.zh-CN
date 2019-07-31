---
title: 使用 HoloLens 仿真器
description: 使用 HoloLens 仿真器可以在未配备物理 HoloLens 的电脑上测试混合现实应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, 仿真器
ms.openlocfilehash: e675911e661ad6a4b1f05f2ecb3aa77994c3815c
ms.sourcegitcommit: 36601a19306a05c826b91dea191b020f634912bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2019
ms.locfileid: "67650825"
---
# <a name="using-the-hololens-emulator"></a>使用 HoloLens 仿真器

使用 HoloLens 仿真器可以在未配备物理 HoloLens 的电脑上测试全息应用程序。 它还附带 HoloLens 开发工具集。 该仿真器使用 Hyper-V 虚拟机。 HoloLens 传感器通常读取的人类和环境输入通过键盘、鼠标或 Xbox 控制器模拟。 应用程序无需经过修改即可在仿真器上运行，并且不知道它们不是在 HoloLens 上运行。

如果想要开发适用于台式机的 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备应用程序或游戏，请查看 [Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)，该设备可用于模拟桌面头戴显示设备。


## <a name="installing-the-hololens-emulator"></a>安装 HoloLens 仿真器
下载 HoloLens 仿真器和全息项目模板。

版本： 
* [HoloLens 2 仿真器和全息项目模板](https://go.microsoft.com/fwlink/?linkid=2098508)。
* [HoloLens 仿真器（第 1 代）和全息项目模板](https://go.microsoft.com/fwlink/?linkid=2065980)。

可以在 [HoloLens 仿真器存档](hololens-emulator-archive.md)页上找到旧版 HoloLens 仿真器。

### <a name="hololens-emulator-system-requirements"></a>HoloLens 仿真器系统要求

HoloLens 仿真器结合使用 Hyper-V 和 RemoteFx（第 1 代仿真器）或 GPU-PV（HoloLens 2 仿真器）来实现图形硬件加速。 若要使用仿真器，请确保电脑符合以下硬件要求：
* 64 位 Windows 10 专业版、企业版或教育版 
    >[!NOTE]
    >Windows 10 家庭版不支持 Hyper-V 或 HoloLens 仿真器。  
    >HoloLens 2 仿真器需要 Windows 10 2018 年 10 月更新版或更高版本。
* 64 位 CPU
* 4 核 CPU（或总共有 4 个核心的多个 CPU）
* 8 GB 或更大的 RAM
* 在 BIOS 中，必须[支持且启用](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx)以下功能：
   * 硬件辅助虚拟化
   * 二级地址转换 (SLAT)
   * 基于硬件的数据执行保护 (DEP)
* GPU 要求
   * DirectX 11.0 或更高版本
   * WDDM 1.2 图形驱动程序或更高版本（第 1 代）
   * WDDM 2.5 图形驱动程序（HoloLens 2 仿真器）
   * 仿真器可与不受支持的 GPU 配合工作，但速度会明显变慢

如果你的系统满足上述要求，请**确保系统上已启用“Hyper-V”功能**，方法是在控制面板中选择“程序”->“程序和功能”->“启用或关闭 Windows 功能”，确保已选择“Hyper-V”，使仿真器能够成功安装。

## <a name="deploying-apps-to-the-hololens-emulator"></a>将应用部署到 HoloLens 仿真器

1. 在 Visual Studio 中加载应用程序解决方案。
    >[!NOTE]
    >使用 Unity 时，请从 Unity 生成项目，然后像往常一样将生成的解决方案载入 Visual Studio。
2. 对于 HoloLens 仿真器（第 1 代），请确保平台设置为“x86”。  对于 HoloLens 2 仿真器，请确保平台设置为“x86”或“x64”。  
3. 选择所需的 **HoloLens 仿真器**版本作为目标调试设备。
4. 转到“调试”>“开始调试”或按 **F5** 启动仿真器，然后部署要调试的应用程序。 

仿真器在首次启动时，可能需要花费一分钟或更长的时间来完成引导。 我们建议在调试会话期间将仿真器保持打开，以便可以快速将应用程序部署到正在运行的仿真器。

## <a name="basic-emulator-input"></a>基本的仿真器输入

控制仿真器与许多常见的 3D 视频游戏非常相似。 可以通过输入选项来使用键盘、鼠标或 Xbox 控制器。 通过定向佩戴 HoloLens 的模拟用户执行的操作来控制仿真器。 你的操作可在环境中四处移动该模拟用户。 仿真器中运行的应用程序可以像在真实设备上一样做出响应。

HoloLens（第 1 代）上的光标可跟踪头部运动和旋转。 在 HoloLens 2 仿真器中，光标跟踪手部运动和方向。

* **前后左右走动** - 使用键盘上的 WASD 键，或 Xbox 控制器上的左摇杆。
* **上下左右注视** - 单击并拖动鼠标、使用键盘上的箭头键，或使用 Xbox 控制器上的右摇杆。
* **隔空敲击手势** - 单击鼠标右键、按键盘上的 Enter 键，或使用 Xbox 控制器上的 A 按钮。
* **开花手势/系统手势** - 按键盘上的 Windows 键或 F2 键，或按 Xbox 控制器上的 B 按钮。
* **滚动时的手部运动** - 按住 Alt 键和鼠标右键的同时向上或向下拖动鼠标，或者在 Xbox 控制器中按住右触发器和 A 按钮的同时向上和向下移动右摇杆。
* **手部运动和方向**（仅适用于 HoloLens 2 仿真器）- 按住 Alt 键的同时向上、向下、向左或向右拖动鼠标以移动手部，或使用箭头键和 Q 或 E 来旋转和倾斜手部。 在 Xbox 控制器中，请在按住左缓冲键或右缓冲键的同时，使用左拇指操纵杆向左、向右、向前和向后移动手部，或使用 Dpad 上的向上或向下键来抬高或降低手部。

## <a name="anatomy-of-the-hololens-2-emulator"></a>HoloLens 2 仿真器剖析 

### <a name="main-window"></a>主窗口

![HoloLens 2 仿真器主窗口](images/emulator2-900px.png)

### <a name="toolbar"></a>工具栏

在主窗口的右侧，可以看到仿真器工具栏。 工具栏包含以下按钮：
* ![关闭图标](images/emulator-close.png)**关闭**：关闭仿真器。
* ![最小化图标](images/emulator-minimize.png)**最小化**：最小化仿真器窗口。
* ![模拟图标](images/emulator-simulation-panel.png) **模拟控制面板**：显示或隐藏[模拟控制面板](#simulation-control-panel)，以便配置和控制[仿真器的输入](#basic-emulator-input)。
* ![适应屏幕图标](images/emulator-fit.png)**适应屏幕**：使仿真器适合屏幕大小。
* ![缩放图标](images/emulator-zoom.png)**缩放**：放大和缩小仿真器。
* ![帮助图标](images/emulator-help.png)**帮助**：打开仿真器帮助。
* ![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。
* ![工具图标](images/emulator-tools.png)**工具**：打开“其他工具”窗格。 

### <a name="simulation-control-panel"></a>模拟控制面板

使用模拟控制面板可以查看模拟人类和输入设备的当前位置与方向。 使用它还可以配置模拟输入（例如，显示或隐藏一只或两只手）和用于控制模拟输入的设备（例如电脑的键盘、鼠标和游戏手柄）。

![模拟控制面板](images/emulator-simulation-control-panel.png)

* 若要隐藏或显示模拟面板，请单击工具栏按钮或按键盘上的 F7。
* 将鼠标悬停在控件或字段上可显示工具提示，其中包含键盘、鼠标和游戏手柄的控件。
* 若要显示或隐藏手部，请切换左手或右手下方的相应开关。
* 若要控制手部，请使用键盘上的左/右 Alt 键，或游戏手柄上的左/右缓冲键。
* 若要将所有输入定向到一只或两只手，请单击切换开关下的图钉按钮。  这相当于针对手部按住 Alt 键。
* 若要控制视线方向，请单击“眼睛”部分中的图钉。 这相当于按住键盘上的 Y 键。
* 若要加载房间录制内容，请单击“录制”部分中的“加载”按钮。 有关详细信息，请参阅[模拟的房间](#simulated-rooms)。
* 若要调整模拟人类或输入设备在响应键盘、鼠标或游戏手柄输入时移动或旋转的速度，请单击“输入设置”旁边的齿轮图标并调整滑块。
* 默认情况下，键盘输入会控制模拟人类和模拟输入。 若要将电脑的键盘输入发送到 HoloLens，请取消选中“使用键盘进行模拟”。  F4 是此项设置的快捷键。
* 如果模拟面板已显示，按 F8 会将键盘焦点转移到模拟面板。
* 若要在仿真器窗口中取消停靠模拟面板，请单击面板底部的按钮，或按键盘上的 F9。  关闭窗口或再次按 F9 会恢复为仿真器窗口。
* 可将模拟控制面板作为单独的应用程序启动，这样就可以通过运行 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\ 中的 PerceptionSimulationInput.exe，来连接和控制 HoloLens 2 仿真器、HoloLens 2 设备或 Windows Mixed Reality 模拟。

### <a name="account-tab"></a>“帐户”选项卡

在“帐户”选项卡中，可将仿真器配置为使用 Microsoft 帐户登录。 在测试需要用户使用帐户登录的 API 时，此配置非常有用。 切换此选项需要完全关闭并重启 HoloLens 仿真器，使设置生效。 如果启用此选项，则后续启动仿真器时，系统会要求你登录，就像用户首次启动 HoloLens 时一样。 若要使用电脑键盘输入凭据，请先在模拟控制面板中关闭“使用键盘进行模拟”，或按键盘上的 F4 打开或关闭键盘设置。

### <a name="optional-settings-tab"></a>“可选设置”选项卡

“可选设置”选项卡显示用于启用或禁用硬件加速图形的控件。 默认情况下，如果电脑图形适配器的驱动器支持硬件加速图形，则就会使用硬件加速图形。 如果图形适配器的驱动程序不支持 GPU-PV，则不会显示此选项。

### <a name="diagnostics-tab"></a>“诊断”选项卡

“诊断”选项卡以 Windows 设备门户链接的形式显示仿真器的 IP 地址，以及虚拟 GPU 的状态。


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>HoloLens（第 1 代）仿真器剖析

### <a name="main-window"></a>主窗口

当仿真器启动时，你会看到一个显示 HoloLens OS 的窗口。

![HoloLens 仿真器主窗口](images/emulator-890px.png)

### <a name="toolbar"></a>工具栏

在主窗口的右侧，可以看到仿真器工具栏。 工具栏包含以下按钮：
* ![关闭图标](images/emulator-close.png)**关闭**：关闭仿真器。
* ![最小化图标](images/emulator-minimize.png)**最小化**：最小化仿真器窗口。
* ![人类输入图标](images/emulator-control.png)**人类输入**：使用鼠标和键盘来模拟[仿真器的人类输入](#basic-emulator-input)。
* ![键盘和鼠标输入图标](images/emulator-input.png)**键盘和鼠标输入**：键盘和鼠标输入将作为键盘和鼠标事件直接传递给 HoloLens OS，就如同已连接蓝牙键盘和鼠标一样。
* ![适应屏幕图标](images/emulator-fit.png)**适应屏幕**：使仿真器适合屏幕大小。
* ![缩放图标](images/emulator-zoom.png)**缩放**：放大和缩小仿真器。
* ![帮助图标](images/emulator-help.png)**帮助**：打开仿真器帮助。
* ![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。
* ![工具图标](images/emulator-tools.png)**工具**：打开“其他工具”窗格。 

### <a name="simulation-tab"></a>“模拟”选项卡

“其他工具”窗格中的默认选项卡是“模拟”选项卡。  

![HoloLens 仿真器的“其他工具”窗格](images/emulator-simulation-500px.png)

“模拟”选项卡显示用于在仿真器中驱动 HoloLens OS 的模拟传感器的当前状态。 将鼠标悬停在“模拟”选项卡中的任一值上会显示工具提示，其中描述了如何控制该值。

### <a name="room-tab"></a>“房间”选项卡

仿真器以模拟“房间”的空间映射网格形式模拟世界坐标输入。 使用此选项卡可以选择要加载的房间而不是默认房间。

![HoloLens 仿真器的“房间”选项卡](images/emulator-room-500px.png)

有关详细信息，请参阅[模拟的房间](#simulated-rooms)。

### <a name="account-tab"></a>“帐户”选项卡

在“帐户”选项卡中，可将仿真器配置为使用 Microsoft 帐户登录。 在测试需要用户使用帐户登录的 API 时，此配置非常有用。 选中此页上的框后，后续启动仿真器时，系统会要求你登录，如同用户首次启动 HoloLens 时那样。

## <a name="simulated-rooms"></a>模拟的房间

模拟的房间可用于在多个环境中测试应用程序。 仿真器随附了多个房间。 安装仿真器后，可以在 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(version)\Plugins\Rooms 中找到这些房间。 所有这些房间是使用 HoloLens 在真实环境中捕获的：
* **DefaultRoom.xef** - 配有一台电视机、一个茶几和两套沙发的小客厅。 启动仿真器时，默认会加载该房间。
* **Bedroom1.xef** - 配有一张桌子的小卧室。
* **Bedroom2.xef** - 配有一张双人床、梳妆台、床头柜和步入式衣橱的卧室。
* **GreatRoom.xef** - 配有客厅、餐桌和厨房的开阔大房间。
* **LivingRoom.xef** - 配有壁炉、沙发、摇椅和摆放了花瓶的茶几的客厅。

也可以在 HoloLens 上（第 1 代）上使用 [Windows 设备门户](using-the-windows-device-portal.md)的“模拟”页录制你自己的房间，以便在仿真器中使用。

在仿真器中，你只会看到自己渲染的全息影像。 但你看不到全息影像后面的模拟房间。 而在实际的 HoloLens 中，你会同时看到两者的混合形式。 若要在 HoloLens 仿真器中查看模拟的房间，需要更新应用程序，以便在场景中渲染空间映射网格。

## <a name="troubleshooting"></a>疑难解答

安装仿真器时，可能会出错错误，指出需要“Visual Studio 2015 Update 1 和 UWP 工具版本 1.2”。  出现此错误的三个可能原因如下：
* Visual Studio 的版本不够新（需要 Visual Studio 2019、Visual Studio 2017 或 Visual Studio 2015 Update 1 或更高版本）。 若要纠正此问题，请安装最新版本的 Visual Studio。
* 已安装最新版本的 Visual Studio，但未安装通用 Windows 平台 (UWP) 工具。 这是 Visual Studio 的一项可选功能。

此外，在 Windows 的非专业版/企业版/教育版 SKU 上安装仿真器，或者未启用 Hyper-V 功能时，也可能会看到错误。
* 有关完整的要求，请阅读前面的[系统要求](#hololens-emulator-system-requirements)部分。
* 另请确保已在系统上启用 Hyper-V 功能。

如果安装成功完成，但未看到 HoloLens 仿真器作为一个部署和调试选项列出，请检查以下各项：
* Visual Studio 项目配置已设置为 x86（HoloLens 第一代），或 x86 或 x64（HoloLens 2 仿真器）。
* 如果使用 Visual Studio 2019，则项目配置中的平台工具集应设置为 v142。

如果安装成功完成，但尝试启动 HoloLens 仿真器时 Visual Studio 显示错误，请尝试以下操作：
* 以管理员身份运行 Visual Studio
* 如果曾经只安装过 Visual Studio 2019，请检查 HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots 中的“KitsRoot10”注册表值是否指向 32 位 Program Files 文件夹（例如“C:\Program Files (x86)\Windows Kits\10”）。  如果不是，请卸载 HoloLens 仿真器，将该注册表值更改为你的 32 位 Program Files 文件夹，然后重新安装 HoloLens 仿真器。  此问题在 Visual Studio 2019 16.0.3 中已得到解决。

如果启动时仿真器显示“无效的字节编码”错误对话框：
* 请删除 %localappdata%\Microsoft\XDE\HCS 中的所有文件，然后重试。

如果 Visual Studio 中的调试目标列表为空（例如，“启动”是唯一选项），并且你已遵循上述所有故障排除步骤：
* 请删除 %localappdata%\Microsoft\VisualStudio\\<*安装 ID*>\CoreCon 中的 ConfigurationCache 文件夹，然后重试。

如果仿真器启动时系统挂起，请对仿真器图形禁用硬件加速。
* 在“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0”中创建名为“DisableGPU”的注册表 DWORD 值，并将其值设置为 1。

## <a name="see-also"></a>另请参阅
* [高级 HoloLens 仿真器和混合现实模拟器输入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens 仿真器软件历史记录](hololens-emulator-archive.md)
* [Unity 中的空间映射](spatial-mapping-in-unity.md)
* [DirectX 中的空间映射](spatial-mapping-in-directx.md)
