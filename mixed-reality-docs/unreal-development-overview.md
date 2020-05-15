---
title: Unreal 开发概述
description: 使用 Unreal Engine 4 进行混合现实开发概述
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 流式传输, 远程处理, 混合现实, 开发, 入门, 功能, 新项目, 仿真器, 文档, 指南, 功能, 全息影像
ms.openlocfilehash: 08ba760acc1a35d8f47de6a7bf6cbc020c8aca3f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851561"
---
# <a name="unreal-development-overview"></a><span data-ttu-id="07b17-104">Unreal 开发概述</span><span class="sxs-lookup"><span data-stu-id="07b17-104">Unreal development overview</span></span>

<span data-ttu-id="07b17-105">Unreal Engine 4 现完全支持针对 Windows 混合现实 (VR) 和 HoloLens 2 (AR) 设备进行开发！</span><span class="sxs-lookup"><span data-stu-id="07b17-105">Unreal Engine 4 now fully supports development for both Windows Mixed Reality (VR) and HoloLens 2 (AR) devices!</span></span> <span data-ttu-id="07b17-106">如果不熟悉 Unreal 开发，不妨浏览一下 <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Unreal Engine 4 入门</a>页面。</span><span class="sxs-lookup"><span data-stu-id="07b17-106">If you're new to Unreal development, <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Getting Started with Unreal Engine 4</a> is a great page to explore.</span></span> <span data-ttu-id="07b17-107">如果你需要资产，Unreal 有一个包罗万象的<a href="https://www.unrealengine.com/marketplace//store" target="_blank">市场</a>。</span><span class="sxs-lookup"><span data-stu-id="07b17-107">If you need assets, Unreal has a comprehensive <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>.</span></span> 

<span data-ttu-id="07b17-108">掌握了 Unreal 开发的基本知识后，请参阅教程的下一节，了解如何在 HoloLens 上构建和运行应用。</span><span class="sxs-lookup"><span data-stu-id="07b17-108">Once you've gained a basic understanding of Unreal development, check out the tutorial in the next section to learn how to build and run your apps on HoloLens.</span></span> <span data-ttu-id="07b17-109">若要与在 Unreal 中构建混合现实应用的社区人员交流心得，请务必访问 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 混合现实论坛</a>。</span><span class="sxs-lookup"><span data-stu-id="07b17-109">Be sure to visit the <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality forums</a> to engage with the community building mixed reality apps in Unreal.</span></span> <span data-ttu-id="07b17-110">那里是一个求教解惑的好去处。</span><span class="sxs-lookup"><span data-stu-id="07b17-110">It's a great place to find solutions to problems you run into.</span></span>

## <a name="tutorial"></a><span data-ttu-id="07b17-111">教程</span><span class="sxs-lookup"><span data-stu-id="07b17-111">Tutorial</span></span>

<span data-ttu-id="07b17-112">遵循我们的端到端教程，你可学习如何针对 HoloLens 2 [生成和部署一款简单的象棋应用](unreal-uxt-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="07b17-112">Learn how to [build and deploy a simple chess app](unreal-uxt-ch1.md) for HoloLens 2 by following our end-to-end tutorial.</span></span> <span data-ttu-id="07b17-113">本教程使用 UX Tools 插件来加速开发包含交互式 UX 组件（包括按钮和操控器）的应用。</span><span class="sxs-lookup"><span data-stu-id="07b17-113">This tutorial uses the UX Tools plugin to accelerate developing apps with interactive UX components including a button and a manipulator.</span></span> <span data-ttu-id="07b17-114">有关 UX Tools 插件的详细信息，请参阅下一节关于 MRTK 的内容。</span><span class="sxs-lookup"><span data-stu-id="07b17-114">For more information about UX Tools plugin, see the next section on MRTK.</span></span> 

## <a name="mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="07b17-115">适用于 Unreal 的混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="07b17-115">Mixed Reality Toolkit for Unreal</span></span>

<span data-ttu-id="07b17-116">[适用于 Unreal 的混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unreal)是一组组件，包含插件、示例和文档，旨在加快使用 Unreal Engine 开发混合现实应用程序的速度。</span><span class="sxs-lookup"><span data-stu-id="07b17-116">The [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) is a set of components, in the form of plugins, samples, and documentation, designed to accelerate the development of mixed reality applications using the Unreal Engine.</span></span> <span data-ttu-id="07b17-117">作为此工具包的一部分，第一个发布的组件是[适用于 Unreal 的 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal)，此插件可添加到 HoloLens 2 项目，为 HoloLens 2 应用程序提供 UX 功能。</span><span class="sxs-lookup"><span data-stu-id="07b17-117">The first component released as part of this toolkit is the [UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), a plugin that can be added to your HoloLens 2 project to provide UX features for HoloLens 2 applications.</span></span> <span data-ttu-id="07b17-118">可在相应的 GitHub 存储库中找到有关适用于 Unreal 的混合现实工具包和 UX Tools 的文档。</span><span class="sxs-lookup"><span data-stu-id="07b17-118">Documentation for the Mixed Reality Toolkit and UX Tools for Unreal can be found in their respective GitHub repositories.</span></span> 

## <a name="performance"></a><span data-ttu-id="07b17-119">性能</span><span class="sxs-lookup"><span data-stu-id="07b17-119">Performance</span></span>

<span data-ttu-id="07b17-120">HoloLens 2 应用必须以每秒 60 帧的速度运行，才能使全息影像稳定显示且快速响应。</span><span class="sxs-lookup"><span data-stu-id="07b17-120">A HoloLens 2 app must run at 60 frames per second for holograms to appear stable and responsive.</span></span> <span data-ttu-id="07b17-121">若要在应用中实现此目的，强烈建议遵循我们[针对 Unreal 的性能建议](performance-recommendations-for-unreal.md)。</span><span class="sxs-lookup"><span data-stu-id="07b17-121">To achieve this in your app, we highly recommend following our [performance recommendations for Unreal](performance-recommendations-for-unreal.md).</span></span> 

## <a name="guides-to-specific-features"></a><span data-ttu-id="07b17-122">特定功能指南</span><span class="sxs-lookup"><span data-stu-id="07b17-122">Guides to specific features</span></span>

<span data-ttu-id="07b17-123">要了解如何使用 Unreal 中的特定功能，请查看以下指南：</span><span class="sxs-lookup"><span data-stu-id="07b17-123">To learn how to use specific features in Unreal, check out the below guides:</span></span> 
* [<span data-ttu-id="07b17-124">手部跟踪</span><span class="sxs-lookup"><span data-stu-id="07b17-124">Hand tracking</span></span>](unreal-hand-tracking.md)
* [<span data-ttu-id="07b17-125">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="07b17-125">Eye tracking</span></span>](unreal-gaze-input.md)
* [<span data-ttu-id="07b17-126">空间映射</span><span class="sxs-lookup"><span data-stu-id="07b17-126">Spatial mapping</span></span>](unreal-spatial-mapping.md)
* [<span data-ttu-id="07b17-127">空间定位点</span><span class="sxs-lookup"><span data-stu-id="07b17-127">Spatial anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="07b17-128">语音输入</span><span class="sxs-lookup"><span data-stu-id="07b17-128">Voice input</span></span>](unreal-voice-input.md)
* [<span data-ttu-id="07b17-129">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="07b17-129">HoloLens camera</span></span>](unreal-hololens-camera.md)
* [<span data-ttu-id="07b17-130">QR 码</span><span class="sxs-lookup"><span data-stu-id="07b17-130">QR codes</span></span>](unreal-qr-codes.md)

## <a name="supported-features"></a><span data-ttu-id="07b17-131">支持的功能</span><span class="sxs-lookup"><span data-stu-id="07b17-131">Supported Features</span></span>

| <span data-ttu-id="07b17-132">HoloLens 2 功能</span><span class="sxs-lookup"><span data-stu-id="07b17-132">HoloLens 2 Feature</span></span> | <span data-ttu-id="07b17-133">最早支持的 Unreal Engine 版本</span><span class="sxs-lookup"><span data-stu-id="07b17-133">Earliest Supported Unreal Engine Version</span></span> |
| ----------- | ----------- |
| <span data-ttu-id="07b17-134">ARM64 支持</span><span class="sxs-lookup"><span data-stu-id="07b17-134">ARM64 support</span></span> | <span data-ttu-id="07b17-135">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-135">4.23</span></span> |
| <span data-ttu-id="07b17-136">从电脑进行流式传输</span><span class="sxs-lookup"><span data-stu-id="07b17-136">Streaming from a PC</span></span> | <span data-ttu-id="07b17-137">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-137">4.23</span></span> |
| <span data-ttu-id="07b17-138">空间映射</span><span class="sxs-lookup"><span data-stu-id="07b17-138">Spatial mapping</span></span> | <span data-ttu-id="07b17-139">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-139">4.23</span></span> |
| <span data-ttu-id="07b17-140">手动和联合跟踪</span><span class="sxs-lookup"><span data-stu-id="07b17-140">Hand and joint tracking</span></span> | <span data-ttu-id="07b17-141">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-141">4.23</span></span> |
| <span data-ttu-id="07b17-142">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="07b17-142">Eye tracking</span></span> | <span data-ttu-id="07b17-143">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-143">4.23</span></span> |
| <span data-ttu-id="07b17-144">语音输入</span><span class="sxs-lookup"><span data-stu-id="07b17-144">Voice input</span></span> | <span data-ttu-id="07b17-145">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-145">4.23</span></span> |
| <span data-ttu-id="07b17-146">空间定位点</span><span class="sxs-lookup"><span data-stu-id="07b17-146">Spatial anchors</span></span> | <span data-ttu-id="07b17-147">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-147">4.23</span></span> |
| <span data-ttu-id="07b17-148">摄像头访问</span><span class="sxs-lookup"><span data-stu-id="07b17-148">Camera access</span></span> | <span data-ttu-id="07b17-149">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-149">4.23</span></span> |
| <span data-ttu-id="07b17-150">QR 码</span><span class="sxs-lookup"><span data-stu-id="07b17-150">QR codes</span></span> | <span data-ttu-id="07b17-151">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-151">4.23</span></span> |
| <span data-ttu-id="07b17-152">空间音频</span><span class="sxs-lookup"><span data-stu-id="07b17-152">Spatial audio</span></span> | <span data-ttu-id="07b17-153">4.23</span><span class="sxs-lookup"><span data-stu-id="07b17-153">4.23</span></span> |
| <span data-ttu-id="07b17-154">Spectator Screen 支持流式传输</span><span class="sxs-lookup"><span data-stu-id="07b17-154">Spectator Screen support for streaming</span></span> | <span data-ttu-id="07b17-155">4.24</span><span class="sxs-lookup"><span data-stu-id="07b17-155">4.24</span></span> |
| <span data-ttu-id="07b17-156">通过流式传输的平面 LSR</span><span class="sxs-lookup"><span data-stu-id="07b17-156">Planar LSR over streaming</span></span> | <span data-ttu-id="07b17-157">4.24</span><span class="sxs-lookup"><span data-stu-id="07b17-157">4.24</span></span> |
| <span data-ttu-id="07b17-158">示例应用（[HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 和[任务 AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)）</span><span class="sxs-lookup"><span data-stu-id="07b17-158">Sample apps ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) and [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html))</span></span> | <span data-ttu-id="07b17-159">4.24</span><span class="sxs-lookup"><span data-stu-id="07b17-159">4.24</span></span> |
| <span data-ttu-id="07b17-160">移动多视图：性能达到 60 fps</span><span class="sxs-lookup"><span data-stu-id="07b17-160">Mobile multi-View: Performance hits 60 fps</span></span> | <span data-ttu-id="07b17-161">4.25</span><span class="sxs-lookup"><span data-stu-id="07b17-161">4.25</span></span> |
| <span data-ttu-id="07b17-162">第三人称摄像机渲染</span><span class="sxs-lookup"><span data-stu-id="07b17-162">3rd camera render</span></span> | <span data-ttu-id="07b17-163">4.25</span><span class="sxs-lookup"><span data-stu-id="07b17-163">4.25</span></span> |
| <span data-ttu-id="07b17-164">从打包的桌面应用进行流式传输</span><span class="sxs-lookup"><span data-stu-id="07b17-164">Streaming from a packaged desktop app</span></span> | <span data-ttu-id="07b17-165">4.25</span><span class="sxs-lookup"><span data-stu-id="07b17-165">4.25</span></span> |
| <span data-ttu-id="07b17-166">面向 HoloLens 2 的 Azure 空间定位点 (beta)</span><span class="sxs-lookup"><span data-stu-id="07b17-166">Azure Spatial Anchors for HoloLens 2 (beta)</span></span> | <span data-ttu-id="07b17-167">4.25</span><span class="sxs-lookup"><span data-stu-id="07b17-167">4.25</span></span> |
| <span data-ttu-id="07b17-168">OpenXR 支持 (beta)</span><span class="sxs-lookup"><span data-stu-id="07b17-168">OpenXR support (beta)</span></span> | <span data-ttu-id="07b17-169">4.25</span><span class="sxs-lookup"><span data-stu-id="07b17-169">4.25</span></span> |
| <span data-ttu-id="07b17-170">UX Tools 支持 (0.8)</span><span class="sxs-lookup"><span data-stu-id="07b17-170">UX Tools support (0.8)</span></span> | <span data-ttu-id="07b17-171">4.25</span><span class="sxs-lookup"><span data-stu-id="07b17-171">4.25</span></span> |
| <span data-ttu-id="07b17-172">开发人员文档和教程</span><span class="sxs-lookup"><span data-stu-id="07b17-172">Developer docs & tutorials</span></span> | <span data-ttu-id="07b17-173">4.25</span><span class="sxs-lookup"><span data-stu-id="07b17-173">4.25</span></span> |

## <a name="see-also"></a><span data-ttu-id="07b17-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07b17-174">See also</span></span>
* <span data-ttu-id="07b17-175"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">关于流式传输、部署到仿真器和设备的 Unreal 文档</a></span><span class="sxs-lookup"><span data-stu-id="07b17-175"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Unreal docs for streaming, deploying to emulator and device</a></span></span>
* <span data-ttu-id="07b17-176"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">移动设备的 Unreal 性能指南</a></span><span class="sxs-lookup"><span data-stu-id="07b17-176"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a></span></span>
