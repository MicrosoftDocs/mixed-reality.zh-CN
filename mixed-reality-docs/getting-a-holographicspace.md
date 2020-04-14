---
title: 获取 HolographicSpace
description: 介绍 HolographicSpace API，这是全息呈现和空间输入的核心概念。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HolographicSpace，CoreWindow，空间输入，呈现，交换链，全息帧，更新循环，游戏循环，引用框架，locatability，示例代码，演练
ms.openlocfilehash: 76211c8a5394e2e296748253df4eac063841746c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277825"
---
# <a name="getting-a-holographicspace"></a>获取 HolographicSpace

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类是您在全息环境中的门户。 它控制沉浸式渲染、提供相机数据，并提供对空间推理 Api 的访问。 你将为 UWP 应用的<a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a>或 Win32 应用的 HWND 创建一个。

## <a name="set-up-the-holographic-space"></a>设置全息空间

创建全息空间对象是创建 Windows Mixed Reality 应用程序的第一步。 传统的 Windows 应用会呈现给为其应用程序视图的核心窗口创建的 Direct3D 交换链。 此交换链在全息 UI 中显示为一个石板。 若要使应用程序视图为全息而不是2D 石板，请为其核心窗口而不是交换链创建一个全息空间。 提供此全息空间创建的全息帧会使您的应用程序进入全屏呈现模式。

对于[从 "*全息 DirectX 11 应用（通用 Windows）" 模板*开始](creating-a-holographic-directx-project.md)的**UWP 应用**，请在 AppView 中的**SetWindow**方法中查找此代码：

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

对于[从*BasicHologram* win32 示例开始](creating-a-holographic-directx-project.md#creating-a-win32-project)的**Win32 应用**，请查看**app：： CreateWindowAndHolographicSpace** ，了解如何创建 HWND，然后通过创建关联的<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>将其转换为沉浸式 HWND：
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

现在，你已获得 UWP CoreWindow 或 Win32 HWND 的 HolographicSpace，你将使用该 HolographicSpace 来处理全息相机、创建坐标系统和执行全息着色。 当前全息空间用于 DirectX 模板中的多个位置：
* 若要创建 Direct3D 设备， **DeviceResources**类需要从 HolographicSpace 对象获取一些信息。 这是与全息显示器关联的 DXGI 适配器 ID。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类使用应用的 Direct3D 11 设备来创建和管理基于设备的资源，例如每个全息相机的后台缓冲区。 如果你有兴趣查看此函数的作用，你可以在 DeviceResources 中找到它。
* 函数**DeviceResources：： InitializeUsingHolographicSpace**演示了如何通过查找 LUID 获取适配器，以及如何在未指定首选适配器的情况下选择默认适配器。
* 应用的主类使用**AppView：： SetWindow**中的全息空间或**应用：： CreateWindowAndHolographicSpace**进行更新和呈现。

>[!NOTE]
>以下各节介绍了模板中的函数名称（如**AppView：： SetWindow** ），该模板假设你从全息 UWP 应用程序模板开始，你看到的代码段将在 UWP 和 Win32 应用中均匀应用。

接下来，我们将深入探讨**SetHolographicSpace**在 AppMain 类中所负责的设置过程。

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>订阅照相机事件，创建和删除相机资源

您的应用程序的全息内容位于其全息空间中，并且通过一个或多个全息相机进行查看，这在场景上表现出了不同的观点。 现在您已经有了全息空间，您可以接收全息相机的数据了。

应用需要通过创建特定于该相机的任何资源（如后台缓冲区呈现目标视图）来响应**CameraAdded**事件。 在应用创建任何全息帧之前，可以在**DeviceResources：： SetHolographicSpace**函数中看到此代码，由**AppView：： SetWindow**调用：

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

您的应用程序还需要通过释放为该照相机创建的资源来响应**CameraRemoved**事件。

From **DeviceResources：： SetHolographicSpace**：

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

事件处理程序必须完成一些工作才能使全息呈现流畅地流动，并使应用能够根本呈现。 阅读详细信息的代码和备注：可以在主类中查找**OnCameraAdded**和**OnCameraRemoved** ，以了解如何通过**DeviceResources**处理**m_cameraResources**映射。

现在，我们将重点放在 AppMain 和设置上，使应用程序能够了解全息相机。 考虑到这一点，请务必注意以下两个要求：

1. 对于**CameraAdded**事件处理程序，应用程序可以异步工作，为新的全息相机完成创建资源和加载资产的操作。 需要多个帧来完成此项工作的应用应请求延迟，并在异步加载后完成延迟;[PPL 任务](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)可用于执行异步工作。 您的应用程序必须确保在退出事件处理程序时或在完成延迟时立即呈现给该摄像机。 退出事件处理程序或完成延迟，告诉系统你的应用程序现已准备好接收包含该相机的全息帧。

2. 当应用接收到**CameraRemoved**事件时，它必须释放对后台缓冲区的所有引用并立即退出函数。 这包括呈现目标视图和可能包含对[IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)的引用的任何其他资源。 应用还必须确保后台缓冲区不会附加为呈现器目标，如**CameraResources：： ReleaseResourcesForBackBuffer**中所示。 为了帮助提高速度，你的应用程序可以释放后台缓冲区，然后启动任务以异步完成拆下相机所需的任何其他工作。 全息应用模板包括可用于此目的的 PPL 任务。

>[!NOTE]
>如果要确定在帧上显示的是已添加或已删除的照相机，请使用**HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras)和[RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)属性。

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>为全息内容创建参考框架

应用的内容必须位于要在 HolographicSpace 中呈现的[空间坐标系统](coordinate-systems-in-directx.md)中。 系统提供了两个主要的参考框架，可用于为全息影像建立坐标系统。

Windows 全息版中有两种参考帧：附加到设备的参考框架，以及设备在用户的环境中移动时保持静止的参考帧。 默认情况下，全息应用模板使用固定的参考框架。这是一种最简单的方式来呈现全球锁定的全息影像。

固定参考帧旨在使设备当前位置附近的位置稳定。 这意味着，在设备更多地了解它周围的空间时，允许从设备进行的其他协调与用户的环境略有不同。 可以通过两种方法创建固定的引用框架：从[空间阶段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)获取坐标系统，或使用默认的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。 如果要为沉浸式耳机创建 Windows Mixed Reality 应用，建议的起点是[空间阶段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，它还提供了有关玩家戴显示的沉浸式耳机功能的信息。 在这里，我们将演示如何使用默认的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。

空间定位符代表 Windows Mixed Reality 设备，并跟踪设备的运动，并提供可以相对于其位置所理解的坐标系统。

From **AppMain：： OnHolographicDisplayIsAvailableChanged**：

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

当应用程序启动时，创建静止引用框架。 这类似于定义一个世界坐标系统，并在应用程序启动时将原点置于设备位置。 此参考框架不会随设备一起移动。

From **AppMain：： SetHolographicSpace**：

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

所有引用帧都是重力对齐的，这意味着 y 轴指向用户环境的 "向上"。 由于 Windows 使用 "右手传" 坐标系统，因此在创建引用框架时，-z 轴的方向与设备的 "向前" 方向一致。

>[!NOTE]
>当你的应用程序需要精确放置单独的全息影像时，请使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>将各个全息图锚定到现实世界中的某个位置。 例如，当用户指示某个点是特别感兴趣的点时，请使用空间锚。 定位点位置不会偏移，但可以调整它们。 默认情况下，当调整定位点后，它会在更正发生后，使其在接下来的几个帧上出现位置。 如果出现这种情况，则可能需要以不同的方式处理调整（例如，将其推迟到全息图外），这取决于你的应用程序。 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>属性和<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件启用这些自定义项。

## <a name="respond-to-locatability-changed-events"></a>响应 locatability 已更改事件

渲染世界上锁定的全息影像要求设备能够在世界各地找到自己。 这并不总是可能的，因为存在环境情况，如果是这样，则用户可能会发现跟踪中断的视觉指示。 此视觉对象的指示必须使用附加到设备的参考框架而不是在世界上。

如果出于任何原因导致跟踪中断，你的应用程序可以请求通知。 注册 LocatabilityChanged 事件，检测设备在世界上发生变化的能力。 From **AppMain：： SetHolographicSpace：**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

然后，使用此事件来确定何时无法在世界范围内静止全息影像。

## <a name="see-also"></a>另请参阅
* [在 DirectX 中渲染](rendering-in-directx.md)
* [DirectX 中的坐标系统](coordinate-systems-in-directx.md)
