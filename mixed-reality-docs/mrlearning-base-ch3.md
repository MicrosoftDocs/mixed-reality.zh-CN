---
title: 入门教程 - 4. 放置动态内容和使用解算器
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362036"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="2478c-105">4.放置动态内容和使用解算器</span><span class="sxs-lookup"><span data-stu-id="2478c-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="2478c-106">当全息影像直观地跟随用户并且在物理环境中无缝巧妙地参与互动时，它们在 HoloLens 2 中会变得真实生动。</span><span class="sxs-lookup"><span data-stu-id="2478c-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="2478c-107">本教程探讨如何使用 MRTK 提供的定位工具（称为“解算器”）动态放置全息影像，以解算复杂的空间定位方案。</span><span class="sxs-lookup"><span data-stu-id="2478c-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="2478c-108">在 MRTK 中，解算器是一个脚本和行为系统，可让 UI 元素跟随你、用户或场景中的其他游戏对象。</span><span class="sxs-lookup"><span data-stu-id="2478c-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="2478c-109">它们还可用于快速贴靠到某个位置，使应用程序更加直观。</span><span class="sxs-lookup"><span data-stu-id="2478c-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="2478c-110">目标</span><span class="sxs-lookup"><span data-stu-id="2478c-110">Objectives</span></span>

* <span data-ttu-id="2478c-111">介绍 MRTK 的解算器</span><span class="sxs-lookup"><span data-stu-id="2478c-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="2478c-112">使用解算器让一组按钮跟随用户</span><span class="sxs-lookup"><span data-stu-id="2478c-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="2478c-113">使用解算器使游戏对象跟随用户的跟踪手</span><span class="sxs-lookup"><span data-stu-id="2478c-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="2478c-114">解算器在 MRTK 中的位置</span><span class="sxs-lookup"><span data-stu-id="2478c-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="2478c-115">MRTK 的解算器位于 MRTK SDK 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="2478c-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="2478c-116">若要在项目中查看可用的解算器，请在“项目”窗口中，导航到“资产” > “MixedRealityToolkit.SDK” > “功能” > “实用工具” > “解算器”：     </span><span class="sxs-lookup"><span data-stu-id="2478c-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="2478c-118">本教程将回顾轨道解算器和径向视图解算器的实现。</span><span class="sxs-lookup"><span data-stu-id="2478c-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="2478c-119">若要详细了解 MRTK 中提供的各个解算器，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="2478c-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="2478c-120">使用解算器跟随用户</span><span class="sxs-lookup"><span data-stu-id="2478c-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="2478c-121">在本部分，你将增强在上一篇教程中创建的按钮集合，使其跟随用户的视线方向。</span><span class="sxs-lookup"><span data-stu-id="2478c-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user's gaze direction.</span></span> <span data-ttu-id="2478c-122">此外，将配置解算器，使按钮集合始终：</span><span class="sxs-lookup"><span data-stu-id="2478c-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="2478c-123">平行于用户的阅读方向旋转（人们习惯于从左到右阅读）</span><span class="sxs-lookup"><span data-stu-id="2478c-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="2478c-124">定位在低于用户水平视线的位置，使其不会阻挡稍后要在本教程中添加的其他对象</span><span class="sxs-lookup"><span data-stu-id="2478c-124">Positioned below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="2478c-125">定位在相距用户大约半个手臂长度的位置，以便可以方便地按下按钮</span><span class="sxs-lookup"><span data-stu-id="2478c-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="2478c-126">为此，你将使用**轨道解算器**将对象锁定在指定的位置，并与参照对象之间保持一定的偏移量。</span><span class="sxs-lookup"><span data-stu-id="2478c-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="2478c-127">1.添加轨道解算器</span><span class="sxs-lookup"><span data-stu-id="2478c-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="2478c-128">在“层次结构”窗口中选择“ButtonCollection”对象，然后在“检查器”窗口中，使用“添加组件”按钮将“轨道(脚本)”组件添加到 ButtonCollection 对象。   </span><span class="sxs-lookup"><span data-stu-id="2478c-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="2478c-129">添加解算器（在本例中为“轨道(脚本)”组件）时，会自动添加“解算器处理程序(脚本)”组件，因为解算器需要该组件。</span><span class="sxs-lookup"><span data-stu-id="2478c-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="2478c-130">2.配置轨道解算器</span><span class="sxs-lookup"><span data-stu-id="2478c-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="2478c-131">配置“解算器处理程序(脚本)”组件： </span><span class="sxs-lookup"><span data-stu-id="2478c-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="2478c-132">确认“跟踪的目标类型”是否设置为“头部”  </span><span class="sxs-lookup"><span data-stu-id="2478c-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="2478c-133">配置“轨道(脚本)”组件： </span><span class="sxs-lookup"><span data-stu-id="2478c-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="2478c-134">确认“方向类型”是否设置为“跟随跟踪的对象”  </span><span class="sxs-lookup"><span data-stu-id="2478c-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="2478c-135">将“本地偏移”重置为 X = 0，Y = 0，Z = 0 </span><span class="sxs-lookup"><span data-stu-id="2478c-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="2478c-136">将“世界偏移”更改为 X = 0，Y = -0.4，Z = 0.3 </span><span class="sxs-lookup"><span data-stu-id="2478c-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="2478c-138">3.使用编辑器中的模拟功能测试轨道解算器</span><span class="sxs-lookup"><span data-stu-id="2478c-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="2478c-139">按“播放”按钮进入“游戏”模式，然后在按住鼠标右键的同时旋转视线方向，此时会注意到以下情况：</span><span class="sxs-lookup"><span data-stu-id="2478c-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="2478c-140">ButtonCollection 的变换位置现在由解算器设置驱动</span><span class="sxs-lookup"><span data-stu-id="2478c-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="2478c-141">不受解算器影响的立方体保留在同一位置</span><span class="sxs-lookup"><span data-stu-id="2478c-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="2478c-143">如果在“场景”窗口中未看到相机光线，请确保已启用调节器菜单。</span><span class="sxs-lookup"><span data-stu-id="2478c-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="2478c-144">若要详细了解调节器菜单以及如何使用它来优化场景视图，可以访问 Unity 的<a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">调节器菜单</a>文档。</span><span class="sxs-lookup"><span data-stu-id="2478c-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="2478c-145">若要按上图所示并排显示“场景”和“游戏”窗口，只需将“游戏”窗口拖放到“场景”窗口的右侧。</span><span class="sxs-lookup"><span data-stu-id="2478c-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="2478c-146">若要详细了解如何自定义工作区，可以访问 Unity 的<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">自定义工作区</a>文档。</span><span class="sxs-lookup"><span data-stu-id="2478c-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="2478c-147">使对象跟随跟踪手</span><span class="sxs-lookup"><span data-stu-id="2478c-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="2478c-148">在本部分，你将配置在上一篇教程中创建的立方体对象，使其跟随用户的跟踪手，具体而言是右手手腕。</span><span class="sxs-lookup"><span data-stu-id="2478c-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user's tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="2478c-149">此外，将配置解算器，使立方体：</span><span class="sxs-lookup"><span data-stu-id="2478c-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="2478c-150">根据用户手部的旋转改变自身的方向</span><span class="sxs-lookup"><span data-stu-id="2478c-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="2478c-151">定位在用户的手腕上</span><span class="sxs-lookup"><span data-stu-id="2478c-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="2478c-152">为此，你将使用**径向视图解算器**使对象保留在参照对象投射的锥形视图范围内。</span><span class="sxs-lookup"><span data-stu-id="2478c-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="2478c-153">1.添加径向视图解算器</span><span class="sxs-lookup"><span data-stu-id="2478c-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="2478c-154">在“层次结构”窗口中选择“Cube”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“径向视图(脚本)”组件的 Cube 对象。   </span><span class="sxs-lookup"><span data-stu-id="2478c-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="2478c-155">2.配置径向视图解算器</span><span class="sxs-lookup"><span data-stu-id="2478c-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="2478c-156">配置“解算器处理程序(脚本)”组件： </span><span class="sxs-lookup"><span data-stu-id="2478c-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="2478c-157">将“跟踪的目标类型”更改为“手关节”  </span><span class="sxs-lookup"><span data-stu-id="2478c-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="2478c-158">将“跟踪左手还是右手”更改为“右手”  </span><span class="sxs-lookup"><span data-stu-id="2478c-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="2478c-159">将“跟踪的手关节”更改为“手腕”  </span><span class="sxs-lookup"><span data-stu-id="2478c-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="2478c-160">配置“径向视图(脚本)”组件： </span><span class="sxs-lookup"><span data-stu-id="2478c-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="2478c-161">将“参照方向”更改为“对象定向”，然后选中“按参照方向定向”复选框   </span><span class="sxs-lookup"><span data-stu-id="2478c-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="2478c-162">将“最小距离”和“最大距离”更改为 0  </span><span class="sxs-lookup"><span data-stu-id="2478c-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="2478c-164">3.使用编辑器中的模拟功能测试径向视图解算器</span><span class="sxs-lookup"><span data-stu-id="2478c-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="2478c-165">按“播放”按钮进入“游戏”模式，然后在按住空格键的同时抬手。</span><span class="sxs-lookup"><span data-stu-id="2478c-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="2478c-166">移动鼠标光标以移动手形，然后在按住鼠标左键的同时旋转手部：</span><span class="sxs-lookup"><span data-stu-id="2478c-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="2478c-168">祝贺</span><span class="sxs-lookup"><span data-stu-id="2478c-168">Congratulations</span></span>

<span data-ttu-id="2478c-169">在本课程中，你已了解如何使用 MRTK 的解算器使 UI 直观地跟随用户。</span><span class="sxs-lookup"><span data-stu-id="2478c-169">In this tutorial, you learned how to use the MRTK's solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="2478c-170">你还了解了如何将解算器附加到某个对象（这里是立方体）以跟随用户的跟踪手。</span><span class="sxs-lookup"><span data-stu-id="2478c-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user's tracked hands.</span></span> <span data-ttu-id="2478c-171">若要详细了解上述解算器以及 MRTK 中包含的其他解算器，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[解算器](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)指南。</span><span class="sxs-lookup"><span data-stu-id="2478c-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="2478c-172">下一教程：5.与 3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="2478c-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
