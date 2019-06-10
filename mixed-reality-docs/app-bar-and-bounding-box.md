---
title: 应用程序栏和边框
description: 应用程序栏是对象级菜单包含一系列显示一张全息图边界的下边缘的按钮。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality 应用栏，边界框
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813840"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="eee00-104">边界框和应用程序栏</span><span class="sxs-lookup"><span data-stu-id="eee00-104">Bounding box and App bar</span></span>
![边界是混合现实中的对象操作的标准接口。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="eee00-106">边界框是什么？</span><span class="sxs-lookup"><span data-stu-id="eee00-106">What is the Bounding box?</span></span>

<span data-ttu-id="eee00-107">边界是混合现实中的对象操作的标准接口。</span><span class="sxs-lookup"><span data-stu-id="eee00-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="eee00-108">它为用户提供功能的对象是当前可调整的可见性:。</span><span class="sxs-lookup"><span data-stu-id="eee00-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="eee00-109">角将告诉用户还可以缩放对象。</span><span class="sxs-lookup"><span data-stu-id="eee00-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="eee00-110">即使不可见的调整模式，这样 visual 一向用户显示对象 – 总的区域。</span><span class="sxs-lookup"><span data-stu-id="eee00-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="eee00-111">这一点尤其重要，因为如果存在不是，对象对齐到另一个对象或面似乎行为就如同时不应在那里它周围的空间。</span><span class="sxs-lookup"><span data-stu-id="eee00-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="eee00-112">HoloLens 2 上的边界框适用于直接手动操作和响应用户的手指的邻近性。</span><span class="sxs-lookup"><span data-stu-id="eee00-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="eee00-113">它显示了可视反馈以帮助用户感知从该对象的距离。</span><span class="sxs-lookup"><span data-stu-id="eee00-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="eee00-114">![HoloLens-的角度来看的缩放通过边界框的对象](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="eee00-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="eee00-115">*缩放通过边界框的对象*</span><span class="sxs-lookup"><span data-stu-id="eee00-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="eee00-116">中的边界框角的图柄按照调整规模的广为人知的模式。</span><span class="sxs-lookup"><span data-stu-id="eee00-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="eee00-117">![HoloLens-的角度来看旋转通过边界框的对象](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="eee00-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="eee00-118">*旋转对象通过边界框*</span><span class="sxs-lookup"><span data-stu-id="eee00-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="eee00-119">![在手动邻近的可视反馈](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="eee00-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="eee00-120">*邻近的可视反馈*</span><span class="sxs-lookup"><span data-stu-id="eee00-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="eee00-121">边界框的边缘上的垂直矩形等是旋转指示符。</span><span class="sxs-lookup"><span data-stu-id="eee00-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="eee00-122">此选项会使用户更多的精细调整能够对其置入全息。</span><span class="sxs-lookup"><span data-stu-id="eee00-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="eee00-123">不仅可以在调整和缩放，但现在还包括旋转。</span><span class="sxs-lookup"><span data-stu-id="eee00-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="eee00-124">Unity 应用程序开发，请参阅[边界框上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="eee00-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="eee00-125">什么是应用程序栏？</span><span class="sxs-lookup"><span data-stu-id="eee00-125">What is the App bar?</span></span>

<span data-ttu-id="eee00-126">应用程序栏是对象级菜单包含一系列显示一张全息图边界的下边缘的按钮。</span><span class="sxs-lookup"><span data-stu-id="eee00-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="eee00-127">此模式通常用于使用户能够删除和调整全息。</span><span class="sxs-lookup"><span data-stu-id="eee00-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="eee00-128">由于此模式用于访问对象，该对象周围移动用户而言是完全锁定状态，应用程序栏将始终显示在最靠近用户的选择对象端。</span><span class="sxs-lookup"><span data-stu-id="eee00-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="eee00-129">虽然这不公告板，它有效地实现相同的结果;阻止用户的位置以遮蔽或应可从其环境中的不同位置的块功能。</span><span class="sxs-lookup"><span data-stu-id="eee00-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="eee00-130">![移动办公了一张全息图。</span><span class="sxs-lookup"><span data-stu-id="eee00-130">![Walking around a hologram.</span></span> <span data-ttu-id="eee00-131">遵循应用程序栏。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="eee00-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="eee00-132">*移动办公了一张全息图，遵循应用程序栏*</span><span class="sxs-lookup"><span data-stu-id="eee00-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="eee00-133">应用栏旨在主要作为一种方法来管理用户的环境中放置的对象。</span><span class="sxs-lookup"><span data-stu-id="eee00-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="eee00-134">耦合在一起的边界框，用户可以完全控制在何处以及如何在混合现实方向，对象。</span><span class="sxs-lookup"><span data-stu-id="eee00-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="eee00-135">Unity 应用程序开发，请参阅[应用栏上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="eee00-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="eee00-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="eee00-136">See also</span></span>
* [<span data-ttu-id="eee00-137">可交互对象</span><span class="sxs-lookup"><span data-stu-id="eee00-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="eee00-138">Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="eee00-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="eee00-139">对象集合</span><span class="sxs-lookup"><span data-stu-id="eee00-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="eee00-140">显示进度</span><span class="sxs-lookup"><span data-stu-id="eee00-140">Displaying progress</span></span>](progress.md)
