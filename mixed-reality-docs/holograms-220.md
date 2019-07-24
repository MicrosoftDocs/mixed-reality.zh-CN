---
title: MR 空间 220-空间音效
description: 按照此编码演练操作, 使用 Unity、Visual Studio 和 HoloLens 来了解空间音效概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 学院, 教程, 空间音效
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526939"
---
>[!NOTE]
><span data-ttu-id="cda5d-104">混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="cda5d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="cda5d-105">因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="cda5d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="cda5d-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="cda5d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="cda5d-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="cda5d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="cda5d-108">将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="cda5d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="cda5d-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="cda5d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="cda5d-110">MR 空间 220:空间音效</span><span class="sxs-lookup"><span data-stu-id="cda5d-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="cda5d-111">[空间音效](spatial-sound.md)breathes 影像, 并使其在世界中存在。</span><span class="sxs-lookup"><span data-stu-id="cda5d-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="cda5d-112">全息影像同时包含光和声音, 如果你发生丢失全息影像的情况, 空间音效可以帮助你找到它们。</span><span class="sxs-lookup"><span data-stu-id="cda5d-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="cda5d-113">空间音效并不像您在广播上听到的典型声音, 而是位于3D 空间中的声音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="cda5d-114">利用空间音效, 你可以制作出全息影像, 就像你, 甚至是你自己的背景上!</span><span class="sxs-lookup"><span data-stu-id="cda5d-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="cda5d-115">在本课程中, 你将:</span><span class="sxs-lookup"><span data-stu-id="cda5d-115">In this course, you will:</span></span>

* <span data-ttu-id="cda5d-116">将你的开发环境配置为使用 Microsoft 空间音质。</span><span class="sxs-lookup"><span data-stu-id="cda5d-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="cda5d-117">使用空间音效来增强交互。</span><span class="sxs-lookup"><span data-stu-id="cda5d-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="cda5d-118">将空间音效与空间映射结合使用。</span><span class="sxs-lookup"><span data-stu-id="cda5d-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="cda5d-119">了解合理设计和混合最佳实践。</span><span class="sxs-lookup"><span data-stu-id="cda5d-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="cda5d-120">使用声音增强特殊效果, 并使用户进入混合现实世界。</span><span class="sxs-lookup"><span data-stu-id="cda5d-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="cda5d-121">设备支持</span><span class="sxs-lookup"><span data-stu-id="cda5d-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="cda5d-122">摘要</span><span class="sxs-lookup"><span data-stu-id="cda5d-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="cda5d-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="cda5d-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="cda5d-124"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="cda5d-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="cda5d-125">MR 空间 220:空间音效</span><span class="sxs-lookup"><span data-stu-id="cda5d-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="cda5d-126">✔️</span><span class="sxs-lookup"><span data-stu-id="cda5d-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="cda5d-127">✔️</span><span class="sxs-lookup"><span data-stu-id="cda5d-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="cda5d-128">开始之前</span><span class="sxs-lookup"><span data-stu-id="cda5d-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="cda5d-129">系统必备</span><span class="sxs-lookup"><span data-stu-id="cda5d-129">Prerequisites</span></span>

* <span data-ttu-id="cda5d-130">配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="cda5d-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="cda5d-131">一些基本C#的编程能力。</span><span class="sxs-lookup"><span data-stu-id="cda5d-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="cda5d-132">应已完成[尊敬的基本知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="cda5d-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="cda5d-133">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="cda5d-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="cda5d-134">项目文件</span><span class="sxs-lookup"><span data-stu-id="cda5d-134">Project files</span></span>

* <span data-ttu-id="cda5d-135">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)。</span><span class="sxs-lookup"><span data-stu-id="cda5d-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="cda5d-136"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="cda5d-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="cda5d-137">如果仍需要 Unity 5.6 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="cda5d-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="cda5d-138">此版本可能不再是最新版本。</span><span class="sxs-lookup"><span data-stu-id="cda5d-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="cda5d-139">如果仍需要 Unity 5.5 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="cda5d-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="cda5d-140"> 此版本可能不再是最新版本。</span><span class="sxs-lookup"><span data-stu-id="cda5d-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="cda5d-141">如果仍需要 Unity 5.4 支持, 请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="cda5d-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="cda5d-142"> 此版本可能不再是最新版本。</span><span class="sxs-lookup"><span data-stu-id="cda5d-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="cda5d-143">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="cda5d-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="cda5d-144">如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)找到。</span><span class="sxs-lookup"><span data-stu-id="cda5d-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="cda5d-145">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="cda5d-145">Errata and Notes</span></span>

* <span data-ttu-id="cda5d-146">需要在 Visual Studio 的 "工具"-"> 选项-> 调试" 中禁用 (*取消选中*) "启用仅我的代码", 以便在代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="cda5d-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="cda5d-147">第1章-Unity 设置</span><span class="sxs-lookup"><span data-stu-id="cda5d-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="cda5d-148">目标</span><span class="sxs-lookup"><span data-stu-id="cda5d-148">Objectives</span></span>

* <span data-ttu-id="cda5d-149">更改 Unity 的声音配置, 以使用 Microsoft 空间音质。</span><span class="sxs-lookup"><span data-stu-id="cda5d-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="cda5d-150">将三维声音添加到 Unity 中的对象。</span><span class="sxs-lookup"><span data-stu-id="cda5d-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="cda5d-151">说明</span><span class="sxs-lookup"><span data-stu-id="cda5d-151">Instructions</span></span>

* <span data-ttu-id="cda5d-152">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="cda5d-152">Start Unity.</span></span>
* <span data-ttu-id="cda5d-153">选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-153">Select **Open**.</span></span>
* <span data-ttu-id="cda5d-154">导航到桌面并找到以前未存档的文件夹。</span><span class="sxs-lookup"><span data-stu-id="cda5d-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="cda5d-155">单击 " **Starting\Decibel** " 文件夹, 然后按 "**选择文件夹**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="cda5d-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="cda5d-156">等待项目在 Unity 中加载。</span><span class="sxs-lookup"><span data-stu-id="cda5d-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="cda5d-157">在 " **项目**" 面板中, 打开**Scenes\Decibel.unity**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="cda5d-158">在 "**层次结构**" 面板中, 展开 " **HologramCollection** " 并选择 " **P0LY**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="cda5d-159">在检查器中, 展开 " **AudioSource** ", 注意没有 " **Spatialize** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="cda5d-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="cda5d-160">默认情况下, Unity 不会加载 spatializer 插件。</span><span class="sxs-lookup"><span data-stu-id="cda5d-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="cda5d-161">以下步骤将在项目中启用空间音质。</span><span class="sxs-lookup"><span data-stu-id="cda5d-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="cda5d-162">在 Unity 的顶部菜单中, 参阅**编辑 > 音频 > 项目设置**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="cda5d-163">找到**Spatializer 插件**下拉列表, 并选择 " **MS HRTF Spatializer**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="cda5d-164">在 "**层次结构**" 面板中, 选择 " **HologramCollection > P0LY**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="cda5d-165">在 "**检查器**" 面板中, 找到 "**音频源**" 组件。</span><span class="sxs-lookup"><span data-stu-id="cda5d-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="cda5d-166">选中 " **Spatialize** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="cda5d-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="cda5d-167">将**空间混合**滑块一直拖到**3d**上, 或在编辑框中输入**1** 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="cda5d-168">现在, 我们将在 Unity 中生成项目, 并在 Visual Studio 中配置该解决方案。</span><span class="sxs-lookup"><span data-stu-id="cda5d-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="cda5d-169">在 Unity 中, 选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="cda5d-170">单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="cda5d-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="cda5d-171">选择 "**平台**" 列表中的 "**通用 Windows 平台**", 然后单击 "**切换平台**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="cda5d-172">如果要专门针对 HoloLens 进行开发, 请将 "**目标设备**" 设置为 " **hololens**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="cda5d-173">否则, 请将其留在**任何设备**上。</span><span class="sxs-lookup"><span data-stu-id="cda5d-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="cda5d-174">确保将 "**生成类型**" 设置为 " **D3D** ", 并将 " **SDK** " 设置为 "**最新安装**的" (应为 SDK 16299 或更高版本)</span><span class="sxs-lookup"><span data-stu-id="cda5d-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="cda5d-175">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-175">Click **Build**.</span></span>
7. <span data-ttu-id="cda5d-176">创建名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="cda5d-177">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="cda5d-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="cda5d-178">按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-178">Press **Select Folder**.</span></span>

<span data-ttu-id="cda5d-179">当 Unity 完成后, 将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="cda5d-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="cda5d-180">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="cda5d-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="cda5d-181">打开 "**分贝 Visual Studio 解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="cda5d-182">如果部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="cda5d-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="cda5d-183">使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x86**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="cda5d-184">单击 "本地计算机" 按钮旁的下拉箭头, 然后选择 "**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="cda5d-185">输入**HoloLens 设备 IP 地址**, 并将身份验证模式设置为**通用 (未加密的协议)** 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="cda5d-186">单击 "**选择**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-186">Click **Select**.</span></span> <span data-ttu-id="cda5d-187">如果你不知道设备 IP 地址, 请在 "设置" 中查找 " **> 网络 & Internet > 高级选项**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="cda5d-188">在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="cda5d-189">如果这是首次部署到设备, 则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device---hololens-1st-gen)。</span><span class="sxs-lookup"><span data-stu-id="cda5d-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="cda5d-190">如果要部署到沉浸式耳机:</span><span class="sxs-lookup"><span data-stu-id="cda5d-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="cda5d-191">使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x64**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="cda5d-192">确保将部署目标设置为 "**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="cda5d-193">在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="cda5d-194">第2章-空间音效和交互</span><span class="sxs-lookup"><span data-stu-id="cda5d-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="cda5d-195">目标</span><span class="sxs-lookup"><span data-stu-id="cda5d-195">Objectives</span></span>

* <span data-ttu-id="cda5d-196">使用声音提高全息图的真实感。</span><span class="sxs-lookup"><span data-stu-id="cda5d-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="cda5d-197">使用声音定向用户的注视。</span><span class="sxs-lookup"><span data-stu-id="cda5d-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="cda5d-198">使用声音提供手势反馈。</span><span class="sxs-lookup"><span data-stu-id="cda5d-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="cda5d-199">第1部分-增强真实性</span><span class="sxs-lookup"><span data-stu-id="cda5d-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cda5d-200">关键概念</span><span class="sxs-lookup"><span data-stu-id="cda5d-200">Key Concepts</span></span>

* <span data-ttu-id="cda5d-201">Spatialize 全息影像声音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="cda5d-202">应将声音源置于全息图上的适当位置。</span><span class="sxs-lookup"><span data-stu-id="cda5d-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="cda5d-203">声音的适当位置将取决于全息图。</span><span class="sxs-lookup"><span data-stu-id="cda5d-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="cda5d-204">例如, 如果全息影像是人, 则声音源应位于嘴附近, 而不是英尺附近。</span><span class="sxs-lookup"><span data-stu-id="cda5d-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cda5d-205">说明</span><span class="sxs-lookup"><span data-stu-id="cda5d-205">Instructions</span></span>

<span data-ttu-id="cda5d-206">以下说明将 spatialized 声音附加到全息图。</span><span class="sxs-lookup"><span data-stu-id="cda5d-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="cda5d-207">在 "**层次结构**" 面板中, 展开 " **HologramCollection** " 并选择 " **P0LY**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="cda5d-208">在 "**检查器**" 面板的**AudioSource**中, 单击 " **AudioClip** " 旁边的圆圈, 并从弹出窗口中选择 " **PolyHover** "。</span><span class="sxs-lookup"><span data-stu-id="cda5d-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="cda5d-209">单击 "**输出**" 旁边的圆圈, 并从弹出窗口中选择 " **SoundEffects** "。</span><span class="sxs-lookup"><span data-stu-id="cda5d-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="cda5d-210">项目分贝使用 Unity **AudioMixer**组件来启用调整声音组的音量级别。</span><span class="sxs-lookup"><span data-stu-id="cda5d-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="cda5d-211">通过以这种方式对声音进行分组, 可以在保持每个声音的相对音量的同时调整总体音量。</span><span class="sxs-lookup"><span data-stu-id="cda5d-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="cda5d-212">在**AudioSource**中, 展开 "**三维声音设置**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="cda5d-213">将**Doppler 级别**设置为**0**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="cda5d-214">如果将 Doppler 级别设置为零, 则将禁用由运动 (一张全息图或用户) 导致的螺距变化。</span><span class="sxs-lookup"><span data-stu-id="cda5d-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="cda5d-215">Doppler 的典型示例是一种快速移动的汽车。</span><span class="sxs-lookup"><span data-stu-id="cda5d-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="cda5d-216">当汽车接近固定的侦听器时, 引擎的跨度会上升。</span><span class="sxs-lookup"><span data-stu-id="cda5d-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="cda5d-217">当它通过侦听程序时, 间距会降低距离。</span><span class="sxs-lookup"><span data-stu-id="cda5d-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="cda5d-218">第2部分-定向用户的注视</span><span class="sxs-lookup"><span data-stu-id="cda5d-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cda5d-219">关键概念</span><span class="sxs-lookup"><span data-stu-id="cda5d-219">Key Concepts</span></span>

* <span data-ttu-id="cda5d-220">使用声音吸引重要的全息影像。</span><span class="sxs-lookup"><span data-stu-id="cda5d-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="cda5d-221">此耳有助于指导眼睛的外观。</span><span class="sxs-lookup"><span data-stu-id="cda5d-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="cda5d-222">大脑有一些预期的预期。</span><span class="sxs-lookup"><span data-stu-id="cda5d-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="cda5d-223">了解预期的一个示例就是, 鸟瞰一般都是人的水平。</span><span class="sxs-lookup"><span data-stu-id="cda5d-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="cda5d-224">如果用户听到了鸟瞰声, 其初始反应就是查找。</span><span class="sxs-lookup"><span data-stu-id="cda5d-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="cda5d-225">如果在用户下放置鸟, 会使其面向正确的声音方向, 但无法根据需要查找的预期来找到全息影像。</span><span class="sxs-lookup"><span data-stu-id="cda5d-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cda5d-226">说明</span><span class="sxs-lookup"><span data-stu-id="cda5d-226">Instructions</span></span>

<span data-ttu-id="cda5d-227">以下说明允许 P0LY 隐藏在您后面, 以便您可以使用声音查找全息图。</span><span class="sxs-lookup"><span data-stu-id="cda5d-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="cda5d-228">在 "**层次结构**" 面板中, 选择 "**管理器**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="cda5d-229">在**检查器**面板中, 找到 "**语音输入处理程序**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="cda5d-230">在**语音输入处理程序**中, 展开 "**转到隐藏**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="cda5d-231">将**No 函数**更改为**PolyActions. GoHide**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![关键字转为隐藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="cda5d-233">第3部分-手势反馈</span><span class="sxs-lookup"><span data-stu-id="cda5d-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cda5d-234">关键概念</span><span class="sxs-lookup"><span data-stu-id="cda5d-234">Key Concepts</span></span>

* <span data-ttu-id="cda5d-235">使用声音为用户提供积极的手势确认</span><span class="sxs-lookup"><span data-stu-id="cda5d-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="cda5d-236">不要严重影响用户的声音,</span><span class="sxs-lookup"><span data-stu-id="cda5d-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="cda5d-237">微妙的声音效果最好-不要会掩盖体验</span><span class="sxs-lookup"><span data-stu-id="cda5d-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="cda5d-238">说明</span><span class="sxs-lookup"><span data-stu-id="cda5d-238">Instructions</span></span>

* <span data-ttu-id="cda5d-239">在 "**层次结构**" 面板中, 展开 " **HologramCollection**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="cda5d-240">展开 " **EnergyHub** ", 然后选择 "**基本**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="cda5d-241">在**检查器**面板中, 单击 "**添加组件**" 并添加**手势声音处理程序**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="cda5d-242">在**手势声音处理程序**中, 单击 "**导航已启动的剪辑**和**导航已更新的剪辑**" 旁边的圆圈, 并从弹出窗口中选择 " **RotateClick** "。</span><span class="sxs-lookup"><span data-stu-id="cda5d-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="cda5d-243">双击 "GestureSoundHandler" 以在 Visual Studio 中加载。</span><span class="sxs-lookup"><span data-stu-id="cda5d-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="cda5d-244">手势声音处理程序执行以下任务:</span><span class="sxs-lookup"><span data-stu-id="cda5d-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="cda5d-245">创建和配置**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="cda5d-246">将**AudioSource**放在适当**GameObject**的位置。</span><span class="sxs-lookup"><span data-stu-id="cda5d-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="cda5d-247">播放与该笔势关联的**AudioClip** 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="cda5d-248">生成和部署</span><span class="sxs-lookup"><span data-stu-id="cda5d-248">Build and Deploy</span></span>

1. <span data-ttu-id="cda5d-249">在 Unity 中, 选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="cda5d-250">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-250">Click **Build**.</span></span>
3. <span data-ttu-id="cda5d-251">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="cda5d-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="cda5d-252">按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-252">Press **Select Folder**.</span></span>

<span data-ttu-id="cda5d-253">检查工具栏是否显示 "发布"、"x86" 或 "x64", 以及 "远程设备"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="cda5d-254">如果不是, 则这是 Visual Studio 的代码实例。</span><span class="sxs-lookup"><span data-stu-id="cda5d-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="cda5d-255">可能需要从应用程序文件夹重新打开解决方案。</span><span class="sxs-lookup"><span data-stu-id="cda5d-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="cda5d-256">如果系统提示, 请重新加载项目文件。</span><span class="sxs-lookup"><span data-stu-id="cda5d-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="cda5d-257">如前所述, 从 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="cda5d-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="cda5d-258">部署应用程序后:</span><span class="sxs-lookup"><span data-stu-id="cda5d-258">After the application is deployed:</span></span>

* <span data-ttu-id="cda5d-259">观察在 P0LY 移动时声音如何变化。</span><span class="sxs-lookup"><span data-stu-id="cda5d-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="cda5d-260">说 *"转到隐藏"* , 使 P0LY 移到你后面的位置。</span><span class="sxs-lookup"><span data-stu-id="cda5d-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="cda5d-261">通过声音查找。</span><span class="sxs-lookup"><span data-stu-id="cda5d-261">Find it by the sound.</span></span>
* <span data-ttu-id="cda5d-262">注视能源中心的底部。</span><span class="sxs-lookup"><span data-stu-id="cda5d-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="cda5d-263">点击并向左或向右拖动以旋转全息影像, 并注意单击声音如何确认手势。</span><span class="sxs-lookup"><span data-stu-id="cda5d-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="cda5d-264">注意:这里有一个文本面板, 将与您一起标记。</span><span class="sxs-lookup"><span data-stu-id="cda5d-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="cda5d-265">这将包含可在本课程中使用的可用语音命令。</span><span class="sxs-lookup"><span data-stu-id="cda5d-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="cda5d-266">第3章-空间音质和空间映射</span><span class="sxs-lookup"><span data-stu-id="cda5d-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="cda5d-267">目标</span><span class="sxs-lookup"><span data-stu-id="cda5d-267">Objectives</span></span>

* <span data-ttu-id="cda5d-268">使用声音确认全息影像与真实环境之间的交互。</span><span class="sxs-lookup"><span data-stu-id="cda5d-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="cda5d-269">使用实物遮蔽声音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="cda5d-270">第1部分-物理世界交互</span><span class="sxs-lookup"><span data-stu-id="cda5d-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cda5d-271">关键概念</span><span class="sxs-lookup"><span data-stu-id="cda5d-271">Key Concepts</span></span>

* <span data-ttu-id="cda5d-272">当遇到图面或其他对象时, 物理对象通常会发出声音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="cda5d-273">声音应在体验中是适当的上下文。</span><span class="sxs-lookup"><span data-stu-id="cda5d-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="cda5d-274">例如, 对表设置杯会使声音更安静, 而不是在金属片上放置 boulder。</span><span class="sxs-lookup"><span data-stu-id="cda5d-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cda5d-275">说明</span><span class="sxs-lookup"><span data-stu-id="cda5d-275">Instructions</span></span>

* <span data-ttu-id="cda5d-276">在 "**层次结构**" 面板中, 展开 " **HologramCollection**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="cda5d-277">展开 " **EnergyHub**", 选择 "**基本**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="cda5d-278">在 "**检查器**" 面板中, 单击 "**添加组件**", 然后单击 "添加**声音和操作**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="cda5d-279">在中,**单击以放置声音和操作**:</span><span class="sxs-lookup"><span data-stu-id="cda5d-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="cda5d-280">**在点击时选中 "父项"** 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="cda5d-281">设置要**放置**的**放置声音**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="cda5d-282">将**拾取声音**设置为**装货**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="cda5d-283">在 "**分拣" 操作**和 **"放置" 操作**中, 按右下方的 "+"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="cda5d-284">将 EnergyHub 从场景拖到**无 (对象)** 字段。</span><span class="sxs-lookup"><span data-stu-id="cda5d-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="cda5d-285">在 **"分拣操作**" 下, 单击 "**无函数** -> **EnergyHubBase** -> **ResetAnimation**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="cda5d-286">在 **"放置时" 操作**下, 单击 "**无函数** -> **EnergyHubBase** -> **OnSelect**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![点击以放入声音和操作](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="cda5d-288">第2部分-声音封闭</span><span class="sxs-lookup"><span data-stu-id="cda5d-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cda5d-289">关键概念</span><span class="sxs-lookup"><span data-stu-id="cda5d-289">Key Concepts</span></span>

* <span data-ttu-id="cda5d-290">声音, 如光源, 可以是封闭像素。</span><span class="sxs-lookup"><span data-stu-id="cda5d-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="cda5d-291">典型的示例是音乐会厅。</span><span class="sxs-lookup"><span data-stu-id="cda5d-291">A classic example is a concert hall.</span></span> <span data-ttu-id="cda5d-292">当某个侦听器在大厅外且门闭合时, 音乐听起来 muffled。</span><span class="sxs-lookup"><span data-stu-id="cda5d-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="cda5d-293">通常还会减少容量。</span><span class="sxs-lookup"><span data-stu-id="cda5d-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="cda5d-294">打开门后, 就会听到真实音量的所有声音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="cda5d-295">高频声音通常会超出低频率。</span><span class="sxs-lookup"><span data-stu-id="cda5d-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cda5d-296">说明</span><span class="sxs-lookup"><span data-stu-id="cda5d-296">Instructions</span></span>

* <span data-ttu-id="cda5d-297">在 "**层次结构**" 面板中, 展开 " **HologramCollection** " 并选择 " **P0LY**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="cda5d-298">在**检查器**面板中, 单击 "**添加组件**" 并添加**音频发射器**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="cda5d-299">音频发射器类提供以下功能:</span><span class="sxs-lookup"><span data-stu-id="cda5d-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="cda5d-300">还原对**AudioSource**卷的任何更改。</span><span class="sxs-lookup"><span data-stu-id="cda5d-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="cda5d-301">按照**AudioEmitter**连接到的**GameObject**的方向, 从用户的位置执行**RaycastNonAlloc** 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="cda5d-302">RaycastNonAlloc 方法用作性能优化, 以限制分配和返回的结果数。</span><span class="sxs-lookup"><span data-stu-id="cda5d-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="cda5d-303">对于遇到的每个**IAudioInfluencer** , 将调用**ApplyEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="cda5d-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="cda5d-304">对于不再遇到的每个以前的**IAudioInfluencer** , 请调用**RemoveEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="cda5d-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="cda5d-305">请注意, AudioEmitter 对人为时间刻度的更新, 而不是每个框架的更新。</span><span class="sxs-lookup"><span data-stu-id="cda5d-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="cda5d-306">这样做是因为, 人们通常不能以足够快的速度移动, 因此, 需要比每个季度或半秒钟的频率更频繁地进行更新。</span><span class="sxs-lookup"><span data-stu-id="cda5d-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="cda5d-307">从一个位置到另一个位置快速传送的全息影像可能会突破错觉。</span><span class="sxs-lookup"><span data-stu-id="cda5d-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="cda5d-308">在 "**层次结构**" 面板中, 展开 " **HologramCollection**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="cda5d-309">展开 " **EnergyHub** " 并选择 " **BlobOutside**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="cda5d-310">在**检查器**面板中, 单击 "**添加组件**" 并添加**音频 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="cda5d-311">在**音频 Occluder**中, 将 "**截止频率**" 设置为**1500**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="cda5d-312">此设置将 AudioSource 频率限制为 1500 Hz 和更低。</span><span class="sxs-lookup"><span data-stu-id="cda5d-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="cda5d-313">将**Volume Pass**设置为**0.9**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="cda5d-314">此设置将 AudioSource 的量降低到其当前级别的 90%。</span><span class="sxs-lookup"><span data-stu-id="cda5d-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="cda5d-315">音频 Occluder 实现 IAudioInfluencer:</span><span class="sxs-lookup"><span data-stu-id="cda5d-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="cda5d-316">使用附加到**AudioSource**托管的**AudioLowPassFilter**的封闭**效果。**</span><span class="sxs-lookup"><span data-stu-id="cda5d-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="cda5d-317">将卷衰减应用于 AudioSource。</span><span class="sxs-lookup"><span data-stu-id="cda5d-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="cda5d-318">通过设置非特定截止频率并禁用筛选器来禁用该效果。</span><span class="sxs-lookup"><span data-stu-id="cda5d-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="cda5d-319">用于中性的频率为 22 kHz (22000 Hz)。</span><span class="sxs-lookup"><span data-stu-id="cda5d-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="cda5d-320">选择此频率的原因是, 它的最大频率为人体耳可以听到的最大公称, 这不会影响声音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="cda5d-321">在 "**层次结构**" 面板中, 选择 " **SpatialMapping**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="cda5d-322">在**检查器**面板中, 单击 "**添加组件**" 并添加**音频 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="cda5d-323">在**音频 Occluder**中, 将 "**截止频率**" 设置为**750**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="cda5d-324">如果多个 occluders 位于用户与**AudioEmitter**之间的路径中, 则会将最低频率应用于筛选器。</span><span class="sxs-lookup"><span data-stu-id="cda5d-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="cda5d-325">将**Volume Pass**设置为**0.75**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="cda5d-326">如果多个 occluders 位于用户与**AudioEmitter**之间的路径中, 则会应用添加性地。</span><span class="sxs-lookup"><span data-stu-id="cda5d-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="cda5d-327">在 "**层次结构**" 面板中, 选择 "**管理器**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="cda5d-328">在 "**检查器**" 面板中, 展开 "**语音输入处理程序**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="cda5d-329">在**语音输入处理程序**中, 展开 "**转到**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="cda5d-330">将**No 函数**更改为**PolyActions. GoCharge**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![关键字走电](images/gocharge.png)

* <span data-ttu-id="cda5d-332">**在此处**展开。</span><span class="sxs-lookup"><span data-stu-id="cda5d-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="cda5d-333">将**No 函数**更改为**PolyActions. 卷土重来**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![关键字过来这里](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="cda5d-335">生成和部署</span><span class="sxs-lookup"><span data-stu-id="cda5d-335">Build and Deploy</span></span>

* <span data-ttu-id="cda5d-336">如前所述, 在 Unity 中生成项目, 并在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="cda5d-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="cda5d-337">部署应用程序后:</span><span class="sxs-lookup"><span data-stu-id="cda5d-337">After the application is deployed:</span></span>

* <span data-ttu-id="cda5d-338">说 *"走电"* , 让 P0LY 进入能量中心。</span><span class="sxs-lookup"><span data-stu-id="cda5d-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="cda5d-339">请注意声音的变化。</span><span class="sxs-lookup"><span data-stu-id="cda5d-339">Note the change in the sound.</span></span> <span data-ttu-id="cda5d-340">这听起来 muffled。</span><span class="sxs-lookup"><span data-stu-id="cda5d-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="cda5d-341">如果你能够在你与能源中心之间定位墙壁或其他对象, 你应该注意到 muffling 的声音, 因为现实世界封闭了。</span><span class="sxs-lookup"><span data-stu-id="cda5d-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="cda5d-342">说 *"现在*就可以", 让 P0LY 离开能源中心, 并将其放在您前面。</span><span class="sxs-lookup"><span data-stu-id="cda5d-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="cda5d-343">请注意, 一旦 P0LY 退出能源中心, 就会删除声音封闭。</span><span class="sxs-lookup"><span data-stu-id="cda5d-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="cda5d-344">如果你仍在封闭, P0LY 可能会被现实世界封闭像素。</span><span class="sxs-lookup"><span data-stu-id="cda5d-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="cda5d-345">尝试移动以确保对 P0LY 有清楚的视觉。</span><span class="sxs-lookup"><span data-stu-id="cda5d-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="cda5d-346">第3部分-房间模型</span><span class="sxs-lookup"><span data-stu-id="cda5d-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cda5d-347">关键概念</span><span class="sxs-lookup"><span data-stu-id="cda5d-347">Key Concepts</span></span>

* <span data-ttu-id="cda5d-348">空间大小提供了 subliminal 的队列, 它们有助于进行合理的本地化。</span><span class="sxs-lookup"><span data-stu-id="cda5d-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="cda5d-349">房间模型是按**AudioSource**设置的。</span><span class="sxs-lookup"><span data-stu-id="cda5d-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="cda5d-350">[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供用于设置房间模型的代码。</span><span class="sxs-lookup"><span data-stu-id="cda5d-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="cda5d-351">对于混合现实体验, 请选择最适合于现实世界空间的房间模型。</span><span class="sxs-lookup"><span data-stu-id="cda5d-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="cda5d-352">如果要创建虚拟现实方案, 请选择最适合虚拟环境的房间模型。</span><span class="sxs-lookup"><span data-stu-id="cda5d-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="cda5d-353">第4章-声音设计</span><span class="sxs-lookup"><span data-stu-id="cda5d-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="cda5d-354">目标</span><span class="sxs-lookup"><span data-stu-id="cda5d-354">Objectives</span></span>

* <span data-ttu-id="cda5d-355">了解有效的声音设计的注意事项。</span><span class="sxs-lookup"><span data-stu-id="cda5d-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="cda5d-356">了解混合技巧和指导原则。</span><span class="sxs-lookup"><span data-stu-id="cda5d-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="cda5d-357">第1部分-声音和体验设计</span><span class="sxs-lookup"><span data-stu-id="cda5d-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="cda5d-358">本部分介绍关键的声音, 并体验设计注意事项和指导原则。</span><span class="sxs-lookup"><span data-stu-id="cda5d-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="cda5d-359">规范化所有声音</span><span class="sxs-lookup"><span data-stu-id="cda5d-359">Normalize all sounds</span></span>

<span data-ttu-id="cda5d-360">这样就无需使用特殊案例代码调整每个声音的音量级别, 这可能非常耗时, 并且限制了轻松更新声音文件的能力。</span><span class="sxs-lookup"><span data-stu-id="cda5d-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="cda5d-361">设计 untethered 体验</span><span class="sxs-lookup"><span data-stu-id="cda5d-361">Design for an untethered experience</span></span>

<span data-ttu-id="cda5d-362">HoloLens 是完全包含的 untethered 全息计算机。</span><span class="sxs-lookup"><span data-stu-id="cda5d-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="cda5d-363">你的用户可以在移动时使用你的体验。</span><span class="sxs-lookup"><span data-stu-id="cda5d-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="cda5d-364">务必通过浏览来测试您的音频组合。</span><span class="sxs-lookup"><span data-stu-id="cda5d-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="cda5d-365">从逻辑位置在全息影像上发出声音</span><span class="sxs-lookup"><span data-stu-id="cda5d-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="cda5d-366">在现实生活中, 狗不会吠其尾部, 人类的语音不会来自其英尺。</span><span class="sxs-lookup"><span data-stu-id="cda5d-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="cda5d-367">避免在全息影像的意外部分发出声音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="cda5d-368">对于小全息影像, 从几何图形中心开始发出声音是合理的。</span><span class="sxs-lookup"><span data-stu-id="cda5d-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="cda5d-369">熟悉的声音是最可本地化的</span><span class="sxs-lookup"><span data-stu-id="cda5d-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="cda5d-370">人为语音和音乐非常易于本地化。</span><span class="sxs-lookup"><span data-stu-id="cda5d-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="cda5d-371">如果有人调用了您的姓名, 则可以从语音的方向和距离。</span><span class="sxs-lookup"><span data-stu-id="cda5d-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="cda5d-372">简短, 不熟悉的声音更难本地化。</span><span class="sxs-lookup"><span data-stu-id="cda5d-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="cda5d-373">Cognizant 用户期望</span><span class="sxs-lookup"><span data-stu-id="cda5d-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="cda5d-374">生活经验使我们能够确定声音位置。</span><span class="sxs-lookup"><span data-stu-id="cda5d-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="cda5d-375">这就是人们语音特别容易本地化的原因之一。</span><span class="sxs-lookup"><span data-stu-id="cda5d-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="cda5d-376">发出声音时, 请注意用户的预期预期。</span><span class="sxs-lookup"><span data-stu-id="cda5d-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="cda5d-377">例如, 当有人听到了他们通常会查找的鸟瞰歌曲时, 因为鸟瞰通常会位于视线的上方 (飞行或树形上)。</span><span class="sxs-lookup"><span data-stu-id="cda5d-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="cda5d-378">用户打开正确的声音方向并不是很常见, 而是在无法找到全息影像时在错误的垂直方向上看起来不确定的。</span><span class="sxs-lookup"><span data-stu-id="cda5d-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="cda5d-379">避免隐藏发射器</span><span class="sxs-lookup"><span data-stu-id="cda5d-379">Avoid hidden emitters</span></span>

<span data-ttu-id="cda5d-380">在实际情况下, 如果听到声音, 通常可以识别出发出声音的对象。</span><span class="sxs-lookup"><span data-stu-id="cda5d-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="cda5d-381">在您的体验中, 这也应为 true。</span><span class="sxs-lookup"><span data-stu-id="cda5d-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="cda5d-382">用户听听声音非常不安, 知道声音出自何处, 看不到对象。</span><span class="sxs-lookup"><span data-stu-id="cda5d-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="cda5d-383">此准则有一些例外情况。</span><span class="sxs-lookup"><span data-stu-id="cda5d-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="cda5d-384">例如, 字段中的 crickets 等环境声音无需可见。</span><span class="sxs-lookup"><span data-stu-id="cda5d-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="cda5d-385">生活经验为我们熟悉这些声音的来源, 无需查看。</span><span class="sxs-lookup"><span data-stu-id="cda5d-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="cda5d-386">第2部分-混音</span><span class="sxs-lookup"><span data-stu-id="cda5d-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="cda5d-387">在 HoloLens 上将混合目标设定为 70% 的卷</span><span class="sxs-lookup"><span data-stu-id="cda5d-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="cda5d-388">混合现实体验允许在现实世界中查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="cda5d-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="cda5d-389">它们还应该允许听真实世界声音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="cda5d-390">利用 70% 的音量目标, 用户可以在他们周围倾听世界, 并获得你的体验。</span><span class="sxs-lookup"><span data-stu-id="cda5d-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="cda5d-391">100% 卷上的 HoloLens 应 drown 外部声音</span><span class="sxs-lookup"><span data-stu-id="cda5d-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="cda5d-392">100% 的卷级别与虚拟现实体验类似。</span><span class="sxs-lookup"><span data-stu-id="cda5d-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="cda5d-393">用户在视觉上传输到不同的世界。</span><span class="sxs-lookup"><span data-stu-id="cda5d-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="cda5d-394">相同的呼叫时应为 true。</span><span class="sxs-lookup"><span data-stu-id="cda5d-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="cda5d-395">使用 Unity AudioMixer 调整声音类别</span><span class="sxs-lookup"><span data-stu-id="cda5d-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="cda5d-396">设计你的组合时, 创建声音类别并能够将其音量增加或减少为一个单元通常很有帮助。</span><span class="sxs-lookup"><span data-stu-id="cda5d-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="cda5d-397">这会保留每个声音的相对级别, 同时使整体组合的快速而简单的更改。</span><span class="sxs-lookup"><span data-stu-id="cda5d-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="cda5d-398">常见类别包括:声音效果、环境、语音转移和背景音乐。</span><span class="sxs-lookup"><span data-stu-id="cda5d-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="cda5d-399">基于用户的注视混合声音</span><span class="sxs-lookup"><span data-stu-id="cda5d-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="cda5d-400">通常, 根据用户所在的位置 (或不需要) 来更改声音混合, 这通常很有用。</span><span class="sxs-lookup"><span data-stu-id="cda5d-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="cda5d-401">此方法的一个常见用途是降低全息帧之外的全息影像的音量级别, 使用户能够更轻松地将重点放在其前面的信息上。</span><span class="sxs-lookup"><span data-stu-id="cda5d-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="cda5d-402">另一种用途是增加声音量, 以吸引用户关注重要事件。</span><span class="sxs-lookup"><span data-stu-id="cda5d-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="cda5d-403">构建混合</span><span class="sxs-lookup"><span data-stu-id="cda5d-403">Building your mix</span></span>

<span data-ttu-id="cda5d-404">在构建组合时, 建议从体验背景音频开始, 并根据重要性添加层。</span><span class="sxs-lookup"><span data-stu-id="cda5d-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="cda5d-405">通常, 这会导致每个层都大于上一个层。</span><span class="sxs-lookup"><span data-stu-id="cda5d-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="cda5d-406">应该构想你的混合为反转漏斗图, 最重要的是最不重要的 (通常是 quietest 的声音), 因此建议将你的混合与下图类似。</span><span class="sxs-lookup"><span data-stu-id="cda5d-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![声音混合结构](images/soundlevels.png)

<span data-ttu-id="cda5d-408">语音转移是一个有趣的方案。</span><span class="sxs-lookup"><span data-stu-id="cda5d-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="cda5d-409">根据你创建的体验, 你可能想要使用立体声 (未本地化) 声音或 spatialize 你的语音转移。</span><span class="sxs-lookup"><span data-stu-id="cda5d-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="cda5d-410">两个 Microsoft 发布的体验演示了每个方案的极佳示例。</span><span class="sxs-lookup"><span data-stu-id="cda5d-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="cda5d-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87)使用立体声声音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="cda5d-412">当讲述人描述正在查看的位置时, 声音是一致的, 并且不会根据用户的位置而变化。</span><span class="sxs-lookup"><span data-stu-id="cda5d-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="cda5d-413">这使讲述人可以在不离开环境 spatialized 声音的情况下描述场景。</span><span class="sxs-lookup"><span data-stu-id="cda5d-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="cda5d-414">[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)使用 spatialized 的语音。</span><span class="sxs-lookup"><span data-stu-id="cda5d-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="cda5d-415">侦探的声音用于帮助用户关注重要的线索, 就像实际人在房间里。</span><span class="sxs-lookup"><span data-stu-id="cda5d-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="cda5d-416">这样, 就可以更好地浸入式解决谜的体验。</span><span class="sxs-lookup"><span data-stu-id="cda5d-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="cda5d-417">第3部分-性能</span><span class="sxs-lookup"><span data-stu-id="cda5d-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="cda5d-418">CPU 使用情况</span><span class="sxs-lookup"><span data-stu-id="cda5d-418">CPU usage</span></span>

<span data-ttu-id="cda5d-419">使用空间音效时, 10-12 发射器会消耗约 12% 的 CPU。</span><span class="sxs-lookup"><span data-stu-id="cda5d-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="cda5d-420">流式传输长音频文件</span><span class="sxs-lookup"><span data-stu-id="cda5d-420">Stream long audio files</span></span>

<span data-ttu-id="cda5d-421">音频数据可能很大, 尤其是在常见采样速率 (44.1 和 48 kHz) 上。</span><span class="sxs-lookup"><span data-stu-id="cda5d-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="cda5d-422">一般规则是, 应流式传输超过 5-10 秒的音频文件, 以降低应用程序内存使用量。</span><span class="sxs-lookup"><span data-stu-id="cda5d-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="cda5d-423">在 Unity 中, 可以在文件的导入设置中标记音频文件以进行流式传输。</span><span class="sxs-lookup"><span data-stu-id="cda5d-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![音频导入设置](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="cda5d-425">第5章-特殊效果</span><span class="sxs-lookup"><span data-stu-id="cda5d-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="cda5d-426">目标</span><span class="sxs-lookup"><span data-stu-id="cda5d-426">Objectives</span></span>

* <span data-ttu-id="cda5d-427">将深度添加到 "幻窗口"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="cda5d-428">将用户带入虚拟世界。</span><span class="sxs-lookup"><span data-stu-id="cda5d-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="cda5d-429">魔术窗口</span><span class="sxs-lookup"><span data-stu-id="cda5d-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="cda5d-430">关键概念</span><span class="sxs-lookup"><span data-stu-id="cda5d-430">Key Concepts</span></span>

* <span data-ttu-id="cda5d-431">将视图创建到隐藏世界中, 这在视觉上非常引人注目。</span><span class="sxs-lookup"><span data-stu-id="cda5d-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="cda5d-432">当全息图或用户处于隐藏世界附近时, 通过添加音频效果来增强真实性。</span><span class="sxs-lookup"><span data-stu-id="cda5d-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="cda5d-433">说明</span><span class="sxs-lookup"><span data-stu-id="cda5d-433">Instructions</span></span>

* <span data-ttu-id="cda5d-434">在 "**层次结构**" 面板中, 展开 " **HologramCollection** " 并选择 " **Underworld**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="cda5d-435">展开 " **Underworld** " 并选择 " **VoiceSource**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="cda5d-436">在**检查器**面板中, 单击 "**添加组件**" 并添加 "**用户语音效果**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="cda5d-437">**AudioSource**组件将添加到**VoiceSource**中。</span><span class="sxs-lookup"><span data-stu-id="cda5d-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="cda5d-438">在**AudioSource**中, 将 "**输出**" 设置为**UserVoice (混音器)** 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="cda5d-439">选中 " **Spatialize** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="cda5d-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="cda5d-440">将**空间混合**滑块一直拖到**3d**上, 或在编辑框中输入**1** 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="cda5d-441">展开 "**三维声音设置**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="cda5d-442">将**Doppler 级别**设置为**0**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="cda5d-443">在 "**用户语音效果**" 中, 将**父对象**从场景中设置为**Underworld** 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="cda5d-444">将**最大距离**设置为**1**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="cda5d-445">设置**最大距离**会告诉**用户语音效果**在启用此效果之前, 用户必须先到父对象。</span><span class="sxs-lookup"><span data-stu-id="cda5d-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="cda5d-446">在 "**用户语音效果**" 中, 展开 " **Chorus 参数**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="cda5d-447">将**深度**设置为**0.1**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="cda5d-448">依次点击 " **1**"、" **2 卷**" 和 " **3 卷**到**0.8**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="cda5d-449">将**原始**音量设置为**0.5**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="cda5d-450">以前的设置配置用于向用户语音添加丰富的 Unity **AudioChorusFilter**的参数。</span><span class="sxs-lookup"><span data-stu-id="cda5d-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="cda5d-451">在 "**用户语音效果**" 中, 展开 " **Echo Parameters**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="cda5d-452">将**延迟**设置为**300**</span><span class="sxs-lookup"><span data-stu-id="cda5d-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="cda5d-453">将**衰减比率**设置为**0.2**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="cda5d-454">将**原始**音量设置为**0**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="cda5d-455">以前的设置配置用于使用户的语音回显的 Unity **AudioEchoFilter**的参数。</span><span class="sxs-lookup"><span data-stu-id="cda5d-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="cda5d-456">用户语音效果脚本负责:</span><span class="sxs-lookup"><span data-stu-id="cda5d-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="cda5d-457">测量用户与脚本附加到的**GameObject**之间的距离。</span><span class="sxs-lookup"><span data-stu-id="cda5d-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="cda5d-458">确定用户是否面向**GameObject**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="cda5d-459">对于启用的效果, 用户必须面向 GameObject, 而不考虑距离。</span><span class="sxs-lookup"><span data-stu-id="cda5d-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="cda5d-460">将**AudioChorusFilter**和**AudioEchoFilter**应用和配置到**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="cda5d-461">禁用筛选器以禁用该效果。</span><span class="sxs-lookup"><span data-stu-id="cda5d-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="cda5d-462">用户语音效果使用[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)中的 Mic Stream 选择器组件选择高质量的语音流并将其路由到 Unity 的音频系统。</span><span class="sxs-lookup"><span data-stu-id="cda5d-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="cda5d-463">在 "**层次结构**" 面板中, 选择 "**管理器**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="cda5d-464">在 "**检查器**" 面板中, 展开 "**语音输入处理程序**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="cda5d-465">在**语音输入处理程序**中, 展开**Show Underworld**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="cda5d-466">将**No 函数**更改为**UnderworldBase. OnEnable**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![关键字显示 Underworld](images/showunderworld.png)

* <span data-ttu-id="cda5d-468">展开 "**隐藏 Underworld**"。</span><span class="sxs-lookup"><span data-stu-id="cda5d-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="cda5d-469">将**No 函数**更改为**UnderworldBase. OnDisable**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![关键字隐藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="cda5d-471">生成和部署</span><span class="sxs-lookup"><span data-stu-id="cda5d-471">Build and Deploy</span></span>

* <span data-ttu-id="cda5d-472">如前所述, 在 Unity 中生成项目, 并在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="cda5d-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="cda5d-473">部署应用程序后:</span><span class="sxs-lookup"><span data-stu-id="cda5d-473">After the application is deployed:</span></span>

* <span data-ttu-id="cda5d-474">面部面 (墙壁、楼层、桌子), 并说 *"Show Underworld"* 。</span><span class="sxs-lookup"><span data-stu-id="cda5d-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="cda5d-475">将显示 underworld, 所有其他全息影像都将隐藏。</span><span class="sxs-lookup"><span data-stu-id="cda5d-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="cda5d-476">如果看不到 underworld, 请确保您面对的是实际的表面。</span><span class="sxs-lookup"><span data-stu-id="cda5d-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="cda5d-477">Underworld 全息图1米内的方法, 开始谈话。</span><span class="sxs-lookup"><span data-stu-id="cda5d-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="cda5d-478">现在音频效果适用于你的语音!</span><span class="sxs-lookup"><span data-stu-id="cda5d-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="cda5d-479">退出 underworld 并注意如何不再应用该效果。</span><span class="sxs-lookup"><span data-stu-id="cda5d-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="cda5d-480">说 *"隐藏 Underworld"* 以隐藏 Underworld。</span><span class="sxs-lookup"><span data-stu-id="cda5d-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="cda5d-481">Underworld 将隐藏, 并且以前隐藏的全息影像会重新出现。</span><span class="sxs-lookup"><span data-stu-id="cda5d-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="cda5d-482">结束</span><span class="sxs-lookup"><span data-stu-id="cda5d-482">The End</span></span>

<span data-ttu-id="cda5d-483">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="cda5d-483">Congratulations!</span></span> <span data-ttu-id="cda5d-484">你现在已经完成**了 MR 空间 220:空间音质**。</span><span class="sxs-lookup"><span data-stu-id="cda5d-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="cda5d-485">听世界, 让你的体验生活生动!</span><span class="sxs-lookup"><span data-stu-id="cda5d-485">Listen to the world and bring your experiences to life with sound!</span></span>
