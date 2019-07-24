---
title: MR 学习基础模块 - 登月舱组装示例体验
description: 在本节课中，我们将结合在以前课程中所学的多个概念来创建一个独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 79f2d3a4a3224533761ea2e4a7e73dc3d4d5e53e
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387683"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="8e5f3-104">7.创建农历模块示例应用程序</span><span class="sxs-lookup"><span data-stu-id="8e5f3-104">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="8e5f3-105">在本教程中, 我们将在前面的课程中介绍的多个概念结合起来, 以创建独特的示例体验。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-105">In this tutorial, we combine multiple concepts presented in the previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="8e5f3-106">我们将创建一个农历模块程序集应用程序, 用户需要使用跟踪的手选取阴历模块部件, 并尝试组装农历模块。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-106">We will create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts, and attempt to assemble a lunar module.</span></span> <span data-ttu-id="8e5f3-107">我们使用 pressable 按钮切换放置提示、重置我们的体验, 以及将农历模块置于空间中!</span><span class="sxs-lookup"><span data-stu-id="8e5f3-107">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="8e5f3-108">在将来的教程中, 我们将继续基于这一体验来构建, 其中包括使用 Azure 空间锚点实现空间对齐的强大多用户用例。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-108">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="8e5f3-109">目标</span><span class="sxs-lookup"><span data-stu-id="8e5f3-109">Objectives</span></span>

- <span data-ttu-id="8e5f3-110">结合以前课程中的多个概念来创建一个独特的体验</span><span class="sxs-lookup"><span data-stu-id="8e5f3-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="8e5f3-111">了解如何切换对象</span><span class="sxs-lookup"><span data-stu-id="8e5f3-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="8e5f3-112">使用可按按钮触发复杂事件</span><span class="sxs-lookup"><span data-stu-id="8e5f3-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="8e5f3-113">使用刚体的物理特性和力量</span><span class="sxs-lookup"><span data-stu-id="8e5f3-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="8e5f3-114">探索如何使用工具提示</span><span class="sxs-lookup"><span data-stu-id="8e5f3-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="8e5f3-115">说明</span><span class="sxs-lookup"><span data-stu-id="8e5f3-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="8e5f3-116">配置登月舱</span><span class="sxs-lookup"><span data-stu-id="8e5f3-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="8e5f3-117">在本部分中, 我们将介绍创建示例体验所需的各种组件。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-117">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="8e5f3-118">将农历模块程序集 prefab 添加到基础场景中。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-118">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="8e5f3-119">为此, 请在 "项目" 选项卡中搜索 "火箭 Launcher_Tutorial"。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-119">To do this, from the Project tab, search for Rocket Launcher_Tutorial.</span></span> 
<span data-ttu-id="8e5f3-120">查找资产 > BaseModuleAssets-> Prototyping 中的 prefab。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-120">Find the prefab in Assets->BaseModuleAssets->Prefabs.</span></span> <span data-ttu-id="8e5f3-121">还会看到两个火箭启动器 prototyping;一个名为 "教程", 另一个名为 "complete"。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-121">You'll also see two rocket launcher prefabs; one with the name "tutorial" and the other with the name "complete".</span></span> <span data-ttu-id="8e5f3-122">将火箭 Launcher_Tutorial prefab 拖到基础场景, 并根据需要进行定位。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-122">Drag the Rocket Launcher_Tutorial prefab to your base scene, and position as you wish.</span></span>
   <span data-ttu-id="8e5f3-123">注意:火箭 Launcher_Complete prefab 是已完成的启动程序, 旨在供参考。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-123">Note: The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="8e5f3-125">如果在层次结构中展开 "火箭 Launcher_Tutorial 游戏" 对象, 并进一步展开农历模块对象, 则会找到多个具有名称 "x 射线" 的子对象。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-125">If you expand the Rocket Launcher_Tutorial game object in your hierarchy, and further expand the Lunar Module object, you find several child objects that have a material called, "x-ray."</span></span> <span data-ttu-id="8e5f3-126">"X ray" 材料允许使用略微半透明的颜色, 我们将它们用作用户的放置提示。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-126">The "x-ray" material allows for a slightly translucent color that we will use as placement hints for the user.</span></span> 

<span data-ttu-id="8e5f3-127">![Lesson6 chapter1.txt Noteaim](images/Lesson6_Chapter1_noteaim.PNG)中有五个部分用于用户将与之交互的农历模块, 如下图所示:</span><span class="sxs-lookup"><span data-stu-id="8e5f3-127">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user will interact with as shown in the image below:</span></span>

1.  <span data-ttu-id="8e5f3-128">探测器外壳</span><span class="sxs-lookup"><span data-stu-id="8e5f3-128">The Rover Enclosure</span></span>
2.  <span data-ttu-id="8e5f3-129">油箱</span><span class="sxs-lookup"><span data-stu-id="8e5f3-129">The Fuel Tank</span></span>
3.  <span data-ttu-id="8e5f3-130">电池</span><span class="sxs-lookup"><span data-stu-id="8e5f3-130">The Energy Cell</span></span>
4.  <span data-ttu-id="8e5f3-131">插接门户</span><span class="sxs-lookup"><span data-stu-id="8e5f3-131">The Docking Portal</span></span> 
5.  <span data-ttu-id="8e5f3-132">外部传感器</span><span class="sxs-lookup"><span data-stu-id="8e5f3-132">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="8e5f3-134">注意:在基本场景层次结构中看到的游戏对象名称与场景中对象的名称不一致。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-134">Note: The Game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="8e5f3-135">步骤 2：为登月舱添加一个音频源。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-135">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="8e5f3-136">请确保在基本场景层次结构中选择了农历模块, 并单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-136">Make sure the lunar module is selected in your base scene hierarchy, and click Add Component.</span></span> <span data-ttu-id="8e5f3-137">搜索 "音频源", 并将其添加到对象。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-137">Search for Audio Source, and add it to the object.</span></span> <span data-ttu-id="8e5f3-138">暂时将其留空。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-138">Leave it blank for now.</span></span> <span data-ttu-id="8e5f3-139">我们稍后会用它来播放发射声。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-139">We will use this to play the launching sound later.</span></span>

 ![Lesson6 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
<span data-ttu-id="8e5f3-141">步骤 3：添加脚本, 切换放置提示。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-141">Step 3: Add the script, Toggle Placement Hints.</span></span> <span data-ttu-id="8e5f3-142">单击 "添加组件", 然后搜索切换放置提示。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-142">Click Add Component, and search for Toggle Placement Hints.</span></span> <span data-ttu-id="8e5f3-143">这是一个自定义脚本, 通过它可以打开和关闭前面提到的半透明提示 (带有 x 光材料的对象)。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span>  
![Lesson6 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
<span data-ttu-id="8e5f3-145">步骤 4：由于我们有五个对象, 为游戏对象数组大小键入 "5"。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-145">Step 4: Since we have five objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="8e5f3-146">然后, 将看到五个新元素出现。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-146">You'll then see five new elements appear.</span></span>  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="8e5f3-148">将每个半透明对象拖到 "名称 (游戏对象)" 框中。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-148">Drag each of the translucent objects into all the Name (Game Obect) boxes.</span></span>
<span data-ttu-id="8e5f3-149">从基地场景的登月舱中拖动以下对象：</span><span class="sxs-lookup"><span data-stu-id="8e5f3-149">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="8e5f3-150">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="8e5f3-150">•   Backpack</span></span>

<span data-ttu-id="8e5f3-151">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="8e5f3-151">•   GasTank</span></span>

<span data-ttu-id="8e5f3-152">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="8e5f3-152">•   Topleftbody</span></span>

<span data-ttu-id="8e5f3-153">•   Nose</span><span class="sxs-lookup"><span data-stu-id="8e5f3-153">•   Nose</span></span>

<span data-ttu-id="8e5f3-154">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="8e5f3-154">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="8e5f3-156">现在, 已配置切换放置提示脚本。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-156">Now the Toggle Placement Hints script is configured.</span></span> <span data-ttu-id="8e5f3-157">这使我们可以打开和关闭提示。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-157">This allow us to turn hints on and off.</span></span>

<span data-ttu-id="8e5f3-158">步骤 5：添加 "启动农历模块" 脚本。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-158">Step 5: Add the Launch Lunar Module script.</span></span> <span data-ttu-id="8e5f3-159">单击 "添加组件" 按钮, 搜索 "启动农历模块", 然后选择它。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-159">Click the Add Component button, search for "launch lunar module", and select it.</span></span> <span data-ttu-id="8e5f3-160">此脚本将启动农历模块。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-160">This script launches the lunar module.</span></span> <span data-ttu-id="8e5f3-161">按下某个已配置的按钮时, 它会将向上强制添加到农历模块的硬正文部分, 并使模块向上启动。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-161">When we press a configured button, it adds an upward force to the lunar module's rigid body component, and causes the module to launch upwards.</span></span> <span data-ttu-id="8e5f3-162">如果你在室内，登月舱可能会撞到你的天花板网。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-162">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="8e5f3-163">但如果你在户外，它会无限向上飞入太空。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-163">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="8e5f3-165">步骤 6：调整推力，使登月舱将顺利地往上飞。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-165">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="8e5f3-166">尝试使用值 0.01。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-166">Try a value of 0.01.</span></span> <span data-ttu-id="8e5f3-167">将“Rb”字段留空。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-167">Leave the "Rb" field blank.</span></span> <span data-ttu-id="8e5f3-168">Rb 代表刚体，该字段将在运行时自动填充。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-168">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="8e5f3-170">农历模块部件概述</span><span class="sxs-lookup"><span data-stu-id="8e5f3-170">Lunar Module Parts overview</span></span>
<span data-ttu-id="8e5f3-171">农历 Module Part 父对象是用户与之交互的对象的集合。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-171">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="8e5f3-172">下面的列表中提供了游戏对象名称, 其中包含在 paretheses 中标记为名称的场景:</span><span class="sxs-lookup"><span data-stu-id="8e5f3-172">The Game object names, with scene labeled names in paretheses, are provided in the list below:</span></span>

- <span data-ttu-id="8e5f3-173">Backpack（油箱）</span><span class="sxs-lookup"><span data-stu-id="8e5f3-173">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="8e5f3-174">GasTank（电池）</span><span class="sxs-lookup"><span data-stu-id="8e5f3-174">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="8e5f3-175">TopLeftBody（探测器外壳）</span><span class="sxs-lookup"><span data-stu-id="8e5f3-175">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="8e5f3-176">Nose（插接门户）</span><span class="sxs-lookup"><span data-stu-id="8e5f3-176">Nose (Docking Portal)</span></span>
- <span data-ttu-id="8e5f3-177">LeftTwirler（外部传感器）</span><span class="sxs-lookup"><span data-stu-id="8e5f3-177">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="8e5f3-178">请注意, 其中每个对象都有一个操作处理程序, 如第4课中所述。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-178">Notice that each of these objects has a manipulation handler as discussed in Lesson 4.</span></span> <span data-ttu-id="8e5f3-179">借助操作处理程序, 用户可以获取和操作该对象。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-179">With the manipulation handler, users can grab and manipulate the object.</span></span> <span data-ttu-id="8e5f3-180">另请注意, 设置 "将两个被处理的操作类型" 设置为 "移动和旋转"。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-180">Also note that the setting, Two Handed Manipulation Type is set to Move and Rotate.</span></span> <span data-ttu-id="8e5f3-181">这只允许用户移动对象而不改变其大小，这是组装应用程序所需的功能。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-181">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="8e5f3-182">此外, 未选中 "远端操作", 只允许模块部件直接交互。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-182">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="8e5f3-184">Part Assembly Demo script (如上所示) 是管理用户在农历模块上的用户所放置对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-184">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span> 

<span data-ttu-id="8e5f3-185">"要放置的对象" 字段是选择的转换 (如上图所示), 背包/燃料箱与它连接到的对象相关联。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-185">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span> 

<span data-ttu-id="8e5f3-186">近距离和远距离设置确定了单元的位置或可释放的位置。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-186">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="8e5f3-187">例如, 背包/燃油水箱需要0.1 个单位, 远离农历模块, 才能将其放入到位。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-187">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="8e5f3-188">"远处距离" 设置设置对象可以从农历模块分离之前的位置。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-188">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="8e5f3-189">在本例中，用户必须用手抓住 backpack/油箱，将它从登月舱拉出 0.2 个单位才能防止它贴靠回原位。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-189">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="8e5f3-190">工具提示对象是场景中的工具提示标签。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-190">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="8e5f3-191">当对对象进行对齐时, 将禁用该标签。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-191">When the objects are snapped in place, the label is disabled.</span></span> 

<span data-ttu-id="8e5f3-192">音频源会自动进行。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-192">The Audio Source is automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="8e5f3-193">放置提示按钮</span><span class="sxs-lookup"><span data-stu-id="8e5f3-193">Placement Hints buttons</span></span>
<span data-ttu-id="8e5f3-194">在[第 2 课](mrlearning-base-ch2.md)中，了解了如何放置和配置按钮，以执行诸如在按下按钮时，更改物品颜色或使其播放声音等操作。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-194">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="8e5f3-195">在为切换放置提示配置按钮时，我们将继续使用这些原则。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-195">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="8e5f3-196">目标是配置按钮, 以便每次用户按下 "位置提示" 按钮时, 它都会切换半透明放置提示的可见性。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-196">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="8e5f3-197">步骤 1：在基本场景层次结构中选择放置提示对象时, 将阴历模块移到检查器面板中的 "仅限空的运行时" 槽。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-197">Step 1: Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="8e5f3-198">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 步骤 2：现在, 单击 "无函数" 下拉列表。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-198">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the No Function dropdown list.</span></span> <span data-ttu-id="8e5f3-199">向下移动到 TogglePlacementHints, 然后在该菜单中选择 "ToggleGameObjects ()"。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-199">Go down to TogglePlacementHints, and under that menu select ToggleGameObjects ().</span></span> <span data-ttu-id="8e5f3-200">ToggleGameObjects () 打开和关闭放置提示, 使其在每次按下按钮时可见或不可见。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-200">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>  
 <span data-ttu-id="8e5f3-201">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8e5f3-201">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="8e5f3-202">配置重置按钮</span><span class="sxs-lookup"><span data-stu-id="8e5f3-202">Configuring the Reset button</span></span>

<span data-ttu-id="8e5f3-203">在某些情况下, 用户会犯错误, 或者意外地丢弃对象, 或者只是想要重置体验。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-203">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to reset the experience.</span></span> <span data-ttu-id="8e5f3-204">"重置" 按钮增加了重新启动体验的能力。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-204">The Reset button adds the ability to restart the experience.</span></span> 

<span data-ttu-id="8e5f3-205">步骤 1：选择 "重置" 按钮。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-205">Step 1: Select the Reset button.</span></span> <span data-ttu-id="8e5f3-206">在基本场景中, 其名称为 ResetRoundButton。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-206">In the base scene, it’s named, ResetRoundButton.</span></span> 

<span data-ttu-id="8e5f3-207">步骤 2：将农历模块从基本场景层次结构拖至按下 "检查器" 面板按钮下的空槽。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-207">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed the inspector panel.</span></span>
 <span data-ttu-id="8e5f3-208">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8e5f3-208">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="8e5f3-209">步骤 3：选择 "无函数" 下拉菜单, 并将鼠标悬停在 LaunchLunarModule 上, 选择 "resetModule ()"。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-209">Step 3: Select the No Function dropdown menu, and hover over LaunchLunarModule,  select resetModule ().</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="8e5f3-211">注意:请注意, 默认情况下, GameObject 配置为 ResetPlacement。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-211">Note: Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="8e5f3-212">这会为 RocketLauncher_Tutorial 的每个子对象广播一条名为 ResetPlacement 的消息。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-212">This broadcasts a message called, ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="8e5f3-213">具有 ResetPlacement () 方法的任何对象通过重置其位置来响应该消息。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-213">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="8e5f3-214">启动农历模块</span><span class="sxs-lookup"><span data-stu-id="8e5f3-214">Launching the lunar module</span></span>
<span data-ttu-id="8e5f3-215">本部分介绍如何配置 "启动" 按钮 explaings。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-215">This section explaings how to configure the Launch button.</span></span> <span data-ttu-id="8e5f3-216">这允许用户按下该按钮, 并将农历模块启动到空间中。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-216">This permits the user to press the button and launch the lunar module into space.</span></span>

<span data-ttu-id="8e5f3-217">步骤 1：选择 "启动" 按钮。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-217">Step 1: Select the Launch button.</span></span> <span data-ttu-id="8e5f3-218">在基本场景中, 它称为 LaunchRoundButton。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-218">In the base scene it’s called, LaunchRoundButton.</span></span> <span data-ttu-id="8e5f3-219">将农历模块拖到检查器面板中 "Touch 结束" 下的空槽。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-219">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>
 <span data-ttu-id="8e5f3-220">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 步骤 2：选择 "无函数" 下拉菜单, 将鼠标悬停在 LaunchLunarModule 上, 然后选择 "StopThruster" ()。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-220">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the No Function dropdown menu, and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="8e5f3-221">这可控制用户要为农历模块指定多少主旨是。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-221">This controls how much thrust the user wants to give to the lunar module.</span></span> 
 <span data-ttu-id="8e5f3-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8e5f3-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span></span>  
<span data-ttu-id="8e5f3-223">步骤 3：在 "ButtonPressed ()" 下, 将农历模块 (单击、按住和拖动) 添加到空槽。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-223">Step 3: Under ButtonPressed(), add the lunar module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="8e5f3-224">步骤 4：单击 "无函数" 下拉菜单, 将鼠标悬停在 LaunchLunarModule 上, 然后选择 "StartThruster" ()。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-224">Step 4: Click the No function dropdown menu, and hover over LaunchLunarModule, and select StartThruster ().</span></span> 
 <span data-ttu-id="8e5f3-225">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8e5f3-225">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span></span>  
<span data-ttu-id="8e5f3-226">步骤 5：将音乐添加到农历模块, 以便在火箭停止时播放音乐。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-226">Step 5: Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="8e5f3-227">为此, 请将农历模块拖到 "按下" 按钮下的下一个空槽 ()。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-227">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

<span data-ttu-id="8e5f3-228">步骤 6：选择 "无函数" 下拉菜单, 将鼠标悬停在 "AudioSource" 上, 然后选择 "PlayOneShot" (AudioClip)。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-228">Step 6: Select the No Function dropdown menu, hover over AudioSource, and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="8e5f3-229">随意浏览各种 MRTK 中附带的声音。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-229">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="8e5f3-230">在此示例中, 我们将使用 "MRTK_Gem"。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-230">For this example, we'll use "MRTK_Gem."</span></span>
 <span data-ttu-id="8e5f3-231">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="8e5f3-231">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="8e5f3-232">祝贺</span><span class="sxs-lookup"><span data-stu-id="8e5f3-232">Congratulations</span></span> 
<span data-ttu-id="8e5f3-233">已完全配置此应用程序。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-233">You have fully configured this application.</span></span> <span data-ttu-id="8e5f3-234">现在, 当按下 "播放" 时, 可以完全组装农历模块、切换提示、启动农历模块, 并将其重置为再次启动。</span><span class="sxs-lookup"><span data-stu-id="8e5f3-234">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module, and reset it to start all over again.</span></span>
