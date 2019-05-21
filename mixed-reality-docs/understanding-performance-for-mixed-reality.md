---
title: 混合现实的了解性能
description: 优化 Windows 混合现实应用程序的性能上的高级主题和详细信息
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows 混合现实、 混合的现实中，虚拟现实、 VR、 MR、 性能、 优化、 CPU、 GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592659"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="dcfe5-104">混合现实的了解性能</span><span class="sxs-lookup"><span data-stu-id="dcfe5-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="dcfe5-105">本文将介绍到合理化 for Mixed Reality 应用性能的重要性。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-105">This article is an introduction into rationalizing the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="dcfe5-106">如果你的应用程序不会运行以获得最佳的帧速率，可以极大地降低用户体验。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-106">User experience can be greatly degraded if your application does not run at optimal frame rate.</span></span> <span data-ttu-id="dcfe5-107">全息将出现不稳定，头环境的跟踪将不准确导致体验不佳的用户。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-107">Holograms will appear unstable and head tracking of the environment will be inaccurate leading to an poor experience for the user.</span></span> <span data-ttu-id="dcfe5-108">实际上，作为混合现实开发并不稳定、 周期任务的末尾的第一个类功能，必须考虑性能。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-108">Indeed, performance must be considered as a first class feature for Mixed Reality development and not a stabilization, end of cycle task.</span></span>

<span data-ttu-id="dcfe5-109">查看，下面列出了每个目标平台的高性能帧速率值。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-109">For review, the performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="dcfe5-110">平台</span><span class="sxs-lookup"><span data-stu-id="dcfe5-110">Platform</span></span> | <span data-ttu-id="dcfe5-111">目标帧速率</span><span class="sxs-lookup"><span data-stu-id="dcfe5-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="dcfe5-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="dcfe5-112">HoloLens</span></span>](hololens-hardware-details.md) | <span data-ttu-id="dcfe5-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="dcfe5-113">60 FPS</span></span> |
| [<span data-ttu-id="dcfe5-114">Windows Mixed Reality Ultra Pc</span><span class="sxs-lookup"><span data-stu-id="dcfe5-114">Windows Mixed Reality Ultra PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="dcfe5-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="dcfe5-115">90 FPS</span></span> |
| [<span data-ttu-id="dcfe5-116">混合现实 Pc 的 Windows</span><span class="sxs-lookup"><span data-stu-id="dcfe5-116">Windows Mixed Reality PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="dcfe5-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="dcfe5-117">60 FPS</span></span> |

<span data-ttu-id="dcfe5-118">下面的框架为一般摘要提供了有关的最佳实践和理解针对达到目标帧速率。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-118">The framework below gives a general outline for best practices and understandings towards hitting target frame rates.</span></span> <span data-ttu-id="dcfe5-119">若要深入了解更多详细信息，可以考虑阅读[Unity 项目的性能建议](performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-119">To dive further into details, consider reading the [performance recommendations for Unity article](performance-recommendations-for-unity.md).</span></span> <span data-ttu-id="dcfe5-120">具体而言，此相关的文章将讨论如何测量 Unity Windows Mixed Reality 应用以及要在 Unity 环境中执行以提高性能的步骤中的帧速率。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-120">In particular, this related article will discuss how to measure framerate in your Unity Windows Mixed Reality app as well as steps to take in the Unity environment to improve performance.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="dcfe5-121">了解性能瓶颈</span><span class="sxs-lookup"><span data-stu-id="dcfe5-121">Understanding performance bottlenecks</span></span>

<span data-ttu-id="dcfe5-122">如果你的应用程序性能不佳的帧速率，第一步是分析并了解你的应用程序是计算密集型操作。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-122">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="dcfe5-123">有两个主要处理器负责的工作来呈现您的场景： CPU 和 GPU。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-123">There are two primary processors responsible for the work to render your scene: the CPU and the GPU.</span></span> <span data-ttu-id="dcfe5-124">这两个组件的每个处理不同的操作和混合现实应用程序的阶段。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-124">Each of these two components handle different operations and stages of your Mixed Reality app.</span></span> <span data-ttu-id="dcfe5-125">有三个密钥的位置可能会出现瓶颈。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-125">There are three key places where bottlenecks may occur.</span></span> 

1. <span data-ttu-id="dcfe5-126">**应用程序线程的 CPU** -此线程负责你的应用逻辑。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-126">**App Thread - CPU** - This thread is responsible for your app logic.</span></span> <span data-ttu-id="dcfe5-127">这包括处理输入、 动画、 物理特性、 和其他应用程序逻辑/状态</span><span class="sxs-lookup"><span data-stu-id="dcfe5-127">This includes processing input, animations, physics, and other app logic/state</span></span>
2. <span data-ttu-id="dcfe5-128">**呈现线程的 CPU 与 GPU** -此线程负责提交到 GPU 在绘图调用。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-128">**Render Thread - CPU to GPU** - This thread is responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="dcfe5-129">当您的应用程序想要呈现的对象例如多维数据集或模型时，此线程将请求发送到 GPU，其中的优化，以便呈现体系结构，以执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-129">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU, which has an architecture optimized for rendering, to perform these operations.</span></span>
3. <span data-ttu-id="dcfe5-130">**GPU** - 
   此处理器最常处理图形管道的应用程序 （模型、 纹理等） 的 3D 数据转换为像素，并最终生成 2D 图像提交到你的设备的屏幕。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-130">**GPU** - 
 This processor most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, etc) into pixels and ultimately produce a 2D image to submit to your device's screen.</span></span>

![框架的生存期](images/lifetime-of-a-frame.png)

<span data-ttu-id="dcfe5-132">通常情况下，HoloLens 应用程序将有限的 GPU。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-132">Generally, HoloLens applications will be GPU bounded.</span></span> <span data-ttu-id="dcfe5-133">但是，这不保存在每个应用程序中，则返回 true，因此建议使用工具和技术如下回到地面点真实成分为特定应用。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-133">However, this does not hold true in every application and thus it is recommended to use the tools & techniques below to get to ground-truth for your particular app.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="dcfe5-134">如何分析应用程序</span><span class="sxs-lookup"><span data-stu-id="dcfe5-134">How to analyze your application</span></span>

<span data-ttu-id="dcfe5-135">有许多工具，它们可以作为开发人员了解混合现实应用程序的性能配置文件。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-135">There are many tools that allow you as a developer to understand the performance profile of your Mixed Reality application.</span></span> <span data-ttu-id="dcfe5-136">这使您能够通过了瓶颈和如何它们都表现形式本身来对其进行调试这两个目标。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-136">These will enable you to both target where you have bottlenecks and how they are manifesting themselves to debug them.</span></span>

<span data-ttu-id="dcfe5-137">这是一系列流行且强大的工具，以获取你的应用程序的深入分析信息。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-137">This is a list of popular and powerful tools to gain deep profiling information for your application.</span></span>
- [<span data-ttu-id="dcfe5-138">Intel Graphics Performance Analyzers</span><span class="sxs-lookup"><span data-stu-id="dcfe5-138">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="dcfe5-139">Visual Studio 图形调试器</span><span class="sxs-lookup"><span data-stu-id="dcfe5-139">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [<span data-ttu-id="dcfe5-140">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="dcfe5-140">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="dcfe5-141">Unity 框架调试器</span><span class="sxs-lookup"><span data-stu-id="dcfe5-141">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="dcfe5-142">如何在任何环境中的配置文件</span><span class="sxs-lookup"><span data-stu-id="dcfe5-142">How to profile in any environment</span></span>

<span data-ttu-id="dcfe5-143">没有简单的测试来快速确定你是否有可能 GPU 绑定或 CPU 绑定应用程序中。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-143">There is a simple test to quickly determine if you are likely GPU bounded or CPU bounded in your application.</span></span> <span data-ttu-id="dcfe5-144">如果减少呈现器目标输出的分辨率，有更少的像素为单位计算，因此，工作较少 GPU 需要执行以呈现图像。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-144">If you decrease the resolution of the render target output, there are less pixels to calculate and thus, less work the GPU needs to perform to render an image.</span></span> <span data-ttu-id="dcfe5-145">视区缩放 （动态解析缩放） 是呈现到较小的映像的做法是呈现器目标，然后输出设备可以显示。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-145">Viewport scaling (dynamic resolution scaling) is the practice of rendering your image to a smaller render target then your output device can display.</span></span> <span data-ttu-id="dcfe5-146">设备将最多的示例从较小的集要显示最终图像的像素。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-146">The device will up-sample from the smaller set of pixels to display your final image.</span></span>

<span data-ttu-id="dcfe5-147">之后如果减少呈现解决方法：</span><span class="sxs-lookup"><span data-stu-id="dcfe5-147">After decreasing rendering resolution, if:</span></span>
1) <span data-ttu-id="dcfe5-148">应用程序帧速率**增加**，那么您就有可能**GPU 界定**</span><span class="sxs-lookup"><span data-stu-id="dcfe5-148">Application framerate **increases**, then you are likely **GPU Bounded**</span></span>
1) <span data-ttu-id="dcfe5-149">应用程序帧速率**保持不变**，那么您就有可能**CPU 绑定**</span><span class="sxs-lookup"><span data-stu-id="dcfe5-149">Application framerate **unchanged**, then you are likely **CPU Bounded**</span></span>

>[!NOTE]
><span data-ttu-id="dcfe5-150">Unity 提供了可以轻松地修改在运行时通过应用程序的呈现器目标分辨率 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-150">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="dcfe5-151">最终图像显示在设备上具有固定的分辨率。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-151">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="dcfe5-152">该平台将示例输出以生成在显示器上呈现的更高分辨率图像的较低分辨率。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-152">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="dcfe5-153">如何提高你的应用程序</span><span class="sxs-lookup"><span data-stu-id="dcfe5-153">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="dcfe5-154">CPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="dcfe5-154">CPU performance recommendations</span></span>

<span data-ttu-id="dcfe5-155">通常情况下，在 CPU 上的混合的现实应用程序中的大部分工作涉及执行"模拟"的场景和处理大量唯一的应用程序逻辑。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-155">Generally, most work in a mixed reality application on the CPU involves performing the "simulation" of the scene and processing extensive unique application logic.</span></span> <span data-ttu-id="dcfe5-156">因此，以下几个方面通常针对优化。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-156">Thus, the following areas are usually targeted for optimization.</span></span>

- <span data-ttu-id="dcfe5-157">Animations</span><span class="sxs-lookup"><span data-stu-id="dcfe5-157">Animations</span></span>
- <span data-ttu-id="dcfe5-158">简化的物理</span><span class="sxs-lookup"><span data-stu-id="dcfe5-158">Simplify Physics</span></span>
- <span data-ttu-id="dcfe5-159">内存分配</span><span class="sxs-lookup"><span data-stu-id="dcfe5-159">Memory allocations</span></span>
- <span data-ttu-id="dcfe5-160">复杂的算法 （即</span><span class="sxs-lookup"><span data-stu-id="dcfe5-160">Complex algorithms (i.e</span></span> <span data-ttu-id="dcfe5-161">反向运动学、 路径查找）</span><span class="sxs-lookup"><span data-stu-id="dcfe5-161">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="dcfe5-162">GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="dcfe5-162">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="dcfe5-163">了解带宽 vs 的填充率</span><span class="sxs-lookup"><span data-stu-id="dcfe5-163">Understanding bandwidth vs fill rate</span></span>
<span data-ttu-id="dcfe5-164">当呈现在 GPU 上的帧，应用程序是通常是由内存带宽或填充率绑定。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-164">When rendering a frame on the GPU, an application is generally either bounded by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="dcfe5-165">**内存带宽**是读取操作的速率和 GPU 可以执行从内存写入</span><span class="sxs-lookup"><span data-stu-id="dcfe5-165">**Memory bandwidth** is the rate of reads and writes the GPU can perform from memory</span></span>
    - <span data-ttu-id="dcfe5-166">若要确定带宽限制，减少纹理质量，并检查是否有所改善帧速率。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-166">To identify bandwidth limitations, reduce texture quality and check if framerate improved.</span></span>
    - <span data-ttu-id="dcfe5-167">在 Unity 中，这可以通过更改**纹理质量**中**编辑** > **项目设置** >   **[质量设置](https://docs.unity3d.com/Manual/class-QualitySettings.html)**。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-167">In Unity, this can be done by changing **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="dcfe5-168">**填充率**指的是呈现可由 GPU 每秒绘制的像素为单位的吞吐量。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-168">**Fill rate** refers to the throughput of rendered pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="dcfe5-169">若要标识填充速率限制，降低显示分辨率和检查帧速率是否有所改善。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-169">To identify fill rate limitations, decrease the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="dcfe5-170">在 Unity 中，这可以通过完成 *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性</span><span class="sxs-lookup"><span data-stu-id="dcfe5-170">In Unity, this can be done via the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="dcfe5-171">内存带宽通常涉及到为优化</span><span class="sxs-lookup"><span data-stu-id="dcfe5-171">Memory bandwidth generally involves optimizations to either</span></span>
1) <span data-ttu-id="dcfe5-172">减少纹理的解决方法</span><span class="sxs-lookup"><span data-stu-id="dcfe5-172">decrease texture resolutions</span></span>
2) <span data-ttu-id="dcfe5-173">使用更少的纹理 （即</span><span class="sxs-lookup"><span data-stu-id="dcfe5-173">utilize less textures (i.e</span></span> <span data-ttu-id="dcfe5-174">法线，反射高光，等等）</span><span class="sxs-lookup"><span data-stu-id="dcfe5-174">normals, specular, etc)</span></span>

<span data-ttu-id="dcfe5-175">填充率主要致力于减少需要为最终呈现像素计算的操作的数目。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-175">Fill rate is primarily focused on reducing the number of operations that need to be computed for a final rendered pixel.</span></span> <span data-ttu-id="dcfe5-176">此示例通常划分为减少</span><span class="sxs-lookup"><span data-stu-id="dcfe5-176">Examples of this commonly fall into reducing</span></span>
1) <span data-ttu-id="dcfe5-177">要呈现/处理的对象数</span><span class="sxs-lookup"><span data-stu-id="dcfe5-177">number of objects to render/process</span></span>
2) <span data-ttu-id="dcfe5-178">每个着色器的操作数</span><span class="sxs-lookup"><span data-stu-id="dcfe5-178">number of operations per shader</span></span>
3) <span data-ttu-id="dcfe5-179">GPU 阶段到最终结果 （几何着色，后处理效果，等等） 的数目</span><span class="sxs-lookup"><span data-stu-id="dcfe5-179">number of GPU stages to final result (geometry shaders, post-processing effects, etc)</span></span>
4) <span data-ttu-id="dcfe5-180">要呈现 （即的像素数</span><span class="sxs-lookup"><span data-stu-id="dcfe5-180">number of pixels to render (i.e</span></span> <span data-ttu-id="dcfe5-181">显示分辨率）</span><span class="sxs-lookup"><span data-stu-id="dcfe5-181">display resolution)</span></span>

#### <a name="reduce-poly-count"></a><span data-ttu-id="dcfe5-182">减少 poly 计数</span><span class="sxs-lookup"><span data-stu-id="dcfe5-182">Reduce poly count</span></span>
<span data-ttu-id="dcfe5-183">减少您的场景中的多边形的数量将减少的时间来呈现该几何图形和更高版本的多边形计数中的 GPU 的更多操作的结果。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-183">Higher polygon counts result in more operations for the GPU and reducing the number of polygons in your scene will reduce the amount of time to render that geometry.</span></span> <span data-ttu-id="dcfe5-184">还有其他一些因素也参与明暗度的几何图形，它仍可能很昂贵，但会多边形计数的基本度量指标来确定如何昂贵场景会呈现。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-184">There are other factors involved as well in shading the geometry that can still be expensive but polygon count is the base metric to determine how expensive a scene will be to render.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="dcfe5-185">限制过度绘制</span><span class="sxs-lookup"><span data-stu-id="dcfe5-185">Limit overdraw</span></span>

<span data-ttu-id="dcfe5-186">高过度绘制多个对象都呈现，但不是输出到屏幕，因为它们隐藏的另一个的通常接近 occluding 对象时发生。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-186">High overdraw occurs when multiple objects are rendered but not outputted to the screen as they are hidden by another, generally closer, occluding object.</span></span> <span data-ttu-id="dcfe5-187">假设在墙上具有多个房间和其后的几何图形的查找。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-187">Imagine looking at a wall that had multiple rooms and geometry behind it.</span></span> <span data-ttu-id="dcfe5-188">将呈现为处理所有的几何图形，但仅不透明墙上插座真正需要进行的呈现将如 occludes 所有其他内容的视图。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-188">All of the geometry would be processed for rendering but only the opaque wall really needs to be rendered as it occludes the view of all other content.</span></span> <span data-ttu-id="dcfe5-189">这会导致不需要的当前视图的必要操作。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-189">This results in wasteful operations that are not needed for the current view.</span></span>

#### <a name="shaders"></a><span data-ttu-id="dcfe5-190">着色器</span><span class="sxs-lookup"><span data-stu-id="dcfe5-190">Shaders</span></span>

<span data-ttu-id="dcfe5-191">着色器是小程序中，在 GPU 上运行，并通常确定呈现中的两个重要步骤：</span><span class="sxs-lookup"><span data-stu-id="dcfe5-191">Shaders are small programs that run on the GPU and generally determine two important steps in rendering:</span></span>
1) <span data-ttu-id="dcfe5-192">应在屏幕和，并在屏幕空间 （即上绘制的对象的顶点</span><span class="sxs-lookup"><span data-stu-id="dcfe5-192">which object's vertices should be drawn on the screen and where they are in screen space (i.e</span></span> <span data-ttu-id="dcfe5-193">顶点着色器）</span><span class="sxs-lookup"><span data-stu-id="dcfe5-193">the Vertex shader)</span></span>
    - <span data-ttu-id="dcfe5-194">适用于每个 GameObject 中，将顶点着色器通常执行每顶点</span><span class="sxs-lookup"><span data-stu-id="dcfe5-194">The Vertex shader is generally executed per vertex for every GameObject</span></span>
2) <span data-ttu-id="dcfe5-195">内容 （即，这些像素的颜色</span><span class="sxs-lookup"><span data-stu-id="dcfe5-195">what to color those pixels (i.e</span></span> <span data-ttu-id="dcfe5-196">像素着色器）</span><span class="sxs-lookup"><span data-stu-id="dcfe5-196">the Pixel shader)</span></span>
    - <span data-ttu-id="dcfe5-197">像素着色器执行每个像素呈现为设备存在的纹理</span><span class="sxs-lookup"><span data-stu-id="dcfe5-197">The Pixel shader is executed per pixel for the texture being rendered for device present</span></span>

<span data-ttu-id="dcfe5-198">着色器，通常执行很多转换和照明计算。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-198">Typically shaders perform many transformations and lighting calculations.</span></span> <span data-ttu-id="dcfe5-199">尽管复杂照明模型、 阴影和其他操作可以生成出色的结果，但它们还会附带一个价格。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-199">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="dcfe5-200">减少的计算着色器中的操作可以极大地降低由每个框架的 GPU 执行所需的整体工作。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-200">Reducing the number of operations computed in shaders can greatly reduce the overall work needed to be done by a GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="dcfe5-201">着色器编码的建议</span><span class="sxs-lookup"><span data-stu-id="dcfe5-201">Shader coding recommendations</span></span>

- <span data-ttu-id="dcfe5-202">使用双线性筛选，只要有可能</span><span class="sxs-lookup"><span data-stu-id="dcfe5-202">Use bilinear filtering whenever possible</span></span>
- <span data-ttu-id="dcfe5-203">重新排列表达式才能执行乘法和 add 操作在同一时间使用 MAD 内部函数</span><span class="sxs-lookup"><span data-stu-id="dcfe5-203">Rearrange expressions to use MAD intrinsics in order to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="dcfe5-204">要尽可能多地在 CPU 上预先计算并将其作为常量传递到材料</span><span class="sxs-lookup"><span data-stu-id="dcfe5-204">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="dcfe5-205">**倾向于从像素着色器向顶点着色器的移动操作**</span><span class="sxs-lookup"><span data-stu-id="dcfe5-205">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="dcfe5-206">通常的顶点 # << # 像素 （即</span><span class="sxs-lookup"><span data-stu-id="dcfe5-206">Generally the # of vertices << # of pixels (i.e</span></span> <span data-ttu-id="dcfe5-207">720p = = 921,600 像素，1080p = = 2,073,600 像素为单位，等等)</span><span class="sxs-lookup"><span data-stu-id="dcfe5-207">720p == 921,600 pixels, 1080p == 2,073,600 pixels, etc)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="dcfe5-208">删除 GPU 阶段</span><span class="sxs-lookup"><span data-stu-id="dcfe5-208">Remove GPU stages</span></span>
<span data-ttu-id="dcfe5-209">后期处理效果可以开销非常大并通常会禁止您的应用程序的填充率。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-209">Post-processing effects can be very expensive and generally inhibit the fill rate of your application.</span></span> <span data-ttu-id="dcfe5-210">这还包括抗锯齿技术，如 MSAA。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-210">This also includes anti-aliasing techniques such as MSAA.</span></span> <span data-ttu-id="dcfe5-211">上 HoloLens，建议完全避免这些技术。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-211">On HoloLens, it is recommended to avoid these techniques entirely.</span></span> <span data-ttu-id="dcfe5-212">此外，如果可能，应避免额外的着色器阶段，如几何图形、 外壳，并计算着色器。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-212">Furthermore, additional shader stages such as geometry, hull, and compute shaders should be avoided when possible.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="dcfe5-213">内存建议</span><span class="sxs-lookup"><span data-stu-id="dcfe5-213">Memory recommendations</span></span>
<span data-ttu-id="dcfe5-214">过多的内存分配和解除分配操作可以产生负面影响，从而导致不一致的性能、 冻结的框架和其他造成不利影响的行为在全息版应用程序上。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-214">Excessive memory allocation & deallocation operations can have adverse effects on your holographic application resulting in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="dcfe5-215">它是由于内存管理控制垃圾回收器在 Unity 中进行开发时了解内存注意事项尤为重要。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-215">It is especially important to understand memory considerations when developing in Unity since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="dcfe5-216">对象池</span><span class="sxs-lookup"><span data-stu-id="dcfe5-216">Object pooling</span></span>

<span data-ttu-id="dcfe5-217">对象池是一种常用的方法，以降低成本的连续分配和释放的对象。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-217">Object pooling is a popular technique to reduce the cost of continuous allocations & deallocations of objects.</span></span> <span data-ttu-id="dcfe5-218">这是通过分配完全相同的对象的大型池和重新使用从这个池而不是不断地生成和随着时间的推移销毁对象的非活动状态、 可用的实例。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-218">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="dcfe5-219">对象池非常适合用于具有变量的生存期期间应用的可重用组件。</span><span class="sxs-lookup"><span data-stu-id="dcfe5-219">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcfe5-220">请参阅</span><span class="sxs-lookup"><span data-stu-id="dcfe5-220">See also</span></span>
- [<span data-ttu-id="dcfe5-221">Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="dcfe5-221">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
- [<span data-ttu-id="dcfe5-222">Unity 的推荐的设置</span><span class="sxs-lookup"><span data-stu-id="dcfe5-222">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
