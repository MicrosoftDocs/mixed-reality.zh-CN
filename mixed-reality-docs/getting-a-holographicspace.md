---
title: 获取 HolographicSpace
description: 介绍 HolographicSpace API，有关全息呈现和空间输入的核心概念。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 HolographicSpace、 CoreWindow，空间输入，呈现交换链、 holographic 帧、 更新循环、 游戏循环、 参考框架、 locatability、 示例代码、 演练
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593064"
---
# <a name="getting-a-holographicspace"></a>获取 HolographicSpace

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类是进入全息世界的门户。 它控制沉浸式呈现，提供相机数据，并提供对空间推理 Api 的访问。 您将创建一个用于 UWP 应用<a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a>或 Win32 应用程序的 HWND。

## <a name="set-up-the-holographic-space"></a>设置 holographic 空间

创建 holographic 空间对象是对 Windows Mixed Reality 应用进行访问的第一步。 传统的 Windows 应用程序呈现到为其应用程序视图的核心窗口创建 Direct3D 交换链。 此交换链向一台平板电脑 holographic UI 中显示。 若要使应用程序视图而不是 2D 盖板 holographic，创建其核心窗口而不是交换链的 holographic 空间。 显示创建此 holographic 空格的 holographic 帧将您的应用程序放入的全屏呈现模式。

有关**UWP 应用**[从开始*全息版的 DirectX 11 应用 (通用 Windows) 模板*](creating-a-holographic-directx-project.md)，查找在此代码**SetWindow**AppView.cpp 中的方法：

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

有关**Win32 应用程序**[从开始*BasicHologram* Win32 示例](creating-a-holographic-directx-project.md#creating-a-win32-project)，看看**App::CreateWindowAndHolographicSpace**为如何创建 HWND，然后将其转换为令人着迷的 HWND 通过创建一个关联的示例<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

现在，已为你的 UWP CoreWindow 或 Win32 HWND 来获取 HolographicSpace，将使用该 HolographicSpace 来处理 holographic 照相机和创建坐标系统完成全息呈现。 在 DirectX 模板中的多个位置使用的当前的 holographic 空间：
* **DeviceResources**类需要获取一些信息从 HolographicSpace 对象以便创建 Direct3D 设备。 这是与 holographic 显示关联的 DXGI 适配器 ID。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类使用应用程序的 Direct3D 11 设备创建和管理基于设备的资源，例如用于每个 holographic 相机后台缓冲区。 如果您想要查看该函数执行实质上，会发现它在 DeviceResources.cpp。
* 该函数**DeviceResources::InitializeUsingHolographicSpace**演示如何获取适配器通过查找 LUID – 以及如何选择默认适配器时不指定了任何首选的适配器。
* 应用程序的主类使用的 holographic 空间**AppView::SetWindow**或**App::CreateWindowAndHolographicSpace**更新和呈现。

>[!NOTE]
>以下部分指出模板中的函数名喜欢**AppView::SetWindow** ，认为从全息版的 UWP 应用模板开始，你看到的代码段将跨 UWP 和 Win32 应用同样适用。

接下来，我们将深入探究安装流程**SetHolographicSpace**负责 AppMain 类中。

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>相机事件订阅、 创建和删除照相机资源

应用的 holographic 内容位于其 holographic 空间，通过一个或多个 holographic 相机表示场景的视角查看。 现在，已 holographic 空间，可以接收用于 holographic 相机的数据。

您的应用程序需要响应**CameraAdded**类似后台缓冲区呈现目标视图，通过创建任何资源的事件是特定于该摄像机。 您可以查看在此代码**DeviceResources::SetHolographicSpace**由调用的函数**AppView::SetWindow**应用创建任何 holographic 帧之前：

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

您的应用程序还需要响应**CameraRemoved**通过释放针对该相机而创建的资源的事件。

从**DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

事件处理程序必须完成一些工作才能使全息呈现流动非常顺利，以便您的应用程序是能够在所有呈现。 读取代码和注释的详细信息： 则可以寻找**OnCameraAdded**和**OnCameraRemoved**若要了解你主类中如何**m_cameraResources**映射是由处理**DeviceResources**。

现在，我们会集中 AppMain 和安装程序，它会使你的应用需要了解的有关 holographic 照相机。 明确这一点后，务必要记下以下两个要求：

1. 有关**CameraAdded**事件处理程序，该应用程序如何工作，以异步方式完成创建资源并加载新 holographic 照相机的资产。 需要多个帧来完成这项工作的应用程序应请求延迟，并后以异步方式; 加载完成延迟[PPL 任务](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)可用于执行异步工作。 您的应用程序必须确保它已准备好呈现到该摄像机立即退出事件处理程序时或当它完成时延迟。 退出事件处理程序或完成此延迟会告知系统您的应用程序现在已准备好接收 holographic 帧与包含该摄像机。

2. 当应用收到**CameraRemoved**事件，它必须释放对该函数右键消失的后台缓冲区和出口的所有引用。 这包括呈现器目标视图，并可能会保存对引用的任何其他资源[IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)。 应用程序还必须确保后台缓冲区未附加作为呈现器目标，如中所示**CameraResources::ReleaseResourcesForBackBuffer**。 若要帮助加速此过程，您的应用程序可以释放后台缓冲区，然后启动任务以异步方式完成，才可关闭该摄像机的任何其他工作。 全息版的应用程序模板包含可用于此目的的 PPL 任务。

>[!NOTE]
>如果你想要确定何时添加或删除照相机显示在框架中，使用**HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras)并[RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)属性。

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>创建一个参考框架为您全息版的内容

应用程序的内容必须在定位[空间坐标系统](coordinate-systems-in-directx.md)HolographicSpace 中呈现。 系统提供了两个主要的参考框架用于建立在全息坐标系统。

有两种类型的参考帧中 Windows Holographic： 引用附加到该设备的框架和保持静止状态，因为随着用户的环境的移动设备的参考框架。 全息版的应用程序模板的固定参考框架使用默认设置。这是最简单的方式来呈现世界锁定全息之一。

固定参考框架旨在以达到稳定状态的设备的当前位置附近的位置。 这意味着，允许最荒谬不过设备坐标略有偏移相对于用户的环境为设备了解到有关它周围的空间的详细信息。 有两种方法来创建固定参考框架： 获取从坐标系[空间阶段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，或使用默认<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。 如果要创建适用于沉浸式耳机的 Windows Mixed Reality 应用，建议的起始点是[空间阶段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，还提供了有关功能的播放机随身配备沉浸式头戴式耳机。 在这里，我们演示如何使用默认值<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。

空间定位符表示 Windows Mixed Reality 设备和跟踪设备的动作，并提供可以理解相对于其位置的坐标系统。

从**AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

在应用启动时，一次创建固定参考框架。 这是类似于定义世界坐标系，带有时启动应用程序放置在设备的位置处的原点。 此参考框架不会随设备一起移动。

从**AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

所有引用帧都是重力对齐，这意味着与用户的环境相关的 y 轴"向上"箭头。 由于 Windows 使用"惯用右手"坐标系，– z 轴的方向与设备时创建的参考框架为面向"forward"方向。

>[!NOTE]
>当您的应用程序需要精确地放置各个全息时，使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>锚定到现实生活中的位置的单个全息图。 当用户指示特殊感兴趣的一个点，例如，使用空间的定位点。 定位点位置不执行偏差，但它们可以进行调整。 默认情况下，在定位点调整后，它简化了其位置到位的下一步的多个帧上发生更正后。 根据应用程序中，发生此情况时您可能需要调整以不同方式处理 （例如，推迟到全息图均不可见）。 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>属性和<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件启用这些自定义。

## <a name="respond-to-locatability-changed-events"></a>响应 locatability 更改事件

呈现世界锁定全息要求设备必须能够在世界中找到自身。 这可能始终无法可能由于环境条件，如果是这样，用户可能预期跟踪中断的直观指示。 必须使用附加到该设备，而不是固定且世界的参考帧呈现此可视指示。

你的应用可以请求如果出于任何原因中断跟踪获得通知。 注册 LocatabilityChanged 事件来检测时查找本身中的世界更改设备的能力。 从**AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

然后使用此事件以确定无法全息呈现到世界上保持静止时。

## <a name="see-also"></a>请参阅
* [在 DirectX 中呈现](rendering-in-directx.md)
* [在 DirectX 的坐标系统](coordinate-systems-in-directx.md)
