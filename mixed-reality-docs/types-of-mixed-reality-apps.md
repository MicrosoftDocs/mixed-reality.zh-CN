---
title: 类型的混合的现实应用
description: 开发 Windows Mixed Reality 应用的优势之一是，没有一系列平台可以支持完全沉浸式虚拟环境中，到通过用户的当前 environmentl 浅信息分层的体验。
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 应用程序模式
ms.openlocfilehash: 97f8039dcd9bbf8ee3d6c7be926db16b60a76b97
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590335"
---
# <a name="types-of-mixed-reality-apps"></a><span data-ttu-id="57bbb-104">类型的混合的现实应用</span><span class="sxs-lookup"><span data-stu-id="57bbb-104">Types of mixed reality apps</span></span>

<span data-ttu-id="57bbb-105">开发 Windows Mixed Reality 应用的优势之一是，没有一系列平台可以支持的体验。</span><span class="sxs-lookup"><span data-stu-id="57bbb-105">One of the advantages of developing apps for Windows Mixed Reality is that there is a spectrum of experiences that the platform can support.</span></span> <span data-ttu-id="57bbb-106">从完全沉浸式虚拟环境中，通过用户的当前环境中，分层的轻型信息 Windows Mixed Reality 提供了一系列可靠的工具将转换为现实的任何经验。</span><span class="sxs-lookup"><span data-stu-id="57bbb-106">From fully immersive, virtual environments, to light information layering over a user’s current environment, Windows Mixed Reality provides a robust set of tools to bring any experience to life.</span></span> <span data-ttu-id="57bbb-107">非常重要的应用开发者若要了解有关其中沿此系列他们的体验位于其开发过程中尽早。</span><span class="sxs-lookup"><span data-stu-id="57bbb-107">It is important for an app maker to understand early in their development process as to where along this spectrum their experience lies.</span></span> <span data-ttu-id="57bbb-108">这一决定最终会影响应用程序设计结构和开发的技术路径。</span><span class="sxs-lookup"><span data-stu-id="57bbb-108">This decision will ultimately impact both the app design makeup and the technological path for development.</span></span>

## <a name="enhanced-environment-apps-hololens-only"></a><span data-ttu-id="57bbb-109">增强型的环境应用 (仅 HoloLens)</span><span class="sxs-lookup"><span data-stu-id="57bbb-109">Enhanced environment apps (HoloLens only)</span></span>

<span data-ttu-id="57bbb-110">混合的现实可以为用户带来价值的功能最强大方式之一是通过促进数字信息或用户的当前环境中的内容的位置。</span><span class="sxs-lookup"><span data-stu-id="57bbb-110">One of the most powerful ways that mixed reality can bring value to users is by facilitating the placement of digital information or content in a user’s current environment.</span></span> <span data-ttu-id="57bbb-111">这是增强型的环境应用。</span><span class="sxs-lookup"><span data-stu-id="57bbb-111">This is an enhanced environment app.</span></span> <span data-ttu-id="57bbb-112">这种方法是常用于其中的现实世界中的数字内容的上下文位置是极其重要和/或保留用户的现实世界环境"present"在他们的经验是关键的应用。</span><span class="sxs-lookup"><span data-stu-id="57bbb-112">This approach is popular for apps where the contextual placement of digital content in the real world is paramount and/or keeping the user’s real world environment “present” during their experience is key.</span></span> <span data-ttu-id="57bbb-113">此方法还允许用户轻松地将从真实世界的任务移到数字任务又重新轻松，借出更多的信任，以保证，则用户将看到其环境的一部分是真正的混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="57bbb-113">This approach also allows users to easily move from real world tasks to digital tasks and back easily, lending even more credence to promise that the mixed reality apps the user sees are truly a part of their environment.</span></span>

<span data-ttu-id="57bbb-114">![增强的环境的应用](images/enhancedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="57bbb-114">![Enhanced environment apps](images/enhancedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="57bbb-115">*增强的环境的应用*</span><span class="sxs-lookup"><span data-stu-id="57bbb-115">*Enhanced environment apps*</span></span>

<span data-ttu-id="57bbb-116">**示例使用**</span><span class="sxs-lookup"><span data-stu-id="57bbb-116">**Example uses**</span></span>
* <span data-ttu-id="57bbb-117">混合的现实记事本风格的应用程序，允许用户创建，并将围绕其环境的说明</span><span class="sxs-lookup"><span data-stu-id="57bbb-117">A mixed reality notepad style app that allows users to create and place notes around their environment</span></span>
* <span data-ttu-id="57bbb-118">混合的现实电视应用程序放置在合适的位置进行查看</span><span class="sxs-lookup"><span data-stu-id="57bbb-118">A mixed reality television app placed in a comfortable spot for viewing</span></span>
* <span data-ttu-id="57bbb-119">混合的现实烹饪应用放在厨房岛，以帮助在烹饪与任务</span><span class="sxs-lookup"><span data-stu-id="57bbb-119">A mixed reality cooking app placed above the kitchen island to assist in a cooking task</span></span>
* <span data-ttu-id="57bbb-120">为用户提供的"x 射线视力"感觉的混合的现实应用 （即一张全息图的顶部放置和模拟的实际对象，同时允许用户全方位查看"内部）</span><span class="sxs-lookup"><span data-stu-id="57bbb-120">A mixed reality app that gives users the feeling of “x-ray vision” (i.e. a hologram placed on top of and mimics a real world object, while allowing the user to see “inside it” holographically)</span></span>
* <span data-ttu-id="57bbb-121">混合的现实批注放在一个工厂来为工作人员的必要的信息</span><span class="sxs-lookup"><span data-stu-id="57bbb-121">Mixed reality annotations placed throughout a factory to give worker’s necessary information</span></span>
* <span data-ttu-id="57bbb-122">Office 空间中的混合的现实 wayfinding</span><span class="sxs-lookup"><span data-stu-id="57bbb-122">Mixed reality wayfinding in an office space</span></span>
* <span data-ttu-id="57bbb-123">混合的现实和体验 （即棋盘类游戏样式体验）</span><span class="sxs-lookup"><span data-stu-id="57bbb-123">Mixed reality tabletop experiences (i.e. board game style experiences)</span></span>
* <span data-ttu-id="57bbb-124">混合的现实通信应用，如 Skype</span><span class="sxs-lookup"><span data-stu-id="57bbb-124">Mixed reality communication apps like Skype</span></span>

## <a name="blended-environment-apps"></a><span data-ttu-id="57bbb-125">混合的环境的应用</span><span class="sxs-lookup"><span data-stu-id="57bbb-125">Blended environment apps</span></span>

<span data-ttu-id="57bbb-126">提供 Windows Mixed Reality 能力识别和映射用户的环境，它是能够创建一个数字的层，可以完全叠加在用户的空间。</span><span class="sxs-lookup"><span data-stu-id="57bbb-126">Given Windows Mixed Reality’s ability to recognize and map the user's environment, it is capable of creating a digital layer that can be completely overlaid on the user’s space.</span></span> <span data-ttu-id="57bbb-127">将薄层遵循的形状和边界的用户的环境中，但该应用程序可以选择转换它最适合需要可访问这个应用程序中的用户的某些元素。</span><span class="sxs-lookup"><span data-stu-id="57bbb-127">Thin layer respects the shape and boundaries of the user’s environment, but the app may choose to transform certain elements best suited to immerse the user in the app.</span></span> <span data-ttu-id="57bbb-128">这被称为混合的环境应用。</span><span class="sxs-lookup"><span data-stu-id="57bbb-128">This is called a blended environment app.</span></span> <span data-ttu-id="57bbb-129">与增强型的环境应用不同混合的环境的应用可能只关心足够环境以使用其构成为鼓舞人心的特定用户行为 （如鼓舞人心移动或探索） 或通过将更改 （一个厨房中替换元素计数器是几乎带有外观以显示不同的平铺模式）。</span><span class="sxs-lookup"><span data-stu-id="57bbb-129">Unlike an enhanced environment app, blended environment apps may only care enough about the environment to best use its makeup for encouraging specific user behavior (like encouraging movement or exploration) or by replacing elements with changes (a kitchen counter is virtually skinned to show a different tile pattern).</span></span> <span data-ttu-id="57bbb-130">这种类型的体验可能甚至将元素转换为一个完全不同的对象，但仍保留作为其基类的对象的大致尺寸 (厨房岛转换为转储程序犯罪打发游戏)。</span><span class="sxs-lookup"><span data-stu-id="57bbb-130">This type of experience may even transform an element into an entirely different object, but still retain the rough dimensions of the object as its base (a kitchen island is transformed into a dumpster for a crime thriller game).</span></span>

<span data-ttu-id="57bbb-131">![混合的环境的应用](images/blendedenvironmentapps-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="57bbb-131">![Blended environment apps](images/blendedenvironmentapps-640px.jpg)</span></span><br>
<span data-ttu-id="57bbb-132">*混合的环境的应用*</span><span class="sxs-lookup"><span data-stu-id="57bbb-132">*Blended environment apps*</span></span>

<span data-ttu-id="57bbb-133">**示例使用**</span><span class="sxs-lookup"><span data-stu-id="57bbb-133">**Example uses**</span></span>
* <span data-ttu-id="57bbb-134">可以绘制墙、 countertops 或不同的颜色和模式中的楼层 mixed 的 reality 内部设计应用</span><span class="sxs-lookup"><span data-stu-id="57bbb-134">A mixed reality interior design app that can paint walls, countertops or floors in different colors and patterns</span></span>
* <span data-ttu-id="57bbb-135">一个混合的现实应用，它允许到层对于即将发布的汽车刷新现有汽车之上的新设计迭代的汽车设计器</span><span class="sxs-lookup"><span data-stu-id="57bbb-135">A mixed reality app that allows an automotive designer to layer new design iterations for an upcoming car refresh on top of an existing car</span></span>
* <span data-ttu-id="57bbb-136">"已覆盖"和混合的现实水果独立儿童游戏中替换为平台</span><span class="sxs-lookup"><span data-stu-id="57bbb-136">A bed is “covered” and replaced by a mixed reality fruit stand in children’s game</span></span>
* <span data-ttu-id="57bbb-137">"已覆盖"在办公桌前并且将其替换为混合现实转储程序中的犯罪打发游戏</span><span class="sxs-lookup"><span data-stu-id="57bbb-137">A desk is “covered” and replaced with a mixed reality dumpster in a crime thriller game</span></span>
* <span data-ttu-id="57bbb-138">"已覆盖"并替换为使用大致相同的形状和维度的路标悬挂灯笼</span><span class="sxs-lookup"><span data-stu-id="57bbb-138">A hanging lantern is “covered” and replaced with signpost using roughly the same shape and dimension</span></span>
* <span data-ttu-id="57bbb-139">允许用户使用其真实或沉浸式世界墙，显示一个奇妙世界中的冲击漏洞的应用</span><span class="sxs-lookup"><span data-stu-id="57bbb-139">An app that allows users to blast holes in their real or immersive world walls, which reveal a magical world</span></span>

## <a name="immersive-environment-apps"></a><span data-ttu-id="57bbb-140">沉浸式环境应用</span><span class="sxs-lookup"><span data-stu-id="57bbb-140">Immersive environment apps</span></span>

<span data-ttu-id="57bbb-141">沉浸式环境应用程序以完全改变用户的世界的环境为中心，并可以将它们放在不同的时间和空间。</span><span class="sxs-lookup"><span data-stu-id="57bbb-141">Immersive environment apps are centered around an environment that completely changes the user’s world and can place them in a different time and space.</span></span> <span data-ttu-id="57bbb-142">这些环境可以感觉非常实际，创建仅受到应用创建者的想象力的沉浸式和令人振奋的体验。</span><span class="sxs-lookup"><span data-stu-id="57bbb-142">These environments can feel very real, creating immersive and thrilling experiences that are only limited by the app creator’s imagination.</span></span> <span data-ttu-id="57bbb-143">与混合的环境应用不同后 Windows Mixed Reality 标识用户的空间沉浸式环境应用可能会完全忽略用户的当前环境并将其替换自己的其中一个为整个 stock。</span><span class="sxs-lookup"><span data-stu-id="57bbb-143">Unlike blended environment apps, once Windows Mixed Reality identifies the user’s space, an immersive environment app may totally disregard the user’s current environment and replace it whole stock with one of its own.</span></span> <span data-ttu-id="57bbb-144">这些体验可能也完全不同的时间和空间，这意味着用户可以遍历的罗马的沉浸式体验，同时保持相对较高仍在其现实世界空间中的街道。</span><span class="sxs-lookup"><span data-stu-id="57bbb-144">These experiences may also completely separate time and space, meaning a user could walk the streets of Rome in an immersive experience, while remaining relatively still in their real world space.</span></span> <span data-ttu-id="57bbb-145">可能不是重要的沉浸式环境应用到实际环境的上下文。</span><span class="sxs-lookup"><span data-stu-id="57bbb-145">Context of the real world environment may not be important to an immersive environment app.</span></span>

<span data-ttu-id="57bbb-146">![沉浸式环境应用](images/windows-mixed-reality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="57bbb-146">![Immersive environment apps](images/windows-mixed-reality-640px.jpg)</span></span><br>
<span data-ttu-id="57bbb-147">*沉浸式环境应用*</span><span class="sxs-lookup"><span data-stu-id="57bbb-147">*Immersive environment apps*</span></span>

<span data-ttu-id="57bbb-148">**示例使用**</span><span class="sxs-lookup"><span data-stu-id="57bbb-148">**Example uses**</span></span>
* <span data-ttu-id="57bbb-149">可使用户在浏览空间完全独立于其自己的沉浸式应用 （即遍历著名的构建、 博物馆、 热门城市）</span><span class="sxs-lookup"><span data-stu-id="57bbb-149">An immersive app that lets a user tour a space completely separate from their own (i.e. walk through a famous building, museum, popular city)</span></span>
* <span data-ttu-id="57bbb-150">沉浸式应用，用于协调事件或有关用户 （即的多次实战或性能） 情况</span><span class="sxs-lookup"><span data-stu-id="57bbb-150">An immersive app that orchestrates an event or scenario around the user (i.e. a battle or a performance)</span></span>

## <a name="see-also"></a><span data-ttu-id="57bbb-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="57bbb-151">See also</span></span>
* [<span data-ttu-id="57bbb-152">开发概述</span><span class="sxs-lookup"><span data-stu-id="57bbb-152">Development overview</span></span>](development-overview.md)
* [<span data-ttu-id="57bbb-153">应用程序模型</span><span class="sxs-lookup"><span data-stu-id="57bbb-153">App model</span></span>](app-model.md)
* [<span data-ttu-id="57bbb-154">应用程序视图</span><span class="sxs-lookup"><span data-stu-id="57bbb-154">App views</span></span>](app-views.md)
