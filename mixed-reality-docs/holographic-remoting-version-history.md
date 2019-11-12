---
title: 全息远程处理版本历史记录
description: HoloLens 2 上的全息远程处理的版本历史记录。
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: 9ff6a5f7594eb67dd4c1c8690812ab724cac9012
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926652"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="eb041-104">全息远程处理版本历史记录</span><span class="sxs-lookup"><span data-stu-id="eb041-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb041-105">本指南特定于 HoloLens 2 上的全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="eb041-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="eb041-106">版本2.0.14 （2019年10月26日）<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="eb041-106">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="eb041-107">支持新的 PerceptionDevice Api （Windows 10 11 月2019更新）。</span><span class="sxs-lookup"><span data-stu-id="eb041-107">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="eb041-108">修复了阻止 SpatialGestureRecognizer 触发暂停手势事件的问题。</span><span class="sxs-lookup"><span data-stu-id="eb041-108">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="eb041-109">修复了使用 SpatialSurfaceObserver 时的线程处理问题。</span><span class="sxs-lookup"><span data-stu-id="eb041-109">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="eb041-110">版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="eb041-110">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="eb041-111">修复了使用 NavigationRail （X/Y/Z）时 SpatialGestureRecognizer 中的崩溃。</span><span class="sxs-lookup"><span data-stu-id="eb041-111">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="eb041-112">版本 v2.0.10 （2019年10月10日）<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="eb041-112">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="eb041-113">修复了使用 VR 控制器的触发器按钮时出现故障。</span><span class="sxs-lookup"><span data-stu-id="eb041-113">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="eb041-114">全息远程处理并不完全支持控制器，如果与 HoloLens 2 配对，则仅触发器按钮和 Windows 按钮正常工作。</span><span class="sxs-lookup"><span data-stu-id="eb041-114">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="eb041-115">版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="eb041-115">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="eb041-116">添加了对[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支持</span><span class="sxs-lookup"><span data-stu-id="eb041-116">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="eb041-117">添加了新的接口 ```IPlayerContext2``` （由 ```PlayerContext```实现），提供以下成员：</span><span class="sxs-lookup"><span data-stu-id="eb041-117">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="eb041-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)属性。</span><span class="sxs-lookup"><span data-stu-id="eb041-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="eb041-119">已将 ```Failed_RemoteFrameTooOld``` 值添加到 ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="eb041-119">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="eb041-120">稳定性和可靠性改进</span><span class="sxs-lookup"><span data-stu-id="eb041-120">Stability and reliability improvements</span></span>

## <span data-ttu-id="eb041-121">版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="eb041-121">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="eb041-122">修复了使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)作为参数调用[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)时的崩溃。</span><span class="sxs-lookup"><span data-stu-id="eb041-122">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="eb041-123">稳定性和可靠性改进</span><span class="sxs-lookup"><span data-stu-id="eb041-123">Stability and reliability improvements</span></span>

## <span data-ttu-id="eb041-124">版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="eb041-124">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="eb041-125">适用于 HoloLens 2 的全息远程处理的第一个公共版本。</span><span class="sxs-lookup"><span data-stu-id="eb041-125">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb041-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb041-126">See Also</span></span>
* [<span data-ttu-id="eb041-127">编写自定义全息远程处理播放器应用程序</span><span class="sxs-lookup"><span data-stu-id="eb041-127">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="eb041-128">编写全息远程处理主机应用</span><span class="sxs-lookup"><span data-stu-id="eb041-128">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="eb041-129">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="eb041-129">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="eb041-130">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="eb041-130">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="eb041-131">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="eb041-131">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
