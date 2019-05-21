---
title: 对象集合
description: 对象集合是一个布局控件，它可以帮助您布置预定义的三维形状中的对象的数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，控件设计
ms.openlocfilehash: 88ab0359d5083d43d5d6312ef1185f67ca0caa7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593050"
---
# <a name="object-collection"></a><span data-ttu-id="686bc-104">对象集合</span><span class="sxs-lookup"><span data-stu-id="686bc-104">Object collection</span></span>

<span data-ttu-id="686bc-105">对象集合是一个布局控件，它可以帮助您布置预定义的三维形状中的对象的数组。</span><span class="sxs-lookup"><span data-stu-id="686bc-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="686bc-106">它支持四种不同的图面上样式-**平面、 圆柱体、 球体**并**散点图**。</span><span class="sxs-lookup"><span data-stu-id="686bc-106">It supports four different surface styles - **plane, cylinder, sphere** and **scatter**.</span></span> <span data-ttu-id="686bc-107">您可以调整的 radius 和大小的对象和它们之间的空间。</span><span class="sxs-lookup"><span data-stu-id="686bc-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="686bc-108">对象集合支持 Unity 的 2D 和 3D 中的任何对象。</span><span class="sxs-lookup"><span data-stu-id="686bc-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="686bc-109">在中 **[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**，我们创建了 Unity 脚本和 [示例场景](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) 以帮助您创建的对象集合。</span><span class="sxs-lookup"><span data-stu-id="686bc-109">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, we have created Unity script and [example scene](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) that will help you create an object collection.</span></span>

<span data-ttu-id="686bc-110">![使用元素应用的定期表中的对象集合](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="686bc-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="686bc-111">*定期表元素示例应用程序中使用的对象集合*</span><span class="sxs-lookup"><span data-stu-id="686bc-111">*Object collection used in the Periodic Table of the Elements sample app*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="686bc-112">对象集合示例</span><span class="sxs-lookup"><span data-stu-id="686bc-112">Object collection examples</span></span>

<span data-ttu-id="686bc-113">[元素的定期表](periodic-table-of-the-elements.md)是演示对象集合的工作原理的示例应用。</span><span class="sxs-lookup"><span data-stu-id="686bc-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="686bc-114">它使用对象集合进行布局中不同的形状的三维化工元素框。</span><span class="sxs-lookup"><span data-stu-id="686bc-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="686bc-115">![元素应用的定期表中显示的对象集合示例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="686bc-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="686bc-116">*元素的示例应用程序的定期表中显示的对象集合示例*</span><span class="sxs-lookup"><span data-stu-id="686bc-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="686bc-117">三维对象</span><span class="sxs-lookup"><span data-stu-id="686bc-117">3D objects</span></span>

<span data-ttu-id="686bc-118">可以使用对象集合进行布局已导入三维对象。</span><span class="sxs-lookup"><span data-stu-id="686bc-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="686bc-119">以下示例演示平面和一些 3D 椅子对象的圆柱图布局。</span><span class="sxs-lookup"><span data-stu-id="686bc-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="686bc-120">![平面和三维对象的圆柱布局的示例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="686bc-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="686bc-121">*平面和三维对象的圆柱布局的示例*</span><span class="sxs-lookup"><span data-stu-id="686bc-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="686bc-122">2D 对象</span><span class="sxs-lookup"><span data-stu-id="686bc-122">2D objects</span></span>

<span data-ttu-id="686bc-123">此外可以使用对象集合使用 2D 图像。</span><span class="sxs-lookup"><span data-stu-id="686bc-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="686bc-124">下面的示例演示如何 2D 图像可以显示在网格中。</span><span class="sxs-lookup"><span data-stu-id="686bc-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![举例说明如何使用对象集合的 2D 图像](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="686bc-126">![举例说明如何使用对象集合的 2D 图像](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="686bc-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="686bc-127">*使用对象集合的 2D 图像的示例*</span><span class="sxs-lookup"><span data-stu-id="686bc-127">*Examples of 2D images with object collection*</span></span>

## <a name="see-also"></a><span data-ttu-id="686bc-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="686bc-128">See also</span></span>
* [<span data-ttu-id="686bc-129">脚本和 GitHub 上的混合现实工具包中的对象集合的预设</span><span class="sxs-lookup"><span data-stu-id="686bc-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)
* [<span data-ttu-id="686bc-130">种交互的对象</span><span class="sxs-lookup"><span data-stu-id="686bc-130">Interactable object</span></span>](interactable-object.md)
