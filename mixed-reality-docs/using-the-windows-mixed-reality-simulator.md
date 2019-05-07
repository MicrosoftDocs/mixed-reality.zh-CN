---
title: 使用 Windows Mixed Reality 模拟器
description: Windows Mixed Reality 模拟器，您可以测试混合的现实应用而无需 Windows Mixed Reality 沉浸式头戴式在 PC 上。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows 混合现实，模拟器中测试
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580705"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="67633-104">使用 Windows Mixed Reality 模拟器</span><span class="sxs-lookup"><span data-stu-id="67633-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="67633-105">Windows Mixed Reality 模拟器，您可以测试混合的现实应用而无需 Windows Mixed Reality 沉浸式头戴式在 PC 上。</span><span class="sxs-lookup"><span data-stu-id="67633-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="67633-106">它是 Windows 10 创意者更新开始可用。</span><span class="sxs-lookup"><span data-stu-id="67633-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="67633-107">模拟器是类似于[HoloLens 模拟器](using-the-hololens-emulator.md)，但模拟器不使用虚拟机。</span><span class="sxs-lookup"><span data-stu-id="67633-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="67633-108">在会话中运行 Windows 10 桌面用户，就像它们会像使用沉浸式头戴式模拟器中运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="67633-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="67633-109">通常会在沉浸式头戴式传感器读取的人和环境输入改为模拟使用键盘、 鼠标或 Xbox 控制器。</span><span class="sxs-lookup"><span data-stu-id="67633-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="67633-110">应用程序无需修改即可运行在模拟器中，并不知道也不运行在沉浸式头戴式上。</span><span class="sxs-lookup"><span data-stu-id="67633-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="67633-111">启用 Windows Mixed Reality 模拟器</span><span class="sxs-lookup"><span data-stu-id="67633-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="67633-112">**启用开发人员模式**从设置-> 更新和安全-> 面向开发人员</span><span class="sxs-lookup"><span data-stu-id="67633-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="67633-113">启动**混合现实门户**从桌面</span><span class="sxs-lookup"><span data-stu-id="67633-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="67633-114">如果这是你第一次启动门户，你将需要安装程序体验</span><span class="sxs-lookup"><span data-stu-id="67633-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="67633-115">单击**开始**</span><span class="sxs-lookup"><span data-stu-id="67633-115">Click **Get started**</span></span>
   2. <span data-ttu-id="67633-116">单击**我同意**接受协议</span><span class="sxs-lookup"><span data-stu-id="67633-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="67633-117">单击 **（适用于开发人员） 设置为模拟**继续通过安装程序而无需物理设备</span><span class="sxs-lookup"><span data-stu-id="67633-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="67633-118">单击**设置**来确认你的选择</span><span class="sxs-lookup"><span data-stu-id="67633-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="67633-119">单击**面向开发人员**混合现实门户左侧的按钮</span><span class="sxs-lookup"><span data-stu-id="67633-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="67633-120">将模拟切换开关置于**上**</span><span class="sxs-lookup"><span data-stu-id="67633-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="67633-121">启用模拟安装，并默认情况下启用模拟的 6 DOF 左的控制器。</span><span class="sxs-lookup"><span data-stu-id="67633-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="67633-122">在 Windows 之前 2019 年 5 10 个更新，安装模拟的 6 DOF 控制器需要管理员权限。</span><span class="sxs-lookup"><span data-stu-id="67633-122">Prior to the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="67633-123">如果有，你必须接受用户帐户控制对话框。</span><span class="sxs-lookup"><span data-stu-id="67633-123">You must accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="67633-124">你现在应运行与模拟 ！</span><span class="sxs-lookup"><span data-stu-id="67633-124">You should now be running with simulation!</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="67633-125">将应用部署到混合现实模拟器</span><span class="sxs-lookup"><span data-stu-id="67633-125">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="67633-126">模拟器在本地 PC 而无需虚拟机上运行，因为您只需部署到通用 Windows 应用**本地计算机**调试时。</span><span class="sxs-lookup"><span data-stu-id="67633-126">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="67633-127">基本模拟器输入</span><span class="sxs-lookup"><span data-stu-id="67633-127">Basic simulator input</span></span>

<span data-ttu-id="67633-128">控制模拟器是非常类似于许多常见的 3D 视频游戏并[HoloLens 模拟器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="67633-128">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="67633-129">可以使用键盘、 鼠标或 Xbox 控制器是输入的选项。</span><span class="sxs-lookup"><span data-stu-id="67633-129">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="67633-130">你将定向戴上沉浸式头戴式模拟的用户的操作，从而控制模拟器。</span><span class="sxs-lookup"><span data-stu-id="67633-130">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="67633-131">你的操作将模拟的用户，并导致与应用程序就像在沉浸式头戴式之间的交互。</span><span class="sxs-lookup"><span data-stu-id="67633-131">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="67633-132">**引导前滚，、 左和右**-使用 W，A、 S 和 D 键键盘，或在 Xbox 控制器上的左记忆棒。</span><span class="sxs-lookup"><span data-stu-id="67633-132">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="67633-133">**查找、 下、 左、 左右**-单击并拖动鼠标、 键盘或 Xbox 控制器上的右记忆棒上使用箭头键。</span><span class="sxs-lookup"><span data-stu-id="67633-133">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="67633-134">**按控制器上的操作按钮**-右键单击鼠标、 键盘上按 Enter 键或 Xbox 控制器上使用一个按钮。</span><span class="sxs-lookup"><span data-stu-id="67633-134">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="67633-135">**主控制器上的按下按钮**-在键盘上按 Windows 键或 F2 键或 Xbox 控制器上按 B 按钮。</span><span class="sxs-lookup"><span data-stu-id="67633-135">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="67633-136">**控制器移动滚动**-按住 Alt 键，请按住鼠标右键按钮和向上 / 向下拖动鼠标或 Xbox 控制器中按住正确的触发器和一个按钮并向上和向下移动右。</span><span class="sxs-lookup"><span data-stu-id="67633-136">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="67633-137">跟踪的控制器</span><span class="sxs-lookup"><span data-stu-id="67633-137">Tracked controllers</span></span>

<span data-ttu-id="67633-138">混合现实模拟器可以模拟最多两个手持跟踪的动作控制器。</span><span class="sxs-lookup"><span data-stu-id="67633-138">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="67633-139">启用它们在混合现实门户中使用切换开关。</span><span class="sxs-lookup"><span data-stu-id="67633-139">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="67633-140">每个模拟的控制器具有：</span><span class="sxs-lookup"><span data-stu-id="67633-140">Each simulated controller has:</span></span>
* <span data-ttu-id="67633-141">位置和方向中的空间</span><span class="sxs-lookup"><span data-stu-id="67633-141">Position and orientation in space</span></span>
* <span data-ttu-id="67633-142">“主页”按钮</span><span class="sxs-lookup"><span data-stu-id="67633-142">Home button</span></span>
* <span data-ttu-id="67633-143">“菜单”按钮</span><span class="sxs-lookup"><span data-stu-id="67633-143">Menu button</span></span>
* <span data-ttu-id="67633-144">手柄按钮</span><span class="sxs-lookup"><span data-stu-id="67633-144">Grip button</span></span>
* <span data-ttu-id="67633-145">触摸板</span><span class="sxs-lookup"><span data-stu-id="67633-145">Touchpad</span></span>
* <span data-ttu-id="67633-146">摇杆</span><span class="sxs-lookup"><span data-stu-id="67633-146">Thumbstick</span></span>
* <span data-ttu-id="67633-147">电池电量水平</span><span class="sxs-lookup"><span data-stu-id="67633-147">Battery level</span></span>

## <a name="see-also"></a><span data-ttu-id="67633-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="67633-148">See also</span></span>
* [<span data-ttu-id="67633-149">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="67633-149">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="67633-150">高级混合的现实模拟器输入</span><span class="sxs-lookup"><span data-stu-id="67633-150">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="67633-151">Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="67633-151">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="67633-152">DirectX 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="67633-152">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
