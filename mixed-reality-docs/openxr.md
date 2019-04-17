---
title: OpenXR
description: 尝试临时 OpenXR 0.90 API 与混合现实 OpenXR 开发者预览版。
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 混合的现实 OpenXR 开发者预览版
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592752"
---
# <a name="openxr"></a><span data-ttu-id="28e0b-104">OpenXR</span><span class="sxs-lookup"><span data-stu-id="28e0b-104">OpenXR</span></span>

<span data-ttu-id="28e0b-105">OpenXR 是开放式的免版税的标准从[Khronos](https://www.khronos.org/)提供对各种设备的时间跨度的许多供应商从本机访问[混合的现实范围](mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-105">OpenXR is an open royalty-free standard from [Khronos](https://www.khronos.org/) that provides native access to a wide range of devices from many vendors that span across the [mixed reality spectrum](mixed-reality.md).</span></span>

<span data-ttu-id="28e0b-106">使用 OpenXR，您可以构建面向 holographic 设备 （如 HoloLens 2)，将数字内容放置在现实生活中，就好像确实存在，以及隐藏的沉浸式设备 （如桌面 Pc 的 Windows 混合现实耳机） 的应用程序物理世界并替换为数字的体验。</span><span class="sxs-lookup"><span data-stu-id="28e0b-106">With OpenXR, you can build applications that target both holographic devices (like HoloLens 2) that place digital content in the real world as if it were really there, as well as immersive devices (like Windows Mixed Reality headsets for desktop PCs) that hide the physical world and replace it with a digital experience.</span></span>  <span data-ttu-id="28e0b-107">OpenXR 允许你编写代码后，然后可移植对多种硬件平台。</span><span class="sxs-lookup"><span data-stu-id="28e0b-107">OpenXR lets you write code once that's then portable across a wide range of hardware platforms.</span></span>

<span data-ttu-id="28e0b-108">OpenXR 标准当前在临时阶段中，是与发布的反馈意见的初始 OpenXR 0.90 规范。</span><span class="sxs-lookup"><span data-stu-id="28e0b-108">The OpenXR standard is currently in a provisional phase, with an initial OpenXR 0.90 spec released for feedback.</span></span>  <span data-ttu-id="28e0b-109">有关详细信息 OpenXR，包括对访问权限[临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)和[标头](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)，请参阅[Khronos OpenXR 页](https://www.khronos.org/openxr/)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-109">For more information on OpenXR, including access to the [provisional 0.90 spec](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) and [headers](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), see the [Khronos OpenXR page](https://www.khronos.org/openxr/).</span></span>

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a><span data-ttu-id="28e0b-110">设置混合现实 OpenXR 开发者预览版</span><span class="sxs-lookup"><span data-stu-id="28e0b-110">Setting up the Mixed Reality OpenXR Developer Preview</span></span>

<span data-ttu-id="28e0b-111">您可以尝试立即使用混合现实 OpenXR 开发者预览版临时 OpenXR 0.90 API。</span><span class="sxs-lookup"><span data-stu-id="28e0b-111">You can try out the provisional OpenXR 0.90 API today using the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="28e0b-112">此早期的运行时，定位到桌面上的目标 Windows Mixed Reality 沉浸式耳机 OpenXR 0.90 API 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="28e0b-112">This early runtime enables applications targeting the OpenXR 0.90 API to target Windows Mixed Reality immersive headsets on the desktop.</span></span>  <span data-ttu-id="28e0b-113">如果无法访问头戴式耳机，可以改为使用 Windows 混合现实模拟器。</span><span class="sxs-lookup"><span data-stu-id="28e0b-113">If you don't have access to a headset, you can use the Windows Mixed Reality Simulator instead.</span></span>

<span data-ttu-id="28e0b-114">若要开始使用混合现实 OpenXR 开发者预览版：</span><span class="sxs-lookup"><span data-stu-id="28e0b-114">To get started with the Mixed Reality OpenXR Developer Preview:</span></span>

1. <span data-ttu-id="28e0b-115">确保你至少运行 Windows 10 2018 年 10 月更新。</span><span class="sxs-lookup"><span data-stu-id="28e0b-115">Be sure you are running at least the Windows 10 October 2018 Update.</span></span>  <span data-ttu-id="28e0b-116">如果您在早期版本的 Windows 10 上，你可以升级到 2018 年 10 月更新使用[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-116">If you're on an earlier version of Windows 10, you can upgrade to the October 2018 Update using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>  <span data-ttu-id="28e0b-117">如果您感到大胆，则可以安装[Windows 10 Insider Preview 生成](https://insider.windows.com)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-117">If you're feeling adventurous, you can install a [Windows 10 Insider Preview build](https://insider.windows.com).</span></span>
1. <span data-ttu-id="28e0b-118">设置 Windows 混合现实耳机或按照说明[启用 Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-118">Set up a Windows Mixed Reality headset or follow the instructions to [enable the Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md).</span></span>
1. <span data-ttu-id="28e0b-119">安装[混合的现实 OpenXR 开发人员预览应用](https://www.microsoft.com/store/productId/9n5cvvl23qbt)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-119">Install the [Mixed Reality OpenXR Developer Preview app](https://www.microsoft.com/store/productId/9n5cvvl23qbt).</span></span>  <span data-ttu-id="28e0b-120">此应用可帮助你在 Windows 上使用预览 OpenXR 运行时设置了 10 2018 年 10 月更新或更高版本。</span><span class="sxs-lookup"><span data-stu-id="28e0b-120">This app gets you set up with the preview OpenXR runtime on Windows 10 October 2018 Update or later.</span></span>  <span data-ttu-id="28e0b-121">安装此应用后，Windows 应用商店将保留在运行时保持最新。</span><span class="sxs-lookup"><span data-stu-id="28e0b-121">After installing this app, the Windows Store will keep the runtime up to date.</span></span>
1. <span data-ttu-id="28e0b-122">从开始菜单运行混合现实 OpenXR 开发者预览版应用并按照说明进行操作以使运行时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="28e0b-122">Run the Mixed Reality OpenXR Developer Preview app from the Start menu and follow the instructions to make the runtime active.</span></span>  <span data-ttu-id="28e0b-123">很快，此应用会让您浏览以及其他 OpenXR 调试信息。</span><span class="sxs-lookup"><span data-stu-id="28e0b-123">Soon, this app will let you explore other OpenXR debug information as well.</span></span>

![混合的现实 OpenXR 开发人员预览应用](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a><span data-ttu-id="28e0b-125">支持 Windows 10 2018 年 10 月更新</span><span class="sxs-lookup"><span data-stu-id="28e0b-125">Support for Windows 10 October 2018 Update</span></span>

<span data-ttu-id="28e0b-126">若要开始使用混合现实 OpenXR 开发者预览版在 Windows 10 2018 年 10 月更新 （Windows 的当前版本），将需要遵循几个步骤：</span><span class="sxs-lookup"><span data-stu-id="28e0b-126">To get going with the Mixed Reality OpenXR Developer Preview on the Windows 10 October 2018 Update (the current version of Windows), you'll need to follow a few more steps:</span></span>

1. <span data-ttu-id="28e0b-127">按照上述步骤来安装混合现实 OpenXR 开发者预览版。</span><span class="sxs-lookup"><span data-stu-id="28e0b-127">Follow the steps above to install the Mixed Reality OpenXR Developer Preview.</span></span>
1. <span data-ttu-id="28e0b-128">若要将您的系统活动 OpenXR 运行时设置混合现实 OpenXR 开发者预览版，请安装[混合现实 OpenXR 开发人员预览版兼容性工具包](https://aka.ms/openxr-compat)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-128">To set the Mixed Reality OpenXR Developer Preview as your system's active OpenXR runtime, install the [Mixed Reality OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat).</span></span>

## <a name="building-a-test-openxr-app"></a><span data-ttu-id="28e0b-129">构建测试 OpenXR 应用</span><span class="sxs-lookup"><span data-stu-id="28e0b-129">Building a test OpenXR app</span></span>

<span data-ttu-id="28e0b-130">[Hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR 测试应用程序说明如何使用 API 的各个部分。</span><span class="sxs-lookup"><span data-stu-id="28e0b-130">The [hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR test app demonstrates use of various parts of the API.</span></span>  <span data-ttu-id="28e0b-131">您可以按照以下[构建说明](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md)，这将生成测试应用程序和 OpenXR 标头本身。</span><span class="sxs-lookup"><span data-stu-id="28e0b-131">You can follow these [build instructions](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md), which will build both the test app and the OpenXR headers themselves.</span></span>

## <a name="feedback"></a><span data-ttu-id="28e0b-132">反馈</span><span class="sxs-lookup"><span data-stu-id="28e0b-132">Feedback</span></span>

<span data-ttu-id="28e0b-133">若要提供有关反馈[OpenXR 临时 0.90 规范](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)，请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)， [#openxr Slack 通道](https://khr.io/slack)和[规范问题跟踪程序](https://github.com/KhronosGroup/OpenXR-Docs/issues)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-133">To give feedback on the [OpenXR Provisional 0.90 specification](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr), [Slack #openxr channel](https://khr.io/slack) and the [spec issue tracker](https://github.com/KhronosGroup/OpenXR-Docs/issues).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="28e0b-134">疑难解答</span><span class="sxs-lookup"><span data-stu-id="28e0b-134">Troubleshooting</span></span>

<span data-ttu-id="28e0b-135">以下是有关混合现实 OpenXR 开发者预览版的一些故障排除提示。</span><span class="sxs-lookup"><span data-stu-id="28e0b-135">Here are some troubleshooting tips for the Mixed Reality OpenXR Developer Preview.</span></span>  <span data-ttu-id="28e0b-136">如果在遇到任何其他问题，请访问[Khronos OpenXR 论坛](https://community.khronos.org/c/openxr)或[#openxr Slack 通道](https://khr.io/slack)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-136">If you're hitting any other problems, please visit the [Khronos OpenXR Forums](https://community.khronos.org/c/openxr) or [Slack #openxr channel](https://khr.io/slack).</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="28e0b-137">未启动 Windows Mixed Reality OpenXR 应用</span><span class="sxs-lookup"><span data-stu-id="28e0b-137">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="28e0b-138">如果 OpenXR 应用未启动 Windows Mixed Reality 在运行时，混合现实 OpenXR 开发者预览版可能不会设置为活动的运行时。</span><span class="sxs-lookup"><span data-stu-id="28e0b-138">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Mixed Reality OpenXR Developer Preview may not be set as the active runtime.</span></span>  <span data-ttu-id="28e0b-139">请确保运行混合现实 OpenXR 开发者预览版应用并按照说明进行操作以使运行时处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="28e0b-139">Be sure to run the Mixed Reality OpenXR Developer Preview app and follow the instructions to make the runtime active.</span></span>

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a><span data-ttu-id="28e0b-140">混合的现实 OpenXR 开发者预览版应用无法在安装</span><span class="sxs-lookup"><span data-stu-id="28e0b-140">Mixed Reality OpenXR Developer Preview app cannot be installed</span></span> 

<span data-ttu-id="28e0b-141">确保你至少运行 Windows 10 2018 年 10 月更新。</span><span class="sxs-lookup"><span data-stu-id="28e0b-141">Be sure you are running at least the Windows 10 October 2018 Update.</span></span>  <span data-ttu-id="28e0b-142">如果您在早期版本的 Windows 10 上，你可以升级到 2018 年 10 月更新使用[Windows 10 更新助手](https://www.microsoft.com/en-us/software-download/windows10)。</span><span class="sxs-lookup"><span data-stu-id="28e0b-142">If you're on an earlier version of Windows 10, you can upgrade to the October 2018 Update using the [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10).</span></span>

<span data-ttu-id="28e0b-143">如果安装按钮上的混合现实 OpenXR 开发者预览版应用不会在 Windows 10 2018 年 10 月更新，您的系统已缓存应用程序的过时的系统要求。</span><span class="sxs-lookup"><span data-stu-id="28e0b-143">If the Install button on the Mixed Reality OpenXR Developer Preview app does nothing on Windows 10 October 2018 Update, your system may have cached stale system requirements for the app.</span></span>  <span data-ttu-id="28e0b-144">可以运行命令`wsreset.exe`在命令提示符下，若要清除的缓存。</span><span class="sxs-lookup"><span data-stu-id="28e0b-144">You can run the command `wsreset.exe` from a command prompt to clear the cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="28e0b-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="28e0b-145">See also</span></span>

* [<span data-ttu-id="28e0b-146">OpenXR 的详细信息</span><span class="sxs-lookup"><span data-stu-id="28e0b-146">More information on OpenXR</span></span>](https://www.khronos.org/openxr/)
* [<span data-ttu-id="28e0b-147">OpenXR 临时 0.90 规范</span><span class="sxs-lookup"><span data-stu-id="28e0b-147">OpenXR Provisional 0.90 specification</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [<span data-ttu-id="28e0b-148">OpenXR 临时 0.90 API 参考</span><span class="sxs-lookup"><span data-stu-id="28e0b-148">OpenXR Provisional 0.90 API reference</span></span>](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [<span data-ttu-id="28e0b-149">OpenXR 临时 0.90 标头</span><span class="sxs-lookup"><span data-stu-id="28e0b-149">OpenXR Provisional 0.90 headers</span></span>](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
