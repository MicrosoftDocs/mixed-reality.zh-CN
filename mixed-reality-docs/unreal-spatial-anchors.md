---
title: Unreal 中的空间定位点
description: Unreal 中空间定位点使用指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间定位点
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840136"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="52c1b-104">Unreal 中的空间定位点</span><span class="sxs-lookup"><span data-stu-id="52c1b-104">Spatial Anchors in Unreal</span></span>

<span data-ttu-id="52c1b-105">空间定位点用于在应用程序会话之间保持真实世界空间中的全息影像。</span><span class="sxs-lookup"><span data-stu-id="52c1b-105">Spatial anchors are used to persist holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="52c1b-106">这是通过 Unreal 以 ARPin 的形式出现的，并保存在 HoloLens 定位点存储中以便在未来会话中加载。</span><span class="sxs-lookup"><span data-stu-id="52c1b-106">This gets surfaced through Unreal as ARPins and gets saved in the HoloLens’ anchor store to be loaded in future sessions.</span></span> 

<span data-ttu-id="52c1b-107">在保存或加载定位点之前，请先检查定位点存储是否已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="52c1b-107">Before saving or loading anchors, first check that the anchor store is ready.</span></span>  <span data-ttu-id="52c1b-108">在定位点存储准备就绪之前，尝试调用任何 HoloLens 定位点函数都不会成功。</span><span class="sxs-lookup"><span data-stu-id="52c1b-108">Attempting to call any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![空间定位点存储准备就绪](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a><span data-ttu-id="52c1b-110">保存定位点</span><span class="sxs-lookup"><span data-stu-id="52c1b-110">Save Anchors</span></span>

<span data-ttu-id="52c1b-111">一旦应用程序的一个组件需要固定到世界，它可以按照以下顺序保存到定位点存储：</span><span class="sxs-lookup"><span data-stu-id="52c1b-111">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![空间定位点保存](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="52c1b-113">在此，我们将在已知位置生成一个 Actor，使用该位置和基于 Actor 类的名称创建一个 ARPin，将 Actor 添加到 ARPin，然后将引脚保存到 HoloLens 定位点存储中。</span><span class="sxs-lookup"><span data-stu-id="52c1b-113">Here, we are spawning an actor at a known location, creating an ARPin with that location and a name based on the actor’s class, adding the actor to the ARPin, and saving the pin to the HoloLens anchor store.</span></span>  <span data-ttu-id="52c1b-114">选择的定位点名称必须是唯一的，因此在本示例中，我们将追加当前时间戳。</span><span class="sxs-lookup"><span data-stu-id="52c1b-114">The anchor name we choose must be unique, so in this example we append the current timestamp.</span></span>  <span data-ttu-id="52c1b-115">如果定位点成功保存到定位点存储，则可以在 HoloLens 设备门户的“系统”>“映射管理器”>“设备上已保存的定位点文件”下检查定位点。</span><span class="sxs-lookup"><span data-stu-id="52c1b-115">If the anchor successfully saves to the anchor store, it can be inspected in the HoloLens device portal under System > Map manager > Anchor Files Saved On Device.</span></span> 

## <a name="load-anchors"></a><span data-ttu-id="52c1b-116">加载定位点</span><span class="sxs-lookup"><span data-stu-id="52c1b-116">Load Anchors</span></span>

<span data-ttu-id="52c1b-117">当应用程序启动时，可以调用以下蓝图将组件还原到其定位点位置：</span><span class="sxs-lookup"><span data-stu-id="52c1b-117">When an application starts, the following blueprint can be called to restore components to their anchor locations:</span></span>

![空间定位点加载](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="52c1b-119">在本例中，我们循环访问定位点存储中的所有定位点，在标识处生成一个 Actor，并将该 Actor 从定位点存储固定到 ARPin。</span><span class="sxs-lookup"><span data-stu-id="52c1b-119">In this example, we iterate over all of the anchors in the anchor store, spawn an actor at identity, and pin that actor to the ARPin from the anchor store.</span></span>  <span data-ttu-id="52c1b-120">必须按标识生成 Actor，这一点很重要，因为定位点负责根据全息影像的保存位置在世界中重新定位全息影像，因此，此处添加的任何变形都将增加定位点的偏移量。</span><span class="sxs-lookup"><span data-stu-id="52c1b-120">It is important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved, so any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="52c1b-121">还将查询定位点 ID，以便根据定位点的保存名称来生成不同的 Actor。</span><span class="sxs-lookup"><span data-stu-id="52c1b-121">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="remove-anchors"></a><span data-ttu-id="52c1b-122">删除定位点</span><span class="sxs-lookup"><span data-stu-id="52c1b-122">Remove Anchors</span></span> 

<span data-ttu-id="52c1b-123">完成定位点操作后，可以清除整个定位点存储，也可以从定位点存储中删除单个定位点，这样它们就不会包含在未来会话中：</span><span class="sxs-lookup"><span data-stu-id="52c1b-123">When done with an anchor, the entire anchor store can be cleared, or individual anchors can be removed from the anchor store so they are not included in future sessions:</span></span> 

![空间定位点删除](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a><span data-ttu-id="52c1b-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52c1b-125">See also</span></span>
* [<span data-ttu-id="52c1b-126">空间定位点</span><span class="sxs-lookup"><span data-stu-id="52c1b-126">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="52c1b-127">坐标系统</span><span class="sxs-lookup"><span data-stu-id="52c1b-127">Coordinate systems</span></span>](coordinate-systems.md)
