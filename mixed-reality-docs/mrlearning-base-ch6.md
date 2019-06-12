---
title: MR 学习基础模块 - 登月舱组装示例体验
description: 在本节课中，我们将结合在以前课程中所学的多个概念来创建一个独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730848"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a><span data-ttu-id="5cc1c-104">MR 学习基础模块 - 登月舱组装示例体验</span><span class="sxs-lookup"><span data-stu-id="5cc1c-104">MR Learning Base Module - Lunar Module Assembly Sample Experience</span></span>

<span data-ttu-id="5cc1c-105">在本节课中，我们将结合在以前课程中所学的多个概念来创建一个独特的示例体验。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-105">In this lesson, we will combine multiple concepts learned from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="5cc1c-106">我们将创建一个登月舱组装应用程序，用户需要借助该程序使用被追踪的双手拾起登月舱部件并尝试组装一个登月舱。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-106">We will create a lunar module assembly application whereby a user will need to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="5cc1c-107">我们将使用可按下的按钮切换放置提示，重置我们的体验，并将我们的登月舱发射到太空！</span><span class="sxs-lookup"><span data-stu-id="5cc1c-107">We will use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="5cc1c-108">在以后的教程中，我们将继续以此体验为基础，包括利用 Azure 空间定位点进行空间对齐的强大的多用户用例。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-108">In future tutorials, we will continue to build upon this experience, including powerful multi-user use-cases that leverages Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="5cc1c-109">目标</span><span class="sxs-lookup"><span data-stu-id="5cc1c-109">Objectives</span></span>

- <span data-ttu-id="5cc1c-110">结合以前课程中的多个概念来创建一个独特的体验</span><span class="sxs-lookup"><span data-stu-id="5cc1c-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="5cc1c-111">了解如何切换对象</span><span class="sxs-lookup"><span data-stu-id="5cc1c-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="5cc1c-112">使用可按按钮触发复杂事件</span><span class="sxs-lookup"><span data-stu-id="5cc1c-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="5cc1c-113">使用刚体的物理特性和力量</span><span class="sxs-lookup"><span data-stu-id="5cc1c-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="5cc1c-114">探索如何使用工具提示</span><span class="sxs-lookup"><span data-stu-id="5cc1c-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="5cc1c-115">说明</span><span class="sxs-lookup"><span data-stu-id="5cc1c-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="5cc1c-116">配置登月舱</span><span class="sxs-lookup"><span data-stu-id="5cc1c-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="5cc1c-117">在本章中，我们将了解创建示例体验所需的各种组件。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-117">In this chapter, we will be introduced to the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="5cc1c-118">将登月舱的预置组件添加到基本场景。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-118">Add the lunar module assembly prefab to your Base Scene.</span></span> <span data-ttu-id="5cc1c-119">为此，请在项目选项卡中搜索“Rocket Launcher_Tutorial”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-119">To do this, in your project tab, search for "Rocket Launcher_Tutorial."</span></span> <span data-ttu-id="5cc1c-120">还可以在 Assets>BaseModuleAssets>Prefabs 中找到预制件。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-120">You may also find the prefab in Assets>BaseModuleAssets>Prefabs.</span></span> <span data-ttu-id="5cc1c-121">可能会看到两个火箭发射器预制件；一个名为“tutorial”，另一个名为“complete”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-121">You may see two rocket launcher prefabs; one with the name "tutorial" and another with the name "complete."</span></span> <span data-ttu-id="5cc1c-122">将“Rocket Launcher_Tutorial”预制件拖动至基本场景。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-122">Drag the "Rocket Launcher_Tutorial" prefab to your Base Scene.</span></span> <span data-ttu-id="5cc1c-123">请随意在场景中设置预制块的位置。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-123">Feel free to position the placement of the prefab in your scene.</span></span>
   <span data-ttu-id="5cc1c-124">注意：“Rocket Launcher_Complete”预制件是完成的发射器，仅供参考。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-124">Note: The "Rocket Launcher_Complete" prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="5cc1c-126">如果在层次结构中展开“Rocket Launcher_Tutorial”游戏对象，并进一步展开“登月舱”对象，将看到几个子对象，其中包含一个名为“X 射线”的材料。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-126">If you expand the "Rocket Launcher_Tutorial" game object in your hierarchy, and further expand the "Lunar Module" object, you will see several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="5cc1c-127">通过“X 射线”材料，可获取略微半透明的颜色，我们将其用作用户的放置提示。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-127">The "x-ray" material allows for a slightly translucent color which we will use as placement hints for the user.</span></span> 

<span data-ttu-id="5cc1c-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 登月舱由五个部件组成，用户将与之交互，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="5cc1c-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user is going to interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="5cc1c-129">探测器外壳</span><span class="sxs-lookup"><span data-stu-id="5cc1c-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="5cc1c-130">油箱</span><span class="sxs-lookup"><span data-stu-id="5cc1c-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="5cc1c-131">电池</span><span class="sxs-lookup"><span data-stu-id="5cc1c-131">The Energy Cell</span></span>
4.  <span data-ttu-id="5cc1c-132">插接门户</span><span class="sxs-lookup"><span data-stu-id="5cc1c-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="5cc1c-133">外部传感器</span><span class="sxs-lookup"><span data-stu-id="5cc1c-133">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="5cc1c-135">注意：在基本场景层次结构中看到的游戏对象名称与场景中对象的名称不对应。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-135">Note: The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="5cc1c-136">步骤 2：为登月舱添加一个音频源。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="5cc1c-137">请确保在你的基本场景层次结构中选中登月舱，然后点击“添加组件”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-137">Make sure the lunar module is selected in your base scene hierarchy and click "Add Component."</span></span> <span data-ttu-id="5cc1c-138">搜索"音频源"，并将其添加到对象中。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-138">Search for "Audio Source" and add it to the object.</span></span> <span data-ttu-id="5cc1c-139">暂时将其留空。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-139">Leave it blank for now.</span></span> <span data-ttu-id="5cc1c-140">我们稍后会用它来播放发射声。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-140">We will use this to play the launching sound later.</span></span>
 <span data-ttu-id="5cc1c-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 步骤 3：添加脚本“切换放置提示。”</span><span class="sxs-lookup"><span data-stu-id="5cc1c-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Step 3: Add the script "toggle placement hints."</span></span> <span data-ttu-id="5cc1c-142">单击“添加组件”并搜索“切换放置提示。”</span><span class="sxs-lookup"><span data-stu-id="5cc1c-142">Click "Add Component" and search for "Toggle Placement Hints."</span></span> <span data-ttu-id="5cc1c-143">这是一个自定义脚本，通过该脚本可打开和关闭前面提到的半透明提示（使用 X 射线材料的对象）。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-143">This is a custom script that allows you to turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span> 
<span data-ttu-id="5cc1c-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 步骤 4：因为我们有 5 个对象，输入“5”作为游戏对象数组的大小。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Step 4: Since we have 5 objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="5cc1c-145">然后应会看到显示 5 个新元素。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-145">Then you should see 5 new elements appear.</span></span> 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="5cc1c-147">将每个半透明的对象拖到“无（游戏对象）”框中。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-147">Drag each of the translucent objects into the boxes that say "None (Game Object)."</span></span> <span data-ttu-id="5cc1c-148">从基地场景的登月舱中拖动以下对象：</span><span class="sxs-lookup"><span data-stu-id="5cc1c-148">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="5cc1c-149">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="5cc1c-149">•   Backpack</span></span>

<span data-ttu-id="5cc1c-150">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="5cc1c-150">•   GasTank</span></span>

<span data-ttu-id="5cc1c-151">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="5cc1c-151">•   Topleftbody</span></span>

<span data-ttu-id="5cc1c-152">•   Nose</span><span class="sxs-lookup"><span data-stu-id="5cc1c-152">•   Nose</span></span>

<span data-ttu-id="5cc1c-153">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="5cc1c-153">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="5cc1c-155">现已配置“切换放置提示”脚本。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-155">Now the "toggle placement hints" script is configured.</span></span> <span data-ttu-id="5cc1c-156">这将允许我们打开和关闭提示。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-156">This will allow us to turn the hints on and off.</span></span>

<span data-ttu-id="5cc1c-157">步骤 5：添加“发射登月舱”脚本。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-157">Step 5: Add the "launch lunar module" script.</span></span> <span data-ttu-id="5cc1c-158">点击“添加组件”按钮，搜索“发射登月舱”并将其选中。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-158">Click the "Add Component" button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="5cc1c-159">此脚本将负责发射登月舱。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-159">This script will be responsible for launching the lunar module.</span></span> <span data-ttu-id="5cc1c-160">当我们按下配置的按钮时，它会给登月舱的刚体组件增加一个向上的力，并使登月舱向上发射。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-160">When we press a configured button, it will add an upward force to the lunar module's rigid body component and will cause the module to launch upwards.</span></span> <span data-ttu-id="5cc1c-161">如果你在室内，登月舱可能会撞到你的天花板网。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="5cc1c-162">但如果你在户外，它会无限向上飞入太空。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-162">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="5cc1c-164">步骤 6：调整推力，使登月舱将顺利地往上飞。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="5cc1c-165">尝试使用值 0.01。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-165">Try a value of 0.01.</span></span> <span data-ttu-id="5cc1c-166">将“Rb”字段留空。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="5cc1c-167">Rb 代表刚体，该字段将在运行时自动填充。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-167">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="5cc1c-169">登月舱部件概述</span><span class="sxs-lookup"><span data-stu-id="5cc1c-169">Lunar Module Parts Overview</span></span>
<span data-ttu-id="5cc1c-170">登月舱部件父对象是用户将与之交互的对象的集合。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-170">The Lunar Module parts parent object is the collection of the objects that the user will interact with.</span></span> <span data-ttu-id="5cc1c-171">游戏对象名称（场景名称在括号中标注）如以下列表所示：</span><span class="sxs-lookup"><span data-stu-id="5cc1c-171">The game object names (with scene labeled names in paretheses) are provided in the list below:</span></span>

- <span data-ttu-id="5cc1c-172">Backpack（油箱）</span><span class="sxs-lookup"><span data-stu-id="5cc1c-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="5cc1c-173">GasTank（电池）</span><span class="sxs-lookup"><span data-stu-id="5cc1c-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="5cc1c-174">TopLeftBody（探测器外壳）</span><span class="sxs-lookup"><span data-stu-id="5cc1c-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="5cc1c-175">Nose（插接门户）</span><span class="sxs-lookup"><span data-stu-id="5cc1c-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="5cc1c-176">LeftTwirler（外部传感器）</span><span class="sxs-lookup"><span data-stu-id="5cc1c-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="5cc1c-177">注意，每个对象都有操作处理程序，如第 4 课所述。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-177">Notice that each of these objects has the manipulation handler, as discussed in lesson 4.</span></span> <span data-ttu-id="5cc1c-178">使用操作处理程序，用户可以抓取和操作对象。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-178">With the manipulation handler, users are able to grab and manipulate the object.</span></span> <span data-ttu-id="5cc1c-179">另请注意，“双手操纵型”设置为“移动和旋转”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-179">Also note that the setting "two handed manipulation type" is set to "move and rotate."</span></span> <span data-ttu-id="5cc1c-180">这只允许用户移动对象而不改变其大小，这是组装应用程序所需的功能。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-180">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="5cc1c-181">此外，未选中远程操作，以仅允许直接交互登月舱部件。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-181">In addition, far manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="5cc1c-183">部件组装演示脚本（如上所示）用于管理用户要在登月舱上放置的对象。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-183">The part assembly demo script (shown above) is the scrip that manages the objects to be placed on to the lunar module by the user.</span></span> 

<span data-ttu-id="5cc1c-184">“要放置的对象”字段是所选择的转换（如上图所示，为 backpack/油箱）和它可以连接到的对象。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-184">The "Object To Place" field is the transform that is selected (n the case of the image above, the backpack/fuel tank) with the object that it can connect to.</span></span> 

<span data-ttu-id="5cc1c-185">“近距离”和“远距离”设置负责确定某些部件贴靠或释放时的接近度。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-185">The "Near Distance" and "Far Distance" settings are responsible for determining the proximity to which parts will snap in place or be released.</span></span> <span data-ttu-id="5cc1c-186">例如，backpack/油箱需要离登月舱 0.1 个单位才能贴靠到位。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-186">For example, the backpack/fuel tank would need to be 0.1 units away from the lunar module to snap into place.</span></span> <span data-ttu-id="5cc1c-187">“远距离”设置了对象从登月舱拆离所需的位置。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-187">The "Far Distance" sets the location where the object needs to be to detach from the lunar module.</span></span> <span data-ttu-id="5cc1c-188">在本例中，用户必须用手抓住 backpack/油箱，将它从登月舱拉出 0.2 个单位才能防止它贴靠回原位。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="5cc1c-189">“工具提示对象”是场景中的工具提示标签。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-189">The "Tool Tip Object" is the tool tip label in the scene.</span></span> <span data-ttu-id="5cc1c-190">当对象贴靠到位时，标签将被禁用。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-190">When the objects are snapped in place, the label will be disabled.</span></span> 

<span data-ttu-id="5cc1c-191">将自动获取音频源。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-191">The Audio Source will be automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="5cc1c-192">放置提示按钮</span><span class="sxs-lookup"><span data-stu-id="5cc1c-192">Placement Hints Buttons</span></span>
<span data-ttu-id="5cc1c-193">在[第 2 课](mrlearning-base-ch2.md)中，了解了如何放置和配置按钮，以执行诸如在按下按钮时，更改物品颜色或使其播放声音等操作。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="5cc1c-194">在为切换放置提示配置按钮时，我们将继续使用这些原则。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="5cc1c-195">我们的目标是配置我们的按钮，这样每当用户按下放置提示按钮时，它就会切换半透明的放置提示的可见性。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-195">The goal is to configure our button so that every time the user presses the placement hint button, it will toggle visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="5cc1c-196">第 1 步：将登月舱移动到检查器面板中“仅运行时”的空槽，同时在基本场景层次结构中选择放置提示对象。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-196">Step 1: Move the Lunar Module to the empty "runtime only" slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="5cc1c-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 步骤 2：现在单击带有“无函数”字样的下拉列表。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the dropdown list where it says, "no function."</span></span> <span data-ttu-id="5cc1c-198">转到“TogglePlacementHints”，在菜单下选择“ToggleGameObjects()”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-198">Go down to "TogglePlacementHints," and under that menu select "ToggleGameObjects ()."</span></span> <span data-ttu-id="5cc1c-199">ToggleGameObjects() 将打开和关闭放置提示，以便每次按下按钮时它们都会显示或隐藏。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-199">ToggleGameObjects() will toggle the placement hints on and off so that they are visible or invisible every time the button is pressed.</span></span>
 <span data-ttu-id="5cc1c-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="5cc1c-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="5cc1c-201">配置重置按钮</span><span class="sxs-lookup"><span data-stu-id="5cc1c-201">Configuring the Reset Button</span></span>

<span data-ttu-id="5cc1c-202">在某些情况下，用户可能会犯错误，或者不小心扔掉了对象，或只是想中止体验。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-202">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to rest the experience.</span></span> <span data-ttu-id="5cc1c-203">重置按钮将添加重新启动体验的功能。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-203">The reset button will add the ability to restart the experience.</span></span> 

<span data-ttu-id="5cc1c-204">第 1 步：选择重置按钮。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-204">Step 1: Select the reset button.</span></span> <span data-ttu-id="5cc1c-205">在基本场景中，它被命名为“ResetRoundButton”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-205">In the base scene, it’s named "ResetRoundButton."</span></span> 

<span data-ttu-id="5cc1c-206">步骤 2：将登月舱从基本场景层次结构中拖拽到“按下按钮的”检查器面板下的空槽中。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under "button pressed" the inspector panel.</span></span>
 <span data-ttu-id="5cc1c-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="5cc1c-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="5cc1c-208">步骤 3:选择带有“无函数”字样的下拉菜单，并将鼠标悬停在“LaunchLunarModule”上。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-208">Step 3: Select the dropdown menu that says, "no function" and hover over "LaunchLunarModule."</span></span> <span data-ttu-id="5cc1c-209">现在选择“resetModule ()”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-209">Now select "resetModule ()."</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="5cc1c-211">注意：你会注意到默认情况下“GameObject.BroadcastMessage”被配置为“ResetPlacement”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-211">Note: You will notice that by default the "GameObject.BroadcastMessage" is configured to "ResetPlacement."</span></span> <span data-ttu-id="5cc1c-212">这将为 RocketLauncher_Tutorial 的每个子对象广播一条名为“ResetPlacement”的消息。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-212">This will broadcast a message called "ResetPlacement" for every child object of RocketLauncher_Tutorial.</span></span> <span data-ttu-id="5cc1c-213">任何具有“ResetPlacement()”方法的对象都将通过重置位置来响应该消息。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-213">Any object that has a method for "ResetPlacement()" will respond to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="5cc1c-214">发射登月舱</span><span class="sxs-lookup"><span data-stu-id="5cc1c-214">Launching the Lunar Module</span></span>
<span data-ttu-id="5cc1c-215">本章我们将配置发射按钮。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-215">This chapter we will be configuring the launch button.</span></span> <span data-ttu-id="5cc1c-216">这样，用户可以按下按钮，将登月舱发射到太空。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-216">This will permit the user to press the button and launch the Lunar Module into space.</span></span>

<span data-ttu-id="5cc1c-217">第 1 步：选择发射按钮（在基本场景中名为“LaunchRoundButton”）。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-217">Step 1: Select the launch button (in the base scene it’s named "LaunchRoundButton").</span></span> <span data-ttu-id="5cc1c-218">将登月舱拖到检查面板“触摸端”下的空槽。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-218">Drag the Lunar Module to the empty slot under "Touch End" in the inspector panel.</span></span>
 <span data-ttu-id="5cc1c-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 步骤 2：选择带有“无函数”字样的下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the dropdown menu that says, "no function."</span></span> <span data-ttu-id="5cc1c-220">将鼠标悬停在“LaunchLunarModule”上并选择“StopThruster()”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-220">Hover over "LaunchLunarModule" and select "StopThruster ()."</span></span> <span data-ttu-id="5cc1c-221">这将控制用户想给登月舱多少推力。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-221">This will control how much thrust the user wants to give to the Lunar Module.</span></span> 
 <span data-ttu-id="5cc1c-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 步骤 3：在“ButtonPressed()”下，将登月舱（单击、按住并拖动）添加到空槽。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Step 3: Under "ButtonPressed()", add the Lunar Module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="5cc1c-223">步骤 4：单击带有“无函数”字样的下拉菜单，并将鼠标悬停在“LaunchLunarModule”上并选择“StartThruster ()”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-223">Step 4: Click the dropdown menu that says, "no function" and hover over "LaunchLunarModule" and select "StartThruster ()."</span></span> 
 <span data-ttu-id="5cc1c-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 步骤 5：将音乐添加到登月舱，这样当火箭起飞时，音乐就会播放。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Step 5: Add music to the Lunar Module so that when the rocket takes off, the music will play.</span></span> <span data-ttu-id="5cc1c-225">为此，请将登月舱拖到“Button Pressed()”下的下一个空槽。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-225">To do this, drag the Lunar Module to the next empty slot under "Button Pressed()".</span></span>

<span data-ttu-id="5cc1c-226">步骤 6：选择带有“无函数”字样的下拉菜单，将鼠标悬停在“AudioSource”上，然后选择“PlayOneShot (AudioClip)”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-226">Step 6: Select the dropdown menu that says, "no function" and hover over "AudioSource" and select "PlayOneShot (AudioClip)."</span></span> <span data-ttu-id="5cc1c-227">随意浏览各种 MRTK 中附带的声音。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="5cc1c-228">对于本例，我们将一直使用“MRTK_Gem”。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-228">For this example, we are going to stick with "MRTK_Gem."</span></span>
 <span data-ttu-id="5cc1c-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="5cc1c-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="5cc1c-230">祝贺你</span><span class="sxs-lookup"><span data-stu-id="5cc1c-230">Congratulations</span></span> 
<span data-ttu-id="5cc1c-231">你已经完全配置了这个应用程序！</span><span class="sxs-lookup"><span data-stu-id="5cc1c-231">You have fully configured this application!</span></span> <span data-ttu-id="5cc1c-232">现在，当按下播放时，就可以完全组装登月舱、切换提示、发射登月舱，并重置它以重新执行此操作。</span><span class="sxs-lookup"><span data-stu-id="5cc1c-232">Now when you press play, you can fully assemble the Lunar Module, toggle hints, launch the Lunar Module, and reset it to do it all over again.</span></span>
