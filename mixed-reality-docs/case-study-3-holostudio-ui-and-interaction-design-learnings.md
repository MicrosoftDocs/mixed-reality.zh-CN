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
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>案例研究-3 HoloStudio UI 和交互设计知识

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8)是第一个适用于 HoloLens 的 Microsoft 应用程序。 因此, 我们必须为三维 UI 和交互设计创建新的最佳做法。 为此, 我们进行了大量用户测试、原型制作和试用和错误。

我们知道, 并非每个人都具有可供处理此类研究的资源, 因此我们的 Sr-1 设计人员 Marcus Ghaly 在开发 HoloStudio 关于应用程序的 UI 和交互设计方面, 还分享了三项知识。

## <a name="watch-the-video"></a>观看视频

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>问题 #1:用户不想四处移动其创建

我们最初在 HoloStudio 中将工作台设计成了一个矩形, 就像你在现实世界中看到的那样。 问题在于, 人们有经验的生存期, 告诉他们离开办公桌时仍停留在计算机上, 因此他们不会四处四处移动, 并从所有方面浏览3D 创建。

![HoloStudio dissuaded 用户在所有方面的移动和查看其创建的工作台的矩形设计。](images/rectangular-workbench-500px.jpg)

我们了解到了如何进行工作台循环, 以便不会有任何 "正面" 或不明确的位置。 测试这种情况时, 突然有人开始四处移动并浏览其创建。

![循环工作台设计鼓励用户围绕其创建进行演练。](images/circular-workbench-500px.jpg)

**我们学到的内容**

务必要考虑用户的舒适。 利用其物理空间是 HoloLens 的一项不错的功能, 不能使用其他设备。

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>问题 #2:模式对话框有时不在全息帧外

有时, 你的用户可能会从需要在应用中关注的内容中寻找不同的方向。 在电脑上, 你只需弹出一个对话框, 但如果在三维环境的人脸中执行此操作, 则可能会感觉到该对话框正在进行。 你需要它们来读取消息, 但其 instinct 是尝试从该消息中消失。 如果你正在玩游戏, 但在设计为工作的工具中, 这种反应会很好, 但它不是理想之选。

尝试使用几个不同的东西后, 我们最终会在对话框中使用 "思考气泡" 系统进行结算, 并添加了用户可在应用程序中需要关注的位置的 tendrils。 我们还进行了 tendrils 脉冲, 这暗示了一种方向性, 使用户了解到的位置。

!["思想气泡" 系统包含了一 tendrils, 这提供了一种方向, 使用户能够在应用程序中需要关注的位置。](images/thought-bubble-500px.jpg)

**我们学到的内容**

3D 中更难提醒用户需要注意的事项。 使用 "[音量](spatial-sound.md)"、"光线" 或 "想象" 等的 "注意" 主管, 可以让用户在需要的位置进行处理。

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>问题 #3:有时 UI 可能会被其他全息影像阻止

有时, 用户想要与全息图及其关联的 UI 控件交互, 但它们被阻止查看, 因为另一个全息图位于它们前面。 尽管我们正在开发 HoloStudio, 但我们使用了试用和错误来解决这个问题。

![如果与全息图关联的 UI 控件与与 HoloLens 一起使用的用户之间有另一个全息图, 就会被阻止。](images/ui-blocked-500px.jpg)

我们尝试将 UI 控件移动到离用户近的位置, 因此无法阻止该控件, 但发现用户在查看离您附近的某个控件时, 不太熟悉。 但是, 如果我们将控件移动到最靠近用户的最接近的全息图上, 则他们认为该控件已与应影响的全息图分离。

最终, 最终最终会使 UI 控件的出现, 并将其与用户的距离与其关联的全息图保持一致, 因此它们都可以连接起来。 这允许用户与控件交互, 即使它已被遮住。

![解决方案: 我们对 UI 控件进行了幻像, 这两者都允许与控件交互, 并使其感觉与它所影响的全息图相连接。](images/ghosting-ui-500px.jpg)

**我们学到的内容**

用户需要能够轻松访问 UI 控件 (即使它们已被阻止), 因此请找出方法, 以确保用户无论在何处都能完成任务, 无论他们在现实世界中的位置如何。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Sr-iov 设计器@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅
* [本能交互](interaction-fundamentals.md)

 
