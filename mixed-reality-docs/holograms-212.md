---
title: MR 输入 212-语音
description: 按照此编码演练操作, 使用 Unity、Visual Studio 和 HoloLens 来了解语音概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 学院, 教程, 语音
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522356"
---
>[!NOTE]
><span data-ttu-id="10484-104">混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="10484-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="10484-105">因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="10484-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="10484-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="10484-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="10484-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="10484-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="10484-108">将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="10484-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="10484-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="10484-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="10484-110">MR 输入 212:语音</span><span class="sxs-lookup"><span data-stu-id="10484-110">MR Input 212: Voice</span></span>

<span data-ttu-id="10484-111">[语音输入](voice-input.md)提供了另一种与全息影像交互的方法。</span><span class="sxs-lookup"><span data-stu-id="10484-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="10484-112">语音命令的工作方式非常简单。</span><span class="sxs-lookup"><span data-stu-id="10484-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="10484-113">设计语音命令, 以便:</span><span class="sxs-lookup"><span data-stu-id="10484-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="10484-114">固有</span><span class="sxs-lookup"><span data-stu-id="10484-114">Natural</span></span>
* <span data-ttu-id="10484-115">易于记住</span><span class="sxs-lookup"><span data-stu-id="10484-115">Easy to remember</span></span>
* <span data-ttu-id="10484-116">适当上下文</span><span class="sxs-lookup"><span data-stu-id="10484-116">Context appropriate</span></span>
* <span data-ttu-id="10484-117">与同一上下文中的其他选项完全不同</span><span class="sxs-lookup"><span data-stu-id="10484-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="10484-118">在[先生/女士 101](holograms-101.md)中, 我们使用 KeywordRecognizer 来构建两个简单的语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="10484-119">在 MR 输入212中, 我们将深入探讨并了解如何:</span><span class="sxs-lookup"><span data-stu-id="10484-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="10484-120">设计针对 HoloLens 语音引擎进行了优化的语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="10484-121">使用户了解可用的语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="10484-122">确认我们听到了用户的语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="10484-123">使用听写识别器了解用户所说的内容。</span><span class="sxs-lookup"><span data-stu-id="10484-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="10484-124">使用语法识别器侦听基于 SRGS 或语音识别语法规范的命令。</span><span class="sxs-lookup"><span data-stu-id="10484-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="10484-125">在本课程中, 我们将重新访问模型资源管理器, 该资源管理器是在[MR input 210](holograms-210.md)和[mr input 211](holograms-211.md)中构建的。</span><span class="sxs-lookup"><span data-stu-id="10484-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="10484-126">以下各章中嵌入的视频使用较旧版本的 Unity 和混合现实工具包记录。</span><span class="sxs-lookup"><span data-stu-id="10484-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="10484-127">虽然分步说明准确且最新, 但你可能会看到处于过期状态的相应视频中的脚本和视觉对象。</span><span class="sxs-lookup"><span data-stu-id="10484-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="10484-128">视频仍包含在 posterity 中, 因为涵盖的概念仍适用。</span><span class="sxs-lookup"><span data-stu-id="10484-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="10484-129">设备支持</span><span class="sxs-lookup"><span data-stu-id="10484-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="10484-130">摘要</span><span class="sxs-lookup"><span data-stu-id="10484-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="10484-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="10484-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="10484-132"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="10484-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="10484-133">MR 输入 212:语音</span><span class="sxs-lookup"><span data-stu-id="10484-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="10484-134">✔️</span><span class="sxs-lookup"><span data-stu-id="10484-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="10484-135">✔️</span><span class="sxs-lookup"><span data-stu-id="10484-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="10484-136">开始之前</span><span class="sxs-lookup"><span data-stu-id="10484-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="10484-137">先决条件</span><span class="sxs-lookup"><span data-stu-id="10484-137">Prerequisites</span></span>

* <span data-ttu-id="10484-138">配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="10484-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="10484-139">一些基本C#的编程能力。</span><span class="sxs-lookup"><span data-stu-id="10484-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="10484-140">应已完成[尊敬的基本知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="10484-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="10484-141">应已完成[MR 输入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="10484-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="10484-142">应已完成[MR 输入 211](holograms-211.md)。</span><span class="sxs-lookup"><span data-stu-id="10484-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="10484-143">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="10484-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="10484-144">项目文件</span><span class="sxs-lookup"><span data-stu-id="10484-144">Project files</span></span>

* <span data-ttu-id="10484-145">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)。</span><span class="sxs-lookup"><span data-stu-id="10484-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="10484-146">需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="10484-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="10484-147">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="10484-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="10484-148">如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)找到。</span><span class="sxs-lookup"><span data-stu-id="10484-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="10484-149">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="10484-149">Errata and Notes</span></span>

* <span data-ttu-id="10484-150">需要在 Visual Studio 的 "工具"-"> 选项-> 调试" 中禁用 (*取消选中*) "启用仅我的代码", 以便在代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="10484-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="10484-151">Unity 设置</span><span class="sxs-lookup"><span data-stu-id="10484-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="10484-152">说明</span><span class="sxs-lookup"><span data-stu-id="10484-152">Instructions</span></span>

1. <span data-ttu-id="10484-153">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="10484-153">Start Unity.</span></span>
2. <span data-ttu-id="10484-154">选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="10484-154">Select **Open**.</span></span>
3. <span data-ttu-id="10484-155">导航到之前未存档的**HolographicAcademy-212**文件夹。</span><span class="sxs-lookup"><span data-stu-id="10484-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="10484-156">查找并选择 "**启动**/**模型资源管理器**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="10484-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="10484-157">单击 "**选择文件夹**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="10484-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="10484-158">在 "**项目**" 面板中, 展开 "**场景**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="10484-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="10484-159">双击 " **ModelExplorer**场景" 将其加载到 Unity。</span><span class="sxs-lookup"><span data-stu-id="10484-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="10484-160">生成</span><span class="sxs-lookup"><span data-stu-id="10484-160">Building</span></span>

1. <span data-ttu-id="10484-161">在 Unity 中, 选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="10484-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="10484-162">如果场景 **/ModelExplorer**未列在 "**生成**" 中, 请单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="10484-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="10484-163">如果要专门针对 HoloLens 进行开发, 请将 "**目标设备**" 设置为 " **hololens**"。</span><span class="sxs-lookup"><span data-stu-id="10484-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="10484-164">否则, 请将其留在**任何设备**上。</span><span class="sxs-lookup"><span data-stu-id="10484-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="10484-165">确保将 "**生成类型**" 设置为 " **D3D** ", 并将 " **SDK** " 设置为 "**最新安装**的" (应为 SDK 16299 或更高版本)</span><span class="sxs-lookup"><span data-stu-id="10484-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="10484-166">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="10484-166">Click **Build**.</span></span>
6. <span data-ttu-id="10484-167">创建名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="10484-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="10484-168">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="10484-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="10484-169">按**选择文件夹**, Unity 将开始为 Visual Studio 生成项目。</span><span class="sxs-lookup"><span data-stu-id="10484-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="10484-170">当 Unity 完成后, 将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="10484-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="10484-171">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="10484-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="10484-172">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="10484-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="10484-173">如果部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="10484-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="10484-174">使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x86**"。</span><span class="sxs-lookup"><span data-stu-id="10484-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="10484-175">单击 "本地计算机" 按钮旁的下拉箭头, 然后选择 "**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="10484-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="10484-176">输入**HoloLens 设备 IP 地址**, 并将身份验证模式设置为**通用 (未加密的协议)** 。</span><span class="sxs-lookup"><span data-stu-id="10484-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="10484-177">单击 "**选择**"。</span><span class="sxs-lookup"><span data-stu-id="10484-177">Click **Select**.</span></span> <span data-ttu-id="10484-178">如果你不知道设备 IP 地址, 请在 "设置" 中查找 " **> 网络 & Internet > 高级选项**"。</span><span class="sxs-lookup"><span data-stu-id="10484-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="10484-179">在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="10484-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="10484-180">如果这是首次部署到设备, 则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="10484-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="10484-181">当应用程序已部署后, 使用**选择手势**关闭**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="10484-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="10484-182">如果要部署到沉浸式耳机:</span><span class="sxs-lookup"><span data-stu-id="10484-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="10484-183">使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **x64**"。</span><span class="sxs-lookup"><span data-stu-id="10484-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="10484-184">确保将部署目标设置为 "**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="10484-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="10484-185">在顶部菜单栏中, 单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="10484-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="10484-186">当应用程序已部署后, 通过将触发器拖到运动控制器上来关闭**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="10484-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="10484-187">你可能会注意到 Visual Studio 错误面板中出现一些红色错误。</span><span class="sxs-lookup"><span data-stu-id="10484-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="10484-188">可以放心地忽略它们。</span><span class="sxs-lookup"><span data-stu-id="10484-188">It is safe to ignore them.</span></span> <span data-ttu-id="10484-189">切换到 "输出" 面板以查看实际的生成进度。</span><span class="sxs-lookup"><span data-stu-id="10484-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="10484-190">"输出" 面板中的错误将要求您进行修复 (通常是由于脚本中的错误而导致的)。</span><span class="sxs-lookup"><span data-stu-id="10484-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="10484-191">第1章-感知</span><span class="sxs-lookup"><span data-stu-id="10484-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="10484-192">目标</span><span class="sxs-lookup"><span data-stu-id="10484-192">Objectives</span></span>

* <span data-ttu-id="10484-193">了解语音命令设计的**Dos 和不注意事项**。</span><span class="sxs-lookup"><span data-stu-id="10484-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="10484-194">使用**KeywordRecognizer**添加基于注视的语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="10484-195">使用光标**反馈**使用户了解语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="10484-196">语音命令设计</span><span class="sxs-lookup"><span data-stu-id="10484-196">Voice Command Design</span></span>

<span data-ttu-id="10484-197">本章介绍如何设计语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="10484-198">创建语音命令时:</span><span class="sxs-lookup"><span data-stu-id="10484-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="10484-199">DO</span><span class="sxs-lookup"><span data-stu-id="10484-199">DO</span></span>

* <span data-ttu-id="10484-200">创建简洁的命令。</span><span class="sxs-lookup"><span data-stu-id="10484-200">Create concise commands.</span></span> <span data-ttu-id="10484-201">您不想使用 *"播放当前选定的视频"* , 因为该命令不是很简洁, 用户将很容易忘记。</span><span class="sxs-lookup"><span data-stu-id="10484-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="10484-202">相反, 应使用: *"播放视频"* , 因为它很简洁并且具有多个音节。</span><span class="sxs-lookup"><span data-stu-id="10484-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="10484-203">使用简单词汇。</span><span class="sxs-lookup"><span data-stu-id="10484-203">Use a simple vocabulary.</span></span> <span data-ttu-id="10484-204">始终尝试使用便于用户发现和记忆的常见字词和短语。</span><span class="sxs-lookup"><span data-stu-id="10484-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="10484-205">例如, 如果您的应用程序具有可在视图中显示或隐藏的便笺对象, 则不会使用命令 *"Show Placard"* , 因为 "Placard" 是很少使用的术语。</span><span class="sxs-lookup"><span data-stu-id="10484-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="10484-206">相反, 您将使用命令: *"显示注释"* , 用于在应用程序中显示注释。</span><span class="sxs-lookup"><span data-stu-id="10484-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="10484-207">保持一致。</span><span class="sxs-lookup"><span data-stu-id="10484-207">Be consistent.</span></span> <span data-ttu-id="10484-208">语音命令应在应用程序中保持一致。</span><span class="sxs-lookup"><span data-stu-id="10484-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="10484-209">假设应用程序中有两个场景, 并且两个场景都包含一个用于关闭应用程序的按钮。</span><span class="sxs-lookup"><span data-stu-id="10484-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="10484-210">如果第一场景使用命令 *"Exit"* 来触发按钮, 但第二个场景使用命令 *"关闭应用"* , 则用户会感到困惑。</span><span class="sxs-lookup"><span data-stu-id="10484-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="10484-211">如果相同的功能在多个场景中保持不变, 则应使用相同的语音命令来触发它。</span><span class="sxs-lookup"><span data-stu-id="10484-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="10484-212">不要</span><span class="sxs-lookup"><span data-stu-id="10484-212">DON'T</span></span>

* <span data-ttu-id="10484-213">使用单个音节命令。</span><span class="sxs-lookup"><span data-stu-id="10484-213">Use single syllable commands.</span></span> <span data-ttu-id="10484-214">例如, 如果你创建了一个声音命令来播放视频, 则应避免使用简单的命令 *"播放"* , 因为它只是一个音节, 系统可以轻松地将其丢失。</span><span class="sxs-lookup"><span data-stu-id="10484-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="10484-215">相反, 应使用: *"播放视频"* , 因为它很简洁并且具有多个音节。</span><span class="sxs-lookup"><span data-stu-id="10484-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="10484-216">使用系统命令。</span><span class="sxs-lookup"><span data-stu-id="10484-216">Use system commands.</span></span> <span data-ttu-id="10484-217">系统保留了 *"Select"* 命令, 以触发当前聚焦对象的点击事件。</span><span class="sxs-lookup"><span data-stu-id="10484-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="10484-218">不要在关键字或短语中重复使用 *"Select"* 命令, 因为它可能不会像预期那样工作。</span><span class="sxs-lookup"><span data-stu-id="10484-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="10484-219">例如, 如果在应用程序中选择某个多维数据集的语音命令是 *"Select cube"* , 但用户在失措命令时却查看了该球, 则会改为选择球体。</span><span class="sxs-lookup"><span data-stu-id="10484-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="10484-220">类似的应用程序栏命令启用了语音。</span><span class="sxs-lookup"><span data-stu-id="10484-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="10484-221">请勿在 CoreWindow 视图中使用以下语音命令:</span><span class="sxs-lookup"><span data-stu-id="10484-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="10484-222">回去</span><span class="sxs-lookup"><span data-stu-id="10484-222">Go Back</span></span>
    2. <span data-ttu-id="10484-223">滚动工具</span><span class="sxs-lookup"><span data-stu-id="10484-223">Scroll Tool</span></span>
    3. <span data-ttu-id="10484-224">“缩放工具”</span><span class="sxs-lookup"><span data-stu-id="10484-224">Zoom Tool</span></span>
    4. <span data-ttu-id="10484-225">拖动工具</span><span class="sxs-lookup"><span data-stu-id="10484-225">Drag Tool</span></span>
    5. <span data-ttu-id="10484-226">Adjust</span><span class="sxs-lookup"><span data-stu-id="10484-226">Adjust</span></span>
    6. <span data-ttu-id="10484-227">Remove</span><span class="sxs-lookup"><span data-stu-id="10484-227">Remove</span></span>
* <span data-ttu-id="10484-228">使用类似的声音。</span><span class="sxs-lookup"><span data-stu-id="10484-228">Use similar sounds.</span></span> <span data-ttu-id="10484-229">尝试避免使用偏偏的语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="10484-230">如果有支持 *"显示商店"* 和 *"显示更多"* 语音命令的购物应用程序, 则需要禁用其中一个命令, 而另一个命令已被使用。</span><span class="sxs-lookup"><span data-stu-id="10484-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="10484-231">例如, 你可以使用 *"显示商店"* 按钮打开应用商店, 然后在显示应用商店时禁用该命令, 以便可以使用 *"显示更多"* 命令来浏览。</span><span class="sxs-lookup"><span data-stu-id="10484-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="10484-232">说明</span><span class="sxs-lookup"><span data-stu-id="10484-232">Instructions</span></span>

* <span data-ttu-id="10484-233">在 Unity 的**层次结构**面板中, 使用搜索工具查找**holoComm_screen_mesh**对象。</span><span class="sxs-lookup"><span data-stu-id="10484-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="10484-234">双击 " **holoComm_screen_mesh** " 对象以在**场景**中查看它。</span><span class="sxs-lookup"><span data-stu-id="10484-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="10484-235">这是 astronaut 的手表, 它将响应我们的语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="10484-236">在 "**检查器**" 面板中, 找到 "**语音输入源 (脚本)** " 组件。</span><span class="sxs-lookup"><span data-stu-id="10484-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="10484-237">展开**关键字**部分, 查看支持的语音命令:**打开 Communicator**。</span><span class="sxs-lookup"><span data-stu-id="10484-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="10484-238">单击右侧的 "齿轮", 然后选择 "**编辑脚本**"。</span><span class="sxs-lookup"><span data-stu-id="10484-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="10484-239">探索**SpeechInputSource.cs** , 了解它如何使用**KeywordRecognizer**添加语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="10484-240">生成和部署</span><span class="sxs-lookup"><span data-stu-id="10484-240">Build and Deploy</span></span>

* <span data-ttu-id="10484-241">在 Unity 中, 使用**File > 生成设置**重新生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="10484-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="10484-242">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="10484-242">Open the **App** folder.</span></span>
* <span data-ttu-id="10484-243">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="10484-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="10484-244">(如果在安装过程中已经在 Visual Studio 中生成或部署了此项目, 则可以打开 VS 的实例, 并在出现提示时单击 "全部重新加载")。</span><span class="sxs-lookup"><span data-stu-id="10484-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="10484-245">在 Visual Studio 中, 单击 "**调试"-> "无调试开始**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="10484-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="10484-246">在应用程序部署到 HoloLens 后, 请使用[轻攻敲击](gestures.md#air-tap)手势关闭 "拟合" 框。</span><span class="sxs-lookup"><span data-stu-id="10484-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="10484-247">观看 astronaut 的观看。</span><span class="sxs-lookup"><span data-stu-id="10484-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="10484-248">当监视有焦点时, 验证光标是否更改为麦克风。</span><span class="sxs-lookup"><span data-stu-id="10484-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="10484-249">这会提供应用程序侦听语音命令的反馈。</span><span class="sxs-lookup"><span data-stu-id="10484-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="10484-250">验证是否在手表上显示工具提示。</span><span class="sxs-lookup"><span data-stu-id="10484-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="10484-251">这可以帮助用户发现 *"打开 Communicator"* 命令。</span><span class="sxs-lookup"><span data-stu-id="10484-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="10484-252">当 gazing 时, 说 *"打开 communicator"* 即可打开 communicator 面板。</span><span class="sxs-lookup"><span data-stu-id="10484-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="10484-253">第2章-确认</span><span class="sxs-lookup"><span data-stu-id="10484-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="10484-254">目标</span><span class="sxs-lookup"><span data-stu-id="10484-254">Objectives</span></span>

* <span data-ttu-id="10484-255">使用麦克风输入记录一条消息。</span><span class="sxs-lookup"><span data-stu-id="10484-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="10484-256">向用户提供对应用程序侦听其语音的反馈。</span><span class="sxs-lookup"><span data-stu-id="10484-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="10484-257">必须为应用声明**麦克风**功能, 才能从麦克风记录。</span><span class="sxs-lookup"><span data-stu-id="10484-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="10484-258">此操作已在 MR Input 212 中完成, 但请记住你自己的项目。</span><span class="sxs-lookup"><span data-stu-id="10484-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="10484-259">在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player", 转到 "播放机" 设置</span><span class="sxs-lookup"><span data-stu-id="10484-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="10484-260">单击 "通用 Windows 平台" 选项卡</span><span class="sxs-lookup"><span data-stu-id="10484-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="10484-261">在 "发布设置 > 功能" 部分中, 检查**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="10484-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="10484-262">说明</span><span class="sxs-lookup"><span data-stu-id="10484-262">Instructions</span></span>

* <span data-ttu-id="10484-263">在 Unity 的 "**层次结构**" 面板中, 验证是否选择了 " **holoComm_screen_mesh** " 对象。</span><span class="sxs-lookup"><span data-stu-id="10484-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="10484-264">在**检查器**面板中, 找到 " **Astronaut Watch (脚本)** " 组件。</span><span class="sxs-lookup"><span data-stu-id="10484-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="10484-265">单击设置为 " **Communicator Prefab** " 属性值的小型蓝色多维数据集。</span><span class="sxs-lookup"><span data-stu-id="10484-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="10484-266">在 "**项目**" 面板中, **Communicator** prefab 现在应具有焦点。</span><span class="sxs-lookup"><span data-stu-id="10484-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="10484-267">单击 "**项目**" 面板中的**Communicator** Prefab, 在**检查器**中查看其组件。</span><span class="sxs-lookup"><span data-stu-id="10484-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="10484-268">查看**麦克风管理器 (脚本)** 组件, 这将允许我们记录用户的语音。</span><span class="sxs-lookup"><span data-stu-id="10484-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="10484-269">请注意, **Communicator**对象具有用于响应 "**发送消息**" 命令的**语音输入处理程序 (脚本)** 组件。</span><span class="sxs-lookup"><span data-stu-id="10484-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="10484-270">查看**Communicator (脚本)** 组件, 然后双击脚本, 在 Visual Studio 中将其打开。</span><span class="sxs-lookup"><span data-stu-id="10484-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="10484-271">Communicator.cs 负责在 communicator 设备上设置正确的按钮状态。</span><span class="sxs-lookup"><span data-stu-id="10484-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="10484-272">这将允许我们的用户记录消息, 播放消息, 并将消息发送到 astronaut。</span><span class="sxs-lookup"><span data-stu-id="10484-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="10484-273">它还将启动和停止动画波形窗体, 以便向用户确认他们的声音被听到。</span><span class="sxs-lookup"><span data-stu-id="10484-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="10484-274">在**Communicator.cs**中, 从**Start**方法中删除以下行 (81 和 82)。</span><span class="sxs-lookup"><span data-stu-id="10484-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="10484-275">这将启用 communicator 上的 "录制" 按钮。</span><span class="sxs-lookup"><span data-stu-id="10484-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="10484-276">生成和部署</span><span class="sxs-lookup"><span data-stu-id="10484-276">Build and Deploy</span></span>

* <span data-ttu-id="10484-277">在 Visual Studio 中, 重新生成应用程序并将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="10484-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="10484-278">看看 astronaut 的手表, 说 *"打开 communicator"* 显示 Communicator。</span><span class="sxs-lookup"><span data-stu-id="10484-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="10484-279">按 "**录制**" 按钮 (麦克风) 开始录制 astronaut 的口头消息。</span><span class="sxs-lookup"><span data-stu-id="10484-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="10484-280">开始讲话, 并验证波形动画是否在 communicator 上播放, 这向用户提供了他们的语音声音。</span><span class="sxs-lookup"><span data-stu-id="10484-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="10484-281">按 "**停止**" 按钮 (左方形), 并验证波形动画是否停止运行。</span><span class="sxs-lookup"><span data-stu-id="10484-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="10484-282">按下 "**播放**" 按钮 (右三角形) 播放录制的邮件, 并在设备上听到它。</span><span class="sxs-lookup"><span data-stu-id="10484-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="10484-283">按下 "**停止**" 按钮 (右方形) 以停止播放录制的消息。</span><span class="sxs-lookup"><span data-stu-id="10484-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="10484-284">说 *"发送消息"* 关闭 communicator, 并接收来自 astronaut 的 "消息收到" 响应。</span><span class="sxs-lookup"><span data-stu-id="10484-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="10484-285">第3章-了解和听写识别器</span><span class="sxs-lookup"><span data-stu-id="10484-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="10484-286">目标</span><span class="sxs-lookup"><span data-stu-id="10484-286">Objectives</span></span>

* <span data-ttu-id="10484-287">使用听写识别器将用户的语音转换为文本。</span><span class="sxs-lookup"><span data-stu-id="10484-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="10484-288">显示 communicator 中听写识别器的假设和最终结果。</span><span class="sxs-lookup"><span data-stu-id="10484-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="10484-289">在本章中, 我们将使用听写识别器来创建 astronaut 的消息。</span><span class="sxs-lookup"><span data-stu-id="10484-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="10484-290">使用听写识别器时, 请记住:</span><span class="sxs-lookup"><span data-stu-id="10484-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="10484-291">你必须连接到 WiFi 才能让听写识别器正常工作。</span><span class="sxs-lookup"><span data-stu-id="10484-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="10484-292">超时发生在设定的时间段之后。</span><span class="sxs-lookup"><span data-stu-id="10484-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="10484-293">需要注意两个超时:</span><span class="sxs-lookup"><span data-stu-id="10484-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="10484-294">如果识别器在前五秒内开始播放并且不听到任何音频, 则会超时。</span><span class="sxs-lookup"><span data-stu-id="10484-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="10484-295">如果识别器给定了结果, 但随后听到了20秒, 则会超时。</span><span class="sxs-lookup"><span data-stu-id="10484-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="10484-296">一次只能运行一种类型的识别器 (关键字或听写)。</span><span class="sxs-lookup"><span data-stu-id="10484-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="10484-297">必须为应用声明**麦克风**功能, 才能从麦克风记录。</span><span class="sxs-lookup"><span data-stu-id="10484-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="10484-298">此操作已在 MR Input 212 中完成, 但请记住你自己的项目。</span><span class="sxs-lookup"><span data-stu-id="10484-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="10484-299">在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player", 转到 "播放机" 设置</span><span class="sxs-lookup"><span data-stu-id="10484-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="10484-300">单击 "通用 Windows 平台" 选项卡</span><span class="sxs-lookup"><span data-stu-id="10484-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="10484-301">在 "发布设置 > 功能" 部分中, 检查**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="10484-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="10484-302">说明</span><span class="sxs-lookup"><span data-stu-id="10484-302">Instructions</span></span>

<span data-ttu-id="10484-303">我们将编辑**MicrophoneManager.cs**以使用听写识别器。</span><span class="sxs-lookup"><span data-stu-id="10484-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="10484-304">这就是我们要添加的内容:</span><span class="sxs-lookup"><span data-stu-id="10484-304">This is what we'll add:</span></span>

1. <span data-ttu-id="10484-305">按下 "**记录" 按钮**后, 将**启动 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="10484-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="10484-306">显示 DictationRecognizer 理解的**假设**。</span><span class="sxs-lookup"><span data-stu-id="10484-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="10484-307">锁定 DictationRecognizer 理解的**结果**。</span><span class="sxs-lookup"><span data-stu-id="10484-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="10484-308">检查 DictationRecognizer 中的超时。</span><span class="sxs-lookup"><span data-stu-id="10484-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="10484-309">按下 "**停止" 按钮**, 或 mic 会话超时时,**停止 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="10484-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="10484-310">重新启动**KeywordRecognizer**, 这将侦听 "**发送消息**" 命令。</span><span class="sxs-lookup"><span data-stu-id="10484-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="10484-311">让我们开始吧。</span><span class="sxs-lookup"><span data-stu-id="10484-311">Let's get started.</span></span> <span data-ttu-id="10484-312">在**MicrophoneManager.cs**中完成 3. a 的所有编码练习, 或复制并粘贴下面的已完成代码:</span><span class="sxs-lookup"><span data-stu-id="10484-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="10484-313">生成和部署</span><span class="sxs-lookup"><span data-stu-id="10484-313">Build and Deploy</span></span>

* <span data-ttu-id="10484-314">在 Visual Studio 中重新生成并部署到设备。</span><span class="sxs-lookup"><span data-stu-id="10484-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="10484-315">使用 "气攻入点" 消除 "拟合" 框。</span><span class="sxs-lookup"><span data-stu-id="10484-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="10484-316">看看 astronaut 的手表, 说 *"打开 Communicator"* 。</span><span class="sxs-lookup"><span data-stu-id="10484-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="10484-317">选择 "**录制**" 按钮 (麦克风) 以记录您的消息。</span><span class="sxs-lookup"><span data-stu-id="10484-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="10484-318">开始说话。</span><span class="sxs-lookup"><span data-stu-id="10484-318">Start speaking.</span></span> <span data-ttu-id="10484-319">**听写识别器**将解释您的语音, 并显示 communicator 中的假设文本。</span><span class="sxs-lookup"><span data-stu-id="10484-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="10484-320">录制消息时, 尝试口述 *"发送消息"* 。</span><span class="sxs-lookup"><span data-stu-id="10484-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="10484-321">请注意, 由于**听写识别器**仍处于活动状态,**关键字识别器**没有响应。</span><span class="sxs-lookup"><span data-stu-id="10484-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="10484-322">停止说几秒钟。</span><span class="sxs-lookup"><span data-stu-id="10484-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="10484-323">注意听写识别器完成其假设并显示最终结果。</span><span class="sxs-lookup"><span data-stu-id="10484-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="10484-324">开始讲话, 并暂停20秒。</span><span class="sxs-lookup"><span data-stu-id="10484-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="10484-325">这将导致**听写识别器**超时。</span><span class="sxs-lookup"><span data-stu-id="10484-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="10484-326">请注意, 在上述超时后, 将重新启用**关键字识别器**。</span><span class="sxs-lookup"><span data-stu-id="10484-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="10484-327">Communicator 现在会响应语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="10484-328">说 *"发送消息"* , 将消息发送到 astronaut。</span><span class="sxs-lookup"><span data-stu-id="10484-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="10484-329">第4章-语法识别器</span><span class="sxs-lookup"><span data-stu-id="10484-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="10484-330">目标</span><span class="sxs-lookup"><span data-stu-id="10484-330">Objectives</span></span>

* <span data-ttu-id="10484-331">使用语法识别器根据 SRGS 或语音识别语法规范 (文件) 识别用户的语音。</span><span class="sxs-lookup"><span data-stu-id="10484-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="10484-332">必须为应用声明**麦克风**功能, 才能从麦克风记录。</span><span class="sxs-lookup"><span data-stu-id="10484-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="10484-333">此操作已在 MR Input 212 中完成, 但请记住你自己的项目。</span><span class="sxs-lookup"><span data-stu-id="10484-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="10484-334">在 Unity 编辑器中, 导航到 "编辑 > 项目设置 > Player", 转到 "播放机" 设置</span><span class="sxs-lookup"><span data-stu-id="10484-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="10484-335">单击 "通用 Windows 平台" 选项卡</span><span class="sxs-lookup"><span data-stu-id="10484-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="10484-336">在 "发布设置 > 功能" 部分中, 检查**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="10484-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="10484-337">说明</span><span class="sxs-lookup"><span data-stu-id="10484-337">Instructions</span></span>

1. <span data-ttu-id="10484-338">在 "**层次结构**" 面板中, 搜索**Jetpack_Center**并选择它。</span><span class="sxs-lookup"><span data-stu-id="10484-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="10484-339">在 "**检查器**" 面板中查找**Tagalong 操作**脚本。</span><span class="sxs-lookup"><span data-stu-id="10484-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="10484-340">单击要**沿字段标记的对象**右侧的小圆圈。</span><span class="sxs-lookup"><span data-stu-id="10484-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="10484-341">在弹出的窗口中, 搜索**SRGSToolbox**并从列表中选择它。</span><span class="sxs-lookup"><span data-stu-id="10484-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="10484-342">查看**StreamingAssets**文件夹中的**SRGSColor**文件。</span><span class="sxs-lookup"><span data-stu-id="10484-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="10484-343">可以在[此处](https://www.w3.org/TR/speech-grammar/)的 W3C 网站上找到 SRGS 设计规范。</span><span class="sxs-lookup"><span data-stu-id="10484-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="10484-344">在 SRGS 文件中, 有三种类型的规则:</span><span class="sxs-lookup"><span data-stu-id="10484-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="10484-345">一种规则, 它允许您从十二种颜色列表中显示一种颜色。</span><span class="sxs-lookup"><span data-stu-id="10484-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="10484-346">三个规则用于侦听颜色规则和三个形状中的一个组合。</span><span class="sxs-lookup"><span data-stu-id="10484-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="10484-347">根规则 colorChooser, 用于侦听三个 "颜色 + 形状" 规则的任意组合。</span><span class="sxs-lookup"><span data-stu-id="10484-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="10484-348">可以按任何顺序以及从一个到所有三个形状的任意量来表示形状。</span><span class="sxs-lookup"><span data-stu-id="10484-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="10484-349">这是唯一侦听的规则, 因为它在初始&lt;语法&gt;标记中指定为文件顶部的根规则。</span><span class="sxs-lookup"><span data-stu-id="10484-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="10484-350">生成和部署</span><span class="sxs-lookup"><span data-stu-id="10484-350">Build and Deploy</span></span>

* <span data-ttu-id="10484-351">重新生成 Unity 中的应用程序, 然后从 Visual Studio 生成并部署, 以在 HoloLens 上体验应用。</span><span class="sxs-lookup"><span data-stu-id="10484-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="10484-352">使用 "气攻入点" 消除 "拟合" 框。</span><span class="sxs-lookup"><span data-stu-id="10484-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="10484-353">看看 astronaut 的 jetpack, 然后执行 "空气分流" 手势。</span><span class="sxs-lookup"><span data-stu-id="10484-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="10484-354">开始说话。</span><span class="sxs-lookup"><span data-stu-id="10484-354">Start speaking.</span></span> <span data-ttu-id="10484-355">**语法识别器**将根据识别来解释您的语音并更改形状的颜色。</span><span class="sxs-lookup"><span data-stu-id="10484-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="10484-356">例如, 命令为 "蓝圆圈, 黄色正方形"。</span><span class="sxs-lookup"><span data-stu-id="10484-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="10484-357">执行另一个轻攻敲击手势来关闭工具箱。</span><span class="sxs-lookup"><span data-stu-id="10484-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="10484-358">结束</span><span class="sxs-lookup"><span data-stu-id="10484-358">The End</span></span>

<span data-ttu-id="10484-359">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="10484-359">Congratulations!</span></span> <span data-ttu-id="10484-360">你现在已经完成**了 MR 输入 212:语音**。</span><span class="sxs-lookup"><span data-stu-id="10484-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="10484-361">您知道语音命令的 Dos 和不确定。</span><span class="sxs-lookup"><span data-stu-id="10484-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="10484-362">你了解了如何利用工具提示来使用户了解语音命令。</span><span class="sxs-lookup"><span data-stu-id="10484-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="10484-363">你看到了几种类型的反馈, 用来确认用户的语音被听到。</span><span class="sxs-lookup"><span data-stu-id="10484-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="10484-364">您知道如何在关键字识别器和听写识别器之间切换, 这两种功能如何理解和解释您的声音。</span><span class="sxs-lookup"><span data-stu-id="10484-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="10484-365">已了解如何在应用程序中使用 SRGS 文件和用于语音识别的语法识别器。</span><span class="sxs-lookup"><span data-stu-id="10484-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
