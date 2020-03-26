---
title: 入门教程 - 1. 概述和目标
description: 本课程介绍如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36c12d82759b8ac2ba24aa9af37a096e0faf5fb5
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082049"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="7f7b8-105">1.概述和目标</span><span class="sxs-lookup"><span data-stu-id="7f7b8-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="7f7b8-106">设备支持</span><span class="sxs-lookup"><span data-stu-id="7f7b8-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7f7b8-107"><strong>课程</strong></span><span class="sxs-lookup"><span data-stu-id="7f7b8-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="7f7b8-108"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="7f7b8-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7f7b8-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="7f7b8-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="7f7b8-110"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="7f7b8-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="7f7b8-111">✔️</span><span class="sxs-lookup"><span data-stu-id="7f7b8-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="7f7b8-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="7f7b8-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7f7b8-113">必备条件</span><span class="sxs-lookup"><span data-stu-id="7f7b8-113">Prerequisites</span></span>

* <span data-ttu-id="7f7b8-114">一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="7f7b8-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="7f7b8-115">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="7f7b8-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="7f7b8-116">一些基本的 C# 编程功能</span><span class="sxs-lookup"><span data-stu-id="7f7b8-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="7f7b8-117">一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="7f7b8-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="7f7b8-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="7f7b8-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f7b8-119">建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。</span><span class="sxs-lookup"><span data-stu-id="7f7b8-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="7f7b8-120">这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="7f7b8-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="7f7b8-121">下一课：2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="7f7b8-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
