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
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="798cc-104">在 Unity 中的坐标系统</span><span class="sxs-lookup"><span data-stu-id="798cc-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="798cc-105">Windows Mixed Reality 支持跨范围广泛的应用[体验刻度](coordinate-systems.md)，从仅限方向的和固定缩放应用程序会通过聊天室规模的应用。</span><span class="sxs-lookup"><span data-stu-id="798cc-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="798cc-106">上 HoloLens，可以更进一步并构建全球规模的应用，超出了 5 米，引导用户浏览整个 floor 的建筑物和更高版本。</span><span class="sxs-lookup"><span data-stu-id="798cc-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="798cc-107">构建在 Unity 中的混合的现实体验的第一步是确定哪个[体验规模](coordinate-systems.md)应用的目标。</span><span class="sxs-lookup"><span data-stu-id="798cc-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="798cc-108">构建仅限方向的或固定刻度体验</span><span class="sxs-lookup"><span data-stu-id="798cc-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="798cc-109">\**命名空间：\*\*\*UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="798cc-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="798cc-110">\**类型：\*\*\*XRDevice*</span><span class="sxs-lookup"><span data-stu-id="798cc-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="798cc-111">若要生成**仅方向**或**就位规模体验**，必须设置 Unity 为固定且跟踪空间类型。</span><span class="sxs-lookup"><span data-stu-id="798cc-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="798cc-112">这将设置 Unity 的世界坐标系统来跟踪[固定参考框架](coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="798cc-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="798cc-113">在保持静止跟踪模式下，内容放置正前方照相机的默认位置在编辑器中 （正向是-Z） 在应用启动时将显示用户。</span><span class="sxs-lookup"><span data-stu-id="798cc-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="798cc-114">\**命名空间：\*\*\*UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="798cc-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="798cc-115">\**类型：\*\*\*InputTracking*</span><span class="sxs-lookup"><span data-stu-id="798cc-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="798cc-116">有关纯**仅限方向的体验**如 360 度视频查看器 （其中位置头更新将未免效果），然后，可以设置[XR。InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html)为 true:</span><span class="sxs-lookup"><span data-stu-id="798cc-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="798cc-117">有关**装规模体验**，以使用户能够更高版本自动就位的源，可以调用[XR。InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法：</span><span class="sxs-lookup"><span data-stu-id="798cc-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="798cc-118">构建现有规模或聊天室缩放体验</span><span class="sxs-lookup"><span data-stu-id="798cc-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="798cc-119">\**命名空间：\*\*\*UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="798cc-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="798cc-120">\**类型：\*\*\*XRDevice*</span><span class="sxs-lookup"><span data-stu-id="798cc-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="798cc-121">有关**现有规模**或**聊天室规模体验**，都需要将内容放相对于基底。</span><span class="sxs-lookup"><span data-stu-id="798cc-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="798cc-122">有关用户的原因使用 floor **[空间阶段](coordinate-systems.md#spatial-coordinate-systems)**、 floor 级别来源和可选空间边界表示用户的定义、 设置期间首次运行。</span><span class="sxs-lookup"><span data-stu-id="798cc-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="798cc-123">若要确保的 Unity 运行时带有 floor 级别其世界坐标系统，可以设置为跟踪空间类型 RoomScale 的 Unity 并确保集成功：</span><span class="sxs-lookup"><span data-stu-id="798cc-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

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
* <span data-ttu-id="798cc-124">如果 SetTrackingSpaceType 返回 true，Unity 已成功切换其世界坐标系统来跟踪[阶段参考框架](coordinate-systems.md#spatial-coordinate-systems)。</span><span class="sxs-lookup"><span data-stu-id="798cc-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="798cc-125">如果 SetTrackingSpaceType 返回 false，Unity 不能切换到阶段参考框架，有可能，因为用户尚未设置甚至占地在其环境中。</span><span class="sxs-lookup"><span data-stu-id="798cc-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="798cc-126">这并不常见，但如果在不同的房间内设置阶段，设备已移至当前的房间，而无需设置新的阶段的用户则可能发生。</span><span class="sxs-lookup"><span data-stu-id="798cc-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="798cc-127">一旦您的应用程序已成功设置跟踪空间类型，内容在 y 轴上放置 RoomScale = 的 0 平面将显示在地板。</span><span class="sxs-lookup"><span data-stu-id="798cc-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="798cc-128">（0，0，0） 处的原点将在其中用户花了安装过程中的空间，-z 表示的向前他们在安装过程中面临着的车间的具体位置。</span><span class="sxs-lookup"><span data-stu-id="798cc-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="798cc-129">\**命名空间：\*\*\*UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="798cc-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="798cc-130">\**类型：\*\*\*边界*</span><span class="sxs-lookup"><span data-stu-id="798cc-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="798cc-131">在脚本代码中，随后可以调用你的 TryGetGeometry 方法是 UnityEngine.Experimental.XR.Boundary 类型获取边界多边形指定 TrackedArea 边界类型。</span><span class="sxs-lookup"><span data-stu-id="798cc-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="798cc-132">如果用户定义的边界 （重新获取顶点的列表），您知道安全地交付**聊天室规模体验**给用户，他们可以在其中引导在场景周围创建。</span><span class="sxs-lookup"><span data-stu-id="798cc-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="798cc-133">请注意，当用户接近其，系统会自动呈现边界。</span><span class="sxs-lookup"><span data-stu-id="798cc-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="798cc-134">您的应用程序不需要使用此多边形呈现自身的边界。</span><span class="sxs-lookup"><span data-stu-id="798cc-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="798cc-135">但是，您可以选择布局使用此边界的多边形、 为确保用户能够以物理方式访问这些对象，而 teleporting 应用场景对象：</span><span class="sxs-lookup"><span data-stu-id="798cc-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="798cc-136">构建全球规模体验</span><span class="sxs-lookup"><span data-stu-id="798cc-136">Building a world-scale experience</span></span>

<span data-ttu-id="798cc-137">\**命名空间：\*\*\*UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="798cc-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="798cc-138">\**类型：\*\*\*WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="798cc-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="798cc-139">若为 true**世界级体验**上允许用户浏览超出 5 米的 HoloLens，你将需要超出所使用的空间缩放体验的新技术。</span><span class="sxs-lookup"><span data-stu-id="798cc-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="798cc-140">将使用的一个关键技术是创建[空间的定位点](coordinate-systems.md#spatial-anchors)锁定的精确就地真实的场景中，而不考虑用户具有漫游延伸的范围，全息群集，然后[更高版本中再次查找这些全息会话](coordinate-systems.md#spatial-anchor-persistence)。</span><span class="sxs-lookup"><span data-stu-id="798cc-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="798cc-141">在 Unity 中，创建空间的定位点通过添加**WorldAnchor** Unity 组件给一个 gameobject 对象。</span><span class="sxs-lookup"><span data-stu-id="798cc-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="798cc-142">添加世界定位点</span><span class="sxs-lookup"><span data-stu-id="798cc-142">Adding a World Anchor</span></span>

<span data-ttu-id="798cc-143">若要添加世界定位点，请调用 AddComponent<WorldAnchor>你想要在现实生活中的定位点将转换到游戏对象上的 （)。</span><span class="sxs-lookup"><span data-stu-id="798cc-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="798cc-144">就这么简单！</span><span class="sxs-lookup"><span data-stu-id="798cc-144">That's it!</span></span> <span data-ttu-id="798cc-145">此游戏对象现在将定位到其当前物理世界中的位置-可能会看到段时间，以确保该物理的对齐方式略有调整其 Unity 世界坐标。</span><span class="sxs-lookup"><span data-stu-id="798cc-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="798cc-146">使用[持久性](persistence-in-unity.md)若要查找此锚定位置再次在将来的应用程序会话中。</span><span class="sxs-lookup"><span data-stu-id="798cc-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="798cc-147">删除世界定位点</span><span class="sxs-lookup"><span data-stu-id="798cc-147">Removing a World Anchor</span></span>

<span data-ttu-id="798cc-148">如果你不再想 GameObject 锁定到物理世界位置，并且不想将其移动此帧，则可以对全球定位点组件仅调用销毁。</span><span class="sxs-lookup"><span data-stu-id="798cc-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="798cc-149">如果你想要移动此帧的 GameObject，你需要改为调用 DestroyImmediate。</span><span class="sxs-lookup"><span data-stu-id="798cc-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="798cc-150">移动一个世界锚定的 GameObject</span><span class="sxs-lookup"><span data-stu-id="798cc-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="798cc-151">全球定位点在其上时，不能移动 GameObject 的。</span><span class="sxs-lookup"><span data-stu-id="798cc-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="798cc-152">如果您需要移动此帧的 GameObject，您需要：</span><span class="sxs-lookup"><span data-stu-id="798cc-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="798cc-153">DestroyImmediate 世界定位点组件</span><span class="sxs-lookup"><span data-stu-id="798cc-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="798cc-154">移动的 GameObject</span><span class="sxs-lookup"><span data-stu-id="798cc-154">Move the GameObject</span></span>
3. <span data-ttu-id="798cc-155">将新的全球定位点组件添加到的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="798cc-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="798cc-156">处理 Locatability 更改</span><span class="sxs-lookup"><span data-stu-id="798cc-156">Handling Locatability Changes</span></span>

<span data-ttu-id="798cc-157">WorldAnchor 可能不是可定位在某个点在现实环境中的时间。</span><span class="sxs-lookup"><span data-stu-id="798cc-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="798cc-158">如果发生这种情况，Unity 将不更新的转换的定位的对象。</span><span class="sxs-lookup"><span data-stu-id="798cc-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="798cc-159">这还可以更改运行应用时。</span><span class="sxs-lookup"><span data-stu-id="798cc-159">This also can change while an app is running.</span></span> <span data-ttu-id="798cc-160">未能在 locatability 中处理这些更改将导致要不显示在世界上正确的物理位置的对象。</span><span class="sxs-lookup"><span data-stu-id="798cc-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="798cc-161">要将通知 locatability 更改：</span><span class="sxs-lookup"><span data-stu-id="798cc-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="798cc-162">订阅 OnTrackingChanged 事件</span><span class="sxs-lookup"><span data-stu-id="798cc-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="798cc-163">处理事件</span><span class="sxs-lookup"><span data-stu-id="798cc-163">Handle the event</span></span>

<span data-ttu-id="798cc-164">**OnTrackingChanged**基础空间定位点之间的不是可定位与可定位状态发生更改时，将调用事件。</span><span class="sxs-lookup"><span data-stu-id="798cc-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="798cc-165">然后处理该事件：</span><span class="sxs-lookup"><span data-stu-id="798cc-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="798cc-166">有时定位点位于立即情况。</span><span class="sxs-lookup"><span data-stu-id="798cc-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="798cc-167">在这种情况下，定位点此 isLocated 属性将设置为 true 时 AddComponent<WorldAnchor>（） 返回。</span><span class="sxs-lookup"><span data-stu-id="798cc-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="798cc-168">因此，不会触发 OnTrackingChanged 事件。</span><span class="sxs-lookup"><span data-stu-id="798cc-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="798cc-169">清理模式是在附加定位点之后调用具有初始 IsLocated 状态您 OnTrackingChanged 的处理程序。</span><span class="sxs-lookup"><span data-stu-id="798cc-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="798cc-170">跨设备共享的定位点</span><span class="sxs-lookup"><span data-stu-id="798cc-170">Sharing anchors across devices</span></span>

<span data-ttu-id="798cc-171">可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>从您的应用程序然后可以跨多个 HoloLens、 iOS 和 Android 设备找到本地 WorldAnchor 创建持久的云定位点。</span><span class="sxs-lookup"><span data-stu-id="798cc-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="798cc-172">通过在多个设备之间共享公共空间定位点，每个用户可以看到呈现相对于同一物理位置中的锚点的内容。</span><span class="sxs-lookup"><span data-stu-id="798cc-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="798cc-173">这样实时共享体验。</span><span class="sxs-lookup"><span data-stu-id="798cc-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="798cc-174">若要开始构建在 Unity 中的共享的体验，请尝试出 5 分钟<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">快速入门 Azure 空间的定位点 Unity</a>。</span><span class="sxs-lookup"><span data-stu-id="798cc-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="798cc-175">你可以在 Azure 空间的定位点与您使用启动并运行，然后<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">创建并在 Unity 中定位的定位点</a>。</span><span class="sxs-lookup"><span data-stu-id="798cc-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="798cc-176">请参阅</span><span class="sxs-lookup"><span data-stu-id="798cc-176">See Also</span></span>
* [<span data-ttu-id="798cc-177">体验刻度</span><span class="sxs-lookup"><span data-stu-id="798cc-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="798cc-178">空间阶段</span><span class="sxs-lookup"><span data-stu-id="798cc-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="798cc-179">跟踪 Unity 中丢失</span><span class="sxs-lookup"><span data-stu-id="798cc-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="798cc-180">空间的定位点</span><span class="sxs-lookup"><span data-stu-id="798cc-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="798cc-181">在 Unity 中的暂留</span><span class="sxs-lookup"><span data-stu-id="798cc-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="798cc-182">在 Unity 中的共享的体验</span><span class="sxs-lookup"><span data-stu-id="798cc-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="798cc-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a></span><span class="sxs-lookup"><span data-stu-id="798cc-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="798cc-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空间的定位点适用于 Unity SDK</a></span><span class="sxs-lookup"><span data-stu-id="798cc-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>