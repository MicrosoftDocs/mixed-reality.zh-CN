---
title: 案例研究-在 HoloLens 上的我第一年设计团队
description: 从 2D flatland 向 3D 世界开始时我加入了 HoloLens 设计团队在 2016 年 1 月，我经历。
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality HoloLens，设计、 编辑，个人
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873954"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>案例研究-在 HoloLens 上的我第一年设计团队

从 2D flatland 向 3D 世界开始时我加入了 HoloLens 设计团队在 2016 年 1 月，我经历。 加入团队之前, 我很少体验 3D 设计中。 是中文句俗语有关从一个步骤中，但在我的示例的第一步是闰年的千位英里之旅 ！

![从 2D 采用 3D Leap](images/2D_to_3D-800px.gif)<br>
*从 2D 采用 3D leap*

> *"我认为，就好像具有跳转到主导地位而不必知道如何驾驶汽车。我已过载并将被困难所吓倒，但非常有针对性。"*<br>
> — Hae Jin Lee

在上一年中，我还获得的技能和知识可以但我仍有许多东西需要学习速度一样快。 在这里，我编写了 4 个观测值向上记录从 2D 我过渡到三维交互设计人员的视频教程。 我希望我的经验会一直激励其他设计器将飞跃到 3D。

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>再见帧。 Hello 空间 / diegetic UI

每当我设计海报、 杂志、 网站或应用屏幕，在定义的范围 （通常是一个矩形） 时的每个问题的常量。 除非您阅读此文章 HoloLens 或其他 VR 设备中的，您都*从外部看一下这*通过安全地在框架内受保护的 2D 屏幕。 内容不属于你。 但是，混合现实耳机*消除了在帧*，因此你是在内容的空间中，查找并且遍历从内部扩展的内容。

我从概念上讲，理解这一点，但一开始我犯了一个只需将 2D 考虑转移到 3D 空间。 这显然不起作用也因为 3D 空间具有其自己唯一的属性，如视图更改 （基于用户的磁头运动） 和[用户舒适的不同要求](https://www.youtube.com/watch?v=-606oZKLa_s/)（基于设备和使用人类的属性它们）。 例如，在 2D UI 设计空间中，锁定到屏幕的角的 UI 元素是一种非常常见模式，但此 HUD （平视显示） 样式用户界面并不认为自然 MR/VR 体验; 中它会妨碍用户的深入探讨到空间并导致用户不适。 它就像迫切若要消除您眼镜上有令人讨厌的灰尘粒子。 随着时间推移，我了解到它感觉更自然，若要在三维空间中定位内容，并添加使相对固定的距离上的用户的内容遵循的正文锁定行为。

![Body-locked](images/bodylockedtagalong.gif)<br>
*Body-locked*

<br>

![World-locked](images/worldlocked.gif)<br>
*World-locked*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>片断中：下面举例说明 Diegetic 的好用 UI

[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)，由开发第一个人犯罪打发[Asobo Studio](http://www.asobostudio.com/)对于 HoloLens 演示很好的 Diegetic UI。 在此游戏中，用户将成为主要的字符，侦探来解决神秘。 Pivotal 的线索来解决这道谜题获取散布在用户的物理空间中嵌入虚构对象内，而不是现有靠自己，通常情况下。 UI 往往是比正文锁定 UI，变得难于发现的因此 Asobo 团队巧妙地使用多个提示，包括虚拟字符的视线移动方向、 声音、 灯光和参考线 （例如，箭头指向线索的位置） 此 diegetic 获取用户的注意力。

![片段-Diegetic UI 示例](images/fragments-game-example-1.jpg)<br>
*片段-Diegetic UI 示例*

### <a name="observations-about-diegetic-ui"></a>有关 diegetic UI 的观测值

空间 UI （正文锁定和世界锁定） 和 diegetic UI 具有其自己的优势和劣势。 我建议尝试尽可能多 MR/VR 应用，也可以开发适用于定位方法的各种 UI 自己了解和之后的设计器。

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>返回的低劣和神奇的交互

低劣，数字接口，以模拟现实世界对象的形状已"uncool"过去 5 – 7 年设计行业中。 最后，Apple 在 iOS 7 中赋予平面的设计方式，当，看起来低劣已作为一种接口设计方法，最后失效。 但是，一个新的媒体，MR/VR 耳机到达市场并看起来像低劣再次返回是。 : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>作业模拟器：Skeuomorphic VR 设计的示例

[作业模拟器](http://jobsimulatorgame.com/)，由一个古怪的游戏开发[Owlchemy 实验室](https://owlchemylabs.com/)是 skeuomorphic VR 设计的最受欢迎示例之一。 在此游戏，玩家传输未来其中机器人将人类和人类访问艺术馆把世界遇到什么会觉得执行常见任务的一个四个不同的作业：自动的机修工保养、 Gourmet Chef、 存储分配器或办公室工作人员。

低劣的好处是清除。 熟悉的环境和此游戏中的对象帮助新 VR 用户感觉更舒适和虚拟空间中存在。 它还让他们感觉像在控件中通过将熟悉的知识和行为与对象和其相应的物理反应相关联。 例如，要喝杯咖啡，人们只需引导到咖啡机、 按下按钮、 抓住杯控点和针对进嘴里进行倾斜，像现实世界中一样。

![作业模拟器](images/job-simulator.gif)<br>
*作业模拟器*

由于 MR/VR 仍然是开发中，则需要以阐明 MR/VR 技术并引入到世界各地更广泛的受众使用一定低劣。 此外，使用低劣或实际表示形式可能会为特定类型的应用程序，如修改或飞行模拟非常有用。 由于这些应用程序的目的是培养和精通可直接应用在现实生活中的特定技能，模拟越接近实际情况下，越转让知识是。

请记住该低劣是只有一个方法。 MR/VR 世界可能是要远远高于，和设计人员应该努力创建神奇超自然交互 — MR/VR 世界中是唯一可能的新提示。 首先，请考虑添加到普通对象以使用户能够满足他们的基本需求的神奇的强大功能 — 包括 teleportation 和 omniscience。

![Doraemon 的神奇门 （左） 和 Ruby slippers(right)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon 的神奇门 （左） 和 ruby slippers(right)*

### <a name="observations-about-skeuomorphism-in-vr"></a>有关在 VR 低劣的观测值

从"任何位置门"Doraemon，到哈里波特中的"Maurader 的映射"的 Oz 向导中的"Ruby 鞋"中的神奇功能强大的普通对象示例很多常用小说中。 这些神奇的对象帮助我们形象地现实世界和绝妙之处是什么和可能的之间的连接。 请记住，神奇或 surreal 在设计时对象，其中一个需要功能和娱乐之间取得平衡。 请注意创建的内容只是为新奇的起见纯粹神奇的诱惑。

## <a name="understanding-different-input-methods"></a>了解不同输入的方法

我设计的 2D 媒体，我需要专注于触摸、 鼠标和键盘交互输入的清晰度。 在 MR/VR 设计领域，我们正文将成为接口和用户都可以使用更广泛的选择的输入方法： 包括语音、 提供注视、 手势时， [6 dof 控制器](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)，并提供更直观且直接连接的手套使用虚拟对象。

![HoloLens 中可用的输入](images/inputs.jpg)<br>
*HoloLens 中可用的输入*

> *"所有内容是某些内容，最好和最差的其他内容。"*<br>
> — [Bill Buxton](https://www.billbuxton.com/)

例如，输入 HMD 设备上使用裸机手和相机传感器的手势释放用户手动从保存控制器或戴上 sweaty 手套，但频繁使用可能会导致物理疲劳 （a.k.a 大猩猩手臂）。 此外，用户必须保留他们手中直通;如果相机不能看到手中，不能使用手中。

语音输入很好地遍历复杂的任务，因为它允许用户通过用一个命令的嵌套菜单剪切 （例如，"向我显示电影所做的 Laika studio。"） 和也非常经济实惠的方案与其他模式结合使用时 (例如，"我遇到"命令指导全息图用户正在通过向用户）。 但是，语音输入可能无法在杂乱无章的环境中，或可能不适当的非常静默空间中。

除了手势和语音，手持跟踪控制器 （例如，Oculus 触摸，欢跃等） 有非常流行的输入的法，因为它们是易于使用、 准确的利用人员[proprioception](https://en.wikipedia.org/wiki/Proprioception)，并提供被动 haptic 提示。但是，这些优势就会但代价是无法进行裸机手，并使用完整的手指跟踪。

![Senso （左） 和 Manus VR(Right)](images/senso-and-manus-vr.jpg)<br>
*Senso （左） 和 Manus VR （右）*

虽然不一样为控制器流行，手套正在向再次感谢 MR/VR 批。 最近，大脑/考虑输入已开始获得动力虚拟环境的接口作为通过集成到耳机 EEG 或 EMG 传感器 (例如， [MindMaze VR](http://www.mindmaze.com/))。

### <a name="observations-about-input-methods"></a>有关输入法的观测值

这些是仅针对 MR/VR 市场中可用的输入设备的示例。 它们将继续任其扩增直到行业日趋成熟，并同意后最佳实践。 到那时，设计人员应保持关注的新输入设备和精通其特定项目的特定输入方法。 设计器需要寻找创造性的解决方案内限制，同时还播放到设备的优势。

## <a name="sketch-the-scene-and-test-in-the-headset"></a>草绘场景和耳机测试

当我在 2D 中，我主要草绘的内容。 但是，在混合的现实没有足够的空间。 我需要简要地描绘出整个场景中，从而更好地假设用户与虚拟对象之间的关系。 为了帮助我空间的考虑，我开始草图场景[影院 4d](https://www.maxon.net/en/products/cinema-4d/overview/)和有时会创建用于原型制作中的简单资产[Maya](http://www.autodesk.com/products/maya/overview/)。 我加入 HoloLens 团队之前永远不会使用这两个程序和我仍是个新手，但使用这些 3D 程序肯定帮助我熟悉新术语中，如[着色器](https://en.wikipedia.org/wiki/Shader)和[IK （反转运动学）](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)。

**"无论紧密程度我草绘出在 3D 场景，耳机的实际体验是几乎永远不会与该草图相同。这就是为什么务必测试场景中目标耳机。"— Hae Jin Lee**

HoloLens 原型制作、 我尝试在所有教程[混合现实教程](tutorials.md)启动。 然后我开始研究[HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) ，Microsoft 提供了面向开发人员加快开发全息版的应用程序。 当我遇到问题的内容时，我发布到我的问题[HoloLens 问题和答案论坛](https://forums.hololens.com/categories/questions-and-answers/)。

获取基本了解 HoloLens 原型制作之后, 我想要使其他非编码人员，他们自己的原型。 因此，我进行视频的本教程演示如何开发使用 HoloLens 简单 projectile。 我简要甚至如果 HoloLens 开发中有零个经验，您应该能够跟着介绍一起操作说明的基本概念。

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*我进行非程序员像我一样此简单教程。*

我 VR 原型制作、 参加课程[VR 开发学校](http://learn.vrdev.school/)，还需要花费[3D 内容创建的虚拟现实](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/)在 Lynda.com 处。 VR 开发学校提供我的详细信息中编写代码的深度知识和 Lynda 课程提供我为 VR 创建资产的很好简短介绍。

## <a name="take-the-leap"></a>需要 leap

一年前，我认为这是让人有点不知所措等。 现在，我可以告诉您，它是值得的 100%。 MR/VR 仍很年轻的介质并且有这么多有趣的可能性等待实现。 我认为灵感，并幸运能播放中的未来的一小部分。 我希望将加入我到 3D 空间的旅程上 ！

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>UX 设计人员 @Microsoft</td>
</tr>
</table>

 
