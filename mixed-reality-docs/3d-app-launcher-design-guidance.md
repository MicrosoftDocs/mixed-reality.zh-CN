---
title: 三维应用程序启动程序设计指南
description: 三维应用启动器是他们可以选择启动应用程序的用户的混合的现实房屋中的"物理"对象。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 三维应用程序启动程序、 沉浸式头戴式耳机、 实时的多维数据集
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590304"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="bf941-104">三维应用程序启动程序设计指南</span><span class="sxs-lookup"><span data-stu-id="bf941-104">3D app launcher design guidance</span></span>

<span data-ttu-id="bf941-105">放在 Windows Mixed Reality 沉浸式 (VR) 耳机上，输入的主页、 Windows Mixed Reality 可视化为房屋在由山脉和水包围 cliff (尽管您可以[选择其他环境，甚至创建您自己](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="bf941-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="bf941-106">在此空间内主页，用户可以随意排列和组织的三维对象和他们所关心任何需要的方式的应用。</span><span class="sxs-lookup"><span data-stu-id="bf941-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="bf941-107">一个**三维应用启动器**是在用户的"物理"对象的混合现实房屋，他们可以选择启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf941-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="bf941-108">![示例：浮动鸟的 3D 应用程序启动器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf941-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="bf941-109">*浮动鸟的 3D 应用程序启动器示例 （虚构应用程序）*</span><span class="sxs-lookup"><span data-stu-id="bf941-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="bf941-110">三维应用程序启动器创建过程</span><span class="sxs-lookup"><span data-stu-id="bf941-110">3D app launcher creation process</span></span>

<span data-ttu-id="bf941-111">有 3 个步骤创建的 3D 应用程序启动器：</span><span class="sxs-lookup"><span data-stu-id="bf941-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="bf941-112">设计和 concepting （详见本文）</span><span class="sxs-lookup"><span data-stu-id="bf941-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="bf941-113">建模和导出</span><span class="sxs-lookup"><span data-stu-id="bf941-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="bf941-114">将其集成到你的应用程序：</span><span class="sxs-lookup"><span data-stu-id="bf941-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="bf941-115">UWP 应用</span><span class="sxs-lookup"><span data-stu-id="bf941-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="bf941-116">Win32 应用</span><span class="sxs-lookup"><span data-stu-id="bf941-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="bf941-117">设计概念</span><span class="sxs-lookup"><span data-stu-id="bf941-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="bf941-118">太棒了，但熟悉</span><span class="sxs-lookup"><span data-stu-id="bf941-118">Fantastic yet familiar</span></span>

<span data-ttu-id="bf941-119">应用程序启动程序位于 Windows Mixed Reality 环境是一部分熟悉，一部分精巧/名工商管理学博士的办法。</span><span class="sxs-lookup"><span data-stu-id="bf941-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="bf941-120">最佳的启动器遵循这个世界中的规则。</span><span class="sxs-lookup"><span data-stu-id="bf941-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="bf941-121">将如何，您可以从你的应用，需要一个熟悉的、 有代表性的对象，但处理一些实际的现实的规则。</span><span class="sxs-lookup"><span data-stu-id="bf941-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="bf941-122">Magic 将导致。</span><span class="sxs-lookup"><span data-stu-id="bf941-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="bf941-123">直观</span><span class="sxs-lookup"><span data-stu-id="bf941-123">Intuitive</span></span>

<span data-ttu-id="bf941-124">当您查看应用程序启动程序时，其用途-若要启动你的应用-显然应该和不应造成任何混淆。</span><span class="sxs-lookup"><span data-stu-id="bf941-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="bf941-125">例如，请确保你启动器是您的应用程序不会混淆的一段 Cliff 住宅装潢明显足够的代表。</span><span class="sxs-lookup"><span data-stu-id="bf941-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="bf941-126">应用程序启动程序应邀请他人触摸/选择它。</span><span class="sxs-lookup"><span data-stu-id="bf941-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="bf941-127">![示例：全新注意三维应用程序启动程序](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf941-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="bf941-128">*全新注意的 3D 应用程序启动器示例 （虚构应用程序）*</span><span class="sxs-lookup"><span data-stu-id="bf941-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="bf941-129">家庭规模</span><span class="sxs-lookup"><span data-stu-id="bf941-129">Home scale</span></span>

<span data-ttu-id="bf941-130">三维应用启动器上实时 Cliff 住宅和其默认大小应意义与其他"物理"对象的空间中。</span><span class="sxs-lookup"><span data-stu-id="bf941-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="bf941-131">如果将应用启动器，说，房屋工厂或某些家具应感到在家里、 size-wise。</span><span class="sxs-lookup"><span data-stu-id="bf941-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="bf941-132">很好的起点是请参阅如何查看 30 三次方厘米，但请记住，用户可以缩放它向上或向下根据自己喜好。</span><span class="sxs-lookup"><span data-stu-id="bf941-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="bf941-133">可拥有的</span><span class="sxs-lookup"><span data-stu-id="bf941-133">Own-able</span></span>

<span data-ttu-id="bf941-134">应用程序启动程序应该感觉就像一个人会高兴能够在其空间中的对象。</span><span class="sxs-lookup"><span data-stu-id="bf941-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="bf941-135">它们将会几乎周围本身与这些内容，因此启动器应感觉像用户想法是不够理想，若要找出并保持附近。</span><span class="sxs-lookup"><span data-stu-id="bf941-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="bf941-136">![示例：太空式 Warp 的 3D 应用程序启动器](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf941-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="bf941-137">*太空式 Warp 的 3D 应用程序启动器示例 （虚构应用程序）*</span><span class="sxs-lookup"><span data-stu-id="bf941-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="bf941-138">可识别</span><span class="sxs-lookup"><span data-stu-id="bf941-138">Recognizable</span></span>

<span data-ttu-id="bf941-139">三维应用程序启动程序应立即表达人员看不到"应用程序的品牌"。</span><span class="sxs-lookup"><span data-stu-id="bf941-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="bf941-140">如果应用程序中有一个星型字符或尤其是可识别的对象，我们建议使用它作为你的设计的重要组成部分。</span><span class="sxs-lookup"><span data-stu-id="bf941-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="bf941-141">在混合的现实情况下，对象将从用户比只是一个单独的徽标绘制更值得关注。</span><span class="sxs-lookup"><span data-stu-id="bf941-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="bf941-142">快速且明确，可识别对象进行通信的品牌。</span><span class="sxs-lookup"><span data-stu-id="bf941-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="bf941-143">容量耗尽</span><span class="sxs-lookup"><span data-stu-id="bf941-143">Volumetric</span></span>

<span data-ttu-id="bf941-144">您应用值得试用而不仅仅平面平面上将你的徽标和一周。</span><span class="sxs-lookup"><span data-stu-id="bf941-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="bf941-145">在启动程序应该感觉就像用户的空间中的令人兴奋、 3D、 物理对象。</span><span class="sxs-lookup"><span data-stu-id="bf941-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="bf941-146">一个不错的方法是假设您的应用程序将要 Macy 感恩节天入微中有一个气球。</span><span class="sxs-lookup"><span data-stu-id="bf941-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="bf941-147">问问自己，什么会真正 wow 人在其传入后在街？</span><span class="sxs-lookup"><span data-stu-id="bf941-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="bf941-148">什么从所有的查看角度看很好？</span><span class="sxs-lookup"><span data-stu-id="bf941-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="bf941-149">很好的三维模型的提示</span><span class="sxs-lookup"><span data-stu-id="bf941-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="bf941-150">最佳做法</span><span class="sxs-lookup"><span data-stu-id="bf941-150">Best practices</span></span>
* <span data-ttu-id="bf941-151">在规划应用程序启动程序的维度，请给大约为 30 cm 多维数据集。</span><span class="sxs-lookup"><span data-stu-id="bf941-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="bf941-152">因此，1:1 对 1 的大小比率。</span><span class="sxs-lookup"><span data-stu-id="bf941-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="bf941-153">模型必须是 10,000 多边形。</span><span class="sxs-lookup"><span data-stu-id="bf941-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="bf941-154">了解有关三角形计数和级别 (Lod) 的详细信息的详细信息</span><span class="sxs-lookup"><span data-stu-id="bf941-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="bf941-155">如有可能沉浸式头戴式上进行测试。</span><span class="sxs-lookup"><span data-stu-id="bf941-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="bf941-156">构建到模型的几何图形的详细信息，在可能的情况 – 不要依赖于纹理的详细信息。</span><span class="sxs-lookup"><span data-stu-id="bf941-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="bf941-157">生成"water 紧密"关闭几何图形。</span><span class="sxs-lookup"><span data-stu-id="bf941-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="bf941-158">未建模中没有漏洞。</span><span class="sxs-lookup"><span data-stu-id="bf941-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="bf941-159">在您的对象中使用自然的材料。</span><span class="sxs-lookup"><span data-stu-id="bf941-159">Use natural materials in your object.</span></span> <span data-ttu-id="bf941-160">想象一下在现实生活中编写。</span><span class="sxs-lookup"><span data-stu-id="bf941-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="bf941-161">请确保您的模型读取在不同距离和大小。</span><span class="sxs-lookup"><span data-stu-id="bf941-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="bf941-162">当模型准备就绪，读取[导出资产准则](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。</span><span class="sxs-lookup"><span data-stu-id="bf941-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="bf941-163">![具有细节纹理中的模型](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf941-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="bf941-164">*具有细节纹理中的模型*</span><span class="sxs-lookup"><span data-stu-id="bf941-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="bf941-165">要避免的问题</span><span class="sxs-lookup"><span data-stu-id="bf941-165">What to avoid</span></span>
* <span data-ttu-id="bf941-166">不要使用高对比度的详细信息或小忙的模式和纹理。</span><span class="sxs-lookup"><span data-stu-id="bf941-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="bf941-167">不要使用精简的几何图形 – 它不会工作在距离，并且别名错误。</span><span class="sxs-lookup"><span data-stu-id="bf941-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="bf941-168">不要让扩展模型的部分过多超出 1:1 对 1 的大小比率。</span><span class="sxs-lookup"><span data-stu-id="bf941-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="bf941-169">它将创建缩放问题。</span><span class="sxs-lookup"><span data-stu-id="bf941-169">It will create scaling problems.</span></span>

<span data-ttu-id="bf941-170">![避免高对比度、 小忙模式](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf941-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="bf941-171">*避免高对比度、 小型、 忙模式*</span><span class="sxs-lookup"><span data-stu-id="bf941-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="bf941-172">如何处理类型</span><span class="sxs-lookup"><span data-stu-id="bf941-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="bf941-173">最佳做法</span><span class="sxs-lookup"><span data-stu-id="bf941-173">Best practices</span></span>
* <span data-ttu-id="bf941-174">我们建议你的类型包括大约 1/3 的应用程序启动程序 （或多个）。</span><span class="sxs-lookup"><span data-stu-id="bf941-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="bf941-175">类型为可让人们了解应用启动器中这一事实，因此它很好的如果它是非常重大的启动是重点。</span><span class="sxs-lookup"><span data-stu-id="bf941-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="bf941-176">避免创建非常宽的类型 – 尝试使其保持范围内的应用启动器上核心维度 （增加或减少）。</span><span class="sxs-lookup"><span data-stu-id="bf941-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="bf941-177">平面类型可以起作用，但请注意，可能难以查看从特定的角度和在某些环境中。</span><span class="sxs-lookup"><span data-stu-id="bf941-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="bf941-178">您可以考虑将其放可靠对象或为帮助实现此其后的背景。</span><span class="sxs-lookup"><span data-stu-id="bf941-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="bf941-179">添加到你的类型的维度感觉很好以三维形式。</span><span class="sxs-lookup"><span data-stu-id="bf941-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="bf941-180">明暗度类型的方面一种不同的深颜色可帮助提高可读性。</span><span class="sxs-lookup"><span data-stu-id="bf941-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


<span data-ttu-id="bf941-181">**工作的类型颜色**</span><span class="sxs-lookup"><span data-stu-id="bf941-181">**Type colors that work**</span></span>
* <span data-ttu-id="bf941-182">白色</span><span class="sxs-lookup"><span data-stu-id="bf941-182">White</span></span>
* <span data-ttu-id="bf941-183">黑色</span><span class="sxs-lookup"><span data-stu-id="bf941-183">Black</span></span>
* <span data-ttu-id="bf941-184">半饱和的浅色</span><span class="sxs-lookup"><span data-stu-id="bf941-184">Bright semi-saturated color</span></span>

<span data-ttu-id="bf941-185">![工作的类型颜色。](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf941-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="bf941-186">*工作的类型颜色*</span><span class="sxs-lookup"><span data-stu-id="bf941-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="bf941-187">要避免的问题</span><span class="sxs-lookup"><span data-stu-id="bf941-187">What to avoid</span></span>

<span data-ttu-id="bf941-188">**会造成问题的类型颜色**</span><span class="sxs-lookup"><span data-stu-id="bf941-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="bf941-189">中间色调</span><span class="sxs-lookup"><span data-stu-id="bf941-189">Mid-tones</span></span>
* <span data-ttu-id="bf941-190">灰色</span><span class="sxs-lookup"><span data-stu-id="bf941-190">Gray</span></span>
* <span data-ttu-id="bf941-191">过度饱和的颜色或去除饱和度的颜色</span><span class="sxs-lookup"><span data-stu-id="bf941-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="bf941-192">![会造成问题的类型颜色。](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf941-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="bf941-193">*会造成问题的类型颜色*</span><span class="sxs-lookup"><span data-stu-id="bf941-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="bf941-194">照明</span><span class="sxs-lookup"><span data-stu-id="bf941-194">Lighting</span></span>

<span data-ttu-id="bf941-195">为应用程序启动程序照明来自 Cliff 房屋环境。</span><span class="sxs-lookup"><span data-stu-id="bf941-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="bf941-196">请确保在整个房屋的多个位置测试你启动程序，以便它看起来不错中光和阴影。</span><span class="sxs-lookup"><span data-stu-id="bf941-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="bf941-197">好消息是，如果已按照本文档中的其他设计指南，你启动器应该非常顺利 Cliff 房屋中大多数照明。</span><span class="sxs-lookup"><span data-stu-id="bf941-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="bf941-198">若要测试如何在各种系统正常运行的环境中查找你启动器可作为比较好 Studio 中，媒体文件室，任意位置外部的回阳台使用 （与在草坪具体区域）。</span><span class="sxs-lookup"><span data-stu-id="bf941-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="bf941-199">另一个很好的测试是将其放入半光和一半阴影并查看其外观。</span><span class="sxs-lookup"><span data-stu-id="bf941-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="bf941-200">![请确保您启动程序看起来不错中光和阴影。](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bf941-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="bf941-201">*请确保您启动程序看起来不错中光和阴影*</span><span class="sxs-lookup"><span data-stu-id="bf941-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="bf941-202">纹理</span><span class="sxs-lookup"><span data-stu-id="bf941-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="bf941-203">创作你的纹理</span><span class="sxs-lookup"><span data-stu-id="bf941-203">Authoring your textures</span></span>

<span data-ttu-id="bf941-204">在三维应用程序启动程序的最终格式将.glb 文件，它由使用 PBR （以物理方式基于呈现） 管道。</span><span class="sxs-lookup"><span data-stu-id="bf941-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="bf941-205">这可以是一个困难的过程-现在是如果你尚未采用技术艺术家的好时机。</span><span class="sxs-lookup"><span data-stu-id="bf941-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="bf941-206">如果你是勇敢 DIY-嗯，花费的时间[研究和了解 PBR 术语](http://wiki.polycount.com/wiki/PBR)发生了什么情况实质上在开始之前将帮助你避免常见错误。</span><span class="sxs-lookup"><span data-stu-id="bf941-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="bf941-207">![示例：新的笔记应用程序](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="bf941-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="bf941-208">*全新注意的 3D 应用程序启动器示例 （虚构应用程序）*</span><span class="sxs-lookup"><span data-stu-id="bf941-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="bf941-209">**建议使用创作工具**</span><span class="sxs-lookup"><span data-stu-id="bf941-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="bf941-210">我们建议使用[物质刷](https://www.allegorithmic.com/products/substance-painter)通过 Allegorithmic 编写最终文件。</span><span class="sxs-lookup"><span data-stu-id="bf941-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="bf941-211">如果您不熟悉创作中物质刷，此处的 PBR 着色[教程](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)。</span><span class="sxs-lookup"><span data-stu-id="bf941-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="bf941-212">(或者[3D Coat](https://3dcoat.com/home/)， [Quixel 套件 2](https://quixel.se/suite2/)，或[Marmoset Toolbag](https://www.marmoset.co/toolbag/)也有效，如果您更熟悉使用其中一种。)</span><span class="sxs-lookup"><span data-stu-id="bf941-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="bf941-213">最佳做法</span><span class="sxs-lookup"><span data-stu-id="bf941-213">Best practices</span></span>

* <span data-ttu-id="bf941-214">如果您的应用启动器对象为 PBR 创作的则应很简单地将其转换为 Cliff 房屋环境。</span><span class="sxs-lookup"><span data-stu-id="bf941-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="bf941-215">我们的着色器应为裸机/粗糙度的工作流 – Unreal PBR 着色器关闭传真。</span><span class="sxs-lookup"><span data-stu-id="bf941-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="bf941-216">导出你的纹理保持[建议的纹理大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)记住。</span><span class="sxs-lookup"><span data-stu-id="bf941-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="bf941-217">请确保生成您实时光线的对象，这意味着：</span><span class="sxs-lookup"><span data-stu-id="bf941-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="bf941-218">避免甜的阴影 – 或绘制的阴影</span><span class="sxs-lookup"><span data-stu-id="bf941-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="bf941-219">避免纹理中的生成的照明</span><span class="sxs-lookup"><span data-stu-id="bf941-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="bf941-220">使用创作包 PBR 材料之一来获取正确的映射生成我们的着色器</span><span class="sxs-lookup"><span data-stu-id="bf941-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="bf941-221">请参阅</span><span class="sxs-lookup"><span data-stu-id="bf941-221">See also</span></span>

* [<span data-ttu-id="bf941-222">创建主混合现实中使用三维模型</span><span class="sxs-lookup"><span data-stu-id="bf941-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="bf941-223">实现的 3D 应用程序启动器 （UWP 应用）</span><span class="sxs-lookup"><span data-stu-id="bf941-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="bf941-224">实现的 3D 应用程序启动器 （Win32 应用）</span><span class="sxs-lookup"><span data-stu-id="bf941-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
