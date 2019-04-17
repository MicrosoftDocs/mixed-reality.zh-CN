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
# <a name="rendering-in-directx"></a>在 DirectX 中呈现

Windows Mixed Reality 基于 DirectX 生成丰富的构建，3D 图形的用户体验。 呈现抽象位于正上方 DirectX，并允许应用原因有关的位置和方向 holographic 场景，作为预测系统的一个或多个观察程序。 开发人员然后可以找到其全息相对于每个照相机，让用户在将移动呈现这些全息各种空间坐标系统中的应用。

## <a name="update-for-the-current-frame"></a>当前帧的更新

若要更新全息的应用程序状态，一次每一帧应用将：
* 获取<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>显示管理系统中。
* 更新与当前预测的照相机视图将在完成呈现时的场景。 请注意，可以有多个 holographic 场景的照相机。

若要呈现到全息版的照相机视图，一次每一帧应用将：
* 对于每个照相机呈现当前帧时，使用从系统照相机视图和投影矩阵的场景。

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>创建新的 holographic 帧，并获取其预测

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>具有应用程序所需更新和呈现当前帧的信息。 应用程序首先调用每个新帧**CreateNextFrame**方法。 调用此方法时，使用最新的传感器数据可用，并封装在进行预测**CurrentPrediction**对象。

新框架对象必须用于每个呈现的帧，因为它才有效的某个时刻的时间。 **CurrentPrediction**属性包含如照相机的位置的信息。 到时预期帧可对用户可见的时间中的确切时刻中推断出的信息。

以下代码摘自**AppMain::Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>照相机的过程会更新

后台缓冲区可以更改帧之间。 若要验证后你的应用需要为每个照相机缓冲和发布并根据需要重新创建资源视图和深度缓冲区。 请注意，在预测中带来的一套当前帧中正在使用的照相机的权威列表。 通常情况下，您可以使用此列表进行循环访问集的照相机。

从**AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

从**DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>获取要用于呈现为基础的坐标系

Windows Mixed Reality，你的应用可以创建各种[坐标系](coordinate-systems-in-directx.md)，根据需要如附加的参考框架和固定参考框架中，跟踪现实生活中的位置。 有关在何处呈现每个帧的全息，您的应用程序然后可以使用这些坐标系统的原因。 当从 API 请求坐标，您将始终传入<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>中你想要用来表示这些坐标。

从**AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

这些坐标系统然后可用于呈现您的场景中的内容时生成立体声视图矩阵。

从**CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>进程的视线移动和手势输入

[注视](gaze.md)并[手势](gestures.md)输入不是基于时间的因此不需要更新中的**StepTimer**函数。 但是[此输入](gaze,-gestures,-and-motion-controllers-in-directx.md)是指应用程序需要查看每个帧。

### <a name="process-time-based-updates"></a>处理基于时间的更新

任何实时呈现应用将需要某种方式来处理基于时间的更新;我们提供一种方法来执行此操作中的 Windows 全息版的应用程序模板通过**StepTimer**实现。 这类似于 StepTimer 是提供在 DirectX 11 UWP 应用模板，因此如果已查看过该模板在您应该熟悉地面上。 此 StepTimer 示例帮助程序类是能够提供固定的时间步长更新，以及可变时间步长更新，并且默认模式是可变时间步长。

在全息呈现的情况下我们专门选择不将太多到计时器函数。 这是由于可以将其固定的时间步长进行配置，在这种情况下它在一些帧 – 每个框架 – 或根本不可能超过一次获取调用中，我们 holographic 数据更新应执行一次每一帧。


从**AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>位置和旋转全息坐标系统中

如果在运行在单个坐标系统中，使用模板一样**SpatialStationaryReferenceFrame**，此过程不是不同于你是否则用于在三维图中。 我们在这里，旋转多维数据集并将模型矩阵设置相对于固定的坐标系统中的位置。

从**SpinningCubeRenderer::Update**:

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

**请注意有关高级方案：** 旋转多维数据集是如何的非常简单定位单个引用范围内的一张全息图示例。 此外，还可以向[使用多个 SpatialCoordinateSystems](coordinate-systems-in-directx.md)中呈现相同的帧，在同一时间。

### <a name="update-constant-buffer-data"></a>更新常量缓冲区的数据

像往常一样将更新的内容模型转换。 到目前为止，您将具有计算为有效坐标系统，您将在呈现的转换。

从**SpinningCubeRenderer::Update**:

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

视图和投影转换呢？ 为获得最佳结果，我们想要等待，直到我们获取这些之前，我们已基本准备为我们的绘图调用。

## <a name="render-the-current-frame"></a>呈现当前帧

Windows Mixed reality 呈现就不太大区别呈现在 2D mono，但需要注意的一些差异：
* Holographic 帧预测都是重要的。 越接近预测是更好地将查找你全息呈现帧时。
* Windows Mixed Reality 控制的照相机视图。 您需要为每个呈现，因为 holographic 框架将继续介绍它们为你更高版本。
* 立体声呈现建议使用实例化的绘制到呈现目标数组来完成。 全息版的应用程序模板使用建议的方法的实例绘制到呈现目标数组，它使用一个呈现目标视图**Texture2DArray**。
* 如果你想要呈现而无需使用立体声实例化，将需要创建两个非数组 RenderTargetViews （一个用于每只眼睛） 的切片中的两个每个引用**Texture2DArray**从系统提供给应用。 这不是建议，因为它通常是明显慢于使用实例化。

### <a name="get-an-updated-holographicframe-prediction"></a>获取已更新的 HolographicFrame 预测

更新帧预测映像稳定的效率，并允许进行更准确地定位全息由于预测和该框架是对用户可见时之间的较短时间。 理想情况下更新帧呈现之前只是预测。

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>呈现到每个照相机

在预测中，相机带来在组上循环并呈现为在此集中的每个照相机。

**设置呈现处理过程**

Windows Mixed Reality 使用立体呈现以增强具有深度的错觉并呈现 stereoscopically，因此左侧和右侧显示处于活动状态。 使用立体呈现大脑可以作为实际的深度，来协调在两个显示器之间没有偏移量。 此部分涵盖立体呈现使用实例化，使用的 Windows 全息版的应用程序模板中的代码。

每个照相机具有其自己的呈现器目标 （后台缓冲区），以及视图和投影矩阵，到全息版的空间。 您的应用程序将需要创建任何其他基于照相机的资源-例如深度缓冲区中的每个照相机基础上。 在 Windows 全息版的应用程序模板中，我们提供这些资源捆绑在 DX::CameraResources 在一起的帮助器类。 首先设置呈现目标视图：

从**AppMain::Render**:

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

**使用预测照相机中获取视图和投影矩阵**

每个 holographic 照相机的视图和投影矩阵将因每个帧。 刷新每个 holographic 照相机的常量缓冲区中的数据。 执行此操作后更新预测，并在之前任何绘图调用为该摄像机。

从**AppMain::Render**:

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

在这里，我们演示如何从照相机姿势获取矩阵。 在此过程中我们也获得照相机的当前视区。 请注意我们如何提供一个坐标系： 这是我们用于了解视线移动，相同的坐标系统，它是我们使用定位旋转多维数据集的相同。


从**CameraResources::UpdateViewProjectionBuffer**:

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

每个帧，应设置视区。 顶点着色器 （至少） 通常需要对视图/投影数据的访问。


从**CameraResources::AttachViewProjectionBuffer**:

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

**呈现到相机后台缓冲区和提交深度缓冲区**:

它是一个好办法，检查**TryGetViewTransform**成功之前尝试使用视图/投影数据，因为如果坐标系统不是可定位 （例如，跟踪已中断） 您的应用程序不能用它呈现为此，帧。 该模板仅调用**呈现**旋转多维数据集上如果**CameraResources**类表示更新成功。

若要保留全息其中一名开发人员或用户将其放在世界中，Windows Mixed Reality 的功能包括：[映像稳定](hologram-stability.md)。 映像稳定可帮助隐藏呈现管道，以确保用户; 最全息版体验中固有的延迟可能指定的焦点位置来增强更进一步，映像稳定或可提供深度缓冲区来计算优化实时映像稳定。

为获得最佳结果，您的应用程序应提供深度缓冲区使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API。 Windows Mixed Reality 然后可以使用从深度缓冲区的几何图形信息来优化在真实时间中的映像稳定。 Windows 全息版的应用程序模板默认情况下，帮助优化全息图稳定性提交应用程序的深度缓冲区。

从**AppMain::Render**:

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
>Windows 将处理你在 GPU 上的深度纹理，因此，它必须能深度缓冲区用作着色器资源。 无类型的格式应为你创建 ID3D11Texture2D 和它应绑定为着色器资源视图。 下面是如何创建可提交的映像稳定的深度纹理的示例。

为代码**深度缓冲区资源创建为 CommitDirect3D11DepthBuffer**:

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

**绘制全息版的内容**

Windows 全息版的应用程序模板呈现在立体声设备中的内容时使用的绘制到的大小为 2 Texture2DArray 实例化的几何图形的推荐的方法。 让我们看看这，和它如何处理 Windows Mixed Reality 的实例化部分。

从**SpinningCubeRenderer::Render**:

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

每个实例访问常量缓冲区中的不同视图/投影矩阵。 下面是常量缓冲区结构，它只是一个数组的 2 个矩阵。

从**VertexShaderShared.hlsl**、 包含**VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

呈现器目标数组索引必须为每个像素设置。 在以下代码片段，output.viewId 映射到**SV_RenderTargetArrayIndex**语义。 请注意，这要求支持可选的 Direct3D 11.3 功能，允许的呈现器目标数组索引语义若要设置从任何着色器阶段。

从**VPRTVertexShader.hlsl**:

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

从**VertexShaderShared.hlsl**、 包含**VPRTVertexShader.hlsl**:

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

如果你想要使用现有实例时使用此方法绘制到将立体声音频绘制技术呈现目标数组，您需要做的就是绘制两次通常具有的实例数。 在着色器，将划分**input.instId** 2 用于获取原始的实例 ID，这可编入索引 （例如） 的每个对象数据的缓冲区： `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>有关呈现在 HoloLens 上的立体声内容的重要说明

Windows Mixed Reality 支持从任何着色器阶段; 设置呈现器目标数组索引的功能通常情况下，这是只有在由于语义定义 Direct3D 11 的方式在几何着色器阶段中的任务。 这里，我们演示如何使用只是顶点和像素着色器的阶段组设置呈现管道的完整示例。 着色器代码是上文所述。

从**SpinningCubeRenderer::Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>有关在非 HoloLens 设备上呈现的重要说明

顶点着色器中设置的呈现器目标数组索引需要图形驱动程序支持可选的 Direct3D 11.3 功能，支持 HoloLens。 您的应用程序可能能够安全地实现只是进行呈现，该技术，用于在 Microsoft HoloLens 上运行，将满足所有要求。

可能的用例，你想要使用 HoloLens 仿真程序，它可以是您全息版的应用程序 — 一个功能强大的开发工具和支持附加到 Windows 10 电脑的 Windows Mixed Reality 沉浸式头戴式耳机设备。 支持非 HoloLens 呈现路径的因此，所有 Windows Mixed Reality-还内置的 Windows 全息版的应用程序模板。 在模板代码中，您会发现的代码以启用全息版应用中进行开发的电脑的 GPU 上运行。 下面是如何**DeviceResources**类检查此项可选功能支持。

从**DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

若要支持呈现，而无需此项可选功能，您的应用程序必须使用几何着色器设置呈现器目标数组索引。 将添加此代码片段*后* **VSSetConstantBuffers**，并*之前* **PSSetShader**中所示在以前的代码示例介绍了如何呈现上 HoloLens 立体声的部分。

从**SpinningCubeRenderer::Render**:

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

**HLSL 注意**:在这种情况下，您也必须加载将呈现器目标数组索引传递给使用始终允许着色器语义，如 TEXCOORD0 几何着色器的略有修改的顶点着色器。 几何着色器无需执行任何操作;模板几何着色器将传递所有数据，将用于设置 SV_RenderTargetArrayIndex 语义的呈现器目标数组索引除外。

应用模板代码**GeometryShader.hlsl**:

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

## <a name="present"></a>显示

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>启用要呈现交换链的 holographic 框架

使用 Windows Mixed Reality 系统控制交换链。 然后，系统管理每个 holographic 相机上以确保高质量的用户体验的演示框架。 它还提供一个视区更新每个框架，用于每个相机，以优化如映像稳定或混合现实捕获系统的方面。 因此，使用 DirectX 的全息版应用程序不会调用**存在**上 DXGI 交换链。 相反，使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>类来完成后显示范围的所有交换链绘制它。

从**DeviceResources::Present**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

默认情况下，此 API 会等待要完成在返回之前的帧。 全息版的应用程序应等待要在新帧，因为这将减少延迟并允许更好的结果从 holographic 帧预测开始工作之前完成的上一帧。 这不是硬规则，并花费的时间超过一个屏幕刷新来呈现您的帧如果必须可以通过传递到 HolographicFramePresentWaitBehavior 参数来禁用此等待<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>。 在这种情况下，可能会使用为了维护持续负载在 GPU 上的异步呈现线程。 请注意 HoloLens 设备的刷新率是 60 hz，其中一个帧具有持续时间为大约 16 毫秒。 沉浸式头戴式耳机设备的范围可以介于 60 hz 到 90 hz;刷新显示在 90 hz，每个帧将有大约 11 毫秒的持续时间。

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>处理与 HolographicFrame DeviceLost 方案

DirectX 11 应用通常想要检查的 DXGI 交换链返回的 HRESULT**存在**函数来找出是否有**DeviceLost**错误。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>类可以帮助您处理。 检查<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a>它将返回以查找您需要发布和重新创建 Direct3D 设备和基于设备的资源。

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

请注意，是否 Direct3D 设备已丢失，并且未重新创建它，您必须告诉<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>若要开始使用新的设备。 此设备，将重新创建交换链。

从**DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

一旦呈现帧，可以返回到主程序循环，并允许它继续到下一帧。

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>混合图形 Pc 和混合的现实应用程序

Windows 10 创意者更新 Pc 可能会使用配置**同时**离散和集成 Gpu。 使用这些类型的计算机，Windows 将选择耳机连接到的适配器。 应用程序必须确保它将创建在 DirectX 设备使用相同的适配器。

最常规的 Direct3D 示例代码演示如何创建使用默认的硬件适配器，这混合系统上可能不是一个用于将耳机相同的 DirectX 设备。

若要解决这可能会导致任何问题，请使用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a>眖<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>。PrimaryAdapterId() 或<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId()。 此 adapterId 然后用于选择使用 IDXGIFactory4.EnumAdapterByLuid 右 DXGIAdapter。

从**DeviceResources::InitializeUsingHolographicSpace**:

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

代码设为**更新 DeviceResources::CreateDeviceResources 使用 IDXGIAdapter**

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

**混合图形和媒体基础**

使用 Media Foundation 混合系统上可能会导致的问题，将不会呈现视频或视频纹理已损坏。 这可能由于 Media Foundation 默认为系统行为，如上所述。 在某些情况下，创建单独 ID3D11Device 都需要支持多线程处理和标志设置为正确创建。

在初始化时 ID3D11Device，D3D11_CREATE_DEVICE_VIDEO_SUPPORT 标志必须定义为 D3D11_CREATE_DEVICE_FLAG 的一部分。 设备和上下文创建后，调用<a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a>若要启用多线程处理。 若要将与设备关联<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>，使用<a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a>函数。

代码设**IMFDXGIDeviceManager 相关联 ID3D11Device**:

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

## <a name="see-also"></a>请参阅
* [在 DirectX 的坐标系统](coordinate-systems-in-directx.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
