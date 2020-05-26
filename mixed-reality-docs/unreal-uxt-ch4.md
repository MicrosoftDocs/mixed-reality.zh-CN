---
title: 4. 使场景具有交互性
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 4 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 2e4d26ed4e0b8199bfc629016aea688bd1c41ef8
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/18/2020
ms.locfileid: "83520022"
---
# <a name="4-making-your-scene-interactive"></a><span data-ttu-id="46e5e-104">4.使场景具有交互性</span><span class="sxs-lookup"><span data-stu-id="46e5e-104">4. Making your scene interactive</span></span>

<span data-ttu-id="46e5e-105">本部分介绍开放源代码的混合现实工具包 UX Tools 插件，它提供了一组工具来轻松地使场景具有交互性。</span><span class="sxs-lookup"><span data-stu-id="46e5e-105">This section introduces you to the open source Mixed Reality Toolkit UX Tools plugin, which provides a set of tools to easily make your scene interactive.</span></span> <span data-ttu-id="46e5e-106">本部分结束时，棋子将能响应用户输入。</span><span class="sxs-lookup"><span data-stu-id="46e5e-106">By the end of this section, your chess pieces will respond to user input.</span></span> 

## <a name="objectives"></a><span data-ttu-id="46e5e-107">目标</span><span class="sxs-lookup"><span data-stu-id="46e5e-107">Objectives</span></span>

* <span data-ttu-id="46e5e-108">在项目中纳入混合现实工具包 UX Tools 插件</span><span class="sxs-lookup"><span data-stu-id="46e5e-108">Include the Mixed Reality Toolkit UX Tools plugin in your project</span></span>
* <span data-ttu-id="46e5e-109">将手势交互 Actor 添加到指尖</span><span class="sxs-lookup"><span data-stu-id="46e5e-109">Add Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="46e5e-110">创建操控器并将其附加到棋盘和棋子</span><span class="sxs-lookup"><span data-stu-id="46e5e-110">Create and attach Manipulators to your chess board and pieces</span></span> 
* <span data-ttu-id="46e5e-111">使用输入模拟来验证项目</span><span class="sxs-lookup"><span data-stu-id="46e5e-111">Use input simulation to validate your project</span></span>

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a><span data-ttu-id="46e5e-112">下载混合现实工具包 UX Tools 插件</span><span class="sxs-lookup"><span data-stu-id="46e5e-112">Download the Mixed Reality Toolkit UX Tools plugin</span></span>

1.  <span data-ttu-id="46e5e-113">从 [UX Tools GitHub 存储库](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)克隆或下载最新版本的 MRTK UX Tools 插件并将其解压缩</span><span class="sxs-lookup"><span data-stu-id="46e5e-113">Clone or download and unzip the latest release of the MRTK UX Tools plugin from the [UX Tools GitHub repository](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)</span></span>

2.  <span data-ttu-id="46e5e-114">在象棋项目根文件夹中，创建一个名为“插件”的新文件夹。</span><span class="sxs-lookup"><span data-stu-id="46e5e-114">In your chess project root folder, create a new folder called “Plugins”.</span></span> <span data-ttu-id="46e5e-115">将解压缩的 UXTools 插件复制到此文件夹。</span><span class="sxs-lookup"><span data-stu-id="46e5e-115">Copy your unzipped UXTools plugin into this folder.</span></span> <span data-ttu-id="46e5e-116">重新启动 Unreal 编辑器。</span><span class="sxs-lookup"><span data-stu-id="46e5e-116">Restart the Unreal editor.</span></span> 

![创建项目插件文件夹](images/unreal-uxt/4-plugins.PNG)

3.  <span data-ttu-id="46e5e-118">重新启动后，如果在源面板中看不到 UXTools 插件内容，则可能需要单击“查看选项”>“显示插件内容”。</span><span class="sxs-lookup"><span data-stu-id="46e5e-118">After restarting, if you don’t see UXTools plugin content in your sources panel, you may need to click on **View Options > Show Plugin Content**.</span></span> <span data-ttu-id="46e5e-119">你会看到 UXTools 插件提供了一个包含指针、输入模拟和一个简单按钮的“内容”文件夹，以及一个具有由函数分隔的子文件夹的“C++ 类”文件夹。</span><span class="sxs-lookup"><span data-stu-id="46e5e-119">You’ll see that the UXTools plugin provides a Content folder with Pointers, Input Simulation, and a Simple Button, as well as a C++ Classes folder with subfolders separated by function.</span></span>  

![显示插件内容](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a><span data-ttu-id="46e5e-121">生成手势交互 Actor</span><span class="sxs-lookup"><span data-stu-id="46e5e-121">Spawn Hand Interaction Actors</span></span>

1.  <span data-ttu-id="46e5e-122">首先从 MRPawn 中生成手势交互 Actor，这样一来：1) 我们可以将光标放在 Pawn 的食指指尖来使 MRPawn 可视化，2) 可通过 Pawn 提供可表述的手写输入事件（从而直接操纵 Actor），3) 可通过从我们的手掌延伸出的手部光线提供远交互输入事件。</span><span class="sxs-lookup"><span data-stu-id="46e5e-122">Let’s start by spawning Hand Interaction Actors from our MRPawn so that 1) we can visualize MRPawn with a cursor on the tips of the Pawn’s index fingers, 2) we can provide articulated hand input events (and thus, directly manipulate actors) through the Pawn, and 3) we can provide far interaction input events through hand rays extending from our palms.</span></span> <span data-ttu-id="46e5e-123">打开“MRPawn”蓝图，然后导航到“事件图”。</span><span class="sxs-lookup"><span data-stu-id="46e5e-123">Open the **MRPawn** Blueprint and navigate to the **Event Graph**.</span></span> 

2.  <span data-ttu-id="46e5e-124">将执行引脚从事件 BeginPlay 拖离然后释放，以放置一个新节点。</span><span class="sxs-lookup"><span data-stu-id="46e5e-124">Drag the execution pin from Event BeginPlay and release to place a new node.</span></span> <span data-ttu-id="46e5e-125">选择“从类中生成 Actor”节点。</span><span class="sxs-lookup"><span data-stu-id="46e5e-125">Select the **Spawn Actor from Class** node.</span></span> <span data-ttu-id="46e5e-126">单击“类”引脚旁边的下拉列表，并搜索“Uxt 手势交互 Actor”。</span><span class="sxs-lookup"><span data-stu-id="46e5e-126">Click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span> <span data-ttu-id="46e5e-127">从“SpawnActor Uxt 手势交互”节点中拖出执行引脚，然后释放，并搜索“Uxt Hand Interaction Actor”类中包含的“Set Hand”函数。</span><span class="sxs-lookup"><span data-stu-id="46e5e-127">Drag the execution pin from the SpawnActor Uxt Hand Interaction node, release, and search for the **Set Hand** function contained in the Uxt Hand Interaction Actor class.</span></span> <span data-ttu-id="46e5e-128">将 SpawnActor 节点的“返回值”连接到“设置手势”节点的“目标”引脚，以将“手势交互 Actor”的手势设置为“向左”。</span><span class="sxs-lookup"><span data-stu-id="46e5e-128">Connect the SpawnActor node’s Return Value to the Target pin of the Set Hand node to set the hand of the Hand Interaction Actor to **Left**.</span></span> <span data-ttu-id="46e5e-129">生成第二个“Uxt 手势交互 Actor”，这一次是将手势设置为“向右”，以便在事件开始时，将在每只手上生成一个 Uxt 手势交互 Actor。</span><span class="sxs-lookup"><span data-stu-id="46e5e-129">Spawn a second **Uxt Hand Interaction Actor**, this time setting the hand to **Right**, so that when the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span> 

![生成 UXT 手势交互 Actor](images/unreal-uxt/4-spawnactor.PNG)

3.  <span data-ttu-id="46e5e-131">接下来，我们需要为 Uxt 手势交互 Actor 提供要在其中生成的初始变形和一个所有者。</span><span class="sxs-lookup"><span data-stu-id="46e5e-131">Next, we need to provide our Uxt Hand Interaction Actors with an initial transform at which to spawn, and an owner.</span></span> <span data-ttu-id="46e5e-132">将该引脚拖离一个“生成变形”引脚，然后释放，即可放置一个新节点。</span><span class="sxs-lookup"><span data-stu-id="46e5e-132">Drag the pin off one of the **Spawn Transform** pins and release to place a new node.</span></span> <span data-ttu-id="46e5e-133">搜索“做出变形”节点。</span><span class="sxs-lookup"><span data-stu-id="46e5e-133">Search for the **Make Transform** node.</span></span> <span data-ttu-id="46e5e-134">初始变形其实并不重要，因为手势交互 Actor 会在可见（已在 UX Tools 插件中为我们编写了代码）时立即跳到我们手中，否则将会消失。</span><span class="sxs-lookup"><span data-stu-id="46e5e-134">The initial transform really doesn’t matter since the Hand Interaction Actors will jump to our hands as soon as they are visible (code that’s already written for us in the UX Tools plugin), otherwise, they’ll disappear.</span></span> <span data-ttu-id="46e5e-135">但是，SpawnActor 函数需要将 Transform 作为输入来避免编译器错误，因此，我们将按原样保留“做出变形”的默认值。</span><span class="sxs-lookup"><span data-stu-id="46e5e-135">However, the SpawnActor function requires a Transform as input to avoid a compiler error, so we’ll just leave the default values in Make Transform as is.</span></span> <span data-ttu-id="46e5e-136">将“做出变形”的“返回值”拖到另一只手的“交互 Actor 生成变形”中。</span><span class="sxs-lookup"><span data-stu-id="46e5e-136">Drag Make Transform’s **Return Value** to the other hand’s Interaction Actor Spawn Transform as well.</span></span> 

4.  <span data-ttu-id="46e5e-137">单击两个 SpawnActor 节点底部的“向下箭头”，以显示“所有者”引脚。</span><span class="sxs-lookup"><span data-stu-id="46e5e-137">Click the **down arrow** at the bottom of both SpawnActor nodes to reveal the **Owner** pin.</span></span> <span data-ttu-id="46e5e-138">将该引脚拖离一个“所有者”引脚，然后放开，即可放置一个新节点。</span><span class="sxs-lookup"><span data-stu-id="46e5e-138">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span> <span data-ttu-id="46e5e-139">搜索“self”并选择“获取一个 self 引用”变量。</span><span class="sxs-lookup"><span data-stu-id="46e5e-139">Search for “self” and select the **Get a reference to self** variable.</span></span> <span data-ttu-id="46e5e-140">在 Self 对象引用节点和另一个手势交互 Actor 的“所有者”引脚之间创建链接。</span><span class="sxs-lookup"><span data-stu-id="46e5e-140">Create a link between the Self object reference node and the other Hand Interaction Actor’s Owner pin as well.</span></span> <span data-ttu-id="46e5e-141">随意拖动节点以使蓝图更易读。</span><span class="sxs-lookup"><span data-stu-id="46e5e-141">Feel free to drag around nodes to make your Blueprint more readable.</span></span> <span data-ttu-id="46e5e-142">编译并保存后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="46e5e-142">**Compile**, **save**, and return to the Main window.</span></span> 

![完成 UXT 手势交互 Actor 设置](images/unreal-uxt/4-fingerptrs.PNG)

<span data-ttu-id="46e5e-144">有关 MRTK UX Tools 插件中提供的手势交互 Actor 的详细信息，请参阅官方[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)。</span><span class="sxs-lookup"><span data-stu-id="46e5e-144">For more information about the Hand Interaction Actor provided in the MRTK UX Tools plugin, check out the official [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html).</span></span>

## <a name="attach-manipulators"></a><span data-ttu-id="46e5e-145">附加操控器</span><span class="sxs-lookup"><span data-stu-id="46e5e-145">Attach Manipulators</span></span>

1.  <span data-ttu-id="46e5e-146">接下来，我们将操控器连接到我们的棋盘和国王 Actor。</span><span class="sxs-lookup"><span data-stu-id="46e5e-146">Next, we’ll attach Manipulators to our chess board and king Actors.</span></span> <span data-ttu-id="46e5e-147">操控器是一个组件，它响应可表述的手写输入，并可进行抓取、旋转和平移。通过将操控器变形应用到 Actor 变形，可直接操纵 Actor。</span><span class="sxs-lookup"><span data-stu-id="46e5e-147">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated; by applying the Manipulator’s transform to that of an Actor, Actors can be directly manipulated.</span></span> 

2.  <span data-ttu-id="46e5e-148">打开你的棋盘蓝图。</span><span class="sxs-lookup"><span data-stu-id="46e5e-148">Open your Board Blueprint.</span></span> <span data-ttu-id="46e5e-149">在“组件”面板中，单击“添加组件”并搜索“Uxt 通用操控器”。</span><span class="sxs-lookup"><span data-stu-id="46e5e-149">In the **Components** panel, click **Add Component** and search for **Uxt Generic Manipulator**.</span></span> <span data-ttu-id="46e5e-150">在“详细信息”面板中，你会看到一个标题为“通用操控器”的部分，可在其中设置是要启用单手操纵还是双手操纵、旋转模式以及平滑模式。</span><span class="sxs-lookup"><span data-stu-id="46e5e-150">In the Details panel, you’ll find a section titled **Generic Manipulator** where you can set whether you want to enable one-handed or two-handed manipulation, the rotation mode, and smoothing.</span></span> <span data-ttu-id="46e5e-151">可以随意选择所需的模式，然后编译和保存棋盘。</span><span class="sxs-lookup"><span data-stu-id="46e5e-151">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span> 

![添加通用操控器](images/unreal-uxt/4-addmanip.PNG)

![设置模式](images/unreal-uxt/4-setrotmode.PNG)

3.  <span data-ttu-id="46e5e-154">对 WhiteKing Actor 重复以上步骤。</span><span class="sxs-lookup"><span data-stu-id="46e5e-154">Repeat the steps above for the WhiteKing Actor.</span></span>

<span data-ttu-id="46e5e-155">有关 MRTK UX Tools 插件中提供的操控器组件的详细信息，请访问官方[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)。</span><span class="sxs-lookup"><span data-stu-id="46e5e-155">For more information about the Manipulator Components provided in the MRTK UX Tools plugin, visit the official [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html).</span></span>

## <a name="test-out-your-scene-with-simulated-hands"></a><span data-ttu-id="46e5e-156">使用模拟手测试场景</span><span class="sxs-lookup"><span data-stu-id="46e5e-156">Test out your scene with simulated hands</span></span>

1.  <span data-ttu-id="46e5e-157">在主窗口中，按“开始”。</span><span class="sxs-lookup"><span data-stu-id="46e5e-157">In the Main window, press **Play**.</span></span> <span data-ttu-id="46e5e-158">应会看到 MRTK UX Tools 插件提供的两个网格手，且从每个手掌延伸出手部光线！</span><span class="sxs-lookup"><span data-stu-id="46e5e-158">You should see two mesh hands provided by the MRTK UX Tools plugin, with hand rays extending from each hand’s palm!</span></span> 

![视口中的模拟手](images/unreal-uxt/4-handsim.PNG)

2.  <span data-ttu-id="46e5e-160">若要控制“右手”，请按住左 Alt 按钮。</span><span class="sxs-lookup"><span data-stu-id="46e5e-160">To control the **right hand**, hold down the **left Alt** button.</span></span> <span data-ttu-id="46e5e-161">移动鼠标来移动手。</span><span class="sxs-lookup"><span data-stu-id="46e5e-161">Move your mouse to move the hand.</span></span> <span data-ttu-id="46e5e-162">滚动鼠标滚轮，向前或**向后**移动手。</span><span class="sxs-lookup"><span data-stu-id="46e5e-162">Scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span> <span data-ttu-id="46e5e-163">单击鼠标左键进行拾取，单击鼠标中键执行戳操作。</span><span class="sxs-lookup"><span data-stu-id="46e5e-163">Click your left mouse to **pinch**, click the middle mouse button to **poke**.</span></span>

3.  <span data-ttu-id="46e5e-164">若要控制左手，请按住左 Shift 按钮。</span><span class="sxs-lookup"><span data-stu-id="46e5e-164">To control the **left hand**, hold down the **left Shift** button.</span></span> <span data-ttu-id="46e5e-165">移动左手的控件与移动右手的控件相同。</span><span class="sxs-lookup"><span data-stu-id="46e5e-165">The controls for moving the left hand are the same as those for the right hand.</span></span> 

4.  <span data-ttu-id="46e5e-166">现在，请尝试使用模拟手来拿起、移动和放下白棋国王。</span><span class="sxs-lookup"><span data-stu-id="46e5e-166">Now try using the simulated hands to pick up, move, and set down the white chess king.</span></span> <span data-ttu-id="46e5e-167">你还可以操纵棋盘！</span><span class="sxs-lookup"><span data-stu-id="46e5e-167">You can also manipulate the board!</span></span> <span data-ttu-id="46e5e-168">试验近交互和远交互 - 请注意，当手足够靠近可直接抓住棋盘和国王时，手部光线会消失，取而代之的是指针尖上的手指光标。</span><span class="sxs-lookup"><span data-stu-id="46e5e-168">Experiment with both near and far interaction- notice that when your hands get close enough to grab the board and king directly, the hand ray disappears and is replaced with a finger cursor on the index tip.</span></span> 

<span data-ttu-id="46e5e-169">有关 MRTK UX Tools 插件中提供的模拟手功能的详细信息，请访问官方[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)。</span><span class="sxs-lookup"><span data-stu-id="46e5e-169">For more information about the simulated hands feature provided by the MRTK UX Tools plugin, visit the official [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html).</span></span>

[<span data-ttu-id="46e5e-170">下一节：5.添加按钮并重置棋子位置</span><span class="sxs-lookup"><span data-stu-id="46e5e-170">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)
