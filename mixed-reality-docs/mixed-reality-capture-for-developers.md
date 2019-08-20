---
title: 面向开发人员的混合现实捕获
description: 适用于开发人员的混合现实捕获的最佳实践。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、照片、视频、捕获、照相机
ms.openlocfilehash: 740b02dd1714679028541a888d721ae74e8e1f32
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937074"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="250a8-104">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="250a8-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="250a8-105">有关适用于 HoloLens 2 的新 MRC 功能的指南, 请参阅下面[的 PV 相机中的 Render](#render-from-the-pv-camera-opt-in) 。</span><span class="sxs-lookup"><span data-stu-id="250a8-105">See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="250a8-106">由于用户随时都可以使用[混合现实捕获](mixed-reality-capture.md)(MRC) 照片或视频, 因此, 在开发应用程序时, 需要记住几个事项。</span><span class="sxs-lookup"><span data-stu-id="250a8-106">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="250a8-107">这包括在捕获 MRCs 时, 可用于 MRC 视觉质量并响应系统更改的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="250a8-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="250a8-108">开发人员还可以将混合现实捕获和插入无缝集成到其应用中。</span><span class="sxs-lookup"><span data-stu-id="250a8-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="250a8-109">HoloLens 上的 MRC (第一代) 支持最多720p 的视频和照片, 而在 HoloLens 2 上的 MRC 支持最大为1080p 和最大分辨率为4K 的视频。</span><span class="sxs-lookup"><span data-stu-id="250a8-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="250a8-110">质量 MRC 的重要性</span><span class="sxs-lookup"><span data-stu-id="250a8-110">The importance of quality MRC</span></span>

<span data-ttu-id="250a8-111">混合现实捕获的照片和视频可能是用户对你的应用程序的第一次曝光。</span><span class="sxs-lookup"><span data-stu-id="250a8-111">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="250a8-112">是否在 Microsoft Store 页面上或从其他用户共享社交网络上的 MRCs 混合现实屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="250a8-112">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="250a8-113">您可以使用 MRC 来演示您的应用程序、培训用户、鼓励用户共享其混合世界交互, 以及进行用户研究和解决问题。</span><span class="sxs-lookup"><span data-stu-id="250a8-113">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="250a8-114">MRC 如何影响你的应用</span><span class="sxs-lookup"><span data-stu-id="250a8-114">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="250a8-115">在应用程序中启用 MRC</span><span class="sxs-lookup"><span data-stu-id="250a8-115">Enabling MRC in your app</span></span>

<span data-ttu-id="250a8-116">默认情况下, 应用程序无需执行任何操作即可使用户接受混合的现实捕获。</span><span class="sxs-lookup"><span data-stu-id="250a8-116">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="250a8-117">在应用中为 MRC 启用改进的对齐方式</span><span class="sxs-lookup"><span data-stu-id="250a8-117">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="250a8-118">默认情况下, 混合现实捕获结合了正确的眼睛和照片/视频 (PV) 相机。</span><span class="sxs-lookup"><span data-stu-id="250a8-118">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="250a8-119">这两个源使用当前运行的沉浸式应用设置的焦点组合在一起。</span><span class="sxs-lookup"><span data-stu-id="250a8-119">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="250a8-120">这意味着, 在焦点平面外的全息影像也不会对齐 (因为 PV 相机和右显示之间的物理距离)。</span><span class="sxs-lookup"><span data-stu-id="250a8-120">This means that holograms outside the focus plane won't align as well (due to the physical distance between the PV camera and the right display).</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="250a8-121">设置焦点</span><span class="sxs-lookup"><span data-stu-id="250a8-121">Set the focus point</span></span>

<span data-ttu-id="250a8-122">沉浸式应用 (在 HoloLens 上) 应将[焦点](focus-point-in-unity.md)设置为要将其稳定平面置于何处。</span><span class="sxs-lookup"><span data-stu-id="250a8-122">Immersive apps (on HoloLens) should set the [focus point](focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="250a8-123">这确保了耳机和混合现实捕获中的最佳对齐。</span><span class="sxs-lookup"><span data-stu-id="250a8-123">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="250a8-124">如果未设置焦点, 则 "稳定" 平面将默认为两米。</span><span class="sxs-lookup"><span data-stu-id="250a8-124">If a focus point is not set, the stabilization plane will default to two meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="250a8-125">从 PV 相机呈现 (选择加入)</span><span class="sxs-lookup"><span data-stu-id="250a8-125">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="250a8-126">HoloLens 2 添加了一种功能, 使沉浸式应用能够在混合现实捕获运行时**从 PV 摄像机进行呈现**。</span><span class="sxs-lookup"><span data-stu-id="250a8-126">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="250a8-127">若要确保应用正确支持其他呈现, 应用必须选择启用此功能。</span><span class="sxs-lookup"><span data-stu-id="250a8-127">To ensure the app supports the additional render correctly, the app has to opt-in to this functionality.</span></span>

<span data-ttu-id="250a8-128">PV 相机中的呈现功能与默认的 MRC 体验相比具有以下改进:</span><span class="sxs-lookup"><span data-stu-id="250a8-128">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="250a8-129">与您的物理环境和手之间 (几乎交互) 的全息图对齐方式应始终精确, 而不是相对于在默认 MRC 中可能看到的距离以外的距离。</span><span class="sxs-lookup"><span data-stu-id="250a8-129">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="250a8-130">头戴式耳机不会受到影响, 因为它不会用于呈现 MRC 输出的全息影像。</span><span class="sxs-lookup"><span data-stu-id="250a8-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="250a8-131">可以通过以下三个步骤, 通过 PV 相机实现呈现:</span><span class="sxs-lookup"><span data-stu-id="250a8-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="250a8-132">启用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="250a8-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="250a8-133">处理附加的 HolographicCamera 呈现</span><span class="sxs-lookup"><span data-stu-id="250a8-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="250a8-134">通过此附加 HolographicCamera 正确验证着色器和代码呈现</span><span class="sxs-lookup"><span data-stu-id="250a8-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a><span data-ttu-id="250a8-135">启用 PhotoVideoCamera HolographicViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="250a8-135">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>

<span data-ttu-id="250a8-136">若要选择加入, 应用只需启用 PhotoVideoCamera 的[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span><span class="sxs-lookup"><span data-stu-id="250a8-136">To opt-in, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="250a8-137">在 DirectX 中处理附加的 HolographicCamera 呈现</span><span class="sxs-lookup"><span data-stu-id="250a8-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="250a8-138">当应用程序有选择地从 PV 相机进行呈现且混合现实捕获开始时:</span><span class="sxs-lookup"><span data-stu-id="250a8-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="250a8-139">HolographicSpace 的 CameraAdded 事件将激发。</span><span class="sxs-lookup"><span data-stu-id="250a8-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="250a8-140">如果此时应用无法处理照相机, 此事件可能会延迟。</span><span class="sxs-lookup"><span data-stu-id="250a8-140">This event can be deferred if the app cannot handle the camera at this time.</span></span>
2. <span data-ttu-id="250a8-141">事件完成后 (没有未完成的延迟), HolographicCamera 将在下一个 HolographicFrame 的 AddedCameras 列表中显示。</span><span class="sxs-lookup"><span data-stu-id="250a8-141">Once the event has completed (and there are no outstanding deferrals) the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="250a8-142">当混合现实捕获停止时 (或应用在混合现实捕获正在运行时禁用视图配置): HolographicCamera 将显示在下一个 HolographicFrame 的 RemovedCameras 列表中, HolographicSpace 的 CameraRemoved 事件将火灾.</span><span class="sxs-lookup"><span data-stu-id="250a8-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="250a8-143">已将[ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)属性添加到 HolographicCamera, 以帮助标识相机所属的配置。</span><span class="sxs-lookup"><span data-stu-id="250a8-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="250a8-144">处理 Unity 中的其他 HolographicCamera 呈现</span><span class="sxs-lookup"><span data-stu-id="250a8-144">Handle the additional HolographicCamera render in Unity</span></span>

>[!NOTE]
> <span data-ttu-id="250a8-145">通过 PV 相机呈现的 Unity 支持正在开发中, 但尚不能使用。</span><span class="sxs-lookup"><span data-stu-id="250a8-145">Unity support to render from the PV camera is under development and can't be used, yet.</span></span> <span data-ttu-id="250a8-146">当提供支持从 PV 相机呈现的 Unity 时, 将更新此文档。</span><span class="sxs-lookup"><span data-stu-id="250a8-146">This documentation will be updated when a build of Unity with support for rendering from the PV camera is available.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="250a8-147">验证着色器和代码支持其他相机</span><span class="sxs-lookup"><span data-stu-id="250a8-147">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="250a8-148">运行混合现实捕获, 并检查是否存在异常对齐、缺少内容或性能问题。</span><span class="sxs-lookup"><span data-stu-id="250a8-148">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="250a8-149">根据需要更新着色器和代码。</span><span class="sxs-lookup"><span data-stu-id="250a8-149">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="250a8-150">如果某些场景无法支持向其他相机进行呈现, 则可以在 PhotoVideoCamera 的 HolographicViewConfiguration 中禁用它。</span><span class="sxs-lookup"><span data-stu-id="250a8-150">If there are certain scenes that cannot support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration during them.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="250a8-151">在应用中禁用 MRC</span><span class="sxs-lookup"><span data-stu-id="250a8-151">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="250a8-152">2D 应用</span><span class="sxs-lookup"><span data-stu-id="250a8-152">2D app</span></span>

<span data-ttu-id="250a8-153">当混合现实捕获正在运行时, 2D 应用可以选择使其视觉内容遮盖:</span><span class="sxs-lookup"><span data-stu-id="250a8-153">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="250a8-154">与[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)标志一起提供</span><span class="sxs-lookup"><span data-stu-id="250a8-154">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="250a8-155">用[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)标志创建应用的交换链</span><span class="sxs-lookup"><span data-stu-id="250a8-155">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="250a8-156">对于 Windows 10 2019 更新, 设置 w 的[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span><span class="sxs-lookup"><span data-stu-id="250a8-156">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="250a8-157">沉浸式应用</span><span class="sxs-lookup"><span data-stu-id="250a8-157">Immersive app</span></span>

<span data-ttu-id="250a8-158">沉浸式应用可通过以下方式选择将其视觉内容从混合现实捕获中排除:</span><span class="sxs-lookup"><span data-stu-id="250a8-158">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="250a8-159">设置 HolographicCameraRenderingParameter 的[IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)以禁用其关联帧的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="250a8-159">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="250a8-160">将 HolographicCamera 的[IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)设置为对其关联的全息相机禁用混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="250a8-160">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="250a8-161">密码键盘</span><span class="sxs-lookup"><span data-stu-id="250a8-161">Password Keyboard</span></span>

<span data-ttu-id="250a8-162">使用 Windows 10 的2019更新可能会在密码或 pin 键盘可见时, 自动从混合现实捕获中排除可视内容。</span><span class="sxs-lookup"><span data-stu-id="250a8-162">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="250a8-163">了解 MRC 何时处于活动状态</span><span class="sxs-lookup"><span data-stu-id="250a8-163">Knowing when MRC is active</span></span>

<span data-ttu-id="250a8-164">应用程序可以使用[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)类来了解系统混合现实捕获的运行时间 (对于音频或视频)。</span><span class="sxs-lookup"><span data-stu-id="250a8-164">The [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="250a8-165">如果混合现实捕获在设备上不可用, 则 AppCapture 的[GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可以返回 null。</span><span class="sxs-lookup"><span data-stu-id="250a8-165">AppCapture's [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="250a8-166">在应用暂停时取消注册 CapturingChanged 事件也很重要, 否则可能会进入 "已阻止" 状态。</span><span class="sxs-lookup"><span data-stu-id="250a8-166">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="250a8-167">最佳做法 (特定于 HoloLens)</span><span class="sxs-lookup"><span data-stu-id="250a8-167">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="250a8-168">对于开发人员而言, MRC 应该无需额外工作就能正常运行, 但需要注意一些事项, 以便为应用提供最佳混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="250a8-168">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="250a8-169">**MRC 使用全息图的 alpha 通道与[相机](locatable-camera.md)图像混合**</span><span class="sxs-lookup"><span data-stu-id="250a8-169">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="250a8-170">最重要的步骤是确保您的应用程序清除为透明黑色, 而不是清除为不透明的黑色。</span><span class="sxs-lookup"><span data-stu-id="250a8-170">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="250a8-171">在 Unity 中, 这是默认情况下通过 MixedRealityToolkit 完成的, 但是如果是在非 Unity 中进行开发, 则可能需要更改一行。</span><span class="sxs-lookup"><span data-stu-id="250a8-171">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="250a8-172">如果你的应用未清除透明黑色, 以下是你可能会在 MRC 中看到的一些项目:</span><span class="sxs-lookup"><span data-stu-id="250a8-172">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="250a8-173">**示例失败**:内容周围的黑色边缘 (未能清除为透明黑色)</span><span class="sxs-lookup"><span data-stu-id="250a8-173">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

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

<span data-ttu-id="250a8-174">**示例失败**:全息图的整个背景场景显示为黑色。</span><span class="sxs-lookup"><span data-stu-id="250a8-174">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="250a8-175">将背景 alpha 值设置为1会导致黑色背景</span><span class="sxs-lookup"><span data-stu-id="250a8-175">Setting a background alpha value of 1 results in a black background</span></span>

![将背景 alpha 值设置为1会导致黑色背景](images/clearopaqueblack-300px.png)

<span data-ttu-id="250a8-177">**预期结果**:全息影像与真实世界一起正确地混合 (如果清除为透明黑色, 则预期结果)</span><span class="sxs-lookup"><span data-stu-id="250a8-177">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![清除为透明黑色时的预期结果](images/cleartransparentblack-300px.png)

<span data-ttu-id="250a8-179">**解决方案**：</span><span class="sxs-lookup"><span data-stu-id="250a8-179">**Solution**:</span></span>
* <span data-ttu-id="250a8-180">将显示为不透明黑色的任何内容更改为 alpha 值0。</span><span class="sxs-lookup"><span data-stu-id="250a8-180">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="250a8-181">确保应用清除为透明黑色。</span><span class="sxs-lookup"><span data-stu-id="250a8-181">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="250a8-182">Unity 默认为明文以使用 MixedRealityToolkit 自动清除, 但如果它是非 Unity 应用, 应修改与 ID3D11DeiceContext:: ClearRenderTargetView () 一起使用的颜色。</span><span class="sxs-lookup"><span data-stu-id="250a8-182">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="250a8-183">你需要确保清除透明黑色 (0, 0, 0, 0), 而不是透明的黑色 (0, 0, 0, 1)。</span><span class="sxs-lookup"><span data-stu-id="250a8-183">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="250a8-184">你现在可以根据需要调整资产的 alpha 值, 但通常不需要这样做。</span><span class="sxs-lookup"><span data-stu-id="250a8-184">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="250a8-185">大多数情况下, MRCs 将看起来不错。</span><span class="sxs-lookup"><span data-stu-id="250a8-185">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="250a8-186">MRC 假设预乘 alpha。</span><span class="sxs-lookup"><span data-stu-id="250a8-186">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="250a8-187">Alpha 值仅影响 MRC 捕获。</span><span class="sxs-lookup"><span data-stu-id="250a8-187">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="250a8-188">在 HoloLens 上启用了 MRC 时应发生的情况</span><span class="sxs-lookup"><span data-stu-id="250a8-188">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="250a8-189">以下各项适用于 HoloLens (第一代) 和 HoloLens 2, 除非另有说明:</span><span class="sxs-lookup"><span data-stu-id="250a8-189">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="250a8-190">系统会将应用程序限制为30Hz 呈现。</span><span class="sxs-lookup"><span data-stu-id="250a8-190">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="250a8-191">这会为 MRC 创建一些空间, 使应用无需保留固定预算预留, 同时还可与30fps</span><span class="sxs-lookup"><span data-stu-id="250a8-191">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="250a8-192">录制/流式处理 MRC 时, 在设备上看到的全息图内容可能显示为 "火花": 文本可能会变得更难以阅读, 而全息图边缘可能会更 jaggy (选择加入到**HoloLens 2**上的第三个照相机渲染可避免这种损害)</span><span class="sxs-lookup"><span data-stu-id="250a8-192">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="250a8-193">当应用程序启用了应用程序时, MRC 照片和视频将遵循应用程序的[重点点](focus-point-in-unity.md), 这将有助于确保全息影像精确定位。</span><span class="sxs-lookup"><span data-stu-id="250a8-193">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="250a8-194">对于视频, 重点是平滑的, 因此, 如果焦点深度发生变化, 全息影像可能会慢慢地发生缓慢偏移。</span><span class="sxs-lookup"><span data-stu-id="250a8-194">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="250a8-195">以不同于焦点的深度显示的全息影像可能与现实世界的偏移量相同 (请参阅下面的示例, 重点点设置为2米, 而全息图位于1米)。</span><span class="sxs-lookup"><span data-stu-id="250a8-195">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![2米的全息影像会完全注册到世界。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="250a8-198">在应用中集成 MRC 功能</span><span class="sxs-lookup"><span data-stu-id="250a8-198">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="250a8-199">混合现实应用可以从应用内启动 MRC 照片或视频捕获, 而捕获的内容将在应用中提供, 而不会存储到设备的 "照相机"。</span><span class="sxs-lookup"><span data-stu-id="250a8-199">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="250a8-200">您可以创建自定义的 MRC 记录器或利用内置的相机捕获 UI。</span><span class="sxs-lookup"><span data-stu-id="250a8-200">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="250a8-201">带有内置照相机 UI 的 MRC</span><span class="sxs-lookup"><span data-stu-id="250a8-201">MRC with built-in camera UI</span></span>

<span data-ttu-id="250a8-202">开发人员可以使用 *[摄像头捕获 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 若要获取用户捕获混合的现实照片或视频只需几行代码。</span><span class="sxs-lookup"><span data-stu-id="250a8-202">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="250a8-203">此 API 启动内置的 MRC 相机 UI, 用户可以从中拍摄照片或视频, 并将生成的捕获返回到应用。</span><span class="sxs-lookup"><span data-stu-id="250a8-203">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="250a8-204">如果你想要创建自己的照相机 UI, 或者需要对捕获流进行较低级别的访问, 则可以创建自定义混合现实记录。</span><span class="sxs-lookup"><span data-stu-id="250a8-204">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="250a8-205">创建自定义 MRC 记录器</span><span class="sxs-lookup"><span data-stu-id="250a8-205">Creating a custom MRC recorder</span></span>

<span data-ttu-id="250a8-206">尽管用户可以始终使用系统 MRC 捕获服务来触发照片或视频, 但应用程序可能需要构建自定义相机应用程序, 但在照相机流中包含全息影像, 就像 MRC 一样。</span><span class="sxs-lookup"><span data-stu-id="250a8-206">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="250a8-207">这允许应用程序代表用户启动捕获、生成自定义录制 UI, 或自定义 MRC 设置以命名几个示例。</span><span class="sxs-lookup"><span data-stu-id="250a8-207">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="250a8-208">**HoloStudio 使用 MRC 效果添加自定义 MRC 相机**</span><span class="sxs-lookup"><span data-stu-id="250a8-208">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio 使用 MRC 效果添加自定义 MRC 相机](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="250a8-210">Unity 应用程序应查看属性的[Locatable_camera_in_Unity](locatable-camera-in-unity.md)以启用全息影像。</span><span class="sxs-lookup"><span data-stu-id="250a8-210">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="250a8-211">其他应用程序可以通过使用[Windows 媒体捕获 api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)控制相机并添加 MRC 视频和音频效果来包括静止图像和视频中的虚拟全息影像和应用程序音频, 来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="250a8-211">Other applications can do this by using the [Windows Media Capture APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="250a8-212">应用程序有两个选项可添加效果:</span><span class="sxs-lookup"><span data-stu-id="250a8-212">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="250a8-213">旧的 API:[MediaCapture. AddEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="250a8-213">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="250a8-214">新的 Microsoft 推荐 API (返回对象, 使其可以操作动态属性):需要应用程序创建其自己的[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)实现的 [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync)。</span><span class="sxs-lookup"><span data-stu-id="250a8-214">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="250a8-215">有关示例用法, 请参阅 MRC 效果示例。</span><span class="sxs-lookup"><span data-stu-id="250a8-215">Please see the MRC effect sample for sample usage.</span></span>

>[!NOTE]
> <span data-ttu-id="250a8-216">Visual Studio 将无法识别 MixedRealityCapture 命名空间, 但字符串仍然有效。</span><span class="sxs-lookup"><span data-stu-id="250a8-216">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="250a8-217">MRC 视频效果 (**MixedRealityCapture. MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="250a8-217">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="250a8-218">属性名</span><span class="sxs-lookup"><span data-stu-id="250a8-218">Property Name</span></span>  |  <span data-ttu-id="250a8-219">type</span><span class="sxs-lookup"><span data-stu-id="250a8-219">Type</span></span>  |  <span data-ttu-id="250a8-220">Default Value</span><span class="sxs-lookup"><span data-stu-id="250a8-220">Default Value</span></span>  |  <span data-ttu-id="250a8-221">描述</span><span class="sxs-lookup"><span data-stu-id="250a8-221">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="250a8-222">StreamType</span><span class="sxs-lookup"><span data-stu-id="250a8-222">StreamType</span></span>  |  <span data-ttu-id="250a8-223">UINT32 ([mediastreamtype.video](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span><span class="sxs-lookup"><span data-stu-id="250a8-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="250a8-224">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="250a8-224">1 (VideoRecord)</span></span>  |  <span data-ttu-id="250a8-225">描述此影响所使用的捕获流。</span><span class="sxs-lookup"><span data-stu-id="250a8-225">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="250a8-226">音频不可用。</span><span class="sxs-lookup"><span data-stu-id="250a8-226">Audio is not available.</span></span> | 
|  <span data-ttu-id="250a8-227">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="250a8-227">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="250a8-228">boolean</span><span class="sxs-lookup"><span data-stu-id="250a8-228">boolean</span></span>  |  <span data-ttu-id="250a8-229">TRUE</span><span class="sxs-lookup"><span data-stu-id="250a8-229">TRUE</span></span>  |  <span data-ttu-id="250a8-230">用于在视频捕获中启用或禁用全息影像的标志。</span><span class="sxs-lookup"><span data-stu-id="250a8-230">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="250a8-231">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="250a8-231">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="250a8-232">boolean</span><span class="sxs-lookup"><span data-stu-id="250a8-232">boolean</span></span>  |  <span data-ttu-id="250a8-233">TRUE</span><span class="sxs-lookup"><span data-stu-id="250a8-233">TRUE</span></span>  |  <span data-ttu-id="250a8-234">用于在全息影像捕获期间启用或禁用录制指示器的标志。</span><span class="sxs-lookup"><span data-stu-id="250a8-234">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="250a8-235">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="250a8-235">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="250a8-236">boolean</span><span class="sxs-lookup"><span data-stu-id="250a8-236">boolean</span></span>  |  <span data-ttu-id="250a8-237">FALSE</span><span class="sxs-lookup"><span data-stu-id="250a8-237">FALSE</span></span>  |  <span data-ttu-id="250a8-238">用于启用或禁用由 HoloLens 跟踪器支持的视频稳定的标志。</span><span class="sxs-lookup"><span data-stu-id="250a8-238">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="250a8-239">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="250a8-239">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="250a8-240">UINT32</span><span class="sxs-lookup"><span data-stu-id="250a8-240">UINT32</span></span>  |  <span data-ttu-id="250a8-241">0</span><span class="sxs-lookup"><span data-stu-id="250a8-241">0</span></span>  |  <span data-ttu-id="250a8-242">设置视频抖动使用的历史帧数。</span><span class="sxs-lookup"><span data-stu-id="250a8-242">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="250a8-243">从电源和性能的角度来看, 0 从0到延迟, 几乎是 "免费"。</span><span class="sxs-lookup"><span data-stu-id="250a8-243">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="250a8-244">对于最高质量, 建议使用15个 (成本为延迟和内存15帧)。</span><span class="sxs-lookup"><span data-stu-id="250a8-244">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="250a8-245">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="250a8-245">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="250a8-246">浮点数</span><span class="sxs-lookup"><span data-stu-id="250a8-246">float</span></span>  |  <span data-ttu-id="250a8-247">0.9 (HoloLens) 1.0 (沉浸式耳机)</span><span class="sxs-lookup"><span data-stu-id="250a8-247">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="250a8-248">将范围从 0.0 (完全透明) 到1.0 的全局不透明度系数设置为 "完全不透明"。</span><span class="sxs-lookup"><span data-stu-id="250a8-248">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="250a8-249">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="250a8-249">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="250a8-250">boolean</span><span class="sxs-lookup"><span data-stu-id="250a8-250">boolean</span></span>  |  <span data-ttu-id="250a8-251">FALSE</span><span class="sxs-lookup"><span data-stu-id="250a8-251">FALSE</span></span>  |  <span data-ttu-id="250a8-252">用于启用或禁用在有显示受保护内容的 2d UWP 应用时返回空帧的标志。</span><span class="sxs-lookup"><span data-stu-id="250a8-252">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="250a8-253">如果此标志为 false, 并且二维 UWP 应用显示受保护的内容, 则在耳机和混合现实捕获中, 二维 UWP 应用将替换为受保护的内容纹理。</span><span class="sxs-lookup"><span data-stu-id="250a8-253">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="250a8-254">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="250a8-254">ShowHiddenMesh</span></span>  |  <span data-ttu-id="250a8-255">boolean</span><span class="sxs-lookup"><span data-stu-id="250a8-255">boolean</span></span>  |  <span data-ttu-id="250a8-256">FALSE</span><span class="sxs-lookup"><span data-stu-id="250a8-256">FALSE</span></span>  |  <span data-ttu-id="250a8-257">用于启用或禁用显示全息相机隐藏区域网格和相邻内容的标志。</span><span class="sxs-lookup"><span data-stu-id="250a8-257">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="250a8-258">OutputSize</span><span class="sxs-lookup"><span data-stu-id="250a8-258">OutputSize</span></span> | <span data-ttu-id="250a8-259">Size</span><span class="sxs-lookup"><span data-stu-id="250a8-259">Size</span></span> | <span data-ttu-id="250a8-260">0, 0</span><span class="sxs-lookup"><span data-stu-id="250a8-260">0, 0</span></span> | <span data-ttu-id="250a8-261">在裁剪视频稳定性后设置所需的输出大小。</span><span class="sxs-lookup"><span data-stu-id="250a8-261">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="250a8-262">如果指定了0或指定了无效的输出大小, 则选择默认裁剪大小。</span><span class="sxs-lookup"><span data-stu-id="250a8-262">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="250a8-263">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="250a8-263">PreferredHologramPerspective</span></span> | <span data-ttu-id="250a8-264">UINT32</span><span class="sxs-lookup"><span data-stu-id="250a8-264">UINT32</span></span> | <span data-ttu-id="250a8-265">1 (PhotoVideoCamera)</span><span class="sxs-lookup"><span data-stu-id="250a8-265">1 (PhotoVideoCamera)</span></span> | <span data-ttu-id="250a8-266">枚举, 用于指示应捕获的全息相机视图配置。</span><span class="sxs-lookup"><span data-stu-id="250a8-266">Enum used to indicate which holographic camera view configuration should be captured.</span></span> <span data-ttu-id="250a8-267">设置 0 (显示) 表示不要求应用从照片/视频相机进行呈现</span><span class="sxs-lookup"><span data-stu-id="250a8-267">Setting 0 (Display) means that the app won't be asked to render from the photo/video camera</span></span> |

<span data-ttu-id="250a8-268">MRC 音频效果 (**MixedRealityCapture. MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="250a8-268">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="250a8-269">属性名</span><span class="sxs-lookup"><span data-stu-id="250a8-269">Property Name</span></span></th>
<th><span data-ttu-id="250a8-270">type</span><span class="sxs-lookup"><span data-stu-id="250a8-270">Type</span></span></th>
<th><span data-ttu-id="250a8-271">Default Value</span><span class="sxs-lookup"><span data-stu-id="250a8-271">Default Value</span></span></th>
<th><span data-ttu-id="250a8-272">描述</span><span class="sxs-lookup"><span data-stu-id="250a8-272">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="250a8-273">MixerMode</span><span class="sxs-lookup"><span data-stu-id="250a8-273">MixerMode</span></span></td>
<td><span data-ttu-id="250a8-274">UINT32</span><span class="sxs-lookup"><span data-stu-id="250a8-274">UINT32</span></span></td>
<td><span data-ttu-id="250a8-275">2</span><span class="sxs-lookup"><span data-stu-id="250a8-275">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="250a8-276">0仅 Mic 音频</span><span class="sxs-lookup"><span data-stu-id="250a8-276">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="250a8-277">2仅限系统音频</span><span class="sxs-lookup"><span data-stu-id="250a8-277">1 : System audio only</span></span></li>
<li><span data-ttu-id="250a8-278">pps-2Mic 和系统音频</span><span class="sxs-lookup"><span data-stu-id="250a8-278">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="250a8-279">同时 MRC 限制</span><span class="sxs-lookup"><span data-stu-id="250a8-279">Simultaneous MRC limitations</span></span>

<span data-ttu-id="250a8-280">同时访问 MRC 的多个应用有一定的限制。</span><span class="sxs-lookup"><span data-stu-id="250a8-280">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="250a8-281">照片/视频相机访问</span><span class="sxs-lookup"><span data-stu-id="250a8-281">Photo/video camera access</span></span>

<span data-ttu-id="250a8-282">照片/视频摄像机限制为可同时访问的进程数。</span><span class="sxs-lookup"><span data-stu-id="250a8-282">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="250a8-283">当某个进程录制视频或拍摄照片时, 将无法获取照片/视频相机。</span><span class="sxs-lookup"><span data-stu-id="250a8-283">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="250a8-284">(这适用于混合现实捕获和标准照片/视频捕获)</span><span class="sxs-lookup"><span data-stu-id="250a8-284">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="250a8-285">使用 HoloLens 2, 应用程序可以使用 MediaCaptureInitializationSettings 的[SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)属性来指示他们希望在不需要对照片/视频摄像机进行独占控制的情况下运行 SharedReadOnly。</span><span class="sxs-lookup"><span data-stu-id="250a8-285">With HoloLens 2, an app can use MediaCaptureInitializationSettings's [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) property to indicate that they want to run SharedReadOnly if they don't need exclusive control over the photo/video camera.</span></span> <span data-ttu-id="250a8-286">这样做意味着捕获的分辨率和帧速率将限制为其他应用已配置照相机提供的内容。</span><span class="sxs-lookup"><span data-stu-id="250a8-286">Doing so means the resolution and framerate of the capture will be limited to what other apps have configured the camera to provide.</span></span>

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="250a8-287">内置的 MRC 照片/视频相机访问</span><span class="sxs-lookup"><span data-stu-id="250a8-287">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="250a8-288">内置于 Windows 10 的 MRC 功能 (通过 Cortana、开始菜单、硬件快捷方式、Miracast、Windows 设备门户):</span><span class="sxs-lookup"><span data-stu-id="250a8-288">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>
* <span data-ttu-id="250a8-289">默认情况下, 将使用 ExclusiveControl 运行</span><span class="sxs-lookup"><span data-stu-id="250a8-289">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="250a8-290">但是, 对每个要在共享模式下运行的子系统添加了支持:</span><span class="sxs-lookup"><span data-stu-id="250a8-290">However, support has been added to each subsystem to operate in a shared mode:</span></span>
* <span data-ttu-id="250a8-291">如果应用请求 ExclusiveControl 访问照片/视频摄像机, 内置的 MRC 会自动停止使用照片/视频相机, 因此应用的请求将会成功。</span><span class="sxs-lookup"><span data-stu-id="250a8-291">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span>
* <span data-ttu-id="250a8-292">如果在某个应用具有 ExclusiveControl 的情况下启动内置的 MRC, 内置的 MRC 将在 SharedReadOnly 模式下运行</span><span class="sxs-lookup"><span data-stu-id="250a8-292">If built-in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span>

<span data-ttu-id="250a8-293">此共享模式功能有一些限制:</span><span class="sxs-lookup"><span data-stu-id="250a8-293">This shared mode functionality has certain restrictions:</span></span>
* <span data-ttu-id="250a8-294">通过 Cortana、硬件快捷方式或 "开始" 菜单的照片:需要 Windows 10 2018 年4月更新版 (或更高版本)</span><span class="sxs-lookup"><span data-stu-id="250a8-294">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="250a8-295">通过 Cortana、硬件快捷方式或 "开始" 菜单的视频:需要 Windows 10 2018 年4月更新版 (或更高版本)</span><span class="sxs-lookup"><span data-stu-id="250a8-295">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="250a8-296">通过 Miracast 流式处理 MRC:需要 Windows 10 十月2018更新 (或更高版本)</span><span class="sxs-lookup"><span data-stu-id="250a8-296">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="250a8-297">通过 Windows 设备门户或通过 HoloLens 随附应用流式传输 MRC:需要 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="250a8-297">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="250a8-298">当另一个应用正在使用照片/视频摄像机时, 内置 MRC 相机 UI 的分辨率和帧速率可能会从其正常值中减少。</span><span class="sxs-lookup"><span data-stu-id="250a8-298">The resolution and framerate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="250a8-299">MRC 访问</span><span class="sxs-lookup"><span data-stu-id="250a8-299">MRC access</span></span>

<span data-ttu-id="250a8-300">使用 Windows 10 4 2018 月版更新后, 在多个应用程序中访问 MRC 流的情况不再受限制 (不过, 对 photo/视频摄像机的访问仍有限制)。</span><span class="sxs-lookup"><span data-stu-id="250a8-300">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="250a8-301">在 Windows 10 4 2018 月版更新之前, 应用的自定义 MRC 记录器与系统 MRC (捕获照片、捕获视频或从 Windows 设备门户进行流式处理) 互斥。</span><span class="sxs-lookup"><span data-stu-id="250a8-301">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="250a8-302">请参阅</span><span class="sxs-lookup"><span data-stu-id="250a8-302">See also</span></span>
* [<span data-ttu-id="250a8-303">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="250a8-303">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="250a8-304">旁观视图</span><span class="sxs-lookup"><span data-stu-id="250a8-304">Spectator view</span></span>](spectator-view.md)
