---
title: OpenXR 性能
description: 调试 OpenXR 应用程序的 GPU 性能。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件，性能，优化，GPU 调试，RenderDoc，PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163341"
---
# <a name="openxr-performance"></a>OpenXR 性能

在 HoloLens 2 上，有多种方法可通过 `xrEndFrame` 提交组合数据，这会导致后期处理，这将导致性能显著下降。
若要避免性能 penalities，请提交具有以下特征的[单个 `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) ：
* [使用纹理数组存在](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [使用主要颜色存在格式](openxr-best-practices.md#select-a-swapchain-format)
* [使用建议的视图维度](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* 不设置 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 标志
* 将 `XrCompositionLayerDepthInfoKHR` `minDepth` 设置为 0.0 f，并 `maxDepth` 设置为 1.0 f

其他注意事项将导致更好的性能：
* [使用16位深度格式](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [进行实例化绘图调用](openxr-best-practices.md#render-with-texture-array-and-vprt)
