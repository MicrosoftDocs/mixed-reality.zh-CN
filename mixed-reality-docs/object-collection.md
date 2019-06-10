---
title: 对象集合
description: 对象集合是一个布局控件，它可以帮助您布置预定义的三维形状中的对象的数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，控件设计
ms.openlocfilehash: 7c3bbd82ec909b5a2e3c81f122366be564934f4d
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813887"
---
# <a name="object-collection"></a><span data-ttu-id="e8615-104">对象集合</span><span class="sxs-lookup"><span data-stu-id="e8615-104">Object collection</span></span>

<span data-ttu-id="e8615-105">对象集合是一个布局控件，它可以帮助您布置预定义的三维形状中的对象的数组。</span><span class="sxs-lookup"><span data-stu-id="e8615-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="e8615-106">它支持各种图面上的样式-**平面、 圆柱体、 球体**并**径向**。</span><span class="sxs-lookup"><span data-stu-id="e8615-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="e8615-107">您可以调整的 radius 和大小的对象和它们之间的空间。</span><span class="sxs-lookup"><span data-stu-id="e8615-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="e8615-108">对象集合支持 Unity 的 2D 和 3D 中的任何对象。</span><span class="sxs-lookup"><span data-stu-id="e8615-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="e8615-109">在中 **[混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** ，我们创建了 Unity 脚本并将帮助您的示例创建对象集合。</span><span class="sxs-lookup"><span data-stu-id="e8615-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="e8615-110">![使用元素应用的定期表中的对象集合](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e8615-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="e8615-111">*使用对象集合的示例*</span><span class="sxs-lookup"><span data-stu-id="e8615-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="e8615-112">对象集合示例</span><span class="sxs-lookup"><span data-stu-id="e8615-112">Object collection examples</span></span>

<span data-ttu-id="e8615-113">[元素的定期表](periodic-table-of-the-elements.md)是演示对象集合的工作原理的示例应用。</span><span class="sxs-lookup"><span data-stu-id="e8615-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="e8615-114">它使用对象集合进行布局中不同的形状的三维化工元素框。</span><span class="sxs-lookup"><span data-stu-id="e8615-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="e8615-115">![元素应用的定期表中显示的对象集合示例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e8615-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="e8615-116">*元素的示例应用程序的定期表中显示的对象集合示例*</span><span class="sxs-lookup"><span data-stu-id="e8615-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="e8615-117">三维对象</span><span class="sxs-lookup"><span data-stu-id="e8615-117">3D objects</span></span>

<span data-ttu-id="e8615-118">可以使用对象集合进行布局已导入三维对象。</span><span class="sxs-lookup"><span data-stu-id="e8615-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="e8615-119">以下示例演示平面和一些 3D 椅子对象的圆柱图布局。</span><span class="sxs-lookup"><span data-stu-id="e8615-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="e8615-120">![平面和三维对象的圆柱布局的示例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e8615-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="e8615-121">*平面和三维对象的圆柱布局的示例*</span><span class="sxs-lookup"><span data-stu-id="e8615-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="e8615-122">2D 对象</span><span class="sxs-lookup"><span data-stu-id="e8615-122">2D objects</span></span>

<span data-ttu-id="e8615-123">此外可以使用对象集合使用 2D 图像。</span><span class="sxs-lookup"><span data-stu-id="e8615-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="e8615-124">下面的示例演示如何 2D 图像可以显示在网格中。</span><span class="sxs-lookup"><span data-stu-id="e8615-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![举例说明如何使用对象集合的 2D 图像](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="e8615-126">![举例说明如何使用对象集合的 2D 图像](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="e8615-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="e8615-127">*使用 2D 图像对象集合的示例*</span><span class="sxs-lookup"><span data-stu-id="e8615-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="e8615-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="e8615-128">See also</span></span>
* [<span data-ttu-id="e8615-129">脚本和 GitHub 上的混合现实工具包中的对象集合的预设</span><span class="sxs-lookup"><span data-stu-id="e8615-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="e8615-130">可交互对象</span><span class="sxs-lookup"><span data-stu-id="e8615-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e8615-131">边界框</span><span class="sxs-lookup"><span data-stu-id="e8615-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
