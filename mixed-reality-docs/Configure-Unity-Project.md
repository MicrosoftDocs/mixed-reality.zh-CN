---
title: 针对 Windows Mixed Reality 配置新的 Unity 项目
description: 配置而无需 MRTK Unity 项目
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity 中，混合现实、 开发、 开始、 新建项目
ms.openlocfilehash: aad38474781fd78425d48034877122d36d9e3e93
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2019
ms.locfileid: "65940746"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="cdba2-104">针对 Windows Mixed Reality 配置新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="cdba2-104">Configure a New Unity Project for Windows Mixed Reality</span></span> 

<span data-ttu-id="cdba2-105">（如果你已导入 Unity 项目 MRTK v2，请跳过）</span><span class="sxs-lookup"><span data-stu-id="cdba2-105">(skip if you have already imported MRTK v2 into your Unity Project)</span></span>

<span data-ttu-id="cdba2-106">如果你想要创建新的 Unity 项目没有导入混合现实工具包，有少量的 Unity 设置，将需要手动更改 Windows Mixed Reality，划分为两个类别： 每个项目和每个场景。</span><span class="sxs-lookup"><span data-stu-id="cdba2-106">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="cdba2-107">每个项目设置</span><span class="sxs-lookup"><span data-stu-id="cdba2-107">Per-project settings</span></span>

<span data-ttu-id="cdba2-108">若要针对 Windows Mixed Reality，首先需要设置你的 Unity 项目以导出为通用 Windows 平台应用：</span><span class="sxs-lookup"><span data-stu-id="cdba2-108">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span>
1. <span data-ttu-id="cdba2-109">选择**文件 > 生成设置...**</span><span class="sxs-lookup"><span data-stu-id="cdba2-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="cdba2-110">选择**通用 Windows 平台**在平台中列表，并单击**交换机平台**</span><span class="sxs-lookup"><span data-stu-id="cdba2-110">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="cdba2-111">设置**SDK**到**通用 10**</span><span class="sxs-lookup"><span data-stu-id="cdba2-111">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="cdba2-112">设置**目标设备**到**任一设备**以支持沉浸式耳机或切换到**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="cdba2-112">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="cdba2-113">设置**生成的类型**到**D3D**</span><span class="sxs-lookup"><span data-stu-id="cdba2-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="cdba2-114">设置**UWP SDK**到**最新安装**</span><span class="sxs-lookup"><span data-stu-id="cdba2-114">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="cdba2-115">然后，我们需要让 Unity 知道我们尝试导出该应用应创建[沉浸式视图](app-views.md)而不是二维视图。</span><span class="sxs-lookup"><span data-stu-id="cdba2-115">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="cdba2-116">我们通过启用"虚拟现实支持"中执行的操作：</span><span class="sxs-lookup"><span data-stu-id="cdba2-116">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="cdba2-117">从**生成设置...** 窗口中，打开**播放器设置...**</span><span class="sxs-lookup"><span data-stu-id="cdba2-117">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="cdba2-118">选择**通用 Windows 平台的设置**选项卡</span><span class="sxs-lookup"><span data-stu-id="cdba2-118">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="cdba2-119">展开**XR 设置**组</span><span class="sxs-lookup"><span data-stu-id="cdba2-119">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="cdba2-120">在中**XR 设置**部分中，选择**受支持的虚拟现实**复选框以添加**虚拟现实设备**列表。</span><span class="sxs-lookup"><span data-stu-id="cdba2-120">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="cdba2-121">在中**XR 设置**组中，确认 **"Windows Mixed Reality"** 被列为受支持的设备。</span><span class="sxs-lookup"><span data-stu-id="cdba2-121">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="cdba2-122">（这可能显示为"Windows Holographic"在较旧版本的 Unity）</span><span class="sxs-lookup"><span data-stu-id="cdba2-122">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="cdba2-123">![Unity 质量设置](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="cdba2-123">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="cdba2-124">*Unity xr 设置*</span><span class="sxs-lookup"><span data-stu-id="cdba2-124">*Unity xr settings*</span></span>

<span data-ttu-id="cdba2-125">您的应用程序现在可以执行基本全息呈现和空间的输入。</span><span class="sxs-lookup"><span data-stu-id="cdba2-125">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="cdba2-126">若要更进一步，充分利用特定功能，你的应用必须声明其清单中的相应功能。</span><span class="sxs-lookup"><span data-stu-id="cdba2-126">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="cdba2-127">可以在 Unity 中进行的清单的声明，以便将它们包括在每个后续项目导出。</span><span class="sxs-lookup"><span data-stu-id="cdba2-127">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="cdba2-128">该设置位于**播放器设置 > 通用 Windows 平台的设置 > 发布设置 > 功能**。</span><span class="sxs-lookup"><span data-stu-id="cdba2-128">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="cdba2-129">启用的常用的 Unity Api 的混合现实适用的功能包括：</span><span class="sxs-lookup"><span data-stu-id="cdba2-129">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="cdba2-130">功能</span><span class="sxs-lookup"><span data-stu-id="cdba2-130">Capability</span></span>  |  <span data-ttu-id="cdba2-131">Api，需要功能</span><span class="sxs-lookup"><span data-stu-id="cdba2-131">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="cdba2-132">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="cdba2-132">SpatialPerception</span></span>  |  <span data-ttu-id="cdba2-133">SurfaceObserver (访问权限[空间映射](spatial-mapping.md)网格上 HoloLens)&mdash;*所需的常规空间头戴式跟踪没有任何功能*</span><span class="sxs-lookup"><span data-stu-id="cdba2-133">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="cdba2-134">网络摄像头</span><span class="sxs-lookup"><span data-stu-id="cdba2-134">WebCam</span></span>  |  <span data-ttu-id="cdba2-135">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="cdba2-135">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="cdba2-136">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="cdba2-136">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="cdba2-137">PhotoCapture 或 VideoCapture，分别 （时存储捕获的内容）</span><span class="sxs-lookup"><span data-stu-id="cdba2-137">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="cdba2-138">麦克风</span><span class="sxs-lookup"><span data-stu-id="cdba2-138">Microphone</span></span>  |  <span data-ttu-id="cdba2-139">VideoCapture （时捕获音频）、 DictationRecognizer、 GrammarRecognizer 和 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="cdba2-139">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="cdba2-140">InternetClient</span><span class="sxs-lookup"><span data-stu-id="cdba2-140">InternetClient</span></span>  |  <span data-ttu-id="cdba2-141">DictationRecognizer （并使用 Unity Profiler）</span><span class="sxs-lookup"><span data-stu-id="cdba2-141">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="cdba2-142">**Unity 质量设置**</span><span class="sxs-lookup"><span data-stu-id="cdba2-142">**Unity quality settings**</span></span>

<span data-ttu-id="cdba2-143">![Unity 质量设置](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="cdba2-143">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="cdba2-144">*Unity 质量设置*</span><span class="sxs-lookup"><span data-stu-id="cdba2-144">*Unity quality settings*</span></span>

<span data-ttu-id="cdba2-145">HoloLens 有移动类 GPU。</span><span class="sxs-lookup"><span data-stu-id="cdba2-145">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="cdba2-146">如果您的应用程序面向 HoloLens，则需要针对最快的性能优化的质量设置以确保我们保持完整的帧速率：</span><span class="sxs-lookup"><span data-stu-id="cdba2-146">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="cdba2-147">选择**编辑 > 项目设置 > 质量**</span><span class="sxs-lookup"><span data-stu-id="cdba2-147">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="cdba2-148">选择**下拉列表中**下**Windows 应用商店**徽标，然后选择**非常低**。</span><span class="sxs-lookup"><span data-stu-id="cdba2-148">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="cdba2-149">您将知道当正确应用了设置 Windows 应用商店列中的框并**非常低**行都显示为绿色。</span><span class="sxs-lookup"><span data-stu-id="cdba2-149">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="cdba2-150">每个场景设置</span><span class="sxs-lookup"><span data-stu-id="cdba2-150">Per-scene settings</span></span>

<span data-ttu-id="cdba2-151">**Unity 照相机设置**</span><span class="sxs-lookup"><span data-stu-id="cdba2-151">**Unity camera settings**</span></span>

<span data-ttu-id="cdba2-152">![Unity 照相机设置](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="cdba2-152">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="cdba2-153">*Unity 照相机设置*</span><span class="sxs-lookup"><span data-stu-id="cdba2-153">*Unity camera settings*</span></span>

<span data-ttu-id="cdba2-154">可以在"虚拟现实支持"复选框，一旦[Unity 照相机](camera-in-unity.md)组件句柄[头跟踪和立体呈现](rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="cdba2-154">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="cdba2-155">没有无需将其替换为自定义在相机上以执行此操作。</span><span class="sxs-lookup"><span data-stu-id="cdba2-155">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="cdba2-156">如果您的应用程序专门面向 HoloLens，有几个需要更改以使您的应用程序将通过显示物理世界的设备的透明显示优化的设置：</span><span class="sxs-lookup"><span data-stu-id="cdba2-156">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="cdba2-157">在中**层次结构**，选择**Main Camera**</span><span class="sxs-lookup"><span data-stu-id="cdba2-157">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="cdba2-158">在**Inspector**面板中，将转换**位置**到**0，0，0**以便用户头位置始于 Unity 世界原点。</span><span class="sxs-lookup"><span data-stu-id="cdba2-158">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="cdba2-159">更改**清除标志**到**纯色**。</span><span class="sxs-lookup"><span data-stu-id="cdba2-159">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="cdba2-160">更改**背景**颜色**RGBA 0,0,0,0**。</span><span class="sxs-lookup"><span data-stu-id="cdba2-160">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="cdba2-161">黑色将呈现为透明的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="cdba2-161">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="cdba2-162">更改**剪裁平面的附近**到[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 （米）。</span><span class="sxs-lookup"><span data-stu-id="cdba2-162">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="cdba2-163">如果你删除并创建一个新的照相机，请确保您的照相机**标记**作为**MainCamera**。</span><span class="sxs-lookup"><span data-stu-id="cdba2-163">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>


## <a name="see-also"></a><span data-ttu-id="cdba2-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="cdba2-164">See also</span></span>
* [<span data-ttu-id="cdba2-165">混合现实 Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="cdba2-165">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="cdba2-166">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="cdba2-166">Unity Development Overview</span></span>](unity-development-overview.md)
