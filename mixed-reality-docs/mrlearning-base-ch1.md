---
title: 入门教程 - 2. 初始化你的项目和第一个应用程序
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 56adb4bfc66768684c8269c0f0cafd70c486ea8a
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376204"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="b4942-105">2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="b4942-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="b4942-106">概述</span><span class="sxs-lookup"><span data-stu-id="b4942-106">Overview</span></span>

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
<span data-ttu-id="b4942-107">在这第一个教程中，我们将了解<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 提供的一些功能，针对 HoloLens 2 启动第一个应用程序，并将其部署到设备上。</span><span class="sxs-lookup"><span data-stu-id="b4942-107">In this first tutorial, you will learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="b4942-108">目标</span><span class="sxs-lookup"><span data-stu-id="b4942-108">Objectives</span></span>

* <span data-ttu-id="b4942-109">配置用于 Hololens 开发的 Unity</span><span class="sxs-lookup"><span data-stu-id="b4942-109">Configure Unity for HoloLens development</span></span>
* <span data-ttu-id="b4942-110">导入资产并设置场景</span><span class="sxs-lookup"><span data-stu-id="b4942-110">Import assets and set up the scene</span></span>
* <span data-ttu-id="b4942-111">空间映射网格、手部网格和帧率计数器的可视化</span><span class="sxs-lookup"><span data-stu-id="b4942-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b4942-112">必备条件</span><span class="sxs-lookup"><span data-stu-id="b4942-112">Prerequisites</span></span>

* <span data-ttu-id="b4942-113">一台 Windows 10 电脑，其中已[安装](install-the-tools.md)并配置正确的工具</span><span class="sxs-lookup"><span data-stu-id="b4942-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="b4942-114">Windows 10 SDK 10.0.18362.0 或更高版本</span><span class="sxs-lookup"><span data-stu-id="b4942-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="b4942-115">一些基本的 C# 编程功能</span><span class="sxs-lookup"><span data-stu-id="b4942-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="b4942-116">一个[针对开发配置](using-visual-studio.md#enabling-developer-mode)的 HoloLens 2 设备</span><span class="sxs-lookup"><span data-stu-id="b4942-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="b4942-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity 中心</a>，其中已安装 Unity 2019.2.X 并添加了通用 Windows 平台生成支持模块</span><span class="sxs-lookup"><span data-stu-id="b4942-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4942-118">建议用于本系列教程的 Unity 版本是 Unity 2019.2.X。</span><span class="sxs-lookup"><span data-stu-id="b4942-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="b4942-119">这将取代上述链接的先决条件中所述的任何 Unity 版本要求或建议。</span><span class="sxs-lookup"><span data-stu-id="b4942-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="b4942-120">创建新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b4942-120">Create new Unity project</span></span>

<span data-ttu-id="b4942-121">启动“Unity 中心”，  选择“项目”选项卡，  然后单击“新建”按钮旁边的**向下箭头**： </span><span class="sxs-lookup"><span data-stu-id="b4942-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

<span data-ttu-id="b4942-123">选择上面[先决条件](#prerequisites)部分中指定的 Unity 版本：</span><span class="sxs-lookup"><span data-stu-id="b4942-123">Select the Unity version specified in the [Prerequisites](#prerequisites) section above:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

<span data-ttu-id="b4942-125">在“创建新项目”窗口中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b4942-125">In the Create a new project window:</span></span>

* <span data-ttu-id="b4942-126">确保将“模板”设置为“3D”  </span><span class="sxs-lookup"><span data-stu-id="b4942-126">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="b4942-127">输入合适的“项目名称”，例如“MRTK 教程”  </span><span class="sxs-lookup"><span data-stu-id="b4942-127">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="b4942-128">选择合适的“位置”来存储项目，例如“D:\MixedRealityLearning”  </span><span class="sxs-lookup"><span data-stu-id="b4942-128">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="b4942-129">单击“创建”按钮，创建并启动新的 Unity 项目 </span><span class="sxs-lookup"><span data-stu-id="b4942-129">Click the **Create** button to create and launch your new Unity project</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="b4942-131">在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="b4942-131">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="b4942-132">如果任何文件路径的长度超出 255 个字符，则 Unity 受这些限制影响，可能无法编译。</span><span class="sxs-lookup"><span data-stu-id="b4942-132">Unity is affected by these limits and may fail to compile if any file path is longer than 255 characters.</span></span> <span data-ttu-id="b4942-133">因此，强烈建议将 Unity 项目存储在尽可能靠近驱动器根目录的位置。</span><span class="sxs-lookup"><span data-stu-id="b4942-133">Consequently, it is strongly recommended to store your Unity project as close to the root of the drive as possible.</span></span>

<span data-ttu-id="b4942-134">等待 Unity 创建项目：</span><span class="sxs-lookup"><span data-stu-id="b4942-134">Wait for Unity to create the project:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="b4942-136">配置用于 Windows Mixed Reality 的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b4942-136">Configure the Unity project for Windows Mixed Reality</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="b4942-137">在此部分，我们将切换生成平台、启用虚拟现实并启用空间感知。</span><span class="sxs-lookup"><span data-stu-id="b4942-137">In this section, you will switch build platform, enable virtual reality, and enable spatial perception.</span></span>

### <a name="1-switch-build-platform"></a><span data-ttu-id="b4942-138">1.切换生成平台</span><span class="sxs-lookup"><span data-stu-id="b4942-138">1. Switch build platform</span></span>

<span data-ttu-id="b4942-139">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口：  </span><span class="sxs-lookup"><span data-stu-id="b4942-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

<span data-ttu-id="b4942-141">在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮：  </span><span class="sxs-lookup"><span data-stu-id="b4942-141">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

<span data-ttu-id="b4942-143">等待 Unity 完成平台切换操作：</span><span class="sxs-lookup"><span data-stu-id="b4942-143">Wait for Unity to finish switching the platform:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

<span data-ttu-id="b4942-145">当 Unity 完成平台切换后，单击红色 **x** 图标，关闭“生成设置”窗口：</span><span class="sxs-lookup"><span data-stu-id="b4942-145">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a><span data-ttu-id="b4942-147">2.启用虚拟现实</span><span class="sxs-lookup"><span data-stu-id="b4942-147">2. Enable virtual reality</span></span>

> [!NOTE]
> <span data-ttu-id="b4942-148">“启用虚拟现实”功能也适用于混合现实和增强现实头戴显示设备，因为它指的是启用立体视觉，即：为每只眼睛渲染不同的图像。</span><span class="sxs-lookup"><span data-stu-id="b4942-148">Enabling virtual reality also applies to mixed reality and augmented reality headsets because it refers to enabling stereoscopic vision, i.e. rendering different images for each eye.</span></span>

<span data-ttu-id="b4942-149">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口：  </span><span class="sxs-lookup"><span data-stu-id="b4942-149">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

<span data-ttu-id="b4942-151">在“项目设置”窗口中选择“播放器” > “XR 设置”，展开“XR 设置”：  </span><span class="sxs-lookup"><span data-stu-id="b4942-151">In the Project Settings window, select **Player** > **XR Settings** to expand the XR Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

<span data-ttu-id="b4942-153">在“XR 设置”中勾选“支持虚拟现实”复选框以启用虚拟现实，然后单击“+”图标并选择“Windows Mixed Reality”，以便添加 Windows Mixed Reality SDK：   </span><span class="sxs-lookup"><span data-stu-id="b4942-153">In the XR Settings, check the **Virtual Reality Supported** checkbox to enable virtual reality, then click the **+** icon and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

<span data-ttu-id="b4942-155">等待 Unity 完成添加 SDK 的操作：</span><span class="sxs-lookup"><span data-stu-id="b4942-155">Wait for Unity to finish adding the SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

<span data-ttu-id="b4942-157">当 Unity 完成添加 SDK 的操作后，请优化 XR 设置，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b4942-157">When Unity has finished adding the SDK, optimize the XR Settings as follows:</span></span>

* <span data-ttu-id="b4942-158">将 Windows Mixed Reality 的“深度格式”设置为“16 位深度”  </span><span class="sxs-lookup"><span data-stu-id="b4942-158">Set Windows Mixed Reality **Depth Format** to **16-bit depth**</span></span>
* <span data-ttu-id="b4942-159">勾选 Windows Mixed Reality 的“启用深度共享”复选框 </span><span class="sxs-lookup"><span data-stu-id="b4942-159">Check the Windows Mixed Reality **Enable Depth Sharing** checkbox</span></span>
* <span data-ttu-id="b4942-160">将“立体渲染模式\*”更改为“单通道实例化”  </span><span class="sxs-lookup"><span data-stu-id="b4942-160">Set Stereo **Rendering Mode\*** to **Single Pass Instanced**</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> <span data-ttu-id="b4942-162">若要详细了解如何为 Windows Mixed Reality 优化 Unity，可参阅[建议用于 Unity 的设置](recommended-settings-for-unity.md)文档。</span><span class="sxs-lookup"><span data-stu-id="b4942-162">To learn more about optimizing Unity for Windows Mixed Reality, you can refer to the [Recommended settings for Unity](recommended-settings-for-unity.md) documentation.</span></span>

### <a name="3-enable-spatial-perception"></a><span data-ttu-id="b4942-163">3.启用空间感知</span><span class="sxs-lookup"><span data-stu-id="b4942-163">3. Enable spatial perception</span></span>

> [!NOTE]
> <span data-ttu-id="b4942-164">可以通过空间感知在 Windows Mixed Reality 设备上可视化空间映射网格。</span><span class="sxs-lookup"><span data-stu-id="b4942-164">Spatial perception allows visualization of the spatial mapping mesh on Windows Mixed Reality devices.</span></span>

<span data-ttu-id="b4942-165">在“项目设置”窗口中选择“播放器” > “发布设置”，展开“发布设置”：  </span><span class="sxs-lookup"><span data-stu-id="b4942-165">In the Project Settings window, select **Player** > **Publishing Settings** to expand the Publishing Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

<span data-ttu-id="b4942-167">在“发布设置”中，向下滚动到“功能”  部分，勾选“SpatialPerception”  复选框：</span><span class="sxs-lookup"><span data-stu-id="b4942-167">In the Publishing Settings, scroll down to the **Capabilities** section and check the **SpatialPerception** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

<span data-ttu-id="b4942-169">关闭“项目设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="b4942-169">Close the Project Settings window.</span></span>

## <a name="import-textmesh-pro-essential-resources"></a><span data-ttu-id="b4942-170">导入 TextMesh Pro 基本资源</span><span class="sxs-lookup"><span data-stu-id="b4942-170">Import TextMesh Pro Essential Resources</span></span>

> [!NOTE]
> <span data-ttu-id="b4942-171">我们导入此包是因为混合现实工具包的 UI 元素需要此包。</span><span class="sxs-lookup"><span data-stu-id="b4942-171">We are importing this package because it is required by Mixed Reality Toolkit's UI elements.</span></span>

<span data-ttu-id="b4942-172">在 Unity 菜单中，选择“窗口”   > “TextMeshPro”   >   “导入 TMP Pro 基本资源”：</span><span class="sxs-lookup"><span data-stu-id="b4942-172">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

<span data-ttu-id="b4942-174">在“导入 Unity 包”窗口中单击“全部”  按钮，确保选择所有资产，然后单击“导入”  按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="b4942-174">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="b4942-176">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="b4942-176">Import the Mixed Reality Toolkit</span></span>

<span data-ttu-id="b4942-177">下载 Unity 自定义包：</span><span class="sxs-lookup"><span data-stu-id="b4942-177">Download the Unity custom package:</span></span>

* [<span data-ttu-id="b4942-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b4942-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

<span data-ttu-id="b4942-179">在 Unity 菜单中选择“资产” > “导入包” > “自定义包...”，打开“导入包...”窗口：   </span><span class="sxs-lookup"><span data-stu-id="b4942-179">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

<span data-ttu-id="b4942-181">在“导入包...”窗口中，选择下载的 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage**，然后单击“打开”  按钮：</span><span class="sxs-lookup"><span data-stu-id="b4942-181">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

<span data-ttu-id="b4942-183">在“导入 Unity 包”窗口中单击“全部”  按钮，确保选择所有资产，然后单击“导入”  按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="b4942-183">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a><span data-ttu-id="b4942-185">配置用于混合现实工具包的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b4942-185">Configure the Unity project for the Mixed Reality Toolkit</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="b4942-186">在导入包后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="b4942-186">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="b4942-187">如果未显示该窗口，请将其打开，方法是：在 Unity 菜单中选择“混合现实工具包”   > “实用程序”   >   “配置 Unity 项目”。</span><span class="sxs-lookup"><span data-stu-id="b4942-187">If it does not, open it by selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** in the Unity menu.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

<span data-ttu-id="b4942-189">在“MRTK 项目配置器”窗口中，展开“修改配置”部分，<u>取消选中</u>“启用 MSBuild for Unity”复选框，确保勾选所有其他选项，然后单击“应用”按钮以应用设置：   </span><span class="sxs-lookup"><span data-stu-id="b4942-189">In the MRTK Project Configurator window, expand the **Modify Configurations** section, <u>uncheck</u> the **Enable MSBuild for Unity** checkbox, ensure all other options are checked, and click the **Apply** button to apply the settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="b4942-191">MSBuild for Unity 可能不支持你将使用的所有 SDK，在启用它后再禁用它可能比较困难。</span><span class="sxs-lookup"><span data-stu-id="b4942-191">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="b4942-192">因此，强烈建议不要启用 MSBuild for Unity。</span><span class="sxs-lookup"><span data-stu-id="b4942-192">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="b4942-193">配置混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="b4942-193">Configure the Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

<span data-ttu-id="b4942-194">在 Unity 菜单中选择“混合现实工具包”   >   “添加到场景并配置...”，将混合现实工具包添加到当前场景：</span><span class="sxs-lookup"><span data-stu-id="b4942-194">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the Mixed Reality Toolkit to your current scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

<span data-ttu-id="b4942-196">在“层次结构”窗口中选择 MixedRealityToolkit 对象后，请在“检查器”窗口中验证混合现实工具包配置文件是否已设置为 **DefaultMixedRealityToolkitConfigurationProfile**：</span><span class="sxs-lookup"><span data-stu-id="b4942-196">With the MixedRealityToolkit object selected in the Hierarchy window, in the Inspector window, verify the Mixed Reality Toolkit configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> <span data-ttu-id="b4942-198">通常，在针对 HoloLens 进行开发时会使用 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="b4942-198">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens 2.</span></span> <span data-ttu-id="b4942-199">但是，在本教程中，你将使用 DefaultMixedRealityToolkitConfigurationProfile，然后在下一教程（[创建用户界面并配置混合现实工具包](mrlearning-base-ch2.md)）中，你将改用 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="b4942-199">However, for the purpose of this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="b4942-200">在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口：  </span><span class="sxs-lookup"><span data-stu-id="b4942-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

<span data-ttu-id="b4942-202">在“保存场景”窗口中，导航到项目的 **Scenes** 文件夹中，为场景提供一个合适的名称（例如“GettingStarted”  ），然后单击“保存”  按钮以保存场景：</span><span class="sxs-lookup"><span data-stu-id="b4942-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="b4942-204">在设备上构建应用程序</span><span class="sxs-lookup"><span data-stu-id="b4942-204">Build your application to your device</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="b4942-205">1.生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="b4942-205">1. Build the Unity project</span></span>

<span data-ttu-id="b4942-206">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口。  </span><span class="sxs-lookup"><span data-stu-id="b4942-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="b4942-207">在“生成设置”窗口中单击“添加打开的场景”  按钮，将当前场景添加到“生成中的场景”列表  ，然后单击“生成”  按钮以打开“生成通用 Windows 平台”窗口：</span><span class="sxs-lookup"><span data-stu-id="b4942-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

<span data-ttu-id="b4942-209">在“生成通用 Windows 平台”窗口中，选择用于存储生成的适当位置（例如 _D:\MixedRealityLearning\Builds_），创建一个新文件夹并为其指定适当的名称（例如 _GettingStarted_），然后单击“选择文件夹”  按钮，启动生成过程：</span><span class="sxs-lookup"><span data-stu-id="b4942-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

<span data-ttu-id="b4942-211">等待 Unity 完成生成过程：</span><span class="sxs-lookup"><span data-stu-id="b4942-211">Wait for Unity to finish the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="b4942-213">2.生成并部署应用程序</span><span class="sxs-lookup"><span data-stu-id="b4942-213">2. Build and deploy the application</span></span>

<span data-ttu-id="b4942-214">生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。</span><span class="sxs-lookup"><span data-stu-id="b4942-214">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="b4942-215">在文件夹内导航，然后双击解决方案文件，在 Visual Studio 中其打开：</span><span class="sxs-lookup"><span data-stu-id="b4942-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> <span data-ttu-id="b4942-217">如果 Visual Studio 要求安装新组件，请花一点时间确保按照[安装工具](install-the-tools.md)文档中的说明安装所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="b4942-217">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the [Install the Tools](install-the-tools.md) documentation.</span></span>

<span data-ttu-id="b4942-218">通过选择“Master”配置或“发布”配置、“ARM”体系结构和“设备”作为目标，配置 Visual Studio for HoloLens 2。    </span><span class="sxs-lookup"><span data-stu-id="b4942-218">Configure Visual Studio for HoloLens 2 by selecting the **Master** or **Release** configuration, the **ARM** architecture, and **Device** as target:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

> [!NOTE]
> <span data-ttu-id="b4942-220">如果未看到“设备”选项，可能需要将默认启动项目从 IC2Lpp 项目更改为你的 UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="b4942-220">If you don't see Device as an option you may need to change the default start up project from the IC2Lpp project to your UWP Project.</span></span> <span data-ttu-id="b4942-221">在“解决方案资源管理器”中，右键单击“yourprojectname (通用 Windows)”并选择“设为启动项目”。   </span><span class="sxs-lookup"><span data-stu-id="b4942-221">In the **Solution Explorer**, right click on **yourprojectname (Universal Windows)** and select **Set as StartUp Project**.</span></span> 

<span data-ttu-id="b4942-222">将 HoloLens 2 连接到计算机。</span><span class="sxs-lookup"><span data-stu-id="b4942-222">Connect your HoloLens 2 to your computer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4942-223">在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。</span><span class="sxs-lookup"><span data-stu-id="b4942-223">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="b4942-224">这两个步骤都可以按照[这些说明](using-visual-studio.md)来完成。</span><span class="sxs-lookup"><span data-stu-id="b4942-224">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

<span data-ttu-id="b4942-225">最后一步是选择“调试” > “在不调试的情况下启动”，以便生成相关内容并将其部署到设备：  </span><span class="sxs-lookup"><span data-stu-id="b4942-225">The final step is to build and deploy to your device by selecting **Debug** > **Start Without Debugging**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

<span data-ttu-id="b4942-227">虽然这些说明假设你会将内容部署到 HoloLens 2 设备，但你也可以将内容部署到 [HoloLens 2 仿真器](using-the-hololens-emulator.md)，或创建[用于旁加载的应用包](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)。</span><span class="sxs-lookup"><span data-stu-id="b4942-227">While these instructions assume you will be deploying to a HoloLens 2 device, you can also deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span></span>

<span data-ttu-id="b4942-228">选择“在不调试的情况下启动”会导致应用程序在成功生成后立即在设备上启动，但不会在 Visual Studio 中附加调试程序和显示调试信息。</span><span class="sxs-lookup"><span data-stu-id="b4942-228">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="b4942-229">这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="b4942-229">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

<span data-ttu-id="b4942-230">若要在不自动启动应用程序的情况下将内容部署到设备，可以选择“生成”>“部署解决方案”。</span><span class="sxs-lookup"><span data-stu-id="b4942-230">To deploy to your device without having the application start automatically, you can select Build > Deploy Solution.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b4942-231">祝贺</span><span class="sxs-lookup"><span data-stu-id="b4942-231">Congratulations</span></span>

<!-- TODO: Consider cleanup and adding in app screenshots -->
<span data-ttu-id="b4942-232">你现在已经部署了第一个 HoloLens 2 应用程序。</span><span class="sxs-lookup"><span data-stu-id="b4942-232">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="b4942-233">当你四处走动时，应该看到空间映射网格覆盖了 HoloLens 2 感知到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="b4942-233">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="b4942-234">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用程序性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="b4942-234">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="b4942-235">这些只是混合现实工具包中开箱即用的一些基本功能。</span><span class="sxs-lookup"><span data-stu-id="b4942-235">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="b4942-236">在接下来的教程中，我们将开始为场景添加更多的内容和交互性，以便充分探索 HoloLens 2 和混合现实工具包的功能。</span><span class="sxs-lookup"><span data-stu-id="b4942-236">In the tutorials to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="b4942-237">在应用中，你可能会注意到诊断探查器。可以使用语音命令“切换诊断”来切换其可见性。 </span><span class="sxs-lookup"><span data-stu-id="b4942-237">In the app, you may notice the Diagnostics profiler, you can toggle it's visibility using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="b4942-238">但是，通常建议在开发过程中让探查器始终保持可见状态，这样就可以了解何时对应用所做的更改会影响性能，例如，HoloLens 2 应用程序会[在 60 FPS 连续运行](understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="b4942-238">However, it is generally recommended to keep the profiler visible at all times during development to understand when changes to the app may have impacted performance, for example, HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="b4942-239">下一教程：3.创建用户界面并配置混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="b4942-239">Next Tutorial: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
