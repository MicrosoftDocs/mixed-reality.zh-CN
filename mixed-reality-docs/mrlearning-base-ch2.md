---
title: 入门教程 - 3. 创建用户界面并配置混合现实工具包
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376134"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="9719b-105">3.创建用户界面并配置混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="9719b-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="9719b-106">在前一篇教程中，你已通过启动适用于 HoloLens 2 的第一个应用程序，了解了混合现实工具包 (MRTK) 提供的某些功能。</span><span class="sxs-lookup"><span data-stu-id="9719b-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="9719b-107">本教程将会介绍如何创建按钮并在 UI 文本面板中对其进行组织，然后使用默认的交互（触摸）方式来与每个按钮交互。</span><span class="sxs-lookup"><span data-stu-id="9719b-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="9719b-108">此外，本课还会探讨如何添加简单的操作和效果，例如更改对象的大小、声音和颜色。</span><span class="sxs-lookup"><span data-stu-id="9719b-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="9719b-109">本模块将介绍有关如何修改 MRTK 配置文件的基本概念，首先介绍如何禁用[空间映射](spatial-mapping.md)网格可视化。</span><span class="sxs-lookup"><span data-stu-id="9719b-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="9719b-110">目标</span><span class="sxs-lookup"><span data-stu-id="9719b-110">Objectives</span></span>

* <span data-ttu-id="9719b-111">自定义和配置混合现实工具包配置文件</span><span class="sxs-lookup"><span data-stu-id="9719b-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="9719b-112">使用 UI 元素和按钮来与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="9719b-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="9719b-113">基本的手动跟踪输入和交互</span><span class="sxs-lookup"><span data-stu-id="9719b-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="9719b-114">如何配置混合现实工具包配置文件（更改空间感知显示选项）</span><span class="sxs-lookup"><span data-stu-id="9719b-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="9719b-115">本部分介绍如何自定义和配置默认的 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="9719b-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="9719b-116">此特定示例将演示如何通过更改空间网格观察程序的设置来隐藏空间感知网格。</span><span class="sxs-lookup"><span data-stu-id="9719b-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="9719b-117">但是，可以按照相同的原则来自定义 MRTK 配置文件中的任何设置或值。</span><span class="sxs-lookup"><span data-stu-id="9719b-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="9719b-118">隐藏空间感知网格所要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="9719b-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="9719b-119">克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="9719b-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="9719b-120">启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="9719b-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="9719b-121">克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="9719b-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="9719b-122">克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="9719b-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="9719b-123">更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="9719b-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="9719b-124">默认情况下，MRTK 配置文件不可编辑。</span><span class="sxs-lookup"><span data-stu-id="9719b-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="9719b-125">这是一些默认的配置文件模板，必须先克隆它们，然后才能对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="9719b-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="9719b-126">配置文件有多个嵌套层。</span><span class="sxs-lookup"><span data-stu-id="9719b-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="9719b-127">因此，在配置一个或多个设置时，常见的做法是克隆然后编辑多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="9719b-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="9719b-128">1.克隆默认的配置配置文件</span><span class="sxs-lookup"><span data-stu-id="9719b-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="9719b-129">配置配置文件是顶级配置文件。</span><span class="sxs-lookup"><span data-stu-id="9719b-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="9719b-130">因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。</span><span class="sxs-lookup"><span data-stu-id="9719b-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="9719b-131">在“层次结构”窗口中选择“MixedRealityToolkit”对象后，请在“检查器”窗口中将混合现实工具包“配置配置文件”更改为“DefaultHoloLens2ConfigurationProfile”：   </span><span class="sxs-lookup"><span data-stu-id="9719b-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="9719b-133">在仍选中了“MixedRealityToolkit”对象的情况下，在“检查器”窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口：  </span><span class="sxs-lookup"><span data-stu-id="9719b-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="9719b-135">在“克隆配置文件”窗口中，单击“克隆”按钮创建 **DefaultHololens2ConfigurationProfile** 的可编辑副本： </span><span class="sxs-lookup"><span data-stu-id="9719b-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="9719b-137">新建的配置配置文件现已分配为场景中的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="9719b-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="9719b-139">在 Unity 菜单中，选择“文件” > “保存”以保存场景。  </span><span class="sxs-lookup"><span data-stu-id="9719b-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="9719b-140">在学习整篇教程的过程中，请记得保存自己的工作。</span><span class="sxs-lookup"><span data-stu-id="9719b-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="9719b-141">2.启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="9719b-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="9719b-142">仍在“层次结构”窗口中选中了“MixedRealityToolkit”对象的情况下，在“检查器”窗口中选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：   </span><span class="sxs-lookup"><span data-stu-id="9719b-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="9719b-144">3.克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="9719b-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="9719b-145">在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口：  </span><span class="sxs-lookup"><span data-stu-id="9719b-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="9719b-147">在“克隆配置文件”窗口中，单击“克隆”按钮创建 **DefaultMixedRealitySpatialAwarenessSystemProfile** 的可编辑副本： </span><span class="sxs-lookup"><span data-stu-id="9719b-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="9719b-149">新建的空间感知系统配置文件现已自动分配到你的配置配置文件：</span><span class="sxs-lookup"><span data-stu-id="9719b-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="9719b-151">4.克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="9719b-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="9719b-152">在仍然选中了“空间感知”选项卡的情况下，展开“Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口：   </span><span class="sxs-lookup"><span data-stu-id="9719b-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="9719b-154">在“克隆配置文件”窗口中，单击“克隆”按钮创建 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** 的可编辑副本： </span><span class="sxs-lookup"><span data-stu-id="9719b-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="9719b-156">新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：</span><span class="sxs-lookup"><span data-stu-id="9719b-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="9719b-158">5.更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="9719b-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="9719b-159">在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下保持正常运行：   </span><span class="sxs-lookup"><span data-stu-id="9719b-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="9719b-161">尽管空间映射网格不可见，但它依然存在且可正常运行。</span><span class="sxs-lookup"><span data-stu-id="9719b-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="9719b-162">例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。</span><span class="sxs-lookup"><span data-stu-id="9719b-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="9719b-163">你已了解如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="9719b-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="9719b-164">可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="9719b-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="9719b-165">由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。</span><span class="sxs-lookup"><span data-stu-id="9719b-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="9719b-166">若要详细了解 MRTK 配置文件及其体系结构，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[混合现实工具包配置文件配置指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。</span><span class="sxs-lookup"><span data-stu-id="9719b-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="9719b-167">手动跟踪手势和可交互按钮</span><span class="sxs-lookup"><span data-stu-id="9719b-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="9719b-168">本部分介绍如何使用手动跟踪来按下某个按钮并触发事件，以便在按下该按钮时执行某项操作。</span><span class="sxs-lookup"><span data-stu-id="9719b-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="9719b-169">此特定示例演示如何在按下按钮时更改立方体的颜色，并在释放按钮时将其更改回原始颜色。</span><span class="sxs-lookup"><span data-stu-id="9719b-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="9719b-170">但是，可以按照相同的原则创建其他事件。</span><span class="sxs-lookup"><span data-stu-id="9719b-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="9719b-171">更改立方体颜色所要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="9719b-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="9719b-172">将一个可按按钮预制件添加到场景中</span><span class="sxs-lookup"><span data-stu-id="9719b-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="9719b-173">将立方体添加到场景中</span><span class="sxs-lookup"><span data-stu-id="9719b-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="9719b-174">配置 InteractableOnPressReceiver 事件类型</span><span class="sxs-lookup"><span data-stu-id="9719b-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="9719b-175">将立方体配置为接收 On Press 事件</span><span class="sxs-lookup"><span data-stu-id="9719b-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="9719b-176">定义 On Press 事件触发的操作</span><span class="sxs-lookup"><span data-stu-id="9719b-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="9719b-177">将立方体配置为接收 On Release 事件</span><span class="sxs-lookup"><span data-stu-id="9719b-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="9719b-178">定义 On Release 事件触发的操作</span><span class="sxs-lookup"><span data-stu-id="9719b-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="9719b-179">使用编辑器中的模拟功能测试按钮</span><span class="sxs-lookup"><span data-stu-id="9719b-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="9719b-180">1.将一个可按按钮预制件添加到场景中</span><span class="sxs-lookup"><span data-stu-id="9719b-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="9719b-181"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">预制件</a>是作为 Unity 资产存储的预配置 GameObject，可在整个项目中重复使用。</span><span class="sxs-lookup"><span data-stu-id="9719b-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="9719b-182">在“项目”窗口中，搜索 **PressableButtonHoloLens2** 找到用于本示例的预制件： </span><span class="sxs-lookup"><span data-stu-id="9719b-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="9719b-184">在“搜索”结果中，选择“PressableButtonHoloLens2”预制件并将其**拖到**“层次结构”窗口中，以将其添加到场景中：   </span><span class="sxs-lookup"><span data-stu-id="9719b-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="9719b-186">若要按下图所示显示场景，请在 "层次结构" 窗口中双击 "PressableButtonHoloLens2" 对象以使其成为焦点，然后使用位于场景窗口右上角的 <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">场景别出心裁</a>，以将查看角度调整为沿正向 Z 轴。</span><span class="sxs-lookup"><span data-stu-id="9719b-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="9719b-187">在仍选中了“PressableButtonHoloLens2”对象的情况下，在“检查器”窗口中执行以下操作：  </span><span class="sxs-lookup"><span data-stu-id="9719b-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="9719b-188">更改此对象的变换**位置**，将其定位在位于原点处的相机的前面，例如，定位到 x = 0，y = 0，z = 0.5</span><span class="sxs-lookup"><span data-stu-id="9719b-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="9719b-190">一般情况下，Unity 中的 1 个位置单位大致相当于现实生活中的 1 米。</span><span class="sxs-lookup"><span data-stu-id="9719b-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="9719b-191">但也存在例外情况，例如，当对象是缩放对象的子级时。</span><span class="sxs-lookup"><span data-stu-id="9719b-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="9719b-192">2.将立方体添加到场景中</span><span class="sxs-lookup"><span data-stu-id="9719b-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="9719b-193">在“层次结构”窗口中右键单击某个空白位置，然后选择“3D 对象” > “立方体”将一个立方体添加到场景中：  </span><span class="sxs-lookup"><span data-stu-id="9719b-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="9719b-195">在仍选中了“Cube”对象的情况下，在“检查器”窗口中执行以下操作：  </span><span class="sxs-lookup"><span data-stu-id="9719b-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="9719b-196">更改此对象的变换**位置**，将其定位在可按按钮附近，但不要与该按钮重叠，例如，定位到 x = 0，y = 0.04，z = 0.5</span><span class="sxs-lookup"><span data-stu-id="9719b-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="9719b-197">将其变换**标度**更改为适当的大小，例如 x = 0.02，y = 0.02，z = 0.02</span><span class="sxs-lookup"><span data-stu-id="9719b-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="9719b-199">3.配置 InteractableOnPressReceiver 事件类型</span><span class="sxs-lookup"><span data-stu-id="9719b-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="9719b-200">在“层次结构”窗口中选择“PressableButtonHoloLens2”对象，然后在“检查器”窗口的**三横线菜单**中，选择“折叠所有组件”以获取此对象上所有组件的概述：   </span><span class="sxs-lookup"><span data-stu-id="9719b-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="9719b-202">展开“可交互(脚本)”组件，然后找到并展开“事件” > “接收器”部分：   </span><span class="sxs-lookup"><span data-stu-id="9719b-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="9719b-204">单击“添加事件”按钮，创建事件接收器类型 **InteractableOnPressReceiver** 的新事件接收器： </span><span class="sxs-lookup"><span data-stu-id="9719b-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="9719b-206">当跟踪手按下按钮时，名为 InteractableOnPressReceiver 的事件接收器类型将允许该按钮响应 pressed 事件。</span><span class="sxs-lookup"><span data-stu-id="9719b-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="9719b-207">对于新建的事件接收器，请将“交互筛选器”更改为“近距和远距”：  </span><span class="sxs-lookup"><span data-stu-id="9719b-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="9719b-209">4.将立方体配置为接收 On Press 事件</span><span class="sxs-lookup"><span data-stu-id="9719b-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="9719b-210">在“层次结构”窗口中，单击“立方体”并将其**拖放**到“On Press ()”事件的“事件属性”对象字段中，以将 Cube 分配为 On Press () 事件的接收器：   </span><span class="sxs-lookup"><span data-stu-id="9719b-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="9719b-212">5.定义 On Press 事件触发的操作</span><span class="sxs-lookup"><span data-stu-id="9719b-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="9719b-213">单击操作下拉列表（当前分配的值为“无函数”），然后选择“MeshRenderer” > “Material 材料”，以设置在触发 On Press () 事件时要更改的立方体材料属性：   </span><span class="sxs-lookup"><span data-stu-id="9719b-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="9719b-215">单击材料字段（当前填充了“无(材料)”）旁边的小**圆圈**图标，打开“选择材料”窗口： </span><span class="sxs-lookup"><span data-stu-id="9719b-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="9719b-217">在“选择材料”窗口中，**搜索** **MRTK_Standard** 并选择合适的材料（例如 **MRTK_Standard_Cyan**），以便在按下按钮时立方体的颜色更改为青色：</span><span class="sxs-lookup"><span data-stu-id="9719b-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="9719b-219">6.将立方体配置为接收 On Release 事件</span><span class="sxs-lookup"><span data-stu-id="9719b-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="9719b-220">针对 On Release 事件**重复**步骤 4，将 **Cube** 分配为 **On Release ()** 事件的接收器。</span><span class="sxs-lookup"><span data-stu-id="9719b-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="9719b-221">7.定义 On Release 事件触发的操作</span><span class="sxs-lookup"><span data-stu-id="9719b-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="9719b-222">针对 On Release 事件**重复**步骤 5，但请选择“MRTK_Standard_LightGray”材料，以便在释放按钮时立方体的颜色恢复为其原始浅灰色： </span><span class="sxs-lookup"><span data-stu-id="9719b-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="9719b-224">8.使用编辑器中的模拟功能测试按钮</span><span class="sxs-lookup"><span data-stu-id="9719b-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="9719b-225">按“播放”按钮进入“游戏”模式，使用编辑器中的输入模拟功能测试新配置的按钮。 </span><span class="sxs-lookup"><span data-stu-id="9719b-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="9719b-226">未按下按钮（空格键 + 向后滚动鼠标滚轮）：</span><span class="sxs-lookup"><span data-stu-id="9719b-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="9719b-228">已按下按钮（空格键 + 向前滚动鼠标滚轮）：</span><span class="sxs-lookup"><span data-stu-id="9719b-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="9719b-230">若要了解如何使用编辑器中的输入模拟功能，可以参考 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用编辑器中的手写输入模拟来测试场景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。</span><span class="sxs-lookup"><span data-stu-id="9719b-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="9719b-231">使用 MRTK 的网格对象集合创建按钮面板</span><span class="sxs-lookup"><span data-stu-id="9719b-231">Creating a panel of buttons using MRTK's Grid Object Collection</span></span>

<span data-ttu-id="9719b-232">本部分介绍如何使用 MRTK 的网格对象集合工具自动对齐多个按钮，使用户界面保持整洁。</span><span class="sxs-lookup"><span data-stu-id="9719b-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK's Grid Object Collection tool.</span></span>

<span data-ttu-id="9719b-233">此特定示例将演示如何创建一个面板，其中包含五个水平对齐的按钮。</span><span class="sxs-lookup"><span data-stu-id="9719b-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="9719b-234">但是，可以按照相同的原则创建其他布局。</span><span class="sxs-lookup"><span data-stu-id="9719b-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="9719b-235">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="9719b-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="9719b-236">将按钮对象设为父对象的父级</span><span class="sxs-lookup"><span data-stu-id="9719b-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="9719b-237">添加并配置“网格对象集合(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="9719b-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="9719b-238">使用编辑器中的模拟功能测试按钮</span><span class="sxs-lookup"><span data-stu-id="9719b-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="9719b-239">1.将按钮对象设为父对象的父级</span><span class="sxs-lookup"><span data-stu-id="9719b-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="9719b-240">在“层次结构”窗口中右键单击某个空白位置，然后选择“创建空对象”： </span><span class="sxs-lookup"><span data-stu-id="9719b-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="9719b-242">右键单击新建的对象，然后选择“重命名”并为其指定一个适当的名称，例如 **ButtonCollection**： </span><span class="sxs-lookup"><span data-stu-id="9719b-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="9719b-244">选择“PressableButtonHoloLens2”对象，将其**拖放**到“ButtonCollection”对象的顶部，使其成为 ButtonCollection 对象的子级：  </span><span class="sxs-lookup"><span data-stu-id="9719b-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="9719b-246">右键单击“PressableButtonHoloLens2”对象，然后选择“复制”以创建其副本：  </span><span class="sxs-lookup"><span data-stu-id="9719b-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="9719b-248">**重复**此步骤四次，直到总共有五个 PressableButtonHoloLens2 对象。</span><span class="sxs-lookup"><span data-stu-id="9719b-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="9719b-249">2.添加并配置“网格对象集合(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="9719b-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="9719b-250">在“层次结构”窗口中选择了 ButtonCollection 对象的情况下，在“检查器”窗口中单击“添加组件”按钮，然后搜索并选择“网格对象集合”，将“网格对象集合(脚本)”组件添加到 ButtonCollection 对象中：  </span><span class="sxs-lookup"><span data-stu-id="9719b-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="9719b-252">按如下所述配置“网格对象集合(脚本)”：</span><span class="sxs-lookup"><span data-stu-id="9719b-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="9719b-253">将“行数”更改为 1，使所有按钮在一行中对齐 </span><span class="sxs-lookup"><span data-stu-id="9719b-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="9719b-254">将“单元格宽度”更改为 0.05，以隔开行中的按钮 </span><span class="sxs-lookup"><span data-stu-id="9719b-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="9719b-255">然后单击“更新集合”按钮以应用新配置： </span><span class="sxs-lookup"><span data-stu-id="9719b-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="9719b-257">刚刚应用的配置更改，就是实现在一行中放置所有按钮这一目标最起码需要做出的更改。</span><span class="sxs-lookup"><span data-stu-id="9719b-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="9719b-258">但是，在将来的项目中，根据父对象和子对象的方向等因素，你可能需要调整其他设置，例如方向类型。</span><span class="sxs-lookup"><span data-stu-id="9719b-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="9719b-259">若要详细了解 MRTK 的网格对象集合，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[对象集合脚本](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)指南。</span><span class="sxs-lookup"><span data-stu-id="9719b-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="9719b-260">仍在“层次结构”窗口中选中了 ButtonCollection 对象的情况下，在“检查器”窗口中更改 ButtonCollection 对象的变换**位置**，以将其子按钮对象定位在位于原点处的相机的前面，例如，定位到 x = 0，y = 0，z = 0.5：</span><span class="sxs-lookup"><span data-stu-id="9719b-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="9719b-262">在前面的[手动跟踪手势和可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)部分中首次将 PressableButtonHoloLens2 预制件添加到场景时，已将其定位在相机的前面。</span><span class="sxs-lookup"><span data-stu-id="9719b-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="9719b-263">但是，由于网格对象集合会控制其直属子对象的位置，因此，根据网格对象集合与父级之间的默认距离为 0 这一原则，PressableButtonHoloLens2 子对象的 Z 位置已重置为 0。</span><span class="sxs-lookup"><span data-stu-id="9719b-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="9719b-264">正因如此，同时为了在父级/子级之间保持组织有序的位置关系，我们已将父 ButtonCollection 对象的位置前移，而不是通过配置与父级之间的距离值将 PressableButtonHoloLens2 子对象前移。</span><span class="sxs-lookup"><span data-stu-id="9719b-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="9719b-265">3.使用编辑器中的模拟功能测试按钮</span><span class="sxs-lookup"><span data-stu-id="9719b-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="9719b-266">按下“播放”按钮进入“游戏”模式，使用编辑器中的输入模拟功能在新建的按钮面板中测试每个按钮：</span><span class="sxs-lookup"><span data-stu-id="9719b-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="9719b-268">目前，在按下五个按钮中的任何一个时，立方体颜色将变为青色。</span><span class="sxs-lookup"><span data-stu-id="9719b-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="9719b-269">为使体验更有趣，可以运用刚刚学到的知识配置每个按钮，以将立方体更改为不同的颜色。</span><span class="sxs-lookup"><span data-stu-id="9719b-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="9719b-270">将文本添加到场景中</span><span class="sxs-lookup"><span data-stu-id="9719b-270">Adding text into your scene</span></span>

<span data-ttu-id="9719b-271">本部分介绍如何使用 Unity 的 TextMesh Pro 将文本添加到混合现实体验，这些文本是在上一篇教程的[导入 TextMesh Pro 基本资源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)部分中准备的。</span><span class="sxs-lookup"><span data-stu-id="9719b-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="9719b-272">在此特定示例中，你将在上一部分创建的按钮集合下面添加一个简单的标签。</span><span class="sxs-lookup"><span data-stu-id="9719b-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="9719b-273">右键单击“ButtonCollection”对象，然后选择“3D 对象” > “文本 - TextMeshPro”，以创建一个 TextMeshPro 对象作为 ButtonCollection 对象的子级：  </span><span class="sxs-lookup"><span data-stu-id="9719b-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="9719b-275">在仍选中了名为 Text (TMP) 的新建 TextMeshPro 对象的情况下，在“检查器”窗口中更改其位置和大小，以将标签整齐放置在按钮集合下面，例如：</span><span class="sxs-lookup"><span data-stu-id="9719b-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="9719b-276">将矩形变换的“位置 Y”更改为 -0.0425 </span><span class="sxs-lookup"><span data-stu-id="9719b-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="9719b-277">将矩形变换的“宽度”更改为 0.24 </span><span class="sxs-lookup"><span data-stu-id="9719b-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="9719b-278">将矩形变换的“高度”更改为 0.024 </span><span class="sxs-lookup"><span data-stu-id="9719b-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="9719b-279">然后更新文本以反映标签的用途，并选择字体属性，使文本可以放入标签，例如：</span><span class="sxs-lookup"><span data-stu-id="9719b-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="9719b-280">将 Text Mesh Pro (Script) 的“文本”更改为“按钮集合” </span><span class="sxs-lookup"><span data-stu-id="9719b-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="9719b-281">将 Text Mesh Pro (Script) 的“字体样式”更改为“粗体” </span><span class="sxs-lookup"><span data-stu-id="9719b-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="9719b-282">将 Text Mesh Pro (Script) 的“字体大小”更改为 0.2 </span><span class="sxs-lookup"><span data-stu-id="9719b-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="9719b-283">将 Text Mesh Pro (Script) 的“对齐方式”更改为“居中” </span><span class="sxs-lookup"><span data-stu-id="9719b-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="9719b-285">祝贺</span><span class="sxs-lookup"><span data-stu-id="9719b-285">Congratulations</span></span>

<span data-ttu-id="9719b-286">本教程已介绍如何克隆、自定义和配置 MRTK 配置文件设置。</span><span class="sxs-lookup"><span data-stu-id="9719b-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="9719b-287">此外，还介绍了如何在 HoloLens 2 中使用跟踪手来与触发事件的按钮交互。</span><span class="sxs-lookup"><span data-stu-id="9719b-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="9719b-288">最后，介绍了如何使用 MRTK 的“网格对象集合”组件和 Unity 的 Text Mesh Pro 创建一个简单的 UI。</span><span class="sxs-lookup"><span data-stu-id="9719b-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="9719b-289">下一教程：4.放置动态内容并使用求解器</span><span class="sxs-lookup"><span data-stu-id="9719b-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
