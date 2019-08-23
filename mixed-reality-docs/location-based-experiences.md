---
title: 具有 Windows Mixed Reality 的基于位置的娱乐
description: 获取对 Unity 中的基础全息本机对象的访问权限。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: mixed reality, vr, lbe, location
ms.openlocfilehash: e23d17ff2b07c636c98a9f19a5dd20f4dc558bf7
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69983395"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a><span data-ttu-id="92555-104">具有 Windows Mixed Reality 的基于位置的娱乐</span><span class="sxs-lookup"><span data-stu-id="92555-104">Location Based Entertainment with Windows Mixed Reality</span></span>

<span data-ttu-id="92555-105">在过去几年中, 我们在基于地点的娱乐类别中观察到了惊人的增长和创新。</span><span class="sxs-lookup"><span data-stu-id="92555-105">In the last couple of years, we have witnessed an incredible amount of growth and innovation in the Location Based Entertainment category.</span></span> <span data-ttu-id="92555-106">传统的会场 (如主题公园和 theatres) 已开始提供沉浸式多玩家体验, 作为现有搭乘和安装的免费体验。</span><span class="sxs-lookup"><span data-stu-id="92555-106">Traditional venues like theme parks and theatres have started offering immersive, multi-player experiences as complimentary experiences to existing rides and installations.</span></span> <span data-ttu-id="92555-107">新的操作员和会场为面向大众带来了独特的多 sensorial、多玩家体验。</span><span class="sxs-lookup"><span data-stu-id="92555-107">New operators and venues are bringing unique multi-sensorial, multi-player experiences at an attractive price to the masses.</span></span> <span data-ttu-id="92555-108">所有这些经验都是通过推送信封来实现混合现实。</span><span class="sxs-lookup"><span data-stu-id="92555-108">All of these experiences are pushing the envelope for what’s possible with mixed reality.</span></span>

<span data-ttu-id="92555-109">本文档是在基于位置的娱乐类别中开始使用 Windows Mixed Reality 的指南。</span><span class="sxs-lookup"><span data-stu-id="92555-109">This document is a guide to get started with Windows Mixed Reality in the Location Based Entertainment category.</span></span> <span data-ttu-id="92555-110">以下指南可能还适用于超出娱乐的位置体验, 例如培训、产品设计或其他用例。</span><span class="sxs-lookup"><span data-stu-id="92555-110">The guidance below may additionally be applicable to location-based experiences beyond entertainment such as training, product design or other use cases.</span></span>

## <a name="engineering-faq"></a><span data-ttu-id="92555-111">工程常见问题</span><span class="sxs-lookup"><span data-stu-id="92555-111">Engineering FAQ</span></span>

### <a name="hardware"></a><span data-ttu-id="92555-112">硬件</span><span class="sxs-lookup"><span data-stu-id="92555-112">Hardware</span></span>

<span data-ttu-id="92555-113">**:Microsoft 及其合作伙伴提供了哪些可在我的设置中使用的硬件？**</span><span class="sxs-lookup"><span data-stu-id="92555-113">**Q: What hardware is available from Microsoft and its partners that I can use in my setup?**</span></span>

<span data-ttu-id="92555-114">答：Microsoft 及其 OEM 合作伙伴提供了一套诱人的设备, 可根据需要进行选择。</span><span class="sxs-lookup"><span data-stu-id="92555-114">A: Microsoft and its OEM partners offer a compelling portfolio of devices to choose from depending on your needs.</span></span>  

<span data-ttu-id="92555-115">如果你向客户提供的体验需要虚拟现实耳机, 则 HP、Samsung 和 Acer 的以下市场耳机都非常合适。</span><span class="sxs-lookup"><span data-stu-id="92555-115">If the experiences you’re providing to your customers require virtual reality headsets, the following in-market headsets from HP, Samsung and Acer are a great fit.</span></span> <span data-ttu-id="92555-116">每个耳机都有其各自的不同属性。</span><span class="sxs-lookup"><span data-stu-id="92555-116">Each headset has their own differentiated attributes.</span></span> <span data-ttu-id="92555-117">以下各项的详细信息。</span><span class="sxs-lookup"><span data-stu-id="92555-117">More details on each below.</span></span>

<span data-ttu-id="92555-118">HP 回音:[详细信息](https://hp.com/go/Reverbpro)</span><span class="sxs-lookup"><span data-stu-id="92555-118">HP Reverb: [Details](https://hp.com/go/Reverbpro)</span></span>

<span data-ttu-id="92555-119">Samsung 太空 +:[详细信息](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span><span class="sxs-lookup"><span data-stu-id="92555-119">Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span></span>

<span data-ttu-id="92555-120">Acer:[详细信息](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span><span class="sxs-lookup"><span data-stu-id="92555-120">Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span></span>

<span data-ttu-id="92555-121">如果你的位置专门从事需要使用 "查看-通过" 耳机的混合或增加的现实体验, 则可以购买 Microsoft HoloLens 2 (现已打开, 用于提前订购)。</span><span class="sxs-lookup"><span data-stu-id="92555-121">If your location specializes in mixed or augmented reality experiences requiring the use of a see-through headset, you can procure the Microsoft HoloLens 2 (now open for pre-order interest).</span></span>  

<span data-ttu-id="92555-122">HoloLens 2:[预处理利息](https://www.microsoft.com/en-us/hololens/buy)</span><span class="sxs-lookup"><span data-stu-id="92555-122">HoloLens 2: [Pre-order interest](https://www.microsoft.com/en-us/hololens/buy)</span></span>

<span data-ttu-id="92555-123">如果你正在试验需要高级计算机视觉、语音和正文跟踪的体验, 你可能会发现, Azure Kinect 深色适用于你的需求。</span><span class="sxs-lookup"><span data-stu-id="92555-123">If you’re experimenting with experiences that require advanced computer vision, speech and body tracking, you may find the Azure Kinect DK a fit for your needs.</span></span>  

<span data-ttu-id="92555-124">Azure Kinect:[详细信息](https://azure.microsoft.com/en-us/services/kinect-dk/)</span><span class="sxs-lookup"><span data-stu-id="92555-124">Azure Kinect: [Details](https://azure.microsoft.com/en-us/services/kinect-dk/)</span></span>

<span data-ttu-id="92555-125">**:我可以使用哪些背包电脑组合来运行我的电脑-受限 VR 体验？**</span><span class="sxs-lookup"><span data-stu-id="92555-125">**Q: What is the portfolio of backpack PCs I can use to run my PC-tethered VR experiences?**</span></span>

<span data-ttu-id="92555-126">对于电脑受限 VR 体验, 我们的 Oem 提供了令人难以置信地选择的背包 Pc。</span><span class="sxs-lookup"><span data-stu-id="92555-126">For PC-tethered VR experiences, our OEMs offer an incredible selection of backpack PCs built exactly for that need.</span></span>

<span data-ttu-id="92555-127">HP 刚刚启动了其 HP VR 背包 G2, 这是世界上最强大的可穿戴 PC –为自由漫游体验进行了优化, 现在, 在内部使用 RTX 2080 GPU 可提高 30% 的电量。</span><span class="sxs-lookup"><span data-stu-id="92555-127">HP just launched their HP VR backpack G2, the world’s most powerful wearable PC – optimized for free-roam experiences, now with 30% more power with an RTX 2080 GPU inside.</span></span> [<span data-ttu-id="92555-128">详细信息</span><span class="sxs-lookup"><span data-stu-id="92555-128">Details</span></span>](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a><span data-ttu-id="92555-129">安装</span><span class="sxs-lookup"><span data-stu-id="92555-129">Setup</span></span>

<span data-ttu-id="92555-130">**:如何更轻松地配置安装并为 LBE 自定义混合现实门户？**</span><span class="sxs-lookup"><span data-stu-id="92555-130">**Q: How can I more easily configure setup and customize the Mixed Reality Portal for LBE?**</span></span>

>[!NOTE]
><span data-ttu-id="92555-131">此功能需要2000.19061.1011.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="92555-131">This feature requires version 2000.19061.1011.0 or greater.</span></span>  

<span data-ttu-id="92555-132">你可能会发现, 你需要对混合现实门户进行更多的自定义, 而不是通常通过用于将应用部署到展台或自定义体验的应用使用。</span><span class="sxs-lookup"><span data-stu-id="92555-132">You may find that you need more customization of Mixed Reality Portal than is normally available through the app for deploying apps to kiosks or customized experiences.</span></span> <span data-ttu-id="92555-133">混合现实门户的最新7月更新支持多个高级设置, 这些高级设置可以通过配置文件执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="92555-133">The latest July update of Mixed Reality Portal supports several advanced settings that can be via a configuration file to do the following:</span></span>  

<span data-ttu-id="92555-134">允许故障系统检查–在完成安装程序之前, 安装过程通常会检查 PC 与 Windows Mixed Reality 的兼容性。</span><span class="sxs-lookup"><span data-stu-id="92555-134">Allow failed system checks – normally the setup process checks the PC for compatibility with Windows Mixed Reality before completing setup.</span></span> <span data-ttu-id="92555-135">如果出现兼容性问题, 则在尝试运行 Windows Mixed Reality 时, 绕过这种情况可能会导致问题。</span><span class="sxs-lookup"><span data-stu-id="92555-135">Bypassing this may cause issues when trying to run Windows Mixed Reality if there are compatibility issues.</span></span>  

<span data-ttu-id="92555-136">跳过设备辅助应用– DCA 提供制造商提供的耳机特定的设置步骤, 并允许更新耳机固件。</span><span class="sxs-lookup"><span data-stu-id="92555-136">Skip Device Companion App – the DCA provides headset-specific setup steps provided by the manufacturer and allows for updating the headset’s firmware.</span></span>  

<span data-ttu-id="92555-137">跳过房间安装-不会提示创建房间边界, 你可以直接转到处于固定/放置模式的耳机。</span><span class="sxs-lookup"><span data-stu-id="92555-137">Skip room setup – instead of being prompted to create a room boundary, you can proceed directly into the headset in Seated/Standing mode.</span></span>  

<span data-ttu-id="92555-138">跳过从应用商店安装应用-普通安装程序将安装多个应用商店应用, 包括3D 查看器和 Edge 360 查看器加载项。</span><span class="sxs-lookup"><span data-stu-id="92555-138">Skip installing apps from the Store - normal setup installs several Store apps including 3D Viewer and the Edge 360 Viewer add-on.</span></span> <span data-ttu-id="92555-139">这会跳过这些应用的安装, 但可能缺少设备功能。</span><span class="sxs-lookup"><span data-stu-id="92555-139">This will skip the install of these apps, but you may be missing device functionality.</span></span>  

<span data-ttu-id="92555-140">全屏显示预览–混合现实门户将默认为在使用耳机时在台式计算机上全屏显示耳机预览。</span><span class="sxs-lookup"><span data-stu-id="92555-140">Show preview in full screen – Mixed Reality Portal will default to showing the headset preview in full-screen on the desktop PC while the headset is in use.</span></span>  

<span data-ttu-id="92555-141">隐藏你的面板的新用户-这会阻止在启动混合现实门户时展开 "新建" 面板。</span><span class="sxs-lookup"><span data-stu-id="92555-141">Hide New for you side panel – this prevent the New for you panel from being expanded on launch of Mixed Reality Portal.</span></span>  

#### <a name="how-to-configure"></a><span data-ttu-id="92555-142">如何配置:</span><span class="sxs-lookup"><span data-stu-id="92555-142">How to configure:</span></span>  

<span data-ttu-id="92555-143">若要设置这些配置中的任何一种, 需要在此目录下创建一个名为_userconfig.psm1_的文件: _\\ $env: LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState_</span><span class="sxs-lookup"><span data-stu-id="92555-143">To set any of these configurations, you need to create a file called _UserConfig.json_ under this directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="92555-144">对于大多数用户, 这将类似_于\<C:\Users username >\\ \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState_</span><span class="sxs-lookup"><span data-stu-id="92555-144">For most users this will look like _C:\Users\<username>\AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="92555-145">对于您想要启用的任意设置, JSON 文件的内容应为 "true":</span><span class="sxs-lookup"><span data-stu-id="92555-145">The JSON file should have the below contents with “true” set for any of the above settings you want enabled:</span></span>  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
<span data-ttu-id="92555-146">**:是否有关于配置 playspace 的指导？**</span><span class="sxs-lookup"><span data-stu-id="92555-146">**Q: Is there any guidance on configuring the playspace?**</span></span>

<span data-ttu-id="92555-147">答：应按照使用者安装体验来配置 playspace。</span><span class="sxs-lookup"><span data-stu-id="92555-147">A: Configuring a playspace should be done as you would with a consumer setup experience.</span></span> <span data-ttu-id="92555-148">房间设置过程还将允许您定义房间边界。</span><span class="sxs-lookup"><span data-stu-id="92555-148">The Room Setup process will also let you define your room boundaries.</span></span> <span data-ttu-id="92555-149">有关配置空间边界的详细信息, 请参阅[此处](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)。</span><span class="sxs-lookup"><span data-stu-id="92555-149">More details on configuring room boundaries can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="92555-150">如以上文档中所述, 最大合理的单个坐标 playspace 是围绕5mx5m 的。</span><span class="sxs-lookup"><span data-stu-id="92555-150">As discussed in the above document the maximum reasonable single coordinate playspace is around 5mx5m.</span></span> <span data-ttu-id="92555-151">如果要获得更大的区域, 可以使用 Windows 全息 API 堆栈中的空间锚功能。</span><span class="sxs-lookup"><span data-stu-id="92555-151">If you want to have a larger area you can make use of the Spatial Anchors capability in the Windows Holographic API stack.</span></span> <span data-ttu-id="92555-152">使用此 API 需要在生成的体验中进行自定义工程。</span><span class="sxs-lookup"><span data-stu-id="92555-152">Using this API will require custom engineering in the experiences you are producing.</span></span>  

<span data-ttu-id="92555-153">可在[此处](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems)阅读有关如何针对不同的空间大小优化内容的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="92555-153">More details on how to optimize your content for different space sizes can be read [here](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems).</span></span>
 

<span data-ttu-id="92555-154">**:我的空间太大了, 在尝试使用边界建立持续的体验时, 我遇到了错误。设置大的免费漫游体验应该怎么办？**</span><span class="sxs-lookup"><span data-stu-id="92555-154">**Q: My space is too large and I’m running into errors when I try to set up a Standing experience with boundaries. What should I do to setup my large free-roam experience work?**</span></span>

<span data-ttu-id="92555-155">答：若要设置比 ~ 18x18ft 更大的空间, 你将无法使用系统提供的边界体验。</span><span class="sxs-lookup"><span data-stu-id="92555-155">A: To setup a larger space than ~18x18ft you won’t be able to use the boundary experience provided by the system.</span></span>  <span data-ttu-id="92555-156">边界系统依赖于单个固定坐标 "锚点", 当用户离中心舞台锚点太远时, 这会变得不稳定。</span><span class="sxs-lookup"><span data-stu-id="92555-156">The boundary systems relies on leveraging a single fixed coordinate “anchor”, which can become unstable when a user is too far from the center stage anchor.</span></span> 

<span data-ttu-id="92555-157">相反, 您可以设置 "固定" 模式, 这种模式不会显示边界, 也不会配置阶段边界或 playspace。</span><span class="sxs-lookup"><span data-stu-id="92555-157">Instead, you can setup “seated” mode, which will not display the boundary or configure a stage bounds or playspace.</span></span>  <span data-ttu-id="92555-158">然后, 需要在应用内配置多个空间锚点以引用物理边界区域。</span><span class="sxs-lookup"><span data-stu-id="92555-158">Then, you’ll need to configure multiple spatial anchors within the app to reference physical boundary areas.</span></span> 

<span data-ttu-id="92555-159">应用程序开发人员负责显示必要的安全措施, 使用户不会与物理环境发生冲突。</span><span class="sxs-lookup"><span data-stu-id="92555-159">The application developer is responsible to display necessary safeguards so that users don’t collide with physical surroundings.</span></span>  <span data-ttu-id="92555-160">这可能是经验或自定义游戏边界视觉对象中的数字背景。</span><span class="sxs-lookup"><span data-stu-id="92555-160">These could be digital walls within the experience or a customized game boundary visual.</span></span> 

<span data-ttu-id="92555-161">可在[此处](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)找到有关通过 WMR 设置空间边界的指南。</span><span class="sxs-lookup"><span data-stu-id="92555-161">Guidance on setting up the room boundary with WMR can be found [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="92555-162">**:Playspace 的来源是什么？**</span><span class="sxs-lookup"><span data-stu-id="92555-162">**Q: Where is the origin of the playspace?**</span></span>

<span data-ttu-id="92555-163">答：Playspace 的来源取决于房间安装体验, 更具体地说是在安装过程中按下中心按钮时的 HMD 位置。</span><span class="sxs-lookup"><span data-stu-id="92555-163">A: The origin of the playspace is determined by the Room Setup experience, more specifically the HMD position when the Center button is pressed during setup.</span></span> 

### <a name="multi-player-setup"></a><span data-ttu-id="92555-164">多玩家安装</span><span class="sxs-lookup"><span data-stu-id="92555-164">MULTI-PLAYER SETUP</span></span>

<span data-ttu-id="92555-165">**:我将在我的场所部署多玩家体验。Windows Mixed Reality 是否支持？**</span><span class="sxs-lookup"><span data-stu-id="92555-165">**Q: I’m deploying a multi-player experience in at my venue. Is that supported on Windows Mixed Reality?**</span></span>

<span data-ttu-id="92555-166">答：混合现实空间数据包装器工具是一项 beta 功能, 可通过启用将空间数据从一台电脑移植到另一台电脑, 使多个播放器在同一空间中进行本地化。</span><span class="sxs-lookup"><span data-stu-id="92555-166">A: The Mixed Reality Spatial Data Packager tool is a beta feature that allows localizing multiple players in the same space by enabling porting of the spatial data from one PC to another.</span></span> <span data-ttu-id="92555-167">可以访问该工具, 并在[此处](mixedrealityspatialdatapackager.md)了解更多相关信息。</span><span class="sxs-lookup"><span data-stu-id="92555-167">You can access the tool and learn more about it [here](mixedrealityspatialdatapackager.md).</span></span>

### <a name="tracking"></a><span data-ttu-id="92555-168">字距</span><span class="sxs-lookup"><span data-stu-id="92555-168">TRACKING</span></span>

<span data-ttu-id="92555-169">问:Windows Mixed Reality 耳机中的跟踪技术是如何工作的？</span><span class="sxs-lookup"><span data-stu-id="92555-169">Q: How does the tracking technology in the Windows Mixed Reality headsets work?</span></span>  

<span data-ttu-id="92555-170">混合现实与 HoloLens 共享相同的跟踪技术。</span><span class="sxs-lookup"><span data-stu-id="92555-170">Mixed Reality shares the same tracking technology as the HoloLens.</span></span> <span data-ttu-id="92555-171">若要详细了解内部输出跟踪系统, 请查看[此处](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system)的文档。</span><span class="sxs-lookup"><span data-stu-id="92555-171">To learn more about the inside-out tracking system, check out the documentation [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/tracking-system).</span></span>

<span data-ttu-id="92555-172">有关更高级的空间映射系统的工作原理的说明, 请参阅[此处](spatial-mapping-design.md)的说明。</span><span class="sxs-lookup"><span data-stu-id="92555-172">For a description of how the higher-level spatial mapping system works you can read our description [here](spatial-mapping-design.md).</span></span>

<span data-ttu-id="92555-173">**:获取可靠跟踪卷是否有任何最佳实践？**</span><span class="sxs-lookup"><span data-stu-id="92555-173">**Q: Are there any best practices for getting a reliable tracking volume?**</span></span>

<span data-ttu-id="92555-174">为了最好地配置用于跟踪成功的环境, 您可以阅读此[文章](environment-considerations-for-hololens.md)中的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="92555-174">To best configure the environment for tracking success, you can read best practices in this [post](environment-considerations-for-hololens.md).</span></span>

<span data-ttu-id="92555-175">**:对于仓库规模空间或要考虑的优化, 是否存在任何特定的细微差别？**</span><span class="sxs-lookup"><span data-stu-id="92555-175">**Q: Are there any specific nuances with tracking in warehouse-scale spaces or optimizations to consider?**</span></span>

<span data-ttu-id="92555-176">答：以下做法可帮助获取更可靠的跟踪卷:</span><span class="sxs-lookup"><span data-stu-id="92555-176">A: The following practices can help with getting a more reliable tracking volume:</span></span>  

<span data-ttu-id="92555-177">在房间中提供不同于多个位置的功能将有助于跟踪系统获得稳定的锁定。</span><span class="sxs-lookup"><span data-stu-id="92555-177">Providing a variety of features in the room that overlap at multiple positions will help the tracking system get a solid lock.</span></span> <span data-ttu-id="92555-178">请考虑随机绘制 splatters 和阴影, 而不是使用纯色等高线样式线条。</span><span class="sxs-lookup"><span data-stu-id="92555-178">Think of random paint splatters and hatching rather than using solid contour style lines.</span></span> 

<span data-ttu-id="92555-179">尽可能最大程度地减小区域中的光线的动态范围。</span><span class="sxs-lookup"><span data-stu-id="92555-179">Minimize the dynamic range of lighting in your area where possible.</span></span> <span data-ttu-id="92555-180">混合现实 HMDs 上的跟踪相机不是 HDR, 具有 AGC (自动增益) 和 AEC (自动曝光), 以便处理不同的照明。</span><span class="sxs-lookup"><span data-stu-id="92555-180">The tracking cameras on our Mixed Reality HMDs are not HDR and have AGC (auto gain) and AEC (auto exposure) going in order to deal with different lighting.</span></span> <span data-ttu-id="92555-181">根据表面光、模式和对比度的分布情况, AGC 或 AEC 可能会假设您的所有白色或黑色房间都能冲蚀您的功能, 这种情况可能会与 "颜色" 相反。</span><span class="sxs-lookup"><span data-stu-id="92555-181">Depending on the distribution of surface light, patterns and contrast, either AGC or AEC may conclude you’re in a pretty much all white or black room which can wash out your features that may be in the opposite “color”.</span></span> <span data-ttu-id="92555-182">如果你正在尝试在具有鲜日光的外部窗口的前方拍摄内部图片, 并调整了曝光以便查看外的详细信息, 则内部的所有内容都是 underexposed 和黑色。</span><span class="sxs-lookup"><span data-stu-id="92555-182">If you are trying to take an interior picture in front of an exterior window with bright daylight behind and you adjust exposure so you can see detail outside, then everything on the interior is underexposed and black.</span></span> <span data-ttu-id="92555-183">或者, 如果在内部设置, 则所有外部的内容现在都是 overexposed, 所有白色。</span><span class="sxs-lookup"><span data-stu-id="92555-183">Or if set for inside, then everything outside is now overexposed and all white.</span></span>  

<span data-ttu-id="92555-184">如果跟踪相机有时原因, 则在房间 (甚至是开销) 中进行聚光灯, 这会混淆跟踪相机的 AEC/AGC。</span><span class="sxs-lookup"><span data-stu-id="92555-184">Spotlights in a room (even overhead) that are in view if tracking cameras can sometimes be culprits which confuse the AEC/AGC of the tracking cameras.</span></span> <span data-ttu-id="92555-185">平面/散射照明可帮助。</span><span class="sxs-lookup"><span data-stu-id="92555-185">Flat/diffused lighting helps.</span></span>  

### <a name="mixed-reality-cloud-services-and-azure"></a><span data-ttu-id="92555-186">混合现实云服务和 AZURE</span><span class="sxs-lookup"><span data-stu-id="92555-186">MIXED REALITY CLOUD SERVICES AND AZURE</span></span> 

<span data-ttu-id="92555-187">**:Microsoft Azure 如何帮助我的业务规模？**</span><span class="sxs-lookup"><span data-stu-id="92555-187">**Q: How can Microsoft Azure help my business scale?**</span></span>

<span data-ttu-id="92555-188">答：基于 Azure 的现场和远程管理可帮助你的业务进行数据驱动, 降低运营成本并在现有和新位置扩展部署。</span><span class="sxs-lookup"><span data-stu-id="92555-188">A: Azure based onsite and remote management can help your business be data-driven, reduce operational costs and scale deployment across existing and new locations.</span></span> <span data-ttu-id="92555-189">Azure 云服务 (例如 Azure 存储、Azure Functions、应用服务、Azure 网络和 IOT 中心) 可帮助解决以下用例:</span><span class="sxs-lookup"><span data-stu-id="92555-189">Azure cloud services such as Azure Storage, Azure Functions, App Service, Azure Networking and IOT Hub can help with the following use cases:</span></span>  

<span data-ttu-id="92555-190">远程设备部署 & 管理</span><span class="sxs-lookup"><span data-stu-id="92555-190">Remote Device Deployment & Management</span></span> 

<span data-ttu-id="92555-191">实时现场分析</span><span class="sxs-lookup"><span data-stu-id="92555-191">Real Time Onsite Analytics</span></span> 

<span data-ttu-id="92555-192">智能适应性 LBE 游戏</span><span class="sxs-lookup"><span data-stu-id="92555-192">Intelligent Adaptable LBE Gameplay</span></span> 

<span data-ttu-id="92555-193">LBE 内容流式处理和部署</span><span class="sxs-lookup"><span data-stu-id="92555-193">LBE Content Streaming and Deployment</span></span> 

<span data-ttu-id="92555-194">LBE Player 首选项热度地图</span><span class="sxs-lookup"><span data-stu-id="92555-194">LBE Player Preference Heatmap</span></span> 

<span data-ttu-id="92555-195">LBE 预订系统和预订系统</span><span class="sxs-lookup"><span data-stu-id="92555-195">LBE Reservation and Booking System</span></span> 

<span data-ttu-id="92555-196">**:我要开发一个空间 MMOG, 以通过大量的空间来进行部署。有助于管理内容和对象持久性的任何服务？**</span><span class="sxs-lookup"><span data-stu-id="92555-196">**Q: I’m developing a spatial MMOG to deploy over a massive footprint. Any services that help me manage my content and object persistence?**</span></span>

<span data-ttu-id="92555-197">答：Azure 空间锚点是一项新的混合现实服务, 可在 HoloLens、iOS 和 Android 设备上实现多用户、空间丰富的混合现实体验。</span><span class="sxs-lookup"><span data-stu-id="92555-197">A: Azure Spatial Anchors is a new Mixed Reality service that enables multi-user, spatially aware mixed reality experiences across HoloLens, iOS and Android devices.</span></span> <span data-ttu-id="92555-198">可在[此处](https://azure.microsoft.com/en-us/services/spatial-anchors/)了解有关 Azure 空间定位点的详细信息。</span><span class="sxs-lookup"><span data-stu-id="92555-198">You can learn more about Azure Spatial Anchors [here](https://azure.microsoft.com/en-us/services/spatial-anchors/).</span></span>

<span data-ttu-id="92555-199">**:.我们的场地专用于多玩家体验, 我想将开发时间集中在内容和前端开发上。是否有可帮助我启动或卸载后端开发的产品？**</span><span class="sxs-lookup"><span data-stu-id="92555-199">**Q. Our venue specializes in multi-player experiences and I’d like to focus our development time on content and front-end development. Are there offerings that can help me bootstrap or offload backend development?**</span></span>

<span data-ttu-id="92555-200">答：Azure PlayFab 是适用于现场游戏的完整后端平台。</span><span class="sxs-lookup"><span data-stu-id="92555-200">A: Azure PlayFab is a complete backend platform for live games.</span></span> <span data-ttu-id="92555-201">可在[此处](https://playfab.com/)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="92555-201">You can learn more about it [here](https://playfab.com/).</span></span>

### <a name="misc"></a><span data-ttu-id="92555-202">Misc</span><span class="sxs-lookup"><span data-stu-id="92555-202">Misc</span></span>

<span data-ttu-id="92555-203">**:我使用 SteamVR 部署我的体验。Windows Mixed Reality 是否适用于 SteamVR？**</span><span class="sxs-lookup"><span data-stu-id="92555-203">**Q: I use SteamVR to deploy my experiences. Does Windows Mixed Reality work with SteamVR?**</span></span>

<span data-ttu-id="92555-204">答：适用于 SteamVR 的 windows Mixed Reality 允许用户在 Windows Mixed Reality 沉浸式耳机上运行 SteamVR 体验。</span><span class="sxs-lookup"><span data-stu-id="92555-204">A: Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="92555-205">[在此处](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)了解有关 SteamVR 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="92555-205">Learn more about SteamVR with WMR [here](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span></span>

### <a name="support-and-community"></a><span data-ttu-id="92555-206">支持和社区</span><span class="sxs-lookup"><span data-stu-id="92555-206">Support and community</span></span>  

<span data-ttu-id="92555-207">下面是一些有用的资源, 这些资源可与我们团队的行业专家进行交流、获取故障排除支持, 并为更广泛的混合现实开发社区提供支持。</span><span class="sxs-lookup"><span data-stu-id="92555-207">Below are a few helpful resources to engage with subject matter experts on our team, get troubleshooting support, and contribute to the broader mixed reality dev community.</span></span>  

<span data-ttu-id="92555-208">如果遇到任何公开发布功能的问题, 请使用反馈中心提交 bug。有关指南, 请参阅此[页](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback)。</span><span class="sxs-lookup"><span data-stu-id="92555-208">If you run into issues with any publicly released features, please file a bug using Feedback Hub.For guidance, please refer to this [page](https://docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span>

<span data-ttu-id="92555-209">有关 WMR 的其他故障排除帮助, 请通过填写[支持请求](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782)与我们的客户支持团队联系。</span><span class="sxs-lookup"><span data-stu-id="92555-209">For additional troubleshooting help with WMR please get in touch with our customer support team by filing a [support request](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).</span></span>

<span data-ttu-id="92555-210">加入我们的 HoloDevelopers 时差通道, 与团队的混合现实和主题专家合作开发人员: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span><span class="sxs-lookup"><span data-stu-id="92555-210">Join our HoloDevelopers Slack channel to engage with the developers working on mixed reality and subject matter experts from the team: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span></span>

<span data-ttu-id="92555-211">Twitter关注混合现实开发人员关系团队, 以获取新闻、活动和更新@MxdRealityDev</span><span class="sxs-lookup"><span data-stu-id="92555-211">Twitter: Follow our Mixed Reality Developer Relations team for news, events and updates @MxdRealityDev</span></span> 

<span data-ttu-id="92555-212">如果你的工作发生在旧金山或周围, 则 Microsoft 反应器中始终会出现一些问题。</span><span class="sxs-lookup"><span data-stu-id="92555-212">If you happen to be in or around San Francisco, there’s always something going on at the Microsoft Reactor.</span></span> <span data-ttu-id="92555-213">[此处](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco)可以看到我们的事件日历。</span><span class="sxs-lookup"><span data-stu-id="92555-213">You can see our calendar of events [here](https://developer.microsoft.com/en-us/reactor/Location/San%20Francisco).</span></span>