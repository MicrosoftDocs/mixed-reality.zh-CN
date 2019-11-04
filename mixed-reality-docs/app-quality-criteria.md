---
title: 应用质量标准
description: 本文档介绍影响混合现实应用质量的主要因素。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 应用质量标准，混合现实，混合现实应用
ms.openlocfilehash: f98111ebe9aacc30778e86501be41e6ac5f6d165
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437046"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="d9a5b-104">应用质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-104">App quality criteria</span></span>

<span data-ttu-id="d9a5b-105">本文档介绍影响混合现实应用质量的主要因素。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="d9a5b-106">对于每个因素，提供以下信息</span><span class="sxs-lookup"><span data-stu-id="d9a5b-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="d9a5b-107">概述-质量因素的简短说明及其重要原因。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="d9a5b-108">设备影响-影响哪种类型的窗口混合现实设备。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="d9a5b-109">质量标准–如何评估质量因素。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="d9a5b-110">如何度量–衡量问题（或体验）的方法。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="d9a5b-111">建议-概述提供更好的用户体验的方法。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="d9a5b-112">资源-相关的开发人员和设计资源有助于创建更好的应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="d9a5b-113">帧速率</span><span class="sxs-lookup"><span data-stu-id="d9a5b-113">Frame rate</span></span>

<span data-ttu-id="d9a5b-114">帧速率是全息图稳定性和用户舒适的第一个支柱。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="d9a5b-115">低于建议目标的帧速率可能导致全息影像出现抖动，对体验的 believability 产生负面影响，并可能导致目视疲劳。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="d9a5b-116">针对 Windows Mixed Reality 沉浸式耳机的目标帧速率为60Hz 或90Hz，具体取决于你想要支持的与 Windows Mixed Reality 兼容的电脑。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="d9a5b-117">对于 HoloLens，目标帧速率为60Hz。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-118">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-121">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-121">✔️</span></span></td>
        <td><span data-ttu-id="d9a5b-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-123">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-123">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-124">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-124">Best</span></span>  |  <span data-ttu-id="d9a5b-125">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-125">Meets</span></span> |  <span data-ttu-id="d9a5b-126">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="d9a5b-127">应用一致地满足目标设备的每秒帧数（FPS）目标： 60fps on HoloLens;超计算机上的 90fps;并60fps。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="d9a5b-128">应用有间歇性的帧不会阻碍核心体验;或 FPS 一直低于所需的目标，但不会妨碍应用程序的体验。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="d9a5b-129">此应用在每10秒或更短时间内遇到帧速率下降。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-130">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-130">How to measure</span></span>

* <span data-ttu-id="d9a5b-131">实时帧速率图通过[Windows 设备门户](using-the-windows-device-portal.md#system-performance)在 "系统性能" 下提供。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="d9a5b-132">对于开发调试，请将帧速率诊断计数器添加到应用中。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="d9a5b-133">查看示例计数器的资源。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="d9a5b-134">当应用程序运行时，可以在设备中体验到帧速率下降。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="d9a5b-135">如果全息图显示意外的抖动运动，则帧速率较低或稳定性平面可能是原因。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-136">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-136">Recommendations</span></span>

* <span data-ttu-id="d9a5b-137">在开发工作开始时添加帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="d9a5b-138">应评估出现帧速率下降的更改，并适当地将其解析为性能 bug。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-139">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9a5b-140">文档</span><span class="sxs-lookup"><span data-stu-id="d9a5b-140">Documentation</span></span>

* [<span data-ttu-id="d9a5b-141">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="d9a5b-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="d9a5b-142">全息图稳定性和帧速率</span><span class="sxs-lookup"><span data-stu-id="d9a5b-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="d9a5b-143">资产性能预算</span><span class="sxs-lookup"><span data-stu-id="d9a5b-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="d9a5b-144">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9a5b-145">工具和教程</span><span class="sxs-lookup"><span data-stu-id="d9a5b-145">Tools and tutorials</span></span>

* [<span data-ttu-id="d9a5b-146">MRToolkit，FPS 计数器显示</span><span class="sxs-lookup"><span data-stu-id="d9a5b-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="d9a5b-147">MRToolkit，着色器</span><span class="sxs-lookup"><span data-stu-id="d9a5b-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="d9a5b-148">外部引用</span><span class="sxs-lookup"><span data-stu-id="d9a5b-148">External references</span></span>

* [<span data-ttu-id="d9a5b-149">Unity，优化移动应用程序</span><span class="sxs-lookup"><span data-stu-id="d9a5b-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="d9a5b-150">全息影像稳定性</span><span class="sxs-lookup"><span data-stu-id="d9a5b-150">Hologram stability</span></span>

<span data-ttu-id="d9a5b-151">稳定的全息影像会提高应用程序的可用性和 believability，并为用户创建更舒适的查看体验。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="d9a5b-152">全息图稳定性的质量是良好的应用程序开发和设备了解（跟踪）其环境的能力。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="d9a5b-153">尽管帧速率是稳定性的第一支柱，但其他因素可能会影响稳定性，其中包括：</span><span class="sxs-lookup"><span data-stu-id="d9a5b-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="d9a5b-154">使用 "稳定" 平面</span><span class="sxs-lookup"><span data-stu-id="d9a5b-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="d9a5b-155">与空间锚的距离</span><span class="sxs-lookup"><span data-stu-id="d9a5b-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="d9a5b-156">字距</span><span class="sxs-lookup"><span data-stu-id="d9a5b-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-157">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-159"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-160">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-161">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-161">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-162">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-162">Best</span></span>  |  <span data-ttu-id="d9a5b-163">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-163">Meets</span></span> |  <span data-ttu-id="d9a5b-164">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9a5b-165">全息影像显示稳定。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="d9a5b-166">辅助内容展示意外移动;或意外移动不会妨碍总体应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="d9a5b-167">帧中的主要内容表现出意外移动。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-168">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-168">How to measure</span></span>

<span data-ttu-id="d9a5b-169">戴设备并观看体验：</span><span class="sxs-lookup"><span data-stu-id="d9a5b-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="d9a5b-170">从一侧到另一侧移动您的头，如果全息影像显示意外的移动，稳定的稳定性平面与焦距平面之间的不正确对齐就是可能的原因。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="d9a5b-171">四处移动影像和环境，查找泳道和 jumpiness 等行为。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="d9a5b-172">此类动作可能由设备不跟踪环境或到空间锚点的距离引起。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="d9a5b-173">如果帧中有大的或多个全息影像，请在不同的深度观察全息影像行为，同时从一侧到另一侧，如果出现抖动，这可能是由稳定平面导致的。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="d9a5b-174">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-174">Recomendations</span></span>

* <span data-ttu-id="d9a5b-175">在开发工作开始时添加帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="d9a5b-176">使用 "稳定" 平面。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="d9a5b-177">始终在其定位点的3米以内呈现定位的全息影像。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="d9a5b-178">请确保您的环境设置正确跟踪。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="d9a5b-179">设计你的体验，以避免帧内处于不同焦点级别的全息影像。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-180">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9a5b-181">文档</span><span class="sxs-lookup"><span data-stu-id="d9a5b-181">Documentation</span></span>

* [<span data-ttu-id="d9a5b-182">全息图稳定性和帧速率</span><span class="sxs-lookup"><span data-stu-id="d9a5b-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="d9a5b-183">使用 "稳定" 平面进行案例研究</span><span class="sxs-lookup"><span data-stu-id="d9a5b-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="d9a5b-184">了解混合现实的性能</span><span class="sxs-lookup"><span data-stu-id="d9a5b-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="d9a5b-185">针对 Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="d9a5b-186">空间定位点</span><span class="sxs-lookup"><span data-stu-id="d9a5b-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="d9a5b-187">处理跟踪错误</span><span class="sxs-lookup"><span data-stu-id="d9a5b-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="d9a5b-188">固定的引用框架</span><span class="sxs-lookup"><span data-stu-id="d9a5b-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9a5b-189">工具和教程</span><span class="sxs-lookup"><span data-stu-id="d9a5b-189">Tools and tutorials</span></span>

* [<span data-ttu-id="d9a5b-190">MR 配套包，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="d9a5b-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="d9a5b-191">实面上的全息影像位置</span><span class="sxs-lookup"><span data-stu-id="d9a5b-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="d9a5b-192">使用物理对象（如果要彼此相关）的 Misalignments，可以清楚地指示全息影像和真实世界的非联合。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="d9a5b-193">位置的准确性应与方案的需求相关;例如，常规表面布局可以使用空间图，但更准确的放置需要使用标记和校准。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-194">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-196"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-196"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-197">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-198">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-198">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-199">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-199">Best</span></span>  |  <span data-ttu-id="d9a5b-200">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-200">Meets</span></span> |  <span data-ttu-id="d9a5b-201">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="d9a5b-202">全息图通常以厘米到英寸的范围对齐。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="d9a5b-203">如果需要更高的准确性，应用应在所需的应用规范内提供高效的协作方式。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="d9a5b-204">NA</span><span class="sxs-lookup"><span data-stu-id="d9a5b-204">NA</span></span> | <span data-ttu-id="d9a5b-205">通过断开 surface 平面或远离表面，全息影像将与物理目标对象显示不对齐。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="d9a5b-206">如果需要准确性，全息影像应满足方案的邻近规范。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-207">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-207">How to measure</span></span>

* <span data-ttu-id="d9a5b-208">放置在空间地图上的全息影像不会显得明显地浮动在表面上方或下方。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="d9a5b-209">需要精确放置的全息影像应具有某种形式的标记和校准系统，这种系统对于方案的要求是准确的。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-210">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-210">Recommendations</span></span>

* <span data-ttu-id="d9a5b-211">空间映射适用于在不需要精度时将对象放置在图面上。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="d9a5b-212">为了获得最佳的精度，请使用标记或海报来设置全息影像，并使用 Xbox 控制器（或某种手动对齐机制）来进行最终校准。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="d9a5b-213">考虑将超大型全息图分解为逻辑部件，并将每个部件与图面对齐。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="d9a5b-214">错误设置的 interpupilary 距离（IPD）还会影响全息图对齐。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="d9a5b-215">始终将 HoloLens 配置为用户的 IPD。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-216">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9a5b-217">文档</span><span class="sxs-lookup"><span data-stu-id="d9a5b-217">Documentation</span></span>

* [<span data-ttu-id="d9a5b-218">空间映射放置</span><span class="sxs-lookup"><span data-stu-id="d9a5b-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="d9a5b-219">房间扫描过程</span><span class="sxs-lookup"><span data-stu-id="d9a5b-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="d9a5b-220">空间锚定最佳做法</span><span class="sxs-lookup"><span data-stu-id="d9a5b-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="d9a5b-221">处理跟踪错误</span><span class="sxs-lookup"><span data-stu-id="d9a5b-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="d9a5b-222">Unity 中的空间映射</span><span class="sxs-lookup"><span data-stu-id="d9a5b-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="d9a5b-223">Vuforia 开发概述</span><span class="sxs-lookup"><span data-stu-id="d9a5b-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9a5b-224">工具和教程</span><span class="sxs-lookup"><span data-stu-id="d9a5b-224">Tools and tutorials</span></span>

* [<span data-ttu-id="d9a5b-225">MR 空间230：空间映射</span><span class="sxs-lookup"><span data-stu-id="d9a5b-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="d9a5b-226">MR 工具包，空间映射库</span><span class="sxs-lookup"><span data-stu-id="d9a5b-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="d9a5b-227">MR 配套包，海报校准示例</span><span class="sxs-lookup"><span data-stu-id="d9a5b-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="d9a5b-228">MR 配套包，Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="d9a5b-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="d9a5b-229">外部引用</span><span class="sxs-lookup"><span data-stu-id="d9a5b-229">External references</span></span>

* [<span data-ttu-id="d9a5b-230">Lowes 案例研究，精度调整</span><span class="sxs-lookup"><span data-stu-id="d9a5b-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="d9a5b-231">轻松查看区域</span><span class="sxs-lookup"><span data-stu-id="d9a5b-231">Viewing zone of comfort</span></span>

<span data-ttu-id="d9a5b-232">应用开发人员通过在不同的深度放置内容和全息影像来控制用户的眼睛汇聚。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="d9a5b-233">戴 HoloLens 的用户将始终适应 2.0 m 以保持清晰的图像，因为在与用户相比，与用户相比，在大约2.0 个位置固定了 HoloLens 显示。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="d9a5b-234">内容深度不正确可能会导致 visual discomfort 或疲劳。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-235">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-237"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-237"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-238">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-239">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="d9a5b-240">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="d9a5b-241">将内容放置在2m。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-241">Place content at 2m.</span></span></li><li><span data-ttu-id="d9a5b-242">如果无法在2m 中放置全息影像并且无法避免聚合和便利设施之间发生冲突，则全息图位置的最佳区域介于 1.25 m 和5分钟之间。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="d9a5b-243">在每种情况下，设计器都应该构建内容来鼓励用户与 1 + m 交互（例如，调整内容大小和默认位置参数）。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="d9a5b-244">除非方案特别不需要，否则应使用从1m 开始的 fadeout 实现剪辑平面。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="d9a5b-245">如果需要更密切地观察 motionless 全息图，内容不应比50cm 更接近。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="d9a5b-246">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-246">Meets</span></span></td><td> <span data-ttu-id="d9a5b-247">内容在查看和运动指导范围内，但不恰当地使用或不使用剪辑平面。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9a5b-248">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-248">Fail</span></span> </td><td> <span data-ttu-id="d9a5b-249">内容显示得太近（通常 &lt;1.25 m，或 &lt;50cm，适用于需要更密切观察的静止全息影像。）</span><span class="sxs-lookup"><span data-stu-id="d9a5b-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-250">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-250">How to measure</span></span>

* <span data-ttu-id="d9a5b-251">内容通常应2m，但不能比5分钟更接近1.25 或更远。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="d9a5b-252">在少数例外情况下，将在从1m 开始，为 fadeout 的内容设置为85CM。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="d9a5b-253">接近内容并记下剪辑平面效果。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="d9a5b-254">固定内容不应比50cm 更近。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-255">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-255">Recommendations</span></span>

* <span data-ttu-id="d9a5b-256">设计内容以获取2m 的最佳视图距离。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="d9a5b-257">将剪辑呈现距离设置为85cm，并将 fadeout 的内容从1m 开始。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="d9a5b-258">对于需要更近查看的静止全息影像，剪辑平面应不会比30cm 更近，fadeout 应该至少从剪裁平面开始10cm。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-259">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-259">Resources</span></span>

* [<span data-ttu-id="d9a5b-260">呈现距离</span><span class="sxs-lookup"><span data-stu-id="d9a5b-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="d9a5b-261">Unity 中的焦点</span><span class="sxs-lookup"><span data-stu-id="d9a5b-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="d9a5b-262">进行大规模试验</span><span class="sxs-lookup"><span data-stu-id="d9a5b-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="d9a5b-263">文本，建议的字号</span><span class="sxs-lookup"><span data-stu-id="d9a5b-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="d9a5b-264">深度切换</span><span class="sxs-lookup"><span data-stu-id="d9a5b-264">Depth switching</span></span>

<span data-ttu-id="d9a5b-265">无论查看舒适问题的区域如何，用户在接近和远的焦距对象（包括全息影像和真实内容）之间进行频繁或快速切换都可能会导致 oculomotor 疲劳和 general discomfort。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-266">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-268"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-268"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-269">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-269">✔️</span></span></td>
        <td><span data-ttu-id="d9a5b-270">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-271">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-271">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-272">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-272">Best</span></span>  |  <span data-ttu-id="d9a5b-273">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-273">Meets</span></span> |  <span data-ttu-id="d9a5b-274">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9a5b-275">不会导致用户 unnaturally refocus 的有限或自然深度切换。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="d9a5b-276">突然深度切换这是核心的，设计为应用程序体验，或由于意外的实际内容而产生的突然深度切换。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="d9a5b-277">一致的深度切换或对应用程序体验不必要或核心的突然深度切换。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-278">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-278">How to measure</span></span>

* <span data-ttu-id="d9a5b-279">如果应用要求用户持续和/或突然改变深度焦点，则会出现深度切换问题。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-280">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-280">Recommendations</span></span>

* <span data-ttu-id="d9a5b-281">保持主要内容处于一致的焦点平面上，并确保 "稳定" 平面与焦点平面匹配。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="d9a5b-282">这将减少 oculomotor 疲劳和意外的全息图移动。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-283">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-283">Resources</span></span>

* [<span data-ttu-id="d9a5b-284">呈现距离</span><span class="sxs-lookup"><span data-stu-id="d9a5b-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="d9a5b-285">Unity 中的焦点</span><span class="sxs-lookup"><span data-stu-id="d9a5b-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="d9a5b-286">使用空间音效</span><span class="sxs-lookup"><span data-stu-id="d9a5b-286">Use of spatial sound</span></span>

<span data-ttu-id="d9a5b-287">在 Windows Mixed Reality 中，音频引擎通过使用方向、距离和环境模拟模拟3D 声音，提供混合现实体验的听觉组件。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="d9a5b-288">在应用程序中使用空间音效使开发人员能够在整个用户的 convincingly 中放置声音。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="d9a5b-289">然后，这些声音看起来就像是来自真实的物理对象，或是用户的环境中的混合现实影像。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="d9a5b-290">空间音效是用于混合现实应用程序中的浸入式、可访问性和 UX 设计的强大工具。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-291">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-293"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-293"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-294">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-294">✔️</span></span></td>
        <td><span data-ttu-id="d9a5b-295">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-296">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-296">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-297">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-297">Best</span></span>  |  <span data-ttu-id="d9a5b-298">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-298">Meets</span></span> |  <span data-ttu-id="d9a5b-299">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9a5b-300">声音以逻辑方式 spatialized，并适当地使用声音来帮助进行对象发现和用户反馈。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="d9a5b-301">声音非常自然，与对象相关，并在整个方案中标准化。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="d9a5b-302">空间音频适用于 believability，但它不能帮助用户提供反馈和发现。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="d9a5b-303">听不到预期的声音，并且/或缺少声音来帮助用户在 UX 中 spatialized。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="d9a5b-304">或在方案设计中不考虑或使用空间音频。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-305">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-305">How to measure</span></span>

* <span data-ttu-id="d9a5b-306">通常，相关声音应从目标全息影像发出（例如，吠声音来自全息狗。）</span><span class="sxs-lookup"><span data-stu-id="d9a5b-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="d9a5b-307">应在整个 UX 中使用声音提示，以帮助用户在全息帧外提供反馈或了解操作。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-308">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-308">Recommendations</span></span>

* <span data-ttu-id="d9a5b-309">使用空间音频来帮助对象发现和用户界面。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="d9a5b-310">真实声音比合成或非自然声音更好。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="d9a5b-311">大多数声音应为 spatialized。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="d9a5b-312">避免不可见的发射器。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="d9a5b-313">避免空间屏蔽。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="d9a5b-314">规范化所有声音。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-315">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9a5b-316">文档</span><span class="sxs-lookup"><span data-stu-id="d9a5b-316">Documentation</span></span>

* [<span data-ttu-id="d9a5b-317">空间音效</span><span class="sxs-lookup"><span data-stu-id="d9a5b-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="d9a5b-318">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="d9a5b-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="d9a5b-319">Unity 中的空间音效</span><span class="sxs-lookup"><span data-stu-id="d9a5b-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="d9a5b-320">案例研究，HoloTour 的空间音效</span><span class="sxs-lookup"><span data-stu-id="d9a5b-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="d9a5b-321">案例研究，在 RoboRaid 中使用空间音效</span><span class="sxs-lookup"><span data-stu-id="d9a5b-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9a5b-322">工具和教程</span><span class="sxs-lookup"><span data-stu-id="d9a5b-322">Tools and tutorials</span></span>

* [<span data-ttu-id="d9a5b-323">MR 空间220：空间音效</span><span class="sxs-lookup"><span data-stu-id="d9a5b-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="d9a5b-324">MRToolkit，空间音频</span><span class="sxs-lookup"><span data-stu-id="d9a5b-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="d9a5b-325">专注于全息帧（FOV）边界</span><span class="sxs-lookup"><span data-stu-id="d9a5b-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="d9a5b-326">设计良好的用户体验可以创建和维护围绕用户扩展的虚拟环境的有用上下文。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="d9a5b-327">缓解 FOV 边界的影响涉及到精心设计的内容规模和上下文、使用空间音频、指导系统和用户的位置。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="d9a5b-328">如果完成了正确的操作，该用户将感到不受 FOV 边界的影响，同时具有舒适的应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-329">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-329">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-331"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-331"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-332">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-332">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-333">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-333">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-334">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-334">Best</span></span>  |  <span data-ttu-id="d9a5b-335">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-335">Meets</span></span> |  <span data-ttu-id="d9a5b-336">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9a5b-337">用户永远不会失去上下文和查看。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="d9a5b-338">为大对象提供了上下文帮助。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="d9a5b-339">为框架外的对象提供了可发现性和查看指南。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="d9a5b-340">通常，动画的动画设计和规模调整适用于舒适的观看体验。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="d9a5b-341">用户永远不会丢失上下文，但在有限的情况下，可能需要额外的颈部运动。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="d9a5b-342">在有限的情况下，规模会导致动态影像中断垂直或水平的帧，导致某些颈部运动查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="d9a5b-343">若要查看全息影像，用户可能丢失上下文和/或一致的颈部运动。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="d9a5b-344">如果没有适用于大全息对象的上下文指南，则可以轻松地在帧外移动对象，而无需发现指引，或者需要定期移动影像来查看。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-345">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-345">How to measure</span></span>

* <span data-ttu-id="d9a5b-346">由于在边界处裁剪，（大）全息图的上下文丢失或无法理解。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="d9a5b-347">由于缺少引起注意的控制器或可快速移入和移出全息帧的内容，因此很难找到全息影像的位置。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="d9a5b-348">方案需要定期和重复的向上和向下移动，才能完全查看疲劳的全息图。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-349">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-349">Recommendations</span></span>

* <span data-ttu-id="d9a5b-350">开始体验适合 FOV 的小对象，然后将视觉提示转换为较大版本。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="d9a5b-351">使用空间音频和注意控制器来帮助用户查找 FOV 之外的内容。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="d9a5b-352">尽可能避免在垂直剪裁 FOV 的全息影像。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="d9a5b-353">为用户提供应用内指南以获得最佳观看位置。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-354">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9a5b-355">文档</span><span class="sxs-lookup"><span data-stu-id="d9a5b-355">Documentation</span></span>

* [<span data-ttu-id="d9a5b-356">全息帧</span><span class="sxs-lookup"><span data-stu-id="d9a5b-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="d9a5b-357">案例研究，HoloStudio UI 和交互设计知识</span><span class="sxs-lookup"><span data-stu-id="d9a5b-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="d9a5b-358">对象和环境的规模</span><span class="sxs-lookup"><span data-stu-id="d9a5b-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="d9a5b-359">游标，直观提示</span><span class="sxs-lookup"><span data-stu-id="d9a5b-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="d9a5b-360">外部引用</span><span class="sxs-lookup"><span data-stu-id="d9a5b-360">External references</span></span>

* [<span data-ttu-id="d9a5b-361">关于 FOV 的 ado</span><span class="sxs-lookup"><span data-stu-id="d9a5b-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="d9a5b-362">内容对用户位置的响应</span><span class="sxs-lookup"><span data-stu-id="d9a5b-362">Content reacts to user position</span></span>

<span data-ttu-id="d9a5b-363">全息影像应以与 "实际" 对象相同的方式对用户位置做出反应。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="d9a5b-364">一个值得注意的设计注意事项是 UI 元素，这些元素不一定会假设用户的位置为静止，并适应用户的动作。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="d9a5b-365">设计可正确适应用户位置的应用将创建更可信的体验，并使其更易于使用。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-366">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-366">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-368"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-368"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-369">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-369">✔️</span></span></td>
        <td><span data-ttu-id="d9a5b-370">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-370">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-371">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="d9a5b-372">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-372">Best</span></span> </td><td> <span data-ttu-id="d9a5b-373">内容和 UI 适应用户位置，使用户能够在预期用户移动范围内自然地与内容交互。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9a5b-374">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-374">Meets</span></span> </td><td> <span data-ttu-id="d9a5b-375">UI 适应用户位置，但可能会妨碍关键内容的查看，要求用户调整其位置。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d9a5b-376">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="d9a5b-377">UI 元素在移动过程中丢失或锁定，导致用户 unnaturally 返回（或查找）控件。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="d9a5b-378">UI 元素限制主要内容的视图。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="d9a5b-379">UI 移动不是针对查看距离和动力而优化的，尤其是在<a href="billboarding-and-tag-along.md">标记沿</a>ui 元素上。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-380">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-380">How to measure</span></span>

* <span data-ttu-id="d9a5b-381">所有度量值都应在合理的方案范围内完成。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="d9a5b-382">当用户移动发生变化时，不要尝试通过极端的用户移动来诱骗应用。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="d9a5b-383">对于 UI 元素，不管用户移动如何，相关控件都应可用。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="d9a5b-384">例如，如果用户正在使用缩放功能查看和浏览三维地图，则无论位置如何，缩放控件都应立即可供用户使用。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-385">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-385">Recommendations</span></span>

* <span data-ttu-id="d9a5b-386">用户是相机，它们控制移动。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="d9a5b-387">让它们驱动器。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-387">Let them drive.</span></span>
* <span data-ttu-id="d9a5b-388">对于文本和 menuing 系统，请考虑 billboarding，如果用户要四处移动，则可能会被全局锁定或遮住。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="d9a5b-389">同时对需要关注用户的内容使用标记，同时允许用户查看它们前面的内容。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-390">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9a5b-391">文档</span><span class="sxs-lookup"><span data-stu-id="d9a5b-391">Documentation</span></span>

* [<span data-ttu-id="d9a5b-392">交互设计</span><span class="sxs-lookup"><span data-stu-id="d9a5b-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="d9a5b-393">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="d9a5b-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="d9a5b-394">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="d9a5b-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d9a5b-395">本能交互</span><span class="sxs-lookup"><span data-stu-id="d9a5b-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="d9a5b-396">自移动和用户 locomotion</span><span class="sxs-lookup"><span data-stu-id="d9a5b-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9a5b-397">工具和教程</span><span class="sxs-lookup"><span data-stu-id="d9a5b-397">Tools and tutorials</span></span>

* [<span data-ttu-id="d9a5b-398">MR 输入210：注视</span><span class="sxs-lookup"><span data-stu-id="d9a5b-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="d9a5b-399">输入交互清晰度</span><span class="sxs-lookup"><span data-stu-id="d9a5b-399">Input interaction clarity</span></span>

<span data-ttu-id="d9a5b-400">输入交互清晰度对于应用可用性至关重要，其中包括输入一致性、设计、交互方法的可发现性。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="d9a5b-401">用户应能够在不 relearning 的情况下使用平台范围的常见交互。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="d9a5b-402">如果应用具有自定义输入，则应该清楚地传达并演示。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-403">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-403">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-405"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-405"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-406">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-406">✔️</span></span></td>
        <td><span data-ttu-id="d9a5b-407">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-407">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-408">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-408">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-409">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-409">Best</span></span>  |  <span data-ttu-id="d9a5b-410">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-410">Meets</span></span> |  <span data-ttu-id="d9a5b-411">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9a5b-412">输入交互方法与 Windows Mixed Reality 提供的[指南](interaction-fundamentals.md)一致。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="d9a5b-413">任何自定义输入都不应对标准输入冗余（而不是使用标准交互），必须清楚地传达并向用户演示。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="d9a5b-414">与最佳方法相似，但自定义输入对于标准输入方法是冗余的。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="d9a5b-415">用户仍可通过应用体验实现目标和进度。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="d9a5b-416">难以理解输入法或按钮映射。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="d9a5b-417">输入进行了大量自定义，不支持标准输入、无说明或可能会导致疲劳和舒适的问题。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-418">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-418">How to measure</span></span>

* <span data-ttu-id="d9a5b-419">应用使用一致[的标准输入法。](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="d9a5b-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="d9a5b-420">如果应用有时候输入，则会通过以下方法清楚地传达此内容：</span><span class="sxs-lookup"><span data-stu-id="d9a5b-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="d9a5b-421">首次运行体验</span><span class="sxs-lookup"><span data-stu-id="d9a5b-421">First-run experience</span></span>
* <span data-ttu-id="d9a5b-422">介绍屏幕</span><span class="sxs-lookup"><span data-stu-id="d9a5b-422">Introductory screens</span></span>
* <span data-ttu-id="d9a5b-423">工具提示</span><span class="sxs-lookup"><span data-stu-id="d9a5b-423">Tooltips</span></span>
* <span data-ttu-id="d9a5b-424">手动指导</span><span class="sxs-lookup"><span data-stu-id="d9a5b-424">Hand coach</span></span>
* <span data-ttu-id="d9a5b-425">帮助部分</span><span class="sxs-lookup"><span data-stu-id="d9a5b-425">Help section</span></span>
* <span data-ttu-id="d9a5b-426">语音</span><span class="sxs-lookup"><span data-stu-id="d9a5b-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-427">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-427">Recommendations</span></span>

* <span data-ttu-id="d9a5b-428">尽可能使用标准输入方法。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="d9a5b-429">为非标准输入法提供演示、教程和工具提示。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="d9a5b-430">在整个应用程序中使用一致的交互模型。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-431">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9a5b-432">文档</span><span class="sxs-lookup"><span data-stu-id="d9a5b-432">Documentation</span></span>

* [<span data-ttu-id="d9a5b-433">本能交互</span><span class="sxs-lookup"><span data-stu-id="d9a5b-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="d9a5b-434">种不可交互对象</span><span class="sxs-lookup"><span data-stu-id="d9a5b-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="d9a5b-435">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="d9a5b-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="d9a5b-436">光标</span><span class="sxs-lookup"><span data-stu-id="d9a5b-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d9a5b-437">舒适，注视</span><span class="sxs-lookup"><span data-stu-id="d9a5b-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="d9a5b-438">语音输入</span><span class="sxs-lookup"><span data-stu-id="d9a5b-438">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="d9a5b-439">运动控制器</span><span class="sxs-lookup"><span data-stu-id="d9a5b-439">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="d9a5b-440">Unity 的输入移植指南</span><span class="sxs-lookup"><span data-stu-id="d9a5b-440">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="d9a5b-441">Unity 中的键盘输入</span><span class="sxs-lookup"><span data-stu-id="d9a5b-441">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="d9a5b-442">Unity 中的凝视</span><span class="sxs-lookup"><span data-stu-id="d9a5b-442">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="d9a5b-443">Unity 中的手势和运动控制器</span><span class="sxs-lookup"><span data-stu-id="d9a5b-443">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="d9a5b-444">Unity 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="d9a5b-444">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="d9a5b-445">DirectX 中的键盘、鼠标和控制器输入</span><span class="sxs-lookup"><span data-stu-id="d9a5b-445">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="d9a5b-446">DirectX 中的头部和眼部凝视</span><span class="sxs-lookup"><span data-stu-id="d9a5b-446">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="d9a5b-447">DirectX 中的手和运动控制器</span><span class="sxs-lookup"><span data-stu-id="d9a5b-447">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="d9a5b-448">DirectX 中的语音输入</span><span class="sxs-lookup"><span data-stu-id="d9a5b-448">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9a5b-449">工具和教程</span><span class="sxs-lookup"><span data-stu-id="d9a5b-449">Tools and tutorials</span></span>

* [<span data-ttu-id="d9a5b-450">案例研究：对更多个人计算的追求</span><span class="sxs-lookup"><span data-stu-id="d9a5b-450">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="d9a5b-451">强制转换研究： HoloStudio UI 和交互设计知识</span><span class="sxs-lookup"><span data-stu-id="d9a5b-451">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="d9a5b-452">示例应用：元素的定期表</span><span class="sxs-lookup"><span data-stu-id="d9a5b-452">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="d9a5b-453">示例应用：农历模块</span><span class="sxs-lookup"><span data-stu-id="d9a5b-453">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="d9a5b-454">MR 输入210：注视</span><span class="sxs-lookup"><span data-stu-id="d9a5b-454">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="d9a5b-455">MR 输入211：手势</span><span class="sxs-lookup"><span data-stu-id="d9a5b-455">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="d9a5b-456">MR 输入212：语音</span><span class="sxs-lookup"><span data-stu-id="d9a5b-456">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="d9a5b-457">种不可交互对象</span><span class="sxs-lookup"><span data-stu-id="d9a5b-457">Interactable objects</span></span>

<span data-ttu-id="d9a5b-458">"Button" 是一种用于在二维抽象环境中触发事件的比喻。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-458">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="d9a5b-459">在这三维混合现实世界中，我们不必再局限于这种抽象领域。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-459">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="d9a5b-460">任何内容都可以是触发事件的种不可交互对象。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-460">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="d9a5b-461">种不可交互对象可表示为从桌子上的咖啡杯到悬浮的球标的任何内容。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-461">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="d9a5b-462">无论采用何种形式，用户都应该通过视觉对象和音频提示清楚地识别种不可交互对象。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-462">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-463">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-463">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-465"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-465"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-466">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-466">✔️</span></span></td>
        <td><span data-ttu-id="d9a5b-467">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-467">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-468">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-468">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-469">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-469">Best</span></span>  |  <span data-ttu-id="d9a5b-470">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-470">Meets</span></span> |  <span data-ttu-id="d9a5b-471">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-471">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9a5b-472">无论采用何种形式，都可以通过视觉对象和音频提示在三种状态下识别种不可交互对象：空闲、目标和选择。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-472">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="d9a5b-473">"看起来，说它" 是显而易见的，始终在整个体验中使用。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-473">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="d9a5b-474">对象经过缩放和分布，以允许错误释放目标。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-474">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="d9a5b-475">用户可以通过音频或视觉对象反馈将对象识别为种不可交互，并可以定位和激活对象。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-475">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="d9a5b-476">如果没有任何视觉对象或音频提示，用户将无法识别种不可交互对象。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-476">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="d9a5b-477">交互是由于对象比例或对象之间的距离而容易出错。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-477">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-478">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-478">How to measure</span></span>

* <span data-ttu-id="d9a5b-479">种不可交互对象可识别为 "种不可交互";包括按钮、菜单和特定于应用的内容。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-479">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="d9a5b-480">根据经验法则，在面向种不可交互对象时，应该有视觉和音频提示。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-480">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-481">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-481">Recommendations</span></span>

* <span data-ttu-id="d9a5b-482">使用视觉和音频反馈进行交互。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-482">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="d9a5b-483">对于每个输入状态（空闲、目标、选定），可视反馈应该是有差异的</span><span class="sxs-lookup"><span data-stu-id="d9a5b-483">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="d9a5b-484">应缩放种不可交互对象，并将其放置在错误释放目标位置。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-484">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="d9a5b-485">分组的种不可交互对象（如菜单栏或列表）应具有正确的目标间距。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-485">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="d9a5b-486">支持语音命令的按钮和菜单应为命令关键字提供文本标签（"请参阅它）"</span><span class="sxs-lookup"><span data-stu-id="d9a5b-486">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-487">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-487">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9a5b-488">文档</span><span class="sxs-lookup"><span data-stu-id="d9a5b-488">Documentation</span></span>

* [<span data-ttu-id="d9a5b-489">可交互对象</span><span class="sxs-lookup"><span data-stu-id="d9a5b-489">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d9a5b-490">Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="d9a5b-490">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="d9a5b-491">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="d9a5b-491">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d9a5b-492">语音输入</span><span class="sxs-lookup"><span data-stu-id="d9a5b-492">Voice input</span></span>](voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9a5b-493">工具和教程</span><span class="sxs-lookup"><span data-stu-id="d9a5b-493">Tools and tutorials</span></span>

* [<span data-ttu-id="d9a5b-494">混合现实工具包-UX</span><span class="sxs-lookup"><span data-stu-id="d9a5b-494">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="d9a5b-495">房间扫描</span><span class="sxs-lookup"><span data-stu-id="d9a5b-495">Room scanning</span></span>

<span data-ttu-id="d9a5b-496">需要空间映射数据的应用程序依赖于设备在一段时间内和跨会话自动收集此数据，因为用户浏览其环境中的设备处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-496">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="d9a5b-497">此数据的完整性和质量取决于多个因素，包括用户的探索量、从浏览开始起经过的时间，以及从设备扫描区域以来是否移动了家具和门等对象。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-497">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="d9a5b-498">许多应用程序会在体验开始时分析空间映射数据，以判断用户是否应执行额外的步骤来改善空间映射的完整性和质量。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-498">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="d9a5b-499">如果用户需要扫描环境，请在扫描体验期间提供明确的指南。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-499">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-500">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-500">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-502"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-502"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-503">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-503">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-504">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-504">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-505">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-505">Best</span></span>  |  <span data-ttu-id="d9a5b-506">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-506">Meets</span></span> |  <span data-ttu-id="d9a5b-507">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-507">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9a5b-508">空间网格的可视化通知用户正在进行扫描。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-508">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="d9a5b-509">用户清楚地了解要执行的操作以及扫描开始和停止的时间。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-509">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="d9a5b-510">已提供空间网格的可视化效果，但用户可能并不清楚地知道要执行什么操作，并且不会提供任何进度信息。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-510">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="d9a5b-511">没有网格的可视化效果。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-511">No visualization of mesh.</span></span> <span data-ttu-id="d9a5b-512">没有向用户提供有关在何处查找或开始扫描的指导信息。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-512">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-513">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-513">How to measure</span></span>

* <span data-ttu-id="d9a5b-514">在所需的空间扫描过程中，会提供视觉和音频指南，指示在何处进行查找以及何时开始和停止扫描。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-514">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-515">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-515">Recommendations</span></span>

* <span data-ttu-id="d9a5b-516">指示用户附近的用户总数需要成为体验的一部分。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-516">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="d9a5b-517">在扫描开始和停止（例如进度指示器）时进行通信。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-517">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="d9a5b-518">在扫描过程中使用网格的可视化效果。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-518">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="d9a5b-519">提供视觉和音频提示，以鼓励用户在房间内查找和移动。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-519">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="d9a5b-520">通知用户要在何处进行数据改进。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-520">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="d9a5b-521">在许多情况下，最好告诉用户需要执行的操作（例如，查看家具上的天花板），以便获得必要的扫描质量。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-521">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-522">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-522">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="d9a5b-523">文档</span><span class="sxs-lookup"><span data-stu-id="d9a5b-523">Documentation</span></span>

* [<span data-ttu-id="d9a5b-524">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="d9a5b-524">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="d9a5b-525">案例研究：扩展 HoloLens 的空间映射功能</span><span class="sxs-lookup"><span data-stu-id="d9a5b-525">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="d9a5b-526">案例研究： HoloTour 的空间音效设计</span><span class="sxs-lookup"><span data-stu-id="d9a5b-526">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="d9a5b-527">案例研究：在片段中创建沉浸式体验</span><span class="sxs-lookup"><span data-stu-id="d9a5b-527">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="d9a5b-528">工具和教程</span><span class="sxs-lookup"><span data-stu-id="d9a5b-528">Tools and tutorials</span></span>

* [<span data-ttu-id="d9a5b-529">混合现实工具包-UX</span><span class="sxs-lookup"><span data-stu-id="d9a5b-529">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="d9a5b-530">方向指示器</span><span class="sxs-lookup"><span data-stu-id="d9a5b-530">Directional indicators</span></span>

<span data-ttu-id="d9a5b-531">在混合现实应用中，内容可能在视图字段之外或由真实的对象封闭像素。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-531">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="d9a5b-532">设计良好的应用可使用户更轻松地查找不可见内容。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-532">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="d9a5b-533">方向指示器向用户提醒重要内容，并为内容提供与用户位置相关的指导。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-533">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="d9a5b-534">不可见内容的指南可以采用声音发射器、双向箭头或直接视觉提示的形式。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-534">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-535">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-535">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-537"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-537"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-538">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-538">✔️</span></span></td>
        <td><span data-ttu-id="d9a5b-539">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-539">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-540">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-540">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-541">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-541">Best</span></span>  |  <span data-ttu-id="d9a5b-542">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-542">Meets</span></span> |  <span data-ttu-id="d9a5b-543">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-543">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9a5b-544">视觉对象和音频提示直接指导用户查看视图外的相关内容。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-544">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="d9a5b-545">在内容的常规方向上指向用户的箭头或某个指示器。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-545">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="d9a5b-546">相关内容超出了视图的范围，用户未提供不良或无位置指南。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-546">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-547">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-547">How to measure</span></span>

* <span data-ttu-id="d9a5b-548">视图的 user 字段之外的相关内容可通过视觉对象和/或音频提示来发现。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-548">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-549">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-549">Recommendations</span></span>

* <span data-ttu-id="d9a5b-550">当相关内容在用户的 "视图" 字段之外时，请使用方向指示器和音频提示来引导用户使用内容。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-550">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="d9a5b-551">在许多情况下，可通过方向箭头首选直接直观的指南。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-551">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="d9a5b-552">方向指示器不应内置于游标中。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-552">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-553">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-553">Resources</span></span>

* [<span data-ttu-id="d9a5b-554">全息帧</span><span class="sxs-lookup"><span data-stu-id="d9a5b-554">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="d9a5b-555">数据加载</span><span class="sxs-lookup"><span data-stu-id="d9a5b-555">Data loading</span></span>

<span data-ttu-id="d9a5b-556">进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-556">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="d9a5b-557">这可能意味着，当进度指示器可见时，用户无法与应用程序交互，还可以指示等待时间的长短。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-557">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="d9a5b-558">设备影响</span><span class="sxs-lookup"><span data-stu-id="d9a5b-558">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d9a5b-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d9a5b-560"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d9a5b-560"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d9a5b-561">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-561">✔️</span></span></td>
        <td><span data-ttu-id="d9a5b-562">✔️</span><span class="sxs-lookup"><span data-stu-id="d9a5b-562">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="d9a5b-563">质量标准</span><span class="sxs-lookup"><span data-stu-id="d9a5b-563">Quality criteria</span></span>

|  <span data-ttu-id="d9a5b-564">确切</span><span class="sxs-lookup"><span data-stu-id="d9a5b-564">Best</span></span>  |  <span data-ttu-id="d9a5b-565">适合</span><span class="sxs-lookup"><span data-stu-id="d9a5b-565">Meets</span></span> |  <span data-ttu-id="d9a5b-566">失败</span><span class="sxs-lookup"><span data-stu-id="d9a5b-566">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="d9a5b-567">动画视觉对象指示器，其形式为进度栏或振铃，显示任何数据加载或处理过程中的进度。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-567">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="d9a5b-568">视觉对象指示器提供有关等待时间的指导。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-568">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="d9a5b-569">用户通知用户正在进行数据加载，但没有指示等待的时间。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-569">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="d9a5b-570">用于任务的数据加载或处理指示器超过5秒。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-570">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="d9a5b-571">如何度量</span><span class="sxs-lookup"><span data-stu-id="d9a5b-571">How to measure</span></span>

* <span data-ttu-id="d9a5b-572">在数据加载过程中，不会有超过5秒的空白状态。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-572">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="d9a5b-573">建议</span><span class="sxs-lookup"><span data-stu-id="d9a5b-573">Recommendations</span></span>

* <span data-ttu-id="d9a5b-574">当用户可能认为此应用已停止或崩溃时，提供一种 animator 的数据加载。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-574">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="d9a5b-575">合理的经验法则是任何可能需要5秒以上的 "正在进行" 的活动。</span><span class="sxs-lookup"><span data-stu-id="d9a5b-575">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="d9a5b-576">资源</span><span class="sxs-lookup"><span data-stu-id="d9a5b-576">Resources</span></span>

* [<span data-ttu-id="d9a5b-577">显示进度</span><span class="sxs-lookup"><span data-stu-id="d9a5b-577">Displaying progress</span></span>](progress.md)
