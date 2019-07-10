---
title: 面向开发人员混合现实捕获
description: 面向开发人员捕获混合现实的最佳做法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、 照片、 视频、 捕获、 照相机
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694365"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="55bcb-104">面向开发人员混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="55bcb-104">Mixed reality capture for developers</span></span>

> <span data-ttu-id="55bcb-105">[注意 ！]请参阅[PV 照相机从呈现](#render-from-the-pv-camera-opt-in)下面有关 HoloLens 2 新 MRC 功能的指导。</span><span class="sxs-lookup"><span data-stu-id="55bcb-105">[NOTE!] See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="55bcb-106">因为用户可能需要花[混合现实捕获](mixed-reality-capture.md)(MRC) 照片或视频在任何时间，没有开发应用程序时应牢记的一些事项。</span><span class="sxs-lookup"><span data-stu-id="55bcb-106">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="55bcb-107">这包括 MRC 视觉质量和正在响应系统更改，而将其捕获 MRCs 的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="55bcb-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="55bcb-108">开发人员可以也可无缝集成混合的现实捕获和插入到其应用程序。</span><span class="sxs-lookup"><span data-stu-id="55bcb-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="55bcb-109">MRC HoloLens （第一代） 上的支持视频和照片最多为 720p，虽然 MRC HoloLens 2 上的支持多达 1080p 和照片的视频最多有 4k 分辨率。</span><span class="sxs-lookup"><span data-stu-id="55bcb-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="55bcb-110">质量 MRC 的重要性</span><span class="sxs-lookup"><span data-stu-id="55bcb-110">The importance of quality MRC</span></span>

<span data-ttu-id="55bcb-111">混合的现实捕获照片和视频可能是首次用户将拥有的应用程序。</span><span class="sxs-lookup"><span data-stu-id="55bcb-111">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="55bcb-112">是否为 Microsoft Store 页上或从其他用户在社交网络上共享 MRCs 的混合的现实屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="55bcb-112">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="55bcb-113">使用 MRC 演示您的应用程序，对用户进行培训，鼓励用户共享其混合的世界交互，以及用户调查和解决问题。</span><span class="sxs-lookup"><span data-stu-id="55bcb-113">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="55bcb-114">MRC 如何影响您的应用程序</span><span class="sxs-lookup"><span data-stu-id="55bcb-114">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="55bcb-115">在应用中启用 MRC</span><span class="sxs-lookup"><span data-stu-id="55bcb-115">Enabling MRC in your app</span></span>

<span data-ttu-id="55bcb-116">默认情况下，不需要执行任何操作即可使用户能够执行混合的现实捕获应用程序。</span><span class="sxs-lookup"><span data-stu-id="55bcb-116">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="55bcb-117">启用应用程序中的改进了对齐方式 MRC</span><span class="sxs-lookup"><span data-stu-id="55bcb-117">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="55bcb-118">默认情况下，混合的现实捕获组合和照片/视频 (PV) 摄像机正确的人眼 holographic 输出。</span><span class="sxs-lookup"><span data-stu-id="55bcb-118">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="55bcb-119">使用由当前正在运行沉浸式应用程序设置的焦点位置组合这些两个源。</span><span class="sxs-lookup"><span data-stu-id="55bcb-119">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="55bcb-120">这意味着全息焦点平面外的不能也 （由于 PV 照相机和右侧显示之间的物理距离） 对齐。</span><span class="sxs-lookup"><span data-stu-id="55bcb-120">This means that holograms outside the focus plane won't align as well (due to the physical distance between the PV camera and the right display).</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="55bcb-121">设置焦点</span><span class="sxs-lookup"><span data-stu-id="55bcb-121">Set the focus point</span></span>

<span data-ttu-id="55bcb-122">（在 HoloLens) 的沉浸式应用程序应设置[关注点](focus-point-in-unity.md)，他们想要为其稳定平面。</span><span class="sxs-lookup"><span data-stu-id="55bcb-122">Immersive apps (on HoloLens) should set the [focus point](focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="55bcb-123">这可确保这两个耳机和混合的现实捕获中最佳的对齐方式。</span><span class="sxs-lookup"><span data-stu-id="55bcb-123">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="55bcb-124">如果未设置焦点，稳定平面将默认为两个指标。</span><span class="sxs-lookup"><span data-stu-id="55bcb-124">If a focus point is not set, the stabilization plane will default to two meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="55bcb-125">从 （选择中） 的 PV 照相机呈现</span><span class="sxs-lookup"><span data-stu-id="55bcb-125">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="55bcb-126">HoloLens 2 添加了沉浸式应用程序的功能**PV 照相机从呈现**混合的现实捕获正在运行时。</span><span class="sxs-lookup"><span data-stu-id="55bcb-126">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="55bcb-127">若要确保应用正确支持其他呈现器，则应用必须参加与此功能。</span><span class="sxs-lookup"><span data-stu-id="55bcb-127">To ensure the app supports the additional render correctly, the app has to opt-in to this functionality.</span></span>

<span data-ttu-id="55bcb-128">呈现从 PV 照相机产品/服务通过默认 MRC 体验了以下改进：</span><span class="sxs-lookup"><span data-stu-id="55bcb-128">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="55bcb-129">全息图对齐到你的物理环境和手 （适用于近交互） 应是准确的根本距离，而不是让在而不是关注点的距离的偏移量，正如您可能会看到默认 MRC 中。</span><span class="sxs-lookup"><span data-stu-id="55bcb-129">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="55bcb-130">不会损害耳机右侧的眼睛，因为不会使用它来呈现为 MRC 输出全息。</span><span class="sxs-lookup"><span data-stu-id="55bcb-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="55bcb-131">有三个步骤以启用从 PV 照相机呈现：</span><span class="sxs-lookup"><span data-stu-id="55bcb-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="55bcb-132">启用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="55bcb-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="55bcb-133">处理其他 HolographicCamera 呈现器</span><span class="sxs-lookup"><span data-stu-id="55bcb-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="55bcb-134">验证你的着色器和代码正确呈现此额外 HolographicCamera 从</span><span class="sxs-lookup"><span data-stu-id="55bcb-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a><span data-ttu-id="55bcb-135">启用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="55bcb-135">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>

<span data-ttu-id="55bcb-136">为选择加入的应用程序只是让 PhotoVideoCamera [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span><span class="sxs-lookup"><span data-stu-id="55bcb-136">To opt-in, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="55bcb-137">处理其他 HolographicCamera 呈现 DirectX 中</span><span class="sxs-lookup"><span data-stu-id="55bcb-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="55bcb-138">当应用程序处于启用状态来呈现来自 PV 摄像机和混合的现实捕获开始：</span><span class="sxs-lookup"><span data-stu-id="55bcb-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="55bcb-139">HolographicSpace 的 CameraAdded 事件将激发。</span><span class="sxs-lookup"><span data-stu-id="55bcb-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="55bcb-140">如果应用程序不能在此时处理照相机可以推迟此事件。</span><span class="sxs-lookup"><span data-stu-id="55bcb-140">This event can be deferred if the app cannot handle the camera at this time.</span></span>
2. <span data-ttu-id="55bcb-141">该事件已完成 （并有任何未完成延迟） 后 HolographicCamera 会在下一步 HolographicFrame AddedCameras 列表中。</span><span class="sxs-lookup"><span data-stu-id="55bcb-141">Once the event has completed (and there are no outstanding deferrals) the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="55bcb-142">混合的现实捕获将停止时 （或混合的现实捕获正在运行时，应用程序禁用视图配置）： HolographicCamera 会在下一步 HolographicFrame RemovedCameras 列表中，将 HolographicSpace CameraRemoved 事件激发。</span><span class="sxs-lookup"><span data-stu-id="55bcb-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="55bcb-143">一个[ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)属性已添加到 HolographicCamera 以帮助识别照相机所属的配置。</span><span class="sxs-lookup"><span data-stu-id="55bcb-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="55bcb-144">处理其他 HolographicCamera 呈现在 Unity 中</span><span class="sxs-lookup"><span data-stu-id="55bcb-144">Handle the additional HolographicCamera render in Unity</span></span>

>[!NOTE]
> <span data-ttu-id="55bcb-145">Unity 支持从 PV 照相机呈现在开发和不能使用，尚未。</span><span class="sxs-lookup"><span data-stu-id="55bcb-145">Unity support to render from the PV camera is under development and can't be used, yet.</span></span> <span data-ttu-id="55bcb-146">当从 PV 照相机呈现支持 Unity 的版本可用时，将更新本文档。</span><span class="sxs-lookup"><span data-stu-id="55bcb-146">This documentation will be updated when a build of Unity with support for rendering from the PV camera is available.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="55bcb-147">验证着色器和代码支持其他照相机</span><span class="sxs-lookup"><span data-stu-id="55bcb-147">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="55bcb-148">运行混合的现实捕获并检查有不寻常的对齐方式、 缺少的内容或性能问题。</span><span class="sxs-lookup"><span data-stu-id="55bcb-148">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="55bcb-149">更新着色器和相应的代码。</span><span class="sxs-lookup"><span data-stu-id="55bcb-149">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="55bcb-150">如果有无法支持其他摄像头的呈现某些场景，可以在这些期间禁用 PhotoVideoCamera HolographicViewConfiguration。</span><span class="sxs-lookup"><span data-stu-id="55bcb-150">If there are certain scenes that cannot support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration during them.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="55bcb-151">应用程序中禁用 MRC</span><span class="sxs-lookup"><span data-stu-id="55bcb-151">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="55bcb-152">2D 应用</span><span class="sxs-lookup"><span data-stu-id="55bcb-152">2D app</span></span>

<span data-ttu-id="55bcb-153">2D 应用程序可以选择让混合的现实捕获正在运行的被遮挡住其可视内容：</span><span class="sxs-lookup"><span data-stu-id="55bcb-153">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="55bcb-154">在与[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)标志</span><span class="sxs-lookup"><span data-stu-id="55bcb-154">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="55bcb-155">创建与应用程序的交换链[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)标志</span><span class="sxs-lookup"><span data-stu-id="55bcb-155">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="55bcb-156">Windows 10 的可能 2019年更新设置 ApplicationView 的[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span><span class="sxs-lookup"><span data-stu-id="55bcb-156">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="55bcb-157">沉浸式应用程序</span><span class="sxs-lookup"><span data-stu-id="55bcb-157">Immersive app</span></span>

<span data-ttu-id="55bcb-158">沉浸式应用程序可以选择从通过混合的现实捕获中排除其可视内容：</span><span class="sxs-lookup"><span data-stu-id="55bcb-158">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="55bcb-159">设置的 HolographicCameraRenderingParameter [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)以禁用及其关联的帧的混合的现实捕获</span><span class="sxs-lookup"><span data-stu-id="55bcb-159">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="55bcb-160">设置的 HolographicCamera [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)以禁用其关联的 holographic 照相机的混合的现实捕获</span><span class="sxs-lookup"><span data-stu-id="55bcb-160">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="55bcb-161">密码键盘</span><span class="sxs-lookup"><span data-stu-id="55bcb-161">Password Keyboard</span></span>

<span data-ttu-id="55bcb-162">Windows 10 的可能 2019年更新、 密码或 pin 键盘可见时自动从混合的现实捕获排除视觉内容。</span><span class="sxs-lookup"><span data-stu-id="55bcb-162">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="55bcb-163">了解当 MRC 处于活动状态</span><span class="sxs-lookup"><span data-stu-id="55bcb-163">Knowing when MRC is active</span></span>

<span data-ttu-id="55bcb-164">[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)类可以由应用程序了解混合现实捕获系统 （对于音频或视频） 的运行时。</span><span class="sxs-lookup"><span data-stu-id="55bcb-164">The [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="55bcb-165">AppCapture 的[GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可以返回 null，如果混合现实捕获不是设备上可用。</span><span class="sxs-lookup"><span data-stu-id="55bcb-165">AppCapture's [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="55bcb-166">还有一点需要取消注册您的应用程序挂起时的 CapturingChanged 事件，否则 MRC 可能会进入阻止状态。</span><span class="sxs-lookup"><span data-stu-id="55bcb-166">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="55bcb-167">最佳做法 （特定于 HoloLens 的）</span><span class="sxs-lookup"><span data-stu-id="55bcb-167">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="55bcb-168">MRC 预期工作，而其他工作从开发人员，但有几个事项需要注意的以提供您的应用程序的最佳混合的现实捕获体验。</span><span class="sxs-lookup"><span data-stu-id="55bcb-168">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="55bcb-169">**MRC 使用全息图的 alpha 通道来与混合[照相机](locatable-camera.md)图像**</span><span class="sxs-lookup"><span data-stu-id="55bcb-169">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="55bcb-170">最重要的步骤是确保您的应用程序清除为透明黑色，而不是为不透明的黑色清除。</span><span class="sxs-lookup"><span data-stu-id="55bcb-170">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="55bcb-171">在 Unity 中，这是 MixedRealityToolkit 默认情况下，但如果你正在开发非 Unity 中，您可能需要进行更改的一行。</span><span class="sxs-lookup"><span data-stu-id="55bcb-171">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="55bcb-172">下面是一些你可能会在 MRC 中，如果您的应用程序不会清除为透明黑色的项目：</span><span class="sxs-lookup"><span data-stu-id="55bcb-172">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="55bcb-173">**示例故障**:黑色边缘周围的内容 （未能清除为透明黑色）</span><span class="sxs-lookup"><span data-stu-id="55bcb-173">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

<span data-ttu-id="55bcb-174">**示例故障**:整个背景场景的全息图显示为黑色。</span><span class="sxs-lookup"><span data-stu-id="55bcb-174">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="55bcb-175">在黑色背景中设置背景 alpha 值为 1 的结果</span><span class="sxs-lookup"><span data-stu-id="55bcb-175">Setting a background alpha value of 1 results in a black background</span></span>

![在黑色背景中设置背景 alpha 值为 1 的结果](images/clearopaqueblack-300px.png)

<span data-ttu-id="55bcb-177">**预期结果**:全息显示正确混合与现实世界 （如果清除为透明黑色预期结果）</span><span class="sxs-lookup"><span data-stu-id="55bcb-177">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![如果清除为透明黑色的预期的结果](images/cleartransparentblack-300px.png)

<span data-ttu-id="55bcb-179">**解决方案**：</span><span class="sxs-lookup"><span data-stu-id="55bcb-179">**Solution**:</span></span>
* <span data-ttu-id="55bcb-180">更改任何内容都如何显示为不透明的黑色具有 alpha 值为 0。</span><span class="sxs-lookup"><span data-stu-id="55bcb-180">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="55bcb-181">请确保该应用程序正在清除为透明黑色。</span><span class="sxs-lookup"><span data-stu-id="55bcb-181">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="55bcb-182">若要清除此选项可自动清除 MixedRealityToolkit，但如果它是一个非 Unity 应用，应修改与 ID3D11DeiceContext::ClearRenderTargetView() 一起使用的颜色与 unity 默认值。</span><span class="sxs-lookup"><span data-stu-id="55bcb-182">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="55bcb-183">你想要确保清除为透明黑色 (0,0,0,0) 而不是不透明黑 (0,0,0,1)。</span><span class="sxs-lookup"><span data-stu-id="55bcb-183">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="55bcb-184">如果想要但通常不需要现在可以优化你的资产的 alpha 值。</span><span class="sxs-lookup"><span data-stu-id="55bcb-184">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="55bcb-185">大多数情况下，MRCs 看现成的很好。</span><span class="sxs-lookup"><span data-stu-id="55bcb-185">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="55bcb-186">MRC 假定预乘的 alpha。</span><span class="sxs-lookup"><span data-stu-id="55bcb-186">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="55bcb-187">Alpha 值只会影响 MRC 捕获。</span><span class="sxs-lookup"><span data-stu-id="55bcb-187">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="55bcb-188">在 HoloLens 上启用 MRC 时会发生什么</span><span class="sxs-lookup"><span data-stu-id="55bcb-188">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="55bcb-189">以下内容适用于 HoloLens （第一代） 和 HoloLens 2，除非另有说明：</span><span class="sxs-lookup"><span data-stu-id="55bcb-189">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="55bcb-190">系统将限制为 30 Hz 呈现应用程序。</span><span class="sxs-lookup"><span data-stu-id="55bcb-190">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="55bcb-191">这将创建一些空间用于 MRC 运行，因此应用程序不需要保留的常量预算保留并也匹配 30 fps MRC 视频记录帧速率</span><span class="sxs-lookup"><span data-stu-id="55bcb-191">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="55bcb-192">全息图内容眼里出正确的设备时可能会显示以"礼花绽放"流式处理记录/MRC： 文本可能会变得更难以阅读和全息图边缘可能会出现更锯齿状 (在选择加入第三照相机上呈现**HoloLens 2**可避免此入侵）</span><span class="sxs-lookup"><span data-stu-id="55bcb-192">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="55bcb-193">MRC 照片和视频将遵守该应用程序[关注点](focus-point-in-unity.md)如果应用程序启用了它，这将有助于确保全息准确地定位。</span><span class="sxs-lookup"><span data-stu-id="55bcb-193">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="55bcb-194">对于视频，因此全息看起来似乎如果焦点深度发生了重大变化缓慢偏差到位平滑处理的焦点位置。</span><span class="sxs-lookup"><span data-stu-id="55bcb-194">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="55bcb-195">位于不同深度的焦点位置从全息可能在现实生活 （请参阅下面的示例，在 2 米设置焦点，但全息图定位在 1 米） 中显示偏移量。</span><span class="sxs-lookup"><span data-stu-id="55bcb-195">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![在 2 米全息会完全对公众已注册。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="55bcb-198">将从您的应用程序中的 MRC 功能集成</span><span class="sxs-lookup"><span data-stu-id="55bcb-198">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="55bcb-199">混合的现实应用 MRC 照片或视频捕获从在应用中，可以启动和捕获的内容将无需存储提供给您的应用程序到设备的"本机照片。"</span><span class="sxs-lookup"><span data-stu-id="55bcb-199">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="55bcb-200">可以创建自定义 MRC 记录器或充分利用内置相机捕捉 UI。</span><span class="sxs-lookup"><span data-stu-id="55bcb-200">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="55bcb-201">使用内置相机 UI MRC</span><span class="sxs-lookup"><span data-stu-id="55bcb-201">MRC with built-in camera UI</span></span>

<span data-ttu-id="55bcb-202">开发人员可以使用 *[摄像头捕获 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 若要获取用户捕获混合的现实照片或视频只需几行代码。</span><span class="sxs-lookup"><span data-stu-id="55bcb-202">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="55bcb-203">此 API 启动内置 MRC 摄像头 UI，从该用户可以拍摄照片或视频，并返回结果捕获到您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="55bcb-203">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="55bcb-204">如果你想要创建您自己摄像头 UI，或需要较低级别捕获对流的访问权限，则可以创建自定义的混合现实捕获记录器。</span><span class="sxs-lookup"><span data-stu-id="55bcb-204">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="55bcb-205">创建自定义 MRC 记录器</span><span class="sxs-lookup"><span data-stu-id="55bcb-205">Creating a custom MRC recorder</span></span>

<span data-ttu-id="55bcb-206">虽然用户始终可以触发照片或视频使用系统 MRC 捕获服务，应用程序可能想要生成自定义的相机应用程序，但就像 MRC 照相机流中包括全息。</span><span class="sxs-lookup"><span data-stu-id="55bcb-206">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="55bcb-207">这样，应用程序启动捕获代表用户、 生成自定义录制用户界面，或自定义 MRC 设置命名的几个示例。</span><span class="sxs-lookup"><span data-stu-id="55bcb-207">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="55bcb-208">**HoloStudio 添加自定义 MRC 照相机使用 MRC 效果**</span><span class="sxs-lookup"><span data-stu-id="55bcb-208">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio 添加自定义 MRC 照相机使用 MRC 效果](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="55bcb-210">Unity 应用程序应会看到[Locatable_camera_in_Unity](locatable-camera-in-unity.md)要启用全息的属性。</span><span class="sxs-lookup"><span data-stu-id="55bcb-210">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="55bcb-211">其他应用程序可以执行此操作通过使用[Windows 媒体捕获 Api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)控制照相机并添加要在静止图像和视频中包含虚拟全息和应用程序音频 MRC 视频和音频效果。</span><span class="sxs-lookup"><span data-stu-id="55bcb-211">Other applications can do this by using the [Windows Media Capture APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="55bcb-212">应用程序具有两个选项来添加效果：</span><span class="sxs-lookup"><span data-stu-id="55bcb-212">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="55bcb-213">较旧的 API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="55bcb-213">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="55bcb-214">新的 Microsoft 建议 API （返回一个对象，使其可以处理动态属性）：[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync)需要应用程序创建其自己实现[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)并[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)。</span><span class="sxs-lookup"><span data-stu-id="55bcb-214">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="55bcb-215">请参阅示例用法 MRC 效果示例。</span><span class="sxs-lookup"><span data-stu-id="55bcb-215">Please see the MRC effect sample for sample usage.</span></span>

>[!NOTE]
> <span data-ttu-id="55bcb-216">Visual Studio 中，将不会识别 Windows.Media.MixedRealityCapture 命名空间，但字符串仍有效。</span><span class="sxs-lookup"><span data-stu-id="55bcb-216">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="55bcb-217">MRC 视频效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="55bcb-217">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="55bcb-218">属性名</span><span class="sxs-lookup"><span data-stu-id="55bcb-218">Property Name</span></span>  |  <span data-ttu-id="55bcb-219">type</span><span class="sxs-lookup"><span data-stu-id="55bcb-219">Type</span></span>  |  <span data-ttu-id="55bcb-220">Default Value</span><span class="sxs-lookup"><span data-stu-id="55bcb-220">Default Value</span></span>  |  <span data-ttu-id="55bcb-221">描述</span><span class="sxs-lookup"><span data-stu-id="55bcb-221">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="55bcb-222">StreamType</span><span class="sxs-lookup"><span data-stu-id="55bcb-222">StreamType</span></span>  |  <span data-ttu-id="55bcb-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span><span class="sxs-lookup"><span data-stu-id="55bcb-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="55bcb-224">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="55bcb-224">1 (VideoRecord)</span></span>  |  <span data-ttu-id="55bcb-225">描述此效果用于捕获的流。</span><span class="sxs-lookup"><span data-stu-id="55bcb-225">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="55bcb-226">音频不可用。</span><span class="sxs-lookup"><span data-stu-id="55bcb-226">Audio is not available.</span></span> | 
|  <span data-ttu-id="55bcb-227">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="55bcb-227">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="55bcb-228">boolean</span><span class="sxs-lookup"><span data-stu-id="55bcb-228">boolean</span></span>  |  <span data-ttu-id="55bcb-229">TRUE</span><span class="sxs-lookup"><span data-stu-id="55bcb-229">TRUE</span></span>  |  <span data-ttu-id="55bcb-230">若要启用或禁用全息视频捕获中的标记。</span><span class="sxs-lookup"><span data-stu-id="55bcb-230">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="55bcb-231">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="55bcb-231">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="55bcb-232">boolean</span><span class="sxs-lookup"><span data-stu-id="55bcb-232">boolean</span></span>  |  <span data-ttu-id="55bcb-233">TRUE</span><span class="sxs-lookup"><span data-stu-id="55bcb-233">TRUE</span></span>  |  <span data-ttu-id="55bcb-234">一个标志，用于启用或禁用在屏幕上的录制指示器全息图捕获过程。</span><span class="sxs-lookup"><span data-stu-id="55bcb-234">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="55bcb-235">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="55bcb-235">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="55bcb-236">boolean</span><span class="sxs-lookup"><span data-stu-id="55bcb-236">boolean</span></span>  |  <span data-ttu-id="55bcb-237">FALSE</span><span class="sxs-lookup"><span data-stu-id="55bcb-237">FALSE</span></span>  |  <span data-ttu-id="55bcb-238">一个标志，用于启用或禁用由 HoloLens 跟踪程序提供支持的视频防抖动。</span><span class="sxs-lookup"><span data-stu-id="55bcb-238">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="55bcb-239">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="55bcb-239">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="55bcb-240">UINT32</span><span class="sxs-lookup"><span data-stu-id="55bcb-240">UINT32</span></span>  |  <span data-ttu-id="55bcb-241">0</span><span class="sxs-lookup"><span data-stu-id="55bcb-241">0</span></span>  |  <span data-ttu-id="55bcb-242">设置历史帧数用于视频防抖动。</span><span class="sxs-lookup"><span data-stu-id="55bcb-242">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="55bcb-243">0 为 0 的延迟和几乎"免费"从能力和性能的角度来看。</span><span class="sxs-lookup"><span data-stu-id="55bcb-243">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="55bcb-244">15 （但代价是 15 帧的滞后时间和内存） 的最高质量的建议。</span><span class="sxs-lookup"><span data-stu-id="55bcb-244">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="55bcb-245">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="55bcb-245">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="55bcb-246">浮点数</span><span class="sxs-lookup"><span data-stu-id="55bcb-246">float</span></span>  |  <span data-ttu-id="55bcb-247">0.9 (HoloLens) 1.0 （沉浸式头戴式）</span><span class="sxs-lookup"><span data-stu-id="55bcb-247">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="55bcb-248">全局不透明度系数的全息图中设置范围从 0.0 （完全透明） 到 1.0 （完全不透明）。</span><span class="sxs-lookup"><span data-stu-id="55bcb-248">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="55bcb-249">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="55bcb-249">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="55bcb-250">boolean</span><span class="sxs-lookup"><span data-stu-id="55bcb-250">boolean</span></span>  |  <span data-ttu-id="55bcb-251">FALSE</span><span class="sxs-lookup"><span data-stu-id="55bcb-251">FALSE</span></span>  |  <span data-ttu-id="55bcb-252">一个标志，用于启用或禁用 2d 的 UWP 应用显示受保护的内容是否返回一个空框架。</span><span class="sxs-lookup"><span data-stu-id="55bcb-252">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="55bcb-253">此标志为 false 和 2d UWP 应用时显示受保护的内容，2d 的 UWP 应用将替换为受保护内容纹理，这两个耳机和混合的现实捕获中。</span><span class="sxs-lookup"><span data-stu-id="55bcb-253">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="55bcb-254">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="55bcb-254">ShowHiddenMesh</span></span>  |  <span data-ttu-id="55bcb-255">boolean</span><span class="sxs-lookup"><span data-stu-id="55bcb-255">boolean</span></span>  |  <span data-ttu-id="55bcb-256">FALSE</span><span class="sxs-lookup"><span data-stu-id="55bcb-256">FALSE</span></span>  |  <span data-ttu-id="55bcb-257">若要启用或禁用显示 holographic 照相机的隐藏的区域网格和相邻内容的标记。</span><span class="sxs-lookup"><span data-stu-id="55bcb-257">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="55bcb-258">OutputSize</span><span class="sxs-lookup"><span data-stu-id="55bcb-258">OutputSize</span></span> | <span data-ttu-id="55bcb-259">Size</span><span class="sxs-lookup"><span data-stu-id="55bcb-259">Size</span></span> | <span data-ttu-id="55bcb-260">0, 0</span><span class="sxs-lookup"><span data-stu-id="55bcb-260">0, 0</span></span> | <span data-ttu-id="55bcb-261">有关视频防抖动裁剪后设置相应的输出大小。</span><span class="sxs-lookup"><span data-stu-id="55bcb-261">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="55bcb-262">如果指定 0 或无效的输出大小，则，选择默认裁剪大小。</span><span class="sxs-lookup"><span data-stu-id="55bcb-262">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="55bcb-263">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="55bcb-263">PreferredHologramPerspective</span></span> | <span data-ttu-id="55bcb-264">UINT32</span><span class="sxs-lookup"><span data-stu-id="55bcb-264">UINT32</span></span> | <span data-ttu-id="55bcb-265">1 (PhotoVideoCamera)</span><span class="sxs-lookup"><span data-stu-id="55bcb-265">1 (PhotoVideoCamera)</span></span> | <span data-ttu-id="55bcb-266">枚举用于指示应捕获哪 holographic 照相机查看配置。</span><span class="sxs-lookup"><span data-stu-id="55bcb-266">Enum used to indicate which holographic camera view configuration should be captured.</span></span> <span data-ttu-id="55bcb-267">设置应用程序将不会要求从照片/视频照相机呈现的 0 （显示） 表示</span><span class="sxs-lookup"><span data-stu-id="55bcb-267">Setting 0 (Display) means that the app won't be asked to render from the photo/video camera</span></span> |

<span data-ttu-id="55bcb-268">MRC 音频效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="55bcb-268">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="55bcb-269">属性名</span><span class="sxs-lookup"><span data-stu-id="55bcb-269">Property Name</span></span></th>
<th><span data-ttu-id="55bcb-270">type</span><span class="sxs-lookup"><span data-stu-id="55bcb-270">Type</span></span></th>
<th><span data-ttu-id="55bcb-271">Default Value</span><span class="sxs-lookup"><span data-stu-id="55bcb-271">Default Value</span></span></th>
<th><span data-ttu-id="55bcb-272">描述</span><span class="sxs-lookup"><span data-stu-id="55bcb-272">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="55bcb-273">MixerMode</span><span class="sxs-lookup"><span data-stu-id="55bcb-273">MixerMode</span></span></td>
<td><span data-ttu-id="55bcb-274">UINT32</span><span class="sxs-lookup"><span data-stu-id="55bcb-274">UINT32</span></span></td>
<td><span data-ttu-id="55bcb-275">2</span><span class="sxs-lookup"><span data-stu-id="55bcb-275">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="55bcb-276">0 :仅限 mic 音频</span><span class="sxs-lookup"><span data-stu-id="55bcb-276">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="55bcb-277">1 :仅系统音频</span><span class="sxs-lookup"><span data-stu-id="55bcb-277">1 : System audio only</span></span></li>
<li><span data-ttu-id="55bcb-278">2 :Mic 和系统音频</span><span class="sxs-lookup"><span data-stu-id="55bcb-278">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="55bcb-279">同时 MRC 限制</span><span class="sxs-lookup"><span data-stu-id="55bcb-279">Simultaneous MRC limitations</span></span>

<span data-ttu-id="55bcb-280">有多个应用在同一时间访问 MRC 方面的某些限制。</span><span class="sxs-lookup"><span data-stu-id="55bcb-280">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="55bcb-281">照片/视频照相机访问</span><span class="sxs-lookup"><span data-stu-id="55bcb-281">Photo/video camera access</span></span>

<span data-ttu-id="55bcb-282">照片/视频摄像机被限制为可以在同一时间访问它的进程数。</span><span class="sxs-lookup"><span data-stu-id="55bcb-282">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="55bcb-283">而在录制过程将失败视频或任何其他进程拍照获取照片/视频摄像机。</span><span class="sxs-lookup"><span data-stu-id="55bcb-283">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="55bcb-284">（适用于混合现实捕获和标准照片/视频捕获）</span><span class="sxs-lookup"><span data-stu-id="55bcb-284">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="55bcb-285">HoloLens 2 应用程序可以使用 MediaCaptureInitializationSettings 的[SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)属性以指示他们想要运行 SharedReadOnly，如果它们不需要照片/视频摄像机的独有控制。</span><span class="sxs-lookup"><span data-stu-id="55bcb-285">With HoloLens 2, an app can use MediaCaptureInitializationSettings's [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) property to indicate that they want to run SharedReadOnly if they don't need exclusive control over the photo/video camera.</span></span> <span data-ttu-id="55bcb-286">解析和捕获的帧速率为这样做意味着将限制为其他应用已配置的内容提供照相机。</span><span class="sxs-lookup"><span data-stu-id="55bcb-286">Doing so means the resolution and framerate of the capture will be limited to what other apps have configured the camera to provide.</span></span>

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="55bcb-287">内置 MRC 照片/视频照相机访问</span><span class="sxs-lookup"><span data-stu-id="55bcb-287">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="55bcb-288">MRC 功能内置于 Windows 10 （通过 Cortana，开始菜单，硬件快捷方式，Miracast、 Windows Device Portal）：</span><span class="sxs-lookup"><span data-stu-id="55bcb-288">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>
* <span data-ttu-id="55bcb-289">默认情况下将使用 ExclusiveControl 运行</span><span class="sxs-lookup"><span data-stu-id="55bcb-289">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="55bcb-290">但是，支持已添加到每个子系统在共享模式下操作：</span><span class="sxs-lookup"><span data-stu-id="55bcb-290">However, support has been added to each subsystem to operate in a shared mode:</span></span>
* <span data-ttu-id="55bcb-291">如果应用程序请求 ExclusiveControl 访问照片/视频摄像机，内置 MRC 将自动停止使用照片/视频摄像机，因此应用程序的请求将成功</span><span class="sxs-lookup"><span data-stu-id="55bcb-291">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span>
* <span data-ttu-id="55bcb-292">如果内置 MRC 已启动时应用具有 ExclusiveControl，内置 MRC 将在 SharedReadOnly 模式下运行</span><span class="sxs-lookup"><span data-stu-id="55bcb-292">If built-in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span>

<span data-ttu-id="55bcb-293">此共享的模式功能具有某些限制：</span><span class="sxs-lookup"><span data-stu-id="55bcb-293">This shared mode functionality has certain restrictions:</span></span>
* <span data-ttu-id="55bcb-294">通过 Cortana、 硬件快捷方式或开始菜单的照片：需要 Windows 10 2018 年 4 月更新 （或更高版本）</span><span class="sxs-lookup"><span data-stu-id="55bcb-294">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="55bcb-295">通过 Cortana、 硬件快捷方式或开始菜单的视频：需要 Windows 10 2018 年 4 月更新 （或更高版本）</span><span class="sxs-lookup"><span data-stu-id="55bcb-295">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="55bcb-296">通过支持 Miracast 的流式处理 MRC:需要 Windows 10 2018 年 10 月更新 （或更高版本）</span><span class="sxs-lookup"><span data-stu-id="55bcb-296">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="55bcb-297">通过 Windows Device Portal 或通过 HoloLens 辅助应用程序，流式处理 MRC:需要 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="55bcb-297">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="55bcb-298">另一个应用使用照片/视频照相机时，可能通过其正常值降低分辨率和帧速率的内置 MRC 相机 UI。</span><span class="sxs-lookup"><span data-stu-id="55bcb-298">The resolution and framerate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="55bcb-299">MRC 访问</span><span class="sxs-lookup"><span data-stu-id="55bcb-299">MRC access</span></span>

<span data-ttu-id="55bcb-300">使用 Windows 10 2018 年 4 月更新，不再有多个应用程序访问 （但是，对照片/视频摄像机的访问权限仍有一些局限性） MRC 流周围的限制。</span><span class="sxs-lookup"><span data-stu-id="55bcb-300">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="55bcb-301">先前的 windows 10 2018 年 4 月更新，应用程序的自定义 MRC 记录器的互斥与系统 MRC （拍摄照片、 捕获视频，或从 Windows Device Portal 流式处理）。</span><span class="sxs-lookup"><span data-stu-id="55bcb-301">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="55bcb-302">请参阅</span><span class="sxs-lookup"><span data-stu-id="55bcb-302">See also</span></span>
* [<span data-ttu-id="55bcb-303">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="55bcb-303">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="55bcb-304">旁观视图</span><span class="sxs-lookup"><span data-stu-id="55bcb-304">Spectator view</span></span>](spectator-view.md)
