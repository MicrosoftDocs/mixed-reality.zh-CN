---
title: 什么是全息图？
description: HoloLens 您可以查看和使用三维全息进行交互，对象所做的光线和声音中显示的周围世界。
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 HoloLens、 全息、 设计、 交互
ms.openlocfilehash: 5a6cc4df764b1f92f6bea2d7d6e6effe2164e4d6
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590161"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="95c5f-104">什么是全息图？</span><span class="sxs-lookup"><span data-stu-id="95c5f-104">What is a hologram?</span></span>

<span data-ttu-id="95c5f-105">HoloLens 允许您创建**全息**、 对象所做的光线和声音中显示的周围，世界就像它们是真实的对象。</span><span class="sxs-lookup"><span data-stu-id="95c5f-105">HoloLens lets you create **holograms**, objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="95c5f-106">全息响应你[注视](gaze.md)，[手势](gestures.md)并[语音命令](voice-input.md)，并可以与之交互[实际表面](spatial-mapping.md)周围。</span><span class="sxs-lookup"><span data-stu-id="95c5f-106">Holograms respond to your [gaze](gaze.md), [gestures](gestures.md) and [voice commands](voice-input.md), and can interact with [real-world surfaces](spatial-mapping.md) around you.</span></span> <span data-ttu-id="95c5f-107">全息，您可以创建属于您的世界的数字对象。</span><span class="sxs-lookup"><span data-stu-id="95c5f-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a><span data-ttu-id="95c5f-108">设备支持</span><span class="sxs-lookup"><span data-stu-id="95c5f-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="95c5f-109">功能</span><span class="sxs-lookup"><span data-stu-id="95c5f-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="95c5f-110"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></span><span class="sxs-lookup"><span data-stu-id="95c5f-110"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="95c5f-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="95c5f-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="95c5f-112"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="95c5f-112"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="95c5f-113">全息</span><span class="sxs-lookup"><span data-stu-id="95c5f-113">Holograms</span></span></td><td style="text-align: center;"> <span data-ttu-id="95c5f-114">✔️</span><span class="sxs-lookup"><span data-stu-id="95c5f-114">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="95c5f-115">✔️</span><span class="sxs-lookup"><span data-stu-id="95c5f-115">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="95c5f-116">一张全息图组成浅色和声音</span><span class="sxs-lookup"><span data-stu-id="95c5f-116">A hologram is made of light and sound</span></span>

<span data-ttu-id="95c5f-117">全息该 HoloLens[呈现](rendering.md)直接放在用户的眼睛全息版的帧中显示。</span><span class="sxs-lookup"><span data-stu-id="95c5f-117">The holograms that HoloLens [renders](rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="95c5f-118">全息将添加到您的世界，这意味着，您将看到显示灯和从周围的环境光的光。</span><span class="sxs-lookup"><span data-stu-id="95c5f-118">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="95c5f-119">HoloLens 不会从你自己，删除光，因此全息无法呈现颜色使用黑色。</span><span class="sxs-lookup"><span data-stu-id="95c5f-119">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="95c5f-120">相反，黑色的内容显示为透明效果。</span><span class="sxs-lookup"><span data-stu-id="95c5f-120">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="95c5f-121">全息可以具有许多不同的外观和行为。</span><span class="sxs-lookup"><span data-stu-id="95c5f-121">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="95c5f-122">一些实际也更加稳定，而有些则是卡通和 ethereal。</span><span class="sxs-lookup"><span data-stu-id="95c5f-122">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="95c5f-123">全息可以突出显示你环境中的功能，也可以在应用程序的用户界面中的元素。</span><span class="sxs-lookup"><span data-stu-id="95c5f-123">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![Holographic dog 在地板上的每个步骤](images/fang3-640px.jpg)

<span data-ttu-id="95c5f-125">此外可以使全息[声音](spatial-sound.md)，这将显示为来自周围的环境中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="95c5f-125">Holograms can also make [sounds](spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="95c5f-126">在 HoloLens，听起来来自两个位于正上方您的头脑，同时不会覆盖它们的发言人。</span><span class="sxs-lookup"><span data-stu-id="95c5f-126">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="95c5f-127">显示与类似，演讲者是累加式的而不会阻止你的环境中的声音引入新的声音。</span><span class="sxs-lookup"><span data-stu-id="95c5f-127">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="95c5f-128">可以标记与您的世界中放置一张全息图</span><span class="sxs-lookup"><span data-stu-id="95c5f-128">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="95c5f-129">想一张全息图的特定位置后，你可以[放置](coordinate-systems.md)它准确地说那里世界上。</span><span class="sxs-lookup"><span data-stu-id="95c5f-129">When you have a particular location where you want a hologram, you can [place](coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="95c5f-130">您向介绍围绕该全息图，它将显示相对于周围世界稳定。</span><span class="sxs-lookup"><span data-stu-id="95c5f-130">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="95c5f-131">如果您使用[空间的定位点](coordinate-systems.md#spatial-anchors)固定牢固地向该对象，系统可以甚至记住你中断的地方它时稍后返回。</span><span class="sxs-lookup"><span data-stu-id="95c5f-131">If you use a [spatial anchor](coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![全息版构建 maquette 您坐在一个表](images/image5-640px.png)

<span data-ttu-id="95c5f-133">某些全息改为的用户进行操作。</span><span class="sxs-lookup"><span data-stu-id="95c5f-133">Some holograms follow the user instead.</span></span> <span data-ttu-id="95c5f-134">这些尾随全息定位本身相对于用户，无论他们向介绍。</span><span class="sxs-lookup"><span data-stu-id="95c5f-134">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="95c5f-135">您甚至可以选择将与你一张全息图一段时间，然后将它放在墙上后转到另一个房间。</span><span class="sxs-lookup"><span data-stu-id="95c5f-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="95c5f-136">**最佳做法**</span><span class="sxs-lookup"><span data-stu-id="95c5f-136">**Best practices**</span></span>
* <span data-ttu-id="95c5f-137">某些情况下可能要求全息保持轻松容易被发现或整个体验可见。</span><span class="sxs-lookup"><span data-stu-id="95c5f-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="95c5f-138">有两种高级方法，这种类型的定位。</span><span class="sxs-lookup"><span data-stu-id="95c5f-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="95c5f-139">让我们称他们 **"显示锁定"** 并 **"正文禁止"**。</span><span class="sxs-lookup"><span data-stu-id="95c5f-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="95c5f-140">显示锁定内容已按位置"锁定"到设备显示。</span><span class="sxs-lookup"><span data-stu-id="95c5f-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="95c5f-141">这是比较棘手的原因有多种，包括"clingyness"，使多个用户感到沮丧非自然感觉和想要"摇晃它。"</span><span class="sxs-lookup"><span data-stu-id="95c5f-141">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="95c5f-142">一般情况下，许多设计人员已找到更好的做法避免显示锁定内容。</span><span class="sxs-lookup"><span data-stu-id="95c5f-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="95c5f-143">正文锁定的方法是 forgivable 得多。</span><span class="sxs-lookup"><span data-stu-id="95c5f-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="95c5f-144">正文锁定是一张全息图限于用户的主体或的视线移动矢量，但在 3d 空间中围绕用户定位。</span><span class="sxs-lookup"><span data-stu-id="95c5f-144">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="95c5f-145">许多体验已采用其中 hologram"紧跟"用户视线移动，这样用户就可以旋转其主体和浏览空间，而不会丢失全息图正文锁定的行为。</span><span class="sxs-lookup"><span data-stu-id="95c5f-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="95c5f-146">将合并延迟有助于感觉更自然的 hologram 移动。</span><span class="sxs-lookup"><span data-stu-id="95c5f-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="95c5f-147">例如，某些核心的 Windows 全息版操作系统的 UI 使用一种变体正文锁定时在用户打开其头后面，并简要、 类似于弹性的延迟的用户的视线移动。</span><span class="sxs-lookup"><span data-stu-id="95c5f-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="95c5f-148">将放全息图舒适地观看距离通常大约 1-2 米离开头。</span><span class="sxs-lookup"><span data-stu-id="95c5f-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="95c5f-149">提供的元素必须不断地在全息版的框架中，或当用户更改其角度来看，对一侧显示的内容进行动画处理，请考虑所用的偏移量。</span><span class="sxs-lookup"><span data-stu-id="95c5f-149">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="95c5f-150">**将全息放置在最佳的区域-1.25 m 和 5 分钟之间**</span><span class="sxs-lookup"><span data-stu-id="95c5f-150">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="95c5f-151">两种测定仪的最优，并体验会降低近获取从一个指示器。</span><span class="sxs-lookup"><span data-stu-id="95c5f-151">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="95c5f-152">处于越重要比一米以内的距离，定期将移动的深度的全息是更有可能会比静态全息出现问题。</span><span class="sxs-lookup"><span data-stu-id="95c5f-152">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="95c5f-153">请考虑适当地剪切或淡出你的内容时获取得太近，以免意外体验到 jar 用户。</span><span class="sxs-lookup"><span data-stu-id="95c5f-153">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![放置全息从用户的最佳距离。](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="95c5f-155">与您和您的世界交互一张全息图</span><span class="sxs-lookup"><span data-stu-id="95c5f-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="95c5f-156">全息不是仅涉及浅色和声音;它们也是您的世界的活动部分。</span><span class="sxs-lookup"><span data-stu-id="95c5f-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="95c5f-157">在全息图和用一只手，手势的视线移动和一张全息图跟随你便可以开始。</span><span class="sxs-lookup"><span data-stu-id="95c5f-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="95c5f-158">语音命令向一张全息图，它可以进行回复。</span><span class="sxs-lookup"><span data-stu-id="95c5f-158">Give a voice command to a hologram, and it can reply.</span></span>

![在现实生活摩托车正文拟合 holographic 摩托车设计](images/image8-640px.png)

<span data-ttu-id="95c5f-160">全息实现不可能实现的其他位置的个人交互。</span><span class="sxs-lookup"><span data-stu-id="95c5f-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="95c5f-161">因为 HoloLens 知道其中位于世界，holographic 字符可以查询您直接在眼睛房间中四处走动。</span><span class="sxs-lookup"><span data-stu-id="95c5f-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="95c5f-162">一张全息图还可以使用周围的环境进行交互。</span><span class="sxs-lookup"><span data-stu-id="95c5f-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="95c5f-163">例如，您可以放置在表格上方 holographic 跳动的球。</span><span class="sxs-lookup"><span data-stu-id="95c5f-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="95c5f-164">然后，使用[敲击](gestures.md#air-tap)，观看球跳动式和使声音抵达表时。</span><span class="sxs-lookup"><span data-stu-id="95c5f-164">Then, with an [air tap](gestures.md#air-tap), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="95c5f-165">此外可以通过现实世界对象封闭全息。</span><span class="sxs-lookup"><span data-stu-id="95c5f-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="95c5f-166">例如，通过一扇门和后面墙上，在视线之外，可能引导 holographic 字符。</span><span class="sxs-lookup"><span data-stu-id="95c5f-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="95c5f-167">**用于集成全息和现实世界的提示**</span><span class="sxs-lookup"><span data-stu-id="95c5f-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="95c5f-168">对齐到引力规则可让全息更轻松地与更可信。</span><span class="sxs-lookup"><span data-stu-id="95c5f-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="95c5f-169">例如：一开始 （& a） 在表上的花瓶置于 holographic 狗，而不是让他们在空间中浮动。</span><span class="sxs-lookup"><span data-stu-id="95c5f-169">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="95c5f-170">许多设计人员发现它们更加 believably 集成全息通过创建"负影子"hologram 坐在图面上。</span><span class="sxs-lookup"><span data-stu-id="95c5f-170">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="95c5f-171">它们通过围绕全息图地面上创建软发光然后减去从发光"影子"执行此操作。</span><span class="sxs-lookup"><span data-stu-id="95c5f-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="95c5f-172">软发光与集成在现实生活中光和阴影 grounds 全息图在环境中。</span><span class="sxs-lookup"><span data-stu-id="95c5f-172">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

## <a name="a-hologram-is-whatever-you-dream-up"></a><span data-ttu-id="95c5f-173">无论您想到一张全息图是</span><span class="sxs-lookup"><span data-stu-id="95c5f-173">A hologram is whatever you dream up</span></span>

<span data-ttu-id="95c5f-174">作为 holographic 开发人员，您可以中断你的创造力超出 2D 屏幕和到周围世界的能力。</span><span class="sxs-lookup"><span data-stu-id="95c5f-174">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span> <span data-ttu-id="95c5f-175">将会什么*您*生成？</span><span class="sxs-lookup"><span data-stu-id="95c5f-175">What will *you* build?</span></span>

![在起居室 holographic 虚部世界](images/designoverview.jpg)

## <a name="see-also"></a><span data-ttu-id="95c5f-177">请参阅</span><span class="sxs-lookup"><span data-stu-id="95c5f-177">See also</span></span>
* [<span data-ttu-id="95c5f-178">空间声音</span><span class="sxs-lookup"><span data-stu-id="95c5f-178">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="95c5f-179">颜色、 光线和材料</span><span class="sxs-lookup"><span data-stu-id="95c5f-179">Color, light and materials</span></span>](color,-light-and-materials.md)
