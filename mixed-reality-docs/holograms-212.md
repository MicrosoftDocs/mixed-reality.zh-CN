---
title: MR 输入 212-语音
description: 按照本演练使用 Unity、 Visual Studio 和 HoloLens 学习语音概念的详细信息进行编码操作。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 学院、 教程中，语音
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590379"
---
>[!NOTE]
><span data-ttu-id="693ee-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="693ee-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="693ee-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="693ee-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="693ee-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="693ee-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="693ee-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="693ee-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="693ee-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="693ee-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="693ee-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="693ee-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="693ee-110">MR 输入 212:语音</span><span class="sxs-lookup"><span data-stu-id="693ee-110">MR Input 212: Voice</span></span>

<span data-ttu-id="693ee-111">[语音输入](voice-input.md)为我们提供了另一种方法与我们全息进行交互。</span><span class="sxs-lookup"><span data-stu-id="693ee-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="693ee-112">语音命令的工作非常自然和简单的方式。</span><span class="sxs-lookup"><span data-stu-id="693ee-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="693ee-113">设计你的语音命令，以便它们：</span><span class="sxs-lookup"><span data-stu-id="693ee-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="693ee-114">自然</span><span class="sxs-lookup"><span data-stu-id="693ee-114">Natural</span></span>
* <span data-ttu-id="693ee-115">容易记住</span><span class="sxs-lookup"><span data-stu-id="693ee-115">Easy to remember</span></span>
* <span data-ttu-id="693ee-116">适当的上下文</span><span class="sxs-lookup"><span data-stu-id="693ee-116">Context appropriate</span></span>
* <span data-ttu-id="693ee-117">充分不同于在同一上下文中的其他选项</span><span class="sxs-lookup"><span data-stu-id="693ee-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="693ee-118">在中[MR 基础知识 101](holograms-101.md)，我们使用 KeywordRecognizer 来生成两个简单的语音命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="693ee-119">在 MR 输入 212，我们将深入研究，了解如何：</span><span class="sxs-lookup"><span data-stu-id="693ee-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="693ee-120">设计针对 HoloLens 语音引擎进行了优化的语音命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="693ee-121">使用户知道哪些语音的命令都可用。</span><span class="sxs-lookup"><span data-stu-id="693ee-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="693ee-122">确认我们已收到用户的语音命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="693ee-123">了解什么是用户说： 使用听写识别器。</span><span class="sxs-lookup"><span data-stu-id="693ee-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="693ee-124">使用语法识别器来侦听基于 SRGS 或语音识别语法规范，文件的命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="693ee-125">在本课程中，我们将再度讨论模型资源管理器，它在我们构建[MR 输入 210](holograms-210.md)并[MR 输入 211](holograms-211.md)。</span><span class="sxs-lookup"><span data-stu-id="693ee-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="693ee-126">使用 Unity 和混合现实工具包的较旧版本记录中的以下章节每个嵌入的视频。</span><span class="sxs-lookup"><span data-stu-id="693ee-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="693ee-127">准确且最新的分步说明时，可能会看到脚本和已过期的相应视频中的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="693ee-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="693ee-128">保持为长期的视频和因为涵盖了概念仍然适用。</span><span class="sxs-lookup"><span data-stu-id="693ee-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="693ee-129">设备支持</span><span class="sxs-lookup"><span data-stu-id="693ee-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="693ee-130">课程</span><span class="sxs-lookup"><span data-stu-id="693ee-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="693ee-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="693ee-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="693ee-132"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="693ee-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="693ee-133">MR 输入 212:语音</span><span class="sxs-lookup"><span data-stu-id="693ee-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="693ee-134">✔️</span><span class="sxs-lookup"><span data-stu-id="693ee-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="693ee-135">✔️</span><span class="sxs-lookup"><span data-stu-id="693ee-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="693ee-136">开始之前</span><span class="sxs-lookup"><span data-stu-id="693ee-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="693ee-137">先决条件</span><span class="sxs-lookup"><span data-stu-id="693ee-137">Prerequisites</span></span>

* <span data-ttu-id="693ee-138">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="693ee-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="693ee-139">一些基本C#编程功能。</span><span class="sxs-lookup"><span data-stu-id="693ee-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="693ee-140">您应当已完成[MR 基础知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="693ee-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="693ee-141">您应当已完成[MR 输入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="693ee-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="693ee-142">您应当已完成[MR 输入 211](holograms-211.md)。</span><span class="sxs-lookup"><span data-stu-id="693ee-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="693ee-143">HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="693ee-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="693ee-144">项目文件</span><span class="sxs-lookup"><span data-stu-id="693ee-144">Project files</span></span>

* <span data-ttu-id="693ee-145">下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip)所需的项目。</span><span class="sxs-lookup"><span data-stu-id="693ee-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="693ee-146">需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="693ee-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="693ee-147">取消存档到您的桌面或其他轻松地访问位置的文件。</span><span class="sxs-lookup"><span data-stu-id="693ee-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="693ee-148">如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)。</span><span class="sxs-lookup"><span data-stu-id="693ee-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="693ee-149">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="693ee-149">Errata and Notes</span></span>

* <span data-ttu-id="693ee-150">"启用仅我的代码"必须禁用 (*未选中*) 在 Visual Studio 工具-> 选项-> 调试以便你的代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="693ee-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="693ee-151">Unity 安装程序</span><span class="sxs-lookup"><span data-stu-id="693ee-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="693ee-152">说明</span><span class="sxs-lookup"><span data-stu-id="693ee-152">Instructions</span></span>

1. <span data-ttu-id="693ee-153">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="693ee-153">Start Unity.</span></span>
2. <span data-ttu-id="693ee-154">选择**打开**。</span><span class="sxs-lookup"><span data-stu-id="693ee-154">Select **Open**.</span></span>
3. <span data-ttu-id="693ee-155">导航到**HolographicAcademy 全息 212 语音**文件夹你之前未存档。</span><span class="sxs-lookup"><span data-stu-id="693ee-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="693ee-156">找到并选择**起始**/**模型资源管理器**文件夹。</span><span class="sxs-lookup"><span data-stu-id="693ee-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="693ee-157">单击**选择文件夹**按钮。</span><span class="sxs-lookup"><span data-stu-id="693ee-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="693ee-158">在中**项目**面板中，展开**场景**文件夹。</span><span class="sxs-lookup"><span data-stu-id="693ee-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="693ee-159">双击**ModelExplorer**场景中，从而在 Unity 中加载它。</span><span class="sxs-lookup"><span data-stu-id="693ee-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="693ee-160">生成</span><span class="sxs-lookup"><span data-stu-id="693ee-160">Building</span></span>

1. <span data-ttu-id="693ee-161">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="693ee-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="693ee-162">如果**场景/ModelExplorer**中未列出**生成中的场景**，单击**添加打开场景**添加场景。</span><span class="sxs-lookup"><span data-stu-id="693ee-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="693ee-163">如果您专门为 HoloLens 开发，设置**目标设备**到**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="693ee-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="693ee-164">否则，将其保持打开**任何设备**。</span><span class="sxs-lookup"><span data-stu-id="693ee-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="693ee-165">请确保**生成类型**设置为**D3D**并**SDK**设置为**最新安装**（应为 16299 或更高版本的 SDK）。</span><span class="sxs-lookup"><span data-stu-id="693ee-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="693ee-166">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="693ee-166">Click **Build**.</span></span>
6. <span data-ttu-id="693ee-167">创建**新文件夹**名为"应用"。</span><span class="sxs-lookup"><span data-stu-id="693ee-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="693ee-168">单击一下**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="693ee-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="693ee-169">按**选择文件夹**和 Unity 将启动 Visual Studio 的生成项目。</span><span class="sxs-lookup"><span data-stu-id="693ee-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="693ee-170">Unity 完成操作后，将出现一个文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="693ee-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="693ee-171">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="693ee-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="693ee-172">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="693ee-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="693ee-173">如果部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="693ee-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="693ee-174">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x86**。</span><span class="sxs-lookup"><span data-stu-id="693ee-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="693ee-175">单击向下箭头旁边的本地计算机按钮，然后选择**远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="693ee-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="693ee-176">输入**HoloLens 设备 IP 地址**并将身份验证模式设置为**通用 （未加密的协议）**。</span><span class="sxs-lookup"><span data-stu-id="693ee-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="693ee-177">单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="693ee-177">Click **Select**.</span></span> <span data-ttu-id="693ee-178">如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**。</span><span class="sxs-lookup"><span data-stu-id="693ee-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="693ee-179">在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="693ee-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="693ee-180">如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="693ee-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="693ee-181">当部署应用时，消除**Fitbox**与**选择手势**。</span><span class="sxs-lookup"><span data-stu-id="693ee-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="693ee-182">如果部署到沉浸式头戴式：</span><span class="sxs-lookup"><span data-stu-id="693ee-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="693ee-183">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x64**。</span><span class="sxs-lookup"><span data-stu-id="693ee-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="693ee-184">请确保部署目标设置为**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="693ee-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="693ee-185">在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="693ee-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="693ee-186">当部署应用时，消除**Fitbox**拉开运动控制器上的触发器。</span><span class="sxs-lookup"><span data-stu-id="693ee-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="693ee-187">您可能注意到 Visual Studio 错误面板中的某些红色错误。</span><span class="sxs-lookup"><span data-stu-id="693ee-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="693ee-188">它可以安全地忽略它们。</span><span class="sxs-lookup"><span data-stu-id="693ee-188">It is safe to ignore them.</span></span> <span data-ttu-id="693ee-189">切换到输出面板来查看实际生成进度。</span><span class="sxs-lookup"><span data-stu-id="693ee-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="693ee-190">输出面板中的错误将要求您的修补程序 （即最常在脚本中的错误，就会出现）。</span><span class="sxs-lookup"><span data-stu-id="693ee-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="693ee-191">第 1 章-感知</span><span class="sxs-lookup"><span data-stu-id="693ee-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="693ee-192">目标</span><span class="sxs-lookup"><span data-stu-id="693ee-192">Objectives</span></span>

* <span data-ttu-id="693ee-193">了解**注意事项**语音命令设计。</span><span class="sxs-lookup"><span data-stu-id="693ee-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="693ee-194">使用**KeywordRecognizer**将基于的视线移动语音命令添加。</span><span class="sxs-lookup"><span data-stu-id="693ee-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="693ee-195">使用户识别语音命令使用游标**反馈**。</span><span class="sxs-lookup"><span data-stu-id="693ee-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="693ee-196">语音命令设计</span><span class="sxs-lookup"><span data-stu-id="693ee-196">Voice Command Design</span></span>

<span data-ttu-id="693ee-197">在本章中，您将学习如何设计语音命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="693ee-198">创建时的语音命令：</span><span class="sxs-lookup"><span data-stu-id="693ee-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="693ee-199">DO</span><span class="sxs-lookup"><span data-stu-id="693ee-199">DO</span></span>

* <span data-ttu-id="693ee-200">创建简洁的命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-200">Create concise commands.</span></span> <span data-ttu-id="693ee-201">您不想要使用 *"播放当前所选的视频"*，因为该命令不是简洁并轻松地将用户被遗忘。</span><span class="sxs-lookup"><span data-stu-id="693ee-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="693ee-202">相反，应使用：*"播放视频"*，因为它很简洁，并具有多个音节。</span><span class="sxs-lookup"><span data-stu-id="693ee-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="693ee-203">使用简单的词汇。</span><span class="sxs-lookup"><span data-stu-id="693ee-203">Use a simple vocabulary.</span></span> <span data-ttu-id="693ee-204">始终尝试使用常用词和短语，都可轻松地发现，请记住用户。</span><span class="sxs-lookup"><span data-stu-id="693ee-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="693ee-205">例如，如果应用程序出现无法显示或隐藏视图中的说明对象，则不会使用该命令 *"显示布告"*，因为"标牌"是一个很少使用的术语。</span><span class="sxs-lookup"><span data-stu-id="693ee-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="693ee-206">相反，您可以使用命令：*"显示说明"*，以显示你的应用程序中的说明。</span><span class="sxs-lookup"><span data-stu-id="693ee-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="693ee-207">保持一致。</span><span class="sxs-lookup"><span data-stu-id="693ee-207">Be consistent.</span></span> <span data-ttu-id="693ee-208">语音命令应保持一致整个应用程序。</span><span class="sxs-lookup"><span data-stu-id="693ee-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="693ee-209">假设应用程序中有两个场景，并且这两个场景包含一个用于关闭应用程序的按钮。</span><span class="sxs-lookup"><span data-stu-id="693ee-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="693ee-210">如果第一个场景使用命令 *"退出"* 触发按钮，但第二个场景使用该命令 *"关闭应用"*，则用户将感到很困惑。</span><span class="sxs-lookup"><span data-stu-id="693ee-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="693ee-211">如果相同的功能在多个场景之间仍然存在，则应使用相同的语音命令来触发它。</span><span class="sxs-lookup"><span data-stu-id="693ee-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="693ee-212">不要</span><span class="sxs-lookup"><span data-stu-id="693ee-212">DON'T</span></span>

* <span data-ttu-id="693ee-213">使用单个音节命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-213">Use single syllable commands.</span></span> <span data-ttu-id="693ee-214">例如，如果你已创建语音命令来播放视频，应避免使用简单命令 *"播放"*，因为它仅单音节，可以轻松地被系统遗漏。</span><span class="sxs-lookup"><span data-stu-id="693ee-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="693ee-215">相反，应使用：*"播放视频"*，因为它很简洁，并具有多个音节。</span><span class="sxs-lookup"><span data-stu-id="693ee-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="693ee-216">使用系统命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-216">Use system commands.</span></span> <span data-ttu-id="693ee-217">*"选择"* 命令保留的系统来触发当前具有焦点的对象的点击事件。</span><span class="sxs-lookup"><span data-stu-id="693ee-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="693ee-218">不要重新使用 *"选择"* 命令中的关键字或短语，，因为它可能不如预期。</span><span class="sxs-lookup"><span data-stu-id="693ee-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="693ee-219">例如，如果语音命令用于在你的应用程序中选择多维数据集已 *"选择多维数据集"*，但是，用户看看球体时它们失措命令，则会改为选择球体。</span><span class="sxs-lookup"><span data-stu-id="693ee-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="693ee-220">同样应用栏命令都已启用语音。</span><span class="sxs-lookup"><span data-stu-id="693ee-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="693ee-221">不在 CoreWindow 视图中使用以下的语音命令：</span><span class="sxs-lookup"><span data-stu-id="693ee-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="693ee-222">回去</span><span class="sxs-lookup"><span data-stu-id="693ee-222">Go Back</span></span>
    2. <span data-ttu-id="693ee-223">滚动工具</span><span class="sxs-lookup"><span data-stu-id="693ee-223">Scroll Tool</span></span>
    3. <span data-ttu-id="693ee-224">“缩放工具”</span><span class="sxs-lookup"><span data-stu-id="693ee-224">Zoom Tool</span></span>
    4. <span data-ttu-id="693ee-225">拖动工具</span><span class="sxs-lookup"><span data-stu-id="693ee-225">Drag Tool</span></span>
    5. <span data-ttu-id="693ee-226">Adjust</span><span class="sxs-lookup"><span data-stu-id="693ee-226">Adjust</span></span>
    6. <span data-ttu-id="693ee-227">Remove</span><span class="sxs-lookup"><span data-stu-id="693ee-227">Remove</span></span>
* <span data-ttu-id="693ee-228">使用类似的声音。</span><span class="sxs-lookup"><span data-stu-id="693ee-228">Use similar sounds.</span></span> <span data-ttu-id="693ee-229">尽量避免使用韵文的语音命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="693ee-230">如果你有一个购物应用程序，支持 *"显示存储区"* 并 *"显示更多"* 作为语音命令，则可以禁用某个命令的其他过程中使用。</span><span class="sxs-lookup"><span data-stu-id="693ee-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="693ee-231">例如，可以使用 *"显示存储"* 按钮以打开存储，然后又禁用了该命令时显示在存储区，以便 *"显示更多"* 命令无法用于浏览。</span><span class="sxs-lookup"><span data-stu-id="693ee-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="693ee-232">说明</span><span class="sxs-lookup"><span data-stu-id="693ee-232">Instructions</span></span>

* <span data-ttu-id="693ee-233">在 Unity 中的**层次结构**面板中，使用的搜索工具查找**holoComm_screen_mesh**对象。</span><span class="sxs-lookup"><span data-stu-id="693ee-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="693ee-234">双击**holoComm_screen_mesh**对象中查看该**场景**。</span><span class="sxs-lookup"><span data-stu-id="693ee-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="693ee-235">这是顶级的监视，将会响应我们语音命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="693ee-236">在中**Inspector**面板中，找到**语音输入源 （脚本）** 组件。</span><span class="sxs-lookup"><span data-stu-id="693ee-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="693ee-237">展开**关键字**部分，以查看受支持的语音命令：**打开 Communicator**。</span><span class="sxs-lookup"><span data-stu-id="693ee-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="693ee-238">单击到右侧的齿轮图标，然后选择**编辑脚本**。</span><span class="sxs-lookup"><span data-stu-id="693ee-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="693ee-239">探索**SpeechInputSource.cs**若要了解如何使用**KeywordRecognizer**添加语音命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="693ee-240">生成和部署</span><span class="sxs-lookup"><span data-stu-id="693ee-240">Build and Deploy</span></span>

* <span data-ttu-id="693ee-241">在 Unity 中，使用**文件 > 生成设置**重新生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="693ee-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="693ee-242">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="693ee-242">Open the **App** folder.</span></span>
* <span data-ttu-id="693ee-243">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="693ee-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="693ee-244">（如果你已生成/部署此项目在 Visual Studio 中的在设置过程，然后您可以打开与该实例并单击全部重新加载出现提示时）。</span><span class="sxs-lookup"><span data-stu-id="693ee-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="693ee-245">在 Visual Studio 中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="693ee-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="693ee-246">在应用程序部署到 HoloLens 后，关闭配合的框使用[敲击](gestures.md#air-tap)手势。</span><span class="sxs-lookup"><span data-stu-id="693ee-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="693ee-247">注视顶级的监视。</span><span class="sxs-lookup"><span data-stu-id="693ee-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="693ee-248">当监视具有焦点时，验证光标更改为麦克风。</span><span class="sxs-lookup"><span data-stu-id="693ee-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="693ee-249">这提供了应用程序正在侦听的语音命令的反馈。</span><span class="sxs-lookup"><span data-stu-id="693ee-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="693ee-250">验证在手表上显示工具提示。</span><span class="sxs-lookup"><span data-stu-id="693ee-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="693ee-251">这有助于用户发现 *"打开 Communicator"* 命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="693ee-252">监视在观望，同时说 *"打开 Communicator"* 打开 communicator 面板。</span><span class="sxs-lookup"><span data-stu-id="693ee-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="693ee-253">第 2 章-确认</span><span class="sxs-lookup"><span data-stu-id="693ee-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="693ee-254">目标</span><span class="sxs-lookup"><span data-stu-id="693ee-254">Objectives</span></span>

* <span data-ttu-id="693ee-255">记录使用麦克风输入的消息。</span><span class="sxs-lookup"><span data-stu-id="693ee-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="693ee-256">向应用程序正在侦听到他们的语音的用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="693ee-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="693ee-257">**麦克风**从麦克风录制的应用必须声明功能。</span><span class="sxs-lookup"><span data-stu-id="693ee-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="693ee-258">这是为您已在 MR 输入 212 但记住这一点对于您自己的项目。</span><span class="sxs-lookup"><span data-stu-id="693ee-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="693ee-259">在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置</span><span class="sxs-lookup"><span data-stu-id="693ee-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="693ee-260">单击"通用 Windows 平台"选项卡</span><span class="sxs-lookup"><span data-stu-id="693ee-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="693ee-261">在"发布设置 > 功能"部分中，检查**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="693ee-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="693ee-262">说明</span><span class="sxs-lookup"><span data-stu-id="693ee-262">Instructions</span></span>

* <span data-ttu-id="693ee-263">在 Unity 中的**层次结构**面板中，确认**holoComm_screen_mesh**选择对象。</span><span class="sxs-lookup"><span data-stu-id="693ee-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="693ee-264">在中**Inspector**面板中，找到**顶级监视 （脚本）** 组件。</span><span class="sxs-lookup"><span data-stu-id="693ee-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="693ee-265">单击小的蓝色多维数据集上设置的值为**Communicator Prefab**属性。</span><span class="sxs-lookup"><span data-stu-id="693ee-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="693ee-266">在中**项目**面板中， **Communicator**预设现在应具有焦点。</span><span class="sxs-lookup"><span data-stu-id="693ee-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="693ee-267">单击**Communicator**预设中**项目**面板以查看在其组件**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="693ee-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="693ee-268">看看**麦克风管理器 （脚本）** 组件，这将使我们能够记录用户的声音。</span><span class="sxs-lookup"><span data-stu-id="693ee-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="693ee-269">请注意， **Communicator**对象具有**语音输入处理程序 （脚本）** 组件响应**发送消息**命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="693ee-270">看看**Communicator （脚本）** 组件，然后双击该脚本以在 Visual Studio 中打开它。</span><span class="sxs-lookup"><span data-stu-id="693ee-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="693ee-271">Communicator.cs 负责 communicator 设备上设置适当的按钮状态。</span><span class="sxs-lookup"><span data-stu-id="693ee-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="693ee-272">这样，我们用于记录一条消息，播放该录制，并将消息发送到顶级的用户。</span><span class="sxs-lookup"><span data-stu-id="693ee-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="693ee-273">它还将启动和停止的动画的批窗体，以向用户确认他们的语音已听说过。</span><span class="sxs-lookup"><span data-stu-id="693ee-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="693ee-274">在中**Communicator.cs**，删除以下行 （81 和 82） 从**启动**方法。</span><span class="sxs-lookup"><span data-stu-id="693ee-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="693ee-275">这将使 communicator 上的 Record 按钮。</span><span class="sxs-lookup"><span data-stu-id="693ee-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="693ee-276">生成和部署</span><span class="sxs-lookup"><span data-stu-id="693ee-276">Build and Deploy</span></span>

* <span data-ttu-id="693ee-277">在 Visual Studio 中，重新生成应用程序和部署到设备。</span><span class="sxs-lookup"><span data-stu-id="693ee-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="693ee-278">注视顶级的监视和说 *"打开 Communicator"* 显示 communicator。</span><span class="sxs-lookup"><span data-stu-id="693ee-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="693ee-279">按**记录**按钮 （麦克风） 若要开始录制的顶级口头消息。</span><span class="sxs-lookup"><span data-stu-id="693ee-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="693ee-280">开始说话，并验证批动画在 communicator，它提供给用户的反馈其言论被大家听到上播放。</span><span class="sxs-lookup"><span data-stu-id="693ee-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="693ee-281">按**停止**按钮 （左的正方形），并验证批动画停止运行。</span><span class="sxs-lookup"><span data-stu-id="693ee-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="693ee-282">按**播放**按钮以播放录制的消息，然后在设备上听到 （直角三角形）。</span><span class="sxs-lookup"><span data-stu-id="693ee-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="693ee-283">按**停止**按钮 （右正方形） 若要停止播放录制的消息。</span><span class="sxs-lookup"><span data-stu-id="693ee-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="693ee-284">说 *"发送消息"* 关闭 communicator 并接收来自顶级的消息已接收响应。</span><span class="sxs-lookup"><span data-stu-id="693ee-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="693ee-285">第 3 章-了解和听写识别器</span><span class="sxs-lookup"><span data-stu-id="693ee-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="693ee-286">目标</span><span class="sxs-lookup"><span data-stu-id="693ee-286">Objectives</span></span>

* <span data-ttu-id="693ee-287">使用听写识别器来将用户的语音转换为文本。</span><span class="sxs-lookup"><span data-stu-id="693ee-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="693ee-288">在 communicator 中显示结果时听写识别器的零假设和最终结果。</span><span class="sxs-lookup"><span data-stu-id="693ee-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="693ee-289">在本章中，我们将使用听写识别器为顶级创建一条消息。</span><span class="sxs-lookup"><span data-stu-id="693ee-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="693ee-290">在使用时听写识别器，请记住：</span><span class="sxs-lookup"><span data-stu-id="693ee-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="693ee-291">您必须连接到 WiFi 时听写识别器工作。</span><span class="sxs-lookup"><span data-stu-id="693ee-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="693ee-292">在一段时间后，会出现超时。</span><span class="sxs-lookup"><span data-stu-id="693ee-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="693ee-293">有两个超时，需要注意的：</span><span class="sxs-lookup"><span data-stu-id="693ee-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="693ee-294">如果识别器开始，并为第一个 5 秒将不会收听任何音频，就会超时。</span><span class="sxs-lookup"><span data-stu-id="693ee-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="693ee-295">如果识别器提供结果，但然后会静默听到 20 秒，就会超时。</span><span class="sxs-lookup"><span data-stu-id="693ee-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="693ee-296">只有一种类型的识别器 （关键字或听写） 可以运行一次。</span><span class="sxs-lookup"><span data-stu-id="693ee-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="693ee-297">**麦克风**从麦克风录制的应用必须声明功能。</span><span class="sxs-lookup"><span data-stu-id="693ee-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="693ee-298">这是为您已在 MR 输入 212 但记住这一点对于您自己的项目。</span><span class="sxs-lookup"><span data-stu-id="693ee-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="693ee-299">在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置</span><span class="sxs-lookup"><span data-stu-id="693ee-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="693ee-300">单击"通用 Windows 平台"选项卡</span><span class="sxs-lookup"><span data-stu-id="693ee-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="693ee-301">在"发布设置 > 功能"部分中，检查**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="693ee-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="693ee-302">说明</span><span class="sxs-lookup"><span data-stu-id="693ee-302">Instructions</span></span>

<span data-ttu-id="693ee-303">我们将编辑**MicrophoneManager.cs**使用听写识别器。</span><span class="sxs-lookup"><span data-stu-id="693ee-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="693ee-304">这是我们将添加：</span><span class="sxs-lookup"><span data-stu-id="693ee-304">This is what we'll add:</span></span>

1. <span data-ttu-id="693ee-305">当**记录按钮**是按下，我们将**启动 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="693ee-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="693ee-306">显示**假设**DictationRecognizer 理解。</span><span class="sxs-lookup"><span data-stu-id="693ee-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="693ee-307">锁定**结果**DictationRecognizer 理解。</span><span class="sxs-lookup"><span data-stu-id="693ee-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="693ee-308">检查从 DictationRecognizer 超时。</span><span class="sxs-lookup"><span data-stu-id="693ee-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="693ee-309">当**停止按钮**按下时，或 mic 会话超时**停止 DictationRecognizer**。</span><span class="sxs-lookup"><span data-stu-id="693ee-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="693ee-310">重新启动**KeywordRecognizer**，将侦听**发送消息**命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="693ee-311">让我们开始吧。</span><span class="sxs-lookup"><span data-stu-id="693ee-311">Let's get started.</span></span> <span data-ttu-id="693ee-312">完成 3.a 中的所有编码练习**MicrophoneManager.cs**，或复制并粘贴下面找到的已完成的代码：</span><span class="sxs-lookup"><span data-stu-id="693ee-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="693ee-313">生成和部署</span><span class="sxs-lookup"><span data-stu-id="693ee-313">Build and Deploy</span></span>

* <span data-ttu-id="693ee-314">在 Visual Studio 中重新生成并部署到你的设备。</span><span class="sxs-lookup"><span data-stu-id="693ee-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="693ee-315">关闭与-敲击手势的适合性的框。</span><span class="sxs-lookup"><span data-stu-id="693ee-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="693ee-316">注视顶级的监视和说 *"打开 Communicator"*。</span><span class="sxs-lookup"><span data-stu-id="693ee-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="693ee-317">选择**记录**按钮 （麦克风） 来记录您的消息。</span><span class="sxs-lookup"><span data-stu-id="693ee-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="693ee-318">开始说话。</span><span class="sxs-lookup"><span data-stu-id="693ee-318">Start speaking.</span></span> <span data-ttu-id="693ee-319">**听写识别器**会解释语音，并在 communicator 中显示的零假设的文本。</span><span class="sxs-lookup"><span data-stu-id="693ee-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="693ee-320">尝试说 *"发送消息"* 时记录一条消息。</span><span class="sxs-lookup"><span data-stu-id="693ee-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="693ee-321">请注意，**关键字识别器**不会响应因为**听写识别器**仍处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="693ee-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="693ee-322">结束说话几秒钟。</span><span class="sxs-lookup"><span data-stu-id="693ee-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="693ee-323">观看听写识别器完成其假设，并显示了最终结果。</span><span class="sxs-lookup"><span data-stu-id="693ee-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="693ee-324">开始说到，然后暂停 20 秒。</span><span class="sxs-lookup"><span data-stu-id="693ee-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="693ee-325">这将导致**听写识别器**超时。</span><span class="sxs-lookup"><span data-stu-id="693ee-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="693ee-326">请注意，**关键字识别器**上述超时后重新启用。</span><span class="sxs-lookup"><span data-stu-id="693ee-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="693ee-327">Communicator 现在将响应语音命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="693ee-328">说 *"发送消息"* 若要将消息发送到顶级。</span><span class="sxs-lookup"><span data-stu-id="693ee-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="693ee-329">第 4 章-语法识别器</span><span class="sxs-lookup"><span data-stu-id="693ee-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="693ee-330">目标</span><span class="sxs-lookup"><span data-stu-id="693ee-330">Objectives</span></span>

* <span data-ttu-id="693ee-331">使用语法识别器识别根据 SRGS 或语音识别语法规范，文件的用户的语音。</span><span class="sxs-lookup"><span data-stu-id="693ee-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="693ee-332">**麦克风**从麦克风录制的应用必须声明功能。</span><span class="sxs-lookup"><span data-stu-id="693ee-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="693ee-333">这是为您已在 MR 输入 212 但记住这一点对于您自己的项目。</span><span class="sxs-lookup"><span data-stu-id="693ee-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="693ee-334">在 Unity 编辑器中，通过导航到"编辑 > 项目设置 > Player"转到播放机设置</span><span class="sxs-lookup"><span data-stu-id="693ee-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="693ee-335">单击"通用 Windows 平台"选项卡</span><span class="sxs-lookup"><span data-stu-id="693ee-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="693ee-336">在"发布设置 > 功能"部分中，检查**麦克风**功能</span><span class="sxs-lookup"><span data-stu-id="693ee-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="693ee-337">说明</span><span class="sxs-lookup"><span data-stu-id="693ee-337">Instructions</span></span>

1. <span data-ttu-id="693ee-338">在中**层次结构**面板中，搜索**Jetpack_Center**并将其选中。</span><span class="sxs-lookup"><span data-stu-id="693ee-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="693ee-339">寻找**免除操作**中编写脚本**Inspector**面板。</span><span class="sxs-lookup"><span data-stu-id="693ee-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="693ee-340">单击右侧的小圆圈**对象到标记沿**字段。</span><span class="sxs-lookup"><span data-stu-id="693ee-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="693ee-341">在弹出窗口中，搜索**SRGSToolbox**并从列表中选择它。</span><span class="sxs-lookup"><span data-stu-id="693ee-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="693ee-342">看一看**SRGSColor.xml**中的文件**StreamingAssets**文件夹。</span><span class="sxs-lookup"><span data-stu-id="693ee-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="693ee-343">可以在 W3C 网站上找到 SRGS 设计规范[此处](https://www.w3.org/TR/speech-grammar/)。</span><span class="sxs-lookup"><span data-stu-id="693ee-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="693ee-344">在我们 SRGS 文件中，我们有三种类型的规则：</span><span class="sxs-lookup"><span data-stu-id="693ee-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="693ee-345">规则，它允许你说一种颜色从十二个颜色的列表。</span><span class="sxs-lookup"><span data-stu-id="693ee-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="693ee-346">侦听的颜色规则和三个形状之一的组合这三个规则。</span><span class="sxs-lookup"><span data-stu-id="693ee-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="693ee-347">根规则，colorChooser，侦听的三个"颜色 + 形状"规则的任意组合。</span><span class="sxs-lookup"><span data-stu-id="693ee-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="693ee-348">可以说形状，按任意顺序，并在任意数量只是一到所有这三个。</span><span class="sxs-lookup"><span data-stu-id="693ee-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="693ee-349">这是，所侦听的唯一规则，因为它指定为初始中的文件顶部的根规则&lt;语法&gt;标记。</span><span class="sxs-lookup"><span data-stu-id="693ee-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="693ee-350">生成和部署</span><span class="sxs-lookup"><span data-stu-id="693ee-350">Build and Deploy</span></span>

* <span data-ttu-id="693ee-351">重新生成应用程序在 Unity 中，然后生成并从 Visual Studio 体验 HoloLens 上的应用程序部署。</span><span class="sxs-lookup"><span data-stu-id="693ee-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="693ee-352">关闭与-敲击手势的适合性的框。</span><span class="sxs-lookup"><span data-stu-id="693ee-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="693ee-353">注视顶级 jetpack 和执行-敲击手势。</span><span class="sxs-lookup"><span data-stu-id="693ee-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="693ee-354">开始说话。</span><span class="sxs-lookup"><span data-stu-id="693ee-354">Start speaking.</span></span> <span data-ttu-id="693ee-355">**语法识别器**将解释语音和更改基于识别的形状的颜色。</span><span class="sxs-lookup"><span data-stu-id="693ee-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="693ee-356">示例命令是"蓝色圆圈，黄色 square"。</span><span class="sxs-lookup"><span data-stu-id="693ee-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="693ee-357">执行另一个-敲击手势以关闭工具箱。</span><span class="sxs-lookup"><span data-stu-id="693ee-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="693ee-358">结束</span><span class="sxs-lookup"><span data-stu-id="693ee-358">The End</span></span>

<span data-ttu-id="693ee-359">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="693ee-359">Congratulations!</span></span> <span data-ttu-id="693ee-360">你现在已经完成**MR 输入 212:语音**。</span><span class="sxs-lookup"><span data-stu-id="693ee-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="693ee-361">您知道的语音命令的注意事项。</span><span class="sxs-lookup"><span data-stu-id="693ee-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="693ee-362">你已了解如何已使用的工具提示，让用户知道的语音命令。</span><span class="sxs-lookup"><span data-stu-id="693ee-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="693ee-363">您看到了几种类型的用于确认用户的语音已听说过的反馈。</span><span class="sxs-lookup"><span data-stu-id="693ee-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="693ee-364">您知道如何切换关键字识别和听写识别器，并且这两个功能如何了解和解释您的声音。</span><span class="sxs-lookup"><span data-stu-id="693ee-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="693ee-365">您学习了如何在应用程序中的语音识别的使用 SRGS 文件和语法识别器。</span><span class="sxs-lookup"><span data-stu-id="693ee-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
