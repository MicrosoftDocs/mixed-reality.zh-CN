---
title: 全息版的 DirectX 应用中使用 XAML
description: 介绍 2D XAML 视图和 DirectX 应用程序，以及如何有效地使用 XAML 视图和沉浸式视图中的沉浸式视图之间切换的影响。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: windows mixed 的 reality，UWP 应用查看管理、 xaml、 键盘、 演练中，DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590331"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="3f1da-104">全息版的 DirectX 应用中使用 XAML</span><span class="sxs-lookup"><span data-stu-id="3f1da-104">Using XAML with holographic DirectX apps</span></span>

<span data-ttu-id="3f1da-105">本主题介绍了影响之间切换[2D XAML 视图和沉浸式视图](app-views.md)DirectX 应用程序，以及如何有效地使用 XAML 视图和沉浸式视图。</span><span class="sxs-lookup"><span data-stu-id="3f1da-105">This topic explains the impact of switching between [2D XAML views and immersive views](app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="3f1da-106">XAML 视图切换概述</span><span class="sxs-lookup"><span data-stu-id="3f1da-106">XAML view switching overview</span></span>

<span data-ttu-id="3f1da-107">上 HoloLens，可能会更高版本显示二维的 XAML 视图通常沉浸式应用程序必须首先初始化该 XAML 视图并从那里立即切换到的沉浸式视图。</span><span class="sxs-lookup"><span data-stu-id="3f1da-107">On HoloLens, a generally immersive app that may later display a 2D XAML view must initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="3f1da-108">这意味着您的应用程序可以执行任何操作之前，将加载 XAML。</span><span class="sxs-lookup"><span data-stu-id="3f1da-108">This means XAML will load before your app can do anything.</span></span> <span data-ttu-id="3f1da-109">因此，将略微提高您的启动时间，并且 XAML 会继续占用你应用程序进程中的内存空间，它驻留在后台; 中时启动延迟和使用情况取决于应用程序的功能与 XAML 切换到本机视图之前的内存量。</span><span class="sxs-lookup"><span data-stu-id="3f1da-109">As a result, there will be a small increase in your startup time, and XAML will continue to occupy memory space in your app process while it resides in the background; the amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="3f1da-110">如果你不执行任何操作启动代码首先启动沉浸式视图只在 XAML 中，影响应该很小。</span><span class="sxs-lookup"><span data-stu-id="3f1da-110">If you do nothing in your XAML start up code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="3f1da-111">此外，由于全息呈现时执行直接到沉浸式视图，因此将避免这样的呈现任何与 XAML 相关限制。</span><span class="sxs-lookup"><span data-stu-id="3f1da-111">Also, because your holographic rendering is done directly to the immersive view, you will avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="3f1da-112">请注意，内存使用情况的 CPU 和 GPU 计数。</span><span class="sxs-lookup"><span data-stu-id="3f1da-112">Note that the memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="3f1da-113">Direct3D 11 是能够交换虚拟图形内存，但它可能不能换出的部分或所有 XAML GPU 资源，并可能会有明显的性能下降。</span><span class="sxs-lookup"><span data-stu-id="3f1da-113">Direct3D 11 is able to swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="3f1da-114">无论哪种方式，不加载任何 XAML 功能，您不需要将保留您的应用程序的更多空间，并提供更好的体验。</span><span class="sxs-lookup"><span data-stu-id="3f1da-114">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="3f1da-115">切换工作流的 XAML 视图</span><span class="sxs-lookup"><span data-stu-id="3f1da-115">XAML view switching workflow</span></span>

<span data-ttu-id="3f1da-116">直接从 XAML 转至沉浸式模式下的应用的工作流如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f1da-116">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="3f1da-117">应用启动 2D XAML 视图中。</span><span class="sxs-lookup"><span data-stu-id="3f1da-117">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="3f1da-118">应用程序的 XAML 启动序列检测到当前的系统是否支持全息呈现：</span><span class="sxs-lookup"><span data-stu-id="3f1da-118">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="3f1da-119">如果是这样，应用程序创建沉浸式视图，并立即将其带到前台。</span><span class="sxs-lookup"><span data-stu-id="3f1da-119">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="3f1da-120">XAML 加载将跳过任何不必要的内容 Windows Mixed Reality 在设备上，包括任何呈现的类和加载 XAML 视图中的资产。</span><span class="sxs-lookup"><span data-stu-id="3f1da-120">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="3f1da-121">如果应用正在使用的键盘输入 XAML，则仍应创建该输入的页。</span><span class="sxs-lookup"><span data-stu-id="3f1da-121">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="3f1da-122">如果没有，XAML 视图可以像往常一样继续进行业务。</span><span class="sxs-lookup"><span data-stu-id="3f1da-122">If not, the XAML view can proceed with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="3f1da-123">在这两个视图之间呈现图形的提示</span><span class="sxs-lookup"><span data-stu-id="3f1da-123">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="3f1da-124">如果您的应用程序需要 Windows 混合现实中的 XAML 视图在 DirectX 中实现一定量，最好的方法就是呈现的创建一个可以使用这两个视图的呈现器。</span><span class="sxs-lookup"><span data-stu-id="3f1da-124">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="3f1da-125">呈现器应该是可以从这两个视图中，访问的一个实例，它应能 2D 和全息呈现之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="3f1da-125">The renderer should be one instance that can be accessed from both views, and it should be able to switch between 2D and holographic rendering.</span></span> <span data-ttu-id="3f1da-126">这样一来 GPU 资产仅加载一次-这将减少加载时间、 内存影响和数量的资源来进行交换时切换视图。</span><span class="sxs-lookup"><span data-stu-id="3f1da-126">That way GPU assets are only loaded once - this reduces load times, memory impact, and the amount of resources to be swapped when switching views.</span></span>
