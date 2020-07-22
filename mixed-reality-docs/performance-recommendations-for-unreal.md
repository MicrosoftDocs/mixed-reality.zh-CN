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
# <a name="performance-recommendations-for-unreal"></a>针对 Unreal 的性能建议

## <a name="overview"></a>概述

本文是在[针对混合现实的性能建议](understanding-performance-for-mixed-reality.md)中所述内容的基础上编写的，但重点介绍特定于 Unreal Engine 的功能。 建议在继续操作之前，先了解应用程序瓶颈和一般性能修复，以及有关分析和剖析混合现实应用的信息。

## <a name="recommended-unreal-project-settings"></a>建议的 Unreal 项目设置
可以在“编辑”>“项目设置”中找到以下每个设置。

1. 使用移动 VR 呈现器：
    * 滚动到“项目”部分，选择“目标硬件”，并将目标平台设置为“移动/平板电脑”

![移动目标设置](images/unreal/performance-recommendations-img-01.png)

2. 禁用遮挡剔除：
    * 滚动到“引擎”部分，选择“呈现”，展开“剔除”部分，取消选中“遮挡剔除”。
        + 如果需要对呈现的详细场景进行遮挡剔除，建议在“引擎”>“呈现”中启用“支持软件遮挡剔除” 。 这使得 Unreal 可以在 CPU 上执行此操作，并避免 GPU 遮挡查询，后者在 HoloLens 2 上的执行效果不佳。

![禁用遮挡剔除](images/unreal/performance-recommendations-img-02.png)

3. 使用移动多视图：
    * 滚动到“引擎”部分，选择“呈现”，展开“VR”部分，同时启用“实例立体声”和“移动多视图”。 应取消选中移动端 HDR。

![VR 渲染设置](images/unreal/performance-recommendations-img-03.png)

4. 将“要渲染的最大 CSM 级联数”设置为 1，将“最大可移动聚光/点光”设置为 0   。 
