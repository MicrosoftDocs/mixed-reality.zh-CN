---
title: 点和提交
description: 点和提交输入模型概述
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: 混合现实，交互设计
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581307"
---
# <a name="point-and-commit"></a><span data-ttu-id="e6eb7-104">点和提交</span><span class="sxs-lookup"><span data-stu-id="e6eb7-104">Point and commit</span></span>
<span data-ttu-id="e6eb7-105">点和提交是输入的模型，用户可以为目标、 选择和操作 2D 内容和三维对象的距离。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-105">Point and commit is an input model enables users to target, select and manipulate 2D contents and 3D objects in a distance.</span></span> <span data-ttu-id="e6eb7-106">此"远处"交互方法是在它们与现实世界的日常交互期间当时的确没有人正在 navel 交互式体验。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-106">This "Far" interaction technique is a navel interactive experience that human being didn't really have during their daily interaction with the real world.</span></span> <span data-ttu-id="e6eb7-107">例如，在超级英雄电影，磁是能够联系和处理通过手中距离的延伸的范围对象的但用户不能执行此操作在现实中。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-107">For example, in a super hero movie, Magneto is capable of reaching out and manipulating a far object via hands in a distance, but human can't do it in reality.</span></span> <span data-ttu-id="e6eb7-108">在 Microsoft HoloLens (AR) 和 Microsoft 混合现实 (VR) 中，我们做用户这神奇的能力，重大的不只是为了重新燃烧全息版的内容，但若要使交互更高效现实世界的物理约束和高效。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-108">In both Microsoft HoloLens (AR) and Microsoft Mixed Reality (VR), we equip users this magical power, breaking the physical constraint of real world not only to have delightful experience with holographic contents but to make the interaction more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="e6eb7-109">设备支持</span><span class="sxs-lookup"><span data-stu-id="e6eb7-109">Device support</span></span>
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e6eb7-110"><strong>输入的模型</strong></span><span class="sxs-lookup"><span data-stu-id="e6eb7-110"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="e6eb7-111"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="e6eb7-111"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e6eb7-112"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e6eb7-112"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e6eb7-113"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></span><span class="sxs-lookup"><span data-stu-id="e6eb7-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e6eb7-114">点和提交 （最手动交互）</span><span class="sxs-lookup"><span data-stu-id="e6eb7-114">Point and commit (far hand interaction)</span></span></td>
        <td><span data-ttu-id="e6eb7-115">不支持的 ❌</span><span class="sxs-lookup"><span data-stu-id="e6eb7-115">❌ Not supported</span></span></td>
        <td><span data-ttu-id="e6eb7-116">✔️ 建议</span><span class="sxs-lookup"><span data-stu-id="e6eb7-116">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="e6eb7-117">✔️ 建议</span><span class="sxs-lookup"><span data-stu-id="e6eb7-117">✔️ Recommended</span></span></td>
    </tr>
</table>
<br>
<span data-ttu-id="e6eb7-118">点和提交已在 HoloLens 2 上，利用新的明确的手跟踪系统的主要输入模型之一。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-118">Point and commit has been one of the primary input models on HoloLens 2, utilizing the new articulated hand tracking system.</span></span> <span data-ttu-id="e6eb7-119">此输入的模型也是在通过动作控制器使用的沉浸式耳机主输入的模型。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-119">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span> <span data-ttu-id="e6eb7-120">点和提交是我们建议将 Head 注视输入的模型，在 HoloLens 上提交 （第 1 代）。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-120">Point and Commit is the input model that we suggest to replace the Head Gaze and Commit on HoloLens (1st gen).</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="e6eb7-121">手大气</span><span class="sxs-lookup"><span data-stu-id="e6eb7-121">Hand rays</span></span>
<span data-ttu-id="e6eb7-122">在 HoloLens 2 上，我们创建手射线从 palm 中心排除。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-122">On HoloLens 2, we create a hand ray shooting out from the center of a palm.</span></span> <span data-ttu-id="e6eb7-123">Ray 将被视为手形图标的扩展。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-123">The ray is treated as an extension of the hand.</span></span> <span data-ttu-id="e6eb7-124">圆环图形状光标被附加暗示 hitted 对象与射线相交的位置的射线的末尾。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-124">A donut shape cursor is attached at the end of the ray to imply the location where the ray intersects with a hitted object.</span></span> <span data-ttu-id="e6eb7-125">光标进入的对象将手中接收动作命令。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-125">The object that the cursor lands will receive gestural commands from the hand.</span></span> 

<span data-ttu-id="e6eb7-126">通过使用拇指和食指来执行以无线方式点击动作触发非常基本的动作命令。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-126">The very basic gestural command is triggered by using thumb and index finger to perform air tap gesture.</span></span> <span data-ttu-id="e6eb7-127">通过使用手形 ray 可以指向和提交空敲击，用户可以激活的按钮或 web 内容上的超链接。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-127">By using hand ray to point and air tap to commit, users can activate a button or a hyperlink on a web content.</span></span> <span data-ttu-id="e6eb7-128">使用多个复合手势，用户都能够导航 web 内容和操作三维对象的距离。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-128">With more composite gestures, users are capable of navigating the web content and manipulating 3D objects in a distance.</span></span> <span data-ttu-id="e6eb7-129">手 ray 的可视设计还应该响应可以指向和提交状态：</span><span class="sxs-lookup"><span data-stu-id="e6eb7-129">The visual design of the hand ray should also react to point and commit states:</span></span> <br>
* <span data-ttu-id="e6eb7-130">在指针的状态中，ray 是内联，短划线和光标是圆环图形状。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-130">In the pointing state, the ray is dash lined, and the cursor is a donut shape.</span></span>
* <span data-ttu-id="e6eb7-131">在提交状态，ray 将转变为一条实线，和光标缩小为一个点。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-131">in the committing state, the ray turns into a solid line, and the cursor shrinks to a dot.</span></span><br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a><span data-ttu-id="e6eb7-132">近和远之间进行转换</span><span class="sxs-lookup"><span data-stu-id="e6eb7-132">Transition between near and far</span></span>
<span data-ttu-id="e6eb7-133">而不是使用特定手势，如使用索引手指离开屏幕直接射线，指向我们设计推出 palm，中心的射线释放和保留五个手指的动作的更多操作。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-133">Instead of using specific gestures, such as pointing with index finger to direct the ray, we design the ray coming out from the center of the palm, releasing and reserving the five fingers for more gestural manipulations.</span></span> <span data-ttu-id="e6eb7-134">因此，HoloLens 2 支持一组完全相同的手势的近和远交互。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-134">Therefore, HoloLens 2 supports exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="e6eb7-135">任何其他学习不需要时用户传输从靠近远端交互，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-135">No additional learning is needed when users transit from near to far interactions, and vice versa.</span></span> <span data-ttu-id="e6eb7-136">用户可以使用相同的握手势来处理不同距离处的对象。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-136">Users can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="e6eb7-137">射线的调用是自动和邻近基于：</span><span class="sxs-lookup"><span data-stu-id="e6eb7-137">The invocation of the rays is automatic and proximity based:</span></span> <br>
* <span data-ttu-id="e6eb7-138">在 arm 达到距离 (大约 50 cm) 对象时，将关闭射线自动鼓励近交互。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-138">when an object is within arm reached distance (roughly 50 cm), the rays are turned off automatically encouraging for near interaction.</span></span> 
* <span data-ttu-id="e6eb7-139">比 50 cm 对象时，会启用射线。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-139">When the object is farther than 50 cm, the rays are turned on.</span></span>

<span data-ttu-id="e6eb7-140">此机制可以顺畅、 无缝的过渡。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-140">This mechanism makes the transition smooth and seamless.</span></span><br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a><span data-ttu-id="e6eb7-141">2D 盖板交互</span><span class="sxs-lookup"><span data-stu-id="e6eb7-141">2D slate interaction</span></span>
<span data-ttu-id="e6eb7-142">2D 盖板是 holographic 容器托管 2D 应用内容，如 web 浏览器。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-142">A 2D slate is a holographic container hosting 2D app contents, such as web browser.</span></span> <span data-ttu-id="e6eb7-143">目前与 2D 平板式交互的设计概念是使用手大气点并敲击提交。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-143">The design concept for far interacting with a 2D slate is to use hand rays to point and air tap to commit.</span></span><br>

<span data-ttu-id="e6eb7-144">用来与盖板固定的交互：</span><span class="sxs-lookup"><span data-stu-id="e6eb7-144">For interacting with the slate contant:</span></span><br>

* <span data-ttu-id="e6eb7-145">用户可以指向一个超链接或按钮，然后敲击来激活它。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-145">Users can point at a hyperlink or a button, then air tap to activate it.</span></span> 
* <span data-ttu-id="e6eb7-146">用户可以使用一只手来执行导航笔势向上和向下滚动静态内容。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-146">Users can use one hand to perform a navigation gesture to scroll a slate content up and down.</span></span> 
* <span data-ttu-id="e6eb7-147">用户可以使用两只手来执行导航笔势来缩放和静态内容输出。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-147">Users can use two hands to perform navigation gestures to zoom in and out the slate content.</span></span><br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

<span data-ttu-id="e6eb7-148">用于操作 2D 平板本身：</span><span class="sxs-lookup"><span data-stu-id="e6eb7-148">For manipulating the 2D slate itself:</span></span><br>

* <span data-ttu-id="e6eb7-149">用户点的角部或边缘以显示最近操作功能可见性： 在手射线。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-149">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="e6eb7-150">通过功能可见性： 在应用操作手势，用户可以执行角功能可见性： 通过统一缩放和可以重排通过边缘功能可见性： 静态图像。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-150">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="e6eb7-151">通过在顶部的 2D 盖板 holobar 上应用操作手势，用户可以移动整个静态图像。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-151">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the whole slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="e6eb7-152">三维对象操作</span><span class="sxs-lookup"><span data-stu-id="e6eb7-152">3D object manipulation</span></span>
<span data-ttu-id="e6eb7-153">在直接操作，有两种用户操作三维对象功能可见性： 基于操作和非 affordnace 基于操作的方法。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-153">In direct manipulation, there are two ways for users to manipulate 3D object, Affordance Based Manipulation and Non-affordnace Based Manipulation.</span></span> <span data-ttu-id="e6eb7-154">在点和提交模型中，用户都是可达到手大气通过相同的任务。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-154">In point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="e6eb7-155">不需要使用任何其他学习。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-155">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="e6eb7-156">功能可见性： 基于操作</span><span class="sxs-lookup"><span data-stu-id="e6eb7-156">Affordance based manipulation</span></span>
<span data-ttu-id="e6eb7-157">用户使用手大气进行点，并且显示边界框和操作提供。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-157">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="e6eb7-158">要移动整个对象的边界框、 边缘等旋转和上，用户可以应用操作手势 coner 均匀缩放的提示。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-158">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate and on the coner affordances to scale uniformly.</span></span> <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="e6eb7-159">非功能可见性： 基于操作</span><span class="sxs-lookup"><span data-stu-id="e6eb7-159">Non-affordance based manipulation</span></span>
<span data-ttu-id="e6eb7-160">用手大气显示边界框，然后直接对其应用操作手势指向用户。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-160">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="e6eb7-161">用一只手平移和旋转的对象将关联到动作和方向的分值。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-161">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="e6eb7-162">使用两只手，用户可以转换、 缩放和旋转根据相对两只手的动作。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-162">With two hands, users can translate, scale and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gesturers"></a><span data-ttu-id="e6eb7-163">Instinctual gesturers</span><span class="sxs-lookup"><span data-stu-id="e6eb7-163">Instinctual gesturers</span></span>
<span data-ttu-id="e6eb7-164">点和提交 instinctual 手势的概念是与同步，以便直接进行操作。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-164">The concept of instinctual gestures for point and commit is in sync with that for direct manipulation.</span></span> <span data-ttu-id="e6eb7-165">三维对象上执行笔势用户假设是引导式的设计的 UI 提示。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-165">What gestures users suppose to perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="e6eb7-166">小控制点将激励用户捏合用拇指和食指，虽然大型对象使用户能够使用 5 个手指抓住。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-166">A small control point would motivate users to pinch with thumb and index finger, while a large object makes users to grab with 5 finger.</span></span>

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="e6eb7-167">手和 6 DoF 控制器之间的对称设计</span><span class="sxs-lookup"><span data-stu-id="e6eb7-167">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="e6eb7-168">首先创建并定义为混合现实门户 (MRP)，其中用户 wear 沉浸式头戴式和 3d 物体运动控制器通过与之交互的远端交互点和提交模型的概念。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-168">The concept of point and commit model for far interaction is firstly created and defined for the Mixed Reality Portal (MRP), where users wear an immersive headset and interact with the 3d object via motion controllers.</span></span> <span data-ttu-id="e6eb7-169">运动控制器投篮机会控制在出大气指向和操作延伸的范围对象。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-169">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="e6eb7-170">为进一步提交不同功能在控制器上有一些按钮。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-170">There are buttons on the controllers for further committing different functionalities.</span></span> <span data-ttu-id="e6eb7-171">我们利用大气的交互模型，并将其附加两只手上。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-171">We leverage the interaction model of rays and attach them on both hands.</span></span> <span data-ttu-id="e6eb7-172">使用此对称设计时，用户熟悉 MRP 用户无需了解得指向和首次使用 HoloLen 2 时的操作的另一个交互模型，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e6eb7-172">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation while first time using HoloLen 2, and vice versa.</span></span>    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a><span data-ttu-id="e6eb7-173">请参阅</span><span class="sxs-lookup"><span data-stu-id="e6eb7-173">See also</span></span>
* [<span data-ttu-id="e6eb7-174">视线移动和提交</span><span class="sxs-lookup"><span data-stu-id="e6eb7-174">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e6eb7-175">直接操作</span><span class="sxs-lookup"><span data-stu-id="e6eb7-175">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e6eb7-176">交互基础知识</span><span class="sxs-lookup"><span data-stu-id="e6eb7-176">Interaction fundamentals</span></span>](interaction-fundamentals.md)
