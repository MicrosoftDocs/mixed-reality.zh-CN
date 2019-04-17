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
# <a name="using-the-hololens-emulator"></a><span data-ttu-id="6638a-104">使用 HoloLens 仿真程序</span><span class="sxs-lookup"><span data-stu-id="6638a-104">Using the HoloLens emulator</span></span>

<span data-ttu-id="6638a-105">HoloLens 仿真程序允许您测试您的 PC 而无需物理 HoloLens 上全息版应用，并附带了 HoloLens 开发工具集。</span><span class="sxs-lookup"><span data-stu-id="6638a-105">The HoloLens emulator allows you to test holographic apps on your PC without a physical HoloLens and comes with the HoloLens development toolset.</span></span> <span data-ttu-id="6638a-106">在仿真程序使用的 HYPER-V 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="6638a-106">The emulator uses a Hyper-V virtual machine.</span></span> <span data-ttu-id="6638a-107">通常会在 HoloLens 上传感器读取的人和环境输入改为模拟使用键盘、 鼠标或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="6638a-107">The human and environmental inputs that would usually be read by the sensors on the HoloLens are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="6638a-108">应用程序无需修改即可在模拟器上运行，并不知道它们不实际 HoloLens 上运行。</span><span class="sxs-lookup"><span data-stu-id="6638a-108">Apps don't need to be modified to run on the emulator and don't know that they aren't running on a real HoloLens.</span></span>

<span data-ttu-id="6638a-109">如果想要为桌面 Pc 开发 Windows Mixed Reality 沉浸式 (VR) 耳机式应用程序或游戏，请查看[Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)，它可让你改为模拟桌面耳机。</span><span class="sxs-lookup"><span data-stu-id="6638a-109">If you're looking to develop Windows Mixed Reality immersive (VR) headset apps or games for desktop PCs, check out the [Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md), which lets you simulate desktop headsets instead.</span></span>

> [!NOTE]
> <span data-ttu-id="6638a-110">特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="6638a-110">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="installing-the-hololens-emulator"></a><span data-ttu-id="6638a-111">安装 HoloLens 仿真程序</span><span class="sxs-lookup"><span data-stu-id="6638a-111">Installing the HoloLens emulator</span></span>

<span data-ttu-id="6638a-112">下载[HoloLens （第 1 代） 仿真程序和全息版的项目模板](https://go.microsoft.com/fwlink/?linkid=2065980)。</span><span class="sxs-lookup"><span data-stu-id="6638a-112">Download the [HoloLens (1st gen) emulator and holographic project templates](https://go.microsoft.com/fwlink/?linkid=2065980).</span></span>

<span data-ttu-id="6638a-113">可以找到较旧版本的 HoloLens 模拟器[HoloLens 仿真器存档](hololens-emulator-archive.md)页。</span><span class="sxs-lookup"><span data-stu-id="6638a-113">You can find older builds of the HoloLens emulator on the [HoloLens emulator archive](hololens-emulator-archive.md) page.</span></span>

### <a name="hololens-emulator-system-requirements"></a><span data-ttu-id="6638a-114">HoloLens 的模拟器系统要求</span><span class="sxs-lookup"><span data-stu-id="6638a-114">HoloLens emulator system requirements</span></span>

<span data-ttu-id="6638a-115">HoloLens 仿真程序依赖于使用 HYPER-V 和使用 RemoteFx 的硬件加速图形。</span><span class="sxs-lookup"><span data-stu-id="6638a-115">The HoloLens emulator is based on Hyper-V and uses RemoteFx for hardware accelerated graphics.</span></span> <span data-ttu-id="6638a-116">若要使用模拟器，请确保您的 PC 满足以下硬件要求：</span><span class="sxs-lookup"><span data-stu-id="6638a-116">To use the emulator, make sure your PC meets these hardware requirements:</span></span>
* <span data-ttu-id="6638a-117">64 位 Windows 10 Pro、 Enterprise 或教育版</span><span class="sxs-lookup"><span data-stu-id="6638a-117">64-bit Windows 10 Pro, Enterprise, or Education</span></span> 
    >[!NOTE]
    ><span data-ttu-id="6638a-118">Windows 10 家庭版不支持的 HYPER-V 或 HoloLens 仿真程序</span><span class="sxs-lookup"><span data-stu-id="6638a-118">Windows 10 Home edition does not support Hyper-V or the HoloLens emulator</span></span>
* <span data-ttu-id="6638a-119">64 位 CPU</span><span class="sxs-lookup"><span data-stu-id="6638a-119">64-bit CPU</span></span>
* <span data-ttu-id="6638a-120">CPU 具有 4 个核心 （或多个 Cpu 总容量为 4 个核心）</span><span class="sxs-lookup"><span data-stu-id="6638a-120">CPU with 4 cores (or multiple CPUs with a total of 4 cores)</span></span>
* <span data-ttu-id="6638a-121">8 GB 的 RAM 或更多</span><span class="sxs-lookup"><span data-stu-id="6638a-121">8 GB of RAM or more</span></span>
* <span data-ttu-id="6638a-122">必须在 BIOS 中，以下功能[支持且启用了](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):</span><span class="sxs-lookup"><span data-stu-id="6638a-122">In the BIOS, the following features must be [supported and enabled](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):</span></span>
   * <span data-ttu-id="6638a-123">硬件辅助虚拟化</span><span class="sxs-lookup"><span data-stu-id="6638a-123">Hardware-assisted virtualization</span></span>
   * <span data-ttu-id="6638a-124">二级地址转换 (SLAT)</span><span class="sxs-lookup"><span data-stu-id="6638a-124">Second Level Address Translation (SLAT)</span></span>
   * <span data-ttu-id="6638a-125">基于硬件的数据执行保护 (DEP)</span><span class="sxs-lookup"><span data-stu-id="6638a-125">Hardware-based Data Execution Prevention (DEP)</span></span>
* <span data-ttu-id="6638a-126">GPU 要求 （仿真程序可能使用不受支持的 GPU，但会显著变慢）</span><span class="sxs-lookup"><span data-stu-id="6638a-126">GPU requirements (the emulator might work with an unsupported GPU, but will be significantly slower)</span></span>
   * <span data-ttu-id="6638a-127">DirectX 11.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="6638a-127">DirectX 11.0 or later</span></span>
   * <span data-ttu-id="6638a-128">WDDM 1.2 驱动程序或更高版本</span><span class="sxs-lookup"><span data-stu-id="6638a-128">WDDM 1.2 driver or later</span></span>

<span data-ttu-id="6638a-129">如果你的系统满足上述要求**请确保你的系统上是否已启用"HYPER-V"功能**通过控制面板-> 程序-> 程序和功能-> 上的启用 Windows 功能或关闭-> 确保"HYPER-V"选择用于仿真程序的安装才能成功。</span><span class="sxs-lookup"><span data-stu-id="6638a-129">If your system meets the above requirements, **please ensure that the "Hyper-V" feature has been enabled on your system** through Control Panel -> Programs -> Programs and Features -> Turn Windows Features on or off -> ensure that "Hyper-V" is selected for the Emulator installation to be successful.</span></span>

### <a name="installation-troubleshooting"></a><span data-ttu-id="6638a-130">安装故障排除</span><span class="sxs-lookup"><span data-stu-id="6638a-130">Installation troubleshooting</span></span>

<span data-ttu-id="6638a-131">在安装所需的仿真程序时，可能会出错 *"Visual Studio 2015 Update 1 和 UWP 工具版本 1.2"*。</span><span class="sxs-lookup"><span data-stu-id="6638a-131">You may see an error while installing the emulator that you need *"Visual Studio 2015 Update 1 and UWP tools version 1.2"*.</span></span> <span data-ttu-id="6638a-132">有三个可能导致此错误的原因：</span><span class="sxs-lookup"><span data-stu-id="6638a-132">There are three possible causes of this error:</span></span>
* <span data-ttu-id="6638a-133">没有足够新版本的 Visual Studio （Visual Studio 2017 或 Visual Studio 2015 Update 1 或更高版本）。</span><span class="sxs-lookup"><span data-stu-id="6638a-133">You do not have a recent enough version of Visual Studio (Visual Studio 2017 or Visual Studio 2015 Update 1 or later).</span></span> <span data-ttu-id="6638a-134">若要更正此问题，请安装最新版本的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="6638a-134">To correct this, install the latest release of Visual Studio.</span></span>
* <span data-ttu-id="6638a-135">具有足够新版本的 Visual Studio 中，但不是具有安装了通用 Windows 平台 (UWP) 工具。</span><span class="sxs-lookup"><span data-stu-id="6638a-135">You have a recent enough version of Visual Studio, but you do not have the Universal Windows Platform (UWP) tools installed.</span></span> <span data-ttu-id="6638a-136">这是 Visual Studio 的可选功能。</span><span class="sxs-lookup"><span data-stu-id="6638a-136">This is an optional feature for Visual Studio.</span></span>

<span data-ttu-id="6638a-137">启用还可能会看到安装仿真程序上非-教育版 PRO/企业版 SKU 的 Windows 错误或如果不具有 HYPER-V 功能。</span><span class="sxs-lookup"><span data-stu-id="6638a-137">You may also see an error installing the emulator on a non-PRO/Enterprise/Education SKU of Windows or if you do not have Hyper-V feature enabled.</span></span>
* <span data-ttu-id="6638a-138">请阅读[系统要求](#hololens-emulator-system-requirements)上面部分的一组完整的要求。</span><span class="sxs-lookup"><span data-stu-id="6638a-138">Please read the [system requirements](#hololens-emulator-system-requirements) section above for a complete set of requirements.</span></span>
* <span data-ttu-id="6638a-139">请也确保您的系统上启用了 HYPER-V 功能。</span><span class="sxs-lookup"><span data-stu-id="6638a-139">Please also ensure that Hyper-V feature has been enabled on your system.</span></span>

## <a name="deploying-apps-to-the-hololens-emulator"></a><span data-ttu-id="6638a-140">将应用部署到 HoloLens 仿真程序</span><span class="sxs-lookup"><span data-stu-id="6638a-140">Deploying apps to the HoloLens emulator</span></span>

1. <span data-ttu-id="6638a-141">加载 Visual Studio 2015 中的应用解决方案。</span><span class="sxs-lookup"><span data-stu-id="6638a-141">Load your app solution in Visual Studio 2015.</span></span>
    >[!NOTE]
    ><span data-ttu-id="6638a-142">在使用 Unity 时，从 Unity 生成项目，然后加载生成的解决方案到 Visual Studio 中像往常一样。</span><span class="sxs-lookup"><span data-stu-id="6638a-142">When using Unity, build your project from Unity and then load the built solution into Visual Studio as usual.</span></span>
2. <span data-ttu-id="6638a-143">确保将平台设置为**x86**。</span><span class="sxs-lookup"><span data-stu-id="6638a-143">Ensure the Platform is set to **x86**.</span></span>
3. <span data-ttu-id="6638a-144">选择**HoloLens 模拟器**作为目标设备以进行调试。</span><span class="sxs-lookup"><span data-stu-id="6638a-144">Select the **HoloLens Emulator** as the target device for debugging.</span></span>
4. <span data-ttu-id="6638a-145">转到**调试 > 启动调试**或按**F5**启动仿真程序和部署应用程序进行调试。</span><span class="sxs-lookup"><span data-stu-id="6638a-145">Go to **Debug > Start Debugging** or press **F5** to launch the emulator and deploy your app for debugging.</span></span>

<span data-ttu-id="6638a-146">在仿真程序可能需要一分钟或更多用于首次启动时启动。</span><span class="sxs-lookup"><span data-stu-id="6638a-146">The emulator may take a minute or more to boot when you first start it.</span></span> <span data-ttu-id="6638a-147">我们建议你将在仿真程序打开在调试会话期间以便可以快速将应用部署到运行的仿真程序。</span><span class="sxs-lookup"><span data-stu-id="6638a-147">We recommend that you keep the emulator open during your debugging session so you can quickly deploy apps to the running emulator.</span></span>

## <a name="basic-emulator-input"></a><span data-ttu-id="6638a-148">基本仿真程序输入</span><span class="sxs-lookup"><span data-stu-id="6638a-148">Basic emulator input</span></span>

<span data-ttu-id="6638a-149">控制模拟器是与许多常见的 3D 视频游戏非常相似。</span><span class="sxs-lookup"><span data-stu-id="6638a-149">Controlling the emulator is very similar to many common 3D video games.</span></span> <span data-ttu-id="6638a-150">可以使用键盘、 鼠标或 Xbox 控制器是输入的选项。</span><span class="sxs-lookup"><span data-stu-id="6638a-150">There are input options available using the keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="6638a-151">将定向模拟的用户戴上 HoloLens 的操作，从而控制在仿真程序。</span><span class="sxs-lookup"><span data-stu-id="6638a-151">You control the emulator by directing the actions of a simulated user wearing a HoloLens.</span></span> <span data-ttu-id="6638a-152">你的操作移动周围的模拟的用户并在模拟器中运行的应用程序的响应类似的方式在真实设备上。</span><span class="sxs-lookup"><span data-stu-id="6638a-152">Your actions move that simulated user around and apps running in the emulator respond like they would on a real device.</span></span>
* <span data-ttu-id="6638a-153">**引导前滚，、 左和右**-使用 W，A、 S 和 D 键键盘，或在 Xbox 控制器上的左记忆棒。</span><span class="sxs-lookup"><span data-stu-id="6638a-153">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="6638a-154">**查找、 下、 左、 左右**-单击并拖动鼠标、 键盘或 Xbox 控制器上的右记忆棒上使用箭头键。</span><span class="sxs-lookup"><span data-stu-id="6638a-154">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="6638a-155">**空中手势**-右键单击鼠标、 键盘上按 Enter 键或 Xbox 控制器上使用一个按钮。</span><span class="sxs-lookup"><span data-stu-id="6638a-155">**Air tap gesture** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="6638a-156">**百花齐放手势**-在键盘上按 Windows 键或 F2 键或 Xbox 控制器上按 B 按钮。</span><span class="sxs-lookup"><span data-stu-id="6638a-156">**Bloom gesture** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="6638a-157">**将移动滚动**-按住 Alt 键，请按住鼠标右键按钮和向上 / 向下拖动鼠标或 Xbox 控制器中按住正确的触发器和一个按钮并向上和向下移动右。</span><span class="sxs-lookup"><span data-stu-id="6638a-157">**Hand movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="anatomy-of-the-hololens-emulator"></a><span data-ttu-id="6638a-158">HoloLens 仿真程序的剖析</span><span class="sxs-lookup"><span data-stu-id="6638a-158">Anatomy of the HoloLens emulator</span></span>

### <a name="main-window"></a><span data-ttu-id="6638a-159">主窗口</span><span class="sxs-lookup"><span data-stu-id="6638a-159">Main window</span></span>

<span data-ttu-id="6638a-160">当在模拟器启动时，您将看到一个窗口，其中显示 HoloLens OS。</span><span class="sxs-lookup"><span data-stu-id="6638a-160">When the emulator launches, you will see a window which displays the HoloLens OS.</span></span>

![HoloLens 仿真程序主窗口](images/emulator-890px.png)

### <a name="toolbar"></a><span data-ttu-id="6638a-162">工具栏</span><span class="sxs-lookup"><span data-stu-id="6638a-162">Toolbar</span></span>

<span data-ttu-id="6638a-163">在主窗口的右侧，您会发现仿真程序工具栏。</span><span class="sxs-lookup"><span data-stu-id="6638a-163">To the right of the main window, you will find the emulator toolbar.</span></span> <span data-ttu-id="6638a-164">此工具栏包含以下按钮：</span><span class="sxs-lookup"><span data-stu-id="6638a-164">The toolbar contains the following buttons:</span></span>
* <span data-ttu-id="6638a-165">![关闭图标](images/emulator-close.png)**关闭**:关闭模拟器。</span><span class="sxs-lookup"><span data-stu-id="6638a-165">![Close icon](images/emulator-close.png) **Close**: Closes the emulator.</span></span>
* <span data-ttu-id="6638a-166">![最小化图标](images/emulator-minimize.png)**最小化**:最小化模拟器窗口。</span><span class="sxs-lookup"><span data-stu-id="6638a-166">![Minimize icon](images/emulator-minimize.png) **Minimize**: Minimizes the emulator window.</span></span>
* <span data-ttu-id="6638a-167">![人工输入的图标](images/emulator-control.png)**人工输入**:使用鼠标和键盘以模拟人类[输入到仿真程序](#basic-emulator-input)。</span><span class="sxs-lookup"><span data-stu-id="6638a-167">![Human input icon](images/emulator-control.png) **Human Input**: Mouse and Keyboard are used to simulate human [input to the emulator](#basic-emulator-input).</span></span>
* <span data-ttu-id="6638a-168">![键盘和鼠标输入的图标](images/emulator-input.png)**键盘和鼠标输入**:键盘和鼠标输入直接传递到 HoloLens OS 为键盘和鼠标事件就像连接蓝牙键盘和鼠标。</span><span class="sxs-lookup"><span data-stu-id="6638a-168">![Keyboard and mouse input icon](images/emulator-input.png) **Keyboard and Mouse Input**: Keyboard and mouse input are passed directly to the HoloLens OS as keyboard and mouse events as if you connected a Bluetooth keyboard and mouse.</span></span>
* <span data-ttu-id="6638a-169">![适应屏幕图标](images/emulator-fit.png)**适合屏幕大小**:适用于到屏幕的仿真程序。</span><span class="sxs-lookup"><span data-stu-id="6638a-169">![Fit to screen icon](images/emulator-fit.png) **Fit to Screen**: Fits the emulator to screen.</span></span>
* <span data-ttu-id="6638a-170">![缩放图标](images/emulator-zoom.png)**缩放**:使仿真器大和变小。</span><span class="sxs-lookup"><span data-stu-id="6638a-170">![Zoom icon](images/emulator-zoom.png) **Zoom**: Make the emulator larger and smaller.</span></span>
* <span data-ttu-id="6638a-171">![帮助图标](images/emulator-help.png)**帮助**:打开模拟器帮助。</span><span class="sxs-lookup"><span data-stu-id="6638a-171">![Help icon](images/emulator-help.png) **Help**: Open emulator help.</span></span>
* <span data-ttu-id="6638a-172">![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**:为 HoloLens 操作系统在模拟器中打开 Windows Device Portal。</span><span class="sxs-lookup"><span data-stu-id="6638a-172">![Open device portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>
* <span data-ttu-id="6638a-173">![工具图标](images/emulator-tools.png)**工具**:打开**其他工具**窗格。</span><span class="sxs-lookup"><span data-stu-id="6638a-173">![Tools icon](images/emulator-tools.png) **Tools**: Open the **Additional Tools** pane.</span></span>

### <a name="simulation-tab"></a><span data-ttu-id="6638a-174">模拟选项卡</span><span class="sxs-lookup"><span data-stu-id="6638a-174">Simulation tab</span></span>

<span data-ttu-id="6638a-175">在默认选项卡**其他工具**窗格**模拟**选项卡。</span><span class="sxs-lookup"><span data-stu-id="6638a-175">The default tab within the **Additional Tools** pane is the **Simulation** tab.</span></span>

![HoloLens 仿真程序附加工具窗格](images/emulator-simulation-500px.png)

<span data-ttu-id="6638a-177">模拟选项卡显示了用于驱动 HoloLens OS 在仿真程序内的模拟传感器的当前状态。</span><span class="sxs-lookup"><span data-stu-id="6638a-177">The Simulation tab shows the current state of the simulated sensors used to drive the HoloLens OS within the emulator.</span></span> <span data-ttu-id="6638a-178">悬停在模拟选项卡中的任何值将提供描述如何控制此值的工具提示。</span><span class="sxs-lookup"><span data-stu-id="6638a-178">Hovering over any value in the Simulation tab will provide a tooltip describing how to control that value.</span></span>

### <a name="room-tab"></a><span data-ttu-id="6638a-179">聊天室选项卡</span><span class="sxs-lookup"><span data-stu-id="6638a-179">Room tab</span></span>

<span data-ttu-id="6638a-180">仿真程序模拟世界空间映射网格从模拟"聊天室"的形式输入。</span><span class="sxs-lookup"><span data-stu-id="6638a-180">The emulator simulates world input in the form of the spatial mapping mesh from simulated "rooms".</span></span> <span data-ttu-id="6638a-181">此选项卡允许你选择的空间来加载而不是默认聊天室。</span><span class="sxs-lookup"><span data-stu-id="6638a-181">This tab lets you pick which room to load instead of the default room.</span></span>

![HoloLens 仿真程序聊天室选项卡](images/emulator-room-500px.png)

<span data-ttu-id="6638a-183">模拟的聊天室可用于在多个环境中测试您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="6638a-183">Simulated rooms are useful for testing your app in multiple environments.</span></span> <span data-ttu-id="6638a-184">多个房间都附带了仿真程序和安装后仿真，您将在 %programfiles(x86) %\Program 文件 (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms 中找到它们。</span><span class="sxs-lookup"><span data-stu-id="6638a-184">Several rooms are shipped with the emulator and once you install the emulation, you will find them in %ProgramFiles(x86)%\Program Files (x86)\Microsoft XDE\10.0.11082.0\Plugins\Rooms.</span></span> <span data-ttu-id="6638a-185">在真实环境中使用 HoloLens 捕获了所有这些聊天室：</span><span class="sxs-lookup"><span data-stu-id="6638a-185">All of these rooms were captured in real environments using a HoloLens:</span></span>
* <span data-ttu-id="6638a-186">**DefaultRoom.xef** -与电视、 咖啡表和两个 sofas 小客厅。</span><span class="sxs-lookup"><span data-stu-id="6638a-186">**DefaultRoom.xef** - A small living room with a TV, coffee table, and two sofas.</span></span> <span data-ttu-id="6638a-187">启动仿真程序时，默认情况下加载。</span><span class="sxs-lookup"><span data-stu-id="6638a-187">Loaded by default when you start the emulator.</span></span>
* <span data-ttu-id="6638a-188">**Bedroom1.xef** -向支持小卧室。</span><span class="sxs-lookup"><span data-stu-id="6638a-188">**Bedroom1.xef** - A small bedroom with a desk.</span></span>
* <span data-ttu-id="6638a-189">**Bedroom2.xef** -黑桃皇后大小平台、 梳妆台、 nightstands，与 walk-in 密室卧室。</span><span class="sxs-lookup"><span data-stu-id="6638a-189">**Bedroom2.xef** - A bedroom with a queen size bed, dresser, nightstands, and walk-in closet.</span></span>
* <span data-ttu-id="6638a-190">**GreatRoom.xef** -起居室、 餐桌，与厨房中使用大型的空白空间很好聊天室。</span><span class="sxs-lookup"><span data-stu-id="6638a-190">**GreatRoom.xef** - A large open space great room with living room, dining table, and kitchen.</span></span>
* <span data-ttu-id="6638a-191">**LivingRoom.xef** -客厅使用壁炉、 沙发、 摇椅，和具有花瓶咖啡表。</span><span class="sxs-lookup"><span data-stu-id="6638a-191">**LivingRoom.xef** - A living room with a fireplace, sofa, armchairs, and a coffee table with a vase.</span></span>

<span data-ttu-id="6638a-192">此外可以记录使用的模拟页在仿真程序中使用你自己聊天室[Windows Device Portal](using-the-windows-device-portal.md)在 HoloLens 上。</span><span class="sxs-lookup"><span data-stu-id="6638a-192">You can also record your own rooms to use in the emulator using the Simulation page of the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens.</span></span>

<span data-ttu-id="6638a-193">在仿真程序中，将只能看到全息您呈现，则不会看到模拟背后全息房间。</span><span class="sxs-lookup"><span data-stu-id="6638a-193">On the emulator, you will only see holograms that you render and you will not see the simulated room behind the holograms.</span></span> <span data-ttu-id="6638a-194">这是实际 HoloLens 同时看到其中与混合在一起。</span><span class="sxs-lookup"><span data-stu-id="6638a-194">This is in contrast to the real HoloLens where you see both blended together.</span></span> <span data-ttu-id="6638a-195">如果想要查看模拟的聊天室 HoloLens 仿真程序中，将需要更新你的应用场景中将空间的映射网格渲染。</span><span class="sxs-lookup"><span data-stu-id="6638a-195">If you want to see the simulated room in the HoloLens emulator, you will need to update your app to render the spatial mapping mesh in the scene.</span></span>

### <a name="account-tab"></a><span data-ttu-id="6638a-196">“帐户”选项卡</span><span class="sxs-lookup"><span data-stu-id="6638a-196">Account Tab</span></span>

<span data-ttu-id="6638a-197">帐户选项卡，可将模拟器配置为使用 Microsoft 帐户登录。</span><span class="sxs-lookup"><span data-stu-id="6638a-197">The Account tab allows you to configure the emulator to sign-in with a Microsoft Account.</span></span> <span data-ttu-id="6638a-198">这是用于测试的需要 API 用户能够登录的帐户。</span><span class="sxs-lookup"><span data-stu-id="6638a-198">This is useful for testing API's that require the user to be signed-in with an account.</span></span> <span data-ttu-id="6638a-199">在检查后此页上的框，后续启动仿真程序将要求你登录，就像用户一样首次启动 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="6638a-199">After checking the box on this page, subsequent launches of the emulator will ask you to sign-in, just like a user would the first time the HoloLens is started.</span></span>

## <a name="see-also"></a><span data-ttu-id="6638a-200">请参阅</span><span class="sxs-lookup"><span data-stu-id="6638a-200">See also</span></span>
* [<span data-ttu-id="6638a-201">高级的 HoloLens 仿真程序和混合现实模拟器输入</span><span class="sxs-lookup"><span data-stu-id="6638a-201">Advanced HoloLens Emulator and Mixed Reality Simulator input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="6638a-202">HoloLens 模拟器软件历史记录</span><span class="sxs-lookup"><span data-stu-id="6638a-202">HoloLens emulator software history</span></span>](hololens-emulator-archive.md)
* [<span data-ttu-id="6638a-203">在 Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="6638a-203">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="6638a-204">在 DirectX 空间映射</span><span class="sxs-lookup"><span data-stu-id="6638a-204">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
