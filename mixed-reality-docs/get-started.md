---
title: 立即开始行动
description: 本指南概述了开始和运行混合现实开发的最快方法。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 入门, 基础知识, HoloLens, 沉浸式耳机, ar, vr, unity, visual studio, 快速入门, 如何
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873962"
---
# <a name="get-started"></a><span data-ttu-id="78391-104">立即开始行动</span><span class="sxs-lookup"><span data-stu-id="78391-104">Get started</span></span>

<span data-ttu-id="78391-105">欢迎使用混合现实发展世界!</span><span class="sxs-lookup"><span data-stu-id="78391-105">Welcome to the world of mixed reality development!</span></span> <span data-ttu-id="78391-106">如果你不熟悉 MR, 本指南将使你的中心尽快启动并运行。</span><span class="sxs-lookup"><span data-stu-id="78391-106">If you're new to MR, this guide will be your hub to get up and running as quickly as possible.</span></span> <span data-ttu-id="78391-107">我们将帮助你将电脑设置为进行开发, 使你的设备准备就绪, 并安装可加快 MR 开发过程的工具。</span><span class="sxs-lookup"><span data-stu-id="78391-107">We'll help you get your PC set up for development, get your device(s) ready, and install tools that will speed up the MR development process.</span></span> 

## <a name="intro-to-mixed-reality"></a><span data-ttu-id="78391-108">混合现实简介</span><span class="sxs-lookup"><span data-stu-id="78391-108">Intro to mixed reality</span></span>

<span data-ttu-id="78391-109">你可能会遇到 "mixed reality" 的一些问题, 以及它是如何与扩充现实 (AR) 和虚拟现实 (VR) 相关的。</span><span class="sxs-lookup"><span data-stu-id="78391-109">You may have some questions about what we mean by "mixed reality" and how it relates to augmented reality (AR) and virtual reality (VR).</span></span> <span data-ttu-id="78391-110">简而言之, 混合现实是将物理世界与数字世界混合起来, 因此, 这是一项广泛的功能, 其中包括所有内容, 从增加的现实到现实世界, 到虚拟现实 (真实世界几乎完全一样)由数字替换。</span><span class="sxs-lookup"><span data-stu-id="78391-110">In short, mixed reality is the blending of the physical world with the digital world, so it's a spectrum that covers everything from augmented reality, where digital content is placed in the real world, to virtual reality, where your real world is almost entirely replaced by the digital.</span></span> 

<span data-ttu-id="78391-111">![支持 HoloLens 和沉浸式 (VR) 耳机的混合现实应用的示例](images/mr-island.png)</span><span class="sxs-lookup"><span data-stu-id="78391-111">![Example of a mixed reality app that supports both HoloLens and immersive (VR) headsets](images/mr-island.png)</span></span><br>
<span data-ttu-id="78391-112">*混合现实应用可支持 HoloLens 和沉浸式 (VR) 耳机*</span><span class="sxs-lookup"><span data-stu-id="78391-112">*Mixed reality apps can support both HoloLens and immersive (VR) headsets*</span></span>

<span data-ttu-id="78391-113">我们将 Windows Mixed Reality 创建为单一开发平台和一组可涵盖 MR 系列的工具, 并且我们目前支持两种涵盖相同色谱的设备类型:[Microsoft HoloLens](https://www.microsoft.com/hololens), 世界上第一个独立的全息耳机, [Windows Mixed Reality 沉浸式耳机和运动控制器](https://www.microsoft.com/windows/windows-mixed-reality), 它们连接到 PC 以获得强大的虚拟现实体验。</span><span class="sxs-lookup"><span data-stu-id="78391-113">We created Windows Mixed Reality as a single development platform and set of tools that can cover the MR spectrum, and we currently support two device types that cover the same spectrum: [Microsoft HoloLens](https://www.microsoft.com/hololens), the world's first self-contained holographic headset, and [Windows Mixed Reality immersive headsets and motion controllers](https://www.microsoft.com/windows/windows-mixed-reality), which connect to a PC for powerful virtual reality experiences.</span></span> <span data-ttu-id="78391-114">您可以查看 "混合现实" 是什么？(如果感兴趣, 请详细了解相关信息。</span><span class="sxs-lookup"><span data-stu-id="78391-114">You can check out our What is [mixed reality?]( article for a more thorough answer if you're interested.</span></span>

## <a name="choose-your-development-path"></a><span data-ttu-id="78391-115">选择开发路径</span><span class="sxs-lookup"><span data-stu-id="78391-115">Choose your development path</span></span>

<span data-ttu-id="78391-116">开发混合现实应用程序的最简单方法是使用[Unity](https://unity3d.com), 这是一个功能强大的常用中间件工具, 通常用于游戏开发。</span><span class="sxs-lookup"><span data-stu-id="78391-116">The easiest way to develop a mixed reality app is using [Unity](https://unity3d.com), a powerful and popular middleware tool often used for game development.</span></span> <span data-ttu-id="78391-117">如果要使用自定义引擎, 还可以[针对 DirectX 进行构建](directx-development-overview.md), 但大多数 MR 开发人员将 Unity 用于其游戏和应用。</span><span class="sxs-lookup"><span data-stu-id="78391-117">If you want to use a custom engine, you can also [build against DirectX](directx-development-overview.md), but most MR developers use Unity for their games and apps.</span></span> <span data-ttu-id="78391-118">使用 Unity, 你将能够创建面向 HoloLens、沉浸式 (VR) 耳机或两者的混合现实应用!</span><span class="sxs-lookup"><span data-stu-id="78391-118">With Unity you'll be able to create a mixed reality app that targets HoloLens, immersive (VR) headsets, or both!</span></span>

## <a name="prepare-your-pc-and-devices-for-development"></a><span data-ttu-id="78391-119">准备 PC 和设备进行开发</span><span class="sxs-lookup"><span data-stu-id="78391-119">Prepare your PC and devices for development</span></span>

<span data-ttu-id="78391-120">无论是要构建面向 HoloLens、沉浸式 (VR) 耳机还是同时使用这两者的混合现实应用, 都将使用一组常用的工具和 Api。</span><span class="sxs-lookup"><span data-stu-id="78391-120">Whether you're building a mixed reality app that targets HoloLens, immersive (VR) headsets, or both, you'll be using a common set of tools and APIs.</span></span> <span data-ttu-id="78391-121">还需要确保您的 PC 的功能足以满足您的开发需要。</span><span class="sxs-lookup"><span data-stu-id="78391-121">You'll also want to make sure your PC is powerful enough for the development you'll be doing.</span></span> 

>[!NOTE]
><span data-ttu-id="78391-122">可以在 "[安装工具](install-the-tools.md)" 一文中找到有关开发 PC 规格、支持的每个软件工具的版本的建议、每个软件工具的相关设置或配置说明。</span><span class="sxs-lookup"><span data-stu-id="78391-122">You can find our recommendations on development PC specs, supported versions of each software tool, and relevant settings or configuration notes for each in the [Install the tools](install-the-tools.md) article.</span></span> <span data-ttu-id="78391-123">安装以下工具之前, 请查看此文章。</span><span class="sxs-lookup"><span data-stu-id="78391-123">Please review that article before installing the tools below.</span></span>

<span data-ttu-id="78391-124">要安装的工具:</span><span class="sxs-lookup"><span data-stu-id="78391-124">Tools to install:</span></span>
* [<span data-ttu-id="78391-125">Unity</span><span class="sxs-lookup"><span data-stu-id="78391-125">Unity</span></span>](https://store.unity.com/download)
* [<span data-ttu-id="78391-126">Visual Studio (适用于 Windows 10 SDK)</span><span class="sxs-lookup"><span data-stu-id="78391-126">Visual Studio (with Windows 10 SDK)</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="78391-127">适用于 Unity 的混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="78391-127">Mixed Reality Toolkit for Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

<span data-ttu-id="78391-128">还需要将[目标设备置于开发人员模式并配置 Visual Studio, 以便将应用程序部署到目标设备](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="78391-128">You'll also want to [put your target device into Developer mode and configure Visual Studio for deploying apps to the target device](using-visual-studio.md).</span></span>

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="78391-129">有关 Unity 混合现实工具包的注释</span><span class="sxs-lookup"><span data-stu-id="78391-129">A note about the Mixed Reality Toolkit for Unity</span></span>

![Unity 的 MRTK](images/mrtkandunity.png)<br>

<span data-ttu-id="78391-131">***YOYO, 请将其充实, 告诉每个人为什么 MRTK 是如此惊人的东西, 并且它在:)***</span><span class="sxs-lookup"><span data-stu-id="78391-131">***YOYO PLEASE FLESH THIS OUT AND TELL EVERYONE WHY MRTK-UNITY IS SO AMAZING AND ALL THE COOL THINGS IT HAS INSIDE :)***</span></span>

<span data-ttu-id="78391-132">混合现实工具包是一个脚本和组件的集合, 旨在加速开发面向 Microsoft HoloLens 和 Windows Mixed Reality 耳机的应用程序。</span><span class="sxs-lookup"><span data-stu-id="78391-132">The Mixed Reality Toolkit is a collection of scripts and components intended to accelerate development of applications targeting Microsoft HoloLens and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="78391-133">该项目旨在降低创建混合现实应用程序的门槛，并在我们共同成长的过程中回馈社区。</span><span class="sxs-lookup"><span data-stu-id="78391-133">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span>

## <a name="start-your-first-mr-project"></a><span data-ttu-id="78391-134">开始第一位 MR 项目</span><span class="sxs-lookup"><span data-stu-id="78391-134">Start your first MR project</span></span>

<span data-ttu-id="78391-135">现在你的电脑和设备已设置完毕, 你可以在 Unity 中创建第一个混合现实项目。</span><span class="sxs-lookup"><span data-stu-id="78391-135">Now that your PC and device(s) are set up, you're ready to create your first mixed reality project in Unity.</span></span> <span data-ttu-id="78391-136">遵循我们的第一位 mr 学院课程[, 先生/女士 100:Unity](holograms-100.md)入门后, 最终你将在混合现实耳机中启动并运行多维数据集。</span><span class="sxs-lookup"><span data-stu-id="78391-136">Follow along with our first MR academy course, [MR Basics 100: Getting started with Unity](holograms-100.md), and by the end you'll have a cube up and running in a mixed reality headset.</span></span>

<span data-ttu-id="78391-137">![混合现实 Unity 项目中的多维数据集的屏幕截图](images/mr-cube.PNG)</span><span class="sxs-lookup"><span data-stu-id="78391-137">![Screenshot of a cube in a mixed reality Unity project](images/mr-cube.PNG)</span></span><br>
<span data-ttu-id="78391-138">*Unity 中的第一个混合现实项目-hello world!*</span><span class="sxs-lookup"><span data-stu-id="78391-138">*Your first mixed reality project in Unity - hello world!*</span></span>

## <a name="learn-more-and-get-help"></a><span data-ttu-id="78391-139">了解详细信息并获得帮助</span><span class="sxs-lookup"><span data-stu-id="78391-139">Learn more and get help</span></span>

<span data-ttu-id="78391-140">现在, 你已成功创建了第一个 MR 项目, 你可能会有更多的需求!</span><span class="sxs-lookup"><span data-stu-id="78391-140">Now that you've successfully created your first MR project, you're probably hungry for more!</span></span> <span data-ttu-id="78391-141">下面是一些应帮助的资源:</span><span class="sxs-lookup"><span data-stu-id="78391-141">Here are some resources that should help:</span></span>
* <span data-ttu-id="78391-142">[混合现实开发人员文档](mixed-reality.md)-您已经在这里, 但还有更多的内容需要查看, 包括技术文档、设计指南、示例项目和案例研究。</span><span class="sxs-lookup"><span data-stu-id="78391-142">[Mixed reality developer documentation](mixed-reality.md) - you're already here, but there's so much more to check out, including technical documentation, design guidance, sample projects, and case studies.</span></span>
* <span data-ttu-id="78391-143">[混合现实教程](tutorials.md)-按照介绍设置项目、实现核心 MR 构建块 (将 Azure 云服务集成到 MR 应用) 的所有内容的教程进行操作。</span><span class="sxs-lookup"><span data-stu-id="78391-143">[Mixed reality tutorials](tutorials.md) - follow along with tutorials covering everything from setting up projects, to implementing core MR building blocks, to integrating Azure cloud services into your MR app.</span></span>
* <span data-ttu-id="78391-144">[了解 unity](https://unity3d.com/learn) -unity 的网站在学习的每个阶段为创建者提供教程、项目和实时培训会话。</span><span class="sxs-lookup"><span data-stu-id="78391-144">[Learn Unity](https://unity3d.com/learn) - Unity's website offers tutorials, projects, and live training sessions for creators at every stage of learning.</span></span>

<span data-ttu-id="78391-145">你还可以从这些强大的社区资源获取帮助:</span><span class="sxs-lookup"><span data-stu-id="78391-145">You can also get help from these great community resources:</span></span>
* <span data-ttu-id="78391-146">[混合现实开发人员论坛](https://forums.hololens.com/)-适用于混合现实开发人员提出和回答问题的官方论坛, 并直接阅读 MICROSOFT 的 MR 开发新闻。</span><span class="sxs-lookup"><span data-stu-id="78391-146">[Mixed reality developer forums](https://forums.hololens.com/) - the official forum for mixed reality developers to ask and answer questions, as well as read MR development news straight from Microsoft.</span></span>
* <span data-ttu-id="78391-147">[HoloDevelopers 宽延时间通道](https://holodevelopersslack.azurewebsites.net/)-最稳健、更丰富的外部混合现实开发渠道;此处的开发人员是一种非常丰富的知识。</span><span class="sxs-lookup"><span data-stu-id="78391-147">[HoloDevelopers Slack channel](https://holodevelopersslack.azurewebsites.net/) - the most robust and resourceful external mixed reality-specific developer channel; the devs here are knowledgeable and helpful.</span></span>
* <span data-ttu-id="78391-148">[Unity 论坛](https://forum.unity3d.com/)-unity 的官方论坛。</span><span class="sxs-lookup"><span data-stu-id="78391-148">[Unity forums](https://forum.unity3d.com/) - Unity's official forums.</span></span>
