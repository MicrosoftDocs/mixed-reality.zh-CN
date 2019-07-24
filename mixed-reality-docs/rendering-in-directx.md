---
title: 在 DirectX 中呈现
description: 介绍适用于 Windows Mixed Reality 的全息着色。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 全息影像, 呈现, 3D 图形, HolographicFrame, render 循环, 更新循环, 演练, 示例代码
ms.openlocfilehash: 6edcaf808f2d7d48f480169e5579adb8984678a0
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629033"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="ad2aa-104">在 DirectX 中呈现</span><span class="sxs-lookup"><span data-stu-id="ad2aa-104">Rendering in DirectX</span></span>

<span data-ttu-id="ad2aa-105">Windows Mixed Reality 建立在 DirectX 之上, 为用户生成丰富的3D 图形体验。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="ad2aa-106">呈现抽象只是在 DirectX 之上, 并使应用程序可以根据系统的预测, 为一个或多个全息场景的一个或多个观察程序的位置和方向。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="ad2aa-107">然后, 开发人员可以相对于每个相机找到其全息影像, 让应用在用户四处移动时在各种空间坐标系统中呈现这些全息影像。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="ad2aa-108">更新当前帧</span><span class="sxs-lookup"><span data-stu-id="ad2aa-108">Update for the current frame</span></span>

<span data-ttu-id="ad2aa-109">若要更新全息影像的应用程序状态, 每帧一次, 应用将:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="ad2aa-110">从显示管理系统中获取<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="ad2aa-111">将场景更新为当前预测, 即在完成呈现时相机视图将在何处。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="ad2aa-112">请注意, 全息场景可以有多个相机。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="ad2aa-113">若要呈现到全息相机视图, 每帧一次, 应用将:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="ad2aa-114">对于每个照相机, 使用系统中的相机视图和投影矩阵呈现当前帧的场景。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="ad2aa-115">创建新的全息帧并获取其预测</span><span class="sxs-lookup"><span data-stu-id="ad2aa-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="ad2aa-116"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>包含应用程序更新和呈现当前帧所需的信息。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="ad2aa-117">应用通过调用**CreateNextFrame**方法, 开始每个新帧。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="ad2aa-118">调用此方法时, 将使用可用的最新传感器数据, 并将其封装在**CurrentPrediction**对象中。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="ad2aa-119">对于每个呈现的帧, 都必须使用新的帧对象, 因为它仅对即时时间有效。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="ad2aa-120">**CurrentPrediction**属性包含照相机位置等信息。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="ad2aa-121">该信息将被推入到帧应向用户显示的确切时刻。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="ad2aa-122">下面的代码从**AppMain:: Update**摘录内容:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="ad2aa-123">处理照相机更新</span><span class="sxs-lookup"><span data-stu-id="ad2aa-123">Process camera updates</span></span>

<span data-ttu-id="ad2aa-124">后台缓冲区可以从帧更改为帧。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="ad2aa-125">应用需要验证每个照相机的后台缓冲区, 并根据需要释放并重新创建资源视图和深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="ad2aa-126">请注意, 预测中的姿势集是当前帧中所使用的相机的权威列表。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="ad2aa-127">通常, 使用此列表来循环访问相机集。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="ad2aa-128">From **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="ad2aa-129">From **DeviceResources:: EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="ad2aa-130">获取坐标系统作为渲染的基础</span><span class="sxs-lookup"><span data-stu-id="ad2aa-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="ad2aa-131">Windows Mixed Reality 使你的应用能够根据需要创建各种[坐标系统](coordinate-systems-in-directx.md), 例如, 在物理世界中跟踪位置的附加参考框架和固定参考框架。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="ad2aa-132">然后, 你的应用程序可以使用这些坐标系统来考虑在何处呈现每个帧的全息影像。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="ad2aa-133">从 API 请求坐标时, 始终会传入要在其中表示这些坐标的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> 。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="ad2aa-134">From **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="ad2aa-135">然后, 可以使用这些坐标系统在场景中呈现内容时生成立体声视图矩阵。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="ad2aa-136">From **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="ad2aa-137">处理注视和手势输入</span><span class="sxs-lookup"><span data-stu-id="ad2aa-137">Process gaze and gesture input</span></span>

<span data-ttu-id="ad2aa-138">"[注视](gaze-in-directx.md)" 和 "[手](hands-and-motion-controllers-in-directx.md)输入" 不是基于时间的, 因此不需要在**StepTimer**函数中更新。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-138">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="ad2aa-139">但是, 此输入是应用程序需要查看每个帧的内容。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-139">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="ad2aa-140">处理基于时间的更新</span><span class="sxs-lookup"><span data-stu-id="ad2aa-140">Process time-based updates</span></span>

<span data-ttu-id="ad2aa-141">任何实时渲染应用程序都需要某种方式来处理基于时间的更新;我们提供了一种通过**StepTimer**实现在 Windows 全息应用程序模板中执行此操作的方法。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="ad2aa-142">这类似于 DirectX 11 UWP 应用模板中提供的 StepTimer, 因此, 如果你已经了解了该模板, 则应熟悉这一点。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="ad2aa-143">此 StepTimer 示例 helper 类能够提供固定的时间步长更新以及可变的时间更新, 而默认模式是可变的时间步骤。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="ad2aa-144">对于全息渲染, 我们特别选择不将过多的内容放入计时器函数。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="ad2aa-145">这是因为您可以将其配置为固定时间步骤, 在这种情况下, 对于某些帧, 可能会多次调用它, 或者根本不会对某些帧调用一次, 我们的全息数据更新对于每个帧都应该发生一次。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="ad2aa-146">From **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="ad2aa-147">在坐标系统中定位和旋转全息影像</span><span class="sxs-lookup"><span data-stu-id="ad2aa-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="ad2aa-148">如果您在单个坐标系中操作, 则在使用**SpatialStationaryReferenceFrame**时, 此过程与在3d 图形中的使用方式不同。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="ad2aa-149">在这里, 我们将旋转多维数据集, 并将模型矩阵设置为相对于固定坐标系统中的位置。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="ad2aa-150">From **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-150">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="ad2aa-151">**有关高级方案的说明:** 旋转多维数据集是一个非常简单的示例, 说明如何在单个引用框架中放置全息图。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="ad2aa-152">还可以同时在同一个呈现的帧中[使用多个 SpatialCoordinateSystems](coordinate-systems-in-directx.md) 。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="ad2aa-153">更新常量缓冲区数据</span><span class="sxs-lookup"><span data-stu-id="ad2aa-153">Update constant buffer data</span></span>

<span data-ttu-id="ad2aa-154">内容的模型转换照常更新。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="ad2aa-155">现在, 你将为要在中呈现的坐标系统计算有效转换。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="ad2aa-156">From **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-156">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="ad2aa-157">视图和投影转换是怎样的？</span><span class="sxs-lookup"><span data-stu-id="ad2aa-157">What about view and projection transforms?</span></span> <span data-ttu-id="ad2aa-158">为了获得最佳效果, 我们要等待, 直到我们为绘图调用做了准备。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="ad2aa-159">呈现当前帧</span><span class="sxs-lookup"><span data-stu-id="ad2aa-159">Render the current frame</span></span>

<span data-ttu-id="ad2aa-160">在 Windows Mixed Reality 上呈现与在二维 mono 显示上呈现不同, 但需要注意一些差异:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="ad2aa-161">全息帧预测很重要。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="ad2aa-162">对于帧显示后的预测越接近, 全息影像的外观就越好。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="ad2aa-163">Windows Mixed Reality 控制相机视图。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="ad2aa-164">您需要呈现每个文件, 因为全息帧会在以后向您演示。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="ad2aa-165">建议使用为 render 目标数组使用实例化绘图来完成立体声渲染。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="ad2aa-166">全息应用模板使用推荐的方法将绘图转换为呈现目标数组, 该数组使用呈现器目标视图到**Texture2DArray**。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="ad2aa-167">如果要在不使用立体声实例的情况下进行呈现, 则需要创建两个非数组 RenderTargetViews (每个眼睛各有一个), 其中每个都引用系统中为应用提供的**Texture2DArray**中的两个扇区之一。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="ad2aa-168">不建议这样做, 因为通常比使用实例化要慢得多。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="ad2aa-169">获取更新的 HolographicFrame 预测</span><span class="sxs-lookup"><span data-stu-id="ad2aa-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="ad2aa-170">更新帧预测可增强图像稳定性的有效性, 并允许更准确地定位全息影像, 因为预测与帧对用户可见的时间更短。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="ad2aa-171">理想情况下, 只需在呈现之前更新帧预测。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="ad2aa-172">呈现到每个照相机</span><span class="sxs-lookup"><span data-stu-id="ad2aa-172">Render to each camera</span></span>

<span data-ttu-id="ad2aa-173">循环中的一组照相机姿势, 并呈现到此集中的每个照相机。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="ad2aa-174">**设置呈现阶段**</span><span class="sxs-lookup"><span data-stu-id="ad2aa-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="ad2aa-175">Windows Mixed Reality 使用 stereoscopic 渲染来增强深度的错觉并渲染 stereoscopically, 使左侧和右侧显示都处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="ad2aa-176">对于 stereoscopic 渲染, 这两个显示器之间有一个偏移, 大脑可与实际深度进行协调。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="ad2aa-177">本部分介绍使用实例化的 stereoscopic 呈现, 使用 Windows 全息应用程序模板中的代码。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="ad2aa-178">每个照相机都有其自己的呈现目标 (后台缓冲区) 和视图和投影矩阵。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="ad2aa-179">您的应用程序将需要创建任何其他基于照相机的资源, 例如, 每个相机的深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="ad2aa-180">在 Windows 全息版应用程序模板中, 我们提供了一个帮助器类, 用于将这些资源捆绑到 DX:: CameraResources 中。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="ad2aa-181">首先设置呈现目标视图:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="ad2aa-182">From **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-182">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="ad2aa-183">**使用预测获取照相机的视图和投影矩阵**</span><span class="sxs-lookup"><span data-stu-id="ad2aa-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="ad2aa-184">每个全息相机的视图和投影矩阵将随每个帧发生变化。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="ad2aa-185">刷新每个全息相机的常量缓冲区中的数据。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="ad2aa-186">请在更新预测后以及对该照相机进行任何绘图调用之前执行此操作。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="ad2aa-187">From **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-187">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="ad2aa-188">在这里, 我们将演示如何从照相机姿势获取矩阵。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="ad2aa-189">在此过程中, 我们还获取照相机的当前视区。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="ad2aa-190">请注意我们是如何提供坐标系统的: 这是我们用于了解注视的相同坐标系统, 它与我们用于放置旋转多维数据集的坐标系统相同。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="ad2aa-191">From **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="ad2aa-192">应设置每个帧的视区。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-192">The viewport should be set each frame.</span></span> <span data-ttu-id="ad2aa-193">顶点着色器 (至少) 通常需要访问视图/投影数据。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="ad2aa-194">From **CameraResources:: AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="ad2aa-195">**呈现到相机后台缓冲区, 并提交深度缓冲区**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="ad2aa-196">最好检查**TryGetViewTransform**是否已成功, 然后再尝试使用视图/投影数据, 因为如果无法定位坐标系统 (例如, 跟踪被中断), 则应用无法在该帧上为其呈现。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="ad2aa-197">如果**CameraResources**类指示成功的更新, 则模板仅对旋转多维数据集调用**Render** 。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="ad2aa-198">为了使开发人员或用户将其放在世界各地, Windows Mixed Reality 包含用于[映像稳定性](hologram-stability.md)的功能。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="ad2aa-199">图像稳定性有助于隐藏渲染管道中固有的延迟, 以确保用户的最优秀全息体验;为了进一步增强图像稳定性, 还可以指定一个焦点点, 或者可以提供深度缓冲区来实时计算优化的图像稳定性。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="ad2aa-200">为了获得最佳结果, 应用应使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API 提供深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="ad2aa-201">然后, Windows Mixed Reality 可以使用深度缓冲区中的几何信息来实时优化图像稳定性。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="ad2aa-202">默认情况下, Windows 全息应用程序模板会提交应用的深度缓冲区, 有助于优化全息影像稳定性。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="ad2aa-203">From **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-203">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="ad2aa-204">Windows 将在 GPU 上处理深度纹理, 因此它必须可以使用深度缓冲区作为着色器资源。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="ad2aa-205">你创建的 ID3D11Texture2D 应采用无类型的格式, 并且应作为着色器资源视图进行绑定。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="ad2aa-206">下面是一个示例, 演示如何创建可以提交以进行图像稳定性的深度纹理。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="ad2aa-207">用于**CommitDirect3D11DepthBuffer 的深度缓冲区资源创建**代码:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="ad2aa-208">**绘制全息内容**</span><span class="sxs-lookup"><span data-stu-id="ad2aa-208">**Draw holographic content**</span></span>

<span data-ttu-id="ad2aa-209">对于大小为2的 Texture2DArray, Windows 全息应用程序模板使用建议的方法将内容呈现为立体声。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="ad2aa-210">让我们看看此部分的实例化部分以及它如何在 Windows Mixed Reality 上工作。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="ad2aa-211">From **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-211">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="ad2aa-212">每个实例都从常数缓冲区访问不同的视图/投影矩阵。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="ad2aa-213">下面是常量缓冲区结构, 它只是2个矩阵的数组。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="ad2aa-214">VertexShaderShared 中包含的**hlsl** **:**</span><span class="sxs-lookup"><span data-stu-id="ad2aa-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="ad2aa-215">必须为每个像素设置呈现目标数组索引。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="ad2aa-216">在以下代码片段中, viewId 映射到**SV_RenderTargetArrayIndex**语义。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="ad2aa-217">请注意, 这需要支持可选的 Direct3D 11.3 功能, 这允许从任何着色器阶段设置呈现目标数组索引语义。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="ad2aa-218">From **VPRTVertexShader. hlsl**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-218">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="ad2aa-219">VertexShaderShared 中包含的**hlsl** **:**</span><span class="sxs-lookup"><span data-stu-id="ad2aa-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="ad2aa-220">如果要将现有的实例化绘图技术与这种绘图方法一起使用来绘制立体声渲染目标阵列, 只需绘制两次您通常会获得的实例数的两倍。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="ad2aa-221">在着色器中, 将**instid&gt**除以2以获取原始实例 ID, 该 ID 可编入索引 (例如) 每个对象数据的缓冲区:`int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="ad2aa-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="ad2aa-222">有关在 HoloLens 上渲染立体声内容的重要说明</span><span class="sxs-lookup"><span data-stu-id="ad2aa-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="ad2aa-223">Windows Mixed Reality 支持从任何着色器阶段设置呈现目标数组索引;通常, 这是一项只能在几何着色器阶段完成的任务, 这是因为为 Direct3D 11 定义语义的方式。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="ad2aa-224">在这里, 我们将演示如何设置仅具有顶点和像素着色器阶段集的渲染管道的完整示例。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="ad2aa-225">着色器代码如上文所述。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-225">The shader code is as described above.</span></span>

<span data-ttu-id="ad2aa-226">From **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-226">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="ad2aa-227">有关在非 HoloLens 设备上呈现的重要说明</span><span class="sxs-lookup"><span data-stu-id="ad2aa-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="ad2aa-228">在顶点着色器中设置呈现目标数组索引时, 需要图形驱动程序支持 HoloLens 支持的可选 Direct3D 11.3 功能。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="ad2aa-229">您的应用程序可能能够安全地仅实现此方法以进行呈现, 并且所有要求都将在 Microsoft HoloLens 上运行。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="ad2aa-230">这种情况可能是你还想要使用 HoloLens 模拟器, 这是一个功能强大的用于全息应用的开发工具, 并支持 Windows Mixed Reality 沉浸式耳机设备, 这些设备附加到 Windows 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="ad2aa-231">支持非 HoloLens 呈现路径, 因此, 适用于所有 Windows Mixed Reality-也内置于 Windows 全息应用程序模板中。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="ad2aa-232">在模板代码中, 你将找到用于使全息应用在你的开发 PC 上的 GPU 上运行的代码。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="ad2aa-233">下面是**DeviceResources**类检查此可选功能支持的方式。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="ad2aa-234">From **DeviceResources:: CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="ad2aa-235">若要在不使用此可选功能的情况下支持呈现, 你的应用程序必须使用几何着色器来设置呈现目标数组索引。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="ad2aa-236">此代码段将在 **VSSetConstantBuffers**之后和在上一节中所示的代码示例中的**PSSetShader** *之前*添加, 说明如何在 HoloLens 上呈现立体声。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="ad2aa-237">From **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-237">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="ad2aa-238">**HLSL 注意**:在这种情况下, 还必须使用始终允许的着色语义 (如 TEXCOORD0) 加载略微修改的顶点着色器, 将呈现器目标数组索引传递到几何图形着色器。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="ad2aa-239">几何着色器无需执行任何操作;模板几何图形着色器会传递所有数据, 但呈现器目标数组索引除外, 它用于设置 SV_RenderTargetArrayIndex 语义。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="ad2aa-240">GeometryShader 的应用程序模板代码 **。 hlsl**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-240">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="ad2aa-241">显示</span><span class="sxs-lookup"><span data-stu-id="ad2aa-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="ad2aa-242">启用全息帧以显示交换链</span><span class="sxs-lookup"><span data-stu-id="ad2aa-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="ad2aa-243">对于 Windows Mixed Reality, 系统控制交换链。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="ad2aa-244">然后, 系统会管理向每个全息相机提供框架, 以确保高质量的用户体验。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="ad2aa-245">它还为每个照相机提供一个视区来更新每个帧, 以优化系统的各个方面, 例如图像稳定性或混合现实捕获。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="ad2aa-246">因此, 使用 DirectX 的全息版应用不会在 DXGI 交换链**上调用。**</span><span class="sxs-lookup"><span data-stu-id="ad2aa-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="ad2aa-247">而是使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>类, 在完成绘制帧后, 为该帧提供所有交换链。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="ad2aa-248">From **DeviceResources::P 重发**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="ad2aa-249">默认情况下, 此 API 在返回前等待帧完成。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="ad2aa-250">全息应用应等待上一个帧完成, 然后在新帧上启动工作, 因为这样可以减少延迟, 并允许从全息帧预测获得更好的结果。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="ad2aa-251">这并不是一种硬性规则, 如果你的帧所需的时间超过了一个屏幕刷新, 则可以通过将 HolographicFramePresentWaitBehavior 参数传递给<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>来禁用此等待。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="ad2aa-252">在这种情况下, 可能会使用异步呈现线程来维护 GPU 上的连续负载。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="ad2aa-253">请注意, HoloLens 设备的刷新速率为 60hz, 其中一帧的持续时间大约为16毫秒。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="ad2aa-254">沉浸式耳机设备的范围可以是60hz 到 90hz;刷新 90 hz 的显示时, 每个帧的持续时间大约为 11 ms。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="ad2aa-255">与 HolographicFrame 合作, 处理 DeviceLost 方案</span><span class="sxs-lookup"><span data-stu-id="ad2aa-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="ad2aa-256">DirectX 11 应用通常需要检查 DXGI 交换链的**现有**函数返回的 HRESULT, 以找出是否存在**DeviceLost**错误。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="ad2aa-257"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>类将为您处理此情况。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="ad2aa-258">检查其返回的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> , 查明是否需要释放并重新创建 Direct3D 设备和基于设备的资源。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="ad2aa-259">请注意, 如果 Direct3D 设备丢失, 并且重新创建它, 则必须告诉<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>开始使用新设备。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="ad2aa-260">此设备的交换链将重新创建。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="ad2aa-261">From **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="ad2aa-262">出现帧后, 可以返回到主程序循环, 使其继续进入下一帧。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="ad2aa-263">混合图形 Pc 和混合现实应用程序</span><span class="sxs-lookup"><span data-stu-id="ad2aa-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="ad2aa-264">Windows 10 创意者更新电脑可能**配置了离散**和集成的 gpu。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="ad2aa-265">对于这种类型的计算机, Windows 将选择耳机连接的适配器。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="ad2aa-266">应用程序必须确保它创建的 DirectX 设备使用同一个适配器。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="ad2aa-267">最常见的 Direct3D 示例代码演示如何使用默认硬件适配器创建 DirectX 设备, 该设备在混合系统上可能与用于耳机的设备不同。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="ad2aa-268">若要解决这种情况可能导致的任何问题, 请使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>中的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> 。PrimaryAdapterId () 或<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId ()。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="ad2aa-269">然后, 可以使用此 adapterId, 使用 IDXGIFactory4 选择正确的 DXGIAdapter。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="ad2aa-270">From **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="ad2aa-271">用于**更新 DeviceResources:: CreateDeviceResources 以使用 IDXGIAdapter 的**代码</span><span class="sxs-lookup"><span data-stu-id="ad2aa-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="ad2aa-272">**混合图形和媒体基础**</span><span class="sxs-lookup"><span data-stu-id="ad2aa-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="ad2aa-273">对混合系统使用媒体基础可能会导致视频无法呈现或视频纹理损坏的问题。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="ad2aa-274">出现这种情况的原因可能是, 媒体基础默认为系统行为, 如上文所述。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="ad2aa-275">在某些情况下, 需要创建单独的 ID3D11Device 以支持多线程, 并设置正确的创建标志。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="ad2aa-276">初始化 ID3D11Device 时, 必须将 D3D11_CREATE_DEVICE_VIDEO_SUPPORT 标志定义为 D3D11_CREATE_DEVICE_FLAG 的一部分。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="ad2aa-277">创建设备和上下文后, 调用<a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a>以启用多线程处理。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="ad2aa-278">若要将设备与<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>关联, 请使用<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: ResetDevice</a>函数。</span><span class="sxs-lookup"><span data-stu-id="ad2aa-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="ad2aa-279">用于**将 ID3D11Device 与 IMFDXGIDeviceManager 相关联的**代码:</span><span class="sxs-lookup"><span data-stu-id="ad2aa-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="ad2aa-280">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad2aa-280">See also</span></span>
* [<span data-ttu-id="ad2aa-281">DirectX 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="ad2aa-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="ad2aa-282">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="ad2aa-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
