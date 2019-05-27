---
title: Head 注视和停留
description: Head 注视和停留输入模型概述
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实，注视、 停留、 交互，设计
ms.openlocfilehash: ae4688da791fd3afb7be66069049bbe51102dd7e
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039201"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="25ec8-104">Head 注视和停留</span><span class="sxs-lookup"><span data-stu-id="25ec8-104">Head-gaze and dwell</span></span>

<span data-ttu-id="25ec8-105">时手都与工具和部件被占用，笔势可以是枯燥乏味或不可能。</span><span class="sxs-lookup"><span data-stu-id="25ec8-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="25ec8-106">语音命令，如手势，可以在某些上下文中，例如在过大的情况下不可靠。</span><span class="sxs-lookup"><span data-stu-id="25ec8-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="25ec8-107">此外，使用语音控制计算机并不是普遍常见，但它肯定获得流 ！</span><span class="sxs-lookup"><span data-stu-id="25ec8-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="25ec8-108">Head 注视和停留提供了工作 heads-up 和无 HoloLens 上的最常见和最容易 master 机制。</span><span class="sxs-lookup"><span data-stu-id="25ec8-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="25ec8-109">此外，提供注视 head 和停留是 100%可靠独立的操作环境中的干扰会相互干扰，也不静默约束。</span><span class="sxs-lookup"><span data-stu-id="25ec8-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="25ec8-110">方案</span><span class="sxs-lookup"><span data-stu-id="25ec8-110">Scenarios</span></span>

<span data-ttu-id="25ec8-111">Head 注视和停留的优越性体现在方案中人的手均忙于处理其他任务，而语音不是 100%可靠或由于环境或社交约束提供。</span><span class="sxs-lookup"><span data-stu-id="25ec8-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or availible due to environmental or social constraints.</span></span> <span data-ttu-id="25ec8-112">一个很好示例是一个人戴上 HoloLens 覆盖修复汽车引擎时的参考信息。</span><span class="sxs-lookup"><span data-stu-id="25ec8-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="25ec8-113">太多的事情都在忙于 with tools 或支持其主体，因为它们了解到引擎隔离舱。</span><span class="sxs-lookup"><span data-stu-id="25ec8-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="25ec8-114">与常量进行深入探讨和工具，使语音命令变得困难的嗡嗡声噪音车库空间很大。</span><span class="sxs-lookup"><span data-stu-id="25ec8-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="25ec8-115">Head 注视和停留允许 HoloLens 更有信心地导航而无需 interupting 其参考资料中的人员及其工作流。</span><span class="sxs-lookup"><span data-stu-id="25ec8-115">Head-gaze and dwell allows the person in the HoloLens to confidently navigate their reference material without interupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="25ec8-116">设备支持</span><span class="sxs-lookup"><span data-stu-id="25ec8-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="25ec8-117"><strong>输入的模型</strong></span><span class="sxs-lookup"><span data-stu-id="25ec8-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="25ec8-118"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="25ec8-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="25ec8-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="25ec8-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="25ec8-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></span><span class="sxs-lookup"><span data-stu-id="25ec8-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="25ec8-121">Head 注视和停留</span><span class="sxs-lookup"><span data-stu-id="25ec8-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="25ec8-122">✔️ 建议</span><span class="sxs-lookup"><span data-stu-id="25ec8-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="25ec8-123">✔️ 建议</span><span class="sxs-lookup"><span data-stu-id="25ec8-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="25ec8-124">✔️ 建议</span><span class="sxs-lookup"><span data-stu-id="25ec8-124">✔️ Recommended</span></span></td>
    </tr>
</table>

## <a name="goals"></a><span data-ttu-id="25ec8-125">目标</span><span class="sxs-lookup"><span data-stu-id="25ec8-125">Goals</span></span>

<span data-ttu-id="25ec8-126">提供一种机制来进行完全无需手动交互，而无需使用语音。</span><span class="sxs-lookup"><span data-stu-id="25ec8-126">Provide a mechanism for fully hands-free interactions, without using Voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="25ec8-127">设计原则</span><span class="sxs-lookup"><span data-stu-id="25ec8-127">Design principles</span></span>

1. <span data-ttu-id="25ec8-128">避免"作为一武器注视"</span><span class="sxs-lookup"><span data-stu-id="25ec8-128">Avoid "Gaze as a weapon"</span></span>

    <span data-ttu-id="25ec8-129">Head 注视和停留需要视觉反馈以直观，但太多的反馈可以引入感到不安。</span><span class="sxs-lookup"><span data-stu-id="25ec8-129">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="25ec8-130">反馈应帮助用户了解什么他们面向的，但不是自动选择它针对其意图。</span><span class="sxs-lookup"><span data-stu-id="25ec8-130">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="25ec8-131">读取文本、 图标和标签需要额外的注意事项，以便提供应对所导致的信息，然后选择 person 空间。</span><span class="sxs-lookup"><span data-stu-id="25ec8-131">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
2. <span data-ttu-id="25ec8-132">查找 Goldilocks 速度</span><span class="sxs-lookup"><span data-stu-id="25ec8-132">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="25ec8-133">停留交互可以具有不同的计时器根据影响导航-更必然函数可能会受益于填充时间较长时，更常用的函数通常将受益于更快的填充时间。</span><span class="sxs-lookup"><span data-stu-id="25ec8-133">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="25ec8-134">当使用填充效果来显示这些计时器，填充颜色的动画曲线可以积极地影响填充更快的感觉。</span><span class="sxs-lookup"><span data-stu-id="25ec8-134">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="25ec8-135">不考虑，应采取以启用从快速/medium/速度缓慢的用户决定填充速度重写。</span><span class="sxs-lookup"><span data-stu-id="25ec8-135">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="25ec8-136">说到 yo-yo 效果不允许</span><span class="sxs-lookup"><span data-stu-id="25ec8-136">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="25ec8-137">Yo-yo 效果是可以出现时的内容和头注视和停留控件位置强制人去不断地向上和向下重复的磁头运动的令人不舒服模式。</span><span class="sxs-lookup"><span data-stu-id="25ec8-137">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="25ec8-138">例如，列表的导航栏底部的 head 视线移动并停留按钮与引入循环-看下若要在此再次详述，查找在结果中，查找若要在此再次详述，等等。此生成的模式不舒服，应避免通过将导航控件放入后，包括反复占用更少的集中位置。</span><span class="sxs-lookup"><span data-stu-id="25ec8-138">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="25ec8-139">放置停留按钮相对于其效果变得重要舒适。</span><span class="sxs-lookup"><span data-stu-id="25ec8-139">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="25ec8-140">UX 准则和最佳做法</span><span class="sxs-lookup"><span data-stu-id="25ec8-140">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="25ec8-141">目标大小</span><span class="sxs-lookup"><span data-stu-id="25ec8-141">Target sizes</span></span>
  <span data-ttu-id="25ec8-142">可以轻松地访问，head 注视和目标需要足够大到 comforatably 目标，在此再次详述按住的 head stabily 在目标上规定的时间。</span><span class="sxs-lookup"><span data-stu-id="25ec8-142">To be easily accessible, head-gaze and dwell targets need to be large enough to comforatably target, and hold one's head stabily on the target for the prescribed time.</span></span> <span data-ttu-id="25ec8-143">我们建议的最低目标大小为 2 个度，若要获得最合适的体验。</span><span class="sxs-lookup"><span data-stu-id="25ec8-143">We reccomend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="25ec8-144">视觉反馈</span><span class="sxs-lookup"><span data-stu-id="25ec8-144">Visual feedback</span></span>

<span data-ttu-id="25ec8-145">在使用径向填充表示停留计时器，启动从按钮的中心。</span><span class="sxs-lookup"><span data-stu-id="25ec8-145">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="25ec8-146">一致的响应是减少混淆比在不同的按钮上的所有不同的方向。</span><span class="sxs-lookup"><span data-stu-id="25ec8-146">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="25ec8-147">而对于方向交互 （例如，导航栏向上/向下/左/右，等），可以断开此规则。</span><span class="sxs-lookup"><span data-stu-id="25ec8-147">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="25ec8-148">例如，在下一步/后的异常的 Microsoft Dynamics 365 指南使保持正确填充。</span><span class="sxs-lookup"><span data-stu-id="25ec8-148">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="25ec8-149">请考虑反转径向填充从外部，于以下情形： 关闭切换按钮。</span><span class="sxs-lookup"><span data-stu-id="25ec8-149">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="25ec8-150">按下按钮的反感觉是很好的可视模式来维护。</span><span class="sxs-lookup"><span data-stu-id="25ec8-150">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="25ec8-151">渐进式披露</span><span class="sxs-lookup"><span data-stu-id="25ec8-151">Progressive disclosure</span></span>

<span data-ttu-id="25ec8-152">渐进式披露意味着仅显示在每个交互阶段是相关尽可能详细。</span><span class="sxs-lookup"><span data-stu-id="25ec8-152">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="25ec8-153">对于停留，这意味着停留目标上突出显示 （例如，在列表控件） 表示在显示。</span><span class="sxs-lookup"><span data-stu-id="25ec8-153">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="25ec8-154">过大的目标</span><span class="sxs-lookup"><span data-stu-id="25ec8-154">Oversized targets</span></span>
<span data-ttu-id="25ec8-155">停留区域可能会大于非活动状态的图标，以使其更易于使用，如 Microsoft Dynamics 365 指南中的后退按钮。</span><span class="sxs-lookup"><span data-stu-id="25ec8-155">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="25ec8-156">防止闪烁延迟反馈的问题</span><span class="sxs-lookup"><span data-stu-id="25ec8-156">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="25ec8-157">使用开始可视反馈之前短暂的延迟以避免当有人通过停留目标上方时闪烁。</span><span class="sxs-lookup"><span data-stu-id="25ec8-157">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="25ec8-158">为按钮 inteacted 使用频繁，保持非常短的延迟，因此应用程序感觉反应。</span><span class="sxs-lookup"><span data-stu-id="25ec8-158">For buttons inteacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="25ec8-159">对于与 infrequenctly 交互的按钮更长时间可以是适当以免感觉 twitchy 的接口。</span><span class="sxs-lookup"><span data-stu-id="25ec8-159">For buttons that are interacted with infrequenctly a longer delay can be approprate to avoid the interface feeling twitchy.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="25ec8-160">UI 模式</span><span class="sxs-lookup"><span data-stu-id="25ec8-160">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="25ec8-161">高频率按钮</span><span class="sxs-lookup"><span data-stu-id="25ec8-161">High frequency buttons</span></span>
<span data-ttu-id="25ec8-162">![Microsoft Dynamics 365 指南下一步按钮](images/GuideNextButton.png "Microsoft Dynamics 365 指南下一步按钮")高频率按钮是整个应用程序通常使用的按钮。</span><span class="sxs-lookup"><span data-stu-id="25ec8-162">![Microsoft Dynamics 365 Guides Next Button](images/GuideNextButton.png "Microsoft Dynamics 365 Guides Next Button") High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="25ec8-163">其中一个很好示例是 Microsoft Dynamics 365 指南中的前进和后退按钮。</span><span class="sxs-lookup"><span data-stu-id="25ec8-163">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span>

<span data-ttu-id="25ec8-164">高频率按钮应...</span><span class="sxs-lookup"><span data-stu-id="25ec8-164">High frequency buttons should...</span></span>
* <span data-ttu-id="25ec8-165">为更大按钮，更轻松地与 head 注视命中</span><span class="sxs-lookup"><span data-stu-id="25ec8-165">be larger buttons, easier to hit with head-gaze</span></span>
* <span data-ttu-id="25ec8-166">请继续关注高度，以避免人机工程学使出附近。</span><span class="sxs-lookup"><span data-stu-id="25ec8-166">stay near eye height to avoid ergonomic straining.</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="25ec8-167">低频率按钮</span><span class="sxs-lookup"><span data-stu-id="25ec8-167">Low frequency buttons</span></span>
<span data-ttu-id="25ec8-168">低频率按钮是不与之交互，定期整个应用程序的按钮。</span><span class="sxs-lookup"><span data-stu-id="25ec8-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="25ec8-169">很好的示例可能是按钮，访问设置菜单或按钮以清除所有工作。</span><span class="sxs-lookup"><span data-stu-id="25ec8-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="25ec8-170">尝试保留不频繁的视线移动头的路径，以避免意外激活干扰这些按钮。</span><span class="sxs-lookup"><span data-stu-id="25ec8-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

### <a name="confirmations"></a><span data-ttu-id="25ec8-171">确认</span><span class="sxs-lookup"><span data-stu-id="25ec8-171">Confirmations</span></span>
<span data-ttu-id="25ec8-172">![Microsoft Dynamics 365 指南确认对话框](images/GuidesConfirmation.png "Microsoft Dynamics 365 指南确认对话框")</span><span class="sxs-lookup"><span data-stu-id="25ec8-172">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides Confirmation Dialog")</span></span>

<span data-ttu-id="25ec8-173">时操作中有重大影响，如充电资金、 删除的工作，或启动一个长的过程，它可用于确认一个人要选择一个按钮。</span><span class="sxs-lookup"><span data-stu-id="25ec8-173">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span> <span data-ttu-id="25ec8-174">Head 注视和停留存在 Ui 是一些模式和确认对话框时的注意事项：</span><span class="sxs-lookup"><span data-stu-id="25ec8-174">For head-gaze and dwell UIs there are some patterns and considerations for confirmation dialogs:</span></span>

  * <span data-ttu-id="25ec8-175">在主要按钮上显示选择突出显示。</span><span class="sxs-lookup"><span data-stu-id="25ec8-175">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="25ec8-176">在选择突出显示相同的时间显示停留目标。</span><span class="sxs-lookup"><span data-stu-id="25ec8-176">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="25ec8-177">对于辅助按钮，显示 head 注视上的停留目标。</span><span class="sxs-lookup"><span data-stu-id="25ec8-177">For the secondary button, reveal the dwell target on head-gaze.</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="25ec8-178">切换按钮</span><span class="sxs-lookup"><span data-stu-id="25ec8-178">Toggle buttons</span></span>
<span data-ttu-id="25ec8-179">切换按钮需要一些细微的逻辑才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="25ec8-179">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="25ec8-180">当一个人 dwells 上切换按钮和在职员工它时，他们需要退出按钮，然后返回以重启停留逻辑。</span><span class="sxs-lookup"><span data-stu-id="25ec8-180">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="25ec8-181">可滚动按钮处于非活动状态的状态与具有清除活动至关重要。</span><span class="sxs-lookup"><span data-stu-id="25ec8-181">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

### <a name="list-views"></a><span data-ttu-id="25ec8-182">列表视图</span><span class="sxs-lookup"><span data-stu-id="25ec8-182">List views</span></span>
<span data-ttu-id="25ec8-183">![Microsoft Dynamics 365 指南确认对话框](images/GuidesListView.png "Microsoft Dynamics 365 指南确认对话框")列表视图显示 head 视线移动一个特定挑战，输入在此再次详述。</span><span class="sxs-lookup"><span data-stu-id="25ec8-183">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesListView.png "Microsoft Dynamics 365 Guides Confirmation Dialog") List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="25ec8-184">人们需要能够扫描而不 tiptoe 围绕停留目标，这有感觉的内容。</span><span class="sxs-lookup"><span data-stu-id="25ec8-184">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span> 

<span data-ttu-id="25ec8-185">设计列表视图的一些提示：</span><span class="sxs-lookup"><span data-stu-id="25ec8-185">Some tips for designing list views:</span></span>
* <span data-ttu-id="25ec8-186">具有头 gazed 但不开始停留，除非头注视位于特定停留目标时突出显示的整行。</span><span class="sxs-lookup"><span data-stu-id="25ec8-186">have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
* <span data-ttu-id="25ec8-187">仅显示停留目标时突出显示该行以降低视觉干扰。</span><span class="sxs-lookup"><span data-stu-id="25ec8-187">only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
* <span data-ttu-id="25ec8-188">保持清晰一致的停留目标位置。</span><span class="sxs-lookup"><span data-stu-id="25ec8-188">be clear and consistent with the position of dwell targets.</span></span>
* <span data-ttu-id="25ec8-189">不显示所有在此再次详述目标立即以避免重复 UI</span><span class="sxs-lookup"><span data-stu-id="25ec8-189">don't show all dwell targets at once to avoid repetitive UI</span></span>
* <span data-ttu-id="25ec8-190">建立用户体验您所熟悉的尽可能多地重复使用相同的模式</span><span class="sxs-lookup"><span data-stu-id="25ec8-190">re-use the same pattern as often as possible to establish UX familiarity</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="25ec8-191">请参阅</span><span class="sxs-lookup"><span data-stu-id="25ec8-191">See also</span></span>
* [<span data-ttu-id="25ec8-192">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="25ec8-192">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="25ec8-193">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="25ec8-193">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="25ec8-194">本能交互</span><span class="sxs-lookup"><span data-stu-id="25ec8-194">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="25ec8-195">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="25ec8-195">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="25ec8-196">语音命令</span><span class="sxs-lookup"><span data-stu-id="25ec8-196">Voice commanding</span></span>](voice-design.md)
