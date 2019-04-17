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
# <a name="gaze-in-unity"></a><span data-ttu-id="1e9e4-104">在 Unity 中展示</span><span class="sxs-lookup"><span data-stu-id="1e9e4-104">Gaze in Unity</span></span>

<span data-ttu-id="1e9e4-105">[注视](gaze.md)是用户以确定了主要途径[全息](hologram.md)您的应用程序中创建[混合现实](mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [mixed reality](mixed-reality.md).</span></span>

## <a name="implementing-gaze"></a><span data-ttu-id="1e9e4-106">实现的视线移动</span><span class="sxs-lookup"><span data-stu-id="1e9e4-106">Implementing Gaze</span></span>

<span data-ttu-id="1e9e4-107">从概念上讲，[注视](gaze.md)实现通过投影从用户的头部向前面向并确定它们耳机所在 ray 的射线与有冲突。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="1e9e4-108">在 Unity 中，用户的头位置和方向公开通过 Unity Main[照相机](camera-in-unity.md)，具体而言[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html)并[UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="1e9e4-109">调用[Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html)会导致[RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html)结构，其中包含有关包括发生冲突的三维点碰撞效果和其他 GameObject 的视线移动 ray 信息使用发生碰撞。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-gaze"></a><span data-ttu-id="1e9e4-110">例如：实现的视线移动</span><span class="sxs-lookup"><span data-stu-id="1e9e4-110">Example: Implement Gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="1e9e4-111">最佳方案</span><span class="sxs-lookup"><span data-stu-id="1e9e4-111">Best Practices</span></span>

<span data-ttu-id="1e9e4-112">尽管上面的示例演示了如何在更新循环中，若要查找的视线移动目标单一 raycast，建议执行此操作管理而不是执行此操作可能会对感兴趣正在 gazed 处的对象的任何对象中的视线移动单个对象中。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="1e9e4-113">这允许您通过执行每个帧的只是一个提供注视 raycast 保存处理的应用程序。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="1e9e4-114">可视化的视线移动</span><span class="sxs-lookup"><span data-stu-id="1e9e4-114">Visualizing Gaze</span></span>

<span data-ttu-id="1e9e4-115">就像在桌面上使用其中的鼠标指针来面向和交互使用内容，则应实现[游标](cursors.md)，它表示用户的视线移动。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="1e9e4-116">这在如何为用户增添了信心地与之交互。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit"></a><span data-ttu-id="1e9e4-117">对此混合的现实工具包</span><span class="sxs-lookup"><span data-stu-id="1e9e4-117">Gaze in Mixed Reality Toolkit</span></span>
<span data-ttu-id="1e9e4-118">当您导入[MRTK 发布 Unity 包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)或从克隆项目[GitHub 存储库](https://github.com/Microsoft/MixedRealityToolkit-Unity)，要在 Unity 中查找新菜单混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-118">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="1e9e4-119">在配置菜单中，你会看到菜单应用混合现实场景设置。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-119">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="1e9e4-120">当您单击它时，它默认照相机中删除，并添加基础组件- [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)， [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab)，并[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-120">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="1e9e4-121">![MRTK 场景设置菜单](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="1e9e4-121">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="1e9e4-122">*MRTK 场景设置菜单*</span><span class="sxs-lookup"><span data-stu-id="1e9e4-122">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="1e9e4-123">![自动场景中 MRTK 的安装程序](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="1e9e4-123">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="1e9e4-124">*自动场景中 MRTK 的安装程序*</span><span class="sxs-lookup"><span data-stu-id="1e9e4-124">*Automatic scene setup in MRTK*</span></span>

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a><span data-ttu-id="1e9e4-125">注视混合现实工具包中的相关的脚本</span><span class="sxs-lookup"><span data-stu-id="1e9e4-125">Gaze related scripts in Mixed Reality Toolkit</span></span>
<span data-ttu-id="1e9e4-126">混合现实工具包包括 InputManager prefab [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs)并[注视稳定器](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs)。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-126">Mixed Reality Toolkit's InputManager prefab includes [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) and [Gaze Stabilizer](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span></span> <span data-ttu-id="1e9e4-127">下[SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs)，可以分配自定义光标。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-127">Under [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), you can assign your custom Cursor.</span></span> <span data-ttu-id="1e9e4-128">默认情况下，经过动画处理[DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)分配。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-128">In default, animated [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) is assigned.</span></span>

<span data-ttu-id="1e9e4-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)并[CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor)说明如何可视化你的视线移动使用游标。</span><span class="sxs-lookup"><span data-stu-id="1e9e4-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) and [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) shows you how to visualize your Gaze using Cursors.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e9e4-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="1e9e4-130">See also</span></span>
* [<span data-ttu-id="1e9e4-131">摄像头</span><span class="sxs-lookup"><span data-stu-id="1e9e4-131">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="1e9e4-132">Gaze</span><span class="sxs-lookup"><span data-stu-id="1e9e4-132">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="1e9e4-133">游标</span><span class="sxs-lookup"><span data-stu-id="1e9e4-133">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1e9e4-134">目标的视线移动</span><span class="sxs-lookup"><span data-stu-id="1e9e4-134">Gaze targeting</span></span>](gaze-targeting.md)
