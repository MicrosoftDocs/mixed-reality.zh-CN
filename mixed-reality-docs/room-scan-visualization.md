---
title: 房间扫描可视化
description: 需要空间映射数据的应用程序依赖于设备在一段时间内和跨会话自动收集此数据, 因为用户浏览其环境中的设备处于活动状态。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 应用模式, 设计, HoloLens, 房间扫描, 空间映射, 表面重建, 网格
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829913"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="53e7c-104">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="53e7c-104">Room scan visualization</span></span>

<span data-ttu-id="53e7c-105">需要空间映射数据的应用程序依赖于设备在一段时间内和跨会话自动收集此数据, 因为用户浏览其环境中的设备处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="53e7c-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="53e7c-106">此数据的完整性和质量取决于多个因素, 包括用户的探索量、从浏览开始起经过的时间, 以及从设备扫描区域以来是否移动了家具和门等对象。</span><span class="sxs-lookup"><span data-stu-id="53e7c-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="53e7c-107">为了确保有用的空间映射数据, 应用程序开发人员有多种选择:</span><span class="sxs-lookup"><span data-stu-id="53e7c-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="53e7c-108">依赖于可能已收集的内容。</span><span class="sxs-lookup"><span data-stu-id="53e7c-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="53e7c-109">此数据最初可能是不完整的。</span><span class="sxs-lookup"><span data-stu-id="53e7c-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="53e7c-110">要求用户使用布隆手势进入 Windows Mixed Reality 主页, 并浏览他们希望用于体验的领域。</span><span class="sxs-lookup"><span data-stu-id="53e7c-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="53e7c-111">他们可以使用分流来确认设备是否知道所有必要的区域。</span><span class="sxs-lookup"><span data-stu-id="53e7c-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="53e7c-112">在自己的应用程序中生成自定义浏览体验。</span><span class="sxs-lookup"><span data-stu-id="53e7c-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="53e7c-113">请注意, 在所有这些情况下, 在浏览过程中收集的实际数据都由系统存储, 并且应用程序无需执行此操作。</span><span class="sxs-lookup"><span data-stu-id="53e7c-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="53e7c-114">设备支持</span><span class="sxs-lookup"><span data-stu-id="53e7c-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="53e7c-115"><strong>功能</strong></span><span class="sxs-lookup"><span data-stu-id="53e7c-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="53e7c-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="53e7c-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="53e7c-117"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="53e7c-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="53e7c-118">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="53e7c-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="53e7c-119">✔️</span><span class="sxs-lookup"><span data-stu-id="53e7c-119">✔️</span></span></td>
        <td><span data-ttu-id="53e7c-120">❌</span><span class="sxs-lookup"><span data-stu-id="53e7c-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="53e7c-121">构建自定义扫描体验</span><span class="sxs-lookup"><span data-stu-id="53e7c-121">Building a custom scanning experience</span></span>

<span data-ttu-id="53e7c-122">应用程序可以决定在体验开始时对空间映射数据进行分析, 判断他们是否希望用户执行额外的步骤来提高其完整性和质量。</span><span class="sxs-lookup"><span data-stu-id="53e7c-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="53e7c-123">如果分析表明质量应该提高, 开发人员应提供一种可视化对象, 使其在世界上叠加以指示:</span><span class="sxs-lookup"><span data-stu-id="53e7c-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="53e7c-124">用户附近的用户总数需要成为体验的一部分</span><span class="sxs-lookup"><span data-stu-id="53e7c-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="53e7c-125">用户应在何处着手改善数据</span><span class="sxs-lookup"><span data-stu-id="53e7c-125">Where the user should go to improve data</span></span>

<span data-ttu-id="53e7c-126">用户不知道什么是 "良好" 扫描。</span><span class="sxs-lookup"><span data-stu-id="53e7c-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="53e7c-127">如果要求评估扫描– flatness、与实际墙壁的距离等, 则需要显示或告知要查找的内容。开发人员应实现一个反馈循环, 其中包括在扫描或浏览阶段刷新空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="53e7c-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="53e7c-128">在许多情况下, 最好告诉用户需要执行的操作 (例如, 查看家具上的天花板), 以便获得必要的扫描质量。</span><span class="sxs-lookup"><span data-stu-id="53e7c-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="53e7c-129">缓存与连续空间映射</span><span class="sxs-lookup"><span data-stu-id="53e7c-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="53e7c-130">空间映射数据是最繁重的数据源应用程序可以使用的数据源。</span><span class="sxs-lookup"><span data-stu-id="53e7c-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="53e7c-131">若要避免性能问题 (如丢弃的帧或断断续续), 应仔细地使用此数据。</span><span class="sxs-lookup"><span data-stu-id="53e7c-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="53e7c-132">体验过程中的活动扫描可能既有利也有不利, 开发人员需要根据经验决定要使用哪种方法。</span><span class="sxs-lookup"><span data-stu-id="53e7c-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="53e7c-133">缓存空间映射</span><span class="sxs-lookup"><span data-stu-id="53e7c-133">Cached spatial mapping</span></span>

<span data-ttu-id="53e7c-134">对于缓存空间映射, 应用程序通常会拍摄空间映射数据的快照, 并在体验期间使用此快照。</span><span class="sxs-lookup"><span data-stu-id="53e7c-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="53e7c-135">**优势**</span><span class="sxs-lookup"><span data-stu-id="53e7c-135">**Benefits**</span></span>
* <span data-ttu-id="53e7c-136">降低了系统的系统开销, 同时体验运行, 从而提高了性能、散热和 cpu 性能。</span><span class="sxs-lookup"><span data-stu-id="53e7c-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="53e7c-137">由于空间数据中的更改不会中断, 因此更简单的主要体验实现。</span><span class="sxs-lookup"><span data-stu-id="53e7c-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="53e7c-138">对于物理学、图形和其他用途的任何 post 处理空间数据, 一次只需一次。</span><span class="sxs-lookup"><span data-stu-id="53e7c-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="53e7c-139">**弊端**</span><span class="sxs-lookup"><span data-stu-id="53e7c-139">**Drawbacks**</span></span>
* <span data-ttu-id="53e7c-140">实际对象或人员的移动不会由缓存数据反映。</span><span class="sxs-lookup"><span data-stu-id="53e7c-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="53e7c-141">例如</span><span class="sxs-lookup"><span data-stu-id="53e7c-141">E.g.</span></span> <span data-ttu-id="53e7c-142">应用程序可能会将门视为在实际关闭时打开。</span><span class="sxs-lookup"><span data-stu-id="53e7c-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="53e7c-143">可能会有更多的应用程序内存来维护数据的缓存版本。</span><span class="sxs-lookup"><span data-stu-id="53e7c-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="53e7c-144">此方法的一个很好的例子是受控环境或表顶级游戏。</span><span class="sxs-lookup"><span data-stu-id="53e7c-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="53e7c-145">连续空间映射</span><span class="sxs-lookup"><span data-stu-id="53e7c-145">Continuous spatial mapping</span></span>

<span data-ttu-id="53e7c-146">某些应用程序可能依赖于继续扫描以刷新空间映射数据。</span><span class="sxs-lookup"><span data-stu-id="53e7c-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="53e7c-147">**优势**</span><span class="sxs-lookup"><span data-stu-id="53e7c-147">**Benefits**</span></span>
* <span data-ttu-id="53e7c-148">无需在应用程序中提前构建单独的扫描或浏览体验。</span><span class="sxs-lookup"><span data-stu-id="53e7c-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="53e7c-149">尽管有一些延迟, 但现实世界对象的移动可能会反映出来。</span><span class="sxs-lookup"><span data-stu-id="53e7c-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="53e7c-150">**弊端**</span><span class="sxs-lookup"><span data-stu-id="53e7c-150">**Drawbacks**</span></span>
* <span data-ttu-id="53e7c-151">实现主要体验的复杂性更高。</span><span class="sxs-lookup"><span data-stu-id="53e7c-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="53e7c-152">由于需要以增量方式引入这些系统的更改, 因此, 对图形或物理的额外处理可能会造成开销。</span><span class="sxs-lookup"><span data-stu-id="53e7c-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="53e7c-153">高功率、热量和 CPU 影响。</span><span class="sxs-lookup"><span data-stu-id="53e7c-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="53e7c-154">此方法的一种很好的情况是, 全息影像应与移动对象进行交互, 例如, 地面上驱动器的全息汽车可能需要正确地从门中向下移动, 具体取决于它是打开还是关闭。</span><span class="sxs-lookup"><span data-stu-id="53e7c-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="53e7c-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="53e7c-155">See also</span></span>
* [<span data-ttu-id="53e7c-156">空间映射设计</span><span class="sxs-lookup"><span data-stu-id="53e7c-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="53e7c-157">坐标系统</span><span class="sxs-lookup"><span data-stu-id="53e7c-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="53e7c-158">空间音效设计</span><span class="sxs-lookup"><span data-stu-id="53e7c-158">Spatial sound design</span></span>](spatial-sound-design.md)
