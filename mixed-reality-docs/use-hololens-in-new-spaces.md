---
title: 在新空间中使用 HoloLens
description: HoloLens 了解某个空间在一段时间内的外观。 用户可以通过在空间中以特定方式移动 HoloLens 来简化此过程。
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality, 设计, 空间映射, HoloLens, 表面重建, 网格, 头跟踪, 映射
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566016"
---
# <a name="use-hololens-in-new-spaces"></a><span data-ttu-id="4e7c0-105">在新空间中使用 HoloLens</span><span class="sxs-lookup"><span data-stu-id="4e7c0-105">Use HoloLens in New Spaces</span></span>

<span data-ttu-id="4e7c0-106">在用户四处移动空间时, HoloLens*映射*或了解有关其环境的信息。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-106">HoloLens *maps*, or learns information about, its environment as the user moves around a space.</span></span> <span data-ttu-id="4e7c0-107">随着时间的推移, HoloLens 会构建环境中已观察到的所有部件的*空间图*。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-107">Over time, the HoloLens builds up a *spatial map* of all parts of the environment that have been observed.</span></span> <span data-ttu-id="4e7c0-108">当观察到环境中的更改时, HoloLens 会更新该映射。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-108">HoloLens updates the map as changes in the environment are observed.</span></span> <span data-ttu-id="4e7c0-109">此扫描将在应用启动时自动保留。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-109">This scan will automatically persist between app launches.</span></span>

<span data-ttu-id="4e7c0-110">只要设备已打开, 并且用户已登录, HoloLens 就会创建和更新映射。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-110">HoloLens will create and update maps as long as the device is on and a user is logged in.</span></span> <span data-ttu-id="4e7c0-111">如果将设备放在一个空格上并将其戴上, 则设备将尝试映射该区域。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-111">If you hold or wear the device with the cameras pointed at a space, the device will try to map the area.</span></span> <span data-ttu-id="4e7c0-112">虽然 HoloLens 会在一段时间内自然地了解空间, 但仍有一些提示和技巧可以更快、更有效地映射空间。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-112">While the HoloLens will learn a space naturally over time, there are tips and tricks available to map the space faster and more efficiently.</span></span> 

<span data-ttu-id="4e7c0-113">如果你的 HoloLens 无法映射你的空间或无法进行校准, 你可以进入 "限制" 模式。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-113">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="4e7c0-114">在有限模式下, 你将无法在你的环境中放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-114">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="tips-and-tricks-for-mapping-spaces"></a><span data-ttu-id="4e7c0-115">用于映射空间的提示和技巧</span><span class="sxs-lookup"><span data-stu-id="4e7c0-115">Tips and tricks for mapping spaces</span></span>

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a><span data-ttu-id="4e7c0-116">请确保已为混合现实设置空间</span><span class="sxs-lookup"><span data-stu-id="4e7c0-116">Make sure the space is set up for mixed reality</span></span>

<span data-ttu-id="4e7c0-117">环境中的功能可能会使 HoloLens 难以解释空间。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-117">Features in an environment can make it difficult for the HoloLens to interpret a space.</span></span> <span data-ttu-id="4e7c0-118">轻型级别、空间中的材料、对象的布局以及更多内容都可以影响 HoloLens 映射区域的方式。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-118">Light levels, materials in the space, the layout of objects, and more can all affect how HoloLens maps an area.</span></span>

<span data-ttu-id="4e7c0-119">有关为 HoloLens 和其他混合现实设备设置空间的技巧, 请参阅[Hololens 环境注意事项](environment-considerations-for-hololens.md)。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-119">Tips for setting up your space for HoloLens and other mixed reality devices can be found in [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

### <a name="understand-the-scenarios-for-the-area"></a><span data-ttu-id="4e7c0-120">了解领域的方案</span><span class="sxs-lookup"><span data-stu-id="4e7c0-120">Understand the scenarios for the area</span></span>

<span data-ttu-id="4e7c0-121">务必花费最长的时间来使用 HoloLens, 以便映射相关并完成。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-121">It is important to spend the most time where you will be using the HoloLens so that the map is relevant and complete.</span></span> 

<span data-ttu-id="4e7c0-122">例如, 如果某一 HoloLens 用户方案涉及从点 A 移到点 B, 则会遍历该路径二到三次, 并在移动时查看所有方向。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-122">For example, if a user scenario for HoloLens involves moving from Point A to Point B, walk that path two to three times, looking in all directions as you move.</span></span> 

### <a name="walk-slowly-around-the-space"></a><span data-ttu-id="4e7c0-123">围绕空间进行缓慢遍历</span><span class="sxs-lookup"><span data-stu-id="4e7c0-123">Walk slowly around the space</span></span>

<span data-ttu-id="4e7c0-124">如果在该区域中进行的遍历过于迅速, 则很可能是因为 HoloLens 会丢失映射区域。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-124">If you walk too quickly around the area, it's likely that the HoloLens will miss mapping areas.</span></span> <span data-ttu-id="4e7c0-125">在空间上慢慢遍历, 每隔5-8 英尺停止, 以围绕您的环境。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-125">Walk slowly around the space, stopping every 5-8 feet to look around at your surroundings.</span></span>

<span data-ttu-id="4e7c0-126">平滑运动还有助于提高 HoloLens 地图 effeciently。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-126">Smooth movements also help the HoloLens map more effeciently.</span></span>

### <a name="look-in-all-directions"></a><span data-ttu-id="4e7c0-127">在所有方向上查找</span><span class="sxs-lookup"><span data-stu-id="4e7c0-127">Look in all directions</span></span>

<span data-ttu-id="4e7c0-128">如果你映射空间, 则会在每个点之间的相对位置提供额外的数据。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-128">Looking around as you map the space gives the HoloLens more data on where points are relative to each other.</span></span> 

<span data-ttu-id="4e7c0-129">例如, 如果不查找, 则 HoloLens 可能不知道房间中的天花板是哪个位置。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-129">If you don't look up, for example, the HoloLens may not know where the ceiling in a room is.</span></span> 

<span data-ttu-id="4e7c0-130">在映射空间时, 请不要忘记查看地面。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-130">Don't forget to look down at the floor as you map the space.</span></span>

### <a name="cover-key-areas-multiple-times"></a><span data-ttu-id="4e7c0-131">多次涵盖关键区域</span><span class="sxs-lookup"><span data-stu-id="4e7c0-131">Cover key areas multiple times</span></span>

<span data-ttu-id="4e7c0-132">多次移动某个区域将有助于选取你在第一个演练中可能缺少的功能。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-132">Moving through an area multiple times will help pick up features you may have missed on the first walkthrough.</span></span> <span data-ttu-id="4e7c0-133">尝试将某一区域遍历2到3次, 以生成理想的地图。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-133">Try traversing an area two to three times to build an ideal map.</span></span>

<span data-ttu-id="4e7c0-134">如果可能, 重复这些移动时, 请在一个方向上花时间浏览某个区域, 然后翻过来并向后翻一步。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-134">If possible, while repeating these movements, spend time walking through an area in one direction, then turn around and walk back the way you came.</span></span>

### <a name="take-your-time-mapping-the-area"></a><span data-ttu-id="4e7c0-135">花时间映射区域</span><span class="sxs-lookup"><span data-stu-id="4e7c0-135">Take your time mapping the area</span></span>

<span data-ttu-id="4e7c0-136">HoloLens 可能需要15到20分钟的时间才能完全映射并调整其自身环境。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-136">It can take between 15 and 20 minutes for the HoloLens to fully map and adjust itself to its surroundings.</span></span> <span data-ttu-id="4e7c0-137">如果你有一个空间来计划频繁使用 HoloLens, 那么, 在这段时间之前, 若要映射空间, 可能会导致以后出现问题。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-137">If you have a space in which you plan to use a HoloLens frequently, taking that time up front to map the space can prevent issues later on.</span></span> 

## <a name="possible-errors-in-the-spatial-map"></a><span data-ttu-id="4e7c0-138">空间映射中可能存在的错误</span><span class="sxs-lookup"><span data-stu-id="4e7c0-138">Possible errors in the spatial map</span></span>

<span data-ttu-id="4e7c0-139">空间映射数据中的错误分为以下三个类别之一:</span><span class="sxs-lookup"><span data-stu-id="4e7c0-139">Errors in spatial mapping data fall into one of three categories:</span></span>

* <span data-ttu-id="4e7c0-140">*洞*:空间映射数据中缺少实际的表面。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-140">*Holes*: Real-world surfaces are missing from the spatial mapping data.</span></span>
* <span data-ttu-id="4e7c0-141">*Hallucinations*:图面存在于现实世界中不存在的空间映射数据中。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-141">*Hallucinations*: Surfaces exist in the spatial mapping data that do not exist in the real world.</span></span>
* <span data-ttu-id="4e7c0-142">*Wormholes*:HoloLens "丢失" 空间映射的一部分, 这是因为它与实际不同。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-142">*Wormholes*: HoloLens 'loses' part of the spatial map by thinking it is in a different part of the map than it actually is.</span></span>
* <span data-ttu-id="4e7c0-143">*偏向*:空间映射数据中的图面与实际表面生成对齐或拉出。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-143">*Bias*: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.</span></span>

<span data-ttu-id="4e7c0-144">其中许多错误可以通过[删除全息影像](environment-considerations-for-hololens.md)并重新映射空间来减轻。</span><span class="sxs-lookup"><span data-stu-id="4e7c0-144">Many of these errors can be mitigated by [deleting your holograms](environment-considerations-for-hololens.md) and re-mapping the space.</span></span>