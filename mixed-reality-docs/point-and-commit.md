---
title: 点和提交模式以及实践
description: 点和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实，交互、 设计、 hololens、 手，到目前为止，点和提交
ms.openlocfilehash: e69c8ff2091beff7d8fbbde4e6f24d909302290a
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730805"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="9ef8e-104">点和提交模式以及实践</span><span class="sxs-lookup"><span data-stu-id="9ef8e-104">Point and commit with hands</span></span>
<span data-ttu-id="9ef8e-105">点和提交模式以及实践是输入的模型，使用户能够为目标、 选择和操作在距离 2D 内容和三维对象。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects in the distance.</span></span> <span data-ttu-id="9ef8e-106">此"得"交互方法仅适用于混合现实并不是方法人类自然地与现实世界的 intereact。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-106">This "far" interaction technique is unique to mixed reality and is not a way humans naturally intereact with the real world.</span></span> <span data-ttu-id="9ef8e-107">例如，在超级英雄电影*X 男士*，该字符[磁](https://en.wikipedia.org/wiki/Magneto_(comics))能够联系和操作中使用他的距离的延伸的范围对象。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-107">For example, in the super hero movie *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="9ef8e-108">这不是人类可以在现实中做的事情。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="9ef8e-109">在 HoloLens (AR) 和混合现实 (VR) 中，我们做这神奇功能强大、 用户重大不仅可以具有很不一般吧体验 holographic 内容而且也更有效且高效进行交互的实际的物理约束。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-109">In both HoloLens (AR) and Mixed Reality (VR), we equip users with this magical power, breaking the physical constraint of the real world not only to have a delightful experience with holographic contents but also to make the interaction more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="9ef8e-110">设备支持</span><span class="sxs-lookup"><span data-stu-id="9ef8e-110">Device support</span></span>

<span data-ttu-id="9ef8e-111">输入的模型</span><span class="sxs-lookup"><span data-stu-id="9ef8e-111">Input model</span></span> | [<span data-ttu-id="9ef8e-112">HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="9ef8e-112">HoloLens (1st gen)</span></span>](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | <span data-ttu-id="9ef8e-113">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9ef8e-113">HoloLens 2</span></span> | [<span data-ttu-id="9ef8e-114">沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="9ef8e-114">Immersive headsets</span></span>](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
<span data-ttu-id="9ef8e-115">点和提交 （最手动交互）</span><span class="sxs-lookup"><span data-stu-id="9ef8e-115">Point and commit (far hand interaction)</span></span> | <span data-ttu-id="9ef8e-116">不支持的 ❌</span><span class="sxs-lookup"><span data-stu-id="9ef8e-116">❌ Not supported</span></span> | <span data-ttu-id="9ef8e-117">✔️ 建议</span><span class="sxs-lookup"><span data-stu-id="9ef8e-117">✔️ Recommended</span></span> | <span data-ttu-id="9ef8e-118">✔️ 建议</span><span class="sxs-lookup"><span data-stu-id="9ef8e-118">✔️ Recommended</span></span>

<span data-ttu-id="9ef8e-119">点和提交，也称为手到目前为止，是利用新的明确的手动跟踪系统的新功能之一。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-119">Point and commit, also known as hands far, is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="9ef8e-120">此输入的模型也是在通过动作控制器使用的沉浸式耳机主输入的模型。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

## <a name="hand-rays"></a><span data-ttu-id="9ef8e-121">手大气</span><span class="sxs-lookup"><span data-stu-id="9ef8e-121">Hand rays</span></span>

<span data-ttu-id="9ef8e-122">在 HoloLens 2 上，我们将创建从中心 palm 投篮手 ray。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-122">On HoloLens 2, we created a hand ray that shoots out from the center of a palm.</span></span> <span data-ttu-id="9ef8e-123">此 ray 视为手形图标的扩展。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="9ef8e-124">圆环图形光标被附加到以指示目标对象与射线相交的位置的射线的末尾。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="9ef8e-125">光标进入的对象然后可以从手接收动作命令。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="9ef8e-126">通过使用拇指和食指来执行以无线方式点击操作触发此基本动作命令。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="9ef8e-127">通过使用手形 ray 可以指向和提交空敲击，用户可以激活的按钮或 web 内容上的超链接。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink on a web content.</span></span> <span data-ttu-id="9ef8e-128">使用多个复合手势，用户都能够导航 web 内容和操作三维对象一段距离。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="9ef8e-129">手 ray 的可视设计应还应对这些点和提交的状态，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9ef8e-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

* <span data-ttu-id="9ef8e-130">在中*指向*状态下，ray 是虚线，光标位于圆环图形状。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-130">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
* <span data-ttu-id="9ef8e-131">在中*提交*状态下，ray 将转变为一条实线，光标将缩小到一个点。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-131">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a><span data-ttu-id="9ef8e-132">近和远之间进行转换</span><span class="sxs-lookup"><span data-stu-id="9ef8e-132">Transition between near and far</span></span>

<span data-ttu-id="9ef8e-133">而不是使用特定手势，如"使用食指指向"若要指示射线，我们设计出从中心的手掌，释放并保留五个手指的多个操控手势，如捏合而获取的射线。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-133">Instead of using specific gesture, such as "pointing with index finger" to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="9ef8e-134">与此设计中，我们创建一个心理模型，支持一组完全相同的手势的近和远交互。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-134">With this design, we create only one mental model, supporting exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="9ef8e-135">可以使用相同随取即行手势来处理不同距离处的对象。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-135">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="9ef8e-136">射线的调用是自动和邻近基于：</span><span class="sxs-lookup"><span data-stu-id="9ef8e-136">The invocation of the rays is automatic and proximity based:</span></span>

*  <span data-ttu-id="9ef8e-137">在 arm 达到距离 (大约 50 cm) 对象时，将关闭射线自动鼓励近交互。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-137">When an object is within arm reached distance (roughly 50 cm), the rays are turned off automatically encouraging for near interaction.</span></span>
*  <span data-ttu-id="9ef8e-138">比 50 cm 对象时，会启用射线。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-138">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="9ef8e-139">转换应顺畅、 无缝。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-139">The transition should be smooth and seamless.</span></span>

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a><span data-ttu-id="9ef8e-140">2D 盖板交互</span><span class="sxs-lookup"><span data-stu-id="9ef8e-140">2D slate interaction</span></span>

<span data-ttu-id="9ef8e-141">2D 盖板是 holographic 容器托管 2D 应用内容，如 web 浏览器。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-141">A 2D Slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="9ef8e-142">目前与 2D 平板式交互的设计概念是使用手大气目标和 air 点击选择。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-142">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="9ef8e-143">面向使用手 ray 之后, 用户可以隔空敲击触发超链接或按钮。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-143">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="9ef8e-144">他们可以使用一只手"空中点击和拖动"向上和向下滚动静态内容。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-144">They can use one hand to "air tap and drag" to scroll a slate content up and down.</span></span> <span data-ttu-id="9ef8e-145">使用两只手空中点击和拖动的相对动作可以放大 in 和 out 静态内容。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-145">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="9ef8e-146">面向手动射线边角上的显示最接近功能操作可见性:。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-146">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="9ef8e-147">通过"随取即行并将"操作等，用户可以执行统一缩放通过角提示和可以重排通过边缘提供静态图像。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-147">By "grab and drag" the manipulation affordances, users can perform uniform scaling through the corner affordances and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="9ef8e-148">获取和拖动在 2D 静态图像的顶部 holobar 用户可以移动整个静态图像。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-148">Grabbing and dragging the holobar at the top of the 2D slate can users move the whole slate.</span></span>

![](images/2D-Slate-Interaction-Far-720px.jpg)

<span data-ttu-id="9ef8e-149">用于操作 2D 平板本身：</span><span class="sxs-lookup"><span data-stu-id="9ef8e-149">For manipulating the 2D slate itself:</span></span><br>

* <span data-ttu-id="9ef8e-150">用户点的角部或边缘以显示最近操作功能可见性： 在手射线。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-150">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="9ef8e-151">通过功能可见性： 在应用操作手势，用户可以执行角功能可见性： 通过统一缩放和可以重排通过边缘功能可见性： 静态图像。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-151">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="9ef8e-152">通过在顶部的 2D 盖板 holobar 上应用操作手势，用户可以移动整个静态图像。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-152">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the whole slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="9ef8e-153">三维对象操作</span><span class="sxs-lookup"><span data-stu-id="9ef8e-153">3D object manipulation</span></span>

<span data-ttu-id="9ef8e-154">在直接操作，有两种用户操作三维对象、 功能可见性： 基于操作和非功能可见性： 基于的操作的方法。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-154">In direct manipulation, there are two ways for users to manipulate 3D object, affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="9ef8e-155">在点和提交模型中，用户都是可达到手大气通过相同的任务。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-155">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="9ef8e-156">不需要使用任何其他学习。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-156">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="9ef8e-157">基于功能可见性： 的操作</span><span class="sxs-lookup"><span data-stu-id="9ef8e-157">Affordance-based manipulation</span></span>
<span data-ttu-id="9ef8e-158">用户使用手大气进行点，并且显示边界框和操作提供。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-158">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="9ef8e-159">要移动整个对象的边界框、 边缘等旋转和上，用户可以应用操作手势 coner 均匀缩放的提示。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-159">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate and on the coner affordances to scale uniformly.</span></span> <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="9ef8e-160">非功能可见性： 基于操作</span><span class="sxs-lookup"><span data-stu-id="9ef8e-160">Non-affordance based manipulation</span></span>
<span data-ttu-id="9ef8e-161">用手大气显示边界框，然后直接对其应用操作手势指向用户。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-161">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="9ef8e-162">用一只手平移和旋转的对象将关联到动作和方向的分值。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-162">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="9ef8e-163">使用两只手，用户可以转换、 缩放和旋转根据相对两只手的动作。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-163">With two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gesturers"></a><span data-ttu-id="9ef8e-164">Instinctual gesturers</span><span class="sxs-lookup"><span data-stu-id="9ef8e-164">Instinctual gesturers</span></span>
<span data-ttu-id="9ef8e-165">点和提交 instinctual 手势的概念是类似于直接操作。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-165">The concept of instinctual gestures for point and commit is similar to that for direct manipulation.</span></span> <span data-ttu-id="9ef8e-166">设计的 UI 提示将指导用户是假设三维对象上执行的笔势。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-166">The gestures users are suppose to perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="9ef8e-167">例如，一个小的控制点可能激励用户捏合用其拇指和食指，而用户可能想要获取使用所有 5 个手指的较大对象。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-167">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all 5 fingers.</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="9ef8e-168">手和 6 DoF 控制器之间的对称设计</span><span class="sxs-lookup"><span data-stu-id="9ef8e-168">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="9ef8e-169">最初，点和提交远端交互的概念已创建并定义为混合现实门户 (MRP)，其中用户戴沉浸式头戴式耳机，并与通过动作控制器三维对象进行交互。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-169">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP), where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="9ef8e-170">运动控制器投篮机会控制在出大气指向和操作延伸的范围对象。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-170">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="9ef8e-171">为进一步提交不同的操作在控制器上有一些按钮。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-171">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="9ef8e-172">我们利用大气的交互模型，并附加到两只手。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-172">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="9ef8e-173">使用此对称设计时，用户熟悉 MRP 用户无需了解得指向和操作的另一个交互模型，在使用 HoloLen 2 时，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="9ef8e-173">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a><span data-ttu-id="9ef8e-174">Instinctual 手势</span><span class="sxs-lookup"><span data-stu-id="9ef8e-174">Instinctual gestures</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a><span data-ttu-id="9ef8e-175">请参阅</span><span class="sxs-lookup"><span data-stu-id="9ef8e-175">See also</span></span>
* [<span data-ttu-id="9ef8e-176">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="9ef8e-176">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="9ef8e-177">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="9ef8e-177">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9ef8e-178">本能交互</span><span class="sxs-lookup"><span data-stu-id="9ef8e-178">Instinctual interactions</span></span>](interaction-fundamentals.md)

