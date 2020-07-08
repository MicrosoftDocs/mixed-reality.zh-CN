---
title: 手动菜单
description: 手动菜单允许用户快速为常用函数获取手动连接的 UI。 这些是我们的最佳实践和建议。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 手型、菜单、按钮、快速访问、布局
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061161"
---
# <a name="hand-menu"></a><span data-ttu-id="f229e-105">手动菜单</span><span class="sxs-lookup"><span data-stu-id="f229e-105">Hand menu</span></span>

![Ulnar 端位置](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="f229e-107">"手形" 菜单是 HoloLens 2 中最独特的 UX 模式之一。</span><span class="sxs-lookup"><span data-stu-id="f229e-107">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="f229e-108">它可让你快速打开手动连接的 UI。</span><span class="sxs-lookup"><span data-stu-id="f229e-108">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="f229e-109">由于可以随时访问它，并且可以轻松地显示和隐藏，因此对于快速操作非常有用。</span><span class="sxs-lookup"><span data-stu-id="f229e-109">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="f229e-110">你将在下面的列表中找到建议使用的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="f229e-110">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="f229e-111">你还可以在[MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)中找到演示菜单的示例场景。</span><span class="sxs-lookup"><span data-stu-id="f229e-111">You can also find an example scene demonstrating the hand menu in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span></span>

<br>


---

## <a name="best-practices"></a><span data-ttu-id="f229e-112">最佳做法</span><span class="sxs-lookup"><span data-stu-id="f229e-112">Best practices</span></span>
<span data-ttu-id="f229e-113">**使按钮数保持较小**</span><span class="sxs-lookup"><span data-stu-id="f229e-113">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="f229e-114">由于手锁定菜单和眼睛之间的距离，以及用户在任何时间重点关注相对较小的视觉区域（attentional 的视觉效果约为10度），因此我们建议您将按钮数保持为小。</span><span class="sxs-lookup"><span data-stu-id="f229e-114">Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="f229e-115">基于我们的探索，一列包含三个按钮的工作非常有效，即使在用户将其手移到 FOV 的中心时，也会将所有内容保留在视图（FOV）中。</span><span class="sxs-lookup"><span data-stu-id="f229e-115">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="f229e-116">**利用快捷菜单执行快速操作**</span><span class="sxs-lookup"><span data-stu-id="f229e-116">**Utilize hand menu for quick action**</span></span> 

<span data-ttu-id="f229e-117">提起 arm 并维持位置可能很容易导致 arm 疲劳。</span><span class="sxs-lookup"><span data-stu-id="f229e-117">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="f229e-118">对需要短交互的菜单使用手锁定的方法。</span><span class="sxs-lookup"><span data-stu-id="f229e-118">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="f229e-119">如果菜单非常复杂并且需要延长交互时间，请考虑改用世界锁定或正文锁定。</span><span class="sxs-lookup"><span data-stu-id="f229e-119">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="f229e-120">**按钮/面板角度**</span><span class="sxs-lookup"><span data-stu-id="f229e-120">**Button / Panel angle**</span></span>

<span data-ttu-id="f229e-121">菜单应以与之相对的肩和中间的方式为布告栏：这允许自然的手移动与菜单之间的交互，并在触摸按钮时避免任何难或令人不安的位置。</span><span class="sxs-lookup"><span data-stu-id="f229e-121">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="f229e-122">**考虑支持单向或无需操作**</span><span class="sxs-lookup"><span data-stu-id="f229e-122">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="f229e-123">不要假设用户的手始终可用。</span><span class="sxs-lookup"><span data-stu-id="f229e-123">Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="f229e-124">当一种或两种方法均不可用时，请考虑使用各种上下文，并确保你的设计帐户适用于这些情况。</span><span class="sxs-lookup"><span data-stu-id="f229e-124">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="f229e-125">若要支持右手菜单，可以尝试将菜单位置从 "手动锁定" 切换到 "世界锁定" （向下翻向下）。</span><span class="sxs-lookup"><span data-stu-id="f229e-125">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="f229e-126">对于无需人工使用的方案，请考虑使用语音命令调用手形菜单。</span><span class="sxs-lookup"><span data-stu-id="f229e-126">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="f229e-127">**避免在手腕（系统主页按钮）附近添加按钮**</span><span class="sxs-lookup"><span data-stu-id="f229e-127">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="f229e-128">如果将 "手形" 菜单按钮置于 "主页" 按钮附近，则可能会在与 "手形" 菜单交互时意外触发。</span><span class="sxs-lookup"><span data-stu-id="f229e-128">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="f229e-129">包含大型和复杂 UI 控件的菜单</span><span class="sxs-lookup"><span data-stu-id="f229e-129">Hand menu with large and complex UI controls</span></span>
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="f229e-130">建议限制手动附加菜单上的按钮或 UI 控件的数目。</span><span class="sxs-lookup"><span data-stu-id="f229e-130">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="f229e-131">这是因为，与大量 UI 元素的扩展交互可能会导致 arm 疲劳。</span><span class="sxs-lookup"><span data-stu-id="f229e-131">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="f229e-132">如果你的体验需要大菜单，请为用户提供一种简单的方式来锁定菜单。</span><span class="sxs-lookup"><span data-stu-id="f229e-132">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="f229e-133">我们建议的一种方法是在离开或离开用户时，进行全球锁定后菜单。</span><span class="sxs-lookup"><span data-stu-id="f229e-133">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="f229e-134">第二种方法是允许用户直接抓住菜单。</span><span class="sxs-lookup"><span data-stu-id="f229e-134">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="f229e-135">当用户释放菜单时，菜单应为 "全局锁定"。</span><span class="sxs-lookup"><span data-stu-id="f229e-135">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="f229e-136">这样一来，用户就可以在很长一段时间内轻松且自信地与各种 UI 元素交互。</span><span class="sxs-lookup"><span data-stu-id="f229e-136">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="f229e-137">当菜单处于全局锁定状态时，请确保提供移动菜单的方法，并在不再需要菜单时关闭菜单。</span><span class="sxs-lookup"><span data-stu-id="f229e-137">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="f229e-138">通过在菜单边或顶部提供控点，使菜单可移动。</span><span class="sxs-lookup"><span data-stu-id="f229e-138">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="f229e-139">添加 "关闭" 按钮以允许菜单关闭。</span><span class="sxs-lookup"><span data-stu-id="f229e-139">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="f229e-140">允许菜单在用户正面朝用户时重新附加到手。</span><span class="sxs-lookup"><span data-stu-id="f229e-140">Allow for the menu to re-attach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="f229e-141">我们还建议要求用户 gazes，以防止错误激活（见下文）。</span><span class="sxs-lookup"><span data-stu-id="f229e-141">We also recommend requiring that the users gazes at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="f229e-142">**显示可用性问题的大菜单**</span><span class="sxs-lookup"><span data-stu-id="f229e-142">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="f229e-143">**现有的全球锁定菜单**</span><span class="sxs-lookup"><span data-stu-id="f229e-143">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="f229e-144">**手动抓取 & 拉取到世界上-锁定菜单**</span><span class="sxs-lookup"><span data-stu-id="f229e-144">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="f229e-145">如何防止错误激活</span><span class="sxs-lookup"><span data-stu-id="f229e-145">How to prevent false activation</span></span>

<span data-ttu-id="f229e-146">如果使用 "上滑作为事件来触发手形菜单"，则它可能会在您不需要它时意外出现（误报），因为人们有意（对于通信和对象操作）和无意地移动其手。</span><span class="sxs-lookup"><span data-stu-id="f229e-146">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="f229e-147">若要减少错误激活，请添加除手掌事件外的附加步骤，以调用手形菜单（如完全打开的手指或用户有意 gazing）。</span><span class="sxs-lookup"><span data-stu-id="f229e-147">To reduce false activations, add an additional step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="f229e-148">**需要单层掌**</span><span class="sxs-lookup"><span data-stu-id="f229e-148">**Require Flat Palm**</span></span>

<span data-ttu-id="f229e-149">通过要求平整的张开手，可以防止在用户在环境中进行通信的过程中操作对象或手势时出现错误激活。</span><span class="sxs-lookup"><span data-stu-id="f229e-149">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="f229e-150">**需要注视**</span><span class="sxs-lookup"><span data-stu-id="f229e-150">**Require Gaze**</span></span>

<span data-ttu-id="f229e-151">通过要求用户随时注视（使用目视或眼睛），它可防止错误激活，因为用户必须有意将其注意力视为辅助激活步骤（具有可用于允许用户舒适的可调距离阈值）。</span><span class="sxs-lookup"><span data-stu-id="f229e-151">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations due to the user having to intentionally direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="f229e-152">手动菜单布局最佳实践</span><span class="sxs-lookup"><span data-stu-id="f229e-152">Hand menu placement best practices</span></span>

<span data-ttu-id="f229e-153">在人剖析中，ulnar 勇气是在 ulna 骨骼附近运行的勇气。</span><span class="sxs-lookup"><span data-stu-id="f229e-153">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="f229e-154">Ulna 是在 forearm 中找到的一个长骨骼，该骨骼从弯头拉伸到最小手指。</span><span class="sxs-lookup"><span data-stu-id="f229e-154">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="f229e-155">下面是基于我们的探索推荐的2个位置：</span><span class="sxs-lookup"><span data-stu-id="f229e-155">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="f229e-156">![Ulnar 端位置](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="f229e-156">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="f229e-157">**手掌内的 Ulnar**</span><span class="sxs-lookup"><span data-stu-id="f229e-157">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="f229e-158">此位置是可靠的，因为不会相互重叠。</span><span class="sxs-lookup"><span data-stu-id="f229e-158">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="f229e-159">这对于准确的手动检测和跟踪至关重要。</span><span class="sxs-lookup"><span data-stu-id="f229e-159">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f229e-160">![Ulnar 端位置](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="f229e-160">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="f229e-161">**B. Ulnar 以上的手势**</span><span class="sxs-lookup"><span data-stu-id="f229e-161">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="f229e-162">此位置对用户非常熟悉，因为他们不需要将其扶手提高到与手形菜单的交互。</span><span class="sxs-lookup"><span data-stu-id="f229e-162">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="f229e-163">建议将菜单**13cm**置于掌上，并在 ulnar 中对齐按钮。</span><span class="sxs-lookup"><span data-stu-id="f229e-163">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="f229e-164">阅读有关最佳按钮大小的详细信息</span><span class="sxs-lookup"><span data-stu-id="f229e-164">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="f229e-165">出于技术原因，我们建议将此位置用于一个必需实现：一旦用户与之交互，开发人员将需要冻结该菜单。</span><span class="sxs-lookup"><span data-stu-id="f229e-165">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="f229e-166">这将避免 jitteriness 与指针重叠，还允许更快地定位按钮。</span><span class="sxs-lookup"><span data-stu-id="f229e-166">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="f229e-167">HoloLens 2 相机在彼此独立时可以精确地识别。</span><span class="sxs-lookup"><span data-stu-id="f229e-167">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="f229e-168">任何重叠的手势都可以导致手形菜单远离定位点位置。</span><span class="sxs-lookup"><span data-stu-id="f229e-168">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="f229e-169">不建议的菜单位置</span><span class="sxs-lookup"><span data-stu-id="f229e-169">Menu positions that are not recommended</span></span>
<span data-ttu-id="f229e-170">我们使用不同的菜单布局和位置完成了用户研究，**不建议**使用以下菜单位置，查找下面每个研究的缺点：</span><span class="sxs-lookup"><span data-stu-id="f229e-170">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="f229e-171">![上方 arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="f229e-171">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="f229e-172">**Arm 之上**</span><span class="sxs-lookup"><span data-stu-id="f229e-172">**Above the arm**</span></span><br>
        <span data-ttu-id="f229e-173">1-难以维护良好的手写跟踪</span><span class="sxs-lookup"><span data-stu-id="f229e-173">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="f229e-174">2-由于非自然位置导致用户疲劳</span><span class="sxs-lookup"><span data-stu-id="f229e-174">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f229e-175">![上手指](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="f229e-175">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="f229e-176">**上手指**</span><span class="sxs-lookup"><span data-stu-id="f229e-176">**Above fingers**</span></span><br>
        <span data-ttu-id="f229e-177">1-疲劳，因为要长时间保留手</span><span class="sxs-lookup"><span data-stu-id="f229e-177">1 - Hand fatigue due to holding out hand for a long time</span></span><br>
        <span data-ttu-id="f229e-178">2-手动跟踪索引和中间指的问题</span><span class="sxs-lookup"><span data-stu-id="f229e-178">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="f229e-179">![上方中心掌](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="f229e-179">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="f229e-180">**上方-中心掌托**</span><span class="sxs-lookup"><span data-stu-id="f229e-180">**Above-center palm**</span></span><br>
        <span data-ttu-id="f229e-181">1-由于指针重叠而引起的手动跟踪问题</span><span class="sxs-lookup"><span data-stu-id="f229e-181">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="f229e-182">疲劳，因为为了与菜单进行交互，保留了长时间的手</span><span class="sxs-lookup"><span data-stu-id="f229e-182">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f229e-183">![Top 手指 ](images/TopFingerTip.gif) **top 手指**</span><span class="sxs-lookup"><span data-stu-id="f229e-183">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="f229e-184">1-手写跟踪问题</span><span class="sxs-lookup"><span data-stu-id="f229e-184">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="f229e-185">2-疲劳在正常情况上保持手动</span><span class="sxs-lookup"><span data-stu-id="f229e-185">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="f229e-186">3-由于手指间的空间有限，导致按下按钮时出现意外的按键</span><span class="sxs-lookup"><span data-stu-id="f229e-186">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="f229e-187">![Arm 背面](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="f229e-187">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="f229e-188">**Arm 背面**</span><span class="sxs-lookup"><span data-stu-id="f229e-188">**Back of the arm**</span></span><br>
        <span data-ttu-id="f229e-189">1-可以意外触发主按钮</span><span class="sxs-lookup"><span data-stu-id="f229e-189">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="f229e-190">2-不是自然或舒适的位置</span><span class="sxs-lookup"><span data-stu-id="f229e-190">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f229e-191">Unity 中的 MRTK （混合现实工具包）的菜单</span><span class="sxs-lookup"><span data-stu-id="f229e-191">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="f229e-192">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为手形菜单提供脚本和示例场景。</span><span class="sxs-lookup"><span data-stu-id="f229e-192">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="f229e-193">HandConstraintPalmUp 求解器脚本允许您将任何对象附加到各种可配置选项。</span><span class="sxs-lookup"><span data-stu-id="f229e-193">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="f229e-194">MRTK 的手形菜单示例包含有用的选项，例如，用于防止错误激活的平面掌和注视要求。</span><span class="sxs-lookup"><span data-stu-id="f229e-194">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="f229e-195">手动菜单文档</span><span class="sxs-lookup"><span data-stu-id="f229e-195">Hand Menu Documentations</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [<span data-ttu-id="f229e-196">手型菜单示例场景</span><span class="sxs-lookup"><span data-stu-id="f229e-196">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="f229e-197">可以在 HoloLens 2 中试用带有 MRTK 示例中心应用的菜单示例。</span><span class="sxs-lookup"><span data-stu-id="f229e-197">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="f229e-198">MRTK 示例中心中的手形菜单场景</span><span class="sxs-lookup"><span data-stu-id="f229e-198">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a><span data-ttu-id="f229e-199">请参阅</span><span class="sxs-lookup"><span data-stu-id="f229e-199">See also</span></span>

* [<span data-ttu-id="f229e-200">光标</span><span class="sxs-lookup"><span data-stu-id="f229e-200">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f229e-201">手部射线</span><span class="sxs-lookup"><span data-stu-id="f229e-201">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f229e-202">Button</span><span class="sxs-lookup"><span data-stu-id="f229e-202">Button</span></span>](button.md)
* [<span data-ttu-id="f229e-203">可交互对象</span><span class="sxs-lookup"><span data-stu-id="f229e-203">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f229e-204">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="f229e-204">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f229e-205">操作</span><span class="sxs-lookup"><span data-stu-id="f229e-205">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f229e-206">手动菜单</span><span class="sxs-lookup"><span data-stu-id="f229e-206">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f229e-207">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="f229e-207">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f229e-208">对象集合</span><span class="sxs-lookup"><span data-stu-id="f229e-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f229e-209">语音命令</span><span class="sxs-lookup"><span data-stu-id="f229e-209">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f229e-210">键盘</span><span class="sxs-lookup"><span data-stu-id="f229e-210">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f229e-211">工具提示</span><span class="sxs-lookup"><span data-stu-id="f229e-211">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f229e-212">平板</span><span class="sxs-lookup"><span data-stu-id="f229e-212">Slate</span></span>](slate.md)
* [<span data-ttu-id="f229e-213">滑块</span><span class="sxs-lookup"><span data-stu-id="f229e-213">Slider</span></span>](slider.md)
* [<span data-ttu-id="f229e-214">着色器</span><span class="sxs-lookup"><span data-stu-id="f229e-214">Shader</span></span>](shader.md)
* [<span data-ttu-id="f229e-215">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="f229e-215">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f229e-216">显示进度</span><span class="sxs-lookup"><span data-stu-id="f229e-216">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f229e-217">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="f229e-217">Surface magnetism</span></span>](surface-magnetism.md)
