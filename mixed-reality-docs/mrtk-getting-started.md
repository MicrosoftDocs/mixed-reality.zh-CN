---
title: 开始使用 MRTK 版本 2
description: 新开发人员感兴趣利用 MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality 测试，混合现实工具包、 MRTK 版本 2、 MRTK、 工具、 SDK、 HoloLens、 HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750363"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="4e235-104">开始使用 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="4e235-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="4e235-105">MRTK 入门指南</span><span class="sxs-lookup"><span data-stu-id="4e235-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="4e235-106">请参阅[MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)有关如何开始使用 MRTK V2 的信息。</span><span class="sxs-lookup"><span data-stu-id="4e235-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="4e235-107">什么是混合现实工具包 (MRTK)？</span><span class="sxs-lookup"><span data-stu-id="4e235-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="4e235-108">MRTK 是令人惊叹的开放源代码工具包，以来已经过围绕 HoloLens 首次发布，并且不会目前的状况而无需我们的开发人员社区向其提供了大量工作。</span><span class="sxs-lookup"><span data-stu-id="4e235-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="4e235-109">在过去 3 年中，我们有侦听到我们的开发人员社区的反馈，并生成 MRTK v2 要着重考虑的最大的问题。</span><span class="sxs-lookup"><span data-stu-id="4e235-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="4e235-110">使用 Unity MRTK v2 是混合的现实应用程序的一个开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="4e235-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="4e235-111">MRTK 版本 2 旨在加速开发针对 Microsoft HoloLens，Windows Mixed Reality 沉浸式 (VR) 耳机，以及 OpenVR 平台的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4e235-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="4e235-112">项目功能旨在减少到条目创建混合的现实应用程序并提供回社区，随着我们所有的发展的障碍。</span><span class="sxs-lookup"><span data-stu-id="4e235-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="4e235-113">请参阅[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)若要了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="4e235-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="4e235-114">功能区</span><span class="sxs-lookup"><span data-stu-id="4e235-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="在输入的系统" width="105"> <span data-ttu-id="4e235-116">在输入的系统</span><span class="sxs-lookup"><span data-stu-id="4e235-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="手动跟踪 (HoloLens 2)" width="105"> <span data-ttu-id="4e235-118">手动跟踪 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="4e235-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="眼睛追踪 (HoloLens 2)" width="105">
    <span data-ttu-id="4e235-120">眼睛追踪 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="4e235-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="语音命令" width="105"> <span data-ttu-id="4e235-122">语音命令</span><span class="sxs-lookup"><span data-stu-id="4e235-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="注视 + 选择 (HoloLens （第 1 代）)" width="105">
    <span data-ttu-id="4e235-124">注视 + 选择 (HoloLens （第 1 代）)</span><span class="sxs-lookup"><span data-stu-id="4e235-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> <span data-ttu-id="4e235-126">Teleportation</span><span class="sxs-lookup"><span data-stu-id="4e235-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI 控件" width="105"> <span data-ttu-id="4e235-128">UI 控件</span><span class="sxs-lookup"><span data-stu-id="4e235-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="解算器和交互" width="105"> <span data-ttu-id="4e235-130">解算器和交互</span><span class="sxs-lookup"><span data-stu-id="4e235-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="控制器可视化效果" width="105"> <span data-ttu-id="4e235-132">控制器可视化效果</span><span class="sxs-lookup"><span data-stu-id="4e235-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="空间了解" width="105"> <span data-ttu-id="4e235-134">空间了解</span><span class="sxs-lookup"><span data-stu-id="4e235-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="诊断工具" width="105"> <span data-ttu-id="4e235-136">诊断工具</span><span class="sxs-lookup"><span data-stu-id="4e235-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 标准着色器" width="105"> <span data-ttu-id="4e235-138">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="4e235-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="4e235-139">UI 和交互构建基块</span><span class="sxs-lookup"><span data-stu-id="4e235-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Button" width="250"><br>
    <span data-ttu-id="4e235-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="4e235-141">**Button**</span></span><br>
    <span data-ttu-id="4e235-142">一个按钮控件，它支持各种输入的方法包括 HoloLens 2 明确的手 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="边界框" width="250"><br>
    <span data-ttu-id="4e235-144">**边界框**</span><span class="sxs-lookup"><span data-stu-id="4e235-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="4e235-145">用于处理 3D 空间中的对象的标准用户界面 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="操作处理程序" width="250"><br>
    <span data-ttu-id="4e235-147">**操作处理程序**</span><span class="sxs-lookup"><span data-stu-id="4e235-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="4e235-148">用于操作具有一个或两个指针的对象的脚本 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="静态图像" width="250"><br>
    <span data-ttu-id="4e235-150">**静态图像**</span><span class="sxs-lookup"><span data-stu-id="4e235-150">**Slate**</span></span> <br>
    <span data-ttu-id="4e235-151">2D 样式平面支持滚动明确的手动输入 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="系统键盘" width="250"><br>
    <span data-ttu-id="4e235-153">**系统键盘**</span><span class="sxs-lookup"><span data-stu-id="4e235-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="4e235-154">在 Unity 中使用系统键盘的示例脚本 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="种交互" width="250"><br>
     <span data-ttu-id="4e235-156">**Interactable**</span><span class="sxs-lookup"><span data-stu-id="4e235-156">**Interactable**</span></span> <br>
     <span data-ttu-id="4e235-157">用于使对象的可视状态和主题支持使用种交互的脚本 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="解算器" width="250"><br>
    <span data-ttu-id="4e235-159">**Solver**</span><span class="sxs-lookup"><span data-stu-id="4e235-159">**Solver**</span></span> <br>
    <span data-ttu-id="4e235-160">各种对象定位行为，例如尾随、 正文锁、 常量视图大小和图面消除 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="对象集合" width="250"><br>
    <span data-ttu-id="4e235-162">**对象集合**</span><span class="sxs-lookup"><span data-stu-id="4e235-162">**Object Collection**</span></span><br>
    <span data-ttu-id="4e235-163">在三维形状中的对象的数组布局的脚本 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="工具提示" width="250">  <br>
    <span data-ttu-id="4e235-165">**Tooltip**</span><span class="sxs-lookup"><span data-stu-id="4e235-165">**Tooltip**</span></span><br>
    <span data-ttu-id="4e235-166">批注 UI 与灵活的定位点/枢轴系统可用于标记运动控制器和对象 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="应用栏" width="250"><br>
    <span data-ttu-id="4e235-168">**App Bar**</span><span class="sxs-lookup"><span data-stu-id="4e235-168">**App Bar**</span></span><br>
    <span data-ttu-id="4e235-169">边界框手动激活的用户界面 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="指针" width="250"><br>
    <span data-ttu-id="4e235-171">**指针**</span><span class="sxs-lookup"><span data-stu-id="4e235-171">**Pointers**</span></span><br>
    <span data-ttu-id="4e235-172">了解有关各种类型的指针 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="指尖可视化效果" width="250"><br>
     <span data-ttu-id="4e235-174">**指尖可视化效果**</span><span class="sxs-lookup"><span data-stu-id="4e235-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="4e235-175">这将提高直接交互的置信度指尖上可视化功能的可见性： <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="4e235-177">**滑块**</span><span class="sxs-lookup"><span data-stu-id="4e235-177">**Slider**</span></span><br>
    <span data-ttu-id="4e235-178">用于调整滑块 UI 值支持直接手动跟踪交互 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 标准着色器" width="250"><br>
    <span data-ttu-id="4e235-180">**MRTK 标准着色器**</span><span class="sxs-lookup"><span data-stu-id="4e235-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="4e235-181">MRTK 的标准着色器支持与性能的各种 Fluent 设计元素 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="手联合 Chaser" width="250"><br>
     <span data-ttu-id="4e235-183">**手联合 Chaser**</span><span class="sxs-lookup"><span data-stu-id="4e235-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="4e235-184">演示如何使用解算器将对象附加到的现有连接 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="眼睛追踪：选择目标" width="250"><br>
    <span data-ttu-id="4e235-186">**眼睛追踪：选择目标**</span><span class="sxs-lookup"><span data-stu-id="4e235-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="4e235-187">结合使用眼睛、 语音和手动输入快速高效地在您的场景之间选择全息 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="眼睛追踪：导航" width="250"><br>
    <span data-ttu-id="4e235-189">**眼睛追踪：导航**</span><span class="sxs-lookup"><span data-stu-id="4e235-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="4e235-190">了解如何自动滚动文本或流畅缩放到根据你正在查看的内容的已设定焦点内容 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="眼睛追踪：热度地图" width="250"><br>
    <span data-ttu-id="4e235-192">**眼睛追踪：热度地图**</span><span class="sxs-lookup"><span data-stu-id="4e235-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="4e235-193">有关日志记录的示例，加载和可视化的哪些用户已经了解了应用程序中 <a/></span><span class="sxs-lookup"><span data-stu-id="4e235-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="4e235-194">对于 MRTK v2 的最低要求</span><span class="sxs-lookup"><span data-stu-id="4e235-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="4e235-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="4e235-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="4e235-196">Microsoft Visual Studio 2017 或更高版本</span><span class="sxs-lookup"><span data-stu-id="4e235-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="4e235-197">Windows SDK 18362+</span><span class="sxs-lookup"><span data-stu-id="4e235-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="4e235-198">Windows 10 1803年或更高版本</span><span class="sxs-lookup"><span data-stu-id="4e235-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="4e235-199">新功能 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="4e235-199">New with MRTK v2</span></span>
<span data-ttu-id="4e235-200">我们想要强调我们对这些平台工具的承诺。</span><span class="sxs-lookup"><span data-stu-id="4e235-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="4e235-201">事实上，我们就利用了 MRTK 版本 2 开发我们收件箱的体验，例如安装体验 (OOBE) 和混合现实学习应用程序。</span><span class="sxs-lookup"><span data-stu-id="4e235-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="4e235-202">则可能要查看新 HoloLens 2 功能通过 MRTK 首次公开，因为我们认为它是在我们的平台上进行开发的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="4e235-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="4e235-203">采用模块化结构</span><span class="sxs-lookup"><span data-stu-id="4e235-203">Modular</span></span>
<span data-ttu-id="4e235-204">以便不需要考虑该工具包的每一位到你的项目，我们有模块化方式，构建它。</span><span class="sxs-lookup"><span data-stu-id="4e235-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="4e235-205">有此实际几个优点。</span><span class="sxs-lookup"><span data-stu-id="4e235-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="4e235-206">它使您的项目规模较小，以及轻松地管理。</span><span class="sxs-lookup"><span data-stu-id="4e235-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="4e235-207">除此之外，因为它用可编写脚本的对象生成，并且驱动的界面，它还有可能更换附带你自己，以支持其他服务、 系统和平台的组件。</span><span class="sxs-lookup"><span data-stu-id="4e235-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="4e235-208">跨平台</span><span class="sxs-lookup"><span data-stu-id="4e235-208">Cross-platform</span></span>
<span data-ttu-id="4e235-209">说到其他平台，它提供了跨平台支持。</span><span class="sxs-lookup"><span data-stu-id="4e235-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="4e235-210">而这并不意味着每个单个平台支持的功能，我们已确保的工具包代码都不会中断生成目标切换到其他平台时。</span><span class="sxs-lookup"><span data-stu-id="4e235-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="4e235-211">可靠性和可扩展性的模块化设计设置您上能够支持多个平台，例如 ARCore、 ARKit，以及 OpenVR 的好方法。</span><span class="sxs-lookup"><span data-stu-id="4e235-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="4e235-212">高性能</span><span class="sxs-lookup"><span data-stu-id="4e235-212">Performant</span></span>
<span data-ttu-id="4e235-213">我们在使用的移动平台，构造它与性能方面的考虑。</span><span class="sxs-lookup"><span data-stu-id="4e235-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="4e235-214">这是非常重要，我们想要确保这些工具不会对您工作。</span><span class="sxs-lookup"><span data-stu-id="4e235-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="4e235-215">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e235-215">See also</span></span>
* [<span data-ttu-id="4e235-216">MRTK 入门指南</span><span class="sxs-lookup"><span data-stu-id="4e235-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="4e235-217">MRTK 文档主页</span><span class="sxs-lookup"><span data-stu-id="4e235-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="4e235-218">安装工具</span><span class="sxs-lookup"><span data-stu-id="4e235-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="4e235-219">从 HTK/MRTK 移植到 MRTK 版本 2</span><span class="sxs-lookup"><span data-stu-id="4e235-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
