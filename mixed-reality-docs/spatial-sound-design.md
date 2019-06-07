---
title: 空间合理的设计
description: 声音空间是用于浸入式、 可访问性，并在混合的现实应用程序中的用户体验设计的强大工具。
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，空间声音、 设计、 样式
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750313"
---
# <a name="spatial-sound-design"></a><span data-ttu-id="81a00-104">空间合理的设计</span><span class="sxs-lookup"><span data-stu-id="81a00-104">Spatial sound design</span></span>

<span data-ttu-id="81a00-105">声音空间是用于浸入式、 可访问性，并在混合的现实应用程序中的用户体验设计的强大工具。</span><span class="sxs-lookup"><span data-stu-id="81a00-105">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

<span data-ttu-id="81a00-106">如果您以前曾经玩游戏[Marco 马](https://en.wikipedia.org/wiki/Marco_Polo_(game))，或必须有人调用您的电话以帮助你找到它，你已熟悉空间声音的重要性。</span><span class="sxs-lookup"><span data-stu-id="81a00-106">If you've ever played [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), or had someone call your phone to help you locate it, you are already familiar with the importance of spatial sound.</span></span> <span data-ttu-id="81a00-107">我们在日常生活中我们使用声音提示来查找对象，获取某人的关注，或获取更好地了解我们的环境。</span><span class="sxs-lookup"><span data-stu-id="81a00-107">We use sound cues in our daily lives to locate objects, get someone's attention, or get a better understanding of our environment.</span></span> <span data-ttu-id="81a00-108">更紧密地应用的声音的行为像现实世界、 更可信和具有吸引力的将虚拟世界中一样。</span><span class="sxs-lookup"><span data-stu-id="81a00-108">The more closely your app's sound behaves like it does in the real world, the more convincing and engaging your virtual world will be.</span></span>

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a><span data-ttu-id="81a00-109">设备支持</span><span class="sxs-lookup"><span data-stu-id="81a00-109">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="81a00-110"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="81a00-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="81a00-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="81a00-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="81a00-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></span><span class="sxs-lookup"><span data-stu-id="81a00-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="81a00-113">空间合理的设计</span><span class="sxs-lookup"><span data-stu-id="81a00-113">Spatial sound design</span></span></td>
        <td><span data-ttu-id="81a00-114">✔️</span><span class="sxs-lookup"><span data-stu-id="81a00-114">✔️</span></span></td>
        <td><span data-ttu-id="81a00-115">✔️</span><span class="sxs-lookup"><span data-stu-id="81a00-115">✔️</span></span></td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a><span data-ttu-id="81a00-116">为混合的现实开发完成了四个重要事项空间声音</span><span class="sxs-lookup"><span data-stu-id="81a00-116">Four key things spatial sound does for mixed reality development</span></span>

<span data-ttu-id="81a00-117">默认情况下，在立体声设备中可以重新播放声音。</span><span class="sxs-lookup"><span data-stu-id="81a00-117">By default, sounds are played back in stereo.</span></span> <span data-ttu-id="81a00-118">这意味着播放声音与没有空间的位置，以便用户不知道声音原来所在的位置。</span><span class="sxs-lookup"><span data-stu-id="81a00-118">This means the sound will play with no spatial position, so the user does not know where the sound came from.</span></span> <span data-ttu-id="81a00-119">空间声音执行混合的现实开发的四个重要事项：</span><span class="sxs-lookup"><span data-stu-id="81a00-119">Spatial sound does four key things for mixed reality development:</span></span>

<span data-ttu-id="81a00-120">**不断掌握新知识**</span><span class="sxs-lookup"><span data-stu-id="81a00-120">**Grounding**</span></span>

<span data-ttu-id="81a00-121">而无需声音，虚拟对象有效地停止时，我们就把我们头背对他们存在。</span><span class="sxs-lookup"><span data-stu-id="81a00-121">Without sound, virtual objects effectively cease to exist when we turn our head away from them.</span></span> <span data-ttu-id="81a00-122">就像真实的对象，你想要能够听到这些对象，即使您不能查看它们，并且你想要能周围任何位置查找。</span><span class="sxs-lookup"><span data-stu-id="81a00-122">Just like real objects, you want to be able to hear these objects even when you can't see them, and you want to be able to locate them anywhere around you.</span></span> <span data-ttu-id="81a00-123">就像虚拟对象需要以可视方式接地进行混合与真实世界，它们还需要呼叫接地。</span><span class="sxs-lookup"><span data-stu-id="81a00-123">Just as virtual objects need to be grounded visually to blend with your real world, they also need to be grounded audibly.</span></span> <span data-ttu-id="81a00-124">空间声音无缝地混合现实世界音频环境与数字音频环境。</span><span class="sxs-lookup"><span data-stu-id="81a00-124">Spatial sound seamlessly blends your real world audio environment with the digital audio environment.</span></span>

<span data-ttu-id="81a00-125">**用户注意**</span><span class="sxs-lookup"><span data-stu-id="81a00-125">**User attention**</span></span>

<span data-ttu-id="81a00-126">在混合的现实体验，将不能假定你的用户正在和希望看到的内容将放在世界上以可视方式。</span><span class="sxs-lookup"><span data-stu-id="81a00-126">In mixed reality experiences, you can't assume where your user is looking and expect them to see something you place in the world visually.</span></span> <span data-ttu-id="81a00-127">但用户始终可以听到声音播放甚至播放声音的对象是其背后提供支持。</span><span class="sxs-lookup"><span data-stu-id="81a00-127">But users can always hear a sound play even when the object playing the sound is behind them.</span></span> <span data-ttu-id="81a00-128">人们已习惯于具有由声音-绘制其关注我们 instinctually 寻找我们听到周围的对象。</span><span class="sxs-lookup"><span data-stu-id="81a00-128">People are used to having their attention drawn by sound - we instinctually look toward an object that we hear around us.</span></span> <span data-ttu-id="81a00-129">当你想要将定向到特定位置，而不是一个箭头，用于以可视方式，将它们指定的用户的视线移动，因为位置是非常自然和快速的方式来指导他们将声音。</span><span class="sxs-lookup"><span data-stu-id="81a00-129">When you want to direct your user's gaze to a particular place, rather than using an arrow to point them visually, placing a sound in that location is a very natural and fast way to guide them.</span></span>

<span data-ttu-id="81a00-130">**深入探讨**</span><span class="sxs-lookup"><span data-stu-id="81a00-130">**Immersion**</span></span>

<span data-ttu-id="81a00-131">当对象移动或发生冲突时，我们经常听到他们这些材料之间的交互。</span><span class="sxs-lookup"><span data-stu-id="81a00-131">When objects move or collide, we usually hear those interactions between materials.</span></span> <span data-ttu-id="81a00-132">因此当您的对象不像在现实世界的同一个声音，浸入式的级别是丢失-想一直向下看该卷的可怕电影。</span><span class="sxs-lookup"><span data-stu-id="81a00-132">So when your objects don't make the same sound they would in the real world, a level of immersion is lost - like watching a scary movie with the volume all the way down.</span></span> <span data-ttu-id="81a00-133">在现实世界中的所有声音都来自空间-中的特定点，当我们转头，我们听到中这些声音来源相对于我们的耳朵，更改，我们可以跟踪的位置的任何声音这种方式。</span><span class="sxs-lookup"><span data-stu-id="81a00-133">All sounds in the real world come from a particular point in space - when we turn our heads, we hear the change in where those sounds are coming from relative to our ears, and we can track the location of any sound this way.</span></span> <span data-ttu-id="81a00-134">Spatialized 的声音构成了超出我们可以看到哪些内容的位置的"感觉"。</span><span class="sxs-lookup"><span data-stu-id="81a00-134">Spatialized sounds make up the "feel" of a place beyond what we can see.</span></span>

<span data-ttu-id="81a00-135">**交互设计**</span><span class="sxs-lookup"><span data-stu-id="81a00-135">**Interaction design**</span></span>

<span data-ttu-id="81a00-136">在大多数传统的交互体验，将按标准 mono 或立体声播放交互听起来像 UI 声音效果。</span><span class="sxs-lookup"><span data-stu-id="81a00-136">In most traditional interactive experiences, interaction sounds like UI sound effects are played in standard mono or stereo.</span></span> <span data-ttu-id="81a00-137">但是，因为混合现实中的所有内容 （包括 UI） 的 3D 空间中存在这些对象从 spatialized 声音中获益。</span><span class="sxs-lookup"><span data-stu-id="81a00-137">But because everything in mixed reality exists in 3D space - including the UI - these objects benefit from spatialized sounds.</span></span> <span data-ttu-id="81a00-138">当我们按现实生活中的按钮时，我们听到的声音来自该按钮。</span><span class="sxs-lookup"><span data-stu-id="81a00-138">When we press a button in the real world, the sound we hear comes from that button.</span></span> <span data-ttu-id="81a00-139">通过 spatializing 交互声音，我们再次提供更自然而真实的用户体验。</span><span class="sxs-lookup"><span data-stu-id="81a00-139">By spatializing interaction sounds, we again provide a more natural and realistic user experience.</span></span>

## <a name="best-practices-when-using-spatial-sound"></a><span data-ttu-id="81a00-140">使用空间的声音时的最佳做法</span><span class="sxs-lookup"><span data-stu-id="81a00-140">Best practices when using spatial sound</span></span>

<span data-ttu-id="81a00-141">**实际声音效果更佳合成或非自然的声音**</span><span class="sxs-lookup"><span data-stu-id="81a00-141">**Real sounds work better than synthesized or unnatural sounds**</span></span>

<span data-ttu-id="81a00-142">越熟悉你的用户是使用一种类型的声音，会发现它的多个实际而更轻松地他们将能够在其环境中找到它。</span><span class="sxs-lookup"><span data-stu-id="81a00-142">The more familiar your user is with a type of sound, the more real it will feel, and the more easily they will be able to locate it in their environment.</span></span> <span data-ttu-id="81a00-143">人类声音，例如，是非常常见的声音，类型和您的用户将找到它只是最快的速度是真实的人与他们交谈，聊天室中。</span><span class="sxs-lookup"><span data-stu-id="81a00-143">A human voice, for example, is a very common type of sound, and your users will locate it just as quickly as a real person in the room talking to them.</span></span>

<span data-ttu-id="81a00-144">**假定条件下优先于模拟**</span><span class="sxs-lookup"><span data-stu-id="81a00-144">**Expectation trumps simulation**</span></span>

<span data-ttu-id="81a00-145">如果你习惯使用声音来自特定方向，将在该方向而不考虑空间提示引导式关注。例如，大多数情况下我们听到鸟，它们是我们上面。</span><span class="sxs-lookup"><span data-stu-id="81a00-145">If you are used to a sound coming from a particular direction, your attention will be guided in that direction regardless of spatial cues. For example, most of the time that we hear birds, they are above us.</span></span> <span data-ttu-id="81a00-146">即使您将其下面的声音播放声音鸟很可能会导致在表面上看您用户。</span><span class="sxs-lookup"><span data-stu-id="81a00-146">Playing the sound of a bird will most likely cause your user to look up, even if you place the sound below them.</span></span> <span data-ttu-id="81a00-147">这是通常令人困惑，并且建议使用如这些一点，而不是对其进行更自然的体验的期望。</span><span class="sxs-lookup"><span data-stu-id="81a00-147">This is usually confusing, and it is recommended that you work with expectations like these rather than going against them for a more natural experience.</span></span>

<span data-ttu-id="81a00-148">**应 spatialized 大多数声音**</span><span class="sxs-lookup"><span data-stu-id="81a00-148">**Most sounds should be spatialized**</span></span>

<span data-ttu-id="81a00-149">如上所述，混合现实中的所有内容在 3D 空间中存在-也应将声音。</span><span class="sxs-lookup"><span data-stu-id="81a00-149">As mentioned above, everything in Mixed Reality exists in 3D space - your sounds should as well.</span></span> <span data-ttu-id="81a00-150">尤其是在其关联到菜单或一些其他 UI 时，甚至音乐有时可以受益于 spatialization。</span><span class="sxs-lookup"><span data-stu-id="81a00-150">Even music can sometimes benefit from spatialization, particularly when it's tied to a menu or some other UI.</span></span>

<span data-ttu-id="81a00-151">**避免不可见发射器**</span><span class="sxs-lookup"><span data-stu-id="81a00-151">**Avoid invisible emitters**</span></span>

<span data-ttu-id="81a00-152">我们已被限制来看看我们围绕我们听到的声音，因为它可以是一种不自然甚至 unnerving 的体验来查找具有不会显示出来的声音。</span><span class="sxs-lookup"><span data-stu-id="81a00-152">Because we've been conditioned to look at sounds that we hear around us, it can be an unnatural and even unnerving experience to locate a sound that has no visual presence.</span></span> <span data-ttu-id="81a00-153">在现实世界中声音不来自空白区域，因此请确保，如果音频发射器放置，它也可以查看用户的即时环境中。</span><span class="sxs-lookup"><span data-stu-id="81a00-153">Sounds in the real world don't come from empty space, so be sure that if an audio emitter is placed within the user's immediate environment that it can also be seen.</span></span>

<span data-ttu-id="81a00-154">**避免空间屏蔽**</span><span class="sxs-lookup"><span data-stu-id="81a00-154">**Avoid spatial masking**</span></span>

<span data-ttu-id="81a00-155">空间声音依赖于可以通过其他声音 overpowered 的非常微妙声学提示。</span><span class="sxs-lookup"><span data-stu-id="81a00-155">Spatial sound relies on very subtle acoustic cues that can be overpowered by other sounds.</span></span> <span data-ttu-id="81a00-156">如果你具有立体声音乐或环境的声音，请确保它们是够低，以便你将允许用户轻松找到它们，并使它们听起来现实和自然的 spatialized 声音的详细信息的空间的组合中。</span><span class="sxs-lookup"><span data-stu-id="81a00-156">If you do have stereo music or ambient sounds, make sure they are low enough in the mix to give room for the details of your spatialized sounds that will allow your users to locate them easily, and keep them sounding realistic and natural.</span></span>

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a><span data-ttu-id="81a00-157">使用空间的声音时，需要注意的一般概念</span><span class="sxs-lookup"><span data-stu-id="81a00-157">General concepts to keep in mind when using spatial sound</span></span>

<span data-ttu-id="81a00-158">**空间的声音是模拟**</span><span class="sxs-lookup"><span data-stu-id="81a00-158">**Spatial sound is a simulation**</span></span>

<span data-ttu-id="81a00-159">使用最频繁的空间声音正在看起来就好像它从世界上的真实或虚拟对象发出声音。</span><span class="sxs-lookup"><span data-stu-id="81a00-159">The most frequent use of spatial sound is making a sound seem as though it is emanating from a real or virtual object in the world.</span></span> <span data-ttu-id="81a00-160">因此，spatialized 听起来可能会使来自此类对象的最大价值。</span><span class="sxs-lookup"><span data-stu-id="81a00-160">Thus, spatialized sounds may make the most sense coming from such objects.</span></span>

<span data-ttu-id="81a00-161">请注意，将具体取决于大小的对象和用户的距离明显的空间声音一定不应从对象的不同之处的中心发出的声音方式感知到的准确性。</span><span class="sxs-lookup"><span data-stu-id="81a00-161">Note that the perceived accuracy of spatial sound means that a sound shouldn't necessarily emit from the center of an object, as the difference will be noticeable depending on the size of the object and distance from the user.</span></span> <span data-ttu-id="81a00-162">使用小对象，该对象的中心点就足够了。</span><span class="sxs-lookup"><span data-stu-id="81a00-162">With small objects, the center point of the object is usually sufficient.</span></span> <span data-ttu-id="81a00-163">对于较大的对象，您可能希望声音发射器或多个发射器中应会发出声音的对象的特定位置。</span><span class="sxs-lookup"><span data-stu-id="81a00-163">For larger objects, you may want a sound emitter or multiple emitters at the specific location within the object that is supposed to be producing the sound.</span></span>

<span data-ttu-id="81a00-164">**规范化听上去**</span><span class="sxs-lookup"><span data-stu-id="81a00-164">**Normalize all sounds**</span></span>

<span data-ttu-id="81a00-165">距离衰减发生快速在从用户的第一个指示器中，在现实世界中一样。</span><span class="sxs-lookup"><span data-stu-id="81a00-165">Distance attenuation happens quickly within the first meter from the user, as it does in the real world.</span></span> <span data-ttu-id="81a00-166">应规范化所有音频文件，以确保以物理方式准确距离衰减，并确保可以播放音频时多个计量消失 （如果适用）。</span><span class="sxs-lookup"><span data-stu-id="81a00-166">All audio files should be normalized to ensure physically accurate distance attenuation, and ensure that a sound can be heard when several meters away (when applicable).</span></span> <span data-ttu-id="81a00-167">空间音频引擎将处理一种声音"感觉"像是在一定差别范围 （包括衰减和"距离提示"的组合），并基于该应用任何衰减无法降低影响所需的衰减。</span><span class="sxs-lookup"><span data-stu-id="81a00-167">The spatial audio engine will handle the attenuation necessary for a sound to "feel" like it's at a certain distance (with a combination of attenuation and "distance cues"), and applying any attenuation on top of that could reduce the effect.</span></span> <span data-ttu-id="81a00-168">外部模拟真实对象，初始距离的衰减*空间声音*听起来可能会足够适当多种音频。</span><span class="sxs-lookup"><span data-stu-id="81a00-168">Outside of simulating a real object, the initial distance decay of *spatial sound* sounds will likely be more than enough for a proper mix of your audio.</span></span>

<span data-ttu-id="81a00-169">**对象发现和用户接口**</span><span class="sxs-lookup"><span data-stu-id="81a00-169">**Object discovery and user interfaces**</span></span>

<span data-ttu-id="81a00-170">在使用音频提示直接超出其当前视图的用户的注意力，声音应声音和重要的组合，也更高版本的任何立体声的声音，可能会偏离方向的音频提示的任何其他 spatialized 的声音中。</span><span class="sxs-lookup"><span data-stu-id="81a00-170">When using audio cues to direct the user's attention beyond their current view, the sound should be audible and prominent in the mix, well above any stereo sounds, and any other spatialized sounds which might distract from the directional audio cue.</span></span> <span data-ttu-id="81a00-171">对于声音和音乐与用户界面 （例如菜单） 的元素相关联，声音发射器应附加到该对象。</span><span class="sxs-lookup"><span data-stu-id="81a00-171">For sounds and music that are associated with an element of the user interface (e.g. a menu), the sound emitter should be attached to that object.</span></span> <span data-ttu-id="81a00-172">立体声和其他非位置的音频播放可以使 spatialized 的元素难以查找的用户 (如上所示：避免空间屏蔽）。</span><span class="sxs-lookup"><span data-stu-id="81a00-172">Stereo and other non-positional audio playing can make spatialized elements difficult for users to locate (See above: Avoid spatial masking).</span></span>

<span data-ttu-id="81a00-173">**通过标准的三维声音尽可能多地使用空间的声音**</span><span class="sxs-lookup"><span data-stu-id="81a00-173">**Use spatial sound over standard 3D sound as much as possible**</span></span>

<span data-ttu-id="81a00-174">在混合现实中，为获得最佳的用户体验，应使用空间声音而不是旧的 3D 音频技术实现 3D 音频。</span><span class="sxs-lookup"><span data-stu-id="81a00-174">In mixed reality, for the best user experience, 3D audio should be achieved using spatial sound rather than legacy 3D audio technologies.</span></span> <span data-ttu-id="81a00-175">一般情况下，改进了的 spatialization 值得小的 CPU 成本对标准 3D 声音。</span><span class="sxs-lookup"><span data-stu-id="81a00-175">In general, the improved spatialization is worth the small CPU cost over standard 3D sound.</span></span> <span data-ttu-id="81a00-176">标准的三维音频可以用于低优先级声音、 声音 spatialized 但不一定绑定到物理或虚拟对象和用户永远不会需要找到与应用交互的对象。</span><span class="sxs-lookup"><span data-stu-id="81a00-176">Standard 3D audio can be used for low-priority sounds, sounds that are spatialized but not necessarily tied to a physical or virtual object, and objects that the user never need locate to interact with the app.</span></span>

## <a name="see-also"></a><span data-ttu-id="81a00-177">请参阅</span><span class="sxs-lookup"><span data-stu-id="81a00-177">See also</span></span>
* [<span data-ttu-id="81a00-178">空间音效</span><span class="sxs-lookup"><span data-stu-id="81a00-178">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="81a00-179">空间映射</span><span class="sxs-lookup"><span data-stu-id="81a00-179">Spatial mapping</span></span>](spatial-mapping.md)
