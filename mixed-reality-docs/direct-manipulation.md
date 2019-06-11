---
title: 用手直接操作
description: 直接操作输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 视线, 视线定位, 交互, 设计, 手动近距, HoloLens
ms.openlocfilehash: 6e3512eab4070680c48ee8e95240a17e9925822f
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402395"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="62fee-104">用手直接操作</span><span class="sxs-lookup"><span data-stu-id="62fee-104">Direct manipulation with hands</span></span>
<span data-ttu-id="62fee-105">直接操作是一个输入模型，涉及到用手直接触摸全息影像。</span><span class="sxs-lookup"><span data-stu-id="62fee-105">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="62fee-106">直接操作的目标是使对象的行为如同在现实世界中一样自然。</span><span class="sxs-lookup"><span data-stu-id="62fee-106">The goal with direct manipulation is that objects behave just as they do in the real world.</span></span> <span data-ttu-id="62fee-107">只需按下按钮就能将其激活，抓取对象可以拾取对象，2D 内容的行为与在虚拟触摸屏上类似。</span><span class="sxs-lookup"><span data-stu-id="62fee-107">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span>  <span data-ttu-id="62fee-108">因此，直接操作很容易学会，而且充满了乐趣。</span><span class="sxs-lookup"><span data-stu-id="62fee-108">Because of this, direct manipulation is easy for users to learn, and it's fun too.</span></span>  <span data-ttu-id="62fee-109">它被视为一种“近距”输入模型，这意味着，它最好用于与手臂可触及范围内的内容进行交互。</span><span class="sxs-lookup"><span data-stu-id="62fee-109">It is considered a "near" input model, meaning it is best used for interacting with content that is within arms reach.</span></span>

<span data-ttu-id="62fee-110">直接操作基于可见性，因此具备用户友好性。</span><span class="sxs-lookup"><span data-stu-id="62fee-110">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="62fee-111">没有任何符号手势可以向用户传授操作方法。</span><span class="sxs-lookup"><span data-stu-id="62fee-111">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="62fee-112">所有交互都是围绕一个可以触摸或抓取的可视元素构建的。</span><span class="sxs-lookup"><span data-stu-id="62fee-112">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="62fee-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="62fee-113">Device support</span></span>


| <span data-ttu-id="62fee-114">输入模型</span><span class="sxs-lookup"><span data-stu-id="62fee-114">Input Model</span></span> | [<span data-ttu-id="62fee-115">HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="62fee-115">HoloLens (1st gen)</span></span>](hololens-hardware-details.md) | <span data-ttu-id="62fee-116">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="62fee-116">HoloLens 2</span></span> |[<span data-ttu-id="62fee-117">沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="62fee-117">Immersive headsets</span></span>](immersive-headset-hardware-details.md)|
|:-------- | :-------| :--------| :------------|
| <span data-ttu-id="62fee-118">用手直接操作</span><span class="sxs-lookup"><span data-stu-id="62fee-118">Direct manipulation with hands</span></span> | <span data-ttu-id="62fee-119">❌ 不支持</span><span class="sxs-lookup"><span data-stu-id="62fee-119">❌ Not supported</span></span> | <span data-ttu-id="62fee-120">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="62fee-120">✔️ Recommended</span></span> | <span data-ttu-id="62fee-121">➕ 建议改为[用手指向并提交](point-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="62fee-121">➕ An alternative, [point and commit with hands](point-and-commit.md) is recommended.</span></span>

<span data-ttu-id="62fee-122">直接操作是 HoloLens 2 中的主要输入模型，利用最新的语音式手动跟踪系统。</span><span class="sxs-lookup"><span data-stu-id="62fee-122">Direct manipulation is a primary input model on HoloLens 2, and utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="62fee-123">还可以通过运动控制器在沉浸式头戴显示设备中使用该输入模型，但建议将它用作对象操作以外的主要交互方式。</span><span class="sxs-lookup"><span data-stu-id="62fee-123">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span>  <span data-ttu-id="62fee-124">直接操作在 HoloLens（第 1 代）中不可用。</span><span class="sxs-lookup"><span data-stu-id="62fee-124">Direct manipluation is not available on HoloLens (1st gen).</span></span>


## <a name="collidable-fingertip"></a><span data-ttu-id="62fee-125">可碰撞指尖</span><span class="sxs-lookup"><span data-stu-id="62fee-125">Collidable fingertip</span></span>

<span data-ttu-id="62fee-126">在 HoloLens 2 上，用户的实际手部将被识别并解释为左右手骨架模型。</span><span class="sxs-lookup"><span data-stu-id="62fee-126">On HoloLens 2, the user's real hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="62fee-127">为了实现直接用手触摸全息影像的思路，理想情况下，可将 5 个碰撞体附加到每个手部骨架模型的 5 个指尖。</span><span class="sxs-lookup"><span data-stu-id="62fee-127">To implement the idea of touching holograms directly with hands, ideally, 5 colliders could be attached to 5 fingertips of each hand skeletal model.</span></span> <span data-ttu-id="62fee-128">但实际上，由于缺少触觉反馈，使用 10 个可碰撞指尖会导致全息影像中发生意外且不可预测的碰撞。</span><span class="sxs-lookup"><span data-stu-id="62fee-128">However, practically, due to the lack of tactile feedback, 10 collidable fingertips caused unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="62fee-129">因此，我们建议只在每个食指上放置一个碰撞体。</span><span class="sxs-lookup"><span data-stu-id="62fee-129">Hence, we suggest to only put a collider on each index finger.</span></span> <span data-ttu-id="62fee-130">可碰撞的食指指尖仍可充当涉及其他手指的多种触摸手势的活动触摸点，例如单指按下、双指按下和 5 指按下，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="62fee-130">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as 1-finger press, 1-finger tap, 2-finger press and 5-finger press, as shown in the image below.</span></span>

![可碰撞指尖示意图](images/Collidable-Fingertip-720px.jpg)

### <a name="sphere-collider"></a><span data-ttu-id="62fee-132">球体碰撞体</span><span class="sxs-lookup"><span data-stu-id="62fee-132">Sphere collider</span></span>

<span data-ttu-id="62fee-133">如果不使用随机的一般形状，我们建议使用球体碰撞体，并以可视方式渲染它，以便为近距定位提供更好的线索。</span><span class="sxs-lookup"><span data-stu-id="62fee-133">Instead of using a random generic shape, we suggest to use a sphere collider and to visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="62fee-134">该球体的直径应与食指的粗细相匹配，以提高触摸准确度。</span><span class="sxs-lookup"><span data-stu-id="62fee-134">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="62fee-135">可以通过调用手部 API 来轻松检索手指粗细的变量。</span><span class="sxs-lookup"><span data-stu-id="62fee-135">It will be easy to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="62fee-136">指尖光标</span><span class="sxs-lookup"><span data-stu-id="62fee-136">Fingertip cursor</span></span>

<span data-ttu-id="62fee-137">除了在食指指针上渲染可碰撞球体以外，我们还创建了一个高级解决方案“指尖光标”来实现更好的交互式近距定位体验。</span><span class="sxs-lookup"><span data-stu-id="62fee-137">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced solution, fingertip cursor, to achieve better near-targeting experience interactively.</span></span> <span data-ttu-id="62fee-138">它是附在食指上的一个圆环形光标。</span><span class="sxs-lookup"><span data-stu-id="62fee-138">It is a donut-shaped cursor attached on the index fingertip.</span></span> <span data-ttu-id="62fee-139">根据邻近性，它会对目标的方向和大小做出动态反应，下面提供了详述：</span><span class="sxs-lookup"><span data-stu-id="62fee-139">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="62fee-140">将食指移向全息影像时，该光标始终与全息影像的表面平行，在移动过程中会逐渐缩小其大小。</span><span class="sxs-lookup"><span data-stu-id="62fee-140">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface  and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="62fee-141">一旦手指接触到表面，该光标就会缩小为一个点，并发出触摸事件。</span><span class="sxs-lookup"><span data-stu-id="62fee-141">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="62fee-142">借助交互式反馈，用户可以实现高精度的近距定位任务，例如，触发 Web 内容中的超链接，或按下某个按钮，如下所示。</span><span class="sxs-lookup"><span data-stu-id="62fee-142">With the interactive feedback, users can achieve high precision near targeting tasks, such as triggering a hyperlink on web content or pressing a button, as shown, below.</span></span> 

![指尖光标示意图](images/Fingertip-Cursor-720px.jpg)

## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="62fee-144">带有邻近着色器的边界框</span><span class="sxs-lookup"><span data-stu-id="62fee-144">Bounding box with proximity shader</span></span>

<span data-ttu-id="62fee-145">全息影像本身还需要能够提供视频和音频反馈，以补偿触觉反馈的缺失。</span><span class="sxs-lookup"><span data-stu-id="62fee-145">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="62fee-146">为此，我们提出了带有邻近着色器的边界框的概念。</span><span class="sxs-lookup"><span data-stu-id="62fee-146">For that, we generate the concept of a bounding box with proximity shader.</span></span> <span data-ttu-id="62fee-147">边界框是包含一个 3D 对象的紧凑立体区域。</span><span class="sxs-lookup"><span data-stu-id="62fee-147">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="62fee-148">边界框提供名为“邻近着色器”的交互式渲染机制。</span><span class="sxs-lookup"><span data-stu-id="62fee-148">The bounding box has an interactive rendering mechanism called proximity shader.</span></span> <span data-ttu-id="62fee-149">邻近着色器的行为：</span><span class="sxs-lookup"><span data-stu-id="62fee-149">The proximity shader behaves:</span></span>

* <span data-ttu-id="62fee-150">当食指处于某个范围内时，指尖光点会投射到边界框的表面。</span><span class="sxs-lookup"><span data-stu-id="62fee-150">When the index finger is within a range, a fingertip spotlight is cast on the surface of bounding box.</span></span>
* <span data-ttu-id="62fee-151">当指尖更靠近表面时，光点会相应地收缩。</span><span class="sxs-lookup"><span data-stu-id="62fee-151">When the fingertip gets closer to the surface, the spotlight condenses accordingly.</span></span>
* <span data-ttu-id="62fee-152">一旦指尖接触到表面，整个边界框就会改变颜色，或生成视觉效果来反映触摸状态。</span><span class="sxs-lookup"><span data-stu-id="62fee-152">As soon as the fingertip touch the surface, the whole bounding box changes the color or generate visual effect to reflect the touch state.</span></span>
* <span data-ttu-id="62fee-153">同时，可以激活某种音效来增强视觉触摸反馈。</span><span class="sxs-lookup"><span data-stu-id="62fee-153">Meanwhile, a sound effect can be activated to enhance the visual touch feedback.</span></span>

![带有邻近着色器的边界框示意图](images/Bounding-Box-With-Proximity-Shader-720px.jpg)

## <a name="pressable-button"></a><span data-ttu-id="62fee-155">可按按钮</span><span class="sxs-lookup"><span data-stu-id="62fee-155">Pressable button</span></span>

<span data-ttu-id="62fee-156">现在，用户可以使用可碰撞指尖来与一个非常基本的全息图 UI 组件（可按按钮）进行交互。</span><span class="sxs-lookup"><span data-stu-id="62fee-156">With a collidable fingertip, users are now ready to interact with the very fundamental holographic UI component, pressable button.</span></span> <span data-ttu-id="62fee-157">可按按钮是专门用手指直接按下的全息图按钮。</span><span class="sxs-lookup"><span data-stu-id="62fee-157">A pressable button is a holographic button tailored for direct finger press.</span></span> <span data-ttu-id="62fee-158">同样，由于缺少触觉反馈，可按按钮配备了两个机制来解决触觉反馈相关的问题。</span><span class="sxs-lookup"><span data-stu-id="62fee-158">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="62fee-159">第一个机制是上一部分已详述的带有邻近着色器的边界框。</span><span class="sxs-lookup"><span data-stu-id="62fee-159">The first mechanism is a bounding box with proximity shader, detailed in the previous section.</span></span> <span data-ttu-id="62fee-160">该机制可以在用户接近和接触到某个按钮时提供更好的邻近感。</span><span class="sxs-lookup"><span data-stu-id="62fee-160">It serves to provide better sense of proximity for users to approach and make contact with a button.</span></span>
* <span data-ttu-id="62fee-161">第二个机制是沉降。</span><span class="sxs-lookup"><span data-stu-id="62fee-161">The second one is depression.</span></span> <span data-ttu-id="62fee-162">在指尖接触到按钮后，该机制可产生一种按入感。</span><span class="sxs-lookup"><span data-stu-id="62fee-162">It creates sense of press, after a fingertip contacts the button.</span></span> <span data-ttu-id="62fee-163">该机制的工作原理是，按钮在深度轴上如影随形地与指尖一起移动。</span><span class="sxs-lookup"><span data-stu-id="62fee-163">The mechanism is that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="62fee-164">当指尖达到指定的深度（按下按钮），或者在移过按钮后脱离该深度（松开按钮）时，可以触发按钮。</span><span class="sxs-lookup"><span data-stu-id="62fee-164">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="62fee-165">触发按钮时，应该添加音效来增强反馈。</span><span class="sxs-lookup"><span data-stu-id="62fee-165">The sound effect should be added to enhance feedback, when the button is triggered.</span></span>

![可按按钮示意图](images/Pressable-Button-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="62fee-167">2D 盖板交互</span><span class="sxs-lookup"><span data-stu-id="62fee-167">2D slate interaction</span></span>

<span data-ttu-id="62fee-168">2D 盖板是容装 Web 浏览器等 2D 应用内容的全息图容器。</span><span class="sxs-lookup"><span data-stu-id="62fee-168">A 2D slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="62fee-169">通过直接操作来与 2D 盖板交互的设计概念是，利用与物理触摸屏交互的心理模型。</span><span class="sxs-lookup"><span data-stu-id="62fee-169">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

<span data-ttu-id="62fee-170">若要与盖板触点交互：</span><span class="sxs-lookup"><span data-stu-id="62fee-170">To interact with the slate contact:</span></span>

* <span data-ttu-id="62fee-171">使用食指按下某个超链接或按钮。</span><span class="sxs-lookup"><span data-stu-id="62fee-171">Use an index finger to press a hyperlink or a button.</span></span>
* <span data-ttu-id="62fee-172">使用食指上下滚动盖板内容。</span><span class="sxs-lookup"><span data-stu-id="62fee-172">Use an index finger to scroll a slate content up and down.</span></span>
* <span data-ttu-id="62fee-173">用户使用两根食指根据手指的相对运动来放大和缩小盖板内容。</span><span class="sxs-lookup"><span data-stu-id="62fee-173">Users use two index fingers to zoom in and out the slate content according to relative motion of fingers.</span></span>

![2D 盖板示意图](images/2D-Slate-Interaction-720px.jpg)

<span data-ttu-id="62fee-175">操作 2D 盖板本身：</span><span class="sxs-lookup"><span data-stu-id="62fee-175">For manipulating the 2D slate itself:</span></span>

* <span data-ttu-id="62fee-176">将手靠近边角和边缘，显示最靠近的可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="62fee-176">Approach your hands toward corners and edges to reveal the closest manipulation affordances.</span></span>
* <span data-ttu-id="62fee-177">抓取可视操作元素，通过边角视觉元素执行统一的缩放，然后通过边缘视觉元素进行重排。</span><span class="sxs-lookup"><span data-stu-id="62fee-177">Grab the manipulation affordances, and perform uniform scaling through the corner affordances and reflow via the edge affordances.</span></span>
* <span data-ttu-id="62fee-178">抓取 2D 盖板顶层的全息条，以移动整个盖板。</span><span class="sxs-lookup"><span data-stu-id="62fee-178">Grab the holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>

![盖板操作示意图](images/Manipulate-2d-slate-720px.jpg)

## <a name="3d-object-manipulation"></a><span data-ttu-id="62fee-180">3D 对象操作</span><span class="sxs-lookup"><span data-stu-id="62fee-180">3D object manipulation</span></span>

<span data-ttu-id="62fee-181">HoloLens 2 可让用户通过将边界框应用到每个 3D 对象，来用手直接操作 3D 全息图对象。</span><span class="sxs-lookup"><span data-stu-id="62fee-181">HoloLens 2 lets lets users enable their hands to direct manipulate 3D hologramphic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="62fee-182">边界框通过其邻近着色器提供更好的深度感。</span><span class="sxs-lookup"><span data-stu-id="62fee-182">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="62fee-183">使用边界框可以通过两种设计方法来操作 3D 对象。</span><span class="sxs-lookup"><span data-stu-id="62fee-183">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="62fee-184">基于视觉元素的操作</span><span class="sxs-lookup"><span data-stu-id="62fee-184">Affordance-based manipulation</span></span>

<span data-ttu-id="62fee-185">可以通过边界框及其周围的操作视觉元素来操作 3D 对象。</span><span class="sxs-lookup"><span data-stu-id="62fee-185">This lets you manipulate the 3D object through a bounding box and the manipulation affordances around it.</span></span> <span data-ttu-id="62fee-186">一旦用户的手靠近某个 3D 对象，就会显示边界框和最靠近的视觉元素。</span><span class="sxs-lookup"><span data-stu-id="62fee-186">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="62fee-187">用户可以抓取边界框来移动整个对象，抓取边缘视觉元素来旋转对象，或者抓取边角视觉元素进行统一的缩放。</span><span class="sxs-lookup"><span data-stu-id="62fee-187">Users can grab the bounding box to move the whole object, the edge affordances to rotate and the corner affordances to scale uniformly.</span></span>

![3D 对象操作示意图](images/3D-Object-Manipulation-720px.jpg)

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="62fee-189">非基于视觉元素的操作</span><span class="sxs-lookup"><span data-stu-id="62fee-189">Non-affordance based manipulation</span></span>

<span data-ttu-id="62fee-190">在此机制中，不会将任何视觉元素附加到边界框。</span><span class="sxs-lookup"><span data-stu-id="62fee-190">In this mechanism, no affordance is attached to the bounding box.</span></span> <span data-ttu-id="62fee-191">用户只能显示边界框，然后直接与它交互。</span><span class="sxs-lookup"><span data-stu-id="62fee-191">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="62fee-192">如果用一只手抓取边界框，则对象的平移和旋转将与手的动作和方向相关联。</span><span class="sxs-lookup"><span data-stu-id="62fee-192">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="62fee-193">用两只手抓取对象时，用户可以根据两只手的相对运动来平移、缩放和旋转该对象。</span><span class="sxs-lookup"><span data-stu-id="62fee-193">When the object is grabbed with two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="62fee-194">具体的操作需要精确，我们建议使用**基于视觉元素的操作**，因为它提供较高的粒度级。</span><span class="sxs-lookup"><span data-stu-id="62fee-194">Specific manipulation requires precision, we recommend you use **affordance-based manipulation**, because it provides a high level of granularity.</span></span> <span data-ttu-id="62fee-195">若要灵活操作，我们建议使用**非基于视觉元素的操作**，因为它可以实现充满乐趣的即时体验。</span><span class="sxs-lookup"><span data-stu-id="62fee-195">For flexible manipulation, we recommend you uses **non-affordance manipulation** is as it allows for instant and playful experiences.</span></span>

## <a name="instinctual-gestures"></a><span data-ttu-id="62fee-196">本能手势</span><span class="sxs-lookup"><span data-stu-id="62fee-196">Instinctual gestures</span></span>

<span data-ttu-id="62fee-197">在 HoloLens（第 1 代）中，我们已向用户传授了几种预定义的手势，例如“开花”和“隔空敲击”。</span><span class="sxs-lookup"><span data-stu-id="62fee-197">With HoloLens (1st gen), we taught users a couple predefined gestures,such as Bloom and Air Tap.</span></span> <span data-ttu-id="62fee-198">对于 HoloLens 2，我们不要求用户记住任何符号手势。</span><span class="sxs-lookup"><span data-stu-id="62fee-198">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="62fee-199">用户与全息影像和内容交互所要使用的全部手势都是本能的。</span><span class="sxs-lookup"><span data-stu-id="62fee-199">All required user gestures, users need to interact with holograms and contents, are instinctual.</span></span> <span data-ttu-id="62fee-200">实现本能手势的方法是通过 UI 视觉元素的设计引导用户执行手势。</span><span class="sxs-lookup"><span data-stu-id="62fee-200">The way to achieve instinctual gesture is to guide users to perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="62fee-201">例如，如果我们建议使用夹紧的两根手指来抓取某个对象或控制点，该对象或控制点应该很小。</span><span class="sxs-lookup"><span data-stu-id="62fee-201">For example, if we encourage you to grab an object or a control point with two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="62fee-202">如果我们希望你执行五指抓取，则该对象或控制点应该相对较大。</span><span class="sxs-lookup"><span data-stu-id="62fee-202">If we want you to perform five finger grab, the object or the control point should be relatively big.</span></span> <span data-ttu-id="62fee-203">类似于按钮，微小的按钮仅限用户用一根手指点按它，而巨大的按钮则表示建议用户用手掌来点按它。</span><span class="sxs-lookup"><span data-stu-id="62fee-203">Similar to buttons, a tiny button would limit users to press it with a single finger, while a huge button would encourage users to press it with their palms.</span></span>

![](images/Instinctual-Gestures-720px.jpg)

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="62fee-204">手部与 6 DoF 控制器之间的对称设计</span><span class="sxs-lookup"><span data-stu-id="62fee-204">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="62fee-205">你可能已经注意到，我们可以在 AR 中的手部与 VR 中的运动控制器之间引入类似的交互方式。</span><span class="sxs-lookup"><span data-stu-id="62fee-205">You may have noticed that there are now interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="62fee-206">使用这两种输入可在其各自的环境中触发直接操作。</span><span class="sxs-lookup"><span data-stu-id="62fee-206">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="62fee-207">在 HoloLens 2 中，用手近距抓取和拖放非常类似于在 WMR 中的运动控制器上抓取按钮。</span><span class="sxs-lookup"><span data-stu-id="62fee-207">In HoloLens 2, grabbing and dragging with hands at a close distance works much in the same way as the grab button does on the motion controllers in WMR.</span></span> <span data-ttu-id="62fee-208">因此，用户会熟悉这两个平台中的交互方式。如果你决定将应用从一个平台移植到另一个平台，这种类似性会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="62fee-208">This provides users with interaction familiarity between the two platforms and may prove useful should you ever decide to port your app from one to the other.</span></span>

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="62fee-209">使用眼动跟踪进行优化</span><span class="sxs-lookup"><span data-stu-id="62fee-209">Optimize with eye tracking</span></span>

<span data-ttu-id="62fee-210">如果直接操作按预期方式运行，则用户会觉得它充满魔力；但是，如果只能在无意触发全息影像的情况下才能四处移动手部，则直接操作可能很快就会带来困扰。</span><span class="sxs-lookup"><span data-stu-id="62fee-210">Direct manipulation can feel magical if it works as intended, but can also quickly become frustrating if you can’t move your hand anywhere anymore without unintentionally triggering a hologram.</span></span>
<span data-ttu-id="62fee-211">眼动追踪可能有助于更好地识别用户的意图。</span><span class="sxs-lookup"><span data-stu-id="62fee-211">Eye tracking can potentially help in better identifying what the user’s intent is.</span></span>

* <span data-ttu-id="62fee-212">**何时**：减少错误触发操作响应的情况。</span><span class="sxs-lookup"><span data-stu-id="62fee-212">**When**: Reduce falsely triggering a manipulation response.</span></span> <span data-ttu-id="62fee-213">眼动追踪可以更好地识别用户当前正在与哪个对象互动。</span><span class="sxs-lookup"><span data-stu-id="62fee-213">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="62fee-214">例如，假设你在伸手抓取一个现实的工具时正在阅读某段全息图（说明）文本。</span><span class="sxs-lookup"><span data-stu-id="62fee-214">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="62fee-215">此外，你的手会意外地移过某些以前未曾注意到的交互式全息图按钮（也许这些按钮在用户的视场 (FOV) 以外）。</span><span class="sxs-lookup"><span data-stu-id="62fee-215">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (maybe it even was outside of the user's Field-of-View (FOV)).</span></span>

  <span data-ttu-id="62fee-216">长话短说：如果用户有一段时间未注视某张全息影像，但检测到了该全息图的触摸或抓取事件，则有可能该用户并不真正想要与该全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="62fee-216">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="62fee-217">**哪一个**：除了解决误报激活以外，另一个示例反映了眼动跟踪可以更好地识别要抓取或点击的全息影像，因为从你的立场来看，精确的交点可能并不明确，尤其是多个全息影像相互靠近时。</span><span class="sxs-lookup"><span data-stu-id="62fee-217">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="62fee-218">尽管 HoloLens 2 上的眼动跟踪在如何准确确定视线方面存在一定的限制，但对于近距交互，它仍可以发挥很大的作用，因为使用手动输入交互时，存在深度差异。</span><span class="sxs-lookup"><span data-stu-id="62fee-218">While eye tracking on HoloLens 2 has a certain limitation on how accurately it can determine you eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span>  <span data-ttu-id="62fee-219">举例而言，这意味着有时难以确定手是全息影像的前面还是后面，因此无法精确抓取某个操作小组件。</span><span class="sxs-lookup"><span data-stu-id="62fee-219">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget for example.</span></span>

* <span data-ttu-id="62fee-220">**何处**：使用有关用户正在使用快速投射手势观看的内容的信息。</span><span class="sxs-lookup"><span data-stu-id="62fee-220">**Where to**: Use information about what a user is looking at with quick- throwing gestures.</span></span> <span data-ttu-id="62fee-221">抓取一幅全息影像，然后大致将它投射到预期目标。</span><span class="sxs-lookup"><span data-stu-id="62fee-221">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="62fee-222">尽管有时可以正常完成此操作，但快速执行手势可能会导致目标极不准确。</span><span class="sxs-lookup"><span data-stu-id="62fee-222">While this may sometimes works just fine, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="62fee-223">在此情况下，眼动跟踪可以派上用场，它会将手投矢量回归到预期位置。</span><span class="sxs-lookup"><span data-stu-id="62fee-223">This is where eye tracking could help out to lean the hand throwing vector back to your intended position.</span></span>

## <a name="see-also"></a><span data-ttu-id="62fee-224">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62fee-224">See also</span></span>

* [<span data-ttu-id="62fee-225">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="62fee-225">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="62fee-226">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="62fee-226">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="62fee-227">本能交互</span><span class="sxs-lookup"><span data-stu-id="62fee-227">Instinctual interactions</span></span>](interaction-fundamentals.md)

