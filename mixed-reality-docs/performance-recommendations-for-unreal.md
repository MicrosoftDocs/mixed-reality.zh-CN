---
title: 针对 Unreal 的性能建议
description: Unreal 中混合现实应用获得最佳性能的建议
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 性能, 优化, 设置, 文档
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840196"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="aedf8-104">针对 Unreal 的性能建议</span><span class="sxs-lookup"><span data-stu-id="aedf8-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="aedf8-105">本文是在[针对混合现实的性能建议](understanding-performance-for-mixed-reality.md)中所述内容的基础上编写的，但重点介绍特定于 Unreal Engine 环境的知识。</span><span class="sxs-lookup"><span data-stu-id="aedf8-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unreal Engine environment.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="aedf8-106">建议的 Unreal 项目设置</span><span class="sxs-lookup"><span data-stu-id="aedf8-106">Recommended Unreal project settings</span></span>

- <span data-ttu-id="aedf8-107">使用移动 VR 渲染器 - 在项目设置中，确保将目标平台设置为“项目 – 目标硬件”下的“移动/平板电脑”</span><span class="sxs-lookup"><span data-stu-id="aedf8-107">Use the mobile VR renderer- in your project settings, ensure your target platform is set to "Mobile/Tablet" under "Project – Target Hardware"</span></span>
- <span data-ttu-id="aedf8-108">禁用遮挡剔除 - 在“引擎 - 渲染”下的“剔除”部分，取消选中“遮挡剔除”</span><span class="sxs-lookup"><span data-stu-id="aedf8-108">Disable occlusion culling- under "Engine – Rendering" in the "Culling" section, uncheck "Occlusion Culling"</span></span>
    + <span data-ttu-id="aedf8-109">如果因为需要渲染非常详细的场景而需要遮挡剔除，建议在“引擎 - 渲染”下启用“支持软件遮挡剔除”。</span><span class="sxs-lookup"><span data-stu-id="aedf8-109">If occlusion culling is required because a very detailed scene needs to be rendered, it is recommended that "Support Software Occlusion Culling" is enabled Under "Engine – Rendering".</span></span> <span data-ttu-id="aedf8-110">这允许 Unreal 在 CPU 上执行遮挡剔除，并避免 GPU 遮挡查询，后者在 HoloLens 2 上的执行效果不佳。</span><span class="sxs-lookup"><span data-stu-id="aedf8-110">This allows Unreal to do occlusion culling on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
- <span data-ttu-id="aedf8-111">在“VR”类别的“引擎 - 渲染”下，启用“实例立体声”和“移动多视图”。</span><span class="sxs-lookup"><span data-stu-id="aedf8-111">Enable both "Instanced Stereo" and "Mobile Multi-View" under "Engine – Rendering" in the "VR" category.</span></span> <span data-ttu-id="aedf8-112">可能需要取消选中“移动后处理”才能选中“移动多视图”</span><span class="sxs-lookup"><span data-stu-id="aedf8-112">You may need to uncheck "Mobile Post-Processing" in order to be able to check "Mobile Multi-View"</span></span>
