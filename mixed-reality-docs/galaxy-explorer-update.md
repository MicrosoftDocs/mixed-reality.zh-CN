---
title: 针对 HoloLens 2 的 Galaxy 资源管理器创建
description: 欢迎使用更新 HoloLens 2 的 Galaxy 资源管理器的方法。 正如原始 Galaxy 资源管理器, 我们的团队将在 GitHub 上提供项目, 以确保社区具有完全访问权限。
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy 资源管理器, 案例研究, 项目, 示例
ms.openlocfilehash: 1e04b27ff0382d87f8e6a15ae2b7b2284fa020e6
ms.sourcegitcommit: be3631932ea1c88ac3ad8b2390c98c5a6e8b93ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/04/2019
ms.locfileid: "68776452"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a><span data-ttu-id="f61f4-105">针对 HoloLens 2 的 Galaxy 资源管理器创建</span><span class="sxs-lookup"><span data-stu-id="f61f4-105">The Making of Galaxy Explorer for HoloLens 2</span></span>

<span data-ttu-id="f61f4-106">欢迎使用更新 HoloLens 2 的 Galaxy 资源管理器的方法。</span><span class="sxs-lookup"><span data-stu-id="f61f4-106">Welcome to the journey of how we are updating Galaxy Explorer for HoloLens 2.</span></span> <span data-ttu-id="f61f4-107">[Galaxy 资源管理器](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy 资源管理器")最初是通过共享你的想法计划开发的, 它是一种用于 HoloLens (第一代) 的开源应用程序, 这是许多人的第一种混合现实体验之一。</span><span class="sxs-lookup"><span data-stu-id="f61f4-107">[Galaxy Explorer](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy Explorer") was originally developed as an open source application for HoloLens (1st gen) through the Share Your Idea program, and is one of the first mixed reality experiences many people had.</span></span> <span data-ttu-id="f61f4-108">现在我们正在更新它, 以获得[HoloLens 2 的全新功能](https://www.microsoft.com/hololens/hardware)。</span><span class="sxs-lookup"><span data-stu-id="f61f4-108">Now we are updating it for the [new and exciting capabilities of HoloLens 2](https://www.microsoft.com/hololens/hardware).</span></span>

<span data-ttu-id="f61f4-109">作为[Microsoft 混合现实工作室](galaxy-explorer-update.md#mixed-reality-studios)之一, 我们通常会开发商业级解决方案, 并在整个创意和开发过程中在目标平台上开发 & 测试。</span><span class="sxs-lookup"><span data-stu-id="f61f4-109">As one of the [Microsoft Mixed Reality Studios](galaxy-explorer-update.md#mixed-reality-studios), we usually develop commercial grade solutions and are developing & testing on target platforms throughout the creative and development process.</span></span> <span data-ttu-id="f61f4-110">现在, 我们有了一种独特的情况, 即目前尚不具有对 HoloLens 2 设备的访问权限, 但很高兴能够开始更新到 Galaxy 资源管理器。</span><span class="sxs-lookup"><span data-stu-id="f61f4-110">We now have the unique situation where don’t yet have access to HoloLens 2 devices, but are excited to start the updates to Galaxy Explorer.</span></span> <span data-ttu-id="f61f4-111">我们将使用框架和工具 (如[MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)) 来着手此项目, 因为我们和社区都可以使用这些框架和工具。</span><span class="sxs-lookup"><span data-stu-id="f61f4-111">We're embarking on this project utilizing the frameworks and tools (like [MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)) as they become available to us and the community - and we want to bring you along for the ride.</span></span>

<span data-ttu-id="f61f4-112">正如原始 Galaxy 资源管理器,[我们的团队](galaxy-explorer-update.md#meet-the-team)将在[GitHub 上提供项目](https://github.com/Microsoft/GalaxyExplorer), 以确保社区具有完全访问权限。</span><span class="sxs-lookup"><span data-stu-id="f61f4-112">Just like the original Galaxy Explorer, [our team](galaxy-explorer-update.md#meet-the-team) will be [open sourcing the project on GitHub](https://github.com/Microsoft/GalaxyExplorer) to ensure that the community has full access.</span></span> <span data-ttu-id="f61f4-113">我们还将在这里记录我们的旅程, 其中介绍了我们 undertook 从 MRTK v1 迁移到 MRTK v2 的方法, 我们如何根据 HoloLens 2 中提供的新功能增强体验, 以及我们如何确保 Galaxy 资源管理器保持多平台体验。</span><span class="sxs-lookup"><span data-stu-id="f61f4-113">We will also be documenting our journey here in complete transparency about the ways in which we undertook porting from MRTK v1 to MRTK v2, how we enhanced the experience based on the new features available in HoloLens 2, and how we ensured that Galaxy Explorer remained a multi-platform experience.</span></span> <span data-ttu-id="f61f4-114">因此, 无论你是在 HoloLens (第一代)、HoloLens 2、Windows Mixed Reality 耳机还是 Windows 10 桌面上观看 Galaxy 资源管理器, 我们都希望确保你有一个沉浸式体验, 并尽可能地欣赏旅程!</span><span class="sxs-lookup"><span data-stu-id="f61f4-114">So whether you're viewing Galaxy Explorer on HoloLens (1st gen), HoloLens 2, a Windows Mixed Reality headset or on your Windows 10 desktop, we want to ensure that you're having an immersive experience and enjoy the journey as much as we are!</span></span>

<span data-ttu-id="f61f4-115">此页面将在我们完成项目的过程中展开, 并链接到更详细的文章、代码、设计项目、附加的 MRTK v2 文档等, 为你提供内幕的项目。</span><span class="sxs-lookup"><span data-stu-id="f61f4-115">This page will expand as we progress through the project, and we'll link out to more detailed articles, code, design artefacts, additional MRTK v2 documentation, etc. to provide you with an insider's look at the project.</span></span>

## <a name="unveiling-the-new-logo"></a><span data-ttu-id="f61f4-116">揭示新徽标</span><span class="sxs-lookup"><span data-stu-id="f61f4-116">Unveiling the new logo</span></span>

<span data-ttu-id="f61f4-117">我们很高兴开始使用新的 Galaxy 资源管理器徽标的预览!</span><span class="sxs-lookup"><span data-stu-id="f61f4-117">We're excited to kick off with a preview of the new Galaxy Explorer logo!</span></span> <span data-ttu-id="f61f4-118">通过采用银河的方式将献给支付给原始徽标, 我们设计出了真实的可视化效果, 并更新了版式, 以提供更加时尚的新式外观。</span><span class="sxs-lookup"><span data-stu-id="f61f4-118">While paying homage to the original logo by featuring the Milky Way, we've designed a realistic visualization and updated the typography to provide a more sleek and modern feel.</span></span> <span data-ttu-id="f61f4-119">徽标中包含的抢先了解可查看其中一个新图标。</span><span class="sxs-lookup"><span data-stu-id="f61f4-119">Included in the logo is a sneak peek at one of the new icons.</span></span>

![新建 Galaxy 资源管理器徽标](images/ge-update-app-icon.png)

<span data-ttu-id="f61f4-121">徽标的设计和版式将为用户界面元素的总体外观和感觉设置音调。</span><span class="sxs-lookup"><span data-stu-id="f61f4-121">The design and typography of the logo will set the tone for the overall look and feel of UI elements throughout the experience.</span></span> 

## <a name="thinking-about-interactions"></a><span data-ttu-id="f61f4-122">考虑交互</span><span class="sxs-lookup"><span data-stu-id="f61f4-122">Thinking about interactions</span></span>

<span data-ttu-id="f61f4-123">作为一录音室, 我们兴奋了将 Galaxy 资源管理器移植到 HoloLens 2 的权限。</span><span class="sxs-lookup"><span data-stu-id="f61f4-123">As a creative studio, we were ecstatic about the privilege to port Galaxy Explorer to HoloLens 2.</span></span> <span data-ttu-id="f61f4-124">我们知道, 我们希望体验成为新设备的庆祝, 并说明混合现实能力仅限制为想象。</span><span class="sxs-lookup"><span data-stu-id="f61f4-124">We knew from the start that we wanted the experience to be a celebration of the new device and to demonstrate that Mixed Reality empowerment is limited only to the imagination.</span></span>

<span data-ttu-id="f61f4-125">HoloLens 2 使用户能够以自然的方式触摸、抓住和移动全息影像–它们的响应方式非常类似于真实的对象。</span><span class="sxs-lookup"><span data-stu-id="f61f4-125">HoloLens 2 allows users to touch, grasp, and move holograms in ways that feel natural – they respond a lot like real objects.</span></span> <span data-ttu-id="f61f4-126">完全表述的手模型非常惊人, 因为这样可以让用户看起来自然。</span><span class="sxs-lookup"><span data-stu-id="f61f4-126">Fully articulated hand models are amazing, because it lets users do what feels natural.</span></span> <span data-ttu-id="f61f4-127">例如, 每个人都以略有不同的方式挑选一个杯, 而不是实施一种特殊的方式来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="f61f4-127">For example, everybody picks up a cup slightly differently – and instead of enforcing one particular way to do it, HoloLens 2 lets you do it your way.</span></span>

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

<span data-ttu-id="f61f4-128">这是第一代 HoloLens 设备上基于空中分流的接口的重大变化。</span><span class="sxs-lookup"><span data-stu-id="f61f4-128">This is a big change from the Air Tap-based interfaces on first generation HoloLens devices.</span></span> <span data-ttu-id="f61f4-129">用户现在可以 "关闭" 和 "个人", 而不是从距离交互。</span><span class="sxs-lookup"><span data-stu-id="f61f4-129">Instead of interacting with holograms from a distance, users can now get "up close and personal".</span></span> <span data-ttu-id="f61f4-130">将现有体验移植到 HoloLens 2 或规划新的体验时, 务必要使自己熟悉全息影像的直接操作。</span><span class="sxs-lookup"><span data-stu-id="f61f4-130">When porting existing experiences over to HoloLens 2 or planning new ones, it is important to make yourself familiar with the direct manipulation of holograms.</span></span>

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a><span data-ttu-id="f61f4-131">直接操作与空间中的远距离</span><span class="sxs-lookup"><span data-stu-id="f61f4-131">Direct manipulation vs. the vast distances in space</span></span>

<span data-ttu-id="f61f4-132">这是一种神奇的体验, 能够实现并抓住地球并抓住。</span><span class="sxs-lookup"><span data-stu-id="f61f4-132">It is a magical experience to be able to reach out, grab a planet and hold it in your hand.</span></span> <span data-ttu-id="f61f4-133">这种方法的挑战在于太阳系的大小–非常巨大!</span><span class="sxs-lookup"><span data-stu-id="f61f4-133">The challenge with this approach is the size of the solar system – it's huge!</span></span> <span data-ttu-id="f61f4-134">用户需要浏览其空间, 使每个行星都能够与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="f61f4-134">The user would need to walk around their room to get close to each planet to be able to interact with it.</span></span>

<span data-ttu-id="f61f4-135">为了使用户能够与远离远处的对象进行交互, MRTK 提供了从用户掌上走出的手的光线, 作为手型的延伸。</span><span class="sxs-lookup"><span data-stu-id="f61f4-135">To allow users to interact with objects that are farther away, MRTK offers hand rays that shoot out from the center of the user's palm, acting as an extension of the hand.</span></span> <span data-ttu-id="f61f4-136">环形光标连接到射线的末尾, 以指示该射线与目标对象相交的位置。</span><span class="sxs-lookup"><span data-stu-id="f61f4-136">A donut-shaped cursor is attached to the end of the ray to indicate where the ray intersects with a target object.</span></span> <span data-ttu-id="f61f4-137">然后光标所指向的对象可以接收来自手的手势命令。</span><span class="sxs-lookup"><span data-stu-id="f61f4-137">The object that the cursor lands on can then receive gestural commands from the hand.</span></span> 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

<span data-ttu-id="f61f4-138">在 "Galaxy 资源管理器" 的原始版本中, 用户将以 "注视" 光标为地球, 然后单击 "空中" 将其调近。</span><span class="sxs-lookup"><span data-stu-id="f61f4-138">In the original version of Galaxy Explorer, the user would target a planet with the gaze cursor and then air tap to call it closer.</span></span> <span data-ttu-id="f61f4-139">将体验移植到 HoloLens 2 的最简单方法是采用这种行为, 并使用手型来选择行星。</span><span class="sxs-lookup"><span data-stu-id="f61f4-139">The easiest way to port the experience to HoloLens 2 is to take this behavior and use hand rays to select planets.</span></span> <span data-ttu-id="f61f4-140">虽然这是正常运行的, 但仍希望获得更多的功能。</span><span class="sxs-lookup"><span data-stu-id="f61f4-140">While this was functional, it left us wanting more.</span></span>

### <a name="back-to-the-drawing-board"></a><span data-ttu-id="f61f4-141">返回绘图板</span><span class="sxs-lookup"><span data-stu-id="f61f4-141">Back to the drawing board</span></span>

<span data-ttu-id="f61f4-142">我们一起介绍了可在现有交互基础上构建的 ideate。</span><span class="sxs-lookup"><span data-stu-id="f61f4-142">We came together to ideate what could be built on top of the existing interactions.</span></span> <span data-ttu-id="f61f4-143">思考是:尽管 HoloLens 2 使用户能够以自然的方式与全息影像交互, 但影像按定义不是真实的。</span><span class="sxs-lookup"><span data-stu-id="f61f4-143">The thinking was: Although HoloLens 2 allows users to interact with holograms in natural, realistic ways, holograms are by definition not real.</span></span> <span data-ttu-id="f61f4-144">因此, 只要用户的交互是变得合理的, 就不会有可能与真正的对象进行交互, 而是不是很重要。</span><span class="sxs-lookup"><span data-stu-id="f61f4-144">So as long as an interaction is plausible for the user, it doesn't matter if that interaction would be possible with a real object or not – we can make it possible.</span></span>

<span data-ttu-id="f61f4-145">我们研究的一个概念就是基于 telekinesis –处理对象的能力。</span><span class="sxs-lookup"><span data-stu-id="f61f4-145">One concept that we explored was based on telekinesis – the power to manipulate objects with one's mind.</span></span> <span data-ttu-id="f61f4-146">通常, 在超大英雄电影中, 一个人会与他们的想法联系起来, 并将一个对象调入他们的手中。</span><span class="sxs-lookup"><span data-stu-id="f61f4-146">Often seen in super hero movies, a person would reach out with their mind and call an object into their open hand.</span></span> <span data-ttu-id="f61f4-147">我们将使用一种更多的方法进行介绍, 并提供该概念如何工作的快速草图。</span><span class="sxs-lookup"><span data-stu-id="f61f4-147">We played around with the idea some more and came up with a quick sketch of how the concept could work.</span></span>

![强制抓取交互的概念](images/ge-update-interactions-concept-force-grab.png)

<span data-ttu-id="f61f4-149">用户会将手型点指向地球, 这将提供目标反馈。</span><span class="sxs-lookup"><span data-stu-id="f61f4-149">The user would point the hand ray at a planet, which would provide target feedback.</span></span> <span data-ttu-id="f61f4-150">随着用户的张开, 世界将通过神奇的强制向用户拉取, 直到它接近于获取它。</span><span class="sxs-lookup"><span data-stu-id="f61f4-150">As the user then extends their open hand, the planet would be pulled towards the user by a magical force until it is close enough to grab it.</span></span> <span data-ttu-id="f61f4-151">因此, 我们要实现交互: 强制获取的名称。</span><span class="sxs-lookup"><span data-stu-id="f61f4-151">Hence our name for the interaction: force grab.</span></span> <span data-ttu-id="f61f4-152">由于用户会将地球向外推, 它会再次返回到其轨道。</span><span class="sxs-lookup"><span data-stu-id="f61f4-152">As the user would push away the planet with their open hand, it would return again to its orbit.</span></span>

### <a name="force-grab-prototyping"></a><span data-ttu-id="f61f4-153">强制获取抽取原型</span><span class="sxs-lookup"><span data-stu-id="f61f4-153">Force grab prototyping</span></span>

<span data-ttu-id="f61f4-154">然后, 我们创建了多个原型来测试概念:交互的整体效果如何？</span><span class="sxs-lookup"><span data-stu-id="f61f4-154">We then created multiple prototypes to test the concept: How does the interaction feel overall?</span></span> <span data-ttu-id="f61f4-155">被调用的对象是否会在用户前面停止或一直到其上, 直到放置？</span><span class="sxs-lookup"><span data-stu-id="f61f4-155">Should the called object stop in front of the user or stick to their hands until placed?</span></span> <span data-ttu-id="f61f4-156">调用对象是否应在调用时更改大小或缩放？</span><span class="sxs-lookup"><span data-stu-id="f61f4-156">Should the called object change size or scale while being called?</span></span>

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a><span data-ttu-id="f61f4-157">在应用程序中实现强制抓取</span><span class="sxs-lookup"><span data-stu-id="f61f4-157">Implementing force grab into the application</span></span>

<span data-ttu-id="f61f4-158">当我们在行星上尝试抓住强制时, 我们意识到我们不得不改变阳历系统的刻度。</span><span class="sxs-lookup"><span data-stu-id="f61f4-158">When we tried the force grab on planets, we realized that we had to change the scale of the solar system.</span></span> <span data-ttu-id="f61f4-159">事实证明, 阳历系统的准确、中等大小的表示形式对于用户来说很难理解和导航, 他们不知道在何处进行查找。</span><span class="sxs-lookup"><span data-stu-id="f61f4-159">It turned out that an accurate, medium-sized representation of the solar system is difficult for users to understand and navigate - they did not know where to look.</span></span> <span data-ttu-id="f61f4-160">不过, 精确、小尺寸的表示形式使得某些行星太小, 无法轻松选择。</span><span class="sxs-lookup"><span data-stu-id="f61f4-160">However an accurate, small-sized-representation made some planets too small to be easily selected.</span></span> <span data-ttu-id="f61f4-161">因此, 行星的大小和阳历之间的间距设计为在中等大小的房间内自如, 同时保持相对准确性。</span><span class="sxs-lookup"><span data-stu-id="f61f4-161">As a result, the size of the planets and the spacing between solar objects was designed to feel comfortable within a medium-sized room while maintaining relative accuracy.</span></span>

<span data-ttu-id="f61f4-162">在开发冲刺 (sprint) 的更高阶段, 我们已有足够的高手, 足以让 MSFT 混合现实专家参与, 因此我们努力将其输入作为专家测试人员并在强制抓取交互中快速迭代。</span><span class="sxs-lookup"><span data-stu-id="f61f4-162">During the later stages of our development sprint, we were lucky enough to have fellow MSFT Mixed Reality experts in-house, so we got to work getting their input as expert testers and doing quick iterations on the force grab interaction.</span></span>

![来自 Kam 测试 Galaxy 资源管理器的预览版本](images/ge-update-user-testing.png)

<span data-ttu-id="f61f4-164">图片:来自 Kam, 高级设计主管, 对 Galaxy 资源管理器的工作进行测试。</span><span class="sxs-lookup"><span data-stu-id="f61f4-164">In picture: Jenny Kam, Senior Design Lead, testing a work-in-progress of Galaxy Explorer.</span></span>

### <a name="adding-affordances-for-targeting"></a><span data-ttu-id="f61f4-165">为目标添加实用</span><span class="sxs-lookup"><span data-stu-id="f61f4-165">Adding affordances for targeting</span></span>

<span data-ttu-id="f61f4-166">在 HoloLens 2 上 vspackage 时, 我们发现, 即使新的交互是自然而直观的, 全息影像仍保持不变: 无权重或 tactile sensations。</span><span class="sxs-lookup"><span data-stu-id="f61f4-166">As we experimented on HoloLens 2, we found that even though the new interactions are natural and intuitive, holograms remain the same: with no weight or tactile sensations.</span></span> <span data-ttu-id="f61f4-167">由于全息影像并不提供用户在与对象交互时接收的自然反馈, 因此我们需要创建它们。</span><span class="sxs-lookup"><span data-stu-id="f61f4-167">Since holograms don't provide natural feedback that humans are used to receiving when they interact with objects, we needed to create them.</span></span>

<span data-ttu-id="f61f4-168">我们考虑到了视觉对象和音频反馈, 用户将为其交互的各个阶段提供这些反馈, 因为强制获取机制是与 Galaxy 资源管理器进行交互的核心, 所以我们做了很多迭代。</span><span class="sxs-lookup"><span data-stu-id="f61f4-168">We thought about the visual and audio feedback that users would be provided for the various stages of their interactions, and since the force grab mechanism is central to interacting with Galaxy Explorer, we did many iterations.</span></span> <span data-ttu-id="f61f4-169">目标是为交互的每个阶段查找音频和视觉反馈的适当平衡: 集中于预期对象, 将其调用给用户, 然后将其发布。</span><span class="sxs-lookup"><span data-stu-id="f61f4-169">The aim was to find the right balance of audio and visual feedback for each stage of the interaction: focusing on the intended object, calling it to the user, and then releasing it.</span></span> <span data-ttu-id="f61f4-170">我们学到的是, 与我们过去用于 HoloLens (第一代) 相比, 需要比我们更多的音频和视觉反馈。</span><span class="sxs-lookup"><span data-stu-id="f61f4-170">What we learned is that significantly more audio and visual feedback was required to reinforce the interaction than we were used to for HoloLens (1st gen).</span></span>

![行星上的视觉对象实用](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a><span data-ttu-id="f61f4-172">添加实用以进行强制获取</span><span class="sxs-lookup"><span data-stu-id="f61f4-172">Adding affordances for force grab</span></span>
 
<span data-ttu-id="f61f4-173">随着音频和视觉对象实用的基本强制获取机制, 我们介绍了如何使选择的行星更易于用户识别。</span><span class="sxs-lookup"><span data-stu-id="f61f4-173">Once we had the basic force grab mechanism with audio and visual affordances, we looked at how to make selecting planets more user friendly.</span></span> <span data-ttu-id="f61f4-174">要解决以下两个主要方面:由于阳历系统是一种三维移动界面, 因此用户可以更灵活地了解如何以一致的方式来定位对象。</span><span class="sxs-lookup"><span data-stu-id="f61f4-174">There were two main things to address: Because the solar system is a 3D moving interface, there is added complexity for users to learn how to target objects consistently.</span></span> <span data-ttu-id="f61f4-175">这是一种复杂的情况, 那就是, 在选择对象时, 手型的速度非常快, 使行星以极快的速度向用户移动。</span><span class="sxs-lookup"><span data-stu-id="f61f4-175">This was compounded by the fact that the hand ray is very fast at selecting an object, making planets move towards the user incredibly quickly.</span></span>

<span data-ttu-id="f61f4-176">我们使用三个方面的解决方案来做到这一点。</span><span class="sxs-lookup"><span data-stu-id="f61f4-176">We approached this with a three-pronged solution.</span></span> <span data-ttu-id="f61f4-177">第一种方法非常直观: 降低选择过程的速度, 使行星更自然地处理用户。</span><span class="sxs-lookup"><span data-stu-id="f61f4-177">The first was fairly intuitive: slow down the selection process so that planets approach the user at a more natural pace.</span></span> <span data-ttu-id="f61f4-178">调整速度后, 我们必须重新访问音频和视觉对象实用, 并将其他音频反馈添加为用户跟踪的行星。</span><span class="sxs-lookup"><span data-stu-id="f61f4-178">Once the speed was adjusted, we had to revisit the audio and visual affordances, adding additional audio feedback as the planet tracked towards the user.</span></span>

<span data-ttu-id="f61f4-179">解决方案的第二部分是使整个强制抓取交互的可视化成为极有形的。</span><span class="sxs-lookup"><span data-stu-id="f61f4-179">The second part of the solution was to make the visualization of the entire force grab interaction extremely tangible.</span></span> <span data-ttu-id="f61f4-180">我们直观地显示了一条粗线条, 它在与目标对象连接后, 将其移至目标对象, 然后将该对象移回用户喜欢的套索。</span><span class="sxs-lookup"><span data-stu-id="f61f4-180">We visualized a thick line that moves towards the targeted object once the hand ray connects with it, and then brings the object back to the user - like a lasso.</span></span> 

![用于强制抓取的视觉 "套索" 实用](images/ge-update-lasso-affordances.png)

<span data-ttu-id="f61f4-182">最后, 我们优化了太阳系的规模, 以便用户看好行星, 并将其作为目标。</span><span class="sxs-lookup"><span data-stu-id="f61f4-182">Finally, we optimized the scale of the solar system so that the planets were large enough for the user's gaze and hand ray to target them.</span></span> 

<span data-ttu-id="f61f4-183">这三项改进允许用户进行精确选择, 并以直观的方式为他们打电话。</span><span class="sxs-lookup"><span data-stu-id="f61f4-183">These three improvements allowed users to make accurate selections, calling planets to them in an intuitive way.</span></span> <span data-ttu-id="f61f4-184">总体而言, 最终强制获取的效果是在太阳系中获得更具沉浸和交互性的体验。</span><span class="sxs-lookup"><span data-stu-id="f61f4-184">Overall, the effect of the final force grab is a more immersive and interactive experience in the solar system.</span></span>

## <a name="spotlight-on-jupiter"></a><span data-ttu-id="f61f4-185">在木星上聚焦</span><span class="sxs-lookup"><span data-stu-id="f61f4-185">Spotlight on Jupiter</span></span>

<span data-ttu-id="f61f4-186">以银河的方式创建日光体是一种 humbling 体验。</span><span class="sxs-lookup"><span data-stu-id="f61f4-186">Creating the solar bodies of the Milky Way was a humbling experience.</span></span> <span data-ttu-id="f61f4-187">具体而言, 木星的独特特性使其对瞧可见。</span><span class="sxs-lookup"><span data-stu-id="f61f4-187">In particular, the unique characteristics of Jupiter make it a sight to behold.</span></span> <span data-ttu-id="f61f4-188">它是气体巨量的最大和最丰富的质量, 并且比所有其他行星组合的质量大。</span><span class="sxs-lookup"><span data-stu-id="f61f4-188">It is the largest and most colorful of the gas giants, and contains more mass than all other planets combined.</span></span> <span data-ttu-id="f61f4-189">Turbulence 和 cloud dynamics 的非常大的大小和 mesmerizing 带区 prefect, 以实现特别的艺术。</span><span class="sxs-lookup"><span data-stu-id="f61f4-189">Its sheer size and mesmerizing bands of turbulence and cloud dynamics are prefect for special artistic attention.</span></span>

### <a name="geometry-and-meshes"></a><span data-ttu-id="f61f4-190">几何图形和网格</span><span class="sxs-lookup"><span data-stu-id="f61f4-190">Geometry and meshes</span></span>

<span data-ttu-id="f61f4-191">作为一气体, 木星的外部 shell 包含 gaseous 层。</span><span class="sxs-lookup"><span data-stu-id="f61f4-191">As a gas giant, Jupiter's outer shells consists of gaseous layers.</span></span> <span data-ttu-id="f61f4-192">它的快速旋转速度、内部热交换和 Coriolis 强制的结合会创建色彩丰富的层和流, 并将其形成 swirling cloud 皮带和 vortices。</span><span class="sxs-lookup"><span data-stu-id="f61f4-192">The combination of its fast rotational speed, inner heat exchange, and Coriolis forces creates colorful layers and streams that form into swirling cloud belts and vortices.</span></span> <span data-ttu-id="f61f4-193">捕获这个非常复杂的美式是创建太阳系的关键所在。</span><span class="sxs-lookup"><span data-stu-id="f61f4-193">Capturing this intricate beauty was key in creating our solar system.</span></span>

<span data-ttu-id="f61f4-194">很显然, 使用流畅的技术 (如流体模拟) 和带预计算流的动画纹理就没有问题。</span><span class="sxs-lookup"><span data-stu-id="f61f4-194">It was immediately clear that using visualizing techniques like fluid simulations and animated textures with precomputed streams were out of question.</span></span> <span data-ttu-id="f61f4-195">将此方法与其他任何情况同时进行模拟所需的计算能力会对性能产生重大的不利影响。</span><span class="sxs-lookup"><span data-stu-id="f61f4-195">The computing power required to simulate this in combination with everything else happening simultaneously would have had significant detrimental impacts on performance.</span></span> 

![木星对象概述](images/ge-update-jupiter-shells-complete.jpg)

<span data-ttu-id="f61f4-197">接下来的一种方法是 "冒烟和镜像" 解决方案, 其中包括覆盖透明的纹理层, 每个层都有一个用于处理旋转网格的组合的特定方面。</span><span class="sxs-lookup"><span data-stu-id="f61f4-197">The next approach was a 'smoke-and-mirror' solution, consisting of overlaying transparent texture layers, each of which addressed a specific aspect of the atmospheric movement, compiled on a composition of rotating meshes.</span></span>

<span data-ttu-id="f61f4-198">在下图中, 可以在左侧看到内部外壳。</span><span class="sxs-lookup"><span data-stu-id="f61f4-198">In the image below, you can see the inner shell on the left.</span></span> <span data-ttu-id="f61f4-199">此 matt 层为组合提供了背景, 以防止构成云的多个层之间的任何小间隔。</span><span class="sxs-lookup"><span data-stu-id="f61f4-199">This matt layer provided a background to the composition to guard against any small gaps between the multiple layers that comprised the clouds.</span></span> <span data-ttu-id="f61f4-200">由于层的缓慢旋转, 它还在更快速的移动带之间提供直观的缓冲, 有助于在各个层上构建视觉对象。</span><span class="sxs-lookup"><span data-stu-id="f61f4-200">Due to the layer's slow rotation, it also served as a visual buffer between the faster moving bands to help build visual unity throughout the layers.</span></span>

<span data-ttu-id="f61f4-201">将此定位点设置到模型后, 移动云层随后会投影到下面所示的中间和右侧网格上。</span><span class="sxs-lookup"><span data-stu-id="f61f4-201">After setting this anchor to the model, the moving cloud layers were then projected on the middle and right meshes seen below.</span></span>

![带分隔 shell 的木星对象概述](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a><span data-ttu-id="f61f4-203">绘制</span><span class="sxs-lookup"><span data-stu-id="f61f4-203">Texturing</span></span>

<span data-ttu-id="f61f4-204">现有纹理分为三部分纹理阿特拉斯:第三方托管了 motionless 层, 其中包含间距以提供视差效果, 中间部分包含快速移动的外部流, 第三部分包含慢速旋转内部基底层。</span><span class="sxs-lookup"><span data-stu-id="f61f4-204">The existing texture was separated into a three-part texture atlas: The upper third hosts a motionless layer of clouds with gaps to provide a parallax effect, the middle section contains the fast moving outer streams, and the lower third contains a slowly rotating inner base layer.</span></span>

<span data-ttu-id="f61f4-205">特征很棒的红点还分成了不同的移动部件, 并将其插入到其他不可见的纹理区域中。</span><span class="sxs-lookup"><span data-stu-id="f61f4-205">The characteristic Great Red Spot was also separated into its various moving parts and then inserted into an otherwise invisible area of the texture.</span></span> <span data-ttu-id="f61f4-206">可以在下图的中间部分中将这些组件看作 toned speckles。</span><span class="sxs-lookup"><span data-stu-id="f61f4-206">These components can be seen as the red-toned speckles in the middle section of the image below.</span></span>

<span data-ttu-id="f61f4-207">由于每个带区都有特定的方向和速度, 因此纹理分别应用于每个网格。</span><span class="sxs-lookup"><span data-stu-id="f61f4-207">Because each band has a specific direction and speed, the texture was applied to each mesh individually.</span></span> <span data-ttu-id="f61f4-208">然后, 这些网格具有一个公共中心点和一个透视点, 能够 concentrically 对整个表面进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="f61f4-208">The meshes then had a common center and pivot point, to be able to concentrically animate the whole surface.</span></span>

![木星纹理概述](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a><span data-ttu-id="f61f4-210">旋转和纹理行为</span><span class="sxs-lookup"><span data-stu-id="f61f4-210">Rotation and texture behavior</span></span>

<span data-ttu-id="f61f4-211">现在, 已设置了木星的视觉组合, 接下来需要确保正确计算和应用旋转和轨道速度。</span><span class="sxs-lookup"><span data-stu-id="f61f4-211">Now that the visual composition of Jupiter was set, we needed to ensure that the rotation and orbit speeds were properly calculated and applied accordingly.</span></span> <span data-ttu-id="f61f4-212">木星大约需要9小时才能完成完整的旋转。</span><span class="sxs-lookup"><span data-stu-id="f61f4-212">It takes roughly 9 hours for Jupiter to complete a full rotation.</span></span> <span data-ttu-id="f61f4-213">由于其差异旋转, 这是一个定义。</span><span class="sxs-lookup"><span data-stu-id="f61f4-213">This is a matter of definition due to its Differential Rotation.</span></span> <span data-ttu-id="f61f4-214">因此, 赤道几内亚流已设置为 "主流", 采用3600帧进行完全旋转。</span><span class="sxs-lookup"><span data-stu-id="f61f4-214">Therefore the equatorial stream has been set as a 'master stream', taking 3600 frames for a full rotation.</span></span> <span data-ttu-id="f61f4-215">每个其他层都需要将旋转速度提高为 3600, 以匹配其初始位置, 如600、900、1200、1800等。</span><span class="sxs-lookup"><span data-stu-id="f61f4-215">Every other layer needed to have a rotational speed as a factor of 3600 in order to match its initial position, allowing e.g. 600, 900, 1200, 1800 etc.</span></span>

![木星 shell 纹理](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a><span data-ttu-id="f61f4-217">很棒的红点</span><span class="sxs-lookup"><span data-stu-id="f61f4-217">The Great Red Spot</span></span>

<span data-ttu-id="f61f4-218">单独旋转的流提供了良好的视觉印象, 但当观察到关闭范围时, 会详细说明。</span><span class="sxs-lookup"><span data-stu-id="f61f4-218">The individually rotating streams provided a good visual impression, but lacked in detail when observed at close range.</span></span>

<span data-ttu-id="f61f4-219">最引人注目的部分是木星的好红点, 因此我们创建了一组专门用于展示它的网格和纹理。</span><span class="sxs-lookup"><span data-stu-id="f61f4-219">The most eye-catching part was Jupiter's Great Red Spot, so we created a set of meshes and textures specifically to showcase it.</span></span>
 
<span data-ttu-id="f61f4-220">我们使用了类似于木星带区的一种机制: 一组旋转部分彼此组合在一起, 同时在其 "主要层" 下进行分组, 以确保无论 rest 移动的速度如何, 它们都保持不变。</span><span class="sxs-lookup"><span data-stu-id="f61f4-220">We used a similar mechanism as with Jupiter's bands: a set of rotating parts was composed on top of each other, while also being grouped under its 'master layer' to ensure they remain in position no matter how fast the rest moves.</span></span>

<span data-ttu-id="f61f4-221">当网格设置好后, 应用了激烈 vortex 的不同层, 并且每个光盘随后进行了动画处理, 中心部分的移动速度最快, 并且随着它向外移动时, rest 会逐渐下降。</span><span class="sxs-lookup"><span data-stu-id="f61f4-221">When the meshes were set up and in place, different layers of the stormy vortex were applied and each disc was then animated individually, the center pieces moving fastest, with the rest progressively slowing down as it moving outwards.</span></span>

![木星优秀 Red 点网格](images/ge-update-great-red-spot-mesh.jpg)

<span data-ttu-id="f61f4-223">该组合也具有与每个其他网格相同的透视, 同时还使其倾斜于其原始 y 轴 (!), 以允许自由地对旋转进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="f61f4-223">The composition also had the same pivot as every other mesh, while also keeping its tilt from its original y-axis (!) to allow freedom in animating the rotation.</span></span> <span data-ttu-id="f61f4-224">3600帧是基本速率, 每一层的系数为一段旋转。</span><span class="sxs-lookup"><span data-stu-id="f61f4-224">3600 frames is the base rate, with each layer having a factor of this as a period of rotation.</span></span>

![木星极红点纹理](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a><span data-ttu-id="f61f4-226">直接在 Unity 中获取</span><span class="sxs-lookup"><span data-stu-id="f61f4-226">Getting it right in Unity</span></span>

<span data-ttu-id="f61f4-227">在 Unity 中实现此功能时, 需要记住几个关键事项。</span><span class="sxs-lookup"><span data-stu-id="f61f4-227">There are a couple of key things to keep in mind when implementing this in Unity.</span></span>

<span data-ttu-id="f61f4-228">当处理大型透明层集时, Unity 很容易混淆。</span><span class="sxs-lookup"><span data-stu-id="f61f4-228">Unity is easily confused when dealing with large sets of transparent layers.</span></span> <span data-ttu-id="f61f4-229">解决方法是复制每个网格的纹理材料, 并对每个材料以5为递增的方式应用升序的渲染器队列值。</span><span class="sxs-lookup"><span data-stu-id="f61f4-229">The solution was to duplicate the texture material for each mesh and apply ascending Render Queue values progressively from the inner to the outer by 5 to each material.</span></span>

<span data-ttu-id="f61f4-230">结果是, 内部 shell 的 Render Queue 值为 3000 (默认值), 则后面的静态 toned 外接程序的值为 3005, 而 fast 白色的外部云则为3010。</span><span class="sxs-lookup"><span data-stu-id="f61f4-230">The result was the inner shell had a Render Queue value of 3000 (default), the static red-toned outer later had a value of 3005, the fast white outer clouds had 3010.</span></span> <span data-ttu-id="f61f4-231">很好的红点 (从内部层到外部层) 已在此模型中以3025的值结束。</span><span class="sxs-lookup"><span data-stu-id="f61f4-231">The Great Red Spot (progressing from inner to outer layer), finished with a value of 3025 in this model.</span></span>

![木星最终对象](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a><span data-ttu-id="f61f4-233">最终接触</span><span class="sxs-lookup"><span data-stu-id="f61f4-233">Final touches</span></span>

<span data-ttu-id="f61f4-234">首次设置带纹理的木星层, 证明该层不足以实现实现。</span><span class="sxs-lookup"><span data-stu-id="f61f4-234">The textured Jupiter layers were set up at first, which proved to be insufficient for implementation.</span></span>

<span data-ttu-id="f61f4-235">原来的行星标准着色器 (及其所有变体) 通过脚本 (SunLightReceiver, MRTK 标准着色器不支持) 接收其照明信息。</span><span class="sxs-lookup"><span data-stu-id="f61f4-235">The original Planet Standard shader (and all of its variations) receive their lighting information via a script, the SunLightReceiver, which is not supported by the MRTK Standard shader.</span></span>

<span data-ttu-id="f61f4-236">只需交换着色器并不是一种解决方案, 因为行星标准着色器不支持带有透明胶片的纹理地图。</span><span class="sxs-lookup"><span data-stu-id="f61f4-236">Simply swapping the shaders wasn't a solution because the Planet Standard shader doesn't support texture maps with transparencies.</span></span> <span data-ttu-id="f61f4-237">编辑此着色器是为了使木星构建工作按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="f61f4-237">We edited this shader in order to make the Jupiter build work as intended.</span></span>

<span data-ttu-id="f61f4-238">最后, 需要设置 Alpha 混合, 方法是将源 Blend 设置为 10, 将目标混合设置为5。</span><span class="sxs-lookup"><span data-stu-id="f61f4-238">Finally the Alpha Blends needed to be set up by setting the Source Blend to 10 as well as the Destination Blend to 5.</span></span>

![木星 Unity 属性](images/ge-update-jupiter-unity-render-queue.jpg)

<span data-ttu-id="f61f4-240">可以在 Galaxy 资源管理器中查看木星的最终呈现!</span><span class="sxs-lookup"><span data-stu-id="f61f4-240">You can see the final rendering of Jupiter in Galaxy Explorer!</span></span>

## <a name="meet-the-team"></a><span data-ttu-id="f61f4-241">会见团队</span><span class="sxs-lookup"><span data-stu-id="f61f4-241">Meet the team</span></span> 

<span data-ttu-id="f61f4-242">混合现实工作室团队由设计人员、三维音乐家、UX 专家、开发人员、项目经理和工作室主管组成。</span><span class="sxs-lookup"><span data-stu-id="f61f4-242">Our Mixed Reality studio team is made up of designers, 3D artists, UX specialists, developers, a program manager and a studio head.</span></span> <span data-ttu-id="f61f4-243">从世界各地 hail:比利时、加拿大、德国、以色列、日本、英国和美国。</span><span class="sxs-lookup"><span data-stu-id="f61f4-243">We hail from all over the world: Belgium, Canada, Germany, Israel, Japan, the United Kingdom and the United States.</span></span> <span data-ttu-id="f61f4-244">我们是一位丰富的团队, 来自于不同的背景: 游戏-传统和独立、数字营销、卫生保健和科学。</span><span class="sxs-lookup"><span data-stu-id="f61f4-244">We are a multidisciplinary team that comes from a diverse background: gaming - both traditional and indie, digital marketing, health care and science.</span></span>

<span data-ttu-id="f61f4-245">我们很高兴为 HoloLens 2 创建 Galaxy 资源管理器, 并更新 HoloLens (第一代)、VR 和桌面版本。</span><span class="sxs-lookup"><span data-stu-id="f61f4-245">We are excited to create Galaxy Explorer for HoloLens 2, and to update the HoloLens (1st gen), VR and desktop versions.</span></span> 

![Galaxy 资源管理器团队](images/ge-update-team-image.png)

<span data-ttu-id="f61f4-247">从左到右:Artemis Tsouflidou (开发人员)、Angie Teickner (可视化设计器)、David Janer (UX 设计器)、刘娜 Garrett (交付 & 生产主管)、Yasushi Zonno (创造性领导)、Eline Ledent (开发人员) 和 Ben Turner (Sr-iov)。</span><span class="sxs-lookup"><span data-stu-id="f61f4-247">On top from left to right: Artemis Tsouflidou (Developer), Angie Teickner (Visual Designer), David Janer (UX Designer), Laura Garrett (Delivery & Production Lead), Yasushi Zonno (Creative Lead), Eline Ledent (Developer) and Ben Turner (Sr. Developer).</span></span>
<span data-ttu-id="f61f4-248">从左到右的底部:Amit Rojtblat (技术艺术家)、圣马丁 Wettig (3D 艺术家) 和 Dirk Songuer (Studio Head)。</span><span class="sxs-lookup"><span data-stu-id="f61f4-248">Bottom from left to right: Amit Rojtblat (Technical Artist), Martin Wettig (3D Artist) and Dirk Songuer (Studio Head).</span></span>
<span data-ttu-id="f61f4-249">不重要:Tim Gerken (技术组长) 和 Oscar Salandin (可视化设计器)。</span><span class="sxs-lookup"><span data-stu-id="f61f4-249">Not featured: Tim Gerken (Tech Lead) and Oscar Salandin (Visual Designer).</span></span>

## <a name="additional-information"></a><span data-ttu-id="f61f4-250">其他信息</span><span class="sxs-lookup"><span data-stu-id="f61f4-250">Additional information</span></span>

### <a name="mixed-reality-studios"></a><span data-ttu-id="f61f4-251">混合现实工作室</span><span class="sxs-lookup"><span data-stu-id="f61f4-251">Mixed Reality Studios</span></span>

<span data-ttu-id="f61f4-252">Microsoft 混合现实工作室团队-位于美洲、欧洲和亚太地区, 是用户体验设计、全息计算、AR/VR 技术和三维开发方面的专家;包括3D 资产创建、DirectX、Unity 和 Unreal。</span><span class="sxs-lookup"><span data-stu-id="f61f4-252">Microsoft Mixed Reality Studio teams - located in the Americas, Europe and Asia-Pacific - are experts in user experience design, holographic computing, AR/VR technologies, and 3D development; including 3D asset creation, DirectX, Unity and Unreal.</span></span> <span data-ttu-id="f61f4-253">我们帮助构想预期的先期备货、设计、构建和交付解决方案, 同时使客户能够在其组织中创造实实在在的影响。</span><span class="sxs-lookup"><span data-stu-id="f61f4-253">We help envision desired futures, design, build and deliver solutions, while enabling customers to create measurable impact across their organization.</span></span> <span data-ttu-id="f61f4-254">录音室与超过22000个 Microsoft 服务专业人员密切合作, 以实现企业应用程序集成、采用、操作和支持。</span><span class="sxs-lookup"><span data-stu-id="f61f4-254">The studios work closely with over 22,000 Microsoft Services professionals for enterprise application integration, adoption, operations and support.</span></span>
