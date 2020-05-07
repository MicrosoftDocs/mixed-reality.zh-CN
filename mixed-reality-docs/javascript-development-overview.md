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
# <a name="mixed-reality-development-with-javascript-overview"></a>混合现实开发与 JavaScript 概述

## <a name="mixed-reality-applications-on-the-web"></a>Web 上的混合现实应用程序

混合现实功能在 web 上通过使用[WebXR 设备 api](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)和[弃用的 WebVR api](webxr-overview.md)提供。 对于不支持完全 WebXR 功能的浏览器，你可以将[WebXR 填充代码](https://github.com/immersive-web/webxr-polyfill)添加到你的网站。

## <a name="what-is-webxr-polyfill"></a>什么是 WebXR 填充代码

WebXR 设备 API 的 JavaScript 实现，以及 WebXR 游戏板模块。 此填充代码允许开发人员针对最新的规范进行编写，在实现 WebVR 1.1 规范的浏览器上运行时提供支持，或在无 WebVR/WebXR 支持的移动设备上运行。

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>用于在 web 上构建混合现实应用程序的 JavaScript 库

## <a name="babylonjs"></a>Babylon

Babylon 是一个 JavaScript 3D 引擎，可轻松开发3D 内容和沉浸式应用程序。 在开始利用沉浸式应用程序之前，我们建议了解 Babylon 开发的基础知识。

了解如何使用 Babylon 在 "入门"[部分](https://doc.babylonjs.com/)中构建混合现实应用程序。 使用[Babylon 板块](https://doc.babylonjs.com/examples/)以三维示例和其源代码播放。 在文档的[WebXR 部分](https://doc.babylonjs.com/how_to/introduction_to_webxr)深入了解混合现实开发。 

## <a name="a-frame"></a>A 帧

框架是一种声明性的 JavaScript 框架，用于在 web 中开始虚拟现实。 有关详细信息，请参阅[框架文档](https://aframe.io/)。

## <a name="threejs"></a>四分之三

为创建沉浸式体验，有一个流行的3D 库。 有关[详细信息，请参阅文档](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)页和探索[示例](https://threejs.org/examples/#webgl_animation_cloth)。

## <a name="webgl"></a>WebGL

可以通过使用 WebGL Api 直接访问 WebXR 设备 Api。 WebGL （Web 图形库）是一个 JavaScript API，用于在任何兼容的 Web 浏览器中呈现高性能的交互式3D 和2D 图形，而无需使用插件。详细了解[WebGL api](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)。

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>使用 JavaScript 的混合现实本机移动应用程序

借助一些 JavaScript 库的帮助，你可以编写混合现实体验一次，并将其部署到 web 和本机平台，如 Windows Mixed Reality 耳机、Android 和 iOS 设备。

## <a name="babylon-native"></a>Babylon 本机

使用[Babylon 本机](https://www.babylonjs.com/native/)平台，任何人都可以使用其 Babylon 代码，并使用它构建本机应用程序，从而充分利用本机技术的功能。 可在[github 上下载 Babylon native](https://github.com/BabylonJS/BabylonNative) ，并在[Babylon 博客](https://medium.com/@babylonjs/babylon-native-821f1694fffc)上阅读更多相关信息。

## <a name="react-native"></a>React Native

[响应本机](https://reactnative.dev/)是另一个开源库，使开发人员可以使用 JavaScript 构建并部署到多个平台。 你可以下载[Github 上的响应](https://github.com/facebook/react-native)，并在对[本机博客做出响应](https://reactnative.dev/blog/)中了解有关该响应的详细信息。

## <a name="see-also"></a>另请参阅

* [WebXR 概述](webxr-overview.md)
* [WebXR 设备 API 规范](https://immersive-web.github.io/webxr/)
* [WebXR 设备 API 文档](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb](https://immersiveweb.dev/)
* [WebXR 示例](https://immersive-web.github.io/webxr-samples/)
* [使用 Babylon 创建 WebXR 体验](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality 和新的 Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [沉浸式 Web W3C Github](https://github.com/immersive-web)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[游戏板扩展](https://w3c.github.io/gamepad/extensions.html)
* [WebVR 概述](webvr-overview.md)
