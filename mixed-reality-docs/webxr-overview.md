---
title: 将 WebXR 与 Windows Mixed Reality 一起使用
description: 使用和开发 Windows Mixed Reality 中的 WebXR 概述
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR，WinMR，WebAR，WebVR，WindowsMixedReality，HoloLens，windows mixed reality，web vr，web xr，web mr，web ar，360，360视频，360视频，360照片，360照片，360内容，沉浸式 web，immersiveweb，IW
ms.openlocfilehash: 01e6cd44e9879cd7fd9b11e178134eaf364cc53c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278438"
---
# <a name="webxr-overview"></a><span data-ttu-id="75cf8-104">WebXR 概述</span><span class="sxs-lookup"><span data-stu-id="75cf8-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="75cf8-105">什么是 WebXR</span><span class="sxs-lookup"><span data-stu-id="75cf8-105">What is WebXR</span></span>

<span data-ttu-id="75cf8-106">**WebXR 设备 API**用于访问**虚拟现实（VR）** 和扩充的**现实（AR）** 设备，包括**传感器**和在**Web**上**装入的打印头**。</span><span class="sxs-lookup"><span data-stu-id="75cf8-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="75cf8-107">WebXR 设备 API 目前在 Microsoft Edge 中提供，Chrome 版本79及更高版本支持 WebXR 作为默认值。</span><span class="sxs-lookup"><span data-stu-id="75cf8-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="75cf8-108">可以在[caniuse.com](https://caniuse.com/#search=webxr)上检查 WebXR 的最新浏览器支持状态。</span><span class="sxs-lookup"><span data-stu-id="75cf8-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="75cf8-109">详细了解[Windows Mixed Reality 和新的 Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)新增[功能](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide)部分。</span><span class="sxs-lookup"><span data-stu-id="75cf8-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="75cf8-110">查看 WebXR</span><span class="sxs-lookup"><span data-stu-id="75cf8-110">Viewing WebXR</span></span>

<span data-ttu-id="75cf8-111">若要测试你的浏览器是否支持 WebXR，你可以在浏览器中导航到[WebXR 示例](https://immersive-web.github.io/webxr-samples/)。</span><span class="sxs-lookup"><span data-stu-id="75cf8-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="75cf8-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75cf8-112">See Also</span></span>

* [<span data-ttu-id="75cf8-113">WebXR 设备 API 规范</span><span class="sxs-lookup"><span data-stu-id="75cf8-113">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="75cf8-114">WebXR 设备 API 文档</span><span class="sxs-lookup"><span data-stu-id="75cf8-114">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="75cf8-115">Immersiveweb</span><span class="sxs-lookup"><span data-stu-id="75cf8-115">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="75cf8-116">WebXR 示例</span><span class="sxs-lookup"><span data-stu-id="75cf8-116">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="75cf8-117">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="75cf8-117">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="75cf8-118">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="75cf8-118">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="75cf8-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="75cf8-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="75cf8-120">[游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[游戏板扩展](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="75cf8-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="75cf8-121">处理 WebGL 中丢失的上下文</span><span class="sxs-lookup"><span data-stu-id="75cf8-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="75cf8-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="75cf8-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="75cf8-123">glTF</span><span class="sxs-lookup"><span data-stu-id="75cf8-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="75cf8-124">使用 Babylon 创建 WebXR 体验</span><span class="sxs-lookup"><span data-stu-id="75cf8-124">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="75cf8-125">沉浸式 web 社区组</span><span class="sxs-lookup"><span data-stu-id="75cf8-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
