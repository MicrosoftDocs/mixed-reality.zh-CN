---
title: 为 Windows Mixed Reality 配置新的 Unity 项目
description: 不 MRTK 配置 Unity 项目
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 混合现实, 开发, 入门, 新项目
ms.openlocfilehash: 68dded9d0fc9e861bdda56c4954d72ddafafa686
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326095"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="6a417-104">为 Windows Mixed Reality 配置新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="6a417-104">Configure a New Unity Project for Windows Mixed Reality</span></span> 

<span data-ttu-id="6a417-105">(如果已将 MRTK v2 导入到 Unity 项目中, 请跳过)</span><span class="sxs-lookup"><span data-stu-id="6a417-105">(skip if you have already imported MRTK v2 into your Unity Project)</span></span>

<span data-ttu-id="6a417-106">如果要在不导入混合现实工具包的情况下创建新的 Unity 项目, 则需要为 Windows Mixed Reality 手动更改的一小一组 Unity 设置, 分为两类: 每个项目和每场景。</span><span class="sxs-lookup"><span data-stu-id="6a417-106">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="6a417-107">每个项目的设置</span><span class="sxs-lookup"><span data-stu-id="6a417-107">Per-project settings</span></span>

<span data-ttu-id="6a417-108">若要面向 Windows Mixed Reality, 首先需要将 Unity 项目设置为导出为通用 Windows 平台应用:</span><span class="sxs-lookup"><span data-stu-id="6a417-108">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span> 
1. <span data-ttu-id="6a417-109">选择**文件 > 生成设置 ...**</span><span class="sxs-lookup"><span data-stu-id="6a417-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="6a417-110">选择 "平台" 列表中的 "**通用 Windows 平台**", 然后单击 "**切换平台**"</span><span class="sxs-lookup"><span data-stu-id="6a417-110">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="6a417-111">将**SDK**设置为**通用 10**</span><span class="sxs-lookup"><span data-stu-id="6a417-111">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="6a417-112">将**目标设备**设置为**任何设备**以支持沉浸式耳机或切换到**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="6a417-112">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="6a417-113">将**生成类型**设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="6a417-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="6a417-114">将**UWP SDK**设置为**安装的最新版本**</span><span class="sxs-lookup"><span data-stu-id="6a417-114">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="6a417-115">接下来, 我们需要让 Unity 知道我们要导出的应用程序应创建[沉浸式视图](app-views.md)而不是2d 视图。</span><span class="sxs-lookup"><span data-stu-id="6a417-115">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="6a417-116">为此, 请启用 "支持的虚拟现实":</span><span class="sxs-lookup"><span data-stu-id="6a417-116">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="6a417-117">从 "**生成设置 ...** " 窗口中, 打开 "**播放机设置 ...** "</span><span class="sxs-lookup"><span data-stu-id="6a417-117">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="6a417-118">选择通用 Windows 平台 "选项卡的**设置**</span><span class="sxs-lookup"><span data-stu-id="6a417-118">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="6a417-119">展开 " **XR 设置**" 组</span><span class="sxs-lookup"><span data-stu-id="6a417-119">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="6a417-120">在 " **XR 设置**" 部分中, 选中 "**受支持的虚拟现实**" 复选框以添加 "**虚拟现实设备**" 列表。</span><span class="sxs-lookup"><span data-stu-id="6a417-120">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="6a417-121">在 " **XR 设置**" 组中, 确认 **"Windows Mixed Reality"** 列为受支持的设备。</span><span class="sxs-lookup"><span data-stu-id="6a417-121">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="6a417-122">(在早期版本的 Unity 中, 这可能显示为 "Windows 全息")</span><span class="sxs-lookup"><span data-stu-id="6a417-122">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="6a417-123">![Unity 质量设置](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="6a417-123">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="6a417-124">*Unity xr 设置*</span><span class="sxs-lookup"><span data-stu-id="6a417-124">*Unity xr settings*</span></span>

<span data-ttu-id="6a417-125">现在, 你的应用可以执行基本的全息呈现和空间输入。</span><span class="sxs-lookup"><span data-stu-id="6a417-125">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="6a417-126">若要进一步了解并利用某些功能, 应用必须在其清单中声明相应的功能。</span><span class="sxs-lookup"><span data-stu-id="6a417-126">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="6a417-127">清单声明可以在 Unity 中进行, 因此它们包含在每个后续的项目导出中。</span><span class="sxs-lookup"><span data-stu-id="6a417-127">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="6a417-128">此设置位于 "播放机设置" > "设置" 中**通用 Windows 平台 > 发布设置 > 功能**。</span><span class="sxs-lookup"><span data-stu-id="6a417-128">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="6a417-129">为混合现实启用常用 Unity Api 的适用功能包括:</span><span class="sxs-lookup"><span data-stu-id="6a417-129">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="6a417-130">功能</span><span class="sxs-lookup"><span data-stu-id="6a417-130">Capability</span></span>  |  <span data-ttu-id="6a417-131">需要功能的 Api</span><span class="sxs-lookup"><span data-stu-id="6a417-131">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="6a417-132">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="6a417-132">SpatialPerception</span></span>  |  <span data-ttu-id="6a417-133">SurfaceObserver (在 HoloLens 上访问[空间映射](spatial-mapping.md)网格)&mdash;*不需要对耳机进行常规空间跟踪*</span><span class="sxs-lookup"><span data-stu-id="6a417-133">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="6a417-134">网络摄像头</span><span class="sxs-lookup"><span data-stu-id="6a417-134">WebCam</span></span>  |  <span data-ttu-id="6a417-135">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="6a417-135">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="6a417-136">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="6a417-136">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="6a417-137">PhotoCapture 或 VideoCapture (存储捕获的内容时)</span><span class="sxs-lookup"><span data-stu-id="6a417-137">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="6a417-138">麦克风</span><span class="sxs-lookup"><span data-stu-id="6a417-138">Microphone</span></span>  |  <span data-ttu-id="6a417-139">VideoCapture (捕获音频时)、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="6a417-139">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="6a417-140">InternetClient</span><span class="sxs-lookup"><span data-stu-id="6a417-140">InternetClient</span></span>  |  <span data-ttu-id="6a417-141">DictationRecognizer (和使用 Unity 探查器)</span><span class="sxs-lookup"><span data-stu-id="6a417-141">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="6a417-142">**Unity 质量设置**</span><span class="sxs-lookup"><span data-stu-id="6a417-142">**Unity quality settings**</span></span>

<span data-ttu-id="6a417-143">![Unity 质量设置](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="6a417-143">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="6a417-144">*Unity 质量设置*</span><span class="sxs-lookup"><span data-stu-id="6a417-144">*Unity quality settings*</span></span>

<span data-ttu-id="6a417-145">HoloLens 具有移动类 GPU。</span><span class="sxs-lookup"><span data-stu-id="6a417-145">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="6a417-146">如果你的应用面向 HoloLens, 你将希望优化质量设置以实现最快的性能, 以确保保持完整的帧率:</span><span class="sxs-lookup"><span data-stu-id="6a417-146">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="6a417-147">选择 "**编辑 > 项目设置 > 质量**"</span><span class="sxs-lookup"><span data-stu-id="6a417-147">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="6a417-148">选择**Windows 应用商店**徽标下的**下拉列表**, 并选择 "**非常低**"。</span><span class="sxs-lookup"><span data-stu-id="6a417-148">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="6a417-149">如果 Windows 应用商店列和**极低**的行中的框为绿色, 则会知道设置正确应用。</span><span class="sxs-lookup"><span data-stu-id="6a417-149">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="6a417-150">每场景设置</span><span class="sxs-lookup"><span data-stu-id="6a417-150">Per-scene settings</span></span>

<span data-ttu-id="6a417-151">**Unity 照相机设置**</span><span class="sxs-lookup"><span data-stu-id="6a417-151">**Unity camera settings**</span></span>

<span data-ttu-id="6a417-152">![Unity 照相机设置](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="6a417-152">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="6a417-153">*Unity 照相机设置*</span><span class="sxs-lookup"><span data-stu-id="6a417-153">*Unity camera settings*</span></span>

<span data-ttu-id="6a417-154">启用 "受支持的虚拟现实" 复选框后, [Unity 相机](camera-in-unity.md)组件将处理[头跟踪和 stereoscopic 渲染](rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="6a417-154">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="6a417-155">不需要将其替换为自定义相机即可执行此操作。</span><span class="sxs-lookup"><span data-stu-id="6a417-155">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="6a417-156">如果你的应用程序专门面向 HoloLens, 则需要更改一些设置以优化设备的透明显示, 因此你的应用程序将向物理环境显示:</span><span class="sxs-lookup"><span data-stu-id="6a417-156">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="6a417-157">在**层次结构**中, 选择**主相机**</span><span class="sxs-lookup"><span data-stu-id="6a417-157">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="6a417-158">在 "**检查器**" 面板中, 将转换**位置**设置为**0, 0, 0,** 以使用户头部的位置从 Unity 世界原点开始。</span><span class="sxs-lookup"><span data-stu-id="6a417-158">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="6a417-159">将**清除标志**更改为**纯色**。</span><span class="sxs-lookup"><span data-stu-id="6a417-159">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="6a417-160">将**背景**色更改为**RGBA 0, 0, 0, 0**。</span><span class="sxs-lookup"><span data-stu-id="6a417-160">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="6a417-161">在 HoloLens 中, 黑色呈现为透明。</span><span class="sxs-lookup"><span data-stu-id="6a417-161">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="6a417-162">更改**剪辑平面-接近**于[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 (米)。</span><span class="sxs-lookup"><span data-stu-id="6a417-162">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="6a417-163">如果删除并创建新的相机, 请确保将相机**标记**为 " **MainCamera**"。</span><span class="sxs-lookup"><span data-stu-id="6a417-163">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>


## <a name="see-also"></a><span data-ttu-id="6a417-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a417-164">See also</span></span>
* [<span data-ttu-id="6a417-165">混合现实工具包 v2</span><span class="sxs-lookup"><span data-stu-id="6a417-165">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="6a417-166">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="6a417-166">Unity Development Overview</span></span>](unity-development-overview.md)
