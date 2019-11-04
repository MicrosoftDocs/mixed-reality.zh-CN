---
title: MR 输入 210-注视
description: 遵循以下编码演练，使用 Unity、Visual Studio 和 HoloLens 来了解注视概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，学院，教程，注视
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434690"
---
>[!NOTE]
><span data-ttu-id="91b08-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="91b08-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="91b08-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="91b08-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="91b08-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="91b08-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="91b08-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="91b08-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="91b08-108">为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="91b08-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="91b08-109">MR 输入210：注视</span><span class="sxs-lookup"><span data-stu-id="91b08-109">MR Input 210: Gaze</span></span>

<span data-ttu-id="91b08-110">"[注视](gaze-and-commit.md)" 是输入的第一种形式，它显示用户的意图和认知。</span><span class="sxs-lookup"><span data-stu-id="91b08-110">[Gaze](gaze-and-commit.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="91b08-111">MR Input 210 （也称为 "项目资源管理器"）是深入了解 Windows Mixed Reality 的与注视相关的概念。</span><span class="sxs-lookup"><span data-stu-id="91b08-111">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="91b08-112">我们会将上下文感知添加到游标和全息影像，充分利用你的应用程序对用户外观的了解。</span><span class="sxs-lookup"><span data-stu-id="91b08-112">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="91b08-113">这里有一个友好的 astronaut，可帮助你学习注视的概念。</span><span class="sxs-lookup"><span data-stu-id="91b08-113">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="91b08-114">在[尊敬的基本知识 101](holograms-101.md)中，我们有了一个简单的光标，只需跟随你的注视。</span><span class="sxs-lookup"><span data-stu-id="91b08-114">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="91b08-115">今天，我们要将一个步骤移到简单的游标之外：</span><span class="sxs-lookup"><span data-stu-id="91b08-115">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="91b08-116">我们要做的是光标，我们的全息影像看起来很清楚：这两项操作都将根据用户的查找位置或用户*不*在查找的位置而变化。</span><span class="sxs-lookup"><span data-stu-id="91b08-116">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="91b08-117">这使它们可以识别其上下文。</span><span class="sxs-lookup"><span data-stu-id="91b08-117">This makes them context-aware.</span></span>
* <span data-ttu-id="91b08-118">我们会将反馈添加到游标和全息影像，以便为用户提供更多的目标目标上下文。</span><span class="sxs-lookup"><span data-stu-id="91b08-118">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="91b08-119">这种反馈可以是音频和视觉对象。</span><span class="sxs-lookup"><span data-stu-id="91b08-119">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="91b08-120">我们将向你展示用于帮助用户达到更小目标的目标技术。</span><span class="sxs-lookup"><span data-stu-id="91b08-120">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="91b08-121">我们将向你展示如何使用定向指示器将用户的注意力吸引到你的全息影像。</span><span class="sxs-lookup"><span data-stu-id="91b08-121">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="91b08-122">我们将指导你在世界各地四处移动时，与用户一起使用全息影像。</span><span class="sxs-lookup"><span data-stu-id="91b08-122">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="91b08-123">以下各章中嵌入的视频使用较旧版本的 Unity 和混合现实工具包记录。</span><span class="sxs-lookup"><span data-stu-id="91b08-123">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="91b08-124">虽然分步说明准确且最新，但你可能会看到处于过期状态的相应视频中的脚本和视觉对象。</span><span class="sxs-lookup"><span data-stu-id="91b08-124">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="91b08-125">视频仍包含在 posterity 中，因为涵盖的概念仍适用。</span><span class="sxs-lookup"><span data-stu-id="91b08-125">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="91b08-126">设备支持</span><span class="sxs-lookup"><span data-stu-id="91b08-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="91b08-127">摘要</span><span class="sxs-lookup"><span data-stu-id="91b08-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="91b08-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="91b08-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="91b08-129"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="91b08-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="91b08-130">MR 输入210：注视</span><span class="sxs-lookup"><span data-stu-id="91b08-130">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="91b08-131">✔️</span><span class="sxs-lookup"><span data-stu-id="91b08-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="91b08-132">✔️</span><span class="sxs-lookup"><span data-stu-id="91b08-132">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="91b08-133">开始之前</span><span class="sxs-lookup"><span data-stu-id="91b08-133">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="91b08-134">必备条件</span><span class="sxs-lookup"><span data-stu-id="91b08-134">Prerequisites</span></span>

* <span data-ttu-id="91b08-135">配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="91b08-135">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="91b08-136">一些基本C#的编程能力。</span><span class="sxs-lookup"><span data-stu-id="91b08-136">Some basic C# programming ability.</span></span>
* <span data-ttu-id="91b08-137">应已完成[尊敬的基本知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="91b08-137">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="91b08-138">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="91b08-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="91b08-139">项目文件</span><span class="sxs-lookup"><span data-stu-id="91b08-139">Project files</span></span>

* <span data-ttu-id="91b08-140">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)。</span><span class="sxs-lookup"><span data-stu-id="91b08-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="91b08-141"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="91b08-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="91b08-142">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="91b08-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="91b08-143">如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)找到。</span><span class="sxs-lookup"><span data-stu-id="91b08-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="91b08-144">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="91b08-144">Errata and Notes</span></span>

* <span data-ttu-id="91b08-145">在 Visual Studio 中，需要在 "工具"-"> 选项-> 调试" 下禁用（取消选中） "仅我的代码"，以便在代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="91b08-145">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="91b08-146">第1章-Unity 设置</span><span class="sxs-lookup"><span data-stu-id="91b08-146">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="91b08-147">目标</span><span class="sxs-lookup"><span data-stu-id="91b08-147">Objectives</span></span>

* <span data-ttu-id="91b08-148">针对 Hololens 开发优化 Unity。</span><span class="sxs-lookup"><span data-stu-id="91b08-148">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="91b08-149">导入资产并设置场景。</span><span class="sxs-lookup"><span data-stu-id="91b08-149">Import assets and setup the scene.</span></span>
* <span data-ttu-id="91b08-150">查看 HoloLens 中的 astronaut。</span><span class="sxs-lookup"><span data-stu-id="91b08-150">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="91b08-151">说明</span><span class="sxs-lookup"><span data-stu-id="91b08-151">Instructions</span></span>

1. <span data-ttu-id="91b08-152">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="91b08-152">Start Unity.</span></span>
2. <span data-ttu-id="91b08-153">选择 "**新建项目**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-153">Select **New Project**.</span></span>
3. <span data-ttu-id="91b08-154">将项目命名为**ModelExplorer**。</span><span class="sxs-lookup"><span data-stu-id="91b08-154">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="91b08-155">输入 "位置" 作为先前未存档的 "**注视**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="91b08-155">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="91b08-156">请确保将项目设置为“3D”。</span><span class="sxs-lookup"><span data-stu-id="91b08-156">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="91b08-157">单击“创建项目”。</span><span class="sxs-lookup"><span data-stu-id="91b08-157">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="91b08-158">HoloLens 的 Unity 设置</span><span class="sxs-lookup"><span data-stu-id="91b08-158">Unity settings for HoloLens</span></span>

<span data-ttu-id="91b08-159">我们需要让 Unity 知道我们要导出的应用程序应创建[沉浸式视图](app-views.md)而不是2d 视图。</span><span class="sxs-lookup"><span data-stu-id="91b08-159">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="91b08-160">为此，我们添加了 HoloLens 作为虚拟现实设备。</span><span class="sxs-lookup"><span data-stu-id="91b08-160">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="91b08-161">请参阅 "**编辑 > 项目设置" > Player**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-161">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="91b08-162">在 "播放器设置" 的**检查器面板**中，选择 " **Windows 应用商店**" 图标。</span><span class="sxs-lookup"><span data-stu-id="91b08-162">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="91b08-163">展开 " **XR 设置**" 组。</span><span class="sxs-lookup"><span data-stu-id="91b08-163">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="91b08-164">在 "**呈现**" 部分中，选中 "**支持虚拟现实**" 复选框，以添加新的**虚拟现实 sdk**列表。</span><span class="sxs-lookup"><span data-stu-id="91b08-164">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="91b08-165">验证 " **Windows Mixed Reality** " 是否显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="91b08-165">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="91b08-166">如果没有，请选择列表底部的 " **+** " 按钮，然后选择 " **Windows 全息**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-166">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="91b08-167">接下来，我们需要将脚本后端设置为 .NET。</span><span class="sxs-lookup"><span data-stu-id="91b08-167">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="91b08-168">请参阅 "**编辑 > 项目设置" > Player** "（你可能仍然从上一步开始）。</span><span class="sxs-lookup"><span data-stu-id="91b08-168">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="91b08-169">在 "播放器设置" 的**检查器面板**中，选择 " **Windows 应用商店**" 图标。</span><span class="sxs-lookup"><span data-stu-id="91b08-169">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="91b08-170">在 "**其他设置**" "配置" 部分中，确保 "**脚本后端**" 设置为 " **.net** "</span><span class="sxs-lookup"><span data-stu-id="91b08-170">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="91b08-171">最后，我们将更新质量设置，以便在 HoloLens 上实现更快的性能。</span><span class="sxs-lookup"><span data-stu-id="91b08-171">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="91b08-172">请参阅**编辑 > 项目设置 > 质量**。</span><span class="sxs-lookup"><span data-stu-id="91b08-172">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="91b08-173">在 Windows 应用商店图标下，单击**默认**行中的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="91b08-173">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="91b08-174">对于**Windows 应用商店应用**，请选择 "**非常低**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-174">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="91b08-175">导入项目资产</span><span class="sxs-lookup"><span data-stu-id="91b08-175">Import project assets</span></span>

1. <span data-ttu-id="91b08-176">右键单击 "**项目**" 面板中的 "**资产**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="91b08-176">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="91b08-177">单击 "**导入包 > 自定义包**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-177">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="91b08-178">导航到下载的项目文件，然后单击 " **ModelExplorer. unitypackage**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-178">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="91b08-179">单击**打开**。</span><span class="sxs-lookup"><span data-stu-id="91b08-179">Click **Open**.</span></span>
5. <span data-ttu-id="91b08-180">加载包后，单击 "**导入**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="91b08-180">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="91b08-181">设置场景</span><span class="sxs-lookup"><span data-stu-id="91b08-181">Setup the scene</span></span>

1. <span data-ttu-id="91b08-182">在层次结构中，删除**主摄像机**。</span><span class="sxs-lookup"><span data-stu-id="91b08-182">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="91b08-183">在**HoloToolkit**文件夹中，打开 "**输入**" 文件夹，然后打开 " **prototyping** " 文件夹。</span><span class="sxs-lookup"><span data-stu-id="91b08-183">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="91b08-184">将**MixedRealityCameraParent** Prefab 从**prototyping**文件夹拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="91b08-184">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="91b08-185">右键单击层次结构中的**定向光**，然后选择 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-185">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="91b08-186">在**全息影像**文件夹中，将以下资产拖放到**层次结构**的根中：</span><span class="sxs-lookup"><span data-stu-id="91b08-186">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="91b08-187">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="91b08-187">**AstroMan**</span></span>
    * <span data-ttu-id="91b08-188">**灯**</span><span class="sxs-lookup"><span data-stu-id="91b08-188">**Lights**</span></span>
    * <span data-ttu-id="91b08-189">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="91b08-189">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="91b08-190">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="91b08-190">**SpaceBackground**</span></span>
6. <span data-ttu-id="91b08-191">启动**播放模式**▶查看 astronaut。</span><span class="sxs-lookup"><span data-stu-id="91b08-191">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="91b08-192">再次单击**播放模式**▶**停止**。</span><span class="sxs-lookup"><span data-stu-id="91b08-192">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="91b08-193">在**全息影像**文件夹中，找到**Fitbox**资产，并将其拖到**层次结构**的根。</span><span class="sxs-lookup"><span data-stu-id="91b08-193">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="91b08-194">在 "**层次结构**" 面板中选择 " **Fitbox** "。</span><span class="sxs-lookup"><span data-stu-id="91b08-194">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="91b08-195">在 "**检查器**" 面板中，将**AstroMan**集合从**层次结构**中拖到 Fitbox 的**全息图集合**属性中。</span><span class="sxs-lookup"><span data-stu-id="91b08-195">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="91b08-196">保存项目</span><span class="sxs-lookup"><span data-stu-id="91b08-196">Save the project</span></span>

1. <span data-ttu-id="91b08-197">保存新场景： **File > 将场景另存为**。</span><span class="sxs-lookup"><span data-stu-id="91b08-197">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="91b08-198">单击 "**新建文件夹**"，然后将文件夹命名为 "**场景**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-198">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="91b08-199">将该文件命名为 "**ModelExplorer**" 并将其保存在**幕后**文件夹中。</span><span class="sxs-lookup"><span data-stu-id="91b08-199">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="91b08-200">生成项目</span><span class="sxs-lookup"><span data-stu-id="91b08-200">Build the project</span></span>

1. <span data-ttu-id="91b08-201">在 Unity 中，选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-201">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="91b08-202">单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="91b08-202">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="91b08-203">选择 "**平台**" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-203">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="91b08-204">如果要专门针对 HoloLens 进行开发，请将 "**目标设备**" 设置为 " **hololens**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-204">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="91b08-205">否则，请将其留在**任何设备**上。</span><span class="sxs-lookup"><span data-stu-id="91b08-205">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="91b08-206">确保将 "**生成类型**" 设置为 " **D3D** "，并将 " **SDK** " 设置为 "**最新安装**的" （应为 SDK 16299 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="91b08-206">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="91b08-207">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="91b08-207">Click **Build**.</span></span>
7. <span data-ttu-id="91b08-208">创建名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="91b08-208">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="91b08-209">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="91b08-209">Single click the **App** folder.</span></span>
9. <span data-ttu-id="91b08-210">按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-210">Press **Select Folder**.</span></span>

<span data-ttu-id="91b08-211">当 Unity 完成后，将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="91b08-211">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="91b08-212">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="91b08-212">Open the **App** folder.</span></span>
2. <span data-ttu-id="91b08-213">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="91b08-213">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="91b08-214">如果部署到 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="91b08-214">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="91b08-215">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **x86**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-215">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="91b08-216">单击 "本地计算机" 按钮旁的下拉箭头，然后选择 "**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-216">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="91b08-217">输入**HoloLens 设备 IP 地址**，并将身份验证模式设置为**通用（未加密的协议）** 。</span><span class="sxs-lookup"><span data-stu-id="91b08-217">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="91b08-218">单击 "**选择**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-218">Click **Select**.</span></span> <span data-ttu-id="91b08-219">如果你不知道设备 IP 地址，请在 "设置" 中查找 " **> 网络 & Internet > 高级选项**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-219">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="91b08-220">在顶部菜单栏中，单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="91b08-220">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="91b08-221">如果这是首次部署到设备，则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="91b08-221">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="91b08-222">当应用程序已部署后，使用**选择手势**关闭**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="91b08-222">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="91b08-223">如果要部署到沉浸式耳机：</span><span class="sxs-lookup"><span data-stu-id="91b08-223">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="91b08-224">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **x64**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-224">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="91b08-225">确保将部署目标设置为 "**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-225">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="91b08-226">在顶部菜单栏中，单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="91b08-226">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="91b08-227">当应用程序已部署后，通过将触发器拖到运动控制器上来关闭**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="91b08-227">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="91b08-228">第2章-游标和目标反馈</span><span class="sxs-lookup"><span data-stu-id="91b08-228">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="91b08-229">目标</span><span class="sxs-lookup"><span data-stu-id="91b08-229">Objectives</span></span>

* <span data-ttu-id="91b08-230">游标视觉对象设计和行为。</span><span class="sxs-lookup"><span data-stu-id="91b08-230">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="91b08-231">基于注视的光标反馈。</span><span class="sxs-lookup"><span data-stu-id="91b08-231">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="91b08-232">基于注视的全息影像反馈。</span><span class="sxs-lookup"><span data-stu-id="91b08-232">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="91b08-233">我们将使用一些游标设计原则，即：</span><span class="sxs-lookup"><span data-stu-id="91b08-233">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="91b08-234">游标始终存在。</span><span class="sxs-lookup"><span data-stu-id="91b08-234">The cursor is always present.</span></span>
* <span data-ttu-id="91b08-235">不要让光标变得太小或太大。</span><span class="sxs-lookup"><span data-stu-id="91b08-235">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="91b08-236">避免阻碍内容。</span><span class="sxs-lookup"><span data-stu-id="91b08-236">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="91b08-237">说明</span><span class="sxs-lookup"><span data-stu-id="91b08-237">Instructions</span></span>

1. <span data-ttu-id="91b08-238">在**HoloToolkit\Input\Prefabs**文件夹中，找到 " **InputManager** " 资产。</span><span class="sxs-lookup"><span data-stu-id="91b08-238">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="91b08-239">将**InputManager**拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="91b08-239">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="91b08-240">在**HoloToolkit\Input\Prefabs**文件夹中，找到**光标**资产。</span><span class="sxs-lookup"><span data-stu-id="91b08-240">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="91b08-241">将**光标**拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="91b08-241">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="91b08-242">选择**层次结构**中的**InputManager**对象。</span><span class="sxs-lookup"><span data-stu-id="91b08-242">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="91b08-243">将**光标**对象从**层次结构**中拖放到**检查器**底部的 InputManager 的**SimpleSinglePointerSelector**的**游标**字段。</span><span class="sxs-lookup"><span data-stu-id="91b08-243">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![简单的单指针选择器设置](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="91b08-245">生成和部署</span><span class="sxs-lookup"><span data-stu-id="91b08-245">Build and Deploy</span></span>

1. <span data-ttu-id="91b08-246">从**文件 > 生成设置**重新生成应用。</span><span class="sxs-lookup"><span data-stu-id="91b08-246">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="91b08-247">打开**应用程序文件夹**。</span><span class="sxs-lookup"><span data-stu-id="91b08-247">Open the **App folder**.</span></span>
3. <span data-ttu-id="91b08-248">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="91b08-248">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="91b08-249">单击 "**调试-> 启动但不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="91b08-249">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="91b08-250">观察如何绘制光标，以及如何在触摸全息图时更改其外观。</span><span class="sxs-lookup"><span data-stu-id="91b08-250">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="91b08-251">说明</span><span class="sxs-lookup"><span data-stu-id="91b08-251">Instructions</span></span>

1. <span data-ttu-id="91b08-252">在 "**层次结构**" 面板中，展开 " **AstroMan**->**GEO_G**->**Back_Center** " 对象。</span><span class="sxs-lookup"><span data-stu-id="91b08-252">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="91b08-253">双击 " **Interactible.cs** " 在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="91b08-253">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="91b08-254">取消注释**Interactible.cs**中的**IFocusable OnFocusEnter （）** 和**IFocusable （）** 回调中的行。</span><span class="sxs-lookup"><span data-stu-id="91b08-254">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="91b08-255">当焦点（通过 "注视" 或 "通过控制器"）进入和退出特定 GameObject 的碰撞器时，它们由混合现实工具包的 InputManager 调用。</span><span class="sxs-lookup"><span data-stu-id="91b08-255">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="91b08-256">我们使用上面 `EnableKeyword` 和 `DisableKeyword`。</span><span class="sxs-lookup"><span data-stu-id="91b08-256">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="91b08-257">若要在自己的应用程序中使用工具包的标准着色器来使用这些应用程序，需要遵循[Unity 指导原则，通过脚本访问材料](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。</span><span class="sxs-lookup"><span data-stu-id="91b08-257">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="91b08-258">在这种情况下，我们已在 "资源" 文件夹中包含了所需的[突出显示材料的三个变体](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)（查找名称中突出显示的三个材料）。</span><span class="sxs-lookup"><span data-stu-id="91b08-258">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="91b08-259">生成和部署</span><span class="sxs-lookup"><span data-stu-id="91b08-259">Build and Deploy</span></span>

1. <span data-ttu-id="91b08-260">与之前一样，生成项目并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="91b08-260">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="91b08-261">观察注视的目标是对象时，发生的情况。</span><span class="sxs-lookup"><span data-stu-id="91b08-261">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="91b08-262">第3章-目标技术</span><span class="sxs-lookup"><span data-stu-id="91b08-262">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="91b08-263">目标</span><span class="sxs-lookup"><span data-stu-id="91b08-263">Objectives</span></span>

* <span data-ttu-id="91b08-264">更轻松地定位全息影像。</span><span class="sxs-lookup"><span data-stu-id="91b08-264">Make it easier to target holograms.</span></span>
* <span data-ttu-id="91b08-265">稳定的自然头运动。</span><span class="sxs-lookup"><span data-stu-id="91b08-265">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="91b08-266">说明</span><span class="sxs-lookup"><span data-stu-id="91b08-266">Instructions</span></span>

1. <span data-ttu-id="91b08-267">在 "**层次结构**" 面板中，选择 " **InputManager** " 对象。</span><span class="sxs-lookup"><span data-stu-id="91b08-267">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="91b08-268">在 "**检查器**" 面板中，找到 "**注视" 稳定**的脚本。</span><span class="sxs-lookup"><span data-stu-id="91b08-268">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="91b08-269">如果要查看，请单击它以在 Visual Studio 中打开。</span><span class="sxs-lookup"><span data-stu-id="91b08-269">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="91b08-270">此脚本将循环访问 Raycast 数据的示例，并帮助使用户看得更稳定，以实现精确定位。</span><span class="sxs-lookup"><span data-stu-id="91b08-270">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="91b08-271">在**检查器**中，可以编辑**存储的稳定性示例**值。</span><span class="sxs-lookup"><span data-stu-id="91b08-271">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="91b08-272">此值表示稳定程序为计算稳定值而迭代的样本数。</span><span class="sxs-lookup"><span data-stu-id="91b08-272">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="91b08-273">第4章-方向指示器</span><span class="sxs-lookup"><span data-stu-id="91b08-273">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="91b08-274">目标</span><span class="sxs-lookup"><span data-stu-id="91b08-274">Objectives</span></span>

* <span data-ttu-id="91b08-275">在光标处添加方向指示器以帮助查找全息影像。</span><span class="sxs-lookup"><span data-stu-id="91b08-275">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="91b08-276">说明</span><span class="sxs-lookup"><span data-stu-id="91b08-276">Instructions</span></span>

<span data-ttu-id="91b08-277">我们将使用**DirectionIndicator.cs**文件，该文件将：</span><span class="sxs-lookup"><span data-stu-id="91b08-277">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="91b08-278">如果用户不 gazing 在全息影像上，则显示方向指示器。</span><span class="sxs-lookup"><span data-stu-id="91b08-278">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="91b08-279">如果用户在全息影像上 gazing，则隐藏方向指示器。</span><span class="sxs-lookup"><span data-stu-id="91b08-279">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="91b08-280">更新方向指示器以指向全息影像。</span><span class="sxs-lookup"><span data-stu-id="91b08-280">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="91b08-281">让我们开始吧。</span><span class="sxs-lookup"><span data-stu-id="91b08-281">Let's get started.</span></span>

1. <span data-ttu-id="91b08-282">单击 "**层次结构**" 面板中的**AstroMan**对象，然后**单击箭头**将其展开。</span><span class="sxs-lookup"><span data-stu-id="91b08-282">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="91b08-283">在 "**层次结构**" 面板中，选择 " **AstroMan**" 下的**DirectionalIndicator**对象。</span><span class="sxs-lookup"><span data-stu-id="91b08-283">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="91b08-284">在**检查器**面板中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="91b08-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="91b08-285">在菜单中，键入 "搜索框**方向" 指示器**。</span><span class="sxs-lookup"><span data-stu-id="91b08-285">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="91b08-286">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="91b08-286">Select the search result.</span></span>
5. <span data-ttu-id="91b08-287">在 "**层次结构**" 面板中，将**cursor**对象拖放到**检查器**的**cursor**属性上。</span><span class="sxs-lookup"><span data-stu-id="91b08-287">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="91b08-288">在 "**项目**" 面板中，将 " **DirectionalIndicator** **" 资产**拖放到**检查器**的 "**方向指示器**" 属性中。</span><span class="sxs-lookup"><span data-stu-id="91b08-288">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="91b08-289">生成并部署应用。</span><span class="sxs-lookup"><span data-stu-id="91b08-289">Build and deploy the app.</span></span>
8. <span data-ttu-id="91b08-290">观看方向指示器对象如何帮助您找到 astronaut。</span><span class="sxs-lookup"><span data-stu-id="91b08-290">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="91b08-291">第5章-Billboarding</span><span class="sxs-lookup"><span data-stu-id="91b08-291">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="91b08-292">目标</span><span class="sxs-lookup"><span data-stu-id="91b08-292">Objectives</span></span>

* <span data-ttu-id="91b08-293">使用 billboarding，让全息影像始终面向你。</span><span class="sxs-lookup"><span data-stu-id="91b08-293">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="91b08-294">我们将使用**Billboard.cs**文件来保持 GameObject，使其始终面向用户。</span><span class="sxs-lookup"><span data-stu-id="91b08-294">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="91b08-295">在 "**层次结构**" 面板中，选择 " **AstroMan** " 对象。</span><span class="sxs-lookup"><span data-stu-id="91b08-295">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="91b08-296">在**检查器**面板中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="91b08-296">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="91b08-297">在菜单中，在 "搜索" 框中键入 "**布告栏**"。</span><span class="sxs-lookup"><span data-stu-id="91b08-297">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="91b08-298">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="91b08-298">Select the search result.</span></span>
4. <span data-ttu-id="91b08-299">在**检查器**中，将**透视轴**设置为**Y**。</span><span class="sxs-lookup"><span data-stu-id="91b08-299">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="91b08-300">试试看吧！</span><span class="sxs-lookup"><span data-stu-id="91b08-300">Try it!</span></span> <span data-ttu-id="91b08-301">像以前一样构建并部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="91b08-301">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="91b08-302">了解布告栏对象如何面对您如何更改视点。</span><span class="sxs-lookup"><span data-stu-id="91b08-302">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="91b08-303">立即从**AstroMan**中删除脚本。</span><span class="sxs-lookup"><span data-stu-id="91b08-303">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="91b08-304">第6章-标记-沿着</span><span class="sxs-lookup"><span data-stu-id="91b08-304">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="91b08-305">目标</span><span class="sxs-lookup"><span data-stu-id="91b08-305">Objectives</span></span>

* <span data-ttu-id="91b08-306">使用 "标记"，让我们的全息影像围绕空间。</span><span class="sxs-lookup"><span data-stu-id="91b08-306">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="91b08-307">当我们处理此问题时，我们将通过以下设计约束指导：</span><span class="sxs-lookup"><span data-stu-id="91b08-307">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="91b08-308">内容应始终一目了然。</span><span class="sxs-lookup"><span data-stu-id="91b08-308">Content should always be a glance away.</span></span>
* <span data-ttu-id="91b08-309">内容不应采用的方式。</span><span class="sxs-lookup"><span data-stu-id="91b08-309">Content should not be in the way.</span></span>
* <span data-ttu-id="91b08-310">打印头锁定内容不舒服。</span><span class="sxs-lookup"><span data-stu-id="91b08-310">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="91b08-311">此处使用的解决方案是使用 "标记式" 方法。</span><span class="sxs-lookup"><span data-stu-id="91b08-311">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="91b08-312">标记靠对象从不完全离开用户的视图。</span><span class="sxs-lookup"><span data-stu-id="91b08-312">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="91b08-313">可以将标记作为附加到用户 head 的对象（通过橡胶带）。</span><span class="sxs-lookup"><span data-stu-id="91b08-313">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="91b08-314">随着用户的移动，内容将一直滑入视图边缘，无需完全离开。</span><span class="sxs-lookup"><span data-stu-id="91b08-314">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="91b08-315">当用户 gazes 沿标记的对象时，它会更全面地进入视图。</span><span class="sxs-lookup"><span data-stu-id="91b08-315">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="91b08-316">我们将使用**SimpleTagalong.cs**文件，该文件将：</span><span class="sxs-lookup"><span data-stu-id="91b08-316">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="91b08-317">确定标记靠上的对象是否处于相机边界内。</span><span class="sxs-lookup"><span data-stu-id="91b08-317">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="91b08-318">如果视图不在视图中，则将标记一起放置在视图 "截锥" 中部分。</span><span class="sxs-lookup"><span data-stu-id="91b08-318">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="91b08-319">否则，将标记与用户的默认距离相同。</span><span class="sxs-lookup"><span data-stu-id="91b08-319">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="91b08-320">为此，我们必须先更改**Interactible.cs**脚本，以便调用**TagalongAction**。</span><span class="sxs-lookup"><span data-stu-id="91b08-320">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="91b08-321">完成代码编写练习6，编辑**Interactible.cs** 。 a （取消注释行84到87）。</span><span class="sxs-lookup"><span data-stu-id="91b08-321">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="91b08-322">当点击全息影像时，与**Interactible.cs**配对的**InteractibleAction.cs**脚本将执行自定义操作。</span><span class="sxs-lookup"><span data-stu-id="91b08-322">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="91b08-323">在这种情况下，我们将专门用于标记。</span><span class="sxs-lookup"><span data-stu-id="91b08-323">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="91b08-324">在 "**脚本**" 文件夹中，单击 " **TagalongAction.cs**资产" 以在 Visual Studio 中打开。</span><span class="sxs-lookup"><span data-stu-id="91b08-324">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="91b08-325">完成编码练习，或将其更改为：</span><span class="sxs-lookup"><span data-stu-id="91b08-325">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="91b08-326">在**层次结构**的顶部，在搜索栏中键入 " **ChestButton_Center** "，然后选择结果。</span><span class="sxs-lookup"><span data-stu-id="91b08-326">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="91b08-327">在**检查器**面板中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="91b08-327">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="91b08-328">在菜单中，在 "搜索" 框中键入 " **Tagalong" 操作**。</span><span class="sxs-lookup"><span data-stu-id="91b08-328">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="91b08-329">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="91b08-329">Select the search result.</span></span>
  * <span data-ttu-id="91b08-330">在**全息影像**文件夹中查找**Tagalong**资产。</span><span class="sxs-lookup"><span data-stu-id="91b08-330">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="91b08-331">选择**层次结构**中的**ChestButton_Center**对象。</span><span class="sxs-lookup"><span data-stu-id="91b08-331">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="91b08-332">将**TagAlong**对象从 "**项目**" 面板中拖放到 **"** **要 TagAlong 的对象**" 属性中。</span><span class="sxs-lookup"><span data-stu-id="91b08-332">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="91b08-333">将**Tagalong 操作**对象从**检查器**拖到**Interactible**脚本的 " **Interactible 操作**" 字段。</span><span class="sxs-lookup"><span data-stu-id="91b08-333">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="91b08-334">双击**TagalongAction**脚本，在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="91b08-334">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible 设置](images/holograms210-interactible.png)

<span data-ttu-id="91b08-336">我们需要添加以下内容：</span><span class="sxs-lookup"><span data-stu-id="91b08-336">We need to add the following:</span></span>

* <span data-ttu-id="91b08-337">将功能添加到 TagalongAction 脚本中的 PerformAction 函数（继承自 InteractibleAction）。</span><span class="sxs-lookup"><span data-stu-id="91b08-337">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="91b08-338">将 billboarding 添加到 gazed 对象，并将透视轴设置为 XY。</span><span class="sxs-lookup"><span data-stu-id="91b08-338">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="91b08-339">然后将简单标记添加到对象。</span><span class="sxs-lookup"><span data-stu-id="91b08-339">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="91b08-340">下面是**TagalongAction.cs**的解决方案：</span><span class="sxs-lookup"><span data-stu-id="91b08-340">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="91b08-341">试试看吧！</span><span class="sxs-lookup"><span data-stu-id="91b08-341">Try it!</span></span> <span data-ttu-id="91b08-342">生成并部署应用。</span><span class="sxs-lookup"><span data-stu-id="91b08-342">Build and deploy the app.</span></span>
* <span data-ttu-id="91b08-343">观察内容如何沿着注视点的中心，但不会不断地进行阻止。</span><span class="sxs-lookup"><span data-stu-id="91b08-343">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
