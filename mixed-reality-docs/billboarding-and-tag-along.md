---
title: Billboarding 和标记
description: 具有 billboarding 的对象始终向用户提供正面的定向。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，billboarding，连同标记
ms.openlocfilehash: ff2b1ce20174b1b9aecbb90b1d1dc3e8896b3761
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143128"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="17417-104">Billboarding 和标记</span><span class="sxs-lookup"><span data-stu-id="17417-104">Billboarding and tag-along</span></span>

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="17417-105">什么是 billboarding？</span><span class="sxs-lookup"><span data-stu-id="17417-105">What is billboarding?</span></span>

<span data-ttu-id="17417-106">Billboarding 是一种可应用于混合现实中的对象的行为概念。</span><span class="sxs-lookup"><span data-stu-id="17417-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="17417-107">具有 billboarding 的对象始终向用户提供正面的定向。</span><span class="sxs-lookup"><span data-stu-id="17417-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="17417-108">这对于文本和 menuing 系统特别有用，在这种情况下，如果用户要四处移动，用户环境（全球锁定）中放置的静态对象将被掩盖或无法读取。</span><span class="sxs-lookup"><span data-stu-id="17417-108">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="17417-109">启用了 billboarding 的对象可以在用户的环境中自由旋转。</span><span class="sxs-lookup"><span data-stu-id="17417-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="17417-110">它们还可以根据设计注意事项限制为单个轴。</span><span class="sxs-lookup"><span data-stu-id="17417-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="17417-111">请记住，如果 billboarded 对象置于其他对象之前太近，或在 HoloLens 中太接近扫描面，则它们可能会被剪裁或遮蔽。</span><span class="sxs-lookup"><span data-stu-id="17417-111">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="17417-112">为避免出现这种情况，请考虑在为 billboarding 启用轴旋转时对象可能产生的总空间。</span><span class="sxs-lookup"><span data-stu-id="17417-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="17417-113">什么是标记？</span><span class="sxs-lookup"><span data-stu-id="17417-113">What is a tag-along?</span></span>

<span data-ttu-id="17417-114">标记-一起是可以添加到全息影像的行为概念。</span><span class="sxs-lookup"><span data-stu-id="17417-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="17417-115">标记靠后的对象试图停留在允许用户轻松交互的范围内。</span><span class="sxs-lookup"><span data-stu-id="17417-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="17417-116">![的 "HoloLens 引脚" 面板是有关标记的行为方式的很好示例](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="17417-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="17417-117">*HoloLens "开始" 菜单是一个更好的标记和行为示例*</span><span class="sxs-lookup"><span data-stu-id="17417-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="17417-118">标记靠对象具有可对其行为方式进行微调的参数。</span><span class="sxs-lookup"><span data-stu-id="17417-118">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="17417-119">当用户在其环境中移动时，可以根据需要将内容移入或移出用户的行为。</span><span class="sxs-lookup"><span data-stu-id="17417-119">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="17417-120">用户移动时，内容将尝试在用户的绕中移动，并向视图边缘滑动，具体取决于用户的移动速度，可能会使内容暂时消失。</span><span class="sxs-lookup"><span data-stu-id="17417-120">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="17417-121">当用户 gazes 沿标记的对象时，它会更全面地进入视图。</span><span class="sxs-lookup"><span data-stu-id="17417-121">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="17417-122">将内容视为始终 "一目了然"，这样用户就不会忘记内容的方向。</span><span class="sxs-lookup"><span data-stu-id="17417-122">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="17417-123">其他参数可以通过橡皮带来使标记沿着对象的外观附加到用户的头。</span><span class="sxs-lookup"><span data-stu-id="17417-123">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="17417-124">抑制加速或减速为对象提供权重，使其感觉更真实地出现。</span><span class="sxs-lookup"><span data-stu-id="17417-124">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="17417-125">此春季行为是一种 affordance，可帮助用户构建准确的心理模型，说明如何进行标记。</span><span class="sxs-lookup"><span data-stu-id="17417-125">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="17417-126">当用户在标记沿模式下具有对象时，音频有助于提供附加的实用。</span><span class="sxs-lookup"><span data-stu-id="17417-126">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="17417-127">音频应强化移动速度;迅速走下来应提供更为明显的声音效果，同时，如果有任何效果，自然速度应具有最小的音频。</span><span class="sxs-lookup"><span data-stu-id="17417-127">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="17417-128">与真正的 head 锁定的内容一样，如果对象在用户的视图中变得很大或太过太多，则这些对象可能会 nauseating。</span><span class="sxs-lookup"><span data-stu-id="17417-128">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="17417-129">用户浏览并快速停止时，他们的感知告诉他们已停止。</span><span class="sxs-lookup"><span data-stu-id="17417-129">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="17417-130">它们的平衡通知他们打印头已停止转动，并使其视觉效果看起来很好。</span><span class="sxs-lookup"><span data-stu-id="17417-130">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="17417-131">但是，如果在用户停止时仍继续进行标记，则可能会混淆其感知。</span><span class="sxs-lookup"><span data-stu-id="17417-131">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="17417-132">用于 Unity 的 MRTK （混合现实工具包）中的 Billboarding 和标记</span><span class="sxs-lookup"><span data-stu-id="17417-132">Billboarding and Tag-along in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="17417-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为 Billboarding 和标记的行为提供脚本。</span><span class="sxs-lookup"><span data-stu-id="17417-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and Tag-along behavior.</span></span> <span data-ttu-id="17417-134">只需将 Billboard.cs 脚本分配到任何对象即可添加 billboarding 行为，并使对象始终为你。</span><span class="sxs-lookup"><span data-stu-id="17417-134">Simply assign Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="17417-135">若要添加标记和行为，请使用 RadialView.cs 脚本。</span><span class="sxs-lookup"><span data-stu-id="17417-135">To add tag-along behavior, use RadialView.cs script.</span></span> <span data-ttu-id="17417-136">可以调整各种选项，如 lerping 时间、距离和角度。</span><span class="sxs-lookup"><span data-stu-id="17417-136">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="17417-137">MRTK-径向视图规划求解</span><span class="sxs-lookup"><span data-stu-id="17417-137">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="17417-138">MRTK-布告栏脚本</span><span class="sxs-lookup"><span data-stu-id="17417-138">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="17417-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17417-139">See also</span></span>

* [<span data-ttu-id="17417-140">光标</span><span class="sxs-lookup"><span data-stu-id="17417-140">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="17417-141">手动 ray</span><span class="sxs-lookup"><span data-stu-id="17417-141">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="17417-142">Button</span><span class="sxs-lookup"><span data-stu-id="17417-142">Button</span></span>](button.md)
* [<span data-ttu-id="17417-143">可交互对象</span><span class="sxs-lookup"><span data-stu-id="17417-143">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="17417-144">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="17417-144">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="17417-145">起源</span><span class="sxs-lookup"><span data-stu-id="17417-145">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="17417-146">手动菜单</span><span class="sxs-lookup"><span data-stu-id="17417-146">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="17417-147">邻近菜单</span><span class="sxs-lookup"><span data-stu-id="17417-147">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="17417-148">对象集合</span><span class="sxs-lookup"><span data-stu-id="17417-148">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="17417-149">语音命令</span><span class="sxs-lookup"><span data-stu-id="17417-149">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="17417-150">键盘</span><span class="sxs-lookup"><span data-stu-id="17417-150">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="17417-151">提示</span><span class="sxs-lookup"><span data-stu-id="17417-151">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="17417-152">盖板</span><span class="sxs-lookup"><span data-stu-id="17417-152">Slate</span></span>](slate.md)
* [<span data-ttu-id="17417-153">滑块</span><span class="sxs-lookup"><span data-stu-id="17417-153">Slider</span></span>](slider.md)
* [<span data-ttu-id="17417-154">着色器</span><span class="sxs-lookup"><span data-stu-id="17417-154">Shader</span></span>](shader.md)
* [<span data-ttu-id="17417-155">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="17417-155">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="17417-156">显示进度</span><span class="sxs-lookup"><span data-stu-id="17417-156">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="17417-157">Surface 磁性</span><span class="sxs-lookup"><span data-stu-id="17417-157">Surface magnetism</span></span>](surface-magnetism.md)
