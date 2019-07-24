---
title: 获取 HolographicSpace
description: 介绍 HolographicSpace API, 这是全息呈现和空间输入的核心概念。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, 空间输入, 呈现, 交换链, 全息帧, 更新循环, 游戏循环, 引用框架, locatability, 示例代码, 演练
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525445"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="674b9-104">获取 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="674b9-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="674b9-105"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类是您在全息环境中的门户。</span><span class="sxs-lookup"><span data-stu-id="674b9-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="674b9-106">它控制沉浸式渲染、提供相机数据, 并提供对空间推理 Api 的访问。</span><span class="sxs-lookup"><span data-stu-id="674b9-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="674b9-107">你将为 UWP 应用的<a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a>或 Win32 应用的 HWND 创建一个。</span><span class="sxs-lookup"><span data-stu-id="674b9-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="674b9-108">设置全息空间</span><span class="sxs-lookup"><span data-stu-id="674b9-108">Set up the holographic space</span></span>

<span data-ttu-id="674b9-109">创建全息空间对象是创建 Windows Mixed Reality 应用程序的第一步。</span><span class="sxs-lookup"><span data-stu-id="674b9-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="674b9-110">传统的 Windows 应用会呈现给为其应用程序视图的核心窗口创建的 Direct3D 交换链。</span><span class="sxs-lookup"><span data-stu-id="674b9-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="674b9-111">此交换链在全息 UI 中显示为一个石板。</span><span class="sxs-lookup"><span data-stu-id="674b9-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="674b9-112">若要使应用程序视图为全息而不是2D 石板, 请为其核心窗口而不是交换链创建一个全息空间。</span><span class="sxs-lookup"><span data-stu-id="674b9-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="674b9-113">提供此全息空间创建的全息帧会使您的应用程序进入全屏呈现模式。</span><span class="sxs-lookup"><span data-stu-id="674b9-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="674b9-114">对于[从 "*全息 DirectX 11 应用 (通用 Windows)" 模板*开始](creating-a-holographic-directx-project.md)的**UWP 应用**, 请在 AppView 中的**SetWindow**方法中查找此代码:</span><span class="sxs-lookup"><span data-stu-id="674b9-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="674b9-115">对于[从*BasicHologram* win32 示例开始](creating-a-holographic-directx-project.md#creating-a-win32-project)的**Win32 应用**, 请查看**app:: CreateWindowAndHolographicSpace** , 了解如何创建 HWND, 然后通过创建关联<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">的来将其转换为沉浸式 HWNDHolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="674b9-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
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

<span data-ttu-id="674b9-116">现在, 你已获得 UWP CoreWindow 或 Win32 HWND 的 HolographicSpace, 你将使用该 HolographicSpace 来处理全息相机、创建坐标系统和执行全息着色。</span><span class="sxs-lookup"><span data-stu-id="674b9-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="674b9-117">当前全息空间用于 DirectX 模板中的多个位置:</span><span class="sxs-lookup"><span data-stu-id="674b9-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="674b9-118">若要创建 Direct3D 设备, **DeviceResources**类需要从 HolographicSpace 对象获取一些信息。</span><span class="sxs-lookup"><span data-stu-id="674b9-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="674b9-119">这是与全息显示器关联的 DXGI 适配器 ID。</span><span class="sxs-lookup"><span data-stu-id="674b9-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="674b9-120"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类使用应用的 Direct3D 11 设备来创建和管理基于设备的资源, 例如每个全息相机的后台缓冲区。</span><span class="sxs-lookup"><span data-stu-id="674b9-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="674b9-121">如果你有兴趣查看此函数的作用, 你可以在 DeviceResources 中找到它。</span><span class="sxs-lookup"><span data-stu-id="674b9-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="674b9-122">函数**DeviceResources:: InitializeUsingHolographicSpace**演示了如何通过查找 LUID 获取适配器, 以及如何在未指定首选适配器的情况下选择默认适配器。</span><span class="sxs-lookup"><span data-stu-id="674b9-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="674b9-123">应用的主类使用**AppView:: SetWindow**中的全息空间或**应用:: CreateWindowAndHolographicSpace**进行更新和呈现。</span><span class="sxs-lookup"><span data-stu-id="674b9-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="674b9-124">以下各节介绍了模板中的函数名称 (如**AppView:: SetWindow** ), 该模板假设你从全息 UWP 应用程序模板开始, 你看到的代码段将在 UWP 和 Win32 应用中均匀应用。</span><span class="sxs-lookup"><span data-stu-id="674b9-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="674b9-125">接下来, 我们将深入探讨**SetHolographicSpace**在 AppMain 类中所负责的设置过程。</span><span class="sxs-lookup"><span data-stu-id="674b9-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="674b9-126">订阅照相机事件, 创建和删除相机资源</span><span class="sxs-lookup"><span data-stu-id="674b9-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="674b9-127">您的应用程序的全息内容位于其全息空间中, 并且通过一个或多个全息相机进行查看, 这在场景上表现出了不同的观点。</span><span class="sxs-lookup"><span data-stu-id="674b9-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="674b9-128">现在您已经有了全息空间, 您可以接收全息相机的数据了。</span><span class="sxs-lookup"><span data-stu-id="674b9-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="674b9-129">应用需要通过创建特定于该相机的任何资源 (如后台缓冲区呈现目标视图) 来响应**CameraAdded**事件。</span><span class="sxs-lookup"><span data-stu-id="674b9-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="674b9-130">在应用创建任何全息帧之前, 可以在**DeviceResources:: SetHolographicSpace**函数中看到此代码, 由**AppView:: SetWindow**调用:</span><span class="sxs-lookup"><span data-stu-id="674b9-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="674b9-131">您的应用程序还需要通过释放为该照相机创建的资源来响应**CameraRemoved**事件。</span><span class="sxs-lookup"><span data-stu-id="674b9-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="674b9-132">From **DeviceResources:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="674b9-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="674b9-133">事件处理程序必须完成一些工作才能使全息呈现流畅地流动, 并使应用能够根本呈现。</span><span class="sxs-lookup"><span data-stu-id="674b9-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="674b9-134">阅读详细信息中的代码和备注: 可以在主类中查找**OnCameraAdded**和**OnCameraRemoved** , 以了解如何通过**DeviceResources**处理**m_cameraResources**映射。</span><span class="sxs-lookup"><span data-stu-id="674b9-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="674b9-135">现在, 我们将重点放在 AppMain 和设置上, 使应用程序能够了解全息相机。</span><span class="sxs-lookup"><span data-stu-id="674b9-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="674b9-136">考虑到这一点, 请务必注意以下两个要求:</span><span class="sxs-lookup"><span data-stu-id="674b9-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="674b9-137">对于**CameraAdded**事件处理程序, 应用程序可以异步工作, 为新的全息相机完成创建资源和加载资产的操作。</span><span class="sxs-lookup"><span data-stu-id="674b9-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="674b9-138">需要多个帧来完成此项工作的应用应请求延迟, 并在异步加载后完成延迟;[PPL 任务](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)可用于执行异步工作。</span><span class="sxs-lookup"><span data-stu-id="674b9-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="674b9-139">您的应用程序必须确保在退出事件处理程序时或在完成延迟时立即呈现给该摄像机。</span><span class="sxs-lookup"><span data-stu-id="674b9-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="674b9-140">退出事件处理程序或完成延迟, 告诉系统你的应用程序现已准备好接收包含该相机的全息帧。</span><span class="sxs-lookup"><span data-stu-id="674b9-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="674b9-141">当应用接收到**CameraRemoved**事件时, 它必须释放对后台缓冲区的所有引用并立即退出函数。</span><span class="sxs-lookup"><span data-stu-id="674b9-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="674b9-142">这包括呈现目标视图和可能包含对[IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)的引用的任何其他资源。</span><span class="sxs-lookup"><span data-stu-id="674b9-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="674b9-143">应用还必须确保后台缓冲区不会附加为呈现器目标, 如**CameraResources:: ReleaseResourcesForBackBuffer**中所示。</span><span class="sxs-lookup"><span data-stu-id="674b9-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="674b9-144">为了帮助提高速度, 你的应用程序可以释放后台缓冲区, 然后启动任务以异步完成拆下相机所需的任何其他工作。</span><span class="sxs-lookup"><span data-stu-id="674b9-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="674b9-145">全息应用模板包括可用于此目的的 PPL 任务。</span><span class="sxs-lookup"><span data-stu-id="674b9-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="674b9-146">如果要确定在帧上显示的是已添加或已删除的照相机, 请使用**HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras)和[RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)属性。</span><span class="sxs-lookup"><span data-stu-id="674b9-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="674b9-147">为全息内容创建参考框架</span><span class="sxs-lookup"><span data-stu-id="674b9-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="674b9-148">应用的内容必须位于要在 HolographicSpace 中呈现的[空间坐标系统](coordinate-systems-in-directx.md)中。</span><span class="sxs-lookup"><span data-stu-id="674b9-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="674b9-149">系统提供了两个主要的参考框架, 可用于为全息影像建立坐标系统。</span><span class="sxs-lookup"><span data-stu-id="674b9-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="674b9-150">Windows 全息版中有两种参考帧: 附加到设备的参考框架, 以及设备在用户的环境中移动时保持静止的参考帧。</span><span class="sxs-lookup"><span data-stu-id="674b9-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="674b9-151">默认情况下, 全息应用模板使用固定的参考框架。这是一种最简单的方式来呈现全球锁定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="674b9-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="674b9-152">固定参考帧旨在使设备当前位置附近的位置稳定。</span><span class="sxs-lookup"><span data-stu-id="674b9-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="674b9-153">这意味着, 在设备更多地了解它周围的空间时, 允许从设备进行的其他协调与用户的环境略有不同。</span><span class="sxs-lookup"><span data-stu-id="674b9-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="674b9-154">可以通过两种方法创建固定的引用框架: 从[空间阶段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)获取坐标系统, 或使用默认的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。</span><span class="sxs-lookup"><span data-stu-id="674b9-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="674b9-155">如果要为沉浸式耳机创建 Windows Mixed Reality 应用, 建议的起点是[空间阶段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), 它还提供了有关玩家戴显示的沉浸式耳机功能的信息。</span><span class="sxs-lookup"><span data-stu-id="674b9-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="674b9-156">在这里, 我们将演示如何使用默认的<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。</span><span class="sxs-lookup"><span data-stu-id="674b9-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="674b9-157">空间定位符代表 Windows Mixed Reality 设备, 并跟踪设备的运动, 并提供可以相对于其位置所理解的坐标系统。</span><span class="sxs-lookup"><span data-stu-id="674b9-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="674b9-158">From **AppMain:: OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="674b9-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="674b9-159">当应用程序启动时, 创建静止引用框架。</span><span class="sxs-lookup"><span data-stu-id="674b9-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="674b9-160">这类似于定义一个世界坐标系统, 并在应用程序启动时将原点置于设备位置。</span><span class="sxs-lookup"><span data-stu-id="674b9-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="674b9-161">此参考框架不会随设备一起移动。</span><span class="sxs-lookup"><span data-stu-id="674b9-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="674b9-162">From **AppMain:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="674b9-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="674b9-163">所有引用帧都是重力对齐的, 这意味着 y 轴指向用户环境的 "向上"。</span><span class="sxs-lookup"><span data-stu-id="674b9-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="674b9-164">由于 Windows 使用 "右手传" 坐标系统, 因此在创建引用框架时,-z 轴的方向与设备的 "向前" 方向一致。</span><span class="sxs-lookup"><span data-stu-id="674b9-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="674b9-165">当你的应用程序需要精确放置单独的全息影像时, 请使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>将各个全息图锚定到现实世界中的某个位置。</span><span class="sxs-lookup"><span data-stu-id="674b9-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="674b9-166">例如, 当用户指示某个点是特别感兴趣的点时, 请使用空间锚。</span><span class="sxs-lookup"><span data-stu-id="674b9-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="674b9-167">定位点位置不会偏移, 但可以调整它们。</span><span class="sxs-lookup"><span data-stu-id="674b9-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="674b9-168">默认情况下, 当调整定位点后, 它会在更正发生后, 使其在接下来的几个帧上出现位置。</span><span class="sxs-lookup"><span data-stu-id="674b9-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="674b9-169">如果出现这种情况, 则可能需要以不同的方式处理调整 (例如, 将其推迟到全息图外), 这取决于你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="674b9-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="674b9-170"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>属性和<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件启用这些自定义项。</span><span class="sxs-lookup"><span data-stu-id="674b9-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="674b9-171">响应 locatability 已更改事件</span><span class="sxs-lookup"><span data-stu-id="674b9-171">Respond to locatability changed events</span></span>

<span data-ttu-id="674b9-172">渲染世界上锁定的全息影像要求设备能够在世界各地找到自己。</span><span class="sxs-lookup"><span data-stu-id="674b9-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="674b9-173">这并不总是可能的, 因为存在环境情况, 如果是这样, 则用户可能会发现跟踪中断的视觉指示。</span><span class="sxs-lookup"><span data-stu-id="674b9-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="674b9-174">此视觉对象的指示必须使用附加到设备的参考框架而不是在世界上。</span><span class="sxs-lookup"><span data-stu-id="674b9-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="674b9-175">如果出于任何原因导致跟踪中断, 你的应用程序可以请求通知。</span><span class="sxs-lookup"><span data-stu-id="674b9-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="674b9-176">注册 LocatabilityChanged 事件, 检测设备在世界上发生变化的能力。</span><span class="sxs-lookup"><span data-stu-id="674b9-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="674b9-177">From **AppMain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="674b9-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="674b9-178">然后, 使用此事件来确定何时无法在世界范围内静止全息影像。</span><span class="sxs-lookup"><span data-stu-id="674b9-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="674b9-179">请参阅</span><span class="sxs-lookup"><span data-stu-id="674b9-179">See also</span></span>
* [<span data-ttu-id="674b9-180">在 DirectX 中渲染</span><span class="sxs-lookup"><span data-stu-id="674b9-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="674b9-181">DirectX 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="674b9-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
