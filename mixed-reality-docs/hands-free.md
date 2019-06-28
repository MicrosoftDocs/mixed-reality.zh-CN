---
title: 免提
description: 优化应用程序进行无
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 混合现实，无需手动、 注视、 注视目标交互，设计
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414396"
---
# <a name="hands-free"></a><span data-ttu-id="0f42d-104">免提</span><span class="sxs-lookup"><span data-stu-id="0f42d-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="0f42d-105">方案</span><span class="sxs-lookup"><span data-stu-id="0f42d-105">Scenarios</span></span>

<span data-ttu-id="0f42d-106">中所述[交互模型概述](interaction-fundamentals.md)，一旦您已确定用户和他们的目标，问问自己环境或态势处理来完成其任务，它们可能会遇到的挑战。</span><span class="sxs-lookup"><span data-stu-id="0f42d-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="0f42d-107">例如，许多用户需要使用太多的事情来完成实际的目标，并将有困难手控制器基于接口与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="0f42d-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="0f42d-108">某些特定方案可能是：</span><span class="sxs-lookup"><span data-stu-id="0f42d-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="0f42d-109">虽然为忙正在指导您完成一个任务，</span><span class="sxs-lookup"><span data-stu-id="0f42d-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="0f42d-110">虽然都在忙于手引用材料</span><span class="sxs-lookup"><span data-stu-id="0f42d-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="0f42d-111">手疲劳</span><span class="sxs-lookup"><span data-stu-id="0f42d-111">Hand fatigue</span></span>
* <span data-ttu-id="0f42d-112">无法跟踪手套</span><span class="sxs-lookup"><span data-stu-id="0f42d-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="0f42d-113">执行的内容</span><span class="sxs-lookup"><span data-stu-id="0f42d-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="0f42d-114">无模式</span><span class="sxs-lookup"><span data-stu-id="0f42d-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="0f42d-115">语音命令</span><span class="sxs-lookup"><span data-stu-id="0f42d-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="0f42d-116">使用语音命令和控制接口可以不只是允许用户运行 handsfree，但还跳过多个步骤。</span><span class="sxs-lookup"><span data-stu-id="0f42d-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="0f42d-117">此模式的使用情况的范围可以从允许用户只需读取大声读出要激活它，如下所示，请参阅 it-say-it，活跃的可以为您完成任务代理的任何按钮的名称。</span><span class="sxs-lookup"><span data-stu-id="0f42d-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="0f42d-118">头部凝视和停留</span><span class="sxs-lookup"><span data-stu-id="0f42d-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="0f42d-119">在某些无需干预的情况下，使用您的声音不是理想之选或甚至可能。</span><span class="sxs-lookup"><span data-stu-id="0f42d-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="0f42d-120">大声工厂环境、 隐私或社交标准所有可以进行限制。</span><span class="sxs-lookup"><span data-stu-id="0f42d-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="0f42d-121">头注视 + 会仔细斟酌模型允许用户使用其头矢量点时延迟，导航应用程序或抛开按钮将它后激活一定的时间，通常约 1 秒左右。</span><span class="sxs-lookup"><span data-stu-id="0f42d-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="0f42d-122">转换入和移出无</span><span class="sxs-lookup"><span data-stu-id="0f42d-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="0f42d-123">对于这些情况下，释放与命令和导航全息交互手范围可以为要到运行该应用程序，端到端到一种方便性的用户可以在任何转换中是绝对要求时间。</span><span class="sxs-lookup"><span data-stu-id="0f42d-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="0f42d-124">如果应用程序的要求是，它将始终使用无，通过使用停留、 语音命令或单个语音命令，"select"，然后请务必在 UI 中进行相应的住宿部。</span><span class="sxs-lookup"><span data-stu-id="0f42d-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="0f42d-125">如果目标用户需要能够从手中切换到无自行，然后务必考虑以下原则。</span><span class="sxs-lookup"><span data-stu-id="0f42d-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="0f42d-126">假定用户已在他们想要切换到的模式</span><span class="sxs-lookup"><span data-stu-id="0f42d-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="0f42d-127">例如，如果用户是在工厂车间上观看她 hololens 的视频引用，并决定选取扳手以开始使用，她很可能会在中开始工作 handsfree 而无需放下扳手按一个按钮。</span><span class="sxs-lookup"><span data-stu-id="0f42d-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="0f42d-128">她应该能够调用语音会话使用语音命令，开始停留，已经可见 UI 在此再次详述或假设单词"select"。</span><span class="sxs-lookup"><span data-stu-id="0f42d-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="0f42d-129">用户应具有的功能：</span><span class="sxs-lookup"><span data-stu-id="0f42d-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="0f42d-130">切换到无而无需手动</span><span class="sxs-lookup"><span data-stu-id="0f42d-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="0f42d-131">切换到用手向提供</span><span class="sxs-lookup"><span data-stu-id="0f42d-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="0f42d-132">切换到使用控制器的控制器</span><span class="sxs-lookup"><span data-stu-id="0f42d-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="0f42d-133">创建冗余的方式，若要切换模式</span><span class="sxs-lookup"><span data-stu-id="0f42d-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="0f42d-134">有关访问的第一个原则时，第二个是有关可用性。</span><span class="sxs-lookup"><span data-stu-id="0f42d-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="0f42d-135">存在不应只需为转换入和移出一种模式有一种方法。</span><span class="sxs-lookup"><span data-stu-id="0f42d-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="0f42d-136">将一些示例：</span><span class="sxs-lookup"><span data-stu-id="0f42d-136">Some examples would be:</span></span> 
* <span data-ttu-id="0f42d-137">按钮以开始的语音交互</span><span class="sxs-lookup"><span data-stu-id="0f42d-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="0f42d-138">使用提供注视 + 停留转换语音命令</span><span class="sxs-lookup"><span data-stu-id="0f42d-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="0f42d-139">添加短划线 drama</span><span class="sxs-lookup"><span data-stu-id="0f42d-139">Add a dash of drama</span></span>
<span data-ttu-id="0f42d-140">一种模式切换很了不起-非常重要，这些转换发生时它们是显式、 甚至显著交换机，以让用户知道发生了什么情况。</span><span class="sxs-lookup"><span data-stu-id="0f42d-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="0f42d-141">可用性核对清单</span><span class="sxs-lookup"><span data-stu-id="0f42d-141">Usability checklist</span></span>

<span data-ttu-id="0f42d-142">**用户可以做的所有内容和无、 端到端的任何内容？**</span><span class="sxs-lookup"><span data-stu-id="0f42d-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="0f42d-143">每个 interactible 应可访问无</span><span class="sxs-lookup"><span data-stu-id="0f42d-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="0f42d-144">确保所有的自定义笔势，例如重设大小、 放置、 扫，点击等的替换。</span><span class="sxs-lookup"><span data-stu-id="0f42d-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="0f42d-145">确保用户始终可以确信控制的 UI 状态、 位置和详细级别</span><span class="sxs-lookup"><span data-stu-id="0f42d-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="0f42d-146">获取 UI 开</span><span class="sxs-lookup"><span data-stu-id="0f42d-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="0f42d-147">寻址超出视野 (FOV) 的 UI</span><span class="sxs-lookup"><span data-stu-id="0f42d-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="0f42d-148">我看到多少，其中时,</span><span class="sxs-lookup"><span data-stu-id="0f42d-148">How much I see, where, when</span></span>

<span data-ttu-id="0f42d-149">**是的交互机制正在讲授和强化与正确的提示？**</span><span class="sxs-lookup"><span data-stu-id="0f42d-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="0f42d-150">用户了解...</span><span class="sxs-lookup"><span data-stu-id="0f42d-150">Does the user understand ...</span></span>
* <span data-ttu-id="0f42d-151">...它们是哪种模式中？</span><span class="sxs-lookup"><span data-stu-id="0f42d-151">... What mode they are in?</span></span>
* <span data-ttu-id="0f42d-152">...就像在此模式下？</span><span class="sxs-lookup"><span data-stu-id="0f42d-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="0f42d-153">...当前状态是怎样的？</span><span class="sxs-lookup"><span data-stu-id="0f42d-153">... What is the current state?</span></span>
* <span data-ttu-id="0f42d-154">...他们如何可以向外转换？</span><span class="sxs-lookup"><span data-stu-id="0f42d-154">... How they can transition out?</span></span>
    
<span data-ttu-id="0f42d-155">**UI 适用于无？**</span><span class="sxs-lookup"><span data-stu-id="0f42d-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="0f42d-156">例如：停留提供不是内置于典型的 2D 模式</span><span class="sxs-lookup"><span data-stu-id="0f42d-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="0f42d-157">例如：语音目标是更好地与对象突出显示</span><span class="sxs-lookup"><span data-stu-id="0f42d-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="0f42d-158">例如：语音交互是更好地与已启用的隐藏式字幕</span><span class="sxs-lookup"><span data-stu-id="0f42d-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="0f42d-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="0f42d-159">See also</span></span>
* [<span data-ttu-id="0f42d-160">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="0f42d-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0f42d-161">使用手直接操作</span><span class="sxs-lookup"><span data-stu-id="0f42d-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0f42d-162">使用手指向和提交</span><span class="sxs-lookup"><span data-stu-id="0f42d-162">Point and commit with hands</span></span>](point-and-commit.md)
