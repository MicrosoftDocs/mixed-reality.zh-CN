---
title: 凝视
description: 注视是第一种形式的输入, 是混合现实中的主要目标形式。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 混合现实, 注视, 交互, 设计
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414368"
---
# <a name="gaze"></a><span data-ttu-id="7ac68-104">凝视</span><span class="sxs-lookup"><span data-stu-id="7ac68-104">Gaze</span></span>

<span data-ttu-id="7ac68-105">**注视**是第一种形式的输入, 是混合现实中的主要目标形式。</span><span class="sxs-lookup"><span data-stu-id="7ac68-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="7ac68-106">注视告诉你用户在世界中的位置, 并允许你确定其意图。</span><span class="sxs-lookup"><span data-stu-id="7ac68-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="7ac68-107">在现实生活中, 您通常会看到一个要与之交互的对象。</span><span class="sxs-lookup"><span data-stu-id="7ac68-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="7ac68-108">这与注视的情况相同。</span><span class="sxs-lookup"><span data-stu-id="7ac68-108">This is the same with gaze.</span></span>

<span data-ttu-id="7ac68-109">混合现实耳机使用用户头部的位置和方向来确定其头盔向量。</span><span class="sxs-lookup"><span data-stu-id="7ac68-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="7ac68-110">可以直接将此向量视为激光指针, 直接从用户的眼睛之间直接。</span><span class="sxs-lookup"><span data-stu-id="7ac68-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="7ac68-111">当用户寻找房间时, 您的应用程序可以与这一 ray 相交, 这两种情况都具有自己的全息影像和[空间映射](spatial-mapping.md)网格, 以确定用户可能正在查看的虚拟或现实对象。</span><span class="sxs-lookup"><span data-stu-id="7ac68-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="7ac68-112">在 HoloLens 2 上, 可以通过用户的 "注视" 眼睛、"眼睛" 或 "近" 或 "远" 交互来确定交互的目标。</span><span class="sxs-lookup"><span data-stu-id="7ac68-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="7ac68-113">在 HoloLens (第一代) 上, 交互通常应从用户的打印头获取目标, 而不是尝试直接在该位置上呈现或交互。</span><span class="sxs-lookup"><span data-stu-id="7ac68-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="7ac68-114">开始交互后, 可以使用该手型的相对运动来控制[该笔势](gestures.md), 如[操作或导航](gestures.md#composite-gestures)手势。</span><span class="sxs-lookup"><span data-stu-id="7ac68-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="7ac68-115">使用沉浸式耳机, 您可以使用 "注视" 或 "支持支持" 的[运动控制器](motion-controllers.md)进行定位。</span><span class="sxs-lookup"><span data-stu-id="7ac68-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="7ac68-116">设备支持</span><span class="sxs-lookup"><span data-stu-id="7ac68-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7ac68-117"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="7ac68-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="7ac68-118"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="7ac68-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7ac68-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7ac68-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7ac68-120"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="7ac68-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7ac68-121">打印头</span><span class="sxs-lookup"><span data-stu-id="7ac68-121">Head gaze</span></span></td>
        <td><span data-ttu-id="7ac68-122">✔️</span><span class="sxs-lookup"><span data-stu-id="7ac68-122">✔️</span></span></td>
        <td><span data-ttu-id="7ac68-123">✔️</span><span class="sxs-lookup"><span data-stu-id="7ac68-123">✔️</span></span></td>
        <td><span data-ttu-id="7ac68-124">✔️</span><span class="sxs-lookup"><span data-stu-id="7ac68-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7ac68-125">眼睛</span><span class="sxs-lookup"><span data-stu-id="7ac68-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="7ac68-126">❌</span><span class="sxs-lookup"><span data-stu-id="7ac68-126">❌</span></span></td>
        <td><span data-ttu-id="7ac68-127">✔️</span><span class="sxs-lookup"><span data-stu-id="7ac68-127">✔️</span></span></td>
        <td><span data-ttu-id="7ac68-128">❌</span><span class="sxs-lookup"><span data-stu-id="7ac68-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="7ac68-129">即将[推出](index.md#news-and-notes)特定于 HoloLens 2 的更多指导。</span><span class="sxs-lookup"><span data-stu-id="7ac68-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="7ac68-130">用注视</span><span class="sxs-lookup"><span data-stu-id="7ac68-130">Uses of gaze</span></span>

<span data-ttu-id="7ac68-131">作为混合现实开发人员, 您可以很好地使用打印头或眼睛眼睛:</span><span class="sxs-lookup"><span data-stu-id="7ac68-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="7ac68-132">您的应用程序可以在场景中与全息影像交叉, 以确定用户关注的位置。</span><span class="sxs-lookup"><span data-stu-id="7ac68-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="7ac68-133">您的应用程序可以基于用户的注视定位手势和控制器按下, 使用户能够选择、激活、抓取、滚动或以其他方式与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="7ac68-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="7ac68-134">您的应用程序可让用户在实际的表面上放置全息影像, 方法是将其表面与空间映射网格进行交叉处理。</span><span class="sxs-lookup"><span data-stu-id="7ac68-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="7ac68-135">您的应用程序可以知道用户*不*在查找重要对象的方向时, 这可能会导致您的应用程序将视觉和音频提示转换为该对象。</span><span class="sxs-lookup"><span data-stu-id="7ac68-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="7ac68-136">Cursor</span><span class="sxs-lookup"><span data-stu-id="7ac68-136">Cursor</span></span>

<span data-ttu-id="7ac68-137">对于 "注视", 大多数应用程序都应使用[游标](cursors.md)(或其他听觉/视觉指示) 来让用户信任他们要与之交互的内容。</span><span class="sxs-lookup"><span data-stu-id="7ac68-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="7ac68-138">通常将此光标置于世界上, 其中其打印头看起来先与一个对象 (可能是全息图或真实表面) 相交。</span><span class="sxs-lookup"><span data-stu-id="7ac68-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="7ac68-139">![用于显示注视的视觉对象示例](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="7ac68-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="7ac68-140">*用于显示注视的视觉对象示例*</span><span class="sxs-lookup"><span data-stu-id="7ac68-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="7ac68-141">对于眼睛, 我们通常建议*不要*显示游标, 因为这可能会使用户迅速变得杂乱。</span><span class="sxs-lookup"><span data-stu-id="7ac68-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="7ac68-142">相反, 突出强调视觉对象目标或使用非常模糊的光标, 以使用户与之交互的对象更有把握。</span><span class="sxs-lookup"><span data-stu-id="7ac68-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="7ac68-143">有关详细信息, 请查看有关 HoloLens 2 上[基于目视的输入的设计指南](eye-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="7ac68-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="7ac68-144">向用户的注视提供操作</span><span class="sxs-lookup"><span data-stu-id="7ac68-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="7ac68-145">一旦用户使用了其注视来确定全息图或现实世界对象的目标, 下一步就是对该对象执行操作。</span><span class="sxs-lookup"><span data-stu-id="7ac68-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="7ac68-146">用户采取行动的主要方式是通过[手势](gestures.md)、[运动控制器](motion-controllers.md)和[语音](voice-input.md)。</span><span class="sxs-lookup"><span data-stu-id="7ac68-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ac68-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="7ac68-147">See also</span></span>
* [<span data-ttu-id="7ac68-148">MR 输入 210：打印头</span><span class="sxs-lookup"><span data-stu-id="7ac68-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="7ac68-149">DirectX 中的头部和眼部凝视</span><span class="sxs-lookup"><span data-stu-id="7ac68-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="7ac68-150">Unity 中的头盔</span><span class="sxs-lookup"><span data-stu-id="7ac68-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="7ac68-151">目视-注视 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7ac68-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="7ac68-152">使用混合现实工具包的 Unity 中的眼睛</span><span class="sxs-lookup"><span data-stu-id="7ac68-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
