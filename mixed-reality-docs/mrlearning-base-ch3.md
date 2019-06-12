---
title: MR 学习基础模块 - 动态内容放置和求解器
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270402"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a><span data-ttu-id="0df2e-104">MR 学习基础模块 - 动态内容放置和求解器</span><span class="sxs-lookup"><span data-stu-id="0df2e-104">MR Learning Base Module - Dynamic Content Placement and Solvers</span></span>

<span data-ttu-id="0df2e-105">当全息影像直观地跟随用户并且在物理环境中无缝巧妙地参与互动时，它们在 HoloLens 2 中变得真实生动。</span><span class="sxs-lookup"><span data-stu-id="0df2e-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="0df2e-106">在第 3 课中，我们将探索使用 MRTK 的可用放置工具（称为“求解器”）动态放置全息影像的方法。</span><span class="sxs-lookup"><span data-stu-id="0df2e-106">In Lesson 3, we will explore ways to dynamically place holograms using the MRTK’s available placement tools, known as "solvers."</span></span> <span data-ttu-id="0df2e-107">它们被称为“求解器”，用于解决复杂空间放置算法的方式。</span><span class="sxs-lookup"><span data-stu-id="0df2e-107">They are known as "solvers" for the way they solve complex spatial placement algorithms.</span></span> <span data-ttu-id="0df2e-108">在 MRTK 中，求解器是一个脚本和行为系统，我们使用它来允许 UI 元素跟随你、用户或场景中的其他游戏对象。</span><span class="sxs-lookup"><span data-stu-id="0df2e-108">In the MRTK, solvers are a system of scripts and behaviors that we use to be able to allow UI elements to follow you, the user or other game objects in the scene.</span></span> <span data-ttu-id="0df2e-109">它们还可用于快速贴靠到某个位置，使应用程序更加直观。</span><span class="sxs-lookup"><span data-stu-id="0df2e-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="0df2e-110">目标</span><span class="sxs-lookup"><span data-stu-id="0df2e-110">Objectives</span></span>

* <span data-ttu-id="0df2e-111">介绍 MRTK 的求解器</span><span class="sxs-lookup"><span data-stu-id="0df2e-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="0df2e-112">使用求解器让一组按钮跟随用户</span><span class="sxs-lookup"><span data-stu-id="0df2e-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="0df2e-113">使用求解器使游戏对象跟随用户被追踪的双手</span><span class="sxs-lookup"><span data-stu-id="0df2e-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="0df2e-114">说明</span><span class="sxs-lookup"><span data-stu-id="0df2e-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="0df2e-115">求解器在 MRTK 中的位置</span><span class="sxs-lookup"><span data-stu-id="0df2e-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="0df2e-116">要查找项目中的可用求解器，请查看 MRTK SDK 文件夹（MixedRealityToolkit.SDK 文件夹），然后在 utilities 文件夹下，将看到求解器文件夹，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="0df2e-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![求解器](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="0df2e-118">注意：在本课中，我们将仅讨论“Orbital”求解器和“RadialView”求解器的实现。</span><span class="sxs-lookup"><span data-stu-id="0df2e-118">Note: In this lesson we will only go over implementation of the "Orbital" solver and the "RadialView" solver.</span></span> <span data-ttu-id="0df2e-119">要详细了解 MRTK 中的所有求解器，请访问： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="0df2e-119">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="0df2e-120">使用求解器跟随用户</span><span class="sxs-lookup"><span data-stu-id="0df2e-120">Use a Solver to Follow the User</span></span>
<span data-ttu-id="0df2e-121">本章的目标是增强我们之前创建的按钮集合，使其跟随用户的凝视方向。</span><span class="sxs-lookup"><span data-stu-id="0df2e-121">The goal of this chapter is to enhance the button collection we previously created such that it follows the user’s gaze direction.</span></span> <span data-ttu-id="0df2e-122">在以前版本的 MRTK 和 HoloToolkit 中，这被称为“taglong”功能。</span><span class="sxs-lookup"><span data-stu-id="0df2e-122">In previous version of the MRTK and HoloToolkit, this was referred to as a "taglong" functionality.</span></span>

1. <span data-ttu-id="0df2e-123">从上一节课中选择按钮集合父对象。</span><span class="sxs-lookup"><span data-stu-id="0df2e-123">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="0df2e-125">在检查器面板中单击“添加组件”按钮并搜索“orbital”。</span><span class="sxs-lookup"><span data-stu-id="0df2e-125">In the inspector panel, click the "add component" button and search for "orbital."</span></span> <span data-ttu-id="0df2e-126">这时应显示环绕组件。</span><span class="sxs-lookup"><span data-stu-id="0df2e-126">The orbital component should appear.</span></span> <span data-ttu-id="0df2e-127">选中它，将环绕组件添加到按钮集合游戏对象。</span><span class="sxs-lookup"><span data-stu-id="0df2e-127">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="0df2e-129">注意：添加该组件时，将注意到系统在检查器选项卡中添加了环绕脚本和求解器处理程序脚本，这是必需的组件。</span><span class="sxs-lookup"><span data-stu-id="0df2e-129">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="0df2e-130">为了配置按钮集合以跟随用户，我们需要实现以下调整（请参考下图）：</span><span class="sxs-lookup"><span data-stu-id="0df2e-130">In order to configure the button collection to follow the user, we need to implement the following adjustments (please also refer to the image below):</span></span>
- <span data-ttu-id="0df2e-131">在环绕脚本中，将“方向类型”下拉列表设置为“仅限偏航”。</span><span class="sxs-lookup"><span data-stu-id="0df2e-131">In the Orbital script, set the "orientation type" drop-down list to "Yaw Only."</span></span> <span data-ttu-id="0df2e-132">这样，在对象跟随用户时，它只有一个轴在旋转。</span><span class="sxs-lookup"><span data-stu-id="0df2e-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="0df2e-133">将所有轴上的局部偏移量设置为 0。</span><span class="sxs-lookup"><span data-stu-id="0df2e-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="0df2e-134">将世界偏移量设置为 x = 0，y = -0.1，z = 0.6。</span><span class="sxs-lookup"><span data-stu-id="0df2e-134">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="0df2e-135">这样可以锁定对象的移动，当用户改变高度时，对象在物理环境中保持固定高度，同时仍然可以在用户在环境中移动时跟随用户。</span><span class="sxs-lookup"><span data-stu-id="0df2e-135">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="0df2e-136">可以调整这些值以实现广泛的行为。</span><span class="sxs-lookup"><span data-stu-id="0df2e-136">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="0df2e-137">如需获得某种跟随行为，通过该行为，按钮仅在用户头部转动幅度足够大时才跟随用户的视野，则可以选择“对世界偏移量使用角度步进”复选框（注意：此标题可能会在某些屏幕上被截断，如下图所示。）例如，要使对象仅在每隔 90 度时跟随用户一次，请将步进数设置为 4（左侧示例中的绿色箭头标记）。</span><span class="sxs-lookup"><span data-stu-id="0df2e-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the "Use Angle Stepping for world offset" checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="0df2e-139">使对象能够跟随被追踪的双手</span><span class="sxs-lookup"><span data-stu-id="0df2e-139">Enabling Objects to Follow Tracked Hands</span></span>

<span data-ttu-id="0df2e-140">在本节中，我们将使用 RadialView 求解器配置先前创建的立方体游戏对象，以跟随用户被追踪的双手。</span><span class="sxs-lookup"><span data-stu-id="0df2e-140">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="0df2e-141">在 BaseScene 层次结构中选择立方体对象。</span><span class="sxs-lookup"><span data-stu-id="0df2e-141">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="0df2e-142">在检查器面板中，单击“添加组件”。</span><span class="sxs-lookup"><span data-stu-id="0df2e-142">Click "add component" in the inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="0df2e-144">在搜索框中键入"RadialView"并选择要将其添加到立方体的 RadialView 组件。</span><span class="sxs-lookup"><span data-stu-id="0df2e-144">Type in "RadialView" in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="0df2e-145">求解器处理程序组件也将自动添加到立方体。</span><span class="sxs-lookup"><span data-stu-id="0df2e-145">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="0df2e-146">将径向视图更改为不跟随头部，而是跟随左手。</span><span class="sxs-lookup"><span data-stu-id="0df2e-146">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="0df2e-147">选择“要参考的被追踪对象”选项旁边的下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="0df2e-147">Select the dropdown menu next to the "tracked object to reference" option.</span></span> <span data-ttu-id="0df2e-148">然后从菜单中选择“左手关节”。</span><span class="sxs-lookup"><span data-stu-id="0df2e-148">Then select "hand joint left" from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="0df2e-150">选择手关节后，可以选择希望立方体跟随的手的某个部分。</span><span class="sxs-lookup"><span data-stu-id="0df2e-150">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="0df2e-151">对于本示例，我们将使用手腕。</span><span class="sxs-lookup"><span data-stu-id="0df2e-151">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="0df2e-152">在“被追踪的手关节”选项旁边，选择下拉菜单并选择手腕。</span><span class="sxs-lookup"><span data-stu-id="0df2e-152">Next to the option "tracked hand joint" select the dropdown menu and select wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="0df2e-154">将最大和最小距离设置为 0，使立方体与用户的手腕之间没有任何距离。</span><span class="sxs-lookup"><span data-stu-id="0df2e-154">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="0df2e-155">设置后，立方体将与手腕完全对齐。</span><span class="sxs-lookup"><span data-stu-id="0df2e-155">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="0df2e-156">还可以调整“参考方向”字段以调整立方体的定向行为（例如，如果希望对象与用户的手腕一起旋转，请将参考方向设置为“方向跟随被追踪的对象”）</span><span class="sxs-lookup"><span data-stu-id="0df2e-156">You may also adjust the "Reference Direction" field to adjust the behavior of how the cube is oriented (e.g., if you would like to allow the object to rotate with the user's wrist, set the reference direction to "Orient with Tracked Object")</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="0df2e-158">祝贺你</span><span class="sxs-lookup"><span data-stu-id="0df2e-158">Congratulations</span></span>
<span data-ttu-id="0df2e-159">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="0df2e-159">Congratulations!</span></span> <span data-ttu-id="0df2e-160">在本课程中，你了解了如何使用 MRTK 的求解器让 UI 直观地跟随用户。</span><span class="sxs-lookup"><span data-stu-id="0df2e-160">In this lesson, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="0df2e-161">你还了解了如何将求解器附加到游戏对象（这里是立方体）以跟随用户被追踪的双手。</span><span class="sxs-lookup"><span data-stu-id="0df2e-161">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="0df2e-162">要详细了解上述求解器以及 MRTK 中包含的其他求解器，请访问 [MRTK 求解器文档页面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。</span><span class="sxs-lookup"><span data-stu-id="0df2e-162">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="0df2e-163">下一课：3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="0df2e-163">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

