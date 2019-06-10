---
title: 种交互的对象
description: 一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。 在三维混合的现实世界中，我们无需限制为抽象不再这个世界。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合的现实、 控件、 交互、 ui 和 ux
ms.openlocfilehash: eea7eff6c591a9319b920936ce2be511cecb7496
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813815"
---
# <a name="interactable-object"></a><span data-ttu-id="e0aef-105">种交互的对象</span><span class="sxs-lookup"><span data-stu-id="e0aef-105">Interactable object</span></span>

<span data-ttu-id="e0aef-106">一个按钮很长时间以来触发 2D 抽象环境中的事件使用一种工具。</span><span class="sxs-lookup"><span data-stu-id="e0aef-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="e0aef-107">在三维混合的现实世界中，我们无需限制为抽象不再这个世界。</span><span class="sxs-lookup"><span data-stu-id="e0aef-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="e0aef-108">可以是任何内容**种交互对象**触发事件。</span><span class="sxs-lookup"><span data-stu-id="e0aef-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="e0aef-109">种交互的对象可以表示为任何从上表杯咖啡到气球状飘浮在空中。</span><span class="sxs-lookup"><span data-stu-id="e0aef-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="e0aef-110">我们仍进行传统按钮在某些情况下此类如下所示对话框 UI 的使用。</span><span class="sxs-lookup"><span data-stu-id="e0aef-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="e0aef-111">按钮的可视表示形式取决于上下文。</span><span class="sxs-lookup"><span data-stu-id="e0aef-111">The visual representation of the button depends on the context.</span></span>

![Interactible 对象](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="e0aef-113">种交互的对象的重要属性</span><span class="sxs-lookup"><span data-stu-id="e0aef-113">Important properties of the interactable object</span></span>

### <a name="visual-cue"></a><span data-ttu-id="e0aef-114">视觉提示</span><span class="sxs-lookup"><span data-stu-id="e0aef-114">Visual cue</span></span>

<span data-ttu-id="e0aef-115">视觉提示是通过目测光的窗体中由接收和处理 visual 系统期间视觉感知传感器的提示。</span><span class="sxs-lookup"><span data-stu-id="e0aef-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="e0aef-116">由于 visual 系统是基准中许多种类，尤其是人类视觉提示的大的源代码中如何看待世界的信息。</span><span class="sxs-lookup"><span data-stu-id="e0aef-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="e0aef-117">混合现实中 holographic 对象相混合现实世界环境后，因为它可能会比较困难，了解这种交互的对象。</span><span class="sxs-lookup"><span data-stu-id="e0aef-117">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="e0aef-118">你的体验中的任何种交互对象，务必为每个输入状态提供独特的视觉提示。</span><span class="sxs-lookup"><span data-stu-id="e0aef-118">For any interactable objects in your experience, it is important to provide differentiated visual cue for each input state.</span></span> <span data-ttu-id="e0aef-119">这有助于用户了解您的体验的哪个部分是种交互，并使用户确信使用一致的交互方法。</span><span class="sxs-lookup"><span data-stu-id="e0aef-119">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

#### <a name="far-interactions"></a><span data-ttu-id="e0aef-120">远端交互</span><span class="sxs-lookup"><span data-stu-id="e0aef-120">Far interactions</span></span>

<span data-ttu-id="e0aef-121">任何对象该用户可以进行交互提供注视、 手 ray 与运动控制器的射线，我们建议具有不同的视觉提示，为这三种输入状态：</span><span class="sxs-lookup"><span data-stu-id="e0aef-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>
* <span data-ttu-id="e0aef-122">**默认值 （观察）** :对象的默认空闲状态。</span><span class="sxs-lookup"><span data-stu-id="e0aef-122">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="e0aef-123">**目标 （悬停）** :当对象被指向附带的视线移动游标时，手指邻近或动画控制器的指针。</span><span class="sxs-lookup"><span data-stu-id="e0aef-123">**Targeted (Hover)**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="e0aef-124">**按下**:对象按下时使用-敲击手势、 手指按或运动控制器的选择按钮。</span><span class="sxs-lookup"><span data-stu-id="e0aef-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="e0aef-125">技术，如突出显示或缩放可用于提供给用户的输入状态的视觉提示。</span><span class="sxs-lookup"><span data-stu-id="e0aef-125">You can use techniques such as highlighting or scaling to provide visual cue to the user’s input states.</span></span> <span data-ttu-id="e0aef-126">在 Windows Mixed Reality，可以找到的可视化开始菜单和应用程序栏按钮上的不同输入的状态的示例。</span><span class="sxs-lookup"><span data-stu-id="e0aef-126">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> 

<span data-ttu-id="e0aef-127">![示例可视化观察状态，目标状态，并按下状态](images/640px-interactibleobject-states.png)</span><span class="sxs-lookup"><span data-stu-id="e0aef-127">![Example of visualizing observation state, targeted state, and pressed state](images/640px-interactibleobject-states.png)</span></span><br>
<span data-ttu-id="e0aef-128">*示例可视化观察状态，目标状态，并按下状态*</span><span class="sxs-lookup"><span data-stu-id="e0aef-128">*Example of visualizing observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="e0aef-129">![观察状态，目标状态，和 holographic 按钮按下状态](images/MRTK_InteractableState.png)</span><span class="sxs-lookup"><span data-stu-id="e0aef-129">![Observation state, targeted state, and pressed state on holographic button](images/MRTK_InteractableState.png)</span></span><br>
<span data-ttu-id="e0aef-130">*观察状态，目标状态，和 holographic 按钮按下状态*</span><span class="sxs-lookup"><span data-stu-id="e0aef-130">*Observation state, targeted state, and pressed state on holographic button*</span></span>

#### <a name="neardirect-interactions"></a><span data-ttu-id="e0aef-131">Near(direct) 交互</span><span class="sxs-lookup"><span data-stu-id="e0aef-131">Near(direct) interactions</span></span>

<span data-ttu-id="e0aef-132">HoloLens 2 支持明确的手动跟踪输入可用于与对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="e0aef-132">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="e0aef-133">而无需 haptic 反馈和完美深度感知有时可能难以告诉您的手距离是从对象，或是否会接触。</span><span class="sxs-lookup"><span data-stu-id="e0aef-133">Without haptic feedback and perfect depth perception sometimes it can be hard to tell how far away your hand is from an object, or whether you are touching.</span></span> <span data-ttu-id="e0aef-134">请务必提供足够的视觉提示进行通信的对象，您的掌控之中相对于全息具体的状态。</span><span class="sxs-lookup"><span data-stu-id="e0aef-134">It is important to provide enough visual cues to communicate the state of the object and in particular of your hands in relation to holograms.</span></span>

<span data-ttu-id="e0aef-135">使用可视反馈进行以下通信：</span><span class="sxs-lookup"><span data-stu-id="e0aef-135">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="e0aef-136">**默认值 （观察）** :对象的默认空闲状态。</span><span class="sxs-lookup"><span data-stu-id="e0aef-136">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="e0aef-137">**将鼠标悬停在**:当手动一张全息图，更改视觉对象进行通信的手附近定目标到全息图。</span><span class="sxs-lookup"><span data-stu-id="e0aef-137">**Hover**: When hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="e0aef-138">**距离和交互点**: 随着手接近全息图，设计进行通信的预计的点的交互，以及如何当对象远上方的手指的反馈</span><span class="sxs-lookup"><span data-stu-id="e0aef-138">**Distance and point of interaction**: As hand approaches hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="e0aef-139">**请联系 Begin**:更改视觉对象 （光，颜色） 进行通信的触摸屏输入已发生</span><span class="sxs-lookup"><span data-stu-id="e0aef-139">**Contact Begin**: Change visuals (light, color) to communicate that touch has occured</span></span>
* <span data-ttu-id="e0aef-140">**由于**:更改视觉对象 （light、 颜色） 时获取对象。</span><span class="sxs-lookup"><span data-stu-id="e0aef-140">**Grasped**: Change visuals (light, color) when the object is grasped.</span></span>
* <span data-ttu-id="e0aef-141">**请联系最终**:更改视觉对象 （light、 颜色） 时触摸屏输入已结束。</span><span class="sxs-lookup"><span data-stu-id="e0aef-141">**Contact End**: Change visuals (light, color) when touch has ended.</span></span>

<span data-ttu-id="e0aef-142">![示例中的可视化附近交互状态](images/640px-interactibleobject-states-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0aef-142">![Example of visualizing near interaction states](images/640px-interactibleobject-states-near.jpg)</span></span><br>
<span data-ttu-id="e0aef-143">*示例中的可视化附近交互状态*</span><span class="sxs-lookup"><span data-stu-id="e0aef-143">*Example of visualizing near interaction states*</span></span>

<span data-ttu-id="e0aef-144">[HoloLens 2 中的按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)显示可视化不同输入的交互状态的示例。</span><span class="sxs-lookup"><span data-stu-id="e0aef-144">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows the example of visualizing different input interaction states.</span></span>

<span data-ttu-id="e0aef-145">![Pressable 按钮 HoloLens 2 中的示例](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0aef-145">![Example of pressable button in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span></span><br>
<span data-ttu-id="e0aef-146">*Pressable 按钮 HoloLens 2 中的示例*</span><span class="sxs-lookup"><span data-stu-id="e0aef-146">*Example of pressable button in HoloLens 2*</span></span>

<span data-ttu-id="e0aef-147">在 HoloLens 2 中，没有其他的可视化提示可提高用户的置信度在深度感知。</span><span class="sxs-lookup"><span data-stu-id="e0aef-147">In HoloLens 2, there is an additional visual cue which improves the user's confidence on the depth perception.</span></span> <span data-ttu-id="e0aef-148">在指尖环会出现，如指尖更接近于该对象向下缩放。</span><span class="sxs-lookup"><span data-stu-id="e0aef-148">The ring on the fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="e0aef-149">环最终汇聚到一个点上按下状态。</span><span class="sxs-lookup"><span data-stu-id="e0aef-149">The ring eventually converges into a dot on press state.</span></span> <span data-ttu-id="e0aef-150">此 visual 功能可见性： 可帮助用户了解对象的距离。</span><span class="sxs-lookup"><span data-stu-id="e0aef-150">This visual affordance helps the user understand the distance from the object.</span></span>

<span data-ttu-id="e0aef-151">![指尖环可视化效果](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0aef-151">![Fingertip ring visualization](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span></span><br>
<span data-ttu-id="e0aef-152">*指尖环 HoloLens 2 中的可视化效果*</span><span class="sxs-lookup"><span data-stu-id="e0aef-152">*Fingertip ring visualization in HoloLens 2*</span></span>

<span data-ttu-id="e0aef-153">![在手动邻近的可视反馈](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="e0aef-153">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="e0aef-154">*可视反馈的邻近的边界框示例*</span><span class="sxs-lookup"><span data-stu-id="e0aef-154">*Example of visual feedback based on the proximity - Bounding Box*</span></span>


### <a name="audio-cue"></a><span data-ttu-id="e0aef-155">则音频提示</span><span class="sxs-lookup"><span data-stu-id="e0aef-155">Audio cue</span></span>
<span data-ttu-id="e0aef-156">直接手动交互，正确的音频反馈可以极大地改善用户体验。</span><span class="sxs-lookup"><span data-stu-id="e0aef-156">For the direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="e0aef-157">音频反馈用于以下通信：</span><span class="sxs-lookup"><span data-stu-id="e0aef-157">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="e0aef-158">**请联系开始**:开始触摸时播放声音</span><span class="sxs-lookup"><span data-stu-id="e0aef-158">**Contact begin**: Play sound when touch begins</span></span>
* <span data-ttu-id="e0aef-159">**联系人结束**:触摸屏输入端上播放声音</span><span class="sxs-lookup"><span data-stu-id="e0aef-159">**Contact end**: Play sound on touch end</span></span>
* <span data-ttu-id="e0aef-160">**随取即行开始**:随取即行启动时播放声音</span><span class="sxs-lookup"><span data-stu-id="e0aef-160">**Grab begin**: Play sound when grab starts</span></span>
* <span data-ttu-id="e0aef-161">**获取结束**:随取即行结束上播放声音</span><span class="sxs-lookup"><span data-stu-id="e0aef-161">**Grab end**: Play sound on grab end</span></span>

### <a name="voice-command"></a><span data-ttu-id="e0aef-162">语音命令</span><span class="sxs-lookup"><span data-stu-id="e0aef-162">Voice command</span></span>
<span data-ttu-id="e0aef-163">对于任何种交互的对象，务必以支持其他交互选项。</span><span class="sxs-lookup"><span data-stu-id="e0aef-163">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="e0aef-164">默认情况下，建议对于的任何对象都是种交互支持语音命令。</span><span class="sxs-lookup"><span data-stu-id="e0aef-164">In default, it is recommended to support voice command for any objects that are interactable.</span></span> <span data-ttu-id="e0aef-165">若要提高可发现性，你可以提供工具提示处于悬停状态。</span><span class="sxs-lookup"><span data-stu-id="e0aef-165">To improve the discoverability, you can provide tooltip on hover state.</span></span>

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="语音命令的工具提示" width="350"><br/><span data-ttu-id="e0aef-167">*语音命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="e0aef-167">*Tooltip for the voice command*</span></span>

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="e0aef-168">创建混合现实工具包 (MRTK) 的种交互的对象</span><span class="sxs-lookup"><span data-stu-id="e0aef-168">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="e0aef-169">在中 **[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)** ，可以找到的 Unity 脚本一系列和预设将帮助你创建种交互的对象。</span><span class="sxs-lookup"><span data-stu-id="e0aef-169">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="e0aef-170">您可以使用这些响应输入的交互状态的各种类型的对象。</span><span class="sxs-lookup"><span data-stu-id="e0aef-170">You can use these to make objects respond to various types of input interaction states.</span></span>

* <span data-ttu-id="e0aef-171">**[Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)**</span><span class="sxs-lookup"><span data-stu-id="e0aef-171">**[Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)**</span></span>
* <span data-ttu-id="e0aef-172">**[按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)**</span><span class="sxs-lookup"><span data-stu-id="e0aef-172">**[Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)**</span></span>
* <span data-ttu-id="e0aef-173">**[手动交互示例场景](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)**</span><span class="sxs-lookup"><span data-stu-id="e0aef-173">**[Hand Interaction Examples Scene](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)**</span></span>

<span data-ttu-id="e0aef-174">MixedRealityToolkit 的标准着色器提供了各种选项，例如**邻近 light** ，可帮助您创建视觉和声音提示。</span><span class="sxs-lookup"><span data-stu-id="e0aef-174">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* <span data-ttu-id="e0aef-175">**[MRTK 标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)**</span><span class="sxs-lookup"><span data-stu-id="e0aef-175">**[MRTK Standard Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)**</span></span>


## <a name="see-also"></a><span data-ttu-id="e0aef-176">请参阅</span><span class="sxs-lookup"><span data-stu-id="e0aef-176">See also</span></span>

* <span data-ttu-id="e0aef-177">**[边界框](app-bar-and-bounding-box.md)**</span><span class="sxs-lookup"><span data-stu-id="e0aef-177">**[Bounding Box](app-bar-and-bounding-box.md)**</span></span>
* <span data-ttu-id="e0aef-178">**[对象集合](object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="e0aef-178">**[Object collection](object-collection.md)**</span></span>
* <span data-ttu-id="e0aef-179">**[公告板和尾随](billboarding-and-tag-along.md)**</span><span class="sxs-lookup"><span data-stu-id="e0aef-179">**[Billboarding and tag-along](billboarding-and-tag-along.md)**</span></span>
