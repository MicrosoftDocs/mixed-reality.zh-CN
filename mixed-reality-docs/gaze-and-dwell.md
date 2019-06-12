---
title: 头部凝视和停留
description: 头部凝视和停留输入模型概述
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 凝视, 停留, 交互, 设计
ms.openlocfilehash: 70b25949380679d2edc81b07ab54f24fa20e3f3d
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516007"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="f35c7-104">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="f35c7-104">Head-gaze and dwell</span></span>

<span data-ttu-id="f35c7-105">手拿工具和零件，手势可能是没有意义或无法实现。</span><span class="sxs-lookup"><span data-stu-id="f35c7-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="f35c7-106">语音命令（例如手势）在某些情况下可能不可靠，例如在过度嘈杂的条件下。</span><span class="sxs-lookup"><span data-stu-id="f35c7-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="f35c7-107">此外，使用语音控制计算机并不是普遍常见的，但正日益盛行！</span><span class="sxs-lookup"><span data-stu-id="f35c7-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="f35c7-108">头部凝视和停留提供最熟悉且易于掌握的机制，可在 HoloLens 上实现抬头操作和解放双手的操作。</span><span class="sxs-lookup"><span data-stu-id="f35c7-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="f35c7-109">此外，头部凝视和停留 100% 可靠，与操作环境中不受噪声干扰和静音约束。</span><span class="sxs-lookup"><span data-stu-id="f35c7-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="f35c7-110">方案</span><span class="sxs-lookup"><span data-stu-id="f35c7-110">Scenarios</span></span>

<span data-ttu-id="f35c7-111">当双手忙于完成其他任务，且由于环境或社交限制而使声音无法 100% 可靠或可用时，头部凝视和停留效果极佳。</span><span class="sxs-lookup"><span data-stu-id="f35c7-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or availible due to environmental or social constraints.</span></span> <span data-ttu-id="f35c7-112">一个很好的例子是穿戴 HoloLens 的人在修理汽车发动机时获取参考信息。</span><span class="sxs-lookup"><span data-stu-id="f35c7-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="f35c7-113">倚靠在发动机舱内时，他们的手拿着工具或支撑着身体。</span><span class="sxs-lookup"><span data-stu-id="f35c7-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="f35c7-114">车库空间很大，工具不断敲打声和嘈杂声，难以使用语音命令。</span><span class="sxs-lookup"><span data-stu-id="f35c7-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="f35c7-115">通过头部凝视和停留，HoloLens 使用者可安心浏览参考资料，而无需中断工作流程。</span><span class="sxs-lookup"><span data-stu-id="f35c7-115">Head-gaze and dwell allows the person in the HoloLens to confidently navigate their reference material without interupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="f35c7-116">设备支持</span><span class="sxs-lookup"><span data-stu-id="f35c7-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f35c7-117"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="f35c7-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="f35c7-118"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="f35c7-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f35c7-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f35c7-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f35c7-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="f35c7-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f35c7-121">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="f35c7-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="f35c7-122">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="f35c7-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="f35c7-123">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="f35c7-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="f35c7-124">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="f35c7-124">✔️ Recommended</span></span></td>
    </tr>
</table>

## <a name="goals"></a><span data-ttu-id="f35c7-125">目标</span><span class="sxs-lookup"><span data-stu-id="f35c7-125">Goals</span></span>

<span data-ttu-id="f35c7-126">提供完全解放双手的交互机制，无需使用语音。</span><span class="sxs-lookup"><span data-stu-id="f35c7-126">Provide a mechanism for fully hands-free interactions, without using voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="f35c7-127">设计原则</span><span class="sxs-lookup"><span data-stu-id="f35c7-127">Design principles</span></span>

1. <span data-ttu-id="f35c7-128">避免“将凝视作为一种武器”</span><span class="sxs-lookup"><span data-stu-id="f35c7-128">Avoid "Gaze as a weapon"</span></span>

    <span data-ttu-id="f35c7-129">头部凝视和停留需要直观的视觉反馈，但反馈过多会令人焦虑。</span><span class="sxs-lookup"><span data-stu-id="f35c7-129">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="f35c7-130">反馈应有助于用户了解其目标，但不会根据其意图自动选择。</span><span class="sxs-lookup"><span data-stu-id="f35c7-130">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="f35c7-131">阅读文本、图标和标签需要额外考虑，以便为客户提供在进行选择之前吸收信息的空间。</span><span class="sxs-lookup"><span data-stu-id="f35c7-131">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
2. <span data-ttu-id="f35c7-132">寻求适宜速度</span><span class="sxs-lookup"><span data-stu-id="f35c7-132">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="f35c7-133">停留交互根据对导航的影响而使用不同的计时器 - 更频繁使用的功能通常将受益于更快的填充时间，而更具重要性的功能可能受益于更长的填充时间。</span><span class="sxs-lookup"><span data-stu-id="f35c7-133">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="f35c7-134">当使用填充效果来显示这些计时器时，填充颜色的动画曲线可对感知快速填充时间产生正面影响。</span><span class="sxs-lookup"><span data-stu-id="f35c7-134">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="f35c7-135">应进行仔细考虑，使用户能够基于快速/中速/慢速填充速度覆盖来做出决策。</span><span class="sxs-lookup"><span data-stu-id="f35c7-135">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="f35c7-136">对摇摆不定效应说不</span><span class="sxs-lookup"><span data-stu-id="f35c7-136">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="f35c7-137">摇摆不定效应是一种令人不适的头部运动模式，当内容的位置以及头部凝视和停留控制迫使人们不断上下反复看时，即会出现这种效应。</span><span class="sxs-lookup"><span data-stu-id="f35c7-137">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="f35c7-138">例如，通过底部的头部凝视和停留按钮进行列表导航会产生一个循环，即俯视停留、抬头查看结果，再俯视停留。这种生成模式令人不适，应通过将导航控件放置在需要较少来回操作的集中位置来避免。</span><span class="sxs-lookup"><span data-stu-id="f35c7-138">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="f35c7-139">相对于效果放置停留按钮对于确保舒适性非常重要。</span><span class="sxs-lookup"><span data-stu-id="f35c7-139">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="f35c7-140">UX 指南和最佳做法</span><span class="sxs-lookup"><span data-stu-id="f35c7-140">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="f35c7-141">目标大小</span><span class="sxs-lookup"><span data-stu-id="f35c7-141">Target sizes</span></span>
  <span data-ttu-id="f35c7-142">为了方便使用，头部凝视和停留目标需要足够大，以便舒适地瞄准目标，并在规定的时间内使头部稳定地保持在目标上。</span><span class="sxs-lookup"><span data-stu-id="f35c7-142">To be easily accessible, head-gaze and dwell targets need to be large enough to comforatably target, and hold one's head stabily on the target for the prescribed time.</span></span> <span data-ttu-id="f35c7-143">建议最小目标尺寸为 2 度，以获得最舒适的体验。</span><span class="sxs-lookup"><span data-stu-id="f35c7-143">We reccomend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="f35c7-144">视觉反馈</span><span class="sxs-lookup"><span data-stu-id="f35c7-144">Visual feedback</span></span>

<span data-ttu-id="f35c7-145">当使用径向填充来表示停留计时器时，请从按钮中心开始。</span><span class="sxs-lookup"><span data-stu-id="f35c7-145">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="f35c7-146">与在不同按钮上均采用不同方向相比，一致的响应可减少混淆。</span><span class="sxs-lookup"><span data-stu-id="f35c7-146">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="f35c7-147">对于定向交互（例如，向上/向下/向左/向右导航等），可以不遵循此规则。</span><span class="sxs-lookup"><span data-stu-id="f35c7-147">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="f35c7-148">例如，在 Microsoft Dynamics 365 指南中左右两侧填充“下一步”/“后退”时例外。</span><span class="sxs-lookup"><span data-stu-id="f35c7-148">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="f35c7-149">考虑从外部反径向填充，例如关闭按钮。</span><span class="sxs-lookup"><span data-stu-id="f35c7-149">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="f35c7-150">按下按钮的反向效果是一种出色的视觉模式。</span><span class="sxs-lookup"><span data-stu-id="f35c7-150">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="f35c7-151">渐进式披露</span><span class="sxs-lookup"><span data-stu-id="f35c7-151">Progressive disclosure</span></span>

<span data-ttu-id="f35c7-152">渐进式披露是指只显示与交互的每个阶段相关的详细信息。</span><span class="sxs-lookup"><span data-stu-id="f35c7-152">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="f35c7-153">对于停留，这意味着停留目标在突出显示时揭露（例如，在列表控件中）。</span><span class="sxs-lookup"><span data-stu-id="f35c7-153">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="f35c7-154">过大的目标</span><span class="sxs-lookup"><span data-stu-id="f35c7-154">Oversized targets</span></span>
<span data-ttu-id="f35c7-155">停留区域可以比非活动图标大，以便于使用，例如 Microsoft Dynamics 365 指南中的“后退”按钮。</span><span class="sxs-lookup"><span data-stu-id="f35c7-155">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="f35c7-156">通过延迟反馈防止闪烁</span><span class="sxs-lookup"><span data-stu-id="f35c7-156">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="f35c7-157">在开始视觉反馈之前使用短暂的延迟，以避免当有人经过停留目标时闪烁。</span><span class="sxs-lookup"><span data-stu-id="f35c7-157">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="f35c7-158">对于经常与之交互的按钮，请保持非常短的延迟，以便应用程序做出反应。</span><span class="sxs-lookup"><span data-stu-id="f35c7-158">For buttons inteacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="f35c7-159">对于不经常交互的按钮，可能适合使用较长的延迟，以避免界面急于做出响应。</span><span class="sxs-lookup"><span data-stu-id="f35c7-159">For buttons that are interacted with infrequenctly a longer delay can be approprate to avoid the interface feeling twitchy.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="f35c7-160">UI 模式</span><span class="sxs-lookup"><span data-stu-id="f35c7-160">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="f35c7-161">高频率按钮</span><span class="sxs-lookup"><span data-stu-id="f35c7-161">High frequency buttons</span></span>
<span data-ttu-id="f35c7-162">![Microsoft Dynamics 365 指南“下一步”按钮](images/GuideNextButton.png "Microsoft Dynamics 365 指南“下一步”按钮")高频率按钮是在整个应用程序中常用的按钮。</span><span class="sxs-lookup"><span data-stu-id="f35c7-162">![Microsoft Dynamics 365 Guides Next Button](images/GuideNextButton.png "Microsoft Dynamics 365 Guides Next Button") High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="f35c7-163">其中一个很好的例子是 Microsoft Dynamics 365 指南中的“下一步”和“后退”按钮。</span><span class="sxs-lookup"><span data-stu-id="f35c7-163">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span>

<span data-ttu-id="f35c7-164">高频率按钮应...</span><span class="sxs-lookup"><span data-stu-id="f35c7-164">High frequency buttons should...</span></span>
* <span data-ttu-id="f35c7-165">较大，以便更轻松地进行头部凝视</span><span class="sxs-lookup"><span data-stu-id="f35c7-165">be larger buttons, easier to hit with head-gaze</span></span>
* <span data-ttu-id="f35c7-166">保持在视平线附近，以符合人体工程学。</span><span class="sxs-lookup"><span data-stu-id="f35c7-166">stay near eye height to avoid ergonomic straining.</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="f35c7-167">低频率按钮</span><span class="sxs-lookup"><span data-stu-id="f35c7-167">Low frequency buttons</span></span>
<span data-ttu-id="f35c7-168">低频率按钮是整个应用程序中不常与之交互的按钮。</span><span class="sxs-lookup"><span data-stu-id="f35c7-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="f35c7-169">一个很好的例子是用于访问设置菜单的按钮，或用于清除所有工作的按钮。</span><span class="sxs-lookup"><span data-stu-id="f35c7-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="f35c7-170">尽量使这些按钮远离频繁进行头部凝视的路径，以避免意外激活。</span><span class="sxs-lookup"><span data-stu-id="f35c7-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

### <a name="confirmations"></a><span data-ttu-id="f35c7-171">确认</span><span class="sxs-lookup"><span data-stu-id="f35c7-171">Confirmations</span></span>
<span data-ttu-id="f35c7-172">![Microsoft Dynamics 365 指南确认对话框](images/GuidesConfirmation.png "Microsoft Dynamics 365 指南确认对话框")</span><span class="sxs-lookup"><span data-stu-id="f35c7-172">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides Confirmation Dialog")</span></span>

<span data-ttu-id="f35c7-173">当一个动作有重大影响时（如收费、删除工作或启动一个长流程），这对确认要选择按钮非常有用。</span><span class="sxs-lookup"><span data-stu-id="f35c7-173">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span> <span data-ttu-id="f35c7-174">对于头部凝视和停留 UI，确认对话框有一些模式和注意事项：</span><span class="sxs-lookup"><span data-stu-id="f35c7-174">For head-gaze and dwell UIs there are some patterns and considerations for confirmation dialogs:</span></span>

  * <span data-ttu-id="f35c7-175">在主按钮上突出显示选择内容。</span><span class="sxs-lookup"><span data-stu-id="f35c7-175">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="f35c7-176">在选择内容突出显示的同时显示停留目标。</span><span class="sxs-lookup"><span data-stu-id="f35c7-176">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="f35c7-177">对于辅助按钮，在头部凝视上显示停留目标。</span><span class="sxs-lookup"><span data-stu-id="f35c7-177">For the secondary button, reveal the dwell target on head-gaze.</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="f35c7-178">切换按钮</span><span class="sxs-lookup"><span data-stu-id="f35c7-178">Toggle buttons</span></span>
<span data-ttu-id="f35c7-179">切换按钮需要一些细微的逻辑才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="f35c7-179">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="f35c7-180">当用户停留在切换按钮上并激活它时，他们需要退出该按钮然后返回以重启停留逻辑。</span><span class="sxs-lookup"><span data-stu-id="f35c7-180">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="f35c7-181">可切换按钮必须具有明确的活动状态与非活动状态。</span><span class="sxs-lookup"><span data-stu-id="f35c7-181">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

### <a name="list-views"></a><span data-ttu-id="f35c7-182">列表视图</span><span class="sxs-lookup"><span data-stu-id="f35c7-182">List views</span></span>
<span data-ttu-id="f35c7-183">![Microsoft Dynamics 365 指南确认对话框](images/GuidesListView.png "Microsoft Dynamics 365 指南确认对话框")列表视图为头部凝视和停留输入带来了特殊挑战。</span><span class="sxs-lookup"><span data-stu-id="f35c7-183">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesListView.png "Microsoft Dynamics 365 Guides Confirmation Dialog") List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="f35c7-184">用户需要能够浏览内容，而不是感觉必须小心翼翼地绕过停留目标。</span><span class="sxs-lookup"><span data-stu-id="f35c7-184">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span> 

<span data-ttu-id="f35c7-185">设计列表视图的一些提示：</span><span class="sxs-lookup"><span data-stu-id="f35c7-185">Some tips for designing list views:</span></span>
* <span data-ttu-id="f35c7-186">在头部凝视时突出显示整行，但除非头部凝视在特定的停留目标上，否则不会开始停留。</span><span class="sxs-lookup"><span data-stu-id="f35c7-186">have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
* <span data-ttu-id="f35c7-187">仅在突出显示行时显示停留目标以减少视觉干扰。</span><span class="sxs-lookup"><span data-stu-id="f35c7-187">only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
* <span data-ttu-id="f35c7-188">清晰明了并与停留目标的位置保持一致。</span><span class="sxs-lookup"><span data-stu-id="f35c7-188">be clear and consistent with the position of dwell targets.</span></span>
* <span data-ttu-id="f35c7-189">不要一次性显示所有停留目标以避免重复 UI</span><span class="sxs-lookup"><span data-stu-id="f35c7-189">don't show all dwell targets at once to avoid repetitive UI</span></span>
* <span data-ttu-id="f35c7-190">尽可能多地重复使用相同的模式以建立熟悉的用户体验</span><span class="sxs-lookup"><span data-stu-id="f35c7-190">re-use the same pattern as often as possible to establish UX familiarity</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="f35c7-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f35c7-191">See also</span></span>
* [<span data-ttu-id="f35c7-192">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="f35c7-192">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f35c7-193">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="f35c7-193">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="f35c7-194">本能交互</span><span class="sxs-lookup"><span data-stu-id="f35c7-194">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f35c7-195">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="f35c7-195">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="f35c7-196">语音命令</span><span class="sxs-lookup"><span data-stu-id="f35c7-196">Voice commanding</span></span>](voice-design.md)
