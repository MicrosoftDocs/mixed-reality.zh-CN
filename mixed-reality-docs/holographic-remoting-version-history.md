---
title: 全息远程处理版本历史记录
description: HoloLens 2 上的全息远程处理的版本历史记录。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: f051dbf24cab550470a312933ffb99e1ba595257
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181957"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="51d58-104">全息远程处理版本历史记录</span><span class="sxs-lookup"><span data-stu-id="51d58-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51d58-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="51d58-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="51d58-106">版本2.0.18.0 （2019年12月17日）<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="51d58-106">Version 2.0.18.0 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="51d58-107">添加了对 HolographicViewConfiguration 的支持： https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span><span class="sxs-lookup"><span data-stu-id="51d58-107">Added support for HolographicViewConfiguration: https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration</span></span>
* <span data-ttu-id="51d58-108">修复了导致崩溃的各种 bug。</span><span class="sxs-lookup"><span data-stu-id="51d58-108">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="51d58-109">修复了一个 bug，HolographicCamera 需要 HolographicSpace CameraAdded 回调才能接受，并将其显示为 HoloraphicFrame 中的已添加照相机。</span><span class="sxs-lookup"><span data-stu-id="51d58-109">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <span data-ttu-id="51d58-110">版本2.0.16 （2019年11月11日）<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="51d58-110">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="51d58-111">修复了 QR 代码跟踪中的死锁。</span><span class="sxs-lookup"><span data-stu-id="51d58-111">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="51d58-112">修复了在主线程中阻止等待的 unhandeled 异常。</span><span class="sxs-lookup"><span data-stu-id="51d58-112">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <span data-ttu-id="51d58-113">版本2.0.14 （2019年10月26日）<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="51d58-113">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="51d58-114">支持新的 PerceptionDevice Api （Windows 10 11 月2019更新）。</span><span class="sxs-lookup"><span data-stu-id="51d58-114">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="51d58-115">修复了阻止 SpatialGestureRecognizer 触发暂停手势事件的问题。</span><span class="sxs-lookup"><span data-stu-id="51d58-115">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="51d58-116">修复了使用 SpatialSurfaceObserver 时的线程处理问题。</span><span class="sxs-lookup"><span data-stu-id="51d58-116">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="51d58-117">版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="51d58-117">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="51d58-118">修复了使用 NavigationRail （X/Y/Z）时 SpatialGestureRecognizer 中的崩溃。</span><span class="sxs-lookup"><span data-stu-id="51d58-118">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="51d58-119">版本 v2.0.10 （2019年10月10日）<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="51d58-119">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="51d58-120">修复了使用 VR 控制器的触发器按钮时出现故障。</span><span class="sxs-lookup"><span data-stu-id="51d58-120">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="51d58-121">全息远程处理并不完全支持控制器，如果与 HoloLens 2 配对，则仅触发器按钮和 Windows 按钮正常工作。</span><span class="sxs-lookup"><span data-stu-id="51d58-121">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="51d58-122">版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="51d58-122">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="51d58-123">添加了对[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支持</span><span class="sxs-lookup"><span data-stu-id="51d58-123">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="51d58-124">添加了新的接口 ```IPlayerContext2``` （由 ```PlayerContext```实现），提供以下成员：</span><span class="sxs-lookup"><span data-stu-id="51d58-124">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="51d58-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)属性。</span><span class="sxs-lookup"><span data-stu-id="51d58-125">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="51d58-126">已将 ```Failed_RemoteFrameTooOld``` 值添加到 ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="51d58-126">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="51d58-127">稳定性和可靠性改进</span><span class="sxs-lookup"><span data-stu-id="51d58-127">Stability and reliability improvements</span></span>

## <span data-ttu-id="51d58-128">版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="51d58-128">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="51d58-129">修复了使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)作为参数调用[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)时的崩溃。</span><span class="sxs-lookup"><span data-stu-id="51d58-129">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="51d58-130">稳定性和可靠性改进</span><span class="sxs-lookup"><span data-stu-id="51d58-130">Stability and reliability improvements</span></span>

## <span data-ttu-id="51d58-131">版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="51d58-131">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="51d58-132">适用于 HoloLens 2 的全息远程处理的第一个公共版本。</span><span class="sxs-lookup"><span data-stu-id="51d58-132">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="51d58-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="51d58-133">See Also</span></span>
* [<span data-ttu-id="51d58-134">编写自定义全息远程处理播放器应用程序</span><span class="sxs-lookup"><span data-stu-id="51d58-134">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="51d58-135">编写全息远程处理主机应用</span><span class="sxs-lookup"><span data-stu-id="51d58-135">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="51d58-136">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="51d58-136">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="51d58-137">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="51d58-137">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="51d58-138">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="51d58-138">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
