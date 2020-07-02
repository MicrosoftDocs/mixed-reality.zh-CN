---
title: Unreal 开发概述
description: 使用 Unreal Engine 4 进行混合现实开发概述
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 流式传输, 远程处理, 混合现实, 开发, 入门, 功能, 新项目, 仿真器, 文档, 指南, 功能, 全息影像, 游戏开发
ms.openlocfilehash: 0e3f40c7aa05a9c5f93d7eb9dc9793b6daeb8b90
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720363"
---
# <a name="unreal-development-overview"></a><span data-ttu-id="9c1c8-104">Unreal 开发概述</span><span class="sxs-lookup"><span data-stu-id="9c1c8-104">Unreal Development Overview</span></span>

<span data-ttu-id="9c1c8-105">开始使用<a href="https://docs.microsoft.com/en-us/windows/mixed-reality" target="_blank" title="混合现实文档">混合现实应用程序</a>是一个重大任务。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-105">Getting started with <a href="https://docs.microsoft.com/en-us/windows/mixed-reality" target="_blank" title="Mixed Reality Docs"> mixed reality applications</a> is a big task.</span></span> <span data-ttu-id="9c1c8-106">新概念、平台和前沿硬件看似都障碍重重。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-106">New concepts, platforms, and cutting edge hardware can seem like barriers.</span></span> <span data-ttu-id="9c1c8-107">但是，如果你是 Unreal 的开发人员，那么你很幸运。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-107">However, if you're an Unreal developer you're in luck.</span></span> <span data-ttu-id="9c1c8-108">对 <a href="https://www.microsoft.com/en-us/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality 文档">Windows Mixed Reality</a> (VR) 和 <a href="https://www.microsoft.com/en-us/hololens/hardware" target="_blank" title="HoloLens 2 文档">HoloLens 2</a> (AR) 的支持现已包含在 Unreal Engine 的最新 <a href="https://docs.unrealengine.com/en-US/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 发行说明">版本</a>中。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-108">Support for <a href="https://www.microsoft.com/en-us/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality Docs">Windows Mixed Reality</a> (VR) and <a href="https://www.microsoft.com/en-us/hololens/hardware" target="_blank" title="HoloLens 2 Docs">HoloLens 2</a> (AR) is now included in Unreal Engine's newest <a href="https://docs.unrealengine.com/en-US/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 release notes">release</a>.</span></span> <span data-ttu-id="9c1c8-109">此更新包括：</span><span class="sxs-lookup"><span data-stu-id="9c1c8-109">This update includes:</span></span>
* <span data-ttu-id="9c1c8-110">混合现实 UX Tools 插件支持</span><span class="sxs-lookup"><span data-stu-id="9c1c8-110">Mixed Reality UX Tools plugin support</span></span>
* <span data-ttu-id="9c1c8-111">OpenXR 支持</span><span class="sxs-lookup"><span data-stu-id="9c1c8-111">OpenXR support</span></span>
* <span data-ttu-id="9c1c8-112">桌面应用中的应用远程处理</span><span class="sxs-lookup"><span data-stu-id="9c1c8-112">App Remoting from a desktop app</span></span>
* <span data-ttu-id="9c1c8-113">更好的性能</span><span class="sxs-lookup"><span data-stu-id="9c1c8-113">Better performance</span></span>
* <span data-ttu-id="9c1c8-114">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="9c1c8-114">Mixed reality capture</span></span>
* <span data-ttu-id="9c1c8-115">对 Azure 空间定位点的初始支持</span><span class="sxs-lookup"><span data-stu-id="9c1c8-115">Initial support for Azure Spatial Anchors</span></span>

<span data-ttu-id="9c1c8-116">如果你不熟悉 Unreal 开发，请勿直接跳转。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-116">If you're new to Unreal development don't jump in blind.</span></span> <span data-ttu-id="9c1c8-117">探索 Unreal <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">教程系列</a>，以快速了解和查找 Unreal <a href="https://www.unrealengine.com/marketplace//store" target="_blank">市场</a>和混合现实<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">论坛</a>中的资产和支持。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-117">Explore the Unreal <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">tutorial series</a> to get up to speed and look for assets and support in the Unreal <a href="https://www.unrealengine.com/marketplace//store" target="_blank">marketplace</a> and mixed reality <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">forums</a>.</span></span> <span data-ttu-id="9c1c8-118">这些资源是指向当今混合现实市场中的构建者和问题解决者的社区的链接。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-118">These resources are your links to the community of builders and problem solvers in todays mixed reality market.</span></span>

## <a name="mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="9c1c8-119">适用于 Unreal 的混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="9c1c8-119">Mixed Reality Toolkit for Unreal</span></span>

<span data-ttu-id="9c1c8-120">[适用于 Unreal 的混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unreal)是一组设计用于在 Unreal 中加快开发速度的组件。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-120">The [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) is a set of components designed to speed up your development in Unreal.</span></span> <span data-ttu-id="9c1c8-121">每个组件都包含用于设置沉浸式体验的插件、示例和文档。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-121">Each component includes plugins, samples, and documentation for setting up immersive experiences.</span></span> 

<span data-ttu-id="9c1c8-122">[适用于 Unreal 的 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) 是第一个要发布的组件，目前仅在 HoloLens 2 上受支持。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-122">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) is the first component to be released and is currently only supported on HoloLens 2.</span></span> <span data-ttu-id="9c1c8-123">组件插件包括常见 UX 功能的代码、蓝图和示例资产，包括：</span><span class="sxs-lookup"><span data-stu-id="9c1c8-123">The component plugin includes code, blueprints, and example assets of common UX features including:</span></span>
* <span data-ttu-id="9c1c8-124">输入模拟</span><span class="sxs-lookup"><span data-stu-id="9c1c8-124">Input simulation</span></span>
* <span data-ttu-id="9c1c8-125">手势交互 Actor</span><span class="sxs-lookup"><span data-stu-id="9c1c8-125">Hand interaction actor</span></span>
* <span data-ttu-id="9c1c8-126">可按按钮组件</span><span class="sxs-lookup"><span data-stu-id="9c1c8-126">Press-able button component</span></span>
* <span data-ttu-id="9c1c8-127">操控器组件</span><span class="sxs-lookup"><span data-stu-id="9c1c8-127">Manipulator component</span></span>
* <span data-ttu-id="9c1c8-128">跟踪行为组件</span><span class="sxs-lookup"><span data-stu-id="9c1c8-128">Follow behavior component</span></span>

<span data-ttu-id="9c1c8-129">有关功能的详细信息和设置项目的信息，可以深入了解[适用于 Unreal 的 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) GitHub 存储库。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-129">You can dive into the [UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) GitHub repository for feature details and information on setting up your project.</span></span>

## <a name="additional-files"></a><span data-ttu-id="9c1c8-130">其他文件</span><span class="sxs-lookup"><span data-stu-id="9c1c8-130">Additional files</span></span>
<span data-ttu-id="9c1c8-131">如果这是你第一次为 HoloLens 创建或部署 Unreal 应用，则需要从 Epic Launcher [下载支持文件](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app)。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-131">If this is your first time creating or deploying an Unreal app for HoloLens, you'll need to [download supporting files](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) from the Epic Launcher.</span></span>

## <a name="tutorial"></a><span data-ttu-id="9c1c8-132">教程</span><span class="sxs-lookup"><span data-stu-id="9c1c8-132">Tutorial</span></span>

<span data-ttu-id="9c1c8-133">亲自进行构建是学习新技能的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-133">Building something with your own two hands is the best way to learn a new skill.</span></span> <span data-ttu-id="9c1c8-134">了解如何为具有 UX Tools 插件的 HoloLens 2 [生成和部署简单的象棋应用](unreal-uxt-ch1.md)是一个良好的开端。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-134">Learning how to [build and deploy a simple chess app](unreal-uxt-ch1.md) for HoloLens 2 with the UX Tools plugin is a great way to start.</span></span> 

<span data-ttu-id="9c1c8-135">本端到端教程系列提供常见交互式 UX 组件和方案的动手实践。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-135">The end-to-end tutorial series provides hands-on contact with common interactive UX components and scenarios.</span></span> <span data-ttu-id="9c1c8-136">你将完成项目设置，即，将交互添加到场景，并部署到设备或模拟器。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-136">You'll work through the project setup, adding interactions to the scene, and deploying to a device or emulator.</span></span> <span data-ttu-id="9c1c8-137">只需 Windows 10、模拟器和 Visual Studio 2019 即可。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-137">All you need is Windows 10, an emulator, and Visual Studio 2019.</span></span>


## <a name="performance"></a><span data-ttu-id="9c1c8-138">性能</span><span class="sxs-lookup"><span data-stu-id="9c1c8-138">Performance</span></span>

<span data-ttu-id="9c1c8-139">混合现实开发附带依赖于平台的性能检查点。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-139">Developing for mixed reality comes with performance checkpoints that depend on the platform.</span></span> <span data-ttu-id="9c1c8-140">HoloLens 2 应用必须以每秒 60 帧的速度运行，才能使全息影像稳定显示且快速响应。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-140">A HoloLens 2 app must run at 60 frames per second for holograms to appear stable and responsive.</span></span> <span data-ttu-id="9c1c8-141">幸运的是，Unreal 提供了[性能建议](performance-recommendations-for-unreal.md)，以便在应用程序中实现这一点。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-141">Luckily, Unreal provides [performance recommendations](performance-recommendations-for-unreal.md) for achieving this in your applications.</span></span>

## <a name="guides-to-specific-features"></a><span data-ttu-id="9c1c8-142">特定功能指南</span><span class="sxs-lookup"><span data-stu-id="9c1c8-142">Guides to specific features</span></span>

<span data-ttu-id="9c1c8-143">有几项混合现实开发的重要功能在教程系列中未涉及。</span><span class="sxs-lookup"><span data-stu-id="9c1c8-143">There are several key features of mixed reality development that our tutorial series doesn't cover.</span></span> <span data-ttu-id="9c1c8-144">有关详细信息和实际运用，请参阅以下指南：</span><span class="sxs-lookup"><span data-stu-id="9c1c8-144">Check out the following guides for details and practical applications:</span></span> 
* [<span data-ttu-id="9c1c8-145">手部跟踪</span><span class="sxs-lookup"><span data-stu-id="9c1c8-145">Hand tracking</span></span>](unreal-hand-tracking.md)
* [<span data-ttu-id="9c1c8-146">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="9c1c8-146">Eye tracking</span></span>](unreal-gaze-input.md)
* [<span data-ttu-id="9c1c8-147">空间映射</span><span class="sxs-lookup"><span data-stu-id="9c1c8-147">Spatial mapping</span></span>](unreal-spatial-mapping.md)
* [<span data-ttu-id="9c1c8-148">空间定位点</span><span class="sxs-lookup"><span data-stu-id="9c1c8-148">Spatial anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="9c1c8-149">语音输入</span><span class="sxs-lookup"><span data-stu-id="9c1c8-149">Voice input</span></span>](unreal-voice-input.md)
* [<span data-ttu-id="9c1c8-150">HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="9c1c8-150">HoloLens camera</span></span>](unreal-hololens-camera.md)
* [<span data-ttu-id="9c1c8-151">QR 码</span><span class="sxs-lookup"><span data-stu-id="9c1c8-151">QR codes</span></span>](unreal-qr-codes.md)


## <a name="supported-features"></a><span data-ttu-id="9c1c8-152">支持的功能</span><span class="sxs-lookup"><span data-stu-id="9c1c8-152">Supported Features</span></span>

| <span data-ttu-id="9c1c8-153">HoloLens 2 功能</span><span class="sxs-lookup"><span data-stu-id="9c1c8-153">HoloLens 2 Feature</span></span> | <span data-ttu-id="9c1c8-154">最早支持的 Unreal Engine 版本</span><span class="sxs-lookup"><span data-stu-id="9c1c8-154">Earliest Supported Unreal Engine Version</span></span> |
| ----------- | ----------- |
| <span data-ttu-id="9c1c8-155">ARM64 支持</span><span class="sxs-lookup"><span data-stu-id="9c1c8-155">ARM64 support</span></span> | <span data-ttu-id="9c1c8-156">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-156">4.23</span></span> |
| <span data-ttu-id="9c1c8-157">从电脑进行流式传输</span><span class="sxs-lookup"><span data-stu-id="9c1c8-157">Streaming from a PC</span></span> | <span data-ttu-id="9c1c8-158">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-158">4.23</span></span> |
| <span data-ttu-id="9c1c8-159">空间映射</span><span class="sxs-lookup"><span data-stu-id="9c1c8-159">Spatial mapping</span></span> | <span data-ttu-id="9c1c8-160">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-160">4.23</span></span> |
| <span data-ttu-id="9c1c8-161">手动和联合跟踪</span><span class="sxs-lookup"><span data-stu-id="9c1c8-161">Hand and joint tracking</span></span> | <span data-ttu-id="9c1c8-162">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-162">4.23</span></span> |
| <span data-ttu-id="9c1c8-163">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="9c1c8-163">Eye tracking</span></span> | <span data-ttu-id="9c1c8-164">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-164">4.23</span></span> |
| <span data-ttu-id="9c1c8-165">语音输入</span><span class="sxs-lookup"><span data-stu-id="9c1c8-165">Voice input</span></span> | <span data-ttu-id="9c1c8-166">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-166">4.23</span></span> |
| <span data-ttu-id="9c1c8-167">空间定位点</span><span class="sxs-lookup"><span data-stu-id="9c1c8-167">Spatial anchors</span></span> | <span data-ttu-id="9c1c8-168">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-168">4.23</span></span> |
| <span data-ttu-id="9c1c8-169">摄像头访问</span><span class="sxs-lookup"><span data-stu-id="9c1c8-169">Camera access</span></span> | <span data-ttu-id="9c1c8-170">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-170">4.23</span></span> |
| <span data-ttu-id="9c1c8-171">QR 码</span><span class="sxs-lookup"><span data-stu-id="9c1c8-171">QR codes</span></span> | <span data-ttu-id="9c1c8-172">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-172">4.23</span></span> |
| <span data-ttu-id="9c1c8-173">空间音频</span><span class="sxs-lookup"><span data-stu-id="9c1c8-173">Spatial audio</span></span> | <span data-ttu-id="9c1c8-174">4.23</span><span class="sxs-lookup"><span data-stu-id="9c1c8-174">4.23</span></span> |
| <span data-ttu-id="9c1c8-175">Spectator Screen 支持流式传输</span><span class="sxs-lookup"><span data-stu-id="9c1c8-175">Spectator Screen support for streaming</span></span> | <span data-ttu-id="9c1c8-176">4.24</span><span class="sxs-lookup"><span data-stu-id="9c1c8-176">4.24</span></span> |
| <span data-ttu-id="9c1c8-177">通过流式传输的平面 LSR</span><span class="sxs-lookup"><span data-stu-id="9c1c8-177">Planar LSR over streaming</span></span> | <span data-ttu-id="9c1c8-178">4.24</span><span class="sxs-lookup"><span data-stu-id="9c1c8-178">4.24</span></span> |
| <span data-ttu-id="9c1c8-179">示例应用（[HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) 和[任务 AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html)）</span><span class="sxs-lookup"><span data-stu-id="9c1c8-179">Sample apps ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) and [Mission AR](https://docs.unrealengine.com/en-US/Resources/Showcases/MissionAR/index.html))</span></span> | <span data-ttu-id="9c1c8-180">4.24</span><span class="sxs-lookup"><span data-stu-id="9c1c8-180">4.24</span></span> |
| <span data-ttu-id="9c1c8-181">移动多视图：性能达到 60 fps</span><span class="sxs-lookup"><span data-stu-id="9c1c8-181">Mobile multi-View: Performance hits 60 fps</span></span> | <span data-ttu-id="9c1c8-182">4.25</span><span class="sxs-lookup"><span data-stu-id="9c1c8-182">4.25</span></span> |
| <span data-ttu-id="9c1c8-183">第三人称摄像机渲染</span><span class="sxs-lookup"><span data-stu-id="9c1c8-183">3rd camera render</span></span> | <span data-ttu-id="9c1c8-184">4.25</span><span class="sxs-lookup"><span data-stu-id="9c1c8-184">4.25</span></span> |
| <span data-ttu-id="9c1c8-185">从打包的桌面应用进行流式传输</span><span class="sxs-lookup"><span data-stu-id="9c1c8-185">Streaming from a packaged desktop app</span></span> | <span data-ttu-id="9c1c8-186">4.25</span><span class="sxs-lookup"><span data-stu-id="9c1c8-186">4.25</span></span> |
| <span data-ttu-id="9c1c8-187">面向 HoloLens 2 的 Azure 空间定位点 (beta)</span><span class="sxs-lookup"><span data-stu-id="9c1c8-187">Azure Spatial Anchors for HoloLens 2 (beta)</span></span> | <span data-ttu-id="9c1c8-188">4.25</span><span class="sxs-lookup"><span data-stu-id="9c1c8-188">4.25</span></span> |
| <span data-ttu-id="9c1c8-189">OpenXR 支持 (beta)</span><span class="sxs-lookup"><span data-stu-id="9c1c8-189">OpenXR support (beta)</span></span> | <span data-ttu-id="9c1c8-190">4.25</span><span class="sxs-lookup"><span data-stu-id="9c1c8-190">4.25</span></span> |
| <span data-ttu-id="9c1c8-191">UX Tools 支持 (0.8)</span><span class="sxs-lookup"><span data-stu-id="9c1c8-191">UX Tools support (0.8)</span></span> | <span data-ttu-id="9c1c8-192">4.25</span><span class="sxs-lookup"><span data-stu-id="9c1c8-192">4.25</span></span> |
| <span data-ttu-id="9c1c8-193">开发人员文档和教程</span><span class="sxs-lookup"><span data-stu-id="9c1c8-193">Developer docs & tutorials</span></span> | <span data-ttu-id="9c1c8-194">4.25</span><span class="sxs-lookup"><span data-stu-id="9c1c8-194">4.25</span></span> |

## <a name="see-also"></a><span data-ttu-id="9c1c8-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9c1c8-195">See also</span></span>
* <span data-ttu-id="9c1c8-196"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">关于流式传输、部署到仿真器和设备的 Unreal 文档</a></span><span class="sxs-lookup"><span data-stu-id="9c1c8-196"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Unreal docs for streaming, deploying to emulator and device</a></span></span>
* <span data-ttu-id="9c1c8-197"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">移动设备的 Unreal 性能指南</a></span><span class="sxs-lookup"><span data-stu-id="9c1c8-197"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a></span></span>
