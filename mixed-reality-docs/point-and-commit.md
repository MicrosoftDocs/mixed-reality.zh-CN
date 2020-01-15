---
title: 使用手指向和提交
description: 指向和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 交互, 设计, HoloLens, 手, 远, 指向和提交
ms.openlocfilehash: d3f886fd8e892fe34116c3a1d601ae3a87d87a9b
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901531"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="95dcc-104">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="95dcc-104">Point and commit with hands</span></span>

![光标](images/UX/UX_Hero_HandRay.jpg)

<span data-ttu-id="95dcc-106">“用手指向和提交”是一种输入模型，使用户对无法接触的 2D 内容和 3D 对象进行定位、选择和操作。</span><span class="sxs-lookup"><span data-stu-id="95dcc-106">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects that are out of reach.</span></span> <span data-ttu-id="95dcc-107">这种“远程”交互技术是混合现实所独有的，并不是人类与现实世界交互的自然方式。</span><span class="sxs-lookup"><span data-stu-id="95dcc-107">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally interact with the real world.</span></span> <span data-ttu-id="95dcc-108">例如，在超级英雄电影 *X-Men* 中，角色 [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) 能够伸出手去操控远处的对象。</span><span class="sxs-lookup"><span data-stu-id="95dcc-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="95dcc-109">这是人类在现实中无法做到的。</span><span class="sxs-lookup"><span data-stu-id="95dcc-109">This is not something humans can do in reality.</span></span> <span data-ttu-id="95dcc-110">在 HoloLens (AR) 和混合现实 (MR) 中，我们赋予了用户这种神奇的力量，打破了现实世界的物理约束，不仅能让用户享受到全息内容的愉悦体验，还能让互动更加有效、高效。</span><span class="sxs-lookup"><span data-stu-id="95dcc-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic content but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="95dcc-111">设备支持</span><span class="sxs-lookup"><span data-stu-id="95dcc-111">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="95dcc-112"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="95dcc-112"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="95dcc-113"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="95dcc-113"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="95dcc-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="95dcc-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="95dcc-115"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="95dcc-115"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="95dcc-116">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="95dcc-116">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="95dcc-117">❌ 不支持</span><span class="sxs-lookup"><span data-stu-id="95dcc-117">❌ Not supported</span></span></td>
     <td><span data-ttu-id="95dcc-118">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="95dcc-118">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="95dcc-119">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="95dcc-119">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="95dcc-120">“用手指向和提交”是利用新的铰接式手跟踪系统的新功能之一。 </span><span class="sxs-lookup"><span data-stu-id="95dcc-120">_"Point and commit with hands"_ is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="95dcc-121">该输入模型也是在沉浸式头戴显示设备上通过使用运动控制器的主要输入模式。</span><span class="sxs-lookup"><span data-stu-id="95dcc-121">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="95dcc-122">手部射线</span><span class="sxs-lookup"><span data-stu-id="95dcc-122">Hand rays</span></span>

<span data-ttu-id="95dcc-123">在 HoloLens 2 上，我们创造了一种从用户手掌中心射出的手部射线。</span><span class="sxs-lookup"><span data-stu-id="95dcc-123">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="95dcc-124">该射线被视为手的延伸。</span><span class="sxs-lookup"><span data-stu-id="95dcc-124">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="95dcc-125">圆环形光标连接到射线的末端，以指示射线与目标对象相交的位置。</span><span class="sxs-lookup"><span data-stu-id="95dcc-125">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="95dcc-126">然后光标所指向的对象可以接收来自手的手势命令。</span><span class="sxs-lookup"><span data-stu-id="95dcc-126">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="95dcc-127">通过使用拇指和食指执行隔空敲击动作来触发该基本手势命令。</span><span class="sxs-lookup"><span data-stu-id="95dcc-127">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="95dcc-128">通过使用手射线指向和隔空敲击以提交，用户可以激活某个按钮或超链接。</span><span class="sxs-lookup"><span data-stu-id="95dcc-128">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="95dcc-129">借助更多的复合手势，用户可以在 Web 内容中导航，并从远处操纵 3D 对象。</span><span class="sxs-lookup"><span data-stu-id="95dcc-129">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="95dcc-130">手部射线的视觉设计也应对这些指向和提交状态做出反应，如下所述：</span><span class="sxs-lookup"><span data-stu-id="95dcc-130">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="95dcc-131">![手部射线指向](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-131">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="95dcc-132">**“指向”状态**</span><span class="sxs-lookup"><span data-stu-id="95dcc-132">**Pointing state**</span></span><br>
        <span data-ttu-id="95dcc-133">在指向状态下，射线是虚线，光标是圆环形状  。</span><span class="sxs-lookup"><span data-stu-id="95dcc-133">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="95dcc-134">![手部射线提交](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-134">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="95dcc-135">**“提交”状态**</span><span class="sxs-lookup"><span data-stu-id="95dcc-135">**Commit state**</span></span><br>
        <span data-ttu-id="95dcc-136">在提交状态下，光线变为实线，光标缩小为点  。</span><span class="sxs-lookup"><span data-stu-id="95dcc-136">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a><span data-ttu-id="95dcc-137">在远近之间转换</span><span class="sxs-lookup"><span data-stu-id="95dcc-137">Transition between near and far</span></span>

<span data-ttu-id="95dcc-138">我们没有使用特定的手势（如“用食指指向”来引导射线），而是设计了射线从手掌中心发出，留出五根手指来做更多的操控性手势，如捏和抓。</span><span class="sxs-lookup"><span data-stu-id="95dcc-138">Instead of using specific gestures, such as "pointing with index finger" to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="95dcc-139">通过这种设计，我们只创建了一个心理模型 - 同一组手势用于远交互和近交互。</span><span class="sxs-lookup"><span data-stu-id="95dcc-139">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="95dcc-140">可以使用相同的抓取手势来操纵不同距离的对象。</span><span class="sxs-lookup"><span data-stu-id="95dcc-140">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="95dcc-141">射线的调用是自动的，并且基于邻近度，如下所述：</span><span class="sxs-lookup"><span data-stu-id="95dcc-141">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="95dcc-142">![近操作](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-142">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="95dcc-143">**近操作**</span><span class="sxs-lookup"><span data-stu-id="95dcc-143">**Near manipulation**</span></span><br>
        <span data-ttu-id="95dcc-144">当对象在手臂长度范围（大约 50 cm）内时，射线会自动关闭，支持近距交互。</span><span class="sxs-lookup"><span data-stu-id="95dcc-144">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="95dcc-145">![远操作](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-145">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="95dcc-146">**远操作**</span><span class="sxs-lookup"><span data-stu-id="95dcc-146">**Far manipulation**</span></span><br>
        <span data-ttu-id="95dcc-147">当对象距离超过 50 cm 时，将启用射线。</span><span class="sxs-lookup"><span data-stu-id="95dcc-147">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="95dcc-148">转换应该顺利无缝。</span><span class="sxs-lookup"><span data-stu-id="95dcc-148">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="95dcc-149">2D 盖板交互</span><span class="sxs-lookup"><span data-stu-id="95dcc-149">2D slate interaction</span></span>

<span data-ttu-id="95dcc-150">2D 盖板是装有 Web 浏览器等 2D 应用内容的全息容器。</span><span class="sxs-lookup"><span data-stu-id="95dcc-150">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="95dcc-151">与 2D 平板电脑进行远距离交互的设计理念是使用手部射线进行瞄准，并隔空敲击以进行选择。</span><span class="sxs-lookup"><span data-stu-id="95dcc-151">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="95dcc-152">在用手部射线瞄准目标后，用户可以通过隔空敲击来触发超链接或按钮。</span><span class="sxs-lookup"><span data-stu-id="95dcc-152">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="95dcc-153">他们可以用一只手“隔空敲击并拖动”来上下滚动盖板内容。</span><span class="sxs-lookup"><span data-stu-id="95dcc-153">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="95dcc-154">使用两只手进行隔空敲击和拖动的相对运动可以放大和缩小平板电脑内容。</span><span class="sxs-lookup"><span data-stu-id="95dcc-154">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="95dcc-155">在角落和边缘处瞄准手部射线可显示最接近的可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="95dcc-155">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="95dcc-156">通过“抓取和拖动”操作视觉元素，用户可通过边角视觉元素执行统一的缩放，然后通过边缘视觉元素重排盖板。</span><span class="sxs-lookup"><span data-stu-id="95dcc-156">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="95dcc-157">用户可以通过抓取并拖动 2D 盖板顶部的全息条来移动整个盖板。</span><span class="sxs-lookup"><span data-stu-id="95dcc-157">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="95dcc-158">![2D 盖板交互单击](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-158">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="95dcc-159">**单击**</span><span class="sxs-lookup"><span data-stu-id="95dcc-159">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="95dcc-160">![2D 盖板交互滚动](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-160">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="95dcc-161">**滚动**</span><span class="sxs-lookup"><span data-stu-id="95dcc-161">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="95dcc-162">![2D 盖板交互缩放](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-162">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="95dcc-163">**缩放**</span><span class="sxs-lookup"><span data-stu-id="95dcc-163">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="95dcc-164">**操作 2D 盖板**</span><span class="sxs-lookup"><span data-stu-id="95dcc-164">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="95dcc-165">用户在角落或边缘处指向手部射线可显示最接近的可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="95dcc-165">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="95dcc-166">通过对视觉元素应用操作手势，用户可通过边角视觉元素执行统一的缩放，然后通过边缘视觉元素重排盖板。</span><span class="sxs-lookup"><span data-stu-id="95dcc-166">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="95dcc-167">通过在 2D 盖板顶部的全息条上应用操纵手势，用户可以移动整个盖板。</span><span class="sxs-lookup"><span data-stu-id="95dcc-167">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>


<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="95dcc-168">3D 对象操作</span><span class="sxs-lookup"><span data-stu-id="95dcc-168">3D object manipulation</span></span>

<span data-ttu-id="95dcc-169">在直接操作中，用户可以通过两种方式操纵 3D 对象：基于视觉元素的操作和非基于视觉元素的操作。</span><span class="sxs-lookup"><span data-stu-id="95dcc-169">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="95dcc-170">在指向和提交模型中，用户能够通过手部射线实现完全相同的任务。</span><span class="sxs-lookup"><span data-stu-id="95dcc-170">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="95dcc-171">不需要额外的学习。</span><span class="sxs-lookup"><span data-stu-id="95dcc-171">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="95dcc-172">基于可视操作元素的操作</span><span class="sxs-lookup"><span data-stu-id="95dcc-172">Affordance-based manipulation</span></span>
<span data-ttu-id="95dcc-173">用户使用手部射线指向并显示边框和可视操作元素。</span><span class="sxs-lookup"><span data-stu-id="95dcc-173">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="95dcc-174">用户可在边框上应用操作手势来移动整个对象，在边缘视觉元素上应用操作手势来旋转对象，以及在边角视觉元素上应用操作手势以进行统一的缩放。</span><span class="sxs-lookup"><span data-stu-id="95dcc-174">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="95dcc-175">![3D 对象操作远移动](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-175">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="95dcc-176">**移动**</span><span class="sxs-lookup"><span data-stu-id="95dcc-176">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="95dcc-177">![3D 对象操作远旋转](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-177">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="95dcc-178">**旋转**</span><span class="sxs-lookup"><span data-stu-id="95dcc-178">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="95dcc-179">![3D 对象操作远缩放](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-179">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="95dcc-180">**缩放**</span><span class="sxs-lookup"><span data-stu-id="95dcc-180">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="95dcc-181">不基于可视操作元素的操作</span><span class="sxs-lookup"><span data-stu-id="95dcc-181">Non-affordance based manipulation</span></span>
<span data-ttu-id="95dcc-182">用户用手部射线指向以显示边界框，然后直接对其应用操作手势。</span><span class="sxs-lookup"><span data-stu-id="95dcc-182">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="95dcc-183">如果用一只手进行操作，对象的平移和旋转将与手的移动和方向相关联。</span><span class="sxs-lookup"><span data-stu-id="95dcc-183">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="95dcc-184">如果用两只手进行操作，用户可以根据两只手的相对运动来平移、缩放和旋转对象。</span><span class="sxs-lookup"><span data-stu-id="95dcc-184">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="95dcc-185">本能手势</span><span class="sxs-lookup"><span data-stu-id="95dcc-185">Instinctual gestures</span></span>
<span data-ttu-id="95dcc-186">指向和提交的本能手势的概念类似于[用手直接操作](direct-manipulation.md)的概念。</span><span class="sxs-lookup"><span data-stu-id="95dcc-186">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="95dcc-187">用户在 3D 对象上执行的手势是由 UI 视觉元素的设计引导的。</span><span class="sxs-lookup"><span data-stu-id="95dcc-187">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="95dcc-188">例如，一个小的控制点可能会促使用户用拇指和食指捏，而用户可能想用所有 5 根手指抓一个较大的对象。</span><span class="sxs-lookup"><span data-stu-id="95dcc-188">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="95dcc-189">![本能手势远的小型对象](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-189">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="95dcc-190">**小型对象**</span><span class="sxs-lookup"><span data-stu-id="95dcc-190">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="95dcc-191">![本能手势远的中型对象](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-191">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="95dcc-192">**中型对象**</span><span class="sxs-lookup"><span data-stu-id="95dcc-192">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="95dcc-193">![本能手势远的大型对象](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-193">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="95dcc-194">**大型对象**</span><span class="sxs-lookup"><span data-stu-id="95dcc-194">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="95dcc-195">手部与 6 DoF 控制器之间的对称设计</span><span class="sxs-lookup"><span data-stu-id="95dcc-195">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="95dcc-196">远程交互的指向和提交概念最初是为混合现实门户 (MRP) 创建和定义的，在混合现实门户中，用户戴上沉浸式头戴显示设备，通过运动控制器与 3D 对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="95dcc-196">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="95dcc-197">运动控制器射出光线来指向和操纵远处的对象。</span><span class="sxs-lookup"><span data-stu-id="95dcc-197">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="95dcc-198">控制器上有用于进一步提交不同操作的按钮。</span><span class="sxs-lookup"><span data-stu-id="95dcc-198">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="95dcc-199">我们利用射线的交互模式，并将其与双手关联。</span><span class="sxs-lookup"><span data-stu-id="95dcc-199">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="95dcc-200">借助这种对称设计，熟悉 MRP 的用户在使用 HoloLen 2 时不需要学习另一种交互模式来进行远距离指向和操纵，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="95dcc-200">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="95dcc-201">![带控制器的射线的对称设计](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-201">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="95dcc-202">**控制器射线**</span><span class="sxs-lookup"><span data-stu-id="95dcc-202">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="95dcc-203">![带手的射线的对称设计](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="95dcc-203">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="95dcc-204">**手部射线**</span><span class="sxs-lookup"><span data-stu-id="95dcc-204">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="95dcc-205">Unity 的 MRTK（混合现实工具包）中的手部射线</span><span class="sxs-lookup"><span data-stu-id="95dcc-205">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="95dcc-206">默认情况下，MRTK 提供一个手部射线 prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers))，其视觉状态与 shell 的系统手部射线相同。</span><span class="sxs-lookup"><span data-stu-id="95dcc-206">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="95dcc-207">它分配在 MRTK 的输入配置文件的“指针”下。</span><span class="sxs-lookup"><span data-stu-id="95dcc-207">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="95dcc-208">在沉浸式头戴显示设备中，相同的射线会用于运动控制器。</span><span class="sxs-lookup"><span data-stu-id="95dcc-208">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="95dcc-209">MRTK - 指针配置文件</span><span class="sxs-lookup"><span data-stu-id="95dcc-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="95dcc-210">MRTK - 输入系统</span><span class="sxs-lookup"><span data-stu-id="95dcc-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="95dcc-211">MRTK - 指针</span><span class="sxs-lookup"><span data-stu-id="95dcc-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="95dcc-212">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95dcc-212">See also</span></span>
* [<span data-ttu-id="95dcc-213">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="95dcc-213">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="95dcc-214">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="95dcc-214">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="95dcc-215">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="95dcc-215">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="95dcc-216">手 - 手势</span><span class="sxs-lookup"><span data-stu-id="95dcc-216">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="95dcc-217">本能交互</span><span class="sxs-lookup"><span data-stu-id="95dcc-217">Instinctual interactions</span></span>](interaction-fundamentals.md)
