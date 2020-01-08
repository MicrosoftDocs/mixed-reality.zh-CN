---
title: MRTK 101-如何将混合现实工具包 Unity 用于基本交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
description: 如何将混合现实工具包 Unity 用于基本交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens，MRTK，混合现实工具包，Windows Mixed Reality，设计，示例应用，控件
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623497"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="0319e-104">MRTK 101：如何将混合现实工具包 Unity 用于基本交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）</span><span class="sxs-lookup"><span data-stu-id="0319e-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="0319e-106">了解如何使用 MRTK 在混合现实中实现最广泛使用的常见交互模式。</span><span class="sxs-lookup"><span data-stu-id="0319e-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="0319e-107">如何在 Unity 编辑器中模拟输入交互？</span><span class="sxs-lookup"><span data-stu-id="0319e-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="0319e-108">如何获取和移动对象？</span><span class="sxs-lookup"><span data-stu-id="0319e-108">How to grab and move an object?</span></span>
- <span data-ttu-id="0319e-109">如何调整对象的大小？</span><span class="sxs-lookup"><span data-stu-id="0319e-109">How to resize an object?</span></span>
- <span data-ttu-id="0319e-110">如何以精确方式移动或旋转对象？</span><span class="sxs-lookup"><span data-stu-id="0319e-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="0319e-111">如何使对象响应输入事件？</span><span class="sxs-lookup"><span data-stu-id="0319e-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="0319e-112">如何添加视觉反馈？</span><span class="sxs-lookup"><span data-stu-id="0319e-112">How to add visual feedback?</span></span>
- <span data-ttu-id="0319e-113">如何添加音频反馈？</span><span class="sxs-lookup"><span data-stu-id="0319e-113">How to add audio feedback?</span></span>
- <span data-ttu-id="0319e-114">如何使用 HoloLens 2 样式按钮 prototyping？</span><span class="sxs-lookup"><span data-stu-id="0319e-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="0319e-115">如何使对象符合您的需要？</span><span class="sxs-lookup"><span data-stu-id="0319e-115">How to make an object follow you?</span></span>
- <span data-ttu-id="0319e-116">如何制作对象？</span><span class="sxs-lookup"><span data-stu-id="0319e-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="0319e-117">如何在 Unity 编辑器中模拟输入交互？</span><span class="sxs-lookup"><span data-stu-id="0319e-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="0319e-118">MRTK 支持编辑器内输入模拟。</span><span class="sxs-lookup"><span data-stu-id="0319e-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="0319e-119">只需单击 Unity 的 "播放" 按钮即可运行场景。</span><span class="sxs-lookup"><span data-stu-id="0319e-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="0319e-120">使用这些密钥来模拟输入。</span><span class="sxs-lookup"><span data-stu-id="0319e-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="0319e-121">按 W、A、S、D 键移动相机。</span><span class="sxs-lookup"><span data-stu-id="0319e-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="0319e-122">按住鼠标右键，并移动鼠标以进行浏览。</span><span class="sxs-lookup"><span data-stu-id="0319e-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="0319e-123">若要启动模拟的操作，请按空格键（右手）或左移键（左移）以在视图中继续模拟，按 T 或 Y 键旋转模拟手势，按 Q 或 E （水平）</span><span class="sxs-lookup"><span data-stu-id="0319e-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="0319e-124">在 MRTK 文档中了解有关输入模拟的详细信息</span><span class="sxs-lookup"><span data-stu-id="0319e-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="0319e-125">如何获取和移动对象？</span><span class="sxs-lookup"><span data-stu-id="0319e-125">How to grab and move an object?</span></span>
<span data-ttu-id="0319e-126">若要使对象 grabbable，请分配以下两个脚本： ManipulationHandler.cs 和 NearInteractionGrabbable （对于带有清晰的手动跟踪输入的直接抓取） ManipulationHandler 同时支持近距离和远距离交互。</span><span class="sxs-lookup"><span data-stu-id="0319e-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="0319e-127">您可以使用 HoloLens 2 的可表述的手动跟踪输入（附近）、一种手 ray （far）、运动控制器的无线横梁（far）、HoloLens 注视光标 & 的空中点来获取和移动对象。</span><span class="sxs-lookup"><span data-stu-id="0319e-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="0319e-128">如何调整对象的大小？</span><span class="sxs-lookup"><span data-stu-id="0319e-128">How to resize an object?</span></span>
<span data-ttu-id="0319e-129">ManipulationHandler.cs 支持双向缩放/旋转。</span><span class="sxs-lookup"><span data-stu-id="0319e-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="0319e-130">这适用于各种输入类型，例如，HoloLens 2 的有向右输入、HoloLens 1 的注视 + 手势输入和 Windows Mixed Reality 沉浸式耳机的运动控制器输入。</span><span class="sxs-lookup"><span data-stu-id="0319e-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="0319e-131">在 MRTK 文档中详细了解操作处理程序</span><span class="sxs-lookup"><span data-stu-id="0319e-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="0319e-132">如何以精确方式移动或旋转对象？</span><span class="sxs-lookup"><span data-stu-id="0319e-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="0319e-133">将 BoundingBox.cs 分配给对象以使用边界框，这是用于缩放和旋转对象的接口。</span><span class="sxs-lookup"><span data-stu-id="0319e-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="0319e-134">默认情况下，它会显示1个 HoloLens 样式的蓝色控点和线路。</span><span class="sxs-lookup"><span data-stu-id="0319e-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="0319e-135">若要使用基于的 HoloLens 2 样式邻近动画句柄，需要分配 prototyping 和材料。</span><span class="sxs-lookup"><span data-stu-id="0319e-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="0319e-136">有关配置详细信息，请参阅[边界框文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)和 BoundingBoxExamples 场景。</span><span class="sxs-lookup"><span data-stu-id="0319e-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="0319e-137">在 MRTK 文档中了解有关边界框的详细信息</span><span class="sxs-lookup"><span data-stu-id="0319e-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="0319e-138">如何使对象响应输入事件？</span><span class="sxs-lookup"><span data-stu-id="0319e-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="0319e-139">将 PointerHandler.cs 分配给对象。</span><span class="sxs-lookup"><span data-stu-id="0319e-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="0319e-140">在检查器中，你将能够使用事件 OnPointerDown （）、OnPointerUp （）、OnPointerClicked （）、OnPointerDragged （）在脚本中使用这些事件，实现 IMixedRealityPointerHandler。</span><span class="sxs-lookup"><span data-stu-id="0319e-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="0319e-141">在 MRTK 文档中了解有关输入系统的详细信息</span><span class="sxs-lookup"><span data-stu-id="0319e-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="0319e-142">如何添加视觉反馈？</span><span class="sxs-lookup"><span data-stu-id="0319e-142">How to add visual feedback?</span></span>
<span data-ttu-id="0319e-143">将 Interactable.cs 分配给对象。</span><span class="sxs-lookup"><span data-stu-id="0319e-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="0319e-144">在检查器中创建一个新主题。</span><span class="sxs-lookup"><span data-stu-id="0319e-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="0319e-145">使用种不可交互的主题配置文件，你可以轻松地将视觉反馈添加到所有可用的输入交互状态。</span><span class="sxs-lookup"><span data-stu-id="0319e-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="0319e-146">种不可交互提供各种类型的主题，其中包括着色器主题，可用于控制每个交互状态着色器的属性。</span><span class="sxs-lookup"><span data-stu-id="0319e-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="0319e-147">在 MRTK 文档中了解有关种不可交互的详细信息</span><span class="sxs-lookup"><span data-stu-id="0319e-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="0319e-148">用于可视反馈的另一个重要的构建基块是 MRTK 标准着色器。</span><span class="sxs-lookup"><span data-stu-id="0319e-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="0319e-149">借助 MRTK 标准着色器，你可以轻松地添加视觉对象反馈效果，如悬停光线和邻近性光线。</span><span class="sxs-lookup"><span data-stu-id="0319e-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="0319e-150">由于 MRTK 标准着色器比 Unity 标准着色器执行的计算要少得多，因此您可以创建性能良好的体验。</span><span class="sxs-lookup"><span data-stu-id="0319e-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="0319e-151">创建新的材料，并选择着色器的混合现实工具包 > 标准 "。</span><span class="sxs-lookup"><span data-stu-id="0319e-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="0319e-152">或者，您可以选择使用 MRTK 标准着色器的现有材料之一。</span><span class="sxs-lookup"><span data-stu-id="0319e-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="0319e-153">有关 MRTK 标准着色器的详细信息，请参阅 MRTK 文档</span><span class="sxs-lookup"><span data-stu-id="0319e-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="0319e-154">如何添加音频反馈？</span><span class="sxs-lookup"><span data-stu-id="0319e-154">How to add audio feedback?</span></span>
<span data-ttu-id="0319e-155">将 AudioSource 添加到对象。</span><span class="sxs-lookup"><span data-stu-id="0319e-155">Add AudioSource to an object.</span></span> <span data-ttu-id="0319e-156">然后，在公开输入事件的脚本（例如 Interactable.cs 或 PointerHandler.cs）中，将对象分配给该事件，并选择 AudioSource。 PlayOneShot （）。</span><span class="sxs-lookup"><span data-stu-id="0319e-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="0319e-157">可以使用音频剪辑，或从 MRTK 的音频资产中进行选择。</span><span class="sxs-lookup"><span data-stu-id="0319e-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="0319e-158">如何使用 HoloLens 2 样式按钮 prototyping？</span><span class="sxs-lookup"><span data-stu-id="0319e-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="0319e-159">MRTK 提供各种类型的 HoloLens 2 shell （OS）样式按钮。</span><span class="sxs-lookup"><span data-stu-id="0319e-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="0319e-160">它提供了复杂的视觉对象反馈，例如邻近感应、压缩框和按钮表面上的波纹效果。</span><span class="sxs-lookup"><span data-stu-id="0319e-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="0319e-161">只需将其中一个 HoloLens 2 样式的 pressable 按钮拖放到场景中即可。</span><span class="sxs-lookup"><span data-stu-id="0319e-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="0319e-162">Prefab 使用上面介绍的 Interactable.cs。</span><span class="sxs-lookup"><span data-stu-id="0319e-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="0319e-163">可以在种不可交互中使用已公开的事件（如 OnClick （））来触发操作。</span><span class="sxs-lookup"><span data-stu-id="0319e-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="0319e-164">在 MRTK 文档中了解有关按钮 prototyping 的详细信息</span><span class="sxs-lookup"><span data-stu-id="0319e-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="0319e-165">如何使对象符合您的需要？</span><span class="sxs-lookup"><span data-stu-id="0319e-165">How to make an object follow you?</span></span>
<span data-ttu-id="0319e-166">将 RadialView.cs 脚本分配给对象。</span><span class="sxs-lookup"><span data-stu-id="0319e-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="0319e-167">它是规划求解脚本系列的一部分，可用于在三维空间中实现各种类型的对象定位。</span><span class="sxs-lookup"><span data-stu-id="0319e-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="0319e-168">将自动添加 SolverHandler.cs。</span><span class="sxs-lookup"><span data-stu-id="0319e-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="0319e-169">下面是 RadialView 配置的一个示例，用于实现 "延迟跟随" 标记和操作，就像使用 HoloLens shell 中的 "开始" 菜单。</span><span class="sxs-lookup"><span data-stu-id="0319e-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="0319e-170">您可以指定最小/最大距离和最小/最大视图度。</span><span class="sxs-lookup"><span data-stu-id="0319e-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="0319e-171">下面的示例演示了如何在15°内将对象放置在 0.4 m 和 0.8 m 范围之间。</span><span class="sxs-lookup"><span data-stu-id="0319e-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="0319e-172">调整 Lerp 时间值，以使位置更新速度更快或更慢。</span><span class="sxs-lookup"><span data-stu-id="0319e-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="0319e-173">在 MRTK 文档中了解有关 Solvers 的详细信息</span><span class="sxs-lookup"><span data-stu-id="0319e-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="0319e-174">如何制作对象？</span><span class="sxs-lookup"><span data-stu-id="0319e-174">How to make an object face you?</span></span>
<span data-ttu-id="0319e-175">将 Billboard.cs 脚本分配给对象。</span><span class="sxs-lookup"><span data-stu-id="0319e-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="0319e-176">无论您的位置如何，都将始终面对您。</span><span class="sxs-lookup"><span data-stu-id="0319e-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="0319e-177">您可以指定 "轴" 选项。</span><span class="sxs-lookup"><span data-stu-id="0319e-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="0319e-178">准备好为混合现实创建令人惊叹的体验？</span><span class="sxs-lookup"><span data-stu-id="0319e-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="0319e-179">访问以下页面，了解有关 MRTK 和混合现实的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0319e-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="0319e-180">关于作者</span><span class="sxs-lookup"><span data-stu-id="0319e-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="0319e-181"><b>盾 Yoon 停车场</b></span><span class="sxs-lookup"><span data-stu-id="0319e-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="0319e-182">UX 设计器 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="0319e-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="0319e-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0319e-183">See also</span></span>

* [<span data-ttu-id="0319e-184">混合现实工具包-Unity （MRTK） GitHub</span><span class="sxs-lookup"><span data-stu-id="0319e-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="0319e-185">MRTK 文档门户</span><span class="sxs-lookup"><span data-stu-id="0319e-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="0319e-186">入门与 MRTK</span><span class="sxs-lookup"><span data-stu-id="0319e-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="0319e-187">HoloToolkit to MRTK 移植指导原则</span><span class="sxs-lookup"><span data-stu-id="0319e-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
