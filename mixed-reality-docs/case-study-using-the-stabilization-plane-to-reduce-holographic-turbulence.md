---
title: 案例研究-使用稳定面减少全息 turbulence
description: 使用稳定面减少全息 turbulence
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 全息影像, 稳定性, 案例研究
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526250"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>案例研究-使用稳定面减少全息 turbulence

使用全息影像可能比较棘手。 这样一来, 您可以四处移动空间, 从所有不同角度查看全息影像, 都提供了一种不能使用普通计算机屏幕获得的浸入式。 将这些全息影像置于适当位置并寻找现实, 这是一项技术特征, 由 Microsoft HoloLens 硬件和全息式应用程序的智能设计完成。

## <a name="the-tech"></a>技术人员

为了使全息影像看起来像是实际与你共享空间, 它们应该正确呈现, 无需颜色分离。 这一部分是通过内置于 HoloLens 硬件的技术来实现的, 该技术使全息影像定位在我们称为 "[稳定" 平面](hologram-stability.md#stabilization-plane)上的内容。

平面由点和法线定义, 但由于我们始终希望该平面面对相机, 因此我们实际上只关心设置平面的点。 我们可以告诉 HoloLens 哪个点将其处理操作集中在一起, 使所有内容保持锚定并稳定, 但如何设置此焦点点是特定于应用的, 并且可以根据内容创建或中断应用。

简而言之, 在正确应用了稳定平面后, 全息影像最有效, 但实际意味着哪种方式取决于要创建的应用程序的类型。 让我们看看一些当前可用于 HoloLens 的应用如何解决此问题。

## <a name="behind-the-scenes"></a>幕后

在开发以下应用程序时, 我们注意到, 当我们未使用该平面时, 对象会在我们的打印头移动时使用 sway, 并且我们会发现, 使用打印头或全息图进行分色。 在开发的整个过程中, 我们已通过试用和错误了解如何最好地使用稳定面, 以及如何在不能解决的问题周围设计应用程序。

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy 资源管理器:静止内容, 三维交互

在场景中, [Galaxy 资源管理器](galaxy-explorer.md)具有两个主要元素:你的注视后的天体内容和小 UI 工具栏的主视图。 对于稳定性逻辑, 我们将查看当前看上去向量与每个帧中的相交情况, 以确定它是否达到了指定冲突层上的任何内容。 在这种情况下, 我们感兴趣的层是行星, 因此, 如果注视落在地球上, 则会将稳定平面放置在该处。 如果未命中目标冲突层中的任何对象, 则应用将使用辅助 "计划 B" 层。 如果未在 gazed 任何内容, 则稳定面将保持与 gazing 内容时的距离相同。 UI 工具将作为平面目标, 正如我们发现, 在接近到远处, 降低了整体场景的稳定性。

Galaxy 资源管理器的设计适合于使其保持稳定并降低颜色分离的效果。 鼓励用户浏览内容, 而不是从一边移动内容, 而是轨道缓慢, 以致颜色分离并不明显。 此外, 还保留了恒定的 60 FPS, 这在防止颜色分离发生的情况下是一种很长的方式。

若要亲自查看此问题, 请在[GitHub 上的 Galaxy 资源管理器代码](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)中查找名为 LSRPlaneModifier.cs 的文件。

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio:带有 UI 焦点的静止内容

在 HoloStudio 中, 大多数时候都在查看正在使用的同一模型。 如果你选择一个新工具或要浏览 UI, 你的注视不会有很大的影响, 因此, 我们可以将平面设置逻辑保持简单。 查看 UI 时, 平面将设置为您的 "注视" 对齐的任何 UI 元素。 查看模型时, 平面是一组距离, 与您与模型之间的默认距离相对应。

!["HoloStudio" 中的 "稳定" 平面以用户在 "主页" 按钮上 gazes](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour 和3D 查看器:带有动画和电影的静止内容

在 HoloTour 和3D 查看器中, 您正在查看孤立动画对象或电影, 其中添加了三维效果。 这些应用中的稳定设置为当前正在查看的内容。

HoloTour 还可以让你与你的虚拟世界失去联系, 而不是保持在固定位置。 这可以确保你不会从其他影像中获得足够的空间, 以便在中进行爬出。

![在此示例中, HoloTour 为 Hadrian 的 Pantheon 的此电影。](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid:动态内容和环境交互

尽管应用程序需要突然移动, 但在 RoboRaid 中设置稳定平面非常简单。 该平面朝向远离墙壁或周围对象的方向, 当您离离这些物体时, 它将在您前面的固定距离处浮动。

RoboRaid 设计为在设计时考虑到了稳定性。 Reticle, 它将最大程度地移动, 因为它被锁定, 因此只使用红色和蓝色, 这会使任何颜色的颜色最小化。 它还包含各部分之间的一小部分深度, 最大程度地减少了通过使用已预期的视差效果屏蔽的颜色出血。 机器人不会非常快地移动, 而且会按固定的时间间隔轻松移动。 它们的正面往往围绕2米, 在默认情况下, 会设置稳定。

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>片段和年轻人 Conker:带有环境交互的动态内容

使用 Asobo Studio C++编写的片段和年轻人 Conker 采用不同的方法来设置 "稳定" 平面。 相关点 (POI) 在代码中定义, 并按优先级排序。 Poi 是游戏中的内容, 例如年轻人 Conker、菜单、目标 reticle 和徽标中的 Conker 模型。 Poi 与用户的 "注视" 相交, "平面" 设置为具有最高优先级的对象的中心。 如果未发生交集, 则将平面设置为默认距离。

如果移动到之前已作为播放空间进行了扫描的内容, 则片段和年轻人 Conker 还会通过暂停应用程序来设计离全息 straying 太远的位置。 因此, 它们使你能够在提供最稳定的体验的边界内实现。

## <a name="do-it-yourself"></a>自行完成

如果你有一个 HoloLens, 并且想要与我讨论过的概念进行探讨, 你可以下载一个测试场景并尝试以下练习。 它使用 Unity 的内置别出心裁 API, 它应有助于您直观地显示平面的设置位置。 此代码还用于捕获此案例研究中的屏幕截图。
1. 同步最新版本的[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)。
2. 打开[HoloToolkit-Examples/公用事业/场景/StabilizationPlaneSetting](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity)场景。
3. 生成并配置生成的项目。
4. 在设备上运行。

### <a name="exercise-1"></a>练习1

你将看到不同方向的几个白点。 在您之前, 您将在不同的深度看到三个点。 点击以更改平面设置为的点。 对于本练习, 在这两个过程中, 在 gazing 点时移动空间。 向左、向右、向上、向下旋转。 从点接近和成为父亲。 查看稳定性平面设置为不同目标时, 如何做出反应。

### <a name="exercise-2"></a>练习2

现在, 转到右侧, 直到看到两个移动点、水平路径上的一个振荡和一个垂直路径上的一个。 同样, 单击即可更改该平面设置为的点。 请注意, 在连接到平面的点上出现颜色分离的方式。 再次点击以在 "平面" 设置函数中使用点的速度。 此参数向 HoloLens 提供有关对象的预期运动的提示。 了解何时使用这一点非常重要, 因为当在一个圆点上使用了速度时, 另一个移动点将显示更大的颜色分隔。 在设计应用程序时请牢记这一点, 这会使对象的运动产生内聚性, 从而有助于防止出现项目。

### <a name="exercise-3"></a>练习3

再次转到右侧, 直到看到新的点配置。 在这种情况下, 这两个点之间存在点, 并在其前面加上一个圆点。 点击以更改平面设置为的点, 在背面的点与运动中的点之间交替。 请注意, 将平面位置与螺旋式点的速度设置为会使项目显示在任何位置。

**技巧**
* 使平面设置逻辑简单。 如您所见, 您不需要使用复杂的平面设置算法来实现沉浸式体验。 稳定平面只是一片谜。
* 在任何可能的情况下, 始终在目标之间平稳移动平面。 即时切换到远处目标可能会以可视方式中断场景。
* 请考虑在飞机中设置一个选项, 将逻辑锁定到非常具体的目标。 这样一来, 就可以根据需要在对象 (如徽标或标题屏幕) 上锁定平面。

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>软件工程师@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅
* [MR 基础知识 100：Unity 入门](holograms-100.md)
* [Unity 中的焦点](focus-point-in-unity.md)
* [全息影像稳定性](hologram-stability.md)
