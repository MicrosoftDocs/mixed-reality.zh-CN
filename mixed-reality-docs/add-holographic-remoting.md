---
title: 添加 holographic 远程处理
description: 介绍如何使用 Holographic 远程处理以通过网络将全息呈现到 HoloLens。
author: MikeRiches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality，全息、 全息版的远程处理、 远程呈现、 呈现、 HoloLens，远程全息网络
ms.openlocfilehash: 8d645f634ff0fc820893f5554fd602aa3a2f38e3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829618"
---
# <a name="add-holographic-remoting"></a>添加 holographic 远程处理

## <a name="hololens-2"></a>HoloLens 2

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。

使用 Holographic 远程处理的 HoloLens 开发人员将需要更新其应用程序，使它们与 HoloLens 2 兼容。  这将要求尚不可公开可用的 Holographic 远程处理 NuGet 包的新版本。  如果使用 HoloLens NuGet 包的应用程序尝试连接到 HoloLens 2 上全息版的远程处理播放机，则连接将失败。  可用 HoloLens 2 NuGet 包后，请观看此页，进行更新。

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>将 holographic 远程处理添加到你的桌面或 UWP 应用

此页介绍了如何将 Holographic 远程处理添加到桌面或 UWP 应用。

全息版的远程处理，应用可以面向 HoloLens 全息版或 UWP 设备，如 Xbox One，允许更多系统资源的访问并使其可以将集成远程桌面 PC 上托管的内容与[沉浸式视图](app-views.md)到现有桌面 PC 软件。 远程处理宿主应用程序从 HoloLens 接收输入的数据流、 呈现内容中的虚拟的沉浸式视图，并流式传输返回到 HoloLens 的内容帧。 使用标准的 Wi-fi 进行连接。 若要使用远程处理，将使用 NuGet 包将 holographic 远程处理添加到你的桌面或 UWP 应用，并编写代码以处理连接，并呈现在沉浸式视图。 帮助程序库包含在简化处理设备连接的任务的代码示例。

典型的远程处理连接会为 50 毫秒的延迟较低。 播放机应用程序可以报告实时的延迟。

>[!NOTE]
>这篇文章中的代码片段当前演示了如何使用C++/CX 而不是 C + + 17 符合C++中使用 /WinRT [ C++全息版的项目模板](creating-a-holographic-directx-project.md)。  这些概念是等效的C++/WinRT 项目，但您将需要将代码转换。

### <a name="get-the-remoting-nuget-packages"></a>获取 NuGet 包的远程处理

请按照下列步骤以 NuGet 包 holographic 远程处理，并添加从您的项目的引用：
1. 请转到 Visual Studio 中的项目。
2. 右键单击项目节点并选择**管理 NuGet 包...**
3. 在显示的面板，单击**浏览**，然后搜索"Holographic 远程处理"。
4. 选择**Microsoft.Holographic.Remoting**然后单击**安装**。
5. 如果**预览版**对话框出现后，单击**确定**。
6. 下一个对话框中显示的是许可协议。 单击**我接受**接受许可协议。

### <a name="create-the-holographicstreamerhelpers"></a>创建 HolographicStreamerHelpers

首先，我们需要 HolographicStreamerHelpers 的实例。 添加到将处理远程处理的类。

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

此外需要跟踪连接状态。 如果你想要呈现预览，你需要具有要将其复制到的纹理。 您还需要几个连接状态锁定，存储 HoloLens，IP 地址的某种方式等，依此类推。

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>初始化 HolographicStreamerHelpers 并连接到 HoloLens

若要连接到 HoloLens 设备，创建的 HolographicStreamerHelpers 实例并连接到的目标 IP 地址。 你将需要设置视频帧大小以匹配 HoloLens 显示宽度和高度，因为 Holographic 远程处理库需要的编码器和解码器的解决方法若要完全匹配。

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

设备连接是异步的。 你的应用需要提供事件处理程序连接，断开连接，和帧发送事件。

OnConnected 事件可以更新 UI，开始呈现，依次类推。 在我们的桌面代码示例，我们使用"连接"消息更新窗口标题。

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

重新连接、 UI 更新等，可以处理 OnDisconnected 事件。 在此示例中，我们重新连接如果暂时性故障。

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

准备好发送帧远程处理组件时，您的应用程序提供能够 SendFrameEvent 中使它的一个副本。 在这里，我们将在帧到交换链复制，以便我们可以在预览窗口中显示它。

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

### <a name="render-holographic-content"></a>呈现全息版的内容

将内容呈现使用远程处理，可以设置你的桌面或 UWP 应用中虚拟 IFrameworkView 并处理从远程处理 holographic 帧。 所有 Windows Holographic Api 都的使用此视图中，但相同的方式设置略有不同。

而不是创建它们自己，全息版的空间和语音组件来自 HolographicRemotingHelpers 类：

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

而不是使用在运行方法的更新循环，则提供从你的桌面或 UWP 应用的主循环的刻度线更新。 这允许你的桌面或 UWP 应用，以控制消息处理。

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

全息版的应用程序视图 Tick() 方法完成更新、 绘图、 存在循环一次的迭代。

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

全息版的应用程序查看更新、 呈现器，并存在循环与完全相同，只不过在桌面 PC 上有权访问更长的系统资源是在 HoloLens 的运行时。 可以呈现多个更多的三角形，具有多个绘图的阶段，执行多个物理引擎，并使用 x64 进程加载所需内容，超过 2 GB 的 RAM。

### <a name="disconnect-and-end-the-remote-session"></a>断开连接，然后结束远程会话

若要断开连接-例如，当用户单击 UI 按钮以断开连接的对 HolographicStreamerHelpers，调用 Disconnect()，然后释放对象。

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

## <a name="get-the-remoting-player"></a>获取远程处理播放器

Windows Holographic 远程处理的播放机作为远程处理主机应用程序连接到的终结点在 Windows 应用商店中提供。 若要获取 Windows Holographic 远程处理的播放机，请从您 HoloLens，搜索以进行远程处理，请访问 Windows 应用商店并下载应用。 远程处理的播放机包括用于显示统计信息屏幕上，这可能很有用，调试远程处理主机应用程序时的功能。

## <a name="notes-and-resources"></a>说明和资源

全息版的应用视图将需要一种方法向应用提供的 Direct3D 设备，必须用来初始化全息版的空间。 您的应用程序应使用此 Direct3D 设备复制和显示预览帧。

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**代码示例：** 完整的 Holographic 远程处理的代码示例均可用，其中包括与远程处理和远程处理主机项目类型提供的桌面 Win32、 UWP DirectX 和 XAML 与 UWP 兼容的全息版的应用程序视图。 若要获取它，请转到此处：
* [远程处理的 Windows 全息版的代码示例](https://github.com/Microsoft/HoloLensCompanionKit/)

**调试注意：** 全息版的远程处理库可以引发最可能的异常。 这些异常可能会看到在调试会话，具体取决于当时处于活动状态的 Visual Studio 异常设置。 这些异常由 Holographic 远程处理库在内部捕获，可以忽略。
