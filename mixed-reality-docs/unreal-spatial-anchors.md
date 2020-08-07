---
title: Unreal 中的本地空间定位点
description: Unreal 中空间定位点使用指南
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间定位点
ms.openlocfilehash: b102d506b1d670291c3b97ca34d277e2597af043
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376041"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="188bf-104">Unreal 中的本地空间定位点</span><span class="sxs-lookup"><span data-stu-id="188bf-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="188bf-105">概述</span><span class="sxs-lookup"><span data-stu-id="188bf-105">Overview</span></span>

<span data-ttu-id="188bf-106">空间定位点用于在应用程序会话之间保存真实世界空间中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="188bf-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="188bf-107">这些是通过 Unreal 以 ARPin 的形式出现的，并保存在 HoloLens 定位点存储中以便在未来会话中加载。</span><span class="sxs-lookup"><span data-stu-id="188bf-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="188bf-108">当没有 Internet 连接时，本地定位点是理想的备用方案。</span><span class="sxs-lookup"><span data-stu-id="188bf-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="188bf-109">本地定位点存储在设备上，而 Azure 空间定位点存储在云中。</span><span class="sxs-lookup"><span data-stu-id="188bf-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="188bf-110">如果你想要使用 Azure 云服务来存储定位点，我们有一个文档可指导你如何集成 [Azure 空间定位点](unreal-azure-spatial-anchors.md)。</span><span class="sxs-lookup"><span data-stu-id="188bf-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="188bf-111">请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。</span><span class="sxs-lookup"><span data-stu-id="188bf-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="188bf-112">检查定位点存储</span><span class="sxs-lookup"><span data-stu-id="188bf-112">Checking the anchor store</span></span>

<span data-ttu-id="188bf-113">在保存或加载定位点之前，需要检查定位点存储是否已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="188bf-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="188bf-114">在定位点存储准备就绪之前，调用任何 HoloLens 定位点函数都不会成功。</span><span class="sxs-lookup"><span data-stu-id="188bf-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![空间定位点存储准备就绪](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="188bf-116">保存定位点</span><span class="sxs-lookup"><span data-stu-id="188bf-116">Saving anchors</span></span>

<span data-ttu-id="188bf-117">一旦应用程序的一个组件需要固定到世界，它可以按照以下顺序保存到定位点存储：</span><span class="sxs-lookup"><span data-stu-id="188bf-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![空间定位点保存](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="188bf-119">细分如下：</span><span class="sxs-lookup"><span data-stu-id="188bf-119">Breaking this down:</span></span>
1. <span data-ttu-id="188bf-120">在已知位置生成 Actor。</span><span class="sxs-lookup"><span data-stu-id="188bf-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="188bf-121">使用该位置和基于 Actor 的类的名称创建 ARPin。</span><span class="sxs-lookup"><span data-stu-id="188bf-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="188bf-122">将 Actor 添加到 ARPin并将引脚保存到 HoloLens 定位点存储。</span><span class="sxs-lookup"><span data-stu-id="188bf-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="188bf-123">选择的定位点名称必须是唯一的，因此在本示例中是当前时间戳。</span><span class="sxs-lookup"><span data-stu-id="188bf-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="188bf-124">如果定位点成功保存到定位点存储，则可以在 HoloLens 设备门户的“系统”>“映射管理器”>“设备上已保存的定位点文件”下检查定位点。</span><span class="sxs-lookup"><span data-stu-id="188bf-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="188bf-125">加载定位点</span><span class="sxs-lookup"><span data-stu-id="188bf-125">Loading anchors</span></span>

<span data-ttu-id="188bf-126">当应用程序启动时，可以使用以下蓝图将组件还原到其定位点位置：</span><span class="sxs-lookup"><span data-stu-id="188bf-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![空间定位点加载](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="188bf-128">细分如下：</span><span class="sxs-lookup"><span data-stu-id="188bf-128">Breaking this down:</span></span>
1. <span data-ttu-id="188bf-129">循环访问定位点存储中的所有定位点。</span><span class="sxs-lookup"><span data-stu-id="188bf-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="188bf-130">按标识生成 Actor。</span><span class="sxs-lookup"><span data-stu-id="188bf-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="188bf-131">将该 Actor 从定位点存储固定到 ARPin。</span><span class="sxs-lookup"><span data-stu-id="188bf-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="188bf-132">必须按标识生成 Actor，这一点很重要，因为定位点负责根据全息影像的保存位置在世界中重新定位全息影像。</span><span class="sxs-lookup"><span data-stu-id="188bf-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="188bf-133">因此，此处添加的任何变形都将增加定位点的偏移量。</span><span class="sxs-lookup"><span data-stu-id="188bf-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="188bf-134">还将查询定位点 ID，以便根据定位点的保存名称来生成不同的 Actor。</span><span class="sxs-lookup"><span data-stu-id="188bf-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="188bf-135">删除定位点</span><span class="sxs-lookup"><span data-stu-id="188bf-135">Removing anchors</span></span> 

<span data-ttu-id="188bf-136">完成定位点后，可以使用“从 WMRAnchor 存储中删除 ARPin”和“从 WMRAnchor 存储中删除所有 ARPin”组件来清除单个定位点或整个定位点存储 。</span><span class="sxs-lookup"><span data-stu-id="188bf-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![空间定位点删除](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="188bf-138">请记住，空间定位点仍处于测试阶段，因此，请务必查看是否有更新的信息和功能。</span><span class="sxs-lookup"><span data-stu-id="188bf-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="188bf-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="188bf-139">See also</span></span>
* [<span data-ttu-id="188bf-140">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="188bf-140">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="188bf-141">空间定位点</span><span class="sxs-lookup"><span data-stu-id="188bf-141">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="188bf-142">坐标系统</span><span class="sxs-lookup"><span data-stu-id="188bf-142">Coordinate systems</span></span>](coordinate-systems.md)
