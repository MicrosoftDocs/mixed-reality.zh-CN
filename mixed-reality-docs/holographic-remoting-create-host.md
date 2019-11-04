---
title: 编写全息远程处理主机应用
description: 通过创建在远程计算机上呈现的全息远程处理主机应用远程内容，可将其流式传输到 HoloLens 2。 本文介绍如何实现此目的。
author: bethau
ms.author: bethau
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: e296e5847849bb87f76a7187c3f8ea36a1d681e1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434311"
---
# <a name="writing-a-holographic-remoting-host-app"></a><span data-ttu-id="3d15c-105">编写全息远程处理主机应用</span><span class="sxs-lookup"><span data-stu-id="3d15c-105">Writing a Holographic Remoting host app</span></span>

>[!IMPORTANT]
><span data-ttu-id="3d15c-106">本文档介绍了如何为 HoloLens 2 创建主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="3d15c-106">This document describes the creation of a host application for HoloLens 2.</span></span> <span data-ttu-id="3d15c-107">适用于 HoloLens 的主机应用程序 **（第一代）** 必须使用 NuGet**包版本1.x。**</span><span class="sxs-lookup"><span data-stu-id="3d15c-107">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="3d15c-108">这意味着，为 HoloLens 2 编写的主机应用程序与 HoloLens 1 不兼容，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="3d15c-108">This implies that host applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="3d15c-109">可在[此处](add-holographic-remoting.md)找到 HoloLens 1 的文档。</span><span class="sxs-lookup"><span data-stu-id="3d15c-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="3d15c-110">通过创建全息远程处理主机应用，可将在远程计算机上呈现的远程内容流式传输到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="3d15c-110">By creating a Holographic Remoting host app remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="3d15c-111">本文介绍如何实现此目的。</span><span class="sxs-lookup"><span data-stu-id="3d15c-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="3d15c-112">此页面上的所有代码和工作项目都可以在 "[全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" 中找到。</span><span class="sxs-lookup"><span data-stu-id="3d15c-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="3d15c-113">全息远程处理允许应用以在台式计算机上或 UWP 设备（如 Xbox）上托管的全息内容为 HoloLens 2 设定目标，从而能够访问更多系统资源并使远程[沉浸式视图](app-views.md)能够集成到现有台式计算机软件。</span><span class="sxs-lookup"><span data-stu-id="3d15c-113">Holographic remoting allows an app to target HoloLens 2 with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="3d15c-114">远程处理主机应用从 HoloLens 2 接收输入数据流，在虚拟沉浸式视图中呈现内容，并将内容帧流式传输回 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="3d15c-114">A remoting host app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="3d15c-115">使用标准 Wi-fi 建立连接。</span><span class="sxs-lookup"><span data-stu-id="3d15c-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="3d15c-116">全息远程处理通过 NuGet 数据包添加到桌面或 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="3d15c-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="3d15c-117">需要其他代码来处理连接并在沉浸式视图中呈现。</span><span class="sxs-lookup"><span data-stu-id="3d15c-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="3d15c-118">典型的远程处理连接的延迟最低为50毫秒。</span><span class="sxs-lookup"><span data-stu-id="3d15c-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="3d15c-119">播放机应用可以实时报告滞后时间。</span><span class="sxs-lookup"><span data-stu-id="3d15c-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3d15c-120">必备条件</span><span class="sxs-lookup"><span data-stu-id="3d15c-120">Prerequisites</span></span>

<span data-ttu-id="3d15c-121">很好的起点是基于 DirectX 的基于 DirectX 的桌面或 UWP 应用，以 Windows Mixed Reality API 为目标。</span><span class="sxs-lookup"><span data-stu-id="3d15c-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="3d15c-122">有关详细信息，请参阅[DirectX 开发概述](directx-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3d15c-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="3d15c-123">全息项目模板是一个很好的起点。 [ C++ ](creating-a-holographic-directx-project.md)</span><span class="sxs-lookup"><span data-stu-id="3d15c-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="3d15c-124">使用全息远程处理的任何应用都应该编写为使用[多线程单元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="3d15c-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="3d15c-125">支持使用[单线程单元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)，但会导致在播放过程中出现欠最佳的性能，并且可能会断断续续。</span><span class="sxs-lookup"><span data-stu-id="3d15c-125">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="3d15c-126">使用C++/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started)时，多线程单元是默认值。</span><span class="sxs-lookup"><span data-stu-id="3d15c-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="3d15c-127">获取全息远程处理 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="3d15c-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="3d15c-128">将 NuGet 包添加到 Visual Studio 中的项目时需要执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="3d15c-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="3d15c-129">在 Visual Studio 中打开项目。</span><span class="sxs-lookup"><span data-stu-id="3d15c-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="3d15c-130">右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "</span><span class="sxs-lookup"><span data-stu-id="3d15c-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="3d15c-131">在出现的面板中，单击 "**浏览**"，然后搜索 "全息远程处理"。</span><span class="sxs-lookup"><span data-stu-id="3d15c-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="3d15c-132">选择 ""，然后选择 " **Microsoft**"，并单击 "**安装** **"。**</span><span class="sxs-lookup"><span data-stu-id="3d15c-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="3d15c-133">如果**预览**对话框出现，请单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="3d15c-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="3d15c-134">显示的下一个对话框是许可协议。</span><span class="sxs-lookup"><span data-stu-id="3d15c-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="3d15c-135">单击 "**我接受**" 接受许可协议。</span><span class="sxs-lookup"><span data-stu-id="3d15c-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="3d15c-136">NuGet 包的版本1.x 仍适用于想要面向 HoloLens **1 的开发**人员。</span><span class="sxs-lookup"><span data-stu-id="3d15c-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="3d15c-137">有关详细信息，请参阅[添加全息远程处理（HoloLens （第一代））](add-holographic-remoting.md)。</span><span class="sxs-lookup"><span data-stu-id="3d15c-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="3d15c-138">创建远程上下文</span><span class="sxs-lookup"><span data-stu-id="3d15c-138">Create the remote context</span></span>

<span data-ttu-id="3d15c-139">第一步，应用程序应创建远程上下文。</span><span class="sxs-lookup"><span data-stu-id="3d15c-139">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="3d15c-140">全息远程处理的工作原理是通过使用远程处理特定运行时替换作为 Windows 一部分的 Windows Mixed Reality 运行时。</span><span class="sxs-lookup"><span data-stu-id="3d15c-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="3d15c-141">这是在创建远程上下文的过程中完成的。</span><span class="sxs-lookup"><span data-stu-id="3d15c-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="3d15c-142">因此，在创建远程上下文之前对任何 Windows Mixed Reality API 进行的任何调用都可能导致意外的行为。</span><span class="sxs-lookup"><span data-stu-id="3d15c-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="3d15c-143">推荐的方法是尽早创建远程上下文，然后再与任何混合现实 API 交互。</span><span class="sxs-lookup"><span data-stu-id="3d15c-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="3d15c-144">永远不要混合在使用对象创建或检索到 CreateRemoteContext 之前，通过任何 Windows Mixed Reality API 创建或检索的对象。</span><span class="sxs-lookup"><span data-stu-id="3d15c-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="3d15c-145">接下来，需要创建全息空间。</span><span class="sxs-lookup"><span data-stu-id="3d15c-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="3d15c-146">不需要指定 CoreWindow。</span><span class="sxs-lookup"><span data-stu-id="3d15c-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="3d15c-147">没有 CoreWindow 的桌面应用程序可以只传递 ```nullptr```。</span><span class="sxs-lookup"><span data-stu-id="3d15c-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="3d15c-148">连接到设备</span><span class="sxs-lookup"><span data-stu-id="3d15c-148">Connect to the device</span></span>

<span data-ttu-id="3d15c-149">当主机应用已准备好呈现内容后，可以建立与设备的连接。</span><span class="sxs-lookup"><span data-stu-id="3d15c-149">Once the host app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="3d15c-150">可以通过以下两种方式之一来完成连接。</span><span class="sxs-lookup"><span data-stu-id="3d15c-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="3d15c-151">主机应用连接到设备上运行的播放机。</span><span class="sxs-lookup"><span data-stu-id="3d15c-151">The host app connects to the player running on the device.</span></span>
2) <span data-ttu-id="3d15c-152">设备上运行的播放机连接到主机应用。</span><span class="sxs-lookup"><span data-stu-id="3d15c-152">The player running on the device connects to the host app.</span></span>

<span data-ttu-id="3d15c-153">若要建立从主机应用到 HoloLens 2 的连接，请在指定主机名和端口的远程上下文上调用 ```Connect``` 方法。</span><span class="sxs-lookup"><span data-stu-id="3d15c-153">To establish a connection from the host app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="3d15c-154">全息远程处理播放器使用的端口为**8265**。</span><span class="sxs-lookup"><span data-stu-id="3d15c-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="3d15c-155">与任何C++/WinRT API 一样 ```Connect``` 可能会引发需要处理的 WinRT：： hresult_error。</span><span class="sxs-lookup"><span data-stu-id="3d15c-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="3d15c-156">若要避免使用[ C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/)语言投影，可以包含位于全息远程处理 NuGet 包内的文件 ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h```。</span><span class="sxs-lookup"><span data-stu-id="3d15c-156">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="3d15c-157">它包含基础 COM 接口的声明。</span><span class="sxs-lookup"><span data-stu-id="3d15c-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="3d15c-158">不过，建议C++使用/WinRT。</span><span class="sxs-lookup"><span data-stu-id="3d15c-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="3d15c-159">可以通过调用 ```Listen``` 方法来侦听主机应用上的传入连接。</span><span class="sxs-lookup"><span data-stu-id="3d15c-159">Listening for incoming connections on the host app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="3d15c-160">在此调用过程中，可以同时指定握手端口和传输端口。</span><span class="sxs-lookup"><span data-stu-id="3d15c-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="3d15c-161">握手端口用于初始握手。</span><span class="sxs-lookup"><span data-stu-id="3d15c-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="3d15c-162">然后通过传输端口发送数据。</span><span class="sxs-lookup"><span data-stu-id="3d15c-162">The data is then send over the transport port.</span></span> <span data-ttu-id="3d15c-163">默认情况下，使用**8265**和**8266** 。</span><span class="sxs-lookup"><span data-stu-id="3d15c-163">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="3d15c-164">NuGet 包中的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包含由全息远程处理公开的 API 的详细文档。</span><span class="sxs-lookup"><span data-stu-id="3d15c-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="3d15c-165">处理特定于远程处理的事件</span><span class="sxs-lookup"><span data-stu-id="3d15c-165">Handling Remoting specific events</span></span>

<span data-ttu-id="3d15c-166">远程上下文公开三个事件，这些事件对于监视连接状态很重要。</span><span class="sxs-lookup"><span data-stu-id="3d15c-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="3d15c-167">OnConnected：成功建立到设备的连接后触发。</span><span class="sxs-lookup"><span data-stu-id="3d15c-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="3d15c-168">OnDisconnected：如果已建立的连接已关闭或无法建立连接，则触发。</span><span class="sxs-lookup"><span data-stu-id="3d15c-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="3d15c-169">OnListening：侦听传入连接时启动。</span><span class="sxs-lookup"><span data-stu-id="3d15c-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="3d15c-170">此外，还可以使用远程上下文上的 ```ConnectionState``` 属性查询连接状态。</span><span class="sxs-lookup"><span data-stu-id="3d15c-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="3d15c-171">处理语音事件</span><span class="sxs-lookup"><span data-stu-id="3d15c-171">Handling speech events</span></span>

<span data-ttu-id="3d15c-172">使用远程语音界面，可以向 HoloLens 2 注册语音触发器，并使其远程处理到主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="3d15c-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the host application.</span></span>

<span data-ttu-id="3d15c-173">此附加成员是跟踪远程语音状态所必需的。</span><span class="sxs-lookup"><span data-stu-id="3d15c-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="3d15c-174">首先需要检索远程语音接口。</span><span class="sxs-lookup"><span data-stu-id="3d15c-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="3d15c-175">使用异步帮助器方法，你可以初始化远程语音。</span><span class="sxs-lookup"><span data-stu-id="3d15c-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="3d15c-176">这应异步完成，因为初始化可能需要相当长的时间。</span><span class="sxs-lookup"><span data-stu-id="3d15c-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="3d15c-177">[并发和异步操作与C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency)介绍了如何通过C++/WinRT. 创作异步函数</span><span class="sxs-lookup"><span data-stu-id="3d15c-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleHostMain> sampleHostMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleHostMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleHostMain = sampleHostMainWeak.lock())
            {
                sampleHostMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="3d15c-178">可以通过两种方法来指定要识别的短语。</span><span class="sxs-lookup"><span data-stu-id="3d15c-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="3d15c-179">语音语法 xml 文件中的规范。</span><span class="sxs-lookup"><span data-stu-id="3d15c-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="3d15c-180">有关详细信息，请参阅[如何创建基本 XML 语法](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14))。</span><span class="sxs-lookup"><span data-stu-id="3d15c-180">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="3d15c-181">通过将字典向量内传递到 ```ApplyParameters```来指定。</span><span class="sxs-lookup"><span data-stu-id="3d15c-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="3d15c-182">然后，可以在 OnRecognizedSpeech 回调中处理语音事件：</span><span class="sxs-lookup"><span data-stu-id="3d15c-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

```cpp
void SampleHostMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="3d15c-183">在本地预览流式处理内容</span><span class="sxs-lookup"><span data-stu-id="3d15c-183">Preview streamed content locally</span></span>

<span data-ttu-id="3d15c-184">若要在发送到设备的主机应用中显示相同的内容，可以使用远程上下文的 ```OnSendFrame``` 事件。</span><span class="sxs-lookup"><span data-stu-id="3d15c-184">To display the same content in the host app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="3d15c-185">每次全息远程处理库将当前帧发送到远程设备时，都会触发 ```OnSendFrame``` 事件。</span><span class="sxs-lookup"><span data-stu-id="3d15c-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="3d15c-186">这是获取内容并将其 array.blit 到桌面或 UWP 窗口的理想时机。</span><span class="sxs-lookup"><span data-stu-id="3d15c-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="optional-custom-data-channels"></a><span data-ttu-id="3d15c-187">可选：自定义数据通道</span><span class="sxs-lookup"><span data-stu-id="3d15c-187">Optional: Custom data channels</span></span>

<span data-ttu-id="3d15c-188">自定义数据信道可用于通过已建立的远程处理连接发送用户数据。</span><span class="sxs-lookup"><span data-stu-id="3d15c-188">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="3d15c-189">有关详细信息，请参阅[自定义数据通道](holographic-remoting-custom-data-channels.md)。</span><span class="sxs-lookup"><span data-stu-id="3d15c-189">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d15c-190">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d15c-190">See Also</span></span>
* [<span data-ttu-id="3d15c-191">编写自定义全息远程处理播放器应用程序</span><span class="sxs-lookup"><span data-stu-id="3d15c-191">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="3d15c-192">自定义全息远程处理数据通道</span><span class="sxs-lookup"><span data-stu-id="3d15c-192">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="3d15c-193">建立与全息远程处理的安全连接</span><span class="sxs-lookup"><span data-stu-id="3d15c-193">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="3d15c-194">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="3d15c-194">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="3d15c-195">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="3d15c-195">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="3d15c-196">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="3d15c-196">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
