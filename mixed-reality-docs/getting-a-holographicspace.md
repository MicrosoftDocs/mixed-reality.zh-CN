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
# <a name="getting-a-holographicspace"></a><span data-ttu-id="eae7a-104">获取 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="eae7a-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="eae7a-105"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类是进入全息世界的门户。</span><span class="sxs-lookup"><span data-stu-id="eae7a-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="eae7a-106">它控制沉浸式呈现，提供相机数据，并提供对空间推理 Api 的访问。</span><span class="sxs-lookup"><span data-stu-id="eae7a-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="eae7a-107">您将创建一个用于 UWP 应用<a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a>或 Win32 应用程序的 HWND。</span><span class="sxs-lookup"><span data-stu-id="eae7a-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="eae7a-108">设置 holographic 空间</span><span class="sxs-lookup"><span data-stu-id="eae7a-108">Set up the holographic space</span></span>

<span data-ttu-id="eae7a-109">创建 holographic 空间对象是对 Windows Mixed Reality 应用进行访问的第一步。</span><span class="sxs-lookup"><span data-stu-id="eae7a-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="eae7a-110">传统的 Windows 应用程序呈现到为其应用程序视图的核心窗口创建 Direct3D 交换链。</span><span class="sxs-lookup"><span data-stu-id="eae7a-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="eae7a-111">此交换链向一台平板电脑 holographic UI 中显示。</span><span class="sxs-lookup"><span data-stu-id="eae7a-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="eae7a-112">若要使应用程序视图而不是 2D 盖板 holographic，创建其核心窗口而不是交换链的 holographic 空间。</span><span class="sxs-lookup"><span data-stu-id="eae7a-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="eae7a-113">显示创建此 holographic 空格的 holographic 帧将您的应用程序放入的全屏呈现模式。</span><span class="sxs-lookup"><span data-stu-id="eae7a-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="eae7a-114">有关**UWP 应用**[从开始*全息版的 DirectX 11 应用 (通用 Windows) 模板*](creating-a-holographic-directx-project.md)，查找在此代码**SetWindow**AppView.cpp 中的方法：</span><span class="sxs-lookup"><span data-stu-id="eae7a-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="eae7a-115">有关**Win32 应用程序**[从开始*BasicHologram* Win32 示例](creating-a-holographic-directx-project.md#creating-a-win32-project)，看看**App::CreateWindowAndHolographicSpace**为如何创建 HWND，然后将其转换为令人着迷的 HWND 通过创建一个关联的示例<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="eae7a-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
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

<span data-ttu-id="eae7a-116">现在，已为你的 UWP CoreWindow 或 Win32 HWND 来获取 HolographicSpace，将使用该 HolographicSpace 来处理 holographic 照相机和创建坐标系统完成全息呈现。</span><span class="sxs-lookup"><span data-stu-id="eae7a-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="eae7a-117">在 DirectX 模板中的多个位置使用的当前的 holographic 空间：</span><span class="sxs-lookup"><span data-stu-id="eae7a-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="eae7a-118">**DeviceResources**类需要获取一些信息从 HolographicSpace 对象以便创建 Direct3D 设备。</span><span class="sxs-lookup"><span data-stu-id="eae7a-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="eae7a-119">这是与 holographic 显示关联的 DXGI 适配器 ID。</span><span class="sxs-lookup"><span data-stu-id="eae7a-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="eae7a-120"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>类使用应用程序的 Direct3D 11 设备创建和管理基于设备的资源，例如用于每个 holographic 相机后台缓冲区。</span><span class="sxs-lookup"><span data-stu-id="eae7a-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="eae7a-121">如果您想要查看该函数执行实质上，会发现它在 DeviceResources.cpp。</span><span class="sxs-lookup"><span data-stu-id="eae7a-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="eae7a-122">该函数**DeviceResources::InitializeUsingHolographicSpace**演示如何获取适配器通过查找 LUID – 以及如何选择默认适配器时不指定了任何首选的适配器。</span><span class="sxs-lookup"><span data-stu-id="eae7a-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="eae7a-123">应用程序的主类使用的 holographic 空间**AppView::SetWindow**或**App::CreateWindowAndHolographicSpace**更新和呈现。</span><span class="sxs-lookup"><span data-stu-id="eae7a-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="eae7a-124">以下部分指出模板中的函数名喜欢**AppView::SetWindow** ，认为从全息版的 UWP 应用模板开始，你看到的代码段将跨 UWP 和 Win32 应用同样适用。</span><span class="sxs-lookup"><span data-stu-id="eae7a-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="eae7a-125">接下来，我们将深入探究安装流程**SetHolographicSpace**负责 AppMain 类中。</span><span class="sxs-lookup"><span data-stu-id="eae7a-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="eae7a-126">相机事件订阅、 创建和删除照相机资源</span><span class="sxs-lookup"><span data-stu-id="eae7a-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="eae7a-127">应用的 holographic 内容位于其 holographic 空间，通过一个或多个 holographic 相机表示场景的视角查看。</span><span class="sxs-lookup"><span data-stu-id="eae7a-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="eae7a-128">现在，已 holographic 空间，可以接收用于 holographic 相机的数据。</span><span class="sxs-lookup"><span data-stu-id="eae7a-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="eae7a-129">您的应用程序需要响应**CameraAdded**类似后台缓冲区呈现目标视图，通过创建任何资源的事件是特定于该摄像机。</span><span class="sxs-lookup"><span data-stu-id="eae7a-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="eae7a-130">您可以查看在此代码**DeviceResources::SetHolographicSpace**由调用的函数**AppView::SetWindow**应用创建任何 holographic 帧之前：</span><span class="sxs-lookup"><span data-stu-id="eae7a-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="eae7a-131">您的应用程序还需要响应**CameraRemoved**通过释放针对该相机而创建的资源的事件。</span><span class="sxs-lookup"><span data-stu-id="eae7a-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="eae7a-132">从**DeviceResources::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="eae7a-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="eae7a-133">事件处理程序必须完成一些工作才能使全息呈现流动非常顺利，以便您的应用程序是能够在所有呈现。</span><span class="sxs-lookup"><span data-stu-id="eae7a-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="eae7a-134">读取代码和注释的详细信息： 则可以寻找**OnCameraAdded**和**OnCameraRemoved**若要了解你主类中如何**m_cameraResources**映射是由处理**DeviceResources**。</span><span class="sxs-lookup"><span data-stu-id="eae7a-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="eae7a-135">现在，我们会集中 AppMain 和安装程序，它会使你的应用需要了解的有关 holographic 照相机。</span><span class="sxs-lookup"><span data-stu-id="eae7a-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="eae7a-136">明确这一点后，务必要记下以下两个要求：</span><span class="sxs-lookup"><span data-stu-id="eae7a-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="eae7a-137">有关**CameraAdded**事件处理程序，该应用程序如何工作，以异步方式完成创建资源并加载新 holographic 照相机的资产。</span><span class="sxs-lookup"><span data-stu-id="eae7a-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="eae7a-138">需要多个帧来完成这项工作的应用程序应请求延迟，并后以异步方式; 加载完成延迟[PPL 任务](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl)可用于执行异步工作。</span><span class="sxs-lookup"><span data-stu-id="eae7a-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="eae7a-139">您的应用程序必须确保它已准备好呈现到该摄像机立即退出事件处理程序时或当它完成时延迟。</span><span class="sxs-lookup"><span data-stu-id="eae7a-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="eae7a-140">退出事件处理程序或完成此延迟会告知系统您的应用程序现在已准备好接收 holographic 帧与包含该摄像机。</span><span class="sxs-lookup"><span data-stu-id="eae7a-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="eae7a-141">当应用收到**CameraRemoved**事件，它必须释放对该函数右键消失的后台缓冲区和出口的所有引用。</span><span class="sxs-lookup"><span data-stu-id="eae7a-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="eae7a-142">这包括呈现器目标视图，并可能会保存对引用的任何其他资源[IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)。</span><span class="sxs-lookup"><span data-stu-id="eae7a-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="eae7a-143">应用程序还必须确保后台缓冲区未附加作为呈现器目标，如中所示**CameraResources::ReleaseResourcesForBackBuffer**。</span><span class="sxs-lookup"><span data-stu-id="eae7a-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="eae7a-144">若要帮助加速此过程，您的应用程序可以释放后台缓冲区，然后启动任务以异步方式完成，才可关闭该摄像机的任何其他工作。</span><span class="sxs-lookup"><span data-stu-id="eae7a-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="eae7a-145">全息版的应用程序模板包含可用于此目的的 PPL 任务。</span><span class="sxs-lookup"><span data-stu-id="eae7a-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="eae7a-146">如果你想要确定何时添加或删除照相机显示在框架中，使用**HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras)并[RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras)属性。</span><span class="sxs-lookup"><span data-stu-id="eae7a-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="eae7a-147">创建一个参考框架为您全息版的内容</span><span class="sxs-lookup"><span data-stu-id="eae7a-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="eae7a-148">应用程序的内容必须在定位[空间坐标系统](coordinate-systems-in-directx.md)HolographicSpace 中呈现。</span><span class="sxs-lookup"><span data-stu-id="eae7a-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="eae7a-149">系统提供了两个主要的参考框架用于建立在全息坐标系统。</span><span class="sxs-lookup"><span data-stu-id="eae7a-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="eae7a-150">有两种类型的参考帧中 Windows Holographic： 引用附加到该设备的框架和保持静止状态，因为随着用户的环境的移动设备的参考框架。</span><span class="sxs-lookup"><span data-stu-id="eae7a-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="eae7a-151">全息版的应用程序模板的固定参考框架使用默认设置。这是最简单的方式来呈现世界锁定全息之一。</span><span class="sxs-lookup"><span data-stu-id="eae7a-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="eae7a-152">固定参考框架旨在以达到稳定状态的设备的当前位置附近的位置。</span><span class="sxs-lookup"><span data-stu-id="eae7a-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="eae7a-153">这意味着，允许最荒谬不过设备坐标略有偏移相对于用户的环境为设备了解到有关它周围的空间的详细信息。</span><span class="sxs-lookup"><span data-stu-id="eae7a-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="eae7a-154">有两种方法来创建固定参考框架： 获取从坐标系[空间阶段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，或使用默认<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。</span><span class="sxs-lookup"><span data-stu-id="eae7a-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="eae7a-155">如果要创建适用于沉浸式耳机的 Windows Mixed Reality 应用，建议的起始点是[空间阶段](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)，还提供了有关功能的播放机随身配备沉浸式头戴式耳机。</span><span class="sxs-lookup"><span data-stu-id="eae7a-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="eae7a-156">在这里，我们演示如何使用默认值<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>。</span><span class="sxs-lookup"><span data-stu-id="eae7a-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="eae7a-157">空间定位符表示 Windows Mixed Reality 设备和跟踪设备的动作，并提供可以理解相对于其位置的坐标系统。</span><span class="sxs-lookup"><span data-stu-id="eae7a-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="eae7a-158">从**AppMain::OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="eae7a-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="eae7a-159">在应用启动时，一次创建固定参考框架。</span><span class="sxs-lookup"><span data-stu-id="eae7a-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="eae7a-160">这是类似于定义世界坐标系，带有时启动应用程序放置在设备的位置处的原点。</span><span class="sxs-lookup"><span data-stu-id="eae7a-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="eae7a-161">此参考框架不会随设备一起移动。</span><span class="sxs-lookup"><span data-stu-id="eae7a-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="eae7a-162">从**AppMain::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="eae7a-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="eae7a-163">所有引用帧都是重力对齐，这意味着与用户的环境相关的 y 轴"向上"箭头。</span><span class="sxs-lookup"><span data-stu-id="eae7a-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="eae7a-164">由于 Windows 使用"惯用右手"坐标系，– z 轴的方向与设备时创建的参考框架为面向"forward"方向。</span><span class="sxs-lookup"><span data-stu-id="eae7a-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="eae7a-165">当您的应用程序需要精确地放置各个全息时，使用<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>锚定到现实生活中的位置的单个全息图。</span><span class="sxs-lookup"><span data-stu-id="eae7a-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="eae7a-166">当用户指示特殊感兴趣的一个点，例如，使用空间的定位点。</span><span class="sxs-lookup"><span data-stu-id="eae7a-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="eae7a-167">定位点位置不执行偏差，但它们可以进行调整。</span><span class="sxs-lookup"><span data-stu-id="eae7a-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="eae7a-168">默认情况下，在定位点调整后，它简化了其位置到位的下一步的多个帧上发生更正后。</span><span class="sxs-lookup"><span data-stu-id="eae7a-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="eae7a-169">根据应用程序中，发生此情况时您可能需要调整以不同方式处理 （例如，推迟到全息图均不可见）。</span><span class="sxs-lookup"><span data-stu-id="eae7a-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="eae7a-170"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a>属性和<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a>事件启用这些自定义。</span><span class="sxs-lookup"><span data-stu-id="eae7a-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="eae7a-171">响应 locatability 更改事件</span><span class="sxs-lookup"><span data-stu-id="eae7a-171">Respond to locatability changed events</span></span>

<span data-ttu-id="eae7a-172">呈现世界锁定全息要求设备必须能够在世界中找到自身。</span><span class="sxs-lookup"><span data-stu-id="eae7a-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="eae7a-173">这可能始终无法可能由于环境条件，如果是这样，用户可能预期跟踪中断的直观指示。</span><span class="sxs-lookup"><span data-stu-id="eae7a-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="eae7a-174">必须使用附加到该设备，而不是固定且世界的参考帧呈现此可视指示。</span><span class="sxs-lookup"><span data-stu-id="eae7a-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="eae7a-175">你的应用可以请求如果出于任何原因中断跟踪获得通知。</span><span class="sxs-lookup"><span data-stu-id="eae7a-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="eae7a-176">注册 LocatabilityChanged 事件来检测时查找本身中的世界更改设备的能力。</span><span class="sxs-lookup"><span data-stu-id="eae7a-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="eae7a-177">从**AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="eae7a-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="eae7a-178">然后使用此事件以确定无法全息呈现到世界上保持静止时。</span><span class="sxs-lookup"><span data-stu-id="eae7a-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="eae7a-179">请参阅</span><span class="sxs-lookup"><span data-stu-id="eae7a-179">See also</span></span>
* [<span data-ttu-id="eae7a-180">在 DirectX 中呈现</span><span class="sxs-lookup"><span data-stu-id="eae7a-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="eae7a-181">在 DirectX 的坐标系统</span><span class="sxs-lookup"><span data-stu-id="eae7a-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
