---
title: 应用程序栏和边框
description: 应用程序栏是对象级菜单包含一系列显示一张全息图边界的下边缘的按钮。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality 应用栏，边界框
ms.openlocfilehash: bdce92e00193230d1f7a487f11ef0487f1d6657c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592401"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="5b82b-104">边界框和应用程序栏</span><span class="sxs-lookup"><span data-stu-id="5b82b-104">Bounding box and App bar</span></span>
![边界是混合现实中的对象操作的标准接口。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="5b82b-106">边界框是什么？</span><span class="sxs-lookup"><span data-stu-id="5b82b-106">What is the Bounding box?</span></span>

<span data-ttu-id="5b82b-107">边界是混合现实中的对象操作的标准接口。</span><span class="sxs-lookup"><span data-stu-id="5b82b-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="5b82b-108">它为用户提供功能的对象是当前可调整的可见性:。</span><span class="sxs-lookup"><span data-stu-id="5b82b-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="5b82b-109">角将告诉用户还可以缩放对象。</span><span class="sxs-lookup"><span data-stu-id="5b82b-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="5b82b-110">即使不可见的调整模式，这样 visual 一向用户显示对象 – 总的区域。</span><span class="sxs-lookup"><span data-stu-id="5b82b-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="5b82b-111">这一点尤其重要，因为如果存在不是，对象对齐到另一个对象或面似乎行为就如同时不应在那里它周围的空间。</span><span class="sxs-lookup"><span data-stu-id="5b82b-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="5b82b-112">HoloLens 2 上的边界框来响应用户的手指的邻近性。</span><span class="sxs-lookup"><span data-stu-id="5b82b-112">On HoloLens 2, the bounding box responds to the user's finger's proximity.</span></span> <span data-ttu-id="5b82b-113">它显示了可视反馈以帮助找到了该对象的距离。</span><span class="sxs-lookup"><span data-stu-id="5b82b-113">It shows visual feedback to help perceive the distance from the object.</span></span> 

<span data-ttu-id="5b82b-114">![HoloLens-的角度来看的缩放通过边界框的对象](images/bounding-box-scale.gif)</span><span class="sxs-lookup"><span data-stu-id="5b82b-114">![HoloLens point-of-view of scaling an object via bounding box](images/bounding-box-scale.gif)</span></span><br>
<span data-ttu-id="5b82b-115">*缩放通过边界框的对象*</span><span class="sxs-lookup"><span data-stu-id="5b82b-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="5b82b-116">边界框的类似于多维数据集的角遵循用于调整规模广为人知的模式。</span><span class="sxs-lookup"><span data-stu-id="5b82b-116">The cube-like corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="5b82b-117">耦合与显式将一个对象放到"调整模式"的操作很明显，他们可以同时移动对象，但还在其环境中对它进行缩放。</span><span class="sxs-lookup"><span data-stu-id="5b82b-117">Coupled with the explicit action of putting an object into “adjust mode” it’s clear they can both move the object, but also scale it in their environment.</span></span>

<span data-ttu-id="5b82b-118">![HoloLens-的角度来看旋转通过边界框的对象](images/bounding-box-rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="5b82b-118">![HoloLens point-of-view of rotating an object via bounding box](images/bounding-box-rotate.gif)</span></span><br>
<span data-ttu-id="5b82b-119">*旋转对象通过边界框*</span><span class="sxs-lookup"><span data-stu-id="5b82b-119">*Rotating an object via bounding box*</span></span>

<span data-ttu-id="5b82b-120">边界框的边缘上球面的提示是旋转指示符。</span><span class="sxs-lookup"><span data-stu-id="5b82b-120">The spherical affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="5b82b-121">此选项会使用户更多的精细调整能够对其置入全息。</span><span class="sxs-lookup"><span data-stu-id="5b82b-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="5b82b-122">不仅可以在调整和缩放，但现在还包括旋转。</span><span class="sxs-lookup"><span data-stu-id="5b82b-122">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="5b82b-123">Unity 应用程序开发，请参阅[边界框上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="5b82b-123">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>

## <a name="what-is-the-app-bar"></a><span data-ttu-id="5b82b-124">什么是应用程序栏？</span><span class="sxs-lookup"><span data-stu-id="5b82b-124">What is the App bar?</span></span>

<span data-ttu-id="5b82b-125">应用程序栏是对象级菜单包含一系列显示一张全息图边界的下边缘的按钮。</span><span class="sxs-lookup"><span data-stu-id="5b82b-125">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="5b82b-126">此模式通常用于使用户能够删除和调整全息。</span><span class="sxs-lookup"><span data-stu-id="5b82b-126">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="5b82b-127">由于此模式用于访问对象，该对象周围移动用户而言是完全锁定状态，应用程序栏将始终显示在最靠近用户的选择对象端。</span><span class="sxs-lookup"><span data-stu-id="5b82b-127">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="5b82b-128">虽然这不公告板，它有效地实现相同的结果;阻止用户的位置以遮蔽或应可从其环境中的不同位置的块功能。</span><span class="sxs-lookup"><span data-stu-id="5b82b-128">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="5b82b-129">![移动办公了一张全息图。</span><span class="sxs-lookup"><span data-stu-id="5b82b-129">![Walking around a hologram.</span></span> <span data-ttu-id="5b82b-130">遵循应用程序栏。](images/holobar-followuser.gif)</span><span class="sxs-lookup"><span data-stu-id="5b82b-130">The App bar follows.](images/holobar-followuser.gif)</span></span><br>
<span data-ttu-id="5b82b-131">*移动办公了一张全息图，遵循应用程序栏*</span><span class="sxs-lookup"><span data-stu-id="5b82b-131">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="5b82b-132">应用栏旨在主要作为一种方法来管理用户的环境中放置的对象。</span><span class="sxs-lookup"><span data-stu-id="5b82b-132">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="5b82b-133">耦合在一起的边界框，用户可以完全控制在何处以及如何在混合现实方向，对象。</span><span class="sxs-lookup"><span data-stu-id="5b82b-133">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="5b82b-134">Unity 应用程序开发，请参阅[应用栏上混合现实工具包的 Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="5b82b-134">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="5b82b-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="5b82b-135">See also</span></span>
* [<span data-ttu-id="5b82b-136">边界框上混合现实工具包的 Unity</span><span class="sxs-lookup"><span data-stu-id="5b82b-136">Bounding box on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)
* [<span data-ttu-id="5b82b-137">应用栏上混合现实工具包的 Unity</span><span class="sxs-lookup"><span data-stu-id="5b82b-137">App bar on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)
* [<span data-ttu-id="5b82b-138">种交互的对象</span><span class="sxs-lookup"><span data-stu-id="5b82b-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5b82b-139">在 Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="5b82b-139">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="5b82b-140">对象集合</span><span class="sxs-lookup"><span data-stu-id="5b82b-140">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5b82b-141">显示进度</span><span class="sxs-lookup"><span data-stu-id="5b82b-141">Displaying progress</span></span>](progress.md)
