---
title: 凝视
description: 提供注视是第一种形式的输入，主窗体的目标中混合现实。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实、 提供注视、 交互，设计
ms.openlocfilehash: 9e50067f9dfeacf3dce5ea9a928990d1b142e4d0
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453706"
---
# <a name="gaze"></a>凝视

**注视**是第一种形式的输入，主窗体的目标中混合现实。 提供注视告诉您其中用户在世界中查找，并可以确定其意图。 在现实生活中，您将通常看到在你想要与之交互的对象。 这也同样适用于的视线移动。

混合的现实耳机使用位置和方向的用户的头来确定其头的视线移动矢量。 您可以作为激光指针直接向前从用户的眼球之间直接将此向量。 如用户看起来的房间内，你的应用程序如何相互交叉此 ray 使用其自己全息和与[空间映射](spatial-mapping.md)网格来确定您的用户可以查看哪些虚拟还是实际对象。

HoloLens 2 上的交互可通过用户的头视线移动，关注的视线移动定位或通过附近或远分发的交互。
HoloLens 上 （第 1 代），交互应通常是其目标从用户的头的视线移动，而不是非试着来呈现或直接在现有的位置进行交互。 一旦启动交互，相对动作的手可能用于控制[手势](gestures.md)，如同[操作或导航](gestures.md#composite-gestures)手势。 可以使用沉浸式耳机，面向使用任一头的视线移动或指向能够[动作控制器](motion-controllers.md)。

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>功能</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td> Head 的视线移动</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr><tr>
<td> 关注的视线移动</td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。


## <a name="uses-of-gaze"></a>使用的视线移动

混合的现实开发人员，您可以执行许多操作头或关注的视线移动：
* 您的应用程序可以相交与您的场景中全息的视线移动以确定用户的注意力的位置。
* 你的应用可面向手势和控制器按下按钮可以基于用户的视线移动，让用户选择、 激活、 获取、 向下滚动，或与其全息否则交互。
* 您的应用程序可以让用户中放置全息实际的应用层与空间映射网格其提供注视射线相交。
* 您的应用程序可以知道用户何时*不*查找重要的对象，这可能会导致您的应用程序提供视频和音频提示，用于启用向该对象的方向。

## <a name="cursor"></a>Cursor

对于头的视线移动，大多数应用程序应使用[游标](cursors.md)（或其他听觉/visual 表明） 若要在如何使用户确信它们要与之交互。 也通常将此游标放置在世界上其头的视线移动 ray 首先相交一个对象，它可能是一张全息图或实际的图面。

![若要显示的视线移动示例 visual 游标](images/cursor.jpg)<br>
*若要显示的视线移动示例 visual 游标*

对于关注的视线移动，我们通常建议*不*显示游标，这很快就明显，令人讨厌的用户。 而是略有突出显示视觉目标或非常不清晰的关注游标用于提供有关用户是要与之交互的置信度。 有关详细信息，请查看我们[关注基于输入的设计指南](eye-tracking.md)HoloLens 2 上。

## <a name="giving-action-to-the-users-gaze"></a>向用户的视线移动操作

用户具有目标全息图或使用其的视线移动的实际对象，其下一步是对该对象执行操作。 用户可以执行操作的主要方法是： 通过[手势](gestures.md)，[动作控制器](motion-controllers.md)并[语音](voice-input.md)。

## <a name="see-also"></a>请参阅
* [MR 输入 210：Head 的视线移动](holograms-210.md)
* [DirectX 中的头部和眼部凝视](gaze-in-directx.md)
* [在 Unity 中的头视线移动](gaze-in-unity.md)
* [眼睛追踪 HoloLens 2 上](eye-tracking.md)
* [在 Unity 中使用混合现实工具包的眼睛视线移动](https://aka.ms/mrtk-eyes)
