---
title: 什么是全息图？
description: HoloLens 使你可以查看与世界上出现在世界各地的光线和声音的三维全息影像, 并与之交互。
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 全息影像, 设计, 交互
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829779"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="d1067-104">什么是全息图？</span><span class="sxs-lookup"><span data-stu-id="d1067-104">What is a hologram?</span></span>

<span data-ttu-id="d1067-105">通过 HoloLens, 你可以创建**全息影像**, 这些对象是在世界各地显示的光线和声音, 就像它们是真实的对象一样。</span><span class="sxs-lookup"><span data-stu-id="d1067-105">HoloLens lets you create **holograms**, objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="d1067-106">全息影像会响应你的[注视](gaze.md)、[手势](gestures.md)和[语音命令](voice-input.md), 并可与你周围的[实际表面](spatial-mapping.md)交互。</span><span class="sxs-lookup"><span data-stu-id="d1067-106">Holograms respond to your [gaze](gaze.md), [gestures](gestures.md) and [voice commands](voice-input.md), and can interact with [real-world surfaces](spatial-mapping.md) around you.</span></span> <span data-ttu-id="d1067-107">利用全息影像, 你可以创建属于你的世界的数字对象。</span><span class="sxs-lookup"><span data-stu-id="d1067-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a><span data-ttu-id="d1067-108">设备支持</span><span class="sxs-lookup"><span data-stu-id="d1067-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d1067-109"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="d1067-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d1067-110"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="d1067-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d1067-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d1067-111"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d1067-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="d1067-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d1067-113">影像</span><span class="sxs-lookup"><span data-stu-id="d1067-113">Holograms</span></span></td>
        <td><span data-ttu-id="d1067-114">✔️</span><span class="sxs-lookup"><span data-stu-id="d1067-114">✔️</span></span></td>
        <td><span data-ttu-id="d1067-115">✔️</span><span class="sxs-lookup"><span data-stu-id="d1067-115">✔️</span></span></td>
        <td><span data-ttu-id="d1067-116">❌</span><span class="sxs-lookup"><span data-stu-id="d1067-116">❌</span></span></td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="d1067-117">全息图是由光和声音组成的</span><span class="sxs-lookup"><span data-stu-id="d1067-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="d1067-118">HoloLens[呈现](rendering.md)的全息影像会直接显示在用户眼睛的前方。</span><span class="sxs-lookup"><span data-stu-id="d1067-118">The holograms that HoloLens [renders](rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="d1067-119">全息影像为你的世界增加了灯光, 这意味着你会看到来自显示器的灯光和来自你周围的光线。</span><span class="sxs-lookup"><span data-stu-id="d1067-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="d1067-120">HoloLens 不会从眼睛中去除光, 因此无法用黑色呈现全息影像。</span><span class="sxs-lookup"><span data-stu-id="d1067-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="d1067-121">但黑色内容将显示为透明。</span><span class="sxs-lookup"><span data-stu-id="d1067-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="d1067-122">全息影像可以有许多不同的外观和行为。</span><span class="sxs-lookup"><span data-stu-id="d1067-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="d1067-123">有些是真实的、坚实的, 而有些则是 cartoonish 和 ethereal。</span><span class="sxs-lookup"><span data-stu-id="d1067-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="d1067-124">全息影像可以突出显示你的环境中的功能, 并且它们可以是应用用户界面中的元素。</span><span class="sxs-lookup"><span data-stu-id="d1067-124">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![地面上的全息狗浏览](images/fang3-640px.jpg)

<span data-ttu-id="d1067-126">全息影像还可以发出[声音](spatial-sound.md), 这会显示在周围的特定位置。</span><span class="sxs-lookup"><span data-stu-id="d1067-126">Holograms can also make [sounds](spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="d1067-127">在 HoloLens 上, 声音来自两个扬声器, 它们直接位于你的耳上方, 而不会覆盖它们。</span><span class="sxs-lookup"><span data-stu-id="d1067-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="d1067-128">与显示器类似, 扬声器是累加的, 引入新声音, 而不会阻止环境中的声音。</span><span class="sxs-lookup"><span data-stu-id="d1067-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="d1067-129">全息图可以放在世界上, 也可以与你一起标记</span><span class="sxs-lookup"><span data-stu-id="d1067-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="d1067-130">如果你有想要在其中使用全息图的特定位置, 则可以将其精确[放置](coordinate-systems.md)在世界各地。</span><span class="sxs-lookup"><span data-stu-id="d1067-130">When you have a particular location where you want a hologram, you can [place](coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="d1067-131">当您浏览该全息图时, 它会相对于您的世界显得稳定。</span><span class="sxs-lookup"><span data-stu-id="d1067-131">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="d1067-132">如果使用[空间锚点](coordinate-systems.md#spatial-anchors)将该对象牢固地固定到世界, 则系统甚至可以在以后回来时记住它的位置。</span><span class="sxs-lookup"><span data-stu-id="d1067-132">If you use a [spatial anchor](coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![表中的全息建筑 maquette](images/image5-640px.png)

<span data-ttu-id="d1067-134">某些全息影像会按用户进行操作。</span><span class="sxs-lookup"><span data-stu-id="d1067-134">Some holograms follow the user instead.</span></span> <span data-ttu-id="d1067-135">这些基于标记的影像的位置本身相对于用户, 而不管它们在何处。</span><span class="sxs-lookup"><span data-stu-id="d1067-135">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="d1067-136">你甚至可以选择将一段时间带到一段时间, 然后将其放在墙上的另一个房间。</span><span class="sxs-lookup"><span data-stu-id="d1067-136">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="d1067-137">**最佳做法**</span><span class="sxs-lookup"><span data-stu-id="d1067-137">**Best practices**</span></span>
* <span data-ttu-id="d1067-138">在某些情况下, 可能需要在整个体验中轻松发现和查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="d1067-138">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="d1067-139">此类定位有两个高级方法。</span><span class="sxs-lookup"><span data-stu-id="d1067-139">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="d1067-140">让我们将它们称为 **"显示-锁定"** 和 **"正文锁定"** 。</span><span class="sxs-lookup"><span data-stu-id="d1067-140">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="d1067-141">显示锁定的内容按位置 "锁定" 到设备显示。</span><span class="sxs-lookup"><span data-stu-id="d1067-141">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="d1067-142">这是一种很难的原因, 其中包括 "clingyness" 的非自然感觉, 这使得许多用户感到沮丧并希望 "晃动它"。</span><span class="sxs-lookup"><span data-stu-id="d1067-142">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="d1067-143">通常, 许多设计人员发现, 更好的做法是避免显示锁定内容。</span><span class="sxs-lookup"><span data-stu-id="d1067-143">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="d1067-144">主体锁定的方法远远 forgivable。</span><span class="sxs-lookup"><span data-stu-id="d1067-144">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="d1067-145">正文锁定是指受限用户的主体或注视, 而将其置于3d 空间中以环绕用户的情况。</span><span class="sxs-lookup"><span data-stu-id="d1067-145">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="d1067-146">许多经验都采用了一种正文锁定行为, 其中全息图 "跟随" 用户看, 这使用户可以旋转其身体, 而不会丢失全息影像。</span><span class="sxs-lookup"><span data-stu-id="d1067-146">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="d1067-147">合并延迟有助于使全息图移动更加自然。</span><span class="sxs-lookup"><span data-stu-id="d1067-147">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="d1067-148">例如, Windows 全息版 OS 的某些核心 UI 使用的是正文锁定, 这种情况下, 用户将看起来像是一种灵活的、弹性的延迟, 同时用户会将其标头。</span><span class="sxs-lookup"><span data-stu-id="d1067-148">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="d1067-149">将全息图放置在舒适的观看距离上, 通常会远离1-2 米。</span><span class="sxs-lookup"><span data-stu-id="d1067-149">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="d1067-150">为必须持续在全息帧中的元素提供一定数量的偏移, 或在用户更改其视图时考虑将内容动态显示在一侧。</span><span class="sxs-lookup"><span data-stu-id="d1067-150">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="d1067-151">**将全息影像置于最佳区域-介于 1.25 m 和5分钟之间**</span><span class="sxs-lookup"><span data-stu-id="d1067-151">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="d1067-152">这两个指标最适用, 体验会使你从一次计量获得更近的距离。</span><span class="sxs-lookup"><span data-stu-id="d1067-152">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="d1067-153">远距离超过一米, 经常进行深入了解的全息影像比静态全息影像更有可能出现问题。</span><span class="sxs-lookup"><span data-stu-id="d1067-153">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="d1067-154">当内容太近时, 请考虑适当地剪辑或淡化内容, 以便不会使用户进入意外体验。</span><span class="sxs-lookup"><span data-stu-id="d1067-154">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![从用户放置全息影像的最佳距离。](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="d1067-156">全息图与您和您的世界交互</span><span class="sxs-lookup"><span data-stu-id="d1067-156">A hologram interacts with you and your world</span></span>

<span data-ttu-id="d1067-157">全息影像不仅适用于灯光和声音;它们也是您世界的一个活动部分。</span><span class="sxs-lookup"><span data-stu-id="d1067-157">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="d1067-158">用手看一个全息影像和手势, 然后就可以开始使用全息图。</span><span class="sxs-lookup"><span data-stu-id="d1067-158">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="d1067-159">向全息影像发出语音命令, 然后可以回复。</span><span class="sxs-lookup"><span data-stu-id="d1067-159">Give a voice command to a hologram, and it can reply.</span></span>

![房地产摩托车设计适合于现实生活摩托车正文](images/image8-640px.png)

<span data-ttu-id="d1067-161">全息影像实现了不可能在其他地方使用的个人交互。</span><span class="sxs-lookup"><span data-stu-id="d1067-161">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="d1067-162">因为 HoloLens 知道其在世界各地的位置, 所以, 当您在房间内浏览时, 全息字符可以直接显示您的眼睛。</span><span class="sxs-lookup"><span data-stu-id="d1067-162">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="d1067-163">全息图还可以与你的环境交互。</span><span class="sxs-lookup"><span data-stu-id="d1067-163">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="d1067-164">例如, 您可以将一个全息弹跳球置于一个表上方。</span><span class="sxs-lookup"><span data-stu-id="d1067-164">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="d1067-165">然后, 通过[点击](gestures.md#air-tap), 观看球弹跳并在到达表时发出声音。</span><span class="sxs-lookup"><span data-stu-id="d1067-165">Then, with an [air tap](gestures.md#air-tap), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="d1067-166">全息影像还可以由真实的对象封闭像素。</span><span class="sxs-lookup"><span data-stu-id="d1067-166">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="d1067-167">例如, 全息人物可能会走出大门的门和背面。</span><span class="sxs-lookup"><span data-stu-id="d1067-167">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="d1067-168">**有关集成全息影像和现实世界的技巧**</span><span class="sxs-lookup"><span data-stu-id="d1067-168">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="d1067-169">与 gravitational 规则相协调, 可以更轻松地与和更可信相关。</span><span class="sxs-lookup"><span data-stu-id="d1067-169">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="d1067-170">例如将一个全息狗置于 & 表上的花瓶, 而不是让它们在空间中浮动。</span><span class="sxs-lookup"><span data-stu-id="d1067-170">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="d1067-171">许多设计人员发现, 他们甚至可以通过在 believably 的表面上创建 "负阴影" 来更好地集成全息影像。</span><span class="sxs-lookup"><span data-stu-id="d1067-171">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="d1067-172">为此, 可在两个全息图的地面上创建软光亮, 然后从发光中减去 "阴影"。</span><span class="sxs-lookup"><span data-stu-id="d1067-172">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="d1067-173">软发光与现实世界中的光线相集成, 而阴影则是环境中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="d1067-173">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

## <a name="a-hologram-is-whatever-you-dream-up"></a><span data-ttu-id="d1067-174">全息图是你所希望的一切</span><span class="sxs-lookup"><span data-stu-id="d1067-174">A hologram is whatever you dream up</span></span>

<span data-ttu-id="d1067-175">作为全息开发人员, 您可以将您的创造性从2D 屏幕和世界各地突破起来。</span><span class="sxs-lookup"><span data-stu-id="d1067-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span> <span data-ttu-id="d1067-176">*你*将生成什么？</span><span class="sxs-lookup"><span data-stu-id="d1067-176">What will *you* build?</span></span>

![客厅的全息虚世界](images/designoverview.jpg)

## <a name="see-also"></a><span data-ttu-id="d1067-178">请参阅</span><span class="sxs-lookup"><span data-stu-id="d1067-178">See also</span></span>
* [<span data-ttu-id="d1067-179">空间音效</span><span class="sxs-lookup"><span data-stu-id="d1067-179">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="d1067-180">颜色、光线和材料</span><span class="sxs-lookup"><span data-stu-id="d1067-180">Color, light and materials</span></span>](color,-light-and-materials.md)
