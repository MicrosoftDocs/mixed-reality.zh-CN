---
title: MR 学习基本模块简介
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: d4220527a7de8e596f2825fd9d199d536510b972
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148627"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="2c172-104">MR 学习基本模块概述和目标</span><span class="sxs-lookup"><span data-stu-id="2c172-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="2c172-105">设备支持</span><span class="sxs-lookup"><span data-stu-id="2c172-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2c172-106"><strong>课程</strong></span><span class="sxs-lookup"><span data-stu-id="2c172-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="2c172-107"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="2c172-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2c172-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="2c172-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="2c172-109"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="2c172-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="2c172-110">❌</span><span class="sxs-lookup"><span data-stu-id="2c172-110">❌</span></span></td>
        <td><span data-ttu-id="2c172-111">✔️</span><span class="sxs-lookup"><span data-stu-id="2c172-111">✔️</span></span></td>
        <td><span data-ttu-id="2c172-112">❌</span><span class="sxs-lookup"><span data-stu-id="2c172-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="2c172-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="2c172-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="2c172-114">系统必备</span><span class="sxs-lookup"><span data-stu-id="2c172-114">Prerequisites</span></span>

* <span data-ttu-id="2c172-115">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="2c172-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="2c172-116">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="2c172-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="2c172-117">一些基本C#编程功能。</span><span class="sxs-lookup"><span data-stu-id="2c172-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="2c172-118">HoloLens 2 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="2c172-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
