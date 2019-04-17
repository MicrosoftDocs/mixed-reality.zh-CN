---
title: 在 Unity 中的坐标系统
description: 了解如何构建就位，站着、 聊天室规模和世界级混合现实体验在 Unity 中。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 坐标系统、 空间坐标系统、 只方向、 固定缩放、 现有规模房间的小数位数，全球规模，360 度就位，现有、 聊天室、 世界、 规模、 位置、 方向、 Unity、 定位、 空间定位点、 全球定位点，世界上锁定，世界上锁定，锁定正文，正文锁定，跟踪丢失、 locatability、 边界，自动
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593058"
---
# <a name="coordinate-systems-in-unity"></a>在 Unity 中的坐标系统

Windows Mixed Reality 支持跨范围广泛的应用[体验刻度](coordinate-systems.md)，从仅限方向的和固定缩放应用程序会通过聊天室规模的应用。 上 HoloLens，可以更进一步并构建全球规模的应用，超出了 5 米，引导用户浏览整个 floor 的建筑物和更高版本。

构建在 Unity 中的混合的现实体验的第一步是确定哪个[体验规模](coordinate-systems.md)应用的目标。

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>构建仅限方向的或固定刻度体验

**命名空间：***UnityEngine.XR*<br>
**类型：***XRDevice*

若要生成**仅方向**或**就位规模体验**，必须设置 Unity 为固定且跟踪空间类型。 这将设置 Unity 的世界坐标系统来跟踪[固定参考框架](coordinate-systems.md#spatial-coordinate-systems)。 在保持静止跟踪模式下，内容放置正前方照相机的默认位置在编辑器中 （正向是-Z） 在应用启动时将显示用户。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**命名空间：***UnityEngine.XR*<br>
**类型：***InputTracking*

有关纯**仅限方向的体验**如 360 度视频查看器 （其中位置头更新将未免效果），然后，可以设置[XR。InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)为 true:

```cs
InputTracking.disablePositionalTracking = true;
```

有关**装规模体验**，以使用户能够更高版本自动就位的源，可以调用[XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法：

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>构建现有规模或聊天室缩放体验

**命名空间：***UnityEngine.XR*<br>
**类型：***XRDevice*

有关**现有规模**或**聊天室规模体验**，都需要将内容放相对于基底。 有关用户的原因使用 floor **[空间阶段](coordinate-systems.md#spatial-coordinate-systems)**、 floor 级别来源和可选空间边界表示用户的定义、 设置期间首次运行。

若要确保的 Unity 运行时带有 floor 级别其世界坐标系统，可以设置为跟踪空间类型 RoomScale 的 Unity 并确保集成功：

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
* 如果 SetTrackingSpaceType 返回 true，Unity 已成功切换其世界坐标系统来跟踪[阶段参考框架](coordinate-systems.md#spatial-coordinate-systems)。
* 如果 SetTrackingSpaceType 返回 false，Unity 不能切换到阶段参考框架，有可能，因为用户尚未设置甚至占地在其环境中。 这并不常见，但如果在不同的房间内设置阶段，设备已移至当前的房间，而无需设置新的阶段的用户则可能发生。

一旦您的应用程序已成功设置跟踪空间类型，内容在 y 轴上放置 RoomScale = 的 0 平面将显示在地板。 （0，0，0） 处的原点将在其中用户花了安装过程中的空间，-z 表示的向前他们在安装过程中面临着的车间的具体位置。

**命名空间：***UnityEngine.Experimental.XR*<br>
**类型：***边界*

在脚本代码中，随后可以调用你的 TryGetGeometry 方法是 UnityEngine.Experimental.XR.Boundary 类型获取边界多边形指定 TrackedArea 边界类型。 如果用户定义的边界 （重新获取顶点的列表），您知道安全地交付**聊天室规模体验**给用户，他们可以在其中引导在场景周围创建。

请注意，当用户接近其，系统会自动呈现边界。 您的应用程序不需要使用此多边形呈现自身的边界。 但是，您可以选择布局使用此边界的多边形、 为确保用户能够以物理方式访问这些对象，而 teleporting 应用场景对象：

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>构建全球规模体验

**命名空间：***UnityEngine.XR.WSA*<br>
**类型：***WorldAnchor*

若为 true**世界级体验**上允许用户浏览超出 5 米的 HoloLens，你将需要超出所使用的空间缩放体验的新技术。 将使用的一个关键技术是创建[空间的定位点](coordinate-systems.md#spatial-anchors)锁定的精确就地真实的场景中，而不考虑用户具有漫游延伸的范围，全息群集，然后[更高版本中再次查找这些全息会话](coordinate-systems.md#spatial-anchor-persistence)。

在 Unity 中，创建空间的定位点通过添加**WorldAnchor** Unity 组件给一个 gameobject 对象。

### <a name="adding-a-world-anchor"></a>添加世界定位点

若要添加世界定位点，请调用 AddComponent<WorldAnchor>你想要在现实生活中的定位点将转换到游戏对象上的 （)。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

就这么简单！ 此游戏对象现在将定位到其当前物理世界中的位置-可能会看到段时间，以确保该物理的对齐方式略有调整其 Unity 世界坐标。 使用[持久性](persistence-in-unity.md)若要查找此锚定位置再次在将来的应用程序会话中。

### <a name="removing-a-world-anchor"></a>删除世界定位点

如果你不再想 GameObject 锁定到物理世界位置，并且不想将其移动此帧，则可以对全球定位点组件仅调用销毁。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

如果你想要移动此帧的 GameObject，你需要改为调用 DestroyImmediate。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>移动一个世界锚定的 GameObject

全球定位点在其上时，不能移动 GameObject 的。 如果您需要移动此帧的 GameObject，您需要：
1. DestroyImmediate 世界定位点组件
2. 移动的 GameObject
3. 将新的全球定位点组件添加到的 GameObject。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>处理 Locatability 更改

WorldAnchor 可能不是可定位在某个点在现实环境中的时间。 如果发生这种情况，Unity 将不更新的转换的定位的对象。 这还可以更改运行应用时。 未能在 locatability 中处理这些更改将导致要不显示在世界上正确的物理位置的对象。

要将通知 locatability 更改：
1. 订阅 OnTrackingChanged 事件
2. 处理事件

**OnTrackingChanged**基础空间定位点之间的不是可定位与可定位状态发生更改时，将调用事件。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

然后处理该事件：

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

有时定位点位于立即情况。 在这种情况下，定位点此 isLocated 属性将设置为 true 时 AddComponent<WorldAnchor>（） 返回。 因此，不会触发 OnTrackingChanged 事件。 清理模式是在附加定位点之后调用具有初始 IsLocated 状态您 OnTrackingChanged 的处理程序。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>跨设备共享的定位点

可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>从您的应用程序然后可以跨多个 HoloLens、 iOS 和 Android 设备找到本地 WorldAnchor 创建持久的云定位点。  通过在多个设备之间共享公共空间定位点，每个用户可以看到呈现相对于同一物理位置中的锚点的内容。  这样实时共享体验。

若要开始构建在 Unity 中的共享的体验，请尝试出 5 分钟<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">快速入门 Azure 空间的定位点 Unity</a>。

你可以在 Azure 空间的定位点与您使用启动并运行，然后<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">创建并在 Unity 中定位的定位点</a>。

## <a name="see-also"></a>请参阅
* [体验刻度](coordinate-systems.md#mixed-reality-experience-scales)
* [空间阶段](coordinate-systems.md#stage-frame-of-reference)
* [跟踪 Unity 中丢失](tracking-loss-in-unity.md)
* [空间的定位点](spatial-anchors.md)
* [在 Unity 中的暂留](persistence-in-unity.md)
* [在 Unity 中的共享的体验](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空间的定位点适用于 Unity SDK</a>