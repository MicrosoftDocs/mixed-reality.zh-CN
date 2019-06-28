---
title: DirectX 开发概述
description: 生成基于 DirectX 的混合的现实引擎直接使用 Windows 混合现实 Api。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX，全息呈现，本机、 本机应用，WinRT，WinRT 应用平台 Api，自定义引擎，中间件
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414385"
---
# <a name="directx-development-overview"></a><span data-ttu-id="a6155-104">DirectX 开发概述</span><span class="sxs-lookup"><span data-stu-id="a6155-104">DirectX development overview</span></span>


<span data-ttu-id="a6155-105">Windows Mixed Reality 应用程序使用[全息呈现](rendering.md)，[注视](gaze.md)，[手势](gestures.md)，[运动控制器](motion-controllers.md)， [语音](voice-input.md)，并[空间映射](spatial-mapping.md)Api 生成[混合现实](mixed-reality.md)HoloLens 和耳机沉浸式体验。</span><span class="sxs-lookup"><span data-stu-id="a6155-105">Windows Mixed Reality applications use the [holographic rendering](rendering.md), [gaze](gaze.md), [gesture](gestures.md), [motion controller](motion-controllers.md), [voice](voice-input.md), and [spatial mapping](spatial-mapping.md) APIs to build [mixed reality](mixed-reality.md) experiences for HoloLens and immersive headsets.</span></span> <span data-ttu-id="a6155-106">您可以创建混合的现实应用程序使用 3D 引擎，如[Unity](unity-development-overview.md)，或者也可以直接使用 DirectX 11 或 DirectX 12 Windows 混合现实 api。</span><span class="sxs-lookup"><span data-stu-id="a6155-106">You can create mixed reality applications using a 3D engine, such as [Unity](unity-development-overview.md), or you can directly code to the Windows Mixed Reality APIs using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="a6155-107">如果您直接利用该平台，实质上要构建自己的中间件或框架。</span><span class="sxs-lookup"><span data-stu-id="a6155-107">If you are leveraging the platform directly, you'll essentially be building your own middleware or framework.</span></span> <span data-ttu-id="a6155-108">Windows Api 支持在这种编写的应用程序C++和C#。</span><span class="sxs-lookup"><span data-stu-id="a6155-108">The Windows APIs support applications written in both C++ and C#.</span></span> <span data-ttu-id="a6155-109">如果您选择使用C#，你的应用程序可以利用[SharpDX](http://sharpdx.org/)开放源代码软件库。</span><span class="sxs-lookup"><span data-stu-id="a6155-109">If you choose to use C#, your application can leverage the [SharpDX](http://sharpdx.org/) open source software library.</span></span>


<span data-ttu-id="a6155-110">支持 Windows Mixed Reality[两种类型的应用](app-views.md):</span><span class="sxs-lookup"><span data-stu-id="a6155-110">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="a6155-111">**混合现实应用程序**（UWP 或 Win32），使用[HolographicSpace API](getting-a-holographicspace.md)呈现[沉浸式视图](app-views.md)填充耳机显示的用户。</span><span class="sxs-lookup"><span data-stu-id="a6155-111">**Mixed reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) to render an [immersive view](app-views.md) to the user that fills the headset display.</span></span>
* <span data-ttu-id="a6155-112">**2D 应用**(UWP) 的使用 DirectX、 XAML 或其他框架来呈现[2D 视图](app-views.md#2d-views)Windows Mixed Reality 家庭中的平板电脑上。</span><span class="sxs-lookup"><span data-stu-id="a6155-112">**2D apps** (UWP) that use DirectX, XAML, or other frameworks to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home.</span></span>


<span data-ttu-id="a6155-113">DirectX 开发之间的差异[2D 视图和沉浸式视图](app-views.md)是主要与全息呈现和空间的输入。</span><span class="sxs-lookup"><span data-stu-id="a6155-113">The differences between DirectX development for [2D views and immersive views](app-views.md) are primarily related to holographic rendering and spatial input.</span></span> <span data-ttu-id="a6155-114">在 UWP 应用程序[IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx)或 Win32 应用程序的 HWND 是必需的并保持很大程度上是相同的 WinRT Api 可用于应用程序一样。</span><span class="sxs-lookup"><span data-stu-id="a6155-114">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required, and remain largely the same, as do the WinRT APIs available to your application.</span></span> <span data-ttu-id="a6155-115">但是，必须使用这些 Api 的另一个子集以充分利用全息版的功能。</span><span class="sxs-lookup"><span data-stu-id="a6155-115">However, you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="a6155-116">例如，为 holographic appslications 的系统管理交换链。</span><span class="sxs-lookup"><span data-stu-id="a6155-116">For example, the swap chain is managed by the system for holographic appslications.</span></span> <span data-ttu-id="a6155-117">使用 HolographicSpace API 而不是到 DXGI[呈现帧](rendering-in-directx.md)。</span><span class="sxs-lookup"><span data-stu-id="a6155-117">You work with the HolographicSpace API rather than DXGI to [present frames](rendering-in-directx.md).</span></span>

<span data-ttu-id="a6155-118">若要开始开发沉浸式应用程序：</span><span class="sxs-lookup"><span data-stu-id="a6155-118">To begin developing immersive applications:</span></span>
* <span data-ttu-id="a6155-119">有关**UWP 应用**，[创建新的 UWP 项目使用 Visual Studio 中的模板](creating-a-holographic-directx-project.md)。</span><span class="sxs-lookup"><span data-stu-id="a6155-119">For **UWP apps**, [create a new UWP project using the templates in Visual Studio](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="a6155-120">根据你的语言，**可视化C++** 或**Visual C#** ，可以找到下的 UWP 模板**Windows 通用** >  **Holographic**。</span><span class="sxs-lookup"><span data-stu-id="a6155-120">Based on your language, **Visual C++** or **Visual C#**, you can find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="a6155-121">有关**Win32 应用程序**，[从头*BasicHologram* Win32 示例](creating-a-holographic-directx-project.md#creating-a-win32-project)。</span><span class="sxs-lookup"><span data-stu-id="a6155-121">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="a6155-122">这是获取您需要将全息呈现支持添加到现有的应用程序或引擎的代码的好办法。</span><span class="sxs-lookup"><span data-stu-id="a6155-122">This is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="a6155-123">代码和概念的模板中的实时交互式软件开发人员熟悉的方式呈现。</span><span class="sxs-lookup"><span data-stu-id="a6155-123">Code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>


## <a name="getting-started"></a><span data-ttu-id="a6155-124">即刻体验</span><span class="sxs-lookup"><span data-stu-id="a6155-124">Getting started</span></span>

<span data-ttu-id="a6155-125">以下主题讨论 Windows Mixed Reality 支持添加到基于 DirectX 的中间件的基本要求：</span><span class="sxs-lookup"><span data-stu-id="a6155-125">The following topics discuss the base requirements of adding Windows Mixed Reality support to DirectX-based middleware:</span></span>

* <span data-ttu-id="a6155-126">[创建全息版的 DirectX 项目](creating-a-holographic-directx-project.md):结合文档全息版的应用程序模板显示习惯于以及一台设备，其设计目的函数将在您头上时引入的特殊要求之间的差异。</span><span class="sxs-lookup"><span data-stu-id="a6155-126">[Creating a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows you the differences between what you're used to as well as the special requirements introduced by a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="a6155-127">[获取 HolographicSpace](getting-a-holographicspace.md):首先需要创建将提供你的应用程序的表示从其将呈现的每个头位置的 HolographicFrame 对象序列 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="a6155-127">[Getting a HolographicSpace](getting-a-holographicspace.md): You'll first need to create a HolographicSpace That will provide your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="a6155-128">[在 DirectX 呈现](rendering-in-directx.md):由于 holographic 交换链具有两个呈现器目标，你将需要对你的应用程序中的呈现的方式进行一些更改。</span><span class="sxs-lookup"><span data-stu-id="a6155-128">[Rendering in DirectX](rendering-in-directx.md): Since a holographic swap chain has two render targets, you'll need to make some changes to the way your application renders.</span></span>
* <span data-ttu-id="a6155-129">[在 DirectX 的坐标系统](coordinate-systems-in-directx.md):Windows Mixed Reality 学习并更新其了解的全球如周围将指导用户。</span><span class="sxs-lookup"><span data-stu-id="a6155-129">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="a6155-130">这提供了空间坐标系统的应用程序使用来推断用户的环境，包括空间的定位点和用户定义的空间阶段。</span><span class="sxs-lookup"><span data-stu-id="a6155-130">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="a6155-131">添加混合的现实功能和输入</span><span class="sxs-lookup"><span data-stu-id="a6155-131">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="a6155-132">若要启用的沉浸式 appslication 用户可能的最佳体验，你将想要支持以下主要构建基块：</span><span class="sxs-lookup"><span data-stu-id="a6155-132">To enable the best possible experience for users of your immersive appslication, you'll want to support the following key building blocks:</span></span>

* [<span data-ttu-id="a6155-133">DirectX 中的头部和眼部凝视</span><span class="sxs-lookup"><span data-stu-id="a6155-133">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="a6155-134">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="a6155-134">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="a6155-135">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="a6155-135">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="a6155-136">DirectX 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="a6155-136">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="a6155-137">DirectX 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="a6155-137">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)


<span data-ttu-id="a6155-138">有很多沉浸式应用程序将想要使用还向 DirectX 应用程序公开的其他主要功能：</span><span class="sxs-lookup"><span data-stu-id="a6155-138">There are other key features that many immersive applications will want to use that are also exposed to DirectX applicaitons:</span></span>

* [<span data-ttu-id="a6155-139">DirectX 中的共享空间定位点</span><span class="sxs-lookup"><span data-stu-id="a6155-139">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="a6155-140">DirectX 中的可定位相机</span><span class="sxs-lookup"><span data-stu-id="a6155-140">Locatable camera in DirectX</span></span>](locatable-camera-in-directx.md)
* [<span data-ttu-id="a6155-141">DirectX 中的键盘、鼠标和控制器输入</span><span class="sxs-lookup"><span data-stu-id="a6155-141">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="a6155-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="a6155-142">See also</span></span>
* [<span data-ttu-id="a6155-143">应用模型</span><span class="sxs-lookup"><span data-stu-id="a6155-143">App model</span></span>](app-model.md)
* [<span data-ttu-id="a6155-144">应用视图</span><span class="sxs-lookup"><span data-stu-id="a6155-144">App views</span></span>](app-views.md)
