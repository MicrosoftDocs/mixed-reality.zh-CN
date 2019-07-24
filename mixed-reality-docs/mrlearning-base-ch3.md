---
title: MR 学习基础模块 - 动态内容放置和求解器
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 4baee7ba8643f5bb80e0456eb97d915405431654
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387707"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="72255-104">4.放置动态内容并使用 solvers</span><span class="sxs-lookup"><span data-stu-id="72255-104">4. Placing dynamic content and using solvers</span></span>

<span data-ttu-id="72255-105">当全息影像直观地跟随用户并且在物理环境中无缝巧妙地参与互动时，它们在 HoloLens 2 中变得真实生动。</span><span class="sxs-lookup"><span data-stu-id="72255-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="72255-106">在本教程中, 我们将探讨如何使用 MRTK 的可用放置工具 (称为 solvers) 动态放置全息影像, 以解决复杂的空间放置方案。</span><span class="sxs-lookup"><span data-stu-id="72255-106">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as solvers for the way they solve complex spatial placement scenarios.</span></span> <span data-ttu-id="72255-107">在 MRTK 中, solvers 是一种脚本和行为的系统, 用于允许 UI 元素跟随你、用户或场景中的其他游戏对象。</span><span class="sxs-lookup"><span data-stu-id="72255-107">In the MRTK, solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="72255-108">它们还可用于快速贴靠到某个位置，使应用程序更加直观。</span><span class="sxs-lookup"><span data-stu-id="72255-108">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="72255-109">目标</span><span class="sxs-lookup"><span data-stu-id="72255-109">Objectives</span></span>

* <span data-ttu-id="72255-110">介绍 MRTK 的求解器</span><span class="sxs-lookup"><span data-stu-id="72255-110">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="72255-111">使用求解器让一组按钮跟随用户</span><span class="sxs-lookup"><span data-stu-id="72255-111">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="72255-112">使用求解器使游戏对象跟随用户被追踪的双手</span><span class="sxs-lookup"><span data-stu-id="72255-112">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="72255-113">说明</span><span class="sxs-lookup"><span data-stu-id="72255-113">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="72255-114">求解器在 MRTK 中的位置</span><span class="sxs-lookup"><span data-stu-id="72255-114">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="72255-115">要查找项目中的可用求解器，请查看 MRTK SDK 文件夹（MixedRealityToolkit.SDK 文件夹），然后在 utilities 文件夹下，将看到求解器文件夹，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="72255-115">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![求解器](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="72255-117">注意:在本课程中, 我们将只介绍 Orbital 求解器和 RadialView 求解器的实现。</span><span class="sxs-lookup"><span data-stu-id="72255-117">Note: In this lesson we will only go over the implementation of the Orbital solver and the RadialView solver.</span></span> <span data-ttu-id="72255-118">要详细了解 MRTK 中的所有求解器，请访问： https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="72255-118">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="72255-119">使用求解器跟随用户</span><span class="sxs-lookup"><span data-stu-id="72255-119">Use a Solver to Follow the User</span></span>
<span data-ttu-id="72255-120">本章的目标是增强之前创建的按钮集合, 使其遵循用户的注视方向。</span><span class="sxs-lookup"><span data-stu-id="72255-120">The goal of this chapter is to enhance the button collection that was previously created so that it follows the user’s gaze direction.</span></span> <span data-ttu-id="72255-121">在以前版本的 MRTK 和 HoloToolkit 中, 这称为 tagalong 功能。</span><span class="sxs-lookup"><span data-stu-id="72255-121">In previous version of the MRTK and HoloToolkit, this was referred to as a tagalong functionality.</span></span>

1. <span data-ttu-id="72255-122">从上一节课中选择按钮集合父对象。</span><span class="sxs-lookup"><span data-stu-id="72255-122">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="72255-124">在检查器面板中, 单击 "添加组件" 按钮, 然后搜索 "orbital"。</span><span class="sxs-lookup"><span data-stu-id="72255-124">In the Inspector panel, click the Add Component button and search for orbital.</span></span> <span data-ttu-id="72255-125">这时应显示环绕组件。</span><span class="sxs-lookup"><span data-stu-id="72255-125">The orbital component should appear.</span></span> <span data-ttu-id="72255-126">选中它，将环绕组件添加到按钮集合游戏对象。</span><span class="sxs-lookup"><span data-stu-id="72255-126">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="72255-128">注意:添加该组件时，将注意到系统在检查器选项卡中添加了环绕脚本和求解器处理程序脚本，这是必需的组件。</span><span class="sxs-lookup"><span data-stu-id="72255-128">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="72255-129">若要将按钮集合配置为关注用户, 我们需要实现以下调整 (请参阅下图):</span><span class="sxs-lookup"><span data-stu-id="72255-129">In order to configure the button collection to follow the user, we need to implement the following adjustments (refer to the image below):</span></span>
- <span data-ttu-id="72255-130">在 Orbital 脚本中, 将 "方向类型" 下拉列表设置为 "仅偏航"。</span><span class="sxs-lookup"><span data-stu-id="72255-130">In the Orbital script, set the Orientation Type drop-down list to Yaw Only.</span></span> <span data-ttu-id="72255-131">这样，在对象跟随用户时，它只有一个轴在旋转。</span><span class="sxs-lookup"><span data-stu-id="72255-131">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="72255-132">将所有轴上的局部偏移量设置为 0。</span><span class="sxs-lookup"><span data-stu-id="72255-132">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="72255-133">将世界偏移量设置为 x = 0，y = -0.1，z = 0.6。</span><span class="sxs-lookup"><span data-stu-id="72255-133">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="72255-134">这样可以锁定对象的移动，当用户改变高度时，对象在物理环境中保持固定高度，同时仍然可以在用户在环境中移动时跟随用户。</span><span class="sxs-lookup"><span data-stu-id="72255-134">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="72255-135">可以调整这些值以实现广泛的行为。</span><span class="sxs-lookup"><span data-stu-id="72255-135">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="72255-136">对于这种情况, 在用户完全关闭用户的 head 后, 只关注用户的视图, 你可以选择 "对全球偏移使用角度单" 复选框 (注意:此标题可能会在某些屏幕上被截断，如下图所示。）例如，要使对象仅在每隔 90 度时跟随用户一次，请将步进数设置为 4（左侧示例中的绿色箭头标记）。</span><span class="sxs-lookup"><span data-stu-id="72255-136">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the Use Angle Stepping for world offset checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="72255-138">使对象跟随跟踪的手</span><span class="sxs-lookup"><span data-stu-id="72255-138">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="72255-139">在本节中，我们将使用 RadialView 求解器配置先前创建的立方体游戏对象，以跟随用户被追踪的双手。</span><span class="sxs-lookup"><span data-stu-id="72255-139">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="72255-140">在 BaseScene 层次结构中选择立方体对象。</span><span class="sxs-lookup"><span data-stu-id="72255-140">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="72255-141">单击 "检查器" 面板中的 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="72255-141">Click Add Component in the Inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="72255-143">在 "搜索" 框中键入 RadialView, 然后选择 "RadialView" 组件以将其添加到多维数据集中。</span><span class="sxs-lookup"><span data-stu-id="72255-143">Type in RadialView in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="72255-144">求解器处理程序组件也将自动添加到立方体。</span><span class="sxs-lookup"><span data-stu-id="72255-144">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="72255-145">将径向视图更改为不跟随头部，而是跟随左手。</span><span class="sxs-lookup"><span data-stu-id="72255-145">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="72255-146">选择要引用的所跟踪对象旁边的下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="72255-146">Select the dropdown menu next to the Tracked Object to Reference option.</span></span> <span data-ttu-id="72255-147">然后从菜单中选择 "从右到左"。</span><span class="sxs-lookup"><span data-stu-id="72255-147">Then select Hand Joint Left from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="72255-149">选择手关节后，可以选择希望立方体跟随的手的某个部分。</span><span class="sxs-lookup"><span data-stu-id="72255-149">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="72255-150">对于本示例，我们将使用手腕。</span><span class="sxs-lookup"><span data-stu-id="72255-150">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="72255-151">在 "所选的选项" 旁边, 选择下拉菜单, 然后选择 "手腕"。</span><span class="sxs-lookup"><span data-stu-id="72255-151">Next to the option Tracked Hand Joint select the dropdown menu and select Wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="72255-153">将最大和最小距离设置为 0，使立方体与用户的手腕之间没有任何距离。</span><span class="sxs-lookup"><span data-stu-id="72255-153">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="72255-154">设置后，立方体将与手腕完全对齐。</span><span class="sxs-lookup"><span data-stu-id="72255-154">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="72255-155">您还可以调整 "引用方向" 字段以调整多维数据集的方向行为, 例如, 如果您想要允许对象通过将引用方向设置为与被跟踪对象一起旋转来旋转用户的手腕。</span><span class="sxs-lookup"><span data-stu-id="72255-155">You might also adjust the Reference Direction field to adjust the behavior of how the cube is oriented, such as if you want to allow the object to rotate with the user's wrist by setting the reference direction to Orient with Tracked Object.</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="72255-157">祝贺</span><span class="sxs-lookup"><span data-stu-id="72255-157">Congratulations</span></span>
<span data-ttu-id="72255-158">在本教程中, 已学习如何使用 MRTK 的 solvers 让 UI 直观地追随用户。</span><span class="sxs-lookup"><span data-stu-id="72255-158">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="72255-159">你还了解了如何将求解器附加到游戏对象（这里是立方体）以跟随用户被追踪的双手。</span><span class="sxs-lookup"><span data-stu-id="72255-159">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="72255-160">要详细了解上述求解器以及 MRTK 中包含的其他求解器，请访问 [MRTK 求解器文档页面](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)。</span><span class="sxs-lookup"><span data-stu-id="72255-160">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="72255-161">下一课：3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="72255-161">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

