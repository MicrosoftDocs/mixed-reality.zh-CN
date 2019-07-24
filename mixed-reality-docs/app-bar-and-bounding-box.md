---
title: 边界框和应用栏
description: 应用栏是一个对象级菜单, 其中包含一系列按钮, 它们显示在全息图边界的下边缘。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, 应用栏, 边界框
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829686"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="3dc90-104">边界框和应用栏</span><span class="sxs-lookup"><span data-stu-id="3dc90-104">Bounding box and App bar</span></span>
!["边界" 是用于在混合现实中进行对象操作的标准接口。](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="3dc90-106">什么是边界框？</span><span class="sxs-lookup"><span data-stu-id="3dc90-106">What is the Bounding box?</span></span>

<span data-ttu-id="3dc90-107">"边界" 是用于在混合现实中进行对象操作的标准接口。</span><span class="sxs-lookup"><span data-stu-id="3dc90-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="3dc90-108">它向用户提供当前可调整对象的 affordance。</span><span class="sxs-lookup"><span data-stu-id="3dc90-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="3dc90-109">角告诉用户对象还可以缩放。</span><span class="sxs-lookup"><span data-stu-id="3dc90-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="3dc90-110">此视觉对象 affordance 向用户显示对象的总区域–即使它在调整模式之外不可见。</span><span class="sxs-lookup"><span data-stu-id="3dc90-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="3dc90-111">这一点特别重要, 因为如果不存在, 则与另一个对象或表面对齐的对象可能看起来好像不应存在的空间。</span><span class="sxs-lookup"><span data-stu-id="3dc90-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="3dc90-112">在 HoloLens 2 上, 边界框适用于直接操作, 并响应用户的 finger's 邻近性。</span><span class="sxs-lookup"><span data-stu-id="3dc90-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="3dc90-113">它显示了视觉反馈, 可帮助用户感知与对象的距离。</span><span class="sxs-lookup"><span data-stu-id="3dc90-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="3dc90-114">![HoloLens 通过边界框缩放对象的观点](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="3dc90-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="3dc90-115">*通过边界框缩放对象*</span><span class="sxs-lookup"><span data-stu-id="3dc90-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="3dc90-116">边界框的角上的控点遵循用于调整刻度的广泛理解的模式。</span><span class="sxs-lookup"><span data-stu-id="3dc90-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="3dc90-117">![HoloLens 通过边界框旋转对象的观点](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="3dc90-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="3dc90-118">*通过边界框旋转对象*</span><span class="sxs-lookup"><span data-stu-id="3dc90-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="3dc90-119">![视觉对象反馈](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="3dc90-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="3dc90-120">*基于邻近性的视觉反馈*</span><span class="sxs-lookup"><span data-stu-id="3dc90-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="3dc90-121">边界框边缘的垂直矩形实用是旋转指示器。</span><span class="sxs-lookup"><span data-stu-id="3dc90-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="3dc90-122">这样, 用户就可以更好地调整其放置的全息影像。</span><span class="sxs-lookup"><span data-stu-id="3dc90-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="3dc90-123">它们不仅可以进行调整和缩放, 还可以进行旋转。</span><span class="sxs-lookup"><span data-stu-id="3dc90-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="3dc90-124">对于 Unity 应用开发, 请参阅[混合现实工具包上的边界框-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="3dc90-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="3dc90-125">什么是应用栏？</span><span class="sxs-lookup"><span data-stu-id="3dc90-125">What is the App bar?</span></span>

<span data-ttu-id="3dc90-126">应用栏是一个对象级菜单, 其中包含一系列按钮, 它们显示在全息图边界的下边缘。</span><span class="sxs-lookup"><span data-stu-id="3dc90-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="3dc90-127">此模式通常用于使用户能够删除和调整全息影像。</span><span class="sxs-lookup"><span data-stu-id="3dc90-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="3dc90-128">由于此模式与世界锁定的对象一起使用, 因此当用户在对象周围移动时, 应用栏将始终显示在最靠近用户的对象端。</span><span class="sxs-lookup"><span data-stu-id="3dc90-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="3dc90-129">尽管这不是 billboarding 的, 但它实际上实现了相同的结果;防止用户遮蔽或阻止在其环境中的其他位置可用的功能。</span><span class="sxs-lookup"><span data-stu-id="3dc90-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="3dc90-130">![浏览全息图。</span><span class="sxs-lookup"><span data-stu-id="3dc90-130">![Walking around a hologram.</span></span> <span data-ttu-id="3dc90-131">应用栏如下所示。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="3dc90-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="3dc90-132">*浏览全息图, 应用栏如下所示*</span><span class="sxs-lookup"><span data-stu-id="3dc90-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="3dc90-133">应用栏的设计主要是在用户的环境中管理已放置对象的方式。</span><span class="sxs-lookup"><span data-stu-id="3dc90-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="3dc90-134">与边界框结合使用, 用户可以完全控制对象在混合现实中的位置和方式。</span><span class="sxs-lookup"><span data-stu-id="3dc90-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="3dc90-135">有关 Unity 应用开发, 请参阅[混合现实工具包上的应用栏-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="3dc90-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="3dc90-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="3dc90-136">See also</span></span>
* [<span data-ttu-id="3dc90-137">可交互对象</span><span class="sxs-lookup"><span data-stu-id="3dc90-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="3dc90-138">Unity 中的文本</span><span class="sxs-lookup"><span data-stu-id="3dc90-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="3dc90-139">对象集合</span><span class="sxs-lookup"><span data-stu-id="3dc90-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="3dc90-140">显示进度</span><span class="sxs-lookup"><span data-stu-id="3dc90-140">Displaying progress</span></span>](progress.md)
