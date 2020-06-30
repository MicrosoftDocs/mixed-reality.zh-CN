---
title: 4. 使场景具有交互性
description: 教程系列第 4 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 62c0ff839718f7fda34bdc7560eae634fa37d44f
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720333"
---
# <a name="4-making-your-scene-interactive"></a><span data-ttu-id="6795a-104">4.使场景具有交互性</span><span class="sxs-lookup"><span data-stu-id="6795a-104">4. Making your scene interactive</span></span>

## <a name="overview"></a><span data-ttu-id="6795a-105">概述</span><span class="sxs-lookup"><span data-stu-id="6795a-105">Overview</span></span>

<span data-ttu-id="6795a-106">在上一个教程中，你添加了 ARSession、Pawn 和游戏模式，以完成针对象棋应用的混合现实设置。</span><span class="sxs-lookup"><span data-stu-id="6795a-106">In the previous tutorial you added an ARSession, Pawn, and Game Mode to complete the mixed reality setup for the chess app.</span></span> <span data-ttu-id="6795a-107">本部分重点介绍如何使用开放源代码的[混合现实工具包 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) 插件，它提供了使场景具有交互性的工具。</span><span class="sxs-lookup"><span data-stu-id="6795a-107">This section focuses on using the open source [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) plugin, which provides tools to make the scene interactive.</span></span> <span data-ttu-id="6795a-108">本部分结束时，你将能够使用用户输入来移动棋子。</span><span class="sxs-lookup"><span data-stu-id="6795a-108">By the end of this section you'll be able to move the chess pieces with user input.</span></span> 

## <a name="objectives"></a><span data-ttu-id="6795a-109">目标</span><span class="sxs-lookup"><span data-stu-id="6795a-109">Objectives</span></span>

* <span data-ttu-id="6795a-110">下载混合现实工具包 UX Tools 插件</span><span class="sxs-lookup"><span data-stu-id="6795a-110">Downloading the Mixed Reality Toolkit UX Tools plugin</span></span> 
* <span data-ttu-id="6795a-111">将手势交互 Actor 添加到指尖</span><span class="sxs-lookup"><span data-stu-id="6795a-111">Adding Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="6795a-112">创建操控器并将其添加到场景中的对象</span><span class="sxs-lookup"><span data-stu-id="6795a-112">Creating and adding Manipulators to objects in the scene</span></span>
* <span data-ttu-id="6795a-113">使用输入模拟来验证项目</span><span class="sxs-lookup"><span data-stu-id="6795a-113">Using input simulation to validate the project</span></span>

## <a name="downloading-the-mrtk-ux-tools-plugin"></a><span data-ttu-id="6795a-114">下载 MRTK UX Tools 插件</span><span class="sxs-lookup"><span data-stu-id="6795a-114">Downloading the MRTK UX Tools plugin</span></span>
<span data-ttu-id="6795a-115">在开始使用用户输入之前，需要将插件添加到项目。</span><span class="sxs-lookup"><span data-stu-id="6795a-115">Before you start working with user input, you'll need to add the plugin to the project.</span></span>

1.  <span data-ttu-id="6795a-116">从 [GitHub 存储库](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)克隆或下载最新的 MRTK UX Tools 插件并解压缩文件。</span><span class="sxs-lookup"><span data-stu-id="6795a-116">Clone or download the latest MRTK UX Tools plugin from the [GitHub repository](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) and unzip the file.</span></span>

2.  <span data-ttu-id="6795a-117">在项目的根文件夹中，创建一个名为“插件”的新文件夹。</span><span class="sxs-lookup"><span data-stu-id="6795a-117">Create a new folder called **Plugins** in the root folder of the project.</span></span> <span data-ttu-id="6795a-118">将解压缩的 UXTools 插件复制到此文件夹中，然后重新启动 Unreal 编辑器。</span><span class="sxs-lookup"><span data-stu-id="6795a-118">Copy the unzipped UXTools plugin into this folder and restart the Unreal editor.</span></span> 

![创建项目插件文件夹](images/unreal-uxt/4-plugins.PNG)

3.  <span data-ttu-id="6795a-120">UXTools 插件具有一个包含指针、输入模拟和简单按钮的“内容”文件夹，以及一个由函数分隔的“C++ 类”文件夹  。</span><span class="sxs-lookup"><span data-stu-id="6795a-120">The UXTools plugin has a Content folder with subfolders for **Pointers**, **Input Simulation**, and **Simple Button**, as well as a C++ Classes folder separated by function.</span></span>  

> [!NOTE]
> <span data-ttu-id="6795a-121">如果在“内容浏览器”中看不到“UXTools 内容”部分，请单击“视图选项”>“显示插件内容”  。</span><span class="sxs-lookup"><span data-stu-id="6795a-121">If you don’t see the **UXTools Content** section in the **Content Browser**, click **View Options > Show Plugin Content**.</span></span> 

![显示插件内容](images/unreal-uxt/4-showplugincontent.PNG)

<span data-ttu-id="6795a-123">安全安装插件后，便可以开始使用它所提供的工具，从手势交互 Actor 开始。</span><span class="sxs-lookup"><span data-stu-id="6795a-123">With the plugin safely installed, you're ready to start using the tools it has to offer, starting with hand interaction actors.</span></span>

## <a name="spawning-hand-interaction-actors"></a><span data-ttu-id="6795a-124">生成手势交互 Actor</span><span class="sxs-lookup"><span data-stu-id="6795a-124">Spawning Hand Interaction Actors</span></span>
<span data-ttu-id="6795a-125">与 UX 元素的手势交互是使用手势交互 Actor 执行的，这些手势交互 Actor 为近距和远距交互创建并驱动指针和视觉对象。</span><span class="sxs-lookup"><span data-stu-id="6795a-125">Hand interaction with UX elements is performed with Hand Interaction Actors, which create and drive the pointers and visuals for near and far interactions.</span></span>
- <span data-ttu-id="6795a-126">近距交互是通过缩放食指和拇指之间的元素或使用指尖戳元素来执行的。</span><span class="sxs-lookup"><span data-stu-id="6795a-126">*Near interactions* are performed by pinching elements between index finger and thumb or by poking them with a fingertip.</span></span> 
- <span data-ttu-id="6795a-127">远距交互是通过将虚拟手的光线指向元素并同时按住食指和拇指来执行的。</span><span class="sxs-lookup"><span data-stu-id="6795a-127">*Far interactions* are performed by pointing a ray from the virtual hand at an element and pressing index and thumb together.</span></span>

<span data-ttu-id="6795a-128">在我们的示例中，将手势交互 Actor 添加到 MRPawn 可达到以下目的：</span><span class="sxs-lookup"><span data-stu-id="6795a-128">In our case, adding a Hand Interaction Actor to **MRPawn** will:</span></span>
- <span data-ttu-id="6795a-129">将光标添加到 Pawn 的食指指尖。</span><span class="sxs-lookup"><span data-stu-id="6795a-129">Add a cursor to the tips of the Pawn’s index fingers.</span></span>
- <span data-ttu-id="6795a-130">提供可通过 Pawn 操纵的精确手势输入事件。</span><span class="sxs-lookup"><span data-stu-id="6795a-130">Provide articulated hand input events that can be manipulated through the Pawn.</span></span>
- <span data-ttu-id="6795a-131">通过从虚拟手的手掌延伸出的手部光线允许远距交互输入事件。</span><span class="sxs-lookup"><span data-stu-id="6795a-131">Allow far interaction input events through hand rays extending from the palms of the virtual hands.</span></span>

<span data-ttu-id="6795a-132">为了实现这些概念，建议先仔细阅读有关手势交互的[文档](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.8.x/Docs/HandInteraction.md)，然后再继续。</span><span class="sxs-lookup"><span data-stu-id="6795a-132">In order to drive these concepts home, you're encouraged to read through the [documentation](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.8.x/Docs/HandInteraction.md) on hand interactions before continuing.</span></span> 

<span data-ttu-id="6795a-133">准备就绪后，打开“MRPawn”蓝图，然后转到“事件图”。</span><span class="sxs-lookup"><span data-stu-id="6795a-133">Once you're ready, open the **MRPawn** Blueprint and go to the **Event Graph**.</span></span> 

1. <span data-ttu-id="6795a-134">将执行引脚从事件 BeginPlay 拖离然后释放，以放置一个新节点。</span><span class="sxs-lookup"><span data-stu-id="6795a-134">Drag and release the execution pin from **Event BeginPlay** to place a new node.</span></span> 
    * <span data-ttu-id="6795a-135">选择“从类中生成 Actor”，单击“类”引脚旁边的下拉列表，并搜索“UXT 手势交互 Actor”  。</span><span class="sxs-lookup"><span data-stu-id="6795a-135">Select **Spawn Actor from Class**, click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span> 

2. <span data-ttu-id="6795a-136">将执行引脚从“SpawnActor UXT 手势交互”节点拖离然后释放，并搜索“UXT 手势交互 Actor”类中的“设置手势”函数  。</span><span class="sxs-lookup"><span data-stu-id="6795a-136">Drag and release the execution pin from the **SpawnActor Uxt Hand Interaction** node and search for the **Set Hand** function in the **Uxt Hand Interaction Actor** class.</span></span> 
    * <span data-ttu-id="6795a-137">将 SpawnActor 节点的“返回值”连接到“设置手势”节点的“目标”引脚   。</span><span class="sxs-lookup"><span data-stu-id="6795a-137">Connect the **SpawnActor** node’s **Return Value** to the **Target** pin of the **Set Hand** node.</span></span> <span data-ttu-id="6795a-138">这会将“手势交互 Actor”的手势设置为“向左”。</span><span class="sxs-lookup"><span data-stu-id="6795a-138">This sets the hand of the Hand Interaction Actor to **Left**.</span></span> 

3. <span data-ttu-id="6795a-139">生成第二个“UXT 手势交互 Actor”，这次会将手势设置为“向右”。</span><span class="sxs-lookup"><span data-stu-id="6795a-139">Spawn a second **Uxt Hand Interaction Actor**, this time setting the hand to **Right**.</span></span> <span data-ttu-id="6795a-140">事件开始时，将会在每只手上生成 UXT 手势交互 Actor。</span><span class="sxs-lookup"><span data-stu-id="6795a-140">When the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span> 

<span data-ttu-id="6795a-141">事件图应与以下屏幕截图匹配：</span><span class="sxs-lookup"><span data-stu-id="6795a-141">Your **Event Graph** should match the following screenshot:</span></span>

![生成 UXT 手势交互 Actor](images/unreal-uxt/4-spawnactor.PNG)

<span data-ttu-id="6795a-143">两个 UXT 手势交互 Actor 均需要所有者和初始变形位置。</span><span class="sxs-lookup"><span data-stu-id="6795a-143">Both Uxt Hand Interaction Actors need owners and initial transform locations.</span></span> <span data-ttu-id="6795a-144">初始变形并不重要，因为手势交互 Actor 可见后即可跳转到虚拟手（此行为包含在 UX Tools 插件中）。</span><span class="sxs-lookup"><span data-stu-id="6795a-144">The initial transform  doesn’t matter since the Hand Interaction Actors will jump to the virtual hands as soon as they're visible (this behavior is included in the UX Tools plugin).</span></span> <span data-ttu-id="6795a-145">但是，`SpawnActor` 函数需要使用变形输入来避免编译器错误，因此你将使用默认值。</span><span class="sxs-lookup"><span data-stu-id="6795a-145">However, the `SpawnActor` function requires a Transform input to avoid a compiler error, so you'll use the default values.</span></span> 

1. <span data-ttu-id="6795a-146">将该引脚拖离一个“生成变形”引脚，然后释放，即可放置一个新节点。</span><span class="sxs-lookup"><span data-stu-id="6795a-146">Drag and release the pin off one of the **Spawn Transform** pins to place a new node.</span></span> 
    * <span data-ttu-id="6795a-147">搜索“进行变形”节点，然后将“返回值”拖到另一个手势的“生成变形”，以便连接两个 SpawnActor 节点   。</span><span class="sxs-lookup"><span data-stu-id="6795a-147">Search for the **Make Transform** node, then drag the **Return Value** to the other hand’s **Spawn Transform** so that both **SpawnActor** nodes are connected.</span></span> 

3.  <span data-ttu-id="6795a-148">单击两个 SpawnActor 节点底部的“向下箭头”，以显示“所有者”引脚  。</span><span class="sxs-lookup"><span data-stu-id="6795a-148">Click the **down arrow** at the bottom of both **SpawnActor** nodes to reveal the **Owner** pin.</span></span>    
    * <span data-ttu-id="6795a-149">将该引脚拖离一个“所有者”引脚，然后放开，即可放置一个新节点。</span><span class="sxs-lookup"><span data-stu-id="6795a-149">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span> 
    * <span data-ttu-id="6795a-150">搜索“自身”并选择“获取对自身的引用”变量，然后在“自身”对象引用节点和另一个手势交互 Actor 的“所有者”引脚之间创建链接   。</span><span class="sxs-lookup"><span data-stu-id="6795a-150">Search for **self** and select the **Get a reference to self** variable, then create a link between the **Self** object reference node and the other Hand Interaction Actor’s **Owner** pin.</span></span> 
    * <span data-ttu-id="6795a-151">编译并保存后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="6795a-151">**Compile**, **save**, and return to the Main window.</span></span> 

<span data-ttu-id="6795a-152">确保连接与以下屏幕截图匹配，但可随意拖动节点以使蓝图更具可读性</span><span class="sxs-lookup"><span data-stu-id="6795a-152">Make sure the connections match the following screenshot, but feel free to drag around nodes to make your Blueprint more readable</span></span>

![完成 UXT 手势交互 Actor 设置](images/unreal-uxt/4-fingerptrs.PNG) 

<span data-ttu-id="6795a-154">可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)中找到有关 MRTK UX Tools 插件中提供的手势交互 Actor 的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6795a-154">You can find more information about the Hand Interaction Actor provided in the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html).</span></span>

<span data-ttu-id="6795a-155">现在，项目中的虚拟手可以选择对象，但仍无法对其进行操纵。</span><span class="sxs-lookup"><span data-stu-id="6795a-155">Now the virtual hands in the project have a way of selecting objects, but they still can't manipulate them.</span></span> <span data-ttu-id="6795a-156">测试应用之前的最后一个任务是将操控器组件添加到场景中的 Actor。</span><span class="sxs-lookup"><span data-stu-id="6795a-156">Your last task before testing the app is to add Manipulator components to the actors in the scene.</span></span>

## <a name="attaching-manipulators"></a><span data-ttu-id="6795a-157">附加操控器</span><span class="sxs-lookup"><span data-stu-id="6795a-157">Attaching Manipulators</span></span>

<span data-ttu-id="6795a-158">操控器是一个响应精确手动输入的组件，可进行抓取、旋转和平移。</span><span class="sxs-lookup"><span data-stu-id="6795a-158">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated.</span></span> <span data-ttu-id="6795a-159">将操控器的变形应用到 Actor 变形可允许进行直接 Actor 操纵。</span><span class="sxs-lookup"><span data-stu-id="6795a-159">Applying the Manipulator’s transform to an Actors transform allows direct Actor manipulation.</span></span> 

1. <span data-ttu-id="6795a-160">在“组件”面板中，打开“棋盘”蓝图，单击“添加组件”并搜索“UXT 通用操控器”   。</span><span class="sxs-lookup"><span data-stu-id="6795a-160">Open the **Board** blueprint, click **Add Component** and search for **Uxt Generic Manipulator** in the **Components** panel.</span></span>

![添加通用操控器](images/unreal-uxt/4-addmanip.PNG)

2. <span data-ttu-id="6795a-162">展开“详细信息”面板中的“通用操控器”部分 。</span><span class="sxs-lookup"><span data-stu-id="6795a-162">Expand the **Generic Manipulator** section in the **Details** panel.</span></span> <span data-ttu-id="6795a-163">可以在其中设置单手操纵或双手操纵、旋转模式和平滑模式。</span><span class="sxs-lookup"><span data-stu-id="6795a-163">You can set one-handed or two-handed manipulation, rotation mode, and smoothing from here.</span></span> <span data-ttu-id="6795a-164">可以随意选择所需的模式，然后编译和保存棋盘。</span><span class="sxs-lookup"><span data-stu-id="6795a-164">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span> 

![设置模式](images/unreal-uxt/4-setrotmode.PNG)

3. <span data-ttu-id="6795a-166">对 WhiteKing Actor 重复以上步骤。</span><span class="sxs-lookup"><span data-stu-id="6795a-166">Repeat the steps above for the **WhiteKing** Actor.</span></span>

<span data-ttu-id="6795a-167">可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)中找到有关 MRTK UX Tools 插件中提供的操控器组件的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6795a-167">You can find more information about the Manipulator Components provided in the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html).</span></span>

## <a name="testing-the-scene"></a><span data-ttu-id="6795a-168">测试场景</span><span class="sxs-lookup"><span data-stu-id="6795a-168">Testing the scene</span></span>
<span data-ttu-id="6795a-169">好消息！</span><span class="sxs-lookup"><span data-stu-id="6795a-169">Good news everyone!</span></span> <span data-ttu-id="6795a-170">你已准备好使用其新的虚拟手和用户输入来测试应用。</span><span class="sxs-lookup"><span data-stu-id="6795a-170">You're ready to test out the app with its new virtual hands and user input.</span></span> <span data-ttu-id="6795a-171">在主窗口中按“开始”，应该会看到 MRTK UX Tools 插件提供的两个网格手，且从每个手掌延伸出手部光线。</span><span class="sxs-lookup"><span data-stu-id="6795a-171">Press **Play** in the Main Window and you'll see two mesh hands provided by the MRTK UX Tools plugin with hand rays extending from each hand’s palm.</span></span> <span data-ttu-id="6795a-172">可以按如下所示控制手势及其交互：</span><span class="sxs-lookup"><span data-stu-id="6795a-172">You can control the hands and their interactions as follows:</span></span>
- <span data-ttu-id="6795a-173">按住“左 Alt”键以控制左手，按住“左 Shift”键以控制右手   。</span><span class="sxs-lookup"><span data-stu-id="6795a-173">Hold down the **left Alt** key to control the **left hand** and the **left Shift** key to control the **right hand**.</span></span> 
- <span data-ttu-id="6795a-174">移动鼠标来移动手，并滚动鼠标滚轮，向前或向后移动手  。</span><span class="sxs-lookup"><span data-stu-id="6795a-174">Move your mouse to move the hand and scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span> 
- <span data-ttu-id="6795a-175">单击鼠标左键进行缩放，单击鼠标中键执行戳操作。</span><span class="sxs-lookup"><span data-stu-id="6795a-175">Click the left mouse button to **pinch**, click the middle mouse button to **poke**.</span></span> 

![视口中的模拟手](images/unreal-uxt/4-handsim.PNG)

<span data-ttu-id="6795a-177">请尝试使用模拟手来拿起、移动和放下白棋国王并操纵棋盘！</span><span class="sxs-lookup"><span data-stu-id="6795a-177">Try using the simulated hands to pick up, move, and set down the white chess king and manipulate the board!</span></span> <span data-ttu-id="6795a-178">试验近距交互和远距交互 - 请注意，当手足够靠近可直接抓住棋盘和国王时，手部光线会消失，取而代之的是食指指尖上的手指光标。</span><span class="sxs-lookup"><span data-stu-id="6795a-178">Experiment with both near and far interaction - notice that when your hands get close enough to grab the board and king directly, the hand ray disappears and is replaced with a finger cursor at the tip of the index finger.</span></span> 

<span data-ttu-id="6795a-179">可以在[文档](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)中找到有关 MRTK UX Tools 插件中提供的模拟手功能的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6795a-179">You can find more information about the simulated hands feature provided by the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html).</span></span>

<span data-ttu-id="6795a-180">现在，你的虚拟手可以与对象交互，接下来可以继续学习下一个教程，并添加用户界面和事件。</span><span class="sxs-lookup"><span data-stu-id="6795a-180">Now that your virtual hands can interact with objects, you're ready to move on to the next tutorial and add user interfaces and events.</span></span>

[<span data-ttu-id="6795a-181">下一节：5.添加按钮并重置棋子位置</span><span class="sxs-lookup"><span data-stu-id="6795a-181">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)
