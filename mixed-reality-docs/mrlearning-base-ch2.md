---
title: MR 学习基础模块 - 用户界面、手跟踪和混合现实工具包配置
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730944"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a><span data-ttu-id="897f7-104">MR 学习基础模块 - 用户界面、手跟踪和混合现实工具包配置</span><span class="sxs-lookup"><span data-stu-id="897f7-104">MR Learning Base Module - User Interface, Hand Tracking, and Mixed Reality Toolkit Configuration</span></span>

<span data-ttu-id="897f7-105">在上一课中，你已通过启动适用于 HoloLens 2 的第一个应用程序，了解了 MRTK 提供的某些功能。</span><span class="sxs-lookup"><span data-stu-id="897f7-105">In the previous lesson, you learned some of the capabilities the MRTK has to offer, by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="897f7-106">本课将会介绍如何创建按钮并在 UI 文本面板中对其进行组织，然后使用默认的交互（触摸）方式来与每个按钮交互。</span><span class="sxs-lookup"><span data-stu-id="897f7-106">In this next lesson you will learn how to create and organize buttons along with UI text panels and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="897f7-107">此外，本课还会探讨如何添加简单的操作和效果，例如更改对象的大小、声音和颜色。</span><span class="sxs-lookup"><span data-stu-id="897f7-107">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="897f7-108">本模块将会介绍有关如何修改 MRTK 配置文件的基本概念，并从禁用空间网格的可视化开始介绍。</span><span class="sxs-lookup"><span data-stu-id="897f7-108">This module will introduce basic concepts on how to modify MRTK profiles, starting with turning off the visualization of the spatial mesh.</span></span> 

## <a name="objectives"></a><span data-ttu-id="897f7-109">目标</span><span class="sxs-lookup"><span data-stu-id="897f7-109">Objectives</span></span>

* <span data-ttu-id="897f7-110">自定义和配置混合现实工具包配置文件</span><span class="sxs-lookup"><span data-stu-id="897f7-110">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="897f7-111">使用 UI 元素和按钮来与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="897f7-111">Interacting with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="897f7-112">基本的手动跟踪输入和交互</span><span class="sxs-lookup"><span data-stu-id="897f7-112">Basic hand-tracking input and interactions</span></span>

## <a name="instructions"></a><span data-ttu-id="897f7-113">说明</span><span class="sxs-lookup"><span data-stu-id="897f7-113">Instructions</span></span>

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="897f7-114">如何配置混合现实工具包配置文件（更改空间感知显示选项）</span><span class="sxs-lookup"><span data-stu-id="897f7-114">How to Configure the Mixed-Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<span data-ttu-id="897f7-115">本部分将介绍如何通过调整空间感知网格的显示选项，来自定义和配置默认的混合现实工具包配置文件。</span><span class="sxs-lookup"><span data-stu-id="897f7-115">In this section you will learn how to customize and configure the default Mixed Reality Toolkit profiles by adjusting the display option of the spatial awareness mesh.</span></span> <span data-ttu-id="897f7-116">调整 MRTK 配置文件中的任何设置或值时，也可以遵循这些原则。</span><span class="sxs-lookup"><span data-stu-id="897f7-116">You may follow these same principles for adjusting any settings or values in the MRTK profiles.</span></span>

1. <span data-ttu-id="897f7-117">从“BaseScene”层次结构中选择“混合现实工具包(MRTK)”。</span><span class="sxs-lookup"><span data-stu-id="897f7-117">Select Mixed-Reality Toolkit (MRTK) from the “BaseScene” hierarchy.</span></span> <span data-ttu-id="897f7-118">在检查器面板中，找到“混合现实工具包脚本”并选择“活动的配置文件”，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="897f7-118">In the inspector panel, look for the “Mixed Reality Toolkit Script” and select the “active profile” as shown in the figure below.</span></span> <span data-ttu-id="897f7-119">双击该配置文件将其打开。</span><span class="sxs-lookup"><span data-stu-id="897f7-119">Double click to open it.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

><span data-ttu-id="897f7-121">注意：默认情况下，MRTK 配置文件不可编辑。</span><span class="sxs-lookup"><span data-stu-id="897f7-121">Note: By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="897f7-122">这是一些可以从中进行复制和自定义的默认配置文件模板。</span><span class="sxs-lookup"><span data-stu-id="897f7-122">These are default profile templates from which you can copy and customize.</span></span> <span data-ttu-id="897f7-123">有多个自定义和配置文件层，因此，标准的做法是，在配置一个或多个设置时复制并自定义多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="897f7-123">There are several layers of customization and profiles, so it is standard practice to copy and customize several profiles when configuring one or more settings.</span></span>
>
><span data-ttu-id="897f7-124">若要详细了解 MRTK 配置文件及其体系结构，请访问 [MRTK 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)。</span><span class="sxs-lookup"><span data-stu-id="897f7-124">To discover more about MRTK profiles and their architecture, please visit the [MRTK documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).</span></span>

2. <span data-ttu-id="897f7-125">创建默认配置文件的副本以对其进行自定义。</span><span class="sxs-lookup"><span data-stu-id="897f7-125">Create a copy of the default profile to customize it.</span></span> <span data-ttu-id="897f7-126">若要复制默认的配置文件，请单击“复制和自定义”按钮（参考插图）。</span><span class="sxs-lookup"><span data-stu-id="897f7-126">To copy a default profile, click the “Copy & Customize” button (see image).</span></span> <span data-ttu-id="897f7-127">随即会创建 MRTK 配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="897f7-127">This creates a copy of the MRTK profile.</span></span> <span data-ttu-id="897f7-128">现在，可以使用自己的 MRTK 配置文件副本，自定义此配置文件中的任何设置。</span><span class="sxs-lookup"><span data-stu-id="897f7-128">With your own copy of the MRTK profile, you now have the ability customize any settings in this profile.</span></span> <span data-ttu-id="897f7-129">对于嵌套在此配置文件下的任何其他配置文件，也需要根据后续步骤中所述，重复复制/自定义步骤。</span><span class="sxs-lookup"><span data-stu-id="897f7-129">You will also need to repeat the copy/customize step for any additional profiles nested under this profile, as described in the subsequent steps.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. <span data-ttu-id="897f7-131">禁用空间感知网格的可见性。</span><span class="sxs-lookup"><span data-stu-id="897f7-131">Disable the visibility of the spatial awareness mesh.</span></span> <span data-ttu-id="897f7-132">为此，请找到“空间感知系统设置”，如图所示。</span><span class="sxs-lookup"><span data-stu-id="897f7-132">To do this, find “Spatial Awareness System Settings” as shown in the image.</span></span> <span data-ttu-id="897f7-133">单击“空间感知系统配置文件”右侧的“克隆”按钮，将默认配置文件替换为可自定义的副本。</span><span class="sxs-lookup"><span data-stu-id="897f7-133">Click the "clone" button to the right of the the “Spatial Awareness System Profile” to replace the default profile with a customizable copy.</span></span> <span data-ttu-id="897f7-134">如果出现了弹出窗口，请按“克隆”按钮，如下面的第二张插图中所示。</span><span class="sxs-lookup"><span data-stu-id="897f7-134">If a pop-up window appears, press the "Clone" button, as shown in the second image below.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. <span data-ttu-id="897f7-137">创建默认混合现实空间网格观察者的自定义副本。</span><span class="sxs-lookup"><span data-stu-id="897f7-137">Create a custom copy of the Default Mixed Reality Spatial Mesh Observer.</span></span> <span data-ttu-id="897f7-138">单击“Windows 混合现实空间网格观察者”旁边的向下箭头以查看其他选项。</span><span class="sxs-lookup"><span data-stu-id="897f7-138">Click the down arrow next to “Windows Mixed Reality Spatial Mesh Observer” to see additional options.</span></span> <span data-ttu-id="897f7-139">在这些选项中，可以看到“默认混合现实空间网格观察者”已灰显（不可编辑）。</span><span class="sxs-lookup"><span data-stu-id="897f7-139">In these options, you will see the “Default Mixed Reality Spatial Mesh Observer” which appears greyed (not editable).</span></span> <span data-ttu-id="897f7-140">必须将此默认配置文件替换为可自定义的副本，以便能够对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="897f7-140">You must replace this default profile with a customizable copy so you can edit it.</span></span> <span data-ttu-id="897f7-141">单击右侧的按钮（标有绿色箭头）以克隆副本。</span><span class="sxs-lookup"><span data-stu-id="897f7-141">Click the button to the right (marked by green arrow) to clone a copy.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. <span data-ttu-id="897f7-143">接下来，调整带有“遮挡”字样的显示选项的设置。</span><span class="sxs-lookup"><span data-stu-id="897f7-143">Next, you will adjust the settings for the display option to say “occlusion.”</span></span> <span data-ttu-id="897f7-144">此设置会使空间网格不可见，但仍会隐藏空间网格后面的游戏对象（称为遮挡）。</span><span class="sxs-lookup"><span data-stu-id="897f7-144">This makes the spatial mesh invisible, but still hide game objects behind the spatial mesh (this is known as occlusion.)</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

><span data-ttu-id="897f7-146">注意：尽管空间映射网格不可见，但它依然存在，且可与其交互。</span><span class="sxs-lookup"><span data-stu-id="897f7-146">Note: While the spatial mapping mesh is not visible, it is still present and you can interact with it.</span></span> <span data-ttu-id="897f7-147">由于使用了遮挡设置，空间映射网格后面的所有全息影像（例如可见墙壁后面的全息影像）将不可见。</span><span class="sxs-lookup"><span data-stu-id="897f7-147">Any holograms behind the spatial mapping mesh (e.g. A hologram behind your visible wall) will not be visible because of the occlusion setting.</span></span>

<span data-ttu-id="897f7-148">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="897f7-148">Congratulations!</span></span> <span data-ttu-id="897f7-149">你已了解如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="897f7-149">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="897f7-150">你知道，若要修改 MRTK 设置，需要创建默认配置文件的副本，以便能够对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="897f7-150">As you can see, in order to modify MRTK settings you need to create copies of the default profiles so that you can edit them.</span></span> <span data-ttu-id="897f7-151">想要使用新的设置创建配置文件，或重新引用默认的配置文件时，你始终有留底的默认配置文件（不可编辑）。</span><span class="sxs-lookup"><span data-stu-id="897f7-151">You will always have the default profiles (which are not editable) to go back to if you wanted to create a profile with new settings, or refer back to the default profiles.</span></span> <span data-ttu-id="897f7-152">可以调整大量的设置。</span><span class="sxs-lookup"><span data-stu-id="897f7-152">There are numerous settings that you can adjust.</span></span> <span data-ttu-id="897f7-153">有关 MRTK 配置文件设置的完整参考，请参阅 MRTK 文档： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html</span><span class="sxs-lookup"><span data-stu-id="897f7-153">For full reference to MRTK profile settings, refer to the MRTK documentation here: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html</span></span>

### <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="897f7-154">手动跟踪手势和可交互按钮</span><span class="sxs-lookup"><span data-stu-id="897f7-154">Hand Tracking Gestures and Interactable buttons</span></span>
<span data-ttu-id="897f7-155">本部分介绍如何使用手动跟踪来按下某个可交互的按钮。</span><span class="sxs-lookup"><span data-stu-id="897f7-155">In this section, you will learn how to use hand tracking to press an interactable button.</span></span>

1. <span data-ttu-id="897f7-156">从“项目”文件夹中选择“资产”。</span><span class="sxs-lookup"><span data-stu-id="897f7-156">Select “Assets” from the projects folder.</span></span>

2. <span data-ttu-id="897f7-157">在搜索栏中键入“pressablebutton”。</span><span class="sxs-lookup"><span data-stu-id="897f7-157">Type in the search bar, “pressablebutton.”</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. <span data-ttu-id="897f7-159">将名为“PressableButton”的预制件（以蓝框表示）拖入层次结构。</span><span class="sxs-lookup"><span data-stu-id="897f7-159">Drag the prefab (represented by a blue box) named "PressableButton" into your hierarchy.</span></span> 

   > <span data-ttu-id="897f7-160">注意：如果出现了有关“导入 TMP Essentials”的消息，现在请导入 TMP Essentials。</span><span class="sxs-lookup"><span data-stu-id="897f7-160">Note: If you get a message about “importing TMP Essentials” please import it at this time.</span></span> <span data-ttu-id="897f7-161">如果 TMP Essentials 尚未包含在项目中，则导入 TMP Essentials 后你可能需要重复此步骤，否则按钮文本可能不显示。</span><span class="sxs-lookup"><span data-stu-id="897f7-161">If TMP Essentials was not already part of your project, you may need to repeat this step after importing TMP Essentials, otherwise button text may not appear.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. <span data-ttu-id="897f7-163">双击“PressableButton”游戏对象（它现在应在 BaseScene 层次结构中）以在场景中查看它，如图所示（显示的按钮图形可能与下图不同）。</span><span class="sxs-lookup"><span data-stu-id="897f7-163">Double click the “PressableButton” game object (which should now be in your BaseScene hierarchy) to view it in your scene, as shown in the image below (your button graphics may appear different than the image below).</span></span> 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. <span data-ttu-id="897f7-165">在检查器面板中单击“添加事件”，以在按钮中添加一个事件，按下该按钮时会响应该事件。</span><span class="sxs-lookup"><span data-stu-id="897f7-165">In the inspector panel, click “Add Event” to give the button an event to respond to when pushed.</span></span> <span data-ttu-id="897f7-166">在显示的选项中，选择下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="897f7-166">In the option that appears, select the drop-down menu.</span></span> <span data-ttu-id="897f7-167">选择“InteractableOnPressReciever”。</span><span class="sxs-lookup"><span data-stu-id="897f7-167">Select “InteractableOnPressReciever.”</span></span> <span data-ttu-id="897f7-168">这样，在跟踪手按下该按钮时，该按钮会响应按键事件。</span><span class="sxs-lookup"><span data-stu-id="897f7-168">This allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. <span data-ttu-id="897f7-170">将立方体添加到场景。</span><span class="sxs-lookup"><span data-stu-id="897f7-170">Add a cube to the scene.</span></span> <span data-ttu-id="897f7-171">右键单击层次结构区域，选择 3D 对象，然后单击“立方体”。</span><span class="sxs-lookup"><span data-stu-id="897f7-171">Right click on the hierarchy area, select 3D object, then click on “cube.”</span></span> <span data-ttu-id="897f7-172">现在，你的显示画面中应会包含一个立方体。</span><span class="sxs-lookup"><span data-stu-id="897f7-172">Now, a cube should be in your display.</span></span> <span data-ttu-id="897f7-173">该立方体看上去很大，因此，请（在仍已在层次结构区域中选择“立方体”的情况下）调整其坐标，以减小其大小。</span><span class="sxs-lookup"><span data-stu-id="897f7-173">It will appear very large, so adjust the coordinates (while “cube” is still selected in the hierarchy area) to decrease the size.</span></span> <span data-ttu-id="897f7-174">将坐标值设置为 x = 0.1，y = 0.1，z = 0.1。</span><span class="sxs-lookup"><span data-stu-id="897f7-174">Set the scale values to x = 0.1, y = 0.1 and z = 0.1.</span></span> <span data-ttu-id="897f7-175">请务必在场景中将该立方体定位在靠近可按按钮的位置，但不要与该按钮重叠。</span><span class="sxs-lookup"><span data-stu-id="897f7-175">Be sure to position the cube in your scene to place it near the pressable button, but not overlapping with the button.</span></span> <span data-ttu-id="897f7-176">在下图中，立方体的位置为 x = 0，y = 0.2，z = 1。</span><span class="sxs-lookup"><span data-stu-id="897f7-176">In the image below, the cube’s position is x = 0, y = 0.2, and z = 1.</span></span> 

   > <span data-ttu-id="897f7-177">注意：一般情况下，Unity 中的 1 个单位大致相当于现实生活中的 1 米。</span><span class="sxs-lookup"><span data-stu-id="897f7-177">Note: In general, 1 unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="897f7-178">但也存在例外情况，例如，当对象是缩放对象的子级时。</span><span class="sxs-lookup"><span data-stu-id="897f7-178">There are exceptions to this, for example when objects are children of scaled objects.</span></span>
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. <span data-ttu-id="897f7-181">此步骤将立方体设置为在按下按钮时改变颜色。</span><span class="sxs-lookup"><span data-stu-id="897f7-181">In this step you will set up the cube to change color when your button is pressed.</span></span> <span data-ttu-id="897f7-182">在“BaseScene”菜单中选择“PressableButton”。</span><span class="sxs-lookup"><span data-stu-id="897f7-182">Select the PressableButton in the “BaseScene” menu.</span></span> <span data-ttu-id="897f7-183">在检查器面板中的“选择事件类型”框下，单击“+”按钮。</span><span class="sxs-lookup"><span data-stu-id="897f7-183">In the inspector panel, under the “Select Event Type” box, click the “+” button.</span></span> <span data-ttu-id="897f7-184">将“立方体”从“BaseScene”菜单拖入“仅限运行时”框，如下图所示</span><span class="sxs-lookup"><span data-stu-id="897f7-184">Drag the “cube” from the “BaseScene” menu into the “Runtime Only” box, as shown in the image below</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

<span data-ttu-id="897f7-186">单击带有“无函数”字样的下拉列表。</span><span class="sxs-lookup"><span data-stu-id="897f7-186">Click the dropdown list that says “No Function.”</span></span> <span data-ttu-id="897f7-187">依次选择“MeshRenderer”、“材料 <材料>”。</span><span class="sxs-lookup"><span data-stu-id="897f7-187">Select “MeshRenderer” then select “Material material.”</span></span> <span data-ttu-id="897f7-188">这样，就可以在按下按钮时更改材料。</span><span class="sxs-lookup"><span data-stu-id="897f7-188">This will allow you to change the material when the button is pressed.</span></span> 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

<span data-ttu-id="897f7-190">转到项目面板，搜索要更改到的材料。</span><span class="sxs-lookup"><span data-stu-id="897f7-190">Go to the project panel and search for the material you wish to change it to.</span></span> <span data-ttu-id="897f7-191">本示例将使用材料“MRTK_Standard_Cyan”，在项目选项卡的搜索栏中键入“cyan”即可找到它（MRTK 包括许多可供选择的材料和颜色）。将该材料拖到“MeshRenderer.material”下面的框中。</span><span class="sxs-lookup"><span data-stu-id="897f7-191">You are going to use the material “MRTK_Standard_Cyan” for this example, found by typing in “cyan” in the project tab’s search bar (The MRTK includes many materials and colors to choose from.) Drag the material to the box underneath “MeshRenderer.material.”</span></span> <span data-ttu-id="897f7-192">可以在“资产”>“MixedRealityToolkit.SDK”>“标准资产”>“材料”中找到 MRTK 材料。</span><span class="sxs-lookup"><span data-stu-id="897f7-192">The MRTK materials can be found in Assets>MixedRealityToolkit.SDK>StandardAssets>Materials.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

<span data-ttu-id="897f7-195">现已设置事件。按下按钮时，立方体会根据指定的材料改变颜色。</span><span class="sxs-lookup"><span data-stu-id="897f7-195">The event is now set so that when the button is pressed, the cube will change color based on the material you specified.</span></span> <span data-ttu-id="897f7-196">在本示例中，立方体将更改为青色。</span><span class="sxs-lookup"><span data-stu-id="897f7-196">In this example, the cube will change to the cyan color.</span></span>

8. <span data-ttu-id="897f7-197">接下来要设置释放操作，以便在释放按钮时，按钮会恢复其默认颜色。</span><span class="sxs-lookup"><span data-stu-id="897f7-197">Next you are going to set up the release action so that upon release, the button will go back to its default color.</span></span> <span data-ttu-id="897f7-198">重复上述步骤 7，但这次请使用“OnRelease”事件而不是“OnPress”事件，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="897f7-198">Repeat Step 7 (the previous step) but this time with the “OnRelease” event instead of the “OnPress” event, as shown in the image below.</span></span>

9.  <span data-ttu-id="897f7-199">在项目面板中，搜索一个可以在释放按钮时让立方体恢复默认颜色的材料（在本例中，我们选择了“MRTK_Standard_LightGray”）。将该材料拖到“MeshRenderer.material”字段下面的框中。</span><span class="sxs-lookup"><span data-stu-id="897f7-199">In the project panel, search for a material for the cube to default to upon button release (in our case, we chose MRTK_Standard_LightGray.) Drag the material into the box below the “MeshRenderer.material” field.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

<span data-ttu-id="897f7-201">现在，在按下按钮时，它应会更改为新颜色（例如青色）；释放按钮时，它应会恢复指定的默认颜色（例如浅灰色）。按屏幕顶部的“播放”按钮，以在编辑器中尝试这种变换，或者将项目部署到 HoloLens 2 进行测试！</span><span class="sxs-lookup"><span data-stu-id="897f7-201">Now when the button is pressed, it should change to a new color (e.g., cyan) and when the button is released it should change back to the default color you specified (e.g., light gray.) Press the “play” button on the top of the screen to try it out in the editor or deploy to your HoloLens 2 to test!</span></span> <span data-ttu-id="897f7-202">若要详细了解编辑器内部的模拟，包括手部模拟，请阅读 [MRTK 的模拟文档页](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。</span><span class="sxs-lookup"><span data-stu-id="897f7-202">To learn more about in-editor simulation, including hand simulation read the [MRTK's simulation documentation page](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).</span></span> 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="897f7-203">使用 MRTK 的网格对象集合创建按钮面板</span><span class="sxs-lookup"><span data-stu-id="897f7-203">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="897f7-204">本部分介绍如何使用 MRTK 的 GridObjectCollection 工具将多个按钮自动对齐到一个整洁的用户界面。</span><span class="sxs-lookup"><span data-stu-id="897f7-204">In this section, you will learn how to automatically align multiple buttons into a neat user interface using the MRTK’s GridObjectCollection tool.</span></span>

1. <span data-ttu-id="897f7-205">复制上一部分创建的按钮，直到有了 5 个按钮。</span><span class="sxs-lookup"><span data-stu-id="897f7-205">Duplicate the button from the previous section until you have 5 buttons.</span></span> <span data-ttu-id="897f7-206">可通过多种方式进行复制：</span><span class="sxs-lookup"><span data-stu-id="897f7-206">There are several ways to do this:</span></span>
- <span data-ttu-id="897f7-207">右键单击该按钮并单击“复制”，然后在该按钮的下方再次右键单击，并单击“粘贴”。</span><span class="sxs-lookup"><span data-stu-id="897f7-207">Right click on the button and click “copy,” then go down to below the button and right click again and click “paste.”</span></span> 
- <span data-ttu-id="897f7-208">右键单击该按钮并单击“复制”。</span><span class="sxs-lookup"><span data-stu-id="897f7-208">Right click on the button and click “duplicate.”</span></span> 
- <span data-ttu-id="897f7-209">使用键盘命令：单击立方体并按键盘上的“Ctrl+D”。</span><span class="sxs-lookup"><span data-stu-id="897f7-209">Use the keyboard command by clicking on the cube and pressing “ctrl D” on your keyboard.</span></span>

<span data-ttu-id="897f7-210">重复此步骤，直到总共有了 5 个按钮（参考下图中 5 个红色箭头）。</span><span class="sxs-lookup"><span data-stu-id="897f7-210">Repeat this until you have 5 total buttons (see 5 red arrows in image below).</span></span>

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. <span data-ttu-id="897f7-212">将按钮分组到空的父游戏对象下。</span><span class="sxs-lookup"><span data-stu-id="897f7-212">Group the buttons under an empty parent game object.</span></span> <span data-ttu-id="897f7-213">若要在网格集合中添加按钮，需要将按钮分组到公用父对象下。</span><span class="sxs-lookup"><span data-stu-id="897f7-213">In order to have the buttons in grid collection, you need to group your buttons under a common parent object.</span></span> <span data-ttu-id="897f7-214">右键单击层次结构，然后单击“创建空对象”。</span><span class="sxs-lookup"><span data-stu-id="897f7-214">Right click in the hiearachy and click “create empty.”</span></span> <span data-ttu-id="897f7-215">随后会创建一个新的空游戏对象用于放置所有按钮。</span><span class="sxs-lookup"><span data-stu-id="897f7-215">This creates a new empty game object for you to put all the buttons in.</span></span> <span data-ttu-id="897f7-216">此对象显示为“gameObject”。</span><span class="sxs-lookup"><span data-stu-id="897f7-216">It will show up as “gameObject.”</span></span> <span data-ttu-id="897f7-217">右键单击，然后将它重命名为“ButtonCollection”。</span><span class="sxs-lookup"><span data-stu-id="897f7-217">Right click and rename it to “ButtonCollection.”</span></span>

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. <span data-ttu-id="897f7-219">将所有按钮移入新集合，</span><span class="sxs-lookup"><span data-stu-id="897f7-219">Move all the buttons into the new collection.</span></span> <span data-ttu-id="897f7-220">方法是选择层次结构中的所有五个按钮对象，然后将其全部拖放到“ButtonCollection”游戏对象下面，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="897f7-220">Do this by selecting all five of the button objects in your heirarch and drag them all under “ButtonCollection” game object, as shown in the image below.</span></span> <span data-ttu-id="897f7-221">提示：若要选择多个项，可以按住 Ctrl 键并选择项。</span><span class="sxs-lookup"><span data-stu-id="897f7-221">Tip: select multiple items by holding the ctrl key while selecting items.</span></span>

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. <span data-ttu-id="897f7-223">将 MRTK 的“网格对象集合”组件添加到按钮集合中。</span><span class="sxs-lookup"><span data-stu-id="897f7-223">Add MRTK’s “Grid Object Collection” component to the button collection.</span></span>  <span data-ttu-id="897f7-224">为此，请选择“ButtonCollection”父对象，并在检查器面板中单击“添加组件”按钮。</span><span class="sxs-lookup"><span data-stu-id="897f7-224">To do this, select the “ButtonCollection” parent object and in the inspector panel, click the “Add Component” button.</span></span> <span data-ttu-id="897f7-225">然后在搜索栏中搜索“网格对象集合”，当其显示在列表中时，请将其选中。</span><span class="sxs-lookup"><span data-stu-id="897f7-225">Then search for “Grid Object Collection” in the search bar and select it when it appears in the list.</span></span>

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

<span data-ttu-id="897f7-227">使用“网格对象集合”组件可以在整洁的行、列或网格中组织按钮或任何对象集。</span><span class="sxs-lookup"><span data-stu-id="897f7-227">The Grid Object Collection component allows you to organize buttons or any set of objects in a neat row, column, or grid.</span></span> <span data-ttu-id="897f7-228">这是 MRTK 提供的构建基块之一，可让你快速方便地创建美观的用户界面。</span><span class="sxs-lookup"><span data-stu-id="897f7-228">This is one of the building blocks provided by the MRTK that provides you with a quick and simple way to create beautiful user interfaces.</span></span>

5. <span data-ttu-id="897f7-229">配置网格对象集合。</span><span class="sxs-lookup"><span data-stu-id="897f7-229">Configure the grid object collection.</span></span> <span data-ttu-id="897f7-230">为了确保所有按钮朝向用户，请选择“定位类型”，然后选择“朝向父级的正面”（如下图所示）。接下来，更改单元格大小以设置按钮之间的间距。</span><span class="sxs-lookup"><span data-stu-id="897f7-230">To ensure all the buttons face the user, select “orient type” and then select “face parent forward” (as shown in the image.) Next, change the cell size to set the space between your buttons.</span></span> <span data-ttu-id="897f7-231">对于“单元格宽度”和“单元格高度”，最初请使用 0.12 x 0.12 个单位，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="897f7-231">Start with 0.12 units by 0.12 units for the Cell Width and Cell Height, as shown in the image below.</span></span> <span data-ttu-id="897f7-232">根据所选的对象/按钮资产，可能需要调整这些值。</span><span class="sxs-lookup"><span data-stu-id="897f7-232">You may need to adjust these values, depending on object/button assets chosen.</span></span> <span data-ttu-id="897f7-233">请确保“行”设置为 1。</span><span class="sxs-lookup"><span data-stu-id="897f7-233">Make sure "Rows" is set to 1.</span></span> <span data-ttu-id="897f7-234">然后单击“更新集合”。场景应如下图所示。</span><span class="sxs-lookup"><span data-stu-id="897f7-234">Then click “Update Collection” and the scene should look like the picture below.</span></span> 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

><span data-ttu-id="897f7-236">注意：根据子对象或父对象的方向，在将来的项目中可能需要以不同的方式调整方向设置。</span><span class="sxs-lookup"><span data-stu-id="897f7-236">Note: Depending on the orientation of the child objects or parent object, you will likely need to adjust the orientation setting differently in future projects.</span></span> <span data-ttu-id="897f7-237">此外，根据集合中对象的大小，可能需要以不同的方式定义“单元格宽度”和“单元格高度”字段。</span><span class="sxs-lookup"><span data-stu-id="897f7-237">The Cell Width and the Cell Height fields may also need to be defined differently, depending on the size of the objects in your collection.</span></span>

### <a name="adding-text-into-your-scene"></a><span data-ttu-id="897f7-238">将文本添加到场景中</span><span class="sxs-lookup"><span data-stu-id="897f7-238">Adding Text into Your Scene</span></span>

<span data-ttu-id="897f7-239">本部分介绍如何将文本添加到混合现实体验以及如何编辑文本。</span><span class="sxs-lookup"><span data-stu-id="897f7-239">In this section, you will learn how to add and edit text to your mixed reality experiences.</span></span> <span data-ttu-id="897f7-240">遵照[此处](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)的说明，确保已在 Unity 中启用 TextMeshPro（如果尚未启用）。</span><span class="sxs-lookup"><span data-stu-id="897f7-240">If you haven’t already, please ensure you have TextMeshPro enabled in Unity by following the instructions [here](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).</span></span>

1. <span data-ttu-id="897f7-241">选择“ButtonCollection”父对象并右键单击集合。</span><span class="sxs-lookup"><span data-stu-id="897f7-241">Select the “ButtonCollection” parent object and right click the collection.</span></span> <span data-ttu-id="897f7-242">在下拉菜单中展开“3D 对象”，然后选择“TextMeshPro-Text”。</span><span class="sxs-lookup"><span data-stu-id="897f7-242">Expand "3D object" in the dropdown menu, then select "TextMeshPro - Text".</span></span> <span data-ttu-id="897f7-243">按钮集合下面应会显示一个 TextMeshPro 对象，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="897f7-243">You should see a TextMeshPro object under the button collection, as shown in the image below.</span></span>

<span data-ttu-id="897f7-244">![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span><span class="sxs-lookup"><span data-stu-id="897f7-244">![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span></span>

2. <span data-ttu-id="897f7-245">在 TextMeshPro 组件的“文本”字段（位于检查器面板中，如下所示）中，键入“按钮集合文本”。</span><span class="sxs-lookup"><span data-stu-id="897f7-245">In the TextMeshPro component’s Text field (located in the inspector panel, as shown below), type in “Button Collection Text.”</span></span> <span data-ttu-id="897f7-246">该文本将显示在场景中，但会隐藏在按钮和/或错误大小的对象下面。</span><span class="sxs-lookup"><span data-stu-id="897f7-246">The text will appear in the scene, but it will be hidden behind the buttons and/or the wrong size.</span></span>

![Lesson2 Chapter4 Step2](images/Lesson2_Chapter4_Step2.JPG)

3. <span data-ttu-id="897f7-248">若要改善文本大小和位置以提高可读性，请调整 TextMeshPro 组件中的“字体大小”字段，以更改字体大小。</span><span class="sxs-lookup"><span data-stu-id="897f7-248">To improve the text size and placement for readability, adjust the “font size” field in the TextMeshPro component to change the size of the font.</span></span> <span data-ttu-id="897f7-249">还需要如下图所示调整“矩形变换”位置和坐标。</span><span class="sxs-lookup"><span data-stu-id="897f7-249">You will also need to adjust the “Rect Transform” position and scale as shown in the image below.</span></span> <span data-ttu-id="897f7-250">参考下图了解用于文本配置的值，并随意使用这些值作为起点，来进一步改善文本字段的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="897f7-250">See the images below for values used for our text configuration, and feel free to use these values as a starting point from which to further improve the size and placement of your text field.</span></span>

<span data-ttu-id="897f7-251">![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="897f7-251">![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)</span></span>

5. <span data-ttu-id="897f7-252">若要修改按钮对象上的文本值，请单击任一按钮旁边的箭头展开该按钮，导航到“SeeItSayItLabel”对象，然后导航到“TextMeshPro”，在其中可根据上述步骤中所述编辑按钮中的文本。</span><span class="sxs-lookup"><span data-stu-id="897f7-252">To modify the text values on the button objects, click the arrow next to any button to expand it and navigate to the “SeeItSayItLabel” object, then navigate to “TextMeshPro,” where you can edit the text to your buttons as described in the steps above.</span></span>

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a><span data-ttu-id="897f7-254">祝贺</span><span class="sxs-lookup"><span data-stu-id="897f7-254">Congratulations</span></span>
<span data-ttu-id="897f7-255">在本课中，你已了解如何复制、自定义和配置 MRTK 配置文件设置（即，空间感知网格的可见性）。此外，你已了解如何在 HoloLens 2 中使用跟踪手来与触发事件的按钮交互。</span><span class="sxs-lookup"><span data-stu-id="897f7-255">In this lesson, you learned how to copy, customize, and configure an MRTK profile setting (i.e., spatial awareness mesh visibility.) You also learned how to interact with a button to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="897f7-256">最后，你已了解如何使用 Unity 的 Text Mesh Pro 和 MRTK 的“网格对象集合”组件创建一个简单的 UI。</span><span class="sxs-lookup"><span data-stu-id="897f7-256">Finally, you learned how to create a simple UI interface using Unity's Text Mesh Pro the MRTK's Grid Object Collection component.</span></span>

[<span data-ttu-id="897f7-257">下一课：动态内容放置和求解器</span><span class="sxs-lookup"><span data-stu-id="897f7-257">Next Lesson: Dynamic Content Placement and Solvers</span></span>](mrlearning-base-ch3.md)

