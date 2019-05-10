---
title: 视线移动和停留
description: 视线移动和停留输入模型概述
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: 混合现实，注视、 停留、 交互，设计
ms.openlocfilehash: d99180b6eb278eb6d7bf322c01a1c7cceb7fad1f
ms.sourcegitcommit: a4a53e6772805d89a47588857e3e8fb1fd8d9710
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469061"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="aa769-104">视线移动和停留</span><span class="sxs-lookup"><span data-stu-id="aa769-104">Gaze and dwell</span></span>

<span data-ttu-id="aa769-105">时手都与工具和部件被占用，笔势可以是枯燥乏味或不可能。</span><span class="sxs-lookup"><span data-stu-id="aa769-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>  <span data-ttu-id="aa769-106">语音命令，如手势时，可以是情况不可靠，例如在过大的情况下。</span><span class="sxs-lookup"><span data-stu-id="aa769-106">Voice commands, like gesture, can be situationally unreliable, for example under excessively loud conditions.</span></span>  <span data-ttu-id="aa769-107">此外，使用语音控制计算机并不是主流的交互，但它肯定获得流 ！</span><span class="sxs-lookup"><span data-stu-id="aa769-107">Additionally, using voice to control computers isn't a mainstream interaction yet, but it certainly is gaining steam!</span></span>  <span data-ttu-id="aa769-108">提供注视停留提供工作平视无 HoloLens 上的最常见和最容易 master 机制。</span><span class="sxs-lookup"><span data-stu-id="aa769-108">Gaze dwell offers the most familiar and easy-to-master mechanism for working heads-up hands-free on HoloLens.</span></span>  <span data-ttu-id="aa769-109">此外，提供注视停留是 100%可靠独立的操作环境中的干扰会相互干扰，也不静默约束。</span><span class="sxs-lookup"><span data-stu-id="aa769-109">Additionally, gaze dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="goals"></a><span data-ttu-id="aa769-110">目标</span><span class="sxs-lookup"><span data-stu-id="aa769-110">Goals</span></span>

<span data-ttu-id="aa769-111">提供一种机制来进行完全无需手动交互，而无需使用语音。</span><span class="sxs-lookup"><span data-stu-id="aa769-111">Provide a mechanism for full hands-free interactions, without using voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="aa769-112">设计原则</span><span class="sxs-lookup"><span data-stu-id="aa769-112">Design principles</span></span>

1. <span data-ttu-id="aa769-113">视线移动不是一武器</span><span class="sxs-lookup"><span data-stu-id="aa769-113">Gaze is not a weapon</span></span>
    
    <span data-ttu-id="aa769-114">视线移动需要可视反馈进行直观交互，但太多的反馈可以引入感到不安。</span><span class="sxs-lookup"><span data-stu-id="aa769-114">Gaze requires visual feedback for intuitive interaction, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="aa769-115">反馈应帮助用户了解什么他们面向的，但不是自动选择对其意图。</span><span class="sxs-lookup"><span data-stu-id="aa769-115">The feedback should help a user know what they're targeting, but not auto-select against their intent.</span></span> <span data-ttu-id="aa769-116">读取文本需要额外的注意事项，以便提供用户空间，以选择之前消减信息。</span><span class="sxs-lookup"><span data-stu-id="aa769-116">Reading text requires extra consideration to provide a user room to absorb the info before selecting.</span></span>
    
2. <span data-ttu-id="aa769-117">查找 Goldilocks 速度</span><span class="sxs-lookup"><span data-stu-id="aa769-117">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="aa769-118">停留填充可以具有不同的计时器根据影响导航-更必然函数可能会受益于填充时间较长时，更常用的函数通常将受益于更快的填充时间。</span><span class="sxs-lookup"><span data-stu-id="aa769-118">The dwell fill can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="aa769-119">填充颜色的动画曲线可以积极地影响填充更快的感觉。</span><span class="sxs-lookup"><span data-stu-id="aa769-119">Animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="aa769-120">不考虑，应采取以启用从快速/medium/速度缓慢的用户决定填充速度重写。</span><span class="sxs-lookup"><span data-stu-id="aa769-120">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="aa769-121">说到 yo-yo 效果不允许</span><span class="sxs-lookup"><span data-stu-id="aa769-121">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="aa769-122">Yo-yo 效果 (也称为"晚上在 Roxbury") 是不喜欢模式，它可以从内容和的视线移动基于控件的特定位置出现。</span><span class="sxs-lookup"><span data-stu-id="aa769-122">The yo-yo effect (also known as "Night at the Roxbury") is an uncomfortable pattern that can emerge from certain  placement of content and gaze-based controls.</span></span> <span data-ttu-id="aa769-123">例如，列表的导航栏底部的填充按钮与引入循环-看下会仔细斟酌、 查看结果、 向下查看到停留，等等。此生成的模式不舒服，应避免通过将导航控件放入后，包括反复占用更少的集中位置。</span><span class="sxs-lookup"><span data-stu-id="aa769-123">For example, a list nav with the fill button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="aa769-124">放置停留按钮相对于其效果变得重要舒适。</span><span class="sxs-lookup"><span data-stu-id="aa769-124">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="aa769-125">UI 模式</span><span class="sxs-lookup"><span data-stu-id="aa769-125">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="aa769-126">高频率按钮</span><span class="sxs-lookup"><span data-stu-id="aa769-126">High frequency buttons</span></span>
    
* <span data-ttu-id="aa769-127">下一步/后退按钮</span><span class="sxs-lookup"><span data-stu-id="aa769-127">Next/Back buttons</span></span>
  * <span data-ttu-id="aa769-128">非常短暂的延迟预填充 （立交桥闪烁缓冲区）</span><span class="sxs-lookup"><span data-stu-id="aa769-128">Very short delay pre-fill (flyover flicker buffer)</span></span>
  * <span data-ttu-id="aa769-129">更大按钮是容易遭遇的视线移动</span><span class="sxs-lookup"><span data-stu-id="aa769-129">Larger buttons are easier to hit with gaze</span></span>
  * <span data-ttu-id="aa769-130">最好保持在关注高度交互因此没有压力</span><span class="sxs-lookup"><span data-stu-id="aa769-130">Nice to keep these at eye height so no strain to interact</span></span>
  * <span data-ttu-id="aa769-131">停留区域可能会大于处于非活动状态的图标，以使其更易于使用 （返回）</span><span class="sxs-lookup"><span data-stu-id="aa769-131">Dwell region can be larger than inactive icon to make it easier to use (Back)</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="aa769-132">低频率按钮</span><span class="sxs-lookup"><span data-stu-id="aa769-132">Low frequency buttons</span></span>
    
* <span data-ttu-id="aa769-133">激活设置菜单</span><span class="sxs-lookup"><span data-stu-id="aa769-133">Activate settings menu</span></span>
  * <span data-ttu-id="aa769-134">再延迟预填充好 （立交桥闪烁缓冲区）</span><span class="sxs-lookup"><span data-stu-id="aa769-134">Longer delay pre-fill okay (flyover flicker buffer)</span></span>
  * <span data-ttu-id="aa769-135">尝试使这些按钮不频繁的游标的途径干扰</span><span class="sxs-lookup"><span data-stu-id="aa769-135">Try to keep these buttons out of the way of frequent cursor pathways</span></span>

* <span data-ttu-id="aa769-136">确认 （即扫描流，对话框）</span><span class="sxs-lookup"><span data-stu-id="aa769-136">Confirmations (i.e. scan flow, dialogs)</span></span>
  * <span data-ttu-id="aa769-137">在主要按钮上显示选择突出显示</span><span class="sxs-lookup"><span data-stu-id="aa769-137">Show selection highlight on main button</span></span>
  * <span data-ttu-id="aa769-138">显示在选择突出显示相同的时间会仔细斟酌目标</span><span class="sxs-lookup"><span data-stu-id="aa769-138">Reveal dwell target at same time as selection highlight</span></span>
  * <span data-ttu-id="aa769-139">使用在此再次详述周围图标使界面保持简单的目标</span><span class="sxs-lookup"><span data-stu-id="aa769-139">Use dwell target surrounding icon to keep interface simple</span></span>
  * <span data-ttu-id="aa769-140">重要决策，因此不会激活突出显示，请根据情况进行调整的时间显示停留目标</span><span class="sxs-lookup"><span data-stu-id="aa769-140">Important decision, so highlight doesn't activate, reveals dwell target for reconsideration time</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="aa769-141">切换按钮</span><span class="sxs-lookup"><span data-stu-id="aa769-141">Toggle buttons</span></span>

* <span data-ttu-id="aa769-142">Pin</span><span class="sxs-lookup"><span data-stu-id="aa769-142">Pin</span></span>
  * <span data-ttu-id="aa769-143">清除活动/非活动的可视状态</span><span class="sxs-lookup"><span data-stu-id="aa769-143">Clear active/inactive visual state</span></span>
  * <span data-ttu-id="aa769-144">径向填充有助于焦点用户，并提供自然进度</span><span class="sxs-lookup"><span data-stu-id="aa769-144">Radial fill helps focus user and provides natural progress</span></span> 

* <span data-ttu-id="aa769-145">各项设置</span><span class="sxs-lookup"><span data-stu-id="aa769-145">Individual settings</span></span>
  * <span data-ttu-id="aa769-146">清除活动/非活动状态</span><span class="sxs-lookup"><span data-stu-id="aa769-146">Clear active/inactive states</span></span>
  * <span data-ttu-id="aa769-147">在此再次详述左侧周围的图标上所有的目标</span><span class="sxs-lookup"><span data-stu-id="aa769-147">Dwell targets all on left surrounding icon</span></span>
  * <span data-ttu-id="aa769-148">停留以仅显示所选内容时突出显示活动为目标</span><span class="sxs-lookup"><span data-stu-id="aa769-148">Dwell targets only show up when selection highlight active</span></span>
  * <span data-ttu-id="aa769-149">"在此再次详述滑块"右侧的开/关设置</span><span class="sxs-lookup"><span data-stu-id="aa769-149">"Dwell on slider" on right side for on/off settings</span></span>

### <a name="list-views"></a><span data-ttu-id="aa769-150">列表视图</span><span class="sxs-lookup"><span data-stu-id="aa769-150">List views</span></span>

* <span data-ttu-id="aa769-151">浏览列表视图-要打开的指南文件</span><span class="sxs-lookup"><span data-stu-id="aa769-151">Browsing list view - guide files to open</span></span>
  * <span data-ttu-id="aa769-152">游标突出显示行从任意位置在行上，但不开始停留</span><span class="sxs-lookup"><span data-stu-id="aa769-152">Cursor highlights row from anywhere on row but doesn’t begin dwell</span></span>
  * <span data-ttu-id="aa769-153">当行由游标突出显示时，在左侧显示停留目标</span><span class="sxs-lookup"><span data-stu-id="aa769-153">When row is highlighted by cursor, dwell target appears on left</span></span>
  * <span data-ttu-id="aa769-154">在此再次详述目标始终左侧和右侧的所有列表视图中的文本的上一个圆圈</span><span class="sxs-lookup"><span data-stu-id="aa769-154">Dwell target always a circle on left side of text in all list views</span></span>
  * <span data-ttu-id="aa769-155">不显示所有在此再次详述目标立即以避免重复 UI</span><span class="sxs-lookup"><span data-stu-id="aa769-155">Don't show all dwell targets at once to avoid repetitive UI</span></span>
  * <span data-ttu-id="aa769-156">重复使用相同的模式来建立用户体验的了解</span><span class="sxs-lookup"><span data-stu-id="aa769-156">Re-use the same pattern to establish UX familiarity</span></span>
        
* <span data-ttu-id="aa769-157">浏览列表视图-层次结构的任务/在指南中的步骤</span><span class="sxs-lookup"><span data-stu-id="aa769-157">Browsing list view - hierarchy of tasks/steps in a guide</span></span>
  * <span data-ttu-id="aa769-158">在此再次详述目标始终在文本左侧圆圈</span><span class="sxs-lookup"><span data-stu-id="aa769-158">Dwell target always a circle on left side of text</span></span>
  * <span data-ttu-id="aa769-159">展开/折叠功能可见性： 在此再次详述</span><span class="sxs-lookup"><span data-stu-id="aa769-159">Collapse/expand dwell affordance</span></span>
        
* <span data-ttu-id="aa769-160">浏览列表视图-模式，请选择</span><span class="sxs-lookup"><span data-stu-id="aa769-160">Browsing list view - mode select</span></span>
  * <span data-ttu-id="aa769-161">遵循上面建立的模式</span><span class="sxs-lookup"><span data-stu-id="aa769-161">Follow patterns established above</span></span>

### <a name="contextual-buttons"></a><span data-ttu-id="aa769-162">上下文的按钮</span><span class="sxs-lookup"><span data-stu-id="aa769-162">Contextual buttons</span></span>

* <span data-ttu-id="aa769-163">显示/隐藏 3D-显示了在 3D 沿附近全息二者</span><span class="sxs-lookup"><span data-stu-id="aa769-163">Show/Hide 3D - shows up in 3D along tether near holograms</span></span> 
  * <span data-ttu-id="aa769-164">清除活动/非活动的可视状态</span><span class="sxs-lookup"><span data-stu-id="aa769-164">Clear active/inactive visual state</span></span>

### <a name="pivots"></a><span data-ttu-id="aa769-165">透视</span><span class="sxs-lookup"><span data-stu-id="aa769-165">Pivots</span></span>

* <span data-ttu-id="aa769-166">最近/All 指南列表</span><span class="sxs-lookup"><span data-stu-id="aa769-166">Recent/All guides list</span></span>
  * <span data-ttu-id="aa769-167">填充 UI 功能可见保持指示哪个选项卡处于活动状态性：</span><span class="sxs-lookup"><span data-stu-id="aa769-167">Fill the UI affordance that remains to indicate which tab is active</span></span>
  * <span data-ttu-id="aa769-168">对于短单字数据透视表，我们选择放弃停留目标模式</span><span class="sxs-lookup"><span data-stu-id="aa769-168">For short single word pivots, we elected to forego the dwell target pattern</span></span>
  * <span data-ttu-id="aa769-169">我们更简化的界面倾向于另一个 2 个圆圈目标和更广泛的用户界面</span><span class="sxs-lookup"><span data-stu-id="aa769-169">We favored the simplified interface over another 2 circle targets and a wider UI</span></span>
  * <span data-ttu-id="aa769-170">在我们的示例中的单词是短延迟提供足够舒适之前填充</span><span class="sxs-lookup"><span data-stu-id="aa769-170">In our case, the words are short enough that a delay provides enough comfort before filling</span></span>


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="aa769-171">UX 准则和最佳做法</span><span class="sxs-lookup"><span data-stu-id="aa769-171">UX guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="aa769-172">目标大小</span><span class="sxs-lookup"><span data-stu-id="aa769-172">Target sizes</span></span>

  * <span data-ttu-id="aa769-173">固定图标的最小大小：在 Unity 中，30 Mru （@ 2 分 30 厘米） 的世界空间中的 6 cm</span><span class="sxs-lookup"><span data-stu-id="aa769-173">Pin icon minimum size: 6cm in world space in Unity, 30 MRUs ( 30cm @ 2m)</span></span>
  * <span data-ttu-id="aa769-174">一点都目标"磁化"粘滞"？</span><span class="sxs-lookup"><span data-stu-id="aa769-174">Are the targets "magnetized" or "sticky" at all?</span></span> <span data-ttu-id="aa769-175">（即注视游标平滑）</span><span class="sxs-lookup"><span data-stu-id="aa769-175">(i.e. gaze cursor smoothing)</span></span>

### <a name="animation"></a><span data-ttu-id="aa769-176">动画</span><span class="sxs-lookup"><span data-stu-id="aa769-176">Animation</span></span>

  * <span data-ttu-id="aa769-177">前停留视觉触发器.5sec 延迟</span><span class="sxs-lookup"><span data-stu-id="aa769-177">Delay before dwell visual triggers .5sec</span></span>
  * <span data-ttu-id="aa769-178">停留 visual 1.2 秒的持续时间</span><span class="sxs-lookup"><span data-stu-id="aa769-178">Duration of dwell visual 1.2sec</span></span>
  * <span data-ttu-id="aa769-179">曲线动画？</span><span class="sxs-lookup"><span data-stu-id="aa769-179">Curve on animation?</span></span>

### <a name="visual-feedback"></a><span data-ttu-id="aa769-180">视觉反馈</span><span class="sxs-lookup"><span data-stu-id="aa769-180">Visual feedback</span></span>

  * <span data-ttu-id="aa769-181">从的视线移动光标所在的开始位置的径向填充</span><span class="sxs-lookup"><span data-stu-id="aa769-181">Radial fill from gaze cursor start location</span></span>
  * <span data-ttu-id="aa769-182">从中心的按钮始终径向填充。</span><span class="sxs-lookup"><span data-stu-id="aa769-182">Always radial fill from center of button.</span></span> <span data-ttu-id="aa769-183">一致的响应是减少混淆比在不同的按钮上的所有不同的方向。</span><span class="sxs-lookup"><span data-stu-id="aa769-183">A consistent response is less confusing than all different directions on different buttons.</span></span> 
    * <span data-ttu-id="aa769-184">而对于方向交互 （例如，导航栏向上/向下/左/右，等），可以断开此规则。</span><span class="sxs-lookup"><span data-stu-id="aa769-184">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="aa769-185">例如，在下一步/后保留的异常的指南使向右填充。</span><span class="sxs-lookup"><span data-stu-id="aa769-185">For example, Guides makes an exception on Next/Back being left right fills.</span></span>
    * <span data-ttu-id="aa769-186">请考虑反转从外部的径向填充 （如果关闭切换）。</span><span class="sxs-lookup"><span data-stu-id="aa769-186">Consider inverting radial fill from outside (if toggling off).</span></span> <span data-ttu-id="aa769-187">按下按钮的反感觉是很好的可视模式来维护。</span><span class="sxs-lookup"><span data-stu-id="aa769-187">THe inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="aa769-188">渐进式披露</span><span class="sxs-lookup"><span data-stu-id="aa769-188">Progressive disclosure</span></span>

 * <span data-ttu-id="aa769-189">渐进式披露意味着停留目标显示上突出显示 （例如，在列表控件）</span><span class="sxs-lookup"><span data-stu-id="aa769-189">Progressive disclosure means that the dwell target is revealed on highlight (e.g., in a list control)</span></span>
 * <span data-ttu-id="aa769-190">文本栏突出显示与聚焦显示上任意位置上文本的视线移动</span><span class="sxs-lookup"><span data-stu-id="aa769-190">Text bar highlights with spotlight reveal on gaze anywhere on text</span></span>
 * <span data-ttu-id="aa769-191">提供注视填充目标将始终显示列表项突出显示的左侧，但仅限</span><span class="sxs-lookup"><span data-stu-id="aa769-191">Gaze fill target appears always on left, but only for the list item which is highlighted</span></span>
 * <span data-ttu-id="aa769-192">尽量避免由于重复外观堆积圆始终对所有停留目标</span><span class="sxs-lookup"><span data-stu-id="aa769-192">Try to avoid having all dwell targets on at all times due to repetitive look of stacked circles</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="aa769-193">请参阅</span><span class="sxs-lookup"><span data-stu-id="aa769-193">See also</span></span>
* [<span data-ttu-id="aa769-194">直接操作</span><span class="sxs-lookup"><span data-stu-id="aa769-194">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="aa769-195">指向并提交</span><span class="sxs-lookup"><span data-stu-id="aa769-195">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="aa769-196">交互基础知识</span><span class="sxs-lookup"><span data-stu-id="aa769-196">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="aa769-197">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="aa769-197">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="aa769-198">凝视和语音</span><span class="sxs-lookup"><span data-stu-id="aa769-198">Gaze and voice</span></span>](voice-design.md)
