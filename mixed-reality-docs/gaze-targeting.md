---
title: 注视目标
description: 所有交互的基础都是用户能够将想要与之交互的元素设定为目标，而无论使用何种输入模态。
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, 注视, 注视目标, 交互, 设计
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829841"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="6c825-104">注视和停留</span><span class="sxs-lookup"><span data-stu-id="6c825-104">Gaze and dwell</span></span>
<span data-ttu-id="6c825-105">可以通过多种不同的方法来确认_提交_, 如结合使用_声音_或_手写笔势_。</span><span class="sxs-lookup"><span data-stu-id="6c825-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="6c825-106">不过, 有几种用户方案, 用户的手可能繁忙或不能被跟踪 (例如, 具有超大重型手套的工厂工作人员)。</span><span class="sxs-lookup"><span data-stu-id="6c825-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="6c825-107">由于用户首选项、社交上下文或更高的环境, 语音输入也可能不可用。</span><span class="sxs-lookup"><span data-stu-id="6c825-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="6c825-108">作为回退解决方案, 执行_提交_的另一种方法是将起始置于称为_停留_的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="6c825-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="6c825-109">可以使用打印头或眼睛来执行_停留_。</span><span class="sxs-lookup"><span data-stu-id="6c825-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="6c825-110">此理念非常简单, 可以在以下阶段分解:</span><span class="sxs-lookup"><span data-stu-id="6c825-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="6c825-111">用户在全息按钮上启动 gazing</span><span class="sxs-lookup"><span data-stu-id="6c825-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="6c825-112">在短暂的开始延迟 (例如, 150 ms) 后, 将启动一些视觉反馈动画。</span><span class="sxs-lookup"><span data-stu-id="6c825-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="6c825-113">开始延迟用于避免用户通过立即立即弹出反馈来使用户不堪重负。</span><span class="sxs-lookup"><span data-stu-id="6c825-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="6c825-114">对于_眼睛眼睛_, 建议对视觉对象的显示内容进行以下设计:</span><span class="sxs-lookup"><span data-stu-id="6c825-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="6c825-115">**混合 it**:从一开始就是完全不透明地将反馈从几乎可见。</span><span class="sxs-lookup"><span data-stu-id="6c825-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="6c825-116">这使得反馈减少了混乱和 overwhleming, 并与系统具有用户真正想要与此按钮进行合作的置信度非常一致。</span><span class="sxs-lookup"><span data-stu-id="6c825-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="6c825-117">**拉取**:创建视觉反馈, 而不是缩小大小并向目标中心移动, 从而吸引用户的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="6c825-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="6c825-118">预定义停留时间段 (例如, 800 ms) 后, 停留完成, 并触发关联的事件。</span><span class="sxs-lookup"><span data-stu-id="6c825-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="6c825-119">提供一些正在完成的听觉或视觉反馈, 使其真正进入当前选择的项。</span><span class="sxs-lookup"><span data-stu-id="6c825-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![停留状态](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="6c825-121">注视目标</span><span class="sxs-lookup"><span data-stu-id="6c825-121">Gaze targeting</span></span>

<span data-ttu-id="6c825-122">所有交互的基础都是用户能够将想要与之交互的元素设定为目标，而无论使用何种输入模态。</span><span class="sxs-lookup"><span data-stu-id="6c825-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="6c825-123">在 Windows Mixed Reality 中，通常通过用户凝视来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="6c825-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="6c825-124">为了实现成功使用，系统对用户意图的计算理解与用户的实际意图必须尽可能保持一致。</span><span class="sxs-lookup"><span data-stu-id="6c825-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="6c825-125">按照系统正确解释用户目标操作的程度，满意度提高，性能提高。</span><span class="sxs-lookup"><span data-stu-id="6c825-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="6c825-126">设备支持</span><span class="sxs-lookup"><span data-stu-id="6c825-126">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6c825-127"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="6c825-127"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6c825-128"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="6c825-128"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6c825-129"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6c825-129"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6c825-130"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="6c825-130"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6c825-131">注视目标</span><span class="sxs-lookup"><span data-stu-id="6c825-131">Gaze targeting</span></span></td>
        <td><span data-ttu-id="6c825-132">✔️</span><span class="sxs-lookup"><span data-stu-id="6c825-132">✔️</span></span></td>
        <td><span data-ttu-id="6c825-133">✔️</span><span class="sxs-lookup"><span data-stu-id="6c825-133">✔️</span></span></td>
        <td><span data-ttu-id="6c825-134">✔️</span><span class="sxs-lookup"><span data-stu-id="6c825-134">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6c825-135">目视目标</span><span class="sxs-lookup"><span data-stu-id="6c825-135">Eye targeting</span></span></td>
        <td><span data-ttu-id="6c825-136">❌</span><span class="sxs-lookup"><span data-stu-id="6c825-136">❌</span></span></td>
        <td><span data-ttu-id="6c825-137">✔️</span><span class="sxs-lookup"><span data-stu-id="6c825-137">✔️</span></span></td>
        <td><span data-ttu-id="6c825-138">❌</span><span class="sxs-lookup"><span data-stu-id="6c825-138">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="6c825-139">即将[推出](index.md)特定于 HoloLens 2 的更多指导。</span><span class="sxs-lookup"><span data-stu-id="6c825-139">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="6c825-140">目标大小调整和反馈</span><span class="sxs-lookup"><span data-stu-id="6c825-140">Target sizing and feedback</span></span>

<span data-ttu-id="6c825-141">凝视向量已多次被证明可用于精确设定目标，但通常最适合粗略设定目标（获取较大的目标）。</span><span class="sxs-lookup"><span data-stu-id="6c825-141">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="6c825-142">最小目标尺寸为 1 到 1.5 度时，用户在大多数情况下都可成功执行操作，但目标尺寸为 3 度时通常可更快地设定目标。</span><span class="sxs-lookup"><span data-stu-id="6c825-142">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="6c825-143">请注意，即使对于 3D 元素，用户设定为目标的尺寸实际上也是 2D 区域，3D 元素的投影即是可设定为目标的区域。</span><span class="sxs-lookup"><span data-stu-id="6c825-143">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="6c825-144">提供一些明确的提示来表明一个元素“处于活动状态”（即用户将其设定为目标）非常有用，这可能包括可见的“悬停”效果、音频突出显示或单击，或光标与元素清晰对齐。</span><span class="sxs-lookup"><span data-stu-id="6c825-144">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="6c825-145">![2 米远处的最佳目标大小](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6c825-145">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="6c825-146">*2 米远处的最佳目标大小*</span><span class="sxs-lookup"><span data-stu-id="6c825-146">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="6c825-147">![突出显示凝视目标对象的示例](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6c825-147">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="6c825-148">*突出显示凝视目标对象的示例*</span><span class="sxs-lookup"><span data-stu-id="6c825-148">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="6c825-149">目标位置</span><span class="sxs-lookup"><span data-stu-id="6c825-149">Target placement</span></span>

<span data-ttu-id="6c825-150">用户经常无法找到位于其视野中非常高或非常低的位置的 UI 元素，大部分注意力集中在主要焦点（通常大致是视平线位置）周围的区域。</span><span class="sxs-lookup"><span data-stu-id="6c825-150">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="6c825-151">将大多数目标放在视平线位置附近的某个合理范围内可能有所帮助。</span><span class="sxs-lookup"><span data-stu-id="6c825-151">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="6c825-152">考虑到用户在任何时候都倾向于关注一个相对较小的可视区域（注意力视锥大约为 10 度），通过将 UI 元素分组到在概念上相关的位置，可以在用户的视线通过某个区域时利用各项目之间的注意力链锁作用。</span><span class="sxs-lookup"><span data-stu-id="6c825-152">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="6c825-153">在设计 UI 时，请注意 HoloLens 和沉浸式头戴显示设备之间视野的巨大差异。</span><span class="sxs-lookup"><span data-stu-id="6c825-153">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="6c825-154">![在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6c825-154">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="6c825-155">*在 Galaxy Explorer 中使用分组 UI 元素简化凝视目标设定的示例*</span><span class="sxs-lookup"><span data-stu-id="6c825-155">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="6c825-156">改进目标设定行为</span><span class="sxs-lookup"><span data-stu-id="6c825-156">Improving targeting behaviors</span></span>

<span data-ttu-id="6c825-157">如果能够确定（或非常近似地确定）用户目标，那么接受“差一点”的交互尝试非常有帮助，就好像它们是正确的目标一样。</span><span class="sxs-lookup"><span data-stu-id="6c825-157">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="6c825-158">有一些成功的方法可以融入混合现实体验中：</span><span class="sxs-lookup"><span data-stu-id="6c825-158">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="6c825-159">注视稳定 ("重力井")</span><span class="sxs-lookup"><span data-stu-id="6c825-159">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="6c825-160">应在大多数/所有时间启用此技术。</span><span class="sxs-lookup"><span data-stu-id="6c825-160">This should be turned on most/all of the time.</span></span> <span data-ttu-id="6c825-161">此技术消除了用户可能产生的自然头部/颈部抖动。</span><span class="sxs-lookup"><span data-stu-id="6c825-161">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="6c825-162">也可消除因看/说行为导致的运动。</span><span class="sxs-lookup"><span data-stu-id="6c825-162">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="6c825-163">最邻近链接算法</span><span class="sxs-lookup"><span data-stu-id="6c825-163">Closest link algorithms</span></span>

<span data-ttu-id="6c825-164">这些方法在交互内容稀少的区域效果最好。</span><span class="sxs-lookup"><span data-stu-id="6c825-164">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="6c825-165">如果你很有可能确定用户要尝试与之交互的内容，那么可以通过简单地假设某种程度的意图来补充其目标设定能力。</span><span class="sxs-lookup"><span data-stu-id="6c825-165">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="6c825-166">回溯/推迟操作</span><span class="sxs-lookup"><span data-stu-id="6c825-166">Backdating/postdating actions</span></span>

<span data-ttu-id="6c825-167">此机制非常适合需要快速完成的任务。</span><span class="sxs-lookup"><span data-stu-id="6c825-167">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="6c825-168">当用户通过一系列面向设法使其/激活的速度来快速进行操作时, 可能会有一定的意图, 并允许*错过的步骤*处理用户在点击 (50ms 之前/之后) 略有针对性的目标在早期测试中有效。</span><span class="sxs-lookup"><span data-stu-id="6c825-168">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="6c825-169">平滑处理</span><span class="sxs-lookup"><span data-stu-id="6c825-169">Smoothing</span></span>

<span data-ttu-id="6c825-170">此机制对于路径运动非常有用，可减少由于头部自然运动特征引起的轻微抖动/摆动。</span><span class="sxs-lookup"><span data-stu-id="6c825-170">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="6c825-171">对路径运动进行平滑处理时，根据运动幅度/距离（而非随着时间推移）进行平滑处理</span><span class="sxs-lookup"><span data-stu-id="6c825-171">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="6c825-172">磁吸</span><span class="sxs-lookup"><span data-stu-id="6c825-172">Magnetism</span></span>

<span data-ttu-id="6c825-173">此机制可被视为更通用的“最邻近链接”算法，可绘制靠近目标的光标，或者只是在用户接近可能的目标时增加有效范围（无论是否可见），使用一些交互式布局知识来更好地实现用户意图。</span><span class="sxs-lookup"><span data-stu-id="6c825-173">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="6c825-174">这对于小型目标尤其有用。</span><span class="sxs-lookup"><span data-stu-id="6c825-174">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="6c825-175">焦点粘性</span><span class="sxs-lookup"><span data-stu-id="6c825-175">Focus stickiness</span></span>

<span data-ttu-id="6c825-176">此机制可在确定要置于焦点的邻近交互元素时，提供其与当前置于焦点的元素的偏差。</span><span class="sxs-lookup"><span data-stu-id="6c825-176">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="6c825-177">这将有助于减少在具有自然噪声的两个元素之间的中点处浮动时的不稳定焦点切换行为。</span><span class="sxs-lookup"><span data-stu-id="6c825-177">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c825-178">请参阅</span><span class="sxs-lookup"><span data-stu-id="6c825-178">See also</span></span>
* [<span data-ttu-id="6c825-179">手势</span><span class="sxs-lookup"><span data-stu-id="6c825-179">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="6c825-180">语音命令</span><span class="sxs-lookup"><span data-stu-id="6c825-180">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="6c825-181">光标</span><span class="sxs-lookup"><span data-stu-id="6c825-181">Cursors</span></span>](cursors.md)
