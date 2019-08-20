---
title: 更新混合现实的 2D UWP 应用
description: 本文概述了如何更新现有的2D 通用 Windows 平台应用, 以便在 HoloLens 和 Windows Mixed Reality 沉浸式耳机上运行。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 应用, UWP, 平面应用, HoloLens, 沉浸式耳机, 应用模型, 后退按钮, 应用栏, dpi, 分辨率, 缩放
ms.openlocfilehash: f9792a7e5fd9729bf9f5f632c699c74c58c10ddf
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414224"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a><span data-ttu-id="cf0c0-104">更新混合现实的 2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="cf0c0-104">Updating 2D UWP apps for mixed reality</span></span>

<span data-ttu-id="cf0c0-105">Windows Mixed Reality 使用户能够在您的物理或数字世界中查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-105">Windows Mixed Reality enables a user to see holograms as if they are right around you, in your physical or digital world.</span></span> <span data-ttu-id="cf0c0-106">就核心而言, HoloLens 和桌面 Pc 都将沉浸式耳机配件附加到 Windows 10 设备;这意味着, 可以在应用商店中以2D 应用的形式运行几乎所有通用 Windows 平台 (UWP) 应用。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-106">At its core, both HoloLens and the Desktop PCs you attach immersive headset accessories to are Windows 10 devices; this means that you're able to run almost all of the Universal Windows Platform (UWP) apps in the Store as 2D apps.</span></span>

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a><span data-ttu-id="cf0c0-107">为混合现实创建 2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="cf0c0-107">Creating a 2D UWP app for mixed reality</span></span>

<span data-ttu-id="cf0c0-108">向混合现实耳机引入2D 应用程序的第一步是在桌面监视器上将应用作为标准2D 应用运行。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-108">The first step to bringing a 2D app to mixed reality headsets is to get your app running as a standard 2D app on your desktop monitor.</span></span>

### <a name="building-a-new-2d-uwp-app"></a><span data-ttu-id="cf0c0-109">生成新的 2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="cf0c0-109">Building a new 2D UWP app</span></span>

<span data-ttu-id="cf0c0-110">若要为混合现实构建新的2D 应用程序, 只需生成标准的2D 通用 Windows 平台 (UWP) 应用。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-110">To build a new 2D app for mixed reality, you simply build a standard 2D Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="cf0c0-111">对于该应用程序, 无需进行其他应用程序更改, 就能在混合现实中以石板的形式运行。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-111">No other app changes are required for that app to then run as a slate in mixed reality.</span></span>

<span data-ttu-id="cf0c0-112">若要开始生成二维 UWP 应用, 请参阅[创建第一个应用一](https://docs.microsoft.com/windows/uwp/get-started/your-first-app)文。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-112">To get started building a 2D UWP app, check out the [Create your first app](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) article.</span></span>

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a><span data-ttu-id="cf0c0-113">将现有2D 应用商店应用引入 UWP</span><span class="sxs-lookup"><span data-stu-id="cf0c0-113">Bringing an existing 2D Store app to UWP</span></span>

<span data-ttu-id="cf0c0-114">如果存储中已有 2D Windows 应用, 则必须先确保它面向 Windows 10 通用 Windows 平台 (UWP)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-114">If you already have a 2D Windows app in the Store, you must first ensure it is targeting the Windows 10 Universal Windows Platform (UWP).</span></span> <span data-ttu-id="cf0c0-115">下面是你目前可以使用应用商店应用的所有潜在起点:</span><span class="sxs-lookup"><span data-stu-id="cf0c0-115">Here are all the potential starting points you may have with your Store app today:</span></span>
<br>

|  <span data-ttu-id="cf0c0-116">起点</span><span class="sxs-lookup"><span data-stu-id="cf0c0-116">Starting Point</span></span>  |  <span data-ttu-id="cf0c0-117">AppX 清单平台目标</span><span class="sxs-lookup"><span data-stu-id="cf0c0-117">AppX Manifest Platform Target</span></span>  |  <span data-ttu-id="cf0c0-118">如何实现此通用？</span><span class="sxs-lookup"><span data-stu-id="cf0c0-118">How to make this Universal?</span></span> | 
|----------|----------|----------|
|  <span data-ttu-id="cf0c0-119">Windows Phone (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="cf0c0-119">Windows Phone (Silverlight)</span></span>  |  <span data-ttu-id="cf0c0-120">Silverlight 应用程序清单</span><span class="sxs-lookup"><span data-stu-id="cf0c0-120">Silverlight App Manifest</span></span> |  <span data-ttu-id="cf0c0-121">[迁移到 WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span><span class="sxs-lookup"><span data-stu-id="cf0c0-121">[Migrate to WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span></span> | 
|  <span data-ttu-id="cf0c0-122">Windows Phone 8.1 通用</span><span class="sxs-lookup"><span data-stu-id="cf0c0-122">Windows Phone 8.1 Universal</span></span>  |  <span data-ttu-id="cf0c0-123">8.1 AppX 清单, 不包括平台目标</span><span class="sxs-lookup"><span data-stu-id="cf0c0-123">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="cf0c0-124">将应用迁移到通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="cf0c0-124">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="cf0c0-125">Windows 应用商店8</span><span class="sxs-lookup"><span data-stu-id="cf0c0-125">Windows Store 8</span></span>  |  <span data-ttu-id="cf0c0-126">8个不包括平台目标的 AppX 清单</span><span class="sxs-lookup"><span data-stu-id="cf0c0-126">8 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="cf0c0-127">将应用迁移到通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="cf0c0-127">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="cf0c0-128">Windows 应用商店8.1 通用</span><span class="sxs-lookup"><span data-stu-id="cf0c0-128">Windows Store 8.1 Universal</span></span>  |  <span data-ttu-id="cf0c0-129">8.1 AppX 清单, 不包括平台目标</span><span class="sxs-lookup"><span data-stu-id="cf0c0-129">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="cf0c0-130">将应用迁移到通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="cf0c0-130">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 

<span data-ttu-id="cf0c0-131">如果当前构建为 Win32 应用 ("PC, Mac & Linux 独立" 生成目标) 的 2D Unity 应用程序, 则可以通过将 Unity 切换到 "通用 Windows 平台" 生成目标来定位混合现实。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-131">If you have a 2D Unity app today built as a Win32 app (the "PC, Mac & Linux Standalone" build target), you can target mixed reality by switching Unity to the "Universal Windows Platform" build target instead.</span></span>

<span data-ttu-id="cf0c0-132">接下来, 我们将讨论如何使用[下面](#publish-and-maintain-your-universal-app)的 Windows 全息设备系列将应用专用于 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-132">We'll talk about ways that you can restrict your app specifically to HoloLens using the Windows.Holographic device family [below](#publish-and-maintain-your-universal-app).</span></span>

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a><span data-ttu-id="cf0c0-133">在 Windows Mixed Reality 沉浸式耳机中运行你的2D 应用</span><span class="sxs-lookup"><span data-stu-id="cf0c0-133">Run your 2D app in a Windows Mixed Reality immersive headset</span></span>

<span data-ttu-id="cf0c0-134">如果已将2D 应用部署到桌面计算机, 在该计算机上进行开发, 并在显示器上尝试使用它, 则已准备好在沉浸式桌面耳机中试用!</span><span class="sxs-lookup"><span data-stu-id="cf0c0-134">If you've deployed your 2D app to the desktop machine where you are developing and tried it out on your monitor, you're already ready to try it out in an immersive desktop headset!</span></span>

<span data-ttu-id="cf0c0-135">只需进入混合现实耳机内的 "开始" 菜单, 然后从此处启动应用即可。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-135">Just go to the Start menu within the mixed reality headset and launch the app from there.</span></span> <span data-ttu-id="cf0c0-136">桌面 shell 和全息 shell 共享同一组 UWP 应用, 因此, 从 Visual Studio 部署后, 应用应已存在。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-136">The desktop shell and the holographic shell both share the same set of UWP apps, and so the app should already be present once you've deployed from Visual Studio.</span></span>

## <a name="targeting-both-immersive-headsets-and-hololens"></a><span data-ttu-id="cf0c0-137">面向沉浸式耳机和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="cf0c0-137">Targeting both immersive headsets and HoloLens</span></span>

<span data-ttu-id="cf0c0-138">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="cf0c0-138">Congratulations!</span></span> <span data-ttu-id="cf0c0-139">应用现在正在使用 Windows 10 通用 Windows 平台 (UWP)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-139">Your app is now using the Windows 10 Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="cf0c0-140">现在, 你的应用程序能够在当前的 Windows 设备 (如桌面、移动、Xbox、Windows Mixed Reality 沉浸式耳机和 HoloLens) 上运行, 以及将来的 Windows 设备。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-140">Your app is now capable of running on today's Windows devices like Desktop, Mobile, Xbox, Windows Mixed Reality immersive headsets, and HoloLens, as well as future Windows devices.</span></span> <span data-ttu-id="cf0c0-141">但是, 若要实际将所有这些设备作为目标, 需要确保应用面向 Windows 通用设备系列。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-141">However, to actually target all of those devices, you will need to ensure your app is targeting the Windows.Universal device family.</span></span>

### <a name="change-your-device-family-to-windowsuniversal"></a><span data-ttu-id="cf0c0-142">将设备系列改为 Windows 通用</span><span class="sxs-lookup"><span data-stu-id="cf0c0-142">Change your device family to Windows.Universal</span></span>

<span data-ttu-id="cf0c0-143">现在, 让我们跳转到 AppX 清单, 确保 Windows 10 UWP 应用可在 HoloLens 上运行:</span><span class="sxs-lookup"><span data-stu-id="cf0c0-143">Now let's jump into your AppX manifest to ensure your Windows 10 UWP app can run on HoloLens:</span></span>
* <span data-ttu-id="cf0c0-144">用**Visual Studio**打开应用的解决方案文件, 并导航到应用程序包清单</span><span class="sxs-lookup"><span data-stu-id="cf0c0-144">Open your app's solution file with **Visual Studio** and navigate to the app package manifest</span></span>
* <span data-ttu-id="cf0c0-145">右键单击解决方案中的**appxmanifest.xml**文件, 然后单击 "**查看代码**"</span><span class="sxs-lookup"><span data-stu-id="cf0c0-145">Right click the **Package.appxmanifest** file in your Solution and go to **View Code**</span></span><br>
  <span data-ttu-id="cf0c0-146">![解决方案资源管理器中的 appxmanifest.xml](images/openappxmanifest-500px.png)</span><span class="sxs-lookup"><span data-stu-id="cf0c0-146">![package.appxmanifest in Solution Explorer](images/openappxmanifest-500px.png)</span></span><br>
* <span data-ttu-id="cf0c0-147">确保目标平台在 "依赖关系" 部分中为 "Windows 通用"。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-147">Ensure your Target Platform is Windows.Universal in the dependencies section</span></span>
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* <span data-ttu-id="cf0c0-148">把!</span><span class="sxs-lookup"><span data-stu-id="cf0c0-148">Save!</span></span>

<span data-ttu-id="cf0c0-149">如果不使用 Visual Studio 作为开发环境, 则可以在所选的文本编辑器中打开**appxmanifest.xml** , 以确保面向的是**Windows 通用** *y*。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-149">If you do not use Visual Studio for your development environment, you can open **AppXManifest.xml** in the text editor of your choice to ensure you're targeting the **Windows.Universal** *TargetDeviceFamily*.</span></span>

### <a name="run-in-the-hololens-emulator"></a><span data-ttu-id="cf0c0-150">在 HoloLens 模拟器中运行</span><span class="sxs-lookup"><span data-stu-id="cf0c0-150">Run in the HoloLens Emulator</span></span>

<span data-ttu-id="cf0c0-151">现在, UWP 应用面向 "Windows 通用", 接下来让我们构建你的应用, 并在[HoloLens 模拟器](using-the-hololens-emulator.md)中运行它。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-151">Now that your UWP app targets "Windows.Universal", let's build your app and run it in the [HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
* <span data-ttu-id="cf0c0-152">请确保已[安装 HoloLens 模拟器](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-152">Make sure you have [installed the HoloLens Emulator](install-the-tools.md).</span></span>
* <span data-ttu-id="cf0c0-153">在 Visual Studio 中, 选择应用的**x86**生成配置</span><span class="sxs-lookup"><span data-stu-id="cf0c0-153">In Visual Studio, select the **x86** build configuration for your app</span></span>

  ![Visual Studio 中的 x86 生成配置](images/x86setting.png)<br>
* <span data-ttu-id="cf0c0-155">在 "部署目标" 下拉菜单中选择 " **HoloLens 模拟器**"</span><span class="sxs-lookup"><span data-stu-id="cf0c0-155">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span>

  ![部署目标列表中的 HoloLens 模拟器](images/deployemulator-500px.png)<br>
* <span data-ttu-id="cf0c0-157">选择 "**调试" > "开始调试**" 以部署应用并启动调试。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-157">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="cf0c0-158">模拟器将启动并运行您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-158">The emulator will start and run your app.</span></span>
* <span data-ttu-id="cf0c0-159">使用键盘、鼠标和/或 Xbox 控制器, 将您的应用程序置于世界中以启动它。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-159">With a keyboard, mouse, and/or an Xbox controller, place your app in the world to launch it.</span></span>

  ![使用 UWP 示例加载的 HoloLens 模拟器](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a><span data-ttu-id="cf0c0-161">后续步骤</span><span class="sxs-lookup"><span data-stu-id="cf0c0-161">Next steps</span></span>

<span data-ttu-id="cf0c0-162">此时, 可能会出现以下两种情况之一:</span><span class="sxs-lookup"><span data-stu-id="cf0c0-162">At this point, one of two things can happen:</span></span>
1. <span data-ttu-id="cf0c0-163">应用程序将显示它的初始, 并在将其放入模拟器后开始运行!</span><span class="sxs-lookup"><span data-stu-id="cf0c0-163">Your app will show its splash and start running after it is placed in the Emulator!</span></span> <span data-ttu-id="cf0c0-164">出色!</span><span class="sxs-lookup"><span data-stu-id="cf0c0-164">Awesome!</span></span>
2. <span data-ttu-id="cf0c0-165">或者, 在看到2D 全息图的加载动画后, 加载将停止, 您将在其初始屏幕上看到您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-165">Or after you see a loading animation for a 2D hologram, loading will stop and you will just see your app at its splash screen.</span></span> <span data-ttu-id="cf0c0-166">这意味着出现了问题, 并将进行更多调查, 以了解如何在混合现实中实现应用程序的生活。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-166">This means that something went wrong and it will take more investigation to understand how to bring your app to life in Mixed Reality.</span></span>

<span data-ttu-id="cf0c0-167">若要了解可能导致 UWP 应用无法在 HoloLens 上启动的内容, 必须进行调试。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-167">To get to the bottom of what may be causing your UWP app not to start on HoloLens, you'll have to debug.</span></span>

### <a name="running-your-uwp-app-in-the-debugger"></a><span data-ttu-id="cf0c0-168">在调试器中运行 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="cf0c0-168">Running your UWP app in the debugger</span></span>

<span data-ttu-id="cf0c0-169">这些步骤将指导你使用 Visual Studio 调试器调试 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-169">These steps will walk you through debugging your UWP app using the Visual Studio debugger.</span></span>
* <span data-ttu-id="cf0c0-170">如果尚未执行此操作, 请在 Visual Studio 中打开解决方案。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-170">If you haven't already done so, open your solution in Visual Studio.</span></span> <span data-ttu-id="cf0c0-171">将目标更改为**HoloLens 模拟器**, 将生成配置更改为**x86**。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-171">Change the target to the **HoloLens Emulator** and the build configuration to **x86**.</span></span>
* <span data-ttu-id="cf0c0-172">选择 "**调试" > "开始调试**" 以部署应用并启动调试。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-172">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="cf0c0-173">在世界上, 用鼠标、键盘或 Xbox 控制器放置应用程序。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-173">Place the app in the world with your mouse, keyboard, or Xbox controller.</span></span>
* <span data-ttu-id="cf0c0-174">Visual Studio 现在应在应用代码中的某个位置中断。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-174">Visual Studio should now break somewhere in your app code.</span></span>
  - <span data-ttu-id="cf0c0-175">如果应用由于未处理的错误而不会立即崩溃或进入调试器, 请完成应用的核心功能测试, 以确保一切正常运行且正常运行。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-175">If your app doesn't immediately crash or break into the debugger because of an unhandled error, then go through a test pass of the core features of your app to make sure everything is running and functional.</span></span> <span data-ttu-id="cf0c0-176">你可能会看到如下所示的错误 (正在处理的内部异常)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-176">You may see errors like pictured below (internal exceptions that are being handled).</span></span> <span data-ttu-id="cf0c0-177">若要确保不会错过影响应用体验的内部错误, 请运行自动测试和单元测试, 以确保一切都按预期方式运行。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-177">To ensure you don't miss internal errors that impact the experience of your app, run through your automated tests and unit tests to make sure everything behaves as expected.</span></span>

![使用 UWP 示例加载的 HoloLens 模拟器显示系统异常](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a><span data-ttu-id="cf0c0-179">更新用户界面</span><span class="sxs-lookup"><span data-stu-id="cf0c0-179">Update your UI</span></span>

<span data-ttu-id="cf0c0-180">现在, UWP 应用运行在沉浸式耳机上,/或在作为二维全息图的情况下运行, 接下来我们要确保它看起来很漂亮。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-180">Now that your UWP app is running on immersive headsets and/or HoloLens as a 2D hologram, next we'll make sure it looks beautiful.</span></span> <span data-ttu-id="cf0c0-181">下面是一些需要考虑的事项:</span><span class="sxs-lookup"><span data-stu-id="cf0c0-181">Here are some things to consider:</span></span>
* <span data-ttu-id="cf0c0-182">Windows Mixed Reality 会按固定分辨率和 DPI (等同于853x480 有效像素) 运行所有2D 应用。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-182">Windows Mixed Reality will run all 2D apps at a fixed resolution and DPI that equates to 853x480 effective pixels.</span></span> <span data-ttu-id="cf0c0-183">考虑设计是否需要优化此规模, 并查看下面的设计指南, 以改善在 HoloLens 和沉浸式耳机上的体验。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-183">Consider if your design needs refinement at this scale and review the design guidance below to improve your experience on HoloLens and immersive headsets.</span></span>
* <span data-ttu-id="cf0c0-184">Windows Mixed Reality[不支持](app-model.md)2d 动态磁贴。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-184">Windows Mixed Reality [does not support](app-model.md) 2D live tiles.</span></span> <span data-ttu-id="cf0c0-185">如果你的核心功能显示了有关动态磁贴的信息, 请考虑将该信息移回你的应用程序或浏览[3d 应用程序启动器](3d-app-launcher-design-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-185">If your core functionality is showing information on a live tile, consider moving that information back into your app or explore [3D app launchers](3d-app-launcher-design-guidance.md).</span></span>

### <a name="2d-app-view-resolution-and-scale-factor"></a><span data-ttu-id="cf0c0-186">2D 应用视图分辨率和缩放比例</span><span class="sxs-lookup"><span data-stu-id="cf0c0-186">2D app view resolution and scale factor</span></span>

![从响应式设计](images/scale-500px.png)

<span data-ttu-id="cf0c0-188">Windows 10 将所有视觉对象设计从真实屏幕像素变为**有效像素**。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-188">Windows 10 moves all visual design from real screen pixels to **effective pixels**.</span></span> <span data-ttu-id="cf0c0-189">这意味着, 开发人员会按照 Windows 10 人体学接口指导原则为有效像素设计用户界面, 并确保这些有效像素的大小适用于跨设备、分辨率、DPI 等的可用性。有关详细信息, 请参阅[MSDN 上的这篇精彩阅读](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)[版本](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-189">That means, developers design their UI following the Windows 10 Human Interface Guidelines for effective pixels, and Windows scaling ensures those effective pixels are the right size for usability across devices, resolutions, DPI, etc. See this [great read on MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) to learn more as well as this [BUILD presentation](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).</span></span>

<span data-ttu-id="cf0c0-190">即使有独特的功能可以将应用放在世界上的距离范围内, 也建议使用类似于电视的观看距离, 以获得最佳的可读性, 并与注视/手势交互。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-190">Even with the unique ability to place apps in your world at a range of distances, TV-like viewing distances are recommended to produce the best readability and interaction with gaze/gesture.</span></span> <span data-ttu-id="cf0c0-191">因此, 混合现实中的虚拟石板会在以下位置显示平面 UWP 视图:</span><span class="sxs-lookup"><span data-stu-id="cf0c0-191">Because of that, a virtual slate in the Mixed Reality Home will display your flat UWP view at:</span></span>

<span data-ttu-id="cf0c0-192">**1280x720, 150% DPI**(853x480 有效像素)</span><span class="sxs-lookup"><span data-stu-id="cf0c0-192">**1280x720, 150%DPI** (853x480 effective pixels)</span></span>

<span data-ttu-id="cf0c0-193">此分辨率具有几个优点:</span><span class="sxs-lookup"><span data-stu-id="cf0c0-193">This resolution has several advantages:</span></span>
* <span data-ttu-id="cf0c0-194">这一有效的像素布局将与 tablet 或小型桌面具有相同的信息密度。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-194">This effective pixel layout will have about the same information density as a tablet or small desktop.</span></span>
* <span data-ttu-id="cf0c0-195">它与在 Xbox One 上运行的 UWP 应用的固定 DPI 和有效像素匹配, 实现跨设备的无缝体验。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-195">It matches the fixed DPI and effective pixels for UWP apps running on Xbox One, enabling seamless experiences across devices.</span></span>
* <span data-ttu-id="cf0c0-196">当在世界各地的应用范围内扩展时, 此大小看起来很好。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-196">This size looks good when scaled across our range of operating distances for apps in the world.</span></span>

### <a name="2d-app-view-interface-design-best-practices"></a><span data-ttu-id="cf0c0-197">2D 应用视图界面设计最佳实践</span><span class="sxs-lookup"><span data-stu-id="cf0c0-197">2D app view interface design best practices</span></span>

<span data-ttu-id="cf0c0-198">**看**</span><span class="sxs-lookup"><span data-stu-id="cf0c0-198">**Do:**</span></span>
* <span data-ttu-id="cf0c0-199">遵循[Windows 10 人体学接口指导原则 (HIG)](https://dev.windows.com/design) , 了解样式、字号和按钮大小。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-199">Follow the [Windows 10 Human Interface Guidelines (HIG)](https://dev.windows.com/design) for styles, font sizes and button sizes.</span></span> <span data-ttu-id="cf0c0-200">HoloLens 将执行工作以确保你的应用程序具有兼容的应用模式、可读文本大小和适当的命中目标大小调整。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-200">HoloLens will do the work to ensure your app will have compatible app patterns, readable text sizes, and appropriate hit target sizing.</span></span>
* <span data-ttu-id="cf0c0-201">确保你的 UI 遵循最佳做法, 以便在 HoloLen 的独特分辨率和 DPI 上最好地查看最佳[设计](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-201">Ensure your UI follows best practices for [responsive design](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) to look best at HoloLen's unique resolution and DPI.</span></span>
* <span data-ttu-id="cf0c0-202">使用 Windows 中的 "薄" 颜色主题建议。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-202">Use the "light" color theme recommendations from Windows.</span></span>

<span data-ttu-id="cf0c0-203">**不要：**</span><span class="sxs-lookup"><span data-stu-id="cf0c0-203">**Don't:**</span></span>
* <span data-ttu-id="cf0c0-204">在混合现实情况下, 使用户的 UI 变化太大, 以确保用户在耳机中体验和使用熟悉的体验。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-204">Change your UI too drastically when in mixed reality, to ensure users have a familiar experience in and out of the headset.</span></span>

### <a name="understand-the-app-model"></a><span data-ttu-id="cf0c0-205">了解应用模型</span><span class="sxs-lookup"><span data-stu-id="cf0c0-205">Understand the app model</span></span>

<span data-ttu-id="cf0c0-206">混合现实的[应用模型](app-model.md)设计为使用混合现实宿主, 其中的多个应用一起提供。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-206">The [app model](app-model.md) for mixed reality is designed to use the Mixed Reality Home, where many apps live together.</span></span> <span data-ttu-id="cf0c0-207">请将此视为与桌面等效的混合现实, 其中你可以同时运行多个2D 应用。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-207">Think of this as the mixed reality equivalent of the desktop, where you run many 2D apps at once.</span></span> <span data-ttu-id="cf0c0-208">这会影响应用程序的生命周期、磁贴和其他关键功能。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-208">This has implications on app life cycle, Tiles, and other key features of your app.</span></span>

### <a name="app-bar-and-back-button"></a><span data-ttu-id="cf0c0-209">应用栏和 "后退" 按钮</span><span class="sxs-lookup"><span data-stu-id="cf0c0-209">App bar and back button</span></span>

<span data-ttu-id="cf0c0-210">二维视图在其内容上方使用应用栏进行修饰。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-210">2D views are decorated with a app bar above their content.</span></span> <span data-ttu-id="cf0c0-211">应用程序栏有两个特定于应用的个性化设置:</span><span class="sxs-lookup"><span data-stu-id="cf0c0-211">The app bar has two points of app-specific personalization:</span></span>

<span data-ttu-id="cf0c0-212">**标题:** 显示与应用程序实例关联的磁贴的*displayname*</span><span class="sxs-lookup"><span data-stu-id="cf0c0-212">**Title:** displays the *displayname* of the Tile associated with the app instance</span></span>

<span data-ttu-id="cf0c0-213">**后退按钮：** 将引发 *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 时按下事件。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-213">**Back Button:** raises the *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* event when pressed.</span></span> <span data-ttu-id="cf0c0-214">后退按钮可见性由 *[SystemNavigationManager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* 控制。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-214">Back Button visibility is controlled by *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*.</span></span>

<span data-ttu-id="cf0c0-215">![2D 应用视图中的应用程序栏 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span><span class="sxs-lookup"><span data-stu-id="cf0c0-215">![App bar UI in 2D app view](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span></span><br>
<span data-ttu-id="cf0c0-216">*2D 应用视图中的应用程序栏 UI*</span><span class="sxs-lookup"><span data-stu-id="cf0c0-216">*App bar UI in 2D app view*</span></span>

### <a name="test-your-2d-apps-design"></a><span data-ttu-id="cf0c0-217">测试您的2D 应用程序设计</span><span class="sxs-lookup"><span data-stu-id="cf0c0-217">Test your 2D app's design</span></span>

<span data-ttu-id="cf0c0-218">务必要测试您的应用程序以确保文本是可读的, 这些按钮是不再的, 并且整个应用程序看起来是正确的。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-218">It is important to test your app to make sure the text is readable, the buttons are targetable, and the overall app looks correct.</span></span> <span data-ttu-id="cf0c0-219">可以在桌面耳机、HoloLens、模拟器或将分辨率设置为 1280x720 @150% 的触摸设备上进行[测试](testing-your-app-on-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-219">You can [test](testing-your-app-on-hololens.md) on a desktop headset, a HoloLens, an emulator, or a touch device with resolution set to 1280x720 @150%.</span></span>

## <a name="new-input-possibilities"></a><span data-ttu-id="cf0c0-220">新的输入可能性</span><span class="sxs-lookup"><span data-stu-id="cf0c0-220">New input possibilities</span></span>

<span data-ttu-id="cf0c0-221">HoloLens 使用高级深度传感器来查看世界并看到用户。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-221">HoloLens uses advanced depth sensors to see the world and see users.</span></span> <span data-ttu-id="cf0c0-222">这样就可以实现先进的手势, 如[布隆](gestures.md#bloom)和[分流](gestures.md#air-tap)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-222">This enables advanced hand gestures like [bloom](gestures.md#bloom) and [air-tap](gestures.md#air-tap).</span></span> <span data-ttu-id="cf0c0-223">强大的麦克风还启用了[语音体验](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-223">Powerful microphones also enable [voice experiences](voice-input.md).</span></span>

<span data-ttu-id="cf0c0-224">使用桌面耳机, 用户可以使用运动控制器指向应用并采取措施。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-224">With Desktop headsets, users can use motion controllers to point at apps and take action.</span></span> <span data-ttu-id="cf0c0-225">他们还可以使用游戏板, 将对象定位在其看板上。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-225">They can also use a gamepad, targeting objects with their gaze.</span></span>

<span data-ttu-id="cf0c0-226">Windows 负责处理 UWP 应用的所有复杂性, 将[注视](gaze.md)、手势、语音和运动控制器输入转换为抽象出输入机制的[指针事件](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-226">Windows takes care of all of this complexity for UWP apps, translating your [gaze](gaze.md), gestures, voice and motion controller input to [pointer events](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) that abstract away the input mechanism.</span></span> <span data-ttu-id="cf0c0-227">例如, 用户可能已在运动控制器上进行了一次轻点击, 或在运动控制器上拉取了 Select 触发器, 但2D 应用程序无需知道输入来自何处-它们只是在触摸屏上看到2D 触摸按下。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-227">For example, a user may have done an air-tap with their hand or pulled the Select trigger on a motion controller, but 2D applications don't need to know where the input came from - they just see a 2D touch press, as if on a touchscreen.</span></span>

<span data-ttu-id="cf0c0-228">下面是你在将 UWP 应用引入 HoloLens 时应了解的高级概念/方案:</span><span class="sxs-lookup"><span data-stu-id="cf0c0-228">Here are the high level concepts/scenarios you should understand for input when bringing your UWP app to HoloLens:</span></span>
* <span data-ttu-id="cf0c0-229">[注视](gaze.md)悬停事件, 这可能会意外触发菜单、浮出控件或其他用户界面元素, 只需 gazing 围绕应用程序进行弹出。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-229">[Gaze](gaze.md) turns into hover events, which can unexpectedly trigger menus, flyouts or other user interface elements to pop up just by gazing around your app.</span></span>
* <span data-ttu-id="cf0c0-230">看不到鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-230">Gaze is not as precise as mouse input.</span></span> <span data-ttu-id="cf0c0-231">针对 HoloLens 使用适当大小的命中目标, 类似于触摸友好的移动应用程序。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-231">Use appropriately sized hit targets for HoloLens, similar to touch-friendly mobile applications.</span></span> <span data-ttu-id="cf0c0-232">接近应用边缘的小元素尤其难与交互。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-232">Small elements near the edges of the app are especially hard to interact with.</span></span>
* <span data-ttu-id="cf0c0-233">用户必须将输入模式切换为从滚动到拖到两个手指平移。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-233">Users must switch input modes to go from scrolling to dragging to two finger panning.</span></span> <span data-ttu-id="cf0c0-234">如果你的应用程序是针对触控输入设计的, 请考虑确保没有任何主要功能被锁定在两个 finger 平移后。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-234">If your app was designed for touch input, consider ensuring that no major functionality is locked behind two finger panning.</span></span> <span data-ttu-id="cf0c0-235">如果是这样, 请考虑采用其他输入机制, 如可以启动两个 finger 平移的按钮。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-235">If so, consider having alternative input mechanisms like buttons that can initiate two finger panning.</span></span> <span data-ttu-id="cf0c0-236">例如, 地图应用可以使用两个手指平移进行缩放, 但具有一个加号、减号和旋转按钮, 可通过单击来模拟相同的缩放交互。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-236">For example, the Maps app can zoom with two finger panning but has a plus, minus, and rotate button to simulate the same zoom interactions with single clicks.</span></span>

<span data-ttu-id="cf0c0-237">[语音输入](voice-input.md)是混合现实体验的关键部分。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-237">[Voice input](voice-input.md) is a critical part of the mixed reality experience.</span></span> <span data-ttu-id="cf0c0-238">使用耳机时, 我们已启用了 Windows 10 中所有的语音 Api。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-238">We've enabled all of the speech APIs that are in Windows 10 powering Cortana when using a headset.</span></span>

## <a name="publish-and-maintain-your-universal-app"></a><span data-ttu-id="cf0c0-239">发布和维护你的通用应用</span><span class="sxs-lookup"><span data-stu-id="cf0c0-239">Publish and Maintain your Universal app</span></span>

<span data-ttu-id="cf0c0-240">应用启动并运行后, 打包应用以将[其提交到 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)。</span><span class="sxs-lookup"><span data-stu-id="cf0c0-240">Once your app is up and running, package your app to [submit it to the Microsoft Store](submitting-an-app-to-the-microsoft-store.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf0c0-241">请参阅</span><span class="sxs-lookup"><span data-stu-id="cf0c0-241">See also</span></span>
* [<span data-ttu-id="cf0c0-242">应用模型</span><span class="sxs-lookup"><span data-stu-id="cf0c0-242">App model</span></span>](app-model.md)
* [<span data-ttu-id="cf0c0-243">凝视</span><span class="sxs-lookup"><span data-stu-id="cf0c0-243">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="cf0c0-244">姿态</span><span class="sxs-lookup"><span data-stu-id="cf0c0-244">Gesture</span></span>](gestures.md)
* [<span data-ttu-id="cf0c0-245">运动控制器</span><span class="sxs-lookup"><span data-stu-id="cf0c0-245">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="cf0c0-246">语音输入</span><span class="sxs-lookup"><span data-stu-id="cf0c0-246">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="cf0c0-247">将应用提交到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="cf0c0-247">Submitting an app to the Microsoft Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="cf0c0-248">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="cf0c0-248">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
