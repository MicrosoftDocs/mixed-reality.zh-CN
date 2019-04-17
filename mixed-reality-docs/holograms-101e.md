---
title: MR 基础知识 101E-使用仿真程序的完整项目
description: 遵循此编码使用 Unity、 Visual Studio 和 HoloLens 模拟器了解全息版的应用程序的基础知识的演练。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合的现实，Windows Mixed Reality、 HoloLens、 全息图，学院，教程，仿真程序
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591574"
---
>[!NOTE]
><span data-ttu-id="687e0-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="687e0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="687e0-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="687e0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="687e0-106">这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="687e0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="687e0-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="687e0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="687e0-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="687e0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="687e0-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="687e0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="687e0-110">MR 基础知识 101E:使用模拟器的完整项目</span><span class="sxs-lookup"><span data-stu-id="687e0-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="687e0-111">本教程将引导您完成在 Unity 中，用于演示在 HoloLens 包括核心 Windows Mixed Reality 功能构建的完整项目[注视](gaze.md)，[手势](gestures.md)，[语音输入](voice-input.md)，[空间声音](spatial-sound.md)并[空间映射](spatial-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="687e0-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="687e0-112">本教程需要大约 1 小时才能完成。</span><span class="sxs-lookup"><span data-stu-id="687e0-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="687e0-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="687e0-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="687e0-114">课程</span><span class="sxs-lookup"><span data-stu-id="687e0-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="687e0-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="687e0-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="687e0-116"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="687e0-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="687e0-117">MR 基础知识 101E:使用模拟器的完整项目</span><span class="sxs-lookup"><span data-stu-id="687e0-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="687e0-118">✔️</span><span class="sxs-lookup"><span data-stu-id="687e0-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="687e0-119">开始之前</span><span class="sxs-lookup"><span data-stu-id="687e0-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="687e0-120">先决条件</span><span class="sxs-lookup"><span data-stu-id="687e0-120">Prerequisites</span></span>

* <span data-ttu-id="687e0-121">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="687e0-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="687e0-122">项目文件</span><span class="sxs-lookup"><span data-stu-id="687e0-122">Project files</span></span>

* <span data-ttu-id="687e0-123">下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)所需的项目。</span><span class="sxs-lookup"><span data-stu-id="687e0-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="687e0-124"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="687e0-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="687e0-125">如果你仍然需要 Unity 5.6 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="687e0-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="687e0-126">如果你仍然需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="687e0-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="687e0-127">如果你仍然需要 Unity 5.4 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="687e0-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="687e0-128">取消存档到您的桌面或其他轻松地访问位置的文件。</span><span class="sxs-lookup"><span data-stu-id="687e0-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="687e0-129">保留文件夹名称作为**Origami**。</span><span class="sxs-lookup"><span data-stu-id="687e0-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="687e0-130">如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)。</span><span class="sxs-lookup"><span data-stu-id="687e0-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="687e0-131">第 1 章-"Holo"世界</span><span class="sxs-lookup"><span data-stu-id="687e0-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="687e0-132">在本章中，我们将安装我们的第一个 Unity 项目并单步执行生成和部署过程。</span><span class="sxs-lookup"><span data-stu-id="687e0-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="687e0-133">目标</span><span class="sxs-lookup"><span data-stu-id="687e0-133">Objectives</span></span>

* <span data-ttu-id="687e0-134">为 holographic 开发设置 Unity。</span><span class="sxs-lookup"><span data-stu-id="687e0-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="687e0-135">请一张全息图。</span><span class="sxs-lookup"><span data-stu-id="687e0-135">Make a hologram.</span></span>
* <span data-ttu-id="687e0-136">所做的一张全息图，请参阅。</span><span class="sxs-lookup"><span data-stu-id="687e0-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="687e0-137">说明</span><span class="sxs-lookup"><span data-stu-id="687e0-137">Instructions</span></span>

* <span data-ttu-id="687e0-138">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="687e0-138">Start Unity.</span></span>
* <span data-ttu-id="687e0-139">选择**打开**。</span><span class="sxs-lookup"><span data-stu-id="687e0-139">Select **Open**.</span></span>
* <span data-ttu-id="687e0-140">输入与位置**Origami**文件夹你之前未存档。</span><span class="sxs-lookup"><span data-stu-id="687e0-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="687e0-141">选择**Origami**然后单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="687e0-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="687e0-142">保存新的场景：**文件** / **另存为场景**。</span><span class="sxs-lookup"><span data-stu-id="687e0-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="687e0-143">命名该场景**Origami**然后按**保存**按钮。</span><span class="sxs-lookup"><span data-stu-id="687e0-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="687e0-144">安装程序主照相机</span><span class="sxs-lookup"><span data-stu-id="687e0-144">Setup the main camera</span></span>

* <span data-ttu-id="687e0-145">在中**层次结构面板**，选择**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="687e0-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="687e0-146">在中**Inspector**将其转换位置设置为**0,0,0**。</span><span class="sxs-lookup"><span data-stu-id="687e0-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="687e0-147">查找**清除标志**属性，并将更改从下拉列表中**Skybox**到**纯色**。</span><span class="sxs-lookup"><span data-stu-id="687e0-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="687e0-148">单击**背景**字段以打开颜色选取器。</span><span class="sxs-lookup"><span data-stu-id="687e0-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="687e0-149">设置**R、 G、 B 和 A**到**0**。</span><span class="sxs-lookup"><span data-stu-id="687e0-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="687e0-150">设置场景</span><span class="sxs-lookup"><span data-stu-id="687e0-150">Setup the scene</span></span>

* <span data-ttu-id="687e0-151">在中**层次结构面板**，单击**创建**并**创建空白**。</span><span class="sxs-lookup"><span data-stu-id="687e0-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="687e0-152">右键单击新**GameObject**和选择重命名。</span><span class="sxs-lookup"><span data-stu-id="687e0-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="687e0-153">重命名为 GameObject **OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="687e0-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="687e0-154">从**全息**中的文件夹**项目面板**:</span><span class="sxs-lookup"><span data-stu-id="687e0-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="687e0-155">拖动**阶段**到层次结构的子级**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="687e0-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="687e0-156">拖动**Sphere1**到层次结构的子级**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="687e0-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="687e0-157">拖动**Sphere2**到层次结构的子级**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="687e0-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="687e0-158">右键单击**定向光**对象中**层次结构面板**，然后选择**删除**。</span><span class="sxs-lookup"><span data-stu-id="687e0-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="687e0-159">从**全息**文件夹中，拖动**灯**到的根目录**层次结构面板**。</span><span class="sxs-lookup"><span data-stu-id="687e0-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="687e0-160">在中**层次结构**，选择**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="687e0-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="687e0-161">在中**Inspector**，将转换位置设置为**0、-0.5、 2.0**。</span><span class="sxs-lookup"><span data-stu-id="687e0-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="687e0-162">按**播放**在 Unity 中以预览你全息按钮。</span><span class="sxs-lookup"><span data-stu-id="687e0-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="687e0-163">您应看到预览窗口中的 Origami 对象。</span><span class="sxs-lookup"><span data-stu-id="687e0-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="687e0-164">按**播放**停止预览模式下的第二个时机。</span><span class="sxs-lookup"><span data-stu-id="687e0-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="687e0-165">导出到 Visual Studio 从 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="687e0-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="687e0-166">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="687e0-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="687e0-167">选择**Windows 应用商店**中**平台**列表中，单击**切换平台**。</span><span class="sxs-lookup"><span data-stu-id="687e0-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="687e0-168">设置**SDK**到**通用 10**并**生成类型**到**D3D**。</span><span class="sxs-lookup"><span data-stu-id="687e0-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="687e0-169">检查**UnityC#项目**。</span><span class="sxs-lookup"><span data-stu-id="687e0-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="687e0-170">单击**添加打开场景**添加场景。</span><span class="sxs-lookup"><span data-stu-id="687e0-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="687e0-171">单击**播放器设置...**.</span><span class="sxs-lookup"><span data-stu-id="687e0-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="687e0-172">在检查器面板中选择**Windows 应用商店徽标**。</span><span class="sxs-lookup"><span data-stu-id="687e0-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="687e0-173">然后选择**发布设置**。</span><span class="sxs-lookup"><span data-stu-id="687e0-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="687e0-174">在中**功能**部分中，选择**麦克风**并**SpatialPerception**功能。</span><span class="sxs-lookup"><span data-stu-id="687e0-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="687e0-175">在生成设置窗口中，单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="687e0-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="687e0-176">创建**新文件夹**名为"应用"。</span><span class="sxs-lookup"><span data-stu-id="687e0-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="687e0-177">单击一下**应用程序文件夹**。</span><span class="sxs-lookup"><span data-stu-id="687e0-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="687e0-178">按**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="687e0-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="687e0-179">Unity 完成操作后，将出现一个文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="687e0-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="687e0-180">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="687e0-180">Open the **App** folder.</span></span>
* <span data-ttu-id="687e0-181">打开**Origami Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="687e0-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="687e0-182">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **X86**。</span><span class="sxs-lookup"><span data-stu-id="687e0-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="687e0-183">单击设备按钮旁边的箭头，然后选择**HoloLens 模拟器**。</span><span class="sxs-lookup"><span data-stu-id="687e0-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="687e0-184">单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="687e0-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="687e0-185">一段时间后在仿真程序将 Origami 项目开始。</span><span class="sxs-lookup"><span data-stu-id="687e0-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="687e0-186">首次启动时[仿真程序](using-the-hololens-emulator.md)，可能需要长达 15 分钟的时间可以启动仿真程序。</span><span class="sxs-lookup"><span data-stu-id="687e0-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="687e0-187">它一次启动时，不要将其关闭。</span><span class="sxs-lookup"><span data-stu-id="687e0-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="687e0-188">第 2 章-的视线移动</span><span class="sxs-lookup"><span data-stu-id="687e0-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="687e0-189">在本章中，我们将推出的三种方式进行交互的第一个与你全息-[注视](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="687e0-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="687e0-190">目标</span><span class="sxs-lookup"><span data-stu-id="687e0-190">Objectives</span></span>

* <span data-ttu-id="687e0-191">可视化你的视线移动使用 world 锁定的游标。</span><span class="sxs-lookup"><span data-stu-id="687e0-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="687e0-192">说明</span><span class="sxs-lookup"><span data-stu-id="687e0-192">Instructions</span></span>

* <span data-ttu-id="687e0-193">返回到你的 Unity 项目，并关闭生成设置窗口中，如果它仍处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="687e0-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="687e0-194">选择**全息**中的文件夹**项目面板**。</span><span class="sxs-lookup"><span data-stu-id="687e0-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="687e0-195">拖动**游标**对象插入**层次结构面板**根级别。</span><span class="sxs-lookup"><span data-stu-id="687e0-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="687e0-196">双击**游标**对象，若要更详细地介绍它。</span><span class="sxs-lookup"><span data-stu-id="687e0-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="687e0-197">右键单击**脚本**项目面板中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="687e0-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="687e0-198">单击**创建**子菜单。</span><span class="sxs-lookup"><span data-stu-id="687e0-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="687e0-199">选择**C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="687e0-199">Select **C# Script**.</span></span>
* <span data-ttu-id="687e0-200">脚本命名为**WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="687e0-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="687e0-201">注意：该名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="687e0-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="687e0-202">不需要添加.cs 扩展名。</span><span class="sxs-lookup"><span data-stu-id="687e0-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="687e0-203">选择**游标**对象中**层次结构面板**。</span><span class="sxs-lookup"><span data-stu-id="687e0-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="687e0-204">拖放到**WorldCursor**脚本**检查器面板**。</span><span class="sxs-lookup"><span data-stu-id="687e0-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="687e0-205">双击**WorldCursor**脚本以在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="687e0-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="687e0-206">为此代码复制并粘贴**WorldCursor.cs**并**全部保存**。</span><span class="sxs-lookup"><span data-stu-id="687e0-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="687e0-207">重新生成该应用程序从**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="687e0-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="687e0-208">返回到之前用于将部署到仿真程序的 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="687e0-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="687e0-209">选择全部重新加载出现提示时。</span><span class="sxs-lookup"><span data-stu-id="687e0-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="687e0-210">单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="687e0-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="687e0-211">使用 Xbox 控制器在场景周围查找。</span><span class="sxs-lookup"><span data-stu-id="687e0-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="687e0-212">请注意光标是如何与对象的形状交互。</span><span class="sxs-lookup"><span data-stu-id="687e0-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="687e0-213">第 3 章-手势</span><span class="sxs-lookup"><span data-stu-id="687e0-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="687e0-214">在本章中，我们将添加对的支持[手势](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="687e0-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="687e0-215">当用户选择纸张球体时，我们将使处于开启使用 Unity 的物理引擎的重力球体。</span><span class="sxs-lookup"><span data-stu-id="687e0-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="687e0-216">目标</span><span class="sxs-lookup"><span data-stu-id="687e0-216">Objectives</span></span>

* <span data-ttu-id="687e0-217">控制你全息与选择的笔势。</span><span class="sxs-lookup"><span data-stu-id="687e0-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="687e0-218">说明</span><span class="sxs-lookup"><span data-stu-id="687e0-218">Instructions</span></span>

<span data-ttu-id="687e0-219">我们将首先创建一个脚本，不是可以检测到选择手势。</span><span class="sxs-lookup"><span data-stu-id="687e0-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="687e0-220">在中**脚本**文件夹中，创建一个名为脚本**GazeGestureManager**。</span><span class="sxs-lookup"><span data-stu-id="687e0-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="687e0-221">拖动**GazeGestureManager**拖动到脚本**OrigamiCollection**层次结构中的对象。</span><span class="sxs-lookup"><span data-stu-id="687e0-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="687e0-222">打开**GazeGestureManager** Visual Studio 中编写脚本，并添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="687e0-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="687e0-223">在脚本文件夹中名为这次创建另一个脚本**SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="687e0-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="687e0-224">展开**OrigamiCollection**层次结构视图中的对象。</span><span class="sxs-lookup"><span data-stu-id="687e0-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="687e0-225">拖动**SphereCommands**拖动到脚本**Sphere1**层次结构面板中的对象。</span><span class="sxs-lookup"><span data-stu-id="687e0-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="687e0-226">拖动**SphereCommands**拖动到脚本**Sphere2**层次结构面板中的对象。</span><span class="sxs-lookup"><span data-stu-id="687e0-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="687e0-227">在 Visual Studio 中打开脚本进行编辑，并将默认代码替换此为：</span><span class="sxs-lookup"><span data-stu-id="687e0-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="687e0-228">导出、 生成和应用部署到 HoloLens 仿真程序。</span><span class="sxs-lookup"><span data-stu-id="687e0-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="687e0-229">查找在场景周围和一个球体上居中对齐。</span><span class="sxs-lookup"><span data-stu-id="687e0-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="687e0-230">按**A** Xbox 控制器上的按钮或按空格键以模拟选择手势。</span><span class="sxs-lookup"><span data-stu-id="687e0-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="687e0-231">第 4 章-语音</span><span class="sxs-lookup"><span data-stu-id="687e0-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="687e0-232">在本章中，我们将添加两个支持[语音命令](voice-input.md):"重置的 world"到返回到其原始位置删除的球体和"Drop 球体"以使处于球体。</span><span class="sxs-lookup"><span data-stu-id="687e0-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="687e0-233">目标</span><span class="sxs-lookup"><span data-stu-id="687e0-233">Objectives</span></span>

* <span data-ttu-id="687e0-234">在背景中添加始终侦听语音命令。</span><span class="sxs-lookup"><span data-stu-id="687e0-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="687e0-235">创建一张全息图，待语音命令做出反应。</span><span class="sxs-lookup"><span data-stu-id="687e0-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="687e0-236">说明</span><span class="sxs-lookup"><span data-stu-id="687e0-236">Instructions</span></span>

* <span data-ttu-id="687e0-237">在中**脚本**文件夹中，创建一个名为脚本**SpeechManager**。</span><span class="sxs-lookup"><span data-stu-id="687e0-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="687e0-238">拖动**SpeechManager**拖动到脚本**OrigamiCollection**层次结构中的对象</span><span class="sxs-lookup"><span data-stu-id="687e0-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="687e0-239">打开**SpeechManager** Visual Studio 中的脚本。</span><span class="sxs-lookup"><span data-stu-id="687e0-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="687e0-240">为此代码复制并粘贴**SpeechManager.cs**并**全部保存**:</span><span class="sxs-lookup"><span data-stu-id="687e0-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="687e0-241">打开**SphereCommands** Visual Studio 中的脚本。</span><span class="sxs-lookup"><span data-stu-id="687e0-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="687e0-242">更新脚本，以读取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="687e0-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="687e0-243">导出、 生成和应用部署到 HoloLens 仿真程序。</span><span class="sxs-lookup"><span data-stu-id="687e0-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="687e0-244">在仿真程序将支持你的电脑的麦克风和语音响应： 调整此视图，使光标位于一个球体上, 并说"Drop Sphere"。</span><span class="sxs-lookup"><span data-stu-id="687e0-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="687e0-245">说"**重置世界**"将恢复到其初始位置。</span><span class="sxs-lookup"><span data-stu-id="687e0-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="687e0-246">第 5 章-空间声音</span><span class="sxs-lookup"><span data-stu-id="687e0-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="687e0-247">在本章中，我们将将音乐添加到应用程序中，然后触发特定操作的声音效果。</span><span class="sxs-lookup"><span data-stu-id="687e0-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="687e0-248">我们将使用[空间声音](spatial-sound.md)以便声音 3D 空间中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="687e0-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="687e0-249">目标</span><span class="sxs-lookup"><span data-stu-id="687e0-249">Objectives</span></span>

* <span data-ttu-id="687e0-250">听到全息在您的世界。</span><span class="sxs-lookup"><span data-stu-id="687e0-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="687e0-251">说明</span><span class="sxs-lookup"><span data-stu-id="687e0-251">Instructions</span></span>

* <span data-ttu-id="687e0-252">在顶部菜单中，Unity 选择**编辑 > 项目设置 > 音频**</span><span class="sxs-lookup"><span data-stu-id="687e0-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="687e0-253">查找**Spatializer 插件**设置并选择**MS HRTF Spatializer**。</span><span class="sxs-lookup"><span data-stu-id="687e0-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="687e0-254">从**全息**文件夹中，拖动**环境**对象拖到**OrigamiCollection**层次结构面板中的对象。</span><span class="sxs-lookup"><span data-stu-id="687e0-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="687e0-255">选择**OrigamiCollection**并找到**音频源**组件。</span><span class="sxs-lookup"><span data-stu-id="687e0-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="687e0-256">更改这些属性：</span><span class="sxs-lookup"><span data-stu-id="687e0-256">Change these properties:</span></span>
  * <span data-ttu-id="687e0-257">检查**Spatialize**属性。</span><span class="sxs-lookup"><span data-stu-id="687e0-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="687e0-258">检查**唤醒状态上播放**。</span><span class="sxs-lookup"><span data-stu-id="687e0-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="687e0-259">更改**空间 Blend**到**3D**通过将滑块拖到最右侧。</span><span class="sxs-lookup"><span data-stu-id="687e0-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="687e0-260">检查**循环**属性。</span><span class="sxs-lookup"><span data-stu-id="687e0-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="687e0-261">展开**3D 声音设置**，并输入**0.1**有关**Doppler 级别**。</span><span class="sxs-lookup"><span data-stu-id="687e0-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="687e0-262">设置**卷卷绕**到**对数卷绕**。</span><span class="sxs-lookup"><span data-stu-id="687e0-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="687e0-263">设置**最大距离**到**20**。</span><span class="sxs-lookup"><span data-stu-id="687e0-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="687e0-264">在中**脚本**文件夹中，创建一个名为脚本**SphereSounds**。</span><span class="sxs-lookup"><span data-stu-id="687e0-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="687e0-265">拖动**SphereSounds**到**Sphere1**并**Sphere2**层次结构中的对象。</span><span class="sxs-lookup"><span data-stu-id="687e0-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="687e0-266">打开**SphereSounds** Visual Studio 中更新以下代码，并**全部保存**。</span><span class="sxs-lookup"><span data-stu-id="687e0-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="687e0-267">保存脚本，并返回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="687e0-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="687e0-268">导出、 生成和应用部署到 HoloLens 仿真程序。</span><span class="sxs-lookup"><span data-stu-id="687e0-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="687e0-269">带上耳机以获取完整的效果，并移动更接近和最荒谬不过要听到的声音更改的阶段。</span><span class="sxs-lookup"><span data-stu-id="687e0-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="687e0-270">第 6 章-空间映射</span><span class="sxs-lookup"><span data-stu-id="687e0-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="687e0-271">现在，我们将使用[空间映射](spatial-mapping.md)在现实世界中的实际对象上放置游戏板。</span><span class="sxs-lookup"><span data-stu-id="687e0-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="687e0-272">目标</span><span class="sxs-lookup"><span data-stu-id="687e0-272">Objectives</span></span>

* <span data-ttu-id="687e0-273">将引入虚拟世界的现实世界。</span><span class="sxs-lookup"><span data-stu-id="687e0-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="687e0-274">将放置在全息其中它们对你最重要。</span><span class="sxs-lookup"><span data-stu-id="687e0-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="687e0-275">说明</span><span class="sxs-lookup"><span data-stu-id="687e0-275">Instructions</span></span>

* <span data-ttu-id="687e0-276">单击**全息**项目面板中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="687e0-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="687e0-277">拖动**空间映射**到的根目录的资产**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="687e0-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="687e0-278">单击**空间映射**层次结构中的对象。</span><span class="sxs-lookup"><span data-stu-id="687e0-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="687e0-279">在中**检查器面板**，更改下列属性：</span><span class="sxs-lookup"><span data-stu-id="687e0-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="687e0-280">检查**绘制 Visual 网格**框。</span><span class="sxs-lookup"><span data-stu-id="687e0-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="687e0-281">找到**绘制材料**并单击右侧的圆形。</span><span class="sxs-lookup"><span data-stu-id="687e0-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="687e0-282">类型"**线框**"顶部搜索字段中。</span><span class="sxs-lookup"><span data-stu-id="687e0-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="687e0-283">单击该结果，然后关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="687e0-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="687e0-284">导出、 生成和应用部署到 HoloLens 仿真程序。</span><span class="sxs-lookup"><span data-stu-id="687e0-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="687e0-285">应用运行时，将在线框中呈现之前已扫描的实际起居室的网格。</span><span class="sxs-lookup"><span data-stu-id="687e0-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="687e0-286">观看如何滚动球体将不会出现该阶段，注销再到在地板上 ！</span><span class="sxs-lookup"><span data-stu-id="687e0-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="687e0-287">现在我们将向您展示如何将 OrigamiCollection 移动到新位置：</span><span class="sxs-lookup"><span data-stu-id="687e0-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="687e0-288">在中**脚本**文件夹中，创建一个名为脚本**TapToPlaceParent**。</span><span class="sxs-lookup"><span data-stu-id="687e0-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="687e0-289">在中**层次结构**，展开**OrigamiCollection** ，然后选择**阶段**对象。</span><span class="sxs-lookup"><span data-stu-id="687e0-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="687e0-290">拖动**TapToPlaceParent**到阶段对象上的脚本。</span><span class="sxs-lookup"><span data-stu-id="687e0-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="687e0-291">打开**TapToPlaceParent**脚本在 Visual Studio 中，并将其更新为如下：</span><span class="sxs-lookup"><span data-stu-id="687e0-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="687e0-292">导出、 生成和部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="687e0-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="687e0-293">现在，您现在应能够通过它在观望在特定位置放游戏，使用选择手势 (**A**键或空格键) 然后将移至新位置，并再次使用选择的手势。</span><span class="sxs-lookup"><span data-stu-id="687e0-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="687e0-294">结束</span><span class="sxs-lookup"><span data-stu-id="687e0-294">The end</span></span>

<span data-ttu-id="687e0-295">就是本教程结束 ！</span><span class="sxs-lookup"><span data-stu-id="687e0-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="687e0-296">介绍了：</span><span class="sxs-lookup"><span data-stu-id="687e0-296">You learned:</span></span>

* <span data-ttu-id="687e0-297">如何在 Unity 中创建全息版应用。</span><span class="sxs-lookup"><span data-stu-id="687e0-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="687e0-298">如何使提供注视、 手势、 语音、 声音和空间映射的使用。</span><span class="sxs-lookup"><span data-stu-id="687e0-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="687e0-299">如何生成和使用 Visual Studio 部署应用。</span><span class="sxs-lookup"><span data-stu-id="687e0-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="687e0-300">现已准备好开始创建您自己全息版的应用 ！</span><span class="sxs-lookup"><span data-stu-id="687e0-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="687e0-301">请参阅</span><span class="sxs-lookup"><span data-stu-id="687e0-301">See also</span></span>

* [<span data-ttu-id="687e0-302">MR 基础知识 101:与设备的完整项目</span><span class="sxs-lookup"><span data-stu-id="687e0-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="687e0-303">Gaze</span><span class="sxs-lookup"><span data-stu-id="687e0-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="687e0-304">手势</span><span class="sxs-lookup"><span data-stu-id="687e0-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="687e0-305">语音输入</span><span class="sxs-lookup"><span data-stu-id="687e0-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="687e0-306">空间声音</span><span class="sxs-lookup"><span data-stu-id="687e0-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="687e0-307">空间映射</span><span class="sxs-lookup"><span data-stu-id="687e0-307">Spatial mapping</span></span>](spatial-mapping.md)
