---
title: 案例研究-使用稳定平面以减少 holographic 动荡
description: 使用稳定平面以减少 holographic 动荡
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全息、 稳定、 案例研究
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590100"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>案例研究-使用稳定平面以减少 holographic 动荡

使用全息可能很棘手。 这一事实可以移动你的空间并查看你全息从所有不同的角度提供无法获取正常的计算机屏幕的浸入式的级别。 让这些全息保留不动并查看实际是通过 Microsoft HoloLens 硬件和全息版的应用程序的智能化设计技术功能。

## <a name="the-tech"></a>技术人员

若要使全息看起来就像它们实际上与你共享空间，它们应正确呈现，而无需分色。 由此，部分，技术内置于 HoloLens 硬件使得我们所说的定位点全息[稳定平面](hologram-stability.md#stabilization-plane)。

由一个点和正常时，定义一个平面，但因为我们始终希望要面临着相机的平面，我们实际上只是关心设置平面的点。 我们可以告诉点能够将精力集中的保留的所有内容锚定到其处理的 HoloLens 和稳定，但如何设置此焦点是特定于应用并可以执行或破坏您的应用程序，具体取决于内容。

全息简单地说，工作时，最佳的稳定平面正确应用，但的实际方式取决于要创建应用程序的类型。 让我们看一看如何应用当前可用于 HoloLens 的一些解决此问题。

## <a name="behind-the-scenes"></a>幕后

开发以下应用程序，我们注意到我们没有使用平面，当对象将 sway 时我们头移动，并且我们会看到与快速头或全息图动作分色。 开发时间范围内的过程中，我们了解到通过反复试验如何最好地使用稳定平面以及如何设计应用程序围绕它无法修复的问题。

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy 资源管理器：静态内容，三维交互性

[Galaxy 资源管理器](galaxy-explorer.md)场景中有两个主要元素：天体内容和遵循你的视线移动的小型 UI 工具栏的主视图。 稳定的逻辑中，我们了解你当前的视线移动向量中每个帧，以确定是否抵达指定的冲突层上的所有内容相交使用什么。 在这种情况下，我们感兴趣的层是行星，因此如果你的视线移动落入全球，稳定平面放在该文件夹。 如果命中无目标冲突层中的对象，该应用使用辅助的"计划 B"层。 如果不在正在 gazed，稳定平面保留相同距离时，内容在观望时一样。 UI 工具中省略了作为平面目标为我们找到附近之间的差异并得降低整体场景的稳定性。

Galaxy 资源管理器的设计有助于至稳定地保管东西和减少分色的影响。 建议用户四处和轨迹内容而不是从左到右，沿其移动和行星绕速度足够慢，分色并不明显。 此外，会保留常量 60 FPS，这就能防止发生分色。

若要亲自验证这点，查看文件中调用 LSRPlaneModifier.cs [Galaxy 资源管理器代码在 GitHub 上的](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)。

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio:使用 UI 焦点的静态内容

中 HoloStudio，您需要花费大部分时间查看相同的模型在处理。 选择一种新工具或想要导航 UI，因此我们可以简化平面设置逻辑时，你的视线移动没有除移动很长。 查看 UI 时，在平面设置为你的视线移动对应于任何 UI 元素。 查看模型时，平面是设定距离处，使用你与模型之间的默认距离相对应。

![在中实现可视化的稳定平面以用户身份 HoloStudio gazes 在主页按钮](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour 和三维查看器：动画和电影的静态内容

在 HoloTour 和三维查看器中，您就是孤立动画效果的对象或电影与在其上添加三维效果。 这些应用程序稳定性的做法是设置为任何当前正在查看。

HoloTour 还能防止 straying 太远而从虚拟世界通过让其与你移动而不是保留在固定位置。 这可确保你不会获得足够的距离稳定性问题会悄悄引入许多其他全息。

![在此示例中从 HoloTour，稳定平面将设置为 Hadrian 的 Pantheon 此电影。](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid:动态内容和环境之间的交互

在 RoboRaid 中设置的稳定平面是非常简单，尽管应用程序需要最突然移动。 在平面面向坚持使用墙纸或周围的对象，并在足够的距离离开它们时将浮动在准备好固定的距离。

RoboRaid 已设计了记住的稳定平面。 标线，因为它是 head 锁定移最，绕过这通过使用仅红色和蓝色的最大程度减少任何颜色大大超出了。 它还包含一小段深度之间的部分，将会通过模糊化具有某种已经预期的视差效果发生任何颜色出血降至最低。 机器人不非常快速地移动，并且仅移动中固定的时间间隔较短的距离。 他们往往停留大约 2 米的前面，其中默认情况下设置稳定性的做法。

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>片段和年轻 Conker:环境交互的动态内容

编写 Asobo Studio 中的C++，片段和 Young Conker 设置稳定平面到采用不同的方法。 点 (POI) 感兴趣的是在代码中定义和排序在优先级方面。 Poi 是如 Young Conker、 菜单、 瞄准标线和徽标的 Conker 型号中的游戏内容。 通过用户的视线移动与相交 Poi，平面设置为具有最高优先级的对象的中心。 如果没有交集发生，在平面设置为默认的距离。

片段和 Young Conker 还设计您通过暂停应用程序，如果移动之外什么先前已扫描作为 play 空间太远 straying 从全息周围。 在这种情况下，它们可以让您找到提供最稳定的体验的边界内。

## <a name="do-it-yourself"></a>就自己动手

如果您具有 HoloLens，并且想要琢磨我所讨论的概念，可以下载测试场景并尝试下面的练习。 它使用 Unity 的内置零件 API，它可以帮助您直观地显示设置你的平面。 此代码还用于捕获在此案例研究的屏幕快照。
1. 同步的最新版本[MixedRealityToolkit Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)。
2. 打开[HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity)场景。
3. 构建和配置生成的项目。
4. 在设备上运行。

### <a name="exercise-1"></a>练习 1

你将看到几个白色点构成您在不同的方向。 准备好，您将看到三个点在不同的深度。 敲击若要更改的点在平面设置为。 对于此练习，以及另外两个，周围移动你的空间以点观望时。 打开头左侧、 右侧，向上和向下。 从点移动更接近于和父亲。 请参阅它们时如何做出反应的稳定平面设置为不同的目标。

### <a name="exercise-2"></a>练习 2

现在，打开到您的权利，直到您看到一个振荡上水平路径，另一个垂直路径上的两个移动点。 再次重申，-敲击更改平面设置为哪些点。 请注意如何可降低分色显示上连接到平面的点。 再次点击平面设置函数中使用圆点的速度。 此参数为有关对象的预期运动到 HoloLens 提供提示。 务必要了解何时使用此操作，因为您会注意到速度上一个点的使用时，其他移动圆点将显示更高版本分色。 设计您的应用程序时记住这一点 — 具有内聚性流到您的对象的动作可帮助防止项目出现。

### <a name="exercise-3"></a>练习 3

启用到你右一次直至看到新的配置的点。 在这种情况下有距离的点和不断增加在它们的前面的传入和传出的一个点。 隔空敲击更改平面设置为，在后面的点和动作中的点之间交替的点。 请注意如何平面位置和方向的速度设置为的螺旋式上升点使项目显示所有位置。

**提示**
* 保持简单平面设置逻辑。 如您所见，无需复平面设置算法利用的沉浸式体验。 稳定平面是只有一种填数游戏。
* 当在所有可能的始终在平面之间移动目标顺利。 即时切换存有一定距离的目标可以直观地中断场景。
* 请考虑在平面设置逻辑中锁定到特定目标上具有一个选项。 这样一来，如果需要可以可以锁定一个对象，如徽标或标题屏幕上的平面。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>软件工程师 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅
* [MR 基础知识 100:开始使用 Unity](holograms-100.md)
* [在 Unity 中的焦点位置](focus-point-in-unity.md)
* [全息图稳定性](hologram-stability.md)
