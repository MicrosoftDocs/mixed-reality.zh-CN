---
title: 使用手指向和提交
description: 指向和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实、交互、设计、hololens、手、远、指向和提交
ms.openlocfilehash: 30f85d2bb455abab3a533e0a829b4fba8cea0a7a
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402380"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="1ccb1-104">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="1ccb1-104">Point and commit with hands</span></span>
<span data-ttu-id="1ccb1-105">用手指向和提交是一种输入模型，使用户对远处的 2D 内容和 3D 对象进行定位、选择和操作。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects in the distance.</span></span> <span data-ttu-id="1ccb1-106">这种“远程”交互技术是混合现实所独有的，并不是人类与现实世界交互的自然方式。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-106">This "far" interaction technique is unique to mixed reality and is not a way humans naturally intereact with the real world.</span></span> <span data-ttu-id="1ccb1-107">例如，在超级英雄电影 X-Men  中，角色 [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) 能够伸出手去操控远处的对象。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-107">For example, in the super hero movie *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="1ccb1-108">这是人类在现实中无法做到的。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="1ccb1-109">在 HoloLens (AR) 和混合现实 (VR) 中，我们赋予了用户这种神奇的力量，打破了现实世界的物理约束，不仅能让用户享受到全息内容的愉悦体验，还能让互动更加有效、高效。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-109">In both HoloLens (AR) and Mixed Reality (VR), we equip users with this magical power, breaking the physical constraint of the real world not only to have a delightful experience with holographic contents but also to make the interaction more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="1ccb1-110">设备支持</span><span class="sxs-lookup"><span data-stu-id="1ccb1-110">Device support</span></span>

<span data-ttu-id="1ccb1-111">输入模型</span><span class="sxs-lookup"><span data-stu-id="1ccb1-111">Input model</span></span> | [<span data-ttu-id="1ccb1-112">HoloLens（第一代）</span><span class="sxs-lookup"><span data-stu-id="1ccb1-112">HoloLens (1st gen)</span></span>](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | <span data-ttu-id="1ccb1-113">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1ccb1-113">HoloLens 2</span></span> | [<span data-ttu-id="1ccb1-114">沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="1ccb1-114">Immersive headsets</span></span>](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
<span data-ttu-id="1ccb1-115">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="1ccb1-115">Point and commit with hands</span></span> | <span data-ttu-id="1ccb1-116">❌ 不支持</span><span class="sxs-lookup"><span data-stu-id="1ccb1-116">❌ Not supported</span></span> | <span data-ttu-id="1ccb1-117">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="1ccb1-117">✔️ Recommended</span></span> | <span data-ttu-id="1ccb1-118">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="1ccb1-118">✔️ Recommended</span></span>

<span data-ttu-id="1ccb1-119">指向和提交（也称为远程手）是利用新的铰接式手跟踪系统的新功能之一。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-119">Point and commit, also known as hands far, is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="1ccb1-120">该输入模型也是在沉浸式头戴显示设备上通过使用运动控制器的主要输入模式。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

## <a name="hand-rays"></a><span data-ttu-id="1ccb1-121">手部射线</span><span class="sxs-lookup"><span data-stu-id="1ccb1-121">Hand rays</span></span>

<span data-ttu-id="1ccb1-122">在 HoloLens 2 上，我们创造了一种从手掌中心射出的手部射线。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-122">On HoloLens 2, we created a hand ray that shoots out from the center of a palm.</span></span> <span data-ttu-id="1ccb1-123">该射线被视为手的延伸。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="1ccb1-124">圆环形光标连接到射线的末端，以指示射线与目标对象相交的位置。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="1ccb1-125">然后光标所指向的对象可以接收来自手的手势命令。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="1ccb1-126">通过使用拇指和食指执行隔空敲击动作来触发该基本手势命令。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="1ccb1-127">通过使用手射线指向和隔空敲击以提交，用户可以激活 Web 内容上的按钮或超链接。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink on a web content.</span></span> <span data-ttu-id="1ccb1-128">借助更多的复合手势，用户可以在 Web 内容中导航，并从远处操纵 3D 对象。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="1ccb1-129">手部射线的视觉设计也应对这些指向和提交状态做出反应，如下所述：</span><span class="sxs-lookup"><span data-stu-id="1ccb1-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

* <span data-ttu-id="1ccb1-130">在指向状态下，射线是虚线，光标是圆环形状  。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-130">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
* <span data-ttu-id="1ccb1-131">在提交状态下，光线变为实线，光标缩小为点  。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-131">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a><span data-ttu-id="1ccb1-132">在远近之间转换</span><span class="sxs-lookup"><span data-stu-id="1ccb1-132">Transition between near and far</span></span>

<span data-ttu-id="1ccb1-133">我们没有使用特定的手势（如“用食指指向”来引导射线），而是设计了射线从手掌中心发出，留出五根手指来做更多的操控性手势，如捏和抓。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-133">Instead of using specific gesture, such as "pointing with index finger" to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="1ccb1-134">通过这种设计，我们只创建了一个心理模型，支持远近交互使用完全相同的一组手势。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-134">With this design, we create only one mental model, supporting exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="1ccb1-135">可以使用相同的抓取手势来操纵不同距离的对象。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-135">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="1ccb1-136">射线的调用是自动的，基于邻近度：</span><span class="sxs-lookup"><span data-stu-id="1ccb1-136">The invocation of the rays is automatic and proximity based:</span></span>

*  <span data-ttu-id="1ccb1-137">当对象在手臂可达距离（大约 50 cm）内时，射线会自动关闭，支持近距离交互。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-137">When an object is within arm reached distance (roughly 50 cm), the rays are turned off automatically encouraging for near interaction.</span></span>
*  <span data-ttu-id="1ccb1-138">当对象距离超过 50 cm 时，将启用射线。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-138">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="1ccb1-139">转换应该顺利无缝。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-139">The transition should be smooth and seamless.</span></span>

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="1ccb1-140">2D 平板电脑交互</span><span class="sxs-lookup"><span data-stu-id="1ccb1-140">2D slate interaction</span></span>

<span data-ttu-id="1ccb1-141">2D 平板电脑是装有 Web 浏览器等 2D 应用内容的全息容器。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-141">A 2D Slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="1ccb1-142">与 2D 平板电脑进行远距离交互的设计理念是使用手部射线进行瞄准，并隔空敲击以进行选择。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-142">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="1ccb1-143">在用手部射线瞄准目标后，用户可以通过隔空敲击来触发超链接或按钮。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-143">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="1ccb1-144">他们可以用一只手“隔空敲击并拖动”来上下滚动平板电脑内容。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-144">They can use one hand to "air tap and drag" to scroll a slate content up and down.</span></span> <span data-ttu-id="1ccb1-145">使用两只手进行隔空敲击和拖动的相对运动可以放大和缩小平板电脑内容。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-145">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="1ccb1-146">在角落和边缘处瞄准手部射线可显示最接近的可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-146">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="1ccb1-147">通过“抓取和拖动”可视操作元素，用户可通过边角可视操作元素执行统一的缩放，然后通过边缘可视操作元素重排平板电脑。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-147">By "grab and drag" the manipulation affordances, users can perform uniform scaling through the corner affordances and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="1ccb1-148">抓取并拖动 2D 平板电脑顶部的 holobar 可移动整个平板电脑。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-148">Grabbing and dragging the holobar at the top of the 2D slate can users move the whole slate.</span></span>

![](images/2D-Slate-Interaction-Far-720px.jpg)

<span data-ttu-id="1ccb1-149">操作 2D 平板电脑本身：</span><span class="sxs-lookup"><span data-stu-id="1ccb1-149">For manipulating the 2D slate itself:</span></span><br>

* <span data-ttu-id="1ccb1-150">用户在角落或边缘处指向手部射线可显示最接近的可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-150">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="1ccb1-151">通过对可视操作元素应用操作手势，用户可通过边角可视操作元素执行统一的缩放，然后通过边缘可视操作元素重排平板电脑。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-151">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="1ccb1-152">通过在 2D 平板电脑顶部的 holobar 上应用操纵手势，用户可以移动整个平板电脑。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-152">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the whole slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="1ccb1-153">3D 对象操作</span><span class="sxs-lookup"><span data-stu-id="1ccb1-153">3D object manipulation</span></span>

<span data-ttu-id="1ccb1-154">在直接操作中，用户可以通过两种方式操纵 3D 对象，基于可视操作元素的操作和不基于可视操作元素的操作。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-154">In direct manipulation, there are two ways for users to manipulate 3D object, affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="1ccb1-155">在指向和提交模型中，用户能够通过手部射线实现完全相同的任务。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-155">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="1ccb1-156">不需要额外的学习。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-156">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="1ccb1-157">基于可视操作元素的操作</span><span class="sxs-lookup"><span data-stu-id="1ccb1-157">Affordance-based manipulation</span></span>
<span data-ttu-id="1ccb1-158">用户使用手部射线指向并显示边框和可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-158">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="1ccb1-159">用户可在边框上应用操作手势来移动整个对象，在边缘可视操作元素上应用操作手势来旋转对象，以及在边角可视操作元素上应用操作手势以进行统一的缩放。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-159">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate and on the coner affordances to scale uniformly.</span></span> <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="1ccb1-160">不基于可视操作元素的操作</span><span class="sxs-lookup"><span data-stu-id="1ccb1-160">Non-affordance based manipulation</span></span>
<span data-ttu-id="1ccb1-161">用户用手部射线指向以显示边界框，然后直接对其应用操作手势。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-161">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="1ccb1-162">如果用一只手进行操作，对象的平移和旋转将与手的移动和方向相关联。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-162">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="1ccb1-163">如果用两只手进行操作，用户可以根据两只手的相对运动来平移、缩放和旋转对象。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-163">With two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gesturers"></a><span data-ttu-id="1ccb1-164">本能手势</span><span class="sxs-lookup"><span data-stu-id="1ccb1-164">Instinctual gesturers</span></span>
<span data-ttu-id="1ccb1-165">指向和提交的本能手势的概念类似于直接操作的概念。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-165">The concept of instinctual gestures for point and commit is similar to that for direct manipulation.</span></span> <span data-ttu-id="1ccb1-166">用户应在 3D 对象上执行的手势是由 UI 可视操作元素的设计指导的。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-166">The gestures users are suppose to perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="1ccb1-167">例如，一个小的控制点可能会促使用户用拇指和食指捏，而用户可能想用所有 5 根手指抓一个较大的对象。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-167">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all 5 fingers.</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="1ccb1-168">手部与 6 DoF 控制器之间的对称设计</span><span class="sxs-lookup"><span data-stu-id="1ccb1-168">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="1ccb1-169">远程交互的指向和提交概念最初是为混合现实门户 (MRP) 创建和定义的，在混合现实门户中，用户戴上沉浸式头戴显示设备，通过运动控制器与 3D 对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-169">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP), where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="1ccb1-170">运动控制器射出光线来指向和操纵远处的对象。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-170">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="1ccb1-171">控制器上有用于进一步提交不同操作的按钮。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-171">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="1ccb1-172">我们利用射线的交互模式，并将其与双手关联。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-172">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="1ccb1-173">借助这种对称设计，熟悉 MRP 的用户在使用 HoloLen 2 时不需要学习另一种交互模式来进行远距离指向和操纵，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="1ccb1-173">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a><span data-ttu-id="1ccb1-174">本能手势</span><span class="sxs-lookup"><span data-stu-id="1ccb1-174">Instinctual gestures</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a><span data-ttu-id="1ccb1-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ccb1-175">See also</span></span>
* [<span data-ttu-id="1ccb1-176">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="1ccb1-176">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="1ccb1-177">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="1ccb1-177">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1ccb1-178">本能交互</span><span class="sxs-lookup"><span data-stu-id="1ccb1-178">Instinctual interactions</span></span>](interaction-fundamentals.md)

