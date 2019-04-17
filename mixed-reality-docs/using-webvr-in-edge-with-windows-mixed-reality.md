---
title: 使用 Windows Mixed Reality WebVR Microsoft Edge 中
description: 使用和开发在 Windows Mixed Reality WebVR 概述
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR、 WebXR、 WinMR、 WebAR，web vr、 web xr、 web mr、 web ar，360，360 视频、 360 视频、 360 照片、 360 照片、 360 内容、 沉浸式 web、 immersiveweb，信息工作者
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592975"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="6fea9-104">使用 Windows Mixed Reality WebVR Microsoft Edge 中</span><span class="sxs-lookup"><span data-stu-id="6fea9-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="6fea9-105">创建 Windows 混合现实的 WebVR 内容沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="6fea9-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="6fea9-106">WebVR 1.1 是 Microsoft Edge 开头的 Windows 10 Fall Creators Update 中可用。</span><span class="sxs-lookup"><span data-stu-id="6fea9-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="6fea9-107">开发人员现在可以使用此 API 在 web 上创建沉浸式 VR 体验。</span><span class="sxs-lookup"><span data-stu-id="6fea9-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="6fea9-108">WebVR API 提供到页面用于呈现回 HMD 立体声 WebGL 场景 HMD 姿势数据。</span><span class="sxs-lookup"><span data-stu-id="6fea9-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="6fea9-109">API 支持的详细信息位于[Microsoft Edge 平台状态页](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)。</span><span class="sxs-lookup"><span data-stu-id="6fea9-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="6fea9-110">WebVR API 图面区域会出现在所有时间内 Microsoft Edge。</span><span class="sxs-lookup"><span data-stu-id="6fea9-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="6fea9-111">但是，对 getVRDisplays() 的调用将仅返回耳机，如果插入了耳机或模拟器已开启。</span><span class="sxs-lookup"><span data-stu-id="6fea9-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="6fea9-112">查看 Windows Mixed Reality 沉浸式耳机 WebVR 内容</span><span class="sxs-lookup"><span data-stu-id="6fea9-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="6fea9-113">有关访问在您的沉浸式头戴式 WebVR 内容的说明可在[酷爱钻研技术的指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)。</span><span class="sxs-lookup"><span data-stu-id="6fea9-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="6fea9-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="6fea9-114">See Also</span></span>
* [<span data-ttu-id="6fea9-115">WebVR 信息</span><span class="sxs-lookup"><span data-stu-id="6fea9-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="6fea9-116">WebVR 规范</span><span class="sxs-lookup"><span data-stu-id="6fea9-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="6fea9-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="6fea9-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="6fea9-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="6fea9-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="6fea9-119">[游戏手柄 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[游戏板扩展](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="6fea9-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="6fea9-120">处理丢失 WebGL 中的上下文</span><span class="sxs-lookup"><span data-stu-id="6fea9-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="6fea9-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="6fea9-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="6fea9-122">glTF</span><span class="sxs-lookup"><span data-stu-id="6fea9-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="6fea9-123">使用 Babylon.js 启用 WebVR</span><span class="sxs-lookup"><span data-stu-id="6fea9-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

