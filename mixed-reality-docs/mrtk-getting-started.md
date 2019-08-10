---
title: MRTK 版本2入门
description: 对于对利用 MRTK 感兴趣的新开发人员
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, 测试, 混合现实工具包, MRTK 版本 2, MRTK, 工具, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: c785498e1533b2117249d3b21952ff56190126c0
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937089"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="abc21-104">MRTK v2 入门</span><span class="sxs-lookup"><span data-stu-id="abc21-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="abc21-105">MRTK 入门指南</span><span class="sxs-lookup"><span data-stu-id="abc21-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="abc21-106">有关 MRTK V2 入门的信息, 请参阅[MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)。</span><span class="sxs-lookup"><span data-stu-id="abc21-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="abc21-107">什么是混合现实工具包 (MRTK)？</span><span class="sxs-lookup"><span data-stu-id="abc21-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="abc21-108">MRTK 是一种令人惊叹的开源工具包, 它是自2015首次发布后开始的, 并不是我们的开发人员社区的硬性工作, 而是目前为止。</span><span class="sxs-lookup"><span data-stu-id="abc21-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="abc21-109">过去3年来, 我们已听取开发人员社区的反馈, 并构建了 MRTK v2, 以考虑最大的问题。</span><span class="sxs-lookup"><span data-stu-id="abc21-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="abc21-110">使用 Unity 的 MRTK v2 是适用于混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="abc21-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="abc21-111">MRTK 版本2旨在加速开发面向 Microsoft HoloLens、Windows Mixed Reality 沉浸 (VR) 耳机和 OpenVR 平台的应用程序。</span><span class="sxs-lookup"><span data-stu-id="abc21-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="abc21-112">该项目旨在降低创建混合现实应用程序的门槛，并在我们共同成长的过程中回馈社区。</span><span class="sxs-lookup"><span data-stu-id="abc21-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="abc21-113">有关详细信息, 请参阅[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。</span><span class="sxs-lookup"><span data-stu-id="abc21-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="abc21-114">功能区域</span><span class="sxs-lookup"><span data-stu-id="abc21-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="输入系统" width="105"> <span data-ttu-id="abc21-116">输入系统</span><span class="sxs-lookup"><span data-stu-id="abc21-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="手动跟踪 (HoloLens 2)" width="105"> <span data-ttu-id="abc21-118">手动跟踪 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="abc21-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="目视跟踪 (HoloLens 2)" width="105">
    <span data-ttu-id="abc21-120">目视跟踪 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="abc21-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="语音命令" width="105"> <span data-ttu-id="abc21-122">语音命令</span><span class="sxs-lookup"><span data-stu-id="abc21-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="注视 + Select (HoloLens (第一代))" width="105">
    <span data-ttu-id="abc21-124">注视 + Select (HoloLens (第一代))</span><span class="sxs-lookup"><span data-stu-id="abc21-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> <span data-ttu-id="abc21-126">Teleportation</span><span class="sxs-lookup"><span data-stu-id="abc21-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI 控件" width="105"> <span data-ttu-id="abc21-128">UI 控件</span><span class="sxs-lookup"><span data-stu-id="abc21-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="规划求解和交互" width="105"> <span data-ttu-id="abc21-130">规划求解和交互</span><span class="sxs-lookup"><span data-stu-id="abc21-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="控制器可视化" width="105"> <span data-ttu-id="abc21-132">控制器可视化</span><span class="sxs-lookup"><span data-stu-id="abc21-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="空间理解" width="105"> <span data-ttu-id="abc21-134">空间理解</span><span class="sxs-lookup"><span data-stu-id="abc21-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="诊断工具" width="105"> <span data-ttu-id="abc21-136">诊断工具</span><span class="sxs-lookup"><span data-stu-id="abc21-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 标准着色器" width="105"> <span data-ttu-id="abc21-138">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="abc21-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="abc21-139">UI 和交互构建基块</span><span class="sxs-lookup"><span data-stu-id="abc21-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Button" width="250"><br>
    <span data-ttu-id="abc21-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="abc21-141">**Button**</span></span><br>
    <span data-ttu-id="abc21-142">支持各种输入法 (包括 HoloLens 2 的有向右说明) 的 button 控件<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="边界框" width="250"><br>
    <span data-ttu-id="abc21-144">**边界框**</span><span class="sxs-lookup"><span data-stu-id="abc21-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="abc21-145">用于在三维空间中操作对象的标准 UI<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作处理程序" width="250"><br>
    <span data-ttu-id="abc21-147">**操作处理程序**</span><span class="sxs-lookup"><span data-stu-id="abc21-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="abc21-148">用一或两次手操作对象的脚本<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="盖板" width="250"><br>
    <span data-ttu-id="abc21-150">**盖板**</span><span class="sxs-lookup"><span data-stu-id="abc21-150">**Slate**</span></span> <br>
    <span data-ttu-id="abc21-151">支持用有向右输入滚动的2D 样式平面<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="系统键盘" width="250"><br>
    <span data-ttu-id="abc21-153">**系统键盘**</span><span class="sxs-lookup"><span data-stu-id="abc21-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="abc21-154">在 Unity 中使用系统键盘的示例脚本<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="种不可交互" width="250"><br>
     <span data-ttu-id="abc21-156">**种不可交互**</span><span class="sxs-lookup"><span data-stu-id="abc21-156">**Interactable**</span></span> <br>
     <span data-ttu-id="abc21-157">用于使对象种不可交互可视状态和主题支持的脚本<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="求" width="250"><br>
    <span data-ttu-id="abc21-159">**求**</span><span class="sxs-lookup"><span data-stu-id="abc21-159">**Solver**</span></span> <br>
    <span data-ttu-id="abc21-160">各种对象定位行为, 如标记、正文锁定、常量视图大小和表面磁性<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="对象集合" width="250"><br>
    <span data-ttu-id="abc21-162">**对象集合**</span><span class="sxs-lookup"><span data-stu-id="abc21-162">**Object Collection**</span></span><br>
    <span data-ttu-id="abc21-163">用于在三维形状中布局对象数组的脚本<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="工具提示" width="250">  <br>
    <span data-ttu-id="abc21-165">**提示**</span><span class="sxs-lookup"><span data-stu-id="abc21-165">**Tooltip**</span></span><br>
    <span data-ttu-id="abc21-166">具有灵活的定位点/透视系统的批注 UI, 可用于标记运动控制器和对象<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="应用栏" width="250"><br>
    <span data-ttu-id="abc21-168">**应用栏**</span><span class="sxs-lookup"><span data-stu-id="abc21-168">**App Bar**</span></span><br>
    <span data-ttu-id="abc21-169">边界框手动激活的 UI<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="指针" width="250"><br>
    <span data-ttu-id="abc21-171">**指针**</span><span class="sxs-lookup"><span data-stu-id="abc21-171">**Pointers**</span></span><br>
    <span data-ttu-id="abc21-172">了解各种类型的指针<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="手指可视化" width="250"><br>
     <span data-ttu-id="abc21-174">**手指可视化**</span><span class="sxs-lookup"><span data-stu-id="abc21-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="abc21-175">手指上的视觉对象 affordance, 可改善直接交互的置信度<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="abc21-177">**滑块**</span><span class="sxs-lookup"><span data-stu-id="abc21-177">**Slider**</span></span><br>
    <span data-ttu-id="abc21-178">用于调整支持直接跟踪交互的值的滑块 UI<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 标准着色器" width="250"><br>
    <span data-ttu-id="abc21-180">**MRTK 标准着色器**</span><span class="sxs-lookup"><span data-stu-id="abc21-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="abc21-181">MRTK 的标准着色器支持各种流畅的设计元素和性能<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手型接点 Chaser" width="250"><br>
     <span data-ttu-id="abc21-183">**手型接点 Chaser**</span><span class="sxs-lookup"><span data-stu-id="abc21-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="abc21-184">演示如何使用规划求解将对象附加到手中<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="目视跟踪:目标选择" width="250"><br>
    <span data-ttu-id="abc21-186">**目视跟踪:目标选择**</span><span class="sxs-lookup"><span data-stu-id="abc21-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="abc21-187">将眼睛、语音和手写输入与您的场景一起快速轻松地选择全息影像<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="目视跟踪:导航" width="250"><br>
    <span data-ttu-id="abc21-189">**目视跟踪:导航**</span><span class="sxs-lookup"><span data-stu-id="abc21-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="abc21-190">了解如何根据要查看的内容自动滚动文本或流畅地缩放到聚焦内容<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="目视跟踪:热度地图" width="250"><br>
    <span data-ttu-id="abc21-192">**目视跟踪:热度地图**</span><span class="sxs-lookup"><span data-stu-id="abc21-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="abc21-193">记录、加载和可视化用户在应用中查看的内容的示例<a/></span><span class="sxs-lookup"><span data-stu-id="abc21-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="abc21-194">MRTK v2 的最低要求</span><span class="sxs-lookup"><span data-stu-id="abc21-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="abc21-195">Unity 2018。4</span><span class="sxs-lookup"><span data-stu-id="abc21-195">Unity 2018.4.x</span></span>
* <span data-ttu-id="abc21-196">Microsoft Visual Studio 2017 或更高版本</span><span class="sxs-lookup"><span data-stu-id="abc21-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="abc21-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="abc21-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="abc21-198">Windows 10 1803 或更高版本</span><span class="sxs-lookup"><span data-stu-id="abc21-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="abc21-199">新的 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="abc21-199">New with MRTK v2</span></span>
<span data-ttu-id="abc21-200">我们想要对这些平台工具的承诺施加压力。</span><span class="sxs-lookup"><span data-stu-id="abc21-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="abc21-201">事实上, 我们利用 MRTK 版本2来开发收件箱体验, 例如安装体验 (OOBE) 和混合现实学习应用程序。</span><span class="sxs-lookup"><span data-stu-id="abc21-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="abc21-202">你还可以看到新的 HoloLens 2 功能首次通过 MRTK 公开, 因为我们认为这是在我们的平台上进行开发的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="abc21-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="abc21-203">模块化</span><span class="sxs-lookup"><span data-stu-id="abc21-203">Modular</span></span>
<span data-ttu-id="abc21-204">我们采用模块化方式构建了它, 因此您无需将该工具包的每个套件都引入到您的项目中。</span><span class="sxs-lookup"><span data-stu-id="abc21-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="abc21-205">这样做实际上只有几个优点。</span><span class="sxs-lookup"><span data-stu-id="abc21-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="abc21-206">它可以使项目大小保持较小, 并使其更易于管理。</span><span class="sxs-lookup"><span data-stu-id="abc21-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="abc21-207">基于这一点, 因为它是用可编写脚本的对象构建的, 并且是接口驱动的, 所以还可以替换您自己的组件, 以支持其他服务、系统和平台。</span><span class="sxs-lookup"><span data-stu-id="abc21-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="abc21-208">跨平台</span><span class="sxs-lookup"><span data-stu-id="abc21-208">Cross-platform</span></span>
<span data-ttu-id="abc21-209">说到其他平台, 它具有跨平台支持。</span><span class="sxs-lookup"><span data-stu-id="abc21-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="abc21-210">虽然这并不意味着每个平台都受支持, 但我们确保在将生成目标切换到其他平台时, 不会中断任何工具包代码。</span><span class="sxs-lookup"><span data-stu-id="abc21-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="abc21-211">模块化设计的可靠性和扩展性使你能够支持多个平台, 如 ARCore、ARKit 和 OpenVR。</span><span class="sxs-lookup"><span data-stu-id="abc21-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="abc21-212">高性能</span><span class="sxs-lookup"><span data-stu-id="abc21-212">Performant</span></span>
<span data-ttu-id="abc21-213">使用移动平台时, 我们构建了性能方面的考虑因素。</span><span class="sxs-lookup"><span data-stu-id="abc21-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="abc21-214">这非常重要, 我们想要确保这些工具不会与你一起工作。</span><span class="sxs-lookup"><span data-stu-id="abc21-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="abc21-215">请参阅</span><span class="sxs-lookup"><span data-stu-id="abc21-215">See also</span></span>
* [<span data-ttu-id="abc21-216">MRTK 入门指南</span><span class="sxs-lookup"><span data-stu-id="abc21-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="abc21-217">MRTK 文档主页</span><span class="sxs-lookup"><span data-stu-id="abc21-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="abc21-218">安装工具</span><span class="sxs-lookup"><span data-stu-id="abc21-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="abc21-219">从 HTK/MRTK 迁移到 MRTK 版本2</span><span class="sxs-lookup"><span data-stu-id="abc21-219">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
