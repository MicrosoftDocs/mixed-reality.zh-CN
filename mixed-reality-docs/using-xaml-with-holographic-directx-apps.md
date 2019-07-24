---
title: 将 XAML 与全息 DirectX 应用配合使用
description: 说明在 DirectX 应用中切换 2D XAML 视图和沉浸式视图的影响, 以及如何有效地利用 XAML 视图和沉浸式视图。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: windows mixed reality, UWP, 应用视图管理, xaml, 键盘, 演练, DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548709"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="0e33b-104">将 XAML 与全息 DirectX 应用配合使用</span><span class="sxs-lookup"><span data-stu-id="0e33b-104">Using XAML with holographic DirectX apps</span></span>

<span data-ttu-id="0e33b-105">本主题介绍在 DirectX 应用中切换[2D XAML 视图和沉浸式视图](app-views.md)的影响, 以及如何有效地利用 XAML 视图和沉浸式视图。</span><span class="sxs-lookup"><span data-stu-id="0e33b-105">This topic explains the impact of switching between [2D XAML views and immersive views](app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="0e33b-106">XAML 视图切换概述</span><span class="sxs-lookup"><span data-stu-id="0e33b-106">XAML view switching overview</span></span>

<span data-ttu-id="0e33b-107">在 HoloLens 上, 可以在以后显示 2D XAML 视图的一种一般的沉浸式应用程序必须首先初始化该 XAML 视图, 并从该处立即切换到沉浸式视图。</span><span class="sxs-lookup"><span data-stu-id="0e33b-107">On HoloLens, a generally immersive app that may later display a 2D XAML view must initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="0e33b-108">这意味着在你的应用程序可以执行任何操作之前, 将加载 XAML。</span><span class="sxs-lookup"><span data-stu-id="0e33b-108">This means XAML will load before your app can do anything.</span></span> <span data-ttu-id="0e33b-109">因此, 启动时间会有一个较小的增加, 当应用程序驻留在后台时, XAML 将继续占用应用进程中的内存空间;启动延迟量和内存使用情况取决于应用程序在切换到本机视图之前对 XAML 执行的操作。</span><span class="sxs-lookup"><span data-stu-id="0e33b-109">As a result, there will be a small increase in your startup time, and XAML will continue to occupy memory space in your app process while it resides in the background; the amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="0e33b-110">如果在 XAML 中根本不执行任何操作, 则启动沉浸式视图除外, 这种影响应该很小。</span><span class="sxs-lookup"><span data-stu-id="0e33b-110">If you do nothing in your XAML start up code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="0e33b-111">此外, 由于全息呈现直接在沉浸式视图中完成, 因此你将避免对该呈现进行任何与 XAML 相关的限制。</span><span class="sxs-lookup"><span data-stu-id="0e33b-111">Also, because your holographic rendering is done directly to the immersive view, you will avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="0e33b-112">请注意, CPU 和 GPU 的内存使用量都是相同的。</span><span class="sxs-lookup"><span data-stu-id="0e33b-112">Note that the memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="0e33b-113">Direct3D 11 能够交换虚拟图形内存, 但它可能无法调换部分或全部 XAML GPU 资源, 而且可能会显著降低性能。</span><span class="sxs-lookup"><span data-stu-id="0e33b-113">Direct3D 11 is able to swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="0e33b-114">无论采用哪种方式, 不加载任何不需要的 XAML 功能都将为应用程序留出更多空间, 并提供更好的体验。</span><span class="sxs-lookup"><span data-stu-id="0e33b-114">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="0e33b-115">XAML 视图切换工作流</span><span class="sxs-lookup"><span data-stu-id="0e33b-115">XAML view switching workflow</span></span>

<span data-ttu-id="0e33b-116">直接从 XAML 进入沉浸式模式的应用的工作流如下所示:</span><span class="sxs-lookup"><span data-stu-id="0e33b-116">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="0e33b-117">应用程序在 2D XAML 视图中启动。</span><span class="sxs-lookup"><span data-stu-id="0e33b-117">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="0e33b-118">应用的 XAML 启动序列检测当前系统是否支持全息呈现:</span><span class="sxs-lookup"><span data-stu-id="0e33b-118">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="0e33b-119">如果是这样, 该应用程序会创建沉浸式视图, 并立即将其放到前台。</span><span class="sxs-lookup"><span data-stu-id="0e33b-119">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="0e33b-120">对于 Windows Mixed Reality 设备上不需要的任何内容 (包括在 XAML 视图中呈现类和资产加载), 将跳过 XAML 加载。</span><span class="sxs-lookup"><span data-stu-id="0e33b-120">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="0e33b-121">如果应用使用 XAML 进行键盘输入, 则仍应创建该输入页。</span><span class="sxs-lookup"><span data-stu-id="0e33b-121">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="0e33b-122">如果不是这样, 则 XAML 视图可以像平常一样继续工作。</span><span class="sxs-lookup"><span data-stu-id="0e33b-122">If not, the XAML view can proceed with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="0e33b-123">用于跨两个视图呈现图形的提示</span><span class="sxs-lookup"><span data-stu-id="0e33b-123">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="0e33b-124">如果你的应用程序需要在 Windows Mixed Reality 中为 XAML 视图实现某种数量的应用程序, 最佳做法是创建一个可同时使用这两个视图的呈现器。</span><span class="sxs-lookup"><span data-stu-id="0e33b-124">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="0e33b-125">呈现器应该是可从两个视图访问的一个实例, 并且它应该能够在二维和全息呈现之间切换。</span><span class="sxs-lookup"><span data-stu-id="0e33b-125">The renderer should be one instance that can be accessed from both views, and it should be able to switch between 2D and holographic rendering.</span></span> <span data-ttu-id="0e33b-126">这样一来, GPU 资产只会加载一次-这会减少加载时间、内存影响以及切换视图时要交换的资源量。</span><span class="sxs-lookup"><span data-stu-id="0e33b-126">That way GPU assets are only loaded once - this reduces load times, memory impact, and the amount of resources to be swapped when switching views.</span></span>
