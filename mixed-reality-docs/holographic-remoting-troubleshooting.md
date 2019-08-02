---
title: 全息远程处理故障排除和限制
description: HoloLens 2 上的全息远程处理的故障排除步骤。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 08/01/2019
ms.topic: article
keywords: Windows Mixed Reality, 全息影像, 全息远程处理, 远程渲染, 网络渲染, HoloLens, 远程影像, 故障排除, 帮助
ms.openlocfilehash: 86b6979dbfc9b514b3af13ebdcc3d3ece17e6335
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718141"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="511b5-104">全息远程处理疑难解答</span><span class="sxs-lookup"><span data-stu-id="511b5-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="511b5-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="511b5-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="511b5-106">找不到 Spectre 缓解的库。</span><span class="sxs-lookup"><span data-stu-id="511b5-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="511b5-107">全息远程处理示例应用在发布配置中启用了 Spectre 缓解 (/Qspectre)。</span><span class="sxs-lookup"><span data-stu-id="511b5-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="511b5-108">如果收到一条错误链接器错误, 指出无法打开 "vccorlib.h", 请确保你的 Visual Studio 工作负荷包括 Spectre 缓解库。</span><span class="sxs-lookup"><span data-stu-id="511b5-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="511b5-109">有关更多信息，请参见 https://aka.ms/Ofhn4c 。</span><span class="sxs-lookup"><span data-stu-id="511b5-109">See https://aka.ms/Ofhn4c for more information.</span></span>

# <a name="limitations"></a><span data-ttu-id="511b5-110">限制</span><span class="sxs-lookup"><span data-stu-id="511b5-110">Limitations</span></span>

<span data-ttu-id="511b5-111">使用 HoloLens 2 的全息远程处理时, 当前**不**支持以下 api, 除非另有```ERROR_NOT_SUPPORTED```说明, 否则将引发错误:</span><span class="sxs-lookup"><span data-stu-id="511b5-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="511b5-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="511b5-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="511b5-113">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="511b5-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="511b5-114">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="511b5-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="511b5-115">HolographicCameraPose.OverrideViewport</span><span class="sxs-lookup"><span data-stu-id="511b5-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="511b5-116">HolographicCameraPose.OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="511b5-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* <span data-ttu-id="511b5-117">[HolographicCameraRenderingParameters CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) -不会失败, 但深度缓冲区将不会进行远程处理。</span><span class="sxs-lookup"><span data-stu-id="511b5-117">[HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) - Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="511b5-118">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="511b5-118">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="511b5-119">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="511b5-119">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="511b5-120">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="511b5-120">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="511b5-121">SpatialLocation. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="511b5-121">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="511b5-122">SpatialLocation. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="511b5-122">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="511b5-123">SpatialLocation. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="511b5-123">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="511b5-124">SpatialLocation. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="511b5-124">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="511b5-125">SpatialLocation. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="511b5-125">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/is-is/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="511b5-126">SpatialLocation. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="511b5-126">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* <span data-ttu-id="511b5-127">[SpatialStageFrameOfReference](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) -总是返回```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="511b5-127">[SpatialStageFrameOfReference.Current](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) - Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="511b5-128">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="511b5-128">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="511b5-129">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="511b5-129">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* <span data-ttu-id="511b5-130">[SpatialAnchorExporter. adaptivesourcemanager.getdefault](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
) -总是返回```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="511b5-130">[SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
) - Always returns ```nullptr```.</span></span>
* <span data-ttu-id="511b5-131">[SpatialAnchorExporter. RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
) -异步操作始终以```SpatialPerceptionAccessStatus.DeniedBySystem```结束。</span><span class="sxs-lookup"><span data-stu-id="511b5-131">[SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
) - Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* <span data-ttu-id="511b5-132">[SpatialAnchorTransferManager. RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) -异步操作始终以```SpatialPerceptionAccessStatus.DeniedBySystem```结束。</span><span class="sxs-lookup"><span data-stu-id="511b5-132">[SpatialAnchorTransferManager.RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) - Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* <span data-ttu-id="511b5-133">[SpatialAnchorTransferManager. TryExportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) -异步操作始终以```false```结束。</span><span class="sxs-lookup"><span data-stu-id="511b5-133">[SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) - Async operation always completes with ```false```.</span></span>
* <span data-ttu-id="511b5-134">[SpatialAnchorTransferManager. TryImportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) -异步操作始终以```nullptr```结束。</span><span class="sxs-lookup"><span data-stu-id="511b5-134">[SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) - Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="511b5-135">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="511b5-135">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="511b5-136">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="511b5-136">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="511b5-137">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="511b5-137">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="511b5-138">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="511b5-138">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="511b5-139">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="511b5-139">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="511b5-140">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="511b5-140">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="511b5-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="511b5-141">See Also</span></span>
* [<span data-ttu-id="511b5-142">编写全息远程处理主机应用</span><span class="sxs-lookup"><span data-stu-id="511b5-142">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="511b5-143">编写自定义全息远程处理播放器应用程序</span><span class="sxs-lookup"><span data-stu-id="511b5-143">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="511b5-144">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="511b5-144">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="511b5-145">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="511b5-145">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)