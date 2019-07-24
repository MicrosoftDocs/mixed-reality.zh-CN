---
title: 在 Microsoft Edge 中将 WebVR 用于 Windows Mixed Reality
description: 使用和开发 Windows Mixed Reality 中的 WebVR 概述
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, web mr, web ar, 360, 360 视频, 360 视频, 360 照片, 360 照片, 360 内容, 沉浸式 web, immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548753"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="a2780-104">在 Microsoft Edge 中将 WebVR 用于 Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a2780-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="a2780-105">为 Windows Mixed reality 沉浸式耳机创建 WebVR 内容</span><span class="sxs-lookup"><span data-stu-id="a2780-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="a2780-106">从 Windows 10 秋季创意者更新开始, Microsoft Edge 中提供了 WebVR 1.1。</span><span class="sxs-lookup"><span data-stu-id="a2780-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="a2780-107">现在, 开发人员可以使用此 API 在 web 上创建沉浸式 VR 体验。</span><span class="sxs-lookup"><span data-stu-id="a2780-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="a2780-108">WebVR API 向页面提供 HMD 姿势数据, 该数据可用于将立体声 WebGL 场景呈现回 HMD。</span><span class="sxs-lookup"><span data-stu-id="a2780-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="a2780-109">有关 API 支持的详细信息, 请访问[Microsoft Edge 平台状态页](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)。</span><span class="sxs-lookup"><span data-stu-id="a2780-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="a2780-110">Microsoft Edge 中的任何时间都存在 WebVR API 外围应用。</span><span class="sxs-lookup"><span data-stu-id="a2780-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="a2780-111">但是, 如果耳机已插入或模拟器已打开, 则对 getVRDisplays () 的调用将仅返回耳机。</span><span class="sxs-lookup"><span data-stu-id="a2780-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="a2780-112">查看 Windows Mixed Reality 沉浸式耳机中的 WebVR 内容</span><span class="sxs-lookup"><span data-stu-id="a2780-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="a2780-113">有关如何访问沉浸式头戴式耳机中的 WebVR 内容的说明, 请参阅[发烧的指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)。</span><span class="sxs-lookup"><span data-stu-id="a2780-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2780-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="a2780-114">See Also</span></span>
* [<span data-ttu-id="a2780-115">WebVR 信息</span><span class="sxs-lookup"><span data-stu-id="a2780-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="a2780-116">WebVR 规范</span><span class="sxs-lookup"><span data-stu-id="a2780-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="a2780-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="a2780-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="a2780-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="a2780-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="a2780-119">[游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[游戏板扩展](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="a2780-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="a2780-120">处理 WebGL 中丢失的上下文</span><span class="sxs-lookup"><span data-stu-id="a2780-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="a2780-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="a2780-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="a2780-122">glTF</span><span class="sxs-lookup"><span data-stu-id="a2780-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="a2780-123">使用 Babylon 启用 WebVR</span><span class="sxs-lookup"><span data-stu-id="a2780-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

