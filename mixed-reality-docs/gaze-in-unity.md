---
title: 在 Unity 中展示
description: 提供注视是用户以确定你的应用创建混合现实中全息了主要途径。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 提供注视、 unity、 全息图、 混合的现实
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453720"
---
# <a name="head-gaze-in-unity"></a>在 Unity 中的头视线移动

[注视](gaze.md)是用户以确定了主要途径[全息](hologram.md)您的应用程序中创建[混合现实](mixed-reality.md)。


## <a name="implementing-head-gaze"></a>实现头的视线移动

从概念上讲，[注视](gaze.md)实现通过投影从用户的头部向前面向并确定它们耳机所在 ray 的射线与有冲突。 在 Unity 中，用户的头位置和方向公开通过 Unity Main[照相机](camera-in-unity.md)，具体而言[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)并[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)。

调用[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)会导致[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)结构，其中包含有关包括发生冲突的三维点碰撞效果和其他 GameObject 的视线移动 ray 信息使用发生碰撞。

### <a name="example-implement-head-gaze"></a>例如：实现头的视线移动

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

尽管上面的示例演示了如何在更新循环中，若要查找的视线移动目标单一 raycast，建议执行此操作管理而不是执行此操作可能会对感兴趣正在 gazed 处的对象的任何对象中的视线移动单个对象中。 这允许您通过执行每个帧的只是一个提供注视 raycast 保存处理的应用程序。

## <a name="visualizing-gaze"></a>可视化的视线移动

就像在桌面上使用其中的鼠标指针来面向和交互使用内容，则应实现[游标](cursors.md)，它表示用户的视线移动。 这在如何为用户增添了信心地与之交互。

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>对此混合现实 Toolkit v2
您可以访问从注视[输入管理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)MRTK v2 中。

## <a name="see-also"></a>请参阅
* [摄像头](camera-in-unity.md)
* [注视输入](gaze.md)
* [光标](cursors.md)
* [设定凝视目标](gaze-targeting.md)
