---
title: MR 学习基本模块简介
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 389a23129d4dfc5819cdc45d071b678e3792089d
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523157"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="bfc71-104">1.概述和目标</span><span class="sxs-lookup"><span data-stu-id="bfc71-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="bfc71-105">设备支持</span><span class="sxs-lookup"><span data-stu-id="bfc71-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bfc71-106"><strong>课程</strong></span><span class="sxs-lookup"><span data-stu-id="bfc71-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="bfc71-107"><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></span><span class="sxs-lookup"><span data-stu-id="bfc71-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="bfc71-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="bfc71-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="bfc71-109"><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></span><span class="sxs-lookup"><span data-stu-id="bfc71-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="bfc71-110">❌</span><span class="sxs-lookup"><span data-stu-id="bfc71-110">❌</span></span></td>
        <td><span data-ttu-id="bfc71-111">✔️</span><span class="sxs-lookup"><span data-stu-id="bfc71-111">✔️</span></span></td>
        <td><span data-ttu-id="bfc71-112">❌</span><span class="sxs-lookup"><span data-stu-id="bfc71-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="bfc71-113">开始之前</span><span class="sxs-lookup"><span data-stu-id="bfc71-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="bfc71-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="bfc71-114">Prerequisites</span></span>

* <span data-ttu-id="bfc71-115">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="bfc71-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="bfc71-116">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="bfc71-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="bfc71-117">一些基本C#编程功能。</span><span class="sxs-lookup"><span data-stu-id="bfc71-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="bfc71-118">HoloLens 2 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="bfc71-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
