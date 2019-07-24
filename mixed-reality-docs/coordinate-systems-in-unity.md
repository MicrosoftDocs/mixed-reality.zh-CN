---
title: 在 Unity 中协调系统
description: 了解如何在 Unity 中构建具有固定、良好、房间规模和世界规模的混合现实体验。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 坐标系统, 空间坐标系统, 仅限方向, 固定规模, 房间, 房间-缩放, 世界规模, 360 度, 固定, 固定, 房间, 世界, 缩放, 位置, 方向, Unity, 定位, 空间锚, 世界锚, 世界锁定,世界锁定、正文锁定、正文锁定、跟踪丢失、locatability、界限、recenter
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525960"
---
# <a name="coordinate-systems-in-unity"></a>在 Unity 中协调系统

Windows Mixed Reality 在各种[经验](coordinate-systems.md)范围内支持应用, 从仅限方向和大规模应用, 再到房间规模的应用。 在 HoloLens 上, 你可以进一步构建全球规模的应用程序, 让用户经历5米以上的工作, 探索一座建筑的整个楼层。

在 Unity 中构建混合现实体验的第一步是确定应用将面向哪些[经验](coordinate-systems.md)。

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>构建仅限方向或固定规模的体验

**命名空间：** *UnityEngine.XR*<br>
**类型：**  *XRDevice*

若要生成**仅限方向**或**固定规模的体验**, 必须将 Unity 设置为静止跟踪空间类型。 这将设置 Unity 的世界坐标系统以跟踪[固定的引用框架](coordinate-systems.md#spatial-coordinate-systems)。 在静止跟踪模式下, 当应用程序启动时, 位于面板默认位置 (正向-Z) 前面的编辑器中的内容将显示在用户的前面。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**命名空间：** *UnityEngine.XR*<br>
**类型：**  *InputTracking*

对于纯**仅限方向的体验**, 例如360度视频查看器 (其中位置标题更新会破坏错觉), 可以设置[XR。InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)为 true:

```cs
InputTracking.disablePositionalTracking = true;
```

对于**大规模体验**, 若要让用户在以后 recenter 原位置, 可以调用[XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>构建大规模或会议室规模的体验

**命名空间：** *UnityEngine.XR*<br>
**类型：**  *XRDevice*

对于**大规模**或**房间规模的体验**, 需要相对于楼层放置内容。 使用 **[空间阶段](coordinate-systems.md#spatial-coordinate-systems)** (表示用户在首次运行期间设置的已定义的层级来源和可选房间边界) 的原因。

若要确保 Unity 在底层的世界坐标系统中运行, 可以将 Unity 设置为 RoomScale 跟踪空间类型, 并确保设置成功:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* 如果 SetTrackingSpaceType 返回 true, 则 Unity 已成功切换其世界坐标系统以跟踪[引用的阶段框架](coordinate-systems.md#spatial-coordinate-systems)。
* 如果 SetTrackingSpaceType 返回 false, 则 Unity 无法切换到引用的阶段框架, 这可能是因为用户在其环境中尚未设置一层。 这种情况并不常见, 但如果阶段是在不同的房间内设置的并且设备已移动到当前房间, 而用户没有设置新阶段, 则可能会发生这种情况。

应用成功设置 RoomScale 跟踪空间类型后, 放置在 y = 0 平面上的内容将显示在地面上。 位于 (0, 0, 0) 的原点将是用户在房间安装期间考验的特定位置, 并以-Z 表示在安装过程中所面临的正向方向。

**命名空间：** *UnityEngine. XR*<br>
**类型：** *边缘*

在脚本代码中, 您可以对 UnityEngine 调用 TryGetGeometry 方法来获取边界多边形, 并指定 "TrackedArea" 的边界类型。 如果用户定义了边界 (返回顶点的列表), 则你知道向用户提供**房间规模的体验**是安全的, 他们可以在其中浏览你创建的场景。

请注意, 当用户接近边界时, 系统将自动呈现边界。 您的应用程序不需要使用此多边形来呈现边界本身。 不过, 您可以选择使用此边界多边形布局场景对象, 以确保用户可以在不 teleporting 的情况下以物理方式访问这些对象:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>构建全球范围的体验

**命名空间：**  *UnityEngine.XR.WSA*<br>
**类型：** *WorldAnchor*

对于 HoloLens 上真正的**全球规模体验**, 让用户游离5米以上, 你将需要超出用于房间规模体验的新技术。 你将使用的一项关键方法是创建一个[空间定位点](coordinate-systems.md#spatial-anchors), 以便在物理世界中精确地锁定全息机的分类, 无论用户漫游到多远, 然后[在以后的会话中再次查找这些全息影像](coordinate-systems.md#spatial-anchor-persistence)。

在 Unity 中, 可以通过将**WorldAnchor** Unity 组件添加到 GameObject 来创建空间锚。

### <a name="adding-a-world-anchor"></a>添加世界锚

若要添加世界锚, 请在<WorldAnchor>游戏对象上调用 AddComponent (), 将其转换为要锚定到现实世界中的转换。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

就这么简单！ 现在, 此游戏对象将锚定到其在物理世界中的当前位置-你可能会看到其 Unity 世界坐标在一段时间后会略微调整, 以确保物理对齐。 使用[持久性](persistence-in-unity.md)在未来的应用程序会话中再次查找此定位位置。

### <a name="removing-a-world-anchor"></a>删除世界锚

如果不再希望 GameObject 锁定到物理世界位置, 并且不打算将其移动到此帧, 则可以只在世界锚点组件上调用销毁。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

如果要将 GameObject 移动到此帧, 则需改为调用 DestroyImmediate。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>移动世界定位的 GameObject

GameObject 在世界锚点上时无法移动。 如果需要将 GameObject 移动到此框架, 需要执行以下操作:
1. DestroyImmediate 世界锚组件
2. 移动 GameObject
3. 向 GameObject 添加新的世界锚点组件。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>处理 Locatability 更改

在物理环境中, 可能无法在某个时间点定位 WorldAnchor。 如果出现这种情况, 则 Unity 不会更新定位对象的转换。 在应用程序运行时, 这也可能会更改。 如果无法处理 locatability 中的更改, 则会导致对象不显示在世界上正确的物理位置。

若要获得有关 locatability 更改的通知:
1. 订阅 OnTrackingChanged 事件
2. 处理事件

每当基础空间锚点在正在定位的状态与不能定位的状态之间发生变化时, 将调用**OnTrackingChanged**事件。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

然后处理事件:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

有时会立即定位锚点。 在这种情况下, 当 AddComponent<WorldAnchor>() 返回时, 定位点的 isLocated 属性将设置为 true。 因此, 不会触发 OnTrackingChanged 事件。 清理模式是在附加定位点后使用初始 IsLocated 状态调用 OnTrackingChanged 处理程序。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>跨设备共享锚

你可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a>从本地 WorldAnchor 创建持久的云锚点, 你的应用可以在多个 HoloLens、IOS 和 Android 设备中查找。  通过在多个设备之间共享公用空间定位点, 每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。  这可实现实时共享体验。

若要开始在 Unity 中构建共享体验, 请尝试执行5分钟的<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。

启动并运行 Azure 空间锚点后, 便可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。

## <a name="see-also"></a>请参阅
* [体验规模](coordinate-systems.md#mixed-reality-experience-scales)
* [空间阶段](coordinate-systems.md#stage-frame-of-reference)
* [Unity 中的跟踪丢失](tracking-loss-in-unity.md)
* [空间定位点](spatial-anchors.md)
* [Unity 中的持久性](persistence-in-unity.md)
* [Unity 中的共享体验](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a>