---
title: 可定位照相机
description: 有关 HoloLens 前面向摄像头的常规信息。
author: wguyman
ms.author: wguyman
ms.date: 02/24/2019
ms.topic: article
keywords: 相机、 hololens，颜色照相机前端面向
ms.openlocfilehash: ffcd6faf15dd8556db393237d468a3cdf60e4bdb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592742"
---
# <a name="locatable-camera"></a><span data-ttu-id="7f250-104">可定位照相机</span><span class="sxs-lookup"><span data-stu-id="7f250-104">Locatable camera</span></span>

<span data-ttu-id="7f250-105">HoloLens 包括设备这能使应用程序以查看用户看到的内容的正面上装载了世界摄像头。</span><span class="sxs-lookup"><span data-stu-id="7f250-105">HoloLens includes a world-facing camera mounted on the front of the device which enables apps to see what the user sees.</span></span> <span data-ttu-id="7f250-106">开发人员有权访问和控制的照相机就像用于智能手机、 笔记本或台式机上的颜色相机。</span><span class="sxs-lookup"><span data-stu-id="7f250-106">Developers have access to and control of the camera just as they would for color cameras on smartphones, portables, or desktops.</span></span> <span data-ttu-id="7f250-107">相同的通用 windows[媒体捕获](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)，在 HoloLens 上的 windows media foundation Api 适用于移动和桌面工作。</span><span class="sxs-lookup"><span data-stu-id="7f250-107">The same universal windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) and windows media foundation APIs that work on mobile and desktop work on HoloLens.</span></span> <span data-ttu-id="7f250-108">Unity[也具有包装这些 windows Api](locatable-camera-in-unity.md)抽象 HoloLens 的任务，例如正则照片和视频 （有或没有全息） 并在查找中的照相机的位置和角度来看的照相机的简单用法场景。</span><span class="sxs-lookup"><span data-stu-id="7f250-108">Unity [has also wrapped these windows APIs](locatable-camera-in-unity.md) to abstract simple usage of the camera on HoloLens for tasks such as taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.</span></span>

## <a name="device-camera-information"></a><span data-ttu-id="7f250-109">设备相机信息</span><span class="sxs-lookup"><span data-stu-id="7f250-109">Device camera information</span></span>

### <a name="hololens-first-generation"></a><span data-ttu-id="7f250-110">HoloLens （第一代）</span><span class="sxs-lookup"><span data-stu-id="7f250-110">HoloLens (first-generation)</span></span>

* <span data-ttu-id="7f250-111">固定的焦点照片/视频 (PV) 摄像机，白色自动平衡、 自动公开与完整的映像处理管道</span><span class="sxs-lookup"><span data-stu-id="7f250-111">Fixed focus photo/video (PV) camera, with auto white balance, auto exposure, and full image processing pipe</span></span>
* <span data-ttu-id="7f250-112">面向全球的白色隐私发光二极管会只要照相机处于活动状态</span><span class="sxs-lookup"><span data-stu-id="7f250-112">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="7f250-113">照相机支持在 30、 24、 20、 15 和 5 帧/秒 （所有模式都都纵横比为 16:9） 的以下模式：</span><span class="sxs-lookup"><span data-stu-id="7f250-113">The camera supports the following modes (all modes are 16:9 aspect ratio) at 30, 24, 20, 15, and 5 fps:</span></span>

  |  <span data-ttu-id="7f250-114">视频</span><span class="sxs-lookup"><span data-stu-id="7f250-114">Video</span></span>  |  <span data-ttu-id="7f250-115">预览</span><span class="sxs-lookup"><span data-stu-id="7f250-115">Preview</span></span>  |  <span data-ttu-id="7f250-116">仍</span><span class="sxs-lookup"><span data-stu-id="7f250-116">Still</span></span>  |  <span data-ttu-id="7f250-117">水平视野 (FOV H)</span><span class="sxs-lookup"><span data-stu-id="7f250-117">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="7f250-118">建议的用法</span><span class="sxs-lookup"><span data-stu-id="7f250-118">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|
  |  <span data-ttu-id="7f250-119">1280x720</span><span class="sxs-lookup"><span data-stu-id="7f250-119">1280x720</span></span> |  <span data-ttu-id="7f250-120">1280x720</span><span class="sxs-lookup"><span data-stu-id="7f250-120">1280x720</span></span> |  <span data-ttu-id="7f250-121">1280x720</span><span class="sxs-lookup"><span data-stu-id="7f250-121">1280x720</span></span> |  <span data-ttu-id="7f250-122">45deg</span><span class="sxs-lookup"><span data-stu-id="7f250-122">45deg</span></span>  |  <span data-ttu-id="7f250-123">（通过视频防抖动的默认模式）</span><span class="sxs-lookup"><span data-stu-id="7f250-123">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="7f250-124">不可用</span><span class="sxs-lookup"><span data-stu-id="7f250-124">N/A</span></span> |  <span data-ttu-id="7f250-125">不可用</span><span class="sxs-lookup"><span data-stu-id="7f250-125">N/A</span></span> |  <span data-ttu-id="7f250-126">2048x1152</span><span class="sxs-lookup"><span data-stu-id="7f250-126">2048x1152</span></span> |  <span data-ttu-id="7f250-127">67deg</span><span class="sxs-lookup"><span data-stu-id="7f250-127">67deg</span></span> |  <span data-ttu-id="7f250-128">最高分辨率静止图像</span><span class="sxs-lookup"><span data-stu-id="7f250-128">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="7f250-129">1408x792</span><span class="sxs-lookup"><span data-stu-id="7f250-129">1408x792</span></span> |  <span data-ttu-id="7f250-130">1408x792</span><span class="sxs-lookup"><span data-stu-id="7f250-130">1408x792</span></span> |  <span data-ttu-id="7f250-131">1408x792</span><span class="sxs-lookup"><span data-stu-id="7f250-131">1408x792</span></span> |  <span data-ttu-id="7f250-132">48deg</span><span class="sxs-lookup"><span data-stu-id="7f250-132">48deg</span></span> |  <span data-ttu-id="7f250-133">视频防抖动之前自定大小 （填充） 解析</span><span class="sxs-lookup"><span data-stu-id="7f250-133">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="7f250-134">1344x756</span><span class="sxs-lookup"><span data-stu-id="7f250-134">1344x756</span></span> |  <span data-ttu-id="7f250-135">1344x756</span><span class="sxs-lookup"><span data-stu-id="7f250-135">1344x756</span></span> |  <span data-ttu-id="7f250-136">1344x756</span><span class="sxs-lookup"><span data-stu-id="7f250-136">1344x756</span></span> |  <span data-ttu-id="7f250-137">67deg</span><span class="sxs-lookup"><span data-stu-id="7f250-137">67deg</span></span> |  <span data-ttu-id="7f250-138">使用过度扫描大型 FOV 视频模式</span><span class="sxs-lookup"><span data-stu-id="7f250-138">Large FOV video mode with overscan</span></span> | 
  |  <span data-ttu-id="7f250-139">896x504</span><span class="sxs-lookup"><span data-stu-id="7f250-139">896x504</span></span> |  <span data-ttu-id="7f250-140">896x504</span><span class="sxs-lookup"><span data-stu-id="7f250-140">896x504</span></span> |  <span data-ttu-id="7f250-141">896x504</span><span class="sxs-lookup"><span data-stu-id="7f250-141">896x504</span></span> |  <span data-ttu-id="7f250-142">48deg</span><span class="sxs-lookup"><span data-stu-id="7f250-142">48deg</span></span> |  <span data-ttu-id="7f250-143">低功耗 / 图像的低分辨率模式处理任务</span><span class="sxs-lookup"><span data-stu-id="7f250-143">Low power / Low resolution mode for image processing tasks</span></span> | 

### <a name="hololens-2"></a><span data-ttu-id="7f250-144">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7f250-144">HoloLens 2</span></span>

* <span data-ttu-id="7f250-145">自动聚焦照片/视频 (PV) 摄像机，白色自动平衡、 自动公开与完整的映像处理管道</span><span class="sxs-lookup"><span data-stu-id="7f250-145">Auto-focus photo/video (PV) camera, with auto white balance, auto exposure, and full image processing pipe</span></span>
* <span data-ttu-id="7f250-146">面向全球的白色隐私发光二极管会只要照相机处于活动状态</span><span class="sxs-lookup"><span data-stu-id="7f250-146">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="7f250-147">照相机支持以下模式 （所有视频的模式是纵横比为 16:9）：</span><span class="sxs-lookup"><span data-stu-id="7f250-147">The camera supports the following modes (all video modes are 16:9 aspect ratio):</span></span>

  >[!NOTE]
  ><span data-ttu-id="7f250-148">这些模式会在 HoloLens 2 正式发布之前的更改。</span><span class="sxs-lookup"><span data-stu-id="7f250-148">These modes are subject to change prior to HoloLens 2 general availability.</span></span>

  |  <span data-ttu-id="7f250-149">视频</span><span class="sxs-lookup"><span data-stu-id="7f250-149">Video</span></span>  |  <span data-ttu-id="7f250-150">预览</span><span class="sxs-lookup"><span data-stu-id="7f250-150">Preview</span></span>  |  <span data-ttu-id="7f250-151">仍</span><span class="sxs-lookup"><span data-stu-id="7f250-151">Still</span></span>  |  <span data-ttu-id="7f250-152">帧速率</span><span class="sxs-lookup"><span data-stu-id="7f250-152">Frame rates</span></span>  |  <span data-ttu-id="7f250-153">水平视野 (FOV H)</span><span class="sxs-lookup"><span data-stu-id="7f250-153">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="7f250-154">建议的用法</span><span class="sxs-lookup"><span data-stu-id="7f250-154">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|----------|
  |  <span data-ttu-id="7f250-155">1920x1080</span><span class="sxs-lookup"><span data-stu-id="7f250-155">1920x1080</span></span> |  <span data-ttu-id="7f250-156">1920x1080</span><span class="sxs-lookup"><span data-stu-id="7f250-156">1920x1080</span></span> |  <span data-ttu-id="7f250-157">不可用</span><span class="sxs-lookup"><span data-stu-id="7f250-157">N/A</span></span> |  <span data-ttu-id="7f250-158">30、 15 帧/秒</span><span class="sxs-lookup"><span data-stu-id="7f250-158">30, 15 fps</span></span>  |  <span data-ttu-id="7f250-159">54deg</span><span class="sxs-lookup"><span data-stu-id="7f250-159">54deg</span></span>  |  <span data-ttu-id="7f250-160">（通过视频防抖动的默认模式）</span><span class="sxs-lookup"><span data-stu-id="7f250-160">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="7f250-161">不可用</span><span class="sxs-lookup"><span data-stu-id="7f250-161">N/A</span></span> |  <span data-ttu-id="7f250-162">不可用</span><span class="sxs-lookup"><span data-stu-id="7f250-162">N/A</span></span> |  <span data-ttu-id="7f250-163">3904X2196</span><span class="sxs-lookup"><span data-stu-id="7f250-163">3904X2196</span></span> |  <span data-ttu-id="7f250-164">不可用</span><span class="sxs-lookup"><span data-stu-id="7f250-164">N/A</span></span>  |  <span data-ttu-id="7f250-165">64deg</span><span class="sxs-lookup"><span data-stu-id="7f250-165">64deg</span></span> |  <span data-ttu-id="7f250-166">最高分辨率静止图像</span><span class="sxs-lookup"><span data-stu-id="7f250-166">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="7f250-167">2272x1278</span><span class="sxs-lookup"><span data-stu-id="7f250-167">2272x1278</span></span> |  <span data-ttu-id="7f250-168">2272x1278</span><span class="sxs-lookup"><span data-stu-id="7f250-168">2272x1278</span></span> |  <span data-ttu-id="7f250-169">不可用</span><span class="sxs-lookup"><span data-stu-id="7f250-169">N/A</span></span> |  <span data-ttu-id="7f250-170">30、 15 帧/秒</span><span class="sxs-lookup"><span data-stu-id="7f250-170">30, 15 fps</span></span>  |  <span data-ttu-id="7f250-171">64deg</span><span class="sxs-lookup"><span data-stu-id="7f250-171">64deg</span></span> |  <span data-ttu-id="7f250-172">视频防抖动之前自定大小 （填充） 解析</span><span class="sxs-lookup"><span data-stu-id="7f250-172">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="7f250-173">1952x1100</span><span class="sxs-lookup"><span data-stu-id="7f250-173">1952x1100</span></span> |  <span data-ttu-id="7f250-174">1952x1100</span><span class="sxs-lookup"><span data-stu-id="7f250-174">1952x1100</span></span> |  <span data-ttu-id="7f250-175">1952x1100</span><span class="sxs-lookup"><span data-stu-id="7f250-175">1952x1100</span></span>  |  <span data-ttu-id="7f250-176">30、 15 帧/秒</span><span class="sxs-lookup"><span data-stu-id="7f250-176">30, 15 fps</span></span>  |  <span data-ttu-id="7f250-177">64deg</span><span class="sxs-lookup"><span data-stu-id="7f250-177">64deg</span></span> |  <span data-ttu-id="7f250-178">高质量的流式处理</span><span class="sxs-lookup"><span data-stu-id="7f250-178">High-quality streaming</span></span> | 
  |  <span data-ttu-id="7f250-179">1280x720</span><span class="sxs-lookup"><span data-stu-id="7f250-179">1280x720</span></span> |  <span data-ttu-id="7f250-180">1280x720</span><span class="sxs-lookup"><span data-stu-id="7f250-180">1280x720</span></span> |  <span data-ttu-id="7f250-181">不可用</span><span class="sxs-lookup"><span data-stu-id="7f250-181">N/A</span></span> |  <span data-ttu-id="7f250-182">30、 15、 5 帧/秒</span><span class="sxs-lookup"><span data-stu-id="7f250-182">30, 15, 5 fps</span></span>  |  <span data-ttu-id="7f250-183">64deg</span><span class="sxs-lookup"><span data-stu-id="7f250-183">64deg</span></span> |  <span data-ttu-id="7f250-184">流式处理和图像处理任务的每个分辨率低电源模式</span><span class="sxs-lookup"><span data-stu-id="7f250-184">Low power/resolution mode for streaming and image processing tasks</span></span> | 

## <a name="locating-the-device-camera-in-the-world"></a><span data-ttu-id="7f250-185">在世界上定位设备相机</span><span class="sxs-lookup"><span data-stu-id="7f250-185">Locating the Device Camera in the World</span></span>

<span data-ttu-id="7f250-186">照片和视频 HoloLens 时，捕获的帧世界，以及相机的角度来看投影中包括的照相机的位置。</span><span class="sxs-lookup"><span data-stu-id="7f250-186">When HoloLens takes photos and videos, the captured frames include the location of the camera in the world, as well as the perspective projection of the camera.</span></span> <span data-ttu-id="7f250-187">这样，应用程序的原因有关的扩充式映像方案现实生活中的照相机的位置信息。</span><span class="sxs-lookup"><span data-stu-id="7f250-187">This allows applications to reason about the position of the camera in the real world for augmented imaging scenarios.</span></span> <span data-ttu-id="7f250-188">开发人员可以创造性地回滚其自己的方案使用他们最喜爱的图像处理或自定义计算机影像库。</span><span class="sxs-lookup"><span data-stu-id="7f250-188">Developers can creatively roll their own scenarios using their favorite image processing or custom computer vision libraries.</span></span>

<span data-ttu-id="7f250-189">HoloLens 文档中的其他位置的"照相机"可能指"虚拟游戏照相机"（截锥应用程序呈现为）。</span><span class="sxs-lookup"><span data-stu-id="7f250-189">"Camera" elsewhere in HoloLens documentation may refer to the "virtual game camera" (the frustum the app renders to).</span></span> <span data-ttu-id="7f250-190">否则表示，除非在此页上的"照相机"是指实际的 RGB 颜色照相机。</span><span class="sxs-lookup"><span data-stu-id="7f250-190">Unless denoted otherwise, "camera" on this page refers to the real-world RGB color camera.</span></span>

<span data-ttu-id="7f250-191">有关此页面涵盖的详细信息[Media Foundation 特性](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx)，但是也有 Api 拉取照相机内部函数使用[WinRT Api](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics)。</span><span class="sxs-lookup"><span data-stu-id="7f250-191">The details on this page cover [Media Foundation Attributes](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx), however there are also APIs to pull camera intrinsics using [WinRT APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics).</span></span>  

### <a name="images-with-coordinate-systems"></a><span data-ttu-id="7f250-192">与坐标系统的映像</span><span class="sxs-lookup"><span data-stu-id="7f250-192">Images with Coordinate Systems</span></span>

<span data-ttu-id="7f250-193">每个图像帧 (是否照片或视频) 包括坐标系，以及两个重要的转换。</span><span class="sxs-lookup"><span data-stu-id="7f250-193">Each image frame (whether photo or video) includes a coordinate system, as well as two important transforms.</span></span> <span data-ttu-id="7f250-194">"视图"转换到相机，提供的坐标系统中的映射和从照相机"投影"映射至图像中的像素。</span><span class="sxs-lookup"><span data-stu-id="7f250-194">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="7f250-195">在一起，这些转换定义为每个像素 ray 在 3D 空间中表示生成像素 photons 所采用的路径。</span><span class="sxs-lookup"><span data-stu-id="7f250-195">Together, these transforms define for each pixel a ray in 3D space representing the path taken by the photons that produced the pixel.</span></span> <span data-ttu-id="7f250-196">这些大气可以与通过对某些其他坐标系统从框架的坐标系统获取转换应用程序中的其他内容 (例如，从[固定参考框架](coordinate-systems.md#stationary-frame-of-reference))。</span><span class="sxs-lookup"><span data-stu-id="7f250-196">These rays can be related to other content in the app by obtaining the transform from the frame's coordinate system to some other coordinate system (e.g. from a [stationary frame of reference](coordinate-systems.md#stationary-frame-of-reference)).</span></span> <span data-ttu-id="7f250-197">总之，每个图像帧提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="7f250-197">To summarize, each image frame provides the following:</span></span>
* <span data-ttu-id="7f250-198">像素格式的数据 （RGB/NV12/JPEG/等）</span><span class="sxs-lookup"><span data-stu-id="7f250-198">Pixel Data (in RGB/NV12/JPEG/etc. format)</span></span>
* <span data-ttu-id="7f250-199">3 个部分的元数据 (存储为[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx))，使每个帧"定位":</span><span class="sxs-lookup"><span data-stu-id="7f250-199">3 pieces of metadata (stored as [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)) that make each frame "locatable":</span></span>

|  <span data-ttu-id="7f250-200">属性名称</span><span class="sxs-lookup"><span data-stu-id="7f250-200">Attribute name</span></span>  |  <span data-ttu-id="7f250-201">在任务栏的搜索框中键入</span><span class="sxs-lookup"><span data-stu-id="7f250-201">Type</span></span>  |  <span data-ttu-id="7f250-202">GUID</span><span class="sxs-lookup"><span data-stu-id="7f250-202">GUID</span></span>  |  <span data-ttu-id="7f250-203">描述</span><span class="sxs-lookup"><span data-stu-id="7f250-203">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="7f250-204">MFSampleExtension_Spatial_CameraCoordinateSystem</span><span class="sxs-lookup"><span data-stu-id="7f250-204">MFSampleExtension_Spatial_CameraCoordinateSystem</span></span>  |  <span data-ttu-id="7f250-205">IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))</span><span class="sxs-lookup"><span data-stu-id="7f250-205">IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))</span></span>  |  <span data-ttu-id="7f250-206">{9D13C82F-2199-4E67-91CD-D1A4181F2534}</span><span class="sxs-lookup"><span data-stu-id="7f250-206">{9D13C82F-2199-4E67-91CD-D1A4181F2534}</span></span>  |  <span data-ttu-id="7f250-207">存储[坐标系](coordinate-systems-in-directx.md)的捕获的帧</span><span class="sxs-lookup"><span data-stu-id="7f250-207">Stores the [coordinate system](coordinate-systems-in-directx.md) of the captured frame</span></span> | 
|  <span data-ttu-id="7f250-208">MFSampleExtension_Spatial_CameraViewTransform</span><span class="sxs-lookup"><span data-stu-id="7f250-208">MFSampleExtension_Spatial_CameraViewTransform</span></span>  |  <span data-ttu-id="7f250-209">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span><span class="sxs-lookup"><span data-stu-id="7f250-209">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span></span>  |  <span data-ttu-id="7f250-210">{4E251FA4-830F-4770-859A-4B8D99AA809B}</span><span class="sxs-lookup"><span data-stu-id="7f250-210">{4E251FA4-830F-4770-859A-4B8D99AA809B}</span></span>  |  <span data-ttu-id="7f250-211">将照相机的外部转换存储在坐标系统</span><span class="sxs-lookup"><span data-stu-id="7f250-211">Stores the camera's extrinsic transform in the coordinate system</span></span> | 
|  <span data-ttu-id="7f250-212">MFSampleExtension_Spatial_CameraProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="7f250-212">MFSampleExtension_Spatial_CameraProjectionTransform</span></span>  |  <span data-ttu-id="7f250-213">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span><span class="sxs-lookup"><span data-stu-id="7f250-213">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span></span>  |  <span data-ttu-id="7f250-214">{47F9FCB5-2A02-4F26-A477-792FDF95886A}</span><span class="sxs-lookup"><span data-stu-id="7f250-214">{47F9FCB5-2A02-4F26-A477-792FDF95886A}</span></span>  |  <span data-ttu-id="7f250-215">将存储照相机的投影转换</span><span class="sxs-lookup"><span data-stu-id="7f250-215">Stores the camera's projection transform</span></span> | 

<span data-ttu-id="7f250-216">投影转换表示映射到扩展从-1 到 + 1 中的 X 和 Y 轴图平面上的可重用功能区的内部属性 （焦距，中心的投影，倾斜）。</span><span class="sxs-lookup"><span data-stu-id="7f250-216">The projection transform represents the intrinsic properties (focal length, center of projection, skew) of the lens mapped onto an image plane that extends from -1 to +1 in both the X and Y axis.</span></span>

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

<span data-ttu-id="7f250-217">不同的应用程序将具有不同的坐标系统。</span><span class="sxs-lookup"><span data-stu-id="7f250-217">Different applications will have different coordinate systems.</span></span> <span data-ttu-id="7f250-218">下面是流来查找单个应用程序的照相机像素的概览：</span><span class="sxs-lookup"><span data-stu-id="7f250-218">Here's an overview of the flow to locate a camera pixel for a single application:</span></span>

![应用于照相机坐标系统的转换](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a><span data-ttu-id="7f250-220">照相机传送到应用程序指定坐标系统</span><span class="sxs-lookup"><span data-stu-id="7f250-220">Camera to Application-specified Coordinate System</span></span>

<span data-ttu-id="7f250-221">若要从 CameraView 和 CameraCoordinateSystem 转到应用程序/世界坐标系统，你将需要：</span><span class="sxs-lookup"><span data-stu-id="7f250-221">To go from the 'CameraView' and 'CameraCoordinateSystem' to your application/world coordinate system, you'll need the following:</span></span>

<span data-ttu-id="7f250-222">[在 Unity 中的定位照相机](locatable-camera-in-unity.md):CameraToWorldMatrix 会自动提供由 PhotoCaptureFrame 类 （因此，无需担心 CameraCoordinateSystem 转换）。</span><span class="sxs-lookup"><span data-stu-id="7f250-222">[Locatable camera in Unity](locatable-camera-in-unity.md): CameraToWorldMatrix is automatically provided by PhotoCaptureFrame class(so you don't need to worry about the CameraCoordinateSystem transforms).</span></span>

<span data-ttu-id="7f250-223">[在 DirectX 可定位照相机](locatable-camera-in-directx.md):演示了查询的照相机的坐标系统和你自己的应用程序 coordinate system(s) 之间的转换非常简单的方法。</span><span class="sxs-lookup"><span data-stu-id="7f250-223">[Locatable camera in DirectX](locatable-camera-in-directx.md): Shows the fairly straightforward way to query for the transform between the camera's coordinate system and your own application coordinate system(s).</span></span>

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a><span data-ttu-id="7f250-224">应用程序指定到像素坐标的坐标系统</span><span class="sxs-lookup"><span data-stu-id="7f250-224">Application-specified Coordinate System to Pixel Coordinates</span></span>

<span data-ttu-id="7f250-225">让我们假设你想要查找或上的照相机图像绘制在特定的三维位置：</span><span class="sxs-lookup"><span data-stu-id="7f250-225">Let's say you wanted to find or draw at a specific 3d location on a camera image:</span></span>

<span data-ttu-id="7f250-226">需要采用稍有不同的视图和投影转换时这两个 4 × 4 矩阵。</span><span class="sxs-lookup"><span data-stu-id="7f250-226">The view and projection transforms, while both 4x4 matrices, need to be utilized slightly differently.</span></span> <span data-ttu-id="7f250-227">即执行投影后, 一个将规范化通过 w，在投影中的此额外步骤模拟如何将多个不同的三维位置的最终会得到为 （即任何内容沿某些射线将显示同一像素） 的屏幕上的同一个二维位置。</span><span class="sxs-lookup"><span data-stu-id="7f250-227">Namely after performing the Projection, one would 'normalize by w', this extra step in the projection simulates how multiple different 3d locations can end up as the same 2d location on a screen (i.e. anything along a certain ray will show up on the same pixel).</span></span> <span data-ttu-id="7f250-228">因此要点 （在着色器代码中）：</span><span class="sxs-lookup"><span data-stu-id="7f250-228">So key points (in shader code):</span></span>

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a><span data-ttu-id="7f250-229">像素到应用程序指定坐标系统</span><span class="sxs-lookup"><span data-stu-id="7f250-229">Pixel to Application-specified Coordinate System</span></span>

<span data-ttu-id="7f250-230">个世界坐标从像素都是个小技巧：</span><span class="sxs-lookup"><span data-stu-id="7f250-230">Going from pixel to world coordinates is a little trickier:</span></span>

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

<span data-ttu-id="7f250-231">定义作为 UnProject:</span><span class="sxs-lookup"><span data-stu-id="7f250-231">Where we define UnProject as:</span></span>

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

<span data-ttu-id="7f250-232">若要查找一个点的实际世界位置，将需要以下两者之一： 两个世界大气和查找它们的交集，或者有已知的点大小。</span><span class="sxs-lookup"><span data-stu-id="7f250-232">To find the actual world location of a point, you'll need either: two world rays and find their intersection, or a known size of the points.</span></span>

### <a name="distortion-error"></a><span data-ttu-id="7f250-233">扭曲错误</span><span class="sxs-lookup"><span data-stu-id="7f250-233">Distortion Error</span></span>

<span data-ttu-id="7f250-234">HoloLens，在视频和仍图像流是未扭曲系统的映像处理管道中之前帧都提供给应用程序 （预览流包含原始失真的帧）。</span><span class="sxs-lookup"><span data-stu-id="7f250-234">On HoloLens, the video and still image streams are undistorted in the system's image processing pipeline before the frames are made available to the application (the preview stream contains the original distorted frames).</span></span> <span data-ttu-id="7f250-235">由于仅投影矩阵将可用，应用程序必须假定图像帧表示完美 pinhole 照相机，但是变形纠正函数中的图像处理器可能仍将保留最多 10 个像素的错误时使用中的投影矩阵帧的元数据。</span><span class="sxs-lookup"><span data-stu-id="7f250-235">Because only the projection matrix is made available, applications must assume image frames represent a perfect pinhole camera, however the undistortion function in the image processor may still leave an error of up to 10 pixels when using the projection matrix in the frame metadata.</span></span> <span data-ttu-id="7f250-236">在许多用例，此错误将不起作用，但如果要对齐全息到实际海报/标记，例如，且您注意到 < 10px 偏移量 （大致为全息定位 2 米消失的 11 毫米） 此扭曲错误可能是原因。</span><span class="sxs-lookup"><span data-stu-id="7f250-236">In many use cases, this error will not matter, but if you are aligning holograms to real world posters/markers, for example, and you notice a <10px offset (roughly 11mm for holograms positioned 2 meters away) this distortion error could be the cause.</span></span>

## <a name="locatable-camera-usage-scenarios"></a><span data-ttu-id="7f250-237">可定位照相机使用方案</span><span class="sxs-lookup"><span data-stu-id="7f250-237">Locatable Camera Usage Scenarios</span></span>

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a><span data-ttu-id="7f250-238">在捕获时的世界中显示的照片或视频</span><span class="sxs-lookup"><span data-stu-id="7f250-238">Show a photo or video in the world where it was captured</span></span>

<span data-ttu-id="7f250-239">设备相机帧附带"照相机 World"转换，用于显示准确的设备时图像捕获。</span><span class="sxs-lookup"><span data-stu-id="7f250-239">The Device Camera frames come with a "Camera To World" transform, that can be used to show exactly where the device was when the image was taken.</span></span> <span data-ttu-id="7f250-240">例如在 （CameraToWorld.MultiplyPoint(Vector3.zero)) 和甚至绘图小箭头方向照相机面向 (CameraToWorld.MultiplyVector(Vector3.forward)) 此位置开始位置小 holographic 图标。</span><span class="sxs-lookup"><span data-stu-id="7f250-240">For example you could position a small holographic icon at this location (CameraToWorld.MultiplyPoint(Vector3.zero)) and even draw a little arrow in the direction that the camera was facing (CameraToWorld.MultiplyVector(Vector3.forward)).</span></span>

### <a name="painting-the-world-using-a-camera-shader"></a><span data-ttu-id="7f250-241">绘制世界上使用照相机着色器</span><span class="sxs-lookup"><span data-stu-id="7f250-241">Painting the world using a camera shader</span></span>

<span data-ttu-id="7f250-242">在本部分中我们将创建材料着色器世界上基于在其中显示的设备照相机的视图中的颜色。</span><span class="sxs-lookup"><span data-stu-id="7f250-242">In this section we'll create a material 'shader' that colors the world based on where it showed up in a device camera's view.</span></span> <span data-ttu-id="7f250-243">实际上我们将执行的操作是每个顶点将找出相对于照相机，其位置和每个像素然后将投影矩阵利用到图图像与相关联的纹素的扩展。</span><span class="sxs-lookup"><span data-stu-id="7f250-243">Effectively what we'll do is that every vertex will figure out its location relative to the camera, and then every pixel will utilize the 'projection matrix' to figure out which image texel it is associated with.</span></span> <span data-ttu-id="7f250-244">最后，和 （可选），我们将淡出的角映像使其看起来类似于操作之梦的内存的详细信息：</span><span class="sxs-lookup"><span data-stu-id="7f250-244">Lastly, and optionally, we'll fade out the corners of the image to make it appear more as a dream-like memory:</span></span>

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

### <a name="tag--pattern--poster--object-tracking"></a><span data-ttu-id="7f250-245">标记 / 海报 / 对象跟踪</span><span class="sxs-lookup"><span data-stu-id="7f250-245">Tag / Pattern / Poster / Object Tracking</span></span>

<span data-ttu-id="7f250-246">许多混合的现实应用程序使用可识别图像或 visual 模式空间中创建的可跟踪点。</span><span class="sxs-lookup"><span data-stu-id="7f250-246">Many mixed reality applications use a recognizable image or visual pattern to create a trackable point in space.</span></span> <span data-ttu-id="7f250-247">这再用于呈现对象相对于的点或创建一个已知的位置。</span><span class="sxs-lookup"><span data-stu-id="7f250-247">This is then used to render objects relative to that point or create a known location.</span></span> <span data-ttu-id="7f250-248">HoloLens 的一些用途包括的查找现实世界对象标记为裂痕 （例如一个有 QR 码电视监视器）、 通过裂痕，放置全息和直观地与已设置为与通过 HoloLens 的平板电脑之类的非 HoloLens 设备配对Wi-fi。</span><span class="sxs-lookup"><span data-stu-id="7f250-248">Some uses for HoloLens include finding a real world object tagged with fiducials (e.g. a TV monitor with a QR code), placing holograms over fiducials, and visually pairing with non-HoloLens devices like tablets that have been setup to communicate with HoloLens via Wi-Fi.</span></span>

<span data-ttu-id="7f250-249">若要识别 visual 模式，然后将该对象放在应用程序世界空间中，你将需要几件事：</span><span class="sxs-lookup"><span data-stu-id="7f250-249">To recognize a visual pattern, and then place that object in the applications world space, you'll need a few things:</span></span>
1. <span data-ttu-id="7f250-250">一个映像模式识别的工具包，如 QR 码、 AR 标记、 人脸 finder、 圆形跟踪器、 OCR 等。</span><span class="sxs-lookup"><span data-stu-id="7f250-250">An image pattern recognition toolkit, such as QR code, AR tags, face finder, circle trackers, OCR etc.</span></span>
2. <span data-ttu-id="7f250-251">收集在运行时，图像帧，并将其传递给识别层</span><span class="sxs-lookup"><span data-stu-id="7f250-251">Collect image frames at runtime, and pass them to the recognition layer</span></span>
3. <span data-ttu-id="7f250-252">Unproject 回世界位置或可能世界大气其映像位置。</span><span class="sxs-lookup"><span data-stu-id="7f250-252">Unproject their image locations back into world positions, or likely world rays.</span></span> <span data-ttu-id="7f250-253">请参阅</span><span class="sxs-lookup"><span data-stu-id="7f250-253">See</span></span>
4. <span data-ttu-id="7f250-254">虚拟模型放这些世界位置</span><span class="sxs-lookup"><span data-stu-id="7f250-254">Position your virtual models over these world locations</span></span>

<span data-ttu-id="7f250-255">一些重要的图像处理链接：</span><span class="sxs-lookup"><span data-stu-id="7f250-255">Some important image processing links:</span></span>
* [<span data-ttu-id="7f250-256">OpenCV</span><span class="sxs-lookup"><span data-stu-id="7f250-256">OpenCV</span></span>](http://opencv.org/)
* [<span data-ttu-id="7f250-257">QR 标记</span><span class="sxs-lookup"><span data-stu-id="7f250-257">QR Tags</span></span>](https://en.wikipedia.org/wiki/QR_code)
* [<span data-ttu-id="7f250-258">FaceSDK</span><span class="sxs-lookup"><span data-stu-id="7f250-258">FaceSDK</span></span>](http://research.microsoft.com/projects/facesdk/)
* [<span data-ttu-id="7f250-259">Microsoft Translator</span><span class="sxs-lookup"><span data-stu-id="7f250-259">Microsoft Translator</span></span>](https://www.microsoft.com/translator/business)

<span data-ttu-id="7f250-260">保留交互式应用程序帧速率至关重要，尤其是在处理长时间运行图像识别算法。</span><span class="sxs-lookup"><span data-stu-id="7f250-260">Keeping an interactive application frame-rate is critical, especially when dealing with long-running image recognition algorithms.</span></span> <span data-ttu-id="7f250-261">因此我们通常使用以下模式：</span><span class="sxs-lookup"><span data-stu-id="7f250-261">For this reason we commonly use the following pattern:</span></span>
1. <span data-ttu-id="7f250-262">主线程： 管理相机对象</span><span class="sxs-lookup"><span data-stu-id="7f250-262">Main Thread: manages the camera object</span></span>
2. <span data-ttu-id="7f250-263">主线程： 请求新帧 （异步）</span><span class="sxs-lookup"><span data-stu-id="7f250-263">Main Thread: requests new frames (async)</span></span>
3. <span data-ttu-id="7f250-264">主线程： 将新帧传递给跟踪线索</span><span class="sxs-lookup"><span data-stu-id="7f250-264">Main Thread: pass new frames to tracking thread</span></span>
4. <span data-ttu-id="7f250-265">跟踪线程： 处理要收集的关键点图像</span><span class="sxs-lookup"><span data-stu-id="7f250-265">Tracking Thread: processes image to collect key points</span></span>
5. <span data-ttu-id="7f250-266">主线程： 移动虚拟模式，以匹配找到关键点</span><span class="sxs-lookup"><span data-stu-id="7f250-266">Main Thread: moves virtual model to match found key points</span></span>
6. <span data-ttu-id="7f250-267">重复步骤 2 中的主线程：</span><span class="sxs-lookup"><span data-stu-id="7f250-267">Main Thread: repeat from step 2</span></span>

<span data-ttu-id="7f250-268">某些图像标记系统仅提供单个像素的位置 (其他人提供完整的转换在这种情况下将不需要此部分)，其相当于一条可能的位置。</span><span class="sxs-lookup"><span data-stu-id="7f250-268">Some image marker systems only provide a single pixel location (others provide the full transform in which case this section will not be needed), which equates to a ray of possible locations.</span></span> <span data-ttu-id="7f250-269">若要获取到一个单独的三维位置我们可以利用多个大气并查找其近似的交集的最终结果上。</span><span class="sxs-lookup"><span data-stu-id="7f250-269">To get to a single 3d location we can then leverage multiple rays and find the final result by their approximate intersection.</span></span> <span data-ttu-id="7f250-270">若要执行此操作将需要：</span><span class="sxs-lookup"><span data-stu-id="7f250-270">To do this you'll need to:</span></span>
1. <span data-ttu-id="7f250-271">获取一个循环将收集多个照相机图像</span><span class="sxs-lookup"><span data-stu-id="7f250-271">Get a loop going collecting multiple camera images</span></span>
2. <span data-ttu-id="7f250-272">查找[关联的功能点](#pixel-to-application-specified-coordinate-system)，并且其全球大气</span><span class="sxs-lookup"><span data-stu-id="7f250-272">Find the [associated feature points](#pixel-to-application-specified-coordinate-system), and their world rays</span></span>
3. <span data-ttu-id="7f250-273">当具有的功能，每个都有多个世界大气，字典时可以使用下面的代码来解决这些射线相交的：</span><span class="sxs-lookup"><span data-stu-id="7f250-273">When you have a dictionary of features, each with multiple world rays, you can use the following code to solve for the intersection of those rays:</span></span>

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

<span data-ttu-id="7f250-274">给定两个或多个跟踪的标记位置，您可以定位 modelled 的场景以适合用户当前应用场景。</span><span class="sxs-lookup"><span data-stu-id="7f250-274">Given two or more tracked tag locations, you can position a modelled scene to fit the users current scenario.</span></span> <span data-ttu-id="7f250-275">如果您不能假定重力，您将需要三个标记位置。</span><span class="sxs-lookup"><span data-stu-id="7f250-275">If you can't assume gravity, then you'll need three tag locations.</span></span> <span data-ttu-id="7f250-276">在许多情况下，我们使用简单的配色方案白色球体表示实时跟踪标记位置和蓝色球体表示建模标记位置，这允许用户直观地仪表对齐质量。</span><span class="sxs-lookup"><span data-stu-id="7f250-276">In many cases we use a simple color scheme where white spheres represent real-time tracked tag locations, and blue spheres represent modelled tag locations, this allows the user to visually gauge the alignment quality.</span></span> <span data-ttu-id="7f250-277">在我们的所有应用程序中，我们假设以下设置：</span><span class="sxs-lookup"><span data-stu-id="7f250-277">We assume the following setup in all our applications:</span></span>
* <span data-ttu-id="7f250-278">两个或多个建模标记位置</span><span class="sxs-lookup"><span data-stu-id="7f250-278">Two or more modelled tag locations</span></span>
* <span data-ttu-id="7f250-279">其中一个校准的空间场景中的标记的父级</span><span class="sxs-lookup"><span data-stu-id="7f250-279">One 'calibration space' which in the scene is the parent of the tags</span></span>
* <span data-ttu-id="7f250-280">照相机功能标识符</span><span class="sxs-lookup"><span data-stu-id="7f250-280">Camera feature identifier</span></span>
* <span data-ttu-id="7f250-281">将移动校准格对齐 （我们非常小心地将移动的父区域中，不 modelled 标记本身，因为其他 connect 是它们的相对位置） 的实时标记的 modelled 的标记的行为。</span><span class="sxs-lookup"><span data-stu-id="7f250-281">Behavior which moves the calibration space to align the modelled tags with the real-time tags (we are careful to move the parent space, not the modelled markers themselves, because other connect is positions relative to them).</span></span>

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

### <a name="render-holograms-from-the-cameras-position"></a><span data-ttu-id="7f250-282">呈现全息从照相机的位置</span><span class="sxs-lookup"><span data-stu-id="7f250-282">Render holograms from the Camera's position</span></span>

<span data-ttu-id="7f250-283">注意：如果你尝试创建您自己[混合现实捕获 (MRC)](mixed-reality-capture.md)，其中融合全息用照相机的流，则可以使用[MRC 效果](mixed-reality-capture-for-developers.md)或启用中的 showHolograms 属性[在 Unity 中的定位照相机](locatable-camera-in-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="7f250-283">Note: If you are trying to create your own [Mixed reality capture (MRC)](mixed-reality-capture.md), which blends holograms with the Camera stream, you can use the [MRC effects](mixed-reality-capture-for-developers.md) or enable the showHolograms property in [Locatable camera in Unity](locatable-camera-in-unity.md).</span></span>

<span data-ttu-id="7f250-284">如果你想要执行特殊 RGB 照相机流上直接呈现，就可以呈现全息从照相机的位置的空间中以提供自定义全息图录制/实时预览视频源同步。</span><span class="sxs-lookup"><span data-stu-id="7f250-284">If you'd like to do a special render directly on the RGB Camera stream, it's possible to render holograms in space from the Camera's position in sync with a video feed in order to provide a custom hologram recording/live preview.</span></span>

<span data-ttu-id="7f250-285">在 Skype，我们执行此操作以显示远程客户端 HoloLens 用户看到的内容，使他们可以与同一全息进行交互。</span><span class="sxs-lookup"><span data-stu-id="7f250-285">In Skype, we do this to show the remote client what the HoloLens user is seeing and allow them to interact with the same holograms.</span></span> <span data-ttu-id="7f250-286">在发送前通过 Skype 服务每个视频帧内，我们将获取每个帧的相应相机数据。</span><span class="sxs-lookup"><span data-stu-id="7f250-286">Before sending over each video frame through the Skype service, we grab each frame's corresponding camera data.</span></span> <span data-ttu-id="7f250-287">我们然后包照相机的外部和内部元数据与视频帧，然后将其发送通过 Skype 服务。</span><span class="sxs-lookup"><span data-stu-id="7f250-287">We then package the camera's extrinsic and intrinsic metadata with the video frame and then send it over the Skype service.</span></span>

<span data-ttu-id="7f250-288">在接收端，使用 Unity 中，我们已同步所有全息 HoloLens 用户空间使用相同的坐标系统中。</span><span class="sxs-lookup"><span data-stu-id="7f250-288">On the receiving side, using Unity, we've already synced all of the holograms in the HoloLens user's space using the same coordinate system.</span></span> <span data-ttu-id="7f250-289">这使得我们可以使用照相机的外部元数据将 Unity 照相机放在 HoloLens 用户站着时捕获该视频的帧时，（相对于全息其余） 世界中的确切位置并使用的照相机内部函数信息请确保该视图相同。</span><span class="sxs-lookup"><span data-stu-id="7f250-289">This allows us to use the camera's extrinsic metadata to place the Unity camera in the exact place in the world (relative to the rest of the holograms) that the HoloLens user was standing when that video frame was captured, and use the camera intrinsic information to ensure the view is the same.</span></span>

<span data-ttu-id="7f250-290">一旦我们有摄像机正确设置，我们将组合照相机拖到框架上接收到来自 Skype，创建的 HoloLens 用户会看到使用 Graphics.Blit 混合的现实视图看到哪些全息。</span><span class="sxs-lookup"><span data-stu-id="7f250-290">Once we have the camera set up properly, we combine what holograms the camera sees onto the frame we received from Skype, creating a mixed reality view of what the HoloLens user sees using Graphics.Blit.</span></span>

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a><span data-ttu-id="7f250-291">跟踪或标识标记的静态或移动现实世界对象/人脸使用 Led 或其他识别器库</span><span class="sxs-lookup"><span data-stu-id="7f250-291">Track or Identify Tagged Stationary or Moving real-world objects/faces using LEDs or other recognizer libraries</span></span>

<span data-ttu-id="7f250-292">示例：</span><span class="sxs-lookup"><span data-stu-id="7f250-292">Examples:</span></span>
* <span data-ttu-id="7f250-293">使用 Led 工业机器人 （或对象的速度较慢移动 QR 码）</span><span class="sxs-lookup"><span data-stu-id="7f250-293">Industrial robots with LEDs (or QR codes for slower moving objects)</span></span>
* <span data-ttu-id="7f250-294">确定和识别在聊天室中的对象</span><span class="sxs-lookup"><span data-stu-id="7f250-294">Identify and recognize objects in the room</span></span>
* <span data-ttu-id="7f250-295">确定和识别出空间 （例如位置 holographic 联系人卡通过人脸） 中的人员</span><span class="sxs-lookup"><span data-stu-id="7f250-295">Identify and recognize people in the room (e.g. place holographic contact cards over faces)</span></span>

## <a name="see-also"></a><span data-ttu-id="7f250-296">请参阅</span><span class="sxs-lookup"><span data-stu-id="7f250-296">See also</span></span>
* [<span data-ttu-id="7f250-297">在 DirectX 可定位照相机</span><span class="sxs-lookup"><span data-stu-id="7f250-297">Locatable camera in DirectX</span></span>](locatable-camera-in-directx.md)
* [<span data-ttu-id="7f250-298">在 Unity 中定位照相机</span><span class="sxs-lookup"><span data-stu-id="7f250-298">Locatable camera in Unity</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="7f250-299">混合的现实捕获</span><span class="sxs-lookup"><span data-stu-id="7f250-299">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="7f250-300">面向开发人员混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="7f250-300">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="7f250-301">媒体捕获简介</span><span class="sxs-lookup"><span data-stu-id="7f250-301">Media capture introduction</span></span>](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
