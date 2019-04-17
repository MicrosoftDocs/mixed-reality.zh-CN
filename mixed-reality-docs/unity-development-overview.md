---
title: Unity 开发概述
description: 获取开始的生成混合现实应用在 Unity 中。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity 中，混合现实、 开发、 入门、 新的项目、 移植、 功能、 照相机、 模拟、 仿真、 文档
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592957"
---
# <a name="unity-development-overview"></a><span data-ttu-id="50760-104">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="50760-104">Unity development overview</span></span>

<span data-ttu-id="50760-105">生成最快的途径[mixed 的 reality 应用](app-views.md)是与[Unity](http://aka.ms/HoloLensUnity)。</span><span class="sxs-lookup"><span data-stu-id="50760-105">The fastest path to building a [mixed reality app](app-views.md) is with [Unity](http://aka.ms/HoloLensUnity).</span></span> <span data-ttu-id="50760-106">我们建议你花些时间浏览[Unity 教程](https://unity3d.com/learn/tutorials)。</span><span class="sxs-lookup"><span data-stu-id="50760-106">We recommend you take the time to explore the [Unity tutorials](https://unity3d.com/learn/tutorials).</span></span> <span data-ttu-id="50760-107">如果你需要将资产，Unity 广[资产存储库](https://www.assetstore.unity3d.com/)。</span><span class="sxs-lookup"><span data-stu-id="50760-107">If you need assets, Unity has a comprehensive [Asset Store](https://www.assetstore.unity3d.com/).</span></span> <span data-ttu-id="50760-108">一旦已建立的 Unity 一个基本的了解，您可以访问[混合现实学院](academy.md)若要了解使用 Unity 的混合的现实开发的详细信息。</span><span class="sxs-lookup"><span data-stu-id="50760-108">Once you have built up a basic understanding of Unity, you can visit the [Mixed Reality Academy](academy.md) to learn the specifics of mixed reality development with Unity.</span></span> <span data-ttu-id="50760-109">请确保访问[Unity 混合现实论坛](http://forum.unity3d.com/forums/hololens.102/)与社区构建在 Unity 中的混合的现实应用的其余部分，并找到可能会遇到的问题的解决方案。</span><span class="sxs-lookup"><span data-stu-id="50760-109">Be sure to visit the [Unity Mixed Reality forums](http://forum.unity3d.com/forums/hololens.102/) to engage with the rest of the community building mixed reality apps in Unity and find solutions to problems you might run into.</span></span>

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a><span data-ttu-id="50760-110">移植到 Windows Mixed Reality 现有的 Unity 应用</span><span class="sxs-lookup"><span data-stu-id="50760-110">Porting an existing Unity app to Windows Mixed Reality</span></span>

<span data-ttu-id="50760-111">如果有现有的 Unity 项目正在移植到 Windows Mixed Reality 的请按照[Unity 移植指南](porting-guides.md)若要开始。</span><span class="sxs-lookup"><span data-stu-id="50760-111">If you have an existing Unity project that you're porting to Windows Mixed Reality, follow along with the [Unity porting guide](porting-guides.md) to get started.</span></span>

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="50760-112">为 Windows Mixed Reality 配置新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="50760-112">Configuring a new Unity project for Windows Mixed Reality</span></span>

<span data-ttu-id="50760-113">若要开始构建使用 Unity，混合的现实应用首先[安装的工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="50760-113">To get started building mixed reality apps with Unity, first [install the tools](install-the-tools.md).</span></span> <span data-ttu-id="50760-114">如果你将面向 Windows Mixed Reality 沉浸式耳机而不是 HoloLens，将现在需要 Unity 的特殊版本。</span><span class="sxs-lookup"><span data-stu-id="50760-114">If you'll be targeting Windows Mixed Reality immersive headsets rather than HoloLens, you'll need a special version of Unity for now.</span></span>

<span data-ttu-id="50760-115">如果只需创建新的 Unity 项目后，有少量的 Unity 设置，将需要更改 Windows Mixed Reality，划分为两个类别： 每个项目和每个场景。</span><span class="sxs-lookup"><span data-stu-id="50760-115">If you've just created a new Unity project, there are a small set of Unity settings you'll need to change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

### <a name="per-project-settings"></a><span data-ttu-id="50760-116">每个项目设置</span><span class="sxs-lookup"><span data-stu-id="50760-116">Per-project settings</span></span>

<span data-ttu-id="50760-117">若要针对 Windows Mixed Reality，首先需要设置你的 Unity 项目以导出为通用 Windows 平台应用：</span><span class="sxs-lookup"><span data-stu-id="50760-117">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span>
1. <span data-ttu-id="50760-118">选择**文件 > 生成设置...**</span><span class="sxs-lookup"><span data-stu-id="50760-118">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="50760-119">选择**通用 Windows 平台**在平台中列表，并单击**交换机平台**</span><span class="sxs-lookup"><span data-stu-id="50760-119">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="50760-120">设置**SDK**到**通用 10**</span><span class="sxs-lookup"><span data-stu-id="50760-120">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="50760-121">设置**目标设备**到**任一设备**以支持沉浸式耳机或切换到**HoloLens**</span><span class="sxs-lookup"><span data-stu-id="50760-121">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="50760-122">设置**生成的类型**到**D3D**</span><span class="sxs-lookup"><span data-stu-id="50760-122">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="50760-123">设置**UWP SDK**到**最新安装**</span><span class="sxs-lookup"><span data-stu-id="50760-123">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="50760-124">然后，我们需要让 Unity 知道我们尝试导出该应用应创建[沉浸式视图](app-views.md)而不是二维视图。</span><span class="sxs-lookup"><span data-stu-id="50760-124">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="50760-125">我们通过启用"虚拟现实支持"中执行的操作：</span><span class="sxs-lookup"><span data-stu-id="50760-125">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="50760-126">从**生成设置...** 窗口中，打开**播放器设置...**</span><span class="sxs-lookup"><span data-stu-id="50760-126">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="50760-127">选择**通用 Windows 平台的设置**选项卡</span><span class="sxs-lookup"><span data-stu-id="50760-127">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="50760-128">展开**XR 设置**组</span><span class="sxs-lookup"><span data-stu-id="50760-128">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="50760-129">在中**XR 设置**部分中，选择**受支持的虚拟现实**复选框以添加**虚拟现实设备**列表。</span><span class="sxs-lookup"><span data-stu-id="50760-129">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="50760-130">在中**XR 设置**组中，确认 **"Windows Mixed Reality"** 被列为受支持的设备。</span><span class="sxs-lookup"><span data-stu-id="50760-130">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="50760-131">（这可能显示为"Windows Holographic"在较旧版本的 Unity）</span><span class="sxs-lookup"><span data-stu-id="50760-131">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="50760-132">您的应用程序现在可以执行基本全息呈现和空间的输入。</span><span class="sxs-lookup"><span data-stu-id="50760-132">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="50760-133">若要更进一步，充分利用特定功能，你的应用必须声明其清单中的相应功能。</span><span class="sxs-lookup"><span data-stu-id="50760-133">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="50760-134">可以在 Unity 中进行的清单的声明，以便将它们包括在每个后续项目导出。</span><span class="sxs-lookup"><span data-stu-id="50760-134">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="50760-135">该设置位于**播放器设置 > 通用 Windows 平台的设置 > 发布设置 > 功能**。</span><span class="sxs-lookup"><span data-stu-id="50760-135">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="50760-136">启用的常用的 Unity Api 的混合现实适用的功能包括：</span><span class="sxs-lookup"><span data-stu-id="50760-136">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="50760-137">功能</span><span class="sxs-lookup"><span data-stu-id="50760-137">Capability</span></span>  |  <span data-ttu-id="50760-138">Api，需要功能</span><span class="sxs-lookup"><span data-stu-id="50760-138">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="50760-139">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="50760-139">SpatialPerception</span></span>  |  <span data-ttu-id="50760-140">SurfaceObserver (访问权限[空间映射](spatial-mapping.md)网格上 HoloLens)&mdash;*所需的常规空间头戴式跟踪没有任何功能*</span><span class="sxs-lookup"><span data-stu-id="50760-140">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="50760-141">网络摄像头</span><span class="sxs-lookup"><span data-stu-id="50760-141">WebCam</span></span>  |  <span data-ttu-id="50760-142">PhotoCapture 和 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="50760-142">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="50760-143">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="50760-143">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="50760-144">PhotoCapture 或 VideoCapture，分别 （时存储捕获的内容）</span><span class="sxs-lookup"><span data-stu-id="50760-144">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="50760-145">麦克风</span><span class="sxs-lookup"><span data-stu-id="50760-145">Microphone</span></span>  |  <span data-ttu-id="50760-146">VideoCapture （时捕获音频）、 DictationRecognizer、 GrammarRecognizer 和 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="50760-146">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="50760-147">InternetClient</span><span class="sxs-lookup"><span data-stu-id="50760-147">InternetClient</span></span>  |  <span data-ttu-id="50760-148">DictationRecognizer （并使用 Unity Profiler）</span><span class="sxs-lookup"><span data-stu-id="50760-148">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="50760-149">**Unity 质量设置**</span><span class="sxs-lookup"><span data-stu-id="50760-149">**Unity quality settings**</span></span>

<span data-ttu-id="50760-150">![Unity 质量设置](images/unityqualitysettings-350px.png)</span><span class="sxs-lookup"><span data-stu-id="50760-150">![Unity quality settings](images/unityqualitysettings-350px.png)</span></span><br>
<span data-ttu-id="50760-151">*Unity 质量设置*</span><span class="sxs-lookup"><span data-stu-id="50760-151">*Unity quality settings*</span></span>

<span data-ttu-id="50760-152">HoloLens 有移动类 GPU。</span><span class="sxs-lookup"><span data-stu-id="50760-152">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="50760-153">如果您的应用程序面向 HoloLens，则需要针对最快的性能优化的质量设置以确保我们保持完整的帧速率：</span><span class="sxs-lookup"><span data-stu-id="50760-153">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="50760-154">选择**编辑 > 项目设置 > 质量**</span><span class="sxs-lookup"><span data-stu-id="50760-154">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="50760-155">选择**下拉列表中**下**Windows 应用商店**徽标，然后选择**Fastest**。</span><span class="sxs-lookup"><span data-stu-id="50760-155">Select the **dropdown** under the **Windows Store** logo and select **Fastest**.</span></span> <span data-ttu-id="50760-156">您将知道当正确应用了设置 Windows 应用商店列中的框并**Fastest**行都显示为绿色。</span><span class="sxs-lookup"><span data-stu-id="50760-156">You'll know the setting is applied correctly when the box in the Windows Store column and **Fastest** row is green.</span></span>

### <a name="per-scene-settings"></a><span data-ttu-id="50760-157">每个场景设置</span><span class="sxs-lookup"><span data-stu-id="50760-157">Per-scene settings</span></span>

<span data-ttu-id="50760-158">**Unity 照相机设置**</span><span class="sxs-lookup"><span data-stu-id="50760-158">**Unity camera settings**</span></span>

<span data-ttu-id="50760-159">![Unity 照相机设置](images/unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="50760-159">![Unity camera settings](images/unitycamerasettings.png)</span></span><br>
<span data-ttu-id="50760-160">*Unity 照相机设置*</span><span class="sxs-lookup"><span data-stu-id="50760-160">*Unity camera settings*</span></span>

<span data-ttu-id="50760-161">可以在"虚拟现实支持"复选框，一旦[Unity 照相机](camera-in-unity.md)组件句柄[头跟踪和立体呈现](rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="50760-161">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="50760-162">没有无需将其替换为自定义在相机上以执行此操作。</span><span class="sxs-lookup"><span data-stu-id="50760-162">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="50760-163">如果您的应用程序专门面向 HoloLens，有几个需要更改以使您的应用程序将通过显示物理世界的设备的透明显示优化的设置：</span><span class="sxs-lookup"><span data-stu-id="50760-163">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="50760-164">在中**层次结构**，选择**Main Camera**</span><span class="sxs-lookup"><span data-stu-id="50760-164">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="50760-165">在**Inspector**面板中，将转换**位置**到**0，0，0**以便用户头位置始于 Unity 世界原点。</span><span class="sxs-lookup"><span data-stu-id="50760-165">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="50760-166">更改**清除标志**到**纯色**。</span><span class="sxs-lookup"><span data-stu-id="50760-166">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="50760-167">更改**背景**颜色**RGBA 0,0,0,0**。</span><span class="sxs-lookup"><span data-stu-id="50760-167">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="50760-168">黑色将呈现为透明的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="50760-168">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="50760-169">更改**剪裁平面的附近**到[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 （米）。</span><span class="sxs-lookup"><span data-stu-id="50760-169">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="50760-170">如果你删除并创建一个新的照相机，请确保您的照相机**标记**作为**MainCamera**。</span><span class="sxs-lookup"><span data-stu-id="50760-170">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="50760-171">添加混合的现实功能和输入</span><span class="sxs-lookup"><span data-stu-id="50760-171">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="50760-172">一旦您已配置你的项目，如上文所述，标准 Unity 游戏对象 （如照相机） 将亮起立即用于**固定缩放体验**，使用自动更新以用户身份的照相机的位置将移动通过世界其头。</span><span class="sxs-lookup"><span data-stu-id="50760-172">Once you've configured your project as described above, standard Unity game objects (such as the camera) will light up immediately for a **seated-scale experience**, with the camera's position updated automatically as the user moves their head through the world.</span></span>

<span data-ttu-id="50760-173">添加对 Windows Mixed Reality 功能的支持，如[空间阶段](coordinate-systems.md#spatial-coordinate-systems)，[手势、 运动控制器](gestures-and-motion-controllers-in-unity.md)或[语音输入](voice-input-in-unity.md)使用直接内置 Api 实现Unity。</span><span class="sxs-lookup"><span data-stu-id="50760-173">Adding support for Windows Mixed Reality features such as [spatial stages](coordinate-systems.md#spatial-coordinate-systems), [gestures, motion controllers](gestures-and-motion-controllers-in-unity.md) or [voice input](voice-input-in-unity.md) is achieved using APIs built directly into Unity.</span></span>

<span data-ttu-id="50760-174">第一步应查看[体验刻度](coordinate-systems.md)可面向您的应用程序：</span><span class="sxs-lookup"><span data-stu-id="50760-174">Your first step should be to review the [experience scales](coordinate-systems.md) that your app can target:</span></span>
* <span data-ttu-id="50760-175">如果您要建立**方向限**或**固定缩放体验**，将需要设置 Unity 的跟踪到的空间类型[保持静止](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="50760-175">If you're looking to build an **orientation-only** or **seated-scale experience**, you'll need to set Unity's tracking space type to [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="50760-176">如果您要建立**现有规模**或**聊天室规模体验**，将需要确保 Unity 的跟踪空间类型已成功设置为[RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)。</span><span class="sxs-lookup"><span data-stu-id="50760-176">If you're looking to build a **standing-scale** or **room-scale experience**, you'll need to ensure Unity's tracking space type is successfully set to [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).</span></span>
* <span data-ttu-id="50760-177">如果您要建立**世界级**上 HoloLens，体验让用户超出 5 米漫游，您将需要使用[WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience)组件。</span><span class="sxs-lookup"><span data-stu-id="50760-177">If you're looking to build a **world-scale** experience on HoloLens, letting users roam beyond 5 meters, you'll need to use the [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) component.</span></span>

<span data-ttu-id="50760-178">中与其他 Unity Api 一致的方式公开所有混合的现实应用程序的核心构建基块：</span><span class="sxs-lookup"><span data-stu-id="50760-178">All of the core building blocks for mixed reality apps are exposed in a manner consistent with other Unity APIs:</span></span>
* [<span data-ttu-id="50760-179">摄像头</span><span class="sxs-lookup"><span data-stu-id="50760-179">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="50760-180">坐标系统</span><span class="sxs-lookup"><span data-stu-id="50760-180">Coordinate systems</span></span>](coordinate-systems-in-unity.md)
* [<span data-ttu-id="50760-181">Gaze</span><span class="sxs-lookup"><span data-stu-id="50760-181">Gaze</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="50760-182">手势和动作控制器</span><span class="sxs-lookup"><span data-stu-id="50760-182">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="50760-183">语音输入</span><span class="sxs-lookup"><span data-stu-id="50760-183">Voice input</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="50760-184">暂留</span><span class="sxs-lookup"><span data-stu-id="50760-184">Persistence</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="50760-185">空间声音</span><span class="sxs-lookup"><span data-stu-id="50760-185">Spatial sound</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="50760-186">空间映射</span><span class="sxs-lookup"><span data-stu-id="50760-186">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="50760-187">有，许多混合的现实应用程序将需要使用，这还公开到 Unity 应用其他主要功能：</span><span class="sxs-lookup"><span data-stu-id="50760-187">There are other key features that many mixed reality apps will want to use, which are also exposed to Unity apps:</span></span>
* [<span data-ttu-id="50760-188">共享的体验</span><span class="sxs-lookup"><span data-stu-id="50760-188">Shared experiences</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="50760-189">可定位照相机</span><span class="sxs-lookup"><span data-stu-id="50760-189">Locatable camera</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="50760-190">焦点</span><span class="sxs-lookup"><span data-stu-id="50760-190">Focus point</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="50760-191">跟踪丢失</span><span class="sxs-lookup"><span data-stu-id="50760-191">Tracking loss</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="50760-192">键盘</span><span class="sxs-lookup"><span data-stu-id="50760-192">Keyboard</span></span>](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a><span data-ttu-id="50760-193">在真实或模拟设备上运行你的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="50760-193">Running your Unity project on a real or simulated device</span></span>

<span data-ttu-id="50760-194">一旦您购买了全息 Unity 项目准备好测试，在下一步是向[导出并构建 Unity 的 Visual Studio 的解决方案](exporting-and-building-a-unity-visual-studio-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="50760-194">Once you've got your holographic Unity project ready to test out, your next step is to [export and build a Unity Visual Studio solution](exporting-and-building-a-unity-visual-studio-solution.md).</span></span>

<span data-ttu-id="50760-195">掌握该 VS 解决方案，然后，可以运行您的应用程序中有三种方法，使用真实或模拟设备：</span><span class="sxs-lookup"><span data-stu-id="50760-195">With that VS solution in hand, you can then run your app in one of three ways, using either a real or simulated device:</span></span>
* [<span data-ttu-id="50760-196">将部署到实际 HoloLens 或 Windows Mixed Reality 沉浸式头戴式耳机</span><span class="sxs-lookup"><span data-stu-id="50760-196">Deploy to a real HoloLens or Windows Mixed Reality immersive headset</span></span>](using-visual-studio.md)
* [<span data-ttu-id="50760-197">将部署到 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="50760-197">Deploy to the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="50760-198">将部署到 Windows Mixed Reality 沉浸式头戴式模拟器</span><span class="sxs-lookup"><span data-stu-id="50760-198">Deploy to the Windows Mixed Reality immersive headset simulator</span></span>](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a><span data-ttu-id="50760-199">Unity 文档</span><span class="sxs-lookup"><span data-stu-id="50760-199">Unity documentation</span></span>

<span data-ttu-id="50760-200">除了此文档可在 Windows 开发人员中心，Unity 将安装 Windows Mixed Reality 功能以及 Unity 编辑器中的文档。</span><span class="sxs-lookup"><span data-stu-id="50760-200">In addition to this documentation available on the Windows Dev Center, Unity installs documentation for Windows Mixed Reality functionality alongside the Unity Editor.</span></span> <span data-ttu-id="50760-201">Unity 提供文档包括两个单独的部分：</span><span class="sxs-lookup"><span data-stu-id="50760-201">The Unity provided documentation includes two separate sections:</span></span>
1. <span data-ttu-id="50760-202">**Unity 脚本参考**</span><span class="sxs-lookup"><span data-stu-id="50760-202">**Unity scripting reference**</span></span>
    * <span data-ttu-id="50760-203">文档的此部分包含 Unity 提供了脚本编写 API 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="50760-203">This section of the documentation contains details of the scripting API that Unity provides.</span></span>
    * <span data-ttu-id="50760-204">可与 Unity 编辑器通过访问**帮助 > 脚本参考**</span><span class="sxs-lookup"><span data-stu-id="50760-204">Accessible from the Unity Editor through **Help > Scripting Reference**</span></span>
2. <span data-ttu-id="50760-205">**Unity 手动**</span><span class="sxs-lookup"><span data-stu-id="50760-205">**Unity manual**</span></span>
    * <span data-ttu-id="50760-206">此手册旨在帮助您了解如何使用 Unity 中，从基本到高级方法。</span><span class="sxs-lookup"><span data-stu-id="50760-206">This manual is designed to help you learn how to use Unity, from basic to advanced techniques.</span></span>
    * <span data-ttu-id="50760-207">可与 Unity 编辑器通过访问**帮助 > 手动**</span><span class="sxs-lookup"><span data-stu-id="50760-207">Accessible from the Unity Editor through **Help > Manual**</span></span>

## <a name="see-also"></a><span data-ttu-id="50760-208">请参阅</span><span class="sxs-lookup"><span data-stu-id="50760-208">See also</span></span>
* [<span data-ttu-id="50760-209">MR 基础知识 100:开始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="50760-209">MR Basics 100: Getting started with Unity</span></span>](holograms-100.md)
* [<span data-ttu-id="50760-210">Unity 的推荐的设置</span><span class="sxs-lookup"><span data-stu-id="50760-210">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="50760-211">Unity 的性能建议</span><span class="sxs-lookup"><span data-stu-id="50760-211">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="50760-212">导出和构建 Unity 的 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="50760-212">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="50760-213">适用于 Unity 应用的 Windows 命名空间用于 HoloLens</span><span class="sxs-lookup"><span data-stu-id="50760-213">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [<span data-ttu-id="50760-214">使用 Unity 和 Visual Studio 的最佳实践</span><span class="sxs-lookup"><span data-stu-id="50760-214">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="50760-215">Unity 游戏模式</span><span class="sxs-lookup"><span data-stu-id="50760-215">Unity Play Mode</span></span>](unity-play-mode.md)
* [<span data-ttu-id="50760-216">移植指南</span><span class="sxs-lookup"><span data-stu-id="50760-216">Porting guides</span></span>](porting-guides.md)
