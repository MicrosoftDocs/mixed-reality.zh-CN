---
title: 入门教程-7。 创建农历模块示例应用程序
description: 在本课中，您将组合从前面的课程中学到的多个概念，以创建独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926520"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="05ef1-105">7. 创建农历模块示例应用程序</span><span class="sxs-lookup"><span data-stu-id="05ef1-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="05ef1-106">在本教程中，将多个概念与前面的课程结合起来，以创建独特的示例体验。</span><span class="sxs-lookup"><span data-stu-id="05ef1-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="05ef1-107">你将了解如何创建农历模块程序集应用程序，用户需要使用跟踪的手选取阴历模块部件，并尝试组装农历模块。</span><span class="sxs-lookup"><span data-stu-id="05ef1-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="05ef1-108">我们使用 pressable 按钮切换放置提示、重置我们的体验，以及将农历模块置于空间中！</span><span class="sxs-lookup"><span data-stu-id="05ef1-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="05ef1-109">在将来的教程中，我们将继续基于这一体验来构建，其中包括使用 Azure 空间锚点实现空间对齐的强大多用户用例。</span><span class="sxs-lookup"><span data-stu-id="05ef1-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="05ef1-110">目标</span><span class="sxs-lookup"><span data-stu-id="05ef1-110">Objectives</span></span>

- <span data-ttu-id="05ef1-111">结合以前课程中的多个概念来创建一个独特的体验</span><span class="sxs-lookup"><span data-stu-id="05ef1-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="05ef1-112">了解如何切换对象</span><span class="sxs-lookup"><span data-stu-id="05ef1-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="05ef1-113">使用可按按钮触发复杂事件</span><span class="sxs-lookup"><span data-stu-id="05ef1-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="05ef1-114">使用刚体的物理特性和力量</span><span class="sxs-lookup"><span data-stu-id="05ef1-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="05ef1-115">探索如何使用工具提示</span><span class="sxs-lookup"><span data-stu-id="05ef1-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="05ef1-116">说明</span><span class="sxs-lookup"><span data-stu-id="05ef1-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="05ef1-117">配置登月舱</span><span class="sxs-lookup"><span data-stu-id="05ef1-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="05ef1-118">在本部分中，我们将介绍创建示例体验所需的各种组件。</span><span class="sxs-lookup"><span data-stu-id="05ef1-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="05ef1-119">将农历模块程序集 prefab 添加到基础场景中。</span><span class="sxs-lookup"><span data-stu-id="05ef1-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="05ef1-120">为此，请在 "项目" 选项卡中导航到 "资产" > BaseModuleAssets > Prototyping "。</span><span class="sxs-lookup"><span data-stu-id="05ef1-120">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="05ef1-121">你将看到两个火箭启动器 prototyping，将火箭 Launcher_Tutorial prefab 拖到场景中，并根据需要进行定位。</span><span class="sxs-lookup"><span data-stu-id="05ef1-121">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="05ef1-122">火箭 Launcher_Complete prefab 是已完成的启动程序，旨在供参考。</span><span class="sxs-lookup"><span data-stu-id="05ef1-122">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="05ef1-124">如果在层次结构中展开 "火箭 Launcher_Tutorial 游戏" 对象并进一步展开农历模块对象，则会找到多个具有称为 "x 射线" 的子对象。</span><span class="sxs-lookup"><span data-stu-id="05ef1-124">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="05ef1-125">"X ray" 材料允许使用略微半透明的颜色，该颜色将用作用户的放置提示。</span><span class="sxs-lookup"><span data-stu-id="05ef1-125">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span> 

    ![Lesson6 Chapter1.txt Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="05ef1-127">用户将与农历模块的以下部分进行交互，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="05ef1-127">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="05ef1-128">探测器外壳</span><span class="sxs-lookup"><span data-stu-id="05ef1-128">The Rover Enclosure</span></span>
    2. <span data-ttu-id="05ef1-129">油箱</span><span class="sxs-lookup"><span data-stu-id="05ef1-129">The Fuel Tank</span></span>
    3. <span data-ttu-id="05ef1-130">电池</span><span class="sxs-lookup"><span data-stu-id="05ef1-130">The Energy Cell</span></span>
    4. <span data-ttu-id="05ef1-131">插接门户</span><span class="sxs-lookup"><span data-stu-id="05ef1-131">The Docking Portal</span></span>
    5. <span data-ttu-id="05ef1-132">外部传感器</span><span class="sxs-lookup"><span data-stu-id="05ef1-132">The External sensor</span></span>

    ![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="05ef1-134">在基本场景层次结构中看到的游戏对象名称与场景中对象的名称不对应。</span><span class="sxs-lookup"><span data-stu-id="05ef1-134">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="05ef1-135">将音频源添加到 LunarModule 游戏对象。</span><span class="sxs-lookup"><span data-stu-id="05ef1-135">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="05ef1-136">确保在场景层次结构中选择 "LunarModule"，并单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="05ef1-136">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="05ef1-137">搜索 "音频源" 并将其添加到游戏对象。</span><span class="sxs-lookup"><span data-stu-id="05ef1-137">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="05ef1-138">现在，将 "AudioClip" 字段留空，但将特殊 Blend 设置从0更改为1，以便启用空间音频。</span><span class="sxs-lookup"><span data-stu-id="05ef1-138">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="05ef1-139">稍后将使用此音频源播放启动声音。</span><span class="sxs-lookup"><span data-stu-id="05ef1-139">You will use this audio source to play the launching sound later.</span></span>

    ![Lesson6 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="05ef1-141">添加脚本切换放置提示。</span><span class="sxs-lookup"><span data-stu-id="05ef1-141">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="05ef1-142">单击 "添加组件"，然后搜索切换放置提示。</span><span class="sxs-lookup"><span data-stu-id="05ef1-142">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="05ef1-143">这是一个自定义脚本，它使你可以打开和关闭透明提示（具有 x 光材料的对象），如前文所述。</span><span class="sxs-lookup"><span data-stu-id="05ef1-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![Lesson6 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="05ef1-145">由于我们有五个对象，请键入 "5" 作为游戏对象数组大小。</span><span class="sxs-lookup"><span data-stu-id="05ef1-145">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="05ef1-146">然后，将看到五个新元素出现。</span><span class="sxs-lookup"><span data-stu-id="05ef1-146">You will then see five new elements appear.</span></span>

    ![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="05ef1-148">将每个半透明对象拖到 "名称" （游戏对象）框中。</span><span class="sxs-lookup"><span data-stu-id="05ef1-148">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="05ef1-149">将以下对象从场景中的农历模块拖到对象数组字段中，如上面的图像所示：</span><span class="sxs-lookup"><span data-stu-id="05ef1-149">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="05ef1-151">现在已配置切换位置提示脚本，这使我们可以打开和关闭提示。</span><span class="sxs-lookup"><span data-stu-id="05ef1-151">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="05ef1-152">添加 "启动农历模块" 脚本。</span><span class="sxs-lookup"><span data-stu-id="05ef1-152">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="05ef1-153">单击 "添加组件" 按钮，搜索 "启动农历模块" 并将其选中。</span><span class="sxs-lookup"><span data-stu-id="05ef1-153">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="05ef1-154">此脚本将启动农历模块。</span><span class="sxs-lookup"><span data-stu-id="05ef1-154">This script launches the lunar module.</span></span> <span data-ttu-id="05ef1-155">按下某个已配置的按钮时，它会将向上强制添加到农历模块的硬正文部分，并使模块向上启动。</span><span class="sxs-lookup"><span data-stu-id="05ef1-155">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="05ef1-156">如果你在室内，登月舱可能会撞到你的天花板网。</span><span class="sxs-lookup"><span data-stu-id="05ef1-156">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="05ef1-157">如果你所在的区域具有高上限或无上限，则阴历模块会无限期地进入空间。</span><span class="sxs-lookup"><span data-stu-id="05ef1-157">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="05ef1-159">调整推力，使登月舱将顺利地往上飞。</span><span class="sxs-lookup"><span data-stu-id="05ef1-159">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="05ef1-160">尝试使用值 0.01。</span><span class="sxs-lookup"><span data-stu-id="05ef1-160">Try a value of 0.01.</span></span> <span data-ttu-id="05ef1-161">将“Rb”字段留空。</span><span class="sxs-lookup"><span data-stu-id="05ef1-161">Leave the "Rb" field blank.</span></span> <span data-ttu-id="05ef1-162">Rb 代表刚性体，此字段将在运行时自动填充。</span><span class="sxs-lookup"><span data-stu-id="05ef1-162">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="05ef1-164">农历模块部件概述</span><span class="sxs-lookup"><span data-stu-id="05ef1-164">Lunar Module Parts overview</span></span>

<span data-ttu-id="05ef1-165">农历 Module Part 父对象是用户与之交互的对象的集合。</span><span class="sxs-lookup"><span data-stu-id="05ef1-165">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="05ef1-166">下面的列表中提供了用括号标记名称的游戏对象名称：</span><span class="sxs-lookup"><span data-stu-id="05ef1-166">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="05ef1-167">背包（能源单元）</span><span class="sxs-lookup"><span data-stu-id="05ef1-167">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="05ef1-168">GasTank （燃料箱）</span><span class="sxs-lookup"><span data-stu-id="05ef1-168">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="05ef1-169">TopLeftBody（探测器外壳）</span><span class="sxs-lookup"><span data-stu-id="05ef1-169">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="05ef1-170">Nose（插接门户）</span><span class="sxs-lookup"><span data-stu-id="05ef1-170">Nose (Docking Portal)</span></span>
- <span data-ttu-id="05ef1-171">LeftTwirler（外部传感器）</span><span class="sxs-lookup"><span data-stu-id="05ef1-171">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="05ef1-172">请注意，其中每个对象都有一个操作处理程序，如第4课中所述。</span><span class="sxs-lookup"><span data-stu-id="05ef1-172">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="05ef1-173">此功能使用户能够获取和操作该对象。</span><span class="sxs-lookup"><span data-stu-id="05ef1-173">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="05ef1-174">另请注意，设置 "双向操作类型" 设置为 "移动和旋转"。</span><span class="sxs-lookup"><span data-stu-id="05ef1-174">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="05ef1-175">此选项只允许用户移动对象，而不会更改其大小（这是程序集应用程序所需的功能）。</span><span class="sxs-lookup"><span data-stu-id="05ef1-175">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="05ef1-176">此外，未选中 "远端操作"，只允许模块部件直接交互。</span><span class="sxs-lookup"><span data-stu-id="05ef1-176">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="05ef1-178">Part Assembly Demo script （如上所示）是管理用户在农历模块上的用户所放置对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="05ef1-178">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="05ef1-179">"要放置的对象" 字段是选择的转换（如上图所示），背包/燃料箱与它连接到的对象相关联。</span><span class="sxs-lookup"><span data-stu-id="05ef1-179">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="05ef1-180">近距离和远距离设置确定了单元的位置或可释放的位置。</span><span class="sxs-lookup"><span data-stu-id="05ef1-180">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="05ef1-181">例如，背包/燃油水箱需要0.1 个单位，远离农历模块，才能将其放入到位。</span><span class="sxs-lookup"><span data-stu-id="05ef1-181">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="05ef1-182">"远处距离" 设置设置对象可以从农历模块分离之前的位置。</span><span class="sxs-lookup"><span data-stu-id="05ef1-182">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="05ef1-183">在本例中，用户必须用手抓住 backpack/油箱，将它从登月舱拉出 0.2 个单位才能防止它贴靠回原位。</span><span class="sxs-lookup"><span data-stu-id="05ef1-183">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="05ef1-184">工具提示对象是场景中的工具提示标签。</span><span class="sxs-lookup"><span data-stu-id="05ef1-184">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="05ef1-185">当对对象进行对齐时，将禁用该标签。</span><span class="sxs-lookup"><span data-stu-id="05ef1-185">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="05ef1-186">音频源会自动进行。</span><span class="sxs-lookup"><span data-stu-id="05ef1-186">The Audio Source is automatically grabbed.</span></span>

### <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="05ef1-187">配置放置提示按钮</span><span class="sxs-lookup"><span data-stu-id="05ef1-187">Configuring the Placement Hints button</span></span>

<span data-ttu-id="05ef1-188">在[第2课](mrlearning-base-ch2.md)中，您学习了如何设置按钮并对其进行配置，如更改项的颜色或使其在推送时播放声音。</span><span class="sxs-lookup"><span data-stu-id="05ef1-188">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="05ef1-189">在为切换放置提示配置按钮时，我们将继续使用这些原则。</span><span class="sxs-lookup"><span data-stu-id="05ef1-189">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="05ef1-190">目标是配置按钮，以便每次用户按下 "位置提示" 按钮时，它都会切换半透明放置提示的可见性。</span><span class="sxs-lookup"><span data-stu-id="05ef1-190">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="05ef1-191">在基本场景层次结构中选择放置提示对象时，将阴历模块移到检查器面板中的 "仅限空的运行时" 槽。</span><span class="sxs-lookup"><span data-stu-id="05ef1-191">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="05ef1-193">单击 "无函数" 下拉列表。</span><span class="sxs-lookup"><span data-stu-id="05ef1-193">Click the No Function dropdown list.</span></span> <span data-ttu-id="05ef1-194">向下移动到 "TogglePlacementHints"，并选择该菜单下的 "ToggleGameObjects （）"。</span><span class="sxs-lookup"><span data-stu-id="05ef1-194">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="05ef1-195">ToggleGameObjects （）打开和关闭放置提示，使其在每次按下按钮时可见或不可见。</span><span class="sxs-lookup"><span data-stu-id="05ef1-195">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a><span data-ttu-id="05ef1-197">配置重置按钮</span><span class="sxs-lookup"><span data-stu-id="05ef1-197">Configuring the Reset button</span></span>

<span data-ttu-id="05ef1-198">在某些情况下，用户会犯错误，意外地丢弃对象或只是想要重置体验。</span><span class="sxs-lookup"><span data-stu-id="05ef1-198">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="05ef1-199">"重置" 按钮增加了重新启动体验的能力。</span><span class="sxs-lookup"><span data-stu-id="05ef1-199">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="05ef1-200">选择 "重置" 按钮。</span><span class="sxs-lookup"><span data-stu-id="05ef1-200">Select the Reset button.</span></span> <span data-ttu-id="05ef1-201">在基本场景中，其名称为 ResetRoundButton。</span><span class="sxs-lookup"><span data-stu-id="05ef1-201">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="05ef1-202">将农历模块从基本场景层次结构拖到 "检查器" 面板上按下的按钮下的空槽。</span><span class="sxs-lookup"><span data-stu-id="05ef1-202">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="05ef1-204">选择 "无函数" 下拉菜单并将鼠标悬停在 LaunchLunarModule 上，然后选择 "resetModule" （）。</span><span class="sxs-lookup"><span data-stu-id="05ef1-204">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="05ef1-206">请注意，默认情况下，GameObject 配置为 ResetPlacement。</span><span class="sxs-lookup"><span data-stu-id="05ef1-206">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="05ef1-207">这会为 RocketLauncher_Tutorial 的每个子对象广播名为 ResetPlacement 的消息。</span><span class="sxs-lookup"><span data-stu-id="05ef1-207">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="05ef1-208">具有 ResetPlacement （）方法的任何对象通过重置其位置来响应该消息。</span><span class="sxs-lookup"><span data-stu-id="05ef1-208">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

### <a name="configuring-the-launch-button"></a><span data-ttu-id="05ef1-209">配置启动按钮</span><span class="sxs-lookup"><span data-stu-id="05ef1-209">Configuring the Launch button</span></span>

<span data-ttu-id="05ef1-210">本部分介绍如何配置 "启动" 按钮，该按钮允许用户按下按钮并将阴历模块启动到空间中。</span><span class="sxs-lookup"><span data-stu-id="05ef1-210">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="05ef1-211">选择 "启动" 按钮。</span><span class="sxs-lookup"><span data-stu-id="05ef1-211">Select the Launch button.</span></span> <span data-ttu-id="05ef1-212">在基本场景中，它称为 LaunchRoundButton。</span><span class="sxs-lookup"><span data-stu-id="05ef1-212">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="05ef1-213">将农历模块拖到检查器面板中 "Touch 结束" 下的空槽。</span><span class="sxs-lookup"><span data-stu-id="05ef1-213">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="05ef1-215">选择 "无函数" 下拉菜单并将鼠标悬停在 LaunchLunarModule 上，然后选择 "StopThruster" （）。</span><span class="sxs-lookup"><span data-stu-id="05ef1-215">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="05ef1-216">这可控制用户要为农历模块指定多少主旨是。</span><span class="sxs-lookup"><span data-stu-id="05ef1-216">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="05ef1-218">将农历模块从基本场景层次结构拖到 "检查器" 面板中按下的按钮下的空槽。</span><span class="sxs-lookup"><span data-stu-id="05ef1-218">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="05ef1-219">单击 "无函数" 下拉菜单，然后单击 "LaunchLunarModule"，并选择 "StartThruster （）"。</span><span class="sxs-lookup"><span data-stu-id="05ef1-219">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="05ef1-221">将音乐添加到农历模块，以便在火箭停止时播放音乐。</span><span class="sxs-lookup"><span data-stu-id="05ef1-221">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="05ef1-222">为此，请将农历模块拖到 "按下" 按钮下的下一个空槽（）。</span><span class="sxs-lookup"><span data-stu-id="05ef1-222">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="05ef1-223">选择 "无函数" 下拉菜单，悬停在 AudioSource 上，然后选择 PlayOneShot （AudioClip）。</span><span class="sxs-lookup"><span data-stu-id="05ef1-223">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="05ef1-224">随意浏览各种 MRTK 中附带的声音。</span><span class="sxs-lookup"><span data-stu-id="05ef1-224">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="05ef1-225">在此示例中，我们将使用 "MRTK_Gem"。</span><span class="sxs-lookup"><span data-stu-id="05ef1-225">In this example, we'll use "MRTK_Gem."</span></span>

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a><span data-ttu-id="05ef1-227">祝贺</span><span class="sxs-lookup"><span data-stu-id="05ef1-227">Congratulations</span></span>

<span data-ttu-id="05ef1-228">已完全配置此应用程序。</span><span class="sxs-lookup"><span data-stu-id="05ef1-228">You have fully configured this application.</span></span> <span data-ttu-id="05ef1-229">现在，当按下 "播放" 时，可以完全组装农历模块、切换提示、启动农历模块，并将其重置为重新开始。</span><span class="sxs-lookup"><span data-stu-id="05ef1-229">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
