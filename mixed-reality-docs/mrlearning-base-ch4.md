---
title: 入门教程-5。 与三维对象交互
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 29a31f794cbcda4f0c77b4e6e2d0e3c2c91dcb8c
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702014"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="8f0df-104">5.与三维对象交互</span><span class="sxs-lookup"><span data-stu-id="8f0df-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="8f0df-105">在本教程中, 我们将了解基本的3D 内容和用户体验。</span><span class="sxs-lookup"><span data-stu-id="8f0df-105">In this tutorial, we learn about basic 3D content and user experience.</span></span> <span data-ttu-id="8f0df-106">我们将了解:</span><span class="sxs-lookup"><span data-stu-id="8f0df-106">We will learn about:</span></span> 
* <span data-ttu-id="8f0df-107">将三维对象组织为集合的一部分。</span><span class="sxs-lookup"><span data-stu-id="8f0df-107">Organizing 3D objects as part of a collection.</span></span>
* <span data-ttu-id="8f0df-108">基本操作的边界框。</span><span class="sxs-lookup"><span data-stu-id="8f0df-108">Bounding boxes for basic manipulation.</span></span>
* <span data-ttu-id="8f0df-109">近和远交互。</span><span class="sxs-lookup"><span data-stu-id="8f0df-109">Near and far interaction.</span></span>
* <span data-ttu-id="8f0df-110">通过手动跟踪触摸和抓取手势。</span><span class="sxs-lookup"><span data-stu-id="8f0df-110">Touch and grab gestures with hand tracking.</span></span> 

## <a name="objectives"></a><span data-ttu-id="8f0df-111">目标</span><span class="sxs-lookup"><span data-stu-id="8f0df-111">Objectives</span></span>

* <span data-ttu-id="8f0df-112">了解如何通过 MRTK 的网格对象集合来组织3D 内容</span><span class="sxs-lookup"><span data-stu-id="8f0df-112">Learn how to organize 3D content with MRTK's grid object collection</span></span>
* <span data-ttu-id="8f0df-113">实现边界框</span><span class="sxs-lookup"><span data-stu-id="8f0df-113">Implement bounding boxes</span></span>
* <span data-ttu-id="8f0df-114">为基本操作配置3D 对象--移动、旋转和缩放</span><span class="sxs-lookup"><span data-stu-id="8f0df-114">Configure 3D objects for basic manipulation--move, rotate, and scale</span></span>
* <span data-ttu-id="8f0df-115">探索近距和远距交互</span><span class="sxs-lookup"><span data-stu-id="8f0df-115">Explore near and far interaction</span></span>
* <span data-ttu-id="8f0df-116">了解其他手动跟踪手势, 如抓取和触摸</span><span class="sxs-lookup"><span data-stu-id="8f0df-116">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="instructions"></a><span data-ttu-id="8f0df-117">说明</span><span class="sxs-lookup"><span data-stu-id="8f0df-117">Instructions</span></span>

### <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="8f0df-118">在集合中组织 3D 对象</span><span class="sxs-lookup"><span data-stu-id="8f0df-118">Organizing 3D Objects in a Collection</span></span>

1. <span data-ttu-id="8f0df-119">右键单击层次结构, 然后选择 "创建空"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-119">Right click on your hierarchy and select, Create Empty.</span></span> <span data-ttu-id="8f0df-120">这会创建一个空游戏对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-120">This creates an empty game object.</span></span> <span data-ttu-id="8f0df-121">将其重命名为3DObjectCollection。</span><span class="sxs-lookup"><span data-stu-id="8f0df-121">Rename it to 3DObjectCollection.</span></span> <span data-ttu-id="8f0df-122">我们的所有 3D 对象将放入其中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-122">This is where we will put all of our 3D Objects.</span></span> <span data-ttu-id="8f0df-123">确保集合的位置设置为 x = 0，y = 0，z = 0。</span><span class="sxs-lookup"><span data-stu-id="8f0df-123">Make sure the collection’s positioning is set at x = 0, y = 0, and z = 0.</span></span>

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. <span data-ttu-id="8f0df-125">使用与在[学习](mrlearning-base-ch1.md)中概述的自定义包相同的说明导入 BaseModule 资产。</span><span class="sxs-lookup"><span data-stu-id="8f0df-125">Import BaseModule assets using the same instructions to import custom packages outlined in [Lesson1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="8f0df-126">本教程中使用的 BaseModule 资产包括3D 模块和其他有用的脚本。</span><span class="sxs-lookup"><span data-stu-id="8f0df-126">The BaseModule assets include 3D modules and other useful scripts that are used throughout this tutorial.</span></span> <span data-ttu-id="8f0df-127">可在此处找到 BaseModule Unity 包:<https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1></span><span class="sxs-lookup"><span data-stu-id="8f0df-127">The BaseModule Unity package can be found here: <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1></span></span>

3. <span data-ttu-id="8f0df-128">可根据旁边的蓝色立方体识别咖啡杯预制件。</span><span class="sxs-lookup"><span data-stu-id="8f0df-128">The coffee cup prefab can be recognized by a blue cube next to it.</span></span> <span data-ttu-id="8f0df-129">请勿选择蓝色立方体和小白色纸张, 因为这表示原始3D 模型而不是 prefab。)</span><span class="sxs-lookup"><span data-stu-id="8f0df-129">Do not select the coffee cup with the blue cube and small white paper because this denotes the original 3D model and not the prefab.)</span></span> 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. <span data-ttu-id="8f0df-131">将所选的 "咖啡杯" prefab 拖到步骤1中的 "3DObjectCollection 游戏" 对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-131">Drag the coffee cup prefab of your choice into the 3DObjectCollection game object from Step 1.</span></span> <span data-ttu-id="8f0df-132">现在，该咖啡杯是集合的子级。</span><span class="sxs-lookup"><span data-stu-id="8f0df-132">The coffee cup is now a child of the collection.</span></span>

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. <span data-ttu-id="8f0df-134">接下来，将更多的 3D 对象添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-134">Next, we'll add more 3D objects into our scene.</span></span> <span data-ttu-id="8f0df-135">下面是要在本示例中添加的对象列表。</span><span class="sxs-lookup"><span data-stu-id="8f0df-135">Below is a list of objects we are going to add in this example.</span></span> <span data-ttu-id="8f0df-136">添加对象时, 可能会发现它们以各种大小显示在场景中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-136">As you add the objects you might find that they appear in your scene in various sizes.</span></span> <span data-ttu-id="8f0df-137">调整检查器面板中 "转换" 设置下每个三维模型的比例。</span><span class="sxs-lookup"><span data-stu-id="8f0df-137">Adjust the scale of each 3D model under Transform Setting in the Inspector panel.</span></span> <span data-ttu-id="8f0df-138">下面列出了本示例中各个对象的建议调整大小。</span><span class="sxs-lookup"><span data-stu-id="8f0df-138">Recommended adjustments for this example are listed with the objects below.</span></span> <span data-ttu-id="8f0df-139">在 "项目" 面板的 "搜索" 框中搜索这些字词, 然后将3D 对象 prefab 拖动到类似于上一步的3DObjectCollection 对象中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-139">Search these words in the search box in your project panel and drag the 3D object prefab into the 3DObjectCollection object similar to the previous step.</span></span> <span data-ttu-id="8f0df-140">你将在资产 > BaseModuleAssets > 基本模块 Prototyping 中找到这些 prototyping 集合</span><span class="sxs-lookup"><span data-stu-id="8f0df-140">You will find these collections of prefabs in Assets>BaseModuleAssets>Base Module Prefabs</span></span>
- <span data-ttu-id="8f0df-141">搜索 TheModule_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="8f0df-141">Search for TheModule_BaseModuleIncomplete.</span></span> <span data-ttu-id="8f0df-142">将其拖到场景中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-142">Drag into scene.</span></span> <span data-ttu-id="8f0df-143">将坐标设置为 x = 0.03，y = 0.03，z = 0.03。</span><span class="sxs-lookup"><span data-stu-id="8f0df-143">Set the scale to x = 0.03, y = 0.03, z = 0.03.</span></span> 
- <span data-ttu-id="8f0df-144">搜索 Octa_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="8f0df-144">Search for Octa_BaseModuleIncomplete.</span></span> <span data-ttu-id="8f0df-145">将其拖到场景中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-145">Drag into scene.</span></span> <span data-ttu-id="8f0df-146">将坐标设置为 x = 0.13，</span><span class="sxs-lookup"><span data-stu-id="8f0df-146">Set the scale to x = 0.13.</span></span> <span data-ttu-id="8f0df-147">y = 0.13，z =0.13。</span><span class="sxs-lookup"><span data-stu-id="8f0df-147">y = 0.13, z =0.13.</span></span>
- <span data-ttu-id="8f0df-148">搜索 EarthCore_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="8f0df-148">Search for EarthCore_BaseModuleIncomplete.</span></span> <span data-ttu-id="8f0df-149">将其拖到场景中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-149">Drag into scene.</span></span> <span data-ttu-id="8f0df-150">将坐标设置为 x = 50.0，y = 50.0，z = 50.0。</span><span class="sxs-lookup"><span data-stu-id="8f0df-150">Set the scale to x = 50.0 y = 50.0, z = 50.0.</span></span>
- <span data-ttu-id="8f0df-151">搜索 Cheese_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="8f0df-151">Search for Cheese_BaseModuleIncomplete.</span></span> <span data-ttu-id="8f0df-152">将其拖到场景中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-152">Drag into scene.</span></span> <span data-ttu-id="8f0df-153">将坐标设置为 x = 0.05，y = 0.05，z = 0.05。</span><span class="sxs-lookup"><span data-stu-id="8f0df-153">Set the scale to x = 0.05, y = 0.05, z = 0.05.</span></span>
- <span data-ttu-id="8f0df-154">搜索 Model_Platonic_BaseModuleIncomplete。</span><span class="sxs-lookup"><span data-stu-id="8f0df-154">Search for Model_Platonic_BaseModuleIncomplete.</span></span> <span data-ttu-id="8f0df-155">将其拖到场景中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-155">Drag into scene.</span></span> <span data-ttu-id="8f0df-156">将坐标设置为 x = 0.13，y = 0.13，z = 0.13。</span><span class="sxs-lookup"><span data-stu-id="8f0df-156">Set the scale to x = 0.13, y = 0.13, z = 0.13.</span></span>

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. <span data-ttu-id="8f0df-158">将三个多维数据集添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-158">Add three cubes into your scene.</span></span> <span data-ttu-id="8f0df-159">右键单击 "3DObjectCollection" 对象, 选择 "3D 对象", 然后选择 "多维数据集"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-159">Right click the 3DObjectCollection object, select 3D Object, then select Cube.</span></span> <span data-ttu-id="8f0df-160">将坐标设置为 x = 0.14，y = 0.14，z = 0.14。</span><span class="sxs-lookup"><span data-stu-id="8f0df-160">Set the scale to x = 0.14, y = 0.14, and z = 0.14.</span></span> <span data-ttu-id="8f0df-161">重复此步骤两次, 以创建总计三个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8f0df-161">Repeat this step two additional times to create a total of three cubes.</span></span> <span data-ttu-id="8f0df-162">或者, 可以复制多维数据集两次, 共三个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8f0df-162">Alternatively, you can duplicate the cube twice for a total of three cubes.</span></span> <span data-ttu-id="8f0df-163">也可以选择使用“资产”>“基础模块资产”>“基础模块预制件”中三个已准备好的立方体预制件，并选择“GreenCube_BaseModuleIncomplete”、“BlueCube_BaseModuleIncomplete”和“OrangeCube_BaseModuleIncomplete”。</span><span class="sxs-lookup"><span data-stu-id="8f0df-163">You may also choose to use the three prepared cube prefabs from Assets>BaseModuleAssets>Base Module Prefabs and select GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete and OrangeCube_BaseModuleIncomplete.</span></span>

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. <span data-ttu-id="8f0df-165">参考[第 2 课](mrlearning-base-ch2.md)中所述的过程，使用 MRTK 的网格对象集合组织对象集合，以构成一个网格。</span><span class="sxs-lookup"><span data-stu-id="8f0df-165">Organize your collection of objects to form a grid using the procedure described in [Lesson 2](mrlearning-base-ch2.md) using the MRTK’s Grid Object Collection.</span></span> <span data-ttu-id="8f0df-166">请参考下图，其中通过一个示例演示了如何在 3x3 网格中配置对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-166">Refer to the image below to see an example of configuring the objects in a 3x3 grid.</span></span>

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

><span data-ttu-id="8f0df-168">注意:你可能会注意到, 某些对象处于中间中心, 如上图中的对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-168">Note: You might notice that some of the objects are off-center, such as the objects in the image above.</span></span> <span data-ttu-id="8f0df-169">这是因为，预制件或对象可能包含未对齐的子对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-169">This is because prefabs or objects may have child objects that are not aligned.</span></span> <span data-ttu-id="8f0df-170">请对对象位置或子对象位置进行任何必要的调整，以获得适当对齐的网格。</span><span class="sxs-lookup"><span data-stu-id="8f0df-170">Feel free to make any necessary adjustments to object positions or child object positions to achieve a well-aligned grid.</span></span>


### <a name="manipulating-3d-objects"></a><span data-ttu-id="8f0df-171">操作 3D 对象</span><span class="sxs-lookup"><span data-stu-id="8f0df-171">Manipulating 3D Objects</span></span>
1. <span data-ttu-id="8f0df-172">添加操作立方体的功能。</span><span class="sxs-lookup"><span data-stu-id="8f0df-172">Add the ability to manipulate a cube.</span></span> <span data-ttu-id="8f0df-173">若要添加操作3D 对象的功能, 请执行以下操作:</span><span class="sxs-lookup"><span data-stu-id="8f0df-173">To add the ability to manipulate 3D objects, do the following:</span></span>
-   <span data-ttu-id="8f0df-174">选择要在层次结构中操作的3D 对象, 即您的某个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8f0df-174">Select the 3D object you want to manipulate in your hierarchy, i.e., one of your cubes.</span></span>
-   <span data-ttu-id="8f0df-175">单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-175">Click Add Component.</span></span> 
-   <span data-ttu-id="8f0df-176">搜索操作。</span><span class="sxs-lookup"><span data-stu-id="8f0df-176">Search for manipulation.</span></span>
-   <span data-ttu-id="8f0df-177">选择 "操作处理程序"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-177">Select Manipulation Handler.</span></span>
-   <span data-ttu-id="8f0df-178">对3DObjectCollection 对象下的所有3D 对象重复此操作, 而不是3DObjectCollection 本身。</span><span class="sxs-lookup"><span data-stu-id="8f0df-178">Repeat for all 3D objects under the 3DObjectCollection object but not the 3DObjectCollection itself.</span></span>
-   <span data-ttu-id="8f0df-179">确保所有三维对象都具有碰撞器或盒碰撞器 (添加组件 > 框碰撞器)。</span><span class="sxs-lookup"><span data-stu-id="8f0df-179">Ensure all 3D objects have a collider or box collider (Add Component>Box Collider).</span></span>

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

><span data-ttu-id="8f0df-181">操作处理程序是一个组件, 可用于调整对象在操作时的行为方式的设置。</span><span class="sxs-lookup"><span data-stu-id="8f0df-181">The manipulation handler is a component that lets you adjust settings for how objects behave when  manipulated.</span></span> <span data-ttu-id="8f0df-182">这包括在特定轴上进行旋转、缩放、移动和约束移动。</span><span class="sxs-lookup"><span data-stu-id="8f0df-182">This includes rotation, scaling, moving, and constraining movement on a specific axis.</span></span> 

2. <span data-ttu-id="8f0df-183">请限制一个立方体，以便只能对它进行缩放。</span><span class="sxs-lookup"><span data-stu-id="8f0df-183">Restrict one cube so that it can only be scaled.</span></span> <span data-ttu-id="8f0df-184">选择3DObjectCollection 对象中的一个多维数据集。</span><span class="sxs-lookup"><span data-stu-id="8f0df-184">Select one cube in the 3DObjectCollection object.</span></span> <span data-ttu-id="8f0df-185">在 "检查器" 面板中, 在 "两种操作类型" 旁单击下拉菜单, 然后选择 "缩放"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-185">In the Inspector panel, next to Two Handed Manipulation Type, click the drop-down menu and select Scale.</span></span> <span data-ttu-id="8f0df-186">这样，用户只能更改该立方体的大小。</span><span class="sxs-lookup"><span data-stu-id="8f0df-186">This makes it so that the user can only change the cube’s size.</span></span>

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. <span data-ttu-id="8f0df-188">更改每个立方体的颜色，以便可以区分它们。</span><span class="sxs-lookup"><span data-stu-id="8f0df-188">Change the color of each cube so that we can differentiate between them.</span></span> 
-   <span data-ttu-id="8f0df-189">请访问 "项目" 面板并向下滚动, 直到看到 "MixedRealityToolkit", 然后选择它。</span><span class="sxs-lookup"><span data-stu-id="8f0df-189">Go to the Project panel and scroll down until you see MixedRealityToolkit.SDK then select it.</span></span>
-   <span data-ttu-id="8f0df-190">选择 "标准资产" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="8f0df-190">Select the Standard Assets folder.</span></span>
-   <span data-ttu-id="8f0df-191">单击 "材料" 文件夹。</span><span class="sxs-lookup"><span data-stu-id="8f0df-191">Click on the Materials folder.</span></span>
-   <span data-ttu-id="8f0df-192">将不同的材料拖放到每个立方体上。</span><span class="sxs-lookup"><span data-stu-id="8f0df-192">Drag a different material onto each of your cubes.</span></span> 

><span data-ttu-id="8f0df-193">注意:可为立方体选择任意颜色。</span><span class="sxs-lookup"><span data-stu-id="8f0df-193">Note: You can choose any color for your cubes.</span></span> <span data-ttu-id="8f0df-194">对于我们的示例, 我们将使用 glowingcyan、glowingorange 和绿色。</span><span class="sxs-lookup"><span data-stu-id="8f0df-194">For our example, we are going to use glowingcyan, glowingorange, and green.</span></span> <span data-ttu-id="8f0df-195">请随意尝试不同的颜色。</span><span class="sxs-lookup"><span data-stu-id="8f0df-195">Feel free to experiment with different colors.</span></span> <span data-ttu-id="8f0df-196">若要将颜色添加到多维数据集, 请单击想要更改的多维数据集, 然后将该材料拖到多维数据集的 "检查器" 面板中的 "网格呈现器" 材料字段。</span><span class="sxs-lookup"><span data-stu-id="8f0df-196">To add the color to the cube, click the cube you want to change, then drag the material to the mesh renderer's material field in the cube's Inspector panel.</span></span> 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. <span data-ttu-id="8f0df-198">选择3DObjectCollection 对象中的其他多维数据集, 然后将其移动限制为固定距离。</span><span class="sxs-lookup"><span data-stu-id="8f0df-198">Select another cube in the 3DObjectCollection object and make it so that its movement is constrained to a fixed distance from the head.</span></span> <span data-ttu-id="8f0df-199">为此, 请在 "移动" 标签上的 "约束" 右侧单击下拉菜单, 然后选择 "修复距离"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-199">To do this, to the right of Constraint on Movement label, click on the drop-down menu and select Fix Distance from the Head.</span></span> <span data-ttu-id="8f0df-200">这样，用户只能在其视野范围中移动该立方体。</span><span class="sxs-lookup"><span data-stu-id="8f0df-200">This makes it so that the user can only move the cube within their field of vision.</span></span> 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

<span data-ttu-id="8f0df-202">接下来的几个步骤的目标是启用抓取并与我们的3D 对象进行交互, 并应用不同的操作设置。</span><span class="sxs-lookup"><span data-stu-id="8f0df-202">The goal of the next few steps is to enable grabbing and interacting with our 3D objects and applying different manipulation settings.</span></span>

5. <span data-ttu-id="8f0df-203">选择奶酪对象, 并单击 "检查器" 面板中的 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-203">Select the Cheese object, and click Add Component from the Inspector panel.</span></span> 

6. <span data-ttu-id="8f0df-204">在搜索框中搜索近交互 Grabbable, 并选择该脚本。</span><span class="sxs-lookup"><span data-stu-id="8f0df-204">Search in the search box for Near Interaction Grabbable, and select the script.</span></span> <span data-ttu-id="8f0df-205">此组件使用户可以通过跟踪的手访问和吸引对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-205">This component enables users reach out and grab objects with tracked hands.</span></span> <span data-ttu-id="8f0df-206">对象也可以从远处操作, 除非在下图中以绿色圆圈表示的 "允许远操作" 复选框未被选中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-206">Objects can also be manipulated from a distance, unless the Allow Far Manipulation checkbox is unchecked as denoted by green circle in image below.</span></span>

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. <span data-ttu-id="8f0df-208">通过对这些对象重复步骤5和步骤 6, 将近交互 Grabbable 添加到八对象、Platonic 对象、地球核心、农历和咖啡杯。</span><span class="sxs-lookup"><span data-stu-id="8f0df-208">Add Near Interaction Grabbable to the Octa object, Platonic object, Earth Core, Lunar Module, and Coffee Cup by repeating Steps 5 and 6 on those objects.</span></span>

8. <span data-ttu-id="8f0df-209">从八面体对象中删除远距操作功能。</span><span class="sxs-lookup"><span data-stu-id="8f0df-209">Remove the ability of far manipulation from the Octa object.</span></span> <span data-ttu-id="8f0df-210">为此, 请在层次结构中选择 "八", 并取消选中 "允许远端操作" 复选框 (由绿色圆圈标记)。</span><span class="sxs-lookup"><span data-stu-id="8f0df-210">To do this, select the Octa in the hierarchy, and uncheck the Allow far Manipulation checkbox (marked by a green circle).</span></span> <span data-ttu-id="8f0df-211">这样，用户只能使用跟踪手来直接与八面体交互。</span><span class="sxs-lookup"><span data-stu-id="8f0df-211">This makes it so that users can only interact with the octa directly using tracked hands.</span></span>

><span data-ttu-id="8f0df-212">注意:有关操作处理程序组件及其相关设置的完整文档，请参阅 [MRTK 文档](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)。</span><span class="sxs-lookup"><span data-stu-id="8f0df-212">Note: For the full documentation of the manipulation handler component and it's associated settings, please refer to the [MRTK Documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).</span></span>

9. <span data-ttu-id="8f0df-213">确保将近交互 Grabbable 组件添加到了地球核心、农历模块和咖啡杯上 (请参见步骤 7)。</span><span class="sxs-lookup"><span data-stu-id="8f0df-213">Ensure that the Near Interaction Grabbable component has been added to the earth core, the lunar module and the coffee cup (see Step 7).</span></span>

10. <span data-ttu-id="8f0df-214">对于农历模块, 请更改操作处理程序设置, 以使其围绕对象中心围绕近和远交互进行旋转, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8f0df-214">For the lunar module, change the Manipulation Handler settings so that it rotates about the object's center for both near and far interaction as shown in the image below.</span></span>

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

<span data-ttu-id="8f0df-216">11：对于地球核心, 将版本行为更改为 "无"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-216">11: For the earth core, change the release behavior to nothing.</span></span> <span data-ttu-id="8f0df-217">这样做是为了使地球核心从用户的抓住中释放出来, 而不会继续移动。</span><span class="sxs-lookup"><span data-stu-id="8f0df-217">This makes it so that once the earth core is released from the user's grasp, it doesn’t continue to move.</span></span> 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> <span data-ttu-id="8f0df-219">注意:在创建可投射的球等场景中，可以使用此设置。</span><span class="sxs-lookup"><span data-stu-id="8f0df-219">Note: This setting is useful for scenarios such as creating a ball that you can throw.</span></span> <span data-ttu-id="8f0df-220">通过保持速度和角度速度, 使其成为一种球后, 它将继续以其释放速度的速度移动, 类似于物理球的行为方式。</span><span class="sxs-lookup"><span data-stu-id="8f0df-220">Keeping the velocity and the angular velocity makes it so that once the ball is released, it will continue to move at the velocity it was released at, similar to how a physical ball would behave.</span></span>

### <a name="adding-bounding-boxes"></a><span data-ttu-id="8f0df-221">添加边界框</span><span class="sxs-lookup"><span data-stu-id="8f0df-221">Adding Bounding Boxes</span></span>
<span data-ttu-id="8f0df-222">使用边界框可以更方便、更直观地单手操作对象，它支持定向操作（近距交互）和基于光线的操作（远距交互）。边界框提供可用于沿特定轴缩放和旋转对象的句柄。</span><span class="sxs-lookup"><span data-stu-id="8f0df-222">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both direct manipulation (near interaction) and ray-based manipulation (far interaction.) Bounding boxes provide handles that can be grabbed for scaling and rotating objects along a specific axis.</span></span>
><span data-ttu-id="8f0df-223">注意:在将边界框添加到对象之前, 您首先需要在该对象上创建一个碰撞器 (例如, 盒碰撞器), 就像我们在本课前面介绍的那样。</span><span class="sxs-lookup"><span data-stu-id="8f0df-223">Note: Before you can add a bounding box to an object, you first need to have a collider on the object (e.g., a box collider), as we did previously in this lesson.</span></span> <span data-ttu-id="8f0df-224">可通过以下方式添加碰撞体：选择该对象，然后在该对象的检查器面板中选择“添加组件”>“盒碰撞体”。</span><span class="sxs-lookup"><span data-stu-id="8f0df-224">Colliders can be added by selecting the object, and in the object's inspector panel selecting Add Component>Box Collider.</span></span>
>

1. <span data-ttu-id="8f0df-225">如果地球核心对象尚不存在, 请将其添加到地球核心对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-225">Add a box collider to the Earth Core object if one does not already exist.</span></span> <span data-ttu-id="8f0df-226">如果根据给定的说明使用基本模块资产文件夹中提供的 prefab, 则不需要使用框碰撞器和设置。</span><span class="sxs-lookup"><span data-stu-id="8f0df-226">The box collider and setup are not required if using the prefab provided in the Base Module Assets folder per the instructions given.</span></span> <span data-ttu-id="8f0df-227">对于地球核心, 我们将 box 碰撞器添加到了地球核心下的、node_id30 的对象中, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8f0df-227">In the case of the earth core, we added the box collider to the, node_id30, object underneath the earth core, as shown in the image below.</span></span> <span data-ttu-id="8f0df-228">从对象的 "检查器" 选项卡中选择 "node_id30", 单击 "添加组件", 然后搜索 box 碰撞器。</span><span class="sxs-lookup"><span data-stu-id="8f0df-228">Select node_id30 from the object's Inspector tab, click Add Component, and search for box collider.</span></span> 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> <span data-ttu-id="8f0df-231">注意:请确保将框碰撞器的大小设置为不太大或太小。</span><span class="sxs-lookup"><span data-stu-id="8f0df-231">Note: Make sure that you size the box collider so that it’s not too big or too small.</span></span> <span data-ttu-id="8f0df-232">其大小应与围绕它的对象（在本示例中为地核）大致相同。</span><span class="sxs-lookup"><span data-stu-id="8f0df-232">It should be roughly the same size as the object it’s surrounding (in this example, the earth core).</span></span> <span data-ttu-id="8f0df-233">通过选择框碰撞器中的 "编辑碰撞器" 选项, 根据需要调整框碰撞器。</span><span class="sxs-lookup"><span data-stu-id="8f0df-233">Adjust the box collider as needed by selecting the Edit Collider option in the box collider.</span></span> <span data-ttu-id="8f0df-234">您可以更改 x、y 和 z 值, 也可以在编辑器场景窗口中拖动边界框处理程序。</span><span class="sxs-lookup"><span data-stu-id="8f0df-234">You can either changing the x, y, and z values or drag the bounding box handlers in the Editor Scene window.</span></span> 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. <span data-ttu-id="8f0df-236">将边界框添加到地球核心的 node_id30 对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-236">Add a bounding box to the earth core's node_id30 object.</span></span> <span data-ttu-id="8f0df-237">为此, 请从 "3DObjectCollection" 中选择 "node_id30" 对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-237">To do this, select the node_id30 object from the 3DObjectCollection.</span></span> <span data-ttu-id="8f0df-238">在 "检查器" 选项卡中, 单击 "添加组件", 然后搜索 "边界框"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-238">In the inspector tab, click Add Component, and search for bounding box.</span></span> <span data-ttu-id="8f0df-239">确保边界框、盒碰撞体和操作脚本（操作处理程序、近距交互可抓取对象）都在同一个游戏对象中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-239">Ensure that the bounding box, box collider, and manipulation scripts (manipulation handler, near interaction grabbable) are all on the same game object.</span></span>

3.  <span data-ttu-id="8f0df-240">在 "边界框的行为" 部分中, 从 "激活" 下拉列表中选择 "开始时激活"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-240">In the bounding box's Behavior section, select Activate on Start from the Activation drop-down list.</span></span> <span data-ttu-id="8f0df-241">若要查看有关各个激活选项和其他边界框选项的更多详细信息，请参阅 [MRTK 的边界框文档](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)</span><span class="sxs-lookup"><span data-stu-id="8f0df-241">To review additional details regarding the various activation options and other bounding box options, please see the [MRTK's bounding box documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)</span></span>

   

   <span data-ttu-id="8f0df-242">*在接下来的几个步骤中, 我们还将通过以下方式更改边界框的显示方式: 调整默认的框材料、在其被抓取时的材料以及角部和侧图柄的可视化。* MRTK 包含多个用于自定义边界框的选项。</span><span class="sxs-lookup"><span data-stu-id="8f0df-242">*In the next few steps, we will also change how the bounding box looks by adjusting the default box material, the material while it’s being grabbed as well as the visualization of the corner and side handles. The MRTK contains several options to customize the bounding box.*</span></span>

4. <span data-ttu-id="8f0df-243">在 "项目" 面板中搜索 "boundingbox", 并在搜索结果中看到一个蓝色球体表示的材料列表, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8f0df-243">In the Project panel, search for boundingbox, and you’ll see a list of materials denoted by a blue sphere in the search results as shown in the image below.</span></span> 

5. <span data-ttu-id="8f0df-244">将 boundingbox 材料拖动到边界框组件上的盒材料槽。</span><span class="sxs-lookup"><span data-stu-id="8f0df-244">Drag the boundingbox material into the box material slot on the bounding box component.</span></span> <span data-ttu-id="8f0df-245">同时, 抓住 boundingboxgrabbed 材料, 并将其放在边界框组件上的 "将材料槽" 框中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-245">Also grab the boundingboxgrabbed material, and put that in the box grabbed material slot on the bounding box component.</span></span>

6. <span data-ttu-id="8f0df-246">将 MRTK_BoundingBox_ScaleWidget prefab 拖到边界框组件上的刻度控点 prefab 槽。</span><span class="sxs-lookup"><span data-stu-id="8f0df-246">Drag the MRTK_BoundingBox_ScaleWidget prefab into the scale handle prefab slot on the bounding box component.</span></span> 

7. <span data-ttu-id="8f0df-247">将 MRTK_BoundingBox_RotateWidget prefab 拖到 "捆绑箱" 组件上的旋转控点槽。</span><span class="sxs-lookup"><span data-stu-id="8f0df-247">Drag the MRTK_BoundingBox_RotateWidget prefab into the rotation handle slot on the bonding box component.</span></span>

![Lesson4 Chapter3 Step4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. <span data-ttu-id="8f0df-249">确保边界框针对适当的对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-249">Make sure the bounding box is targeting the right object.</span></span> <span data-ttu-id="8f0df-250">在边界框组件中, 有目标对象和边界替代脚本。</span><span class="sxs-lookup"><span data-stu-id="8f0df-250">In the bounding box component, there is the target object and bounds override scripts.</span></span> <span data-ttu-id="8f0df-251">请确保将边界框环绕的对象拖放到这两个槽中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-251">Make sure to drag the object that has the bounding box around it to both of these slots.</span></span> <span data-ttu-id="8f0df-252">在此示例中, 将 node_id30 对象拖到这两个槽, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8f0df-252">In this example, drag the node_id30 object to both these slots as shown in the image below.</span></span>

> <span data-ttu-id="8f0df-253">启动或播放应用程序时, 对象将被蓝色框架括起来。</span><span class="sxs-lookup"><span data-stu-id="8f0df-253">When you start or play the application, your object will be surrounded by a blue frame.</span></span> <span data-ttu-id="8f0df-254">可以放心拖动该框的四角，以调整对象的大小。</span><span class="sxs-lookup"><span data-stu-id="8f0df-254">You’re welcome to drag the corners of that frame to resize the object.</span></span> <span data-ttu-id="8f0df-255">如果希望缩放控点更大且更可见, 则建议使用默认边界框设置 (避免步骤4到7。)</span><span class="sxs-lookup"><span data-stu-id="8f0df-255">If you want the scaling handles and the rotation handles to be larger and more visible, it is recommend using the default bounding box settings (avoiding Steps 4 -through 7.)</span></span> 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. <span data-ttu-id="8f0df-257">若要返回到默认边界框可视化效果, 请在边界框的对象的检查器面板中, 选择旋转控点 prefab 并按 Delete。</span><span class="sxs-lookup"><span data-stu-id="8f0df-257">To return to the default bounding box visualization, in the Inspector panel of the bounding box's object, select the rotation handle prefab and press Delete.</span></span> <span data-ttu-id="8f0df-258">你将看到与下图类似的边界框可视化。</span><span class="sxs-lookup"><span data-stu-id="8f0df-258">You will see a bounding box visualization similar to the image below.</span></span> <span data-ttu-id="8f0df-259">注意：边界框可视化效果仅在游戏模式下显示。</span><span class="sxs-lookup"><span data-stu-id="8f0df-259">Note: the bounding box visualizations only appears when in play mode.</span></span>

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a><span data-ttu-id="8f0df-261">添加触摸效果</span><span class="sxs-lookup"><span data-stu-id="8f0df-261">Adding touch effects</span></span>
<span data-ttu-id="8f0df-262">本示例将在用手触摸某个对象时播放一段音效。</span><span class="sxs-lookup"><span data-stu-id="8f0df-262">In this example, we are going to play a sound effect when you touch an object with your hand.</span></span>

1. <span data-ttu-id="8f0df-263">将音频源组件添加到游戏对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-263">Add an audio source component to your game object.</span></span> <span data-ttu-id="8f0df-264">选择场景层次结构中的八对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-264">Select the Octa object in your scene hierarchy.</span></span> <span data-ttu-id="8f0df-265">在检查器面板中, 单击 "添加组件" 按钮, 搜索并选择 "音频源"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-265">In the inspector panel, click the Add Component button, search for and select audio source.</span></span> <span data-ttu-id="8f0df-266">在稍后的步骤中，我们将使用此音频源播放音效。</span><span class="sxs-lookup"><span data-stu-id="8f0df-266">We’ll use this audio source to play a sound effect in a later step.</span></span> 

><span data-ttu-id="8f0df-267">注意:确保八对象上有一个框碰撞器。</span><span class="sxs-lookup"><span data-stu-id="8f0df-267">Note: Ensure that the Octa object has a box collider on it.</span></span>

2. <span data-ttu-id="8f0df-268">添加 Near 交互可触摸组件。</span><span class="sxs-lookup"><span data-stu-id="8f0df-268">Add the Near Interaction Touchable component.</span></span> <span data-ttu-id="8f0df-269">单击 "检查器" 面板中的 "添加组件" 按钮, 然后搜索 near 交互可触摸。</span><span class="sxs-lookup"><span data-stu-id="8f0df-269">Click the Add Component button in the Inspector panel, and search for near interaction touchable.</span></span> <span data-ttu-id="8f0df-270">选择该对象以将它添加到组件。</span><span class="sxs-lookup"><span data-stu-id="8f0df-270">Select it to add the component.</span></span> 

><span data-ttu-id="8f0df-271">注意:以前, 我们添加了近交互 grabbable。</span><span class="sxs-lookup"><span data-stu-id="8f0df-271">Note: Previously, we added near interaction grabbable.</span></span> <span data-ttu-id="8f0df-272">此交互和近交互可触摸之间的区别在于, grabbable 交互适用于要进行抓取和交互的对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-272">The difference between this and near interaction touchable is that the grabbable interaction is intended for an object to be grabbed and interacted with.</span></span> <span data-ttu-id="8f0df-273">可触摸组件适用于要接触的对象。</span><span class="sxs-lookup"><span data-stu-id="8f0df-273">The touchable component is intended for the object to be touched.</span></span> <span data-ttu-id="8f0df-274">可以结合使用这两个组件以实现组合式交互。</span><span class="sxs-lookup"><span data-stu-id="8f0df-274">Both components can be used together for a combination of interactions.</span></span>

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. <span data-ttu-id="8f0df-276">添加手交互触摸脚本。</span><span class="sxs-lookup"><span data-stu-id="8f0df-276">Add in the Hand Interaction Touch script.</span></span> <span data-ttu-id="8f0df-277">请注意, 此脚本包含在作为此演示的一部分导入的 Unity 场景中, 并不包含在原始 MRTK 中。</span><span class="sxs-lookup"><span data-stu-id="8f0df-277">Note that this script is included with the Unity scene you imported as part of this demo, and it is not included in the original MRTK.</span></span> <span data-ttu-id="8f0df-278">与上一步一样, 单击 "添加组件", 然后搜索 "手交互触摸" 进行添加。</span><span class="sxs-lookup"><span data-stu-id="8f0df-278">Just like the previous step, click Add Component, and search for hand interaction touch to add it.</span></span>

><span data-ttu-id="8f0df-279">请注意, 此脚本有三个选项:</span><span class="sxs-lookup"><span data-stu-id="8f0df-279">Notice that you have three options with the script:</span></span> 

>   - <span data-ttu-id="8f0df-280">On Touch 完成:触摸并释放对象时触发</span><span class="sxs-lookup"><span data-stu-id="8f0df-280">On Touch Completed: Triggers when you touch and release the object</span></span>
>   - <span data-ttu-id="8f0df-281">开始时:接触对象时触发</span><span class="sxs-lookup"><span data-stu-id="8f0df-281">On Touch Started: Triggers when the object is touched</span></span>
>   - <span data-ttu-id="8f0df-282">更新时:在您的手中触摸对象时定期触发</span><span class="sxs-lookup"><span data-stu-id="8f0df-282">On Touch Updated: Triggers periodically while your hand is touching the object</span></span>

>   <span data-ttu-id="8f0df-283">在此示例中, 我们将使用 "按下开始使用" 设置。</span><span class="sxs-lookup"><span data-stu-id="8f0df-283">For this example, we will be working with the On Touch Started setting.</span></span>

4. <span data-ttu-id="8f0df-284">单击 "按下 Touch 开始" 选项上的 "+" 按钮, 如下图所示。</span><span class="sxs-lookup"><span data-stu-id="8f0df-284">Click the + button on the On Touch Started option as shown in the image below.</span></span> <span data-ttu-id="8f0df-285">将八对象拖到空字段。</span><span class="sxs-lookup"><span data-stu-id="8f0df-285">Drag the Octa object into the empty field.</span></span> 

5. <span data-ttu-id="8f0df-286">在未显示 "函数 (位于下图中的绿色矩形上方)" 的下拉框中, 选择 "AudioSource-> PlayOneShot"。</span><span class="sxs-lookup"><span data-stu-id="8f0df-286">In the drop-down that says No Function (above green rectangle in the image below), select AudioSource->PlayOneShot.</span></span> <span data-ttu-id="8f0df-287">使用以下概念将一个音频剪辑添加到此字段：</span><span class="sxs-lookup"><span data-stu-id="8f0df-287">We will add an audio clip to this field using the concepts below:</span></span>

   - <span data-ttu-id="8f0df-288">MRTK 提供了一个简短的音频剪辑列表。</span><span class="sxs-lookup"><span data-stu-id="8f0df-288">The MRTK does provide a small list of audio clips.</span></span> <span data-ttu-id="8f0df-289">请在项目面板中随意浏览这些剪辑。</span><span class="sxs-lookup"><span data-stu-id="8f0df-289">Feel free to explore these in your project panel.</span></span> <span data-ttu-id="8f0df-290">你将在 MixedRealityToolkit 文件夹下找到它们, 然后在 "标准资产" 文件夹下找到。</span><span class="sxs-lookup"><span data-stu-id="8f0df-290">You will find them under the MixedRealityToolkit.SDK folder and then the Standard Assets folder.</span></span> <span data-ttu-id="8f0df-291">此时会显示音频文件夹, 其中包含所有音频剪辑。</span><span class="sxs-lookup"><span data-stu-id="8f0df-291">There you will see an Audio folder where all the audio clips are.</span></span>
   - <span data-ttu-id="8f0df-292">在此示例中, 我们将使用 MRTK_Gem 音频剪辑。</span><span class="sxs-lookup"><span data-stu-id="8f0df-292">For this example, we are going to use the MRTK_Gem audio clip.</span></span> 
   - <span data-ttu-id="8f0df-293">若要添加音频剪辑，只需将项目面板中所需的剪辑拖入检查器面板中的 AudioSource.PlayOneShot（在以上示例中带有绿框标记）。</span><span class="sxs-lookup"><span data-stu-id="8f0df-293">To add an audio clip, simply drag the clip you want from the project panel into the AudioSource.PlayOneShot (marked by green box in the example above) in the inspector panel.</span></span>

   <span data-ttu-id="8f0df-294">现在, 当用户到达并触及八对象时, 将播放音频轨 MRTK_Gem。</span><span class="sxs-lookup"><span data-stu-id="8f0df-294">Now when the user reaches out and touches the Octa object, the audio track MRTK_Gem will play.</span></span> <span data-ttu-id="8f0df-295">触摸时, 手动交互触摸脚本还会调整对象的颜色。</span><span class="sxs-lookup"><span data-stu-id="8f0df-295">The Hand Interaction Touch script will also adjust the color of the object when touched.</span></span> 

![Lesson4 Chapter4 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

## <a name="congratulations"></a><span data-ttu-id="8f0df-297">祝贺</span><span class="sxs-lookup"><span data-stu-id="8f0df-297">Congratulations</span></span> 
<span data-ttu-id="8f0df-298">在本教程中, 您学习了如何在网格集合中组织3D 对象, 以及如何使用接近的交互 (直接捕获到手) 和远距离交互 (使用看片或手写光线) 来操作三维对象 (缩放、旋转和移动)。</span><span class="sxs-lookup"><span data-stu-id="8f0df-298">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate 3D objects  (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="8f0df-299">还了解了如何在三维对象周围添加边界框, 并了解了如何使用和自定义边界框中的 gizmos。</span><span class="sxs-lookup"><span data-stu-id="8f0df-299">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the gizmos on the bounding boxes.</span></span> <span data-ttu-id="8f0df-300">最后，你已了解如何在触摸对象时触发事件。</span><span class="sxs-lookup"><span data-stu-id="8f0df-300">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="8f0df-301">下一课：6.探索高级输入选项</span><span class="sxs-lookup"><span data-stu-id="8f0df-301">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)

