---
title: 入门教程-3。 创建用户界面并配置混合现实工具包
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: f0a54bb591479dbe8ffa719cb5e6a9d846f67f9e
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539745"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="223f4-105">3. 创建用户界面并配置混合现实工具包</span><span class="sxs-lookup"><span data-stu-id="223f4-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>

<span data-ttu-id="223f4-106">在上一课中，您已了解到混合现实工具包（MRTK）通过启动适用于 HoloLens 2 的第一个应用程序而必须提供的一些功能。</span><span class="sxs-lookup"><span data-stu-id="223f4-106">In the previous lesson, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="223f4-107">在下一课中，您将学习如何创建和组织按钮以及 UI 文本面板，并使用默认交互（触摸）与每个按钮进行交互。</span><span class="sxs-lookup"><span data-stu-id="223f4-107">In this next lesson you'll learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="223f4-108">此外，本课还会探讨如何添加简单的操作和效果，例如更改对象的大小、声音和颜色。</span><span class="sxs-lookup"><span data-stu-id="223f4-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="223f4-109">此模块将介绍有关修改 MRTK 配置文件的基本概念，从关闭[空间映射](spatial-mapping.md)网格可视化效果开始。</span><span class="sxs-lookup"><span data-stu-id="223f4-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="223f4-110">目标</span><span class="sxs-lookup"><span data-stu-id="223f4-110">Objectives</span></span>

* <span data-ttu-id="223f4-111">自定义和配置混合现实工具包配置文件</span><span class="sxs-lookup"><span data-stu-id="223f4-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="223f4-112">使用 UI 元素和按钮与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="223f4-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="223f4-113">基本的手动跟踪输入和交互</span><span class="sxs-lookup"><span data-stu-id="223f4-113">Basic hand-tracking input and interactions</span></span>

## <a name="instructions"></a><span data-ttu-id="223f4-114">说明</span><span class="sxs-lookup"><span data-stu-id="223f4-114">Instructions</span></span>

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="223f4-115">如何配置混合现实工具包配置文件（更改空间感知显示选项）</span><span class="sxs-lookup"><span data-stu-id="223f4-115">How to Configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>

<span data-ttu-id="223f4-116">在本部分中，你将了解如何通过调整空间感知网格的显示选项来自定义和配置默认的 MRTK 配置文件。</span><span class="sxs-lookup"><span data-stu-id="223f4-116">In this section, you'll learn how to customize and configure the default MRTK profiles by adjusting the display option of the spatial awareness mesh.</span></span> <span data-ttu-id="223f4-117">调整 MRTK 配置文件中的任何设置或值时，也可以遵循这些原则。</span><span class="sxs-lookup"><span data-stu-id="223f4-117">You may follow these same principles for adjusting any settings or values in the MRTK profiles.</span></span>

1. <span data-ttu-id="223f4-118">从 "BaseScene" 层次结构中选择混合现实工具包（MRTK）。</span><span class="sxs-lookup"><span data-stu-id="223f4-118">Select Mixed-Reality Toolkit (MRTK) from the BaseScene hierarchy.</span></span> <span data-ttu-id="223f4-119">在 "检查器" 面板中，查找混合现实工具包脚本并选择活动配置文件，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-119">In the inspector panel, look for the Mixed Reality Toolkit Script and select the active profile as shown in the figure below.</span></span> <span data-ttu-id="223f4-120">双击以打开它。</span><span class="sxs-lookup"><span data-stu-id="223f4-120">Double-click to open it.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step1.png)

    >[!NOTE]
    ><span data-ttu-id="223f4-122">默认情况下，MRTK 配置文件不可编辑。</span><span class="sxs-lookup"><span data-stu-id="223f4-122">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="223f4-123">这些是可以复制和自定义的默认配置文件模板。</span><span class="sxs-lookup"><span data-stu-id="223f4-123">These are default profile templates that you can copy and customize.</span></span> <span data-ttu-id="223f4-124">自定义项和配置文件有多个层。</span><span class="sxs-lookup"><span data-stu-id="223f4-124">There are several layers of customization and profiles.</span></span> <span data-ttu-id="223f4-125">因此，在配置一个或多个设置时，可以复制和自定义多个配置文件。</span><span class="sxs-lookup"><span data-stu-id="223f4-125">So, it is standard practice to copy and customize several profiles when configuring one or more settings.</span></span>
    >
    ><span data-ttu-id="223f4-126">若要了解有关 MRTK 配置文件及其体系结构的详细信息，请访问[MRTK 文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>)。</span><span class="sxs-lookup"><span data-stu-id="223f4-126">To discover more about MRTK profiles and their architecture, visit the [MRTK documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>).</span></span>

2. <span data-ttu-id="223f4-127">创建默认配置文件的副本以对其进行自定义。</span><span class="sxs-lookup"><span data-stu-id="223f4-127">Create a copy of the default profile to customize it.</span></span> <span data-ttu-id="223f4-128">首先，单击 "**复制 & 自定义**"。</span><span class="sxs-lookup"><span data-stu-id="223f4-128">Start by clicking **Copy & Customize**.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2a.png)

    <span data-ttu-id="223f4-130">这会打开*克隆配置文件*的弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="223f4-130">This will open the *Clone Profile* popup window.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step2b.png)

    <span data-ttu-id="223f4-132">单击 "**克隆**" 创建 MRTK 配置文件的副本。</span><span class="sxs-lookup"><span data-stu-id="223f4-132">Click **Clone** to create a copy of the MRTK profile.</span></span> <span data-ttu-id="223f4-133">使用自己的 MRTK 配置文件副本，现在可以自定义此配置文件中的任何设置。</span><span class="sxs-lookup"><span data-stu-id="223f4-133">With your own copy of the MRTK profile, you now have the ability to customize any settings in this profile.</span></span> <span data-ttu-id="223f4-134">还需要对此配置文件下嵌套的任何其他配置文件重复执行复制和自定义步骤，如后续步骤中所述。</span><span class="sxs-lookup"><span data-stu-id="223f4-134">You will also need to repeat the copy and customize step for any additional profiles nested under this profile as described in the subsequent steps.</span></span>

3. <span data-ttu-id="223f4-135">禁用空间感知网格的可见性。</span><span class="sxs-lookup"><span data-stu-id="223f4-135">Disable the visibility of the spatial awareness mesh.</span></span> <span data-ttu-id="223f4-136">为此，请查找空间感知系统设置，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-136">To do this, find Spatial Awareness system settings as shown in the image below.</span></span> <span data-ttu-id="223f4-137">请确保已选中 "**启用空间感知系统**" 选项。</span><span class="sxs-lookup"><span data-stu-id="223f4-137">Make sure the **Enable Spatial Awareness System** option is checked.</span></span> <span data-ttu-id="223f4-138">单击空间感知系统配置文件右侧的 "**克隆**" 按钮，以使用可自定义的副本替换默认配置文件。</span><span class="sxs-lookup"><span data-stu-id="223f4-138">Click the **Clone** button to the right of the Spatial Awareness System Profile to replace the default profile with a customizable copy.</span></span> <span data-ttu-id="223f4-139">在出现的弹出窗口中，按下的 "**克隆**" 按钮，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-139">In the pop-up window that appears, press the **Clone** button, as shown in the second image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3a.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step3b.png)

4. <span data-ttu-id="223f4-142">创建默认混合现实空间网格观察者的自定义副本。</span><span class="sxs-lookup"><span data-stu-id="223f4-142">Create a custom copy of the Default Mixed Reality Spatial Mesh Observer.</span></span> <span data-ttu-id="223f4-143">单击 "Windows Mixed Reality 空间网格观察器" 旁的向下箭头以查看其他选项。</span><span class="sxs-lookup"><span data-stu-id="223f4-143">Click the down arrow next to Windows Mixed Reality Spatial Mesh Observer to see additional options.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4a.png)

    <span data-ttu-id="223f4-145">在这些选项中，你将看到处于灰色显示状态的默认混合现实空间网格观察程序（不可编辑）。</span><span class="sxs-lookup"><span data-stu-id="223f4-145">In these options, you will see the Default Mixed Reality Spatial Mesh Observer that is greyed-out (not editable).</span></span> <span data-ttu-id="223f4-146">必须将此默认配置文件替换为可自定义的副本，以便能够对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="223f4-146">You must replace this default profile with a customizable copy so you can edit it.</span></span> <span data-ttu-id="223f4-147">如前文所述，单击 "**克隆**" 按钮，然后在显示的弹出窗口中，按下的 "**克隆**" 按钮，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-147">As you did earlier, click the **Clone** button and then, in the pop-up window that appears, press the **Clone** button, as shown in the second image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4b.png)

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step4c.png)

5. <span data-ttu-id="223f4-150">接下来，调整带有“遮挡”字样的显示选项的设置。</span><span class="sxs-lookup"><span data-stu-id="223f4-150">Next, you will adjust the settings for the display option to say “occlusion.”</span></span> <span data-ttu-id="223f4-151">这会使空间映射网格不可见，但仍会隐藏空间映射网格后面的游戏对象（也称为封闭）。</span><span class="sxs-lookup"><span data-stu-id="223f4-151">This makes the spatial mapping mesh invisible, but still hides game objects behind the spatial mapping mesh, also known as occlusion.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-1-step5.png)

    >[!NOTE]
    ><span data-ttu-id="223f4-153">注意：虽然空间映射网格不可见，但仍存在，你可以与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="223f4-153">Note: While the spatial mapping mesh is not visible, it is still present and you can interact with it.</span></span> <span data-ttu-id="223f4-154">空间映射网格后面的任何全息影像（如可见墙后的全息图）都不可见，这是因为封闭设置。</span><span class="sxs-lookup"><span data-stu-id="223f4-154">Any holograms behind the spatial mapping mesh, such as a hologram behind your visible wall, will not be visible because of the occlusion setting.</span></span>

<span data-ttu-id="223f4-155">恭喜你！</span><span class="sxs-lookup"><span data-stu-id="223f4-155">Congratulations!</span></span> <span data-ttu-id="223f4-156">你已了解如何修改 MRTK 配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="223f4-156">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="223f4-157">你知道，若要修改 MRTK 设置，需要创建默认配置文件的副本，以便能够对其进行编辑。</span><span class="sxs-lookup"><span data-stu-id="223f4-157">As you can see, in order to modify MRTK settings you need to create copies of the default profiles so that you can edit them.</span></span> <span data-ttu-id="223f4-158">如果你想要使用新设置创建配置文件，或者可以返回到默认配置文件，则始终拥有默认的配置文件，这是不可编辑的。</span><span class="sxs-lookup"><span data-stu-id="223f4-158">You will always have the default profiles, which are not editable, to go back to if you wanted to create a profile with new settings or you can refer back to the default profiles.</span></span> <span data-ttu-id="223f4-159">可以调整大量的设置。</span><span class="sxs-lookup"><span data-stu-id="223f4-159">There are numerous settings that you can adjust.</span></span> <span data-ttu-id="223f4-160">有关 MRTK 配置文件设置的完整引用，请参阅此处的 MRTK 文档： [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)</span><span class="sxs-lookup"><span data-stu-id="223f4-160">For full reference to MRTK profile settings, refer to the MRTK documentation here: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)</span></span>

### <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="223f4-161">手动跟踪手势和可交互按钮</span><span class="sxs-lookup"><span data-stu-id="223f4-161">Hand Tracking Gestures and Interactable buttons</span></span>

<span data-ttu-id="223f4-162">在本部分中，你将学习如何使用手动跟踪来按 pressable 按钮。</span><span class="sxs-lookup"><span data-stu-id="223f4-162">In this section, you will learn how to use hand tracking to press a pressable button.</span></span>

1. <span data-ttu-id="223f4-163">从 "项目" 文件夹中选择 "资产"。</span><span class="sxs-lookup"><span data-stu-id="223f4-163">Select Assets from the projects folder.</span></span>

2. <span data-ttu-id="223f4-164">在搜索栏中键入 "PressableButtonHoloLens2"。</span><span class="sxs-lookup"><span data-stu-id="223f4-164">Type "PressableButtonHoloLens2" in the search bar.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step2.png)

3. <span data-ttu-id="223f4-166">将名为 "PressableButtonHoloLens2" 的 prefab （由蓝色框表示）拖到层次结构中，并将位置值设置为 x = 0、y = 0 和 z = 0.2，使该按钮位于相机的前方。</span><span class="sxs-lookup"><span data-stu-id="223f4-166">Drag the prefab (represented by a blue box) named "PressableButtonHoloLens2" into your hierarchy and set set the position values to x = 0, y = 0 and z = 0.2 so the button is in front of the camera.</span></span> <span data-ttu-id="223f4-167">（相机定位于原点）。</span><span class="sxs-lookup"><span data-stu-id="223f4-167">(The camera is positioned at origin).</span></span>

    >[!NOTE]
    ><span data-ttu-id="223f4-168">如果收到有关 "导入 TMP Essentials" 的消息，请立即导入它。</span><span class="sxs-lookup"><span data-stu-id="223f4-168">If you get a message about “importing TMP Essentials”, import it at this time.</span></span> <span data-ttu-id="223f4-169">如果你的项目中尚不包含 TMP Essentials，则在导入 TMP Essentials 后可能需要重复此步骤，否则可能不会出现按钮文本。</span><span class="sxs-lookup"><span data-stu-id="223f4-169">If TMP Essentials was not already part of your project, you might need to repeat this step after importing TMP Essentials, otherwise button text may not appear.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step3.png)

4. <span data-ttu-id="223f4-171">将立方体添加到场景。</span><span class="sxs-lookup"><span data-stu-id="223f4-171">Add a cube to the scene.</span></span> <span data-ttu-id="223f4-172">右键单击 "层次结构" 区域，选择一个3D 对象，然后单击 "多维数据集"。</span><span class="sxs-lookup"><span data-stu-id="223f4-172">Right-click on the hierarchy area, select a 3D object, then click on Cube.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6a.png)

    <span data-ttu-id="223f4-174">现在，你的显示画面中应会包含一个立方体。</span><span class="sxs-lookup"><span data-stu-id="223f4-174">Now, a cube should be in your display.</span></span> <span data-ttu-id="223f4-175">它会显得非常大。</span><span class="sxs-lookup"><span data-stu-id="223f4-175">It will appear very large.</span></span> <span data-ttu-id="223f4-176">您可以调整坐标（在层次结构区域中仍选择 Cube 时）以减小大小。</span><span class="sxs-lookup"><span data-stu-id="223f4-176">You can adjust the coordinates (while Cube is still selected in the hierarchy area) to decrease the size.</span></span> <span data-ttu-id="223f4-177">将刻度值设置为 x = 0.02，y = 0.02，z = 0.02。</span><span class="sxs-lookup"><span data-stu-id="223f4-177">Set the scale values to x = 0.02, y = 0.02 and z = 0.02.</span></span> <span data-ttu-id="223f4-178">请确保将多维数据集放在按钮附近，而不是与其重叠。</span><span class="sxs-lookup"><span data-stu-id="223f4-178">Be sure to position the cube in your scene near the button, but not overlapping with it.</span></span> <span data-ttu-id="223f4-179">在下图中，多维数据集的位置为 x = 0、y = 0.4，z = 0.2。</span><span class="sxs-lookup"><span data-stu-id="223f4-179">In the image below, the cube’s position is x = 0, y = 0.4, and z = 0.2.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step6b.png)

    >[!NOTE]
    ><span data-ttu-id="223f4-181">一般情况下，Unity 中的 1 个单位大致相当于现实生活中的 1 米。</span><span class="sxs-lookup"><span data-stu-id="223f4-181">In general, 1 unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="223f4-182">此情况有例外;例如，当对象是缩放对象的子级时。</span><span class="sxs-lookup"><span data-stu-id="223f4-182">There are exceptions to this; for example, when objects are children of scaled objects.</span></span>

5. <span data-ttu-id="223f4-183">选中 "PressableButtonHoloLens2" 游戏对象后，向下滚动到检查器的底部，以找到种不可交互（脚本）组件的 "事件" 部分。</span><span class="sxs-lookup"><span data-stu-id="223f4-183">With the PressableButtonHoloLens2 game object selected, scroll towards the bottom in the Inspector to locate the Events section of the Interactable (Script) component.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step4.png)

6. <span data-ttu-id="223f4-185">我们将修改现有事件，以便在推送时为按钮指定响应事件。</span><span class="sxs-lookup"><span data-stu-id="223f4-185">We will modify the existing event to give the button an event to respond to when pushed.</span></span> <span data-ttu-id="223f4-186">如您所见，事件接收器类型设置为 InteractableOnPressReceiver。</span><span class="sxs-lookup"><span data-stu-id="223f4-186">As you can see, the Event Receiver Type is set to InteractableOnPressReceiver.</span></span> <span data-ttu-id="223f4-187">这样，在跟踪手按下该按钮时，该按钮会响应按键事件。</span><span class="sxs-lookup"><span data-stu-id="223f4-187">This allows the button to respond to a pressed event when a tracked hand presses the button.</span></span> <span data-ttu-id="223f4-188">此时，还应将交互筛选器更改为 "接近" 和 "远"。</span><span class="sxs-lookup"><span data-stu-id="223f4-188">At this point, you should also change the Interaction Filter to Near and Far.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step5.png)

7. <span data-ttu-id="223f4-190">此步骤将立方体设置为在按下按钮时改变颜色。</span><span class="sxs-lookup"><span data-stu-id="223f4-190">In this step you will set up the cube to change color when your button is pressed.</span></span> <span data-ttu-id="223f4-191">选择 "BaseScene" 层次结构中的 "PressableButtonHoloLens2"，并将 "多维数据集游戏" 对象从 BaseScene 层次结构拖到 "仅运行时" 字段，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-191">Select the PressableButtonHoloLens2 in the BaseScene hierarchy and drag the Cube game object from the BaseScene hierarchy into the Runtime Only field as shown in the image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7a.png)

    <span data-ttu-id="223f4-193">单击未显示函数的下拉列表。</span><span class="sxs-lookup"><span data-stu-id="223f4-193">Click the drop-down list that says No Function.</span></span> <span data-ttu-id="223f4-194">选择 "MeshRenderer"，然后选择 "材料材料"。</span><span class="sxs-lookup"><span data-stu-id="223f4-194">Select MeshRenderer, then select Material material.</span></span> <span data-ttu-id="223f4-195">这允许您在按下按钮时更改材料。</span><span class="sxs-lookup"><span data-stu-id="223f4-195">This lets you change the material when the button is pressed.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7b.png)

    <span data-ttu-id="223f4-197">单击 "空白材料" 字段旁边的圆圈，打开 "选择材料" 弹出窗口。</span><span class="sxs-lookup"><span data-stu-id="223f4-197">Click the circle next to the empty material field to open the Select Material popup.</span></span> <span data-ttu-id="223f4-198">MRTK 包括许多要从中进行选择的材料和颜色。</span><span class="sxs-lookup"><span data-stu-id="223f4-198">The MRTK includes many materials and colors to choose from.</span></span> <span data-ttu-id="223f4-199">在此示例中，您将使用通过在弹出搜索栏中键入 "MRTK_Standard" 找到的材料 MRTK_Standard_Cyan。</span><span class="sxs-lookup"><span data-stu-id="223f4-199">For this example, you are going to use the material, MRTK_Standard_Cyan, found by typing in "MRTK_Standard" in the pop-up search bar.</span></span> <span data-ttu-id="223f4-200">选择要填充材料字段的 MRTK_Standard_Cyan 材料。</span><span class="sxs-lookup"><span data-stu-id="223f4-200">Select the MRTK_Standard_Cyan material to populate the material field.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step7c.png)

    <span data-ttu-id="223f4-202">现已设置事件。按下按钮时，立方体会根据指定的材料改变颜色。</span><span class="sxs-lookup"><span data-stu-id="223f4-202">The event is now set so that when the button is pressed, the cube will change color based on the material you specified.</span></span> <span data-ttu-id="223f4-203">在本示例中，立方体将更改为青色。</span><span class="sxs-lookup"><span data-stu-id="223f4-203">In this example, the cube will change to the cyan color.</span></span>

8. <span data-ttu-id="223f4-204">接下来，您将设置 "发布" 操作，以便在发布时，按钮将恢复为其默认颜色。</span><span class="sxs-lookup"><span data-stu-id="223f4-204">Next, you are going to set up the release action so that upon release, the button will go back to its default color.</span></span> <span data-ttu-id="223f4-205">重复上面的步骤7。</span><span class="sxs-lookup"><span data-stu-id="223f4-205">Repeat Step 7, above.</span></span> <span data-ttu-id="223f4-206">但这一次，OnRelease 事件而不是 OnPress MRTK_Standard_LightGray 材料，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-206">However, this time with the OnRelease event instead of the OnPress MRTK_Standard_LightGray material as shown in the image below.</span></span>

    ![MR213_BuildSettings](images/mrlearning-base-ch2-2-step8.png)

    <span data-ttu-id="223f4-208">现在，当按钮被按下时，它将变为新颜色;蓝.</span><span class="sxs-lookup"><span data-stu-id="223f4-208">Now when the button is pressed, it will change to a new color; cyan.</span></span> <span data-ttu-id="223f4-209">当按钮被释放时，它将改回您指定的默认颜色（例如浅灰色）。按屏幕顶部的 "播放" 按钮在编辑器中试用，或将其部署到 HoloLens 2 进行测试。</span><span class="sxs-lookup"><span data-stu-id="223f4-209">When the button is released, it will change back to the default color you specified (e.g., light gray.) Press the Play button on the top of the screen to try it out in the editor or deploy to your HoloLens 2, to test.</span></span> <span data-ttu-id="223f4-210">若要了解有关编辑器内模拟的详细信息（包括手动模拟），请阅读[MRTK 的模拟文档页](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)。</span><span class="sxs-lookup"><span data-stu-id="223f4-210">To learn more about in-editor simulation, including hand simulation, read the [MRTK's simulation documentation page](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>).</span></span>

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="223f4-211">使用 MRTK 的网格对象集合创建按钮面板</span><span class="sxs-lookup"><span data-stu-id="223f4-211">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="223f4-212">在本部分中，你将了解如何使用 MRTK 的 GridObjectCollection 工具自动将多个按钮对齐到巧妙的用户界面。</span><span class="sxs-lookup"><span data-stu-id="223f4-212">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s GridObjectCollection tool.</span></span>

1. <span data-ttu-id="223f4-213">复制前一部分中的按钮，直到有五个按钮。</span><span class="sxs-lookup"><span data-stu-id="223f4-213">Duplicate the button from the previous section until you have five buttons.</span></span> <span data-ttu-id="223f4-214">可以通过多种方法执行此操作：-右键单击按钮，然后单击 "复制"。</span><span class="sxs-lookup"><span data-stu-id="223f4-214">There are several ways to do this: -Right-click on the button, and click Copy.</span></span> <span data-ttu-id="223f4-215">然后，在按钮下向下并再次右键单击，然后单击 "粘贴"。</span><span class="sxs-lookup"><span data-stu-id="223f4-215">Then go down to below the button and right-click again, then click Paste.</span></span>
    <span data-ttu-id="223f4-216">-右键单击按钮，然后单击 "复制"。</span><span class="sxs-lookup"><span data-stu-id="223f4-216">-Right-click on the button and click Duplicate.</span></span>
    <span data-ttu-id="223f4-217">-通过单击多维数据集，然后在键盘上按 Ctrl D 来使用键盘命令。</span><span class="sxs-lookup"><span data-stu-id="223f4-217">-Use the keyboard command by clicking on the cube, and pressing Ctrl D on your keyboard.</span></span>

    <span data-ttu-id="223f4-218">重复此操作，直到有五个按钮;请参阅下图中的五个红色箭头。</span><span class="sxs-lookup"><span data-stu-id="223f4-218">Repeat this until you have five buttons; see the five red arrows in image below.</span></span>

    ![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. <span data-ttu-id="223f4-220">将按钮分组到空的父游戏对象下。</span><span class="sxs-lookup"><span data-stu-id="223f4-220">Group the buttons under an empty parent game object.</span></span> <span data-ttu-id="223f4-221">为了使网格集合中的按钮，需要将按钮分组到公共父对象下。</span><span class="sxs-lookup"><span data-stu-id="223f4-221">In order to have the buttons in the grid collection, you need to group your buttons under a common parent object.</span></span> <span data-ttu-id="223f4-222">右键单击 hiearachy，然后单击 "创建空"。</span><span class="sxs-lookup"><span data-stu-id="223f4-222">Right-click in the hiearachy, and click Create Empty.</span></span> <span data-ttu-id="223f4-223">随后会创建一个新的空游戏对象用于放置所有按钮。</span><span class="sxs-lookup"><span data-stu-id="223f4-223">This creates a new empty game object for you to put all the buttons in.</span></span> <span data-ttu-id="223f4-224">它显示为 "gameObject"。</span><span class="sxs-lookup"><span data-stu-id="223f4-224">It shows up as gameObject.</span></span> <span data-ttu-id="223f4-225">右键单击并将其重命名为 ButtonCollection。</span><span class="sxs-lookup"><span data-stu-id="223f4-225">Right-click and rename it, ButtonCollection.</span></span>

    ![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. <span data-ttu-id="223f4-227">将所有按钮移入新集合，</span><span class="sxs-lookup"><span data-stu-id="223f4-227">Move all the buttons into the new collection.</span></span> <span data-ttu-id="223f4-228">为此，请选择层次结构中的所有五个按钮对象，并将其全部拖动到 ButtonCollection 游戏对象下，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-228">Do this by selecting all five of the button objects in your heirarchy, and drag them all under ButtonCollection game object as shown in the image below.</span></span> <span data-ttu-id="223f4-229">提示：按住 Ctrl 键的同时选择项，选择多个项。</span><span class="sxs-lookup"><span data-stu-id="223f4-229">Tip: select multiple items by holding the Ctrl key while selecting items.</span></span>

    ![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. <span data-ttu-id="223f4-231">将 MRTK 的网格对象集合组件添加到按钮集合。</span><span class="sxs-lookup"><span data-stu-id="223f4-231">Add MRTK’s Grid Object Collection component to the button collection.</span></span> <span data-ttu-id="223f4-232">为此，请选择 "ButtonCollection" 父对象。</span><span class="sxs-lookup"><span data-stu-id="223f4-232">To do this, select the ButtonCollection parent object.</span></span> <span data-ttu-id="223f4-233">从检查器面板中，单击 "添加组件" 按钮。</span><span class="sxs-lookup"><span data-stu-id="223f4-233">From the Inspector panel, click the Add Component button.</span></span> <span data-ttu-id="223f4-234">在搜索栏中搜索 "网格对象集合"，并在列表中显示它时将其选中。</span><span class="sxs-lookup"><span data-stu-id="223f4-234">Search for Grid Object Collection in the search bar, and select it when it appears in the list.</span></span>

    ![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3-step4.png)

    <span data-ttu-id="223f4-236">网格对象集合组件允许您在巧妙的行、列或网格中组织按钮或任何一组对象。</span><span class="sxs-lookup"><span data-stu-id="223f4-236">The Grid Object Collection component lets you organize buttons or any set of objects in a neat row, column, or grid.</span></span> <span data-ttu-id="223f4-237">这是 MRTK 提供的构建基块之一，为你提供了一种快速简单的方法来创建具有吸引力的用户界面。</span><span class="sxs-lookup"><span data-stu-id="223f4-237">This is one of the building blocks provided by the MRTK that gives you a quick and easy way to create enticing user interfaces.</span></span>

5. <span data-ttu-id="223f4-238">配置网格对象集合。</span><span class="sxs-lookup"><span data-stu-id="223f4-238">Configure the grid object collection.</span></span> <span data-ttu-id="223f4-239">若要确保所有按钮都面向用户，请选择 "方向类型"。</span><span class="sxs-lookup"><span data-stu-id="223f4-239">To ensure all the buttons face the user, select Orient Type.</span></span> <span data-ttu-id="223f4-240">然后选择 "正面朝上"，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-240">Then select Face Parent Forward as shown in the image below.</span></span> <span data-ttu-id="223f4-241">接下来，更改单元格大小以设置按钮之间的间距。</span><span class="sxs-lookup"><span data-stu-id="223f4-241">Next, change the cell size to set the space between your buttons.</span></span> <span data-ttu-id="223f4-242">对于单元宽度和单元格高度，从0.05 个0.05 单位开始个单位，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-242">Start with 0.05 units by 0.05 units for the Cell Width and Cell Height, as shown in the image below.</span></span> <span data-ttu-id="223f4-243">请确保 "距离" 设置为0，"行" 设置为1。</span><span class="sxs-lookup"><span data-stu-id="223f4-243">Make sure Distance is set to 0 and Rows is set to 1.</span></span> <span data-ttu-id="223f4-244">单击 "更新集合"。</span><span class="sxs-lookup"><span data-stu-id="223f4-244">Click Update Collection.</span></span> <span data-ttu-id="223f4-245">场景将如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-245">The scene will look similar to the picture below.</span></span>

    ![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3-step5.png)

    >[!NOTE]
    ><span data-ttu-id="223f4-247">根据子对象或父对象的方向，在将来的项目中可能需要以不同的方式调整方向设置。</span><span class="sxs-lookup"><span data-stu-id="223f4-247">Depending on the orientation of the child objects or parent object, you will likely need to adjust the orientation setting differently in future projects.</span></span> <span data-ttu-id="223f4-248">此外，根据集合中对象的大小，可能需要以不同的方式定义“单元格宽度”和“单元格高度”字段。</span><span class="sxs-lookup"><span data-stu-id="223f4-248">The Cell Width and the Cell Height fields may also need to be defined differently, depending on the size of the objects in your collection.</span></span>

### <a name="adding-text-into-your-scene"></a><span data-ttu-id="223f4-249">将文本添加到场景中</span><span class="sxs-lookup"><span data-stu-id="223f4-249">Adding Text into Your Scene</span></span>

<span data-ttu-id="223f4-250">本部分介绍如何将文本添加到混合现实体验以及如何编辑文本。</span><span class="sxs-lookup"><span data-stu-id="223f4-250">In this section, you will learn how to add and edit text to your mixed reality experiences.</span></span> <span data-ttu-id="223f4-251">如果尚未这样做，请按照[此处](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)的说明操作，确保已在 Unity 中启用了 TextMeshPro。</span><span class="sxs-lookup"><span data-stu-id="223f4-251">If you haven’t already, ensure you have TextMeshPro enabled in Unity by following the instructions [here](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation).</span></span>

1. <span data-ttu-id="223f4-252">选择 ButtonCollection 父对象，并右键单击该集合。</span><span class="sxs-lookup"><span data-stu-id="223f4-252">Select the ButtonCollection parent object, and right-click the collection.</span></span> <span data-ttu-id="223f4-253">展开下拉菜单中的 "3D 对象"。</span><span class="sxs-lookup"><span data-stu-id="223f4-253">Expand 3D object in the drop-down menu.</span></span> <span data-ttu-id="223f4-254">然后选择 "TextMeshPro"。</span><span class="sxs-lookup"><span data-stu-id="223f4-254">Then select TextMeshPro - Text.</span></span> <span data-ttu-id="223f4-255">你应在按钮集合下看到一个 TextMeshPro 对象，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-255">You should see a TextMeshPro object under the button collection as shown in the image below.</span></span>

    <span data-ttu-id="223f4-256">![第2课 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![第2课 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span><span class="sxs-lookup"><span data-stu-id="223f4-256">![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG) ![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)</span></span>

2. <span data-ttu-id="223f4-257">若要改善可读性的文本大小和位置，请调整 TextMeshPro 组件中的 "字体大小" 字段以更改字体大小。</span><span class="sxs-lookup"><span data-stu-id="223f4-257">To improve the text size and placement for readability, adjust the Font Size field in the TextMeshPro component to change the size of the font.</span></span> <span data-ttu-id="223f4-258">还需要调整矩形转换位置和缩放比例，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-258">You will also need to adjust the Rect Transform position and scale as shown in the image below.</span></span> <span data-ttu-id="223f4-259">请参阅下面的图像获取用于文本配置的值。</span><span class="sxs-lookup"><span data-stu-id="223f4-259">See the images below for values used for our text configuration.</span></span> <span data-ttu-id="223f4-260">您可以使用这些值作为开始点，进一步提高文本字段的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="223f4-260">Feel free to use these values as a starting point to further improve the size and placement of your text field.</span></span>

    ![第2课 Chapter4 步骤3](images/mrlearning-base-ch2-4-step3.png)

3. <span data-ttu-id="223f4-262">在 "检查器" 面板的 "TextMeshPro" 组件的 "文本" 字段中，键入 "Button Collection Text"，并将对齐属性调整为居中和靠上，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="223f4-262">In the TextMeshPro component’s text field in the Inspector panel, type in "Button Collection Text" and adjust the Alignment properties to be Center and Top, as shown in the image below.</span></span>

    ![第2课 Chapter4 步骤4](images/mrlearning-base-ch2-4-step4.png)

4. <span data-ttu-id="223f4-264">若要修改按钮对象的文本值，请单击任何按钮旁边的箭头将其展开，然后导航到 SeeItSayItLabel 对象。</span><span class="sxs-lookup"><span data-stu-id="223f4-264">To modify the text values on the button objects, click the arrow next to any button to expand it and navigate to the SeeItSayItLabel object.</span></span> <span data-ttu-id="223f4-265">导航到 TextMeshPro，在其中可以根据上述步骤中所述，编辑按钮的文本。</span><span class="sxs-lookup"><span data-stu-id="223f4-265">Navigate to TextMeshPro, where you can edit the text to your buttons as described in the steps above.</span></span>

    ![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a><span data-ttu-id="223f4-267">祝贺</span><span class="sxs-lookup"><span data-stu-id="223f4-267">Congratulations</span></span>

<span data-ttu-id="223f4-268">在本课中，您学习了如何复制、自定义和配置 MRTK 配置文件设置（例如，空间感知网格可见性）。还了解了如何与按钮交互，以便在 HoloLens 2 上使用跟踪的手触发事件。</span><span class="sxs-lookup"><span data-stu-id="223f4-268">In this lesson, you learned how to copy, customize, and configure an MRTK profile setting (i.e., spatial awareness mesh visibility.) You also learned how to interact with a button to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="223f4-269">最后，你已学习了如何使用 Unity 文本网格专业版和 MRTK 的网格对象集合组件创建简单的 UI 接口。</span><span class="sxs-lookup"><span data-stu-id="223f4-269">Finally, you learned how to create a simple UI interface using Unity's Text Mesh Pro and the MRTK's Grid Object Collection component.</span></span>

[<span data-ttu-id="223f4-270">下一课： 4. 放置动态内容并使用 solvers</span><span class="sxs-lookup"><span data-stu-id="223f4-270">Next Lesson: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
