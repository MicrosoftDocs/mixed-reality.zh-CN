---
title: OpenXR 最佳实践
description: 了解 OpenXR 应用程序的视觉质量、稳定性和性能的最佳实践。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件，最佳做法，性能，质量，稳定性
ms.openlocfilehash: 0a0bbd37521be52ec328b4f32e53969c0ec7fef4
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549370"
---
# <a name="openxr-app-best-practices"></a>OpenXR 应用最佳实践

可在<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>的 OpenXRProgram 文件中查看以下最佳实践的示例。 开始时，Run （）函数从初始化到事件和呈现循环捕获典型的 OpenXR 应用代码流。

## <a name="best-practices-for-visual-quality-and-stability"></a>视觉质量和稳定性的最佳实践

本节中的最佳实践介绍了如何在任何 OpenXR 应用程序中获得最佳视觉质量和稳定性。

有关特定于 HoloLens 2 的更多性能建议，请参阅下面的 " [hololens 2 的最佳性能方案](#best-practices-for-performance-on-hololens-2)" 部分。

### <a name="gamma-correct-rendering"></a>伽玛正确的呈现

必须小心，以确保您的渲染管道为伽玛正确。 在呈现到存在时，呈现目标视图格式应与存在格式（例如，存在格式和呈现目标视图 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`）匹配。
这种情况的例外是应用程序的呈现管道在着色器代码中执行手动 sRGB 转换，在这种情况下，应用程序应请求 sRGB 存在格式，但使用线性格式作为呈现目标视图（例如，请求 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 为存在格式但使用 `DXGI_FORMAT_B8G8R8A8_UNORM` 作为呈现目标视图），以防止内容被双重伽玛更正。

### <a name="submit-depth-buffer-for-projection-layers"></a>提交用于投影层的深度缓冲区

提交帧到 `xrEndFrame`时，请始终使用 `XR_KHR_composition_layer_depth` 扩展，并随投影层一起提交深度缓冲区。
这可以通过在 HoloLens 2 上启用硬件深度 reprojection 来改善全息影像的稳定性。

### <a name="choose-a-reasonable-depth-range"></a>选择合理的深度范围

首选较窄的深度范围来确定虚拟内容的作用域，以帮助在 HoloLens 上对虚拟目录进行稳定性。
例如，OpenXrProgram 示例使用0.1 到20米。
使用[反向-Z](https://developer.nvidia.com/content/depth-precision-visualized)以获得更统一的深度解析。
请注意，在 HoloLens 2 上，使用首选 `DXGI_FORMAT_D16_UNORM` 深度格式将有助于获得更好的帧速率和性能，不过，16位深度缓冲区提供的分辨率低于24位深度缓冲区。
因此，遵循这些最佳做法，充分利用深度解析变得更加重要。

### <a name="prepare-for-different-environment-blend-modes"></a>针对不同的环境混合模式做好准备

如果你的应用程序也将在完全堵塞世界的沉浸式耳机上运行，请确保使用 `xrEnumerateEnvironmentBlendModes` API 枚举支持的环境混合模式，并相应地准备呈现内容。
例如，对于具有 `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` 的系统（如 HoloLens），应用应使用透明的颜色作为清晰的颜色，而对于具有 `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`的系统，应用应在后台呈现一些不透明颜色或某些虚拟空间。

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>选择未绑定的引用空间作为应用程序的根空间

应用程序通常会建立一些根世界坐标空间，以便将视图、操作和全息连接在一起。
当支持扩展以建立[全球范围的坐标系统](coordinate-systems.md#building-a-world-scale-experience)时，可使用 `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT`，使应用能够避免在用户从应用启动的位置移到远处（如5米以外）时出现意外的全息影像偏移。
如果未绑定的空间扩展不存在，请使用 `XR_REFERENCE_SPACE_TYPE_LOCAL` 作为回退。

### <a name="associate-hologram-with-spatial-anchor"></a>将全息图与空间定位关联

使用未绑定的引用空间时，在该引用空间中直接放置的全息影像[可能会在用户进入远处房间后进入远处，并返回](coordinate-systems.md#building-a-world-scale-experience)。
对于全息图用户在世界各地的不同位置，请使用 `xrCreateSpatialAnchorSpaceMSFT` extension 函数[创建空间锚](spatial-anchors.md#best-practices)，并将全息影像置于其原点。
这会使全息图在一段时间内独立稳定。

### <a name="support-mixed-reality-capture"></a>支持混合现实捕获

尽管 HoloLens 2 的主显示器使用加法环境混合，但当用户启动[混合现实捕获](mixed-reality-capture-for-developers.md)时，应用的呈现内容将与环境视频流进行 alpha 混合。
若要在混合现实中获得最佳视觉质量捕获视频，最好将 `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` 设置在投影层的 `layerFlags`中。

## <a name="best-practices-for-performance-on-hololens-2"></a>HoloLens 2 上性能最佳方案

作为提供硬件 reprojection 支持的移动设备，HoloLens 2 对获得最佳性能的要求更严格。  有多种方法可通过 `xrEndFrame` 提交组合数据，这会导致后期处理，这将导致性能显著下降。

### <a name="select-a-swapchain-format"></a>选择存在格式

始终使用 `xrEnumerateSwapchainFormats`枚举受支持的像素格式，并选择应用程序支持的运行时中的第一种颜色和深度像素格式，因为这是运行时首选的，以实现最佳性能。 请注意，在 HoloLens 2 上，`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 和 `DXGI_FORMAT_D16_UNORM` 通常是实现更好的呈现性能的第一选择。 在台式计算机上运行的 VR 耳机上，此首选项可能有所不同，其中24位深度缓冲区的性能影响较低。
  
**性能警告：** 使用不是主存在颜色格式的格式将导致运行时后处理，这会产生严重的性能损失。

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>使用建议的呈现参数和帧计时进行呈现

始终使用推荐的视图配置宽度/高度（`recommendedImageRectWidth` 和 `recommendedImageRectHeight` `XrViewConfigurationView`）进行呈现，并且始终使用 `xrLocateViews` API 在呈现之前查询建议的视图 fov、和其他呈现参数。
查询姿势和视图时，请始终使用最新 `xrWaitFrame` 调用中的 `XrFrameEndInfo.predictedDisplayTime`。
这允许 HoloLens 为正在戴上的 HoloLens 的人员调整呈现和优化视觉质量。

### <a name="use-a-single-projection-layer"></a>使用单个投影层

HoloLens 2 为应用程序提供了有限的 GPU 能力，可让应用程序呈现内容和针对单个投影层优化的硬件组合器。
始终使用单个投影层可帮助应用程序的帧速率、全息图稳定性和视觉质量。  
  
**性能警告：** 提交任何内容，但只有一个保护层会导致运行时后处理，这会产生严重的性能损失。

### <a name="render-with-texture-array-and-vprt"></a>用纹理数组和 VPRT 进行呈现

使用 `arraySize=2` 颜色存在和深度，为左右眼睛创建一个 `xrSwapchain`。
将视觉眼睛渲染为切片0，将视觉眼睛转换为切片1。
使用带有 VPRT 的着色器并使用实例化绘图调用 stereoscopic 渲染来最大程度地减少 GPU 负载。
这还使运行时的优化能够在 HoloLens 2 上获得最佳性能。
使用纹理数组的替代方法（如双重渲染或每个眼睛单独的存在）将导致运行时后处理，这会产生严重的性能损失。

### <a name="avoid-quad-layers"></a>避免出现四个层

无需将四个层作为组合层提交 `XrCompositionLayerQuad`，而是直接将四个存在的内容呈现到投影中。

**性能警告：** 除了多个层以外，提供其他层（如四层）将导致运行时后处理，这会产生严重的性能损失。