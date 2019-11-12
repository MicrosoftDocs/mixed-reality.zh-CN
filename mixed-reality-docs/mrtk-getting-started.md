---
title: MRTK 版本2入门
description: 对于对利用 MRTK 感兴趣的新开发人员
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
keywords: Windows Mixed Reality，测试，混合现实工具包，MRTK 版本2，MRTK，工具，SDK，HoloLens，HoloLens 2
ms.openlocfilehash: bb958543aa68586dd689a2048665b233d6be7064
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913136"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="84e46-104">MRTK v2 入门</span><span class="sxs-lookup"><span data-stu-id="84e46-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="84e46-105">MRTK 入门指南</span><span class="sxs-lookup"><span data-stu-id="84e46-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="84e46-106">有关 MRTK V2 入门的详细信息，请参阅[MRTK 入门指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)。</span><span class="sxs-lookup"><span data-stu-id="84e46-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for detailed information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="84e46-107">什么是混合现实工具包（MRTK）？</span><span class="sxs-lookup"><span data-stu-id="84e46-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="84e46-108">MRTK 是一种令人惊叹的开源工具包，它是自2015首次发布后开始的，并不是我们的开发人员社区的硬性工作，而是目前为止。</span><span class="sxs-lookup"><span data-stu-id="84e46-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="84e46-109">过去3年来，我们已听取开发人员社区的反馈，并构建了 MRTK v2，以考虑最大的问题。</span><span class="sxs-lookup"><span data-stu-id="84e46-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="84e46-110">适用于 Unity 的 MRTK v2 是一个面向混合现实应用程序的开源跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="84e46-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="84e46-111">MRTK 版本 2 旨在加快面向 Microsoft HoloLens、Windows Mixed Reality 沉浸式 (VR) 头戴显示设备和 OpenVR 平台的应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="84e46-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="84e46-112">该项目的目的是为了减少进入障碍，创建混合现实应用程序，并在我们的所有增长时向社区提供反馈。</span><span class="sxs-lookup"><span data-stu-id="84e46-112">The project is aimed at reducing barriers to entry, to create mixed reality applications and contribute back to the community as we all grow.</span></span> 

<span data-ttu-id="84e46-113">有关详细信息，请参阅[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)。</span><span class="sxs-lookup"><span data-stu-id="84e46-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="84e46-114">新的 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="84e46-114">New with MRTK v2</span></span>
<span data-ttu-id="84e46-115">我们想要对这些平台工具的承诺施加压力。</span><span class="sxs-lookup"><span data-stu-id="84e46-115">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="84e46-116">事实上，我们利用 MRTK 版本2来开发收件箱体验，例如安装体验（OOBE）和混合现实学习应用程序。</span><span class="sxs-lookup"><span data-stu-id="84e46-116">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="84e46-117">你还可以看到新的 HoloLens 2 功能首次通过 MRTK 公开，因为我们认为这是在我们的平台上进行开发的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="84e46-117">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="84e46-118">模块化</span><span class="sxs-lookup"><span data-stu-id="84e46-118">Modular</span></span>
<span data-ttu-id="84e46-119">我们采用模块化方式构建了它，因此，无需将工具包的每个套件都引入项目。</span><span class="sxs-lookup"><span data-stu-id="84e46-119">We have built it in a modular way, so there's no need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="84e46-120">这样做实际上只有几个优点。</span><span class="sxs-lookup"><span data-stu-id="84e46-120">There are actually a few benefits to this.</span></span>  <span data-ttu-id="84e46-121">它可以使项目大小保持较小，并使其更易于管理。</span><span class="sxs-lookup"><span data-stu-id="84e46-121">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="84e46-122">此外，由于它是用可编写脚本的对象构建的，并且是由接口驱动的，因此您还可以替换您自己所附带的组件以支持其他服务、系统和平台。</span><span class="sxs-lookup"><span data-stu-id="84e46-122">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="84e46-123">跨平台</span><span class="sxs-lookup"><span data-stu-id="84e46-123">Cross-platform</span></span>
<span data-ttu-id="84e46-124">说到其他平台，它具有跨平台支持。</span><span class="sxs-lookup"><span data-stu-id="84e46-124">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="84e46-125">虽然这并不意味着每个平台都受支持，但我们确保在将生成目标切换到其他平台时，不会中断任何工具包代码。</span><span class="sxs-lookup"><span data-stu-id="84e46-125">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="84e46-126">模块化设计的可靠性和扩展性使你能够支持多个平台，如 ARCore、ARKit 和 OpenVR。</span><span class="sxs-lookup"><span data-stu-id="84e46-126">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="84e46-127">高性能</span><span class="sxs-lookup"><span data-stu-id="84e46-127">Performant</span></span>
<span data-ttu-id="84e46-128">使用移动平台时，我们构建了性能方面的考虑因素。</span><span class="sxs-lookup"><span data-stu-id="84e46-128">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="84e46-129">这非常重要，我们想要确保这些工具不会与你一起工作。</span><span class="sxs-lookup"><span data-stu-id="84e46-129">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="84e46-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84e46-130">See also</span></span>
* [<span data-ttu-id="84e46-131">MRTK 入门指南</span><span class="sxs-lookup"><span data-stu-id="84e46-131">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="84e46-132">MRTK 文档主页</span><span class="sxs-lookup"><span data-stu-id="84e46-132">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="84e46-133">安装工具</span><span class="sxs-lookup"><span data-stu-id="84e46-133">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="84e46-134">从 HTK/MRTK 迁移到 MRTK 版本2</span><span class="sxs-lookup"><span data-stu-id="84e46-134">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
