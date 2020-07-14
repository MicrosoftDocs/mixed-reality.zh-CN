---
title: 全息远程处理故障排除和限制
description: HoloLens 2 上的全息远程处理的故障排除步骤。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality，全息影像，全息远程处理，远程渲染，网络渲染，HoloLens，远程影像，故障排除，帮助
ms.openlocfilehash: 593b242326b83d4596d22a7e1a39ef18c26bc67a
ms.sourcegitcommit: b392847529961ac36bbff154ce0830f8b2dbd766
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86300499"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="f2c10-104">全息远程处理疑难解答</span><span class="sxs-lookup"><span data-stu-id="f2c10-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2c10-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="f2c10-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="f2c10-106">找不到 Spectre 缓解的库。</span><span class="sxs-lookup"><span data-stu-id="f2c10-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="f2c10-107">全息远程处理示例应用在发布配置中启用了 Spectre 缓解 (/Qspectre) 。</span><span class="sxs-lookup"><span data-stu-id="f2c10-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="f2c10-108">如果收到一条错误链接器错误，指出无法打开 "vccorlib.h"，请确保你的 Visual Studio 工作负荷包括 Spectre 缓解库。</span><span class="sxs-lookup"><span data-stu-id="f2c10-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="f2c10-109">有关详细信息，请参阅 https://aka.ms/Ofhn4c 。</span><span class="sxs-lookup"><span data-stu-id="f2c10-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="speech"></a><span data-ttu-id="f2c10-110">语音</span><span class="sxs-lookup"><span data-stu-id="f2c10-110">Speech</span></span>

<span data-ttu-id="f2c10-111">全息远程处理播放器支持诊断覆盖，可以通过口述和禁用来启用此覆盖 ```Enable Diagnostics``` ```Disable Diagnostics``` 。</span><span class="sxs-lookup"><span data-stu-id="f2c10-111">The Holographic Remoting Player supports a diagnostics overlay which can be enabled by saying ```Enable Diagnostics``` and disabled by saying ```Disable Diagnostics```.</span></span> <span data-ttu-id="f2c10-112">如果使用这些语音命令时遇到问题，也可以通过 web 浏览器使用作为 URL 来启动全息远程处理播放器 ```ms-holographic-remoting:?stats``` 。</span><span class="sxs-lookup"><span data-stu-id="f2c10-112">If you have trouble with these voice commands you can also launch the Holographic Remoting player via a web browser using ```ms-holographic-remoting:?stats``` as an URL.</span></span>

## <a name="h265-video-codec-not-available"></a><span data-ttu-id="f2c10-113">H265 视频编解码器不可用</span><span class="sxs-lookup"><span data-stu-id="f2c10-113">H265 video codec not available</span></span>

<span data-ttu-id="f2c10-114">在远程应用中使用 H265 视频编解码器时，需要安装[HEVC 视频扩展](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7)。</span><span class="sxs-lookup"><span data-stu-id="f2c10-114">You need to install the [HEVC Video Extensions](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) when using H265 video codec in your remote app.</span></span> <span data-ttu-id="f2c10-115">如果遇到安装了编解码器但无法使用的问题，请查看[故障排除](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available)指南。</span><span class="sxs-lookup"><span data-stu-id="f2c10-115">If you run into issues where the codec is installed but can't be used, check out [troubleshooting](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) guide.</span></span>

## <a name="limitations"></a><span data-ttu-id="f2c10-116">限制</span><span class="sxs-lookup"><span data-stu-id="f2c10-116">Limitations</span></span>

<span data-ttu-id="f2c10-117">使用 HoloLens 2 的全息远程处理时，当前**不**支持以下 api，除非另有说明，否则将引发 ```ERROR_NOT_SUPPORTED``` 错误：</span><span class="sxs-lookup"><span data-stu-id="f2c10-117">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="f2c10-118">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="f2c10-118">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="f2c10-119">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2c10-119">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="f2c10-120">支持从版本[2.0.18](holographic-remoting-version-history.md#v2.0.18)开始</span><span class="sxs-lookup"><span data-stu-id="f2c10-120">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="f2c10-121">在以前的版本中，始终会引发错误。</span><span class="sxs-lookup"><span data-stu-id="f2c10-121">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="f2c10-122">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="f2c10-122">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="f2c10-123">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="f2c10-123">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="f2c10-124">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="f2c10-124">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="f2c10-125">在以前的版本中不会失败，但不会更改呈现目标大小。</span><span class="sxs-lookup"><span data-stu-id="f2c10-125">On previous versions does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="f2c10-126">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="f2c10-126">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="f2c10-127">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="f2c10-127">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="f2c10-128">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="f2c10-128">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - <span data-ttu-id="f2c10-129">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="f2c10-129">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="f2c10-130">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="f2c10-130">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="f2c10-131">不会失败，但深度缓冲区将不会进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="f2c10-131">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="f2c10-132">支持从版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)开始</span><span class="sxs-lookup"><span data-stu-id="f2c10-132">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="f2c10-133">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2c10-133">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="f2c10-134">查询 HolographicViewConfigurationKind PhotoVideoCamera 将始终返回 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="f2c10-134">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="f2c10-135">支持从版本[2.0.18](holographic-remoting-version-history.md#v2.0.18)开始</span><span class="sxs-lookup"><span data-stu-id="f2c10-135">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="f2c10-136">在以前的版本中，始终会引发错误。</span><span class="sxs-lookup"><span data-stu-id="f2c10-136">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="f2c10-137">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="f2c10-137">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="f2c10-138">HolographicDisplay. Adaptivesourcemanager.getdefault</span><span class="sxs-lookup"><span data-stu-id="f2c10-138">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="f2c10-139">如果在建立连接之前调用，将报告错误。</span><span class="sxs-lookup"><span data-stu-id="f2c10-139">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="f2c10-140">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="f2c10-140">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="f2c10-141">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="f2c10-141">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="f2c10-142">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="f2c10-142">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="f2c10-143">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="f2c10-143">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="f2c10-144">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="f2c10-144">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="f2c10-145">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="f2c10-145">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="f2c10-146">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="f2c10-146">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="f2c10-147">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="f2c10-147">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="f2c10-148">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="f2c10-148">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="f2c10-149">在以前的版本中 ```nullptr``` ，始终返回。</span><span class="sxs-lookup"><span data-stu-id="f2c10-149">On previous versions always returns ```nullptr```.</span></span>
* [<span data-ttu-id="f2c10-150">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="f2c10-150">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - <span data-ttu-id="f2c10-151">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="f2c10-151">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="f2c10-152">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="f2c10-152">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="f2c10-153">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="f2c10-153">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="f2c10-154">从版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持。</span><span class="sxs-lookup"><span data-stu-id="f2c10-154">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="f2c10-155">在以前的版本中 ```nullptr``` ，始终返回。</span><span class="sxs-lookup"><span data-stu-id="f2c10-155">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="f2c10-156">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="f2c10-156">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="f2c10-157">从版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持。</span><span class="sxs-lookup"><span data-stu-id="f2c10-157">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="f2c10-158">在以前的版本中，异步操作始终以完成 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="f2c10-158">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="f2c10-159">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="f2c10-159">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="f2c10-160">异步操作始终以结束 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="f2c10-160">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="f2c10-161">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="f2c10-161">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="f2c10-162">异步操作始终以结束 ```false``` 。</span><span class="sxs-lookup"><span data-stu-id="f2c10-162">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="f2c10-163">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="f2c10-163">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="f2c10-164">异步操作始终以结束 ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="f2c10-164">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="f2c10-165">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="f2c10-165">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="f2c10-166">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="f2c10-166">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="f2c10-167">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="f2c10-167">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="f2c10-168">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="f2c10-168">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - <span data-ttu-id="f2c10-169">支持从版本[2.2.0](holographic-remoting-version-history.md#v2.2.0)开始</span><span class="sxs-lookup"><span data-stu-id="f2c10-169">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>

[<span data-ttu-id="f2c10-170">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="f2c10-170">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="f2c10-171">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="f2c10-171">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="f2c10-172">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="f2c10-172">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="f2c10-173">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2c10-173">See Also</span></span>
* [<span data-ttu-id="f2c10-174">全息远程处理版本历史记录</span><span class="sxs-lookup"><span data-stu-id="f2c10-174">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="f2c10-175">编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="f2c10-175">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="f2c10-176">编写自定义全息远程处理播放器应用</span><span class="sxs-lookup"><span data-stu-id="f2c10-176">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="f2c10-177">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="f2c10-177">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="f2c10-178">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="f2c10-178">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
