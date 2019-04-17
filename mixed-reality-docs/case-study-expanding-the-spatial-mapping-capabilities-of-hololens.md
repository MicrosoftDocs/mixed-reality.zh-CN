---
title: 案例研究-扩展 HoloLens 的空间映射功能
description: 当创建适用于 Microsoft HoloLens 我们第一个应用，我们急于想看到只是程度我们无法在设备上按空间映射的边界。
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality HoloLens，空间映射
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592552"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="9fa49-104">案例研究-扩展 HoloLens 的空间映射功能</span><span class="sxs-lookup"><span data-stu-id="9fa49-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="9fa49-105">当创建适用于 Microsoft HoloLens 我们第一个应用，我们急于想看到只是程度我们无法在设备上按空间映射的边界。</span><span class="sxs-lookup"><span data-stu-id="9fa49-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="9fa49-106">Jeff Evertt，Microsoft Studios 的软件工程师介绍了如何一项新技术已开发出更好地控制如何在用户的实际环境中放置全息的需要。</span><span class="sxs-lookup"><span data-stu-id="9fa49-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="9fa49-107">观看视频</span><span class="sxs-lookup"><span data-stu-id="9fa49-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="9fa49-108">超出空间映射</span><span class="sxs-lookup"><span data-stu-id="9fa49-108">Beyond spatial mapping</span></span>

<span data-ttu-id="9fa49-109">虽然我们正在处理[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)并[Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)、 两个 HoloLens 的第一个游戏，我们发现我们的执行过程放置全息现实生活中，我们需要更高的级别有关用户的环境的了解。</span><span class="sxs-lookup"><span data-stu-id="9fa49-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="9fa49-110">每个游戏都有其自己特定位置的要求：在段落中，例如，我们希望能够区分不同的图面 — 例如 floor 或表，可以将线索置于相关位置。</span><span class="sxs-lookup"><span data-stu-id="9fa49-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="9fa49-111">我们还想要能够识别，坐下来的栩栩如生 holographic 字符无法如 couch 或椅子的图面。</span><span class="sxs-lookup"><span data-stu-id="9fa49-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="9fa49-112">在 Young Conker 我们想 Conker 和他的对手能够引发图面玩家的房间中用作平台。</span><span class="sxs-lookup"><span data-stu-id="9fa49-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="9fa49-113">[Asobo Studios](http://www.asobostudio.com/index.html)，这些游戏，我们开发合作伙伴直接针对遇到此问题并创建一种技术，扩展了 HoloLens 的空间映射功能。</span><span class="sxs-lookup"><span data-stu-id="9fa49-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="9fa49-114">使用此，我们无法分析玩家的空间并确定如墙壁、 表、 椅子和地面图面。</span><span class="sxs-lookup"><span data-stu-id="9fa49-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="9fa49-115">它还会为我们提供的功能优化针对一组限制，以确定 holographic 对象的最佳位置。</span><span class="sxs-lookup"><span data-stu-id="9fa49-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="9fa49-116">空间理解代码</span><span class="sxs-lookup"><span data-stu-id="9fa49-116">The spatial understanding code</span></span>

<span data-ttu-id="9fa49-117">我们花费了 Asobo 的原始代码，并创建一个库，它封装此技术。</span><span class="sxs-lookup"><span data-stu-id="9fa49-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="9fa49-118">Microsoft 和 Asobo 具有现在开放源代码的此代码并使其能够在[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) ，以便在您自己的项目中使用。</span><span class="sxs-lookup"><span data-stu-id="9fa49-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="9fa49-119">从而可以根据需求进行自定义和与社区共享您的改进中包含所有源代码都。</span><span class="sxs-lookup"><span data-stu-id="9fa49-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="9fa49-120">代码C++包装到 UWP DLL 解算器和将其公开到使用 Unity [MixedRealityToolkit 中包含的嵌入式预设](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)。</span><span class="sxs-lookup"><span data-stu-id="9fa49-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="9fa49-121">有许多有用的查询包含在 Unity 示例中，您可以找到在墙上的空白空间，将天花板上或在地板上大空间上放置对象、 识别对字符设有和大量的其他空间了解查询的位置。</span><span class="sxs-lookup"><span data-stu-id="9fa49-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="9fa49-122">虽然 HoloLens 由提供的空间映射解决方案专为一般性还不足以满足整个域中问题所在领域的需求，生成空间了解模块来支持这两个特定游戏的需求。</span><span class="sxs-lookup"><span data-stu-id="9fa49-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="9fa49-123">在这种情况下，其解决方案是围绕一个特定的进程和一组假设的结构化：</span><span class="sxs-lookup"><span data-stu-id="9fa49-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="9fa49-124">**固定大小 playspace**:用户在 init 调用中指定的最大 playspace 大小。</span><span class="sxs-lookup"><span data-stu-id="9fa49-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="9fa49-125">**一次性扫描进程**:该过程需要离散扫描其中用户走周围的阶段，但定义 playspace。</span><span class="sxs-lookup"><span data-stu-id="9fa49-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="9fa49-126">扫描已完成后，查询函数将无法正常之前。</span><span class="sxs-lookup"><span data-stu-id="9fa49-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="9fa49-127">**用户驱动的 playspace"绘制"**:在扫描阶段，用户将移动，并查找围绕 playspace，有效地进行绘制的区域应包括。</span><span class="sxs-lookup"><span data-stu-id="9fa49-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="9fa49-128">务必在此阶段提供用户反馈是生成的网格。</span><span class="sxs-lookup"><span data-stu-id="9fa49-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="9fa49-129">**室内家庭或办公室安装**:查询函数是围绕平面曲面和墙成直角设计的。</span><span class="sxs-lookup"><span data-stu-id="9fa49-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="9fa49-130">这是软限制。</span><span class="sxs-lookup"><span data-stu-id="9fa49-130">This is a soft limitation.</span></span> <span data-ttu-id="9fa49-131">但是，在扫描阶段，主坐标轴分析完成优化主版本号和次的轴的网格分割。</span><span class="sxs-lookup"><span data-stu-id="9fa49-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="9fa49-132">聊天室扫描进程</span><span class="sxs-lookup"><span data-stu-id="9fa49-132">Room Scanning Process</span></span>

<span data-ttu-id="9fa49-133">当空间了解模块加载时，将执行的第一个操作是扫描你的空间，因此所有可用的图面，如 floor、 ceiling 和墙 — 问题被确定并标记为。</span><span class="sxs-lookup"><span data-stu-id="9fa49-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="9fa49-134">在扫描过程中，你看你的聊天室和"画图应包含在扫描过程中的区域。</span><span class="sxs-lookup"><span data-stu-id="9fa49-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="9fa49-135">在此阶段中所示网格是可让用户知道聊天室的哪些部分正在扫描的可视反馈的重要部分。</span><span class="sxs-lookup"><span data-stu-id="9fa49-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="9fa49-136">空间了解模块的 DLL 在内部存储 playspace 为调整大小的 8 cm voxel 多维数据集的网格。</span><span class="sxs-lookup"><span data-stu-id="9fa49-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="9fa49-137">在扫描的初始阶段，完成主成分分析以确定聊天室的轴。</span><span class="sxs-lookup"><span data-stu-id="9fa49-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="9fa49-138">在内部，它将存储到这些轴对齐其 voxel 空间。</span><span class="sxs-lookup"><span data-stu-id="9fa49-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="9fa49-139">通过从 voxel 卷提取等值面大约每隔一秒生成网格。</span><span class="sxs-lookup"><span data-stu-id="9fa49-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![空间映射网格以白色和了解 playspace 网格以绿色](images/spatial-mapping-500px.png)

<span data-ttu-id="9fa49-141">空间映射网格以白色和了解 playspace 网格以绿色</span><span class="sxs-lookup"><span data-stu-id="9fa49-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="9fa49-142">所包含的 SpatialUnderstanding.cs 文件管理扫描阶段的过程。</span><span class="sxs-lookup"><span data-stu-id="9fa49-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="9fa49-143">它将调用以下函数：</span><span class="sxs-lookup"><span data-stu-id="9fa49-143">It calls the following functions:</span></span>
* <span data-ttu-id="9fa49-144">**SpatialUnderstanding_Init**:开始时调用一次。</span><span class="sxs-lookup"><span data-stu-id="9fa49-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="9fa49-145">**GeneratePlayspace_InitScan**:指示应开始扫描阶段。</span><span class="sxs-lookup"><span data-stu-id="9fa49-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="9fa49-146">**GeneratePlayspace_UpdateScan_DynamicScan**:调用每个帧来更新扫描的过程。</span><span class="sxs-lookup"><span data-stu-id="9fa49-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="9fa49-147">照相机位置和方向传入，并且用于 playspace 绘制进程，上面所述。</span><span class="sxs-lookup"><span data-stu-id="9fa49-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="9fa49-148">**GeneratePlayspace_RequestFinish**:调用以完成 playspace。</span><span class="sxs-lookup"><span data-stu-id="9fa49-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="9fa49-149">这将使用"绘制"扫描阶段的区域来定义和锁定 playspace。</span><span class="sxs-lookup"><span data-stu-id="9fa49-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="9fa49-150">在扫描阶段，以及查询自定义网格提供用户的反馈期间，应用程序可以查询统计信息。</span><span class="sxs-lookup"><span data-stu-id="9fa49-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="9fa49-151">**Import_UnderstandingMesh**:在扫描期间**SpatialUnderstandingCustomMesh**模块提供和了解预设可放置的行为将定期查询进程生成的自定义的网格。</span><span class="sxs-lookup"><span data-stu-id="9fa49-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="9fa49-152">此外，这是一次后扫描已完成。</span><span class="sxs-lookup"><span data-stu-id="9fa49-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="9fa49-153">扫描的流，由驱动**SpatialUnderstanding**行为将调用**InitScan**，然后**UpdateScan**每个帧。</span><span class="sxs-lookup"><span data-stu-id="9fa49-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="9fa49-154">当统计信息查询报告合理覆盖率时，用户可以 airtap 调用**RequestFinish**指示扫描阶段结束。</span><span class="sxs-lookup"><span data-stu-id="9fa49-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="9fa49-155">**UpdateScan**继续调用之前返回值指示 DLL 已完成处理。</span><span class="sxs-lookup"><span data-stu-id="9fa49-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="9fa49-156">查询</span><span class="sxs-lookup"><span data-stu-id="9fa49-156">The queries</span></span>

<span data-ttu-id="9fa49-157">扫描完成后，你将能够访问三种不同类型的接口中的查询：</span><span class="sxs-lookup"><span data-stu-id="9fa49-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="9fa49-158">**拓扑查询**:这些是聊天室的基于扫描的拓扑的快速查询。</span><span class="sxs-lookup"><span data-stu-id="9fa49-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="9fa49-159">**调整查询**:这些利用拓扑查询以查找良好匹配到定义的自定义形状的水平表面的结果。</span><span class="sxs-lookup"><span data-stu-id="9fa49-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="9fa49-160">**对象放置查询**:这些是更复杂的查询查找基于一组规则和约束对象的最佳的位置。</span><span class="sxs-lookup"><span data-stu-id="9fa49-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="9fa49-161">除了三个主查询中，没有可用于检索标记的图面类型的光线投射的细节接口，并且自定义的那样严密空间网格可以复制出来。</span><span class="sxs-lookup"><span data-stu-id="9fa49-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="9fa49-162">拓扑查询</span><span class="sxs-lookup"><span data-stu-id="9fa49-162">Topology queries</span></span>

<span data-ttu-id="9fa49-163">在 DLL 内的拓扑管理器处理环境的标记。</span><span class="sxs-lookup"><span data-stu-id="9fa49-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="9fa49-164">如上所述，大量数据存储在 surfels，包含在 voxel 卷中。</span><span class="sxs-lookup"><span data-stu-id="9fa49-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="9fa49-165">此外， **PlaySpaceInfos**结构用于存储有关 playspace，包括世界对齐方式 （下文更多详细信息）、 floor、 和 ceiling 高度的信息。</span><span class="sxs-lookup"><span data-stu-id="9fa49-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="9fa49-166">启发式方法用于确定 floor、 ceiling 和墙。</span><span class="sxs-lookup"><span data-stu-id="9fa49-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="9fa49-167">例如，与大于 1 m2 图面区域的最大和最小水平的面被视为基底。</span><span class="sxs-lookup"><span data-stu-id="9fa49-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="9fa49-168">请注意在此过程中还使用在扫描过程中的照相机路径。</span><span class="sxs-lookup"><span data-stu-id="9fa49-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="9fa49-169">公开的拓扑结构管理器的查询的子集通过 DLL 公开出。</span><span class="sxs-lookup"><span data-stu-id="9fa49-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="9fa49-170">公开的拓扑查询如下所示：</span><span class="sxs-lookup"><span data-stu-id="9fa49-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="9fa49-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="9fa49-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="9fa49-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="9fa49-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="9fa49-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="9fa49-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="9fa49-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="9fa49-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="9fa49-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="9fa49-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="9fa49-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="9fa49-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="9fa49-177">每个查询具有一组特定的查询类型参数。</span><span class="sxs-lookup"><span data-stu-id="9fa49-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="9fa49-178">在以下示例中，用户指定的最小高度和宽度的所需的卷、 更高版本的基底，最少的许可卷的前面放置最小高度。</span><span class="sxs-lookup"><span data-stu-id="9fa49-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="9fa49-179">所有度量值是以米为单位。</span><span class="sxs-lookup"><span data-stu-id="9fa49-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="9fa49-180">每个这些查询采用预分配的数组**TopologyResult**结构。</span><span class="sxs-lookup"><span data-stu-id="9fa49-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="9fa49-181">**LocationCount**参数指定传入的数组的长度。</span><span class="sxs-lookup"><span data-stu-id="9fa49-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="9fa49-182">返回值将报告返回位置数。</span><span class="sxs-lookup"><span data-stu-id="9fa49-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="9fa49-183">此数字大于永远不会传入的**locationCount**参数。</span><span class="sxs-lookup"><span data-stu-id="9fa49-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="9fa49-184">**TopologyResult**包含返回的卷、 面向公众的方向 （即正常），并找到空间的维度的中间位置。</span><span class="sxs-lookup"><span data-stu-id="9fa49-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="9fa49-185">请注意，在 Unity 示例，这些查询的每个虚拟用户界面面板中的按钮为链接。</span><span class="sxs-lookup"><span data-stu-id="9fa49-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="9fa49-186">硬示例代码的合理值到这些查询每个参数。</span><span class="sxs-lookup"><span data-stu-id="9fa49-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="9fa49-187">请参阅*SpaceVisualizer.cs*中更多示例的示例代码。</span><span class="sxs-lookup"><span data-stu-id="9fa49-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="9fa49-188">形状的查询</span><span class="sxs-lookup"><span data-stu-id="9fa49-188">Shape queries</span></span>

<span data-ttu-id="9fa49-189">在 DLL，形状分析器 (**ShapeAnalyzer_W**) 使用拓扑分析器以匹配由用户定义的自定义形状。</span><span class="sxs-lookup"><span data-stu-id="9fa49-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="9fa49-190">Unity 示例有一组预定义的形状选项卡上的查询菜单中显示的形状。</span><span class="sxs-lookup"><span data-stu-id="9fa49-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="9fa49-191">请注意，形状 analysis 工作仅水平图面上。</span><span class="sxs-lookup"><span data-stu-id="9fa49-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="9fa49-192">躺椅，例如，是由平面席位面和平面顶部躺椅上重新定义。</span><span class="sxs-lookup"><span data-stu-id="9fa49-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="9fa49-193">Shape 查询查找与两个表面对齐和连接特定大小、 高度和长宽范围的两个面。</span><span class="sxs-lookup"><span data-stu-id="9fa49-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="9fa49-194">使用 Api 术语，坐在沙发上和躺椅后面的顶部是形状组件和要求的对齐方式形状组件约束。</span><span class="sxs-lookup"><span data-stu-id="9fa49-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="9fa49-195">在 Unity 示例中定义的示例查询 (**ShapeDefinition.cs**)，对于"sittable"对象是按如下所示：</span><span class="sxs-lookup"><span data-stu-id="9fa49-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="9fa49-196">每个形状查询由一组形状组件，每个都有一组组件约束和一组形状约束，其中列出了组件之间的依赖关系定义。</span><span class="sxs-lookup"><span data-stu-id="9fa49-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="9fa49-197">（因为只有一个组件），此示例在单个组件定义和组件之间的任何形状约束中包含三个约束。</span><span class="sxs-lookup"><span data-stu-id="9fa49-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="9fa49-198">与此相反，couch 形状具有两个形状组件和四个形状约束。</span><span class="sxs-lookup"><span data-stu-id="9fa49-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="9fa49-199">请注意，由它们在用户的组件列表 （0 和 1 在此示例中） 中的索引标识组件。</span><span class="sxs-lookup"><span data-stu-id="9fa49-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="9fa49-200">轻松创建自定义形状定义 Unity 模块中提供了包装器函数。</span><span class="sxs-lookup"><span data-stu-id="9fa49-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="9fa49-201">组件和形状的约束的完整列表可在**SpatialUnderstandingDll.cs**内**ShapeComponentConstraint**并**ShapeConstraint**结构。</span><span class="sxs-lookup"><span data-stu-id="9fa49-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![蓝色矩形突出显示了椅子 shape 查询的结果。](images/chair-shape-query-500px.png)

<span data-ttu-id="9fa49-203">蓝色矩形突出显示了椅子 shape 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="9fa49-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="9fa49-204">对象放置解算器</span><span class="sxs-lookup"><span data-stu-id="9fa49-204">Object placement solver</span></span>

<span data-ttu-id="9fa49-205">可以使用对象放置查询以确定放置您的对象的物理空间中的理想位置。</span><span class="sxs-lookup"><span data-stu-id="9fa49-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="9fa49-206">解算器将查找给定的对象规则和约束的最佳的位置。</span><span class="sxs-lookup"><span data-stu-id="9fa49-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="9fa49-207">此外，对象查询持续，直到使用删除的对象**Solver_RemoveObject**或**Solver_RemoveAllObjects**调用，从而允许约束多重对象位置。</span><span class="sxs-lookup"><span data-stu-id="9fa49-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="9fa49-208">对象放置查询由三部分组成： 参数、 一组规则，与约束的列表的位置类型。</span><span class="sxs-lookup"><span data-stu-id="9fa49-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="9fa49-209">若要运行查询，使用以下 API:</span><span class="sxs-lookup"><span data-stu-id="9fa49-209">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="9fa49-210">此函数采用对象名称、 位置定义和规则和约束的列表。</span><span class="sxs-lookup"><span data-stu-id="9fa49-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="9fa49-211">C#包装器提供构造帮助程序函数来简化规则和约束构造。</span><span class="sxs-lookup"><span data-stu-id="9fa49-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="9fa49-212">放置定义包含查询类型，即以下值之一：</span><span class="sxs-lookup"><span data-stu-id="9fa49-212">The placement definition contains the query type — that is, one of the following:</span></span>




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

<span data-ttu-id="9fa49-213">每个位置类型具有一组唯一的类型参数。</span><span class="sxs-lookup"><span data-stu-id="9fa49-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="9fa49-214">**ObjectPlacementDefinition**结构包含一组用于创建这些定义的静态帮助器函数。</span><span class="sxs-lookup"><span data-stu-id="9fa49-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="9fa49-215">例如，若要查找的地板上放置对象的地方，可以使用以下函数：</span><span class="sxs-lookup"><span data-stu-id="9fa49-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="9fa49-216">除了放置类型，可以提供一组规则和约束。</span><span class="sxs-lookup"><span data-stu-id="9fa49-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="9fa49-217">不能违反规则。</span><span class="sxs-lookup"><span data-stu-id="9fa49-217">Rules cannot be violated.</span></span> <span data-ttu-id="9fa49-218">然后，满足的类型和规则的可能的放置位置进行了优化选择最佳的放置位置的约束的一组。</span><span class="sxs-lookup"><span data-stu-id="9fa49-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="9fa49-219">提供静态创建函数，可以创建的每个规则和约束。</span><span class="sxs-lookup"><span data-stu-id="9fa49-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="9fa49-220">下面提供了一个示例规则和约束构造函数。</span><span class="sxs-lookup"><span data-stu-id="9fa49-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="9fa49-221">下面的对象放置查询寻找一半计量多维数据集放入图面的边缘、 从其他以前放置对象和中心附近的房间。</span><span class="sxs-lookup"><span data-stu-id="9fa49-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="9fa49-222">如果成功， **ObjectPlacementResult**返回结构，它包含的放置位置、 尺寸和方向。</span><span class="sxs-lookup"><span data-stu-id="9fa49-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="9fa49-223">此外，位置被添加到放置对象的 DLL 的内部列表。</span><span class="sxs-lookup"><span data-stu-id="9fa49-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="9fa49-224">后续放置查询会考虑到此对象。</span><span class="sxs-lookup"><span data-stu-id="9fa49-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="9fa49-225">**LevelSolver.cs** Unity 示例中的文件包含更多的示例查询。</span><span class="sxs-lookup"><span data-stu-id="9fa49-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![蓝色方框显示使用"立即从照相机位置"规则的三个位置上 Floor 查询的结果。](images/away-from-camera-position-500px.png)

<span data-ttu-id="9fa49-227">蓝色方框显示使用"立即从照相机位置"规则的三个位置上 Floor 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="9fa49-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="9fa49-228">**提示：**</span><span class="sxs-lookup"><span data-stu-id="9fa49-228">**Tips:**</span></span>
* <span data-ttu-id="9fa49-229">当解决所需的级别或应用程序方案的多个对象的放置位置，第一个解决不可或缺和大型对象，若要最大化可找到空间的概率。</span><span class="sxs-lookup"><span data-stu-id="9fa49-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="9fa49-230">放置顺序非常重要。</span><span class="sxs-lookup"><span data-stu-id="9fa49-230">Placement order is important.</span></span> <span data-ttu-id="9fa49-231">如果找不到对象位置，请尝试不太受约束的配置。</span><span class="sxs-lookup"><span data-stu-id="9fa49-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="9fa49-232">具有一组的回退配置对跨多个空间配置支持的功能至关重要。</span><span class="sxs-lookup"><span data-stu-id="9fa49-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="9fa49-233">Ray 强制转换</span><span class="sxs-lookup"><span data-stu-id="9fa49-233">Ray casting</span></span>

<span data-ttu-id="9fa49-234">除了三个主查询中，ray 强制转换接口可用于检索标记的图面类型，并且可以复制自定义的那样严密 playspace 网格出空间已经过扫描并最终确定之后, 标签会在内部生成图面，例如floor、 ceiling 和墙。</span><span class="sxs-lookup"><span data-stu-id="9fa49-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="9fa49-235">**PlayspaceRaycast**函数将一条射线并返回如果射线与已知的图面有冲突，如果是这样，该图面中的窗体有关的信息**RaycastResult**。</span><span class="sxs-lookup"><span data-stu-id="9fa49-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="9fa49-236">在内部，raycast 计算针对 playspace 的立方计算 8 cm voxel 表示形式。</span><span class="sxs-lookup"><span data-stu-id="9fa49-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="9fa49-237">每个 voxel 包含一组的图面上元素与处理的拓扑数据 (也称为 surfels)。</span><span class="sxs-lookup"><span data-stu-id="9fa49-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="9fa49-238">包含在相交的 voxel 单元格中 surfels 进行比较，用于查看拓扑信息的最佳匹配项。</span><span class="sxs-lookup"><span data-stu-id="9fa49-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="9fa49-239">此拓扑的数据包含标记的形式返回**SurfaceTypes**枚举，以及相交曲面的图面区域。</span><span class="sxs-lookup"><span data-stu-id="9fa49-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="9fa49-240">在 Unity 示例中，游标将一条转换为每个帧。</span><span class="sxs-lookup"><span data-stu-id="9fa49-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="9fa49-241">首先，对 Unity 的碰撞体;其次，对了解模块的世界表示形式;和最后，对 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="9fa49-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="9fa49-242">在此应用程序 UI 获取优先级，然后了解结果，并最后，Unity 的碰撞体。</span><span class="sxs-lookup"><span data-stu-id="9fa49-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="9fa49-243">**SurfaceType**报告为旁的文本。</span><span class="sxs-lookup"><span data-stu-id="9fa49-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Raycast 结果报告与 floor 交集。](images/raycast-result-500px.jpg)

<span data-ttu-id="9fa49-245">Raycast 结果报告与 floor 交集。</span><span class="sxs-lookup"><span data-stu-id="9fa49-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="9fa49-246">获取代码</span><span class="sxs-lookup"><span data-stu-id="9fa49-246">Get the code</span></span>

<span data-ttu-id="9fa49-247">开放源代码现已推出[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)。</span><span class="sxs-lookup"><span data-stu-id="9fa49-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="9fa49-248">告知我们[HoloLens 开发人员论坛](https://forums.hololens.com/)如果在项目中使用代码。</span><span class="sxs-lookup"><span data-stu-id="9fa49-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="9fa49-249">我们迫不及待地想看到使用它做什么 ！</span><span class="sxs-lookup"><span data-stu-id="9fa49-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="9fa49-250">关于作者</span><span class="sxs-lookup"><span data-stu-id="9fa49-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="9fa49-251"><b>Jeff Evertt</b>是一种软件工程主管，他曾在 HoloLens 上早期阶段，从孵化体验开发。</span><span class="sxs-lookup"><span data-stu-id="9fa49-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="9fa49-252">HoloLens 之前, 他曾在 Xbox Kinect 上并在游戏行业在各种平台和游戏。</span><span class="sxs-lookup"><span data-stu-id="9fa49-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="9fa49-253">Jeff 充满热情 robotics、 图形和转提示音的闪光灯操作。</span><span class="sxs-lookup"><span data-stu-id="9fa49-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="9fa49-254">他喜欢学习新内容，并使用在软件、 硬件，尤其是在两个相交处的空间。</span><span class="sxs-lookup"><span data-stu-id="9fa49-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="9fa49-255">请参阅</span><span class="sxs-lookup"><span data-stu-id="9fa49-255">See also</span></span>
* [<span data-ttu-id="9fa49-256">空间映射</span><span class="sxs-lookup"><span data-stu-id="9fa49-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="9fa49-257">空间映射设计</span><span class="sxs-lookup"><span data-stu-id="9fa49-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="9fa49-258">聊天室扫描可视化效果</span><span class="sxs-lookup"><span data-stu-id="9fa49-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="9fa49-259">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="9fa49-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="9fa49-260">Asobo Studio:从 HoloLens 开发的一线人员获得的教训</span><span class="sxs-lookup"><span data-stu-id="9fa49-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
