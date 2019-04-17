---
title: 空间的定位点
description: 有关使用空间的定位点呈现稳定全息最佳实践。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 坐标系统、 空间坐标系统、 全球规模，世界、 规模、 位置、 方向、 定位点、 空间定位点、 世界锁定，世界上锁定，持久性共享
ms.openlocfilehash: eb0fae7881f1b6517da57305ef2fa3cb1ed78648
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593069"
---
# <a name="spatial-anchors"></a>空间的定位点

空间的定位点表示世界上，系统应保持跟踪随着时间的推移很重要的一点。 每个定位点已[坐标系](coordinate-systems.md)，调整根据需要相对于其他的定位点，或将的参考框架，以确保定位的全息保持准确地说中。  呈现的定位点的坐标系统中的一张全息图提供最准确定位该全息图在任何给定时间。 这为代价的微小调整随着时间的推移到全息图的位置，如系统不断地将其移回到相对于现实世界的位置。

您还可以保留和在应用程序会话之间和跨设备共享空间的定位点：
* 通过将本地空间定位点保存到磁盘和更高版本将它们重新的加载，您的应用程序可以推断现实世界中的同一位置在单一的 HoloLens 设备上的多个应用程序会话。
* 通过使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>若要创建云定位点，您的应用程序可以共享空间定位点跨多个 HoloLens、 iOS 和 Android 设备。 通过让每个设备呈现一张全息图，使用相同的空间定位点，所有用户将都看到出现在现实生活中的同一位置的全息图。  这样实时共享体验。
* 此外可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>异步全息图暂留在 HoloLens、 iOS 和 Android 设备。  通过共享持久的云空间定位点，多个设备可以观察到相同的持久化全息图随着时间推移，即使这些设备不存在同时在一起。

对于现有规模或聊天室刻度体验将保留在 5 米直径的受限桌面耳机，您通常只是可以使用[阶段参考框架](coordinate-systems.md#stage-frame-of-reference)而不空间的定位点，为您提供一个坐标系统中的呈现所有内容。 但是，如果您的应用程序打算让用户在 HoloLens 上游离超出 5 米，可能在整个楼层，整个操作需要空间要保留内容稳定的定位点。

而空间的定位点非常适合用于全息应保留的固定在世界中，定位点放置后，它不能移动。 有更适用于应标记以及用户的动态全息的定位点的替代方法。 最好是定位动态全息使用固定参考框架 （Unity 的世界坐标的基础） 或附加的参考框架。

## <a name="best-practices"></a>最佳做法

这些空间的定位点指南将帮助你准确地跟踪现实世界的稳定全息呈现。

### <a name="create-spatial-anchors-where-users-place-them"></a>创建空间，用户将其放置的锚点

大多数情况下，用户应是显式将空间的定位点。

例如，在 HoloLens，应用可以相交用户的[注视](gaze.md)与光纤[空间映射](spatial-mapping.md)网格，会让用户决定是否要将一张全息图。 当用户点击放置该全息图时的交点创建空间的定位点，然后将全息图放在该定位点的坐标系统的原点。

本地空间定位点的方法很简单和高性能，若要创建，且系统将整合其内部数据，如果多个定位点可以共享其基础的传感器数据。 通常应创建新的本地空间定位，为用户显式将放入，每个全息图如下所述的全息刚性组等资源的情况除外。

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>始终呈现在 3 米的其定位点定位的全息

空间的定位点稳定定位点的源附近其坐标系统。 如果呈现全息超过大约 3 米从该原点，这些全息可能会遇到成比例地从该原点，由于杆 arm 影响其距离的明显位置错误。 如果用户代表附近作为定位点，因为全息图太远而从用户，这意味着远处全息图 angular 错误将会很低的效果。 但是，如果用户对此存有一定距离全息图遍历，它然后将其视图，从而杠杆 arm 效果遥远的定位点从源难度很大。

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>应形成刚性群集组全息

如果应用需要这些全息保持固定到另一个关系，多个全息可以共享相同空间定位点。

例如，如果您对 holographic 太阳系聊天室中进行动画处理，最好在中心，将所有太阳系对象与一个定位点，以便它们相对于彼此顺利移动。 在这种情况下，它是太阳系作为一个整体锚定，即使其各个组成部分移动动态定位点。

密钥这里需要注意维护全息图稳定性是遵循上述 3 米长规则。

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>呈现高动态全息使用而不本地空间定位点的固定参考框架

如果已高度动态的全息图，如移动办公了空间或沿附近用户墙上的浮动 UI 的字符是最佳来跳过本地空间定位点和呈现这些全息提供的坐标系统中直接[</c01>固定参考框架<spanclass="notranslate">](coordinate-systems.md#stationary-frame-of-reference)（即在 Unity 中，你通过实现此目的而无需 WorldAnchor 世界坐标直接置于全息）。</span> 全息固定参考框架中的可能会遇到偏差，当用户与相差甚远全息图，但这是不太可能明显的动态全息： 全息图不断不管怎样，移动或其动画不断地使其靠近用户的位置偏差将最小化。

动态全息的一个有趣的用例是从一个锚定的坐标系统到另一个动画处理的对象。 例如，你可能两个 castle 10 米，每隔上其自己空间的定位点，每个与一个 castle 触发在其他 castle cannonball。 在触发 cannonball 时刻，您可能会导致中固定参考框架，以便与第一个 castle 锚定的坐标系统中 cannon 一致的适当位置。 因为它将飞以无线方式通过 10 米，它然后可以按照其轨迹中固定参考框架。 当 cannonball 到达其他城堡，您可以选择移动到第二个 castle 定位坐标系统，以允许物理引擎该 castle 刚体的运算。

如果要在设备之间共享高动态全息图，您需要保持静止的参考框架不能在设备之间共享选取某些云空间定位点作为其父级。  但是，在这种情况下，应确保可以动态全息图或设备查看其保留在定位点的 3 米半径，以确保全息图显示稳定在所有设备上。

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>避免创建空间的定位点的网格

您可能想要删除空间的定位点的正则网格，因为用户走，转换动态对象定位到定位点，因为它们四处移动应用程序。 但是，这涉及到大量的管理为你的应用，而无需系统本身会在内部维护的深度的传感器数据的好处。 对于这些情况下，您将通常实现更轻松地更好的结果通过将你全息放置在固定参考框架，如上面的部分中所述。

时预定位一组静态空间围绕云空间定位标记，请考虑将空间的定位点放在用户将会遇到上述原则每密钥全息位置，而不是创建任意网格的定位点。  这可确保你将这些密钥全息可以获得最大的稳定性。

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>释放不再需要的本地空间定位点

虽然本地空间定位点处于活动状态，系统将确定即将达到该定位点的传感器数据的保留的优先级。 如果您不再使用空间的定位点，停止访问其坐标系统。 这将允许在必要时要删除其基础的传感器数据。

这一点尤其重要的本地保留空间的定位点存储的定位点。 这些定位点背后的传感器数据将保留围绕永久以允许你的应用程序，以查找该定位点在将来应用会话中，这将减少跟踪其他定位点的可用空间。 保留仅需要再次在将来的会话中查找并删除这些存储中，不再对用户有意义时这些本地定位点。

有关云空间定位标记，可以根据你的方案需要向你的存储。  你可以存储无数云定位标记，根据需要仅当你知道你的用户将不需要再次在该定位点处找到全息时释放它们。

## <a name="see-also"></a>请参阅
* [坐标系统](coordinate-systems.md)
* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>
* [在 Unity 中的暂留](persistence-in-unity.md)
* [DirectX 中的空间定位点](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [案例研究-通查在现实中的漏洞](case-study-looking-through-holes-in-your-reality.md)
