---
title: 空间音效设计
description: 空间音效是用于混合现实应用程序中的浸入式、可访问性和 UX 设计的强大工具。
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 空间音质, 设计, 样式
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750313"
---
# <a name="spatial-sound-design"></a><span data-ttu-id="054f2-104">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="054f2-104">Spatial sound design</span></span>

<span data-ttu-id="054f2-105">空间音效是用于混合现实应用程序中的浸入式、可访问性和 UX 设计的强大工具。</span><span class="sxs-lookup"><span data-stu-id="054f2-105">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

<span data-ttu-id="054f2-106">如果您曾玩过[Marco 水球](https://en.wikipedia.org/wiki/Marco_Polo_(game)), 或者有人打电话打电话来帮助您找到它, 您已经熟悉了空间音效的重要性。</span><span class="sxs-lookup"><span data-stu-id="054f2-106">If you've ever played [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), or had someone call your phone to help you locate it, you are already familiar with the importance of spatial sound.</span></span> <span data-ttu-id="054f2-107">我们会在日常生活中使用声音提示来查找对象、了解用户的注意力, 或更好地了解我们的环境。</span><span class="sxs-lookup"><span data-stu-id="054f2-107">We use sound cues in our daily lives to locate objects, get someone's attention, or get a better understanding of our environment.</span></span> <span data-ttu-id="054f2-108">应用的声音行为与现实世界中的行为更加接近, 虚拟世界的说服力就越多。</span><span class="sxs-lookup"><span data-stu-id="054f2-108">The more closely your app's sound behaves like it does in the real world, the more convincing and engaging your virtual world will be.</span></span>

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a><span data-ttu-id="054f2-109">设备支持</span><span class="sxs-lookup"><span data-stu-id="054f2-109">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="054f2-110"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="054f2-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="054f2-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="054f2-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="054f2-112"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="054f2-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="054f2-113">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="054f2-113">Spatial sound design</span></span></td>
        <td><span data-ttu-id="054f2-114">✔️</span><span class="sxs-lookup"><span data-stu-id="054f2-114">✔️</span></span></td>
        <td><span data-ttu-id="054f2-115">✔️</span><span class="sxs-lookup"><span data-stu-id="054f2-115">✔️</span></span></td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a><span data-ttu-id="054f2-116">对于混合现实开发, 空间音效的四个关键因素</span><span class="sxs-lookup"><span data-stu-id="054f2-116">Four key things spatial sound does for mixed reality development</span></span>

<span data-ttu-id="054f2-117">默认情况下, 将以立体声播放声音。</span><span class="sxs-lookup"><span data-stu-id="054f2-117">By default, sounds are played back in stereo.</span></span> <span data-ttu-id="054f2-118">这意味着声音无空间位置就会播放, 因此用户不知道声音来自何处。</span><span class="sxs-lookup"><span data-stu-id="054f2-118">This means the sound will play with no spatial position, so the user does not know where the sound came from.</span></span> <span data-ttu-id="054f2-119">空间音效对于混合现实开发有四个关键因素:</span><span class="sxs-lookup"><span data-stu-id="054f2-119">Spatial sound does four key things for mixed reality development:</span></span>

<span data-ttu-id="054f2-120">**舌**</span><span class="sxs-lookup"><span data-stu-id="054f2-120">**Grounding**</span></span>

<span data-ttu-id="054f2-121">如果没有声音, 则当我们使我们失去了这些对象时, 虚拟对象会有效地停止存在。</span><span class="sxs-lookup"><span data-stu-id="054f2-121">Without sound, virtual objects effectively cease to exist when we turn our head away from them.</span></span> <span data-ttu-id="054f2-122">就像真实的对象一样, 即使您看不到这些对象, 而且您希望能够在您的任何位置找到这些对象, 也是如此。</span><span class="sxs-lookup"><span data-stu-id="054f2-122">Just like real objects, you want to be able to hear these objects even when you can't see them, and you want to be able to locate them anywhere around you.</span></span> <span data-ttu-id="054f2-123">正如需要以直观方式将虚拟对象与您的真实世界混合起来一样, 它们也需要呼叫时。</span><span class="sxs-lookup"><span data-stu-id="054f2-123">Just as virtual objects need to be grounded visually to blend with your real world, they also need to be grounded audibly.</span></span> <span data-ttu-id="054f2-124">空间音效将您的真实世界音频环境与数字音频环境无缝混合。</span><span class="sxs-lookup"><span data-stu-id="054f2-124">Spatial sound seamlessly blends your real world audio environment with the digital audio environment.</span></span>

<span data-ttu-id="054f2-125">**用户注意**</span><span class="sxs-lookup"><span data-stu-id="054f2-125">**User attention**</span></span>

<span data-ttu-id="054f2-126">在混合现实体验中, 你不能想象你的用户在哪里寻找, 并希望他们看到你在世界上出现的内容。</span><span class="sxs-lookup"><span data-stu-id="054f2-126">In mixed reality experiences, you can't assume where your user is looking and expect them to see something you place in the world visually.</span></span> <span data-ttu-id="054f2-127">但即使播放声音的对象位于声音上, 用户也始终会听到声音播放。</span><span class="sxs-lookup"><span data-stu-id="054f2-127">But users can always hear a sound play even when the object playing the sound is behind them.</span></span> <span data-ttu-id="054f2-128">人们用声音来吸引他们的注意力-我们 instinctually 于我们听到的对象。</span><span class="sxs-lookup"><span data-stu-id="054f2-128">People are used to having their attention drawn by sound - we instinctually look toward an object that we hear around us.</span></span> <span data-ttu-id="054f2-129">当您想要将用户的注视定向到某个特定位置时, 而不是使用箭头将其指向特定位置时, 将声音置于该位置就是一种很自然的方式来指导他们。</span><span class="sxs-lookup"><span data-stu-id="054f2-129">When you want to direct your user's gaze to a particular place, rather than using an arrow to point them visually, placing a sound in that location is a very natural and fast way to guide them.</span></span>

<span data-ttu-id="054f2-130">**浸入式**</span><span class="sxs-lookup"><span data-stu-id="054f2-130">**Immersion**</span></span>

<span data-ttu-id="054f2-131">当对象移动或冲突时, 我们通常会听到材料之间的交互。</span><span class="sxs-lookup"><span data-stu-id="054f2-131">When objects move or collide, we usually hear those interactions between materials.</span></span> <span data-ttu-id="054f2-132">因此, 当您的对象不能与现实世界中的声音完全相同时, 就会丢失一浸入式, 比如观看大量电影, 使其一直向下移动。</span><span class="sxs-lookup"><span data-stu-id="054f2-132">So when your objects don't make the same sound they would in the real world, a level of immersion is lost - like watching a scary movie with the volume all the way down.</span></span> <span data-ttu-id="054f2-133">现实世界中的所有声音都来自空间中的某个特定点-当我们转向我们的头时, 我们会听到这些声音相对于我们的耳的变化, 我们可以以这种方式跟踪任何声音的位置。</span><span class="sxs-lookup"><span data-stu-id="054f2-133">All sounds in the real world come from a particular point in space - when we turn our heads, we hear the change in where those sounds are coming from relative to our ears, and we can track the location of any sound this way.</span></span> <span data-ttu-id="054f2-134">Spatialized 听起来就是我们所能看到的内容的 "感觉"。</span><span class="sxs-lookup"><span data-stu-id="054f2-134">Spatialized sounds make up the "feel" of a place beyond what we can see.</span></span>

<span data-ttu-id="054f2-135">**交互设计**</span><span class="sxs-lookup"><span data-stu-id="054f2-135">**Interaction design**</span></span>

<span data-ttu-id="054f2-136">在大多数传统的交互式体验中, 会以标准 mono 或立体声播放诸如 UI 声音效果之类的交互音。</span><span class="sxs-lookup"><span data-stu-id="054f2-136">In most traditional interactive experiences, interaction sounds like UI sound effects are played in standard mono or stereo.</span></span> <span data-ttu-id="054f2-137">但由于在三维空间中存在混合现实中的所有内容-包括 UI, 因此这些对象从 spatialized 的声音中获益。</span><span class="sxs-lookup"><span data-stu-id="054f2-137">But because everything in mixed reality exists in 3D space - including the UI - these objects benefit from spatialized sounds.</span></span> <span data-ttu-id="054f2-138">当我们在现实世界中按下某个按钮时, 听到的声音来自该按钮。</span><span class="sxs-lookup"><span data-stu-id="054f2-138">When we press a button in the real world, the sound we hear comes from that button.</span></span> <span data-ttu-id="054f2-139">通过 spatializing 的互动声音, 我们再次提供了更自然、真实的用户体验。</span><span class="sxs-lookup"><span data-stu-id="054f2-139">By spatializing interaction sounds, we again provide a more natural and realistic user experience.</span></span>

## <a name="best-practices-when-using-spatial-sound"></a><span data-ttu-id="054f2-140">使用空间音效时的最佳做法</span><span class="sxs-lookup"><span data-stu-id="054f2-140">Best practices when using spatial sound</span></span>

<span data-ttu-id="054f2-141">**真实声音比合成或非自然的声音更好**</span><span class="sxs-lookup"><span data-stu-id="054f2-141">**Real sounds work better than synthesized or unnatural sounds**</span></span>

<span data-ttu-id="054f2-142">您的用户使用某种类型的声音就越熟悉, 感觉就越真实, 而且他们在环境中的定位就越容易。</span><span class="sxs-lookup"><span data-stu-id="054f2-142">The more familiar your user is with a type of sound, the more real it will feel, and the more easily they will be able to locate it in their environment.</span></span> <span data-ttu-id="054f2-143">例如, 人为声音, 就是一种非常常见的声音, 用户将找到它, 就像聊天室中的真实人员一样。</span><span class="sxs-lookup"><span data-stu-id="054f2-143">A human voice, for example, is a very common type of sound, and your users will locate it just as quickly as a real person in the room talking to them.</span></span>

<span data-ttu-id="054f2-144">**预期胜过模拟**</span><span class="sxs-lookup"><span data-stu-id="054f2-144">**Expectation trumps simulation**</span></span>

<span data-ttu-id="054f2-145">如果你使用的是来自特定方向的声音, 则会在该方向上引导你注意, 而不考虑空间提示。例如, 在大多数情况下, 我们听到了鸟, 就在这里。</span><span class="sxs-lookup"><span data-stu-id="054f2-145">If you are used to a sound coming from a particular direction, your attention will be guided in that direction regardless of spatial cues. For example, most of the time that we hear birds, they are above us.</span></span> <span data-ttu-id="054f2-146">播放 "鸟" 的声音很可能会导致用户进行查找, 即使您将声音置于其下面也是如此。</span><span class="sxs-lookup"><span data-stu-id="054f2-146">Playing the sound of a bird will most likely cause your user to look up, even if you place the sound below them.</span></span> <span data-ttu-id="054f2-147">这通常会造成混淆, 建议你使用这些预期, 而不是为了获得更自然的体验。</span><span class="sxs-lookup"><span data-stu-id="054f2-147">This is usually confusing, and it is recommended that you work with expectations like these rather than going against them for a more natural experience.</span></span>

<span data-ttu-id="054f2-148">**大多数声音应为 spatialized**</span><span class="sxs-lookup"><span data-stu-id="054f2-148">**Most sounds should be spatialized**</span></span>

<span data-ttu-id="054f2-149">如上所述, 混合现实中的所有内容都位于3D 空间中-你的声音也应该也是。</span><span class="sxs-lookup"><span data-stu-id="054f2-149">As mentioned above, everything in Mixed Reality exists in 3D space - your sounds should as well.</span></span> <span data-ttu-id="054f2-150">甚至音乐有时可以从 spatialization 中获益, 特别是当它绑定到某个菜单或其他一些 UI 时。</span><span class="sxs-lookup"><span data-stu-id="054f2-150">Even music can sometimes benefit from spatialization, particularly when it's tied to a menu or some other UI.</span></span>

<span data-ttu-id="054f2-151">**避免不可见的发射器**</span><span class="sxs-lookup"><span data-stu-id="054f2-151">**Avoid invisible emitters**</span></span>

<span data-ttu-id="054f2-152">由于我们已经过检测到我们听到的声音, 因此, 它可能是一个非自然甚至 unnerving 的体验来寻找没有视觉对象的声音。</span><span class="sxs-lookup"><span data-stu-id="054f2-152">Because we've been conditioned to look at sounds that we hear around us, it can be an unnatural and even unnerving experience to locate a sound that has no visual presence.</span></span> <span data-ttu-id="054f2-153">现实生活中的声音不是空白空间, 因此, 如果音频发射器在用户的即时环境内, 还可以查看它。</span><span class="sxs-lookup"><span data-stu-id="054f2-153">Sounds in the real world don't come from empty space, so be sure that if an audio emitter is placed within the user's immediate environment that it can also be seen.</span></span>

<span data-ttu-id="054f2-154">**避免空间屏蔽**</span><span class="sxs-lookup"><span data-stu-id="054f2-154">**Avoid spatial masking**</span></span>

<span data-ttu-id="054f2-155">空间音效依赖于非常微妙的声音提示, 这些提示可以通过其他声音 overpowered。</span><span class="sxs-lookup"><span data-stu-id="054f2-155">Spatial sound relies on very subtle acoustic cues that can be overpowered by other sounds.</span></span> <span data-ttu-id="054f2-156">如果你有立体声音乐或环境声音, 请确保它们在组合中足够低, 以便为你的 spatialized 声音的详细信息提供空间, 使用户能够轻松找到这些声音, 并使其听起来真实和自然。</span><span class="sxs-lookup"><span data-stu-id="054f2-156">If you do have stereo music or ambient sounds, make sure they are low enough in the mix to give room for the details of your spatialized sounds that will allow your users to locate them easily, and keep them sounding realistic and natural.</span></span>

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a><span data-ttu-id="054f2-157">使用空间音效时要记住的一般概念</span><span class="sxs-lookup"><span data-stu-id="054f2-157">General concepts to keep in mind when using spatial sound</span></span>

<span data-ttu-id="054f2-158">**空间音效是一种模拟**</span><span class="sxs-lookup"><span data-stu-id="054f2-158">**Spatial sound is a simulation**</span></span>

<span data-ttu-id="054f2-159">空间音质最常使用的是与世界上的真实或虚拟对象 emanating 的声音。</span><span class="sxs-lookup"><span data-stu-id="054f2-159">The most frequent use of spatial sound is making a sound seem as though it is emanating from a real or virtual object in the world.</span></span> <span data-ttu-id="054f2-160">因此, spatialized 声音可能会从这类对象中获得最大意义。</span><span class="sxs-lookup"><span data-stu-id="054f2-160">Thus, spatialized sounds may make the most sense coming from such objects.</span></span>

<span data-ttu-id="054f2-161">请注意, 空间音质的感知准确性意味着声音不一定会从对象的中心发出, 因为这种差别会根据对象大小和用户之间的距离而明显。</span><span class="sxs-lookup"><span data-stu-id="054f2-161">Note that the perceived accuracy of spatial sound means that a sound shouldn't necessarily emit from the center of an object, as the difference will be noticeable depending on the size of the object and distance from the user.</span></span> <span data-ttu-id="054f2-162">对于小对象, 对象的中心点通常已足够。</span><span class="sxs-lookup"><span data-stu-id="054f2-162">With small objects, the center point of the object is usually sufficient.</span></span> <span data-ttu-id="054f2-163">对于较大的对象, 可能希望对象内特定位置的声音发射器或多个发射器产生声音。</span><span class="sxs-lookup"><span data-stu-id="054f2-163">For larger objects, you may want a sound emitter or multiple emitters at the specific location within the object that is supposed to be producing the sound.</span></span>

<span data-ttu-id="054f2-164">**规范化所有声音**</span><span class="sxs-lookup"><span data-stu-id="054f2-164">**Normalize all sounds**</span></span>

<span data-ttu-id="054f2-165">距离衰减在用户的第一次计量内快速发生, 就像在现实世界中一样。</span><span class="sxs-lookup"><span data-stu-id="054f2-165">Distance attenuation happens quickly within the first meter from the user, as it does in the real world.</span></span> <span data-ttu-id="054f2-166">应将所有音频文件标准化, 以确保物理准确的距离衰减, 并确保在几个时间计量 (适用时) 可以听到声音。</span><span class="sxs-lookup"><span data-stu-id="054f2-166">All audio files should be normalized to ensure physically accurate distance attenuation, and ensure that a sound can be heard when several meters away (when applicable).</span></span> <span data-ttu-id="054f2-167">空间音频引擎将处理声音所需的衰减, 使其看起来像是某个距离 (结合衰减和 "距离提示"), 并在最上面应用任何衰减, 这可能会减少影响。</span><span class="sxs-lookup"><span data-stu-id="054f2-167">The spatial audio engine will handle the attenuation necessary for a sound to "feel" like it's at a certain distance (with a combination of attenuation and "distance cues"), and applying any attenuation on top of that could reduce the effect.</span></span> <span data-ttu-id="054f2-168">在模拟实际对象之外,*空间音效*衰减的初始距离可能会超出适当的音频混合量。</span><span class="sxs-lookup"><span data-stu-id="054f2-168">Outside of simulating a real object, the initial distance decay of *spatial sound* sounds will likely be more than enough for a proper mix of your audio.</span></span>

<span data-ttu-id="054f2-169">**对象发现和用户界面**</span><span class="sxs-lookup"><span data-stu-id="054f2-169">**Object discovery and user interfaces**</span></span>

<span data-ttu-id="054f2-170">当使用音频提示使用户注意到超出其当前视图的效果时, 声音应声音并突出显示在混合范围内、任何立体声声音上, 以及可能会打乱方向音频提示的任何其他 spatialized 声音。</span><span class="sxs-lookup"><span data-stu-id="054f2-170">When using audio cues to direct the user's attention beyond their current view, the sound should be audible and prominent in the mix, well above any stereo sounds, and any other spatialized sounds which might distract from the directional audio cue.</span></span> <span data-ttu-id="054f2-171">对于与用户界面的元素 (例如菜单) 关联的声音和音乐, 声音发射器应附加到该对象。</span><span class="sxs-lookup"><span data-stu-id="054f2-171">For sounds and music that are associated with an element of the user interface (e.g. a menu), the sound emitter should be attached to that object.</span></span> <span data-ttu-id="054f2-172">立体声和其他非位置音频播放会使用户难以查找 spatialized 元素 (请参阅上面的内容:避免空间屏蔽)。</span><span class="sxs-lookup"><span data-stu-id="054f2-172">Stereo and other non-positional audio playing can make spatialized elements difficult for users to locate (See above: Avoid spatial masking).</span></span>

<span data-ttu-id="054f2-173">**尽可能多地使用标准三维声音上的空间音效**</span><span class="sxs-lookup"><span data-stu-id="054f2-173">**Use spatial sound over standard 3D sound as much as possible**</span></span>

<span data-ttu-id="054f2-174">在混合现实中, 为获得最佳用户体验, 应使用空间音效而不是传统的3D 音频技术来实现3D 音频。</span><span class="sxs-lookup"><span data-stu-id="054f2-174">In mixed reality, for the best user experience, 3D audio should be achieved using spatial sound rather than legacy 3D audio technologies.</span></span> <span data-ttu-id="054f2-175">通常, 改进后的 spatialization 值得一提的是标准三维声音的小型 CPU 成本。</span><span class="sxs-lookup"><span data-stu-id="054f2-175">In general, the improved spatialization is worth the small CPU cost over standard 3D sound.</span></span> <span data-ttu-id="054f2-176">标准3D 音频可用于低优先级声音、spatialized 但不一定与物理或虚拟对象相关的声音, 以及用户从不需要找到以与应用交互的对象。</span><span class="sxs-lookup"><span data-stu-id="054f2-176">Standard 3D audio can be used for low-priority sounds, sounds that are spatialized but not necessarily tied to a physical or virtual object, and objects that the user never need locate to interact with the app.</span></span>

## <a name="see-also"></a><span data-ttu-id="054f2-177">请参阅</span><span class="sxs-lookup"><span data-stu-id="054f2-177">See also</span></span>
* [<span data-ttu-id="054f2-178">空间音效</span><span class="sxs-lookup"><span data-stu-id="054f2-178">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="054f2-179">空间映射</span><span class="sxs-lookup"><span data-stu-id="054f2-179">Spatial mapping</span></span>](spatial-mapping.md)
