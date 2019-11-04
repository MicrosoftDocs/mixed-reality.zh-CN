---
title: MR 要点 100-Unity 入门
description: 了解如何创建第一个基本的混合现实的 "hello world" 应用程序。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 混合现实，Windows Mixed Reality，HoloLens，沉浸，，vr，先生，入门，全息影像，学院，教程
ms.openlocfilehash: 5e9a90af6b80333addbde2a2e11086372483b7c3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434774"
---
>[!NOTE]
><span data-ttu-id="7ef58-104">混合现实学院教程的设计附带了 HoloLens （第一代）和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="7ef58-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7ef58-105">因此，对于那些仍在寻找为这些设备进行开发的指导的开发人员来说，我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="7ef58-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7ef58-106">这些教程将 **_不_** 会使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="7ef58-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7ef58-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="7ef58-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7ef58-108">为 HoloLens 2 发布了[一系列新教程](mrlearning-base.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef58-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="7ef58-109">MR 要点100： Unity 入门</span><span class="sxs-lookup"><span data-stu-id="7ef58-109">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="7ef58-110">本教程将指导你创建使用 Unity 构建的基本混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="7ef58-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="7ef58-111">设备支持</span><span class="sxs-lookup"><span data-stu-id="7ef58-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7ef58-112">摘要</span><span class="sxs-lookup"><span data-stu-id="7ef58-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7ef58-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7ef58-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7ef58-114"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="7ef58-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="7ef58-115">MR 要点100： Unity 入门</span><span class="sxs-lookup"><span data-stu-id="7ef58-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="7ef58-116">✔️</span><span class="sxs-lookup"><span data-stu-id="7ef58-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7ef58-117">✔️</span><span class="sxs-lookup"><span data-stu-id="7ef58-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="7ef58-118">必备条件</span><span class="sxs-lookup"><span data-stu-id="7ef58-118">Prerequisites</span></span>

* <span data-ttu-id="7ef58-119">配置了正确[工具](install-the-tools.md)的 WINDOWS 10 电脑。</span><span class="sxs-lookup"><span data-stu-id="7ef58-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="7ef58-120">第1章-创建新项目</span><span class="sxs-lookup"><span data-stu-id="7ef58-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="7ef58-121">若要使用 Unity 构建应用，首先需要创建一个项目。</span><span class="sxs-lookup"><span data-stu-id="7ef58-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="7ef58-122">此项目组织为多个文件夹，其中最重要的文件夹是 "资产" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="7ef58-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="7ef58-123">此文件夹包含从数字内容创建工具（如 Maya、最大电影院4D 或 Photoshop）中导入的所有资产、你用 Visual Studio 创建的所有代码或你最喜欢的代码编辑器，以及当你编写场景时 Unity 创建的任意数量的内容文件、动画和其他 Unity 资产类型。</span><span class="sxs-lookup"><span data-stu-id="7ef58-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="7ef58-124">若要生成和部署 UWP 应用，Unity 可将项目导出为 Visual Studio 解决方案，该解决方案将包含所有必需的资产和代码文件。</span><span class="sxs-lookup"><span data-stu-id="7ef58-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="7ef58-125">启动 Unity</span><span class="sxs-lookup"><span data-stu-id="7ef58-125">Start Unity</span></span>
2. <span data-ttu-id="7ef58-126">选择**新**</span><span class="sxs-lookup"><span data-stu-id="7ef58-126">Select **New**</span></span>
3. <span data-ttu-id="7ef58-127">输入项目名称（例如 "MixedRealityIntroduction"）</span><span class="sxs-lookup"><span data-stu-id="7ef58-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="7ef58-128">输入用于保存项目的位置</span><span class="sxs-lookup"><span data-stu-id="7ef58-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="7ef58-129">确保选择了**3d**切换</span><span class="sxs-lookup"><span data-stu-id="7ef58-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="7ef58-130">选择 "**创建项目**"</span><span class="sxs-lookup"><span data-stu-id="7ef58-130">Select **Create project**</span></span>

<span data-ttu-id="7ef58-131">恭喜，你可以立即开始进行混合现实自定义。</span><span class="sxs-lookup"><span data-stu-id="7ef58-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="7ef58-132">第2章-设置照相机</span><span class="sxs-lookup"><span data-stu-id="7ef58-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="7ef58-133">Unity 摄像机处理头跟踪和 stereoscopic 呈现。</span><span class="sxs-lookup"><span data-stu-id="7ef58-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="7ef58-134">需要对主摄像机进行一些更改，以将其用于混合现实。</span><span class="sxs-lookup"><span data-stu-id="7ef58-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="7ef58-135">选择文件 > 新建场景</span><span class="sxs-lookup"><span data-stu-id="7ef58-135">Select File > New Scene</span></span>

<span data-ttu-id="7ef58-136">首先，如果您将用户的起始位置想像为（**X**：0， **Y**：0， **Z**：0），则可以更容易地对应用程序进行布局。</span><span class="sxs-lookup"><span data-stu-id="7ef58-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="7ef58-137">由于摄像机正在跟踪用户的头移动，因此可以通过设置主摄像机的开始位置来设置用户的起始位置。</span><span class="sxs-lookup"><span data-stu-id="7ef58-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="7ef58-138">选择 "**层次结构**" 面板中的 "**主相机**"</span><span class="sxs-lookup"><span data-stu-id="7ef58-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="7ef58-139">在**检查器**面板中，找到**转换**组件，并将**位置**（**x**：0， **Y**：1， **Z**：-10）更改为（**x**：0， **Y**：0， **Z**：0）</span><span class="sxs-lookup"><span data-stu-id="7ef58-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="7ef58-140">其次，默认相机背景需要一些想法。</span><span class="sxs-lookup"><span data-stu-id="7ef58-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="7ef58-141">**对于 HoloLens 应用程序**，实际情况应该出现在照相机呈现的所有内容上，而不是 Skybox 的纹理。</span><span class="sxs-lookup"><span data-stu-id="7ef58-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="7ef58-142">在 "**层次结构**" 面板中，在 "层次结构" 面板中**选择 "相机** **" 组件，并将 "** **清除标志**" 下拉列表**从 "** **Skybox** " 更改为 "**纯色**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="7ef58-143">选择**背景**色选取器并将**RGBA**值更改为（0，0，0，0）</span><span class="sxs-lookup"><span data-stu-id="7ef58-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="7ef58-144">**对于以沉浸式耳机为目标的混合现实应用程序**，我们可以使用 Unity 提供的默认 Skybox 纹理。</span><span class="sxs-lookup"><span data-stu-id="7ef58-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="7ef58-145">在 "**层次结构**" 面板中选择了**主相机**后，在 "**检查器**" 面板中查找**相机**组件，并将 "**清除标志**" 下拉列表保留为 " **Skybox**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="7ef58-146">第三，让我们在 Unity 中考虑近剪裁平面，并防止用户在用户接近对象或对象时向用户眼睛呈现对象。</span><span class="sxs-lookup"><span data-stu-id="7ef58-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="7ef58-147">**对于 hololens 应用程序**，near 剪辑平面可以设置为[HoloLens 建议](camera-in-unity.md#clip-planes)0.85 米。</span><span class="sxs-lookup"><span data-stu-id="7ef58-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="7ef58-148">在 "**层次结构**" 面板中选择了**主相机**后，请在 "**检查器**" 面板中找到**照相机**组件，并将 "**附近的剪辑平面**" 字段从默认的**0.3**更改为**0.85 "** .</span><span class="sxs-lookup"><span data-stu-id="7ef58-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="7ef58-149">**对于以沉浸式耳机为目标的混合现实应用程序**，可以使用 Unity 提供的默认设置。</span><span class="sxs-lookup"><span data-stu-id="7ef58-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="7ef58-150">如果仍在 "**层次结构**" 面板中选择了**主相机**，请在 "**检查器**" 面板中查找**相机**组件，并将 "**近处剪裁飞机**" 字段保留为默认值**0.3**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="7ef58-151">最后，让我们来保存迄今为止的进度。</span><span class="sxs-lookup"><span data-stu-id="7ef58-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="7ef58-152">若要保存场景更改，请选择 "**文件" > "将场景另存为**"，为场景**主**命名，然后选择 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="7ef58-153">第3章-设置项目设置</span><span class="sxs-lookup"><span data-stu-id="7ef58-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="7ef58-154">在本章中，我们将设置一些 Unity 项目设置，这些设置可帮助我们面向 Windows 全息 SDK 进行开发。</span><span class="sxs-lookup"><span data-stu-id="7ef58-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="7ef58-155">我们还将设置应用程序的质量设置。</span><span class="sxs-lookup"><span data-stu-id="7ef58-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="7ef58-156">最后，我们将确保生成目标设置为 Windows 应用商店。</span><span class="sxs-lookup"><span data-stu-id="7ef58-156">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="7ef58-157">Unity 性能和质量设置</span><span class="sxs-lookup"><span data-stu-id="7ef58-157">Unity performance and quality settings</span></span>

<span data-ttu-id="7ef58-158">**HoloLens 的 Unity 质量设置**</span><span class="sxs-lookup"><span data-stu-id="7ef58-158">**Unity quality settings for HoloLens**</span></span>

![HoloLens 的 Unity 质量设置](images/qualitysettings.png)

<span data-ttu-id="7ef58-160">由于在 HoloLens 上维护高的帧率非常重要，因此我们希望优化质量设置以实现最高性能。</span><span class="sxs-lookup"><span data-stu-id="7ef58-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="7ef58-161">有关性能的详细信息，请查看[Unity 的性能建议](performance-recommendations-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef58-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="7ef58-162">选择 "**编辑 > 项目设置 > 质量**"</span><span class="sxs-lookup"><span data-stu-id="7ef58-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="7ef58-163">选择**Windows 应用商店**徽标下的**下拉列表**，并选择 "**非常低**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-163">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="7ef58-164">如果 Windows 应用商店列和**极低**的行中的框为绿色，则会知道设置正确应用。</span><span class="sxs-lookup"><span data-stu-id="7ef58-164">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="7ef58-165">**对于目标为封闭像素的混合现实应用程序**，你可以将质量设置保留为其默认值。</span><span class="sxs-lookup"><span data-stu-id="7ef58-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="7ef58-166">面向 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="7ef58-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="7ef58-167">**面向 Windows 全息 SDK**</span><span class="sxs-lookup"><span data-stu-id="7ef58-167">**Target Windows Holographic SDK**</span></span>

![面向 Windows 全息 SDK](images/xrsettings.png)

<span data-ttu-id="7ef58-169">我们需要让 Unity 知道我们要导出的应用程序应创建[沉浸式视图](app-views.md)而不是2d 视图。</span><span class="sxs-lookup"><span data-stu-id="7ef58-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="7ef58-170">为此，我们将在针对 Windows 10 SDK 的 Unity 上启用虚拟现实支持。</span><span class="sxs-lookup"><span data-stu-id="7ef58-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="7ef58-171">请参阅 "**编辑 > 项目设置" > Player**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="7ef58-172">在 "播放器设置" 的**检查器面板**中，选择 " **Windows 应用商店**" 图标。</span><span class="sxs-lookup"><span data-stu-id="7ef58-172">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="7ef58-173">展开 " **XR 设置**" 组。</span><span class="sxs-lookup"><span data-stu-id="7ef58-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="7ef58-174">在 "**呈现**" 部分中，选中 "**支持虚拟现实**" 复选框，以添加新的**虚拟现实 sdk**列表。</span><span class="sxs-lookup"><span data-stu-id="7ef58-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="7ef58-175">验证 " **Windows Mixed Reality** " 是否显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="7ef58-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="7ef58-176">如果没有，请选择列表底部的 " **+** " 按钮，然后选择 " **Windows Mixed Reality**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="7ef58-177">如果看不到**Windows 应用商店**图标，请仔细检查以确保在安装之前选择了 Windows 应用商店 .Net 脚本后端。</span><span class="sxs-lookup"><span data-stu-id="7ef58-177">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="7ef58-178">否则，可能需要重新安装具有正确 Windows 安装的 Unity。</span><span class="sxs-lookup"><span data-stu-id="7ef58-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="7ef58-179">**验证 .NET 配置**</span><span class="sxs-lookup"><span data-stu-id="7ef58-179">**Verify .NET Configuration**</span></span>

![验证 .NET 配置](images/configoptions-375px.png)

1. <span data-ttu-id="7ef58-181">请参阅 "**编辑 > 项目设置" > Player** "（你可能仍然从上一步开始）。</span><span class="sxs-lookup"><span data-stu-id="7ef58-181">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="7ef58-182">在 "播放器设置" 的**检查器面板**中，选择 " **Windows 应用商店**" 图标。</span><span class="sxs-lookup"><span data-stu-id="7ef58-182">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="7ef58-183">在 "**其他设置**" "配置" 部分中，确保 "**脚本后端**" 设置为 " **.net** "</span><span class="sxs-lookup"><span data-stu-id="7ef58-183">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="7ef58-184">获取应用了所有项目设置的出色作业。</span><span class="sxs-lookup"><span data-stu-id="7ef58-184">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="7ef58-185">接下来，让我们添加全息影像！</span><span class="sxs-lookup"><span data-stu-id="7ef58-185">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="7ef58-186">第4章-创建多维数据集</span><span class="sxs-lookup"><span data-stu-id="7ef58-186">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="7ef58-187">在 Unity 项目中创建多维数据集类似于在 Unity 中创建任何其他对象。</span><span class="sxs-lookup"><span data-stu-id="7ef58-187">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="7ef58-188">将多维数据集放在用户前面非常简单，因为 Unity 的坐标系统会映射到现实世界-其中，Unity 中的一种指示器约为现实中的一个计量。</span><span class="sxs-lookup"><span data-stu-id="7ef58-188">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="7ef58-189">在**层次结构**面板的左上角，选择 "**创建**" 下拉列表，然后选择 " **3D 对象 > 多维数据集**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-189">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="7ef58-190">在 "**层次结构**" 面板中选择新创建的**多维数据集**</span><span class="sxs-lookup"><span data-stu-id="7ef58-190">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="7ef58-191">在**检查器**中查找**转换**组件，并**将位置**更改为（**X**：0， **Y**：0， **Z**：2）。</span><span class="sxs-lookup"><span data-stu-id="7ef58-191">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="7ef58-192">*这会将 cube 2 计量置于用户的起始位置之前。*</span><span class="sxs-lookup"><span data-stu-id="7ef58-192">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="7ef58-193">在**转换**组件中，将**旋转**更改为 **（x**：45， **Y**：45， **Z**：45），将**刻度**更改为（**x**：0.25， **Y**：0.25， **Z**：0.25）。</span><span class="sxs-lookup"><span data-stu-id="7ef58-193">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="7ef58-194">*这会将多维数据集缩放到0.25 米。*</span><span class="sxs-lookup"><span data-stu-id="7ef58-194">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="7ef58-195">若要保存场景更改，请选择 "**文件" > 保存场景**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-195">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="7ef58-196">第5章-从 Unity 编辑器验证设备</span><span class="sxs-lookup"><span data-stu-id="7ef58-196">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="7ef58-197">现在，我们已经创建了多维数据集，可以在设备中快速完成检查了。</span><span class="sxs-lookup"><span data-stu-id="7ef58-197">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="7ef58-198">可以直接从 Unity 编辑器中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="7ef58-198">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="7ef58-199">初始设置</span><span class="sxs-lookup"><span data-stu-id="7ef58-199">Initial setup</span></span>

1. <span data-ttu-id="7ef58-200">在开发 PC 的 Unity 中，打开 "**文件 > 生成设置**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="7ef58-200">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="7ef58-201">将**平台**更改为 "**通用 Windows 平台**"，然后单击 "**切换 platfrom.details.heap.alignedallocate** "</span><span class="sxs-lookup"><span data-stu-id="7ef58-201">Change **Platform** to **Universal Windows Platform** and click **Switch Platfrom**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="7ef58-202">对于 HoloLens，使用 Unity 远程处理</span><span class="sxs-lookup"><span data-stu-id="7ef58-202">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="7ef58-203">在 HoloLens 上，安装并运行 Windows 应用商店提供的[全息远程处理播放器](holographic-remoting-player.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef58-203">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="7ef58-204">在设备上启动应用程序，该应用程序将进入等待状态并显示设备的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="7ef58-204">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="7ef58-205">记下 IP。</span><span class="sxs-lookup"><span data-stu-id="7ef58-205">Note down the IP.</span></span>
2. <span data-ttu-id="7ef58-206">**> 全息仿真打开 > XR 的窗口**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-206">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="7ef58-207">将**仿真模式**从**None**更改为**远程到设备**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-207">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="7ef58-208">在**远程计算机**上，输入你之前记下的 HOLOLENS 的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="7ef58-208">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="7ef58-209">单击**连接**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-209">Click **Connect**.</span></span>
6. <span data-ttu-id="7ef58-210">确保**连接状态**更改为 "**已连接**绿色"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-210">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="7ef58-211">现在，你可以在 Unity 编辑器中单击 "**播放**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-211">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="7ef58-212">现在，可以在设备和编辑器中查看多维数据集。</span><span class="sxs-lookup"><span data-stu-id="7ef58-212">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="7ef58-213">您可以暂停、检查对象和调试，就像您在编辑器中运行应用一样，因为这实质上是发生的事情，但使用视频、音频和设备输入通过网络在主机和设备之间来回传输。</span><span class="sxs-lookup"><span data-stu-id="7ef58-213">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="7ef58-214">适用于其他混合现实支持的耳机</span><span class="sxs-lookup"><span data-stu-id="7ef58-214">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="7ef58-215">使用 USB 电缆和 HDMI 或显示器端口电缆将耳机连接到开发 PC。</span><span class="sxs-lookup"><span data-stu-id="7ef58-215">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="7ef58-216">启动**混合现实门户**并确保已完成首次运行体验。</span><span class="sxs-lookup"><span data-stu-id="7ef58-216">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="7ef58-217">现在，可以从 Unity 按下 "播放" 按钮。</span><span class="sxs-lookup"><span data-stu-id="7ef58-217">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="7ef58-218">现在，你将能够在混合现实耳机和编辑器中看到多维数据集呈现。</span><span class="sxs-lookup"><span data-stu-id="7ef58-218">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="7ef58-219">第6章-从 Visual Studio 生成并部署到设备</span><span class="sxs-lookup"><span data-stu-id="7ef58-219">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="7ef58-220">现在，我们已准备好将项目编译到 Visual Studio 并部署到我们的目标设备。</span><span class="sxs-lookup"><span data-stu-id="7ef58-220">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="7ef58-221">导出到 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="7ef58-221">Export to the Visual Studio solution</span></span>

1.  <span data-ttu-id="7ef58-222">打开**文件 > 生成设置**"窗口。</span><span class="sxs-lookup"><span data-stu-id="7ef58-222">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="7ef58-223">单击 "**添加打开的场景**" 添加场景。</span><span class="sxs-lookup"><span data-stu-id="7ef58-223">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="7ef58-224">将**平台**更改为 "**通用 Windows 平台**"，然后单击 "**切换平台**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-224">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="7ef58-225">在**Windows 应用商店**设置中，请确保**SDK**为**通用 10**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-225">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="7ef58-226">对于 "目标设备"，请将封闭像素的**任何设备**保留为 "显示" 或 "切换到**HoloLens**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-226">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="7ef58-227">**UWP 生成类型**应为**D3D**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-227">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="7ef58-228">**UWP SDK**可以保持**最新安装的版本**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-228">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="7ef58-229">检查正在调试的**Unity C#项目**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-229">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="7ef58-230">单击**生成**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-230">Click **Build**.</span></span>
10. <span data-ttu-id="7ef58-231">在文件资源管理器中，单击 "**新建文件夹**"，然后将文件夹命名为 **"App"** 。</span><span class="sxs-lookup"><span data-stu-id="7ef58-231">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="7ef58-232">选择**应用**文件夹后，单击 "**选择文件夹**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="7ef58-232">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="7ef58-233">当 Unity 完成生成后，将显示一个 Windows 文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="7ef58-233">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="7ef58-234">在文件资源管理器中打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="7ef58-234">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="7ef58-235">打开生成的 Visual Studio 解决方案（在本示例中为 MixedRealityIntroduction）</span><span class="sxs-lookup"><span data-stu-id="7ef58-235">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="7ef58-236">编译 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="7ef58-236">Compile the Visual Studio solution</span></span>

<span data-ttu-id="7ef58-237">最后，我们将编译导出的 Visual Studio 解决方案，对其进行部署，然后在设备上试用。</span><span class="sxs-lookup"><span data-stu-id="7ef58-237">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="7ef58-238">使用 Visual Studio 中的顶部工具栏，将目标从 "**调试**" 更改为 "**发布**"，将 "从**ARM** " 更改为 " **X86**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-238">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="7ef58-239">有关部署到设备与模拟器的说明有所不同。</span><span class="sxs-lookup"><span data-stu-id="7ef58-239">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="7ef58-240">按照与你的设置相匹配的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7ef58-240">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="7ef58-241">通过 Wi-fi 部署到混合现实设备</span><span class="sxs-lookup"><span data-stu-id="7ef58-241">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="7ef58-242">单击 "**本地计算机**" 按钮旁边的箭头，将部署目标更改为 "**远程计算机**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-242">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="7ef58-243">输入混合现实设备的 IP 地址，并将 "**身份验证模式**" 更改为 "适用于 HoloLens 的通用（未加密的协议）" 和 " **Windows** " 作为其他设备。</span><span class="sxs-lookup"><span data-stu-id="7ef58-243">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="7ef58-244">单击 "**调试" > "开始（不调试**）"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-244">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="7ef58-245">**对于 HoloLens**，如果这是首次部署到设备，则需要[使用 Visual Studio](using-visual-studio.md)进行配对。</span><span class="sxs-lookup"><span data-stu-id="7ef58-245">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="7ef58-246">通过 USB 部署到混合现实设备</span><span class="sxs-lookup"><span data-stu-id="7ef58-246">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="7ef58-247">确保设备通过 USB 电缆接通电源。</span><span class="sxs-lookup"><span data-stu-id="7ef58-247">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="7ef58-248">**对于 HoloLens**，单击 "**本地计算机**" 按钮旁边的箭头，然后将 "部署目标" 更改为 "**设备**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-248">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="7ef58-249">**对于连接到电脑的封闭像素设备**，请将设置保留为 "本地计算机"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-249">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="7ef58-250">确保已运行**混合现实门户**。</span><span class="sxs-lookup"><span data-stu-id="7ef58-250">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="7ef58-251">单击 "**调试" > "开始（不调试**）"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-251">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="7ef58-252">部署到模拟器</span><span class="sxs-lookup"><span data-stu-id="7ef58-252">Deploy to Emulator</span></span>

1. <span data-ttu-id="7ef58-253">单击 "**设备**" 按钮旁边的箭头，并从下拉菜单中选择 " **HoloLens 模拟器**"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-253">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="7ef58-254">单击 "**调试" > "开始（不调试**）"。</span><span class="sxs-lookup"><span data-stu-id="7ef58-254">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="7ef58-255">试用你的应用</span><span class="sxs-lookup"><span data-stu-id="7ef58-255">Try out your app</span></span>

<span data-ttu-id="7ef58-256">部署你的应用后，请尝试四处移动该多维数据集，并观察它是否在世界各地。</span><span class="sxs-lookup"><span data-stu-id="7ef58-256">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ef58-257">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ef58-257">See also</span></span>

* [<span data-ttu-id="7ef58-258">Unity 开发概述</span><span class="sxs-lookup"><span data-stu-id="7ef58-258">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="7ef58-259">使用 Unity 和 Visual Studio 的最佳做法</span><span class="sxs-lookup"><span data-stu-id="7ef58-259">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="7ef58-260">MR 101</span><span class="sxs-lookup"><span data-stu-id="7ef58-260">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="7ef58-261">先生101E</span><span class="sxs-lookup"><span data-stu-id="7ef58-261">MR Basics 101E</span></span>](holograms-101e.md)
