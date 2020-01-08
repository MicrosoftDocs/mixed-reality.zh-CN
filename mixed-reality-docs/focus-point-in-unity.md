---
title: Unity 中的焦点
description: 通过设置焦点在 Unity 中手动优化全息影像稳定性
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，焦点，焦点平面，稳定平面，稳定点，reprojection，LSR，深度缓冲区
ms.openlocfilehash: 9a7f30b552242b24a9a7b260b6574690a27d2c1d
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502618"
---
# <a name="focus-point-in-unity"></a>Unity 中的焦点

**命名空间：** *UnityEngine. XR*<br>
**类型**： *HolographicSettings*

可以将[焦点](hologram-stability.md#reprojection)设置为提供有关如何在当前显示的全息影像上最好地执行稳定的提示。

如果要在 Unity 中设置焦点，则需要使用*HolographicSettings. SetFocusPointForFrame （）* 设置每个框架。 如果未为帧设置焦点，则将使用默认的稳定平面。

> [!NOTE]
> 默认情况下，新的 Unity 项目设置了 "启用深度缓冲共享" 选项。  使用此选项时，在沉浸式桌面耳机上运行的 Unity 应用或运行 Windows 10 4 月2018更新（RS4）或更高版本的 HoloLens 将向 Windows 提交深度缓冲区以自动优化全息影像稳定性，无需应用指定焦点：
> * 在沉浸式桌面耳机上，这将启用基于像素深度的 reprojection。
> * 在运行 Windows 10 4 月2018更新或更高版本的 HoloLens 上，这将分析深度缓冲区以自动选择最佳的稳定平面。
>
> 这两种方法都应该提供更好的图像质量，而无需由您的应用程序显式工作，从而为每个帧选择焦点。  请注意，如果你确实手动提供了焦点，这将替代上述自动行为，并且通常会降低全息图的稳定性。  通常，仅当你的应用在尚未更新到 Windows 10 4 2018 月版更新的 HoloLens 上运行时，才应指定手动焦点点。

### <a name="example"></a>示例

有多种方法可设置焦点，如*SetFocusPointForFrame*静态函数上的可用重载所建议的那样。 下面提供了一个简单的示例，可将焦点平面设置为每个帧的提供的对象：

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

请注意，如果焦点对象最终出现在用户后面，则上述简单代码可能最终会降低全息体稳定性。  这就是通常应设置 "启用深度缓冲区共享" 而不是手动指定焦点的原因。

### <a name="see-also"></a>另请参阅
* [稳定平面](hologram-stability.md#reprojection)
