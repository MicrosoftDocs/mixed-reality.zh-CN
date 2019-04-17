---
title: Spectator 视图
description: 作为一种方式的演示的外部显示器上的混合的现实体验或录制视频的混合的现实体验可视化全息从外部设备。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator 视图，iPhone、 iOS、 iPad，OpenCV、 照相机、 ARKit、 HoloLens、 混合现实、 MixedRealityToolkit，演示中，记录
ms.openlocfilehash: 77102cf5fb1c23f27f7f2d651c6ca1ae9df5a1d1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592439"
---
# <a name="spectator-view-for-hololens"></a><span data-ttu-id="5ed14-104">HoloLens spectator 视图</span><span class="sxs-lookup"><span data-stu-id="5ed14-104">Spectator View for HoloLens</span></span>

![Marker](images/SpecViewPhoneHero.jpg)


## <a name="current-refactor"></a><span data-ttu-id="5ed14-106">当前的重构</span><span class="sxs-lookup"><span data-stu-id="5ed14-106">Current Refactor</span></span>

> [!NOTE]
><span data-ttu-id="5ed14-107">HoloLens spectator 视图是正在积极地重构。</span><span class="sxs-lookup"><span data-stu-id="5ed14-107">Spectator View for HoloLens is being actively refactored.</span></span> <span data-ttu-id="5ed14-108">此工作旨在合并在预览 Pro 代码库和将支持扩展到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="5ed14-108">This work is intended to consolidate the Preview and Pro codebases and extend support to HoloLens 2.</span></span> 

<span data-ttu-id="5ed14-109">若要查看当前 Spectator 视图重构的状态，请参阅 MixedRealityToolkit 和 MixedRealityToolkit Unity 存储库中的功能/spectatorView 分支：</span><span class="sxs-lookup"><span data-stu-id="5ed14-109">To view the current state of the Spectator View refactor see 'feature/spectatorView' branches in both the MixedRealityToolkit and MixedRealityToolkit-Unity repos:</span></span>

https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/feature/spectatorView/Assets/MixedRealityToolkit.Extensions/SpectatorView

<span data-ttu-id="5ed14-110">和</span><span class="sxs-lookup"><span data-stu-id="5ed14-110">and</span></span>

https://github.com/Microsoft/MixedRealityToolkit/tree/feature/spectatorView/SpectatorViewPlugin

## <a name="overview"></a><span data-ttu-id="5ed14-111">概述</span><span class="sxs-lookup"><span data-stu-id="5ed14-111">Overview</span></span>

<span data-ttu-id="5ed14-112">当戴上 HoloLens，我们经常忘记的一个人谁不包含该列不能体验我们可以神奇。</span><span class="sxs-lookup"><span data-stu-id="5ed14-112">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="5ed14-113">Spectator 视图允许其他人在 2D 屏幕上看到 HoloLens 用户在他们的世界中所看到的内容。</span><span class="sxs-lookup"><span data-stu-id="5ed14-113">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="5ed14-114">Spectator 视图 （预览版） 是快速且经济实惠方法中 HD，录制全息时 Spectator 视图 Pro 适用于的全息专业的高质量录音。</span><span class="sxs-lookup"><span data-stu-id="5ed14-114">Spectator View (Preview) is fast and affordable approach to recording holograms in HD, while Spectator View Pro is intended for professional quality recording of holograms.</span></span>

<span data-ttu-id="5ed14-115">下表显示选项和其功能。</span><span class="sxs-lookup"><span data-stu-id="5ed14-115">The following table shows both options and their capabilities.</span></span> <span data-ttu-id="5ed14-116">选择最适合你的视频录制需要的选项：</span><span class="sxs-lookup"><span data-stu-id="5ed14-116">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="5ed14-117">Spectator 视图 （预览版）</span><span class="sxs-lookup"><span data-stu-id="5ed14-117">Spectator View (Preview)</span></span> |              <span data-ttu-id="5ed14-118">Spectator 查看 Pro</span><span class="sxs-lookup"><span data-stu-id="5ed14-118">Spectator View Pro</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="5ed14-119">HD 质量</span><span class="sxs-lookup"><span data-stu-id="5ed14-119">HD quality</span></span>                         |         <span data-ttu-id="5ed14-120">全高清</span><span class="sxs-lookup"><span data-stu-id="5ed14-120">Full HD</span></span>         |        <span data-ttu-id="5ed14-121">专业质量与 （这由 DSLR）</span><span class="sxs-lookup"><span data-stu-id="5ed14-121">Professional quality filming (as determined by DSLR)</span></span>      |
| <span data-ttu-id="5ed14-122">简易照相机移动</span><span class="sxs-lookup"><span data-stu-id="5ed14-122">Easy camera movement</span></span>                      |            <span data-ttu-id="5ed14-123">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-123">✔</span></span>            |                                             |
| <span data-ttu-id="5ed14-124">第三个人视图</span><span class="sxs-lookup"><span data-stu-id="5ed14-124">Third-person view</span></span>                    |            <span data-ttu-id="5ed14-125">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-125">✔</span></span>            |                      <span data-ttu-id="5ed14-126">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-126">✔</span></span>                      |
| <span data-ttu-id="5ed14-127">为流式传输到屏幕</span><span class="sxs-lookup"><span data-stu-id="5ed14-127">Can be streamed to screens</span></span>           |            <span data-ttu-id="5ed14-128">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-128">✔</span></span>            |                      <span data-ttu-id="5ed14-129">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-129">✔</span></span>                      |
| <span data-ttu-id="5ed14-130">可移植</span><span class="sxs-lookup"><span data-stu-id="5ed14-130">Portable</span></span>                             |            <span data-ttu-id="5ed14-131">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-131">✔</span></span>            |                                             |
| <span data-ttu-id="5ed14-132">无线</span><span class="sxs-lookup"><span data-stu-id="5ed14-132">Wireless</span></span>                             |            <span data-ttu-id="5ed14-133">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-133">✔</span></span>            |                                             |
| <span data-ttu-id="5ed14-134">其他所需的硬件</span><span class="sxs-lookup"><span data-stu-id="5ed14-134">Additional required hardware</span></span>         |     <span data-ttu-id="5ed14-135">iPhone （或 iPad）</span><span class="sxs-lookup"><span data-stu-id="5ed14-135">iPhone (or iPad)</span></span>    | <span data-ttu-id="5ed14-136">HoloLens + 远程测试机组 + 三脚架 + DSLR + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="5ed14-136">HoloLens + Rig + Tripod + DSLR + PC + Unity</span></span> |
| <span data-ttu-id="5ed14-137">硬件投资</span><span class="sxs-lookup"><span data-stu-id="5ed14-137">Hardware investment</span></span>                  |           <span data-ttu-id="5ed14-138">低</span><span class="sxs-lookup"><span data-stu-id="5ed14-138">Low</span></span>           |                     <span data-ttu-id="5ed14-139">高</span><span class="sxs-lookup"><span data-stu-id="5ed14-139">High</span></span>                    |
| <span data-ttu-id="5ed14-140">跨平台</span><span class="sxs-lookup"><span data-stu-id="5ed14-140">Cross-platform</span></span>                       |           <span data-ttu-id="5ed14-141">iOS</span><span class="sxs-lookup"><span data-stu-id="5ed14-141">iOS</span></span>           |                                             |
| <span data-ttu-id="5ed14-142">查看器可以进行交互</span><span class="sxs-lookup"><span data-stu-id="5ed14-142">Viewer can interact</span></span>                  |            <span data-ttu-id="5ed14-143">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-143">✔</span></span>            |                                             |
| <span data-ttu-id="5ed14-144">(UNET scripting) 所需的网络</span><span class="sxs-lookup"><span data-stu-id="5ed14-144">Networking required (UNET scripting)</span></span> |            <span data-ttu-id="5ed14-145">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-145">✔</span></span>            |                      <span data-ttu-id="5ed14-146">✔</span><span class="sxs-lookup"><span data-stu-id="5ed14-146">✔</span></span>                      |
| <span data-ttu-id="5ed14-147">运行时安装程序持续时间</span><span class="sxs-lookup"><span data-stu-id="5ed14-147">Runtime setup duration</span></span>               |         <span data-ttu-id="5ed14-148">即时</span><span class="sxs-lookup"><span data-stu-id="5ed14-148">Instant</span></span>         |                     <span data-ttu-id="5ed14-149">慢速</span><span class="sxs-lookup"><span data-stu-id="5ed14-149">Slow</span></span>                    |

## <a name="spectator-view-preview"></a><span data-ttu-id="5ed14-150">Spectator 视图 （预览版）</span><span class="sxs-lookup"><span data-stu-id="5ed14-150">Spectator View (Preview)</span></span>

![Marker](images/SpecViewPhoneDemo.jpg)

### <a name="use-cases"></a><span data-ttu-id="5ed14-152">用例</span><span class="sxs-lookup"><span data-stu-id="5ed14-152">Use cases</span></span>

- <span data-ttu-id="5ed14-153">与全息 HD 中：使用 Spectator 视图 （预览版），您可以记录使用 iPhone 的混合的现实体验。</span><span class="sxs-lookup"><span data-stu-id="5ed14-153">Filming holograms in HD: Using Spectator View (Preview), you can record a mixed reality experience using an iPhone.</span></span> <span data-ttu-id="5ed14-154">在完整 HD 中记录并将抗锯齿应用于全息和甚至阴影。</span><span class="sxs-lookup"><span data-stu-id="5ed14-154">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="5ed14-155">它是捕获视频全息经济高效且快速方法。</span><span class="sxs-lookup"><span data-stu-id="5ed14-155">It is a cost-effective and quick way to capture video of holograms.</span></span>
- <span data-ttu-id="5ed14-156">现场演示：Stream 实时混合的现实体验到 Apple TV 直接从 iPhone 或 iPad，延隔免费 ！</span><span class="sxs-lookup"><span data-stu-id="5ed14-156">Live demos: Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
- <span data-ttu-id="5ed14-157">与来宾共享体验：允许非 HoloLens 用户体验全息直接通过其手机或平板电脑。</span><span class="sxs-lookup"><span data-stu-id="5ed14-157">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

### <a name="current-features"></a><span data-ttu-id="5ed14-158">当前功能</span><span class="sxs-lookup"><span data-stu-id="5ed14-158">Current features</span></span>

- <span data-ttu-id="5ed14-159">将电话添加到该会话的自动发现的网络。</span><span class="sxs-lookup"><span data-stu-id="5ed14-159">Network auto-discovery for adding phones to the session.</span></span>
- <span data-ttu-id="5ed14-160">自动会话处理，以便用户添加到正确的会话。</span><span class="sxs-lookup"><span data-stu-id="5ed14-160">Automatic session handling, so users are added to the correct session.</span></span>
- <span data-ttu-id="5ed14-161">全息，以便每个人都看到全息完全相同的位置的空间同步。</span><span class="sxs-lookup"><span data-stu-id="5ed14-161">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
- <span data-ttu-id="5ed14-162">iOS 支持 （ARKit 启用设备）。</span><span class="sxs-lookup"><span data-stu-id="5ed14-162">iOS support (ARKit-enabled devices).</span></span>
- <span data-ttu-id="5ed14-163">多个 iOS 来宾。</span><span class="sxs-lookup"><span data-stu-id="5ed14-163">Multiple iOS guests.</span></span>
- <span data-ttu-id="5ed14-164">录制的视频 + 全息 + 环境音效 + 全息图声音。</span><span class="sxs-lookup"><span data-stu-id="5ed14-164">Recording of video + holograms + ambient sound + hologram sound.</span></span>
- <span data-ttu-id="5ed14-165">共享工作表，因此可以保存视频、 电子邮件发送它，或与其他支持的应用共享。</span><span class="sxs-lookup"><span data-stu-id="5ed14-165">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>


>[!NOTE] 
><span data-ttu-id="5ed14-166">Spectator 视图 （预览） 代码不能用于 Spectator 视图专业人员的版本代码。</span><span class="sxs-lookup"><span data-stu-id="5ed14-166">The Spectator View (Preview) code cannot be used with the Spectator View Pro version code.</span></span> <span data-ttu-id="5ed14-167">我们建议您在需要的全息视频录制的新项目中实现它。</span><span class="sxs-lookup"><span data-stu-id="5ed14-167">We recommend to implement it in new projects where video recording of holograms is required.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/3fXlPw_FGLg]


### <a name="licenses"></a><span data-ttu-id="5ed14-168">许可证</span><span class="sxs-lookup"><span data-stu-id="5ed14-168">Licenses</span></span>

- [<span data-ttu-id="5ed14-169">OpenCV-（3 子句 BSD 许可）</span><span class="sxs-lookup"><span data-stu-id="5ed14-169">OpenCV - (3-clause BSD License)</span></span>](https://opencv.org/license.html)
- [<span data-ttu-id="5ed14-170">Unity ARKit-（MIT 许可证）</span><span class="sxs-lookup"><span data-stu-id="5ed14-170">Unity ARKit - (MIT License)</span></span>](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/src/3691df77caca2095d632c5e72ff4ffa68ced111f/LICENSES/MIT_LICENSE?at=default&fileviewer=file-view-default)

## <a name="how-to-set-up-spectator-view-preview"></a><span data-ttu-id="5ed14-171">如何设置 Spectator 视图 （预览版）</span><span class="sxs-lookup"><span data-stu-id="5ed14-171">How to set up Spectator View (Preview)</span></span>

### <a name="requirements"></a><span data-ttu-id="5ed14-172">要求</span><span class="sxs-lookup"><span data-stu-id="5ed14-172">Requirements</span></span>

- <span data-ttu-id="5ed14-173">[Spectator 视图插件和必需的 OpenCV 二进制文件](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)-可在下面找到如何 Spectator 视图本机插件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="5ed14-173">[Spectator View plugin and required OpenCV binaries](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin) - Details on how to build the Spectator View Native Plugin can be found below.</span></span> <span data-ttu-id="5ed14-174">从生成的二进制文件中，你将需要：</span><span class="sxs-lookup"><span data-stu-id="5ed14-174">From the generated binaries you will need:</span></span>

    - <span data-ttu-id="5ed14-175">opencv_aruco343.dll</span><span class="sxs-lookup"><span data-stu-id="5ed14-175">opencv_aruco343.dll</span></span>
    - <span data-ttu-id="5ed14-176">opencv_calib3d343.dll</span><span class="sxs-lookup"><span data-stu-id="5ed14-176">opencv_calib3d343.dll</span></span>
    - <span data-ttu-id="5ed14-177">opencv_core343.dll</span><span class="sxs-lookup"><span data-stu-id="5ed14-177">opencv_core343.dll</span></span>
    - <span data-ttu-id="5ed14-178">opencv_features2d343.dll</span><span class="sxs-lookup"><span data-stu-id="5ed14-178">opencv_features2d343.dll</span></span>
    - <span data-ttu-id="5ed14-179">opencv_flann343.dll</span><span class="sxs-lookup"><span data-stu-id="5ed14-179">opencv_flann343.dll</span></span>
    - <span data-ttu-id="5ed14-180">opencv_imgproc343.dll</span><span class="sxs-lookup"><span data-stu-id="5ed14-180">opencv_imgproc343.dll</span></span>

    - <span data-ttu-id="5ed14-181">zlib1.dll</span><span class="sxs-lookup"><span data-stu-id="5ed14-181">zlib1.dll</span></span>
    - <span data-ttu-id="5ed14-182">SpectatorViewPlugin.dll</span><span class="sxs-lookup"><span data-stu-id="5ed14-182">SpectatorViewPlugin.dll</span></span>
- <span data-ttu-id="5ed14-183">Spectator 视图使用的网络发现和空间同步 Unity 网络 (UNET)。</span><span class="sxs-lookup"><span data-stu-id="5ed14-183">Spectator View uses Unity Networking (UNET) for its network discovery and spatial syncing.</span></span> <span data-ttu-id="5ed14-184">这意味着需要在设备之间同步期间应用程序的所有交互。</span><span class="sxs-lookup"><span data-stu-id="5ed14-184">This means all interactivity during the application needs to be synced between the devices.</span></span>
- <span data-ttu-id="5ed14-185">Unity 2017.2.1p2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="5ed14-185">Unity 2017.2.1p2 or later</span></span>
- <span data-ttu-id="5ed14-186">硬件</span><span class="sxs-lookup"><span data-stu-id="5ed14-186">Hardware</span></span>
    - <span data-ttu-id="5ed14-187">HoloLens</span><span class="sxs-lookup"><span data-stu-id="5ed14-187">A HoloLens</span></span>
    - <span data-ttu-id="5ed14-188">运行 Windows 10 的 Windows 电脑</span><span class="sxs-lookup"><span data-stu-id="5ed14-188">Windows PC running Windows 10</span></span>
    - <span data-ttu-id="5ed14-189">ARKit 兼容的设备 (iPhone 6s 及更高版本 / iPad Pro 2016 及更高版本 / iPad 2017 及更高版本) 的运行 iOS 11 或更高版本</span><span class="sxs-lookup"><span data-stu-id="5ed14-189">ARKit compatible device (iPhone 6s onwards / iPad Pro 2016 onwards / iPad 2017 onwards) - running iOS 11 or above</span></span>
    - <span data-ttu-id="5ed14-190">与 xcode 9.2 及以上版本的 Mac</span><span class="sxs-lookup"><span data-stu-id="5ed14-190">Mac with xcode 9.2 onwards</span></span>
- <span data-ttu-id="5ed14-191">Apple 开发人员帐户，免费或[付费](https://developer.apple.com/)</span><span class="sxs-lookup"><span data-stu-id="5ed14-191">Apple developer account, free or [paid](https://developer.apple.com/)</span></span>
- <span data-ttu-id="5ed14-192">Microsoft Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="5ed14-192">Microsoft Visual Studio 2017</span></span>

### <a name="building-the-spectator-view-native-plugin"></a><span data-ttu-id="5ed14-193">构建 Spectator 视图本机插件</span><span class="sxs-lookup"><span data-stu-id="5ed14-193">Building the Spectator View native plugin</span></span>

<span data-ttu-id="5ed14-194">若要生成所需的文件，请执行以下步骤： https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md</span><span class="sxs-lookup"><span data-stu-id="5ed14-194">To generate the required files, follow these steps: https://github.com/Microsoft/MixedRealityToolkit/blob/master/SpectatorViewPlugin/README.md</span></span>

### <a name="project-setup"></a><span data-ttu-id="5ed14-195">项目设置</span><span class="sxs-lookup"><span data-stu-id="5ed14-195">Project setup</span></span>

1. <span data-ttu-id="5ed14-196">准备您的场景中，确保您的场景中的所有可见 gameobjects 包含在全球根 gameobject 之下。</span><span class="sxs-lookup"><span data-stu-id="5ed14-196">Prepare your scene, ensuring all visable gameobjects within your scene are contained under a world root gameobject.</span></span>

    ![全球根](images/SpecViewPhoneWorldRoot2.PNG)

2. <span data-ttu-id="5ed14-198">添加 SpectatorView 预设 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) 到您的场景。</span><span class="sxs-lookup"><span data-stu-id="5ed14-198">Add the SpectatorView prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorView.prefab)) into your scene.</span></span>
3. <span data-ttu-id="5ed14-199">添加 SpectatorViewNetworking 预设 ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) 到您的场景。</span><span class="sxs-lookup"><span data-stu-id="5ed14-199">Add the SpectatorViewNetworking prefab ([Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Preview/SpectatorView/Prefabs/SpectatorViewNetworking.prefab)) into your scene.</span></span>
4. <span data-ttu-id="5ed14-200">选择 SpectatorViewNetworking gameobject 并且 SpectatorViewNetworkingManager 组件上没有可以链接启用的一些事项。</span><span class="sxs-lookup"><span data-stu-id="5ed14-200">Select the SpectatorViewNetworking gameobject and on the SpectatorViewNetworkingManager component, there's a few things you can link up.</span></span> <span data-ttu-id="5ed14-201">如果保持不变，左侧有必要脚本在运行时将搜索此组件。</span><span class="sxs-lookup"><span data-stu-id="5ed14-201">If left untouched this component will search for necessary scripts at runtime.</span></span>
    - <span data-ttu-id="5ed14-202">标记检测 HoloLens-> SpectatorView/Hololens/MarkerDetection</span><span class="sxs-lookup"><span data-stu-id="5ed14-202">Marker Detection HoloLens -> SpectatorView/Hololens/MarkerDetection</span></span>
    - <span data-ttu-id="5ed14-203">标记生成 3D-> SpectatorView/IPhone/SyncMarker/3DMarker</span><span class="sxs-lookup"><span data-stu-id="5ed14-203">Marker Generation 3D -> SpectatorView/IPhone/SyncMarker/3DMarker</span></span>

    ![SpectatorView 网络发现](images/SpecViewPhoneNetworkDiscovery.PNG)

### <a name="networking-your-app"></a><span data-ttu-id="5ed14-205">网络应用程序</span><span class="sxs-lookup"><span data-stu-id="5ed14-205">Networking your app</span></span>

- <span data-ttu-id="5ed14-206">Spectator 视图 UNET 用于其网络和管理为你的所有主机客户端连接。</span><span class="sxs-lookup"><span data-stu-id="5ed14-206">Spectator View uses UNET for its networking and manages all host-client connections for you.</span></span>
- <span data-ttu-id="5ed14-207">任何应用程序特定的数据必须进行同步，并且您使用例如 SyncVars、 NetworkTransform、 NetworkBehavior 实现。</span><span class="sxs-lookup"><span data-stu-id="5ed14-207">Any app specific data has to be synced and implemented by you, using e.g. SyncVars, NetworkTransform, NetworkBehavior.</span></span>
- <span data-ttu-id="5ed14-208">有关 Unity 网络的详细信息，请访问[之多人游戏和网络](https://docs.unity3d.com/Manual/UNet.html)。</span><span class="sxs-lookup"><span data-stu-id="5ed14-208">For more information on Unity Networking please visit [Multiplayer and Networking](https://docs.unity3d.com/Manual/UNet.html).</span></span> <span data-ttu-id="5ed14-209">（注意：已不推荐使用 UNet;Spectator 视图基本代码的当前重构将解决此问题）</span><span class="sxs-lookup"><span data-stu-id="5ed14-209">(Note: UNet has been deprecated; the current refactor of the Spectator View codebase will address this issue)</span></span>

### <a name="building-for-each-platform-hololens-or-ios"></a><span data-ttu-id="5ed14-210">为每个平台 （HoloLens 或 iOS）</span><span class="sxs-lookup"><span data-stu-id="5ed14-210">Building for each platform (HoloLens or iOS)</span></span>

- <span data-ttu-id="5ed14-211">为 iOS 生成时，请确保您删除 MRTK GLTF 组件，因为这不是尚未与此平台兼容。</span><span class="sxs-lookup"><span data-stu-id="5ed14-211">When building for iOS, ensure you remove the GLTF component of MRTK as this is not yet compatible with this platform.</span></span>
- <span data-ttu-id="5ed14-212">SpectatorView 预设的最高级别没有名为平台切换器的组件。</span><span class="sxs-lookup"><span data-stu-id="5ed14-212">At the top level of the SpectatorView prefab there is a component called 'Platform Switcher'.</span></span> <span data-ttu-id="5ed14-213">选择你想要构建面向的平台。</span><span class="sxs-lookup"><span data-stu-id="5ed14-213">Select the platform you want to build for.</span></span>
    - <span data-ttu-id="5ed14-214">如果选择 Hololens 可以看到下方的 iPhone gameobject SpectatorView 预设可变为不活动状态中的所有 gameobjects 和 Hololens 变为活动状态下的所有 gameobject。</span><span class="sxs-lookup"><span data-stu-id="5ed14-214">If selecting 'Hololens' you should see all gameobjects beneath the iPhone gameobject in the SpectatorView prefab become inactive and all the gameobjects under 'Hololens' become active.</span></span>
    - <span data-ttu-id="5ed14-215">这可能需要一段时间，具体取决于平台选择 HoloToolkit 正在项目中添加或删除。</span><span class="sxs-lookup"><span data-stu-id="5ed14-215">This can take a little while as depending on the platform you choose the HoloToolkit is being added or removed from the project.</span></span>

    ![平台切换器](images/SpecViewPhoneSwitcher.PNG)

- <span data-ttu-id="5ed14-217">请确保生成因 Unity 未解决问题而使用相同的 Unity 编辑器实例 （不要之间不关闭 Unity 生成） 的应用程序的所有版本。</span><span class="sxs-lookup"><span data-stu-id="5ed14-217">Ensure you build all versions of the application using the same Unity editor instance (do not close Unity between builds) due to an unresolved issue with Unity.</span></span>

### <a name="running-your-app"></a><span data-ttu-id="5ed14-218">运行您的应用程序</span><span class="sxs-lookup"><span data-stu-id="5ed14-218">Running your app</span></span>

<span data-ttu-id="5ed14-219">一旦已生成并部署了应用程序的所有 iPhone 和 HoloLens 上的版本，您应能够将它们连接。</span><span class="sxs-lookup"><span data-stu-id="5ed14-219">Once you have built and deployed a version of you application on iPhone and on HoloLens, you should be able to connect them.</span></span>

1. <span data-ttu-id="5ed14-220">确保这两种设备位于同一 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="5ed14-220">Ensure that both devices are on the same Wi-Fi network.</span></span>
2. <span data-ttu-id="5ed14-221">在这两个设备，以非特定顺序上启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="5ed14-221">Start the application on the both devices, in no specific order.</span></span> <span data-ttu-id="5ed14-222">在 iPhone 上启动应用程序的过程应触发 HoloLens 照相机来启用和开始拍摄照片。</span><span class="sxs-lookup"><span data-stu-id="5ed14-222">The process of starting the application on the iPhone should trigger the HoloLens camera to turn on and begin taking pictures.</span></span>
3. <span data-ttu-id="5ed14-223">立即在 iPhone 应用启动时，它会查找楼层或表等的图面。</span><span class="sxs-lookup"><span data-stu-id="5ed14-223">As soon as iPhone app starts, it will look for surfaces like floors or tables.</span></span> <span data-ttu-id="5ed14-224">当找不到图面时，应会看到类似于下面的标记。</span><span class="sxs-lookup"><span data-stu-id="5ed14-224">When surfaces are found, you should see a marker similar to the one below.</span></span> <span data-ttu-id="5ed14-225">此标记向 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5ed14-225">Show this marker to the HoloLens.</span></span>

    ![Marker](images/SpecViewPhoneMarker.PNG)

4. <span data-ttu-id="5ed14-227">一旦检测到标记的 HoloLens 它应会消失，这两种设备应连接并在空间上同步。</span><span class="sxs-lookup"><span data-stu-id="5ed14-227">Once the marker has been detected by the HoloLens it should disappear and both devices should be connected and spatially synced.</span></span>

### <a name="recording-video"></a><span data-ttu-id="5ed14-228">录制视频</span><span class="sxs-lookup"><span data-stu-id="5ed14-228">Recording video</span></span>

1. <span data-ttu-id="5ed14-229">若要捕获和保存从 iPhone 的视频，点击按住屏幕 1 秒。</span><span class="sxs-lookup"><span data-stu-id="5ed14-229">To capture and save a video from the iPhone, tap and hold the screen for 1 second.</span></span> <span data-ttu-id="5ed14-230">这将打开录制菜单。</span><span class="sxs-lookup"><span data-stu-id="5ed14-230">This will open the recording menu.</span></span>
2. <span data-ttu-id="5ed14-231">点击红色录制按钮，这将启动开始记录屏幕之前的倒计时。</span><span class="sxs-lookup"><span data-stu-id="5ed14-231">Tap the red record button, this will start a countdown before beginning to record the screen.</span></span>
3. <span data-ttu-id="5ed14-232">若要完成录制点击并保留在屏幕的另一个 1 秒，然后点击停止按钮。</span><span class="sxs-lookup"><span data-stu-id="5ed14-232">To finish recording tap and hold the screen for another 1 second, then tap the stop button.</span></span>
4. <span data-ttu-id="5ed14-233">录制的视频加载后，将显示一个预览按钮 （蓝色按钮），点击观看录制的视频。</span><span class="sxs-lookup"><span data-stu-id="5ed14-233">Once the recorded video loads, a Preview button (blue button) will appear, tap to watch the recorded video.</span></span>
5. <span data-ttu-id="5ed14-234">打开共享表并选择保存到本机照片。</span><span class="sxs-lookup"><span data-stu-id="5ed14-234">Open the Share sheet and select Save to camera roll.</span></span>

### <a name="example-scene"></a><span data-ttu-id="5ed14-235">示例场景</span><span class="sxs-lookup"><span data-stu-id="5ed14-235">Example scene</span></span>

<span data-ttu-id="5ed14-236">可在示例场景[HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)</span><span class="sxs-lookup"><span data-stu-id="5ed14-236">An example scene can be found in [HoloToolkit-Examples\SpectatorView\Scenes\SpectatorViewExample.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpectatorView/Scenes/SpectatorViewExample.unity)</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="5ed14-237">疑难解答</span><span class="sxs-lookup"><span data-stu-id="5ed14-237">Troubleshooting</span></span>

<span data-ttu-id="5ed14-238">**在 Unity 编辑器不会连接到托管的 HoloLens 设备的会话**</span><span class="sxs-lookup"><span data-stu-id="5ed14-238">**The Unity Editor won't connect to a session hosted by a HoloLens device**</span></span>

- <span data-ttu-id="5ed14-239">这可能是 Windows 防火墙。</span><span class="sxs-lookup"><span data-stu-id="5ed14-239">This could be the Windows Firewall.</span></span>
- <span data-ttu-id="5ed14-240">转到 Windows 防火墙选项。</span><span class="sxs-lookup"><span data-stu-id="5ed14-240">Go to Windows Firewall options.</span></span>
- <span data-ttu-id="5ed14-241">允许应用或功能通过 Windows 防火墙。</span><span class="sxs-lookup"><span data-stu-id="5ed14-241">Allow an app or feature through Windows Firewall.</span></span>
- <span data-ttu-id="5ed14-242">所有实例的 Unity 编辑器中的列表刻度线，域、 专用和公共。</span><span class="sxs-lookup"><span data-stu-id="5ed14-242">For all instances of Unity Editor in the list tick, Domain, Private and Public.</span></span>
- <span data-ttu-id="5ed14-243">然后返回到 Windows 防火墙选项。</span><span class="sxs-lookup"><span data-stu-id="5ed14-243">Then go back to Windows Firewall options.</span></span>
- <span data-ttu-id="5ed14-244">单击高级的设置。</span><span class="sxs-lookup"><span data-stu-id="5ed14-244">Click Advanced settings.</span></span>
- <span data-ttu-id="5ed14-245">单击入站的规则。</span><span class="sxs-lookup"><span data-stu-id="5ed14-245">Click Inbound Rules.</span></span>
- <span data-ttu-id="5ed14-246">在 Unity 编辑器的所有实例应都具有一个绿色对勾。</span><span class="sxs-lookup"><span data-stu-id="5ed14-246">All instances of Unity Editor should have a green tick.</span></span>
- <span data-ttu-id="5ed14-247">在 Unity 编辑器的任何实例，没有一个绿色的勾选标记：</span><span class="sxs-lookup"><span data-stu-id="5ed14-247">For any instances of Unity Editor that don't have a green tick:</span></span>
    - <span data-ttu-id="5ed14-248">双击它。</span><span class="sxs-lookup"><span data-stu-id="5ed14-248">Double click it.</span></span>
    - <span data-ttu-id="5ed14-249">在操作对话框中选择允许连接。</span><span class="sxs-lookup"><span data-stu-id="5ed14-249">In the action dialog select Allow the connection.</span></span>
    - <span data-ttu-id="5ed14-250">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="5ed14-250">Click OK.</span></span>
    - <span data-ttu-id="5ed14-251">重新启动 Unity 编辑器。</span><span class="sxs-lookup"><span data-stu-id="5ed14-251">Restart the Unity Editor.</span></span>

<span data-ttu-id="5ed14-252">**在运行时 iPhone 屏幕上显示"查找 Floor..."但不显示 AR 标记。**</span><span class="sxs-lookup"><span data-stu-id="5ed14-252">**At runtime the iPhone screen says "Locating Floor..." but does not display an AR marker.**</span></span>

- <span data-ttu-id="5ed14-253">这部 iphone 手机寻找水平面尝试指向 iPhone 照相机向 floor 或表。</span><span class="sxs-lookup"><span data-stu-id="5ed14-253">The iPhone is looking for a horizontal surface so try pointing the iPhone camera towards the floor or a table.</span></span> <span data-ttu-id="5ed14-254">这将有助于 ARKit 发现图面必要论据在空间上与 HoloLens 的同步。</span><span class="sxs-lookup"><span data-stu-id="5ed14-254">This will help ARKit find surfaces necessary to spatially sync with HoloLens.</span></span>

<span data-ttu-id="5ed14-255">**HoloLens 照相机未开启自动当 iPhone 尝试加入。**</span><span class="sxs-lookup"><span data-stu-id="5ed14-255">**HoloLens camera does not turn on automatically when iPhone tries to join.**</span></span>

- <span data-ttu-id="5ed14-256">请确保 HoloLens 和 iPhone 相同的 Wi-fi 网络上运行。</span><span class="sxs-lookup"><span data-stu-id="5ed14-256">Make sure both HoloLens and iPhone are running on the same Wi-Fi network.</span></span>

<span data-ttu-id="5ed14-257">**正在运行的其他 Spectator 视图应用其他 hololens 时启动 Spectator 视图应用程序在移动设备上的，打开其摄像机**</span><span class="sxs-lookup"><span data-stu-id="5ed14-257">**When launching an Spectator View application on a mobile device, other hololens running other Spectator View apps turn on their camera**</span></span>

- <span data-ttu-id="5ed14-258">转到 NewDeviceDiscovery 组件并更改为两个唯一值的广播密钥和广播的端口。</span><span class="sxs-lookup"><span data-stu-id="5ed14-258">Goto the NewDeviceDiscovery component and change the both the Broadcast Key and Broadcast port to two unique values.</span></span>
- <span data-ttu-id="5ed14-259">转到 SpectatorViewDiscovery 并将广播密钥和广播端口更改为另一组唯一的数字。</span><span class="sxs-lookup"><span data-stu-id="5ed14-259">Go to SpectatorViewDiscovery and change the Broadcast Key and Broadcast port to another set of unique numbers.</span></span>

<span data-ttu-id="5ed14-260">**HoloLens 不会使用 mac 的 Unity 编辑器进行连接。**</span><span class="sxs-lookup"><span data-stu-id="5ed14-260">**The HoloLens won't connect with the mac Unity Editor.**</span></span>

- <span data-ttu-id="5ed14-261">这是一个已知的问题，无法链接到的 Unity 版本。</span><span class="sxs-lookup"><span data-stu-id="5ed14-261">This is a known issue which could be linked to the Unity version.</span></span> <span data-ttu-id="5ed14-262">在 iPhone 中的生成仍适用，而且连接正常。</span><span class="sxs-lookup"><span data-stu-id="5ed14-262">Building to the iPhone should still work and connect as normal.</span></span>

<span data-ttu-id="5ed14-263">**HoloLens 照相机将启用，但不能扫描标记。**</span><span class="sxs-lookup"><span data-stu-id="5ed14-263">**The HoloLens camera turns on but is not able to scan the marker.**</span></span>

- <span data-ttu-id="5ed14-264">请确保生成的应用程序使用相同的 Unity 编辑器实例 （不要之间不关闭 Unity 生成） 的所有版本。</span><span class="sxs-lookup"><span data-stu-id="5ed14-264">Ensure that you build all versions of the application using the same Unity Editor instance (do not close Unity between builds).</span></span> <span data-ttu-id="5ed14-265">这是由于未知问题而使用 Unity。</span><span class="sxs-lookup"><span data-stu-id="5ed14-265">This is due to an unknown issue with Unity.</span></span>

## <a name="spectator-view-pro"></a><span data-ttu-id="5ed14-266">Spectator 查看 Pro</span><span class="sxs-lookup"><span data-stu-id="5ed14-266">Spectator View Pro</span></span>

![Spectator 视图设置](images/spectatorview-300px.png)

<span data-ttu-id="5ed14-268">使用 Spectator 视图 Pro 涉及以下四个组件：</span><span class="sxs-lookup"><span data-stu-id="5ed14-268">Using Spectator View Pro involves these four components:</span></span>
1. <span data-ttu-id="5ed14-269">具体而言，若要启用 spectator 视图，它为基础而构建的应用[混合现实中的共享体验](shared-experiences-in-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="5ed14-269">An app built specifically to enable spectator view, which is based on [shared experiences in mixed reality](shared-experiences-in-mixed-reality.md).</span></span>
2. <span data-ttu-id="5ed14-270">用户戴上使用应用的 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5ed14-270">A user wearing HoloLens using the app.</span></span>
3. <span data-ttu-id="5ed14-271">Spectator 视图照相机远程测试机组提供第三个人角度来看视频。</span><span class="sxs-lookup"><span data-stu-id="5ed14-271">A spectator view camera rig providing a third-person perspective video.</span></span>
4. <span data-ttu-id="5ed14-272">运行的共享的体验应用和组合的情况下为 spectator 视图视频全息的桌面 PC。</span><span class="sxs-lookup"><span data-stu-id="5ed14-272">A desktop PC running the shared experience app and compositing the holograms into a spectator view video.</span></span>

![Spectator 视图 Pro 设置](images/hololensspectatorview-500px.jpg) 

### <a name="use-cases"></a><span data-ttu-id="5ed14-274">用例</span><span class="sxs-lookup"><span data-stu-id="5ed14-274">Use cases</span></span>

>[!VIDEO https://www.youtube.com/embed/DgIHjxoPy_c]


<span data-ttu-id="5ed14-275">*可以共享您全息版的作品使用 spectator 视图，无论他们是静止图像、 视频剪辑或实时演示。*</span><span class="sxs-lookup"><span data-stu-id="5ed14-275">*Spectator view can be used for sharing your holographic creations, whether they're a still image, a video clip, or a live demonstration.*</span></span>


<span data-ttu-id="5ed14-276">有很好地配合此技术的三个关键方案：</span><span class="sxs-lookup"><span data-stu-id="5ed14-276">There are three key scenarios that work well with this technology:</span></span>

<span data-ttu-id="5ed14-277">**1.照片拍摄**</span><span class="sxs-lookup"><span data-stu-id="5ed14-277">**1. Photo capture**</span></span><br>
<span data-ttu-id="5ed14-278">使用此技术，您可以捕获你全息的高分辨率图像。</span><span class="sxs-lookup"><span data-stu-id="5ed14-278">Using this technology, you can capture high resolution images of your holograms.</span></span> <span data-ttu-id="5ed14-279">这些映像可用于展示在市场营销事件的内容，将发送到潜在的客户端，或甚至提交到 Windows 应用商店应用程序。</span><span class="sxs-lookup"><span data-stu-id="5ed14-279">These images can be used to showcase content at marketing events, send to your potential clients, or even submit your application to the Windows Store.</span></span> <span data-ttu-id="5ed14-280">您可以决定你想要用于捕获这些映像的照片照相机，这种情况下您可能更倾向于质量 DSLR 照相机。</span><span class="sxs-lookup"><span data-stu-id="5ed14-280">You get to decide which photo camera you would like to use to capture these images, as such you may prefer a quality DSLR camera.</span></span>


<span data-ttu-id="5ed14-281">![Spectator 视图 Pro 照片捕获示例](images/fall-350px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5ed14-281">![Spectator View Pro photo capture example](images/fall-350px.jpg)</span></span><br>
<span data-ttu-id="5ed14-282">*捕获的照片示例-从而使其显示在地板由岩浆。*</span><span class="sxs-lookup"><span data-stu-id="5ed14-282">*Photo capture example - making it appear the floor is made of lava.*</span></span>


<span data-ttu-id="5ed14-283">**2.视频捕获**</span><span class="sxs-lookup"><span data-stu-id="5ed14-283">**2. Video capture**</span></span><br>
<span data-ttu-id="5ed14-284">视频是最佳的故事告诉机制，用于与许多人共享全息版的应用体验。</span><span class="sxs-lookup"><span data-stu-id="5ed14-284">Videos are the best story telling mechanism for sharing a holographic app experience with many people.</span></span> <span data-ttu-id="5ed14-285">Spectator 视图，可以选择最的适合你想要展示你的应用的照相机、 可重用功能区和帧。</span><span class="sxs-lookup"><span data-stu-id="5ed14-285">Spectator view lets you choose the camera, lens, and framing that best suits how you want to showcase your app.</span></span> <span data-ttu-id="5ed14-286">它会将你的基于视频硬件上的视频质量的控件中必须可用。</span><span class="sxs-lookup"><span data-stu-id="5ed14-286">It puts you in control of the video quality based on the video hardware you have available.</span></span>

<span data-ttu-id="5ed14-287">![Spectator 视图 Pro 视频捕获示例](images/spectatorviewvideo.gif)</span><span class="sxs-lookup"><span data-stu-id="5ed14-287">![Spectator View Pro video capture example](images/spectatorviewvideo.gif)</span></span><br>
<span data-ttu-id="5ed14-288">*视频捕获示例-录制混合的现实的协作体验。*</span><span class="sxs-lookup"><span data-stu-id="5ed14-288">*Video capture example - recording a mixed reality collaboration experience.*</span></span>


<span data-ttu-id="5ed14-289">**3.实时演示**</span><span class="sxs-lookup"><span data-stu-id="5ed14-289">**3. Live demonstrations**</span></span><br>
<span data-ttu-id="5ed14-290">Spectator 视图是实时演示的首选的方法，如照相机的位置保持不稳定或控制。</span><span class="sxs-lookup"><span data-stu-id="5ed14-290">Spectator view is a preferred approach for live demonstrations as the camera position remains steady or controlled.</span></span> <span data-ttu-id="5ed14-291">因为您可以使用高质量视频摄像机，也可以生成高质量图像适用于大屏幕。</span><span class="sxs-lookup"><span data-stu-id="5ed14-291">Because you can use a high-quality video camera, you can also produce high-quality images meant for a big screen.</span></span> <span data-ttu-id="5ed14-292">这也是适用于流式处理在屏幕上，可能给为其启用排队等候了预先参与者的现场演示。</span><span class="sxs-lookup"><span data-stu-id="5ed14-292">This is also appropriate for streaming live demos on a screen, possibly to eager participants waiting in line for their turn.</span></span>

### <a name="comparing-video-capture-techniques"></a><span data-ttu-id="5ed14-293">比较视频捕获方法</span><span class="sxs-lookup"><span data-stu-id="5ed14-293">Comparing video capture techniques</span></span>

<span data-ttu-id="5ed14-294">[混合现实捕获](mixed-reality-capture.md)(MRC) 提供了视频复合的 HoloLens 用户从第一个人-的-角度看到的内容。</span><span class="sxs-lookup"><span data-stu-id="5ed14-294">[Mixed reality capture](mixed-reality-capture.md) (MRC) provides a video composite of what the HoloLens user is seeing from a first person point-of-view.</span></span> <span data-ttu-id="5ed14-295">Spectator 视图生成从第三个人角度看，允许视频观察程序中，若要查看具有全息和戴上 HoloLens 设备的用户环境的视频。</span><span class="sxs-lookup"><span data-stu-id="5ed14-295">Spectator view produces a video from a third-person perspective, allowing the video observer to see the environment with holograms and the user wearing a HoloLens device.</span></span> <span data-ttu-id="5ed14-296">由于你有摄像机的选择，spectator 视图还可以生成更高的分辨率和比内置 HoloLens 照相机用于 MRC 映像更好的高质量图像。</span><span class="sxs-lookup"><span data-stu-id="5ed14-296">Because you have a choice of camera, spectator views can also produce higher resolution and better quality images than the built-in HoloLens camera used for MRC images.</span></span> <span data-ttu-id="5ed14-297">出于此原因，spectator 视图更适合用于市场营销的视频，Windows 应用商店中的应用图像或投影为受众的实时视图。</span><span class="sxs-lookup"><span data-stu-id="5ed14-297">For this reason, spectator view is better suited for app images in the Windows Store, marketing videos, or for projecting a live view for an audience.</span></span>

<span data-ttu-id="5ed14-298">![查看 Pro spectator Microsoft 主题演讲演示文稿中使用的专业照相机](images/spectator-view-professional-red-camera-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5ed14-298">![Spectator View Pro professional camera used in Microsoft keynote presentations](images/spectator-view-professional-red-camera-300px.jpg)</span></span><br>
<span data-ttu-id="5ed14-299">*查看 Pro spectator Microsoft 主题演讲演示文稿中使用的专业照相机*</span><span class="sxs-lookup"><span data-stu-id="5ed14-299">*Spectator View Pro professional camera used in Microsoft keynote presentations*</span></span>


<span data-ttu-id="5ed14-300">Spectator 视图后如何 Microsoft HoloLens 具有体验时呈现给受众自一开始以来该产品已在 2015 年 1 月宣布必不可少的组成部分。</span><span class="sxs-lookup"><span data-stu-id="5ed14-300">Spectator view has been an essential piece of how Microsoft HoloLens has presented experiences to audiences since the very beginning when the product was announced in January 2015.</span></span> <span data-ttu-id="5ed14-301">专业的安装程序使用具有很高的要求和成本高昂的价格标记使用它。</span><span class="sxs-lookup"><span data-stu-id="5ed14-301">The professional setup used had high demands and an expensive price tag to go with it.</span></span> <span data-ttu-id="5ed14-302">例如，照相机使用 genlock 信号以确保与跟踪系统 HoloLens 协调的精确计时。</span><span class="sxs-lookup"><span data-stu-id="5ed14-302">For example, the camera uses a genlock signal to ensure precise timing that coordinates with the HoloLens tracking system.</span></span> <span data-ttu-id="5ed14-303">在此设置中，移动 spectator 视图摄像头，可能会同时保持全息稳定来匹配人，他们将看到直接在 HoloLens 中的体验的体验。</span><span class="sxs-lookup"><span data-stu-id="5ed14-303">In this setup, moving the spectator view camera was possible while keeping holograms stable to match the experience of someone who is seeing the experience directly in HoloLens.</span></span>

<span data-ttu-id="5ed14-304">Spectator 视图的开放源代码版本权衡移动照相机远程测试机组，以大幅降低总体安装程序的成本的功能。</span><span class="sxs-lookup"><span data-stu-id="5ed14-304">The open-source version of spectator view trades off the ability to move the camera rig in order to dramatically lower the cost of the overall setup.</span></span> <span data-ttu-id="5ed14-305">此项目使用严格装载到 HoloLens 外部照相机高清晰照片和视频 holographic Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="5ed14-305">This project uses an external camera rigidly mounted to a HoloLens to take high-definition pictures and video of your holographic Unity project.</span></span> <span data-ttu-id="5ed14-306">**在实时演示，照相机应保持在固定位置。**</span><span class="sxs-lookup"><span data-stu-id="5ed14-306">**During live demonstrations, the camera should remain in a fixed position.**</span></span> <span data-ttu-id="5ed14-307">照相机移动可能会导致全息图抖动或偏差。</span><span class="sxs-lookup"><span data-stu-id="5ed14-307">Movement of the camera can lead to hologram jitter or drift.</span></span> <span data-ttu-id="5ed14-308">这是因为视频帧的计时和全息在 PC 上的呈现方式可能不会精确同步。</span><span class="sxs-lookup"><span data-stu-id="5ed14-308">This is because the timing of the video frame and the rendering of holograms on the PC may not be precisely synchronized.</span></span> <span data-ttu-id="5ed14-309">因此，保持稳定照相机或限制移动将产生接近戴上 HoloLens 的人可以看到结果。</span><span class="sxs-lookup"><span data-stu-id="5ed14-309">Therefore, keeping the camera steady or limiting movement will produce a result close to what the person wearing a HoloLens can see.</span></span>

<span data-ttu-id="5ed14-310">若要使应用能够准备好进行 spectator 视图，您将需要生成[共享体验](holograms-240.md)应用，并确保应用程序可以运行 HoloLens 以及 Unity 编辑器中的桌面。</span><span class="sxs-lookup"><span data-stu-id="5ed14-310">To make your app ready for spectator view, you'll need to build a [shared experience](holograms-240.md) app and ensure the app can run on both HoloLens as well as desktop in the Unity editor.</span></span> <span data-ttu-id="5ed14-311">桌面版本的应用会在该复合视频源和呈现全息中生成的其他组件。</span><span class="sxs-lookup"><span data-stu-id="5ed14-311">The desktop version of the app will have additional components built in that composite the video feed with the rendered holograms.</span></span>

## <a name="how-to-set-up-spectator-view-pro"></a><span data-ttu-id="5ed14-312">如何设置 Spectator 视图 Pro</span><span class="sxs-lookup"><span data-stu-id="5ed14-312">How to set up Spectator View Pro</span></span> 

### <a name="requirements"></a><span data-ttu-id="5ed14-313">要求</span><span class="sxs-lookup"><span data-stu-id="5ed14-313">Requirements</span></span>

![Spectator 视图 Pro 远程测试机组](images/spectatorviewrig-350px.jpg)

#### <a name="hardware-shopping-list"></a><span data-ttu-id="5ed14-315">硬件购物列表</span><span class="sxs-lookup"><span data-stu-id="5ed14-315">Hardware shopping list</span></span>

<span data-ttu-id="5ed14-316">下面是推荐的硬件列表，但太尝试使用其他兼容的单位。</span><span class="sxs-lookup"><span data-stu-id="5ed14-316">Below is a recommended list of hardware, but you can experiment with other compatible units too.</span></span> 

|<span data-ttu-id="5ed14-317">硬件组件</span><span class="sxs-lookup"><span data-stu-id="5ed14-317">Hardware component</span></span>                                                                     |<span data-ttu-id="5ed14-318">建议</span><span class="sxs-lookup"><span data-stu-id="5ed14-318">Recommendation</span></span>               | 
|:--------------------------------------------------------------------------------------|:----------------------------|
|<span data-ttu-id="5ed14-319">适用于使用 HoloLens 模拟器 holographic 开发 PC 配置</span><span class="sxs-lookup"><span data-stu-id="5ed14-319">A PC configuration that works for holographic development with the HoloLens emulator</span></span>  |                              | 
|<span data-ttu-id="5ed14-320">照相机，摄像机带有 out HDMI 或照片拍摄 SDK</span><span class="sxs-lookup"><span data-stu-id="5ed14-320">Camera with HDMI out or photo capture SDK</span></span>                                             | <span data-ttu-id="5ed14-321">对于照片和视频捕获，我们已测试[Canon EOS 5d 标记 III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III)照相机。</span><span class="sxs-lookup"><span data-stu-id="5ed14-321">For photo and video capture, we have tested the [Canon EOS 5D Mark III](https://www.amazon.com/Canon-Frame-Full-HD-Digital-Camera/dp/B007FGYZFI/ref=sr_1_3?s=photo&ie=UTF8&qid=1480537693&sr=1-3&keywords=Canon+5D+Mark+III) camera.</span></span> <span data-ttu-id="5ed14-322">有关实时演示，我们已测试[Blackmagic 设计生产照相机 4k](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k)。</span><span class="sxs-lookup"><span data-stu-id="5ed14-322">For live demonstrations, we have tested the [Blackmagic Design Production Camera 4K](https://www.amazon.com/Blackmagic-Design-Production-Camera-Mount/dp/B00CWLSHYG/ref=sr_1_1?s=photo&ie=UTF8&qid=1480537790&sr=1-1&keywords=blackmagic+design+production+camera+4k).</span></span><br><br><span data-ttu-id="5ed14-323">请注意，使用 (例如 GoPro) 出 HDMI 任何照相机应适用。</span><span class="sxs-lookup"><span data-stu-id="5ed14-323">Note, any camera with HDMI out (e.g. GoPro) should work.</span></span> <span data-ttu-id="5ed14-324">使用我们的视频的许多[Canon EF 14 mm f/2.8 L II USM Ultra-wide 角度固定可重用功能区](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q)，但应选择满足你的需求的相机镜头。</span><span class="sxs-lookup"><span data-stu-id="5ed14-324">Many of our videos use the [Canon EF 14mm f/2.8L II USM Ultra-Wide Angle Fixed Lens](https://www.amazon.com/Canon-Ultra-Wide-Angle-Digital-Cameras/dp/B000V5P94Q), but you should choose a camera lens that meets your needs.</span></span> | 
|<span data-ttu-id="5ed14-325">捕获有关您的 PC 以获得颜色帧从照相机校准你远程测试机组并预览复合场景的卡</span><span class="sxs-lookup"><span data-stu-id="5ed14-325">Capture card for your PC to get color frames from your camera to calibrate your rig and preview your composite scene</span></span> |  <span data-ttu-id="5ed14-326">我们已测试[Blackmagic 设计强度 Pro 4k 捕获卡](https://www.amazon.com/dp/B00U3QNP7Q)。</span><span class="sxs-lookup"><span data-stu-id="5ed14-326">We have tested the [Blackmagic Design Intensity Pro 4K capture card](https://www.amazon.com/dp/B00U3QNP7Q).</span></span> | 
|<span data-ttu-id="5ed14-327">电缆</span><span class="sxs-lookup"><span data-stu-id="5ed14-327">Cables</span></span>                                                                                 |  <span data-ttu-id="5ed14-328">[为迷你 HDMI HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00)将您的照相机附加到捕获卡。</span><span class="sxs-lookup"><span data-stu-id="5ed14-328">[HDMI to Mini HDMI](https://www.amazon.com/AmazonBasics-High-Speed-Mini-HDMI-HDMI-Cable/dp/B014I8UHXE?ie=UTF8&psc=1&redirect=true&ref_=oh_aui_detailpage_o03_s00) for attaching your camera to your capture card.</span></span> <span data-ttu-id="5ed14-329">请确保你购买符合您的照相机 HDMI 外形规格。</span><span class="sxs-lookup"><span data-stu-id="5ed14-329">Ensure you purchase an HDMI form factor that fits your camera.</span></span> <span data-ttu-id="5ed14-330">(GoPro，例如，通过输出[Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1)。)</span><span class="sxs-lookup"><span data-stu-id="5ed14-330">(GoPro, for instance, outputs over [Micro HDMI](https://www.amazon.com/dp/B014I8U33I/ref=twister_B0198TA40O?_encoding=UTF8&psc=1).)</span></span><br><br><span data-ttu-id="5ed14-331">[HDMI 电缆](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1)用于查看源预览监视器或电视上复合</span><span class="sxs-lookup"><span data-stu-id="5ed14-331">[HDMI cable](https://www.amazon.com/dp/B014I8TC4E/ref=twister_B016I3XG0S?_encoding=UTF8&th=1) for viewing the composite feed on a preview monitor or television</span></span> | 
|<span data-ttu-id="5ed14-332">加工 aluminum 大括号，使你 HoloLens 连接到摄像机。</span><span class="sxs-lookup"><span data-stu-id="5ed14-332">Machined aluminum bracket to connect your HoloLens to the camera.</span></span> | [<span data-ttu-id="5ed14-333">Aluminum 括号</span><span class="sxs-lookup"><span data-stu-id="5ed14-333">Aluminum bracket</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/HoloLens_Mount.stp)   | 
|<span data-ttu-id="5ed14-334">3D 打印适配器以便连接到摄像机 hotshoe HoloLens 装入。</span><span class="sxs-lookup"><span data-stu-id="5ed14-334">3D printed adapter to connect the HoloLens mount to the camera hotshoe.</span></span>| [<span data-ttu-id="5ed14-335">3D 打印的适配器</span><span class="sxs-lookup"><span data-stu-id="5ed14-335">3D printed adapter</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/blob/master/LegacySpectatorView/Hardware/Mount_Adapter.stl)  | 
|<span data-ttu-id="5ed14-336">Hotshoe fastener 装载 hotshoe 适配器</span><span class="sxs-lookup"><span data-stu-id="5ed14-336">Hotshoe fastener to mount the hotshoe adapter</span></span>                                       |  [<span data-ttu-id="5ed14-337">Hotshoe Fastener</span><span class="sxs-lookup"><span data-stu-id="5ed14-337">Hotshoe Fastener</span></span>](https://www.amazon.com/Fotasy-SCX2-Adapter-Premier-Cleaning/dp/B00HPAPFNU/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) | 
|<span data-ttu-id="5ed14-338">已分类的 nuts、 bolt 和工具</span><span class="sxs-lookup"><span data-stu-id="5ed14-338">Assorted nuts, bolts, and tools</span></span>                                                |  [<span data-ttu-id="5ed14-339">1/4 到 20 个"nuts</span><span class="sxs-lookup"><span data-stu-id="5ed14-339">1/4-20" Nuts</span></span>](https://www.amazon.com/Hillman-Group-150003-20-Inch-100-Pack/dp/B000BPEPNW/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img)<br>[<span data-ttu-id="5ed14-340">1/4-20"x 3/4"Bolt</span><span class="sxs-lookup"><span data-stu-id="5ed14-340">1/4-20" x 3/4" Bolts</span></span>](https://www.amazon.com/Hard-Find-Fastener-014973100032-4-20-Inch/dp/B004S6RZPK/ref=redir_mobile_desktop?ie=UTF8&psc=1&ref_=yo_ii_img) <br>[<span data-ttu-id="5ed14-341">7/16 nut 驱动程序</span><span class="sxs-lookup"><span data-stu-id="5ed14-341">7/16 Nut Driver</span></span>](https://www.amazon.com/Klein-Tools-630-7-Cushion-Grip-Hollow-Shank/dp/B000BPG4CW/ref=sr_1_1?ie=UTF8&qid=1479853212&sr=8-1)<br>[<span data-ttu-id="5ed14-342">T15 Torx</span><span class="sxs-lookup"><span data-stu-id="5ed14-342">T15 Torx</span></span>](https://www.amazon.com/Stanley-60-011-Standard-Torx-Screwdriver/dp/B000KFXDWW/ref=sr_1_1?ie=UTF8&qid=1479853303&sr=8-1)<br>[<span data-ttu-id="5ed14-343">T7 Torx</span><span class="sxs-lookup"><span data-stu-id="5ed14-343">T7 Torx</span></span>](https://www.amazon.com/SE-7542ST-6-Piece-Professional-Screwdriver/dp/B000ST3K3W/ref=sr_1_1?ie=UTF8&qid=1479853479&sr=8-1) | 

#### <a name="software-components"></a><span data-ttu-id="5ed14-344">软件组件</span><span class="sxs-lookup"><span data-stu-id="5ed14-344">Software components</span></span>

1. <span data-ttu-id="5ed14-345">从下载的软件[spectator 视图的 GitHub 项目](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)。</span><span class="sxs-lookup"><span data-stu-id="5ed14-345">Software downloaded from the [GitHub project for spectator view](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView).</span></span>
2. <span data-ttu-id="5ed14-346">[Blackmagic 捕获卡 SDK](https://www.blackmagicdesign.com/support)。 \\</span><span class="sxs-lookup"><span data-stu-id="5ed14-346">[Blackmagic Capture Card SDK](https://www.blackmagicdesign.com/support).\\</span></span>
 <span data-ttu-id="5ed14-347">桌面的视频开发人员 SDK 在"下载最新"的搜索。</span><span class="sxs-lookup"><span data-stu-id="5ed14-347">Search for Desktop Video Developer SDK in "Latest Downloads".</span></span>
3. <span data-ttu-id="5ed14-348">[Blackmagic 桌面视频运行时](https://www.blackmagicdesign.com/support)。 \\</span><span class="sxs-lookup"><span data-stu-id="5ed14-348">[Blackmagic Desktop Video Runtime](https://www.blackmagicdesign.com/support).\\</span></span>
 <span data-ttu-id="5ed14-349">在"下载最新"的桌面的视频软件更新的搜索。 \\</span><span class="sxs-lookup"><span data-stu-id="5ed14-349">Search for Desktop Video Software Update in "Latest Downloads".\\</span></span>
 <span data-ttu-id="5ed14-350">请确保版本编号匹配项的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="5ed14-350">Ensure the version number matches the SDK version.</span></span>
4. <span data-ttu-id="5ed14-351">[OpenCV 3.1](https://opencv.org/releases.html)校准或视频捕获，而无需 Blackmagic 捕获卡。</span><span class="sxs-lookup"><span data-stu-id="5ed14-351">[OpenCV 3.1](https://opencv.org/releases.html) For calibration or video capture without the Blackmagic capture card.</span></span>
5. <span data-ttu-id="5ed14-352">[Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) （可选）。 \\</span><span class="sxs-lookup"><span data-stu-id="5ed14-352">[Canon SDK](https://www.usa.canon.com/internet/portal/us/home/explore/solutions-services/digital-camera-sdk-information) (Optional).\\</span></span>
 <span data-ttu-id="5ed14-353">如果您使用 Canon 摄像机，并且有权访问 Canon SDK，你可以为您的 PC 以获取更高分辨率图像接入照相机。</span><span class="sxs-lookup"><span data-stu-id="5ed14-353">If you are using a Canon camera and have access to the Canon SDK, you can tether your camera to your PC to take higher resolution images.</span></span>
6. <span data-ttu-id="5ed14-354">适用于您全息版的应用程序开发的 unity。 \\</span><span class="sxs-lookup"><span data-stu-id="5ed14-354">Unity for your holographic app development.\\</span></span>
 <span data-ttu-id="5ed14-355">OSS 项目中找不到受支持的版本。</span><span class="sxs-lookup"><span data-stu-id="5ed14-355">Supported version can be found in the OSS project.</span></span>
7. <span data-ttu-id="5ed14-356">使用最新的更新的 visual Studio 2015。</span><span class="sxs-lookup"><span data-stu-id="5ed14-356">Visual Studio 2015 with latest updates.</span></span>

### <a name="building-your-own-spectator-view-pro-camera"></a><span data-ttu-id="5ed14-357">构建 Spectator 视图 Pro 照相机</span><span class="sxs-lookup"><span data-stu-id="5ed14-357">Building your own Spectator View Pro camera</span></span>

<span data-ttu-id="5ed14-358">**通知和免责声明：** 进行到 HoloLens 硬件 （包括但不是限于，设置"spectator 视图"将 HoloLens） 修改基本时应始终遵循安全防范措施。</span><span class="sxs-lookup"><span data-stu-id="5ed14-358">**NOTICE & DISCLAIMER:** When making modifications to your HoloLens hardware (including, but not limited to, setting up your HoloLens for "spectator view") basic safety precautions should always be observed.</span></span> <span data-ttu-id="5ed14-359">进行任何修改之前，阅读所有说明和手册。</span><span class="sxs-lookup"><span data-stu-id="5ed14-359">Read all instructions and manuals before making any modifications.</span></span> <span data-ttu-id="5ed14-360">它由你负责按照所有说明并使用工具的指导。</span><span class="sxs-lookup"><span data-stu-id="5ed14-360">It is your responsibility to follow all instructions and use tools as directed.</span></span> <span data-ttu-id="5ed14-361">购买或许可你 HoloLens 与有限的担保或不作任何担保。</span><span class="sxs-lookup"><span data-stu-id="5ed14-361">You may have purchased or licensed your HoloLens with a limited warranty or no warranty.</span></span> <span data-ttu-id="5ed14-362">请阅读在适用[HoloLens 许可协议或使用条款和销售](https://www.microsoft.com/hololens/support/warranty)若要了解保证选项。</span><span class="sxs-lookup"><span data-stu-id="5ed14-362">Please read your applicable [HoloLens License Agreement or Terms of Use and Sale](https://www.microsoft.com/hololens/support/warranty) to understand your warranty options.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/aKX8UMejtWc]

#### <a name="rig-assembly"></a><span data-ttu-id="5ed14-363">远程测试机组程序集</span><span class="sxs-lookup"><span data-stu-id="5ed14-363">Rig Assembly</span></span>

<span data-ttu-id="5ed14-364">![组装的 Spectator 视图 Pro 远程测试机组 HoloLens 和 DSLR 照相机的。](images/assembly.gif)</span><span class="sxs-lookup"><span data-stu-id="5ed14-364">![Assembled Spectator View Pro rig with HoloLens and DSLR camera.](images/assembly.gif)</span></span><br>
<span data-ttu-id="5ed14-365">*与 HoloLens 和 DSLR 相机已组装的 Spectator 视图 Pro 远程测试机组*</span><span class="sxs-lookup"><span data-stu-id="5ed14-365">*Assembled Spectator View Pro rig with HoloLens and DSLR camera*</span></span>


* <span data-ttu-id="5ed14-366">使用 T7 螺丝刀 headband 移除 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5ed14-366">Use a T7 screwdriver to remove the headband from the HoloLens.</span></span> <span data-ttu-id="5ed14-367">松散螺丝后，浏览它们与从另一侧一支文档活页夹。</span><span class="sxs-lookup"><span data-stu-id="5ed14-367">Once the screws are loose, poke them out with a paperclip from the other side.</span></span>
* <span data-ttu-id="5ed14-368">删除螺丝上限内使用小型平面头螺丝刀 HoloLens 面板的前面。</span><span class="sxs-lookup"><span data-stu-id="5ed14-368">Remove the screw cap on the inside front of the HoloLens visor with a small flat head screwdriver.</span></span>
* <span data-ttu-id="5ed14-369">使用 T15 螺丝刀 HoloLens 大括号，使你删除从删除小 torx bolt 和钩状附件。</span><span class="sxs-lookup"><span data-stu-id="5ed14-369">Use a T15 screwdriver to remove the small torx bolts from the HoloLens bracket to remove the U and Hook-shaped attachments.</span></span>
* <span data-ttu-id="5ed14-370">HoloLens 置于大括号对齐的面板内与前面的括号延伸公开漏洞。</span><span class="sxs-lookup"><span data-stu-id="5ed14-370">Place the HoloLens on the bracket, lining up the exposed hole on the inside of the visor with the extrusion on the front of the bracket.</span></span> <span data-ttu-id="5ed14-371">HoloLens 的手臂应通过底部的大括号球瓶保持原位。</span><span class="sxs-lookup"><span data-stu-id="5ed14-371">The HoloLens' arms should be kept in place by the pins on the bottom of the bracket.</span></span>
* <span data-ttu-id="5ed14-372">重新附加你和钩状附件来保护对括号 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="5ed14-372">Reattach the U and Hook-shaped attachments to secure the HoloLens to the bracket.</span></span>
* <span data-ttu-id="5ed14-373">附加到您的相机 hotshoe hotshoe fastener。</span><span class="sxs-lookup"><span data-stu-id="5ed14-373">Attach the hotshoe fastener to the hotshoe of your camera.</span></span>
* <span data-ttu-id="5ed14-374">将装入适配器附加到 hotshoe fastener。</span><span class="sxs-lookup"><span data-stu-id="5ed14-374">Attach the mount adapter to the hotshoe fastener.</span></span>
* <span data-ttu-id="5ed14-375">旋转适配器以便在窄端朝前且平行于照相机的可重用功能区。</span><span class="sxs-lookup"><span data-stu-id="5ed14-375">Rotate the adapter so the narrow side is facing forward and parallel to the camera's lens.</span></span>
* <span data-ttu-id="5ed14-376">使用 1/4"螺母使用 7/16 nut 驱动程序保护的位置中的适配器。</span><span class="sxs-lookup"><span data-stu-id="5ed14-376">Secure the adapter in place with a 1/4" nut using the 7/16 nut driver.</span></span>
* <span data-ttu-id="5ed14-377">将针对适配器的括号置于前面的 HoloLens 的面板是尽可能接近前置照相机的可重用功能区位置。</span><span class="sxs-lookup"><span data-stu-id="5ed14-377">Position the bracket against the adapter so the front of the HoloLens' visor is as close as possible to the front of the camera's lens.</span></span>
* <span data-ttu-id="5ed14-378">将括号附加与 4 1/4"细节使用 7/16 nut 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="5ed14-378">Attach the bracket with 4 1/4" nuts and bolts using the 7/16 nut driver.</span></span>

#### <a name="pc-setup"></a><span data-ttu-id="5ed14-379">PC 安装程序</span><span class="sxs-lookup"><span data-stu-id="5ed14-379">PC Setup</span></span>
* <span data-ttu-id="5ed14-380">从软件组件部分安装软件。</span><span class="sxs-lookup"><span data-stu-id="5ed14-380">Install the software from the software components section.</span></span>
* <span data-ttu-id="5ed14-381">将捕获卡添加到您的主板上打开 PCIe 槽。</span><span class="sxs-lookup"><span data-stu-id="5ed14-381">Add the capture card to an open PCIe slot on your motherboard.</span></span>
* <span data-ttu-id="5ed14-382">插入从照相机 HDMI 电缆连接到外部 HDMI 槽 （HDMI 接程序） 捕获卡上。</span><span class="sxs-lookup"><span data-stu-id="5ed14-382">Plug an HDMI cable from your camera to the outer HDMI slot (HDMI-In) on the capture card.</span></span>
* <span data-ttu-id="5ed14-383">插入从捕获卡上的中央 HDMI 插槽 （HDMI 扩展） HDMI 电缆连接到的可选预览监视器。</span><span class="sxs-lookup"><span data-stu-id="5ed14-383">Plug an HDMI cable from the center HDMI slot (HDMI-Out) on the capture card to an optional preview monitor.</span></span>

#### <a name="camera-setup"></a><span data-ttu-id="5ed14-384">照相机设置</span><span class="sxs-lookup"><span data-stu-id="5ed14-384">Camera Setup</span></span>
* <span data-ttu-id="5ed14-385">更改您的照相机为视频模式，因此它会输出在完整 1920 x 1080 解析而裁剪后 3:4 照片分辨率。</span><span class="sxs-lookup"><span data-stu-id="5ed14-385">Change your camera to Video Mode so it outputs at the full 1920x1080 resolution rather than a cropped 3:4 photo resolution.</span></span>
* <span data-ttu-id="5ed14-386">找到照相机的 HDMI 设置并启用**镜像**或**双监视器**。</span><span class="sxs-lookup"><span data-stu-id="5ed14-386">Find your camera's HDMI settings and enable **Mirroring** or **Dual Monitor**.</span></span>
* <span data-ttu-id="5ed14-387">将输出分辨率设置为 1080 p。</span><span class="sxs-lookup"><span data-stu-id="5ed14-387">Set the output resolution to 1080P.</span></span>
* <span data-ttu-id="5ed14-388">关闭**屏幕显示上实时查看**因此复合源中不出现任何屏幕覆盖。</span><span class="sxs-lookup"><span data-stu-id="5ed14-388">Turn off **Live View On Screen Display** so any screen overlays do not appear in the composite feed.</span></span>
* <span data-ttu-id="5ed14-389">打开您的摄像机**实时视图**。</span><span class="sxs-lookup"><span data-stu-id="5ed14-389">Turn on your camera's **Live View**.</span></span>
* <span data-ttu-id="5ed14-390">如果使用**Canon SDK**并且想要使用 flash 的单元，请禁用**无提示 LV 投篮机会控制在**。</span><span class="sxs-lookup"><span data-stu-id="5ed14-390">If using the **Canon SDK** and would like to use a flash unit, disable **Silent LV Shoot**.</span></span>
* <span data-ttu-id="5ed14-391">插入从照相机 HDMI 电缆连接到外部 HDMI 槽 （HDMI 接程序） 捕获卡上。</span><span class="sxs-lookup"><span data-stu-id="5ed14-391">Plug an HDMI cable from the camera to the outer HDMI slot (HDMI-In) on the capture card.</span></span>

#### <a name="calibration"></a><span data-ttu-id="5ed14-392">校准</span><span class="sxs-lookup"><span data-stu-id="5ed14-392">Calibration</span></span>

<span data-ttu-id="5ed14-393">设置后你 spectator 视图远程测试机组，必须以获取对你 HoloLens 照相机的位置和旋转偏移量进行调整。</span><span class="sxs-lookup"><span data-stu-id="5ed14-393">After setting up your spectator view rig, you must calibrate in order to get the position and rotation offset of your camera to your HoloLens.</span></span>
* <span data-ttu-id="5ed14-394">打开下 Calibration\Calibration.sln 的校准 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="5ed14-394">Open the Calibration Visual Studio solution under Calibration\Calibration.sln.</span></span>
* <span data-ttu-id="5ed14-395">在此解决方案中，您会发现文件 dependencies.props 这会创建用于第三方源的非独占位置的宏。</span><span class="sxs-lookup"><span data-stu-id="5ed14-395">In this solution, you will find the file dependencies.props which creates macros for the inc locations of the 3rd party sources.</span></span>
* <span data-ttu-id="5ed14-396">更新此文件的位置安装 OpenCV 3.1、 Blackmagic SDK 和 Canon SDK （如果适用）</span><span class="sxs-lookup"><span data-stu-id="5ed14-396">Update this file with the location you installed OpenCV 3.1, the Blackmagic SDK, and the Canon SDK (if applicable)</span></span>

<span data-ttu-id="5ed14-397">![在 Visual Studio 中的依赖项位置快照](images/dependencies-600px.png)</span><span class="sxs-lookup"><span data-stu-id="5ed14-397">![Dependency locations snapshot in Visual Studio](images/dependencies-600px.png)</span></span><br>
<span data-ttu-id="5ed14-398">*在 Visual Studio 中的依赖项位置快照*</span><span class="sxs-lookup"><span data-stu-id="5ed14-398">*Dependency locations snapshot in Visual Studio*</span></span>


* <span data-ttu-id="5ed14-399">输出校准模式 Calibration\CalibrationPatterns\2_66_grid_FULL.png 平面、 刚性图面上。</span><span class="sxs-lookup"><span data-stu-id="5ed14-399">Print out the calibration pattern Calibration\CalibrationPatterns\2_66_grid_FULL.png on a flat, rigid surface.</span></span>
* <span data-ttu-id="5ed14-400">通过 USB 将 HoloLens 插入您的 PC。</span><span class="sxs-lookup"><span data-stu-id="5ed14-400">Plug your HoloLens into your PC over USB.</span></span>
* <span data-ttu-id="5ed14-401">更新预处理器定义**HOLOLENS_USER**并**HOLOLENS_PW**中**stdafx.h**有 HoloLens' 设备门户凭据。</span><span class="sxs-lookup"><span data-stu-id="5ed14-401">Update the preprocessor definitions **HOLOLENS_USER** and **HOLOLENS_PW** in **stdafx.h** with your HoloLens' device portal credentials.</span></span>
* <span data-ttu-id="5ed14-402">HDMI 通过将您的照相机附加到您捕获的卡，并将其打开。</span><span class="sxs-lookup"><span data-stu-id="5ed14-402">Attach your camera to your capture card over HDMI and turn it on.</span></span>
* <span data-ttu-id="5ed14-403">运行校准解决方案。</span><span class="sxs-lookup"><span data-stu-id="5ed14-403">Run the Calibration solution.</span></span>
* <span data-ttu-id="5ed14-404">移动棋盘图案周围的视图如下：</span><span class="sxs-lookup"><span data-stu-id="5ed14-404">Move the checkerboard pattern around the view like this:</span></span>

<span data-ttu-id="5ed14-405">![校准 Spectator 视图 Pro 远程测试机组](images/calibration.gif)</span><span class="sxs-lookup"><span data-stu-id="5ed14-405">![Calibrating the Spectator View Pro rig](images/calibration.gif)</span></span><br>
<span data-ttu-id="5ed14-406">*校准 Spectator 视图 Pro 远程测试机组*</span><span class="sxs-lookup"><span data-stu-id="5ed14-406">*Calibrating the Spectator View Pro rig*</span></span>


* <span data-ttu-id="5ed14-407">棋盘视图中时，将自动执行图片。</span><span class="sxs-lookup"><span data-stu-id="5ed14-407">A picture will automatically be taken when a checkerboard is in view.</span></span> <span data-ttu-id="5ed14-408">然后转到下一步姿势之前查找白光 HoloLens 的面板上。</span><span class="sxs-lookup"><span data-stu-id="5ed14-408">Look for the white light on the HoloLens' visor before advancing to the next pose.</span></span>
* <span data-ttu-id="5ed14-409">完成后，按**Enter**焦点创建校准应用**CalibrationData.txt**文件。</span><span class="sxs-lookup"><span data-stu-id="5ed14-409">When finished, press **Enter** with the Calibration app in focus to create a **CalibrationData.txt** file.</span></span>
* <span data-ttu-id="5ed14-410">此文件将保存到**Documents\CalibrationFiles\CalibrationData.txt**</span><span class="sxs-lookup"><span data-stu-id="5ed14-410">This file will be saved to **Documents\CalibrationFiles\CalibrationData.txt**</span></span>
* <span data-ttu-id="5ed14-411">检查此文件以查看是否准确校准数据：</span><span class="sxs-lookup"><span data-stu-id="5ed14-411">Inspect this file to see if your calibration data is accurate:</span></span>
   * <span data-ttu-id="5ed14-412">**DSLR RMS**应接近于 0。</span><span class="sxs-lookup"><span data-stu-id="5ed14-412">**DSLR RMS** should be close to 0.</span></span>
   * <span data-ttu-id="5ed14-413">**HoloLens RMS**应接近于 0。</span><span class="sxs-lookup"><span data-stu-id="5ed14-413">**HoloLens RMS** should be close to 0.</span></span>
   * <span data-ttu-id="5ed14-414">**立体声 RMS**可能是 20-50，这是可以接受因为之间两个相机的视野可能不同。</span><span class="sxs-lookup"><span data-stu-id="5ed14-414">**Stereo RMS** may be 20-50, this is acceptable since the field of view between the two cameras may be different.</span></span>
   * <span data-ttu-id="5ed14-415">**翻译**是连接的相机镜头到 HoloLens 的照相机的距离。</span><span class="sxs-lookup"><span data-stu-id="5ed14-415">**Translation** is the distance from the HoloLens' camera to the attached camera's lens.</span></span> <span data-ttu-id="5ed14-416">这是以米为单位。</span><span class="sxs-lookup"><span data-stu-id="5ed14-416">This is in meters.</span></span>
   * <span data-ttu-id="5ed14-417">**旋转**应接近标识。</span><span class="sxs-lookup"><span data-stu-id="5ed14-417">**Rotation** should be close to identity.</span></span>
   * <span data-ttu-id="5ed14-418">**DSLR_fov** y 值应接近垂直视图的字段预期的方式从滤镜的焦点长度和正文的任何照相机裁剪因素。</span><span class="sxs-lookup"><span data-stu-id="5ed14-418">**DSLR_fov** y value should be close to the vertical field of view expected from your lens' focal length and any camera body crop factor.</span></span>
* <span data-ttu-id="5ed14-419">如果上述值的任何不似乎有意义，重新校准。</span><span class="sxs-lookup"><span data-stu-id="5ed14-419">If any of the above values do not appear to make sense, recalibrate.</span></span>
* <span data-ttu-id="5ed14-420">此文件复制到**资产**目录中 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="5ed14-420">Copy this file to the **Assets** directory in your Unity project.</span></span>

### <a name="compositor"></a><span data-ttu-id="5ed14-421">Compositor</span><span class="sxs-lookup"><span data-stu-id="5ed14-421">Compositor</span></span>

<span data-ttu-id="5ed14-422">复合器是一个 Unity 扩展，以在 Unity 编辑器中的窗口的形式运行。</span><span class="sxs-lookup"><span data-stu-id="5ed14-422">The compositor is a Unity extension that runs as a window in the Unity editor.</span></span> <span data-ttu-id="5ed14-423">若要启用此功能，复合器 Visual Studio 解决方案首先需要生成。</span><span class="sxs-lookup"><span data-stu-id="5ed14-423">To enable this, the Compositor Visual Studio solution first needs to be built.</span></span>
* <span data-ttu-id="5ed14-424">打开下 Compositor\Compositor.sln 的复合器 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="5ed14-424">Open the Compositor Visual Studio solution under Compositor\Compositor.sln</span></span>
* <span data-ttu-id="5ed14-425">使用上面的校准解决方案相同的条件更新 dependencies.props。</span><span class="sxs-lookup"><span data-stu-id="5ed14-425">Update dependencies.props with the same criteria from the Calibration solution above.</span></span> <span data-ttu-id="5ed14-426">如果遵循了校准的步骤，此文件将具有已更新。</span><span class="sxs-lookup"><span data-stu-id="5ed14-426">If you followed the calibration steps, this file will already have been updated.</span></span>
* <span data-ttu-id="5ed14-427">生成整个解决方案作为版本和体系结构与你的 Unity 版本的体系结构匹配。</span><span class="sxs-lookup"><span data-stu-id="5ed14-427">Build the entire solution as Release and the architecture that matches your Unity version's architecture.</span></span> <span data-ttu-id="5ed14-428">如果有疑问，构建 x86 和 x64。</span><span class="sxs-lookup"><span data-stu-id="5ed14-428">If in doubt, build both x86 and x64.</span></span>
* <span data-ttu-id="5ed14-429">如果您生成适用于 x64 的解决方案，还生成 SpatialPerceptionHelper 项目为 x86 因为它将在 HoloLens 上运行。</span><span class="sxs-lookup"><span data-stu-id="5ed14-429">If you built the solution for x64, also build the SpatialPerceptionHelper project as x86 since it will run on the HoloLens.</span></span>
* <span data-ttu-id="5ed14-430">如果它正在运行你的应用程序，请关闭 Unity。</span><span class="sxs-lookup"><span data-stu-id="5ed14-430">Close Unity if it is running your application.</span></span> <span data-ttu-id="5ed14-431">Unity 需要进行重新启动，如果在运行时更改了 Dll。</span><span class="sxs-lookup"><span data-stu-id="5ed14-431">Unity needs to be relaunched if DLLs are changed at runtime.</span></span>
* <span data-ttu-id="5ed14-432">运行 Compositor\CopyDLL.cmd 要复制到 Unity 项目构建此解决方案中的 Dll。</span><span class="sxs-lookup"><span data-stu-id="5ed14-432">Run Compositor\CopyDLL.cmd to copy the DLLs built from this solution to your Unity project.</span></span> <span data-ttu-id="5ed14-433">此脚本将 Dll 复制到包含的示例项目。</span><span class="sxs-lookup"><span data-stu-id="5ed14-433">This script will copy the DLLs to the included sample project.</span></span> <span data-ttu-id="5ed14-434">项目设置后，可以使用命令行自变量指向你的项目的资产目录复制以及运行 CopyDLL。</span><span class="sxs-lookup"><span data-stu-id="5ed14-434">Once you have your own project set up, you can run CopyDLL with a command line argument pointing to your project's Assets directory to copy there as well.</span></span>
* <span data-ttu-id="5ed14-435">启动示例 Unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="5ed14-435">Launch the sample Unity app.</span></span>

### <a name="unity-app"></a><span data-ttu-id="5ed14-436">Unity 应用</span><span class="sxs-lookup"><span data-stu-id="5ed14-436">Unity app</span></span>

<span data-ttu-id="5ed14-437">为窗口在 Unity 编辑器中运行排序器。</span><span class="sxs-lookup"><span data-stu-id="5ed14-437">The compositor runs as a window in the Unity Editor.</span></span> <span data-ttu-id="5ed14-438">包含的示例项目具有的所有内容设置为使用 spectator 视图一次复合器 Dll 被复制。</span><span class="sxs-lookup"><span data-stu-id="5ed14-438">The included sample project has everything set up to work with spectator view once the compositor DLLs are copied.</span></span>

<span data-ttu-id="5ed14-439">Spectator 视图需要应用程序作为运行[共享体验](holograms-240.md)。</span><span class="sxs-lookup"><span data-stu-id="5ed14-439">Spectator view requires the application to be run as a [shared experience](holograms-240.md).</span></span> <span data-ttu-id="5ed14-440">这意味着在 HoloLens 发生任何应用程序状态更改需要联网更新过在 Unity 中运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="5ed14-440">This means that any application state changes that happen on the HoloLens need to be networked to update the app running in Unity too.</span></span>

<span data-ttu-id="5ed14-441">如果从新的 Unity 项目开始，你需要先进行一些设置：</span><span class="sxs-lookup"><span data-stu-id="5ed14-441">If starting from a new Unity project, you will need to do some setup first:</span></span>
* <span data-ttu-id="5ed14-442">复制**资产/加载项/HolographicCameraRig**从示例项目到项目。</span><span class="sxs-lookup"><span data-stu-id="5ed14-442">Copy **Assets/Addons/HolographicCameraRig** from the sample project to your project.</span></span>
* <span data-ttu-id="5ed14-443">将最新 MixedRealityToolkit 添加到你的项目，包括**共享**， **csc.rsp**， **gmcs.rsp**，以及**smcs.rsp**。</span><span class="sxs-lookup"><span data-stu-id="5ed14-443">Add the latest MixedRealityToolkit to your project, including **Sharing**, **csc.rsp**, **gmcs.rsp**, and **smcs.rsp**.</span></span>
* <span data-ttu-id="5ed14-444">添加你**CalibrationData.txt**文件解压缩到资产目录。</span><span class="sxs-lookup"><span data-stu-id="5ed14-444">Add your **CalibrationData.txt** file to your Assets directory.</span></span>

![Unity 资产目录快照](images/files-400px.png)

* <span data-ttu-id="5ed14-446">添加**HolographicCameraRig\Prefabs\SpectatorViewManager** prefab 向场景并填写字段：</span><span class="sxs-lookup"><span data-stu-id="5ed14-446">Add the **HolographicCameraRig\Prefabs\SpectatorViewManager** prefab to your scene and fill in the fields:</span></span>
   * <span data-ttu-id="5ed14-447">**HolographicCameraManager**应与 HolographicCameraManager 预设可从 HolographicCameraRig prefab 目录填充。</span><span class="sxs-lookup"><span data-stu-id="5ed14-447">**HolographicCameraManager** should be populated with the HolographicCameraManager prefab from the HolographicCameraRig prefab directory.</span></span>
   * <span data-ttu-id="5ed14-448">**定位点**应与定位点预设可从 HolographicCameraRig prefab 目录填充。</span><span class="sxs-lookup"><span data-stu-id="5ed14-448">**Anchor** should be populated with the Anchor prefab from the HolographicCameraRig prefab directory.</span></span>
   * <span data-ttu-id="5ed14-449">**共享**应与共享预设可从 MixedRealityToolkit 填充。</span><span class="sxs-lookup"><span data-stu-id="5ed14-449">**Sharing** should be populated with the Sharing prefab from the MixedRealityToolkit.</span></span>
   * <span data-ttu-id="5ed14-450">注意：如果任何这些预设已存在项目层次结构中，而不是这些客户都将使用现有预设。</span><span class="sxs-lookup"><span data-stu-id="5ed14-450">Note: If any of these prefabs already exist in your project hierarchy, the existing prefabs will be used instead of these ones.</span></span>
   * <span data-ttu-id="5ed14-451">**Spectator 视图 IP**应附加到你 spectator 视图远程测试机组你 HoloLens 的 IP。</span><span class="sxs-lookup"><span data-stu-id="5ed14-451">**Spectator View IP** should be the IP of your HoloLens attached to your spectator view rig.</span></span>
   * <span data-ttu-id="5ed14-452">**共享服务 IP**应运行 MixedRealityToolkit SharingService PC 的 IP。</span><span class="sxs-lookup"><span data-stu-id="5ed14-452">**Sharing Service IP** should be the IP of the PC running the MixedRealityToolkit SharingService.</span></span>
   * <span data-ttu-id="5ed14-453">可选：如果有多个 spectator 查看远程测试机组附加到多个 PC 的**本地计算机 IP**应与 spectator 视图远程测试机组将与其的 PC 设置。</span><span class="sxs-lookup"><span data-stu-id="5ed14-453">Optional: If you have multiple spectator view rigs attached to multiple PC's, **Local Computer IP** should be set with the PC the spectator view rig will communicate with.</span></span>

![在 Unity 中 spectator 视图管理器属性](images/spectatorviewmanager-500px.png)

* <span data-ttu-id="5ed14-455">启动 MixedRealityToolkit**共享服务**</span><span class="sxs-lookup"><span data-stu-id="5ed14-455">Start the MixedRealityToolkit **Sharing Service**</span></span>
* <span data-ttu-id="5ed14-456">生成和部署应用程序，如到 HoloLens D3D UWP 附加到 spectator 视图远程测试机组。</span><span class="sxs-lookup"><span data-stu-id="5ed14-456">Build and deploy the app as a D3D UWP to the HoloLens attached to the spectator view rig.</span></span>
* <span data-ttu-id="5ed14-457">将应用部署到体验中的任何其他 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="5ed14-457">Deploy the app to any other HoloLens devices in the experience.</span></span>
* <span data-ttu-id="5ed14-458">检查**运行在后台**下的复选框**编辑/项目设置/播放机**。</span><span class="sxs-lookup"><span data-stu-id="5ed14-458">Check the **Run In Background** checkbox under **edit/project settings/player**.</span></span>

![在 Unity 中的背景设置中运行](images/run-in-bg-400px.png)
* <span data-ttu-id="5ed14-460">启动复合器窗口下的**Spectator 视图排序器**</span><span class="sxs-lookup"><span data-stu-id="5ed14-460">Launch the compositor window under **Spectator View/Compositor**</span></span>

![在 Unity 中 spectator 视图的复合器视图](images/compositor-500px.png)

* <span data-ttu-id="5ed14-462">此窗口可以：</span><span class="sxs-lookup"><span data-stu-id="5ed14-462">This window allows you to:</span></span>
   * <span data-ttu-id="5ed14-463">开始录制视频</span><span class="sxs-lookup"><span data-stu-id="5ed14-463">Start recording video</span></span>
   * <span data-ttu-id="5ed14-464">拍摄一张照片</span><span class="sxs-lookup"><span data-stu-id="5ed14-464">Take a picture</span></span>
   * <span data-ttu-id="5ed14-465">更改全息图不透明度</span><span class="sxs-lookup"><span data-stu-id="5ed14-465">Change hologram opacity</span></span>
   * <span data-ttu-id="5ed14-466">更改的帧偏移量 （它可调整颜色时间戳以的捕获卡滞后时间）</span><span class="sxs-lookup"><span data-stu-id="5ed14-466">Change the frame offset (which adjusts the color timestamp to account for capture card latency)</span></span>
   * <span data-ttu-id="5ed14-467">打开捕获保存到的目录</span><span class="sxs-lookup"><span data-stu-id="5ed14-467">Open the directory the captures are saved to</span></span>
   * <span data-ttu-id="5ed14-468">（如果在项目中存在 SpatialMappingManager） 请求 spectator 视图照相机中的空间映射数据</span><span class="sxs-lookup"><span data-stu-id="5ed14-468">Request spatial mapping data from the spectator view camera (if a SpatialMappingManager exists in your project)</span></span>
   * <span data-ttu-id="5ed14-469">单独可视化场景的复合视图，以及颜色、 全息和 alpha 通道。</span><span class="sxs-lookup"><span data-stu-id="5ed14-469">Visualize the scene's composite view as well as color, holograms, and alpha channel individually.</span></span>
   * <span data-ttu-id="5ed14-470">打开您的照相机。</span><span class="sxs-lookup"><span data-stu-id="5ed14-470">Turn your camera on.</span></span>
   * <span data-ttu-id="5ed14-471">在 Unity 中按简单不过了。</span><span class="sxs-lookup"><span data-stu-id="5ed14-471">Press play in Unity.</span></span>
   * <span data-ttu-id="5ed14-472">照相机移动时，在 Unity 中的全息应身在何处在现实生活中相对于源您相机的颜色。</span><span class="sxs-lookup"><span data-stu-id="5ed14-472">When the camera is moved, holograms in Unity should be where they are in the real world relative to your camera color feed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ed14-473">请参阅</span><span class="sxs-lookup"><span data-stu-id="5ed14-473">See also</span></span>

* [<span data-ttu-id="5ed14-474">混合的现实捕获</span><span class="sxs-lookup"><span data-stu-id="5ed14-474">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="5ed14-475">面向开发人员混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="5ed14-475">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="5ed14-476">混合现实中的共享体验</span><span class="sxs-lookup"><span data-stu-id="5ed14-476">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* [<span data-ttu-id="5ed14-477">GitHub 上的 spectator 视图 （预览） 代码</span><span class="sxs-lookup"><span data-stu-id="5ed14-477">Spectator View (Preview) code on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/SpectatorView)
* [<span data-ttu-id="5ed14-478">Spectator 视图 （预览版） 在 GitHub 上的本机代码</span><span class="sxs-lookup"><span data-stu-id="5ed14-478">Spectator View (Preview) native code on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpectatorViewPlugin)
* [<span data-ttu-id="5ed14-479">GitHub 上 spectator Pro 视图代码</span><span class="sxs-lookup"><span data-stu-id="5ed14-479">Spectator View Pro code on GitHub</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView)
