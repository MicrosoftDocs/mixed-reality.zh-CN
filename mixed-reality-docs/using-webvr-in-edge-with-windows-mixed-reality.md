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
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>在 Microsoft Edge 中将 WebVR 用于 Windows Mixed Reality

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>为 Windows Mixed reality 沉浸式耳机创建 WebVR 内容

从 Windows 10 秋季创意者更新开始, Microsoft Edge 中提供了 WebVR 1.1。 现在, 开发人员可以使用此 API 在 web 上创建沉浸式 VR 体验。

WebVR API 向页面提供 HMD 姿势数据, 该数据可用于将立体声 WebGL 场景呈现回 HMD。 有关 API 支持的详细信息, 请访问[Microsoft Edge 平台状态页](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)。 Microsoft Edge 中的任何时间都存在 WebVR API 外围应用。 但是, 如果耳机已插入或模拟器已打开, 则对 getVRDisplays () 的调用将仅返回耳机。

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>查看 Windows Mixed Reality 沉浸式耳机中的 WebVR 内容

有关如何访问沉浸式头戴式耳机中的 WebVR 内容的说明, 请参阅[发烧的指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)。

## <a name="see-also"></a>请参阅
* [WebVR 信息](http://webvr.info)
* [WebVR 规范](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [游戏板 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx)和[游戏板扩展](https://w3c.github.io/gamepad/extensions.html)
* [处理 WebGL 中丢失的上下文](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [使用 Babylon 启用 WebVR](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

