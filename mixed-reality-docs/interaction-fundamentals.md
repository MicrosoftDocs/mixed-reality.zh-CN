---
title: 本能交互
description: 了解简单本能交互的理念，这一理念贯穿整个混合现实平台。
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, 凝视, 设定凝视目标, 交互, 设计, hololens, MMR, 多模式
ms.openlocfilehash: abd82947be08a2f6aecc4462abc34c4674abfb7a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437972"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="ac992-104">本能交互简介</span><span class="sxs-lookup"><span data-stu-id="ac992-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="ac992-105">实现简单的本能交互这一理念贯穿整个混合现实 (MR) 平台。</span><span class="sxs-lookup"><span data-stu-id="ac992-105">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="ac992-106">我们采取了三个步骤来确保应用程序设计人员和开发人员能够为其客户提供简单直观的交互。</span><span class="sxs-lookup"><span data-stu-id="ac992-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="ac992-107">首先，确保将我们的传感器和输入技术（包括手部跟踪、眼动跟踪和自然语言输入）融入无缝多模式交互模型。</span><span class="sxs-lookup"><span data-stu-id="ac992-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  
<span data-ttu-id="ac992-108">基于在多模框架中的研究、设计和开发，而不是单个输入，是建立本能体验的关键所在。</span><span class="sxs-lookup"><span data-stu-id="ac992-108">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="ac992-109">其次，我们已认识到，许多开发人员以多种 HoloLens 设备（例如 HoloLens 2 和 HoloLens 第 1 代）或 HoloLens 和 VR 为目标。</span><span class="sxs-lookup"><span data-stu-id="ac992-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  
<span data-ttu-id="ac992-110">因此，我们设计了可跨设备工作的交互模型，即使每个设备上的输入技术不同。</span><span class="sxs-lookup"><span data-stu-id="ac992-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  
<span data-ttu-id="ac992-111">例如，具有 6DoF 控制器的 Windows 沉浸式头戴显示设备上的远距交互和 HoloLens 2 上的远距交互都使用相同的视觉元素和模式，可轻松实现跨设备应用程序开发，并为用户的交互提供自然感受。</span><span class="sxs-lookup"><span data-stu-id="ac992-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use identical affordances and patterns, making it easy for cross-device application development and providing a natural feel to user interactions.</span></span> 

<span data-ttu-id="ac992-112">虽然我们认识到 MR 中有成千上万种有效且吸引力十足的神奇交互，但是我们发现有意地在应用程序中衔接使用单个交互模型是确保用户成功并获得良好体验的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="ac992-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model end-to-end in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="ac992-113">为此，我们在交互指南中提供了三项内容：</span><span class="sxs-lookup"><span data-stu-id="ac992-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="ac992-114">围绕三个主要交互模型以及每个模型所需的组件和模式的特定指南。</span><span class="sxs-lookup"><span data-stu-id="ac992-114">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="ac992-115">有关平台提供的其他优势的补充指南。</span><span class="sxs-lookup"><span data-stu-id="ac992-115">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="ac992-116">常规指南，用于选择适合开发方案的交互模型。</span><span class="sxs-lookup"><span data-stu-id="ac992-116">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="ac992-117">多模式交互模型</span><span class="sxs-lookup"><span data-stu-id="ac992-117">Multimodal interaction models</span></span>

<span data-ttu-id="ac992-118">根据我们的研究以及与客户的反馈，我们发现，有三个主要交互模型适合大多数混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="ac992-118">Based on our research and feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span> <span data-ttu-id="ac992-119">在许多方面，交互模型是用户的心理模型，旨在阐述如何完成某个工作流。</span><span class="sxs-lookup"><span data-stu-id="ac992-119">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="ac992-120">每个交互模型都针对一组客户需求进行了优化，便于使用、功能强大且用途广泛（在正确使用的前提下）。</span><span class="sxs-lookup"><span data-stu-id="ac992-120">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="ac992-121">下图是简化概述。</span><span class="sxs-lookup"><span data-stu-id="ac992-121">The chart below is a simplified overview.</span></span> <span data-ttu-id="ac992-122">本页下方通过链接提供了有关使用每个交互模型的详细信息以及相关图像和代码示例。</span><span class="sxs-lookup"><span data-stu-id="ac992-122">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ac992-123"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="ac992-123"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="ac992-124"><strong>示例方案</strong></span><span class="sxs-lookup"><span data-stu-id="ac992-124"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="ac992-125"><strong>适合</strong></span><span class="sxs-lookup"><span data-stu-id="ac992-125"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="ac992-126"><strong>硬件</strong></span><span class="sxs-lookup"><span data-stu-id="ac992-126"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ac992-127"><a href="hands-and-tools.md">手和运动控制器</a></span><span class="sxs-lookup"><span data-stu-id="ac992-127"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="ac992-128">3D 空间体验，例如空间布局和设计、内容操作或模拟。</span><span class="sxs-lookup"><span data-stu-id="ac992-128">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="ac992-129">非常适合新用户，可与语音、眼动跟踪或头部凝视结合使用。</span><span class="sxs-lookup"><span data-stu-id="ac992-129">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="ac992-130">可轻易掌握。</span><span class="sxs-lookup"><span data-stu-id="ac992-130">Low learning curve.</span></span> <span data-ttu-id="ac992-131">跨手部跟踪和 6DoF 控制器使用一致的 UX 。</span><span class="sxs-lookup"><span data-stu-id="ac992-131">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="ac992-132">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ac992-132">HoloLens 2</span></span><br><span data-ttu-id="ac992-133">沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="ac992-133">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ac992-134"><a href="hands-free.md">免动手操作</a></span><span class="sxs-lookup"><span data-stu-id="ac992-134"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="ac992-135">用户双手不空时的情境体验，例如在职学习和维护。</span><span class="sxs-lookup"><span data-stu-id="ac992-135">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="ac992-136">必需进行一些学习。</span><span class="sxs-lookup"><span data-stu-id="ac992-136">Some learning required.</span></span> <span data-ttu-id="ac992-137">如果无法用手，设备可以配合使用语音和自然语言。</span><span class="sxs-lookup"><span data-stu-id="ac992-137">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="ac992-138">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ac992-138">HoloLens 2</span></span><br><span data-ttu-id="ac992-139">HoloLens（第 1 代）</span><span class="sxs-lookup"><span data-stu-id="ac992-139">HoloLens (1st gen)</span></span><br><span data-ttu-id="ac992-140">沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="ac992-140">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ac992-141"><a href="gaze-and-commit.md">凝视和提交</a></span><span class="sxs-lookup"><span data-stu-id="ac992-141"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="ac992-142">点击式体验，例如 3D 演示文稿、演示。</span><span class="sxs-lookup"><span data-stu-id="ac992-142">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="ac992-143">需要接受有关 HMD 的培训，但无需进行有关移动设备的培训。</span><span class="sxs-lookup"><span data-stu-id="ac992-143">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="ac992-144">最适合可访问控制器。</span><span class="sxs-lookup"><span data-stu-id="ac992-144">Best for accessible controllers.</span></span> <span data-ttu-id="ac992-145">最适合 HoloLens（第 1 代）。</span><span class="sxs-lookup"><span data-stu-id="ac992-145">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="ac992-146">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ac992-146">HoloLens 2</span></span><br><span data-ttu-id="ac992-147">HoloLens（第 1 代）</span><span class="sxs-lookup"><span data-stu-id="ac992-147">HoloLens (1st gen)</span></span><br><span data-ttu-id="ac992-148">沉浸式头戴显示设备</span><span class="sxs-lookup"><span data-stu-id="ac992-148">Immersive headsets</span></span><br><span data-ttu-id="ac992-149">移动 AR</span><span class="sxs-lookup"><span data-stu-id="ac992-149">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="ac992-150">为了确保用户交互体验中不存在差距，最好是从头到尾遵循单个模型的指南。</span><span class="sxs-lookup"><span data-stu-id="ac992-150">To ensure that there are no gaps in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="ac992-151">以下部分将会介绍选择和实现其中一种交互模型的步骤。</span><span class="sxs-lookup"><span data-stu-id="ac992-151">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="ac992-152">查看完本页后，你将了解有关以下方面的指南：</span><span class="sxs-lookup"><span data-stu-id="ac992-152">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="ac992-153">为你的客户选择交互模型</span><span class="sxs-lookup"><span data-stu-id="ac992-153">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="ac992-154">实现交互模型</span><span class="sxs-lookup"><span data-stu-id="ac992-154">Implementing the interaction model</span></span>
* <span data-ttu-id="ac992-155">在交互模型之间转换</span><span class="sxs-lookup"><span data-stu-id="ac992-155">Transitioning between interaction models</span></span>
* <span data-ttu-id="ac992-156">设计后续步骤</span><span class="sxs-lookup"><span data-stu-id="ac992-156">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="ac992-157">为你的客户选择交互模型</span><span class="sxs-lookup"><span data-stu-id="ac992-157">Choose an interaction model for your customer</span></span>

<span data-ttu-id="ac992-158">通常，开发人员和创作者已经全盘考虑了其客户可能使用的交互类型。</span><span class="sxs-lookup"><span data-stu-id="ac992-158">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="ac992-159">为了鼓励实现以客户为中心的设计，建议遵循以下指导选择针对客户进行了优化的交互模型。</span><span class="sxs-lookup"><span data-stu-id="ac992-159">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="ac992-160">为什么要遵循以下指南？</span><span class="sxs-lookup"><span data-stu-id="ac992-160">Why follow this guidance?</span></span>

* <span data-ttu-id="ac992-161">我们的交互模型针对客观和主观标准（例如身体和认知努力、直觉和学习能力）进行了测试。</span><span class="sxs-lookup"><span data-stu-id="ac992-161">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="ac992-162">由于交互不同，各交互模型的视觉/音频元素以及对象行为也可能不同。</span><span class="sxs-lookup"><span data-stu-id="ac992-162">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="ac992-163">将多个交互模型的各个部分组合在一起可能会产生竞争性视觉元素的风险，例如同时出现手部射线和头部凝视光标，</span><span class="sxs-lookup"><span data-stu-id="ac992-163">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="ac992-164">这可能会使用户感到不知所措和混淆。</span><span class="sxs-lookup"><span data-stu-id="ac992-164">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="ac992-165">以下是一些如何针对每种交互模型优化可视线索和行为的示例。</span><span class="sxs-lookup"><span data-stu-id="ac992-165">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="ac992-166">我们经常看到新用户提出类似的问题，例如“我怎样才能知道系统是否在正常工作”、“我怎样才能知道我可以做什么”，以及“我怎样才能知道它是否理解我刚刚做了什么？”   </span><span class="sxs-lookup"><span data-stu-id="ac992-166">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ac992-167"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="ac992-167"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="ac992-168"><strong>我怎样才能知道它是否在正常工作？</strong></span><span class="sxs-lookup"><span data-stu-id="ac992-168"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="ac992-169"><strong>我怎样才能知道我可以做什么？</strong></span><span class="sxs-lookup"><span data-stu-id="ac992-169"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="ac992-170"><strong>我怎样才能知道刚才的操作？</strong></span><span class="sxs-lookup"><span data-stu-id="ac992-170"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ac992-171"><a href="hands-and-tools.md">手和运动控制器</a></span><span class="sxs-lookup"><span data-stu-id="ac992-171"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="ac992-172">我看到一个手部网格，以及一个指尖视觉元素或手/控制器射线。</span><span class="sxs-lookup"><span data-stu-id="ac992-172">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="ac992-173">当我的手靠近对象时，我看到可抓握的手柄或边界框出现。</span><span class="sxs-lookup"><span data-stu-id="ac992-173">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="ac992-174">我听到有声音调，看到抓取和释放的动画。</span><span class="sxs-lookup"><span data-stu-id="ac992-174">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ac992-175"><a href="gaze-and-commit.md">头部凝视并提交</a></span><span class="sxs-lookup"><span data-stu-id="ac992-175"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="ac992-176">我在视野中央看到一个光标。</span><span class="sxs-lookup"><span data-stu-id="ac992-176">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="ac992-177">在光标置于某些对象上时，其状态会发生改变。</span><span class="sxs-lookup"><span data-stu-id="ac992-177">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="ac992-178">当我执行动作时，我会看到/听到视觉和听觉确认。</span><span class="sxs-lookup"><span data-stu-id="ac992-178">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="ac992-179"><a href="hands-free.md">解放双手（头部凝视和停留）</a></span><span class="sxs-lookup"><span data-stu-id="ac992-179"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="ac992-180">我在视野中央看到一个光标。</span><span class="sxs-lookup"><span data-stu-id="ac992-180">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="ac992-181">当我停留在一个可交互对象上时，我会看到一个进度指示器。</span><span class="sxs-lookup"><span data-stu-id="ac992-181">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="ac992-182">当我执行动作时，我会看到/听到视觉和听觉确认。</span><span class="sxs-lookup"><span data-stu-id="ac992-182">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="ac992-183"><a href="hands-free.md">（语音命令）</a></span><span class="sxs-lookup"><span data-stu-id="ac992-183"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="ac992-184">我看到一个侦听指示器和字幕，显示系统听到的内容。</span><span class="sxs-lookup"><span data-stu-id="ac992-184">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="ac992-185">我获得了语音提示。</span><span class="sxs-lookup"><span data-stu-id="ac992-185">I get voice prompts and hints.</span></span> <span data-ttu-id="ac992-186">当我说：“我可以说什么？”</span><span class="sxs-lookup"><span data-stu-id="ac992-186">When I say: "What can I say?"</span></span> <span data-ttu-id="ac992-187">我看到了反馈。</span><span class="sxs-lookup"><span data-stu-id="ac992-187">I see feedback.</span></span></td>
        <td><span data-ttu-id="ac992-188">当我发出命令时，我看到/听到视觉和听觉确认，或者在需要时得到消除歧义 UX。</span><span class="sxs-lookup"><span data-stu-id="ac992-188">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="ac992-189">以下问题可帮助团队选择交互模型：</span><span class="sxs-lookup"><span data-stu-id="ac992-189">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="ac992-190">问:用户是否想要触控全息影像并执行精确的全息操作？</span><span class="sxs-lookup"><span data-stu-id="ac992-190">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="ac992-191">答：如果是，请查看手部和运动控制器交互模型，以便进行精确定位和操作。</span><span class="sxs-lookup"><span data-stu-id="ac992-191">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="ac992-192">问:用户是否需要因真实世界的任务而保持双手空闲？</span><span class="sxs-lookup"><span data-stu-id="ac992-192">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="ac992-193">答：如果是，请查看解放双手交互模型，该模型通过基于凝视和语音的交互提供出色的解放双手体验。</span><span class="sxs-lookup"><span data-stu-id="ac992-193">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="ac992-194">问:用户是否有时间学习 MR 应用程序的交互，或者他们是否需要尽可能轻松的掌握交互知识？</span><span class="sxs-lookup"><span data-stu-id="ac992-194">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="ac992-195">答：建议使用手部和运动控制器模型，以便用户尽可能轻松地掌握相关知识并进行最直观的交互（只要用户能够用双手进行交互）。</span><span class="sxs-lookup"><span data-stu-id="ac992-195">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="ac992-196">问:用户是否使用运动控制器进行指向和操作？</span><span class="sxs-lookup"><span data-stu-id="ac992-196">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="ac992-197">答：手部和运动控制器模型包含了有关使用运动控制器实现出色体验的所有指导。</span><span class="sxs-lookup"><span data-stu-id="ac992-197">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="ac992-198">问:用户是否使用辅助功能控制器或常用蓝牙控制器，例如遥控器？</span><span class="sxs-lookup"><span data-stu-id="ac992-198">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="ac992-199">答：建议对所有非跟踪控制器使用头部凝视和提交模型。</span><span class="sxs-lookup"><span data-stu-id="ac992-199">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="ac992-200">它可让用户使用简单的“目标和提交”机制遍历全部体验。</span><span class="sxs-lookup"><span data-stu-id="ac992-200">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="ac992-201">问:用户是否仅通过“点击”来进行逐步体验（例如在类似 3D 幻灯片的环境中），而不是导航密集的 UI 控件布局？</span><span class="sxs-lookup"><span data-stu-id="ac992-201">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="ac992-202">答：如果用户不需要控制大量 UI，则其可学习使用头部凝视和提交，无需担心如何进行定位。</span><span class="sxs-lookup"><span data-stu-id="ac992-202">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="ac992-203">问:用户是否同时使用 HoloLens（第 1 代）和 HoloLens 2/Windows Mixed Reality 沉浸式头戴显示设备 (VR)？</span><span class="sxs-lookup"><span data-stu-id="ac992-203">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="ac992-204">答：由于头部凝视和提交是适用于 HoloLens（第 1 代）的交互模型，因此建议支持 HoloLens（第 1 代）的创意者对用户在 HoloLens（第 1 代）头戴显示设备上使用的任何功能或模式使用头部凝视和提交。</span><span class="sxs-lookup"><span data-stu-id="ac992-204">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="ac992-205">有关为多代 HoloLens 打造出色体验的详细信息，请参阅下面的“转换交互模型”部分  。</span><span class="sxs-lookup"><span data-stu-id="ac992-205">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="ac992-206">问:与经常在单个空间中工作的用户相比，时常移动的用户（覆盖大空间或在各空间之间移动）可使用哪些交互模型？</span><span class="sxs-lookup"><span data-stu-id="ac992-206">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="ac992-207">答：任何交互模型都适用于这些用户。</span><span class="sxs-lookup"><span data-stu-id="ac992-207">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="ac992-208">[即将推出](news.md)有关应用设计的更多指南。</span><span class="sxs-lookup"><span data-stu-id="ac992-208">More guidance specific to app design [coming soon](news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="ac992-209">转换交互模型</span><span class="sxs-lookup"><span data-stu-id="ac992-209">Transitioning interaction models</span></span>
<span data-ttu-id="ac992-210">还有一些用例可能要求利用多个交互模型。</span><span class="sxs-lookup"><span data-stu-id="ac992-210">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="ac992-211">例如，应用程序的创建流程使用“手部和运动控制器”交互模型，但你想要为现场技术人员使用解放双手模式。 </span><span class="sxs-lookup"><span data-stu-id="ac992-211">For example, your application's creation flow utilizes the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span>
<span data-ttu-id="ac992-212">如果你的体验确实需要多个交互模型，请注意，许多用户可能会在从一个模型转换到另一个模型时遇到困难，特别是刚接触混合现实的用户。</span><span class="sxs-lookup"><span data-stu-id="ac992-212">If your experience does require multiple interaction models, please keep in mind that many users might encounter difficulty when transitioning from one model to another, especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="ac992-213">我们正在持续为开发人员和设计人员编写更多的指南，以告知他们如何、何时以及为何使用多个 MR 交互模型。</span><span class="sxs-lookup"><span data-stu-id="ac992-213">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="ac992-214">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ac992-214">See also</span></span>
* [<span data-ttu-id="ac992-215">舒适</span><span class="sxs-lookup"><span data-stu-id="ac992-215">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="ac992-216">基于眼睛的交互</span><span class="sxs-lookup"><span data-stu-id="ac992-216">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="ac992-217">HoloLens 2 中的眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="ac992-217">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="ac992-218">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="ac992-218">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ac992-219">凝视和停留</span><span class="sxs-lookup"><span data-stu-id="ac992-219">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="ac992-220">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="ac992-220">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ac992-221">手 - 手势</span><span class="sxs-lookup"><span data-stu-id="ac992-221">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="ac992-222">手 - 指向并提交</span><span class="sxs-lookup"><span data-stu-id="ac992-222">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="ac992-223">本能交互</span><span class="sxs-lookup"><span data-stu-id="ac992-223">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="ac992-224">运动控制器</span><span class="sxs-lookup"><span data-stu-id="ac992-224">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="ac992-225">空间映射</span><span class="sxs-lookup"><span data-stu-id="ac992-225">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="ac992-226">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="ac992-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="ac992-227">语音输入</span><span class="sxs-lookup"><span data-stu-id="ac992-227">Voice input</span></span>](voice-input.md)


