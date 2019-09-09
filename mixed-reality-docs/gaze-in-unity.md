---
title: 注视 Unity
description: 注视是用户在混合现实中以应用程序创建的方式为目标的主要方式。
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 眼睛、头盔、unity、全息图、混合现实
ms.openlocfilehash: 43e643bac00e3c889b14000331d2ed95014fdcc5
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122039"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="89132-104">头-注视 Unity</span><span class="sxs-lookup"><span data-stu-id="89132-104">Head-gaze in Unity</span></span>

<span data-ttu-id="89132-105">[注视](gaze.md)是用户在[混合现实](mixed-reality.md)中以应用程序[创建的方式](hologram.md)为目标的主要方式。</span><span class="sxs-lookup"><span data-stu-id="89132-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="89132-106">实现机头</span><span class="sxs-lookup"><span data-stu-id="89132-106">Implementing head-gaze</span></span>

<span data-ttu-id="89132-107">从概念上讲，[打印头](gaze.md)的实现方式是从用户的头投影一条射线，其中的耳机是正面朝上，并确定与该射线发生冲突的内容。</span><span class="sxs-lookup"><span data-stu-id="89132-107">Conceptually, [head-gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="89132-108">在 Unity 中，用户的头位置和方向通过 Unity 主[摄像机](camera-in-unity.md)公开，特别是[UnityEngine](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform](http://docs.unity3d.com/ScriptReference/Transform-forward.html)和[UnityEngine](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[转换。位置](http://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="89132-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="89132-109">如果调用[RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) ，则会生成一个[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)结构，其中包含有关冲突的信息，其中包括发生冲突的三维点，以及使用的另一 GameObject。</span><span class="sxs-lookup"><span data-stu-id="89132-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="89132-110">例如：实现机头</span><span class="sxs-lookup"><span data-stu-id="89132-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="89132-111">最佳实践</span><span class="sxs-lookup"><span data-stu-id="89132-111">Best practices</span></span>

<span data-ttu-id="89132-112">尽管上面的示例演示了如何在更新循环中执行单个 raycast 来查找用户头所在的目标，但建议在管理打印头的单个对象中执行此操作，而不是在可能对对象传递感兴趣的任何对象中执行此操作。t 正在 gazed。</span><span class="sxs-lookup"><span data-stu-id="89132-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="89132-113">这样，你的应用程序就可以通过只对每个帧执行一个 raycast 的操作来保存处理。</span><span class="sxs-lookup"><span data-stu-id="89132-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="89132-114">形象注视</span><span class="sxs-lookup"><span data-stu-id="89132-114">Visualizing head-gaze</span></span>

<span data-ttu-id="89132-115">就像在使用鼠标指针来定位内容并与内容交互的桌面上，你应该实现表示用户头看的[光标](cursors.md)。</span><span class="sxs-lookup"><span data-stu-id="89132-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="89132-116">这为用户提供了与交互相关的置信度。</span><span class="sxs-lookup"><span data-stu-id="89132-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="89132-117">标题-注视混合现实工具包 v2</span><span class="sxs-lookup"><span data-stu-id="89132-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="89132-118">可以从 MRTK v2 中的[输入管理器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)访问 head。</span><span class="sxs-lookup"><span data-stu-id="89132-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="89132-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="89132-119">See also</span></span>
* [<span data-ttu-id="89132-120">摄像头</span><span class="sxs-lookup"><span data-stu-id="89132-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="89132-121">光标</span><span class="sxs-lookup"><span data-stu-id="89132-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="89132-122">注视输入</span><span class="sxs-lookup"><span data-stu-id="89132-122">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="89132-123">设定凝视目标</span><span class="sxs-lookup"><span data-stu-id="89132-123">Gaze targeting</span></span>](gaze-targeting.md)
