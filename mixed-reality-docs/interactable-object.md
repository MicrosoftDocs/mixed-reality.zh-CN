---
title: 可交互对象
description: 按钮是一个隐喻，长久以来用于触发二维抽象世界中的某个事件。 而在三维混合现实世界中, 我们无需局限在这种抽象世界中。
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 混合现实、控件、交互、ui、ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415288"
---
# <a name="interactable-object"></a><span data-ttu-id="b8c2d-105">可交互对象</span><span class="sxs-lookup"><span data-stu-id="b8c2d-105">Interactable object</span></span>

<span data-ttu-id="b8c2d-106">按钮是一个隐喻，长久以来用于触发二维抽象世界中的某个事件。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="b8c2d-107">而在三维混合现实世界中, 我们无需局限在这种抽象世界中。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="b8c2d-108">任何内容都可以是触发事件的**可交互对象**。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="b8c2d-109">从桌子上的咖啡杯到悬浮在空中的气球，可交互对象可表示为任何内容。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="b8c2d-110">在某些情况下 (例如, 在对话框 UI 中)，我们仍会使用传统的按钮。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="b8c2d-111">按钮的可视化表示形式取决于上下文。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-111">The visual representation of the button depends on the context.</span></span>

![Interactible 对象](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="b8c2d-113">可交互对象的重要属性</span><span class="sxs-lookup"><span data-stu-id="b8c2d-113">Important properties of the interactable object</span></span>

### <a name="visual-cue"></a><span data-ttu-id="b8c2d-114">视觉提示</span><span class="sxs-lookup"><span data-stu-id="b8c2d-114">Visual cue</span></span>

<span data-ttu-id="b8c2d-115">视觉提示是视觉对象的视觉对象系统中的眼睛传感器提示, 由视觉对象系统处理。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="b8c2d-116">由于视觉对象系统在很多物种中是主导的, 尤其是在人们看来, 直观提示是了解世界上的信息。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="b8c2d-117">在混合现实中, 由于全息对象与真实环境混合, 因此很难了解哪些对象是可交互的。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-117">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="b8c2d-118">对于所提供的体验中的任何可交互对象，为每种输入状态提供不同的视觉提示非常重要。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-118">For any interactable objects in your experience, it is important to provide differentiated visual cue for each input state.</span></span> <span data-ttu-id="b8c2d-119">这可以帮助用户了解所提供的体验的哪个部分是可交互的，并使用户能够借助一致的交互方法自信得获得体验。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-119">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

#### <a name="far-interactions"></a><span data-ttu-id="b8c2d-120">远距离交互</span><span class="sxs-lookup"><span data-stu-id="b8c2d-120">Far interactions</span></span>

<span data-ttu-id="b8c2d-121">对于用户可与 "注视"、"手形" 和 "运动控制器" 射线交互的任何对象, 我们建议对这三个输入状态使用不同的视觉提示:</span><span class="sxs-lookup"><span data-stu-id="b8c2d-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>
* <span data-ttu-id="b8c2d-122">**默认值 (观察)** :对象的默认空闲状态。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-122">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="b8c2d-123">**目标 (悬停)** :当对象面向注视光标时, 指的是指邻近的或运动控制器的指针。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-123">**Targeted (Hover)**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="b8c2d-124">**按下**:按下了 "按压" 手势时, 按下或运动控制器的选择按钮。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="b8c2d-125">您可以使用诸如突出显示或缩放等方法为用户输入状态提供视觉提示。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-125">You can use techniques such as highlighting or scaling to provide visual cue to the user’s input states.</span></span> <span data-ttu-id="b8c2d-126">在 Windows Mixed Reality 中, 可以在 "开始" 菜单和应用栏按钮上查找可视化不同输入状态的示例。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-126">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> 

<span data-ttu-id="b8c2d-127">![可视化观察状态、目标状态和按下状态的示例](images/640px-interactibleobject-states.png)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-127">![Example of visualizing observation state, targeted state, and pressed state](images/640px-interactibleobject-states.png)</span></span><br>
<span data-ttu-id="b8c2d-128">*可视化观察状态、目标状态和按下状态的示例*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-128">*Example of visualizing observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="b8c2d-129">![全息按钮上的观察状态、目标状态和按下状态](images/MRTK_InteractableState.png)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-129">![Observation state, targeted state, and pressed state on holographic button](images/MRTK_InteractableState.png)</span></span><br>
<span data-ttu-id="b8c2d-130">*全息按钮上的观察状态、目标状态和按下状态*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-130">*Observation state, targeted state, and pressed state on holographic button*</span></span>

#### <a name="neardirect-interactions"></a><span data-ttu-id="b8c2d-131">接近 (直接) 交互</span><span class="sxs-lookup"><span data-stu-id="b8c2d-131">Near(direct) interactions</span></span>

<span data-ttu-id="b8c2d-132">HoloLens 2 支持已表述的手动跟踪输入, 可用于与对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-132">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="b8c2d-133">如果没有 haptic 的反馈和完美的深度理解, 有时很难判断你手中的距离是来自对象, 还是要接触。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-133">Without haptic feedback and perfect depth perception sometimes it can be hard to tell how far away your hand is from an object, or whether you are touching.</span></span> <span data-ttu-id="b8c2d-134">务必提供足够多的可视提示来传达对象的状态, 特别是与全息影像相关。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-134">It is important to provide enough visual cues to communicate the state of the object and in particular of your hands in relation to holograms.</span></span>

<span data-ttu-id="b8c2d-135">使用视觉反馈传达以下内容:</span><span class="sxs-lookup"><span data-stu-id="b8c2d-135">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="b8c2d-136">**默认值 (观察)** :对象的默认空闲状态。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-136">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="b8c2d-137">**悬停**:当手位于全息图附近时, 更改视觉对象以传达此局的目标是全息影像。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-137">**Hover**: When hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="b8c2d-138">**交互的距离和点**: 作为现有方法的方法, 设计反馈可传达投影的交互点, 以及手指的对象距离</span><span class="sxs-lookup"><span data-stu-id="b8c2d-138">**Distance and point of interaction**: As hand approaches hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="b8c2d-139">**联系人开始**:更改视觉对象 (浅色、颜色) 以传达触摸已发生的情况</span><span class="sxs-lookup"><span data-stu-id="b8c2d-139">**Contact Begin**: Change visuals (light, color) to communicate that touch has occured</span></span>
* <span data-ttu-id="b8c2d-140">**Grasped**:当对象为 grasped 时, 更改视觉对象 (浅色、颜色)。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-140">**Grasped**: Change visuals (light, color) when the object is grasped.</span></span>
* <span data-ttu-id="b8c2d-141">**联系人结尾**:触摸已结束时更改视觉对象 (浅色、颜色)。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-141">**Contact End**: Change visuals (light, color) when touch has ended.</span></span>

<span data-ttu-id="b8c2d-142">![可视化接近交互状态的示例](images/640px-interactibleobject-states-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-142">![Example of visualizing near interaction states](images/640px-interactibleobject-states-near.jpg)</span></span><br>
<span data-ttu-id="b8c2d-143">*可视化接近交互状态的示例*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-143">*Example of visualizing near interaction states*</span></span>

<span data-ttu-id="b8c2d-144">[HoloLens 2 中的按钮](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)显示了可视化不同输入交互状态的示例。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-144">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows the example of visualizing different input interaction states.</span></span>

<span data-ttu-id="b8c2d-145">![HoloLens 2 中 pressable 按钮的示例](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-145">![Example of pressable button in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span></span><br>
<span data-ttu-id="b8c2d-146">*HoloLens 2 中 pressable 按钮的示例*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-146">*Example of pressable button in HoloLens 2*</span></span>

<span data-ttu-id="b8c2d-147">在 HoloLens 2 中, 有一个其他视觉提示, 可提高用户对深度认知的置信度。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-147">In HoloLens 2, there is an additional visual cue which improves the user's confidence on the depth perception.</span></span> <span data-ttu-id="b8c2d-148">当手指更接近对象时, 手指上的圆圈会显示并缩小。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-148">The ring on the fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="b8c2d-149">该环最终汇聚为按下状态的点。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-149">The ring eventually converges into a dot on press state.</span></span> <span data-ttu-id="b8c2d-150">此视觉对象 affordance 可帮助用户了解与对象之间的距离。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-150">This visual affordance helps the user understand the distance from the object.</span></span>

<span data-ttu-id="b8c2d-151">![手指环形可视化](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-151">![Fingertip ring visualization](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span></span><br>
<span data-ttu-id="b8c2d-152">*HoloLens 2 中的手指环可视化*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-152">*Fingertip ring visualization in HoloLens 2*</span></span>

<span data-ttu-id="b8c2d-153">![视觉对象反馈](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-153">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="b8c2d-154">*基于邻近边界框的视觉反馈示例*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-154">*Example of visual feedback based on the proximity - Bounding box*</span></span>


### <a name="audio-cue"></a><span data-ttu-id="b8c2d-155">音频提示</span><span class="sxs-lookup"><span data-stu-id="b8c2d-155">Audio cue</span></span>
<span data-ttu-id="b8c2d-156">对于直接交互, 可通过适当的音频反馈来大幅改善用户体验。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-156">For the direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="b8c2d-157">使用音频反馈来传达以下内容:</span><span class="sxs-lookup"><span data-stu-id="b8c2d-157">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="b8c2d-158">**联系人开始**:触摸开始时播放声音</span><span class="sxs-lookup"><span data-stu-id="b8c2d-158">**Contact begin**: Play sound when touch begins</span></span>
* <span data-ttu-id="b8c2d-159">**联系人结尾**:在 touch 端上播放声音</span><span class="sxs-lookup"><span data-stu-id="b8c2d-159">**Contact end**: Play sound on touch end</span></span>
* <span data-ttu-id="b8c2d-160">**开始**操作:开始抓取时播放声音</span><span class="sxs-lookup"><span data-stu-id="b8c2d-160">**Grab begin**: Play sound when grab starts</span></span>
* <span data-ttu-id="b8c2d-161">**抓取结束**:在抓取结束时播放声音</span><span class="sxs-lookup"><span data-stu-id="b8c2d-161">**Grab end**: Play sound on grab end</span></span>

### <a name="voice-command"></a><span data-ttu-id="b8c2d-162">语音命令</span><span class="sxs-lookup"><span data-stu-id="b8c2d-162">Voice command</span></span>
<span data-ttu-id="b8c2d-163">对于任何可交互对象，提供替代交互选项支持非常重要。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-163">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="b8c2d-164">默认情况下，建议为可交互的任何对象提供语音命令支持。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-164">In default, it is recommended to support voice command for any objects that are interactable.</span></span> <span data-ttu-id="b8c2d-165">若要改进可发现性，可以提供悬停状态的工具提示。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-165">To improve the discoverability, you can provide tooltip on hover state.</span></span>

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="语音命令的工具提示" width="350"><br/><span data-ttu-id="b8c2d-167">*语音命令的工具提示*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-167">*Tooltip for the voice command*</span></span>

## <a name="sizing"></a><span data-ttu-id="b8c2d-168">大小调整</span><span class="sxs-lookup"><span data-stu-id="b8c2d-168">Sizing</span></span>
<span data-ttu-id="b8c2d-169">为确保用户能够轻松碰触到所有可交互对象，建议确保使可交互对象的大小达到必要的最小值 (视觉角度，通常以视觉弧度来度量)，这基于该对象与用户之间的距离。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-169">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="b8c2d-170">视觉角度基于用户眼睛与对象之间的距离并保持不变，而目标的物理大小可能会随与用户之间距离的更改而更改。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-170">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="b8c2d-171">若要根据与用户的距离来确定对象的必要物理大小，请尝试使用视觉角度计算器 ，例如[这一个](http://elvers.us/perception/visualAngle/)。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-171">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](http://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="b8c2d-172">下面是有关可交互内容的最小大小的建议。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-172">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="b8c2d-173">直接手动交互的目标大小</span><span class="sxs-lookup"><span data-stu-id="b8c2d-173">Target size for direct hand interaction</span></span>
| <span data-ttu-id="b8c2d-174">长途</span><span class="sxs-lookup"><span data-stu-id="b8c2d-174">Distance</span></span> | <span data-ttu-id="b8c2d-175">查看角度</span><span class="sxs-lookup"><span data-stu-id="b8c2d-175">Viewing angle</span></span> | <span data-ttu-id="b8c2d-176">Size</span><span class="sxs-lookup"><span data-stu-id="b8c2d-176">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="b8c2d-177">45cm</span><span class="sxs-lookup"><span data-stu-id="b8c2d-177">45cm</span></span>  | <span data-ttu-id="b8c2d-178">不小于2°</span><span class="sxs-lookup"><span data-stu-id="b8c2d-178">no smaller than 2°</span></span> | <span data-ttu-id="b8c2d-179">1.6 x 1.6 厘米</span><span class="sxs-lookup"><span data-stu-id="b8c2d-179">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="b8c2d-180">![直接手动交互的目标大小](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-180">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="b8c2d-181">*直接手动交互的目标大小*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-181">*Target size for direct hand interaction*</span></span>

<span data-ttu-id="b8c2d-182">创建直接交互的按钮时, 建议使用较大的最小 3.2 x 3.2 厘米, 以确保有足够的空间来包含图标, 并有可能出现一些文本 \* \*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-182">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text\*\*</span></span>

| <span data-ttu-id="b8c2d-183">长途</span><span class="sxs-lookup"><span data-stu-id="b8c2d-183">Distance</span></span> | <span data-ttu-id="b8c2d-184">最小大小</span><span class="sxs-lookup"><span data-stu-id="b8c2d-184">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="b8c2d-185">45cm</span><span class="sxs-lookup"><span data-stu-id="b8c2d-185">45cm</span></span>  | <span data-ttu-id="b8c2d-186">3.2 x 3.2 厘米</span><span class="sxs-lookup"><span data-stu-id="b8c2d-186">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="b8c2d-187">![按钮的目标大小](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-187">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="b8c2d-188">*按钮的目标大小*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-188">*Target size for the buttons*</span></span>


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="b8c2d-189">手动 ray 或注视交互的目标大小</span><span class="sxs-lookup"><span data-stu-id="b8c2d-189">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="b8c2d-190">长途</span><span class="sxs-lookup"><span data-stu-id="b8c2d-190">Distance</span></span> | <span data-ttu-id="b8c2d-191">查看角度</span><span class="sxs-lookup"><span data-stu-id="b8c2d-191">Viewing angle</span></span> | <span data-ttu-id="b8c2d-192">Size</span><span class="sxs-lookup"><span data-stu-id="b8c2d-192">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="b8c2d-193">2m</span><span class="sxs-lookup"><span data-stu-id="b8c2d-193">2m</span></span>  | <span data-ttu-id="b8c2d-194">不小于1°</span><span class="sxs-lookup"><span data-stu-id="b8c2d-194">no smaller than 1°</span></span> | <span data-ttu-id="b8c2d-195">3.5 x 3.5 厘米</span><span class="sxs-lookup"><span data-stu-id="b8c2d-195">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="b8c2d-196">![手动 ray 或注视交互的目标大小](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-196">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="b8c2d-197">*手动 ray 或注视交互的目标大小*</span><span class="sxs-lookup"><span data-stu-id="b8c2d-197">*Target size for hand ray or gaze interaction*</span></span>

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="b8c2d-198">利用混合现实工具包创建可交互对象 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="b8c2d-198">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="b8c2d-199">在 **[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 中, 可以找到可帮助你创建可交互对象的一系列 Unity 脚本和 prototyping。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-199">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="b8c2d-200">您可以使用这些对象来对各种类型的输入交互状态进行响应。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-200">You can use these to make objects respond to various types of input interaction states.</span></span>

* [<span data-ttu-id="b8c2d-201">可交互</span><span class="sxs-lookup"><span data-stu-id="b8c2d-201">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="b8c2d-202">Button</span><span class="sxs-lookup"><span data-stu-id="b8c2d-202">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="b8c2d-203">手动交互示例场景</span><span class="sxs-lookup"><span data-stu-id="b8c2d-203">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="b8c2d-204">MixedRealityToolkit 的标准着色器提供了各种选项 **, 例如**, 可帮助您创建视觉对象和音频提示。</span><span class="sxs-lookup"><span data-stu-id="b8c2d-204">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="b8c2d-205">MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="b8c2d-205">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a><span data-ttu-id="b8c2d-206">请参阅</span><span class="sxs-lookup"><span data-stu-id="b8c2d-206">See also</span></span>

* [<span data-ttu-id="b8c2d-207">边界框</span><span class="sxs-lookup"><span data-stu-id="b8c2d-207">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="b8c2d-208">对象集合</span><span class="sxs-lookup"><span data-stu-id="b8c2d-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b8c2d-209">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="b8c2d-209">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)