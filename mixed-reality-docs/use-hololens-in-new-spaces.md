---
title: 在新空间中使用 HoloLens
description: HoloLens 了解某个空间在一段时间内的外观。 用户可以通过在空间中以特定方式移动 HoloLens 来简化此过程。
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality, 设计, 空间映射, HoloLens, 表面重建, 网格, 头跟踪, 映射
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566016"
---
# <a name="use-hololens-in-new-spaces"></a>在新空间中使用 HoloLens

在用户四处移动空间时, HoloLens*映射*或了解有关其环境的信息。 随着时间的推移, HoloLens 会构建环境中已观察到的所有部件的*空间图*。 当观察到环境中的更改时, HoloLens 会更新该映射。 此扫描将在应用启动时自动保留。

只要设备已打开, 并且用户已登录, HoloLens 就会创建和更新映射。 如果将设备放在一个空格上并将其戴上, 则设备将尝试映射该区域。 虽然 HoloLens 会在一段时间内自然地了解空间, 但仍有一些提示和技巧可以更快、更有效地映射空间。 

如果你的 HoloLens 无法映射你的空间或无法进行校准, 你可以进入 "限制" 模式。 在有限模式下, 你将无法在你的环境中放置全息影像。

## <a name="tips-and-tricks-for-mapping-spaces"></a>用于映射空间的提示和技巧

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a>请确保已为混合现实设置空间

环境中的功能可能会使 HoloLens 难以解释空间。 轻型级别、空间中的材料、对象的布局以及更多内容都可以影响 HoloLens 映射区域的方式。

有关为 HoloLens 和其他混合现实设备设置空间的技巧, 请参阅[Hololens 环境注意事项](environment-considerations-for-hololens.md)。

### <a name="understand-the-scenarios-for-the-area"></a>了解领域的方案

务必花费最长的时间来使用 HoloLens, 以便映射相关并完成。 

例如, 如果某一 HoloLens 用户方案涉及从点 A 移到点 B, 则会遍历该路径二到三次, 并在移动时查看所有方向。 

### <a name="walk-slowly-around-the-space"></a>围绕空间进行缓慢遍历

如果在该区域中进行的遍历过于迅速, 则很可能是因为 HoloLens 会丢失映射区域。 在空间上慢慢遍历, 每隔5-8 英尺停止, 以围绕您的环境。

平滑运动还有助于提高 HoloLens 地图 effeciently。

### <a name="look-in-all-directions"></a>在所有方向上查找

如果你映射空间, 则会在每个点之间的相对位置提供额外的数据。 

例如, 如果不查找, 则 HoloLens 可能不知道房间中的天花板是哪个位置。 

在映射空间时, 请不要忘记查看地面。

### <a name="cover-key-areas-multiple-times"></a>多次涵盖关键区域

多次移动某个区域将有助于选取你在第一个演练中可能缺少的功能。 尝试将某一区域遍历2到3次, 以生成理想的地图。

如果可能, 重复这些移动时, 请在一个方向上花时间浏览某个区域, 然后翻过来并向后翻一步。

### <a name="take-your-time-mapping-the-area"></a>花时间映射区域

HoloLens 可能需要15到20分钟的时间才能完全映射并调整其自身环境。 如果你有一个空间来计划频繁使用 HoloLens, 那么, 在这段时间之前, 若要映射空间, 可能会导致以后出现问题。 

## <a name="possible-errors-in-the-spatial-map"></a>空间映射中可能存在的错误

空间映射数据中的错误分为以下三个类别之一:

* *洞*:空间映射数据中缺少实际的表面。
* *Hallucinations*:图面存在于现实世界中不存在的空间映射数据中。
* *Wormholes*:HoloLens "丢失" 空间映射的一部分, 这是因为它与实际不同。
* *偏向*:空间映射数据中的图面与实际表面生成对齐或拉出。

其中许多错误可以通过[删除全息影像](environment-considerations-for-hololens.md)并重新映射空间来减轻。