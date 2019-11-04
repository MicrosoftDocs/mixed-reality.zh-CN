---
title: 对象集合
description: 对象集合是一个布局控件，可帮助您在预定义的三维形状中布局对象数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，控件，设计
ms.openlocfilehash: 8f3629c6d9465383efc901ed784a3719cd6fdfb2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438166"
---
# <a name="object-collection"></a><span data-ttu-id="a7761-104">对象集合</span><span class="sxs-lookup"><span data-stu-id="a7761-104">Object collection</span></span>

![在元素应用的定期表中使用的对象集合](images/640px-objectcollection-hero-640px.jpg)<br>


<span data-ttu-id="a7761-106">对象集合是一个布局控件，可帮助您在预定义的三维形状中布局对象数组。</span><span class="sxs-lookup"><span data-stu-id="a7761-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="a7761-107">它支持各种表面样式-**平面、圆柱、球面**和**放射状**。</span><span class="sxs-lookup"><span data-stu-id="a7761-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="a7761-108">您可以调整对象的半径和大小以及它们之间的空间。</span><span class="sxs-lookup"><span data-stu-id="a7761-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="a7761-109">对象集合支持从 Unity （二维和三维）的任何对象。</span><span class="sxs-lookup"><span data-stu-id="a7761-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="a7761-110">在 **[混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** 中，我们已创建了 Unity 脚本和示例，可帮助您创建对象集合。</span><span class="sxs-lookup"><span data-stu-id="a7761-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="a7761-111">对象集合示例</span><span class="sxs-lookup"><span data-stu-id="a7761-111">Object collection examples</span></span>

<span data-ttu-id="a7761-112">[元素的周期性表](periodic-table-of-the-elements.md)是一个示例应用程序，演示了对象集合的工作方式。</span><span class="sxs-lookup"><span data-stu-id="a7761-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="a7761-113">它使用对象集合来布局不同形状中的3D 化学元素框。</span><span class="sxs-lookup"><span data-stu-id="a7761-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="a7761-114">![在元素应用的定期表中显示的对象集合示例](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a7761-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="a7761-115">*在元素示例应用的定期表中显示的对象集合示例*</span><span class="sxs-lookup"><span data-stu-id="a7761-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="a7761-116">三维对象</span><span class="sxs-lookup"><span data-stu-id="a7761-116">3D objects</span></span>

<span data-ttu-id="a7761-117">可以使用对象集合对导入的3D 对象进行布局。</span><span class="sxs-lookup"><span data-stu-id="a7761-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="a7761-118">下面的示例显示了一些3D 椅子对象的平面和圆柱布局。</span><span class="sxs-lookup"><span data-stu-id="a7761-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="a7761-119">![3D 对象的平面和圆柱形布局示例](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a7761-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="a7761-120">*三维对象的平面和圆柱形布局示例*</span><span class="sxs-lookup"><span data-stu-id="a7761-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="a7761-121">2D 对象</span><span class="sxs-lookup"><span data-stu-id="a7761-121">2D objects</span></span>

<span data-ttu-id="a7761-122">您还可以将2D 图像与对象集合一起使用。</span><span class="sxs-lookup"><span data-stu-id="a7761-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="a7761-123">下面的示例演示如何在网格中显示2D 图像。</span><span class="sxs-lookup"><span data-stu-id="a7761-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![使用对象集合的2D 图像示例](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="a7761-125">使用对象集合 ![2D 图像的示例](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="a7761-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="a7761-126">*将对象集合与2D 图像一起使用的示例*</span><span class="sxs-lookup"><span data-stu-id="a7761-126">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="a7761-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7761-127">See also</span></span>
* [<span data-ttu-id="a7761-128">GitHub 上混合现实工具包中对象集合的脚本和 prototyping</span><span class="sxs-lookup"><span data-stu-id="a7761-128">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="a7761-129">可交互对象</span><span class="sxs-lookup"><span data-stu-id="a7761-129">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a7761-130">边界框</span><span class="sxs-lookup"><span data-stu-id="a7761-130">Bounding Box</span></span>](app-bar-and-bounding-box.md)
