---
title: 了解混合现实的性能
description: 有关优化 Windows Mixed Reality 应用的性能的高级主题和详细信息
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality，混合现实，虚拟现实，VR，先生，性能，优化，CPU，GPU
ms.openlocfilehash: 7d8a0c95d59ec7e42e11bc1e1b6b40c702e01529
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438232"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="57f5b-104">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="57f5b-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="57f5b-105">本文介绍了如何了解混合现实应用的性能的重要性。</span><span class="sxs-lookup"><span data-stu-id="57f5b-105">This article is an introduction to understanding the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="57f5b-106">如果你的应用程序未以最佳帧速率运行，则用户体验会大幅降低。</span><span class="sxs-lookup"><span data-stu-id="57f5b-106">User experience can be greatly degraded if your application does not run at optimal frame rate.</span></span> <span data-ttu-id="57f5b-107">全息影像会显得不稳定，因此，对环境的打印头跟踪是不准确的，导致用户体验不佳。</span><span class="sxs-lookup"><span data-stu-id="57f5b-107">Holograms will appear unstable and head tracking of the environment will be inaccurate, leading to an poor experience for the user.</span></span> <span data-ttu-id="57f5b-108">对于混合现实开发而言，必须将性能视为第一类功能，而不是波兰语任务。</span><span class="sxs-lookup"><span data-stu-id="57f5b-108">Performance must be considered a first class feature for mixed reality development and not a polish task.</span></span>

<span data-ttu-id="57f5b-109">下面列出了每个目标平台的高性能帧速率值。</span><span class="sxs-lookup"><span data-stu-id="57f5b-109">The performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="57f5b-110">平台</span><span class="sxs-lookup"><span data-stu-id="57f5b-110">Platform</span></span> | <span data-ttu-id="57f5b-111">目标帧速率</span><span class="sxs-lookup"><span data-stu-id="57f5b-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="57f5b-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="57f5b-112">HoloLens</span></span>](hololens-hardware-details.md) | <span data-ttu-id="57f5b-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="57f5b-113">60 FPS</span></span> |
| [<span data-ttu-id="57f5b-114">Windows Mixed Reality 超 Pc</span><span class="sxs-lookup"><span data-stu-id="57f5b-114">Windows Mixed Reality Ultra PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="57f5b-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="57f5b-115">90 FPS</span></span> |
| [<span data-ttu-id="57f5b-116">Windows Mixed Reality Pc</span><span class="sxs-lookup"><span data-stu-id="57f5b-116">Windows Mixed Reality PCs</span></span>](immersive-headset-hardware-details.md) | <span data-ttu-id="57f5b-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="57f5b-117">60 FPS</span></span> |

<span data-ttu-id="57f5b-118">下面的框架概述了命中目标帧速率的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="57f5b-118">The framework below outlines best practices for hitting target frame rates.</span></span> <span data-ttu-id="57f5b-119">如果在 Unity 中进行开发，则请考虑阅读有关[unity 的性能建议一文](performance-recommendations-for-unity.md)，了解在 unity 环境中测量和提高帧率的技巧。</span><span class="sxs-lookup"><span data-stu-id="57f5b-119">If developing in Unity, consider reading the [performance recommendations for Unity article](performance-recommendations-for-unity.md) for tips on measuring and improving framerate in the Unity environment.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="57f5b-120">了解性能瓶颈</span><span class="sxs-lookup"><span data-stu-id="57f5b-120">Understanding performance bottlenecks</span></span>

<span data-ttu-id="57f5b-121">如果你的应用程序具有绩效不佳的帧速率，则第一步是分析并了解应用程序的计算工作量。</span><span class="sxs-lookup"><span data-stu-id="57f5b-121">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="57f5b-122">有两个主要处理器负责呈现场景： CPU 和 GPU。</span><span class="sxs-lookup"><span data-stu-id="57f5b-122">There are two primary processors responsible for the work to render your scene: the CPU and the GPU.</span></span> <span data-ttu-id="57f5b-123">其中每个都处理混合现实应用的不同方面。</span><span class="sxs-lookup"><span data-stu-id="57f5b-123">Each of these handle different aspects of your Mixed Reality app.</span></span> <span data-ttu-id="57f5b-124">有三个关键地方可能出现瓶颈：</span><span class="sxs-lookup"><span data-stu-id="57f5b-124">There are three key places where bottlenecks may occur:</span></span> 

1. <span data-ttu-id="57f5b-125">**应用线程-CPU** -此线程负责应用逻辑。</span><span class="sxs-lookup"><span data-stu-id="57f5b-125">**App Thread - CPU** - This thread is responsible for your app logic.</span></span> <span data-ttu-id="57f5b-126">这包括处理输入、动画、物理学和其他应用逻辑。</span><span class="sxs-lookup"><span data-stu-id="57f5b-126">This includes processing input, animations, physics, and other app logic.</span></span>
2. <span data-ttu-id="57f5b-127">**将线程 CPU 呈现为 gpu** -此线程负责将绘图调用提交到 gpu。</span><span class="sxs-lookup"><span data-stu-id="57f5b-127">**Render Thread - CPU to GPU** - This thread is responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="57f5b-128">当应用程序想要呈现某个对象（如多维数据集或模型）时，此线程会将请求发送到 GPU 以执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="57f5b-128">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU to perform these operations.</span></span>
3. <span data-ttu-id="57f5b-129">**GPU** -此处理器最常见地处理应用程序的图形管道，以将3d 数据（模型、纹理等）转换为像素。</span><span class="sxs-lookup"><span data-stu-id="57f5b-129">**GPU** - This processor most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, etc.) into pixels.</span></span> <span data-ttu-id="57f5b-130">它最终会生成一个要提交到设备屏幕的二维图像。</span><span class="sxs-lookup"><span data-stu-id="57f5b-130">It ultimately produces a 2D image to submit to your device's screen.</span></span>

![帧的生存期](images/lifetime-of-a-frame.png)

<span data-ttu-id="57f5b-132">通常情况下，HoloLens 应用程序将被绑定到 GPU，但并不总是如此。</span><span class="sxs-lookup"><span data-stu-id="57f5b-132">Generally, HoloLens applications will be GPU bound, but not always.</span></span> <span data-ttu-id="57f5b-133">使用下面的工具和技术来了解你的特定应用程序的瓶颈所在。</span><span class="sxs-lookup"><span data-stu-id="57f5b-133">Use the tools and techniques below to understand where your particular app is bottlenecked.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="57f5b-134">如何分析应用程序</span><span class="sxs-lookup"><span data-stu-id="57f5b-134">How to analyze your application</span></span>

<span data-ttu-id="57f5b-135">有许多工具可让你了解混合现实应用程序的性能配置文件。</span><span class="sxs-lookup"><span data-stu-id="57f5b-135">There are many tools that allow you to understand the performance profile of your mixed reality application.</span></span> <span data-ttu-id="57f5b-136">这样，你就可以找到存在瓶颈的位置和原因，以便解决问题。</span><span class="sxs-lookup"><span data-stu-id="57f5b-136">These will enable you to find where and why you have bottlenecks, so you can address them.</span></span>

<span data-ttu-id="57f5b-137">下面是一些常用工具，用于获取应用程序的深入分析信息：</span><span class="sxs-lookup"><span data-stu-id="57f5b-137">Below are some common tools to gain deep profiling information for your application:</span></span>
- [<span data-ttu-id="57f5b-138">Intel 图形性能分析器</span><span class="sxs-lookup"><span data-stu-id="57f5b-138">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="57f5b-139">Visual Studio 图形调试器</span><span class="sxs-lookup"><span data-stu-id="57f5b-139">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [<span data-ttu-id="57f5b-140">Unity 探查器</span><span class="sxs-lookup"><span data-stu-id="57f5b-140">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="57f5b-141">Unity 框架调试器</span><span class="sxs-lookup"><span data-stu-id="57f5b-141">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="57f5b-142">如何在任何环境中进行分析</span><span class="sxs-lookup"><span data-stu-id="57f5b-142">How to profile in any environment</span></span>

<span data-ttu-id="57f5b-143">确定你的应用程序中是否有 GPU 界限或 CPU 限制的一种方法是降低呈现器目标输出的分辨率。</span><span class="sxs-lookup"><span data-stu-id="57f5b-143">One way to determine if you are GPU bound or CPU bound in your application is to decrease the resolution of the render target output.</span></span> <span data-ttu-id="57f5b-144">通过减少要计算的像素数，这将减少 GPU 负载。</span><span class="sxs-lookup"><span data-stu-id="57f5b-144">By reducing the number of pixels to calculate, this will reduce your GPU load.</span></span> <span data-ttu-id="57f5b-145">设备将呈现为一个较小的纹理，然后显示一个示例，显示最终图像。</span><span class="sxs-lookup"><span data-stu-id="57f5b-145">The device will render to a smaller texture, then up-sample to display your final image.</span></span>

<span data-ttu-id="57f5b-146">减少呈现分辨率后，如果：</span><span class="sxs-lookup"><span data-stu-id="57f5b-146">After decreasing rendering resolution, if:</span></span>
1) <span data-ttu-id="57f5b-147">应用程序的帧速率**增加**，则可能会**绑定 GPU**</span><span class="sxs-lookup"><span data-stu-id="57f5b-147">Application framerate **increases**, then you are likely **GPU Bound**</span></span>
1) <span data-ttu-id="57f5b-148">应用程序的帧速率**未更改**，则可能会**绑定 CPU**</span><span class="sxs-lookup"><span data-stu-id="57f5b-148">Application framerate **unchanged**, then you are likely **CPU Bound**</span></span>

>[!NOTE]
><span data-ttu-id="57f5b-149">Unity 提供了在运行时通过 *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性轻松修改应用程序的呈现目标解析的能力。</span><span class="sxs-lookup"><span data-stu-id="57f5b-149">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="57f5b-150">设备上提供的最终映像具有固定的分辨率。</span><span class="sxs-lookup"><span data-stu-id="57f5b-150">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="57f5b-151">平台将采样低分辨率输出，以生成更高分辨率的图像，以便在显示时呈现。</span><span class="sxs-lookup"><span data-stu-id="57f5b-151">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="57f5b-152">如何改进应用程序</span><span class="sxs-lookup"><span data-stu-id="57f5b-152">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="57f5b-153">CPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="57f5b-153">CPU performance recommendations</span></span>

<span data-ttu-id="57f5b-154">通常，在 CPU 上混合现实应用程序中的大部分工作都涉及到执行场景的 "模拟" 和处理应用程序逻辑。</span><span class="sxs-lookup"><span data-stu-id="57f5b-154">Generally, most work in a mixed reality application on the CPU involves performing the "simulation" of the scene and processing your application logic.</span></span> <span data-ttu-id="57f5b-155">以下区域通常针对优化：</span><span class="sxs-lookup"><span data-stu-id="57f5b-155">The following areas are usually targeted for optimization:</span></span>

- <span data-ttu-id="57f5b-156">“动画”</span><span class="sxs-lookup"><span data-stu-id="57f5b-156">Animations</span></span>
- <span data-ttu-id="57f5b-157">物理</span><span class="sxs-lookup"><span data-stu-id="57f5b-157">Physics</span></span>
- <span data-ttu-id="57f5b-158">内存分配</span><span class="sxs-lookup"><span data-stu-id="57f5b-158">Memory allocations</span></span>
- <span data-ttu-id="57f5b-159">复杂算法（即</span><span class="sxs-lookup"><span data-stu-id="57f5b-159">Complex algorithms (i.e</span></span> <span data-ttu-id="57f5b-160">反向运动，路径查找）</span><span class="sxs-lookup"><span data-stu-id="57f5b-160">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="57f5b-161">GPU 性能建议</span><span class="sxs-lookup"><span data-stu-id="57f5b-161">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="57f5b-162">了解带宽与填充速率</span><span class="sxs-lookup"><span data-stu-id="57f5b-162">Understanding bandwidth vs. fill rate</span></span>
<span data-ttu-id="57f5b-163">当在 GPU 上呈现帧时，应用程序通常按内存带宽或填充速率进行绑定。</span><span class="sxs-lookup"><span data-stu-id="57f5b-163">When rendering a frame on the GPU, an application is generally either bound by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="57f5b-164">**内存带宽**是 GPU 可以从内存执行的读取和写入速率</span><span class="sxs-lookup"><span data-stu-id="57f5b-164">**Memory bandwidth** is the rate of reads and writes the GPU can perform from memory</span></span>
    - <span data-ttu-id="57f5b-165">若要确定带宽限制，请降低纹理质量并检查帧速率是否已提高。</span><span class="sxs-lookup"><span data-stu-id="57f5b-165">To identify bandwidth limitations, reduce texture quality and check if the framerate has improved.</span></span>
    - <span data-ttu-id="57f5b-166">在 Unity 中，这可以通过在 "**编辑** > **项目" 设置**中更改**纹理质量**来实现 >  **[质量设置](https://docs.unity3d.com/Manual/class-QualitySettings.html)** 。</span><span class="sxs-lookup"><span data-stu-id="57f5b-166">In Unity, this can be done by changing **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="57f5b-167">**填充速率**是指每秒可以通过 GPU 绘制的像素。</span><span class="sxs-lookup"><span data-stu-id="57f5b-167">**Fill rate** refers to the pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="57f5b-168">若要确定填充速率限制，请减小显示分辨率，并检查是否已提高速度。</span><span class="sxs-lookup"><span data-stu-id="57f5b-168">To identify fill rate limitations, decrease the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="57f5b-169">在 Unity 中，可以通过 *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* 属性完成此操作</span><span class="sxs-lookup"><span data-stu-id="57f5b-169">In Unity, this can be done via the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="57f5b-170">内存带宽一般涉及优化到以下任一操作：</span><span class="sxs-lookup"><span data-stu-id="57f5b-170">Memory bandwidth generally involves optimizations to either:</span></span>
1) <span data-ttu-id="57f5b-171">降低纹理分辨率</span><span class="sxs-lookup"><span data-stu-id="57f5b-171">Decrease texture resolutions</span></span>
2) <span data-ttu-id="57f5b-172">利用更少纹理（法线、镜面等）</span><span class="sxs-lookup"><span data-stu-id="57f5b-172">Utilize fewer textures (normals, specular, etc.)</span></span>

<span data-ttu-id="57f5b-173">填充速率侧重于减少需要针对最终呈现的像素进行计算的操作的数量。</span><span class="sxs-lookup"><span data-stu-id="57f5b-173">Fill rate is focused on reducing the number of operations that need to be computed for a final rendered pixel.</span></span> <span data-ttu-id="57f5b-174">这包括减少：</span><span class="sxs-lookup"><span data-stu-id="57f5b-174">This includes reducing:</span></span>
1) <span data-ttu-id="57f5b-175">要呈现/处理的对象数</span><span class="sxs-lookup"><span data-stu-id="57f5b-175">Number of objects to render/process</span></span>
2) <span data-ttu-id="57f5b-176">每个着色器的操作数</span><span class="sxs-lookup"><span data-stu-id="57f5b-176">Number of operations per shader</span></span>
3) <span data-ttu-id="57f5b-177">到最终结果的 GPU 阶段数（几何着色器、后处理效果等）</span><span class="sxs-lookup"><span data-stu-id="57f5b-177">Number of GPU stages to final result (geometry shaders, post-processing effects, etc.)</span></span>
4) <span data-ttu-id="57f5b-178">要呈现的像素数（显示分辨率）</span><span class="sxs-lookup"><span data-stu-id="57f5b-178">Number of pixels to render (display resolution)</span></span>

#### <a name="reduce-polygon-count"></a><span data-ttu-id="57f5b-179">减少多边形计数</span><span class="sxs-lookup"><span data-stu-id="57f5b-179">Reduce polygon count</span></span>
<span data-ttu-id="57f5b-180">较大的多边形计数会导致更多的 GPU 操作;减少场景中的多边形数量将减少渲染时间。</span><span class="sxs-lookup"><span data-stu-id="57f5b-180">Higher polygon counts result in more operations for the GPU; reducing the number of polygons in your scene will reduce the render time.</span></span> <span data-ttu-id="57f5b-181">对于可能开销较大的几何图形，还涉及到其他因素，而多边形计数是确定要呈现场景的成本最高的指标。</span><span class="sxs-lookup"><span data-stu-id="57f5b-181">There are other factors involved in shading the geometry that can be expensive, but polygon count is the simplest metric to determine how expensive a scene will be to render.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="57f5b-182">限制过度绘制</span><span class="sxs-lookup"><span data-stu-id="57f5b-182">Limit overdraw</span></span>

<span data-ttu-id="57f5b-183">当显示多个对象但在屏幕上未显示过度绘制时，因为 occluding 对象隐藏了多个对象。</span><span class="sxs-lookup"><span data-stu-id="57f5b-183">High overdraw occurs when multiple objects are rendered but not shown on screen as they are hidden by an occluding object.</span></span> <span data-ttu-id="57f5b-184">想象一下，看看有对象后面的墙。</span><span class="sxs-lookup"><span data-stu-id="57f5b-184">Imagine looking at a wall that has objects behind it.</span></span> <span data-ttu-id="57f5b-185">所有几何都将处理以便呈现，但只需呈现不透明的墙壁。</span><span class="sxs-lookup"><span data-stu-id="57f5b-185">All of the geometry would be processed for rendering, but only the opaque wall needs to be rendered.</span></span> <span data-ttu-id="57f5b-186">这会导致不必要的操作。</span><span class="sxs-lookup"><span data-stu-id="57f5b-186">This results in unnecessary operations.</span></span>

#### <a name="shaders"></a><span data-ttu-id="57f5b-187">着色器</span><span class="sxs-lookup"><span data-stu-id="57f5b-187">Shaders</span></span>

<span data-ttu-id="57f5b-188">着色器是在 GPU 上运行的小程序，可执行以下两个重要步骤：</span><span class="sxs-lookup"><span data-stu-id="57f5b-188">Shaders are small programs that run on the GPU and perform two important steps in rendering:</span></span>
1) <span data-ttu-id="57f5b-189">确定应绘制的顶点以及它们在屏幕空间中的位置（顶点着色器）</span><span class="sxs-lookup"><span data-stu-id="57f5b-189">Determining which vertices should be drawn and where they are in screen space (the Vertex shader)</span></span>
    - <span data-ttu-id="57f5b-190">对于每个网格，顶点着色器通常按顶点执行。</span><span class="sxs-lookup"><span data-stu-id="57f5b-190">The Vertex shader is generally executed per vertex for every mesh.</span></span>
2) <span data-ttu-id="57f5b-191">确定每个像素的颜色（像素着色器）</span><span class="sxs-lookup"><span data-stu-id="57f5b-191">Determining the color of each pixel (the Pixel shader)</span></span>
    - <span data-ttu-id="57f5b-192">像素着色器将由几何图形呈现的每个像素执行到所呈现的纹理。</span><span class="sxs-lookup"><span data-stu-id="57f5b-192">The Pixel shader is executed per pixel rendered by the geometry to the texture being rendered to.</span></span>

<span data-ttu-id="57f5b-193">通常，着色器会执行许多转换和照明计算。</span><span class="sxs-lookup"><span data-stu-id="57f5b-193">Typically, shaders perform many transformations and lighting calculations.</span></span> <span data-ttu-id="57f5b-194">尽管复杂的照明模型、阴影和其他操作可能会产生极好的结果，但它们也具有价格。</span><span class="sxs-lookup"><span data-stu-id="57f5b-194">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="57f5b-195">减少着色器中计算的操作数可以极大地减少 GPU 每帧所需的工作量。</span><span class="sxs-lookup"><span data-stu-id="57f5b-195">Reducing the number of operations computed in shaders can greatly reduce the work needed for the GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="57f5b-196">着色器编码建议</span><span class="sxs-lookup"><span data-stu-id="57f5b-196">Shader coding recommendations</span></span>

- <span data-ttu-id="57f5b-197">尽可能使用双线性筛选</span><span class="sxs-lookup"><span data-stu-id="57f5b-197">Use bilinear filtering, whenever possible</span></span>
- <span data-ttu-id="57f5b-198">重新排列表达式以使用 MAD 内部函数，以便同时执行相乘和 add 操作</span><span class="sxs-lookup"><span data-stu-id="57f5b-198">Rearrange expressions to use MAD intrinsics in order to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="57f5b-199">在 CPU 上尽可能 Precalculate，并将其作为常量传递给材料</span><span class="sxs-lookup"><span data-stu-id="57f5b-199">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="57f5b-200">**优选从像素着色器移动到顶点着色器的操作**</span><span class="sxs-lookup"><span data-stu-id="57f5b-200">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="57f5b-201">通常，顶点的数目要小于像素数（720p 为921600像素，1080p 为2073600像素，等等）。</span><span class="sxs-lookup"><span data-stu-id="57f5b-201">Generally, the number of vertices is much smaller than the number of pixels (720p is 921,600 pixels, 1080p is 2,073,600 pixels, etc.)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="57f5b-202">删除 GPU 阶段</span><span class="sxs-lookup"><span data-stu-id="57f5b-202">Remove GPU stages</span></span>
<span data-ttu-id="57f5b-203">后期处理效果可能会非常昂贵，并会提高应用程序的填充率。</span><span class="sxs-lookup"><span data-stu-id="57f5b-203">Post-processing effects can be very expensive and increase the fill rate of your application.</span></span> <span data-ttu-id="57f5b-204">这包括诸如 MSAA 这样的抗锯齿技术。</span><span class="sxs-lookup"><span data-stu-id="57f5b-204">This includes anti-aliasing techniques such as MSAA.</span></span> <span data-ttu-id="57f5b-205">在 HoloLens 上，建议完全避免使用这些技术以及其他着色器阶段，如几何、球面和计算着色器。</span><span class="sxs-lookup"><span data-stu-id="57f5b-205">On HoloLens, it is recommended to avoid these techniques entirely, as well as additional shader stages such as geometry, hull, and compute shaders.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="57f5b-206">内存建议</span><span class="sxs-lookup"><span data-stu-id="57f5b-206">Memory recommendations</span></span>
<span data-ttu-id="57f5b-207">过多的内存分配和释放操作可能导致性能不一致、冻结帧以及其他不利行为。</span><span class="sxs-lookup"><span data-stu-id="57f5b-207">Excessive memory allocation and deallocation operations can result in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="57f5b-208">在 Unity 中进行开发时了解内存的注意事项尤其重要，因为内存管理由垃圾回收器控制。</span><span class="sxs-lookup"><span data-stu-id="57f5b-208">It is especially important to understand memory considerations when developing in Unity, since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="57f5b-209">对象池</span><span class="sxs-lookup"><span data-stu-id="57f5b-209">Object pooling</span></span>

<span data-ttu-id="57f5b-210">对象池是一种常用技术，可降低对象的连续分配和释放的成本。</span><span class="sxs-lookup"><span data-stu-id="57f5b-210">Object pooling is a popular technique to reduce the cost of continuous allocations and deallocations of objects.</span></span> <span data-ttu-id="57f5b-211">这是通过以下方式实现的：分配一个较大的相同对象池，并重新使用此池中的非活动可用实例，而不是随着时间推移不断地生成和销毁对象。</span><span class="sxs-lookup"><span data-stu-id="57f5b-211">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="57f5b-212">对象池非常适合在应用过程中具有可变生存期的重复使用的组件。</span><span class="sxs-lookup"><span data-stu-id="57f5b-212">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="57f5b-213">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57f5b-213">See also</span></span>
- [<span data-ttu-id="57f5b-214">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="57f5b-214">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
- [<span data-ttu-id="57f5b-215">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="57f5b-215">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
