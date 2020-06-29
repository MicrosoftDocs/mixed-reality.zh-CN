---
title: 空间定位点
description: 使用空间定位点呈现稳定全息影像的最佳做法。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 坐标系、空间坐标系、世界规模、世界、规模、位置、方向、定位点、空间定位点、世界锁定、持久性、共享
ms.openlocfilehash: 8d270f96add795fdb54e0a91ebc9d38a34640da1
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441784"
---
# <a name="spatial-anchors"></a>空间定位点

空间定位点表示世界上系统跟踪一段时间的重要点。 每个定位点具有可根据需要进行调整的[坐标系](coordinate-systems.md)（相对于其他定位点或参照系），以确保锚定的全息影像保持位置精确。  在定位点的坐标系中呈现全息影像可以在任何给定时间为你提供最准确的全息影像定位。 随着系统不断地将其移回相对于真实世界的位置，这是一段时间内的小调整成本。

你还可以跨应用程序会话和跨设备保留和共享空间定位点：
* 通过将本地空间锚点保存到磁盘并稍后将其加载回来，你的应用程序可以在一个 HoloLens 上跨多个应用程序会话计算同一位置。
* 使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚</a>点创建云锚点，你的应用程序可以跨多个 HoloLens、IOS 和 Android 设备共享空间锚。 通过让每个设备使用相同的空间定位点呈现一个全息影像，用户将看到全息图显示在现实世界中的同一位置。 这可实现实时共享体验。
* 还可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>在 HoloLens、iOS 和 Android 设备上实现异步全息影像持久性。 通过共享持久的云空间定位点，多个设备可以随着时间推移观察相同的持久全息影像，即使这些设备没有同时出现，也是如此。

对于受限台式机耳机的大规模或房间规模体验，这些体验将停留在5米内，你通常可以使用[参考的阶段框架](coordinate-systems.md#stage-frame-of-reference)，而不是空间锚，为你提供一个用于呈现所有内容的单一坐标系统。 但是，如果应用程序希望让用户游离在一座办公楼的整个楼层内超过5米，则需要使用空间锚，使内容保持稳定。

虽然空间定位点非常适合应该在世界中保持固定的全息影像，但是放置定位点后，它便无法移动。 对于与用户一起标记的动态全息影像，更适合定位锚。 最好使用固定的参照系（Unity 世界坐标的基础）或附加的参照系来定位动态全息影像。

## <a name="best-practices"></a>最佳做法

这些空间定位点指南将帮助你呈现稳定的全息影像，准确跟踪现实世界。

### <a name="create-spatial-anchors-where-users-place-them"></a>在用户需要放置空间定位点的位置创建空间定位点

通常，用户是显式放置空间锚的用户。

例如，在 HoloLens 上，应用程序可以使用[空间映射](spatial-mapping.md)网格将用户的 "注视" 光线与用户的 "[注视](gaze-and-commit.md)" 网格相交，让用户决定放置全息图的位置。 当用户点击来放置该全息图时，请在交点处创建一个空间锚点，然后将其放置在该锚点坐标系统的原点。

本地空间锚容易创建。 如果多个定位点可以共享其底层的传感器数据，系统将合并其内部数据。 通常应为用户显式放置的每个全息图创建新的本地空间定位点，但下面列出的情况除外，如下面所述的一组全息影像。

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>始终呈现定位点 3 米范围内的锚定的全息影像

空间定位点稳定定位点原点附近的坐标系。 如果从该原点渲染全息超过3米，则这些全息影像可能会遇到明显的位置错误，它们与源相对于其原点的距离成了不同的距离。 如果用户位于定位点附近，则此操作将起作用，因为全息图也远离用户。 换句话说，遥远全息图的角度误差将会很小。 但是，如果用户遍历到该多个全息图，则它会在其视图中很大，因此，遥远定位源的杠杆臂效果非常明显。

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>聚集应形成固定群集的全息影像

如果应用程序预期这些全息影像彼此保持固定关系，则多个全息影像可以共享同一个空间定位点。

例如，如果您要对房间中的全息阳历系统进行动画处理，最好将所有太阳系对象绑定到中心的单个锚，使其彼此平滑。 在这种情况下，太阳系作为一个整体被锚定，即使其组成部分围绕定位点动态移动，也是如此。

保持全息图稳定性的关键是遵循上面的3米规则。

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>使用固定参照系（而不是局部空间定位点）呈现高度动态全息影像

如果你有一个高度动态的全息图（例如，人物围绕用户附近的墙壁或浮动 UI），最好跳过本地空间锚，并直接在[固定的参考框架](coordinate-systems.md#stationary-frame-of-reference)提供的坐标系统中渲染这些全息影像。 在 Unity 中，可以通过在不使用 WorldAnchor 的情况下直接将全息影像置于世界坐标中来实现此目的。 当用户离全息影像时，固定框架中的全息影像可能会出现偏移。 但对于动态全息影像而言，这不太可能是显而易见的：这可能是因为全息影像经常发生移动，或者它的运动不断地使其靠近用户，而偏移量会降至最低。

动态全息影像的一个有趣的例子是创建从一个锚定坐标系到另一个锚定坐标系的动画的对象。 例如，你可能有两个 castles 的10米，每个都在其自己的空间锚，其中有一个城堡触发 cannonball。 在触发 cannonball 时，可以将其呈现在固定引用框架中的适当位置，使其与第一个城堡的定位坐标系统中的 cannon 一致。 然后，它可以循着它在固定参照系中的轨迹，在空中飞行 10 米。 当 cannonball 到达另一个城堡时，您可以选择将它移动到第二个城堡的定位坐标系，以允许与该城堡的严格主体进行物理学计算。

如果跨设备共享高度动态的全息图，则需要选取某个云空间锚，使其成为父代，因为不能跨设备共享固定的参考框架。  但是，在这种情况下，应确保动态全息图或查看它的设备仍在锚定的3米半径内，以确保在所有设备上都能稳定显示。

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>避免创建空间定位点网格

您可能想让您的应用程序在用户四处浏览时删除空间锚点的常规网格，并在移动动态对象时将其转换为锚点。 但是，这涉及到应用程序的许多管理，而不会带来系统本身在内部维护的深层传感器数据的好处。 在这种情况下，你通常可以通过将全息影像置于固定的参考框架中来获得更好的效果，如以上部分所述。
在将一组云空间锚点置于静态空间周围之前，请考虑将空间锚点放置在用户根据上述原则遇到的密钥全息影像位置，而不是创建任意的定位点网格。 该操作可确保获得这些关键全息影像的最大稳定性。

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>释放你不再需要的局部空间定位点

本地空间锚点处于活动状态时，系统会将保留在该锚点附近的传感器数据排定优先顺序。 如果你不再使用空间定位点，请停止访问其坐标系。 这允许根据需要删除其基础传感器数据。

这对于你持久保存到空间定位点存储的局部定位点尤其重要。 这些定位点后面的传感器数据将永久保留，以允许你的应用程序在将来的会话中查找该定位点，这将减少用于跟踪其他锚点的空间。 仅保留需要在未来的会话中再次查找的本地锚，并在用户不再有意义的情况下将其从应用商店中删除。

对于云空间定位点，存储可以根据场景需要进行扩展。 你可以根据需要存储任意数量的云定位点，仅当你知道用户不需要在该定位点上再次查找全息影像时才会将其释放。

## <a name="see-also"></a>请参阅
* [坐标系统](coordinate-systems.md)
* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* [Unity 中的持久性](persistence-in-unity.md)
* [DirectX 中的空间定位点](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [案例研究 - 看透现实中的洞](case-study-looking-through-holes-in-your-reality.md)
