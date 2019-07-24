---
title: 元素周期表
description: 定期表是 Microsoft 的混合现实设计实验室中的一个开源示例应用, 你可以在其中了解如何使用对象集合在三维空间中使用不同的表面类型布置对象数组。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 设计, 示例应用, 控件
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525402"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="90cb5-104">元素周期表</span><span class="sxs-lookup"><span data-stu-id="90cb5-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="90cb5-105">本文讨论了我们在[混合现实设计实验室](https://github.com/Microsoft/MRDesignLabs_Unity)中创建的探索示例, 这是我们与混合现实应用开发的知识和建议。</span><span class="sxs-lookup"><span data-stu-id="90cb5-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="90cb5-106">我们设计相关的文章和代码将随着我们的新发现而发展。</span><span class="sxs-lookup"><span data-stu-id="90cb5-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="90cb5-107">[定期表](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)是 Microsoft 混合现实设计实验室中的一个开源示例应用。</span><span class="sxs-lookup"><span data-stu-id="90cb5-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="90cb5-108">与此项目中，可以了解如何使用各种图面上的类型使用设置布局在 3D 空间中的对象的数组 **[对象集合](object-collection.md)** 。</span><span class="sxs-lookup"><span data-stu-id="90cb5-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="90cb5-109">还将了解如何创建响应 HoloLens 标准输入的种不可交互对象。</span><span class="sxs-lookup"><span data-stu-id="90cb5-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="90cb5-110">您可以使用此项目的组件来创建自己的混合现实应用程序体验。</span><span class="sxs-lookup"><span data-stu-id="90cb5-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![元素应用的 Period 表](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="90cb5-112">关于应用</span><span class="sxs-lookup"><span data-stu-id="90cb5-112">About the app</span></span>

<span data-ttu-id="90cb5-113">元素的周期性表在三维空间中直观显示化学元素及其每个属性。</span><span class="sxs-lookup"><span data-stu-id="90cb5-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="90cb5-114">它结合了 HoloLens 的基本交互, 如注视和分流。</span><span class="sxs-lookup"><span data-stu-id="90cb5-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="90cb5-115">用户可以了解带有动画3D 模型的元素。</span><span class="sxs-lookup"><span data-stu-id="90cb5-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="90cb5-116">它们可以直观地了解元素的 electron shell 及其核心, 这是由 protons 和 neutrons 组成的。</span><span class="sxs-lookup"><span data-stu-id="90cb5-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="90cb5-117">后台</span><span class="sxs-lookup"><span data-stu-id="90cb5-117">Background</span></span>

<span data-ttu-id="90cb5-118">在我首次体验 HoloLens 后, 我知道我想在混合现实中尝试使用定期表应用程序。</span><span class="sxs-lookup"><span data-stu-id="90cb5-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="90cb5-119">由于每个元素都有多个与文本一起显示的数据点, 因此, 我认为这对于浏览三维空间中的排版组合非常重要。</span><span class="sxs-lookup"><span data-stu-id="90cb5-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="90cb5-120">在此项目中, 可以可视化元素的 electron 模型是另一个有趣的部分。</span><span class="sxs-lookup"><span data-stu-id="90cb5-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="90cb5-121">设计</span><span class="sxs-lookup"><span data-stu-id="90cb5-121">Design</span></span>

<span data-ttu-id="90cb5-122">对于周期性表的默认视图, 我想要将包含每个元素的 electron 模型的三维方框。</span><span class="sxs-lookup"><span data-stu-id="90cb5-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="90cb5-123">每个框的表面都是透明的, 这样用户就可以大致了解元素的音量。</span><span class="sxs-lookup"><span data-stu-id="90cb5-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="90cb5-124">使用注视和空中点击, 用户可以打开每个元素的详细视图。</span><span class="sxs-lookup"><span data-stu-id="90cb5-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="90cb5-125">为了使表视图和详细信息视图之间的过渡平滑和自然, 我使其类似于实际生活中打开的方框的物理交互。</span><span class="sxs-lookup"><span data-stu-id="90cb5-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="90cb5-126">![设计草图](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="90cb5-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="90cb5-127">*设计草图*</span><span class="sxs-lookup"><span data-stu-id="90cb5-127">*Design sketches*</span></span>

<span data-ttu-id="90cb5-128">在详细信息视图中, 我想要将每个元素的信息可视化到三维空间中完美呈现的文本。</span><span class="sxs-lookup"><span data-stu-id="90cb5-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="90cb5-129">动画 3D electron 模型将显示在中心区域, 并且可以从不同角度查看。</span><span class="sxs-lookup"><span data-stu-id="90cb5-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![交互](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="90cb5-131">![原型](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="90cb5-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="90cb5-132">*交互原型*</span><span class="sxs-lookup"><span data-stu-id="90cb5-132">*Interaction prototypes*</span></span>

<span data-ttu-id="90cb5-133">用户可以通过点击表格底部的按钮来更改曲面类型, 它们可以在平面、圆柱、球和散点之间切换。</span><span class="sxs-lookup"><span data-stu-id="90cb5-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="90cb5-134">此应用中使用的公共控件和模式</span><span class="sxs-lookup"><span data-stu-id="90cb5-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="90cb5-135">种不可交互对象 (按钮)</span><span class="sxs-lookup"><span data-stu-id="90cb5-135">Interactable object (button)</span></span>

<span data-ttu-id="90cb5-136">[种不可交互对象](interactable-object.md)是可响应基本的 HoloLens 输入的对象。</span><span class="sxs-lookup"><span data-stu-id="90cb5-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="90cb5-137">它以 prefab/脚本形式提供, 你可以轻松地将其应用于任何对象。</span><span class="sxs-lookup"><span data-stu-id="90cb5-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="90cb5-138">例如, 可以在场景种不可交互中发出咖啡杯, 并对输入 (如注视、分流、导航和操作手势) 做出响应。</span><span class="sxs-lookup"><span data-stu-id="90cb5-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="90cb5-139">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="90cb5-139">Learn more</span></span>](interactable-object.md)

![nteractable 对象](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="90cb5-141">对象集合</span><span class="sxs-lookup"><span data-stu-id="90cb5-141">Object collection</span></span>

<span data-ttu-id="90cb5-142">[对象集合](object-collection.md)是一个对象, 可帮助您在不同的形状中布局多个对象。</span><span class="sxs-lookup"><span data-stu-id="90cb5-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="90cb5-143">它支持平面、圆柱、球面和散点图。</span><span class="sxs-lookup"><span data-stu-id="90cb5-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="90cb5-144">可以配置其他属性, 如 radius、行数和间距。</span><span class="sxs-lookup"><span data-stu-id="90cb5-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="90cb5-145">了解详细信息</span><span class="sxs-lookup"><span data-stu-id="90cb5-145">Learn more</span></span>](object-collection.md)

![对象集合](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="90cb5-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="90cb5-147">Fitbox</span></span>

<span data-ttu-id="90cb5-148">默认情况下, 将在启动应用程序时, 将全息影像置于用户正在 gazing 的位置。</span><span class="sxs-lookup"><span data-stu-id="90cb5-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="90cb5-149">这有时会导致不需要的结果, 如全息影像位于墙壁后面或表中间。</span><span class="sxs-lookup"><span data-stu-id="90cb5-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="90cb5-150">Fitbox 允许用户使用 "注视" 来确定要放置全息影像的位置。</span><span class="sxs-lookup"><span data-stu-id="90cb5-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="90cb5-151">使用简单的 PNG 图像纹理进行创建, 可以使用自己的图像或三维对象轻松自定义该纹理。</span><span class="sxs-lookup"><span data-stu-id="90cb5-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="90cb5-153">技术细节</span><span class="sxs-lookup"><span data-stu-id="90cb5-153">Technical details</span></span>

<span data-ttu-id="90cb5-154">可在[混合现实设计实验室 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)上查找元素应用的定期表的脚本和 prototyping。</span><span class="sxs-lookup"><span data-stu-id="90cb5-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="90cb5-155">应用程序示例</span><span class="sxs-lookup"><span data-stu-id="90cb5-155">Application examples</span></span>

<span data-ttu-id="90cb5-156">下面是利用此项目中的组件可以创建的一些建议。</span><span class="sxs-lookup"><span data-stu-id="90cb5-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="90cb5-157">股票数据可视化应用</span><span class="sxs-lookup"><span data-stu-id="90cb5-157">Stock data visualization app</span></span>

<span data-ttu-id="90cb5-158">使用与 "元素" 示例的 "定期" 表相同的控件和交互模型, 可以构建一个直观显示股票市场数据的应用。</span><span class="sxs-lookup"><span data-stu-id="90cb5-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="90cb5-159">此示例使用对象集合控件来布局球面形状中的股票数据。</span><span class="sxs-lookup"><span data-stu-id="90cb5-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="90cb5-160">您可以想象一个详细信息视图, 其中每个股票的其他信息可能以一种有趣的方式显示。</span><span class="sxs-lookup"><span data-stu-id="90cb5-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![应用程序示例:财务 (共3个)](images/640px-periodictable-applicationexamples-finance1.jpg)

![应用程序示例:财务 (2/3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="90cb5-163">![应用程序示例:财务 (3 个)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="90cb5-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="90cb5-164">*有关如何在 "元素示例" 应用的 "定期" 表中使用的对象集合的示例, 可在金融应用中使用*</span><span class="sxs-lookup"><span data-stu-id="90cb5-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="90cb5-165">体育应用</span><span class="sxs-lookup"><span data-stu-id="90cb5-165">Sports app</span></span>

<span data-ttu-id="90cb5-166">这是使用对象集合和元素示例应用的定期表中的其他组件来可视化运动数据的一个示例。</span><span class="sxs-lookup"><span data-stu-id="90cb5-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![应用程序示例:体育 (共3个)](images/640px-periodictable-applicationexamples-sports0.jpg)

![应用程序示例:体育 (2/3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="90cb5-169">![应用程序示例:体育 (3 个)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="90cb5-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="90cb5-170">*有关如何在体育应用中使用在元素的周期性表中使用的对象集合的示例 appcould*</span><span class="sxs-lookup"><span data-stu-id="90cb5-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="90cb5-171">关于作者</span><span class="sxs-lookup"><span data-stu-id="90cb5-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="90cb5-172"><b>盾 Yoon 停车场</b></span><span class="sxs-lookup"><span data-stu-id="90cb5-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="90cb5-173">UX 设计器@Microsoft</span><span class="sxs-lookup"><span data-stu-id="90cb5-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="90cb5-174">请参阅</span><span class="sxs-lookup"><span data-stu-id="90cb5-174">See also</span></span>

* [<span data-ttu-id="90cb5-175">可交互对象</span><span class="sxs-lookup"><span data-stu-id="90cb5-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="90cb5-176">对象集合</span><span class="sxs-lookup"><span data-stu-id="90cb5-176">Object collection</span></span>](object-collection.md)
