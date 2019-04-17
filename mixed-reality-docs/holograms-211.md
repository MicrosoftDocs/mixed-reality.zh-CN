---
title: MR 输入 211 的手势
description: 按照本演练使用 Unity、 Visual Studio 和 HoloLens 学习手势概念的详细信息进行编码操作。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit、 mixedrealitytoolkit、 mixedrealitytoolkit unity、 学院、 教程中，手势
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592683"
---
>[!NOTE]
><span data-ttu-id="501a1-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="501a1-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="501a1-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="501a1-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="501a1-106">这些教程将**_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="501a1-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="501a1-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="501a1-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="501a1-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="501a1-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="501a1-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="501a1-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="501a1-110">MR 输入 211:手势</span><span class="sxs-lookup"><span data-stu-id="501a1-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="501a1-111">[手势](gestures.md)转变为操作的用户的意图。</span><span class="sxs-lookup"><span data-stu-id="501a1-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="501a1-112">使用手势，用户可以与全息交互。</span><span class="sxs-lookup"><span data-stu-id="501a1-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="501a1-113">在本课程中，我们将了解如何跟踪用户的手、 响应用户输入，并向用户提供反馈的基于状态和位置。</span><span class="sxs-lookup"><span data-stu-id="501a1-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="501a1-114">在中[MR 基础知识 101](holograms-101.md)，我们用简单敲击手势来与我们全息交互。</span><span class="sxs-lookup"><span data-stu-id="501a1-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="501a1-115">现在，我们将以无线方式点击动作可以超越并浏览到新的概念：</span><span class="sxs-lookup"><span data-stu-id="501a1-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="501a1-116">正在跟踪用户的手时进行检测并向用户提供反馈。</span><span class="sxs-lookup"><span data-stu-id="501a1-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="501a1-117">使用导航笔势轮换我们全息。</span><span class="sxs-lookup"><span data-stu-id="501a1-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="501a1-118">当用户的手即将超出视图时，请提供反馈。</span><span class="sxs-lookup"><span data-stu-id="501a1-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="501a1-119">将使用操作事件，以便用户可以移动则用手全息。</span><span class="sxs-lookup"><span data-stu-id="501a1-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="501a1-120">在本课程中，我们将再度讨论 Unity 项目**模型资源管理器**，它我们构建[MR 输入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="501a1-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="501a1-121">我们顶级的朋友是返回到我们的探索这些新手势概念在帮助我们。</span><span class="sxs-lookup"><span data-stu-id="501a1-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="501a1-122">使用 Unity 和混合现实工具包的较旧版本记录中的以下章节每个嵌入的视频。</span><span class="sxs-lookup"><span data-stu-id="501a1-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="501a1-123">准确且最新的分步说明时，可能会看到脚本和已过期的相应视频中的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="501a1-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="501a1-124">保持为长期的视频和因为涵盖了概念仍然适用。</span><span class="sxs-lookup"><span data-stu-id="501a1-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="501a1-125">设备支持</span><span class="sxs-lookup"><span data-stu-id="501a1-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="501a1-126">课程</span><span class="sxs-lookup"><span data-stu-id="501a1-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="501a1-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="501a1-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="501a1-128"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="501a1-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="501a1-129">MR 输入 211:手势</span><span class="sxs-lookup"><span data-stu-id="501a1-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="501a1-130">✔️</span><span class="sxs-lookup"><span data-stu-id="501a1-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="501a1-131">✔️</span><span class="sxs-lookup"><span data-stu-id="501a1-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="501a1-132">开始之前</span><span class="sxs-lookup"><span data-stu-id="501a1-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="501a1-133">先决条件</span><span class="sxs-lookup"><span data-stu-id="501a1-133">Prerequisites</span></span>

* <span data-ttu-id="501a1-134">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="501a1-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="501a1-135">一些基本C#编程功能。</span><span class="sxs-lookup"><span data-stu-id="501a1-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="501a1-136">您应当已完成[MR 基础知识 101](holograms-101.md)。</span><span class="sxs-lookup"><span data-stu-id="501a1-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="501a1-137">您应当已完成[MR 输入 210](holograms-210.md)。</span><span class="sxs-lookup"><span data-stu-id="501a1-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="501a1-138">HoloLens 设备[为开发配置](using-visual-studio.md#enabling-developer-mode)。</span><span class="sxs-lookup"><span data-stu-id="501a1-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="501a1-139">项目文件</span><span class="sxs-lookup"><span data-stu-id="501a1-139">Project files</span></span>

* <span data-ttu-id="501a1-140">下载[文件](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip)所需的项目。</span><span class="sxs-lookup"><span data-stu-id="501a1-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="501a1-141"> 需要 Unity 2017.2 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="501a1-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="501a1-142">取消存档到您的桌面或其他轻松地访问位置的文件。</span><span class="sxs-lookup"><span data-stu-id="501a1-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="501a1-143">如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)。</span><span class="sxs-lookup"><span data-stu-id="501a1-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="501a1-144">勘误表和说明</span><span class="sxs-lookup"><span data-stu-id="501a1-144">Errata and Notes</span></span>

* <span data-ttu-id="501a1-145">"启用仅我的代码"必须禁用 (*未选中*) 在 Visual Studio 工具-> 选项-> 调试以便你的代码中命中断点。</span><span class="sxs-lookup"><span data-stu-id="501a1-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="501a1-146">章 0-Unity 安装程序</span><span class="sxs-lookup"><span data-stu-id="501a1-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="501a1-147">说明</span><span class="sxs-lookup"><span data-stu-id="501a1-147">Instructions</span></span>

1. <span data-ttu-id="501a1-148">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="501a1-148">Start Unity.</span></span>
2. <span data-ttu-id="501a1-149">选择**打开**。</span><span class="sxs-lookup"><span data-stu-id="501a1-149">Select **Open**.</span></span>
3. <span data-ttu-id="501a1-150">导航到**手势**文件夹你之前未存档。</span><span class="sxs-lookup"><span data-stu-id="501a1-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="501a1-151">找到并选择**起始**/**模型资源管理器**文件夹。</span><span class="sxs-lookup"><span data-stu-id="501a1-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="501a1-152">单击**选择文件夹**按钮。</span><span class="sxs-lookup"><span data-stu-id="501a1-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="501a1-153">在中**项目**面板中，展开**场景**文件夹。</span><span class="sxs-lookup"><span data-stu-id="501a1-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="501a1-154">双击**ModelExplorer**场景中，从而在 Unity 中加载它。</span><span class="sxs-lookup"><span data-stu-id="501a1-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="501a1-155">生成</span><span class="sxs-lookup"><span data-stu-id="501a1-155">Building</span></span>

1. <span data-ttu-id="501a1-156">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="501a1-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="501a1-157">如果**场景/ModelExplorer**中未列出**生成中的场景**，单击**添加打开场景**添加场景。</span><span class="sxs-lookup"><span data-stu-id="501a1-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="501a1-158">如果您专门为 HoloLens 开发，设置**目标设备**到**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="501a1-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="501a1-159">否则，将其保持打开**任何设备**。</span><span class="sxs-lookup"><span data-stu-id="501a1-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="501a1-160">请确保**生成类型**设置为**D3D**并**SDK**设置为**最新安装**（应为 16299 或更高版本的 SDK）。</span><span class="sxs-lookup"><span data-stu-id="501a1-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="501a1-161">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="501a1-161">Click **Build**.</span></span>
6. <span data-ttu-id="501a1-162">创建**新文件夹**名为"应用"。</span><span class="sxs-lookup"><span data-stu-id="501a1-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="501a1-163">单击一下**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="501a1-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="501a1-164">按**选择文件夹**和 Unity 将启动 Visual Studio 的生成项目。</span><span class="sxs-lookup"><span data-stu-id="501a1-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="501a1-165">Unity 完成操作后，将出现一个文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="501a1-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="501a1-166">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="501a1-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="501a1-167">打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="501a1-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="501a1-168">如果部署到 HoloLens:</span><span class="sxs-lookup"><span data-stu-id="501a1-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="501a1-169">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x86**。</span><span class="sxs-lookup"><span data-stu-id="501a1-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="501a1-170">单击向下箭头旁边的本地计算机按钮，然后选择**远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="501a1-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="501a1-171">输入**HoloLens 设备 IP 地址**并将身份验证模式设置为**通用 （未加密的协议）**。</span><span class="sxs-lookup"><span data-stu-id="501a1-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="501a1-172">单击**选择**。</span><span class="sxs-lookup"><span data-stu-id="501a1-172">Click **Select**.</span></span> <span data-ttu-id="501a1-173">如果不知道你设备的 IP 地址，在中查找**设置 > 网络和 Internet > 高级选项**。</span><span class="sxs-lookup"><span data-stu-id="501a1-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="501a1-174">在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="501a1-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="501a1-175">如果这是首次部署到你的设备，你将需要[与 Visual Studio 配对](using-visual-studio.md#pairing-your-device-hololens)。</span><span class="sxs-lookup"><span data-stu-id="501a1-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="501a1-176">当部署应用时，消除**Fitbox**与**选择手势**。</span><span class="sxs-lookup"><span data-stu-id="501a1-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="501a1-177">如果部署到沉浸式头戴式：</span><span class="sxs-lookup"><span data-stu-id="501a1-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="501a1-178">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **x64**。</span><span class="sxs-lookup"><span data-stu-id="501a1-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="501a1-179">请确保部署目标设置为**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="501a1-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="501a1-180">在顶部菜单栏中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="501a1-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="501a1-181">当部署应用时，消除**Fitbox**拉开运动控制器上的触发器。</span><span class="sxs-lookup"><span data-stu-id="501a1-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="501a1-182">您可能注意到 Visual Studio 错误面板中的某些红色错误。</span><span class="sxs-lookup"><span data-stu-id="501a1-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="501a1-183">它可以安全地忽略它们。</span><span class="sxs-lookup"><span data-stu-id="501a1-183">It is safe to ignore them.</span></span> <span data-ttu-id="501a1-184">切换到输出面板来查看实际生成进度。</span><span class="sxs-lookup"><span data-stu-id="501a1-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="501a1-185">输出面板中的错误将要求您的修补程序 （即最常在脚本中的错误，就会出现）。</span><span class="sxs-lookup"><span data-stu-id="501a1-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="501a1-186">第 1 章-手动检测到的反馈</span><span class="sxs-lookup"><span data-stu-id="501a1-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="501a1-187">目标</span><span class="sxs-lookup"><span data-stu-id="501a1-187">Objectives</span></span>

* <span data-ttu-id="501a1-188">移交订阅跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="501a1-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="501a1-189">使用游标反馈以向用户显示手的形状在跟踪时。</span><span class="sxs-lookup"><span data-stu-id="501a1-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="501a1-190">说明</span><span class="sxs-lookup"><span data-stu-id="501a1-190">Instructions</span></span>

* <span data-ttu-id="501a1-191">在中**层次结构**面板中，展开**InputManager**对象。</span><span class="sxs-lookup"><span data-stu-id="501a1-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="501a1-192">查找并选择**GesturesInput**对象。</span><span class="sxs-lookup"><span data-stu-id="501a1-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="501a1-193">**InteractionInputSource.cs**脚本执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="501a1-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="501a1-194">订阅的 InteractionSourceDetected 和 InteractionSourceLost 事件。</span><span class="sxs-lookup"><span data-stu-id="501a1-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="501a1-195">设置 HandDetected 状态。</span><span class="sxs-lookup"><span data-stu-id="501a1-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="501a1-196">从 InteractionSourceDetected 和 InteractionSourceLost 事件取消订阅。</span><span class="sxs-lookup"><span data-stu-id="501a1-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="501a1-197">接下来，我们将升级从我们的光标[MR 输入 210](holograms-210.md)到一个显示了具体取决于用户的操作的反馈。</span><span class="sxs-lookup"><span data-stu-id="501a1-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="501a1-198">在中**层次结构**面板中，选择**光标**对象，并将其删除。</span><span class="sxs-lookup"><span data-stu-id="501a1-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="501a1-199">在中**项目**面板中，搜索**CursorWithFeedback**将其拖到**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="501a1-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="501a1-200">单击**InputManager**中**层次结构**面板，然后拖动**CursorWithFeedback**对象**层次结构**到InputManager 的**SimpleSinglePointerSelector**的**光标**字段中，在底部**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="501a1-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="501a1-201">单击**CursorWithFeedback**中**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="501a1-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="501a1-202">在中**Inspector**面板中，展开**游标状态数据**上**对象游标**脚本。</span><span class="sxs-lookup"><span data-stu-id="501a1-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="501a1-203">**游标状态数据**工作方式类似于此：</span><span class="sxs-lookup"><span data-stu-id="501a1-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="501a1-204">任何**观察**状态意味着检测到任何现有用户只需仔细。</span><span class="sxs-lookup"><span data-stu-id="501a1-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="501a1-205">任何**Interact**状态指的手形或控制器检测到。</span><span class="sxs-lookup"><span data-stu-id="501a1-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="501a1-206">任何**将鼠标悬停在**状态意味着用户查看一张全息图。</span><span class="sxs-lookup"><span data-stu-id="501a1-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="501a1-207">生成和部署</span><span class="sxs-lookup"><span data-stu-id="501a1-207">Build and Deploy</span></span>

* <span data-ttu-id="501a1-208">在 Unity 中，使用**文件 > 生成设置**重新生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="501a1-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="501a1-209">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="501a1-209">Open the **App** folder.</span></span>
* <span data-ttu-id="501a1-210">如果尚未打开，打开**ModelExplorer Visual Studio 解决方案**。</span><span class="sxs-lookup"><span data-stu-id="501a1-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="501a1-211">（如果你已生成/部署此项目在 Visual Studio 中的在设置过程，然后您可以打开与该实例并单击全部重新加载出现提示时）。</span><span class="sxs-lookup"><span data-stu-id="501a1-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="501a1-212">在 Visual Studio 中，单击**调试-> 启动不调试**或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="501a1-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="501a1-213">在应用程序部署到 HoloLens 后，关闭使用-敲击手势 fitbox。</span><span class="sxs-lookup"><span data-stu-id="501a1-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="501a1-214">将您的手移到视图和食指指向天空启动手动跟踪。</span><span class="sxs-lookup"><span data-stu-id="501a1-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="501a1-215">向您的手左、 向右、 向上和向下。</span><span class="sxs-lookup"><span data-stu-id="501a1-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="501a1-216">观看光标时检测到您的手并将其从视图然后丢失的更改。</span><span class="sxs-lookup"><span data-stu-id="501a1-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="501a1-217">如果您在沉浸式头戴式耳机，您必须连接和断开你的控制器。</span><span class="sxs-lookup"><span data-stu-id="501a1-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="501a1-218">此反馈变得令人着迷的设备上还没那么有趣，如连接的控制器始终将"可用"。</span><span class="sxs-lookup"><span data-stu-id="501a1-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="501a1-219">第 2 章-导航</span><span class="sxs-lookup"><span data-stu-id="501a1-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="501a1-220">目标</span><span class="sxs-lookup"><span data-stu-id="501a1-220">Objectives</span></span>

* <span data-ttu-id="501a1-221">使用导航手势事件轮换顶级。</span><span class="sxs-lookup"><span data-stu-id="501a1-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="501a1-222">说明</span><span class="sxs-lookup"><span data-stu-id="501a1-222">Instructions</span></span>

<span data-ttu-id="501a1-223">若要在我们的应用程序中使用导航笔势，我们将编辑**GestureAction.cs**旋转对象时导航笔势时发生。</span><span class="sxs-lookup"><span data-stu-id="501a1-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="501a1-224">此外，我们将添加到要获得导航时显示的光标的反馈。</span><span class="sxs-lookup"><span data-stu-id="501a1-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="501a1-225">在中**层次结构**面板中，展开**CursorWithFeedback**。</span><span class="sxs-lookup"><span data-stu-id="501a1-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="501a1-226">在中**全息**文件夹中，找到**ScrollFeedback**资产。</span><span class="sxs-lookup"><span data-stu-id="501a1-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="501a1-227">拖放到**ScrollFeedback**拖动到 prefab **CursorWithFeedback**中的 GameObject**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="501a1-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="501a1-228">单击**CursorWithFeedback**。</span><span class="sxs-lookup"><span data-stu-id="501a1-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="501a1-229">在中**Inspector**面板中，单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="501a1-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="501a1-230">在菜单中，在搜索框中键入**CursorFeedback**。</span><span class="sxs-lookup"><span data-stu-id="501a1-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="501a1-231">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="501a1-231">Select the search result.</span></span>
7. <span data-ttu-id="501a1-232">拖放到**ScrollFeedback**对象从**层次结构**拖到**滚动检测到游戏对象**中的属性**光标反馈**组件**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="501a1-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="501a1-233">在中**层次结构**面板中，选择**AstroMan**对象。</span><span class="sxs-lookup"><span data-stu-id="501a1-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="501a1-234">在中**Inspector**面板中，单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="501a1-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="501a1-235">在菜单中，在搜索框中键入**手势动作**。</span><span class="sxs-lookup"><span data-stu-id="501a1-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="501a1-236">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="501a1-236">Select the search result.</span></span>

<span data-ttu-id="501a1-237">接下来，打开**GestureAction.cs** Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="501a1-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="501a1-238">在编码练习 2.c，编辑脚本以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="501a1-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="501a1-239">**旋转 AstroMan**对象执行导航笔势。</span><span class="sxs-lookup"><span data-stu-id="501a1-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="501a1-240">计算**rotationFactor**来控制应用于对象的旋转的量。</span><span class="sxs-lookup"><span data-stu-id="501a1-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="501a1-241">**旋转对象**绕 y 轴时用户将其手动移动左侧或右侧。</span><span class="sxs-lookup"><span data-stu-id="501a1-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="501a1-242">完成编码练习中的脚本或将已完成的解决方案以下代码替换为 2.c:</span><span class="sxs-lookup"><span data-stu-id="501a1-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="501a1-243">您会发现其他导航事件已填充一些信息。</span><span class="sxs-lookup"><span data-stu-id="501a1-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="501a1-244">我们将推送到该工具包的 GameObject InputSystem 的模式堆栈，因此用户无需维护专注于顶级，一旦已开始旋转。</span><span class="sxs-lookup"><span data-stu-id="501a1-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="501a1-245">相应地，我们弹出堆栈的 GameObject 手势完成。</span><span class="sxs-lookup"><span data-stu-id="501a1-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="501a1-246">生成和部署</span><span class="sxs-lookup"><span data-stu-id="501a1-246">Build and Deploy</span></span>

1. <span data-ttu-id="501a1-247">重新生成 Unity 中的应用程序然后生成并部署从 Visual Studio 在 HoloLens 中运行它。</span><span class="sxs-lookup"><span data-stu-id="501a1-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="501a1-248">注视顶级，两个箭头应显示光标的任何一侧。</span><span class="sxs-lookup"><span data-stu-id="501a1-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="501a1-249">这个新的视觉指示可以旋转顶级。</span><span class="sxs-lookup"><span data-stu-id="501a1-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="501a1-250">将您的手放在准备好的位置 （食指指向向天空） 以便 HoloLens 将开始跟踪您的手。</span><span class="sxs-lookup"><span data-stu-id="501a1-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="501a1-251">若要旋转顶级，降低到 pinch 一个位置，索引手指，然后您的手左移或右移触发 NavigationX 手势。</span><span class="sxs-lookup"><span data-stu-id="501a1-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="501a1-252">第 3 章-手指南</span><span class="sxs-lookup"><span data-stu-id="501a1-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="501a1-253">目标</span><span class="sxs-lookup"><span data-stu-id="501a1-253">Objectives</span></span>

* <span data-ttu-id="501a1-254">使用**分发指南分数**帮助预测时手动跟踪将会丢失。</span><span class="sxs-lookup"><span data-stu-id="501a1-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="501a1-255">提供**反馈对游标**以显示当用户的手接近视图的照相机的边缘。</span><span class="sxs-lookup"><span data-stu-id="501a1-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="501a1-256">说明</span><span class="sxs-lookup"><span data-stu-id="501a1-256">Instructions</span></span>

1. <span data-ttu-id="501a1-257">在中**层次结构**面板中，选择**CursorWithFeedback**对象。</span><span class="sxs-lookup"><span data-stu-id="501a1-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="501a1-258">在中**Inspector**面板中，单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="501a1-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="501a1-259">在菜单中，在搜索框中键入**手指南**。</span><span class="sxs-lookup"><span data-stu-id="501a1-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="501a1-260">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="501a1-260">Select the search result.</span></span>
4. <span data-ttu-id="501a1-261">在中**项目**面板**全息**文件夹中，找到**HandGuidanceFeedback**资产。</span><span class="sxs-lookup"><span data-stu-id="501a1-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="501a1-262">拖放到**HandGuidanceFeedback**拖动到资产**手指南指示器**中的属性**Inspector**面板。</span><span class="sxs-lookup"><span data-stu-id="501a1-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="501a1-263">生成和部署</span><span class="sxs-lookup"><span data-stu-id="501a1-263">Build and Deploy</span></span>

* <span data-ttu-id="501a1-264">重新生成 Unity 中的应用程序然后生成并从 Visual Studio 体验 HoloLens 上的应用程序部署。</span><span class="sxs-lookup"><span data-stu-id="501a1-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="501a1-265">将您的手放入视图，并引发手指索引获取跟踪。</span><span class="sxs-lookup"><span data-stu-id="501a1-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="501a1-266">开始旋转与导航笔势顶级 （捏合索引手指和拇指一起）。</span><span class="sxs-lookup"><span data-stu-id="501a1-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="501a1-267">最左侧、 右侧、，向上和向下移动您的手。</span><span class="sxs-lookup"><span data-stu-id="501a1-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="501a1-268">当您的手接近手势帧的边缘应旁边显示一个箭头光标以向您发出警告跟踪该手动将会丢失。</span><span class="sxs-lookup"><span data-stu-id="501a1-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="501a1-269">箭头指示哪个方向移动以防止丢失跟踪您的手。</span><span class="sxs-lookup"><span data-stu-id="501a1-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="501a1-270">第 4 章-操作</span><span class="sxs-lookup"><span data-stu-id="501a1-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="501a1-271">目标</span><span class="sxs-lookup"><span data-stu-id="501a1-271">Objectives</span></span>

* <span data-ttu-id="501a1-272">使用操作事件移动用手顶级。</span><span class="sxs-lookup"><span data-stu-id="501a1-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="501a1-273">若要让用户知道可以使用操作时对游标提供反馈。</span><span class="sxs-lookup"><span data-stu-id="501a1-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="501a1-274">说明</span><span class="sxs-lookup"><span data-stu-id="501a1-274">Instructions</span></span>

<span data-ttu-id="501a1-275">GestureManager.cs 和 AstronautManager.cs 将使我们可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="501a1-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="501a1-276">使用语音关键字"**移动顶级**"以启用**操作**手势和"**旋转顶级**"来禁用它们。</span><span class="sxs-lookup"><span data-stu-id="501a1-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="501a1-277">切换到响应**操作笔势识别器**。</span><span class="sxs-lookup"><span data-stu-id="501a1-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="501a1-278">让我们开始吧。</span><span class="sxs-lookup"><span data-stu-id="501a1-278">Let's get started.</span></span>

1. <span data-ttu-id="501a1-279">在中**层次结构**面板中，创建新的空 GameObject。</span><span class="sxs-lookup"><span data-stu-id="501a1-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="501a1-280">其命名为"**AstronautManager**"。</span><span class="sxs-lookup"><span data-stu-id="501a1-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="501a1-281">在中**Inspector**面板中，单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="501a1-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="501a1-282">在菜单中，在搜索框中键入**顶级 Manager**。</span><span class="sxs-lookup"><span data-stu-id="501a1-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="501a1-283">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="501a1-283">Select the search result.</span></span>
4. <span data-ttu-id="501a1-284">在中**Inspector**面板中，单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="501a1-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="501a1-285">在菜单中，在搜索框中键入**语音输入源**。</span><span class="sxs-lookup"><span data-stu-id="501a1-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="501a1-286">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="501a1-286">Select the search result.</span></span>

<span data-ttu-id="501a1-287">我们现在将添加的语音命令，来控制顶级的交互状态。</span><span class="sxs-lookup"><span data-stu-id="501a1-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="501a1-288">展开**关键字**主题中**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="501a1-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="501a1-289">单击**+** 右侧添加一个新的关键字。</span><span class="sxs-lookup"><span data-stu-id="501a1-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="501a1-290">类型为关键字**移动顶级**。</span><span class="sxs-lookup"><span data-stu-id="501a1-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="501a1-291">随时根据需要添加一个键的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="501a1-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="501a1-292">单击**+** 右侧添加一个新的关键字。</span><span class="sxs-lookup"><span data-stu-id="501a1-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="501a1-293">类型为关键字**旋转顶级**。</span><span class="sxs-lookup"><span data-stu-id="501a1-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="501a1-294">随时根据需要添加一个键的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="501a1-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="501a1-295">可在相应的处理程序代码**GestureAction.cs**，在**ISpeechHandler.OnSpeechKeywordRecognized**处理程序。</span><span class="sxs-lookup"><span data-stu-id="501a1-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![如何设置第 4 章语音输入源](images/holograms211-speech.png)

<span data-ttu-id="501a1-297">接下来，我们将设置对游标的操作反馈。</span><span class="sxs-lookup"><span data-stu-id="501a1-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="501a1-298">在中**项目**面板**全息**文件夹中，找到**PathingFeedback**资产。</span><span class="sxs-lookup"><span data-stu-id="501a1-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="501a1-299">拖放到**PathingFeedback**拖动到 prefab **CursorWithFeedback**对象中**层次结构**。</span><span class="sxs-lookup"><span data-stu-id="501a1-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="501a1-300">在中**层次结构**面板中，单击**CursorWithFeedback**。</span><span class="sxs-lookup"><span data-stu-id="501a1-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="501a1-301">拖放到**PathingFeedback**对象从**层次结构**拖到**路径检测到游戏对象**中的属性**光标反馈**组件**Inspector**。</span><span class="sxs-lookup"><span data-stu-id="501a1-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="501a1-302">现在，我们需要将代码添加到**GestureAction.cs**以实现以下：</span><span class="sxs-lookup"><span data-stu-id="501a1-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="501a1-303">将代码添加到**IManipulationHandler.OnManipulationUpdated**函数，它会将移动的顶级时**操作**检测到笔势。</span><span class="sxs-lookup"><span data-stu-id="501a1-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="501a1-304">计算**移动矢量**来确定应将顶级转移到基于现有位置。</span><span class="sxs-lookup"><span data-stu-id="501a1-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="501a1-305">**移动**顶级到新位置。</span><span class="sxs-lookup"><span data-stu-id="501a1-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="501a1-306">完成编码练习中的 4.a **GestureAction.cs**，或使用我们已完成的解决方案如下：</span><span class="sxs-lookup"><span data-stu-id="501a1-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="501a1-307">生成和部署</span><span class="sxs-lookup"><span data-stu-id="501a1-307">Build and Deploy</span></span>

* <span data-ttu-id="501a1-308">在 Unity 中重新生成然后生成并从 Visual Studio HoloLens 中运行应用程序部署。</span><span class="sxs-lookup"><span data-stu-id="501a1-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="501a1-309">移动您的手 HoloLens 的前面，并引发索引手指，以便可以跟踪。</span><span class="sxs-lookup"><span data-stu-id="501a1-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="501a1-310">通过顶级焦点光标。</span><span class="sxs-lookup"><span data-stu-id="501a1-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="501a1-311">说移动顶级移动与操作笔势顶级。</span><span class="sxs-lookup"><span data-stu-id="501a1-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="501a1-312">四个箭头光标以指示该程序将立即响应操作事件周围应显示。</span><span class="sxs-lookup"><span data-stu-id="501a1-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="501a1-313">降低食指到您的拇指，并将其挤压在一起。</span><span class="sxs-lookup"><span data-stu-id="501a1-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="501a1-314">您的手周围移动时，也会移动顶级 （这是操作）。</span><span class="sxs-lookup"><span data-stu-id="501a1-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="501a1-315">引发食指停止操作顶级。</span><span class="sxs-lookup"><span data-stu-id="501a1-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="501a1-316">注意：如果您的手再不说出移动顶级，则将改为使用导航笔势。</span><span class="sxs-lookup"><span data-stu-id="501a1-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="501a1-317">说旋转顶级以返回到可旋转的状态。</span><span class="sxs-lookup"><span data-stu-id="501a1-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="501a1-318">第 5 章-模型扩展</span><span class="sxs-lookup"><span data-stu-id="501a1-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="501a1-319">目标</span><span class="sxs-lookup"><span data-stu-id="501a1-319">Objectives</span></span>

* <span data-ttu-id="501a1-320">展开顶级模型分为多个，较小部分用户可以与交互。</span><span class="sxs-lookup"><span data-stu-id="501a1-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="501a1-321">将移动每个部分使用单独的导航和操作的笔势。</span><span class="sxs-lookup"><span data-stu-id="501a1-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="501a1-322">说明</span><span class="sxs-lookup"><span data-stu-id="501a1-322">Instructions</span></span>

<span data-ttu-id="501a1-323">在本部分中，我们将完成以下任务：</span><span class="sxs-lookup"><span data-stu-id="501a1-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="501a1-324">添加一个新的关键字"**展开模型**"以展开顶级模型。</span><span class="sxs-lookup"><span data-stu-id="501a1-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="501a1-325">添加一个新的关键字"**重置模型**"可为其原始形式返回的模型。</span><span class="sxs-lookup"><span data-stu-id="501a1-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="501a1-326">我们将通过将两个多个关键字添加到语音输入源，从上一章来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="501a1-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="501a1-327">我们还将演示另一种方法来处理识别事件。</span><span class="sxs-lookup"><span data-stu-id="501a1-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="501a1-328">单击重新**AstronautManager**中**Inspector**展开**关键字**主题中**检查器**。</span><span class="sxs-lookup"><span data-stu-id="501a1-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="501a1-329">单击**+** 右侧添加一个新的关键字。</span><span class="sxs-lookup"><span data-stu-id="501a1-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="501a1-330">类型为关键字**展开模型**。</span><span class="sxs-lookup"><span data-stu-id="501a1-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="501a1-331">随时根据需要添加一个键的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="501a1-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="501a1-332">单击**+** 右侧添加一个新的关键字。</span><span class="sxs-lookup"><span data-stu-id="501a1-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="501a1-333">类型为关键字**重置模型**。</span><span class="sxs-lookup"><span data-stu-id="501a1-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="501a1-334">随时根据需要添加一个键的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="501a1-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="501a1-335">在中**Inspector**面板中，单击**添加组件**按钮。</span><span class="sxs-lookup"><span data-stu-id="501a1-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="501a1-336">在菜单中，在搜索框中键入**语音输入处理程序**。</span><span class="sxs-lookup"><span data-stu-id="501a1-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="501a1-337">选择搜索结果。</span><span class="sxs-lookup"><span data-stu-id="501a1-337">Select the search result.</span></span>
8. <span data-ttu-id="501a1-338">检查**是全局侦听器**，因为我们希望这些命令来处理而不考虑 GameObject 中我们主要。</span><span class="sxs-lookup"><span data-stu-id="501a1-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="501a1-339">单击**+** 按钮，然后选择**展开模型**从关键字下拉列表。</span><span class="sxs-lookup"><span data-stu-id="501a1-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="501a1-340">单击**+** 下的响应，并将**AstronautManager**从**层次结构**到**None （对象）** 字段。</span><span class="sxs-lookup"><span data-stu-id="501a1-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="501a1-341">现在，单击**否函数**下拉列表中，选择**AstronautManager**，然后**ExpandModelCommand**。</span><span class="sxs-lookup"><span data-stu-id="501a1-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="501a1-342">单击语音输入处理程序的**+** 按钮，然后选择**重置模型**从关键字下拉列表。</span><span class="sxs-lookup"><span data-stu-id="501a1-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="501a1-343">单击**+** 下的响应，并将**AstronautManager**从**层次结构**到**None （对象）** 字段。</span><span class="sxs-lookup"><span data-stu-id="501a1-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="501a1-344">现在，单击**否函数**下拉列表中，选择**AstronautManager**，然后**ResetModelCommand**。</span><span class="sxs-lookup"><span data-stu-id="501a1-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![如何设置语音输入源和处理程序第 5 章](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="501a1-346">生成和部署</span><span class="sxs-lookup"><span data-stu-id="501a1-346">Build and Deploy</span></span>

* <span data-ttu-id="501a1-347">试试看吧！</span><span class="sxs-lookup"><span data-stu-id="501a1-347">Try it!</span></span> <span data-ttu-id="501a1-348">生成并将应用部署到 HoloLens。</span><span class="sxs-lookup"><span data-stu-id="501a1-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="501a1-349">说**展开模型**，查看扩展的顶级模型。</span><span class="sxs-lookup"><span data-stu-id="501a1-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="501a1-350">使用**导航**旋转的顶级花色的各个部分。</span><span class="sxs-lookup"><span data-stu-id="501a1-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="501a1-351">说**移动顶级**，然后使用**操作**移动的顶级花色的各个部分。</span><span class="sxs-lookup"><span data-stu-id="501a1-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="501a1-352">说**旋转顶级**再次旋转部分。</span><span class="sxs-lookup"><span data-stu-id="501a1-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="501a1-353">说**重置模型**以返回到其原始形式的顶级。</span><span class="sxs-lookup"><span data-stu-id="501a1-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="501a1-354">结束</span><span class="sxs-lookup"><span data-stu-id="501a1-354">The End</span></span>

<span data-ttu-id="501a1-355">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="501a1-355">Congratulations!</span></span> <span data-ttu-id="501a1-356">你现在已经完成**MR 输入 211:手势**。</span><span class="sxs-lookup"><span data-stu-id="501a1-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="501a1-357">您知道如何进行检测和响应移交跟踪、 导航和操作事件。</span><span class="sxs-lookup"><span data-stu-id="501a1-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="501a1-358">了解导航和操作手势之间的差异。</span><span class="sxs-lookup"><span data-stu-id="501a1-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="501a1-359">您知道如何进行更改会丢失，手的形状时检测到手的形状是和对象时支持不同的交互 (导航 vs 操作) 提供可视反馈的光标。</span><span class="sxs-lookup"><span data-stu-id="501a1-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
