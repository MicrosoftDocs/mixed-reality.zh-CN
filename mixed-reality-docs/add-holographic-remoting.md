---
title: 添加全息远程处理
description: 介绍如何使用全息远程处理通过网络将全息影像呈现到 HoloLens。
author: mikeriches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality，全息影像，全息远程处理，远程渲染，网络渲染，HoloLens，远程全息影像
ms.openlocfilehash: 2f6ade5552c993f66281d0be8a7e62c8f076deac
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277705"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a><span data-ttu-id="bc4ab-104">添加全息远程处理（HoloLens （第一代））</span><span class="sxs-lookup"><span data-stu-id="bc4ab-104">Add Holographic Remoting (HoloLens (1st gen))</span></span>

>[!IMPORTANT]
><span data-ttu-id="bc4ab-105">本文档介绍了如何为 HoloLens 1 创建主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="bc4ab-106">适用于 HoloLens 的主机应用程序 **（第一代）** 必须使用 NuGet**包版本1.x。**</span><span class="sxs-lookup"><span data-stu-id="bc4ab-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="bc4ab-107">这意味着，为 HoloLens 1 编写的主机应用程序与 HoloLens 2 不兼容，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="bc4ab-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bc4ab-108">HoloLens 2</span></span>

<span data-ttu-id="bc4ab-109">使用全息远程处理的 HoloLens 开发人员需要更新其应用程序，使其与 HoloLens 2 兼容。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="bc4ab-110">这需要全新版本的全息远程处理 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="bc4ab-111">如果使用全息远程处理 NuGet 包的应用程序的版本号小于2.0.0.0，尝试连接到 HoloLens 2 上的全息远程处理播放机，则连接将失败。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-111">If an application using the Holographic Remoting NuGet package with a version number smaller than 2.0.0.0 attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>

>[!NOTE]
><span data-ttu-id="bc4ab-112">可在[此处](holographic-remoting-create-host.md)找到特定于 HoloLens 2 的指南。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-host.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="bc4ab-113">将全息远程处理添加到桌面或 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="bc4ab-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="bc4ab-114">本页介绍如何向桌面或 UWP 应用添加全息远程处理。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="bc4ab-115">使用全息远程处理，你的应用程序可以面向在台式计算机或 UWP 设备（如 Xbox 设备）上托管的全息内容的 HoloLens，并允许访问更多系统资源，并使你能够将远程[沉浸式视图](app-views.md)集成到现有的台式计算机软件中。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-115">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="bc4ab-116">远程处理主机应用从 HoloLens 接收输入数据流，在虚拟沉浸式视图中呈现内容，并将内容帧流式传输回 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-116">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="bc4ab-117">使用标准 Wi-fi 建立连接。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-117">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="bc4ab-118">若要使用远程处理，你将使用 NuGet 包将全息远程处理添加到桌面或 UWP 应用，并编写代码来处理连接并在沉浸式视图中呈现。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-118">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="bc4ab-119">帮助程序库包括在代码示例中，用于简化设备连接的处理任务。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-119">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="bc4ab-120">典型的远程处理连接的延迟最低为50毫秒。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-120">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="bc4ab-121">播放机应用可以实时报告滞后时间。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-121">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="bc4ab-122">本文中的代码片段当前演示了C++ C++ [ C++ ](creating-a-holographic-directx-project.md)如何使用/cx 而不是 C + 17 兼容/WinRT，这与全息项目模板中使用的不同。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-122">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="bc4ab-123">概念对于C++/WinRT 项目是等效的，但你将需要转换代码。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-123">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="bc4ab-124">获取远程处理 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="bc4ab-124">Get the remoting NuGet packages</span></span>

<span data-ttu-id="bc4ab-125">按照以下步骤获取用于全息远程处理的 NuGet 包，并从项目中添加引用：</span><span class="sxs-lookup"><span data-stu-id="bc4ab-125">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="bc4ab-126">在 Visual Studio 中中转到你的项目。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-126">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="bc4ab-127">右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "</span><span class="sxs-lookup"><span data-stu-id="bc4ab-127">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="bc4ab-128">在出现的面板中，单击 "**浏览**"，然后搜索 "全息远程处理"。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-128">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="bc4ab-129">选择 **"** "，然后单击 "**安装**"。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-129">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="bc4ab-130">如果**预览**对话框出现，请单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-130">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="bc4ab-131">显示的下一个对话框是许可协议。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-131">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="bc4ab-132">单击 "**我接受**" 接受许可协议。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-132">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="bc4ab-133">创建 HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="bc4ab-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="bc4ab-134">首先，需要 HolographicStreamerHelpers 的实例。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-134">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="bc4ab-135">将此添加到将处理远程处理的类。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-135">Add this to the class that will be handling remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="bc4ab-136">还需要跟踪连接状态。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-136">You'll also need to track connection state.</span></span> <span data-ttu-id="bc4ab-137">如果要呈现预览，则需要有要将其复制到的纹理。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-137">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="bc4ab-138">还需要一些功能，如连接状态锁定、用于存储 HoloLens IP 地址等的方法。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-138">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="bc4ab-139">初始化 HolographicStreamerHelpers 并连接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="bc4ab-139">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="bc4ab-140">若要连接到 HoloLens 设备，请创建 HolographicStreamerHelpers 的实例并连接到目标 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-140">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="bc4ab-141">你将需要设置视频帧大小以匹配 HoloLens 显示宽度和高度，因为全息远程处理库需要编码器和解码器解析完全匹配。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-141">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="bc4ab-142">设备连接是异步的。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-142">The device connection is asynchronous.</span></span> <span data-ttu-id="bc4ab-143">应用需要为连接、断开连接和帧发送事件提供事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-143">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="bc4ab-144">OnConnected 事件可以更新 UI，开始呈现，等等。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-144">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="bc4ab-145">在我们的桌面代码示例中，我们使用 "已连接" 消息更新窗口标题。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-145">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="bc4ab-146">OnDisconnected 事件可以处理重新连接、UI 更新等。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-146">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="bc4ab-147">在此示例中，如果发生暂时性故障，则重新连接。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-147">In this example, we reconnect if there is a transient failure.</span></span>

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="bc4ab-148">当远程处理组件准备好发送帧时，您的应用程序将有机会在 SendFrameEvent 中创建它的副本。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-148">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="bc4ab-149">在这里，我们将帧复制到一个交换链，以便可以在预览窗口中显示它。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-149">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="bc4ab-150">呈现全息内容</span><span class="sxs-lookup"><span data-stu-id="bc4ab-150">Render holographic content</span></span>

<span data-ttu-id="bc4ab-151">若要使用远程处理呈现内容，请在桌面或 UWP 应用中设置一个虚拟 IFrameworkView，并处理远程处理中的全息帧。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-151">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="bc4ab-152">所有 Windows 全息 Api 的使用方式与此视图相同，但设置略有不同。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-152">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="bc4ab-153">全息空间和语音组件来自 HolographicRemotingHelpers 类，而不是自行创建：</span><span class="sxs-lookup"><span data-stu-id="bc4ab-153">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="bc4ab-154">不在 Run 方法内部使用 update 循环，而是通过桌面或 UWP 应用程序的主循环来提供滴答更新。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-154">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="bc4ab-155">这允许桌面或 UWP 应用保持对消息处理的控制。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-155">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="bc4ab-156">全息应用视图的 Tick （）方法完成更新、绘制和呈现循环的一次迭代。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-156">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="bc4ab-157">全息应用视图的更新、呈现和呈现循环与在 HoloLens 上运行时完全相同，只是你有权访问台式计算机上更多的系统资源。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-157">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="bc4ab-158">您可以呈现更多的三角形，更多的绘图走刀，执行更多物理学，并使用 x64 进程加载需要 2 GB 以上 RAM 的内容。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-158">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="bc4ab-159">断开并结束远程会话</span><span class="sxs-lookup"><span data-stu-id="bc4ab-159">Disconnect and end the remote session</span></span>

<span data-ttu-id="bc4ab-160">若要断开连接，例如，当用户单击 UI 按钮以断开 HolographicStreamerHelpers 上的调用 Disconnect （），然后释放对象。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-160">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="bc4ab-161">获取远程处理播放机</span><span class="sxs-lookup"><span data-stu-id="bc4ab-161">Get the remoting player</span></span>

<span data-ttu-id="bc4ab-162">Windows 全息远程处理播放机在 Windows 应用商店中提供，作为要连接到的远程处理主机应用的终结点。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-162">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="bc4ab-163">若要获取 Windows 全息远程处理播放器，请从 HoloLens 访问 Windows 应用商店，搜索远程处理并下载应用。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-163">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="bc4ab-164">远程处理播放机包含一项功能，可用于在屏幕上显示统计信息，这在调试远程处理主机应用时非常有用。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-164">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="bc4ab-165">备注和资源</span><span class="sxs-lookup"><span data-stu-id="bc4ab-165">Notes and resources</span></span>

<span data-ttu-id="bc4ab-166">全息应用视图需要提供一种方法来为你的应用提供 Direct3D 设备，该设备必须用于初始化全息空间。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-166">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="bc4ab-167">应用应使用此 Direct3D 设备复制和显示预览框架。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-167">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="bc4ab-168">**代码示例：** 提供完整的全息远程处理代码示例，其中包含一个全息应用程序视图，该视图与用于桌面 Win32、UWP DirectX 和具有 XAML 的 UWP 的远程处理和远程处理主机项目兼容。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-168">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="bc4ab-169">若要获取它，请转到此处：</span><span class="sxs-lookup"><span data-stu-id="bc4ab-169">To get it, go here:</span></span>
* [<span data-ttu-id="bc4ab-170">用于远程处理的 Windows 全息代码示例</span><span class="sxs-lookup"><span data-stu-id="bc4ab-170">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="bc4ab-171">**调试说明：** 全息远程处理库可能会引发第一次异常。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-171">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="bc4ab-172">这些异常在调试会话中可能会显示，具体取决于目前处于活动状态的 Visual Studio 异常设置。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-172">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="bc4ab-173">这些例外由全息远程处理库在内部捕获，可被忽略。</span><span class="sxs-lookup"><span data-stu-id="bc4ab-173">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
