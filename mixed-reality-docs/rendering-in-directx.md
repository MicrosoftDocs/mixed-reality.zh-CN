---
title: 在 DirectX 中呈现
description: 介绍了有关 Windows Mixed Reality 全息呈现。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全息、 呈现、 3D 图形，HolographicFrame，呈现循环、 更新循环、 演练、 示例代码
ms.openlocfilehash: fd35f971af4c3c9dfd7f21ee396c92216b3246e9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593080"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="f8bcf-104">在 DirectX 中呈现</span><span class="sxs-lookup"><span data-stu-id="f8bcf-104">Rendering in DirectX</span></span>

<span data-ttu-id="f8bcf-105">Windows Mixed Reality 基于 DirectX 生成丰富的构建，3D 图形的用户体验。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="f8bcf-106">呈现抽象位于正上方 DirectX，并允许应用原因有关的位置和方向 holographic 场景，作为预测系统的一个或多个观察程序。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="f8bcf-107">开发人员然后可以找到其全息相对于每个照相机，让用户在将移动呈现这些全息各种空间坐标系统中的应用。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="f8bcf-108">当前帧的更新</span><span class="sxs-lookup"><span data-stu-id="f8bcf-108">Update for the current frame</span></span>

<span data-ttu-id="f8bcf-109">若要更新全息的应用程序状态，一次每一帧应用将：</span><span class="sxs-lookup"><span data-stu-id="f8bcf-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="f8bcf-110">获取<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>显示管理系统中。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="f8bcf-111">更新与当前预测的照相机视图将在完成呈现时的场景。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="f8bcf-112">请注意，可以有多个 holographic 场景的照相机。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="f8bcf-113">若要呈现到全息版的照相机视图，一次每一帧应用将：</span><span class="sxs-lookup"><span data-stu-id="f8bcf-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="f8bcf-114">对于每个照相机呈现当前帧时，使用从系统照相机视图和投影矩阵的场景。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="f8bcf-115">创建新的 holographic 帧，并获取其预测</span><span class="sxs-lookup"><span data-stu-id="f8bcf-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="f8bcf-116"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>具有应用程序所需更新和呈现当前帧的信息。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="f8bcf-117">应用程序首先调用每个新帧**CreateNextFrame**方法。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="f8bcf-118">调用此方法时，使用最新的传感器数据可用，并封装在进行预测**CurrentPrediction**对象。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="f8bcf-119">新框架对象必须用于每个呈现的帧，因为它才有效的某个时刻的时间。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="f8bcf-120">**CurrentPrediction**属性包含如照相机的位置的信息。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="f8bcf-121">到时预期帧可对用户可见的时间中的确切时刻中推断出的信息。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="f8bcf-122">以下代码摘自**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="f8bcf-123">照相机的过程会更新</span><span class="sxs-lookup"><span data-stu-id="f8bcf-123">Process camera updates</span></span>

<span data-ttu-id="f8bcf-124">后台缓冲区可以更改帧之间。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="f8bcf-125">若要验证后你的应用需要为每个照相机缓冲和发布并根据需要重新创建资源视图和深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="f8bcf-126">请注意，在预测中带来的一套当前帧中正在使用的照相机的权威列表。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="f8bcf-127">通常情况下，您可以使用此列表进行循环访问集的照相机。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="f8bcf-128">从**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="f8bcf-129">从**DeviceResources::EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="f8bcf-130">获取要用于呈现为基础的坐标系</span><span class="sxs-lookup"><span data-stu-id="f8bcf-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="f8bcf-131">Windows Mixed Reality，你的应用可以创建各种[坐标系](coordinate-systems-in-directx.md)，根据需要如附加的参考框架和固定参考框架中，跟踪现实生活中的位置。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="f8bcf-132">有关在何处呈现每个帧的全息，您的应用程序然后可以使用这些坐标系统的原因。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="f8bcf-133">当从 API 请求坐标，您将始终传入<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>中你想要用来表示这些坐标。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="f8bcf-134">从**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="f8bcf-135">这些坐标系统然后可用于呈现您的场景中的内容时生成立体声视图矩阵。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="f8bcf-136">从**CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="f8bcf-137">进程的视线移动和手势输入</span><span class="sxs-lookup"><span data-stu-id="f8bcf-137">Process gaze and gesture input</span></span>

<span data-ttu-id="f8bcf-138">[注视](gaze.md)并[手势](gestures.md)输入不是基于时间的因此不需要更新中的**StepTimer**函数。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-138">[Gaze](gaze.md) and [gesture](gestures.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="f8bcf-139">但是[此输入](gaze,-gestures,-and-motion-controllers-in-directx.md)是指应用程序需要查看每个帧。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-139">However [this input](gaze,-gestures,-and-motion-controllers-in-directx.md) is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="f8bcf-140">处理基于时间的更新</span><span class="sxs-lookup"><span data-stu-id="f8bcf-140">Process time-based updates</span></span>

<span data-ttu-id="f8bcf-141">任何实时呈现应用将需要某种方式来处理基于时间的更新;我们提供一种方法来执行此操作中的 Windows 全息版的应用程序模板通过**StepTimer**实现。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="f8bcf-142">这类似于 StepTimer 是提供在 DirectX 11 UWP 应用模板，因此如果已查看过该模板在您应该熟悉地面上。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="f8bcf-143">此 StepTimer 示例帮助程序类是能够提供固定的时间步长更新，以及可变时间步长更新，并且默认模式是可变时间步长。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="f8bcf-144">在全息呈现的情况下我们专门选择不将太多到计时器函数。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="f8bcf-145">这是由于可以将其固定的时间步长进行配置，在这种情况下它在一些帧 – 每个框架 – 或根本不可能超过一次获取调用中，我们 holographic 数据更新应执行一次每一帧。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="f8bcf-146">从**AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="f8bcf-147">位置和旋转全息坐标系统中</span><span class="sxs-lookup"><span data-stu-id="f8bcf-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="f8bcf-148">如果在运行在单个坐标系统中，使用模板一样**SpatialStationaryReferenceFrame**，此过程不是不同于你是否则用于在三维图中。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="f8bcf-149">我们在这里，旋转多维数据集并将模型矩阵设置相对于固定的坐标系统中的位置。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="f8bcf-150">从**SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-150">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="f8bcf-151">**请注意有关高级方案：** 旋转多维数据集是如何的非常简单定位单个引用范围内的一张全息图示例。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="f8bcf-152">此外，还可以向[使用多个 SpatialCoordinateSystems](coordinate-systems-in-directx.md)中呈现相同的帧，在同一时间。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="f8bcf-153">更新常量缓冲区的数据</span><span class="sxs-lookup"><span data-stu-id="f8bcf-153">Update constant buffer data</span></span>

<span data-ttu-id="f8bcf-154">像往常一样将更新的内容模型转换。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="f8bcf-155">到目前为止，您将具有计算为有效坐标系统，您将在呈现的转换。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="f8bcf-156">从**SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-156">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="f8bcf-157">视图和投影转换呢？</span><span class="sxs-lookup"><span data-stu-id="f8bcf-157">What about view and projection transforms?</span></span> <span data-ttu-id="f8bcf-158">为获得最佳结果，我们想要等待，直到我们获取这些之前，我们已基本准备为我们的绘图调用。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="f8bcf-159">呈现当前帧</span><span class="sxs-lookup"><span data-stu-id="f8bcf-159">Render the current frame</span></span>

<span data-ttu-id="f8bcf-160">Windows Mixed reality 呈现就不太大区别呈现在 2D mono，但需要注意的一些差异：</span><span class="sxs-lookup"><span data-stu-id="f8bcf-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="f8bcf-161">Holographic 帧预测都是重要的。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="f8bcf-162">越接近预测是更好地将查找你全息呈现帧时。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="f8bcf-163">Windows Mixed Reality 控制的照相机视图。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="f8bcf-164">您需要为每个呈现，因为 holographic 框架将继续介绍它们为你更高版本。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="f8bcf-165">立体声呈现建议使用实例化的绘制到呈现目标数组来完成。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="f8bcf-166">全息版的应用程序模板使用建议的方法的实例绘制到呈现目标数组，它使用一个呈现目标视图**Texture2DArray**。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="f8bcf-167">如果你想要呈现而无需使用立体声实例化，将需要创建两个非数组 RenderTargetViews （一个用于每只眼睛） 的切片中的两个每个引用**Texture2DArray**从系统提供给应用。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="f8bcf-168">这不是建议，因为它通常是明显慢于使用实例化。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="f8bcf-169">获取已更新的 HolographicFrame 预测</span><span class="sxs-lookup"><span data-stu-id="f8bcf-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="f8bcf-170">更新帧预测映像稳定的效率，并允许进行更准确地定位全息由于预测和该框架是对用户可见时之间的较短时间。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="f8bcf-171">理想情况下更新帧呈现之前只是预测。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="f8bcf-172">呈现到每个照相机</span><span class="sxs-lookup"><span data-stu-id="f8bcf-172">Render to each camera</span></span>

<span data-ttu-id="f8bcf-173">在预测中，相机带来在组上循环并呈现为在此集中的每个照相机。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="f8bcf-174">**设置呈现处理过程**</span><span class="sxs-lookup"><span data-stu-id="f8bcf-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="f8bcf-175">Windows Mixed Reality 使用立体呈现以增强具有深度的错觉并呈现 stereoscopically，因此左侧和右侧显示处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="f8bcf-176">使用立体呈现大脑可以作为实际的深度，来协调在两个显示器之间没有偏移量。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="f8bcf-177">此部分涵盖立体呈现使用实例化，使用的 Windows 全息版的应用程序模板中的代码。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="f8bcf-178">每个照相机具有其自己的呈现器目标 （后台缓冲区），以及视图和投影矩阵，到全息版的空间。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="f8bcf-179">您的应用程序将需要创建任何其他基于照相机的资源-例如深度缓冲区中的每个照相机基础上。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="f8bcf-180">在 Windows 全息版的应用程序模板中，我们提供这些资源捆绑在 DX::CameraResources 在一起的帮助器类。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="f8bcf-181">首先设置呈现目标视图：</span><span class="sxs-lookup"><span data-stu-id="f8bcf-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="f8bcf-182">从**AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-182">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="f8bcf-183">**使用预测照相机中获取视图和投影矩阵**</span><span class="sxs-lookup"><span data-stu-id="f8bcf-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="f8bcf-184">每个 holographic 照相机的视图和投影矩阵将因每个帧。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="f8bcf-185">刷新每个 holographic 照相机的常量缓冲区中的数据。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="f8bcf-186">执行此操作后更新预测，并在之前任何绘图调用为该摄像机。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="f8bcf-187">从**AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-187">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="f8bcf-188">在这里，我们演示如何从照相机姿势获取矩阵。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="f8bcf-189">在此过程中我们也获得照相机的当前视区。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="f8bcf-190">请注意我们如何提供一个坐标系： 这是我们用于了解视线移动，相同的坐标系统，它是我们使用定位旋转多维数据集的相同。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="f8bcf-191">从**CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="f8bcf-192">每个帧，应设置视区。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-192">The viewport should be set each frame.</span></span> <span data-ttu-id="f8bcf-193">顶点着色器 （至少） 通常需要对视图/投影数据的访问。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="f8bcf-194">从**CameraResources::AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="f8bcf-195">**呈现到相机后台缓冲区和提交深度缓冲区**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="f8bcf-196">它是一个好办法，检查**TryGetViewTransform**成功之前尝试使用视图/投影数据，因为如果坐标系统不是可定位 （例如，跟踪已中断） 您的应用程序不能用它呈现为此，帧。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="f8bcf-197">该模板仅调用**呈现**旋转多维数据集上如果**CameraResources**类表示更新成功。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="f8bcf-198">若要保留全息其中一名开发人员或用户将其放在世界中，Windows Mixed Reality 的功能包括：[映像稳定](hologram-stability.md)。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="f8bcf-199">映像稳定可帮助隐藏呈现管道，以确保用户; 最全息版体验中固有的延迟可能指定的焦点位置来增强更进一步，映像稳定或可提供深度缓冲区来计算优化实时映像稳定。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="f8bcf-200">为获得最佳结果，您的应用程序应提供深度缓冲区使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="f8bcf-201">Windows Mixed Reality 然后可以使用从深度缓冲区的几何图形信息来优化在真实时间中的映像稳定。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="f8bcf-202">Windows 全息版的应用程序模板默认情况下，帮助优化全息图稳定性提交应用程序的深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="f8bcf-203">从**AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-203">From **AppMain::Render**:</span></span>

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
><span data-ttu-id="f8bcf-204">Windows 将处理你在 GPU 上的深度纹理，因此，它必须能深度缓冲区用作着色器资源。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="f8bcf-205">无类型的格式应为你创建 ID3D11Texture2D 和它应绑定为着色器资源视图。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="f8bcf-206">下面是如何创建可提交的映像稳定的深度纹理的示例。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="f8bcf-207">为代码**深度缓冲区资源创建为 CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

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

<span data-ttu-id="f8bcf-208">**绘制全息版的内容**</span><span class="sxs-lookup"><span data-stu-id="f8bcf-208">**Draw holographic content**</span></span>

<span data-ttu-id="f8bcf-209">Windows 全息版的应用程序模板呈现在立体声设备中的内容时使用的绘制到的大小为 2 Texture2DArray 实例化的几何图形的推荐的方法。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="f8bcf-210">让我们看看这，和它如何处理 Windows Mixed Reality 的实例化部分。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="f8bcf-211">从**SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-211">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="f8bcf-212">每个实例访问常量缓冲区中的不同视图/投影矩阵。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="f8bcf-213">下面是常量缓冲区结构，它只是一个数组的 2 个矩阵。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="f8bcf-214">从**VertexShaderShared.hlsl**、 包含**VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="f8bcf-215">呈现器目标数组索引必须为每个像素设置。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="f8bcf-216">在以下代码片段，output.viewId 映射到**SV_RenderTargetArrayIndex**语义。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="f8bcf-217">请注意，这要求支持可选的 Direct3D 11.3 功能，允许的呈现器目标数组索引语义若要设置从任何着色器阶段。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="f8bcf-218">从**VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-218">From **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="f8bcf-219">从**VertexShaderShared.hlsl**、 包含**VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="f8bcf-220">如果你想要使用现有实例时使用此方法绘制到将立体声音频绘制技术呈现目标数组，您需要做的就是绘制两次通常具有的实例数。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="f8bcf-221">在着色器，将划分**input.instId** 2 用于获取原始的实例 ID，这可编入索引 （例如） 的每个对象数据的缓冲区： `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="f8bcf-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="f8bcf-222">有关呈现在 HoloLens 上的立体声内容的重要说明</span><span class="sxs-lookup"><span data-stu-id="f8bcf-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="f8bcf-223">Windows Mixed Reality 支持从任何着色器阶段; 设置呈现器目标数组索引的功能通常情况下，这是只有在由于语义定义 Direct3D 11 的方式在几何着色器阶段中的任务。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="f8bcf-224">这里，我们演示如何使用只是顶点和像素着色器的阶段组设置呈现管道的完整示例。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="f8bcf-225">着色器代码是上文所述。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-225">The shader code is as described above.</span></span>

<span data-ttu-id="f8bcf-226">从**SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-226">From **SpinningCubeRenderer::Render**:</span></span>

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="f8bcf-227">有关在非 HoloLens 设备上呈现的重要说明</span><span class="sxs-lookup"><span data-stu-id="f8bcf-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="f8bcf-228">顶点着色器中设置的呈现器目标数组索引需要图形驱动程序支持可选的 Direct3D 11.3 功能，支持 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="f8bcf-229">您的应用程序可能能够安全地实现只是进行呈现，该技术，用于在 Microsoft HoloLens 上运行，将满足所有要求。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="f8bcf-230">可能的用例，你想要使用 HoloLens 仿真程序，它可以是您全息版的应用程序 — 一个功能强大的开发工具和支持附加到 Windows 10 电脑的 Windows Mixed Reality 沉浸式头戴式耳机设备。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="f8bcf-231">支持非 HoloLens 呈现路径的因此，所有 Windows Mixed Reality-还内置的 Windows 全息版的应用程序模板。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="f8bcf-232">在模板代码中，您会发现的代码以启用全息版应用中进行开发的电脑的 GPU 上运行。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="f8bcf-233">下面是如何**DeviceResources**类检查此项可选功能支持。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="f8bcf-234">从**DeviceResources::CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="f8bcf-235">若要支持呈现，而无需此项可选功能，您的应用程序必须使用几何着色器设置呈现器目标数组索引。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="f8bcf-236">将添加此代码片段*后* **VSSetConstantBuffers**，并*之前* **PSSetShader**中所示在以前的代码示例介绍了如何呈现上 HoloLens 立体声的部分。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="f8bcf-237">从**SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-237">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="f8bcf-238">**HLSL 注意**:在这种情况下，您也必须加载将呈现器目标数组索引传递给使用始终允许着色器语义，如 TEXCOORD0 几何着色器的略有修改的顶点着色器。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="f8bcf-239">几何着色器无需执行任何操作;模板几何着色器将传递所有数据，将用于设置 SV_RenderTargetArrayIndex 语义的呈现器目标数组索引除外。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="f8bcf-240">应用模板代码**GeometryShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-240">App template code for **GeometryShader.hlsl**:</span></span>

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

## <a name="present"></a><span data-ttu-id="f8bcf-241">显示</span><span class="sxs-lookup"><span data-stu-id="f8bcf-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="f8bcf-242">启用要呈现交换链的 holographic 框架</span><span class="sxs-lookup"><span data-stu-id="f8bcf-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="f8bcf-243">使用 Windows Mixed Reality 系统控制交换链。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="f8bcf-244">然后，系统管理每个 holographic 相机上以确保高质量的用户体验的演示框架。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="f8bcf-245">它还提供一个视区更新每个框架，用于每个相机，以优化如映像稳定或混合现实捕获系统的方面。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="f8bcf-246">因此，使用 DirectX 的全息版应用程序不会调用**存在**上 DXGI 交换链。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="f8bcf-247">相反，使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>类来完成后显示范围的所有交换链绘制它。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="f8bcf-248">从**DeviceResources::Present**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="f8bcf-249">默认情况下，此 API 会等待要完成在返回之前的帧。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="f8bcf-250">全息版的应用程序应等待要在新帧，因为这将减少延迟并允许更好的结果从 holographic 帧预测开始工作之前完成的上一帧。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="f8bcf-251">这不是硬规则，并花费的时间超过一个屏幕刷新来呈现您的帧如果必须可以通过传递到 HolographicFramePresentWaitBehavior 参数来禁用此等待<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="f8bcf-252">在这种情况下，可能会使用为了维护持续负载在 GPU 上的异步呈现线程。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="f8bcf-253">请注意 HoloLens 设备的刷新率是 60 hz，其中一个帧具有持续时间为大约 16 毫秒。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="f8bcf-254">沉浸式头戴式耳机设备的范围可以介于 60 hz 到 90 hz;刷新显示在 90 hz，每个帧将有大约 11 毫秒的持续时间。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="f8bcf-255">处理与 HolographicFrame DeviceLost 方案</span><span class="sxs-lookup"><span data-stu-id="f8bcf-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="f8bcf-256">DirectX 11 应用通常想要检查的 DXGI 交换链返回的 HRESULT**存在**函数来找出是否有**DeviceLost**错误。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="f8bcf-257"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>类可以帮助您处理。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="f8bcf-258">检查<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a>它将返回以查找您需要发布和重新创建 Direct3D 设备和基于设备的资源。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

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

<span data-ttu-id="f8bcf-259">请注意，是否 Direct3D 设备已丢失，并且未重新创建它，您必须告诉<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>若要开始使用新的设备。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="f8bcf-260">此设备，将重新创建交换链。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="f8bcf-261">从**DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="f8bcf-262">一旦呈现帧，可以返回到主程序循环，并允许它继续到下一帧。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="f8bcf-263">混合图形 Pc 和混合的现实应用程序</span><span class="sxs-lookup"><span data-stu-id="f8bcf-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="f8bcf-264">Windows 10 创意者更新 Pc 可能会使用配置**同时**离散和集成 Gpu。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="f8bcf-265">使用这些类型的计算机，Windows 将选择耳机连接到的适配器。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="f8bcf-266">应用程序必须确保它将创建在 DirectX 设备使用相同的适配器。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="f8bcf-267">最常规的 Direct3D 示例代码演示如何创建使用默认的硬件适配器，这混合系统上可能不是一个用于将耳机相同的 DirectX 设备。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="f8bcf-268">若要解决这可能会导致任何问题，请使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a>眖<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>。PrimaryAdapterId() 或<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId()。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="f8bcf-269">此 adapterId 然后用于选择使用 IDXGIFactory4.EnumAdapterByLuid 右 DXGIAdapter。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="f8bcf-270">从**DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

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

<span data-ttu-id="f8bcf-271">代码设为**更新 DeviceResources::CreateDeviceResources 使用 IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="f8bcf-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

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

<span data-ttu-id="f8bcf-272">**混合图形和媒体基础**</span><span class="sxs-lookup"><span data-stu-id="f8bcf-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="f8bcf-273">使用 Media Foundation 混合系统上可能会导致的问题，将不会呈现视频或视频纹理已损坏。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="f8bcf-274">这可能由于 Media Foundation 默认为系统行为，如上所述。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="f8bcf-275">在某些情况下，创建单独 ID3D11Device 都需要支持多线程处理和标志设置为正确创建。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="f8bcf-276">在初始化时 ID3D11Device，D3D11_CREATE_DEVICE_VIDEO_SUPPORT 标志必须定义为 D3D11_CREATE_DEVICE_FLAG 的一部分。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="f8bcf-277">设备和上下文创建后，调用<a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a>若要启用多线程处理。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="f8bcf-278">若要将与设备关联<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>，使用<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a>函数。</span><span class="sxs-lookup"><span data-stu-id="f8bcf-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="f8bcf-279">代码设**IMFDXGIDeviceManager 相关联 ID3D11Device**:</span><span class="sxs-lookup"><span data-stu-id="f8bcf-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f8bcf-280">请参阅</span><span class="sxs-lookup"><span data-stu-id="f8bcf-280">See also</span></span>
* [<span data-ttu-id="f8bcf-281">在 DirectX 的坐标系统</span><span class="sxs-lookup"><span data-stu-id="f8bcf-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="f8bcf-282">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="f8bcf-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
