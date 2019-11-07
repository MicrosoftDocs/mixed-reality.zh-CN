---
title: 眼睛凝视和停留
description: 眼睛凝视和停留输入模型概述
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: 眼动跟踪, 混合现实, 输入, 眼睛凝视, 视线定位, HoloLens 2, 视线选择, 停留
ms.openlocfilehash: 5130fd3c1ecd551788f61f8abb8d02cdedeb4181
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437803"
---
# <a name="eye-gaze-and-dwell"></a><span data-ttu-id="ee993-104">眼睛凝视和停留</span><span class="sxs-lookup"><span data-stu-id="ee993-104">Eye-gaze and dwell</span></span>

<span data-ttu-id="ee993-105">“眼睛凝视和停留”交互模型  是[眼睛凝视和提交](gaze-and-commit.md)交互模型的特例：</span><span class="sxs-lookup"><span data-stu-id="ee993-105">The _"eye-gaze and dwell"_ interaction model is a special case of the [eye-gaze and commit](gaze-and-commit.md) interaction model:</span></span>
1. <span data-ttu-id="ee993-106">只需看一下目标，并</span><span class="sxs-lookup"><span data-stu-id="ee993-106">Simply look at a target and</span></span> 
2. <span data-ttu-id="ee993-107">若要确认选择目标的意图，请执行辅助显式输入：只是一直看着要选择的目标。 </span><span class="sxs-lookup"><span data-stu-id="ee993-107">To confirm your intention to select the target, perform a secondary explicit input: _Simply keep looking at the target you would like to select_.</span></span>

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a><span data-ttu-id="ee993-108">“眼睛凝视和停留”交互模型的优势</span><span class="sxs-lookup"><span data-stu-id="ee993-108">Advantages of the "eye-gaze and dwell" interaction model</span></span> 
<span data-ttu-id="ee993-109">如果你正在用手执行某个任务，或者手中拿了工具，则可能无法用手与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="ee993-109">When your hands are already occupied with a task or holding tools, using them for interacting with holograms may not be an option.</span></span>
<span data-ttu-id="ee993-110">选择全息影像时，一种解放双手的替代性交互方式是“眼睛凝视和停留”，换言之，“盯着看”。 </span><span class="sxs-lookup"><span data-stu-id="ee993-110">A hands-free interaction alternative for selecting holograms is "eye-gaze and dwell" or in other words: _"look and stare"_.</span></span> <span data-ttu-id="ee993-111">这种方式的优点在于，即使是行动严重受限的可能无法正常转动其头部或身体的用户（例如，在空间严重受限的工作环境中的用户），也可以与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="ee993-111">The advantage of this approach is that even severly constrained users who may not be able to fully turn their heads or bodies can interact with holograms (e.g., in a highly confined work environment).</span></span>
<span data-ttu-id="ee993-112">用户只需一直看着要选择的目标，系统就会显示不同的停留反馈来指示过程。</span><span class="sxs-lookup"><span data-stu-id="ee993-112">The user simply keeps looking at the target they would like to select and different dwell feedback is displayed to indicate the process.</span></span>


## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a><span data-ttu-id="ee993-113">“眼睛凝视和停留”交互模型的难点</span><span class="sxs-lookup"><span data-stu-id="ee993-113">Challenges of the "eye-gaze and dwell" interaction model</span></span>
<span data-ttu-id="ee993-114">通常情况下，建议只在语音输入和手动输入都不可用的情况下使用基于停留的激活。</span><span class="sxs-lookup"><span data-stu-id="ee993-114">In general, we  recommend to only use dwell-based activations as a last fall-back if neither voice input nor hand input is available.</span></span> <span data-ttu-id="ee993-115">原因在于难以选择适当的停留时间。</span><span class="sxs-lookup"><span data-stu-id="ee993-115">The reason is that the choice of dwell time can be pretty tricky.</span></span> <span data-ttu-id="ee993-116">新手用户可以使用较长的停留时间，专家用户则希望快速且高效地浏览其整个体验。</span><span class="sxs-lookup"><span data-stu-id="ee993-116">Novice users are ok with longer dwell times, while expert users want to quickly and efficiently navigate through their experiences.</span></span> <span data-ttu-id="ee993-117">因此，难点在于如何根据用户的具体需求调整停留时间。</span><span class="sxs-lookup"><span data-stu-id="ee993-117">This leads to the challenge of how to adjust the dwell time to the specific needs of a user.</span></span>
<span data-ttu-id="ee993-118">如果停留时间太短，则会因为全息影像一直在对用户的眼睛凝视进行响应而导致用户感到精疲力尽。</span><span class="sxs-lookup"><span data-stu-id="ee993-118">If the dwell time is too short: The user may feel overwhelmed by having holograms reacht to their eye-gaze all the time.</span></span> <span data-ttu-id="ee993-119">如果停留时间太长，则会给用户造成体验太慢且易中断的感觉，因为用户必须长时间盯着目标。</span><span class="sxs-lookup"><span data-stu-id="ee993-119">If the dwell time is too long: The experience may feel too slow and interruptive as the user has to keep looking at targets for a long time.</span></span>

## <a name="design-recommendations"></a><span data-ttu-id="ee993-120">设计建议</span><span class="sxs-lookup"><span data-stu-id="ee993-120">Design recommendations</span></span>
<span data-ttu-id="ee993-121">建议对停留反馈使用双状态方法：</span><span class="sxs-lookup"><span data-stu-id="ee993-121">We recommend using a two-state approach for dwell feedback:</span></span>
1. <span data-ttu-id="ee993-122">初动延迟  ：当用户开始看着目标时，系统不应立即响应，否则可能会给用户带来不愉快的体验，导致用户精疲力尽。</span><span class="sxs-lookup"><span data-stu-id="ee993-122">*Onset delay*: When the user starts looking at a target, nothing should immediately happen as this may result in an unpleasant and overwhelming user experience.</span></span> <span data-ttu-id="ee993-123">这种情况下，我们会启动一个计时器，用于检测用户是在有意盯着该目标，还是仅仅瞟了它一眼。</span><span class="sxs-lookup"><span data-stu-id="ee993-123">Instead we start a timer to detect whether the user is intentionally staring at the target or merely skimming over it.</span></span>
2. <span data-ttu-id="ee993-124">启动停留反馈：  在确定用户是在有意盯着该目标以后，我们开始显示停留反馈，通知用户停留激活正在启动。</span><span class="sxs-lookup"><span data-stu-id="ee993-124">*Start dwell feedback:* After ensuring that the user is intentionally looking at the target, we start showing dwell feedback to inform the user that the dwell activation is being initiated.</span></span> <span data-ttu-id="ee993-125">在设定好临近度（即用户在注视而不是瞟着某个大型目标）的情况下，建议将初动时间设置为 150-250 毫秒。</span><span class="sxs-lookup"><span data-stu-id="ee993-125">We recommend an onset time of 150-250 ms in a given proximity (meaning the user is fixating vs. looking around on a large target).</span></span>  
3. <span data-ttu-id="ee993-126">持续反馈：  当用户持续看着目标时，显示一个连续进度指示器，这样用户就知道自己必须始终看着目标。</span><span class="sxs-lookup"><span data-stu-id="ee993-126">*Continuous Feedback:* While the user keeps looking at the target, show a continous progress indicator so that the user knows that they have to keep looking at the target.</span></span> <span data-ttu-id="ee993-127">具体说来，对于眼睛凝视输入，建议一开始显示一个较大的圆圈或球体，然后将其缩小，通过这种方式吸引用户的视觉注意力。 </span><span class="sxs-lookup"><span data-stu-id="ee993-127">In particular for eye-gaze input, we recommend _pulling in the user's visual attention_ by starting out with a bigger circle or sphere that contracts into a smaller version.</span></span> <span data-ttu-id="ee993-128">显示一个表示最终状态的指示器（小圆圈）是为了告知用户停留将何时结束。</span><span class="sxs-lookup"><span data-stu-id="ee993-128">Showing an indicator for the final state (small circle) helps to communicate to the user when the dwell will be finished.</span></span> <span data-ttu-id="ee993-129">示例图如下所示。</span><span class="sxs-lookup"><span data-stu-id="ee993-129">An example illustration is shown below.</span></span> 
4. <span data-ttu-id="ee993-130">完成：  如果用户一直注视该目标（又注视了 650-850 毫秒），则完成停留激活，选择被用户注视的目标。</span><span class="sxs-lookup"><span data-stu-id="ee993-130">*Finish:* If the user kept fixating the target (for another 650-850 ms), complete the dwell activation and select the looked-at target.</span></span>

![停留状态](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a><span data-ttu-id="ee993-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ee993-132">See also</span></span>
* [<span data-ttu-id="ee993-133">眼动跟踪</span><span class="sxs-lookup"><span data-stu-id="ee993-133">Eye tracking</span></span>](eye-tracking.md)
* [<span data-ttu-id="ee993-134">眼睛凝视和提交</span><span class="sxs-lookup"><span data-stu-id="ee993-134">Eye-gaze and commit</span></span>](gaze-and-commit-eyes.md)
* [<span data-ttu-id="ee993-135">凝视和提交</span><span class="sxs-lookup"><span data-stu-id="ee993-135">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ee993-136">凝视和停留</span><span class="sxs-lookup"><span data-stu-id="ee993-136">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="ee993-137">语音输入</span><span class="sxs-lookup"><span data-stu-id="ee993-137">Voice input</span></span>](voice-design.md)
