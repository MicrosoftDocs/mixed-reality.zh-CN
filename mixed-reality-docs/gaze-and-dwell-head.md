---
title: 头部凝视和停留
description: 头部凝视和停留输入模型概述
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: 混合现实, 凝视, 停留, 交互, 设计
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439308"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="75ed0-104">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="75ed0-104">Head-gaze and dwell</span></span>

<span data-ttu-id="75ed0-105">手拿工具和零件，手势可能是没有意义或无法实现。</span><span class="sxs-lookup"><span data-stu-id="75ed0-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="75ed0-106">语音命令（例如手势）在某些情况下可能不可靠，例如在过度嘈杂的条件下。</span><span class="sxs-lookup"><span data-stu-id="75ed0-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="75ed0-107">此外，使用语音控制计算机并不是普遍常见的，但正日益盛行！</span><span class="sxs-lookup"><span data-stu-id="75ed0-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="75ed0-108">头部凝视和停留提供最熟悉且易于掌握的机制，可在 HoloLens 上实现抬头操作和解放双手的操作。</span><span class="sxs-lookup"><span data-stu-id="75ed0-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="75ed0-109">此外，头部凝视和停留 100% 可靠，与操作环境中不受噪声干扰和静音约束。</span><span class="sxs-lookup"><span data-stu-id="75ed0-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="75ed0-110">场景</span><span class="sxs-lookup"><span data-stu-id="75ed0-110">Scenarios</span></span>

<span data-ttu-id="75ed0-111">在人的手忙于处理其他任务的情况下，打印头和停留 transact-sql，而语音没有100% 的可靠性或由于环境或社交限制而无法使用。</span><span class="sxs-lookup"><span data-stu-id="75ed0-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="75ed0-112">一个很好的例子是穿戴 HoloLens 的人在修理汽车发动机时获取参考信息。</span><span class="sxs-lookup"><span data-stu-id="75ed0-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="75ed0-113">倚靠在发动机舱内时，他们的手拿着工具或支撑着身体。</span><span class="sxs-lookup"><span data-stu-id="75ed0-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="75ed0-114">车库空间很大，工具不断敲打声和嘈杂声，难以使用语音命令。</span><span class="sxs-lookup"><span data-stu-id="75ed0-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="75ed0-115">通过打印头和停留，使用 HoloLens 的人员可以放心地浏览其参考材料，而不会中断工作流。</span><span class="sxs-lookup"><span data-stu-id="75ed0-115">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="75ed0-116">设备支持</span><span class="sxs-lookup"><span data-stu-id="75ed0-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="75ed0-117"><strong>输入模型</strong></span><span class="sxs-lookup"><span data-stu-id="75ed0-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="75ed0-118"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="75ed0-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="75ed0-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="75ed0-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="75ed0-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="75ed0-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="75ed0-121">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="75ed0-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="75ed0-122">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="75ed0-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="75ed0-123">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="75ed0-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="75ed0-124">✔️ 推荐</span><span class="sxs-lookup"><span data-stu-id="75ed0-124">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="75ed0-125">设计原则</span><span class="sxs-lookup"><span data-stu-id="75ed0-125">Design principles</span></span>

<span data-ttu-id="75ed0-126">**避免 "注视武器"**</span><span class="sxs-lookup"><span data-stu-id="75ed0-126">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="75ed0-127">头部凝视和停留需要直观的视觉反馈，但反馈过多会令人焦虑。</span><span class="sxs-lookup"><span data-stu-id="75ed0-127">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="75ed0-128">反馈应有助于用户了解其目标，但不会根据其意图自动选择。</span><span class="sxs-lookup"><span data-stu-id="75ed0-128">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="75ed0-129">阅读文本、图标和标签需要额外考虑，以便为客户提供在进行选择之前吸收信息的空间。</span><span class="sxs-lookup"><span data-stu-id="75ed0-129">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
<span data-ttu-id="75ed0-130">**查找 Goldilocks 速度**</span><span class="sxs-lookup"><span data-stu-id="75ed0-130">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="75ed0-131">停留交互根据对导航的影响而使用不同的计时器 - 更频繁使用的功能通常将受益于更快的填充时间，而更具重要性的功能可能受益于更长的填充时间。</span><span class="sxs-lookup"><span data-stu-id="75ed0-131">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="75ed0-132">当使用填充效果来显示这些计时器时，填充颜色的动画曲线可对感知快速填充时间产生正面影响。</span><span class="sxs-lookup"><span data-stu-id="75ed0-132">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="75ed0-133">应进行仔细考虑，使用户能够基于快速/中速/慢速填充速度覆盖来做出决策。</span><span class="sxs-lookup"><span data-stu-id="75ed0-133">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="75ed0-134">**假设 "无-否" 为 yo-yo 效果**</span><span class="sxs-lookup"><span data-stu-id="75ed0-134">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="75ed0-135">摇摆不定效应是一种令人不适的头部运动模式，当内容的位置以及头部凝视和停留控制迫使人们不断上下反复看时，即会出现这种效应。</span><span class="sxs-lookup"><span data-stu-id="75ed0-135">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="75ed0-136">例如，使用底部的 "注视" 和 "停留" 按钮的列表导航到 "停留" 循环，查找结果，查看 "停留" 等。这种结果模式不舒服，应避免将导航控件置于需要更少恢复的集中位置。</span><span class="sxs-lookup"><span data-stu-id="75ed0-136">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="75ed0-137">相对于效果放置停留按钮对于确保舒适性非常重要。</span><span class="sxs-lookup"><span data-stu-id="75ed0-137">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

<br>

---


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="75ed0-138">UX 指南和最佳做法</span><span class="sxs-lookup"><span data-stu-id="75ed0-138">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="75ed0-139">目标大小</span><span class="sxs-lookup"><span data-stu-id="75ed0-139">Target sizes</span></span>
  <span data-ttu-id="75ed0-140">为了能够轻松地访问，打印头和停留目标需要足够大，以便能够轻松地查看，并在规定时间的目标位置上保持一头稳定。</span><span class="sxs-lookup"><span data-stu-id="75ed0-140">To be easily accessible, head-gaze and dwell targets need to be large enough to comfortably look at, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="75ed0-141">建议最小目标大小为2度，以获得最舒适的体验。</span><span class="sxs-lookup"><span data-stu-id="75ed0-141">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="75ed0-142">视觉反馈</span><span class="sxs-lookup"><span data-stu-id="75ed0-142">Visual feedback</span></span>

<span data-ttu-id="75ed0-143">当使用径向填充来表示停留计时器时，请从按钮中心开始。</span><span class="sxs-lookup"><span data-stu-id="75ed0-143">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="75ed0-144">与在不同按钮上均采用不同方向相比，一致的响应可减少混淆。</span><span class="sxs-lookup"><span data-stu-id="75ed0-144">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="75ed0-145">对于定向交互（例如，向上/向下/向左/向右导航等），可以不遵循此规则。</span><span class="sxs-lookup"><span data-stu-id="75ed0-145">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="75ed0-146">例如，在 Microsoft Dynamics 365 指南中左右两侧填充“下一步”/“后退”时例外。</span><span class="sxs-lookup"><span data-stu-id="75ed0-146">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="75ed0-147">考虑从外部反径向填充，例如关闭按钮。</span><span class="sxs-lookup"><span data-stu-id="75ed0-147">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="75ed0-148">按下按钮的反向效果是一种出色的视觉模式。</span><span class="sxs-lookup"><span data-stu-id="75ed0-148">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="75ed0-149">渐进式披露</span><span class="sxs-lookup"><span data-stu-id="75ed0-149">Progressive disclosure</span></span>

<span data-ttu-id="75ed0-150">渐进式披露是指只显示与交互的每个阶段相关的详细信息。</span><span class="sxs-lookup"><span data-stu-id="75ed0-150">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="75ed0-151">对于停留，这意味着停留目标在突出显示时揭露（例如，在列表控件中）。</span><span class="sxs-lookup"><span data-stu-id="75ed0-151">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="75ed0-152">过大的目标</span><span class="sxs-lookup"><span data-stu-id="75ed0-152">Oversized targets</span></span>
<span data-ttu-id="75ed0-153">停留区域可以比非活动图标大，以便于使用，例如 Microsoft Dynamics 365 指南中的“后退”按钮。</span><span class="sxs-lookup"><span data-stu-id="75ed0-153">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="75ed0-154">通过延迟反馈防止闪烁</span><span class="sxs-lookup"><span data-stu-id="75ed0-154">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="75ed0-155">在开始视觉反馈之前使用短暂的延迟，以避免当有人经过停留目标时闪烁。</span><span class="sxs-lookup"><span data-stu-id="75ed0-155">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="75ed0-156">对于按钮经常交互的按钮，保持延迟非常短，使应用程序感觉被动。</span><span class="sxs-lookup"><span data-stu-id="75ed0-156">For buttons interacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="75ed0-157">对于不常交互的按钮，更长的延迟可能适用于避免出现 twitchy 的界面。</span><span class="sxs-lookup"><span data-stu-id="75ed0-157">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>


<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="75ed0-158">UI 模式</span><span class="sxs-lookup"><span data-stu-id="75ed0-158">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="75ed0-159">高频率按钮</span><span class="sxs-lookup"><span data-stu-id="75ed0-159">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="75ed0-160">高频率按钮是通常在整个应用程序中使用的按钮。</span><span class="sxs-lookup"><span data-stu-id="75ed0-160">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="75ed0-161">其中一个很好的例子是 Microsoft Dynamics 365 指南中的“下一步”和“后退”按钮。</span><span class="sxs-lookup"><span data-stu-id="75ed0-161">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="75ed0-162">**针对**</span><span class="sxs-lookup"><span data-stu-id="75ed0-162">**Recommendations**</span></span><br>
  * <span data-ttu-id="75ed0-163">高频率按钮应该很大，更容易碰到打印头</span><span class="sxs-lookup"><span data-stu-id="75ed0-163">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="75ed0-164">保持近眼睛，以避免人体工学。</span><span class="sxs-lookup"><span data-stu-id="75ed0-164">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="75ed0-165">*图像： Microsoft Dynamics 365 "下一步" 按钮*</span><span class="sxs-lookup"><span data-stu-id="75ed0-165">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 "下一步" 按钮](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="75ed0-167">低频率按钮</span><span class="sxs-lookup"><span data-stu-id="75ed0-167">Low frequency buttons</span></span>
<span data-ttu-id="75ed0-168">低频率按钮是整个应用程序中不常与之交互的按钮。</span><span class="sxs-lookup"><span data-stu-id="75ed0-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="75ed0-169">一个很好的例子是用于访问设置菜单的按钮，或用于清除所有工作的按钮。</span><span class="sxs-lookup"><span data-stu-id="75ed0-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="75ed0-170">尽量使这些按钮远离频繁进行头部凝视的路径，以避免意外激活。</span><span class="sxs-lookup"><span data-stu-id="75ed0-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="75ed0-171">确认</span><span class="sxs-lookup"><span data-stu-id="75ed0-171">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="75ed0-172">当一个动作有重大影响时（如收费、删除工作或启动一个长流程），这对确认要选择按钮非常有用。</span><span class="sxs-lookup"><span data-stu-id="75ed0-172">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="75ed0-173">**针对**</span><span class="sxs-lookup"><span data-stu-id="75ed0-173">**Recommendations**</span></span><br>
  * <span data-ttu-id="75ed0-174">在主按钮上突出显示选择内容。</span><span class="sxs-lookup"><span data-stu-id="75ed0-174">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="75ed0-175">在选择内容突出显示的同时显示停留目标。</span><span class="sxs-lookup"><span data-stu-id="75ed0-175">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="75ed0-176">对于辅助按钮，在头部凝视上显示停留目标。</span><span class="sxs-lookup"><span data-stu-id="75ed0-176">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="75ed0-177">*映像： Microsoft Dynamics 365 指南确认对话框*</span><span class="sxs-lookup"><span data-stu-id="75ed0-177">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南确认对话框](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="75ed0-179">切换按钮</span><span class="sxs-lookup"><span data-stu-id="75ed0-179">Toggle buttons</span></span>
<span data-ttu-id="75ed0-180">切换按钮需要一些细微的逻辑才能正常工作。</span><span class="sxs-lookup"><span data-stu-id="75ed0-180">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="75ed0-181">当用户停留在切换按钮上并激活它时，他们需要退出该按钮然后返回以重启停留逻辑。</span><span class="sxs-lookup"><span data-stu-id="75ed0-181">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="75ed0-182">可切换按钮必须具有明确的活动状态与非活动状态。</span><span class="sxs-lookup"><span data-stu-id="75ed0-182">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="75ed0-183">列表视图</span><span class="sxs-lookup"><span data-stu-id="75ed0-183">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="75ed0-184">列表视图为打印头和停留输入提供了一个特定的挑战。</span><span class="sxs-lookup"><span data-stu-id="75ed0-184">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="75ed0-185">用户需要能够浏览内容，而不是感觉必须小心翼翼地绕过停留目标。</span><span class="sxs-lookup"><span data-stu-id="75ed0-185">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="75ed0-186">**针对**</span><span class="sxs-lookup"><span data-stu-id="75ed0-186">**Recommendations**</span></span><br>
  * <span data-ttu-id="75ed0-187">在 gazed 但不开始停留在特定停留目标上时，将整个行突出显示，但不会开始停留。</span><span class="sxs-lookup"><span data-stu-id="75ed0-187">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="75ed0-188">突出显示行时，仅显示停留目标，以减少视觉干扰。</span><span class="sxs-lookup"><span data-stu-id="75ed0-188">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="75ed0-189">清楚地与停留目标的位置一致。</span><span class="sxs-lookup"><span data-stu-id="75ed0-189">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="75ed0-190">不要一次显示所有停留目标，以避免重复的 UI。</span><span class="sxs-lookup"><span data-stu-id="75ed0-190">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="75ed0-191">尽可能频繁地使用相同的模式，以建立 UX 熟悉。</span><span class="sxs-lookup"><span data-stu-id="75ed0-191">Re-use the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="75ed0-192">*映像： Microsoft Dynamics 365 指南列表*</span><span class="sxs-lookup"><span data-stu-id="75ed0-192">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 指南列表](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="75ed0-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="75ed0-194">See also</span></span>
* [<span data-ttu-id="75ed0-195">注视并提交</span><span class="sxs-lookup"><span data-stu-id="75ed0-195">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="75ed0-196">直接操作</span><span class="sxs-lookup"><span data-stu-id="75ed0-196">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="75ed0-197">动手手势</span><span class="sxs-lookup"><span data-stu-id="75ed0-197">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="75ed0-198">动手并提交</span><span class="sxs-lookup"><span data-stu-id="75ed0-198">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="75ed0-199">本能交互</span><span class="sxs-lookup"><span data-stu-id="75ed0-199">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="75ed0-200">语音输入</span><span class="sxs-lookup"><span data-stu-id="75ed0-200">Voice input</span></span>](voice-input.md)
