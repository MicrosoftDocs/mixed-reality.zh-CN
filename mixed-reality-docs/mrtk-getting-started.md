---
title: 开始使用 MRTK 版本 2
description: 新开发人员感兴趣利用 MRTK
author: grbury
ms.author: grbury
ms.date: 02/22/19
ms.topic: article
keywords: Windows Mixed Reality，测试、 MRTK 版本 2，MRTK，工具、 SDK、 HoloLens、 HoloLens 2
ms.openlocfilehash: 44e5fe0fd4384af68922eda4bcb0594d39a1c1b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591825"
---
# <a name="getting-started-with-mrtk-version-2"></a><span data-ttu-id="6808e-104">开始使用 MRTK 版本 2</span><span class="sxs-lookup"><span data-stu-id="6808e-104">Getting started with MRTK version 2</span></span>

<span data-ttu-id="6808e-105">MRTK 是令人惊叹的开放源代码工具包，以来已经过围绕 HoloLens 首次发布，并且不会目前的状况而无需我们的开发人员社区向其提供了大量工作。</span><span class="sxs-lookup"><span data-stu-id="6808e-105">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="6808e-106">在过去 3 年中，我们有侦听到我们的开发人员社区的反馈，并生成 MRTK 版本 2 要着重考虑的最大的问题。</span><span class="sxs-lookup"><span data-stu-id="6808e-106">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK version 2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="6808e-107">使用 Unity 的版本 2 MRTK 是混合的现实应用程序的一个开放源代码跨平台开发工具包。</span><span class="sxs-lookup"><span data-stu-id="6808e-107">The MRTK version 2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="6808e-108">MRTK 版本 2 旨在加速开发针对 Microsoft HoloLens，Windows Mixed Reality 沉浸式 (VR) 耳机，以及 OpenVR 平台的应用程序。</span><span class="sxs-lookup"><span data-stu-id="6808e-108">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="6808e-109">项目功能旨在减少到条目创建混合的现实应用程序并提供回社区，随着我们所有的发展的障碍。</span><span class="sxs-lookup"><span data-stu-id="6808e-109">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="6808e-110">请参阅<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK 版本 2 wiki</a>来开始，了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="6808e-110">See the <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK version 2 wiki</a> to get started and learn more.</span></span>

## <a name="new-with-mrtk-version-2"></a><span data-ttu-id="6808e-111">新功能 MRTK 版本 2</span><span class="sxs-lookup"><span data-stu-id="6808e-111">New with MRTK version 2</span></span>
<span data-ttu-id="6808e-112">我们想要强调我们对这些平台工具的承诺。</span><span class="sxs-lookup"><span data-stu-id="6808e-112">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="6808e-113">事实上，我们就利用了 MRTK 版本 2 开发我们收件箱的体验，例如安装体验 (OOBE) 和混合现实学习应用程序。</span><span class="sxs-lookup"><span data-stu-id="6808e-113">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="6808e-114">则可能要查看新 HoloLens 2 功能通过 MRTK 首次公开，因为我们认为它是在我们的平台上进行开发的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="6808e-114">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="6808e-115">采用模块化结构</span><span class="sxs-lookup"><span data-stu-id="6808e-115">Modular</span></span>
<span data-ttu-id="6808e-116">以便不需要考虑该工具包的每一位到你的项目，我们有模块化方式，构建它。</span><span class="sxs-lookup"><span data-stu-id="6808e-116">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="6808e-117">有此实际几个优点。</span><span class="sxs-lookup"><span data-stu-id="6808e-117">There are actually a few benefits to this.</span></span>  <span data-ttu-id="6808e-118">它使您的项目规模较小，以及轻松地管理。</span><span class="sxs-lookup"><span data-stu-id="6808e-118">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="6808e-119">除此之外，因为它用可编写脚本的对象生成，并且驱动的界面，它还有可能更换附带你自己，以支持其他服务、 系统和平台的组件。</span><span class="sxs-lookup"><span data-stu-id="6808e-119">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="6808e-120">跨平台</span><span class="sxs-lookup"><span data-stu-id="6808e-120">Cross-platform</span></span>
<span data-ttu-id="6808e-121">说到其他平台，它提供了跨平台支持。</span><span class="sxs-lookup"><span data-stu-id="6808e-121">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="6808e-122">而这并不意味着每个单个平台支持的功能，我们已确保的工具包代码都不会中断生成目标切换到其他平台时。</span><span class="sxs-lookup"><span data-stu-id="6808e-122">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="6808e-123">可靠性和可扩展性的模块化设计设置您上能够支持多个平台，例如 ARCore、 ARKit，以及 OpenVR 的好方法。</span><span class="sxs-lookup"><span data-stu-id="6808e-123">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="6808e-124">高性能</span><span class="sxs-lookup"><span data-stu-id="6808e-124">Performant</span></span>
<span data-ttu-id="6808e-125">我们在使用的移动平台，构造它与性能方面的考虑。</span><span class="sxs-lookup"><span data-stu-id="6808e-125">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="6808e-126">这是非常重要，我们想要确保这些工具不会对您工作。</span><span class="sxs-lookup"><span data-stu-id="6808e-126">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="6808e-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="6808e-127">See also</span></span>
* [<span data-ttu-id="6808e-128">安装工具</span><span class="sxs-lookup"><span data-stu-id="6808e-128">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="6808e-129">从 HTK/MRTK 移植到 MRTK 版本 2</span><span class="sxs-lookup"><span data-stu-id="6808e-129">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
