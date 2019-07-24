---
title: MR 共享 240-多个 HoloLens 设备
description: 按照此编码演练操作, 使用 Unity、Visual Studio 和 HoloLens 了解共享全息影像的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 共享, 网络, 学院, 教程
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522331"
---
>[!NOTE]
><span data-ttu-id="db244-104">混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="db244-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="db244-105">因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="db244-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="db244-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="db244-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="db244-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="db244-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="db244-108">将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="db244-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="db244-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="db244-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="db244-110">尊敬的共享 240:多个 HoloLens 设备</span><span class="sxs-lookup"><span data-stu-id="db244-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="db244-111">随着我们在空间中的发展, 我们将在世界各地提供全息影像。</span><span class="sxs-lookup"><span data-stu-id="db244-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="db244-112">通过使用各种[坐标系统](coordinate-systems.md)跟踪对象的位置和方向, HoloLens 保留了全息影像。</span><span class="sxs-lookup"><span data-stu-id="db244-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="db244-113">当我们在设备之间共享这些坐标系统时, 我们可以创建共享体验, 使我们能够参与共享全息环境。</span><span class="sxs-lookup"><span data-stu-id="db244-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="db244-114">在本教程中, 我们将:</span><span class="sxs-lookup"><span data-stu-id="db244-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="db244-115">为共享体验设置网络。</span><span class="sxs-lookup"><span data-stu-id="db244-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="db244-116">跨 HoloLens 设备共享全息影像。</span><span class="sxs-lookup"><span data-stu-id="db244-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="db244-117">了解我们的共享全息领域中的其他人员。</span><span class="sxs-lookup"><span data-stu-id="db244-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="db244-118">创建可面向其他玩家的共享交互式体验, 并在其上启动炮弹!</span><span class="sxs-lookup"><span data-stu-id="db244-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="db244-119">设备支持</span><span class="sxs-lookup"><span data-stu-id="db244-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="db244-120">摘要</span><span class="sxs-lookup"><span data-stu-id="db244-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="db244-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="db244-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="db244-122"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="db244-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="db244-123">尊敬的共享 240:多个 HoloLens 设备</span><span class="sxs-lookup"><span data-stu-id="db244-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="db244-124">✔️</span><span class="sxs-lookup"><span data-stu-id="db244-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="db244-125">开始之前</span><span class="sxs-lookup"><span data-stu-id="db244-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="db244-126">先决条件</span><span class="sxs-lookup"><span data-stu-id="db244-126">Prerequisites</span></span>

* <span data-ttu-id="db244-127">使用随 Internet 访问权限安装的正确[工具](install-the-tools.md)配置的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="db244-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="db244-128">至少[为开发配置了](using-visual-studio.md#enabling-developer-mode)两个 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="db244-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="db244-129">项目文件</span><span class="sxs-lookup"><span data-stu-id="db244-129">Project files</span></span>

* <span data-ttu-id="db244-130">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)。</span><span class="sxs-lookup"><span data-stu-id="db244-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="db244-131">需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="db244-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="db244-132">如果仍需要 Unity 5.6 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="db244-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="db244-133">如果仍需要 Unity 5.5 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="db244-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="db244-134">如果仍需要 Unity 5.4 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="db244-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="db244-135">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="db244-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="db244-136">将文件夹名称保留为**SharedHolograms**。</span><span class="sxs-lookup"><span data-stu-id="db244-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="db244-137">如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)找到。</span><span class="sxs-lookup"><span data-stu-id="db244-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="db244-138">第1章-Holo World</span><span class="sxs-lookup"><span data-stu-id="db244-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="db244-139">在本章中, 我们将设置第一个 Unity 项目, 并逐步完成生成和部署过程。</span><span class="sxs-lookup"><span data-stu-id="db244-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="db244-140">目标</span><span class="sxs-lookup"><span data-stu-id="db244-140">Objectives</span></span>

* <span data-ttu-id="db244-141">安装 Unity 以开发全息版应用。</span><span class="sxs-lookup"><span data-stu-id="db244-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="db244-142">查看全息图!</span><span class="sxs-lookup"><span data-stu-id="db244-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="db244-143">说明</span><span class="sxs-lookup"><span data-stu-id="db244-143">Instructions</span></span>

* <span data-ttu-id="db244-144">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="db244-144">Start Unity.</span></span>
* <span data-ttu-id="db244-145">选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="db244-145">Select **Open**.</span></span>
* <span data-ttu-id="db244-146">输入位置作为之前 unarchived 的**SharedHolograms**文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="db244-147">选择 "**项目名称**", 然后单击 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="db244-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="db244-148">在**层次结构**中, 右键单击**主相机**, 然后选择 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="db244-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="db244-149">在**HoloToolkit/prototyping/相机**文件夹中, 找到**摄像机的主**prefab。</span><span class="sxs-lookup"><span data-stu-id="db244-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="db244-150">将**主相机**拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="db244-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="db244-151">在**层次结构**中, 单击 "**创建**" 并**创建空**。</span><span class="sxs-lookup"><span data-stu-id="db244-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="db244-152">右键单击新的 " **GameObject** ", 然后选择 "**重命名**"。</span><span class="sxs-lookup"><span data-stu-id="db244-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="db244-153">将 GameObject 重命名为**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="db244-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="db244-154">选择**层次结构**中的**HologramCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="db244-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="db244-155">在**检查器**中, 将**转换位置**设置为:**X-BLADE0, Y:-0.25, Z:2**。</span><span class="sxs-lookup"><span data-stu-id="db244-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="db244-156">在 "**项目" 面板**的 "**全息影像**" 文件夹中, 找到 " **EnergyHub**资产"。</span><span class="sxs-lookup"><span data-stu-id="db244-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="db244-157">将**EnergyHub**对象从 "**项目" 面板**中拖放到**层次结构**中, 将其作为**HologramCollection 的子项**。</span><span class="sxs-lookup"><span data-stu-id="db244-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="db244-158">选择**文件 > 将场景另存为 ...**</span><span class="sxs-lookup"><span data-stu-id="db244-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="db244-159">将场景命名为**SharedHolograms** , 然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="db244-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="db244-160">按下 Unity 中的 "**播放**" 按钮, 预览全息影像。</span><span class="sxs-lookup"><span data-stu-id="db244-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="db244-161">按第二次**播放**以停止预览模式。</span><span class="sxs-lookup"><span data-stu-id="db244-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="db244-162">**将项目从 Unity 导出到 Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="db244-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="db244-163">在 Unity 中, 选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="db244-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="db244-164">单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="db244-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="db244-165">选择 "**平台**" 列表中的 "**通用 Windows 平台**", 然后单击 "**切换平台**"。</span><span class="sxs-lookup"><span data-stu-id="db244-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="db244-166">将**SDK**设置为**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="db244-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="db244-167">将**目标设备**设置为**HoloLens** , 将 " **UWP" 生成类型**设置为 " **D3D**"。</span><span class="sxs-lookup"><span data-stu-id="db244-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="db244-168">检查**Unity C#项目**。</span><span class="sxs-lookup"><span data-stu-id="db244-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="db244-169">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="db244-169">Click **Build**.</span></span>
* <span data-ttu-id="db244-170">在出现的 "文件资源管理器" 窗口中, 创建一个名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="db244-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="db244-171">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="db244-172">按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="db244-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="db244-173">当 Unity 完成后, 将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="db244-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="db244-174">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-174">Open the **App** folder.</span></span>
* <span data-ttu-id="db244-175">打开**SharedHolograms**以启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="db244-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="db244-176">使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **X86**"。</span><span class="sxs-lookup"><span data-stu-id="db244-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="db244-177">单击 "本地计算机" 旁边的下拉箭头, 然后选择 "**远程设备**"。</span><span class="sxs-lookup"><span data-stu-id="db244-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="db244-178">将**地址**设置为 HoloLens 的名称或 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="db244-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="db244-179">如果你不知道设备 IP 地址, 请在 "设置" 中查找 " **> 网络 & Internet > 高级选项** **" 或 "我的 IP 地址是什么？"。**</span><span class="sxs-lookup"><span data-stu-id="db244-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="db244-180">将**身份验证模式**设置为 "**通用**"。</span><span class="sxs-lookup"><span data-stu-id="db244-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="db244-181">单击 "**选择**"</span><span class="sxs-lookup"><span data-stu-id="db244-181">Click **Select**</span></span>
* <span data-ttu-id="db244-182">单击 "**调试" > "开始但不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="db244-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="db244-183">如果这是首次部署到设备, 则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="db244-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="db244-184">放在你的 HoloLens 上, 找到 EnergyHub 全息图。</span><span class="sxs-lookup"><span data-stu-id="db244-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="db244-185">第2章-交互</span><span class="sxs-lookup"><span data-stu-id="db244-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="db244-186">在本章中, 我们将与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="db244-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="db244-187">首先, 我们将添加一个光标以直观显示[注视](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="db244-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="db244-188">接下来, 我们将添加[手势](gestures.md), 并使用我们的手在空间中放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="db244-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="db244-189">目标</span><span class="sxs-lookup"><span data-stu-id="db244-189">Objectives</span></span>

* <span data-ttu-id="db244-190">使用 "注视输入" 控制光标。</span><span class="sxs-lookup"><span data-stu-id="db244-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="db244-191">使用手势输入与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="db244-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="db244-192">说明</span><span class="sxs-lookup"><span data-stu-id="db244-192">Instructions</span></span>

<span data-ttu-id="db244-193">**凝视**</span><span class="sxs-lookup"><span data-stu-id="db244-193">**Gaze**</span></span>
* <span data-ttu-id="db244-194">在 "**层次结构" 面板**中, 选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="db244-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="db244-195">在**检查器面板**中, 单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="db244-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="db244-196">在菜单中, 在 "搜索" 框中键入 "**注视经理**"。</span><span class="sxs-lookup"><span data-stu-id="db244-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="db244-197">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="db244-197">Select the search result.</span></span>
* <span data-ttu-id="db244-198">在**HoloToolkit-Sharing-240\Prefabs\Input**文件夹中, 找到**光标**资产。</span><span class="sxs-lookup"><span data-stu-id="db244-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="db244-199">将**光标**资产拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="db244-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="db244-200">**姿态**</span><span class="sxs-lookup"><span data-stu-id="db244-200">**Gesture**</span></span>
* <span data-ttu-id="db244-201">在 "**层次结构" 面板**中, 选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="db244-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="db244-202">单击 "**添加组件**", 并在搜索字段中键入**笔势管理器**。</span><span class="sxs-lookup"><span data-stu-id="db244-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="db244-203">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="db244-203">Select the search result.</span></span>
* <span data-ttu-id="db244-204">在 "**层次结构" 面板**中, 展开 " **HologramCollection**"。</span><span class="sxs-lookup"><span data-stu-id="db244-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="db244-205">选择 "子**EnergyHub** " 对象。</span><span class="sxs-lookup"><span data-stu-id="db244-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="db244-206">在**检查器面板**中, 单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="db244-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="db244-207">在 "搜索 **" 框中**, 键入 "搜索" 对话框。</span><span class="sxs-lookup"><span data-stu-id="db244-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="db244-208">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="db244-208">Select the search result.</span></span>
* <span data-ttu-id="db244-209">通过选择 "文件" **> 保存**场景来保存场景。</span><span class="sxs-lookup"><span data-stu-id="db244-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="db244-210">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="db244-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="db244-211">使用上一章中的说明生成并部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="db244-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="db244-212">在您的 HoloLens 上启动该应用程序后, 请四处移动您的头, 注意 EnergyHub 如何进入您的注视。</span><span class="sxs-lookup"><span data-stu-id="db244-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="db244-213">请注意, 在您看出全息影像时光标如何显示, 当不 gazing 在全息图上时, 也会改变点光。</span><span class="sxs-lookup"><span data-stu-id="db244-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="db244-214">执行轻按下以放置全息影像。</span><span class="sxs-lookup"><span data-stu-id="db244-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="db244-215">此时, 我们的项目中只能放置一次全息图一次 (重新部署后重试)。</span><span class="sxs-lookup"><span data-stu-id="db244-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="db244-216">第3章-共享坐标</span><span class="sxs-lookup"><span data-stu-id="db244-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="db244-217">与全息影像进行查看和交互很有趣, 但让我们进一步了解一下。</span><span class="sxs-lookup"><span data-stu-id="db244-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="db244-218">我们将设置我们的第一个共享体验-每个人都可以同时查看。</span><span class="sxs-lookup"><span data-stu-id="db244-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="db244-219">目标</span><span class="sxs-lookup"><span data-stu-id="db244-219">Objectives</span></span>

* <span data-ttu-id="db244-220">为共享体验设置网络。</span><span class="sxs-lookup"><span data-stu-id="db244-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="db244-221">建立一个公共参考点。</span><span class="sxs-lookup"><span data-stu-id="db244-221">Establish a common reference point.</span></span>
* <span data-ttu-id="db244-222">跨设备共享坐标系统。</span><span class="sxs-lookup"><span data-stu-id="db244-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="db244-223">所有人都看到同一个全息图!</span><span class="sxs-lookup"><span data-stu-id="db244-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="db244-224">必须为应用声明**InternetClientServer**和**PrivateNetworkClientServer**功能才能连接到共享服务器。</span><span class="sxs-lookup"><span data-stu-id="db244-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="db244-225">此操作已在全息影像240中完成, 但请记住你自己的项目。</span><span class="sxs-lookup"><span data-stu-id="db244-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="db244-226">在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player", 转到 "播放机" 设置</span><span class="sxs-lookup"><span data-stu-id="db244-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="db244-227">单击 "Windows 应用商店" 选项卡</span><span class="sxs-lookup"><span data-stu-id="db244-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="db244-228">在 "发布设置 > 功能" 部分中, 查看**InternetClientServer**功能和**PrivateNetworkClientServer**功能</span><span class="sxs-lookup"><span data-stu-id="db244-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="db244-229">说明</span><span class="sxs-lookup"><span data-stu-id="db244-229">Instructions</span></span>

* <span data-ttu-id="db244-230">在 "**项目" 面板**中, 导航到**HoloToolkit-Sharing-240\Prefabs\Sharing**文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="db244-231">将**共享**prefab 拖放到**层次结构面板**。</span><span class="sxs-lookup"><span data-stu-id="db244-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="db244-232">接下来, 我们需要启动共享服务。</span><span class="sxs-lookup"><span data-stu-id="db244-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="db244-233">共享体验中只有**一台 PC**需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="db244-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="db244-234">在 Unity 中-在顶部菜单中, 选择 " **HoloToolkit-240" 菜单**。</span><span class="sxs-lookup"><span data-stu-id="db244-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="db244-235">在下拉栏中选择 "**启动共享服务**" 项。</span><span class="sxs-lookup"><span data-stu-id="db244-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="db244-236">选中 "**专用网络**" 选项, 并在出现防火墙提示时单击 "**允许访问**"。</span><span class="sxs-lookup"><span data-stu-id="db244-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="db244-237">记下 "共享服务控制台" 窗口中显示的 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="db244-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="db244-238">此 IP 与运行服务的计算机的 IP 相同。</span><span class="sxs-lookup"><span data-stu-id="db244-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="db244-239">按照将加入共享体验的**所有 pc**上的其余说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="db244-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="db244-240">在**层次结构**中, 选择**共享**对象。</span><span class="sxs-lookup"><span data-stu-id="db244-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="db244-241">在**检查器**的**共享阶段**组件上, 将**服务器地址**从 "localhost" 更改为运行 SharingService 的计算机的 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="db244-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="db244-242">在**层次结构**中, 选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="db244-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="db244-243">在**检查器**中, 单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="db244-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="db244-244">在搜索框中, 键入 "**导入导出定位点管理器**"。</span><span class="sxs-lookup"><span data-stu-id="db244-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="db244-245">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="db244-245">Select the search result.</span></span>
* <span data-ttu-id="db244-246">在 "**项目" 面板**中, 导航到**Scripts**文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="db244-247">双击**HologramPlacement**脚本, 在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="db244-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="db244-248">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="db244-248">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="db244-249">返回 Unity, 在 "**层次结构" 面板**中选择 " **HologramCollection** "。</span><span class="sxs-lookup"><span data-stu-id="db244-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="db244-250">在**检查器面板**中, 单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="db244-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="db244-251">在菜单中, 在 "搜索" 框中键入 "**应用状态管理器**"。</span><span class="sxs-lookup"><span data-stu-id="db244-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="db244-252">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="db244-252">Select the search result.</span></span>

<span data-ttu-id="db244-253">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="db244-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="db244-254">生成适用于 HoloLens 设备的项目。</span><span class="sxs-lookup"><span data-stu-id="db244-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="db244-255">指定要首先部署到的一个 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="db244-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="db244-256">你将需要等待定位点上载到服务, 然后才能放置 EnergyHub (这可能需要大约30-60 秒)。</span><span class="sxs-lookup"><span data-stu-id="db244-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="db244-257">完成上传之前, 将忽略攻丝手势。</span><span class="sxs-lookup"><span data-stu-id="db244-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="db244-258">放置 EnergyHub 后, 其位置将被上传到服务, 然后你可以将其部署到所有其他 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="db244-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="db244-259">新的 HoloLens 首次加入会话时, 该设备上的 EnergyHub 位置可能不正确。</span><span class="sxs-lookup"><span data-stu-id="db244-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="db244-260">但是, 一旦从服务下载了定位点和 EnergyHub 位置, EnergyHub 应跳转到新的共享位置。</span><span class="sxs-lookup"><span data-stu-id="db244-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="db244-261">如果这不是在约30-60 秒内发生的, 则在设置定位点时转到原始 HoloLens 的位置, 以收集更多的环境线索。</span><span class="sxs-lookup"><span data-stu-id="db244-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="db244-262">如果位置仍未锁定, 请重新部署到设备。</span><span class="sxs-lookup"><span data-stu-id="db244-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="db244-263">当设备全部准备就绪并运行应用程序时, 请查找 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="db244-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="db244-264">你是否完全同意了全息图的位置以及文本的方向:</span><span class="sxs-lookup"><span data-stu-id="db244-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="db244-265">第4章-发现</span><span class="sxs-lookup"><span data-stu-id="db244-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="db244-266">现在, 所有人都可以看到相同的全息图!</span><span class="sxs-lookup"><span data-stu-id="db244-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="db244-267">现在, 让我们看看与共享全息环境连接的其他人。</span><span class="sxs-lookup"><span data-stu-id="db244-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="db244-268">在本章中, 我们将抓住同一共享会话中所有其他 HoloLens 设备的打印头位置和旋转。</span><span class="sxs-lookup"><span data-stu-id="db244-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="db244-269">目标</span><span class="sxs-lookup"><span data-stu-id="db244-269">Objectives</span></span>

* <span data-ttu-id="db244-270">了解共享体验。</span><span class="sxs-lookup"><span data-stu-id="db244-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="db244-271">选择并共享播放机头像。</span><span class="sxs-lookup"><span data-stu-id="db244-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="db244-272">将播放机头像附加到每个人的标题旁边。</span><span class="sxs-lookup"><span data-stu-id="db244-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="db244-273">说明</span><span class="sxs-lookup"><span data-stu-id="db244-273">Instructions</span></span>

* <span data-ttu-id="db244-274">在 "**项目" 面板**中, 导航到 "**全息影像**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="db244-275">将**PlayerAvatarStore**拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="db244-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="db244-276">在 "**项目" 面板**中, 导航到**Scripts**文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="db244-277">双击**AvatarSelector**脚本, 在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="db244-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="db244-278">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="db244-278">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="db244-279">在**层次结构**中, 选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="db244-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="db244-280">在**检查器**中单击 "**添加组件**"。</span><span class="sxs-lookup"><span data-stu-id="db244-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="db244-281">在搜索框中, 键入 "**本地播放机管理器**"。</span><span class="sxs-lookup"><span data-stu-id="db244-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="db244-282">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="db244-282">Select the search result.</span></span>
* <span data-ttu-id="db244-283">在**层次结构**中, 选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="db244-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="db244-284">在**检查器**中单击 "**添加组件**"。</span><span class="sxs-lookup"><span data-stu-id="db244-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="db244-285">在搜索框中, 键入 "**远程播放机管理器**"。</span><span class="sxs-lookup"><span data-stu-id="db244-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="db244-286">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="db244-286">Select the search result.</span></span>
* <span data-ttu-id="db244-287">在 Visual Studio 中打开**HologramPlacement**脚本。</span><span class="sxs-lookup"><span data-stu-id="db244-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="db244-288">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="db244-288">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="db244-289">在 Visual Studio 中打开**AppStateManager**脚本。</span><span class="sxs-lookup"><span data-stu-id="db244-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="db244-290">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="db244-290">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="db244-291">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="db244-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="db244-292">生成项目并将其部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="db244-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="db244-293">听到 ping 声音时, 请找到头像选择菜单, 并选择一个具有 "轻攻器" 手势的头像。</span><span class="sxs-lookup"><span data-stu-id="db244-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="db244-294">如果你不想查看任何全息影像, 则当你的 HoloLens 与服务进行通信时, 光标周围的点亮将变为不同的颜色: 正在初始化 (深紫色), 下载定位点数据 (绿色)、导入/导出位置数据 (黄色)、正在上载定位点 (蓝色)。</span><span class="sxs-lookup"><span data-stu-id="db244-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="db244-295">如果光标周围的点亮是默认颜色 (浅紫色), 则已准备好与会话中的其他玩家交互!</span><span class="sxs-lookup"><span data-stu-id="db244-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="db244-296">查看与你的空间连接的其他人员-将有一个全息机器人浮在其肩上并模拟其头运动!</span><span class="sxs-lookup"><span data-stu-id="db244-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="db244-297">第5章-位置</span><span class="sxs-lookup"><span data-stu-id="db244-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="db244-298">在本章中, 我们将定位标记, 使其能够放置在实际的表面上。</span><span class="sxs-lookup"><span data-stu-id="db244-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="db244-299">我们将使用共享坐标将该定位点置于连接到共享体验的每个用户之间的中间点。</span><span class="sxs-lookup"><span data-stu-id="db244-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="db244-300">目标</span><span class="sxs-lookup"><span data-stu-id="db244-300">Objectives</span></span>

* <span data-ttu-id="db244-301">根据玩家的头位置, 将全息影像置于空间地图上。</span><span class="sxs-lookup"><span data-stu-id="db244-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="db244-302">说明</span><span class="sxs-lookup"><span data-stu-id="db244-302">Instructions</span></span>

* <span data-ttu-id="db244-303">在 "**项目" 面板**中, 导航到 "**全息影像**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="db244-304">将**CustomSpatialMapping** prefab 拖放到**层次结构**中。</span><span class="sxs-lookup"><span data-stu-id="db244-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="db244-305">在 "**项目" 面板**中, 导航到**Scripts**文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="db244-306">双击**AppStateManager**脚本, 在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="db244-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="db244-307">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="db244-307">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="db244-308">在 "**项目" 面板**中, 导航到**Scripts**文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="db244-309">双击**HologramPlacement**脚本, 在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="db244-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="db244-310">将内容替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="db244-310">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="db244-311">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="db244-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="db244-312">生成项目并将其部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="db244-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="db244-313">当应用程序准备就绪时, 请将其放在一个圆圈上, 并注意 EnergyHub 如何出现在每个人的中心。</span><span class="sxs-lookup"><span data-stu-id="db244-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="db244-314">点击以放置 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="db244-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="db244-315">尝试使用语音命令 "重置目标" 来选择 EnergyHub 备份, 并以组的形式协同工作, 以便将全息图移动到新位置。</span><span class="sxs-lookup"><span data-stu-id="db244-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="db244-316">第6章-真实物理</span><span class="sxs-lookup"><span data-stu-id="db244-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="db244-317">在本章中, 我们将添加从实际表面弹跳的全息影像。</span><span class="sxs-lookup"><span data-stu-id="db244-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="db244-318">观看您和您的朋友所启动的项目的空间。</span><span class="sxs-lookup"><span data-stu-id="db244-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="db244-319">目标</span><span class="sxs-lookup"><span data-stu-id="db244-319">Objectives</span></span>

* <span data-ttu-id="db244-320">启动炮弹, 从实际表面弹跳。</span><span class="sxs-lookup"><span data-stu-id="db244-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="db244-321">共享炮弹, 使其他玩家可以看到它们。</span><span class="sxs-lookup"><span data-stu-id="db244-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="db244-322">说明</span><span class="sxs-lookup"><span data-stu-id="db244-322">Instructions</span></span>

* <span data-ttu-id="db244-323">在**层次结构**中, 选择 " **HologramCollection** " 对象。</span><span class="sxs-lookup"><span data-stu-id="db244-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="db244-324">在**检查器**中单击 "**添加组件**"。</span><span class="sxs-lookup"><span data-stu-id="db244-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="db244-325">在搜索框中, 键入 " **Projectile 启动**程序"。</span><span class="sxs-lookup"><span data-stu-id="db244-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="db244-326">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="db244-326">Select the search result.</span></span>

<span data-ttu-id="db244-327">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="db244-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="db244-328">生成并部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="db244-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="db244-329">当应用程序在所有设备上运行时, 请在实际的表面上执行轻点击以启动 projectile。</span><span class="sxs-lookup"><span data-stu-id="db244-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="db244-330">了解 projectile 与其他玩家的头像发生冲突时会发生什么情况!</span><span class="sxs-lookup"><span data-stu-id="db244-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="db244-331">第7章-总计 Finale</span><span class="sxs-lookup"><span data-stu-id="db244-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="db244-332">在本章中, 我们将发现一个只能通过协作发现的门户。</span><span class="sxs-lookup"><span data-stu-id="db244-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="db244-333">目标</span><span class="sxs-lookup"><span data-stu-id="db244-333">Objectives</span></span>

* <span data-ttu-id="db244-334">协同工作, 在定位点上启动足够的炮弹来发现机密门户!</span><span class="sxs-lookup"><span data-stu-id="db244-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="db244-335">说明</span><span class="sxs-lookup"><span data-stu-id="db244-335">Instructions</span></span>

* <span data-ttu-id="db244-336">在 "**项目" 面板**中, 导航到 "**全息影像**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="db244-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="db244-337">将**Underworld**资产拖放为 HologramCollection 的**子项**。</span><span class="sxs-lookup"><span data-stu-id="db244-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="db244-338">选择**HologramCollection**后, 在**检查器**中单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="db244-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="db244-339">在菜单中, 在 "搜索" 框中键入**ExplodeTarget**。</span><span class="sxs-lookup"><span data-stu-id="db244-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="db244-340">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="db244-340">Select the search result.</span></span>
* <span data-ttu-id="db244-341">选择**HologramCollection**后, 从**层次结构**中,**将 EnergyHub**对象拖到**检查器**中的**目标**字段。</span><span class="sxs-lookup"><span data-stu-id="db244-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="db244-342">选择**HologramCollection**后, 从**层次结构**中,**将 Underworld**对象拖到**检查器**中的**Underworld**字段。</span><span class="sxs-lookup"><span data-stu-id="db244-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="db244-343">**部署和体验**</span><span class="sxs-lookup"><span data-stu-id="db244-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="db244-344">生成并部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="db244-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="db244-345">当应用程序启动时, 在 EnergyHub 上协作以启动炮弹。</span><span class="sxs-lookup"><span data-stu-id="db244-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="db244-346">显示 underworld 时, 启动炮弹 at underworld 机器人 (单击机器人三次, 以获得更多乐趣)。</span><span class="sxs-lookup"><span data-stu-id="db244-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
