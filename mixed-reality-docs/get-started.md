---
title: 立即开始行动
description: 本指南概述了混合的现实开发快速启动并正在运行的最快方法。
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: 开始，基础知识，HoloLens，沉浸式头戴式耳机、 ar、 vr、 unity、 visual studio、 快速入门中，如何
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873962"
---
# <a name="get-started"></a><span data-ttu-id="77cd6-104">立即开始行动</span><span class="sxs-lookup"><span data-stu-id="77cd6-104">Get started</span></span>

<span data-ttu-id="77cd6-105">欢迎来到混合的现实开发的世界 ！</span><span class="sxs-lookup"><span data-stu-id="77cd6-105">Welcome to the world of mixed reality development!</span></span> <span data-ttu-id="77cd6-106">如果您是初次接触 MR，本指南将你的中心启动和尽可能快地运行。</span><span class="sxs-lookup"><span data-stu-id="77cd6-106">If you're new to MR, this guide will be your hub to get up and running as quickly as possible.</span></span> <span data-ttu-id="77cd6-107">我们将帮助你获取用于开发的 PC 设置、 准备在设备和安装工具将加快 MR 开发过程。</span><span class="sxs-lookup"><span data-stu-id="77cd6-107">We'll help you get your PC set up for development, get your device(s) ready, and install tools that will speed up the MR development process.</span></span> 

## <a name="intro-to-mixed-reality"></a><span data-ttu-id="77cd6-108">混合现实简介</span><span class="sxs-lookup"><span data-stu-id="77cd6-108">Intro to mixed reality</span></span>

<span data-ttu-id="77cd6-109">可能有一些有关我们所说的"mixed reality"和它如何与增强现实 (AR) 相关的问题和虚拟现实 (VR)。</span><span class="sxs-lookup"><span data-stu-id="77cd6-109">You may have some questions about what we mean by "mixed reality" and how it relates to augmented reality (AR) and virtual reality (VR).</span></span> <span data-ttu-id="77cd6-110">简单地说，混合的现实是混合现实世界与数字世界，因此它是从增强现实的一切内容提供了一系列数字内容在现实生活中，为虚拟现实，现实世界其中几乎完全是中的放置位置替换为数字。</span><span class="sxs-lookup"><span data-stu-id="77cd6-110">In short, mixed reality is the blending of the physical world with the digital world, so it's a spectrum that covers everything from augmented reality, where digital content is placed in the real world, to virtual reality, where your real world is almost entirely replaced by the digital.</span></span> 

<span data-ttu-id="77cd6-111">![支持 HoloLens 和沉浸式 (VR) 耳机的混合的现实应用程序示例](images/mr-island.png)</span><span class="sxs-lookup"><span data-stu-id="77cd6-111">![Example of a mixed reality app that supports both HoloLens and immersive (VR) headsets](images/mr-island.png)</span></span><br>
<span data-ttu-id="77cd6-112">*混合的现实应用可以支持 HoloLens 和沉浸式 (VR) 耳机*</span><span class="sxs-lookup"><span data-stu-id="77cd6-112">*Mixed reality apps can support both HoloLens and immersive (VR) headsets*</span></span>

<span data-ttu-id="77cd6-113">我们作为一个开发平台和组的工具，可以覆盖 MR 范围内，创建 Windows Mixed Reality 和我们目前支持涵盖的相同范围的两种设备类型：[Microsoft HoloLens](https://www.microsoft.com/hololens)，世界上的第一个自包含 holographic 耳机，并[Windows Mixed Reality 沉浸式耳机和动作控制器](https://www.microsoft.com/windows/windows-mixed-reality)，其连接到 PC for 强大虚拟现实体验。</span><span class="sxs-lookup"><span data-stu-id="77cd6-113">We created Windows Mixed Reality as a single development platform and set of tools that can cover the MR spectrum, and we currently support two device types that cover the same spectrum: [Microsoft HoloLens](https://www.microsoft.com/hololens), the world's first self-contained holographic headset, and [Windows Mixed Reality immersive headsets and motion controllers](https://www.microsoft.com/windows/windows-mixed-reality), which connect to a PC for powerful virtual reality experiences.</span></span> <span data-ttu-id="77cd6-114">您可以签出我们什么 [混合现实]？（有关更全面的答案，如果您感兴趣的文章。</span><span class="sxs-lookup"><span data-stu-id="77cd6-114">You can check out our What is [mixed reality?]( article for a more thorough answer if you're interested.</span></span>

## <a name="choose-your-development-path"></a><span data-ttu-id="77cd6-115">选择您开发的路径</span><span class="sxs-lookup"><span data-stu-id="77cd6-115">Choose your development path</span></span>

<span data-ttu-id="77cd6-116">若要开发混合的现实应用程序的最简单方法使用[Unity](https://unity3d.com)，通常用于游戏开发的功能强大且常用的中间件工具。</span><span class="sxs-lookup"><span data-stu-id="77cd6-116">The easiest way to develop a mixed reality app is using [Unity](https://unity3d.com), a powerful and popular middleware tool often used for game development.</span></span> <span data-ttu-id="77cd6-117">如果你想要使用自定义引擎，还可以[针对 DirectX 生成](directx-development-overview.md)，但是大多数 MR 开发人员使用 Unity 进行其游戏和应用程序。</span><span class="sxs-lookup"><span data-stu-id="77cd6-117">If you want to use a custom engine, you can also [build against DirectX](directx-development-overview.md), but most MR developers use Unity for their games and apps.</span></span> <span data-ttu-id="77cd6-118">使用 Unity 将能够创建面向 HoloLens、 沉浸式 (VR) 耳机，或这两者的混合的现实应用 ！</span><span class="sxs-lookup"><span data-stu-id="77cd6-118">With Unity you'll be able to create a mixed reality app that targets HoloLens, immersive (VR) headsets, or both!</span></span>

## <a name="prepare-your-pc-and-devices-for-development"></a><span data-ttu-id="77cd6-119">准备你的 PC 和设备进行开发</span><span class="sxs-lookup"><span data-stu-id="77cd6-119">Prepare your PC and devices for development</span></span>

<span data-ttu-id="77cd6-120">无论构建面向 HoloLens、 沉浸式 (VR) 耳机，或这两者的混合的现实应用，则您将使用一组常用的工具和 Api。</span><span class="sxs-lookup"><span data-stu-id="77cd6-120">Whether you're building a mixed reality app that targets HoloLens, immersive (VR) headsets, or both, you'll be using a common set of tools and APIs.</span></span> <span data-ttu-id="77cd6-121">此外需要确保您的 PC 是功能强大，足以用于开发时需要执行。</span><span class="sxs-lookup"><span data-stu-id="77cd6-121">You'll also want to make sure your PC is powerful enough for the development you'll be doing.</span></span> 

>[!NOTE]
><span data-ttu-id="77cd6-122">您可以找到了开发 PC 上的建议规范，支持的每个软件工具，版本和相关设置或配置说明中的 for each[安装的工具](install-the-tools.md)一文。</span><span class="sxs-lookup"><span data-stu-id="77cd6-122">You can find our recommendations on development PC specs, supported versions of each software tool, and relevant settings or configuration notes for each in the [Install the tools](install-the-tools.md) article.</span></span> <span data-ttu-id="77cd6-123">请安装以下工具之前，查看这篇文章。</span><span class="sxs-lookup"><span data-stu-id="77cd6-123">Please review that article before installing the tools below.</span></span>

<span data-ttu-id="77cd6-124">若要安装的工具：</span><span class="sxs-lookup"><span data-stu-id="77cd6-124">Tools to install:</span></span>
* [<span data-ttu-id="77cd6-125">Unity</span><span class="sxs-lookup"><span data-stu-id="77cd6-125">Unity</span></span>](https://store.unity.com/download)
* [<span data-ttu-id="77cd6-126">Visual Studio (使用 Windows 10 SDK)</span><span class="sxs-lookup"><span data-stu-id="77cd6-126">Visual Studio (with Windows 10 SDK)</span></span>](https://developer.microsoft.com/windows/downloads)
* [<span data-ttu-id="77cd6-127">适用于 Unity 的混合的现实工具包</span><span class="sxs-lookup"><span data-stu-id="77cd6-127">Mixed Reality Toolkit for Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

<span data-ttu-id="77cd6-128">您还需要[将你的目标设备放入开发人员模式和配置 Visual Studio 以进行应用部署到目标设备](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="77cd6-128">You'll also want to [put your target device into Developer mode and configure Visual Studio for deploying apps to the target device](using-visual-studio.md).</span></span>

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="77cd6-129">有关适用于 Unity 的混合现实工具包的注意事项</span><span class="sxs-lookup"><span data-stu-id="77cd6-129">A note about the Mixed Reality Toolkit for Unity</span></span>

![Unity 的 MRTK](images/mrtkandunity.png)<br>

<span data-ttu-id="77cd6-131">***YOYO 请填充此项，然后告诉每个人为何 MRTK UNITY 是人诧异，那还有的炫酷功能十分内:)***</span><span class="sxs-lookup"><span data-stu-id="77cd6-131">***YOYO PLEASE FLESH THIS OUT AND TELL EVERYONE WHY MRTK-UNITY IS SO AMAZING AND ALL THE COOL THINGS IT HAS INSIDE :)***</span></span>

<span data-ttu-id="77cd6-132">混合现实工具包是脚本的集合，组件应加速开发针对 Microsoft HoloLens 和 Windows 混合现实耳机的应用程序。</span><span class="sxs-lookup"><span data-stu-id="77cd6-132">The Mixed Reality Toolkit is a collection of scripts and components intended to accelerate development of applications targeting Microsoft HoloLens and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="77cd6-133">项目功能旨在减少到条目创建混合的现实应用程序并提供回社区，随着我们所有的发展的障碍。</span><span class="sxs-lookup"><span data-stu-id="77cd6-133">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span>

## <a name="start-your-first-mr-project"></a><span data-ttu-id="77cd6-134">启动第一个 MR 项目</span><span class="sxs-lookup"><span data-stu-id="77cd6-134">Start your first MR project</span></span>

<span data-ttu-id="77cd6-135">现在，设置您的 PC 和设备，你准备好在 Unity 中创建第一个混合的现实项目。</span><span class="sxs-lookup"><span data-stu-id="77cd6-135">Now that your PC and device(s) are set up, you're ready to create your first mixed reality project in Unity.</span></span> <span data-ttu-id="77cd6-136">按照我们的第一个 MR 学院课程， [MR 基础知识 100:开始使用 Unity](holograms-100.md)，结束时您一定会启动并运行了混合的现实耳机，多维数据集。</span><span class="sxs-lookup"><span data-stu-id="77cd6-136">Follow along with our first MR academy course, [MR Basics 100: Getting started with Unity](holograms-100.md), and by the end you'll have a cube up and running in a mixed reality headset.</span></span>

<span data-ttu-id="77cd6-137">![混合的现实 Unity 项目中的多维数据集的屏幕截图](images/mr-cube.PNG)</span><span class="sxs-lookup"><span data-stu-id="77cd6-137">![Screenshot of a cube in a mixed reality Unity project](images/mr-cube.PNG)</span></span><br>
<span data-ttu-id="77cd6-138">*Unity-你好世界中第一个混合的现实项目 ！*</span><span class="sxs-lookup"><span data-stu-id="77cd6-138">*Your first mixed reality project in Unity - hello world!*</span></span>

## <a name="learn-more-and-get-help"></a><span data-ttu-id="77cd6-139">了解详细信息并获取帮助</span><span class="sxs-lookup"><span data-stu-id="77cd6-139">Learn more and get help</span></span>

<span data-ttu-id="77cd6-140">既然您已成功创建第一个 MR 项目，您就可能消耗大量的详细信息 ！</span><span class="sxs-lookup"><span data-stu-id="77cd6-140">Now that you've successfully created your first MR project, you're probably hungry for more!</span></span> <span data-ttu-id="77cd6-141">下面是一些资源，可帮助：</span><span class="sxs-lookup"><span data-stu-id="77cd6-141">Here are some resources that should help:</span></span>
* <span data-ttu-id="77cd6-142">[混合现实开发人员文档](mixed-reality.md)-您已经在这里，但有更多功能，若要查看，包括技术文档、 设计指南、 示例项目和案例研究。</span><span class="sxs-lookup"><span data-stu-id="77cd6-142">[Mixed reality developer documentation](mixed-reality.md) - you're already here, but there's so much more to check out, including technical documentation, design guidance, sample projects, and case studies.</span></span>
* <span data-ttu-id="77cd6-143">[混合现实教程](tutorials.md)-按照教程涵盖了从项目中，为实现核心 MR 构建基块进行设置，将集成 Azure MR 应用到云服务。</span><span class="sxs-lookup"><span data-stu-id="77cd6-143">[Mixed reality tutorials](tutorials.md) - follow along with tutorials covering everything from setting up projects, to implementing core MR building blocks, to integrating Azure cloud services into your MR app.</span></span>
* <span data-ttu-id="77cd6-144">[了解 Unity](https://unity3d.com/learn) -Unity 的网站提供教程、 项目和实时培训课程创建者的每个阶段的学习。</span><span class="sxs-lookup"><span data-stu-id="77cd6-144">[Learn Unity](https://unity3d.com/learn) - Unity's website offers tutorials, projects, and live training sessions for creators at every stage of learning.</span></span>

<span data-ttu-id="77cd6-145">此外可以从这些良好的社区资源获取帮助：</span><span class="sxs-lookup"><span data-stu-id="77cd6-145">You can also get help from these great community resources:</span></span>
* <span data-ttu-id="77cd6-146">[混合现实开发人员论坛](https://forums.hololens.com/)-混合的现实开发人员提出和回答问题，以及从 Microsoft 直接读取 MR 开发新闻的官方论坛。</span><span class="sxs-lookup"><span data-stu-id="77cd6-146">[Mixed reality developer forums](https://forums.hololens.com/) - the official forum for mixed reality developers to ask and answer questions, as well as read MR development news straight from Microsoft.</span></span>
* <span data-ttu-id="77cd6-147">[HoloDevelopers Slack 通道](https://holodevelopersslack.azurewebsites.net/)-最可靠且提供丰富的内容的外部混合现实特定于开发人员通道; 此处的开发人员是知识渊博的专家和有帮助。</span><span class="sxs-lookup"><span data-stu-id="77cd6-147">[HoloDevelopers Slack channel](https://holodevelopersslack.azurewebsites.net/) - the most robust and resourceful external mixed reality-specific developer channel; the devs here are knowledgeable and helpful.</span></span>
* <span data-ttu-id="77cd6-148">[Unity 论坛](https://forum.unity3d.com/)-Unity 的官方论坛。</span><span class="sxs-lookup"><span data-stu-id="77cd6-148">[Unity forums](https://forum.unity3d.com/) - Unity's official forums.</span></span>
