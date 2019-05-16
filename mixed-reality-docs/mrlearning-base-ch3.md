---
title: MR 学习基本模块的动态内容的位置和求解器
description: 完成此课程以了解如何在混合的现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity 中，教程，hololens 混合的现实
ms.openlocfilehash: 04ed2217c473c5649c1850fcc757d866e23b9b56
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730893"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a><span data-ttu-id="ac970-104">MR 学习基本模块的动态内容的位置和求解器</span><span class="sxs-lookup"><span data-stu-id="ac970-104">MR Learning Base Module - Dynamic Content Placement and Solvers</span></span>

<span data-ttu-id="ac970-105">全息来自生活 HoloLens 2 中，在直观的用户操作和放置在使交互，无缝且简洁的方式中的物理环境时。</span><span class="sxs-lookup"><span data-stu-id="ac970-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="ac970-106">在第 3 课，我们将探讨方法可以动态地将全息使用 MRTK 的可用布局工具，称为"求解器。"</span><span class="sxs-lookup"><span data-stu-id="ac970-106">In Lesson 3, we will explore ways to dynamically place holograms using the MRTK’s available placement tools, known as "solvers."</span></span> <span data-ttu-id="ac970-107">它们被称为"求解器"，它们解决复杂的空间放置算法的方式。</span><span class="sxs-lookup"><span data-stu-id="ac970-107">They are known as "solvers" for the way they solve complex spatial placement algorithms.</span></span> <span data-ttu-id="ac970-108">在 MRTK，求解器是系统的脚本和我们使用能够允许 UI 元素跟随你，用户或其他场景中的游戏对象的行为。</span><span class="sxs-lookup"><span data-stu-id="ac970-108">In the MRTK, solvers are a system of scripts and behaviors that we use to be able to allow UI elements to follow you, the user or other game objects in the scene.</span></span> <span data-ttu-id="ac970-109">它们还可用来对齐到特定位置快速，从而使您的应用程序更直观。</span><span class="sxs-lookup"><span data-stu-id="ac970-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="ac970-110">目标</span><span class="sxs-lookup"><span data-stu-id="ac970-110">Objectives</span></span>

* <span data-ttu-id="ac970-111">引入 MRTK 求解器</span><span class="sxs-lookup"><span data-stu-id="ac970-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="ac970-112">使用求解器具有一组按钮的用户操作</span><span class="sxs-lookup"><span data-stu-id="ac970-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="ac970-113">使用求解器将使游戏对象按照用户的手中跟踪</span><span class="sxs-lookup"><span data-stu-id="ac970-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="ac970-114">说明</span><span class="sxs-lookup"><span data-stu-id="ac970-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="ac970-115">在 MRTK 求解器的位置</span><span class="sxs-lookup"><span data-stu-id="ac970-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="ac970-116">要在项目中查找可用求解器，请检查 MRTK SDK 文件夹 （MixedRealityToolkit.SDK 文件夹中），然后在 utilities 文件夹中会求解器文件夹中，如下图中所示。</span><span class="sxs-lookup"><span data-stu-id="ac970-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![求解器](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="ac970-118">注意：在本课程中我们只会通过"绕"解算器和"RadialView"解算器的实现。</span><span class="sxs-lookup"><span data-stu-id="ac970-118">Note: In this lesson we will only go over implementation of the "Orbital" solver and the "RadialView" solver.</span></span> <span data-ttu-id="ac970-119">若要了解有关推出 MRTK 求解器的完整范围的详细信息，请访问： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="ac970-119">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="ac970-120">使用解算器的用户操作</span><span class="sxs-lookup"><span data-stu-id="ac970-120">Use a Solver to Follow the User</span></span>
<span data-ttu-id="ac970-121">本章旨在增强我们之前创建，以便它遵循用户的视线移动方向的按钮集合。</span><span class="sxs-lookup"><span data-stu-id="ac970-121">The goal of this chapter is to enhance the button collection we previously created such that it follows the user’s gaze direction.</span></span> <span data-ttu-id="ac970-122">在以前版本的 MRTK 和 HoloToolkit，这被称为"taglong"功能。</span><span class="sxs-lookup"><span data-stu-id="ac970-122">In previous version of the MRTK and HoloToolkit, this was referred to as a "taglong" functionality.</span></span>

1. <span data-ttu-id="ac970-123">从上一课中选择按钮集合的父对象。</span><span class="sxs-lookup"><span data-stu-id="ac970-123">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="ac970-125">在检查器窗格中，单击"添加组件"按钮并搜索"绕。"</span><span class="sxs-lookup"><span data-stu-id="ac970-125">In the inspector panel, click the "add component" button and search for "orbital."</span></span> <span data-ttu-id="ac970-126">绕组件应显示。</span><span class="sxs-lookup"><span data-stu-id="ac970-126">The orbital component should appear.</span></span> <span data-ttu-id="ac970-127">选择它以将绕组件添加到按钮集合游戏对象。</span><span class="sxs-lookup"><span data-stu-id="ac970-127">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 第 2 章 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="ac970-129">注意：添加组件时你会注意到系统中检查器选项卡上，这是必需的组件添加绕脚本和解算器处理程序脚本。</span><span class="sxs-lookup"><span data-stu-id="ac970-129">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="ac970-130">若要配置的按钮集合的用户操作，我们需要实现以下调整 （另请参阅下图所示）：</span><span class="sxs-lookup"><span data-stu-id="ac970-130">In order to configure the button collection to follow the user, we need to implement the following adjustments (please also refer to the image below):</span></span>
- <span data-ttu-id="ac970-131">在绕脚本中，将设置为"仅偏航。""方向类型"下拉列表</span><span class="sxs-lookup"><span data-stu-id="ac970-131">In the Orbital script, set the "orientation type" drop-down list to "Yaw Only."</span></span> <span data-ttu-id="ac970-132">这样就使该对象，只有一个轴旋转，它如下所示的用户。</span><span class="sxs-lookup"><span data-stu-id="ac970-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="ac970-133">设置为 0 的所有轴上的本地偏移量。</span><span class="sxs-lookup"><span data-stu-id="ac970-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="ac970-134">设置世界偏移量为 x = 0，y =-0.1 和 z = 0.6。</span><span class="sxs-lookup"><span data-stu-id="ac970-134">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="ac970-135">这将锁定对象的移动，以便当用户更改高度，该对象将始终保持固定高度在物理环境中，同时仍允许其用户在将移动有关环境的用户操作。</span><span class="sxs-lookup"><span data-stu-id="ac970-135">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="ac970-136">这些值进行调整，以实现 wade 行为范围之内。</span><span class="sxs-lookup"><span data-stu-id="ac970-136">These values may be adjusted to achieve a wade range of behaviors.</span></span>
- <span data-ttu-id="ac970-137">对于以下行为，凭此按钮仅按照用户的视图后在用户打开他或她头保持足够距离，可以选择"使用角度单步执行的全局偏移量"复选框 (请注意：此标题可能会被截断某些在屏幕上，因为它是在下图中。）例如，如果希望仅每隔 90 度的用户操作的对象，请将步骤数设置为 4 （由左侧的示例中的绿色箭头标记）。</span><span class="sxs-lookup"><span data-stu-id="ac970-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the "Use Angle Stepping for world offset" checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="ac970-139">使对象能够按照跟踪的手</span><span class="sxs-lookup"><span data-stu-id="ac970-139">Enabling Objects to Follow Tracked Hands</span></span>

<span data-ttu-id="ac970-140">在本部分中，我们将配置以前创建遵循使用 RadialView 解算器的用户的被跟踪的手的多维数据集游戏对象。</span><span class="sxs-lookup"><span data-stu-id="ac970-140">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="ac970-141">BaseScene 层次结构中选择多维数据集对象。</span><span class="sxs-lookup"><span data-stu-id="ac970-141">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="ac970-142">单击检查器面板中的"添加组件"。</span><span class="sxs-lookup"><span data-stu-id="ac970-142">Click "add component" in the inspector panel.</span></span> 

![Lesson3 第 3 章 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="ac970-144">在搜索框中键入"RadialView"并选择要将其添加到多维数据集的 RadialView 组件。</span><span class="sxs-lookup"><span data-stu-id="ac970-144">Type in "RadialView" in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="ac970-145">解算器处理程序组件将也会自动添加到多维数据集。</span><span class="sxs-lookup"><span data-stu-id="ac970-145">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="ac970-146">更改径向视图以不遵循头，但按照左侧显示。</span><span class="sxs-lookup"><span data-stu-id="ac970-146">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="ac970-147">选择"跟踪对象，以引用"选项旁边的下拉列表菜单。</span><span class="sxs-lookup"><span data-stu-id="ac970-147">Select the dropdown menu next to the "tracked object to reference" option.</span></span> <span data-ttu-id="ac970-148">然后，从菜单选择"将剩余的联合"。</span><span class="sxs-lookup"><span data-stu-id="ac970-148">Then select "hand joint left" from the menu.</span></span>

![Lesson3 第 3 章 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="ac970-150">一旦您选择现有联合，可以选择希望多维数据集遵循手形图标的哪个部分。</span><span class="sxs-lookup"><span data-stu-id="ac970-150">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="ac970-151">对于此示例中，我们将使用手腕。</span><span class="sxs-lookup"><span data-stu-id="ac970-151">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="ac970-152">选项旁边"跟踪的手联合"选择下拉列表菜单，然后选择手腕。</span><span class="sxs-lookup"><span data-stu-id="ac970-152">Next to the option "tracked hand joint" select the dropdown menu and select wrist.</span></span> 

![Lesson3 第 3 章 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="ac970-154">设置为 0 的最大和最小距离，以使多维数据集不具有任何它与用户的手腕之间的距离。</span><span class="sxs-lookup"><span data-stu-id="ac970-154">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="ac970-155">完成设置后，该多维数据集将是完全对齐手腕。</span><span class="sxs-lookup"><span data-stu-id="ac970-155">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="ac970-156">您还可以调整"引用方向"字段以调整的方式在多维数据集中的方向 （例如，如果你想要允许的对象要随用户的手腕旋转，请将"定位与跟踪对象"引用方向） 的行为</span><span class="sxs-lookup"><span data-stu-id="ac970-156">You may also adjust the "Reference Direction" field to adjust the behavior of how the cube is oriented (e.g., if you would like to allow the object to rotate with the user's wrist, set the reference direction to "Orient with Tracked Object")</span></span>

![Lesson3 第 3 章 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="ac970-158">恭喜 ！</span><span class="sxs-lookup"><span data-stu-id="ac970-158">Congratulations</span></span>
<span data-ttu-id="ac970-159">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="ac970-159">Congratulations!</span></span> <span data-ttu-id="ac970-160">在本课程中，您学习了如何使用 MRTK 求解器具有直观的用户操作的用户界面。</span><span class="sxs-lookup"><span data-stu-id="ac970-160">In this lesson, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="ac970-161">您还学习了如何将解算器附加到游戏对象 （即，多维数据集），从而按照用户的被跟踪的手。</span><span class="sxs-lookup"><span data-stu-id="ac970-161">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="ac970-162">若要了解有关这些和其他 MRTK 中包含的求解器的详细信息，可随意访问[MRTK 求解器文档页](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。</span><span class="sxs-lookup"><span data-stu-id="ac970-162">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="ac970-163">下一课：三维对象交互</span><span class="sxs-lookup"><span data-stu-id="ac970-163">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

