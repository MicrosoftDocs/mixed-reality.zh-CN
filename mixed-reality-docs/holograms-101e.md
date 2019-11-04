---
title: MR 基本知识 101E-仿真程序的完整项目
description: 按照此编码演练操作，使用 Unity、Visual Studio 和 HoloLens 模拟器了解全息应用程序的基础知识。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实，Windows Mixed Reality，HoloLens，全息影像，学院，教程，模拟器
ms.openlocfilehash: b1d8e1f3f272051bdd6f69ab88c3aef4f86f13ef
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434705"
---
>[!NOTE]
><span data-ttu-id="3f808-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="3f808-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="3f808-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="3f808-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="3f808-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="3f808-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="3f808-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="3f808-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="3f808-108">为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="3f808-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="3f808-109">MR 基本知识101E：通过模拟器完成项目</span><span class="sxs-lookup"><span data-stu-id="3f808-109">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="3f808-110">本教程将引导你完成 Unity 中内置的一个完整项目，该项目演示了 HoloLens 上核心 Windows Mixed Reality 功能，包括[注视](gaze-and-commit.md)、[手势](gaze-and-commit.md#composite-gestures)、[语音输入](voice-input.md)、[空间音效](spatial-sound.md)和[空间映射](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3f808-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="3f808-111">教程大约需要1小时才能完成。</span><span class="sxs-lookup"><span data-stu-id="3f808-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="3f808-112">设备支持</span><span class="sxs-lookup"><span data-stu-id="3f808-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3f808-113">摘要</span><span class="sxs-lookup"><span data-stu-id="3f808-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="3f808-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="3f808-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="3f808-115"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="3f808-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="3f808-116">MR 基本知识101E：通过模拟器完成项目</span><span class="sxs-lookup"><span data-stu-id="3f808-116">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="3f808-117">✔️</span><span class="sxs-lookup"><span data-stu-id="3f808-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="3f808-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="3f808-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3f808-119">必备条件</span><span class="sxs-lookup"><span data-stu-id="3f808-119">Prerequisites</span></span>

* <span data-ttu-id="3f808-120">配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="3f808-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="3f808-121">项目文件</span><span class="sxs-lookup"><span data-stu-id="3f808-121">Project files</span></span>

* <span data-ttu-id="3f808-122">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="3f808-122">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="3f808-123"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="3f808-123"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="3f808-124">如果仍需要 Unity 5.6 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="3f808-124">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="3f808-125">如果仍需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="3f808-125">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="3f808-126">如果仍需要 Unity 5.4 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="3f808-126">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="3f808-127">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="3f808-127">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="3f808-128">将文件夹名称保留为**日式折纸**。</span><span class="sxs-lookup"><span data-stu-id="3f808-128">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="3f808-129">如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)找到。</span><span class="sxs-lookup"><span data-stu-id="3f808-129">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="3f808-130">第1章-"Holo" 世界</span><span class="sxs-lookup"><span data-stu-id="3f808-130">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="3f808-131">在本章中，我们将设置第一个 Unity 项目，并逐步完成生成和部署过程。</span><span class="sxs-lookup"><span data-stu-id="3f808-131">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="3f808-132">目标</span><span class="sxs-lookup"><span data-stu-id="3f808-132">Objectives</span></span>

* <span data-ttu-id="3f808-133">为全息版开发设置 Unity。</span><span class="sxs-lookup"><span data-stu-id="3f808-133">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="3f808-134">制作全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f808-134">Make a hologram.</span></span>
* <span data-ttu-id="3f808-135">查看您创建的全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f808-135">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f808-136">说明</span><span class="sxs-lookup"><span data-stu-id="3f808-136">Instructions</span></span>

* <span data-ttu-id="3f808-137">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="3f808-137">Start Unity.</span></span>
* <span data-ttu-id="3f808-138">选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-138">Select **Open**.</span></span>
* <span data-ttu-id="3f808-139">输入 "位置" 作为以前未存档的**日式折纸**文件夹。</span><span class="sxs-lookup"><span data-stu-id="3f808-139">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="3f808-140">选择 "**日式折纸**" 并单击 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-140">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="3f808-141">保存新场景： **File** / **将场景另存为**。</span><span class="sxs-lookup"><span data-stu-id="3f808-141">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="3f808-142">将场景命名为**日式折纸**，并按 "**保存**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="3f808-142">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="3f808-143">设置摄像机</span><span class="sxs-lookup"><span data-stu-id="3f808-143">Setup the main camera</span></span>

* <span data-ttu-id="3f808-144">在 "**层次结构" 面板**中，选择 "**主相机**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-144">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="3f808-145">**检查器**将其转换位置设置为**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="3f808-145">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="3f808-146">找到 "**清除标志**" 属性，然后将下拉列表中的**Skybox**更改为**纯色**。</span><span class="sxs-lookup"><span data-stu-id="3f808-146">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="3f808-147">单击 "**背景**" 字段打开颜色选取器。</span><span class="sxs-lookup"><span data-stu-id="3f808-147">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="3f808-148">将**R、G、B 和 A**设置为**0**。</span><span class="sxs-lookup"><span data-stu-id="3f808-148">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="3f808-149">设置场景</span><span class="sxs-lookup"><span data-stu-id="3f808-149">Setup the scene</span></span>

* <span data-ttu-id="3f808-150">在 "**层次结构" 面板**中，单击 "**创建**" 并**创建空**。</span><span class="sxs-lookup"><span data-stu-id="3f808-150">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="3f808-151">右键单击新的 " **GameObject** "，然后选择 "重命名"。</span><span class="sxs-lookup"><span data-stu-id="3f808-151">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="3f808-152">将 GameObject 重命名为**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="3f808-152">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="3f808-153">从 "**项目" 面板**中的 "**全息影像**" 文件夹：</span><span class="sxs-lookup"><span data-stu-id="3f808-153">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="3f808-154">将**阶段**拖到层次结构中，使其成为**OrigamiCollection**的子级。</span><span class="sxs-lookup"><span data-stu-id="3f808-154">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="3f808-155">将**Sphere1**拖到层次结构中，使其成为**OrigamiCollection**的子元素。</span><span class="sxs-lookup"><span data-stu-id="3f808-155">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="3f808-156">将**Sphere2**拖到层次结构中，使其成为**OrigamiCollection**的子元素。</span><span class="sxs-lookup"><span data-stu-id="3f808-156">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="3f808-157">右键单击 "**层次结构" 面板**中的**方向浅**对象，然后选择 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-157">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="3f808-158">从 "**全息影像**" 文件夹中，将**灯光**拖到**层次结构面板**的根。</span><span class="sxs-lookup"><span data-stu-id="3f808-158">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="3f808-159">在**层次结构**中，选择 " **OrigamiCollection**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-159">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="3f808-160">在**检查器**中，将转换位置设置为**0、-0.5、2.0**。</span><span class="sxs-lookup"><span data-stu-id="3f808-160">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="3f808-161">按下 Unity 中的 "**播放**" 按钮，预览全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f808-161">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="3f808-162">预览窗口中应会显示日式折纸对象。</span><span class="sxs-lookup"><span data-stu-id="3f808-162">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="3f808-163">按第二次**播放**以停止预览模式。</span><span class="sxs-lookup"><span data-stu-id="3f808-163">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="3f808-164">将项目从 Unity 导出到 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3f808-164">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="3f808-165">在 Unity 中，选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-165">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="3f808-166">选择 "**平台**" 列表中的 " **Windows 应用商店**"，并单击 "**切换平台**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-166">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="3f808-167">将**SDK**设置为**通用 10** ，将**类型**设置为**D3D**。</span><span class="sxs-lookup"><span data-stu-id="3f808-167">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="3f808-168">检查**Unity C#项目**。</span><span class="sxs-lookup"><span data-stu-id="3f808-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="3f808-169">单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="3f808-169">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="3f808-170">单击 "**播放机设置 ...** "。</span><span class="sxs-lookup"><span data-stu-id="3f808-170">Click **Player Settings...**.</span></span>
* <span data-ttu-id="3f808-171">在 "检查器" 面板中，选择**Windows 应用商店徽标**。</span><span class="sxs-lookup"><span data-stu-id="3f808-171">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="3f808-172">然后选择 "**发布设置**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-172">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="3f808-173">在 "**功能**" 部分中，选择 "**麦克风**" 和 " **SpatialPerception** " 功能。</span><span class="sxs-lookup"><span data-stu-id="3f808-173">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="3f808-174">返回到 "生成设置" 窗口，单击 "**生成**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-174">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="3f808-175">创建名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="3f808-175">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="3f808-176">单击**应用文件夹**。</span><span class="sxs-lookup"><span data-stu-id="3f808-176">Single click the **App Folder**.</span></span>
* <span data-ttu-id="3f808-177">按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-177">Press **Select Folder**.</span></span>
* <span data-ttu-id="3f808-178">当 Unity 完成后，将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="3f808-178">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="3f808-179">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="3f808-179">Open the **App** folder.</span></span>
* <span data-ttu-id="3f808-180">打开**日式折纸 Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="3f808-180">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="3f808-181">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **X86**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-181">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="3f808-182">单击 "设备" 按钮旁边的箭头，然后选择 " **HoloLens 模拟器**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-182">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="3f808-183">单击 "**调试-> 启动但不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="3f808-183">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="3f808-184">经过一段时间后，模拟器将从日式折纸项目开始。</span><span class="sxs-lookup"><span data-stu-id="3f808-184">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="3f808-185">首次启动[仿真程序](using-the-hololens-emulator.md)时，可能需要15分钟的时间来启动仿真器。</span><span class="sxs-lookup"><span data-stu-id="3f808-185">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="3f808-186">启动后，请不要将其关闭。</span><span class="sxs-lookup"><span data-stu-id="3f808-186">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="3f808-187">第2章-注视</span><span class="sxs-lookup"><span data-stu-id="3f808-187">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="3f808-188">在本章中，我们将介绍第三种与全息影像交互的方式--[注视](gaze-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="3f808-188">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="3f808-189">目标</span><span class="sxs-lookup"><span data-stu-id="3f808-189">Objectives</span></span>

* <span data-ttu-id="3f808-190">使用全球锁定的光标直观显示注视。</span><span class="sxs-lookup"><span data-stu-id="3f808-190">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f808-191">说明</span><span class="sxs-lookup"><span data-stu-id="3f808-191">Instructions</span></span>

* <span data-ttu-id="3f808-192">返回到 Unity 项目，并关闭 "生成设置" 窗口（如果它仍处于打开状态）。</span><span class="sxs-lookup"><span data-stu-id="3f808-192">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="3f808-193">在 "**项目" 面板**中选择**全息影像**文件夹。</span><span class="sxs-lookup"><span data-stu-id="3f808-193">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="3f808-194">将**光标**对象拖到**层次结构面板**中的根级别。</span><span class="sxs-lookup"><span data-stu-id="3f808-194">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="3f808-195">双击**光标**对象以详细查看它。</span><span class="sxs-lookup"><span data-stu-id="3f808-195">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="3f808-196">右键单击 "项目" 面板中的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3f808-196">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="3f808-197">单击 "**创建**" 子菜单。</span><span class="sxs-lookup"><span data-stu-id="3f808-197">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="3f808-198">选择 **C# "脚本**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-198">Select **C# Script**.</span></span>
* <span data-ttu-id="3f808-199">将脚本命名为**WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="3f808-199">Name the script **WorldCursor**.</span></span> <span data-ttu-id="3f808-200">注意：名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="3f808-200">Note: The name is case-sensitive.</span></span> <span data-ttu-id="3f808-201">无需添加 .cs 扩展名。</span><span class="sxs-lookup"><span data-stu-id="3f808-201">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="3f808-202">选择 "**层次结构" 面板**中的**光标**对象。</span><span class="sxs-lookup"><span data-stu-id="3f808-202">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="3f808-203">将**WorldCursor**脚本拖放到**检查器面板**。</span><span class="sxs-lookup"><span data-stu-id="3f808-203">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="3f808-204">双击**WorldCursor**脚本，在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="3f808-204">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3f808-205">将此代码复制并粘贴到**WorldCursor.cs** ，并**保存全部**。</span><span class="sxs-lookup"><span data-stu-id="3f808-205">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="3f808-206">从**文件 > 生成设置**重新生成应用。</span><span class="sxs-lookup"><span data-stu-id="3f808-206">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="3f808-207">返回到以前用于部署到模拟器的 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="3f808-207">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="3f808-208">出现提示时，选择 "全部重新加载"。</span><span class="sxs-lookup"><span data-stu-id="3f808-208">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="3f808-209">单击 "**调试-> 启动但不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="3f808-209">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="3f808-210">使用 Xbox 控制器查看场景。</span><span class="sxs-lookup"><span data-stu-id="3f808-210">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="3f808-211">请注意，光标如何与对象的形状交互。</span><span class="sxs-lookup"><span data-stu-id="3f808-211">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="3f808-212">第3章-手势</span><span class="sxs-lookup"><span data-stu-id="3f808-212">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="3f808-213">在本章中，我们将添加对[手势](gaze-and-commit.md#composite-gestures)的支持。</span><span class="sxs-lookup"><span data-stu-id="3f808-213">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="3f808-214">当用户选择某一回形针时，我们将使用 Unity 的物理引擎开启重心来使球落在一起。</span><span class="sxs-lookup"><span data-stu-id="3f808-214">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="3f808-215">目标</span><span class="sxs-lookup"><span data-stu-id="3f808-215">Objectives</span></span>

* <span data-ttu-id="3f808-216">用选择手势控制全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f808-216">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f808-217">说明</span><span class="sxs-lookup"><span data-stu-id="3f808-217">Instructions</span></span>

<span data-ttu-id="3f808-218">首先，我们要创建一个脚本来检测选择的手势。</span><span class="sxs-lookup"><span data-stu-id="3f808-218">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="3f808-219">在 "**脚本**" 文件夹中，创建一个名为**GazeGestureManager**的脚本。</span><span class="sxs-lookup"><span data-stu-id="3f808-219">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="3f808-220">将**GazeGestureManager**脚本拖到层次结构中的**OrigamiCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="3f808-220">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="3f808-221">在 Visual Studio 中打开**GazeGestureManager**脚本，并添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="3f808-221">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="3f808-222">在 Scripts 文件夹中创建另一个脚本，这一次名为**SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="3f808-222">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="3f808-223">展开层次结构视图中的**OrigamiCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="3f808-223">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="3f808-224">将**SphereCommands**脚本拖到 "层次结构" 面板中的 " **Sphere1** " 对象。</span><span class="sxs-lookup"><span data-stu-id="3f808-224">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="3f808-225">将**SphereCommands**脚本拖到 "层次结构" 面板中的 " **Sphere2** " 对象。</span><span class="sxs-lookup"><span data-stu-id="3f808-225">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="3f808-226">在 Visual Studio 中打开脚本进行编辑，并将默认代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="3f808-226">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="3f808-227">导出应用，生成应用并将其部署到 HoloLens 模拟器。</span><span class="sxs-lookup"><span data-stu-id="3f808-227">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="3f808-228">查看场景，并将其放在一个球上。</span><span class="sxs-lookup"><span data-stu-id="3f808-228">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="3f808-229">按下 Xbox 控制器上**的按钮，** 或按空格键来模拟选择手势。</span><span class="sxs-lookup"><span data-stu-id="3f808-229">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="3f808-230">第4章-语音</span><span class="sxs-lookup"><span data-stu-id="3f808-230">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="3f808-231">在本章中，我们将添加对两个[声音命令](voice-input.md)的支持： "重置世界"，将已删除的球返回到其原始位置，并将 "丢球" 设置为球落。</span><span class="sxs-lookup"><span data-stu-id="3f808-231">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="3f808-232">目标</span><span class="sxs-lookup"><span data-stu-id="3f808-232">Objectives</span></span>

* <span data-ttu-id="3f808-233">添加始终在后台侦听的语音命令。</span><span class="sxs-lookup"><span data-stu-id="3f808-233">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="3f808-234">创建可响应语音命令的全息图。</span><span class="sxs-lookup"><span data-stu-id="3f808-234">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f808-235">说明</span><span class="sxs-lookup"><span data-stu-id="3f808-235">Instructions</span></span>

* <span data-ttu-id="3f808-236">在 "**脚本**" 文件夹中，创建一个名为**SpeechManager**的脚本。</span><span class="sxs-lookup"><span data-stu-id="3f808-236">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="3f808-237">将**SpeechManager**脚本拖到层次结构中的**OrigamiCollection**对象上</span><span class="sxs-lookup"><span data-stu-id="3f808-237">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="3f808-238">在 Visual Studio 中打开**SpeechManager**脚本。</span><span class="sxs-lookup"><span data-stu-id="3f808-238">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="3f808-239">将此代码复制并粘贴到**SpeechManager.cs** ，并**保存全部**内容：</span><span class="sxs-lookup"><span data-stu-id="3f808-239">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="3f808-240">在 Visual Studio 中打开**SphereCommands**脚本。</span><span class="sxs-lookup"><span data-stu-id="3f808-240">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="3f808-241">按如下所示更新脚本以进行读取：</span><span class="sxs-lookup"><span data-stu-id="3f808-241">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="3f808-242">导出应用，生成应用并将其部署到 HoloLens 模拟器。</span><span class="sxs-lookup"><span data-stu-id="3f808-242">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="3f808-243">模拟器将支持您的 PC 麦克风并对您的语音做出响应：调整视图，使光标位于球体之一上，并说 "放置球"。</span><span class="sxs-lookup"><span data-stu-id="3f808-243">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="3f808-244">说 "**重置世界**"，将其返回到其初始位置。</span><span class="sxs-lookup"><span data-stu-id="3f808-244">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="3f808-245">第5章-空间音效</span><span class="sxs-lookup"><span data-stu-id="3f808-245">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="3f808-246">在本章中，我们将向应用程序添加音乐，并触发对某些操作的声音影响。</span><span class="sxs-lookup"><span data-stu-id="3f808-246">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="3f808-247">我们将使用[空间音效](spatial-sound.md)为声音指定3d 空间中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="3f808-247">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="3f808-248">目标</span><span class="sxs-lookup"><span data-stu-id="3f808-248">Objectives</span></span>

* <span data-ttu-id="3f808-249">收听世界上的全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f808-249">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f808-250">说明</span><span class="sxs-lookup"><span data-stu-id="3f808-250">Instructions</span></span>

* <span data-ttu-id="3f808-251">在 Unity 中从顶部菜单中选择 "**编辑 > 项目设置 > 音频**"</span><span class="sxs-lookup"><span data-stu-id="3f808-251">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="3f808-252">找到**Spatializer 插件**设置，并选择 " **MS HRTF Spatializer**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-252">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="3f808-253">从 "**全息影像**" 文件夹中，将 "**环境**" 对象拖到 "层次结构" 面板中的**OrigamiCollection**对象上。</span><span class="sxs-lookup"><span data-stu-id="3f808-253">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="3f808-254">选择**OrigamiCollection**并找到**音频源**组件。</span><span class="sxs-lookup"><span data-stu-id="3f808-254">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="3f808-255">更改这些属性：</span><span class="sxs-lookup"><span data-stu-id="3f808-255">Change these properties:</span></span>
  * <span data-ttu-id="3f808-256">检查**Spatialize**属性。</span><span class="sxs-lookup"><span data-stu-id="3f808-256">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="3f808-257">选中 "**在唤醒状态播放**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-257">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="3f808-258">通过将滑块一直拖到右侧，将**空间混合**更改为**三维**。</span><span class="sxs-lookup"><span data-stu-id="3f808-258">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="3f808-259">检查**循环**属性。</span><span class="sxs-lookup"><span data-stu-id="3f808-259">Check the **Loop** property.</span></span>
  * <span data-ttu-id="3f808-260">展开 "**三维声音设置**"，然后为 " **Doppler" 级别**输入**0.1** 。</span><span class="sxs-lookup"><span data-stu-id="3f808-260">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="3f808-261">将**Volume Rolloff**设置为**对数 Rolloff**。</span><span class="sxs-lookup"><span data-stu-id="3f808-261">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="3f808-262">将**最大距离**设置为**20**。</span><span class="sxs-lookup"><span data-stu-id="3f808-262">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="3f808-263">在 "**脚本**" 文件夹中，创建一个名为**SphereSounds**的脚本。</span><span class="sxs-lookup"><span data-stu-id="3f808-263">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="3f808-264">将**SphereSounds**拖到层次结构中的**Sphere1**和**Sphere2**对象。</span><span class="sxs-lookup"><span data-stu-id="3f808-264">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="3f808-265">在 Visual Studio 中打开**SphereSounds** ，更新以下代码并**全部保存**。</span><span class="sxs-lookup"><span data-stu-id="3f808-265">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="3f808-266">保存该脚本并返回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="3f808-266">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="3f808-267">导出应用，生成应用并将其部署到 HoloLens 模拟器。</span><span class="sxs-lookup"><span data-stu-id="3f808-267">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="3f808-268">戴耳机以获得全部效果，并从舞台更近和更深入地收听声音变化。</span><span class="sxs-lookup"><span data-stu-id="3f808-268">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="3f808-269">第6章-空间映射</span><span class="sxs-lookup"><span data-stu-id="3f808-269">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="3f808-270">现在，我们将使用[空间映射](spatial-mapping.md)将游戏板置于真实世界的真实对象上。</span><span class="sxs-lookup"><span data-stu-id="3f808-270">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="3f808-271">目标</span><span class="sxs-lookup"><span data-stu-id="3f808-271">Objectives</span></span>

* <span data-ttu-id="3f808-272">将你的真实世界带入虚拟世界。</span><span class="sxs-lookup"><span data-stu-id="3f808-272">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="3f808-273">将全息影像置于最重要的位置。</span><span class="sxs-lookup"><span data-stu-id="3f808-273">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="3f808-274">说明</span><span class="sxs-lookup"><span data-stu-id="3f808-274">Instructions</span></span>

* <span data-ttu-id="3f808-275">在 "项目" 面板中单击 "**全息影像**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3f808-275">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="3f808-276">将**空间映射**资产拖到**层次结构**的根。</span><span class="sxs-lookup"><span data-stu-id="3f808-276">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="3f808-277">单击层次结构中的**空间映射**对象。</span><span class="sxs-lookup"><span data-stu-id="3f808-277">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="3f808-278">在 "**检查器" 面板**中，更改以下属性：</span><span class="sxs-lookup"><span data-stu-id="3f808-278">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="3f808-279">选中 "**绘制可视网格**" 框。</span><span class="sxs-lookup"><span data-stu-id="3f808-279">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="3f808-280">定位**绘图材料**，并单击右侧的圆圈。</span><span class="sxs-lookup"><span data-stu-id="3f808-280">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="3f808-281">在顶部的搜索字段中键入 "**线框**"。</span><span class="sxs-lookup"><span data-stu-id="3f808-281">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="3f808-282">单击结果，然后关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="3f808-282">Click on the result and then close the window.</span></span>
* <span data-ttu-id="3f808-283">导出应用，生成应用并将其部署到 HoloLens 模拟器。</span><span class="sxs-lookup"><span data-stu-id="3f808-283">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="3f808-284">当应用程序运行时，先前扫描的现实生活空间的网格将以线框形式呈现。</span><span class="sxs-lookup"><span data-stu-id="3f808-284">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="3f808-285">观看某个滚动球如何偏离舞台，并观看地面！</span><span class="sxs-lookup"><span data-stu-id="3f808-285">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="3f808-286">现在，我们将向你展示如何将 OrigamiCollection 移动到一个新位置：</span><span class="sxs-lookup"><span data-stu-id="3f808-286">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="3f808-287">在 "**脚本**" 文件夹中，创建一个名为**TapToPlaceParent**的脚本。</span><span class="sxs-lookup"><span data-stu-id="3f808-287">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="3f808-288">在**层次结构**中，展开 " **OrigamiCollection** "，然后选择 "**暂存**" 对象。</span><span class="sxs-lookup"><span data-stu-id="3f808-288">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="3f808-289">将**TapToPlaceParent**脚本拖到 "暂存" 对象上。</span><span class="sxs-lookup"><span data-stu-id="3f808-289">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="3f808-290">在 Visual Studio 中打开**TapToPlaceParent**脚本，并将其更新为以下内容：</span><span class="sxs-lookup"><span data-stu-id="3f808-290">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="3f808-291">导出、生成并部署应用。</span><span class="sxs-lookup"><span data-stu-id="3f808-291">Export, build and deploy the app.</span></span>
* <span data-ttu-id="3f808-292">现在，您应该能够通过 gazing 在特定位置放置游戏，使用 "选择手势" （**a**或空格键），然后移动到一个新位置，然后再次使用 "选择手势"。</span><span class="sxs-lookup"><span data-stu-id="3f808-292">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="3f808-293">结束</span><span class="sxs-lookup"><span data-stu-id="3f808-293">The end</span></span>

<span data-ttu-id="3f808-294">这就是本教程的结尾！</span><span class="sxs-lookup"><span data-stu-id="3f808-294">And that's the end of this tutorial!</span></span>

<span data-ttu-id="3f808-295">已学习：</span><span class="sxs-lookup"><span data-stu-id="3f808-295">You learned:</span></span>

* <span data-ttu-id="3f808-296">如何在 Unity 中创建全息应用。</span><span class="sxs-lookup"><span data-stu-id="3f808-296">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="3f808-297">如何使用注视、手势、语音、声音和空间映射。</span><span class="sxs-lookup"><span data-stu-id="3f808-297">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="3f808-298">如何使用 Visual Studio 生成和部署应用。</span><span class="sxs-lookup"><span data-stu-id="3f808-298">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="3f808-299">你现在已准备好开始创建自己的全息应用！</span><span class="sxs-lookup"><span data-stu-id="3f808-299">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="3f808-300">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f808-300">See also</span></span>

* [<span data-ttu-id="3f808-301">MR 基本101：通过设备完成项目</span><span class="sxs-lookup"><span data-stu-id="3f808-301">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="3f808-302">凝视</span><span class="sxs-lookup"><span data-stu-id="3f808-302">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="3f808-303">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="3f808-303">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="3f808-304">语音输入</span><span class="sxs-lookup"><span data-stu-id="3f808-304">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="3f808-305">空间音效</span><span class="sxs-lookup"><span data-stu-id="3f808-305">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="3f808-306">空间映射</span><span class="sxs-lookup"><span data-stu-id="3f808-306">Spatial mapping</span></span>](spatial-mapping.md)
