---
title: 在 Unity 中展示
description: 提供注视是用户以确定你的应用创建混合现实中全息了主要途径。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 提供注视、 unity、 全息图、 混合的现实
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593008"
---
# <a name="gaze-in-unity"></a>在 Unity 中展示

[注视](gaze.md)是用户以确定了主要途径[全息](hologram.md)您的应用程序中创建[混合现实](mixed-reality.md)。

## <a name="implementing-gaze"></a>实现的视线移动

从概念上讲，[注视](gaze.md)实现通过投影从用户的头部向前面向并确定它们耳机所在 ray 的射线与有冲突。 在 Unity 中，用户的头位置和方向公开通过 Unity Main[照相机](camera-in-unity.md)，具体而言[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)并[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)。

调用[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)会导致[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)结构，其中包含有关包括发生冲突的三维点碰撞效果和其他 GameObject 的视线移动 ray 信息使用发生碰撞。

### <a name="example-implement-gaze"></a>例如：实现的视线移动

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

## <a name="gaze-in-mixed-reality-toolkit"></a>对此混合的现实工具包
当您导入[MRTK 发布 Unity 包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或从克隆项目[GitHub 存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，要在 Unity 中查找新菜单混合现实工具包。 在配置菜单中，你会看到菜单应用混合现实场景设置。 当您单击它时，它默认照相机中删除，并添加基础组件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，并[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。

![MRTK 场景设置菜单](images/MRTK_Input_Menu.png)<br>
*MRTK 场景设置菜单*

![自动场景中 MRTK 的安装程序](images/MRTK_HowTo_Input1.png)<br>
*自动场景中 MRTK 的安装程序*

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a>注视混合现实工具包中的相关的脚本
混合现实工具包包括 InputManager prefab [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs)并[注视稳定器](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs)。 下[SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs)，可以分配自定义光标。 默认情况下，经过动画处理[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)分配。

[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)并[CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)说明如何可视化你的视线移动使用游标。

## <a name="see-also"></a>请参阅
* [摄像头](camera-in-unity.md)
* [Gaze](gaze.md)
* [游标](cursors.md)
* [目标的视线移动](gaze-targeting.md)
