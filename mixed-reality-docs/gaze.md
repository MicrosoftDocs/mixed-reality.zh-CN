---
title: 凝视
description: 注视是第一种形式的输入, 是混合现实中的主要目标形式。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实, 注视, 交互, 设计
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414368"
---
# <a name="gaze"></a>凝视

**注视**是第一种形式的输入, 是混合现实中的主要目标形式。 注视告诉你用户在世界中的位置, 并允许你确定其意图。 在现实生活中, 您通常会看到一个要与之交互的对象。 这与注视的情况相同。

混合现实耳机使用用户头部的位置和方向来确定其头盔向量。 可以直接将此向量视为激光指针, 直接从用户的眼睛之间直接。 当用户寻找房间时, 您的应用程序可以与这一 ray 相交, 这两种情况都具有自己的全息影像和[空间映射](spatial-mapping.md)网格, 以确定用户可能正在查看的虚拟或现实对象。

在 HoloLens 2 上, 可以通过用户的 "注视" 眼睛、"眼睛" 或 "近" 或 "远" 交互来确定交互的目标。
在 HoloLens (第一代) 上, 交互通常应从用户的打印头获取目标, 而不是尝试直接在该位置上呈现或交互。 开始交互后, 可以使用该手型的相对运动来控制[该笔势](gestures.md), 如[操作或导航](gestures.md#composite-gestures)手势。 使用沉浸式耳机, 您可以使用 "注视" 或 "支持支持" 的[运动控制器](motion-controllers.md)进行定位。

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>打印头</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>眼睛</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> 即将[推出](index.md#news-and-notes)特定于 HoloLens 2 的更多指导。


## <a name="uses-of-gaze"></a>用注视

作为混合现实开发人员, 您可以很好地使用打印头或眼睛眼睛:
* 您的应用程序可以在场景中与全息影像交叉, 以确定用户关注的位置。
* 您的应用程序可以基于用户的注视定位手势和控制器按下, 使用户能够选择、激活、抓取、滚动或以其他方式与全息影像交互。
* 您的应用程序可让用户在实际的表面上放置全息影像, 方法是将其表面与空间映射网格进行交叉处理。
* 您的应用程序可以知道用户*不*在查找重要对象的方向时, 这可能会导致您的应用程序将视觉和音频提示转换为该对象。

## <a name="cursor"></a>Cursor

对于 "注视", 大多数应用程序都应使用[游标](cursors.md)(或其他听觉/视觉指示) 来让用户信任他们要与之交互的内容。 通常将此光标置于世界上, 其中其打印头看起来先与一个对象 (可能是全息图或真实表面) 相交。

![用于显示注视的视觉对象示例](images/cursor.jpg)<br>
*用于显示注视的视觉对象示例*

对于眼睛, 我们通常建议*不要*显示游标, 因为这可能会使用户迅速变得杂乱。 相反, 突出强调视觉对象目标或使用非常模糊的光标, 以使用户与之交互的对象更有把握。 有关详细信息, 请查看有关 HoloLens 2 上[基于目视的输入的设计指南](eye-tracking.md)。

## <a name="giving-action-to-the-users-gaze"></a>向用户的注视提供操作

一旦用户使用了其注视来确定全息图或现实世界对象的目标, 下一步就是对该对象执行操作。 用户采取行动的主要方式是通过[手势](gestures.md)、[运动控制器](motion-controllers.md)和[语音](voice-input.md)。

## <a name="see-also"></a>请参阅
* [MR 输入 210：打印头](holograms-210.md)
* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [Unity 中的头盔](gaze-in-unity.md)
* [目视-注视 HoloLens 2](eye-tracking.md)
* [使用混合现实工具包的 Unity 中的眼睛](https://aka.ms/mrtk-eyes)
