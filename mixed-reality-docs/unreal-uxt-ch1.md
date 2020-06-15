---
title: 1. 入门
description: 教程系列第 1 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: c16671fc8f4233378dafa646786df1f7b5ae18e1
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330164"
---
# <a name="1-getting-started"></a><span data-ttu-id="b22ce-104">1.入门</span><span class="sxs-lookup"><span data-stu-id="b22ce-104">1. Getting started</span></span>

<span data-ttu-id="b22ce-105">无论你是混合现实新手还是经验丰富的专业人员，都可以使用 [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) 和 [Unreal Engine](https://www.unrealengine.com/en-US/) 开始你的体验之旅。</span><span class="sxs-lookup"><span data-stu-id="b22ce-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="b22ce-106">本系列教程将为你提供有关如何使用 [UX Tools 插件](https://github.com/microsoft/MixedReality-UXTools-Unreal)构建交互式象棋应用的分步指南，该插件是 [Unreal 混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unreal)的一部分。</span><span class="sxs-lookup"><span data-stu-id="b22ce-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="b22ce-107">该插件将帮助你通过代码、蓝图和示例将常见的 UX 功能添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="b22ce-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![在视口中结束场景](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="b22ce-109">在本系列文章结束时，你将拥有以下方面的实操经验：</span><span class="sxs-lookup"><span data-stu-id="b22ce-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="b22ce-110">开始新项目</span><span class="sxs-lookup"><span data-stu-id="b22ce-110">Starting a new project</span></span>
* <span data-ttu-id="b22ce-111">设置混合现实</span><span class="sxs-lookup"><span data-stu-id="b22ce-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="b22ce-112">使用用户输入</span><span class="sxs-lookup"><span data-stu-id="b22ce-112">Working with user input</span></span>
* <span data-ttu-id="b22ce-113">添加按钮</span><span class="sxs-lookup"><span data-stu-id="b22ce-113">Adding buttons</span></span>
* <span data-ttu-id="b22ce-114">在模拟器或设备上播放</span><span class="sxs-lookup"><span data-stu-id="b22ce-114">Playing on an emulator or device</span></span>

<span data-ttu-id="b22ce-115">如果有任何疑问，请查看我们的 [Unreal 开发概述](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)。</span><span class="sxs-lookup"><span data-stu-id="b22ce-115">If you have any questions, check out our [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b22ce-116">必备条件</span><span class="sxs-lookup"><span data-stu-id="b22ce-116">Prerequisites</span></span>
<span data-ttu-id="b22ce-117">在开始之前，请确保满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="b22ce-117">Make sure you've met the following requirements before jumping in:</span></span>
* <span data-ttu-id="b22ce-118">Windows 10 1809 或更高版本</span><span class="sxs-lookup"><span data-stu-id="b22ce-118">Windows 10 1809 or later</span></span>
* <span data-ttu-id="b22ce-119">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="b22ce-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="b22ce-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 或更高版本</span><span class="sxs-lookup"><span data-stu-id="b22ce-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="b22ce-121">[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 Microsoft HoloLens 2 设备，或仿真器</span><span class="sxs-lookup"><span data-stu-id="b22ce-121">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="b22ce-122">具有以下工作负载的 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b22ce-122">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="b22ce-123">安装 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b22ce-123">Installing Visual Studio 2019</span></span>
<span data-ttu-id="b22ce-124">最后一步是设置 Visual Studio，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b22ce-124">The last step is to setup Visual Studio as follows:</span></span>
1. <span data-ttu-id="b22ce-125">安装最新版本的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span><span class="sxs-lookup"><span data-stu-id="b22ce-125">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="b22ce-126">安装以下[工作负载](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads)：</span><span class="sxs-lookup"><span data-stu-id="b22ce-126">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):</span></span>
    * <span data-ttu-id="b22ce-127">使用 C++ 的桌面开发</span><span class="sxs-lookup"><span data-stu-id="b22ce-127">Desktop development with C++</span></span>
    * <span data-ttu-id="b22ce-128">.NET 桌面开发</span><span class="sxs-lookup"><span data-stu-id="b22ce-128">.NET desktop development</span></span>
    * <span data-ttu-id="b22ce-129">通用 Windows 平台开发</span><span class="sxs-lookup"><span data-stu-id="b22ce-129">Universal Windows Platform development</span></span>

3. <span data-ttu-id="b22ce-130">安装以下[组件](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components)：</span><span class="sxs-lookup"><span data-stu-id="b22ce-130">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):</span></span>
    * <span data-ttu-id="b22ce-131">编译器、生成工具和运行时 > MSVC v142 - VS 2019 C++ ARM64 生成工具（最新版本）</span><span class="sxs-lookup"><span data-stu-id="b22ce-131">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="b22ce-132">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="b22ce-132">That's it!</span></span> <span data-ttu-id="b22ce-133">一切准备就绪，现在可以开始象棋应用项目了。</span><span class="sxs-lookup"><span data-stu-id="b22ce-133">You're all set to move on to starting the chess app project.</span></span>

[<span data-ttu-id="b22ce-134">下一节：2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="b22ce-134">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)