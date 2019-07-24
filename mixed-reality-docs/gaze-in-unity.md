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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="d7f2c-104">Unity 中的头盔</span><span class="sxs-lookup"><span data-stu-id="d7f2c-104">Head gaze in Unity</span></span>

<span data-ttu-id="d7f2c-105">[注视](gaze.md)是用户在[混合现实](mixed-reality.md)中以应用程序[创建的方式](hologram.md)为目标的主要方式。</span><span class="sxs-lookup"><span data-stu-id="d7f2c-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="d7f2c-106">实现打印头</span><span class="sxs-lookup"><span data-stu-id="d7f2c-106">Implementing head gaze</span></span>

<span data-ttu-id="d7f2c-107">从概念上讲,[注视](gaze.md)的实现方式是: 从用户的头投影一条射线, 其中的耳机是正面朝上, 并确定与该射线发生冲突的情况。</span><span class="sxs-lookup"><span data-stu-id="d7f2c-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="d7f2c-108">在 Unity 中, 用户的头位置和方向通过 Unity 主[摄像机](camera-in-unity.md)公开, 特别是[UnityEngine](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform](http://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[转换。位置](http://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="d7f2c-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="d7f2c-109">如果调用[RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) , 则会生成一个[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)结构, 其中包含有关冲突的信息, 包括发生冲突的三维点, 以及使用 "注视" 光线与的另一个 GameObject。</span><span class="sxs-lookup"><span data-stu-id="d7f2c-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="d7f2c-110">例如：实现打印头</span><span class="sxs-lookup"><span data-stu-id="d7f2c-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="d7f2c-111">最佳方案</span><span class="sxs-lookup"><span data-stu-id="d7f2c-111">Best Practices</span></span>

<span data-ttu-id="d7f2c-112">尽管上面的示例演示了如何在更新循环中执行单个 raycast 来查找注视目标, 但建议在管理注视的单个对象中执行此操作, 而不是在可能对要在 gazed 的对象感兴趣的任何对象中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="d7f2c-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="d7f2c-113">这样, 你的应用程序就可以通过只对每个帧执行一个注视 raycast 来保存处理。</span><span class="sxs-lookup"><span data-stu-id="d7f2c-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="d7f2c-114">可视化注视</span><span class="sxs-lookup"><span data-stu-id="d7f2c-114">Visualizing Gaze</span></span>

<span data-ttu-id="d7f2c-115">就像在使用鼠标指针来定位内容并与内容交互的桌面上, 你应该实现表示用户注视的[光标](cursors.md)。</span><span class="sxs-lookup"><span data-stu-id="d7f2c-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="d7f2c-116">这为用户提供了与交互相关的置信度。</span><span class="sxs-lookup"><span data-stu-id="d7f2c-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="d7f2c-117">注视混合现实工具包 v2</span><span class="sxs-lookup"><span data-stu-id="d7f2c-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="d7f2c-118">可以从 MRTK v2 中的[输入管理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)访问注视。</span><span class="sxs-lookup"><span data-stu-id="d7f2c-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7f2c-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="d7f2c-119">See also</span></span>
* [<span data-ttu-id="d7f2c-120">摄像头</span><span class="sxs-lookup"><span data-stu-id="d7f2c-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="d7f2c-121">注视输入</span><span class="sxs-lookup"><span data-stu-id="d7f2c-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="d7f2c-122">光标</span><span class="sxs-lookup"><span data-stu-id="d7f2c-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d7f2c-123">设定凝视目标</span><span class="sxs-lookup"><span data-stu-id="d7f2c-123">Gaze targeting</span></span>](gaze-targeting.md)
