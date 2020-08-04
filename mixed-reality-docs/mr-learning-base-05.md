---
title: 入门教程 - 5. 使用求解器创建动态内容
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 1a5017d8bc18ef239db88ee62cb2b65c77b2ab6f
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376609"
---
# <a name="5-creating-dynamic-content-using-solvers"></a><span data-ttu-id="534c8-105">5.使用求解器创建动态内容</span><span class="sxs-lookup"><span data-stu-id="534c8-105">5. Creating dynamic content using Solvers</span></span>

## <a name="overview"></a><span data-ttu-id="534c8-106">概述</span><span class="sxs-lookup"><span data-stu-id="534c8-106">Overview</span></span>

<span data-ttu-id="534c8-107">本教程探讨如何使用 MRTK 提供的定位工具（求解器）动态放置全息影像，以解算复杂的空间定位场景。</span><span class="sxs-lookup"><span data-stu-id="534c8-107">In this tutorial, you will explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="534c8-108">在 MRTK 中，求解器是一个脚本和行为系统，可让对象跟随你、用户或场景中的其他游戏对象。</span><span class="sxs-lookup"><span data-stu-id="534c8-108">In the MRTK, Solvers are a system of scripts and behaviors used to allow objects to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="534c8-109">它们还可用于贴靠到某些位置，使应用更加直观。</span><span class="sxs-lookup"><span data-stu-id="534c8-109">They can also be used to snap to certain positions, making your app more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="534c8-110">目标</span><span class="sxs-lookup"><span data-stu-id="534c8-110">Objectives</span></span>

* <span data-ttu-id="534c8-111">介绍 MRTK 的解算器</span><span class="sxs-lookup"><span data-stu-id="534c8-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="534c8-112">了解如何使用求解器将用户定向到对象</span><span class="sxs-lookup"><span data-stu-id="534c8-112">Learn how to use Solvers to direct the user to objects</span></span>
* <span data-ttu-id="534c8-113">了解如何使用求解器重新定位对象</span><span class="sxs-lookup"><span data-stu-id="534c8-113">Learn how to use Solvers to reposition objects</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="534c8-114">解算器在 MRTK 中的位置</span><span class="sxs-lookup"><span data-stu-id="534c8-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="534c8-115">MRTK 的解算器位于 MRTK SDK 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="534c8-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="534c8-116">若要在项目中查看可用的求解器，请在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “功能” > “实用工具” > “求解器”     ：</span><span class="sxs-lookup"><span data-stu-id="534c8-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

<span data-ttu-id="534c8-118">本教程将回顾方向指示器求解器和点击放置求解器的实现。</span><span class="sxs-lookup"><span data-stu-id="534c8-118">In this tutorial, we will review the implementation of the Directional Indicator Solver and the Tap To Place Solver.</span></span> <span data-ttu-id="534c8-119">若要详细了解 MRTK 中提供的各个求解器，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[求解器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="534c8-119">To learn more about the full range of Solvers available in the MRTK, you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!NOTE]
> <span data-ttu-id="534c8-120">方向指示器求解器不在上面所述的求解器文件夹中，而是在“资产”>“MRTK”>“SDK”>“实验性”>“功能”>“实用工具”文件夹，因为这是一项实验性功能。</span><span class="sxs-lookup"><span data-stu-id="534c8-120">The Directional Indicator Solver is not located in the Solvers folders referenced above, but in the Assets > MRTK > SDK > Experimental > Features > Utilities folders, because it is an experimental feature.</span></span>

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a><span data-ttu-id="534c8-121">使用方向指示器求解器将用户定向到对象</span><span class="sxs-lookup"><span data-stu-id="534c8-121">Using the Directional Indicator Solver to direct the user to objects</span></span>

<span data-ttu-id="534c8-122">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”文件夹，单击 V 形预制件并将其拖放到“层次结构”窗口中，然后将其“转换”位置设置为 X = 0、Y = 0、Z = 2，使其定位到 RoverExplorer 对象附近    ：</span><span class="sxs-lookup"><span data-stu-id="534c8-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **Chevron** prefab into the Hierarchy window, and set it's Transform **Position** to X = 0, Y = 0, Z = 2 to position it near the RoverExplorer object:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="534c8-124">如果在场景中发现相机或任何其他图标隐藏了对象或让人分心，则可以通过<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">切换调节器</a>（切换到关闭位置）来隐藏这些图标，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="534c8-124">If you find that the camera or any other icons in your scene are hiding the objects or are distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span> <span data-ttu-id="534c8-125">若要详细了解调节器菜单以及如何使用它来优化场景视图，可以参阅 Unity 的<a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">调节器菜单</a>文档。</span><span class="sxs-lookup"><span data-stu-id="534c8-125">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>

<span data-ttu-id="534c8-126">重命名新添加的 V 形对象指示器，然后在“检查器”窗口中，使用“添加组件”按钮添加 DirectionalIndicator 和“方向指示器控制器(脚本)”组件   ：</span><span class="sxs-lookup"><span data-stu-id="534c8-126">Rename the newly added Chevron object **Indicator**, then in the Inspector window, use the **Add Component** button to add the **DirectionalIndicator** and the **Directional Indicator Controller (Script)** component:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="534c8-128">添加求解器（在本例中为 DirectionalIndicator 组件）时，系统会自动添加 SolverHandler 组件，因为求解器需要该组件。</span><span class="sxs-lookup"><span data-stu-id="534c8-128">When you add a Solver, in this case, the DirectionalIndicator component, the SolverHandler component is automatically added because Solvers require it.</span></span>

> [!NOTE]
> <span data-ttu-id="534c8-129">“方向指示器控制器(脚本)”并不是 MRTK 的一部分，而是属于本教程的资源。</span><span class="sxs-lookup"><span data-stu-id="534c8-129">The Directional Indicator Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="534c8-130">按如下所示配置 DirectionalIndicator 和 SolverHandler 组件：</span><span class="sxs-lookup"><span data-stu-id="534c8-130">Configure the DirectionalIndicator and SolverHandler components as follows:</span></span>

* <span data-ttu-id="534c8-131">验证 SolverHandler 组件的“跟踪的目标类型”是否设置为“头部”  </span><span class="sxs-lookup"><span data-stu-id="534c8-131">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="534c8-132">将 RoverExplorer 分配到 DirectionalIndicator 组件的方向目标，具体方法是将其从“层次结构”窗口拖到“无(转换)”字段   </span><span class="sxs-lookup"><span data-stu-id="534c8-132">Assign the **RoverExplorer** to the **DirectionalIndicator** component's **Directional Target** by dragging it from the Hierarchy window into the **None (Transform)** field</span></span>
* <span data-ttu-id="534c8-133">将“视图偏移量”更改为 0.2</span><span class="sxs-lookup"><span data-stu-id="534c8-133">Change the **View Offset** to 0.2</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

<span data-ttu-id="534c8-135">按“播放”按钮进入“游戏”模式，然后在按住鼠标右键的同时在左右移动鼠标以旋转视线方向，此时你会注意到以下情况：</span><span class="sxs-lookup"><span data-stu-id="534c8-135">Press the Play button to enter Game mode, press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="534c8-136">当你将视线从 RoverExplorer 对象移开时，将看到 Indicator 对象，它指向 RoverExplorer 对象</span><span class="sxs-lookup"><span data-stu-id="534c8-136">When you look away from the RoverExplorer object, the Indicator object will appear and point towards the RoverExplorer object</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="534c8-138">如果在“场景”窗口中未看到相机光线，请确保已启用调节器菜单，如上图所示。</span><span class="sxs-lookup"><span data-stu-id="534c8-138">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled, as shown in the image above.</span></span>

> [!TIP]
> <span data-ttu-id="534c8-139">若要了解如何使用编辑器中的输入模拟功能，可以参考 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用编辑器中的手写输入模拟来测试场景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。</span><span class="sxs-lookup"><span data-stu-id="534c8-139">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!TIP]
> <span data-ttu-id="534c8-140">如果计算机有麦克风，你可以使用语音命令“切换诊断”轻松切换游戏窗口中显示的“诊断”面板的活动状态。</span><span class="sxs-lookup"><span data-stu-id="534c8-140">If your computer has a microphone, you can easily toggle the active state of the Diagnostics panel that appears in the Game window by using the speech command "toggle diagnostics."</span></span> <span data-ttu-id="534c8-141">或者，你也可以在“MRTK 配置文件”>“诊断”>“启用诊断系统”中禁用它。</span><span class="sxs-lookup"><span data-stu-id="534c8-141">Alternatively, you can disable it in the MRTK Configuration Profile > Diagnostics > Enable Diagnostics System.</span></span> <span data-ttu-id="534c8-142">但是，我们通常建议你在开发过程中使诊断系统保持活动状态。</span><span class="sxs-lookup"><span data-stu-id="534c8-142">However, it is generally recommended to keep the Diagnostics System active during development.</span></span>

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a><span data-ttu-id="534c8-143">使用点击放置求解器重新定位对象</span><span class="sxs-lookup"><span data-stu-id="534c8-143">Using the Tap to Place Solver to reposition objects</span></span>

<span data-ttu-id="534c8-144">在“层次结构”窗口中依次选择“RoverExplorer”>“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“点击放置(脚本)”组件，并按如下所述配置该组件：  </span><span class="sxs-lookup"><span data-stu-id="534c8-144">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **Tap To Place (Script)** component, and configure it as follows:</span></span>

* <span data-ttu-id="534c8-145">验证 SolverHandler 组件的“跟踪的目标类型”是否设置为“头部”  </span><span class="sxs-lookup"><span data-stu-id="534c8-145">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="534c8-146">选中“保持垂直方向”复选框</span><span class="sxs-lookup"><span data-stu-id="534c8-146">Check the **Keep Orientation Vertical** checkbox</span></span>
* <span data-ttu-id="534c8-147">从“磁性界面” > “元素 0”下拉列表中，取消选中除“空间感知”以外的所有选项  </span><span class="sxs-lookup"><span data-stu-id="534c8-147">From the **Magnetic Surfaces** > **Element 0** dropdown, uncheck all options expect **Spatial Awareness**</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="534c8-149">磁性界面设置可确定放置对象时“点击放置(脚本)”组件可以检测的对象。</span><span class="sxs-lookup"><span data-stu-id="534c8-149">The Magnetic Surfaces setting determines which objects the Tap To Place (Script) component can detect when placing an object.</span></span> <span data-ttu-id="534c8-150">将设置更改为仅“空间感知”后，“点击放置(脚本)”组件将只能在名为“空间感知”的 Unity 层上放置对象的探测器，默认情况下，它是由 HoloLens 生成的空间感知网格。</span><span class="sxs-lookup"><span data-stu-id="534c8-150">By changing the setting to only Spatial Awareness, the Tap To Place (Script) component will only be able to place the Rover on objects on the Unity Layer named Spatial Awareness, which by default is the Spatial Awareness Mesh generated by the HoloLens.</span></span>
>
><span data-ttu-id="534c8-151">若要了解有关层的详细信息，可以参考 Unity 的<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">层</a>文档。</span><span class="sxs-lookup"><span data-stu-id="534c8-151">To learn more about Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Layers</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="534c8-152">如果要在 HoloLens 上测试“点击放置”功能时查看空间感知网格，你可以暂时将空间网格观察程序的“显示”选项设置为“可见”。</span><span class="sxs-lookup"><span data-stu-id="534c8-152">If you want to see the Spatial Awareness Mesh when testing the Tap To Place functionality on your HoloLens, you can temporarily set the Spatial Mesh Observer's Display Option to Visible.</span></span> <span data-ttu-id="534c8-153">有关如何更改“显示”选项的提醒，可参考[更改空间感知显示选项](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)说明。</span><span class="sxs-lookup"><span data-stu-id="534c8-153">For a reminder on how to change the Display Option, you can refer to the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="534c8-154">仍在“层次结构”窗口中选中“RoverAssembly”对象，在“检查器”窗口中找到“On Placing Started ()”事件，然后单击 + 图标以添加新事件 ：</span><span class="sxs-lookup"><span data-stu-id="534c8-154">With the RoverAssembly object still selected in the Hierarchy window, in the Inspector window, locate the **On Placing Started ()** event and click the **+** icon to add a new event:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

<span data-ttu-id="534c8-156">按如下所示配置事件：</span><span class="sxs-lookup"><span data-stu-id="534c8-156">Configure the event as follows:</span></span>

* <span data-ttu-id="534c8-157">将 RoverAssembly 对象指定为“On Placing Started ()”事件的侦听器，具体方法是将该对象从“层次结构”窗口拖到“无(对象)”字段 </span><span class="sxs-lookup"><span data-stu-id="534c8-157">Assign the **RoverAssembly** object as a listener for the On Placing Started () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="534c8-158">在“无函数”下拉列表中，选择“TapToPlace” > “float SurfaceNormalOffset”，以便在触发事件时更新 SurfaceNormalOffset 属性值  </span><span class="sxs-lookup"><span data-stu-id="534c8-158">From the **No Function** dropdown, select **TapToPlace** > **float SurfaceNormalOffset** to update the SurfaceNormalOffset property value when the event is triggered</span></span>
* <span data-ttu-id="534c8-159">验证参数是否设置为 0</span><span class="sxs-lookup"><span data-stu-id="534c8-159">Verify that the argument is set to **0**</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

<span data-ttu-id="534c8-161">在“层次结构”窗口中，右键单击空白区域，然后选择“3D 对象” > “Cube”，创建代表地面的临时对象，并按如下所示配置“转换”组件  ：</span><span class="sxs-lookup"><span data-stu-id="534c8-161">In the Hierarchy window, right-click on an empty spot and select **3D Object** > **Cube**, to create a temporary object representing the ground, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="534c8-162">**位置**：X = 0, Y = -1.65, Z = 6</span><span class="sxs-lookup"><span data-stu-id="534c8-162">**Position**: X = 0, Y = -1.65, Z = 6</span></span>
* <span data-ttu-id="534c8-163">**旋转**：X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="534c8-163">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="534c8-164">**缩放**：X = 10, Y = 0.2, Z = 10</span><span class="sxs-lookup"><span data-stu-id="534c8-164">**Scale**: X = 10, Y = 0.2, Z = 10</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

<span data-ttu-id="534c8-166">仍在“层次结构”窗口中选中临时 Cube，在“检查器”窗口中使用“层”下拉列表来更改 Cube 的层设置，使之仅包含“空间感知”层 ：</span><span class="sxs-lookup"><span data-stu-id="534c8-166">With the temporary Cube still selected in the Hierarchy window, in the Inspector window, use the **Layers** dropdown to change the Cube's Layer setting only to include the **Spatial Awareness** layer:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

<span data-ttu-id="534c8-168">按下“播放”按钮进入“游戏”模式，然后在按住鼠标右键的同时向下移动鼠标，直到视线瞄准 RoverAssembly 对象：</span><span class="sxs-lookup"><span data-stu-id="534c8-168">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse down until the gaze hit's the RoverAssembly object:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

<span data-ttu-id="534c8-170">单击鼠标左键以启动“点击放置”过程：</span><span class="sxs-lookup"><span data-stu-id="534c8-170">Click the left mouse button to start the tap-to-place process:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

<span data-ttu-id="534c8-172">按住鼠标右键的同时左右移动鼠标以旋转视线方向，对定位感到满意后，单击鼠标左键：</span><span class="sxs-lookup"><span data-stu-id="534c8-172">Press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, when you are happy with the placement, click the left mouse button:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

<span data-ttu-id="534c8-174">在“游戏”模式下测试完功能后，右键单击 Cube 对象，然后选择“删除”，以从场景中将其删除：</span><span class="sxs-lookup"><span data-stu-id="534c8-174">Once you are done testing the feature in the Game mode, right-click on the Cube object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a><span data-ttu-id="534c8-176">祝贺</span><span class="sxs-lookup"><span data-stu-id="534c8-176">Congratulations</span></span>

<span data-ttu-id="534c8-177">在本教程中，你学习了如何使用 MRTK 的方向指示器求解器让 UI 元素直观地将用户定向到对象。</span><span class="sxs-lookup"><span data-stu-id="534c8-177">In this tutorial, you learned how to use the MRTK's Directional Indicator Solver to have a UI element intuitively direct the user to objects.</span></span> <span data-ttu-id="534c8-178">还了解了如何使用“点击放置”求解器轻松重新定位对象。</span><span class="sxs-lookup"><span data-stu-id="534c8-178">You also learned how to use the Tap To Place Solver to reposition objects easily.</span></span>

<span data-ttu-id="534c8-179">若要详细了解上述求解器以及 MRTK 中包含的其他求解器，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[求解器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="534c8-179">To learn more about these and other solvers included with the MRTK,  you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="534c8-180">下一教程：6.创建用户界面</span><span class="sxs-lookup"><span data-stu-id="534c8-180">Next Tutorial: 6. Creating user interfaces</span></span>](mr-learning-base-06.md)
