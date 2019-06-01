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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="4761e-104">在 Unity 中的头视线移动</span><span class="sxs-lookup"><span data-stu-id="4761e-104">Head gaze in Unity</span></span>

<span data-ttu-id="4761e-105">[注视](gaze.md)是用户以确定了主要途径[全息](hologram.md)您的应用程序中创建[混合现实](mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="4761e-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="4761e-106">实现头的视线移动</span><span class="sxs-lookup"><span data-stu-id="4761e-106">Implementing head gaze</span></span>

<span data-ttu-id="4761e-107">从概念上讲，[注视](gaze.md)实现通过投影从用户的头部向前面向并确定它们耳机所在 ray 的射线与有冲突。</span><span class="sxs-lookup"><span data-stu-id="4761e-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="4761e-108">在 Unity 中，用户的头位置和方向公开通过 Unity Main[照相机](camera-in-unity.md)，具体而言[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)并[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="4761e-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="4761e-109">调用[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)会导致[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)结构，其中包含有关包括发生冲突的三维点碰撞效果和其他 GameObject 的视线移动 ray 信息使用发生碰撞。</span><span class="sxs-lookup"><span data-stu-id="4761e-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="4761e-110">例如：实现头的视线移动</span><span class="sxs-lookup"><span data-stu-id="4761e-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="4761e-111">最佳方案</span><span class="sxs-lookup"><span data-stu-id="4761e-111">Best Practices</span></span>

<span data-ttu-id="4761e-112">尽管上面的示例演示了如何在更新循环中，若要查找的视线移动目标单一 raycast，建议执行此操作管理而不是执行此操作可能会对感兴趣正在 gazed 处的对象的任何对象中的视线移动单个对象中。</span><span class="sxs-lookup"><span data-stu-id="4761e-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="4761e-113">这允许您通过执行每个帧的只是一个提供注视 raycast 保存处理的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4761e-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="4761e-114">可视化的视线移动</span><span class="sxs-lookup"><span data-stu-id="4761e-114">Visualizing Gaze</span></span>

<span data-ttu-id="4761e-115">就像在桌面上使用其中的鼠标指针来面向和交互使用内容，则应实现[游标](cursors.md)，它表示用户的视线移动。</span><span class="sxs-lookup"><span data-stu-id="4761e-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="4761e-116">这在如何为用户增添了信心地与之交互。</span><span class="sxs-lookup"><span data-stu-id="4761e-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="4761e-117">对此混合现实 Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="4761e-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="4761e-118">您可以访问从注视[输入管理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)MRTK v2 中。</span><span class="sxs-lookup"><span data-stu-id="4761e-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="4761e-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="4761e-119">See also</span></span>
* [<span data-ttu-id="4761e-120">摄像头</span><span class="sxs-lookup"><span data-stu-id="4761e-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="4761e-121">注视输入</span><span class="sxs-lookup"><span data-stu-id="4761e-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="4761e-122">光标</span><span class="sxs-lookup"><span data-stu-id="4761e-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="4761e-123">设定凝视目标</span><span class="sxs-lookup"><span data-stu-id="4761e-123">Gaze targeting</span></span>](gaze-targeting.md)
