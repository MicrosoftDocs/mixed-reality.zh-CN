---
title: 多模式交互概述
description: 多模式交互的概述
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实、 提供注视、 视线移动目标交互，设计、 hololens，MMR，multimodal
ms.openlocfilehash: 9d0e639d7474c7e8728282acfa8d288cfeec7043
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974908"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="73720-104">引入 instinctual 交互</span><span class="sxs-lookup"><span data-stu-id="73720-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="73720-105">简单、 instinctual 交互的基本原理是整个 Microsoft 混合现实 (MMR) 平台，从硬件到软件织物。</span><span class="sxs-lookup"><span data-stu-id="73720-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality (MMR) platform, from hardware to software.</span></span>

<span data-ttu-id="73720-106">这些 instinctual 交互利用所有可用的输入的技术，包括无缝多模式交互模型中的内而外跟踪、 跟踪的手、 眼睛追踪和自然语言。</span><span class="sxs-lookup"><span data-stu-id="73720-106">These instinctual interactions utilize all available input technologies, including inside-out tracking, hand tracking, eye tracking, and natural language, in seamless multimodal interaction models.</span></span> <span data-ttu-id="73720-107">根据我们的研究，设计和开发 multimodals，并且不基于单个输入至关重要时创建本能的体验。</span><span class="sxs-lookup"><span data-stu-id="73720-107">Based on our research, designing and developing multimodals, and not based on single inputs, is critical when creating instinctive experiences.</span></span>

<span data-ttu-id="73720-108">跨设备类型还很自然地对齐 Instinctual 交互模型。</span><span class="sxs-lookup"><span data-stu-id="73720-108">The Instinctual Interaction models also naturally align across device types.</span></span>  <span data-ttu-id="73720-109">例如，为 6 的自由 (DoF) 控制器在沉浸式头戴式远端交互和 HoloLens 2 上的远端交互使用相同的提示、 模式和行为。</span><span class="sxs-lookup"><span data-stu-id="73720-109">For example, far interaction on an immersive headset with a 6 degrees of freedom (DoF) controller and far interaction on a HoloLens 2 use the same affordances, patterns, and behaviors.</span></span>  <span data-ttu-id="73720-110">不只是这方便，为开发人员和设计器中，但它感觉自然向最终用户。</span><span class="sxs-lookup"><span data-stu-id="73720-110">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span>


<span data-ttu-id="73720-111">最后，虽然我们已经认识到，有数千个有效、 富有吸引力神奇的交互可能 MR 中，我们已找到该有意采用单个交互模型中端到端应用程序就是确保用户是成功的最佳方法和获得完美的体验。</span><span class="sxs-lookup"><span data-stu-id="73720-111">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="73720-112">为此，我们提供了此交互指南中的三个操作：</span><span class="sxs-lookup"><span data-stu-id="73720-112">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="73720-113">我们已结构化围绕三个主要交互模型的组件和模式所需的每个本指南</span><span class="sxs-lookup"><span data-stu-id="73720-113">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="73720-114">我们提供了我们平台提供了其他权益的补充指南</span><span class="sxs-lookup"><span data-stu-id="73720-114">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="73720-115">我们提供了指导，以帮助选择适合您的方案的相应交互模型</span><span class="sxs-lookup"><span data-stu-id="73720-115">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="73720-116">多模式交互模型</span><span class="sxs-lookup"><span data-stu-id="73720-116">Multimodal interaction models</span></span>

<span data-ttu-id="73720-117">根据我们的研究和使用日期的客户，我们已发现满足大多数混合现实体验的三个主要交互模型。</span><span class="sxs-lookup"><span data-stu-id="73720-117">Based on our research and work with customers to date, we've discovered three primary interaction models that suit the majority of Mixed Reality experiences.</span></span>  

<span data-ttu-id="73720-118">这些交互模型视为完成他们的流的用户的思维模式。</span><span class="sxs-lookup"><span data-stu-id="73720-118">Think of these interaction models as the user's mental model for completing their flows.</span></span>

<span data-ttu-id="73720-119">每个这些交互模型是方便、 强大且可在自己的权限中使用，所有客户需求的一组针对进行了优化。</span><span class="sxs-lookup"><span data-stu-id="73720-119">Each of these interaction models is convenient, powerful, and usable in its own right, and all are optimized for a set of customer needs.</span></span> <span data-ttu-id="73720-120">查看图表下方、 方案、 示例和每个交互模型的好处的。</span><span class="sxs-lookup"><span data-stu-id="73720-120">View the chart below, for scenarios, examples, and benefits of each interaction model.</span></span>  

<span data-ttu-id="73720-121">**Model**</span><span class="sxs-lookup"><span data-stu-id="73720-121">**Model**</span></span> | <span data-ttu-id="73720-122">**[双手和工具](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)**</span><span class="sxs-lookup"><span data-stu-id="73720-122">**[Hands and Tools](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-and-tools)**</span></span> | <span data-ttu-id="73720-123">**[免提](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)**</span><span class="sxs-lookup"><span data-stu-id="73720-123">**[Hands free](https://docs.microsoft.com/en-us/windows/mixed-reality/hands-free)**</span></span> | <span data-ttu-id="73720-124">**[视线移动和提交](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**</span><span class="sxs-lookup"><span data-stu-id="73720-124">**[Gaze and Commit](https://docs.microsoft.com/en-us/windows/mixed-reality/gaze-and-commit?)**</span></span>
|--------- | --------------| ------------| ---------|
<span data-ttu-id="73720-125">**示例方案**</span><span class="sxs-lookup"><span data-stu-id="73720-125">**Example Scenarios**</span></span> | <span data-ttu-id="73720-126">3D 空间的体验，例如空间布局和设计，内容操作或模拟</span><span class="sxs-lookup"><span data-stu-id="73720-126">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation</span></span> | <span data-ttu-id="73720-127">上下文体验，其中用户的手都被占用，例如学习，维护作业</span><span class="sxs-lookup"><span data-stu-id="73720-127">Contextual experiences where a user's hands are occupied, e.g. on the-job learning, maintenance</span></span>| <span data-ttu-id="73720-128">点击体验，例如 3D 演示文稿、 演示材料</span><span class="sxs-lookup"><span data-stu-id="73720-128">Click-through experiences, e.g. 3D presentations, demos</span></span>
<span data-ttu-id="73720-129">**合适大小**</span><span class="sxs-lookup"><span data-stu-id="73720-129">**Fit**</span></span> | <span data-ttu-id="73720-130">非常适用于新用户，耦合的 wit 语音眼睛跟踪或头的视线移动。</span><span class="sxs-lookup"><span data-stu-id="73720-130">Great for new users, coupled wit voice, eye tracking or head gaze.</span></span> <span data-ttu-id="73720-131">低学习曲线。</span><span class="sxs-lookup"><span data-stu-id="73720-131">Low learning curve.</span></span> <span data-ttu-id="73720-132">在手动跟踪和 6 DoF 控制器之间的一致用户体验。</span><span class="sxs-lookup"><span data-stu-id="73720-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span> | <span data-ttu-id="73720-133">一些学习所需。</span><span class="sxs-lookup"><span data-stu-id="73720-133">Some learning required.</span></span> <span data-ttu-id="73720-134">如果为对也不可用语音和自然语言</span><span class="sxs-lookup"><span data-stu-id="73720-134">If hands are unavailable pairs well with voice and natural language</span></span> | <span data-ttu-id="73720-135">需要培训 HMDs 上但不是移动设备上。</span><span class="sxs-lookup"><span data-stu-id="73720-135">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="73720-136">最佳的可访问控制器最适合 HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="73720-136">Best for accessible controllers Best for HoloLens (1st gen)</span></span> |
<span data-ttu-id="73720-137">**硬件**</span><span class="sxs-lookup"><span data-stu-id="73720-137">**Hardware**</span></span> | <span data-ttu-id="73720-138">HoloLens 2 沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="73720-138">HoloLens 2 Immersive headsets</span></span> | <span data-ttu-id="73720-139">HoloLens 2 HoloLens （第 1 代） 沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="73720-139">HoloLens 2 HoloLens (1st gen) Immersive headsets</span></span> | <span data-ttu-id="73720-140">HoloLens 2 沉浸式耳机</span><span class="sxs-lookup"><span data-stu-id="73720-140">HoloLens 2 Immersive headsets</span></span> | <span data-ttu-id="73720-141">HoloLens 2 HoloLens （第 1 代） 沉浸式耳机移动 AR</span><span class="sxs-lookup"><span data-stu-id="73720-141">HoloLens 2 HoloLens (1st gen) Immersive headsets Mobile AR</span></span> |

<span data-ttu-id="73720-142">在每个交互模型中无缝地配合使用所有可用输入的详细的信息是按照图例和从我们 Unity MRTK 示例内容的链接以及页面上。</span><span class="sxs-lookup"><span data-stu-id="73720-142">Detailed information for using all available inputs seamlessly together in each interaction model is on the pages that follow, as well as illustrations and links to sample content from our Unity MRTK.</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="73720-143">选择为您的客户交互模型</span><span class="sxs-lookup"><span data-stu-id="73720-143">Choose an interaction model for your customer</span></span>


<span data-ttu-id="73720-144">很可能，开发人员和创建者也已有的一些观点记住他们想要其用户的交互体验种类。</span><span class="sxs-lookup"><span data-stu-id="73720-144">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="73720-145">鼓励客户为中心的方法来设计，我们建议遵循以下指南来选择适合您的客户的交互模型。</span><span class="sxs-lookup"><span data-stu-id="73720-145">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="73720-146">为什么要遵循以下指南？</span><span class="sxs-lookup"><span data-stu-id="73720-146">Why follow this guidance?</span></span>

* <span data-ttu-id="73720-147">测试我们的交互模型为目标和物理和认知工作量、 intuitiveness 和 learnability 等的主观标准。</span><span class="sxs-lookup"><span data-stu-id="73720-147">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="73720-148">因为交互不同，视频和音频提示和对象行为可能之间的交互模型也不同。</span><span class="sxs-lookup"><span data-stu-id="73720-148">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="73720-149">组合在一起的多个交互模型部分会竞争等，如同时进行手动大气和 head 视线移动游标，这会倾覆并使用户感到困惑的风险。</span><span class="sxs-lookup"><span data-stu-id="73720-149">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="73720-150">下面是针对每个交互模型提供和行为进行了优化的一些示例。</span><span class="sxs-lookup"><span data-stu-id="73720-150">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="73720-151">我们通常看到新的用户类似的问题，如"如何知道系统工作，如何知道我可以做什么，以及如何知道是否理解刚才的操作？"</span><span class="sxs-lookup"><span data-stu-id="73720-151">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="73720-152"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="73720-152"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="73720-153"><strong>如何知道是否正常工作？</strong></span><span class="sxs-lookup"><span data-stu-id="73720-153"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="73720-154"><strong>如何知道我可以做什么？</strong></span><span class="sxs-lookup"><span data-stu-id="73720-154"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="73720-155"><strong>如何知道刚才的操作？</strong></span><span class="sxs-lookup"><span data-stu-id="73720-155"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="73720-156"><a href="hands-and-tools.md">双手和工具</a></span><span class="sxs-lookup"><span data-stu-id="73720-156"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="73720-157">我看到 mesh 手的形状，我看到指尖功能可见性： 或手动 / 控制器光线。</span><span class="sxs-lookup"><span data-stu-id="73720-157">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="73720-158">我看到 grabbable 句柄或即将达到我的手时，将显示边界框。</span><span class="sxs-lookup"><span data-stu-id="73720-158">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="73720-159">我听到声音声音，并在随取即行和发布到动画。</span><span class="sxs-lookup"><span data-stu-id="73720-159">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="73720-160"><a href="gaze-and-commit.md">头部凝视并提交</a></span><span class="sxs-lookup"><span data-stu-id="73720-160"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="73720-161">我看到我的视野中心中的游标。</span><span class="sxs-lookup"><span data-stu-id="73720-161">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="73720-162">Head 视线移动游标时对特定对象的状态更改。</span><span class="sxs-lookup"><span data-stu-id="73720-162">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="73720-163">我看到/听到视频和音频确认时我采取措施。</span><span class="sxs-lookup"><span data-stu-id="73720-163">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="73720-164"><a href="hands-free.md">无 （Head 注视和停留）</a></span><span class="sxs-lookup"><span data-stu-id="73720-164"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="73720-165">我看到我的视野中心中的游标。</span><span class="sxs-lookup"><span data-stu-id="73720-165">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="73720-166">当我在此再次详述种交互的对象时，我看到一个进度指示器。</span><span class="sxs-lookup"><span data-stu-id="73720-166">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="73720-167">我看到/听到视频和音频确认时我采取措施。</span><span class="sxs-lookup"><span data-stu-id="73720-167">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="73720-168"><a href="hands-free.md">无 （语音命令）</a></span><span class="sxs-lookup"><span data-stu-id="73720-168"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="73720-169">我看到一个侦听的指示符和显示系统听到的隐藏式字幕。</span><span class="sxs-lookup"><span data-stu-id="73720-169">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="73720-170">获取语音提示和提示。</span><span class="sxs-lookup"><span data-stu-id="73720-170">I get voice prompts and hints.</span></span>  <span data-ttu-id="73720-171">当我说"我可以说什么？"</span><span class="sxs-lookup"><span data-stu-id="73720-171">When I say "what can I say?"</span></span> <span data-ttu-id="73720-172">我看到的反馈。</span><span class="sxs-lookup"><span data-stu-id="73720-172">I see feedback.</span></span></td>
        <td><span data-ttu-id="73720-173">我看到/听到视频和音频确认为提供一个命令，或获取消除歧义时所需的用户体验时。</span><span class="sxs-lookup"><span data-stu-id="73720-173">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="73720-174">以下是，我们发现，帮助团队选择交互模型的问题：</span><span class="sxs-lookup"><span data-stu-id="73720-174">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="73720-175">问:我的用户是否想要触摸全息并执行精度 holographic 操作？</span><span class="sxs-lookup"><span data-stu-id="73720-175">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="73720-176">答：如果是这样，请查看精度目标以及与手或运动控制器操作的双手和工具交互模型。</span><span class="sxs-lookup"><span data-stu-id="73720-176">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="73720-177">问:我的用户是否需要保留其手中免费的实际的任务？</span><span class="sxs-lookup"><span data-stu-id="73720-177">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="73720-178">答：如果是这样，看一看无交互模型，它提供更完美的动手体验通过基于的视线移动和语音的交互。</span><span class="sxs-lookup"><span data-stu-id="73720-178">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="73720-179">问:我的用户拥有时间来学习我混合的现实的应用程序的交互或他们是否需要与最小的学习曲线之间的交互可能？</span><span class="sxs-lookup"><span data-stu-id="73720-179">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="73720-180">答：我们建议的最低的学习曲线和最直观交互的双手和工具模型，只要用户就能够使用太多的事情进行交互。</span><span class="sxs-lookup"><span data-stu-id="73720-180">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="73720-181">问:我的用户是否为指向和操作使用 motion 控制器？</span><span class="sxs-lookup"><span data-stu-id="73720-181">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="73720-182">答：双手和工具模型包括所有指南与运动控制器更完美的体验。</span><span class="sxs-lookup"><span data-stu-id="73720-182">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="73720-183">问:是否可访问性控制器或常见的蓝牙控制器，例如 clicker 使用我的用户？</span><span class="sxs-lookup"><span data-stu-id="73720-183">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="73720-184">答：我们建议为所有非跟踪控制器的 Head 注视和提交模型。</span><span class="sxs-lookup"><span data-stu-id="73720-184">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="73720-185">它旨在使用户能够遍历整个简单的"目标和提交"技工经验。</span><span class="sxs-lookup"><span data-stu-id="73720-185">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="73720-186">问:我的用户仅进行体验"通过单击"（例如在 3d 类似于幻灯片放映的环境中），而不是导航的 UI 控件的密集布局？</span><span class="sxs-lookup"><span data-stu-id="73720-186">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="73720-187">答：如果用户不需要控制 UI 的很多，Head 注视和提交提供了其中的用户不需要担心如何面向 learnable 选项。</span><span class="sxs-lookup"><span data-stu-id="73720-187">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="73720-188">问:我的用户使用这两个 HoloLens （第 1 代） 和 HoloLens 2 / Windows 沉浸式 （VR 耳机）</span><span class="sxs-lookup"><span data-stu-id="73720-188">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="73720-189">答：由于头注视和提交是 HoloLens 交互模型 （第 1 代），我们建议，创作者支持 HoloLens （第 1 代） 使用 Head 视线移动，并提交的任何功能或用户可能会遇到 HoloLens 的模式 （第 1 代） 耳机。</span><span class="sxs-lookup"><span data-stu-id="73720-189">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="73720-190">请参阅下面的下一步部分上*转换交互模型*有关更多 HoloLens 代为很好的体验的详细信息。</span><span class="sxs-lookup"><span data-stu-id="73720-190">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="73720-191">问:怎么办对于用户而言通常移动 （涉及大型空间或空间之间移动），而不是往往会在单个的空间内工作的用户？</span><span class="sxs-lookup"><span data-stu-id="73720-191">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="73720-192">答：交互模型中的任何适用于这些用户。</span><span class="sxs-lookup"><span data-stu-id="73720-192">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="73720-193">特定于应用程序设计的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="73720-193">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="73720-194">转换交互模型</span><span class="sxs-lookup"><span data-stu-id="73720-194">Transition interaction models</span></span>
<span data-ttu-id="73720-195">此外，还有用例可能需要利用多个交互模型的情况。</span><span class="sxs-lookup"><span data-stu-id="73720-195">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="73720-196">例如，你的应用的"创建流"利用双手和工具交互模型，但你想要对现场技术人员采用无模式。</span><span class="sxs-lookup"><span data-stu-id="73720-196">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="73720-197">如果您的体验确实需要多个交互模型，我们发现许多最终用户可能会遇到转换从一个模型到另一个-尤其是最终用户的新 MR 的难度。</span><span class="sxs-lookup"><span data-stu-id="73720-197">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="73720-198">为了帮助指南设计人员和开发人员通过在 MR 将非常困难的选择，我们正致力于使用多个交互模型的详细指南。</span><span class="sxs-lookup"><span data-stu-id="73720-198">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="73720-199">请参阅</span><span class="sxs-lookup"><span data-stu-id="73720-199">See also</span></span>
* [<span data-ttu-id="73720-200">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="73720-200">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="73720-201">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="73720-201">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="73720-202">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="73720-202">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="73720-203">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="73720-203">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="73720-204">手势</span><span class="sxs-lookup"><span data-stu-id="73720-204">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="73720-205">语音命令</span><span class="sxs-lookup"><span data-stu-id="73720-205">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="73720-206">运动控制器</span><span class="sxs-lookup"><span data-stu-id="73720-206">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="73720-207">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="73720-207">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="73720-208">空间映射设计</span><span class="sxs-lookup"><span data-stu-id="73720-208">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="73720-209">舒适</span><span class="sxs-lookup"><span data-stu-id="73720-209">Comfort</span></span>](comfort.md)

