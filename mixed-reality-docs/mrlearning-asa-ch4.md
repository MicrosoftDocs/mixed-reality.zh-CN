---
title: Azure 空间定位点教程 - 4. 适用于 Android 和 iOS 的 Azure 空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 空间定位点。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: 混合现实, unity, 教程, 课程, hololens, azure, 空间定位点
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867619"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="e2b00-105">4.适用于 Android 和 iOS 的 Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="e2b00-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="e2b00-106">在本教程中，你将学习如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件对 Android 和 iOS 设备生成项目。</span><span class="sxs-lookup"><span data-stu-id="e2b00-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="e2b00-107">目标</span><span class="sxs-lookup"><span data-stu-id="e2b00-107">Objectives</span></span>

* <span data-ttu-id="e2b00-108">学习如何使用 Unity AR Foundation 和 ARCore XR 插件对 Android 设备生成项目。</span><span class="sxs-lookup"><span data-stu-id="e2b00-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="e2b00-109">学习如何使用 Unity AR Foundation 和 ARKit XR 插件对 iOS 设备生成项目。</span><span class="sxs-lookup"><span data-stu-id="e2b00-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

[!NOTE] <span data-ttu-id="e2b00-110">要完成本教程，请确保你已学完 Azure 空间定位点教程的 [Azure 空间定位点入门](mrlearning-asa-ch1.md)。</span><span class="sxs-lookup"><span data-stu-id="e2b00-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="e2b00-111">添加内置 Unity 包</span><span class="sxs-lookup"><span data-stu-id="e2b00-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="e2b00-112">在本部分，你将安装 Unity 内置的 AR Foundation、ARCore XR 插件和 ARKit XR 插件包，需使用这些包来支持 Android 和 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="e2b00-112">In this section, you will install Unity's inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="e2b00-113">请务必安装这些 Unity 包的正确版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e2b00-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="e2b00-114">**AR Foundation 2.1.4**</span><span class="sxs-lookup"><span data-stu-id="e2b00-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="e2b00-115">**ARCore XR 插件 2.2.0 预览版 2**</span><span class="sxs-lookup"><span data-stu-id="e2b00-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="e2b00-116">**ARKit XR 插件 2.1.1**</span><span class="sxs-lookup"><span data-stu-id="e2b00-116">**ARKit XR plugin 2.1.1**</span></span>

[!NOTE] <span data-ttu-id="e2b00-117">如果你要为 Android 开发此项目，则无需安装 ARKit XR 插件包。</span><span class="sxs-lookup"><span data-stu-id="e2b00-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="e2b00-118">同样，如果你要为 iOS 开发此项目，则无需安装 ARCore XR 插件。</span><span class="sxs-lookup"><span data-stu-id="e2b00-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="e2b00-119">在 Unity 菜单中，选择“窗口” > “包管理器”： </span><span class="sxs-lookup"><span data-stu-id="e2b00-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="e2b00-121">所有包可能几秒后才会在列表中显示。</span><span class="sxs-lookup"><span data-stu-id="e2b00-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="e2b00-122">单击“高级”选项，再选择“显示预览包”来显示它</span><span class="sxs-lookup"><span data-stu-id="e2b00-122">Display preview packages by clicking on Advanced option and select "**Show preview packages.**"</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="e2b00-124">在包管理器窗口中选择 AR Foundation，你将在这里看到多个版本，你需要选择版本 2.1.4 并单击“更新到 2.1.4”按钮来更新包 ：</span><span class="sxs-lookup"><span data-stu-id="e2b00-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select version 2.1.4 and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="e2b00-126">要支持 Android 设备，可按相同的过程导入 ARCore XR 插件 2.2.0 预览版 2。</span><span class="sxs-lookup"><span data-stu-id="e2b00-126">To support Android devices, follow the same process to import ARCore XR Plugin 2.2.0 preview 2.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="e2b00-128">要支持 iOS 设备，则应从包管理器中导入“ARKit XR 插件 2.1.1”Unity 包。</span><span class="sxs-lookup"><span data-stu-id="e2b00-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="e2b00-130">自定义 MRTK 来支持 AR Foundation 相机</span><span class="sxs-lookup"><span data-stu-id="e2b00-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="e2b00-131">通过在“层次结构”窗口中选择 MixedRealityToolKit，自定义 MRTK 设置来支持 AR Foundation，然后在检查器窗口的混合现实工具包中单击“克隆”按钮。</span><span class="sxs-lookup"><span data-stu-id="e2b00-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="e2b00-133">单击“克隆”按钮时，会出现一个新的“克隆配置文件”窗口，请再次单击“克隆”按钮来克隆 DefaultMixedRealityToolkitProfile。</span><span class="sxs-lookup"><span data-stu-id="e2b00-133">When you click the **Clone** button, a new Clone Profile window will appear, click on the Clone button again to clone the DefaultMixedRealityToolkitProfile.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="e2b00-135">同样地，在检查器窗口中克隆相机配置文件，将该配置文件重命名为“UnityARConfigurationProfile”，并单击“克隆”按钮。</span><span class="sxs-lookup"><span data-stu-id="e2b00-135">Similarly, clone the camera profile in the Inspector window and rename the profile to “UnityARConfigurationProfile” and click on the **Clone** button.</span></span> <span data-ttu-id="e2b00-136">在检查器窗口中，找到 MixedReality，然后选择“相机”选项卡。在检查器窗口展开相机设置提供程序，然后单击“+添加相机设置提供程序”，展开“新数据提供程序 1”，选择类型“无”，再选择“Microsoft .MixedReality.Toolkit.Experimental.UnityAR”，最后选择“UnityARCameraSettings”    。</span><span class="sxs-lookup"><span data-stu-id="e2b00-136">In the Inspector window, locate the MixedReality, select the Camera tab Expand the camera setting providers in the inspector window and click on **+Add Camera Setting Provider** > expand **New data provider 1**> select Type **None** >select **Microsoft .MixedReality.Toolkit.Experimental.UnityAR** > Select **UnityARCameraSettings**.</span></span>


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="e2b00-138">在“层次结构”窗口中选择 MixedRealityToolKit 对象后，单击“添加组件”按钮在检查器窗口中附加支持脚本，然后键入“AR 引用点管理器”并选择该脚本。</span><span class="sxs-lookup"><span data-stu-id="e2b00-138">With the MixedRealityToolKit object selected in the Hierarchy window, in the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="e2b00-139">如果添加“AR 引用点管理器”脚本，则将在检查器窗口中随附该脚本自动添加“AR 会话来源”。</span><span class="sxs-lookup"><span data-stu-id="e2b00-139">Adding the  "AR Reference Point Manager" script will automatically add "AR session origin" along with it in the Inspector window.</span></span> <span data-ttu-id="e2b00-140">添加支持脚本后，检查器窗口如下所示。</span><span class="sxs-lookup"><span data-stu-id="e2b00-140">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a><span data-ttu-id="e2b00-142">对 Android 设备生成应用程序</span><span class="sxs-lookup"><span data-stu-id="e2b00-142">Build application to Android device</span></span>

<span data-ttu-id="e2b00-143">要对 Android 设备生成此应用程序，请单击窗口顶部的“文件”，然后选择“生成设置” 。</span><span class="sxs-lookup"><span data-stu-id="e2b00-143">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="e2b00-144">屏幕上将显示一个新窗口，选择“Android”，然后单击“切换平台” 。</span><span class="sxs-lookup"><span data-stu-id="e2b00-144">A new window will appear on the screen, select **Android,** and click on the **Switch Platform**.</span></span> <span data-ttu-id="e2b00-145">切换平台需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="e2b00-145">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="e2b00-146">切换到 Android 平台后，单击“添加打开的场景”，确保你当前的场景是“生成中的场景”列表中唯一选中的场景 。</span><span class="sxs-lookup"><span data-stu-id="e2b00-146">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="e2b00-148">关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="e2b00-148">Close the **Build Settings** window.</span></span> <span data-ttu-id="e2b00-149">在 Unity 菜单中，选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”，然后单击“应用”，为 Android 平台配置 Unity 项目   。</span><span class="sxs-lookup"><span data-stu-id="e2b00-149">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="e2b00-151">在 Unity 菜单中选择“编辑” > “项目设置”，打开“项目设置”窗口 。</span><span class="sxs-lookup"><span data-stu-id="e2b00-151">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="e2b00-152">在“项目设置”窗口中，选择“播放器”选项卡，展开“其他设置”部分，然后选择“Vulkan”并单击“-”符号将它删除 。</span><span class="sxs-lookup"><span data-stu-id="e2b00-152">In the Project Settings, window selects the **Player** tab, expand the Other Settings section, select **Vulkan,** and remove it by clicking the "-" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="e2b00-154">关闭“播放器设置”窗口，再次打开“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="e2b00-154">Close the Player Settings window and open the Build Settings window again.</span></span> <span data-ttu-id="e2b00-155">然后，使用 USB 线缆将 Android 设备连接到计算机，并在“生成和运行位置”下拉列表中选择你的设备，然后单击“生成并运行” 。</span><span class="sxs-lookup"><span data-stu-id="e2b00-155">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run on** the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="e2b00-156">系统会要求你保存一个 .apk 文件，可选择任意名称。</span><span class="sxs-lookup"><span data-stu-id="e2b00-156">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="e2b00-158">如果在 Unity 控制台窗口中收到任何与 Android SDK、NDK 和/或 JDK 模块相关的错误，则需要打开 Unity Hub，然后为 Android 生成支持模块安装关联的 SDK、NDK 和 JDK 模块。</span><span class="sxs-lookup"><span data-stu-id="e2b00-158">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="e2b00-159">生成过程完成后，应用程序应会在 Android 设备上自动加载。</span><span class="sxs-lookup"><span data-stu-id="e2b00-159">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-application-to-ios-device"></a><span data-ttu-id="e2b00-160">对 iOS 设备生成应用程序</span><span class="sxs-lookup"><span data-stu-id="e2b00-160">Build application to iOS Device</span></span>

<span data-ttu-id="e2b00-161">要对 iOS 设备生成此应用程序，请单击窗口顶部的“文件”，然后选择“生成设置” 。</span><span class="sxs-lookup"><span data-stu-id="e2b00-161">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="e2b00-162">屏幕上将显示一个新窗口，选择“iOS”，然后单击“切换平台” 。</span><span class="sxs-lookup"><span data-stu-id="e2b00-162">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="e2b00-164">关闭“生成设置”窗口。</span><span class="sxs-lookup"><span data-stu-id="e2b00-164">Close the **Build Settings** window.</span></span> <span data-ttu-id="e2b00-165">在 Unity 菜单中，选择“混合现实工具包” > “实用程序” > “配置 Unity 项目”，然后单击“应用”，为 iOS 平台配置 Unity 项目   。</span><span class="sxs-lookup"><span data-stu-id="e2b00-165">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="e2b00-167">要生成 iOS XCode 项目，请转到“生成设置”并单击“生成”。</span><span class="sxs-lookup"><span data-stu-id="e2b00-167">To build the iOS XCode project, go to Build Settings and, click on **Build**.</span></span>

<span data-ttu-id="e2b00-168">按照[本指南](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)了解如何将此项目部署到 iOS 设备中。</span><span class="sxs-lookup"><span data-stu-id="e2b00-168">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e2b00-169">祝贺</span><span class="sxs-lookup"><span data-stu-id="e2b00-169">Congratulations</span></span>

<span data-ttu-id="e2b00-170">在本教程中，你学习了如何为 Android 和 iOS 设备生成项目。</span><span class="sxs-lookup"><span data-stu-id="e2b00-170">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="e2b00-171">你还学习了如何使用 AR Foundation、ARCore XR 插件和 ARKit XR 插件来让你的项目适用于 Android 和 iOS 设备。</span><span class="sxs-lookup"><span data-stu-id="e2b00-171">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>