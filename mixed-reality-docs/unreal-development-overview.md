---
title: Unreal 开发概述
description: 在 Unreal 中构建混合现实应用入门。
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, 流式传输, 远程处理, 混合现实, 开发, 入门, 新项目, 仿真器, 文档
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491169"
---
# <a name="unreal-development-overview"></a><span data-ttu-id="520fb-104">Unreal 开发概述</span><span class="sxs-lookup"><span data-stu-id="520fb-104">Unreal development overview</span></span>

<span data-ttu-id="520fb-105">对 Unreal Engine 4 的混合现实支持现在为 Beta 版！</span><span class="sxs-lookup"><span data-stu-id="520fb-105">Mixed reality support for Unreal Engine 4 is now in beta!</span></span> <span data-ttu-id="520fb-106">如果不熟悉 Unreal 开发，不妨浏览一下 <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Unreal Engine 4 入门</a>页面。</span><span class="sxs-lookup"><span data-stu-id="520fb-106">If you're new to Unreal development, <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Getting Started with Unreal Engine 4</a> is a great page to explore.</span></span> <span data-ttu-id="520fb-107">如果你需要资产，Unreal 有一个包罗万象的<a href="https://www.unrealengine.com/marketplace//store" target="_blank">市场</a>。</span><span class="sxs-lookup"><span data-stu-id="520fb-107">If you need assets, Unreal has a comprehensive <a href="https://www.unrealengine.com/marketplace//store" target="_blank">Marketplace</a>.</span></span> 

<span data-ttu-id="520fb-108">有了对 Unreal Engine 4 的基本了解以后，即可访问 Unreal Engine 文档站点上的 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens 开发</a>页面，了解如果构建应用并在 HoloLens 上运行它们。</span><span class="sxs-lookup"><span data-stu-id="520fb-108">Once you've built a basic understanding of Unreal Engine 4, you can visit the <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens Development</a> page on the Unreal Engine documentation site to learn how to build and run your apps on HoloLens.</span></span> <span data-ttu-id="520fb-109">若要与在 Unreal 中构建混合现实应用的社区人员交流心得，请务必访问 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 混合现实论坛</a>。</span><span class="sxs-lookup"><span data-stu-id="520fb-109">Be sure to visit the <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal Mixed Reality forums</a> to engage with the community who build mixed reality apps in Unreal.</span></span> <span data-ttu-id="520fb-110">可以在那里查找可能会遇到的问题的解决方案。</span><span class="sxs-lookup"><span data-stu-id="520fb-110">It's a great place to find solutions to problems you might run into.</span></span>

## <a name="installing-the-prerequisites"></a><span data-ttu-id="520fb-111">安装必备组件</span><span class="sxs-lookup"><span data-stu-id="520fb-111">Installing the prerequisites</span></span>

<span data-ttu-id="520fb-112">若要开始在 Unreal 中构建 HoloLens 2 应用，需要 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或 HoloLens 头戴显示设备。</span><span class="sxs-lookup"><span data-stu-id="520fb-112">To get started with building a HoloLens 2 app in Unreal, you'll need the [HoloLens 2 Emulator](using-the-hololens-emulator.md) or a HoloLens headset.</span></span> <span data-ttu-id="520fb-113">还需安装最新版 Visual Studio，其工作负荷和组件列在 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">Unreal 的 HoloLens 2 必备组件</a>中。</span><span class="sxs-lookup"><span data-stu-id="520fb-113">You'll also need to install the latest version of Visual Studio with the workloads and components listed in <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">HoloLens 2 Prerequisites for Unreal</a>.</span></span>

## <a name="building-and-running-your-unreal-app"></a><span data-ttu-id="520fb-114">构建并运行 Unreal 应用</span><span class="sxs-lookup"><span data-stu-id="520fb-114">Building and running your Unreal app</span></span>

<span data-ttu-id="520fb-115">首先，<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">将 HoloLens 2 应用打包</a>。</span><span class="sxs-lookup"><span data-stu-id="520fb-115">First, <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">package your app for HoloLens 2</a>.</span></span> <span data-ttu-id="520fb-116">接下来，选择要将包部署到的位置：</span><span class="sxs-lookup"><span data-stu-id="520fb-116">Next, choose where you want to deploy your package:</span></span>
* <span data-ttu-id="520fb-117"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">部署到 HoloLens 2 仿真器</a></span><span class="sxs-lookup"><span data-stu-id="520fb-117"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">Deploy to the HoloLens 2 Emulator</a></span></span>
* <span data-ttu-id="520fb-118"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">部署到 HoloLens 2 头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="520fb-118"><a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">Deploy to a HoloLens 2 Headset</a></span></span>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a><span data-ttu-id="520fb-119">通过全息远程处理播放器将应用流式传输到头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="520fb-119">Streaming your app to a headset via the Holographic Remoting Player</span></span>

<span data-ttu-id="520fb-120">将应用从桌面设备流式传输到 HoloLens 头戴显示设备上的全息远程处理播放器应用有两大好处：</span><span class="sxs-lookup"><span data-stu-id="520fb-120">Streaming your app from your desktop to the Holographic Remoting Player app on a HoloLens headset has two main advantages:</span></span> 
* <span data-ttu-id="520fb-121">加快开发速度，这样就不需每次进行更改时都将应用重新打包并上传</span><span class="sxs-lookup"><span data-stu-id="520fb-121">Speeds up development, so there's no need to repackage and upload your app each time you make a change</span></span>
* <span data-ttu-id="520fb-122">充分利用桌面设备的功能，这样你就可以渲染尽可能多的多边形（只要桌面设备的 GPU 允许），不受头戴显示设备上提供的计算机的限制</span><span class="sxs-lookup"><span data-stu-id="520fb-122">Leverages the power of your desktop, so you can render as many polygons as your desktop GPU allows, without being limited by the computer available on the headset</span></span>

<span data-ttu-id="520fb-123">若要开始流式传输，请参阅 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 流送快速入门</a>[]()。</span><span class="sxs-lookup"><span data-stu-id="520fb-123">To get started with streaming, check out the <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 Streaming Quick Start</a>[]().</span></span>

## <a name="see-also"></a><span data-ttu-id="520fb-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="520fb-124">See also</span></span>
* <span data-ttu-id="520fb-125"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">移动设备的 Unreal 性能指南</a></span><span class="sxs-lookup"><span data-stu-id="520fb-125"><a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a></span></span>
