---
title: 入门教程-5。 与三维对象交互
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 7eb38e205237257e400550299fdeebb73ba746f1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555431"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="9a2ea-104">5. 与三维对象交互</span><span class="sxs-lookup"><span data-stu-id="9a2ea-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="9a2ea-105">在本教程中，你将了解基本的3D 内容和用户体验，例如将3D 对象组织为集合的一部分、基本操作的边界框、近和远交互，以及使用手动跟踪触摸和获取手势。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-105">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="9a2ea-106">目标</span><span class="sxs-lookup"><span data-stu-id="9a2ea-106">Objectives</span></span>

* <span data-ttu-id="9a2ea-107">创建将用于其他学习目标的3D 对象面板</span><span class="sxs-lookup"><span data-stu-id="9a2ea-107">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="9a2ea-108">实现边界框</span><span class="sxs-lookup"><span data-stu-id="9a2ea-108">Implement bounding boxes</span></span>
* <span data-ttu-id="9a2ea-109">为基本操作（如移动、旋转和缩放）配置3D 对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-109">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="9a2ea-110">探索近距和远距交互</span><span class="sxs-lookup"><span data-stu-id="9a2ea-110">Explore near and far interaction</span></span>
* <span data-ttu-id="9a2ea-111">了解其他手动跟踪手势，如抓取和触摸</span><span class="sxs-lookup"><span data-stu-id="9a2ea-111">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9a2ea-112">导入教程资产</span><span class="sxs-lookup"><span data-stu-id="9a2ea-112">Importing the tutorial assets</span></span>

<span data-ttu-id="9a2ea-113">下载并导入 Unity 自定义包：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-113">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="9a2ea-114">MRTK.HoloLens2. GettingStarted. 2.3.0.2. unitypackage</span><span class="sxs-lookup"><span data-stu-id="9a2ea-114">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

<span data-ttu-id="9a2ea-115">导入教程资产后，项目窗口应如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-115">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="9a2ea-117">有关如何导入 Unity 自定义包的提醒，可以参阅[导入混合现实工具包](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)说明。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-117">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="9a2ea-118">Decluttering 场景视图</span><span class="sxs-lookup"><span data-stu-id="9a2ea-118">Decluttering the scene view</span></span>

<span data-ttu-id="9a2ea-119">若要更轻松地使用场景，请通过单击对象左侧的**眼睛**图标将**Cube**和**ButtonCollection**对象的**场景可见性**设置为 off。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-119">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="9a2ea-120">这将隐藏场景窗口中的对象，而无需更改其游戏中的可见性：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-120">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="9a2ea-122">若要详细了解场景可见性控件以及如何使用它们来优化场景视图和工作流，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">场景可见性</a>文档。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-122">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="9a2ea-123">组织集合中的3D 对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-123">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="9a2ea-124">在本部分中，你将创建一个3D 对象面板，在本教程的以下部分中，你将使用此面板来浏览与3D 对象交互的各种方式。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-124">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="9a2ea-125">具体来说，您需要将三维对象配置为置于 3 x 3 网格上。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-125">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="9a2ea-126">类似于[创建按钮面板](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)时，执行此操作需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-126">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="9a2ea-127">将三维对象作为父对象的父级</span><span class="sxs-lookup"><span data-stu-id="9a2ea-127">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="9a2ea-128">添加和配置网格对象集合（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-128">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="9a2ea-129">1. 将3D 对象作为父对象的父级</span><span class="sxs-lookup"><span data-stu-id="9a2ea-129">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="9a2ea-130">在 "层次结构" 窗口中，**创建一个空的对象**，为其指定一个适当的名称（例如**3DObjectCollection**），并将其放置在合适的位置，例如 X = 0，Y =-0.2，Z = 2。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-130">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="9a2ea-131">在项目窗口中，导航到 "**资产**" > **MRTK "。GettingStarted** > **prototyping**，然后将以下 Prototyping**父级**为**3DObjectCollection**：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-131">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="9a2ea-132">比萨饼</span><span class="sxs-lookup"><span data-stu-id="9a2ea-132">Cheese</span></span>
* <span data-ttu-id="9a2ea-133">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="9a2ea-133">CoffeeCup</span></span>
* <span data-ttu-id="9a2ea-134">EarthCore</span><span class="sxs-lookup"><span data-stu-id="9a2ea-134">EarthCore</span></span>
* <span data-ttu-id="9a2ea-135">八</span><span class="sxs-lookup"><span data-stu-id="9a2ea-135">Octa</span></span>
* <span data-ttu-id="9a2ea-136">Platonic</span><span class="sxs-lookup"><span data-stu-id="9a2ea-136">Platonic</span></span>
* <span data-ttu-id="9a2ea-137">TheModule</span><span class="sxs-lookup"><span data-stu-id="9a2ea-137">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="9a2ea-139">在 "层次结构" 窗口中，**创建三个多维数据集**作为**3DObjectCollection**的子对象，并将其转换**比例**设置为 X = 0.15，Y = 0.15，Z = 0.15：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-139">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="9a2ea-141">有关如何执行上述步骤的提醒，可以参阅[创建用户界面和配置混合现实工具包](mrlearning-base-ch2.md)教程。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-141">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="9a2ea-142">重新定位多维数据集，以便可以查看每个多维数据集：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-142">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="9a2ea-144">在 "项目" 窗口中，导航到 "**资产**" > " **MixedRealityToolkit** " > **STANDARDASSETS** > **材料**，查看 MRTK 提供的材料。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-144">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="9a2ea-145">**单击并将**适当的材料拖到每个多维数据集的 "网格呈现器**材料**元素 0" 属性，例如：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-145">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="9a2ea-146">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="9a2ea-146">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="9a2ea-147">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="9a2ea-147">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="9a2ea-148">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="9a2ea-148">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="9a2ea-150">2. 添加和配置网格对象集合（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-150">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="9a2ea-151">将**网格对象集合（脚本）** 组件添加到**3DObjectCollection**对象，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-151">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="9a2ea-152">将**排序类型**更改为**子级顺序**，以确保子对象按照其置于父对象下的顺序进行排序</span><span class="sxs-lookup"><span data-stu-id="9a2ea-152">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="9a2ea-153">然后单击 "**更新集合**" 按钮应用新配置：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-153">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="9a2ea-155">操作三维对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-155">Manipulating 3D objects</span></span>

<span data-ttu-id="9a2ea-156">在本部分中，您将添加操作在上一节中创建的面板中的所有3D 对象的功能。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-156">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="9a2ea-157">此外，对于 prefab 对象，用户可以通过跟踪来访问和获取这些对象。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-157">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="9a2ea-158">然后，您将探索一些可应用于您的对象的操作行为。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-158">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="9a2ea-159">为实现此目的需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-159">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="9a2ea-160">向所有对象添加操作处理程序（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-160">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="9a2ea-161">将 Near 交互 Grabbable （脚本）组件添加到 prefab 对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-161">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="9a2ea-162">配置操作处理程序（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-162">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a2ea-163">为了能够**操作对象**，对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-163">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="9a2ea-164">**碰撞**器组件，例如，盒碰撞器</span><span class="sxs-lookup"><span data-stu-id="9a2ea-164">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="9a2ea-165">**操作处理程序（脚本）** 组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-165">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="9a2ea-166">若要能够**操作**并**抓住跟踪的对象**，对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-166">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="9a2ea-167">**碰撞**器组件，例如，盒碰撞器</span><span class="sxs-lookup"><span data-stu-id="9a2ea-167">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="9a2ea-168">**操作处理程序（脚本）** 组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-168">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="9a2ea-169">**近交互 Grabbable （脚本）** 组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-169">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="9a2ea-170">1. 将操作处理程序（脚本）组件添加到所有对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-170">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="9a2ea-171">在 "层次结构" 窗口中，选择 "**奶酪**" 对象，按住**Shift**键，然后选择**Cube （） 2**对象，并将**操作处理程序（脚本）** 组件添加到所有对象：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-171">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9a2ea-173">出于本教程的目的，colliders 已添加到 prototyping 中。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-173">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="9a2ea-174">对于 Unity 基元（如 Cube 对象），创建对象时，会自动添加碰撞器组件。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-174">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="9a2ea-175">在上面的图像中，colliders 表示为绿色的轮廓。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-175">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="9a2ea-176">若要了解有关 colliders 的详细信息，可访问 Unity 的<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">碰撞</a>器文档。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-176">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="9a2ea-177">2. 将 Near 交互 Grabbable （脚本）组件添加到 prefab 对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-177">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="9a2ea-178">在 "层次结构" 窗口中，选择 "**奶酪**" 对象，按住**Shift**键，然后选择 " **TheModule** " 对象，并将**Near 交互 Grabbable （脚本）** 组件添加到所有对象：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-178">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="9a2ea-180">3. 配置操作处理程序（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-180">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="9a2ea-181">默认操作</span><span class="sxs-lookup"><span data-stu-id="9a2ea-181">Default manipulation</span></span>

<span data-ttu-id="9a2ea-182">对于**多维数据集**对象，请保留默认的所有属性，以体验默认操作行为：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-182">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="9a2ea-184">若要将组件重置为其默认值，可以选择组件的 "设置" 图标，然后选择 "重置"。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-184">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="9a2ea-185">仅限缩放操作</span><span class="sxs-lookup"><span data-stu-id="9a2ea-185">Restrict manipulation to scale only</span></span>

<span data-ttu-id="9a2ea-186">对于**多维数据集（1）** 对象，将两个**正在进行的** **操作类型**更改为仅允许用户更改对象的大小：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-186">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="9a2ea-188">限制移动与用户的固定距离</span><span class="sxs-lookup"><span data-stu-id="9a2ea-188">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="9a2ea-189">对于**Cube （2）** 对象，更改**对移动的约束**以**修复与 Head 的距离**，以便在移动对象时，它将保持与用户相同的距离：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-189">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="9a2ea-191">默认 grabbable 操作</span><span class="sxs-lookup"><span data-stu-id="9a2ea-191">Default grabbable manipulation</span></span>

<span data-ttu-id="9a2ea-192">对于**奶酪**、 **CoffeCup**和**EarthCore**对象，请将所有属性都保留为默认值，以体验默认 grabbable 操作行为：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-192">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="9a2ea-194">消除远端操作的能力</span><span class="sxs-lookup"><span data-stu-id="9a2ea-194">Remove the ability of far manipulation</span></span>

<span data-ttu-id="9a2ea-195">对于**八**对象，请取消选中 "**允许远端操作**" 复选框，以便用户只能使用跟踪的指针直接与对象交互：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-195">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="9a2ea-197">使对象围绕中心旋转</span><span class="sxs-lookup"><span data-stu-id="9a2ea-197">Make an object rotate around its center</span></span>

<span data-ttu-id="9a2ea-198">对于**Platonic**对象，请将**一只手旋转模式**更改为近、**一只手旋转模式**，以围绕**对象中心旋转**，这样当用户用一只手旋转对象时，它就会围绕对象中心旋转：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-198">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="9a2ea-200">释放对象后保持移动</span><span class="sxs-lookup"><span data-stu-id="9a2ea-200">Keep movement after object is released</span></span>

<span data-ttu-id="9a2ea-201">对于**TheModule**对象，添加一个**刚体**组件以启用物理学，然后取消选中 "**使用重力**" 复选框，以使对象不受重力的影响：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-201">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="9a2ea-203">返回到操作处理程序（脚本）组件，验证是否已将 "**发布行为**" 设置为 "**保持速度**" 并**保持角度速度**，以便一旦对象从用户的手中释放，就会继续移动：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-203">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="9a2ea-205">若要了解有关操作处理程序组件及其关联属性的详细信息，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[操作处理程序](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)指南。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-205">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="9a2ea-206">添加边界框</span><span class="sxs-lookup"><span data-stu-id="9a2ea-206">Adding bounding boxes</span></span>

<span data-ttu-id="9a2ea-207">使用边界框，可通过提供可用于缩放和旋转的句柄，更轻松、更直观地处理对象，同时实现近乎交互和远距离交互。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-207">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="9a2ea-208">在此示例中，您将向 EarthCore 对象添加一个边界框，以便现在可以使用您在上一节中配置的对象操作与进行交互，并使用边界框控点进行缩放和旋转。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-208">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a2ea-209">若要能够使用**边界框**，对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-209">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="9a2ea-210">**碰撞**器组件，例如，盒碰撞器</span><span class="sxs-lookup"><span data-stu-id="9a2ea-210">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="9a2ea-211">**边界框（脚本）** 组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-211">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="9a2ea-212">1. 将边界框（脚本）组件添加到 EarthCore 对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-212">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="9a2ea-213">在 "检查器" 窗口中，选择 " **EarthCore** " 对象，并将**边界框（脚本）** 组件添加到 EarthCore 对象：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-213">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9a2ea-215">边界框可视化效果是在运行时创建的，因此在进入游戏模式之前不可见。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-215">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="9a2ea-216">2. 使用编辑器内模拟来可视化和测试边界框</span><span class="sxs-lookup"><span data-stu-id="9a2ea-216">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="9a2ea-217">按 "播放" 按钮进入游戏模式。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-217">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="9a2ea-218">然后按住空格键以调出手，并使用鼠标与边界框进行交互：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-218">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="9a2ea-220">若要详细了解边界框组件及其关联的属性，可以访问[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的 "[边界框](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)" 指南。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-220">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="9a2ea-221">添加触摸效果</span><span class="sxs-lookup"><span data-stu-id="9a2ea-221">Adding touch effects</span></span>

<span data-ttu-id="9a2ea-222">在此示例中，你将允许在你用手触摸对象时触发事件。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-222">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="9a2ea-223">具体来说，您将配置八对象，使其在用户接触时播放声音效果。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-223">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="9a2ea-224">为实现此目的需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-224">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="9a2ea-225">向对象中添加音频源组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-225">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="9a2ea-226">将 Near 交互可触摸（脚本）组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-226">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="9a2ea-227">将手写交互触摸（脚本）组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-227">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="9a2ea-228">实现 On Touch 已开始事件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-228">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="9a2ea-229">使用编辑器中的模拟测试触摸交互</span><span class="sxs-lookup"><span data-stu-id="9a2ea-229">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a2ea-230">为了能够**触发触控事件**，对象必须具有以下组件：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-230">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="9a2ea-231">**碰撞**器组件，最好是盒碰撞器</span><span class="sxs-lookup"><span data-stu-id="9a2ea-231">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="9a2ea-232">**近交互可触摸（脚本）** 组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-232">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="9a2ea-233">**手动交互触摸（脚本）** 组件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-233">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="9a2ea-234">手动交互触摸（脚本）组件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-234">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="9a2ea-235">它已通过本教程的资产导入，最初是 MixedReality 工具包 Unity 示例的一部分。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-235">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="9a2ea-236">1. 将音频源组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-236">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="9a2ea-237">在 "层次结构" 窗口中，选择 "**八**" 对象，将 "**音频源**" 组件添加到八对象，然后将 "**空间混合**" 更改为1以启用空间音频：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-237">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="9a2ea-239">2. 将 Near 交互可触摸（脚本）组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-239">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="9a2ea-240">在仍选择**八**对象的情况下，将**near 交互可触摸（脚本）** 组件添加到八对象，然后单击 "**修复边界**" 和 "**修复中心**" 按钮，更新接近交互可触摸（脚本）的局部中心和边界属性，使之与 BoxCollider 匹配：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-240">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="9a2ea-242">3. 将手形交互触摸（脚本）组件添加到对象</span><span class="sxs-lookup"><span data-stu-id="9a2ea-242">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="9a2ea-243">在仍选择**八**对象的情况下，将**手写交互触摸（脚本）** 组件添加到八对象：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-243">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="9a2ea-245">4. 实现 On Touch 已开始事件</span><span class="sxs-lookup"><span data-stu-id="9a2ea-245">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="9a2ea-246">在 "**手动交互触摸（脚本）** " 组件上，单击 "小 **+** " 图标以**在 "Touch 已启动（）"** 事件上创建新的。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-246">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="9a2ea-247">然后配置**八**对象以接收事件，并将**AudioSource**定义为要触发的操作：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-247">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="9a2ea-249">导航到 "**资产**" > **MixedRealityToolkit** " > **StandardAssets** >" 材料 "查看与 MRTK 一起提供的音频剪辑，然后将合适的音频剪辑分配到"**音频剪辑**"字段，例如 MRTK_Gem 音频剪辑：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-249">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="9a2ea-251">有关如何实现事件的提醒，可参阅 "[手动跟踪手势" 和 "种不可交互" 按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)说明。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-251">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="9a2ea-252">5. 使用编辑器内模拟测试触摸交互</span><span class="sxs-lookup"><span data-stu-id="9a2ea-252">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="9a2ea-253">按 "播放" 按钮进入游戏模式。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-253">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="9a2ea-254">然后按住空格键以调出手，并使用鼠标来触摸八对象并触发声音效果：</span><span class="sxs-lookup"><span data-stu-id="9a2ea-254">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="9a2ea-256">正如上图中所示，在测试触摸屏交互时，八对象的颜色 pulsated。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-256">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="9a2ea-257">此效果硬编码为手动交互触摸（脚本）组件，而不是上面步骤中完成的事件配置的结果。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-257">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="9a2ea-258">如果要禁用此效果，则可以（例如，注释掉或第32行） "TargetRenderer = GetComponentInChildren<Renderer>（）;"，这将导致 TargetRenderer 剩余 null，并且颜色不 pulsating。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-258">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9a2ea-259">祝贺你</span><span class="sxs-lookup"><span data-stu-id="9a2ea-259">Congratulations</span></span>

<span data-ttu-id="9a2ea-260">在本教程中，您学习了如何在网格集合中组织3D 对象，以及如何使用接近的交互（直接抓取、旋转和移动）来处理这些对象（使用 "注视" 光线或手写光线）。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-260">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="9a2ea-261">还了解了如何在三维对象周围放置边框，并了解了如何使用和自定义边界框中的句柄。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-261">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="9a2ea-262">最后，你已了解如何在触摸对象时触发事件。</span><span class="sxs-lookup"><span data-stu-id="9a2ea-262">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="9a2ea-263">下一课： 6. 浏览高级输入选项</span><span class="sxs-lookup"><span data-stu-id="9a2ea-263">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
