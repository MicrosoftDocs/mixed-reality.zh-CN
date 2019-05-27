---
title: OpenXR
description: 尝试临时 OpenXR 0.90 API 与混合现实 OpenXR 开发者预览版。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 混合的现实 OpenXR 开发者预览版
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039174"
---
# <a name="openxr"></a><span data-ttu-id="414d6-104">OpenXR</span><span class="sxs-lookup"><span data-stu-id="414d6-104">OpenXR</span></span>

<span data-ttu-id="414d6-105">OpenXR 是开放式的免版税的标准从[Khronos](https://www.khronos.org/)提供对各种设备的时间跨度的许多供应商从本机访问[混合的现实范围](mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="414d6-105">OpenXR is an open royalty-free standard from [Khronos](https://www.khronos.org/) that provides native access to a wide range of devices from many vendors that span across the [mixed reality spectrum](mixed-reality.md).</span></span>

<span data-ttu-id="414d6-106">使用 OpenXR，您可以构建面向 holographic 设备 （如 HoloLens 2)，将数字内容放置在现实生活中，就好像确实存在，以及隐藏的沉浸式设备 （如桌面 Pc 的 Windows 混合现实耳机） 的应用程序物理世界并替换为数字的体验。</span><span class="sxs-lookup"><span data-stu-id="414d6-106">With OpenXR, you can build applications that target both holographic devices (like HoloLens 2) that place digital content in the real world as if it were really there, as well as immersive devices (like Windows Mixed Reality headsets for desktop PCs) that hide the physical world and replace it with a digital experience.</span></span>  <span data-ttu-id="414d6-107">OpenXR 允许你编写代码后，然后可移植对多种硬件平台。</span><span class="sxs-lookup"><span data-stu-id="414d6-107">OpenXR lets you write code once that's then portable across a wide range of hardware platforms.</span></span>

<span data-ttu-id="414d6-108">OpenXR 标准当前在临时阶段中，是与发布的反馈意见的初始 OpenXR 0.90 规范。</span><span class="sxs-lookup"><span data-stu-id="414d6-108">The OpenXR standard is currently in a provisional phase, with an initial OpenXR 0.90 spec released for feedback.</span></span>  <span data-ttu-id="414d6-109">有关详细信息 OpenXR，包括对访问权限[临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)和[标头](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)，请参阅[Khronos OpenXR 页](https://www.khronos.org/openxr/)。</span><span class="sxs-lookup"><span data-stu-id="414d6-109">For more information on OpenXR, including access to the [provisional 0.90 spec](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) and [headers](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), see the [Khronos OpenXR page](https://www.khronos.org/openxr/).</span></span> 

<span data-ttu-id="414d6-110">您可以试用 HoloLens 2 或使用混合现实 OpenXR 开发者预览版台式计算机上的临时 OpenXR 0.90 API。</span><span class="sxs-lookup"><span data-stu-id="414d6-110">You can try out the provisional OpenXR 0.90 API on a HoloLens 2 or a desktop PC using the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="414d6-111">此早期的运行时，面向 OpenXR 0.90 API 的应用程序以面向 HoloLens 2 或 Windows Mixed Reality 沉浸式耳机在桌面上。</span><span class="sxs-lookup"><span data-stu-id="414d6-111">This early runtime enables applications targeting the OpenXR 0.90 API to target HoloLens 2 or Windows Mixed Reality immersive headsets on the desktop.</span></span>

<span data-ttu-id="414d6-112">如果无法访问头戴式耳机，可以改为使用 HoloLens 2 仿真程序或 Windows 混合现实模拟器。</span><span class="sxs-lookup"><span data-stu-id="414d6-112">If you don't have access to a headset, you can use the HoloLens 2 Emulator or the Windows Mixed Reality Simulator instead.</span></span>

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a><span data-ttu-id="414d6-113">设置 HoloLens 2 混合现实 OpenXR 开发者预览版</span><span class="sxs-lookup"><span data-stu-id="414d6-113">Setting up the Mixed Reality OpenXR Developer Preview for HoloLens 2</span></span>

<span data-ttu-id="414d6-114">若要开始使用混合现实 OpenXR 开发者预览版 HoloLens 2 上：</span><span class="sxs-lookup"><span data-stu-id="414d6-114">To get started with the Mixed Reality OpenXR Developer Preview on HoloLens 2:</span></span>

1. <span data-ttu-id="414d6-115">设置 HoloLens 2 或按照说明[安装 HoloLens 2 模拟器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="414d6-115">Set up a HoloLens 2 or follow the instructions to [install the HoloLens 2 emulator](using-the-hololens-emulator.md).</span></span>
1. <span data-ttu-id="414d6-116">启动应用商店应用程序从设备或仿真程序中的，并确保更新所有应用。</span><span class="sxs-lookup"><span data-stu-id="414d6-116">Launch the Store app from within the device or emulator and ensure all apps are updated.</span></span>  <span data-ttu-id="414d6-117">这会使用该设备上的应用程序安装用于混合现实 OpenXR 开发者预览版。</span><span class="sxs-lookup"><span data-stu-id="414d6-117">This will install the Mixed Reality OpenXR Developer Preview for use with apps on that device.</span></span>  <span data-ttu-id="414d6-118">如果使用模拟器，您将需要查阅[仿真程序输入说明](using-the-hololens-emulator.md#basic-emulator-input)可帮助你使用应用商店应用在仿真程序内的。</span><span class="sxs-lookup"><span data-stu-id="414d6-118">If using the emulator, you'll want to consult the [emulator input instructions](using-the-hololens-emulator.md#basic-emulator-input) to help you use the Store app within the emulator.</span></span>

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a><span data-ttu-id="414d6-119">设置沉浸式桌面耳机混合现实 OpenXR 开发者预览版</span><span class="sxs-lookup"><span data-stu-id="414d6-119">Setting up the Mixed Reality OpenXR Developer Preview for immersive desktop headsets</span></span>

<span data-ttu-id="414d6-120">若要开始使用桌面 PC 上混合现实 OpenXR 开发者预览版：</span><span class="sxs-lookup"><span data-stu-id="414d6-120">To get started with the Mixed Reality OpenXR Developer Preview on a desktop PC:</span></span>

1. <span data-ttu-id="414d6-121">确保运行的 Windows 10 2018 年 10 月更新 (1809) 或 Windows 10 可能 2019年更新 (1903)。</span><span class="sxs-lookup"><span data-stu-id="414d6-121">Be sure you are running the Windows 10 October 2018 Update (1809) or the Windows 10 May 2019 Update (1903).</span></span>  <span data-ttu-id="414d6-122">如果您在早期版本的 Windows 10 上，你可以升级到 2019 年 5 使用更新[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="414d6-122">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>
1. <span data-ttu-id="414d6-123">设置 Windows 混合现实耳机或按照说明[启用 Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)。</span><span class="sxs-lookup"><span data-stu-id="414d6-123">Set up a Windows Mixed Reality headset or follow the instructions to [enable the Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md).</span></span>
1. <span data-ttu-id="414d6-124">安装[混合的现实 OpenXR 开发人员预览应用](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。</span><span class="sxs-lookup"><span data-stu-id="414d6-124">Install the [Mixed Reality OpenXR Developer Preview app](https://www.microsoft.com/store/productId/9n5cvvl23qbt).</span></span>  <span data-ttu-id="414d6-125">此应用可帮助你使用预览版 OpenXR 运行时上设置 Windows 10 2018 年 10 月更新 (1809) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="414d6-125">This app gets you set up with the preview OpenXR runtime on Windows 10 October 2018 Update (1809) or later.</span></span>  <span data-ttu-id="414d6-126">安装此应用后，Windows 应用商店将保留在运行时保持最新。</span><span class="sxs-lookup"><span data-stu-id="414d6-126">After installing this app, the Windows Store will keep the runtime up to date.</span></span>
1. <span data-ttu-id="414d6-127">从开始菜单运行混合现实 OpenXR 开发者预览版应用并按照说明进行操作以使运行时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="414d6-127">Run the Mixed Reality OpenXR Developer Preview app from the Start menu and follow the instructions to make the runtime active.</span></span>  <span data-ttu-id="414d6-128">很快，此应用会让您浏览以及其他 OpenXR 调试信息。</span><span class="sxs-lookup"><span data-stu-id="414d6-128">Soon, this app will let you explore other OpenXR debug information as well.</span></span>

![混合的现实 OpenXR 开发人员预览应用](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a><span data-ttu-id="414d6-130">支持 Windows 10 2018 年 10 月更新</span><span class="sxs-lookup"><span data-stu-id="414d6-130">Support for Windows 10 October 2018 Update</span></span>

<span data-ttu-id="414d6-131">如果您在运行 Windows 10 2019 年 5 更新 (1903) 并按照上述步骤，你应该已准备好使用混合现实 OpenXR 开发者预览版 ！</span><span class="sxs-lookup"><span data-stu-id="414d6-131">If you're running the Windows 10 May 2019 Update (1903) and followed the steps above, you should be ready to use the Mixed Reality OpenXR Developer Preview!</span></span>

<span data-ttu-id="414d6-132">如果您不准备[桌面 PC 升级到 2019 年 5 更新](https://www.microsoft.com/en-us/software-download/windows10)，您可以继续在 Windows 10 2018 年 10 月通过一个步骤来更新 (1809):</span><span class="sxs-lookup"><span data-stu-id="414d6-132">If you're not ready to [upgrade your desktop PC to the May 2019 Update](https://www.microsoft.com/en-us/software-download/windows10), you can get going on the Windows 10 October 2018 Update (1809) by following one more step:</span></span>

1. <span data-ttu-id="414d6-133">按照上述步骤来安装混合现实 OpenXR 开发者预览版。</span><span class="sxs-lookup"><span data-stu-id="414d6-133">Follow the steps above to install the Mixed Reality OpenXR Developer Preview.</span></span>
1. <span data-ttu-id="414d6-134">若要将您的系统活动 OpenXR 运行时设置混合现实 OpenXR 开发者预览版，请安装[混合现实 OpenXR 开发人员预览版兼容性工具包](https://aka.ms/openxr-compat)。</span><span class="sxs-lookup"><span data-stu-id="414d6-134">To set the Mixed Reality OpenXR Developer Preview as your system's active OpenXR runtime, install the [Mixed Reality OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).</span></span>

## <a name="building-a-sample-openxr-app"></a><span data-ttu-id="414d6-135">构建示例 OpenXR 应用</span><span class="sxs-lookup"><span data-stu-id="414d6-135">Building a sample OpenXR app</span></span>

<span data-ttu-id="414d6-136">[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp)项目演示简单 OpenXR 示例由两个 Visual Studio 项目文件，一个同时 Win32 桌面应用程序，一个用于 UWP HoloLens 2 应用程序。</span><span class="sxs-lookup"><span data-stu-id="414d6-136">The [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) project demonstrates a simple OpenXR sample with two Visual Studio project files, one for both a Win32 desktop app and one for a UWP HoloLens 2 app.</span></span>  <span data-ttu-id="414d6-137">因为该解决方案包含 HoloLens UWP 项目，你将需要[通用 Windows 平台开发工作负载](install-the-tools.md#installation-checklist)安装在 Visual Studio 以完全将其打开。</span><span class="sxs-lookup"><span data-stu-id="414d6-137">Because the solution contains a HoloLens UWP project, you'll need the [Universal Windows Platform development workload](install-the-tools.md#installation-checklist) installed in Visual Studio to fully open it.</span></span>

<span data-ttu-id="414d6-138">请注意，尽管 Win32 和 UWP 项目文件是单独由于打包和部署，每个项目中的应用程序代码之间的差异是 100%相同 ！</span><span class="sxs-lookup"><span data-stu-id="414d6-138">Note that while the Win32 and UWP project files are separate due to differences in packaging and deployment, the app code inside each project is 100% the same!</span></span>

## <a name="feedback"></a><span data-ttu-id="414d6-139">反馈</span><span class="sxs-lookup"><span data-stu-id="414d6-139">Feedback</span></span>

<span data-ttu-id="414d6-140">若要提供有关反馈[OpenXR 临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)，请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)， [#openxr Slack 通道](https://khr.io/slack)和[规范问题跟踪程序](https://github.com/KhronosGroup/OpenXR-Docs/issues)。</span><span class="sxs-lookup"><span data-stu-id="414d6-140">To give feedback on the [OpenXR Provisional 0.90 specification](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr), [Slack #openxr channel](https://khr.io/slack) and the [spec issue tracker](https://github.com/KhronosGroup/OpenXR-Docs/issues).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="414d6-141">疑难解答</span><span class="sxs-lookup"><span data-stu-id="414d6-141">Troubleshooting</span></span>

<span data-ttu-id="414d6-142">以下是有关混合现实 OpenXR 开发者预览版的一些故障排除提示。</span><span class="sxs-lookup"><span data-stu-id="414d6-142">Here are some troubleshooting tips for the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="414d6-143">如果在遇到任何其他问题，请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)或[#openxr Slack 通道](https://khr.io/slack)。</span><span class="sxs-lookup"><span data-stu-id="414d6-143">If you're hitting any other problems, please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr) or [Slack #openxr channel](https://khr.io/slack).</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="414d6-144">未启动 Windows Mixed Reality OpenXR 应用</span><span class="sxs-lookup"><span data-stu-id="414d6-144">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="414d6-145">如果 OpenXR 应用未启动 Windows Mixed Reality 在运行时，混合现实 OpenXR 开发者预览版可能不会设置为活动的运行时。</span><span class="sxs-lookup"><span data-stu-id="414d6-145">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Mixed Reality OpenXR Developer Preview may not be set as the active runtime.</span></span>  <span data-ttu-id="414d6-146">请确保运行混合现实 OpenXR 开发者预览版应用并按照说明进行操作以使运行时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="414d6-146">Be sure to run the Mixed Reality OpenXR Developer Preview app and follow the instructions to make the runtime active.</span></span>

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a><span data-ttu-id="414d6-147">混合的现实 OpenXR 开发者预览版应用无法在安装</span><span class="sxs-lookup"><span data-stu-id="414d6-147">Mixed Reality OpenXR Developer Preview app cannot be installed</span></span> 

<span data-ttu-id="414d6-148">确保你至少运行 Windows 10 2018 年 10 月更新 (1809)。</span><span class="sxs-lookup"><span data-stu-id="414d6-148">Be sure you are running at least the Windows 10 October 2018 Update (1809).</span></span>  <span data-ttu-id="414d6-149">如果您在早期版本的 Windows 10 上，你可以升级到 2019 年 5 更新 (1903) 使用[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="414d6-149">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update (1903) using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>

<span data-ttu-id="414d6-150">如果安装按钮上的混合现实 OpenXR 开发者预览版应用不会在 Windows 10 2018 年 10 月更新，您的系统已缓存应用程序的过时的系统要求。</span><span class="sxs-lookup"><span data-stu-id="414d6-150">If the Install button on the Mixed Reality OpenXR Developer Preview app does nothing on Windows 10 October 2018 Update, your system may have cached stale system requirements for the app.</span></span>  <span data-ttu-id="414d6-151">可以运行命令`wsreset.exe`在命令提示符下，若要清除的缓存。</span><span class="sxs-lookup"><span data-stu-id="414d6-151">You can run the command `wsreset.exe` from a command prompt to clear the cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="414d6-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="414d6-152">See also</span></span>

* [<span data-ttu-id="414d6-153">OpenXR 的详细信息</span><span class="sxs-lookup"><span data-stu-id="414d6-153">More information on OpenXR</span></span>](https://www.khronos.org/openxr/)
* [<span data-ttu-id="414d6-154">OpenXR 临时 0.90 规范</span><span class="sxs-lookup"><span data-stu-id="414d6-154">OpenXR Provisional 0.90 specification</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [<span data-ttu-id="414d6-155">OpenXR 临时 0.90 API 参考</span><span class="sxs-lookup"><span data-stu-id="414d6-155">OpenXR Provisional 0.90 API reference</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [<span data-ttu-id="414d6-156">OpenXR 临时 0.90 标头</span><span class="sxs-lookup"><span data-stu-id="414d6-156">OpenXR Provisional 0.90 headers</span></span>](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [<span data-ttu-id="414d6-157">OpenXR 临时 0.90 快速参考指南</span><span class="sxs-lookup"><span data-stu-id="414d6-157">OpenXR Provisional 0.90 quick reference guide</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
