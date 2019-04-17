---
title: 什么是全息图？
description: HoloLens 您可以查看和使用三维全息进行交互，对象所做的光线和声音中显示的周围世界。
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 HoloLens、 全息、 设计、 交互
ms.openlocfilehash: 5a6cc4df764b1f92f6bea2d7d6e6effe2164e4d6
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590161"
---
# <a name="what-is-a-hologram"></a>什么是全息图？

HoloLens 允许您创建**全息**、 对象所做的光线和声音中显示的周围，世界就像它们是真实的对象。 全息响应你[注视](gaze.md)，[手势](gestures.md)并[语音命令](voice-input.md)，并可以与之交互[实际表面](spatial-mapping.md)周围。 全息，您可以创建属于您的世界的数字对象。

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> 全息</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>一张全息图组成浅色和声音

全息该 HoloLens[呈现](rendering.md)直接放在用户的眼睛全息版的帧中显示。 全息将添加到您的世界，这意味着，您将看到显示灯和从周围的环境光的光。 HoloLens 不会从你自己，删除光，因此全息无法呈现颜色使用黑色。 相反，黑色的内容显示为透明效果。

全息可以具有许多不同的外观和行为。 一些实际也更加稳定，而有些则是卡通和 ethereal。 全息可以突出显示你环境中的功能，也可以在应用程序的用户界面中的元素。

![Holographic dog 在地板上的每个步骤](images/fang3-640px.jpg)

此外可以使全息[声音](spatial-sound.md)，这将显示为来自周围的环境中的特定位置。 在 HoloLens，听起来来自两个位于正上方您的头脑，同时不会覆盖它们的发言人。 显示与类似，演讲者是累加式的而不会阻止你的环境中的声音引入新的声音。

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>可以标记与您的世界中放置一张全息图

想一张全息图的特定位置后，你可以[放置](coordinate-systems.md)它准确地说那里世界上。 您向介绍围绕该全息图，它将显示相对于周围世界稳定。 如果您使用[空间的定位点](coordinate-systems.md#spatial-anchors)固定牢固地向该对象，系统可以甚至记住你中断的地方它时稍后返回。

![全息版构建 maquette 您坐在一个表](images/image5-640px.png)

某些全息改为的用户进行操作。 这些尾随全息定位本身相对于用户，无论他们向介绍。 您甚至可以选择将与你一张全息图一段时间，然后将它放在墙上后转到另一个房间。

**最佳做法**
* 某些情况下可能要求全息保持轻松容易被发现或整个体验可见。 有两种高级方法，这种类型的定位。 让我们称他们 **"显示锁定"** 并 **"正文禁止"**。
   * 显示锁定内容已按位置"锁定"到设备显示。 这是比较棘手的原因有多种，包括"clingyness"，使多个用户感到沮丧非自然感觉和想要"摇晃它。" 一般情况下，许多设计人员已找到更好的做法避免显示锁定内容。
   * 正文锁定的方法是 forgivable 得多。 正文锁定是一张全息图限于用户的主体或的视线移动矢量，但在 3d 空间中围绕用户定位。 许多体验已采用其中 hologram"紧跟"用户视线移动，这样用户就可以旋转其主体和浏览空间，而不会丢失全息图正文锁定的行为。 将合并延迟有助于感觉更自然的 hologram 移动。 例如，某些核心的 Windows 全息版操作系统的 UI 使用一种变体正文锁定时在用户打开其头后面，并简要、 类似于弹性的延迟的用户的视线移动。
* 将放全息图舒适地观看距离通常大约 1-2 米离开头。
* 提供的元素必须不断地在全息版的框架中，或当用户更改其角度来看，对一侧显示的内容进行动画处理，请考虑所用的偏移量。

**将全息放置在最佳的区域-1.25 m 和 5 分钟之间**

两种测定仪的最优，并体验会降低近获取从一个指示器。 处于越重要比一米以内的距离，定期将移动的深度的全息是更有可能会比静态全息出现问题。 请考虑适当地剪切或淡出你的内容时获取得太近，以免意外体验到 jar 用户。

![放置全息从用户的最佳距离。](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>与您和您的世界交互一张全息图

全息不是仅涉及浅色和声音;它们也是您的世界的活动部分。 在全息图和用一只手，手势的视线移动和一张全息图跟随你便可以开始。 语音命令向一张全息图，它可以进行回复。

![在现实生活摩托车正文拟合 holographic 摩托车设计](images/image8-640px.png)

全息实现不可能实现的其他位置的个人交互。 因为 HoloLens 知道其中位于世界，holographic 字符可以查询您直接在眼睛房间中四处走动。

一张全息图还可以使用周围的环境进行交互。 例如，您可以放置在表格上方 holographic 跳动的球。 然后，使用[敲击](gestures.md#air-tap)，观看球跳动式和使声音抵达表时。

此外可以通过现实世界对象封闭全息。 例如，通过一扇门和后面墙上，在视线之外，可能引导 holographic 字符。

**用于集成全息和现实世界的提示**
* 对齐到引力规则可让全息更轻松地与更可信。 例如：一开始 （& a） 在表上的花瓶置于 holographic 狗，而不是让他们在空间中浮动。
* 许多设计人员发现它们更加 believably 集成全息通过创建"负影子"hologram 坐在图面上。 它们通过围绕全息图地面上创建软发光然后减去从发光"影子"执行此操作。 软发光与集成在现实生活中光和阴影 grounds 全息图在环境中。

## <a name="a-hologram-is-whatever-you-dream-up"></a>无论您想到一张全息图是

作为 holographic 开发人员，您可以中断你的创造力超出 2D 屏幕和到周围世界的能力。 将会什么*您*生成？

![在起居室 holographic 虚部世界](images/designoverview.jpg)

## <a name="see-also"></a>请参阅
* [空间声音](spatial-sound.md)
* [颜色、 光线和材料](color,-light-and-materials.md)
