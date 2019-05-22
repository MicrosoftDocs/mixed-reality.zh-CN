---
title: 目标的视线移动
description: 用户能够针对他们想要进行交互，而不考虑输入模式的元素为基础构建的所有交互。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实、 提供注视、 视线移动目标交互，设计
ms.openlocfilehash: bbacf9bc0039280b9944f2ad6616108d9ceae1cd
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974915"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="e6404-104">视线移动和停留</span><span class="sxs-lookup"><span data-stu-id="e6404-104">Gaze and dwell</span></span>
<span data-ttu-id="e6404-105">有很多不同的方式，以确认_提交_如结合使用的视线移动_语音_或_传递手势_。</span><span class="sxs-lookup"><span data-stu-id="e6404-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="e6404-106">有几种用户方案，在其中的用户的手可能正忙或无法跟踪 （例如，使用过大的重型手套工厂工作进程）。</span><span class="sxs-lookup"><span data-stu-id="e6404-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="e6404-107">语音输入可能也不可用，因为用户首选项、 社交上下文或嘈杂的环境。</span><span class="sxs-lookup"><span data-stu-id="e6404-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="e6404-108">另一种作为回退解决方案来执行_提交_是只需保留盯住 UI 元素，我们称之为_会仔细斟酌_。</span><span class="sxs-lookup"><span data-stu-id="e6404-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="e6404-109">一个_会仔细斟酌_头或关注的视线移动就可以执行。</span><span class="sxs-lookup"><span data-stu-id="e6404-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="e6404-110">其思路很简单，可以在以下几个阶段中细分：</span><span class="sxs-lookup"><span data-stu-id="e6404-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="e6404-111">用户启动 holographic 按钮在观望</span><span class="sxs-lookup"><span data-stu-id="e6404-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="e6404-112">简要开始延迟 （例如，150 毫秒） 后启动一些可视反馈的动画。</span><span class="sxs-lookup"><span data-stu-id="e6404-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="e6404-113">用于开始延迟用于避免庞大用户的方法是立即弹出反馈的时间。</span><span class="sxs-lookup"><span data-stu-id="e6404-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="e6404-114">有关_关注的视线移动_，我们建议以下视觉对象的设计会仔细斟酌反馈：</span><span class="sxs-lookup"><span data-stu-id="e6404-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="e6404-115">**其混合**:顺利 blend 中几乎不能看到在第一次完全不透明的反馈。</span><span class="sxs-lookup"><span data-stu-id="e6404-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="e6404-116">这使得反馈更少的分散注意力和 overwhleming，并可以很好地符合系统具有用户真正想要与此按钮的置信度。</span><span class="sxs-lookup"><span data-stu-id="e6404-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="e6404-117">**拉入**:创建可视反馈，不是减小大小，并将移至目标，提取用户的 visual 注意力的中心。</span><span class="sxs-lookup"><span data-stu-id="e6404-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="e6404-118">预定义的停留时间段 （例如，800 毫秒） 后停留完成并触发关联的事件。</span><span class="sxs-lookup"><span data-stu-id="e6404-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="e6404-119">提供一些正在最后完成听觉或可视反馈，以真正使主页的项有现在选择。</span><span class="sxs-lookup"><span data-stu-id="e6404-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![在此再次详述状态](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="e6404-121">目标的视线移动</span><span class="sxs-lookup"><span data-stu-id="e6404-121">Gaze targeting</span></span>

<span data-ttu-id="e6404-122">用户能够针对他们想要进行交互，而不考虑输入模式的元素为基础构建的所有交互。</span><span class="sxs-lookup"><span data-stu-id="e6404-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="e6404-123">在 Windows Mixed Reality，通常这是使用用户的视线移动。</span><span class="sxs-lookup"><span data-stu-id="e6404-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="e6404-124">若要使用户能够成功使用体验，系统的计算的了解用户的意图和用户的实际目的，必须尽可能接近地对齐。</span><span class="sxs-lookup"><span data-stu-id="e6404-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="e6404-125">某种程度上，系统将解释用户的预期的操作正确，满意度增加和性能提高。</span><span class="sxs-lookup"><span data-stu-id="e6404-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="e6404-126">设备支持</span><span class="sxs-lookup"><span data-stu-id="e6404-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e6404-127">功能</span><span class="sxs-lookup"><span data-stu-id="e6404-127">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="e6404-128"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="e6404-128"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="e6404-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e6404-129">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="e6404-130"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="e6404-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e6404-131">目标的视线移动</span><span class="sxs-lookup"><span data-stu-id="e6404-131">Gaze targeting</span></span></td><td style="text-align: center;"> <span data-ttu-id="e6404-132">✔️</span><span class="sxs-lookup"><span data-stu-id="e6404-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e6404-133">✔️</span><span class="sxs-lookup"><span data-stu-id="e6404-133">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="e6404-134">✔️</span><span class="sxs-lookup"><span data-stu-id="e6404-134">✔️</span></span> </td>
</tr><tr>
<td> <span data-ttu-id="e6404-135">密切关注面向</span><span class="sxs-lookup"><span data-stu-id="e6404-135">Eye targeting</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="e6404-136">✔️</span><span class="sxs-lookup"><span data-stu-id="e6404-136">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="e6404-137">特定于 HoloLens 2 的更多指导[即将推出](index.md)。</span><span class="sxs-lookup"><span data-stu-id="e6404-137">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="e6404-138">目标大小调整和反馈</span><span class="sxs-lookup"><span data-stu-id="e6404-138">Target sizing and feedback</span></span>

<span data-ttu-id="e6404-139">视线移动矢量具有已重复显示可用于面向正常，但通常最适合总目标 （获取稍大些目标）。</span><span class="sxs-lookup"><span data-stu-id="e6404-139">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="e6404-140">1 到 1.5 度为单位的最小目标大小应在 3 个度的目标通常的速度更快，但在大多数情况下，允许用户成功操作。</span><span class="sxs-lookup"><span data-stu-id="e6404-140">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="e6404-141">请注意，用户目标实际上是三维元素-甚至的 2D 区域的大小无论投影面向它们应该是定目标区域。</span><span class="sxs-lookup"><span data-stu-id="e6404-141">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="e6404-142">提供一个元素是"活动"（该用户面向） 一些突出提示会非常有用-这可以包括处理，例如可见"悬停"效果、 音频突出显示或单击，或清除的元素的光标对齐方式。</span><span class="sxs-lookup"><span data-stu-id="e6404-142">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="e6404-143">![2 个计量距离处的最佳目标大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e6404-143">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="e6404-144">*2 个计量距离处的最佳目标大小*</span><span class="sxs-lookup"><span data-stu-id="e6404-144">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="e6404-145">![突出显示的视线移动目标的对象的一个示例](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e6404-145">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="e6404-146">*突出显示的视线移动目标的对象的一个示例*</span><span class="sxs-lookup"><span data-stu-id="e6404-146">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="e6404-147">目标位置</span><span class="sxs-lookup"><span data-stu-id="e6404-147">Target placement</span></span>

<span data-ttu-id="e6404-148">用户将通常无法天线的视野中, 找到很高或极低定位 UI 元素将重点放大部分其关注其主要焦点 （通常大约为水平视线） 周围的区域。</span><span class="sxs-lookup"><span data-stu-id="e6404-148">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="e6404-149">可帮助将大多数目标放入一些合理带围水平视线。</span><span class="sxs-lookup"><span data-stu-id="e6404-149">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="e6404-150">给定用户的情况下往往会将焦点置于将 UI 元素组合在一起的程度上它们从概念上讲相关一个相对较小可视区域上随时 （视觉 attentional 圆锥体约为 10 度），可以利用从关注链接行为项目到项目的用户将其提供注视转到区域。</span><span class="sxs-lookup"><span data-stu-id="e6404-150">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="e6404-151">在设计时用户界面，请记住在 HoloLens 和沉浸式耳机之间的字段的视图可能较大的变化。</span><span class="sxs-lookup"><span data-stu-id="e6404-151">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="e6404-152">![举例说明如何更轻松的视线移动 Galaxy 资源管理器中的目标的分组 UI 元素](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e6404-152">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="e6404-153">*举例说明如何更轻松的视线移动 Galaxy 资源管理器中的目标的分组 UI 元素*</span><span class="sxs-lookup"><span data-stu-id="e6404-153">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="e6404-154">提高目标行为</span><span class="sxs-lookup"><span data-stu-id="e6404-154">Improving targeting behaviors</span></span>

<span data-ttu-id="e6404-155">如果用户的意图以面向内容可以是确定 （或近似密切），它可以接受"near miss"会尝试在交互，就好像它们已正确目标很有帮助。</span><span class="sxs-lookup"><span data-stu-id="e6404-155">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="e6404-156">有了一些可纳入混合的现实体验的成功方法：</span><span class="sxs-lookup"><span data-stu-id="e6404-156">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="e6404-157">提供注视稳定 ("重力 wells")</span><span class="sxs-lookup"><span data-stu-id="e6404-157">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="e6404-158">这应打开大多数/all 的时间。</span><span class="sxs-lookup"><span data-stu-id="e6404-158">This should be turned on most/all of the time.</span></span> <span data-ttu-id="e6404-159">此方法中删除用户可能有自然的 head 颈部 jit 编译器。</span><span class="sxs-lookup"><span data-stu-id="e6404-159">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="e6404-160">由于查找/谈到的行为也移动。</span><span class="sxs-lookup"><span data-stu-id="e6404-160">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="e6404-161">最接近链接算法</span><span class="sxs-lookup"><span data-stu-id="e6404-161">Closest link algorithms</span></span>

<span data-ttu-id="e6404-162">这些效果最佳稀疏的交互式内容与几个方面。</span><span class="sxs-lookup"><span data-stu-id="e6404-162">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="e6404-163">如果没有，您可以确定用户已尝试与之交互的可能性非常高，可以通过简单地假定某一级别的意图进行补充其目标的能力。</span><span class="sxs-lookup"><span data-stu-id="e6404-163">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="e6404-164">Backdating/postdating 操作</span><span class="sxs-lookup"><span data-stu-id="e6404-164">Backdating/postdating actions</span></span>

<span data-ttu-id="e6404-165">此机制可在需要速度的任务。</span><span class="sxs-lookup"><span data-stu-id="e6404-165">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="e6404-166">如果某个用户是通过一系列的目标/激活 maneuvers 速度移动，它可用于假定某些目的，并允许*丢失步骤*若要对其用户在具有焦点略有之前或之后的点击 （略有目标执行操作50 毫秒之前/之后为有效的早期测试）。</span><span class="sxs-lookup"><span data-stu-id="e6404-166">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="e6404-167">平滑处理</span><span class="sxs-lookup"><span data-stu-id="e6404-167">Smoothing</span></span>

<span data-ttu-id="e6404-168">此机制可用于的路径移动，减少由于自然磁头运动特征轻微抖动/原因。</span><span class="sxs-lookup"><span data-stu-id="e6404-168">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="e6404-169">通过路径动作，平滑大小/距离的移动而不是随着时间的推移通过平滑处理时</span><span class="sxs-lookup"><span data-stu-id="e6404-169">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="e6404-170">消除</span><span class="sxs-lookup"><span data-stu-id="e6404-170">Magnetism</span></span>

<span data-ttu-id="e6404-171">此机制可以看作"最靠近链接"算法的绘制光标向目标，或只需增加 hitboxes （无论是以可视方式还是不） 的更多常规版本用户达到可能的目标，如使用交互式布局与一些知识更好的方法用户的意图。</span><span class="sxs-lookup"><span data-stu-id="e6404-171">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="e6404-172">这可以是小型的目标对于特别有用。</span><span class="sxs-lookup"><span data-stu-id="e6404-172">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="e6404-173">焦点粘性</span><span class="sxs-lookup"><span data-stu-id="e6404-173">Focus stickiness</span></span>

<span data-ttu-id="e6404-174">在确定其附近的焦点转至交互式元素，提供对当前已设定焦点的元素偏移。</span><span class="sxs-lookup"><span data-stu-id="e6404-174">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="e6404-175">这将有助于减少不正常时浮点位于自然干扰的两个元素之间的中点的切换行为的焦点。</span><span class="sxs-lookup"><span data-stu-id="e6404-175">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6404-176">请参阅</span><span class="sxs-lookup"><span data-stu-id="e6404-176">See also</span></span>
* [<span data-ttu-id="e6404-177">手势</span><span class="sxs-lookup"><span data-stu-id="e6404-177">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="e6404-178">语音命令</span><span class="sxs-lookup"><span data-stu-id="e6404-178">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="e6404-179">光标</span><span class="sxs-lookup"><span data-stu-id="e6404-179">Cursors</span></span>](cursors.md)
