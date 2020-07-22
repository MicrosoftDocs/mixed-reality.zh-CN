---
title: 入门教程 - 2. 初始化项目并部署第一个应用程序
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4f72f70b9eaac159f7d9231e61f23d18d708d0c7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304270"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="3be20-105">2.初始化项目并部署第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="3be20-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="3be20-106">概述</span><span class="sxs-lookup"><span data-stu-id="3be20-106">Overview</span></span>

<span data-ttu-id="3be20-107">在本教程中，你将了解如何创建新的 Unity 项目、如何配置该项目以进行<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">混合现实工具包 (MRTK)</a> 开发，以及如何导入 MRTK。</span><span class="sxs-lookup"><span data-stu-id="3be20-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="3be20-108">你还将演练如何配置和生成基本 Unity 示例场景，并将其从 Visual Studio 部署到 HoloLens 2 或模拟器。</span><span class="sxs-lookup"><span data-stu-id="3be20-108">You'll also walk through configuring, building, and deploying the basic Unity sample scene from Visual Studio to your HoloLens 2 or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="3be20-109">目标</span><span class="sxs-lookup"><span data-stu-id="3be20-109">Objectives</span></span>

* <span data-ttu-id="3be20-110">了解如何配置用于 HoloLens 开发的 Unity</span><span class="sxs-lookup"><span data-stu-id="3be20-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="3be20-111">了解如何生成应用并将其部署到 HoloLens</span><span class="sxs-lookup"><span data-stu-id="3be20-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="3be20-112">体验空间映射网格、手部网格和帧率计数器</span><span class="sxs-lookup"><span data-stu-id="3be20-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="3be20-113">创建 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="3be20-113">Creating the Unity project</span></span>

<span data-ttu-id="3be20-114">启动“Unity 中心”，选择“项目”选项卡，然后单击“新建”按钮旁边的**向下箭头**：</span><span class="sxs-lookup"><span data-stu-id="3be20-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="3be20-116">在下拉列表中，选择[先决条件](mr-learning-base-01.md#prerequisites)中指定的 Unity 版本：</span><span class="sxs-lookup"><span data-stu-id="3be20-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="3be20-118">如果 Unity Hub 没有特定的 Unity 版本，可以从 Unity 的 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">下载存档</a>启动安装。</span><span class="sxs-lookup"><span data-stu-id="3be20-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="3be20-119">在“创建新项目”窗口中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="3be20-119">In the Create a new project window:</span></span>

* <span data-ttu-id="3be20-120">确保将“模板”设置为“3D” </span><span class="sxs-lookup"><span data-stu-id="3be20-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="3be20-121">输入合适的“项目名称”，例如“MRTK 教程”</span><span class="sxs-lookup"><span data-stu-id="3be20-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="3be20-122">选择合适的“位置”来存储项目，例如“D:\MixedRealityLearning”</span><span class="sxs-lookup"><span data-stu-id="3be20-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="3be20-123">单击“创建”按钮，创建并启动新的 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="3be20-123">Click the **Create** button to create and launch your new Unity project</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="3be20-125">在 Windows 上工作时，有 255 个字符的 MAX_PATH 限制。</span><span class="sxs-lookup"><span data-stu-id="3be20-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="3be20-126">因此，应将 Unity 项目保存到驱动器的根目录附近。</span><span class="sxs-lookup"><span data-stu-id="3be20-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="3be20-127">等待 Unity 创建项目：</span><span class="sxs-lookup"><span data-stu-id="3be20-127">Wait for Unity to create the project:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="3be20-129">切换生成平台</span><span class="sxs-lookup"><span data-stu-id="3be20-129">Switching the build platform</span></span>

<span data-ttu-id="3be20-130">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="3be20-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="3be20-132">在“生成设置”窗口中选择“通用 Windows 平台”，然后单击“切换平台”按钮： </span><span class="sxs-lookup"><span data-stu-id="3be20-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="3be20-134">等待 Unity 完成平台切换操作：</span><span class="sxs-lookup"><span data-stu-id="3be20-134">Wait for Unity to finish switching the platform:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="3be20-136">当 Unity 完成平台切换后，单击红色 **x** 图标，关闭“生成设置”窗口：</span><span class="sxs-lookup"><span data-stu-id="3be20-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="3be20-138">导入 TextMeshPro 基本资源</span><span class="sxs-lookup"><span data-stu-id="3be20-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="3be20-139">在 Unity 菜单中，选择“窗口” > “TextMeshPro” > “导入 TMP 基本资源”以打开“导入 Unity 包”窗口  ：</span><span class="sxs-lookup"><span data-stu-id="3be20-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="3be20-141">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="3be20-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="3be20-143">MRTK 的 UI 元素需要 TextMeshPro 基本资源。</span><span class="sxs-lookup"><span data-stu-id="3be20-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="3be20-144">如果你不打算在项目中使用 MRTK 的 UI 元素，则可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="3be20-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="3be20-145">导入混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="3be20-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="3be20-146">下载 Unity 自定义包：</span><span class="sxs-lookup"><span data-stu-id="3be20-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="3be20-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="3be20-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

<span data-ttu-id="3be20-148">在 Unity 菜单中选择“资产” > “导入包” > “自定义包...”，打开“导入包...”窗口：  </span><span class="sxs-lookup"><span data-stu-id="3be20-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="3be20-150">在“导入包…”窗口中，选择下载的 Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage，然后单击“打开”按钮 ：</span><span class="sxs-lookup"><span data-stu-id="3be20-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="3be20-152">在“导入 Unity 包”窗口中单击“全部”按钮，确保选择所有资产，然后单击“导入”按钮以导入资产：</span><span class="sxs-lookup"><span data-stu-id="3be20-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="3be20-154">配置 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="3be20-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="3be20-155">1.应用 MRTK 项目配置器设置</span><span class="sxs-lookup"><span data-stu-id="3be20-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="3be20-156">Unity 完成上一部分中的导入包操作后，应显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="3be20-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="3be20-157">如果未显示，请转到 Unity 菜单，并选择“混合现实工具包” > “实用工具” > “配置 Unity 项目”  ：</span><span class="sxs-lookup"><span data-stu-id="3be20-157">If it doesn't, open the Configurator window by going to the Unity menu and selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="3be20-159">在“MRTK 项目配置器”窗口中，展开“修改配置”部分，确保勾选所有选项，然后单击“应用”按钮以应用设置 ：</span><span class="sxs-lookup"><span data-stu-id="3be20-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="3be20-161">2.配置其他项目设置</span><span class="sxs-lookup"><span data-stu-id="3be20-161">2. Configure additional project settings</span></span>

<span data-ttu-id="3be20-162">在 Unity 菜单中选择“编辑” > “项目设置...”，打开“项目设置”窗口： </span><span class="sxs-lookup"><span data-stu-id="3be20-162">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="3be20-164">在“项目设置”窗口中，选择“播放器” > “XR 设置”，单击 + 图标，然后选择“Windows Mixed Reality”以添加 Windows Mixed Reality SDK  ：</span><span class="sxs-lookup"><span data-stu-id="3be20-164">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="3be20-166">Unity 导入完 Windows Mixed Reality SDK 后，应再次显示“MRTK 项目配置器”窗口。</span><span class="sxs-lookup"><span data-stu-id="3be20-166">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="3be20-167">如果未显示，请使用 Unity 菜单打开它。</span><span class="sxs-lookup"><span data-stu-id="3be20-167">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="3be20-168">在“MRTK 项目配置器”窗口中，使用“音频空间定位器”下拉列表选择 MS HRTF Spatializer，然后单击“应用”按钮以应用该设置  ：</span><span class="sxs-lookup"><span data-stu-id="3be20-168">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="3be20-170">在“项目设置”窗口中，选择“播放器” > “XR 设置”，然后使用“深度格式”下拉列表选“16 位深度”   ：</span><span class="sxs-lookup"><span data-stu-id="3be20-170">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="3be20-172">在“项目设置”窗口中，选择“播放器” > “发布设置”，然后在“包名称”字段中，输入合适的名称，例如 MRTKTutorials-GettingStarted  ：</span><span class="sxs-lookup"><span data-stu-id="3be20-172">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> <span data-ttu-id="3be20-174">“包名称”是应用的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="3be20-174">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="3be20-175">在部署应用之前应更改此标识符，以免覆盖以前安装的应用。</span><span class="sxs-lookup"><span data-stu-id="3be20-175">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="3be20-176">“产品名称”是在 HoloLens“开始”菜单中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="3be20-176">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="3be20-177">要更轻松地在开发期间查找应用，请在名称前面添加一个下划线，以将其排在顶部。</span><span class="sxs-lookup"><span data-stu-id="3be20-177">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="3be20-178">创建和配置场景</span><span class="sxs-lookup"><span data-stu-id="3be20-178">Creating and configuring the scene</span></span>

<span data-ttu-id="3be20-179">在 Unity 菜单中，选择“文件” > “新建场景”，以创建新场景 ：</span><span class="sxs-lookup"><span data-stu-id="3be20-179">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="3be20-181">在 Unity 菜单中，选择“混合现实工具包” > “添加到场景并配置…”，将 MRTK 添加到当前场景 ：</span><span class="sxs-lookup"><span data-stu-id="3be20-181">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="3be20-183">仍在“层次结构”窗口中选中 MixedRealityToolkit 对象，在“检查器”窗口中验证 MixedRealityToolkit 配置文件是否已设置为 DefaultMixedRealityToolkitConfigurationProfile  ：</span><span class="sxs-lookup"><span data-stu-id="3be20-183">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="3be20-185">通常，在针对 HoloLens 进行开发时会使用 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="3be20-185">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="3be20-186">但在本教程中，将使用 DefaultMixedRealityToolkitConfigurationProfile，在下一教程（[配置 MRTK 配置文件](mr-learning-base-03.md)）中，将改用 DefaultHoloLens2ConfigurationProfile。</span><span class="sxs-lookup"><span data-stu-id="3be20-186">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="3be20-187">在 Unity 菜单中选择“文件” > “另存为...”，打开“保存场景”窗口： </span><span class="sxs-lookup"><span data-stu-id="3be20-187">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="3be20-189">在“保存场景”窗口中，导航到项目的 **Scenes** 文件夹中，为场景提供一个合适的名称（例如“GettingStarted”），然后单击“保存”按钮以保存场景：</span><span class="sxs-lookup"><span data-stu-id="3be20-189">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="3be20-191">将应用程序构建到 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3be20-191">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="3be20-192">1.生成 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="3be20-192">1. Build the Unity project</span></span>

<span data-ttu-id="3be20-193">在 Unity 菜单中选择“文件” > “生成设置...”，打开“生成设置”窗口。 </span><span class="sxs-lookup"><span data-stu-id="3be20-193">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="3be20-194">在“生成设置”窗口中单击“添加打开的场景”按钮，将当前场景添加到“生成中的场景”列表，然后单击“生成”按钮以打开“生成通用 Windows 平台”窗口：</span><span class="sxs-lookup"><span data-stu-id="3be20-194">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="3be20-196">在“生成通用 Windows 平台”窗口中，选择用于存储生成的适当位置（例如 _D:\MixedRealityLearning\Builds_），创建一个新文件夹并为其指定适当的名称（例如 _GettingStarted_），然后单击“选择文件夹”按钮，启动生成过程：</span><span class="sxs-lookup"><span data-stu-id="3be20-196">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="3be20-198">等待 Unity 完成生成过程：</span><span class="sxs-lookup"><span data-stu-id="3be20-198">Wait for Unity to finish the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="3be20-200">2.生成并部署应用程序</span><span class="sxs-lookup"><span data-stu-id="3be20-200">2. Build and deploy the application</span></span>

<span data-ttu-id="3be20-201">生成过程完成后，Unity 会提示 Windows 文件资源管理器打开你存储生成的位置。</span><span class="sxs-lookup"><span data-stu-id="3be20-201">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="3be20-202">在文件夹内导航，然后双击解决方案文件，在 Visual Studio 中其打开：</span><span class="sxs-lookup"><span data-stu-id="3be20-202">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="3be20-204">如果 Visual Studio 要求安装新组件，请花一点时间确保拥有[安装工具](install-the-tools.md)文档中的所有必备组件。</span><span class="sxs-lookup"><span data-stu-id="3be20-204">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="3be20-205">通过选择“Master”配置或“发布”配置、ARM64 体系结构和“设备”作为目标，配置 Visual Studio for HoloLens   ：</span><span class="sxs-lookup"><span data-stu-id="3be20-205">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="3be20-207">如果要部署到 HoloLens（第一代），请选择 x86 体系结构。</span><span class="sxs-lookup"><span data-stu-id="3be20-207">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="3be20-208">对于 HoloLens，通常是针对 ARM 体系结构进行生成。</span><span class="sxs-lookup"><span data-stu-id="3be20-208">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="3be20-209">但是，在 Unity 2019.3 中有一个 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>已知问题</strong></a>，即在 Visual Studio 中选择 ARM 作为生成体系结构时会导致错误。</span><span class="sxs-lookup"><span data-stu-id="3be20-209">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="3be20-210">建议的解决方法是针对 ARM64 进行生成。</span><span class="sxs-lookup"><span data-stu-id="3be20-210">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="3be20-211">如果该方法不可行，请前往“编辑”>“项目设置”>“播放器”>“其他设置”并禁用“图形作业” 。</span><span class="sxs-lookup"><span data-stu-id="3be20-211">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="3be20-212">如果目标选项中没有“设备”，则可能需要将 Visual Studio 解决方案的启动项目从 IL2CPP 项目更改为 UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="3be20-212">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="3be20-213">在“解决方案资源管理器”中，右键单击“YourProjectName (通用 Windows)”并选择“设为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="3be20-213">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="3be20-214">将 HoloLens 连接到计算机，然后选择“调试” > “启动但不调试”，以生成并部署到你的设备 ：</span><span class="sxs-lookup"><span data-stu-id="3be20-214">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="3be20-216">在生成到设备之前，设备必须处于开发人员模式并与开发计算机配对。</span><span class="sxs-lookup"><span data-stu-id="3be20-216">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="3be20-217">这两个步骤都可以按照[这些说明](using-visual-studio.md)来完成。</span><span class="sxs-lookup"><span data-stu-id="3be20-217">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="3be20-218">你还可以部署到 [HoloLens 模拟器](using-the-hololens-emulator.md)或创建[应用包](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)用于旁加载。</span><span class="sxs-lookup"><span data-stu-id="3be20-218">You can also deploy to the [HoloLens Emulator](using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="3be20-219">使用“启动但不调试”会自动启动设备上的应用，而不会连接 Visual Studio 调试器。</span><span class="sxs-lookup"><span data-stu-id="3be20-219">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="3be20-220">选择“生成”>“部署解决方案”，在不自动启动应用的情况下将内容部署到设备。</span><span class="sxs-lookup"><span data-stu-id="3be20-220">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="3be20-221">在应用中，你可能会注意到诊断探查器，可以使用语音命令“切换诊断”来切换其可见性。</span><span class="sxs-lookup"><span data-stu-id="3be20-221">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="3be20-222">我们建议你在开发过程中使探查器在大部分时间都可见，以便了解何时更改应用可能会影响性能。</span><span class="sxs-lookup"><span data-stu-id="3be20-222">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="3be20-223">例如，HoloLens 应用应以 [60 Fps 连续运行](understanding-performance-for-mixed-reality.md)。</span><span class="sxs-lookup"><span data-stu-id="3be20-223">For example, HoloLens apps should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="3be20-224">祝贺</span><span class="sxs-lookup"><span data-stu-id="3be20-224">Congratulations</span></span>

<span data-ttu-id="3be20-225">现在，你已经部署了第一个 HoloLens 2 应用。</span><span class="sxs-lookup"><span data-stu-id="3be20-225">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="3be20-226">四处浏览一下，应该会看到空间映射网格覆盖了 HoloLens 感知到的所有表面。</span><span class="sxs-lookup"><span data-stu-id="3be20-226">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="3be20-227">此外，你应该在你的手和手指上看到用于手部跟踪的指示器，以及用于监视应用性能的帧速率计数器。</span><span class="sxs-lookup"><span data-stu-id="3be20-227">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="3be20-228">这些只是 MRTK 附带的几个基础功能。</span><span class="sxs-lookup"><span data-stu-id="3be20-228">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="3be20-229">在接下来的教程中，我们将向场景添加内容，以探索 HoloLens 和 MRTK 的各种功能。</span><span class="sxs-lookup"><span data-stu-id="3be20-229">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

[<span data-ttu-id="3be20-230">下一教程：3.配置 MRTK 配置文件</span><span class="sxs-lookup"><span data-stu-id="3be20-230">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
