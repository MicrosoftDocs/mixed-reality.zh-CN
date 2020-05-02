---
title: MRTK 101 - 如何使用混合现实工具包 Unity 进行基本的交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
description: 如何使用混合现实工具包 Unity 进行基本的交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, 混合现实工具包, Windows Mixed Reality, 设计, 示例应用, 控件
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028314"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="47c56-104">MRTK 101：如何使用混合现实工具包 Unity 进行基本的交互（HoloLens 2、HoloLens、Windows Mixed Reality、Open VR）</span><span class="sxs-lookup"><span data-stu-id="47c56-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="47c56-106">了解如何使用 MRTK 在混合现实中实现最常用的交互模式。</span><span class="sxs-lookup"><span data-stu-id="47c56-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="47c56-107">如何在 Unity 编辑器中模拟输入交互？</span><span class="sxs-lookup"><span data-stu-id="47c56-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="47c56-108">如何抓取和移动对象？</span><span class="sxs-lookup"><span data-stu-id="47c56-108">How to grab and move an object?</span></span>
- <span data-ttu-id="47c56-109">如何调整对象的大小？</span><span class="sxs-lookup"><span data-stu-id="47c56-109">How to resize an object?</span></span>
- <span data-ttu-id="47c56-110">如何精确移动或旋转对象？</span><span class="sxs-lookup"><span data-stu-id="47c56-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="47c56-111">如何使对象响应输入事件？</span><span class="sxs-lookup"><span data-stu-id="47c56-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="47c56-112">如何添加视觉反馈？</span><span class="sxs-lookup"><span data-stu-id="47c56-112">How to add visual feedback?</span></span>
- <span data-ttu-id="47c56-113">如何添加音频反馈？</span><span class="sxs-lookup"><span data-stu-id="47c56-113">How to add audio feedback?</span></span>
- <span data-ttu-id="47c56-114">如何使用 HoloLens 2 样式按钮预制件？</span><span class="sxs-lookup"><span data-stu-id="47c56-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="47c56-115">如何使对象跟随你？</span><span class="sxs-lookup"><span data-stu-id="47c56-115">How to make an object follow you?</span></span>
- <span data-ttu-id="47c56-116">如何使对象朝向你？</span><span class="sxs-lookup"><span data-stu-id="47c56-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="47c56-117">如何在 Unity 编辑器中模拟输入交互？</span><span class="sxs-lookup"><span data-stu-id="47c56-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="47c56-118">MRTK 支持编辑器中的输入模拟。</span><span class="sxs-lookup"><span data-stu-id="47c56-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="47c56-119">只需单击 Unity 的播放按钮即可运行场景。</span><span class="sxs-lookup"><span data-stu-id="47c56-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="47c56-120">请使用这些键来模拟输入。</span><span class="sxs-lookup"><span data-stu-id="47c56-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="47c56-121">按 W、A、S、D 键可移动相机。</span><span class="sxs-lookup"><span data-stu-id="47c56-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="47c56-122">在按住鼠标右键的同时移动鼠标可以四处浏览。</span><span class="sxs-lookup"><span data-stu-id="47c56-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="47c56-123">若要显示模拟手形图标，请按空格键（右手）或左 Shift 键（左手）。若要在视图中保留模拟手形图标，请按 T 或 Y 键。若要旋转模拟手形图标，请按 Q 或 E（水平旋转）/R 或 F（垂直旋转）</span><span class="sxs-lookup"><span data-stu-id="47c56-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="47c56-124">在 MRTK 文档中详细了解输入模拟</span><span class="sxs-lookup"><span data-stu-id="47c56-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="47c56-125">如何抓取和移动对象？</span><span class="sxs-lookup"><span data-stu-id="47c56-125">How to grab and move an object?</span></span>
<span data-ttu-id="47c56-126">若要使对象可抓取，请分配以下两个脚本：ManipulationHandler.cs 和 NearInteractionGrabbable.cs（根据精确手动跟踪输入直接抓取）。ManipulationHandler 支持近距交互和远距交互。</span><span class="sxs-lookup"><span data-stu-id="47c56-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="47c56-127">可以使用 HoloLens 2 的精确手动跟踪输入（近距）、手部射线（远距）、运动控制器光束（远距）、HoloLens 凝视光标和隔空敲击（远距）来抓取和移动对象。</span><span class="sxs-lookup"><span data-stu-id="47c56-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="47c56-128">如何调整对象的大小？</span><span class="sxs-lookup"><span data-stu-id="47c56-128">How to resize an object?</span></span>
<span data-ttu-id="47c56-129">ManipulationHandler.cs 支持双手缩放/旋转。</span><span class="sxs-lookup"><span data-stu-id="47c56-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="47c56-130">此功能适用于各种输入类型，例如 HoloLens 2 的精确手动输入、HoloLens 1 的凝视 + 手势输入，以及 Windows Mixed Reality 沉浸式头戴显示设备的运动控制器输入。</span><span class="sxs-lookup"><span data-stu-id="47c56-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="47c56-131">在 MRTK 文档中详细了解操作处理程序</span><span class="sxs-lookup"><span data-stu-id="47c56-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="47c56-132">如何精确移动或旋转对象？</span><span class="sxs-lookup"><span data-stu-id="47c56-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="47c56-133">将 BoundingBox.cs 分配到某个对象以使用边界框（用于缩放和旋转对象的界面）。</span><span class="sxs-lookup"><span data-stu-id="47c56-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="47c56-134">默认情况下，该脚本会显示 HoloLens 1 样式的蓝色控点和线条。</span><span class="sxs-lookup"><span data-stu-id="47c56-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="47c56-135">若要使用基于 HoloLens 2 样式邻近性的动画控点，需要分配预制件和材料。</span><span class="sxs-lookup"><span data-stu-id="47c56-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="47c56-136">有关配置详细信息，请参阅[边界框文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)和 BoundingBoxExamples.unity 场景。</span><span class="sxs-lookup"><span data-stu-id="47c56-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="47c56-137">在 MRTK 文档中详细了解边界框</span><span class="sxs-lookup"><span data-stu-id="47c56-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="47c56-138">如何使对象响应输入事件？</span><span class="sxs-lookup"><span data-stu-id="47c56-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="47c56-139">将 PointerHandler.cs 分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="47c56-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="47c56-140">在检查器中，可以使用事件 OnPointerDown()、OnPointerUp()、OnPointerClicked() 和 OnPointerDragged()。若要在脚本中使用这些事件，请实现 IMixedRealityPointerHandler。</span><span class="sxs-lookup"><span data-stu-id="47c56-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="47c56-141">在 MRTK 文档中详细了解输入系统</span><span class="sxs-lookup"><span data-stu-id="47c56-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="47c56-142">如何添加视觉反馈？</span><span class="sxs-lookup"><span data-stu-id="47c56-142">How to add visual feedback?</span></span>
<span data-ttu-id="47c56-143">将 Interactable.cs 分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="47c56-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="47c56-144">在检查器中创建一个新主题。</span><span class="sxs-lookup"><span data-stu-id="47c56-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="47c56-145">使用 Interactable 的主题配置文件可以轻松将视觉反馈添加到所有可用的输入交互状态。</span><span class="sxs-lookup"><span data-stu-id="47c56-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="47c56-146">Interactable 提供各种类型的主题，包括着色器主题，该主题可用于控制每种交互状态的着色器的属性。</span><span class="sxs-lookup"><span data-stu-id="47c56-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="47c56-147">在 MRTK 文档中详细了解 Interactable</span><span class="sxs-lookup"><span data-stu-id="47c56-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="47c56-148">视觉反馈的另一个重要构建基块是 MRTK 标准着色器。</span><span class="sxs-lookup"><span data-stu-id="47c56-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="47c56-149">使用 MRTK 标准着色器可以轻松添加视觉反馈效果，例如悬停光线和邻近光线。</span><span class="sxs-lookup"><span data-stu-id="47c56-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="47c56-150">由于 MRTK 标准着色器占用的计算资源要比 Unity 标准着色器少得多，因此你可以创建高性能的体验。</span><span class="sxs-lookup"><span data-stu-id="47c56-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="47c56-151">创建新材料，然后选择着色器的“混合现实工具包”>“标准”。</span><span class="sxs-lookup"><span data-stu-id="47c56-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="47c56-152">或者，可以选择某个使用 MRTK 标准着色器的现有材料。</span><span class="sxs-lookup"><span data-stu-id="47c56-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="47c56-153">在 MRTK 文档中详细了解 MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="47c56-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="47c56-154">如何添加音频反馈？</span><span class="sxs-lookup"><span data-stu-id="47c56-154">How to add audio feedback?</span></span>
<span data-ttu-id="47c56-155">将 AudioSource 添加到某个对象。</span><span class="sxs-lookup"><span data-stu-id="47c56-155">Add AudioSource to an object.</span></span> <span data-ttu-id="47c56-156">然后，在公开输入事件的脚本（例如 Interactable.cs 或 PointerHandler.cs）中，将该对象分配到该事件，并选择“AudioSource.PlayOneShot()”。</span><span class="sxs-lookup"><span data-stu-id="47c56-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="47c56-157">可以使用自己的音频剪辑，或从 MRTK 的音频资产中进行选择。</span><span class="sxs-lookup"><span data-stu-id="47c56-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="47c56-158">如何使用 HoloLens 2 样式按钮预制件？</span><span class="sxs-lookup"><span data-stu-id="47c56-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="47c56-159">MRTK 提供各种类型的 HoloLens 2 shell (OS) 样式按钮。</span><span class="sxs-lookup"><span data-stu-id="47c56-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="47c56-160">它可以在按钮表面上提供复杂的视觉反馈，例如邻近光线、压缩框和波纹效果。</span><span class="sxs-lookup"><span data-stu-id="47c56-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="47c56-161">只需将某个 HoloLens 2 样式的可按按钮预制件拖放到场景中即可。</span><span class="sxs-lookup"><span data-stu-id="47c56-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="47c56-162">该预制件将使用前面介绍的 Interactable.cs。</span><span class="sxs-lookup"><span data-stu-id="47c56-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="47c56-163">可以使用 Interactable 中公开的事件（例如 OnClick()）来触发操作。</span><span class="sxs-lookup"><span data-stu-id="47c56-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="47c56-164">在 MRTK 文档中详细了解按钮预制件</span><span class="sxs-lookup"><span data-stu-id="47c56-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="47c56-165">如何使对象跟随你？</span><span class="sxs-lookup"><span data-stu-id="47c56-165">How to make an object follow you?</span></span>
<span data-ttu-id="47c56-166">将 RadialView.cs 脚本分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="47c56-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="47c56-167">此脚本是解算器脚本系列的一部分，可用于在 3D 空间中实现各种类型的对象定位。</span><span class="sxs-lookup"><span data-stu-id="47c56-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="47c56-168">将自动添加 SolverHandler.cs。</span><span class="sxs-lookup"><span data-stu-id="47c56-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="47c56-169">下面是 RadialView 配置的一个示例，它可以实现“惰性跟踪”追随行为，就如同使用 HoloLens shell 中的“开始”菜单一样。</span><span class="sxs-lookup"><span data-stu-id="47c56-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="47c56-170">可以指定最小/最大距离和最小/最大视图角度。</span><span class="sxs-lookup"><span data-stu-id="47c56-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="47c56-171">以下示例演示如何在 0.4 到 0.8 米范围内以 15° 的视图角度定位对象。</span><span class="sxs-lookup"><span data-stu-id="47c56-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="47c56-172">调整“线性插值时间”值，以加快或减慢定位更新的速度。</span><span class="sxs-lookup"><span data-stu-id="47c56-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="47c56-173">在 MRTK 文档中详细了解解算器</span><span class="sxs-lookup"><span data-stu-id="47c56-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="47c56-174">如何使对象朝向你？</span><span class="sxs-lookup"><span data-stu-id="47c56-174">How to make an object face you?</span></span>
<span data-ttu-id="47c56-175">将 Billboard.cs 脚本分配到某个对象。</span><span class="sxs-lookup"><span data-stu-id="47c56-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="47c56-176">不管你处于哪个位置，该对象都会朝向你。</span><span class="sxs-lookup"><span data-stu-id="47c56-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="47c56-177">可以指定枢轴选项。</span><span class="sxs-lookup"><span data-stu-id="47c56-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="47c56-178">准备好创建令人惊叹的混合现实体验了吗？</span><span class="sxs-lookup"><span data-stu-id="47c56-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="47c56-179">请访问以下页面来详细了解 MRTK 和混合现实。</span><span class="sxs-lookup"><span data-stu-id="47c56-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="47c56-180">关于作者</span><span class="sxs-lookup"><span data-stu-id="47c56-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="47c56-181"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="47c56-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="47c56-182">用户体验设计师 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="47c56-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="47c56-183">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47c56-183">See also</span></span>

* [<span data-ttu-id="47c56-184">混合现实工具包 - Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="47c56-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="47c56-185">MRTK 文档门户</span><span class="sxs-lookup"><span data-stu-id="47c56-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="47c56-186">MRTK 入门</span><span class="sxs-lookup"><span data-stu-id="47c56-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="47c56-187">HoloToolkit 到 MRTK 的移植指南</span><span class="sxs-lookup"><span data-stu-id="47c56-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
