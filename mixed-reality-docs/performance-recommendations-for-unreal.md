---
title: 针对 Unreal 的性能建议
description: Unreal 中混合现实应用获得最佳性能的建议
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 性能, 优化, 设置, 文档
ms.openlocfilehash: a7972962eeb2b1480a7da38210b5ee77104f508b
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303629"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="f1d42-104">针对 Unreal 的性能建议</span><span class="sxs-lookup"><span data-stu-id="f1d42-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="f1d42-105">概述</span><span class="sxs-lookup"><span data-stu-id="f1d42-105">Overview</span></span>

<span data-ttu-id="f1d42-106">本文是在[针对混合现实的性能建议](understanding-performance-for-mixed-reality.md)中所述内容的基础上编写的，但重点介绍特定于 Unreal Engine 的功能。</span><span class="sxs-lookup"><span data-stu-id="f1d42-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="f1d42-107">建议在继续操作之前，先了解应用程序瓶颈和一般性能修复，以及有关分析和剖析混合现实应用的信息。</span><span class="sxs-lookup"><span data-stu-id="f1d42-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="f1d42-108">建议的 Unreal 项目设置</span><span class="sxs-lookup"><span data-stu-id="f1d42-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="f1d42-109">可以在“编辑”>“项目设置”中找到以下每个设置。</span><span class="sxs-lookup"><span data-stu-id="f1d42-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="f1d42-110">使用移动 VR 呈现器：</span><span class="sxs-lookup"><span data-stu-id="f1d42-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="f1d42-111">滚动到“项目”部分，选择“目标硬件”，并将目标平台设置为“移动/平板电脑”</span><span class="sxs-lookup"><span data-stu-id="f1d42-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![移动目标设置](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="f1d42-113">禁用遮挡剔除：</span><span class="sxs-lookup"><span data-stu-id="f1d42-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="f1d42-114">滚动到“引擎”部分，选择“呈现”，展开“剔除”部分，取消选中“遮挡剔除”。</span><span class="sxs-lookup"><span data-stu-id="f1d42-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="f1d42-115">如果需要对呈现的详细场景进行遮挡剔除，建议在“引擎”>“呈现”中启用“支持软件遮挡剔除” 。</span><span class="sxs-lookup"><span data-stu-id="f1d42-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="f1d42-116">这使得 Unreal 可以在 CPU 上执行此操作，并避免 GPU 遮挡查询，后者在 HoloLens 2 上的执行效果不佳。</span><span class="sxs-lookup"><span data-stu-id="f1d42-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![禁用遮挡剔除](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="f1d42-118">使用移动多视图：</span><span class="sxs-lookup"><span data-stu-id="f1d42-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="f1d42-119">滚动到“引擎”部分，选择“呈现”，展开“VR”部分，同时启用“实例立体声”和“移动多视图”。</span><span class="sxs-lookup"><span data-stu-id="f1d42-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="f1d42-120">应取消选中移动端 HDR。</span><span class="sxs-lookup"><span data-stu-id="f1d42-120">Mobile HDR should be unchecked.</span></span>

![VR 渲染设置](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="f1d42-122">将“要渲染的最大 CSM 级联数”设置为 1，将“最大可移动聚光/点光”设置为 0   。</span><span class="sxs-lookup"><span data-stu-id="f1d42-122">Setting the **Maximum number of CSM cascades to render** to **1** and **Max Movable Spotlights / Point Lights** to **0**.</span></span> 
