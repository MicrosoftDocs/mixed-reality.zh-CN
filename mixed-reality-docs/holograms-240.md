---
title: MR 共享 240-多个 HoloLens 设备
description: 遵循此编码使用 Unity、 Visual Studio 和 HoloLens 若要了解详细信息的共享全息演练。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 共享、 网络、 学院、 教程
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592263"
---
>[!NOTE]
><span data-ttu-id="06b1f-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="06b1f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="06b1f-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="06b1f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="06b1f-106">这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="06b1f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="06b1f-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="06b1f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="06b1f-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="06b1f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="06b1f-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="06b1f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="06b1f-110">共享 240 MR:多个 HoloLens 设备</span><span class="sxs-lookup"><span data-stu-id="06b1f-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="06b1f-111">全息提供我们的世界中存在剩余到位，随着我们空间中。</span><span class="sxs-lookup"><span data-stu-id="06b1f-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="06b1f-112">HoloLens 使用各种就地保留全息[坐标系](coordinate-systems.md)来跟踪的位置和方向的对象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="06b1f-113">当我们共享这些设备之间的坐标系统时，我们可以创建可用于共享 holographic 世界中的共享的体验。</span><span class="sxs-lookup"><span data-stu-id="06b1f-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="06b1f-114">在本教程中，我们将：</span><span class="sxs-lookup"><span data-stu-id="06b1f-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="06b1f-115">设置共享体验的网络。</span><span class="sxs-lookup"><span data-stu-id="06b1f-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="06b1f-116">在 HoloLens 设备之间共享全息。</span><span class="sxs-lookup"><span data-stu-id="06b1f-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="06b1f-117">发现我们共享 holographic 世界中的其他人员。</span><span class="sxs-lookup"><span data-stu-id="06b1f-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="06b1f-118">创建共享的交互式体验，可在其中面向其他玩家-并启动它们的炮弹 ！</span><span class="sxs-lookup"><span data-stu-id="06b1f-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="06b1f-119">设备支持</span><span class="sxs-lookup"><span data-stu-id="06b1f-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="06b1f-120">课程</span><span class="sxs-lookup"><span data-stu-id="06b1f-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="06b1f-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="06b1f-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="06b1f-122"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="06b1f-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="06b1f-123">共享 240 MR:多个 HoloLens 设备</span><span class="sxs-lookup"><span data-stu-id="06b1f-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="06b1f-124">✔️</span><span class="sxs-lookup"><span data-stu-id="06b1f-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="06b1f-125">开始之前</span><span class="sxs-lookup"><span data-stu-id="06b1f-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="06b1f-126">先决条件</span><span class="sxs-lookup"><span data-stu-id="06b1f-126">Prerequisites</span></span>

* <span data-ttu-id="06b1f-127">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)具有 Internet 访问权限。</span><span class="sxs-lookup"><span data-stu-id="06b1f-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="06b1f-128">至少两个 HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="06b1f-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="06b1f-129">项目文件</span><span class="sxs-lookup"><span data-stu-id="06b1f-129">Project files</span></span>

* <span data-ttu-id="06b1f-130">下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip)所需的项目。</span><span class="sxs-lookup"><span data-stu-id="06b1f-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="06b1f-131">需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="06b1f-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="06b1f-132">如果你仍然需要 Unity 5.6 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="06b1f-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="06b1f-133">如果你仍然需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="06b1f-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="06b1f-134">如果你仍然需要 Unity 5.4 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)。</span><span class="sxs-lookup"><span data-stu-id="06b1f-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="06b1f-135">取消存档到您的桌面或其他轻松地访问位置的文件。</span><span class="sxs-lookup"><span data-stu-id="06b1f-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="06b1f-136">保留文件夹名称作为**SharedHolograms**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="06b1f-137">如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)。</span><span class="sxs-lookup"><span data-stu-id="06b1f-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="06b1f-138">第 1 章-Holo 世界</span><span class="sxs-lookup"><span data-stu-id="06b1f-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="06b1f-139">在本章中，我们将安装我们的第一个 Unity 项目并单步执行生成和部署过程。</span><span class="sxs-lookup"><span data-stu-id="06b1f-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="06b1f-140">目标</span><span class="sxs-lookup"><span data-stu-id="06b1f-140">Objectives</span></span>

* <span data-ttu-id="06b1f-141">设置 Unity 开发全息版的应用程序。</span><span class="sxs-lookup"><span data-stu-id="06b1f-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="06b1f-142">请参阅你全息图 ！</span><span class="sxs-lookup"><span data-stu-id="06b1f-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="06b1f-143">说明</span><span class="sxs-lookup"><span data-stu-id="06b1f-143">Instructions</span></span>

* <span data-ttu-id="06b1f-144">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="06b1f-144">Start Unity.</span></span>
* <span data-ttu-id="06b1f-145">选择**打开**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-145">Select **Open**.</span></span>
* <span data-ttu-id="06b1f-146">输入与位置**SharedHolograms**你之前未存档的文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="06b1f-147">选择**项目名称**然后单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="06b1f-148">在中**层次结构**，右键单击**Main Camera** ，然后选择**删除**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="06b1f-149">在中**HoloToolkit 共享-240/预设/相机**文件夹中，找到**Main Camera**预设。</span><span class="sxs-lookup"><span data-stu-id="06b1f-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="06b1f-150">拖放到**Main Camera**成**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="06b1f-151">在中**层次结构**，单击**创建**并**创建空白**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="06b1f-152">右键单击新**GameObject** ，然后选择**重命名**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="06b1f-153">重命名为 GameObject **HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="06b1f-154">选择**HologramCollection**对象中**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="06b1f-155">在中**Inspector**设置**转换位置**到：**X:0，Y:-0.25，Z:2**.</span><span class="sxs-lookup"><span data-stu-id="06b1f-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="06b1f-156">在中**全息**中的文件夹**项目面板**，找到**EnergyHub**资产。</span><span class="sxs-lookup"><span data-stu-id="06b1f-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="06b1f-157">拖放到**EnergyHub**对象从**项目面板**到**层次结构**作为**子 HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="06b1f-158">选择**文件 > 另存为场景...**</span><span class="sxs-lookup"><span data-stu-id="06b1f-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="06b1f-159">命名该场景**SharedHolograms**然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="06b1f-160">按**播放**在 Unity 中以预览你全息按钮。</span><span class="sxs-lookup"><span data-stu-id="06b1f-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="06b1f-161">按**播放**停止预览模式下的第二个时机。</span><span class="sxs-lookup"><span data-stu-id="06b1f-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="06b1f-162">**导出到 Visual Studio 从 Unity 项目**</span><span class="sxs-lookup"><span data-stu-id="06b1f-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="06b1f-163">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="06b1f-164">单击**添加打开场景**添加场景。</span><span class="sxs-lookup"><span data-stu-id="06b1f-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="06b1f-165">选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="06b1f-166">设置**SDK**到**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="06b1f-167">设置**目标设备**到**HoloLens**并**UWP 生成类型**到**D3D**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="06b1f-168">检查**UnityC#项目**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="06b1f-169">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="06b1f-169">Click **Build**.</span></span>
* <span data-ttu-id="06b1f-170">在文件资源管理器窗口中显示，创建**新文件夹**名为"应用"。</span><span class="sxs-lookup"><span data-stu-id="06b1f-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="06b1f-171">单击一下**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="06b1f-172">按**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="06b1f-173">Unity 完成操作后，将出现一个文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="06b1f-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="06b1f-174">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-174">Open the **App** folder.</span></span>
* <span data-ttu-id="06b1f-175">打开**SharedHolograms.sln**以启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="06b1f-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="06b1f-176">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **X86**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="06b1f-177">单击本地计算机旁边的下拉箭头，然后选择**远程设备**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="06b1f-178">设置**地址**的名称或 IP 地址在 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="06b1f-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="06b1f-179">如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**问 Cortana 或 **"你好，小娜，我的 IP 地址是什么？"**</span><span class="sxs-lookup"><span data-stu-id="06b1f-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="06b1f-180">将保留**身份验证模式**设置为**通用**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="06b1f-181">单击**选择**</span><span class="sxs-lookup"><span data-stu-id="06b1f-181">Click **Select**</span></span>
* <span data-ttu-id="06b1f-182">单击**调试 > 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="06b1f-183">如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="06b1f-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="06b1f-184">在你 HoloLens 上并查找 EnergyHub 全息图。</span><span class="sxs-lookup"><span data-stu-id="06b1f-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="06b1f-185">第 2 章-交互</span><span class="sxs-lookup"><span data-stu-id="06b1f-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="06b1f-186">在本章中，我们将与我们全息中进行交互。</span><span class="sxs-lookup"><span data-stu-id="06b1f-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="06b1f-187">首先，我们将添加要可视化的游标我们[注视](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="06b1f-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="06b1f-188">然后，我们将添加[手势](gestures.md)和用我们一只手我们全息置于空间。</span><span class="sxs-lookup"><span data-stu-id="06b1f-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="06b1f-189">目标</span><span class="sxs-lookup"><span data-stu-id="06b1f-189">Objectives</span></span>

* <span data-ttu-id="06b1f-190">使用输入来控制游标的视线移动。</span><span class="sxs-lookup"><span data-stu-id="06b1f-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="06b1f-191">使用笔势输入与全息进行交互。</span><span class="sxs-lookup"><span data-stu-id="06b1f-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="06b1f-192">说明</span><span class="sxs-lookup"><span data-stu-id="06b1f-192">Instructions</span></span>

<span data-ttu-id="06b1f-193">**Gaze**</span><span class="sxs-lookup"><span data-stu-id="06b1f-193">**Gaze**</span></span>
* <span data-ttu-id="06b1f-194">在中**层次结构面板**选择**HologramCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="06b1f-195">在中**检查器面板**单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="06b1f-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="06b1f-196">在菜单中，在搜索框中键入**注视 Manager**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="06b1f-197">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="06b1f-197">Select the search result.</span></span>
* <span data-ttu-id="06b1f-198">在中**HoloToolkit 共享 240\Prefabs\Input**文件夹中，找到**光标**资产。</span><span class="sxs-lookup"><span data-stu-id="06b1f-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="06b1f-199">拖放到**游标**拖动到资产**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="06b1f-200">**手势**</span><span class="sxs-lookup"><span data-stu-id="06b1f-200">**Gesture**</span></span>
* <span data-ttu-id="06b1f-201">在中**层次结构面板**选择**HologramCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="06b1f-202">单击**添加组件**并键入**笔势管理器**搜索字段中。</span><span class="sxs-lookup"><span data-stu-id="06b1f-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="06b1f-203">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="06b1f-203">Select the search result.</span></span>
* <span data-ttu-id="06b1f-204">在中**层次结构面板**，展开**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="06b1f-205">选择子**EnergyHub**对象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="06b1f-206">在中**检查器面板**单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="06b1f-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="06b1f-207">在菜单中，在搜索框中键入**全息图放置**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="06b1f-208">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="06b1f-208">Select the search result.</span></span>
* <span data-ttu-id="06b1f-209">通过选择保存场景**文件 > 保存场景**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="06b1f-210">**部署和享受**</span><span class="sxs-lookup"><span data-stu-id="06b1f-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="06b1f-211">生成并部署到你 HoloLens，使用上一章中的说明。</span><span class="sxs-lookup"><span data-stu-id="06b1f-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="06b1f-212">一旦在 HoloLens 上启动该应用程序，移动您，注意 EnergyHub 如何遵循你的视线移动。</span><span class="sxs-lookup"><span data-stu-id="06b1f-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="06b1f-213">请注意，光标出现时您展示全息图，及时不观望在一张全息图将更改为点光的方式。</span><span class="sxs-lookup"><span data-stu-id="06b1f-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="06b1f-214">执行以无线方式点击以放置全息图。</span><span class="sxs-lookup"><span data-stu-id="06b1f-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="06b1f-215">在这次是在我们的项目，您可以仅将 hologram 一次 （重新部署再试一次）。</span><span class="sxs-lookup"><span data-stu-id="06b1f-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="06b1f-216">第 3 章 — 共享坐标</span><span class="sxs-lookup"><span data-stu-id="06b1f-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="06b1f-217">它很有趣，请参阅并全息，与之交互，但让我们进一步。</span><span class="sxs-lookup"><span data-stu-id="06b1f-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="06b1f-218">我们将设置我们第一次的共享体验的每个人都可以同时看到一张全息图。</span><span class="sxs-lookup"><span data-stu-id="06b1f-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="06b1f-219">目标</span><span class="sxs-lookup"><span data-stu-id="06b1f-219">Objectives</span></span>

* <span data-ttu-id="06b1f-220">设置共享体验的网络。</span><span class="sxs-lookup"><span data-stu-id="06b1f-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="06b1f-221">建立的常见的参考点。</span><span class="sxs-lookup"><span data-stu-id="06b1f-221">Establish a common reference point.</span></span>
* <span data-ttu-id="06b1f-222">跨设备共享坐标系统。</span><span class="sxs-lookup"><span data-stu-id="06b1f-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="06b1f-223">每个人都看到同一个全息图 ！</span><span class="sxs-lookup"><span data-stu-id="06b1f-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="06b1f-224">**InternetClientServer**并**PrivateNetworkClientServer**功能必须声明应用程序无法连接到共享服务器。</span><span class="sxs-lookup"><span data-stu-id="06b1f-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="06b1f-225">这是为您已在全息 240 但记住这一点对于您自己的项目。</span><span class="sxs-lookup"><span data-stu-id="06b1f-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="06b1f-226">在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置</span><span class="sxs-lookup"><span data-stu-id="06b1f-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="06b1f-227">单击"Windows 应用商店"选项卡</span><span class="sxs-lookup"><span data-stu-id="06b1f-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="06b1f-228">在"发布设置 > 功能"部分中，检查**InternetClientServer**功能并**PrivateNetworkClientServer**功能</span><span class="sxs-lookup"><span data-stu-id="06b1f-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="06b1f-229">说明</span><span class="sxs-lookup"><span data-stu-id="06b1f-229">Instructions</span></span>

* <span data-ttu-id="06b1f-230">在中**项目面板**导航到**HoloToolkit 共享 240\Prefabs\Sharing**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="06b1f-231">拖放到**共享**到 prefab**层次结构面板**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="06b1f-232">接下来我们需要启动该共享服务。</span><span class="sxs-lookup"><span data-stu-id="06b1f-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="06b1f-233">仅**一台 PC**中的共享体验需要执行此步骤。</span><span class="sxs-lookup"><span data-stu-id="06b1f-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="06b1f-234">在 Unity-顶部手工菜单中选择**HoloToolkit 共享 240 菜单**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="06b1f-235">选择**启动共享服务**下拉列表中的项。</span><span class="sxs-lookup"><span data-stu-id="06b1f-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="06b1f-236">检查**专用网络**选项，然后单击**允许访问**防火墙提示符出现时。</span><span class="sxs-lookup"><span data-stu-id="06b1f-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="06b1f-237">请记下共享服务控制台窗口中显示的 IPv4 地址。</span><span class="sxs-lookup"><span data-stu-id="06b1f-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="06b1f-238">这是该服务正在运行的计算机相同的 IP。</span><span class="sxs-lookup"><span data-stu-id="06b1f-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="06b1f-239">说明的其余部分并遵照**所有 Pc** ，将加入的共享的体验。</span><span class="sxs-lookup"><span data-stu-id="06b1f-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="06b1f-240">在中**层次结构**，选择**共享**对象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="06b1f-241">中**Inspector**，然后在**共享阶段**组件，更改**服务器地址**从运行 SharingService.exe 的计算机的 IPv4 地址 localhost。</span><span class="sxs-lookup"><span data-stu-id="06b1f-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="06b1f-242">在中**层次结构**选择**HologramCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="06b1f-243">在中**Inspector**单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="06b1f-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="06b1f-244">在搜索框中，键入**导入导出定位点管理器**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="06b1f-245">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="06b1f-245">Select the search result.</span></span>
* <span data-ttu-id="06b1f-246">在中**项目面板**导航到**脚本**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="06b1f-247">双击**HologramPlacement**脚本以在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="06b1f-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="06b1f-248">将下面的代码替换为内容。</span><span class="sxs-lookup"><span data-stu-id="06b1f-248">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="06b1f-249">返回在 Unity 中，选择**HologramCollection**中**层次结构面板**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="06b1f-250">在中**检查器面板**单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="06b1f-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="06b1f-251">在菜单中，在搜索框中键入**应用程序状态管理器**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="06b1f-252">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="06b1f-252">Select the search result.</span></span>

<span data-ttu-id="06b1f-253">**部署和享受**</span><span class="sxs-lookup"><span data-stu-id="06b1f-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="06b1f-254">构建于 HoloLens 设备的项目。</span><span class="sxs-lookup"><span data-stu-id="06b1f-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="06b1f-255">将指定一个 HoloLens 将部署到第一个。</span><span class="sxs-lookup"><span data-stu-id="06b1f-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="06b1f-256">将需要等待要上传到该服务之前可以放置 EnergyHub 的定位点 (这可能需要大约 30-60 秒)。</span><span class="sxs-lookup"><span data-stu-id="06b1f-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="06b1f-257">上传完成之前，将忽略点击手势。</span><span class="sxs-lookup"><span data-stu-id="06b1f-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="06b1f-258">已放 EnergyHub 后，其位置将上载到服务，然后将部署到所有其他 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="06b1f-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="06b1f-259">当新 HoloLens 首次加入会话时，EnergyHub 的位置可能不正确的设备上。</span><span class="sxs-lookup"><span data-stu-id="06b1f-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="06b1f-260">但是，一旦已从服务下载的定位点和 EnergyHub 位置，EnergyHub 应跳转到新的共享位置。</span><span class="sxs-lookup"><span data-stu-id="06b1f-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="06b1f-261">如果此情况发生在大约 30-60 秒，引导到原始 HoloLens 所在设置定位点来收集多个环境线索时。</span><span class="sxs-lookup"><span data-stu-id="06b1f-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="06b1f-262">如果该位置仍不会锁定，重新部署到设备。</span><span class="sxs-lookup"><span data-stu-id="06b1f-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="06b1f-263">当设备已全部准备好并运行该应用程序，查找 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="06b1f-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="06b1f-264">可以在所有达成全息图的位置和方向面向文本？</span><span class="sxs-lookup"><span data-stu-id="06b1f-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="06b1f-265">第 4 章-发现</span><span class="sxs-lookup"><span data-stu-id="06b1f-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="06b1f-266">现在，每个人都可以看到相同的 hologram ！</span><span class="sxs-lookup"><span data-stu-id="06b1f-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="06b1f-267">现在让我们查看其他连接到共享 holographic 世界。</span><span class="sxs-lookup"><span data-stu-id="06b1f-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="06b1f-268">在本章中，我们将获取的头位置和相同的共享会话中的所有其他 HoloLens 设备旋转。</span><span class="sxs-lookup"><span data-stu-id="06b1f-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="06b1f-269">目标</span><span class="sxs-lookup"><span data-stu-id="06b1f-269">Objectives</span></span>

* <span data-ttu-id="06b1f-270">发现彼此共享我们的经验。</span><span class="sxs-lookup"><span data-stu-id="06b1f-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="06b1f-271">选择并共享播放机头像。</span><span class="sxs-lookup"><span data-stu-id="06b1f-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="06b1f-272">附加所有人的头旁边的播放机虚拟形象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="06b1f-273">说明</span><span class="sxs-lookup"><span data-stu-id="06b1f-273">Instructions</span></span>

* <span data-ttu-id="06b1f-274">在中**项目面板**导航到**全息**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="06b1f-275">拖放到**PlayerAvatarStore**成**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="06b1f-276">在中**项目面板**导航到**脚本**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="06b1f-277">双击**AvatarSelector**脚本以在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="06b1f-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="06b1f-278">将下面的代码替换为内容。</span><span class="sxs-lookup"><span data-stu-id="06b1f-278">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="06b1f-279">在中**层次结构**选择**HologramCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="06b1f-280">在中**Inspector**单击**添加组件**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="06b1f-281">在搜索框中，键入**本地播放机管理器**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="06b1f-282">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="06b1f-282">Select the search result.</span></span>
* <span data-ttu-id="06b1f-283">在中**层次结构**选择**HologramCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="06b1f-284">在中**Inspector**单击**添加组件**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="06b1f-285">在搜索框中，键入**远程播放机管理器**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="06b1f-286">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="06b1f-286">Select the search result.</span></span>
* <span data-ttu-id="06b1f-287">打开**HologramPlacement** Visual Studio 中的脚本。</span><span class="sxs-lookup"><span data-stu-id="06b1f-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="06b1f-288">将下面的代码替换为内容。</span><span class="sxs-lookup"><span data-stu-id="06b1f-288">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="06b1f-289">打开**AppStateManager** Visual Studio 中的脚本。</span><span class="sxs-lookup"><span data-stu-id="06b1f-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="06b1f-290">将下面的代码替换为内容。</span><span class="sxs-lookup"><span data-stu-id="06b1f-290">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="06b1f-291">**部署和享受**</span><span class="sxs-lookup"><span data-stu-id="06b1f-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="06b1f-292">生成并部署到 HoloLens 设备项目。</span><span class="sxs-lookup"><span data-stu-id="06b1f-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="06b1f-293">当您听到声音执行 ping 操作时，找到头像选择菜单并选择与-敲击手势头像。</span><span class="sxs-lookup"><span data-stu-id="06b1f-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="06b1f-294">如果您不希望在任何全息，浅光标周围的点将变为不同的颜色时你 HoloLens 与服务进行通信： 初始化 （深紫色）、 下载导入/导出位置数据 （黄色） 的定位点 （绿色）上传的定位点 （蓝色）。</span><span class="sxs-lookup"><span data-stu-id="06b1f-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="06b1f-295">如果你浅光标周围的点为默认颜色 （淡紫色），你已准备好在你的会话中与其他玩家进行交互 ！</span><span class="sxs-lookup"><span data-stu-id="06b1f-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="06b1f-296">查看其他人连接到你的空间-会有一个 holographic 机器人浮动上面其即时权限提升和模拟其头动作 ！</span><span class="sxs-lookup"><span data-stu-id="06b1f-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="06b1f-297">第 5 章-放置</span><span class="sxs-lookup"><span data-stu-id="06b1f-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="06b1f-298">在本章中，我们将能够在实际的图面上放置的定位点。</span><span class="sxs-lookup"><span data-stu-id="06b1f-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="06b1f-299">我们将使用共享的坐标中的中间点之间连接的共享体验到的每个人都放置该定位点。</span><span class="sxs-lookup"><span data-stu-id="06b1f-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="06b1f-300">目标</span><span class="sxs-lookup"><span data-stu-id="06b1f-300">Objectives</span></span>

* <span data-ttu-id="06b1f-301">将全息放置在基于玩家的头位置空间映射。</span><span class="sxs-lookup"><span data-stu-id="06b1f-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="06b1f-302">说明</span><span class="sxs-lookup"><span data-stu-id="06b1f-302">Instructions</span></span>

* <span data-ttu-id="06b1f-303">在中**项目面板**导航到**全息**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="06b1f-304">拖放到**CustomSpatialMapping**拖动到 prefab**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="06b1f-305">在中**项目面板**导航到**脚本**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="06b1f-306">双击**AppStateManager**脚本以在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="06b1f-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="06b1f-307">将下面的代码替换为内容。</span><span class="sxs-lookup"><span data-stu-id="06b1f-307">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="06b1f-308">在中**项目面板**导航到**脚本**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="06b1f-309">双击**HologramPlacement**脚本以在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="06b1f-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="06b1f-310">将下面的代码替换为内容。</span><span class="sxs-lookup"><span data-stu-id="06b1f-310">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="06b1f-311">**部署和享受**</span><span class="sxs-lookup"><span data-stu-id="06b1f-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="06b1f-312">生成并部署到 HoloLens 设备项目。</span><span class="sxs-lookup"><span data-stu-id="06b1f-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="06b1f-313">应用程序准备就绪后，在一个圆周中构建并请注意 EnergyHub 的每个用户中心中的显示方式。</span><span class="sxs-lookup"><span data-stu-id="06b1f-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="06b1f-314">点击放置 EnergyHub。</span><span class="sxs-lookup"><span data-stu-id="06b1f-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="06b1f-315">请尝试将全息图移动到新位置的语音命令重置目标以选取 EnergyHub 并作为一个组协同工作。</span><span class="sxs-lookup"><span data-stu-id="06b1f-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="06b1f-316">第 6 章-实际的物理引擎</span><span class="sxs-lookup"><span data-stu-id="06b1f-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="06b1f-317">在这一章中我们将添加全息弹实际的图面。</span><span class="sxs-lookup"><span data-stu-id="06b1f-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="06b1f-318">观看您与项目由你和你的朋友启动填满的空间 ！</span><span class="sxs-lookup"><span data-stu-id="06b1f-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="06b1f-319">目标</span><span class="sxs-lookup"><span data-stu-id="06b1f-319">Objectives</span></span>

* <span data-ttu-id="06b1f-320">启动炮弹弹实际的图面。</span><span class="sxs-lookup"><span data-stu-id="06b1f-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="06b1f-321">共享敌人发射的炮弹，因此其他播放机可以查看它们。</span><span class="sxs-lookup"><span data-stu-id="06b1f-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="06b1f-322">说明</span><span class="sxs-lookup"><span data-stu-id="06b1f-322">Instructions</span></span>

* <span data-ttu-id="06b1f-323">在中**层次结构**选择**HologramCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="06b1f-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="06b1f-324">在中**Inspector**单击**添加组件**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="06b1f-325">在搜索框中，键入**Projectile 启动器**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="06b1f-326">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="06b1f-326">Select the search result.</span></span>

<span data-ttu-id="06b1f-327">**部署和享受**</span><span class="sxs-lookup"><span data-stu-id="06b1f-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="06b1f-328">生成并部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="06b1f-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="06b1f-329">当所有设备上运行应用时，执行以无线方式点击以启动 projectile 在现实世界图面。</span><span class="sxs-lookup"><span data-stu-id="06b1f-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="06b1f-330">请参阅与其他播放机的虚拟形象在 projectile 冲突时会发生什么情况 ！</span><span class="sxs-lookup"><span data-stu-id="06b1f-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="06b1f-331">第 7 章 — 凯旋</span><span class="sxs-lookup"><span data-stu-id="06b1f-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="06b1f-332">在本章中，我们将发现一个门户，它只能发现与协作。</span><span class="sxs-lookup"><span data-stu-id="06b1f-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="06b1f-333">目标</span><span class="sxs-lookup"><span data-stu-id="06b1f-333">Objectives</span></span>

* <span data-ttu-id="06b1f-334">协同工作以启动在定位点来发现机密门户足够炮弹 ！</span><span class="sxs-lookup"><span data-stu-id="06b1f-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="06b1f-335">说明</span><span class="sxs-lookup"><span data-stu-id="06b1f-335">Instructions</span></span>

* <span data-ttu-id="06b1f-336">在中**项目面板**导航到**全息**文件夹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="06b1f-337">拖放到**Underworld**作为资产**HologramCollection 子**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="06b1f-338">与**HologramCollection**处于选中状态，单击**添加组件**按钮**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="06b1f-339">在菜单中，在搜索框中键入**ExplodeTarget**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="06b1f-340">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="06b1f-340">Select the search result.</span></span>
* <span data-ttu-id="06b1f-341">与**HologramCollection**选定，从**层次结构**拖动**EnergyHub**对象传递给**目标**字段中**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="06b1f-342">与**HologramCollection**选定，从**层次结构**拖动**Underworld**对象传递给**Underworld** 字段**检查器**。</span><span class="sxs-lookup"><span data-stu-id="06b1f-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="06b1f-343">**部署和享受**</span><span class="sxs-lookup"><span data-stu-id="06b1f-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="06b1f-344">生成并部署到 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="06b1f-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="06b1f-345">当应用启动时，共同协作以启动在 EnergyHub 炮弹。</span><span class="sxs-lookup"><span data-stu-id="06b1f-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="06b1f-346">Underworld 出现时，启动炮弹在 underworld 机器人 （命中三倍的额外有趣机器人）。</span><span class="sxs-lookup"><span data-stu-id="06b1f-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
