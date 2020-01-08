---
title: 入门教程 - 2. 初始化你的项目和第一个应用程序
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334412"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="baec8-105">2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="baec8-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="baec8-106">概述</span><span class="sxs-lookup"><span data-stu-id="baec8-106">Overview</span></span>

<span data-ttu-id="baec8-107">在第一堂课中，你将了解<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 提供的一些功能，针对 HoloLens 2 启动你的第一个应用程序，并将其部署到设备上。</span><span class="sxs-lookup"><span data-stu-id="baec8-107">In this first lesson, you'll learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="baec8-108">目标</span><span class="sxs-lookup"><span data-stu-id="baec8-108">Objectives</span></span>

* <span data-ttu-id="baec8-109">配置 Unity 以便进行 Hololens 开发。</span><span class="sxs-lookup"><span data-stu-id="baec8-109">Configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="baec8-110">导入资产并设置场景。</span><span class="sxs-lookup"><span data-stu-id="baec8-110">Import assets and set up the scene.</span></span>
* <span data-ttu-id="baec8-111">空间映射网格、手部网格和帧率计数器的可视化。</span><span class="sxs-lookup"><span data-stu-id="baec8-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="baec8-112">创建新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="baec8-112">Create new Unity project</span></span>

1. <span data-ttu-id="baec8-113">启动 Unity。</span><span class="sxs-lookup"><span data-stu-id="baec8-113">Start Unity.</span></span>

2. <span data-ttu-id="baec8-114">选择“新建”  。</span><span class="sxs-lookup"><span data-stu-id="baec8-114">Select **New**.</span></span>

    ![第 1 课第 1 部分步骤 2](images/mrlearning-base-ch1-1-step2.JPG)

3. <span data-ttu-id="baec8-116">输入项目名称（例如“MixedRealityBase”）。</span><span class="sxs-lookup"><span data-stu-id="baec8-116">Enter a project name (e.g. "MixedRealityBase").</span></span>

    ![第 1 课第 1 部分步骤 3](images/mrlearning-base-ch1-1-step3.JPG)

4. <span data-ttu-id="baec8-118">输入保存项目的位置。</span><span class="sxs-lookup"><span data-stu-id="baec8-118">Enter a location to save your project.</span></span>

    ![第 1 课第 1 部分步骤 4](images/mrlearning-base-ch1-1-step4.JPG)

5. <span data-ttu-id="baec8-120">请确保将项目设置为“3D”  。</span><span class="sxs-lookup"><span data-stu-id="baec8-120">Make sure the project is set to **3D**.</span></span>

    ![第 1 课第 1 部分步骤 5](images/mrlearning-base-ch1-1-step5.JPG)

6. <span data-ttu-id="baec8-122">单击“创建项目”  。</span><span class="sxs-lookup"><span data-stu-id="baec8-122">Click **Create Project**.</span></span>

    ![第 1 课第 1 部分步骤 6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="baec8-124">配置用于 Windows Mixed Reality 的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="baec8-124">Configure the Unity project for Windows Mixed Reality</span></span>

1. <span data-ttu-id="baec8-125">转到“文件” > “生成设置”，打开“生成设置”窗口。   </span><span class="sxs-lookup"><span data-stu-id="baec8-125">Open the *Build Settings* window by going to **File** > **Build Settings**.</span></span>

    ![第 1 课第 2 部分步骤 1](images/mrlearning-base-ch1-2-step1.JPG)

2. <span data-ttu-id="baec8-127">选择“通用 Windows 平台”，然后单击“切换平台”按钮以切换平台。  </span><span class="sxs-lookup"><span data-stu-id="baec8-127">Select the *Universal Windows Platform* and click the **Switch Platform** button to switch platforms.</span></span> <span data-ttu-id="baec8-128">在 HoloLens 2 上运行的应用程序必须兼容通用 Windows 平台 (UWP)。</span><span class="sxs-lookup"><span data-stu-id="baec8-128">Applications running on HoloLens 2 are required to be Universal Windows Platform (UWP) compatible.</span></span>

    ![第 1 课第 2 部分步骤 2](images/mrlearning-base-ch1-2-step2.JPG)

3. <span data-ttu-id="baec8-130">通过单击“生成”窗口中的“播放器设置”按钮启用虚拟现实，然后在检查器面板中启用“XR 设置”下的“支持虚拟现实”复选框，如下图所示。  </span><span class="sxs-lookup"><span data-stu-id="baec8-130">Enable virtual reality by clicking the **Player Settings** button in the Build Window, and enable the *Virtual Reality Supported* checkbox under XR Settings from the inspector panel, as shown in the image below.</span></span> <span data-ttu-id="baec8-131">请注意，可能需要将“生成设置”窗口拖动到旁边，以便查看检查器面板。 </span><span class="sxs-lookup"><span data-stu-id="baec8-131">Note that you might need to drag the *Build Settings* window out of the way in order to see the inspector panel.</span></span> <span data-ttu-id="baec8-132">“支持虚拟现实”复选框也适用于混合现实和增强现实头戴显示设备，因为它指的是启用立体视觉（为每只眼睛渲染不同的图像）。 </span><span class="sxs-lookup"><span data-stu-id="baec8-132">The *Virtual Reality Supported* checkbox also applies to Mixed Reality and Augmented Reality headsets because it refers to the enabling of stereoscopic vision (rendering different images for each eye.)</span></span>

    ![第 1 课第 2 部分步骤 3](images/mrlearning-base-ch1-2-step3.JPG)

4. <span data-ttu-id="baec8-134">另外，请在“XR 设置”下将“立体渲染模式”更改为“单通道实例化”。  </span><span class="sxs-lookup"><span data-stu-id="baec8-134">Also under XR Settings, change the *Stereo Rendering Mode* to *Single Pass Instanced*.</span></span> <span data-ttu-id="baec8-135">对于 HoloLens 2 来说，此[渲染管道样式](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)通常是性能最强的。</span><span class="sxs-lookup"><span data-stu-id="baec8-135">This [rendering pipeline style](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) is generally most performant for HoloLens 2.</span></span> <span data-ttu-id="baec8-136">如果对适合 Unity 环境的其他高性能配置感兴趣，请按照[这些说明](recommended-settings-for-unity.md)操作。</span><span class="sxs-lookup"><span data-stu-id="baec8-136">If interested in other performant configurations for your Unity environment, follow [these instructions](recommended-settings-for-unity.md).</span></span>

    ![第 1 课第 2 部分步骤 4](images/mrlearning-base-ch1-2-step4.jpg)

5. <span data-ttu-id="baec8-138">在同一个检查器面板中，确保在“发布设置”下启用“功能”部分的“空间感知”复选框。  </span><span class="sxs-lookup"><span data-stu-id="baec8-138">From the same inspector panel, ensure that the *Spatial Perception* checkbox in the capabilities section is enabled under *Publishing Settings*.</span></span> <span data-ttu-id="baec8-139">通过“空间感知”功能，我们可以在混合现实设备（如 HoloLens 2）上可视化空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="baec8-139">Spatial Perception allows us to visualize the spatial mapping mesh on a mixed reality device, such as HoloLens 2.</span></span> <span data-ttu-id="baec8-140">可以在检查器面板的“XR 设置”上方和“其他设置”下方找到“发布设置”。</span><span class="sxs-lookup"><span data-stu-id="baec8-140">Publishing Settings are found in the inspector panel, above XR Settings and under Other Settings.</span></span>

    ![第 1 课第 2 部分步骤 5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    ><span data-ttu-id="baec8-142">你可能希望启用一些其他的常用功能（虽然本部分未使用到），包括“麦克风”（用于语音命令）和 *InternetClient*（用于连接到需要网络连接的服务）。 </span><span class="sxs-lookup"><span data-stu-id="baec8-142">While not used in this section, some other common capabilities you might want to enable include the *Microphone* for voice commands, and *InternetClient* for connecting to services requiring a network connection.</span></span>

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="baec8-143">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="baec8-143">Import the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="baec8-144">下载[混合现实工具包](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation 包版本 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) 并将其保存到电脑上的文件夹。</span><span class="sxs-lookup"><span data-stu-id="baec8-144">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) and save it to a folder on your PC.</span></span>

2. <span data-ttu-id="baec8-145">导入在上一步下载的混合现实工具包  。</span><span class="sxs-lookup"><span data-stu-id="baec8-145">Import the *Mixed Reality Toolkit* package that you downloaded in the previous step.</span></span> <span data-ttu-id="baec8-146">一开始请单击“资产”   >   “导入” >   “自定义包”，然后选择 *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* 并将其打开，开始导入过程。</span><span class="sxs-lookup"><span data-stu-id="baec8-146">Start by clicking on **Assets** > **Import** > **Custom Package**, select *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* and open it to begin the importing process.</span></span> <span data-ttu-id="baec8-147">等待几分钟，以便该导入过程完成。</span><span class="sxs-lookup"><span data-stu-id="baec8-147">Allow a few minutes for the importing process to complete.</span></span>

    ![第 1 课第 3 部分步骤 2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![第 1 课第 3 部分步骤 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. <span data-ttu-id="baec8-150">在下一个弹出窗口中单击“导入”，开始将所选包导入 Unity 项目。 </span><span class="sxs-lookup"><span data-stu-id="baec8-150">In the next pop-up window, click **Import** to begin importing the selected package into the Unity project.</span></span> <span data-ttu-id="baec8-151">请确保选中所有项，如图所示。</span><span class="sxs-lookup"><span data-stu-id="baec8-151">Ensure all items are checked as shown in the image.</span></span>

    ![第 1 课第 3 部分步骤 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > <span data-ttu-id="baec8-153">如果看到一个弹出式对话框，要求应用混合现实工具包默认设置，请单击“应用”。 </span><span class="sxs-lookup"><span data-stu-id="baec8-153">If you see a pop-up dialog box asking to apply the Mixed Reality Toolkit default settings, click **Apply**.</span></span> <span data-ttu-id="baec8-154">在导入后进行自动设置时，MRTK 会分析项目中是否缺少建议的设置。</span><span class="sxs-lookup"><span data-stu-id="baec8-154">MRTK analyzes your project for any missing recommended settings when imported for automated setup.</span></span> <span data-ttu-id="baec8-155">弹出式对话框看起来可能不同于下图，具体取决于你的设置。</span><span class="sxs-lookup"><span data-stu-id="baec8-155">Depending on your settings, the pop-up might look different than the image below.</span></span>

    ![第 1 课第 3 部分步骤 4 说明 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="baec8-157">配置混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="baec8-157">Configure the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="baec8-158">将混合现实工具包添加到当前场景，方法是：  从菜单栏选择“混合现实工具包”   >  </span><span class="sxs-lookup"><span data-stu-id="baec8-158">Add the *Mixed Reality Toolkit* to your current scene by selecting **Mixed Reality Toolkit** > **Add to Scene and Configure..**</span></span> <span data-ttu-id="baec8-159">“添加到场景并配置...”。</span><span class="sxs-lookup"><span data-stu-id="baec8-159">from the menu bar.</span></span> <span data-ttu-id="baec8-160">如果在导入混合现实工具包后没有看到此菜单项，请重启 Unity。</span><span class="sxs-lookup"><span data-stu-id="baec8-160">If you don't see this menu item after importing the mixed reality toolkit, restart Unity.</span></span>

    ![第 1 课第 4 部分步骤 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > <span data-ttu-id="baec8-162">可能会看到一个弹出式对话框，用于选择[混合现实工具包的配置文件](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)。</span><span class="sxs-lookup"><span data-stu-id="baec8-162">You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="baec8-163">请双击名为 *DefaultHoloLens2ConfigurationProfile* 的配置文件，将其选中。</span><span class="sxs-lookup"><span data-stu-id="baec8-163">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

2. <span data-ttu-id="baec8-164">你的场景会有多个新项和修改项。</span><span class="sxs-lookup"><span data-stu-id="baec8-164">Your scene will have several new items and modifications.</span></span> <span data-ttu-id="baec8-165">单击“文件” > “另存为”，使用其他名称保存场景并为场景命名，例如 *BaseScene*。  </span><span class="sxs-lookup"><span data-stu-id="baec8-165">Save your scene under a different name by clicking **File** > **Save As...**, and give your scene a name, such as *BaseScene*.</span></span> <span data-ttu-id="baec8-166">将场景保存到项目的 *Assets* 文件夹中的 *Scenes* 文件夹，以保持场景的有序性。</span><span class="sxs-lookup"><span data-stu-id="baec8-166">Keep your scene organized by saving it to the *Scenes* folder in your project’s *Assets* folder.</span></span>

    ![第 1 课第 4 部分步骤 2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![第 1 课第 4 部分步骤 2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="baec8-169">在设备上构建应用程序</span><span class="sxs-lookup"><span data-stu-id="baec8-169">Build your application to your device</span></span>

1. <span data-ttu-id="baec8-170">如果在前面的部分关闭了“生成设置”窗口，请转到“文件” > “生成设置”，再次打开“生成设置”窗口。    </span><span class="sxs-lookup"><span data-stu-id="baec8-170">If you closed the *Build Settings* window from the previous sections, open the *Build Settings* window again by going to **File** > **Build Settings**.</span></span>

    ![第 1 课第 5 部分步骤 1](images/mrlearning-base-ch1-5-step1.JPG)

2. <span data-ttu-id="baec8-172">当场景在 Unity 中处于打开状态时，请单击“添加打开的场景”按钮，确保刚创建的场景位于“生成中的场景”列表中。  </span><span class="sxs-lookup"><span data-stu-id="baec8-172">Ensure the scene you just created is in the *Scenes in Build* list by clicking on the **Add Open Scenes** button while your scene is open in Unity.</span></span>

3. <span data-ttu-id="baec8-173">按“生成”按钮，开始生成过程。 </span><span class="sxs-lookup"><span data-stu-id="baec8-173">Press the **Build** button to begin the build process.</span></span>

    ![第 1 课第 5 部分步骤 3](images/mrlearning-base-ch1-5-step3.JPG)

4. <span data-ttu-id="baec8-175">为应用程序创建一个新文件夹并为其命名。</span><span class="sxs-lookup"><span data-stu-id="baec8-175">Create and name a new folder for your application.</span></span> <span data-ttu-id="baec8-176">在下图中，我们创建了一个名为 App 的文件夹，用于存储该应用程序。</span><span class="sxs-lookup"><span data-stu-id="baec8-176">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="baec8-177">请单击“选择文件夹”，开始生成到新创建的文件夹。 </span><span class="sxs-lookup"><span data-stu-id="baec8-177">Click **Select Folder** to begin building to the newly created folder.</span></span> <span data-ttu-id="baec8-178">生成完成后，可以关闭 Unity 中的“生成设置”窗口。 </span><span class="sxs-lookup"><span data-stu-id="baec8-178">After the build has completed, you can close the *Build Settings* window in Unity.</span></span>

    ![第 1 课第 5 部分步骤 4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    ><span data-ttu-id="baec8-180">如果生成失败，尝试再次生成或重启 Unity 并再次生成。</span><span class="sxs-lookup"><span data-stu-id="baec8-180">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="baec8-181">如果看到错误，如“错误:CS0246 = 找不到类型或命名空间名称 “XX” (是否缺少 using 指令或程序集引用?)”，</span><span class="sxs-lookup"><span data-stu-id="baec8-181">If you see an error, such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="baec8-182">可能需要安装 [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span><span class="sxs-lookup"><span data-stu-id="baec8-182">If so, you might need to install [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span></span>

5. <span data-ttu-id="baec8-183">生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="baec8-183">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="baec8-184">双击“MixedRealityBase.sln”解决方案或相应的名称（如果使用了项目的替代名称），在 Visual Studio 中打开解决方案文件。 </span><span class="sxs-lookup"><span data-stu-id="baec8-184">Double-click on the *MixedRealityBase.sln* solution, or the corresponding name, if you used an alternative name for your project, to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="baec8-185">请务必打开新创建的文件夹（即 *App* 文件夹，如果遵循前面步骤中的命名约定），因为在该文件夹之外会有一个类似名称的 .sln 文件，不能将其与生成文件夹内的 .sln 文件混淆。</span><span class="sxs-lookup"><span data-stu-id="baec8-185">Be sure to open the newly created folder (i.e. the *App* folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder, that is not to be confused with the .sln file inside the build folder.</span></span> <span data-ttu-id="baec8-186">文件夹结构看起来应该类似于下图。</span><span class="sxs-lookup"><span data-stu-id="baec8-186">The folder structure should look similar to the image below.</span></span>
    >
    ><span data-ttu-id="baec8-187">如果 Visual Studio 要求你安装新组件，请花一点时间确保按照[“安装工具”页面](install-the-tools.md)中的说明安装所有必备组件</span><span class="sxs-lookup"><span data-stu-id="baec8-187">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

    ![第 1 课第 5 部分步骤 5](images/mrlearning-base-ch1-5-step5.JPG)

6. <span data-ttu-id="baec8-189">将 HoloLens 2 连接到电脑中。</span><span class="sxs-lookup"><span data-stu-id="baec8-189">Connect your HoloLens 2 into your PC.</span></span> <span data-ttu-id="baec8-190">虽然这些说明假设你会部署到 HoloLens 2 设备，但你也可以选择部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或选择创建[用于旁加载的应用包](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span><span class="sxs-lookup"><span data-stu-id="baec8-190">While these instructions assume you will be deploying to a HoloLens 2 device, you might also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="baec8-191">在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。 </span><span class="sxs-lookup"><span data-stu-id="baec8-191">Before building to your device, the device must be in *Developer Mode* and paired with your development machine.</span></span> <span data-ttu-id="baec8-192">这两个步骤都可以按照[这些说明](using-visual-studio.md)来完成</span><span class="sxs-lookup"><span data-stu-id="baec8-192">Both of these steps can be completed by following [these instructions](using-visual-studio.md)</span></span>

7. <span data-ttu-id="baec8-193">通过选择“发布”配置或“Master”配置、“ARM”体系结构和“设备”作为目标，配置 Visual Studio 以生成到 HoloLens 2。    </span><span class="sxs-lookup"><span data-stu-id="baec8-193">Configure Visual Studio for building to your HoloLens 2 by selecting the *Release* or *Master* configuration, the *ARM* architecture, and *Device* as target.</span></span>

    ![第 1 课第 5 部分步骤 8](images/mrlearning-base-ch1-5-step7.JPG)

8. <span data-ttu-id="baec8-195">最后一步是选择“调试” > “在不调试的情况下启动”，以便生成并部署到你的设备。  </span><span class="sxs-lookup"><span data-stu-id="baec8-195">The final step is to build and deploy to your device by selecting **Debug** > **Start without debugging**.</span></span> <span data-ttu-id="baec8-196">选择“在不调试的情况下启动”会导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中附加调试程序和显示调试信息。 </span><span class="sxs-lookup"><span data-stu-id="baec8-196">Selecting *Start without Debugging* causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="baec8-197">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="baec8-197">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="baec8-198">也可以选择“生成” > “部署解决方案”以部署到你的设备，而无需自动启动应用程序。  </span><span class="sxs-lookup"><span data-stu-id="baec8-198">You might also select **Build** > **Deploy Solution** to deploy to your device without having the application automatically start.</span></span>

    ![第 1 课第 5 部分步骤 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a><span data-ttu-id="baec8-200">祝贺</span><span class="sxs-lookup"><span data-stu-id="baec8-200">Congratulations</span></span>

<span data-ttu-id="baec8-201">你现在已经部署了第一个 HoloLens 2 应用程序。</span><span class="sxs-lookup"><span data-stu-id="baec8-201">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="baec8-202">当你四处走动时，应该看到空间映射网格覆盖了 HoloLens 2 感知到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="baec8-202">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="baec8-203">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用程序性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="baec8-203">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="baec8-204">这些只是混合现实工具包中开箱即用的一些基本功能。</span><span class="sxs-lookup"><span data-stu-id="baec8-204">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="baec8-205">在接下来的课程中，你将开始为场景添加更多的内容和交互性，以便充分探索 HoloLens 2 和混合现实工具包的功能。</span><span class="sxs-lookup"><span data-stu-id="baec8-205">In the lessons to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="baec8-206">在应用中，你可能会注意到可视探查器。</span><span class="sxs-lookup"><span data-stu-id="baec8-206">In the app, you may notice the visual profiler.</span></span> <span data-ttu-id="baec8-207">[第 5 课](mrlearning-base-ch5.md)会介绍如何使用语音命令切换帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="baec8-207">You will cover how to toggle the frame rate counter using a voice command in [Lesson 5](mrlearning-base-ch5.md).</span></span> <span data-ttu-id="baec8-208">通常建议在开发过程中让可视探查器始终保持可见状态，这样就可以了解何时代码更改会影响性能。</span><span class="sxs-lookup"><span data-stu-id="baec8-208">It is generally recommended to keep the visual profiler visible at all times during development to understand when code changes may have impacted perf.</span></span> <span data-ttu-id="baec8-209">HoloLens 2 应用程序应该[持续在 60 FPS 运行](understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="baec8-209">HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="baec8-210">下一课：3.创建用户界面并配置混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="baec8-210">Next Lesson: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
