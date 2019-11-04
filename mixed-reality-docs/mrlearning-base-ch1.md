---
title: 入门教程-2。 初始化项目和首个应用程序
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 3a7b25a17ed1a80834dc7029e172bc7924992b07
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438437"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="90dda-105">2. 初始化项目和首个应用程序</span><span class="sxs-lookup"><span data-stu-id="90dda-105">2. Initializing your project and first application</span></span>

<span data-ttu-id="90dda-106">在第一课中，您将了解到[混合现实工具包（MRTK）]()必须提供的某些功能，启动 HoloLens 2 的第一个应用程序，并将其部署到设备。</span><span class="sxs-lookup"><span data-stu-id="90dda-106">In this first lesson, you'll learn about some of the capabilities the [Mixed Reality Toolkit (MRTK)]() has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="90dda-107">目标</span><span class="sxs-lookup"><span data-stu-id="90dda-107">Objectives</span></span>

* <span data-ttu-id="90dda-108">针对 Hololens 开发优化 Unity。</span><span class="sxs-lookup"><span data-stu-id="90dda-108">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="90dda-109">导入资产并设置场景。</span><span class="sxs-lookup"><span data-stu-id="90dda-109">Import assets and setup the scene.</span></span>
* <span data-ttu-id="90dda-110">空间映射网格、手动网格和帧速率计数器的可视化。</span><span class="sxs-lookup"><span data-stu-id="90dda-110">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter.</span></span>

## <a name="instructions"></a><span data-ttu-id="90dda-111">说明</span><span class="sxs-lookup"><span data-stu-id="90dda-111">Instructions</span></span>

### <a name="create-new-unity-project"></a><span data-ttu-id="90dda-112">创建新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="90dda-112">Create new Unity project</span></span>

1. <span data-ttu-id="90dda-113">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="90dda-113">Start Unity.</span></span>
2. <span data-ttu-id="90dda-114">选择**新建**。</span><span class="sxs-lookup"><span data-stu-id="90dda-114">Select **New**.</span></span>
<span data-ttu-id="90dda-115">![第 1 课 第 1 章 第 2 步](images/Lesson1Chapter1Step2.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-115">![Lesson1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)</span></span>
3. <span data-ttu-id="90dda-116">输入项目名称（例如 "MixedRealityBase"）。</span><span class="sxs-lookup"><span data-stu-id="90dda-116">Enter a project name (e.g. "MixedRealityBase").</span></span>
<span data-ttu-id="90dda-117">![第 1 课 第 1 章 第 3 步](images/Lesson1Chapter1Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-117">![Lesson1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)</span></span>
4. <span data-ttu-id="90dda-118">输入保存项目的位置。</span><span class="sxs-lookup"><span data-stu-id="90dda-118">Enter a location to save your project.</span></span>
<span data-ttu-id="90dda-119">![第 1 课 第 1 章 第 4 步](images/Lesson1Chapter1Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-119">![Lesson1 Chapter1 Step4](images/Lesson1Chapter1Step4.JPG)</span></span>
5. <span data-ttu-id="90dda-120">请确保将项目设置为“3D”。</span><span class="sxs-lookup"><span data-stu-id="90dda-120">Make sure the project is set to **3D**.</span></span>
<span data-ttu-id="90dda-121">![第 1 课 第 1 章 第 5 步](images/Lesson1Chapter1Step5.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-121">![Lesson1 Chapter1 Step5](images/Lesson1Chapter1Step5.JPG)</span></span>
6. <span data-ttu-id="90dda-122">单击“创建项目”。</span><span class="sxs-lookup"><span data-stu-id="90dda-122">Click **Create Project**.</span></span>
<span data-ttu-id="90dda-123">![第 1 课 第 1 章 第 6 步](images/Lesson1Chapter1Step6.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-123">![Lesson1 Chapter1 Step6](images/Lesson1Chapter1Step6.JPG)</span></span>

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="90dda-124">配置用于 Windows Mixed Reality 的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="90dda-124">Configure the Unity project for Windows Mixed Reality</span></span>

1. <span data-ttu-id="90dda-125">转到 "**文件** > **生成设置**"，打开 "*生成设置*" 窗口。</span><span class="sxs-lookup"><span data-stu-id="90dda-125">Open the *Build Settings* window by going to **File** > **Build Settings**.</span></span>
<span data-ttu-id="90dda-126">![第 1 课 第 4 章 第 1 步](images/Lesson1Chapter4Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-126">![Lesson1 Chapter4 Step1](images/Lesson1Chapter4Step1.JPG)</span></span>
2. <span data-ttu-id="90dda-127">选择 "*通用 Windows 平台*"，然后单击 "**切换平台**" 按钮切换平台。</span><span class="sxs-lookup"><span data-stu-id="90dda-127">Select the *Universal Windows Platform* and click the **Switch Platform** button to switch platforms.</span></span> <span data-ttu-id="90dda-128">在 HoloLens 2 上运行的应用程序需要与通用 Windows 平台（UWP）兼容。</span><span class="sxs-lookup"><span data-stu-id="90dda-128">Applications running on HoloLens 2 are required to be Universal Windows Platform (UWP) compatible.</span></span>
<span data-ttu-id="90dda-129">![第 1 课 第 4 章 第 2 步](images/Lesson1Chapter4Step2.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-129">![Lesson1 Chapter4 Step2](images/Lesson1Chapter4Step2.JPG)</span></span>
3. <span data-ttu-id="90dda-130">通过单击 "生成" 窗口中的 "**播放机设置**" 按钮启用虚拟现实，并在 "检查器" 面板中的 "XR 设置" 下启用 "*支持虚拟现实*" 复选框，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="90dda-130">Enable virtual reality by clicking on **Player Settings** button in the Build Window, and enable the *Virtual Reality Supported* checkbox under XR Settings from the inspector panel, as shown in the image below.</span></span> <span data-ttu-id="90dda-131">请注意，您可能需要将 "*生成设置*" 窗口拖出，以查看检查器面板。</span><span class="sxs-lookup"><span data-stu-id="90dda-131">Note that you might need to drag the *Build Settings* window out of the way in order to see the inspector panel.</span></span> <span data-ttu-id="90dda-132">"*受支持的虚拟现实*" 复选框还适用于混合现实和增加的现实耳机，因为它指的是启用 stereoscopic 视觉（每个眼睛呈现不同的图像） ![学习 Chapter4 步骤 3](images/Lesson1Chapter4Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-132">The *Virtual Reality Supported* checkbox also applies to Mixed Reality and Augmented Reality headsets because it refers to the enabling of stereoscopic vision (rendering different images for each eye.) ![Lesson1 Chapter4 Step3](images/Lesson1Chapter4Step3.JPG)</span></span>
4. <span data-ttu-id="90dda-133">同时，在 XR 设置下，将*立体声渲染模式*改为*单步实例*。</span><span class="sxs-lookup"><span data-stu-id="90dda-133">Also under XR Settings, change the *Stereo Rendering Mode* to *Single Pass Instanced*.</span></span> <span data-ttu-id="90dda-134">此[呈现管道样式](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)对于 Hololens 2 而言通常是最高性能的。</span><span class="sxs-lookup"><span data-stu-id="90dda-134">This [rendering pipeline style](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) is generally most performant for Hololens 2.</span></span> <span data-ttu-id="90dda-135">如果对 Unity 环境的其他性能配置感兴趣，请遵循[这些说明](recommended-settings-for-unity.md)。</span><span class="sxs-lookup"><span data-stu-id="90dda-135">If interested in other performant configurations for your Unity environment, follow [these instructions](recommended-settings-for-unity.md).</span></span>
<span data-ttu-id="90dda-136">![学习 Chapter4 Step3b](images/Lesson1Chapter4Step3b.jpg)</span><span class="sxs-lookup"><span data-stu-id="90dda-136">![Lesson1 Chapter4 Step3b](images/Lesson1Chapter4Step3b.jpg)</span></span>
5. <span data-ttu-id="90dda-137">在相同的检查器面板中，确保在 "*发布设置*" 下启用 "功能" 部分中的 "*空间感知*" 复选框。</span><span class="sxs-lookup"><span data-stu-id="90dda-137">From the same inspector panel, ensure that the *Spatial Perception* checkbox in the capabilities section is enabled under *Publishing Settings*.</span></span> <span data-ttu-id="90dda-138">空间感知使我们能够在混合现实设备上（如 HoloLens 2）直观显示空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="90dda-138">Spatial Perception allows us to visualize the spatial mapping mesh on a mixed reality device, such as HoloLens 2.</span></span> <span data-ttu-id="90dda-139">发布设置可在 "检查器" 面板中的 "XR 设置" 和 "其他设置" 下找到。</span><span class="sxs-lookup"><span data-stu-id="90dda-139">Publishing Settings are found in the inspector panel, above XR Settings and under Other Settings.</span></span>
<span data-ttu-id="90dda-140">![第 1 课 第 4 章 第 4 步](images/Lesson1Chapter4Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-140">![Lesson1 Chapter4 Step4](images/Lesson1Chapter4Step4.JPG)</span></span>

> [!NOTE]
> <span data-ttu-id="90dda-141">虽然本部分未使用，但你可能想要启用的其他一些常见功能包括用于语音命令的*麦克风*，以及用于连接到需要网络连接的服务的*InternetClient* 。</span><span class="sxs-lookup"><span data-stu-id="90dda-141">While not used in this section, some other common capabilities you might want to enable include the *Microphone* for voice commands, and *InternetClient* for connecting to services requiring a network connection.</span></span>

### <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="90dda-142">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="90dda-142">Import the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="90dda-143">下载最新的[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)Unity 包，并将其保存到电脑上的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="90dda-143">Download the latest [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity packages, and save them to a folder on your PC.</span></span>

2. <span data-ttu-id="90dda-144">导入每个*混合现实工具包*包。</span><span class="sxs-lookup"><span data-stu-id="90dda-144">Import each of the *Mixed Reality Toolkit* packages.</span></span> <span data-ttu-id="90dda-145">首先，单击 "**资产**" > **导入** > **自定义包**"。</span><span class="sxs-lookup"><span data-stu-id="90dda-145">Start by clicking on **Assets** > **Import** > **Custom Package**.</span></span> <span data-ttu-id="90dda-146">选择在步骤1中下载的*混合现实工具包*包之一，并打开它以开始导入过程。</span><span class="sxs-lookup"><span data-stu-id="90dda-146">Select one of the *Mixed Reality Toolkit* packages downloaded in Step 1 and open it to begin the importing process.</span></span> <span data-ttu-id="90dda-147">导入过程需几分钟。</span><span class="sxs-lookup"><span data-stu-id="90dda-147">Please allow a few minutes for the importing process.</span></span>
    <span data-ttu-id="90dda-148">![第 1 课 第 2 章 第 2a 步](images/Lesson1Chapter2Step2a.JPG) ![第 1 课 第 2 章 第 2b 步](images/Lesson1Chapter2Step2b.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-148">![Lesson1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)</span></span>

3. <span data-ttu-id="90dda-149">在下一个弹出窗口中，单击 "**导入**"，开始将所选包导入 Unity 项目。</span><span class="sxs-lookup"><span data-stu-id="90dda-149">In the next pop-up window, click **Import** to begin importing the selected package into the Unity project.</span></span> <span data-ttu-id="90dda-150">确保所有项都已选中，如图所示。</span><span class="sxs-lookup"><span data-stu-id="90dda-150">Ensure all items are checked as shown in the image.</span></span>
    <span data-ttu-id="90dda-151">![学习 Chapter2 步骤 3](images/Lesson1Chapter2Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-151">![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG)</span></span>
4. <span data-ttu-id="90dda-152">对于下载的每个包*混合现实工具包*包，请重复上面的步骤2和3。</span><span class="sxs-lookup"><span data-stu-id="90dda-152">Repeat steps 2 and 3 above for each package *Mixed Reality Toolkit* package downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="90dda-153">如果你看到一个弹出对话框，要求应用混合现实工具包默认设置，请单击 "**应用**"。</span><span class="sxs-lookup"><span data-stu-id="90dda-153">If you see a pop-up dialog box asking to apply the Mixed Reality Toolkit default settings, click **Apply**.</span></span> <span data-ttu-id="90dda-154">MRTK 在为自动安装导入时，分析你的项目中是否缺少建议的设置。</span><span class="sxs-lookup"><span data-stu-id="90dda-154">MRTK analyzes your project for any missing recommended settings when imported for automated setup.</span></span>

![学习 Chapter2 步骤3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="90dda-156">配置混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="90dda-156">Configure the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="90dda-157">通过选择 "**混合现实工具包**" > "**添加到场景" 并配置**，将*混合现实工具包*添加到当前场景。</span><span class="sxs-lookup"><span data-stu-id="90dda-157">Add the *Mixed Reality Toolkit* to your current scene by selecting **Mixed Reality Toolkit** > **Add to Scene and Configure..**</span></span> <span data-ttu-id="90dda-158">从菜单栏中。</span><span class="sxs-lookup"><span data-stu-id="90dda-158">from the menu bar.</span></span> <span data-ttu-id="90dda-159">如果在导入混合现实工具包后没有看到此菜单项，请重启 Unity。</span><span class="sxs-lookup"><span data-stu-id="90dda-159">If you don't see this menu item after importing the mixed reality toolkit, please restart Unity.</span></span>
  <span data-ttu-id="90dda-160">![第 1 课 第 3 章 第 1 步](images/Lesson1Chapter3Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-160">![Lesson1 Chapter3 Step1](images/Lesson1Chapter3Step1.JPG)</span></span>

> [!NOTE]
> <span data-ttu-id="90dda-161">你可能会看到一个弹出对话框，要求为[混合现实工具包选择一个配置文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。</span><span class="sxs-lookup"><span data-stu-id="90dda-161">You may see a pop-up dialog box asking to select a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="90dda-162">如果是，请选择 **"确定**"，然后选择名为 *"DefaultMixedRealityToolkitConfigurationProfile"* 的配置文件。</span><span class="sxs-lookup"><span data-stu-id="90dda-162">If so, select **Ok**, and choose the profile named *"DefaultMixedRealityToolkitConfigurationProfile"*.</span></span>

2. <span data-ttu-id="90dda-163">场景将包含多个新的项目和修改。</span><span class="sxs-lookup"><span data-stu-id="90dda-163">Your scene will have several new items and modifications.</span></span> <span data-ttu-id="90dda-164">单击 "**文件**" > "**另存为**"，将场景保存在其他名称下，并为场景指定名称，例如*BaseScene*。</span><span class="sxs-lookup"><span data-stu-id="90dda-164">Save your scene under a different name by clicking **File** > **Save As**, and give your scene a name, such as *BaseScene*.</span></span> <span data-ttu-id="90dda-165">通过将场景保存到项目的 "*资产*" 文件夹中的*场景*文件夹，使场景保持井然有序。</span><span class="sxs-lookup"><span data-stu-id="90dda-165">Keep your scene organized by saving it to the *Scenes* folder in your project’s *Assets* folder.</span></span>
  <span data-ttu-id="90dda-166">![第 1 课 第 3 章 第 2a 步](images/Lesson1Chapter3Step2a.JPG)
  ![第 1 课 第 3 章 第 2b 步](images/Lesson1Chapter3Step2b.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-166">![Lesson1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Lesson1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)</span></span>

### <a name="build-your-application-to-your-device"></a><span data-ttu-id="90dda-167">在设备上构建应用程序</span><span class="sxs-lookup"><span data-stu-id="90dda-167">Build your application to your device</span></span>

1. <span data-ttu-id="90dda-168">如果关闭了前面几节中的 "*生成设置*" 窗口，请通过转到 "**文件** > **生成设置**"，重新打开 "*生成设置*" 窗口。</span><span class="sxs-lookup"><span data-stu-id="90dda-168">If you closed the *Build Settings* window from the previous sections, open the *Build Settings* window again by going to **File** > **Build Settings**.</span></span>
    <span data-ttu-id="90dda-169">![第 1 课 第 5 章 第 1 步](images/Lesson1Chapter5Step1.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-169">![Lesson1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)</span></span>

2. <span data-ttu-id="90dda-170">如果场景在 Unity 中打开，请单击 "**添加打开的场景**" 按钮，确保刚刚创建的场景在 "*生成*" 列表中的场景中。</span><span class="sxs-lookup"><span data-stu-id="90dda-170">Ensure the scene you just created is in the *Scenes in Build* list by clicking on the **Add Open Scenes** button while your scene is open in Unity.</span></span>

3. <span data-ttu-id="90dda-171">按 "**生成**" 按钮开始生成过程。</span><span class="sxs-lookup"><span data-stu-id="90dda-171">Press the **Build** button to begin the build process.</span></span>
    <span data-ttu-id="90dda-172">![第 1 课 第 5 章 第 3 步](images/Lesson1Chapter5Step3.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-172">![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)</span></span>

4. <span data-ttu-id="90dda-173">为应用程序创建一个新文件夹并为其命名。</span><span class="sxs-lookup"><span data-stu-id="90dda-173">Create and name a new folder for your application.</span></span> <span data-ttu-id="90dda-174">在下图中，创建了一个包含应用程序的名称为 "应用程序" 的文件夹。</span><span class="sxs-lookup"><span data-stu-id="90dda-174">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="90dda-175">单击 "**选择文件夹**"，开始生成到新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="90dda-175">Click **Select Folder** to begin building to the newly created folder.</span></span> <span data-ttu-id="90dda-176">完成生成后，可以关闭 Unity 中的 "*生成设置*" 窗口。</span><span class="sxs-lookup"><span data-stu-id="90dda-176">After the build has completed, you can close the *Build Settings* window in Unity.</span></span>
    <span data-ttu-id="90dda-177">![第 1 课 第 5 章 第 4 步](images/Lesson1Chapter5Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-177">![Lesson1 Chapter5 Step4](images/Lesson1Chapter5Step4.JPG)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90dda-178">如果生成失败，尝试再次生成或重启 Unity 并再次生成。</span><span class="sxs-lookup"><span data-stu-id="90dda-178">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="90dda-179">如果看到错误，如 "错误： CS0246 = 类型或命名空间名称" XX "（是否缺少 using 指令或程序集引用？）。</span><span class="sxs-lookup"><span data-stu-id="90dda-179">If you see an error, such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="90dda-180">如果是这样，则可能需要安装[Windows 10 SDK （10.0.18362.0）](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span><span class="sxs-lookup"><span data-stu-id="90dda-180">If so, then you might need to install [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span></span>

5. <span data-ttu-id="90dda-181">生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="90dda-181">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="90dda-182">双击 " *MixedRealityBase* " 解决方案或相应的名称（如果你使用的是项目的备用名称）以在 Visual Studio 中打开解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="90dda-182">Double click on the *MixedRealityBase.sln* solution, or the corresponding name, if you used an alternative name for your project, to open the solution file in Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="90dda-183">如果遵循前面步骤中的命名约定，请确保打开新创建的文件夹（即*App*文件夹），因为在该文件夹外，不会与 build 文件夹内的 .sln 文件混淆的名称类似。</span><span class="sxs-lookup"><span data-stu-id="90dda-183">Be sure to open the newly created folder (i.e. the *App* folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> <span data-ttu-id="90dda-184">文件夹结构应类似于下图。</span><span class="sxs-lookup"><span data-stu-id="90dda-184">The folder structure should look similar to the image below.</span></span>
>
> <span data-ttu-id="90dda-185">如果 Visual Studio 要求你安装新组件，请花一点时间确保按照[“安装工具”页面](install-the-tools.md)中的说明安装所有必备组件</span><span class="sxs-lookup"><span data-stu-id="90dda-185">If Visual Studio asks you to install new components, please take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

![第 1 课 第 5 章 第 5 步](images/Lesson1Chapter5Step5.JPG)

6. <span data-ttu-id="90dda-187">将 HoloLens 2 连接到您的 PC。</span><span class="sxs-lookup"><span data-stu-id="90dda-187">Connect your HoloLens 2 into your PC.</span></span> <span data-ttu-id="90dda-188">尽管这些说明假设你将部署到 HoloLens 2 设备，但你也可以选择部署到[hololens 2 模拟器](using-the-hololens-emulator.md)，或选择创建[用于旁加载的应用包](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="90dda-188">While these instructions assume you will be deploying to a HoloLens 2 device, you might also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="90dda-189">在生成到设备之前，设备必须处于*开发人员模式*并与开发计算机配对。</span><span class="sxs-lookup"><span data-stu-id="90dda-189">Before building to your device, the device must be in *Developer Mode* and paired with your development machine.</span></span> <span data-ttu-id="90dda-190">可以按照以下[说明](using-visual-studio.md)完成这两个步骤</span><span class="sxs-lookup"><span data-stu-id="90dda-190">Both of these steps can be completed by following [these instructions](using-visual-studio.md)</span></span>

8. <span data-ttu-id="90dda-191">将 Visual Studio 配置为通过选择 "*发布*" 或 "*主*" 配置和*ARM*体系结构生成到 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="90dda-191">Configure Visual Studio for building to your HoloLens 2 by selecting the *Release* or *Master* configuration and the *ARM* architecture.</span></span>
    <span data-ttu-id="90dda-192">![第 1 课 第 5 章 第 8 步](images/Lesson1Chapter5Step8.JPG)</span><span class="sxs-lookup"><span data-stu-id="90dda-192">![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)</span></span>

9. <span data-ttu-id="90dda-193">最后一步是通过选择 "**调试**" > "开始执行（**不调试**）" 来生成并部署到设备。</span><span class="sxs-lookup"><span data-stu-id="90dda-193">The final step is to build and deploy to your device by selecting **Debug** > **Start without debugging**.</span></span> <span data-ttu-id="90dda-194">如果选择 "*启动但不调试*"，则会导致应用程序在成功生成后立即在设备上启动，但不会附加调试器，而且会在 Visual Studio 中显示信息。</span><span class="sxs-lookup"><span data-stu-id="90dda-194">Selecting *Start without Debugging* causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="90dda-195">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="90dda-195">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

> [!NOTE]
> <span data-ttu-id="90dda-196">你还可以选择 "**生成**" > **部署解决方案**以部署到设备，而无需应用程序自动启动。</span><span class="sxs-lookup"><span data-stu-id="90dda-196">You might also select **Build** > **Deploy Solution** to deploy to your device without having the application automatically start.</span></span>

![学习 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a><span data-ttu-id="90dda-198">祝贺</span><span class="sxs-lookup"><span data-stu-id="90dda-198">Congratulations</span></span>

<span data-ttu-id="90dda-199">现在，你已部署了第一个 HoloLens 2 应用程序。</span><span class="sxs-lookup"><span data-stu-id="90dda-199">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="90dda-200">在四处浏览时，应会看到一个空间映射网格，其中包含已由 HoloLens 2 检测到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="90dda-200">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="90dda-201">此外，你应该看到手指和抓手指，以及用于跟踪应用程序性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="90dda-201">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="90dda-202">这些只是混合现实工具包中开箱即用的一些基本功能。</span><span class="sxs-lookup"><span data-stu-id="90dda-202">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="90dda-203">在即将推出的课程中，您将开始向场景中添加更多内容和交互性，以便您可以充分探索 HoloLens 2 的功能和混合现实工具包。</span><span class="sxs-lookup"><span data-stu-id="90dda-203">In the lessons to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="90dda-204">你将在[第5课](mrlearning-base-ch5.md)中介绍如何使用语音命令切换帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="90dda-204">You will cover how to toggle the frame rate counter using a voice command in [Lesson 5](mrlearning-base-ch5.md).</span></span> <span data-ttu-id="90dda-205">通常建议在开发过程中始终保持可视化探查器的可见性，以了解代码更改可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="90dda-205">It is generally recommended to keep the visual profiler visible at all times during development to understand when code changes may have impacted perf.</span></span> <span data-ttu-id="90dda-206">Hololens 2 应用程序应[持续运行 60 FPS](understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="90dda-206">Hololens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="90dda-207">下一课： 3. 创建用户界面和配置混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="90dda-207">Next Lesson: 3. Creating user interface and configure Mixed Reality Toolkit </span></span>](mrlearning-base-ch2.md)
