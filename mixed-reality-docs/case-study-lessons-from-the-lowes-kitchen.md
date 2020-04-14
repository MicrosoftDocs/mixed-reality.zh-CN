---
title: 案例研究-来自 Lowe 厨房的课程
description: HoloLens 团队想要分享一些派生自 Lowe HoloLens 项目的最佳实践。
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，Lowe，HoloLens，厨房，案例研究
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278125"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="af6c3-104">案例研究-来自 Lowe 厨房的课程</span><span class="sxs-lookup"><span data-stu-id="af6c3-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="af6c3-105">HoloLens 团队想要分享一些派生自 Lowe HoloLens 项目的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="af6c3-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="af6c3-106">下面是 Lowe 的 HoloLens 计划的视频，其中演示了 Satya 的 2016 Ignite 主题。</span><span class="sxs-lookup"><span data-stu-id="af6c3-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="af6c3-107">Lowe 的 HoloLens 最佳实践</span><span class="sxs-lookup"><span data-stu-id="af6c3-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="af6c3-108">这两个视频覆盖了自2016年4月起，从 Lowe 的 HoloLens 试点派生的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="af6c3-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="af6c3-109">关键主题包括：</span><span class="sxs-lookup"><span data-stu-id="af6c3-109">The key topics are:</span></span>
* <span data-ttu-id="af6c3-110">最大化移动设备性能</span><span class="sxs-lookup"><span data-stu-id="af6c3-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="af6c3-111">创建具有完整全息帧的 UX 方法（第二个讨论）</span><span class="sxs-lookup"><span data-stu-id="af6c3-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="af6c3-112">精度对齐（第二个讨论）</span><span class="sxs-lookup"><span data-stu-id="af6c3-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="af6c3-113">共享全息体验（第二个讨论）</span><span class="sxs-lookup"><span data-stu-id="af6c3-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="af6c3-114">与客户交互（第二次交谈）</span><span class="sxs-lookup"><span data-stu-id="af6c3-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="af6c3-115">视频1</span><span class="sxs-lookup"><span data-stu-id="af6c3-115">Video 1</span></span>

<span data-ttu-id="af6c3-116">**最大化移动设备性能**HoloLens 是在设备中进行所有处理的 untethered 设备。</span><span class="sxs-lookup"><span data-stu-id="af6c3-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="af6c3-117">这需要移动平台，并且需要类似于创建移动应用程序的思维方式。</span><span class="sxs-lookup"><span data-stu-id="af6c3-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="af6c3-118">Microsoft 建议你的 HoloLens 应用程序维护60FPS，为你的用户提供可口体验。</span><span class="sxs-lookup"><span data-stu-id="af6c3-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="af6c3-119">低 FPS 会导致不稳定的全息影像。</span><span class="sxs-lookup"><span data-stu-id="af6c3-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="af6c3-120">在 HoloLens 上进行开发时，需要注意的一些最重要的事项是使用自定义着色器（在[Hololens 工具包](https://github.com/Microsoft/HoloToolkit-Unity)中免费提供）的资产优化/decimation。</span><span class="sxs-lookup"><span data-stu-id="af6c3-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="af6c3-121">另一个重要的考虑因素是从项目的最开始度量帧速率。</span><span class="sxs-lookup"><span data-stu-id="af6c3-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="af6c3-122">根据项目的不同，显示资产的顺序也可能是一个大参与者</span><span class="sxs-lookup"><span data-stu-id="af6c3-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="af6c3-123">视频2</span><span class="sxs-lookup"><span data-stu-id="af6c3-123">Video 2</span></span>

<span data-ttu-id="af6c3-124">**使用完整全息帧创建 UX 方法**了解影像在物理世界中的位置非常重要。</span><span class="sxs-lookup"><span data-stu-id="af6c3-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="af6c3-125">通过 Lowe，我们讨论了不同的 UX 方法，这些方法可帮助用户在出现全息影像的更大环境时，使其保持关闭状态。</span><span class="sxs-lookup"><span data-stu-id="af6c3-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="af6c3-126">**精度对齐**对于 Lowe 的应用场景，使全息影像与物理厨房实现精确对齐非常重要。</span><span class="sxs-lookup"><span data-stu-id="af6c3-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="af6c3-127">我们讨论的技术有助于确保结论用户的物理环境更改的体验。</span><span class="sxs-lookup"><span data-stu-id="af6c3-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="af6c3-128">**共享全息体验**使用方式是 Lowe 的体验的主要方式。</span><span class="sxs-lookup"><span data-stu-id="af6c3-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="af6c3-129">一个人可以更改台面，其他人将看到所做的更改。</span><span class="sxs-lookup"><span data-stu-id="af6c3-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="af6c3-130">我们称之为 "共享体验"。</span><span class="sxs-lookup"><span data-stu-id="af6c3-130">We called this "shared experiences".</span></span>

<span data-ttu-id="af6c3-131">**与客户交互**Lowe 的设计器不使用 HoloLens，但需要查看客户的情况。</span><span class="sxs-lookup"><span data-stu-id="af6c3-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="af6c3-132">本文介绍如何捕获客户在 UWP 应用程序上看到的内容。</span><span class="sxs-lookup"><span data-stu-id="af6c3-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
