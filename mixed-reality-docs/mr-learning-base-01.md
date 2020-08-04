---
title: 入门教程 - 1. 简介
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 330863d36abe051e8fe17b87ce913b1b110e2d3d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376429"
---
# <a name="1-introduction"></a><span data-ttu-id="015cf-105">1.简介</span><span class="sxs-lookup"><span data-stu-id="015cf-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="015cf-106">概述</span><span class="sxs-lookup"><span data-stu-id="015cf-106">Overview</span></span>

<span data-ttu-id="015cf-107">欢迎使用入门教程系列！</span><span class="sxs-lookup"><span data-stu-id="015cf-107">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="015cf-108">这些教程将介绍混合现实工具包 (MRTK) 及其提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="015cf-108">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="015cf-109">此外，还将构建一个混合现实体验，让用户可在其中浏览按 NASA 的“好奇号”火星探测车建模的全息图。</span><span class="sxs-lookup"><span data-stu-id="015cf-109">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="015cf-110">本系列结束后，你将牢牢把握 MRTK 及其如何加速开发过程。</span><span class="sxs-lookup"><span data-stu-id="015cf-110">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="015cf-111">本系列教程的设计遵循一定的顺序，因此请按正确的顺序学习：</span><span class="sxs-lookup"><span data-stu-id="015cf-111">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. [<span data-ttu-id="015cf-112">简介</span><span class="sxs-lookup"><span data-stu-id="015cf-112">Introduction</span></span>](mr-learning-base-01.md)
2. [<span data-ttu-id="015cf-113">初始化项目并部署第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="015cf-113">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="015cf-114">配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="015cf-114">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="015cf-115">定位场景中的对象</span><span class="sxs-lookup"><span data-stu-id="015cf-115">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="015cf-116">使用求解器创建动态内容</span><span class="sxs-lookup"><span data-stu-id="015cf-116">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="015cf-117">创建用户界面</span><span class="sxs-lookup"><span data-stu-id="015cf-117">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="015cf-118">与 3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="015cf-118">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="015cf-119">使用眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="015cf-119">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="015cf-120">使用语音命令</span><span class="sxs-lookup"><span data-stu-id="015cf-120">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="015cf-121">目标</span><span class="sxs-lookup"><span data-stu-id="015cf-121">Objectives</span></span>

* <span data-ttu-id="015cf-122">了解如何针对 MRTK 配置 Unity</span><span class="sxs-lookup"><span data-stu-id="015cf-122">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="015cf-123">了解如何生成和部署到设备</span><span class="sxs-lookup"><span data-stu-id="015cf-123">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="015cf-124">了解如何使用 MRTK 的一些主要功能</span><span class="sxs-lookup"><span data-stu-id="015cf-124">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="015cf-125">创建完整的混合现实体验</span><span class="sxs-lookup"><span data-stu-id="015cf-125">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="015cf-126">必备条件</span><span class="sxs-lookup"><span data-stu-id="015cf-126">Prerequisites</span></span>

* <span data-ttu-id="015cf-127">一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="015cf-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="015cf-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="015cf-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="015cf-129">一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="015cf-129">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="015cf-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>，其中已安装 Unity 2019.3.15 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="015cf-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="015cf-131">建议用于本系列教程的 MRTK 版本是 MRTK 2.4.0。</span><span class="sxs-lookup"><span data-stu-id="015cf-131">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="015cf-132">建议对本系列教程使用 Unity 2019.3.15。</span><span class="sxs-lookup"><span data-stu-id="015cf-132">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="015cf-133">这将取代上述链接的先决条件中所述的任何 Unity 版本要求。</span><span class="sxs-lookup"><span data-stu-id="015cf-133">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="015cf-134">下一教程：2.初始化项目并部署第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="015cf-134">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
