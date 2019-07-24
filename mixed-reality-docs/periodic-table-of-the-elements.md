---
title: 元素周期表
description: 定期表是 Microsoft 的混合现实设计实验室中的一个开源示例应用, 你可以在其中了解如何使用对象集合在三维空间中使用不同的表面类型布置对象数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 设计, 示例应用, 控件
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525402"
---
# <a name="periodic-table-of-the-elements"></a>元素周期表

>[!NOTE]
>本文讨论了我们在[混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)中创建的探索示例, 这是我们与混合现实应用开发的知识和建议。 我们设计相关的文章和代码将随着我们的新发现而发展。

[定期表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是 Microsoft 混合现实设计实验室中的一个开源示例应用。 与此项目中，可以了解如何使用各种图面上的类型使用设置布局在 3D 空间中的对象的数组 **[对象集合](object-collection.md)** 。 还将了解如何创建响应 HoloLens 标准输入的种不可交互对象。 您可以使用此项目的组件来创建自己的混合现实应用程序体验。

![元素应用的 Period 表](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>关于应用

元素的周期性表在三维空间中直观显示化学元素及其每个属性。 它结合了 HoloLens 的基本交互, 如注视和分流。 用户可以了解带有动画3D 模型的元素。 它们可以直观地了解元素的 electron shell 及其核心, 这是由 protons 和 neutrons 组成的。

## <a name="background"></a>后台

在我首次体验 HoloLens 后, 我知道我想在混合现实中尝试使用定期表应用程序。 由于每个元素都有多个与文本一起显示的数据点, 因此, 我认为这对于浏览三维空间中的排版组合非常重要。 在此项目中, 可以可视化元素的 electron 模型是另一个有趣的部分。

## <a name="design"></a>设计

对于周期性表的默认视图, 我想要将包含每个元素的 electron 模型的三维方框。 每个框的表面都是透明的, 这样用户就可以大致了解元素的音量。 使用注视和空中点击, 用户可以打开每个元素的详细视图。 为了使表视图和详细信息视图之间的过渡平滑和自然, 我使其类似于实际生活中打开的方框的物理交互。

![设计草图](images/640px-sketch20170406.jpg)<br>
*设计草图*

在详细信息视图中, 我想要将每个元素的信息可视化到三维空间中完美呈现的文本。 动画 3D electron 模型将显示在中心区域, 并且可以从不同角度查看。

![交互](images/640px-periodictable-interaction.jpg)

![原型](images/640px-periodictable-prototypes.jpg)<br>
*交互原型*

用户可以通过点击表格底部的按钮来更改曲面类型, 它们可以在平面、圆柱、球和散点之间切换。

## <a name="common-controls-and-patterns-used-in-this-app"></a>此应用中使用的公共控件和模式

### <a name="interactable-object-button"></a>种不可交互对象 (按钮)

[种不可交互对象](interactable-object.md)是可响应基本的 HoloLens 输入的对象。 它以 prefab/脚本形式提供, 你可以轻松地将其应用于任何对象。 例如, 可以在场景种不可交互中发出咖啡杯, 并对输入 (如注视、分流、导航和操作手势) 做出响应。 [了解详细信息](interactable-object.md)

![nteractable 对象](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>对象集合

[对象集合](object-collection.md)是一个对象, 可帮助您在不同的形状中布局多个对象。 它支持平面、圆柱、球面和散点图。 可以配置其他属性, 如 radius、行数和间距。 [了解详细信息](object-collection.md)

![对象集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

默认情况下, 将在启动应用程序时, 将全息影像置于用户正在 gazing 的位置。 这有时会导致不需要的结果, 如全息影像位于墙壁后面或表中间。 Fitbox 允许用户使用 "注视" 来确定要放置全息影像的位置。 使用简单的 PNG 图像纹理进行创建, 可以使用自己的图像或三维对象轻松自定义该纹理。

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>技术细节

可在[混合现实设计实验室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上查找元素应用的定期表的脚本和 prototyping。

## <a name="application-examples"></a>应用程序示例

下面是利用此项目中的组件可以创建的一些建议。

### <a name="stock-data-visualization-app"></a>股票数据可视化应用

使用与 "元素" 示例的 "定期" 表相同的控件和交互模型, 可以构建一个直观显示股票市场数据的应用。 此示例使用对象集合控件来布局球面形状中的股票数据。 您可以想象一个详细信息视图, 其中每个股票的其他信息可能以一种有趣的方式显示。

![应用程序示例:财务 (共3个)](images/640px-periodictable-applicationexamples-finance1.jpg)

![应用程序示例:财务 (2/3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![应用程序示例:财务 (3 个)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*有关如何在 "元素示例" 应用的 "定期" 表中使用的对象集合的示例, 可在金融应用中使用*

### <a name="sports-app"></a>体育应用

这是使用对象集合和元素示例应用的定期表中的其他组件来可视化运动数据的一个示例。

![应用程序示例:体育 (共3个)](images/640px-periodictable-applicationexamples-sports0.jpg)

![应用程序示例:体育 (2/3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![应用程序示例:体育 (3 个)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*有关如何在体育应用中使用在元素的周期性表中使用的对象集合的示例 appcould*

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon 停车场</b><br>UX 设计器@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅

* [可交互对象](interactable-object.md)
* [对象集合](object-collection.md)
