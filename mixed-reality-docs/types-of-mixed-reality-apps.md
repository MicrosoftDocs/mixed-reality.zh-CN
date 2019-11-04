---
title: 混合现实应用的类型
description: 开发 Windows Mixed Reality 应用的优势之一在于，平台可以从完全沉浸的虚拟环境中支持的一系列经验，通过用户的当前 environmentl 进行分层分层。
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，应用模式
ms.openlocfilehash: 62a0b76ba7853262a46b34466a6d3b0567bc137d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438251"
---
# <a name="types-of-mixed-reality-apps"></a><span data-ttu-id="c9bdb-104">混合现实应用的类型</span><span class="sxs-lookup"><span data-stu-id="c9bdb-104">Types of mixed reality apps</span></span>

<span data-ttu-id="c9bdb-105">为 Windows Mixed Reality 开发应用程序的一个优点是，该平台可以支持多种体验。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-105">One of the advantages of developing apps for Windows Mixed Reality is that there is a spectrum of experiences that the platform can support.</span></span> <span data-ttu-id="c9bdb-106">从完全沉浸式的虚拟环境到用户当前环境中的光线信息分层，Windows Mixed Reality 提供了一组强大的工具，可将任何体验引入到生活中。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-106">From fully immersive, virtual environments, to light information layering over a user’s current environment, Windows Mixed Reality provides a robust set of tools to bring any experience to life.</span></span> <span data-ttu-id="c9bdb-107">对于应用程序制造商来说，在开发过程的早期了解其体验的位置，这一点非常重要。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-107">It is important for an app maker to understand early in their development process as to where along this spectrum their experience lies.</span></span> <span data-ttu-id="c9bdb-108">此决定最终会影响应用设计的构成和开发的技术路径。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-108">This decision will ultimately impact both the app design makeup and the technological path for development.</span></span>

## <a name="enhanced-environment-apps-hololens-only"></a><span data-ttu-id="c9bdb-109">增强的环境应用（仅限 HoloLens）</span><span class="sxs-lookup"><span data-stu-id="c9bdb-109">Enhanced environment apps (HoloLens only)</span></span>

<span data-ttu-id="c9bdb-110">混合现实可为用户带来价值的最强大的方式之一是，方便在用户的当前环境中放置数字信息或内容。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-110">One of the most powerful ways that mixed reality can bring value to users is by facilitating the placement of digital information or content in a user’s current environment.</span></span> <span data-ttu-id="c9bdb-111">这是一个增强的环境应用。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-111">This is an enhanced environment app.</span></span> <span data-ttu-id="c9bdb-112">此方法对于以下情况很常见：真实环境中数字内容的上下文放置非常重要，并且/或在其体验过程中使用户的实际环境 "存在" 成为关键。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-112">This approach is popular for apps where the contextual placement of digital content in the real world is paramount and/or keeping the user’s real world environment “present” during their experience is key.</span></span> <span data-ttu-id="c9bdb-113">这种方法还可让用户轻松地从实际任务移动到数字任务并轻松地进行操作，借此获得更多的信任，以保证用户看到的混合现实应用真正成为其环境的一部分。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-113">This approach also allows users to easily move from real world tasks to digital tasks and back easily, lending even more credence to promise that the mixed reality apps the user sees are truly a part of their environment.</span></span>

<span data-ttu-id="c9bdb-114">![增强的环境应用](images/enhancedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c9bdb-114">![Enhanced environment apps](images/enhancedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="c9bdb-115">*增强的环境应用*</span><span class="sxs-lookup"><span data-stu-id="c9bdb-115">*Enhanced environment apps*</span></span>

<span data-ttu-id="c9bdb-116">**示例使用**</span><span class="sxs-lookup"><span data-stu-id="c9bdb-116">**Example uses**</span></span>
* <span data-ttu-id="c9bdb-117">混合现实记事本样式应用，允许用户创建笔记并将其放置在其环境中</span><span class="sxs-lookup"><span data-stu-id="c9bdb-117">A mixed reality notepad style app that allows users to create and place notes around their environment</span></span>
* <span data-ttu-id="c9bdb-118">将混合现实电视应用置于舒适的位置以供观看</span><span class="sxs-lookup"><span data-stu-id="c9bdb-118">A mixed reality television app placed in a comfortable spot for viewing</span></span>
* <span data-ttu-id="c9bdb-119">放置在厨房岛之上的混合现实烹饪应用，可帮助你进行烹饪任务</span><span class="sxs-lookup"><span data-stu-id="c9bdb-119">A mixed reality cooking app placed above the kitchen island to assist in a cooking task</span></span>
* <span data-ttu-id="c9bdb-120">一种混合现实应用，为用户提供 "x 光线愿景" （即，放置在上并模拟真实世界对象，同时使用户能够看到 "holographically" 的全息图）</span><span class="sxs-lookup"><span data-stu-id="c9bdb-120">A mixed reality app that gives users the feeling of “x-ray vision” (i.e. a hologram placed on top of and mimics a real world object, while allowing the user to see “inside it” holographically)</span></span>
* <span data-ttu-id="c9bdb-121">混合现实批注放置在工厂中，用于为辅助角色指定必要的信息</span><span class="sxs-lookup"><span data-stu-id="c9bdb-121">Mixed reality annotations placed throughout a factory to give worker’s necessary information</span></span>
* <span data-ttu-id="c9bdb-122">办公空间中混合现实 wayfinding</span><span class="sxs-lookup"><span data-stu-id="c9bdb-122">Mixed reality wayfinding in an office space</span></span>
* <span data-ttu-id="c9bdb-123">混合现实 tabletop 体验（即，棋盘游戏样式体验）</span><span class="sxs-lookup"><span data-stu-id="c9bdb-123">Mixed reality tabletop experiences (i.e. board game style experiences)</span></span>
* <span data-ttu-id="c9bdb-124">混合现实通信应用，如 Skype</span><span class="sxs-lookup"><span data-stu-id="c9bdb-124">Mixed reality communication apps like Skype</span></span>

## <a name="blended-environment-apps"></a><span data-ttu-id="c9bdb-125">混合环境应用</span><span class="sxs-lookup"><span data-stu-id="c9bdb-125">Blended environment apps</span></span>

<span data-ttu-id="c9bdb-126">由于 Windows Mixed Reality 能够识别和映射用户的环境，因此它能够创建可完全叠加在用户空间上的数字层。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-126">Given Windows Mixed Reality’s ability to recognize and map the user's environment, it is capable of creating a digital layer that can be completely overlaid on the user’s space.</span></span> <span data-ttu-id="c9bdb-127">精简层会考虑用户环境的形状和边界，但是应用程序可能会选择转换最适合从而深入了解应用程序中用户的某些元素。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-127">Thin layer respects the shape and boundaries of the user’s environment, but the app may choose to transform certain elements best suited to immerse the user in the app.</span></span> <span data-ttu-id="c9bdb-128">这称为混合环境应用。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-128">This is called a blended environment app.</span></span> <span data-ttu-id="c9bdb-129">与增强的环境应用不同，混合环境应用程序可能只关心环境，以最好地使用其构成来鼓励特定用户的行为（例如，鼓励移动或探索）或通过将元素替换为更改（厨房计数器几乎 skinned 显示不同的平铺模式）。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-129">Unlike an enhanced environment app, blended environment apps may only care enough about the environment to best use its makeup for encouraging specific user behavior (like encouraging movement or exploration) or by replacing elements with changes (a kitchen counter is virtually skinned to show a different tile pattern).</span></span> <span data-ttu-id="c9bdb-130">这种类型的体验甚至可能会将元素转换为完全不同的对象，但仍会保留对象的大致尺寸作为其基础（厨房岛会转换为犯罪 thriller 游戏的转储程序）。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-130">This type of experience may even transform an element into an entirely different object, but still retain the rough dimensions of the object as its base (a kitchen island is transformed into a dumpster for a crime thriller game).</span></span>

<span data-ttu-id="c9bdb-131">![混合环境应用](images/blendedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c9bdb-131">![Blended environment apps](images/blendedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="c9bdb-132">*混合环境应用*</span><span class="sxs-lookup"><span data-stu-id="c9bdb-132">*Blended environment apps*</span></span>

<span data-ttu-id="c9bdb-133">**示例使用**</span><span class="sxs-lookup"><span data-stu-id="c9bdb-133">**Example uses**</span></span>
* <span data-ttu-id="c9bdb-134">混合现实内部设计应用，可使用不同的颜色和模式绘制墙壁、countertops 或地面</span><span class="sxs-lookup"><span data-stu-id="c9bdb-134">A mixed reality interior design app that can paint walls, countertops or floors in different colors and patterns</span></span>
* <span data-ttu-id="c9bdb-135">一种混合现实应用，允许汽车设计器将新的设计迭代置于现有汽车顶层的即将到来的汽车刷新之上</span><span class="sxs-lookup"><span data-stu-id="c9bdb-135">A mixed reality app that allows an automotive designer to layer new design iterations for an upcoming car refresh on top of an existing car</span></span>
* <span data-ttu-id="c9bdb-136">床已 "覆盖"，由儿童游戏中的混合现实水果支架替换</span><span class="sxs-lookup"><span data-stu-id="c9bdb-136">A bed is “covered” and replaced by a mixed reality fruit stand in children’s game</span></span>
* <span data-ttu-id="c9bdb-137">在犯罪 thriller 游戏中，桌面被 "覆盖" 并替换为混合现实转储程序</span><span class="sxs-lookup"><span data-stu-id="c9bdb-137">A desk is “covered” and replaced with a mixed reality dumpster in a crime thriller game</span></span>
* <span data-ttu-id="c9bdb-138">使用大致相同的形状和尺寸 "覆盖" 了悬挂灯笼并将其替换为 signpost</span><span class="sxs-lookup"><span data-stu-id="c9bdb-138">A hanging lantern is “covered” and replaced with signpost using roughly the same shape and dimension</span></span>
* <span data-ttu-id="c9bdb-139">一种应用，它允许用户在其真实或沉浸式世界中冲击孔洞，这会显示神奇世界</span><span class="sxs-lookup"><span data-stu-id="c9bdb-139">An app that allows users to blast holes in their real or immersive world walls, which reveal a magical world</span></span>

## <a name="immersive-environment-apps"></a><span data-ttu-id="c9bdb-140">沉浸式环境应用</span><span class="sxs-lookup"><span data-stu-id="c9bdb-140">Immersive environment apps</span></span>

<span data-ttu-id="c9bdb-141">沉浸式环境应用以完全更改用户世界的环境为中心，并可将其置于不同的时间和空间。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-141">Immersive environment apps are centered around an environment that completely changes the user’s world and can place them in a different time and space.</span></span> <span data-ttu-id="c9bdb-142">这些环境看起来非常真实，只是在应用程序创建者的想象中仅限制了 thrilling 体验。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-142">These environments can feel very real, creating immersive and thrilling experiences that are only limited by the app creator’s imagination.</span></span> <span data-ttu-id="c9bdb-143">与混合环境应用不同，一旦 Windows Mixed Reality 标识用户的空间，沉浸式环境应用可能会完全忽略用户的当前环境，并将其替换为自己的整个股票。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-143">Unlike blended environment apps, once Windows Mixed Reality identifies the user’s space, an immersive environment app may totally disregard the user’s current environment and replace it whole stock with one of its own.</span></span> <span data-ttu-id="c9bdb-144">这些体验还可能会完全分离时间和空间，这意味着用户可以通过沉浸式体验来浏览罗马的</span><span class="sxs-lookup"><span data-stu-id="c9bdb-144">These experiences may also completely separate time and space, meaning a user could walk the streets of Rome in an immersive experience, while remaining relatively still in their real world space.</span></span> <span data-ttu-id="c9bdb-145">实际环境的上下文对于沉浸式环境应用可能并不重要。</span><span class="sxs-lookup"><span data-stu-id="c9bdb-145">Context of the real world environment may not be important to an immersive environment app.</span></span>

<span data-ttu-id="c9bdb-146">![沉浸式环境应用](images/windows-mixed-reality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c9bdb-146">![Immersive environment apps](images/windows-mixed-reality-640px.jpg)</span></span><br>
<span data-ttu-id="c9bdb-147">*沉浸式环境应用*</span><span class="sxs-lookup"><span data-stu-id="c9bdb-147">*Immersive environment apps*</span></span>

<span data-ttu-id="c9bdb-148">**示例使用**</span><span class="sxs-lookup"><span data-stu-id="c9bdb-148">**Example uses**</span></span>
* <span data-ttu-id="c9bdb-149">允许用户浏览完全独立于其自己的空间的沉浸式应用程序（即，演练著名的建筑物、博物馆、受欢迎的城市）</span><span class="sxs-lookup"><span data-stu-id="c9bdb-149">An immersive app that lets a user tour a space completely separate from their own (i.e. walk through a famous building, museum, popular city)</span></span>
* <span data-ttu-id="c9bdb-150">协调用户的事件或方案（即一种工作或性能）的沉浸式应用程序</span><span class="sxs-lookup"><span data-stu-id="c9bdb-150">An immersive app that orchestrates an event or scenario around the user (i.e. a battle or a performance)</span></span>

## <a name="see-also"></a><span data-ttu-id="c9bdb-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9bdb-151">See also</span></span>
* [<span data-ttu-id="c9bdb-152">开发概述</span><span class="sxs-lookup"><span data-stu-id="c9bdb-152">Development overview</span></span>](development.md)
* [<span data-ttu-id="c9bdb-153">应用模型</span><span class="sxs-lookup"><span data-stu-id="c9bdb-153">App model</span></span>](app-model.md)
* [<span data-ttu-id="c9bdb-154">应用视图</span><span class="sxs-lookup"><span data-stu-id="c9bdb-154">App views</span></span>](app-views.md)
