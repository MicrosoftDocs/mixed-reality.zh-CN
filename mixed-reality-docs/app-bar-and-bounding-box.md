---
title: 边界框和应用程序栏
description: 应用程序栏是对象级菜单包含一系列显示一张全息图边界的下边缘的按钮。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality 应用栏，边界框
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829686"
---
# <a name="bounding-box-and-app-bar"></a>边界框和应用程序栏
![边界是混合现实中的对象操作的标准接口。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>边界框是什么？

边界是混合现实中的对象操作的标准接口。 它为用户提供功能的对象是当前可调整的可见性:。 角将告诉用户还可以缩放对象。 即使不可见的调整模式，这样 visual 一向用户显示对象 – 总的区域。 这一点尤其重要，因为如果存在不是，对象对齐到另一个对象或面似乎行为就如同时不应在那里它周围的空间。 HoloLens 2 上的边界框适用于直接手动操作和响应用户的手指的邻近性。 它显示了可视反馈以帮助用户感知从该对象的距离。 

![HoloLens-的角度来看的缩放通过边界框的对象](images/HoloLens2_BoundingBox.gif)<br>
*缩放通过边界框的对象*

中的边界框角的图柄按照调整规模的广为人知的模式。 

![HoloLens-的角度来看旋转通过边界框的对象](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*旋转对象通过边界框*


![在手动邻近的可视反馈](images/HoloLens2_Proximity.gif)<br>
*邻近的可视反馈*

边界框的边缘上的垂直矩形等是旋转指示符。 此选项会使用户更多的精细调整能够对其置入全息。 不仅可以在调整和缩放，但现在还包括旋转。

* Unity 应用程序开发，请参阅[边界框上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>什么是应用程序栏？

应用程序栏是对象级菜单包含一系列显示一张全息图边界的下边缘的按钮。 此模式通常用于使用户能够删除和调整全息。

由于此模式用于访问对象，该对象周围移动用户而言是完全锁定状态，应用程序栏将始终显示在最靠近用户的选择对象端。 虽然这不公告板，它有效地实现相同的结果;阻止用户的位置以遮蔽或应可从其环境中的不同位置的块功能。

![移动办公了一张全息图。 遵循应用程序栏。](images/HoloLens2_AppBarFollowing.gif)<br>
*移动办公了一张全息图，遵循应用程序栏*

应用栏旨在主要作为一种方法来管理用户的环境中放置的对象。 耦合在一起的边界框，用户可以完全控制在何处以及如何在混合现实方向，对象。

* Unity 应用程序开发，请参阅[应用栏上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>请参阅
* [可交互对象](interactable-object.md)
* [Unity 中的文本](text-in-unity.md)
* [对象集合](object-collection.md)
* [显示进度](progress.md)
