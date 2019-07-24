---
title: 免提
description: 优化你的应用程序以进行无人参与
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 混合现实, 无人参与, 注视, 注视目标, 交互, 设计
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414396"
---
# <a name="hands-free"></a><span data-ttu-id="8c404-104">免提</span><span class="sxs-lookup"><span data-stu-id="8c404-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="8c404-105">方案</span><span class="sxs-lookup"><span data-stu-id="8c404-105">Scenarios</span></span>

<span data-ttu-id="8c404-106">如[交互模型概述](interaction-fundamentals.md)中所述, 一旦确定了用户及其目标, 就可以在工作完成任务时询问自己面临的环境或环境挑战。</span><span class="sxs-lookup"><span data-stu-id="8c404-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="8c404-107">例如, 许多用户都需要使用他们的手来完成其真实的目标, 并且难以与基于手工控制器的界面进行交互。</span><span class="sxs-lookup"><span data-stu-id="8c404-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="8c404-108">某些特定情况可能如下:</span><span class="sxs-lookup"><span data-stu-id="8c404-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="8c404-109">正在通过任务进行指导, 而实际情况却非常繁忙</span><span class="sxs-lookup"><span data-stu-id="8c404-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="8c404-110">在您的计算机忙时引用材料</span><span class="sxs-lookup"><span data-stu-id="8c404-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="8c404-111">手动疲劳</span><span class="sxs-lookup"><span data-stu-id="8c404-111">Hand fatigue</span></span>
* <span data-ttu-id="8c404-112">无法跟踪的手套</span><span class="sxs-lookup"><span data-stu-id="8c404-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="8c404-113">携带东西</span><span class="sxs-lookup"><span data-stu-id="8c404-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="8c404-114">无人参与情态</span><span class="sxs-lookup"><span data-stu-id="8c404-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="8c404-115">语音命令</span><span class="sxs-lookup"><span data-stu-id="8c404-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="8c404-116">使用语音执行命令和控制接口不仅可允许用户操作 handsfree, 还可以跳过多个步骤。</span><span class="sxs-lookup"><span data-stu-id="8c404-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="8c404-117">这种形式的使用范围包括允许用户只需大声地阅读任何按钮名称以激活它, 如中所示, 可以使用可以完成任务的代理。</span><span class="sxs-lookup"><span data-stu-id="8c404-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="8c404-118">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="8c404-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="8c404-119">在某些免提情况下, 使用语音并不理想或甚至可能。</span><span class="sxs-lookup"><span data-stu-id="8c404-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="8c404-120">很大的工厂环境、隐私或社会规范都可以进行限制。</span><span class="sxs-lookup"><span data-stu-id="8c404-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="8c404-121">使用 head + 停留模型, 用户可以通过使用其头向量在应用中导航, 而延迟或按钮上的 dwelling 会在一段时间后激活它, 通常为1秒左右。</span><span class="sxs-lookup"><span data-stu-id="8c404-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="8c404-122">转换为无干预</span><span class="sxs-lookup"><span data-stu-id="8c404-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="8c404-123">在这些情况下, 让你可以轻松地与用于发出命令和导航的全息影像交互, 范围可能是对应用程序进行端到端操作的绝对要求, 而不是用户可以在任何阶段.</span><span class="sxs-lookup"><span data-stu-id="8c404-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="8c404-124">如果应用程序的要求是始终使用免提, 无论是使用停留、语音命令还是单个语音命令 "select", 都请确保在用户界面中设置适当的 accomodations。</span><span class="sxs-lookup"><span data-stu-id="8c404-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="8c404-125">如果你的目标用户需要能够自行从手切换到无人参与, 则必须考虑以下原则。</span><span class="sxs-lookup"><span data-stu-id="8c404-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="8c404-126">假设用户已处于要切换到的模式</span><span class="sxs-lookup"><span data-stu-id="8c404-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="8c404-127">例如, 如果用户在工厂地面上, 观看其 Hololens 上的视频参考, 并决定选取一个扳手开始工作, 那么她很可能会开始在 handsfree 中工作, 而无需将扳手按下某个按钮。</span><span class="sxs-lookup"><span data-stu-id="8c404-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="8c404-128">她应能够使用语音命令调用语音会话, 停留在已可见的 UI 上, 开始停留, 或说 "选择" 一词。</span><span class="sxs-lookup"><span data-stu-id="8c404-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="8c404-129">用户应该能够:</span><span class="sxs-lookup"><span data-stu-id="8c404-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="8c404-130">在无人参与的情况下切换到无人参与</span><span class="sxs-lookup"><span data-stu-id="8c404-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="8c404-131">用双手切换</span><span class="sxs-lookup"><span data-stu-id="8c404-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="8c404-132">使用控制器切换到控制器</span><span class="sxs-lookup"><span data-stu-id="8c404-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="8c404-133">创建冗余方式来切换模式</span><span class="sxs-lookup"><span data-stu-id="8c404-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="8c404-134">第一个原则就是访问, 另一个原则就是可用性。</span><span class="sxs-lookup"><span data-stu-id="8c404-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="8c404-135">不应该只是一种在模式中执行转换的方法。</span><span class="sxs-lookup"><span data-stu-id="8c404-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="8c404-136">以下是一些示例:</span><span class="sxs-lookup"><span data-stu-id="8c404-136">Some examples would be:</span></span> 
* <span data-ttu-id="8c404-137">用于开始语音交互的按钮</span><span class="sxs-lookup"><span data-stu-id="8c404-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="8c404-138">用注视 + 停留转换为的语音命令</span><span class="sxs-lookup"><span data-stu-id="8c404-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="8c404-139">添加 drama 的短划线</span><span class="sxs-lookup"><span data-stu-id="8c404-139">Add a dash of drama</span></span>
<span data-ttu-id="8c404-140">模式切换是一项很重要的事情, 这一点很重要, 在这些过渡发生时, 它们是一种显式甚至巨大的交换机, 让用户知道发生了什么情况。</span><span class="sxs-lookup"><span data-stu-id="8c404-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="8c404-141">可用性清单</span><span class="sxs-lookup"><span data-stu-id="8c404-141">Usability checklist</span></span>

<span data-ttu-id="8c404-142">**用户可以执行所有操作, 也可以从端到端免费完成,**</span><span class="sxs-lookup"><span data-stu-id="8c404-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="8c404-143">每个 interactible 应可随时访问</span><span class="sxs-lookup"><span data-stu-id="8c404-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="8c404-144">确保所有自定义手势都有替换, 如调整大小、放置、swipes、点击等。</span><span class="sxs-lookup"><span data-stu-id="8c404-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="8c404-145">确保用户完全控制 UI 的存在、位置和详细程度</span><span class="sxs-lookup"><span data-stu-id="8c404-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="8c404-146">正在获取 UI</span><span class="sxs-lookup"><span data-stu-id="8c404-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="8c404-147">对超出视图 (FOV) 的 UI 进行寻址</span><span class="sxs-lookup"><span data-stu-id="8c404-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="8c404-148">我看到了多少,</span><span class="sxs-lookup"><span data-stu-id="8c404-148">How much I see, where, when</span></span>

<span data-ttu-id="8c404-149">**与正确的实用一起教授和加强的交互的机制是什么？**</span><span class="sxs-lookup"><span data-stu-id="8c404-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="8c404-150">用户了解 。</span><span class="sxs-lookup"><span data-stu-id="8c404-150">Does the user understand ...</span></span>
* <span data-ttu-id="8c404-151">...它们处于哪种模式？</span><span class="sxs-lookup"><span data-stu-id="8c404-151">... What mode they are in?</span></span>
* <span data-ttu-id="8c404-152">...在此模式下可以执行哪些操作？</span><span class="sxs-lookup"><span data-stu-id="8c404-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="8c404-153">...什么是当前状态？</span><span class="sxs-lookup"><span data-stu-id="8c404-153">... What is the current state?</span></span>
* <span data-ttu-id="8c404-154">...如何转换？</span><span class="sxs-lookup"><span data-stu-id="8c404-154">... How they can transition out?</span></span>
    
<span data-ttu-id="8c404-155">**UI 是否经过优化, 无人参与？**</span><span class="sxs-lookup"><span data-stu-id="8c404-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="8c404-156">例如：停留实用不能内置于典型的2D 模式</span><span class="sxs-lookup"><span data-stu-id="8c404-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="8c404-157">例如：对象突出显示效果更佳</span><span class="sxs-lookup"><span data-stu-id="8c404-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="8c404-158">例如：与必须打开的字幕相比, 语音交互更好</span><span class="sxs-lookup"><span data-stu-id="8c404-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="8c404-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="8c404-159">See also</span></span>
* [<span data-ttu-id="8c404-160">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="8c404-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8c404-161">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="8c404-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8c404-162">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="8c404-162">Point and commit with hands</span></span>](point-and-commit.md)
