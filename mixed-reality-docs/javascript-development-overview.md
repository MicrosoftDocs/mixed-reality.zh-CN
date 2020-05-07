---
title: JavaScript 混合现实开发概述
description: 使用适用于 web、移动和 windows 沉浸式耳机的 JavaScript 进行混合现实开发的概述。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR，WinMR，WebAR，WebVR，WindowsMixedReality，HoloLens，windows mixed reality，web vr，web xr，web mr，web ar，360，360视频，360视频，360照片，360照片，IW，immersiveweb，
ms.openlocfilehash: a1288e8f477f42b0937e797623fb83fe8f63685c
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835606"
---
# <a name="mixed-reality-development-with-javascript-overview"></a><span data-ttu-id="99898-104">混合现实开发与 JavaScript 概述</span><span class="sxs-lookup"><span data-stu-id="99898-104">Mixed Reality Development with JavaScript Overview</span></span>

## <a name="mixed-reality-applications-on-the-web"></a><span data-ttu-id="99898-105">Web 上的混合现实应用程序</span><span class="sxs-lookup"><span data-stu-id="99898-105">Mixed Reality applications on the web</span></span>

<span data-ttu-id="99898-106">混合现实功能在 web 上通过使用[WebXR 设备 api](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)和[弃用的 WebVR api](webxr-overview.md)提供。</span><span class="sxs-lookup"><span data-stu-id="99898-106">Mixed Reality features are available on the web by the use of [WebXR Device APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) and [deprecated WebVR APIs](webxr-overview.md).</span></span> <span data-ttu-id="99898-107">对于不支持完全 WebXR 功能的浏览器，你可以将[WebXR 填充代码](https://github.com/immersive-web/webxr-polyfill)添加到你的网站。</span><span class="sxs-lookup"><span data-stu-id="99898-107">For browsers that do not support full WebXR features, you can add [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill) to your website.</span></span>

## <a name="what-is-webxr-polyfill"></a><span data-ttu-id="99898-108">什么是 WebXR 填充代码</span><span class="sxs-lookup"><span data-stu-id="99898-108">What is WebXR Polyfill</span></span>

<span data-ttu-id="99898-109">WebXR 设备 API 的 JavaScript 实现，以及 WebXR 游戏板模块。</span><span class="sxs-lookup"><span data-stu-id="99898-109">A JavaScript implementation of the WebXR Device API, as well as the WebXR Gamepad Module.</span></span> <span data-ttu-id="99898-110">此填充代码允许开发人员针对最新的规范进行编写，在实现 WebVR 1.1 规范的浏览器上运行时提供支持，或在无 WebVR/WebXR 支持的移动设备上运行。</span><span class="sxs-lookup"><span data-stu-id="99898-110">This polyfill allows developers to write against the latest specification, providing support when run on browsers that implement the WebVR 1.1 spec, or on mobile devices with no WebVR/WebXR support at all.</span></span>

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a><span data-ttu-id="99898-111">用于在 web 上构建混合现实应用程序的 JavaScript 库</span><span class="sxs-lookup"><span data-stu-id="99898-111">JavaScript libraries to build Mixed Reality applications on the web</span></span>

## <a name="babylonjs"></a><span data-ttu-id="99898-112">Babylon</span><span class="sxs-lookup"><span data-stu-id="99898-112">Babylon.js</span></span>

<span data-ttu-id="99898-113">Babylon 是一个 JavaScript 3D 引擎，可轻松开发3D 内容和沉浸式应用程序。</span><span class="sxs-lookup"><span data-stu-id="99898-113">Babylon is a JavaScript 3D engine that makes developing 3D content and immersive applications easy.</span></span> <span data-ttu-id="99898-114">在开始利用沉浸式应用程序之前，我们建议了解 Babylon 开发的基础知识。</span><span class="sxs-lookup"><span data-stu-id="99898-114">Before getting started with immersive applications, we recommend to learn the basics of Babylon.js development.</span></span>

<span data-ttu-id="99898-115">了解如何使用 Babylon 在 "入门"[部分](https://doc.babylonjs.com/)中构建混合现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="99898-115">Learn how to build a mixed reality application with Babylon in the [getting started section](https://doc.babylonjs.com/).</span></span> <span data-ttu-id="99898-116">使用[Babylon 板块](https://doc.babylonjs.com/examples/)以三维示例和其源代码播放。</span><span class="sxs-lookup"><span data-stu-id="99898-116">Play with 3D examples and their source code using [Babylon Playground](https://doc.babylonjs.com/examples/).</span></span> <span data-ttu-id="99898-117">在文档的[WebXR 部分](https://doc.babylonjs.com/how_to/introduction_to_webxr)深入了解混合现实开发。</span><span class="sxs-lookup"><span data-stu-id="99898-117">Dive into mixed reality development on the [WebXR section](https://doc.babylonjs.com/how_to/introduction_to_webxr) of the documentation.</span></span> 

## <a name="a-frame"></a><span data-ttu-id="99898-118">A 帧</span><span class="sxs-lookup"><span data-stu-id="99898-118">A-Frame</span></span>

<span data-ttu-id="99898-119">框架是一种声明性的 JavaScript 框架，用于在 web 中开始虚拟现实。</span><span class="sxs-lookup"><span data-stu-id="99898-119">A-frame is a declarative JavaScript framework to get started with Virtual Reality in the web.</span></span> <span data-ttu-id="99898-120">有关详细信息，请参阅[框架文档](https://aframe.io/)。</span><span class="sxs-lookup"><span data-stu-id="99898-120">Check out the [A-Frame documentation](https://aframe.io/) to learn more.</span></span>

## <a name="threejs"></a><span data-ttu-id="99898-121">四分之三</span><span class="sxs-lookup"><span data-stu-id="99898-121">Three.js</span></span>

<span data-ttu-id="99898-122">为创建沉浸式体验，有一个流行的3D 库。</span><span class="sxs-lookup"><span data-stu-id="99898-122">Three.js is a popular 3D library for creating immersive experiences.</span></span> <span data-ttu-id="99898-123">有关[详细信息，请参阅文档](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)页和探索[示例](https://threejs.org/examples/#webgl_animation_cloth)。</span><span class="sxs-lookup"><span data-stu-id="99898-123">Learn more about [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) in documentation page and by exploring [examples](https://threejs.org/examples/#webgl_animation_cloth).</span></span>

## <a name="webgl"></a><span data-ttu-id="99898-124">WebGL</span><span class="sxs-lookup"><span data-stu-id="99898-124">WebGL</span></span>

<span data-ttu-id="99898-125">可以通过使用 WebGL Api 直接访问 WebXR 设备 Api。</span><span class="sxs-lookup"><span data-stu-id="99898-125">You can access the WebXR Device APIs directly by using WebGL APIs.</span></span> <span data-ttu-id="99898-126">WebGL （Web 图形库）是一个 JavaScript API，用于在任何兼容的 Web 浏览器中呈现高性能的交互式3D 和2D 图形，而无需使用插件。详细了解[WebGL api](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)。</span><span class="sxs-lookup"><span data-stu-id="99898-126">WebGL (Web Graphics Library) is a JavaScript API for rendering high-performance interactive 3D and 2D graphics within any compatible web browser without the use of plug-ins. Learn more about the [WebGL APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).</span></span>

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a><span data-ttu-id="99898-127">使用 JavaScript 的混合现实本机移动应用程序</span><span class="sxs-lookup"><span data-stu-id="99898-127">Mixed Reality native mobile applications using JavaScript</span></span>

<span data-ttu-id="99898-128">借助一些 JavaScript 库的帮助，你可以编写混合现实体验一次，并将其部署到 web 和本机平台，如 Windows Mixed Reality 耳机、Android 和 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="99898-128">With the help of few JavaScript libraries you can write your mixed reality experiences once and deploy it to web and to native platforms like Windows Mixed Reality headsets, Android and iOS devices.</span></span>

## <a name="babylon-native"></a><span data-ttu-id="99898-129">Babylon 本机</span><span class="sxs-lookup"><span data-stu-id="99898-129">Babylon Native</span></span>

<span data-ttu-id="99898-130">使用[Babylon 本机](https://www.babylonjs.com/native/)平台，任何人都可以使用其 Babylon 代码，并使用它构建本机应用程序，从而充分利用本机技术的功能。</span><span class="sxs-lookup"><span data-stu-id="99898-130">[Babylon Native](https://www.babylonjs.com/native/) platform allows anyone to take their Babylon.js code and build a native application with it, unlocking the power of native technologies.</span></span> <span data-ttu-id="99898-131">可在[github 上下载 Babylon native](https://github.com/BabylonJS/BabylonNative) ，并在[Babylon 博客](https://medium.com/@babylonjs/babylon-native-821f1694fffc)上阅读更多相关信息。</span><span class="sxs-lookup"><span data-stu-id="99898-131">You can download [Babylon native on github](https://github.com/BabylonJS/BabylonNative) and read more about it on [Babylon.js blog](https://medium.com/@babylonjs/babylon-native-821f1694fffc).</span></span>

## <a name="react-native"></a><span data-ttu-id="99898-132">React Native</span><span class="sxs-lookup"><span data-stu-id="99898-132">React Native</span></span>

<span data-ttu-id="99898-133">[响应本机](https://reactnative.dev/)是另一个开源库，使开发人员可以使用 JavaScript 构建并部署到多个平台。</span><span class="sxs-lookup"><span data-stu-id="99898-133">[React Native](https://reactnative.dev/) is another open source library that allows developers to build using JavaScript and deploy to multiple platforms.</span></span> <span data-ttu-id="99898-134">你可以下载[Github 上的响应](https://github.com/facebook/react-native)，并在对[本机博客做出响应](https://reactnative.dev/blog/)中了解有关该响应的详细信息。</span><span class="sxs-lookup"><span data-stu-id="99898-134">You can download [React Native on Github](https://github.com/facebook/react-native) and learn more about it in [React Native Blog](https://reactnative.dev/blog/).</span></span>

## <a name="see-also"></a><span data-ttu-id="99898-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99898-135">See Also</span></span>

* [<span data-ttu-id="99898-136">WebXR 概述</span><span class="sxs-lookup"><span data-stu-id="99898-136">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="99898-137">WebXR 设备 API 规范</span><span class="sxs-lookup"><span data-stu-id="99898-137">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="99898-138">WebXR 设备 API 文档</span><span class="sxs-lookup"><span data-stu-id="99898-138">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="99898-139">Immersiveweb</span><span class="sxs-lookup"><span data-stu-id="99898-139">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="99898-140">WebXR 示例</span><span class="sxs-lookup"><span data-stu-id="99898-140">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="99898-141">使用 Babylon 创建 WebXR 体验</span><span class="sxs-lookup"><span data-stu-id="99898-141">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="99898-142">Windows Mixed Reality 和新的 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="99898-142">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="99898-143">沉浸式 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="99898-143">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="99898-144">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="99898-144">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="99898-145">[游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[游戏板扩展](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="99898-145">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="99898-146">WebVR 概述</span><span class="sxs-lookup"><span data-stu-id="99898-146">WebVR Overview</span></span>](webvr-overview.md)
