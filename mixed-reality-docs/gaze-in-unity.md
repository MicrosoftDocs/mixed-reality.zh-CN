---
title: 注视 Unity
description: 注视是用户在混合现实中以应用程序创建的方式为目标的主要方式。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 注视, unity, 全息影像, 混合现实
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453720"
---
# <a name="head-gaze-in-unity"></a>Unity 中的头盔

[注视](gaze.md)是用户在[混合现实](mixed-reality.md)中以应用程序[创建的方式](hologram.md)为目标的主要方式。


## <a name="implementing-head-gaze"></a>实现打印头

从概念上讲,[注视](gaze.md)的实现方式是: 从用户的头投影一条射线, 其中的耳机是正面朝上, 并确定与该射线发生冲突的情况。 在 Unity 中, 用户的头位置和方向通过 Unity 主[摄像机](camera-in-unity.md)公开, 特别是[UnityEngine](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform](http://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[转换。位置](http://docs.unity3d.com/ScriptReference/Transform-position.html)。

如果调用[RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) , 则会生成一个[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)结构, 其中包含有关冲突的信息, 包括发生冲突的三维点, 以及使用 "注视" 光线与的另一个 GameObject。

### <a name="example-implement-head-gaze"></a>例如：实现打印头

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

### <a name="best-practices"></a>最佳方案

尽管上面的示例演示了如何在更新循环中执行单个 raycast 来查找注视目标, 但建议在管理注视的单个对象中执行此操作, 而不是在可能对要在 gazed 的对象感兴趣的任何对象中执行此操作。 这样, 你的应用程序就可以通过只对每个帧执行一个注视 raycast 来保存处理。

## <a name="visualizing-gaze"></a>可视化注视

就像在使用鼠标指针来定位内容并与内容交互的桌面上, 你应该实现表示用户注视的[光标](cursors.md)。 这为用户提供了与交互相关的置信度。

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>注视混合现实工具包 v2
可以从 MRTK v2 中的[输入管理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)访问注视。

## <a name="see-also"></a>请参阅
* [摄像头](camera-in-unity.md)
* [注视输入](gaze.md)
* [光标](cursors.md)
* [设定凝视目标](gaze-targeting.md)
