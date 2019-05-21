---
title: MR 空间 220-空间声音
description: 按照本演练使用 Unity、 Visual Studio 和 HoloLens 学习空间声音概念的详细信息进行编码操作。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 学院、 教程、 空间声音
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590397"
---
>[!NOTE]
><span data-ttu-id="fd3a8-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fd3a8-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fd3a8-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fd3a8-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fd3a8-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fd3a8-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="fd3a8-110">MR 空间 220:空间音效</span><span class="sxs-lookup"><span data-stu-id="fd3a8-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="fd3a8-111">[空间声音](spatial-sound.md)到全息 breathes 生活并为他们提供了在我们的世界中的存在。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="fd3a8-112">全息组成浅色和声音，和如果碰巧被忽视您全息，空间声音可以帮助您找到它们。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="fd3a8-113">空间声音不类似于典型的声音，您将听到广播，它是在 3D 空间中放置的声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="fd3a8-114">使用空间的声音，您可以使声音起来像是后端，旁边，或甚至在您头上全息 ！</span><span class="sxs-lookup"><span data-stu-id="fd3a8-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="fd3a8-115">在本课程中，你将：</span><span class="sxs-lookup"><span data-stu-id="fd3a8-115">In this course, you will:</span></span>

* <span data-ttu-id="fd3a8-116">配置开发环境，使用 Microsoft 空间声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="fd3a8-117">使用空间声音来增强的交互。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="fd3a8-118">与空间映射结合使用空间的声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="fd3a8-119">了解合理的设计和混合使用最佳做法。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="fd3a8-120">使用声音来增强特殊效果并将用户带到混合现实世界。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="fd3a8-121">设备支持</span><span class="sxs-lookup"><span data-stu-id="fd3a8-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fd3a8-122">课程</span><span class="sxs-lookup"><span data-stu-id="fd3a8-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fd3a8-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fd3a8-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fd3a8-124"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="fd3a8-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="fd3a8-125">MR 空间 220:空间音效</span><span class="sxs-lookup"><span data-stu-id="fd3a8-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="fd3a8-126">✔️</span><span class="sxs-lookup"><span data-stu-id="fd3a8-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="fd3a8-127">✔️</span><span class="sxs-lookup"><span data-stu-id="fd3a8-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="fd3a8-128">开始之前</span><span class="sxs-lookup"><span data-stu-id="fd3a8-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="fd3a8-129">系统必备</span><span class="sxs-lookup"><span data-stu-id="fd3a8-129">Prerequisites</span></span>

* <span data-ttu-id="fd3a8-130">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="fd3a8-131">一些基本C#编程功能。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="fd3a8-132">您应当已完成[MR 基础知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="fd3a8-133">HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="fd3a8-134">项目文件</span><span class="sxs-lookup"><span data-stu-id="fd3a8-134">Project files</span></span>

* <span data-ttu-id="fd3a8-135">下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)所需的项目。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="fd3a8-136"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="fd3a8-137">如果你仍然需要 Unity 5.6 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="fd3a8-138">此版本中可能不再保持最新状态。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="fd3a8-139">如果你仍然需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="fd3a8-140"> 此版本中可能不再保持最新状态。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="fd3a8-141">如果你仍然需要 Unity 5.4 的支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="fd3a8-142"> 此版本中可能不再保持最新状态。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="fd3a8-143">取消存档到您的桌面或其他轻松地访问位置的文件。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="fd3a8-144">如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="fd3a8-145">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="fd3a8-145">Errata and Notes</span></span>

* <span data-ttu-id="fd3a8-146">"启用仅我的代码"必须禁用 (*未选中*) 在 Visual Studio 工具-> 选项-> 调试以便你的代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="fd3a8-147">第 1 章-Unity 安装程序</span><span class="sxs-lookup"><span data-stu-id="fd3a8-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="fd3a8-148">目标</span><span class="sxs-lookup"><span data-stu-id="fd3a8-148">Objectives</span></span>

* <span data-ttu-id="fd3a8-149">Unity 的声音配置更改为使用 Microsoft 空间声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="fd3a8-150">将三维声音添加到 Unity 中的对象。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="fd3a8-151">说明</span><span class="sxs-lookup"><span data-stu-id="fd3a8-151">Instructions</span></span>

* <span data-ttu-id="fd3a8-152">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-152">Start Unity.</span></span>
* <span data-ttu-id="fd3a8-153">选择**打开**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-153">Select **Open**.</span></span>
* <span data-ttu-id="fd3a8-154">导航到你的桌面和查找文件夹你之前未存档。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="fd3a8-155">单击**Starting\Decibel**文件夹，然后按**选择文件夹**按钮。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="fd3a8-156">等待要在 Unity 中加载的项目。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="fd3a8-157">在中 **项目**面板中，打开**Scenes\Decibel.unity**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="fd3a8-158">在中**层次结构**面板中，展开**HologramCollection** ，然后选择**P0LY**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="fd3a8-159">在检查器中，展开**AudioSource**请注意，没有任何**Spatialize**复选框。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="fd3a8-160">默认情况下，Unity 不会加载 spatializer 插件。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="fd3a8-161">以下步骤将在项目中启用空间声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="fd3a8-162">在 Unity 的顶部菜单中，转到**编辑 > 项目设置 > 音频**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="fd3a8-163">查找**Spatializer 插件**下拉列表中，然后选择**MS HRTF Spatializer**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="fd3a8-164">在中**层次结构**面板中，选择**HologramCollection > P0LY**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="fd3a8-165">在中**Inspector**面板中，找到**音频源**组件。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="fd3a8-166">检查**Spatialize**复选框。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="fd3a8-167">拖动**空间 Blend**滑块一直向**3D**，或输入**1**编辑框中。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="fd3a8-168">现在，Unity 中生成项目并在 Visual Studio 中配置该解决方案。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="fd3a8-169">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="fd3a8-170">单击**添加打开场景**添加场景。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="fd3a8-171">选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="fd3a8-172">如果您专门为 HoloLens 开发，设置**目标设备**到**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="fd3a8-173">否则，将其保持打开**任何设备**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="fd3a8-174">请确保**生成类型**设置为**D3D**并**SDK**设置为**最新安装**（应为 16299 或更高版本的 SDK）。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="fd3a8-175">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-175">Click **Build**.</span></span>
7. <span data-ttu-id="fd3a8-176">创建**新文件夹**名为"应用"。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="fd3a8-177">单击一下**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="fd3a8-178">按**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-178">Press **Select Folder**.</span></span>

<span data-ttu-id="fd3a8-179">Unity 完成操作后，将出现一个文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="fd3a8-180">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="fd3a8-181">打开**分贝 Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="fd3a8-182">如果部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="fd3a8-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="fd3a8-183">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x86**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="fd3a8-184">单击向下箭头旁边的本地计算机按钮，然后选择**远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="fd3a8-185">输入**HoloLens 设备 IP 地址**并将身份验证模式设置为**通用 （未加密的协议）**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="fd3a8-186">单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-186">Click **Select**.</span></span> <span data-ttu-id="fd3a8-187">如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="fd3a8-188">在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="fd3a8-189">如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device---hololens-1st-gen)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="fd3a8-190">如果部署到沉浸式头戴式：</span><span class="sxs-lookup"><span data-stu-id="fd3a8-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="fd3a8-191">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x64**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="fd3a8-192">请确保部署目标设置为**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="fd3a8-193">在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="fd3a8-194">第 2 章-空间声音和交互</span><span class="sxs-lookup"><span data-stu-id="fd3a8-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="fd3a8-195">目标</span><span class="sxs-lookup"><span data-stu-id="fd3a8-195">Objectives</span></span>

* <span data-ttu-id="fd3a8-196">增强使用声音的 hologram 真实性。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="fd3a8-197">直接使用声音的用户的视线移动。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="fd3a8-198">提供使用声音的手势反馈。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="fd3a8-199">第 1 部分-增强真实性</span><span class="sxs-lookup"><span data-stu-id="fd3a8-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="fd3a8-200">关键概念</span><span class="sxs-lookup"><span data-stu-id="fd3a8-200">Key Concepts</span></span>

* <span data-ttu-id="fd3a8-201">Spatialize 全息图声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="fd3a8-202">声音源应置于全息图上的适当位置。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="fd3a8-203">将声音的适当位置取决于全息图。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="fd3a8-204">例如，如果全息图的人，声音源应靠近嘴巴不使用英尺。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="fd3a8-205">说明</span><span class="sxs-lookup"><span data-stu-id="fd3a8-205">Instructions</span></span>

<span data-ttu-id="fd3a8-206">以下说明将附加到一张全息图 spatialized 的声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="fd3a8-207">在中**层次结构**面板中，展开**HologramCollection** ，然后选择**P0LY**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="fd3a8-208">中**Inspector**面板**AudioSource**，旁边单击该圆圈**AudioClip** ，然后选择**PolyHover**在弹出窗口中。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="fd3a8-209">单击该圆圈旁边**输出**，然后选择**SoundEffects**在弹出窗口中。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="fd3a8-210">项目级分贝使用 Unity **AudioMixer**组件以便调整的声音的组的声音级别。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="fd3a8-211">通过分组声音这种方式，可以同时保持相对每个声音的音量调整总数量。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="fd3a8-212">在中**AudioSource**，展开**3D 声音设置**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="fd3a8-213">设置**Doppler 级别**到**0**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="fd3a8-214">无需禁用更改引起的运动 （不管是全息图或用户） 的间距的级别设置 Doppler。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="fd3a8-215">Doppler 一个典型示例是快速发展的汽车。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="fd3a8-216">随着汽车的临近保持静止的侦听器，该引擎的音调上升。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="fd3a8-217">它通过侦听器后，与距离会降低间距。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="fd3a8-218">第 2 部分-将定向用户的视线移动</span><span class="sxs-lookup"><span data-stu-id="fd3a8-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="fd3a8-219">关键概念</span><span class="sxs-lookup"><span data-stu-id="fd3a8-219">Key Concepts</span></span>

* <span data-ttu-id="fd3a8-220">使用声音呼吁人们关注重要全息。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="fd3a8-221">耳朵帮助指导眼睛应在其中查找操作。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="fd3a8-222">大脑有一些已学习的预期。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="fd3a8-223">已学习的期望的一个示例是鸟通常是上面的人。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="fd3a8-224">如果用户能听到鸟声音，其第一反应是查找。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="fd3a8-225">放置鸟如下用户可能会导致它们面向正确的方向的声音，但无法找到基于的无需查找的假定条件下的全息图。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="fd3a8-226">说明</span><span class="sxs-lookup"><span data-stu-id="fd3a8-226">Instructions</span></span>

<span data-ttu-id="fd3a8-227">下面的说明启用 P0LY 隐藏后端，以便可以使用声音来查找全息图。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="fd3a8-228">在中**层次结构**面板中，选择**经理**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="fd3a8-229">在中**Inspector**面板中，找到**语音输入处理程序**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="fd3a8-230">在中**语音输入处理程序**，展开**转隐藏**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="fd3a8-231">更改**没有函数**到**PolyActions.GoHide**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![关键字：转隐藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="fd3a8-233">第 3 部分-手势的反馈</span><span class="sxs-lookup"><span data-stu-id="fd3a8-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="fd3a8-234">关键概念</span><span class="sxs-lookup"><span data-stu-id="fd3a8-234">Key Concepts</span></span>

* <span data-ttu-id="fd3a8-235">为用户提供使用声音正手势确认</span><span class="sxs-lookup"><span data-stu-id="fd3a8-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="fd3a8-236">不会给用户的方式的过度很大的声音 get</span><span class="sxs-lookup"><span data-stu-id="fd3a8-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="fd3a8-237">最佳的细微声音工作做不会掩盖体验</span><span class="sxs-lookup"><span data-stu-id="fd3a8-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="fd3a8-238">说明</span><span class="sxs-lookup"><span data-stu-id="fd3a8-238">Instructions</span></span>

* <span data-ttu-id="fd3a8-239">在中**层次结构**面板中，展开**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="fd3a8-240">展开**EnergyHub** ，然后选择**Base**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="fd3a8-241">在中**Inspector**面板中，单击**添加组件**，并添加**笔势声音处理程序**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="fd3a8-242">中**笔势声音处理程序**，单击旁边的圆形可**导航开始剪辑**并**导航更新剪辑**，然后选择**RotateClick**从两个弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="fd3a8-243">双击"GestureSoundHandler"若要在 Visual Studio 中加载。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="fd3a8-244">声音笔势处理程序执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="fd3a8-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="fd3a8-245">创建和配置**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="fd3a8-246">位置**AudioSource**的相应位置处**GameObject**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="fd3a8-247">播放**AudioClip**与手势相关。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="fd3a8-248">生成和部署</span><span class="sxs-lookup"><span data-stu-id="fd3a8-248">Build and Deploy</span></span>

1. <span data-ttu-id="fd3a8-249">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="fd3a8-250">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-250">Click **Build**.</span></span>
3. <span data-ttu-id="fd3a8-251">单击一下**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="fd3a8-252">按**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-252">Press **Select Folder**.</span></span>

<span data-ttu-id="fd3a8-253">检查工具栏上显示"发布"、"x86"或"x64"和"远程设备"。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="fd3a8-254">如果没有，这是 Visual Studio 的编码的实例。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="fd3a8-255">您可能需要重新打开应用程序文件夹中的解决方案。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="fd3a8-256">如果系统提示，请重新加载项目文件。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="fd3a8-257">与前面一样，从 Visual Studio 进行部署。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="fd3a8-258">后部署该应用程序：</span><span class="sxs-lookup"><span data-stu-id="fd3a8-258">After the application is deployed:</span></span>

* <span data-ttu-id="fd3a8-259">观察随着移动 P0LY 声音的更改。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="fd3a8-260">说 *"转到隐藏"* 使 P0LY 移到后端的位置。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="fd3a8-261">找到它的声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-261">Find it by the sound.</span></span>
* <span data-ttu-id="fd3a8-262">注视能源中心的基础。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="fd3a8-263">点击和拖动左或向右旋转全息图，请注意如何产生咔嗒声确认手势。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="fd3a8-264">注意：没有将与你的尾随的文本面板。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="fd3a8-265">这将包含可以使用在本课程中可用的语音命令。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="fd3a8-266">第 3 章 — 空间声音和空间映射</span><span class="sxs-lookup"><span data-stu-id="fd3a8-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="fd3a8-267">目标</span><span class="sxs-lookup"><span data-stu-id="fd3a8-267">Objectives</span></span>

* <span data-ttu-id="fd3a8-268">确认全息和实际使用声音之间的交互。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="fd3a8-269">遮蔽使用物理世界的声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="fd3a8-270">第 1 部分-物理世界交互</span><span class="sxs-lookup"><span data-stu-id="fd3a8-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="fd3a8-271">关键概念</span><span class="sxs-lookup"><span data-stu-id="fd3a8-271">Key Concepts</span></span>

* <span data-ttu-id="fd3a8-272">物理对象通常发出声音时遇到一个面或另一个对象。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="fd3a8-273">声音应该是可以在进行适当的上下文。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="fd3a8-274">例如，在表上设置一杯应发出比删除上一种裸机博尔德县更安静声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="fd3a8-275">说明</span><span class="sxs-lookup"><span data-stu-id="fd3a8-275">Instructions</span></span>

* <span data-ttu-id="fd3a8-276">在中**层次结构**面板中，展开**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="fd3a8-277">展开**EnergyHub**，选择**Base**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="fd3a8-278">在中**Inspector**面板中，单击**添加组件**，并添加**点击到位置与声音和操作**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="fd3a8-279">在中**到用声音和操作的位置点击**:</span><span class="sxs-lookup"><span data-stu-id="fd3a8-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="fd3a8-280">检查**父置于点击**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="fd3a8-281">设置**放置声音**到**位置**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="fd3a8-282">设置**Pickup 声音**到**Pickup**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="fd3a8-283">按 + 下同时底部**上 Pickup 操作**并**上放置操作**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="fd3a8-284">从到场景拖动 EnergyHub **None （对象）** 字段。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="fd3a8-285">下**上 Pickup 操作**，单击**否函数** -> **EnergyHubBase** -> **ResetAnimation**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="fd3a8-286">下**上放置操作**，单击**否函数** -> **EnergyHubBase** -> **OnSelect**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![点击到用声音和操作的位置](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="fd3a8-288">第 2 部分-声音封闭</span><span class="sxs-lookup"><span data-stu-id="fd3a8-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="fd3a8-289">关键概念</span><span class="sxs-lookup"><span data-stu-id="fd3a8-289">Key Concepts</span></span>

* <span data-ttu-id="fd3a8-290">声音，光，如可以封闭的像素。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="fd3a8-291">一个典型示例是 concert hall。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-291">A classic example is a concert hall.</span></span> <span data-ttu-id="fd3a8-292">当侦听器都可以顺利之外 hall 和门已关闭，muffled 音乐听起来。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="fd3a8-293">此外还有通常种数量缩减。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="fd3a8-294">在门打开时，在实际容量听到声音的整个范围。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="fd3a8-295">高频率声音通常多个低频率吸收。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="fd3a8-296">说明</span><span class="sxs-lookup"><span data-stu-id="fd3a8-296">Instructions</span></span>

* <span data-ttu-id="fd3a8-297">在中**层次结构**面板中，展开**HologramCollection** ，然后选择**P0LY**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="fd3a8-298">在中**Inspector**面板中，单击**添加组件**，并添加**音频发射器**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="fd3a8-299">音频发射器类提供了以下功能：</span><span class="sxs-lookup"><span data-stu-id="fd3a8-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="fd3a8-300">将任何更改还原到的卷**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="fd3a8-301">执行**Physics.RaycastNonAlloc**从用户的位置的方向**GameObject**所属**AudioEmitter**附加。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="fd3a8-302">RaycastNonAlloc 方法作为一种性能优化用于限制分配，以及返回的结果数。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="fd3a8-303">每个**IAudioInfluencer**遇到调用**ApplyEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="fd3a8-304">每个以前**IAudioInfluencer** ，它是不会再遇到的调用**RemoveEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="fd3a8-305">请注意，AudioEmitter 上更新的人类时间刻度，而不是基于每个帧来。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="fd3a8-306">这是因为人们通常不会移动速度足以处理要比每季度或约半秒钟更频繁地更新的效果。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="fd3a8-307">全息快速从一个位置到另一个该 teleport 可能会中断视觉效果。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="fd3a8-308">在中**层次结构**面板中，展开**HologramCollection**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="fd3a8-309">展开**EnergyHub** ，然后选择**BlobOutside**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="fd3a8-310">在中**Inspector**面板中，单击**添加组件**，并添加**音频 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="fd3a8-311">在中**音频 Occluder**，请设置**截止频率**到**1500年**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="fd3a8-312">此设置将限制 AudioSource 频率到 1500 Hz 和更低版本。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="fd3a8-313">设置**卷传递**到**0.9**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="fd3a8-314">此设置可 AudioSource 量减少到 90%的当前级别。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="fd3a8-315">音频 Occluder 实现 IAudioInfluencer 到：</span><span class="sxs-lookup"><span data-stu-id="fd3a8-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="fd3a8-316">将封闭效果使用**AudioLowPassFilter**哪些获取附加到**AudioSource**托管的购买**AudioEmitter**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="fd3a8-317">适用于 AudioSource 卷衰减。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="fd3a8-318">通过设置非特定语言的截止频率并禁用筛选器会禁用效果。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="fd3a8-319">使用作为非特定语言的频率是 22 kHz (22000 Hz)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="fd3a8-320">由于上面的名义上的最大频率可以听到的声音对此进行任何明显影响人耳选择了此频率。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="fd3a8-321">在中**层次结构**面板中，选择**SpatialMapping**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="fd3a8-322">在中**Inspector**面板中，单击**添加组件**，并添加**音频 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="fd3a8-323">在中**音频 Occluder**，请设置**截止频率**到**750**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="fd3a8-324">当多个 occluders 位于中的用户之间的路径和**AudioEmitter**，最低频率应用于筛选器。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="fd3a8-325">设置**卷传递**到**0.75**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="fd3a8-326">当多个 occluders 位于中的用户之间的路径和**AudioEmitter**，卷通过应用附加。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="fd3a8-327">在中**层次结构**面板中，选择**经理**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="fd3a8-328">在中**Inspector**面板中，展开**语音输入处理程序**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="fd3a8-329">在中**语音输入处理程序**，展开**转费用**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="fd3a8-330">更改**没有函数**到**PolyActions.GoCharge**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![关键字：转费用](images/gocharge.png)

* <span data-ttu-id="fd3a8-332">展开**此处**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="fd3a8-333">更改**没有函数**到**PolyActions.ComeBack**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![关键字：过来这里](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="fd3a8-335">生成和部署</span><span class="sxs-lookup"><span data-stu-id="fd3a8-335">Build and Deploy</span></span>

* <span data-ttu-id="fd3a8-336">与前面一样，Unity 中的项目在构建和部署 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="fd3a8-337">后部署该应用程序：</span><span class="sxs-lookup"><span data-stu-id="fd3a8-337">After the application is deployed:</span></span>

* <span data-ttu-id="fd3a8-338">说 *"转费用"* 具有 P0LY 输入能源中心。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="fd3a8-339">请注意声音中的更改。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-339">Note the change in the sound.</span></span> <span data-ttu-id="fd3a8-340">它应听起来 muffled 和有点更安静。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="fd3a8-341">如果能够自行定位与墙或其他您与能源中心之间的对象，您应注意到进一步 muffling 因为现实世界的封闭声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="fd3a8-342">说 *"出现在此处"* 具有 P0LY 保留能源中心并准备好将自身定位。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="fd3a8-343">请注意 P0LY 退出能源中心后，删除声音的阻挡物。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="fd3a8-344">如果您依然是听力不好的阻挡物，P0LY 可能封闭的现实世界中。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="fd3a8-345">尝试移动以确保有到 P0LY 清楚的认识。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="fd3a8-346">第 3 部分-聊天室模型</span><span class="sxs-lookup"><span data-stu-id="fd3a8-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="fd3a8-347">关键概念</span><span class="sxs-lookup"><span data-stu-id="fd3a8-347">Key Concepts</span></span>

* <span data-ttu-id="fd3a8-348">空间大小提供张潜意识贡献声音本地化的队列。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="fd3a8-349">每个设置的空间模型-**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="fd3a8-350">[Unity 的 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)聊天室模式设置为提供代码。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="fd3a8-351">混合现实体验，选择最适合的实际空间空间模型。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="fd3a8-352">如果要创建的虚拟现实方案，选择最适合虚拟环境的房间模型。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="fd3a8-353">第 4 章-合理的设计</span><span class="sxs-lookup"><span data-stu-id="fd3a8-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="fd3a8-354">目标</span><span class="sxs-lookup"><span data-stu-id="fd3a8-354">Objectives</span></span>

* <span data-ttu-id="fd3a8-355">了解有关有效可靠的设计注意事项。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="fd3a8-356">了解混合技术和指导原则。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="fd3a8-357">第 1 部分-声音和体验设计</span><span class="sxs-lookup"><span data-stu-id="fd3a8-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="fd3a8-358">本部分讨论关键声音和体验设计注意事项和指南。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="fd3a8-359">规范化听上去</span><span class="sxs-lookup"><span data-stu-id="fd3a8-359">Normalize all sounds</span></span>

<span data-ttu-id="fd3a8-360">这不需要使用特殊大小写的代码，以调整每个声音，可能会非常耗时的音量级别，并限制能够轻松地更新声音文件。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="fd3a8-361">针对无约束体验的设计</span><span class="sxs-lookup"><span data-stu-id="fd3a8-361">Design for an untethered experience</span></span>

<span data-ttu-id="fd3a8-362">HoloLens 是完全包含、 无约束全息版的计算机。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="fd3a8-363">你的用户可以并将使用你移动时的体验。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="fd3a8-364">请确保测试音频混合周围的每个步骤。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="fd3a8-365">发出声音从你全息上的逻辑位置</span><span class="sxs-lookup"><span data-stu-id="fd3a8-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="fd3a8-366">在现实生活中，dog 不会从其结尾吠和人的语音不是来自他/她英尺。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="fd3a8-367">避免从意外部分你全息发出声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="fd3a8-368">小全息是几何的合乎情理中心发出的声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="fd3a8-369">熟悉声音进行最本地化</span><span class="sxs-lookup"><span data-stu-id="fd3a8-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="fd3a8-370">人类声音和音乐也非常易于本地化。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="fd3a8-371">如果有人调用你的名称，您就能够非常准确地远离确定从语音是何种方向和如何。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="fd3a8-372">较短的不熟悉的声音是更难进行本地化。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="fd3a8-373">要了解的用户的期望</span><span class="sxs-lookup"><span data-stu-id="fd3a8-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="fd3a8-374">生活体验起的作用我们能够标识声音的位置。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="fd3a8-375">这是一个人的语音为何特别易于本地化的原因。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="fd3a8-376">请务必将放置在声音时，应注意用户的已学习的期望。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="fd3a8-377">例如，当有人会听到一鸟首歌曲时它们通常看起来，因为鸟往往上面直通 （飞编译或在树中）。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="fd3a8-378">不常见的声音，按正确方向打开但查找中错误的垂直方向，并会变得混淆或感到沮丧时找不到全息图的用户。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="fd3a8-379">避免隐藏的发射器</span><span class="sxs-lookup"><span data-stu-id="fd3a8-379">Avoid hidden emitters</span></span>

<span data-ttu-id="fd3a8-380">在现实生活中，如果我们听到声音，我们可以通常确定发出声音的对象。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="fd3a8-381">这还应包含在你的体验，则返回 true。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="fd3a8-382">它可以会为用户听到声音，知道从哪里声音产生非常令其不安，不能以查看对象。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="fd3a8-383">有一些例外情况，此原则。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="fd3a8-384">例如，如 crickets 字段中的环境声音不需要可见。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="fd3a8-385">生活体验为我们提供了熟悉这些声音而无需以查看它的源。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="fd3a8-386">第 2 部分-混音</span><span class="sxs-lookup"><span data-stu-id="fd3a8-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="fd3a8-387">目标为 70%卷上 HoloLens 混合</span><span class="sxs-lookup"><span data-stu-id="fd3a8-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="fd3a8-388">混合的现实体验支持全息现实世界中出现。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="fd3a8-389">它们还应允许实际声音，以提出反馈意见。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="fd3a8-390">70%卷目标可让用户了解其周围世界以及您的体验的声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="fd3a8-391">在 100%卷 HoloLens 应淹没出外部声音</span><span class="sxs-lookup"><span data-stu-id="fd3a8-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="fd3a8-392">卷级别为 100%是类似于虚拟现实体验。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="fd3a8-393">您可以看到，用户被传输到一个不同的世界。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="fd3a8-394">相同应为 true 时传递语音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="fd3a8-395">使用 Unity AudioMixer 调整类别的声音</span><span class="sxs-lookup"><span data-stu-id="fd3a8-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="fd3a8-396">在设计您的混合时，最好经常创建声音类别，并且能够以增大或减小其作为一个单元的卷。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="fd3a8-397">这将启用对整体组合的快速而简单的更改时保留的每个声音相对的级别。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="fd3a8-398">常见类别包括：声音效果、 环境、 语音旁白和背景音乐。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="fd3a8-399">基于用户的视线移动混合声音</span><span class="sxs-lookup"><span data-stu-id="fd3a8-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="fd3a8-400">通常可用于更改声音的组合在功能上的位置基于用户 （或不是） 查找。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="fd3a8-401">此方法的一个常见用途是减少全息之外 Holographic 帧以方便用户将精力集中在它们的前面的信息上的音量级别。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="fd3a8-402">另一个用途是声音的以提高突出用户的一个重要事件的音量。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="fd3a8-403">构建您的混合</span><span class="sxs-lookup"><span data-stu-id="fd3a8-403">Building your mix</span></span>

<span data-ttu-id="fd3a8-404">在生成您的混合时，建议开始体验的背景音频，添加层根据重要性。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="fd3a8-405">通常情况下，这会导致要比之前更大的每一层。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="fd3a8-406">期待您的混合会作为反转漏斗图中，使用最不重要 （和通常 quietest 声音） 在底部，我们建议结构您混合使用类似于下面的关系图。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![声音组合结构](images/soundlevels.png)

<span data-ttu-id="fd3a8-408">语音转移是一个有趣话题。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="fd3a8-409">基于要创建的体验上你可能想让立体声 （未本地化） 功能或 spatialize 语音转移。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="fd3a8-410">两个 Microsoft 发布体验说明每个方案的极好示例。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="fd3a8-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)通过使用立体声语音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="fd3a8-412">讲述人描述时查看的位置，声音将是一致，并且不会不随用户的位置。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="fd3a8-413">这使讲述人来描述而无需离开环境 spatialized 声音拍摄的场景。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="fd3a8-414">[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)形式的侦探通过利用 spatialized 的语音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="fd3a8-415">侦探的语音使用以帮助使用户注意到了重要的启示，就像实际的人是在聊天室中。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="fd3a8-416">这使解决神秘的深入体验更有意义。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="fd3a8-417">第 3-性能</span><span class="sxs-lookup"><span data-stu-id="fd3a8-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="fd3a8-418">CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="fd3a8-418">CPU usage</span></span>

<span data-ttu-id="fd3a8-419">时使用的空间声音，10-12 发射器将占用大约 12%的 CPU。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="fd3a8-420">Stream 长音频文件</span><span class="sxs-lookup"><span data-stu-id="fd3a8-420">Stream long audio files</span></span>

<span data-ttu-id="fd3a8-421">音频数据可能很大，尤其是在常用的采样速率 (44.1 和 48 kHz)。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="fd3a8-422">一般规则是应该传输时间超过 5-10 秒的音频文件以减少应用程序内存使用量。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="fd3a8-423">在 Unity 中，可以将标记中的文件导入设置的流式处理的音频文件。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![音频导入设置](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="fd3a8-425">第 5 章-特殊效果</span><span class="sxs-lookup"><span data-stu-id="fd3a8-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="fd3a8-426">目标</span><span class="sxs-lookup"><span data-stu-id="fd3a8-426">Objectives</span></span>

* <span data-ttu-id="fd3a8-427">将深度添加到"魔力 Windows"。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="fd3a8-428">将用户引入虚拟世界。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="fd3a8-429">Magic Windows</span><span class="sxs-lookup"><span data-stu-id="fd3a8-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="fd3a8-430">关键概念</span><span class="sxs-lookup"><span data-stu-id="fd3a8-430">Key Concepts</span></span>

* <span data-ttu-id="fd3a8-431">到隐藏的世界上创建视图，是极具视觉表现力。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="fd3a8-432">通过添加音频效果，一张全息图或用户是隐藏的世界附近时增强真实性。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="fd3a8-433">说明</span><span class="sxs-lookup"><span data-stu-id="fd3a8-433">Instructions</span></span>

* <span data-ttu-id="fd3a8-434">在中**层次结构**面板中，展开**HologramCollection** ，然后选择**Underworld**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="fd3a8-435">展开**Underworld** ，然后选择**VoiceSource**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="fd3a8-436">在中**Inspector**面板中，单击**添加组件**，并添加**用户语音效果**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="fd3a8-437">**AudioSource**组件将添加到**VoiceSource**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="fd3a8-438">在中**AudioSource**，请设置**输出**到**UserVoice (Mixer)**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="fd3a8-439">检查**Spatialize**复选框。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="fd3a8-440">拖动**空间 Blend**滑块一直向**3D**，或输入**1**编辑框中。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="fd3a8-441">展开**声音的三维设置**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="fd3a8-442">设置**Doppler 级别**到**0**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="fd3a8-443">在中**用户语音效果**，请设置**父对象**到**Underworld**从场景。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="fd3a8-444">设置**最大距离**到**1**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="fd3a8-445">设置**最大距离**告知**用户语音效果**接近程度的用户必须对父对象之前已启用的效果。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="fd3a8-446">在中**用户语音效果**，展开**合唱团参数**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="fd3a8-447">设置**深度**到**0.1**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="fd3a8-448">设置**点击 1 个卷**，**点击 2 卷**并**点击 3 个卷**到**0.8**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="fd3a8-449">设置**原生卷**到**0.5**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="fd3a8-450">以前的设置配置 Unity 的参数**AudioChorusFilter**用于将丰富功能添加到用户的声音。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="fd3a8-451">在中**用户语音效果**，展开**Echo 参数**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="fd3a8-452">设置**延迟**到**300**</span><span class="sxs-lookup"><span data-stu-id="fd3a8-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="fd3a8-453">设置**Decay 比率**到**0.2**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="fd3a8-454">设置**原生卷**到**0**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="fd3a8-455">以前的设置配置 Unity 的参数**AudioEchoFilter**用于导致用户的声音回显。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="fd3a8-456">用户语音效果脚本负责：</span><span class="sxs-lookup"><span data-stu-id="fd3a8-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="fd3a8-457">测量的用户之间的距离并**GameObject**脚本所附加到。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="fd3a8-458">确定用户是否面向**GameObject**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="fd3a8-459">用户必须面向的 GameObject，而不考虑距离，对于要启用的效果。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="fd3a8-460">将应用和配置**AudioChorusFilter**和一个**AudioEchoFilter**到**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="fd3a8-461">通过禁用筛选器中禁用效果。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="fd3a8-462">用户语音效果使用的 Mic Stream 选择器组件，从[Unity 的 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)，以选择高质量的语音流并将其路由到 Unity 的音频系统。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="fd3a8-463">在中**层次结构**面板中，选择**经理**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="fd3a8-464">在中**Inspector**面板中，展开**语音输入处理程序**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="fd3a8-465">在中**语音输入处理程序**，展开**显示 Underworld**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="fd3a8-466">更改**没有函数**到**UnderworldBase.OnEnable**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![关键字：显示 Underworld](images/showunderworld.png)

* <span data-ttu-id="fd3a8-468">展开**隐藏 Underworld**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="fd3a8-469">更改**没有函数**到**UnderworldBase.OnDisable**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![关键字：隐藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="fd3a8-471">生成和部署</span><span class="sxs-lookup"><span data-stu-id="fd3a8-471">Build and Deploy</span></span>

* <span data-ttu-id="fd3a8-472">与前面一样，Unity 中的项目在构建和部署 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="fd3a8-473">后部署该应用程序：</span><span class="sxs-lookup"><span data-stu-id="fd3a8-473">After the application is deployed:</span></span>

* <span data-ttu-id="fd3a8-474">人脸的图面 （墙、 floor、 表） 和 say *"显示 Underworld"*。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="fd3a8-475">将显示 underworld 并且所有其他全息将被隐藏。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="fd3a8-476">如果您看不到 underworld，确保正面临着实际的图面。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="fd3a8-477">方法在 1 米以内的 underworld 全息图并开始交谈。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="fd3a8-478">现在是应用于语音的音频效果 ！</span><span class="sxs-lookup"><span data-stu-id="fd3a8-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="fd3a8-479">打开 underworld 离开并请注意，不会再应用效果的方式。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="fd3a8-480">说 *"隐藏 Underworld"* 隐藏 underworld。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="fd3a8-481">将隐藏 underworld 并且以前隐藏的所有全息将重新都出现。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="fd3a8-482">结束</span><span class="sxs-lookup"><span data-stu-id="fd3a8-482">The End</span></span>

<span data-ttu-id="fd3a8-483">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="fd3a8-483">Congratulations!</span></span> <span data-ttu-id="fd3a8-484">你现在已经完成**MR 空间 220:空间声音**。</span><span class="sxs-lookup"><span data-stu-id="fd3a8-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="fd3a8-485">侦听世界上并通过声音将你的体验 ！</span><span class="sxs-lookup"><span data-stu-id="fd3a8-485">Listen to the world and bring your experiences to life with sound!</span></span>
