---
title: MR 学习基本模块的用户界面手动跟踪和混合现实工具包配置
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: unity 中，教程，hololens 混合的现实
ms.openlocfilehash: 1530fd1a1ee06d01e8ab0cc009dfba03873c3427
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993636"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a><span data-ttu-id="069f2-104">MR 学习基本模块的用户界面手动跟踪和混合现实工具包配置</span><span class="sxs-lookup"><span data-stu-id="069f2-104">MR Learning Base Module - User Interface, Hand Tracking, and Mixed Reality Toolkit Configuration</span></span>

<span data-ttu-id="069f2-105">在上一课中，您学习了一些 MRTK 必须提供通过启动 HoloLens 2 首个应用程序的功能。</span><span class="sxs-lookup"><span data-stu-id="069f2-105">In the previous lesson, you learned some of the capabilities the MRTK has to offer, by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="069f2-106">在下一课中，您将学习如何创建和整理以及 UI 文本面板按钮并使用默认的交互 （触控） 来与每个按钮进行交互。</span><span class="sxs-lookup"><span data-stu-id="069f2-106">In this next lesson you will learn how to create and organize buttons along with UI text panels and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="069f2-107">此外将探讨新增的简单操作和效果，如更改声音的大小和对象的颜色。</span><span class="sxs-lookup"><span data-stu-id="069f2-107">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="069f2-108">此模块将介绍如何修改 MRTK 配置文件，从开始关闭空间网格的可视化效果的基本概念。</span><span class="sxs-lookup"><span data-stu-id="069f2-108">This module will introduce basic concepts on how to modify MRTK profiles, starting with turning off the visualization of the spatial mesh.</span></span> 

## <a name="objectives"></a><span data-ttu-id="069f2-109">目标</span><span class="sxs-lookup"><span data-stu-id="069f2-109">Objectives</span></span>

* <span data-ttu-id="069f2-110">自定义和配置混合现实工具包配置文件</span><span class="sxs-lookup"><span data-stu-id="069f2-110">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="069f2-111">与使用 UI 元素和按钮的全息交互</span><span class="sxs-lookup"><span data-stu-id="069f2-111">Interacting with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="069f2-112">基本手动跟踪输入和交互</span><span class="sxs-lookup"><span data-stu-id="069f2-112">Basic hand-tracking input and interactions</span></span>

## <a name="instructions"></a><span data-ttu-id="069f2-113">说明</span><span class="sxs-lookup"><span data-stu-id="069f2-113">Instructions</span></span>

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="069f2-114">如何配置混合现实工具包配置文件 （更改空间感知显示选项）</span><span class="sxs-lookup"><span data-stu-id="069f2-114">How to Configure the Mixed-Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<span data-ttu-id="069f2-115">在本部分中将了解如何自定义和配置的默认混合现实工具包配置文件通过调整空间感知的显示选项网格。</span><span class="sxs-lookup"><span data-stu-id="069f2-115">In this section you will learn how to customize and configure the default Mixed Reality Toolkit profiles by adjusting the display option of the spatial awareness mesh.</span></span> <span data-ttu-id="069f2-116">可能遵循这些原理同样调整任何设置或 MRTK 配置文件中的值。</span><span class="sxs-lookup"><span data-stu-id="069f2-116">You may follow these same principles for adjusting any settings or values in the MRTK profiles.</span></span>

1. <span data-ttu-id="069f2-117">从"BaseScene"层次结构中选择混合现实工具包 (MRTK)。</span><span class="sxs-lookup"><span data-stu-id="069f2-117">Select Mixed-Reality Toolkit (MRTK) from the “BaseScene” hierarchy.</span></span> <span data-ttu-id="069f2-118">在检查器窗格中，查找"混合现实工具包脚本"并选择"活动配置文件"，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="069f2-118">In the inspector panel, look for the “Mixed Reality Toolkit Script” and select the “active profile” as shown in the figure below.</span></span> <span data-ttu-id="069f2-119">双击以打开它。</span><span class="sxs-lookup"><span data-stu-id="069f2-119">Double click to open it.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

><span data-ttu-id="069f2-121">注意：默认情况下，MRTK 配置文件是不可编辑。</span><span class="sxs-lookup"><span data-stu-id="069f2-121">Note: By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="069f2-122">这些是默认配置文件模板可以从其复制并自定义。</span><span class="sxs-lookup"><span data-stu-id="069f2-122">These are default profile templates from which you can copy and customize.</span></span> <span data-ttu-id="069f2-123">有多个层的自定义和配置文件，因此它是标准做法来复制和配置一个或多个设置时，自定义多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="069f2-123">There are several layers of customization and profiles, so it is standard practice to copy and customize several profiles when configuring one or more settings.</span></span>
>
><span data-ttu-id="069f2-124">若要了解有关 MRTK 配置文件和其体系结构的详细信息，请访问[MRTK 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)。</span><span class="sxs-lookup"><span data-stu-id="069f2-124">To discover more about MRTK profiles and their architecture, please visit the [MRTK documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>).</span></span>

2. <span data-ttu-id="069f2-125">创建进行自定义的默认配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="069f2-125">Create a copy of the default profile to customize it.</span></span> <span data-ttu-id="069f2-126">若要复制的默认配置文件，单击"复制和自定义"按钮 （请参阅图）。</span><span class="sxs-lookup"><span data-stu-id="069f2-126">To copy a default profile, click the “Copy & Customize” button (see image).</span></span> <span data-ttu-id="069f2-127">这将创建一份 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="069f2-127">This creates a copy of the MRTK profile.</span></span> <span data-ttu-id="069f2-128">使用您自己的 MRTK 配置文件的副本，您现在可以自定义此配置文件中的任何设置。</span><span class="sxs-lookup"><span data-stu-id="069f2-128">With your own copy of the MRTK profile, you now have the ability customize any settings in this profile.</span></span> <span data-ttu-id="069f2-129">您还需要在后续步骤中所述嵌套在此配置文件，任何其他配置文件的重复副本/自定义步骤。</span><span class="sxs-lookup"><span data-stu-id="069f2-129">You will also need to repeat the copy/customize step for any additional profiles nested under this profile, as described in the subsequent steps.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. <span data-ttu-id="069f2-131">禁用空间感知网格的可见性。</span><span class="sxs-lookup"><span data-stu-id="069f2-131">Disable the visibility of the spatial awareness mesh.</span></span> <span data-ttu-id="069f2-132">若要执行此操作，找到"空间感知系统设置"图中所示。</span><span class="sxs-lookup"><span data-stu-id="069f2-132">To do this, find “Spatial Awareness System Settings” as shown in the image.</span></span> <span data-ttu-id="069f2-133">单击"克隆"按钮右侧的"空间感知系统配置文件"以默认配置文件替换为可自定义的副本。</span><span class="sxs-lookup"><span data-stu-id="069f2-133">Click the "clone" button to the right of the the “Spatial Awareness System Profile” to replace the default profile with a customizable copy.</span></span> <span data-ttu-id="069f2-134">如果出现一个弹出窗口，按"克隆"按钮，如下面的第二个图像中所示。</span><span class="sxs-lookup"><span data-stu-id="069f2-134">If a pop-up window appears, press the "Clone" button, as shown in the second image below.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. <span data-ttu-id="069f2-137">创建自定义默认混合现实空间网格观察者的副本。</span><span class="sxs-lookup"><span data-stu-id="069f2-137">Create a custom copy of the Default Mixed Reality Spatial Mesh Observer.</span></span> <span data-ttu-id="069f2-138">单击"Windows 混合现实空间网格观察者"以查看其他选项旁边的向下箭头。</span><span class="sxs-lookup"><span data-stu-id="069f2-138">Click the down arrow next to “Windows Mixed Reality Spatial Mesh Observer” to see additional options.</span></span> <span data-ttu-id="069f2-139">在这些选项中，你将看到"默认混合现实空间网格观察者"会显示灰 （不可编辑）。</span><span class="sxs-lookup"><span data-stu-id="069f2-139">In these options, you will see the “Default Mixed Reality Spatial Mesh Observer” which appears greyed (not editable).</span></span> <span data-ttu-id="069f2-140">因此你可以对其进行编辑，必须将此默认配置文件替换的可自定义的副本。</span><span class="sxs-lookup"><span data-stu-id="069f2-140">You must replace this default profile with a customizable copy so you can edit it.</span></span> <span data-ttu-id="069f2-141">单击向右 （标记的绿色箭头） 按钮以克隆副本。</span><span class="sxs-lookup"><span data-stu-id="069f2-141">Click the button to the right (marked by green arrow) to clone a copy.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. <span data-ttu-id="069f2-143">接下来，将调整说"的阻挡物。"的显示选项的设置</span><span class="sxs-lookup"><span data-stu-id="069f2-143">Next, you will adjust the settings for the display option to say “occlusion.”</span></span> <span data-ttu-id="069f2-144">这会使空间网格不可见，但仍隐藏游戏对象背后空间网格 （这称为封闭。）</span><span class="sxs-lookup"><span data-stu-id="069f2-144">This makes the spatial mesh invisible, but still hide game objects behind the spatial mesh (this is known as occlusion.)</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

><span data-ttu-id="069f2-146">注意：空间映射网格不可见时，仍存在，并可以与之交互。</span><span class="sxs-lookup"><span data-stu-id="069f2-146">Note: While the spatial mapping mesh is not visible, it is still present and you can interact with it.</span></span> <span data-ttu-id="069f2-147">任何全息背后空间映射网格 （例如一张全息图背后可见墙壁上） 将无法看到由于封闭设置。</span><span class="sxs-lookup"><span data-stu-id="069f2-147">Any holograms behind the spatial mapping mesh (e.g. A hologram behind your visible wall) will not be visible because of the occlusion setting.</span></span>

<span data-ttu-id="069f2-148">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="069f2-148">Congratulations!</span></span> <span data-ttu-id="069f2-149">你刚刚了解了如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="069f2-149">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="069f2-150">如您所见，若要修改 MRTK 设置，需要创建的默认配置文件的副本，以便您可以编辑它们。</span><span class="sxs-lookup"><span data-stu-id="069f2-150">As you can see, in order to modify MRTK settings you need to create copies of the default profiles so that you can edit them.</span></span> <span data-ttu-id="069f2-151">您将始终拥有的默认配置文件 （这是不可编辑） 若要返回到，如果你想要使用新的设置创建配置文件或回头参考默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="069f2-151">You will always have the default profiles (which are not editable) to go back to if you wanted to create a profile with new settings, or refer back to the default profiles.</span></span> <span data-ttu-id="069f2-152">有许多可以调整的设置。</span><span class="sxs-lookup"><span data-stu-id="069f2-152">There are numerous settings that you can adjust.</span></span> <span data-ttu-id="069f2-153">有关为 MRTK 配置文件设置的完整参考，请参阅此处的 MRTK 文档： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html</span><span class="sxs-lookup"><span data-stu-id="069f2-153">For full reference to MRTK profile settings, refer to the MRTK documentation here: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html</span></span>

### <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="069f2-154">跟踪手势和种交互的按钮</span><span class="sxs-lookup"><span data-stu-id="069f2-154">Hand Tracking Gestures and Interactable buttons</span></span>
<span data-ttu-id="069f2-155">在本部分中，将了解如何使用跟踪来按种交互的按钮的工具。</span><span class="sxs-lookup"><span data-stu-id="069f2-155">In this section, you will learn how to use hand tracking to press an interactable button.</span></span>

1. <span data-ttu-id="069f2-156">从项目文件夹中选择"资产"。</span><span class="sxs-lookup"><span data-stu-id="069f2-156">Select “Assets” from the projects folder.</span></span>

2. <span data-ttu-id="069f2-157">键入在搜索栏中，"pressablebutton。"</span><span class="sxs-lookup"><span data-stu-id="069f2-157">Type in the search bar, “pressablebutton.”</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. <span data-ttu-id="069f2-159">将名为"PressableButton"预设 （由蓝色框表示） 拖到你的层次结构。</span><span class="sxs-lookup"><span data-stu-id="069f2-159">Drag the prefab (represented by a blue box) named "PressableButton" into your hierarchy.</span></span> 

   > <span data-ttu-id="069f2-160">注意：如果一条消息获取有关"导入 TMP Essentials"请其导入这一次。</span><span class="sxs-lookup"><span data-stu-id="069f2-160">Note: If you get a message about “importing TMP Essentials” please import it at this time.</span></span> <span data-ttu-id="069f2-161">如果 TMP Essentials 已不是项目的一部分，您可能需要在导入 TMP Essentials 的服务器，否则按钮文本可能不会显示后重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="069f2-161">If TMP Essentials was not already part of your project, you may need to repeat this step after importing TMP Essentials, otherwise button text may not appear.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. <span data-ttu-id="069f2-163">双击"PressableButton"游戏对象 （它现在应是 BaseScene 层次结构中） 以查看在您的场景，如图所示 （按钮图形可能会显示不同于下图） 中所示。</span><span class="sxs-lookup"><span data-stu-id="069f2-163">Double click the “PressableButton” game object (which should now be in your BaseScene hierarchy) to view it in your scene, as shown in the image below (your button graphics may appear different than the image below).</span></span> 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. <span data-ttu-id="069f2-165">在检查器窗格中，单击"添加事件"提供的事件响应推送时的按钮。</span><span class="sxs-lookup"><span data-stu-id="069f2-165">In the inspector panel, click “Add Event” to give the button an event to respond to when pushed.</span></span> <span data-ttu-id="069f2-166">在显示的选项，选择下拉列表菜单。</span><span class="sxs-lookup"><span data-stu-id="069f2-166">In the option that appears, select the drop-down menu.</span></span> <span data-ttu-id="069f2-167">选择"InteractableOnPressReciever。"</span><span class="sxs-lookup"><span data-stu-id="069f2-167">Select “InteractableOnPressReciever.”</span></span> <span data-ttu-id="069f2-168">这样，按钮按下的事件跟踪手的形状按下按钮时响应。</span><span class="sxs-lookup"><span data-stu-id="069f2-168">This allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. <span data-ttu-id="069f2-170">将多维数据集添加到场景。</span><span class="sxs-lookup"><span data-stu-id="069f2-170">Add a cube to the scene.</span></span> <span data-ttu-id="069f2-171">右键单击层次结构区，选择三维对象，然后单击"多维数据集。"</span><span class="sxs-lookup"><span data-stu-id="069f2-171">Right click on the hierarchy area, select 3D object, then click on “cube.”</span></span> <span data-ttu-id="069f2-172">现在，多维数据集应在您的显示器。</span><span class="sxs-lookup"><span data-stu-id="069f2-172">Now, a cube should be in your display.</span></span> <span data-ttu-id="069f2-173">它将看上去非常大，因此，调整坐标 （尽管仍在层次结构区域中选择"多维数据集"） 以减小大小。</span><span class="sxs-lookup"><span data-stu-id="069f2-173">It will appear very large, so adjust the coordinates (while “cube” is still selected in the hierarchy area) to decrease the size.</span></span> <span data-ttu-id="069f2-174">将缩放值设置为 x = 0.1，y = 0.1 和 z = 0.1。</span><span class="sxs-lookup"><span data-stu-id="069f2-174">Set the scale values to x = 0.1, y = 0.1 and z = 0.1.</span></span> <span data-ttu-id="069f2-175">为确保在将附近 pressable 按钮，将其放在场景中定位该多维数据集，但不是重叠的按钮。</span><span class="sxs-lookup"><span data-stu-id="069f2-175">Be sure to position the cube in your scene to place it near the pressable button, but not overlapping with the button.</span></span> <span data-ttu-id="069f2-176">在下图中，多维数据集的位置是 x = 0，y = 0.2 和 z = 1。</span><span class="sxs-lookup"><span data-stu-id="069f2-176">In the image below, the cube’s position is x = 0, y = 0.2, and z = 1.</span></span> 

   > <span data-ttu-id="069f2-177">注意：一般情况下，在 Unity 中的 1 个单位是大致相当于现实生活中的 1 米。</span><span class="sxs-lookup"><span data-stu-id="069f2-177">Note: In general, 1 unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="069f2-178">有例外情况，例如当对象是扩展对象的子级。</span><span class="sxs-lookup"><span data-stu-id="069f2-178">There are exceptions to this, for example when objects are children of scaled objects.</span></span>
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. <span data-ttu-id="069f2-181">在此步骤中您将设置多维数据集时按下按钮更改颜色。</span><span class="sxs-lookup"><span data-stu-id="069f2-181">In this step you will set up the cube to change color when your button is pressed.</span></span> <span data-ttu-id="069f2-182">在"BaseScene"菜单中选择 PressableButton。</span><span class="sxs-lookup"><span data-stu-id="069f2-182">Select the PressableButton in the “BaseScene” menu.</span></span> <span data-ttu-id="069f2-183">在检查器窗格中，在"选择事件类型"框中，单击"+"按钮。</span><span class="sxs-lookup"><span data-stu-id="069f2-183">In the inspector panel, under the “Select Event Type” box, click the “+” button.</span></span> <span data-ttu-id="069f2-184">将"多维数据集"从"BaseScene"菜单到"仅限运行时"框中，如下图中所示</span><span class="sxs-lookup"><span data-stu-id="069f2-184">Drag the “cube” from the “BaseScene” menu into the “Runtime Only” box, as shown in the image below</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

<span data-ttu-id="069f2-186">单击下拉列表显示"没有函数"。</span><span class="sxs-lookup"><span data-stu-id="069f2-186">Click the dropdown list that says “No Function.”</span></span> <span data-ttu-id="069f2-187">选择"MeshRenderer"然后选择"材料 material。"</span><span class="sxs-lookup"><span data-stu-id="069f2-187">Select “MeshRenderer” then select “Material material.”</span></span> <span data-ttu-id="069f2-188">这将允许您按下按钮更改材料。</span><span class="sxs-lookup"><span data-stu-id="069f2-188">This will allow you to change the material when the button is pressed.</span></span> 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

<span data-ttu-id="069f2-190">请转到项目面板和搜索你想要将其更改为的材料。</span><span class="sxs-lookup"><span data-stu-id="069f2-190">Go to the project panel and search for the material you wish to change it to.</span></span> <span data-ttu-id="069f2-191">您将此示例中使用的材料"MRTK_Standard_Cyan"，找到以"青色"（MRTK 包括很多材料和可供选择的颜色。） 项目选项卡的搜索栏中键入将材料拖到"MeshRenderer.material。"下方的框</span><span class="sxs-lookup"><span data-stu-id="069f2-191">You are going to use the material “MRTK_Standard_Cyan” for this example, found by typing in “cyan” in the project tab’s search bar (The MRTK includes many materials and colors to choose from.) Drag the material to the box underneath “MeshRenderer.material.”</span></span> <span data-ttu-id="069f2-192">可以在资产中找到 MRTK 材料 > MixedRealityToolkit.SDK > StandardAssets > 材料。</span><span class="sxs-lookup"><span data-stu-id="069f2-192">The MRTK materials can be found in Assets>MixedRealityToolkit.SDK>StandardAssets>Materials.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

<span data-ttu-id="069f2-195">现在设置了事件，以便按下按钮时，多维数据集将更改基于你指定的材料的颜色。</span><span class="sxs-lookup"><span data-stu-id="069f2-195">The event is now set so that when the button is pressed, the cube will change color based on the material you specified.</span></span> <span data-ttu-id="069f2-196">在此示例中，多维数据集将变为青色颜色。</span><span class="sxs-lookup"><span data-stu-id="069f2-196">In this example, the cube will change to the cyan color.</span></span>

8. <span data-ttu-id="069f2-197">接下来要设置发布操作，以便在版本中，按钮将返回到其默认颜色。</span><span class="sxs-lookup"><span data-stu-id="069f2-197">Next you are going to set up the release action so that upon release, the button will go back to its default color.</span></span> <span data-ttu-id="069f2-198">重复步骤 7 （上一步），但这次使用"OnRelease"事件，而不是"OnPress"事件，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="069f2-198">Repeat Step 7 (the previous step) but this time with the “OnRelease” event instead of the “OnPress” event, as shown in the image below.</span></span>

9.  <span data-ttu-id="069f2-199">在项目面板中，搜索为默认值在按钮时释放该多维数据集的材料 （在本例中，我们选择了 MRTK_Standard_LightGray。）将材料拖到"MeshRenderer.material"字段下方的框。</span><span class="sxs-lookup"><span data-stu-id="069f2-199">In the project panel, search for a material for the cube to default to upon button release (in our case, we chose MRTK_Standard_LightGray.) Drag the material into the box below the “MeshRenderer.material” field.</span></span>

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

<span data-ttu-id="069f2-201">现在，按下按钮时，它应更改为新的颜色 (例如，蓝绿色) 和释放按钮时应更改回您指定的默认颜色 （例如，浅灰色。）按以在编辑器中试用它或将部署到 HoloLens 2，以测试在屏幕顶部的"播放"按钮 ！</span><span class="sxs-lookup"><span data-stu-id="069f2-201">Now when the button is pressed, it should change to a new color (e.g., cyan) and when the button is released it should change back to the default color you specified (e.g., light gray.) Press the “play” button on the top of the screen to try it out in the editor or deploy to your HoloLens 2 to test!</span></span> <span data-ttu-id="069f2-202">若要详细了解在编辑器中模拟，包括读取的手动模拟[MRTK 的模拟文档页](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。</span><span class="sxs-lookup"><span data-stu-id="069f2-202">To learn more about in-editor simulation, including hand simulation read the [MRTK's simulation documentation page](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).</span></span> 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="069f2-203">创建按钮使用 MRTK 的网格对象集合的一个面板</span><span class="sxs-lookup"><span data-stu-id="069f2-203">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="069f2-204">在本部分中，将了解如何自动调整到一个巧妙的用户界面中使用 MRTK GridObjectCollection 工具的多个按钮。</span><span class="sxs-lookup"><span data-stu-id="069f2-204">In this section, you will learn how to automatically align multiple buttons into a neat user interface using the MRTK’s GridObjectCollection tool.</span></span>

1. <span data-ttu-id="069f2-205">重复上一节中的按钮，直到你具有 5 个按钮。</span><span class="sxs-lookup"><span data-stu-id="069f2-205">Duplicate the button from the previous section until you have 5 buttons.</span></span> <span data-ttu-id="069f2-206">有几种方法来执行此操作：</span><span class="sxs-lookup"><span data-stu-id="069f2-206">There are several ways to do this:</span></span>
- <span data-ttu-id="069f2-207">右键单击的按钮单击"复制，"然后向下按钮下方和再次右键单击然后单击"粘贴"。</span><span class="sxs-lookup"><span data-stu-id="069f2-207">Right click on the button and click “copy,” then go down to below the button and right click again and click “paste.”</span></span> 
- <span data-ttu-id="069f2-208">右键单击的按钮，然后单击"重复。"</span><span class="sxs-lookup"><span data-stu-id="069f2-208">Right click on the button and click “duplicate.”</span></span> 
- <span data-ttu-id="069f2-209">通过单击多维数据集并按"ctrl D"在键盘上的使用的键盘命令。</span><span class="sxs-lookup"><span data-stu-id="069f2-209">Use the keyboard command by clicking on the cube and pressing “ctrl D” on your keyboard.</span></span>

<span data-ttu-id="069f2-210">重复此步骤，直到你具有 5 个总按钮 （请参阅下图中的 5 个红色箭头）。</span><span class="sxs-lookup"><span data-stu-id="069f2-210">Repeat this until you have 5 total buttons (see 5 red arrows in image below).</span></span>

![Mrlearning 基本 Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. <span data-ttu-id="069f2-212">组为空的父游戏对象下的按钮。</span><span class="sxs-lookup"><span data-stu-id="069f2-212">Group the buttons under an empty parent game object.</span></span> <span data-ttu-id="069f2-213">为了获得网格集合中的按钮，您需要进行分组你常用的父对象下的按钮。</span><span class="sxs-lookup"><span data-stu-id="069f2-213">In order to have the buttons in grid collection, you need to group your buttons under a common parent object.</span></span> <span data-ttu-id="069f2-214">Hiearachy 中右键单击，然后单击"创建为空。"</span><span class="sxs-lookup"><span data-stu-id="069f2-214">Right click in the hiearachy and click “create empty.”</span></span> <span data-ttu-id="069f2-215">这将创建可将所有按钮都放在新的空游戏对象。</span><span class="sxs-lookup"><span data-stu-id="069f2-215">This creates a new empty game object for you to put all the buttons in.</span></span> <span data-ttu-id="069f2-216">它将显示为"gameObject。"</span><span class="sxs-lookup"><span data-stu-id="069f2-216">It will show up as “gameObject.”</span></span> <span data-ttu-id="069f2-217">右键单击，然后将它重命名为"ButtonCollection。"</span><span class="sxs-lookup"><span data-stu-id="069f2-217">Right click and rename it to “ButtonCollection.”</span></span>

![Mrlearning 基本 Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. <span data-ttu-id="069f2-219">将所有按钮都移动到新集合。</span><span class="sxs-lookup"><span data-stu-id="069f2-219">Move all the buttons into the new collection.</span></span> <span data-ttu-id="069f2-220">执行此操作通过你 heirarch 中选择所有五个按钮对象并将其拖下面"ButtonCollection"游戏对象，对所有，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="069f2-220">Do this by selecting all five of the button objects in your heirarch and drag them all under “ButtonCollection” game object, as shown in the image below.</span></span> <span data-ttu-id="069f2-221">提示： 选择项时按住 ctrl 键选择多个项目。</span><span class="sxs-lookup"><span data-stu-id="069f2-221">Tip: select multiple items by holding the ctrl key while selecting items.</span></span>

![Mrlearning 基本 Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. <span data-ttu-id="069f2-223">将 MRTK 的"网格对象集合"组件添加到按钮集合。</span><span class="sxs-lookup"><span data-stu-id="069f2-223">Add MRTK’s “Grid Object Collection” component to the button collection.</span></span>  <span data-ttu-id="069f2-224">若要执行此操作，选择"ButtonCollection"父对象，并在检查器窗格中，单击"添加组件"按钮。</span><span class="sxs-lookup"><span data-stu-id="069f2-224">To do this, select the “ButtonCollection” parent object and in the inspector panel, click the “Add Component” button.</span></span> <span data-ttu-id="069f2-225">并在搜索栏中搜索"网格对象集合"并选择它时它将显示在列表中。</span><span class="sxs-lookup"><span data-stu-id="069f2-225">Then search for “Grid Object Collection” in the search bar and select it when it appears in the list.</span></span>

![Mrlearning 基本 Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

<span data-ttu-id="069f2-227">网格对象集合组件允许您将按钮或任何巧妙行、 列或网格中的对象集。</span><span class="sxs-lookup"><span data-stu-id="069f2-227">The Grid Object Collection component allows you to organize buttons or any set of objects in a neat row, column, or grid.</span></span> <span data-ttu-id="069f2-228">这是由你提供了一种快速简单的方式来创建美观的用户界面 MRTK 提供构建基块之一。</span><span class="sxs-lookup"><span data-stu-id="069f2-228">This is one of the building blocks provided by the MRTK that provides you with a quick and simple way to create beautiful user interfaces.</span></span>

5. <span data-ttu-id="069f2-229">配置网格对象集合。</span><span class="sxs-lookup"><span data-stu-id="069f2-229">Configure the grid object collection.</span></span> <span data-ttu-id="069f2-230">若要确保所有按钮人脸用户，选择"定位类型"，并选择"人脸父向前"（如下图所示。）接下来，更改单元格大小以设置你的按钮之间的空间。</span><span class="sxs-lookup"><span data-stu-id="069f2-230">To ensure all the buttons face the user, select “orient type” and then select “face parent forward” (as shown in the image.) Next, change the cell size to set the space between your buttons.</span></span> <span data-ttu-id="069f2-231">开始按 0.12 单位 0.12 单位的单元格宽度和单元格高度，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="069f2-231">Start with 0.12 units by 0.12 units for the Cell Width and Cell Height, as shown in the image below.</span></span> <span data-ttu-id="069f2-232">您可能需要调整这些值，具体取决于选择的对象/按钮资产。</span><span class="sxs-lookup"><span data-stu-id="069f2-232">You may need to adjust these values, depending on object/button assets chosen.</span></span> <span data-ttu-id="069f2-233">请确保"行"设置为 1。</span><span class="sxs-lookup"><span data-stu-id="069f2-233">Make sure "Rows" is set to 1.</span></span> <span data-ttu-id="069f2-234">然后单击"更新集合"，场景应外观如下图所示。</span><span class="sxs-lookup"><span data-stu-id="069f2-234">Then click “Update Collection” and the scene should look like the picture below.</span></span> 


![Mrlearning 基本 Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

><span data-ttu-id="069f2-236">注意：具体取决于子对象或父对象的方向，您可能需要调整在将来的项目中以不同方式设置的方向。</span><span class="sxs-lookup"><span data-stu-id="069f2-236">Note: Depending on the orientation of the child objects or parent object, you will likely need to adjust the orientation setting differently in future projects.</span></span> <span data-ttu-id="069f2-237">单元格宽度和单元格高度字段可能还需要有不同，具体取决于你的集合中的对象大小的定义。</span><span class="sxs-lookup"><span data-stu-id="069f2-237">The Cell Width and the Cell Height fields may also need to be defined differently, depending on the size of the objects in your collection.</span></span>

### <a name="adding-text-into-your-scene"></a><span data-ttu-id="069f2-238">将文本添加到您的场景</span><span class="sxs-lookup"><span data-stu-id="069f2-238">Adding Text into Your Scene</span></span>

<span data-ttu-id="069f2-239">在本部分中，将了解如何添加和编辑你的混合的现实体验到的文本。</span><span class="sxs-lookup"><span data-stu-id="069f2-239">In this section, you will learn how to add and edit text to your mixed reality experiences.</span></span> <span data-ttu-id="069f2-240">如果你尚未这样做，请确保您具有在 Unity 中的说明启用 TextMeshPro[此处](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)。</span><span class="sxs-lookup"><span data-stu-id="069f2-240">If you haven’t already, please ensure you have TextMeshPro enabled in Unity by following the instructions [here](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).</span></span>

1. <span data-ttu-id="069f2-241">选择"ButtonCollection"父对象，右键单击的集合。</span><span class="sxs-lookup"><span data-stu-id="069f2-241">Select the “ButtonCollection” parent object and right click the collection.</span></span> <span data-ttu-id="069f2-242">在下拉列表菜单中，展开"3D 对象"，然后选择"TextMeshPro-Text"。</span><span class="sxs-lookup"><span data-stu-id="069f2-242">Expand "3D object" in the dropdown menu, then select "TextMeshPro - Text".</span></span> <span data-ttu-id="069f2-243">下图中所示，您应看到按钮集合中下, 一个 TextMeshPro 对象。</span><span class="sxs-lookup"><span data-stu-id="069f2-243">You should see a TextMeshPro object under the button collection, as shown in the image below.</span></span>

<span data-ttu-id="069f2-244">![第 2 课第 4 章 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![第 2 课第 4 章 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span><span class="sxs-lookup"><span data-stu-id="069f2-244">![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span></span>

2. <span data-ttu-id="069f2-245">在 TextMeshPro 组件的文本字段中 （位于检查器面板中，如下所示），键入"按钮集合 Text"。</span><span class="sxs-lookup"><span data-stu-id="069f2-245">In the TextMeshPro component’s Text field (located in the inspector panel, as shown below), type in “Button Collection Text.”</span></span> <span data-ttu-id="069f2-246">文本将显示在场景中，但它会隐藏在按钮和/或错误的大小。</span><span class="sxs-lookup"><span data-stu-id="069f2-246">The text will appear in the scene, but it will be hidden behind the buttons and/or the wrong size.</span></span>

![第 2 课第 4 章步骤 2](images/Lesson2_Chapter4_Step2.JPG)

3. <span data-ttu-id="069f2-248">若要提高的文本大小和位置以提高可读性，调整要更改字体大小的 TextMeshPro 组件中的"字体大小"字段。</span><span class="sxs-lookup"><span data-stu-id="069f2-248">To improve the text size and placement for readability, adjust the “font size” field in the TextMeshPro component to change the size of the font.</span></span> <span data-ttu-id="069f2-249">您还需要调整"Rect 转换"位置和缩放比例，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="069f2-249">You will also need to adjust the “Rect Transform” position and scale as shown in the image below.</span></span> <span data-ttu-id="069f2-250">请参阅下图中的值用于我们的文本的配置，并随意使用这些值作为起始点以进一步改善的大小和位置的文本字段。</span><span class="sxs-lookup"><span data-stu-id="069f2-250">See the images below for values used for our text configuration, and feel free to use these values as a starting point from which to further improve the size and placement of your text field.</span></span>

<span data-ttu-id="069f2-251">![第 2 课第 4 章 Step3](images/Lesson2_Chapter4_Step3.JPG)
![第 2 课第 4 章步骤 4](images/Lesson2_Chapter4_Step4.JPG)</span><span class="sxs-lookup"><span data-stu-id="069f2-251">![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)</span></span>

5. <span data-ttu-id="069f2-252">若要修改的按钮对象上的文本值，单击导航到"SeeItSayItLabel"的对象，并展开任何按钮旁边的箭头，然后导航到"TextMeshPro"，其中可以为你的按钮，如上述步骤中所述编辑文本。</span><span class="sxs-lookup"><span data-stu-id="069f2-252">To modify the text values on the button objects, click the arrow next to any button to expand it and navigate to the “SeeItSayItLabel” object, then navigate to “TextMeshPro,” where you can edit the text to your buttons as described in the steps above.</span></span>

![第 2 课第 4 章步骤 5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a><span data-ttu-id="069f2-254">恭喜 ！</span><span class="sxs-lookup"><span data-stu-id="069f2-254">Congratulations</span></span>
<span data-ttu-id="069f2-255">在本课程中，您学习了如何复制、 自定义和配置 MRTK 配置文件设置 （即，空间感知网格可见性。）您还学习了如何使用跟踪的手上 HoloLens 2 触发事件的按钮与进行交互。</span><span class="sxs-lookup"><span data-stu-id="069f2-255">In this lesson, you learned how to copy, customize, and configure an MRTK profile setting (i.e., spatial awareness mesh visibility.) You also learned how to interact with a button to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="069f2-256">最后，您学习了如何创建一个简单的 UI 接口使用 Unity 的文本 Mesh Pro MRTK 的网格对象集合组件。</span><span class="sxs-lookup"><span data-stu-id="069f2-256">Finally, you learned how to create a simple UI interface using Unity's Text Mesh Pro the MRTK's Grid Object Collection component.</span></span>

[<span data-ttu-id="069f2-257">下一课：动态内容的位置和求解器</span><span class="sxs-lookup"><span data-stu-id="069f2-257">Next Lesson: Dynamic Content Placement and Solvers</span></span>](mrlearning-base-ch3.md)

