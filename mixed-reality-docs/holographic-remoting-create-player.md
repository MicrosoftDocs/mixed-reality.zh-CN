---
title: 编写自定义全息远程处理播放器
description: 通过创建自定义的全息远程处理播放器应用，你可以创建一个自定义应用程序，该应用程序能够将远程计算机上呈现的内容显示到 HoloLens 2 上。 本文介绍如何实现此目的。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: eaa6549eb34d3a37c21b3decb348bf43594a110f
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092415"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="f041a-105">编写自定义全息远程处理播放器应用程序</span><span class="sxs-lookup"><span data-stu-id="f041a-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="f041a-106">本文档介绍了如何为 HoloLens 2 创建自定义播放器应用程序。</span><span class="sxs-lookup"><span data-stu-id="f041a-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="f041a-107">为 HoloLens 2 编写的自定义播放器与为 HoloLens 1 编写的远程应用程序不兼容。</span><span class="sxs-lookup"><span data-stu-id="f041a-107">Custom players written for HoloLens 2 are not compatible with remote applications written for HoloLens 1.</span></span> <span data-ttu-id="f041a-108">这意味着两个应用程序必须使用 NuGet 包**版本2.x。**</span><span class="sxs-lookup"><span data-stu-id="f041a-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="f041a-109">通过创建自定义的全息远程处理播放器应用，你可以创建一个自定义应用程序，该应用程序能够在你的 HoloLens 2 上的远程计算机上显示[沉浸式视图](app-views.md)。</span><span class="sxs-lookup"><span data-stu-id="f041a-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="f041a-110">本文介绍如何实现此目的。</span><span class="sxs-lookup"><span data-stu-id="f041a-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="f041a-111">此页面上的所有代码和工作项目都可以在 "[全息远程处理示例 github 存储库](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)" 中找到。</span><span class="sxs-lookup"><span data-stu-id="f041a-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="f041a-112">全息远程处理播放机允许应用显示桌面 PC 或 UWP 设备（如 Xbox 设备）上[呈现](rendering.md)的全息内容，允许访问更多系统资源。</span><span class="sxs-lookup"><span data-stu-id="f041a-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="f041a-113">全息远程处理播放机应用将输入数据流式传输到全息远程处理远程应用程序，并将沉浸式视图作为视频和音频流接收回来。</span><span class="sxs-lookup"><span data-stu-id="f041a-113">A Holographic Remoting player app streams input data to a Holographic Remoting remote application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="f041a-114">使用标准 Wi-fi 建立连接。</span><span class="sxs-lookup"><span data-stu-id="f041a-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="f041a-115">若要创建播放器应用，需要使用 NuGet 包将全息远程处理添加到 UWP 应用，并编写代码来处理连接并显示沉浸式视图。</span><span class="sxs-lookup"><span data-stu-id="f041a-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="f041a-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="f041a-116">Prerequisites</span></span>

<span data-ttu-id="f041a-117">很好的起点是基于 DirectX 的基于 DirectX 的 UWP 应用，已经以 Windows Mixed Reality API 为目标。</span><span class="sxs-lookup"><span data-stu-id="f041a-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="f041a-118">有关详细信息，请参阅[DirectX 开发概述](directx-development-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f041a-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="f041a-119">如果你没有现有应用，并且想要从头开始，则可以使用[ C++全息版项目模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="f041a-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f041a-120">使用全息远程处理的任何应用都应该编写为使用[多线程单元](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)。</span><span class="sxs-lookup"><span data-stu-id="f041a-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="f041a-121">支持使用[单线程单元](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)，但在播放过程中可能会导致性能不佳，并且可能会断断续续。</span><span class="sxs-lookup"><span data-stu-id="f041a-121">The use of a [single-threaded appartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="f041a-122">使用C++/WinRT [WinRT：： init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started)多线程单元是默认值。</span><span class="sxs-lookup"><span data-stu-id="f041a-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="f041a-123">获取全息远程处理 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="f041a-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="f041a-124">将 NuGet 包添加到 Visual Studio 中的项目时需要执行以下步骤。</span><span class="sxs-lookup"><span data-stu-id="f041a-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="f041a-125">在 Visual Studio 中打开项目。</span><span class="sxs-lookup"><span data-stu-id="f041a-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="f041a-126">右键单击项目节点，然后选择 "**管理 NuGet 包 ...** "</span><span class="sxs-lookup"><span data-stu-id="f041a-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="f041a-127">在出现的面板中，单击 "**浏览**"，然后搜索 "全息远程处理"。</span><span class="sxs-lookup"><span data-stu-id="f041a-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="f041a-128">选择 ""，然后选择 " **Microsoft**"，并单击 "**安装** **"。**</span><span class="sxs-lookup"><span data-stu-id="f041a-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="f041a-129">如果**预览**对话框出现，请单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="f041a-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="f041a-130">显示的下一个对话框是许可协议。</span><span class="sxs-lookup"><span data-stu-id="f041a-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="f041a-131">单击 "**我接受**" 接受许可协议。</span><span class="sxs-lookup"><span data-stu-id="f041a-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="f041a-132">NuGet 包中的 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 包含由全息远程处理公开的 API 的详细文档。</span><span class="sxs-lookup"><span data-stu-id="f041a-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="f041a-133">修改应用程序的 appxmanifest.xml</span><span class="sxs-lookup"><span data-stu-id="f041a-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="f041a-134">若要使应用程序了解 NuGet 包添加的 AppRemoting，需要在项目中执行以下步骤：：</span><span class="sxs-lookup"><span data-stu-id="f041a-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="f041a-135">在解决方案资源管理器右键单击**appxmanifest.xml**文件并选择 "**打开方式 ...** "</span><span class="sxs-lookup"><span data-stu-id="f041a-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="f041a-136">选择 " **XML （文本）编辑器**"，然后单击 "确定"</span><span class="sxs-lookup"><span data-stu-id="f041a-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="f041a-137">将以下行添加到文件中并保存</span><span class="sxs-lookup"><span data-stu-id="f041a-137">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="f041a-138">创建播放机上下文</span><span class="sxs-lookup"><span data-stu-id="f041a-138">Create the player context</span></span>

<span data-ttu-id="f041a-139">作为第一步，应用程序应创建播放机上下文。</span><span class="sxs-lookup"><span data-stu-id="f041a-139">As a first step the application should create a player context.</span></span>

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
><span data-ttu-id="f041a-140">全息远程处理的工作原理是通过使用远程处理特定运行时替换作为 Windows 一部分的 Windows Mixed Reality 运行时。</span><span class="sxs-lookup"><span data-stu-id="f041a-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="f041a-141">这是在创建播放机上下文的过程中完成的。</span><span class="sxs-lookup"><span data-stu-id="f041a-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="f041a-142">因此，在创建播放机上下文之前对任何 Windows Mixed Reality API 进行的任何调用都可能导致意外的行为。</span><span class="sxs-lookup"><span data-stu-id="f041a-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="f041a-143">推荐的方法是尽早创建播放机上下文，然后再与任何混合现实 API 交互。</span><span class="sxs-lookup"><span data-stu-id="f041a-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="f041a-144">永远不要混合使用任何 Windows Mixed Reality ```PlayerContext::Create``` API 创建或检索的对象。</span><span class="sxs-lookup"><span data-stu-id="f041a-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="f041a-145">接下来，可以通过调用[CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)创建 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="f041a-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a><span data-ttu-id="f041a-146">连接到远程应用</span><span class="sxs-lookup"><span data-stu-id="f041a-146">Connect to the remote app</span></span>

<span data-ttu-id="f041a-147">播放机应用准备好呈现内容后，可以建立到远程应用的连接。</span><span class="sxs-lookup"><span data-stu-id="f041a-147">Once the player app is ready for rendering content a connection to the remote app can be established.</span></span>

<span data-ttu-id="f041a-148">可以通过以下方式之一建立连接：</span><span class="sxs-lookup"><span data-stu-id="f041a-148">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="f041a-149">在 HoloLens 2 上运行的播放机应用会连接到远程应用。</span><span class="sxs-lookup"><span data-stu-id="f041a-149">The player app running on HoloLens 2 connects to the remote app.</span></span>
2) <span data-ttu-id="f041a-150">远程应用连接到在 HoloLens 2 上运行的播放机应用。</span><span class="sxs-lookup"><span data-stu-id="f041a-150">The remote app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="f041a-151">若要从播放机应用连接到远程应用，请调用播放机上下文中指定主机名和端口的 ```Connect``` 方法。</span><span class="sxs-lookup"><span data-stu-id="f041a-151">To connect from the player app to the remote app call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="f041a-152">默认端口为**8265**。</span><span class="sxs-lookup"><span data-stu-id="f041a-152">The default port is **8265**.</span></span>

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
><span data-ttu-id="f041a-153">与任何C++/WinRT API 一样 ```Connect``` 可能会引发需要处理的 WinRT：： hresult_error。</span><span class="sxs-lookup"><span data-stu-id="f041a-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="f041a-154">可以通过调用 ```Listen``` 方法来侦听播放机应用上的传入连接。</span><span class="sxs-lookup"><span data-stu-id="f041a-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="f041a-155">在此调用过程中，可以同时指定握手端口和传输端口。</span><span class="sxs-lookup"><span data-stu-id="f041a-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="f041a-156">握手端口用于初始握手。</span><span class="sxs-lookup"><span data-stu-id="f041a-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="f041a-157">然后通过传输端口发送数据。</span><span class="sxs-lookup"><span data-stu-id="f041a-157">The data is then send over the transport port.</span></span> <span data-ttu-id="f041a-158">默认情况下，使用端口号**8265**和**8266** 。</span><span class="sxs-lookup"><span data-stu-id="f041a-158">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="f041a-159">处理与连接相关的事件</span><span class="sxs-lookup"><span data-stu-id="f041a-159">Handling connection related events</span></span>

<span data-ttu-id="f041a-160">```PlayerContext``` 公开了三个事件来监视连接的状态</span><span class="sxs-lookup"><span data-stu-id="f041a-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="f041a-161">OnConnected：已成功建立到远程应用程序的连接时触发。</span><span class="sxs-lookup"><span data-stu-id="f041a-161">OnConnected: Triggered when a connection to the remote app has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="f041a-162">OnDisconnected：如果已建立的连接终止或无法建立连接，则触发。</span><span class="sxs-lookup"><span data-stu-id="f041a-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
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
><span data-ttu-id="f041a-163">```Microsoft.Holographic.AppRemoting.idl```[文件](#idl)中记录了可能 ```ConnectionFailureReason``` 值。</span><span class="sxs-lookup"><span data-stu-id="f041a-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="f041a-164">OnListening：侦听传入连接时启动。</span><span class="sxs-lookup"><span data-stu-id="f041a-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="f041a-165">此外，还可以使用播放机上下文上的 ```ConnectionState``` 属性查询连接状态。</span><span class="sxs-lookup"><span data-stu-id="f041a-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="f041a-166">显示远程呈现的帧</span><span class="sxs-lookup"><span data-stu-id="f041a-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="f041a-167">若要显示远程呈现的内容，请在呈现[HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)时调用 ```PlayerContext::BlitRemoteFrame```。</span><span class="sxs-lookup"><span data-stu-id="f041a-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="f041a-168">```BlitRemoteFrame``` 要求当前 HolographicFrame 的后台缓冲区绑定为呈现器目标。</span><span class="sxs-lookup"><span data-stu-id="f041a-168">```BlitRemoteFrame``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="f041a-169">可以通过[Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)属性从[HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)接收后台缓冲区。</span><span class="sxs-lookup"><span data-stu-id="f041a-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="f041a-170">调用时，```BlitRemoteFrame``` 将从远程应用程序接收的最新帧复制到 HolographicFrame 的后台缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="f041a-170">When called, ```BlitRemoteFrame``` copies the latest received frame from the remote application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="f041a-171">此外，如果远程应用程序在呈现远程帧期间指定了焦点，则会设置焦点集。</span><span class="sxs-lookup"><span data-stu-id="f041a-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="f041a-172">```PlayerContext::BlitRemoteFrame``` 可能会覆盖当前帧的焦点。</span><span class="sxs-lookup"><span data-stu-id="f041a-172">```PlayerContext::BlitRemoteFrame``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="f041a-173">若要指定回退焦点点，请在 ```PlayerContext::BlitRemoteFrame```之前调用[HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 。</span><span class="sxs-lookup"><span data-stu-id="f041a-173">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame```.</span></span> 
>- <span data-ttu-id="f041a-174">若要覆盖远程焦点，请在 ```PlayerContext::BlitRemoteFrame```后调用[HolographicCameraRenderingParameters：： SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 。</span><span class="sxs-lookup"><span data-stu-id="f041a-174">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame```.</span></span>

<span data-ttu-id="f041a-175">成功时，```BlitRemoteFrame``` 返回 ```BlitResult::Success_Color```。</span><span class="sxs-lookup"><span data-stu-id="f041a-175">On success, ```BlitRemoteFrame``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="f041a-176">否则，它将返回失败原因：</span><span class="sxs-lookup"><span data-stu-id="f041a-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="f041a-177">```BlitResult::Failed_NoRemoteFrameAvailable```：失败，因为没有可用的远程帧。</span><span class="sxs-lookup"><span data-stu-id="f041a-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="f041a-178">```BlitResult::Failed_NoCamera```：由于没有照相机，导致失败。</span><span class="sxs-lookup"><span data-stu-id="f041a-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="f041a-179">```BlitResult::Failed_RemoteFrameTooOld```：由于远程帧太旧，导致失败（请参见 PlayerContext：： BlitRemoteFrameTimeout 属性）。</span><span class="sxs-lookup"><span data-stu-id="f041a-179">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f041a-180">从版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)开始，自定义播放器可以通过全息远程处理使用深度 reprojection。</span><span class="sxs-lookup"><span data-stu-id="f041a-180">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) it is possible with a custom player to use depth reprojection via Holographic Remoting.</span></span>

<span data-ttu-id="f041a-181">```BlitResult``` 还可以在以下条件下返回 ```BlitResult::Success_Color_Depth```：</span><span class="sxs-lookup"><span data-stu-id="f041a-181">```BlitResult``` can also return ```BlitResult::Success_Color_Depth``` under the following conditions:</span></span>

- <span data-ttu-id="f041a-182">远程应用已通过 HolographicCameraRenderingParameters 提交深度缓冲区[。 CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。</span><span class="sxs-lookup"><span data-stu-id="f041a-182">The remote app has committed a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>
- <span data-ttu-id="f041a-183">自定义播放机应用在调用 ```BlitRemoteFrame```之前已经绑定了有效的深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="f041a-183">The custom player app has bound a valid depth buffer before calling ```BlitRemoteFrame```.</span></span>

<span data-ttu-id="f041a-184">如果满足这些条件 ```BlitRemoteFrame``` 会将远程深度 array.blit 当前绑定的本地深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="f041a-184">If these conditions are met ```BlitRemoteFrame``` will blit the remote depth into the currently bound local depth buffer.</span></span> <span data-ttu-id="f041a-185">然后，您可以呈现其他本地内容，这将与远程呈现的内容具有深度交集。</span><span class="sxs-lookup"><span data-stu-id="f041a-185">You can then render additional local content which will have depth intersection with the remote rendered content.</span></span> <span data-ttu-id="f041a-186">此外，还可以通过自定义播放机中的[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)来提交本地深度缓冲区，以获得远程和本地呈现内容的深度 reprojection。</span><span class="sxs-lookup"><span data-stu-id="f041a-186">Additionally you can commit the local depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in your custom player to have depth reprojection for remote and local rendered content.</span></span> <span data-ttu-id="f041a-187">有关详细信息，请参阅[深度 Reprojection](hologram-stability.md#reprojection) 。</span><span class="sxs-lookup"><span data-stu-id="f041a-187">See [Depth Reprojection](hologram-stability.md#reprojection) for details.</span></span>

### <a name="projection-transform-mode"></a><span data-ttu-id="f041a-188">投影转换模式</span><span class="sxs-lookup"><span data-stu-id="f041a-188">Projection Transform Mode</span></span>

<span data-ttu-id="f041a-189">通过全息远程处理使用深度 reprojection 的一个问题是，可以使用不同于自定义播放器应用直接呈现的本地内容的投影转换来呈现远程内容。</span><span class="sxs-lookup"><span data-stu-id="f041a-189">One problem which surfaces when using depth reprojection via Holographic Remoting is that the remote content can be rendered with a different projection transform than local content directly rendered by your custom player app.</span></span> <span data-ttu-id="f041a-190">常见的用例是在播放机端和远程端为近和远平面指定不同的值（通过[HolographicCamera：： SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance)和[HolographicCamera：： SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)）。</span><span class="sxs-lookup"><span data-stu-id="f041a-190">A common use-case is to specify different values for near and far plane (via [HolographicCamera::SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) and [HolographicCamera::SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) on the player side and the remote side.</span></span> <span data-ttu-id="f041a-191">在这种情况下，如果播放机端上的投影转换应反映远程的接近/远平面距离或局部，则不清楚。</span><span class="sxs-lookup"><span data-stu-id="f041a-191">In this case it's not clear if the projection transform on the player side should reflect the remote near/far plane distances or the local ones.</span></span>

<span data-ttu-id="f041a-192">从版本[2.1.0](holographic-remoting-version-history.md#v2.1.0)开始，可以通过 ```PlayerContext::ProjectionTransformConfig```来控制投影转换模式。</span><span class="sxs-lookup"><span data-stu-id="f041a-192">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) you can control the projection transform mode via ```PlayerContext::ProjectionTransformConfig```.</span></span> <span data-ttu-id="f041a-193">支持的值是：</span><span class="sxs-lookup"><span data-stu-id="f041a-193">Supported values are:</span></span>

- <span data-ttu-id="f041a-194">```Local``` - [HolographicCameraPose：:P rojectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform)返回投影转换，该转换反映自定义播放器应用在 HolographicCamera 上设置的近/远平面距离。</span><span class="sxs-lookup"><span data-stu-id="f041a-194">```Local``` - [HolographicCameraPose::ProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) returns a projection transform which reflects the near/far plane distances set by your custom player app on the HolographicCamera.</span></span>
- <span data-ttu-id="f041a-195">```Remote``` 投影转换反映远程应用指定的近/远平面距离。</span><span class="sxs-lookup"><span data-stu-id="f041a-195">```Remote``` - Projection transform reflects the near/far plane distances specified by the remote app.</span></span>
- <span data-ttu-id="f041a-196">```Merged```-与远程应用和自定义播放器应用的接近/远平面距离将合并。</span><span class="sxs-lookup"><span data-stu-id="f041a-196">```Merged``` - Near/Far plane distances from your remote app and your custom player app are merged.</span></span> <span data-ttu-id="f041a-197">默认情况下，这是通过使用接近平面距离和最大平面距离的最小值来完成的。</span><span class="sxs-lookup"><span data-stu-id="f041a-197">By default this is done by taking the minimum of the near plane distances and the maximum of the far plane distances.</span></span> <span data-ttu-id="f041a-198">如果远程或本地侧反转，说远 < 接近，则会翻转远程近/远平面距离。</span><span class="sxs-lookup"><span data-stu-id="f041a-198">In case either the remote or local side are inverted, say far < near, the remote near/far plane distances are flipped.</span></span>

## <span data-ttu-id="f041a-199">可选：设置 BlitRemoteFrameTimeout<a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="f041a-199">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="f041a-200">从版本[2.0.9](holographic-remoting-version-history.md#v2.0.9)开始支持 ```PlayerContext::BlitRemoteFrameTimeout```。</span><span class="sxs-lookup"><span data-stu-id="f041a-200">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="f041a-201">如果未接收到新的远程帧，则 ```PlayerContext::BlitRemoteFrameTimeout``` 属性指定重复使用远程帧的时间长度。</span><span class="sxs-lookup"><span data-stu-id="f041a-201">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="f041a-202">常见的用例是，如果在一段时间内没有收到新帧，BlitRemoteFrame 超时将显示空白屏幕。</span><span class="sxs-lookup"><span data-stu-id="f041a-202">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="f041a-203">启用后，还可使用 ```BlitRemoteFrame``` 方法的返回类型切换到本地呈现的回退内容。</span><span class="sxs-lookup"><span data-stu-id="f041a-203">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="f041a-204">若要启用超时，请将属性值设置为等于或大于100ms 的持续时间。</span><span class="sxs-lookup"><span data-stu-id="f041a-204">To enable the timeout, set the property value to a duration equal or greater than 100ms.</span></span> <span data-ttu-id="f041a-205">若要禁用超时，请将属性设置为零。</span><span class="sxs-lookup"><span data-stu-id="f041a-205">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="f041a-206">如果在设置的持续时间内启用了超时并且未收到任何远程帧，BlitRemoteFrame 将失败并返回 ```Failed_RemoteFrameTooOld``` 直到收到新的远程帧。</span><span class="sxs-lookup"><span data-stu-id="f041a-206">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="f041a-207">可选：获取有关最后一个远程帧的统计信息</span><span class="sxs-lookup"><span data-stu-id="f041a-207">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="f041a-208">若要诊断性能或网络问题，可以通过 ```PlayerContext::LastFrameStatistics``` 属性检索有关最后一个远程帧的统计信息。</span><span class="sxs-lookup"><span data-stu-id="f041a-208">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="f041a-209">在调用 HolographicFrame 期间更新统计信息[：:P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)。</span><span class="sxs-lookup"><span data-stu-id="f041a-209">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="f041a-210">有关更多详细信息，请参阅 ```Microsoft.Holographic.AppRemoting.idl```[文件](#idl)中的 ```PlayerFrameStatistics``` 文档。</span><span class="sxs-lookup"><span data-stu-id="f041a-210">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="f041a-211">可选：自定义数据通道</span><span class="sxs-lookup"><span data-stu-id="f041a-211">Optional: Custom data channels</span></span>

<span data-ttu-id="f041a-212">自定义数据信道可用于通过已建立的远程处理连接发送用户数据。</span><span class="sxs-lookup"><span data-stu-id="f041a-212">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="f041a-213">有关详细信息，请参阅[自定义数据通道](holographic-remoting-custom-data-channels.md)。</span><span class="sxs-lookup"><span data-stu-id="f041a-213">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="f041a-214">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f041a-214">See Also</span></span>
* [<span data-ttu-id="f041a-215">编写全息远程处理远程应用</span><span class="sxs-lookup"><span data-stu-id="f041a-215">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="f041a-216">自定义全息远程处理数据通道</span><span class="sxs-lookup"><span data-stu-id="f041a-216">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="f041a-217">建立与全息远程处理的安全连接</span><span class="sxs-lookup"><span data-stu-id="f041a-217">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="f041a-218">全息远程处理故障排除和限制</span><span class="sxs-lookup"><span data-stu-id="f041a-218">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="f041a-219">全息远程处理软件许可条款</span><span class="sxs-lookup"><span data-stu-id="f041a-219">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="f041a-220">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="f041a-220">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
