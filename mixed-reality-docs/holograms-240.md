---
title: MR 共享 240-多个 HoloLens 设备
description: 按照此编码演练操作，使用 Unity、Visual Studio 和 HoloLens 了解共享全息影像的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，共享，网络，学院，教程
ms.openlocfilehash: 0d8e8f4484546d82caadf162623a6f4059eb2f00
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434563"
---
>[!NOTE]
><span data-ttu-id="28164-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="28164-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="28164-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="28164-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="28164-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="28164-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="28164-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="28164-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="28164-108">为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="28164-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="28164-109">MR 共享240：多个 HoloLens 设备</span><span class="sxs-lookup"><span data-stu-id="28164-109">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="28164-110">随着我们在空间中的发展，我们将在世界各地提供全息影像。</span><span class="sxs-lookup"><span data-stu-id="28164-110">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="28164-111">通过使用各种[坐标系统](coordinate-systems.md)跟踪对象的位置和方向，HoloLens 保留了全息影像。</span><span class="sxs-lookup"><span data-stu-id="28164-111">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="28164-112">当我们在设备之间共享这些坐标系统时，我们可以创建共享体验，使我们能够参与共享全息环境。</span><span class="sxs-lookup"><span data-stu-id="28164-112">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="28164-113">在本教程中，我们将：</span><span class="sxs-lookup"><span data-stu-id="28164-113">In this tutorial, we will:</span></span>

* <span data-ttu-id="28164-114">为共享体验设置网络。</span><span class="sxs-lookup"><span data-stu-id="28164-114">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="28164-115">跨 HoloLens 设备共享全息影像。</span><span class="sxs-lookup"><span data-stu-id="28164-115">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="28164-116">了解我们的共享全息领域中的其他人员。</span><span class="sxs-lookup"><span data-stu-id="28164-116">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="28164-117">创建可面向其他玩家的共享交互式体验，并在其上启动炮弹！</span><span class="sxs-lookup"><span data-stu-id="28164-117">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="28164-118">设备支持</span><span class="sxs-lookup"><span data-stu-id="28164-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="28164-119">摘要</span><span class="sxs-lookup"><span data-stu-id="28164-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="28164-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="28164-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="28164-121"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="28164-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="28164-122">MR 共享240：多个 HoloLens 设备</span><span class="sxs-lookup"><span data-stu-id="28164-122">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="28164-123">✔️</span><span class="sxs-lookup"><span data-stu-id="28164-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="28164-124">开始之前</span><span class="sxs-lookup"><span data-stu-id="28164-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="28164-125">必备条件</span><span class="sxs-lookup"><span data-stu-id="28164-125">Prerequisites</span></span>

* <span data-ttu-id="28164-126">使用随 Internet 访问权限安装的正确[工具](install-the-tools.md)配置的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="28164-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="28164-127">至少[为开发配置了](using-visual-studio.md#enabling-developer-mode)两个 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="28164-127">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="28164-128">项目文件</span><span class="sxs-lookup"><span data-stu-id="28164-128">Project files</span></span>

* <span data-ttu-id="28164-129">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)。</span><span class="sxs-lookup"><span data-stu-id="28164-129">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="28164-130">需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="28164-130">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="28164-131">如果仍需要 Unity 5.6 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="28164-131">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="28164-132">如果仍需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="28164-132">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="28164-133">如果仍需要 Unity 5.4 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="28164-133">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="28164-134">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="28164-134">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="28164-135">将文件夹名称保留为**SharedHolograms**。</span><span class="sxs-lookup"><span data-stu-id="28164-135">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="28164-136">如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)找到。</span><span class="sxs-lookup"><span data-stu-id="28164-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="28164-137">第1章-Holo World</span><span class="sxs-lookup"><span data-stu-id="28164-137">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="28164-138">在本章中，我们将设置第一个 Unity 项目，并逐步完成生成和部署过程。</span><span class="sxs-lookup"><span data-stu-id="28164-138">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="28164-139">目标</span><span class="sxs-lookup"><span data-stu-id="28164-139">Objectives</span></span>

* <span data-ttu-id="28164-140">安装 Unity 以开发全息版应用。</span><span class="sxs-lookup"><span data-stu-id="28164-140">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="28164-141">查看全息图！</span><span class="sxs-lookup"><span data-stu-id="28164-141">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="28164-142">说明</span><span class="sxs-lookup"><span data-stu-id="28164-142">Instructions</span></span>

* <span data-ttu-id="28164-143">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="28164-143">Start Unity.</span></span>
* <span data-ttu-id="28164-144">选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="28164-144">Select **Open**.</span></span>
* <span data-ttu-id="28164-145">输入位置作为之前 unarchived 的**SharedHolograms**文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-145">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="28164-146">选择 "**项目名称**"，然后单击 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="28164-146">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="28164-147">在**层次结构**中，右键单击**主相机**，然后选择 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="28164-147">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="28164-148">在**HoloToolkit/prototyping/相机**文件夹中，找到**摄像机的主**prefab。</span><span class="sxs-lookup"><span data-stu-id="28164-148">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="28164-149">将**主相机**拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="28164-149">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="28164-150">在**层次结构**中，单击 "**创建**" 并**创建空**。</span><span class="sxs-lookup"><span data-stu-id="28164-150">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="28164-151">右键单击新的 " **GameObject** "，然后选择 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="28164-151">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="28164-152">将 GameObject 重命名为**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="28164-152">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="28164-153">选择**层次结构**中的**HologramCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="28164-153">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="28164-154">**检查器**中，将**转换位置**设置为： **X：0，Y：-0.25，Z： 2**。</span><span class="sxs-lookup"><span data-stu-id="28164-154">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="28164-155">在 "**项目" 面板**的 "**全息影像**" 文件夹中，找到 " **EnergyHub**资产"。</span><span class="sxs-lookup"><span data-stu-id="28164-155">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="28164-156">将**EnergyHub**对象从 "**项目" 面板**中拖放到**层次结构**中，将其作为**HologramCollection 的子项**。</span><span class="sxs-lookup"><span data-stu-id="28164-156">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="28164-157">选择**文件 > 将场景另存为 ...**</span><span class="sxs-lookup"><span data-stu-id="28164-157">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="28164-158">将场景命名为**SharedHolograms** ，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="28164-158">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="28164-159">按下 Unity 中的 "**播放**" 按钮，预览全息影像。</span><span class="sxs-lookup"><span data-stu-id="28164-159">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="28164-160">按第二次**播放**以停止预览模式。</span><span class="sxs-lookup"><span data-stu-id="28164-160">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="28164-161">**将项目从 Unity 导出到 Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="28164-161">**Export the project from Unity to Visual Studio**</span></span>

* <span data-ttu-id="28164-162">在 Unity 中，选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="28164-162">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="28164-163">单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="28164-163">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="28164-164">选择 "**平台**" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**"。</span><span class="sxs-lookup"><span data-stu-id="28164-164">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="28164-165">将**SDK**设置为**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="28164-165">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="28164-166">将**目标设备**设置为**HoloLens** ，将 " **UWP" 生成类型**设置为 " **D3D**"。</span><span class="sxs-lookup"><span data-stu-id="28164-166">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="28164-167">检查**Unity C#项目**。</span><span class="sxs-lookup"><span data-stu-id="28164-167">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="28164-168">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="28164-168">Click **Build**.</span></span>
* <span data-ttu-id="28164-169">在出现的 "文件资源管理器" 窗口中，创建一个名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="28164-169">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="28164-170">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-170">Single click the **App** folder.</span></span>
* <span data-ttu-id="28164-171">按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="28164-171">Press **Select Folder**.</span></span>
* <span data-ttu-id="28164-172">当 Unity 完成后，将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="28164-172">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="28164-173">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-173">Open the **App** folder.</span></span>
* <span data-ttu-id="28164-174">打开**SharedHolograms**以启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="28164-174">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="28164-175">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **X86**"。</span><span class="sxs-lookup"><span data-stu-id="28164-175">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="28164-176">单击 "本地计算机" 旁边的下拉箭头，然后选择 "**远程设备**"。</span><span class="sxs-lookup"><span data-stu-id="28164-176">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="28164-177">将**地址**设置为 HoloLens 的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="28164-177">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="28164-178">如果你不知道设备 IP 地址，请在 "设置" 中查找 " **> 网络 & Internet > 高级选项** **" 或 "我的 IP 地址是什么？"。**</span><span class="sxs-lookup"><span data-stu-id="28164-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="28164-179">将**身份验证模式**设置为 "**通用**"。</span><span class="sxs-lookup"><span data-stu-id="28164-179">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="28164-180">单击 "**选择**"</span><span class="sxs-lookup"><span data-stu-id="28164-180">Click **Select**</span></span>
* <span data-ttu-id="28164-181">单击 "**调试" > "开始但不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="28164-181">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="28164-182">如果这是首次部署到设备，则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="28164-182">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
* <span data-ttu-id="28164-183">放在你的 HoloLens 上，找到 EnergyHub 全息图。</span><span class="sxs-lookup"><span data-stu-id="28164-183">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="28164-184">第2章-交互</span><span class="sxs-lookup"><span data-stu-id="28164-184">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="28164-185">在本章中，我们将与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="28164-185">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="28164-186">首先，我们将添加一个光标以直观显示[注视](gaze-and-commit.md)。</span><span class="sxs-lookup"><span data-stu-id="28164-186">First, we'll add a cursor to visualize our [Gaze](gaze-and-commit.md).</span></span> <span data-ttu-id="28164-187">接下来，我们将添加[手势](gaze-and-commit.md#composite-gestures)，并使用我们的手在空间中放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="28164-187">Then, we'll add [Gestures](gaze-and-commit.md#composite-gestures) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="28164-188">目标</span><span class="sxs-lookup"><span data-stu-id="28164-188">Objectives</span></span>

* <span data-ttu-id="28164-189">使用 "注视输入" 控制光标。</span><span class="sxs-lookup"><span data-stu-id="28164-189">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="28164-190">使用手势输入与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="28164-190">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="28164-191">说明</span><span class="sxs-lookup"><span data-stu-id="28164-191">Instructions</span></span>

<span data-ttu-id="28164-192">**凝视**</span><span class="sxs-lookup"><span data-stu-id="28164-192">**Gaze**</span></span>

* <span data-ttu-id="28164-193">在 "**层次结构" 面板**中，选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="28164-193">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="28164-194">在**检查器面板**中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="28164-194">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="28164-195">在菜单中，在 "搜索" 框中键入 "**注视经理**"。</span><span class="sxs-lookup"><span data-stu-id="28164-195">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="28164-196">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="28164-196">Select the search result.</span></span>
* <span data-ttu-id="28164-197">在**HoloToolkit-Sharing-240\Prefabs\Input**文件夹中，找到**光标**资产。</span><span class="sxs-lookup"><span data-stu-id="28164-197">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="28164-198">将**光标**资产拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="28164-198">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="28164-199">**姿态**</span><span class="sxs-lookup"><span data-stu-id="28164-199">**Gesture**</span></span>

* <span data-ttu-id="28164-200">在 "**层次结构" 面板**中，选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="28164-200">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="28164-201">单击 "**添加组件**"，并在搜索字段中键入**笔势管理器**。</span><span class="sxs-lookup"><span data-stu-id="28164-201">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="28164-202">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="28164-202">Select the search result.</span></span>
* <span data-ttu-id="28164-203">在 "**层次结构" 面板**中，展开 " **HologramCollection**"。</span><span class="sxs-lookup"><span data-stu-id="28164-203">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="28164-204">选择 "子**EnergyHub** " 对象。</span><span class="sxs-lookup"><span data-stu-id="28164-204">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="28164-205">在**检查器面板**中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="28164-205">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="28164-206">在 "搜索 **" 框中**，键入 "搜索" 对话框。</span><span class="sxs-lookup"><span data-stu-id="28164-206">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="28164-207">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="28164-207">Select the search result.</span></span>
* <span data-ttu-id="28164-208">通过选择 "文件" **> 保存**场景来保存场景。</span><span class="sxs-lookup"><span data-stu-id="28164-208">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="28164-209">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="28164-209">**Deploy and enjoy**</span></span>

* <span data-ttu-id="28164-210">使用上一章中的说明生成并部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="28164-210">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="28164-211">在您的 HoloLens 上启动该应用程序后，请四处移动您的头，注意 EnergyHub 如何进入您的注视。</span><span class="sxs-lookup"><span data-stu-id="28164-211">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="28164-212">请注意，在您看出全息影像时光标如何显示，当不 gazing 在全息图上时，也会改变点光。</span><span class="sxs-lookup"><span data-stu-id="28164-212">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="28164-213">执行轻按下以放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="28164-213">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="28164-214">此时，我们的项目中只能放置一次全息图一次（重新部署后重试）。</span><span class="sxs-lookup"><span data-stu-id="28164-214">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="28164-215">第3章-共享坐标</span><span class="sxs-lookup"><span data-stu-id="28164-215">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="28164-216">与全息影像进行查看和交互很有趣，但让我们进一步了解一下。</span><span class="sxs-lookup"><span data-stu-id="28164-216">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="28164-217">我们将设置我们的第一个共享体验-每个人都可以同时查看。</span><span class="sxs-lookup"><span data-stu-id="28164-217">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="28164-218">目标</span><span class="sxs-lookup"><span data-stu-id="28164-218">Objectives</span></span>

* <span data-ttu-id="28164-219">为共享体验设置网络。</span><span class="sxs-lookup"><span data-stu-id="28164-219">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="28164-220">建立一个公共参考点。</span><span class="sxs-lookup"><span data-stu-id="28164-220">Establish a common reference point.</span></span>
* <span data-ttu-id="28164-221">跨设备共享坐标系统。</span><span class="sxs-lookup"><span data-stu-id="28164-221">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="28164-222">所有人都看到同一个全息图！</span><span class="sxs-lookup"><span data-stu-id="28164-222">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="28164-223">必须为应用声明**InternetClientServer**和**PrivateNetworkClientServer**功能才能连接到共享服务器。</span><span class="sxs-lookup"><span data-stu-id="28164-223">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="28164-224">此操作已在全息影像240中完成，但请记住你自己的项目。</span><span class="sxs-lookup"><span data-stu-id="28164-224">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>

>1. <span data-ttu-id="28164-225">在 Unity 编辑器中，导航到 "编辑 > 项目设置 > Player"，转到 "播放机" 设置</span><span class="sxs-lookup"><span data-stu-id="28164-225">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="28164-226">单击 "Windows 应用商店" 选项卡</span><span class="sxs-lookup"><span data-stu-id="28164-226">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="28164-227">在 "发布设置 > 功能" 部分中，查看**InternetClientServer**功能和**PrivateNetworkClientServer**功能</span><span class="sxs-lookup"><span data-stu-id="28164-227">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="28164-228">说明</span><span class="sxs-lookup"><span data-stu-id="28164-228">Instructions</span></span>

* <span data-ttu-id="28164-229">在 "**项目" 面板**中，导航到**HoloToolkit-Sharing-240\Prefabs\Sharing**文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-229">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="28164-230">将**共享**prefab 拖放到**层次结构面板**。</span><span class="sxs-lookup"><span data-stu-id="28164-230">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="28164-231">接下来，我们需要启动共享服务。</span><span class="sxs-lookup"><span data-stu-id="28164-231">Next we need to launch the sharing service.</span></span> <span data-ttu-id="28164-232">共享体验中只有**一台 PC**需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="28164-232">Only **one PC** in the shared experience needs to do this step.</span></span>

* <span data-ttu-id="28164-233">在 Unity 中-在顶部菜单中，选择 " **HoloToolkit-240" 菜单**。</span><span class="sxs-lookup"><span data-stu-id="28164-233">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="28164-234">在下拉栏中选择 "**启动共享服务**" 项。</span><span class="sxs-lookup"><span data-stu-id="28164-234">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="28164-235">选中 "**专用网络**" 选项，并在出现防火墙提示时单击 "**允许访问**"。</span><span class="sxs-lookup"><span data-stu-id="28164-235">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="28164-236">记下 "共享服务控制台" 窗口中显示的 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="28164-236">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="28164-237">此 IP 与运行服务的计算机的 IP 相同。</span><span class="sxs-lookup"><span data-stu-id="28164-237">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="28164-238">按照将加入共享体验的**所有 pc**上的其余说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="28164-238">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>

* <span data-ttu-id="28164-239">在**层次结构**中，选择**共享**对象。</span><span class="sxs-lookup"><span data-stu-id="28164-239">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="28164-240">在**检查器**的**共享阶段**组件上，将**服务器地址**从 "localhost" 更改为运行 SharingService 的计算机的 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="28164-240">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="28164-241">在**层次结构**中，选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="28164-241">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="28164-242">在**检查器**中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="28164-242">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="28164-243">在搜索框中，键入 "**导入导出定位点管理器**"。</span><span class="sxs-lookup"><span data-stu-id="28164-243">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="28164-244">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="28164-244">Select the search result.</span></span>
* <span data-ttu-id="28164-245">在 "**项目" 面板**中，导航到**Scripts**文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-245">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="28164-246">双击**HologramPlacement**脚本，在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="28164-246">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="28164-247">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="28164-247">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="28164-248">返回 Unity，在 "**层次结构" 面板**中选择 " **HologramCollection** "。</span><span class="sxs-lookup"><span data-stu-id="28164-248">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="28164-249">在**检查器面板**中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="28164-249">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="28164-250">在菜单中，在 "搜索" 框中键入 "**应用状态管理器**"。</span><span class="sxs-lookup"><span data-stu-id="28164-250">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="28164-251">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="28164-251">Select the search result.</span></span>

<span data-ttu-id="28164-252">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="28164-252">**Deploy and enjoy**</span></span>

* <span data-ttu-id="28164-253">生成适用于 HoloLens 设备的项目。</span><span class="sxs-lookup"><span data-stu-id="28164-253">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="28164-254">指定要首先部署到的一个 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="28164-254">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="28164-255">你将需要等待定位点上载到服务，然后才能放置 EnergyHub （这可能需要大约30-60 秒）。</span><span class="sxs-lookup"><span data-stu-id="28164-255">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="28164-256">完成上传之前，将忽略攻丝手势。</span><span class="sxs-lookup"><span data-stu-id="28164-256">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="28164-257">放置 EnergyHub 后，其位置将被上传到服务，然后你可以将其部署到所有其他 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="28164-257">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="28164-258">新的 HoloLens 首次加入会话时，该设备上的 EnergyHub 位置可能不正确。</span><span class="sxs-lookup"><span data-stu-id="28164-258">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="28164-259">但是，一旦从服务下载了定位点和 EnergyHub 位置，EnergyHub 应跳转到新的共享位置。</span><span class="sxs-lookup"><span data-stu-id="28164-259">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="28164-260">如果这不是在约30-60 秒内发生的，则在设置定位点时转到原始 HoloLens 的位置，以收集更多的环境线索。</span><span class="sxs-lookup"><span data-stu-id="28164-260">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="28164-261">如果位置仍未锁定，请重新部署到设备。</span><span class="sxs-lookup"><span data-stu-id="28164-261">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="28164-262">当设备全部准备就绪并运行应用程序时，请查找 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="28164-262">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="28164-263">你是否完全同意了全息图的位置以及文本的方向：</span><span class="sxs-lookup"><span data-stu-id="28164-263">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="28164-264">第4章-发现</span><span class="sxs-lookup"><span data-stu-id="28164-264">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="28164-265">现在，所有人都可以看到相同的全息图！</span><span class="sxs-lookup"><span data-stu-id="28164-265">Everyone can now see the same hologram!</span></span> <span data-ttu-id="28164-266">现在，让我们看看与共享全息环境连接的其他人。</span><span class="sxs-lookup"><span data-stu-id="28164-266">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="28164-267">在本章中，我们将抓住同一共享会话中所有其他 HoloLens 设备的打印头位置和旋转。</span><span class="sxs-lookup"><span data-stu-id="28164-267">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="28164-268">目标</span><span class="sxs-lookup"><span data-stu-id="28164-268">Objectives</span></span>

* <span data-ttu-id="28164-269">了解共享体验。</span><span class="sxs-lookup"><span data-stu-id="28164-269">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="28164-270">选择并共享播放机头像。</span><span class="sxs-lookup"><span data-stu-id="28164-270">Choose and share a player avatar.</span></span>
* <span data-ttu-id="28164-271">将播放机头像附加到每个人的标题旁边。</span><span class="sxs-lookup"><span data-stu-id="28164-271">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="28164-272">说明</span><span class="sxs-lookup"><span data-stu-id="28164-272">Instructions</span></span>

* <span data-ttu-id="28164-273">在 "**项目" 面板**中，导航到 "**全息影像**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-273">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="28164-274">将**PlayerAvatarStore**拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="28164-274">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="28164-275">在 "**项目" 面板**中，导航到**Scripts**文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-275">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="28164-276">双击**AvatarSelector**脚本，在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="28164-276">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="28164-277">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="28164-277">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="28164-278">在**层次结构**中，选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="28164-278">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="28164-279">在**检查器**中单击 "**添加组件**"。</span><span class="sxs-lookup"><span data-stu-id="28164-279">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="28164-280">在搜索框中，键入 "**本地播放机管理器**"。</span><span class="sxs-lookup"><span data-stu-id="28164-280">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="28164-281">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="28164-281">Select the search result.</span></span>
* <span data-ttu-id="28164-282">在**层次结构**中，选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="28164-282">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="28164-283">在**检查器**中单击 "**添加组件**"。</span><span class="sxs-lookup"><span data-stu-id="28164-283">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="28164-284">在搜索框中，键入 "**远程播放机管理器**"。</span><span class="sxs-lookup"><span data-stu-id="28164-284">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="28164-285">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="28164-285">Select the search result.</span></span>
* <span data-ttu-id="28164-286">在 Visual Studio 中打开**HologramPlacement**脚本。</span><span class="sxs-lookup"><span data-stu-id="28164-286">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="28164-287">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="28164-287">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="28164-288">在 Visual Studio 中打开**AppStateManager**脚本。</span><span class="sxs-lookup"><span data-stu-id="28164-288">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="28164-289">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="28164-289">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="28164-290">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="28164-290">**Deploy and Enjoy**</span></span>

* <span data-ttu-id="28164-291">生成项目并将其部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="28164-291">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="28164-292">听到 ping 声音时，请找到头像选择菜单，并选择一个具有 "轻攻器" 手势的头像。</span><span class="sxs-lookup"><span data-stu-id="28164-292">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="28164-293">如果你不想查看任何全息影像，则当你的 HoloLens 与服务进行通信时，光标周围的点亮将变为不同的颜色：正在初始化（深紫色），下载定位点数据（绿色）、导入/导出位置数据（黄色）、正在上载定位点（蓝色）。</span><span class="sxs-lookup"><span data-stu-id="28164-293">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="28164-294">如果光标周围的点亮是默认颜色（浅紫色），则已准备好与会话中的其他玩家交互！</span><span class="sxs-lookup"><span data-stu-id="28164-294">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="28164-295">查看与你的空间连接的其他人员-将有一个全息机器人浮在其肩上并模拟其头运动！</span><span class="sxs-lookup"><span data-stu-id="28164-295">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="28164-296">第5章-位置</span><span class="sxs-lookup"><span data-stu-id="28164-296">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="28164-297">在本章中，我们将定位标记，使其能够放置在实际的表面上。</span><span class="sxs-lookup"><span data-stu-id="28164-297">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="28164-298">我们将使用共享坐标将该定位点置于连接到共享体验的每个用户之间的中间点。</span><span class="sxs-lookup"><span data-stu-id="28164-298">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="28164-299">目标</span><span class="sxs-lookup"><span data-stu-id="28164-299">Objectives</span></span>

* <span data-ttu-id="28164-300">根据玩家的头位置，将全息影像置于空间映射网格上。</span><span class="sxs-lookup"><span data-stu-id="28164-300">Place holograms on the spatial mapping mesh based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="28164-301">说明</span><span class="sxs-lookup"><span data-stu-id="28164-301">Instructions</span></span>

* <span data-ttu-id="28164-302">在 "**项目" 面板**中，导航到 "**全息影像**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-302">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="28164-303">将**CustomSpatialMapping** prefab 拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="28164-303">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="28164-304">在 "**项目" 面板**中，导航到**Scripts**文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-304">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="28164-305">双击**AppStateManager**脚本，在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="28164-305">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="28164-306">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="28164-306">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="28164-307">在 "**项目" 面板**中，导航到**Scripts**文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-307">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="28164-308">双击**HologramPlacement**脚本，在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="28164-308">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="28164-309">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="28164-309">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="28164-310">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="28164-310">**Deploy and enjoy**</span></span>

* <span data-ttu-id="28164-311">生成项目并将其部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="28164-311">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="28164-312">当应用程序准备就绪时，请将其放在一个圆圈上，并注意 EnergyHub 如何出现在每个人的中心。</span><span class="sxs-lookup"><span data-stu-id="28164-312">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="28164-313">点击以放置 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="28164-313">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="28164-314">尝试使用语音命令 "重置目标" 来选择 EnergyHub 备份，并以组的形式协同工作，以便将全息图移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="28164-314">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="28164-315">第6章-真实物理</span><span class="sxs-lookup"><span data-stu-id="28164-315">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="28164-316">在本章中，我们将添加从实际表面弹跳的全息影像。</span><span class="sxs-lookup"><span data-stu-id="28164-316">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="28164-317">观看您和您的朋友所启动的项目的空间。</span><span class="sxs-lookup"><span data-stu-id="28164-317">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="28164-318">目标</span><span class="sxs-lookup"><span data-stu-id="28164-318">Objectives</span></span>

* <span data-ttu-id="28164-319">启动炮弹，从实际表面弹跳。</span><span class="sxs-lookup"><span data-stu-id="28164-319">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="28164-320">共享炮弹，使其他玩家可以看到它们。</span><span class="sxs-lookup"><span data-stu-id="28164-320">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="28164-321">说明</span><span class="sxs-lookup"><span data-stu-id="28164-321">Instructions</span></span>

* <span data-ttu-id="28164-322">在**层次结构**中，选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="28164-322">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="28164-323">在**检查器**中单击 "**添加组件**"。</span><span class="sxs-lookup"><span data-stu-id="28164-323">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="28164-324">在搜索框中，键入 " **Projectile 启动**程序"。</span><span class="sxs-lookup"><span data-stu-id="28164-324">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="28164-325">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="28164-325">Select the search result.</span></span>

<span data-ttu-id="28164-326">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="28164-326">**Deploy and enjoy**</span></span>

* <span data-ttu-id="28164-327">生成并部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="28164-327">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="28164-328">当应用程序在所有设备上运行时，请在实际的表面上执行轻点击以启动 projectile。</span><span class="sxs-lookup"><span data-stu-id="28164-328">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="28164-329">了解 projectile 与其他玩家的头像发生冲突时会发生什么情况！</span><span class="sxs-lookup"><span data-stu-id="28164-329">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="28164-330">第7章-总计 Finale</span><span class="sxs-lookup"><span data-stu-id="28164-330">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="28164-331">在本章中，我们将发现一个只能通过协作发现的门户。</span><span class="sxs-lookup"><span data-stu-id="28164-331">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="28164-332">目标</span><span class="sxs-lookup"><span data-stu-id="28164-332">Objectives</span></span>

* <span data-ttu-id="28164-333">协同工作，在定位点上启动足够的炮弹来发现机密门户！</span><span class="sxs-lookup"><span data-stu-id="28164-333">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="28164-334">说明</span><span class="sxs-lookup"><span data-stu-id="28164-334">Instructions</span></span>

* <span data-ttu-id="28164-335">在 "**项目" 面板**中，导航到 "**全息影像**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="28164-335">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="28164-336">将**Underworld**资产拖放为 HologramCollection 的**子项**。</span><span class="sxs-lookup"><span data-stu-id="28164-336">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="28164-337">选择**HologramCollection**后，在**检查器**中单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="28164-337">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="28164-338">在菜单中，在 "搜索" 框中键入**ExplodeTarget**。</span><span class="sxs-lookup"><span data-stu-id="28164-338">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="28164-339">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="28164-339">Select the search result.</span></span>
* <span data-ttu-id="28164-340">选择**HologramCollection**后，从**层次结构**中，**将 EnergyHub**对象拖到**检查器**中的**目标**字段。</span><span class="sxs-lookup"><span data-stu-id="28164-340">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="28164-341">选择**HologramCollection**后，从**层次结构**中，**将 Underworld**对象拖到**检查器**中的**Underworld**字段。</span><span class="sxs-lookup"><span data-stu-id="28164-341">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="28164-342">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="28164-342">**Deploy and enjoy**</span></span>

* <span data-ttu-id="28164-343">生成并部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="28164-343">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="28164-344">当应用程序启动时，在 EnergyHub 上协作以启动炮弹。</span><span class="sxs-lookup"><span data-stu-id="28164-344">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="28164-345">显示 underworld 时，启动炮弹 at underworld 机器人（单击机器人三次，以获得更多乐趣）。</span><span class="sxs-lookup"><span data-stu-id="28164-345">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
