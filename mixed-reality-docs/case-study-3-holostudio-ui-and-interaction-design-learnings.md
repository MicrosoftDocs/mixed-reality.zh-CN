---
title: 案例研究-3 HoloStudio UI 和交互设计知识
description: HoloStudio UI 和交互设计知识
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、HoloStudio、Windows Mixed Reality
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974821"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="eba4d-104">案例研究-3 HoloStudio UI 和交互设计知识</span><span class="sxs-lookup"><span data-stu-id="eba4d-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="eba4d-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8)是第一个适用于 HoloLens 的 Microsoft 应用程序。</span><span class="sxs-lookup"><span data-stu-id="eba4d-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="eba4d-106">因此, 我们必须为三维 UI 和交互设计创建新的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="eba4d-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="eba4d-107">为此, 我们进行了大量用户测试、原型制作和试用和错误。</span><span class="sxs-lookup"><span data-stu-id="eba4d-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="eba4d-108">我们知道, 并非每个人都具有可供处理此类研究的资源, 因此我们的 Sr-1 设计人员 Marcus Ghaly 在开发 HoloStudio 关于应用程序的 UI 和交互设计方面, 还分享了三项知识。</span><span class="sxs-lookup"><span data-stu-id="eba4d-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="eba4d-109">观看视频</span><span class="sxs-lookup"><span data-stu-id="eba4d-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="eba4d-110">问题 #1:用户不想四处移动其创建</span><span class="sxs-lookup"><span data-stu-id="eba4d-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="eba4d-111">我们最初在 HoloStudio 中将工作台设计成了一个矩形, 就像你在现实世界中看到的那样。</span><span class="sxs-lookup"><span data-stu-id="eba4d-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="eba4d-112">问题在于, 人们有经验的生存期, 告诉他们离开办公桌时仍停留在计算机上, 因此他们不会四处四处移动, 并从所有方面浏览3D 创建。</span><span class="sxs-lookup"><span data-stu-id="eba4d-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![HoloStudio dissuaded 用户在所有方面的移动和查看其创建的工作台的矩形设计。](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="eba4d-114">我们了解到了如何进行工作台循环, 以便不会有任何 "正面" 或不明确的位置。</span><span class="sxs-lookup"><span data-stu-id="eba4d-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="eba4d-115">测试这种情况时, 突然有人开始四处移动并浏览其创建。</span><span class="sxs-lookup"><span data-stu-id="eba4d-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![循环工作台设计鼓励用户围绕其创建进行演练。](images/circular-workbench-500px.jpg)

<span data-ttu-id="eba4d-117">**我们学到的内容**</span><span class="sxs-lookup"><span data-stu-id="eba4d-117">**What we learned**</span></span>

<span data-ttu-id="eba4d-118">务必要考虑用户的舒适。</span><span class="sxs-lookup"><span data-stu-id="eba4d-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="eba4d-119">利用其物理空间是 HoloLens 的一项不错的功能, 不能使用其他设备。</span><span class="sxs-lookup"><span data-stu-id="eba4d-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="eba4d-120">问题 #2:模式对话框有时不在全息帧外</span><span class="sxs-lookup"><span data-stu-id="eba4d-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="eba4d-121">有时, 你的用户可能会从需要在应用中关注的内容中寻找不同的方向。</span><span class="sxs-lookup"><span data-stu-id="eba4d-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="eba4d-122">在电脑上, 你只需弹出一个对话框, 但如果在三维环境的人脸中执行此操作, 则可能会感觉到该对话框正在进行。</span><span class="sxs-lookup"><span data-stu-id="eba4d-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="eba4d-123">你需要它们来读取消息, 但其 instinct 是尝试从该消息中消失。</span><span class="sxs-lookup"><span data-stu-id="eba4d-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="eba4d-124">如果你正在玩游戏, 但在设计为工作的工具中, 这种反应会很好, 但它不是理想之选。</span><span class="sxs-lookup"><span data-stu-id="eba4d-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="eba4d-125">尝试使用几个不同的东西后, 我们最终会在对话框中使用 "思考气泡" 系统进行结算, 并添加了用户可在应用程序中需要关注的位置的 tendrils。</span><span class="sxs-lookup"><span data-stu-id="eba4d-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="eba4d-126">我们还进行了 tendrils 脉冲, 这暗示了一种方向性, 使用户了解到的位置。</span><span class="sxs-lookup"><span data-stu-id="eba4d-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

!["思想气泡" 系统包含了一 tendrils, 这提供了一种方向, 使用户能够在应用程序中需要关注的位置。](images/thought-bubble-500px.jpg)

<span data-ttu-id="eba4d-128">**我们学到的内容**</span><span class="sxs-lookup"><span data-stu-id="eba4d-128">**What we learned**</span></span>

<span data-ttu-id="eba4d-129">3D 中更难提醒用户需要注意的事项。</span><span class="sxs-lookup"><span data-stu-id="eba4d-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="eba4d-130">使用 "[音量](spatial-sound.md)"、"光线" 或 "想象" 等的 "注意" 主管, 可以让用户在需要的位置进行处理。</span><span class="sxs-lookup"><span data-stu-id="eba4d-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="eba4d-131">问题 #3:有时 UI 可能会被其他全息影像阻止</span><span class="sxs-lookup"><span data-stu-id="eba4d-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="eba4d-132">有时, 用户想要与全息图及其关联的 UI 控件交互, 但它们被阻止查看, 因为另一个全息图位于它们前面。</span><span class="sxs-lookup"><span data-stu-id="eba4d-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="eba4d-133">尽管我们正在开发 HoloStudio, 但我们使用了试用和错误来解决这个问题。</span><span class="sxs-lookup"><span data-stu-id="eba4d-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![如果与全息图关联的 UI 控件与与 HoloLens 一起使用的用户之间有另一个全息图, 就会被阻止。](images/ui-blocked-500px.jpg)

<span data-ttu-id="eba4d-135">我们尝试将 UI 控件移动到离用户近的位置, 因此无法阻止该控件, 但发现用户在查看离您附近的某个控件时, 不太熟悉。</span><span class="sxs-lookup"><span data-stu-id="eba4d-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="eba4d-136">但是, 如果我们将控件移动到最靠近用户的最接近的全息图上, 则他们认为该控件已与应影响的全息图分离。</span><span class="sxs-lookup"><span data-stu-id="eba4d-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="eba4d-137">最终, 最终最终会使 UI 控件的出现, 并将其与用户的距离与其关联的全息图保持一致, 因此它们都可以连接起来。</span><span class="sxs-lookup"><span data-stu-id="eba4d-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="eba4d-138">这允许用户与控件交互, 即使它已被遮住。</span><span class="sxs-lookup"><span data-stu-id="eba4d-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![解决方案: 我们对 UI 控件进行了幻像, 这两者都允许与控件交互, 并使其感觉与它所影响的全息图相连接。](images/ghosting-ui-500px.jpg)

<span data-ttu-id="eba4d-140">**我们学到的内容**</span><span class="sxs-lookup"><span data-stu-id="eba4d-140">**What we learned**</span></span>

<span data-ttu-id="eba4d-141">用户需要能够轻松访问 UI 控件 (即使它们已被阻止), 因此请找出方法, 以确保用户无论在何处都能完成任务, 无论他们在现实世界中的位置如何。</span><span class="sxs-lookup"><span data-stu-id="eba4d-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="eba4d-142">关于作者</span><span class="sxs-lookup"><span data-stu-id="eba4d-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="eba4d-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="eba4d-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="eba4d-144">Sr-iov 设计器@Microsoft</span><span class="sxs-lookup"><span data-stu-id="eba4d-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="eba4d-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="eba4d-145">See also</span></span>
* [<span data-ttu-id="eba4d-146">本能交互</span><span class="sxs-lookup"><span data-stu-id="eba4d-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
