---
title: 边界框和应用栏
description: 应用栏是一个对象级菜单，其中包含一系列按钮，它们显示在全息图边界的下边缘。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality，应用栏，边界框
ms.openlocfilehash: dab41207c2558fe8bb3fe07fca666cb2668f4e45
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723196"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="1bbf2-104">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="1bbf2-104">Bounding box and App bar</span></span>
<span data-ttu-id="1bbf2-105">![边界是在混合现实中用于对象操作的标准接口。](images/UX/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="1bbf2-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="1bbf2-106">什么是边界框？</span><span class="sxs-lookup"><span data-stu-id="1bbf2-106">What is the Bounding box?</span></span>

<span data-ttu-id="1bbf2-107">"边界" 是用于在混合现实中进行对象操作的标准接口。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="1bbf2-108">它向用户提供当前可调整对象的 affordance。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="1bbf2-109">在 HoloLens 2 上，边界框适用于直接操作，并响应用户的 finger's 邻近性。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="1bbf2-110">它显示了视觉反馈，可帮助用户感知与对象的距离。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="1bbf2-111">缩放对象</span><span class="sxs-lookup"><span data-stu-id="1bbf2-111">Scaling an object</span></span><br>
        <span data-ttu-id="1bbf2-112">边界框的角告诉用户该对象可以缩放。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="1bbf2-113">句柄遵循用于调整刻度的广泛理解的模式。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="1bbf2-114">此视觉对象 affordance 向用户显示对象的总区域–即使它在调整模式之外不可见。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="1bbf2-115">这一点特别重要，因为如果不存在，则与另一个对象或表面对齐的对象可能看起来好像不应存在的空间。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="1bbf2-116">*视频循环：通过边界框缩放对象*</span><span class="sxs-lookup"><span data-stu-id="1bbf2-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="1bbf2-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="1bbf2-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="1bbf2-118">![通过边界框缩放对象](images/HoloLens2_BoundingBox.gif) 的 HoloLens 观点</span><span class="sxs-lookup"><span data-stu-id="1bbf2-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="1bbf2-119">旋转对象</span><span class="sxs-lookup"><span data-stu-id="1bbf2-119">Rotating an object</span></span><br>
        <span data-ttu-id="1bbf2-120">边界框边缘的垂直矩形实用是旋转指示器。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="1bbf2-121">这样，用户就可以更好地调整其放置的全息影像。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="1bbf2-122">它们不仅可以进行调整和缩放，还可以进行旋转。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="1bbf2-123">*视频循环：通过边界框旋转对象*</span><span class="sxs-lookup"><span data-stu-id="1bbf2-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="1bbf2-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="1bbf2-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="1bbf2-125">![通过边界框旋转对象](images/HoloLens2_BoundingBox_Rotate.gif) 的 HoloLens 观点</span><span class="sxs-lookup"><span data-stu-id="1bbf2-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="1bbf2-126">HoloLens 2 上的现有视觉对象反馈</span><span class="sxs-lookup"><span data-stu-id="1bbf2-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="1bbf2-127">在 HoloLens 2 上，还有其他视觉提示，可帮助用户了解深度。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="1bbf2-128">当手指更接近对象时，其手指附近的圆圈会显示并缩小。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="1bbf2-129">当达到按下状态时，环最终汇聚为一个点。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="1bbf2-130">此视觉对象 affordance 可帮助用户了解其在对象中的距离。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="1bbf2-131">*视频循环：基于与边界框的邻近的视觉反馈示例*</span><span class="sxs-lookup"><span data-stu-id="1bbf2-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="1bbf2-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="1bbf2-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="1bbf2-133">![视觉对象反馈](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="1bbf2-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="1bbf2-134">**对于 Unity 应用开发，请参阅[混合现实工具包中的边界框-Unity。](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="1bbf2-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="1bbf2-135">什么是应用栏？</span><span class="sxs-lookup"><span data-stu-id="1bbf2-135">What is the App bar?</span></span>

<span data-ttu-id="1bbf2-136">应用栏是一个对象级菜单，其中包含一系列按钮，它们显示在全息图边界的下边缘。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="1bbf2-137">此模式通常用于使用户能够删除和调整全息影像。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="1bbf2-138">应用栏的设计主要是在用户的环境中管理已放置对象的方式。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="1bbf2-139">与边界框结合使用，用户可以完全控制对象在混合现实中的位置和方式。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="1bbf2-140">应用栏追随用户</span><span class="sxs-lookup"><span data-stu-id="1bbf2-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="1bbf2-141">由于此模式与世界锁定的对象一起使用，因此当用户在对象周围移动时，应用栏将始终显示在最靠近用户的对象端。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="1bbf2-142">尽管这不是 billboarding 的，但它实际上实现了相同的结果;防止用户遮蔽或阻止在其环境中的其他位置可用的功能。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="1bbf2-143">*视频循环：浏览全息图，应用栏跟随*</span><span class="sxs-lookup"><span data-stu-id="1bbf2-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="1bbf2-144">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="1bbf2-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="1bbf2-145">![走出全息影像。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-145">![Walking around a hologram.</span></span> <span data-ttu-id="1bbf2-146">应用栏如下所示。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="1bbf2-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="1bbf2-147">Unity 的 MRTK （混合现实工具包）中的边界框</span><span class="sxs-lookup"><span data-stu-id="1bbf2-147">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="1bbf2-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 为边界框和应用栏提供脚本和 prototyping。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="1bbf2-149">只需将 BoundingBox.cs 脚本分配到任何对象即可添加边界框。</span><span class="sxs-lookup"><span data-stu-id="1bbf2-149">You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="1bbf2-150">MRTK-边界框</span><span class="sxs-lookup"><span data-stu-id="1bbf2-150">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="1bbf2-151">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bbf2-151">See also</span></span>

* [<span data-ttu-id="1bbf2-152">光标</span><span class="sxs-lookup"><span data-stu-id="1bbf2-152">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1bbf2-153">手部射线</span><span class="sxs-lookup"><span data-stu-id="1bbf2-153">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="1bbf2-154">Button</span><span class="sxs-lookup"><span data-stu-id="1bbf2-154">Button</span></span>](button.md)
* [<span data-ttu-id="1bbf2-155">可交互对象</span><span class="sxs-lookup"><span data-stu-id="1bbf2-155">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1bbf2-156">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="1bbf2-156">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="1bbf2-157">操作</span><span class="sxs-lookup"><span data-stu-id="1bbf2-157">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1bbf2-158">手动菜单</span><span class="sxs-lookup"><span data-stu-id="1bbf2-158">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="1bbf2-159">追踪菜单</span><span class="sxs-lookup"><span data-stu-id="1bbf2-159">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="1bbf2-160">对象集合</span><span class="sxs-lookup"><span data-stu-id="1bbf2-160">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="1bbf2-161">语音命令</span><span class="sxs-lookup"><span data-stu-id="1bbf2-161">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="1bbf2-162">键盘</span><span class="sxs-lookup"><span data-stu-id="1bbf2-162">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="1bbf2-163">工具提示</span><span class="sxs-lookup"><span data-stu-id="1bbf2-163">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="1bbf2-164">平板</span><span class="sxs-lookup"><span data-stu-id="1bbf2-164">Slate</span></span>](slate.md)
* [<span data-ttu-id="1bbf2-165">滑块</span><span class="sxs-lookup"><span data-stu-id="1bbf2-165">Slider</span></span>](slider.md)
* [<span data-ttu-id="1bbf2-166">着色器</span><span class="sxs-lookup"><span data-stu-id="1bbf2-166">Shader</span></span>](shader.md)
* [<span data-ttu-id="1bbf2-167">公告和尾随</span><span class="sxs-lookup"><span data-stu-id="1bbf2-167">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="1bbf2-168">显示进度</span><span class="sxs-lookup"><span data-stu-id="1bbf2-168">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="1bbf2-169">表面磁吸</span><span class="sxs-lookup"><span data-stu-id="1bbf2-169">Surface magnetism</span></span>](surface-magnetism.md)
