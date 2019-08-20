---
title: 案例研究-扩展 HoloLens 的空间映射功能
description: 在创建 Microsoft HoloLens 的第一个应用程序时, 我们渴望知道我们可以在设备上推送空间映射边界。
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 空间映射
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522699"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="763bf-104">案例研究-扩展 HoloLens 的空间映射功能</span><span class="sxs-lookup"><span data-stu-id="763bf-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="763bf-105">在创建 Microsoft HoloLens 的第一个应用程序时, 我们渴望知道我们可以在设备上推送空间映射边界。</span><span class="sxs-lookup"><span data-stu-id="763bf-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="763bf-106">Jeff Evertt 是 Microsoft 录音室的软件工程师, 介绍了如何开发一项新技术, 以更好地控制如何在用户的实际环境中放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="763bf-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="763bf-107">观看视频</span><span class="sxs-lookup"><span data-stu-id="763bf-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="763bf-108">超出空间映射</span><span class="sxs-lookup"><span data-stu-id="763bf-108">Beyond spatial mapping</span></span>

<span data-ttu-id="763bf-109">尽管我们处理的是[Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)的第一项游戏中的两个, 但我们发现, 当我们在物理世界中进行程序的过程放置时, 我们需要对用户的环境.</span><span class="sxs-lookup"><span data-stu-id="763bf-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="763bf-110">每个游戏都有其自己的特定放置需求:例如, 在片段中, 我们希望能够区分不同的图面 (如地面或表格), 以便在相关位置放置线索。</span><span class="sxs-lookup"><span data-stu-id="763bf-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="763bf-111">此外, 我们还希望能够确定生活空间内全息字符可能位于的表面, 如床或椅子。</span><span class="sxs-lookup"><span data-stu-id="763bf-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="763bf-112">在年轻的 Conker 中, 我们希望 Conker 及其对手能够将播放机房间中凸起的表面用作平台。</span><span class="sxs-lookup"><span data-stu-id="763bf-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="763bf-113">[Asobo 工作室](http://www.asobostudio.com/index.html)是这些游戏的开发合作伙伴, 面对这一问题, 并创建了一种可扩展 HoloLens 空间映射功能的技术。</span><span class="sxs-lookup"><span data-stu-id="763bf-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="763bf-114">使用此类, 我们可以分析玩家的房间, 并识别面、表、椅子和地面等表面。</span><span class="sxs-lookup"><span data-stu-id="763bf-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="763bf-115">它还使我们能够根据一组约束进行优化, 以确定全息对象的最佳位置。</span><span class="sxs-lookup"><span data-stu-id="763bf-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="763bf-116">空间理解代码</span><span class="sxs-lookup"><span data-stu-id="763bf-116">The spatial understanding code</span></span>

<span data-ttu-id="763bf-117">我们采用 Asobo 的原始代码, 并创建了一个封装了此技术的库。</span><span class="sxs-lookup"><span data-stu-id="763bf-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="763bf-118">Microsoft 和 Asobo 现在提供了此代码, 并使其在[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping)中可用, 以便你可以在自己的项目中使用。</span><span class="sxs-lookup"><span data-stu-id="763bf-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="763bf-119">所有源代码都包含在内, 允许你根据需求进行自定义, 并与社区分享你的改进。</span><span class="sxs-lookup"><span data-stu-id="763bf-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="763bf-120">C++规划求解的代码已包装到 UWP DLL 中, 并使用[MixedRealityToolkit 中包含的下拉 prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)向 Unity 公开。</span><span class="sxs-lookup"><span data-stu-id="763bf-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="763bf-121">Unity 示例中包含了许多有用的查询, 可用于查找墙壁上的空白空间, 将对象置于天花板上或空间上的较大空间, 确定要放置的字符的位置以及其他许多空间理解查询。</span><span class="sxs-lookup"><span data-stu-id="763bf-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="763bf-122">虽然 HoloLens 提供的空间映射解决方案设计为能够满足整个范围内的所有问题, 但构建了空间理解模块, 以支持两个特定游戏的需求。</span><span class="sxs-lookup"><span data-stu-id="763bf-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="763bf-123">因此, 其解决方案是围绕特定过程和假设集构造的:</span><span class="sxs-lookup"><span data-stu-id="763bf-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="763bf-124">**固定大小 playspace**:用户指定 init 调用中的最大 playspace 大小。</span><span class="sxs-lookup"><span data-stu-id="763bf-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="763bf-125">**一次性扫描进程**:此过程需要一个独立的扫描阶段, 其中用户会在其中进行操作, 定义 playspace。</span><span class="sxs-lookup"><span data-stu-id="763bf-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="763bf-126">在完成扫描后, 查询函数将不起作用。</span><span class="sxs-lookup"><span data-stu-id="763bf-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="763bf-127">**用户驱动的 playspace "painting"** :在扫描阶段, 用户会四处移动并查看 playspace, 从而有效地绘制应包括的区域。</span><span class="sxs-lookup"><span data-stu-id="763bf-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="763bf-128">在此阶段, 生成的网格非常重要, 可提供用户反馈。</span><span class="sxs-lookup"><span data-stu-id="763bf-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="763bf-129">**室内家庭或办公设置**:查询函数围绕平整表面和墙壁围绕直角设计。</span><span class="sxs-lookup"><span data-stu-id="763bf-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="763bf-130">这是一个软限制。</span><span class="sxs-lookup"><span data-stu-id="763bf-130">This is a soft limitation.</span></span> <span data-ttu-id="763bf-131">但是, 在扫描阶段, 将完成主轴分析以按主要轴和次要轴优化网格分割。</span><span class="sxs-lookup"><span data-stu-id="763bf-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="763bf-132">房间扫描过程</span><span class="sxs-lookup"><span data-stu-id="763bf-132">Room Scanning Process</span></span>

<span data-ttu-id="763bf-133">当您加载空间理解模块时, 您首先要扫描您的空间, 以便标识并标记所有可用的图面 (如地面、天花板和墙壁)。</span><span class="sxs-lookup"><span data-stu-id="763bf-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="763bf-134">在扫描过程中, 你将查找聊天室, 并 "粉刷" 应包括在扫描中的区域。</span><span class="sxs-lookup"><span data-stu-id="763bf-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="763bf-135">此阶段中的网格是一项非常重要的视觉反馈, 可让用户知道要扫描的房间的哪些部分。</span><span class="sxs-lookup"><span data-stu-id="763bf-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="763bf-136">空间理解模块的 DLL 在内部将 playspace 存储为8cm 大小 voxel 多维数据集的网格。</span><span class="sxs-lookup"><span data-stu-id="763bf-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="763bf-137">在扫描的初始部分中, 将完成主要组件分析以确定房间的轴。</span><span class="sxs-lookup"><span data-stu-id="763bf-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="763bf-138">在内部, 它存储其 voxel 空间与这些轴对齐。</span><span class="sxs-lookup"><span data-stu-id="763bf-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="763bf-139">大约每秒生成一次网格, 方法是从 voxel 卷中提取等值面。</span><span class="sxs-lookup"><span data-stu-id="763bf-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![白色的空间映射网格, 并了解绿色的 playspace 网格](images/spatial-mapping-500px.png)

<span data-ttu-id="763bf-141">白色的空间映射网格, 并了解绿色的 playspace 网格</span><span class="sxs-lookup"><span data-stu-id="763bf-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="763bf-142">包含的 SpatialUnderstanding.cs 文件管理扫描阶段过程。</span><span class="sxs-lookup"><span data-stu-id="763bf-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="763bf-143">它调用以下函数:</span><span class="sxs-lookup"><span data-stu-id="763bf-143">It calls the following functions:</span></span>
* <span data-ttu-id="763bf-144">**SpatialUnderstanding_Init**:在开始时调用一次。</span><span class="sxs-lookup"><span data-stu-id="763bf-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="763bf-145">**GeneratePlayspace_InitScan**:指示扫描阶段应开始。</span><span class="sxs-lookup"><span data-stu-id="763bf-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="763bf-146">**GeneratePlayspace_UpdateScan_DynamicScan**:调用每个帧以更新扫描进程。</span><span class="sxs-lookup"><span data-stu-id="763bf-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="763bf-147">照相机位置和方向传入并用于 playspace 绘制过程, 如上所述。</span><span class="sxs-lookup"><span data-stu-id="763bf-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="763bf-148">**GeneratePlayspace_RequestFinish**:调用以完成 playspace。</span><span class="sxs-lookup"><span data-stu-id="763bf-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="763bf-149">这会在扫描阶段使用 "绘制" 区域来定义和锁定 playspace。</span><span class="sxs-lookup"><span data-stu-id="763bf-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="763bf-150">应用程序可以在扫描阶段查询统计信息, 还可以查询自定义网格来提供用户反馈。</span><span class="sxs-lookup"><span data-stu-id="763bf-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="763bf-151">**Import_UnderstandingMesh**:在扫描过程中, 模块提供并置于理解 prefab 上的**SpatialUnderstandingCustomMesh**行为会定期查询由进程生成的自定义网格。</span><span class="sxs-lookup"><span data-stu-id="763bf-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="763bf-152">此外, 完成扫描后, 还将执行此操作。</span><span class="sxs-lookup"><span data-stu-id="763bf-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="763bf-153">**SpatialUnderstanding**行为驱动的扫描流调用**InitScan**, 然后**UpdateScan**每个帧。</span><span class="sxs-lookup"><span data-stu-id="763bf-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="763bf-154">当统计信息查询报告合理的范围时, 用户可以 airtap 调用**RequestFinish**以指示扫描阶段的结束。</span><span class="sxs-lookup"><span data-stu-id="763bf-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="763bf-155">继续调用**UpdateScan** , 直到返回值指示 DLL 已完成处理。</span><span class="sxs-lookup"><span data-stu-id="763bf-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="763bf-156">查询</span><span class="sxs-lookup"><span data-stu-id="763bf-156">The queries</span></span>

<span data-ttu-id="763bf-157">扫描完成后, 你将能够访问接口中的三种不同类型的查询:</span><span class="sxs-lookup"><span data-stu-id="763bf-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="763bf-158">**拓扑查询**:这些是基于扫描房间的拓扑的快速查询。</span><span class="sxs-lookup"><span data-stu-id="763bf-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="763bf-159">**形状查询**:它们利用拓扑查询的结果来查找与您定义的自定义形状非常匹配的水平曲面。</span><span class="sxs-lookup"><span data-stu-id="763bf-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="763bf-160">**对象放置查询**:这些是更复杂的查询, 可基于对象的一组规则和约束查找最佳位置。</span><span class="sxs-lookup"><span data-stu-id="763bf-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="763bf-161">除了三个主要查询外, 还提供了一个 raycasting 接口, 该接口可用于检索标记的表面类型和自定义的 watertight 房间网格。</span><span class="sxs-lookup"><span data-stu-id="763bf-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="763bf-162">拓扑查询</span><span class="sxs-lookup"><span data-stu-id="763bf-162">Topology queries</span></span>

<span data-ttu-id="763bf-163">在 DLL 中, 拓扑管理器处理环境的标记。</span><span class="sxs-lookup"><span data-stu-id="763bf-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="763bf-164">如上所述, 很多数据存储在 surfels 中, 这些数据包含在 voxel 卷中。</span><span class="sxs-lookup"><span data-stu-id="763bf-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="763bf-165">此外, **PlaySpaceInfos**结构用于存储有关 playspace 的信息, 其中包括世界对齐 (有关此内容的更多详细信息)、楼层和天花板高度。</span><span class="sxs-lookup"><span data-stu-id="763bf-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="763bf-166">试探法用于确定地面、天花板和墙。</span><span class="sxs-lookup"><span data-stu-id="763bf-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="763bf-167">例如, 具有大于1个 m2 面区的最大和最低水平曲面被视为楼层。</span><span class="sxs-lookup"><span data-stu-id="763bf-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="763bf-168">请注意, 在此过程中也使用了扫描过程中的照相机路径。</span><span class="sxs-lookup"><span data-stu-id="763bf-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="763bf-169">拓扑管理器公开的查询子集通过 DLL 公开。</span><span class="sxs-lookup"><span data-stu-id="763bf-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="763bf-170">公开的拓扑查询如下所示:</span><span class="sxs-lookup"><span data-stu-id="763bf-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="763bf-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="763bf-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="763bf-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="763bf-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="763bf-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="763bf-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="763bf-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="763bf-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="763bf-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="763bf-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="763bf-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="763bf-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="763bf-177">每个查询都具有一组特定于查询类型的参数。</span><span class="sxs-lookup"><span data-stu-id="763bf-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="763bf-178">在下面的示例中, 用户指定了所需的卷的最小高度 & 宽度、地面上的最小位置高度以及卷前面的最小间隙量。</span><span class="sxs-lookup"><span data-stu-id="763bf-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="763bf-179">所有度量都以米为单位。</span><span class="sxs-lookup"><span data-stu-id="763bf-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="763bf-180">其中每个查询都采用预分配的**TopologyResult**结构数组。</span><span class="sxs-lookup"><span data-stu-id="763bf-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="763bf-181">**LocationCount**参数指定传入数组的长度。</span><span class="sxs-lookup"><span data-stu-id="763bf-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="763bf-182">返回值报告返回的位置的数量。</span><span class="sxs-lookup"><span data-stu-id="763bf-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="763bf-183">此数字绝不会大于传入的**locationCount**参数。</span><span class="sxs-lookup"><span data-stu-id="763bf-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="763bf-184">**TopologyResult**包含返回的卷的中心位置、定向方向 (即普通) 以及找到的空间的尺寸。</span><span class="sxs-lookup"><span data-stu-id="763bf-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="763bf-185">请注意, 在 Unity 示例中, 其中每个查询都链接到 "虚拟 UI" 面板中的某个按钮。</span><span class="sxs-lookup"><span data-stu-id="763bf-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="763bf-186">示例将每个查询的参数硬编码为合理的值。</span><span class="sxs-lookup"><span data-stu-id="763bf-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="763bf-187">有关更多示例, 请参阅示例代码中的*SpaceVisualizer.cs* 。</span><span class="sxs-lookup"><span data-stu-id="763bf-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="763bf-188">形状查询</span><span class="sxs-lookup"><span data-stu-id="763bf-188">Shape queries</span></span>

<span data-ttu-id="763bf-189">在 DLL 内部, 形状分析器 (**ShapeAnalyzer_W**) 使用拓扑分析器与用户定义的自定义形状相匹配。</span><span class="sxs-lookup"><span data-stu-id="763bf-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="763bf-190">Unity 示例包含一组预定义的形状, 它们显示在 "查询" 菜单的 "形状" 选项卡上。</span><span class="sxs-lookup"><span data-stu-id="763bf-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="763bf-191">请注意, 形状分析仅适用于水平曲面。</span><span class="sxs-lookup"><span data-stu-id="763bf-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="763bf-192">例如, 沙发由平面座位表面和沙发顶部的扁平顶部定义。</span><span class="sxs-lookup"><span data-stu-id="763bf-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="763bf-193">形状查询查找特定大小、高度和方位范围的两个图面, 两个图面对齐并连接起来。</span><span class="sxs-lookup"><span data-stu-id="763bf-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="763bf-194">使用 Api 术语, 沙发座位和沙发背面的顶部是形状组件, 对齐要求是形状组件约束。</span><span class="sxs-lookup"><span data-stu-id="763bf-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="763bf-195">"Sittable" 对象在 Unity 示例 (**ShapeDefinition.cs**) 中定义的示例查询如下所示:</span><span class="sxs-lookup"><span data-stu-id="763bf-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




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

<span data-ttu-id="763bf-196">每个形状查询都由一组形状组件定义, 每个形状组件都具有一组组件约束和一组形状约束, 其中列出了组件之间的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="763bf-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="763bf-197">此示例在单个组件定义中包含三个约束, 组件之间没有任何形状约束 (因为只有一个组件)。</span><span class="sxs-lookup"><span data-stu-id="763bf-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="763bf-198">与此相反, 沙发形状具有两个形状组件和四个形状约束。</span><span class="sxs-lookup"><span data-stu-id="763bf-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="763bf-199">请注意, 组件由其在用户的组件列表中的索引标识 (在本示例中为0和 1)。</span><span class="sxs-lookup"><span data-stu-id="763bf-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="763bf-200">在 Unity 模块中提供包装函数以便于创建自定义形状定义。</span><span class="sxs-lookup"><span data-stu-id="763bf-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="763bf-201">可以在**ShapeComponentConstraint**和**ShapeConstraint**结构内的**SpatialUnderstandingDll.cs**中找到组件和形状约束的完整列表。</span><span class="sxs-lookup"><span data-stu-id="763bf-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![蓝色矩形突出显示椅子形状查询的结果。](images/chair-shape-query-500px.png)

<span data-ttu-id="763bf-203">蓝色矩形突出显示椅子形状查询的结果。</span><span class="sxs-lookup"><span data-stu-id="763bf-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="763bf-204">对象放置规划求解</span><span class="sxs-lookup"><span data-stu-id="763bf-204">Object placement solver</span></span>

<span data-ttu-id="763bf-205">对象放置查询可用于确定放置对象的物理空间中的理想位置。</span><span class="sxs-lookup"><span data-stu-id="763bf-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="763bf-206">规划求解会根据对象规则和约束找到最佳位置。</span><span class="sxs-lookup"><span data-stu-id="763bf-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="763bf-207">此外, 对象查询会一直保留, 直到通过**Solver_RemoveObject**或**Solver_RemoveAllObjects**调用移除该对象, 从而允许约束的多对象位置。</span><span class="sxs-lookup"><span data-stu-id="763bf-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="763bf-208">对象放置查询由三个部分组成: 具有参数的放置类型、规则列表和约束列表。</span><span class="sxs-lookup"><span data-stu-id="763bf-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="763bf-209">若要运行查询, 请使用以下 API:</span><span class="sxs-lookup"><span data-stu-id="763bf-209">To run a query, use the following API:</span></span>




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
<span data-ttu-id="763bf-210">此函数采用对象名称、位置定义和规则和约束列表。</span><span class="sxs-lookup"><span data-stu-id="763bf-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="763bf-211">C#包装器提供构造帮助器函数, 可简化规则和约束构造。</span><span class="sxs-lookup"><span data-stu-id="763bf-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="763bf-212">"位置" 定义包含查询类型, 即:</span><span class="sxs-lookup"><span data-stu-id="763bf-212">The placement definition contains the query type — that is, one of the following:</span></span>




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

<span data-ttu-id="763bf-213">每个放置类型都具有一组特定于该类型的参数。</span><span class="sxs-lookup"><span data-stu-id="763bf-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="763bf-214">**ObjectPlacementDefinition**结构包含一组静态 helper 函数, 用于创建这些定义。</span><span class="sxs-lookup"><span data-stu-id="763bf-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="763bf-215">例如, 若要查找在楼层上放置对象的位置, 可以使用以下函数:</span><span class="sxs-lookup"><span data-stu-id="763bf-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="763bf-216">除了放置类型之外, 还可以提供一组规则和约束。</span><span class="sxs-lookup"><span data-stu-id="763bf-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="763bf-217">不能违反规则。</span><span class="sxs-lookup"><span data-stu-id="763bf-217">Rules cannot be violated.</span></span> <span data-ttu-id="763bf-218">然后, 将根据一组约束优化满足类型和规则的位置位置, 以选择最佳放置位置。</span><span class="sxs-lookup"><span data-stu-id="763bf-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="763bf-219">每个规则和约束都可以通过提供的静态创建函数来创建。</span><span class="sxs-lookup"><span data-stu-id="763bf-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="763bf-220">下面提供了一个示例规则和约束构造函数。</span><span class="sxs-lookup"><span data-stu-id="763bf-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="763bf-221">下面的对象放置查询正在寻找一个位置, 用于将半米立方体放置在表面的边缘, 远离其他以前放置的对象, 靠近房间的中心。</span><span class="sxs-lookup"><span data-stu-id="763bf-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




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

<span data-ttu-id="763bf-222">如果成功, 则返回包含放置位置、尺寸和方向的**ObjectPlacementResult**结构。</span><span class="sxs-lookup"><span data-stu-id="763bf-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="763bf-223">此外, 放置将添加到 DLL 的已放置对象的内部列表中。</span><span class="sxs-lookup"><span data-stu-id="763bf-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="763bf-224">后续的放置查询会将此对象考虑在内。</span><span class="sxs-lookup"><span data-stu-id="763bf-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="763bf-225">Unity 示例中的**LevelSolver.cs**文件包含更多的示例查询。</span><span class="sxs-lookup"><span data-stu-id="763bf-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![蓝框显示了三个位置对地面查询的结果, 其 "远离照相机位置" 规则。](images/away-from-camera-position-500px.png)

<span data-ttu-id="763bf-227">蓝框显示了三个位置对地面查询的结果, 其 "远离照相机位置" 规则。</span><span class="sxs-lookup"><span data-stu-id="763bf-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="763bf-228">**技巧**</span><span class="sxs-lookup"><span data-stu-id="763bf-228">**Tips:**</span></span>
* <span data-ttu-id="763bf-229">在为级别或应用程序方案所需的多个对象进行放置位置求解时, 首先要解决不必要的和大型对象, 以最大程度地提高空间的出现概率。</span><span class="sxs-lookup"><span data-stu-id="763bf-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="763bf-230">放置顺序很重要。</span><span class="sxs-lookup"><span data-stu-id="763bf-230">Placement order is important.</span></span> <span data-ttu-id="763bf-231">如果找不到对象位置, 请尝试减少不受约束的配置。</span><span class="sxs-lookup"><span data-stu-id="763bf-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="763bf-232">具有一组后备配置对于跨许多房间配置支持功能至关重要。</span><span class="sxs-lookup"><span data-stu-id="763bf-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="763bf-233">Ray 转换</span><span class="sxs-lookup"><span data-stu-id="763bf-233">Ray casting</span></span>

<span data-ttu-id="763bf-234">除了三个主要查询外, 还可以使用 ray 强制转换接口检索标记的表面类型, 在扫描并完成空间后, 可以将自定义 watertight playspace 网格复制到楼层、天花板和墙。</span><span class="sxs-lookup"><span data-stu-id="763bf-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="763bf-235">**PlayspaceRaycast**函数将使用一条射线, 如果该射线与已知表面冲突, 则返回, 如果是, 则返回**RaycastResult**形式的有关该曲面的信息。</span><span class="sxs-lookup"><span data-stu-id="763bf-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


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

<span data-ttu-id="763bf-236">在内部, raycast 是针对 playspace 的计算8cm 立方 voxel 表示法计算的。</span><span class="sxs-lookup"><span data-stu-id="763bf-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="763bf-237">每个 voxel 包含一组具有已处理拓扑数据 (也称为 surfels) 的 surface 元素。</span><span class="sxs-lookup"><span data-stu-id="763bf-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="763bf-238">将比较交叉 voxel 单元中包含的 surfels 和用于查找拓扑信息的最佳匹配项。</span><span class="sxs-lookup"><span data-stu-id="763bf-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="763bf-239">此拓扑数据包含以**SurfaceTypes**枚举形式返回的标签, 以及相交表面的图面区域。</span><span class="sxs-lookup"><span data-stu-id="763bf-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="763bf-240">在 Unity 示例中, 游标将每个帧都转换为射线。</span><span class="sxs-lookup"><span data-stu-id="763bf-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="763bf-241">首先, 针对 Unity 的 colliders;其次, 针对理解模块的世界表示形式;最后, 针对 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="763bf-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="763bf-242">在此应用程序中, UI 获得优先级, 然后是理解结果, 最后是 Unity 的 colliders。</span><span class="sxs-lookup"><span data-stu-id="763bf-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="763bf-243">**SurfaceType**将报告为光标旁边的文本。</span><span class="sxs-lookup"><span data-stu-id="763bf-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Raycast 结果报告与楼层的交集。](images/raycast-result-500px.jpg)

<span data-ttu-id="763bf-245">Raycast 结果报告与楼层的交集。</span><span class="sxs-lookup"><span data-stu-id="763bf-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="763bf-246">获取代码</span><span class="sxs-lookup"><span data-stu-id="763bf-246">Get the code</span></span>

<span data-ttu-id="763bf-247">[MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)中提供了开放源代码。</span><span class="sxs-lookup"><span data-stu-id="763bf-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="763bf-248">如果你在项目中使用代码, 请在[HoloLens 开发人员论坛](https://forums.hololens.com/)上告知我们。</span><span class="sxs-lookup"><span data-stu-id="763bf-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="763bf-249">我们无法等待了解你的操作!</span><span class="sxs-lookup"><span data-stu-id="763bf-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="763bf-250">关于作者</span><span class="sxs-lookup"><span data-stu-id="763bf-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="763bf-251"><b>Jeff Evertt</b>是从 incubation 到体验开发以来从一天起开始开始工作的软件工程组长。</span><span class="sxs-lookup"><span data-stu-id="763bf-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="763bf-252">在 HoloLens 之前, 他在各种平台和游戏的各种平台和游戏中使用了 Xbox Kinect 和游戏行业。</span><span class="sxs-lookup"><span data-stu-id="763bf-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="763bf-253">Jeff 是热衷于的机器人、图形和东西, 暴躁会发出嘟嘟声。</span><span class="sxs-lookup"><span data-stu-id="763bf-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="763bf-254">他喜欢学习新东西并处理软件、硬件, 尤其是在这两个交叉点的空间中。</span><span class="sxs-lookup"><span data-stu-id="763bf-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="763bf-255">请参阅</span><span class="sxs-lookup"><span data-stu-id="763bf-255">See also</span></span>
* [<span data-ttu-id="763bf-256">空间映射</span><span class="sxs-lookup"><span data-stu-id="763bf-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="763bf-257">空间映射设计</span><span class="sxs-lookup"><span data-stu-id="763bf-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="763bf-258">房间扫描可视化</span><span class="sxs-lookup"><span data-stu-id="763bf-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="763bf-259">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="763bf-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="763bf-260">Asobo Studio:HoloLens 开发前端的课程</span><span class="sxs-lookup"><span data-stu-id="763bf-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
