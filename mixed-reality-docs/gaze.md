---
title: 凝视
description: 提供注视是第一种形式的输入，主窗体的目标中混合现实。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实、 提供注视、 交互，设计
ms.openlocfilehash: e0c1a925f6faeb37ec35e511cef36f9c06672c8a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829740"
---
# <a name="gaze"></a><span data-ttu-id="2ed17-104">凝视</span><span class="sxs-lookup"><span data-stu-id="2ed17-104">Gaze</span></span>

<span data-ttu-id="2ed17-105">**注视**是第一种形式的输入，主窗体的目标中混合现实。</span><span class="sxs-lookup"><span data-stu-id="2ed17-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="2ed17-106">提供注视告诉您其中用户在世界中查找，并可以确定其意图。</span><span class="sxs-lookup"><span data-stu-id="2ed17-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="2ed17-107">在现实生活中，您将通常看到在你想要与之交互的对象。</span><span class="sxs-lookup"><span data-stu-id="2ed17-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="2ed17-108">这也同样适用于的视线移动。</span><span class="sxs-lookup"><span data-stu-id="2ed17-108">This is the same with gaze.</span></span>

<span data-ttu-id="2ed17-109">混合的现实耳机使用位置和方向的用户的头来确定其头的视线移动矢量。</span><span class="sxs-lookup"><span data-stu-id="2ed17-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="2ed17-110">您可以作为激光指针直接向前从用户的眼球之间直接将此向量。</span><span class="sxs-lookup"><span data-stu-id="2ed17-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="2ed17-111">如用户看起来的房间内，你的应用程序如何相互交叉此 ray 使用其自己全息和与[空间映射](spatial-mapping.md)网格来确定您的用户可以查看哪些虚拟还是实际对象。</span><span class="sxs-lookup"><span data-stu-id="2ed17-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="2ed17-112">HoloLens 2 上的交互可通过用户的头视线移动，关注的视线移动定位或通过附近或远分发的交互。</span><span class="sxs-lookup"><span data-stu-id="2ed17-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="2ed17-113">HoloLens 上 （第 1 代），交互应通常是其目标从用户的头的视线移动，而不是非试着来呈现或直接在现有的位置进行交互。</span><span class="sxs-lookup"><span data-stu-id="2ed17-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="2ed17-114">一旦启动交互，相对动作的手可能用于控制[手势](gestures.md)，如同[操作或导航](gestures.md#composite-gestures)手势。</span><span class="sxs-lookup"><span data-stu-id="2ed17-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="2ed17-115">可以使用沉浸式耳机，面向使用任一头的视线移动或指向能够[动作控制器](motion-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="2ed17-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="2ed17-116">设备支持</span><span class="sxs-lookup"><span data-stu-id="2ed17-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2ed17-117"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="2ed17-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="2ed17-118"><a href="hololens-hardware-details.md"><strong>HoloLens （第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="2ed17-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2ed17-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2ed17-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2ed17-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></span><span class="sxs-lookup"><span data-stu-id="2ed17-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2ed17-121">Head 的视线移动</span><span class="sxs-lookup"><span data-stu-id="2ed17-121">Head gaze</span></span></td>
        <td><span data-ttu-id="2ed17-122">✔️</span><span class="sxs-lookup"><span data-stu-id="2ed17-122">✔️</span></span></td>
        <td><span data-ttu-id="2ed17-123">✔️</span><span class="sxs-lookup"><span data-stu-id="2ed17-123">✔️</span></span></td>
        <td><span data-ttu-id="2ed17-124">✔️</span><span class="sxs-lookup"><span data-stu-id="2ed17-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2ed17-125">关注的视线移动</span><span class="sxs-lookup"><span data-stu-id="2ed17-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="2ed17-126">❌</span><span class="sxs-lookup"><span data-stu-id="2ed17-126">❌</span></span></td>
        <td><span data-ttu-id="2ed17-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2ed17-127">✔️</span></span></td>
        <td><span data-ttu-id="2ed17-128">❌</span><span class="sxs-lookup"><span data-stu-id="2ed17-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="2ed17-129">特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。</span><span class="sxs-lookup"><span data-stu-id="2ed17-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="2ed17-130">使用的视线移动</span><span class="sxs-lookup"><span data-stu-id="2ed17-130">Uses of gaze</span></span>

<span data-ttu-id="2ed17-131">混合的现实开发人员，您可以执行许多操作头或关注的视线移动：</span><span class="sxs-lookup"><span data-stu-id="2ed17-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="2ed17-132">您的应用程序可以相交与您的场景中全息的视线移动以确定用户的注意力的位置。</span><span class="sxs-lookup"><span data-stu-id="2ed17-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="2ed17-133">你的应用可面向手势和控制器按下按钮可以基于用户的视线移动，让用户选择、 激活、 获取、 向下滚动，或与其全息否则交互。</span><span class="sxs-lookup"><span data-stu-id="2ed17-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="2ed17-134">您的应用程序可以让用户中放置全息实际的应用层与空间映射网格其提供注视射线相交。</span><span class="sxs-lookup"><span data-stu-id="2ed17-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="2ed17-135">您的应用程序可以知道用户何时*不*查找重要的对象，这可能会导致您的应用程序提供视频和音频提示，用于启用向该对象的方向。</span><span class="sxs-lookup"><span data-stu-id="2ed17-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="2ed17-136">Cursor</span><span class="sxs-lookup"><span data-stu-id="2ed17-136">Cursor</span></span>

<span data-ttu-id="2ed17-137">对于头的视线移动，大多数应用程序应使用[游标](cursors.md)（或其他听觉/visual 表明） 若要在如何使用户确信它们要与之交互。</span><span class="sxs-lookup"><span data-stu-id="2ed17-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="2ed17-138">也通常将此游标放置在世界上其头的视线移动 ray 首先相交一个对象，它可能是一张全息图或实际的图面。</span><span class="sxs-lookup"><span data-stu-id="2ed17-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="2ed17-139">![若要显示的视线移动示例 visual 游标](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="2ed17-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="2ed17-140">*若要显示的视线移动示例 visual 游标*</span><span class="sxs-lookup"><span data-stu-id="2ed17-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="2ed17-141">对于关注的视线移动，我们通常建议*不*显示游标，这很快就明显，令人讨厌的用户。</span><span class="sxs-lookup"><span data-stu-id="2ed17-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="2ed17-142">而是略有突出显示视觉目标或非常不清晰的关注游标用于提供有关用户是要与之交互的置信度。</span><span class="sxs-lookup"><span data-stu-id="2ed17-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="2ed17-143">有关详细信息，请查看我们[关注基于输入的设计指南](eye-tracking.md)HoloLens 2 上。</span><span class="sxs-lookup"><span data-stu-id="2ed17-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="2ed17-144">向用户的视线移动操作</span><span class="sxs-lookup"><span data-stu-id="2ed17-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="2ed17-145">用户具有目标全息图或使用其的视线移动的实际对象，其下一步是对该对象执行操作。</span><span class="sxs-lookup"><span data-stu-id="2ed17-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="2ed17-146">用户可以执行操作的主要方法是： 通过[手势](gestures.md)，[动作控制器](motion-controllers.md)并[语音](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="2ed17-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ed17-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="2ed17-147">See also</span></span>
* [<span data-ttu-id="2ed17-148">MR 输入 210：Head 的视线移动</span><span class="sxs-lookup"><span data-stu-id="2ed17-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="2ed17-149">DirectX 中的头部和眼部凝视</span><span class="sxs-lookup"><span data-stu-id="2ed17-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="2ed17-150">在 Unity 中的头视线移动</span><span class="sxs-lookup"><span data-stu-id="2ed17-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="2ed17-151">眼睛追踪 HoloLens 2 上</span><span class="sxs-lookup"><span data-stu-id="2ed17-151">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="2ed17-152">在 Unity 中使用混合现实工具包的眼睛视线移动</span><span class="sxs-lookup"><span data-stu-id="2ed17-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
