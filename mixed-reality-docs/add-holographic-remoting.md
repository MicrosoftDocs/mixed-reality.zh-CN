---
title: 添加 holographic 远程处理
description: 介绍如何使用 Holographic 远程处理以通过网络将全息呈现到 HoloLens。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全息、 全息版的远程处理、 远程呈现、 呈现、 HoloLens，远程全息网络
ms.openlocfilehash: 1e9567976bad1e2b72e95feca292bf3475893230
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270348"
---
# <a name="add-holographic-remoting"></a><span data-ttu-id="86c01-104">添加 holographic 远程处理</span><span class="sxs-lookup"><span data-stu-id="86c01-104">Add holographic remoting</span></span>

## <a name="hololens-2"></a><span data-ttu-id="86c01-105">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="86c01-105">HoloLens 2</span></span>

> [!NOTE]
> <span data-ttu-id="86c01-106">特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="86c01-106">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="86c01-107">使用 Holographic 远程处理的 HoloLens 开发人员将需要更新其应用程序，使它们与 HoloLens 2 兼容。</span><span class="sxs-lookup"><span data-stu-id="86c01-107">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span>  <span data-ttu-id="86c01-108">这将要求尚不可公开可用的 Holographic 远程处理 NuGet 包的新版本。</span><span class="sxs-lookup"><span data-stu-id="86c01-108">This will require a new version of the Holographic Remoting NuGet package that is not publicly available yet.</span></span>  <span data-ttu-id="86c01-109">如果使用 HoloLens NuGet 包的应用程序尝试连接到 HoloLens 2 上全息版的远程处理播放机，则连接将失败。</span><span class="sxs-lookup"><span data-stu-id="86c01-109">If an application using the HoloLens NuGet package attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>  <span data-ttu-id="86c01-110">可用 HoloLens 2 NuGet 包后，请观看此页，进行更新。</span><span class="sxs-lookup"><span data-stu-id="86c01-110">Watch this page for updates once the HoloLens 2 NuGet package is available.</span></span>

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="86c01-111">将 holographic 远程处理添加到你的桌面或 UWP 应用</span><span class="sxs-lookup"><span data-stu-id="86c01-111">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="86c01-112">此页介绍了如何将 Holographic 远程处理添加到桌面或 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="86c01-112">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="86c01-113">全息版的远程处理，应用可以面向 HoloLens 全息版或 UWP 设备，如 Xbox One，允许更多系统资源的访问并使其可以将集成远程桌面 PC 上托管的内容与[沉浸式视图](app-views.md)到现有桌面 PC 软件。</span><span class="sxs-lookup"><span data-stu-id="86c01-113">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="86c01-114">远程处理宿主应用程序从 HoloLens 接收输入的数据流、 呈现内容中的虚拟的沉浸式视图，并流式传输返回到 HoloLens 的内容帧。</span><span class="sxs-lookup"><span data-stu-id="86c01-114">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="86c01-115">使用标准的 Wi-fi 进行连接。</span><span class="sxs-lookup"><span data-stu-id="86c01-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="86c01-116">若要使用远程处理，将使用 NuGet 包将 holographic 远程处理添加到你的桌面或 UWP 应用，并编写代码以处理连接，并呈现在沉浸式视图。</span><span class="sxs-lookup"><span data-stu-id="86c01-116">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="86c01-117">帮助程序库包含在简化处理设备连接的任务的代码示例。</span><span class="sxs-lookup"><span data-stu-id="86c01-117">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="86c01-118">典型的远程处理连接会为 50 毫秒的延迟较低。</span><span class="sxs-lookup"><span data-stu-id="86c01-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="86c01-119">播放机应用程序可以报告实时的延迟。</span><span class="sxs-lookup"><span data-stu-id="86c01-119">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="86c01-120">这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="86c01-120">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="86c01-121">这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。</span><span class="sxs-lookup"><span data-stu-id="86c01-121">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="86c01-122">获取 NuGet 包的远程处理</span><span class="sxs-lookup"><span data-stu-id="86c01-122">Get the remoting NuGet packages</span></span>

<span data-ttu-id="86c01-123">请按照下列步骤以 NuGet 包 holographic 远程处理，并添加从您的项目的引用：</span><span class="sxs-lookup"><span data-stu-id="86c01-123">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="86c01-124">请转到 Visual Studio 中的项目。</span><span class="sxs-lookup"><span data-stu-id="86c01-124">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="86c01-125">右键单击项目节点并选择**管理 NuGet 包...**</span><span class="sxs-lookup"><span data-stu-id="86c01-125">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="86c01-126">在显示的面板，单击**浏览**，然后搜索"Holographic 远程处理"。</span><span class="sxs-lookup"><span data-stu-id="86c01-126">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="86c01-127">选择**Microsoft.Holographic.Remoting**然后单击**安装**。</span><span class="sxs-lookup"><span data-stu-id="86c01-127">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="86c01-128">如果**预览版**对话框出现后，单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="86c01-128">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="86c01-129">下一个对话框中显示的是许可协议。</span><span class="sxs-lookup"><span data-stu-id="86c01-129">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="86c01-130">单击**我接受**接受许可协议。</span><span class="sxs-lookup"><span data-stu-id="86c01-130">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="86c01-131">创建 HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="86c01-131">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="86c01-132">首先，我们需要 HolographicStreamerHelpers 的实例。</span><span class="sxs-lookup"><span data-stu-id="86c01-132">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="86c01-133">添加到将处理远程处理的类。</span><span class="sxs-lookup"><span data-stu-id="86c01-133">Add this to the class that will be handling remoting.</span></span>

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="86c01-134">此外需要跟踪连接状态。</span><span class="sxs-lookup"><span data-stu-id="86c01-134">You'll also need to track connection state.</span></span> <span data-ttu-id="86c01-135">如果你想要呈现预览，你需要具有要将其复制到的纹理。</span><span class="sxs-lookup"><span data-stu-id="86c01-135">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="86c01-136">您还需要几个连接状态锁定，存储 HoloLens，IP 地址的某种方式等，依此类推。</span><span class="sxs-lookup"><span data-stu-id="86c01-136">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```
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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="86c01-137">初始化 HolographicStreamerHelpers 并连接到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="86c01-137">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="86c01-138">若要连接到 HoloLens 设备，创建的 HolographicStreamerHelpers 实例并连接到的目标 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="86c01-138">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="86c01-139">你将需要设置视频帧大小以匹配 HoloLens 显示宽度和高度，因为 Holographic 远程处理库需要的编码器和解码器的解决方法若要完全匹配。</span><span class="sxs-lookup"><span data-stu-id="86c01-139">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```
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

<span data-ttu-id="86c01-140">设备连接是异步的。</span><span class="sxs-lookup"><span data-stu-id="86c01-140">The device connection is asynchronous.</span></span> <span data-ttu-id="86c01-141">你的应用需要提供事件处理程序连接，断开连接，和帧发送事件。</span><span class="sxs-lookup"><span data-stu-id="86c01-141">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="86c01-142">OnConnected 事件可以更新 UI，开始呈现，依次类推。</span><span class="sxs-lookup"><span data-stu-id="86c01-142">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="86c01-143">在我们的桌面代码示例，我们使用"连接"消息更新窗口标题。</span><span class="sxs-lookup"><span data-stu-id="86c01-143">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="86c01-144">重新连接、 UI 更新等，可以处理 OnDisconnected 事件。</span><span class="sxs-lookup"><span data-stu-id="86c01-144">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="86c01-145">在此示例中，我们重新连接如果暂时性故障。</span><span class="sxs-lookup"><span data-stu-id="86c01-145">In this example, we reconnect if there is a transient failure.</span></span>

```
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

<span data-ttu-id="86c01-146">准备好发送帧远程处理组件时，您的应用程序提供能够 SendFrameEvent 中使它的一个副本。</span><span class="sxs-lookup"><span data-stu-id="86c01-146">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="86c01-147">在这里，我们将在帧到交换链复制，以便我们可以在预览窗口中显示它。</span><span class="sxs-lookup"><span data-stu-id="86c01-147">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```
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

### <a name="render-holographic-content"></a><span data-ttu-id="86c01-148">呈现全息版的内容</span><span class="sxs-lookup"><span data-stu-id="86c01-148">Render holographic content</span></span>

<span data-ttu-id="86c01-149">将内容呈现使用远程处理，可以设置你的桌面或 UWP 应用中虚拟 IFrameworkView 并处理从远程处理 holographic 帧。</span><span class="sxs-lookup"><span data-stu-id="86c01-149">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="86c01-150">所有 Windows Holographic Api 都的使用此视图中，但相同的方式设置略有不同。</span><span class="sxs-lookup"><span data-stu-id="86c01-150">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="86c01-151">而不是创建它们自己，全息版的空间和语音组件来自 HolographicRemotingHelpers 类：</span><span class="sxs-lookup"><span data-stu-id="86c01-151">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="86c01-152">而不是使用在运行方法的更新循环，则提供从你的桌面或 UWP 应用的主循环的刻度线更新。</span><span class="sxs-lookup"><span data-stu-id="86c01-152">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="86c01-153">这允许你的桌面或 UWP 应用，以控制消息处理。</span><span class="sxs-lookup"><span data-stu-id="86c01-153">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="86c01-154">全息版的应用程序视图 Tick() 方法完成更新、 绘图、 存在循环一次的迭代。</span><span class="sxs-lookup"><span data-stu-id="86c01-154">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```
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

<span data-ttu-id="86c01-155">全息版的应用程序查看更新、 呈现器，并存在循环与完全相同，只不过在桌面 PC 上有权访问更长的系统资源是在 HoloLens 的运行时。</span><span class="sxs-lookup"><span data-stu-id="86c01-155">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="86c01-156">可以呈现多个更多的三角形，具有多个绘图的阶段，执行多个物理引擎，并使用 x64 进程加载所需内容，超过 2 GB 的 RAM。</span><span class="sxs-lookup"><span data-stu-id="86c01-156">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="86c01-157">断开连接，然后结束远程会话</span><span class="sxs-lookup"><span data-stu-id="86c01-157">Disconnect and end the remote session</span></span>

<span data-ttu-id="86c01-158">若要断开连接-例如，当用户单击 UI 按钮以断开连接的对 HolographicStreamerHelpers，调用 Disconnect()，然后释放对象。</span><span class="sxs-lookup"><span data-stu-id="86c01-158">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```
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

## <a name="get-the-remoting-player"></a><span data-ttu-id="86c01-159">获取远程处理播放器</span><span class="sxs-lookup"><span data-stu-id="86c01-159">Get the remoting player</span></span>

<span data-ttu-id="86c01-160">Windows Holographic 远程处理的播放机作为远程处理主机应用程序连接到的终结点在 Windows 应用商店中提供。</span><span class="sxs-lookup"><span data-stu-id="86c01-160">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="86c01-161">若要获取 Windows Holographic 远程处理的播放机，请从您 HoloLens，搜索以进行远程处理，请访问 Windows 应用商店并下载应用。</span><span class="sxs-lookup"><span data-stu-id="86c01-161">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="86c01-162">远程处理的播放机包括用于显示统计信息屏幕上，这可能很有用，调试远程处理主机应用程序时的功能。</span><span class="sxs-lookup"><span data-stu-id="86c01-162">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="86c01-163">说明和资源</span><span class="sxs-lookup"><span data-stu-id="86c01-163">Notes and resources</span></span>

<span data-ttu-id="86c01-164">全息版的应用视图将需要一种方法向应用提供的 Direct3D 设备，必须用来初始化全息版的空间。</span><span class="sxs-lookup"><span data-stu-id="86c01-164">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="86c01-165">您的应用程序应使用此 Direct3D 设备复制和显示预览帧。</span><span class="sxs-lookup"><span data-stu-id="86c01-165">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="86c01-166">**代码示例：** 完整的 Holographic 远程处理的代码示例均可用，其中包括与远程处理和远程处理主机项目类型提供的桌面 Win32、 UWP DirectX 和 XAML 与 UWP 兼容的全息版的应用程序视图。</span><span class="sxs-lookup"><span data-stu-id="86c01-166">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="86c01-167">若要获取它，请转到此处：</span><span class="sxs-lookup"><span data-stu-id="86c01-167">To get it, go here:</span></span>
* [<span data-ttu-id="86c01-168">远程处理的 Windows 全息版的代码示例</span><span class="sxs-lookup"><span data-stu-id="86c01-168">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="86c01-169">**调试注意：** 全息版的远程处理库可以引发最可能的异常。</span><span class="sxs-lookup"><span data-stu-id="86c01-169">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="86c01-170">这些异常可能会看到在调试会话，具体取决于当时处于活动状态的 Visual Studio 异常设置。</span><span class="sxs-lookup"><span data-stu-id="86c01-170">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="86c01-171">这些异常由 Holographic 远程处理库在内部捕获，可以忽略。</span><span class="sxs-lookup"><span data-stu-id="86c01-171">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
