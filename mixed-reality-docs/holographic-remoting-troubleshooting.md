---
title: 全息远程处理故障排除和限制
description: HoloLens 2 上的全息远程处理的故障排除步骤。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 12/17/2019
ms.topic: article
keywords: Windows Mixed Reality，全息影像，全息远程处理，远程渲染，网络渲染，HoloLens，远程影像，故障排除，帮助
ms.openlocfilehash: 05333c8911010945a543cf603b9925eb30c841db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181967"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="7e7c5-104">全息远程处理疑难解答</span><span class="sxs-lookup"><span data-stu-id="7e7c5-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e7c5-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="7e7c5-106">找不到 Spectre 缓解的库。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="7e7c5-107">全息远程处理示例应用在发布配置中启用了 Spectre 缓解（/Qspectre）。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="7e7c5-108">如果收到一条错误链接器错误，指出无法打开 "vccorlib.h"，请确保你的 Visual Studio 工作负荷包括 Spectre 缓解库。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="7e7c5-109">有关详细信息，请参阅 https://aka.ms/Ofhn4c 。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="7e7c5-110">限制</span><span class="sxs-lookup"><span data-stu-id="7e7c5-110">Limitations</span></span>

<span data-ttu-id="7e7c5-111">使用 HoloLens 2 的全息远程处理时，当前**不**支持以下 api，除非另有说明，否则将引发 ```ERROR_NOT_SUPPORTED``` 错误：</span><span class="sxs-lookup"><span data-stu-id="7e7c5-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="7e7c5-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="7e7c5-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="7e7c5-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="7e7c5-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="7e7c5-114">支持从版本[2.0.18](holographic-remoting-version-history.md#v2.0.18)开始</span><span class="sxs-lookup"><span data-stu-id="7e7c5-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="7e7c5-115">在以前的版本中，始终会引发错误。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="7e7c5-116">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="7e7c5-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="7e7c5-117">不会失败，但不会更改呈现目标大小。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="7e7c5-118">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="7e7c5-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="7e7c5-119">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="7e7c5-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="7e7c5-120">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="7e7c5-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="7e7c5-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="7e7c5-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="7e7c5-122">不会失败，但深度缓冲区将不会进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-122">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="7e7c5-123">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="7e7c5-123">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="7e7c5-124">查询 HolographicViewConfigurationKind PhotoVideoCamera 将始终返回 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-124">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="7e7c5-125">支持从版本[2.0.18](holographic-remoting-version-history.md#v2.0.18)开始</span><span class="sxs-lookup"><span data-stu-id="7e7c5-125">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="7e7c5-126">在以前的版本中，始终会引发错误。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-126">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="7e7c5-127">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="7e7c5-127">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="7e7c5-128">HolographicDisplay. Adaptivesourcemanager.getdefault</span><span class="sxs-lookup"><span data-stu-id="7e7c5-128">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="7e7c5-129">如果在建立连接之前调用，将报告错误。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-129">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="7e7c5-130">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="7e7c5-130">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="7e7c5-131">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="7e7c5-131">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="7e7c5-132">SpatialLocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="7e7c5-132">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="7e7c5-133">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="7e7c5-133">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="7e7c5-134">SpatialLocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="7e7c5-134">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="7e7c5-135">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="7e7c5-135">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="7e7c5-136">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="7e7c5-136">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="7e7c5-137">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="7e7c5-137">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="7e7c5-138">始终返回 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-138">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="7e7c5-139">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="7e7c5-139">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="7e7c5-140">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="7e7c5-140">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="7e7c5-141">SpatialAnchorExporter. Adaptivesourcemanager.getdefault</span><span class="sxs-lookup"><span data-stu-id="7e7c5-141">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="7e7c5-142">从版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-142">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="7e7c5-143">在以前的版本中，始终返回 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-143">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="7e7c5-144">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="7e7c5-144">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="7e7c5-145">从版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-145">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="7e7c5-146">在以前的版本中，异步操作始终以 ```SpatialPerceptionAccessStatus.DeniedBySystem```完成。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-146">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="7e7c5-147">SpatialAnchorTransferManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="7e7c5-147">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="7e7c5-148">异步操作始终以 ```SpatialPerceptionAccessStatus.DeniedBySystem```完成。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-148">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="7e7c5-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="7e7c5-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="7e7c5-150">异步操作始终以 ```false```完成。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-150">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="7e7c5-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="7e7c5-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="7e7c5-152">异步操作始终以 ```nullptr```完成。</span><span class="sxs-lookup"><span data-stu-id="7e7c5-152">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="7e7c5-153">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="7e7c5-153">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="7e7c5-154">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="7e7c5-154">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="7e7c5-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="7e7c5-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="7e7c5-156">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="7e7c5-156">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="7e7c5-157">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="7e7c5-157">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="7e7c5-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="7e7c5-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="7e7c5-159">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="7e7c5-159">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="7e7c5-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e7c5-160">See Also</span></span>
* [<span data-ttu-id="7e7c5-161">全息远程处理版本历史记录</span><span class="sxs-lookup"><span data-stu-id="7e7c5-161">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="7e7c5-162">编写全息远程处理主机应用</span><span class="sxs-lookup"><span data-stu-id="7e7c5-162">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="7e7c5-163">编写自定义全息远程处理播放器应用程序</span><span class="sxs-lookup"><span data-stu-id="7e7c5-163">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="7e7c5-164">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="7e7c5-164">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="7e7c5-165">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="7e7c5-165">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
