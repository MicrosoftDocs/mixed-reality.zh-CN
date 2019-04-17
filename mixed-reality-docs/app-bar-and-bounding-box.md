---
title: 应用程序栏和边框
description: 应用程序栏是对象级菜单包含一系列显示一张全息图边界的下边缘的按钮。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality 应用栏，边界框
ms.openlocfilehash: bdce92e00193230d1f7a487f11ef0487f1d6657c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592401"
---
# <a name="bounding-box-and-app-bar"></a>边界框和应用程序栏
![边界是混合现实中的对象操作的标准接口。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>边界框是什么？

边界是混合现实中的对象操作的标准接口。 它为用户提供功能的对象是当前可调整的可见性:。 角将告诉用户还可以缩放对象。 即使不可见的调整模式，这样 visual 一向用户显示对象 – 总的区域。 这一点尤其重要，因为如果存在不是，对象对齐到另一个对象或面似乎行为就如同时不应在那里它周围的空间。 HoloLens 2 上的边界框来响应用户的手指的邻近性。 它显示了可视反馈以帮助找到了该对象的距离。 

![HoloLens-的角度来看的缩放通过边界框的对象](images/bounding-box-scale.gif)<br>
*缩放通过边界框的对象*

边界框的类似于多维数据集的角遵循用于调整规模广为人知的模式。 耦合与显式将一个对象放到"调整模式"的操作很明显，他们可以同时移动对象，但还在其环境中对它进行缩放。

![HoloLens-的角度来看旋转通过边界框的对象](images/bounding-box-rotate.gif)<br>
*旋转对象通过边界框*

边界框的边缘上球面的提示是旋转指示符。 此选项会使用户更多的精细调整能够对其置入全息。 不仅可以在调整和缩放，但现在还包括旋转。

* Unity 应用程序开发，请参阅[边界框上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="what-is-the-app-bar"></a>什么是应用程序栏？

应用程序栏是对象级菜单包含一系列显示一张全息图边界的下边缘的按钮。 此模式通常用于使用户能够删除和调整全息。

由于此模式用于访问对象，该对象周围移动用户而言是完全锁定状态，应用程序栏将始终显示在最靠近用户的选择对象端。 虽然这不公告板，它有效地实现相同的结果;阻止用户的位置以遮蔽或应可从其环境中的不同位置的块功能。

![移动办公了一张全息图。 遵循应用程序栏。](images/holobar-followuser.gif)<br>
*移动办公了一张全息图，遵循应用程序栏*

应用栏旨在主要作为一种方法来管理用户的环境中放置的对象。 耦合在一起的边界框，用户可以完全控制在何处以及如何在混合现实方向，对象。

* Unity 应用程序开发，请参阅[应用栏上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>请参阅
* [边界框上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)
* [应用栏上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)
* [种交互的对象](interactable-object.md)
* [在 Unity 中的文本](text-in-unity.md)
* [对象集合](object-collection.md)
* [显示进度](progress.md)
