---
title: 聊天室扫描可视化效果
description: 需要空间映射数据的应用程序依赖于设备要自动随着时间的推移收集这些数据，并跨会话作为用户与设备 active 探讨其环境。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，应用模式、 设计、 HoloLens、 聊天室扫描，空间映射，图面重建，网格
ms.openlocfilehash: 8ffde9d476e25016f986321377dce8125ee3a596
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592977"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="64036-104">聊天室扫描可视化效果</span><span class="sxs-lookup"><span data-stu-id="64036-104">Room scan visualization</span></span>

<span data-ttu-id="64036-105">需要空间映射数据的应用程序依赖于设备要自动随着时间的推移收集这些数据，并跨会话作为用户与设备 active 探讨其环境。</span><span class="sxs-lookup"><span data-stu-id="64036-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="64036-106">完整性和此数据的质量取决于多种因素，包括用户已经进行了数量、 探索以来经过多少时间和家具和门之类的对象是否具有移动设备扫描区域之后。</span><span class="sxs-lookup"><span data-stu-id="64036-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="64036-107">若要确保有用空间映射数据，应用程序开发人员有几个选项：</span><span class="sxs-lookup"><span data-stu-id="64036-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="64036-108">依赖于哪些有可能已收集了。</span><span class="sxs-lookup"><span data-stu-id="64036-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="64036-109">此数据最初可能不完整。</span><span class="sxs-lookup"><span data-stu-id="64036-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="64036-110">要求用户使用布隆手势获取 Windows Mixed reality 主页，然后浏览他们想要使用体验的区域。</span><span class="sxs-lookup"><span data-stu-id="64036-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="64036-111">他们可以使用以无线方式点击以确认所有必要的区域称为到设备。</span><span class="sxs-lookup"><span data-stu-id="64036-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="64036-112">构建他们自己的应用程序中自定义的浏览体验。</span><span class="sxs-lookup"><span data-stu-id="64036-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="64036-113">请注意，在这些情况下探索过程中收集的实际数据存储系统应用程序不需要执行此操作。</span><span class="sxs-lookup"><span data-stu-id="64036-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="64036-114">设备支持</span><span class="sxs-lookup"><span data-stu-id="64036-114">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="64036-115">功能</span><span class="sxs-lookup"><span data-stu-id="64036-115">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="64036-116"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="64036-116"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="64036-117"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="64036-117"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="64036-118">聊天室扫描可视化效果</span><span class="sxs-lookup"><span data-stu-id="64036-118">Room scan visualization</span></span></td><td style="text-align: center;"> <span data-ttu-id="64036-119">✔️</span><span class="sxs-lookup"><span data-stu-id="64036-119">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="64036-120">构建自定义扫描体验</span><span class="sxs-lookup"><span data-stu-id="64036-120">Building a custom scanning experience</span></span>

<span data-ttu-id="64036-121">应用程序可能会决定分析空间映射数据丰富的经验来判断是否需要用户执行其他步骤来改进其完整性和质量的开头。</span><span class="sxs-lookup"><span data-stu-id="64036-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="64036-122">如果分析指示应该改进质量，开发人员应提供一个视觉对象用于指示对世界：</span><span class="sxs-lookup"><span data-stu-id="64036-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="64036-123">多少用户邻近范围中的总卷必须是体验的一部分</span><span class="sxs-lookup"><span data-stu-id="64036-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="64036-124">用户应发送到何处以提高数据</span><span class="sxs-lookup"><span data-stu-id="64036-124">Where the user should go to improve data</span></span>

<span data-ttu-id="64036-125">用户不知道是什么使"良好"扫描。</span><span class="sxs-lookup"><span data-stu-id="64036-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="64036-126">他们需要显示或告诉查找在被要求来评估扫描 – 展平、 从实际墙壁、 距离等。开发人员应实现反馈循环，包括扫描或探索阶段刷新空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="64036-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="64036-127">在许多情况下，可能是最好地告知用户他们需要执行操作 （例如回顾上限，在查找家具），以获取必要的扫描质量。</span><span class="sxs-lookup"><span data-stu-id="64036-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="64036-128">缓存而不是连续空间映射</span><span class="sxs-lookup"><span data-stu-id="64036-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="64036-129">空间映射数据是数据源的应用可以使用的最大量权重。</span><span class="sxs-lookup"><span data-stu-id="64036-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="64036-130">为了避免性能问题，例如丢弃的帧或断断续续的情况，使用此数据时应谨慎。</span><span class="sxs-lookup"><span data-stu-id="64036-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="64036-131">Active 扫描体验期间可以有益或造成不利影响和开发人员将需要决定要使用的方法根据的体验。</span><span class="sxs-lookup"><span data-stu-id="64036-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="64036-132">缓存空间的映射</span><span class="sxs-lookup"><span data-stu-id="64036-132">Cached spatial mapping</span></span>

<span data-ttu-id="64036-133">在缓存空间映射的情况下应用程序通常将空间映射数据的快照，并体验的持续时间内使用此快照。</span><span class="sxs-lookup"><span data-stu-id="64036-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="64036-134">**优势**</span><span class="sxs-lookup"><span data-stu-id="64036-134">**Benefits**</span></span>
* <span data-ttu-id="64036-135">减少开销，在系统上时体验到巨大的电源，散热运行前导和 cpu 性能的改善。</span><span class="sxs-lookup"><span data-stu-id="64036-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="64036-136">因为空间数据中的更改不中断的主要体验更简单实现。</span><span class="sxs-lookup"><span data-stu-id="64036-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="64036-137">将单个成本上的空间数据的物理特性、 图形和其他用途的任何后续处理一次。</span><span class="sxs-lookup"><span data-stu-id="64036-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="64036-138">**缺点**</span><span class="sxs-lookup"><span data-stu-id="64036-138">**Drawbacks**</span></span>
* <span data-ttu-id="64036-139">缓存的数据不反映实际对象或人员的移动。</span><span class="sxs-lookup"><span data-stu-id="64036-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="64036-140">例如</span><span class="sxs-lookup"><span data-stu-id="64036-140">E.g.</span></span> <span data-ttu-id="64036-141">应用程序可能会考虑门打开时实际立即关闭。</span><span class="sxs-lookup"><span data-stu-id="64036-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="64036-142">可能的其他应用程序内存以维护数据的缓存的版本。</span><span class="sxs-lookup"><span data-stu-id="64036-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="64036-143">理想的情形，此方法是在受控的环境或表顶部游戏。</span><span class="sxs-lookup"><span data-stu-id="64036-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="64036-144">连续空间映射</span><span class="sxs-lookup"><span data-stu-id="64036-144">Continuous spatial mapping</span></span>

<span data-ttu-id="64036-145">某些应用程序可能依赖于在继续扫描，以刷新空间映射的数据。</span><span class="sxs-lookup"><span data-stu-id="64036-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="64036-146">**优势**</span><span class="sxs-lookup"><span data-stu-id="64036-146">**Benefits**</span></span>
* <span data-ttu-id="64036-147">不需要单独扫描或浏览体验提前在应用程序中生成。</span><span class="sxs-lookup"><span data-stu-id="64036-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="64036-148">尽管有一些延迟，游戏时，可以反映实际对象的移动。</span><span class="sxs-lookup"><span data-stu-id="64036-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="64036-149">**缺点**</span><span class="sxs-lookup"><span data-stu-id="64036-149">**Drawbacks**</span></span>
* <span data-ttu-id="64036-150">在实现中的主要体验的更高版本复杂性。</span><span class="sxs-lookup"><span data-stu-id="64036-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="64036-151">潜在的图形或物理作为更改需要这些系统以增量方式引入的附加处理开销。</span><span class="sxs-lookup"><span data-stu-id="64036-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="64036-152">更高的能力、 温度和 CPU 的影响。</span><span class="sxs-lookup"><span data-stu-id="64036-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="64036-153">理想的情形，此方法是一个预期全息与移动对象，例如在地板上的驱动器可能想要正确地遇到具体取决于是否打开或关闭门 holographic 汽车进行交互。</span><span class="sxs-lookup"><span data-stu-id="64036-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="64036-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="64036-154">See also</span></span>
* [<span data-ttu-id="64036-155">空间映射设计</span><span class="sxs-lookup"><span data-stu-id="64036-155">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="64036-156">坐标系统</span><span class="sxs-lookup"><span data-stu-id="64036-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="64036-157">空间合理的设计</span><span class="sxs-lookup"><span data-stu-id="64036-157">Spatial sound design</span></span>](spatial-sound-design.md)
