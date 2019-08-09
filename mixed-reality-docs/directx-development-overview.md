---
title: DirectX 开发概述
description: 直接使用 Windows Mixed Reality Api 构建基于 DirectX 的混合现实引擎。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, 全息呈现, 本机, 本机应用, WinRT, WinRT 应用, 平台 Api, 自定义引擎, 中间件
ms.openlocfilehash: 58b311038633dc325cc2c5425fd09b9a0192b161
ms.sourcegitcommit: 4ac761fed7a9570977f6d031ba4f870585d6630a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68861706"
---
# <a name="directx-development-overview"></a><span data-ttu-id="17235-104">DirectX 开发概述</span><span class="sxs-lookup"><span data-stu-id="17235-104">DirectX development overview</span></span>


<span data-ttu-id="17235-105">Windows Mixed Reality 应用程序使用[全息渲染](rendering.md)、[注视](gaze.md)、[手势](gestures.md)、[运动控制器](motion-controllers.md)、[语音](voice-input.md)和[空间映射](spatial-mapping.md)api, 为 HoloLens 构建[混合现实](mixed-reality.md)体验和沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="17235-105">Windows Mixed Reality applications use the [holographic rendering](rendering.md), [gaze](gaze.md), [gesture](gestures.md), [motion controller](motion-controllers.md), [voice](voice-input.md), and [spatial mapping](spatial-mapping.md) APIs to build [mixed reality](mixed-reality.md) experiences for HoloLens and immersive headsets.</span></span> <span data-ttu-id="17235-106">可以使用三维引擎 (如[Unity](unity-development-overview.md)) 创建混合现实应用程序, 也可以使用 directx 11 或 directx 12 直接向 Windows Mixed reality api 进行编码。</span><span class="sxs-lookup"><span data-stu-id="17235-106">You can create mixed reality applications using a 3D engine, such as [Unity](unity-development-overview.md), or you can directly code to the Windows Mixed Reality APIs using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="17235-107">如果直接利用该平台, 则会实质上构建自己的中间件或框架。</span><span class="sxs-lookup"><span data-stu-id="17235-107">If you are leveraging the platform directly, you'll essentially be building your own middleware or framework.</span></span> <span data-ttu-id="17235-108">Windows Api 支持在C++和C#中编写的应用程序。</span><span class="sxs-lookup"><span data-stu-id="17235-108">The Windows APIs support applications written in both C++ and C#.</span></span> <span data-ttu-id="17235-109">如果你选择使用C#, 你的应用程序可以利用[SharpDX](http://sharpdx.org/)开源软件库。</span><span class="sxs-lookup"><span data-stu-id="17235-109">If you choose to use C#, your application can leverage the [SharpDX](http://sharpdx.org/) open source software library.</span></span>


<span data-ttu-id="17235-110">Windows Mixed Reality 支持[两种类型的应用](app-views.md):</span><span class="sxs-lookup"><span data-stu-id="17235-110">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="17235-111">**混合现实应用程序**(UWP 或 Win32), 使用[HOLOGRAPHICSPACE API](getting-a-holographicspace.md)将[沉浸式视图](app-views.md)呈现给用户以填充耳机显示。</span><span class="sxs-lookup"><span data-stu-id="17235-111">**Mixed reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) to render an [immersive view](app-views.md) to the user that fills the headset display.</span></span>
* <span data-ttu-id="17235-112">**2d 应用**(UWP), 使用 DirectX、XAML 或其他框架在 Windows Mixed Reality home 中的清单上呈现[2d 视图](app-views.md#2d-views)。</span><span class="sxs-lookup"><span data-stu-id="17235-112">**2D apps** (UWP) that use DirectX, XAML, or other frameworks to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home.</span></span>


<span data-ttu-id="17235-113">[2d 视图和沉浸式视图](app-views.md)的 DirectX 开发之间的差异主要与全息呈现和空间输入有关。</span><span class="sxs-lookup"><span data-stu-id="17235-113">The differences between DirectX development for [2D views and immersive views](app-views.md) are primarily related to holographic rendering and spatial input.</span></span> <span data-ttu-id="17235-114">UWP 应用程序的[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 应用程序的 HWND 是必需的, 并且与应用程序可使用的 WinRT api 相同。</span><span class="sxs-lookup"><span data-stu-id="17235-114">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required, and remain largely the same, as do the WinRT APIs available to your application.</span></span> <span data-ttu-id="17235-115">但是, 必须使用这些 Api 的不同子集才能利用全息版功能。</span><span class="sxs-lookup"><span data-stu-id="17235-115">However, you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="17235-116">例如, 交换链由系统为全息 appslications 进行管理。</span><span class="sxs-lookup"><span data-stu-id="17235-116">For example, the swap chain is managed by the system for holographic appslications.</span></span> <span data-ttu-id="17235-117">使用 HolographicSpace API, 而不是使用 DXGI 来[呈现帧](rendering-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="17235-117">You work with the HolographicSpace API rather than DXGI to [present frames](rendering-in-directx.md).</span></span>

<span data-ttu-id="17235-118">开始开发沉浸式应用程序:</span><span class="sxs-lookup"><span data-stu-id="17235-118">To begin developing immersive applications:</span></span>
* <span data-ttu-id="17235-119">对于**UWP 应用**, 请[使用 Visual Studio 中的模板创建新的 UWP 项目](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="17235-119">For **UWP apps**, [create a new UWP project using the templates in Visual Studio](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="17235-120">根据语言、**视觉对象C++** 或**视觉对象C#** , 可以在**Windows 通用** > **全息**版下查找 UWP 模板。</span><span class="sxs-lookup"><span data-stu-id="17235-120">Based on your language, **Visual C++** or **Visual C#**, you can find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="17235-121">对于**Win32 应用程序**, 请[从*BasicHologram* Win32 示例开始](creating-a-holographic-directx-project.md#creating-a-win32-project)。</span><span class="sxs-lookup"><span data-stu-id="17235-121">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="17235-122">这是一种很好的方法, 可用于获取将全息呈现支持添加到现有应用程序或引擎所需的代码。</span><span class="sxs-lookup"><span data-stu-id="17235-122">This is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="17235-123">在模板中, 代码和概念的显示方式与实时交互式软件的任何开发人员都非常熟悉。</span><span class="sxs-lookup"><span data-stu-id="17235-123">Code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>


## <a name="getting-started"></a><span data-ttu-id="17235-124">即刻体验</span><span class="sxs-lookup"><span data-stu-id="17235-124">Getting started</span></span>

<span data-ttu-id="17235-125">以下主题讨论向基于 DirectX 的中间件添加 Windows Mixed Reality 支持的基本要求:</span><span class="sxs-lookup"><span data-stu-id="17235-125">The following topics discuss the base requirements of adding Windows Mixed Reality support to DirectX-based middleware:</span></span>

* <span data-ttu-id="17235-126">[创建全息版 DirectX 项目](creating-a-holographic-directx-project.md):全息应用程序模板与文档一起显示了你所使用的内容之间的差异, 以及在你的计算机上设计为正常工作的设备引入的特殊要求。</span><span class="sxs-lookup"><span data-stu-id="17235-126">[Creating a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows you the differences between what you're used to as well as the special requirements introduced by a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="17235-127">[获取 HolographicSpace](getting-a-holographicspace.md):首先需要创建一个 HolographicSpace, 它将为应用程序提供一系列 HolographicFrame 对象, 这些对象表示你将呈现的每个头位置。</span><span class="sxs-lookup"><span data-stu-id="17235-127">[Getting a HolographicSpace](getting-a-holographicspace.md): You'll first need to create a HolographicSpace That will provide your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="17235-128">[在 DirectX 中呈现](rendering-in-directx.md):由于全息交换链有两个呈现目标, 因此你需要对应用程序的呈现方式进行一些更改。</span><span class="sxs-lookup"><span data-stu-id="17235-128">[Rendering in DirectX](rendering-in-directx.md): Since a holographic swap chain has two render targets, you'll need to make some changes to the way your application renders.</span></span>
* <span data-ttu-id="17235-129">[在 DirectX 中协调系统](coordinate-systems-in-directx.md):Windows Mixed Reality 在用户浏览时了解并更新对世界的了解。</span><span class="sxs-lookup"><span data-stu-id="17235-129">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="17235-130">这会提供应用程序用于确定用户周围环境的空间坐标系统, 其中包括空间锚和用户定义的空间阶段。</span><span class="sxs-lookup"><span data-stu-id="17235-130">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="17235-131">添加混合现实功能和输入</span><span class="sxs-lookup"><span data-stu-id="17235-131">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="17235-132">若要为沉浸式 appslication 的用户提供最佳体验, 需要支持以下关键构建基块:</span><span class="sxs-lookup"><span data-stu-id="17235-132">To enable the best possible experience for users of your immersive appslication, you'll want to support the following key building blocks:</span></span>

* [<span data-ttu-id="17235-133">DirectX 中的头部和眼部凝视</span><span class="sxs-lookup"><span data-stu-id="17235-133">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="17235-134">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="17235-134">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="17235-135">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="17235-135">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="17235-136">DirectX 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="17235-136">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="17235-137">DirectX 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="17235-137">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)


<span data-ttu-id="17235-138">许多沉浸式应用程序都要使用其他重要功能, 这些功能也会向 DirectX 应用程序公开:</span><span class="sxs-lookup"><span data-stu-id="17235-138">There are other key features that many immersive applications will want to use that are also exposed to DirectX applicaitons:</span></span>

* [<span data-ttu-id="17235-139">DirectX 中的共享空间定位点</span><span class="sxs-lookup"><span data-stu-id="17235-139">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="17235-140">DirectX 中的键盘、鼠标和控制器输入</span><span class="sxs-lookup"><span data-stu-id="17235-140">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="17235-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="17235-141">See also</span></span>
* [<span data-ttu-id="17235-142">应用模型</span><span class="sxs-lookup"><span data-stu-id="17235-142">App model</span></span>](app-model.md)
* [<span data-ttu-id="17235-143">应用视图</span><span class="sxs-lookup"><span data-stu-id="17235-143">App views</span></span>](app-views.md)
