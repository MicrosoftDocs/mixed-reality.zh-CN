---
title: Spectator 视图
description: 从外部设备中可视化全息影像, 这是一种演示混合现实体验中的混合现实体验的方式。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, 摄像, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, demo, 记录
ms.openlocfilehash: 708ed694af3769f16d5dce0595e026f9a348d754
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047177"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="10851-104">HoloLens 和 HoloLens 2 的 Spectator 视图</span><span class="sxs-lookup"><span data-stu-id="10851-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="10851-106">概述</span><span class="sxs-lookup"><span data-stu-id="10851-106">Overview</span></span>

<span data-ttu-id="10851-107">在戴上 HoloLens 时, 我们经常忘记, 没有 it 人员的人不能绑住。</span><span class="sxs-lookup"><span data-stu-id="10851-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="10851-108">Spectator 视图允许其他人在二维屏幕上看到一个 HoloLens 用户在其世界中看到的内容。</span><span class="sxs-lookup"><span data-stu-id="10851-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="10851-109">Spectator 视图提供了一种快速且经济实惠的方法, 用于通过移动设备录制高清影像。</span><span class="sxs-lookup"><span data-stu-id="10851-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="10851-110">它还通过视频相机提供一种专业的影像质量记录。</span><span class="sxs-lookup"><span data-stu-id="10851-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="10851-111">关键资源</span><span class="sxs-lookup"><span data-stu-id="10851-111">Key Resources</span></span>

* [<span data-ttu-id="10851-112">**GitHub 上的 Spectator 视图**</span><span class="sxs-lookup"><span data-stu-id="10851-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="10851-113">**Spectator 视图文档**</span><span class="sxs-lookup"><span data-stu-id="10851-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="10851-114">**Spectator 视图示例**</span><span class="sxs-lookup"><span data-stu-id="10851-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="10851-115">用例</span><span class="sxs-lookup"><span data-stu-id="10851-115">Use Cases</span></span>
* <span data-ttu-id="10851-116">可以使用 iPhone 或 Android 设备记录混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="10851-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="10851-117">以完整 HD 记录, 并将抗锯齿应用于全息影像甚至阴影。</span><span class="sxs-lookup"><span data-stu-id="10851-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="10851-118">这是一种经济高效的方法, 可用于捕获影像的视频。</span><span class="sxs-lookup"><span data-stu-id="10851-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="10851-119">直接从 iPhone 或 iPad, 将实时混合现实体验流式处理到 Apple TV 中, 无滞后!</span><span class="sxs-lookup"><span data-stu-id="10851-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="10851-120">与来宾分享体验:让非 HoloLens 用户直接从手机或平板电脑体验全息影像。</span><span class="sxs-lookup"><span data-stu-id="10851-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="10851-121">当前功能</span><span class="sxs-lookup"><span data-stu-id="10851-121">Current Features</span></span>

* <span data-ttu-id="10851-122">全息影像的空间同步, 因此所有人都能在完全相同的位置看到全息影像。</span><span class="sxs-lookup"><span data-stu-id="10851-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="10851-123">iOS (启用 ARKit 的设备) 和 Android (启用 ARCore 的设备) 支持。</span><span class="sxs-lookup"><span data-stu-id="10851-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="10851-124">多个 iOS 来宾。</span><span class="sxs-lookup"><span data-stu-id="10851-124">Multiple iOS guests.</span></span>
<span data-ttu-id="10851-125">视频 + 全息影像 + 环境音效 + 全息影像声音。</span><span class="sxs-lookup"><span data-stu-id="10851-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="10851-126">共享工作表, 以便您可以保存视频、向其发送电子邮件或与其他支持应用共享。</span><span class="sxs-lookup"><span data-stu-id="10851-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="10851-127">![](images/SpecViewPhoneDemo.jpg)
标记标记](images/hololensspectatorview-500px.jpg) ![ ![](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="10851-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="10851-128">下表显示了不同的 Spectator 视图功能及其功能。</span><span class="sxs-lookup"><span data-stu-id="10851-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="10851-129">选择最适合您的视频录制需求的选项:</span><span class="sxs-lookup"><span data-stu-id="10851-129">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="10851-130">移动电话</span><span class="sxs-lookup"><span data-stu-id="10851-130">Mobile</span></span>                  |                    <span data-ttu-id="10851-131">视频摄像机</span><span class="sxs-lookup"><span data-stu-id="10851-131">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="10851-132">HD 质量</span><span class="sxs-lookup"><span data-stu-id="10851-132">HD quality</span></span>                           |         <span data-ttu-id="10851-133">完整高清</span><span class="sxs-lookup"><span data-stu-id="10851-133">Full HD</span></span>         |        <span data-ttu-id="10851-134">专业质量与 (由视频相机确定)</span><span class="sxs-lookup"><span data-stu-id="10851-134">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="10851-135">轻松移动相机</span><span class="sxs-lookup"><span data-stu-id="10851-135">Easy camera movement</span></span>                 |            <span data-ttu-id="10851-136">✔</span><span class="sxs-lookup"><span data-stu-id="10851-136">✔</span></span>            |                      <span data-ttu-id="10851-137">✔</span><span class="sxs-lookup"><span data-stu-id="10851-137">✔</span></span>                      |
| <span data-ttu-id="10851-138">第三人员视图</span><span class="sxs-lookup"><span data-stu-id="10851-138">Third-person view</span></span>                    |            <span data-ttu-id="10851-139">✔</span><span class="sxs-lookup"><span data-stu-id="10851-139">✔</span></span>            |                      <span data-ttu-id="10851-140">✔</span><span class="sxs-lookup"><span data-stu-id="10851-140">✔</span></span>                      |
| <span data-ttu-id="10851-141">可以流式传输到屏幕</span><span class="sxs-lookup"><span data-stu-id="10851-141">Can be streamed to screens</span></span>           |            <span data-ttu-id="10851-142">✔</span><span class="sxs-lookup"><span data-stu-id="10851-142">✔</span></span>            |                      <span data-ttu-id="10851-143">✔</span><span class="sxs-lookup"><span data-stu-id="10851-143">✔</span></span>                      |
| <span data-ttu-id="10851-144">可移植</span><span class="sxs-lookup"><span data-stu-id="10851-144">Portable</span></span>                             |            <span data-ttu-id="10851-145">✔</span><span class="sxs-lookup"><span data-stu-id="10851-145">✔</span></span>            |                                             |
| <span data-ttu-id="10851-146">无线</span><span class="sxs-lookup"><span data-stu-id="10851-146">Wireless</span></span>                             |            <span data-ttu-id="10851-147">✔</span><span class="sxs-lookup"><span data-stu-id="10851-147">✔</span></span>            |                                             |
| <span data-ttu-id="10851-148">其他必需硬件</span><span class="sxs-lookup"><span data-stu-id="10851-148">Additional required hardware</span></span>         |     <span data-ttu-id="10851-149">Android 手机, iPhone</span><span class="sxs-lookup"><span data-stu-id="10851-149">Android phone, iPhone</span></span>    | <span data-ttu-id="10851-150">HoloLens + Rig + "装备 + 视频相机 + PC + Unity"</span><span class="sxs-lookup"><span data-stu-id="10851-150">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="10851-151">硬件投资</span><span class="sxs-lookup"><span data-stu-id="10851-151">Hardware investment</span></span>                  |           <span data-ttu-id="10851-152">低</span><span class="sxs-lookup"><span data-stu-id="10851-152">Low</span></span>            |                     <span data-ttu-id="10851-153">高</span><span class="sxs-lookup"><span data-stu-id="10851-153">High</span></span>                    |
| <span data-ttu-id="10851-154">跨平台</span><span class="sxs-lookup"><span data-stu-id="10851-154">Cross-platform</span></span>                       |           <span data-ttu-id="10851-155">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="10851-155">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="10851-156">同步内容</span><span class="sxs-lookup"><span data-stu-id="10851-156">Synchronized content</span></span>                 |            <span data-ttu-id="10851-157">✔</span><span class="sxs-lookup"><span data-stu-id="10851-157">✔</span></span>            |                      <span data-ttu-id="10851-158">✔</span><span class="sxs-lookup"><span data-stu-id="10851-158">✔</span></span>                      |
| <span data-ttu-id="10851-159">运行时安装持续时间</span><span class="sxs-lookup"><span data-stu-id="10851-159">Runtime setup duration</span></span>               |         <span data-ttu-id="10851-160">速递</span><span class="sxs-lookup"><span data-stu-id="10851-160">Instant</span></span>          |                     <span data-ttu-id="10851-161">慢速</span><span class="sxs-lookup"><span data-stu-id="10851-161">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="10851-162">请参阅</span><span class="sxs-lookup"><span data-stu-id="10851-162">See also</span></span>

* [<span data-ttu-id="10851-163">混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="10851-163">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="10851-164">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="10851-164">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="10851-165">混合现实中的共享体验</span><span class="sxs-lookup"><span data-stu-id="10851-165">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
