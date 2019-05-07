---
title: 多模式交互概述
description: 多模式交互的概述
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: 混合现实的视线移动，注视目标交互，设计
ms.openlocfilehash: f52a0cd8ec53bfe0f4c5da2c054c538eda1c93ca
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993602"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="67cbf-104">引入 instinctual 交互</span><span class="sxs-lookup"><span data-stu-id="67cbf-104">Introducing instinctual interactions</span></span>
<span data-ttu-id="67cbf-105">简单、 instinctual 交互的基本原理是整个 Microsoft 混合现实平台织物。</span><span class="sxs-lookup"><span data-stu-id="67cbf-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="67cbf-106">我们采取了三个步骤以确保应用程序设计人员和开发人员可以提供为其客户比较容易、 直观的交互。</span><span class="sxs-lookup"><span data-stu-id="67cbf-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="67cbf-107">首先，我们已确保我们令人惊叹的传感器和输入的技术，包括手动跟踪、 眼睛追踪和自然语言中，将合并到无缝多模式交互模型。</span><span class="sxs-lookup"><span data-stu-id="67cbf-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="67cbf-108">根据我们的研究，设计和开发 multimodally-以及不基于单个输入--是创建 instinctual 体验的关键。</span><span class="sxs-lookup"><span data-stu-id="67cbf-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="67cbf-109">其次，我们已经认识到很多开发人员面向多个设备，还是 HoloLens 2 和 HoloLens （第 1 代） 或 HoloLens 和 VR。</span><span class="sxs-lookup"><span data-stu-id="67cbf-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="67cbf-110">所以我们设计了我们的交互模型来跨设备工作 （即使每个设备上，输入的技术各不相同）。</span><span class="sxs-lookup"><span data-stu-id="67cbf-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="67cbf-111">例如，Windows 沉浸式头戴式耳机与 6DOF 控制器上的远端交互和 HoloLens 2 这两个最交互使用的相同提示和模式，轻松跨设备应用程序。</span><span class="sxs-lookup"><span data-stu-id="67cbf-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="67cbf-112">不只是这方便，为开发人员和设计器中，但它感觉自然向最终用户。</span><span class="sxs-lookup"><span data-stu-id="67cbf-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="67cbf-113">最后，虽然我们已经认识到，有数千个有效、 富有吸引力神奇的交互可能 MR 中，我们已找到该有意采用单个交互模型中端到端应用程序就是确保用户是成功的最佳方法和获得完美的体验。</span><span class="sxs-lookup"><span data-stu-id="67cbf-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="67cbf-114">为此，我们提供了此交互指南中的三个操作：</span><span class="sxs-lookup"><span data-stu-id="67cbf-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="67cbf-115">我们已结构化围绕三个主要交互模型的组件和模式所需的每个本指南</span><span class="sxs-lookup"><span data-stu-id="67cbf-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="67cbf-116">我们提供了我们平台提供了其他权益的补充指南</span><span class="sxs-lookup"><span data-stu-id="67cbf-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="67cbf-117">我们提供了指导，以帮助选择适合您的方案的相应交互模型</span><span class="sxs-lookup"><span data-stu-id="67cbf-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>


## <a name="three-multimodal-interaction-models"></a><span data-ttu-id="67cbf-118">三个多模式交互模型</span><span class="sxs-lookup"><span data-stu-id="67cbf-118">Three multimodal interaction models</span></span>
<span data-ttu-id="67cbf-119">根据我们的研究和使用日期的客户，我们发现三个主要交互模型满足大多数混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="67cbf-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of Mixed Reality experiences.</span></span>

<span data-ttu-id="67cbf-120">在许多方面，交互模型是用于完成他们的流的用户的心理模型。</span><span class="sxs-lookup"><span data-stu-id="67cbf-120">In many ways, the interaction model  is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="67cbf-121">这些交互模型的每个客户需求的一组针对进行了优化，以及方便、 强大且可在自己的权限中使用。</span><span class="sxs-lookup"><span data-stu-id="67cbf-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="67cbf-122">下图是简要的概述。</span><span class="sxs-lookup"><span data-stu-id="67cbf-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="67cbf-123">在以下页中使用图像和代码示例链接使用每个交互模型的详细的信息。</span><span class="sxs-lookup"><span data-stu-id="67cbf-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span>  

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="67cbf-124"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="67cbf-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="67cbf-125"><strong>示例方案</strong></span><span class="sxs-lookup"><span data-stu-id="67cbf-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="67cbf-126"><strong>合适大小</strong></span><span class="sxs-lookup"><span data-stu-id="67cbf-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="67cbf-127"><strong>硬件</strong></span><span class="sxs-lookup"><span data-stu-id="67cbf-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="67cbf-128"><a href="hands-and-tools.md">双手和工具</a></span><span class="sxs-lookup"><span data-stu-id="67cbf-128"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="67cbf-129">3D 空间体验</span><span class="sxs-lookup"><span data-stu-id="67cbf-129">3D spatial experiences</span></span><br><span data-ttu-id="67cbf-130">例如空间布局和设计、 内容操作或模拟</span><span class="sxs-lookup"><span data-stu-id="67cbf-130">e.g. spatial layout and design, content manipulation, or simulation</span></span></td>
        <td><span data-ttu-id="67cbf-131">非常适用于新用户</span><span class="sxs-lookup"><span data-stu-id="67cbf-131">Great for new users</span></span><br><span data-ttu-id="67cbf-132">低学习曲线</span><span class="sxs-lookup"><span data-stu-id="67cbf-132">Low learning curve</span></span><br><span data-ttu-id="67cbf-133">接地中轻松可视化提示</span><span class="sxs-lookup"><span data-stu-id="67cbf-133">Grounded in easy visual affordances</span></span><br><span data-ttu-id="67cbf-134">在手动跟踪和 6 DoF 控制器之间的一致用户体验</span><span class="sxs-lookup"><span data-stu-id="67cbf-134">Consistent UX across hand tracking and 6 DoF controllers</span></span><br><span data-ttu-id="67cbf-135">与语音结合使用时，很好的眼跟踪或 head 注视</span><span class="sxs-lookup"><span data-stu-id="67cbf-135">Great when coupled with voice, eye tracking, or head gaze</span></span></td>
        <td><span data-ttu-id="67cbf-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="67cbf-136">HoloLens 2</span></span><br><span data-ttu-id="67cbf-137">带 6DOF 控制器沉浸式 Windows</span><span class="sxs-lookup"><span data-stu-id="67cbf-137">Windows Immersive w/ 6DOF Controllers</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="67cbf-138"><a href="hands-free.md">Hands-free</a></span><span class="sxs-lookup"><span data-stu-id="67cbf-138"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="67cbf-139">上下文体验，其中用户的手都被占用例如学习，维护作业</span><span class="sxs-lookup"><span data-stu-id="67cbf-139">Contextual experiences where a user's hands are occupied e.g. on the-job learning, maintenance</span></span></td>
        <td><span data-ttu-id="67cbf-140">一些学习所需</span><span class="sxs-lookup"><span data-stu-id="67cbf-140">Some learning required</span></span><br><span data-ttu-id="67cbf-141">如果为不可用</span><span class="sxs-lookup"><span data-stu-id="67cbf-141">If hands are unavailable</span></span><br><span data-ttu-id="67cbf-142">对语音和自然语言</span><span class="sxs-lookup"><span data-stu-id="67cbf-142">pairs well with voice and natural language</span></span></td>
        <td><span data-ttu-id="67cbf-143">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="67cbf-143">HoloLens 2</span></span><br><span data-ttu-id="67cbf-144">HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="67cbf-144">HoloLens (1st gen)</span></span><br> <span data-ttu-id="67cbf-145">沉浸式 Windows</span><span class="sxs-lookup"><span data-stu-id="67cbf-145">Windows Immersive</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="67cbf-146"><a href="gaze-and-commit.md">Head 注视和提交</a></span><span class="sxs-lookup"><span data-stu-id="67cbf-146"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="67cbf-147">点击体验例如 3D 演示文稿、 演示</span><span class="sxs-lookup"><span data-stu-id="67cbf-147">Click-through experiences e.g. 3D presentations, demos</span></span></td>
        <td><span data-ttu-id="67cbf-148">需要培训 HMDs 上但不是移动设备上</span><span class="sxs-lookup"><span data-stu-id="67cbf-148">Requires training on HMDs but not on mobile</span></span><br><span data-ttu-id="67cbf-149">最适合可访问的控制器</span><span class="sxs-lookup"><span data-stu-id="67cbf-149">Best for accessible controllers</span></span><br><span data-ttu-id="67cbf-150">最适合 HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="67cbf-150">Best for HoloLens (1st gen)</span></span></td>
        <td><span data-ttu-id="67cbf-151">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="67cbf-151">HoloLens 2</span></span><br><span data-ttu-id="67cbf-152">HoloLens （第 1 代）</span><span class="sxs-lookup"><span data-stu-id="67cbf-152">HoloLens (1st gen)</span></span><br> <span data-ttu-id="67cbf-153">沉浸式 Windows</span><span class="sxs-lookup"><span data-stu-id="67cbf-153">Windows Immersive</span></span><br> <span data-ttu-id="67cbf-154">移动 AR</span><span class="sxs-lookup"><span data-stu-id="67cbf-154">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="67cbf-155">确保没有任何空白或为你的体验的交互中的漏洞的最佳方法是按照从开始到结束的单个模型的指导。</span><span class="sxs-lookup"><span data-stu-id="67cbf-155">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="67cbf-156">为了加快设计和开发，我们提供了详细的信息以及指向图像和代码示例中我们的每个模型的覆盖范围。</span><span class="sxs-lookup"><span data-stu-id="67cbf-156">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="67cbf-157">但首先，以下各节介绍的选择和实现这些交互模型之一的步骤。</span><span class="sxs-lookup"><span data-stu-id="67cbf-157">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="67cbf-158">此页结束时，将上了解我们的指南：</span><span class="sxs-lookup"><span data-stu-id="67cbf-158">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="67cbf-159">选择为您的客户交互模型</span><span class="sxs-lookup"><span data-stu-id="67cbf-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="67cbf-160">使用交互模型指南</span><span class="sxs-lookup"><span data-stu-id="67cbf-160">Using the interaction model guidance</span></span>
* <span data-ttu-id="67cbf-161">交互模型之间转换</span><span class="sxs-lookup"><span data-stu-id="67cbf-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="67cbf-162">设计后续步骤</span><span class="sxs-lookup"><span data-stu-id="67cbf-162">Design next steps</span></span>

## <a name="choosing-an-interaction-model-for-your-customer"></a><span data-ttu-id="67cbf-163">选择为您的客户交互模型</span><span class="sxs-lookup"><span data-stu-id="67cbf-163">Choosing an interaction model for your customer</span></span>

<span data-ttu-id="67cbf-164">很可能，开发人员和创建者已有的一些观点记住他们希望为其用户的交互体验种类。</span><span class="sxs-lookup"><span data-stu-id="67cbf-164">Most likely, developers and creators already have some ideas in mind of the kinds of interaction experience they want for their users.</span></span>
<span data-ttu-id="67cbf-165">鼓励客户为中心的方法来设计，我们建议遵循以下指南来选择适合您的客户的交互模型。</span><span class="sxs-lookup"><span data-stu-id="67cbf-165">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="67cbf-166">为什么要遵循以下指南？</span><span class="sxs-lookup"><span data-stu-id="67cbf-166">Why follow this guidance?</span></span>

* <span data-ttu-id="67cbf-167">测试我们的交互模型为目标和物理和认知工作量、 intuitiveness 和 learnability 等的主观标准。</span><span class="sxs-lookup"><span data-stu-id="67cbf-167">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="67cbf-168">因为交互不同，视频和音频提示和对象行为可能之间的交互模型也不同。</span><span class="sxs-lookup"><span data-stu-id="67cbf-168">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="67cbf-169">组合在一起的多个交互模型部分会竞争等，如同时进行手动大气和的视线移动游标，这会倾覆并使用户感到困惑的风险。</span><span class="sxs-lookup"><span data-stu-id="67cbf-169">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="67cbf-170">下面是针对每个交互模型提供和行为进行了优化的一些示例。</span><span class="sxs-lookup"><span data-stu-id="67cbf-170">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="67cbf-171">我们通常看到新的用户类似的问题，如"如何知道系统工作，如何知道我可以做什么，以及如何知道是否理解刚才的操作？"</span><span class="sxs-lookup"><span data-stu-id="67cbf-171">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="67cbf-172"><strong>Model</strong></span><span class="sxs-lookup"><span data-stu-id="67cbf-172"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="67cbf-173"><strong>如何知道是否正常工作？</strong></span><span class="sxs-lookup"><span data-stu-id="67cbf-173"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="67cbf-174"><strong>如何知道什么该怎么办？</strong></span><span class="sxs-lookup"><span data-stu-id="67cbf-174"><strong>How do I know what can I do?</strong></span></span></td>
        <td><span data-ttu-id="67cbf-175"><strong>如何知道刚才的操作？</strong></span><span class="sxs-lookup"><span data-stu-id="67cbf-175"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="67cbf-176"><a href="hands-and-tools.md">双手和工具</a></span><span class="sxs-lookup"><span data-stu-id="67cbf-176"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="67cbf-177">我看到 mesh 手的形状，我看到指尖功能可见性： 或手动 / 控制器光线。</span><span class="sxs-lookup"><span data-stu-id="67cbf-177">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="67cbf-178">我看到 grabbable 句柄或即将达到我的手时，将显示边界框。</span><span class="sxs-lookup"><span data-stu-id="67cbf-178">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="67cbf-179">我听到声音声音，并在随取即行和发布到动画。</span><span class="sxs-lookup"><span data-stu-id="67cbf-179">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="67cbf-180"><a href="gaze-and-commit.md">Head 注视和提交</a></span><span class="sxs-lookup"><span data-stu-id="67cbf-180"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="67cbf-181">我看到我的视野中心中的游标。</span><span class="sxs-lookup"><span data-stu-id="67cbf-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="67cbf-182">视线移动游标时对特定对象的状态更改。</span><span class="sxs-lookup"><span data-stu-id="67cbf-182">The gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="67cbf-183">我看到/听到视频和音频确认时我采取措施。</span><span class="sxs-lookup"><span data-stu-id="67cbf-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="67cbf-184"><a href="hands-free.md">无 （的视线移动和停留）</a></span><span class="sxs-lookup"><span data-stu-id="67cbf-184"><a href="hands-free.md">Hands-free (Gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="67cbf-185">我看到我的视野中心中的游标。</span><span class="sxs-lookup"><span data-stu-id="67cbf-185">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="67cbf-186">当我在此再次详述种交互的对象时，我看到一个进度指示器。</span><span class="sxs-lookup"><span data-stu-id="67cbf-186">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="67cbf-187">我看到/听到视频和音频确认时我采取措施。</span><span class="sxs-lookup"><span data-stu-id="67cbf-187">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="67cbf-188"><a href="hands-free.md">无 （语音命令）</a></span><span class="sxs-lookup"><span data-stu-id="67cbf-188"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="67cbf-189">我看到一个侦听的指示符和显示系统听到的隐藏式字幕。</span><span class="sxs-lookup"><span data-stu-id="67cbf-189">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="67cbf-190">获取语音提示和提示。</span><span class="sxs-lookup"><span data-stu-id="67cbf-190">I get voice prompts and hints.</span></span>  <span data-ttu-id="67cbf-191">当我说"我可以说什么？"</span><span class="sxs-lookup"><span data-stu-id="67cbf-191">When I say "what can I say?"</span></span> <span data-ttu-id="67cbf-192">我看到的反馈。</span><span class="sxs-lookup"><span data-stu-id="67cbf-192">I see feedback.</span></span></td>
        <td><span data-ttu-id="67cbf-193">我看到/听到视频和音频确认为提供一个命令，或获取消除歧义时所需的用户体验时。</span><span class="sxs-lookup"><span data-stu-id="67cbf-193">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="67cbf-194">以下是，我们发现，帮助团队选择交互模型的问题：</span><span class="sxs-lookup"><span data-stu-id="67cbf-194">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="67cbf-195">问:我的用户是否想要触摸全息并执行精度 holographic 操作？</span><span class="sxs-lookup"><span data-stu-id="67cbf-195">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span>
<span data-ttu-id="67cbf-196">答：如果是这样，请查看精度目标以及与手或运动控制器操作的双手和工具交互模型。</span><span class="sxs-lookup"><span data-stu-id="67cbf-196">A:  If so, check out the Hands and Tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="67cbf-197">问:我的用户是否需要保留其手中免费的实际的任务？</span><span class="sxs-lookup"><span data-stu-id="67cbf-197">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span>
<span data-ttu-id="67cbf-198">答：如果是这样，看一看无交互模型，它提供更完美的动手体验通过基于的视线移动和语音的交互。</span><span class="sxs-lookup"><span data-stu-id="67cbf-198">A:  If so, take a look at the Hands-Free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="67cbf-199">问:我的用户拥有时间来学习我混合的现实的应用程序的交互或他们是否需要与最小的学习曲线之间的交互可能？</span><span class="sxs-lookup"><span data-stu-id="67cbf-199">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span>
<span data-ttu-id="67cbf-200">答：我们建议的最低的学习曲线和最直观交互的双手和工具模型，只要用户就能够使用太多的事情进行交互。</span><span class="sxs-lookup"><span data-stu-id="67cbf-200">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="67cbf-201">问:我的用户是否为指向和操作使用 motion 控制器？</span><span class="sxs-lookup"><span data-stu-id="67cbf-201">Q:  Do my users use motion controllers for pointing and manipulation?</span></span>
<span data-ttu-id="67cbf-202">答：双手和工具模型包括所有指南与运动控制器更完美的体验。</span><span class="sxs-lookup"><span data-stu-id="67cbf-202">A:  The Hands and Tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="67cbf-203">问:是否可访问性控制器或常见的蓝牙控制器，例如 clicker 使用我的用户？</span><span class="sxs-lookup"><span data-stu-id="67cbf-203">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span>
<span data-ttu-id="67cbf-204">答：我们建议为所有非跟踪控制器的 Head 注视和提交模型。</span><span class="sxs-lookup"><span data-stu-id="67cbf-204">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="67cbf-205">它旨在使用户能够遍历整个简单的"目标和提交"技工经验。</span><span class="sxs-lookup"><span data-stu-id="67cbf-205">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="67cbf-206">问:我的用户仅进行体验"通过单击"（例如在 3d 类似于幻灯片放映的环境中），而不是导航的 UI 控件的密集布局？</span><span class="sxs-lookup"><span data-stu-id="67cbf-206">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span>
<span data-ttu-id="67cbf-207">答：如果用户不需要控制 UI 的很多，Head 注视和提交提供了其中的用户不需要担心如何面向 learnable 选项。</span><span class="sxs-lookup"><span data-stu-id="67cbf-207">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="67cbf-208">问:我的用户使用这两个 HoloLens （第 1 代） 和 HoloLens 2 / Windows 沉浸式 （VR 耳机） 答：由于头注视和提交是 HoloLens 交互模型 （第 1 代），我们建议，创作者支持 HoloLens （第 1 代） 使用 Head 视线移动，并提交的任何功能或用户可能会遇到 HoloLens 的模式 （第 1 代） 耳机。</span><span class="sxs-lookup"><span data-stu-id="67cbf-208">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets) A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="67cbf-209">请参阅下面的下一步部分上*转换交互模型*有关更多 HoloLens 代为很好的体验的详细信息。</span><span class="sxs-lookup"><span data-stu-id="67cbf-209">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="67cbf-210">问:怎么办对于用户而言通常移动 （涉及大型空间或空间之间移动），而不是往往会在单个的空间内工作的用户？</span><span class="sxs-lookup"><span data-stu-id="67cbf-210">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span>  
<span data-ttu-id="67cbf-211">答：交互模型中的任何适用于这些用户。</span><span class="sxs-lookup"><span data-stu-id="67cbf-211">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="67cbf-212">特定于应用程序设计的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="67cbf-212">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="67cbf-213">转换交互模型</span><span class="sxs-lookup"><span data-stu-id="67cbf-213">Transition interaction models</span></span>
<span data-ttu-id="67cbf-214">此外，还有用例可能需要利用多个交互模型的情况。</span><span class="sxs-lookup"><span data-stu-id="67cbf-214">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="67cbf-215">例如，你的应用的"创建流"利用双手和工具交互模型，但你想要对现场技术人员采用无模式。</span><span class="sxs-lookup"><span data-stu-id="67cbf-215">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="67cbf-216">如果您的体验确实需要多个交互模型，我们发现许多最终用户可能会遇到转换从一个模型到另一个-尤其是最终用户的新 MR 的难度。</span><span class="sxs-lookup"><span data-stu-id="67cbf-216">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="67cbf-217">为了帮助指南设计人员和开发人员通过在 MR 将非常困难的选择，我们正致力于使用多个交互模型的详细指南。</span><span class="sxs-lookup"><span data-stu-id="67cbf-217">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="67cbf-218">请参阅</span><span class="sxs-lookup"><span data-stu-id="67cbf-218">See also</span></span>
* [<span data-ttu-id="67cbf-219">Head 注视和提交</span><span class="sxs-lookup"><span data-stu-id="67cbf-219">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="67cbf-220">直接操作</span><span class="sxs-lookup"><span data-stu-id="67cbf-220">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="67cbf-221">点和提交</span><span class="sxs-lookup"><span data-stu-id="67cbf-221">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="67cbf-222">设定凝视目标</span><span class="sxs-lookup"><span data-stu-id="67cbf-222">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="67cbf-223">手势</span><span class="sxs-lookup"><span data-stu-id="67cbf-223">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="67cbf-224">语音设计</span><span class="sxs-lookup"><span data-stu-id="67cbf-224">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="67cbf-225">运动控制器</span><span class="sxs-lookup"><span data-stu-id="67cbf-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="67cbf-226">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="67cbf-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="67cbf-227">空间映射设计</span><span class="sxs-lookup"><span data-stu-id="67cbf-227">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="67cbf-228">舒适</span><span class="sxs-lookup"><span data-stu-id="67cbf-228">Comfort</span></span>](comfort.md)
