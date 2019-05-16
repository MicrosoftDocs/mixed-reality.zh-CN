---
title: MR 学习基本模块-农历模块程序集示例体验
description: 在本课中，我们将合并多个前面的课程创建唯一示例体验从中学到的概念。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity 中，教程，hololens 混合的现实
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730848"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a><span data-ttu-id="561a0-104">MR 学习基本模块-农历模块程序集示例体验</span><span class="sxs-lookup"><span data-stu-id="561a0-104">MR Learning Base Module - Lunar Module Assembly Sample Experience</span></span>

<span data-ttu-id="561a0-105">在本课中，我们将合并多个前面的课程创建唯一示例体验从中学到的概念。</span><span class="sxs-lookup"><span data-stu-id="561a0-105">In this lesson, we will combine multiple concepts learned from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="561a0-106">我们将创建农历模块程序集应用程序，用户将需要使用跟踪的手选取农历模块的组成部分，并尝试组合农历模块。</span><span class="sxs-lookup"><span data-stu-id="561a0-106">We will create a lunar module assembly application whereby a user will need to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="561a0-107">我们将使用 pressable 按钮来切换放置提示，要重置我们的经验，并启动我们农历模块到空间 ！</span><span class="sxs-lookup"><span data-stu-id="561a0-107">We will use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="561a0-108">在将来的教程中，我们将继续基于此体验，包括功能强大多用户的用例，利用 Azure 空间的定位点来实现空间对齐方式。</span><span class="sxs-lookup"><span data-stu-id="561a0-108">In future tutorials, we will continue to build upon this experience, including powerful multi-user use-cases that leverages Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="561a0-109">目标</span><span class="sxs-lookup"><span data-stu-id="561a0-109">Objectives</span></span>

- <span data-ttu-id="561a0-110">合并多个概念从前面的课程，以创建独特的体验</span><span class="sxs-lookup"><span data-stu-id="561a0-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="561a0-111">了解如何切换对象</span><span class="sxs-lookup"><span data-stu-id="561a0-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="561a0-112">触发器复杂的事件，使用 pressable 按钮</span><span class="sxs-lookup"><span data-stu-id="561a0-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="561a0-113">使用 rigidbody 物理和强制</span><span class="sxs-lookup"><span data-stu-id="561a0-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="561a0-114">了解如何使用工具提示</span><span class="sxs-lookup"><span data-stu-id="561a0-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="561a0-115">说明</span><span class="sxs-lookup"><span data-stu-id="561a0-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="561a0-116">农历模块的配置</span><span class="sxs-lookup"><span data-stu-id="561a0-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="561a0-117">在本章中，我们将创建我们的示例体验所需的各种组件介绍。</span><span class="sxs-lookup"><span data-stu-id="561a0-117">In this chapter, we will be introduced to the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="561a0-118">向基本场景中添加农历模块程序集预设。</span><span class="sxs-lookup"><span data-stu-id="561a0-118">Add the lunar module assembly prefab to your Base Scene.</span></span> <span data-ttu-id="561a0-119">为此，请在你项目的选项卡中，搜索"火箭 Launcher_Tutorial。"</span><span class="sxs-lookup"><span data-stu-id="561a0-119">To do this, in your project tab, search for "Rocket Launcher_Tutorial."</span></span> <span data-ttu-id="561a0-120">也可以在资产中找到预设可 > BaseModuleAssets > 预设。</span><span class="sxs-lookup"><span data-stu-id="561a0-120">You may also find the prefab in Assets>BaseModuleAssets>Prefabs.</span></span> <span data-ttu-id="561a0-121">你可能会看到两个火箭启动器预设;一个具有名称"教程"，另一个具有名称"完成。</span><span class="sxs-lookup"><span data-stu-id="561a0-121">You may see two rocket launcher prefabs; one with the name "tutorial" and another with the name "complete."</span></span> <span data-ttu-id="561a0-122">将"火箭 Launcher_Tutorial"预设可拖动到您的基本场景。</span><span class="sxs-lookup"><span data-stu-id="561a0-122">Drag the "Rocket Launcher_Tutorial" prefab to your Base Scene.</span></span> <span data-ttu-id="561a0-123">随意放置在您的场景预设的位置。</span><span class="sxs-lookup"><span data-stu-id="561a0-123">Feel free to position the placement of the prefab in your scene.</span></span>
   <span data-ttu-id="561a0-124">注意："火箭 Launcher_Complete"预设是已完成的启动器，供参考。</span><span class="sxs-lookup"><span data-stu-id="561a0-124">Note: The "Rocket Launcher_Complete" prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="561a0-126">如果你在层次结构中展开"火箭 Launcher_Tutorial"游戏对象，并进一步展开"农历模块"对象，你将看到多个对象的子对象的材料，名为"x 射线。"</span><span class="sxs-lookup"><span data-stu-id="561a0-126">If you expand the "Rocket Launcher_Tutorial" game object in your hierarchy, and further expand the "Lunar Module" object, you will see several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="561a0-127">"X 射线"材料允许我们将使用用户为放置提示略有半透明颜色。</span><span class="sxs-lookup"><span data-stu-id="561a0-127">The "x-ray" material allows for a slightly translucent color which we will use as placement hints for the user.</span></span> 

<span data-ttu-id="561a0-128">![Lesson6 第 1 章 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)有五个部分农历模块的用户要进行交互，如下图中所示：</span><span class="sxs-lookup"><span data-stu-id="561a0-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user is going to interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="561a0-129">漫游存储模块</span><span class="sxs-lookup"><span data-stu-id="561a0-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="561a0-130">油箱</span><span class="sxs-lookup"><span data-stu-id="561a0-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="561a0-131">能源单元格</span><span class="sxs-lookup"><span data-stu-id="561a0-131">The Energy Cell</span></span>
4.  <span data-ttu-id="561a0-132">在停靠门户</span><span class="sxs-lookup"><span data-stu-id="561a0-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="561a0-133">外部传感器</span><span class="sxs-lookup"><span data-stu-id="561a0-133">The External sensor</span></span>

![Lesson6 第 1 章 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="561a0-135">注意：您看到基本场景层次结构中的游戏对象名称不对应于场景中对象的名称。</span><span class="sxs-lookup"><span data-stu-id="561a0-135">Note: The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="561a0-136">步骤 2：将音频源添加到农历模块。</span><span class="sxs-lookup"><span data-stu-id="561a0-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="561a0-137">请确保基场景层次结构中选择该农历模块，然后单击"添加组件"。</span><span class="sxs-lookup"><span data-stu-id="561a0-137">Make sure the lunar module is selected in your base scene hierarchy and click "Add Component."</span></span> <span data-ttu-id="561a0-138">搜索"音频源"，并将其添加到该对象。</span><span class="sxs-lookup"><span data-stu-id="561a0-138">Search for "Audio Source" and add it to the object.</span></span> <span data-ttu-id="561a0-139">将其留空现在。</span><span class="sxs-lookup"><span data-stu-id="561a0-139">Leave it blank for now.</span></span> <span data-ttu-id="561a0-140">我们将使用此播放启动声音更高版本。</span><span class="sxs-lookup"><span data-stu-id="561a0-140">We will use this to play the launching sound later.</span></span>
 <span data-ttu-id="561a0-141">![Lesson6 第 1 章 Step2im](images/Lesson6_Chapter1_step2im.PNG)步骤 3:添加脚本"切换放置提示"。</span><span class="sxs-lookup"><span data-stu-id="561a0-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Step 3: Add the script "toggle placement hints."</span></span> <span data-ttu-id="561a0-142">单击"添加组件"并搜索"放置提示切换"。</span><span class="sxs-lookup"><span data-stu-id="561a0-142">Click "Add Component" and search for "Toggle Placement Hints."</span></span> <span data-ttu-id="561a0-143">这是一个自定义脚本，您可以打开和关闭之前提到的半透明提示 （使用 x 射线材料的对象）。</span><span class="sxs-lookup"><span data-stu-id="561a0-143">This is a custom script that allows you to turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span> 
<span data-ttu-id="561a0-144">![Lesson6 第 1 章 Step3im](images/Lesson6_Chapter1_step3im.PNG)步骤 4:由于我们有 5 个对象，键入"5"的游戏对象数组大小。</span><span class="sxs-lookup"><span data-stu-id="561a0-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Step 4: Since we have 5 objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="561a0-145">然后应会看到显示的 5 个新元素。</span><span class="sxs-lookup"><span data-stu-id="561a0-145">Then you should see 5 new elements appear.</span></span> 

![Lesson6 第 1 章 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="561a0-147">将每个半透明对象拖入框指出"None （游戏对象）。</span><span class="sxs-lookup"><span data-stu-id="561a0-147">Drag each of the translucent objects into the boxes that say "None (Game Object)."</span></span> <span data-ttu-id="561a0-148">从基本场景中的农历模块拖动以下对象：</span><span class="sxs-lookup"><span data-stu-id="561a0-148">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="561a0-149">• 背包</span><span class="sxs-lookup"><span data-stu-id="561a0-149">•   Backpack</span></span>

<span data-ttu-id="561a0-150">• GasTank</span><span class="sxs-lookup"><span data-stu-id="561a0-150">•   GasTank</span></span>

<span data-ttu-id="561a0-151">• Topleftbody</span><span class="sxs-lookup"><span data-stu-id="561a0-151">•   Topleftbody</span></span>

<span data-ttu-id="561a0-152">• 鼻子</span><span class="sxs-lookup"><span data-stu-id="561a0-152">•   Nose</span></span>

<span data-ttu-id="561a0-153">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="561a0-153">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="561a0-155">现在已配置的"切换放置提示"的脚本。</span><span class="sxs-lookup"><span data-stu-id="561a0-155">Now the "toggle placement hints" script is configured.</span></span> <span data-ttu-id="561a0-156">这将使我们能够打开和关闭的提示。</span><span class="sxs-lookup"><span data-stu-id="561a0-156">This will allow us to turn the hints on and off.</span></span>

<span data-ttu-id="561a0-157">步骤 5：添加的"启动农历模块"的脚本。</span><span class="sxs-lookup"><span data-stu-id="561a0-157">Step 5: Add the "launch lunar module" script.</span></span> <span data-ttu-id="561a0-158">单击"添加组件"按钮、"启动农历模块"中搜索并选择它。</span><span class="sxs-lookup"><span data-stu-id="561a0-158">Click the "Add Component" button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="561a0-159">此脚本将负责启动农历模块。</span><span class="sxs-lookup"><span data-stu-id="561a0-159">This script will be responsible for launching the lunar module.</span></span> <span data-ttu-id="561a0-160">当我们按配置的按钮时，它会将向上强制添加到农历模块刚体组件，并将导致模块以向上启动。</span><span class="sxs-lookup"><span data-stu-id="561a0-160">When we press a configured button, it will add an upward force to the lunar module's rigid body component and will cause the module to launch upwards.</span></span> <span data-ttu-id="561a0-161">如果你是室内，农历模块可能会崩溃针对 ceiling 网格。</span><span class="sxs-lookup"><span data-stu-id="561a0-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="561a0-162">但如果你是室外，它会飞入到空间无限期。</span><span class="sxs-lookup"><span data-stu-id="561a0-162">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="561a0-164">步骤 6：调整一些咄咄逼人以便农历模块会一头向上正常。</span><span class="sxs-lookup"><span data-stu-id="561a0-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="561a0-165">请尝试的值为 0.01。</span><span class="sxs-lookup"><span data-stu-id="561a0-165">Try a value of 0.01.</span></span> <span data-ttu-id="561a0-166">将"Rb"字段留空。</span><span class="sxs-lookup"><span data-stu-id="561a0-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="561a0-167">Rb 代表刚体，，将在运行时期间自动填充此字段。</span><span class="sxs-lookup"><span data-stu-id="561a0-167">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="561a0-169">农历模块部件概述</span><span class="sxs-lookup"><span data-stu-id="561a0-169">Lunar Module Parts Overview</span></span>
<span data-ttu-id="561a0-170">农历模块部分父对象是用户交互的对象的集合。</span><span class="sxs-lookup"><span data-stu-id="561a0-170">The Lunar Module parts parent object is the collection of the objects that the user will interact with.</span></span> <span data-ttu-id="561a0-171">下面的列表中提供的游戏对象名称 （使用场景标记为 paretheses 中的名称）：</span><span class="sxs-lookup"><span data-stu-id="561a0-171">The game object names (with scene labeled names in paretheses) are provided in the list below:</span></span>

- <span data-ttu-id="561a0-172">背包 （油箱）</span><span class="sxs-lookup"><span data-stu-id="561a0-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="561a0-173">GasTank （能源单元格）</span><span class="sxs-lookup"><span data-stu-id="561a0-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="561a0-174">TopLeftBody （Rover 机箱）</span><span class="sxs-lookup"><span data-stu-id="561a0-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="561a0-175">鼻子 （停靠门户）</span><span class="sxs-lookup"><span data-stu-id="561a0-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="561a0-176">LeftTwirler （外部传感器）</span><span class="sxs-lookup"><span data-stu-id="561a0-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="561a0-177">请注意每个对象具有操作处理程序，第 4 课中所述。</span><span class="sxs-lookup"><span data-stu-id="561a0-177">Notice that each of these objects has the manipulation handler, as discussed in lesson 4.</span></span> <span data-ttu-id="561a0-178">与操作处理程序，用户就能够获取和处理对象。</span><span class="sxs-lookup"><span data-stu-id="561a0-178">With the manipulation handler, users are able to grab and manipulate the object.</span></span> <span data-ttu-id="561a0-179">另请注意，"两个提交的操作类型"设置为"移动和旋转。"</span><span class="sxs-lookup"><span data-stu-id="561a0-179">Also note that the setting "two handed manipulation type" is set to "move and rotate."</span></span> <span data-ttu-id="561a0-180">这仅允许用户将对象移动并更改其大小，这是程序集应用程序所需的功能。</span><span class="sxs-lookup"><span data-stu-id="561a0-180">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="561a0-181">此外，远端操作没有被选中以仅允许直接交互的模块的组成部分。</span><span class="sxs-lookup"><span data-stu-id="561a0-181">In addition, far manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="561a0-183">部分程序集演示脚本 （如上所示） 是管理用户将其放到农历模块的对象脚本。</span><span class="sxs-lookup"><span data-stu-id="561a0-183">The part assembly demo script (shown above) is the scrip that manages the objects to be placed on to the lunar module by the user.</span></span> 

<span data-ttu-id="561a0-184">"对象到另一个位置"字段是图像的为所选 (n 上面，背包/油箱的大小写) 与它能够连接到的对象的转换。</span><span class="sxs-lookup"><span data-stu-id="561a0-184">The "Object To Place" field is the transform that is selected (n the case of the image above, the backpack/fuel tank) with the object that it can connect to.</span></span> 

<span data-ttu-id="561a0-185">"近距离"和"远距离"设置负责确定的邻近到的部分将对齐到位，或被释放。</span><span class="sxs-lookup"><span data-stu-id="561a0-185">The "Near Distance" and "Far Distance" settings are responsible for determining the proximity to which parts will snap in place or be released.</span></span> <span data-ttu-id="561a0-186">例如，背包/油箱需要为 0.1 单位距离农历模块来对齐到位。</span><span class="sxs-lookup"><span data-stu-id="561a0-186">For example, the backpack/fuel tank would need to be 0.1 units away from the lunar module to snap into place.</span></span> <span data-ttu-id="561a0-187">"远距离"设置对象需要为要分离的农历模块中的位置。</span><span class="sxs-lookup"><span data-stu-id="561a0-187">The "Far Distance" sets the location where the object needs to be to detach from the lunar module.</span></span> <span data-ttu-id="561a0-188">在这种情况下，用户的手必须获取背包/油箱并将其拉出 0.2 单位距离农历模块，将其从重新对齐到位删除。</span><span class="sxs-lookup"><span data-stu-id="561a0-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="561a0-189">"工具提示对象"是在场景中的工具提示标签。</span><span class="sxs-lookup"><span data-stu-id="561a0-189">The "Tool Tip Object" is the tool tip label in the scene.</span></span> <span data-ttu-id="561a0-190">当对象会对齐到位时，标签将被禁用。</span><span class="sxs-lookup"><span data-stu-id="561a0-190">When the objects are snapped in place, the label will be disabled.</span></span> 

<span data-ttu-id="561a0-191">将自动获取音频源。</span><span class="sxs-lookup"><span data-stu-id="561a0-191">The Audio Source will be automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="561a0-192">放置提示按钮</span><span class="sxs-lookup"><span data-stu-id="561a0-192">Placement Hints Buttons</span></span>
<span data-ttu-id="561a0-193">在中[第 2 课](mrlearning-base-ch2.md)，您学习了如何发出及配置按钮来执行诸如更改项的颜色，或将其推送时播放声音。</span><span class="sxs-lookup"><span data-stu-id="561a0-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="561a0-194">我们将继续使用这些原则，我们配置用于放置提示切换按钮。</span><span class="sxs-lookup"><span data-stu-id="561a0-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="561a0-195">目标是配置我们的按钮，以便每次用户按位置提示按钮，它将切换半透明放置提示的可见性。</span><span class="sxs-lookup"><span data-stu-id="561a0-195">The goal is to configure our button so that every time the user presses the placement hint button, it will toggle visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="561a0-196">第 1 步：放置提示对象基本场景层次结构中处于选定状态时，将农历模块移动到检查器面板中的空"仅限运行时"槽。</span><span class="sxs-lookup"><span data-stu-id="561a0-196">Step 1: Move the Lunar Module to the empty "runtime only" slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="561a0-197">![Lesson6 第 3 章 Step1im](images/Lesson6_Chapter3_step1im.PNG)步骤 2:现在，单击下拉列表中的状态显示，""没有函数。</span><span class="sxs-lookup"><span data-stu-id="561a0-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the dropdown list where it says, "no function."</span></span> <span data-ttu-id="561a0-198">转到"TogglePlacementHints，"，该菜单下选择"ToggleGameObjects （）。"</span><span class="sxs-lookup"><span data-stu-id="561a0-198">Go down to "TogglePlacementHints," and under that menu select "ToggleGameObjects ()."</span></span> <span data-ttu-id="561a0-199">打开和关闭以便每次按下按钮时进行显示或隐藏 ToggleGameObjects() 会切换位置提示。</span><span class="sxs-lookup"><span data-stu-id="561a0-199">ToggleGameObjects() will toggle the placement hints on and off so that they are visible or invisible every time the button is pressed.</span></span>
 <span data-ttu-id="561a0-200">![Lesson6 第 3 章 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="561a0-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="561a0-201">配置重置按钮</span><span class="sxs-lookup"><span data-stu-id="561a0-201">Configuring the Reset Button</span></span>

<span data-ttu-id="561a0-202">将让用户进行了错误的操作或对象，或只是想要体验的 rest 的意外引发的情况。</span><span class="sxs-lookup"><span data-stu-id="561a0-202">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to rest the experience.</span></span> <span data-ttu-id="561a0-203">重置按钮将添加重新启动体验的功能。</span><span class="sxs-lookup"><span data-stu-id="561a0-203">The reset button will add the ability to restart the experience.</span></span> 

<span data-ttu-id="561a0-204">第 1 步：选择重置按钮。</span><span class="sxs-lookup"><span data-stu-id="561a0-204">Step 1: Select the reset button.</span></span> <span data-ttu-id="561a0-205">在基本的场景中，它是名为"ResetRoundButton。"</span><span class="sxs-lookup"><span data-stu-id="561a0-205">In the base scene, it’s named "ResetRoundButton."</span></span> 

<span data-ttu-id="561a0-206">步骤 2：将农历模块从基本场景的层次结构拖到"按钮按下"下的空槽检查器面板。</span><span class="sxs-lookup"><span data-stu-id="561a0-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under "button pressed" the inspector panel.</span></span>
 <span data-ttu-id="561a0-207">![Lesson6 第 4 章 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="561a0-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="561a0-208">步骤 3:选择下拉列表菜单，指出:"函数"，然后悬停在"LaunchLunarModule。"</span><span class="sxs-lookup"><span data-stu-id="561a0-208">Step 3: Select the dropdown menu that says, "no function" and hover over "LaunchLunarModule."</span></span> <span data-ttu-id="561a0-209">现在，选择"resetModule （）。"</span><span class="sxs-lookup"><span data-stu-id="561a0-209">Now select "resetModule ()."</span></span>

![Lesson6 第 4 章 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="561a0-211">注意：你会注意到，默认情况下"GameObject.BroadcastMessage"配置为"ResetPlacement。"</span><span class="sxs-lookup"><span data-stu-id="561a0-211">Note: You will notice that by default the "GameObject.BroadcastMessage" is configured to "ResetPlacement."</span></span> <span data-ttu-id="561a0-212">这将广播消息为 RocketLauncher_Tutorial 每个子对象调用"ResetPlacement"。</span><span class="sxs-lookup"><span data-stu-id="561a0-212">This will broadcast a message called "ResetPlacement" for every child object of RocketLauncher_Tutorial.</span></span> <span data-ttu-id="561a0-213">对于"ResetPlacement()"有一个方法的任何对象将通过重置其位置来响应该消息。</span><span class="sxs-lookup"><span data-stu-id="561a0-213">Any object that has a method for "ResetPlacement()" will respond to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="561a0-214">启动农历模块</span><span class="sxs-lookup"><span data-stu-id="561a0-214">Launching the Lunar Module</span></span>
<span data-ttu-id="561a0-215">本章我们将配置的启动按钮。</span><span class="sxs-lookup"><span data-stu-id="561a0-215">This chapter we will be configuring the launch button.</span></span> <span data-ttu-id="561a0-216">这将允许用户按下按钮，并启动到空间农历模块。</span><span class="sxs-lookup"><span data-stu-id="561a0-216">This will permit the user to press the button and launch the Lunar Module into space.</span></span>

<span data-ttu-id="561a0-217">第 1 步：选择启动按钮 （基本场景中它名为"LaunchRoundButton"）。</span><span class="sxs-lookup"><span data-stu-id="561a0-217">Step 1: Select the launch button (in the base scene it’s named "LaunchRoundButton").</span></span> <span data-ttu-id="561a0-218">检查器面板中，将农历模块拖到"触摸结束"下的空槽。</span><span class="sxs-lookup"><span data-stu-id="561a0-218">Drag the Lunar Module to the empty slot under "Touch End" in the inspector panel.</span></span>
 <span data-ttu-id="561a0-219">![Lesson6 第 5 章 Step1im](images/Lesson6_Chapter5_step1im.PNG)步骤 2:选择下拉列表菜单，指出:"没有函数"。</span><span class="sxs-lookup"><span data-stu-id="561a0-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the dropdown menu that says, "no function."</span></span> <span data-ttu-id="561a0-220">将鼠标悬停"LaunchLunarModule"，然后选择"StopThruster （）。"</span><span class="sxs-lookup"><span data-stu-id="561a0-220">Hover over "LaunchLunarModule" and select "StopThruster ()."</span></span> <span data-ttu-id="561a0-221">这将控制用户想要向农历模块多少主旨的是。</span><span class="sxs-lookup"><span data-stu-id="561a0-221">This will control how much thrust the user wants to give to the Lunar Module.</span></span> 
 <span data-ttu-id="561a0-222">![Lesson6 第 5 章 Step2im](images/Lesson6_Chapter5_step2im.PNG)步骤 3:在"ButtonPressed()"（单击、 保持状态，并拖动） 将农历模块添加到空槽。</span><span class="sxs-lookup"><span data-stu-id="561a0-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Step 3: Under "ButtonPressed()", add the Lunar Module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="561a0-223">步骤 4：单击下拉列表菜单，显示"函数"，将鼠标悬停"LaunchLunarModule"并选择"StartThruster （）。"</span><span class="sxs-lookup"><span data-stu-id="561a0-223">Step 4: Click the dropdown menu that says, "no function" and hover over "LaunchLunarModule" and select "StartThruster ()."</span></span> 
 <span data-ttu-id="561a0-224">![Lesson6 第 5 章 Step4im](images/Lesson6_Chapter5_step4im.PNG)步骤 5:将音乐添加到农历模块，以便火箭时，将播放音乐。</span><span class="sxs-lookup"><span data-stu-id="561a0-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Step 5: Add music to the Lunar Module so that when the rocket takes off, the music will play.</span></span> <span data-ttu-id="561a0-225">若要执行此操作，将农历模块拖放到下一步"按钮 Pressed()"下的空槽。</span><span class="sxs-lookup"><span data-stu-id="561a0-225">To do this, drag the Lunar Module to the next empty slot under "Button Pressed()".</span></span>

<span data-ttu-id="561a0-226">步骤 6：选择下拉列表菜单，显示"函数"，将鼠标悬停"AudioSource"并选择"PlayOneShot (AudioClip)。"</span><span class="sxs-lookup"><span data-stu-id="561a0-226">Step 6: Select the dropdown menu that says, "no function" and hover over "AudioSource" and select "PlayOneShot (AudioClip)."</span></span> <span data-ttu-id="561a0-227">随意浏览各种 MRTK 中包含的声音。</span><span class="sxs-lookup"><span data-stu-id="561a0-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="561a0-228">对于此示例中，我们将继续使用"MRTK_Gem。"</span><span class="sxs-lookup"><span data-stu-id="561a0-228">For this example, we are going to stick with "MRTK_Gem."</span></span>
 <span data-ttu-id="561a0-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="561a0-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="561a0-230">恭喜 ！</span><span class="sxs-lookup"><span data-stu-id="561a0-230">Congratulations</span></span> 
<span data-ttu-id="561a0-231">你已完整地配置此应用程序 ！</span><span class="sxs-lookup"><span data-stu-id="561a0-231">You have fully configured this application!</span></span> <span data-ttu-id="561a0-232">现在时按播放，可以完全组装农历模块、 切换提示、 启动农历模块，并重置其再次执行该世界各地。</span><span class="sxs-lookup"><span data-stu-id="561a0-232">Now when you press play, you can fully assemble the Lunar Module, toggle hints, launch the Lunar Module, and reset it to do it all over again.</span></span>
