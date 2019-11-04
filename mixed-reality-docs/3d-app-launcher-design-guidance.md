---
title: 3D 应用启动器设计指南
description: 3D 应用启动器是用户混合现实房子中的 "物理" 对象，他们可以选择启动应用。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，3D 应用程序启动器，沉浸式耳机，活动立方体
ms.openlocfilehash: ce9d242e26d67c8fe5af7ac32f4e910a15715d25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437229"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="f229e-104">3D 应用启动器设计指南</span><span class="sxs-lookup"><span data-stu-id="f229e-104">3D app launcher design guidance</span></span>

<span data-ttu-id="f229e-105">当你置于 Windows Mixed Reality 沉浸式（VR）头戴式耳机上时，你将进入 Windows Mixed Reality 主页，并在 cliff 的周围（尽管你可以[选择其他环境，甚至创建你自己的环境](add-custom-home-environments.md)）以房屋的形式可视化。</span><span class="sxs-lookup"><span data-stu-id="f229e-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="f229e-106">在此家中，用户可以自由地按所需的方式排列和组织3D 对象和应用。</span><span class="sxs-lookup"><span data-stu-id="f229e-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="f229e-107">**3d 应用启动器**是用户混合现实房子中的 "物理" 对象，他们可以选择启动应用。</span><span class="sxs-lookup"><span data-stu-id="f229e-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="f229e-108">![示例： Floaty 鸟3D 应用启动器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f229e-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="f229e-109">*Floaty 鸟3D 应用启动器示例（虚拟应用）*</span><span class="sxs-lookup"><span data-stu-id="f229e-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="f229e-110">3D 应用程序启动器创建过程</span><span class="sxs-lookup"><span data-stu-id="f229e-110">3D app launcher creation process</span></span>

<span data-ttu-id="f229e-111">创建三维应用启动器有三个步骤：</span><span class="sxs-lookup"><span data-stu-id="f229e-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="f229e-112">设计和 concepting （本文）</span><span class="sxs-lookup"><span data-stu-id="f229e-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="f229e-113">建模和导出</span><span class="sxs-lookup"><span data-stu-id="f229e-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="f229e-114">将其集成到应用程序中：</span><span class="sxs-lookup"><span data-stu-id="f229e-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="f229e-115">UWP 应用</span><span class="sxs-lookup"><span data-stu-id="f229e-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="f229e-116">Win32 应用</span><span class="sxs-lookup"><span data-stu-id="f229e-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="f229e-117">设计概念</span><span class="sxs-lookup"><span data-stu-id="f229e-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="f229e-118">太棒了</span><span class="sxs-lookup"><span data-stu-id="f229e-118">Fantastic yet familiar</span></span>

<span data-ttu-id="f229e-119">应用启动器所在的 Windows Mixed Reality 环境是部分熟悉的部分精巧/科幻。</span><span class="sxs-lookup"><span data-stu-id="f229e-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="f229e-120">最佳启动器遵循这一领域的规则。</span><span class="sxs-lookup"><span data-stu-id="f229e-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="f229e-121">考虑如何从应用程序中获取熟悉的代表对象，但要折上一些实际现实规则。</span><span class="sxs-lookup"><span data-stu-id="f229e-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="f229e-122">将产生幻数。</span><span class="sxs-lookup"><span data-stu-id="f229e-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="f229e-123">直观</span><span class="sxs-lookup"><span data-stu-id="f229e-123">Intuitive</span></span>

<span data-ttu-id="f229e-124">当你查看应用程序启动器时，启动你的应用程序的目的是非常明显，不会造成任何混淆。</span><span class="sxs-lookup"><span data-stu-id="f229e-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="f229e-125">例如，请确保您的启动器是您的应用程序的一个显而易见的代表，这不会对 Cliff 房子中的一 décor。</span><span class="sxs-lookup"><span data-stu-id="f229e-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="f229e-126">应用启动器应邀请人员触摸/选择。</span><span class="sxs-lookup"><span data-stu-id="f229e-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="f229e-127">![示例：全新备注3D 应用启动器](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f229e-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="f229e-128">*全新备注3D 应用启动器示例（虚拟应用）*</span><span class="sxs-lookup"><span data-stu-id="f229e-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="f229e-129">主比例</span><span class="sxs-lookup"><span data-stu-id="f229e-129">Home scale</span></span>

<span data-ttu-id="f229e-130">Cliff 房子中的三维应用启动器及其默认大小对于空间中的其他 "物理" 对象应该是有意义的。</span><span class="sxs-lookup"><span data-stu-id="f229e-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="f229e-131">如果将您的启动器置于附近（比如，房屋植物或某个家具），则应在家中、按大小进行调整。</span><span class="sxs-lookup"><span data-stu-id="f229e-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="f229e-132">很好的起点是查看它如何以30立方米为单位显示，但请记住，如果用户喜欢，可以增加或减少。</span><span class="sxs-lookup"><span data-stu-id="f229e-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="f229e-133">自己可以</span><span class="sxs-lookup"><span data-stu-id="f229e-133">Own-able</span></span>

<span data-ttu-id="f229e-134">应用启动器应感觉到某个人很高兴能够在他们的空间中使用。</span><span class="sxs-lookup"><span data-stu-id="f229e-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="f229e-135">它们几乎都是通过这些内容来处理的，因此启动器应喜欢用户认为是足以寻找并保留附近的内容。</span><span class="sxs-lookup"><span data-stu-id="f229e-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="f229e-136">![示例： Astro 扭曲3D 应用启动器](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f229e-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="f229e-137">*Astro 变形三维应用启动器示例（虚拟应用）*</span><span class="sxs-lookup"><span data-stu-id="f229e-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="f229e-138">识别</span><span class="sxs-lookup"><span data-stu-id="f229e-138">Recognizable</span></span>

<span data-ttu-id="f229e-139">你的3D 应用程序启动器应立即将 "你的应用程序" 的品牌表达为看到它的人。</span><span class="sxs-lookup"><span data-stu-id="f229e-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="f229e-140">如果应用中有星形或特别可识别的对象，我们建议将其作为设计的一个很大的组成部分。</span><span class="sxs-lookup"><span data-stu-id="f229e-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="f229e-141">在混合现实世界中，对象对用户的兴趣比单独的徽标要多。</span><span class="sxs-lookup"><span data-stu-id="f229e-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="f229e-142">可识别对象快速、清晰地传达品牌。</span><span class="sxs-lookup"><span data-stu-id="f229e-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="f229e-143">容量耗尽</span><span class="sxs-lookup"><span data-stu-id="f229e-143">Volumetric</span></span>

<span data-ttu-id="f229e-144">您的应用程序只需将徽标置于平整平面上，并一整天就会调用它。</span><span class="sxs-lookup"><span data-stu-id="f229e-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="f229e-145">您的启动器应类似于用户空间中令人兴奋的、三维的物理对象。</span><span class="sxs-lookup"><span data-stu-id="f229e-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="f229e-146">一种很好的方法是假设您的应用程序将在 Macy 的感恩节日醒目中有一个气球。</span><span class="sxs-lookup"><span data-stu-id="f229e-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="f229e-147">问问自己，究竟是什么人在街道下出现了什么呢？</span><span class="sxs-lookup"><span data-stu-id="f229e-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="f229e-148">所有查看角度看起来都很好？</span><span class="sxs-lookup"><span data-stu-id="f229e-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="f229e-149">仅 ![徽标](images/20171016-140436-mixedreality-640px.jpg)*徽标*</span><span class="sxs-lookup"><span data-stu-id="f229e-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f229e-150">![更可识别的字符](images/20171016-140557-mixedreality-640px.jpg)*更可识别字符*</span><span class="sxs-lookup"><span data-stu-id="f229e-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        <span data-ttu-id="f229e-151">![平面方法，而不是令人吃惊](images/20171016-155101-mixedreality-640px.jpg)*平面方法，而不是令人吃惊*</span><span class="sxs-lookup"><span data-stu-id="f229e-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f229e-152">![容量耗尽方法更好地展示您的应用程序](images/20171016-161407-mixedreality-640px.jpg)*容量耗尽方法更好地展示您的应用程序*</span><span class="sxs-lookup"><span data-stu-id="f229e-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="f229e-153">适用于三维模型的提示</span><span class="sxs-lookup"><span data-stu-id="f229e-153">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="f229e-154">最佳做法</span><span class="sxs-lookup"><span data-stu-id="f229e-154">Best practices</span></span>
* <span data-ttu-id="f229e-155">规划应用程序启动器的维度时，会针对大致的30cm 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="f229e-155">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="f229e-156">因此，1:1:1 大小的比率。</span><span class="sxs-lookup"><span data-stu-id="f229e-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="f229e-157">模型必须在10000多边形下。</span><span class="sxs-lookup"><span data-stu-id="f229e-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="f229e-158">详细了解三角形计数和详细级别（LODs）</span><span class="sxs-lookup"><span data-stu-id="f229e-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="f229e-159">如果可能，请在沉浸式耳机上测试。</span><span class="sxs-lookup"><span data-stu-id="f229e-159">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="f229e-160">在可能的情况下，将详细信息生成到模型的几何图形–不要依赖于纹理获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="f229e-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="f229e-161">生成 "水紧密型" 闭合几何。</span><span class="sxs-lookup"><span data-stu-id="f229e-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="f229e-162">没有在中建模的孔。</span><span class="sxs-lookup"><span data-stu-id="f229e-162">No holes that are not modeled in.</span></span>
* <span data-ttu-id="f229e-163">使用对象中的自然材料。</span><span class="sxs-lookup"><span data-stu-id="f229e-163">Use natural materials in your object.</span></span> <span data-ttu-id="f229e-164">想象一下在现实世界中手工制作。</span><span class="sxs-lookup"><span data-stu-id="f229e-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="f229e-165">请确保您的模型在不同的距离和大小上都能正常阅读。</span><span class="sxs-lookup"><span data-stu-id="f229e-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="f229e-166">模型准备就绪后，请阅读[导出资产的准则](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。</span><span class="sxs-lookup"><span data-stu-id="f229e-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="f229e-167">纹理](images/20171013-143334-mixedreality-640px.jpg) 中包含精细详细信息的 ![模型</span><span class="sxs-lookup"><span data-stu-id="f229e-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="f229e-168">*纹理中包含微妙细节的模型*</span><span class="sxs-lookup"><span data-stu-id="f229e-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="f229e-169">要避免的情况</span><span class="sxs-lookup"><span data-stu-id="f229e-169">What to avoid</span></span>
* <span data-ttu-id="f229e-170">不要使用高对比度详细信息或较小、繁忙的模式和纹理。</span><span class="sxs-lookup"><span data-stu-id="f229e-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="f229e-171">不要使用精简几何-它在某种程度上并不能很好地工作，并且不会产生错误。</span><span class="sxs-lookup"><span data-stu-id="f229e-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="f229e-172">不要让模型的一部分扩展到超过1:1:1 大小的比率。</span><span class="sxs-lookup"><span data-stu-id="f229e-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="f229e-173">它将创建缩放问题。</span><span class="sxs-lookup"><span data-stu-id="f229e-173">It will create scaling problems.</span></span>

<span data-ttu-id="f229e-174">![避免高对比度、小型繁忙模式](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f229e-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="f229e-175">*避免高对比度、小型、繁忙的模式*</span><span class="sxs-lookup"><span data-stu-id="f229e-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="f229e-176">如何处理类型</span><span class="sxs-lookup"><span data-stu-id="f229e-176">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="f229e-177">最佳做法</span><span class="sxs-lookup"><span data-stu-id="f229e-177">Best practices</span></span>
* <span data-ttu-id="f229e-178">建议你的类型包含大约1/3 的应用启动器（或更多）。</span><span class="sxs-lookup"><span data-stu-id="f229e-178">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="f229e-179">类型主要是使用户了解你的启动程序，事实上，启动程序很好，因为它非常重要。</span><span class="sxs-lookup"><span data-stu-id="f229e-179">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="f229e-180">避免使类型成为超级类型-尝试将其放在应用程序启动器核心维度的范围内（更多或更少）。</span><span class="sxs-lookup"><span data-stu-id="f229e-180">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="f229e-181">平面类型可正常运行，但请注意，在某些角度和某些环境下，可能难以查看。</span><span class="sxs-lookup"><span data-stu-id="f229e-181">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="f229e-182">您可以考虑将它放在一个实体对象或背景上，以帮助解决此情况。</span><span class="sxs-lookup"><span data-stu-id="f229e-182">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="f229e-183">将维度添加到您的类型非常适合3D。</span><span class="sxs-lookup"><span data-stu-id="f229e-183">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="f229e-184">将类型的两侧的底纹着色为不同、更暗的颜色可帮助提高可读性。</span><span class="sxs-lookup"><span data-stu-id="f229e-184">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="f229e-185">在不使用背景的情况下，不能从特定角度观看 ![平面类型，并且在某些环境中，*不能从特定角度和某些环境中查看](images/flattype-640px.png) 平面类型\*</span><span class="sxs-lookup"><span data-stu-id="f229e-185">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f229e-186">带有内置背景的 ![类型可以很好地](images/flattypeandbkg-640px.png)*使用内置背景的类型可以很好地工作*</span><span class="sxs-lookup"><span data-stu-id="f229e-186">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f229e-187">如果对边进行着色，则 ![拉伸类型可以很好地](images/20171016-160221-mixedreality-640px.jpg)*拉伸类型可以很好地工作*</span><span class="sxs-lookup"><span data-stu-id="f229e-187">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::


<span data-ttu-id="f229e-188">**键入工作的颜色**</span><span class="sxs-lookup"><span data-stu-id="f229e-188">**Type colors that work**</span></span>
* <span data-ttu-id="f229e-189">白色</span><span class="sxs-lookup"><span data-stu-id="f229e-189">White</span></span>
* <span data-ttu-id="f229e-190">黑线</span><span class="sxs-lookup"><span data-stu-id="f229e-190">Black</span></span>
* <span data-ttu-id="f229e-191">亮半饱和颜色</span><span class="sxs-lookup"><span data-stu-id="f229e-191">Bright semi-saturated color</span></span>

<span data-ttu-id="f229e-192">![类型。](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f229e-192">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="f229e-193">*键入工作的颜色*</span><span class="sxs-lookup"><span data-stu-id="f229e-193">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="f229e-194">要避免的情况</span><span class="sxs-lookup"><span data-stu-id="f229e-194">What to avoid</span></span>

<span data-ttu-id="f229e-195">**键入导致问题的颜色**</span><span class="sxs-lookup"><span data-stu-id="f229e-195">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="f229e-196">中声</span><span class="sxs-lookup"><span data-stu-id="f229e-196">Mid-tones</span></span>
* <span data-ttu-id="f229e-197">阶</span><span class="sxs-lookup"><span data-stu-id="f229e-197">Gray</span></span>
* <span data-ttu-id="f229e-198">过度饱和颜色或 desaturated 颜色</span><span class="sxs-lookup"><span data-stu-id="f229e-198">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="f229e-199">![类型导致问题的颜色。](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f229e-199">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="f229e-200">*键入导致问题的颜色*</span><span class="sxs-lookup"><span data-stu-id="f229e-200">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="f229e-201">照明</span><span class="sxs-lookup"><span data-stu-id="f229e-201">Lighting</span></span>

<span data-ttu-id="f229e-202">应用启动器的照明来自 Cliff 房子环境。</span><span class="sxs-lookup"><span data-stu-id="f229e-202">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="f229e-203">请确保在整个房子内的多个位置测试启动器，使其看起来很好。</span><span class="sxs-lookup"><span data-stu-id="f229e-203">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="f229e-204">好消息是，如果您按照本文档中的其他设计指南进行了，则您的启动器应该非常适合 Cliff 房子中的大多数照明。</span><span class="sxs-lookup"><span data-stu-id="f229e-204">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="f229e-205">很好地测试启动器在环境中的各种灯光上的外观，就是工作室、Media 房间、背面的任何位置和背面的 Patio （带有草地的具体区域）。</span><span class="sxs-lookup"><span data-stu-id="f229e-205">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="f229e-206">另一种好的测试是将它放在半轻和半阴影上，并查看其外观。</span><span class="sxs-lookup"><span data-stu-id="f229e-206">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="f229e-207">![确保启动器在灯光和阴影中都看起来很正常。](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f229e-207">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="f229e-208">*请确保启动程序在灯光和阴影中都看起来很好*</span><span class="sxs-lookup"><span data-stu-id="f229e-208">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="f229e-209">绘制</span><span class="sxs-lookup"><span data-stu-id="f229e-209">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="f229e-210">创作纹理</span><span class="sxs-lookup"><span data-stu-id="f229e-210">Authoring your textures</span></span>

<span data-ttu-id="f229e-211">三维应用启动器的结束格式为 glb 文件，该文件是使用 .PBR （基于物理的渲染）管道生成的。</span><span class="sxs-lookup"><span data-stu-id="f229e-211">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="f229e-212">这可能是一项棘手的过程-现在最好是使用技术音乐家（如果尚未这样做）。</span><span class="sxs-lookup"><span data-stu-id="f229e-212">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="f229e-213">如果你是无畏的 DIY，则在开始之前，请花时间[研究并了解 .pbr 术语](https://wiki.polycount.com/wiki/PBR)，在幕后，这将有助于你避免常见错误。</span><span class="sxs-lookup"><span data-stu-id="f229e-213">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="f229e-214">![示例：全新备注应用](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="f229e-214">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="f229e-215">*全新备注3D 应用启动器示例（虚拟应用）*</span><span class="sxs-lookup"><span data-stu-id="f229e-215">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="f229e-216">**推荐的创作工具**</span><span class="sxs-lookup"><span data-stu-id="f229e-216">**Recommended authoring tool**</span></span>

<span data-ttu-id="f229e-217">建议通过 Allegorithmic 使用[材料刷](https://www.allegorithmic.com/products/substance-painter)来创作最终文件。</span><span class="sxs-lookup"><span data-stu-id="f229e-217">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="f229e-218">如果你不熟悉在物质刷中创作 .PBR 着色器，请参阅以下[教程](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)。</span><span class="sxs-lookup"><span data-stu-id="f229e-218">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="f229e-219">（或者，如果你更熟悉其中的一个，则[Coat](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)或[Marmoset Toolbag](https://www.marmoset.co/toolbag/)也会起作用。）</span><span class="sxs-lookup"><span data-stu-id="f229e-219">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="f229e-220">最佳做法</span><span class="sxs-lookup"><span data-stu-id="f229e-220">Best practices</span></span>

* <span data-ttu-id="f229e-221">如果你的应用启动器对象是为 .PBR 编写的，则为 Cliff 房子环境转换该对象应该非常简单。</span><span class="sxs-lookup"><span data-stu-id="f229e-221">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="f229e-222">着色器应为金属/粗糙度工作流– Unreal .PBR 着色器是一个关闭的传真。</span><span class="sxs-lookup"><span data-stu-id="f229e-222">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="f229e-223">导出纹理时，请牢记[建议的纹理大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)。</span><span class="sxs-lookup"><span data-stu-id="f229e-223">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="f229e-224">请确保为实时照明生成对象，这意味着：</span><span class="sxs-lookup"><span data-stu-id="f229e-224">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="f229e-225">避免融入阴影-或绘制阴影</span><span class="sxs-lookup"><span data-stu-id="f229e-225">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="f229e-226">避免纹理中的融入光照</span><span class="sxs-lookup"><span data-stu-id="f229e-226">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="f229e-227">使用其中一个 .PBR 材料创作包获取为着色器生成的正确地图</span><span class="sxs-lookup"><span data-stu-id="f229e-227">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="f229e-228">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f229e-228">See also</span></span>

* [<span data-ttu-id="f229e-229">创建用于混合现实主页的3D 模型</span><span class="sxs-lookup"><span data-stu-id="f229e-229">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="f229e-230">实现 3D 应用启动器（UWP 应用）</span><span class="sxs-lookup"><span data-stu-id="f229e-230">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="f229e-231">实现 3D 应用启动器（Win32 应用）</span><span class="sxs-lookup"><span data-stu-id="f229e-231">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
