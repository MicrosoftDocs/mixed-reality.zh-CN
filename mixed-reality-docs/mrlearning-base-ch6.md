---
title: 入门教程-7。 创建农历模块示例应用程序
description: 在本课中，您将组合从前面的课程中学到的多个概念，以创建独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 3127ffceea08202fe9d978ad77f8fddb6fba60a3
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334377"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="a05b4-105">7. 创建农历模块示例应用程序</span><span class="sxs-lookup"><span data-stu-id="a05b4-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="a05b4-106">在本教程中，将多个概念与前面的课程结合起来，以创建独特的示例体验。</span><span class="sxs-lookup"><span data-stu-id="a05b4-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="a05b4-107">你将了解如何创建农历模块程序集应用程序，用户需要使用跟踪的手选取阴历模块部件，并尝试组装农历模块。</span><span class="sxs-lookup"><span data-stu-id="a05b4-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="a05b4-108">我们使用 pressable 按钮切换放置提示、重置我们的体验，以及将农历模块置于空间中！</span><span class="sxs-lookup"><span data-stu-id="a05b4-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="a05b4-109">在将来的教程中，我们将继续基于这一体验来构建，其中包括使用 Azure 空间锚点实现空间对齐的强大多用户用例。</span><span class="sxs-lookup"><span data-stu-id="a05b4-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="a05b4-110">目标</span><span class="sxs-lookup"><span data-stu-id="a05b4-110">Objectives</span></span>

- <span data-ttu-id="a05b4-111">结合以前课程中的多个概念来创建一个独特的体验</span><span class="sxs-lookup"><span data-stu-id="a05b4-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="a05b4-112">了解如何切换对象</span><span class="sxs-lookup"><span data-stu-id="a05b4-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="a05b4-113">使用可按按钮触发复杂事件</span><span class="sxs-lookup"><span data-stu-id="a05b4-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="a05b4-114">使用刚体的物理特性和力量</span><span class="sxs-lookup"><span data-stu-id="a05b4-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="a05b4-115">探索如何使用工具提示</span><span class="sxs-lookup"><span data-stu-id="a05b4-115">Explore the use of tool tips</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="a05b4-116">配置登月舱</span><span class="sxs-lookup"><span data-stu-id="a05b4-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="a05b4-117">在本部分中，我们将介绍创建示例体验所需的各种组件。</span><span class="sxs-lookup"><span data-stu-id="a05b4-117">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="a05b4-118">将农历模块程序集 prefab 添加到基础场景中。</span><span class="sxs-lookup"><span data-stu-id="a05b4-118">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="a05b4-119">为此，请在 "项目" 选项卡中导航到 "资产" > BaseModuleAssets > Prototyping "。</span><span class="sxs-lookup"><span data-stu-id="a05b4-119">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="a05b4-120">你将看到两个火箭启动器 prototyping，将火箭 Launcher_Tutorial prefab 拖到场景中，并根据需要进行定位。</span><span class="sxs-lookup"><span data-stu-id="a05b4-120">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="a05b4-121">火箭 Launcher_Complete prefab 是已完成的启动程序，旨在供参考。</span><span class="sxs-lookup"><span data-stu-id="a05b4-121">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="a05b4-123">如果在层次结构中展开 "火箭 Launcher_Tutorial 游戏" 对象并进一步展开农历模块对象，则会找到多个具有称为 "x 射线" 的子对象。</span><span class="sxs-lookup"><span data-stu-id="a05b4-123">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="a05b4-124">"X ray" 材料允许使用略微半透明的颜色，该颜色将用作用户的放置提示。</span><span class="sxs-lookup"><span data-stu-id="a05b4-124">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span>

    ![Lesson6 Chapter1.txt Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="a05b4-126">用户将与农历模块的以下部分进行交互，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="a05b4-126">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="a05b4-127">探测器外壳</span><span class="sxs-lookup"><span data-stu-id="a05b4-127">The Rover Enclosure</span></span>
    2. <span data-ttu-id="a05b4-128">油箱</span><span class="sxs-lookup"><span data-stu-id="a05b4-128">The Fuel Tank</span></span>
    3. <span data-ttu-id="a05b4-129">电池</span><span class="sxs-lookup"><span data-stu-id="a05b4-129">The Energy Cell</span></span>
    4. <span data-ttu-id="a05b4-130">插接门户</span><span class="sxs-lookup"><span data-stu-id="a05b4-130">The Docking Portal</span></span>
    5. <span data-ttu-id="a05b4-131">外部传感器</span><span class="sxs-lookup"><span data-stu-id="a05b4-131">The External sensor</span></span>

    ![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="a05b4-133">在基本场景层次结构中看到的游戏对象名称与场景中对象的名称不对应。</span><span class="sxs-lookup"><span data-stu-id="a05b4-133">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="a05b4-134">将音频源添加到 LunarModule 游戏对象。</span><span class="sxs-lookup"><span data-stu-id="a05b4-134">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="a05b4-135">确保在场景层次结构中选择 "LunarModule"，并单击 "添加组件"。</span><span class="sxs-lookup"><span data-stu-id="a05b4-135">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="a05b4-136">搜索 "音频源" 并将其添加到游戏对象。</span><span class="sxs-lookup"><span data-stu-id="a05b4-136">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="a05b4-137">现在，将 "AudioClip" 字段留空，但将特殊 Blend 设置从0更改为1，以便启用空间音频。</span><span class="sxs-lookup"><span data-stu-id="a05b4-137">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="a05b4-138">稍后将使用此音频源播放启动声音。</span><span class="sxs-lookup"><span data-stu-id="a05b4-138">You will use this audio source to play the launching sound later.</span></span>

    ![Lesson6 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="a05b4-140">添加脚本切换放置提示。</span><span class="sxs-lookup"><span data-stu-id="a05b4-140">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="a05b4-141">单击 "添加组件"，然后搜索切换放置提示。</span><span class="sxs-lookup"><span data-stu-id="a05b4-141">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="a05b4-142">这是一个自定义脚本，它使你可以打开和关闭透明提示（具有 x 光材料的对象），如前文所述。</span><span class="sxs-lookup"><span data-stu-id="a05b4-142">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![Lesson6 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="a05b4-144">由于我们有五个对象，请键入 "5" 作为游戏对象数组大小。</span><span class="sxs-lookup"><span data-stu-id="a05b4-144">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="a05b4-145">然后，将看到五个新元素出现。</span><span class="sxs-lookup"><span data-stu-id="a05b4-145">You will then see five new elements appear.</span></span>

    ![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="a05b4-147">将每个半透明对象拖到 "名称" （游戏对象）框中。</span><span class="sxs-lookup"><span data-stu-id="a05b4-147">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="a05b4-148">将以下对象从场景中的农历模块拖到对象数组字段中，如上面的图像所示：</span><span class="sxs-lookup"><span data-stu-id="a05b4-148">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="a05b4-150">现在已配置切换位置提示脚本，这使我们可以打开和关闭提示。</span><span class="sxs-lookup"><span data-stu-id="a05b4-150">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="a05b4-151">添加 "启动农历模块" 脚本。</span><span class="sxs-lookup"><span data-stu-id="a05b4-151">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="a05b4-152">单击 "添加组件" 按钮，搜索 "启动农历模块" 并将其选中。</span><span class="sxs-lookup"><span data-stu-id="a05b4-152">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="a05b4-153">此脚本将启动农历模块。</span><span class="sxs-lookup"><span data-stu-id="a05b4-153">This script launches the lunar module.</span></span> <span data-ttu-id="a05b4-154">按下某个已配置的按钮时，它会将向上强制添加到农历模块的硬正文部分，并使模块向上启动。</span><span class="sxs-lookup"><span data-stu-id="a05b4-154">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="a05b4-155">如果你在室内，登月舱可能会撞到你的天花板网。</span><span class="sxs-lookup"><span data-stu-id="a05b4-155">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="a05b4-156">如果你所在的区域具有高上限或无上限，则阴历模块会无限期地进入空间。</span><span class="sxs-lookup"><span data-stu-id="a05b4-156">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="a05b4-158">调整推力，使登月舱将顺利地往上飞。</span><span class="sxs-lookup"><span data-stu-id="a05b4-158">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="a05b4-159">尝试使用值 0.01。</span><span class="sxs-lookup"><span data-stu-id="a05b4-159">Try a value of 0.01.</span></span> <span data-ttu-id="a05b4-160">将“Rb”字段留空。</span><span class="sxs-lookup"><span data-stu-id="a05b4-160">Leave the "Rb" field blank.</span></span> <span data-ttu-id="a05b4-161">Rb 代表刚性体，此字段将在运行时自动填充。</span><span class="sxs-lookup"><span data-stu-id="a05b4-161">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="a05b4-163">农历模块部件概述</span><span class="sxs-lookup"><span data-stu-id="a05b4-163">Lunar Module Parts overview</span></span>

<span data-ttu-id="a05b4-164">农历 Module Part 父对象是用户与之交互的对象的集合。</span><span class="sxs-lookup"><span data-stu-id="a05b4-164">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="a05b4-165">下面的列表中提供了用括号标记名称的游戏对象名称：</span><span class="sxs-lookup"><span data-stu-id="a05b4-165">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="a05b4-166">背包（能源单元）</span><span class="sxs-lookup"><span data-stu-id="a05b4-166">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="a05b4-167">GasTank （燃料箱）</span><span class="sxs-lookup"><span data-stu-id="a05b4-167">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="a05b4-168">TopLeftBody（探测器外壳）</span><span class="sxs-lookup"><span data-stu-id="a05b4-168">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="a05b4-169">Nose（插接门户）</span><span class="sxs-lookup"><span data-stu-id="a05b4-169">Nose (Docking Portal)</span></span>
- <span data-ttu-id="a05b4-170">LeftTwirler（外部传感器）</span><span class="sxs-lookup"><span data-stu-id="a05b4-170">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="a05b4-171">请注意，其中每个对象都有一个操作处理程序，如第4课中所述。</span><span class="sxs-lookup"><span data-stu-id="a05b4-171">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="a05b4-172">此功能使用户能够获取和操作该对象。</span><span class="sxs-lookup"><span data-stu-id="a05b4-172">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="a05b4-173">另请注意，设置 "双向操作类型" 设置为 "移动和旋转"。</span><span class="sxs-lookup"><span data-stu-id="a05b4-173">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="a05b4-174">此选项只允许用户移动对象，而不会更改其大小（这是程序集应用程序所需的功能）。</span><span class="sxs-lookup"><span data-stu-id="a05b4-174">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="a05b4-175">此外，未选中 "远端操作"，只允许模块部件直接交互。</span><span class="sxs-lookup"><span data-stu-id="a05b4-175">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="a05b4-177">Part Assembly Demo script （如上所示）是管理用户在农历模块上的用户所放置对象的脚本。</span><span class="sxs-lookup"><span data-stu-id="a05b4-177">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="a05b4-178">"要放置的对象" 字段是选择的转换（如上图所示），背包/燃料箱与它连接到的对象相关联。</span><span class="sxs-lookup"><span data-stu-id="a05b4-178">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="a05b4-179">近距离和远距离设置确定了单元的位置或可释放的位置。</span><span class="sxs-lookup"><span data-stu-id="a05b4-179">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="a05b4-180">例如，背包/燃油水箱需要0.1 个单位，远离农历模块，才能将其放入到位。</span><span class="sxs-lookup"><span data-stu-id="a05b4-180">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="a05b4-181">"远处距离" 设置设置对象可以从农历模块分离之前的位置。</span><span class="sxs-lookup"><span data-stu-id="a05b4-181">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="a05b4-182">在本例中，用户必须用手抓住 backpack/油箱，将它从登月舱拉出 0.2 个单位才能防止它贴靠回原位。</span><span class="sxs-lookup"><span data-stu-id="a05b4-182">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="a05b4-183">工具提示对象是场景中的工具提示标签。</span><span class="sxs-lookup"><span data-stu-id="a05b4-183">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="a05b4-184">当对对象进行对齐时，将禁用该标签。</span><span class="sxs-lookup"><span data-stu-id="a05b4-184">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="a05b4-185">音频源会自动进行。</span><span class="sxs-lookup"><span data-stu-id="a05b4-185">The Audio Source is automatically grabbed.</span></span>

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="a05b4-186">配置放置提示按钮</span><span class="sxs-lookup"><span data-stu-id="a05b4-186">Configuring the Placement Hints button</span></span>

<span data-ttu-id="a05b4-187">在[第2课](mrlearning-base-ch2.md)中，您学习了如何设置按钮并对其进行配置，如更改项的颜色或使其在推送时播放声音。</span><span class="sxs-lookup"><span data-stu-id="a05b4-187">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="a05b4-188">在为切换放置提示配置按钮时，我们将继续使用这些原则。</span><span class="sxs-lookup"><span data-stu-id="a05b4-188">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="a05b4-189">目标是配置按钮，以便每次用户按下 "位置提示" 按钮时，它都会切换半透明放置提示的可见性。</span><span class="sxs-lookup"><span data-stu-id="a05b4-189">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="a05b4-190">在基本场景层次结构中选择放置提示对象时，将阴历模块移到检查器面板中的 "仅限空的运行时" 槽。</span><span class="sxs-lookup"><span data-stu-id="a05b4-190">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="a05b4-192">单击 "无函数" 下拉列表。</span><span class="sxs-lookup"><span data-stu-id="a05b4-192">Click the No Function dropdown list.</span></span> <span data-ttu-id="a05b4-193">向下移动到 "TogglePlacementHints"，并选择该菜单下的 "ToggleGameObjects （）"。</span><span class="sxs-lookup"><span data-stu-id="a05b4-193">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="a05b4-194">ToggleGameObjects （）打开和关闭放置提示，使其在每次按下按钮时可见或不可见。</span><span class="sxs-lookup"><span data-stu-id="a05b4-194">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="a05b4-196">配置重置按钮</span><span class="sxs-lookup"><span data-stu-id="a05b4-196">Configuring the Reset button</span></span>

<span data-ttu-id="a05b4-197">在某些情况下，用户会犯错误，意外地丢弃对象或只是想要重置体验。</span><span class="sxs-lookup"><span data-stu-id="a05b4-197">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="a05b4-198">"重置" 按钮增加了重新启动体验的能力。</span><span class="sxs-lookup"><span data-stu-id="a05b4-198">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="a05b4-199">选择 "重置" 按钮。</span><span class="sxs-lookup"><span data-stu-id="a05b4-199">Select the Reset button.</span></span> <span data-ttu-id="a05b4-200">在基本场景中，其名称为 ResetRoundButton。</span><span class="sxs-lookup"><span data-stu-id="a05b4-200">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="a05b4-201">将农历模块从基本场景层次结构拖到 "检查器" 面板上按下的按钮下的空槽。</span><span class="sxs-lookup"><span data-stu-id="a05b4-201">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="a05b4-203">选择 "无函数" 下拉菜单并将鼠标悬停在 LaunchLunarModule 上，然后选择 "resetModule" （）。</span><span class="sxs-lookup"><span data-stu-id="a05b4-203">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="a05b4-205">请注意，默认情况下，GameObject 配置为 ResetPlacement。</span><span class="sxs-lookup"><span data-stu-id="a05b4-205">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="a05b4-206">这会为 RocketLauncher_Tutorial 的每个子对象广播名为 ResetPlacement 的消息。</span><span class="sxs-lookup"><span data-stu-id="a05b4-206">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="a05b4-207">具有 ResetPlacement （）方法的任何对象通过重置其位置来响应该消息。</span><span class="sxs-lookup"><span data-stu-id="a05b4-207">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

## <a name="configuring-the-launch-button"></a><span data-ttu-id="a05b4-208">配置启动按钮</span><span class="sxs-lookup"><span data-stu-id="a05b4-208">Configuring the Launch button</span></span>

<span data-ttu-id="a05b4-209">本部分介绍如何配置 "启动" 按钮，该按钮允许用户按下按钮并将阴历模块启动到空间中。</span><span class="sxs-lookup"><span data-stu-id="a05b4-209">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="a05b4-210">选择 "启动" 按钮。</span><span class="sxs-lookup"><span data-stu-id="a05b4-210">Select the Launch button.</span></span> <span data-ttu-id="a05b4-211">在基本场景中，它称为 LaunchRoundButton。</span><span class="sxs-lookup"><span data-stu-id="a05b4-211">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="a05b4-212">将农历模块拖到检查器面板中 "Touch 结束" 下的空槽。</span><span class="sxs-lookup"><span data-stu-id="a05b4-212">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="a05b4-214">选择 "无函数" 下拉菜单并将鼠标悬停在 LaunchLunarModule 上，然后选择 "StopThruster" （）。</span><span class="sxs-lookup"><span data-stu-id="a05b4-214">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="a05b4-215">这可控制用户要为农历模块指定多少主旨是。</span><span class="sxs-lookup"><span data-stu-id="a05b4-215">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="a05b4-217">将农历模块从基本场景层次结构拖到 "检查器" 面板中按下的按钮下的空槽。</span><span class="sxs-lookup"><span data-stu-id="a05b4-217">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="a05b4-218">单击 "无函数" 下拉菜单，然后单击 "LaunchLunarModule"，并选择 "StartThruster （）"。</span><span class="sxs-lookup"><span data-stu-id="a05b4-218">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="a05b4-220">将音乐添加到农历模块，以便在火箭停止时播放音乐。</span><span class="sxs-lookup"><span data-stu-id="a05b4-220">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="a05b4-221">为此，请将农历模块拖到 "按下" 按钮下的下一个空槽（）。</span><span class="sxs-lookup"><span data-stu-id="a05b4-221">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="a05b4-222">选择 "无函数" 下拉菜单，悬停在 AudioSource 上，然后选择 PlayOneShot （AudioClip）。</span><span class="sxs-lookup"><span data-stu-id="a05b4-222">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="a05b4-223">随意浏览各种 MRTK 中附带的声音。</span><span class="sxs-lookup"><span data-stu-id="a05b4-223">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="a05b4-224">在此示例中，我们将使用 "MRTK_Gem"。</span><span class="sxs-lookup"><span data-stu-id="a05b4-224">In this example, we'll use "MRTK_Gem."</span></span>

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

## <a name="congratulations"></a><span data-ttu-id="a05b4-226">祝贺</span><span class="sxs-lookup"><span data-stu-id="a05b4-226">Congratulations</span></span>

<span data-ttu-id="a05b4-227">已完全配置此应用程序。</span><span class="sxs-lookup"><span data-stu-id="a05b4-227">You have fully configured this application.</span></span> <span data-ttu-id="a05b4-228">现在，当按下 "播放" 时，可以完全组装农历模块、切换提示、启动农历模块，并将其重置为重新开始。</span><span class="sxs-lookup"><span data-stu-id="a05b4-228">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
