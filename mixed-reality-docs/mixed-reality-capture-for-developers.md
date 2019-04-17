---
title: 面向开发人员混合现实捕获
description: 面向开发人员捕获混合现实的最佳做法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、 照片、 视频、 捕获、 照相机
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591594"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="0904d-104">面向开发人员混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="0904d-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="0904d-105">特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="0904d-105">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span> 

<span data-ttu-id="0904d-106">请参阅[应用程序中启用 MRC](#enabling-mrc-in-your-app)下面有关 HoloLens 2 新 MRC 功能的指导。</span><span class="sxs-lookup"><span data-stu-id="0904d-106">See [Enabling MRC in your app](#enabling-mrc-in-your-app) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="0904d-107">因为用户可能需要花[混合现实捕获](mixed-reality-capture.md)(MRC) 照片或视频在任何时间，没有开发应用程序时应牢记的一些事项。</span><span class="sxs-lookup"><span data-stu-id="0904d-107">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="0904d-108">这包括 MRC 视觉质量和正在响应系统更改，而将其捕获 MRCs 的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="0904d-108">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="0904d-109">开发人员可以也可无缝集成混合的现实捕获和插入到其应用程序。</span><span class="sxs-lookup"><span data-stu-id="0904d-109">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="0904d-110">MRC HoloLens （第一代） 上的支持视频和照片最多为 720p，虽然 MRC HoloLens 2 上的支持多达 1080p 和照片的视频最多有 4k 分辨率。</span><span class="sxs-lookup"><span data-stu-id="0904d-110">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="0904d-111">质量 MRC 的重要性</span><span class="sxs-lookup"><span data-stu-id="0904d-111">The importance of quality MRC</span></span>

<span data-ttu-id="0904d-112">混合的现实捕获照片和视频可能是首次用户将拥有的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0904d-112">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="0904d-113">是否为 Microsoft Store 页上或从其他用户在社交网络上共享 MRCs 的混合的现实屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="0904d-113">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="0904d-114">使用 MRC 演示您的应用程序，对用户进行培训，鼓励用户共享其混合的世界交互，以及用户调查和解决问题。</span><span class="sxs-lookup"><span data-stu-id="0904d-114">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="0904d-115">MRC 如何影响您的应用程序</span><span class="sxs-lookup"><span data-stu-id="0904d-115">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="0904d-116">在应用中启用 MRC</span><span class="sxs-lookup"><span data-stu-id="0904d-116">Enabling MRC in your app</span></span>

<span data-ttu-id="0904d-117">默认情况下，不需要执行任何操作即可使用户能够执行混合的现实捕获应用程序。</span><span class="sxs-lookup"><span data-stu-id="0904d-117">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span> <span data-ttu-id="0904d-118">但是，由于 HoloLens 2 的设计会增加照片/视频 (PV) 摄像机和显示之间的距离，我们将引入了新选项，生成的 PV 照相机与对齐第三照相机渲染**HoloLens 2**。</span><span class="sxs-lookup"><span data-stu-id="0904d-118">However, because the design of HoloLens 2 increases the distance between the photo/video (PV) camera and the display, we'll be introducing a new option to produce a 3rd camera render aligned to the PV camera of **HoloLens 2**.</span></span> 

<span data-ttu-id="0904d-119">在选择加入第三照相机上呈现 HoloLens 2 产品/服务的以下改进对默认 MRC 体验：</span><span class="sxs-lookup"><span data-stu-id="0904d-119">Opting-in to 3rd camera render on HoloLens 2 offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="0904d-120">全息图对齐方式为你的物理环境和手 （适用于近交互） 应是准确根本距离，而不是在距离而不让某一偏移量[关注点](focus-point-in-unity.md)正如您可能会看到默认 MRC 中。</span><span class="sxs-lookup"><span data-stu-id="0904d-120">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the [focus point](focus-point-in-unity.md) as you might see in the default MRC.</span></span>
* <span data-ttu-id="0904d-121">不会损害耳机右侧的眼睛，因为不会使用它来呈现为 MRC 输出全息。</span><span class="sxs-lookup"><span data-stu-id="0904d-121">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="0904d-122">应用程序中禁用 MRC</span><span class="sxs-lookup"><span data-stu-id="0904d-122">Disabling MRC in your app</span></span>

<span data-ttu-id="0904d-123">当使用 2D 应用[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx)或[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx)若要显示受保护的内容正确配置交换链，应用程序的可视内容将是混合的现实捕获正在运行时，会自动被遮盖。</span><span class="sxs-lookup"><span data-stu-id="0904d-123">When a 2D app uses [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) or [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) to show protected content with a properly-configured swap chain, the app's visual content will be automatically obscured while mixed reality capture is running.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="0904d-124">了解当 MRC 处于活动状态</span><span class="sxs-lookup"><span data-stu-id="0904d-124">Knowing when MRC is active</span></span>

<span data-ttu-id="0904d-125">[AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx)类可以由应用程序了解混合现实捕获系统 （对于音频或视频） 的运行时。</span><span class="sxs-lookup"><span data-stu-id="0904d-125">The [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="0904d-126">AppCapture 的[GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API 可以返回 null，如果混合现实捕获不是设备上可用。</span><span class="sxs-lookup"><span data-stu-id="0904d-126">AppCapture's [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="0904d-127">还有一点需要取消注册您的应用程序挂起时的 CapturingChanged 事件，否则 MRC 可能会进入阻止状态。</span><span class="sxs-lookup"><span data-stu-id="0904d-127">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="0904d-128">最佳做法 （特定于 HoloLens 的）</span><span class="sxs-lookup"><span data-stu-id="0904d-128">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="0904d-129">MRC 预期工作，而其他工作从开发人员，但有几个事项需要注意的以提供您的应用程序的最佳混合的现实捕获体验。</span><span class="sxs-lookup"><span data-stu-id="0904d-129">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="0904d-130">**MRC 使用全息图的 alpha 通道来与混合[照相机](locatable-camera.md)图像**</span><span class="sxs-lookup"><span data-stu-id="0904d-130">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="0904d-131">最重要的步骤是确保您的应用程序清除为透明黑色，而不是为不透明的黑色清除。</span><span class="sxs-lookup"><span data-stu-id="0904d-131">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="0904d-132">在 Unity 中，这是 MixedRealityToolkit 默认情况下，但如果你正在开发非 Unity 中，您可能需要进行更改的一行。</span><span class="sxs-lookup"><span data-stu-id="0904d-132">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="0904d-133">下面是一些你可能会在 MRC 中，如果您的应用程序不会清除为透明黑色的项目：</span><span class="sxs-lookup"><span data-stu-id="0904d-133">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="0904d-134">**示例故障**:黑色边缘周围的内容 （未能清除为透明黑色）</span><span class="sxs-lookup"><span data-stu-id="0904d-134">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

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

<span data-ttu-id="0904d-135">**示例故障**:整个背景场景的全息图显示为黑色。</span><span class="sxs-lookup"><span data-stu-id="0904d-135">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="0904d-136">在黑色背景中设置背景 alpha 值为 1 的结果</span><span class="sxs-lookup"><span data-stu-id="0904d-136">Setting a background alpha value of 1 results in a black background</span></span>

![在黑色背景中设置背景 alpha 值为 1 的结果](images/clearopaqueblack-300px.png)

<span data-ttu-id="0904d-138">**预期结果**:全息显示正确混合与现实世界 （如果清除为透明黑色预期结果）</span><span class="sxs-lookup"><span data-stu-id="0904d-138">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![如果清除为透明黑色的预期的结果](images/cleartransparentblack-300px.png)

<span data-ttu-id="0904d-140">**解决方案**：</span><span class="sxs-lookup"><span data-stu-id="0904d-140">**Solution**:</span></span>
* <span data-ttu-id="0904d-141">更改任何内容都如何显示为不透明的黑色具有 alpha 值为 0。</span><span class="sxs-lookup"><span data-stu-id="0904d-141">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="0904d-142">请确保该应用程序正在清除为透明黑色。</span><span class="sxs-lookup"><span data-stu-id="0904d-142">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="0904d-143">若要清除此选项可自动清除 MixedRealityToolkit，但如果它是一个非 Unity 应用，应修改与 ID3D11DeiceContext::ClearRenderTargetView() 一起使用的颜色与 unity 默认值。</span><span class="sxs-lookup"><span data-stu-id="0904d-143">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="0904d-144">你想要确保清除为透明黑色 (0,0,0,0) 而不是不透明黑 (0,0,0,1)。</span><span class="sxs-lookup"><span data-stu-id="0904d-144">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="0904d-145">如果想要但通常不需要现在可以优化你的资产的 alpha 值。</span><span class="sxs-lookup"><span data-stu-id="0904d-145">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="0904d-146">大多数情况下，MRCs 看现成的很好。</span><span class="sxs-lookup"><span data-stu-id="0904d-146">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="0904d-147">MRC 假定预乘的 alpha。</span><span class="sxs-lookup"><span data-stu-id="0904d-147">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="0904d-148">Alpha 值只会影响 MRC 捕获。</span><span class="sxs-lookup"><span data-stu-id="0904d-148">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="0904d-149">在 HoloLens 上启用 MRC 时会发生什么</span><span class="sxs-lookup"><span data-stu-id="0904d-149">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="0904d-150">以下内容适用于 HoloLens （第一代） 和 HoloLens 2，除非另有说明：</span><span class="sxs-lookup"><span data-stu-id="0904d-150">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="0904d-151">系统将限制为 30 Hz 呈现应用程序。</span><span class="sxs-lookup"><span data-stu-id="0904d-151">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="0904d-152">这将创建一些空间用于 MRC 运行，因此应用程序不需要保留的常量预算保留并也匹配 30 fps MRC 视频记录帧速率</span><span class="sxs-lookup"><span data-stu-id="0904d-152">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="0904d-153">全息图内容眼里出正确的设备时可能会显示以"礼花绽放"流式处理记录/MRC： 文本可能会变得更难以阅读和全息图边缘可能会出现更锯齿状 (在选择加入第三照相机上呈现**HoloLens 2**可避免此入侵）</span><span class="sxs-lookup"><span data-stu-id="0904d-153">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="0904d-154">MRC 照片和视频将遵守该应用程序[关注点](focus-point-in-unity.md)如果应用程序启用了它，这将有助于确保全息准确地定位。</span><span class="sxs-lookup"><span data-stu-id="0904d-154">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="0904d-155">对于视频，因此全息看起来似乎如果焦点深度发生了重大变化缓慢偏差到位平滑处理的焦点位置。</span><span class="sxs-lookup"><span data-stu-id="0904d-155">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="0904d-156">位于不同深度的焦点位置从全息可能在现实生活 （请参阅下面的示例，在 2 米设置焦点，但全息图定位在 1 米） 中显示偏移量。</span><span class="sxs-lookup"><span data-stu-id="0904d-156">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![在 2 米全息会完全对公众已注册。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="0904d-159">将从您的应用程序中的 MRC 功能集成</span><span class="sxs-lookup"><span data-stu-id="0904d-159">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="0904d-160">混合的现实应用 MRC 照片或视频捕获从在应用中，可以启动和捕获的内容将无需存储提供给您的应用程序到设备的"本机照片。"</span><span class="sxs-lookup"><span data-stu-id="0904d-160">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="0904d-161">可以创建自定义 MRC 记录器或充分利用内置相机捕捉 UI。</span><span class="sxs-lookup"><span data-stu-id="0904d-161">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="0904d-162">使用内置相机 UI MRC</span><span class="sxs-lookup"><span data-stu-id="0904d-162">MRC with built-in camera UI</span></span>

<span data-ttu-id="0904d-163">开发人员可以使用*[摄像头捕获 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 若要获取用户捕获混合的现实照片或视频只需几行代码。</span><span class="sxs-lookup"><span data-stu-id="0904d-163">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="0904d-164">此 API 启动内置 MRC 摄像头 UI，从该用户可以拍摄照片或视频，并返回结果捕获到您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0904d-164">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="0904d-165">如果你想要创建您自己摄像头 UI，或需要较低级别捕获对流的访问权限，则可以创建自定义的混合现实捕获记录器。</span><span class="sxs-lookup"><span data-stu-id="0904d-165">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="0904d-166">创建自定义 MRC 记录器</span><span class="sxs-lookup"><span data-stu-id="0904d-166">Creating a custom MRC recorder</span></span>

<span data-ttu-id="0904d-167">虽然用户始终可以触发照片或视频使用系统 MRC 捕获服务，应用程序可能想要生成自定义的相机应用程序，但就像 MRC 照相机流中包括全息。</span><span class="sxs-lookup"><span data-stu-id="0904d-167">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="0904d-168">这样，应用程序启动捕获代表用户、 生成自定义录制用户界面，或自定义 MRC 设置命名的几个示例。</span><span class="sxs-lookup"><span data-stu-id="0904d-168">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="0904d-169">**HoloStudio 添加自定义 MRC 照相机使用 MRC 效果**</span><span class="sxs-lookup"><span data-stu-id="0904d-169">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio 添加自定义 MRC 照相机使用 MRC 效果](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="0904d-171">Unity 应用程序应会看到[Locatable_camera_in_Unity](locatable-camera-in-unity.md)要启用全息的属性。</span><span class="sxs-lookup"><span data-stu-id="0904d-171">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="0904d-172">其他应用程序可以执行此操作通过使用[Windows 媒体捕获 Api](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)控制照相机并添加要在静止图像和视频中包含虚拟全息和应用程序音频 MRC 视频和音频效果。</span><span class="sxs-lookup"><span data-stu-id="0904d-172">Other applications can do this by using the [Windows Media Capture APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="0904d-173">应用程序具有两个选项来添加效果：</span><span class="sxs-lookup"><span data-stu-id="0904d-173">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="0904d-174">较旧的 API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)</span><span class="sxs-lookup"><span data-stu-id="0904d-174">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)</span></span>
* <span data-ttu-id="0904d-175">新的 Microsoft 建议 API （返回一个对象，使其可以处理动态属性）：[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx)需要应用程序创建其自己实现[IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx)并[IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx)。</span><span class="sxs-lookup"><span data-stu-id="0904d-175">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) which require the app create its own implementation of [IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) and [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx).</span></span> <span data-ttu-id="0904d-176">请参阅示例用法 MRC 效果示例。</span><span class="sxs-lookup"><span data-stu-id="0904d-176">Please see the MRC effect sample for sample usage.</span></span>

<span data-ttu-id="0904d-177">（请注意，Visual Studio 中，将无法识别这些命名空间，但字符串仍有效）</span><span class="sxs-lookup"><span data-stu-id="0904d-177">(Note that these namespaces will not be recognized by Visual Studio, but the strings are still valid)</span></span>

<span data-ttu-id="0904d-178">MRC 视频效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="0904d-178">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="0904d-179">属性名</span><span class="sxs-lookup"><span data-stu-id="0904d-179">Property Name</span></span>  |  <span data-ttu-id="0904d-180">在任务栏的搜索框中键入</span><span class="sxs-lookup"><span data-stu-id="0904d-180">Type</span></span>  |  <span data-ttu-id="0904d-181">默认值</span><span class="sxs-lookup"><span data-stu-id="0904d-181">Default Value</span></span>  |  <span data-ttu-id="0904d-182">描述</span><span class="sxs-lookup"><span data-stu-id="0904d-182">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="0904d-183">StreamType</span><span class="sxs-lookup"><span data-stu-id="0904d-183">StreamType</span></span>  |  <span data-ttu-id="0904d-184">UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))</span><span class="sxs-lookup"><span data-stu-id="0904d-184">UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))</span></span>  |  <span data-ttu-id="0904d-185">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="0904d-185">1 (VideoRecord)</span></span>  |  <span data-ttu-id="0904d-186">描述此效果用于捕获的流。</span><span class="sxs-lookup"><span data-stu-id="0904d-186">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="0904d-187">音频不可用。</span><span class="sxs-lookup"><span data-stu-id="0904d-187">Audio is not available.</span></span> | 
|  <span data-ttu-id="0904d-188">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="0904d-188">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="0904d-189">布尔值</span><span class="sxs-lookup"><span data-stu-id="0904d-189">boolean</span></span>  |  <span data-ttu-id="0904d-190">TRUE</span><span class="sxs-lookup"><span data-stu-id="0904d-190">TRUE</span></span>  |  <span data-ttu-id="0904d-191">若要启用或禁用全息视频捕获中的标记。</span><span class="sxs-lookup"><span data-stu-id="0904d-191">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="0904d-192">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="0904d-192">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="0904d-193">布尔值</span><span class="sxs-lookup"><span data-stu-id="0904d-193">boolean</span></span>  |  <span data-ttu-id="0904d-194">TRUE</span><span class="sxs-lookup"><span data-stu-id="0904d-194">TRUE</span></span>  |  <span data-ttu-id="0904d-195">一个标志，用于启用或禁用在屏幕上的录制指示器全息图捕获过程。</span><span class="sxs-lookup"><span data-stu-id="0904d-195">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="0904d-196">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="0904d-196">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="0904d-197">布尔值</span><span class="sxs-lookup"><span data-stu-id="0904d-197">boolean</span></span>  |  <span data-ttu-id="0904d-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="0904d-198">FALSE</span></span>  |  <span data-ttu-id="0904d-199">一个标志，用于启用或禁用由 HoloLens 跟踪程序提供支持的视频防抖动。</span><span class="sxs-lookup"><span data-stu-id="0904d-199">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="0904d-200">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="0904d-200">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="0904d-201">UINT32</span><span class="sxs-lookup"><span data-stu-id="0904d-201">UINT32</span></span>  |  <span data-ttu-id="0904d-202">0</span><span class="sxs-lookup"><span data-stu-id="0904d-202">0</span></span>  |  <span data-ttu-id="0904d-203">设置历史帧数用于视频防抖动。</span><span class="sxs-lookup"><span data-stu-id="0904d-203">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="0904d-204">0 为 0 的延迟和几乎"免费"从能力和性能的角度来看。</span><span class="sxs-lookup"><span data-stu-id="0904d-204">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="0904d-205">15 （但代价是 15 帧的滞后时间和内存） 的最高质量的建议。</span><span class="sxs-lookup"><span data-stu-id="0904d-205">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="0904d-206">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="0904d-206">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="0904d-207">浮点数</span><span class="sxs-lookup"><span data-stu-id="0904d-207">float</span></span>  |  <span data-ttu-id="0904d-208">0.9 (HoloLens) 1.0 （沉浸式头戴式）</span><span class="sxs-lookup"><span data-stu-id="0904d-208">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="0904d-209">全局不透明度系数的全息图中设置范围从 0.0 （完全透明） 到 1.0 （完全不透明）。</span><span class="sxs-lookup"><span data-stu-id="0904d-209">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="0904d-210">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="0904d-210">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="0904d-211">布尔值</span><span class="sxs-lookup"><span data-stu-id="0904d-211">boolean</span></span>  |  <span data-ttu-id="0904d-212">FALSE</span><span class="sxs-lookup"><span data-stu-id="0904d-212">FALSE</span></span>  |  <span data-ttu-id="0904d-213">一个标志，用于启用或禁用 2d 的 UWP 应用显示受保护的内容是否返回一个空框架。</span><span class="sxs-lookup"><span data-stu-id="0904d-213">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="0904d-214">此标志为 false 和 2d UWP 应用时显示受保护的内容，2d 的 UWP 应用将替换为受保护内容纹理，这两个耳机和混合的现实捕获中。</span><span class="sxs-lookup"><span data-stu-id="0904d-214">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="0904d-215">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="0904d-215">ShowHiddenMesh</span></span>  |  <span data-ttu-id="0904d-216">布尔值</span><span class="sxs-lookup"><span data-stu-id="0904d-216">boolean</span></span>  |  <span data-ttu-id="0904d-217">FALSE</span><span class="sxs-lookup"><span data-stu-id="0904d-217">FALSE</span></span>  |  <span data-ttu-id="0904d-218">若要启用或禁用显示 holographic 照相机的隐藏的区域网格和相邻内容的标记。</span><span class="sxs-lookup"><span data-stu-id="0904d-218">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |

<span data-ttu-id="0904d-219">MRC 音频效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="0904d-219">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="0904d-220">属性名</span><span class="sxs-lookup"><span data-stu-id="0904d-220">Property Name</span></span></th>
<th><span data-ttu-id="0904d-221">在任务栏的搜索框中键入</span><span class="sxs-lookup"><span data-stu-id="0904d-221">Type</span></span></th>
<th><span data-ttu-id="0904d-222">默认值</span><span class="sxs-lookup"><span data-stu-id="0904d-222">Default Value</span></span></th>
<th><span data-ttu-id="0904d-223">描述</span><span class="sxs-lookup"><span data-stu-id="0904d-223">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="0904d-224">MixerMode</span><span class="sxs-lookup"><span data-stu-id="0904d-224">MixerMode</span></span></td>
<td><span data-ttu-id="0904d-225">UINT32</span><span class="sxs-lookup"><span data-stu-id="0904d-225">UINT32</span></span></td>
<td><span data-ttu-id="0904d-226">2</span><span class="sxs-lookup"><span data-stu-id="0904d-226">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="0904d-227">0 :仅限 mic 音频</span><span class="sxs-lookup"><span data-stu-id="0904d-227">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="0904d-228">1 :仅系统音频</span><span class="sxs-lookup"><span data-stu-id="0904d-228">1 : System audio only</span></span></li>
<li><span data-ttu-id="0904d-229">2 :Mic 和系统音频</span><span class="sxs-lookup"><span data-stu-id="0904d-229">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="0904d-230">同时 MRC 限制</span><span class="sxs-lookup"><span data-stu-id="0904d-230">Simultaneous MRC limitations</span></span>

<span data-ttu-id="0904d-231">有多个应用在同一时间访问 MRC 方面的某些限制。</span><span class="sxs-lookup"><span data-stu-id="0904d-231">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="0904d-232">照片/视频照相机访问</span><span class="sxs-lookup"><span data-stu-id="0904d-232">Photo/video camera access</span></span>

<span data-ttu-id="0904d-233">照片/视频摄像机被限制为可以在同一时间访问它的进程数。</span><span class="sxs-lookup"><span data-stu-id="0904d-233">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="0904d-234">而在录制过程将失败视频或任何其他进程拍照获取照片/视频摄像机。</span><span class="sxs-lookup"><span data-stu-id="0904d-234">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="0904d-235">（适用于混合现实捕获和标准照片/视频捕获）</span><span class="sxs-lookup"><span data-stu-id="0904d-235">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="0904d-236">使用 Windows 10 2018 年 4 月更新，此限制不适用于如果内置 MRC 摄像头 UI 用于后应用已开始使用照片/视频照相机拍摄照片或视频。</span><span class="sxs-lookup"><span data-stu-id="0904d-236">With the Windows 10 April 2018 Update, this restriction does not apply if the built-in MRC camera UI is used to take a photo or a video after an app has started using the photo/video camera.</span></span> <span data-ttu-id="0904d-237">在此情况下，解析和内置 MRC 摄像头 UI 帧速率可能会降低其正常值中。</span><span class="sxs-lookup"><span data-stu-id="0904d-237">When this happens, the resolution and framerate of the built-in MRC camera UI might be reduced from its normal values.</span></span>

<span data-ttu-id="0904d-238">使用 Windows 10 2018 年 10 月更新，此限制不适用于 Miracast 通过流式处理 MRC。</span><span class="sxs-lookup"><span data-stu-id="0904d-238">With the Windows 10 October 2018 Update, this restriction does not apply to streaming MRC over Miracast.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="0904d-239">MRC 访问</span><span class="sxs-lookup"><span data-stu-id="0904d-239">MRC access</span></span>

<span data-ttu-id="0904d-240">使用 Windows 10 2018 年 4 月更新，不再有多个应用程序访问 （但是，对照片/视频摄像机的访问权限仍有一些局限性） MRC 流周围的限制。</span><span class="sxs-lookup"><span data-stu-id="0904d-240">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="0904d-241">先前的 windows 10 2018 年 4 月更新，应用程序的自定义 MRC 记录器的互斥与系统 MRC （拍摄照片、 捕获视频，或从 Windows Device Portal 流式处理）。</span><span class="sxs-lookup"><span data-stu-id="0904d-241">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="0904d-242">请参阅</span><span class="sxs-lookup"><span data-stu-id="0904d-242">See also</span></span>
* [<span data-ttu-id="0904d-243">混合的现实捕获</span><span class="sxs-lookup"><span data-stu-id="0904d-243">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="0904d-244">Spectator 视图</span><span class="sxs-lookup"><span data-stu-id="0904d-244">Spectator view</span></span>](spectator-view.md)
