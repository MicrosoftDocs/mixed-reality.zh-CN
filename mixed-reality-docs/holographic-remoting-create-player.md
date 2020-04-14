---
title: 编写自定义全息远程处理播放器
description: 通过创建自定义的全息远程处理播放器应用，你可以创建一个自定义应用程序，该应用程序能够将远程计算机上呈现的内容显示到 HoloLens 2 上。 本文介绍如何实现此目的。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: b276558e43fc545be9e5c0be6feded229904ee97
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278215"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a>编写自定义全息远程处理播放器应用程序

>[!IMPORTANT]
>本文档介绍了如何为 HoloLens 2 创建自定义播放器应用程序。 为 HoloLens 2 编写的自定义播放器与为 HoloLens 1 编写的远程应用程序不兼容。 这意味着两个应用程序必须使用 NuGet 包**版本2.x。**

通过创建自定义的全息远程处理播放器应用，你可以创建一个自定义应用程序，该应用程序能够在你的 HoloLens 2 上的远程计算机上显示[沉浸式视图](app-views.md)。 本文介绍如何实现此目的。 此页面上的所有代码和工作项目都可以在 "[全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" 中找到。

全息远程处理播放机允许应用显示桌面 PC 或 UWP 设备（如 Xbox 设备）上[呈现](rendering.md)的全息内容，允许访问更多系统资源。 全息远程处理播放机应用将输入数据流式传输到全息远程处理远程应用程序，并将沉浸式视图作为视频和音频流接收回来。 使用标准 Wi-fi 建立连接。 若要创建播放器应用，需要使用 NuGet 包将全息远程处理添加到 UWP 应用，并编写代码来处理连接并显示沉浸式视图。 

## <a name="prerequisites"></a>先决条件

很好的起点是基于 DirectX 的基于 DirectX 的 UWP 应用，已经以 Windows Mixed Reality API 为目标。 有关详细信息，请参阅[DirectX 开发概述](directx-development-overview.md)。 如果你没有现有应用，并且想要从头开始，则可以使用[ C++全息版项目模板](creating-a-holographic-directx-project.md)。

>[!IMPORTANT]
>使用全息远程处理的任何应用都应该编写为使用[多线程单元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。 支持使用[单线程单元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)，但在播放过程中可能会导致性能不佳，并且可能会断断续续。 使用C++/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started)多线程单元是默认值。

## <a name="get-the-holographic-remoting-nuget-package"></a>获取全息远程处理 NuGet 包

将 NuGet 包添加到 Visual Studio 中的项目时需要执行以下步骤。
1. 在 Visual Studio 中打开项目。
2. 右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "
3. 在出现的面板中，单击 "**浏览**"，然后搜索 "全息远程处理"。
4. 选择 ""，然后选择 " **Microsoft**"，并单击 "**安装** **"。**
5. 如果**预览**对话框出现，请单击 **"确定"** 。
6. 显示的下一个对话框是许可协议。 单击 "**我接受**" 接受许可协议。

>[!IMPORTANT]
><a name="idl"></a>NuGet 包中的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包含由全息远程处理公开的 API 的详细文档。

## <a name="modify-the-packageappxmanifest-of-the-application"></a>修改应用程序的 appxmanifest.xml

若要使应用程序了解 NuGet 包添加的 AppRemoting，需要在项目中执行以下步骤：：

1. 在解决方案资源管理器右键单击**appxmanifest.xml**文件并选择 "**打开方式 ...** "
2. 选择 " **XML （文本）编辑器**"，然后单击 "确定"
3. 将以下行添加到文件中并保存
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>创建播放机上下文

作为第一步，应用程序应创建播放机上下文。

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>全息远程处理的工作原理是通过使用远程处理特定运行时替换作为 Windows 一部分的 Windows Mixed Reality 运行时。 这是在创建播放机上下文的过程中完成的。 因此，在创建播放机上下文之前对任何 Windows Mixed Reality API 进行的任何调用都可能导致意外的行为。 推荐的方法是尽早创建播放机上下文，然后再与任何混合现实 API 交互。 永远不要混合使用任何 Windows Mixed Reality ```PlayerContext::Create``` API 创建或检索的对象。

接下来，可以通过调用[CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)创建 HolographicSpace。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>连接到远程应用

播放机应用准备好呈现内容后，可以建立到远程应用的连接。

可以通过以下方式之一建立连接：
1) 在 HoloLens 2 上运行的播放机应用会连接到远程应用。
2) 远程应用连接到在 HoloLens 2 上运行的播放机应用。

若要从播放机应用连接到远程应用，请调用播放机上下文中指定主机名和端口的 ```Connect``` 方法。 默认端口为**8265**。

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>与任何C++/WinRT API 一样 ```Connect``` 可能会引发需要处理的 WinRT：： hresult_error。

可以通过调用 ```Listen``` 方法来侦听播放机应用上的传入连接。 在此调用过程中，可以同时指定握手端口和传输端口。 握手端口用于初始握手。 然后通过传输端口发送数据。 默认情况下，使用端口号**8265**和**8266** 。

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>处理与连接相关的事件

```PlayerContext``` 公开了三个事件来监视连接的状态
1) OnConnected：已成功建立到远程应用程序的连接时触发。
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected：如果已建立的连接终止或无法建立连接，则触发。
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>```Microsoft.Holographic.AppRemoting.idl```[文件](#idl)中记录了可能 ```ConnectionFailureReason``` 值。

3) OnListening：侦听传入连接时启动。
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

此外，还可以使用播放机上下文上的 ```ConnectionState``` 属性查询连接状态。
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>显示远程呈现的帧

若要显示远程呈现的内容，请在呈现[HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)时调用 ```PlayerContext::BlitRemoteFrame```。 

```BlitRemoteFrame``` 要求当前 HolographicFrame 的后台缓冲区绑定为呈现器目标。 可以通过[Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)属性从[HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)接收后台缓冲区。

调用时，```BlitRemoteFrame``` 将从远程应用程序接收的最新帧复制到 HolographicFrame 的后台缓冲区中。 此外，如果远程应用程序在呈现远程帧期间指定了焦点，则会设置焦点集。

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` 可能会覆盖当前帧的焦点。 
>- 若要指定回退焦点点，请在 ```PlayerContext::BlitRemoteFrame```之前调用[HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 。 
>- 若要覆盖远程焦点，请在 ```PlayerContext::BlitRemoteFrame```后调用[HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 。

成功时，```BlitRemoteFrame``` 返回 ```BlitResult::Success_Color```。 否则，它将返回失败原因：
- ```BlitResult::Failed_NoRemoteFrameAvailable```：失败，因为没有可用的远程帧。
- ```BlitResult::Failed_NoCamera```：由于没有照相机，导致失败。
- ```BlitResult::Failed_RemoteFrameTooOld```：由于远程帧太旧，导致失败（请参见 PlayerContext：： BlitRemoteFrameTimeout 属性）。

>[!IMPORTANT]
> 从版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)开始，自定义播放器可以通过全息远程处理使用深度 reprojection。

```BlitResult``` 还可以在以下条件下返回 ```BlitResult::Success_Color_Depth```：

- 远程应用已通过 HolographicCameraRenderingParameters 提交深度缓冲区[。 CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。
- 自定义播放机应用在调用 ```BlitRemoteFrame```之前已经绑定了有效的深度缓冲区。

如果满足这些条件 ```BlitRemoteFrame``` 会将远程深度 array.blit 当前绑定的本地深度缓冲区。 然后，您可以呈现其他本地内容，这将与远程呈现的内容具有深度交集。 此外，还可以通过自定义播放机中的[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)来提交本地深度缓冲区，以获得远程和本地呈现内容的深度 reprojection。 有关详细信息，请参阅[深度 Reprojection](hologram-stability.md#reprojection) 。

### <a name="projection-transform-mode"></a>投影转换模式

通过全息远程处理使用深度 reprojection 的一个问题是，可以使用不同于自定义播放器应用直接呈现的本地内容的投影转换来呈现远程内容。 常见的用例是在播放机端和远程端为近和远平面指定不同的值（通过[HolographicCamera：： SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance)和[HolographicCamera：： SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)）。 在这种情况下，如果播放机端上的投影转换应反映远程的接近/远平面距离或局部，则不清楚。

从版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)开始，可以通过 ```PlayerContext::ProjectionTransformConfig```来控制投影转换模式。 支持的值是：

- ```Local``` - [HolographicCameraPose：:P rojectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform)返回投影转换，该转换反映自定义播放器应用在 HolographicCamera 上设置的近/远平面距离。
- ```Remote``` 投影转换反映远程应用指定的近/远平面距离。
- ```Merged```-与远程应用和自定义播放器应用的接近/远平面距离将合并。 默认情况下，这是通过使用接近平面距离和最大平面距离的最小值来完成的。 如果远程或本地侧反转，说远 < 接近，则会翻转远程近/远平面距离。

## <a name="optional-set-blitremoteframetimeout"></a>可选：设置 BlitRemoteFrameTimeout<a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> 从版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持 ```PlayerContext::BlitRemoteFrameTimeout```。 

如果未接收到新的远程帧，则 ```PlayerContext::BlitRemoteFrameTimeout``` 属性指定重复使用远程帧的时间长度。 

常见的用例是，如果在一段时间内没有收到新帧，BlitRemoteFrame 超时将显示空白屏幕。 启用后，还可使用 ```BlitRemoteFrame``` 方法的返回类型切换到本地呈现的回退内容。 

若要启用超时，请将属性值设置为等于或大于100ms 的持续时间。 若要禁用超时，请将属性设置为零。 如果在设置的持续时间内启用了超时并且未收到任何远程帧，BlitRemoteFrame 将失败并返回 ```Failed_RemoteFrameTooOld``` 直到收到新的远程帧。

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>可选：获取有关最后一个远程帧的统计信息

若要诊断性能或网络问题，可以通过 ```PlayerContext::LastFrameStatistics``` 属性检索有关最后一个远程帧的统计信息。 在调用 HolographicFrame 期间更新统计信息[：:P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)。

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

有关更多详细信息，请参阅 ```Microsoft.Holographic.AppRemoting.idl```[文件](#idl)中的 ```PlayerFrameStatistics``` 文档。

## <a name="optional-custom-data-channels"></a>可选：自定义数据通道

自定义数据信道可用于通过已建立的远程处理连接发送用户数据。 有关详细信息，请参阅[自定义数据通道](holographic-remoting-custom-data-channels.md)。

## <a name="see-also"></a>另请参阅
* [编写全息远程处理远程应用](holographic-remoting-create-host.md)
* [自定义全息远程处理数据通道](holographic-remoting-custom-data-channels.md)
* [建立与全息远程处理的安全连接](holographic-remoting-secure-connection.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)
