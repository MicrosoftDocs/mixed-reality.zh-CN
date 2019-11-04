---
title: MR 输入 211-手势
description: 按照以下编码演练操作，使用 Unity、Visual Studio 和 HoloLens 来了解手势概念的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit-unity，学院，教程，手势
ms.openlocfilehash: d7a92e4b2f196d6d8b0ba0fe3ccb2aed87479ac1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434696"
---
>[!NOTE]
><span data-ttu-id="f3000-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="f3000-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f3000-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="f3000-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f3000-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="f3000-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f3000-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="f3000-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f3000-108">为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="f3000-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="f3000-109">MR 输入211：手势</span><span class="sxs-lookup"><span data-stu-id="f3000-109">MR Input 211: Gesture</span></span>

<span data-ttu-id="f3000-110">[手势](gaze-and-commit.md#composite-gestures)会使用户意向变为操作。</span><span class="sxs-lookup"><span data-stu-id="f3000-110">[Gestures](gaze-and-commit.md#composite-gestures) turn user intention into action.</span></span> <span data-ttu-id="f3000-111">借助笔势，用户可以与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="f3000-111">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="f3000-112">在本课程中，我们将了解如何跟踪用户的动手，响应用户输入，并根据手头状态和位置向用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="f3000-112">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="f3000-113">在[先生/女士 101](holograms-101.md)中，我们使用了一种简单的点击手势来与全息影像交互。</span><span class="sxs-lookup"><span data-stu-id="f3000-113">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="f3000-114">现在，我们将转到轻攻攻攻，并探索新的概念：</span><span class="sxs-lookup"><span data-stu-id="f3000-114">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="f3000-115">检测何时跟踪用户的手并向用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="f3000-115">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="f3000-116">使用导航手势旋转全息影像。</span><span class="sxs-lookup"><span data-stu-id="f3000-116">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="f3000-117">请在用户即将退出查看时提供反馈。</span><span class="sxs-lookup"><span data-stu-id="f3000-117">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="f3000-118">使用操作事件可允许用户使用其手移动全息影像。</span><span class="sxs-lookup"><span data-stu-id="f3000-118">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="f3000-119">在本课程中，我们将重新访问 Unity 项目**模型资源管理器，该资源管理器**是在[MR Input 210](holograms-210.md)中生成的。</span><span class="sxs-lookup"><span data-stu-id="f3000-119">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="f3000-120">我们 astronaut 的朋友会回来，帮助我们探索这些新的手势概念。</span><span class="sxs-lookup"><span data-stu-id="f3000-120">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f3000-121">以下各章中嵌入的视频使用较旧版本的 Unity 和混合现实工具包记录。</span><span class="sxs-lookup"><span data-stu-id="f3000-121">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="f3000-122">虽然分步说明准确且最新，但你可能会看到处于过期状态的相应视频中的脚本和视觉对象。</span><span class="sxs-lookup"><span data-stu-id="f3000-122">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="f3000-123">视频仍包含在 posterity 中，因为涵盖的概念仍适用。</span><span class="sxs-lookup"><span data-stu-id="f3000-123">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="f3000-124">设备支持</span><span class="sxs-lookup"><span data-stu-id="f3000-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f3000-125">摘要</span><span class="sxs-lookup"><span data-stu-id="f3000-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f3000-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f3000-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f3000-127"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="f3000-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="f3000-128">MR 输入211：手势</span><span class="sxs-lookup"><span data-stu-id="f3000-128">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="f3000-129">✔️</span><span class="sxs-lookup"><span data-stu-id="f3000-129">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f3000-130">✔️</span><span class="sxs-lookup"><span data-stu-id="f3000-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="f3000-131">开始之前</span><span class="sxs-lookup"><span data-stu-id="f3000-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f3000-132">必备条件</span><span class="sxs-lookup"><span data-stu-id="f3000-132">Prerequisites</span></span>

* <span data-ttu-id="f3000-133">配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="f3000-133">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="f3000-134">一些基本C#的编程能力。</span><span class="sxs-lookup"><span data-stu-id="f3000-134">Some basic C# programming ability.</span></span>
* <span data-ttu-id="f3000-135">应已完成[尊敬的基本知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="f3000-135">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="f3000-136">应已完成[MR 输入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="f3000-136">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="f3000-137">[为开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 设备。</span><span class="sxs-lookup"><span data-stu-id="f3000-137">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="f3000-138">项目文件</span><span class="sxs-lookup"><span data-stu-id="f3000-138">Project files</span></span>

* <span data-ttu-id="f3000-139">下载项目所需的[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)。</span><span class="sxs-lookup"><span data-stu-id="f3000-139">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="f3000-140"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="f3000-140"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="f3000-141">取消将文件存档到桌面或其他易于访问的位置。</span><span class="sxs-lookup"><span data-stu-id="f3000-141">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="f3000-142">如果要在下载之前查看源代码，[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)找到。</span><span class="sxs-lookup"><span data-stu-id="f3000-142">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="f3000-143">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="f3000-143">Errata and Notes</span></span>

* <span data-ttu-id="f3000-144">需要在 Visual Studio 的 "工具"-"> 选项-> 调试" 中禁用（*取消选中*） "启用仅我的代码"，以便在代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="f3000-144">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="f3000-145">第0章-Unity 设置</span><span class="sxs-lookup"><span data-stu-id="f3000-145">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="f3000-146">说明</span><span class="sxs-lookup"><span data-stu-id="f3000-146">Instructions</span></span>

1. <span data-ttu-id="f3000-147">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="f3000-147">Start Unity.</span></span>
2. <span data-ttu-id="f3000-148">选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-148">Select **Open**.</span></span>
3. <span data-ttu-id="f3000-149">导航到之前未存档的**手势**文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3000-149">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="f3000-150">找到并选择 "**开始**/**模型资源管理器**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3000-150">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="f3000-151">单击 "**选择文件夹**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f3000-151">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="f3000-152">在 "**项目**" 面板中，展开 "**场景**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3000-152">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="f3000-153">双击 " **ModelExplorer**场景" 将其加载到 Unity。</span><span class="sxs-lookup"><span data-stu-id="f3000-153">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="f3000-154">生成</span><span class="sxs-lookup"><span data-stu-id="f3000-154">Building</span></span>

1. <span data-ttu-id="f3000-155">在 Unity 中，选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-155">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="f3000-156">如果场景 **/ModelExplorer**未列在 "**生成**" 中，请单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="f3000-156">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="f3000-157">如果要专门针对 HoloLens 进行开发，请将 "**目标设备**" 设置为 " **hololens**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-157">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="f3000-158">否则，请将其留在**任何设备**上。</span><span class="sxs-lookup"><span data-stu-id="f3000-158">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="f3000-159">确保将 "**生成类型**" 设置为 " **D3D** "，并将 " **SDK** " 设置为 "**最新安装**的" （应为 SDK 16299 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="f3000-159">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="f3000-160">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="f3000-160">Click **Build**.</span></span>
6. <span data-ttu-id="f3000-161">创建名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="f3000-161">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="f3000-162">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3000-162">Single click the **App** folder.</span></span>
8. <span data-ttu-id="f3000-163">按**选择文件夹**，Unity 将开始为 Visual Studio 生成项目。</span><span class="sxs-lookup"><span data-stu-id="f3000-163">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="f3000-164">当 Unity 完成后，将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="f3000-164">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="f3000-165">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3000-165">Open the **App** folder.</span></span>
2. <span data-ttu-id="f3000-166">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="f3000-166">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="f3000-167">如果部署到 HoloLens：</span><span class="sxs-lookup"><span data-stu-id="f3000-167">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="f3000-168">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **x86**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-168">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="f3000-169">单击 "本地计算机" 按钮旁的下拉箭头，然后选择 "**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-169">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="f3000-170">输入**HoloLens 设备 IP 地址**，并将身份验证模式设置为**通用（未加密的协议）** 。</span><span class="sxs-lookup"><span data-stu-id="f3000-170">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="f3000-171">单击 "**选择**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-171">Click **Select**.</span></span> <span data-ttu-id="f3000-172">如果你不知道设备 IP 地址，请在 "设置" 中查找 " **> 网络 & Internet > 高级选项**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-172">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="f3000-173">在顶部菜单栏中，单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="f3000-173">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="f3000-174">如果这是首次部署到设备，则需要将[其与 Visual Studio 配对](using-visual-studio.md#pairing-your-device)。</span><span class="sxs-lookup"><span data-stu-id="f3000-174">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="f3000-175">当应用程序已部署后，使用**选择手势**关闭**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="f3000-175">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="f3000-176">如果要部署到沉浸式耳机：</span><span class="sxs-lookup"><span data-stu-id="f3000-176">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="f3000-177">使用 Visual Studio 中的顶部工具栏，将目标从 "调试" 更改为 "**发布**"，将 "从 ARM" 更改为 " **x64**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-177">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="f3000-178">确保将部署目标设置为 "**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-178">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="f3000-179">在顶部菜单栏中，单击 "**调试-> 启动而不调试**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="f3000-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="f3000-180">当应用程序已部署后，通过将触发器拖到运动控制器上来关闭**Fitbox** 。</span><span class="sxs-lookup"><span data-stu-id="f3000-180">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="f3000-181">你可能会注意到 Visual Studio 错误面板中出现一些红色错误。</span><span class="sxs-lookup"><span data-stu-id="f3000-181">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="f3000-182">可以放心地忽略它们。</span><span class="sxs-lookup"><span data-stu-id="f3000-182">It is safe to ignore them.</span></span> <span data-ttu-id="f3000-183">切换到 "输出" 面板以查看实际的生成进度。</span><span class="sxs-lookup"><span data-stu-id="f3000-183">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="f3000-184">"输出" 面板中的错误将要求您进行修复（通常是由于脚本中的错误而导致的）。</span><span class="sxs-lookup"><span data-stu-id="f3000-184">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="f3000-185">第1章-手动检测的反馈</span><span class="sxs-lookup"><span data-stu-id="f3000-185">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="f3000-186">目标</span><span class="sxs-lookup"><span data-stu-id="f3000-186">Objectives</span></span>

* <span data-ttu-id="f3000-187">订阅手动跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="f3000-187">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="f3000-188">使用光标反馈向用户显示要跟踪的用户。</span><span class="sxs-lookup"><span data-stu-id="f3000-188">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="f3000-189">在 HoloLens 2 上，只要指针可见（而不仅仅是指手指处于向上状态时），就会触发指针。</span><span class="sxs-lookup"><span data-stu-id="f3000-189">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="f3000-190">说明</span><span class="sxs-lookup"><span data-stu-id="f3000-190">Instructions</span></span>

* <span data-ttu-id="f3000-191">在 "**层次结构**" 面板中，展开 " **InputManager** " 对象。</span><span class="sxs-lookup"><span data-stu-id="f3000-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="f3000-192">查找并选择 " **GesturesInput** " 对象。</span><span class="sxs-lookup"><span data-stu-id="f3000-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="f3000-193">**InteractionInputSource.cs**脚本将执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="f3000-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="f3000-194">订阅 InteractionSourceDetected 和 InteractionSourceLost 事件。</span><span class="sxs-lookup"><span data-stu-id="f3000-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="f3000-195">设置 HandDetected 状态。</span><span class="sxs-lookup"><span data-stu-id="f3000-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="f3000-196">取消订阅 InteractionSourceDetected 和 InteractionSourceLost 事件。</span><span class="sxs-lookup"><span data-stu-id="f3000-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="f3000-197">接下来，我们将根据用户的操作，将游标从[MR 输入 210](holograms-210.md)升级到显示反馈的游标。</span><span class="sxs-lookup"><span data-stu-id="f3000-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="f3000-198">在 "**层次结构**" 面板中，选择**光标**对象并将其删除。</span><span class="sxs-lookup"><span data-stu-id="f3000-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="f3000-199">在 "**项目**" 面板中，搜索 " **CursorWithFeedback** " 并将其拖到 "**层次结构**" 面板中。</span><span class="sxs-lookup"><span data-stu-id="f3000-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="f3000-200">在 "**层次结构**" 面板中单击 " **InputManager** "，然后将**CursorWithFeedback**对象从**层次结构**拖到**检查器**。</span><span class="sxs-lookup"><span data-stu-id="f3000-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="f3000-201">在**层次结构**中单击 " **CursorWithFeedback** "。</span><span class="sxs-lookup"><span data-stu-id="f3000-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="f3000-202">在 "**检查器**" 面板中，展开**对象游标**脚本上的 "**游标状态数据**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="f3000-203">**游标状态数据**的工作方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="f3000-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="f3000-204">任何**观察**状态都意味着未检测到任何手形，用户只需查看。</span><span class="sxs-lookup"><span data-stu-id="f3000-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="f3000-205">任何**交互**状态都表示检测到手型或控制器。</span><span class="sxs-lookup"><span data-stu-id="f3000-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="f3000-206">任何**悬停**状态都意味着用户正在查看全息影像。</span><span class="sxs-lookup"><span data-stu-id="f3000-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="f3000-207">生成和部署</span><span class="sxs-lookup"><span data-stu-id="f3000-207">Build and Deploy</span></span>

* <span data-ttu-id="f3000-208">在 Unity 中，使用**File > 生成设置**重新生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="f3000-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="f3000-209">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="f3000-209">Open the **App** folder.</span></span>
* <span data-ttu-id="f3000-210">如果它尚未打开，请打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="f3000-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="f3000-211">（如果在安装过程中已经在 Visual Studio 中生成或部署了此项目，则可以打开 VS 的实例，并在出现提示时单击 "全部重新加载"）。</span><span class="sxs-lookup"><span data-stu-id="f3000-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="f3000-212">在 Visual Studio 中，单击 "**调试"-> "无调试开始**" 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="f3000-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="f3000-213">在应用程序部署到 HoloLens 后，请使用 "轻攻攻" 手势关闭 fitbox。</span><span class="sxs-lookup"><span data-stu-id="f3000-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="f3000-214">将您的手转到视图，并将您的索引手指指向天空，开始进行手动跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3000-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="f3000-215">向左、向右、向下和向下移动。</span><span class="sxs-lookup"><span data-stu-id="f3000-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="f3000-216">监视在检测到您的手形后光标发生变化的方式，并从视图中丢失。</span><span class="sxs-lookup"><span data-stu-id="f3000-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="f3000-217">如果你使用的是沉浸式耳机，则必须连接并断开控制器的连接。</span><span class="sxs-lookup"><span data-stu-id="f3000-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="f3000-218">此反馈在沉浸式设备上变得不太感兴趣，因为连接的控制器始终为 "可用"。</span><span class="sxs-lookup"><span data-stu-id="f3000-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="f3000-219">第2章-导航</span><span class="sxs-lookup"><span data-stu-id="f3000-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="f3000-220">目标</span><span class="sxs-lookup"><span data-stu-id="f3000-220">Objectives</span></span>

* <span data-ttu-id="f3000-221">使用导航手势事件来轮换 astronaut。</span><span class="sxs-lookup"><span data-stu-id="f3000-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="f3000-222">说明</span><span class="sxs-lookup"><span data-stu-id="f3000-222">Instructions</span></span>

<span data-ttu-id="f3000-223">若要在应用中使用导航笔势，我们将在导航手势发生时编辑**GestureAction.cs**来旋转对象。</span><span class="sxs-lookup"><span data-stu-id="f3000-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="f3000-224">此外，我们还会将反馈添加到要在导航可用时显示的光标。</span><span class="sxs-lookup"><span data-stu-id="f3000-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="f3000-225">在 "**层次结构**" 面板中，展开 " **CursorWithFeedback**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="f3000-226">在**全息影像**文件夹中，找到 " **ScrollFeedback**资产"。</span><span class="sxs-lookup"><span data-stu-id="f3000-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="f3000-227">将**ScrollFeedback** prefab 拖放到**层次结构**中的**CursorWithFeedback** GameObject。</span><span class="sxs-lookup"><span data-stu-id="f3000-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="f3000-228">单击**CursorWithFeedback**。</span><span class="sxs-lookup"><span data-stu-id="f3000-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="f3000-229">在**检查器**面板中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f3000-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="f3000-230">在菜单中，在 "搜索" 框中键入**CursorFeedback**。</span><span class="sxs-lookup"><span data-stu-id="f3000-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="f3000-231">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="f3000-231">Select the search result.</span></span>
7. <span data-ttu-id="f3000-232">将**ScrollFeedback**对象从**层次结构**中拖放到**检查器**的**光标反馈**组件中的 "**滚动检测到的游戏对象**" 属性上。</span><span class="sxs-lookup"><span data-stu-id="f3000-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="f3000-233">在 "**层次结构**" 面板中，选择 " **AstroMan** " 对象。</span><span class="sxs-lookup"><span data-stu-id="f3000-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="f3000-234">在**检查器**面板中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f3000-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="f3000-235">在菜单中，键入 "搜索框**手势" 操作**。</span><span class="sxs-lookup"><span data-stu-id="f3000-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="f3000-236">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="f3000-236">Select the search result.</span></span>

<span data-ttu-id="f3000-237">接下来，在 Visual Studio 中打开**GestureAction.cs** 。</span><span class="sxs-lookup"><span data-stu-id="f3000-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="f3000-238">在编码练习 2. c 中，编辑脚本以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f3000-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="f3000-239">只要执行导航手势，就会**旋转 AstroMan**对象。</span><span class="sxs-lookup"><span data-stu-id="f3000-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="f3000-240">计算**rotationFactor**以控制应用于对象的旋转量。</span><span class="sxs-lookup"><span data-stu-id="f3000-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="f3000-241">当用户向左或向右移动对象时，绕 y 轴**旋转对象**。</span><span class="sxs-lookup"><span data-stu-id="f3000-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="f3000-242">在脚本中完成编码演练 2. c，或将代码替换为以下已完成的解决方案：</span><span class="sxs-lookup"><span data-stu-id="f3000-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="f3000-243">你会注意到，其他导航事件已经填充了某些信息。</span><span class="sxs-lookup"><span data-stu-id="f3000-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="f3000-244">我们将 GameObject 推送到工具包的 InputSystem's 模式堆栈上，这样用户就无需在旋转开始后在 Astronaut 上保持焦点。</span><span class="sxs-lookup"><span data-stu-id="f3000-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="f3000-245">同样，在完成该笔势后，将从堆栈中弹出 GameObject。</span><span class="sxs-lookup"><span data-stu-id="f3000-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="f3000-246">生成和部署</span><span class="sxs-lookup"><span data-stu-id="f3000-246">Build and Deploy</span></span>

1. <span data-ttu-id="f3000-247">重新生成 Unity 中的应用程序，然后从 Visual Studio 生成并部署，以便在 HoloLens 中运行。</span><span class="sxs-lookup"><span data-stu-id="f3000-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="f3000-248">注视 astronaut，光标两侧应会出现两个箭头。</span><span class="sxs-lookup"><span data-stu-id="f3000-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="f3000-249">此新视觉对象指示 astronaut 可以旋转。</span><span class="sxs-lookup"><span data-stu-id="f3000-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="f3000-250">将手置于 "就绪" 位置（食指指向天空），以便 HoloLens 开始跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3000-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="f3000-251">若要旋转 astronaut，请将食指降低到挤压位置，然后向左或向右移动以触发 NavigationX 手势。</span><span class="sxs-lookup"><span data-stu-id="f3000-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="f3000-252">第三章-手写指南</span><span class="sxs-lookup"><span data-stu-id="f3000-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="f3000-253">目标</span><span class="sxs-lookup"><span data-stu-id="f3000-253">Objectives</span></span>

* <span data-ttu-id="f3000-254">使用 "**手动指南分数**" 有助于预测何时会丢失手动跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3000-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="f3000-255">提供**有关光标的反馈**，以便在用户尝试观看相机边缘时显示。</span><span class="sxs-lookup"><span data-stu-id="f3000-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="f3000-256">说明</span><span class="sxs-lookup"><span data-stu-id="f3000-256">Instructions</span></span>

1. <span data-ttu-id="f3000-257">在 "**层次结构**" 面板中，选择 " **CursorWithFeedback** " 对象。</span><span class="sxs-lookup"><span data-stu-id="f3000-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="f3000-258">在**检查器**面板中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f3000-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="f3000-259">在菜单中，键入搜索框的**指导**。</span><span class="sxs-lookup"><span data-stu-id="f3000-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="f3000-260">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="f3000-260">Select the search result.</span></span>
4. <span data-ttu-id="f3000-261">在 "**项目**"**面板中**，找到 " **HandGuidanceFeedback**资产"。</span><span class="sxs-lookup"><span data-stu-id="f3000-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="f3000-262">将**HandGuidanceFeedback**资产拖放到 "**检查器**" 面板中的 "**手写指南" 指示符**属性上。</span><span class="sxs-lookup"><span data-stu-id="f3000-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="f3000-263">生成和部署</span><span class="sxs-lookup"><span data-stu-id="f3000-263">Build and Deploy</span></span>

* <span data-ttu-id="f3000-264">重新生成 Unity 中的应用程序，然后从 Visual Studio 生成并部署，以在 HoloLens 上体验应用。</span><span class="sxs-lookup"><span data-stu-id="f3000-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="f3000-265">将你的手转到视图中，并抬起你的索引手指进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3000-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="f3000-266">开始旋转 astronaut，使其具有导航手势（将您的索引手指同时一起）。</span><span class="sxs-lookup"><span data-stu-id="f3000-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="f3000-267">向左、向右、向上、向下移动。</span><span class="sxs-lookup"><span data-stu-id="f3000-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="f3000-268">当手接近该笔势帧的边缘时，光标旁边应会出现一个箭头，警告您将丢失手动跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3000-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="f3000-269">箭头指示移动哪一方向，以防丢失跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3000-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="f3000-270">第4章-操作</span><span class="sxs-lookup"><span data-stu-id="f3000-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="f3000-271">目标</span><span class="sxs-lookup"><span data-stu-id="f3000-271">Objectives</span></span>

* <span data-ttu-id="f3000-272">使用操作事件将 astronaut 移动到手中。</span><span class="sxs-lookup"><span data-stu-id="f3000-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="f3000-273">提供有关游标的反馈，以让用户知道何时可以使用操作。</span><span class="sxs-lookup"><span data-stu-id="f3000-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="f3000-274">说明</span><span class="sxs-lookup"><span data-stu-id="f3000-274">Instructions</span></span>

<span data-ttu-id="f3000-275">GestureManager.cs 和 AstronautManager.cs 将允许我们执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="f3000-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="f3000-276">使用 speech 关键字 "**Move Astronaut**" 启用**操作**手势，并使用 "**旋转 Astronaut**" 来禁用它们。</span><span class="sxs-lookup"><span data-stu-id="f3000-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="f3000-277">切换到响应**操作笔势识别器**。</span><span class="sxs-lookup"><span data-stu-id="f3000-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="f3000-278">让我们开始吧。</span><span class="sxs-lookup"><span data-stu-id="f3000-278">Let's get started.</span></span>

1. <span data-ttu-id="f3000-279">在 "**层次结构**" 面板中，创建一个新的空 GameObject。</span><span class="sxs-lookup"><span data-stu-id="f3000-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="f3000-280">将其命名为 "**AstronautManager**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="f3000-281">在**检查器**面板中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f3000-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="f3000-282">在菜单中，在 "搜索" 框中键入 " **Astronaut Manager**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="f3000-283">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="f3000-283">Select the search result.</span></span>
4. <span data-ttu-id="f3000-284">在**检查器**面板中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f3000-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="f3000-285">在菜单中，在 "搜索" 框中键入 "**语音输入源**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="f3000-286">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="f3000-286">Select the search result.</span></span>

<span data-ttu-id="f3000-287">现在，我们将添加控制 astronaut 交互状态所需的语音命令。</span><span class="sxs-lookup"><span data-stu-id="f3000-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="f3000-288">展开**检查器**中的 "**关键字**" 部分。</span><span class="sxs-lookup"><span data-stu-id="f3000-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="f3000-289">单击右侧的 " **+** "，添加新的关键字。</span><span class="sxs-lookup"><span data-stu-id="f3000-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="f3000-290">将关键字键入为**Move Astronaut**。</span><span class="sxs-lookup"><span data-stu-id="f3000-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="f3000-291">如果需要，可以随意添加密钥快捷方式。</span><span class="sxs-lookup"><span data-stu-id="f3000-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="f3000-292">单击右侧的 " **+** "，添加新的关键字。</span><span class="sxs-lookup"><span data-stu-id="f3000-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="f3000-293">将关键字键入为**轮换 Astronaut**。</span><span class="sxs-lookup"><span data-stu-id="f3000-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="f3000-294">如果需要，可以随意添加密钥快捷方式。</span><span class="sxs-lookup"><span data-stu-id="f3000-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="f3000-295">可在**GestureAction.cs**中的**ISpeechHandler. OnSpeechKeywordRecognized**处理程序中找到相应的处理程序代码。</span><span class="sxs-lookup"><span data-stu-id="f3000-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![如何设置第4章的语音输入源](images/holograms211-speech.png)

<span data-ttu-id="f3000-297">接下来，我们将在游标上设置操作反馈。</span><span class="sxs-lookup"><span data-stu-id="f3000-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="f3000-298">在 "**项目**"**面板中**，找到 " **PathingFeedback**资产"。</span><span class="sxs-lookup"><span data-stu-id="f3000-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="f3000-299">将**PathingFeedback** prefab 拖放到**层次结构**中的**CursorWithFeedback**对象上。</span><span class="sxs-lookup"><span data-stu-id="f3000-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="f3000-300">在 "**层次结构**" 面板中，单击 " **CursorWithFeedback**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="f3000-301">将**PathingFeedback**对象从**层次结构**中拖放到**检查器**的 "**游标反馈**" 组件中的 "**检测到路径" 游戏对象**属性上。</span><span class="sxs-lookup"><span data-stu-id="f3000-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="f3000-302">现在，我们需要将代码添加到**GestureAction.cs** ，以启用以下内容：</span><span class="sxs-lookup"><span data-stu-id="f3000-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="f3000-303">将代码添加到**IManipulationHandler. OnManipulationUpdated**函数，该函数将在检测到**操作**笔势时移动 astronaut。</span><span class="sxs-lookup"><span data-stu-id="f3000-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="f3000-304">计算**移动向量**，以根据手头位置确定应将 astronaut 移动到的位置。</span><span class="sxs-lookup"><span data-stu-id="f3000-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="f3000-305">**将 Astronaut 移动**到新位置。</span><span class="sxs-lookup"><span data-stu-id="f3000-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="f3000-306">完成编码练习 4. 在**GestureAction.cs**中，或使用下面的已完成解决方案：</span><span class="sxs-lookup"><span data-stu-id="f3000-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="f3000-307">生成和部署</span><span class="sxs-lookup"><span data-stu-id="f3000-307">Build and Deploy</span></span>

* <span data-ttu-id="f3000-308">在 Unity 中重新生成，然后在 Visual Studio 中生成并部署，以在 HoloLens 中运行该应用。</span><span class="sxs-lookup"><span data-stu-id="f3000-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="f3000-309">将你的手移到 HoloLens 前面，并抬起你的食指，以便能够进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3000-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="f3000-310">将光标放在 astronaut 上。</span><span class="sxs-lookup"><span data-stu-id="f3000-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="f3000-311">说 "Move Astronaut" 将 Astronaut 与操作手势一起移动。</span><span class="sxs-lookup"><span data-stu-id="f3000-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="f3000-312">光标两侧应出现四个箭头，指示程序将立即响应操作事件。</span><span class="sxs-lookup"><span data-stu-id="f3000-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="f3000-313">将索引向下减小到拇指，并使其 pinched 在一起。</span><span class="sxs-lookup"><span data-stu-id="f3000-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="f3000-314">在四处移动手时，astronaut 也会移动（这是操作）。</span><span class="sxs-lookup"><span data-stu-id="f3000-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="f3000-315">抬起索引手指，停止操作 astronaut。</span><span class="sxs-lookup"><span data-stu-id="f3000-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="f3000-316">注意：如果在移动手前未说 "移动 Astronaut"，则将改用导航手势。</span><span class="sxs-lookup"><span data-stu-id="f3000-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="f3000-317">说 "旋转 Astronaut" 返回到 rotatable 状态。</span><span class="sxs-lookup"><span data-stu-id="f3000-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="f3000-318">第5章-模型扩展</span><span class="sxs-lookup"><span data-stu-id="f3000-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="f3000-319">目标</span><span class="sxs-lookup"><span data-stu-id="f3000-319">Objectives</span></span>

* <span data-ttu-id="f3000-320">将 Astronaut 模型扩展为用户可与之交互的多个较小的部分。</span><span class="sxs-lookup"><span data-stu-id="f3000-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="f3000-321">使用导航和操作笔势分别移动各个部分。</span><span class="sxs-lookup"><span data-stu-id="f3000-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="f3000-322">说明</span><span class="sxs-lookup"><span data-stu-id="f3000-322">Instructions</span></span>

<span data-ttu-id="f3000-323">在本部分中，我们将完成下列任务：</span><span class="sxs-lookup"><span data-stu-id="f3000-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="f3000-324">添加新的关键字 "**展开模型**"，展开 astronaut 模型。</span><span class="sxs-lookup"><span data-stu-id="f3000-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="f3000-325">添加新的关键字 "**重置模型**"，以将模型返回到其原始形式。</span><span class="sxs-lookup"><span data-stu-id="f3000-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="f3000-326">为此，我们将向上一章的语音输入源添加另外两个关键字。</span><span class="sxs-lookup"><span data-stu-id="f3000-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="f3000-327">我们还将演示另一种处理识别事件的方法。</span><span class="sxs-lookup"><span data-stu-id="f3000-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="f3000-328">在**检查器**中单击 " **AstronautManager** "，然后展开**检查器**中的 "**关键字**" 部分。</span><span class="sxs-lookup"><span data-stu-id="f3000-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="f3000-329">单击右侧的 " **+** "，添加新的关键字。</span><span class="sxs-lookup"><span data-stu-id="f3000-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="f3000-330">将关键字键入为**展开 "模型**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="f3000-331">如果需要，可以随意添加密钥快捷方式。</span><span class="sxs-lookup"><span data-stu-id="f3000-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="f3000-332">单击右侧的 " **+** "，添加新的关键字。</span><span class="sxs-lookup"><span data-stu-id="f3000-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="f3000-333">将关键字键入为 "**重置模型**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="f3000-334">如果需要，可以随意添加密钥快捷方式。</span><span class="sxs-lookup"><span data-stu-id="f3000-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="f3000-335">在**检查器**面板中，单击 "**添加组件**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="f3000-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="f3000-336">在菜单中，在 "搜索" 框中键入**语音输入处理程序**。</span><span class="sxs-lookup"><span data-stu-id="f3000-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="f3000-337">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="f3000-337">Select the search result.</span></span>
8. <span data-ttu-id="f3000-338">勾选**是全局侦听器**，因为我们希望这些命令可以正常运行，而不考虑我们的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="f3000-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="f3000-339">单击 " **+** " 按钮，然后从 "关键字" 下拉列表中选择 "**展开模型**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="f3000-340">单击 "响应" 下的 **+** ，并将 " **AstronautManager** " 从**层次结构**拖到 "**无（对象）** " 字段。</span><span class="sxs-lookup"><span data-stu-id="f3000-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="f3000-341">现在，单击 "**无函数**" 下拉列表，选择 " **AstronautManager**"，然后选择 " **ExpandModelCommand**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="f3000-342">单击语音输入处理程序的 **+** "按钮，然后从" 关键字 "下拉列表中选择"**重置模型**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="f3000-343">单击 "响应" 下的 **+** ，并将 " **AstronautManager** " 从**层次结构**拖到 "**无（对象）** " 字段。</span><span class="sxs-lookup"><span data-stu-id="f3000-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="f3000-344">现在，单击 "**无函数**" 下拉列表，选择 " **AstronautManager**"，然后选择 " **ResetModelCommand**"。</span><span class="sxs-lookup"><span data-stu-id="f3000-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![如何设置第5章的语音输入源和处理程序](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="f3000-346">生成和部署</span><span class="sxs-lookup"><span data-stu-id="f3000-346">Build and Deploy</span></span>

* <span data-ttu-id="f3000-347">试试看吧！</span><span class="sxs-lookup"><span data-stu-id="f3000-347">Try it!</span></span> <span data-ttu-id="f3000-348">生成应用并将其部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="f3000-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="f3000-349">说**展开 "模型**" 以查看扩展的 astronaut 模型。</span><span class="sxs-lookup"><span data-stu-id="f3000-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="f3000-350">使用**导航**旋转 astronaut 花色的各个部分。</span><span class="sxs-lookup"><span data-stu-id="f3000-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="f3000-351">假设**移动 Astronaut** ，然后使用**操作**来移动 Astronaut 花色的各个部分。</span><span class="sxs-lookup"><span data-stu-id="f3000-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="f3000-352">说**旋转 Astronaut**再次旋转棋子。</span><span class="sxs-lookup"><span data-stu-id="f3000-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="f3000-353">假设**Reset Model**将 astronaut 返回到其原始形式。</span><span class="sxs-lookup"><span data-stu-id="f3000-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="f3000-354">结束</span><span class="sxs-lookup"><span data-stu-id="f3000-354">The End</span></span>

<span data-ttu-id="f3000-355">恭喜你！</span><span class="sxs-lookup"><span data-stu-id="f3000-355">Congratulations!</span></span> <span data-ttu-id="f3000-356">你现在已经完成了**MR 输入211：手势**。</span><span class="sxs-lookup"><span data-stu-id="f3000-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="f3000-357">你知道如何检测和响应手动跟踪、导航和操作事件。</span><span class="sxs-lookup"><span data-stu-id="f3000-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="f3000-358">了解导航和操作笔势之间的差异。</span><span class="sxs-lookup"><span data-stu-id="f3000-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="f3000-359">你知道如何更改光标以提供有关何时检测到手、即将丢失以及何时对象支持不同交互（导航与操作）的视觉反馈。</span><span class="sxs-lookup"><span data-stu-id="f3000-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
