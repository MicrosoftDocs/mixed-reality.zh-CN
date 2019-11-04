---
title: 入门教程-4。 放置动态内容并使用 solvers
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 93fcdcdfb7941f377b2f3f7786368783415b1ef2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438402"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="4e192-105">4. 放置动态内容并使用 solvers</span><span class="sxs-lookup"><span data-stu-id="4e192-105">4. Placing dynamic content and using solvers</span></span>

<span data-ttu-id="4e192-106">当你直观地关注用户并将其放置在物理环境中，使交互方式无缝且精致，就能在 HoloLens 2 中生活。</span><span class="sxs-lookup"><span data-stu-id="4e192-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="4e192-107">在本教程中，我们将探讨如何使用 MRTK 的可用放置工具（称为 solvers）动态放置全息影像，以解决复杂的空间放置方案。</span><span class="sxs-lookup"><span data-stu-id="4e192-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools (known as solvers) to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="4e192-108">在 MRTK 中，solvers 是一种脚本和行为的系统，用于允许 UI 元素跟随你、用户或场景中的其他游戏对象。</span><span class="sxs-lookup"><span data-stu-id="4e192-108">In the MRTK, solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="4e192-109">它们还可用于快速贴靠到某个位置，使应用程序更加直观。</span><span class="sxs-lookup"><span data-stu-id="4e192-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="4e192-110">目标</span><span class="sxs-lookup"><span data-stu-id="4e192-110">Objectives</span></span>

* <span data-ttu-id="4e192-111">介绍 MRTK 的求解器</span><span class="sxs-lookup"><span data-stu-id="4e192-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="4e192-112">使用求解器让一组按钮跟随用户</span><span class="sxs-lookup"><span data-stu-id="4e192-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="4e192-113">使用求解器使游戏对象跟随用户被追踪的双手</span><span class="sxs-lookup"><span data-stu-id="4e192-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="4e192-114">说明</span><span class="sxs-lookup"><span data-stu-id="4e192-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="4e192-115">求解器在 MRTK 中的位置</span><span class="sxs-lookup"><span data-stu-id="4e192-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="4e192-116">若要在项目中查找可用的 solvers，请查看 MRTK SDK 文件夹（MixedRealityToolkit 文件夹）。</span><span class="sxs-lookup"><span data-stu-id="4e192-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder).</span></span> <span data-ttu-id="4e192-117">在 "实用程序" 文件夹下，会显示 solvers 文件夹，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="4e192-117">Under the utilities folder, you will see the solvers folder, as shown in the image below.</span></span>

![求解器](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="4e192-119">注意：在本课中，我们将只回顾 Orbital 求解器和 RadialView 求解器的实现。</span><span class="sxs-lookup"><span data-stu-id="4e192-119">Note: In this lesson, we will only review the implementation of the Orbital solver and the RadialView solver.</span></span> <span data-ttu-id="4e192-120">若要详细了解 MRTK 中可用的 solvers 的详细信息，请访问： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="4e192-120">To learn more about the full range of solvers available in the MRTK, visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="4e192-121">使用求解器跟随用户</span><span class="sxs-lookup"><span data-stu-id="4e192-121">Use a Solver to Follow the User</span></span>
<span data-ttu-id="4e192-122">本章的目标是增强之前创建的按钮集合，使其遵循用户的注视方向。</span><span class="sxs-lookup"><span data-stu-id="4e192-122">The goal of this chapter is to enhance the button collection that was previously created so that it follows the user’s gaze direction.</span></span> <span data-ttu-id="4e192-123">在以前版本的 MRTK 和 HoloToolkit 中，这称为 tagalong 功能。</span><span class="sxs-lookup"><span data-stu-id="4e192-123">In the previous version of the MRTK and HoloToolkit, this was referred to as a tagalong functionality.</span></span>

1. <span data-ttu-id="4e192-124">从上一节课中选择按钮集合父对象。</span><span class="sxs-lookup"><span data-stu-id="4e192-124">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="4e192-126">在检查器面板中，单击 "添加组件" 按钮，然后搜索 "orbital"。</span><span class="sxs-lookup"><span data-stu-id="4e192-126">In the Inspector panel, click the Add Component button and search for orbital.</span></span> <span data-ttu-id="4e192-127">应显示 "Orbital" 组件。</span><span class="sxs-lookup"><span data-stu-id="4e192-127">The Orbital component should appear.</span></span> <span data-ttu-id="4e192-128">选择该按钮，将 Orbital 组件添加到 "按钮集合游戏" 对象。</span><span class="sxs-lookup"><span data-stu-id="4e192-128">Select it to add the Orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="4e192-130">注意：添加 Orbital 组件时，你会注意到，系统还添加了 SolverHandler 组件，这是必需的组件。</span><span class="sxs-lookup"><span data-stu-id="4e192-130">Note: When you add the Orbital component you will notice that the system also adds the SolverHandler component, which is a required component.</span></span> 

3. <span data-ttu-id="4e192-131">若要将按钮集合配置为关注用户，我们需要实现以下调整（请参阅下图）：</span><span class="sxs-lookup"><span data-stu-id="4e192-131">In order to configure the Button Collection to follow the user, we need to implement the following adjustments (refer to the image below):</span></span>
- <span data-ttu-id="4e192-132">在 Orbital 脚本中，将 "方向类型" 下拉列表设置为 "仅偏航"。</span><span class="sxs-lookup"><span data-stu-id="4e192-132">In the Orbital script, set the Orientation Type drop-down list to Yaw Only.</span></span> <span data-ttu-id="4e192-133">这样，在对象跟随用户时，它只有一个轴在旋转。</span><span class="sxs-lookup"><span data-stu-id="4e192-133">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="4e192-134">将所有轴上的局部偏移量设置为 0。</span><span class="sxs-lookup"><span data-stu-id="4e192-134">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="4e192-135">将世界偏移量设置为 x = 0、y =-0.1 和 z = 0.6。</span><span class="sxs-lookup"><span data-stu-id="4e192-135">Set the World Offset to x = 0, y = -0.1, and z = 0.6.</span></span> <span data-ttu-id="4e192-136">这会锁定对象的移动，以便在用户更改高度时，对象将在物理环境中保持为固定高度，同时在用户移动有关环境的情况下仍允许它跟随用户。</span><span class="sxs-lookup"><span data-stu-id="4e192-136">This locks movement of the object so that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="4e192-137">可以调整这些值以实现广泛的行为。</span><span class="sxs-lookup"><span data-stu-id="4e192-137">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="4e192-138">对于这种情况，在用户完全关闭用户的头衔后，只关注用户的视图，你可以选择 "对全球偏移使用角度单" 复选框（注意：在某些屏幕上可能会截断此标题，如下图所示）。例如，若要让对象每隔90度仅关注用户，请设置等于4的步骤数（在下面的示例中，用绿色箭头进行标记）。</span><span class="sxs-lookup"><span data-stu-id="4e192-138">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the Use Angle Stepping For World Offset checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example below).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="4e192-140">使对象跟随跟踪的手</span><span class="sxs-lookup"><span data-stu-id="4e192-140">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="4e192-141">在本部分中，我们将配置先前创建的 Cube 游戏对象，以使用 RadialView 求解器按用户跟踪。</span><span class="sxs-lookup"><span data-stu-id="4e192-141">In this section, we will configure the Cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="4e192-142">选择 BaseScene 层次结构中的多维数据集对象。</span><span class="sxs-lookup"><span data-stu-id="4e192-142">Select the Cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="4e192-143">单击 "检查器" 面板中的 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="4e192-143">Click Add Component in the Inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="4e192-145">在 "搜索" 框中键入 RadialView，然后选择 "RadialView" 组件以将其添加到多维数据集中。</span><span class="sxs-lookup"><span data-stu-id="4e192-145">Type in RadialView in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="4e192-146">SolverHandler 组件还将自动添加到多维数据集中。</span><span class="sxs-lookup"><span data-stu-id="4e192-146">The SolverHandler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="4e192-147">若要将 RadialView 更改为靠左而不是头，请选择要引用的跟踪对象旁边的下拉菜单，然后从菜单中选择 "右侧接点"。</span><span class="sxs-lookup"><span data-stu-id="4e192-147">To change the RadialView to follow the left hand instead of the head, select the dropdown menu next to the Tracked Object to Reference option, then select Hand Joint Left from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="4e192-149">选择手关节后，可以选择希望立方体跟随的手的某个部分。</span><span class="sxs-lookup"><span data-stu-id="4e192-149">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="4e192-150">对于本示例，我们将使用手腕。</span><span class="sxs-lookup"><span data-stu-id="4e192-150">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="4e192-151">在 "选项" 选项旁，选择下拉菜单，然后选择 "手腕"。</span><span class="sxs-lookup"><span data-stu-id="4e192-151">Next to the option Tracked Hand Joint, select the dropdown menu and select Wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="4e192-153">将最大和最小距离设置为 0，使立方体与用户的手腕之间没有任何距离。</span><span class="sxs-lookup"><span data-stu-id="4e192-153">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="4e192-154">设置后，立方体将与手腕完全对齐。</span><span class="sxs-lookup"><span data-stu-id="4e192-154">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="4e192-155">您还可以调整 "引用方向" 字段以调整多维数据集的方向行为，例如，如果您想要允许对象通过将引用方向设置为与被跟踪对象一起旋转来旋转用户的手腕。</span><span class="sxs-lookup"><span data-stu-id="4e192-155">You might also adjust the Reference Direction field to adjust the behavior of how the cube is oriented, such as if you want to allow the object to rotate with the user's wrist by setting the Reference Direction to Orient with Tracked Object.</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a><span data-ttu-id="4e192-157">祝贺</span><span class="sxs-lookup"><span data-stu-id="4e192-157">Congratulations</span></span>
<span data-ttu-id="4e192-158">在本教程中，已学习如何使用 MRTK 的 solvers 让 UI 直观地追随用户。</span><span class="sxs-lookup"><span data-stu-id="4e192-158">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="4e192-159">你还了解了如何将求解器附加到游戏对象（这里是立方体）以跟随用户被追踪的双手。</span><span class="sxs-lookup"><span data-stu-id="4e192-159">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="4e192-160">要详细了解上述求解器以及 MRTK 中包含的其他求解器，请访问 [MRTK 求解器文档页面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。</span><span class="sxs-lookup"><span data-stu-id="4e192-160">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="4e192-161">下一课： 5. 与三维对象交互</span><span class="sxs-lookup"><span data-stu-id="4e192-161">Next Lesson: 5.    Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)

