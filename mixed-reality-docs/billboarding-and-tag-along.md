---
title: Billboarding 和标记
description: 具有 billboarding 的对象始终向用户提供正面的定向。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，billboarding，连同标记
ms.openlocfilehash: 032e665d94a73b94b59f693e452874af0b45f021
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436996"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="c0c03-104">Billboarding 和标记</span><span class="sxs-lookup"><span data-stu-id="c0c03-104">Billboarding and tag-along</span></span>

<br>

<img src="images/billboarding-fragments.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">

<span data-ttu-id="c0c03-105">Billboarding 是一种可应用于混合现实中的对象的行为概念。</span><span class="sxs-lookup"><span data-stu-id="c0c03-105">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="c0c03-106">具有 billboarding 的对象始终向用户提供正面的定向。</span><span class="sxs-lookup"><span data-stu-id="c0c03-106">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="c0c03-107">这对于文本和 menuing 系统特别有用，在这种情况下，如果用户要四处移动，用户环境（全球锁定）中放置的静态对象将被掩盖或无法读取。</span><span class="sxs-lookup"><span data-stu-id="c0c03-107">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="c0c03-108">启用了 billboarding 的对象可以在用户的环境中自由旋转。</span><span class="sxs-lookup"><span data-stu-id="c0c03-108">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="c0c03-109">它们还可以根据设计注意事项限制为单个轴。</span><span class="sxs-lookup"><span data-stu-id="c0c03-109">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="c0c03-110">请记住，如果 billboarded 对象置于其他对象之前太近，或在 HoloLens 中太接近扫描面，则它们可能会被剪裁或遮蔽。</span><span class="sxs-lookup"><span data-stu-id="c0c03-110">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="c0c03-111">为避免出现这种情况，请考虑在为 billboarding 启用轴旋转时对象可能产生的总空间。</span><span class="sxs-lookup"><span data-stu-id="c0c03-111">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

## <a name="what-is-a-tag-along"></a><span data-ttu-id="c0c03-112">什么是标记？</span><span class="sxs-lookup"><span data-stu-id="c0c03-112">What is a tag-along?</span></span>

<span data-ttu-id="c0c03-113">标记-一起是可以添加到影像的行为概念，包括 billboarded 对象。</span><span class="sxs-lookup"><span data-stu-id="c0c03-113">Tag-along is a behavioral concept that can be added to holograms, including billboarded objects.</span></span> <span data-ttu-id="c0c03-114">这种交互是实现 head 锁定内容效果的更自然且友好的方式。</span><span class="sxs-lookup"><span data-stu-id="c0c03-114">This interaction is a more natural and friendly way of achieving the effect of head-locked content.</span></span> <span data-ttu-id="c0c03-115">标记靠后的对象将不会离开用户的视图。</span><span class="sxs-lookup"><span data-stu-id="c0c03-115">A tag-along object attempts to never leave the user's view.</span></span> <span data-ttu-id="c0c03-116">这样，用户就可以自由地与其前面的内容交互，同时还会看到其直接视图外的全息影像。</span><span class="sxs-lookup"><span data-stu-id="c0c03-116">This allows the user to freely interact with what is front of them while also still seeing the holograms outside their direct view.</span></span>

<span data-ttu-id="c0c03-117">![的 "HoloLens 引脚" 面板是有关标记的行为方式的很好示例](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c0c03-117">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="c0c03-118">*HoloLens "开始" 菜单是一个更好的标记和行为示例*</span><span class="sxs-lookup"><span data-stu-id="c0c03-118">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="c0c03-119">标记靠对象具有可对其行为方式进行微调的参数。</span><span class="sxs-lookup"><span data-stu-id="c0c03-119">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="c0c03-120">当用户在其环境中移动时，可以根据需要将内容移入或移出用户的行为。</span><span class="sxs-lookup"><span data-stu-id="c0c03-120">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="c0c03-121">用户移动时，内容将尝试在用户的绕中移动，并向视图边缘滑动，具体取决于用户的移动速度，可能会使内容暂时消失。</span><span class="sxs-lookup"><span data-stu-id="c0c03-121">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="c0c03-122">当用户 gazes 沿标记的对象时，它会更全面地进入视图。</span><span class="sxs-lookup"><span data-stu-id="c0c03-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="c0c03-123">将内容视为始终 "一目了然"，这样用户就不会忘记内容的方向。</span><span class="sxs-lookup"><span data-stu-id="c0c03-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="c0c03-124">其他参数可以通过橡皮带来使标记沿着对象的外观附加到用户的头。</span><span class="sxs-lookup"><span data-stu-id="c0c03-124">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="c0c03-125">抑制加速或减速为对象提供权重，使其感觉更真实地出现。</span><span class="sxs-lookup"><span data-stu-id="c0c03-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="c0c03-126">此春季行为是一种 affordance，可帮助用户构建准确的心理模型，说明如何进行标记。</span><span class="sxs-lookup"><span data-stu-id="c0c03-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="c0c03-127">当用户在标记沿模式下具有对象时，音频有助于提供附加的实用。</span><span class="sxs-lookup"><span data-stu-id="c0c03-127">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="c0c03-128">音频应强化移动速度;迅速走下来应提供更为明显的声音效果，同时，如果有任何效果，自然速度应具有最小的音频。</span><span class="sxs-lookup"><span data-stu-id="c0c03-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="c0c03-129">与真正的 head 锁定的内容一样，如果对象在用户的视图中变得很大或太过太多，则这些对象可能会 nauseating。</span><span class="sxs-lookup"><span data-stu-id="c0c03-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="c0c03-130">用户浏览并快速停止时，他们的感知告诉他们已停止。</span><span class="sxs-lookup"><span data-stu-id="c0c03-130">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="c0c03-131">它们的平衡通知他们打印头已停止转动，并使其视觉效果看起来很好。</span><span class="sxs-lookup"><span data-stu-id="c0c03-131">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="c0c03-132">但是，如果在用户停止时仍继续进行标记，则可能会混淆其感知。</span><span class="sxs-lookup"><span data-stu-id="c0c03-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0c03-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0c03-133">See also</span></span>
* [<span data-ttu-id="c0c03-134">光标</span><span class="sxs-lookup"><span data-stu-id="c0c03-134">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c0c03-135">本能交互</span><span class="sxs-lookup"><span data-stu-id="c0c03-135">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="c0c03-136">舒适</span><span class="sxs-lookup"><span data-stu-id="c0c03-136">Comfort</span></span>](comfort.md)
