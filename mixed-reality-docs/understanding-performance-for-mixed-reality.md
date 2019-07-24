---
title: 了解混合现实的性能
description: 有关优化 Windows Mixed Reality 应用的性能的高级主题和详细信息
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, 混合现实, 虚拟现实, VR, 先生, 性能, 优化, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548826"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="242e6-104">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="242e6-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="242e6-105">本文介绍了合理化混合现实应用性能的重要性。</span><span class="sxs-lookup"><span data-stu-id="242e6-105">This article is an introduction into rationalizing the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="242e6-106">如果你的应用程序未以最佳帧速率运行, 则用户体验会大幅降低。</span><span class="sxs-lookup"><span data-stu-id="242e6-106">User experience can be greatly degraded if your application does not run at optimal frame rate.</span></span> <span data-ttu-id="242e6-107">全息影像看起来不稳定, 并且头跟踪的环境不准确, 导致用户体验不佳。</span><span class="sxs-lookup"><span data-stu-id="242e6-107">Holograms will appear unstable and head tracking of the environment will be inaccurate leading to an poor experience for the user.</span></span> <span data-ttu-id="242e6-108">事实上, 必须将性能视为用于混合现实开发的第一类功能, 而不是稳定、循环结束任务。</span><span class="sxs-lookup"><span data-stu-id="242e6-108">Indeed, performance must be considered as a first class feature for Mixed Reality development and not a stabilization, end of cycle task.</span></span>

<span data-ttu-id="242e6-109">为了查看, 下面列出了每个目标平台的高性能帧速率值。</span><span class="sxs-lookup"><span data-stu-id="242e6-109">For review, the performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="242e6-110">平台</span><span class="sxs-lookup"><span data-stu-id="242e6-110">Platform</span></span> | <span data-ttu-id="242e6-111">目标帧速率</span><span class="sxs-lookup"><span data-stu-id="242e6-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="242e6-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="242e6-112">HoloLens</span></span>](hololens-hardware-details.md) | <span data-ttu-id="242e6-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="242e6-113">60 FPS</span></span> |
| [<span data-ttu-id="242e6-114">Windows Mixed Reality 超 Pc</span><span class="sxs-lookup"><span data-stu-id="242e6-114">Windows Mixed Reality Ultra PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="242e6-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="242e6-115">90 FPS</span></span> |
| [<span data-ttu-id="242e6-116">Windows Mixed Reality Pc</span><span class="sxs-lookup"><span data-stu-id="242e6-116">Windows Mixed Reality PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="242e6-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="242e6-117">60 FPS</span></span> |

<span data-ttu-id="242e6-118">下图提供了有关最佳实践的一般概述, 并提供了接近目标帧速率的理解。</span><span class="sxs-lookup"><span data-stu-id="242e6-118">The framework below gives a general outline for best practices and understandings towards hitting target frame rates.</span></span> <span data-ttu-id="242e6-119">若要深入了解详细信息, 请考虑阅读[有关 Unity 的性能建议一文](performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="242e6-119">To dive further into details, consider reading the [performance recommendations for Unity article](performance-recommendations-for-unity.md).</span></span> <span data-ttu-id="242e6-120">具体而言, 本文将讨论如何测量 Unity Windows Mixed Reality 应用中的帧速率, 以及在 Unity 环境中采取的步骤来提高性能。</span><span class="sxs-lookup"><span data-stu-id="242e6-120">In particular, this related article will discuss how to measure framerate in your Unity Windows Mixed Reality app as well as steps to take in the Unity environment to improve performance.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="242e6-121">了解性能瓶颈</span><span class="sxs-lookup"><span data-stu-id="242e6-121">Understanding performance bottlenecks</span></span>

<span data-ttu-id="242e6-122">如果你的应用程序具有绩效不佳的帧速率, 则第一步是分析并了解应用程序的计算工作量。</span><span class="sxs-lookup"><span data-stu-id="242e6-122">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="242e6-123">有两个主要处理器负责呈现场景: CPU 和 GPU。</span><span class="sxs-lookup"><span data-stu-id="242e6-123">There are two primary processors responsible for the work to render your scene: the CPU and the GPU.</span></span> <span data-ttu-id="242e6-124">这两个组件分别处理混合现实应用的不同操作和阶段。</span><span class="sxs-lookup"><span data-stu-id="242e6-124">Each of these two components handle different operations and stages of your Mixed Reality app.</span></span> <span data-ttu-id="242e6-125">有三个关键地方可能出现瓶颈。</span><span class="sxs-lookup"><span data-stu-id="242e6-125">There are three key places where bottlenecks may occur.</span></span> 

1. <span data-ttu-id="242e6-126">**应用线程-CPU** -此线程负责应用逻辑。</span><span class="sxs-lookup"><span data-stu-id="242e6-126">**App Thread - CPU** - This thread is responsible for your app logic.</span></span> <span data-ttu-id="242e6-127">这包括处理输入、动画、物理学以及其他应用逻辑/状态</span><span class="sxs-lookup"><span data-stu-id="242e6-127">This includes processing input, animations, physics, and other app logic/state</span></span>
2. <span data-ttu-id="242e6-128">**将线程 CPU 呈现为 gpu** -此线程负责将绘图调用提交到 gpu。</span><span class="sxs-lookup"><span data-stu-id="242e6-128">**Render Thread - CPU to GPU** - This thread is responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="242e6-129">当应用程序想要呈现某个对象 (如多维数据集或模型) 时, 此线程会将请求发送到 GPU, 该 GPU 具有为呈现进行了优化的体系结构, 以便执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="242e6-129">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU, which has an architecture optimized for rendering, to perform these operations.</span></span>
3. <span data-ttu-id="242e6-130">**GPU**- 
   此处理器最常见地处理应用程序的图形管道, 以将3d 数据 (模型、纹理等) 转换为像素, 并最终生成一个要提交到设备屏幕的二维图像。</span><span class="sxs-lookup"><span data-stu-id="242e6-130">**GPU** - 
 This processor most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, etc) into pixels and ultimately produce a 2D image to submit to your device's screen.</span></span>

![帧的生存期](images/lifetime-of-a-frame.png)

<span data-ttu-id="242e6-132">通常情况下, HoloLens 应用程序将受到 GPU 限制。</span><span class="sxs-lookup"><span data-stu-id="242e6-132">Generally, HoloLens applications will be GPU bounded.</span></span> <span data-ttu-id="242e6-133">但是, 这并不是每个应用程序中的 true, 因此建议使用下面的工具 & 技术来实现特定应用程序的基础。</span><span class="sxs-lookup"><span data-stu-id="242e6-133">However, this does not hold true in every application and thus it is recommended to use the tools & techniques below to get to ground-truth for your particular app.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="242e6-134">如何分析应用程序</span><span class="sxs-lookup"><span data-stu-id="242e6-134">How to analyze your application</span></span>

<span data-ttu-id="242e6-135">有许多工具可让你作为开发人员了解混合现实应用程序的性能配置文件。</span><span class="sxs-lookup"><span data-stu-id="242e6-135">There are many tools that allow you as a developer to understand the performance profile of your Mixed Reality application.</span></span> <span data-ttu-id="242e6-136">这样, 你就可以在具有瓶颈的目标位置, 还可以 manifesting 自己对它们进行调试。</span><span class="sxs-lookup"><span data-stu-id="242e6-136">These will enable you to both target where you have bottlenecks and how they are manifesting themselves to debug them.</span></span>

<span data-ttu-id="242e6-137">这是一系列常用且功能强大的工具, 用于获取应用程序的深入分析信息。</span><span class="sxs-lookup"><span data-stu-id="242e6-137">This is a list of popular and powerful tools to gain deep profiling information for your application.</span></span>
- [<span data-ttu-id="242e6-138">Intel 图形性能分析器</span><span class="sxs-lookup"><span data-stu-id="242e6-138">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="242e6-139">Visual Studio 图形调试器</span><span class="sxs-lookup"><span data-stu-id="242e6-139">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [<span data-ttu-id="242e6-140">Unity 探查器</span><span class="sxs-lookup"><span data-stu-id="242e6-140">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="242e6-141">Unity 框架调试器</span><span class="sxs-lookup"><span data-stu-id="242e6-141">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="242e6-142">如何在任何环境中进行分析</span><span class="sxs-lookup"><span data-stu-id="242e6-142">How to profile in any environment</span></span>

<span data-ttu-id="242e6-143">有一个简单的测试, 可以快速确定你的应用程序中是否有可能会限制 GPU 界限或 CPU。</span><span class="sxs-lookup"><span data-stu-id="242e6-143">There is a simple test to quickly determine if you are likely GPU bounded or CPU bounded in your application.</span></span> <span data-ttu-id="242e6-144">如果减少了渲染器目标输出的分辨率, 则需要计算的像素越少, 因此, 在呈现图像时 GPU 需要执行的工作量就越少。</span><span class="sxs-lookup"><span data-stu-id="242e6-144">If you decrease the resolution of the render target output, there are less pixels to calculate and thus, less work the GPU needs to perform to render an image.</span></span> <span data-ttu-id="242e6-145">视区缩放 (动态分辨率缩放) 是指将图像呈现到较小的呈现器目标, 然后显示输出设备的做法。</span><span class="sxs-lookup"><span data-stu-id="242e6-145">Viewport scaling (dynamic resolution scaling) is the practice of rendering your image to a smaller render target then your output device can display.</span></span> <span data-ttu-id="242e6-146">设备将从较小的一组像素向上采样, 以显示最终图像。</span><span class="sxs-lookup"><span data-stu-id="242e6-146">The device will up-sample from the smaller set of pixels to display your final image.</span></span>

<span data-ttu-id="242e6-147">减少呈现分辨率后, 如果:</span><span class="sxs-lookup"><span data-stu-id="242e6-147">After decreasing rendering resolution, if:</span></span>
1) <span data-ttu-id="242e6-148">应用程序的帧速率**增加**, 则可能会**限制 GPU**</span><span class="sxs-lookup"><span data-stu-id="242e6-148">Application framerate **increases**, then you are likely **GPU Bounded**</span></span>
1) <span data-ttu-id="242e6-149">应用程序的帧速率**未更改**, 则可能会**限制 CPU**</span><span class="sxs-lookup"><span data-stu-id="242e6-149">Application framerate **unchanged**, then you are likely **CPU Bounded**</span></span>

>[!NOTE]
><span data-ttu-id="242e6-150">Unity 提供了可以轻松地修改在运行时通过应用程序的呈现器目标分辨率 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性。</span><span class="sxs-lookup"><span data-stu-id="242e6-150">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="242e6-151">设备上提供的最终映像具有固定的分辨率。</span><span class="sxs-lookup"><span data-stu-id="242e6-151">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="242e6-152">平台将采样低分辨率输出, 以生成更高分辨率的图像, 以便在显示时呈现。</span><span class="sxs-lookup"><span data-stu-id="242e6-152">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="242e6-153">如何改进应用程序</span><span class="sxs-lookup"><span data-stu-id="242e6-153">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="242e6-154">CPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="242e6-154">CPU performance recommendations</span></span>

<span data-ttu-id="242e6-155">通常, 在 CPU 上混合现实应用程序中的大部分工作都涉及到执行场景的 "模拟" 并处理大量的唯一应用程序逻辑。</span><span class="sxs-lookup"><span data-stu-id="242e6-155">Generally, most work in a mixed reality application on the CPU involves performing the "simulation" of the scene and processing extensive unique application logic.</span></span> <span data-ttu-id="242e6-156">因此, 通常将以下方面作为优化目标。</span><span class="sxs-lookup"><span data-stu-id="242e6-156">Thus, the following areas are usually targeted for optimization.</span></span>

- <span data-ttu-id="242e6-157">Animations</span><span class="sxs-lookup"><span data-stu-id="242e6-157">Animations</span></span>
- <span data-ttu-id="242e6-158">简化物理学</span><span class="sxs-lookup"><span data-stu-id="242e6-158">Simplify Physics</span></span>
- <span data-ttu-id="242e6-159">内存分配</span><span class="sxs-lookup"><span data-stu-id="242e6-159">Memory allocations</span></span>
- <span data-ttu-id="242e6-160">复杂算法 (即</span><span class="sxs-lookup"><span data-stu-id="242e6-160">Complex algorithms (i.e</span></span> <span data-ttu-id="242e6-161">反向运动, 路径查找)</span><span class="sxs-lookup"><span data-stu-id="242e6-161">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="242e6-162">GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="242e6-162">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="242e6-163">了解带宽与填充率</span><span class="sxs-lookup"><span data-stu-id="242e6-163">Understanding bandwidth vs fill rate</span></span>
<span data-ttu-id="242e6-164">在 GPU 上呈现帧时, 应用程序通常会被内存带宽或填充速率限制。</span><span class="sxs-lookup"><span data-stu-id="242e6-164">When rendering a frame on the GPU, an application is generally either bounded by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="242e6-165">**内存带宽**是 GPU 可以从内存执行的读取和写入速率</span><span class="sxs-lookup"><span data-stu-id="242e6-165">**Memory bandwidth** is the rate of reads and writes the GPU can perform from memory</span></span>
    - <span data-ttu-id="242e6-166">若要确定带宽限制, 请降低纹理质量并检查是否改进了帧速率。</span><span class="sxs-lookup"><span data-stu-id="242e6-166">To identify bandwidth limitations, reduce texture quality and check if framerate improved.</span></span>
    - <span data-ttu-id="242e6-167">在 Unity 中, 这可以通过在 "**编辑** > **项目设置** >  **[质量" 设置](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 中更改**纹理质量**来实现。</span><span class="sxs-lookup"><span data-stu-id="242e6-167">In Unity, this can be done by changing **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="242e6-168">**填充速率**是指每秒可以通过 GPU 绘制的呈现像素的吞吐量。</span><span class="sxs-lookup"><span data-stu-id="242e6-168">**Fill rate** refers to the throughput of rendered pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="242e6-169">若要确定填充速率限制, 请减小显示分辨率, 并检查是否已提高速度。</span><span class="sxs-lookup"><span data-stu-id="242e6-169">To identify fill rate limitations, decrease the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="242e6-170">在 Unity 中，这可以通过完成 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性</span><span class="sxs-lookup"><span data-stu-id="242e6-170">In Unity, this can be done via the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="242e6-171">内存带宽一般涉及优化到</span><span class="sxs-lookup"><span data-stu-id="242e6-171">Memory bandwidth generally involves optimizations to either</span></span>
1) <span data-ttu-id="242e6-172">降低纹理分辨率</span><span class="sxs-lookup"><span data-stu-id="242e6-172">decrease texture resolutions</span></span>
2) <span data-ttu-id="242e6-173">利用更少纹理 (即</span><span class="sxs-lookup"><span data-stu-id="242e6-173">utilize less textures (i.e</span></span> <span data-ttu-id="242e6-174">法线、镜面等)</span><span class="sxs-lookup"><span data-stu-id="242e6-174">normals, specular, etc)</span></span>

<span data-ttu-id="242e6-175">填充速率主要侧重于减少需要针对最终呈现的像素进行计算的操作的数量。</span><span class="sxs-lookup"><span data-stu-id="242e6-175">Fill rate is primarily focused on reducing the number of operations that need to be computed for a final rendered pixel.</span></span> <span data-ttu-id="242e6-176">这通常会降低</span><span class="sxs-lookup"><span data-stu-id="242e6-176">Examples of this commonly fall into reducing</span></span>
1) <span data-ttu-id="242e6-177">要呈现/处理的对象数</span><span class="sxs-lookup"><span data-stu-id="242e6-177">number of objects to render/process</span></span>
2) <span data-ttu-id="242e6-178">每个着色器的操作数</span><span class="sxs-lookup"><span data-stu-id="242e6-178">number of operations per shader</span></span>
3) <span data-ttu-id="242e6-179">到最终结果的 GPU 阶段数 (几何着色器、后处理效果等)</span><span class="sxs-lookup"><span data-stu-id="242e6-179">number of GPU stages to final result (geometry shaders, post-processing effects, etc)</span></span>
4) <span data-ttu-id="242e6-180">要呈现的像素数 (即</span><span class="sxs-lookup"><span data-stu-id="242e6-180">number of pixels to render (i.e</span></span> <span data-ttu-id="242e6-181">显示分辨率)</span><span class="sxs-lookup"><span data-stu-id="242e6-181">display resolution)</span></span>

#### <a name="reduce-poly-count"></a><span data-ttu-id="242e6-182">减少 poly 计数</span><span class="sxs-lookup"><span data-stu-id="242e6-182">Reduce poly count</span></span>
<span data-ttu-id="242e6-183">较大的多边形计数会导致更多的 GPU 操作, 减少场景中的多边形数量将减少渲染该几何的时间。</span><span class="sxs-lookup"><span data-stu-id="242e6-183">Higher polygon counts result in more operations for the GPU and reducing the number of polygons in your scene will reduce the amount of time to render that geometry.</span></span> <span data-ttu-id="242e6-184">还涉及到其他因素, 这会使几何保持较高的成本, 但多边形计数是确定场景呈现的成本的基本指标。</span><span class="sxs-lookup"><span data-stu-id="242e6-184">There are other factors involved as well in shading the geometry that can still be expensive but polygon count is the base metric to determine how expensive a scene will be to render.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="242e6-185">限制过度绘制</span><span class="sxs-lookup"><span data-stu-id="242e6-185">Limit overdraw</span></span>

<span data-ttu-id="242e6-186">当呈现多个对象但该对象被另一个 (通常是更接近的 occluding 对象) 隐藏时, 将会出现高过度绘制。</span><span class="sxs-lookup"><span data-stu-id="242e6-186">High overdraw occurs when multiple objects are rendered but not outputted to the screen as they are hidden by another, generally closer, occluding object.</span></span> <span data-ttu-id="242e6-187">想象一下, 看看有多个房间和几何的墙壁。</span><span class="sxs-lookup"><span data-stu-id="242e6-187">Imagine looking at a wall that had multiple rooms and geometry behind it.</span></span> <span data-ttu-id="242e6-188">所有几何都将针对呈现进行处理, 但不透明的墙壁确实需要呈现, 因为它 occludes 了所有其他内容的视图。</span><span class="sxs-lookup"><span data-stu-id="242e6-188">All of the geometry would be processed for rendering but only the opaque wall really needs to be rendered as it occludes the view of all other content.</span></span> <span data-ttu-id="242e6-189">这会导致不会浪费当前视图所需的操作。</span><span class="sxs-lookup"><span data-stu-id="242e6-189">This results in wasteful operations that are not needed for the current view.</span></span>

#### <a name="shaders"></a><span data-ttu-id="242e6-190">着色器</span><span class="sxs-lookup"><span data-stu-id="242e6-190">Shaders</span></span>

<span data-ttu-id="242e6-191">着色器是在 GPU 上运行的小程序, 通常确定要呈现的两个重要步骤:</span><span class="sxs-lookup"><span data-stu-id="242e6-191">Shaders are small programs that run on the GPU and generally determine two important steps in rendering:</span></span>
1) <span data-ttu-id="242e6-192">应在屏幕上绘制哪个对象的顶点以及它们在屏幕空间中的位置 (例如</span><span class="sxs-lookup"><span data-stu-id="242e6-192">which object's vertices should be drawn on the screen and where they are in screen space (i.e</span></span> <span data-ttu-id="242e6-193">顶点着色器)</span><span class="sxs-lookup"><span data-stu-id="242e6-193">the Vertex shader)</span></span>
    - <span data-ttu-id="242e6-194">对于每个 GameObject, 顶点着色器通常按顶点执行</span><span class="sxs-lookup"><span data-stu-id="242e6-194">The Vertex shader is generally executed per vertex for every GameObject</span></span>
2) <span data-ttu-id="242e6-195">如何为这些像素着色 (即</span><span class="sxs-lookup"><span data-stu-id="242e6-195">what to color those pixels (i.e</span></span> <span data-ttu-id="242e6-196">像素着色器)</span><span class="sxs-lookup"><span data-stu-id="242e6-196">the Pixel shader)</span></span>
    - <span data-ttu-id="242e6-197">对于为设备呈现的纹理, 将为每个像素执行像素着色器</span><span class="sxs-lookup"><span data-stu-id="242e6-197">The Pixel shader is executed per pixel for the texture being rendered for device present</span></span>

<span data-ttu-id="242e6-198">通常, 着色器会执行许多转换和照明计算。</span><span class="sxs-lookup"><span data-stu-id="242e6-198">Typically shaders perform many transformations and lighting calculations.</span></span> <span data-ttu-id="242e6-199">尽管复杂的照明模型、阴影和其他操作可能会产生极好的结果, 但它们也具有价格。</span><span class="sxs-lookup"><span data-stu-id="242e6-199">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="242e6-200">减少着色器中计算的操作数可大大减少每帧 GPU 需要完成的总体工作。</span><span class="sxs-lookup"><span data-stu-id="242e6-200">Reducing the number of operations computed in shaders can greatly reduce the overall work needed to be done by a GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="242e6-201">着色器编码建议</span><span class="sxs-lookup"><span data-stu-id="242e6-201">Shader coding recommendations</span></span>

- <span data-ttu-id="242e6-202">尽可能使用双线性筛选</span><span class="sxs-lookup"><span data-stu-id="242e6-202">Use bilinear filtering whenever possible</span></span>
- <span data-ttu-id="242e6-203">重新排列表达式以使用 MAD 内部函数, 以便同时执行相乘和 add 操作</span><span class="sxs-lookup"><span data-stu-id="242e6-203">Rearrange expressions to use MAD intrinsics in order to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="242e6-204">在 CPU 上尽可能 Precalculate, 并将其作为常量传递给材料</span><span class="sxs-lookup"><span data-stu-id="242e6-204">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="242e6-205">**优选从像素着色器移动到顶点着色器的操作**</span><span class="sxs-lookup"><span data-stu-id="242e6-205">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="242e6-206">通常, 顶点的 < < 的像素数 (即</span><span class="sxs-lookup"><span data-stu-id="242e6-206">Generally the # of vertices << # of pixels (i.e</span></span> <span data-ttu-id="242e6-207">720p = = 921600 像素, 1080p = = 2073600 像素, 等等)</span><span class="sxs-lookup"><span data-stu-id="242e6-207">720p == 921,600 pixels, 1080p == 2,073,600 pixels, etc)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="242e6-208">删除 GPU 阶段</span><span class="sxs-lookup"><span data-stu-id="242e6-208">Remove GPU stages</span></span>
<span data-ttu-id="242e6-209">后期处理效果可能非常昂贵, 并且通常会阻止应用程序的填充率。</span><span class="sxs-lookup"><span data-stu-id="242e6-209">Post-processing effects can be very expensive and generally inhibit the fill rate of your application.</span></span> <span data-ttu-id="242e6-210">这还包括诸如 MSAA 这样的抗锯齿技术。</span><span class="sxs-lookup"><span data-stu-id="242e6-210">This also includes anti-aliasing techniques such as MSAA.</span></span> <span data-ttu-id="242e6-211">在 HoloLens 上, 建议完全避免使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="242e6-211">On HoloLens, it is recommended to avoid these techniques entirely.</span></span> <span data-ttu-id="242e6-212">此外, 如果可能, 应尽可能避免其他着色器阶段, 如几何、球面和计算着色器。</span><span class="sxs-lookup"><span data-stu-id="242e6-212">Furthermore, additional shader stages such as geometry, hull, and compute shaders should be avoided when possible.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="242e6-213">内存建议</span><span class="sxs-lookup"><span data-stu-id="242e6-213">Memory recommendations</span></span>
<span data-ttu-id="242e6-214">内存分配过多 & 释放操作可能对全息应用程序产生不利影响, 从而导致性能不一致、冻结帧和其他不利行为。</span><span class="sxs-lookup"><span data-stu-id="242e6-214">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="242e6-215">在 Unity 中进行开发时, 了解内存的注意事项尤其重要, 因为内存管理由垃圾回收器控制。</span><span class="sxs-lookup"><span data-stu-id="242e6-215">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="242e6-216">对象池</span><span class="sxs-lookup"><span data-stu-id="242e6-216">Object pooling</span></span>

<span data-ttu-id="242e6-217">对象池是一种常用技术, 可降低对象 & 释放的持续分配成本。</span><span class="sxs-lookup"><span data-stu-id="242e6-217">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="242e6-218">这是通过以下方式实现的: 分配一个较大的相同对象池, 并重新使用此池中的非活动可用实例, 而不是随着时间推移不断地生成和销毁对象。</span><span class="sxs-lookup"><span data-stu-id="242e6-218">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="242e6-219">对象池非常适合在应用过程中具有可变生存期的重复使用的组件。</span><span class="sxs-lookup"><span data-stu-id="242e6-219">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="242e6-220">请参阅</span><span class="sxs-lookup"><span data-stu-id="242e6-220">See also</span></span>
- [<span data-ttu-id="242e6-221">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="242e6-221">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
- [<span data-ttu-id="242e6-222">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="242e6-222">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
