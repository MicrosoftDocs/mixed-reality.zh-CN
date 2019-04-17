---
title: 目标的视线移动
description: 用户能够针对他们想要进行交互，而不考虑输入模式的元素为基础构建的所有交互。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实、 提供注视、 视线移动目标交互，设计
ms.openlocfilehash: c3225e27331f8afcda65469eb84fe5470bf6ee8c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592085"
---
# <a name="gaze-targeting"></a><span data-ttu-id="75204-104">目标的视线移动</span><span class="sxs-lookup"><span data-stu-id="75204-104">Gaze targeting</span></span>

<span data-ttu-id="75204-105">用户能够针对他们想要进行交互，而不考虑输入模式的元素为基础构建的所有交互。</span><span class="sxs-lookup"><span data-stu-id="75204-105">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="75204-106">在 Windows Mixed Reality，通常这是使用用户的视线移动。</span><span class="sxs-lookup"><span data-stu-id="75204-106">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="75204-107">若要使用户能够成功使用体验，系统的计算的了解用户的意图和用户的实际目的，必须尽可能接近地对齐。</span><span class="sxs-lookup"><span data-stu-id="75204-107">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="75204-108">某种程度上，系统将解释用户的预期的操作正确，满意度增加和性能提高。</span><span class="sxs-lookup"><span data-stu-id="75204-108">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="75204-109">设备支持</span><span class="sxs-lookup"><span data-stu-id="75204-109">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="75204-110">功能</span><span class="sxs-lookup"><span data-stu-id="75204-110">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="75204-111"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="75204-111"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="75204-112">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="75204-112">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="75204-113"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="75204-113"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="75204-114">目标的视线移动</span><span class="sxs-lookup"><span data-stu-id="75204-114">Gaze targeting</span></span></td><td style="text-align: center;"> <span data-ttu-id="75204-115">✔️</span><span class="sxs-lookup"><span data-stu-id="75204-115">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="75204-116">✔️</span><span class="sxs-lookup"><span data-stu-id="75204-116">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="75204-117">✔️</span><span class="sxs-lookup"><span data-stu-id="75204-117">✔️</span></span> </td>
</tr><tr>
<td> <span data-ttu-id="75204-118">密切关注面向</span><span class="sxs-lookup"><span data-stu-id="75204-118">Eye targeting</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="75204-119">✔️</span><span class="sxs-lookup"><span data-stu-id="75204-119">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="75204-120">特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="75204-120">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="75204-121">目标大小调整和反馈</span><span class="sxs-lookup"><span data-stu-id="75204-121">Target sizing and feedback</span></span>

<span data-ttu-id="75204-122">视线移动矢量具有已重复显示可用于面向正常，但通常最适合总目标 （获取稍大些目标）。</span><span class="sxs-lookup"><span data-stu-id="75204-122">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="75204-123">1 到 1.5 度为单位的最小目标大小应在 3 个度的目标通常的速度更快，但在大多数情况下，允许用户成功操作。</span><span class="sxs-lookup"><span data-stu-id="75204-123">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="75204-124">请注意，用户目标实际上是三维元素-甚至的 2D 区域的大小无论投影面向它们应该是定目标区域。</span><span class="sxs-lookup"><span data-stu-id="75204-124">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="75204-125">提供一个元素是"活动"（该用户面向） 一些突出提示会非常有用-这可以包括处理，例如可见"悬停"效果、 音频突出显示或单击，或清除的元素的光标对齐方式。</span><span class="sxs-lookup"><span data-stu-id="75204-125">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="75204-126">![2 个计量距离处的最佳目标大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="75204-126">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="75204-127">*2 个计量距离处的最佳目标大小*</span><span class="sxs-lookup"><span data-stu-id="75204-127">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="75204-128">![突出显示的视线移动目标的对象的一个示例](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="75204-128">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="75204-129">*突出显示的视线移动目标的对象的一个示例*</span><span class="sxs-lookup"><span data-stu-id="75204-129">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="75204-130">目标位置</span><span class="sxs-lookup"><span data-stu-id="75204-130">Target placement</span></span>

<span data-ttu-id="75204-131">用户将通常无法天线的视野中, 找到很高或极低定位 UI 元素将重点放大部分其关注其主要焦点 （通常大约为水平视线） 周围的区域。</span><span class="sxs-lookup"><span data-stu-id="75204-131">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="75204-132">可帮助将大多数目标放入一些合理带围水平视线。</span><span class="sxs-lookup"><span data-stu-id="75204-132">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="75204-133">给定用户的情况下往往会将焦点置于将 UI 元素组合在一起的程度上它们从概念上讲相关一个相对较小可视区域上随时 （视觉 attentional 圆锥体约为 10 度），可以利用从关注链接行为项目到项目的用户将其提供注视转到区域。</span><span class="sxs-lookup"><span data-stu-id="75204-133">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="75204-134">在设计时用户界面，请记住在 HoloLens 和沉浸式耳机之间的字段的视图可能较大的变化。</span><span class="sxs-lookup"><span data-stu-id="75204-134">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="75204-135">![举例说明如何更轻松的视线移动 Galaxy 资源管理器中的目标的分组 UI 元素](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="75204-135">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="75204-136">*举例说明如何更轻松的视线移动 Galaxy 资源管理器中的目标的分组 UI 元素*</span><span class="sxs-lookup"><span data-stu-id="75204-136">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="75204-137">提高目标行为</span><span class="sxs-lookup"><span data-stu-id="75204-137">Improving targeting behaviors</span></span>

<span data-ttu-id="75204-138">如果用户的意图以面向内容可以是确定 （或近似密切），它可以接受"near miss"会尝试在交互，就好像它们已正确目标很有帮助。</span><span class="sxs-lookup"><span data-stu-id="75204-138">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="75204-139">有了一些可纳入混合的现实体验的成功方法：</span><span class="sxs-lookup"><span data-stu-id="75204-139">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="75204-140">提供注视稳定 ("重力 wells")</span><span class="sxs-lookup"><span data-stu-id="75204-140">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="75204-141">这应打开大多数/all 的时间。</span><span class="sxs-lookup"><span data-stu-id="75204-141">This should be turned on most/all of the time.</span></span> <span data-ttu-id="75204-142">此方法中删除用户可能有自然的 head 颈部 jit 编译器。</span><span class="sxs-lookup"><span data-stu-id="75204-142">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="75204-143">由于查找/谈到的行为也移动。</span><span class="sxs-lookup"><span data-stu-id="75204-143">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="75204-144">最接近链接算法</span><span class="sxs-lookup"><span data-stu-id="75204-144">Closest link algorithms</span></span>

<span data-ttu-id="75204-145">这些效果最佳稀疏的交互式内容与几个方面。</span><span class="sxs-lookup"><span data-stu-id="75204-145">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="75204-146">如果没有，您可以确定用户已尝试与之交互的可能性非常高，可以通过简单地假定某一级别的意图进行补充其目标的能力。</span><span class="sxs-lookup"><span data-stu-id="75204-146">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="75204-147">Backdating/postdating 操作</span><span class="sxs-lookup"><span data-stu-id="75204-147">Backdating/postdating actions</span></span>

<span data-ttu-id="75204-148">此机制可在需要速度的任务。</span><span class="sxs-lookup"><span data-stu-id="75204-148">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="75204-149">如果某个用户是通过一系列的目标/激活 maneuvers 速度移动，它可用于假定某些目的，并允许*丢失步骤*若要对其用户在具有焦点略有之前或之后的点击 （略有目标执行操作50 毫秒之前/之后为有效的早期测试）。</span><span class="sxs-lookup"><span data-stu-id="75204-149">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="75204-150">平滑处理</span><span class="sxs-lookup"><span data-stu-id="75204-150">Smoothing</span></span>

<span data-ttu-id="75204-151">此机制可用于的路径移动，减少由于自然磁头运动特征轻微抖动/原因。</span><span class="sxs-lookup"><span data-stu-id="75204-151">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="75204-152">通过路径动作，平滑大小/距离的移动而不是随着时间的推移通过平滑处理时</span><span class="sxs-lookup"><span data-stu-id="75204-152">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="75204-153">消除</span><span class="sxs-lookup"><span data-stu-id="75204-153">Magnetism</span></span>

<span data-ttu-id="75204-154">此机制可以看作"最靠近链接"算法的绘制光标向目标，或只需增加 hitboxes （无论是以可视方式还是不） 的更多常规版本用户达到可能的目标，如使用交互式布局与一些知识更好的方法用户的意图。</span><span class="sxs-lookup"><span data-stu-id="75204-154">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="75204-155">这可以是小型的目标对于特别有用。</span><span class="sxs-lookup"><span data-stu-id="75204-155">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="75204-156">焦点粘性</span><span class="sxs-lookup"><span data-stu-id="75204-156">Focus stickiness</span></span>

<span data-ttu-id="75204-157">在确定其附近的焦点转至交互式元素，提供对当前已设定焦点的元素偏移。</span><span class="sxs-lookup"><span data-stu-id="75204-157">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="75204-158">这将有助于减少不正常时浮点位于自然干扰的两个元素之间的中点的切换行为的焦点。</span><span class="sxs-lookup"><span data-stu-id="75204-158">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="75204-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="75204-159">See also</span></span>
* [<span data-ttu-id="75204-160">手势</span><span class="sxs-lookup"><span data-stu-id="75204-160">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="75204-161">语音设计</span><span class="sxs-lookup"><span data-stu-id="75204-161">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="75204-162">游标</span><span class="sxs-lookup"><span data-stu-id="75204-162">Cursors</span></span>](cursors.md)
