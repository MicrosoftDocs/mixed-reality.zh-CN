---
title: 注视 Unity
description: 注视是用户在混合现实中以应用程序创建的方式为目标的主要方式。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛、头盔、unity、全息图、混合现实
ms.openlocfilehash: 8222a5199cc1ea35429f21e7490e1eff49fcd1bc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435293"
---
# <a name="head-gaze-in-unity"></a>头-注视 Unity

[注视](gaze-and-commit.md)是用户在[混合现实](mixed-reality.md)中以应用程序[创建的方式](hologram.md)为目标的主要方式。


## <a name="implementing-head-gaze"></a>实现机头

从概念上讲，[打印头](gaze-and-commit.md)的实现方式是从用户的头投影一条射线，其中的耳机是正面朝上，并确定与该射线发生冲突的内容。 在 Unity 中，用户的头位置和方向通过 Unity 主[摄像机](camera-in-unity.md)公开，特别是[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform](https://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[转换。位置](https://docs.unity3d.com/ScriptReference/Transform-position.html)。

如果调用[RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) ，则会生成一个[RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html)结构，其中包含有关冲突的信息，其中包括发生冲突的三维点，以及使用的另一 GameObject。

### <a name="example-implement-head-gaze"></a>示例：实现机头

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>最佳做法

尽管上面的示例演示了如何在更新循环中执行单个 raycast 来查找用户头所在的目标，但建议在管理打印头的单个对象中执行此操作，而不是在可能对对象传递感兴趣的任何对象中执行此操作。t 正在 gazed。 这样，你的应用程序就可以通过只对每个帧执行一个 raycast 的操作来保存处理。

## <a name="visualizing-head-gaze"></a>形象注视

就像在使用鼠标指针来定位内容并与内容交互的桌面上，你应该实现表示用户头看的[光标](cursors.md)。 这为用户提供了与交互相关的置信度。

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>标题-注视混合现实工具包 v2
可以从 MRTK v2 中的[输入管理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)访问 head。

## <a name="see-also"></a>另请参阅
* [摄像头](camera-in-unity.md)
* [光标](cursors.md)
* [头部凝视并提交](gaze-and-commit.md)
