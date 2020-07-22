---
title: OpenXR
description: 使用可移植 OpenXR API 标准构建引擎，并将其部署到 Windows Mixed Reality 和 HoloLens 2 耳机。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件
ms.openlocfilehash: 170ce0b55990158940692db25b925a1e79d7cf39
ms.sourcegitcommit: 3c32f45fd941767d408cccc5a76f1ff1cec763da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86879154"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR 是来自<a href="https://www.khronos.org/" target="_blank">Khronos</a>的开放版税免费 API 标准，可提供引擎，可从多个供应商处跨[混合现实频谱](mixed-reality.md)对各种设备进行本机访问。

可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 上的 Windows Mixed 耳机上进行开发。  如果你无权访问耳机，则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。

## <a name="why-openxr"></a>为什么要 OpenXR？

借助 OpenXR，你可以构建面向全息设备（如 HoloLens 2）的引擎，该引擎将数字内容置于真实世界中，就像它确实如此，还可以使用沉浸式设备（如台式计算机的 Windows Mixed Reality 耳机）来隐藏物理世界，并将其替换为数字体验。  OpenXR 可让你编写代码，然后在各种硬件平台上对其进行迁移。

OpenXR API 使用加载程序将应用程序直接连接到头戴显示设备的本机平台支持。  这为最终用户提供最大的性能和最小延迟，无论他们使用的是 Windows Mixed Reality 耳机还是其他任何耳机都是如此。

## <a name="what-is-openxr"></a>什么是 OpenXR？

OpenXR API 提供核心姿势预测、帧计时和空间输入功能，你需要构建一个引擎，该引擎可面向一个全息设备，如 HoloLens 2 和沉浸式设备，如 Windows Mixed Reality 耳机。

若要了解有关 OpenXR API 的信息，请参阅 OpenXR 1.0<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">规范</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 参考</a>和<a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速参考指南</a>。  有关详细信息，请参阅<a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 页</a>。

若要面向一组完整的 HoloLens 2 功能，还将使用跨供应商和供应商特定的 OpenXR 扩展，这些扩展启用 OpenXR 1.0 核心之外的其他功能，例如已表述的手动跟踪、目视跟踪、空间映射和空间锚。  请参阅下面的 "[路线图" 部分](#roadmap)，了解有关今年晚些扩展的详细信息。

请注意，OpenXR 本身并不是混合现实引擎。  相反，OpenXR 使 Unity 和 Unreal 等引擎可以编写可移植代码一次，这样就可以访问用户的全息或沉浸式设备的本机平台功能，而不管哪个供应商构建了该平台。

## <a name="roadmap"></a>路线图

OpenXR 规范定义了一种扩展机制，它使运行时实现程序能够公开超出<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">基本 OpenXR 1.0 规范</a>中定义的[核心功能](#what-is-openxr)的其他功能。

有三种类型的 OpenXR 扩展：
* **供应商扩展（例如 `MSFT` ）：** 支持硬件或软件功能中的每个供应商创新。  任何运行时供应商随时都可以引入和交付供应商扩展。
  * **实验性供应商扩展（例如 `MSFT_preview` ）：** 要预览的实验性供应商扩展以收集反馈。  `MSFT_preview`扩展仅适用于开发人员设备，并将在真正的扩展交付时删除。  若要对其进行试验，可以[在开发人员设备上启用预览版扩展](openxr-getting-started.md#using-preview-extensions)。
* **跨供应商 `EXT` 扩展：** 多个公司定义和实现的跨供应商扩展。  一组感兴趣的公司随时可以引入扩展扩展。
* **官方 `KHR` 扩展：** 正式 Khronos 扩展作为核心规范版本的一部分而被批准。  KHR 扩展与核心规范本身具有相同的许可证。

截止2020年7月，Windows Mixed Reality OpenXR 运行时支持一组 `MSFT` 和 `EXT` 扩展，这些扩展将一组完整的 HoloLens 2 功能提供给 OpenXR 应用程序：

| 功能区域 | 扩展可用性 |
|--------------|------------------------|
| 系统 + 会话 | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [引用空间（视图、本地、暂存）](coordinate-systems.md) | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| 查看配置（单声道、立体声） | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [交换链](rendering.md)  + [帧计时](understanding-performance-for-mixed-reality.md) | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| 组合层<br />（投影，四个） | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [输入和 haptics](interaction-fundamentals.md) | **OpenXR 1.0 核心规范：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 集成 | **正式 `KHR` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12 集成 | **正式 `KHR` 扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [未绑定的参考空间 <br /> （全球范围体验）](coordinate-systems.md#building-a-world-scale-experience) | **`MSFT`扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [空间定位点](spatial-anchors.md) | **`MSFT`扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [手动交互 <br /> （手柄/aim 姿势、空气分流、抓住）](hands-and-tools.md)<p>*仅 HoloLens 2*</p> | **`MSFT`扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [手型 articulation + 手写网格](hands-and-tools.md)<p>*仅 HoloLens 2*</p> | <p>**`EXT`在运行时102中发布的扩展：**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT`在运行时102中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [眼睛凝视](eye-tracking.md)<p>*仅 HoloLens 2*</p> | **`EXT`扩展已发布：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| 与其他 HoloLens Sdk 互操作<br />（例如[QR](qr-code-tracking.md)）<p>*仅 HoloLens 2*</p> | **`MSFT`在运行时102中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> |
| [混合现实捕获 <br /> （PV 相机的第三个渲染）](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*仅 HoloLens 2*</p> | **`MSFT`在运行时102中发布的扩展：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| 与 UWP CoreWindow API 互操作<br />（例如键盘/鼠标） | **`MSFT_preview`[预览版运行时 102](openxr-getting-started.md#using-preview-extensions)中的扩展：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_holographic_window_attachment_preview">XR_MSFT_holographic_window_attachment_preview</a></code><p>** `MSFT` 预览版运行时中的扩展**：8月 2020 *（已计划）*</p>
| [运动控制器呈现模型](motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT_preview`[预览版运行时](openxr-getting-started.md#using-preview-extensions)中的扩展：**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_controller_model_preview">XR_MSFT_controller_model_preview</a></code><p>** `MSFT` 预览版运行时中的扩展**：2020年9月 *（已计划）*</p> |
| [场景理解（平面、网格）](scene-understanding.md)<p>*仅 HoloLens 2*</p> | <p>**在[预览版运行时 102](openxr-getting-started.md#using-preview-extensions)中：**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code>与[场景理解 SDK](scene-understanding-sdk.md)一起使用</p><p>** `MSFT_preview` 未来预览运行时中的扩展** *（已计划）*</p> |
| 其他跨供应商扩展 | <p>**正式 `KHR` 扩展已发布：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT`已发布的扩展：**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

尽管其中一些扩展可能会作为特定于供应商的 `MSFT` 扩展开始，但 Microsoft 和其他 OpenXR 运行时供应商正在协同工作，以便为 `EXT` 其中许多功能领域设计跨供应商或 `KHR` 扩展。  这将使你为这些功能编写的代码可在运行时供应商之间移植，就像核心规范一样。

## <a name="get-started-with-openxr"></a>OpenXR 入门

可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 上的 Windows Mixed 耳机上进行开发。  如果你无权访问耳机，则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。

若要开始为 HoloLens 2 或沉浸式 Windows Mixed Reality 耳机开发 OpenXR 应用程序，请参阅[如何开始 OpenXR 开发](openxr-getting-started.md)。

## <a name="see-also"></a>另请参阅

* <a href="https://www.khronos.org/openxr/" target="_blank">有关 OpenXR 的详细信息</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 参考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速参考指南</a>
