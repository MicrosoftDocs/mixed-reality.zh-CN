---
title: 在 Unity 中的照相机
description: 如何使用 Unity 的主照相机的 Windows Mixed Reality 开发进行全息呈现
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 全息呈现、 全息版的沉浸式，焦点、 深度缓冲区、 仅限方向、 位置、 不透明且透明的剪辑
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590150"
---
# <a name="camera-in-unity"></a><span data-ttu-id="ddfd8-104">在 Unity 中的照相机</span><span class="sxs-lookup"><span data-stu-id="ddfd8-104">Camera in Unity</span></span>

<span data-ttu-id="ddfd8-105">Wear 混合的现实耳机，它就成为 holographic 世界的中心。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="ddfd8-106">Unity[照相机](http://docs.unity3d.com/Manual/class-Camera.html)组件将会自动处理立体呈现，随着将遵循磁头的移动和旋转时你的项目具有"虚拟现实受支持的"选择"Windows Mixed Reality"中的设备 （Windows 应用商店播放器设置的其他设置部分中）。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-106">The Unity [Camera](http://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and will follow your head movement and rotation when your project has "Virtual Reality Supported" selected with "Windows Mixed Reality" as the device (in the Other Settings section of the Windows Store Player Settings).</span></span> <span data-ttu-id="ddfd8-107">这可能被列为"Windows Holographic"中的 Unity 的较旧版本。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-107">This may be listed as "Windows Holographic" in older versions of Unity.</span></span>

<span data-ttu-id="ddfd8-108">但是，为了全面优化视觉质量并[全息图稳定性](hologram-stability.md)，应设置如下所述的照相机设置。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-108">However, to fully optimize visual quality and [hologram stability](hologram-stability.md), you should set the camera settings described below.</span></span>

>[!NOTE]
><span data-ttu-id="ddfd8-109">这些设置需要应用于您的应用程序的每个场景中的照相机。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-109">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="ddfd8-110">默认情况下，在 Unity 中，创建新的场景时它将包含一个主相机 GameObject 包括照相机组件，但不具有正确应用下面的设置在层次结构中。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-110">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

## <a name="holographic-vs-immersive-headsets"></a><span data-ttu-id="ddfd8-111">与沉浸式耳机全息版</span><span class="sxs-lookup"><span data-stu-id="ddfd8-111">Holographic vs. immersive headsets</span></span>

<span data-ttu-id="ddfd8-112">Unity 照相机组件上的默认设置适用于传统的三维应用程序需要类似于 skybox 的背景，因为没有现实世界的。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-112">The default settings on the Unity Camera component are for traditional 3D applications which need a skybox-like background as they don't have a real world.</span></span>
* <span data-ttu-id="ddfd8-113">运行时**[沉浸式头戴式](immersive-headset-hardware-details.md)**、 呈现所有内容的用户会看到，并因此可能会希望保留 skybox。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-113">When running on an **[immersive headset](immersive-headset-hardware-details.md)**, you are rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="ddfd8-114">但是，运行时**holographic 耳机**等[HoloLens](hololens-hardware-details.md)，实际应显示隐藏所有内容照相机呈现。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-114">However, when running on a **holographic headset** like [HoloLens](hololens-hardware-details.md), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="ddfd8-115">若要执行此操作，设置照相机背景是透明 （在 HoloLens，黑色将呈现为透明) 而不是 Skybox 纹理：</span><span class="sxs-lookup"><span data-stu-id="ddfd8-115">To do this, set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="ddfd8-116">在层次结构面板中选择 Main Camera</span><span class="sxs-lookup"><span data-stu-id="ddfd8-116">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="ddfd8-117">在检查器窗格中，找到此照相机组件并将清除标志下拉列表中从 Skybox 更改为纯色</span><span class="sxs-lookup"><span data-stu-id="ddfd8-117">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="ddfd8-118">选择背景颜色选取器和 RGBA 值更改为 （0，0，0，0）</span><span class="sxs-lookup"><span data-stu-id="ddfd8-118">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="ddfd8-119">可以使用脚本代码来确定在运行时将耳机通过检查是否是沉浸式还是 holographic [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-119">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>


## <a name="positioning-the-camera"></a><span data-ttu-id="ddfd8-120">定位照相机</span><span class="sxs-lookup"><span data-stu-id="ddfd8-120">Positioning the Camera</span></span>

<span data-ttu-id="ddfd8-121">它将是用户的更轻松地布置您的应用程序，如果您想象的起始位置为 （x:0，Y:0，Z:0).</span><span class="sxs-lookup"><span data-stu-id="ddfd8-121">It will be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="ddfd8-122">因为 Main Camera 正在跟踪的用户的头移动，可以通过设置 Main Camera 的起始位置设置用户的起始位置。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-122">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>
1. <span data-ttu-id="ddfd8-123">在层次结构面板中选择 Main Camera</span><span class="sxs-lookup"><span data-stu-id="ddfd8-123">Select Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="ddfd8-124">在检查器窗格中，查找转换组件和更改数据的位置 （x:0，Y:1，z:-10） 到 （x:0，Y:0，Z:0)</span><span class="sxs-lookup"><span data-stu-id="ddfd8-124">In the Inspector panel, find the Transform component and change the Position from (X: 0, Y: 1, Z: -10) to (X: 0, Y: 0, Z: 0)</span></span>

   <span data-ttu-id="ddfd8-125">![在 Unity 中的检查器窗格中的照相机](images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="ddfd8-125">![Camera in the Inspector pane in Unity](images/maincamera-350px.png)</span></span><br>
   <span data-ttu-id="ddfd8-126">*在 Unity 中的检查器窗格中的照相机*</span><span class="sxs-lookup"><span data-stu-id="ddfd8-126">*Camera in the Inspector pane in Unity*</span></span>

## <a name="clip-planes"></a><span data-ttu-id="ddfd8-127">剪辑平面</span><span class="sxs-lookup"><span data-stu-id="ddfd8-127">Clip planes</span></span>

<span data-ttu-id="ddfd8-128">太接近呈现内容的用户可以是混合现实中令人不舒服。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-128">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="ddfd8-129">您可以调整[近和远修剪平面](hologram-stability.md#hologram-render-distances)照相机组件上。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-129">You can adjust the [near and far clip planes](hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>
1. <span data-ttu-id="ddfd8-130">在层次结构面板中选择 Main Camera</span><span class="sxs-lookup"><span data-stu-id="ddfd8-130">Select the Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="ddfd8-131">在检查器窗格中，找到照相机组件中的剪辑平面并从 0.3 更改 Near 文本框中，为.85。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-131">In the Inspector panel, find the Camera component Clipping Planes and change the Near textbox from 0.3 to .85.</span></span> <span data-ttu-id="ddfd8-132">呈现甚至更接近内容可能会导致用户不适，应当避免每个[呈现距离准则](hologram-stability.md#hologram-render-distances)。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-132">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](hologram-stability.md#hologram-render-distances).</span></span>

## <a name="multiple-cameras"></a><span data-ttu-id="ddfd8-133">多个照相机</span><span class="sxs-lookup"><span data-stu-id="ddfd8-133">Multiple Cameras</span></span>

<span data-ttu-id="ddfd8-134">当场景中存在多个照相机组件时，Unity 知道要用于立体呈现的照相机，并且通过检查哪个 GameObject 头跟踪有 MainCamera 标记。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-134">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering and head tracking by checking which GameObject has the MainCamera tag.</span></span>

## <a name="recentering-a-seated-experience"></a><span data-ttu-id="ddfd8-135">Recentering 关注的体验</span><span class="sxs-lookup"><span data-stu-id="ddfd8-135">Recentering a seated experience</span></span>

<span data-ttu-id="ddfd8-136">如果您正在构建[装规模体验](coordinate-systems.md)，你可以通过调用用户的当前头位置处的自动 Unity 的世界原点**[XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 方法。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-136">If you're building a [seated-scale experience](coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>

## <a name="reprojection-modes"></a><span data-ttu-id="ddfd8-137">Reprojection 模式</span><span class="sxs-lookup"><span data-stu-id="ddfd8-137">Reprojection modes</span></span>

<span data-ttu-id="ddfd8-138">HoloLens 和沉浸式耳机将 reproject 您的应用程序呈现时发出 photons 调整用户的实际头位置的任何预测的每个帧。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-138">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="ddfd8-139">默认情况下：</span><span class="sxs-lookup"><span data-stu-id="ddfd8-139">By default:</span></span>

* <span data-ttu-id="ddfd8-140">**沉浸式耳机**将执行位置 reprojection，调整位置和方向，预测你全息，如果应用程序为给定的框架提供了深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-140">**Immersive headsets** will perform positional reprojection, adjusting your holograms for misprediction in both position and orientation, if the app provides a depth buffer for a given frame.</span></span>  <span data-ttu-id="ddfd8-141">如果未提供深度缓冲区，系统将仅更正方向中的错误。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-141">If a depth buffer is not provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="ddfd8-142">**Holographic 耳机**如 HoloLens 将执行位置 reprojection 是否应用程序或不提供其深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-142">**Holographic headsets** like HoloLens will perform positional reprojection whether the app provides its depth buffer or not.</span></span>  <span data-ttu-id="ddfd8-143">呈现通常会是稀疏具有稳定的背景提供的实际位置 reprojection 可能而无需在 HoloLens 上深度缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-143">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

<span data-ttu-id="ddfd8-144">如果您知道您构建[仅限方向的体验](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)严格锁定正文的内容 （例如 360 度视频内容），您可以显式设置 reprojection 模式仅通过设置为方向[HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)到[HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-144">If you know that you are building an [orientation-only experience](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (e.g. 360-degree video content), you can explicitly set the reprojection mode to be orientation only by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>

## <a name="sharing-your-depth-buffers-with-windows"></a><span data-ttu-id="ddfd8-145">与 Windows 共享深度缓冲区</span><span class="sxs-lookup"><span data-stu-id="ddfd8-145">Sharing your depth buffers with Windows</span></span>

<span data-ttu-id="ddfd8-146">你共享的每个帧将您的应用程序为一个提供两个提升全息图稳定性，根据耳机类型中的 Windows 应用的深度缓冲区的呈现：</span><span class="sxs-lookup"><span data-stu-id="ddfd8-146">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>
* <span data-ttu-id="ddfd8-147">**沉浸式耳机**调整位置和方向的预测你全息提供深度缓冲区时可以执行位置 reprojection。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-147">**Immersive headsets** can perform positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="ddfd8-148">**Holographic 耳机**例如，将自动选择 HoloLens[关注点](focus-point-in-unity.md)提供深度缓冲区时，优化全息图稳定性沿相交最内容的平面。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-148">**Holographic headsets** like HoloLens will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span>

<span data-ttu-id="ddfd8-149">若要设置的 Unity 应用将向 Windows 提供深度缓冲区：</span><span class="sxs-lookup"><span data-stu-id="ddfd8-149">To set whether your Unity app will provide a depth buffer to Windows:</span></span>
1. <span data-ttu-id="ddfd8-150">转到**编辑** > **项目设置** > **播放机** > **通用 Windows 平台选项卡**  >  **XR 设置**。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-150">Go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform tab** > **XR Settings**.</span></span>
2. <span data-ttu-id="ddfd8-151">展开**Windows 混合现实 SDK**项。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-151">Expand the **Windows Mixed Reality SDK** item.</span></span>
3. <span data-ttu-id="ddfd8-152">选中或取消选中**启用深度缓冲区共享**复选框。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-152">Check or uncheck the **Enable Depth Buffer Sharing** check box.</span></span>  <span data-ttu-id="ddfd8-153">默认情况下，对于已升级的较旧项目创建，因为此功能已添加到 Unity 并将取消选择的新项目中默认情况下将选中此项。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-153">This will be checked by default in new projects created since this feature was added to Unity and will be unchecked by default for older projects that were upgraded.</span></span>

<span data-ttu-id="ddfd8-154">向 Windows 提供深度缓冲区可以提高视觉质量，只要 Windows 可以准确地映射深度缓冲区中的规范化的每个像素深度值回距离以米为单位，使用在 Unity 中设置主照相机的近和远平面。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-154">Providing a depth buffer to Windows can improve visual quality so long as Windows can accurately map the normalized per-pixel depth values in your depth buffer back to distances in meters, using the near and far planes you've set in Unity on the main camera.</span></span>  <span data-ttu-id="ddfd8-155">如果您呈现器将传递的句柄的深度中的典型方法的值，您通常最好在这里，尽管半透明的呈现器将写传递给深度缓冲区时通过对现有的显示颜色像素可以混淆 reprojection。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-155">If your render passes handle depth values in typical ways, you should generally be fine here, though translucent render passes that write to the depth buffer while showing through to existing color pixels can confuse the reprojection.</span></span>  <span data-ttu-id="ddfd8-156">如果您知道，呈现阶段将保留的最后一个深度像素许多不准确的深度值，您很可能获得更好的视觉质量，通过取消选中"启用深度缓冲区共享"。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-156">If you know that your render passes will leave many of your final depth pixels with inaccurate depth values, you are likely to get better visual quality by unchecking "Enable Depth Buffer Sharing".</span></span>

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a><span data-ttu-id="ddfd8-157">混合的现实工具包自动场景安装程序</span><span class="sxs-lookup"><span data-stu-id="ddfd8-157">Mixed Reality Toolkit's automatic scene setup</span></span>
<span data-ttu-id="ddfd8-158">当您导入[MRTK 发布 Unity 包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或从克隆项目[GitHub 存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，要在 Unity 中查找新菜单混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-158">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="ddfd8-159">在配置菜单中，你会看到菜单应用混合现实场景设置。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-159">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="ddfd8-160">当您单击它时，它默认照相机中删除，并添加基础组件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，并[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-160">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="ddfd8-161">![MRTK 场景设置菜单](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="ddfd8-161">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="ddfd8-162">*MRTK 场景设置菜单*</span><span class="sxs-lookup"><span data-stu-id="ddfd8-162">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="ddfd8-163">![自动场景中 MRTK 的安装程序](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="ddfd8-163">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="ddfd8-164">*自动场景中 MRTK 的安装程序*</span><span class="sxs-lookup"><span data-stu-id="ddfd8-164">*Automatic scene setup in MRTK*</span></span>

## <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="ddfd8-165">MixedRealityCamera 预设</span><span class="sxs-lookup"><span data-stu-id="ddfd8-165">MixedRealityCamera prefab</span></span>
<span data-ttu-id="ddfd8-166">您可以手动添加这些项目面板中。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-166">You can also manually add these from the project panel.</span></span> <span data-ttu-id="ddfd8-167">您可以找到这些组件作为预设。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-167">You can find these components as prefabs.</span></span> <span data-ttu-id="ddfd8-168">当您搜索**MixedRealityCamera**，你将能够看到两个不同的照相机预设。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-168">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="ddfd8-169">其差异是， **MixedRealityCamera**才照相机 prefab 而**MixedRealityCameraParent**包括如 Teleportation，Motion 沉浸式耳机的其他组件控制器和，边界。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-169">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="ddfd8-170">![在 MRTK 照相机预设](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="ddfd8-170">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="ddfd8-171">*在 MRTK 照相机预设*</span><span class="sxs-lookup"><span data-stu-id="ddfd8-171">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="ddfd8-172">**MixedRealtyCamera**支持 HoloLens 和沉浸式头戴式耳机。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-172">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="ddfd8-173">它检测到的设备类型，并优化了清除标志和 Skybox 等属性。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-173">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="ddfd8-174">可以在下面查找一些有用的属性可以自定义光标，Motion 控制器模型，如自定义和 Floor。</span><span class="sxs-lookup"><span data-stu-id="ddfd8-174">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="ddfd8-175">![游标和 Floor 运动控制器属性](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="ddfd8-175">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="ddfd8-176">*游标和 Floor 运动控制器属性*</span><span class="sxs-lookup"><span data-stu-id="ddfd8-176">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="see-also"></a><span data-ttu-id="ddfd8-177">请参阅</span><span class="sxs-lookup"><span data-stu-id="ddfd8-177">See also</span></span>
* [<span data-ttu-id="ddfd8-178">全息图稳定性</span><span class="sxs-lookup"><span data-stu-id="ddfd8-178">Hologram stability</span></span>](hologram-stability.md)
* [<span data-ttu-id="ddfd8-179">MixedRealityToolkit Main Camera.prefab</span><span class="sxs-lookup"><span data-stu-id="ddfd8-179">MixedRealityToolkit Main Camera.prefab</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)