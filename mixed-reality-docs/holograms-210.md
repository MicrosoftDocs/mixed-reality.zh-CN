---
title: MR 输入 210-的视线移动
description: 遵循此编码使用 Unity、 Visual Studio 和 HoloLens 若要了解的视线移动概念的详细信息的演练。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity，学院，教程，提供注视
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993548"
---
>[!NOTE]
><span data-ttu-id="adac0-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="adac0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="adac0-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="adac0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="adac0-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="adac0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="adac0-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="adac0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="adac0-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="adac0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="adac0-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="adac0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="adac0-110">MR 输入 210:凝视</span><span class="sxs-lookup"><span data-stu-id="adac0-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="adac0-111">[注视](gaze.md)是第一种形式的输入和显示用户的意图和感知。</span><span class="sxs-lookup"><span data-stu-id="adac0-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="adac0-112">MR 输入 210 （也称为项目资源管理器） 是为 Windows Mixed Reality 为提供注视相关概念的深入探讨。</span><span class="sxs-lookup"><span data-stu-id="adac0-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="adac0-113">我们将添加的上下文感知到我们的光标和全息，充分利用您的应用程序有关的视线移动用户的信息可以了解的内容。</span><span class="sxs-lookup"><span data-stu-id="adac0-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="adac0-114">我们具有友好顶级此处可帮助你了解的视线移动概念。</span><span class="sxs-lookup"><span data-stu-id="adac0-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="adac0-115">在中[MR 基础知识 101](holograms-101.md)，我们有一个简单的游标，只需遵循你的视线移动。</span><span class="sxs-lookup"><span data-stu-id="adac0-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="adac0-116">今天我们要搬走局限于简单的游标：</span><span class="sxs-lookup"><span data-stu-id="adac0-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="adac0-117">我们正在进行的游标和我们全息的视线移动感知： 同时将更改基于位置查找用户-或用户所在*不*查找。</span><span class="sxs-lookup"><span data-stu-id="adac0-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="adac0-118">这使它们上下文感知。</span><span class="sxs-lookup"><span data-stu-id="adac0-118">This makes them context-aware.</span></span>
* <span data-ttu-id="adac0-119">我们将添加到我们的光标和全息为用户提供更多上下文上的目标的反馈。</span><span class="sxs-lookup"><span data-stu-id="adac0-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="adac0-120">这种反馈可以是音频和可视化。</span><span class="sxs-lookup"><span data-stu-id="adac0-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="adac0-121">我们将展示你的目标的技术来帮助用户按较小的目标。</span><span class="sxs-lookup"><span data-stu-id="adac0-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="adac0-122">我们将向您展示如何为你使用方向指示器全息突出用户的。</span><span class="sxs-lookup"><span data-stu-id="adac0-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="adac0-123">我们将指导您使用的用户需要在全息，因为她在您的世界中移动的技术。</span><span class="sxs-lookup"><span data-stu-id="adac0-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="adac0-124">使用 Unity 和混合现实工具包的较旧版本记录中的以下章节每个嵌入的视频。</span><span class="sxs-lookup"><span data-stu-id="adac0-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="adac0-125">准确且最新的分步说明时，可能会看到脚本和已过期的相应视频中的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="adac0-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="adac0-126">保持为长期的视频和因为涵盖了概念仍然适用。</span><span class="sxs-lookup"><span data-stu-id="adac0-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="adac0-127">设备支持</span><span class="sxs-lookup"><span data-stu-id="adac0-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="adac0-128">课程</span><span class="sxs-lookup"><span data-stu-id="adac0-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="adac0-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="adac0-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="adac0-130"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="adac0-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="adac0-131">MR 输入 210:凝视</span><span class="sxs-lookup"><span data-stu-id="adac0-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="adac0-132">✔️</span><span class="sxs-lookup"><span data-stu-id="adac0-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="adac0-133">✔️</span><span class="sxs-lookup"><span data-stu-id="adac0-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="adac0-134">开始之前</span><span class="sxs-lookup"><span data-stu-id="adac0-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="adac0-135">系统必备</span><span class="sxs-lookup"><span data-stu-id="adac0-135">Prerequisites</span></span>

* <span data-ttu-id="adac0-136">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="adac0-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="adac0-137">一些基本C#编程功能。</span><span class="sxs-lookup"><span data-stu-id="adac0-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="adac0-138">您应当已完成[MR 基础知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="adac0-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="adac0-139">HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="adac0-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="adac0-140">项目文件</span><span class="sxs-lookup"><span data-stu-id="adac0-140">Project files</span></span>

* <span data-ttu-id="adac0-141">下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip)所需的项目。</span><span class="sxs-lookup"><span data-stu-id="adac0-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="adac0-142"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="adac0-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="adac0-143">取消存档到您的桌面或其他轻松地访问位置的文件。</span><span class="sxs-lookup"><span data-stu-id="adac0-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="adac0-144">如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)。</span><span class="sxs-lookup"><span data-stu-id="adac0-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="adac0-145">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="adac0-145">Errata and Notes</span></span>

* <span data-ttu-id="adac0-146">"仅我的代码"必须是在 Visual Studio 中，在工具 （未选中） 已禁用-> 选项-> 以命中断点在代码中的调试。</span><span class="sxs-lookup"><span data-stu-id="adac0-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="adac0-147">第 1 章-Unity 安装程序</span><span class="sxs-lookup"><span data-stu-id="adac0-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="adac0-148">目标</span><span class="sxs-lookup"><span data-stu-id="adac0-148">Objectives</span></span>

* <span data-ttu-id="adac0-149">优化 HoloLens 开发 Unity。</span><span class="sxs-lookup"><span data-stu-id="adac0-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="adac0-150">导入资产和设置场景。</span><span class="sxs-lookup"><span data-stu-id="adac0-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="adac0-151">HoloLens 中查看顶级。</span><span class="sxs-lookup"><span data-stu-id="adac0-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="adac0-152">说明</span><span class="sxs-lookup"><span data-stu-id="adac0-152">Instructions</span></span>

1. <span data-ttu-id="adac0-153">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="adac0-153">Start Unity.</span></span>
2. <span data-ttu-id="adac0-154">选择**新的项目**。</span><span class="sxs-lookup"><span data-stu-id="adac0-154">Select **New Project**.</span></span>
3. <span data-ttu-id="adac0-155">将项目命名**ModelExplorer**。</span><span class="sxs-lookup"><span data-stu-id="adac0-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="adac0-156">输入与位置**注视**文件夹你之前未存档。</span><span class="sxs-lookup"><span data-stu-id="adac0-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="adac0-157">请确保项目设置为**3D**。</span><span class="sxs-lookup"><span data-stu-id="adac0-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="adac0-158">单击**创建项目**。</span><span class="sxs-lookup"><span data-stu-id="adac0-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="adac0-159">HoloLens 的 unity 设置</span><span class="sxs-lookup"><span data-stu-id="adac0-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="adac0-160">我们需要让 Unity 知道我们尝试导出该应用应创建[沉浸式视图](app-views.md)而不是二维视图。</span><span class="sxs-lookup"><span data-stu-id="adac0-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="adac0-161">我们通过将 HoloLens 添加为虚拟现实设备执行该操作。</span><span class="sxs-lookup"><span data-stu-id="adac0-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="adac0-162">转到**编辑 > 项目设置 > 播放机**。</span><span class="sxs-lookup"><span data-stu-id="adac0-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="adac0-163">在中**检查器面板**对于播放机设置，选择**Windows 应用商店**图标。</span><span class="sxs-lookup"><span data-stu-id="adac0-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="adac0-164">展开**XR 设置**组。</span><span class="sxs-lookup"><span data-stu-id="adac0-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="adac0-165">在中**呈现**部分中，选择**受支持的虚拟现实**复选框以添加新**虚拟现实 Sdk**列表。</span><span class="sxs-lookup"><span data-stu-id="adac0-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="adac0-166">确认**Windows Mixed Reality**出现在列表中。</span><span class="sxs-lookup"><span data-stu-id="adac0-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="adac0-167">如果没有，请选择 **+** 按钮在列表的底部，然后选择**Windows Holographic**。</span><span class="sxs-lookup"><span data-stu-id="adac0-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="adac0-168">接下来，我们需要将我们的脚本编写后端设置为.NET。</span><span class="sxs-lookup"><span data-stu-id="adac0-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="adac0-169">转到**编辑 > 项目设置 > 播放机**（你可能仍需要这从上一步）。</span><span class="sxs-lookup"><span data-stu-id="adac0-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="adac0-170">在中**检查器面板**对于播放机设置，选择**Windows 应用商店**图标。</span><span class="sxs-lookup"><span data-stu-id="adac0-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="adac0-171">在中**其他设置**配置部分中，请确保**脚本编写后端**设置为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="adac0-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="adac0-172">最后，我们将更新我们的质量设置，以实现在 HoloLens 上的快速性能。</span><span class="sxs-lookup"><span data-stu-id="adac0-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="adac0-173">转到**编辑 > 项目设置 > 质量**。</span><span class="sxs-lookup"><span data-stu-id="adac0-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="adac0-174">中的向下箭头上单击**默认**Windows 应用商店图标下面的行。</span><span class="sxs-lookup"><span data-stu-id="adac0-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="adac0-175">选择**非常低**有关**Windows 应用商店应用程序**。</span><span class="sxs-lookup"><span data-stu-id="adac0-175">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="adac0-176">导入项目资产</span><span class="sxs-lookup"><span data-stu-id="adac0-176">Import project assets</span></span>

1. <span data-ttu-id="adac0-177">右键单击**资产**中的文件夹**项目**面板。</span><span class="sxs-lookup"><span data-stu-id="adac0-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="adac0-178">单击**导入包 > 自定义包**。</span><span class="sxs-lookup"><span data-stu-id="adac0-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="adac0-179">导航到下载的项目文件并单击**ModelExplorer.unitypackage**。</span><span class="sxs-lookup"><span data-stu-id="adac0-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="adac0-180">单击“打开” 。</span><span class="sxs-lookup"><span data-stu-id="adac0-180">Click **Open**.</span></span>
5. <span data-ttu-id="adac0-181">包加载后，单击**导入**按钮。</span><span class="sxs-lookup"><span data-stu-id="adac0-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="adac0-182">设置场景</span><span class="sxs-lookup"><span data-stu-id="adac0-182">Setup the scene</span></span>

1. <span data-ttu-id="adac0-183">在层次结构中删除**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="adac0-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="adac0-184">在中**HoloToolkit**文件夹中，打开**输入**文件夹，然后打开**预设**文件夹。</span><span class="sxs-lookup"><span data-stu-id="adac0-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="adac0-185">拖放到**MixedRealityCameraParent**从预设**预设**文件夹导入到**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="adac0-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="adac0-186">右键单击**定向光**在层次结构中，选择**删除**。</span><span class="sxs-lookup"><span data-stu-id="adac0-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="adac0-187">在中**全息**文件夹中，拖放到的根以下资产**层次结构**:</span><span class="sxs-lookup"><span data-stu-id="adac0-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="adac0-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="adac0-188">**AstroMan**</span></span>
    * <span data-ttu-id="adac0-189">**灯**</span><span class="sxs-lookup"><span data-stu-id="adac0-189">**Lights**</span></span>
    * <span data-ttu-id="adac0-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="adac0-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="adac0-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="adac0-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="adac0-192">启动**播放模式下**▶ 查看顶级。</span><span class="sxs-lookup"><span data-stu-id="adac0-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="adac0-193">单击**播放模式下**▶ 再次向**停止**。</span><span class="sxs-lookup"><span data-stu-id="adac0-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="adac0-194">在中**全息**文件夹中，找到**Fitbox**资产并将其拖到的根**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="adac0-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="adac0-195">选择**Fitbox**中**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="adac0-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="adac0-196">拖动**AstroMan**从集合**层次结构**到**Hologram 集合**属性中 Fitbox**检查器**面板。</span><span class="sxs-lookup"><span data-stu-id="adac0-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="adac0-197">保存项目</span><span class="sxs-lookup"><span data-stu-id="adac0-197">Save the project</span></span>

1. <span data-ttu-id="adac0-198">保存新的场景：**文件 > 另存为场景**。</span><span class="sxs-lookup"><span data-stu-id="adac0-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="adac0-199">单击**新文件夹**，然后将文件夹**场景**。</span><span class="sxs-lookup"><span data-stu-id="adac0-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="adac0-200">将文件"**ModelExplorer**"并将其保存在**场景**文件夹。</span><span class="sxs-lookup"><span data-stu-id="adac0-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="adac0-201">生成项目</span><span class="sxs-lookup"><span data-stu-id="adac0-201">Build the project</span></span>

1. <span data-ttu-id="adac0-202">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="adac0-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="adac0-203">单击**添加打开场景**添加场景。</span><span class="sxs-lookup"><span data-stu-id="adac0-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="adac0-204">选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**。</span><span class="sxs-lookup"><span data-stu-id="adac0-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="adac0-205">如果您专门为 HoloLens 开发，设置**目标设备**到**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="adac0-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="adac0-206">否则，将其保持打开**任何设备**。</span><span class="sxs-lookup"><span data-stu-id="adac0-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="adac0-207">请确保**生成类型**设置为**D3D**并**SDK**设置为**最新安装**（应为 16299 或更高版本的 SDK）。</span><span class="sxs-lookup"><span data-stu-id="adac0-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="adac0-208">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="adac0-208">Click **Build**.</span></span>
7. <span data-ttu-id="adac0-209">创建**新文件夹**名为"应用"。</span><span class="sxs-lookup"><span data-stu-id="adac0-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="adac0-210">单击一下**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="adac0-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="adac0-211">按**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="adac0-211">Press **Select Folder**.</span></span>

<span data-ttu-id="adac0-212">Unity 完成操作后，将出现一个文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="adac0-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="adac0-213">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="adac0-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="adac0-214">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="adac0-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="adac0-215">如果部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="adac0-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="adac0-216">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x86**。</span><span class="sxs-lookup"><span data-stu-id="adac0-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="adac0-217">单击向下箭头旁边的本地计算机按钮，然后选择**远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="adac0-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="adac0-218">输入**HoloLens 设备 IP 地址**并将身份验证模式设置为**通用 （未加密的协议）**。</span><span class="sxs-lookup"><span data-stu-id="adac0-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="adac0-219">单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="adac0-219">Click **Select**.</span></span> <span data-ttu-id="adac0-220">如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**。</span><span class="sxs-lookup"><span data-stu-id="adac0-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="adac0-221">在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="adac0-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="adac0-222">如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="adac0-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="adac0-223">当部署应用时，消除**Fitbox**与**选择手势**。</span><span class="sxs-lookup"><span data-stu-id="adac0-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="adac0-224">如果部署到沉浸式头戴式：</span><span class="sxs-lookup"><span data-stu-id="adac0-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="adac0-225">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x64**。</span><span class="sxs-lookup"><span data-stu-id="adac0-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="adac0-226">请确保部署目标设置为**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="adac0-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="adac0-227">在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="adac0-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="adac0-228">当部署应用时，消除**Fitbox**拉开运动控制器上的触发器。</span><span class="sxs-lookup"><span data-stu-id="adac0-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="adac0-229">第 2 章-光标和目标的反馈</span><span class="sxs-lookup"><span data-stu-id="adac0-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="adac0-230">目标</span><span class="sxs-lookup"><span data-stu-id="adac0-230">Objectives</span></span>

* <span data-ttu-id="adac0-231">光标视觉设计和行为。</span><span class="sxs-lookup"><span data-stu-id="adac0-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="adac0-232">视线移动基于游标的反馈。</span><span class="sxs-lookup"><span data-stu-id="adac0-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="adac0-233">基于的视线移动的 hologram 反馈。</span><span class="sxs-lookup"><span data-stu-id="adac0-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="adac0-234">我们要即基础的一些游标设计原则，我们的工作：</span><span class="sxs-lookup"><span data-stu-id="adac0-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="adac0-235">光标始终存在。</span><span class="sxs-lookup"><span data-stu-id="adac0-235">The cursor is always present.</span></span>
* <span data-ttu-id="adac0-236">不要让获取太小或最大的光标。</span><span class="sxs-lookup"><span data-stu-id="adac0-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="adac0-237">避免不阻止的内容。</span><span class="sxs-lookup"><span data-stu-id="adac0-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="adac0-238">说明</span><span class="sxs-lookup"><span data-stu-id="adac0-238">Instructions</span></span>

1. <span data-ttu-id="adac0-239">在中**HoloToolkit\Input\Prefabs**文件夹中，找到**InputManager**资产。</span><span class="sxs-lookup"><span data-stu-id="adac0-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="adac0-240">拖放到**InputManager**拖动到**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="adac0-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="adac0-241">在中**HoloToolkit\Input\Prefabs**文件夹中，找到**光标**资产。</span><span class="sxs-lookup"><span data-stu-id="adac0-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="adac0-242">拖放到**游标**拖动到**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="adac0-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="adac0-243">选择**InputManager**对象中**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="adac0-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="adac0-244">拖动**游标**对象从**层次结构**到 InputManager **SimpleSinglePointerSelector**的**游标**字段中，在底部**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="adac0-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![简单单指针选择器设置](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="adac0-246">生成和部署</span><span class="sxs-lookup"><span data-stu-id="adac0-246">Build and Deploy</span></span>

1. <span data-ttu-id="adac0-247">重新生成该应用程序从**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="adac0-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="adac0-248">打开**应用程序文件夹**。</span><span class="sxs-lookup"><span data-stu-id="adac0-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="adac0-249">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="adac0-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="adac0-250">单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="adac0-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="adac0-251">观察如何绘制光标，及其如何更改外观，如果它触摸一张全息图。</span><span class="sxs-lookup"><span data-stu-id="adac0-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="adac0-252">说明</span><span class="sxs-lookup"><span data-stu-id="adac0-252">Instructions</span></span>

1. <span data-ttu-id="adac0-253">在中**层次结构**面板中，展开**AstroMan**->**GEO_G**->**Back_Center**对象。</span><span class="sxs-lookup"><span data-stu-id="adac0-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="adac0-254">双击**Interactible.cs**若要在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="adac0-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="adac0-255">取消注释中的行**IFocusable.OnFocusEnter()** 并**IFocusable.OnFocusExit()** 中的回调**Interactible.cs**。</span><span class="sxs-lookup"><span data-stu-id="adac0-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="adac0-256">当焦点 （不管是通过提供注视或控制器指向） 进入和退出特定 GameObject 碰撞体由混合现实工具包 InputManager 调用。</span><span class="sxs-lookup"><span data-stu-id="adac0-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

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
><span data-ttu-id="adac0-257">我们使用`EnableKeyword`和`DisableKeyword`上面。</span><span class="sxs-lookup"><span data-stu-id="adac0-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="adac0-258">为了使这些与标准的工具包的着色器应用中使用，将需要遵循[Unity 指导原则，用于访问通过脚本材料](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)。</span><span class="sxs-lookup"><span data-stu-id="adac0-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="adac0-259">在这种情况下，我们已经提供了[突出显示的材料的三个变体](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials)所需的资源文件夹 （查找名称中的突出显示的三个材料） 中。</span><span class="sxs-lookup"><span data-stu-id="adac0-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="adac0-260">生成和部署</span><span class="sxs-lookup"><span data-stu-id="adac0-260">Build and Deploy</span></span>

1. <span data-ttu-id="adac0-261">与前面一样，生成项目，并将部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="adac0-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="adac0-262">观察提供注视旨在对象时会发生什么情况，它不是。</span><span class="sxs-lookup"><span data-stu-id="adac0-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="adac0-263">第 3 章-面向技术</span><span class="sxs-lookup"><span data-stu-id="adac0-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="adac0-264">目标</span><span class="sxs-lookup"><span data-stu-id="adac0-264">Objectives</span></span>

* <span data-ttu-id="adac0-265">使其更易于目标全息。</span><span class="sxs-lookup"><span data-stu-id="adac0-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="adac0-266">稳定自然头移动。</span><span class="sxs-lookup"><span data-stu-id="adac0-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="adac0-267">说明</span><span class="sxs-lookup"><span data-stu-id="adac0-267">Instructions</span></span>

1. <span data-ttu-id="adac0-268">在中**层次结构**面板中，选择**InputManager**对象。</span><span class="sxs-lookup"><span data-stu-id="adac0-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="adac0-269">在中**Inspector**面板中，找到**注视稳定器**脚本。</span><span class="sxs-lookup"><span data-stu-id="adac0-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="adac0-270">如果你想要查看，请单击它以在 Visual Studio 中打开。</span><span class="sxs-lookup"><span data-stu-id="adac0-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="adac0-271">此脚本循环访问示例 Raycast 数据，并有助于稳定精度面向用户的视线移动。</span><span class="sxs-lookup"><span data-stu-id="adac0-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="adac0-272">在中**Inspector**，可以编辑**存储稳定性示例**值。</span><span class="sxs-lookup"><span data-stu-id="adac0-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="adac0-273">此值表示稳定器循环访问到计算经过稳定的值的样本的数。</span><span class="sxs-lookup"><span data-stu-id="adac0-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="adac0-274">第 4 章-方向指示器</span><span class="sxs-lookup"><span data-stu-id="adac0-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="adac0-275">目标</span><span class="sxs-lookup"><span data-stu-id="adac0-275">Objectives</span></span>

* <span data-ttu-id="adac0-276">添加对游标来帮助查找全息方向指示器。</span><span class="sxs-lookup"><span data-stu-id="adac0-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="adac0-277">说明</span><span class="sxs-lookup"><span data-stu-id="adac0-277">Instructions</span></span>

<span data-ttu-id="adac0-278">我们将使用**DirectionIndicator.cs**文件将该文件：</span><span class="sxs-lookup"><span data-stu-id="adac0-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="adac0-279">如果用户不在全息观望显示方向指示器。</span><span class="sxs-lookup"><span data-stu-id="adac0-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="adac0-280">在全息观望用户的情况下隐藏方向指示器。</span><span class="sxs-lookup"><span data-stu-id="adac0-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="adac0-281">更新为指向全息方向指示器。</span><span class="sxs-lookup"><span data-stu-id="adac0-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="adac0-282">让我们开始吧。</span><span class="sxs-lookup"><span data-stu-id="adac0-282">Let's get started.</span></span>

1. <span data-ttu-id="adac0-283">单击**AstroMan**对象中**层次结构**面板并**单击箭头**以将其展开。</span><span class="sxs-lookup"><span data-stu-id="adac0-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="adac0-284">在中**层次结构**面板中，选择**DirectionalIndicator**对象下**AstroMan**。</span><span class="sxs-lookup"><span data-stu-id="adac0-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="adac0-285">在中**Inspector**面板中，单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="adac0-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="adac0-286">在菜单中，在搜索框中键入**方向指示器**。</span><span class="sxs-lookup"><span data-stu-id="adac0-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="adac0-287">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="adac0-287">Select the search result.</span></span>
5. <span data-ttu-id="adac0-288">在**层次结构**面板中，拖放**光标**对象拖到**游标**中的属性**检查器**。</span><span class="sxs-lookup"><span data-stu-id="adac0-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="adac0-289">在中**项目**面板**全息**文件夹的拖放**DirectionalIndicator**拖到资产**方向指示器**中的属性**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="adac0-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="adac0-290">生成和部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="adac0-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="adac0-291">观看方向指示器对象如何帮助你查找顶级。</span><span class="sxs-lookup"><span data-stu-id="adac0-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="adac0-292">第 5 章-公告板</span><span class="sxs-lookup"><span data-stu-id="adac0-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="adac0-293">目标</span><span class="sxs-lookup"><span data-stu-id="adac0-293">Objectives</span></span>

* <span data-ttu-id="adac0-294">使用公告板可使全息始终面临面向使用者。</span><span class="sxs-lookup"><span data-stu-id="adac0-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="adac0-295">我们将使用**Billboard.cs**要保留一个 GameObject，面向，以便在任何时候，它对着用户文件。</span><span class="sxs-lookup"><span data-stu-id="adac0-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="adac0-296">在中**层次结构**面板中，选择**AstroMan**对象。</span><span class="sxs-lookup"><span data-stu-id="adac0-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="adac0-297">在中**Inspector**面板中，单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="adac0-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="adac0-298">在菜单中，在搜索框中键入**布告栏**。</span><span class="sxs-lookup"><span data-stu-id="adac0-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="adac0-299">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="adac0-299">Select the search result.</span></span>
4. <span data-ttu-id="adac0-300">在中**Inspector**设置**枢轴**到**Y**。</span><span class="sxs-lookup"><span data-stu-id="adac0-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="adac0-301">试试看吧！</span><span class="sxs-lookup"><span data-stu-id="adac0-301">Try it!</span></span> <span data-ttu-id="adac0-302">生成和部署之前为应用。</span><span class="sxs-lookup"><span data-stu-id="adac0-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="adac0-303">请参阅如何宣传位置对象的人脸，无论您如何更改视区。</span><span class="sxs-lookup"><span data-stu-id="adac0-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="adac0-304">删除从脚本**AstroMan**现在。</span><span class="sxs-lookup"><span data-stu-id="adac0-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="adac0-305">第 6 章-尾随</span><span class="sxs-lookup"><span data-stu-id="adac0-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="adac0-306">目标</span><span class="sxs-lookup"><span data-stu-id="adac0-306">Objectives</span></span>

* <span data-ttu-id="adac0-307">使用尾随我们全息关注我们周围的空间。</span><span class="sxs-lookup"><span data-stu-id="adac0-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="adac0-308">当我们在此问题，我们本教程介绍以下设计约束：</span><span class="sxs-lookup"><span data-stu-id="adac0-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="adac0-309">内容应始终为快速消失。</span><span class="sxs-lookup"><span data-stu-id="adac0-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="adac0-310">内容不应为的方式。</span><span class="sxs-lookup"><span data-stu-id="adac0-310">Content should not be in the way.</span></span>
* <span data-ttu-id="adac0-311">Head 锁定内容不舒服。</span><span class="sxs-lookup"><span data-stu-id="adac0-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="adac0-312">此处使用的解决方案是使用"尾随"方法。</span><span class="sxs-lookup"><span data-stu-id="adac0-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="adac0-313">尾随对象永远不会完全离开用户的视图。</span><span class="sxs-lookup"><span data-stu-id="adac0-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="adac0-314">您可以将橡胶带尾随对象为其附加到用户的头。</span><span class="sxs-lookup"><span data-stu-id="adac0-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="adac0-315">当用户移动时，内容将保留在轻松浏览通过滑动指向视图的边缘，无需完全离开。</span><span class="sxs-lookup"><span data-stu-id="adac0-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="adac0-316">时用户 gazes 针对尾随对象，它更充分发挥视图。</span><span class="sxs-lookup"><span data-stu-id="adac0-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="adac0-317">我们将使用**SimpleTagalong.cs**文件将该文件：</span><span class="sxs-lookup"><span data-stu-id="adac0-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="adac0-318">确定是否尾随对象是相机的边界内。</span><span class="sxs-lookup"><span data-stu-id="adac0-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="adac0-319">如果没有在视图截锥，定位到尾随视图截锥内的部分。</span><span class="sxs-lookup"><span data-stu-id="adac0-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="adac0-320">否则，将默认距离的尾随定位从用户中。</span><span class="sxs-lookup"><span data-stu-id="adac0-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="adac0-321">若要执行此操作，我们首先必须更改**Interactible.cs**脚本，以调用**TagalongAction**。</span><span class="sxs-lookup"><span data-stu-id="adac0-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="adac0-322">编辑**Interactible.cs**通过完成编码练习 6.a （取消注释行到第 87 84）。</span><span class="sxs-lookup"><span data-stu-id="adac0-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="adac0-323">**InteractibleAction.cs**脚本，与配对**Interactible.cs**全息上点击时执行自定义操作。</span><span class="sxs-lookup"><span data-stu-id="adac0-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="adac0-324">在这种情况下，我们将使用一个专用于尾随。</span><span class="sxs-lookup"><span data-stu-id="adac0-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="adac0-325">在中**脚本**上的文件夹中单击**TagalongAction.cs**资产，以便在 Visual Studio 中打开。</span><span class="sxs-lookup"><span data-stu-id="adac0-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="adac0-326">完成编码练习，或将它更改为：</span><span class="sxs-lookup"><span data-stu-id="adac0-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="adac0-327">在顶部**层次结构**，在搜索栏中键入**ChestButton_Center**和选择的结果。</span><span class="sxs-lookup"><span data-stu-id="adac0-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="adac0-328">在中**Inspector**面板中，单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="adac0-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="adac0-329">在菜单中，在搜索框中键入**免除操作**。</span><span class="sxs-lookup"><span data-stu-id="adac0-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="adac0-330">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="adac0-330">Select the search result.</span></span>
  * <span data-ttu-id="adac0-331">在中**全息**文件夹查找**免除**资产。</span><span class="sxs-lookup"><span data-stu-id="adac0-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="adac0-332">选择**ChestButton_Center**对象中**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="adac0-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="adac0-333">拖放到**免除**对象从**项目**面板拖到**检查器**到**对象到免除**属性。</span><span class="sxs-lookup"><span data-stu-id="adac0-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="adac0-334">拖动**免除操作**对象从**Inspector**到**Interactible 操作**字段**Interactible**脚本。</span><span class="sxs-lookup"><span data-stu-id="adac0-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="adac0-335">双击**TagalongAction**脚本以在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="adac0-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible 设置](images/holograms210-interactible.png)

<span data-ttu-id="adac0-337">我们需要添加下列代码：</span><span class="sxs-lookup"><span data-stu-id="adac0-337">We need to add the following:</span></span>

* <span data-ttu-id="adac0-338">将功能添加到 （继承自 InteractibleAction） TagalongAction 脚本中的 PerformAction 函数。</span><span class="sxs-lookup"><span data-stu-id="adac0-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="adac0-339">添加公告板 gazed 时对象，并将枢轴设置为 XY。</span><span class="sxs-lookup"><span data-stu-id="adac0-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="adac0-340">然后将简单尾随添加到该对象。</span><span class="sxs-lookup"><span data-stu-id="adac0-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="adac0-341">下面是我们的解决方案，从**TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="adac0-341">Here's our solution, from **TagalongAction.cs**:</span></span>

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

* <span data-ttu-id="adac0-342">试试看吧！</span><span class="sxs-lookup"><span data-stu-id="adac0-342">Try it!</span></span> <span data-ttu-id="adac0-343">生成和部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="adac0-343">Build and deploy the app.</span></span>
* <span data-ttu-id="adac0-344">观看的内容如何遵循的视线移动点的中心，但不是持续并且不会阻止它。</span><span class="sxs-lookup"><span data-stu-id="adac0-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
