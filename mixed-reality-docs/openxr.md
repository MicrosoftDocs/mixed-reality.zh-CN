---
title: OpenXR
description: 使用可移植 OpenXR API 标准构建引擎，并将其部署到 Windows Mixed Reality 和 HoloLens 2 耳机。
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，Mixed Reality OpenXR 开发人员门户，DirectX，本机，本机应用，自定义引擎，中间件
ms.openlocfilehash: 8140b9d3a9e1f4d2d7a25b77a48b39cb765cf6d9
ms.sourcegitcommit: 270ca09ec61e1153a83cf44942d7ba3783ef1805
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694131"
---
# <a name="openxr"></a>OpenXR

OpenXR 是来自<a href="https://www.khronos.org/" target="_blank">Khronos</a>的开放版税免费 API 标准，可提供引擎，可从多个供应商处跨[混合现实频谱](mixed-reality.md)对各种设备进行本机访问。

可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 上的 Windows Mixed 耳机上进行开发。  如果你无权访问耳机，则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。

## <a name="why-openxr"></a>为什么要 OpenXR？

借助 OpenXR，你可以构建面向全息设备（如 HoloLens 2）的引擎，该引擎将数字内容置于真实世界中，就像它确实如此，还可以提供沉浸式设备（如台式计算机的 Windows Mixed Reality 耳机）世界，并将其替换为数字体验。  OpenXR 可让你编写代码，然后在各种硬件平台上对其进行迁移。

OpenXR API 使用加载程序将应用程序直接连接到头戴显示设备的本机平台支持。  这为最终用户提供最大的性能和最小延迟，无论他们使用的是 Windows Mixed Reality 耳机还是其他任何耳机都是如此。

## <a name="what-is-openxr"></a>什么是 OpenXR？

Core OpenXR 1.0 API 提供生成引擎的基本功能，你可以将其作为一种全息设备，如 HoloLens 2 和沉浸式设备，如 Windows Mixed Reality 耳机：
* 系统 + 会话
* 引用空间（视图、本地、暂存）
* 查看配置（单声道、立体声）
* 交换链 + 帧计时
* 组合层
* 输入和 haptics
* 图形 API + 平台集成

若要了解有关 OpenXR API 的信息，请参阅 OpenXR 1.0<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">规范</a>、 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 参考</a>和<a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">快速参考指南</a>。  有关详细信息，请参阅<a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 页</a>。

若要面向一组完整的 HoloLens 2 功能，还将使用跨供应商和供应商特定的 OpenXR 扩展，这些扩展启用 OpenXR 1.0 核心之外的其他功能，例如已表述的手动跟踪、目视跟踪、空间映射和空间锚。  请参阅下面的 "[规划" 部分](openxr.md#roadmap)，了解有关今年晚些扩展的详细信息。

请注意，OpenXR 本身并不是混合现实引擎。  相反，OpenXR 使 Unity 和 Unreal 等引擎可以编写可移植代码一次，这样就可以访问用户的全息或沉浸式设备的本机平台功能，而不管哪个供应商构建了该平台。

## <a name="getting-started-with-openxr-for-hololens-2"></a>针对 HoloLens 2 的 OpenXR 入门

开始开发适用于 HoloLens 2 的 OpenXR 应用程序：

1. 设置 HoloLens 2 或按照说明[安装 hololens 2 模拟器](using-the-hololens-emulator.md)。
1. 从设备或模拟器中启动应用商店应用，并确保更新所有应用。  这将确保你的 HoloLens 上的 OpenXR 运行时更新为 OpenXR 1.0。  如果使用模拟器，你将需要咨询[模拟器输入说明](using-the-hololens-emulator.md#basic-emulator-input)，以帮助你在模拟器内使用应用商店应用。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>OpenXR for Windows Mixed Reality 耳机入门

开始为沉浸式 Windows Mixed Reality 耳机开发 OpenXR 应用程序：

1. 请确保运行 Windows 10 2019 更新（1903），这是 Windows Mixed Reality 最终用户运行 OpenXR 应用程序的最低要求。  如果你使用的是早期版本的 Windows 10，则可以使用<a href="https://www.microsoft.com//software-download/windows10" target="_blank">Windows 10 更新助手</a>升级到5月2019更新。  如果无法更新您的 PC，还可以[使用 Windows 10 10 月2018版（1809）开发 OpenXR 应用程序](openxr.md#developing-on-windows-10-october-2018-update)，不过您可能会遇到性能下降或其他问题。
2. 设置 Windows Mixed Reality 耳机，或按照说明[启用 Windows Mixed reality 模拟器](using-the-windows-mixed-reality-simulator.md)。  设置 Windows Mixed Reality 后，混合现实门户会自动安装 Windows Mixed Reality OpenXR 运行时。  然后，Microsoft Store 会使运行时保持最新状态。
3. 通过从 "开始" 菜单启动混合现实门户，并单击 .。。菜单，然后选择 "设置 OpenXR"。<br>
![在混合现实门户中设置 OpenXR](images/mixed-reality-portal-set-up-openxr.png)

如果需要让 Windows Mixed Reality OpenXR 运行时再次激活，请重复步骤3。

> [!NOTE]
> 系统很快会自动为所有 Windows Mixed Reality 最终用户设置 Windows Mixed Reality OpenXR 运行时。

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>获取混合现实 OpenXR 开发人员门户

若要尝试 Windows Mixed Reality OpenXR 运行时，可以安装<a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">[Mixed Reality OpenXR 开发人员门户应用程序</a>。  此应用程序提供了演示 OpenXR 的各种功能的演示场景，同时提供了一个系统状态页，其中提供了有关活动运行时和当前耳机的关键信息。

![混合现实 OpenXR 开发人员门户应用](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>生成示例 OpenXR 应用

<a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>项目演示了一个简单的 OpenXR 示例，其中包含两个 Visual Studio 项目文件，一个用于 Win32 桌面应用，另一个用于 UWP HoloLens 2 应用。  由于解决方案包含一个 HoloLens UWP 项目，因此需要在 Visual Studio 中安装[通用 Windows 平台开发工作负载](install-the-tools.md#installation-checklist)才能完全打开它。

请注意，虽然 Win32 和 UWP 项目文件是独立的，但由于打包和部署的不同，每个项目中的应用代码都是100%。

生成 OpenXR 的 Win32 桌面后。EXE，无论是 Windows Mixed Reality 耳机还是任何其他耳机，都可以在任何支持 OpenXR 的 desktop VR 平台上将它与 VR 耳机一起使用。

生成 OpenXR UWP 应用包后，可以将[该包部署](using-visual-studio.md)到 hololens 2 设备或 Hololens 2 仿真器。

## <a name="openxr-app-best-practices-for-hololens-2"></a>针对 HoloLens 2 的 OpenXR 应用最佳实践

可在 BasicXrApp 的[OpenXRProgram](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp)文件中查看以下最佳实践的示例。 开始时，Run （）函数从初始化到事件和呈现循环捕获典型的 OpenXR 应用代码流。

### <a name="select-a-swapchain-format"></a>选择存在格式

始终使用 `xrEnumerateSwapchainFormats`枚举受支持的像素格式，并从应用程序支持的运行时选择第一种颜色和深度像素格式，因为这是运行时首选的。 请注意，在 HoloLens 2 上，`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 和 `DXGI_FORMAT_D16_UNORM` 通常是实现更好的呈现性能的第一选择。 在台式计算机上运行的 VR 耳机上，此首选项可能有所不同。  
  
**性能警告：** 使用不是主存在颜色格式的格式将导致运行时后处理，这会产生严重的性能损失。

### <a name="gamma-correct-rendering"></a>伽玛正确的呈现

尽管这适用于所有 OpenXR 运行时，但必须注意确保呈现管道是伽玛正确的。 在呈现到存在时，呈现目标视图格式应与存在格式（例如，存在格式和呈现目标视图 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB）匹配。
例外情况是，应用程序的呈现管道在着色器代码中执行手动的 sRGB 转换，在这种情况下，应用程序应请求 sRGB 存在格式，但使用线性格式作为呈现目标视图（例如，request DXGI_FORMAT_B8G8R8A8_UNORM_SRGB存在格式，但使用 DXGI_FORMAT_B8G8R8A8_UNORM 作为呈现目标视图）以防止内容被更正为双精度。

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

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>使用建议的呈现参数和帧计时进行呈现

始终使用推荐的视图配置宽度/高度（`recommendedImageRectWidth` 和 `recommendedImageRectHeight` `XrViewConfigurationView`）进行呈现，并且始终使用 `xrLocateViews` API 在呈现之前查询建议的视图 fov、和其他呈现参数。
查询姿势和视图时，请始终使用最新 `xrWaitFrame` 调用中的 `XrFrameEndInfo.predictedDisplayTime`。
这允许 HoloLens 为正在戴上的 HoloLens 的人员调整呈现和优化视觉质量。

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

### <a name="avoid-quad-layers"></a>避免出现四个层

无需将四个层作为组合层提交 `XrCompositionLayerQuad`，而是直接将四个存在的内容呈现到投影中。

**性能警告：** 除了多个层以外，提供其他层（如四层）将导致运行时后处理，这会产生严重的性能损失。

## <a name="openxr-app-performance-on-hololens-2"></a>HoloLens 2 上的 OpenXR 应用程序性能

在 HoloLens 2 上，有多种方法可通过 `xrEndFrame` 提交组合数据，这会导致后期处理，这将导致性能显著下降。
若要避免性能 penalities，请提交具有以下特征的[单个 `XrCompositionProjectionLayer`](#use-a-single-projection-layer) ：
* [使用纹理数组存在](#render-with-texture-array-and-vprt)
* [使用主要颜色存在格式](#select-a-swapchain-format)
* [使用建议的视图维度](#render-with-recommended-rendering-parameters-and-frame-timing)
* 不设置 `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 标志
* 将 `XrCompositionLayerDepthInfoKHR` `minDepth` 设置为 0.0 f，并 `maxDepth` 设置为 1.0 f

其他注意事项将导致更好的性能：
* [使用16位深度格式](#choose-a-reasonable-depth-range)
* [进行实例化绘图调用](#render-with-texture-array-and-vprt)

## <a name="roadmap"></a>路线图

OpenXR 规范定义了一种扩展机制，它使运行时实现程序能够公开超出<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">基本 OpenXR 1.0 规范</a>中定义的[核心功能](openxr.md#what-is-openxr)的其他功能。

有三种类型的 OpenXR 扩展：
* **供应商扩展（例如 MSFT）：** 启用硬件或软件功能中的每个供应商创新。  任何运行时供应商随时都可以引入和交付供应商扩展。
* **扩展插件：** 多个公司定义和实现的跨供应商扩展。  一组感兴趣的公司随时可以引入扩展扩展。
* **KHR 扩展：** 正式 Khronos 扩展作为核心规范版本的一部分而被批准。  KHR 扩展与核心规范本身具有相同的许可证。

一年结束后，Windows Mixed Reality OpenXR 运行时将支持一组 MSFT 和 EXT 扩展，这些扩展将整套 HoloLens 2 功能引入 OpenXR 应用程序：
* [未绑定的参考空间（全球范围体验）](coordinate-systems.md#building-a-world-scale-experience)
* [空间锚 + 存储](spatial-anchors.md)
* [手型 articulation + 手写网格](hands-and-tools.md)
* [眼睛凝视](eye-tracking.md)
* [辅助视图配置（混合现实捕获）](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [场景理解](scene-understanding.md)
* 与 Windows SDK Api 互操作

尽管其中一些扩展可能会作为特定于供应商的 MSFT 扩展而开始，但 Microsoft 和其他 OpenXR 运行时供应商正在协同工作，为许多这些功能领域设计跨供应商 EXT 或 KHR 扩展。  这将使你为这些功能编写的代码可在运行时供应商之间移植，就像核心规范一样。

## <a name="troubleshooting"></a>“疑难解答”

下面是一些 Windows Mixed Reality OpenXR 运行时的故障排除提示。  如果你有关于<a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>的任何其他问题，请访问<a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 论坛</a>或<a href="https://khr.io/slack" target="_blank">时差 #openxr 频道</a>。

### <a name="developing-on-windows-10-october-2018-update"></a>在 Windows 10 10 月2018更新上进行开发

如果无法将[开发电脑升级到 "2019 年5月更新版" 更新](https://www.microsoft.com//software-download/windows10)，可以通过执行以下一项操作来设置 Windows 10 10 月版2018更新（1809） PC 进行开发：

1. 按照上述步骤开始在台式计算机上 OpenXR。
1. 若要将 Windows Mixed Reality OpenXR 运行时设置为系统的活动 OpenXR 运行时，请安装[Windows Mixed Reality OpenXR Developer 兼容包](https://aka.ms/openxr-compat)。

> [!NOTE]
> 尽管在开发 OpenXR 应用程序时可以使用 Windows 10 十月2018更新（1809），但对于最终用户来说，Windows 10 可能2019更新（1903）是最终用户在 Windows Mixed Reality 中使用 OpenXR 的最低要求。  在 10 2018 月的更新中运行 OpenXR 应用程序时，可能会遇到性能下降或其他问题。  强烈建议将开发 PC 升级到 Windows 10 2019 更新（1903）。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR 应用未启动 Windows Mixed Reality

如果 OpenXR 应用在运行时未启动 Windows Mixed Reality，则 Windows Mixed Reality OpenXR 运行时可能不会设置为活动运行时。  请务必遵循上述说明，了解如何[开始 OpenXR For Windows Mixed Reality 耳机](#getting-started-with-openxr-for-windows-mixed-reality-headsets)，使运行时处于活动状态。

还可以运行[混合现实 OpenXR 开发人员门户](#getting-the-mixed-reality-openxr-developer-portal)，以获取有关系统上 Windows Mixed Reality OpenXR 运行时状态的其他故障排除帮助。

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>混合现实门户未显示 "设置 OpenXR" 菜单项

请确保至少运行 Windows 10 十月2018更新（1809）。  如果使用的是早期版本的 Windows 10，则可以使用[windows 10 更新助手](https://www.microsoft.com//software-download/windows10)升级到2019更新（1903）。

如果你的混合现实门户应用的版本较旧，"设置 OpenXR" 菜单项可能不可用。  检查[混合现实门户应用更新](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m)以确保具有最新版本。

请注意，如果已安装并激活 Windows Mixed Reality OpenXR 运行时，则不会显示 "设置 OpenXR" 菜单项。  可以安装[混合现实 OpenXR 开发人员门户](#getting-the-mixed-reality-openxr-developer-portal)来确定系统上 OpenXR 运行时的当前状态。

## <a name="see-also"></a>另请参阅

* <a href="https://www.khronos.org/openxr/" target="_blank">有关 OpenXR 的详细信息</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 规范</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 参考</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 快速参考指南</a>
