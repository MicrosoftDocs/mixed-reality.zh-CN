---
title: 入门教程 - 7. 创建登月舱示例应用程序
description: 本课程将结合以前课程中所介绍的多个概念来创建一个独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031562"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="36508-105">7.创建登月舱示例应用程序</span><span class="sxs-lookup"><span data-stu-id="36508-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="36508-106">本教程结合前面课程中介绍的多个概念创建一个独特的示例体验。</span><span class="sxs-lookup"><span data-stu-id="36508-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="36508-107">其中将会介绍如何创建一个部件装配应用程序，其用户需要使用跟踪手来拾取部件并尝试装配登月舱。</span><span class="sxs-lookup"><span data-stu-id="36508-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="36508-108">你将使用可按按钮打开和关闭位置提示、重置体验，并将登月舱发射到太空！</span><span class="sxs-lookup"><span data-stu-id="36508-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="36508-109">在以后的教程中，你将继续基于此体验生成应用程序，包括强大的利用 Azure 空间定位点进行空间对齐的多用户用例。</span><span class="sxs-lookup"><span data-stu-id="36508-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="36508-110">目标</span><span class="sxs-lookup"><span data-stu-id="36508-110">Objectives</span></span>

* <span data-ttu-id="36508-111">结合以前课程中的多个概念来创建一个独特的体验</span><span class="sxs-lookup"><span data-stu-id="36508-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="36508-112">了解如何切换对象</span><span class="sxs-lookup"><span data-stu-id="36508-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="36508-113">使用可按按钮触发复杂事件</span><span class="sxs-lookup"><span data-stu-id="36508-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="36508-114">使用刚体的物理特性和力量</span><span class="sxs-lookup"><span data-stu-id="36508-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="36508-115">探索如何使用工具提示</span><span class="sxs-lookup"><span data-stu-id="36508-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="36508-116">登月舱部件概述</span><span class="sxs-lookup"><span data-stu-id="36508-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="36508-117">在本部分，你将创建一个简单的部件装配质询方案，其中，用户的目标是将分散在台面上的五个部件定位在登月舱中的适当位置。</span><span class="sxs-lookup"><span data-stu-id="36508-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="36508-118">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="36508-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="36508-119">将火箭发射器预制件添加到场景中</span><span class="sxs-lookup"><span data-stu-id="36508-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="36508-120">为所有部件启用对象操作</span><span class="sxs-lookup"><span data-stu-id="36508-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="36508-121">添加并配置“部件装配演示(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="36508-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="36508-122">MRTK 中未包含“部件装配演示(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="36508-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="36508-123">本教程的资产中随附了该组件。</span><span class="sxs-lookup"><span data-stu-id="36508-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="36508-124">1.将火箭发射器预制件添加到场景中</span><span class="sxs-lookup"><span data-stu-id="36508-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="36508-125">在“项目”窗口中导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件” > “RocketLauncher”文件夹，将“RocketLauncher”预制件拖放到“层次结构”窗口以将其添加到场景中，然后将其定位在适当的位置，例如：     </span><span class="sxs-lookup"><span data-stu-id="36508-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="36508-126">变换位置 X = 1.5，Y = -0.4，Z = 0，使之位于用户右侧的腰部高度处</span><span class="sxs-lookup"><span data-stu-id="36508-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="36508-127">转换旋转 X = 0，Y = 180，Z = 0，使该体验的主要功能面对用户</span><span class="sxs-lookup"><span data-stu-id="36508-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="36508-129">2.为所有部件启用对象操作</span><span class="sxs-lookup"><span data-stu-id="36508-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="36508-130">在“层次结构”窗口中找到“RocketLauncher”>“LunarModuleParts”对象，选择所有**子对象**，添加“操作处理程序(脚本)”组件和“近距交互可抓取对象(脚本)”组件，然后按如下所述配置“操作处理程序(脚本)”：   </span><span class="sxs-lookup"><span data-stu-id="36508-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="36508-131">取消选中“允许远距操作”复选框，以便仅允许近距交互 </span><span class="sxs-lookup"><span data-stu-id="36508-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="36508-132">将“双手操作类型”更改为“移动旋转”，以禁用缩放  </span><span class="sxs-lookup"><span data-stu-id="36508-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="36508-134">有关如何实现对象操作的提示和分步说明，可参阅[操作 3D 对象](mrlearning-base-ch4.md#manipulating-3d-objects)中的说明。</span><span class="sxs-lookup"><span data-stu-id="36508-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="36508-135">3.添加并配置“部件装配演示(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="36508-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="36508-136">在仍选中了所有 LunarModuleParts 子对象的情况下，添加“音频源”组件，然后按如下所述对其进行配置： </span><span class="sxs-lookup"><span data-stu-id="36508-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="36508-137">将适当的音频剪辑（例如 MRKT_Scale_Start）分配到“AudioClip”字段 </span><span class="sxs-lookup"><span data-stu-id="36508-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="36508-138">取消选中“唤醒时播放”复选框，以便在加载场景时不会自动播放该音频剪辑 </span><span class="sxs-lookup"><span data-stu-id="36508-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="36508-139">将“空间混合”更改为 1，以启用空间音频 </span><span class="sxs-lookup"><span data-stu-id="36508-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="36508-141">在仍选中了所有 LunarModuleParts 子对象的情况下，添加“部件装配演示(脚本)”组件： </span><span class="sxs-lookup"><span data-stu-id="36508-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="36508-143">在“层次结构”窗口中选择“RoverEnclosure”对象，并按如下所述配置其“部件装配演示(脚本)”组件：  </span><span class="sxs-lookup"><span data-stu-id="36508-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="36508-144">在“要定位的对象”字段中分配该对象**本身**，在本例中为 RoverEnclosure 对象 </span><span class="sxs-lookup"><span data-stu-id="36508-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="36508-145">在“定位位置”字段中分配相应的“PlacementHints”对象，在本例中为 RoverEnclosure_PlacementHint 对象  </span><span class="sxs-lookup"><span data-stu-id="36508-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="36508-146">在“工具提示对象”字段中分配相应的“ToolTip”对象，在本例中为 RoverEnclosure_ToolTip 对象  </span><span class="sxs-lookup"><span data-stu-id="36508-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="36508-147">在“音频源”字段中分配该对象**本身**，在本例中为 RoverEnclosure 对象 </span><span class="sxs-lookup"><span data-stu-id="36508-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="36508-149">针对其他每个 LunarModuleParts 子对象（即 FuelTank、EnergyCell、DockingPortal 和 ExternalSensor）**重复**上述步骤。</span><span class="sxs-lookup"><span data-stu-id="36508-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="36508-150">如果现在进入“游戏”模式，并使某个“要定位的对象”靠近其相应的“定位位置”，将会发现：</span><span class="sxs-lookup"><span data-stu-id="36508-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="36508-151">该对象将会卡入就位，并成为 LunarModule 对象下的父级，因此成了登月舱的部件</span><span class="sxs-lookup"><span data-stu-id="36508-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="36508-152">该对象上的音频源将在该对象的位置播放分配的音频剪辑</span><span class="sxs-lookup"><span data-stu-id="36508-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="36508-153">相应的工具提示对象将会隐藏</span><span class="sxs-lookup"><span data-stu-id="36508-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="36508-155">有关如何使用编辑器中的输入模拟功能的提示，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用编辑器中的手写输入模拟来测试场景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。</span><span class="sxs-lookup"><span data-stu-id="36508-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="36508-156">配置登月舱</span><span class="sxs-lookup"><span data-stu-id="36508-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="36508-157">在本部分，你将在火箭发射器应用程序中添加附加的功能，使用户能够：</span><span class="sxs-lookup"><span data-stu-id="36508-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="36508-158">与登月舱交互</span><span class="sxs-lookup"><span data-stu-id="36508-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="36508-159">将登月舱发射到太空，并在发射时播放声音</span><span class="sxs-lookup"><span data-stu-id="36508-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="36508-160">重置应用程序，使登月舱和所有部件复位到其原始位置</span><span class="sxs-lookup"><span data-stu-id="36508-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="36508-161">隐藏位置提示，使部件装配质询变得更困难。</span><span class="sxs-lookup"><span data-stu-id="36508-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="36508-162">若要实现此目的，请执行以下主要步骤：</span><span class="sxs-lookup"><span data-stu-id="36508-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="36508-163">启用对象操作</span><span class="sxs-lookup"><span data-stu-id="36508-163">Enable object manipulation</span></span>
2. <span data-ttu-id="36508-164">启用物理学</span><span class="sxs-lookup"><span data-stu-id="36508-164">Enable physics</span></span>
3. <span data-ttu-id="36508-165">添加“音频源”组件</span><span class="sxs-lookup"><span data-stu-id="36508-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="36508-166">添加并配置“发射登月舱(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="36508-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="36508-167">添加并配置“切换位置提示(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="36508-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="36508-168">MRTK 中未包含“发射登月舱(脚本)”组件和“切换位置提示(脚本)”组件。</span><span class="sxs-lookup"><span data-stu-id="36508-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="36508-169">本教程的资产中随附了这些组件。</span><span class="sxs-lookup"><span data-stu-id="36508-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="36508-170">1.启用对象操作</span><span class="sxs-lookup"><span data-stu-id="36508-170">1. Enable object manipulation</span></span>

<span data-ttu-id="36508-171">在“层次结构”窗口中选择“RocketLauncher”>“LunarModule”对象，添加“操作处理程序(脚本)”组件和“近距交互可抓取对象(脚本)”组件，然后按如下所述配置“操作处理程序(脚本)”：   </span><span class="sxs-lookup"><span data-stu-id="36508-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="36508-172">取消选中“允许远距操作”复选框，以便仅允许近距交互 </span><span class="sxs-lookup"><span data-stu-id="36508-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="36508-173">将“双手操作类型”更改为“移动旋转”，以禁用缩放 </span><span class="sxs-lookup"><span data-stu-id="36508-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="36508-175">2.启用物理学</span><span class="sxs-lookup"><span data-stu-id="36508-175">2. Enable physics</span></span>

<span data-ttu-id="36508-176">在仍选中了“RocketLauncher”>“LunarModule”对象的情况下，添加一个“刚体”组件，并按如下所述对其进行配置：  </span><span class="sxs-lookup"><span data-stu-id="36508-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="36508-177">取消选中“使用重力”复选框，使登月舱不受重力的影响 </span><span class="sxs-lookup"><span data-stu-id="36508-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="36508-178">选中“遵守运动力学”复选框，使登月舱最初不受物理作用力的影响 </span><span class="sxs-lookup"><span data-stu-id="36508-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="36508-180">3.添加“音频源”组件</span><span class="sxs-lookup"><span data-stu-id="36508-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="36508-181">在仍选中了“RocketLauncher”>“LunarModule”对象的情况下，添加一个“音频源”组件，并按如下所述对其进行配置：  </span><span class="sxs-lookup"><span data-stu-id="36508-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="36508-182">将“空间混合”更改为 1，以启用空间音频 </span><span class="sxs-lookup"><span data-stu-id="36508-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="36508-184">4.添加并配置“发射登月舱(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="36508-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="36508-185">在仍选中了“RocketLauncher”>“LunarModule”对象的情况下，添加“发射登月舱(脚本)”组件，并按如下所述对其进行配置：  </span><span class="sxs-lookup"><span data-stu-id="36508-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="36508-186">更改“推力”值（例如，更改为 0.01），使登月舱在发射后优雅飞行 </span><span class="sxs-lookup"><span data-stu-id="36508-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="36508-188">5.添加并配置“切换位置提示(脚本)”组件</span><span class="sxs-lookup"><span data-stu-id="36508-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="36508-189">在仍选中了“RocketLauncher”>“LunarModule”对象的情况下，添加“切换位置提示(脚本)”组件，并按如下所述对其进行配置：  </span><span class="sxs-lookup"><span data-stu-id="36508-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="36508-190">将游戏对象数组“大小”属性设置为 5 </span><span class="sxs-lookup"><span data-stu-id="36508-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="36508-191">将“RocketLauncher”>“LunarModule”>“PlacementHints”对象的每个**子对象**分配到游戏对象数组中的“元素”字段：  </span><span class="sxs-lookup"><span data-stu-id="36508-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="36508-193">配置“发射”按钮</span><span class="sxs-lookup"><span data-stu-id="36508-193">Configuring the Launch button</span></span>

<span data-ttu-id="36508-194">在“层次结构”窗口中选择“RocketLauncher”>“Buttons”>“LaunchButton”对象，然后在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“LunarModule”对象配置为接收该事件，然后将“LaunchLunarModule.StartThruster”定义为要触发的操作：    </span><span class="sxs-lookup"><span data-stu-id="36508-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="36508-196">有关如何实现事件的提示，可参阅[手动跟踪手势和可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)中的说明。</span><span class="sxs-lookup"><span data-stu-id="36508-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="36508-197">在仍选中了“RocketLauncher”>“Buttons”>“LaunchButton”对象的情况下，在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“LunarModule”对象配置为接收该事件，将“AudioSource.PlayOneShot”定义为要触发的操作，然后将适当的音频剪辑（例如 MRTK_Gem 音频剪辑）分配到“音频剪辑”字段：     </span><span class="sxs-lookup"><span data-stu-id="36508-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="36508-199">在仍选中了“RocketLauncher”>“Buttons”>“LaunchButton”对象的情况下，在“可按按钮(脚本)”组件中创建新的 **Touch End ()** 事件，将“LunarModule”对象配置为接收该事件，然后将“LaunchLunarModule.StopThruster”定义为要触发的操作：    </span><span class="sxs-lookup"><span data-stu-id="36508-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="36508-201">如果现在进入“游戏”模式并按下“发射”按钮，将会听到播放的音频剪辑；如果按住“发射”按钮一秒或更长时间，将会看到登月舱已发射到太空：</span><span class="sxs-lookup"><span data-stu-id="36508-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="36508-203">配置“重置”按钮</span><span class="sxs-lookup"><span data-stu-id="36508-203">Configuring the Reset button</span></span>

<span data-ttu-id="36508-204">在“层次结构”窗口中选择“RocketLauncher”>“Buttons”>“ResetButton”对象，然后在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“LunarModule”对象配置为接收该事件，然后将“LaunchLunarModule.ResetModule”定义为要触发的操作：    </span><span class="sxs-lookup"><span data-stu-id="36508-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="36508-206">在仍选中了“RocketLauncher”>“Buttons”>“ResetButton”对象的情况下，在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“RocketLauncher”对象配置为接收该事件，将“GameObject.BroadcastMessage”定义为要触发的操作，然后在消息字段中输入 **ResetPlacement**：    </span><span class="sxs-lookup"><span data-stu-id="36508-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="36508-208">GameObject.BroadcastMessage 操作会将 ResetPlacement 消息从 RocketLauncher 对象发送到其所有子对象。</span><span class="sxs-lookup"><span data-stu-id="36508-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="36508-209">具有 ResetPlacement 函数（在添加到所有 LunarModuleParts 子对象的“部件装配演示(脚本)”组件中定义）的任何子对象将调用 ResetPlacement 函数，以重置该子对象的位置。</span><span class="sxs-lookup"><span data-stu-id="36508-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="36508-210">如果现在进入“游戏”模式，移动某些部件和/或发射登月舱，然后按“重置”按钮，则将看到这些部件和/或登月舱重置到其原始位置：</span><span class="sxs-lookup"><span data-stu-id="36508-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="36508-212">配置“位置提示”按钮</span><span class="sxs-lookup"><span data-stu-id="36508-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="36508-213">在“层次结构”窗口中选择“RocketLauncher”>“Buttons”>“HintsButton”对象，然后在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“LunarModule”对象配置为接收该事件，然后将“TogglePlacementHints.ToggleGameObjects”定义为要触发的操作：    </span><span class="sxs-lookup"><span data-stu-id="36508-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="36508-215">如果现在进入“游戏”模式，将会看到，默认已禁用半透明的位置提示，但可以通过按“提示”按钮来打开和关闭提示：</span><span class="sxs-lookup"><span data-stu-id="36508-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="36508-217">祝贺</span><span class="sxs-lookup"><span data-stu-id="36508-217">Congratulations</span></span>

<span data-ttu-id="36508-218">现已完全配置了此应用程序。</span><span class="sxs-lookup"><span data-stu-id="36508-218">You have fully configured this application.</span></span> <span data-ttu-id="36508-219">该应用程序将允许用户全面装配登月舱，发射登月舱，打开/关闭提示，以及重置应用程序以重新开始设置。</span><span class="sxs-lookup"><span data-stu-id="36508-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
