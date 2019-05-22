---
title: MR 基础知识 100-开始使用 Unity
description: 了解如何创建第一个基本的混合的现实"你好 world"应用程序。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 混合现实，Windows Mixed Reality 开始 HoloLens，令人着迷，vr，先生，，全息图，学院，教程
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993624"
---
>[!NOTE]
><span data-ttu-id="e7cb9-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e7cb9-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e7cb9-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e7cb9-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e7cb9-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e7cb9-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="e7cb9-110">MR 基础知识 100:开始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="e7cb9-110">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="e7cb9-111">本教程将引导你完成创建使用 Unity 构建的基本混合的现实应用程序。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-111">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="e7cb9-112">设备支持</span><span class="sxs-lookup"><span data-stu-id="e7cb9-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e7cb9-113">课程</span><span class="sxs-lookup"><span data-stu-id="e7cb9-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e7cb9-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e7cb9-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e7cb9-115"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="e7cb9-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="e7cb9-116">MR 基础知识 100:开始使用 Unity</span><span class="sxs-lookup"><span data-stu-id="e7cb9-116">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="e7cb9-117">✔️</span><span class="sxs-lookup"><span data-stu-id="e7cb9-117">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e7cb9-118">✔️</span><span class="sxs-lookup"><span data-stu-id="e7cb9-118">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="e7cb9-119">系统必备</span><span class="sxs-lookup"><span data-stu-id="e7cb9-119">Prerequisites</span></span>

* <span data-ttu-id="e7cb9-120">使用正确配置 Windows 10 电脑[安装工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="e7cb9-121">第 1 章-创建新项目</span><span class="sxs-lookup"><span data-stu-id="e7cb9-121">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="e7cb9-122">若要生成使用 Unity 应用，首先需要创建一个项目。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-122">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="e7cb9-123">此项目划分为几个文件夹，其中最重要的是你的资产文件夹。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-123">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="e7cb9-124">这是包含从 Maya、 最大影院 4d 或 Photoshop，使用 Visual Studio 或你最喜欢的代码编辑器中，创建的所有代码等的数字内容创建工具导入的所有资产的文件夹和任意数量的 Unity 创建你的内容文件撰写场景动画和在编辑器中的其他 Unity 资产类型。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-124">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="e7cb9-125">若要生成和部署 UWP 应用，Unity 可以导出为 Visual Studio 解决方案将包含所有必需的资产和代码文件的项目。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-125">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="e7cb9-126">启动 Unity</span><span class="sxs-lookup"><span data-stu-id="e7cb9-126">Start Unity</span></span>
2. <span data-ttu-id="e7cb9-127">选择**新**</span><span class="sxs-lookup"><span data-stu-id="e7cb9-127">Select **New**</span></span>
3. <span data-ttu-id="e7cb9-128">输入项目名称 （例如"MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="e7cb9-128">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="e7cb9-129">输入用于保存你的项目的位置</span><span class="sxs-lookup"><span data-stu-id="e7cb9-129">Enter a location to save your project</span></span>
5. <span data-ttu-id="e7cb9-130">请确保**3D**切换处于选中状态</span><span class="sxs-lookup"><span data-stu-id="e7cb9-130">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="e7cb9-131">选择**创建项目**</span><span class="sxs-lookup"><span data-stu-id="e7cb9-131">Select **Create project**</span></span>

<span data-ttu-id="e7cb9-132">恭喜，您将所有安装程序以立即开始使用混合的现实自定义设置。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-132">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="e7cb9-133">第 2 章-安装照相机</span><span class="sxs-lookup"><span data-stu-id="e7cb9-133">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="e7cb9-134">Unity Main Camera 处理跟踪的头节点和立体呈现。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-134">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="e7cb9-135">有一些更改以进行到 Main Camera 以用于混合现实。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-135">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>
1. <span data-ttu-id="e7cb9-136">选择文件 > 新的场景</span><span class="sxs-lookup"><span data-stu-id="e7cb9-136">Select File > New Scene</span></span>

<span data-ttu-id="e7cb9-137">首先，它将是更轻松地布置您的应用程序，如果您想象为用户的起始位置 (**X**:0， **Y**:0， **Z**:0).</span><span class="sxs-lookup"><span data-stu-id="e7cb9-137">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="e7cb9-138">因为 Main Camera 正在跟踪的用户的头移动，可以通过设置 Main Camera 的起始位置设置用户的起始位置。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-138">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>
1. <span data-ttu-id="e7cb9-139">选择**Main Camera**中**层次结构**面板</span><span class="sxs-lookup"><span data-stu-id="e7cb9-139">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="e7cb9-140">在中**Inspector**面板中，找到**转换**组件，并更改**位置**从 (**X**:0， **Y**:1， **Z**:-10) 到 (**X**:0， **Y**:0， **Z**:0)</span><span class="sxs-lookup"><span data-stu-id="e7cb9-140">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="e7cb9-141">其次，默认照相机背景需要思考一下。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-141">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="e7cb9-142">**对于 HoloLens 应用程序**，实际应显示隐藏的所有内容照相机呈现时，不 Skybox 纹理。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-142">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>
1. <span data-ttu-id="e7cb9-143">与**Main Camera**仍然中选择**层次结构**面板中，找到**照相机**组件**检查器**面板和更改**清除标志**下拉列表从**Skybox**到**纯色**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-143">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="e7cb9-144">选择**背景**颜色选取器和更改**RGBA**值到 （0，0，0，0）</span><span class="sxs-lookup"><span data-stu-id="e7cb9-144">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="e7cb9-145">**对于混合的现实应用程序针对沉浸式耳机**，我们可以使用 Unity 提供了默认 Skybox 纹理。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-145">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>
1. <span data-ttu-id="e7cb9-146">与**Main Camera**仍然中选择**层次结构**面板中，找到**照相机**组件**检查器**面板和保留**清除标志**下拉列表中**Skybox**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-146">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="e7cb9-147">第三，让我们考虑在 Unity 中的剪辑近视且阻止对象被呈现太靠近用户的眼睛用户接近对象或对象接近用户。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-147">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="e7cb9-148">**对于 HoloLens 应用程序**，几乎剪裁平面可设置为[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 计量。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-148">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>
1. <span data-ttu-id="e7cb9-149">与**Main Camera**仍然中选择**层次结构**面板中，找到**照相机**组件**检查器**面板和更改**附近剪裁平面**字段从默认**0.3**到建议 HoloLens **0.85**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-149">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="e7cb9-150">**对于混合的现实应用程序针对沉浸式耳机**，我们可以使用 Unity 提供的默认设置。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-150">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>
1. <span data-ttu-id="e7cb9-151">与**Main Camera**仍然中选择**层次结构**面板中，找到**照相机**组件**检查器**面板和保留**附近剪裁平面**字段为默认值**0.3**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-151">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="e7cb9-152">最后，让我们到目前为止保存我们的进度。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-152">Finally, let us save our progress so far.</span></span> <span data-ttu-id="e7cb9-153">若要保存场景更改，请选择**文件 > 场景另存为**，命名该场景**Main**，然后选择**保存**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-153">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="e7cb9-154">第 3 章-安装程序项目设置</span><span class="sxs-lookup"><span data-stu-id="e7cb9-154">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="e7cb9-155">在本章中，我们将帮助我们一些 Unity 项目设置目标用于开发的 Windows 全息版 SDK。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-155">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="e7cb9-156">我们还将为我们的应用程序设置一些质量设置。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-156">We will also set some quality settings for our application.</span></span> <span data-ttu-id="e7cb9-157">最后，我们将确保我们生成目标设置为 Windows 应用商店。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-157">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="e7cb9-158">Unity 的性能和质量设置</span><span class="sxs-lookup"><span data-stu-id="e7cb9-158">Unity performance and quality settings</span></span>

<span data-ttu-id="e7cb9-159">**HoloLens 的 unity 质量设置**</span><span class="sxs-lookup"><span data-stu-id="e7cb9-159">**Unity quality settings for HoloLens**</span></span>

![HoloLens 的 unity 质量设置](images/qualitysettings.png) 

<span data-ttu-id="e7cb9-161">由于维护在 HoloLens 上的高帧速率是很重要，我们需要的最快的性能优化的质量设置。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-161">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="e7cb9-162">有关更多详细性能信息[Unity 的性能建议](performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-162">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>
1. <span data-ttu-id="e7cb9-163">选择**编辑 > 项目设置 > 质量**</span><span class="sxs-lookup"><span data-stu-id="e7cb9-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="e7cb9-164">选择**下拉列表中**下**Windows 应用商店**徽标，然后选择**非常低**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="e7cb9-165">您将知道当正确应用了设置 Windows 应用商店列中的框并**非常低**行都显示为绿色。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="e7cb9-166">**混合的现实针对的应用程序到封闭的像素显示**，可以将质量设置保留到其默认值。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-166">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="e7cb9-167">面向 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="e7cb9-167">Target Windows 10 SDK</span></span>

<span data-ttu-id="e7cb9-168">**目标 Windows 全息版 SDK**</span><span class="sxs-lookup"><span data-stu-id="e7cb9-168">**Target Windows Holographic SDK**</span></span>

![目标 Windows 全息版 SDK](images/xrsettings.png) 

<span data-ttu-id="e7cb9-170">我们需要让 Unity 知道我们尝试导出该应用应创建[沉浸式视图](app-views.md)而不是二维视图。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-170">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="e7cb9-171">为此，我们启用上 Unity 虚拟现实支持面向 Windows 10 SDK。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-171">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>
1. <span data-ttu-id="e7cb9-172">转到**编辑 > 项目设置 > 播放机**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-172">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="e7cb9-173">在中**检查器面板**对于播放机设置，选择**Windows 应用商店**图标。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-173">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="e7cb9-174">展开**XR 设置**组。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-174">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="e7cb9-175">在中**呈现**部分中，选择**受支持的虚拟现实**复选框以添加新**虚拟现实 Sdk**列表。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-175">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="e7cb9-176">确认**Windows Mixed Reality**出现在列表中。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-176">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="e7cb9-177">如果没有，请选择 **+** 按钮在列表的底部，然后选择**Windows Mixed Reality**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-177">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="e7cb9-178">如果没有看到**Windows 应用商店**图标，仔细检查以确保选择 Windows 应用商店.NET 脚本编写后端之前安装。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-178">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="e7cb9-179">否则，可能需要使用正确的 Windows 安装重新安装 Unity。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-179">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="e7cb9-180">**验证.NET 配置**</span><span class="sxs-lookup"><span data-stu-id="e7cb9-180">**Verify .NET Configuration**</span></span>

![验证.NET 配置](images/configoptions-375px.png)

1. <span data-ttu-id="e7cb9-182">转到**编辑 > 项目设置 > 播放机**（你可能仍需要这从上一步）。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-182">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="e7cb9-183">在中**检查器面板**对于播放机设置，选择**Windows 应用商店**图标。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-183">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="e7cb9-184">在中**其他设置**配置部分中，请确保**脚本编写后端**设置为 **.NET**</span><span class="sxs-lookup"><span data-stu-id="e7cb9-184">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="e7cb9-185">获取应用的所有项目设置的太好了作业。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-185">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="e7cb9-186">接下来，让我们添加一张全息图 ！</span><span class="sxs-lookup"><span data-stu-id="e7cb9-186">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="e7cb9-187">章 4-创建多维数据集</span><span class="sxs-lookup"><span data-stu-id="e7cb9-187">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="e7cb9-188">在 Unity 项目中创建多维数据集就像在 Unity 中创建任何其他对象。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-188">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="e7cb9-189">将用户的多维数据集非常简单，因为 Unity 的坐标系统映射到实际的其中一个指示器在 Unity 中是大约一米现实世界中。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-189">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>
1. <span data-ttu-id="e7cb9-190">中的左上角**层次结构**面板中，选择**创建**下拉列表中选择**三维对象 > 多维数据集**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-190">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="e7cb9-191">选择新建**多维数据集**中**层次结构**面板</span><span class="sxs-lookup"><span data-stu-id="e7cb9-191">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="e7cb9-192">在中**Inspector**查找**转换**组件，并更改**位置**到 (**X**:0， **Y**:0， **Z**:2).</span><span class="sxs-lookup"><span data-stu-id="e7cb9-192">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="e7cb9-193">*此选项会将该多维数据集 2 米定位用户的起始位置的前面。*</span><span class="sxs-lookup"><span data-stu-id="e7cb9-193">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="e7cb9-194">在中**转换**组件，更改**旋转**到 (**X**:45 **Y**:45 **Z**:45） 和更改**规模**到 (**X**:0.25， **Y**:0.25， **Z**:0.25).</span><span class="sxs-lookup"><span data-stu-id="e7cb9-194">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="e7cb9-195">*这会缩放至 0.25 米多维数据集。*</span><span class="sxs-lookup"><span data-stu-id="e7cb9-195">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="e7cb9-196">若要保存场景更改，请选择**文件 > 保存场景**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-196">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="e7cb9-197">章节 5-验证在设备上从 Unity 编辑器</span><span class="sxs-lookup"><span data-stu-id="e7cb9-197">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="e7cb9-198">现在，我们创建了我们的多维数据集，就可以执行一个快速检查设备中。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-198">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="e7cb9-199">你可以直接从 Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-199">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="e7cb9-200">初始设置</span><span class="sxs-lookup"><span data-stu-id="e7cb9-200">Initial setup</span></span>
1. <span data-ttu-id="e7cb9-201">在您的开发 PC 上，在 Unity 中，打开**文件 > 生成设置**窗口。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-201">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="e7cb9-202">更改**平台**到**通用 Windows 平台**单击**交换机平台**</span><span class="sxs-lookup"><span data-stu-id="e7cb9-202">Change **Platform** to **Universal Windows Platform** and click **Switch Platfrom**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="e7cb9-203">对于 HoloLens 使用 Unity 远程处理</span><span class="sxs-lookup"><span data-stu-id="e7cb9-203">For HoloLens use Unity Remoting</span></span>
1. <span data-ttu-id="e7cb9-204">在你 HoloLens 上安装并运行[Holographic 远程处理的播放机](holographic-remoting-player.md)，可从 Windows 应用商店。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-204">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="e7cb9-205">启动应用程序在设备上，并且它将进入等待状态，并显示设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-205">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="e7cb9-206">请记下 IP。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-206">Note down the IP.</span></span>
2. <span data-ttu-id="e7cb9-207">打开**窗口 > XR > Holographic 仿真**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-207">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="e7cb9-208">更改**仿真模式**从**None**到**远程连接到设备**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-208">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="e7cb9-209">在中**远程计算机**，输入前面记下你 HoloLens 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-209">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="e7cb9-210">单击“连接”。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-210">Click **Connect**.</span></span>
6. <span data-ttu-id="e7cb9-211">请确保**连接状态**更改为绿色**已连接**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-211">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="e7cb9-212">现在，你现在可以单击**播放**Unity 编辑器中。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-212">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="e7cb9-213">现在，你将能够看到在设备和在编辑器中的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-213">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="e7cb9-214">可以暂停、 检查对象，并调试就像在编辑器中，运行应用，因为这实质上是发生什么情况，但与视频、 音频和通过网络在主机计算机和设备之间来回传输设备输入。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-214">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="e7cb9-215">对于其他混合现实支持耳机</span><span class="sxs-lookup"><span data-stu-id="e7cb9-215">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="e7cb9-216">将耳机连接到开发电脑使用 USB 电缆和 HDMI 或显示端口电缆。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-216">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="e7cb9-217">启动**混合现实门户**，并确保已完成第一次运行的体验。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-217">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="e7cb9-218">从 Unity 中，现在可以按播放按钮。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-218">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="e7cb9-219">现在，您将能够看到在混合的现实耳机，并在编辑器中的多维数据集呈现。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-219">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="e7cb9-220">第 6-章生成，并从 Visual Studio 部署到设备</span><span class="sxs-lookup"><span data-stu-id="e7cb9-220">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="e7cb9-221">现在我们就可以编译到 Visual Studio 项目并将其部署到我们的目标设备。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-221">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="e7cb9-222">将导出到 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="e7cb9-222">Export to the Visual Studio solution</span></span>
1.  <span data-ttu-id="e7cb9-223">打开**文件 > 生成设置**窗口。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-223">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="e7cb9-224">单击**添加打开场景**添加场景。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-224">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="e7cb9-225">更改**平台**到**通用 Windows 平台**然后单击**切换平台**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-225">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="e7cb9-226">在中**Windows 应用商店**确保设置，请**SDK**是**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-226">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="e7cb9-227">对于目标设备，请保留**任一设备**封闭的像素显示或切换到**HoloLens**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-227">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="e7cb9-228">**UWP 生成类型**应**D3D**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-228">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="e7cb9-229">**UWP SDK**无法将其保留为**最新安装**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-229">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="e7cb9-230">检查**UnityC#项目**在调试下。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-230">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="e7cb9-231">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-231">Click **Build**.</span></span>
10. <span data-ttu-id="e7cb9-232">在文件资源管理器，单击**新文件夹**，然后将文件夹 **"应用"**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-232">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="e7cb9-233">与**应用程序**文件夹选择，单击**选择文件夹**按钮。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-233">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="e7cb9-234">当完成 Unity 构建，将出现一个 Windows 文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-234">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="e7cb9-235">打开**应用**文件夹在文件资源管理器。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-235">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="e7cb9-236">打开生成的 Visual Studio 解决方案 (在此示例中 MixedRealityIntroduction.sln)</span><span class="sxs-lookup"><span data-stu-id="e7cb9-236">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="e7cb9-237">编译的 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="e7cb9-237">Compile the Visual Studio solution</span></span>

<span data-ttu-id="e7cb9-238">最后，我们将编译导出 Visual Studio 解决方案，部署方式，并在设备上进行试用。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-238">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>
1. <span data-ttu-id="e7cb9-239">在 Visual Studio 中，使用顶部的工具栏更改从目标**调试**到**发行**来回**ARM**到**X86**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-239">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="e7cb9-240">对于部署到仿真程序与设备不同的说明。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-240">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="e7cb9-241">按照与你的设置相匹配的说明。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-241">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="e7cb9-242">通过 Wi-fi 将部署到混合的现实设备</span><span class="sxs-lookup"><span data-stu-id="e7cb9-242">Deploy to mixed reality device over Wi-Fi</span></span>
1. <span data-ttu-id="e7cb9-243">旁边的箭头上单击**本地计算机**按钮，然后更改到部署目标**远程计算机**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-243">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="e7cb9-244">输入你的混合的现实设备的 IP 地址并将更改**身份验证模式**为通用 （未加密的协议） 的 HoloLens 和**Windows**为其他设备。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-244">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="e7cb9-245">单击**调试 > 启动但不调试**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-245">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="e7cb9-246">**对于 HoloLens**，如果这是首次部署到你的设备，你将需要对[使用 Visual Studio](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-246">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="e7cb9-247">通过 USB 将部署到混合的现实设备</span><span class="sxs-lookup"><span data-stu-id="e7cb9-247">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="e7cb9-248">请确保在通过 USB 电缆插入您的设备。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-248">Ensure you device is plugged in via the USB cable.</span></span>
1. <span data-ttu-id="e7cb9-249">**对于 HoloLens**，单击旁边的箭头**本地计算机**按钮，并更改部署到目标**设备**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-249">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="e7cb9-250">**针对连接到您的 PC 的封闭的像素设备**，保留到本地计算机的设置。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-250">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="e7cb9-251">请确保您具有**混合现实门户**运行。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-251">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="e7cb9-252">单击**调试 > 启动但不调试**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-252">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="e7cb9-253">将部署到仿真程序</span><span class="sxs-lookup"><span data-stu-id="e7cb9-253">Deploy to Emulator</span></span>
1. <span data-ttu-id="e7cb9-254">旁边的箭头上单击**设备**按钮，并从下拉列表中，选择**HoloLens 模拟器**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-254">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="e7cb9-255">单击**调试 > 启动但不调试**。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-255">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="e7cb9-256">试用您的应用程序</span><span class="sxs-lookup"><span data-stu-id="e7cb9-256">Try out your app</span></span>

<span data-ttu-id="e7cb9-257">现在，部署您的应用程序，尝试移动各地多维数据集并观察它保持在准备好世界中。</span><span class="sxs-lookup"><span data-stu-id="e7cb9-257">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7cb9-258">请参阅</span><span class="sxs-lookup"><span data-stu-id="e7cb9-258">See also</span></span>
* [<span data-ttu-id="e7cb9-259">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="e7cb9-259">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="e7cb9-260">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="e7cb9-260">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="e7cb9-261">MR 基础知识 101</span><span class="sxs-lookup"><span data-stu-id="e7cb9-261">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="e7cb9-262">MR 基础知识 101E</span><span class="sxs-lookup"><span data-stu-id="e7cb9-262">MR Basics 101E</span></span>](holograms-101e.md)
