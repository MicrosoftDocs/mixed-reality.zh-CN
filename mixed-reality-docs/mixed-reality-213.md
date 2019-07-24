---
title: MR 输入213
description: 按照此编码教程使用 Unity、Visual Studio 和沉浸式耳机来了解动作控制器的详细信息。
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 沉浸式, 运动总监, 学院, 教程
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516400"
---
>[!NOTE]
><span data-ttu-id="68e17-104">混合现实学院教程的设计附带了 HoloLens (第一代) 和混合现实沉浸式耳机。</span><span class="sxs-lookup"><span data-stu-id="68e17-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="68e17-105">因此, 对于那些仍在寻找为这些设备进行开发的指导的开发人员来说, 我们认为这些教程是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="68e17-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="68e17-106">这些教程将 **_不_** 使用最新工具集或用于 HoloLens 2 的交互进行更新。</span><span class="sxs-lookup"><span data-stu-id="68e17-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="68e17-107">将保留这些设备以继续使用支持的设备。</span><span class="sxs-lookup"><span data-stu-id="68e17-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="68e17-108">将来会发布一系列新教程, 这些教程将演示如何针对 HoloLens 2 进行开发。</span><span class="sxs-lookup"><span data-stu-id="68e17-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="68e17-109">此通知将在发布时通过指向这些教程的链接进行更新。</span><span class="sxs-lookup"><span data-stu-id="68e17-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="68e17-110">MR 输入 213:运动控制器</span><span class="sxs-lookup"><span data-stu-id="68e17-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="68e17-111">混合现实世界中的运动控制器增加了另一层的交互性。</span><span class="sxs-lookup"><span data-stu-id="68e17-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="68e17-112">借助[运动控制器](motion-controllers.md), 我们可以以更自然的方式与对象直接交互, 类似于真实生活中的物理交互, 增加浸入式和感到满意的应用体验。</span><span class="sxs-lookup"><span data-stu-id="68e17-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="68e17-113">在 MR 输入213中, 我们将通过创建一个简单的空间绘制体验来浏览运动控制器的输入事件。</span><span class="sxs-lookup"><span data-stu-id="68e17-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="68e17-114">对于此应用程序, 用户可以在具有各种类型的画笔和颜色的三维空间中进行绘制。</span><span class="sxs-lookup"><span data-stu-id="68e17-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="68e17-115">本教程中介绍的主题</span><span class="sxs-lookup"><span data-stu-id="68e17-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="68e17-119">**控制器可视化**</span><span class="sxs-lookup"><span data-stu-id="68e17-119">**Controller visualization**</span></span>|<span data-ttu-id="68e17-120">**控制器输入事件**</span><span class="sxs-lookup"><span data-stu-id="68e17-120">**Controller input events**</span></span>|<span data-ttu-id="68e17-121">**自定义控制器和 UI**</span><span class="sxs-lookup"><span data-stu-id="68e17-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="68e17-122">了解如何在 Unity 的游戏模式和运行时中呈现运动控制器模型。</span><span class="sxs-lookup"><span data-stu-id="68e17-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="68e17-123">了解不同类型的按钮事件及其应用程序。</span><span class="sxs-lookup"><span data-stu-id="68e17-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="68e17-124">了解如何在控制器顶部覆盖 UI 元素或对其进行完全自定义。</span><span class="sxs-lookup"><span data-stu-id="68e17-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="68e17-125">设备支持</span><span class="sxs-lookup"><span data-stu-id="68e17-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="68e17-126">摘要</span><span class="sxs-lookup"><span data-stu-id="68e17-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="68e17-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="68e17-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="68e17-128"><a href="immersive-headset-hardware-details.md">沉浸式头戴显示设备</a></span><span class="sxs-lookup"><span data-stu-id="68e17-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="68e17-129">MR 输入 213:运动控制器</span><span class="sxs-lookup"><span data-stu-id="68e17-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="68e17-130">✔️</span><span class="sxs-lookup"><span data-stu-id="68e17-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="68e17-131">开始之前</span><span class="sxs-lookup"><span data-stu-id="68e17-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="68e17-132">先决条件</span><span class="sxs-lookup"><span data-stu-id="68e17-132">Prerequisites</span></span>

<span data-ttu-id="68e17-133">请参阅[本页上的](install-the-tools.md)沉浸式耳机安装清单。</span><span class="sxs-lookup"><span data-stu-id="68e17-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="68e17-134">本教程需要[Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="68e17-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="68e17-135">项目文件</span><span class="sxs-lookup"><span data-stu-id="68e17-135">Project files</span></span>

* <span data-ttu-id="68e17-136">下载项目所需[的文件](https://github.com/Microsoft/MixedReality213/archive/master.zip), 并将文件解压缩到桌面。</span><span class="sxs-lookup"><span data-stu-id="68e17-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="68e17-137">如果要在下载之前查看源代码,[可在 GitHub 上](https://github.com/Microsoft/MixedReality213)找到。</span><span class="sxs-lookup"><span data-stu-id="68e17-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="68e17-138">Unity 设置</span><span class="sxs-lookup"><span data-stu-id="68e17-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="68e17-139">目标</span><span class="sxs-lookup"><span data-stu-id="68e17-139">Objectives</span></span>

* <span data-ttu-id="68e17-140">优化 Unity 以实现 Windows Mixed Reality 开发</span><span class="sxs-lookup"><span data-stu-id="68e17-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="68e17-141">设置混合现实照相机</span><span class="sxs-lookup"><span data-stu-id="68e17-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="68e17-142">设置环境</span><span class="sxs-lookup"><span data-stu-id="68e17-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="68e17-143">说明</span><span class="sxs-lookup"><span data-stu-id="68e17-143">Instructions</span></span>

* <span data-ttu-id="68e17-144">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="68e17-144">Start Unity.</span></span>
* <span data-ttu-id="68e17-145">选择 "**打开**"。</span><span class="sxs-lookup"><span data-stu-id="68e17-145">Select **Open**.</span></span>
* <span data-ttu-id="68e17-146">导航到桌面并找到之前 unarchived 的**MixedReality213**文件夹。</span><span class="sxs-lookup"><span data-stu-id="68e17-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="68e17-147">单击“选择文件夹”。</span><span class="sxs-lookup"><span data-stu-id="68e17-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="68e17-148">Unity 完成加载项目文件后, 你将能够看到 Unity 编辑器。</span><span class="sxs-lookup"><span data-stu-id="68e17-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="68e17-149">在 Unity 中, 选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="68e17-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="68e17-151">选择 "**平台**" 列表中的 "**通用 Windows 平台**", 然后单击 "**切换平台**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="68e17-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="68e17-152">将目标设备设置为**任何设备**</span><span class="sxs-lookup"><span data-stu-id="68e17-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="68e17-153">将生成类型设置为**D3D**</span><span class="sxs-lookup"><span data-stu-id="68e17-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="68e17-154">将 SDK 设置为**安装的最新版本**</span><span class="sxs-lookup"><span data-stu-id="68e17-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="68e17-155">检查**Unity C#项目**</span><span class="sxs-lookup"><span data-stu-id="68e17-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="68e17-156">这样, 便可以修改 Visual Studio 项目中的脚本文件, 而无需重新生成 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="68e17-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="68e17-157">单击 "**播放机设置**"。</span><span class="sxs-lookup"><span data-stu-id="68e17-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="68e17-158">在 "**检查器**" 面板中, 向下滚动到底部</span><span class="sxs-lookup"><span data-stu-id="68e17-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="68e17-159">在 XR 设置中, 检查**支持的虚拟现实**</span><span class="sxs-lookup"><span data-stu-id="68e17-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="68e17-160">在虚拟现实 Sdk 下, 选择 " **Windows Mixed Reality** "</span><span class="sxs-lookup"><span data-stu-id="68e17-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="68e17-162">关闭 "**生成设置**" 窗口。</span><span class="sxs-lookup"><span data-stu-id="68e17-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="68e17-163">项目结构</span><span class="sxs-lookup"><span data-stu-id="68e17-163">Project structure</span></span>

<span data-ttu-id="68e17-164">本教程使用 **[混合现实工具包-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 。</span><span class="sxs-lookup"><span data-stu-id="68e17-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="68e17-165">可以在[此页](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)上找到发布。</span><span class="sxs-lookup"><span data-stu-id="68e17-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="68e17-167">**已完成用于引用的场景**</span><span class="sxs-lookup"><span data-stu-id="68e17-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="68e17-168">你会在**场景**文件夹中找到两个已完成的 Unity 场景。</span><span class="sxs-lookup"><span data-stu-id="68e17-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="68e17-169">**MixedReality213**:带有单一画笔的已完成场景</span><span class="sxs-lookup"><span data-stu-id="68e17-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="68e17-170">**MixedReality213Advanced**:针对具有多个画笔的高级设计完成的场景</span><span class="sxs-lookup"><span data-stu-id="68e17-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="68e17-171">**教程的新场景设置**</span><span class="sxs-lookup"><span data-stu-id="68e17-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="68e17-172">在 Unity 中, 单击 "**文件" > 新建场景**</span><span class="sxs-lookup"><span data-stu-id="68e17-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="68e17-173">删除**摄像机**和**方向灯**</span><span class="sxs-lookup"><span data-stu-id="68e17-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="68e17-174">在 "**项目" 面板**中, 搜索并将以下 prototyping 拖到 "**层次结构**" 面板中:</span><span class="sxs-lookup"><span data-stu-id="68e17-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="68e17-175">资产/HoloToolkit/Input/Prototyping/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="68e17-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="68e17-176">资产/AppPrefabs/**环境**</span><span class="sxs-lookup"><span data-stu-id="68e17-176">Assets/AppPrefabs/**Environment**</span></span>

![照相机和环境](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="68e17-178">混合现实工具包中有两个照相机 prototyping:</span><span class="sxs-lookup"><span data-stu-id="68e17-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="68e17-179">**MixedRealityCamera. prefab**:仅照相机</span><span class="sxs-lookup"><span data-stu-id="68e17-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="68e17-180">**MixedRealityCameraParent. prefab**:相机 + Teleportation + 边界</span><span class="sxs-lookup"><span data-stu-id="68e17-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="68e17-181">在本教程中, 我们将使用不带 teleportation 功能的**MixedRealityCamera** 。</span><span class="sxs-lookup"><span data-stu-id="68e17-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="68e17-182">为此, 我们添加了简单的**环境**prefab, 其中包含一个基本楼层, 使用户感觉不到接地。</span><span class="sxs-lookup"><span data-stu-id="68e17-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="68e17-183">若要了解有关 teleportation 与**MixedRealityCameraParent**的详细信息, 请参阅[高级设计-teleportation 和 locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="68e17-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="68e17-184">**Skybox 安装程序**</span><span class="sxs-lookup"><span data-stu-id="68e17-184">**Skybox setup**</span></span>
* <span data-ttu-id="68e17-185">单击 "**窗口" > 照明 > 设置**</span><span class="sxs-lookup"><span data-stu-id="68e17-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="68e17-186">单击**Skybox 材料字段**右侧的圆圈</span><span class="sxs-lookup"><span data-stu-id="68e17-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="68e17-187">键入 "灰色" 并选择**SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="68e17-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="68e17-188">(资产/AppPrefabs/支持/材料/SkyboxGray)</span><span class="sxs-lookup"><span data-stu-id="68e17-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![设置 skybox](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="68e17-190">检查**Skybox**选项以查看已分配的灰色渐变 Skybox</span><span class="sxs-lookup"><span data-stu-id="68e17-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![切换 skybox 选项](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="68e17-192">带有 MixedRealityCamera、环境和灰色 skybox 的场景将如下所示。</span><span class="sxs-lookup"><span data-stu-id="68e17-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213 环境](images/mr213-environment-600px.jpg)
* <span data-ttu-id="68e17-194">单击 "**文件" > 将场景另存为**</span><span class="sxs-lookup"><span data-stu-id="68e17-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="68e17-195">用任意名称**将场景保存**在场景文件夹下</span><span class="sxs-lookup"><span data-stu-id="68e17-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="68e17-196">第1章-控制器可视化</span><span class="sxs-lookup"><span data-stu-id="68e17-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="68e17-197">目标</span><span class="sxs-lookup"><span data-stu-id="68e17-197">Objectives</span></span>

* <span data-ttu-id="68e17-198">了解如何在 Unity 的游戏模式下和在运行时呈现运动控制器模型。</span><span class="sxs-lookup"><span data-stu-id="68e17-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="68e17-199">Windows Mixed Reality 提供适用于控制器可视化的动画控制器模型。</span><span class="sxs-lookup"><span data-stu-id="68e17-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="68e17-200">可在应用中使用以下几种方法来实现控制器可视化:</span><span class="sxs-lookup"><span data-stu-id="68e17-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="68e17-201">默认-使用默认控制器但不修改</span><span class="sxs-lookup"><span data-stu-id="68e17-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="68e17-202">混合-使用默认控制器, 但自定义其部分元素或覆盖 UI 组件</span><span class="sxs-lookup"><span data-stu-id="68e17-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="68e17-203">替换-将你自己的自定义3D 模型用于控制器</span><span class="sxs-lookup"><span data-stu-id="68e17-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="68e17-204">在本章中, 我们将了解这些控制器自定义的示例。</span><span class="sxs-lookup"><span data-stu-id="68e17-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="68e17-205">说明</span><span class="sxs-lookup"><span data-stu-id="68e17-205">Instructions</span></span>

* <span data-ttu-id="68e17-206">在 "**项目**" 面板的 "搜索" 框中, 键入**MotionControllers** 。</span><span class="sxs-lookup"><span data-stu-id="68e17-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="68e17-207">还可以在 "资产/HoloToolkit/输入/Prototyping/" 下找到它。</span><span class="sxs-lookup"><span data-stu-id="68e17-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="68e17-208">将**MotionControllers** prefab 拖到 "**层次结构**" 面板中。</span><span class="sxs-lookup"><span data-stu-id="68e17-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-209">单击 "**层次结构**" 面板中的**MotionControllers** prefab。</span><span class="sxs-lookup"><span data-stu-id="68e17-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="68e17-210">**MotionControllers prefab**</span><span class="sxs-lookup"><span data-stu-id="68e17-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="68e17-211">**MotionControllers** prefab 有一个**MotionControllerVisualizer**脚本, 该脚本提供备用控制器型号的槽。</span><span class="sxs-lookup"><span data-stu-id="68e17-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="68e17-212">如果您为自己的自定义3D 模型 (如手或剑) 指定了一个, 并选中 "始终使用备用的左/右模型", 则会看到它们, 而不是默认模型。</span><span class="sxs-lookup"><span data-stu-id="68e17-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="68e17-213">我们将在第4章中使用此槽, 用画笔替换控制器模型。</span><span class="sxs-lookup"><span data-stu-id="68e17-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="68e17-215">**说明**</span><span class="sxs-lookup"><span data-stu-id="68e17-215">**Instructions**</span></span>
* <span data-ttu-id="68e17-216">在 "**检查器**" 面板中, 双击 " **MotionControllerVisualizer** Script" 以查看 Visual Studio 中的代码</span><span class="sxs-lookup"><span data-stu-id="68e17-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="68e17-217">**MotionControllerVisualizer 脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="68e17-218">**MotionControllerVisualizer**和**MotionControllerInfo**类提供访问 & 修改默认控制器模型的方法。</span><span class="sxs-lookup"><span data-stu-id="68e17-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="68e17-219">**MotionControllerVisualizer**订阅 Unity 的**InteractionSourceDetected**事件, 并在发现控制器模型时自动将其实例化。</span><span class="sxs-lookup"><span data-stu-id="68e17-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="68e17-220">控制器模型是根据[glTF 规范](https://github.com/KhronosGroup/glTF)传递的。</span><span class="sxs-lookup"><span data-stu-id="68e17-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="68e17-221">创建此格式是为了提供通用格式, 同时改进了在传输和解包3D 资产后的过程。</span><span class="sxs-lookup"><span data-stu-id="68e17-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="68e17-222">在这种情况下, 我们需要在运行时检索并加载控制器模型, 因为我们希望尽可能使用户体验尽可能顺畅, 并不保证用户可能正在使用的运动控制器版本。</span><span class="sxs-lookup"><span data-stu-id="68e17-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="68e17-223">本课程通过混合现实工具包使用 Khronos 组的[UnityGLTF 项目](https://github.com/KhronosGroup/UnityGLTF)版本。</span><span class="sxs-lookup"><span data-stu-id="68e17-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="68e17-224">提供控制器后, 脚本可以使用**MotionControllerInfo**查找特定控制器元素的转换, 以便它们可以正确定位。</span><span class="sxs-lookup"><span data-stu-id="68e17-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="68e17-225">在后面的章节中, 我们将了解如何使用这些脚本将 UI 元素附加到控制器。</span><span class="sxs-lookup"><span data-stu-id="68e17-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="68e17-226">*在某些脚本中, 你将找到带有 #if 的代码块 **!UNITY_EDITOR**或**UNITY_WSA**。这些代码块仅在部署到 Windows 时在 UWP 运行时上运行。这是因为 Unity 编辑器和 UWP 应用运行时所使用的 Api 集是不同的。*</span><span class="sxs-lookup"><span data-stu-id="68e17-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="68e17-227">**保存**场景并单击 "**播放**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="68e17-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="68e17-228">你将能够在耳机中看到带有运动控制器的场景。</span><span class="sxs-lookup"><span data-stu-id="68e17-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="68e17-229">可以查看按钮单击、操纵杆运动和触摸板触摸突出显示的详细动画。</span><span class="sxs-lookup"><span data-stu-id="68e17-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller 可视化默认值](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="68e17-231">第2章-将 UI 元素附加到控制器</span><span class="sxs-lookup"><span data-stu-id="68e17-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="68e17-232">目标</span><span class="sxs-lookup"><span data-stu-id="68e17-232">Objectives</span></span>

* <span data-ttu-id="68e17-233">了解运动控制器的元素</span><span class="sxs-lookup"><span data-stu-id="68e17-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="68e17-234">了解如何将对象附加到控制器的特定部分</span><span class="sxs-lookup"><span data-stu-id="68e17-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="68e17-235">在本章中, 你将学习如何将用户界面元素添加到用户可随时轻松访问和操作的控制器。</span><span class="sxs-lookup"><span data-stu-id="68e17-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="68e17-236">你还将了解如何使用触摸板输入添加简单的颜色选取器 UI。</span><span class="sxs-lookup"><span data-stu-id="68e17-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="68e17-237">说明</span><span class="sxs-lookup"><span data-stu-id="68e17-237">Instructions</span></span>

* <span data-ttu-id="68e17-238">在 "**项目**" 面板中, 搜索 " **MotionControllerInfo** script"。</span><span class="sxs-lookup"><span data-stu-id="68e17-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="68e17-239">在搜索结果中, 双击 " **MotionControllerInfo** script" 以查看 Visual Studio 中的代码。</span><span class="sxs-lookup"><span data-stu-id="68e17-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="68e17-240">**MotionControllerInfo 脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="68e17-241">第一步是选择要将 UI 附加到的控制器的元素。</span><span class="sxs-lookup"><span data-stu-id="68e17-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="68e17-242">这些元素在**MotionControllerInfo.cs**的**ControllerElementEnum**中定义。</span><span class="sxs-lookup"><span data-stu-id="68e17-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="68e17-244">**主页**</span><span class="sxs-lookup"><span data-stu-id="68e17-244">**Home**</span></span>
* <span data-ttu-id="68e17-245">**菜单**</span><span class="sxs-lookup"><span data-stu-id="68e17-245">**Menu**</span></span>
* <span data-ttu-id="68e17-246">**掌握**</span><span class="sxs-lookup"><span data-stu-id="68e17-246">**Grasp**</span></span>
* <span data-ttu-id="68e17-247">**控制**</span><span class="sxs-lookup"><span data-stu-id="68e17-247">**Thumbstick**</span></span>
* <span data-ttu-id="68e17-248">**单击**</span><span class="sxs-lookup"><span data-stu-id="68e17-248">**Select**</span></span>
* <span data-ttu-id="68e17-249">**触摸板**</span><span class="sxs-lookup"><span data-stu-id="68e17-249">**Touchpad**</span></span>
* <span data-ttu-id="68e17-250">**指针姿势**–此元素表示控制器向后方向的笔尖。</span><span class="sxs-lookup"><span data-stu-id="68e17-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="68e17-251">**说明**</span><span class="sxs-lookup"><span data-stu-id="68e17-251">**Instructions**</span></span>
* <span data-ttu-id="68e17-252">在 "**项目**" 面板中, 搜索 " **AttachToController** script"。</span><span class="sxs-lookup"><span data-stu-id="68e17-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="68e17-253">在搜索结果中, 双击 " **AttachToController** script" 以查看 Visual Studio 中的代码。</span><span class="sxs-lookup"><span data-stu-id="68e17-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="68e17-254">**AttachToController 脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-254">**AttachToController script**</span></span>

<span data-ttu-id="68e17-255">**AttachToController**脚本提供了一种简单的方法, 可将任何对象附加到指定的控制器左右手使用习惯和元素。</span><span class="sxs-lookup"><span data-stu-id="68e17-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="68e17-256">在**AttachElementToController ()** 中,</span><span class="sxs-lookup"><span data-stu-id="68e17-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="68e17-257">使用 MotionControllerInfo 检查左右手使用习惯 **。左右手使用习惯**</span><span class="sxs-lookup"><span data-stu-id="68e17-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="68e17-258">使用**MotionControllerInfo. TryGetElement ()** 获取控制器的特定元素</span><span class="sxs-lookup"><span data-stu-id="68e17-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="68e17-259">从控制器模型检索该元素的转换后, 将其父对象置于其下, 并将对象的本地位置 & 旋转到零。</span><span class="sxs-lookup"><span data-stu-id="68e17-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="68e17-260">使用**AttachToController**脚本的最简单方法是从其继承, 就像我们在 ColorPickerWheel 的情况下所做的那样 **。**</span><span class="sxs-lookup"><span data-stu-id="68e17-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="68e17-261">只需重写**OnAttachToController**和**OnDetatchFromController**函数, 以便在检测到控制器/断开连接时执行设置/细分。</span><span class="sxs-lookup"><span data-stu-id="68e17-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="68e17-262">**说明**</span><span class="sxs-lookup"><span data-stu-id="68e17-262">**Instructions**</span></span>
* <span data-ttu-id="68e17-263">在 "**项目**" 面板的 "搜索" 框中键入**ColorPickerWheel**。</span><span class="sxs-lookup"><span data-stu-id="68e17-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="68e17-264">还可以在 "资产/AppPrefabs/" 下找到它。</span><span class="sxs-lookup"><span data-stu-id="68e17-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="68e17-265">将**ColorPickerWheel** prefab 拖到 "**层次结构**" 面板中。</span><span class="sxs-lookup"><span data-stu-id="68e17-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-266">单击 "**层次结构**" 面板中的**ColorPickerWheel** prefab。</span><span class="sxs-lookup"><span data-stu-id="68e17-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-267">在 "**检查器**" 面板中, 双击 " **ColorPickerWheel** Script" 以查看 Visual Studio 中的代码。</span><span class="sxs-lookup"><span data-stu-id="68e17-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="68e17-269">**ColorPickerWheel 脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="68e17-270">由于**ColorPickerWheel**继承**了 AttachToController**, 它会在 "**检查器**" 面板中显示**左右手使用习惯**和**元素**。</span><span class="sxs-lookup"><span data-stu-id="68e17-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="68e17-271">我们会将 UI 附加到左侧控制器上的触摸板元素。</span><span class="sxs-lookup"><span data-stu-id="68e17-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![ColorPickerWheel 脚本](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="68e17-273">**ColorPickerWheel**重写**OnAttachToController**和**OnDetatchFromController**以订阅输入事件, 此事件将在下一章中用于使用触摸板输入的颜色选择。</span><span class="sxs-lookup"><span data-stu-id="68e17-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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
* <span data-ttu-id="68e17-274">**保存**场景并单击 "**播放**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="68e17-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="68e17-275">**将对象附加到控制器的替代方法**</span><span class="sxs-lookup"><span data-stu-id="68e17-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="68e17-276">建议你的脚本继承自**AttachToController** , 并重写**OnAttachToController**。</span><span class="sxs-lookup"><span data-stu-id="68e17-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="68e17-277">但这并不总是可行。</span><span class="sxs-lookup"><span data-stu-id="68e17-277">However, this may not always be possible.</span></span> <span data-ttu-id="68e17-278">替代方法是将其用作独立组件。</span><span class="sxs-lookup"><span data-stu-id="68e17-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="68e17-279">如果要将现有的 prefab 附加到控制器而不重构脚本, 这会很有用。</span><span class="sxs-lookup"><span data-stu-id="68e17-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="68e17-280">只需将 IsAttached 设置为 true, 然后再执行任何设置。</span><span class="sxs-lookup"><span data-stu-id="68e17-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="68e17-281">执行此操作的最简单方法是使用协同程序作为 "Start"。</span><span class="sxs-lookup"><span data-stu-id="68e17-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="68e17-282">第3章-使用触摸板输入</span><span class="sxs-lookup"><span data-stu-id="68e17-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="68e17-283">目标</span><span class="sxs-lookup"><span data-stu-id="68e17-283">Objectives</span></span>

* <span data-ttu-id="68e17-284">了解如何获取触摸板输入数据事件</span><span class="sxs-lookup"><span data-stu-id="68e17-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="68e17-285">了解如何将触摸板轴位置信息用于应用体验</span><span class="sxs-lookup"><span data-stu-id="68e17-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="68e17-286">说明</span><span class="sxs-lookup"><span data-stu-id="68e17-286">Instructions</span></span>

* <span data-ttu-id="68e17-287">在 "**层次结构**" 面板中, 单击 " **ColorPickerWheel** "</span><span class="sxs-lookup"><span data-stu-id="68e17-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="68e17-288">在 "**检查器**" 面板中的 " **Animatior**" 下, 双击 " **ColorPickerWheelController** "</span><span class="sxs-lookup"><span data-stu-id="68e17-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="68e17-289">你将能够看到 " **Animator** " 选项卡已打开</span><span class="sxs-lookup"><span data-stu-id="68e17-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="68e17-290">**显示/隐藏具有 Unity 动画控制器的 UI**</span><span class="sxs-lookup"><span data-stu-id="68e17-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="68e17-291">若要显示和隐藏带有动画的**ColorPickerWheel** UI, 我们使用[的是 Unity 的动画系统](https://docs.unity3d.com/Manual/AnimationOverview.html)。</span><span class="sxs-lookup"><span data-stu-id="68e17-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="68e17-292">如果将**ColorPickerWheel**的**Visible**属性设置为 true 或 False, 则将**显示**和**隐藏**动画触发器。</span><span class="sxs-lookup"><span data-stu-id="68e17-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="68e17-293">在**ColorPickerWheelController**动画控制器中定义了**显示**和**隐藏**参数。</span><span class="sxs-lookup"><span data-stu-id="68e17-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity 动画控制器](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="68e17-295">**说明**</span><span class="sxs-lookup"><span data-stu-id="68e17-295">**Instructions**</span></span>
* <span data-ttu-id="68e17-296">在 "**层次结构**" 面板中, 选择**ColorPickerWheel** prefab</span><span class="sxs-lookup"><span data-stu-id="68e17-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="68e17-297">在 "**检查器**" 面板中, 双击 " **ColorPickerWheel** Script" 以查看 Visual Studio 中的代码</span><span class="sxs-lookup"><span data-stu-id="68e17-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="68e17-298">**ColorPickerWheel 脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="68e17-299">**ColorPickerWheel**订阅 Unity 的**InteractionSourceUpdated**事件来侦听触摸板事件。</span><span class="sxs-lookup"><span data-stu-id="68e17-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="68e17-300">在**InteractionSourceUpdated ()** 中, 脚本首先检查以确保:</span><span class="sxs-lookup"><span data-stu-id="68e17-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="68e17-301">实际上是一个触摸板事件 (.obj. 状态。**touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="68e17-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="68e17-302">源自左侧控制器 (.obj. 状态 **。左右手使用习惯**)</span><span class="sxs-lookup"><span data-stu-id="68e17-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="68e17-303">如果两者都为 true, 则表示触摸板位置 (.obj. 状态。**touchpadPosition**) 分配给**selectorPosition**。</span><span class="sxs-lookup"><span data-stu-id="68e17-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="68e17-304">在**Update ()** 中, 根据**Visible**属性触发显示和隐藏颜色选取器的 animator 组件中的动画触发器</span><span class="sxs-lookup"><span data-stu-id="68e17-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="68e17-305">在**Update ()** 中, **selectorPosition**用于在色轮的网格碰撞器上强制转换射线, 这将返回一个 UV 位置。</span><span class="sxs-lookup"><span data-stu-id="68e17-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="68e17-306">然后, 可以使用此位置查找色轮纹理的像素坐标和颜色值。</span><span class="sxs-lookup"><span data-stu-id="68e17-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="68e17-307">其他脚本可以通过**SelectedColor**属性访问此值。</span><span class="sxs-lookup"><span data-stu-id="68e17-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![颜色选取器轮 Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="68e17-309">第4章-覆盖控制器模型</span><span class="sxs-lookup"><span data-stu-id="68e17-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="68e17-310">目标</span><span class="sxs-lookup"><span data-stu-id="68e17-310">Objectives</span></span>

* <span data-ttu-id="68e17-311">了解如何使用自定义3D 模型替代控制器模型。</span><span class="sxs-lookup"><span data-stu-id="68e17-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="68e17-313">说明</span><span class="sxs-lookup"><span data-stu-id="68e17-313">Instructions</span></span>

* <span data-ttu-id="68e17-314">在 "**层次结构**" 面板中单击 " **MotionControllers** "。</span><span class="sxs-lookup"><span data-stu-id="68e17-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-315">单击**替换右侧控制器**字段右侧的圆圈。</span><span class="sxs-lookup"><span data-stu-id="68e17-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="68e17-316">键入 **"BrushController**", 并从结果中选择 prefab。</span><span class="sxs-lookup"><span data-stu-id="68e17-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="68e17-317">可以在 "资产/AppPrefabs/**BrushController**" 下找到它。</span><span class="sxs-lookup"><span data-stu-id="68e17-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="68e17-318">选中 "**始终使用备用模式**"</span><span class="sxs-lookup"><span data-stu-id="68e17-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="68e17-320">不需要在**层次结构**面板中包含**BrushController** prefab。</span><span class="sxs-lookup"><span data-stu-id="68e17-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="68e17-321">但是, 若要查看子组件, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="68e17-321">However, to check out its child components:</span></span>
* <span data-ttu-id="68e17-322">在 "**项目**" 面板中, 键入**BrushController**并将**BrushController** prefab 拖到 "**层次结构**" 面板中。</span><span class="sxs-lookup"><span data-stu-id="68e17-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="68e17-324">你会在**BrushController**中找到**Tip**组件。</span><span class="sxs-lookup"><span data-stu-id="68e17-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="68e17-325">我们将使用其转换来启动/停止绘制线条。</span><span class="sxs-lookup"><span data-stu-id="68e17-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="68e17-326">从**层次结构**面板中删除**BrushController** 。</span><span class="sxs-lookup"><span data-stu-id="68e17-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-327">**保存**场景并单击 "**播放**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="68e17-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="68e17-328">你将能够看到画笔模型已替换右手运动控制器。</span><span class="sxs-lookup"><span data-stu-id="68e17-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="68e17-329">第5章-用选择输入进行绘制</span><span class="sxs-lookup"><span data-stu-id="68e17-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="68e17-330">目标</span><span class="sxs-lookup"><span data-stu-id="68e17-330">Objectives</span></span>

* <span data-ttu-id="68e17-331">了解如何使用 "选择按钮" 事件来启动和停止线条绘制</span><span class="sxs-lookup"><span data-stu-id="68e17-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="68e17-332">说明</span><span class="sxs-lookup"><span data-stu-id="68e17-332">Instructions</span></span>

* <span data-ttu-id="68e17-333">在 "**项目**" 面板中搜索**BrushController** prefab。</span><span class="sxs-lookup"><span data-stu-id="68e17-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="68e17-334">在 "**检查器**" 面板中, 双击 " **BrushController** Script" 以查看 Visual Studio 中的代码</span><span class="sxs-lookup"><span data-stu-id="68e17-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="68e17-335">**BrushController 脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-335">**BrushController script**</span></span>

<span data-ttu-id="68e17-336">**BrushController**订阅 InteractionManager 的**InteractionSourcePressed**和**InteractionSourceReleased**事件。</span><span class="sxs-lookup"><span data-stu-id="68e17-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="68e17-337">触发**InteractionSourcePressed**事件后, 画笔的**Draw**属性将设置为 true;触发**InteractionSourceReleased**事件后, 画笔的**Draw**属性将设置为 false。</span><span class="sxs-lookup"><span data-stu-id="68e17-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="68e17-338">**绘图**设置为 true 时, 画笔将在实例化的 Unity **LineRenderer**中生成点。</span><span class="sxs-lookup"><span data-stu-id="68e17-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="68e17-339">对此 prefab 的引用将保存在画笔的**Stroke prefab**字段中。</span><span class="sxs-lookup"><span data-stu-id="68e17-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="68e17-340">若要从颜色选取器滚轮 UI 使用当前选定的颜色, **BrushController**需要具有对**ColorPickerWheel**对象的引用。</span><span class="sxs-lookup"><span data-stu-id="68e17-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="68e17-341">因为在运行时将**BrushController** prefab 实例化为替换控制器, 所以必须在运行时设置对场景中对象的任何引用。</span><span class="sxs-lookup"><span data-stu-id="68e17-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="68e17-342">在此示例中, 我们使用**GameObject**来查找**ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="68e17-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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
* <span data-ttu-id="68e17-343">**保存**场景并单击 "**播放**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="68e17-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="68e17-344">你将能够使用右侧控制器上的 "选择" 按钮绘制线条并进行绘制。</span><span class="sxs-lookup"><span data-stu-id="68e17-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="68e17-345">第6章-带有选择输入的对象生成</span><span class="sxs-lookup"><span data-stu-id="68e17-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="68e17-346">目标</span><span class="sxs-lookup"><span data-stu-id="68e17-346">Objectives</span></span>

* <span data-ttu-id="68e17-347">了解如何使用 "选择并抓住" 按钮输入事件</span><span class="sxs-lookup"><span data-stu-id="68e17-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="68e17-348">了解如何实例化对象</span><span class="sxs-lookup"><span data-stu-id="68e17-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="68e17-349">说明</span><span class="sxs-lookup"><span data-stu-id="68e17-349">Instructions</span></span>

* <span data-ttu-id="68e17-350">在 "**项目**" 面板的 "搜索" 框中, 键入**ObjectSpawner** 。</span><span class="sxs-lookup"><span data-stu-id="68e17-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="68e17-351">还可以在 "资产/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="68e17-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="68e17-352">将**ObjectSpawner** prefab 拖到 "**层次结构**" 面板中。</span><span class="sxs-lookup"><span data-stu-id="68e17-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-353">在 "**层次结构**" 面板中单击 " **ObjectSpawner** "。</span><span class="sxs-lookup"><span data-stu-id="68e17-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-354">**ObjectSpawner**有一个名为 "**颜色源**" 的字段。</span><span class="sxs-lookup"><span data-stu-id="68e17-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="68e17-355">从 "**层次结构**" 面板中, 将 " **ColorPickerWheel** " 引用拖到此字段中。</span><span class="sxs-lookup"><span data-stu-id="68e17-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![对象 Spawner 检查器](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="68e17-357">单击 "**层次结构**" 面板中的**ObjectSpawner** prefab。</span><span class="sxs-lookup"><span data-stu-id="68e17-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-358">在 "**检查器**" 面板中, 双击 " **ObjectSpawner** Script" 以查看 Visual Studio 中的代码。</span><span class="sxs-lookup"><span data-stu-id="68e17-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="68e17-359">**ObjectSpawner 脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="68e17-360">**ObjectSpawner**将基元网格 (cube, 圆柱体) 的副本实例化为空间。</span><span class="sxs-lookup"><span data-stu-id="68e17-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="68e17-361">检测到**InteractionSourcePressed**时, 它会检查左右手使用习惯, 并检查其是否为**InteractionSourcePressType**或**InteractionSourcePressType。**</span><span class="sxs-lookup"><span data-stu-id="68e17-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="68e17-362">对于**抓住**事件, 它会递增当前网格类型 (球、cube、圆柱) 的索引</span><span class="sxs-lookup"><span data-stu-id="68e17-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="68e17-363">对于**Select**事件, 在**SpawnObject ()** 中, 将实例化新的对象, 并将其作为父级并将其发布到世界。</span><span class="sxs-lookup"><span data-stu-id="68e17-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

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

<span data-ttu-id="68e17-364">**ObjectSpawner**使用**ColorPickerWheel**设置显示对象材料的颜色。</span><span class="sxs-lookup"><span data-stu-id="68e17-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="68e17-365">将为生成的对象提供此材料的实例, 以使它们保留其颜色。</span><span class="sxs-lookup"><span data-stu-id="68e17-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="68e17-366">**保存**场景并单击 "**播放**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="68e17-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="68e17-367">你将能够通过 "抓住" 按钮更改对象, 并通过 "选择" 按钮生成对象。</span><span class="sxs-lookup"><span data-stu-id="68e17-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="68e17-368">构建应用并将其部署到混合现实门户</span><span class="sxs-lookup"><span data-stu-id="68e17-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="68e17-369">在 Unity 中, 选择 "**文件 > 生成设置**"。</span><span class="sxs-lookup"><span data-stu-id="68e17-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="68e17-370">单击 "**添加打开的场景**", 将当前场景添加到**生成的场景中**。</span><span class="sxs-lookup"><span data-stu-id="68e17-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="68e17-371">单击“生成” 。</span><span class="sxs-lookup"><span data-stu-id="68e17-371">Click **Build**.</span></span>
* <span data-ttu-id="68e17-372">创建名为 "App" 的**新文件夹**。</span><span class="sxs-lookup"><span data-stu-id="68e17-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="68e17-373">单击**应用**文件夹。</span><span class="sxs-lookup"><span data-stu-id="68e17-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="68e17-374">单击“选择文件夹”。</span><span class="sxs-lookup"><span data-stu-id="68e17-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="68e17-375">当 Unity 完成后, 将显示文件资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="68e17-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="68e17-376">打开**应用程序**文件夹。</span><span class="sxs-lookup"><span data-stu-id="68e17-376">Open the **App** folder.</span></span>
* <span data-ttu-id="68e17-377">双击 " **YourSceneName** " Visual Studio 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="68e17-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="68e17-378">使用 Visual Studio 中的顶部工具栏, 将目标从 "调试" 更改为 "**发布**", 将 "从 ARM" 更改为 " **X64**"。</span><span class="sxs-lookup"><span data-stu-id="68e17-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="68e17-379">单击 "设备" 按钮旁边的下拉箭头, 然后选择 "**本地计算机**"。</span><span class="sxs-lookup"><span data-stu-id="68e17-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="68e17-380">单击菜单中的 "**调试-> 启动但不调试**", 或按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="68e17-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="68e17-381">现在, 在混合现实门户中生成并安装应用。</span><span class="sxs-lookup"><span data-stu-id="68e17-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="68e17-382">可以通过混合现实门户中的 "开始" 菜单再次启动它。</span><span class="sxs-lookup"><span data-stu-id="68e17-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="68e17-383">高级设计-具有径向布局的画笔工具</span><span class="sxs-lookup"><span data-stu-id="68e17-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="68e17-385">在本章中, 你将学习如何将默认运动控制器模型替换为自定义画笔工具集合。</span><span class="sxs-lookup"><span data-stu-id="68e17-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="68e17-386">对于引用, 可以在 "**场景**" 文件夹下找到已完成的场景**MixedReality213Advanced** 。</span><span class="sxs-lookup"><span data-stu-id="68e17-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="68e17-387">说明</span><span class="sxs-lookup"><span data-stu-id="68e17-387">Instructions</span></span>

* <span data-ttu-id="68e17-388">在 "**项目**" 面板的 "搜索" 框中, 键入**BrushSelector** 。</span><span class="sxs-lookup"><span data-stu-id="68e17-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="68e17-389">还可以在 "资产/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="68e17-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="68e17-390">将**BrushSelector** prefab 拖到 "**层次结构**" 面板中。</span><span class="sxs-lookup"><span data-stu-id="68e17-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-391">对于组织, 创建名为 "**画笔**" 的空 GameObject</span><span class="sxs-lookup"><span data-stu-id="68e17-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="68e17-392">将以下 prototyping 从 "**项目**" 面板拖到 "**画笔**"</span><span class="sxs-lookup"><span data-stu-id="68e17-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="68e17-393">资产/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="68e17-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="68e17-394">资产/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="68e17-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="68e17-395">资产/AppPrefabs/**橡皮擦**</span><span class="sxs-lookup"><span data-stu-id="68e17-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="68e17-396">资产/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="68e17-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="68e17-397">资产/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="68e17-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="68e17-398">资产/AppPrefabs/**铅笔**</span><span class="sxs-lookup"><span data-stu-id="68e17-398">Assets/AppPrefabs/**Pencil**</span></span>

![画笔](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="68e17-400">在 "**层次结构**" 面板中单击 " **MotionControllers** prefab"。</span><span class="sxs-lookup"><span data-stu-id="68e17-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="68e17-401">在 "**检查器**" 面板中, 取消选中 "在**运动控制器可视化工具**上**始终使用替代右模型**"</span><span class="sxs-lookup"><span data-stu-id="68e17-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="68e17-402">在 "**层次结构**" 面板中, 单击 " **BrushSelector** "</span><span class="sxs-lookup"><span data-stu-id="68e17-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="68e17-403">**BrushSelector**有一个名为**ColorPicker**的字段</span><span class="sxs-lookup"><span data-stu-id="68e17-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="68e17-404">从 "**层次结构**" 面板中, 将 " **ColorPickerWheel** " 拖动到**检查器**面板中的 " **ColorPicker** " 字段。</span><span class="sxs-lookup"><span data-stu-id="68e17-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![将 ColorPickerWheel 分配给画笔选择器](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="68e17-406">在 "**层次结构**" 面板中的 " **BrushSelector** prefab" 下, 选择 " **Menu** " 对象。</span><span class="sxs-lookup"><span data-stu-id="68e17-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="68e17-407">在 "**检查器**" 面板中的**LineObjectCollection**组件下, 打开 "**对象**数组" 下拉列表。</span><span class="sxs-lookup"><span data-stu-id="68e17-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="68e17-408">你将看到6个空槽。</span><span class="sxs-lookup"><span data-stu-id="68e17-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="68e17-409">从 "**层次结构**" 面板中, 将 "**画笔**" 下的每个 prototyping 父级以任意顺序拖动到这些槽。</span><span class="sxs-lookup"><span data-stu-id="68e17-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="68e17-410">(请确保从场景中拖动 prototyping, 而不是项目文件夹中的 prototyping。)</span><span class="sxs-lookup"><span data-stu-id="68e17-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![画笔选择器](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="68e17-412">**BrushSelector prefab**</span><span class="sxs-lookup"><span data-stu-id="68e17-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="68e17-413">由于**BrushSelector**继承了**AttachToController**, 它将在 "**检查器**" 面板中显示**左右手使用习惯**和**元素**选项。</span><span class="sxs-lookup"><span data-stu-id="68e17-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="68e17-414">我们选择了 "**向右** **" 并将**画笔工具连接到右侧的右控制器。</span><span class="sxs-lookup"><span data-stu-id="68e17-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="68e17-415">**BrushSelector**利用了两个实用工具:</span><span class="sxs-lookup"><span data-stu-id="68e17-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="68e17-416">**椭圆形**: 用于沿椭圆形状生成空间中的点。</span><span class="sxs-lookup"><span data-stu-id="68e17-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="68e17-417">**LineObjectCollection**: 使用由任意直线类 (例如, 椭圆形) 生成的点来分配对象。</span><span class="sxs-lookup"><span data-stu-id="68e17-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="68e17-418">这就是我们用来沿椭圆形状放置画笔的内容。</span><span class="sxs-lookup"><span data-stu-id="68e17-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="68e17-419">结合使用时, 可以使用这些实用程序创建放射状菜单。</span><span class="sxs-lookup"><span data-stu-id="68e17-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="68e17-420">**LineObjectCollection 脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="68e17-421">**LineObjectCollection**具有控件沿行分布的对象的大小、位置和旋转。</span><span class="sxs-lookup"><span data-stu-id="68e17-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="68e17-422">这对于创建径向菜单 (如画笔选择器) 很有用。</span><span class="sxs-lookup"><span data-stu-id="68e17-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="68e17-423">若要创建画笔的外观, 使其在接近中心选定位置的情况下进行缩放, **ObjectScale**曲线会在中心处峰值, 并在边缘处关闭 tapers。</span><span class="sxs-lookup"><span data-stu-id="68e17-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="68e17-424">**BrushSelector 脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-424">**BrushSelector script**</span></span>

<span data-ttu-id="68e17-425">对于**BrushSelector**, 我们选择了使用过程动画。</span><span class="sxs-lookup"><span data-stu-id="68e17-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="68e17-426">首先, 画笔模型由**LineObjectCollection**脚本分布在一个椭圆中。</span><span class="sxs-lookup"><span data-stu-id="68e17-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="68e17-427">然后, 每个画笔负责根据其**DisplayMode**值来维护其在用户的手边, 这会根据所选内容进行更改。</span><span class="sxs-lookup"><span data-stu-id="68e17-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="68e17-428">我们选择了过程方法, 因为当用户选择画笔时, 画笔位置转换的概率很高。</span><span class="sxs-lookup"><span data-stu-id="68e17-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="68e17-429">Mecanim 动画可以合理地处理中断, 但比简单的 Lerp 操作要复杂得多。</span><span class="sxs-lookup"><span data-stu-id="68e17-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="68e17-430">**BrushSelector**结合使用这两种方法。</span><span class="sxs-lookup"><span data-stu-id="68e17-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="68e17-431">检测到触摸板输入后, 画笔选项将变为可见, 并沿径向菜单向上缩放。</span><span class="sxs-lookup"><span data-stu-id="68e17-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="68e17-432">超时期限 (指示用户进行了选择) 之后, 画笔选项将再次缩小, 只留下所选的画笔。</span><span class="sxs-lookup"><span data-stu-id="68e17-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="68e17-433">**可视化触摸板输入**</span><span class="sxs-lookup"><span data-stu-id="68e17-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="68e17-434">即使在完全替换控制器模型的情况下, 显示原始模型输入的输入也可能会很有帮助。</span><span class="sxs-lookup"><span data-stu-id="68e17-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="68e17-435">这有助于使用户的操作成为现实。</span><span class="sxs-lookup"><span data-stu-id="68e17-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="68e17-436">对于**BrushSelector** , 我们选择了在收到输入时使触摸板短暂可见。</span><span class="sxs-lookup"><span data-stu-id="68e17-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="68e17-437">这是通过从控制器检索触摸板元素, 将其材料替换为自定义材料, 然后根据收到的触摸板输入的最后时间向该材料的颜色应用渐变来完成的。</span><span class="sxs-lookup"><span data-stu-id="68e17-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="68e17-438">**带有触摸板输入的画笔工具选择**</span><span class="sxs-lookup"><span data-stu-id="68e17-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="68e17-439">当画笔选择器检测到触摸板的按下输入时, 它将检查输入的位置以确定其是否在左侧或右侧。</span><span class="sxs-lookup"><span data-stu-id="68e17-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="68e17-440">**笔划粗细与 selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="68e17-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="68e17-441">可以通过**selectPressedAmount**获取按下量的模拟值, 而不是**InteractionSourcePressed ()** 中的**InteractionSourcePressType 事件。**</span><span class="sxs-lookup"><span data-stu-id="68e17-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="68e17-442">可以在**InteractionSourceUpdated ()** 中检索此值。</span><span class="sxs-lookup"><span data-stu-id="68e17-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="68e17-443">**橡皮擦脚本**</span><span class="sxs-lookup"><span data-stu-id="68e17-443">**Eraser script**</span></span>

<span data-ttu-id="68e17-444">**橡皮擦**是一种特殊类型的画笔, 用于重写基**画笔**的**DrawOverTime ()** 函数。</span><span class="sxs-lookup"><span data-stu-id="68e17-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="68e17-445">绘图为 true 时, 橡皮擦检查其刀尖是否与任何现有画笔笔划相交。</span><span class="sxs-lookup"><span data-stu-id="68e17-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="68e17-446">如果已添加到队列中, 则会将它们添加到要缩减和删除的队列中。</span><span class="sxs-lookup"><span data-stu-id="68e17-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="68e17-447">高级设计-Teleportation 和 locomotion</span><span class="sxs-lookup"><span data-stu-id="68e17-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="68e17-448">如果要允许用户使用 teleportation 在场景周围移动, 请使用**MixedRealityCameraParent**而不是**MixedRealityCamera**。</span><span class="sxs-lookup"><span data-stu-id="68e17-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="68e17-449">还需要添加**InputManager**和**DefaultCusor**。</span><span class="sxs-lookup"><span data-stu-id="68e17-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="68e17-450">由于**MixedRealityCameraParent**已将**MotionControllers**和**边界**包含为子组件, 因此应该删除现有的**MotionControllers**和**环境**prefab。</span><span class="sxs-lookup"><span data-stu-id="68e17-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="68e17-451">说明</span><span class="sxs-lookup"><span data-stu-id="68e17-451">Instructions</span></span>

* <span data-ttu-id="68e17-452">在**层次结构**面板中删除 **"MixedRealityCamera**"、"**环境**" 和 " **MotionControllers** "</span><span class="sxs-lookup"><span data-stu-id="68e17-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="68e17-453">在 "**项目" 面板**中, 搜索并将以下 prototyping 拖到 "**层次结构**" 面板中:</span><span class="sxs-lookup"><span data-stu-id="68e17-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="68e17-454">资产/AppPrefabs/Input/Prototyping/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="68e17-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="68e17-455">资产/AppPrefabs/Input/Prototyping/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="68e17-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="68e17-456">资产/AppPrefabs/Input/Prototyping/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="68e17-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![混合现实相机父项](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="68e17-458">在**层次结构**面板中, 单击 "**输入管理器**"</span><span class="sxs-lookup"><span data-stu-id="68e17-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="68e17-459">在 "**检查器**" 面板中, 向下滚动到**简单的单指针选择器**部分</span><span class="sxs-lookup"><span data-stu-id="68e17-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="68e17-460">从 "**层次结构**" 面板中, 将**DefaultCursor**拖到**Cursor**字段</span><span class="sxs-lookup"><span data-stu-id="68e17-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![分配 DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="68e17-462">**保存**场景并单击 "**播放**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="68e17-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="68e17-463">你将能够使用操纵杆向左或向右旋转。</span><span class="sxs-lookup"><span data-stu-id="68e17-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="68e17-464">结束</span><span class="sxs-lookup"><span data-stu-id="68e17-464">The end</span></span>

<span data-ttu-id="68e17-465">这就是本教程的结尾!</span><span class="sxs-lookup"><span data-stu-id="68e17-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="68e17-466">已学习:</span><span class="sxs-lookup"><span data-stu-id="68e17-466">You learned:</span></span>
* <span data-ttu-id="68e17-467">如何使用 Unity 的游戏模式和运行时中的运动控制器模型。</span><span class="sxs-lookup"><span data-stu-id="68e17-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="68e17-468">如何使用不同类型的按钮事件及其应用程序。</span><span class="sxs-lookup"><span data-stu-id="68e17-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="68e17-469">如何在控制器顶部覆盖 UI 元素或对其进行完全自定义。</span><span class="sxs-lookup"><span data-stu-id="68e17-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="68e17-470">现在, 你可以开始创建自己的具有运动控制器的沉浸式体验!</span><span class="sxs-lookup"><span data-stu-id="68e17-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="68e17-471">已完成场景</span><span class="sxs-lookup"><span data-stu-id="68e17-471">Completed scenes</span></span>

* <span data-ttu-id="68e17-472">在 Unity 的 "**项目**" 面板中, 单击 "**场景**" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="68e17-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="68e17-473">你将看到两个 Unity sceens **MixedReality213**和**MixedReality213Advanced**。</span><span class="sxs-lookup"><span data-stu-id="68e17-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="68e17-474">**MixedReality213**:带有单一画笔的已完成场景</span><span class="sxs-lookup"><span data-stu-id="68e17-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="68e17-475">**MixedReality213Advanced**:具有多个画笔并带有选择按钮的按量示例的已完成场景</span><span class="sxs-lookup"><span data-stu-id="68e17-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="68e17-476">请参阅</span><span class="sxs-lookup"><span data-stu-id="68e17-476">See also</span></span>

* [<span data-ttu-id="68e17-477">MR 输入213项目文件</span><span class="sxs-lookup"><span data-stu-id="68e17-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="68e17-478">混合现实工具包-运动控制器测试场景</span><span class="sxs-lookup"><span data-stu-id="68e17-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="68e17-479">混合现实工具包-抓取机制</span><span class="sxs-lookup"><span data-stu-id="68e17-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="68e17-480">运动控制器开发指南</span><span class="sxs-lookup"><span data-stu-id="68e17-480">Motion controller development guidelines</span></span>](motion-controllers.md)
