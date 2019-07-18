---
title: Spectator 视图
description: 从外部设备中可视化全息影像, 这是一种演示混合现实体验中的混合现实体验的方式。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, 摄像, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, demo, 记录
ms.openlocfilehash: 02088d7b218a25c72f2eb98ae24c85a90e6e5b86
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293610"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="c719c-104">HoloLens 和 HoloLens 2 的 Spectator 视图</span><span class="sxs-lookup"><span data-stu-id="c719c-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="c719c-106">概述</span><span class="sxs-lookup"><span data-stu-id="c719c-106">Overview</span></span>

<span data-ttu-id="c719c-107">在戴上 HoloLens 时, 我们经常忘记, 没有 it 人员的人不能绑住。</span><span class="sxs-lookup"><span data-stu-id="c719c-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="c719c-108">Spectator 视图允许其他人在二维屏幕上看到一个 HoloLens 用户在其世界中看到的内容。</span><span class="sxs-lookup"><span data-stu-id="c719c-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="c719c-109">Spectator 视图提供了一种快速且经济实惠的方法, 用于通过移动设备录制高清影像。</span><span class="sxs-lookup"><span data-stu-id="c719c-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="c719c-110">它还通过 DSLR 相机提供一种专业的影像质量记录。</span><span class="sxs-lookup"><span data-stu-id="c719c-110">It also offers a professional quality recording of holograms with DSLR cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="c719c-111">关键资源</span><span class="sxs-lookup"><span data-stu-id="c719c-111">Key Resources</span></span>

* [<span data-ttu-id="c719c-112">**GitHub 上的 Spectator 视图**</span><span class="sxs-lookup"><span data-stu-id="c719c-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="c719c-113">**种**</span><span class="sxs-lookup"><span data-stu-id="c719c-113">**Architecture**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [<span data-ttu-id="c719c-114">**范例**</span><span class="sxs-lookup"><span data-stu-id="c719c-114">**Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [<span data-ttu-id="c719c-115">**移动设置说明**</span><span class="sxs-lookup"><span data-stu-id="c719c-115">**Mobile Setup Instructions**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [<span data-ttu-id="c719c-116">**DSLR 安装说明**</span><span class="sxs-lookup"><span data-stu-id="c719c-116">**DSLR Setup Instructions**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.DSLR.md)

## <a name="use-cases"></a><span data-ttu-id="c719c-117">用例</span><span class="sxs-lookup"><span data-stu-id="c719c-117">Use Cases</span></span>
* <span data-ttu-id="c719c-118">可以使用 iPhone 或 Android 设备记录混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="c719c-118">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="c719c-119">以完整 HD 记录, 并将抗锯齿应用于全息影像甚至阴影。</span><span class="sxs-lookup"><span data-stu-id="c719c-119">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="c719c-120">这是一种经济高效的方法, 可用于捕获影像的视频。</span><span class="sxs-lookup"><span data-stu-id="c719c-120">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="c719c-121">直接从 iPhone 或 iPad, 将实时混合现实体验流式处理到 Apple TV 中, 无滞后!</span><span class="sxs-lookup"><span data-stu-id="c719c-121">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="c719c-122">与来宾分享体验:让非 HoloLens 用户直接从手机或平板电脑体验全息影像。</span><span class="sxs-lookup"><span data-stu-id="c719c-122">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="c719c-123">当前功能</span><span class="sxs-lookup"><span data-stu-id="c719c-123">Current Features</span></span>

* <span data-ttu-id="c719c-124">全息影像的空间同步, 因此所有人都能在完全相同的位置看到全息影像。</span><span class="sxs-lookup"><span data-stu-id="c719c-124">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="c719c-125">iOS (启用 ARKit 的设备) 和 Android (启用 ARCore 的设备) 支持。</span><span class="sxs-lookup"><span data-stu-id="c719c-125">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="c719c-126">多个 iOS 来宾。</span><span class="sxs-lookup"><span data-stu-id="c719c-126">Multiple iOS guests.</span></span>
<span data-ttu-id="c719c-127">视频 + 全息影像 + 环境音效 + 全息影像声音。</span><span class="sxs-lookup"><span data-stu-id="c719c-127">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="c719c-128">共享工作表, 以便您可以保存视频、向其发送电子邮件或与其他支持应用共享。</span><span class="sxs-lookup"><span data-stu-id="c719c-128">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="c719c-129">![](images/SpecViewPhoneDemo.jpg)
标记标记](images/hololensspectatorview-500px.jpg) ![ ![](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="c719c-129">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="c719c-130">下表显示了不同的 Spectator 视图功能及其功能。</span><span class="sxs-lookup"><span data-stu-id="c719c-130">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="c719c-131">选择最适合您的视频录制需求的选项:</span><span class="sxs-lookup"><span data-stu-id="c719c-131">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="c719c-132">移动电话</span><span class="sxs-lookup"><span data-stu-id="c719c-132">Mobile</span></span>                  |                    <span data-ttu-id="c719c-133">DSLR 照相机</span><span class="sxs-lookup"><span data-stu-id="c719c-133">DSLR Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="c719c-134">HD 质量</span><span class="sxs-lookup"><span data-stu-id="c719c-134">HD quality</span></span>                           |         <span data-ttu-id="c719c-135">完整高清</span><span class="sxs-lookup"><span data-stu-id="c719c-135">Full HD</span></span>         |        <span data-ttu-id="c719c-136">专业质量与 (由 DSLR 确定)</span><span class="sxs-lookup"><span data-stu-id="c719c-136">Professional quality filming (as determined by DSLR)</span></span>      |
| <span data-ttu-id="c719c-137">轻松移动相机</span><span class="sxs-lookup"><span data-stu-id="c719c-137">Easy camera movement</span></span>                 |            <span data-ttu-id="c719c-138">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-138">✔</span></span>            |                      <span data-ttu-id="c719c-139">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-139">✔</span></span>                      |
| <span data-ttu-id="c719c-140">第三人员视图</span><span class="sxs-lookup"><span data-stu-id="c719c-140">Third-person view</span></span>                    |            <span data-ttu-id="c719c-141">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-141">✔</span></span>            |                      <span data-ttu-id="c719c-142">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-142">✔</span></span>                      |
| <span data-ttu-id="c719c-143">可以流式传输到屏幕</span><span class="sxs-lookup"><span data-stu-id="c719c-143">Can be streamed to screens</span></span>           |            <span data-ttu-id="c719c-144">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-144">✔</span></span>            |                      <span data-ttu-id="c719c-145">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-145">✔</span></span>                      |
| <span data-ttu-id="c719c-146">可移植</span><span class="sxs-lookup"><span data-stu-id="c719c-146">Portable</span></span>                             |            <span data-ttu-id="c719c-147">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-147">✔</span></span>            |                                             |
| <span data-ttu-id="c719c-148">无线</span><span class="sxs-lookup"><span data-stu-id="c719c-148">Wireless</span></span>                             |            <span data-ttu-id="c719c-149">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-149">✔</span></span>            |                                             |
| <span data-ttu-id="c719c-150">其他必需硬件</span><span class="sxs-lookup"><span data-stu-id="c719c-150">Additional required hardware</span></span>         |     <span data-ttu-id="c719c-151">Android 手机, iPhone</span><span class="sxs-lookup"><span data-stu-id="c719c-151">Android phone, iPhone</span></span>    | <span data-ttu-id="c719c-152">HoloLens + Rig + 架 + DSLR + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="c719c-152">HoloLens + Rig + Tripod + DSLR + PC + Unity</span></span> |
| <span data-ttu-id="c719c-153">硬件投资</span><span class="sxs-lookup"><span data-stu-id="c719c-153">Hardware investment</span></span>                  |           <span data-ttu-id="c719c-154">低</span><span class="sxs-lookup"><span data-stu-id="c719c-154">Low</span></span>            |                     <span data-ttu-id="c719c-155">高</span><span class="sxs-lookup"><span data-stu-id="c719c-155">High</span></span>                    |
| <span data-ttu-id="c719c-156">跨平台</span><span class="sxs-lookup"><span data-stu-id="c719c-156">Cross-platform</span></span>                       |           <span data-ttu-id="c719c-157">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="c719c-157">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="c719c-158">同步内容</span><span class="sxs-lookup"><span data-stu-id="c719c-158">Synchronized content</span></span>                 |            <span data-ttu-id="c719c-159">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-159">✔</span></span>            |                      <span data-ttu-id="c719c-160">✔</span><span class="sxs-lookup"><span data-stu-id="c719c-160">✔</span></span>                      |
| <span data-ttu-id="c719c-161">运行时安装持续时间</span><span class="sxs-lookup"><span data-stu-id="c719c-161">Runtime setup duration</span></span>               |         <span data-ttu-id="c719c-162">速递</span><span class="sxs-lookup"><span data-stu-id="c719c-162">Instant</span></span>          |                     <span data-ttu-id="c719c-163">慢速</span><span class="sxs-lookup"><span data-stu-id="c719c-163">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="c719c-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="c719c-164">See also</span></span>

* [<span data-ttu-id="c719c-165">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="c719c-165">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="c719c-166">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="c719c-166">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="c719c-167">混合现实中的共享体验</span><span class="sxs-lookup"><span data-stu-id="c719c-167">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
