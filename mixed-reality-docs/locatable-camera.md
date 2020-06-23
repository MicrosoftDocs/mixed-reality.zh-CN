---
title: 可定位相机
description: 有关短期正面相机相机、工作原理以及开发人员可用的配置文件和分辨率的一般信息。
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: 照相机，hololens，彩色相机，正面朝，hololens 2，cv，计算机视觉，基准，标记，qr 码，qr，照片，视频
ms.openlocfilehash: e158eb2e708164cbd68620f3f46d3039c2eaa730
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216218"
---
# <a name="locatable-camera"></a><span data-ttu-id="db46d-104">可定位相机</span><span class="sxs-lookup"><span data-stu-id="db46d-104">Locatable camera</span></span>

<span data-ttu-id="db46d-105">HoloLens 包含在设备前面安装的面向世界的相机，使应用能够查看用户看到的内容。</span><span class="sxs-lookup"><span data-stu-id="db46d-105">HoloLens includes a world-facing camera mounted on the front of the device, which enables apps to see what the user sees.</span></span> <span data-ttu-id="db46d-106">开发人员可以访问和控制照相机，就像在 smartphone、笔记本或台式机上的彩色照相机一样。</span><span class="sxs-lookup"><span data-stu-id="db46d-106">Developers have access to and control of the camera, just as they would for color cameras on smartphones, portables, or desktops.</span></span> <span data-ttu-id="db46d-107">在 mobile 和 desktop 上工作的相同通用 windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)和 windows Media foundation Api 在 HoloLens 上工作。</span><span class="sxs-lookup"><span data-stu-id="db46d-107">The same universal windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) and windows media foundation APIs that work on mobile and desktop work on HoloLens.</span></span> <span data-ttu-id="db46d-108">Unity[还包装了这些 Windows api](locatable-camera-in-unity.md) ，以便在 HoloLens 上抽象地使用照相机的简单用法，例如拍摄定期照片和视频（有或没有全息影像）以及查找相机在场景中的位置和透视。</span><span class="sxs-lookup"><span data-stu-id="db46d-108">Unity [has also wrapped these windows APIs](locatable-camera-in-unity.md) to abstract simple usage of the camera on HoloLens for tasks such as taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.</span></span>

## <a name="device-camera-information"></a><span data-ttu-id="db46d-109">设备照相机信息</span><span class="sxs-lookup"><span data-stu-id="db46d-109">Device camera information</span></span>

### <a name="hololens-first-generation"></a><span data-ttu-id="db46d-110">HoloLens （第一代）</span><span class="sxs-lookup"><span data-stu-id="db46d-110">HoloLens (first-generation)</span></span>

* <span data-ttu-id="db46d-111">固定的照片/视频（PV）摄像机，具有自动白平衡、自动曝光和完整图像处理管道。</span><span class="sxs-lookup"><span data-stu-id="db46d-111">Fixed focus photo/video (PV) camera with auto white balance, auto exposure, and full image processing pipeline.</span></span>
* <span data-ttu-id="db46d-112">当照相机处于活动状态时，面向世界的白色隐私 LED 将发亮</span><span class="sxs-lookup"><span data-stu-id="db46d-112">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="db46d-113">摄像头支持以下模式（所有模式均为16:9 纵横比），其状态为30、24、20、15和 5 fps：</span><span class="sxs-lookup"><span data-stu-id="db46d-113">The camera supports the following modes (all modes are 16:9 aspect ratio) at 30, 24, 20, 15, and 5 fps:</span></span>

  |  <span data-ttu-id="db46d-114">视频</span><span class="sxs-lookup"><span data-stu-id="db46d-114">Video</span></span>  |  <span data-ttu-id="db46d-115">预览</span><span class="sxs-lookup"><span data-stu-id="db46d-115">Preview</span></span>  |  <span data-ttu-id="db46d-116">正常</span><span class="sxs-lookup"><span data-stu-id="db46d-116">Still</span></span>  |  <span data-ttu-id="db46d-117">视图的水平字段（FOV）</span><span class="sxs-lookup"><span data-stu-id="db46d-117">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="db46d-118">建议的用法</span><span class="sxs-lookup"><span data-stu-id="db46d-118">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|
  |  <span data-ttu-id="db46d-119">1280x720</span><span class="sxs-lookup"><span data-stu-id="db46d-119">1280x720</span></span> |  <span data-ttu-id="db46d-120">1280x720</span><span class="sxs-lookup"><span data-stu-id="db46d-120">1280x720</span></span> |  <span data-ttu-id="db46d-121">1280x720</span><span class="sxs-lookup"><span data-stu-id="db46d-121">1280x720</span></span> |  <span data-ttu-id="db46d-122">45deg</span><span class="sxs-lookup"><span data-stu-id="db46d-122">45deg</span></span>  |  <span data-ttu-id="db46d-123">（视频不稳定的默认模式）</span><span class="sxs-lookup"><span data-stu-id="db46d-123">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="db46d-124">空值</span><span class="sxs-lookup"><span data-stu-id="db46d-124">N/A</span></span> |  <span data-ttu-id="db46d-125">空值</span><span class="sxs-lookup"><span data-stu-id="db46d-125">N/A</span></span> |  <span data-ttu-id="db46d-126">2048x1152</span><span class="sxs-lookup"><span data-stu-id="db46d-126">2048x1152</span></span> |  <span data-ttu-id="db46d-127">67deg</span><span class="sxs-lookup"><span data-stu-id="db46d-127">67deg</span></span> |  <span data-ttu-id="db46d-128">最高分辨率静止图像</span><span class="sxs-lookup"><span data-stu-id="db46d-128">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="db46d-129">1408x792</span><span class="sxs-lookup"><span data-stu-id="db46d-129">1408x792</span></span> |  <span data-ttu-id="db46d-130">1408x792</span><span class="sxs-lookup"><span data-stu-id="db46d-130">1408x792</span></span> |  <span data-ttu-id="db46d-131">1408x792</span><span class="sxs-lookup"><span data-stu-id="db46d-131">1408x792</span></span> |  <span data-ttu-id="db46d-132">48deg</span><span class="sxs-lookup"><span data-stu-id="db46d-132">48deg</span></span> |  <span data-ttu-id="db46d-133">视频抖动之前的 Overscan （填充）分辨率</span><span class="sxs-lookup"><span data-stu-id="db46d-133">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="db46d-134">1344x756</span><span class="sxs-lookup"><span data-stu-id="db46d-134">1344x756</span></span> |  <span data-ttu-id="db46d-135">1344x756</span><span class="sxs-lookup"><span data-stu-id="db46d-135">1344x756</span></span> |  <span data-ttu-id="db46d-136">1344x756</span><span class="sxs-lookup"><span data-stu-id="db46d-136">1344x756</span></span> |  <span data-ttu-id="db46d-137">67deg</span><span class="sxs-lookup"><span data-stu-id="db46d-137">67deg</span></span> |  <span data-ttu-id="db46d-138">带有 overscan 的大型 FOV 视频模式</span><span class="sxs-lookup"><span data-stu-id="db46d-138">Large FOV video mode with overscan</span></span> | 
  |  <span data-ttu-id="db46d-139">896x504</span><span class="sxs-lookup"><span data-stu-id="db46d-139">896x504</span></span> |  <span data-ttu-id="db46d-140">896x504</span><span class="sxs-lookup"><span data-stu-id="db46d-140">896x504</span></span> |  <span data-ttu-id="db46d-141">896x504</span><span class="sxs-lookup"><span data-stu-id="db46d-141">896x504</span></span> |  <span data-ttu-id="db46d-142">48deg</span><span class="sxs-lookup"><span data-stu-id="db46d-142">48deg</span></span> |  <span data-ttu-id="db46d-143">图像处理任务的低功率/低分辨率模式</span><span class="sxs-lookup"><span data-stu-id="db46d-143">Low power / Low resolution mode for image processing tasks</span></span> | 

### <a name="hololens-2"></a><span data-ttu-id="db46d-144">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="db46d-144">HoloLens 2</span></span>

* <span data-ttu-id="db46d-145">自动将照片/视频（PV）摄像机与自动平衡、自动曝光和完整图像处理管道配合工作。</span><span class="sxs-lookup"><span data-stu-id="db46d-145">Auto-focus photo/video (PV) camera with auto white balance, auto exposure, and full image processing pipeline.</span></span>
* <span data-ttu-id="db46d-146">当照相机处于活动状态时，世界上的白色隐私 LED 将会亮起。</span><span class="sxs-lookup"><span data-stu-id="db46d-146">White Privacy LED facing the world will illuminate whenever the camera is active.</span></span>
* <span data-ttu-id="db46d-147">HoloLens 2 支持不同的相机配置文件。</span><span class="sxs-lookup"><span data-stu-id="db46d-147">HoloLens 2 supports different camera profiles.</span></span> <span data-ttu-id="db46d-148">了解如何[发现和选择相机功能](https://docs.microsoft.com//windows/uwp/audio-video-camera/camera-profiles)。</span><span class="sxs-lookup"><span data-stu-id="db46d-148">Learn how to [discover and select camera capabilities](https://docs.microsoft.com//windows/uwp/audio-video-camera/camera-profiles).</span></span>
* <span data-ttu-id="db46d-149">摄像头支持以下配置文件和分辨率（所有视频模式均为16:9 纵横比）：</span><span class="sxs-lookup"><span data-stu-id="db46d-149">The camera supports the following profiles and resolutions (all video modes are 16:9 aspect ratio):</span></span>
  
  | <span data-ttu-id="db46d-150">配置文件</span><span class="sxs-lookup"><span data-stu-id="db46d-150">Profile</span></span>                                         | <span data-ttu-id="db46d-151">视频</span><span class="sxs-lookup"><span data-stu-id="db46d-151">Video</span></span>     | <span data-ttu-id="db46d-152">预览</span><span class="sxs-lookup"><span data-stu-id="db46d-152">Preview</span></span>   | <span data-ttu-id="db46d-153">正常</span><span class="sxs-lookup"><span data-stu-id="db46d-153">Still</span></span>     | <span data-ttu-id="db46d-154">帧速率</span><span class="sxs-lookup"><span data-stu-id="db46d-154">Frame rates</span></span> | <span data-ttu-id="db46d-155">视图的水平字段（FOV）</span><span class="sxs-lookup"><span data-stu-id="db46d-155">Horizontal Field of View (H-FOV)</span></span> | <span data-ttu-id="db46d-156">建议的用法</span><span class="sxs-lookup"><span data-stu-id="db46d-156">Suggested usage</span></span>                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | <span data-ttu-id="db46d-157">旧，0 BalancedVideoAndPhoto，100</span><span class="sxs-lookup"><span data-stu-id="db46d-157">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="db46d-158">2272x1278</span><span class="sxs-lookup"><span data-stu-id="db46d-158">2272x1278</span></span> | <span data-ttu-id="db46d-159">2272x1278</span><span class="sxs-lookup"><span data-stu-id="db46d-159">2272x1278</span></span> |           | <span data-ttu-id="db46d-160">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-160">15,30</span></span>       | <span data-ttu-id="db46d-161">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-161">64.69</span></span>                            | <span data-ttu-id="db46d-162">高质量视频录制</span><span class="sxs-lookup"><span data-stu-id="db46d-162">High quality video recording</span></span>                |
  | <span data-ttu-id="db46d-163">旧，0 BalancedVideoAndPhoto，100</span><span class="sxs-lookup"><span data-stu-id="db46d-163">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="db46d-164">896x504</span><span class="sxs-lookup"><span data-stu-id="db46d-164">896x504</span></span>   | <span data-ttu-id="db46d-165">896x504</span><span class="sxs-lookup"><span data-stu-id="db46d-165">896x504</span></span>   |           | <span data-ttu-id="db46d-166">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-166">15,30</span></span>       | <span data-ttu-id="db46d-167">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-167">64.69</span></span>                            | <span data-ttu-id="db46d-168">用于高质量照片捕获的预览流</span><span class="sxs-lookup"><span data-stu-id="db46d-168">Preview stream for high quality photo capture</span></span> |
  | <span data-ttu-id="db46d-169">旧，0 BalancedVideoAndPhoto，100</span><span class="sxs-lookup"><span data-stu-id="db46d-169">Legacy,0  BalancedVideoAndPhoto,100</span></span>             |           |           | <span data-ttu-id="db46d-170">3904x2196</span><span class="sxs-lookup"><span data-stu-id="db46d-170">3904x2196</span></span> |             | <span data-ttu-id="db46d-171">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-171">64.69</span></span>                            | <span data-ttu-id="db46d-172">优质照片捕获</span><span class="sxs-lookup"><span data-stu-id="db46d-172">High quality photo capture</span></span>                  |
  | <span data-ttu-id="db46d-173">BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-173">BalancedVideoAndPhoto,120</span></span>                       | <span data-ttu-id="db46d-174">1952x1100</span><span class="sxs-lookup"><span data-stu-id="db46d-174">1952x1100</span></span> | <span data-ttu-id="db46d-175">1952x1100</span><span class="sxs-lookup"><span data-stu-id="db46d-175">1952x1100</span></span> | <span data-ttu-id="db46d-176">1952x1100</span><span class="sxs-lookup"><span data-stu-id="db46d-176">1952x1100</span></span> | <span data-ttu-id="db46d-177">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-177">15,30</span></span>       | <span data-ttu-id="db46d-178">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-178">64.69</span></span>                            | <span data-ttu-id="db46d-179">长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-179">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="db46d-180">BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-180">BalancedVideoAndPhoto,120</span></span>                       | <span data-ttu-id="db46d-181">1504x846</span><span class="sxs-lookup"><span data-stu-id="db46d-181">1504x846</span></span>  | <span data-ttu-id="db46d-182">1504x846</span><span class="sxs-lookup"><span data-stu-id="db46d-182">1504x846</span></span>  |           | <span data-ttu-id="db46d-183">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-183">15,30</span></span>       | <span data-ttu-id="db46d-184">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-184">64.69</span></span>                            | <span data-ttu-id="db46d-185">长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-185">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="db46d-186">视频会议，100</span><span class="sxs-lookup"><span data-stu-id="db46d-186">VideoConferencing,100</span></span>                           | <span data-ttu-id="db46d-187">1952x1100</span><span class="sxs-lookup"><span data-stu-id="db46d-187">1952x1100</span></span> | <span data-ttu-id="db46d-188">1952x1100</span><span class="sxs-lookup"><span data-stu-id="db46d-188">1952x1100</span></span> | <span data-ttu-id="db46d-189">1952x1100</span><span class="sxs-lookup"><span data-stu-id="db46d-189">1952x1100</span></span> | <span data-ttu-id="db46d-190">15、30、60</span><span class="sxs-lookup"><span data-stu-id="db46d-190">15,30,60</span></span>    | <span data-ttu-id="db46d-191">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-191">64.69</span></span>                            | <span data-ttu-id="db46d-192">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-192">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="db46d-193">视频会议，100</span><span class="sxs-lookup"><span data-stu-id="db46d-193">Videoconferencing,100</span></span>                           | <span data-ttu-id="db46d-194">1504x846</span><span class="sxs-lookup"><span data-stu-id="db46d-194">1504x846</span></span>  | <span data-ttu-id="db46d-195">1504x846</span><span class="sxs-lookup"><span data-stu-id="db46d-195">1504x846</span></span>  |           | <span data-ttu-id="db46d-196">5、15、30、60</span><span class="sxs-lookup"><span data-stu-id="db46d-196">5,15,30,60</span></span>  | <span data-ttu-id="db46d-197">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-197">64.69</span></span>                            | <span data-ttu-id="db46d-198">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-198">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="db46d-199">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-199">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="db46d-200">1920x1080</span><span class="sxs-lookup"><span data-stu-id="db46d-200">1920x1080</span></span> | <span data-ttu-id="db46d-201">1920x1080</span><span class="sxs-lookup"><span data-stu-id="db46d-201">1920x1080</span></span> | <span data-ttu-id="db46d-202">1920x1080</span><span class="sxs-lookup"><span data-stu-id="db46d-202">1920x1080</span></span> | <span data-ttu-id="db46d-203">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-203">15,30</span></span>       | <span data-ttu-id="db46d-204">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-204">64.69</span></span>                            | <span data-ttu-id="db46d-205">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-205">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="db46d-206">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-206">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="db46d-207">1280x720</span><span class="sxs-lookup"><span data-stu-id="db46d-207">1280x720</span></span>  | <span data-ttu-id="db46d-208">1280x720</span><span class="sxs-lookup"><span data-stu-id="db46d-208">1280x720</span></span>  | <span data-ttu-id="db46d-209">1280x720</span><span class="sxs-lookup"><span data-stu-id="db46d-209">1280x720</span></span>  | <span data-ttu-id="db46d-210">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-210">15,30</span></span>       | <span data-ttu-id="db46d-211">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-211">64.69</span></span>                            | <span data-ttu-id="db46d-212">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-212">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="db46d-213">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-213">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="db46d-214">1128x636</span><span class="sxs-lookup"><span data-stu-id="db46d-214">1128x636</span></span>  |           |           | <span data-ttu-id="db46d-215">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-215">15,30</span></span>       | <span data-ttu-id="db46d-216">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-216">64.69</span></span>                            | <span data-ttu-id="db46d-217">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-217">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="db46d-218">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-218">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="db46d-219">960x540</span><span class="sxs-lookup"><span data-stu-id="db46d-219">960x540</span></span>   |           |           | <span data-ttu-id="db46d-220">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-220">15,30</span></span>       | <span data-ttu-id="db46d-221">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-221">64.69</span></span>                            | <span data-ttu-id="db46d-222">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-222">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="db46d-223">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-223">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="db46d-224">760x428</span><span class="sxs-lookup"><span data-stu-id="db46d-224">760x428</span></span>   |           |           | <span data-ttu-id="db46d-225">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-225">15,30</span></span>       | <span data-ttu-id="db46d-226">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-226">64.69</span></span>                            | <span data-ttu-id="db46d-227">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-227">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="db46d-228">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-228">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="db46d-229">640x360</span><span class="sxs-lookup"><span data-stu-id="db46d-229">640x360</span></span>   |           |           | <span data-ttu-id="db46d-230">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-230">15,30</span></span>       | <span data-ttu-id="db46d-231">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-231">64.69</span></span>                            | <span data-ttu-id="db46d-232">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-232">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="db46d-233">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-233">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="db46d-234">500x282</span><span class="sxs-lookup"><span data-stu-id="db46d-234">500x282</span></span>   |           |           | <span data-ttu-id="db46d-235">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-235">15,30</span></span>       | <span data-ttu-id="db46d-236">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-236">64.69</span></span>                            | <span data-ttu-id="db46d-237">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-237">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="db46d-238">视频会议，100 BalancedVideoAndPhoto，120</span><span class="sxs-lookup"><span data-stu-id="db46d-238">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="db46d-239">424x240</span><span class="sxs-lookup"><span data-stu-id="db46d-239">424x240</span></span>   |           |           | <span data-ttu-id="db46d-240">15、30</span><span class="sxs-lookup"><span data-stu-id="db46d-240">15,30</span></span>       | <span data-ttu-id="db46d-241">64.69</span><span class="sxs-lookup"><span data-stu-id="db46d-241">64.69</span></span>                            | <span data-ttu-id="db46d-242">视频会议，长持续时间方案</span><span class="sxs-lookup"><span data-stu-id="db46d-242">Video conferencing, long duration scenarios</span></span> |

>[!NOTE]
><span data-ttu-id="db46d-243">客户可以利用[混合现实捕获](mixed-reality-capture.md)来获取应用的视频或照片，其中包括全息影像和视频抖动。</span><span class="sxs-lookup"><span data-stu-id="db46d-243">Customers can leverage [mixed reality capture](mixed-reality-capture.md) to take videos or photos of your app, which include holograms and video stabilization.</span></span>
>
><span data-ttu-id="db46d-244">作为开发人员，如果你希望在客户捕获内容时能够更好地显示你的应用程序，请考虑创建应用程序时应考虑的一些事项。</span><span class="sxs-lookup"><span data-stu-id="db46d-244">As a developer, there are considerations you should take into account when creating your app if you want it to look as good as possible when a customer captures content.</span></span> <span data-ttu-id="db46d-245">你还可以直接在应用中启用（和自定义）混合现实捕获。</span><span class="sxs-lookup"><span data-stu-id="db46d-245">You can also enable (and customize) mixed reality capture from directly within your app.</span></span> <span data-ttu-id="db46d-246">在[混合现实捕获](mixed-reality-capture-for-developers.md)中了解更多开发人员。</span><span class="sxs-lookup"><span data-stu-id="db46d-246">Learn more at [mixed reality capture for developers](mixed-reality-capture-for-developers.md).</span></span>

## <a name="locating-the-device-camera-in-the-world"></a><span data-ttu-id="db46d-247">在世界各地查找设备照相机</span><span class="sxs-lookup"><span data-stu-id="db46d-247">Locating the Device Camera in the World</span></span>

<span data-ttu-id="db46d-248">当 HoloLens 拍摄照片和视频时，捕获的帧包括世界上相机的位置以及照相机的镜头型号。</span><span class="sxs-lookup"><span data-stu-id="db46d-248">When HoloLens takes photos and videos, the captured frames include the location of the camera in the world, as well as the lens model of the camera.</span></span> <span data-ttu-id="db46d-249">这样，应用程序就可以在现实世界中为补充式的图像处理方案提供有关相机位置的原因。</span><span class="sxs-lookup"><span data-stu-id="db46d-249">This allows applications to reason about the position of the camera in the real world for augmented imaging scenarios.</span></span> <span data-ttu-id="db46d-250">开发人员可以使用他们最喜爱的图像处理或自定义计算机视觉库，创造性地滚动自己的方案。</span><span class="sxs-lookup"><span data-stu-id="db46d-250">Developers can creatively roll their own scenarios using their favorite image processing or custom computer vision libraries.</span></span>

<span data-ttu-id="db46d-251">HoloLens 文档中其他地方的 "照相机" 可能指的是 "虚拟游戏相机" （应用呈现到的截锥）。</span><span class="sxs-lookup"><span data-stu-id="db46d-251">"Camera" elsewhere in HoloLens documentation may refer to the "virtual game camera" (the frustum the app renders to).</span></span> <span data-ttu-id="db46d-252">除非另有指示，否则，此页上的 "照相机" 指的是实际的 RGB 颜色相机。</span><span class="sxs-lookup"><span data-stu-id="db46d-252">Unless denoted otherwise, "camera" on this page refers to the real-world RGB color camera.</span></span>

### <a name="using-unity"></a><span data-ttu-id="db46d-253">使用 Unity</span><span class="sxs-lookup"><span data-stu-id="db46d-253">Using Unity</span></span>

<span data-ttu-id="db46d-254">若要从 "CameraIntrinsics" 和 "CameraCoordinateSystem" 中转到应用程序/全球坐标系统，请按照[Unity 中](locatable-camera-in-unity.md)的可定位照相机一文中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="db46d-254">To go from the 'CameraIntrinsics' and 'CameraCoordinateSystem' to your application/world coordinate system, follow the instructions in the [Locatable camera in Unity](locatable-camera-in-unity.md) article.</span></span>  <span data-ttu-id="db46d-255">CameraToWorldMatrix 由 PhotoCaptureFrame 类自动提供，因此你无需担心下面讨论的 CameraCoordinateSystem 转换。</span><span class="sxs-lookup"><span data-stu-id="db46d-255">CameraToWorldMatrix is automatically provided by PhotoCaptureFrame class, and so you don't need to worry about the CameraCoordinateSystem transforms discussed below.</span></span>

### <a name="using-mediaframereference"></a><span data-ttu-id="db46d-256">使用 MediaFrameReference</span><span class="sxs-lookup"><span data-stu-id="db46d-256">Using MediaFrameReference</span></span>

<span data-ttu-id="db46d-257">如果使用[MediaFrameReference](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference)类从照相机读取图像帧，则会应用这些说明。</span><span class="sxs-lookup"><span data-stu-id="db46d-257">These instructions apply if you are using the [MediaFrameReference](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference) class to read image frames from the camera.</span></span>

<span data-ttu-id="db46d-258">每个图像帧（无论是照片还是视频）在捕获时都包含[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem)的根，可以使用[MediaFrameReference](https://docs.microsoft.com//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)的[坐标系](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)属性访问。</span><span class="sxs-lookup"><span data-stu-id="db46d-258">Each image frame (whether photo or video) includes a [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) rooted at the camera at the time of capture, which can be accessed using the [CoordinateSystem](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) property of your [MediaFrameReference](https://docs.microsoft.com//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference).</span></span> <span data-ttu-id="db46d-259">此外，每个帧都包含对相机镜头型号的说明，可在[CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)属性中找到。</span><span class="sxs-lookup"><span data-stu-id="db46d-259">In addition, each frame contains a description of the camera lens model, which can be found in the [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) property.</span></span> <span data-ttu-id="db46d-260">这些转换一起为每个像素定义了三维空间中的射线，表示生成像素的 photons 所采用的路径。</span><span class="sxs-lookup"><span data-stu-id="db46d-260">Together, these transforms define for each pixel a ray in 3D space representing the path taken by the photons that produced the pixel.</span></span> <span data-ttu-id="db46d-261">通过获取从帧的坐标系统到某个其他坐标系统的转换（例如从[固定的参考框架](coordinate-systems.md#stationary-frame-of-reference)中），可以将这些光线与应用程序中的其他内容相关。</span><span class="sxs-lookup"><span data-stu-id="db46d-261">These rays can be related to other content in the app by obtaining the transform from the frame's coordinate system to some other coordinate system (e.g. from a [stationary frame of reference](coordinate-systems.md#stationary-frame-of-reference)).</span></span> <span data-ttu-id="db46d-262">总而言之，每个图像框架提供以下内容：</span><span class="sxs-lookup"><span data-stu-id="db46d-262">To summarize, each image frame provides the following:</span></span>
* <span data-ttu-id="db46d-263">像素数据（以 RGB/NV12/JPEG/etc 格式）</span><span class="sxs-lookup"><span data-stu-id="db46d-263">Pixel Data (in RGB/NV12/JPEG/etc. format)</span></span>
* <span data-ttu-id="db46d-264">捕获位置的[SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem)</span><span class="sxs-lookup"><span data-stu-id="db46d-264">A [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) from the location of capture</span></span>
* <span data-ttu-id="db46d-265">包含照相机镜头模式的[CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics)类</span><span class="sxs-lookup"><span data-stu-id="db46d-265">A [CameraIntrinsics](https://docs.microsoft.com//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) class containing the lens mode of the camera</span></span>

<span data-ttu-id="db46d-266">[HolographicFaceTracking 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)演示了查询照相机坐标系统和自己的应用程序坐标系统之间的转换的相当直接的方法。</span><span class="sxs-lookup"><span data-stu-id="db46d-266">The [HolographicFaceTracking sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) shows the fairly straightforward way to query for the transform between the camera's coordinate system and your own application coordinate systems.</span></span>

### <a name="using-media-foundation"></a><span data-ttu-id="db46d-267">使用媒体基础</span><span class="sxs-lookup"><span data-stu-id="db46d-267">Using Media Foundation</span></span>

<span data-ttu-id="db46d-268">如果使用媒体基础直接从照相机读取图像帧，则可以使用每个帧的[MFSampleExtension_CameraExtrinsics 属性](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-cameraextrinsics)和[MFSampleExtension_PinholeCameraIntrinsics 特性](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics)来相对于应用程序的其他坐标系统定位相机帧，如下面的示例代码所示：</span><span class="sxs-lookup"><span data-stu-id="db46d-268">If you are using Media Foundation directly to read image frames from the camera, you can use each frame's [MFSampleExtension_CameraExtrinsics attribute](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-cameraextrinsics) and [MFSampleExtension_PinholeCameraIntrinsics attribute](https://docs.microsoft.com/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) to locate camera frames relative to your application's other coordinate systems, as shown in this sample code:</span></span>

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a><span data-ttu-id="db46d-269">失真错误</span><span class="sxs-lookup"><span data-stu-id="db46d-269">Distortion Error</span></span>

<span data-ttu-id="db46d-270">在 HoloLens 上，视频和静态图像流在系统的图像处理管道中 undistorted，然后才能将帧提供给应用程序（预览流包含原始扭曲帧）。</span><span class="sxs-lookup"><span data-stu-id="db46d-270">On HoloLens, the video and still image streams are undistorted in the system's image processing pipeline before the frames are made available to the application (the preview stream contains the original distorted frames).</span></span> <span data-ttu-id="db46d-271">由于只有 CameraIntrinsics 可用，因此应用程序必须假定图像帧表示完美的 pinhole 相机。</span><span class="sxs-lookup"><span data-stu-id="db46d-271">Because only the CameraIntrinsics are made available, applications must assume image frames represent a perfect pinhole camera.</span></span>

<span data-ttu-id="db46d-272">在 HoloLens （第一代）上，在帧元数据中使用 CameraIntrinsics 时，图像处理器中的 undistortion 函数可能仍会导致最多10个像素的错误。</span><span class="sxs-lookup"><span data-stu-id="db46d-272">On HoloLens (first-generation), the undistortion function in the image processor may still leave an error of up to 10 pixels when using the CameraIntrinsics in the frame metadata.</span></span> <span data-ttu-id="db46d-273">在许多用例中，此错误并不重要，但如果将全息影像与真实的海报/标记对齐，则会注意到 <的10px 偏移（大约11mm，对于离2米的全息影像），这可能导致此扭曲错误。</span><span class="sxs-lookup"><span data-stu-id="db46d-273">In many use cases, this error will not matter, but if you are aligning holograms to real world posters/markers, for example, and you notice a <10px offset (roughly 11mm for holograms positioned 2 meters away), this distortion error could be the cause.</span></span> 

## <a name="locatable-camera-usage-scenarios"></a><span data-ttu-id="db46d-274">定位照相机使用方案</span><span class="sxs-lookup"><span data-stu-id="db46d-274">Locatable Camera Usage Scenarios</span></span>

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a><span data-ttu-id="db46d-275">在捕获照片或视频的世界中显示照片或视频</span><span class="sxs-lookup"><span data-stu-id="db46d-275">Show a photo or video in the world where it was captured</span></span>

<span data-ttu-id="db46d-276">设备照相机帧附带了 "相机到世界" 转换，可用于显示在拍摄映像时设备的确切位置。</span><span class="sxs-lookup"><span data-stu-id="db46d-276">The Device Camera frames come with a "Camera To World" transform, that can be used to show exactly where the device was when the image was taken.</span></span> <span data-ttu-id="db46d-277">例如，你可以在此位置（CameraToWorld. MultiplyPoint （System.numerics.vector2））放置一个小全息图标，甚至可以在相机面对的方向（CameraToWorld. MultiplyVector （System.numerics.vector2））中绘制一个小箭头。</span><span class="sxs-lookup"><span data-stu-id="db46d-277">For example, you could position a small holographic icon at this location (CameraToWorld.MultiplyPoint(Vector3.zero)) and even draw a little arrow in the direction that the camera was facing (CameraToWorld.MultiplyVector(Vector3.forward)).</span></span>

### <a name="tag--pattern--poster--object-tracking"></a><span data-ttu-id="db46d-278">标记/模式/海报/对象跟踪</span><span class="sxs-lookup"><span data-stu-id="db46d-278">Tag / Pattern / Poster / Object Tracking</span></span>

<span data-ttu-id="db46d-279">许多混合现实应用程序使用可识别的图像或视觉模式在空间中创建以可跟踪点。</span><span class="sxs-lookup"><span data-stu-id="db46d-279">Many mixed reality applications use a recognizable image or visual pattern to create a trackable point in space.</span></span> <span data-ttu-id="db46d-280">然后，使用该对象相对于该点呈现对象，或创建一个已知位置。</span><span class="sxs-lookup"><span data-stu-id="db46d-280">This is then used to render objects relative to that point or create a known location.</span></span> <span data-ttu-id="db46d-281">某些情况下，HoloLens 包括查找用 fiducials 标记的真实世界对象（例如，带有 QR 码的电视显示器），通过 fiducials 放置全息影像，并与使用已设置为通过 Wi-fi 进行 HoloLens 通信的非 HoloLens 设备（如平板电脑）直观配对。</span><span class="sxs-lookup"><span data-stu-id="db46d-281">Some uses for HoloLens include finding a real world object tagged with fiducials (e.g. a TV monitor with a QR code), placing holograms over fiducials, and visually pairing with non-HoloLens devices like tablets that have been setup to communicate with HoloLens via Wi-Fi.</span></span>

<span data-ttu-id="db46d-282">若要识别可视模式，然后将该对象放在应用程序的世界空间中，需要执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="db46d-282">To recognize a visual pattern, and then place that object in the applications world space, you'll need a few things:</span></span>
1. <span data-ttu-id="db46d-283">图像模式识别工具包，如 QR 码、AR 标记、面部查找器、圆形跟踪器、OCR 等。</span><span class="sxs-lookup"><span data-stu-id="db46d-283">An image pattern recognition toolkit, such as QR code, AR tags, face finder, circle trackers, OCR etc.</span></span>
2. <span data-ttu-id="db46d-284">在运行时收集图像帧，并将其传递到识别层</span><span class="sxs-lookup"><span data-stu-id="db46d-284">Collect image frames at runtime, and pass them to the recognition layer</span></span>
3. <span data-ttu-id="db46d-285">将其图像位置 Unproject 为世界位置，或可能是世界光线。</span><span class="sxs-lookup"><span data-stu-id="db46d-285">Unproject their image locations back into world positions, or likely world rays.</span></span> 
4. <span data-ttu-id="db46d-286">将虚拟模型放置在这些世界位置</span><span class="sxs-lookup"><span data-stu-id="db46d-286">Position your virtual models over these world locations</span></span>

<span data-ttu-id="db46d-287">一些重要的图像处理链接：</span><span class="sxs-lookup"><span data-stu-id="db46d-287">Some important image processing links:</span></span>
* [<span data-ttu-id="db46d-288">OpenCV</span><span class="sxs-lookup"><span data-stu-id="db46d-288">OpenCV</span></span>](https://opencv.org/)
* [<span data-ttu-id="db46d-289">QR 标记</span><span class="sxs-lookup"><span data-stu-id="db46d-289">QR Tags</span></span>](https://en.wikipedia.org/wiki/QR_code)
* [<span data-ttu-id="db46d-290">FaceSDK</span><span class="sxs-lookup"><span data-stu-id="db46d-290">FaceSDK</span></span>](https://research.microsoft.com/projects/facesdk/)
* [<span data-ttu-id="db46d-291">Microsoft Translator</span><span class="sxs-lookup"><span data-stu-id="db46d-291">Microsoft Translator</span></span>](https://www.microsoft.com/translator/business)

<span data-ttu-id="db46d-292">保持交互应用程序帧速率非常重要，尤其是在处理长时间运行的图像识别算法时。</span><span class="sxs-lookup"><span data-stu-id="db46d-292">Keeping an interactive application frame-rate is critical, especially when dealing with long-running image recognition algorithms.</span></span> <span data-ttu-id="db46d-293">出于此原因，我们通常使用以下模式：</span><span class="sxs-lookup"><span data-stu-id="db46d-293">For this reason, we commonly use the following pattern:</span></span>
1. <span data-ttu-id="db46d-294">主线程：管理照相机对象</span><span class="sxs-lookup"><span data-stu-id="db46d-294">Main Thread: manages the camera object</span></span>
2. <span data-ttu-id="db46d-295">主线程：请求新帧（异步）</span><span class="sxs-lookup"><span data-stu-id="db46d-295">Main Thread: requests new frames (async)</span></span>
3. <span data-ttu-id="db46d-296">主线程：将新帧传递到跟踪线程</span><span class="sxs-lookup"><span data-stu-id="db46d-296">Main Thread: pass new frames to tracking thread</span></span>
4. <span data-ttu-id="db46d-297">跟踪线程：处理收集关键点的图像</span><span class="sxs-lookup"><span data-stu-id="db46d-297">Tracking Thread: processes image to collect key points</span></span>
5. <span data-ttu-id="db46d-298">主线程：移动虚拟模型以匹配找到的关键点</span><span class="sxs-lookup"><span data-stu-id="db46d-298">Main Thread: moves virtual model to match found key points</span></span>
6. <span data-ttu-id="db46d-299">主线程：从步骤2重复</span><span class="sxs-lookup"><span data-stu-id="db46d-299">Main Thread: repeat from step 2</span></span>

<span data-ttu-id="db46d-300">某些图像标记系统仅提供单个像素位置（其他在这种情况下将不需要此部分），这相当于可能的位置。</span><span class="sxs-lookup"><span data-stu-id="db46d-300">Some image marker systems only provide a single pixel location (others provide the full transform in which case this section will not be needed), which equates to a ray of possible locations.</span></span> <span data-ttu-id="db46d-301">若要访问单个3d 位置，我们可以利用多个射线，并按大致交集查找最终结果。</span><span class="sxs-lookup"><span data-stu-id="db46d-301">To get to a single 3d location, we can then leverage multiple rays and find the final result by their approximate intersection.</span></span> <span data-ttu-id="db46d-302">为此需要：</span><span class="sxs-lookup"><span data-stu-id="db46d-302">To do this, you'll need to:</span></span>
1. <span data-ttu-id="db46d-303">获取正在收集多个照相机图像的循环</span><span class="sxs-lookup"><span data-stu-id="db46d-303">Get a loop going collecting multiple camera images</span></span>
2. <span data-ttu-id="db46d-304">查找关联的功能点及其世界光线</span><span class="sxs-lookup"><span data-stu-id="db46d-304">Find the associated feature points, and their world rays</span></span>
3. <span data-ttu-id="db46d-305">如果有一个功能字典，每个功能都有多个世界光线，则可以使用以下代码来解决这些光线的交集：</span><span class="sxs-lookup"><span data-stu-id="db46d-305">When you have a dictionary of features, each with multiple world rays, you can use the following code to solve for the intersection of those rays:</span></span>

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

<span data-ttu-id="db46d-306">如果有两个或多个跟踪标记位置，则可以将建模场景定位到适合用户的当前方案。</span><span class="sxs-lookup"><span data-stu-id="db46d-306">Given two or more tracked tag locations, you can position a modelled scene to fit the user's current scenario.</span></span> <span data-ttu-id="db46d-307">如果无法假定重心，则需要三个标记位置。</span><span class="sxs-lookup"><span data-stu-id="db46d-307">If you can't assume gravity, then you'll need three tag locations.</span></span> <span data-ttu-id="db46d-308">在许多情况下，我们使用简单的配色方案，其中白色球体表示实时跟踪的标记位置，蓝色球体表示建模标记位置。</span><span class="sxs-lookup"><span data-stu-id="db46d-308">In many cases, we use a simple color scheme where white spheres represent real-time tracked tag locations, and blue spheres represent modelled tag locations.</span></span> <span data-ttu-id="db46d-309">这允许用户以直观方式衡量对齐质量。</span><span class="sxs-lookup"><span data-stu-id="db46d-309">This allows the user to visually gauge the alignment quality.</span></span> <span data-ttu-id="db46d-310">我们假定在所有应用程序中都进行以下设置：</span><span class="sxs-lookup"><span data-stu-id="db46d-310">We assume the following setup in all our applications:</span></span>
* <span data-ttu-id="db46d-311">两个或多个建模标记位置</span><span class="sxs-lookup"><span data-stu-id="db46d-311">Two or more modelled tag locations</span></span>
* <span data-ttu-id="db46d-312">场景中的一个 "校准空间" 是标记的父项</span><span class="sxs-lookup"><span data-stu-id="db46d-312">One 'calibration space' which in the scene is the parent of the tags</span></span>
* <span data-ttu-id="db46d-313">相机功能标识符</span><span class="sxs-lookup"><span data-stu-id="db46d-313">Camera feature identifier</span></span>
* <span data-ttu-id="db46d-314">移动校准空间以便使建模标记与实时标记对齐的行为（我们小心地移动父空间，而不是建模标记本身，因为其他连接是相对于它们的位置）。</span><span class="sxs-lookup"><span data-stu-id="db46d-314">Behavior which moves the calibration space to align the modelled tags with the real-time tags (we are careful to move the parent space, not the modelled markers themselves, because other connect is positions relative to them).</span></span>

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a><span data-ttu-id="db46d-315">使用 Led 或其他识别器库跟踪或确定标记为静止或移动现实世界对象/面部</span><span class="sxs-lookup"><span data-stu-id="db46d-315">Track or Identify Tagged Stationary or Moving real-world objects/faces using LEDs or other recognizer libraries</span></span>

<span data-ttu-id="db46d-316">示例：</span><span class="sxs-lookup"><span data-stu-id="db46d-316">Examples:</span></span>
* <span data-ttu-id="db46d-317">带有 Led 的工业机器人（或用于缓慢移动对象的 QR 码）</span><span class="sxs-lookup"><span data-stu-id="db46d-317">Industrial robots with LEDs (or QR codes for slower moving objects)</span></span>
* <span data-ttu-id="db46d-318">标识并识别房间中的对象</span><span class="sxs-lookup"><span data-stu-id="db46d-318">Identify and recognize objects in the room</span></span>
* <span data-ttu-id="db46d-319">确定并识别房间中的人员（例如，在人脸上放置全息的联系人卡片）</span><span class="sxs-lookup"><span data-stu-id="db46d-319">Identify and recognize people in the room (e.g. place holographic contact cards over faces)</span></span>

## <a name="see-also"></a><span data-ttu-id="db46d-320">请参阅</span><span class="sxs-lookup"><span data-stu-id="db46d-320">See also</span></span>
* [<span data-ttu-id="db46d-321">定位相机示例</span><span class="sxs-lookup"><span data-stu-id="db46d-321">Locatable camera sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [<span data-ttu-id="db46d-322">Unity 中的可定位相机</span><span class="sxs-lookup"><span data-stu-id="db46d-322">Locatable camera in Unity</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="db46d-323">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="db46d-323">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="db46d-324">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="db46d-324">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="db46d-325">媒体捕获简介</span><span class="sxs-lookup"><span data-stu-id="db46d-325">Media capture introduction</span></span>](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
* [<span data-ttu-id="db46d-326">全息面部跟踪示例</span><span class="sxs-lookup"><span data-stu-id="db46d-326">Holographic face tracking sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
