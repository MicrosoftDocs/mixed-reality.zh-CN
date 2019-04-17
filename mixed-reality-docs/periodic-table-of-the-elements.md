---
title: 定期表的元素
description: 元素的定期表是开放源代码示例应用程序从 Microsoft 的混合现实设计实验室可从中了解如何使用各种使用对象集合的图面类型设置布局在 3D 空间中的对象的数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 示例应用程序、 控件
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592865"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="f320f-104">定期表的元素</span><span class="sxs-lookup"><span data-stu-id="f320f-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="f320f-105">本文讨论了我们已在中创建一个探索示例[混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)，其中我们共享有关我们的知识和建议的混合现实应用程序开发。</span><span class="sxs-lookup"><span data-stu-id="f320f-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="f320f-106">当我们进行新的发现，我们与设计相关文章和代码将发展。</span><span class="sxs-lookup"><span data-stu-id="f320f-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="f320f-107">[元素的定期表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是来自 Microsoft 的混合现实设计实验室一个开放源代码示例应用。</span><span class="sxs-lookup"><span data-stu-id="f320f-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="f320f-108">与此项目中，可以了解如何使用各种图面上的类型使用设置布局在 3D 空间中的对象的数组**[对象集合](object-collection.md)**。</span><span class="sxs-lookup"><span data-stu-id="f320f-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="f320f-109">此外了解如何创建种交互响应来自 HoloLens 的标准输入的对象。</span><span class="sxs-lookup"><span data-stu-id="f320f-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="f320f-110">可以使用此项目的组件来创建你自己的混合现实应用体验。</span><span class="sxs-lookup"><span data-stu-id="f320f-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![时间段表的元素应用](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="f320f-112">有关应用程序</span><span class="sxs-lookup"><span data-stu-id="f320f-112">About the app</span></span>

<span data-ttu-id="f320f-113">定期表的元素的可视化化工元素和每个 3D 空间中的其属性。</span><span class="sxs-lookup"><span data-stu-id="f320f-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="f320f-114">它集成了 HoloLens 等的视线移动和 air 点击的基本交互。</span><span class="sxs-lookup"><span data-stu-id="f320f-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="f320f-115">用户可以了解具有经过动画处理三维模型的元素。</span><span class="sxs-lookup"><span data-stu-id="f320f-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="f320f-116">它们可以直观地了解元素的 electron shell 和其核心-由质子和 neutrons 组成。</span><span class="sxs-lookup"><span data-stu-id="f320f-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="f320f-117">后台</span><span class="sxs-lookup"><span data-stu-id="f320f-117">Background</span></span>

<span data-ttu-id="f320f-118">我首次遇到 HoloLens 后，定期表应用时的了解我知道，我希望尝试混合现实中使用。</span><span class="sxs-lookup"><span data-stu-id="f320f-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="f320f-119">由于每个元素将以文本显示的多个数据点，我认为它是用于浏览在 3D 空间中的版式组合的有用主题事项。</span><span class="sxs-lookup"><span data-stu-id="f320f-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="f320f-120">能够可视化元素的 electron 模型是此项目的另一个有趣的一部分。</span><span class="sxs-lookup"><span data-stu-id="f320f-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="f320f-121">设计</span><span class="sxs-lookup"><span data-stu-id="f320f-121">Design</span></span>

<span data-ttu-id="f320f-122">对于定期表的默认视图中，我可以想象将包含每个元素的 electron 模型的三维框。</span><span class="sxs-lookup"><span data-stu-id="f320f-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="f320f-123">每个框的面将透明，以便用户可以获取元素的卷的粗略。</span><span class="sxs-lookup"><span data-stu-id="f320f-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="f320f-124">视线移动和 air 点击，用户可以打开每个元素的详细视图。</span><span class="sxs-lookup"><span data-stu-id="f320f-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="f320f-125">若要使表视图和详细信息视图之间的转换平滑和自然，我得类似于在现实生活中打开一个框的物理交互。</span><span class="sxs-lookup"><span data-stu-id="f320f-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="f320f-126">![设计草图](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="f320f-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="f320f-127">*设计草图*</span><span class="sxs-lookup"><span data-stu-id="f320f-127">*Design sketches*</span></span>

<span data-ttu-id="f320f-128">在详细信息视图中，我想要可视化的美观地呈现在 3D 空间中的文本与每个元素的信息。</span><span class="sxs-lookup"><span data-stu-id="f320f-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="f320f-129">动画三维 electron 模型显示在中心区域，并且可以从不同角度查看。</span><span class="sxs-lookup"><span data-stu-id="f320f-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![交互](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="f320f-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="f320f-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="f320f-132">*交互原型*</span><span class="sxs-lookup"><span data-stu-id="f320f-132">*Interaction prototypes*</span></span>

<span data-ttu-id="f320f-133">用户可以通过点击底部的表上的按钮以无线方式来更改图面上的类型-它们可以平面、 圆柱体、 球体和散点图之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="f320f-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="f320f-134">常见控件和此应用中使用的模式</span><span class="sxs-lookup"><span data-stu-id="f320f-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="f320f-135">种交互对象 （按钮）</span><span class="sxs-lookup"><span data-stu-id="f320f-135">Interactable object (button)</span></span>

<span data-ttu-id="f320f-136">[种交互对象](interactable-object.md)是可以对基本 HoloLens 输入作出响应的对象。</span><span class="sxs-lookup"><span data-stu-id="f320f-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="f320f-137">它作为方便地将应用于任何对象的预设/脚本提供。</span><span class="sxs-lookup"><span data-stu-id="f320f-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="f320f-138">例如，可以使您的场景中的咖啡杯种交互，并响应如注视、 敲击、 导航和操作手势输入。</span><span class="sxs-lookup"><span data-stu-id="f320f-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="f320f-139">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="f320f-139">Learn more</span></span>](interactable-object.md)

![nteractable 对象](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="f320f-141">对象集合</span><span class="sxs-lookup"><span data-stu-id="f320f-141">Object collection</span></span>

<span data-ttu-id="f320f-142">[对象集合](object-collection.md)是的有助于布局中各种形状的多个对象的一个对象。</span><span class="sxs-lookup"><span data-stu-id="f320f-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="f320f-143">它支持平面、 圆柱体、 球体和散点图。</span><span class="sxs-lookup"><span data-stu-id="f320f-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="f320f-144">可以配置其他属性，如半径，数量的行和间距。</span><span class="sxs-lookup"><span data-stu-id="f320f-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="f320f-145">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="f320f-145">Learn more</span></span>](object-collection.md)

![对象集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="f320f-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="f320f-147">Fitbox</span></span>

<span data-ttu-id="f320f-148">将默认情况下，在其中观望用户位置中放置全息目前启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="f320f-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="f320f-149">这有时会导致不需要的结果，如全息背后墙或中间表放置。</span><span class="sxs-lookup"><span data-stu-id="f320f-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="f320f-150">Fitbox 允许用户使用的视线移动来确定放置全息图的位置。</span><span class="sxs-lookup"><span data-stu-id="f320f-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="f320f-151">它由用简单的 PNG 图像纹理可轻松地自定义与你自己的映像或三维对象。</span><span class="sxs-lookup"><span data-stu-id="f320f-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="f320f-153">技术细节</span><span class="sxs-lookup"><span data-stu-id="f320f-153">Technical details</span></span>

<span data-ttu-id="f320f-154">有关脚本和预设定期表的元素应用[混合现实设计实验室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)。</span><span class="sxs-lookup"><span data-stu-id="f320f-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="f320f-155">应用程序示例</span><span class="sxs-lookup"><span data-stu-id="f320f-155">Application examples</span></span>

<span data-ttu-id="f320f-156">以下是有关您可以创建通过利用此项目中的组件的一些建议。</span><span class="sxs-lookup"><span data-stu-id="f320f-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="f320f-157">股票数据可视化应用</span><span class="sxs-lookup"><span data-stu-id="f320f-157">Stock data visualization app</span></span>

<span data-ttu-id="f320f-158">与定期表的元素的示例中使用的相同控件和交互模型，您可以构建应用它将直观显示股票市场数据。</span><span class="sxs-lookup"><span data-stu-id="f320f-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="f320f-159">此示例使用对象集合控件进行布局球面形状中的常用数据。</span><span class="sxs-lookup"><span data-stu-id="f320f-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="f320f-160">您可以假设其中无法以有趣的方式显示有关每个股票的其他信息的详细信息视图。</span><span class="sxs-lookup"><span data-stu-id="f320f-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![应用程序示例：财务 (第 1 个 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![应用程序示例：财务 (共 2 个 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="f320f-163">![应用程序示例：财务 3 部分 （共 3）](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="f320f-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="f320f-164">*下面举例说明如何在财务应用程序中使用元素示例应用程序的定期表中使用的对象集合*</span><span class="sxs-lookup"><span data-stu-id="f320f-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="f320f-165">体育应用</span><span class="sxs-lookup"><span data-stu-id="f320f-165">Sports app</span></span>

<span data-ttu-id="f320f-166">这是可视化对象集合和其他组件的定期表中的元素示例应用程序使用的运动数据的示例。</span><span class="sxs-lookup"><span data-stu-id="f320f-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![应用程序示例：体育 (第 1 个 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![应用程序示例：体育 (共 2 个 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="f320f-169">![应用程序示例：体育 3 部分 （共 3）](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="f320f-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="f320f-170">*在体育应用程序中使用对象集合的元素示例 appcould 定期表中的使用方式的示例*</span><span class="sxs-lookup"><span data-stu-id="f320f-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="f320f-171">关于作者</span><span class="sxs-lookup"><span data-stu-id="f320f-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f320f-172"><b>盾 Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="f320f-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="f320f-173">UX 设计人员 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f320f-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="f320f-174">请参阅</span><span class="sxs-lookup"><span data-stu-id="f320f-174">See also</span></span>

* [<span data-ttu-id="f320f-175">种交互的对象</span><span class="sxs-lookup"><span data-stu-id="f320f-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f320f-176">对象集合</span><span class="sxs-lookup"><span data-stu-id="f320f-176">Object collection</span></span>](object-collection.md)
