---
title: 入门教程 - 5. 与 3D 对象交互
description: 了解基本的3D 内容和用户体验，例如，如何组织 3D 对象，以及如何使用边界框执行基本操作。
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 65bcef6a7c10450816d7a928302b0b266b132f0f
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362071"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="cc296-105">5.与 3D 对象交互</span><span class="sxs-lookup"><span data-stu-id="cc296-105">5. Interacting with 3D objects</span></span>

<span data-ttu-id="cc296-106">本教程介绍基本的 3D 内容和用户体验，例如，将 3D 对象组织为集合的一部分、用于执行基本操作的边界框、近距和远距交互，以及结合手动跟踪的触摸和抓取手势。</span><span class="sxs-lookup"><span data-stu-id="cc296-106">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="cc296-107">目标</span><span class="sxs-lookup"><span data-stu-id="cc296-107">Objectives</span></span>

* <span data-ttu-id="cc296-108">创建用于其他学习目标的 3D 对象面板</span><span class="sxs-lookup"><span data-stu-id="cc296-108">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="cc296-109">实现边界框</span><span class="sxs-lookup"><span data-stu-id="cc296-109">Implement bounding boxes</span></span>
* <span data-ttu-id="cc296-110">配置用于基本操作（例如移动、旋转和缩放）的 3D 对象</span><span class="sxs-lookup"><span data-stu-id="cc296-110">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="cc296-111">探索近距和远距交互</span><span class="sxs-lookup"><span data-stu-id="cc296-111">Explore near and far interaction</span></span>
* <span data-ttu-id="cc296-112">了解其他手动跟踪手势，例如抓取和触摸</span><span class="sxs-lookup"><span data-stu-id="cc296-112">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="cc296-113">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="cc296-113">Importing the tutorial assets</span></span>

<span data-ttu-id="cc296-114">下载并导入 Unity 自定义包：</span><span class="sxs-lookup"><span data-stu-id="cc296-114">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="cc296-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cc296-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

<span data-ttu-id="cc296-116">导入教程资产后，“项目”窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="cc296-116">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="cc296-118">有关如何导入 Unity 自定义包的提示，可参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)中的说明。</span><span class="sxs-lookup"><span data-stu-id="cc296-118">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="cc296-119">整理场景视图</span><span class="sxs-lookup"><span data-stu-id="cc296-119">Decluttering the scene view</span></span>

<span data-ttu-id="cc296-120">为了更轻松地在场景中操作，请单击“Cube”和“ButtonCollection”对象左侧的**眼睛**图标，将这些对象的**场景可见性**设置为关闭。  </span><span class="sxs-lookup"><span data-stu-id="cc296-120">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="cc296-121">这会在“场景”窗口中隐藏这些对象，但在游戏中不会改变其可见性：</span><span class="sxs-lookup"><span data-stu-id="cc296-121">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="cc296-123">若要详细了解“场景可见性”控件以及如何使用它们来优化场景视图和工作流，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">场景可见性</a>文档。</span><span class="sxs-lookup"><span data-stu-id="cc296-123">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="cc296-124">在集合中组织 3D 对象</span><span class="sxs-lookup"><span data-stu-id="cc296-124">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="cc296-125">在本部分，你将创建 3D 对象的面板。在本教程的后续部分，你将使用此面板来探索与 3D 对象交互的各种方式。</span><span class="sxs-lookup"><span data-stu-id="cc296-125">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="cc296-126">具体而言，要将 3D 对象配置为定位在 3x3 网格中。</span><span class="sxs-lookup"><span data-stu-id="cc296-126">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="cc296-127">要执行的主要步骤类似于[创建按钮面板](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)，包括：</span><span class="sxs-lookup"><span data-stu-id="cc296-127">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="cc296-128">将 3D 对象设为父对象的父级</span><span class="sxs-lookup"><span data-stu-id="cc296-128">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="cc296-129">添加并配置“网格对象集合(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="cc296-129">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="cc296-130">1.将 3D 对象设为父对象的父级</span><span class="sxs-lookup"><span data-stu-id="cc296-130">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="cc296-131">在“层次结构”窗口中**创建一个空对象**，为其指定适当的名称（例如 **3DObjectCollection**），并将其定位在适当的位置，例如 X = 0，Y = -0.2，Z = 2。</span><span class="sxs-lookup"><span data-stu-id="cc296-131">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="cc296-132">在“项目”窗口中，导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件”，然后将以下预制件设为 **3DObjectCollection** 的**父级**：   </span><span class="sxs-lookup"><span data-stu-id="cc296-132">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="cc296-133">Cheese</span><span class="sxs-lookup"><span data-stu-id="cc296-133">Cheese</span></span>
* <span data-ttu-id="cc296-134">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="cc296-134">CoffeeCup</span></span>
* <span data-ttu-id="cc296-135">EarthCore</span><span class="sxs-lookup"><span data-stu-id="cc296-135">EarthCore</span></span>
* <span data-ttu-id="cc296-136">Octa</span><span class="sxs-lookup"><span data-stu-id="cc296-136">Octa</span></span>
* <span data-ttu-id="cc296-137">Platonic</span><span class="sxs-lookup"><span data-stu-id="cc296-137">Platonic</span></span>
* <span data-ttu-id="cc296-138">TheModule</span><span class="sxs-lookup"><span data-stu-id="cc296-138">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="cc296-140">在“层次结构”窗口中，**创建三个立方体**作为 **3DObjectCollection** 的子对象，并将其变换**标度**设置为 X = 0.15，Y = 0.15，Z = 0.15：</span><span class="sxs-lookup"><span data-stu-id="cc296-140">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="cc296-142">有关如何执行上述步骤的提示，可参阅[创建用户界面并配置混合现实工具包](mrlearning-base-ch2.md)教程。</span><span class="sxs-lookup"><span data-stu-id="cc296-142">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="cc296-143">重新定位立方体，以便可以看到每个立方体：</span><span class="sxs-lookup"><span data-stu-id="cc296-143">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="cc296-145">在“项目”窗口中，导航到“资产” > “MixedRealityToolkit.SDK” > “StandardAssets” > “材料”查看 MRTK 随附的材料。    </span><span class="sxs-lookup"><span data-stu-id="cc296-145">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="cc296-146">单击某个合适的材料并将其拖放到每个立方体的网格渲染器“材料”元素 0 属性，例如：  </span><span class="sxs-lookup"><span data-stu-id="cc296-146">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="cc296-147">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="cc296-147">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="cc296-148">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="cc296-148">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="cc296-149">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="cc296-149">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="cc296-151">2.添加并配置“网格对象集合(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="cc296-151">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="cc296-152">将“网格对象集合(脚本)”组件添加到“3DObjectCollection”对象，并按如下所述配置该组件：  </span><span class="sxs-lookup"><span data-stu-id="cc296-152">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="cc296-153">将“排序类型”更改为“子级顺序”，确保按照子对象在父对象下的放置顺序对子对象进行排序  </span><span class="sxs-lookup"><span data-stu-id="cc296-153">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="cc296-154">然后单击“更新集合”按钮以应用新配置： </span><span class="sxs-lookup"><span data-stu-id="cc296-154">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="cc296-156">操作 3D 对象</span><span class="sxs-lookup"><span data-stu-id="cc296-156">Manipulating 3D objects</span></span>

<span data-ttu-id="cc296-157">在本部分，你将添加所需的功能，以便在上一部分创建的面板中操作所有 3D 对象。</span><span class="sxs-lookup"><span data-stu-id="cc296-157">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="cc296-158">此外，对于预制件对象，可让用户使用跟踪手来接触和抓取这些对象。</span><span class="sxs-lookup"><span data-stu-id="cc296-158">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="cc296-159">然后，探索一些可应用于对象的操作行为。</span><span class="sxs-lookup"><span data-stu-id="cc296-159">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="cc296-160">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="cc296-160">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="cc296-161">将“操作处理程序(脚本)”组件添加到所有对象</span><span class="sxs-lookup"><span data-stu-id="cc296-161">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="cc296-162">将“近距交互可抓取对象(脚本)”组件添加到预制件对象</span><span class="sxs-lookup"><span data-stu-id="cc296-162">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="cc296-163">配置“操作处理程序(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="cc296-163">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc296-164">若要**操作某个对象**，该对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="cc296-164">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="cc296-165">“碰撞体”组件，例如盒碰撞体 </span><span class="sxs-lookup"><span data-stu-id="cc296-165">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="cc296-166">“操作处理程序(脚本)”组件 </span><span class="sxs-lookup"><span data-stu-id="cc296-166">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="cc296-167">若要使用跟踪手**操作**和**抓取某个对象**，该对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="cc296-167">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="cc296-168">“碰撞体”组件，例如盒碰撞体 </span><span class="sxs-lookup"><span data-stu-id="cc296-168">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="cc296-169">“操作处理程序(脚本)”组件 </span><span class="sxs-lookup"><span data-stu-id="cc296-169">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="cc296-170">“近距交互可抓取对象(脚本)”组件 </span><span class="sxs-lookup"><span data-stu-id="cc296-170">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="cc296-171">1.将“操作处理程序(脚本)”组件添加到所有对象</span><span class="sxs-lookup"><span data-stu-id="cc296-171">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="cc296-172">在“层次结构”窗口中选择“Cheese”对象，在按住 **Shift** 键的同时选择“Cube () 2”对象，然后将“操作处理程序(脚本)”组件添加到所有对象：   </span><span class="sxs-lookup"><span data-stu-id="cc296-172">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="cc296-174">在本教程中，碰撞体已添加到预制件中。</span><span class="sxs-lookup"><span data-stu-id="cc296-174">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="cc296-175">对于 Unity 基元（例如 Cube 对象），创建对象时会自动添加碰撞体组件。</span><span class="sxs-lookup"><span data-stu-id="cc296-175">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="cc296-176">在上图中，碰撞体由绿色外框表示。</span><span class="sxs-lookup"><span data-stu-id="cc296-176">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="cc296-177">若要详细了解碰撞体，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞体</a>文档。</span><span class="sxs-lookup"><span data-stu-id="cc296-177">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="cc296-178">2.将“近距交互可抓取对象(脚本)”组件添加到预制件对象</span><span class="sxs-lookup"><span data-stu-id="cc296-178">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="cc296-179">在“层次结构”窗口中选择“Cheese”对象，在按住 **Shift** 键的同时选择“TheModule”对象，然后将“近距交互可抓取对象(脚本)”组件添加到所有对象：   </span><span class="sxs-lookup"><span data-stu-id="cc296-179">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="cc296-181">3.配置“操作处理程序(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="cc296-181">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="cc296-182">默认操作</span><span class="sxs-lookup"><span data-stu-id="cc296-182">Default manipulation</span></span>

<span data-ttu-id="cc296-183">对于“Cube”对象，请将所有属性保留默认值，以体验默认的操作行为： </span><span class="sxs-lookup"><span data-stu-id="cc296-183">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="cc296-185">若要将某个组件重置为其默认值，可以选择该组件的“设置”图标，然后选择“重置”。</span><span class="sxs-lookup"><span data-stu-id="cc296-185">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="cc296-186">将操作限制为缩放</span><span class="sxs-lookup"><span data-stu-id="cc296-186">Restrict manipulation to scale only</span></span>

<span data-ttu-id="cc296-187">对于“Cube (1)”对象，请将“双手操作类型”更改为“缩放”，以便仅允许用户更改对象的大小：   </span><span class="sxs-lookup"><span data-stu-id="cc296-187">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="cc296-189">将用户运动范围约束为固定的距离</span><span class="sxs-lookup"><span data-stu-id="cc296-189">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="cc296-190">对于“Cube (2)”对象，请将“运动约束”更改为“与头部之间的固定距离”，以便在移动该对象时，它与用户保持相同的距离：   </span><span class="sxs-lookup"><span data-stu-id="cc296-190">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="cc296-192">默认的可抓取对象操作</span><span class="sxs-lookup"><span data-stu-id="cc296-192">Default grabbable manipulation</span></span>

<span data-ttu-id="cc296-193">对于“Cheese”，“CoffeCup”和“EarthCore”对象，请将所有属性保留默认值，以体验默认的可抓取对象操作行为：   </span><span class="sxs-lookup"><span data-stu-id="cc296-193">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="cc296-195">删除远距操作功能</span><span class="sxs-lookup"><span data-stu-id="cc296-195">Remove the ability of far manipulation</span></span>

<span data-ttu-id="cc296-196">对于“Octa”对象，请取消选中“允许远距操作”复选框，使用户只能直接通过跟踪手来与该对象交互：  </span><span class="sxs-lookup"><span data-stu-id="cc296-196">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="cc296-198">使对象围绕中心旋转</span><span class="sxs-lookup"><span data-stu-id="cc296-198">Make an object rotate around its center</span></span>

<span data-ttu-id="cc296-199">对于“Platonic”对象，请将“近距单手旋转模式”和“远距单手旋转模式”更改为“围绕对象中心旋转”，以便在用户单手旋转该对象时，该对象围绕其中心旋转：    </span><span class="sxs-lookup"><span data-stu-id="cc296-199">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="cc296-201">释放对象后保持运动</span><span class="sxs-lookup"><span data-stu-id="cc296-201">Keep movement after object is released</span></span>

<span data-ttu-id="cc296-202">对于“TheModule”对象，请添加一个 **Rigidbody** 组件以启用物理学，然后取消选中“使用重力”复选框，使该对象不受重力的影响：  </span><span class="sxs-lookup"><span data-stu-id="cc296-202">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="cc296-204">返回到“操作处理程序(脚本)”组件，检查“释放行为”是否同时设置为“保持速度”和“保持角速度”，以便在从用户手中释放对象后，该对象会继续运动：   </span><span class="sxs-lookup"><span data-stu-id="cc296-204">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="cc296-206">若要详细了解“操作处理程序”组件及其相关属性，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[操作处理程序](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)指南。</span><span class="sxs-lookup"><span data-stu-id="cc296-206">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="cc296-207">添加边界框</span><span class="sxs-lookup"><span data-stu-id="cc296-207">Adding bounding boxes</span></span>

<span data-ttu-id="cc296-208">边界框提供用于缩放和旋转的控点，在近距和远距交互时，使用边界框可以更轻松、更直观地单手操作对象。</span><span class="sxs-lookup"><span data-stu-id="cc296-208">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="cc296-209">此示例将一个边界框添加到 EarthCore 对象，以便可以使用在上一部分中配置的对象操作来与此对象交互，并使用边界框控点来缩放和旋转此对象。</span><span class="sxs-lookup"><span data-stu-id="cc296-209">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc296-210">若要使用**边界框**，对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="cc296-210">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="cc296-211">“碰撞体”组件，例如盒碰撞体 </span><span class="sxs-lookup"><span data-stu-id="cc296-211">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="cc296-212">“边界框(脚本)”组件 </span><span class="sxs-lookup"><span data-stu-id="cc296-212">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="cc296-213">1.将“边界框(脚本)”组件添加到 EarthCore 对象</span><span class="sxs-lookup"><span data-stu-id="cc296-213">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="cc296-214">在“检查器”窗口中选择“EarthCore”对象，然后将“边界框(脚本)”组件添加到 EarthCore 对象：  </span><span class="sxs-lookup"><span data-stu-id="cc296-214">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="cc296-216">边界框可视化效果是在运行时创建的，因此在进入“游戏”模式之前不可见。</span><span class="sxs-lookup"><span data-stu-id="cc296-216">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="cc296-217">2.使用编辑器中的模拟功能可视化和测试边界框</span><span class="sxs-lookup"><span data-stu-id="cc296-217">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="cc296-218">按“播放”按钮进入“游戏”模式。</span><span class="sxs-lookup"><span data-stu-id="cc296-218">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="cc296-219">长按空格键显示手形光标，然后使用鼠标来与边界框交互：</span><span class="sxs-lookup"><span data-stu-id="cc296-219">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="cc296-221">若要详细了解“边界框”组件及其相关属性，可以访问 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[边界框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)指南。</span><span class="sxs-lookup"><span data-stu-id="cc296-221">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="cc296-222">添加触摸效果</span><span class="sxs-lookup"><span data-stu-id="cc296-222">Adding touch effects</span></span>

<span data-ttu-id="cc296-223">此示例启用在用手触摸对象时要触发的事件。</span><span class="sxs-lookup"><span data-stu-id="cc296-223">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="cc296-224">具体而言，你将配置 Octa 对象，以便在用户触摸它时播放声音效果。</span><span class="sxs-lookup"><span data-stu-id="cc296-224">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="cc296-225">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="cc296-225">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="cc296-226">将“音频源”组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="cc296-226">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="cc296-227">将“近距交互可触摸对象(脚本)”组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="cc296-227">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="cc296-228">将“手动交互触摸(脚本)”组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="cc296-228">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="cc296-229">实现 On Touch Started 事件</span><span class="sxs-lookup"><span data-stu-id="cc296-229">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="cc296-230">使用编辑器中的模拟功能测试触摸交互</span><span class="sxs-lookup"><span data-stu-id="cc296-230">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc296-231">若要**触发触摸事件**，对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="cc296-231">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="cc296-232">“碰撞体”组件，最好是盒碰撞体 </span><span class="sxs-lookup"><span data-stu-id="cc296-232">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="cc296-233">“近距交互可触摸对象(脚本)”组件 </span><span class="sxs-lookup"><span data-stu-id="cc296-233">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="cc296-234">“手动交互触摸(脚本)”组件 </span><span class="sxs-lookup"><span data-stu-id="cc296-234">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="cc296-235">MRTK 中未包含“手动交互触摸(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="cc296-235">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="cc296-236">它已连同本教程的资产一起导入，最初包含在混合现实工具包 Unity 示例中。</span><span class="sxs-lookup"><span data-stu-id="cc296-236">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="cc296-237">1.将“音频源”组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="cc296-237">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="cc296-238">在“层次结构”窗口中选择“Octa”对象，将“音频源”组件添加到 Octa 对象，然后将“空间混合”更改为 1，以启用空间音频：   </span><span class="sxs-lookup"><span data-stu-id="cc296-238">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="cc296-240">2.将“近距交互可触摸对象(脚本)”组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="cc296-240">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="cc296-241">在仍选中了“Octa”对象的情况下，将“近距交互可触摸(脚本)”组件添加到 Octa 对象，然后单击“拟合边界”和“拟合中点”按钮，以更新“近距交互可触摸(脚本)”组件的“局部中点”和“边界”属性，使之与 BoxCollider 匹配：    </span><span class="sxs-lookup"><span data-stu-id="cc296-241">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="cc296-243">3.将“手动交互触摸(脚本)”组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="cc296-243">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="cc296-244">在仍选中了“Octa”对象的情况下，将“手动交互触摸(脚本)”组件添加到 Octa 对象：  </span><span class="sxs-lookup"><span data-stu-id="cc296-244">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="cc296-246">4.实现 On Touch Started 事件</span><span class="sxs-lookup"><span data-stu-id="cc296-246">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="cc296-247">在“手动交互触摸(脚本)”组件中，单击 **+** 小图标创建新的 **On Touch Started ()** 事件。 </span><span class="sxs-lookup"><span data-stu-id="cc296-247">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="cc296-248">然后将“Octa”对象配置为接收该事件，并将“AudioSource.PlayOneShot”定义为要触发的操作：  </span><span class="sxs-lookup"><span data-stu-id="cc296-248">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="cc296-250">导航到“资产” > “MixedRealityToolkit.SDK” > “StandardAssets” > “音频”以查看 MRTK 随附的音频剪辑，然后将适当的音频剪辑（例如 MRTK_Gem 音频剪辑）分配到“音频剪辑”字段：     </span><span class="sxs-lookup"><span data-stu-id="cc296-250">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Audio** to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="cc296-252">有关如何实现事件的提示，可参阅[手动跟踪手势和可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)中的说明。</span><span class="sxs-lookup"><span data-stu-id="cc296-252">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="cc296-253">5.使用编辑器中的模拟功能测试触摸交互</span><span class="sxs-lookup"><span data-stu-id="cc296-253">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="cc296-254">按“播放”按钮进入“游戏”模式。</span><span class="sxs-lookup"><span data-stu-id="cc296-254">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="cc296-255">长按空格键显示手形光标，然后使用鼠标触摸 Octa 对象并触发声音效果：</span><span class="sxs-lookup"><span data-stu-id="cc296-255">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="cc296-257">如上图所示，在测试触摸交互时，Octa 对象的颜色会有节律性地变化。</span><span class="sxs-lookup"><span data-stu-id="cc296-257">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="cc296-258">此效果已在“手动交互触摸(脚本)”组件中硬编码，而与前面步骤中完成的事件配置无关。</span><span class="sxs-lookup"><span data-stu-id="cc296-258">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="cc296-259">若要禁用此效果，可以执行相应的操作，例如，注释掉第 32 行“TargetRenderer = GetComponentInChildren<Renderer>();”，使 TargetRenderer 保持为 null，这样颜色就不会呈节律性的变化。</span><span class="sxs-lookup"><span data-stu-id="cc296-259">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="cc296-260">祝贺</span><span class="sxs-lookup"><span data-stu-id="cc296-260">Congratulations</span></span>

<span data-ttu-id="cc296-261">在本教程中，你已了解如何在网格集合中组织 3D 对象，以及如何使用近距交互（使用跟踪手直接抓取）和远距交互（使用视线或手部射线）操作这些对象（缩放、旋转和移动）。</span><span class="sxs-lookup"><span data-stu-id="cc296-261">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="cc296-262">此外，你还了解了如何在 3D 对象的周围放置边界框，以及如何使用和自定义边界框上的控点。</span><span class="sxs-lookup"><span data-stu-id="cc296-262">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="cc296-263">最后，你已了解如何在触摸对象时触发事件。</span><span class="sxs-lookup"><span data-stu-id="cc296-263">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="cc296-264">下一课：6.探索高级输入选项</span><span class="sxs-lookup"><span data-stu-id="cc296-264">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
