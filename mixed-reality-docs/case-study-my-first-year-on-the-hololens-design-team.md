---
title: 案例研究-我在 HoloLens 设计团队中的第一年
description: 当我在2016年1月加入 HoloLens 设计团队时，我从 2D flatland 到三维世界的旅程开始使用。
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，HoloLens，设计，编辑，个人
ms.openlocfilehash: 47ed5edd58846687daa4242f7bdbc85dae0f5255
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436603"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>案例研究-我在 HoloLens 设计团队中的第一年

当我在2016年1月加入 HoloLens 设计团队时，我从 2D flatland 到三维世界的旅程开始使用。 在加入团队之前，我在三维设计方面的体验非常少。 这就像是从单个步骤开始，这就是谚语的一段时间，只不过第一步是 leap，

![从2D 到3D 的](images/2D_to_3D-800px.gif)<br>
*从2D 到3D 的*

> *"我认为我一直在不知道如何推动汽车的情况下，跳转到驱动程序的座位。我曾恐惧，但却非常专注。 "*<br>
> — Hae 金

在过去一年中，我选择了快速的技能和知识，但仍有许多经验。 在这里，我使用视频教程撰写了4个观察，其中介绍了从2D 到三维交互设计器的转换。 我希望我的体验会使其他设计人员能够使用这一三维。

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>令人非常再见的帧。 Hello 空间/diegetic UI

无论何时设计海报、杂志、网站或应用程序屏幕，定义的帧（通常是矩形）都是每个问题的常量。 除非你要在 HoloLens 或其他 VR 设备中阅读此文章，否则你将从外部通过2D 屏幕安全地在帧内*查看此*文章。 内容是您的外部内容。 但是，混合现实头戴式耳机*消除了帧*，因此你在内容空间中，并在内容空间内查看内容。

我在概念上了解到这一点，但在开始时，我犯了一个错误，只是将2D 思维转移到了3D 空间。 显然，这不是很好，因为3D 空间具有自己的独特属性，如视图更改（基于用户的头移动）和[用户舒适的不同要求](https://www.youtube.com/watch?v=-606oZKLa_s/)（基于设备的属性和使用者的人员）。 例如，在 2D UI 设计空间中，将 UI 元素锁定到屏幕的角是一种非常常见的模式，但这种 HUD （Head 显示）样式 UI 在 MR/VR 体验中并不自然。它阻碍用户浸入式空间，导致用户 discomfort。 这就像在眼镜上有一个令人讨厌的灰尘粒子，因为您中断了。 随着时间的推移，我已经了解到，在三维空间中放置内容更自然，并添加了正文锁定行为，使内容以相对固定的距离在用户关注。

![正文锁定](images/bodylockedtagalong.gif)<br>
*正文-锁定*

<br>

![世界锁定](images/worldlocked.gif)<br>
*世界锁定*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>片段：大 Diegetic UI 的示例

[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)是[Asobo Studio](https://www.asobostudio.com/) for HoloLens 开发的第一人犯罪 thriller，它展示了一个很好的 Diegetic UI。 在此游戏中，用户成为了一个主字符，这是一种试图解决神秘的侦探。 在用户的物理空间中解决这个神秘的 get 分散的 pivotal 线索，通常是嵌入在虚构的对象中，而不是在自己的内部嵌入。 与正文锁定的 UI 相比，此 diegetic UI 的可发现性更低，因此 Asobo 团队巧妙使用了许多提示，其中包括虚拟字符看起来、声音、光和参考线（如指向线索位置的箭头），以吸引用户的注意力。

![片段-Diegetic UI 示例](images/fragments-game-example-1.jpg)<br>
*片段-Diegetic UI 示例*

### <a name="observations-about-diegetic-ui"></a>有关 diegetic UI 的观察

空间 UI （正文锁定和世界锁定）和 diegetic UI 具有各自的优点和缺点。 我鼓励设计人员尽可能多地尝试 MR/VR 应用，并为各种 UI 定位方法开发自己的了解和差异。

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Skeuomorphism 和神奇交互的返回

Skeuomorphism，模仿现实世界对象的形状的数字接口在设计行业中的过去5–7年一直为 "uncool"。 当 Apple 最终在 iOS 7 中提供了平面设计方式时，似乎 Skeuomorphism 最终就会成为接口设计方法。 不过，在市场上，新的媒体（MR/VR 耳机）到达市场，似乎 Skeuomorphism 再次返回。 : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>作业模拟器： skeuomorphic VR 设计的示例

[作业模拟器](https://jobsimulatorgame.com/)是 skeuomorphic VR 设计的最常见示例之一，由[Owlchemy 实验室](https://owlchemylabs.com/)开发的古怪游戏。 在此游戏中，播放机将被传输到将来，其中，机器人会将其替换为在以下四个不同作业之一中执行常见任务的内容：自动 Mechanic、Gourmet Chef、商店员工

Skeuomorphism 的好处是显而易见的。 此游戏中熟悉的环境和对象可帮助新的 VR 用户感觉更舒适，并在虚拟空间中呈现。 它还通过将熟悉的知识和行为与对象及其相应的物理反应关联起来，使它们在控制之下。 例如，为了给杯杯杯杯，人们只需走到咖啡机，按下按钮，抓住杯控把手，就像在现实世界中那样倾斜。

![作业模拟器](images/job-simulator.gif)<br>
*作业模拟器*

因为 MR/VR 仍是开发媒介，所以必须使用一定程度的 skeuomorphism 来释义 MR/VR 技术，并将其引入世界各地更大的受众。 此外，对于特定类型的应用程序（如外科模拟或飞行模拟），使用 skeuomorphism 或现实表示可能会很有用。 由于这些应用程序的目标是开发和优化可以直接应用于现实世界的特定技能，因此，对现实世界的模拟越接近，该知识就越有限制。

请记住，skeuomorphism 只是一种方法。 MR/VR 世界的潜力远远超过这一点，设计人员应尽力创建神奇的超自然交互，这是在 MR/VR 世界中独特的新实用。 开始时，请考虑向普通对象添加神奇，以使用户能够满足其根本需要，包括 teleportation 和 omniscience。

![Doraemon 的神奇门（left）和 Ruby slippers （right）](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon 的神奇门（左侧）和 ruby slippers （右）*

### <a name="observations-about-skeuomorphism-in-vr"></a>在 VR 中了解 skeuomorphism

从 Doraemon 的 "Anywhere 门" 中的 "Oz" 的向导中的 "Ruby Slippers" 到 Harry 哈里波特中的 "Maurader 地图"，其中包含神奇 power abound 的普通对象示例。 这些神奇对象可帮助我们直观显示现实世界和理想之处之间的连接。 请记住，设计神奇或 surreal 对象时，需要在功能和娱乐之间实现平衡。 请注意，创建纯粹神奇的东西只是为了新奇。

## <a name="understanding-different-input-methods"></a>了解不同的输入方法

当我为2D 中型设计时，我不得不专注于输入的触摸、鼠标和键盘交互。 在 MR/VR 设计领域，我们的主体成为接口，用户可以使用更广泛的输入方法：包括语音、注视、手势、 [6 dof 控制器](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)和手套，它们具有更直观的与虚拟对象的直接连接。

HoloLens](images/inputs.jpg) ![可用输入<br>
*HoloLens 中的可用输入*

> *"一切都最适用于某些事情，但对于其他事情，这是最差的。"*<br>
> -[帐单 Buxton](https://www.billbuxton.com/)

例如，在 HMD 设备上使用裸机和相机传感器进行的手势输入使用户不会拿住控制器或戴 sweaty 手套，但频繁使用可能会导致物理疲劳（gorilla）。 此外，用户必须在视线内保持其手。如果相机看不到手，则无法使用手。

语音输入非常适合遍历复杂的任务，因为它允许用户通过一个命令（例如，"向我显示 Laika studio 所做的电影"）来剪切嵌套菜单，而且在与其他模态结合使用时（例如，"面部 me" 命令将定向到用户正在查看用户的全息图）。 但是，语音输入在干扰环境中可能无法正常工作，或者可能不适合在非常安静的空间中使用。

除了手势和语音外，手持跟踪控制器（例如，Oculus 触控、Naopak 等）是非常流行的输入方法，因为它们易于使用、准确、利用人员的[proprioception](https://en.wikipedia.org/wiki/Proprioception)，并提供被动 haptic 提示。不过，这些优势的代价是不能成为实际的，而是使用完全 finger 跟踪。

![Senso （Left）和 Manus VR （Right）](images/senso-and-manus-vr.jpg)<br>
*Senso （Left）和 Manus VR （Right）*

与控制器一样，与控制器相比，手套还能再次发展，这归功于尊敬的尊敬。 最近，大脑输入已经开始通过将 EEG 或 EMG 传感器集成到耳机（例如[MINDMAZE VR](https://www.mindmaze.com/)）来获得虚拟环境的界面。

### <a name="observations-about-input-methods"></a>有关输入方法的观察

这只是一种为 MR/VR 市场提供的输入设备示例。 在行业成熟并同意最佳实践之前，他们将继续增加。 在此之前，设计人员应始终知道新的输入设备，并在特定的项目的特定输入方法中精通。 设计人员需要在限制范围内寻找创造性的解决方案，同时还能在设备上寻找优势。

## <a name="sketch-the-scene-and-test-in-the-headset"></a>草拟耳机中的场景和测试

当我在2D 中工作时，我主要只是要绘出内容。 但是，在混合现实空间中，这并不是足够的。 我必须草拟整个场景，以便更好地想象用户和虚拟对象之间的关系。 为了帮助我的空间思维，我开始在[电影院 4d](https://www.maxon.net/en/products/cinema-4d/overview/)中草拟场景，有时为[Maya](https://www.autodesk.com/products/maya/overview/)中的原型创建简单的资产。 在加入 HoloLens 团队之前，我从未使用过任何一种程序，但我仍然是一新手，但使用这些三维程序一定会帮助我熟悉新术语，如[着色器](https://en.wikipedia.org/wiki/Shader)和[IK （反运动学）](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)。

**"无论是在三维中绘制场景的紧密关系，耳机中的实际体验几乎不会与草图相同。这就是在目标耳机中测试场景很重要的原因。 "— Hae 金**

对于 HoloLens 原型编写，我尝试在[混合现实教程](tutorials.md)中启动所有教程。 然后我开始开始与 Microsoft 为开发人员提供的[HoloToolkit](https://github.com/Microsoft/HoloToolkit-Unity/) ，以加速全息应用程序的开发。 当我停滞了某些东西后，我将我的问题发布到了[HoloLens 问题 & 答案论坛](https://forums.hololens.com/categories/questions-and-answers/)。

在获取对 HoloLens 原型的基本了解后，我想要自行实现其他非普通人原型。 我制作了一个视频教程，介绍如何使用 HoloLens 开发一个简单的 projectile。 我简要介绍了基本的概念，因此，即使您在 HoloLens 开发中没有经验，您也应该能够继续操作。

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*我为非编程人员提供了这个简单的教程。*

对于 VR 原型编写，我采用了[Vr 开发学校](https://learn.vrdev.school/)的课程，并在 Lynda.com 中[为虚拟现实拍摄了3d 内容](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/)。 使用 VR 开发人员，我们可以更深入地了解如何编写代码和 Lynda 课程，为我提供了创建用于 VR 的资产的简短介绍。

## <a name="take-the-leap"></a>采用 leap

一年前，我觉得这一切都有点复杂。 现在，我可以告诉您此操作是否值得100%。 先生/VR 仍非常年轻，有很多有趣的等待实现。 我觉得有些灵感，幸运可以在设计未来的一小部分中发挥作用。 我希望将我的旅程加入三维空间！

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae 金</b><br>UX 设计器 @Microsoft</td>
</tr>
</table>

 
