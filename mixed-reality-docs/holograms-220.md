---
title: MR 空间 220-空间音效
description: 按照此编码演练操作，使用 Unity、Visual Studio 和 HoloLens 来了解空间音效概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，学院，教程，空间音效
ms.openlocfilehash: a3fc054927d73cf9ac21f831caa4ec23875977bd
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434722"
---
>[!NOTE]
><span data-ttu-id="9a556-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="9a556-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9a556-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="9a556-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9a556-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="9a556-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9a556-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="9a556-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9a556-108">为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="9a556-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="9a556-109">MR 空间220：空间音效</span><span class="sxs-lookup"><span data-stu-id="9a556-109">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="9a556-110">[空间音效](spatial-sound.md)breathes 影像，并使其在世界中存在。</span><span class="sxs-lookup"><span data-stu-id="9a556-110">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="9a556-111">全息影像同时包含光和声音，如果你发生丢失全息影像的情况，空间音效可以帮助你找到它们。</span><span class="sxs-lookup"><span data-stu-id="9a556-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="9a556-112">空间音效并不像您在广播上听到的典型声音，而是位于3D 空间中的声音。</span><span class="sxs-lookup"><span data-stu-id="9a556-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="9a556-113">利用空间音效，你可以制作出全息影像，就像你，甚至是你自己的背景上！</span><span class="sxs-lookup"><span data-stu-id="9a556-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="9a556-114">在本课程中，你将：</span><span class="sxs-lookup"><span data-stu-id="9a556-114">In this course, you will:</span></span>

* <span data-ttu-id="9a556-115">将你的开发环境配置为使用 Microsoft 空间音质。</span><span class="sxs-lookup"><span data-stu-id="9a556-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="9a556-116">使用空间音效来增强交互。</span><span class="sxs-lookup"><span data-stu-id="9a556-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="9a556-117">将空间音效与[空间映射](spatial-mapping.md)结合使用。</span><span class="sxs-lookup"><span data-stu-id="9a556-117">Use Spatial Sound in conjunction with [Spatial Mapping](spatial-mapping.md).</span></span>
* <span data-ttu-id="9a556-118">了解合理设计和混合最佳实践。</span><span class="sxs-lookup"><span data-stu-id="9a556-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="9a556-119">使用声音增强特殊效果，并使用户进入混合现实世界。</span><span class="sxs-lookup"><span data-stu-id="9a556-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="9a556-120">设备支持</span><span class="sxs-lookup"><span data-stu-id="9a556-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9a556-121">摘要</span><span class="sxs-lookup"><span data-stu-id="9a556-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9a556-122"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9a556-122"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9a556-123"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="9a556-123"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9a556-124">MR 空间220：空间音效</span><span class="sxs-lookup"><span data-stu-id="9a556-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="9a556-125">✔️</span><span class="sxs-lookup"><span data-stu-id="9a556-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9a556-126">✔️</span><span class="sxs-lookup"><span data-stu-id="9a556-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9a556-127">开始之前</span><span class="sxs-lookup"><span data-stu-id="9a556-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9a556-128">必备条件</span><span class="sxs-lookup"><span data-stu-id="9a556-128">Prerequisites</span></span>

* <span data-ttu-id="9a556-129">配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="9a556-129">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="9a556-130">一些基本C#的编程能力。</span><span class="sxs-lookup"><span data-stu-id="9a556-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="9a556-131">应已完成[尊敬的基本知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="9a556-131">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="9a556-132">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="9a556-132">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="9a556-133">项目文件</span><span class="sxs-lookup"><span data-stu-id="9a556-133">Project files</span></span>

* <span data-ttu-id="9a556-134">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip)。</span><span class="sxs-lookup"><span data-stu-id="9a556-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="9a556-135"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="9a556-135"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="9a556-136">如果仍需要 Unity 5.6 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="9a556-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="9a556-137">此版本可能不再是最新版本。</span><span class="sxs-lookup"><span data-stu-id="9a556-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="9a556-138">如果仍需要 Unity 5.5 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="9a556-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="9a556-139"> 此版本可能不再是最新版本。</span><span class="sxs-lookup"><span data-stu-id="9a556-139"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="9a556-140">如果仍需要 Unity 5.4 支持，请使用[此版本](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)。</span><span class="sxs-lookup"><span data-stu-id="9a556-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="9a556-141"> 此版本可能不再是最新版本。</span><span class="sxs-lookup"><span data-stu-id="9a556-141"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="9a556-142">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="9a556-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="9a556-143">如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)找到。</span><span class="sxs-lookup"><span data-stu-id="9a556-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="9a556-144">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="9a556-144">Errata and Notes</span></span>

* <span data-ttu-id="9a556-145">需要在 Visual Studio 的 "工具"-"> 选项-> 调试" 中禁用（*取消选中*） "启用仅我的代码"，以便在代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="9a556-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="9a556-146">第1章-Unity 设置</span><span class="sxs-lookup"><span data-stu-id="9a556-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="9a556-147">目标</span><span class="sxs-lookup"><span data-stu-id="9a556-147">Objectives</span></span>

* <span data-ttu-id="9a556-148">更改 Unity 的声音配置，以使用 Microsoft 空间音质。</span><span class="sxs-lookup"><span data-stu-id="9a556-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="9a556-149">将三维声音添加到 Unity 中的对象。</span><span class="sxs-lookup"><span data-stu-id="9a556-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="9a556-150">说明</span><span class="sxs-lookup"><span data-stu-id="9a556-150">Instructions</span></span>

* <span data-ttu-id="9a556-151">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="9a556-151">Start Unity.</span></span>
* <span data-ttu-id="9a556-152">选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-152">Select **Open**.</span></span>
* <span data-ttu-id="9a556-153">导航到桌面并找到以前未存档的文件夹。</span><span class="sxs-lookup"><span data-stu-id="9a556-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="9a556-154">单击 " **Starting\Decibel** " 文件夹，然后按 "**选择文件夹**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="9a556-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="9a556-155">等待项目在 Unity 中加载。</span><span class="sxs-lookup"><span data-stu-id="9a556-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="9a556-156">在 " **项目**" 面板中，打开**Scenes\Decibel.unity**。</span><span class="sxs-lookup"><span data-stu-id="9a556-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="9a556-157">在 "**层次结构**" 面板中，展开 " **HologramCollection** " 并选择 " **P0LY**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="9a556-158">在检查器中，展开 " **AudioSource** "，注意没有 " **Spatialize** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="9a556-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="9a556-159">默认情况下，Unity 不会加载 spatializer 插件。</span><span class="sxs-lookup"><span data-stu-id="9a556-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="9a556-160">以下步骤将在项目中启用空间音质。</span><span class="sxs-lookup"><span data-stu-id="9a556-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="9a556-161">在 Unity 的顶部菜单中，参阅**编辑 > 音频 > 项目设置**。</span><span class="sxs-lookup"><span data-stu-id="9a556-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="9a556-162">找到**Spatializer 插件**下拉列表，并选择 " **MS HRTF Spatializer**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="9a556-163">在 "**层次结构**" 面板中，选择 " **HologramCollection > P0LY**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="9a556-164">在 "**检查器**" 面板中，找到 "**音频源**" 组件。</span><span class="sxs-lookup"><span data-stu-id="9a556-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="9a556-165">选中 " **Spatialize** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="9a556-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="9a556-166">将**空间混合**滑块一直拖到**3d**上，或在编辑框中输入**1** 。</span><span class="sxs-lookup"><span data-stu-id="9a556-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="9a556-167">现在，我们将在 Unity 中生成项目，并在 Visual Studio 中配置该解决方案。</span><span class="sxs-lookup"><span data-stu-id="9a556-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="9a556-168">在 Unity 中，选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="9a556-169">单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="9a556-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="9a556-170">选择 "**平台**" 列表中的 "**通用 Windows 平台**"，然后单击 "**切换平台**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="9a556-171">如果要专门针对 HoloLens 进行开发，请将 "**目标设备**" 设置为 " **hololens**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="9a556-172">否则，请将其留在**任何设备**上。</span><span class="sxs-lookup"><span data-stu-id="9a556-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="9a556-173">确保将 "**生成类型**" 设置为 " **D3D** "，并将 " **SDK** " 设置为 "**最新安装**的" （应为 SDK 16299 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="9a556-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="9a556-174">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="9a556-174">Click **Build**.</span></span>
7. <span data-ttu-id="9a556-175">创建名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="9a556-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="9a556-176">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="9a556-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="9a556-177">按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-177">Press **Select Folder**.</span></span>

<span data-ttu-id="9a556-178">当 Unity 完成后，将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="9a556-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="9a556-179">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="9a556-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="9a556-180">打开 "**分贝 Visual Studio 解决方案**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="9a556-181">如果部署到 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="9a556-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="9a556-182">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **x86**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="9a556-183">单击 "本地计算机" 按钮旁的下拉箭头，然后选择 "**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="9a556-184">输入**HoloLens 设备 IP 地址**，并将身份验证模式设置为**通用（未加密的协议）** 。</span><span class="sxs-lookup"><span data-stu-id="9a556-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="9a556-185">单击 "**选择**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-185">Click **Select**.</span></span> <span data-ttu-id="9a556-186">如果你不知道设备 IP 地址，请在 "设置" 中查找 " **> 网络 & Internet > 高级选项**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="9a556-187">在顶部菜单栏中，单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="9a556-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="9a556-188">如果这是首次部署到设备，则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="9a556-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="9a556-189">如果要部署到沉浸式耳机：</span><span class="sxs-lookup"><span data-stu-id="9a556-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="9a556-190">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **x64**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="9a556-191">确保将部署目标设置为 "**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="9a556-192">在顶部菜单栏中，单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="9a556-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="9a556-193">第2章-空间音效和交互</span><span class="sxs-lookup"><span data-stu-id="9a556-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="9a556-194">目标</span><span class="sxs-lookup"><span data-stu-id="9a556-194">Objectives</span></span>

* <span data-ttu-id="9a556-195">使用声音提高全息图的真实感。</span><span class="sxs-lookup"><span data-stu-id="9a556-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="9a556-196">使用声音定向用户的注视。</span><span class="sxs-lookup"><span data-stu-id="9a556-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="9a556-197">使用声音提供手势反馈。</span><span class="sxs-lookup"><span data-stu-id="9a556-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="9a556-198">第1部分-增强真实性</span><span class="sxs-lookup"><span data-stu-id="9a556-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9a556-199">关键概念</span><span class="sxs-lookup"><span data-stu-id="9a556-199">Key Concepts</span></span>

* <span data-ttu-id="9a556-200">Spatialize 全息影像声音。</span><span class="sxs-lookup"><span data-stu-id="9a556-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="9a556-201">应将声音源置于全息图上的适当位置。</span><span class="sxs-lookup"><span data-stu-id="9a556-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="9a556-202">声音的适当位置将取决于全息图。</span><span class="sxs-lookup"><span data-stu-id="9a556-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="9a556-203">例如，如果全息影像是人，则声音源应位于嘴附近，而不是英尺附近。</span><span class="sxs-lookup"><span data-stu-id="9a556-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9a556-204">说明</span><span class="sxs-lookup"><span data-stu-id="9a556-204">Instructions</span></span>

<span data-ttu-id="9a556-205">以下说明将 spatialized 声音附加到全息图。</span><span class="sxs-lookup"><span data-stu-id="9a556-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="9a556-206">在 "**层次结构**" 面板中，展开 " **HologramCollection** " 并选择 " **P0LY**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="9a556-207">在 "**检查器**" 面板的**AudioSource**中，单击 " **AudioClip** " 旁边的圆圈，并从弹出窗口中选择 " **PolyHover** "。</span><span class="sxs-lookup"><span data-stu-id="9a556-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="9a556-208">单击 "**输出**" 旁边的圆圈，并从弹出窗口中选择 " **SoundEffects** "。</span><span class="sxs-lookup"><span data-stu-id="9a556-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="9a556-209">项目分贝使用 Unity **AudioMixer**组件来启用调整声音组的音量级别。</span><span class="sxs-lookup"><span data-stu-id="9a556-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="9a556-210">通过以这种方式对声音进行分组，可以在保持每个声音的相对音量的同时调整总体音量。</span><span class="sxs-lookup"><span data-stu-id="9a556-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="9a556-211">在**AudioSource**中，展开 "**三维声音设置**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="9a556-212">将**Doppler 级别**设置为**0**。</span><span class="sxs-lookup"><span data-stu-id="9a556-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="9a556-213">如果将 Doppler 级别设置为零，则将禁用由运动（一张全息图或用户）导致的螺距变化。</span><span class="sxs-lookup"><span data-stu-id="9a556-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="9a556-214">Doppler 的典型示例是一种快速移动的汽车。</span><span class="sxs-lookup"><span data-stu-id="9a556-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="9a556-215">当汽车接近固定的侦听器时，引擎的跨度会上升。</span><span class="sxs-lookup"><span data-stu-id="9a556-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="9a556-216">当它通过侦听程序时，间距会降低距离。</span><span class="sxs-lookup"><span data-stu-id="9a556-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="9a556-217">第2部分-定向用户的注视</span><span class="sxs-lookup"><span data-stu-id="9a556-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9a556-218">关键概念</span><span class="sxs-lookup"><span data-stu-id="9a556-218">Key Concepts</span></span>

* <span data-ttu-id="9a556-219">使用声音吸引重要的全息影像。</span><span class="sxs-lookup"><span data-stu-id="9a556-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="9a556-220">此耳有助于指导眼睛的外观。</span><span class="sxs-lookup"><span data-stu-id="9a556-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="9a556-221">大脑有一些预期的预期。</span><span class="sxs-lookup"><span data-stu-id="9a556-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="9a556-222">了解预期的一个示例就是，鸟瞰一般都是人的水平。</span><span class="sxs-lookup"><span data-stu-id="9a556-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="9a556-223">如果用户听到了鸟瞰声，其初始反应就是查找。</span><span class="sxs-lookup"><span data-stu-id="9a556-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="9a556-224">如果在用户下放置鸟，会使其面向正确的声音方向，但无法根据需要查找的预期来找到全息影像。</span><span class="sxs-lookup"><span data-stu-id="9a556-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9a556-225">说明</span><span class="sxs-lookup"><span data-stu-id="9a556-225">Instructions</span></span>

<span data-ttu-id="9a556-226">以下说明允许 P0LY 隐藏在您后面，以便您可以使用声音查找全息图。</span><span class="sxs-lookup"><span data-stu-id="9a556-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="9a556-227">在 "**层次结构**" 面板中，选择 "**管理器**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="9a556-228">在**检查器**面板中，找到 "**语音输入处理程序**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="9a556-229">在**语音输入处理程序**中，展开 "**转到隐藏**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="9a556-230">将**No 函数**更改为**PolyActions. GoHide**。</span><span class="sxs-lookup"><span data-stu-id="9a556-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![关键字：中转隐藏](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="9a556-232">第3部分-手势反馈</span><span class="sxs-lookup"><span data-stu-id="9a556-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9a556-233">关键概念</span><span class="sxs-lookup"><span data-stu-id="9a556-233">Key Concepts</span></span>

* <span data-ttu-id="9a556-234">使用声音为用户提供积极的手势确认</span><span class="sxs-lookup"><span data-stu-id="9a556-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="9a556-235">不要严重影响用户的声音，</span><span class="sxs-lookup"><span data-stu-id="9a556-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="9a556-236">微妙的声音效果最好-不要会掩盖体验</span><span class="sxs-lookup"><span data-stu-id="9a556-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="9a556-237">说明</span><span class="sxs-lookup"><span data-stu-id="9a556-237">Instructions</span></span>

* <span data-ttu-id="9a556-238">在 "**层次结构**" 面板中，展开 " **HologramCollection**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9a556-239">展开 " **EnergyHub** "，然后选择 "**基本**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="9a556-240">在**检查器**面板中，单击 "**添加组件**" 并添加**手势声音处理程序**。</span><span class="sxs-lookup"><span data-stu-id="9a556-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="9a556-241">在**手势声音处理程序**中，单击 "**导航已启动的剪辑**和**导航已更新的剪辑**" 旁边的圆圈，并从弹出窗口中选择 " **RotateClick** "。</span><span class="sxs-lookup"><span data-stu-id="9a556-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="9a556-242">双击 "GestureSoundHandler" 以在 Visual Studio 中加载。</span><span class="sxs-lookup"><span data-stu-id="9a556-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="9a556-243">手势声音处理程序执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="9a556-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="9a556-244">创建和配置**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="9a556-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="9a556-245">将**AudioSource**放在适当**GameObject**的位置。</span><span class="sxs-lookup"><span data-stu-id="9a556-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="9a556-246">播放与该笔势关联的**AudioClip** 。</span><span class="sxs-lookup"><span data-stu-id="9a556-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="9a556-247">生成和部署</span><span class="sxs-lookup"><span data-stu-id="9a556-247">Build and Deploy</span></span>

1. <span data-ttu-id="9a556-248">在 Unity 中，选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="9a556-249">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="9a556-249">Click **Build**.</span></span>
3. <span data-ttu-id="9a556-250">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="9a556-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="9a556-251">按 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-251">Press **Select Folder**.</span></span>

<span data-ttu-id="9a556-252">检查工具栏是否显示 "发布"、"x86" 或 "x64"，以及 "远程设备"。</span><span class="sxs-lookup"><span data-stu-id="9a556-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="9a556-253">如果不是，则这是 Visual Studio 的代码实例。</span><span class="sxs-lookup"><span data-stu-id="9a556-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="9a556-254">可能需要从应用程序文件夹重新打开解决方案。</span><span class="sxs-lookup"><span data-stu-id="9a556-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="9a556-255">如果系统提示，请重新加载项目文件。</span><span class="sxs-lookup"><span data-stu-id="9a556-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="9a556-256">如前所述，从 Visual Studio 部署。</span><span class="sxs-lookup"><span data-stu-id="9a556-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="9a556-257">部署应用程序后：</span><span class="sxs-lookup"><span data-stu-id="9a556-257">After the application is deployed:</span></span>

* <span data-ttu-id="9a556-258">观察在 P0LY 移动时声音如何变化。</span><span class="sxs-lookup"><span data-stu-id="9a556-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="9a556-259">说 *"转到隐藏"* ，使 P0LY 移到你后面的位置。</span><span class="sxs-lookup"><span data-stu-id="9a556-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="9a556-260">通过声音查找。</span><span class="sxs-lookup"><span data-stu-id="9a556-260">Find it by the sound.</span></span>
* <span data-ttu-id="9a556-261">注视能源中心的底部。</span><span class="sxs-lookup"><span data-stu-id="9a556-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="9a556-262">点击并向左或向右拖动以旋转全息影像，并注意单击声音如何确认手势。</span><span class="sxs-lookup"><span data-stu-id="9a556-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="9a556-263">注意：有一个文本面板会与你一起标记。</span><span class="sxs-lookup"><span data-stu-id="9a556-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="9a556-264">这将包含可在本课程中使用的可用语音命令。</span><span class="sxs-lookup"><span data-stu-id="9a556-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="9a556-265">第3章-空间音质和空间映射</span><span class="sxs-lookup"><span data-stu-id="9a556-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="9a556-266">目标</span><span class="sxs-lookup"><span data-stu-id="9a556-266">Objectives</span></span>

* <span data-ttu-id="9a556-267">使用声音确认全息影像与真实环境之间的交互。</span><span class="sxs-lookup"><span data-stu-id="9a556-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="9a556-268">使用实物遮蔽声音。</span><span class="sxs-lookup"><span data-stu-id="9a556-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="9a556-269">第1部分-物理世界交互</span><span class="sxs-lookup"><span data-stu-id="9a556-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9a556-270">关键概念</span><span class="sxs-lookup"><span data-stu-id="9a556-270">Key Concepts</span></span>

* <span data-ttu-id="9a556-271">当遇到图面或其他对象时，物理对象通常会发出声音。</span><span class="sxs-lookup"><span data-stu-id="9a556-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="9a556-272">声音应在体验中是适当的上下文。</span><span class="sxs-lookup"><span data-stu-id="9a556-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="9a556-273">例如，对表设置杯会使声音更安静，而不是在金属片上放置 boulder。</span><span class="sxs-lookup"><span data-stu-id="9a556-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9a556-274">说明</span><span class="sxs-lookup"><span data-stu-id="9a556-274">Instructions</span></span>

* <span data-ttu-id="9a556-275">在 "**层次结构**" 面板中，展开 " **HologramCollection**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9a556-276">展开 " **EnergyHub**"，选择 "**基本**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="9a556-277">在 "**检查器**" 面板中，单击 "**添加组件**"，然后单击 "添加**声音和操作**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="9a556-278">在中，**单击以放置声音和操作**：</span><span class="sxs-lookup"><span data-stu-id="9a556-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="9a556-279">**在点击时选中 "父项"** 。</span><span class="sxs-lookup"><span data-stu-id="9a556-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="9a556-280">设置要**放置**的**放置声音**。</span><span class="sxs-lookup"><span data-stu-id="9a556-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="9a556-281">将**拾取声音**设置为**装货**。</span><span class="sxs-lookup"><span data-stu-id="9a556-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="9a556-282">在 "**分拣" 操作**和 **"放置" 操作**中，按右下方的 "+"。</span><span class="sxs-lookup"><span data-stu-id="9a556-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="9a556-283">将 EnergyHub 从场景拖到**无（对象）** 字段。</span><span class="sxs-lookup"><span data-stu-id="9a556-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="9a556-284">在 **"选取操作**" 下，单击 "**无函数**" -> **EnergyHubBase** -> **ResetAnimation**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="9a556-285">在 **"放置时" 操作**下，单击 "**无函数**" -> **EnergyHubBase** -> **OnSelect**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![点击以放入声音和操作](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="9a556-287">第2部分-声音封闭</span><span class="sxs-lookup"><span data-stu-id="9a556-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9a556-288">关键概念</span><span class="sxs-lookup"><span data-stu-id="9a556-288">Key Concepts</span></span>

* <span data-ttu-id="9a556-289">声音，如光源，可以是封闭像素。</span><span class="sxs-lookup"><span data-stu-id="9a556-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="9a556-290">典型的示例是音乐会厅。</span><span class="sxs-lookup"><span data-stu-id="9a556-290">A classic example is a concert hall.</span></span> <span data-ttu-id="9a556-291">当某个侦听器在大厅外且门闭合时，音乐听起来 muffled。</span><span class="sxs-lookup"><span data-stu-id="9a556-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="9a556-292">通常还会减少容量。</span><span class="sxs-lookup"><span data-stu-id="9a556-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="9a556-293">打开门后，就会听到真实音量的所有声音。</span><span class="sxs-lookup"><span data-stu-id="9a556-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="9a556-294">高频声音通常会超出低频率。</span><span class="sxs-lookup"><span data-stu-id="9a556-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9a556-295">说明</span><span class="sxs-lookup"><span data-stu-id="9a556-295">Instructions</span></span>

* <span data-ttu-id="9a556-296">在 "**层次结构**" 面板中，展开 " **HologramCollection** " 并选择 " **P0LY**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="9a556-297">在**检查器**面板中，单击 "**添加组件**" 并添加**音频发射器**。</span><span class="sxs-lookup"><span data-stu-id="9a556-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="9a556-298">音频发射器类提供以下功能：</span><span class="sxs-lookup"><span data-stu-id="9a556-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="9a556-299">还原对**AudioSource**卷的任何更改。</span><span class="sxs-lookup"><span data-stu-id="9a556-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="9a556-300">按照**AudioEmitter**连接到的**GameObject**的方向，从用户的位置执行**RaycastNonAlloc** 。</span><span class="sxs-lookup"><span data-stu-id="9a556-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="9a556-301">RaycastNonAlloc 方法用作性能优化，以限制分配和返回的结果数。</span><span class="sxs-lookup"><span data-stu-id="9a556-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="9a556-302">对于遇到的每个**IAudioInfluencer** ，将调用**ApplyEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="9a556-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="9a556-303">对于不再遇到的每个以前的**IAudioInfluencer** ，请调用**RemoveEffect**方法。</span><span class="sxs-lookup"><span data-stu-id="9a556-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="9a556-304">请注意，AudioEmitter 对人为时间刻度的更新，而不是每个框架的更新。</span><span class="sxs-lookup"><span data-stu-id="9a556-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="9a556-305">这样做是因为，人们通常不能以足够快的速度移动，因此，需要比每个季度或半秒钟的频率更频繁地进行更新。</span><span class="sxs-lookup"><span data-stu-id="9a556-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="9a556-306">从一个位置到另一个位置快速传送的全息影像可能会突破错觉。</span><span class="sxs-lookup"><span data-stu-id="9a556-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="9a556-307">在 "**层次结构**" 面板中，展开 " **HologramCollection**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9a556-308">展开 " **EnergyHub** " 并选择 " **BlobOutside**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="9a556-309">在**检查器**面板中，单击 "**添加组件**" 并添加**音频 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="9a556-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="9a556-310">在**音频 Occluder**中，将 "**截止频率**" 设置为**1500**。</span><span class="sxs-lookup"><span data-stu-id="9a556-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="9a556-311">此设置将 AudioSource 频率限制为 1500 Hz 和更低。</span><span class="sxs-lookup"><span data-stu-id="9a556-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="9a556-312">将**Volume Pass**设置为**0.9**。</span><span class="sxs-lookup"><span data-stu-id="9a556-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="9a556-313">此设置将 AudioSource 的量降低到其当前级别的90%。</span><span class="sxs-lookup"><span data-stu-id="9a556-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="9a556-314">音频 Occluder 实现 IAudioInfluencer：</span><span class="sxs-lookup"><span data-stu-id="9a556-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="9a556-315">使用附加到**AudioSource**托管的**AudioLowPassFilter**的封闭**效果。**</span><span class="sxs-lookup"><span data-stu-id="9a556-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="9a556-316">将卷衰减应用于 AudioSource。</span><span class="sxs-lookup"><span data-stu-id="9a556-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="9a556-317">通过设置非特定截止频率并禁用筛选器来禁用该效果。</span><span class="sxs-lookup"><span data-stu-id="9a556-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="9a556-318">用于中性的频率为 22 kHz （22000 Hz）。</span><span class="sxs-lookup"><span data-stu-id="9a556-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="9a556-319">选择此频率的原因是，它的最大频率为人体耳可以听到的最大公称，这不会影响声音。</span><span class="sxs-lookup"><span data-stu-id="9a556-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="9a556-320">在 "**层次结构**" 面板中，选择 " **SpatialMapping**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="9a556-321">在**检查器**面板中，单击 "**添加组件**" 并添加**音频 Occluder**。</span><span class="sxs-lookup"><span data-stu-id="9a556-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="9a556-322">在**音频 Occluder**中，将 "**截止频率**" 设置为**750**。</span><span class="sxs-lookup"><span data-stu-id="9a556-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="9a556-323">如果多个 occluders 位于用户与**AudioEmitter**之间的路径中，则会将最低频率应用于筛选器。</span><span class="sxs-lookup"><span data-stu-id="9a556-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="9a556-324">将**Volume Pass**设置为**0.75**。</span><span class="sxs-lookup"><span data-stu-id="9a556-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="9a556-325">如果多个 occluders 位于用户与**AudioEmitter**之间的路径中，则会应用添加性地。</span><span class="sxs-lookup"><span data-stu-id="9a556-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="9a556-326">在 "**层次结构**" 面板中，选择 "**管理器**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="9a556-327">在 "**检查器**" 面板中，展开 "**语音输入处理程序**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="9a556-328">在**语音输入处理程序**中，展开 "**转到**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="9a556-329">将**No 函数**更改为**PolyActions. GoCharge**。</span><span class="sxs-lookup"><span data-stu-id="9a556-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![关键字：中转](images/gocharge.png)

* <span data-ttu-id="9a556-331">**在此处**展开。</span><span class="sxs-lookup"><span data-stu-id="9a556-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="9a556-332">将**No 函数**更改为**PolyActions. 卷土重来**。</span><span class="sxs-lookup"><span data-stu-id="9a556-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![关键字：此处提供](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="9a556-334">生成和部署</span><span class="sxs-lookup"><span data-stu-id="9a556-334">Build and Deploy</span></span>

* <span data-ttu-id="9a556-335">如前所述，在 Unity 中生成项目，并在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="9a556-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="9a556-336">部署应用程序后：</span><span class="sxs-lookup"><span data-stu-id="9a556-336">After the application is deployed:</span></span>

* <span data-ttu-id="9a556-337">说 *"走电"* ，让 P0LY 进入能量中心。</span><span class="sxs-lookup"><span data-stu-id="9a556-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="9a556-338">请注意声音的变化。</span><span class="sxs-lookup"><span data-stu-id="9a556-338">Note the change in the sound.</span></span> <span data-ttu-id="9a556-339">这听起来 muffled。</span><span class="sxs-lookup"><span data-stu-id="9a556-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="9a556-340">如果你能够在你与能源中心之间定位墙壁或其他对象，你应该注意到 muffling 的声音，因为现实世界封闭了。</span><span class="sxs-lookup"><span data-stu-id="9a556-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="9a556-341">说 *"现在*就可以"，让 P0LY 离开能源中心，并将其放在您前面。</span><span class="sxs-lookup"><span data-stu-id="9a556-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="9a556-342">请注意，一旦 P0LY 退出能源中心，就会删除声音封闭。</span><span class="sxs-lookup"><span data-stu-id="9a556-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="9a556-343">如果你仍在封闭，P0LY 可能会被现实世界封闭像素。</span><span class="sxs-lookup"><span data-stu-id="9a556-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="9a556-344">尝试移动以确保对 P0LY 有清楚的视觉。</span><span class="sxs-lookup"><span data-stu-id="9a556-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="9a556-345">第3部分-房间模型</span><span class="sxs-lookup"><span data-stu-id="9a556-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9a556-346">关键概念</span><span class="sxs-lookup"><span data-stu-id="9a556-346">Key Concepts</span></span>

* <span data-ttu-id="9a556-347">空间大小提供了 subliminal 的队列，它们有助于进行合理的本地化。</span><span class="sxs-lookup"><span data-stu-id="9a556-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="9a556-348">房间模型是按**AudioSource**设置的。</span><span class="sxs-lookup"><span data-stu-id="9a556-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="9a556-349">[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)提供用于设置房间模型的代码。</span><span class="sxs-lookup"><span data-stu-id="9a556-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="9a556-350">对于混合现实体验，请选择最适合于现实世界空间的房间模型。</span><span class="sxs-lookup"><span data-stu-id="9a556-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="9a556-351">如果要创建虚拟现实方案，请选择最适合虚拟环境的房间模型。</span><span class="sxs-lookup"><span data-stu-id="9a556-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="9a556-352">第4章-声音设计</span><span class="sxs-lookup"><span data-stu-id="9a556-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="9a556-353">目标</span><span class="sxs-lookup"><span data-stu-id="9a556-353">Objectives</span></span>

* <span data-ttu-id="9a556-354">了解有效的声音设计的注意事项。</span><span class="sxs-lookup"><span data-stu-id="9a556-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="9a556-355">了解混合技巧和指导原则。</span><span class="sxs-lookup"><span data-stu-id="9a556-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="9a556-356">第1部分-声音和体验设计</span><span class="sxs-lookup"><span data-stu-id="9a556-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="9a556-357">本部分介绍关键的声音，并体验设计注意事项和指导原则。</span><span class="sxs-lookup"><span data-stu-id="9a556-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="9a556-358">规范化所有声音</span><span class="sxs-lookup"><span data-stu-id="9a556-358">Normalize all sounds</span></span>

<span data-ttu-id="9a556-359">这样就无需使用特殊案例代码调整每个声音的音量级别，这可能非常耗时，并且限制了轻松更新声音文件的能力。</span><span class="sxs-lookup"><span data-stu-id="9a556-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="9a556-360">设计 untethered 体验</span><span class="sxs-lookup"><span data-stu-id="9a556-360">Design for an untethered experience</span></span>

<span data-ttu-id="9a556-361">HoloLens 是完全包含的 untethered 全息计算机。</span><span class="sxs-lookup"><span data-stu-id="9a556-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="9a556-362">你的用户可以在移动时使用你的体验。</span><span class="sxs-lookup"><span data-stu-id="9a556-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="9a556-363">务必通过浏览来测试您的音频组合。</span><span class="sxs-lookup"><span data-stu-id="9a556-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="9a556-364">从逻辑位置在全息影像上发出声音</span><span class="sxs-lookup"><span data-stu-id="9a556-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="9a556-365">在现实生活中，狗不会吠其尾部，人类的语音不会来自其英尺。</span><span class="sxs-lookup"><span data-stu-id="9a556-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="9a556-366">避免在全息影像的意外部分发出声音。</span><span class="sxs-lookup"><span data-stu-id="9a556-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="9a556-367">对于小全息影像，从几何图形中心开始发出声音是合理的。</span><span class="sxs-lookup"><span data-stu-id="9a556-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="9a556-368">熟悉的声音是最可本地化的</span><span class="sxs-lookup"><span data-stu-id="9a556-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="9a556-369">人为语音和音乐非常易于本地化。</span><span class="sxs-lookup"><span data-stu-id="9a556-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="9a556-370">如果有人调用了您的姓名，则可以从语音的方向和距离。</span><span class="sxs-lookup"><span data-stu-id="9a556-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="9a556-371">简短，不熟悉的声音更难本地化。</span><span class="sxs-lookup"><span data-stu-id="9a556-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="9a556-372">Cognizant 用户期望</span><span class="sxs-lookup"><span data-stu-id="9a556-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="9a556-373">生活经验使我们能够确定声音位置。</span><span class="sxs-lookup"><span data-stu-id="9a556-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="9a556-374">这就是人们语音特别容易本地化的原因之一。</span><span class="sxs-lookup"><span data-stu-id="9a556-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="9a556-375">发出声音时，请注意用户的预期预期。</span><span class="sxs-lookup"><span data-stu-id="9a556-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="9a556-376">例如，当有人听到了他们通常会查找的鸟瞰歌曲时，因为鸟瞰通常会位于视线的上方（飞行或树形上）。</span><span class="sxs-lookup"><span data-stu-id="9a556-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="9a556-377">用户打开正确的声音方向并不是很常见，而是在无法找到全息影像时在错误的垂直方向上看起来不确定的。</span><span class="sxs-lookup"><span data-stu-id="9a556-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="9a556-378">避免隐藏发射器</span><span class="sxs-lookup"><span data-stu-id="9a556-378">Avoid hidden emitters</span></span>

<span data-ttu-id="9a556-379">在实际情况下，如果听到声音，通常可以识别出发出声音的对象。</span><span class="sxs-lookup"><span data-stu-id="9a556-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="9a556-380">在您的体验中，这也应为 true。</span><span class="sxs-lookup"><span data-stu-id="9a556-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="9a556-381">用户听听声音非常不安，知道声音出自何处，看不到对象。</span><span class="sxs-lookup"><span data-stu-id="9a556-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="9a556-382">此准则有一些例外情况。</span><span class="sxs-lookup"><span data-stu-id="9a556-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="9a556-383">例如，字段中的 crickets 等环境声音无需可见。</span><span class="sxs-lookup"><span data-stu-id="9a556-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="9a556-384">生活经验为我们熟悉这些声音的来源，无需查看。</span><span class="sxs-lookup"><span data-stu-id="9a556-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="9a556-385">第2部分-混音</span><span class="sxs-lookup"><span data-stu-id="9a556-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="9a556-386">在 HoloLens 上将混合目标设定为70% 的卷</span><span class="sxs-lookup"><span data-stu-id="9a556-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="9a556-387">混合现实体验允许在现实世界中查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="9a556-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="9a556-388">它们还应该允许听真实世界声音。</span><span class="sxs-lookup"><span data-stu-id="9a556-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="9a556-389">利用70% 的音量目标，用户可以在他们周围倾听世界，并获得你的体验。</span><span class="sxs-lookup"><span data-stu-id="9a556-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="9a556-390">100% 卷上的 HoloLens 应 drown 外部声音</span><span class="sxs-lookup"><span data-stu-id="9a556-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="9a556-391">100% 的卷级别与虚拟现实体验类似。</span><span class="sxs-lookup"><span data-stu-id="9a556-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="9a556-392">用户在视觉上传输到不同的世界。</span><span class="sxs-lookup"><span data-stu-id="9a556-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="9a556-393">相同的呼叫时应为 true。</span><span class="sxs-lookup"><span data-stu-id="9a556-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="9a556-394">使用 Unity AudioMixer 调整声音类别</span><span class="sxs-lookup"><span data-stu-id="9a556-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="9a556-395">设计你的组合时，创建声音类别并能够将其音量增加或减少为一个单元通常很有帮助。</span><span class="sxs-lookup"><span data-stu-id="9a556-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="9a556-396">这会保留每个声音的相对级别，同时使整体组合的快速而简单的更改。</span><span class="sxs-lookup"><span data-stu-id="9a556-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="9a556-397">常见类别包括：声音效果、环境、语音转移和背景音乐。</span><span class="sxs-lookup"><span data-stu-id="9a556-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="9a556-398">基于用户的注视混合声音</span><span class="sxs-lookup"><span data-stu-id="9a556-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="9a556-399">通常，根据用户所在的位置（或不需要）来更改声音混合，这通常很有用。</span><span class="sxs-lookup"><span data-stu-id="9a556-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="9a556-400">此方法的一个常见用途是降低全息帧之外的全息影像的音量级别，使用户能够更轻松地将重点放在其前面的信息上。</span><span class="sxs-lookup"><span data-stu-id="9a556-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="9a556-401">另一种用途是增加声音量，以吸引用户关注重要事件。</span><span class="sxs-lookup"><span data-stu-id="9a556-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="9a556-402">构建混合</span><span class="sxs-lookup"><span data-stu-id="9a556-402">Building your mix</span></span>

<span data-ttu-id="9a556-403">在构建组合时，建议从体验背景音频开始，并根据重要性添加层。</span><span class="sxs-lookup"><span data-stu-id="9a556-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="9a556-404">通常，这会导致每个层都大于上一个层。</span><span class="sxs-lookup"><span data-stu-id="9a556-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="9a556-405">应该构想你的混合为反转漏斗图，最重要的是最不重要的（通常是 quietest 的声音），因此建议将你的混合与下图类似。</span><span class="sxs-lookup"><span data-stu-id="9a556-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![声音混合结构](images/soundlevels.png)

<span data-ttu-id="9a556-407">语音转移是一个有趣的方案。</span><span class="sxs-lookup"><span data-stu-id="9a556-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="9a556-408">根据你创建的体验，你可能想要使用立体声（未本地化）声音或 spatialize 你的语音转移。</span><span class="sxs-lookup"><span data-stu-id="9a556-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="9a556-409">两个 Microsoft 发布的体验演示了每个方案的极佳示例。</span><span class="sxs-lookup"><span data-stu-id="9a556-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="9a556-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87)使用立体声声音。</span><span class="sxs-lookup"><span data-stu-id="9a556-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="9a556-411">当讲述人描述正在查看的位置时，声音是一致的，并且不会根据用户的位置而变化。</span><span class="sxs-lookup"><span data-stu-id="9a556-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="9a556-412">这使讲述人可以在不离开环境 spatialized 声音的情况下描述场景。</span><span class="sxs-lookup"><span data-stu-id="9a556-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="9a556-413">[片段](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8)使用 spatialized 的语音。</span><span class="sxs-lookup"><span data-stu-id="9a556-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="9a556-414">侦探的声音用于帮助用户关注重要的线索，就像实际人在房间里。</span><span class="sxs-lookup"><span data-stu-id="9a556-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="9a556-415">这样，就可以更好地浸入式解决谜的体验。</span><span class="sxs-lookup"><span data-stu-id="9a556-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="9a556-416">第3部分-性能</span><span class="sxs-lookup"><span data-stu-id="9a556-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="9a556-417">CPU 使用情况</span><span class="sxs-lookup"><span data-stu-id="9a556-417">CPU usage</span></span>

<span data-ttu-id="9a556-418">使用空间音效时，10-12 发射器会消耗约12% 的 CPU。</span><span class="sxs-lookup"><span data-stu-id="9a556-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="9a556-419">流式传输长音频文件</span><span class="sxs-lookup"><span data-stu-id="9a556-419">Stream long audio files</span></span>

<span data-ttu-id="9a556-420">音频数据可能很大，尤其是在常见采样速率（44.1 和 48 kHz）上。</span><span class="sxs-lookup"><span data-stu-id="9a556-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="9a556-421">一般规则是，应流式传输超过 5-10 秒的音频文件，以降低应用程序内存使用量。</span><span class="sxs-lookup"><span data-stu-id="9a556-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="9a556-422">在 Unity 中，可以在文件的导入设置中标记音频文件以进行流式传输。</span><span class="sxs-lookup"><span data-stu-id="9a556-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![音频导入设置](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="9a556-424">第5章-特殊效果</span><span class="sxs-lookup"><span data-stu-id="9a556-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="9a556-425">目标</span><span class="sxs-lookup"><span data-stu-id="9a556-425">Objectives</span></span>

* <span data-ttu-id="9a556-426">将深度添加到 "幻窗口"。</span><span class="sxs-lookup"><span data-stu-id="9a556-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="9a556-427">将用户带入虚拟世界。</span><span class="sxs-lookup"><span data-stu-id="9a556-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="9a556-428">魔术窗口</span><span class="sxs-lookup"><span data-stu-id="9a556-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9a556-429">关键概念</span><span class="sxs-lookup"><span data-stu-id="9a556-429">Key Concepts</span></span>

* <span data-ttu-id="9a556-430">将视图创建到隐藏世界中，这在视觉上非常引人注目。</span><span class="sxs-lookup"><span data-stu-id="9a556-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="9a556-431">当全息图或用户处于隐藏世界附近时，通过添加音频效果来增强真实性。</span><span class="sxs-lookup"><span data-stu-id="9a556-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9a556-432">说明</span><span class="sxs-lookup"><span data-stu-id="9a556-432">Instructions</span></span>

* <span data-ttu-id="9a556-433">在 "**层次结构**" 面板中，展开 " **HologramCollection** " 并选择 " **Underworld**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="9a556-434">展开 " **Underworld** " 并选择 " **VoiceSource**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="9a556-435">在**检查器**面板中，单击 "**添加组件**" 并添加 "**用户语音效果**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="9a556-436">**AudioSource**组件将添加到**VoiceSource**中。</span><span class="sxs-lookup"><span data-stu-id="9a556-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="9a556-437">在**AudioSource**中，将 "**输出**" 设置为**UserVoice （混音器）** 。</span><span class="sxs-lookup"><span data-stu-id="9a556-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="9a556-438">选中 " **Spatialize** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="9a556-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="9a556-439">将**空间混合**滑块一直拖到**3d**上，或在编辑框中输入**1** 。</span><span class="sxs-lookup"><span data-stu-id="9a556-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="9a556-440">展开 "**三维声音设置**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="9a556-441">将**Doppler 级别**设置为**0**。</span><span class="sxs-lookup"><span data-stu-id="9a556-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="9a556-442">在 "**用户语音效果**" 中，将**父对象**从场景中设置为**Underworld** 。</span><span class="sxs-lookup"><span data-stu-id="9a556-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="9a556-443">将**最大距离**设置为**1**。</span><span class="sxs-lookup"><span data-stu-id="9a556-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="9a556-444">设置**最大距离**会告诉**用户语音效果**在启用此效果之前，用户必须先到父对象。</span><span class="sxs-lookup"><span data-stu-id="9a556-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="9a556-445">在 "**用户语音效果**" 中，展开 " **Chorus 参数**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="9a556-446">将**深度**设置为**0.1**。</span><span class="sxs-lookup"><span data-stu-id="9a556-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="9a556-447">依次点击 " **1**"、" **2 卷**" 和 " **3 卷**到**0.8**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="9a556-448">将**原始**音量设置为**0.5**。</span><span class="sxs-lookup"><span data-stu-id="9a556-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="9a556-449">以前的设置配置用于向用户语音添加丰富的 Unity **AudioChorusFilter**的参数。</span><span class="sxs-lookup"><span data-stu-id="9a556-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="9a556-450">在 "**用户语音效果**" 中，展开 " **Echo Parameters**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="9a556-451">将**延迟**设置为**300**</span><span class="sxs-lookup"><span data-stu-id="9a556-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="9a556-452">将**衰减比率**设置为**0.2**。</span><span class="sxs-lookup"><span data-stu-id="9a556-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="9a556-453">将**原始**音量设置为**0**。</span><span class="sxs-lookup"><span data-stu-id="9a556-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="9a556-454">以前的设置配置用于使用户的语音回显的 Unity **AudioEchoFilter**的参数。</span><span class="sxs-lookup"><span data-stu-id="9a556-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="9a556-455">用户语音效果脚本负责：</span><span class="sxs-lookup"><span data-stu-id="9a556-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="9a556-456">测量用户与脚本附加到的**GameObject**之间的距离。</span><span class="sxs-lookup"><span data-stu-id="9a556-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="9a556-457">确定用户是否面向**GameObject**。</span><span class="sxs-lookup"><span data-stu-id="9a556-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="9a556-458">对于启用的效果，用户必须面向 GameObject，而不考虑距离。</span><span class="sxs-lookup"><span data-stu-id="9a556-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="9a556-459">将**AudioChorusFilter**和**AudioEchoFilter**应用和配置到**AudioSource**。</span><span class="sxs-lookup"><span data-stu-id="9a556-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="9a556-460">禁用筛选器以禁用该效果。</span><span class="sxs-lookup"><span data-stu-id="9a556-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="9a556-461">用户语音效果使用[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)中的 Mic Stream 选择器组件选择高质量的语音流并将其路由到 Unity 的音频系统。</span><span class="sxs-lookup"><span data-stu-id="9a556-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="9a556-462">在 "**层次结构**" 面板中，选择 "**管理器**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="9a556-463">在 "**检查器**" 面板中，展开 "**语音输入处理程序**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="9a556-464">在**语音输入处理程序**中，展开**Show Underworld**。</span><span class="sxs-lookup"><span data-stu-id="9a556-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="9a556-465">将**No 函数**更改为**UnderworldBase. OnEnable**。</span><span class="sxs-lookup"><span data-stu-id="9a556-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![关键字： Show Underworld](images/showunderworld.png)

* <span data-ttu-id="9a556-467">展开 "**隐藏 Underworld**"。</span><span class="sxs-lookup"><span data-stu-id="9a556-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="9a556-468">将**No 函数**更改为**UnderworldBase. OnDisable**。</span><span class="sxs-lookup"><span data-stu-id="9a556-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![关键字：隐藏 Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="9a556-470">生成和部署</span><span class="sxs-lookup"><span data-stu-id="9a556-470">Build and Deploy</span></span>

* <span data-ttu-id="9a556-471">如前所述，在 Unity 中生成项目，并在 Visual Studio 中部署。</span><span class="sxs-lookup"><span data-stu-id="9a556-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="9a556-472">部署应用程序后：</span><span class="sxs-lookup"><span data-stu-id="9a556-472">After the application is deployed:</span></span>

* <span data-ttu-id="9a556-473">面部面（墙壁、楼层、桌子），并说 *"Show Underworld"* 。</span><span class="sxs-lookup"><span data-stu-id="9a556-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="9a556-474">将显示 underworld，所有其他全息影像都将隐藏。</span><span class="sxs-lookup"><span data-stu-id="9a556-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="9a556-475">如果看不到 underworld，请确保您面对的是实际的表面。</span><span class="sxs-lookup"><span data-stu-id="9a556-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="9a556-476">Underworld 全息图1米内的方法，开始谈话。</span><span class="sxs-lookup"><span data-stu-id="9a556-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="9a556-477">现在音频效果适用于你的语音！</span><span class="sxs-lookup"><span data-stu-id="9a556-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="9a556-478">退出 underworld 并注意如何不再应用该效果。</span><span class="sxs-lookup"><span data-stu-id="9a556-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="9a556-479">说 *"隐藏 Underworld"* 以隐藏 Underworld。</span><span class="sxs-lookup"><span data-stu-id="9a556-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="9a556-480">Underworld 将隐藏，并且以前隐藏的全息影像会重新出现。</span><span class="sxs-lookup"><span data-stu-id="9a556-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="9a556-481">结束</span><span class="sxs-lookup"><span data-stu-id="9a556-481">The End</span></span>

<span data-ttu-id="9a556-482">恭喜你！</span><span class="sxs-lookup"><span data-stu-id="9a556-482">Congratulations!</span></span> <span data-ttu-id="9a556-483">你现在已经完成了**MR 空间220：空间音质**。</span><span class="sxs-lookup"><span data-stu-id="9a556-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="9a556-484">听世界，让你的体验生活生动！</span><span class="sxs-lookup"><span data-stu-id="9a556-484">Listen to the world and bring your experiences to life with sound!</span></span>
