---
title: 使用 HoloLens 仿真器
description: 使用 HoloLens 仿真器可以在未配备物理 HoloLens 的电脑上测试混合现实应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, 仿真器
ms.openlocfilehash: 0dfca73e6c8e1809e1bea3df6ca344b3de0698d5
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730922"
---
# <a name="using-the-hololens-emulator"></a><span data-ttu-id="3fc28-104">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="3fc28-104">Using the HoloLens Emulator</span></span>

<span data-ttu-id="3fc28-105">HoloLens 仿真器附带 HoloLens 开发工具集，可让你在未配备物理 HoloLens 的电脑上测试全息应用。</span><span class="sxs-lookup"><span data-stu-id="3fc28-105">The HoloLens Emulator allows you to test holographic apps on your PC without a physical HoloLens and comes with the HoloLens development toolset.</span></span> <span data-ttu-id="3fc28-106">该仿真器使用 Hyper-V 虚拟机。</span><span class="sxs-lookup"><span data-stu-id="3fc28-106">The emulator uses a Hyper-V virtual machine.</span></span> <span data-ttu-id="3fc28-107">通常由 HoloLens 上的传感器读取的人类和环境输入现在改为由键盘、鼠标或 Xbox 控制器模拟。</span><span class="sxs-lookup"><span data-stu-id="3fc28-107">The human and environmental inputs that would usually be read by the sensors on the HoloLens are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="3fc28-108">应用无需经过修改即可在仿真器上运行，并且不知道它们不是在 HoloLens 上运行。</span><span class="sxs-lookup"><span data-stu-id="3fc28-108">Apps don't need to be modified to run on the emulator and don't know that they aren't running on a real HoloLens.</span></span>

<span data-ttu-id="3fc28-109">如果想要开发适用于台式机的 Windows Mixed Reality 沉浸式 (VR) 头戴显示设备应用或游戏，请查看 [Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)，该设备可用于模拟桌面头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="3fc28-109">If you're looking to develop Windows Mixed Reality immersive (VR) headset apps or games for desktop PCs, check out the [Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md), which lets you simulate desktop headsets instead.</span></span>


## <a name="installing-the-hololens-emulator"></a><span data-ttu-id="3fc28-110">安装 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="3fc28-110">Installing the HoloLens Emulator</span></span>
<span data-ttu-id="3fc28-111">下载 HoloLens 仿真器和全息项目模板。</span><span class="sxs-lookup"><span data-stu-id="3fc28-111">Download the HoloLens Emulator and holographic project templates.</span></span>

<span data-ttu-id="3fc28-112">版本：</span><span class="sxs-lookup"><span data-stu-id="3fc28-112">Versions:</span></span> 
* <span data-ttu-id="3fc28-113">[HoloLens 2 仿真器和全息项目模板](https://go.microsoft.com/fwlink/?linkid=2087187)。</span><span class="sxs-lookup"><span data-stu-id="3fc28-113">[HoloLens 2 Emulator and holographic project templates](https://go.microsoft.com/fwlink/?linkid=2087187).</span></span>
* <span data-ttu-id="3fc28-114">[HoloLens 仿真器（第 1 代）和全息项目模板](https://go.microsoft.com/fwlink/?linkid=2065980)。</span><span class="sxs-lookup"><span data-stu-id="3fc28-114">[HoloLens Emulator (1st Gen) and holographic project templates](https://go.microsoft.com/fwlink/?linkid=2065980).</span></span>

<span data-ttu-id="3fc28-115">可以在 [HoloLens 仿真器存档](hololens-emulator-archive.md)页上找到旧版 HoloLens 仿真器。</span><span class="sxs-lookup"><span data-stu-id="3fc28-115">You can find older builds of the HoloLens Emulator on the [HoloLens Emulator archive](hololens-emulator-archive.md) page.</span></span>

### <a name="hololens-emulator-system-requirements"></a><span data-ttu-id="3fc28-116">HoloLens 仿真器系统要求</span><span class="sxs-lookup"><span data-stu-id="3fc28-116">HoloLens Emulator system requirements</span></span>

<span data-ttu-id="3fc28-117">HoloLens 仿真器结合使用 Hyper-V 和 RemoteFx（第 1 代仿真器）或 GPU-PV（HoloLens 2 仿真器）来实现图形硬件加速。</span><span class="sxs-lookup"><span data-stu-id="3fc28-117">The HoloLens Emulator uses Hyper-V with RemoteFx (1st Gen Emulator) or GPU-PV (HoloLens 2 Emulator) for hardware accelerated graphics.</span></span> <span data-ttu-id="3fc28-118">若要使用仿真器，请确保电脑符合以下硬件要求：</span><span class="sxs-lookup"><span data-stu-id="3fc28-118">To use the emulator, make sure your PC meets these hardware requirements:</span></span>
* <span data-ttu-id="3fc28-119">64 位 Windows 10 专业版、企业版或教育版</span><span class="sxs-lookup"><span data-stu-id="3fc28-119">64-bit Windows 10 Pro, Enterprise, or Education</span></span> 
    >[!NOTE]
    ><span data-ttu-id="3fc28-120">Windows 10 家庭版不支持 Hyper-V 或 HoloLens 仿真器。</span><span class="sxs-lookup"><span data-stu-id="3fc28-120">Windows 10 Home edition does not support Hyper-V or the HoloLens Emulator.</span></span>  
    ><span data-ttu-id="3fc28-121">HoloLens 2 仿真器需要 Windows 10 2018 年 10 月更新版或更高版本。</span><span class="sxs-lookup"><span data-stu-id="3fc28-121">The HoloLens 2 Emulator requires the Windows 10 October 2018 update or newer.</span></span>
* <span data-ttu-id="3fc28-122">64 位 CPU</span><span class="sxs-lookup"><span data-stu-id="3fc28-122">64-bit CPU</span></span>
* <span data-ttu-id="3fc28-123">4 核 CPU（或总共有 4 个核心的多个 CPU）</span><span class="sxs-lookup"><span data-stu-id="3fc28-123">CPU with 4 cores (or multiple CPUs with a total of 4 cores)</span></span>
* <span data-ttu-id="3fc28-124">8 GB 或更大的 RAM</span><span class="sxs-lookup"><span data-stu-id="3fc28-124">8 GB of RAM or more</span></span>
* <span data-ttu-id="3fc28-125">在 BIOS 中，必须[支持且启用](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx)以下功能：</span><span class="sxs-lookup"><span data-stu-id="3fc28-125">In the BIOS, the following features must be [supported and enabled](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):</span></span>
   * <span data-ttu-id="3fc28-126">硬件辅助虚拟化</span><span class="sxs-lookup"><span data-stu-id="3fc28-126">Hardware-assisted virtualization</span></span>
   * <span data-ttu-id="3fc28-127">二级地址转换 (SLAT)</span><span class="sxs-lookup"><span data-stu-id="3fc28-127">Second Level Address Translation (SLAT)</span></span>
   * <span data-ttu-id="3fc28-128">基于硬件的数据执行保护 (DEP)</span><span class="sxs-lookup"><span data-stu-id="3fc28-128">Hardware-based Data Execution Prevention (DEP)</span></span>
* <span data-ttu-id="3fc28-129">GPU 要求</span><span class="sxs-lookup"><span data-stu-id="3fc28-129">GPU requirements</span></span>
   * <span data-ttu-id="3fc28-130">DirectX 11.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="3fc28-130">DirectX 11.0 or later</span></span>
   * <span data-ttu-id="3fc28-131">WDDM 1.2 图形驱动程序或更高版本（第 1 代）</span><span class="sxs-lookup"><span data-stu-id="3fc28-131">WDDM 1.2 graphics driver or later (1st Gen)</span></span>
   * <span data-ttu-id="3fc28-132">WDDM 2.5 图形驱动程序（HoloLens 2 仿真器）</span><span class="sxs-lookup"><span data-stu-id="3fc28-132">WDDM 2.5 graphics driver (HoloLens 2 Emulator)</span></span>
   * <span data-ttu-id="3fc28-133">仿真器可与不受支持的 GPU 配合工作，但速度会明显变慢</span><span class="sxs-lookup"><span data-stu-id="3fc28-133">The emulator might work with an unsupported GPU, but will be significantly slower</span></span>

<span data-ttu-id="3fc28-134">如果你的系统满足上述要求，请**确保系统上已启用“Hyper-V”功能**，方法是在控制面板中选择“程序”->“程序和功能”->“启用或关闭 Windows 功能”，确保已选择“Hyper-V”，使仿真器能够成功安装。</span><span class="sxs-lookup"><span data-stu-id="3fc28-134">If your system meets the above requirements, **please ensure that the "Hyper-V" feature has been enabled on your system** through Control Panel -> Programs -> Programs and Features -> Turn Windows Features on or off -> ensure that "Hyper-V" is selected for the Emulator installation to be successful.</span></span>

## <a name="deploying-apps-to-the-hololens-emulator"></a><span data-ttu-id="3fc28-135">将应用部署到 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="3fc28-135">Deploying apps to the HoloLens Emulator</span></span>

1. <span data-ttu-id="3fc28-136">在 Visual Studio 中加载应用解决方案。</span><span class="sxs-lookup"><span data-stu-id="3fc28-136">Load your app solution in Visual Studio.</span></span>
    >[!NOTE]
    ><span data-ttu-id="3fc28-137">使用 Unity 时，请从 Unity 生成项目，然后像往常一样将生成的解决方案载入 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3fc28-137">When using Unity, build your project from Unity and then load the built solution into Visual Studio as usual.</span></span>
2. <span data-ttu-id="3fc28-138">对于 HoloLens 仿真器（第 1 代），请确保平台设置为“x86”。 </span><span class="sxs-lookup"><span data-stu-id="3fc28-138">For the HoloLens Emulator (1st Gen), ensure the Platform is set to **x86**.</span></span> <span data-ttu-id="3fc28-139">对于 HoloLens 2 仿真器，请确保平台设置为“x86”或“x64”。  </span><span class="sxs-lookup"><span data-stu-id="3fc28-139">For the HoloLens 2 Emulator ensure the Platform is set to **x86** or **x64**.</span></span>
3. <span data-ttu-id="3fc28-140">选择所需的 **HoloLens 仿真器**版本作为目标调试设备。</span><span class="sxs-lookup"><span data-stu-id="3fc28-140">Select the desired **HoloLens Emulator** version as the target device for debugging.</span></span>
4. <span data-ttu-id="3fc28-141">转到“调试”>“开始调试”或按 **F5** 启动仿真器，然后部署要调试的应用。 </span><span class="sxs-lookup"><span data-stu-id="3fc28-141">Go to **Debug > Start Debugging** or press **F5** to launch the emulator and deploy your app for debugging.</span></span>

<span data-ttu-id="3fc28-142">仿真器在首次启动时，可能需要花费一分钟或更长的时间来完成引导。</span><span class="sxs-lookup"><span data-stu-id="3fc28-142">The emulator may take a minute or more to boot when you first start it.</span></span> <span data-ttu-id="3fc28-143">我们建议在调试会话期间将仿真器保持打开，以便可以快速将应用部署到正在运行的仿真器。</span><span class="sxs-lookup"><span data-stu-id="3fc28-143">We recommend that you keep the emulator open during your debugging session so you can quickly deploy apps to the running emulator.</span></span>

## <a name="basic-emulator-input"></a><span data-ttu-id="3fc28-144">基本的仿真器输入</span><span class="sxs-lookup"><span data-stu-id="3fc28-144">Basic emulator input</span></span>

<span data-ttu-id="3fc28-145">控制仿真器与许多常见的 3D 视频游戏非常相似。</span><span class="sxs-lookup"><span data-stu-id="3fc28-145">Controlling the emulator is very similar to many common 3D video games.</span></span> <span data-ttu-id="3fc28-146">可以使用键盘、鼠标或 Xbox 控制器提供输入。</span><span class="sxs-lookup"><span data-stu-id="3fc28-146">There are input options available using the keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="3fc28-147">通过定向佩戴 HoloLens 的模拟用户执行的操作来控制仿真器。</span><span class="sxs-lookup"><span data-stu-id="3fc28-147">You control the emulator by directing the actions of a simulated user wearing a HoloLens.</span></span> <span data-ttu-id="3fc28-148">你的操作可四处移动该模拟用户，而仿真器中运行的应用可以像在真实设备上一样做出响应。</span><span class="sxs-lookup"><span data-stu-id="3fc28-148">Your actions move that simulated user around and apps running in the emulator respond like they would on a real device.</span></span>

<span data-ttu-id="3fc28-149">HoloLens（第 1 代）上的光标可跟踪头部运动和旋转。</span><span class="sxs-lookup"><span data-stu-id="3fc28-149">The cursor on HoloLens (1st Gen) follows head movement and rotation.</span></span>  <span data-ttu-id="3fc28-150">在 HoloLens 2 仿真器中，光标跟踪手部运动和方向。</span><span class="sxs-lookup"><span data-stu-id="3fc28-150">In the HoloLens 2 Emulator, the cursor follows hand movement and orientation.</span></span>

* <span data-ttu-id="3fc28-151">**前后左右走动** - 使用键盘上的 WASD 键，或 Xbox 控制器上的左摇杆。</span><span class="sxs-lookup"><span data-stu-id="3fc28-151">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="3fc28-152">**上下左右注视** - 单击并拖动鼠标、使用键盘上的箭头键，或使用 Xbox 控制器上的右摇杆。</span><span class="sxs-lookup"><span data-stu-id="3fc28-152">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="3fc28-153">**隔空敲击手势** - 单击鼠标右键、按键盘上的 Enter 键，或使用 Xbox 控制器上的 A 按钮。</span><span class="sxs-lookup"><span data-stu-id="3fc28-153">**Air tap gesture** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="3fc28-154">**开花手势/系统手势** - 按键盘上的 Windows 键或 F2 键，或按 Xbox 控制器上的 B 按钮。</span><span class="sxs-lookup"><span data-stu-id="3fc28-154">**Bloom/System gesture** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="3fc28-155">**滚动时的手部运动** - 按住 Alt 键和鼠标右键的同时向上/向下拖动鼠标，或者在 Xbox 控制器中按住右触发器和 A 按钮的同时向上和向下移动右摇杆。</span><span class="sxs-lookup"><span data-stu-id="3fc28-155">**Hand movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>
* <span data-ttu-id="3fc28-156">**手部运动和方向**（仅适用于 HoloLens 2 仿真器）- 按住 Alt 键的同时向上/向下/向左/向右拖动鼠标以移动手部，或使用箭头键和 Q/E 来旋转和倾斜手部。</span><span class="sxs-lookup"><span data-stu-id="3fc28-156">**Hand movement and orientation** (HoloLens 2 Emulator only) - Hold the Alt key and drag the mouse up / down / left / right to move the hand, or use the arrow keys and Q / E to rotate and tilt the hand.</span></span>  <span data-ttu-id="3fc28-157">在 Xbox 控制器中，请在按住左缓冲键或右缓冲键的同时，使用左拇指操纵杆向左/向右/向前/向后移动手部，或使用 Dpad 上的向上/向下键来抬高或降低手部。</span><span class="sxs-lookup"><span data-stu-id="3fc28-157">For an Xbox controller, hold the left or right bumper and use the left thumbstick to move the hand left / right / forward / back, the right thumbstick to rotate it, and up / down on the Dpad to raise or lower the hand.</span></span>

## <a name="anatomy-of-the-hololens-2-emulator"></a><span data-ttu-id="3fc28-158">HoloLens 2 仿真器剖析</span><span class="sxs-lookup"><span data-stu-id="3fc28-158">Anatomy of the HoloLens 2 Emulator</span></span> 

### <a name="main-window"></a><span data-ttu-id="3fc28-159">主窗口</span><span class="sxs-lookup"><span data-stu-id="3fc28-159">Main window</span></span>

![HoloLens 2 仿真器主窗口](images/emulator2-900px.png)

### <a name="toolbar"></a><span data-ttu-id="3fc28-161">工具栏</span><span class="sxs-lookup"><span data-stu-id="3fc28-161">Toolbar</span></span>

<span data-ttu-id="3fc28-162">在主窗口的右侧，可以看到仿真器工具栏。</span><span class="sxs-lookup"><span data-stu-id="3fc28-162">To the right of the main window, you will find the emulator toolbar.</span></span> <span data-ttu-id="3fc28-163">工具栏包含以下按钮：</span><span class="sxs-lookup"><span data-stu-id="3fc28-163">The toolbar contains the following buttons:</span></span>
* <span data-ttu-id="3fc28-164">![关闭图标](images/emulator-close.png)**关闭**：关闭仿真器。</span><span class="sxs-lookup"><span data-stu-id="3fc28-164">![Close icon](images/emulator-close.png) **Close**: Closes the emulator.</span></span>
* <span data-ttu-id="3fc28-165">![最小化图标](images/emulator-minimize.png)**最小化**：最小化仿真器窗口。</span><span class="sxs-lookup"><span data-stu-id="3fc28-165">![Minimize icon](images/emulator-minimize.png) **Minimize**: Minimizes the emulator window.</span></span>
* <span data-ttu-id="3fc28-166">![模拟图标](images/emulator-simulation-panel.png) **模拟控制面板**：显示或隐藏[模拟控制面板](#simulation-control-panel)，以便配置和控制[仿真器的输入](#basic-emulator-input)。</span><span class="sxs-lookup"><span data-stu-id="3fc28-166">![Simulation_icon](images/emulator-simulation-panel.png) **Simulation Control Panel**: Show or hide the [Simulation Control panel](#simulation-control-panel) for configuring and controlling [input to the emulator](#basic-emulator-input).</span></span>
* <span data-ttu-id="3fc28-167">![适应屏幕图标](images/emulator-fit.png)**适应屏幕**：使仿真器适合屏幕大小。</span><span class="sxs-lookup"><span data-stu-id="3fc28-167">![Fit to screen icon](images/emulator-fit.png) **Fit to Screen**: Fits the emulator to screen.</span></span>
* <span data-ttu-id="3fc28-168">![缩放图标](images/emulator-zoom.png)**缩放**：放大和缩小仿真器。</span><span class="sxs-lookup"><span data-stu-id="3fc28-168">![Zoom icon](images/emulator-zoom.png) **Zoom**: Make the emulator larger and smaller.</span></span>
* <span data-ttu-id="3fc28-169">![帮助图标](images/emulator-help.png)**帮助**：打开仿真器帮助。</span><span class="sxs-lookup"><span data-stu-id="3fc28-169">![Help icon](images/emulator-help.png) **Help**: Open emulator help.</span></span>
* <span data-ttu-id="3fc28-170">![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="3fc28-170">![Open device portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>
* <span data-ttu-id="3fc28-171">![工具图标](images/emulator-tools.png)**工具**：打开“其他工具”窗格。 </span><span class="sxs-lookup"><span data-stu-id="3fc28-171">![Tools icon](images/emulator-tools.png) **Tools**: Open the **Additional Tools** pane.</span></span>

### <a name="simulation-control-panel"></a><span data-ttu-id="3fc28-172">模拟控制面板</span><span class="sxs-lookup"><span data-stu-id="3fc28-172">Simulation Control Panel</span></span>

<span data-ttu-id="3fc28-173">使用模拟控制面板可以查看模拟人类和模拟输入设备的当前位置与方向。</span><span class="sxs-lookup"><span data-stu-id="3fc28-173">The Simulation Control Panel allows you to view the current position and orientation of the simulated human and simulated input devices.</span></span>  <span data-ttu-id="3fc28-174">使用它还可以配置模拟输入（例如，显示或隐藏一只或两只手）和用于控制模拟输入的设备（例如电脑的键盘、鼠标和游戏手柄）。</span><span class="sxs-lookup"><span data-stu-id="3fc28-174">It also allows you to configure both simulated input, such as showing or hiding one or both hands, and devices used for controlling simulated input such as your PC's keyboard, mouse and gamepad.</span></span>

![模拟控制面板](images/emulator-simulation-control-panel.png)

* <span data-ttu-id="3fc28-176">若要隐藏或显示模拟面板，请单击工具栏按钮或按键盘上的 F7。</span><span class="sxs-lookup"><span data-stu-id="3fc28-176">To hide or show the simulation panel, click the toolbar button or press F7 on your keyboard.</span></span>
* <span data-ttu-id="3fc28-177">将鼠标悬停在控件或字段上可显示工具提示，其中包含键盘、鼠标和游戏手柄的控件。</span><span class="sxs-lookup"><span data-stu-id="3fc28-177">Hover the mouse over a control or field to display a tooltip which contains keyboard, mouse and gamepad controls for it.</span></span>
* <span data-ttu-id="3fc28-178">若要显示或隐藏手部，请切换左手或右手下方的相应开关。</span><span class="sxs-lookup"><span data-stu-id="3fc28-178">To show or hide a hand, toggle the appropriate switch under Left hand or Right hand.</span></span>
* <span data-ttu-id="3fc28-179">若要控制手部，请使用键盘上的左/右 Alt 键，或游戏手柄上的左/右缓冲键。</span><span class="sxs-lookup"><span data-stu-id="3fc28-179">To control the hand, use either the left or right Alt keys on your keyboard or the left or right bumper on the gamepad.</span></span>
* <span data-ttu-id="3fc28-180">若要将所有输入定向到一只或两只手，请单击切换开关下的图钉按钮。</span><span class="sxs-lookup"><span data-stu-id="3fc28-180">To direct all input to one or both hands, click the pushpin button under the toggle switch.</span></span>  <span data-ttu-id="3fc28-181">这相当于针对手部按住 Alt 键。</span><span class="sxs-lookup"><span data-stu-id="3fc28-181">This is the equivalent of holding the Alt key for the hand.</span></span>
* <span data-ttu-id="3fc28-182">若要控制视线方向，请单击“眼睛”部分中的图钉。</span><span class="sxs-lookup"><span data-stu-id="3fc28-182">To control the eye gaze direction, click the pushpin in the "Eyes" section.</span></span>  <span data-ttu-id="3fc28-183">这相当于按住键盘上的“Y”键。</span><span class="sxs-lookup"><span data-stu-id="3fc28-183">This is the equivalent of holding down the 'Y' key on the keyboard.</span></span>
* <span data-ttu-id="3fc28-184">若要加载房间录制内容，请单击“录制”部分中的“加载”按钮。</span><span class="sxs-lookup"><span data-stu-id="3fc28-184">To load a room recording, click the "Load" button in the "Recording" section.</span></span>  <span data-ttu-id="3fc28-185">有关详细信息，请参阅[模拟的房间](#simulated-rooms)。</span><span class="sxs-lookup"><span data-stu-id="3fc28-185">See [simulated rooms](#simulated-rooms) for more information.</span></span>
* <span data-ttu-id="3fc28-186">若要调整模拟人类或模拟输入设备在响应键盘、鼠标或游戏手柄输入时移动或旋转的速度，请单击“输入设置”旁边的齿轮图标并调整滑块。</span><span class="sxs-lookup"><span data-stu-id="3fc28-186">To adjust the speed that the simulated human or simulated input devices will move or rotate in response to keyboard, mouse or gamepad input, click the gear icon next to "Input settings" and adjust the sliders.</span></span>
* <span data-ttu-id="3fc28-187">默认情况下，键盘输入会控制模拟人类和模拟输入。</span><span class="sxs-lookup"><span data-stu-id="3fc28-187">By default, keyboard input controls the simulated human and simulated input.</span></span>  <span data-ttu-id="3fc28-188">若要将电脑的键盘输入发送到 HoloLens，请取消选中“使用键盘进行模拟”。</span><span class="sxs-lookup"><span data-stu-id="3fc28-188">To have your PC's keyboard input sent through to the HoloLens, uncheck "Use keyboard for simulation."</span></span>  <span data-ttu-id="3fc28-189">F4 是此项设置的快捷键。</span><span class="sxs-lookup"><span data-stu-id="3fc28-189">F4 is the shortcut key for this setting.</span></span>
* <span data-ttu-id="3fc28-190">如果模拟面板已显示，按 F8 会将键盘焦点转移到模拟面板。</span><span class="sxs-lookup"><span data-stu-id="3fc28-190">If the simulation panel is already visible, pressing F8 will move keyboard focus to it.</span></span>
* <span data-ttu-id="3fc28-191">若要在仿真器窗口中取消停靠模拟面板，请单击面板底部的按钮，或按键盘上的 F9。</span><span class="sxs-lookup"><span data-stu-id="3fc28-191">To undock the simulation panel from the emulator window, click the button at the bottom of the panel or press F9 on your keyboard.</span></span>  <span data-ttu-id="3fc28-192">关闭窗口或再次按 F9 会恢复为仿真器窗口。</span><span class="sxs-lookup"><span data-stu-id="3fc28-192">Closing the window or pressing F9 again will return the window to the emulator.</span></span>
* <span data-ttu-id="3fc28-193">可将模拟控制面板作为单独的应用程序启动，这样就可以通过运行 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\ 中的 PerceptionSimulationInput.exe，来连接和控制 HoloLens 2 仿真器、HoloLens 2 设备或 Windows Mixed Reality 模拟。</span><span class="sxs-lookup"><span data-stu-id="3fc28-193">The simulation control panel can be launched as a separate application, allowing you to connect to and control the HoloLens 2 Emulator, a HoloLens 2 device, or Windows Mixed Reality simulation by running PerceptionSimulationInput.exe from %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\.</span></span>

### <a name="account-tab"></a><span data-ttu-id="3fc28-194">“帐户”选项卡</span><span class="sxs-lookup"><span data-stu-id="3fc28-194">Account Tab</span></span>

<span data-ttu-id="3fc28-195">在“帐户”选项卡中，可将仿真器配置为使用 Microsoft 帐户登录。</span><span class="sxs-lookup"><span data-stu-id="3fc28-195">The Account tab allows you to configure the emulator to sign-in with a Microsoft Account.</span></span> <span data-ttu-id="3fc28-196">在测试需要用户使用帐户登录的 API 时，此配置非常有用。</span><span class="sxs-lookup"><span data-stu-id="3fc28-196">This is useful for testing APIs that require the user to be signed-in with an account.</span></span>  <span data-ttu-id="3fc28-197">切换此选项需要完全关闭并重启 HoloLens 仿真器，使设置生效。</span><span class="sxs-lookup"><span data-stu-id="3fc28-197">Toggling this option will require that you completely close and restart the HoloLens Emulator for the setting to take effect.</span></span>  <span data-ttu-id="3fc28-198">如果启用此选项，则后续启动仿真器时，系统会要求你登录，就像用户首次启动 HoloLens 时一样。</span><span class="sxs-lookup"><span data-stu-id="3fc28-198">If this option is enabled, subsequent launches of the emulator will ask you to sign-in, just like a user would the first time the HoloLens is started.</span></span>  <span data-ttu-id="3fc28-199">若要使用电脑键盘快速输入凭据，请先在模拟控制面板中关闭“使用键盘进行模拟”，或按键盘上的 F4 打开或关闭键盘设置。</span><span class="sxs-lookup"><span data-stu-id="3fc28-199">To quickly enter your credentials using your PC's keyboard, first turn off "Use keyboard for simulation" in the Simulation Control Panel, or press F4 on your keyboard to toggle the keyboard setting on or off.</span></span>

### <a name="optional-settings-tab"></a><span data-ttu-id="3fc28-200">“可选设置”选项卡</span><span class="sxs-lookup"><span data-stu-id="3fc28-200">Optional Settings Tab</span></span>

<span data-ttu-id="3fc28-201">“可选设置”选项卡显示用于启用或禁用硬件加速图形的控件。</span><span class="sxs-lookup"><span data-stu-id="3fc28-201">The Optional Settings tab will display a control to enable or disable hardware accelerated graphics.</span></span>  <span data-ttu-id="3fc28-202">默认情况下，如果电脑图形适配器的驱动程序支持硬件加速图形，则就会使用硬件加速图形。</span><span class="sxs-lookup"><span data-stu-id="3fc28-202">Hardware accelerated graphics will be used by default if supported by the driver for your PC's graphics adapter.</span></span>  <span data-ttu-id="3fc28-203">如果图形适配器的驱动程序不支持 GPU-PV，则不会显示此选项。</span><span class="sxs-lookup"><span data-stu-id="3fc28-203">If your graphics adapter's driver does not support GPU-PV, this option will not be visible.</span></span>

### <a name="diagnostics-tab"></a><span data-ttu-id="3fc28-204">“诊断”选项卡</span><span class="sxs-lookup"><span data-stu-id="3fc28-204">Diagnostics Tab</span></span>

<span data-ttu-id="3fc28-205">“诊断”选项卡以 Windows 设备门户链接的形式显示仿真器的 IP 地址，以及虚拟 GPU 的状态。</span><span class="sxs-lookup"><span data-stu-id="3fc28-205">The Diagnostics tab shows the emulator's IP address in the form of a link to Windows Device Portal along with the status of the virtual GPU.</span></span>


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a><span data-ttu-id="3fc28-206">HoloLens（第 1 代）仿真器剖析</span><span class="sxs-lookup"><span data-stu-id="3fc28-206">Anatomy of the HoloLens (1st Gen) emulator</span></span>

### <a name="main-window"></a><span data-ttu-id="3fc28-207">主窗口</span><span class="sxs-lookup"><span data-stu-id="3fc28-207">Main window</span></span>

<span data-ttu-id="3fc28-208">当仿真器启动时，你会看到一个显示 HoloLens OS 的窗口。</span><span class="sxs-lookup"><span data-stu-id="3fc28-208">When the emulator launches, you will see a window which displays the HoloLens OS.</span></span>

![HoloLens 仿真器主窗口](images/emulator-890px.png)

### <a name="toolbar"></a><span data-ttu-id="3fc28-210">工具栏</span><span class="sxs-lookup"><span data-stu-id="3fc28-210">Toolbar</span></span>

<span data-ttu-id="3fc28-211">在主窗口的右侧，可以看到仿真器工具栏。</span><span class="sxs-lookup"><span data-stu-id="3fc28-211">To the right of the main window, you will find the emulator toolbar.</span></span> <span data-ttu-id="3fc28-212">工具栏包含以下按钮：</span><span class="sxs-lookup"><span data-stu-id="3fc28-212">The toolbar contains the following buttons:</span></span>
* <span data-ttu-id="3fc28-213">![关闭图标](images/emulator-close.png)**关闭**：关闭仿真器。</span><span class="sxs-lookup"><span data-stu-id="3fc28-213">![Close icon](images/emulator-close.png) **Close**: Closes the emulator.</span></span>
* <span data-ttu-id="3fc28-214">![最小化图标](images/emulator-minimize.png)**最小化**：最小化仿真器窗口。</span><span class="sxs-lookup"><span data-stu-id="3fc28-214">![Minimize icon](images/emulator-minimize.png) **Minimize**: Minimizes the emulator window.</span></span>
* <span data-ttu-id="3fc28-215">![人类输入图标](images/emulator-control.png)**人类输入**：使用鼠标和键盘来模拟[仿真器的人类输入](#basic-emulator-input)。</span><span class="sxs-lookup"><span data-stu-id="3fc28-215">![Human input icon](images/emulator-control.png) **Human Input**: Mouse and Keyboard are used to simulate human [input to the emulator](#basic-emulator-input).</span></span>
* <span data-ttu-id="3fc28-216">![键盘和鼠标输入图标](images/emulator-input.png)**键盘和鼠标输入**：键盘和鼠标输入将作为键盘和鼠标事件直接传递给 HoloLens OS，就如同已连接蓝牙键盘和鼠标一样。</span><span class="sxs-lookup"><span data-stu-id="3fc28-216">![Keyboard and mouse input icon](images/emulator-input.png) **Keyboard and Mouse Input**: Keyboard and mouse input are passed directly to the HoloLens OS as keyboard and mouse events as if you connected a Bluetooth keyboard and mouse.</span></span>
* <span data-ttu-id="3fc28-217">![适应屏幕图标](images/emulator-fit.png)**适应屏幕**：使仿真器适合屏幕大小。</span><span class="sxs-lookup"><span data-stu-id="3fc28-217">![Fit to screen icon](images/emulator-fit.png) **Fit to Screen**: Fits the emulator to screen.</span></span>
* <span data-ttu-id="3fc28-218">![缩放图标](images/emulator-zoom.png)**缩放**：放大和缩小仿真器。</span><span class="sxs-lookup"><span data-stu-id="3fc28-218">![Zoom icon](images/emulator-zoom.png) **Zoom**: Make the emulator larger and smaller.</span></span>
* <span data-ttu-id="3fc28-219">![帮助图标](images/emulator-help.png)**帮助**：打开仿真器帮助。</span><span class="sxs-lookup"><span data-stu-id="3fc28-219">![Help icon](images/emulator-help.png) **Help**: Open emulator help.</span></span>
* <span data-ttu-id="3fc28-220">![打开设备门户图标](images/emulator-deviceportal.png)**打开设备门户**：在仿真器中打开 HoloLens OS 的 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="3fc28-220">![Open device portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>
* <span data-ttu-id="3fc28-221">![工具图标](images/emulator-tools.png)**工具**：打开“其他工具”窗格。 </span><span class="sxs-lookup"><span data-stu-id="3fc28-221">![Tools icon](images/emulator-tools.png) **Tools**: Open the **Additional Tools** pane.</span></span>

### <a name="simulation-tab"></a><span data-ttu-id="3fc28-222">“模拟”选项卡</span><span class="sxs-lookup"><span data-stu-id="3fc28-222">Simulation tab</span></span>

<span data-ttu-id="3fc28-223">“其他工具”窗格中的默认选项卡是“模拟”选项卡。  </span><span class="sxs-lookup"><span data-stu-id="3fc28-223">The default tab within the **Additional Tools** pane is the **Simulation** tab.</span></span>

![HoloLens 仿真器的“其他工具”窗格](images/emulator-simulation-500px.png)

<span data-ttu-id="3fc28-225">“模拟”选项卡显示用于在仿真器中驱动 HoloLens OS 的模拟传感器的当前状态。</span><span class="sxs-lookup"><span data-stu-id="3fc28-225">The Simulation tab shows the current state of the simulated sensors used to drive the HoloLens OS within the emulator.</span></span> <span data-ttu-id="3fc28-226">将鼠标悬停在“模拟”选项卡中的任一值上会显示工具提示，其中描述了如何控制该值。</span><span class="sxs-lookup"><span data-stu-id="3fc28-226">Hovering over any value in the Simulation tab will provide a tooltip describing how to control that value.</span></span>

### <a name="room-tab"></a><span data-ttu-id="3fc28-227">“房间”选项卡</span><span class="sxs-lookup"><span data-stu-id="3fc28-227">Room tab</span></span>

<span data-ttu-id="3fc28-228">仿真器以模拟“房间”的空间映射网格形式模拟世界坐标输入。</span><span class="sxs-lookup"><span data-stu-id="3fc28-228">The emulator simulates world input in the form of the spatial mapping mesh from simulated "rooms".</span></span> <span data-ttu-id="3fc28-229">使用此选项卡可以选择要加载的房间而不是默认房间。</span><span class="sxs-lookup"><span data-stu-id="3fc28-229">This tab lets you pick which room to load instead of the default room.</span></span>

![HoloLens 仿真器的“房间”选项卡](images/emulator-room-500px.png)

<span data-ttu-id="3fc28-231">有关详细信息，请参阅[模拟的房间](#simulated-rooms)。</span><span class="sxs-lookup"><span data-stu-id="3fc28-231">See [simulated rooms](#simulated-rooms) for more information.</span></span>

### <a name="account-tab"></a><span data-ttu-id="3fc28-232">“帐户”选项卡</span><span class="sxs-lookup"><span data-stu-id="3fc28-232">Account Tab</span></span>

<span data-ttu-id="3fc28-233">在“帐户”选项卡中，可将仿真器配置为使用 Microsoft 帐户登录。</span><span class="sxs-lookup"><span data-stu-id="3fc28-233">The Account tab allows you to configure the emulator to sign-in with a Microsoft Account.</span></span> <span data-ttu-id="3fc28-234">在测试需要用户使用帐户登录的 API 时，此配置非常有用。</span><span class="sxs-lookup"><span data-stu-id="3fc28-234">This is useful for testing API's that require the user to be signed-in with an account.</span></span> <span data-ttu-id="3fc28-235">选中此页上的框后，后续启动仿真器时，系统会要求你登录，如同用户首次启动 HoloLens 时那样。</span><span class="sxs-lookup"><span data-stu-id="3fc28-235">After checking the box on this page, subsequent launches of the emulator will ask you to sign-in, just like a user would the first time the HoloLens is started.</span></span>

## <a name="simulated-rooms"></a><span data-ttu-id="3fc28-236">模拟的房间</span><span class="sxs-lookup"><span data-stu-id="3fc28-236">Simulated Rooms</span></span>

<span data-ttu-id="3fc28-237">模拟的房间可用于在多个环境中测试应用。</span><span class="sxs-lookup"><span data-stu-id="3fc28-237">Simulated rooms are useful for testing your app in multiple environments.</span></span> <span data-ttu-id="3fc28-238">仿真器随附了多个房间，安装仿真器后，可以在 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(version)\Plugins\Rooms 中找到这些房间。</span><span class="sxs-lookup"><span data-stu-id="3fc28-238">Several rooms are shipped with the emulator and once you install the emulation, you will find them in %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(version)\Plugins\Rooms.</span></span> <span data-ttu-id="3fc28-239">所有这些房间是使用 HoloLens 在真实环境中捕获的：</span><span class="sxs-lookup"><span data-stu-id="3fc28-239">All of these rooms were captured in real environments using a HoloLens:</span></span>
* <span data-ttu-id="3fc28-240">**DefaultRoom.xef** - 配有一台电视机、一个茶几和两套沙发的小客厅。</span><span class="sxs-lookup"><span data-stu-id="3fc28-240">**DefaultRoom.xef** - A small living room with a TV, coffee table, and two sofas.</span></span> <span data-ttu-id="3fc28-241">启动仿真器时，默认会加载该房间。</span><span class="sxs-lookup"><span data-stu-id="3fc28-241">Loaded by default when you start the emulator.</span></span>
* <span data-ttu-id="3fc28-242">**Bedroom1.xef** - 配有一张桌子的小卧室。</span><span class="sxs-lookup"><span data-stu-id="3fc28-242">**Bedroom1.xef** - A small bedroom with a desk.</span></span>
* <span data-ttu-id="3fc28-243">**Bedroom2.xef** - 配有一张双人床、梳妆台、床头柜和步入式衣橱的卧室。</span><span class="sxs-lookup"><span data-stu-id="3fc28-243">**Bedroom2.xef** - A bedroom with a queen size bed, dresser, nightstands, and walk-in closet.</span></span>
* <span data-ttu-id="3fc28-244">**GreatRoom.xef** - 配有客厅、餐桌和厨房的开阔大房间。</span><span class="sxs-lookup"><span data-stu-id="3fc28-244">**GreatRoom.xef** - A large open space great room with living room, dining table, and kitchen.</span></span>
* <span data-ttu-id="3fc28-245">**LivingRoom.xef** - 配有壁炉、沙发、摇椅和摆放了花瓶的茶几的客厅。</span><span class="sxs-lookup"><span data-stu-id="3fc28-245">**LivingRoom.xef** - A living room with a fireplace, sofa, armchairs, and a coffee table with a vase.</span></span>

<span data-ttu-id="3fc28-246">也可以在 HoloLens 上（第 1 代）上使用 [Windows 设备门户](using-the-windows-device-portal.md)的“模拟”页录制你自己的房间，以便在仿真器中使用。</span><span class="sxs-lookup"><span data-stu-id="3fc28-246">You can also record your own rooms to use in the emulator using the Simulation page of the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens (1st Gen).</span></span>

<span data-ttu-id="3fc28-247">在仿真器中，你只会看到自己渲染的全息影像，而看不到全息影像后面的模拟房间。</span><span class="sxs-lookup"><span data-stu-id="3fc28-247">In the emulator, you will only see holograms that you render and you will not see the simulated room behind the holograms.</span></span> <span data-ttu-id="3fc28-248">相反，在实际的 HoloLens 中，你会同时看到两者的混合形式。</span><span class="sxs-lookup"><span data-stu-id="3fc28-248">This is in contrast to the real HoloLens where you see both blended together.</span></span> <span data-ttu-id="3fc28-249">若要在 HoloLens 仿真器中查看模拟的房间，需要更新应用，以便在场景中渲染空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="3fc28-249">If you want to see the simulated room in the HoloLens Emulator, you will need to update your app to render the spatial mapping mesh in the scene.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="3fc28-250">疑难解答</span><span class="sxs-lookup"><span data-stu-id="3fc28-250">Troubleshooting</span></span>

<span data-ttu-id="3fc28-251">安装仿真器时，可能会出错错误，指出需要“Visual Studio 2015 Update 1 和 UWP 工具版本 1.2”。 </span><span class="sxs-lookup"><span data-stu-id="3fc28-251">You may see an error while installing the emulator that you need *"Visual Studio 2015 Update 1 and UWP tools version 1.2"*.</span></span> <span data-ttu-id="3fc28-252">出现此错误的三个可能原因如下：</span><span class="sxs-lookup"><span data-stu-id="3fc28-252">There are three possible causes of this error:</span></span>
* <span data-ttu-id="3fc28-253">Visual Studio 的版本不够新（需要 Visual Studio 2019、Visual Studio 2017 或 Visual Studio 2015 Update 1 或更高版本）。</span><span class="sxs-lookup"><span data-stu-id="3fc28-253">You do not have a recent enough version of Visual Studio (Visual Studio 2019, Visual Studio 2017, or Visual Studio 2015 Update 1 or later).</span></span> <span data-ttu-id="3fc28-254">若要纠正此问题，请安装最新版本的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3fc28-254">To correct this, install the latest release of Visual Studio.</span></span>
* <span data-ttu-id="3fc28-255">已安装版本足够新的 Visual Studio，但未安装通用 Windows 平台 (UWP) 工具。</span><span class="sxs-lookup"><span data-stu-id="3fc28-255">You have a recent enough version of Visual Studio, but you do not have the Universal Windows Platform (UWP) tools installed.</span></span> <span data-ttu-id="3fc28-256">这是 Visual Studio 的一项可选功能。</span><span class="sxs-lookup"><span data-stu-id="3fc28-256">This is an optional feature for Visual Studio.</span></span>

<span data-ttu-id="3fc28-257">此外，在 Windows 的非专业版/企业版/教育版 SKU 上安装仿真器，或者未启用 Hyper-V 功能时，也可能会看到错误。</span><span class="sxs-lookup"><span data-stu-id="3fc28-257">You may also see an error installing the emulator on a non-Pro/Enterprise/Education SKU of Windows or if you do not have Hyper-V feature enabled.</span></span>
* <span data-ttu-id="3fc28-258">有关完整的要求，请阅读前面的[系统要求](#hololens-emulator-system-requirements)部分。</span><span class="sxs-lookup"><span data-stu-id="3fc28-258">Please read the [system requirements](#hololens-emulator-system-requirements) section above for a complete set of requirements.</span></span>
* <span data-ttu-id="3fc28-259">另请确保已在系统上启用 Hyper-V 功能。</span><span class="sxs-lookup"><span data-stu-id="3fc28-259">Please also ensure that Hyper-V feature has been enabled on your system.</span></span>

<span data-ttu-id="3fc28-260">如果安装成功完成，但未看到 HoloLens 仿真器作为一个部署和调试选项列出，请检查以下各项：</span><span class="sxs-lookup"><span data-stu-id="3fc28-260">If your installation completes successfully, but you do not see the HoloLens Emulator as an option for deployment and debugging, please check the following:</span></span>
* <span data-ttu-id="3fc28-261">Visual Studio 项目配置已设置为 x86（HoloLens 第一代），或 x86 或 x64（HoloLens 2 仿真器）。</span><span class="sxs-lookup"><span data-stu-id="3fc28-261">Your Visual Studio project configuration is set to x86 (HoloLens 1st Gen) or x86 or x64 (HoloLens 2 Emulator).</span></span>
* <span data-ttu-id="3fc28-262">如果使用 Visual Studio 2019，则项目配置中的平台工具集应设置为 v142。</span><span class="sxs-lookup"><span data-stu-id="3fc28-262">If using Visual Studio 2019, the Platform Toolset in your project configuration is set to v142.</span></span>

<span data-ttu-id="3fc28-263">如果安装成功完成，但尝试启动 HoloLens 仿真器时 Visual Studio 显示错误，请尝试以下操作：</span><span class="sxs-lookup"><span data-stu-id="3fc28-263">If your installation completes successfully, but Visual Studio displays an error attempting to launch the HoloLens Emulator, please try the following:</span></span>
* <span data-ttu-id="3fc28-264">以管理员身份运行 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3fc28-264">Run Visual Studio as Administrator</span></span>
* <span data-ttu-id="3fc28-265">如果曾经只安装过 Visual Studio 2019，请检查 HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots 中的“KitsRoot10”注册表值是否指向 32 位 Program Files 文件夹（例如“C:\Program Files (x86)\Windows Kits\10”）。</span><span class="sxs-lookup"><span data-stu-id="3fc28-265">If you have only ever had Visual Studio 2019 installed, verify that the registry value "KitsRoot10" at HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots points to your 32-bit Program Files folder (e.g., "C:\Program Files (x86)\Windows Kits\10").</span></span>  <span data-ttu-id="3fc28-266">如果不是，请卸载 HoloLens 仿真器，将该注册表值更改为你的 32 位 Program Files 文件夹，然后重新安装 HoloLens 仿真器。</span><span class="sxs-lookup"><span data-stu-id="3fc28-266">If it does not, uninstall the HoloLens Emulator, change the registry value to your 32-bit Program Files folder, then reinstall the HoloLens Emulator.</span></span>  <span data-ttu-id="3fc28-267">此问题在 Visual Studio 2019 16.0.3 中已得到解决。</span><span class="sxs-lookup"><span data-stu-id="3fc28-267">This issue is addressed in Visual Studio 2019 16.0.3.</span></span>

<span data-ttu-id="3fc28-268">如果启动时仿真器显示“无效的字节编码”错误对话框：</span><span class="sxs-lookup"><span data-stu-id="3fc28-268">If the emulator displays an "Invalid Byte Encoding" error dialog on launch:</span></span>
* <span data-ttu-id="3fc28-269">请删除 %localappdata%\Microsoft\XDE\HCS 中的所有文件，然后重试。</span><span class="sxs-lookup"><span data-stu-id="3fc28-269">Delete all files in %localappdata%\Microsoft\XDE\HCS and try again.</span></span>

<span data-ttu-id="3fc28-270">如果 Visual Studio 中的调试目标列表为空（例如，“启动”是唯一选项），并且你已遵循上述所有故障排除步骤：</span><span class="sxs-lookup"><span data-stu-id="3fc28-270">If your debug target list in Visual Studio is empty (for example, "Start" is the only option) and you've followed all troubleshooting steps above:</span></span>
* <span data-ttu-id="3fc28-271">请删除 %localappdata%\Microsoft\VisualStudio\\<*安装 ID*>\CoreCon 中的“ConfigurationCache”文件夹，然后重试。</span><span class="sxs-lookup"><span data-stu-id="3fc28-271">Delete the 'ConfigurationCache' folder in %localappdata%\Microsoft\VisualStudio\\<*installation id*>\CoreCon and try again.</span></span>

<span data-ttu-id="3fc28-272">如果仿真器启动时系统挂起，请对仿真器图形禁用硬件加速。</span><span class="sxs-lookup"><span data-stu-id="3fc28-272">If your system hangs when the emulator is starting, disable hardware acceleration for emulator graphics.</span></span>
* <span data-ttu-id="3fc28-273">在“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0”中创建名为“DisableGPU”的注册表 DWORD 值，并将其值设置为 1。</span><span class="sxs-lookup"><span data-stu-id="3fc28-273">Create a registry DWORD value named "DisableGPU" at HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0 and set its value to 1.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fc28-274">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fc28-274">See also</span></span>
* [<span data-ttu-id="3fc28-275">高级 HoloLens 仿真器和混合现实模拟器输入</span><span class="sxs-lookup"><span data-stu-id="3fc28-275">Advanced HoloLens Emulator and Mixed Reality Simulator input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="3fc28-276">HoloLens 仿真器软件历史记录</span><span class="sxs-lookup"><span data-stu-id="3fc28-276">HoloLens Emulator software history</span></span>](hololens-emulator-archive.md)
* [<span data-ttu-id="3fc28-277">Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="3fc28-277">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="3fc28-278">DirectX 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="3fc28-278">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
