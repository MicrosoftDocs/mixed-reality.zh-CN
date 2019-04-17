---
title: 案例研究-从 Lowe 的厨房获得的教训
description: HoloLens 团队想要分享一些衍生 Lowe 的 HoloLens 项目的最佳实践。
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、 Lowe 的、 HoloLens、 厨房、 案例研究
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591750"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="74453-104">案例研究-从 Lowe 的厨房获得的教训</span><span class="sxs-lookup"><span data-stu-id="74453-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="74453-105">HoloLens 团队想要分享一些衍生 Lowe 的 HoloLens 项目的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="74453-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="74453-106">下面是投影 Lowe 的 HoloLens 的视频演示了 Satya 的 2016 Ignite 主题。</span><span class="sxs-lookup"><span data-stu-id="74453-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="74453-107">Lowe 的 HoloLens 最佳实践</span><span class="sxs-lookup"><span data-stu-id="74453-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="74453-108">两个视频介绍衍生自 2016 年 4 月以来一直驻留在两个 Lowe 存储 Lowe 的 HoloLens 试验的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="74453-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="74453-109">关键主题包括：</span><span class="sxs-lookup"><span data-stu-id="74453-109">The key topics are:</span></span>
* <span data-ttu-id="74453-110">最大限度地移动设备的性能</span><span class="sxs-lookup"><span data-stu-id="74453-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="74453-111">创建具有完整 holographic 帧 UX 方法 （第 2 个对话）</span><span class="sxs-lookup"><span data-stu-id="74453-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="74453-112">精度的对齐方式 （第 2 个对话）</span><span class="sxs-lookup"><span data-stu-id="74453-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="74453-113">共享 holographic 体验 （第 2 个对话）</span><span class="sxs-lookup"><span data-stu-id="74453-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="74453-114">与客户交互 （第 2 个对话）</span><span class="sxs-lookup"><span data-stu-id="74453-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="74453-115">视频 1</span><span class="sxs-lookup"><span data-stu-id="74453-115">Video 1</span></span>

<span data-ttu-id="74453-116">**使移动设备的性能最大化**HoloLens 是无约束的设备的设备中发生的所有处理。</span><span class="sxs-lookup"><span data-stu-id="74453-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="74453-117">这需要移动平台并且思维方式类似于创建移动应用程序。</span><span class="sxs-lookup"><span data-stu-id="74453-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="74453-118">Microsoft 建议您 HoloLens 的应用程序维护 60 FPS，若要为用户提供一种美味体验。</span><span class="sxs-lookup"><span data-stu-id="74453-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="74453-119">具有较低的每秒帧数可能会导致不稳定全息。</span><span class="sxs-lookup"><span data-stu-id="74453-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="74453-120">一些最重要的事情，若要查看在 HoloLens 上进行开发时资产优化/抽取，使用自定义着色器 (免费提供[HoloLens 工具包](https://github.com/Microsoft/HoloToolkit-Unity))。</span><span class="sxs-lookup"><span data-stu-id="74453-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="74453-121">另一个重要的考虑因素是项目的度量值从一开始您的帧速率。</span><span class="sxs-lookup"><span data-stu-id="74453-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="74453-122">具体取决于该项目，显示你的资产的顺序也可以是大参与者</span><span class="sxs-lookup"><span data-stu-id="74453-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="74453-123">视频 2</span><span class="sxs-lookup"><span data-stu-id="74453-123">Video 2</span></span>

<span data-ttu-id="74453-124">**创建具有完整 holographic 帧 UX 方法**务必了解全息物理世界中的位置。</span><span class="sxs-lookup"><span data-stu-id="74453-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="74453-125">使用 Lowe 的我们讨论有关帮助的用户注册体验全息关闭同时仍可以查看全息的较大环境的不同用户体验方法。</span><span class="sxs-lookup"><span data-stu-id="74453-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="74453-126">**精度对齐**为 Lowe 的方案中，它是至关重要的体验，没有到物理厨房全息精度对齐方式。</span><span class="sxs-lookup"><span data-stu-id="74453-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="74453-127">我们将讨论的技术有助于确保使其物理环境已更改的用户的体验。</span><span class="sxs-lookup"><span data-stu-id="74453-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="74453-128">**共享 holographic 体验**将紧密结合起来都使用 Lowe 的体验的主要方法。</span><span class="sxs-lookup"><span data-stu-id="74453-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="74453-129">一个人可以更改台面上，其他人将看到所做的更改。</span><span class="sxs-lookup"><span data-stu-id="74453-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="74453-130">我们调用了此"共享体验"。</span><span class="sxs-lookup"><span data-stu-id="74453-130">We called this "shared experiences".</span></span>

<span data-ttu-id="74453-131">**与客户交互**Lowe 的设计器不使用 HoloLens，但他们需要查看客户看到的内容。</span><span class="sxs-lookup"><span data-stu-id="74453-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="74453-132">我们演示如何捕获客户 UWP 应用程序上看到的内容。</span><span class="sxs-lookup"><span data-stu-id="74453-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
