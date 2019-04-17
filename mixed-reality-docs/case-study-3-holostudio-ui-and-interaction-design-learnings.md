---
title: 案例研究-3 HoloStudio UI 和交互设计知识
description: HoloStudio UI 和交互设计经验
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，HoloStudio，Windows 混合现实
ms.openlocfilehash: 217c489fed3c0588dae1c2753db6ba15da3522c8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592639"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>案例研究-3 HoloStudio UI 和交互设计知识

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) HoloLens 的是第一个 Microsoft 应用程序之一。 因此，我们需要创建新 3d UI 的最佳做法和交互设计。 我们通过大量的用户测试、 原型制作和试用和错误。

我们知道，并非每个人都具有其可供使用，来进行研究此类的资源，因此，我们必须我们高级全息版的设计器，Marcus Ghaly 共享三件事我们了解到有关 HoloLens 应用的 UI 和交互设计 HoloStudio 开发的过程。

## <a name="watch-the-video"></a>观看视频

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>问题 #1:用户不想要移动其作品

我们最初设计中 HoloStudio workbench 为一个矩形，更像你会发现现实世界中。 问题在于人们的体验，告知他们继续仍时它们坐在桌旁或工作计算机前状态，以便它们并不移动围绕在 workbench 并从所有边探索其 3D 创建的生存期。

![在 workbench 中 HoloStudio 矩形设计 dissuaded 中四处移动，并查看所有边从其创建的用户。](images/rectangular-workbench-500px.jpg)

我们的见解，以使 workbench 舍入，以便没有任何"前端"或清除已假定以突出显示的位置。 当我们测试表明时，突然人开始四处移动和其自己探索其作品。

![循环 workbench 设计鼓励用户一直四处其作品。](images/circular-workbench-500px.jpg)

**我们了解到的内容**

始终为思考一下什么是熟练的用户。 充分利用其物理空间是 HoloLens 和不能与其他设备做的事情很酷的功能。

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>问题 #2:模式对话框有时不 holographic 帧

有时，可能需要其关注应用程序中的不同方向从某些对象中查找你的用户。 在 PC 上，只是弹出可以启动一个对话框，但如果某人的人脸在 3D 环境中执行此操作，它可以感觉对话框获取按自己的方式。 你需要它们以读取消息，但其想到的是尝试摆脱它。 如果您正在玩游戏，但在设计工作的一种工具，它是不太理想，这种反应是很好。

之后尝试几个不同的事物，我们最后决定使用我们的对话框的"认为气泡"系统和添加 tendrils，用户可以通过到我们的应用程序中需要其关注的位置。 我们还进行隐式的方向性的意义上，以便用户知道到哪儿去 tendrils pulse。

!["认为气泡"系统包含闪烁 tendrils 提供某种意义上的方向，从而导致其关注其中需要在应用中的用户。](images/thought-bubble-500px.jpg)

**我们了解到的内容**

会在 3D 中的内容所需的要多加注意，警告用户非常困难。 如使用关注主管[空间声音](spatial-sound.md)、 浅色大气，或考虑冒泡，可能会导致用户他们需要为。

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>问题 #3:有时 UI 可能会阻塞由其他全息

有些的时候，当用户想要与一张全息图和其关联的用户界面控件进行交互，但它们会阻止视图，因为另一个全息图是在它们的前面。 尽管我们已开发 HoloStudio，我们用于试验和错误发送给解决方案进行这。

![如果它与用户戴上 HoloLens 之间的另一个全息图，一张全息图与关联的 UI 控件可能被阻止。](images/ui-blocked-500px.jpg)

我们尝试移动到用户的 UI 控件更接近，因此无法获取阻止，但找到它并不熟练的用户查看时同时查看远了一张全息图已接近您的控件。 如果，但是，我们移动到用户控件最接近全息图的前面，他们认为像分离的全息图，应会影响从。

我们最后最终重像 UI 控件，并将其放相同距离时从用户作为全息图相关联，以便它们都认为已连接。 这允许用户与控件交互，即使已被遮盖。

![解决方案： 我们幻像 UI 控件，同时允许与控件交互，并使其可以连接到的全息图，那么这影响。](images/ghosting-ui-500px.jpg)

**我们了解到的内容**

用户需要能够轻松地访问 UI 控件，即使它们已被阻止，因此需弄清方法，以确保用户可以完成其任务，无论其全息现实世界中。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>部门高级 Holographic 设计器 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅
* [交互基础知识](interaction-fundamentals.md)

 
