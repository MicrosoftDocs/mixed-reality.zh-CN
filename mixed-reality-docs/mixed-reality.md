---
title: 什么是混合现实？
description: 本文定义了混合现实, 并展示了简单的 AR 和 VR 设备以及 Windows Mixed Reality 设备 (如 Microsoft HoloLens 和 Windows Mixed Reality 沉浸式耳机) 在混合现实范围内的位置。
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality, 全息, ar, vr, 先生, xr, 扩充现实, 虚拟现实, 说明
ms.openlocfilehash: fbac8176b36cf28673dd9633cc059e5856a50296
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326312"
---
# <a name="what-is-mixed-reality"></a>什么是混合现实？

混合现实是将物理世界与数字世界混合的结果。 混合现实是在人们、计算机和环境交互中的下一个发展, 并在现在限制为我们的想象力之前解除锁定。 这是通过计算机视觉、图形处理能力、显示技术和输入系统的进步来实现的。 术语*混合现实*1994 最初是通过 Paul Milgram 和 Fumio Kishino, "[一种混合现实视觉对象的分类](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)。" 他们的白皮书介绍了*virtuality*的一种概念, 重点介绍如何应用分类分类。 此后, 混合现实的应用程序会超出显示范围。 它还包括环境输入、空间音质和位置。

## <a name="environmental-input-and-perception"></a>环境输入和感知

![显示计算机、人类和环境之间的交互的维恩图](images/mixed-reality-venn-diagram-300px.png)<br> 

过去几十年来, 人们和计算机输入之间的关系已经过充分的探讨。 甚至还具有一种称为人员*计算机交互*或 HCI 的广泛研究的原则。 人工输入是通过多种方式进行的, 包括键盘、鼠标、触摸、墨迹、语音, 甚至 Kinect 框架跟踪。

传感器和处理方面的进步是从环境到新的计算机输入领域。 计算机和环境之间的交互实际上是环境理解或*认知*。 因此, Windows 中显示环境信息的 API 名称称为 "[感知 api](https://docs.microsoft.com/uwp/api/Windows.Perception)"。 环境输入会捕获用户在世界上的位置 (例如,[打印头跟踪](coordinate-systems.md))、表面和边界 (例如,[空间映射](spatial-mapping.md)和[空间理解](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md))、环境照明、环境声音、对象识别和位置。

现在, 所有三个--计算机处理、人工输入和环境输入的组合都可用于创建真正的混合现实体验。 在现实世界中的移动可以转换为数字世界中的运动。 现实世界中的边界可能会影响数字世界中的应用程序体验, 例如游戏播放。 如果没有环境输入, 体验就不能在物理和数字现实之间融合。

## <a name="the-mixed-reality-spectrum"></a>混合现实范围

因为混合现实混合了物理和数字世界, 所以这两个现实定义了一种称为 virtuality continuum 的极有极端的端。 为简单起见, 我们将此视为*混合现实频谱*。 在左侧, 我们的现实生活中存在;在右侧, 我们有相应的数码现实。

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

目前市场上的大多数移动电话几乎没有环境理解功能。 因此, 它们所提供的体验不能在物理和数字现实之间混合使用。 在物理世界的视频流上覆盖图形的经验得以增加 *。* 遮蔽你的视图呈现数字体验的体验是*虚拟现实*。 正如您所看到的, 在这两种极端情况下启用的体验是*混合的现实*:
* 从物理世界开始, 放入数字对象 (如全息图), 就像它确实如此。
* 从身体开始, 另一个用户 (即头像) 的数字表示形式, 显示离开笔记时的位置。 换句话说, 在不同时间点表示异步协作的经验。
* 从数字世界开始, 来自实物世界的物理边界 (如墙壁和家具) 在体验中以数字形式显示, 以帮助用户避免物理对象。

![混合现实范围](images/mixed-reality-spectrum-550px.png)

目前提供的大多数增加的现实和虚拟现实产品都代表了这种色谱的一小部分。 但它们是较大混合现实范围的子集。 Windows 10 在构建时考虑了整个频谱, 并允许在现实世界中混合人员、地点和物品的数字表示形式。

![混合现实范围内的设备类型](images/mixed-reality-spectrum-device-types-550px.png)

有两种主要类型的设备可提供 Windows Mixed Reality 体验:
1. **全息设备。** 这些特征的特征在于设备能够将数字内容置于真实世界中, 就像确实如此。
2. **沉浸式设备。** 这些特征的特征是设备能够创建 "状态"--隐藏物理世界, 并将其替换为数字体验。

<table>
<tr>
<th width="20%"> 特征</th><th width="40%"> 全息设备</th><th width="40%"> 沉浸式设备</th>
</tr><tr>
<td> 示例设备</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows Mixed Reality 开发版<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> 显示</td><td> <i>查看-通过显示。</i> 允许用户在戴上耳机时查看物理环境。</td><td> <i>不透明显示。</i> 在戴上耳机时阻塞物理环境。</td>
</tr><tr>
<td> 搬家</td><td> 旋转和平移都具有全部六个自由度。</td><td> 旋转和平移都具有全部六个自由度。</td>
</tr>
</table>

请注意, 设备是连接到单独的 PC 还是受限 (通过 USB 电缆或 Wi-fi) 或自包含设备 (untethered), 并不反映设备是全息设备还是沉浸式设备。 当然, 改进移动性的功能会导致更好的体验, 而全息和沉浸式设备可能是受限或 untethered。

## <a name="devices-and-experiences"></a>设备和体验

技术进步已经实现了混合现实体验。 目前没有可在整个范围内运行体验的设备。 但是, Windows 10 为设备制造商和开发人员提供了共同的混合现实平台。 目前的设备可以支持混合现实范围内的特定范围。 随着时间的推移, 新设备将扩展此范围。 未来, 全息设备将变得更加引人入胜, 沉浸式设备将会变得更全息。

![设备在混合现实频谱上的布局](images/mixed-reality-spectrum-device-placement-550px.png)

通常, 最好考虑应用程序或游戏开发人员要创建的体验类型。 这些体验通常面向特定的点或部分。 然后, 开发人员应考虑要面向的设备的功能。 例如, 依赖于现实世界的体验将在 HoloLens 上运行最佳。
* **向左 (接近物理事实)。** 用户仍在其物理环境中存在, 永远不会相信他们已离开该环境。
* **中间 (完全混合现实)。** 这些经验融合了真实世界和数字世界。 观看了电影[Jumanji](https://en.wikipedia.org/wiki/Jumanji)的观看者可以协调出故事发生的物理结构与蛙鸣环境的混合方式。
* **向右 (接近数字事实)。** 用户体验到完全数字环境, 并不知道其周围的物理环境发生了什么情况。


## <a name="see-also"></a>请参阅
* [API 参考:Windows。感知](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [API 参考:Windows. 感知](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [API 参考:Windows 感知. 面](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
