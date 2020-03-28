---
title: OpenXR 最佳实践
description: 了解 OpenXR 应用程序的视觉质量、稳定性和性能的最佳实践。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，DirectX，本机，本机应用，自定义引擎，中间件，最佳做法，性能，质量，稳定性
ms.openlocfilehash: c0ddbd0604760ccae34d347e93b918be4aead269
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362014"
---
# <a name="openxr-app-best-practices"></a><span data-ttu-id="9bf4d-104">OpenXR 应用最佳实践</span><span class="sxs-lookup"><span data-stu-id="9bf4d-104">OpenXR app best practices</span></span>

<span data-ttu-id="9bf4d-105">可在<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>的 OpenXRProgram 文件中查看以下最佳实践的示例。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-105">You can see an example of the best practices below in <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>'s OpenXRProgram.cpp file.</span></span> <span data-ttu-id="9bf4d-106">开始时，Run （）函数从初始化到事件和呈现循环捕获典型的 OpenXR 应用代码流。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-106">The Run() function at the beginning captures a typical OpenXR app code flow from initialization to the event and rendering loop.</span></span>

## <a name="best-practices-for-visual-quality-and-stability"></a><span data-ttu-id="9bf4d-107">视觉质量和稳定性的最佳实践</span><span class="sxs-lookup"><span data-stu-id="9bf4d-107">Best practices for visual quality and stability</span></span>

<span data-ttu-id="9bf4d-108">本节中的最佳实践介绍了如何在任何 OpenXR 应用程序中获得最佳视觉质量和稳定性。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-108">The best practices in this section describe how to get the best visual quality and stability in any OpenXR application.</span></span>

<span data-ttu-id="9bf4d-109">有关特定于 HoloLens 2 的更多性能建议，请参阅下面的 " [hololens 2 的最佳性能方案](#best-practices-for-performance-on-hololens-2)" 部分。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-109">For further performance recommendations specific to HoloLens 2, see the [Best practices for performance on HoloLens 2](#best-practices-for-performance-on-hololens-2) section below.</span></span>

### <a name="gamma-correct-rendering"></a><span data-ttu-id="9bf4d-110">伽玛正确的呈现</span><span class="sxs-lookup"><span data-stu-id="9bf4d-110">Gamma-correct rendering</span></span>

<span data-ttu-id="9bf4d-111">必须小心，以确保您的渲染管道为伽玛正确。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-111">Care must be taken to ensure that your rendering pipeline is gamma-correct.</span></span> <span data-ttu-id="9bf4d-112">在呈现到存在时，呈现目标视图格式应与存在格式（例如，存在格式和呈现目标视图 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB）匹配。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-112">When rendering to a swapchain, the render-target view format should match the swapchain format (e.g. DXGI_FORMAT_B8G8R8A8_UNORM_SRGB for both the swapchain format and the render-target view).</span></span>
<span data-ttu-id="9bf4d-113">例外情况是，应用程序的呈现管道在着色器代码中执行手动的 sRGB 转换，在这种情况下，应用程序应请求 sRGB 存在格式，但使用线性格式作为呈现目标视图（例如，request DXGI_FORMAT_B8G8R8A8_UNORM_SRGB存在格式，但使用 DXGI_FORMAT_B8G8R8A8_UNORM 作为呈现目标视图）以防止内容被更正为双精度。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-113">The exception is if the app's rendering pipeline does a manual sRGB conversion in shader code, in which case the app should request an sRGB swapchain format but use the linear format for the render-target view (e.g. request DXGI_FORMAT_B8G8R8A8_UNORM_SRGB as the swapchain format but use DXGI_FORMAT_B8G8R8A8_UNORM as the render-target view) to prevent content from being double-gamma corrected.</span></span>

### <a name="submit-depth-buffer-for-projection-layers"></a><span data-ttu-id="9bf4d-114">提交用于投影层的深度缓冲区</span><span class="sxs-lookup"><span data-stu-id="9bf4d-114">Submit depth buffer for projection layers</span></span>

<span data-ttu-id="9bf4d-115">提交帧到 `xrEndFrame`时，请始终使用 `XR_KHR_composition_layer_depth` 扩展，并随投影层一起提交深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-115">Always use `XR_KHR_composition_layer_depth` extension and submit the depth buffer together with the projection layer when submitting a frame to `xrEndFrame`.</span></span>
<span data-ttu-id="9bf4d-116">这可以通过在 HoloLens 2 上启用硬件深度 reprojection 来改善全息影像的稳定性。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-116">This improves hologram stability by enabling hardware depth reprojection on HoloLens 2.</span></span>

### <a name="choose-a-reasonable-depth-range"></a><span data-ttu-id="9bf4d-117">选择合理的深度范围</span><span class="sxs-lookup"><span data-stu-id="9bf4d-117">Choose a reasonable depth range</span></span>

<span data-ttu-id="9bf4d-118">首选较窄的深度范围来确定虚拟内容的作用域，以帮助在 HoloLens 上对虚拟目录进行稳定性。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-118">Prefer a narrower depth range to scope the virtual content to help hologram stability on HoloLens.</span></span>
<span data-ttu-id="9bf4d-119">例如，OpenXrProgram 示例使用0.1 到20米。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-119">For example, the OpenXrProgram.cpp sample is using 0.1 to 20 meters.</span></span>
<span data-ttu-id="9bf4d-120">使用[反向-Z](https://developer.nvidia.com/content/depth-precision-visualized)以获得更统一的深度解析。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-120">Use [reversed-Z](https://developer.nvidia.com/content/depth-precision-visualized) for a more uniform depth resolution.</span></span>
<span data-ttu-id="9bf4d-121">请注意，在 HoloLens 2 上，使用首选 `DXGI_FORMAT_D16_UNORM` 深度格式将有助于获得更好的帧速率和性能，不过，16位深度缓冲区提供的分辨率低于24位深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-121">Note that, on HoloLens 2, using the preferred `DXGI_FORMAT_D16_UNORM` depth format will help achieve better frame rate and performance, although 16-bit depth buffers provide less depth resolution than 24-bit depth buffers.</span></span>
<span data-ttu-id="9bf4d-122">因此，遵循这些最佳做法，充分利用深度解析变得更加重要。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-122">Therefore, following these best practices to make best use of the depth resolution becomes more important.</span></span>

### <a name="prepare-for-different-environment-blend-modes"></a><span data-ttu-id="9bf4d-123">针对不同的环境混合模式做好准备</span><span class="sxs-lookup"><span data-stu-id="9bf4d-123">Prepare for different environment blend modes</span></span>

<span data-ttu-id="9bf4d-124">如果你的应用程序也将在完全堵塞世界的沉浸式耳机上运行，请确保使用 `xrEnumerateEnvironmentBlendModes` API 枚举支持的环境混合模式，并相应地准备呈现内容。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-124">If your application will also run on immersive headsets that completely block out the world, be sure to enumerate supported environment blend modes using `xrEnumerateEnvironmentBlendModes` API, and prepare your rendering content accordingly.</span></span>
<span data-ttu-id="9bf4d-125">例如，对于具有 `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` 的系统（如 HoloLens），应用应使用透明的颜色作为清晰的颜色，而对于具有 `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`的系统，应用应在后台呈现一些不透明颜色或某些虚拟空间。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-125">For example, for a system with `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` such as the HoloLens, the app should use transparent as the clear color, while for a system with `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`, the app should render some opaque color or some virtual room in the background.</span></span>

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a><span data-ttu-id="9bf4d-126">选择未绑定的引用空间作为应用程序的根空间</span><span class="sxs-lookup"><span data-stu-id="9bf4d-126">Choose unbounded reference space as application's root space</span></span>

<span data-ttu-id="9bf4d-127">应用程序通常会建立一些根世界坐标空间，以便将视图、操作和全息连接在一起。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-127">Applications typically establish some root world coordinate space to connect views, actions and holograms together.</span></span>
<span data-ttu-id="9bf4d-128">当支持扩展以建立[全球范围的坐标系统](coordinate-systems.md#building-a-world-scale-experience)时，可使用 `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT`，使应用能够避免在用户从应用启动的位置移到远处（如5米以外）时出现意外的全息影像偏移。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-128">Use `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` when the extension is supported to establish a [world-scale coordinate system](coordinate-systems.md#building-a-world-scale-experience), enabling your app to avoid undesired hologram drift when the user moves far (e.g. 5 meters away) from where the app starts.</span></span>
<span data-ttu-id="9bf4d-129">如果未绑定的空间扩展不存在，请使用 `XR_REFERENCE_SPACE_TYPE_LOCAL` 作为回退。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-129">Use `XR_REFERENCE_SPACE_TYPE_LOCAL` as a fallback if the unbounded space extension doesn't exist.</span></span>

### <a name="associate-hologram-with-spatial-anchor"></a><span data-ttu-id="9bf4d-130">将全息图与空间定位关联</span><span class="sxs-lookup"><span data-stu-id="9bf4d-130">Associate hologram with spatial anchor</span></span>

<span data-ttu-id="9bf4d-131">使用未绑定的引用空间时，在该引用空间中直接放置的全息影像[可能会在用户进入远处房间后进入远处，并返回](coordinate-systems.md#building-a-world-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-131">When using an unbounded reference space, holograms you place directly in that reference space [may drift as the user walks to distant rooms and then comes back](coordinate-systems.md#building-a-world-scale-experience).</span></span>
<span data-ttu-id="9bf4d-132">对于全息图用户在世界各地的不同位置，请使用 `xrCreateSpatialAnchorSpaceMSFT` extension 函数[创建空间锚](spatial-anchors.md#best-practices)，并将全息影像置于其原点。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-132">For hologram users place at a discrete location in the world, [create a spatial anchor](spatial-anchors.md#best-practices) using the `xrCreateSpatialAnchorSpaceMSFT` extension function and position the hologram at its origin.</span></span>
<span data-ttu-id="9bf4d-133">这会使全息图在一段时间内独立稳定。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-133">That will keep that hologram independently stable over time.</span></span>

### <a name="support-mixed-reality-capture"></a><span data-ttu-id="9bf4d-134">支持混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="9bf4d-134">Support mixed reality capture</span></span>

<span data-ttu-id="9bf4d-135">尽管 HoloLens 2 的主显示器使用加法环境混合，但当用户启动[混合现实捕获](mixed-reality-capture-for-developers.md)时，应用的呈现内容将与环境视频流进行 alpha 混合。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-135">Although HoloLens 2's primary display uses additive environment blending, when the user initiates [mixed reality capture](mixed-reality-capture-for-developers.md), the app's rendering content will be alpha-blended with the environment video stream.</span></span>
<span data-ttu-id="9bf4d-136">若要在混合现实中获得最佳视觉质量捕获视频，最好将 `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` 设置在投影层的 `layerFlags`中。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-136">To achieve the best visual quality in mixed reality capture videos, it's best to set the `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` in your projection layer's `layerFlags`.</span></span>

## <a name="best-practices-for-performance-on-hololens-2"></a><span data-ttu-id="9bf4d-137">HoloLens 2 上性能最佳方案</span><span class="sxs-lookup"><span data-stu-id="9bf4d-137">Best practices for performance on HoloLens 2</span></span>

<span data-ttu-id="9bf4d-138">作为提供硬件 reprojection 支持的移动设备，HoloLens 2 对获得最佳性能的要求更严格。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-138">As a mobile device with hardware reprojection support, HoloLens 2 has stricter requirements to obtain optimal performance.</span></span>  <span data-ttu-id="9bf4d-139">有多种方法可通过 `xrEndFrame` 提交组合数据，这会导致后期处理，这将导致性能显著下降。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-139">There are a number of ways to submit composition data through `xrEndFrame` which will result in post-processing that will have a noticeable performance penalty.</span></span>

### <a name="select-a-swapchain-format"></a><span data-ttu-id="9bf4d-140">选择存在格式</span><span class="sxs-lookup"><span data-stu-id="9bf4d-140">Select a swapchain format</span></span>

<span data-ttu-id="9bf4d-141">始终使用 `xrEnumerateSwapchainFormats`枚举受支持的像素格式，并选择应用程序支持的运行时中的第一种颜色和深度像素格式，因为这是运行时首选的，以实现最佳性能。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-141">Always enumerate supported pixel formats using `xrEnumerateSwapchainFormats`, and choose the first color and depth pixel format from the runtime that the app supports, because that's what the runtime prefers for optimal performance.</span></span> <span data-ttu-id="9bf4d-142">请注意，在 HoloLens 2 上，`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 和 `DXGI_FORMAT_D16_UNORM` 通常是实现更好的呈现性能的第一选择。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-142">Note, on HoloLens 2, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` and `DXGI_FORMAT_D16_UNORM` is typically the first choice to achieve better rendering performance.</span></span> <span data-ttu-id="9bf4d-143">在台式计算机上运行的 VR 耳机上，此首选项可能有所不同，其中24位深度缓冲区的性能影响较低。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-143">This preference can be different on VR headsets running on a Desktop PC, where 24-bit depth buffers have less of a performance impact.</span></span>
  
<span data-ttu-id="9bf4d-144">**性能警告：** 使用不是主存在颜色格式的格式将导致运行时后处理，这会产生严重的性能损失。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-144">**Performance Warning:** Using a format other than the primary swapchain color format will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a><span data-ttu-id="9bf4d-145">使用建议的呈现参数和帧计时进行呈现</span><span class="sxs-lookup"><span data-stu-id="9bf4d-145">Render with recommended rendering parameters and frame timing</span></span>

<span data-ttu-id="9bf4d-146">始终使用推荐的视图配置宽度/高度（`recommendedImageRectWidth` 和 `recommendedImageRectHeight` `XrViewConfigurationView`）进行呈现，并且始终使用 `xrLocateViews` API 在呈现之前查询建议的视图 fov、和其他呈现参数。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-146">Always render with the recommended view configuration width/height (`recommendedImageRectWidth` and `recommendedImageRectHeight` from `XrViewConfigurationView`), and always use `xrLocateViews` API to query for the recommended view pose, fov, and other rendering parameters before rendering.</span></span>
<span data-ttu-id="9bf4d-147">查询姿势和视图时，请始终使用最新 `xrWaitFrame` 调用中的 `XrFrameEndInfo.predictedDisplayTime`。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-147">Always use the `XrFrameEndInfo.predictedDisplayTime` from the latest `xrWaitFrame` call when querying for poses and views.</span></span>
<span data-ttu-id="9bf4d-148">这允许 HoloLens 为正在戴上的 HoloLens 的人员调整呈现和优化视觉质量。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-148">This allows HoloLens to adjust rendering and optimize visual quality for the person who is wearing the HoloLens.</span></span>

### <a name="use-a-single-projection-layer"></a><span data-ttu-id="9bf4d-149">使用单个投影层</span><span class="sxs-lookup"><span data-stu-id="9bf4d-149">Use a single projection layer</span></span>

<span data-ttu-id="9bf4d-150">HoloLens 2 为应用程序提供了有限的 GPU 能力，可让应用程序呈现内容和针对单个投影层优化的硬件组合器。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-150">HoloLens 2 has limited GPU power for applications to render content and a hardware compositor optimized for a single projection layer.</span></span>
<span data-ttu-id="9bf4d-151">始终使用单个投影层可帮助应用程序的帧速率、全息图稳定性和视觉质量。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-151">Always using a single projection layer can help the application's framerate, hologram stability and visual quality.</span></span>  
  
<span data-ttu-id="9bf4d-152">**性能警告：** 提交任何内容，但只有一个保护层会导致运行时后处理，这会产生严重的性能损失。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-152">**Performance Warning:** Submitting anything but a single protection layer will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="render-with-texture-array-and-vprt"></a><span data-ttu-id="9bf4d-153">用纹理数组和 VPRT 进行呈现</span><span class="sxs-lookup"><span data-stu-id="9bf4d-153">Render with texture array and VPRT</span></span>

<span data-ttu-id="9bf4d-154">使用 `arraySize=2` 颜色存在和深度，为左右眼睛创建一个 `xrSwapchain`。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-154">Create one `xrSwapchain` for both left and right eye using `arraySize=2` for color swapchain, and one for depth.</span></span>
<span data-ttu-id="9bf4d-155">将视觉眼睛渲染为切片0，将视觉眼睛转换为切片1。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-155">Render the left eye into slice 0 and the right eye into slice 1.</span></span>
<span data-ttu-id="9bf4d-156">使用带有 VPRT 的着色器并使用实例化绘图调用 stereoscopic 渲染来最大程度地减少 GPU 负载。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-156">Use a shader with VPRT and instanced draw calls for stereoscopic rendering to minimize GPU load.</span></span>
<span data-ttu-id="9bf4d-157">这还使运行时的优化能够在 HoloLens 2 上获得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-157">This also enables the runtime's optimization to achieve the best performance on HoloLens 2.</span></span>
<span data-ttu-id="9bf4d-158">使用纹理数组的替代方法（如双重渲染或每个眼睛单独的存在）将导致运行时后处理，这会产生严重的性能损失。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-158">Alternatives to using a texture array, such as double-wide rendering or a separate swapchain per eye, will result in runtime post-processing which comes at a significant performance penalty.</span></span>

### <a name="avoid-quad-layers"></a><span data-ttu-id="9bf4d-159">避免出现四个层</span><span class="sxs-lookup"><span data-stu-id="9bf4d-159">Avoid quad layers</span></span>

<span data-ttu-id="9bf4d-160">无需将四个层作为组合层提交 `XrCompositionLayerQuad`，而是直接将四个存在的内容呈现到投影中。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-160">Rather than submitting quad layers as composition layers with `XrCompositionLayerQuad`, render the quad content directly into the projection swapchain.</span></span>

<span data-ttu-id="9bf4d-161">**性能警告：** 除了多个层以外，提供其他层（如四层）将导致运行时后处理，这会产生严重的性能损失。</span><span class="sxs-lookup"><span data-stu-id="9bf4d-161">**Performance Warning:** Providing additional layers beyond a single projection layer, such as quad layers, will result in runtime post-processing which comes at a significant performance penalty.</span></span>