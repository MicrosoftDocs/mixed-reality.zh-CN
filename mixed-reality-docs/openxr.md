---
title: OpenXR
description: 试用带有混合现实 OpenXR 开发者预览版的临时 OpenXR 0.90 API。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 混合现实 OpenXR 开发者预览版
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039174"
---
# <a name="openxr"></a><span data-ttu-id="e36f7-104">OpenXR</span><span class="sxs-lookup"><span data-stu-id="e36f7-104">OpenXR</span></span>

<span data-ttu-id="e36f7-105">OpenXR 是来自[Khronos](https://www.khronos.org/)的开放版税免费标准, 可提供跨[混合现实](mixed-reality.md)范围内多家供应商的各种设备的本机访问权限。</span><span class="sxs-lookup"><span data-stu-id="e36f7-105">OpenXR is an open royalty-free standard from [Khronos](https://www.khronos.org/) that provides native access to a wide range of devices from many vendors that span across the [mixed reality spectrum](mixed-reality.md).</span></span>

<span data-ttu-id="e36f7-106">借助 OpenXR, 你可以构建面向全息设备 (如 HoloLens 2) 的应用程序, 该应用程序将数字内容置于真实世界中, 就像它确实如此, 还可以提供沉浸式设备 (如台式计算机的 Windows Mixed Reality 耳机)实物, 并将其替换为数字体验。</span><span class="sxs-lookup"><span data-stu-id="e36f7-106">With OpenXR, you can build applications that target both holographic devices (like HoloLens 2) that place digital content in the real world as if it were really there, as well as immersive devices (like Windows Mixed Reality headsets for desktop PCs) that hide the physical world and replace it with a digital experience.</span></span>  <span data-ttu-id="e36f7-107">OpenXR 可让你编写代码, 然后在各种硬件平台上对其进行迁移。</span><span class="sxs-lookup"><span data-stu-id="e36f7-107">OpenXR lets you write code once that's then portable across a wide range of hardware platforms.</span></span>

<span data-ttu-id="e36f7-108">OpenXR 标准目前处于临时阶段, 为获得反馈而发布了初始 OpenXR 0.90 规范。</span><span class="sxs-lookup"><span data-stu-id="e36f7-108">The OpenXR standard is currently in a provisional phase, with an initial OpenXR 0.90 spec released for feedback.</span></span>  <span data-ttu-id="e36f7-109">有关 OpenXR 的详细信息, 包括对[临时0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)和[标头](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)的访问, 请参阅[Khronos OpenXR 页](https://www.khronos.org/openxr/)。</span><span class="sxs-lookup"><span data-stu-id="e36f7-109">For more information on OpenXR, including access to the [provisional 0.90 spec](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) and [headers](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), see the [Khronos OpenXR page](https://www.khronos.org/openxr/).</span></span> 

<span data-ttu-id="e36f7-110">可以使用混合现实 OpenXR 开发者预览版在 HoloLens 2 或台式计算机上尝试使用临时的 OpenXR 0.90 API。</span><span class="sxs-lookup"><span data-stu-id="e36f7-110">You can try out the provisional OpenXR 0.90 API on a HoloLens 2 or a desktop PC using the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="e36f7-111">此早期运行时使面向 OpenXR 0.90 API 的应用程序可以面向 HoloLens 2 或桌面上的 Windows Mixed Reality 沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="e36f7-111">This early runtime enables applications targeting the OpenXR 0.90 API to target HoloLens 2 or Windows Mixed Reality immersive headsets on the desktop.</span></span>

<span data-ttu-id="e36f7-112">如果你无权访问耳机, 则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。</span><span class="sxs-lookup"><span data-stu-id="e36f7-112">If you don't have access to a headset, you can use the HoloLens 2 Emulator or the Windows Mixed Reality Simulator instead.</span></span>

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a><span data-ttu-id="e36f7-113">为 HoloLens 2 设置混合现实 OpenXR 开发人员预览版</span><span class="sxs-lookup"><span data-stu-id="e36f7-113">Setting up the Mixed Reality OpenXR Developer Preview for HoloLens 2</span></span>

<span data-ttu-id="e36f7-114">若要开始在 HoloLens 2 上进行混合现实 OpenXR 开发者预览版:</span><span class="sxs-lookup"><span data-stu-id="e36f7-114">To get started with the Mixed Reality OpenXR Developer Preview on HoloLens 2:</span></span>

1. <span data-ttu-id="e36f7-115">设置 HoloLens 2 或按照说明[安装 hololens 2 模拟器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="e36f7-115">Set up a HoloLens 2 or follow the instructions to [install the HoloLens 2 emulator](using-the-hololens-emulator.md).</span></span>
1. <span data-ttu-id="e36f7-116">从设备或模拟器中启动应用商店应用, 并确保更新所有应用。</span><span class="sxs-lookup"><span data-stu-id="e36f7-116">Launch the Store app from within the device or emulator and ensure all apps are updated.</span></span>  <span data-ttu-id="e36f7-117">这将安装混合现实 OpenXR 开发人员预览版, 以用于该设备上的应用。</span><span class="sxs-lookup"><span data-stu-id="e36f7-117">This will install the Mixed Reality OpenXR Developer Preview for use with apps on that device.</span></span>  <span data-ttu-id="e36f7-118">如果使用模拟器, 你将需要咨询[模拟器输入说明](using-the-hololens-emulator.md#basic-emulator-input), 以帮助你在模拟器内使用应用商店应用。</span><span class="sxs-lookup"><span data-stu-id="e36f7-118">If using the emulator, you'll want to consult the [emulator input instructions](using-the-hololens-emulator.md#basic-emulator-input) to help you use the Store app within the emulator.</span></span>

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a><span data-ttu-id="e36f7-119">为沉浸式桌面耳机设置混合现实 OpenXR 开发人员预览版</span><span class="sxs-lookup"><span data-stu-id="e36f7-119">Setting up the Mixed Reality OpenXR Developer Preview for immersive desktop headsets</span></span>

<span data-ttu-id="e36f7-120">若要开始使用台式计算机上的 Mixed Reality OpenXR 开发者预览版:</span><span class="sxs-lookup"><span data-stu-id="e36f7-120">To get started with the Mixed Reality OpenXR Developer Preview on a desktop PC:</span></span>

1. <span data-ttu-id="e36f7-121">请确保运行的是 Windows 10 十月2018更新 (1809) 或 Windows 10 可能2019更新 (1903)。</span><span class="sxs-lookup"><span data-stu-id="e36f7-121">Be sure you are running the Windows 10 October 2018 Update (1809) or the Windows 10 May 2019 Update (1903).</span></span>  <span data-ttu-id="e36f7-122">如果你使用的是早期版本的 Windows 10, 则可以使用[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)升级到5月2019更新。</span><span class="sxs-lookup"><span data-stu-id="e36f7-122">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>
1. <span data-ttu-id="e36f7-123">设置 Windows Mixed Reality 耳机, 或按照说明[启用 Windows Mixed reality 模拟器](using-the-windows-mixed-reality-simulator.md)。</span><span class="sxs-lookup"><span data-stu-id="e36f7-123">Set up a Windows Mixed Reality headset or follow the instructions to [enable the Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md).</span></span>
1. <span data-ttu-id="e36f7-124">安装[混合现实 OpenXR 开发者预览版应用](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。</span><span class="sxs-lookup"><span data-stu-id="e36f7-124">Install the [Mixed Reality OpenXR Developer Preview app](https://www.microsoft.com/store/productId/9n5cvvl23qbt).</span></span>  <span data-ttu-id="e36f7-125">此应用可用于在 Windows 10 十月2018更新 (1809) 或更高版本上设置预览版 OpenXR runtime。</span><span class="sxs-lookup"><span data-stu-id="e36f7-125">This app gets you set up with the preview OpenXR runtime on Windows 10 October 2018 Update (1809) or later.</span></span>  <span data-ttu-id="e36f7-126">安装此应用后, Windows 应用商店会使运行时保持最新状态。</span><span class="sxs-lookup"><span data-stu-id="e36f7-126">After installing this app, the Windows Store will keep the runtime up to date.</span></span>
1. <span data-ttu-id="e36f7-127">从 "开始" 菜单运行 "混合现实 OpenXR" 开发人员预览版应用, 并按照说明操作, 使运行时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="e36f7-127">Run the Mixed Reality OpenXR Developer Preview app from the Start menu and follow the instructions to make the runtime active.</span></span>  <span data-ttu-id="e36f7-128">不久, 此应用程序还允许浏览其他 OpenXR 调试信息。</span><span class="sxs-lookup"><span data-stu-id="e36f7-128">Soon, this app will let you explore other OpenXR debug information as well.</span></span>

![混合现实 OpenXR 开发者预览版应用](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a><span data-ttu-id="e36f7-130">支持 Windows 10 十月2018更新</span><span class="sxs-lookup"><span data-stu-id="e36f7-130">Support for Windows 10 October 2018 Update</span></span>

<span data-ttu-id="e36f7-131">如果你运行的是 Windows 10 2019 更新 (1903), 并遵循上述步骤, 则应该已准备好使用混合现实 OpenXR 开发者预览版!</span><span class="sxs-lookup"><span data-stu-id="e36f7-131">If you're running the Windows 10 May 2019 Update (1903) and followed the steps above, you should be ready to use the Mixed Reality OpenXR Developer Preview!</span></span>

<span data-ttu-id="e36f7-132">如果尚未准备好将[台式计算机升级到 "2019 年5月更新](https://www.microsoft.com/en-us/software-download/windows10)", 则可以通过以下步骤继续使用 Windows 10 10 月2018更新 (1809):</span><span class="sxs-lookup"><span data-stu-id="e36f7-132">If you're not ready to [upgrade your desktop PC to the May 2019 Update](https://www.microsoft.com/en-us/software-download/windows10), you can get going on the Windows 10 October 2018 Update (1809) by following one more step:</span></span>

1. <span data-ttu-id="e36f7-133">按照上述步骤安装混合现实 OpenXR 开发者预览版。</span><span class="sxs-lookup"><span data-stu-id="e36f7-133">Follow the steps above to install the Mixed Reality OpenXR Developer Preview.</span></span>
1. <span data-ttu-id="e36f7-134">若要将混合现实 OpenXR 开发者预览版设置为系统的活动 OpenXR 运行时, 请安装[混合现实 OpenXR 开发者预览版兼容性包](https://aka.ms/openxr-compat)。</span><span class="sxs-lookup"><span data-stu-id="e36f7-134">To set the Mixed Reality OpenXR Developer Preview as your system's active OpenXR runtime, install the [Mixed Reality OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).</span></span>

## <a name="building-a-sample-openxr-app"></a><span data-ttu-id="e36f7-135">生成示例 OpenXR 应用</span><span class="sxs-lookup"><span data-stu-id="e36f7-135">Building a sample OpenXR app</span></span>

<span data-ttu-id="e36f7-136">[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp)项目演示了一个简单的 OpenXR 示例, 其中包含两个 Visual Studio 项目文件, 一个用于 Win32 桌面应用, 另一个用于 UWP HoloLens 2 应用。</span><span class="sxs-lookup"><span data-stu-id="e36f7-136">The [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) project demonstrates a simple OpenXR sample with two Visual Studio project files, one for both a Win32 desktop app and one for a UWP HoloLens 2 app.</span></span>  <span data-ttu-id="e36f7-137">由于解决方案包含一个 HoloLens UWP 项目, 因此需要在 Visual Studio 中安装[通用 Windows 平台开发工作负载](install-the-tools.md#installation-checklist)才能完全打开它。</span><span class="sxs-lookup"><span data-stu-id="e36f7-137">Because the solution contains a HoloLens UWP project, you'll need the [Universal Windows Platform development workload](install-the-tools.md#installation-checklist) installed in Visual Studio to fully open it.</span></span>

<span data-ttu-id="e36f7-138">请注意, 虽然 Win32 和 UWP 项目文件是独立的, 但由于打包和部署的不同, 每个项目中的应用代码都是 100%。</span><span class="sxs-lookup"><span data-stu-id="e36f7-138">Note that while the Win32 and UWP project files are separate due to differences in packaging and deployment, the app code inside each project is 100% the same!</span></span>

## <a name="feedback"></a><span data-ttu-id="e36f7-139">反馈</span><span class="sxs-lookup"><span data-stu-id="e36f7-139">Feedback</span></span>

<span data-ttu-id="e36f7-140">若要提供有关[OpenXR 临时0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)的反馈, 请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)、可[宽延时间 #openxr 频道](https://khr.io/slack)和[spec 问题跟踪](https://github.com/KhronosGroup/OpenXR-Docs/issues)器。</span><span class="sxs-lookup"><span data-stu-id="e36f7-140">To give feedback on the [OpenXR Provisional 0.90 specification](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr), [Slack #openxr channel](https://khr.io/slack) and the [spec issue tracker](https://github.com/KhronosGroup/OpenXR-Docs/issues).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e36f7-141">疑难解答</span><span class="sxs-lookup"><span data-stu-id="e36f7-141">Troubleshooting</span></span>

<span data-ttu-id="e36f7-142">下面是有关混合现实 OpenXR 开发者预览版的一些故障排除提示。</span><span class="sxs-lookup"><span data-stu-id="e36f7-142">Here are some troubleshooting tips for the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="e36f7-143">如果遇到任何其他问题, 请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)或[时差 #openxr 频道](https://khr.io/slack)。</span><span class="sxs-lookup"><span data-stu-id="e36f7-143">If you're hitting any other problems, please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr) or [Slack #openxr channel](https://khr.io/slack).</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="e36f7-144">OpenXR 应用未启动 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e36f7-144">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="e36f7-145">如果 OpenXR 应用在运行时未启动 Windows Mixed Reality, 则混合现实 OpenXR 开发者预览版可能不会设置为活动运行时。</span><span class="sxs-lookup"><span data-stu-id="e36f7-145">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Mixed Reality OpenXR Developer Preview may not be set as the active runtime.</span></span>  <span data-ttu-id="e36f7-146">请务必运行混合现实 OpenXR 开发者预览版应用, 并按照说明操作, 使运行时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="e36f7-146">Be sure to run the Mixed Reality OpenXR Developer Preview app and follow the instructions to make the runtime active.</span></span>

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a><span data-ttu-id="e36f7-147">无法安装混合现实 OpenXR 开发人员预览版应用</span><span class="sxs-lookup"><span data-stu-id="e36f7-147">Mixed Reality OpenXR Developer Preview app cannot be installed</span></span> 

<span data-ttu-id="e36f7-148">请确保至少运行 Windows 10 十月2018更新 (1809)。</span><span class="sxs-lookup"><span data-stu-id="e36f7-148">Be sure you are running at least the Windows 10 October 2018 Update (1809).</span></span>  <span data-ttu-id="e36f7-149">如果使用的是早期版本的 Windows 10, 则可以使用[windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)升级到2019更新 (1903)。</span><span class="sxs-lookup"><span data-stu-id="e36f7-149">If you're on an earlier version of Windows 10, you can upgrade to the May 2019 Update (1903) using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>

<span data-ttu-id="e36f7-150">如果混合现实 OpenXR 开发者预览版应用上的 "安装" 按钮在 Windows 10 10 月2018更新上不执行任何操作, 则您的系统可能已缓存了应用的陈旧系统要求。</span><span class="sxs-lookup"><span data-stu-id="e36f7-150">If the Install button on the Mixed Reality OpenXR Developer Preview app does nothing on Windows 10 October 2018 Update, your system may have cached stale system requirements for the app.</span></span>  <span data-ttu-id="e36f7-151">你可以从命令提示符`wsreset.exe`处运行命令来清除缓存。</span><span class="sxs-lookup"><span data-stu-id="e36f7-151">You can run the command `wsreset.exe` from a command prompt to clear the cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="e36f7-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="e36f7-152">See also</span></span>

* [<span data-ttu-id="e36f7-153">有关 OpenXR 的详细信息</span><span class="sxs-lookup"><span data-stu-id="e36f7-153">More information on OpenXR</span></span>](https://www.khronos.org/openxr/)
* [<span data-ttu-id="e36f7-154">OpenXR 临时0.90 规范</span><span class="sxs-lookup"><span data-stu-id="e36f7-154">OpenXR Provisional 0.90 specification</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [<span data-ttu-id="e36f7-155">OpenXR 临时 0.90 API 参考</span><span class="sxs-lookup"><span data-stu-id="e36f7-155">OpenXR Provisional 0.90 API reference</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [<span data-ttu-id="e36f7-156">OpenXR 临时0.90 标头</span><span class="sxs-lookup"><span data-stu-id="e36f7-156">OpenXR Provisional 0.90 headers</span></span>](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [<span data-ttu-id="e36f7-157">OpenXR 临时0.90 快速参考指南</span><span class="sxs-lookup"><span data-stu-id="e36f7-157">OpenXR Provisional 0.90 quick reference guide</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
