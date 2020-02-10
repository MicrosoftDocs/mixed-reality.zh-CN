---
title: 手动菜单
description: 手动菜单允许用户快速为常用函数获取手动连接的 UI。 这些是我们的最佳实践和建议。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手型、菜单、按钮、快速访问、布局
ms.openlocfilehash: 41a936d6041438c1cf1d8e4d4cc8cc30a5167491
ms.sourcegitcommit: 40b37104b0aec4554502dcc7dc430e340a6fa46a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "77092051"
---
# <a name="hand-menu"></a><span data-ttu-id="e281a-105">手动菜单</span><span class="sxs-lookup"><span data-stu-id="e281a-105">Hand menu</span></span>

![Ulnar 端位置](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="e281a-107">手动菜单允许用户快速为常用函数获取手动连接的 UI。</span><span class="sxs-lookup"><span data-stu-id="e281a-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="e281a-108">下面是我们找到的用于手动菜单的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="e281a-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="e281a-109">你还可以在[MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)中找到演示菜单的示例场景。</span><span class="sxs-lookup"><span data-stu-id="e281a-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="e281a-110">行为最佳实践</span><span class="sxs-lookup"><span data-stu-id="e281a-110">Behavior best practices</span></span>
<span data-ttu-id="e281a-111">**答：保持较小的按钮数：** 由于手锁定菜单和眼睛之间的距离接近，而且用户在任何时候都关注相对较小的视觉区域（attentional 的视觉效果约为10度），因此我们建议您保持小的按钮数。</span><span class="sxs-lookup"><span data-stu-id="e281a-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="e281a-112">基于我们的探索，一列包含三个按钮的工作非常有效，即使在用户将其手移到 FOV 的中心时，也会将所有内容保留在视图（FOV）中。</span><span class="sxs-lookup"><span data-stu-id="e281a-112">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="e281a-113">**B. 利用 "快速操作" 菜单：** 提起扶手并维持位置可以轻松地引起 arm 疲劳。</span><span class="sxs-lookup"><span data-stu-id="e281a-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="e281a-114">对需要短交互的菜单使用手锁定的方法。</span><span class="sxs-lookup"><span data-stu-id="e281a-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="e281a-115">如果菜单非常复杂并且需要延长交互时间，请考虑改用世界锁定或正文锁定。</span><span class="sxs-lookup"><span data-stu-id="e281a-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="e281a-116">**C. 按钮/面板角度：** 菜单应以相反的肩和中间开头：这允许自然手移动与菜单之间的交互，并避免在触摸按钮上出现任何难或令人不安的位置。</span><span class="sxs-lookup"><span data-stu-id="e281a-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="e281a-117">**D. 考虑支持单向或无需手动操作：** 不要假设用户的手始终可用。</span><span class="sxs-lookup"><span data-stu-id="e281a-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="e281a-118">当一种或两种方法均不可用时，请考虑使用各种上下文，并确保你的设计帐户适用于这些情况。</span><span class="sxs-lookup"><span data-stu-id="e281a-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="e281a-119">若要支持右手菜单，可以尝试将菜单位置从 "手动锁定" 切换到 "世界锁定" （向下翻向下）。</span><span class="sxs-lookup"><span data-stu-id="e281a-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="e281a-120">对于无需人工使用的方案，请考虑使用语音命令调用手形菜单按钮。</span><span class="sxs-lookup"><span data-stu-id="e281a-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="e281a-121">**E. 双重调用：** 如果使用 "上滑作为事件来触发手形菜单"，则它可能会在您不需要时意外出现（误报），因为人们有意（用于通信和对象操作）和无意地移动它们。</span><span class="sxs-lookup"><span data-stu-id="e281a-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="e281a-122">如果在应用中遇到误报，请考虑添加除手掌事件外的附加步骤，以调用手菜单，如完全打开的手指。</span><span class="sxs-lookup"><span data-stu-id="e281a-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="e281a-123">**F. 避免在手腕（系统主页按钮）附近添加按钮：** 如果菜单按钮离 home 按钮太近，则当与 "手形" 菜单交互时，可能会意外触发该按钮。</span><span class="sxs-lookup"><span data-stu-id="e281a-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="e281a-124">**G. 测试、测试、测试：** 人们具有不同的正文，并具有不同的阈值，可让人感到 discomfort，等等。请确保在上测试你的设计，并从各种人员那里获取反馈。</span><span class="sxs-lookup"><span data-stu-id="e281a-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="e281a-125">手动菜单布局最佳实践</span><span class="sxs-lookup"><span data-stu-id="e281a-125">Hand menu placement best practices</span></span>

<span data-ttu-id="e281a-126">在人剖析中，ulnar 勇气是在 ulna 骨骼附近运行的勇气。</span><span class="sxs-lookup"><span data-stu-id="e281a-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="e281a-127">Ulna 是在 forearm 中找到的一个长骨骼，该骨骼从弯头拉伸到最小手指。</span><span class="sxs-lookup"><span data-stu-id="e281a-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="e281a-128">下面是基于我们的探索推荐的2个位置：</span><span class="sxs-lookup"><span data-stu-id="e281a-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="e281a-129">![Ulnar 端位置](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="e281a-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="e281a-130">**手掌内的 Ulnar**</span><span class="sxs-lookup"><span data-stu-id="e281a-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="e281a-131">此位置是可靠的，因为不会相互重叠。</span><span class="sxs-lookup"><span data-stu-id="e281a-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="e281a-132">这对于准确的手动检测和跟踪至关重要。</span><span class="sxs-lookup"><span data-stu-id="e281a-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e281a-133">![Ulnar 端位置](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="e281a-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="e281a-134">**B. Ulnar 以上的手势**</span><span class="sxs-lookup"><span data-stu-id="e281a-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="e281a-135">此位置对用户非常熟悉，因为他们不需要将其扶手提高到与手形菜单的交互。</span><span class="sxs-lookup"><span data-stu-id="e281a-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="e281a-136">建议将菜单**13cm**置于掌上，并在 ulnar 中对齐按钮。</span><span class="sxs-lookup"><span data-stu-id="e281a-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="e281a-137">阅读有关最佳按钮大小的详细信息</span><span class="sxs-lookup"><span data-stu-id="e281a-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="e281a-138">出于技术原因，我们建议将此位置用于一个必需实现：一旦用户与之交互，开发人员将需要冻结该菜单。</span><span class="sxs-lookup"><span data-stu-id="e281a-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="e281a-139">这将避免 jitteriness 与指针重叠，还允许更快地定位按钮。</span><span class="sxs-lookup"><span data-stu-id="e281a-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="e281a-140">HoloLens 2 相机在彼此独立时可以精确地识别。</span><span class="sxs-lookup"><span data-stu-id="e281a-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="e281a-141">任何重叠的手势都可以导致手形菜单远离定位点位置。</span><span class="sxs-lookup"><span data-stu-id="e281a-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="e281a-142">不建议的菜单位置</span><span class="sxs-lookup"><span data-stu-id="e281a-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="e281a-143">我们使用不同的菜单布局和位置完成了用户研究，**不建议**使用以下菜单位置，查找下面每个研究的缺点：</span><span class="sxs-lookup"><span data-stu-id="e281a-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="e281a-144">![以上 arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="e281a-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="e281a-145">**Arm 之上**</span><span class="sxs-lookup"><span data-stu-id="e281a-145">**Above the arm**</span></span><br>
        <span data-ttu-id="e281a-146">1-难以维护良好的手写跟踪</span><span class="sxs-lookup"><span data-stu-id="e281a-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="e281a-147">2-由于非自然位置导致用户疲劳</span><span class="sxs-lookup"><span data-stu-id="e281a-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e281a-148">![上手指](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="e281a-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="e281a-149">**上手指**</span><span class="sxs-lookup"><span data-stu-id="e281a-149">**Above fingers**</span></span><br>
        <span data-ttu-id="e281a-150">1-疲劳，因为要长时间保留手</span><span class="sxs-lookup"><span data-stu-id="e281a-150">1 - Hand fatigue due to holding out hand for a long time</span></span><br>
        <span data-ttu-id="e281a-151">2-手动跟踪索引和中间指的问题</span><span class="sxs-lookup"><span data-stu-id="e281a-151">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="e281a-152">![以上中心掌托](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="e281a-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="e281a-153">**上方-中心掌托**</span><span class="sxs-lookup"><span data-stu-id="e281a-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="e281a-154">1-由于指针重叠而引起的手动跟踪问题</span><span class="sxs-lookup"><span data-stu-id="e281a-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="e281a-155">疲劳，因为为了与菜单进行交互，保留了长时间的手</span><span class="sxs-lookup"><span data-stu-id="e281a-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e281a-156">![Top 手指](images/TopFingerTip.gif) **top 手指**</span><span class="sxs-lookup"><span data-stu-id="e281a-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="e281a-157">1-手写跟踪问题</span><span class="sxs-lookup"><span data-stu-id="e281a-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="e281a-158">2-疲劳在正常情况上保持手动</span><span class="sxs-lookup"><span data-stu-id="e281a-158">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="e281a-159">3-由于手指间的空间有限，导致按下按钮时出现意外的按键</span><span class="sxs-lookup"><span data-stu-id="e281a-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="e281a-160">Arm ![背面](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="e281a-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="e281a-161">**Arm 背面**</span><span class="sxs-lookup"><span data-stu-id="e281a-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="e281a-162">1-可以意外触发主按钮</span><span class="sxs-lookup"><span data-stu-id="e281a-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="e281a-163">2-不是自然或舒适的位置</span><span class="sxs-lookup"><span data-stu-id="e281a-163">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e281a-164">Unity 中的 MRTK （混合现实工具包）的菜单</span><span class="sxs-lookup"><span data-stu-id="e281a-164">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="e281a-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为手形菜单提供脚本和示例场景。</span><span class="sxs-lookup"><span data-stu-id="e281a-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="e281a-166">HandConstraintPalmUp 求解器脚本允许你轻松地将任何对象附加到各种可配置选项。</span><span class="sxs-lookup"><span data-stu-id="e281a-166">HandConstraintPalmUp solver script allows you easily attach any objects to the hands with various configurable options.</span></span>

* [<span data-ttu-id="e281a-167">MRTK HandConstraint 和 HandConstraintPalmUp 的菜单</span><span class="sxs-lookup"><span data-stu-id="e281a-167">MRTK - Hand Menu with HandConstraint and HandConstraintPalmUp </span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a><span data-ttu-id="e281a-168">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e281a-168">See also</span></span>

* [<span data-ttu-id="e281a-169">光标</span><span class="sxs-lookup"><span data-stu-id="e281a-169">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e281a-170">手部射线</span><span class="sxs-lookup"><span data-stu-id="e281a-170">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="e281a-171">Button</span><span class="sxs-lookup"><span data-stu-id="e281a-171">Button</span></span>](button.md)
* [<span data-ttu-id="e281a-172">可交互对象</span><span class="sxs-lookup"><span data-stu-id="e281a-172">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e281a-173">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="e281a-173">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e281a-174">操作</span><span class="sxs-lookup"><span data-stu-id="e281a-174">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e281a-175">手动菜单</span><span class="sxs-lookup"><span data-stu-id="e281a-175">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="e281a-176">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="e281a-176">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="e281a-177">对象集合</span><span class="sxs-lookup"><span data-stu-id="e281a-177">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e281a-178">语音命令</span><span class="sxs-lookup"><span data-stu-id="e281a-178">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="e281a-179">键盘</span><span class="sxs-lookup"><span data-stu-id="e281a-179">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="e281a-180">工具提示</span><span class="sxs-lookup"><span data-stu-id="e281a-180">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="e281a-181">平板</span><span class="sxs-lookup"><span data-stu-id="e281a-181">Slate</span></span>](slate.md)
* [<span data-ttu-id="e281a-182">滑块</span><span class="sxs-lookup"><span data-stu-id="e281a-182">Slider</span></span>](slider.md)
* [<span data-ttu-id="e281a-183">着色器</span><span class="sxs-lookup"><span data-stu-id="e281a-183">Shader</span></span>](shader.md)
* [<span data-ttu-id="e281a-184">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="e281a-184">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e281a-185">显示进度</span><span class="sxs-lookup"><span data-stu-id="e281a-185">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="e281a-186">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="e281a-186">Surface magnetism</span></span>](surface-magnetism.md)
