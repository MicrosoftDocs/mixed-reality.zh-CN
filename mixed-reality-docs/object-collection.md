---
title: 对象集合
description: 对象集合是一个布局控件，它可以帮助您布置预定义的三维形状中的对象的数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，控件设计
ms.openlocfilehash: 88ab0359d5083d43d5d6312ef1185f67ca0caa7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593050"
---
# <a name="object-collection"></a>对象集合

对象集合是一个布局控件，它可以帮助您布置预定义的三维形状中的对象的数组。 它支持四种不同的图面上样式-**平面、 圆柱体、 球体**并**散点图**。 您可以调整的 radius 和大小的对象和它们之间的空间。 对象集合支持 Unity 的 2D 和 3D 中的任何对象。 在中**[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**，我们创建了 Unity 脚本和[示例场景](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity)以帮助您创建的对象集合。

![使用元素应用的定期表中的对象集合](images/640px-objectcollection-hero-640px.jpg)<br>
*定期表元素示例应用程序中使用的对象集合*

## <a name="object-collection-examples"></a>对象集合示例

[元素的定期表](periodic-table-of-the-elements.md)是演示对象集合的工作原理的示例应用。 它使用对象集合进行布局中不同的形状的三维化工元素框。

![元素应用的定期表中显示的对象集合示例](images/periodictable-collections-1000px.jpg)<br>
*元素的示例应用程序的定期表中显示的对象集合示例*

### <a name="3d-objects"></a>三维对象

可以使用对象集合进行布局已导入三维对象。 以下示例演示平面和一些 3D 椅子对象的圆柱图布局。

![平面和三维对象的圆柱布局的示例](images/objectcollection-3dobjects-1000px.jpg)<br>
*平面和三维对象的圆柱布局的示例*

### <a name="2d-objects"></a>2D 对象

此外可以使用对象集合使用 2D 图像。 下面的示例演示如何 2D 图像可以显示在网格中。

![举例说明如何使用对象集合的 2D 图像](images/640px-layout-3dobjects-3.jpg)

![举例说明如何使用对象集合的 2D 图像](images/640px-layout-2dimages.jpg)<br>
*使用对象集合的 2D 图像的示例*

## <a name="see-also"></a>请参阅
* [脚本和 GitHub 上的混合现实工具包中的对象集合的预设](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)
* [种交互的对象](interactable-object.md)
