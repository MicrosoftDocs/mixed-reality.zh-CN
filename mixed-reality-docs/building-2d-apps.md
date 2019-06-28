---
title: 更新适用于混合现实的 2D UWP 应用
description: 本文概述了更新现有的 2D 通用 Windows 平台应用 HoloLens 和 Windows Mixed Reality 沉浸式耳机上运行。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 应用程序中，UWP，平面应用，HoloLens，沉浸式耳机，应用程序模型返回按钮，应用程序栏、 dpi，分辨率，规模
ms.openlocfilehash: f9792a7e5fd9729bf9f5f632c699c74c58c10ddf
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414224"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a><span data-ttu-id="0ae54-104">更新适用于混合现实的 2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="0ae54-104">Updating 2D UWP apps for mixed reality</span></span>

<span data-ttu-id="0ae54-105">Windows Mixed Reality，用户若要查看全息，就好像它们是右周围，还是数字世界中。</span><span class="sxs-lookup"><span data-stu-id="0ae54-105">Windows Mixed Reality enables a user to see holograms as if they are right around you, in your physical or digital world.</span></span> <span data-ttu-id="0ae54-106">就其核心而言，HoloLens 和桌面 Pc 将附加到的沉浸式头戴式附件是 Windows 10 设备;这意味着你能够以 2D 应用程序存储区中运行几乎所有通用 Windows 平台 (UWP) 应用。</span><span class="sxs-lookup"><span data-stu-id="0ae54-106">At its core, both HoloLens and the Desktop PCs you attach immersive headset accessories to are Windows 10 devices; this means that you're able to run almost all of the Universal Windows Platform (UWP) apps in the Store as 2D apps.</span></span>

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a><span data-ttu-id="0ae54-107">创建适用于混合现实的 2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="0ae54-107">Creating a 2D UWP app for mixed reality</span></span>

<span data-ttu-id="0ae54-108">2D 应用程序引入混合的现实耳机的第一步是获取应用程序作为标准 2D 应用程序在桌面监视器上运行。</span><span class="sxs-lookup"><span data-stu-id="0ae54-108">The first step to bringing a 2D app to mixed reality headsets is to get your app running as a standard 2D app on your desktop monitor.</span></span>

### <a name="building-a-new-2d-uwp-app"></a><span data-ttu-id="0ae54-109">生成新的 2D UWP 应用</span><span class="sxs-lookup"><span data-stu-id="0ae54-109">Building a new 2D UWP app</span></span>

<span data-ttu-id="0ae54-110">若要生成新的 2D 混合现实应用，只需生成标准 2D 通用 Windows 平台 (UWP) 应用。</span><span class="sxs-lookup"><span data-stu-id="0ae54-110">To build a new 2D app for mixed reality, you simply build a standard 2D Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="0ae54-111">需要对该应用，然后作为一台平板电脑运行混合现实中任何其他应用更改不。</span><span class="sxs-lookup"><span data-stu-id="0ae54-111">No other app changes are required for that app to then run as a slate in mixed reality.</span></span>

<span data-ttu-id="0ae54-112">若要开始构建 2D 的 UWP 应用，请查看[创建第一个应用](https://docs.microsoft.com/windows/uwp/get-started/your-first-app)一文。</span><span class="sxs-lookup"><span data-stu-id="0ae54-112">To get started building a 2D UWP app, check out the [Create your first app](https://docs.microsoft.com/windows/uwp/get-started/your-first-app) article.</span></span>

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a><span data-ttu-id="0ae54-113">现有的 2D 应用商店应用程序引入 UWP</span><span class="sxs-lookup"><span data-stu-id="0ae54-113">Bringing an existing 2D Store app to UWP</span></span>

<span data-ttu-id="0ae54-114">如果在存储区中已有 2D 的 Windows 应用，必须首先确保它面向 Windows 10 通用 Windows 平台 (UWP)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-114">If you already have a 2D Windows app in the Store, you must first ensure it is targeting the Windows 10 Universal Windows Platform (UWP).</span></span> <span data-ttu-id="0ae54-115">下面是所有潜在起始点今天你可能与应用商店应用程序：</span><span class="sxs-lookup"><span data-stu-id="0ae54-115">Here are all the potential starting points you may have with your Store app today:</span></span>
<br>

|  <span data-ttu-id="0ae54-116">起始点</span><span class="sxs-lookup"><span data-stu-id="0ae54-116">Starting Point</span></span>  |  <span data-ttu-id="0ae54-117">AppX 清单平台目标</span><span class="sxs-lookup"><span data-stu-id="0ae54-117">AppX Manifest Platform Target</span></span>  |  <span data-ttu-id="0ae54-118">如何使此世界？</span><span class="sxs-lookup"><span data-stu-id="0ae54-118">How to make this Universal?</span></span> | 
|----------|----------|----------|
|  <span data-ttu-id="0ae54-119">Windows Phone (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="0ae54-119">Windows Phone (Silverlight)</span></span>  |  <span data-ttu-id="0ae54-120">Silverlight 应用程序清单</span><span class="sxs-lookup"><span data-stu-id="0ae54-120">Silverlight App Manifest</span></span> |  <span data-ttu-id="0ae54-121">[将迁移到 WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span><span class="sxs-lookup"><span data-stu-id="0ae54-121">[Migrate to WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx)</span></span> | 
|  <span data-ttu-id="0ae54-122">Windows Phone 8.1 通用</span><span class="sxs-lookup"><span data-stu-id="0ae54-122">Windows Phone 8.1 Universal</span></span>  |  <span data-ttu-id="0ae54-123">8.1 不包括目标平台的 AppX 清单</span><span class="sxs-lookup"><span data-stu-id="0ae54-123">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="0ae54-124">将您的应用程序迁移到通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="0ae54-124">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="0ae54-125">Windows 应用商店 8</span><span class="sxs-lookup"><span data-stu-id="0ae54-125">Windows Store 8</span></span>  |  <span data-ttu-id="0ae54-126">不包括目标平台的 8 AppX 清单</span><span class="sxs-lookup"><span data-stu-id="0ae54-126">8 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="0ae54-127">将您的应用程序迁移到通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="0ae54-127">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  <span data-ttu-id="0ae54-128">Windows 应用商店 8.1 通用</span><span class="sxs-lookup"><span data-stu-id="0ae54-128">Windows Store 8.1 Universal</span></span>  |  <span data-ttu-id="0ae54-129">8.1 不包括目标平台的 AppX 清单</span><span class="sxs-lookup"><span data-stu-id="0ae54-129">8.1 AppX Manifest that Doesn't Include Platform Target</span></span>  |  [<span data-ttu-id="0ae54-130">将您的应用程序迁移到通用 Windows 平台</span><span class="sxs-lookup"><span data-stu-id="0ae54-130">Migrate your app to the Universal Windows Platform</span></span>](https://msdn.microsoft.com/library/mt148501.aspx) | 

<span data-ttu-id="0ae54-131">如果必须立即生成为 （"PC、 Mac 和 Linux 独立"生成目标） 的 Win32 应用程序的 2D Unity 应用，你可以通过改为切换到"通用 Windows 平台"生成目标的 Unity 面向混合的现实。</span><span class="sxs-lookup"><span data-stu-id="0ae54-131">If you have a 2D Unity app today built as a Win32 app (the "PC, Mac & Linux Standalone" build target), you can target mixed reality by switching Unity to the "Universal Windows Platform" build target instead.</span></span>

<span data-ttu-id="0ae54-132">我们将讨论方法，可以限制您的应用程序特定于使用 Windows.Holographic 设备系列的 HoloLens[如下](#publish-and-maintain-your-universal-app)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-132">We'll talk about ways that you can restrict your app specifically to HoloLens using the Windows.Holographic device family [below](#publish-and-maintain-your-universal-app).</span></span>

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a><span data-ttu-id="0ae54-133">运行 Windows Mixed Reality 沉浸式头戴式 2D 应用</span><span class="sxs-lookup"><span data-stu-id="0ae54-133">Run your 2D app in a Windows Mixed Reality immersive headset</span></span>

<span data-ttu-id="0ae54-134">如果你已将 2D 应用部署到你要开发并且尝试在监视器上的桌面计算机，您已经准备好在沉浸式的桌面耳机中试用它 ！</span><span class="sxs-lookup"><span data-stu-id="0ae54-134">If you've deployed your 2D app to the desktop machine where you are developing and tried it out on your monitor, you're already ready to try it out in an immersive desktop headset!</span></span>

<span data-ttu-id="0ae54-135">只需转到开始菜单中混合的现实耳机，并从该处启动应用。</span><span class="sxs-lookup"><span data-stu-id="0ae54-135">Just go to the Start menu within the mixed reality headset and launch the app from there.</span></span> <span data-ttu-id="0ae54-136">桌面外壳程序和全息版的 shell 都共享一组相同的 UWP 应用，并因此应用程序应从 Visual Studio 部署后存在。</span><span class="sxs-lookup"><span data-stu-id="0ae54-136">The desktop shell and the holographic shell both share the same set of UWP apps, and so the app should already be present once you've deployed from Visual Studio.</span></span>

## <a name="targeting-both-immersive-headsets-and-hololens"></a><span data-ttu-id="0ae54-137">面向沉浸式耳机和 HoloLens</span><span class="sxs-lookup"><span data-stu-id="0ae54-137">Targeting both immersive headsets and HoloLens</span></span>

<span data-ttu-id="0ae54-138">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="0ae54-138">Congratulations!</span></span> <span data-ttu-id="0ae54-139">你的应用现在使用 Windows 10 通用 Windows 平台 (UWP)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-139">Your app is now using the Windows 10 Universal Windows Platform (UWP).</span></span>

<span data-ttu-id="0ae54-140">您的应用程序现在是能够在今天的桌面、 移动、 Xbox、 Windows Mixed Reality 沉浸式耳机等 HoloLens，以及为未来的 Windows 设备的 Windows 设备上运行。</span><span class="sxs-lookup"><span data-stu-id="0ae54-140">Your app is now capable of running on today's Windows devices like Desktop, Mobile, Xbox, Windows Mixed Reality immersive headsets, and HoloLens, as well as future Windows devices.</span></span> <span data-ttu-id="0ae54-141">但是，若要实际针对所有这些设备，并将需要确保您的应用程序所面向的 Windows.Universal 设备系列。</span><span class="sxs-lookup"><span data-stu-id="0ae54-141">However, to actually target all of those devices, you will need to ensure your app is targeting the Windows.Universal device family.</span></span>

### <a name="change-your-device-family-to-windowsuniversal"></a><span data-ttu-id="0ae54-142">更改您的设备系列为 Windows.Universal</span><span class="sxs-lookup"><span data-stu-id="0ae54-142">Change your device family to Windows.Universal</span></span>

<span data-ttu-id="0ae54-143">现在让我们跳转到你的 AppX 清单以确保你的 Windows 10 UWP 应用可以在 HoloLens 上运行：</span><span class="sxs-lookup"><span data-stu-id="0ae54-143">Now let's jump into your AppX manifest to ensure your Windows 10 UWP app can run on HoloLens:</span></span>
* <span data-ttu-id="0ae54-144">打开与应用程序的解决方案文件**Visual Studio**并导航到应用程序包清单</span><span class="sxs-lookup"><span data-stu-id="0ae54-144">Open your app's solution file with **Visual Studio** and navigate to the app package manifest</span></span>
* <span data-ttu-id="0ae54-145">右键单击**Package.appxmanifest**文件位于你的解决方案，并转到**查看代码**</span><span class="sxs-lookup"><span data-stu-id="0ae54-145">Right click the **Package.appxmanifest** file in your Solution and go to **View Code**</span></span><br>
  <span data-ttu-id="0ae54-146">![在解决方案资源管理器中的 package.appxmanifest](images/openappxmanifest-500px.png)</span><span class="sxs-lookup"><span data-stu-id="0ae54-146">![package.appxmanifest in Solution Explorer](images/openappxmanifest-500px.png)</span></span><br>
* <span data-ttu-id="0ae54-147">请确保您的目标平台中的依赖项部分 Windows.Universal</span><span class="sxs-lookup"><span data-stu-id="0ae54-147">Ensure your Target Platform is Windows.Universal in the dependencies section</span></span>
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* <span data-ttu-id="0ae54-148">保存 ！</span><span class="sxs-lookup"><span data-stu-id="0ae54-148">Save!</span></span>

<span data-ttu-id="0ae54-149">如果不为您的开发环境中使用 Visual Studio，则可以打开**AppXManifest.xml**中以确保您的目标所选的文本编辑器**Windows.Universal** *TargetDeviceFamily*。</span><span class="sxs-lookup"><span data-stu-id="0ae54-149">If you do not use Visual Studio for your development environment, you can open **AppXManifest.xml** in the text editor of your choice to ensure you're targeting the **Windows.Universal** *TargetDeviceFamily*.</span></span>

### <a name="run-in-the-hololens-emulator"></a><span data-ttu-id="0ae54-150">HoloLens 的模拟器中运行</span><span class="sxs-lookup"><span data-stu-id="0ae54-150">Run in the HoloLens Emulator</span></span>

<span data-ttu-id="0ae54-151">现在，你的 UWP 应用面向"Windows.Universal"，让我们构建您的应用程序，然后在运行[HoloLens 模拟器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-151">Now that your UWP app targets "Windows.Universal", let's build your app and run it in the [HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
* <span data-ttu-id="0ae54-152">请确保你拥有[安装了 HoloLens Emulator](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-152">Make sure you have [installed the HoloLens Emulator](install-the-tools.md).</span></span>
* <span data-ttu-id="0ae54-153">在 Visual Studio 中，选择**x86**生成应用的配置</span><span class="sxs-lookup"><span data-stu-id="0ae54-153">In Visual Studio, select the **x86** build configuration for your app</span></span>

  ![x86 生成 Visual Studio 中的配置](images/x86setting.png)<br>
* <span data-ttu-id="0ae54-155">选择**HoloLens 模拟器**部署目标下拉列表菜单中</span><span class="sxs-lookup"><span data-stu-id="0ae54-155">Select **HoloLens Emulator** in the deployment target drop-down menu</span></span>

  ![HoloLens 仿真程序中部署目标列表](images/deployemulator-500px.png)<br>
* <span data-ttu-id="0ae54-157">选择**调试 > 启动调试**来部署应用，并开始调试。</span><span class="sxs-lookup"><span data-stu-id="0ae54-157">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="0ae54-158">在仿真程序将启动并运行您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0ae54-158">The emulator will start and run your app.</span></span>
* <span data-ttu-id="0ae54-159">使用键盘、 鼠标和/或 Xbox 控制器，将您的应用程序放在世界上启动它。</span><span class="sxs-lookup"><span data-stu-id="0ae54-159">With a keyboard, mouse, and/or an Xbox controller, place your app in the world to launch it.</span></span>

  ![HoloLens 仿真器加载与 UWP 示例](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a><span data-ttu-id="0ae54-161">后续步骤</span><span class="sxs-lookup"><span data-stu-id="0ae54-161">Next steps</span></span>

<span data-ttu-id="0ae54-162">此时，可能发生两项操作之一：</span><span class="sxs-lookup"><span data-stu-id="0ae54-162">At this point, one of two things can happen:</span></span>
1. <span data-ttu-id="0ae54-163">您的应用程序将显示其初始并开始运行后放置在仿真程序中 ！</span><span class="sxs-lookup"><span data-stu-id="0ae54-163">Your app will show its splash and start running after it is placed in the Emulator!</span></span> <span data-ttu-id="0ae54-164">太好了 ！</span><span class="sxs-lookup"><span data-stu-id="0ae54-164">Awesome!</span></span>
2. <span data-ttu-id="0ae54-165">或者请参阅 2D hologram 加载动画之后，加载将停止，将只看到您的应用程序在其初始屏幕。</span><span class="sxs-lookup"><span data-stu-id="0ae54-165">Or after you see a loading animation for a 2D hologram, loading will stop and you will just see your app at its splash screen.</span></span> <span data-ttu-id="0ae54-166">这意味着出现了问题，这需要花费更多的调查以了解如何将应用迁移到混合现实中的时间。</span><span class="sxs-lookup"><span data-stu-id="0ae54-166">This means that something went wrong and it will take more investigation to understand how to bring your app to life in Mixed Reality.</span></span>

<span data-ttu-id="0ae54-167">若要获取到什么可能会导致你的 UWP 应用的底部，不能在 HoloLens 上启动，您需要调试。</span><span class="sxs-lookup"><span data-stu-id="0ae54-167">To get to the bottom of what may be causing your UWP app not to start on HoloLens, you'll have to debug.</span></span>

### <a name="running-your-uwp-app-in-the-debugger"></a><span data-ttu-id="0ae54-168">在调试器中运行 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="0ae54-168">Running your UWP app in the debugger</span></span>

<span data-ttu-id="0ae54-169">这些步骤将引导您完成调试 UWP 应用使用 Visual Studio 调试器。</span><span class="sxs-lookup"><span data-stu-id="0ae54-169">These steps will walk you through debugging your UWP app using the Visual Studio debugger.</span></span>
* <span data-ttu-id="0ae54-170">如果尚未这样做，Visual Studio 中打开你的解决方案。</span><span class="sxs-lookup"><span data-stu-id="0ae54-170">If you haven't already done so, open your solution in Visual Studio.</span></span> <span data-ttu-id="0ae54-171">更改到目标**HoloLens 模拟器**和生成配置以进行**x86**。</span><span class="sxs-lookup"><span data-stu-id="0ae54-171">Change the target to the **HoloLens Emulator** and the build configuration to **x86**.</span></span>
* <span data-ttu-id="0ae54-172">选择**调试 > 启动调试**来部署应用，并开始调试。</span><span class="sxs-lookup"><span data-stu-id="0ae54-172">Select **Debug > Start Debugging** to deploy your app and start debugging.</span></span>
* <span data-ttu-id="0ae54-173">在使用鼠标、 键盘或 Xbox 控制器世界中将此应用程序。</span><span class="sxs-lookup"><span data-stu-id="0ae54-173">Place the app in the world with your mouse, keyboard, or Xbox controller.</span></span>
* <span data-ttu-id="0ae54-174">Visual Studio 应立即在应用代码中某处中断。</span><span class="sxs-lookup"><span data-stu-id="0ae54-174">Visual Studio should now break somewhere in your app code.</span></span>
  - <span data-ttu-id="0ae54-175">如果您的应用程序不会立即崩溃或进入调试器由于未经处理的错误，然后经过测试流程的应用程序以确保一切都运行，并且功能的核心功能。</span><span class="sxs-lookup"><span data-stu-id="0ae54-175">If your app doesn't immediately crash or break into the debugger because of an unhandled error, then go through a test pass of the core features of your app to make sure everything is running and functional.</span></span> <span data-ttu-id="0ae54-176">您可能会看到错误，如 （正在处理的内部异常） 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="0ae54-176">You may see errors like pictured below (internal exceptions that are being handled).</span></span> <span data-ttu-id="0ae54-177">若要确保不会错过影响您的应用程序体验的内部错误，运行通过自动的测试和单元测试，以确保一切按预期的行为。</span><span class="sxs-lookup"><span data-stu-id="0ae54-177">To ensure you don't miss internal errors that impact the experience of your app, run through your automated tests and unit tests to make sure everything behaves as expected.</span></span>

![HoloLens 仿真器加载与 UWP 示例显示系统异常](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a><span data-ttu-id="0ae54-179">更新你的 UI</span><span class="sxs-lookup"><span data-stu-id="0ae54-179">Update your UI</span></span>

<span data-ttu-id="0ae54-180">现在，运行 UWP 应用的沉浸式耳机和/或作为 2D 全息图 HoloLens，接下来我们将确保它看起来美观。</span><span class="sxs-lookup"><span data-stu-id="0ae54-180">Now that your UWP app is running on immersive headsets and/or HoloLens as a 2D hologram, next we'll make sure it looks beautiful.</span></span> <span data-ttu-id="0ae54-181">下面是一些要考虑的事项：</span><span class="sxs-lookup"><span data-stu-id="0ae54-181">Here are some things to consider:</span></span>
* <span data-ttu-id="0ae54-182">到 853 x 480 有效像素，Windows Mixed Reality 将在固定的分辨率和 DPI 等同于运行 2D 的所有应用。</span><span class="sxs-lookup"><span data-stu-id="0ae54-182">Windows Mixed Reality will run all 2D apps at a fixed resolution and DPI that equates to 853x480 effective pixels.</span></span> <span data-ttu-id="0ae54-183">如果您的设计需要在此规模较大的优化，请考虑并查看设计以下指南来增强 HoloLens 和沉浸式耳机的体验。</span><span class="sxs-lookup"><span data-stu-id="0ae54-183">Consider if your design needs refinement at this scale and review the design guidance below to improve your experience on HoloLens and immersive headsets.</span></span>
* <span data-ttu-id="0ae54-184">Windows Mixed Reality[不支持](app-model.md)2D 动态磁贴。</span><span class="sxs-lookup"><span data-stu-id="0ae54-184">Windows Mixed Reality [does not support](app-model.md) 2D live tiles.</span></span> <span data-ttu-id="0ae54-185">如果您的核心功能动态磁贴上显示信息，请考虑将该信息移回您的应用程序或探索[三维应用启动器上](3d-app-launcher-design-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-185">If your core functionality is showing information on a live tile, consider moving that information back into your app or explore [3D app launchers](3d-app-launcher-design-guidance.md).</span></span>

### <a name="2d-app-view-resolution-and-scale-factor"></a><span data-ttu-id="0ae54-186">2D 应用视图解析和缩放系数</span><span class="sxs-lookup"><span data-stu-id="0ae54-186">2D app view resolution and scale factor</span></span>

![从响应式设计](images/scale-500px.png)

<span data-ttu-id="0ae54-188">Windows 10 移动所有视觉对象设计从到的实际屏幕像素**有效像素**。</span><span class="sxs-lookup"><span data-stu-id="0ae54-188">Windows 10 moves all visual design from real screen pixels to **effective pixels**.</span></span> <span data-ttu-id="0ae54-189">这意味着，开发人员设计它们遵循 Windows 10 人机接口指南 》 的有效像素的 UI 和 Windows 缩放可以确保这些有效像素的适当大小的设备，分辨率、 DPI，跨可用性等。请参阅此[MSDN 上的很好读](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)了解详细信息以及此[生成演示文稿](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-189">That means, developers design their UI following the Windows 10 Human Interface Guidelines for effective pixels, and Windows scaling ensures those effective pixels are the right size for usability across devices, resolutions, DPI, etc. See this [great read on MSDN](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx) to learn more as well as this [BUILD presentation](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx).</span></span>

<span data-ttu-id="0ae54-190">即使使用独特的功能将应用放在您在为单位的距离范围内的世界，类似于电视的查看距离建议以产生最佳可读性和与的视线移动/手势的交互。</span><span class="sxs-lookup"><span data-stu-id="0ae54-190">Even with the unique ability to place apps in your world at a range of distances, TV-like viewing distances are recommended to produce the best readability and interaction with gaze/gesture.</span></span> <span data-ttu-id="0ae54-191">正因为如此，虚拟平板式混合现实在家中的将显示在你平面 UWP 视图：</span><span class="sxs-lookup"><span data-stu-id="0ae54-191">Because of that, a virtual slate in the Mixed Reality Home will display your flat UWP view at:</span></span>

<span data-ttu-id="0ae54-192">**1280 x 720、 150 %dpi** （853 x 480 有效像素）</span><span class="sxs-lookup"><span data-stu-id="0ae54-192">**1280x720, 150%DPI** (853x480 effective pixels)</span></span>

<span data-ttu-id="0ae54-193">此解决方案具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="0ae54-193">This resolution has several advantages:</span></span>
* <span data-ttu-id="0ae54-194">有关为平板电脑或小桌面的相同信息密度将具有此有效像素布局。</span><span class="sxs-lookup"><span data-stu-id="0ae54-194">This effective pixel layout will have about the same information density as a tablet or small desktop.</span></span>
* <span data-ttu-id="0ae54-195">它可匹配固定的 DPI 和适用于 Xbox One，启用无缝体验跨设备上运行的 UWP 应用的有效像素。</span><span class="sxs-lookup"><span data-stu-id="0ae54-195">It matches the fixed DPI and effective pixels for UWP apps running on Xbox One, enabling seamless experiences across devices.</span></span>
* <span data-ttu-id="0ae54-196">此大小看起来没问题，我们的世界中应用的距离范围内缩放时。</span><span class="sxs-lookup"><span data-stu-id="0ae54-196">This size looks good when scaled across our range of operating distances for apps in the world.</span></span>

### <a name="2d-app-view-interface-design-best-practices"></a><span data-ttu-id="0ae54-197">2D 应用视图接口设计最佳实践</span><span class="sxs-lookup"><span data-stu-id="0ae54-197">2D app view interface design best practices</span></span>

<span data-ttu-id="0ae54-198">**执行操作：**</span><span class="sxs-lookup"><span data-stu-id="0ae54-198">**Do:**</span></span>
* <span data-ttu-id="0ae54-199">请按照[Windows 10 人机接口准则 (HIG)](https://dev.windows.com/design)样式、 字体大小和按钮大小。</span><span class="sxs-lookup"><span data-stu-id="0ae54-199">Follow the [Windows 10 Human Interface Guidelines (HIG)](https://dev.windows.com/design) for styles, font sizes and button sizes.</span></span> <span data-ttu-id="0ae54-200">HoloLens 将执行的工作以确保你的应用具有兼容的应用模式、 可读的文本大小和相应的命中的目标大小调整。</span><span class="sxs-lookup"><span data-stu-id="0ae54-200">HoloLens will do the work to ensure your app will have compatible app patterns, readable text sizes, and appropriate hit target sizing.</span></span>
* <span data-ttu-id="0ae54-201">确保在 UI 如下所示的最佳做法[响应式设计](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)查找最佳支持 HoloLen 的唯一分辨率和 DPI。</span><span class="sxs-lookup"><span data-stu-id="0ae54-201">Ensure your UI follows best practices for [responsive design](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx) to look best at HoloLen's unique resolution and DPI.</span></span>
* <span data-ttu-id="0ae54-202">从 Windows 使用的"light"颜色主题建议。</span><span class="sxs-lookup"><span data-stu-id="0ae54-202">Use the "light" color theme recommendations from Windows.</span></span>

<span data-ttu-id="0ae54-203">**不要：**</span><span class="sxs-lookup"><span data-stu-id="0ae54-203">**Don't:**</span></span>
* <span data-ttu-id="0ae54-204">在混合现实，以确保用户拥有入和移出耳机熟悉的体验时太显著更改你的 UI。</span><span class="sxs-lookup"><span data-stu-id="0ae54-204">Change your UI too drastically when in mixed reality, to ensure users have a familiar experience in and out of the headset.</span></span>

### <a name="understand-the-app-model"></a><span data-ttu-id="0ae54-205">了解应用程序模型</span><span class="sxs-lookup"><span data-stu-id="0ae54-205">Understand the app model</span></span>

<span data-ttu-id="0ae54-206">[应用程序模型](app-model.md)的混合的现实设计为使用混合现实主页，许多应用程序一起居住的位置。</span><span class="sxs-lookup"><span data-stu-id="0ae54-206">The [app model](app-model.md) for mixed reality is designed to use the Mixed Reality Home, where many apps live together.</span></span> <span data-ttu-id="0ae54-207">将此视为混合的现实等效于在桌面上，其中同时运行许多 2D 应用程序。</span><span class="sxs-lookup"><span data-stu-id="0ae54-207">Think of this as the mixed reality equivalent of the desktop, where you run many 2D apps at once.</span></span> <span data-ttu-id="0ae54-208">这会影响应用程序生命周期、 磁贴，和您的应用程序的其他主要功能。</span><span class="sxs-lookup"><span data-stu-id="0ae54-208">This has implications on app life cycle, Tiles, and other key features of your app.</span></span>

### <a name="app-bar-and-back-button"></a><span data-ttu-id="0ae54-209">应用程序栏和后退按钮</span><span class="sxs-lookup"><span data-stu-id="0ae54-209">App bar and back button</span></span>

<span data-ttu-id="0ae54-210">使用其内容的顶部应用栏进行修饰二维视图。</span><span class="sxs-lookup"><span data-stu-id="0ae54-210">2D views are decorated with a app bar above their content.</span></span> <span data-ttu-id="0ae54-211">应用栏有两个点的特定于应用的个性化设置：</span><span class="sxs-lookup"><span data-stu-id="0ae54-211">The app bar has two points of app-specific personalization:</span></span>

<span data-ttu-id="0ae54-212">**标题：** 将显示*displayname*与应用程序实例相关联的磁贴</span><span class="sxs-lookup"><span data-stu-id="0ae54-212">**Title:** displays the *displayname* of the Tile associated with the app instance</span></span>

<span data-ttu-id="0ae54-213">**后退按钮：** 将引发 *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 时按下事件。</span><span class="sxs-lookup"><span data-stu-id="0ae54-213">**Back Button:** raises the *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* event when pressed.</span></span> <span data-ttu-id="0ae54-214">通过控制后退按钮可见性 *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* 。</span><span class="sxs-lookup"><span data-stu-id="0ae54-214">Back Button visibility is controlled by *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*.</span></span>

<span data-ttu-id="0ae54-215">![应用栏 2D 应用视图中的用户界面](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0ae54-215">![App bar UI in 2D app view](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)</span></span><br>
<span data-ttu-id="0ae54-216">*应用栏 2D 应用视图中的用户界面*</span><span class="sxs-lookup"><span data-stu-id="0ae54-216">*App bar UI in 2D app view*</span></span>

### <a name="test-your-2d-apps-design"></a><span data-ttu-id="0ae54-217">测试 2D 应用程序的设计</span><span class="sxs-lookup"><span data-stu-id="0ae54-217">Test your 2D app's design</span></span>

<span data-ttu-id="0ae54-218">请务必测试该应用，请确保该文本是可读，以，这些按钮为目标，整体应用看上去正确。</span><span class="sxs-lookup"><span data-stu-id="0ae54-218">It is important to test your app to make sure the text is readable, the buttons are targetable, and the overall app looks correct.</span></span> <span data-ttu-id="0ae54-219">你可以[测试](testing-your-app-on-hololens.md)桌面耳机、 HoloLens、 一个仿真程序或解析设置为 1280 x 720 使用触控设备上@150%。</span><span class="sxs-lookup"><span data-stu-id="0ae54-219">You can [test](testing-your-app-on-hololens.md) on a desktop headset, a HoloLens, an emulator, or a touch device with resolution set to 1280x720 @150%.</span></span>

## <a name="new-input-possibilities"></a><span data-ttu-id="0ae54-220">新的输入的可能性</span><span class="sxs-lookup"><span data-stu-id="0ae54-220">New input possibilities</span></span>

<span data-ttu-id="0ae54-221">HoloLens 使用高级的深度传感器，请参阅世界，并查看用户。</span><span class="sxs-lookup"><span data-stu-id="0ae54-221">HoloLens uses advanced depth sensors to see the world and see users.</span></span> <span data-ttu-id="0ae54-222">这样，如高级的手势[布隆](gestures.md#bloom)并[air 点击](gestures.md#air-tap)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-222">This enables advanced hand gestures like [bloom](gestures.md#bloom) and [air-tap](gestures.md#air-tap).</span></span> <span data-ttu-id="0ae54-223">此外启用功能强大的麦克风[语音体验](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-223">Powerful microphones also enable [voice experiences](voice-input.md).</span></span>

<span data-ttu-id="0ae54-224">与桌面耳机，用户可以使用 motion 控制器以指向应用程序并采取措施。</span><span class="sxs-lookup"><span data-stu-id="0ae54-224">With Desktop headsets, users can use motion controllers to point at apps and take action.</span></span> <span data-ttu-id="0ae54-225">他们还可以使用游戏手柄，指向其的视线移动的对象。</span><span class="sxs-lookup"><span data-stu-id="0ae54-225">They can also use a gamepad, targeting objects with their gaze.</span></span>

<span data-ttu-id="0ae54-226">Windows 将负责所有这种复杂性适用于 UWP 应用的转换您[注视](gaze.md)，手势，语音和动作的输入控制器[指针事件](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)抽象出输入的机制。</span><span class="sxs-lookup"><span data-stu-id="0ae54-226">Windows takes care of all of this complexity for UWP apps, translating your [gaze](gaze.md), gestures, voice and motion controller input to [pointer events](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events) that abstract away the input mechanism.</span></span> <span data-ttu-id="0ae54-227">例如，用户可能已完成-敲击用其一只手或动作在控制器上，请求选择触发器但 2D 应用程序无需知道其中原来的位置输入-只看到 2D 触摸屏输入按下时，像触摸屏上。</span><span class="sxs-lookup"><span data-stu-id="0ae54-227">For example, a user may have done an air-tap with their hand or pulled the Select trigger on a motion controller, but 2D applications don't need to know where the input came from - they just see a 2D touch press, as if on a touchscreen.</span></span>

<span data-ttu-id="0ae54-228">此处是到 HoloLens 使 UWP 应用时，应了解的输入的高级概念/方案：</span><span class="sxs-lookup"><span data-stu-id="0ae54-228">Here are the high level concepts/scenarios you should understand for input when bringing your UWP app to HoloLens:</span></span>
* <span data-ttu-id="0ae54-229">[注视](gaze.md)变为悬停事件，以便在意外触发菜单、 浮出控件或其他用户界面元素，只需通过在应用周围观望弹出。</span><span class="sxs-lookup"><span data-stu-id="0ae54-229">[Gaze](gaze.md) turns into hover events, which can unexpectedly trigger menus, flyouts or other user interface elements to pop up just by gazing around your app.</span></span>
* <span data-ttu-id="0ae54-230">视线移动不精确的鼠标输入。</span><span class="sxs-lookup"><span data-stu-id="0ae54-230">Gaze is not as precise as mouse input.</span></span> <span data-ttu-id="0ae54-231">使用适当调整大小的 HoloLens，类似于触摸功能的移动应用程序的命中的目标。</span><span class="sxs-lookup"><span data-stu-id="0ae54-231">Use appropriately sized hit targets for HoloLens, similar to touch-friendly mobile applications.</span></span> <span data-ttu-id="0ae54-232">应用的边缘附近的小元素是特别难，若要与之交互。</span><span class="sxs-lookup"><span data-stu-id="0ae54-232">Small elements near the edges of the app are especially hard to interact with.</span></span>
* <span data-ttu-id="0ae54-233">用户必须切换输入的法从滚动到拖动到两个指平移。</span><span class="sxs-lookup"><span data-stu-id="0ae54-233">Users must switch input modes to go from scrolling to dragging to two finger panning.</span></span> <span data-ttu-id="0ae54-234">如果您的应用程序专为触摸输入，请考虑确保任何主要功能锁定后面两个指平移。</span><span class="sxs-lookup"><span data-stu-id="0ae54-234">If your app was designed for touch input, consider ensuring that no major functionality is locked behind two finger panning.</span></span> <span data-ttu-id="0ae54-235">如果是这样，请考虑让像按钮一样，可以启动两个指平移的替代输入的机制。</span><span class="sxs-lookup"><span data-stu-id="0ae54-235">If so, consider having alternative input mechanisms like buttons that can initiate two finger panning.</span></span> <span data-ttu-id="0ae54-236">例如，地图应用程序可以放大具有两个手指平移而减号的加号，，旋转按钮以模拟与次单击之间的相同的缩放交互。</span><span class="sxs-lookup"><span data-stu-id="0ae54-236">For example, the Maps app can zoom with two finger panning but has a plus, minus, and rotate button to simulate the same zoom interactions with single clicks.</span></span>

<span data-ttu-id="0ae54-237">[语音输入](voice-input.md)是混合的现实体验的关键部分。</span><span class="sxs-lookup"><span data-stu-id="0ae54-237">[Voice input](voice-input.md) is a critical part of the mixed reality experience.</span></span> <span data-ttu-id="0ae54-238">我们已启用所有语音在 Windows 10 中使用耳机时增强 Cortana Api。</span><span class="sxs-lookup"><span data-stu-id="0ae54-238">We've enabled all of the speech APIs that are in Windows 10 powering Cortana when using a headset.</span></span>

## <a name="publish-and-maintain-your-universal-app"></a><span data-ttu-id="0ae54-239">发布和维护通用应用</span><span class="sxs-lookup"><span data-stu-id="0ae54-239">Publish and Maintain your Universal app</span></span>

<span data-ttu-id="0ae54-240">启动并运行您的应用程序后，到将应用打包[将其提交到 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae54-240">Once your app is up and running, package your app to [submit it to the Microsoft Store](submitting-an-app-to-the-microsoft-store.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ae54-241">请参阅</span><span class="sxs-lookup"><span data-stu-id="0ae54-241">See also</span></span>
* [<span data-ttu-id="0ae54-242">应用模型</span><span class="sxs-lookup"><span data-stu-id="0ae54-242">App model</span></span>](app-model.md)
* [<span data-ttu-id="0ae54-243">凝视</span><span class="sxs-lookup"><span data-stu-id="0ae54-243">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="0ae54-244">手势</span><span class="sxs-lookup"><span data-stu-id="0ae54-244">Gesture</span></span>](gestures.md)
* [<span data-ttu-id="0ae54-245">运动控制器</span><span class="sxs-lookup"><span data-stu-id="0ae54-245">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="0ae54-246">语音输入</span><span class="sxs-lookup"><span data-stu-id="0ae54-246">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="0ae54-247">将应用提交到 Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="0ae54-247">Submitting an app to the Microsoft Store</span></span>](submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="0ae54-248">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="0ae54-248">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
