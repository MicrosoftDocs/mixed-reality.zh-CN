---
title: 全息远程处理版本历史记录
description: HoloLens 2 上的全息远程处理的版本历史记录。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: 5ba3aaa8874dea4418114b331d3d99fc977e982c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278195"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="2ca42-104">全息远程处理版本历史记录</span><span class="sxs-lookup"><span data-stu-id="2ca42-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ca42-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="2ca42-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="version-210-march-11-2020"></a><span data-ttu-id="2ca42-106">版本2.1.0 （2020年3月11日）<a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-106">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>
* <span data-ttu-id="2ca42-107">已将网络传输切换为使用[RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP。</span><span class="sxs-lookup"><span data-stu-id="2ca42-107">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="2ca42-108">安全连接现在使用[SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 。</span><span class="sxs-lookup"><span data-stu-id="2ca42-108">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="2ca42-109">请注意，[全息远程处理播放器](holographic-remoting-player.md)仍与所有以前版本的全息远程处理版本兼容。</span><span class="sxs-lookup"><span data-stu-id="2ca42-109">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="2ca42-110">若要从新的网络传输中获益，全息远程处理播放器和有问题的远程应用必须使用版本2.1.0。</span><span class="sxs-lookup"><span data-stu-id="2ca42-110">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="2ca42-111">添加了对[HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)的支持。</span><span class="sxs-lookup"><span data-stu-id="2ca42-111">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <a name="version-2020-february-2-2020"></a><span data-ttu-id="2ca42-112">版本2.0.20 （2020年2月2日）<a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-112">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>
* <span data-ttu-id="2ca42-113">修复了导致崩溃的各种 bug。</span><span class="sxs-lookup"><span data-stu-id="2ca42-113">Fixed various bugs that lead to crashes.</span></span>

## <a name="version-2018-december-17-2019"></a><span data-ttu-id="2ca42-114">版本2.0.18 （2019年12月17日）<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-114">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="2ca42-115">添加了对[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)的支持</span><span class="sxs-lookup"><span data-stu-id="2ca42-115">Added support for [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="2ca42-116">修复了导致崩溃的各种 bug。</span><span class="sxs-lookup"><span data-stu-id="2ca42-116">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="2ca42-117">修复了一个 bug，HolographicCamera 需要 HolographicSpace CameraAdded 回调才能接受，并将其显示为 HoloraphicFrame 中的已添加照相机。</span><span class="sxs-lookup"><span data-stu-id="2ca42-117">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <a name="version-2016-november-11-2019"></a><span data-ttu-id="2ca42-118">版本2.0.16 （2019年11月11日）<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-118">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="2ca42-119">修复了 QR 代码跟踪中的死锁。</span><span class="sxs-lookup"><span data-stu-id="2ca42-119">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="2ca42-120">修复了在主线程中阻止等待的 unhandeled 异常。</span><span class="sxs-lookup"><span data-stu-id="2ca42-120">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <a name="version-2014-october-26-2019"></a><span data-ttu-id="2ca42-121">版本2.0.14 （2019年10月26日）<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-121">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="2ca42-122">支持新的 PerceptionDevice Api （Windows 10 11 月2019更新）。</span><span class="sxs-lookup"><span data-stu-id="2ca42-122">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="2ca42-123">修复了阻止 SpatialGestureRecognizer 触发暂停手势事件的问题。</span><span class="sxs-lookup"><span data-stu-id="2ca42-123">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="2ca42-124">修复了使用 SpatialSurfaceObserver 时的线程处理问题。</span><span class="sxs-lookup"><span data-stu-id="2ca42-124">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <a name="version-2012-october-18-2019"></a><span data-ttu-id="2ca42-125">版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-125">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="2ca42-126">修复了使用 NavigationRail （X/Y/Z）时 SpatialGestureRecognizer 中的崩溃。</span><span class="sxs-lookup"><span data-stu-id="2ca42-126">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <a name="version-2010-october-10-2019"></a><span data-ttu-id="2ca42-127">版本 v2.0.10 （2019年10月10日）<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-127">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="2ca42-128">修复了使用 VR 控制器的触发器按钮时出现故障。</span><span class="sxs-lookup"><span data-stu-id="2ca42-128">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="2ca42-129">全息远程处理并不完全支持控制器，如果与 HoloLens 2 配对，则仅触发器按钮和 Windows 按钮正常工作。</span><span class="sxs-lookup"><span data-stu-id="2ca42-129">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <a name="version-209-september-19-2019"></a><span data-ttu-id="2ca42-130">版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-130">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="2ca42-131">添加了对[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支持</span><span class="sxs-lookup"><span data-stu-id="2ca42-131">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="2ca42-132">添加了新的接口 ```IPlayerContext2``` （由 ```PlayerContext```实现），提供以下成员：</span><span class="sxs-lookup"><span data-stu-id="2ca42-132">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="2ca42-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)属性。</span><span class="sxs-lookup"><span data-stu-id="2ca42-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="2ca42-134">已将 ```Failed_RemoteFrameTooOld``` 值添加到 ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="2ca42-134">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="2ca42-135">稳定性和可靠性改进</span><span class="sxs-lookup"><span data-stu-id="2ca42-135">Stability and reliability improvements</span></span>

## <a name="version-208-august-20-2019"></a><span data-ttu-id="2ca42-136">版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-136">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="2ca42-137">修复了使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)作为参数调用[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)时的崩溃。</span><span class="sxs-lookup"><span data-stu-id="2ca42-137">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="2ca42-138">稳定性和可靠性改进</span><span class="sxs-lookup"><span data-stu-id="2ca42-138">Stability and reliability improvements</span></span>

## <a name="version-207-july-26-2019"></a><span data-ttu-id="2ca42-139">版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="2ca42-139">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="2ca42-140">适用于 HoloLens 2 的全息远程处理的第一个公共版本。</span><span class="sxs-lookup"><span data-stu-id="2ca42-140">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ca42-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ca42-141">See Also</span></span>
* [<span data-ttu-id="2ca42-142">编写自定义全息远程处理播放器应用程序</span><span class="sxs-lookup"><span data-stu-id="2ca42-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="2ca42-143">编写全息远程处理主机应用</span><span class="sxs-lookup"><span data-stu-id="2ca42-143">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="2ca42-144">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="2ca42-144">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="2ca42-145">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="2ca42-145">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="2ca42-146">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="2ca42-146">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
