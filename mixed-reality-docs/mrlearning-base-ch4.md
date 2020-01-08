---
title: 入门教程-5。 与三维对象交互
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: fe068d0cfcea369f10e6fa636eb73fecb3002fa7
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334386"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="54ff7-104">5. 与三维对象交互</span><span class="sxs-lookup"><span data-stu-id="54ff7-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="54ff7-105">在本教程中，你将了解基本的3D 内容和用户体验，例如：</span><span class="sxs-lookup"><span data-stu-id="54ff7-105">In this tutorial, you will learn about basic 3D content and user experience, such as:</span></span>

* <span data-ttu-id="54ff7-106">将三维对象组织为集合的一部分</span><span class="sxs-lookup"><span data-stu-id="54ff7-106">Organizing 3D objects as part of a collection</span></span>
* <span data-ttu-id="54ff7-107">基本操作的边界框</span><span class="sxs-lookup"><span data-stu-id="54ff7-107">Bounding boxes for basic manipulation</span></span>
* <span data-ttu-id="54ff7-108">近和远交互</span><span class="sxs-lookup"><span data-stu-id="54ff7-108">Near and far interaction</span></span>
* <span data-ttu-id="54ff7-109">触摸和获取手动跟踪的手势</span><span class="sxs-lookup"><span data-stu-id="54ff7-109">Touch and grab gestures with hand tracking</span></span>

## <a name="objectives"></a><span data-ttu-id="54ff7-110">目标</span><span class="sxs-lookup"><span data-stu-id="54ff7-110">Objectives</span></span>

* <span data-ttu-id="54ff7-111">了解如何通过 MRTK 的网格对象集合来组织3D 内容</span><span class="sxs-lookup"><span data-stu-id="54ff7-111">Learn how to organize 3D content with MRTK's grid object collection</span></span>
* <span data-ttu-id="54ff7-112">实现边界框</span><span class="sxs-lookup"><span data-stu-id="54ff7-112">Implement bounding boxes</span></span>
* <span data-ttu-id="54ff7-113">为基本操作配置3D 对象--移动、旋转和缩放</span><span class="sxs-lookup"><span data-stu-id="54ff7-113">Configure 3D objects for basic manipulation--move, rotate, and scale</span></span>
* <span data-ttu-id="54ff7-114">探索近距和远距交互</span><span class="sxs-lookup"><span data-stu-id="54ff7-114">Explore near and far interaction</span></span>
* <span data-ttu-id="54ff7-115">了解其他手动跟踪手势，如抓取和触摸</span><span class="sxs-lookup"><span data-stu-id="54ff7-115">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="54ff7-116">在集合中组织 3D 对象</span><span class="sxs-lookup"><span data-stu-id="54ff7-116">Organizing 3D Objects in a Collection</span></span>

1. <span data-ttu-id="54ff7-117">右键单击你的层次结构，然后选择 "创建空" 创建一个空游戏对象，将其重命名为 "3DObjectCollection"，并确保其位于 x = 0、y = 0，z = 0。</span><span class="sxs-lookup"><span data-stu-id="54ff7-117">Right-click on your hierarchy and select Create Empty to create an empty game object, rename it to 3DObjectCollection, and make sure it is positioned at x = 0, y = 0, and z = 0.</span></span>

    ![mrlearning-base-ch4-1-step1 .png](images/mrlearning-base-ch4-1-step1.png)

2. <span data-ttu-id="54ff7-119">下载 Unity 包[HoloLens2](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) ，并使用与导入[学习](mrlearning-base-ch1.md)中所述的自定义包相同的说明导入它。</span><span class="sxs-lookup"><span data-stu-id="54ff7-119">Download the Unity package [Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) and import it using the same instructions to import custom packages outlined in [Lesson1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="54ff7-120">此包包括3D 模型以及在本教程中使用的其他有用资产。</span><span class="sxs-lookup"><span data-stu-id="54ff7-120">This package includes 3D models and other useful assets that are used throughout this tutorial.</span></span>

3. <span data-ttu-id="54ff7-121">在 "项目" 面板中，导航到 "资产" > BaseModuleAssets > 基本模块 "Prototyping"，然后搜索 "未完成"，我们将使用其中一些 prototyping。</span><span class="sxs-lookup"><span data-stu-id="54ff7-121">In the Project panel, navigate to Assets > BaseModuleAssets > Base Module Prefabs and search for "incomplete", we will use some of these prefabs.</span></span>

    ![mrlearning-base-ch4-1-step3 .png](images/mrlearning-base-ch4-1-step3.png)

4. <span data-ttu-id="54ff7-123">将咖啡杯拖到步骤1中的3DObjectCollection 游戏对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-123">Drag the coffee cup into the 3DObjectCollection game object from Step 1.</span></span> <span data-ttu-id="54ff7-124">现在，该咖啡杯是集合的子级。</span><span class="sxs-lookup"><span data-stu-id="54ff7-124">The coffee cup is now a child of the collection.</span></span>

    ![mrlearning-base-ch4-1-step4 .png](images/mrlearning-base-ch4-1-step4.png)

5. <span data-ttu-id="54ff7-126">接下来，您将按照上一步骤中的相同过程，将更多的3D 对象添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="54ff7-126">Next, you'll add more 3D objects into our scene by following the same process as in the previous step.</span></span> <span data-ttu-id="54ff7-127">下面是此示例中要添加的对象的列表。</span><span class="sxs-lookup"><span data-stu-id="54ff7-127">Below is a list of objects to add in this example.</span></span> <span data-ttu-id="54ff7-128">添加这些对象时，可能会发现它们以各种大小显示在场景中。</span><span class="sxs-lookup"><span data-stu-id="54ff7-128">As you add the objects, you might find they appear in your scene in various sizes.</span></span> <span data-ttu-id="54ff7-129">调整检查器面板中 "转换设置" 下的每个三维模型的比例。</span><span class="sxs-lookup"><span data-stu-id="54ff7-129">Adjust the scale of each 3D model under Transform settings in the Inspector panel.</span></span> <span data-ttu-id="54ff7-130">下面列出了本示例中各个对象的建议调整大小。</span><span class="sxs-lookup"><span data-stu-id="54ff7-130">Recommended adjustments for this example are listed with the objects below.</span></span>

    * <span data-ttu-id="54ff7-131">Cheese_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="54ff7-131">Cheese_BaseModuleIncomplete.</span></span> <span data-ttu-id="54ff7-132">Scale： x = 0.05，y = 0.05，z = 0.05。</span><span class="sxs-lookup"><span data-stu-id="54ff7-132">Scale: x = 0.05, y = 0.05, z = 0.05.</span></span>
    * <span data-ttu-id="54ff7-133">CoffeeCup_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="54ff7-133">CoffeeCup_BaseModuleIncomplete.</span></span> <span data-ttu-id="54ff7-134">Scale： x = 0.1，y = 0.1，z = 0.1。</span><span class="sxs-lookup"><span data-stu-id="54ff7-134">Scale: x = 0.1, y = 0.1, z = 0.1.</span></span>
    * <span data-ttu-id="54ff7-135">EarthCore_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="54ff7-135">EarthCore_BaseModuleIncomplete.</span></span> <span data-ttu-id="54ff7-136">Scale： x = 50.0 y = 50.0，z = 50.0。</span><span class="sxs-lookup"><span data-stu-id="54ff7-136">Scale: x = 50.0 y = 50.0, z = 50.0.</span></span>
    * <span data-ttu-id="54ff7-137">Model_Platonic_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="54ff7-137">Model_Platonic_BaseModuleIncomplete.</span></span> <span data-ttu-id="54ff7-138">Scale： x = 0.13，y = 0.13，z = 0.13。</span><span class="sxs-lookup"><span data-stu-id="54ff7-138">Scale: x = 0.13, y = 0.13, z = 0.13.</span></span>
    * <span data-ttu-id="54ff7-139">Octa_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="54ff7-139">Octa_BaseModuleIncomplete.</span></span> <span data-ttu-id="54ff7-140">Scale： x = 0.13。</span><span class="sxs-lookup"><span data-stu-id="54ff7-140">Scale: x = 0.13.</span></span> <span data-ttu-id="54ff7-141">y = 0.13，z =0.13。</span><span class="sxs-lookup"><span data-stu-id="54ff7-141">y = 0.13, z =0.13.</span></span>
    * <span data-ttu-id="54ff7-142">TheModule_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="54ff7-142">TheModule_BaseModuleIncomplete.</span></span> <span data-ttu-id="54ff7-143">Scale： x = 0.03，y = 0.03，z = 0.03。</span><span class="sxs-lookup"><span data-stu-id="54ff7-143">Scale: x = 0.03, y = 0.03, z = 0.03.</span></span>

    ![mrlearning-base-ch4-1-step5 .png](images/mrlearning-base-ch4-1-step5.png)

6. <span data-ttu-id="54ff7-145">将三个多维数据集添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="54ff7-145">Add three cubes into your scene.</span></span> <span data-ttu-id="54ff7-146">右键单击 "3DObjectCollection" 对象，选择 "3D 对象"，然后选择 "多维数据集"。</span><span class="sxs-lookup"><span data-stu-id="54ff7-146">Right-click the 3DObjectCollection object, select 3D Object, then select Cube.</span></span> <span data-ttu-id="54ff7-147">将坐标设置为 x = 0.14，y = 0.14，z = 0.14。</span><span class="sxs-lookup"><span data-stu-id="54ff7-147">Set the scale to x = 0.14, y = 0.14, and z = 0.14.</span></span> <span data-ttu-id="54ff7-148">重复此步骤两次，以创建总计三个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="54ff7-148">Repeat this step two additional times to create a total of three cubes.</span></span> <span data-ttu-id="54ff7-149">或者，可以复制多维数据集两次，共三个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="54ff7-149">Alternatively, you can duplicate the cube twice for a total of three cubes.</span></span> <span data-ttu-id="54ff7-150">也可以选择使用“资产”>“基础模块资产”>“基础模块预制件”中三个已准备好的立方体预制件，并选择“GreenCube_BaseModuleIncomplete”、“BlueCube_BaseModuleIncomplete”和“OrangeCube_BaseModuleIncomplete”。</span><span class="sxs-lookup"><span data-stu-id="54ff7-150">You may also choose to use the three prepared cube prefabs from Assets>BaseModuleAssets>Base Module Prefabs and select GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete and OrangeCube_BaseModuleIncomplete.</span></span>

    ![mrlearning-base-ch4-1-step6 .png](images/mrlearning-base-ch4-1-step6.png)

7. <span data-ttu-id="54ff7-152">使用 MRTK 的网格对象集合，通过[第2课](mrlearning-base-ch2.md)中所述的过程来组织对象集合，以形成网格。</span><span class="sxs-lookup"><span data-stu-id="54ff7-152">Organize your collection of objects to form a grid, via the procedure described in [Lesson 2](mrlearning-base-ch2.md), using the MRTK’s Grid Object Collection.</span></span> <span data-ttu-id="54ff7-153">请参阅下图，以了解在3x3 网格中配置对象的示例。</span><span class="sxs-lookup"><span data-stu-id="54ff7-153">Refer to the image below, for an example of configuring the objects in a 3x3 grid.</span></span>

    ![mrlearning-base-ch4-1-step7 .png](images/mrlearning-base-ch4-1-step7.png)

    >[!NOTE]
    ><span data-ttu-id="54ff7-155">你可能会注意到，某些对象处于中间中心，如上图中的对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-155">You might notice that some of the objects are off-center, such as the objects in the image above.</span></span> <span data-ttu-id="54ff7-156">这是因为，预制件或对象可能包含未对齐的子对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-156">This is because prefabs or objects may have child objects that are not aligned.</span></span> <span data-ttu-id="54ff7-157">请对对象位置或子对象位置进行任何必要的调整，以获得适当对齐的网格。</span><span class="sxs-lookup"><span data-stu-id="54ff7-157">Feel free to make any necessary adjustments to object positions or child object positions to achieve a well-aligned grid.</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="54ff7-158">操作 3D 对象</span><span class="sxs-lookup"><span data-stu-id="54ff7-158">Manipulating 3D Objects</span></span>

1. <span data-ttu-id="54ff7-159">添加操作立方体的功能。</span><span class="sxs-lookup"><span data-stu-id="54ff7-159">Add the ability to manipulate a cube.</span></span> <span data-ttu-id="54ff7-160">若要添加操作3D 对象的功能，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="54ff7-160">To add the ability to manipulate 3D objects, do the following:</span></span>
    * <span data-ttu-id="54ff7-161">选择要在层次结构中操作的3D 对象（即某个多维数据集）。</span><span class="sxs-lookup"><span data-stu-id="54ff7-161">Select the 3D object you want to manipulate in your hierarchy (i.e. one of your cubes).</span></span>
    * <span data-ttu-id="54ff7-162">单击 "添加组件"</span><span class="sxs-lookup"><span data-stu-id="54ff7-162">Click Add Component</span></span>
    * <span data-ttu-id="54ff7-163">搜索 "操作"</span><span class="sxs-lookup"><span data-stu-id="54ff7-163">Search for "manipulation"</span></span>
    * <span data-ttu-id="54ff7-164">选择操作处理程序</span><span class="sxs-lookup"><span data-stu-id="54ff7-164">Select Manipulation Handler</span></span>
    * <span data-ttu-id="54ff7-165">对3DObjectCollection 对象下的所有3D 对象重复此操作，而不是3DObjectCollection 本身。</span><span class="sxs-lookup"><span data-stu-id="54ff7-165">Repeat for all 3D objects under the 3DObjectCollection object, but not the 3DObjectCollection itself.</span></span>
    * <span data-ttu-id="54ff7-166">确保所有三维对象都具有碰撞器或盒碰撞器（添加组件 > 框碰撞器）。</span><span class="sxs-lookup"><span data-stu-id="54ff7-166">Ensure that all 3D objects have a collider or box collider (Add Component>Box Collider).</span></span>

    ![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

    >[!NOTE]
    ><span data-ttu-id="54ff7-168">操作处理程序是一个组件，可用于调整对象在操作时的行为方式的设置。</span><span class="sxs-lookup"><span data-stu-id="54ff7-168">The manipulation handler is a component that lets you adjust settings for how objects behave when manipulated.</span></span> <span data-ttu-id="54ff7-169">这包括在特定轴上进行旋转、缩放、移动和约束移动。</span><span class="sxs-lookup"><span data-stu-id="54ff7-169">This includes rotation, scaling, moving, and constraining movement on a specific axis.</span></span>

2. <span data-ttu-id="54ff7-170">请限制一个立方体，以便只能对它进行缩放。</span><span class="sxs-lookup"><span data-stu-id="54ff7-170">Restrict one cube so that it can only be scaled.</span></span> <span data-ttu-id="54ff7-171">选择3DObjectCollection 对象中的一个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="54ff7-171">Select one cube in the 3DObjectCollection object.</span></span> <span data-ttu-id="54ff7-172">在 "检查器" 面板中，在 "两种操作类型" 旁单击下拉菜单，然后选择 "缩放"。</span><span class="sxs-lookup"><span data-stu-id="54ff7-172">In the Inspector panel, next to Two Handed Manipulation Type, click the drop-down menu and select Scale.</span></span> <span data-ttu-id="54ff7-173">这样，用户只能更改该立方体的大小。</span><span class="sxs-lookup"><span data-stu-id="54ff7-173">This makes it so that the user can only change the cube’s size.</span></span>

    ![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. <span data-ttu-id="54ff7-175">更改每个立方体的颜色，以便可以区分它们。</span><span class="sxs-lookup"><span data-stu-id="54ff7-175">Change the color of each cube so that we can differentiate between them.</span></span>
    * <span data-ttu-id="54ff7-176">请访问 "项目" 面板并向下滚动，直到看到 "MixedRealityToolkit"，然后选择它。</span><span class="sxs-lookup"><span data-stu-id="54ff7-176">Go to the Project panel and scroll down until you see MixedRealityToolkit.SDK, then select it.</span></span>
    * <span data-ttu-id="54ff7-177">选择 "标准资产" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="54ff7-177">Select the Standard Assets folder.</span></span>
    * <span data-ttu-id="54ff7-178">单击 "材料" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="54ff7-178">Click the Materials folder.</span></span>
    * <span data-ttu-id="54ff7-179">将不同的材料拖放到每个立方体上。</span><span class="sxs-lookup"><span data-stu-id="54ff7-179">Drag a different material onto each of your cubes.</span></span>

    >[!NOTE]
    ><span data-ttu-id="54ff7-180">可为立方体选择任意颜色。</span><span class="sxs-lookup"><span data-stu-id="54ff7-180">You can choose any color for your cubes.</span></span> <span data-ttu-id="54ff7-181">在此示例中，使用了 glowingcyan、glowingorange 和绿色。</span><span class="sxs-lookup"><span data-stu-id="54ff7-181">For this example, glowingcyan, glowingorange and green are used.</span></span> <span data-ttu-id="54ff7-182">请随意尝试不同的颜色。</span><span class="sxs-lookup"><span data-stu-id="54ff7-182">Feel free to experiment with different colors.</span></span> <span data-ttu-id="54ff7-183">若要将颜色添加到多维数据集，请单击想要更改的多维数据集，然后将该材料拖到多维数据集的 "检查器" 面板中的 "网格呈现器" 材料字段。</span><span class="sxs-lookup"><span data-stu-id="54ff7-183">To add the color to the cube, click the cube you want to change, then drag the material to the mesh renderer's material field in the cube's Inspector panel.</span></span>

    ![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. <span data-ttu-id="54ff7-185">选择3DObjectCollection 对象中的其他多维数据集，然后将其移动限制为固定距离。</span><span class="sxs-lookup"><span data-stu-id="54ff7-185">Select another cube in the 3DObjectCollection object and make it so that its movement is constrained to a fixed distance from the head.</span></span> <span data-ttu-id="54ff7-186">为此，请在 "移动标签上的约束" 右侧单击下拉菜单，然后选择 "修复距离"。</span><span class="sxs-lookup"><span data-stu-id="54ff7-186">To do this, to the right of Constraint on Movement label, click the drop-down menu and select Fix Distance from the Head.</span></span> <span data-ttu-id="54ff7-187">这会将多维数据集调整到其视觉领域。</span><span class="sxs-lookup"><span data-stu-id="54ff7-187">This adjusts the cube to be within their field of vision.</span></span>

    ![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

    <span data-ttu-id="54ff7-189">下面几个步骤的目标是启用抓取并与我们的3D 对象进行交互，并应用不同的操作设置。</span><span class="sxs-lookup"><span data-stu-id="54ff7-189">The goal of the following few steps is to enable grabbing and interacting with our 3D objects and applying different manipulation settings.</span></span>

5. <span data-ttu-id="54ff7-190">选择奶酪对象，并单击 "检查器" 面板中的 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="54ff7-190">Select the Cheese object, then click Add Component from the Inspector panel.</span></span>

6. <span data-ttu-id="54ff7-191">在搜索框中搜索近乎交互 Grabbable，并选择该脚本。</span><span class="sxs-lookup"><span data-stu-id="54ff7-191">Search in the search box for Near Interaction Grabbable and select the script.</span></span> <span data-ttu-id="54ff7-192">此组件使用户可以通过跟踪的手访问和吸引对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-192">This component enables users to reach out and grab objects with tracked hands.</span></span> <span data-ttu-id="54ff7-193">对象也可以从远处操作，除非在下图中以绿色圆圈表示的 "允许远操作" 复选框未被选中。</span><span class="sxs-lookup"><span data-stu-id="54ff7-193">Objects can also be manipulated from a distance, unless the Allow Far Manipulation checkbox is unchecked as denoted by a green circle in the image below.</span></span>

    ![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. <span data-ttu-id="54ff7-195">通过对这些对象重复步骤5和步骤6，将近交互 Grabbable 添加到八对象、Platonic 对象、地球核心、农历和咖啡杯。</span><span class="sxs-lookup"><span data-stu-id="54ff7-195">Add Near Interaction Grabbable to the Octa object, Platonic object, Earth Core, Lunar Module, and Coffee Cup by repeating Steps 5 and 6 on those objects.</span></span>

8. <span data-ttu-id="54ff7-196">从八面体对象中删除远距操作功能。</span><span class="sxs-lookup"><span data-stu-id="54ff7-196">Remove the ability of far manipulation from the Octa object.</span></span> <span data-ttu-id="54ff7-197">为此，请选择层次结构中的八，并取消选中 "允许远端操作" 复选框（由绿色圆圈标记）。</span><span class="sxs-lookup"><span data-stu-id="54ff7-197">To do this, select the Octa in the hierarchy and uncheck the Allow far Manipulation checkbox (marked by a green circle).</span></span> <span data-ttu-id="54ff7-198">这样，用户就只能使用跟踪的手直接与八交互。</span><span class="sxs-lookup"><span data-stu-id="54ff7-198">This makes it so users can only interact with the octa directly using tracked hands.</span></span>

    >[!NOTE]
    ><span data-ttu-id="54ff7-199">有关操作处理程序组件及其相关设置的完整文档，请参阅[MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。</span><span class="sxs-lookup"><span data-stu-id="54ff7-199">For the full documentation of the manipulation handler component and it's associated settings, refer to the [MRTK Documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).</span></span>

9. <span data-ttu-id="54ff7-200">确保将近交互 Grabbable 组件添加到了地球核心、农历模块和咖啡杯上（请参见步骤7）。</span><span class="sxs-lookup"><span data-stu-id="54ff7-200">Ensure that the Near Interaction Grabbable component has been added to the earth core, the lunar module and the coffee cup (see Step 7).</span></span>

10. <span data-ttu-id="54ff7-201">对于农历模块，请更改操作处理程序设置，使其围绕对象中心围绕近和远交互进行旋转，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="54ff7-201">For the lunar module, change the Manipulation Handler settings so that it rotates around the object's center for both near and far interaction, as shown in the image below.</span></span>

    ![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11. <span data-ttu-id="54ff7-203">对于地球核心，将版本行为更改为 "无"。</span><span class="sxs-lookup"><span data-stu-id="54ff7-203">For the earth core, change the release behavior to nothing.</span></span> <span data-ttu-id="54ff7-204">这样做是为了使地球核心从用户的抓住中释放出来，而不会继续移动。</span><span class="sxs-lookup"><span data-stu-id="54ff7-204">This makes it so that once the earth core is released from the user's grasp, it doesn’t continue to move.</span></span>

    ![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

    >[!NOTE]
    ><span data-ttu-id="54ff7-206">此设置适用于方案，例如创建可引发的球。</span><span class="sxs-lookup"><span data-stu-id="54ff7-206">This setting is useful for scenarios, such as creating a ball that you can throw.</span></span> <span data-ttu-id="54ff7-207">保持适当的速度和角度速度，以确保在球发布后，它将继续以其释放速度的速度移动;与物理球的行为方式类似。</span><span class="sxs-lookup"><span data-stu-id="54ff7-207">Keeping the appropriate velocity and angular velocity to ensure that once the ball is released, it will continue to move at the velocity it was released at; similar to how a physical ball would behave.</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="54ff7-208">添加边界框</span><span class="sxs-lookup"><span data-stu-id="54ff7-208">Adding Bounding Boxes</span></span>

<span data-ttu-id="54ff7-209">边界框使您可以更轻松、更直观地处理对象，同时可以直接操作（接近交互）和基于光线的操作（远交互）。边界框提供可用于沿特定轴缩放和旋转对象的句柄。</span><span class="sxs-lookup"><span data-stu-id="54ff7-209">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both direct manipulation (near interaction) and ray-based manipulation (far interaction.) Bounding boxes provide handles that can be grabbed for scaling and rotating objects along a specific axis.</span></span>

>[!NOTE]
><span data-ttu-id="54ff7-210">在将边界框添加到对象之前，您首先需要在该对象上创建一个碰撞器（例如，盒碰撞器），如本课程前面所述。</span><span class="sxs-lookup"><span data-stu-id="54ff7-210">Before you can add a bounding box to an object, you first need to have a collider on the object (e.g., a box collider), as was covered previously in this lesson.</span></span> <span data-ttu-id="54ff7-211">可以通过选择对象并在对象的 "检查器" 面板中选择 "添加组件 >" 碰撞器来添加 Colliders。</span><span class="sxs-lookup"><span data-stu-id="54ff7-211">Colliders can be added by selecting the object and in the object's inspector panel selecting Add Component>Box Collider.</span></span>

1. <span data-ttu-id="54ff7-212">如果地球核心对象尚不存在，请将其添加到地球核心对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-212">Add a box collider to the Earth Core object if one does not already exist.</span></span> <span data-ttu-id="54ff7-213">如果根据给定的说明使用基本模块资产文件夹中提供的 prefab，则不需要使用框碰撞器和设置。</span><span class="sxs-lookup"><span data-stu-id="54ff7-213">The box collider and setup are not required, if using the prefab provided in the Base Module Assets folder per the instructions given.</span></span> <span data-ttu-id="54ff7-214">对于地球核心，我们将框碰撞器添加到了地球核心下的、node_id30 的对象，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="54ff7-214">In the case of the earth core, we added the box collider to the, node_id30, object underneath the earth core, as shown in the image below.</span></span> <span data-ttu-id="54ff7-215">从对象的 "检查器" 选项卡中选择 "node_id30"，单击 "添加组件"，然后搜索 box 碰撞器。</span><span class="sxs-lookup"><span data-stu-id="54ff7-215">Select node_id30 from the object's Inspector tab, click Add Component, and search for box collider.</span></span>

    ![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

    ![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

    >[!NOTE]
    ><span data-ttu-id="54ff7-218">请确保将框碰撞器的大小设置为不太大或太小。</span><span class="sxs-lookup"><span data-stu-id="54ff7-218">Make sure that you size the box collider so that it’s not too big or too small.</span></span> <span data-ttu-id="54ff7-219">其大小应与围绕它的对象（在本示例中为地核）大致相同。</span><span class="sxs-lookup"><span data-stu-id="54ff7-219">It should be roughly the same size as the object it’s surrounding (in this example, the earth core).</span></span> <span data-ttu-id="54ff7-220">通过选择框碰撞器中的 "编辑碰撞器" 选项，根据需要调整框碰撞器。</span><span class="sxs-lookup"><span data-stu-id="54ff7-220">Adjust the box collider as needed by selecting the Edit Collider option in the box collider.</span></span> <span data-ttu-id="54ff7-221">您可以更改 x、y 和 z 值，也可以在编辑器场景窗口中拖动边界框处理程序。</span><span class="sxs-lookup"><span data-stu-id="54ff7-221">You can either changing the x, y, and z values or drag the bounding box handlers in the Editor Scene window.</span></span>

    ![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. <span data-ttu-id="54ff7-223">将边界框添加到地球核心的 node_id30 对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-223">Add a bounding box to the earth core's node_id30 object.</span></span> <span data-ttu-id="54ff7-224">为此，请从3DObjectCollection 中选择 "node_id30" 对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-224">To do this, select the node_id30 object from the 3DObjectCollection.</span></span> <span data-ttu-id="54ff7-225">在 "检查器" 选项卡中，单击 "添加组件"，然后搜索 "边界框"。</span><span class="sxs-lookup"><span data-stu-id="54ff7-225">In the inspector tab, click Add Component, and search for bounding box.</span></span> <span data-ttu-id="54ff7-226">确保边界框、盒碰撞体和操作脚本（操作处理程序、近距交互可抓取对象）都在同一个游戏对象中。</span><span class="sxs-lookup"><span data-stu-id="54ff7-226">Ensure that the bounding box, box collider, and manipulation scripts (manipulation handler, near interaction grabbable) are all on the same game object.</span></span>

3. <span data-ttu-id="54ff7-227">在 "边界框的行为" 部分中，从 "激活" 下拉列表中选择 "开始时激活"。</span><span class="sxs-lookup"><span data-stu-id="54ff7-227">In the bounding box's Behavior section, select Activate on Start from the Activation drop-down list.</span></span> <span data-ttu-id="54ff7-228">若要查看有关各个激活选项和其他范围框选项的其他详细信息，请参阅[MRTK 的边界框文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)</span><span class="sxs-lookup"><span data-stu-id="54ff7-228">To review additional details regarding the various activation options and other bounding box options, see the [MRTK's bounding box documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)</span></span>

    <span data-ttu-id="54ff7-229">*在接下来的几个步骤中，我们还将通过以下方式更改边界框的显示方式：调整默认的框材料、在其被抓取时的材料以及角部和侧图柄的可视化。MRTK 包含多个用于自定义边界框的选项。*</span><span class="sxs-lookup"><span data-stu-id="54ff7-229">*In the next few steps, we will also change how the bounding box looks by adjusting the default box material, the material while it’s being grabbed as well as the visualization of the corner and side handles. The MRTK contains several options to customize the bounding box.*</span></span>

4. <span data-ttu-id="54ff7-230">在 "项目" 面板中搜索 "boundingbox"，并在搜索结果中看到一个蓝色球体表示的材料列表，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="54ff7-230">In the Project panel, search for "boundingbox" and you’ll see a list of materials denoted by a blue sphere in the search results as shown in the image below.</span></span>

5. <span data-ttu-id="54ff7-231">将 boundingbox 材料拖动到边界框组件上的盒材料槽。</span><span class="sxs-lookup"><span data-stu-id="54ff7-231">Drag the boundingbox material into the box material slot on the bounding box component.</span></span> <span data-ttu-id="54ff7-232">另外，还可以获取 boundingboxgrabbed 材料，并将其放在边界框组件上的 "获取材料" 槽。</span><span class="sxs-lookup"><span data-stu-id="54ff7-232">Also grab the boundingboxgrabbed material and put that in the box grabbed material slot on the bounding box component.</span></span>

    ![mrlearning-base-ch4-3-step5 .png](images/mrlearning-base-ch4-3-step5.png)

6. <span data-ttu-id="54ff7-234">将 MRTK_BoundingBox_ScaleHandle prefab 拖到 "prefab" 槽中的刻度控点，并将 MRTK_BoundingBox_RotateHandle prefab 拖到 "捆绑箱" 组件上的旋转控点槽。</span><span class="sxs-lookup"><span data-stu-id="54ff7-234">Drag the MRTK_BoundingBox_ScaleHandle prefab into the scale handle prefab slot and the MRTK_BoundingBox_RotateHandle prefab into the rotation handle slot on the bonding box component.</span></span>

    ![mrlearning-base-ch4-3-step6 .png](images/mrlearning-base-ch4-3-step6.png)

7. <span data-ttu-id="54ff7-236">确保边界框针对适当的对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-236">Make sure the bounding box is targeting the right object.</span></span> <span data-ttu-id="54ff7-237">在边界框组件中，有目标对象和边界替代脚本。</span><span class="sxs-lookup"><span data-stu-id="54ff7-237">In the bounding box component, there is the target object and bounds override scripts.</span></span> <span data-ttu-id="54ff7-238">将边界框周围的对象拖到这两个槽。</span><span class="sxs-lookup"><span data-stu-id="54ff7-238">Drag the object that has the bounding box around it to both of these slots.</span></span> <span data-ttu-id="54ff7-239">在此示例中，将 node_id30 对象拖到这两个槽，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="54ff7-239">In this example, drag the node_id30 object to both of these slots, as shown in the image below.</span></span>

    ![mrlearning-base-ch4-3-step7 .png](images/mrlearning-base-ch4-3-step7.png)

    >[!NOTE]
    ><span data-ttu-id="54ff7-241">启动或播放应用程序时，对象将被蓝色框架括起来。</span><span class="sxs-lookup"><span data-stu-id="54ff7-241">When you start or play the application, your object will be surrounded by a blue frame.</span></span> <span data-ttu-id="54ff7-242">可以放心拖动该框的四角，以调整对象的大小。</span><span class="sxs-lookup"><span data-stu-id="54ff7-242">You’re welcome to drag the corners of that frame to resize the object.</span></span> <span data-ttu-id="54ff7-243">如果希望缩放控点更大且更可见，则建议使用默认边界框设置（避免步骤 4-6）。</span><span class="sxs-lookup"><span data-stu-id="54ff7-243">If you want the scaling handles and the rotation handles to be larger and more visible, it is recommend using the default bounding box settings (avoiding Steps 4 -through 6.)</span></span>

8. <span data-ttu-id="54ff7-244">若要返回到默认边界框可视化效果，请在边界框的对象的检查器面板中，选择旋转控点 prefab，并按 delete 将其删除。</span><span class="sxs-lookup"><span data-stu-id="54ff7-244">To return to the default bounding box visualization, in the Inspector panel of the bounding box's object, select the rotation handle prefab and press delete to remove it.</span></span> <span data-ttu-id="54ff7-245">进入播放模式时，wou 会看到类似于下图的边界框可视化。</span><span class="sxs-lookup"><span data-stu-id="54ff7-245">When you enter play mode, wou will see a bounding box visualization similar to the image below.</span></span>

    ![mrlearning-base-ch4-3-step8 .png](images/mrlearning-base-ch4-3-step8.png)

    >[!NOTE]
    ><span data-ttu-id="54ff7-247">只有在播放模式下，边界框可视化效果才会显示。</span><span class="sxs-lookup"><span data-stu-id="54ff7-247">The bounding box visualizations only appear when in play mode.</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="54ff7-248">添加触摸效果</span><span class="sxs-lookup"><span data-stu-id="54ff7-248">Adding touch effects</span></span>

<span data-ttu-id="54ff7-249">本示例将在用手触摸某个对象时播放一段音效。</span><span class="sxs-lookup"><span data-stu-id="54ff7-249">In this example, we are going to play a sound effect when you touch an object with your hand.</span></span>

1. <span data-ttu-id="54ff7-250">将音频源组件添加到游戏对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-250">Add an audio source component to your game object.</span></span> <span data-ttu-id="54ff7-251">选择场景层次结构中的八对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-251">Select the Octa object in your scene hierarchy.</span></span> <span data-ttu-id="54ff7-252">在检查器面板中，单击 "添加组件" 按钮，搜索并选择 "音频源"。</span><span class="sxs-lookup"><span data-stu-id="54ff7-252">In the inspector panel, click the Add Component button, search for and select audio source.</span></span> <span data-ttu-id="54ff7-253">在稍后的步骤中，我们将使用此音频源播放音效。</span><span class="sxs-lookup"><span data-stu-id="54ff7-253">We’ll use this audio source to play a sound effect in a later step.</span></span>

    >[!NOTE]
    ><span data-ttu-id="54ff7-254">确保八对象上有一个框碰撞器。</span><span class="sxs-lookup"><span data-stu-id="54ff7-254">Ensure that the Octa object has a box collider on it.</span></span>

2. <span data-ttu-id="54ff7-255">添加 Near 交互可触摸组件。</span><span class="sxs-lookup"><span data-stu-id="54ff7-255">Add the Near Interaction Touchable component.</span></span> <span data-ttu-id="54ff7-256">单击 "检查器" 面板中的 "添加组件" 按钮，搜索近乎交互可触摸。</span><span class="sxs-lookup"><span data-stu-id="54ff7-256">Click the Add Component button in the Inspector panel and search for near interaction touchable.</span></span> <span data-ttu-id="54ff7-257">选择该对象以将它添加到组件。</span><span class="sxs-lookup"><span data-stu-id="54ff7-257">Select it to add the component.</span></span>

    >[!NOTE]
    ><span data-ttu-id="54ff7-258">以前，我们添加了近交互 grabbable。</span><span class="sxs-lookup"><span data-stu-id="54ff7-258">Previously, we added near interaction grabbable.</span></span> <span data-ttu-id="54ff7-259">此交互和近交互可触摸之间的区别在于，grabbable 交互适用于要进行抓取和交互的对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-259">The difference between this and near interaction touchable is that the grabbable interaction is intended for an object to be grabbed and interacted with.</span></span> <span data-ttu-id="54ff7-260">可触摸组件适用于要接触的对象。</span><span class="sxs-lookup"><span data-stu-id="54ff7-260">The touchable component is intended for the object to be touched.</span></span> <span data-ttu-id="54ff7-261">可以结合使用这两个组件以实现组合式交互。</span><span class="sxs-lookup"><span data-stu-id="54ff7-261">Both components can be used together for a combination of interactions.</span></span>

    ![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. <span data-ttu-id="54ff7-263">添加手交互触摸脚本。</span><span class="sxs-lookup"><span data-stu-id="54ff7-263">Add in the Hand Interaction Touch script.</span></span> <span data-ttu-id="54ff7-264">与上一步一样，单击 "添加组件"，然后搜索 "手动交互触摸" 进行添加。</span><span class="sxs-lookup"><span data-stu-id="54ff7-264">Just like the previous step, click Add Component and search for hand interaction touch to add it.</span></span>

    <span data-ttu-id="54ff7-265">请注意，此脚本有三个选项：</span><span class="sxs-lookup"><span data-stu-id="54ff7-265">Notice that you have three options with the script:</span></span>
    * <span data-ttu-id="54ff7-266">On Touch 完成：触控并释放对象时触发</span><span class="sxs-lookup"><span data-stu-id="54ff7-266">On Touch Completed: Triggers when you touch and release the object</span></span>
    * <span data-ttu-id="54ff7-267">开始时：接触对象时触发</span><span class="sxs-lookup"><span data-stu-id="54ff7-267">On Touch Started: Triggers when the object is touched</span></span>
    * <span data-ttu-id="54ff7-268">On Touch 更新：在你的手中触摸对象时定期触发</span><span class="sxs-lookup"><span data-stu-id="54ff7-268">On Touch Updated: Triggers periodically while your hand is touching the object</span></span>

    <span data-ttu-id="54ff7-269">在此示例中，我们将使用 "按下开始使用" 设置。</span><span class="sxs-lookup"><span data-stu-id="54ff7-269">For this example, we will be working with the On Touch Started setting.</span></span>

    >[!NOTE]
    ><span data-ttu-id="54ff7-270">此脚本随你在本教程开始时导入的 BaseModuleAssets Unity 包一起提供，并且不包含在原始 MRTK 中。</span><span class="sxs-lookup"><span data-stu-id="54ff7-270">This script is included with the BaseModuleAssets Unity package that you imported as at the beginning of this tutorial and it is not included in the original MRTK.</span></span>

4. <span data-ttu-id="54ff7-271">单击 "按 Touch 开始" 选项上的 "+" 按钮，然后将八对象拖到空字段。</span><span class="sxs-lookup"><span data-stu-id="54ff7-271">Click the + button on the On Touch Started option and drag the Octa object into the empty field.</span></span>

    ![mrlearning-base-ch4-4-step4 .png](images/mrlearning-base-ch4-4-step4.png)

5. <span data-ttu-id="54ff7-273">在 "没有函数" 下拉箭头中，选择 "AudioSource > PlayOneShot"。</span><span class="sxs-lookup"><span data-stu-id="54ff7-273">In the drop-down that says No Function, select AudioSource > PlayOneShot.</span></span> <span data-ttu-id="54ff7-274">使用以下概念将一个音频剪辑添加到此字段：</span><span class="sxs-lookup"><span data-stu-id="54ff7-274">We will add an audio clip to this field using the concepts below:</span></span>

    * <span data-ttu-id="54ff7-275">MRTK 提供了一个简短的音频剪辑列表。</span><span class="sxs-lookup"><span data-stu-id="54ff7-275">The MRTK does provide a small list of audio clips.</span></span> <span data-ttu-id="54ff7-276">可以在项目面板中随意浏览这些项。</span><span class="sxs-lookup"><span data-stu-id="54ff7-276">Feel free to explore these in your Project panel.</span></span> <span data-ttu-id="54ff7-277">你会在资产 > MixedRealityToolkit > 标准资产 > 音频文件夹 "下找到它们。</span><span class="sxs-lookup"><span data-stu-id="54ff7-277">You will find them under the Assets > MixedRealityToolkit.SDK > Standard Assets > Audio folder.</span></span>
    * <span data-ttu-id="54ff7-278">在此示例中，我们将使用 MRTK_Gem 音频剪辑。</span><span class="sxs-lookup"><span data-stu-id="54ff7-278">For this example, we are going to use the MRTK_Gem audio clip.</span></span>
    * <span data-ttu-id="54ff7-279">若要添加音频剪辑，只需将所需剪辑从 "项目" 面板拖动到 "AudioSource" PlayOneShot 字段。</span><span class="sxs-lookup"><span data-stu-id="54ff7-279">To add an audio clip, simply drag the clip you want from the project panel into the AudioSource.PlayOneShot field.</span></span>

    ![mrlearning-base-ch4-4-step5 .png](images/mrlearning-base-ch4-4-step5.png)

   <span data-ttu-id="54ff7-281">现在，当用户到达并接触八对象时，将播放 MRTK_Gem 音频轨。</span><span class="sxs-lookup"><span data-stu-id="54ff7-281">Now, when the user reaches out and touches the Octa object, the audio track MRTK_Gem will play.</span></span> <span data-ttu-id="54ff7-282">触摸时，手动交互触摸脚本还会调整对象的颜色。</span><span class="sxs-lookup"><span data-stu-id="54ff7-282">The Hand Interaction Touch script will also adjust the color of the object, when touched.</span></span>

## <a name="congratulations"></a><span data-ttu-id="54ff7-283">祝贺</span><span class="sxs-lookup"><span data-stu-id="54ff7-283">Congratulations</span></span>

<span data-ttu-id="54ff7-284">在本教程中，您学习了如何在网格集合中组织3D 对象，以及如何使用接近的交互（直接抓取、旋转和移动）来处理这些对象（使用 "注视" 光线或手写光线）。</span><span class="sxs-lookup"><span data-stu-id="54ff7-284">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="54ff7-285">还了解了如何在三维对象周围添加边界框，并了解了如何使用和自定义边界框中的 gizmos。</span><span class="sxs-lookup"><span data-stu-id="54ff7-285">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the gizmos on the bounding boxes.</span></span> <span data-ttu-id="54ff7-286">最后，你已了解如何在触摸对象时触发事件。</span><span class="sxs-lookup"><span data-stu-id="54ff7-286">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="54ff7-287">下一课： 6. 浏览高级输入选项</span><span class="sxs-lookup"><span data-stu-id="54ff7-287">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
