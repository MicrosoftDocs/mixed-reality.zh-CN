---
title: 什么被混合现实？
description: 本文定义了混合的现实，并说明了其中简单 AR 和 VR 设备，以及 Windows Mixed Reality 设备，如 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式耳机，坐下来的混合的现实范畴。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: 混合的现实 holographic，ar、 vr、 mr、 xr、 增强的现实、 虚拟现实说明
ms.openlocfilehash: fbac8176b36cf28673dd9633cc059e5856a50296
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326312"
---
# <a name="what-is-mixed-reality"></a>什么被混合现实？

混合的现实是混合现实世界与数字世界的结果。 混合的现实是用户、 计算机和环境交互的下一个演化，解锁之前现在已限制为我们想象力的可能性。 它是通过实现计算机视觉、 图形处理能力、 显示技术和输入的系统中的高级功能。 术语*混合现实*最初由 Paul Milgram 和 Fumio Kishino 引入 1994年白皮书中"[分类的混合现实的视觉显示](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)。" 引入了的概念，其纸张*virtuality continuum*，并专注于应用于分类的分类的显示方式。 从那时起，应用程序的混合现实超越了显示。 它还包括环境的输入、 空间声音和位置。

## <a name="environmental-input-and-perception"></a>环境的输入和感知

![显示计算机、 人和环境之间的交互的维恩图](images/mixed-reality-venn-diagram-300px.png)<br> 

通过过去的几个几十年来，用户和计算机输入之间的关系已还探讨了。 它甚至还包含名为广为研究的专业*人机交互*或 HCI。 通过多种不同的方法，包括键盘、 鼠标、 触控、 手写内容、 语音、 和甚至 Kinect 主干跟踪发生人工输入。

中的传感器和处理的高级功能即表示授予上升到的计算机输入新的区域从环境。 计算机和环境之间的交互是有效地环境了解或*perception*。 因此调用显示环境信息的 Windows 中的 API 名称[perception Api](https://docs.microsoft.com/uwp/api/Windows.Perception)。 环境输入捕获等人的世界中的位置 (例如[头跟踪](coordinate-systems.md))，图面和边界 (例如[空间映射](spatial-mapping.md)和[空间了解](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md))，环境照明、 环境声音、 对象识别和位置。

现在，所有三个-计算机的处理相结合，人工输入和环境输入-设置来创建，则返回 true 的混合的现实体验的机会。 通过物理世界移动可以将转换为数字世界中的移动。 现实生活中的边界可能会影响应用程序的体验，例如玩游戏，在数字世界中。 而无需环境输入体验不能混合之间物理和数字的实际问题。

## <a name="the-mixed-reality-spectrum"></a>混合的现实范围

由于混合的现实混合物理和数字世界，这些两个现实情况定义称为 virtuality continuum 提供了一系列在极坐标图结束。 为简单起见，我们将它称为*混合的现实范围*。 在左侧，我们有在其中我们人类，存在; 的物理现实在右侧上有相应的数字现实。

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

市场上大多数移动电话现在有一些不环境了解功能。 因此，它们提供的体验不能混合之间物理和数字的实际问题。 覆盖层上的物理世界的视频流的图形体验*增强现实*。 遮蔽视图，以便提供一种数字体验体验*虚拟现实*。 正如您所看到的是这两个极端之间启用了体验*混合现实*:
* 启动与物理世界，放置一个数字的对象，例如一张全息图，就像它是确实存在。
* 与物理世界，另一个人-的数字表示开始头像-显示其中它们站着离开说明时的位置。 换而言之，表示异步协作的不同时间点在时间中的体验。
* 从开始的数字世界，物理边界从真实的场景中，如墙壁和家具，数字中显示了体验，以帮助用户避免物理对象。

![混合的现实范围](images/mixed-reality-spectrum-550px.png)

最增强的现实和虚拟现实产品/服务提供立即表示此频谱的一小部分。 它们，但是，在更大的混合的现实范畴内形成的子集。 Windows 10 的一点是，所有使用构建而成，并允许值混合处理的人员、 地点和操作与现实世界的数字表示形式。

![混合的现实范围中的设备类型](images/mixed-reality-spectrum-device-types-550px.png)

有两种主要类型的设备提供的 Windows Mixed Reality 体验：
1. **Holographic 的设备。** 这些的特征是设备的能力，就好像确实可以将数字内容放置在现实生活中。
2. **沉浸式设备。** 这些的特征是创建"状态显示"-隐藏真实的场景中，并将它替换数字体验的意义上设备的功能。

<table>
<tr>
<th width="20%"> 特征</th><th width="40%"> Holographic 的设备</th><th width="40%"> 沉浸式设备</th>
</tr><tr>
<td> 示例设备</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows 混合现实开发版<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> 显示</td><td> <i>透明显示。</i> 允许用户戴耳机时看到的物理环境。</td><td> <i>不透明的显示。</i> 物理环境时戴耳机的块。</td>
</tr><tr>
<td> 移动</td><td> 完整的六个度自由移动、 旋转和转换。</td><td> 完整的六个度自由移动、 旋转和转换。</td>
</tr>
</table>

请注意，在设备连接到或已接入的到单独的 PC （通过 USB 线缆或 Wi-fi），或者在自包含 （无约束） 是否不会反映设备是全息版或沉浸式。 当然，提高移动性的功能会导致更好的体验，而全息版和沉浸式设备可能是受限或无约束。

## <a name="devices-and-experiences"></a>设备和体验

技术进步是什么已启用混合的现实体验。 有条件的设备现在可以跨所有运行体验。 但是，Windows 10 设备制造商和开发人员提供一个通用的混合的现实平台。 设备现在可以支持混合的现实范围内的特定范围。 随着时间推移，新设备将扩展该范围。 将来，holographic 的设备将变得更多沉浸式的并且沉浸式设备将成为更全息版。

![设备在混合的现实范畴内形成布局的位置](images/mixed-reality-spectrum-device-placement-550px.png)

通常情况下，最好考虑一下何种类型的体验的应用程序或游戏开发人员希望创建。 体验通常将针对某个特定点或在范畴内形成的一部分。 然后，开发人员应考虑他们想要面向的设备的功能。 例如，依赖于现实世界的体验将在 HoloLens 上运行最佳。
* **向 （附近物理现实） 左侧。** 用户仍处于其物理环境中存在，并且永远不会进行相信还剩该环境。
* **中的中间 （完全混合现实）。** 这些体验混合现实世界和数字世界。 看过电影的查看者[Jumanji](https://en.wikipedia.org/wiki/Jumanji)可以协调的房屋故事发生的物理结构如何混合和森林环境。
* **针对 （附近数字现实） 的权限。** 用户体验完全采用数字环境，并不知道其周围的物理环境中发生的事情。


## <a name="see-also"></a>请参阅
* [API 参考：Windows.Perception](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [API 参考：Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [API 参考：Windows.Perception.Spatial.Surfaces](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
