---
title: 边界框和应用栏
description: 应用栏是一个对象级菜单, 其中包含一系列按钮, 它们显示在全息图边界的下边缘。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, 应用栏, 边界框
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829686"
---
# <a name="bounding-box-and-app-bar"></a>边界框和应用栏
!["边界" 是用于在混合现实中进行对象操作的标准接口。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>什么是边界框？

"边界" 是用于在混合现实中进行对象操作的标准接口。 它向用户提供当前可调整对象的 affordance。 角告诉用户对象还可以缩放。 此视觉对象 affordance 向用户显示对象的总区域–即使它在调整模式之外不可见。 这一点特别重要, 因为如果不存在, 则与另一个对象或表面对齐的对象可能看起来好像不应存在的空间。 在 HoloLens 2 上, 边界框适用于直接操作, 并响应用户的 finger's 邻近性。 它显示了视觉反馈, 可帮助用户感知与对象的距离。 

![HoloLens 通过边界框缩放对象的观点](images/HoloLens2_BoundingBox.gif)<br>
*通过边界框缩放对象*

边界框的角上的控点遵循用于调整刻度的广泛理解的模式。 

![HoloLens 通过边界框旋转对象的观点](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*通过边界框旋转对象*


![视觉对象反馈](images/HoloLens2_Proximity.gif)<br>
*基于邻近性的视觉反馈*

边界框边缘的垂直矩形实用是旋转指示器。 这样, 用户就可以更好地调整其放置的全息影像。 它们不仅可以进行调整和缩放, 还可以进行旋转。

* 对于 Unity 应用开发, 请参阅[混合现实工具包上的边界框-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>什么是应用栏？

应用栏是一个对象级菜单, 其中包含一系列按钮, 它们显示在全息图边界的下边缘。 此模式通常用于使用户能够删除和调整全息影像。

由于此模式与世界锁定的对象一起使用, 因此当用户在对象周围移动时, 应用栏将始终显示在最靠近用户的对象端。 尽管这不是 billboarding 的, 但它实际上实现了相同的结果;防止用户遮蔽或阻止在其环境中的其他位置可用的功能。

![浏览全息图。 应用栏如下所示。](images/HoloLens2_AppBarFollowing.gif)<br>
*浏览全息图, 应用栏如下所示*

应用栏的设计主要是在用户的环境中管理已放置对象的方式。 与边界框结合使用, 用户可以完全控制对象在混合现实中的位置和方式。

* 有关 Unity 应用开发, 请参阅[混合现实工具包上的应用栏-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>请参阅
* [可交互对象](interactable-object.md)
* [Unity 中的文本](text-in-unity.md)
* [对象集合](object-collection.md)
* [显示进度](progress.md)
