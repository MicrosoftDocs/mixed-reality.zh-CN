---
title: 定期表的元素
description: 元素的定期表是开放源代码示例应用程序从 Microsoft 的混合现实设计实验室可从中了解如何使用各种使用对象集合的图面类型设置布局在 3D 空间中的对象的数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 示例应用程序、 控件
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592865"
---
# <a name="periodic-table-of-the-elements"></a>定期表的元素

>[!NOTE]
>本文讨论了我们已在中创建一个探索示例[混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)，其中我们共享有关我们的知识和建议的混合现实应用程序开发。 当我们进行新的发现，我们与设计相关文章和代码将发展。

[元素的定期表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是来自 Microsoft 的混合现实设计实验室一个开放源代码示例应用。 与此项目中，可以了解如何使用各种图面上的类型使用设置布局在 3D 空间中的对象的数组 **[对象集合](object-collection.md)** 。 此外了解如何创建种交互响应来自 HoloLens 的标准输入的对象。 可以使用此项目的组件来创建你自己的混合现实应用体验。

![时间段表的元素应用](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>有关应用程序

定期表的元素的可视化化工元素和每个 3D 空间中的其属性。 它集成了 HoloLens 等的视线移动和 air 点击的基本交互。 用户可以了解具有经过动画处理三维模型的元素。 它们可以直观地了解元素的 electron shell 和其核心-由质子和 neutrons 组成。

## <a name="background"></a>后台

我首次遇到 HoloLens 后，定期表应用时的了解我知道，我希望尝试混合现实中使用。 由于每个元素将以文本显示的多个数据点，我认为它是用于浏览在 3D 空间中的版式组合的有用主题事项。 能够可视化元素的 electron 模型是此项目的另一个有趣的一部分。

## <a name="design"></a>设计

对于定期表的默认视图中，我可以想象将包含每个元素的 electron 模型的三维框。 每个框的面将透明，以便用户可以获取元素的卷的粗略。 视线移动和 air 点击，用户可以打开每个元素的详细视图。 若要使表视图和详细信息视图之间的转换平滑和自然，我得类似于在现实生活中打开一个框的物理交互。

![设计草图](images/640px-sketch20170406.jpg)<br>
*设计草图*

在详细信息视图中，我想要可视化的美观地呈现在 3D 空间中的文本与每个元素的信息。 动画三维 electron 模型显示在中心区域，并且可以从不同角度查看。

![交互](images/640px-periodictable-interaction.jpg)

![Prototypes](images/640px-periodictable-prototypes.jpg)<br>
*交互原型*

用户可以通过点击底部的表上的按钮以无线方式来更改图面上的类型-它们可以平面、 圆柱体、 球体和散点图之间进行切换。

## <a name="common-controls-and-patterns-used-in-this-app"></a>常见控件和此应用中使用的模式

### <a name="interactable-object-button"></a>种交互对象 （按钮）

[种交互对象](interactable-object.md)是可以对基本 HoloLens 输入作出响应的对象。 它作为方便地将应用于任何对象的预设/脚本提供。 例如，可以使您的场景中的咖啡杯种交互，并响应如注视、 敲击、 导航和操作手势输入。 [了解详细信息](interactable-object.md)

![nteractable 对象](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>对象集合

[对象集合](object-collection.md)是的有助于布局中各种形状的多个对象的一个对象。 它支持平面、 圆柱体、 球体和散点图。 可以配置其他属性，如半径，数量的行和间距。 [了解详细信息](object-collection.md)

![对象集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

将默认情况下，在其中观望用户位置中放置全息目前启动应用程序。 这有时会导致不需要的结果，如全息背后墙或中间表放置。 Fitbox 允许用户使用的视线移动来确定放置全息图的位置。 它由用简单的 PNG 图像纹理可轻松地自定义与你自己的映像或三维对象。

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>技术细节

有关脚本和预设定期表的元素应用[混合现实设计实验室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)。

## <a name="application-examples"></a>应用程序示例

以下是有关您可以创建通过利用此项目中的组件的一些建议。

### <a name="stock-data-visualization-app"></a>股票数据可视化应用

与定期表的元素的示例中使用的相同控件和交互模型，您可以构建应用它将直观显示股票市场数据。 此示例使用对象集合控件进行布局球面形状中的常用数据。 您可以假设其中无法以有趣的方式显示有关每个股票的其他信息的详细信息视图。

![应用程序示例：财务 (第 1 个 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![应用程序示例：财务 (共 2 个 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![应用程序示例：财务 3 部分 （共 3）](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*下面举例说明如何在财务应用程序中使用元素示例应用程序的定期表中使用的对象集合*

### <a name="sports-app"></a>体育应用

这是可视化对象集合和其他组件的定期表中的元素示例应用程序使用的运动数据的示例。

![应用程序示例：体育 (第 1 个 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![应用程序示例：体育 (共 2 个 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![应用程序示例：体育 3 部分 （共 3）](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*在体育应用程序中使用对象集合的元素示例 appcould 定期表中的使用方式的示例*

## <a name="about-the-author"></a>关于作者

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>盾 Yoon Park</b><br>UX 设计人员 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>请参阅

* [种交互的对象](interactable-object.md)
* [对象集合](object-collection.md)
