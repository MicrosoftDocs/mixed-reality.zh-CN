---
title: 1. 入门
description: 教程第 1 部分介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840126"
---
# <a name="1-getting-started"></a><span data-ttu-id="54012-104">1.入门</span><span class="sxs-lookup"><span data-stu-id="54012-104">1. Getting started</span></span>

<span data-ttu-id="54012-105">本分步教程将向你展示如何使用 Unreal Engine 4 构建一个交互式 HoloLens 2 象棋应用。</span><span class="sxs-lookup"><span data-stu-id="54012-105">This is a step by step tutorial that will show you how to build an interactive HoloLens 2 chess app using Unreal Engine 4.</span></span> <span data-ttu-id="54012-106">你还将了解如何使用适用于 Unreal 的混合现实工具包中的 UX Tools 插件来加快开发进程。</span><span class="sxs-lookup"><span data-stu-id="54012-106">You will also learn how to use the UX Tools plugin from the Mixed Reality Toolkit for Unreal to speed up development.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="54012-107">必备条件</span><span class="sxs-lookup"><span data-stu-id="54012-107">Prerequisites</span></span>

* <span data-ttu-id="54012-108">Windows 10 1809 或更高版本</span><span class="sxs-lookup"><span data-stu-id="54012-108">Windows 10 1809 or later</span></span>
* <span data-ttu-id="54012-109">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="54012-109">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="54012-110">Unreal Engine 4.25 或更高版本</span><span class="sxs-lookup"><span data-stu-id="54012-110">Unreal Engine 4.25 or later</span></span>
* <span data-ttu-id="54012-111">[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 Microsoft HoloLens 2 设备，或仿真器</span><span class="sxs-lookup"><span data-stu-id="54012-111">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="54012-112">Visual Studio 2019（包含以下工作负载和组件）</span><span class="sxs-lookup"><span data-stu-id="54012-112">Visual Studio 2019 (with below workloads and components)</span></span>

### <a name="installing-visual-studio-2019-workloads-and-components"></a><span data-ttu-id="54012-113">安装 Visual Studio 2019、工作负载和组件</span><span class="sxs-lookup"><span data-stu-id="54012-113">Installing Visual Studio 2019, workloads, and components</span></span>
1. <span data-ttu-id="54012-114">安装或更新到最新版本的 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="54012-114">Install or and update to the latest version of Visual Studio 2019</span></span>
* [<span data-ttu-id="54012-115">下载 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="54012-115">Download Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
2. <span data-ttu-id="54012-116">安装以下工作负载：</span><span class="sxs-lookup"><span data-stu-id="54012-116">Install the following workloads:</span></span>
* <span data-ttu-id="54012-117">使用 C++ 的桌面开发</span><span class="sxs-lookup"><span data-stu-id="54012-117">Desktop development with C++</span></span>
* <span data-ttu-id="54012-118">.NET 桌面开发</span><span class="sxs-lookup"><span data-stu-id="54012-118">.NET desktop development</span></span>
* <span data-ttu-id="54012-119">通用 Windows 平台开发</span><span class="sxs-lookup"><span data-stu-id="54012-119">Universal Windows Platform development</span></span>
3. <span data-ttu-id="54012-120">安装以下各个组件：</span><span class="sxs-lookup"><span data-stu-id="54012-120">Install the following individual components:</span></span>
* <span data-ttu-id="54012-121">编译器、生成工具和运行时 > MSVC v142 - VS 2019 C++ ARM64 生成工具（最新版本）</span><span class="sxs-lookup"><span data-stu-id="54012-121">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

[<span data-ttu-id="54012-122">下一节：2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="54012-122">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)