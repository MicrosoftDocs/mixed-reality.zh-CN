---
title: MR 基本 101-设备的完整项目
description: 按照此编码演练操作，使用 Unity、Visual Studio 和 HoloLens 了解 Windows Mixed Reality 的基本知识。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实，Windows Mixed Reality，HoloLens，全息影像，学院，教程
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434718"
---
>[!NOTE]
><span data-ttu-id="b0d66-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="b0d66-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b0d66-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="b0d66-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b0d66-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="b0d66-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b0d66-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="b0d66-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b0d66-108">为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d66-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="b0d66-109">MR 基本101：通过设备完成项目</span><span class="sxs-lookup"><span data-stu-id="b0d66-109">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="b0d66-110">本教程将引导你完成 Unity 中内置的一个完整项目，该项目演示了 HoloLens 上核心 Windows Mixed Reality 功能，包括[注视](gaze-and-commit.md)、[手势](gaze-and-commit.md#composite-gestures)、[语音输入](voice-input.md)、[空间音效](spatial-sound.md)和[空间映射](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="b0d66-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="b0d66-111">教程大约需要1小时才能完成。</span><span class="sxs-lookup"><span data-stu-id="b0d66-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="b0d66-112">设备支持</span><span class="sxs-lookup"><span data-stu-id="b0d66-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b0d66-113">摘要</span><span class="sxs-lookup"><span data-stu-id="b0d66-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b0d66-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b0d66-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b0d66-115"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="b0d66-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b0d66-116">MR 基本101：通过设备完成项目</span><span class="sxs-lookup"><span data-stu-id="b0d66-116">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="b0d66-117">✔️</span><span class="sxs-lookup"><span data-stu-id="b0d66-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="b0d66-118">开始之前</span><span class="sxs-lookup"><span data-stu-id="b0d66-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b0d66-119">必备条件</span><span class="sxs-lookup"><span data-stu-id="b0d66-119">Prerequisites</span></span>

* <span data-ttu-id="b0d66-120">配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="b0d66-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="b0d66-121">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="b0d66-121">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="b0d66-122">项目文件</span><span class="sxs-lookup"><span data-stu-id="b0d66-122">Project files</span></span>

* <span data-ttu-id="b0d66-123">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="b0d66-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="b0d66-124"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="b0d66-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="b0d66-125">如果仍需要 Unity 5.6 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="b0d66-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="b0d66-126">如果仍需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="b0d66-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="b0d66-127">如果仍需要 Unity 5.4 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="b0d66-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="b0d66-128">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="b0d66-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="b0d66-129">将文件夹名称保留为**日式折纸**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="b0d66-130">如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)找到。</span><span class="sxs-lookup"><span data-stu-id="b0d66-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="b0d66-131">第1章-"Holo" 世界</span><span class="sxs-lookup"><span data-stu-id="b0d66-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="b0d66-132">在本章中，我们将设置第一个 Unity 项目，并逐步完成生成和部署过程。</span><span class="sxs-lookup"><span data-stu-id="b0d66-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0d66-133">目标</span><span class="sxs-lookup"><span data-stu-id="b0d66-133">Objectives</span></span>

* <span data-ttu-id="b0d66-134">为全息版开发设置 Unity。</span><span class="sxs-lookup"><span data-stu-id="b0d66-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="b0d66-135">制作全息影像。</span><span class="sxs-lookup"><span data-stu-id="b0d66-135">Make a hologram.</span></span>
* <span data-ttu-id="b0d66-136">查看您创建的全息影像。</span><span class="sxs-lookup"><span data-stu-id="b0d66-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0d66-137">说明</span><span class="sxs-lookup"><span data-stu-id="b0d66-137">Instructions</span></span>

* <span data-ttu-id="b0d66-138">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="b0d66-138">Start Unity.</span></span>
* <span data-ttu-id="b0d66-139">选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-139">Select **Open**.</span></span>
* <span data-ttu-id="b0d66-140">输入 "位置" 作为以前未存档的**日式折纸**文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0d66-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="b0d66-141">选择 "**日式折纸**" 并单击 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="b0d66-142">由于**日式折纸**项目不包含场景，因此请使用： **File** / **将场景保存为**，将空的默认场景保存到新文件中。</span><span class="sxs-lookup"><span data-stu-id="b0d66-142">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="b0d66-143">将新场景命名为**日式折纸**，并按 "**保存**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="b0d66-143">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="b0d66-144">设置主虚拟摄像机</span><span class="sxs-lookup"><span data-stu-id="b0d66-144">Setup the main virtual camera</span></span>

* <span data-ttu-id="b0d66-145">在 "**层次结构" 面板**中，选择 "**主相机**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="b0d66-146">**检查器**将其转换位置设置为**0，0，0**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="b0d66-147">找到 "**清除标志**" 属性，然后将下拉列表中的**Skybox**更改为**纯色**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="b0d66-148">单击 "**背景**" 字段打开颜色选取器。</span><span class="sxs-lookup"><span data-stu-id="b0d66-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="b0d66-149">将**R、G、B 和 A**设置为**0**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="b0d66-150">设置场景</span><span class="sxs-lookup"><span data-stu-id="b0d66-150">Setup the scene</span></span>

* <span data-ttu-id="b0d66-151">在 "**层次结构" 面板**中，单击 "**创建**" 并**创建空**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="b0d66-152">右键单击新的 " **GameObject** "，然后选择 "重命名"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="b0d66-153">将 GameObject 重命名为**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0d66-154">从 "项目" 面板（展开 "**资产" 并**选择全息影像，或双击 "项目" 面板中的 "全息影像" 文件夹）：</span><span class="sxs-lookup"><span data-stu-id="b0d66-154">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="b0d66-155">将**阶段**拖到层次结构中，使其成为**OrigamiCollection**的子级。</span><span class="sxs-lookup"><span data-stu-id="b0d66-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="b0d66-156">将**Sphere1**拖到层次结构中，使其成为**OrigamiCollection**的子元素。</span><span class="sxs-lookup"><span data-stu-id="b0d66-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="b0d66-157">将**Sphere2**拖到层次结构中，使其成为**OrigamiCollection**的子元素。</span><span class="sxs-lookup"><span data-stu-id="b0d66-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0d66-158">右键单击 "**层次结构" 面板**中的**方向浅**对象，然后选择 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="b0d66-159">从 "**全息影像**" 文件夹中，将**灯光**拖到**层次结构面板**的根。</span><span class="sxs-lookup"><span data-stu-id="b0d66-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="b0d66-160">在**层次结构**中，选择 " **OrigamiCollection**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0d66-161">在**检查器**中，将转换位置设置为**0、-0.5、2.0**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="b0d66-162">按下 Unity 中的 "**播放**" 按钮，预览全息影像。</span><span class="sxs-lookup"><span data-stu-id="b0d66-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="b0d66-163">预览窗口中应会显示日式折纸对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="b0d66-164">按第二次**播放**以停止预览模式。</span><span class="sxs-lookup"><span data-stu-id="b0d66-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="b0d66-165">将项目从 Unity 导出到 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b0d66-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="b0d66-166">在 Unity 中，选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="b0d66-167">选择 "**平台**" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-167">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="b0d66-168">将**SDK**设置为**通用 10** ，将**类型**设置为**D3D**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="b0d66-169">检查**Unity C#项目**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="b0d66-170">单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="b0d66-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="b0d66-171">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-171">Click **Build**.</span></span>
* <span data-ttu-id="b0d66-172">在出现的 "文件资源管理器" 窗口中，创建一个名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-172">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="b0d66-173">单击**应用文件夹**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-173">Single click the **App Folder**.</span></span>
* <span data-ttu-id="b0d66-174">按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-174">Press **Select Folder**.</span></span>
* <span data-ttu-id="b0d66-175">当 Unity 完成后，将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="b0d66-175">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="b0d66-176">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0d66-176">Open the **App** folder.</span></span>
* <span data-ttu-id="b0d66-177">打开（双击） "**日式折纸**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-177">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="b0d66-178">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **X86**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="b0d66-179">单击 "设备" 按钮旁边的箭头，并选择 "**远程计算机**" 以通过 wi-fi 进行部署。</span><span class="sxs-lookup"><span data-stu-id="b0d66-179">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="b0d66-180">将**地址**设置为 HoloLens 的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="b0d66-180">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="b0d66-181">如果你不知道设备 IP 地址，请在 "设置" 中查找 " **> 网络 & Internet > 高级选项** **" 或 "我的 IP 地址是什么？"。**</span><span class="sxs-lookup"><span data-stu-id="b0d66-181">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="b0d66-182">如果 HoloLens 通过 USB 连接，则可以选择 "**设备**通过 usb 进行部署"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-182">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="b0d66-183">将**身份验证模式**设置为 "**通用**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-183">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="b0d66-184">单击 "**选择**"</span><span class="sxs-lookup"><span data-stu-id="b0d66-184">Click **Select**</span></span>

* <span data-ttu-id="b0d66-185">单击 "**调试" > "开始但不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-185">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="b0d66-186">如果这是首次部署到设备，则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="b0d66-186">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

* <span data-ttu-id="b0d66-187">现在，日式折纸项目将生成、部署到 HoloLens，然后运行。</span><span class="sxs-lookup"><span data-stu-id="b0d66-187">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="b0d66-188">放在你的 HoloLens 上，并查看你的新全息影像。</span><span class="sxs-lookup"><span data-stu-id="b0d66-188">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="b0d66-189">第2章-注视</span><span class="sxs-lookup"><span data-stu-id="b0d66-189">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="b0d66-190">在本章中，我们将介绍第三种与全息影像交互的方式--[注视](gaze-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="b0d66-190">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="b0d66-191">目标</span><span class="sxs-lookup"><span data-stu-id="b0d66-191">Objectives</span></span>

* <span data-ttu-id="b0d66-192">使用全球锁定的光标直观显示注视。</span><span class="sxs-lookup"><span data-stu-id="b0d66-192">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0d66-193">说明</span><span class="sxs-lookup"><span data-stu-id="b0d66-193">Instructions</span></span>

* <span data-ttu-id="b0d66-194">返回到 Unity 项目，并关闭 "生成设置" 窗口（如果它仍处于打开状态）。</span><span class="sxs-lookup"><span data-stu-id="b0d66-194">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="b0d66-195">在 "**项目" 面板**中选择**全息影像**文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0d66-195">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="b0d66-196">将**光标**对象拖到**层次结构面板**中的根级别。</span><span class="sxs-lookup"><span data-stu-id="b0d66-196">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="b0d66-197">双击**光标**对象以详细查看它。</span><span class="sxs-lookup"><span data-stu-id="b0d66-197">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="b0d66-198">右键单击 "项目" 面板中的 "**脚本**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0d66-198">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="b0d66-199">单击 "**创建**" 子菜单。</span><span class="sxs-lookup"><span data-stu-id="b0d66-199">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="b0d66-200">选择 **C# "脚本**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-200">Select **C# Script**.</span></span>
* <span data-ttu-id="b0d66-201">将脚本命名为**WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-201">Name the script **WorldCursor**.</span></span> <span data-ttu-id="b0d66-202">注意：名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b0d66-202">Note: The name is case-sensitive.</span></span> <span data-ttu-id="b0d66-203">无需添加 .cs 扩展名。</span><span class="sxs-lookup"><span data-stu-id="b0d66-203">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="b0d66-204">选择 "**层次结构" 面板**中的**光标**对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-204">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="b0d66-205">将**WorldCursor**脚本拖放到**检查器面板**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-205">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="b0d66-206">双击**WorldCursor**脚本，在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="b0d66-206">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="b0d66-207">将此代码复制并粘贴到**WorldCursor.cs** ，并**保存全部**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-207">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move the cursor to the point where the raycast hit.
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

* <span data-ttu-id="b0d66-208">从**文件 > 生成设置**重新生成应用。</span><span class="sxs-lookup"><span data-stu-id="b0d66-208">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="b0d66-209">返回到以前用于部署到 HoloLens 的 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="b0d66-209">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="b0d66-210">出现提示时，选择 "全部重新加载"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-210">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="b0d66-211">单击 "**调试-> 启动但不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-211">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="b0d66-212">现在，浏览场景并注意光标如何与对象的形状交互。</span><span class="sxs-lookup"><span data-stu-id="b0d66-212">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="b0d66-213">第3章-手势</span><span class="sxs-lookup"><span data-stu-id="b0d66-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="b0d66-214">在本章中，我们将添加对[手势](gaze-and-commit.md#composite-gestures)的支持。</span><span class="sxs-lookup"><span data-stu-id="b0d66-214">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="b0d66-215">当用户选择某一回形针时，我们将使用 Unity 的物理引擎开启重心来使球落在一起。</span><span class="sxs-lookup"><span data-stu-id="b0d66-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0d66-216">目标</span><span class="sxs-lookup"><span data-stu-id="b0d66-216">Objectives</span></span>

* <span data-ttu-id="b0d66-217">用选择手势控制全息影像。</span><span class="sxs-lookup"><span data-stu-id="b0d66-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0d66-218">说明</span><span class="sxs-lookup"><span data-stu-id="b0d66-218">Instructions</span></span>

<span data-ttu-id="b0d66-219">首先，我们将创建一个脚本，然后可以检测选择的手势。</span><span class="sxs-lookup"><span data-stu-id="b0d66-219">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="b0d66-220">在 "**脚本**" 文件夹中，创建一个名为**GazeGestureManager**的脚本。</span><span class="sxs-lookup"><span data-stu-id="b0d66-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="b0d66-221">将**GazeGestureManager**脚本拖到层次结构中的**OrigamiCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="b0d66-222">在 Visual Studio 中打开**GazeGestureManager**脚本，并添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="b0d66-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Awake()
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

* <span data-ttu-id="b0d66-223">在 Scripts 文件夹中创建另一个脚本，这一次名为**SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="b0d66-224">展开层次结构视图中的**OrigamiCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="b0d66-225">将**SphereCommands**脚本拖到 "层次结构" 面板中的 " **Sphere1** " 对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="b0d66-226">将**SphereCommands**脚本拖到 "层次结构" 面板中的 " **Sphere2** " 对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="b0d66-227">在 Visual Studio 中打开脚本进行编辑，并将默认代码替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="b0d66-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="b0d66-228">导出应用，生成应用并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b0d66-228">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b0d66-229">查看球之一。</span><span class="sxs-lookup"><span data-stu-id="b0d66-229">Look at one of the spheres.</span></span>
* <span data-ttu-id="b0d66-230">执行 "选择手势" 并观看以下图面上的球。</span><span class="sxs-lookup"><span data-stu-id="b0d66-230">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="b0d66-231">第4章-语音</span><span class="sxs-lookup"><span data-stu-id="b0d66-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="b0d66-232">在本章中，我们将添加对两个[声音命令](voice-input.md)的支持： "重置世界"，将已删除的球返回到其原始位置，并将 "丢球" 设置为球落。</span><span class="sxs-lookup"><span data-stu-id="b0d66-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0d66-233">目标</span><span class="sxs-lookup"><span data-stu-id="b0d66-233">Objectives</span></span>

* <span data-ttu-id="b0d66-234">添加始终在后台侦听的语音命令。</span><span class="sxs-lookup"><span data-stu-id="b0d66-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="b0d66-235">创建可响应语音命令的全息图。</span><span class="sxs-lookup"><span data-stu-id="b0d66-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0d66-236">说明</span><span class="sxs-lookup"><span data-stu-id="b0d66-236">Instructions</span></span>

* <span data-ttu-id="b0d66-237">在 "**脚本**" 文件夹中，创建一个名为**SpeechManager**的脚本。</span><span class="sxs-lookup"><span data-stu-id="b0d66-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="b0d66-238">将**SpeechManager**脚本拖到层次结构中的**OrigamiCollection**对象上</span><span class="sxs-lookup"><span data-stu-id="b0d66-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="b0d66-239">在 Visual Studio 中打开**SpeechManager**脚本。</span><span class="sxs-lookup"><span data-stu-id="b0d66-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="b0d66-240">将此代码复制并粘贴到**SpeechManager.cs** ，并**保存全部**内容：</span><span class="sxs-lookup"><span data-stu-id="b0d66-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="b0d66-241">在 Visual Studio 中打开**SphereCommands**脚本。</span><span class="sxs-lookup"><span data-stu-id="b0d66-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="b0d66-242">按如下所示更新脚本以进行读取：</span><span class="sxs-lookup"><span data-stu-id="b0d66-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="b0d66-243">导出应用，生成应用并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b0d66-243">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b0d66-244">查看某一球，说 "**击落球**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-244">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="b0d66-245">说 "**重置世界**"，将其返回到其初始位置。</span><span class="sxs-lookup"><span data-stu-id="b0d66-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="b0d66-246">第5章-空间音效</span><span class="sxs-lookup"><span data-stu-id="b0d66-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="b0d66-247">在本章中，我们将向应用程序添加音乐，并触发对某些操作的声音影响。</span><span class="sxs-lookup"><span data-stu-id="b0d66-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="b0d66-248">我们将使用[空间音效](spatial-sound.md)为声音指定3d 空间中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="b0d66-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0d66-249">目标</span><span class="sxs-lookup"><span data-stu-id="b0d66-249">Objectives</span></span>

* <span data-ttu-id="b0d66-250">收听世界上的全息影像。</span><span class="sxs-lookup"><span data-stu-id="b0d66-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0d66-251">说明</span><span class="sxs-lookup"><span data-stu-id="b0d66-251">Instructions</span></span>

* <span data-ttu-id="b0d66-252">在 Unity 中从顶部菜单中选择 "**编辑 > 项目设置 > 音频**"</span><span class="sxs-lookup"><span data-stu-id="b0d66-252">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="b0d66-253">在右侧的检查器面板中，找到 " **Spatializer" 插件**设置，然后选择 " **MS HRTF Spatializer**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-253">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="b0d66-254">在 "项目" 面板中，**将 "** **环境**" 对象拖到 "层次结构" 面板中的**OrigamiCollection**对象上。</span><span class="sxs-lookup"><span data-stu-id="b0d66-254">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="b0d66-255">选择**OrigamiCollection**并在 "检查器" 面板中查找**音频源**组件。</span><span class="sxs-lookup"><span data-stu-id="b0d66-255">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="b0d66-256">更改这些属性：</span><span class="sxs-lookup"><span data-stu-id="b0d66-256">Change these properties:</span></span>
  * <span data-ttu-id="b0d66-257">检查**Spatialize**属性。</span><span class="sxs-lookup"><span data-stu-id="b0d66-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="b0d66-258">选中 "**在唤醒状态播放**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="b0d66-259">通过将滑块一直拖到右侧，将**空间混合**更改为**三维**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="b0d66-260">移动滑块时，值应从0更改为1。</span><span class="sxs-lookup"><span data-stu-id="b0d66-260">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="b0d66-261">检查**循环**属性。</span><span class="sxs-lookup"><span data-stu-id="b0d66-261">Check the **Loop** property.</span></span>
  * <span data-ttu-id="b0d66-262">展开 "**三维声音设置**"，然后为 " **Doppler" 级别**输入**0.1** 。</span><span class="sxs-lookup"><span data-stu-id="b0d66-262">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="b0d66-263">将**Volume Rolloff**设置为**对数 Rolloff**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-263">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="b0d66-264">将**最大距离**设置为**20**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-264">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="b0d66-265">在 "**脚本**" 文件夹中，创建一个名为**SphereSounds**的脚本。</span><span class="sxs-lookup"><span data-stu-id="b0d66-265">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="b0d66-266">将**SphereSounds**拖放到层次结构中的**Sphere1**和**Sphere2**对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-266">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="b0d66-267">在 Visual Studio 中打开**SphereSounds** ，更新以下代码并**全部保存**。</span><span class="sxs-lookup"><span data-stu-id="b0d66-267">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="b0d66-268">保存该脚本并返回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="b0d66-268">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="b0d66-269">导出应用，生成应用并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b0d66-269">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b0d66-270">从舞台更近和更密切地移动，并翻到一边，倾听声音发生变化。</span><span class="sxs-lookup"><span data-stu-id="b0d66-270">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="b0d66-271">第6章-空间映射</span><span class="sxs-lookup"><span data-stu-id="b0d66-271">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="b0d66-272">现在，我们将使用[空间映射](spatial-mapping.md)将游戏板置于真实世界的真实对象上。</span><span class="sxs-lookup"><span data-stu-id="b0d66-272">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0d66-273">目标</span><span class="sxs-lookup"><span data-stu-id="b0d66-273">Objectives</span></span>

* <span data-ttu-id="b0d66-274">将你的真实世界带入虚拟世界。</span><span class="sxs-lookup"><span data-stu-id="b0d66-274">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="b0d66-275">将全息影像置于最重要的位置。</span><span class="sxs-lookup"><span data-stu-id="b0d66-275">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0d66-276">说明</span><span class="sxs-lookup"><span data-stu-id="b0d66-276">Instructions</span></span>

* <span data-ttu-id="b0d66-277">在 Unity 中，在 "项目" 面板中单击 "**全息影像**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0d66-277">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="b0d66-278">将**空间映射**资产拖到**层次结构**的根。</span><span class="sxs-lookup"><span data-stu-id="b0d66-278">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="b0d66-279">单击层次结构中的**空间映射**对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-279">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="b0d66-280">在 "**检查器" 面板**中，更改以下属性：</span><span class="sxs-lookup"><span data-stu-id="b0d66-280">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="b0d66-281">选中 "**绘制可视网格**" 框。</span><span class="sxs-lookup"><span data-stu-id="b0d66-281">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="b0d66-282">定位**绘图材料**，并单击右侧的圆圈。</span><span class="sxs-lookup"><span data-stu-id="b0d66-282">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="b0d66-283">在顶部的搜索字段中键入 "**线框**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-283">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="b0d66-284">单击结果，然后关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="b0d66-284">Click on the result and then close the window.</span></span> <span data-ttu-id="b0d66-285">执行此操作时，绘制材料的值应设置为线框。</span><span class="sxs-lookup"><span data-stu-id="b0d66-285">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="b0d66-286">导出应用，生成应用并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b0d66-286">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b0d66-287">当应用程序运行时，线框网格将覆盖你的真实世界。</span><span class="sxs-lookup"><span data-stu-id="b0d66-287">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="b0d66-288">观看某个滚动球如何偏离舞台，并观看地面！</span><span class="sxs-lookup"><span data-stu-id="b0d66-288">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="b0d66-289">现在，我们将向你展示如何将 OrigamiCollection 移动到一个新位置：</span><span class="sxs-lookup"><span data-stu-id="b0d66-289">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="b0d66-290">在 "**脚本**" 文件夹中，创建一个名为**TapToPlaceParent**的脚本。</span><span class="sxs-lookup"><span data-stu-id="b0d66-290">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="b0d66-291">在**层次结构**中，展开 " **OrigamiCollection** "，然后选择 "**暂存**" 对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-291">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="b0d66-292">将**TapToPlaceParent**脚本拖到 "暂存" 对象上。</span><span class="sxs-lookup"><span data-stu-id="b0d66-292">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="b0d66-293">在 Visual Studio 中打开**TapToPlaceParent**脚本，并将其更新为以下内容：</span><span class="sxs-lookup"><span data-stu-id="b0d66-293">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="b0d66-294">导出、生成并部署应用。</span><span class="sxs-lookup"><span data-stu-id="b0d66-294">Export, build and deploy the app.</span></span>
* <span data-ttu-id="b0d66-295">现在，您应该能够通过 gazing 将游戏置于特定位置，使用 "选择手势"，然后移动到一个新位置，然后再次使用 "选择手势"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-295">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="b0d66-296">第7章-全息娱乐</span><span class="sxs-lookup"><span data-stu-id="b0d66-296">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="b0d66-297">目标</span><span class="sxs-lookup"><span data-stu-id="b0d66-297">Objectives</span></span>

* <span data-ttu-id="b0d66-298">显示全息 underworld 的入口。</span><span class="sxs-lookup"><span data-stu-id="b0d66-298">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0d66-299">说明</span><span class="sxs-lookup"><span data-stu-id="b0d66-299">Instructions</span></span>

<span data-ttu-id="b0d66-300">接下来，我们将向您展示如何发现全息 underworld：</span><span class="sxs-lookup"><span data-stu-id="b0d66-300">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="b0d66-301">从 "项目" 面板中的 "**全息影像**" 文件夹：</span><span class="sxs-lookup"><span data-stu-id="b0d66-301">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="b0d66-302">将**Underworld**拖到层次结构中，使其成为**OrigamiCollection**的子元素。</span><span class="sxs-lookup"><span data-stu-id="b0d66-302">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0d66-303">在 "**脚本**" 文件夹中，创建一个名为**HitTarget**的脚本。</span><span class="sxs-lookup"><span data-stu-id="b0d66-303">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="b0d66-304">在**层次结构**中，展开 " **OrigamiCollection**"。</span><span class="sxs-lookup"><span data-stu-id="b0d66-304">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0d66-305">展开 "**暂存**" 对象并选择**目标**对象（蓝色风扇）。</span><span class="sxs-lookup"><span data-stu-id="b0d66-305">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="b0d66-306">将**HitTarget**脚本拖到**目标**对象上。</span><span class="sxs-lookup"><span data-stu-id="b0d66-306">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="b0d66-307">在 Visual Studio 中打开**HitTarget**脚本，并将其更新为以下内容：</span><span class="sxs-lookup"><span data-stu-id="b0d66-307">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="b0d66-308">在 Unity 中，选择**目标**对象。</span><span class="sxs-lookup"><span data-stu-id="b0d66-308">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="b0d66-309">现在，两个公共属性在**命中目标**组件上可见，需要引用场景中的对象：</span><span class="sxs-lookup"><span data-stu-id="b0d66-309">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="b0d66-310">将**Underworld**从 "**层次结构**" 面板拖到**命中目标**组件上的 " **Underworld** " 属性。</span><span class="sxs-lookup"><span data-stu-id="b0d66-310">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="b0d66-311">从 "**层次结构**" 面板将 "**阶段**" 拖到对象上，**以隐藏** **命中目标**组件的属性。</span><span class="sxs-lookup"><span data-stu-id="b0d66-311">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="b0d66-312">导出、生成并部署应用。</span><span class="sxs-lookup"><span data-stu-id="b0d66-312">Export, build and deploy the app.</span></span>
* <span data-ttu-id="b0d66-313">将日式折纸收集到地面上，然后使用 "选择手势" 创建球体放置。</span><span class="sxs-lookup"><span data-stu-id="b0d66-313">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="b0d66-314">当球到达目标（蓝色风扇）时，将发生爆炸。</span><span class="sxs-lookup"><span data-stu-id="b0d66-314">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="b0d66-315">该集合将隐藏，并且将显示 underworld 的孔。</span><span class="sxs-lookup"><span data-stu-id="b0d66-315">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="b0d66-316">结束</span><span class="sxs-lookup"><span data-stu-id="b0d66-316">The end</span></span>

<span data-ttu-id="b0d66-317">这就是本教程的结尾！</span><span class="sxs-lookup"><span data-stu-id="b0d66-317">And that's the end of this tutorial!</span></span>

<span data-ttu-id="b0d66-318">已学习：</span><span class="sxs-lookup"><span data-stu-id="b0d66-318">You learned:</span></span>

* <span data-ttu-id="b0d66-319">如何在 Unity 中创建全息应用。</span><span class="sxs-lookup"><span data-stu-id="b0d66-319">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="b0d66-320">如何使用注视、手势、语音、声音和空间映射。</span><span class="sxs-lookup"><span data-stu-id="b0d66-320">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="b0d66-321">如何使用 Visual Studio 生成和部署应用。</span><span class="sxs-lookup"><span data-stu-id="b0d66-321">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="b0d66-322">你现在已准备好开始创建自己的全息体验！</span><span class="sxs-lookup"><span data-stu-id="b0d66-322">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="b0d66-323">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0d66-323">See also</span></span>

* [<span data-ttu-id="b0d66-324">MR 基本知识101E：通过模拟器完成项目</span><span class="sxs-lookup"><span data-stu-id="b0d66-324">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="b0d66-325">凝视</span><span class="sxs-lookup"><span data-stu-id="b0d66-325">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b0d66-326">头部凝视并提交</span><span class="sxs-lookup"><span data-stu-id="b0d66-326">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b0d66-327">语音输入</span><span class="sxs-lookup"><span data-stu-id="b0d66-327">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="b0d66-328">空间音效</span><span class="sxs-lookup"><span data-stu-id="b0d66-328">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="b0d66-329">空间映射</span><span class="sxs-lookup"><span data-stu-id="b0d66-329">Spatial mapping</span></span>](spatial-mapping.md)
