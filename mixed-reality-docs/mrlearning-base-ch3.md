---
title: 入门教程-4。 放置动态内容并使用 solvers
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 5463f363291790fd5e5d76ffa322a61ca7bf8e31
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553860"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="a9855-105">4. 放置动态内容并使用 Solvers</span><span class="sxs-lookup"><span data-stu-id="a9855-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="a9855-106">当你直观地关注用户并将其放置在物理环境中，使交互方式无缝且精致，就能在 HoloLens 2 中生活。</span><span class="sxs-lookup"><span data-stu-id="a9855-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="a9855-107">在本教程中，我们将探讨如何使用 MRTK 的可用放置工具（称为 Solvers）动态放置全息影像，以解决复杂的空间放置方案。</span><span class="sxs-lookup"><span data-stu-id="a9855-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="a9855-108">在 MRTK 中，Solvers 是一种脚本和行为的系统，用于允许 UI 元素跟随你、用户或场景中的其他游戏对象。</span><span class="sxs-lookup"><span data-stu-id="a9855-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="a9855-109">它们还可用于快速贴靠到某个位置，使应用程序更加直观。</span><span class="sxs-lookup"><span data-stu-id="a9855-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="a9855-110">目标</span><span class="sxs-lookup"><span data-stu-id="a9855-110">Objectives</span></span>

* <span data-ttu-id="a9855-111">介绍 MRTK 的 Solvers</span><span class="sxs-lookup"><span data-stu-id="a9855-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="a9855-112">使用 Solvers 对用户执行按钮的集合</span><span class="sxs-lookup"><span data-stu-id="a9855-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="a9855-113">使用 Solvers 使游戏对象跟随用户的跟踪</span><span class="sxs-lookup"><span data-stu-id="a9855-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="a9855-114">MRTK 中 Solvers 的位置</span><span class="sxs-lookup"><span data-stu-id="a9855-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="a9855-115">MRTK 的 Solvers 位于 MRTK SDK 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="a9855-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="a9855-116">若要在项目中查看可用的 Solvers，请在 "项目" 窗口中，导航到 "**资产**" > **MixedRealityToolkit** > **功能**" > **实用工具**" > **Solvers**：</span><span class="sxs-lookup"><span data-stu-id="a9855-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="a9855-118">在本教程中，我们将回顾 Orbital 求解器和径向视图规划求解的实现。</span><span class="sxs-lookup"><span data-stu-id="a9855-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="a9855-119">若要详细了解 MRTK 中可用的 Solvers 的详细信息，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="a9855-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="a9855-120">使用规划求解来追随用户</span><span class="sxs-lookup"><span data-stu-id="a9855-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="a9855-121">在本部分中，您将增强在上一教程中创建的按钮集合，使其遵循用户的注视方向。</span><span class="sxs-lookup"><span data-stu-id="a9855-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user’s gaze direction.</span></span> <span data-ttu-id="a9855-122">此外，您还将配置规划求解，使按钮集合始终为：</span><span class="sxs-lookup"><span data-stu-id="a9855-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="a9855-123">与用户的阅读方向平行旋转，适用于自然从左到右阅读</span><span class="sxs-lookup"><span data-stu-id="a9855-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="a9855-124">置于稍微低于用户的 "注视" 方向，因此它不会阻碍您稍后将在本教程中添加的其他对象</span><span class="sxs-lookup"><span data-stu-id="a9855-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="a9855-125">在用户中定位大约一半的 arm 长度，因此可以轻松地按下按钮</span><span class="sxs-lookup"><span data-stu-id="a9855-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="a9855-126">为此，你将使用**Orbital 求解**器，它将对象锁定到指定的位置，并与所引用的对象偏移。</span><span class="sxs-lookup"><span data-stu-id="a9855-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="a9855-127">1. 添加 Orbital 求解器</span><span class="sxs-lookup"><span data-stu-id="a9855-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="a9855-128">在 "层次结构" 窗口中，选择 " **ButtonCollection** " 对象，然后在 "检查器" 窗口中，使用 "**添加组件**" 按钮将**Orbital （脚本）** 组件添加到 ButtonCollection 对象。</span><span class="sxs-lookup"><span data-stu-id="a9855-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="a9855-129">添加规划求解（在本例中为 Orbital （Script）组件）时，将自动添加 "规划求解处理程序（脚本）" 组件，因为它是求解器所必需的。</span><span class="sxs-lookup"><span data-stu-id="a9855-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="a9855-130">2. 配置 Orbital 求解器</span><span class="sxs-lookup"><span data-stu-id="a9855-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="a9855-131">配置**规划求解处理程序（脚本）** 组件：</span><span class="sxs-lookup"><span data-stu-id="a9855-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="a9855-132">验证**跟踪的目标类型**是否设置为**Head**</span><span class="sxs-lookup"><span data-stu-id="a9855-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="a9855-133">配置**Orbital （脚本）** 组件：</span><span class="sxs-lookup"><span data-stu-id="a9855-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="a9855-134">验证是否已将 "**方向类型**" 设置为 "**跟随跟踪的对象**"</span><span class="sxs-lookup"><span data-stu-id="a9855-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="a9855-135">将**局部偏移量**重置为 X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="a9855-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="a9855-136">将**世界偏移量**更改为 X = 0，Y =-0.4，Z = 0。3</span><span class="sxs-lookup"><span data-stu-id="a9855-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="a9855-138">3. 使用编辑器内模拟测试 Orbital 求解器</span><span class="sxs-lookup"><span data-stu-id="a9855-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="a9855-139">按下 "播放" 按钮进入游戏模式，然后按住鼠标右键以旋转注视方向，并注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="a9855-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="a9855-140">现在，ButtonCollection 的转换位置由求解器设置驱动</span><span class="sxs-lookup"><span data-stu-id="a9855-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="a9855-141">多维数据集不受求解器影响的多维数据集将保持不变</span><span class="sxs-lookup"><span data-stu-id="a9855-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="a9855-143">如果在场景窗口中看不到相机射线，请确保已启用 Gizmos 菜单。</span><span class="sxs-lookup"><span data-stu-id="a9855-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="a9855-144">若要详细了解 Gizmos 菜单以及如何使用它来优化场景视图，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos 菜单</a>文档。</span><span class="sxs-lookup"><span data-stu-id="a9855-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="a9855-145">若要在上图中并排显示场景和游戏窗口，只需将游戏窗口拖到场景窗口的右侧。</span><span class="sxs-lookup"><span data-stu-id="a9855-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="a9855-146">若要详细了解如何自定义工作区，可访问 Unity<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自定义工作区</a>文档。</span><span class="sxs-lookup"><span data-stu-id="a9855-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="a9855-147">使对象跟随跟踪的手</span><span class="sxs-lookup"><span data-stu-id="a9855-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="a9855-148">在本部分中，你将配置在上一教程中创建的多维数据集对象，使其跟随用户的跟踪，尤其是右边的手腕。</span><span class="sxs-lookup"><span data-stu-id="a9855-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user’s tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="a9855-149">此外，还会将规划求解配置为多维数据集：</span><span class="sxs-lookup"><span data-stu-id="a9855-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="a9855-150">更改用户的旋转方向</span><span class="sxs-lookup"><span data-stu-id="a9855-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="a9855-151">定位在用户的手腕上</span><span class="sxs-lookup"><span data-stu-id="a9855-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="a9855-152">为此，您将使用**径向视图规划求解**，使被引用对象在视图锥内转换对象。</span><span class="sxs-lookup"><span data-stu-id="a9855-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="a9855-153">1. 添加径向视图规划求解</span><span class="sxs-lookup"><span data-stu-id="a9855-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="a9855-154">在 "层次结构" 窗口中，选择**多维数据集**对象，然后在 "检查器" 窗口中，使用 "**添加组件**" 按钮添加**径向视图（脚本）** 组件多维数据集对象。</span><span class="sxs-lookup"><span data-stu-id="a9855-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="a9855-155">2. 配置径向视图规划求解</span><span class="sxs-lookup"><span data-stu-id="a9855-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="a9855-156">配置**规划求解处理程序（脚本）** 组件：</span><span class="sxs-lookup"><span data-stu-id="a9855-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="a9855-157">将**跟踪的目标类型**更改为**手动接点**</span><span class="sxs-lookup"><span data-stu-id="a9855-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="a9855-158">将**跟踪的 Handness**更改为**Right**</span><span class="sxs-lookup"><span data-stu-id="a9855-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="a9855-159">更改与**手腕**的**接点**</span><span class="sxs-lookup"><span data-stu-id="a9855-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="a9855-160">配置**径向视图（脚本）** 组件：</span><span class="sxs-lookup"><span data-stu-id="a9855-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="a9855-161">更改**面向对象**的**引用方向**，然后选中 "**定向到引用方向**" 复选框</span><span class="sxs-lookup"><span data-stu-id="a9855-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="a9855-162">更改**最小距离**和**最大距离**为0</span><span class="sxs-lookup"><span data-stu-id="a9855-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="a9855-164">3. 使用编辑器内模拟测试径向视图规划求解</span><span class="sxs-lookup"><span data-stu-id="a9855-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="a9855-165">按下 "播放" 按钮进入游戏模式，然后按住空格键以调出手。</span><span class="sxs-lookup"><span data-stu-id="a9855-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="a9855-166">将鼠标光标移动到手上，然后单击并按住鼠标左键来旋转手：</span><span class="sxs-lookup"><span data-stu-id="a9855-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="a9855-168">祝贺你</span><span class="sxs-lookup"><span data-stu-id="a9855-168">Congratulations</span></span>

<span data-ttu-id="a9855-169">在本教程中，已学习如何使用 MRTK 的 solvers 让 UI 直观地追随用户。</span><span class="sxs-lookup"><span data-stu-id="a9855-169">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="a9855-170">还了解了如何将规划求解附加到对象（即多维数据集），以遵循用户的跟踪。</span><span class="sxs-lookup"><span data-stu-id="a9855-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="a9855-171">若要详细了解 MRTK 随附的这些和其他 solvers，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="a9855-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="a9855-172">下一教程： 5. 与三维对象交互</span><span class="sxs-lookup"><span data-stu-id="a9855-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
