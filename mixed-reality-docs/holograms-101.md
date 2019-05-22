---
title: MR 基础知识 101-与设备的完整项目
description: 请按照本演练中使用 Unity、 Visual Studio 和 HoloLens 了解 Windows Mixed Reality 的基础知识编码。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合现实，Windows Mixed Reality、 HoloLens、 全息图，学院，教程
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591557"
---
>[!NOTE]
><span data-ttu-id="b0172-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="b0172-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b0172-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="b0172-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b0172-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="b0172-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b0172-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="b0172-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b0172-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="b0172-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b0172-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="b0172-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="b0172-110">MR 基础知识 101:与设备的完整项目</span><span class="sxs-lookup"><span data-stu-id="b0172-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="b0172-111">本教程将引导您完成在 Unity 中，用于演示在 HoloLens 包括核心 Windows Mixed Reality 功能构建的完整项目[注视](gaze.md)，[手势](gestures.md)，[语音输入](voice-input.md)，[空间声音](spatial-sound.md)并[空间映射](spatial-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="b0172-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="b0172-112">本教程需要大约 1 小时才能完成。</span><span class="sxs-lookup"><span data-stu-id="b0172-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="b0172-113">设备支持</span><span class="sxs-lookup"><span data-stu-id="b0172-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b0172-114">课程</span><span class="sxs-lookup"><span data-stu-id="b0172-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b0172-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b0172-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b0172-116"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="b0172-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b0172-117">MR 基础知识 101:与设备的完整项目</span><span class="sxs-lookup"><span data-stu-id="b0172-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="b0172-118">✔️</span><span class="sxs-lookup"><span data-stu-id="b0172-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="b0172-119">开始之前</span><span class="sxs-lookup"><span data-stu-id="b0172-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b0172-120">先决条件</span><span class="sxs-lookup"><span data-stu-id="b0172-120">Prerequisites</span></span>

* <span data-ttu-id="b0172-121">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="b0172-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="b0172-122">HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="b0172-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="b0172-123">项目文件</span><span class="sxs-lookup"><span data-stu-id="b0172-123">Project files</span></span>

* <span data-ttu-id="b0172-124">下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip)所需的项目。</span><span class="sxs-lookup"><span data-stu-id="b0172-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="b0172-125"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="b0172-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="b0172-126">如果你仍然需要 Unity 5.6 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="b0172-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="b0172-127">如果你仍然需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="b0172-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="b0172-128">如果你仍然需要 Unity 5.4 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)。</span><span class="sxs-lookup"><span data-stu-id="b0172-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="b0172-129">取消存档到您的桌面或其他轻松地访问位置的文件。</span><span class="sxs-lookup"><span data-stu-id="b0172-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="b0172-130">保留文件夹名称作为**Origami**。</span><span class="sxs-lookup"><span data-stu-id="b0172-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="b0172-131">如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)。</span><span class="sxs-lookup"><span data-stu-id="b0172-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="b0172-132">第 1 章-"Holo"世界</span><span class="sxs-lookup"><span data-stu-id="b0172-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="b0172-133">在本章中，我们将安装我们的第一个 Unity 项目并单步执行生成和部署过程。</span><span class="sxs-lookup"><span data-stu-id="b0172-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0172-134">目标</span><span class="sxs-lookup"><span data-stu-id="b0172-134">Objectives</span></span>

* <span data-ttu-id="b0172-135">为 holographic 开发设置 Unity。</span><span class="sxs-lookup"><span data-stu-id="b0172-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="b0172-136">请一张全息图。</span><span class="sxs-lookup"><span data-stu-id="b0172-136">Make a hologram.</span></span>
* <span data-ttu-id="b0172-137">所做的一张全息图，请参阅。</span><span class="sxs-lookup"><span data-stu-id="b0172-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0172-138">说明</span><span class="sxs-lookup"><span data-stu-id="b0172-138">Instructions</span></span>

* <span data-ttu-id="b0172-139">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="b0172-139">Start Unity.</span></span>
* <span data-ttu-id="b0172-140">选择**打开**。</span><span class="sxs-lookup"><span data-stu-id="b0172-140">Select **Open**.</span></span>
* <span data-ttu-id="b0172-141">输入与位置**Origami**文件夹你之前未存档。</span><span class="sxs-lookup"><span data-stu-id="b0172-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="b0172-142">选择**Origami**然后单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="b0172-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="b0172-143">由于**Origami**项目不包含一个场景，保存到新文件使用空的默认场景：**文件** / **另存为场景**。</span><span class="sxs-lookup"><span data-stu-id="b0172-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="b0172-144">命名新的场景**Origami**然后按**保存**按钮。</span><span class="sxs-lookup"><span data-stu-id="b0172-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="b0172-145">安装程序主虚拟照相机</span><span class="sxs-lookup"><span data-stu-id="b0172-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="b0172-146">在中**层次结构面板**，选择**Main Camera**。</span><span class="sxs-lookup"><span data-stu-id="b0172-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="b0172-147">在中**Inspector**将其转换位置设置为**0,0,0**。</span><span class="sxs-lookup"><span data-stu-id="b0172-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="b0172-148">查找**清除标志**属性，并将更改从下拉列表中**Skybox**到**纯色**。</span><span class="sxs-lookup"><span data-stu-id="b0172-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="b0172-149">单击**背景**字段以打开颜色选取器。</span><span class="sxs-lookup"><span data-stu-id="b0172-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="b0172-150">设置**R、 G、 B 和 A**到**0**。</span><span class="sxs-lookup"><span data-stu-id="b0172-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="b0172-151">设置场景</span><span class="sxs-lookup"><span data-stu-id="b0172-151">Setup the scene</span></span>

* <span data-ttu-id="b0172-152">在中**层次结构面板**，单击**创建**并**创建空白**。</span><span class="sxs-lookup"><span data-stu-id="b0172-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="b0172-153">右键单击新**GameObject**和选择重命名。</span><span class="sxs-lookup"><span data-stu-id="b0172-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="b0172-154">重命名为 GameObject **OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="b0172-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0172-155">从**全息**项目面板中的文件夹 （展开资产和选择全息或双击项目面板中的全息文件夹）：</span><span class="sxs-lookup"><span data-stu-id="b0172-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="b0172-156">拖动**阶段**到层次结构的子级**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="b0172-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="b0172-157">拖动**Sphere1**到层次结构的子级**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="b0172-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="b0172-158">拖动**Sphere2**到层次结构的子级**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="b0172-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0172-159">右键单击**定向光**对象中**层次结构面板**，然后选择**删除**。</span><span class="sxs-lookup"><span data-stu-id="b0172-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="b0172-160">从**全息**文件夹中，拖动**灯**到的根目录**层次结构面板**。</span><span class="sxs-lookup"><span data-stu-id="b0172-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="b0172-161">在中**层次结构**，选择**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="b0172-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0172-162">在中**Inspector**，将转换位置设置为**0、-0.5、 2.0**。</span><span class="sxs-lookup"><span data-stu-id="b0172-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="b0172-163">按**播放**在 Unity 中以预览你全息按钮。</span><span class="sxs-lookup"><span data-stu-id="b0172-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="b0172-164">您应看到预览窗口中的 Origami 对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="b0172-165">按**播放**停止预览模式下的第二个时机。</span><span class="sxs-lookup"><span data-stu-id="b0172-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="b0172-166">导出到 Visual Studio 从 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b0172-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="b0172-167">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="b0172-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="b0172-168">选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**。</span><span class="sxs-lookup"><span data-stu-id="b0172-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="b0172-169">设置**SDK**到**通用 10**并**生成类型**到**D3D**。</span><span class="sxs-lookup"><span data-stu-id="b0172-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="b0172-170">检查**UnityC#项目**。</span><span class="sxs-lookup"><span data-stu-id="b0172-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="b0172-171">单击**添加打开场景**添加场景。</span><span class="sxs-lookup"><span data-stu-id="b0172-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="b0172-172">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="b0172-172">Click **Build**.</span></span>
* <span data-ttu-id="b0172-173">在文件资源管理器窗口中显示，创建**新文件夹**名为"应用"。</span><span class="sxs-lookup"><span data-stu-id="b0172-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="b0172-174">单击一下**应用程序文件夹**。</span><span class="sxs-lookup"><span data-stu-id="b0172-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="b0172-175">按**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="b0172-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="b0172-176">Unity 完成操作后，将出现一个文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="b0172-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="b0172-177">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0172-177">Open the **App** folder.</span></span>
* <span data-ttu-id="b0172-178">打开 （双击） **Origami.sln**。</span><span class="sxs-lookup"><span data-stu-id="b0172-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="b0172-179">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **X86**。</span><span class="sxs-lookup"><span data-stu-id="b0172-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="b0172-180">单击设备按钮旁边的箭头，然后选择**远程计算机**通过 Wi-fi 部署。</span><span class="sxs-lookup"><span data-stu-id="b0172-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="b0172-181">设置**地址**的名称或 IP 地址在 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b0172-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="b0172-182">如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**问 Cortana 或 **"你好，小娜，我的 IP 地址是什么？"**</span><span class="sxs-lookup"><span data-stu-id="b0172-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="b0172-183">如果通过 USB 连接了 HoloLens，则可能会改为选择**设备**通过 USB 部署。</span><span class="sxs-lookup"><span data-stu-id="b0172-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="b0172-184">将保留**身份验证模式**设置为**通用**。</span><span class="sxs-lookup"><span data-stu-id="b0172-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="b0172-185">单击**选择**</span><span class="sxs-lookup"><span data-stu-id="b0172-185">Click **Select**</span></span>

* <span data-ttu-id="b0172-186">单击**调试 > 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="b0172-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="b0172-187">如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens-(1st-gen))。</span><span class="sxs-lookup"><span data-stu-id="b0172-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="b0172-188">Origami 项目将现在构建、 部署到你 HoloLens，然后运行。</span><span class="sxs-lookup"><span data-stu-id="b0172-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="b0172-189">在你 HoloLens 上并浏览以查看新全息。</span><span class="sxs-lookup"><span data-stu-id="b0172-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="b0172-190">第 2 章-的视线移动</span><span class="sxs-lookup"><span data-stu-id="b0172-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="b0172-191">在本章中，我们将推出的三种方式进行交互的第一个与你全息-[注视](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="b0172-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="b0172-192">目标</span><span class="sxs-lookup"><span data-stu-id="b0172-192">Objectives</span></span>

* <span data-ttu-id="b0172-193">可视化你的视线移动使用 world 锁定的游标。</span><span class="sxs-lookup"><span data-stu-id="b0172-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0172-194">说明</span><span class="sxs-lookup"><span data-stu-id="b0172-194">Instructions</span></span>

* <span data-ttu-id="b0172-195">返回到你的 Unity 项目，并关闭生成设置窗口中，如果它仍处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="b0172-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="b0172-196">选择**全息**中的文件夹**项目面板**。</span><span class="sxs-lookup"><span data-stu-id="b0172-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="b0172-197">拖动**游标**对象插入**层次结构面板**根级别。</span><span class="sxs-lookup"><span data-stu-id="b0172-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="b0172-198">双击**游标**对象，若要更详细地介绍它。</span><span class="sxs-lookup"><span data-stu-id="b0172-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="b0172-199">右键单击**脚本**项目面板中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0172-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="b0172-200">单击**创建**子菜单。</span><span class="sxs-lookup"><span data-stu-id="b0172-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="b0172-201">选择**C#脚本**。</span><span class="sxs-lookup"><span data-stu-id="b0172-201">Select **C# Script**.</span></span>
* <span data-ttu-id="b0172-202">脚本命名为**WorldCursor**。</span><span class="sxs-lookup"><span data-stu-id="b0172-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="b0172-203">注意：该名称区分大小写。</span><span class="sxs-lookup"><span data-stu-id="b0172-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="b0172-204">不需要添加.cs 扩展名。</span><span class="sxs-lookup"><span data-stu-id="b0172-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="b0172-205">选择**游标**对象中**层次结构面板**。</span><span class="sxs-lookup"><span data-stu-id="b0172-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="b0172-206">拖放到**WorldCursor**脚本**检查器面板**。</span><span class="sxs-lookup"><span data-stu-id="b0172-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="b0172-207">双击**WorldCursor**脚本以在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="b0172-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="b0172-208">为此代码复制并粘贴**WorldCursor.cs**并**全部保存**。</span><span class="sxs-lookup"><span data-stu-id="b0172-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="b0172-209">重新生成该应用程序从**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="b0172-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="b0172-210">返回到之前用于将部署到你 HoloLens 的 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="b0172-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="b0172-211">选择全部重新加载出现提示时。</span><span class="sxs-lookup"><span data-stu-id="b0172-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="b0172-212">单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="b0172-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="b0172-213">现在看起来在场景周围，并请注意，光标如何与对象的形状进行交互。</span><span class="sxs-lookup"><span data-stu-id="b0172-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="b0172-214">第 3 章-手势</span><span class="sxs-lookup"><span data-stu-id="b0172-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="b0172-215">在本章中，我们将添加对的支持[手势](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="b0172-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="b0172-216">当用户选择纸张球体时，我们将使处于开启使用 Unity 的物理引擎的重力球体。</span><span class="sxs-lookup"><span data-stu-id="b0172-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0172-217">目标</span><span class="sxs-lookup"><span data-stu-id="b0172-217">Objectives</span></span>

* <span data-ttu-id="b0172-218">控制你全息与选择的笔势。</span><span class="sxs-lookup"><span data-stu-id="b0172-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0172-219">说明</span><span class="sxs-lookup"><span data-stu-id="b0172-219">Instructions</span></span>

<span data-ttu-id="b0172-220">我们首先将创建一个脚本，然后可以检测到选择手势。</span><span class="sxs-lookup"><span data-stu-id="b0172-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="b0172-221">在中**脚本**文件夹中，创建一个名为脚本**GazeGestureManager**。</span><span class="sxs-lookup"><span data-stu-id="b0172-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="b0172-222">拖动**GazeGestureManager**拖动到脚本**OrigamiCollection**层次结构中的对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="b0172-223">打开**GazeGestureManager** Visual Studio 中编写脚本，并添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="b0172-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="b0172-224">在脚本文件夹中名为这次创建另一个脚本**SphereCommands**。</span><span class="sxs-lookup"><span data-stu-id="b0172-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="b0172-225">展开**OrigamiCollection**层次结构视图中的对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="b0172-226">拖动**SphereCommands**拖动到脚本**Sphere1**层次结构面板中的对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="b0172-227">拖动**SphereCommands**拖动到脚本**Sphere2**层次结构面板中的对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="b0172-228">在 Visual Studio 中打开脚本进行编辑，并将默认代码替换此为：</span><span class="sxs-lookup"><span data-stu-id="b0172-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="b0172-229">导出、 生成和应用部署到你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b0172-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b0172-230">查看其中一个球体。</span><span class="sxs-lookup"><span data-stu-id="b0172-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="b0172-231">执行选择手势并观看球体拖放到下面图面上。</span><span class="sxs-lookup"><span data-stu-id="b0172-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="b0172-232">第 4 章-语音</span><span class="sxs-lookup"><span data-stu-id="b0172-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="b0172-233">在本章中，我们将添加两个支持[语音命令](voice-input.md):"重置的 world"返回到其原始位置，则删除的球体和"删除球体"以使处于球体。</span><span class="sxs-lookup"><span data-stu-id="b0172-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0172-234">目标</span><span class="sxs-lookup"><span data-stu-id="b0172-234">Objectives</span></span>

* <span data-ttu-id="b0172-235">在背景中添加始终侦听语音命令。</span><span class="sxs-lookup"><span data-stu-id="b0172-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="b0172-236">创建一张全息图，待语音命令做出反应。</span><span class="sxs-lookup"><span data-stu-id="b0172-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0172-237">说明</span><span class="sxs-lookup"><span data-stu-id="b0172-237">Instructions</span></span>

* <span data-ttu-id="b0172-238">在中**脚本**文件夹中，创建一个名为脚本**SpeechManager**。</span><span class="sxs-lookup"><span data-stu-id="b0172-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="b0172-239">拖动**SpeechManager**拖动到脚本**OrigamiCollection**层次结构中的对象</span><span class="sxs-lookup"><span data-stu-id="b0172-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="b0172-240">打开**SpeechManager** Visual Studio 中的脚本。</span><span class="sxs-lookup"><span data-stu-id="b0172-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="b0172-241">为此代码复制并粘贴**SpeechManager.cs**并**全部保存**:</span><span class="sxs-lookup"><span data-stu-id="b0172-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="b0172-242">打开**SphereCommands** Visual Studio 中的脚本。</span><span class="sxs-lookup"><span data-stu-id="b0172-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="b0172-243">更新脚本，以读取，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b0172-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="b0172-244">导出、 生成和应用部署到你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b0172-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b0172-245">看到一个球体，就会说"**Drop 球体**"。</span><span class="sxs-lookup"><span data-stu-id="b0172-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="b0172-246">说"**重置世界**"将恢复到其初始位置。</span><span class="sxs-lookup"><span data-stu-id="b0172-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="b0172-247">第 5 章-空间声音</span><span class="sxs-lookup"><span data-stu-id="b0172-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="b0172-248">在本章中，我们将将音乐添加到应用程序中，然后触发特定操作的声音效果。</span><span class="sxs-lookup"><span data-stu-id="b0172-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="b0172-249">我们将使用[空间声音](spatial-sound.md)以便声音 3D 空间中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="b0172-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0172-250">目标</span><span class="sxs-lookup"><span data-stu-id="b0172-250">Objectives</span></span>

* <span data-ttu-id="b0172-251">听到全息在您的世界。</span><span class="sxs-lookup"><span data-stu-id="b0172-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0172-252">说明</span><span class="sxs-lookup"><span data-stu-id="b0172-252">Instructions</span></span>

* <span data-ttu-id="b0172-253">在顶部菜单中，Unity 选择**编辑 > 项目设置 > 音频**</span><span class="sxs-lookup"><span data-stu-id="b0172-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="b0172-254">在右侧的检查器窗格中，找到**Spatializer 插件**设置并选择**MS HRTF Spatializer**。</span><span class="sxs-lookup"><span data-stu-id="b0172-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="b0172-255">从**全息**文件夹中的项目面板中，拖动**环境**对象拖到**OrigamiCollection**层次结构面板中的对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="b0172-256">选择**OrigamiCollection**并找到**音频源**组件检查器面板中。</span><span class="sxs-lookup"><span data-stu-id="b0172-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="b0172-257">更改这些属性：</span><span class="sxs-lookup"><span data-stu-id="b0172-257">Change these properties:</span></span>
  * <span data-ttu-id="b0172-258">检查**Spatialize**属性。</span><span class="sxs-lookup"><span data-stu-id="b0172-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="b0172-259">检查**唤醒状态上播放**。</span><span class="sxs-lookup"><span data-stu-id="b0172-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="b0172-260">更改**空间 Blend**到**3D**通过将滑块拖到最右侧。</span><span class="sxs-lookup"><span data-stu-id="b0172-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="b0172-261">当移动滑块时，值应从 0 更改为 1 中。</span><span class="sxs-lookup"><span data-stu-id="b0172-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="b0172-262">检查**循环**属性。</span><span class="sxs-lookup"><span data-stu-id="b0172-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="b0172-263">展开**3D 声音设置**，并输入**0.1**有关**Doppler 级别**。</span><span class="sxs-lookup"><span data-stu-id="b0172-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="b0172-264">设置**卷卷绕**到**对数卷绕**。</span><span class="sxs-lookup"><span data-stu-id="b0172-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="b0172-265">设置**最大距离**到**20**。</span><span class="sxs-lookup"><span data-stu-id="b0172-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="b0172-266">在中**脚本**文件夹中，创建一个名为脚本**SphereSounds**。</span><span class="sxs-lookup"><span data-stu-id="b0172-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="b0172-267">拖放到**SphereSounds**到**Sphere1**并**Sphere2**层次结构中的对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="b0172-268">打开**SphereSounds** Visual Studio 中更新以下代码，并**全部保存**。</span><span class="sxs-lookup"><span data-stu-id="b0172-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="b0172-269">保存脚本，并返回到 Unity。</span><span class="sxs-lookup"><span data-stu-id="b0172-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="b0172-270">导出、 生成和应用部署到你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b0172-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b0172-271">移动更接近和最荒谬不过阶段并打开端端，若要听到的声音更改。</span><span class="sxs-lookup"><span data-stu-id="b0172-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="b0172-272">第 6 章-空间映射</span><span class="sxs-lookup"><span data-stu-id="b0172-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="b0172-273">现在，我们将使用[空间映射](spatial-mapping.md)在现实世界中的实际对象上放置游戏板。</span><span class="sxs-lookup"><span data-stu-id="b0172-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="b0172-274">目标</span><span class="sxs-lookup"><span data-stu-id="b0172-274">Objectives</span></span>

* <span data-ttu-id="b0172-275">将引入虚拟世界的现实世界。</span><span class="sxs-lookup"><span data-stu-id="b0172-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="b0172-276">将放置在全息其中它们对你最重要。</span><span class="sxs-lookup"><span data-stu-id="b0172-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0172-277">说明</span><span class="sxs-lookup"><span data-stu-id="b0172-277">Instructions</span></span>

* <span data-ttu-id="b0172-278">在 Unity 中，单击**全息**项目面板中的文件夹。</span><span class="sxs-lookup"><span data-stu-id="b0172-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="b0172-279">拖动**空间映射**到的根目录的资产**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="b0172-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="b0172-280">单击**空间映射**层次结构中的对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="b0172-281">在中**检查器面板**，更改下列属性：</span><span class="sxs-lookup"><span data-stu-id="b0172-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="b0172-282">检查**绘制 Visual 网格**框。</span><span class="sxs-lookup"><span data-stu-id="b0172-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="b0172-283">找到**绘制材料**并单击右侧的圆形。</span><span class="sxs-lookup"><span data-stu-id="b0172-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="b0172-284">类型"**线框**"顶部搜索字段中。</span><span class="sxs-lookup"><span data-stu-id="b0172-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="b0172-285">单击该结果，然后关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="b0172-285">Click on the result and then close the window.</span></span> <span data-ttu-id="b0172-286">时执行此操作时，应获取绘制材料的值设置为透明框架。</span><span class="sxs-lookup"><span data-stu-id="b0172-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="b0172-287">导出、 生成和应用部署到你 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="b0172-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="b0172-288">应用运行时，线框网格将覆盖在现实世界。</span><span class="sxs-lookup"><span data-stu-id="b0172-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="b0172-289">观看如何滚动球体将不会出现该阶段，注销再到在地板上 ！</span><span class="sxs-lookup"><span data-stu-id="b0172-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="b0172-290">现在我们将向您展示如何将 OrigamiCollection 移动到新位置：</span><span class="sxs-lookup"><span data-stu-id="b0172-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="b0172-291">在中**脚本**文件夹中，创建一个名为脚本**TapToPlaceParent**。</span><span class="sxs-lookup"><span data-stu-id="b0172-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="b0172-292">在中**层次结构**，展开**OrigamiCollection** ，然后选择**阶段**对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="b0172-293">拖动**TapToPlaceParent**到阶段对象上的脚本。</span><span class="sxs-lookup"><span data-stu-id="b0172-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="b0172-294">打开**TapToPlaceParent**脚本在 Visual Studio 中，并将其更新为如下：</span><span class="sxs-lookup"><span data-stu-id="b0172-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="b0172-295">导出、 生成和部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="b0172-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="b0172-296">现在您现在应能够将游戏放在特定位置，通过它在观望，使用选择手势然后将移至新位置，并再次使用选择的手势。</span><span class="sxs-lookup"><span data-stu-id="b0172-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="b0172-297">第 7 章 — Holographic 乐趣</span><span class="sxs-lookup"><span data-stu-id="b0172-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="b0172-298">目标</span><span class="sxs-lookup"><span data-stu-id="b0172-298">Objectives</span></span>

* <span data-ttu-id="b0172-299">显示进行 holographic underworld 的入口。</span><span class="sxs-lookup"><span data-stu-id="b0172-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="b0172-300">说明</span><span class="sxs-lookup"><span data-stu-id="b0172-300">Instructions</span></span>

<span data-ttu-id="b0172-301">现在，我们将向您展示如何以发现 holographic underworld:</span><span class="sxs-lookup"><span data-stu-id="b0172-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="b0172-302">从**全息**项目面板中的文件夹：</span><span class="sxs-lookup"><span data-stu-id="b0172-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="b0172-303">拖动**Underworld**到层次结构的子级**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="b0172-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0172-304">在中**脚本**文件夹中，创建一个名为脚本**HitTarget**。</span><span class="sxs-lookup"><span data-stu-id="b0172-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="b0172-305">在中**层次结构**，展开**OrigamiCollection**。</span><span class="sxs-lookup"><span data-stu-id="b0172-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="b0172-306">展开**阶段**对象，并选择**目标**对象 （蓝色风扇）。</span><span class="sxs-lookup"><span data-stu-id="b0172-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="b0172-307">拖动**HitTarget**拖动到脚本**目标**对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="b0172-308">打开**HitTarget**脚本在 Visual Studio 中，并将其更新为如下：</span><span class="sxs-lookup"><span data-stu-id="b0172-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="b0172-309">在 Unity 中，选择**目标**对象。</span><span class="sxs-lookup"><span data-stu-id="b0172-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="b0172-310">两个公共属性即会显示在**命中目标**组件和到我们的场景中的引用对象的需求：</span><span class="sxs-lookup"><span data-stu-id="b0172-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="b0172-311">拖动**Underworld**从**层次结构**到面板**Underworld**属性**命中目标**组件。</span><span class="sxs-lookup"><span data-stu-id="b0172-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="b0172-312">拖动**阶段**从**层次结构**到面板**隐藏的对象**属性**命中目标**组件。</span><span class="sxs-lookup"><span data-stu-id="b0172-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="b0172-313">导出、 生成和部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="b0172-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="b0172-314">将 Origami 集合放在地板上，然后使用选择手势进行删除球体。</span><span class="sxs-lookup"><span data-stu-id="b0172-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="b0172-315">当球达到目标 （蓝色风扇） 时，将发生爆炸式增长。</span><span class="sxs-lookup"><span data-stu-id="b0172-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="b0172-316">集合将被隐藏，到 underworld 漏洞会出现。</span><span class="sxs-lookup"><span data-stu-id="b0172-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="b0172-317">结束</span><span class="sxs-lookup"><span data-stu-id="b0172-317">The end</span></span>

<span data-ttu-id="b0172-318">就是本教程结束 ！</span><span class="sxs-lookup"><span data-stu-id="b0172-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="b0172-319">介绍了：</span><span class="sxs-lookup"><span data-stu-id="b0172-319">You learned:</span></span>

* <span data-ttu-id="b0172-320">如何在 Unity 中创建全息版应用。</span><span class="sxs-lookup"><span data-stu-id="b0172-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="b0172-321">如何使提供注视、 手势、 语音、 声音、 使用和空间的映射。</span><span class="sxs-lookup"><span data-stu-id="b0172-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="b0172-322">如何生成和使用 Visual Studio 部署应用。</span><span class="sxs-lookup"><span data-stu-id="b0172-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="b0172-323">现已准备好开始创建您自己 holographic 体验 ！</span><span class="sxs-lookup"><span data-stu-id="b0172-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="b0172-324">请参阅</span><span class="sxs-lookup"><span data-stu-id="b0172-324">See also</span></span>

* [<span data-ttu-id="b0172-325">MR 基础知识 101E:使用模拟器的完整项目</span><span class="sxs-lookup"><span data-stu-id="b0172-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="b0172-326">Gaze</span><span class="sxs-lookup"><span data-stu-id="b0172-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="b0172-327">手势</span><span class="sxs-lookup"><span data-stu-id="b0172-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="b0172-328">语音输入</span><span class="sxs-lookup"><span data-stu-id="b0172-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="b0172-329">空间声音</span><span class="sxs-lookup"><span data-stu-id="b0172-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="b0172-330">空间映射</span><span class="sxs-lookup"><span data-stu-id="b0172-330">Spatial mapping</span></span>](spatial-mapping.md)
