---
title: MR 输入 213
description: 请按照本编码教程中使用 Unity、 Visual Studio 和沉浸式耳机，若要了解 motion 控制器的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit，mixedrealitytoolkit，mixedrealitytoolkit unity，令人着迷，动作控制器、 学院、 教程
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592988"
---
>[!NOTE]
><span data-ttu-id="96c72-104">混合现实学院教程均针对具有 HoloLens （第 1 代） 和混合现实沉浸式耳机记住。</span><span class="sxs-lookup"><span data-stu-id="96c72-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="96c72-105">在这种情况下，我们认为很重要的开发人员仍在查找中针对这些设备进行开发指南将这些教程保留在原处。</span><span class="sxs-lookup"><span data-stu-id="96c72-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="96c72-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="96c72-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="96c72-107">它们都将保留在受支持的设备上继续工作。</span><span class="sxs-lookup"><span data-stu-id="96c72-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="96c72-108">将一系列新的将在将来发布的教程将演示如何开发适用于 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="96c72-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="96c72-109">在发布时，将使用这些教程的链接更新此通知。</span><span class="sxs-lookup"><span data-stu-id="96c72-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="96c72-110">MR 输入 213:运动控制器</span><span class="sxs-lookup"><span data-stu-id="96c72-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="96c72-111">混合的现实世界中的动作控制器添加另一个级别的交互功能。</span><span class="sxs-lookup"><span data-stu-id="96c72-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="96c72-112">与[动作控制器](motion-controllers.md)，我们可以直接与对象进行交互以更自然的方式，类似于我们在现实生活中的物理交互增加浸入式并喜欢以你的应用体验。</span><span class="sxs-lookup"><span data-stu-id="96c72-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="96c72-113">在 MR 输入 213，我们将通过创建简单的空间绘制体验探讨运动控制器的输入的事件。</span><span class="sxs-lookup"><span data-stu-id="96c72-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="96c72-114">与此应用，用户就可以绘制各种类型的画笔和颜色的三维空间中。</span><span class="sxs-lookup"><span data-stu-id="96c72-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="96c72-115">在本教程中涵盖的主题</span><span class="sxs-lookup"><span data-stu-id="96c72-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="96c72-119">**控制器可视化效果**</span><span class="sxs-lookup"><span data-stu-id="96c72-119">**Controller visualization**</span></span>|<span data-ttu-id="96c72-120">**控制器输入的事件**</span><span class="sxs-lookup"><span data-stu-id="96c72-120">**Controller input events**</span></span>|<span data-ttu-id="96c72-121">**自定义控制器和 UI**</span><span class="sxs-lookup"><span data-stu-id="96c72-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="96c72-122">了解如何呈现 Unity 的游戏模式和运行时中的动作控制器模型。</span><span class="sxs-lookup"><span data-stu-id="96c72-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="96c72-123">了解不同类型的按钮事件和他们的应用程序。</span><span class="sxs-lookup"><span data-stu-id="96c72-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="96c72-124">了解如何覆盖在控制器上的 UI 元素或完全自定义。</span><span class="sxs-lookup"><span data-stu-id="96c72-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="96c72-125">设备支持</span><span class="sxs-lookup"><span data-stu-id="96c72-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="96c72-126">课程</span><span class="sxs-lookup"><span data-stu-id="96c72-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="96c72-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="96c72-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="96c72-128"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></span><span class="sxs-lookup"><span data-stu-id="96c72-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="96c72-129">MR 输入 213:运动控制器</span><span class="sxs-lookup"><span data-stu-id="96c72-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="96c72-130">✔️</span><span class="sxs-lookup"><span data-stu-id="96c72-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="96c72-131">开始之前</span><span class="sxs-lookup"><span data-stu-id="96c72-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="96c72-132">系统必备</span><span class="sxs-lookup"><span data-stu-id="96c72-132">Prerequisites</span></span>

<span data-ttu-id="96c72-133">有关，请参阅沉浸式耳机的安装清单[本页](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="96c72-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="96c72-134">本教程需要[Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="96c72-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="96c72-135">项目文件</span><span class="sxs-lookup"><span data-stu-id="96c72-135">Project files</span></span>

* <span data-ttu-id="96c72-136">[将文件下载](https://github.com/Microsoft/MixedReality213/archive/master.zip)所需的项目和文件提取到桌面。</span><span class="sxs-lookup"><span data-stu-id="96c72-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="96c72-137">如果你想要查看完成的源代码下载前，它具有[可在 GitHub 上](https://github.com/Microsoft/MixedReality213)。</span><span class="sxs-lookup"><span data-stu-id="96c72-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="96c72-138">Unity 安装程序</span><span class="sxs-lookup"><span data-stu-id="96c72-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="96c72-139">目标</span><span class="sxs-lookup"><span data-stu-id="96c72-139">Objectives</span></span>

* <span data-ttu-id="96c72-140">优化 Unity 为 Windows Mixed Reality 开发</span><span class="sxs-lookup"><span data-stu-id="96c72-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="96c72-141">设置混合的现实照相机</span><span class="sxs-lookup"><span data-stu-id="96c72-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="96c72-142">设置环境</span><span class="sxs-lookup"><span data-stu-id="96c72-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="96c72-143">说明</span><span class="sxs-lookup"><span data-stu-id="96c72-143">Instructions</span></span>

* <span data-ttu-id="96c72-144">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="96c72-144">Start Unity.</span></span>
* <span data-ttu-id="96c72-145">选择**打开**。</span><span class="sxs-lookup"><span data-stu-id="96c72-145">Select **Open**.</span></span>
* <span data-ttu-id="96c72-146">导航到你的桌面和查找**MixedReality213 master**你之前未存档的文件夹。</span><span class="sxs-lookup"><span data-stu-id="96c72-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="96c72-147">单击“选择文件夹”。</span><span class="sxs-lookup"><span data-stu-id="96c72-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="96c72-148">完成 Unity 加载项目文件后，你将能够看到 Unity 编辑器。</span><span class="sxs-lookup"><span data-stu-id="96c72-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="96c72-149">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="96c72-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="96c72-151">选择**通用 Windows 平台**中**平台**列表中，单击**切换平台**按钮。</span><span class="sxs-lookup"><span data-stu-id="96c72-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="96c72-152">目标设备设置为**任何设备**</span><span class="sxs-lookup"><span data-stu-id="96c72-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="96c72-153">将生成类型设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="96c72-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="96c72-154">设置为 SDK**最新安装**</span><span class="sxs-lookup"><span data-stu-id="96c72-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="96c72-155">检查**UnityC#项目**</span><span class="sxs-lookup"><span data-stu-id="96c72-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="96c72-156">这允许您修改 Visual Studio 项目中的脚本文件而无需重新生成 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="96c72-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="96c72-157">单击**播放器设置**。</span><span class="sxs-lookup"><span data-stu-id="96c72-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="96c72-158">在中**Inspector**面板中，向下滚动到底部</span><span class="sxs-lookup"><span data-stu-id="96c72-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="96c72-159">在 XR 设置中，检查**虚拟现实支持**</span><span class="sxs-lookup"><span data-stu-id="96c72-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="96c72-160">在虚拟现实 Sdk 下选择**Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="96c72-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="96c72-162">关闭**生成设置**窗口。</span><span class="sxs-lookup"><span data-stu-id="96c72-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="96c72-163">项目结构</span><span class="sxs-lookup"><span data-stu-id="96c72-163">Project structure</span></span>

<span data-ttu-id="96c72-164">本教程使用 **[混合现实工具包-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 。</span><span class="sxs-lookup"><span data-stu-id="96c72-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="96c72-165">您可以在找到版本[本页](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)。</span><span class="sxs-lookup"><span data-stu-id="96c72-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="96c72-167">**已完成为你的引用的场景**</span><span class="sxs-lookup"><span data-stu-id="96c72-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="96c72-168">您会发现两个已完成的 Unity 场景下**场景**文件夹。</span><span class="sxs-lookup"><span data-stu-id="96c72-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="96c72-169">**MixedReality213**:已完成的场景中具有单个画笔</span><span class="sxs-lookup"><span data-stu-id="96c72-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="96c72-170">**MixedReality213Advanced**:完成高级设计使用多个画笔的场景</span><span class="sxs-lookup"><span data-stu-id="96c72-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="96c72-171">**本教程中的新场景安装程序**</span><span class="sxs-lookup"><span data-stu-id="96c72-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="96c72-172">在 Unity 中，单击**文件 > 新的场景**</span><span class="sxs-lookup"><span data-stu-id="96c72-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="96c72-173">删除**主照相机**和**定向光**</span><span class="sxs-lookup"><span data-stu-id="96c72-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="96c72-174">从**项目面板**，搜索并拖动到以下预设**层次结构**面板：</span><span class="sxs-lookup"><span data-stu-id="96c72-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="96c72-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="96c72-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="96c72-176">Assets/AppPrefabs/**Environment**</span><span class="sxs-lookup"><span data-stu-id="96c72-176">Assets/AppPrefabs/**Environment**</span></span>

![照相机和环境](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="96c72-178">有两个相机预设混合现实工具包中：</span><span class="sxs-lookup"><span data-stu-id="96c72-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="96c72-179">**MixedRealityCamera.prefab**:仅照相机</span><span class="sxs-lookup"><span data-stu-id="96c72-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="96c72-180">**MixedRealityCameraParent.prefab**:照相机 + Teleportation + 边界</span><span class="sxs-lookup"><span data-stu-id="96c72-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="96c72-181">在本教程中，我们将使用**MixedRealityCamera**而无需 teleportation 功能。</span><span class="sxs-lookup"><span data-stu-id="96c72-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="96c72-182">因此，我们添加了简单**环境**预设包含基本的基底，若要让用户感到接地。</span><span class="sxs-lookup"><span data-stu-id="96c72-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="96c72-183">若要详细了解与 teleportation **MixedRealityCameraParent**，请参阅[高级设计-Teleportation 和 locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="96c72-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="96c72-184">**Skybox 安装程序**</span><span class="sxs-lookup"><span data-stu-id="96c72-184">**Skybox setup**</span></span>
* <span data-ttu-id="96c72-185">单击**窗口 > 照明 > 设置**</span><span class="sxs-lookup"><span data-stu-id="96c72-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="96c72-186">单击右侧的圆形**Skybox 材料字段**</span><span class="sxs-lookup"><span data-stu-id="96c72-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="96c72-187">Gray 中键入，然后选择**SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="96c72-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="96c72-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span><span class="sxs-lookup"><span data-stu-id="96c72-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![设置 skybox](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="96c72-190">检查**Skybox**选项才能够看到分配灰色渐变 skybox</span><span class="sxs-lookup"><span data-stu-id="96c72-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![切换 skybox 选项](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="96c72-192">使用 MixedRealityCamera、 环境和灰色 skybox 场景将如下所示。</span><span class="sxs-lookup"><span data-stu-id="96c72-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213 环境](images/mr213-environment-600px.jpg)
* <span data-ttu-id="96c72-194">单击**文件 > 另存为场景**</span><span class="sxs-lookup"><span data-stu-id="96c72-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="96c72-195">**保存**场景文件夹具有任何名称下的场景</span><span class="sxs-lookup"><span data-stu-id="96c72-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="96c72-196">第 1 章-控制器可视化效果</span><span class="sxs-lookup"><span data-stu-id="96c72-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="96c72-197">目标</span><span class="sxs-lookup"><span data-stu-id="96c72-197">Objectives</span></span>

* <span data-ttu-id="96c72-198">了解如何呈现控制器模型在 Unity 的游戏模式下和在运行时的动作。</span><span class="sxs-lookup"><span data-stu-id="96c72-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="96c72-199">Windows Mixed Reality 提供动画的控制器模型为控制器的可视化效果。</span><span class="sxs-lookup"><span data-stu-id="96c72-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="96c72-200">有几种方法可以在应用中执行为控制器的可视化效果：</span><span class="sxs-lookup"><span data-stu-id="96c72-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="96c72-201">默认值-使用默认控制器，而无需修改</span><span class="sxs-lookup"><span data-stu-id="96c72-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="96c72-202">混合-使用默认控制器，但自定义的某些元素或覆盖 UI 组件</span><span class="sxs-lookup"><span data-stu-id="96c72-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="96c72-203">更换 — 使用你自己自定义控制器的三维模型</span><span class="sxs-lookup"><span data-stu-id="96c72-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="96c72-204">在本章中，我们将了解这些控制器的自定义的示例。</span><span class="sxs-lookup"><span data-stu-id="96c72-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="96c72-205">说明</span><span class="sxs-lookup"><span data-stu-id="96c72-205">Instructions</span></span>

* <span data-ttu-id="96c72-206">在中**项目**面板中，键入**MotionControllers**在搜索框中。</span><span class="sxs-lookup"><span data-stu-id="96c72-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="96c72-207">此外可以在资产/HoloToolkit/输入/预设下找到它 /。</span><span class="sxs-lookup"><span data-stu-id="96c72-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="96c72-208">拖动**MotionControllers**到 prefab**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-209">单击**MotionControllers**预设中**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="96c72-210">**MotionControllers 预设**</span><span class="sxs-lookup"><span data-stu-id="96c72-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="96c72-211">**MotionControllers**预设已**MotionControllerVisualizer**为槽的备用控制器模型提供的脚本。</span><span class="sxs-lookup"><span data-stu-id="96c72-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="96c72-212">如果指定如手的形状或一双刃剑自己自定义三维模型，然后选中始终使用备用左/右模型，您将看到它们而不是默认模型。</span><span class="sxs-lookup"><span data-stu-id="96c72-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="96c72-213">我们将使用第 4 章中的此槽的控制器模型替换为画笔。</span><span class="sxs-lookup"><span data-stu-id="96c72-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="96c72-215">**说明**</span><span class="sxs-lookup"><span data-stu-id="96c72-215">**Instructions**</span></span>
* <span data-ttu-id="96c72-216">在中**Inspector**面板中，双击**MotionControllerVisualizer**脚本，以查看 Visual Studio 中的代码</span><span class="sxs-lookup"><span data-stu-id="96c72-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="96c72-217">**MotionControllerVisualizer script**</span><span class="sxs-lookup"><span data-stu-id="96c72-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="96c72-218">**MotionControllerVisualizer**并**MotionControllerInfo**类提供了用来访问和修改默认控制器模型。</span><span class="sxs-lookup"><span data-stu-id="96c72-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="96c72-219">**MotionControllerVisualizer** Unity 的订阅**InteractionSourceDetected**事件和自动实例化控制器模型，何时找到它们。</span><span class="sxs-lookup"><span data-stu-id="96c72-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="96c72-220">根据传递控制器模型[glTF 规范](https://github.com/KhronosGroup/glTF)。</span><span class="sxs-lookup"><span data-stu-id="96c72-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="96c72-221">已创建此格式提供一种通用格式，同时提高传输和解压缩三维资产后面的过程。</span><span class="sxs-lookup"><span data-stu-id="96c72-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="96c72-222">在这种情况下，我们需要检索和加载在运行时，控制器模型，因为我们想要让用户获得的体验尽可能流畅，并不保证哪个版本的运动控制器用户可能正在使用。</span><span class="sxs-lookup"><span data-stu-id="96c72-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="96c72-223">本课程中的，混合现实工具包，通过使用新版 Khronos 组[UnityGLTF 项目](https://github.com/KhronosGroup/UnityGLTF)。</span><span class="sxs-lookup"><span data-stu-id="96c72-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="96c72-224">一旦已传递控制器，可以使用脚本**MotionControllerInfo**特定控制器元素查找转换，以便它们可以正确地确定自己的位置。</span><span class="sxs-lookup"><span data-stu-id="96c72-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="96c72-225">在更高版本的章中，我们将了解如何使用这些脚本将 UI 元素附加到的控制器。</span><span class="sxs-lookup"><span data-stu-id="96c72-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="96c72-226">*在一些脚本，您会发现使用的代码块 **#if ！UNITY_EDITOR**或**UNITY_WSA**。部署到 Windows 时，只能在 UWP 运行时上运行这些代码块。这是因为 Unity 编辑器和 UWP 应用运行时使用的 Api 集不同。*</span><span class="sxs-lookup"><span data-stu-id="96c72-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="96c72-227">**保存**场景和单击**播放**按钮。</span><span class="sxs-lookup"><span data-stu-id="96c72-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="96c72-228">你将能够看到与您的头戴式中动作控制器场景。</span><span class="sxs-lookup"><span data-stu-id="96c72-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="96c72-229">您可以看到详细的动画效果的按钮单击、 摇杆移动和触摸板触摸突出显示。</span><span class="sxs-lookup"><span data-stu-id="96c72-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller 可视化效果默认](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="96c72-231">第 2 章-附加到控制器的 UI 元素</span><span class="sxs-lookup"><span data-stu-id="96c72-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="96c72-232">目标</span><span class="sxs-lookup"><span data-stu-id="96c72-232">Objectives</span></span>

* <span data-ttu-id="96c72-233">了解有关元素的动作控制器</span><span class="sxs-lookup"><span data-stu-id="96c72-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="96c72-234">了解如何将对象附加到的控制器的特定部分</span><span class="sxs-lookup"><span data-stu-id="96c72-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="96c72-235">在本章中，您将学习如何将用户界面元素添加到控制器的用户可以轻松地访问和处理在任何时间。</span><span class="sxs-lookup"><span data-stu-id="96c72-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="96c72-236">您将学习如何添加简单的颜色选取器 UI 使用触摸板输入。</span><span class="sxs-lookup"><span data-stu-id="96c72-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="96c72-237">说明</span><span class="sxs-lookup"><span data-stu-id="96c72-237">Instructions</span></span>

* <span data-ttu-id="96c72-238">在中**项目**面板中，搜索**MotionControllerInfo**脚本。</span><span class="sxs-lookup"><span data-stu-id="96c72-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="96c72-239">从搜索结果中，双击**MotionControllerInfo**脚本，以查看 Visual Studio 中的代码。</span><span class="sxs-lookup"><span data-stu-id="96c72-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="96c72-240">**MotionControllerInfo script**</span><span class="sxs-lookup"><span data-stu-id="96c72-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="96c72-241">第一步是选择想要附加到的 UI 控制器的哪些元素。</span><span class="sxs-lookup"><span data-stu-id="96c72-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="96c72-242">这些元素中定义**ControllerElementEnum**中**MotionControllerInfo.cs**。</span><span class="sxs-lookup"><span data-stu-id="96c72-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="96c72-244">**主页**</span><span class="sxs-lookup"><span data-stu-id="96c72-244">**Home**</span></span>
* <span data-ttu-id="96c72-245">**菜单**</span><span class="sxs-lookup"><span data-stu-id="96c72-245">**Menu**</span></span>
* <span data-ttu-id="96c72-246">**Grasp**</span><span class="sxs-lookup"><span data-stu-id="96c72-246">**Grasp**</span></span>
* <span data-ttu-id="96c72-247">**摇杆**</span><span class="sxs-lookup"><span data-stu-id="96c72-247">**Thumbstick**</span></span>
* <span data-ttu-id="96c72-248">**Select**</span><span class="sxs-lookup"><span data-stu-id="96c72-248">**Select**</span></span>
* <span data-ttu-id="96c72-249">**触摸板**</span><span class="sxs-lookup"><span data-stu-id="96c72-249">**Touchpad**</span></span>
* <span data-ttu-id="96c72-250">**指针姿势**– 此元素表示指向向前方向的控制器的提示。</span><span class="sxs-lookup"><span data-stu-id="96c72-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="96c72-251">**说明**</span><span class="sxs-lookup"><span data-stu-id="96c72-251">**Instructions**</span></span>
* <span data-ttu-id="96c72-252">在中**项目**面板中，搜索**AttachToController**脚本。</span><span class="sxs-lookup"><span data-stu-id="96c72-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="96c72-253">从搜索结果中，双击**AttachToController**脚本，以查看 Visual Studio 中的代码。</span><span class="sxs-lookup"><span data-stu-id="96c72-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="96c72-254">**AttachToController 脚本**</span><span class="sxs-lookup"><span data-stu-id="96c72-254">**AttachToController script**</span></span>

<span data-ttu-id="96c72-255">**AttachToController**脚本提供了简单的方法将任何对象附加到指定的控制器左右手使用习惯和元素。</span><span class="sxs-lookup"><span data-stu-id="96c72-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="96c72-256">In **AttachElementToController()**,</span><span class="sxs-lookup"><span data-stu-id="96c72-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="96c72-257">检查左右手使用习惯使用**MotionControllerInfo.Handedness**</span><span class="sxs-lookup"><span data-stu-id="96c72-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="96c72-258">获取控制器使用的特定元素**MotionControllerInfo.TryGetElement()**</span><span class="sxs-lookup"><span data-stu-id="96c72-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="96c72-259">检索的元素后从控制器模型，父对象下它将转换并设置为零的对象的本地位置和旋转。</span><span class="sxs-lookup"><span data-stu-id="96c72-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="96c72-260">若要使用的最简单方法**AttachToController**脚本是从它继承，如我们所做的情况下**ColorPickerWheel。**</span><span class="sxs-lookup"><span data-stu-id="96c72-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="96c72-261">只需重写**OnAttachToController**并**OnDetatchFromController**函数来执行您的安装程序 / 明细时检测到 / 断开连接控制器。</span><span class="sxs-lookup"><span data-stu-id="96c72-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="96c72-262">**说明**</span><span class="sxs-lookup"><span data-stu-id="96c72-262">**Instructions**</span></span>
* <span data-ttu-id="96c72-263">在中**项目**面板中，在搜索框中键入**ColorPickerWheel**。</span><span class="sxs-lookup"><span data-stu-id="96c72-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="96c72-264">此外可以在资产/AppPrefabs 下找到它 /。</span><span class="sxs-lookup"><span data-stu-id="96c72-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="96c72-265">拖动**ColorPickerWheel**到 prefab**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-266">单击**ColorPickerWheel**预设中**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-267">在中**Inspector**面板中，双击**ColorPickerWheel**脚本，以查看 Visual Studio 中的代码。</span><span class="sxs-lookup"><span data-stu-id="96c72-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel 预设](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="96c72-269">**ColorPickerWheel 脚本**</span><span class="sxs-lookup"><span data-stu-id="96c72-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="96c72-270">由于**ColorPickerWheel**继承**AttachToController**，它显示了**左右手使用习惯**并**元素**中**检查器**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="96c72-271">我们将把在左侧的控制器上的触摸板元素到连接的用户界面。</span><span class="sxs-lookup"><span data-stu-id="96c72-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![ColorPickerWheel 脚本](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="96c72-273">**ColorPickerWheel**重写**OnAttachToController**并**OnDetatchFromController**订阅将用于与颜色选择下一步一章中的输入事件触摸板进行输入。</span><span class="sxs-lookup"><span data-stu-id="96c72-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* <span data-ttu-id="96c72-274">**保存**场景和单击**播放**按钮。</span><span class="sxs-lookup"><span data-stu-id="96c72-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="96c72-275">**将对象附加到的控制器的另一种方法**</span><span class="sxs-lookup"><span data-stu-id="96c72-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="96c72-276">我们建议你的脚本，从继承**AttachToController**并重写**OnAttachToController**。</span><span class="sxs-lookup"><span data-stu-id="96c72-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="96c72-277">但是，这不总是可能。</span><span class="sxs-lookup"><span data-stu-id="96c72-277">However, this may not always be possible.</span></span> <span data-ttu-id="96c72-278">一种替代方法使用它作为独立组件。</span><span class="sxs-lookup"><span data-stu-id="96c72-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="96c72-279">当你想要将现有预设可附加到一个控制器，而无需重构您的脚本时，这很有用。</span><span class="sxs-lookup"><span data-stu-id="96c72-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="96c72-280">只需让类等待 IsAttached 设置为 true，然后才能执行任何设置。</span><span class="sxs-lookup"><span data-stu-id="96c72-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="96c72-281">若要执行此操作的最简单方法是使用协同程序的 Start。</span><span class="sxs-lookup"><span data-stu-id="96c72-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="96c72-282">第 3 章 — 使用触摸板进行输入</span><span class="sxs-lookup"><span data-stu-id="96c72-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="96c72-283">目标</span><span class="sxs-lookup"><span data-stu-id="96c72-283">Objectives</span></span>

* <span data-ttu-id="96c72-284">了解如何将触摸板输入的数据事件</span><span class="sxs-lookup"><span data-stu-id="96c72-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="96c72-285">了解如何使用触摸板轴位置信息的应用体验</span><span class="sxs-lookup"><span data-stu-id="96c72-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="96c72-286">说明</span><span class="sxs-lookup"><span data-stu-id="96c72-286">Instructions</span></span>

* <span data-ttu-id="96c72-287">在中**层次结构**面板中，单击**ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="96c72-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="96c72-288">在中**Inspector**面板下**Animatior**，双击**ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="96c72-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="96c72-289">你将能够看到**动画器**打开选项卡</span><span class="sxs-lookup"><span data-stu-id="96c72-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="96c72-290">**显示/隐藏 UI 与 Unity 的动画控制器**</span><span class="sxs-lookup"><span data-stu-id="96c72-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="96c72-291">若要显示和隐藏**ColorPickerWheel**动画的 UI 中，我们将使用[Unity 的动画系统](https://docs.unity3d.com/Manual/AnimationOverview.html)。</span><span class="sxs-lookup"><span data-stu-id="96c72-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="96c72-292">设置**ColorPickerWheel**的**Visible**属性设置为 true 或 false 触发器**显示**并**隐藏**动画触发器。</span><span class="sxs-lookup"><span data-stu-id="96c72-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="96c72-293">**显示**并**隐藏**中定义参数**ColorPickerWheelController**动画控制器。</span><span class="sxs-lookup"><span data-stu-id="96c72-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity 动画控制器](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="96c72-295">**说明**</span><span class="sxs-lookup"><span data-stu-id="96c72-295">**Instructions**</span></span>
* <span data-ttu-id="96c72-296">在中**层次结构**面板中，选择**ColorPickerWheel**预设</span><span class="sxs-lookup"><span data-stu-id="96c72-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="96c72-297">在中**Inspector**面板中，双击**ColorPickerWheel**脚本，以查看 Visual Studio 中的代码</span><span class="sxs-lookup"><span data-stu-id="96c72-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="96c72-298">**ColorPickerWheel 脚本**</span><span class="sxs-lookup"><span data-stu-id="96c72-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="96c72-299">**ColorPickerWheel** Unity 的订阅**InteractionSourceUpdated**以侦听触摸板事件的事件。</span><span class="sxs-lookup"><span data-stu-id="96c72-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="96c72-300">在中**InteractionSourceUpdated()**，该脚本首先检查以确保其：</span><span class="sxs-lookup"><span data-stu-id="96c72-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="96c72-301">是实际的触摸板事件 (obj.state。**touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="96c72-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="96c72-302">源自左控制器 (obj.state.source。**左右手使用习惯**)</span><span class="sxs-lookup"><span data-stu-id="96c72-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="96c72-303">如果两者均为 true，触摸板位置 (obj.state。**touchpadPosition**) 分配给**selectorPosition**。</span><span class="sxs-lookup"><span data-stu-id="96c72-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="96c72-304">在**update （)** 根据**可见**属性，它将触发颜色选取器的动画器组件中的显示和隐藏动画触发器</span><span class="sxs-lookup"><span data-stu-id="96c72-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="96c72-305">在中**update （)**， **selectorPosition**用于将一条颜色盘网格碰撞体，它将返回 UV 位置在强制转换。</span><span class="sxs-lookup"><span data-stu-id="96c72-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="96c72-306">此位置可以用于查找的像素坐标和颜色的颜色盘纹理值。</span><span class="sxs-lookup"><span data-stu-id="96c72-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="96c72-307">此值是通过其他脚本可以访问**SelectedColor**属性。</span><span class="sxs-lookup"><span data-stu-id="96c72-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![颜色选取器滚轮光线投射的细节](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="96c72-309">第 4 章-重写控制器模型</span><span class="sxs-lookup"><span data-stu-id="96c72-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="96c72-310">目标</span><span class="sxs-lookup"><span data-stu-id="96c72-310">Objectives</span></span>

* <span data-ttu-id="96c72-311">了解如何重写具有自定义的三维模型的控制器模型。</span><span class="sxs-lookup"><span data-stu-id="96c72-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="96c72-313">说明</span><span class="sxs-lookup"><span data-stu-id="96c72-313">Instructions</span></span>

* <span data-ttu-id="96c72-314">单击**MotionControllers**中**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-315">单击右侧的圆形**备用右控制器**字段。</span><span class="sxs-lookup"><span data-stu-id="96c72-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="96c72-316">在键入**BrushController**，然后从结果选择预设。</span><span class="sxs-lookup"><span data-stu-id="96c72-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="96c72-317">你可以在资产/AppPrefabs 下找到它/**BrushController**。</span><span class="sxs-lookup"><span data-stu-id="96c72-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="96c72-318">检查**始终使用正确的备用模式**</span><span class="sxs-lookup"><span data-stu-id="96c72-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="96c72-320">**BrushController**预设不需要将其纳入**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="96c72-321">但是，若要查看其子组件：</span><span class="sxs-lookup"><span data-stu-id="96c72-321">However, to check out its child components:</span></span>
* <span data-ttu-id="96c72-322">在中**项目**面板中，键入**BrushController**拖到**BrushController**到 prefab**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="96c72-324">您会发现**提示**组件**BrushController**。</span><span class="sxs-lookup"><span data-stu-id="96c72-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="96c72-325">我们将其转换要启动/停止绘制线条。</span><span class="sxs-lookup"><span data-stu-id="96c72-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="96c72-326">删除**BrushController**从**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-327">**保存**场景和单击**播放**按钮。</span><span class="sxs-lookup"><span data-stu-id="96c72-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="96c72-328">你将能够看到画笔模型替换为右侧运动控制器。</span><span class="sxs-lookup"><span data-stu-id="96c72-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="96c72-329">第 5 章-使用选择的输入进行绘制</span><span class="sxs-lookup"><span data-stu-id="96c72-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="96c72-330">目标</span><span class="sxs-lookup"><span data-stu-id="96c72-330">Objectives</span></span>

* <span data-ttu-id="96c72-331">了解如何使用选择按钮事件来启动和停止为线图</span><span class="sxs-lookup"><span data-stu-id="96c72-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="96c72-332">说明</span><span class="sxs-lookup"><span data-stu-id="96c72-332">Instructions</span></span>

* <span data-ttu-id="96c72-333">搜索**BrushController**预设中**项目**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="96c72-334">在中**Inspector**面板中，双击**BrushController**脚本，以查看 Visual Studio 中的代码</span><span class="sxs-lookup"><span data-stu-id="96c72-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="96c72-335">**BrushController 脚本**</span><span class="sxs-lookup"><span data-stu-id="96c72-335">**BrushController script**</span></span>

<span data-ttu-id="96c72-336">**BrushController**订阅 InteractionManager **InteractionSourcePressed**并**InteractionSourceReleased**事件。</span><span class="sxs-lookup"><span data-stu-id="96c72-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="96c72-337">当**InteractionSourcePressed**触发事件时，将画笔的**绘制**属性设置为 true; 当**InteractionSourceReleased**触发事件时，将画笔的**绘制**属性设置为 false。</span><span class="sxs-lookup"><span data-stu-id="96c72-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="96c72-338">虽然**绘制**设置为 true，画笔会生成点在实例化 Unity **LineRenderer**。</span><span class="sxs-lookup"><span data-stu-id="96c72-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="96c72-339">此预设的引用保存在的画笔**笔划 Prefab**字段。</span><span class="sxs-lookup"><span data-stu-id="96c72-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="96c72-340">若要使用从颜色选取器滚轮 UI 中，当前选定的颜色**BrushController**需要具有对引用**ColorPickerWheel**对象。</span><span class="sxs-lookup"><span data-stu-id="96c72-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="96c72-341">因为**BrushController**在更换控制器的运行时实例化预设时，必须在运行时设置的场景中的对象的引用。</span><span class="sxs-lookup"><span data-stu-id="96c72-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="96c72-342">在这种情况下，我们使用**GameObject.FindObjectOfType**来查找**ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="96c72-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* <span data-ttu-id="96c72-343">**保存**场景和单击**播放**按钮。</span><span class="sxs-lookup"><span data-stu-id="96c72-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="96c72-344">你将能够绘制线条和绘制右侧的控制器上使用选择按钮。</span><span class="sxs-lookup"><span data-stu-id="96c72-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="96c72-345">第 6-章对象生成与 Select 一起输入</span><span class="sxs-lookup"><span data-stu-id="96c72-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="96c72-346">目标</span><span class="sxs-lookup"><span data-stu-id="96c72-346">Objectives</span></span>

* <span data-ttu-id="96c72-347">了解如何使用 Select，然后抓住按钮输入的事件</span><span class="sxs-lookup"><span data-stu-id="96c72-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="96c72-348">了解如何实例化对象</span><span class="sxs-lookup"><span data-stu-id="96c72-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="96c72-349">说明</span><span class="sxs-lookup"><span data-stu-id="96c72-349">Instructions</span></span>

* <span data-ttu-id="96c72-350">在中**项目**面板中，键入**ObjectSpawner**在搜索框中。</span><span class="sxs-lookup"><span data-stu-id="96c72-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="96c72-351">此外可以在资产/AppPrefabs 下找到它 /</span><span class="sxs-lookup"><span data-stu-id="96c72-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="96c72-352">拖动**ObjectSpawner**到 prefab**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-353">单击**ObjectSpawner**中**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-354">**ObjectSpawner**具有一个名为字段**颜色源**。</span><span class="sxs-lookup"><span data-stu-id="96c72-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="96c72-355">从**层次结构**面板中，将**ColorPickerWheel**到此字段的引用。</span><span class="sxs-lookup"><span data-stu-id="96c72-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![对象 Spawner 检查器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="96c72-357">单击**ObjectSpawner**预设中**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-358">在中**Inspector**面板中，双击**ObjectSpawner**脚本，以查看 Visual Studio 中的代码。</span><span class="sxs-lookup"><span data-stu-id="96c72-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="96c72-359">**ObjectSpawner 脚本**</span><span class="sxs-lookup"><span data-stu-id="96c72-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="96c72-360">**ObjectSpawner**到空间实例化的基元的网格 （多维数据集、 球体、 cylinder） 副本。</span><span class="sxs-lookup"><span data-stu-id="96c72-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="96c72-361">当**InteractionSourcePressed**检测到它会检查旋向性以及它是否**InteractionSourcePressType.Grasp**或**InteractionSourcePressType.Select**事件。</span><span class="sxs-lookup"><span data-stu-id="96c72-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="96c72-362">有关**掌握**事件，则会递增当前网格类型 （球体、 立方体、 圆柱体） 的索引</span><span class="sxs-lookup"><span data-stu-id="96c72-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="96c72-363">有关**选择**事件，请在**SpawnObject()**，新对象是实例化、 无父级且已发布到世界。</span><span class="sxs-lookup"><span data-stu-id="96c72-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="96c72-364">**ObjectSpawner**使用**ColorPickerWheel**设置显示对象的材料的颜色。</span><span class="sxs-lookup"><span data-stu-id="96c72-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="96c72-365">生成的对象是给定此材料的实例，因此它们将保留其颜色。</span><span class="sxs-lookup"><span data-stu-id="96c72-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="96c72-366">**保存**场景和单击**播放**按钮。</span><span class="sxs-lookup"><span data-stu-id="96c72-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="96c72-367">你将能够更改与掌握按钮对象并生成具有选择按钮的对象。</span><span class="sxs-lookup"><span data-stu-id="96c72-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="96c72-368">生成并部署到混合现实门户应用</span><span class="sxs-lookup"><span data-stu-id="96c72-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="96c72-369">在 Unity 中，选择**文件 > 生成设置**。</span><span class="sxs-lookup"><span data-stu-id="96c72-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="96c72-370">单击**添加打开场景**若要添加到当前场景**生成中的场景**。</span><span class="sxs-lookup"><span data-stu-id="96c72-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="96c72-371">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="96c72-371">Click **Build**.</span></span>
* <span data-ttu-id="96c72-372">创建**新文件夹**名为"应用"。</span><span class="sxs-lookup"><span data-stu-id="96c72-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="96c72-373">单击一下**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="96c72-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="96c72-374">单击“选择文件夹”。</span><span class="sxs-lookup"><span data-stu-id="96c72-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="96c72-375">Unity 完成操作后，将出现一个文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="96c72-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="96c72-376">打开**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="96c72-376">Open the **App** folder.</span></span>
* <span data-ttu-id="96c72-377">双击**YourSceneName.sln** Visual Studio 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="96c72-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="96c72-378">在 Visual Studio 中，使用顶部的工具栏将目标更改为调试从**发行**并从到的 ARM **X64**。</span><span class="sxs-lookup"><span data-stu-id="96c72-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="96c72-379">单击设备按钮旁边的下拉箭头，然后选择**本地计算机**。</span><span class="sxs-lookup"><span data-stu-id="96c72-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="96c72-380">单击**调试-> 启动不调试**中的菜单或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="96c72-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="96c72-381">现在应用生成并安装在混合现实门户。</span><span class="sxs-lookup"><span data-stu-id="96c72-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="96c72-382">您可以再次启动通过混合现实门户中的开始菜单。</span><span class="sxs-lookup"><span data-stu-id="96c72-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="96c72-383">高级的设计-画笔工具与射线布局</span><span class="sxs-lookup"><span data-stu-id="96c72-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="96c72-385">在本章中，您将学习如何使用自定义画笔工具集合替换默认运动控制器模型。</span><span class="sxs-lookup"><span data-stu-id="96c72-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="96c72-386">为了便于参考，可以找到已完成的场景**MixedReality213Advanced**下**场景**文件夹。</span><span class="sxs-lookup"><span data-stu-id="96c72-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="96c72-387">说明</span><span class="sxs-lookup"><span data-stu-id="96c72-387">Instructions</span></span>

* <span data-ttu-id="96c72-388">在中**项目**面板中，键入**BrushSelector**在搜索框中。</span><span class="sxs-lookup"><span data-stu-id="96c72-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="96c72-389">此外可以在资产/AppPrefabs 下找到它 /</span><span class="sxs-lookup"><span data-stu-id="96c72-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="96c72-390">拖动**BrushSelector**到 prefab**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-391">对于组织中，创建名为空的 GameObject**画笔**</span><span class="sxs-lookup"><span data-stu-id="96c72-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="96c72-392">以下预设从拖动**项目**面板拖动到图表**画笔**</span><span class="sxs-lookup"><span data-stu-id="96c72-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="96c72-393">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="96c72-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="96c72-394">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="96c72-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="96c72-395">Assets/AppPrefabs/**Eraser**</span><span class="sxs-lookup"><span data-stu-id="96c72-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="96c72-396">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="96c72-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="96c72-397">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="96c72-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="96c72-398">Assets/AppPrefabs/**Pencil**</span><span class="sxs-lookup"><span data-stu-id="96c72-398">Assets/AppPrefabs/**Pencil**</span></span>

![画笔](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="96c72-400">单击**MotionControllers**预设中**层次结构**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="96c72-401">在中**Inspector**面板中，取消选中**始终使用备用右模型**上**运动控制器可视化工具**</span><span class="sxs-lookup"><span data-stu-id="96c72-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="96c72-402">在中**层次结构**面板中，单击**BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="96c72-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="96c72-403">**BrushSelector**有一个名为**颜色选取器**</span><span class="sxs-lookup"><span data-stu-id="96c72-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="96c72-404">从**层次结构**面板中，将**ColorPickerWheel**到**颜色选取器**字段中**检查器**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![分配 ColorPickerWheel 的画笔选择器](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="96c72-406">在中**层次结构**面板下**BrushSelector**预设，请选择**菜单**对象。</span><span class="sxs-lookup"><span data-stu-id="96c72-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="96c72-407">在**Inspector**面板下**LineObjectCollection**组件中，打开**对象**数组下拉列表。</span><span class="sxs-lookup"><span data-stu-id="96c72-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="96c72-408">你将看到 6 个空插槽。</span><span class="sxs-lookup"><span data-stu-id="96c72-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="96c72-409">从**层次结构**面板中，将每个父级下预设**画笔**到按任意顺序这些槽的 GameObject。</span><span class="sxs-lookup"><span data-stu-id="96c72-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="96c72-410">（请确保自己从场景，而不在项目文件夹中预设拖动的预设。）</span><span class="sxs-lookup"><span data-stu-id="96c72-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![画笔选择器](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="96c72-412">**BrushSelector 预设**</span><span class="sxs-lookup"><span data-stu-id="96c72-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="96c72-413">由于**BrushSelector**继承**AttachToController**，它显示了**左右手使用习惯**并**元素**中的选项**检查器**面板。</span><span class="sxs-lookup"><span data-stu-id="96c72-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="96c72-414">我们选择了**右**并**指向会带来**若要将画笔工具附加到与正向右侧控制器。</span><span class="sxs-lookup"><span data-stu-id="96c72-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="96c72-415">**BrushSelector**使用两个实用程序：</span><span class="sxs-lookup"><span data-stu-id="96c72-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="96c72-416">**椭圆**： 用于在空间沿椭圆形形状中生成点。</span><span class="sxs-lookup"><span data-stu-id="96c72-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="96c72-417">**LineObjectCollection**： 将分发对象使用生成的任何行类 （例如，椭圆） 的点。</span><span class="sxs-lookup"><span data-stu-id="96c72-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="96c72-418">这是什么，我们将使用来放置我们画笔沿椭圆形形状。</span><span class="sxs-lookup"><span data-stu-id="96c72-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="96c72-419">结合使用时，可以使用这些实用程序来创建径向菜单。</span><span class="sxs-lookup"><span data-stu-id="96c72-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="96c72-420">**LineObjectCollection 脚本**</span><span class="sxs-lookup"><span data-stu-id="96c72-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="96c72-421">**LineObjectCollection**具有的大小、 位置和分布沿其行中的对象的旋转的控件。</span><span class="sxs-lookup"><span data-stu-id="96c72-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="96c72-422">这可用于创建类似的画笔选择器径向菜单。</span><span class="sxs-lookup"><span data-stu-id="96c72-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="96c72-423">若要创建的外观画笔该规模从它们接近所选中心位置，如 nothing **ObjectScale**边缘关闭曲线中的中心和音量补偿器的峰值。</span><span class="sxs-lookup"><span data-stu-id="96c72-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="96c72-424">**BrushSelector 脚本**</span><span class="sxs-lookup"><span data-stu-id="96c72-424">**BrushSelector script**</span></span>

<span data-ttu-id="96c72-425">情况下**BrushSelector**，我们选择了使用过程的动画。</span><span class="sxs-lookup"><span data-stu-id="96c72-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="96c72-426">首先，通过一个椭圆中分布画笔模型**LineObjectCollection**脚本。</span><span class="sxs-lookup"><span data-stu-id="96c72-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="96c72-427">然后，每个画笔负责维护其基于用户的手中的位置及其**DisplayMode**更改基于对所选内容的值。</span><span class="sxs-lookup"><span data-stu-id="96c72-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="96c72-428">我们选择的原因是高概率的画笔在用户选择画笔被中断的位置转换过程的方法。</span><span class="sxs-lookup"><span data-stu-id="96c72-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="96c72-429">Mecanim 动画可以处理服务中断正常，但往往比简单 Lerp 操作更复杂。</span><span class="sxs-lookup"><span data-stu-id="96c72-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="96c72-430">**BrushSelector**使用这两者的组合。</span><span class="sxs-lookup"><span data-stu-id="96c72-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="96c72-431">检测到触摸板进行输入时，画笔选项变得可见和纵向扩展沿的射线的菜单。</span><span class="sxs-lookup"><span data-stu-id="96c72-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="96c72-432">（这表明用户已做出了选择） 超时期限过后画笔选项规模下再次离开仅选定的画笔。</span><span class="sxs-lookup"><span data-stu-id="96c72-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="96c72-433">**可视化触摸板进行输入**</span><span class="sxs-lookup"><span data-stu-id="96c72-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="96c72-434">甚至在控制器模型已被完全替换的情况下，它可以是有帮助，以显示原始模型输入输入。</span><span class="sxs-lookup"><span data-stu-id="96c72-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="96c72-435">这有助于在现实中接地用户的操作。</span><span class="sxs-lookup"><span data-stu-id="96c72-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="96c72-436">有关**BrushSelector**我们选择以使触摸板简要可见时收到了输入。</span><span class="sxs-lookup"><span data-stu-id="96c72-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="96c72-437">通过从替换自定义的材料，为其材料的控制器中检索的触摸板元素执行此操作，然后将过渡应用于该材料的颜色基于最后一次触摸板接收输入。</span><span class="sxs-lookup"><span data-stu-id="96c72-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="96c72-438">**画笔工具使用触摸板进行输入的选定内容**</span><span class="sxs-lookup"><span data-stu-id="96c72-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="96c72-439">当画笔选择器检测到触摸板的按下的输入时，它会检查输入以确定它是从左到右的位置。</span><span class="sxs-lookup"><span data-stu-id="96c72-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="96c72-440">**使用 selectPressedAmount 笔画粗细**</span><span class="sxs-lookup"><span data-stu-id="96c72-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="96c72-441">而不是**InteractionSourcePressType.Select**中的事件**InteractionSourcePressed()**，就可以通过按下的量的模拟值**selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="96c72-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="96c72-442">此值可以在中检索**InteractionSourceUpdated()**。</span><span class="sxs-lookup"><span data-stu-id="96c72-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="96c72-443">**橡皮擦脚本**</span><span class="sxs-lookup"><span data-stu-id="96c72-443">**Eraser script**</span></span>

<span data-ttu-id="96c72-444">**橡皮擦**是一种特殊的重写基的画笔**画笔**的**DrawOverTime()** 函数。</span><span class="sxs-lookup"><span data-stu-id="96c72-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="96c72-445">绘制为真，橡皮擦将检查以确定其提示是否与任何现有的画笔笔画相交。</span><span class="sxs-lookup"><span data-stu-id="96c72-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="96c72-446">如果是这样，它们都添加到队列，向下要收缩和删除。</span><span class="sxs-lookup"><span data-stu-id="96c72-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="96c72-447">高级的设计-Teleportation 和 locomotion</span><span class="sxs-lookup"><span data-stu-id="96c72-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="96c72-448">如果你想要允许用户与使用摇杆 teleportation 在场景周围移动，请使用**MixedRealityCameraParent**而不是**MixedRealityCamera**。</span><span class="sxs-lookup"><span data-stu-id="96c72-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="96c72-449">此外需要添加**InputManager**并**DefaultCusor**。</span><span class="sxs-lookup"><span data-stu-id="96c72-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="96c72-450">由于**MixedRealityCameraParent**已包括**MotionControllers**并**边界**作为子组件，应删除现有**MotionControllers**并**环境**预设。</span><span class="sxs-lookup"><span data-stu-id="96c72-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="96c72-451">说明</span><span class="sxs-lookup"><span data-stu-id="96c72-451">Instructions</span></span>

* <span data-ttu-id="96c72-452">在中**层次结构**面板中，删除**MixedRealityCamera**，**环境**和**MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="96c72-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="96c72-453">从**项目面板**，搜索并拖动到以下预设**层次结构**面板：</span><span class="sxs-lookup"><span data-stu-id="96c72-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="96c72-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="96c72-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="96c72-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="96c72-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="96c72-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="96c72-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![混合的现实照相机父](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="96c72-458">在中**层次结构**面板中，单击**输入管理器**</span><span class="sxs-lookup"><span data-stu-id="96c72-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="96c72-459">在中**Inspector**面板中，向下滚动到**简单单个指针选择器**部分</span><span class="sxs-lookup"><span data-stu-id="96c72-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="96c72-460">从**层次结构**面板中，将**DefaultCursor**到**游标**字段</span><span class="sxs-lookup"><span data-stu-id="96c72-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![分配 DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="96c72-462">**保存**场景和单击**播放**按钮。</span><span class="sxs-lookup"><span data-stu-id="96c72-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="96c72-463">你将能够使用摇杆左/右或 teleport 轮换一次。</span><span class="sxs-lookup"><span data-stu-id="96c72-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="96c72-464">结束</span><span class="sxs-lookup"><span data-stu-id="96c72-464">The end</span></span>

<span data-ttu-id="96c72-465">就是本教程结束 ！</span><span class="sxs-lookup"><span data-stu-id="96c72-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="96c72-466">介绍了：</span><span class="sxs-lookup"><span data-stu-id="96c72-466">You learned:</span></span>
* <span data-ttu-id="96c72-467">如何使用 Unity 的游戏模式和运行时中的动作控制器模型。</span><span class="sxs-lookup"><span data-stu-id="96c72-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="96c72-468">如何使用不同类型的按钮事件和他们的应用程序。</span><span class="sxs-lookup"><span data-stu-id="96c72-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="96c72-469">如何覆盖在控制器上的 UI 元素或完全自定义。</span><span class="sxs-lookup"><span data-stu-id="96c72-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="96c72-470">现已准备好开始使用 motion 控制器创建自己的沉浸式体验 ！</span><span class="sxs-lookup"><span data-stu-id="96c72-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="96c72-471">已完成的场景</span><span class="sxs-lookup"><span data-stu-id="96c72-471">Completed scenes</span></span>

* <span data-ttu-id="96c72-472">在 Unity 中的**项目**面板中单击**场景**文件夹。</span><span class="sxs-lookup"><span data-stu-id="96c72-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="96c72-473">您会发现两个 Unity sceens **MixedReality213**并**MixedReality213Advanced**。</span><span class="sxs-lookup"><span data-stu-id="96c72-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="96c72-474">**MixedReality213**:已完成的场景中具有单个画笔</span><span class="sxs-lookup"><span data-stu-id="96c72-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="96c72-475">**MixedReality213Advanced**:使用选择按钮的按量示例的多个画笔的已完成的场景</span><span class="sxs-lookup"><span data-stu-id="96c72-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="96c72-476">请参阅</span><span class="sxs-lookup"><span data-stu-id="96c72-476">See also</span></span>

* [<span data-ttu-id="96c72-477">MR 输入 213 项目文件</span><span class="sxs-lookup"><span data-stu-id="96c72-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="96c72-478">混合的现实工具包-运动控制器测试场景</span><span class="sxs-lookup"><span data-stu-id="96c72-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="96c72-479">混合的现实工具包-随取即行机制</span><span class="sxs-lookup"><span data-stu-id="96c72-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="96c72-480">运动控制器开发指导原则</span><span class="sxs-lookup"><span data-stu-id="96c72-480">Motion controller development guidelines</span></span>](motion-controllers.md)
