---
title: 优化应用程序进行无
description: 优化应用程序进行无
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 混合现实，无需手动、 注视、 注视目标交互，设计
ms.openlocfilehash: b64dec802d8ed2886021a54f302ba4a948c4f5b9
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581027"
---
# <a name="optimizing-your-app-for-hands-free"></a><span data-ttu-id="784e7-104">优化应用程序进行无</span><span class="sxs-lookup"><span data-stu-id="784e7-104">Optimizing your app for hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="784e7-105">方案</span><span class="sxs-lookup"><span data-stu-id="784e7-105">Scenarios</span></span>

<span data-ttu-id="784e7-106">中所述[交互模型概述](interaction-fundamentals.md)，一旦您已确定用户和他们的目标，问问自己环境或态势处理来完成其任务，它们可能会遇到的挑战。</span><span class="sxs-lookup"><span data-stu-id="784e7-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="784e7-107">例如，多个用户需要使用太多的事情来完成其实际目标并将有困难手控制器基于接口与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="784e7-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="784e7-108">某些特定方案可能是：</span><span class="sxs-lookup"><span data-stu-id="784e7-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="784e7-109">虽然为忙正在指导您完成一个任务，</span><span class="sxs-lookup"><span data-stu-id="784e7-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="784e7-110">虽然都在忙于手引用材料</span><span class="sxs-lookup"><span data-stu-id="784e7-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="784e7-111">手疲劳</span><span class="sxs-lookup"><span data-stu-id="784e7-111">Hand fatigue</span></span>
* <span data-ttu-id="784e7-112">无法跟踪手套</span><span class="sxs-lookup"><span data-stu-id="784e7-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="784e7-113">执行的内容</span><span class="sxs-lookup"><span data-stu-id="784e7-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="784e7-114">无模式</span><span class="sxs-lookup"><span data-stu-id="784e7-114">Hands-free modalities</span></span>

### <a name="voice-commanding"></a><span data-ttu-id="784e7-115">语音命令</span><span class="sxs-lookup"><span data-stu-id="784e7-115">Voice commanding</span></span>

<span data-ttu-id="784e7-116">使用语音命令和控制接口可以不只是允许用户运行 handsfree，但还跳过多个步骤。</span><span class="sxs-lookup"><span data-stu-id="784e7-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="784e7-117">此模式的使用情况的范围可以从允许用户只需读取任何按钮名称大声读出来激活它，如下所示，请参阅 it-say-it，到使用可以为您完成任务代理进行会话。</span><span class="sxs-lookup"><span data-stu-id="784e7-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>

* [<span data-ttu-id="784e7-118">语音设计</span><span class="sxs-lookup"><span data-stu-id="784e7-118">Voice design</span></span>](voice-design.md)


### <a name="head-gaze-and-dwell"></a><span data-ttu-id="784e7-119">Head 的视线移动和停留</span><span class="sxs-lookup"><span data-stu-id="784e7-119">Head gaze and dwell</span></span>

<span data-ttu-id="784e7-120">在某些无需干预的情况下，使用您的声音不是理想之选或甚至可能。</span><span class="sxs-lookup"><span data-stu-id="784e7-120">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="784e7-121">大声工厂环境、 隐私或社交标准所有可以进行限制。</span><span class="sxs-lookup"><span data-stu-id="784e7-121">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="784e7-122">头注视 + 会仔细斟酌模型允许用户使用其头矢量点时延迟，导航应用程序或抛开按钮将它后激活一定的时间 （通常大约 1 秒左右）。</span><span class="sxs-lookup"><span data-stu-id="784e7-122">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 

* [<span data-ttu-id="784e7-123">视线移动和停留</span><span class="sxs-lookup"><span data-stu-id="784e7-123">Gaze and dwell</span></span>](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="784e7-124">转换入和移出无</span><span class="sxs-lookup"><span data-stu-id="784e7-124">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="784e7-125">对于这些情况下，释放与命令和导航全息交互手范围可以为正在操作的应用，端到端，为一种方便性的用户可以在任何时候在转换中是绝对要求。</span><span class="sxs-lookup"><span data-stu-id="784e7-125">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="784e7-126">如果应用程序的要求是，它将始终使用无，通过使用停留、 语音命令或单个语音命令，"select"，然后请务必在 UI 中进行相应的住宿部。</span><span class="sxs-lookup"><span data-stu-id="784e7-126">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="784e7-127">如果目标用户需要能够从手中切换到无自行，然后务必要考虑这些原则：</span><span class="sxs-lookup"><span data-stu-id="784e7-127">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="784e7-128">假定用户已在他们想要切换到的模式</span><span class="sxs-lookup"><span data-stu-id="784e7-128">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="784e7-129">例如，如果你的用户是在工厂车间上观看她 hololens 的视频引用，并决定选取扳手以开始使用，她很可能想要开始在 handsfree 中工作而无需放下扳手按一个按钮。</span><span class="sxs-lookup"><span data-stu-id="784e7-129">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="784e7-130">她应该能够调用使用语音命令的语音会话，已经可见 UI 以开始停留，在此再次详述或假设单词"select"。</span><span class="sxs-lookup"><span data-stu-id="784e7-130">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="784e7-131">用户应具有的功能：</span><span class="sxs-lookup"><span data-stu-id="784e7-131">The user should have the ability to:</span></span> 
* <span data-ttu-id="784e7-132">切换到 handsfree handsfree 时</span><span class="sxs-lookup"><span data-stu-id="784e7-132">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="784e7-133">切换到用手向提供</span><span class="sxs-lookup"><span data-stu-id="784e7-133">Switch to hands with your hands</span></span>
* <span data-ttu-id="784e7-134">切换到使用控制器的控制器</span><span class="sxs-lookup"><span data-stu-id="784e7-134">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="784e7-135">创建冗余的方式，若要切换模式</span><span class="sxs-lookup"><span data-stu-id="784e7-135">Create redundant ways to switch modes</span></span>
<span data-ttu-id="784e7-136">有关访问的第一个原则时，第二个是有关可用性。</span><span class="sxs-lookup"><span data-stu-id="784e7-136">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="784e7-137">存在不应只需为转换入和移出一种模式有一种方法。</span><span class="sxs-lookup"><span data-stu-id="784e7-137">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="784e7-138">将一些示例：</span><span class="sxs-lookup"><span data-stu-id="784e7-138">Some examples would be:</span></span> 
* <span data-ttu-id="784e7-139">按钮以开始的语音交互</span><span class="sxs-lookup"><span data-stu-id="784e7-139">A button to begin voice interactions</span></span>
* <span data-ttu-id="784e7-140">使用提供注视 + 停留转换语音命令</span><span class="sxs-lookup"><span data-stu-id="784e7-140">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="784e7-141">添加短划线 drama</span><span class="sxs-lookup"><span data-stu-id="784e7-141">Add a dash of drama</span></span>
<span data-ttu-id="784e7-142">一种模式切换很了不起，重要的是重要的这些转换发生时，它们是显式、 甚至显著交换机，以让用户知道发生了什么情况。</span><span class="sxs-lookup"><span data-stu-id="784e7-142">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="784e7-143">可用性核对清单</span><span class="sxs-lookup"><span data-stu-id="784e7-143">Usability checklist</span></span>

<span data-ttu-id="784e7-144">**用户可以做的所有内容和无、 端到端的任何内容？**</span><span class="sxs-lookup"><span data-stu-id="784e7-144">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="784e7-145">每个 interactible 应可访问无</span><span class="sxs-lookup"><span data-stu-id="784e7-145">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="784e7-146">确保所有的自定义笔势，例如重设大小、 放置、 扫，点击等的替换。</span><span class="sxs-lookup"><span data-stu-id="784e7-146">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="784e7-147">确保用户始终可以确信控制的 UI 状态显示、 放置、 详细级别</span><span class="sxs-lookup"><span data-stu-id="784e7-147">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="784e7-148">获取 UI 开</span><span class="sxs-lookup"><span data-stu-id="784e7-148">Getting UI out of the way</span></span>
    * <span data-ttu-id="784e7-149">寻址超出视野 (FOV) 的 UI</span><span class="sxs-lookup"><span data-stu-id="784e7-149">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="784e7-150">我看到多少，其中时,</span><span class="sxs-lookup"><span data-stu-id="784e7-150">How much I see, where, when</span></span>

<span data-ttu-id="784e7-151">**是的交互机制正在讲授和强化与正确的提示？**</span><span class="sxs-lookup"><span data-stu-id="784e7-151">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="784e7-152">用户了解...</span><span class="sxs-lookup"><span data-stu-id="784e7-152">Does the user understand ...</span></span>
* <span data-ttu-id="784e7-153">...它们是哪种模式中？</span><span class="sxs-lookup"><span data-stu-id="784e7-153">... What mode they are in?</span></span>
* <span data-ttu-id="784e7-154">...就像在此模式下？</span><span class="sxs-lookup"><span data-stu-id="784e7-154">... What they can do in this mode?</span></span>
* <span data-ttu-id="784e7-155">...当前状态是怎样的？</span><span class="sxs-lookup"><span data-stu-id="784e7-155">... What is the current state?</span></span>
* <span data-ttu-id="784e7-156">...他们如何可以向外转换？</span><span class="sxs-lookup"><span data-stu-id="784e7-156">... How they can transition out?</span></span>
    
<span data-ttu-id="784e7-157">**UI 适用于无？**</span><span class="sxs-lookup"><span data-stu-id="784e7-157">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="784e7-158">例如，</span><span class="sxs-lookup"><span data-stu-id="784e7-158">Ex.</span></span> <span data-ttu-id="784e7-159">停留提供不是内置于典型的 2D 模式</span><span class="sxs-lookup"><span data-stu-id="784e7-159">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="784e7-160">例如，</span><span class="sxs-lookup"><span data-stu-id="784e7-160">Ex.</span></span> <span data-ttu-id="784e7-161">语音目标是更好地与对象突出显示</span><span class="sxs-lookup"><span data-stu-id="784e7-161">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="784e7-162">例如，</span><span class="sxs-lookup"><span data-stu-id="784e7-162">Ex.</span></span> <span data-ttu-id="784e7-163">语音交互是更好地与已启用的隐藏式字幕</span><span class="sxs-lookup"><span data-stu-id="784e7-163">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="784e7-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="784e7-164">See also</span></span>
* [<span data-ttu-id="784e7-165">视线移动和提交</span><span class="sxs-lookup"><span data-stu-id="784e7-165">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="784e7-166">直接操作</span><span class="sxs-lookup"><span data-stu-id="784e7-166">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="784e7-167">点和提交</span><span class="sxs-lookup"><span data-stu-id="784e7-167">Point and commit</span></span>](point-and-commit.md)
