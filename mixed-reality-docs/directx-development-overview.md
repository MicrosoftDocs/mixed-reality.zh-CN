---
title: 本机开发概述
description: 直接使用 Windows Mixed Reality Api 构建基于 DirectX 的混合现实引擎。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全息呈现，本机，本机应用，WinRT，WinRT 应用，平台 Api，自定义引擎，中间件
ms.openlocfilehash: 06227b41dde69e6610b151f3b27a3800e76431bd
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181897"
---
# <a name="native-development-overview"></a><span data-ttu-id="f1335-104">本机开发概述</span><span class="sxs-lookup"><span data-stu-id="f1335-104">Native development overview</span></span>

<span data-ttu-id="f1335-105">Windows Mixed Reality 应用程序使用以下 Api 为 HoloLens 和其他沉浸式耳机构建[混合现实](mixed-reality.md)体验：</span><span class="sxs-lookup"><span data-stu-id="f1335-105">Windows Mixed Reality applications use the following APIs to build [mixed-reality](mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

 - [<span data-ttu-id="f1335-106">全息渲染</span><span class="sxs-lookup"><span data-stu-id="f1335-106">Holographic rendering</span></span>](rendering.md)
 - [<span data-ttu-id="f1335-107">凝视</span><span class="sxs-lookup"><span data-stu-id="f1335-107">Gaze</span></span>](gaze-and-commit.md)
 - [<span data-ttu-id="f1335-108">姿态</span><span class="sxs-lookup"><span data-stu-id="f1335-108">Gesture</span></span>](gaze-and-commit.md#composite-gestures)
 - [<span data-ttu-id="f1335-109">运动控制器</span><span class="sxs-lookup"><span data-stu-id="f1335-109">Motion controller</span></span>](motion-controllers.md)
 - [<span data-ttu-id="f1335-110">语音</span><span class="sxs-lookup"><span data-stu-id="f1335-110">Voice</span></span>](voice-input.md)
 - [<span data-ttu-id="f1335-111">空间映射</span><span class="sxs-lookup"><span data-stu-id="f1335-111">Spatial mapping</span></span>](spatial-mapping.md)

<span data-ttu-id="f1335-112">可以使用三维引擎（如[Unity](unity-development-overview.md)）创建混合现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1335-112">You can create mixed reality applications by using a 3D engine, such as [Unity](unity-development-overview.md).</span></span> <span data-ttu-id="f1335-113">或者，你可以通过使用 DirectX 11 或 DirectX 12 直接向 Windows Mixed Reality Api 进行编码。</span><span class="sxs-lookup"><span data-stu-id="f1335-113">Or you can directly code to the Windows Mixed Reality APIs by using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="f1335-114">如果直接利用该平台，则会实质上构建自己的中间件或框架。</span><span class="sxs-lookup"><span data-stu-id="f1335-114">If you leverage the platform directly, you essentially build your own middleware or framework.</span></span> <span data-ttu-id="f1335-115">Windows Api 支持在C++和C#中编写的应用程序。</span><span class="sxs-lookup"><span data-stu-id="f1335-115">The Windows APIs support applications that are written in both C++ and C#.</span></span> <span data-ttu-id="f1335-116">如果使用C#，你的应用程序可以利用[SharpDX](https://sharpdx.org/)开源软件库。</span><span class="sxs-lookup"><span data-stu-id="f1335-116">If you use C#, your application can leverage the [SharpDX](https://sharpdx.org/) open source software library.</span></span>

<span data-ttu-id="f1335-117">Windows Mixed Reality 支持[两种类型的应用](app-views.md)：</span><span class="sxs-lookup"><span data-stu-id="f1335-117">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="f1335-118">**混合现实应用程序**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)将[沉浸式视图](app-views.md)呈现给填充耳机显示的用户</span><span class="sxs-lookup"><span data-stu-id="f1335-118">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) to render an [immersive view](app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="f1335-119">使用 DirectX、XAML 或其他框架在 Windows Mixed Reality 主页上的清单上呈现[2d 视图](app-views.md#2d-views)的**2d 应用**（UWP）</span><span class="sxs-lookup"><span data-stu-id="f1335-119">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="f1335-120">[2d 视图和沉浸式视图](app-views.md)的 DirectX 开发之间的差异主要涉及全息呈现和空间输入。</span><span class="sxs-lookup"><span data-stu-id="f1335-120">The differences between DirectX development for [2D views and immersive views](app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="f1335-121">UWP 应用程序的[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 应用程序的 HWND 是必需的，并且保持基本相同。</span><span class="sxs-lookup"><span data-stu-id="f1335-121">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="f1335-122">适用于应用程序的 WinRT Api 也是如此。</span><span class="sxs-lookup"><span data-stu-id="f1335-122">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="f1335-123">但您必须使用这些 Api 的不同子集才能利用全息功能。</span><span class="sxs-lookup"><span data-stu-id="f1335-123">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="f1335-124">例如，交换链由适用于全息应用程序的系统管理。</span><span class="sxs-lookup"><span data-stu-id="f1335-124">For example, the swap chain is managed by the system for holographic applications.</span></span> <span data-ttu-id="f1335-125">并使用 HolographicSpace API，而不是使用 DXGI 来[呈现帧](rendering-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="f1335-125">And you use the HolographicSpace API rather than DXGI to [present frames](rendering-in-directx.md).</span></span>

<span data-ttu-id="f1335-126">开始开发沉浸式应用程序：</span><span class="sxs-lookup"><span data-stu-id="f1335-126">To begin developing immersive applications:</span></span>
* <span data-ttu-id="f1335-127">对于**UWP 应用**，请[使用 Visual Studio 中的模板创建新的 UWP 项目](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="f1335-127">For **UWP apps**, [use the templates in Visual Studio to create a new UWP project](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="f1335-128">根据语言C++ 、视觉对象或视觉对象C#，在**Windows 通用** > **全息**版下查找 UWP 模板。</span><span class="sxs-lookup"><span data-stu-id="f1335-128">Based on your language, Visual C++ or Visual C#, find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="f1335-129">对于**Win32 应用程序**，请[从*BasicHologram* Win32 示例开始](creating-a-holographic-directx-project.md#creating-a-win32-project)。</span><span class="sxs-lookup"><span data-stu-id="f1335-129">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="f1335-130">此步骤是获取将全息呈现支持添加到现有应用程序或引擎所需的代码的好方法。</span><span class="sxs-lookup"><span data-stu-id="f1335-130">This step is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="f1335-131">在模板中，代码和概念的显示方式与实时交互式软件的任何开发人员都非常熟悉。</span><span class="sxs-lookup"><span data-stu-id="f1335-131">The code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>

## <a name="get-started"></a><span data-ttu-id="f1335-132">“开始”</span><span class="sxs-lookup"><span data-stu-id="f1335-132">Get started</span></span>

<span data-ttu-id="f1335-133">以下主题介绍了向基于 DirectX 的中间件添加 Windows Mixed Reality 支持时的基本要求。</span><span class="sxs-lookup"><span data-stu-id="f1335-133">The following topics describe the base requirements when you add Windows Mixed Reality support to DirectX-based middleware.</span></span>

* <span data-ttu-id="f1335-134">[创建全息版 DirectX 项目](creating-a-holographic-directx-project.md)：全息应用程序模板与文档一起显示与你使用的不同之处。</span><span class="sxs-lookup"><span data-stu-id="f1335-134">[Create a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows the differences compared to what you're used to.</span></span> <span data-ttu-id="f1335-135">还介绍了在打印头上运行时设计的设备的特殊要求。</span><span class="sxs-lookup"><span data-stu-id="f1335-135">It also describes the special requirements for a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="f1335-136">[获取 HolographicSpace](getting-a-holographicspace.md)：首先需要创建一个 HolographicSpace，它为应用程序提供了一个 HolographicFrame 对象的序列，这些对象表示你将呈现的每个头位置。</span><span class="sxs-lookup"><span data-stu-id="f1335-136">[Get a HolographicSpace](getting-a-holographicspace.md): You first need to create a HolographicSpace that gives your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="f1335-137">[在 DirectX 中呈现](rendering-in-directx.md)：由于全息交换链有两个呈现目标，因此你必须对应用呈现的方式进行一些更改。</span><span class="sxs-lookup"><span data-stu-id="f1335-137">[Render in DirectX](rendering-in-directx.md): Because a holographic swap chain has two render targets, you must make some changes to the way your app renders.</span></span>
* <span data-ttu-id="f1335-138">[在 DirectX 中协调系统](coordinate-systems-in-directx.md)： Windows Mixed Reality 在用户浏览时了解并更新对世界的了解。</span><span class="sxs-lookup"><span data-stu-id="f1335-138">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="f1335-139">这会提供应用程序用于确定用户周围环境的空间坐标系统，其中包括空间锚和用户定义的空间阶段。</span><span class="sxs-lookup"><span data-stu-id="f1335-139">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="add-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="f1335-140">添加混合现实功能和输入</span><span class="sxs-lookup"><span data-stu-id="f1335-140">Add mixed reality capabilities and inputs</span></span>

<span data-ttu-id="f1335-141">若要为沉浸式应用程序的用户提供可能的最佳体验，应支持以下关键构建基块：</span><span class="sxs-lookup"><span data-stu-id="f1335-141">To provide the best possible experience for users of your immersive app, you should support the following key building blocks:</span></span>

* [<span data-ttu-id="f1335-142">DirectX 中的头部和眼部凝视</span><span class="sxs-lookup"><span data-stu-id="f1335-142">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="f1335-143">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="f1335-143">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="f1335-144">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="f1335-144">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="f1335-145">空间音效</span><span class="sxs-lookup"><span data-stu-id="f1335-145">Spatial sound</span></span>](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [<span data-ttu-id="f1335-146">DirectX 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="f1335-146">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)

<span data-ttu-id="f1335-147">这些是许多沉浸式应用程序所使用的其他主要功能，这些功能也会公开给 DirectX 应用程序：</span><span class="sxs-lookup"><span data-stu-id="f1335-147">These are other key features that many immersive applications use that are also exposed to DirectX applications:</span></span>

* [<span data-ttu-id="f1335-148">DirectX 中的共享空间定位点</span><span class="sxs-lookup"><span data-stu-id="f1335-148">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="f1335-149">DirectX 中的键盘、鼠标和控制器输入</span><span class="sxs-lookup"><span data-stu-id="f1335-149">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="f1335-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1335-150">See also</span></span>
* [<span data-ttu-id="f1335-151">应用模型</span><span class="sxs-lookup"><span data-stu-id="f1335-151">App model</span></span>](app-model.md)
* [<span data-ttu-id="f1335-152">应用视图</span><span class="sxs-lookup"><span data-stu-id="f1335-152">App views</span></span>](app-views.md)
