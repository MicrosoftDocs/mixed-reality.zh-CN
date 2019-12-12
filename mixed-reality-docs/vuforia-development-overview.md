---
title: 将 Vuforia 与 Unity 一起使用
description: 利用 Vuforia 在 Unity 中构建 Windows Mixed Reality 应用程序。
author: thetuvix
ms.author: alexturn
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia，标记，坐标，引用框架，跟踪
ms.openlocfilehash: bae5d0eb04ab9434dd3e72674686743779a8f70c
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003186"
---
# <a name="using-vuforia-engine-with-unity"></a><span data-ttu-id="950b3-104">将 Vuforia 引擎与 Unity 一起使用</span><span class="sxs-lookup"><span data-stu-id="950b3-104">Using Vuforia Engine with Unity</span></span>

<span data-ttu-id="950b3-105">Vuforia 引擎为 HoloLens 提供一项重要功能–将 AR 体验连接到环境中的特定映像和对象的能力。</span><span class="sxs-lookup"><span data-stu-id="950b3-105">Vuforia Engine brings an important capability to HoloLens – the power to connect AR experiences to specific images and objects in the environment.</span></span> <span data-ttu-id="950b3-106">你可以使用此功能来覆盖工业企业的机械上的引导式分步说明，或者向物理产品或游戏添加数字功能和体验。</span><span class="sxs-lookup"><span data-stu-id="950b3-106">You can use this capability to overlay guided step-by-step instructions on top of machinery for the industrial enterprise or add digital features and experiences to a physical product or game.</span></span>

<span data-ttu-id="950b3-107">为了在开发 AR 体验时获得更大的灵活性，Vuforia 引擎提供了范围广泛的功能和目标。</span><span class="sxs-lookup"><span data-stu-id="950b3-107">For greater flexibility when developing AR experiences, Vuforia Engine offers a broad range of features and targets.</span></span> <span data-ttu-id="950b3-108">我们最新的功能 Vuforia 模型目标之一是用于商业和工业用途的一项重要功能。</span><span class="sxs-lookup"><span data-stu-id="950b3-108">One of our newest features, Vuforia Model Targets, is a key capability for both commercial and industrial uses.</span></span> <span data-ttu-id="950b3-109">模型目标允许应用程序识别诸如计算机、汽车或玩具等物理对象，并根据 CAD 或数字3D 模型对其进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="950b3-109">Model Targets allow applications to recognize physical objects like machines, automobiles or toys and track them based on a CAD or digital 3D model.</span></span> <span data-ttu-id="950b3-110">对于工业用途，此功能可以为程序集工作者和服务技术人员提供 AR 工作说明和过程指南，同时在现场或现场推出。</span><span class="sxs-lookup"><span data-stu-id="950b3-110">For industrial uses, this feature can provide assembly workers and service technicians with AR work instructions and procedural guidance while in the factory or out in the field.</span></span>

<span data-ttu-id="950b3-111">在 Unity 中，可以轻松地在 Unity 中配置为手机和平板电脑构建的现有 Vuforia 引擎应用。</span><span class="sxs-lookup"><span data-stu-id="950b3-111">Existing Vuforia Engine apps that were built for phones and tablets can easily be configured in Unity to run on HoloLens.</span></span> <span data-ttu-id="950b3-112">甚至可以使用 Vuforia 引擎将新的 HoloLens 应用程序带到 Windows 10 平板电脑，如 Surface Pro 和 Surface Book。</span><span class="sxs-lookup"><span data-stu-id="950b3-112">You can even use Vuforia Engine to take your new HoloLens app to Windows 10 tablets such as the Surface Pro and Surface Book.</span></span>


## <a name="get-the-tools"></a><span data-ttu-id="950b3-113">获取工具</span><span class="sxs-lookup"><span data-stu-id="950b3-113">Get the tools</span></span>

<span data-ttu-id="950b3-114">安装 Visual Studio 和 Unity[的推荐版本](install-the-tools.md)，然后将 Unity 配置为使用 Visual studio 和首选 IDE 和编译器。</span><span class="sxs-lookup"><span data-stu-id="950b3-114">[Install the recommended versions](install-the-tools.md) of Visual Studio and Unity and then configure Unity to use Visual Studio and the preferred IDE and compiler.</span></span> 

<span data-ttu-id="950b3-115">安装 Unity 时，请确保安装 "Windows 应用商店 IL2CPP 脚本后端"。</span><span class="sxs-lookup"><span data-stu-id="950b3-115">When installing Unity, be sure to install the “Windows Store IL2CPP Scripting Backend”.</span></span>

<span data-ttu-id="950b3-116">添加 Vuforia 引擎支持的工作方式有所不同，具体取决于你的 Unity 版本：</span><span class="sxs-lookup"><span data-stu-id="950b3-116">Adding  Vuforia Engine Support works differently depending on your version of Unity:</span></span>
*   <span data-ttu-id="950b3-117">Unity 2018.4：从 Vuforia 开发人员门户下载适用于 Unity 2018.4 的 Vuforia 引擎安装程序</span><span class="sxs-lookup"><span data-stu-id="950b3-117">Unity 2018.4: Download the Vuforia Engine installer for Unity 2018.4 from the Vuforia developer portal</span></span>
*   <span data-ttu-id="950b3-118">Unity 2019.2：获取最新的[Vuforia 引擎包](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)</span><span class="sxs-lookup"><span data-stu-id="950b3-118">Unity 2019.2: Get the latest [Vuforia Engine package](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html)</span></span> 

## <a name="getting-started-with-vuforia-engine"></a><span data-ttu-id="950b3-119">Vuforia 引擎入门</span><span class="sxs-lookup"><span data-stu-id="950b3-119">Getting started with Vuforia Engine</span></span>

<span data-ttu-id="950b3-120">了解将 Vuforia Engine 与 HoloLens 配合使用的最佳起点是使用[Vuforia 引擎 HoloLens 示例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)（可在 Unity 资产存储库中找到）。</span><span class="sxs-lookup"><span data-stu-id="950b3-120">The best starting point for learning about using Vuforia Engine with HoloLens is with the [Vuforia Engine HoloLens sample](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (available in the Unity Asset Store).</span></span> <span data-ttu-id="950b3-121">该示例提供了一个完整的 HoloLens 项目，其中包括可以部署到 HoloLens 的预配置的场景。</span><span class="sxs-lookup"><span data-stu-id="950b3-121">The sample provides a complete HoloLens project including pre-configured scenes that can be deployed to a HoloLens.</span></span>

<span data-ttu-id="950b3-122">幕后介绍了如何使用 Vuforia 图像目标识别映像，并在 HoloLens 体验中使用数字内容对其进行扩充。</span><span class="sxs-lookup"><span data-stu-id="950b3-122">The scenes show how to use Vuforia Image Targets to recognize an image and augment it with digital content in a HoloLens experience.</span></span> <span data-ttu-id="950b3-123">Vuforia 引擎 Hololens 示例还包含一个场景，其中显示了在 HoloLens 上使用模型目标和 VuMarks 的情况。</span><span class="sxs-lookup"><span data-stu-id="950b3-123">The Vuforia Engine Hololens Sample also includes a scene showing the usage of Model Targets and VuMarks on HoloLens.</span></span> <span data-ttu-id="950b3-124">你可以轻松地在幕后替换你自己的内容，以尝试创建使用 Vuforia 引擎的 HoloLens 应用。</span><span class="sxs-lookup"><span data-stu-id="950b3-124">You can easily substitute your own content in the scenes to experiment with the creation of HoloLens apps that use Vuforia Engine.</span></span>



## <a name="configuring-a-vuforia-app-for-hololens"></a><span data-ttu-id="950b3-125">为 HoloLens 配置 Vuforia 应用</span><span class="sxs-lookup"><span data-stu-id="950b3-125">Configuring a Vuforia App for HoloLens</span></span>

<span data-ttu-id="950b3-126">开发适用于 HoloLens 的 Vuforia 引擎应用与为其他设备开发 Vuforia 引擎应用基本相同。</span><span class="sxs-lookup"><span data-stu-id="950b3-126">Developing a Vuforia Engine app for HoloLens is fundamentally the same as developing Vuforia Engine apps for other devices.</span></span> <span data-ttu-id="950b3-127">然后，你可以应用以下部分中所述的生成设置和配置。</span><span class="sxs-lookup"><span data-stu-id="950b3-127">You can then apply the build settings and configurations described in the section below.</span></span> <span data-ttu-id="950b3-128">这就是使 Vuforia 引擎能够使用 HoloLens 空间映射和位置跟踪系统所需的全部操作。</span><span class="sxs-lookup"><span data-stu-id="950b3-128">That’s all that’s needed to enable Vuforia Engine to work with the HoloLens spatial mapping and positional tracking systems.</span></span>

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a><span data-ttu-id="950b3-129">生成和运行 HoloLens 的 Vuforia 引擎示例</span><span class="sxs-lookup"><span data-stu-id="950b3-129">Build and Run the Vuforia Engine Sample for HoloLens</span></span>
1.  <span data-ttu-id="950b3-130">从 Unity 资产存储区下载[适用于 HoloLens 的 Vuforia 引擎示例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)</span><span class="sxs-lookup"><span data-stu-id="950b3-130">Download the [Vuforia Engine Sample for HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) from the Unity Asset Store</span></span>
2.  <span data-ttu-id="950b3-131">[为电源和性能应用建议的 Unity 引擎选项](performance-recommendations-for-unity.md)</span><span class="sxs-lookup"><span data-stu-id="950b3-131">Apply the [recommended Unity engine options for power and performance](performance-recommendations-for-unity.md)</span></span>
3.  <span data-ttu-id="950b3-132">在生成中将示例场景添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="950b3-132">Add the sample scenes to Scenes in Build.</span></span>
4.  <span data-ttu-id="950b3-133">在文件 > 生成设置 "中设置" 通用 Windows 平台 "的平台生成目标。</span><span class="sxs-lookup"><span data-stu-id="950b3-133">Set your platform build target for “Universal Windows Platform” in File > Build Settings.</span></span>
5.  <span data-ttu-id="950b3-134">选择以下平台生成配置设置：</span><span class="sxs-lookup"><span data-stu-id="950b3-134">Select the following platform build configuration settings:</span></span> 
   * <span data-ttu-id="950b3-135">目标设备 = HoloLens</span><span class="sxs-lookup"><span data-stu-id="950b3-135">Target Device = HoloLens</span></span>
   * <span data-ttu-id="950b3-136">生成类型 = D3D</span><span class="sxs-lookup"><span data-stu-id="950b3-136">Build Type = D3D</span></span>
   * <span data-ttu-id="950b3-137">SDK = 最新安装</span><span class="sxs-lookup"><span data-stu-id="950b3-137">SDK = Latest Installed</span></span>
   * <span data-ttu-id="950b3-138">Visual Studio 版本 = 最新安装</span><span class="sxs-lookup"><span data-stu-id="950b3-138">Visual Studio Version = Latest Installed</span></span>
   * <span data-ttu-id="950b3-139">生成并运行于 = 本地计算机</span><span class="sxs-lookup"><span data-stu-id="950b3-139">Build and Run on = Local Machine</span></span>
6.  <span data-ttu-id="950b3-140">在**播放机设置**中定义唯一**产品名称**，以在安装在 HoloLens 上时充当应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="950b3-140">Define a unique **Product Name**, in **Player Settings**, to serve as the name of the app when installed on the HoloLens.</span></span>
7.  <span data-ttu-id="950b3-141">在**播放机设置 > XR 设置**中检查**Vuforia 扩充的现实**和**虚拟现实**</span><span class="sxs-lookup"><span data-stu-id="950b3-141">Check **Vuforia Augmented Reality** and **Virtual Reality Supported** in **Player Settings > XR Settings**</span></span>
8.  <span data-ttu-id="950b3-142">同时，在**XR 设置**下，确保已将 "Windows Mixed Reality" 添加到**虚拟现实 sdk**列表中</span><span class="sxs-lookup"><span data-stu-id="950b3-142">Also under **XR Settings**, make sure that “Windows Mixed Reality” is added to the **Virtual Reality SDKs** List</span></span>
9.  <span data-ttu-id="950b3-143">检查播放机设置中的以下功能 > 发布设置</span><span class="sxs-lookup"><span data-stu-id="950b3-143">Check the following Capabilities in Player Settings > Publish Settings</span></span> 
   * <span data-ttu-id="950b3-144">InternetClient</span><span class="sxs-lookup"><span data-stu-id="950b3-144">InternetClient</span></span>
   * <span data-ttu-id="950b3-145">网络摄像头</span><span class="sxs-lookup"><span data-stu-id="950b3-145">WebCam</span></span>
   * <span data-ttu-id="950b3-146">SpatialPerception-如果你打算使用 Surface 观察器 API</span><span class="sxs-lookup"><span data-stu-id="950b3-146">SpatialPerception - if you intend to use the Surface Observer API</span></span>
10. <span data-ttu-id="950b3-147">选择 "生成" 以生成 Visual Studio 项目</span><span class="sxs-lookup"><span data-stu-id="950b3-147">Select Build to generate a Visual Studio project</span></span>
11. <span data-ttu-id="950b3-148">从 Visual Studio 生成可执行文件并将其安装在 HoloLens 上</span><span class="sxs-lookup"><span data-stu-id="950b3-148">Build the executable from Visual Studio and install it on your HoloLens</span></span>

<span data-ttu-id="950b3-149">注意：从版本7.2 开始，HoloLens 的 Vuforia 引擎示例包含一个示例场景，其中包括模型目标的示例用法</span><span class="sxs-lookup"><span data-stu-id="950b3-149">Note: Starting with version 7.2, the Vuforia Engine Sample for HoloLens includes a sample scene including example usage of Model Targets</span></span>

## <a name="the-vuforia-developer-portal"></a><span data-ttu-id="950b3-150">Vuforia 开发人员门户</span><span class="sxs-lookup"><span data-stu-id="950b3-150">The Vuforia Developer Portal</span></span>

<span data-ttu-id="950b3-151">希望用 Vuforia 引擎和 HoloLens 创建自己的 AR 体验的开发人员应在[developer.vuforia.com](https://developer.vuforia.com/)的 Vuforia 开发人员门户注册。</span><span class="sxs-lookup"><span data-stu-id="950b3-151">Developers looking to create their own AR experiences with Vuforia Engine and HoloLens should sign up on our Vuforia Developer Portal at [developer.vuforia.com](https://developer.vuforia.com/).</span></span> <span data-ttu-id="950b3-152">在门户中，开发人员有权访问[Vuforia 引擎论坛](https://developer.vuforia.com/forum)，他们可以在其中加入社区讨论、包含有关所有 Vuforia 引擎功能的深入文档的[库](https://library.vuforia.com/)以及[Vuforia 目标管理器](https://developer.vuforia.com/target-manager)，用户可以在其中创建自己的自定义目标。</span><span class="sxs-lookup"><span data-stu-id="950b3-152">In the portal, developers have access to the [Vuforia Engine Forums](https://developer.vuforia.com/forum) where they can join community discussions, a [library](https://library.vuforia.com/) with in-depth documentation on all the Vuforia Engine Features, and the [Vuforia Target Manager](https://developer.vuforia.com/target-manager) where users can create their own custom Targets.</span></span> <span data-ttu-id="950b3-153">开发人员还可以使用[Vuforia 许可证管理器](https://developer.vuforia.com/license-manager)注册免费的开发人员许可证。</span><span class="sxs-lookup"><span data-stu-id="950b3-153">Developers can also sign up for a free Developer License using the [Vuforia License Manager](https://developer.vuforia.com/license-manager).</span></span>

## <a name="extended-tracking-with-vuforia"></a><span data-ttu-id="950b3-154">Vuforia 扩展跟踪</span><span class="sxs-lookup"><span data-stu-id="950b3-154">Extended tracking with Vuforia</span></span>

<span data-ttu-id="950b3-155">即使目标不再处于视图中，[扩展跟踪](https://library.vuforia.com/articles/Training/Extended-Tracking)仍保持跟踪。</span><span class="sxs-lookup"><span data-stu-id="950b3-155">[Extended tracking](https://library.vuforia.com/articles/Training/Extended-Tracking) maintains tracking even when a target is no longer in view.</span></span> <span data-ttu-id="950b3-156">启用位置设备跟踪器后，会自动为所有目标启用此功能。</span><span class="sxs-lookup"><span data-stu-id="950b3-156">It is automatically enabled for all targets when the Positional Device Tracker is enabled.</span></span> <span data-ttu-id="950b3-157">对于 HoloLens 应用程序，位置设备跟踪器会在 Unity 中自动启动。</span><span class="sxs-lookup"><span data-stu-id="950b3-157">For HoloLens applications, the Positional Device Tracker is started automatically in Unity.</span></span>

<span data-ttu-id="950b3-158">Vuforia 引擎自动融合来自相机跟踪和 HoloLens 空间跟踪的姿势，以提供稳定的目标，而不考虑是否由照相机来查看目标。</span><span class="sxs-lookup"><span data-stu-id="950b3-158">Vuforia Engine automatically fuses the poses from camera tracking and HoloLens's spatial tracking to provide stable target poses independent of whether the target is seen by the camera or not.</span></span>

<span data-ttu-id="950b3-159">由于过程是自动处理的，因此不需要开发人员进行任何编程。</span><span class="sxs-lookup"><span data-stu-id="950b3-159">Since the process is handled automatically, it does not require any programming by the developer.</span></span>


<span data-ttu-id="950b3-160">**下面是发生的情况 ...**</span><span class="sxs-lookup"><span data-stu-id="950b3-160">**Here is what occurs...**</span></span>
1. <span data-ttu-id="950b3-161">Vuforia 的目标跟踪器识别目标</span><span class="sxs-lookup"><span data-stu-id="950b3-161">Vuforia’s target Tracker recognizes the target</span></span>
2. <span data-ttu-id="950b3-162">然后初始化目标跟踪</span><span class="sxs-lookup"><span data-stu-id="950b3-162">Target tracking is then initialized</span></span>
3. <span data-ttu-id="950b3-163">分析目标的位置和旋转，为 HoloLens 提供可靠的姿势估计</span><span class="sxs-lookup"><span data-stu-id="950b3-163">The position and rotation of the target are analyzed to provide a robust pose estimate for HoloLens</span></span>
4. <span data-ttu-id="950b3-164">Vuforia 引擎将目标的姿势转换为 HoloLens 空间映射坐标空间</span><span class="sxs-lookup"><span data-stu-id="950b3-164">Vuforia Engine transforms the target's pose into the HoloLens spatial mapping coordinate space</span></span>
5. <span data-ttu-id="950b3-165">如果目标不再处于视图中，则 HoloLens 会接管跟踪。</span><span class="sxs-lookup"><span data-stu-id="950b3-165">HoloLens takes over tracking if the target is no longer in view.</span></span> <span data-ttu-id="950b3-166">再次查看目标时，Vuforia 将继续准确地跟踪图像和对象。</span><span class="sxs-lookup"><span data-stu-id="950b3-166">Whenever you look again at the target, Vuforia will continue to track the images and objects accurately.</span></span>

<span data-ttu-id="950b3-167">检测到但不再在视图中的目标将报告为 EXTENDED_TRACKED。</span><span class="sxs-lookup"><span data-stu-id="950b3-167">Targets that are detected, but no longer in view, are reported as EXTENDED_TRACKED.</span></span> <span data-ttu-id="950b3-168">在这些情况下，用于所有目标的 DefaultTrackableEventHandler 脚本将继续呈现增加内容。</span><span class="sxs-lookup"><span data-stu-id="950b3-168">In these cases, the DefaultTrackableEventHandler script that is used on all targets continues to render augmentation content.</span></span> <span data-ttu-id="950b3-169">开发人员可以通过实现自定义的以可跟踪事件处理程序脚本来控制此行为。</span><span class="sxs-lookup"><span data-stu-id="950b3-169">The developer can control this behavior by implementing a custom trackable event handler script.</span></span>


## <a name="performance-mode-with-vuforia-engine"></a><span data-ttu-id="950b3-170">带有 Vuforia 引擎的性能模式</span><span class="sxs-lookup"><span data-stu-id="950b3-170">Performance Mode with Vuforia Engine</span></span> 

<span data-ttu-id="950b3-171">可以通过 Vuforia 引擎来管理 HoloLens 到区 AR 体验的性能，并减少 CPU 工作负荷。</span><span class="sxs-lookup"><span data-stu-id="950b3-171">It is possible through the Vuforia Engine to manage the performance on the HoloLens to extent AR experiences and reduce the workload on the CPU.</span></span> <span data-ttu-id="950b3-172">Vuforia 引擎提供了三种可供选择的模式：默认值、优化速度和优化质量。</span><span class="sxs-lookup"><span data-stu-id="950b3-172">The Vuforia Engine offers three modes that can be selected: default, for optimizing speed, and for optimizing quality.</span></span> 

*   <span data-ttu-id="950b3-173">MODE_OPTIMIZE_SPEED 使你可以最大程度地减少 HoloLens 设备上的工作负荷，并且非常适合用于扩展 AR 体验。</span><span class="sxs-lookup"><span data-stu-id="950b3-173">MODE_OPTIMIZE_SPEED lets you minimize the workload on the HoloLens device and is great for extending AR experiences.</span></span> <span data-ttu-id="950b3-174">建议在应用跟踪静态对象/目标的情况下使用。</span><span class="sxs-lookup"><span data-stu-id="950b3-174">It is recommended for situations where the app is tracking static objects/targets.</span></span>
*   <span data-ttu-id="950b3-175">MODE_DEFAULT 是正常模式，可在大多数情况下使用。</span><span class="sxs-lookup"><span data-stu-id="950b3-175">MODE_DEFAULT is the normal mode which can be used in most scenarios.</span></span>
*   <span data-ttu-id="950b3-176">MODE_OPTIMIZE_QUALITY 更适合跟踪预期选取的可移动目标或模型目标。</span><span class="sxs-lookup"><span data-stu-id="950b3-176">MODE_OPTIMIZE_QUALITY is better for tracking movable targets or model targets you expect to be picked up.</span></span>

<span data-ttu-id="950b3-177">**设置模式**</span><span class="sxs-lookup"><span data-stu-id="950b3-177">**Setting the mode**</span></span>

<span data-ttu-id="950b3-178">若要在 Unity 中更改性能模式，请导航到位于 ARCamera GameObject 中作为组件的 Vuforia 配置（Ctrl + Shift + V/Cmd + Shift + V）。</span><span class="sxs-lookup"><span data-stu-id="950b3-178">To change the performance mode in Unity, navigate to Vuforia Configuration (Ctrl+Shift+V / Cmd+Shift+V) that is located as a component in the ARCamera GameObject.</span></span> 
*   <span data-ttu-id="950b3-179">选择 "相机设备模式" 下拉菜单，然后选择三个选项之一。</span><span class="sxs-lookup"><span data-stu-id="950b3-179">Select the dropdown menu for Camera Device Mode and select one of the three options.</span></span>


## <a name="see-also"></a><span data-ttu-id="950b3-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="950b3-180">See also</span></span>
* [<span data-ttu-id="950b3-181">安装工具</span><span class="sxs-lookup"><span data-stu-id="950b3-181">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="950b3-182">坐标系统</span><span class="sxs-lookup"><span data-stu-id="950b3-182">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="950b3-183">空间映射</span><span class="sxs-lookup"><span data-stu-id="950b3-183">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="950b3-184">Unity 中的相机</span><span class="sxs-lookup"><span data-stu-id="950b3-184">Camera in Unity</span></span>](camera-in-unity.md)
* [<span data-ttu-id="950b3-185">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="950b3-185">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="950b3-186">Vuforia 文档：针对 Unity 中的 Windows 10 进行开发</span><span class="sxs-lookup"><span data-stu-id="950b3-186">Vuforia documentation: Developing for Windows 10 in Unity</span></span>](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [<span data-ttu-id="950b3-187">Vuforia 文档：如何安装 Vuforia Unity 扩展</span><span class="sxs-lookup"><span data-stu-id="950b3-187">Vuforia documentation: How to install the Vuforia Unity extension</span></span>](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [<span data-ttu-id="950b3-188">Vuforia 文档：在 Unity 中使用 HoloLens 示例</span><span class="sxs-lookup"><span data-stu-id="950b3-188">Vuforia documentation: Working with the HoloLens sample in Unity</span></span>](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [<span data-ttu-id="950b3-189">Vuforia 文档： Vuforia 中的扩展跟踪</span><span class="sxs-lookup"><span data-stu-id="950b3-189">Vuforia documentation: Extended tracking in Vuforia</span></span>](https://library.vuforia.com/articles/Training/Extended-Tracking)
