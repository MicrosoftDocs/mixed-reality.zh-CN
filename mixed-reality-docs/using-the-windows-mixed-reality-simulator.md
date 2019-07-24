---
title: 使用 Windows Mixed Reality 模拟器
description: 使用 Windows Mixed Reality 模拟器, 无需 Windows Mixed Reality 沉浸式耳机即可在电脑上测试混合现实应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, 模拟器, 测试
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580705"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="95366-104">使用 Windows Mixed Reality 模拟器</span><span class="sxs-lookup"><span data-stu-id="95366-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="95366-105">使用 Windows Mixed Reality 模拟器, 无需 Windows Mixed Reality 沉浸式耳机即可在电脑上测试混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="95366-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="95366-106">它从 Windows 10 创意者更新开始可用。</span><span class="sxs-lookup"><span data-stu-id="95366-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="95366-107">模拟器与[HoloLens 模拟器](using-the-hololens-emulator.md)类似, 但模拟器不使用虚拟机。</span><span class="sxs-lookup"><span data-stu-id="95366-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="95366-108">在模拟器中运行的应用将在 Windows 10 桌面用户会话中运行, 就像使用沉浸式耳机一样。</span><span class="sxs-lookup"><span data-stu-id="95366-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="95366-109">通常由沉浸式耳机上的传感器读取的人工和环境输入使用键盘、鼠标或 Xbox 控制器来模拟。</span><span class="sxs-lookup"><span data-stu-id="95366-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="95366-110">应用无需修改即可在模拟器中运行, 并且不知道它们没有在沉浸式耳机上运行。</span><span class="sxs-lookup"><span data-stu-id="95366-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="95366-111">启用 Windows Mixed Reality 模拟器</span><span class="sxs-lookup"><span data-stu-id="95366-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="95366-112">**启用**开发人员模式-> 更新和安全性-为开发人员 ></span><span class="sxs-lookup"><span data-stu-id="95366-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="95366-113">从桌面启动**混合现实门户**</span><span class="sxs-lookup"><span data-stu-id="95366-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="95366-114">如果这是你第一次启动门户, 则需要完成安装体验</span><span class="sxs-lookup"><span data-stu-id="95366-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="95366-115">单击 "**入门**"</span><span class="sxs-lookup"><span data-stu-id="95366-115">Click **Get started**</span></span>
   2. <span data-ttu-id="95366-116">单击 "**我同意**接受协议"</span><span class="sxs-lookup"><span data-stu-id="95366-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="95366-117">单击 "**设置" 进行模拟 (适用于开发人员)** 以在不使用物理设备的情况下进行安装</span><span class="sxs-lookup"><span data-stu-id="95366-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="95366-118">单击 "**设置**" 以确认你的选择</span><span class="sxs-lookup"><span data-stu-id="95366-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="95366-119">单击混合现实门户左侧的 "**开发人员**" 按钮</span><span class="sxs-lookup"><span data-stu-id="95366-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="95366-120">将模拟切换开关切换到**打开**</span><span class="sxs-lookup"><span data-stu-id="95366-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="95366-121">默认情况下, 启用模拟将安装并启用左模拟的 DOF 控制器。</span><span class="sxs-lookup"><span data-stu-id="95366-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="95366-122">在 Windows 10 可能2019更新之前, 安装模拟 6 DOF 控制器需要管理员权限。</span><span class="sxs-lookup"><span data-stu-id="95366-122">Prior to the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="95366-123">必须接受 "用户帐户控制" 对话框 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="95366-123">You must accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="95366-124">现在, 你应该已运行模拟!</span><span class="sxs-lookup"><span data-stu-id="95366-124">You should now be running with simulation!</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="95366-125">将应用部署到混合现实模拟器</span><span class="sxs-lookup"><span data-stu-id="95366-125">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="95366-126">由于模拟器在没有虚拟机的情况下在本地 PC 上运行, 因此, 在调试时, 只需将通用 Windows 应用程序部署到**本地计算机**上即可。</span><span class="sxs-lookup"><span data-stu-id="95366-126">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="95366-127">基本模拟器输入</span><span class="sxs-lookup"><span data-stu-id="95366-127">Basic simulator input</span></span>

<span data-ttu-id="95366-128">控制模拟器非常类似于许多常见的3D 视频游戏和[HoloLens 模拟器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="95366-128">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="95366-129">可以使用键盘、鼠标或 Xbox 控制器提供输入。</span><span class="sxs-lookup"><span data-stu-id="95366-129">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="95366-130">可以通过定向模拟用户的操作, 戴上沉浸式耳机来控制模拟器。</span><span class="sxs-lookup"><span data-stu-id="95366-130">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="95366-131">你的操作将移动模拟用户, 并与应用进行交互, 使其与沉浸式耳机上的响应相同。</span><span class="sxs-lookup"><span data-stu-id="95366-131">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="95366-132">**前后左右走动** - 使用键盘上的 WASD 键，或 Xbox 控制器上的左摇杆。</span><span class="sxs-lookup"><span data-stu-id="95366-132">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="95366-133">**上下左右注视** - 单击并拖动鼠标、使用键盘上的箭头键，或使用 Xbox 控制器上的右摇杆。</span><span class="sxs-lookup"><span data-stu-id="95366-133">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="95366-134">**操作按钮按下控制器**-右键单击鼠标, 按键盘上的 enter 键, 或使用 Xbox 控制器上的按钮。</span><span class="sxs-lookup"><span data-stu-id="95366-134">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="95366-135">**"主页" 按钮按下控制器**-按键盘上的 Windows 键或 F2 键, 或按 Xbox 控制器上的 B 按钮。</span><span class="sxs-lookup"><span data-stu-id="95366-135">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="95366-136">**用于滚动的控制器移动**-按住 Alt 键, 按住鼠标右键, 然后向上/向下拖动鼠标, 或在 Xbox 控制器中按住右触发器并向下移动, 并向下移动适当的按钮。</span><span class="sxs-lookup"><span data-stu-id="95366-136">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="95366-137">跟踪控制器</span><span class="sxs-lookup"><span data-stu-id="95366-137">Tracked controllers</span></span>

<span data-ttu-id="95366-138">混合现实模拟器最多可以模拟两个手持跟踪的运动控制器。</span><span class="sxs-lookup"><span data-stu-id="95366-138">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="95366-139">在混合现实门户中使用切换开关启用它们。</span><span class="sxs-lookup"><span data-stu-id="95366-139">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="95366-140">每个模拟控制器都有:</span><span class="sxs-lookup"><span data-stu-id="95366-140">Each simulated controller has:</span></span>
* <span data-ttu-id="95366-141">位置和方向 (空间)</span><span class="sxs-lookup"><span data-stu-id="95366-141">Position and orientation in space</span></span>
* <span data-ttu-id="95366-142">“主页”按钮</span><span class="sxs-lookup"><span data-stu-id="95366-142">Home button</span></span>
* <span data-ttu-id="95366-143">“菜单”按钮</span><span class="sxs-lookup"><span data-stu-id="95366-143">Menu button</span></span>
* <span data-ttu-id="95366-144">手柄按钮</span><span class="sxs-lookup"><span data-stu-id="95366-144">Grip button</span></span>
* <span data-ttu-id="95366-145">触摸板</span><span class="sxs-lookup"><span data-stu-id="95366-145">Touchpad</span></span>
* <span data-ttu-id="95366-146">控制</span><span class="sxs-lookup"><span data-stu-id="95366-146">Thumbstick</span></span>
* <span data-ttu-id="95366-147">电池电量水平</span><span class="sxs-lookup"><span data-stu-id="95366-147">Battery level</span></span>

## <a name="see-also"></a><span data-ttu-id="95366-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="95366-148">See also</span></span>
* [<span data-ttu-id="95366-149">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="95366-149">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="95366-150">高级混合现实模拟器输入</span><span class="sxs-lookup"><span data-stu-id="95366-150">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="95366-151">Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="95366-151">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="95366-152">DirectX 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="95366-152">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
