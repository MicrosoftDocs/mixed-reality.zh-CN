---
title: 入门教程-7。 创建农历模块示例应用程序
description: 在本课中，您将组合从前面的课程中学到的多个概念，以创建独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 3a557be91bee9b98e750ae1546ea1c4b3103298e
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555215"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="fc05d-105">7. 创建农历模块示例应用程序</span><span class="sxs-lookup"><span data-stu-id="fc05d-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="fc05d-106">在本教程中，将多个概念与前面的课程结合起来，以创建独特的示例体验。</span><span class="sxs-lookup"><span data-stu-id="fc05d-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="fc05d-107">你将了解如何创建部件程序集应用程序，用户需要使用跟踪的手选取部件并尝试组装农历模块。</span><span class="sxs-lookup"><span data-stu-id="fc05d-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="fc05d-108">你将使用 pressable 按钮来打开和关闭放置提示、重置体验并将阴历模块启动到空间中！</span><span class="sxs-lookup"><span data-stu-id="fc05d-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="fc05d-109">在将来的教程中，你将继续根据此体验来构建，其中包括使用 Azure 空间锚点实现空间对齐的强大多用户用例。</span><span class="sxs-lookup"><span data-stu-id="fc05d-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="fc05d-110">目标</span><span class="sxs-lookup"><span data-stu-id="fc05d-110">Objectives</span></span>

* <span data-ttu-id="fc05d-111">结合以前课程中的多个概念来创建一个独特的体验</span><span class="sxs-lookup"><span data-stu-id="fc05d-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="fc05d-112">了解如何切换对象</span><span class="sxs-lookup"><span data-stu-id="fc05d-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="fc05d-113">使用可按按钮触发复杂事件</span><span class="sxs-lookup"><span data-stu-id="fc05d-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="fc05d-114">使用刚体的物理特性和力量</span><span class="sxs-lookup"><span data-stu-id="fc05d-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="fc05d-115">探索如何使用工具提示</span><span class="sxs-lookup"><span data-stu-id="fc05d-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="fc05d-116">农历模块部件概述</span><span class="sxs-lookup"><span data-stu-id="fc05d-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="fc05d-117">在本部分中，你将创建一个简单的部件程序集质询，其中用户的目标是将位于表格上的五个部件分散到农历模块上的正确位置。</span><span class="sxs-lookup"><span data-stu-id="fc05d-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="fc05d-118">为实现此目的需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="fc05d-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="fc05d-119">将火箭启动器 prefab 添加到场景</span><span class="sxs-lookup"><span data-stu-id="fc05d-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="fc05d-120">为所有部件启用对象操作</span><span class="sxs-lookup"><span data-stu-id="fc05d-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="fc05d-121">添加和配置部件程序集演示（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="fc05d-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="fc05d-122">部分程序集演示（脚本）组件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="fc05d-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="fc05d-123">本教程提供了本教程的资产。</span><span class="sxs-lookup"><span data-stu-id="fc05d-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="fc05d-124">1. 将火箭启动器 prefab 添加到场景</span><span class="sxs-lookup"><span data-stu-id="fc05d-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="fc05d-125">在项目窗口中，导航到 "**资产**" > " **MRTK"。GettingStarted** > **Prototyping** > **RocketLauncher**文件夹中，将**RocketLauncher** prefab 拖到 "层次结构" 窗口中，将其添加到场景中，然后将其放置在合适的位置，例如：</span><span class="sxs-lookup"><span data-stu-id="fc05d-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="fc05d-126">转换位置 X = 1.5，Y =-0.4，Z = 0，因此它位于用户右侧 waist 高度</span><span class="sxs-lookup"><span data-stu-id="fc05d-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="fc05d-127">转换 X = 0，Y = 180，Z = 0，使用户体验的主要功能</span><span class="sxs-lookup"><span data-stu-id="fc05d-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="fc05d-129">2. 为所有部件启用对象操作</span><span class="sxs-lookup"><span data-stu-id="fc05d-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="fc05d-130">在 "层次结构" 窗口中，找到 RocketLauncher > **LunarModuleParts**对象，然后选择所有**子对象**，添加**操作处理程序（脚本）** 组件和**近交互 Grabbable （脚本）** 组件，然后按如下所示配置操作处理程序（脚本）：</span><span class="sxs-lookup"><span data-stu-id="fc05d-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="fc05d-131">取消选中 "**允许远端操作**" 复选框以仅允许近交互</span><span class="sxs-lookup"><span data-stu-id="fc05d-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="fc05d-132">更改**两个**正在进行的操作类型以**移动旋转**，因而禁用缩放</span><span class="sxs-lookup"><span data-stu-id="fc05d-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="fc05d-134">若要获得有关如何实现对象操作的分步说明，请参阅[操作三维对象](mrlearning-base-ch4.md#manipulating-3d-objects)说明。</span><span class="sxs-lookup"><span data-stu-id="fc05d-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="fc05d-135">3. 添加和配置部件程序集演示（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="fc05d-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="fc05d-136">在仍选择所有 LunarModuleParts 子对象的情况下，添加**音频源**组件，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="fc05d-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="fc05d-137">将合适的音频剪辑分配到**AudioClip**字段，例如 MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="fc05d-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="fc05d-138">取消选中 "**在唤醒**状态下播放" 复选框，以便在加载场景时不会自动播放音频剪辑</span><span class="sxs-lookup"><span data-stu-id="fc05d-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="fc05d-139">更改**空间混合**为1以启用空间音频</span><span class="sxs-lookup"><span data-stu-id="fc05d-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="fc05d-141">所有 LunarModuleParts 子对象仍处于选中状态时，添加**部分程序集演示（脚本）** 组件：</span><span class="sxs-lookup"><span data-stu-id="fc05d-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="fc05d-143">在 "层次结构" 窗口中，选择 " **RoverEnclosure** " 对象，并按如下所示配置其**部件程序集演示（脚本）** 组件：</span><span class="sxs-lookup"><span data-stu-id="fc05d-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="fc05d-144">对于 "要**放置的对象**" 字段，分配对象**本身**，在本例中为 RoverEnclosure 对象</span><span class="sxs-lookup"><span data-stu-id="fc05d-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="fc05d-145">对于 "要**放置的位置**" 字段，分配相应的**PlacementHints**对象，在本例中为 RoverEnclosure_PlacementHint 对象</span><span class="sxs-lookup"><span data-stu-id="fc05d-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="fc05d-146">在 "**工具提示对象**" 字段中，指定相应的**工具提示**，在本例中为 RoverEnclosure_ToolTip 对象</span><span class="sxs-lookup"><span data-stu-id="fc05d-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="fc05d-147">在 "**音频源**" 字段中，分配对象**本身**，在本例中为 RoverEnclosure 对象</span><span class="sxs-lookup"><span data-stu-id="fc05d-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="fc05d-149">对每个其他 LunarModuleParts 子对象（例如 FuelTank、EnergyCell、DockingPortal 和 ExternalSensor）**重复**此操作。</span><span class="sxs-lookup"><span data-stu-id="fc05d-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="fc05d-150">如果你现在进入游戏模式并移动 "对象，使其靠近其位置"，你会注意到：</span><span class="sxs-lookup"><span data-stu-id="fc05d-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="fc05d-151">对象将会靠下并置于 LunarModule 对象下，使其成为农历模块的一部分</span><span class="sxs-lookup"><span data-stu-id="fc05d-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="fc05d-152">对象上的音频源将在对象的位置播放指定的音频剪辑</span><span class="sxs-lookup"><span data-stu-id="fc05d-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="fc05d-153">将隐藏相应的工具提示对象</span><span class="sxs-lookup"><span data-stu-id="fc05d-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="fc05d-155">有关如何使用编辑器内输入模拟的提醒，可参阅[使用编辑器内手写输入模拟](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)在[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中测试场景指南。</span><span class="sxs-lookup"><span data-stu-id="fc05d-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="fc05d-156">配置登月舱</span><span class="sxs-lookup"><span data-stu-id="fc05d-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="fc05d-157">在本部分中，你将向火箭启动器应用程序添加其他功能，以便用户能够：</span><span class="sxs-lookup"><span data-stu-id="fc05d-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="fc05d-158">与农历模块交互</span><span class="sxs-lookup"><span data-stu-id="fc05d-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="fc05d-159">启动农历模块并在其启动时播放声音</span><span class="sxs-lookup"><span data-stu-id="fc05d-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="fc05d-160">重置应用程序，使农历模块和所有部件恢复到其原始位置</span><span class="sxs-lookup"><span data-stu-id="fc05d-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="fc05d-161">隐藏放置提示，使部件程序集质询更难。</span><span class="sxs-lookup"><span data-stu-id="fc05d-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="fc05d-162">为实现此目的需要执行的主要步骤如下：</span><span class="sxs-lookup"><span data-stu-id="fc05d-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="fc05d-163">启用对象操作</span><span class="sxs-lookup"><span data-stu-id="fc05d-163">Enable object manipulation</span></span>
2. <span data-ttu-id="fc05d-164">启用物理学</span><span class="sxs-lookup"><span data-stu-id="fc05d-164">Enable physics</span></span>
3. <span data-ttu-id="fc05d-165">添加音频源组件</span><span class="sxs-lookup"><span data-stu-id="fc05d-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="fc05d-166">添加和配置 "启动农历模块（脚本）" 组件</span><span class="sxs-lookup"><span data-stu-id="fc05d-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="fc05d-167">添加和配置切换放置提示（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="fc05d-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="fc05d-168">启动农历模块（脚本）组件和切换放置提示（脚本）组件不是 MRTK 的一部分。</span><span class="sxs-lookup"><span data-stu-id="fc05d-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="fc05d-169">本教程提供了本教程的资产。</span><span class="sxs-lookup"><span data-stu-id="fc05d-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="fc05d-170">1. 启用对象操作</span><span class="sxs-lookup"><span data-stu-id="fc05d-170">1. Enable object manipulation</span></span>

<span data-ttu-id="fc05d-171">在 "层次结构" 窗口中，选择 RocketLauncher > **LunarModule**对象，添加**操作处理程序（脚本）** 组件和**近交互 Grabbable （脚本）** 组件，然后配置操作处理程序（脚本），如下所示：</span><span class="sxs-lookup"><span data-stu-id="fc05d-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="fc05d-172">取消选中 "**允许远端操作**" 复选框以仅允许近交互</span><span class="sxs-lookup"><span data-stu-id="fc05d-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="fc05d-173">更改**两个**正在进行的操作类型以移动旋转，因而禁用缩放</span><span class="sxs-lookup"><span data-stu-id="fc05d-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="fc05d-175">2. 启用物理学</span><span class="sxs-lookup"><span data-stu-id="fc05d-175">2. Enable physics</span></span>

<span data-ttu-id="fc05d-176">在仍选择 RocketLauncher > **LunarModule**对象的情况下，添加一个**刚体**组件，然后按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="fc05d-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="fc05d-177">取消选中 "**使用重力**" 复选框，使农历模块不受引力的影响</span><span class="sxs-lookup"><span data-stu-id="fc05d-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="fc05d-178">选中 "**是运动**" 复选框，这样农历模块最初不会受到 physic 强制的影响</span><span class="sxs-lookup"><span data-stu-id="fc05d-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="fc05d-180">3. 添加音频源组件</span><span class="sxs-lookup"><span data-stu-id="fc05d-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="fc05d-181">在仍选择 RocketLauncher > **LunarModule**对象的情况下，添加**音频源**组件，并按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="fc05d-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="fc05d-182">将**空间混合**更改为1以启用空间音频</span><span class="sxs-lookup"><span data-stu-id="fc05d-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="fc05d-184">4. 添加和配置 "启动农历模块（脚本）" 组件</span><span class="sxs-lookup"><span data-stu-id="fc05d-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="fc05d-185">在仍选择 RocketLauncher > **LunarModule**对象的情况下，添加 "**启动农历模块（脚本）** " 组件，并按如下所示进行配置：</span><span class="sxs-lookup"><span data-stu-id="fc05d-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="fc05d-186">更改**主旨是**值，以使农历模块在启动时正常飞入，例如，到0.01</span><span class="sxs-lookup"><span data-stu-id="fc05d-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="fc05d-188">5. 添加并配置切换放置提示（脚本）组件</span><span class="sxs-lookup"><span data-stu-id="fc05d-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="fc05d-189">在仍选择 RocketLauncher > **LunarModule**对象的情况下，添加**切换放置提示（脚本）** 组件，然后按如下所示对其进行配置：</span><span class="sxs-lookup"><span data-stu-id="fc05d-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="fc05d-190">将 "游戏对象数组**大小**" 属性设置为5</span><span class="sxs-lookup"><span data-stu-id="fc05d-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="fc05d-191">将每个 RocketLauncher > LunarModule > **PlacementHints**对象的**子对象**分配到游戏对象数组中的一个**元素**字段：</span><span class="sxs-lookup"><span data-stu-id="fc05d-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="fc05d-193">配置启动按钮</span><span class="sxs-lookup"><span data-stu-id="fc05d-193">Configuring the Launch button</span></span>

<span data-ttu-id="fc05d-194">在 "层次结构" 窗口中，选择 "RocketLauncher >" 按钮 > **LaunchButton** "对象，然后在" **Pressable "按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，配置**LunarModule**对象以接收事件，并将**LaunchLunarModule**定义为要触发的操作：</span><span class="sxs-lookup"><span data-stu-id="fc05d-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="fc05d-196">有关如何实现事件的提醒，可参阅 "[手动跟踪手势" 和 "种不可交互" 按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)说明。</span><span class="sxs-lookup"><span data-stu-id="fc05d-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="fc05d-197">使用 RocketLauncher > 按钮 > **LaunchButton**对象，在**Pressable 按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，将**LunarModule**对象配置为接收事件，将**AudioSource**定义为要触发的操作，并将适当的音频剪辑分配给**音频剪辑**字段，例如 MRTK_Gem 音频剪辑：</span><span class="sxs-lookup"><span data-stu-id="fc05d-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="fc05d-199">将 RocketLauncher > 按钮 > **LaunchButton**对象保持为选中状态，在 " **Pressable" 按钮（脚本）** 组件上，创建一个新的 " **Touch End （）** " 事件，将**LunarModule**对象配置为接收事件，并将**LaunchLunarModule**定义为要触发的操作：</span><span class="sxs-lookup"><span data-stu-id="fc05d-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="fc05d-201">如果你现在进入游戏模式并按下 "启动" 按钮，则会听到音频剪辑播放，如果你将 "启动" 按钮向下移动大约一秒钟或更长时间，你会看到农历模块启动到空间中：</span><span class="sxs-lookup"><span data-stu-id="fc05d-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="fc05d-203">配置重置按钮</span><span class="sxs-lookup"><span data-stu-id="fc05d-203">Configuring the Reset button</span></span>

<span data-ttu-id="fc05d-204">在 "层次结构" 窗口中，选择 "RocketLauncher >" 按钮 > **ResetButton** "对象，然后在" **Pressable "按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，配置**LunarModule**对象以接收事件，并将**LaunchLunarModule**定义为要触发的操作：</span><span class="sxs-lookup"><span data-stu-id="fc05d-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="fc05d-206">将 RocketLauncher > 按钮 > **ResetButton**对象保持为选中状态，在 " **Pressable" 按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，将**RocketLauncher**对象配置为接收事件，将**GameObject**定义为要触发的操作，并在 "消息" 字段中输入**BroadcastMessage** ：</span><span class="sxs-lookup"><span data-stu-id="fc05d-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="fc05d-208">GameObject. BroadcastMessage 操作将 ResetPlacement 消息从 RocketLauncher 对象发送到其所有子对象。</span><span class="sxs-lookup"><span data-stu-id="fc05d-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="fc05d-209">在添加到所有 LunarModuleParts 子对象的部件程序集演示（脚本）组件中定义的 ResetPlacement 函数的任何子对象将调用重置该子对象的位置的 ResetPlacement 函数。</span><span class="sxs-lookup"><span data-stu-id="fc05d-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="fc05d-210">如果你现在进入游戏模式，则移动部分和/或启动农历模块，然后按 "重置" 按钮，你将看到部件和/或农历模块正在重置为其原始位置：</span><span class="sxs-lookup"><span data-stu-id="fc05d-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="fc05d-212">配置放置提示按钮</span><span class="sxs-lookup"><span data-stu-id="fc05d-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="fc05d-213">在 "层次结构" 窗口中，选择 "RocketLauncher >" 按钮 > **HintsButton** "对象，然后在" **Pressable "按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，配置**LunarModule**对象以接收事件，并将**TogglePlacementHints**定义为要触发的操作：</span><span class="sxs-lookup"><span data-stu-id="fc05d-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="fc05d-215">如果你现在进入游戏模式，你会注意到，默认情况下会禁用半透明的放置提示，但你可以通过按 "提示" 按钮打开和关闭它们：</span><span class="sxs-lookup"><span data-stu-id="fc05d-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="fc05d-217">祝贺你</span><span class="sxs-lookup"><span data-stu-id="fc05d-217">Congratulations</span></span>

<span data-ttu-id="fc05d-218">已完全配置此应用程序。</span><span class="sxs-lookup"><span data-stu-id="fc05d-218">You have fully configured this application.</span></span> <span data-ttu-id="fc05d-219">现在，你的应用程序允许用户完全组装农历模块，启动农历模块，切换提示，并重置应用程序以重新启动。</span><span class="sxs-lookup"><span data-stu-id="fc05d-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
