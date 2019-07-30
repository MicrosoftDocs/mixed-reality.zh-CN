---
title: MR 空间 230-空间映射
description: 遵循以下编码演练, 使用 Unity、Visual Studio 和 HoloLens 来了解空间映射概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 学院, 教程, 空间映射, 表面重建, 网格
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993562"
---
>[!NOTE]
><span data-ttu-id="18436-104">混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="18436-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="18436-105">因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="18436-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="18436-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="18436-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="18436-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="18436-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="18436-108">将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="18436-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="18436-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="18436-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="18436-110">MR 空间 230:空间映射</span><span class="sxs-lookup"><span data-stu-id="18436-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="18436-111">[空间映射](spatial-mapping.md)将现实世界和虚拟世界结合在一起, 并讲授有关环境的影像。</span><span class="sxs-lookup"><span data-stu-id="18436-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="18436-112">在尊敬的空间 230 (项目 Planetarium) 中, 我们将学习如何:</span><span class="sxs-lookup"><span data-stu-id="18436-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="18436-113">扫描环境并将数据从 HoloLens 传输到你的开发计算机。</span><span class="sxs-lookup"><span data-stu-id="18436-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="18436-114">探索着色器并了解如何使用着色器来可视化空间。</span><span class="sxs-lookup"><span data-stu-id="18436-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="18436-115">使用网格处理将房间网格分解为简单的平面。</span><span class="sxs-lookup"><span data-stu-id="18436-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="18436-116">超越我们在[MR 基础知识 101](holograms-101.md)中学习的放置技术, 并提供有关在环境中放置全息影像的位置的反馈。</span><span class="sxs-lookup"><span data-stu-id="18436-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="18436-117">探索封闭效果, 因此, 当您的全息影像位于真实世界的对象后面时, 您仍然可以看到它具有 x 光愿景!</span><span class="sxs-lookup"><span data-stu-id="18436-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="18436-118">设备支持</span><span class="sxs-lookup"><span data-stu-id="18436-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="18436-119">摘要</span><span class="sxs-lookup"><span data-stu-id="18436-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="18436-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="18436-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="18436-121"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="18436-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="18436-122">MR 空间 230:空间映射</span><span class="sxs-lookup"><span data-stu-id="18436-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="18436-123">✔️</span><span class="sxs-lookup"><span data-stu-id="18436-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="18436-124">开始之前</span><span class="sxs-lookup"><span data-stu-id="18436-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="18436-125">系统必备</span><span class="sxs-lookup"><span data-stu-id="18436-125">Prerequisites</span></span>

* <span data-ttu-id="18436-126">配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="18436-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="18436-127">一些基本C#的编程能力。</span><span class="sxs-lookup"><span data-stu-id="18436-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="18436-128">应已完成[尊敬的基本知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="18436-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="18436-129">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="18436-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="18436-130">项目文件</span><span class="sxs-lookup"><span data-stu-id="18436-130">Project files</span></span>

* <span data-ttu-id="18436-131">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip)。</span><span class="sxs-lookup"><span data-stu-id="18436-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="18436-132"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="18436-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="18436-133">如果仍需要 Unity 5.6 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="18436-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="18436-134">如果仍需要 Unity 5.5 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="18436-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="18436-135">如果仍需要 Unity 5.4 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)。</span><span class="sxs-lookup"><span data-stu-id="18436-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="18436-136">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="18436-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="18436-137">如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)找到。</span><span class="sxs-lookup"><span data-stu-id="18436-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="18436-138">说明</span><span class="sxs-lookup"><span data-stu-id="18436-138">Notes</span></span>

* <span data-ttu-id="18436-139">Visual Studio 中的 "Enable 仅我的代码" 需要在 "工具" > 选项 "下禁用 (*未选中*) > 调试, 以便在代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="18436-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="18436-140">Unity 设置</span><span class="sxs-lookup"><span data-stu-id="18436-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="18436-141">启动**Unity**。</span><span class="sxs-lookup"><span data-stu-id="18436-141">Start **Unity**.</span></span>
* <span data-ttu-id="18436-142">选择 "**新建**" 以创建新项目。</span><span class="sxs-lookup"><span data-stu-id="18436-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="18436-143">将项目命名为**Planetarium**。</span><span class="sxs-lookup"><span data-stu-id="18436-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="18436-144">验证是否选择了**3d**设置。</span><span class="sxs-lookup"><span data-stu-id="18436-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="18436-145">单击“创建项目”。</span><span class="sxs-lookup"><span data-stu-id="18436-145">Click **Create Project**.</span></span>
* <span data-ttu-id="18436-146">Unity 启动后, 请参阅 "**编辑 > 项目设置" > Player**"。</span><span class="sxs-lookup"><span data-stu-id="18436-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="18436-147">在 "**检查器**" 面板中, 找到并选择绿色的**Windows 应用商店**图标。</span><span class="sxs-lookup"><span data-stu-id="18436-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="18436-148">展开 "**其他设置**"。</span><span class="sxs-lookup"><span data-stu-id="18436-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="18436-149">在 "**呈现**" 部分中, 查看 "**支持虚拟现实**" 选项。</span><span class="sxs-lookup"><span data-stu-id="18436-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="18436-150">验证**虚拟现实 sdk**列表中是否出现**Windows 全息**。</span><span class="sxs-lookup"><span data-stu-id="18436-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="18436-151">如果没有，请选择 **+** 按钮在列表的底部，然后选择**Windows Holographic**。</span><span class="sxs-lookup"><span data-stu-id="18436-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="18436-152">展开 "**发布设置**"。</span><span class="sxs-lookup"><span data-stu-id="18436-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="18436-153">在 "**功能**" 部分中, 检查以下设置:</span><span class="sxs-lookup"><span data-stu-id="18436-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="18436-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="18436-154">InternetClientServer</span></span>
    * <span data-ttu-id="18436-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="18436-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="18436-156">麦克风</span><span class="sxs-lookup"><span data-stu-id="18436-156">Microphone</span></span>
    * <span data-ttu-id="18436-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="18436-157">SpatialPerception</span></span>
* <span data-ttu-id="18436-158">开始**编辑 > 项目设置 > 质量**</span><span class="sxs-lookup"><span data-stu-id="18436-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="18436-159">在 "**检查器**" 面板中的 "Windows 应用商店" 图标下, 选择 "默认" 行下的黑色下拉箭头并将默认设置更改为 "**非常低**"。</span><span class="sxs-lookup"><span data-stu-id="18436-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="18436-160">请参阅**资产 > 导入包 > 自定义包**。</span><span class="sxs-lookup"><span data-stu-id="18436-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="18436-161">导航到 **..\holographicacademy-holograms-230-SpatialMapping\Starting**文件夹。</span><span class="sxs-lookup"><span data-stu-id="18436-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="18436-162">单击 " **Planetarium. unitypackage**"。</span><span class="sxs-lookup"><span data-stu-id="18436-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="18436-163">单击“打开” 。</span><span class="sxs-lookup"><span data-stu-id="18436-163">Click **Open**.</span></span>
* <span data-ttu-id="18436-164">随即出现 "**导入 Unity 包**" 窗口, 单击 "**导入**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="18436-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="18436-165">等待 Unity 导入完成此项目所需的所有资产。</span><span class="sxs-lookup"><span data-stu-id="18436-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="18436-166">在 "**层次结构**" 面板中, 删除**主摄像机**。</span><span class="sxs-lookup"><span data-stu-id="18436-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="18436-167">在 "**项目**" 面板中, 找到 " **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** " 文件夹, 查找 "**照相机**" 对象。</span><span class="sxs-lookup"><span data-stu-id="18436-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="18436-168">将**主相机**prefab 拖放到 "**层次结构**" 面板中。</span><span class="sxs-lookup"><span data-stu-id="18436-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="18436-169">在 "**层次结构**" 面板中, 删除**方向轻型**对象。</span><span class="sxs-lookup"><span data-stu-id="18436-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="18436-170">在 "**项目**" 面板的 "**全息影像**" 文件夹中, 找到**Cursor**对象。</span><span class="sxs-lookup"><span data-stu-id="18436-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="18436-171">拖动 & 将**游标**prefab 拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="18436-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="18436-172">在 "**层次结构**" 面板中, 选择**Cursor**对象。</span><span class="sxs-lookup"><span data-stu-id="18436-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="18436-173">在**检查器**面板中, 单击 "**层**" 下拉箭头, 然后选择 "**编辑层 ...** "。</span><span class="sxs-lookup"><span data-stu-id="18436-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="18436-174">将**用户层 31**命名为 "**SpatialMapping**"。</span><span class="sxs-lookup"><span data-stu-id="18436-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="18436-175">保存新场景:**文件 > 将场景另存为 ...**</span><span class="sxs-lookup"><span data-stu-id="18436-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="18436-176">单击 "**新建文件夹**", 然后将文件夹命名为 "**场景**"。</span><span class="sxs-lookup"><span data-stu-id="18436-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="18436-177">将该文件命名为 "**Planetarium**" 并将其保存在**幕后**文件夹中。</span><span class="sxs-lookup"><span data-stu-id="18436-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="18436-178">第1章-扫描</span><span class="sxs-lookup"><span data-stu-id="18436-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="18436-179">**目标**</span><span class="sxs-lookup"><span data-stu-id="18436-179">**Objectives**</span></span>
* <span data-ttu-id="18436-180">了解 SurfaceObserver 及其设置对体验和性能的影响。</span><span class="sxs-lookup"><span data-stu-id="18436-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="18436-181">创建房间扫描体验, 收集房间的网格。</span><span class="sxs-lookup"><span data-stu-id="18436-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="18436-182">**说明**</span><span class="sxs-lookup"><span data-stu-id="18436-182">**Instructions**</span></span>
* <span data-ttu-id="18436-183">在 "**项目**" 面板的**HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs**文件夹中, 找到**SpatialMapping** prefab。</span><span class="sxs-lookup"><span data-stu-id="18436-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="18436-184">拖动 & 将**SpatialMapping** prefab 拖到 "**层次结构**" 面板中。</span><span class="sxs-lookup"><span data-stu-id="18436-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="18436-185">**生成和部署 (第1部分)**</span><span class="sxs-lookup"><span data-stu-id="18436-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="18436-186">在 Unity 中, 选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="18436-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="18436-187">单击 "**添加打开的场景**", 将 " **Planetarium** " 场景添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="18436-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="18436-188">选择 "**平台**" 列表中的 "**通用 Windows 平台**", 然后单击 "**切换平台**"。</span><span class="sxs-lookup"><span data-stu-id="18436-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="18436-189">将**SDK**设置为**通用 10** , 将**UWP 版本**设置为**D3D**。</span><span class="sxs-lookup"><span data-stu-id="18436-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="18436-190">检查**Unity C#项目**。</span><span class="sxs-lookup"><span data-stu-id="18436-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="18436-191">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="18436-191">Click **Build**.</span></span>
* <span data-ttu-id="18436-192">创建名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="18436-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="18436-193">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="18436-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="18436-194">按 "**选择文件夹**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="18436-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="18436-195">当 Unity 完成生成后, 将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="18436-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="18436-196">双击**应用**文件夹以将其打开。</span><span class="sxs-lookup"><span data-stu-id="18436-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="18436-197">双击**Planetarium**以在 Visual Studio 中加载项目。</span><span class="sxs-lookup"><span data-stu-id="18436-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="18436-198">在 Visual Studio 中, 使用顶部工具栏将配置更改为 "**发布**"。</span><span class="sxs-lookup"><span data-stu-id="18436-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="18436-199">将平台更改为**x86**。</span><span class="sxs-lookup"><span data-stu-id="18436-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="18436-200">单击 "本地计算机" 右侧的下拉箭头, 然后选择 "**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="18436-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="18436-201">在 "地址" 字段中输入[设备的 IP 地址](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network), 并将身份验证模式更改为**通用 (未加密的协议)** 。</span><span class="sxs-lookup"><span data-stu-id="18436-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="18436-202">单击 "**调试-> 启动但不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="18436-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="18436-203">在 Visual Studio 中查看 "**输出**" 面板以了解 "生成和部署" 状态。</span><span class="sxs-lookup"><span data-stu-id="18436-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="18436-204">在应用程序部署完成后, 请四处浏览聊天室。</span><span class="sxs-lookup"><span data-stu-id="18436-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="18436-205">你将看到由黑色和白色线框网格覆盖的周围面。</span><span class="sxs-lookup"><span data-stu-id="18436-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="18436-206">扫描您的环境。</span><span class="sxs-lookup"><span data-stu-id="18436-206">Scan your surroundings.</span></span> <span data-ttu-id="18436-207">务必查看墙壁、上限和楼层。</span><span class="sxs-lookup"><span data-stu-id="18436-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="18436-208">**生成和部署 (第2部分)**</span><span class="sxs-lookup"><span data-stu-id="18436-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="18436-209">现在, 让我们了解空间映射如何影响性能。</span><span class="sxs-lookup"><span data-stu-id="18436-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="18436-210">在 Unity 中, 选择 " **Window > Profiler**"。</span><span class="sxs-lookup"><span data-stu-id="18436-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="18436-211">单击 "**添加探查器 > GPU**"。</span><span class="sxs-lookup"><span data-stu-id="18436-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="18436-212">单击 "**活动探查<Enter IP>器 >** 。</span><span class="sxs-lookup"><span data-stu-id="18436-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="18436-213">输入 HoloLens 的**IP 地址**。</span><span class="sxs-lookup"><span data-stu-id="18436-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="18436-214">单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="18436-214">Click **Connect**.</span></span>
* <span data-ttu-id="18436-215">观察 GPU 呈现帧所花的时间 (以毫秒为单位)。</span><span class="sxs-lookup"><span data-stu-id="18436-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="18436-216">阻止应用程序在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="18436-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="18436-217">返回到 Visual Studio 并打开**SpatialMappingObserver.cs**。</span><span class="sxs-lookup"><span data-stu-id="18436-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="18436-218">你会在 Assembly-CSharp (通用 Windows) 项目的 HoloToolkit\SpatialMapping 文件夹中找到它。</span><span class="sxs-lookup"><span data-stu-id="18436-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="18436-219">找到**唤醒 ()** 函数, 并添加以下代码行:**TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="18436-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="18436-220">将项目重新部署到你的设备, 然后**重新连接探查器**。</span><span class="sxs-lookup"><span data-stu-id="18436-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="18436-221">观察帧的呈现时间 (毫秒)。</span><span class="sxs-lookup"><span data-stu-id="18436-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="18436-222">阻止应用程序在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="18436-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="18436-223">**在 Unity 中保存和加载**</span><span class="sxs-lookup"><span data-stu-id="18436-223">**Save and load in Unity**</span></span>

<span data-ttu-id="18436-224">最后, 让我们保存房间网格, 并将其加载到 Unity。</span><span class="sxs-lookup"><span data-stu-id="18436-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="18436-225">返回到 Visual Studio 并删除在上一节中在**唤醒 ()** 函数中添加的**TrianglesPerCubicMeter**行。</span><span class="sxs-lookup"><span data-stu-id="18436-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="18436-226">将项目重新部署到你的设备。</span><span class="sxs-lookup"><span data-stu-id="18436-226">Redeploy the project to your device.</span></span> <span data-ttu-id="18436-227">现在, 我们应该运行每个立方米的**500**三角形。</span><span class="sxs-lookup"><span data-stu-id="18436-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="18436-228">打开浏览器并输入你的 HoloLens IPAddress 以导航到**Windows 设备门户**。</span><span class="sxs-lookup"><span data-stu-id="18436-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="18436-229">在左侧面板中选择 " **3D 视图**" 选项。</span><span class="sxs-lookup"><span data-stu-id="18436-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="18436-230">在 "**表面重建**" 下, 选择 "**更新**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="18436-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="18436-231">观看您在 HoloLens 上扫描的区域显示在 "显示" 窗口中。</span><span class="sxs-lookup"><span data-stu-id="18436-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="18436-232">若要保存房间扫描, 请按 "**保存**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="18436-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="18436-233">打开 "**下载**" 文件夹, 查找保存的会议室模型**SRMesh**。</span><span class="sxs-lookup"><span data-stu-id="18436-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="18436-234">将**SRMesh**复制到 Unity 项目的 "**资产**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="18436-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="18436-235">在 Unity 中, 在 "**层次结构**" 面板中选择 " **SpatialMapping** " 对象。</span><span class="sxs-lookup"><span data-stu-id="18436-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="18436-236">找到**对象图面观察器 (脚本)** 组件。</span><span class="sxs-lookup"><span data-stu-id="18436-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="18436-237">单击 "**房间模型**" 属性右侧的圆圈。</span><span class="sxs-lookup"><span data-stu-id="18436-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="18436-238">找到并选择 " **SRMesh** " 对象, 然后关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="18436-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="18436-239">验证**检查器**面板中的 "**房间模型**" 属性现在是否设置为 " **SRMesh**"。</span><span class="sxs-lookup"><span data-stu-id="18436-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="18436-240">按 "**播放**" 按钮进入 Unity 的预览模式。</span><span class="sxs-lookup"><span data-stu-id="18436-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="18436-241">SpatialMapping 组件将从保存的房间模型加载网格, 以便可以在 Unity 中使用它们。</span><span class="sxs-lookup"><span data-stu-id="18436-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="18436-242">切换到**场景**视图, 查看以线框着色器显示的所有房间模型。</span><span class="sxs-lookup"><span data-stu-id="18436-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="18436-243">再次按 "**播放**" 按钮以退出预览模式。</span><span class="sxs-lookup"><span data-stu-id="18436-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="18436-244">**注意：** 下次在 Unity 中进入预览模式时, 它会默认加载已保存的会议室网格。</span><span class="sxs-lookup"><span data-stu-id="18436-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="18436-245">第2章-可视化</span><span class="sxs-lookup"><span data-stu-id="18436-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="18436-246">**目标**</span><span class="sxs-lookup"><span data-stu-id="18436-246">**Objectives**</span></span>
* <span data-ttu-id="18436-247">了解着色器的基本知识。</span><span class="sxs-lookup"><span data-stu-id="18436-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="18436-248">可视化你的环境。</span><span class="sxs-lookup"><span data-stu-id="18436-248">Visualize your surroundings.</span></span>

<span data-ttu-id="18436-249">**说明**</span><span class="sxs-lookup"><span data-stu-id="18436-249">**Instructions**</span></span>
* <span data-ttu-id="18436-250">在 Unity 的 "**层次结构**" 面板中, 选择 " **SpatialMapping** " 对象。</span><span class="sxs-lookup"><span data-stu-id="18436-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="18436-251">在 "**检查器**" 面板中, 找到**空间映射管理器 (脚本)** 组件。</span><span class="sxs-lookup"><span data-stu-id="18436-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="18436-252">单击 "**表面材料**" 属性右侧的圆圈。</span><span class="sxs-lookup"><span data-stu-id="18436-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="18436-253">找到并选择**BlueLinesOnWalls**材料并关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="18436-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="18436-254">在 "**项目**面板**着色**器" 文件夹中, 双击**BlueLinesOnWalls**以在 Visual Studio 中打开着色器。</span><span class="sxs-lookup"><span data-stu-id="18436-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="18436-255">这是一个简单像素 (顶点到片段) 着色器, 用于完成以下任务:</span><span class="sxs-lookup"><span data-stu-id="18436-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="18436-256">将顶点的位置转换为世界空间。</span><span class="sxs-lookup"><span data-stu-id="18436-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="18436-257">检查顶点的法线, 确定像素是否为垂直。</span><span class="sxs-lookup"><span data-stu-id="18436-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="18436-258">设置要呈现的像素的颜色。</span><span class="sxs-lookup"><span data-stu-id="18436-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="18436-259">**生成和部署**</span><span class="sxs-lookup"><span data-stu-id="18436-259">**Build and Deploy**</span></span>
* <span data-ttu-id="18436-260">返回到 Unity, 按 "**播放**" 进入预览模式。</span><span class="sxs-lookup"><span data-stu-id="18436-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="18436-261">将在房间网格的所有垂直表面上呈现蓝线 (自动从已保存的扫描数据加载)。</span><span class="sxs-lookup"><span data-stu-id="18436-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="18436-262">切换到 "**场景**" 选项卡以调整房间的视图, 并查看整个房间网格在 Unity 中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="18436-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="18436-263">在 "**项目**" 面板中, 找到 "**材料**" 文件夹, 并选择**BlueLinesOnWalls**材料。</span><span class="sxs-lookup"><span data-stu-id="18436-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="18436-264">修改某些属性, 并查看更改在 Unity 编辑器中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="18436-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="18436-265">在 "**检查器**" 面板中, 调整**LineScale**值, 使线条显得更粗或更细。</span><span class="sxs-lookup"><span data-stu-id="18436-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="18436-266">在 "**检查器**" 面板中, 调整**LinesPerMeter**值以更改每个墙壁上显示的行数。</span><span class="sxs-lookup"><span data-stu-id="18436-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="18436-267">再次单击 "**播放**" 退出预览模式。</span><span class="sxs-lookup"><span data-stu-id="18436-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="18436-268">生成并部署到 HoloLens, 并观察着色器呈现在真实表面上的显示方式。</span><span class="sxs-lookup"><span data-stu-id="18436-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="18436-269">Unity 非常适合用于预览材料, 但在设备中签出渲染始终是一个好主意。</span><span class="sxs-lookup"><span data-stu-id="18436-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="18436-270">第3章-处理</span><span class="sxs-lookup"><span data-stu-id="18436-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="18436-271">**目标**</span><span class="sxs-lookup"><span data-stu-id="18436-271">**Objectives**</span></span>
* <span data-ttu-id="18436-272">了解用于处理空间映射数据以在应用程序中使用的方法。</span><span class="sxs-lookup"><span data-stu-id="18436-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="18436-273">分析空间映射数据以查找平面并删除三角形。</span><span class="sxs-lookup"><span data-stu-id="18436-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="18436-274">使用平面放置全息图。</span><span class="sxs-lookup"><span data-stu-id="18436-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="18436-275">**说明**</span><span class="sxs-lookup"><span data-stu-id="18436-275">**Instructions**</span></span>
* <span data-ttu-id="18436-276">在 Unity 的 "**项目**" 面板**中, 找到**" **SpatialProcessing** " 对象。</span><span class="sxs-lookup"><span data-stu-id="18436-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="18436-277">拖动 & 将**SpatialProcessing**对象放入**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="18436-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="18436-278">SpatialProcessing prefab 包含用于处理空间映射数据的组件。</span><span class="sxs-lookup"><span data-stu-id="18436-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="18436-279">**SurfaceMeshesToPlanes.cs**将根据空间映射数据查找并生成平面。</span><span class="sxs-lookup"><span data-stu-id="18436-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="18436-280">我们将在应用程序中使用平面来表示墙壁、地面和上限。</span><span class="sxs-lookup"><span data-stu-id="18436-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="18436-281">此 prefab 还包含**RemoveSurfaceVertices.cs** , 可从空间映射网格中删除顶点。</span><span class="sxs-lookup"><span data-stu-id="18436-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="18436-282">这可用于在网格中创建孔, 或删除不再需要的多余三角形 (因为可以改用平面)。</span><span class="sxs-lookup"><span data-stu-id="18436-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="18436-283">在 Unity 的 "**项目**" 面板**中, 找到**" **SpaceCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="18436-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="18436-284">将**SpaceCollection**对象拖放到**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="18436-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="18436-285">在 "**层次结构**" 面板中, 选择 " **SpatialProcessing** " 对象。</span><span class="sxs-lookup"><span data-stu-id="18436-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="18436-286">在 "**检查器**" 面板中, 找到 "**播放空间管理器 (脚本)** " 组件。</span><span class="sxs-lookup"><span data-stu-id="18436-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="18436-287">双击**PlaySpaceManager.cs** , 在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="18436-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="18436-288">PlaySpaceManager.cs 包含应用程序特定的代码。</span><span class="sxs-lookup"><span data-stu-id="18436-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="18436-289">我们将向此脚本添加功能, 以实现以下行为:</span><span class="sxs-lookup"><span data-stu-id="18436-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="18436-290">超过扫描时间限制后停止收集空间映射数据 (10 秒)。</span><span class="sxs-lookup"><span data-stu-id="18436-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="18436-291">处理空间映射数据:</span><span class="sxs-lookup"><span data-stu-id="18436-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="18436-292">使用 SurfaceMeshesToPlanes 将世界的更简单表示为平面 (墙壁、楼层、上限等)。</span><span class="sxs-lookup"><span data-stu-id="18436-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="18436-293">使用 RemoveSurfaceVertices 可删除位于平面边界内的曲面三角形。</span><span class="sxs-lookup"><span data-stu-id="18436-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="18436-294">在世界各地生成全息影像的集合, 并将其放在靠近用户的墙壁和地面平面上。</span><span class="sxs-lookup"><span data-stu-id="18436-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="18436-295">完成标记为在 PlaySpaceManager.cs 中的编码练习, 或将脚本替换为以下已完成的解决方案:</span><span class="sxs-lookup"><span data-stu-id="18436-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="18436-296">**生成和部署**</span><span class="sxs-lookup"><span data-stu-id="18436-296">**Build and Deploy**</span></span>
* <span data-ttu-id="18436-297">在部署到 HoloLens 之前, 请按 Unity 中的 "**播放**" 按钮进入播放模式。</span><span class="sxs-lookup"><span data-stu-id="18436-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="18436-298">从文件加载房间网格后, 请等待10秒, 然后再开始处理空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="18436-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="18436-299">处理完成后, 平面将显示为表示地面、墙壁、天花板等。</span><span class="sxs-lookup"><span data-stu-id="18436-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="18436-300">找到所有平面后, 应会看到一个阳历系统出现在摄像机附近的地面表上。</span><span class="sxs-lookup"><span data-stu-id="18436-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="18436-301">照相机附近的墙壁上还应显示两个海报。</span><span class="sxs-lookup"><span data-stu-id="18436-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="18436-302">切换到 "**场景**" 选项卡 (如果在**游戏**模式下看不到这些选项卡)。</span><span class="sxs-lookup"><span data-stu-id="18436-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="18436-303">再次按 "**播放**" 按钮以退出播放模式。</span><span class="sxs-lookup"><span data-stu-id="18436-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="18436-304">照常生成并部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="18436-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="18436-305">等待扫描和处理空间映射数据完成。</span><span class="sxs-lookup"><span data-stu-id="18436-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="18436-306">看到飞机后, 请尝试在世界各地查找太阳系和海报。</span><span class="sxs-lookup"><span data-stu-id="18436-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="18436-307">第4章-位置</span><span class="sxs-lookup"><span data-stu-id="18436-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="18436-308">**目标**</span><span class="sxs-lookup"><span data-stu-id="18436-308">**Objectives**</span></span>
* <span data-ttu-id="18436-309">确定是否可在表面上容纳全息图。</span><span class="sxs-lookup"><span data-stu-id="18436-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="18436-310">在图面上无法容纳时, 为用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="18436-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="18436-311">**说明**</span><span class="sxs-lookup"><span data-stu-id="18436-311">**Instructions**</span></span>
* <span data-ttu-id="18436-312">在 Unity 的 "**层次结构**" 面板中, 选择 " **SpatialProcessing** " 对象。</span><span class="sxs-lookup"><span data-stu-id="18436-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="18436-313">在 "**检查器**" 面板中, 找到 "**平面到平面 (脚本)** " 组件。</span><span class="sxs-lookup"><span data-stu-id="18436-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="18436-314">将 "**绘图平面**" 属性更改为 "**无**" 以清除选定内容。</span><span class="sxs-lookup"><span data-stu-id="18436-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="18436-315">将 "**绘图平面**" 属性更改为 "**墙壁**", 以便仅呈现墙壁平面。</span><span class="sxs-lookup"><span data-stu-id="18436-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="18436-316">在 "**项目**" 面板的 "**脚本**" 文件夹中, 双击**Placeable.cs**以在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="18436-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="18436-317">可**放置**脚本已附加到在完成平面查找之后创建的 "海报和投影" 框。</span><span class="sxs-lookup"><span data-stu-id="18436-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="18436-318">我们需要做的就是取消注释某些代码, 此脚本将实现以下内容:</span><span class="sxs-lookup"><span data-stu-id="18436-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="18436-319">通过 raycasting 从边界多维数据中心的中心和四个角来确定是否适合某个图面。</span><span class="sxs-lookup"><span data-stu-id="18436-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="18436-320">检查表面法线, 确定它是否平滑足以使全息影像能够坐在一起。</span><span class="sxs-lookup"><span data-stu-id="18436-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="18436-321">在子图的周围渲染边界立方体, 以在放置时显示其实际大小。</span><span class="sxs-lookup"><span data-stu-id="18436-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="18436-322">在全息图的下方/后面转换阴影, 以显示将其放在地面/墙壁上的位置。</span><span class="sxs-lookup"><span data-stu-id="18436-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="18436-323">如果无法在图面上放置全息影像, 则将阴影渲染为红色; 如果可能, 则显示绿色。</span><span class="sxs-lookup"><span data-stu-id="18436-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="18436-324">重新调整全息图的方向, 使之与它具有关联的表面类型 (垂直或水平) 对齐。</span><span class="sxs-lookup"><span data-stu-id="18436-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="18436-325">将全息图平滑放置在所选表面上, 以避免跳跃或对齐行为。</span><span class="sxs-lookup"><span data-stu-id="18436-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="18436-326">取消注释以下代码中的所有代码, 或在**Placeable.cs**中使用此完整解决方案:</span><span class="sxs-lookup"><span data-stu-id="18436-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="18436-327">**生成和部署**</span><span class="sxs-lookup"><span data-stu-id="18436-327">**Build and Deploy**</span></span>
* <span data-ttu-id="18436-328">与之前一样, 生成项目并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="18436-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="18436-329">等待扫描和处理空间映射数据完成。</span><span class="sxs-lookup"><span data-stu-id="18436-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="18436-330">看到阳历系统后, 请看下面的投影框, 然后执行选择手势来移动它。</span><span class="sxs-lookup"><span data-stu-id="18436-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="18436-331">选择 "投影" 框时, 将在投影框周围显示一个边界多维数据集。</span><span class="sxs-lookup"><span data-stu-id="18436-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="18436-332">将您转到房间中的不同位置。</span><span class="sxs-lookup"><span data-stu-id="18436-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="18436-333">应遵循您的注视。</span><span class="sxs-lookup"><span data-stu-id="18436-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="18436-334">当投影框下的阴影变为红色时, 您不能将全息图放置在该图面上。</span><span class="sxs-lookup"><span data-stu-id="18436-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="18436-335">当投影框下的阴影变为绿色时, 可以通过执行另一个选择手势来放置全息图。</span><span class="sxs-lookup"><span data-stu-id="18436-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="18436-336">在墙壁上查找并选择一个全息版海报, 以将其移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="18436-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="18436-337">请注意, 不能将海报放置在地面或天花板上, 并且在四处移动时, 它将一直面向每个墙。</span><span class="sxs-lookup"><span data-stu-id="18436-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="18436-338">第5章-封闭</span><span class="sxs-lookup"><span data-stu-id="18436-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="18436-339">**目标**</span><span class="sxs-lookup"><span data-stu-id="18436-339">**Objectives**</span></span>
* <span data-ttu-id="18436-340">确定空间映射网格是否封闭像素全息图。</span><span class="sxs-lookup"><span data-stu-id="18436-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="18436-341">运用不同的封闭技术来实现有趣的效果。</span><span class="sxs-lookup"><span data-stu-id="18436-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="18436-342">**说明**</span><span class="sxs-lookup"><span data-stu-id="18436-342">**Instructions**</span></span>

<span data-ttu-id="18436-343">首先, 我们将允许空间映射网格遮蔽其他影像, 而不 occluding 现实世界:</span><span class="sxs-lookup"><span data-stu-id="18436-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="18436-344">在 "**层次结构**" 面板中, 选择 " **SpatialProcessing** " 对象。</span><span class="sxs-lookup"><span data-stu-id="18436-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="18436-345">在 "**检查器**" 面板中, 找到 "**播放空间管理器 (脚本)** " 组件。</span><span class="sxs-lookup"><span data-stu-id="18436-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="18436-346">单击 "**次要材料**" 属性右侧的圆圈。</span><span class="sxs-lookup"><span data-stu-id="18436-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="18436-347">找到并选择**封闭**材料并关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="18436-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="18436-348">接下来, 我们将向地球添加特殊行为, 使其在另一个全息图 (例如 sun) 或空间映射网格封闭像素时具有蓝色突出显示:</span><span class="sxs-lookup"><span data-stu-id="18436-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="18436-349">在 "**项目**" 面板的 "**全息影像**" 文件夹中, 展开 " **SolarSystem** " 对象。</span><span class="sxs-lookup"><span data-stu-id="18436-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="18436-350">单击**地球**。</span><span class="sxs-lookup"><span data-stu-id="18436-350">Click on **Earth**.</span></span>
* <span data-ttu-id="18436-351">在 "**检查器**" 面板中, 找到地球材料 (底部组件)。</span><span class="sxs-lookup"><span data-stu-id="18436-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="18436-352">在 "**着色器" 下拉**> OcclusionRim 中, 将着色器更改为 "**自定义**"。</span><span class="sxs-lookup"><span data-stu-id="18436-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="18436-353">当另一对象封闭像素时, 这会在地球周围呈现蓝色突出显示。</span><span class="sxs-lookup"><span data-stu-id="18436-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="18436-354">最后, 我们将为太阳系中的行星启用 x 光视觉效果。</span><span class="sxs-lookup"><span data-stu-id="18436-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="18436-355">需要编辑**PlanetOcclusion.cs** (在 Scripts\SolarSystem 文件夹中找到) 以实现以下目的:</span><span class="sxs-lookup"><span data-stu-id="18436-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="18436-356">确定 SpatialMapping 层 (房间网格和平面) 是否封闭像素。</span><span class="sxs-lookup"><span data-stu-id="18436-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="18436-357">在 SpatialMapping 层封闭像素时显示行星的线框表示。</span><span class="sxs-lookup"><span data-stu-id="18436-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="18436-358">隐藏 SpatialMapping 层不阻止的行星的线框表示。</span><span class="sxs-lookup"><span data-stu-id="18436-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="18436-359">按照 PlanetOcclusion.cs 中的编码练习进行操作, 或使用以下解决方案:</span><span class="sxs-lookup"><span data-stu-id="18436-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="18436-360">**生成和部署**</span><span class="sxs-lookup"><span data-stu-id="18436-360">**Build and Deploy**</span></span>
* <span data-ttu-id="18436-361">照常构建应用程序并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="18436-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="18436-362">等待扫描和处理空间映射数据完成 (在墙壁上显示蓝色线)。</span><span class="sxs-lookup"><span data-stu-id="18436-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="18436-363">找到并选择 "阳历系统" 的投影框, 然后设置墙或计数器后的框。</span><span class="sxs-lookup"><span data-stu-id="18436-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="18436-364">您可以通过在 "海报" 或 "投影" 框中隐藏对等图面, 查看基本封闭。</span><span class="sxs-lookup"><span data-stu-id="18436-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="18436-365">寻找地球, 无论何时出现在另一个全息图或表面上, 都应有蓝色的突出显示效果。</span><span class="sxs-lookup"><span data-stu-id="18436-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="18436-366">观察行星在房间后移动, 或在房间中的其他表面上移动。</span><span class="sxs-lookup"><span data-stu-id="18436-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="18436-367">现在, 你有了 x 光愿景, 可以看到其线框骨架!</span><span class="sxs-lookup"><span data-stu-id="18436-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="18436-368">结束</span><span class="sxs-lookup"><span data-stu-id="18436-368">The End</span></span>

<span data-ttu-id="18436-369">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="18436-369">Congratulations!</span></span> <span data-ttu-id="18436-370">你现在已经完成**了 MR 空间 230:空间映射**。</span><span class="sxs-lookup"><span data-stu-id="18436-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="18436-371">你知道如何扫描环境并将空间映射数据加载到 Unity。</span><span class="sxs-lookup"><span data-stu-id="18436-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="18436-372">你了解着色器的基本知识, 以及如何使用材料来重新可视化世界。</span><span class="sxs-lookup"><span data-stu-id="18436-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="18436-373">了解了用于查找平面和从网格中删除三角形的新处理技术。</span><span class="sxs-lookup"><span data-stu-id="18436-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="18436-374">您可以在有意义的表面上移动和放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="18436-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="18436-375">您经历了不同的封闭技术, 伴随了 x 光愿景的强大功能!</span><span class="sxs-lookup"><span data-stu-id="18436-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
