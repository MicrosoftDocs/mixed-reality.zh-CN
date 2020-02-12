---
title: 入门教程-3。 创建用户界面并配置混合现实工具包
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 067832a130f130ffbaa8d455007b8e77e1b13671
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130474"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="e239b-105">3. 创建用户界面并配置混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="e239b-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="e239b-106">在上一教程中，你已了解到混合现实工具包（MRTK）通过启动适用于 HoloLens 2 的第一个应用程序而必须提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="e239b-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="e239b-107">在本教程中，您将学习如何创建和组织按钮以及 UI 文本面板，并使用默认交互（触摸）与每个按钮进行交互。</span><span class="sxs-lookup"><span data-stu-id="e239b-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="e239b-108">此外，本课还会探讨如何添加简单的操作和效果，例如更改对象的大小、声音和颜色。</span><span class="sxs-lookup"><span data-stu-id="e239b-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="e239b-109">此模块将介绍有关修改 MRTK 配置文件的基本概念，从关闭[空间映射](spatial-mapping.md)网格可视化效果开始。</span><span class="sxs-lookup"><span data-stu-id="e239b-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="e239b-110">目标</span><span class="sxs-lookup"><span data-stu-id="e239b-110">Objectives</span></span>

* <span data-ttu-id="e239b-111">自定义和配置混合现实工具包配置文件</span><span class="sxs-lookup"><span data-stu-id="e239b-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="e239b-112">使用 UI 元素和按钮与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="e239b-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="e239b-113">基本的手动跟踪输入和交互</span><span class="sxs-lookup"><span data-stu-id="e239b-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="e239b-114">如何配置混合现实工具包配置文件（更改空间感知显示选项）</span><span class="sxs-lookup"><span data-stu-id="e239b-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="e239b-115">在本部分中，你将学习如何自定义和配置默认的 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="e239b-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="e239b-116">此特定示例将演示如何通过更改空间网格观察程序的设置来隐藏空间感知网格。</span><span class="sxs-lookup"><span data-stu-id="e239b-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="e239b-117">但是，你可以遵循这些相同的原则自定义 MRTK 配置文件中的任何设置或值。</span><span class="sxs-lookup"><span data-stu-id="e239b-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="e239b-118">隐藏空间感知网格需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="e239b-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="e239b-119">克隆默认配置文件</span><span class="sxs-lookup"><span data-stu-id="e239b-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="e239b-120">启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="e239b-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="e239b-121">克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="e239b-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="e239b-122">克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="e239b-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="e239b-123">更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="e239b-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="e239b-124">默认情况下，MRTK 配置文件不可编辑。</span><span class="sxs-lookup"><span data-stu-id="e239b-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="e239b-125">这些是默认的配置文件模板，你必须先进行克隆，然后才能编辑它们。</span><span class="sxs-lookup"><span data-stu-id="e239b-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="e239b-126">配置文件有多个嵌套层。</span><span class="sxs-lookup"><span data-stu-id="e239b-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="e239b-127">因此，在配置一个或多个设置时，通常会克隆和编辑多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="e239b-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="e239b-128">1. 克隆默认配置文件</span><span class="sxs-lookup"><span data-stu-id="e239b-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="e239b-129">配置文件是顶级配置文件。</span><span class="sxs-lookup"><span data-stu-id="e239b-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="e239b-130">因此，为了能够编辑任何其他配置文件，你必须首先克隆配置文件。</span><span class="sxs-lookup"><span data-stu-id="e239b-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="e239b-131">在 "层次结构" 窗口中选择**MixedRealityToolkit**对象后，在 "检查器" 窗口中，单击 "**复制 & 自定义**" 按钮以打开 "克隆配置文件" 窗口：</span><span class="sxs-lookup"><span data-stu-id="e239b-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="e239b-133">在 "克隆配置文件" 窗口中，单击 "**克隆**" 按钮，创建**DefaultHololens2ConfigurationProfile**的可编辑副本：</span><span class="sxs-lookup"><span data-stu-id="e239b-133">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="e239b-135">新创建的配置文件现已分配为场景的配置文件：</span><span class="sxs-lookup"><span data-stu-id="e239b-135">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="e239b-137">在 Unity 菜单中，选择 "**文件**" > **保存**"以保存场景。</span><span class="sxs-lookup"><span data-stu-id="e239b-137">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="e239b-138">请记住在整个教程中保存您的工作。</span><span class="sxs-lookup"><span data-stu-id="e239b-138">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="e239b-139">2. 启用空间感知系统</span><span class="sxs-lookup"><span data-stu-id="e239b-139">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="e239b-140">仍在 "层次结构" 窗口中选择**MixedRealityToolkit**对象后，在 "检查器" 窗口中，选择 "**空间感知**" 选项卡，然后选中 "**启用空间感知系统**" 复选框：</span><span class="sxs-lookup"><span data-stu-id="e239b-140">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="e239b-142">3. 克隆默认的空间感知系统配置文件</span><span class="sxs-lookup"><span data-stu-id="e239b-142">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="e239b-143">在 "**空间感知**" 选项卡中，单击 "**克隆**" 按钮打开 "克隆配置文件" 窗口：</span><span class="sxs-lookup"><span data-stu-id="e239b-143">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="e239b-145">在 "克隆配置文件" 窗口中，单击 "**克隆**" 按钮，创建**DefaultMixedRealitySpatialAwarenessSystemProfile**的可编辑副本：</span><span class="sxs-lookup"><span data-stu-id="e239b-145">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="e239b-147">新创建的空间感知系统配置文件现在会自动分配给配置文件：</span><span class="sxs-lookup"><span data-stu-id="e239b-147">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="e239b-149">4. 克隆默认的空间感知网格观察程序配置文件</span><span class="sxs-lookup"><span data-stu-id="e239b-149">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="e239b-150">在仍然选择 "**空间感知**" 选项卡的情况下，展开 " **Windows Mixed Reality 空间网格观察**程序" 部分，然后单击 "**克隆**" 按钮以打开克隆配置文件窗口：</span><span class="sxs-lookup"><span data-stu-id="e239b-150">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="e239b-152">在 "克隆配置文件" 窗口中，单击 "**克隆**" 按钮，创建**DefaultMixedRealitySpatialAwarenessMeshObserverProfile**的可编辑副本：</span><span class="sxs-lookup"><span data-stu-id="e239b-152">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="e239b-154">此时，新建的空间感知网格观察程序配置文件会自动分配给空间感知系统配置文件：</span><span class="sxs-lookup"><span data-stu-id="e239b-154">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="e239b-156">5. 更改空间感知网格的可见性</span><span class="sxs-lookup"><span data-stu-id="e239b-156">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="e239b-157">在**空间网格观察程序设置**中，将**显示选项**更改为**封闭**，使空间映射网格在仍正常运行时不可见：</span><span class="sxs-lookup"><span data-stu-id="e239b-157">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="e239b-159">虽然空间映射网格不可见，但它仍然存在且正常工作。</span><span class="sxs-lookup"><span data-stu-id="e239b-159">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="e239b-160">例如，空间映射网格后面的任何全息影像（如物理壁后面的全息图）都将不可见。</span><span class="sxs-lookup"><span data-stu-id="e239b-160">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="e239b-161">你已了解如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="e239b-161">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="e239b-162">正如您所看到的，为了自定义 MRTK 设置，您首先需要创建默认配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="e239b-162">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="e239b-163">因为默认的配置文件是不可编辑的，所以，如果要还原为默认设置，你始终会将它们作为参考。</span><span class="sxs-lookup"><span data-stu-id="e239b-163">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="e239b-164">若要了解有关 MRTK 配置文件及其体系结构的详细信息，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[混合现实工具包配置文件配置指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。</span><span class="sxs-lookup"><span data-stu-id="e239b-164">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="e239b-165">手动跟踪手势和种不可交互按钮</span><span class="sxs-lookup"><span data-stu-id="e239b-165">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="e239b-166">在本部分中，你将学习如何使用手动跟踪按下按钮，并在按下按钮时触发事件，从而导致操作。</span><span class="sxs-lookup"><span data-stu-id="e239b-166">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="e239b-167">此特定示例将演示如何在按下按钮时更改多维数据集的颜色，并在释放按钮时将其更改回原始颜色。</span><span class="sxs-lookup"><span data-stu-id="e239b-167">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="e239b-168">但是，您可以遵循这些相同的原则来创建其他事件。</span><span class="sxs-lookup"><span data-stu-id="e239b-168">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="e239b-169">更改多维数据集颜色的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="e239b-169">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="e239b-170">将 pressable 按钮 prefab 添加到场景</span><span class="sxs-lookup"><span data-stu-id="e239b-170">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="e239b-171">将多维数据集添加到场景</span><span class="sxs-lookup"><span data-stu-id="e239b-171">Add a cube to the scene</span></span>
3. <span data-ttu-id="e239b-172">配置 InteractableOnPressReceiver 事件类型</span><span class="sxs-lookup"><span data-stu-id="e239b-172">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="e239b-173">配置多维数据集以接收按下事件</span><span class="sxs-lookup"><span data-stu-id="e239b-173">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="e239b-174">定义要在按下事件时触发的操作</span><span class="sxs-lookup"><span data-stu-id="e239b-174">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="e239b-175">配置多维数据集以接收 On Release 事件</span><span class="sxs-lookup"><span data-stu-id="e239b-175">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="e239b-176">定义要在发布事件时触发的操作</span><span class="sxs-lookup"><span data-stu-id="e239b-176">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="e239b-177">使用编辑器中的模拟测试按钮</span><span class="sxs-lookup"><span data-stu-id="e239b-177">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="e239b-178">1. 向场景添加 pressable 按钮 prefab</span><span class="sxs-lookup"><span data-stu-id="e239b-178">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="e239b-179"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a>是作为 Unity 资产存储的预配置 GameObject，可在整个项目中重复使用。</span><span class="sxs-lookup"><span data-stu-id="e239b-179">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="e239b-180">在 "**项目" 窗口**中，搜索**PressableButtonHoloLens2**以查找将用于此示例的 prefab：</span><span class="sxs-lookup"><span data-stu-id="e239b-180">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="e239b-182">在**搜索**结果中，选择**PressableButtonHoloLens2** prefab 并**将其拖**到 "**层次结构**" 窗口中，将其添加到场景：</span><span class="sxs-lookup"><span data-stu-id="e239b-182">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="e239b-184">若要按下图所示显示场景，请在 "层次结构" 窗口中双击 "PressableButtonHoloLens2" 对象以使其成为焦点，然后使用位于场景窗口右上角的<a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">场景别出心裁</a>，将查看角度调整为沿正向 Z 轴。</span><span class="sxs-lookup"><span data-stu-id="e239b-184">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="e239b-185">在 PressableButtonHoloLens2 对象仍处于选中状态的**检查器**窗口中：</span><span class="sxs-lookup"><span data-stu-id="e239b-185">With the PressableButtonHoloLens2 object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="e239b-186">更改其转换**位置**，使其位于相机前面（例如 x = 0、y = 0 和 z = 0.5）。</span><span class="sxs-lookup"><span data-stu-id="e239b-186">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="e239b-188">通常，Unity 中的1个位置单位大致相当于物理世界中的1米。</span><span class="sxs-lookup"><span data-stu-id="e239b-188">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="e239b-189">但存在一些例外情况，例如，当对象是缩放对象的子级时。</span><span class="sxs-lookup"><span data-stu-id="e239b-189">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="e239b-190">2. 将多维数据集添加到场景</span><span class="sxs-lookup"><span data-stu-id="e239b-190">2. Add a cube to the scene</span></span>

<span data-ttu-id="e239b-191">右键单击 "层次结构" 窗口中的空白点，然后选择 " **3D 对象** > **多维数据集**以将多维数据集添加到场景：</span><span class="sxs-lookup"><span data-stu-id="e239b-191">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="e239b-193">如果仍选中多维数据集对象，则在 "**检查器**" 窗口中：</span><span class="sxs-lookup"><span data-stu-id="e239b-193">With the Cube object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="e239b-194">更改其转换**位置**，使其位于 "pressable" 按钮附近，但不与它重叠，例如 x = 0、y = 0.04 和 z = 0。5</span><span class="sxs-lookup"><span data-stu-id="e239b-194">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="e239b-195">将其转换**比例**更改为合适的大小，例如 x = 0.02、y = 0.02 和 z = 0.02</span><span class="sxs-lookup"><span data-stu-id="e239b-195">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="e239b-197">3. 配置 InteractableOnPressReceiver 事件类型</span><span class="sxs-lookup"><span data-stu-id="e239b-197">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="e239b-198">在 "层次结构" 窗口中选择 "PressableButtonHoloLens2" 对象之后，在 "**检查器**" 窗口**汉堡菜单**中，选择 " **Collaps 所有组件**" 以获取此对象上的所有组件的概述：</span><span class="sxs-lookup"><span data-stu-id="e239b-198">With the PressableButtonHoloLens2 object selected in the Hierarchy window, in the **Inspector** window **hamburger menu**, select **Collaps All Components** to get an overview of all components on this object:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="e239b-200">展开**种不可交互（脚本）** 组件，然后找到并展开 "**事件** > **接收**方" 部分：</span><span class="sxs-lookup"><span data-stu-id="e239b-200">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="e239b-202">对于事件接收器类型**InteractableOnPressReceiver**，请将**交互筛选器**更改为 "**接近" 和 "远**"：</span><span class="sxs-lookup"><span data-stu-id="e239b-202">For the Event Receiver Type **InteractableOnPressReceiver**, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="e239b-204">名为 InteractableOnPressReceiver 的事件接收器类型允许按钮在按下按钮时响应按下的事件。</span><span class="sxs-lookup"><span data-stu-id="e239b-204">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="e239b-205">4. 配置多维数据集以接收按下事件</span><span class="sxs-lookup"><span data-stu-id="e239b-205">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="e239b-206">在 "层次结构" 窗口中，**单击并将** **多维数据集**拖动到 "**按下（）** 事件的**事件属性**对象" 字段中，以便将多维数据集分配为按下（）事件的接收方：</span><span class="sxs-lookup"><span data-stu-id="e239b-206">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="e239b-208">5. 定义要在按下事件时触发的操作</span><span class="sxs-lookup"><span data-stu-id="e239b-208">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="e239b-209">单击 "操作" 下拉列表，当前未分配 "**函数**"，然后选择 " **MeshRenderer** > **材料材料**，以设置在触发 On 按下（）事件时要更改的多维数据集的材料属性：</span><span class="sxs-lookup"><span data-stu-id="e239b-209">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="e239b-211">单击 "材料" 字段旁边的小**圆圈**图标（当前填充了 "**无（材料）"）** 以打开 "选择材料" 窗口：</span><span class="sxs-lookup"><span data-stu-id="e239b-211">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="e239b-213">在 "选择材料" 窗口中，**搜索**" **MRTK_Standard** " 并选择合适的材料，例如**MRTK_Standard_Cyan** ，以便在按下按钮时，多维数据集的颜色更改为 "青色"：</span><span class="sxs-lookup"><span data-stu-id="e239b-213">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="e239b-215">6. 配置多维数据集以接收 On Release 事件</span><span class="sxs-lookup"><span data-stu-id="e239b-215">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="e239b-216">**重复**"发布时" 事件的步骤4，用于将多维数据集分配为 On Release （）事件的接收方。</span><span class="sxs-lookup"><span data-stu-id="e239b-216">**Repeat** Step 4 for the On Release event to assign the Cube as a receiver of the On Release () event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="e239b-217">7. 定义要在发布事件时触发的操作</span><span class="sxs-lookup"><span data-stu-id="e239b-217">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="e239b-218">**重复**第5步：对于 "发布" 事件，但选择 " **MRTK_Standard_LightGray**材料，以便在按钮被释放时，将多维数据集的颜色恢复为其原始的浅灰色颜色：</span><span class="sxs-lookup"><span data-stu-id="e239b-218">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="e239b-220">8. 使用编辑器内模拟测试按钮</span><span class="sxs-lookup"><span data-stu-id="e239b-220">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="e239b-221">按 "**播放**" 按钮进入游戏模式，并使用编辑器内输入模拟来测试新配置的按钮。</span><span class="sxs-lookup"><span data-stu-id="e239b-221">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="e239b-222">未按下按钮（向后滚动鼠标滚轮）：</span><span class="sxs-lookup"><span data-stu-id="e239b-222">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="e239b-224">按下按钮（向前滚动滚轮）：</span><span class="sxs-lookup"><span data-stu-id="e239b-224">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="e239b-226">若要了解如何使用编辑器内输入模拟，可以参考[使用编辑器内手写输入模拟](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)在[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中测试场景指南。</span><span class="sxs-lookup"><span data-stu-id="e239b-226">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="e239b-227">使用 MRTK 的网格对象集合创建按钮面板</span><span class="sxs-lookup"><span data-stu-id="e239b-227">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="e239b-228">在本部分中，你将了解如何使用 MRTK 的网格对象集合工具自动将多个按钮对齐到巧妙的用户界面。</span><span class="sxs-lookup"><span data-stu-id="e239b-228">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s Grid Object Collection tool.</span></span>

<span data-ttu-id="e239b-229">此特定示例将演示如何创建一个面板，该面板具有水平对齐的五个按钮。</span><span class="sxs-lookup"><span data-stu-id="e239b-229">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="e239b-230">但是，您可以遵循这些相同的原则来创建其他布局。</span><span class="sxs-lookup"><span data-stu-id="e239b-230">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="e239b-231">为实现此目的需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="e239b-231">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="e239b-232">父对象的父对象的父对象</span><span class="sxs-lookup"><span data-stu-id="e239b-232">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="e239b-233">添加和配置网格对象集合（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="e239b-233">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="e239b-234">使用编辑器内模拟测试按钮</span><span class="sxs-lookup"><span data-stu-id="e239b-234">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="e239b-235">1. 将 button 对象父对象的父对象</span><span class="sxs-lookup"><span data-stu-id="e239b-235">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="e239b-236">右键单击 "层次结构" 窗口中的空白点，然后选择 "**创建空**项"：</span><span class="sxs-lookup"><span data-stu-id="e239b-236">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="e239b-238">右键单击新创建的对象，选择 "**重命名**"，并为其指定一个适当的名称，例如**ButtonCollection**：</span><span class="sxs-lookup"><span data-stu-id="e239b-238">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="e239b-240">选择**PressableButtonHoloLens2**对象并**将其拖**到**ButtonCollection**对象的顶部，使其成为 ButtonCollection 对象的子元素：</span><span class="sxs-lookup"><span data-stu-id="e239b-240">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="e239b-242">右键单击**PressableButtonHoloLens2**对象，然后选择 "**复制**" 以创建其副本：</span><span class="sxs-lookup"><span data-stu-id="e239b-242">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="e239b-244">**重复**此步骤四次，直到总共有5个 PressableButtonHoloLens2 对象。</span><span class="sxs-lookup"><span data-stu-id="e239b-244">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="e239b-245">2. 添加和配置网格对象集合（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="e239b-245">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="e239b-246">在 "层次结构" 窗口中选择 "ButtonCollection" 对象之后，在 "检查器" 窗口中，单击 "**添加组件**" 按钮，然后搜索并选择 "**网格对象集合**"，将网格对象集合（脚本）组件添加到 ButtonCollection 对象：</span><span class="sxs-lookup"><span data-stu-id="e239b-246">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="e239b-248">按如下所示配置网格对象集合（脚本）：</span><span class="sxs-lookup"><span data-stu-id="e239b-248">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="e239b-249">将**Num 行**更改为1，使所有按钮在一行上对齐</span><span class="sxs-lookup"><span data-stu-id="e239b-249">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="e239b-250">将**单元格宽度**改为0.05，使行中的按钮间距</span><span class="sxs-lookup"><span data-stu-id="e239b-250">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="e239b-251">然后单击 "**更新集合**" 按钮应用新配置：</span><span class="sxs-lookup"><span data-stu-id="e239b-251">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="e239b-253">刚才应用的配置更改表示实现将按钮置于单个行中的目标所需的最小更改。</span><span class="sxs-lookup"><span data-stu-id="e239b-253">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="e239b-254">但是，在将来的项目中，根据各种因素（例如，父对象和子对象的方向），您可能需要调整其他设置，例如，如方向类型。</span><span class="sxs-lookup"><span data-stu-id="e239b-254">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="e239b-255">若要详细了解 MRTK 的网格对象集合，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[对象集合脚本](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts)指南。</span><span class="sxs-lookup"><span data-stu-id="e239b-255">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="e239b-256">如果仍在 "层次结构" 窗口中选择 "ButtonCollection" 对象，则在 "检查器" 窗口中，更改 ButtonCollection 对象的转换**位置**，使其子按钮对象位于相机前面，例如 x = 0、y = 0 和 z = 0.5：</span><span class="sxs-lookup"><span data-stu-id="e239b-256">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="e239b-258">第一次将 PressableButtonHoloLens2 prefab 添加到上面的 "[手写跟踪手势" 和 "种不可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)" 部分时，会将其放在照相机的前方。</span><span class="sxs-lookup"><span data-stu-id="e239b-258">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="e239b-259">但是，因为网格对象集合控制其直接子对象的位置，所以根据网格对象集合与父值0之间的默认距离，PressableButtonHoloLens2 子对象的 Z 位置被重置为0。</span><span class="sxs-lookup"><span data-stu-id="e239b-259">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="e239b-260">这是为了使父/子位置关系保持井然有序，这是因为我们将父 ButtonCollection 对象的位置向前移动，而不是配置从父值到 PressableButtonHoloLens2 子对象的距离。</span><span class="sxs-lookup"><span data-stu-id="e239b-260">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="e239b-261">3. 使用编辑器内模拟测试按钮</span><span class="sxs-lookup"><span data-stu-id="e239b-261">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="e239b-262">按下 "播放" 按钮进入游戏模式，并使用编辑器内输入模拟在新创建的按钮面板中测试每个按钮：</span><span class="sxs-lookup"><span data-stu-id="e239b-262">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="e239b-264">目前，当您按下任何五个按钮时，多维数据集颜色将变为青色。</span><span class="sxs-lookup"><span data-stu-id="e239b-264">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="e239b-265">若要使体验更有趣，可使用刚刚了解的内容来配置每个按钮，将多维数据集更改为不同的颜色。</span><span class="sxs-lookup"><span data-stu-id="e239b-265">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="e239b-266">向场景中添加文本</span><span class="sxs-lookup"><span data-stu-id="e239b-266">Adding text into your scene</span></span>

<span data-ttu-id="e239b-267">在本部分中，你将学习如何使用 Unity 的 TextMesh Pro，并在上一教程的 "[导入 TextMesh Pro 基本资源](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)" 部分中准备好如何向混合现实体验添加文本。</span><span class="sxs-lookup"><span data-stu-id="e239b-267">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="e239b-268">在此特定示例中，你将在上一节中创建的按钮集合下添加一个简单标签。</span><span class="sxs-lookup"><span data-stu-id="e239b-268">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="e239b-269">右键单击 "ButtonCollection" 对象，然后选择 " **3D object** > **TextMeshPro** ，将 TextMeshPro 对象创建为 ButtonCollection 对象的子对象：</span><span class="sxs-lookup"><span data-stu-id="e239b-269">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="e239b-271">在新创建的 TextMeshPro 对象（仍处于选定状态）中，在 "检查器" 窗口中更改其位置和大小，以便将标签整齐放置在按钮集合下，例如：</span><span class="sxs-lookup"><span data-stu-id="e239b-271">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="e239b-272">将矩形转换位置**Y**改为-0.0425</span><span class="sxs-lookup"><span data-stu-id="e239b-272">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="e239b-273">将矩形转换**宽度**更改为0.24</span><span class="sxs-lookup"><span data-stu-id="e239b-273">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="e239b-274">将矩形转换**高度**更改为0.024</span><span class="sxs-lookup"><span data-stu-id="e239b-274">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="e239b-275">然后，更新文本以反映标签的内容，并选择字体属性，使文本适合标签，例如：</span><span class="sxs-lookup"><span data-stu-id="e239b-275">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="e239b-276">将文本网格 Pro （脚本）**文本**更改为按钮集合</span><span class="sxs-lookup"><span data-stu-id="e239b-276">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="e239b-277">将文本网格 Pro （脚本）**字体样式**更改为粗体</span><span class="sxs-lookup"><span data-stu-id="e239b-277">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="e239b-278">将文本网格 Pro （脚本）**字号**更改为0。2</span><span class="sxs-lookup"><span data-stu-id="e239b-278">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="e239b-279">将文本网格 Pro （脚本）**对齐方式**更改为居中和居中</span><span class="sxs-lookup"><span data-stu-id="e239b-279">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="e239b-281">祝贺你</span><span class="sxs-lookup"><span data-stu-id="e239b-281">Congratulations</span></span>

<span data-ttu-id="e239b-282">本教程介绍了如何克隆、自定义和配置 MRTK 配置文件设置。</span><span class="sxs-lookup"><span data-stu-id="e239b-282">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="e239b-283">还了解了如何与按钮交互，以便在 HoloLens 2 上使用跟踪的动手触发器事件。</span><span class="sxs-lookup"><span data-stu-id="e239b-283">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="e239b-284">最后，你已了解如何使用 MRTK 的网格对象集合组件和 Unity 文本网格 Pro 创建简单的 UI 接口。</span><span class="sxs-lookup"><span data-stu-id="e239b-284">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="e239b-285">下一教程： 4. 放置动态内容并使用 solvers</span><span class="sxs-lookup"><span data-stu-id="e239b-285">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
