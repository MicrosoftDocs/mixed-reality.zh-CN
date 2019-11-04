---
title: 光标
description: 对于目标向量，光标或指示器可为用户提供持续的反馈，以了解 HoloLens 对其意图的了解情况。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens （第一代），HoloLens 2，混合现实，光标，定位，注视，手势
ms.openlocfilehash: ef011d8400de1e23db3d6fb4b0f2a853d787ae86
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435808"
---
# <a name="cursors"></a><span data-ttu-id="d374d-104">光标</span><span class="sxs-lookup"><span data-stu-id="d374d-104">Cursors</span></span>

<span data-ttu-id="d374d-105">当前目标向量的光标或指示器可为用户提供持续的反馈，以了解头戴显示在该时间的位置。</span><span class="sxs-lookup"><span data-stu-id="d374d-105">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="d374d-106">光标允许用户了解其当前目标点，并作为反馈来指示哪个区域、全息图或点将响应输入。</span><span class="sxs-lookup"><span data-stu-id="d374d-106">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="d374d-107">它是设备理解用户注意的数字表示形式（尽管这可能不同于确定其意图的任何内容）。</span><span class="sxs-lookup"><span data-stu-id="d374d-107">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="d374d-108">游标提供的反馈为用户提供预测系统响应方式的能力，使用该信号作为反馈来更好地传达设备对设备的意图，并最终更有把握其交互。</span><span class="sxs-lookup"><span data-stu-id="d374d-108">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="d374d-109">有三种类型的游标：**手指、光线**和**打印头**。</span><span class="sxs-lookup"><span data-stu-id="d374d-109">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="d374d-110">这些指针在 HoloLens、HoloLens 2 和沉浸式耳机上使用不同的输入情态。</span><span class="sxs-lookup"><span data-stu-id="d374d-110">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="d374d-111">下面是针对每种类型的耳机和交互模型使用哪种类型的游标的指导。</span><span class="sxs-lookup"><span data-stu-id="d374d-111">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="d374d-112">在混合现实工具包（MRTK）中，我们创建了拖放游标模块，以帮助你生成正确的指针体验。</span><span class="sxs-lookup"><span data-stu-id="d374d-112">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="d374d-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="d374d-113">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d374d-114"><strong>具有</strong></span><span class="sxs-lookup"><span data-stu-id="d374d-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d374d-115"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="d374d-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d374d-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d374d-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d374d-117"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d374d-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d374d-118">手指光标</span><span class="sxs-lookup"><span data-stu-id="d374d-118">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="d374d-119">✔️</span><span class="sxs-lookup"><span data-stu-id="d374d-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="d374d-120">Ray 光标</span><span class="sxs-lookup"><span data-stu-id="d374d-120">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="d374d-121">✔️</span><span class="sxs-lookup"><span data-stu-id="d374d-121">✔️</span></span></td>
        <td><span data-ttu-id="d374d-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d374d-122">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="d374d-123">打印头光标</span><span class="sxs-lookup"><span data-stu-id="d374d-123">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="d374d-124">✔️</span><span class="sxs-lookup"><span data-stu-id="d374d-124">✔️</span></span></td>
        <td><span data-ttu-id="d374d-125">✔️</span><span class="sxs-lookup"><span data-stu-id="d374d-125">✔️</span></span></td>
        <td><span data-ttu-id="d374d-126">✔️</span><span class="sxs-lookup"><span data-stu-id="d374d-126">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="d374d-127">手指光标</span><span class="sxs-lookup"><span data-stu-id="d374d-127">Finger cursor</span></span>
<span data-ttu-id="d374d-128">Finger 游标仅在 HoloLens 2 上可用，以增强 "[直接操作](direct-manipulation.md)" 交互模式。</span><span class="sxs-lookup"><span data-stu-id="d374d-128">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="d374d-129">为了更好地了解手指的位置，我们将环附加到了两个食指的提示。</span><span class="sxs-lookup"><span data-stu-id="d374d-129">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="d374d-130">环形大小基于与 UI 图面的连接的距离（手指越接近，环形越小，圆圈则缩小为点形，当手指与 UI 联系时将收缩到点形状。</span><span class="sxs-lookup"><span data-stu-id="d374d-130">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="d374d-131">![finger 光标](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="d374d-131">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="d374d-132">**Finger cursor 1 的视觉反馈状态**：环形收缩为点。</span><span class="sxs-lookup"><span data-stu-id="d374d-132">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="d374d-133">2：环形与图面对齐。</span><span class="sxs-lookup"><span data-stu-id="d374d-133">2: The ring aligns with surface.</span></span> <span data-ttu-id="d374d-134">3：环与 finger 矢量垂直。</span><span class="sxs-lookup"><span data-stu-id="d374d-134">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="d374d-135">4：无环。</span><span class="sxs-lookup"><span data-stu-id="d374d-135">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="d374d-136">Ray 光标</span><span class="sxs-lookup"><span data-stu-id="d374d-136">Ray cursor</span></span>
<span data-ttu-id="d374d-137">Ray 光标连接到最靠近的光线的末尾，以允许对不是手接触的对象进行操作。</span><span class="sxs-lookup"><span data-stu-id="d374d-137">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="d374d-138">在沉浸式耳机中，从运动控制器开始，并以点光标结束。</span><span class="sxs-lookup"><span data-stu-id="d374d-138">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="d374d-139">在 HoloLens 2 中，我们充分利用了这些运动控制器光线的心理模型，并利用了源自不要和 end 的环形光标（与直接操作中使用的 finger 光标一致）。</span><span class="sxs-lookup"><span data-stu-id="d374d-139">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="d374d-140">![Ray cursor 控制器](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="d374d-140">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="d374d-141">**运动控制器的光线光标**</span><span class="sxs-lookup"><span data-stu-id="d374d-141">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d374d-142">![Ray cursor 手型](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="d374d-142">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="d374d-143">**免提的光线光标**</span><span class="sxs-lookup"><span data-stu-id="d374d-143">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="d374d-144">打印头光标</span><span class="sxs-lookup"><span data-stu-id="d374d-144">Head-gaze cursor</span></span>
<span data-ttu-id="d374d-145">打印头光标是一个点，用于连接到使用点的位置和旋转点的不可见的端面向量。</span><span class="sxs-lookup"><span data-stu-id="d374d-145">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="d374d-146">若要执行操作，请将指针光标与各种提交输入（如分流、语音命令、停留和按钮按下）配对。</span><span class="sxs-lookup"><span data-stu-id="d374d-146">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="d374d-147">在 HoloLens 2 中，打印头最好与任何不是分流的提交输入配对，因为这会在空中分流和远手光线之间发生交互冲突。</span><span class="sxs-lookup"><span data-stu-id="d374d-147">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="d374d-148">![打印头的光标手](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="d374d-148">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="d374d-149">**带有手动手势的打印头**</span><span class="sxs-lookup"><span data-stu-id="d374d-149">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d374d-150">![打印头的光标声音](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="d374d-150">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="d374d-151">**带有声音命令的头盔光标**</span><span class="sxs-lookup"><span data-stu-id="d374d-151">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="d374d-152">游标自定义建议</span><span class="sxs-lookup"><span data-stu-id="d374d-152">Cursor customization recommendations</span></span>
<span data-ttu-id="d374d-153">如果要自定义游标反馈行为和外观，以下是一些设计建议：</span><span class="sxs-lookup"><span data-stu-id="d374d-153">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="d374d-154">游标刻度</span><span class="sxs-lookup"><span data-stu-id="d374d-154">Cursor scale</span></span>
* <span data-ttu-id="d374d-155">光标不应大于可用目标，从而使用户可以轻松地与内容交互并查看内容。</span><span class="sxs-lookup"><span data-stu-id="d374d-155">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="d374d-156">根据您创建的体验，在用户看起来时缩放光标也是一个重要的考虑因素。</span><span class="sxs-lookup"><span data-stu-id="d374d-156">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="d374d-157">例如，当用户看到你的体验时，游标不应太小，因此不会丢失。</span><span class="sxs-lookup"><span data-stu-id="d374d-157">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="d374d-158">缩放光标时，请考虑将软动画应用到它，因为它会进行缩放以使其成为一种有机感觉。</span><span class="sxs-lookup"><span data-stu-id="d374d-158">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="d374d-159">避免阻碍内容。</span><span class="sxs-lookup"><span data-stu-id="d374d-159">Avoid obstructing content.</span></span> <span data-ttu-id="d374d-160">全息影像使体验更加容易，并且光标不应从它们中消失。</span><span class="sxs-lookup"><span data-stu-id="d374d-160">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="d374d-161">Directionless 光标形状</span><span class="sxs-lookup"><span data-stu-id="d374d-161">Directionless cursor shape</span></span>
* <span data-ttu-id="d374d-162">尽管没有一个右光标形状，但建议使用 directionless 形状（如圆环图）。</span><span class="sxs-lookup"><span data-stu-id="d374d-162">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="d374d-163">指向某个方向（例如传统箭头光标）的光标可能会使用户感到困惑，这可能会使用户感到困惑。</span><span class="sxs-lookup"><span data-stu-id="d374d-163">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="d374d-164">当使用游标向用户传达交互指令时，会出现这种情况的例外情况。</span><span class="sxs-lookup"><span data-stu-id="d374d-164">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="d374d-165">例如，在混合现实操作系统中缩放全息影像时，光标暂时会包括一些箭头，指导用户如何移动其手来缩放全息影像。</span><span class="sxs-lookup"><span data-stu-id="d374d-165">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="d374d-166">外观</span><span class="sxs-lookup"><span data-stu-id="d374d-166">Look and feel</span></span>
* <span data-ttu-id="d374d-167">环形或圆环图游标适用于许多应用程序。</span><span class="sxs-lookup"><span data-stu-id="d374d-167">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="d374d-168">选择最能代表您正在创建的体验的颜色和形状。</span><span class="sxs-lookup"><span data-stu-id="d374d-168">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="d374d-169">游标特别容易出现[颜色分离](hologram-stability.md#color-separation)。</span><span class="sxs-lookup"><span data-stu-id="d374d-169">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="d374d-170">具有均衡不透明度的小游标将使其具有信息性，而无需占据视觉层次结构。</span><span class="sxs-lookup"><span data-stu-id="d374d-170">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="d374d-171">请 cognizant 在游标后面使用阴影或突出显示，因为它们可能会妨碍内容和对任务的注意力。</span><span class="sxs-lookup"><span data-stu-id="d374d-171">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="d374d-172">光标应与应用中的表面对齐并进行分配，这会使用户感觉到系统可以看到的位置，但系统也知道其周围的位置。</span><span class="sxs-lookup"><span data-stu-id="d374d-172">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="d374d-173">例如，在混合现实操作系统中，光标与用户世界的表面保持一致，即使用户没有直接在全息图上查看，也可以感觉到世界认知。</span><span class="sxs-lookup"><span data-stu-id="d374d-173">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="d374d-174">当光标位于接近邻近的位置时，会将光标锁定到交互式元素，从而有助于提高用户在执行选择操作时与该元素进行交互的置信度。</span><span class="sxs-lookup"><span data-stu-id="d374d-174">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="d374d-175">视觉提示</span><span class="sxs-lookup"><span data-stu-id="d374d-175">Visual cues</span></span>
* <span data-ttu-id="d374d-176">如果你的体验侧重于单个全息图，则当你看起来远离该全息图时，光标应该只与全息图和改变形状对齐。</span><span class="sxs-lookup"><span data-stu-id="d374d-176">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="d374d-177">这可以向用户传达全息影像是可操作的，并且可以与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="d374d-177">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="d374d-178">如果你的应用程序使用空间映射，则光标可能会对齐并向其看到的每个表面显示。</span><span class="sxs-lookup"><span data-stu-id="d374d-178">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="d374d-179">这会向 HoloLens 和你的应用程序可以看到其空间的用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="d374d-179">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="d374d-180">这就是一个事实，那就是全息影像非常真实，并可帮助您弥补现实和虚拟之间的差距。</span><span class="sxs-lookup"><span data-stu-id="d374d-180">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="d374d-181">在视图中没有全息影像或曲面时，了解光标应执行的操作。</span><span class="sxs-lookup"><span data-stu-id="d374d-181">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="d374d-182">将其放置在用户前面预先确定的距离上是一种选择。</span><span class="sxs-lookup"><span data-stu-id="d374d-182">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="d374d-183">可能的操作</span><span class="sxs-lookup"><span data-stu-id="d374d-183">Possible actions</span></span>
* <span data-ttu-id="d374d-184">光标可由不同的图标表示，以传达全息图可以执行的可能操作，例如缩放或旋转。</span><span class="sxs-lookup"><span data-stu-id="d374d-184">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="d374d-185">仅在游标中添加了其他内容时，才添加其他信息。</span><span class="sxs-lookup"><span data-stu-id="d374d-185">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="d374d-186">否则，用户可能不会注意到状态发生更改，也可能会使光标混淆。</span><span class="sxs-lookup"><span data-stu-id="d374d-186">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="d374d-187">输入状态</span><span class="sxs-lookup"><span data-stu-id="d374d-187">Input state</span></span>
* <span data-ttu-id="d374d-188">可以使用光标显示用户的输入状态或意向。</span><span class="sxs-lookup"><span data-stu-id="d374d-188">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="d374d-189">例如，我们可以显示一个图标，告诉用户系统看到其手状态，并且应用程序知道他们已准备好采取措施。</span><span class="sxs-lookup"><span data-stu-id="d374d-189">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="d374d-190">还可以使用光标向用户显示系统通过暂时颜色改动听到的声音命令</span><span class="sxs-lookup"><span data-stu-id="d374d-190">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="d374d-191">可以通过不同的方式实现以下游标状态。</span><span class="sxs-lookup"><span data-stu-id="d374d-191">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="d374d-192">您可以通过对游标（如状态机）进行建模来实现这些不同的状态。</span><span class="sxs-lookup"><span data-stu-id="d374d-192">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="d374d-193">例如：</span><span class="sxs-lookup"><span data-stu-id="d374d-193">For example:</span></span>
    * <span data-ttu-id="d374d-194">空闲状态是显示默认光标的位置。</span><span class="sxs-lookup"><span data-stu-id="d374d-194">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="d374d-195">"就绪" 状态为 "已检测到用户" 就绪位置。</span><span class="sxs-lookup"><span data-stu-id="d374d-195">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="d374d-196">交互状态是用户执行特定交互时的状态。</span><span class="sxs-lookup"><span data-stu-id="d374d-196">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="d374d-197">当你传达可以在全息图上执行的可能操作时，可能的操作状态或悬停状态。</span><span class="sxs-lookup"><span data-stu-id="d374d-197">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="d374d-198">您还可以以外观方式实现这些状态，以便在检测到不同的状态时可以显示不同的图稿资产。</span><span class="sxs-lookup"><span data-stu-id="d374d-198">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="d374d-199">转到 "无游标"</span><span class="sxs-lookup"><span data-stu-id="d374d-199">Going "cursor-free"</span></span>
<span data-ttu-id="d374d-200">如果浸入式是一个经验的关键组成部分，而指向交互（通过注视和手势）不需要更高的精度，则建议在不使用光标的情况下进行设计。</span><span class="sxs-lookup"><span data-stu-id="d374d-200">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="d374d-201">通过向用户提供对系统的理解并帮助他们自信地将其意图传达给系统的方式，系统仍必须满足游标通常满足的需求。</span><span class="sxs-lookup"><span data-stu-id="d374d-201">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="d374d-202">这可以通过其他明显的状态更改实现。</span><span class="sxs-lookup"><span data-stu-id="d374d-202">This may be achievable through other noticeable state changes.</span></span>

<br>

---


## <a name="see-also"></a><span data-ttu-id="d374d-203">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d374d-203">See also</span></span>
* [<span data-ttu-id="d374d-204">手势</span><span class="sxs-lookup"><span data-stu-id="d374d-204">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="d374d-205">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="d374d-205">Head-gaze and commit</span></span>](gaze-and-commit.md)
