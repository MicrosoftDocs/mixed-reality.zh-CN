---
title: 入门教程-1。 概述和目标
description: 本课程介绍如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: a311fbe377e4a2654c8905276417cf1104fc4754
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334342"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="a5880-105">1. 概述和目标</span><span class="sxs-lookup"><span data-stu-id="a5880-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="a5880-106">设备支持</span><span class="sxs-lookup"><span data-stu-id="a5880-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a5880-107"><strong>摘要</strong></span><span class="sxs-lookup"><span data-stu-id="a5880-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="a5880-108"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="a5880-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a5880-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="a5880-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="a5880-110"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="a5880-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="a5880-111">✔️</span><span class="sxs-lookup"><span data-stu-id="a5880-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="a5880-112">开始之前</span><span class="sxs-lookup"><span data-stu-id="a5880-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a5880-113">先决条件</span><span class="sxs-lookup"><span data-stu-id="a5880-113">Prerequisites</span></span>

* <span data-ttu-id="a5880-114">使用安装了正确的[工具](install-the-tools.md)配置的 WINDOWS 10 电脑</span><span class="sxs-lookup"><span data-stu-id="a5880-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="a5880-115">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="a5880-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a5880-116">一些基本C#编程功能</span><span class="sxs-lookup"><span data-stu-id="a5880-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="a5880-117">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="a5880-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
><span data-ttu-id="a5880-118">本系列教程需要<a href="https://unity3d.com/get-unity/download/archive" target="_blank">unity 2019.1</a> ，建议的版本是 unity 2019.1.14。</span><span class="sxs-lookup"><span data-stu-id="a5880-118">This tutorial series requires <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity 2019.1</a> and the recommended version is Unity 2019.1.14.</span></span> <span data-ttu-id="a5880-119">这将取代上述先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="a5880-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="a5880-120">下一课： 2. 初始化项目和首个应用程序</span><span class="sxs-lookup"><span data-stu-id="a5880-120">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
