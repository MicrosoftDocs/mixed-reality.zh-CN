---
title: 应用程序质量准则
description: 本文档介绍顶部因素影响混合的现实应用程序的质量。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 应用程序质量标准，混合现实，混合现实应用
ms.openlocfilehash: 756bc148f290aa3406c9ac8bb7003d463c62772c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974741"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="f197f-104">应用程序质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-104">App quality criteria</span></span>

<span data-ttu-id="f197f-105">本文档介绍顶部因素影响混合的现实应用程序的质量。</span><span class="sxs-lookup"><span data-stu-id="f197f-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="f197f-106">对于每个因素提供了以下信息</span><span class="sxs-lookup"><span data-stu-id="f197f-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="f197f-107">概述-的质量因子以及为何它很重要的简短说明。</span><span class="sxs-lookup"><span data-stu-id="f197f-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="f197f-108">设备的影响-哪种类型的窗口混合现实设备会受到影响。</span><span class="sxs-lookup"><span data-stu-id="f197f-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="f197f-109">质量标准 – 如何评估的质量因子。</span><span class="sxs-lookup"><span data-stu-id="f197f-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="f197f-110">如何测量 – 度量值 （或体验） 问题的方法。</span><span class="sxs-lookup"><span data-stu-id="f197f-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="f197f-111">建议 – 摘要的某些方法来提供更好的用户体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="f197f-112">资源 – 相关的开发人员和设计资源都有可用于创建更好的应用体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="f197f-113">帧速率</span><span class="sxs-lookup"><span data-stu-id="f197f-113">Frame rate</span></span>

<span data-ttu-id="f197f-114">帧速率是全息图稳定性和用户舒适的第一个支柱。</span><span class="sxs-lookup"><span data-stu-id="f197f-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="f197f-115">帧速率低于建议的目标可能会导致全息出现抖动，造成负面影响的体验 believability 并可能会引起眼睛疲劳。</span><span class="sxs-lookup"><span data-stu-id="f197f-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="f197f-116">Windows Mixed Reality 沉浸式耳机的体验的目标帧速率将 60 Hz 或你想要支持具体取决于哪些 Windows 混合现实兼容 Pc 90 Hz。</span><span class="sxs-lookup"><span data-stu-id="f197f-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="f197f-117">对于 HoloLens 目标帧速率是 60 Hz。</span><span class="sxs-lookup"><span data-stu-id="f197f-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-118">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-118">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-120"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-121">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-121">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f197f-122">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-122">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-123">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-123">Quality criteria</span></span>

|  <span data-ttu-id="f197f-124">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-124">Best</span></span>  |  <span data-ttu-id="f197f-125">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-125">Meets</span></span> |  <span data-ttu-id="f197f-126">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="f197f-127">应用一致地满足每个目标设备的第二个 (FPS) 目标帧：HoloLens; 上的 60 fps超高电脑; 上 90 fps和 60 fps 主流的 Pc 上。</span><span class="sxs-lookup"><span data-stu-id="f197f-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="f197f-128">该应用程序有间歇性帧删除不妨碍核心体验中;或每秒帧数一致地低于所需目标，但不会妨碍应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="f197f-129">应用程序在遇到平均每隔十秒或更少的帧速率下降。</span><span class="sxs-lookup"><span data-stu-id="f197f-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="f197f-130">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-130">How to measure</span></span>

* <span data-ttu-id="f197f-131">实时帧速率图通过提供由[Windows Device Portal](using-the-windows-device-portal.md#system-performance)下"系统性能"。</span><span class="sxs-lookup"><span data-stu-id="f197f-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="f197f-132">对于开发调试，将添加到应用的帧速率诊断计数器。</span><span class="sxs-lookup"><span data-stu-id="f197f-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="f197f-133">示例计数器，请参阅资源。</span><span class="sxs-lookup"><span data-stu-id="f197f-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="f197f-134">移动您从左到右运行应用时，可以在设备中遇到帧速率下降。</span><span class="sxs-lookup"><span data-stu-id="f197f-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="f197f-135">如果全息图显示了意外的抖动移动，然后较低的帧速率或稳定性平面是可能的原因。</span><span class="sxs-lookup"><span data-stu-id="f197f-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-136">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-136">Recommendations</span></span>

* <span data-ttu-id="f197f-137">开发工作的开头添加一个帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="f197f-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="f197f-138">应计算并相应地解决的性能 bug 会导致帧速率下降的更改。</span><span class="sxs-lookup"><span data-stu-id="f197f-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-139">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f197f-140">文档</span><span class="sxs-lookup"><span data-stu-id="f197f-140">Documentation</span></span>

* [<span data-ttu-id="f197f-141">混合现实的了解性能</span><span class="sxs-lookup"><span data-stu-id="f197f-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="f197f-142">全息图稳定性和帧速率</span><span class="sxs-lookup"><span data-stu-id="f197f-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="f197f-143">资产的性能预算</span><span class="sxs-lookup"><span data-stu-id="f197f-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="f197f-144">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="f197f-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f197f-145">工具和教程</span><span class="sxs-lookup"><span data-stu-id="f197f-145">Tools and tutorials</span></span>

* [<span data-ttu-id="f197f-146">MRToolkit，每秒帧数计数器显示</span><span class="sxs-lookup"><span data-stu-id="f197f-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="f197f-147">MRToolkit，着色器</span><span class="sxs-lookup"><span data-stu-id="f197f-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="f197f-148">外部引用</span><span class="sxs-lookup"><span data-stu-id="f197f-148">External references</span></span>

* [<span data-ttu-id="f197f-149">Unity 中，优化移动应用程序</span><span class="sxs-lookup"><span data-stu-id="f197f-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="f197f-150">全息图稳定性</span><span class="sxs-lookup"><span data-stu-id="f197f-150">Hologram stability</span></span>

<span data-ttu-id="f197f-151">稳定全息将提高可用性和 believability 您的应用程序，并创建用户提供更舒适的查看体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="f197f-152">全息图稳定性的质量是很好的应用程序开发和设备的功能，若要了解 （跟踪） 的结果及其环境。</span><span class="sxs-lookup"><span data-stu-id="f197f-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="f197f-153">稳定性，首先必须按时帧速率时，其他因素可以影响稳定性包括：</span><span class="sxs-lookup"><span data-stu-id="f197f-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="f197f-154">稳定平面的使用</span><span class="sxs-lookup"><span data-stu-id="f197f-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="f197f-155">空间的定位点的距离</span><span class="sxs-lookup"><span data-stu-id="f197f-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="f197f-156">跟踪</span><span class="sxs-lookup"><span data-stu-id="f197f-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-157">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-157">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-158"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-158"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-159"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-160">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-160">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-161">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-161">Quality criteria</span></span>

|  <span data-ttu-id="f197f-162">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-162">Best</span></span>  |  <span data-ttu-id="f197f-163">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-163">Meets</span></span> |  <span data-ttu-id="f197f-164">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f197f-165">全息总是出现稳定。</span><span class="sxs-lookup"><span data-stu-id="f197f-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="f197f-166">辅助内容表现出意外的移动;或意外的移动不会影响总体应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="f197f-167">在帧中的主要内容表现出意外的移动。</span><span class="sxs-lookup"><span data-stu-id="f197f-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="f197f-168">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-168">How to measure</span></span>

<span data-ttu-id="f197f-169">尽管戴上设备并查看体验：</span><span class="sxs-lookup"><span data-stu-id="f197f-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="f197f-170">移动您从左到右，如果全息显示意外的移动然后较低的帧速率或到焦平面稳定性平面的不正确的对齐方式是可能的原因。</span><span class="sxs-lookup"><span data-stu-id="f197f-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="f197f-171">移动全息和环境中，查找行为如泳道和 jumpiness。</span><span class="sxs-lookup"><span data-stu-id="f197f-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="f197f-172">导致这种类型的运动的原因可能不是跟踪对空间定位点的环境或距离的设备。</span><span class="sxs-lookup"><span data-stu-id="f197f-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="f197f-173">如果大型或多个全息框架中，观察在各种深入探索全息图行为，而移动头位置从左到右，如果不显示这是有可能引起的稳定平面。</span><span class="sxs-lookup"><span data-stu-id="f197f-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="f197f-174">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-174">Recomendations</span></span>

* <span data-ttu-id="f197f-175">开发工作的开头添加帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="f197f-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="f197f-176">使用稳定平面。</span><span class="sxs-lookup"><span data-stu-id="f197f-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="f197f-177">始终呈现定位的全息内 3 米的其定位点。</span><span class="sxs-lookup"><span data-stu-id="f197f-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="f197f-178">请确保环境已设置为正确的跟踪。</span><span class="sxs-lookup"><span data-stu-id="f197f-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="f197f-179">设计你的体验，以避免全息在范围内的各个重要深度级别。</span><span class="sxs-lookup"><span data-stu-id="f197f-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-180">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f197f-181">文档</span><span class="sxs-lookup"><span data-stu-id="f197f-181">Documentation</span></span>

* [<span data-ttu-id="f197f-182">全息图稳定性和帧速率</span><span class="sxs-lookup"><span data-stu-id="f197f-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="f197f-183">案例研究中，使用稳定平面</span><span class="sxs-lookup"><span data-stu-id="f197f-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="f197f-184">混合现实的了解性能</span><span class="sxs-lookup"><span data-stu-id="f197f-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="f197f-185">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="f197f-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="f197f-186">空间定位点</span><span class="sxs-lookup"><span data-stu-id="f197f-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="f197f-187">处理跟踪错误</span><span class="sxs-lookup"><span data-stu-id="f197f-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="f197f-188">固定参考框架</span><span class="sxs-lookup"><span data-stu-id="f197f-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f197f-189">工具和教程</span><span class="sxs-lookup"><span data-stu-id="f197f-189">Tools and tutorials</span></span>

* [<span data-ttu-id="f197f-190">MR 配套工具包，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="f197f-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="f197f-191">全息真实的图面上的位置</span><span class="sxs-lookup"><span data-stu-id="f197f-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="f197f-192">与物理对象 （如果要相对于另一个放置） 全息 misalignments 是明确表示的非联合，全息和实际。</span><span class="sxs-lookup"><span data-stu-id="f197f-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="f197f-193">位置的准确性应相对于的方案; 需要例如，常规的图面上放置可使用空间的映射，但更准确地放置将需要一些使用标记和校准。</span><span class="sxs-lookup"><span data-stu-id="f197f-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-194">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-194">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-195"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-195"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-196"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-197">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-197">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-198">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-198">Quality criteria</span></span>

|  <span data-ttu-id="f197f-199">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-199">Best</span></span>  |  <span data-ttu-id="f197f-200">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-200">Meets</span></span> |  <span data-ttu-id="f197f-201">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="f197f-202">全息对齐到英寸范围通常以厘米为单位的面。</span><span class="sxs-lookup"><span data-stu-id="f197f-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="f197f-203">如果需要更精确，应用应为所需的应用规范内的协作提供一种有效方式。</span><span class="sxs-lookup"><span data-stu-id="f197f-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="f197f-204">NA</span><span class="sxs-lookup"><span data-stu-id="f197f-204">NA</span></span> | <span data-ttu-id="f197f-205">全息出现重大的图面上的平面或使其不显示浮动离开面与物理目标对象未对齐。</span><span class="sxs-lookup"><span data-stu-id="f197f-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="f197f-206">如果需要准确性，全息应满足方案的邻近性规范。</span><span class="sxs-lookup"><span data-stu-id="f197f-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f197f-207">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-207">How to measure</span></span>

* <span data-ttu-id="f197f-208">空间代码图放置的全息不应出现显著浮动的上方或下方的图面。</span><span class="sxs-lookup"><span data-stu-id="f197f-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="f197f-209">需要准确放置全息应具有某种形式的标记和校准系统是准确的方案的要求。</span><span class="sxs-lookup"><span data-stu-id="f197f-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-210">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-210">Recommendations</span></span>

* <span data-ttu-id="f197f-211">空间映射是适用于精度不需要时图面上放置对象。</span><span class="sxs-lookup"><span data-stu-id="f197f-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="f197f-212">最佳的精度，使用标记或海报设置全息和 Xbox 控制器 （或某些手动对齐机制） 的最终校准。</span><span class="sxs-lookup"><span data-stu-id="f197f-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="f197f-213">请考虑将超大型全息分成逻辑部分以及对齐到图面每个部分。</span><span class="sxs-lookup"><span data-stu-id="f197f-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="f197f-214">未正确设定 interpupilary 的距离 (IPD) 还可以影响全息图对齐方式。</span><span class="sxs-lookup"><span data-stu-id="f197f-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="f197f-215">始终配置为用户的 IPD HoloLens。</span><span class="sxs-lookup"><span data-stu-id="f197f-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-216">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f197f-217">文档</span><span class="sxs-lookup"><span data-stu-id="f197f-217">Documentation</span></span>

* [<span data-ttu-id="f197f-218">空间映射放置</span><span class="sxs-lookup"><span data-stu-id="f197f-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="f197f-219">扫描进程的房间</span><span class="sxs-lookup"><span data-stu-id="f197f-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="f197f-220">空间的定位点的最佳做法</span><span class="sxs-lookup"><span data-stu-id="f197f-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="f197f-221">处理跟踪错误</span><span class="sxs-lookup"><span data-stu-id="f197f-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="f197f-222">Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="f197f-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="f197f-223">Vuforia 开发概述</span><span class="sxs-lookup"><span data-stu-id="f197f-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f197f-224">工具和教程</span><span class="sxs-lookup"><span data-stu-id="f197f-224">Tools and tutorials</span></span>

* [<span data-ttu-id="f197f-225">MR 空间 230：空间映射</span><span class="sxs-lookup"><span data-stu-id="f197f-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="f197f-226">MR 工具包，空间映射库</span><span class="sxs-lookup"><span data-stu-id="f197f-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="f197f-227">MR 配套工具包，海报校准示例</span><span class="sxs-lookup"><span data-stu-id="f197f-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="f197f-228">MR 配套工具包，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="f197f-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="f197f-229">外部引用</span><span class="sxs-lookup"><span data-stu-id="f197f-229">External references</span></span>

* [<span data-ttu-id="f197f-230">Lowes 案例研究，精度对齐方式</span><span class="sxs-lookup"><span data-stu-id="f197f-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="f197f-231">查看区域的舒适</span><span class="sxs-lookup"><span data-stu-id="f197f-231">Viewing zone of comfort</span></span>

<span data-ttu-id="f197f-232">通过将内容和全息放置在各种深入探索聚合用户的眼睛，其中应用开发人员控制。</span><span class="sxs-lookup"><span data-stu-id="f197f-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="f197f-233">戴上 HoloLens 的用户将始终允许到 2.0 m 来维护清晰的图像因为 HoloLens 显示固定为光学的距离大约 2.0 m 背朝用户。</span><span class="sxs-lookup"><span data-stu-id="f197f-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="f197f-234">不正确的内容深度可能会导致 visual 不适或疲劳。</span><span class="sxs-lookup"><span data-stu-id="f197f-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-235">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-235">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-236"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-236"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-237"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-238">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-238">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-239">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="f197f-240">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="f197f-241">将内容放在 2 分钟。</span><span class="sxs-lookup"><span data-stu-id="f197f-241">Place content at 2m.</span></span></li><li><span data-ttu-id="f197f-242">当聚合和便利设施之间的冲突无法避免全息不能放在 2 分钟，全息图放置的最佳区域为 1.25 m 到 5 分钟。</span><span class="sxs-lookup"><span data-stu-id="f197f-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="f197f-243">设计器应在所有情况下，结构内容鼓励用户交互 1 + 米的位置 （例如调整内容大小和默认的位置参数）。</span><span class="sxs-lookup"><span data-stu-id="f197f-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="f197f-244">具体而言不需要的方案，除非修剪平面应与 fadeout 开始 1 百万的实现。</span><span class="sxs-lookup"><span data-stu-id="f197f-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="f197f-245">在更接近观测到的静止不动全息图需要的情况下，内容不应为 50 cm 比更接近。</span><span class="sxs-lookup"><span data-stu-id="f197f-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="f197f-246">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-246">Meets</span></span></td><td> <span data-ttu-id="f197f-247">内容是在查看和动作的指导，但不正当使用或不使用剪裁平面。</span><span class="sxs-lookup"><span data-stu-id="f197f-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="f197f-248">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-248">Fail</span></span> </td><td> <span data-ttu-id="f197f-249">内容显示太靠近 (通常&lt;1.25 m 或&lt;为静止状态全息需要仔细观察 50 cm。)</span><span class="sxs-lookup"><span data-stu-id="f197f-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="f197f-250">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-250">How to measure</span></span>

* <span data-ttu-id="f197f-251">内容通常应该是 2 分离开，但之间的距离大于 1.25 或关注 5 分钟。</span><span class="sxs-lookup"><span data-stu-id="f197f-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="f197f-252">有几个例外，HoloLens 剪辑呈现距离应与 fadeout 开始 1 百万的内容设置为.85CM。</span><span class="sxs-lookup"><span data-stu-id="f197f-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="f197f-253">方法的内容并记下剪辑平面效果。</span><span class="sxs-lookup"><span data-stu-id="f197f-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="f197f-254">静态内容不应接近 50 cm 消失。</span><span class="sxs-lookup"><span data-stu-id="f197f-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-255">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-255">Recommendations</span></span>

* <span data-ttu-id="f197f-256">设计 2 分钟的最佳观看距离的内容。</span><span class="sxs-lookup"><span data-stu-id="f197f-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="f197f-257">将剪辑呈现距离设置为 85 cm 与 fadeout 开始 1 百万的内容。</span><span class="sxs-lookup"><span data-stu-id="f197f-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="f197f-258">对于需要更接近查看的静态全息，修剪平面应为之间的距离大于 30 的 cm 和 fadeout 应开始在至少 10 个 cm 离开修剪平面。</span><span class="sxs-lookup"><span data-stu-id="f197f-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-259">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-259">Resources</span></span>

* [<span data-ttu-id="f197f-260">呈现距离</span><span class="sxs-lookup"><span data-stu-id="f197f-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="f197f-261">Unity 中的焦点</span><span class="sxs-lookup"><span data-stu-id="f197f-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="f197f-262">用规模进行试验</span><span class="sxs-lookup"><span data-stu-id="f197f-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="f197f-263">文本，建议字体大小</span><span class="sxs-lookup"><span data-stu-id="f197f-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="f197f-264">深度切换</span><span class="sxs-lookup"><span data-stu-id="f197f-264">Depth switching</span></span>

<span data-ttu-id="f197f-265">而不考虑查看区域的舒适的问题，要求用户之间进行切换频繁或快速附近，以及最重要的对象 （包括全息和实际内容） 可能导致 oculomotor 疲劳症和常规不安。</span><span class="sxs-lookup"><span data-stu-id="f197f-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-266">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-266">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-267"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-267"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-268"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-269">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-269">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f197f-270">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-270">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-271">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-271">Quality criteria</span></span>

|  <span data-ttu-id="f197f-272">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-272">Best</span></span>  |  <span data-ttu-id="f197f-273">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-273">Meets</span></span> |  <span data-ttu-id="f197f-274">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f197f-275">有限的或自然深度切换，不会导致用户可以重新 unnaturally 集中。</span><span class="sxs-lookup"><span data-stu-id="f197f-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="f197f-276">突然深度开关，这是核心，设计应用体验或引起意外的实际内容的突然深度开关。</span><span class="sxs-lookup"><span data-stu-id="f197f-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="f197f-277">一致的深度交换机或突然深度切换并不是必需的或应用程序体验的核心。</span><span class="sxs-lookup"><span data-stu-id="f197f-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f197f-278">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-278">How to measure</span></span>

* <span data-ttu-id="f197f-279">如果应用需要用户持续和/或突然更改深度焦点，则切换问题的深度。</span><span class="sxs-lookup"><span data-stu-id="f197f-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-280">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-280">Recommendations</span></span>

* <span data-ttu-id="f197f-281">主内容保持一致的焦平面，并确保稳定平面与匹配焦平面。</span><span class="sxs-lookup"><span data-stu-id="f197f-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="f197f-282">这将缓解 oculomotor 疲劳和意外的 hologram 移动。</span><span class="sxs-lookup"><span data-stu-id="f197f-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-283">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-283">Resources</span></span>

* [<span data-ttu-id="f197f-284">呈现距离</span><span class="sxs-lookup"><span data-stu-id="f197f-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="f197f-285">Unity 中的焦点</span><span class="sxs-lookup"><span data-stu-id="f197f-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="f197f-286">使用的空间声音</span><span class="sxs-lookup"><span data-stu-id="f197f-286">Use of spatial sound</span></span>

<span data-ttu-id="f197f-287">在 Windows Mixed Reality 音频引擎提供的混合的现实体验的语音组件通过模拟 3D 声音使用方向、 距离和环境模拟。</span><span class="sxs-lookup"><span data-stu-id="f197f-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="f197f-288">应用程序中使用空间声音各地用户允许开发人员将声音 convincingly 放在 3 个维空间 （球体）。</span><span class="sxs-lookup"><span data-stu-id="f197f-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="f197f-289">这些听起来然后将看起来像其视为来自用户的环境中混合的现实全息或实际的物理对象。</span><span class="sxs-lookup"><span data-stu-id="f197f-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="f197f-290">声音空间是用于浸入式、 可访问性，并在混合的现实应用程序中的用户体验设计的强大工具。</span><span class="sxs-lookup"><span data-stu-id="f197f-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-291">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-291">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-292"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-292"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-293"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-294">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-294">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f197f-295">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-295">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-296">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-296">Quality criteria</span></span>

|  <span data-ttu-id="f197f-297">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-297">Best</span></span>  |  <span data-ttu-id="f197f-298">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-298">Meets</span></span> |  <span data-ttu-id="f197f-299">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f197f-300">以逻辑方式 spatialized 声音，并 UX 适当地使用声音来帮助进行对象发现和用户反馈。</span><span class="sxs-lookup"><span data-stu-id="f197f-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="f197f-301">声音方案中均自然和相关对象和规范化。</span><span class="sxs-lookup"><span data-stu-id="f197f-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="f197f-302">空间音频未适当地用于 believability 作为方式可帮助用户反馈和可发现性。</span><span class="sxs-lookup"><span data-stu-id="f197f-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="f197f-303">按预期运行，不 spatialized 声音和/或缺少的声音，以帮助用户中的用户体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="f197f-304">或空间音频不视为或未在该方案的设计中使用。</span><span class="sxs-lookup"><span data-stu-id="f197f-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f197f-305">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-305">How to measure</span></span>

* <span data-ttu-id="f197f-306">一般情况下，相关的声音应发出从目标全息 (例如。，虚张声势发出的声音 holographic dog。)</span><span class="sxs-lookup"><span data-stu-id="f197f-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="f197f-307">声音提示应使用整个用户体验，以帮助用户有任何反馈或了解 holographic 框架之外的操作。</span><span class="sxs-lookup"><span data-stu-id="f197f-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-308">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-308">Recommendations</span></span>

* <span data-ttu-id="f197f-309">使用空间的音频以协助对象发现和用户接口。</span><span class="sxs-lookup"><span data-stu-id="f197f-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="f197f-310">实际声音效果更佳合成或非自然的声音。</span><span class="sxs-lookup"><span data-stu-id="f197f-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="f197f-311">应 spatialized 大多数声音。</span><span class="sxs-lookup"><span data-stu-id="f197f-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="f197f-312">避免不可见发射器。</span><span class="sxs-lookup"><span data-stu-id="f197f-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="f197f-313">避免空间屏蔽。</span><span class="sxs-lookup"><span data-stu-id="f197f-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="f197f-314">规范化听上去。</span><span class="sxs-lookup"><span data-stu-id="f197f-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-315">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f197f-316">文档</span><span class="sxs-lookup"><span data-stu-id="f197f-316">Documentation</span></span>

* [<span data-ttu-id="f197f-317">空间音效</span><span class="sxs-lookup"><span data-stu-id="f197f-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="f197f-318">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="f197f-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="f197f-319">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="f197f-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="f197f-320">案例研究，空间 HoloTour 的声音</span><span class="sxs-lookup"><span data-stu-id="f197f-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="f197f-321">案例研究，在 RoboRaid 中使用空间的声音</span><span class="sxs-lookup"><span data-stu-id="f197f-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f197f-322">工具和教程</span><span class="sxs-lookup"><span data-stu-id="f197f-322">Tools and tutorials</span></span>

* [<span data-ttu-id="f197f-323">MR 空间 220：空间音效</span><span class="sxs-lookup"><span data-stu-id="f197f-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="f197f-324">MRToolkit，空间音频</span><span class="sxs-lookup"><span data-stu-id="f197f-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="f197f-325">专注于 holographic 帧 (FOV) 边界</span><span class="sxs-lookup"><span data-stu-id="f197f-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="f197f-326">设计良好的用户体验可以创建和维护的虚拟环境的扩展围绕用户有用的上下文。</span><span class="sxs-lookup"><span data-stu-id="f197f-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="f197f-327">缓解 FOV 边界的效果涉及精心设计的内容的缩放和上下文信息，请使用的空间音频、 指导系统和用户的位置。</span><span class="sxs-lookup"><span data-stu-id="f197f-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="f197f-328">如果正确操作后，用户将可以小于被削弱 FOV 边界的同时轻松应用体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-329">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-329">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-330"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-330"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-331"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-332">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-332">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-333">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-333">Quality criteria</span></span>

|  <span data-ttu-id="f197f-334">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-334">Best</span></span>  |  <span data-ttu-id="f197f-335">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-335">Meets</span></span> |  <span data-ttu-id="f197f-336">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f197f-337">用户永远不会丢失上下文，轻松查看。</span><span class="sxs-lookup"><span data-stu-id="f197f-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="f197f-338">为大型对象提供上下文帮助。</span><span class="sxs-lookup"><span data-stu-id="f197f-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="f197f-339">可发现性和查看指导提供框架之外的对象。</span><span class="sxs-lookup"><span data-stu-id="f197f-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="f197f-340">一般情况下，motion 设计和全息的小数位数是适用于舒适地观看体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="f197f-341">用户永远不会丢失上下文，但额外颈部动作可能需要在有限的环境。</span><span class="sxs-lookup"><span data-stu-id="f197f-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="f197f-342">在有限的环境规模会导致全息中断或者导致某些颈部动作，若要查看全息垂直或水平帧。</span><span class="sxs-lookup"><span data-stu-id="f197f-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="f197f-343">用户可能会丢失上下文和/或一致颈部运动需要查看全息。</span><span class="sxs-lookup"><span data-stu-id="f197f-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="f197f-344">对于大型 holographic 对象，将对象移易被不带任何可发现性的指南或高全息框架之外没有上下文的指南要求若要查看的正则颈部运动。</span><span class="sxs-lookup"><span data-stu-id="f197f-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f197f-345">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-345">How to measure</span></span>

* <span data-ttu-id="f197f-346">丢失或不理解由于进行剪裁边界上下文 （大） 全息图。</span><span class="sxs-lookup"><span data-stu-id="f197f-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="f197f-347">全息的位置很难找到由于缺乏关注主管或快速将移入和移出 holographic 帧的内容。</span><span class="sxs-lookup"><span data-stu-id="f197f-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="f197f-348">方案需要常规和重复向上和向下头动作以完全看到一张全息图，从而导致颈部疲劳。</span><span class="sxs-lookup"><span data-stu-id="f197f-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-349">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-349">Recommendations</span></span>

* <span data-ttu-id="f197f-350">使用的小型对象的符合 FOV，那转换到更大版本的视觉提示与启动体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="f197f-351">使用空间的音频和关注主管帮助 FOV 之外的用户查找内容。</span><span class="sxs-lookup"><span data-stu-id="f197f-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="f197f-352">尽可能多地，避免垂直剪辑 FOV 全息。</span><span class="sxs-lookup"><span data-stu-id="f197f-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="f197f-353">向用户提供最佳的视觉位置的应用程序内指南。</span><span class="sxs-lookup"><span data-stu-id="f197f-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-354">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f197f-355">文档</span><span class="sxs-lookup"><span data-stu-id="f197f-355">Documentation</span></span>

* [<span data-ttu-id="f197f-356">全息帧</span><span class="sxs-lookup"><span data-stu-id="f197f-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="f197f-357">案例研究、 HoloStudio UI 和交互设计经验</span><span class="sxs-lookup"><span data-stu-id="f197f-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="f197f-358">对象和环境的规模</span><span class="sxs-lookup"><span data-stu-id="f197f-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="f197f-359">光标、 可视提示</span><span class="sxs-lookup"><span data-stu-id="f197f-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="f197f-360">外部引用</span><span class="sxs-lookup"><span data-stu-id="f197f-360">External references</span></span>

* [<span data-ttu-id="f197f-361">有关 FOV 的 ado</span><span class="sxs-lookup"><span data-stu-id="f197f-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="f197f-362">用户位置的内容做出响应</span><span class="sxs-lookup"><span data-stu-id="f197f-362">Content reacts to user position</span></span>

<span data-ttu-id="f197f-363">全息应大致"真实"对象执行的相同方法中的用户位置做出反应。</span><span class="sxs-lookup"><span data-stu-id="f197f-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="f197f-364">值得注意的设计注意事项，并且一定不能假定用户的位置的 UI 元素保持静止时适应用户的动作。</span><span class="sxs-lookup"><span data-stu-id="f197f-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="f197f-365">设计的应用程序正确调整到用户的位置将创建更可信的体验，并使其易于使用。</span><span class="sxs-lookup"><span data-stu-id="f197f-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-366">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-366">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-367"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-367"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-368"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-369">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-369">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f197f-370">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-370">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-371">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="f197f-372">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-372">Best</span></span> </td><td> <span data-ttu-id="f197f-373">内容和 UI 适应允许用户与预期的用户移动的范围内的内容自然交互的用户位置。</span><span class="sxs-lookup"><span data-stu-id="f197f-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="f197f-374">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-374">Meets</span></span> </td><td> <span data-ttu-id="f197f-375">UI 可适应用户位置，但可能会阻碍要求用户调整其位置的关键内容的视图。</span><span class="sxs-lookup"><span data-stu-id="f197f-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="f197f-376">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="f197f-377">丢失或在移动导致用户 unnaturally 返回到 （或查找） 控件过程中锁定 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="f197f-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="f197f-378">UI 元素限制主内容的视图。</span><span class="sxs-lookup"><span data-stu-id="f197f-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="f197f-379">用于查看距离和动量，尤其是对于不优化 UI 移动<a href="billboarding-and-tag-along.md">尾随</a>UI 元素。</span><span class="sxs-lookup"><span data-stu-id="f197f-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="f197f-380">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-380">How to measure</span></span>

* <span data-ttu-id="f197f-381">应在此方案的合理范围内完成所有度量值。</span><span class="sxs-lookup"><span data-stu-id="f197f-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="f197f-382">虽然将不同用户移动，请勿尝试欺骗极端用户移动与该应用程序。</span><span class="sxs-lookup"><span data-stu-id="f197f-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="f197f-383">对于 UI 元素相关的控件应该是无论用户移动。</span><span class="sxs-lookup"><span data-stu-id="f197f-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="f197f-384">例如，如果用户是查看并围绕 3D 映射与 zoom 的每个步骤时，缩放控件应随时可供用户而不考虑位置。</span><span class="sxs-lookup"><span data-stu-id="f197f-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-385">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-385">Recommendations</span></span>

* <span data-ttu-id="f197f-386">用户是照相机和它们控制移动。</span><span class="sxs-lookup"><span data-stu-id="f197f-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="f197f-387">让这些驱动器。</span><span class="sxs-lookup"><span data-stu-id="f197f-387">Let them drive.</span></span>
* <span data-ttu-id="f197f-388">请考虑文本公告板和面前系统，否则为将世界锁定或者被遮盖，如果用户已移动。</span><span class="sxs-lookup"><span data-stu-id="f197f-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="f197f-389">使用尾随需要遵循用户，同时仍允许用户查看新增内容在它们的前面的内容。</span><span class="sxs-lookup"><span data-stu-id="f197f-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-390">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f197f-391">文档</span><span class="sxs-lookup"><span data-stu-id="f197f-391">Documentation</span></span>

* [<span data-ttu-id="f197f-392">交互设计</span><span class="sxs-lookup"><span data-stu-id="f197f-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="f197f-393">颜色、 灯光和材料</span><span class="sxs-lookup"><span data-stu-id="f197f-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="f197f-394">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="f197f-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f197f-395">本能交互</span><span class="sxs-lookup"><span data-stu-id="f197f-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f197f-396">自动作和用户 locomotion</span><span class="sxs-lookup"><span data-stu-id="f197f-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f197f-397">工具和教程</span><span class="sxs-lookup"><span data-stu-id="f197f-397">Tools and tutorials</span></span>

* [<span data-ttu-id="f197f-398">MR 输入 210：凝视</span><span class="sxs-lookup"><span data-stu-id="f197f-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="f197f-399">输入的交互清晰度</span><span class="sxs-lookup"><span data-stu-id="f197f-399">Input interaction clarity</span></span>

<span data-ttu-id="f197f-400">输入的交互清楚起见对应用程序的可用性至关重要，包括输入的一致性、 简单性和直接性、 可发现性的交互方法。</span><span class="sxs-lookup"><span data-stu-id="f197f-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="f197f-401">用户应该能够使用而无需重新学习的常见平台范围的交互。</span><span class="sxs-lookup"><span data-stu-id="f197f-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="f197f-402">如果应用具有自定义输入，应清楚地传达并演示了。</span><span class="sxs-lookup"><span data-stu-id="f197f-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-403">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-403">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-404"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-404"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-405"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-406">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-406">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f197f-407">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-407">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-408">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-408">Quality criteria</span></span>

|  <span data-ttu-id="f197f-409">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-409">Best</span></span>  |  <span data-ttu-id="f197f-410">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-410">Meets</span></span> |  <span data-ttu-id="f197f-411">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f197f-412">输入的交互方法是与 Windows Mixed Reality 提供一致[指导](interaction-fundamentals.md)。</span><span class="sxs-lookup"><span data-stu-id="f197f-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="f197f-413">任何自定义的输入不应为冗余的标准输入 （而不是使用标准交互） 和必须清楚地传达并向用户演示。</span><span class="sxs-lookup"><span data-stu-id="f197f-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="f197f-414">类似于最佳，但自定义输入是冗余的标准输入方法。</span><span class="sxs-lookup"><span data-stu-id="f197f-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="f197f-415">用户仍可以实现的目标和通过应用体验的进度。</span><span class="sxs-lookup"><span data-stu-id="f197f-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="f197f-416">难以理解输入的方法或按钮映射。</span><span class="sxs-lookup"><span data-stu-id="f197f-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="f197f-417">输入大量自定义，不支持标准的输入，没有说明，或可能会导致疲劳、 感觉更舒适的问题。</span><span class="sxs-lookup"><span data-stu-id="f197f-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f197f-418">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-418">How to measure</span></span>

* <span data-ttu-id="f197f-419">该应用使用一致[标准输入方法。](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="f197f-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="f197f-420">如果应用具有自定义输入，它是清楚地表达通过：</span><span class="sxs-lookup"><span data-stu-id="f197f-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="f197f-421">首次运行体验</span><span class="sxs-lookup"><span data-stu-id="f197f-421">First-run experience</span></span>
* <span data-ttu-id="f197f-422">介绍性屏幕</span><span class="sxs-lookup"><span data-stu-id="f197f-422">Introductory screens</span></span>
* <span data-ttu-id="f197f-423">工具提示</span><span class="sxs-lookup"><span data-stu-id="f197f-423">Tooltips</span></span>
* <span data-ttu-id="f197f-424">手教练</span><span class="sxs-lookup"><span data-stu-id="f197f-424">Hand coach</span></span>
* <span data-ttu-id="f197f-425">帮助部分</span><span class="sxs-lookup"><span data-stu-id="f197f-425">Help section</span></span>
* <span data-ttu-id="f197f-426">语音朗读</span><span class="sxs-lookup"><span data-stu-id="f197f-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-427">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-427">Recommendations</span></span>

* <span data-ttu-id="f197f-428">使用标准输入的方法只要有可能。</span><span class="sxs-lookup"><span data-stu-id="f197f-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="f197f-429">为非标准的输入方法提供演示、 教程和工具提示。</span><span class="sxs-lookup"><span data-stu-id="f197f-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="f197f-430">使用在整个应用一致的交互模型。</span><span class="sxs-lookup"><span data-stu-id="f197f-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-431">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f197f-432">文档</span><span class="sxs-lookup"><span data-stu-id="f197f-432">Documentation</span></span>

* [<span data-ttu-id="f197f-433">本能交互</span><span class="sxs-lookup"><span data-stu-id="f197f-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f197f-434">种交互的对象</span><span class="sxs-lookup"><span data-stu-id="f197f-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="f197f-435">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="f197f-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="f197f-436">光标</span><span class="sxs-lookup"><span data-stu-id="f197f-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f197f-437">舒适度和的视线移动</span><span class="sxs-lookup"><span data-stu-id="f197f-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="f197f-438">手势</span><span class="sxs-lookup"><span data-stu-id="f197f-438">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="f197f-439">语音输入</span><span class="sxs-lookup"><span data-stu-id="f197f-439">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="f197f-440">语音命令</span><span class="sxs-lookup"><span data-stu-id="f197f-440">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="f197f-441">运动控制器</span><span class="sxs-lookup"><span data-stu-id="f197f-441">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="f197f-442">Unity 的输入移植指南</span><span class="sxs-lookup"><span data-stu-id="f197f-442">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="f197f-443">Unity 中的键盘输入</span><span class="sxs-lookup"><span data-stu-id="f197f-443">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="f197f-444">Unity 中的凝视</span><span class="sxs-lookup"><span data-stu-id="f197f-444">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="f197f-445">Unity 中的手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="f197f-445">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="f197f-446">Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="f197f-446">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="f197f-447">DirectX 中的键盘、鼠标和控制器输入</span><span class="sxs-lookup"><span data-stu-id="f197f-447">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="f197f-448">DirectX 中的头部和眼部凝视</span><span class="sxs-lookup"><span data-stu-id="f197f-448">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="f197f-449">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="f197f-449">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="f197f-450">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="f197f-450">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f197f-451">工具和教程</span><span class="sxs-lookup"><span data-stu-id="f197f-451">Tools and tutorials</span></span>

* [<span data-ttu-id="f197f-452">案例研究：追求更多个人计算</span><span class="sxs-lookup"><span data-stu-id="f197f-452">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="f197f-453">强制转换研究：HoloStudio UI 和交互设计经验</span><span class="sxs-lookup"><span data-stu-id="f197f-453">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="f197f-454">应用程序示例：定期表的元素</span><span class="sxs-lookup"><span data-stu-id="f197f-454">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="f197f-455">应用程序示例：农历模块</span><span class="sxs-lookup"><span data-stu-id="f197f-455">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="f197f-456">MR 输入 210：凝视</span><span class="sxs-lookup"><span data-stu-id="f197f-456">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="f197f-457">MR 输入 211：手势</span><span class="sxs-lookup"><span data-stu-id="f197f-457">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="f197f-458">MR 输入 212：语音</span><span class="sxs-lookup"><span data-stu-id="f197f-458">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="f197f-459">种交互的对象</span><span class="sxs-lookup"><span data-stu-id="f197f-459">Interactable objects</span></span>

<span data-ttu-id="f197f-460">一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。</span><span class="sxs-lookup"><span data-stu-id="f197f-460">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="f197f-461">在三维混合的现实世界中，我们无需限制为抽象不再这个世界。</span><span class="sxs-lookup"><span data-stu-id="f197f-461">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="f197f-462">任何可以是一个种交互的对象，将触发一个事件。</span><span class="sxs-lookup"><span data-stu-id="f197f-462">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="f197f-463">种交互的对象可以表示为任何从上表杯咖啡到气球状飘浮在空中。</span><span class="sxs-lookup"><span data-stu-id="f197f-463">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="f197f-464">无论窗体中，应通过视频和音频提示用户清楚地识别种交互的对象。</span><span class="sxs-lookup"><span data-stu-id="f197f-464">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-465">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-465">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-466"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-466"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-467"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-467"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-468">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-468">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f197f-469">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-469">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-470">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-470">Quality criteria</span></span>

|  <span data-ttu-id="f197f-471">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-471">Best</span></span>  |  <span data-ttu-id="f197f-472">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-472">Meets</span></span> |  <span data-ttu-id="f197f-473">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-473">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f197f-474">无论窗体，种交互对象都是通过视频和音频提示可识别跨三种状态： 空闲，设定目标，并选择。</span><span class="sxs-lookup"><span data-stu-id="f197f-474">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="f197f-475">"到它，请说"清晰、 一致地使用整个体验。</span><span class="sxs-lookup"><span data-stu-id="f197f-475">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="f197f-476">缩放对象并将其分发以便免费目标错误。</span><span class="sxs-lookup"><span data-stu-id="f197f-476">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="f197f-477">用户可以将对象识别为种交互通过音频或可视反馈和可以为目标并激活对象。</span><span class="sxs-lookup"><span data-stu-id="f197f-477">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="f197f-478">给定没有直观或音频提示，用户不能识别种交互的对象。</span><span class="sxs-lookup"><span data-stu-id="f197f-478">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="f197f-479">交互是由于对象规模或对象之间的距离容易出错。</span><span class="sxs-lookup"><span data-stu-id="f197f-479">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f197f-480">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-480">How to measure</span></span>

* <span data-ttu-id="f197f-481">种交互的对象是识别为种交互';其中包括按钮、 菜单和应用程序特定的内容。</span><span class="sxs-lookup"><span data-stu-id="f197f-481">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="f197f-482">作为经验法则存在时应为视频和音频提示指向种交互的对象。</span><span class="sxs-lookup"><span data-stu-id="f197f-482">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-483">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-483">Recommendations</span></span>

* <span data-ttu-id="f197f-484">使用视频和音频反馈进行交互。</span><span class="sxs-lookup"><span data-stu-id="f197f-484">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="f197f-485">对于每个输入 （空闲、 目标、 所选） 的状态应区分可视反馈</span><span class="sxs-lookup"><span data-stu-id="f197f-485">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="f197f-486">应缩放并放置错误免费面向种交互的对象。</span><span class="sxs-lookup"><span data-stu-id="f197f-486">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="f197f-487">分组种交互对象 （如菜单栏或列表） 应具有针对适当的间距。</span><span class="sxs-lookup"><span data-stu-id="f197f-487">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="f197f-488">按钮和菜单支持语音命令应为命令关键字提供文本标签 （"来看，说"）</span><span class="sxs-lookup"><span data-stu-id="f197f-488">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-489">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-489">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f197f-490">文档</span><span class="sxs-lookup"><span data-stu-id="f197f-490">Documentation</span></span>

* [<span data-ttu-id="f197f-491">可交互对象</span><span class="sxs-lookup"><span data-stu-id="f197f-491">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f197f-492">Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="f197f-492">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="f197f-493">应用栏和边界框</span><span class="sxs-lookup"><span data-stu-id="f197f-493">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f197f-494">语音命令</span><span class="sxs-lookup"><span data-stu-id="f197f-494">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f197f-495">工具和教程</span><span class="sxs-lookup"><span data-stu-id="f197f-495">Tools and tutorials</span></span>

* [<span data-ttu-id="f197f-496">混合的现实工具包-用户体验</span><span class="sxs-lookup"><span data-stu-id="f197f-496">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="f197f-497">扫描的房间</span><span class="sxs-lookup"><span data-stu-id="f197f-497">Room scanning</span></span>

<span data-ttu-id="f197f-498">需要空间映射数据的应用程序依赖于设备要自动随着时间的推移收集这些数据，并跨会话作为用户与设备 active 探讨其环境。</span><span class="sxs-lookup"><span data-stu-id="f197f-498">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="f197f-499">完整性和此数据的质量取决于多种因素，包括用户已经进行了数量、 探索以来经过多少时间和家具和门之类的对象是否具有移动设备扫描区域之后。</span><span class="sxs-lookup"><span data-stu-id="f197f-499">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="f197f-500">许多应用程序将分析了体验，以判断用户是否应该执行附加步骤以提高完整性和质量空间映射的开头处的空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="f197f-500">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="f197f-501">如果用户需要扫描环境中，清除应扫描体验期间提供的指导。</span><span class="sxs-lookup"><span data-stu-id="f197f-501">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-502">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-502">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-503"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-503"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-504"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-504"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-505">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-505">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-506">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-506">Quality criteria</span></span>

|  <span data-ttu-id="f197f-507">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-507">Best</span></span>  |  <span data-ttu-id="f197f-508">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-508">Meets</span></span> |  <span data-ttu-id="f197f-509">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-509">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f197f-510">空间网格的可视化效果告诉用户扫描正在进行中。</span><span class="sxs-lookup"><span data-stu-id="f197f-510">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="f197f-511">用户清楚地知道要执行的操作和扫描的启动和停止时。</span><span class="sxs-lookup"><span data-stu-id="f197f-511">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="f197f-512">提供空间网格的可视化效果，但用户不清楚地知道要执行的操作并提供进度的信息。</span><span class="sxs-lookup"><span data-stu-id="f197f-512">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="f197f-513">网格的任何可视化效果。</span><span class="sxs-lookup"><span data-stu-id="f197f-513">No visualization of mesh.</span></span> <span data-ttu-id="f197f-514">没有为用户提供有关在何处查找或当扫描启动/停止提供指导信息。</span><span class="sxs-lookup"><span data-stu-id="f197f-514">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="f197f-515">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-515">How to measure</span></span>

* <span data-ttu-id="f197f-516">在所需的空间扫描期间，该值指示哪儿去，以及何时启动和停止扫描提供视频和音频指导。</span><span class="sxs-lookup"><span data-stu-id="f197f-516">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-517">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-517">Recommendations</span></span>

* <span data-ttu-id="f197f-518">指示用户邻近范围中的总卷大小必须是体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="f197f-518">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="f197f-519">进行通信时在扫描开始和停止进度指示器等。</span><span class="sxs-lookup"><span data-stu-id="f197f-519">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="f197f-520">使用网格的扫描期间的可视化效果。</span><span class="sxs-lookup"><span data-stu-id="f197f-520">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="f197f-521">提供视觉和声音鼓励用户查找和移动的房间内的提示。</span><span class="sxs-lookup"><span data-stu-id="f197f-521">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="f197f-522">通知用户转到以提高数据的位置。</span><span class="sxs-lookup"><span data-stu-id="f197f-522">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="f197f-523">在许多情况下，可能是最好地告知用户他们需要执行操作 （例如回顾上限，在查找家具），以获取必要的扫描质量。</span><span class="sxs-lookup"><span data-stu-id="f197f-523">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-524">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-524">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f197f-525">文档</span><span class="sxs-lookup"><span data-stu-id="f197f-525">Documentation</span></span>

* [<span data-ttu-id="f197f-526">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="f197f-526">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="f197f-527">案例研究：扩展 HoloLens 的空间映射功能</span><span class="sxs-lookup"><span data-stu-id="f197f-527">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="f197f-528">案例研究：有关 HoloTour 空间合理的设计</span><span class="sxs-lookup"><span data-stu-id="f197f-528">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="f197f-529">案例研究：在片段中创建的沉浸式体验</span><span class="sxs-lookup"><span data-stu-id="f197f-529">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f197f-530">工具和教程</span><span class="sxs-lookup"><span data-stu-id="f197f-530">Tools and tutorials</span></span>

* [<span data-ttu-id="f197f-531">混合的现实工具包-用户体验</span><span class="sxs-lookup"><span data-stu-id="f197f-531">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="f197f-532">方向指示器</span><span class="sxs-lookup"><span data-stu-id="f197f-532">Directional indicators</span></span>

<span data-ttu-id="f197f-533">在混合的现实应用中，内容可能不在视图的字段或封闭的实际对象。</span><span class="sxs-lookup"><span data-stu-id="f197f-533">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="f197f-534">设计良好的应用程序将便于用户查找不可见的内容。</span><span class="sxs-lookup"><span data-stu-id="f197f-534">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="f197f-535">方向指示器重要内容向用户发出警报，并提供指导以相对于用户的位置的内容。</span><span class="sxs-lookup"><span data-stu-id="f197f-535">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="f197f-536">非可见内容的指南可以采用声音发射器、 方向箭头或直接视觉提示的形式。</span><span class="sxs-lookup"><span data-stu-id="f197f-536">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-537">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-537">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-538"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-538"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-539"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-539"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-540">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-540">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f197f-541">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-541">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-542">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-542">Quality criteria</span></span>

|  <span data-ttu-id="f197f-543">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-543">Best</span></span>  |  <span data-ttu-id="f197f-544">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-544">Meets</span></span> |  <span data-ttu-id="f197f-545">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-545">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f197f-546">视频和音频提示直接引导到外部的视图的字段的相关内容的用户。</span><span class="sxs-lookup"><span data-stu-id="f197f-546">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="f197f-547">一个箭头或指向内容的常规方向中的用户某个指示器。</span><span class="sxs-lookup"><span data-stu-id="f197f-547">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="f197f-548">相关内容是外部视野，以及较差或没有位置的指南提供给用户。</span><span class="sxs-lookup"><span data-stu-id="f197f-548">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f197f-549">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-549">How to measure</span></span>

* <span data-ttu-id="f197f-550">外部用户视角的相关内容是通过 visual 和/或音频提示发现。</span><span class="sxs-lookup"><span data-stu-id="f197f-550">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-551">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-551">Recommendations</span></span>

* <span data-ttu-id="f197f-552">外部用户的视角相关的内容时，请使用方向指示器和音频提示来指导用户到达的内容。</span><span class="sxs-lookup"><span data-stu-id="f197f-552">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="f197f-553">在许多情况下，直接的可视指南优于方向箭头。</span><span class="sxs-lookup"><span data-stu-id="f197f-553">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="f197f-554">方向指示器不应内置光标。</span><span class="sxs-lookup"><span data-stu-id="f197f-554">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-555">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-555">Resources</span></span>

* [<span data-ttu-id="f197f-556">全息帧</span><span class="sxs-lookup"><span data-stu-id="f197f-556">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="f197f-557">数据加载</span><span class="sxs-lookup"><span data-stu-id="f197f-557">Data loading</span></span>

<span data-ttu-id="f197f-558">进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。</span><span class="sxs-lookup"><span data-stu-id="f197f-558">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="f197f-559">它可能表示用户不能与应用交互，当进度指示器可见，并且还可以指示等待时间可能是多长时间。</span><span class="sxs-lookup"><span data-stu-id="f197f-559">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f197f-560">设备的影响</span><span class="sxs-lookup"><span data-stu-id="f197f-560">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="f197f-561"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f197f-561"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f197f-562"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="f197f-562"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="f197f-563">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-563">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f197f-564">✔️</span><span class="sxs-lookup"><span data-stu-id="f197f-564">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f197f-565">质量准则</span><span class="sxs-lookup"><span data-stu-id="f197f-565">Quality criteria</span></span>

|  <span data-ttu-id="f197f-566">最佳</span><span class="sxs-lookup"><span data-stu-id="f197f-566">Best</span></span>  |  <span data-ttu-id="f197f-567">符合</span><span class="sxs-lookup"><span data-stu-id="f197f-567">Meets</span></span> |  <span data-ttu-id="f197f-568">失败</span><span class="sxs-lookup"><span data-stu-id="f197f-568">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f197f-569">经过动画处理的可视指示器，进度栏或环，在任何数据加载或处理期间显示进度的窗体中。</span><span class="sxs-lookup"><span data-stu-id="f197f-569">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="f197f-570">可视的指示器多长时间等待可能是提供指导。</span><span class="sxs-lookup"><span data-stu-id="f197f-570">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="f197f-571">数据加载过程中，但不会指示的时间可能是在等待时通知用户。</span><span class="sxs-lookup"><span data-stu-id="f197f-571">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="f197f-572">无数据加载或过程的时间超过 5 秒的任务的指示符。</span><span class="sxs-lookup"><span data-stu-id="f197f-572">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="f197f-573">如何测量</span><span class="sxs-lookup"><span data-stu-id="f197f-573">How to measure</span></span>

* <span data-ttu-id="f197f-574">在数据加载过程中验证多个 5 秒后没有任何空白状态。</span><span class="sxs-lookup"><span data-stu-id="f197f-574">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f197f-575">建议</span><span class="sxs-lookup"><span data-stu-id="f197f-575">Recommendations</span></span>

* <span data-ttu-id="f197f-576">提供在任何情况下显示进度时用户可能会觉察到此应用程序已停止或已崩溃数据加载动画器。</span><span class="sxs-lookup"><span data-stu-id="f197f-576">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="f197f-577">合理的经验法则是可能需要超过 5 秒的任何正在加载的活动。</span><span class="sxs-lookup"><span data-stu-id="f197f-577">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="f197f-578">资源</span><span class="sxs-lookup"><span data-stu-id="f197f-578">Resources</span></span>

* [<span data-ttu-id="f197f-579">显示进度</span><span class="sxs-lookup"><span data-stu-id="f197f-579">Displaying progress</span></span>](progress.md)
