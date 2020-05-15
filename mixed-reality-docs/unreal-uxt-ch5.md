---
title: 5. 添加按钮并重置棋子位置
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 5 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: df5ea22e7097fdd3b788ec298bc1cd78c315b585
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840396"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="545f1-104">5.添加按钮并重置棋子位置</span><span class="sxs-lookup"><span data-stu-id="545f1-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="545f1-105">本部分将继续演示混合现实工具包 UX Tools 插件的功能，并构建象棋应用的功能。</span><span class="sxs-lookup"><span data-stu-id="545f1-105">This section continues demonstrating the capabilities of the Mixed Reality Toolkit UX Tools plugin and building out the features of your chess app.</span></span> <span data-ttu-id="545f1-106">你将创建一个新函数，并了解如何将对 Actor 的引用从关卡转换到蓝图中。</span><span class="sxs-lookup"><span data-stu-id="545f1-106">You’ll create a new function and learn how to get references to Actors from your Level into a Blueprint.</span></span>

## <a name="objectives"></a><span data-ttu-id="545f1-107">目标</span><span class="sxs-lookup"><span data-stu-id="545f1-107">Objectives</span></span>

* <span data-ttu-id="545f1-108">向你的项目添加一个按钮</span><span class="sxs-lookup"><span data-stu-id="545f1-108">Add a button to your project</span></span>
* <span data-ttu-id="545f1-109">创建一个新的“Reset Location”函数，该函数将一个棋子发送回其原始位置</span><span class="sxs-lookup"><span data-stu-id="545f1-109">Create a new “Reset Location” function that sends a piece back to its original location</span></span>
* <span data-ttu-id="545f1-110">连接按钮，以在按下时触发新创建的函数</span><span class="sxs-lookup"><span data-stu-id="545f1-110">Hook the button up to trigger the newly created function when pressed</span></span>

## <a name="create-a-function-to-reset-location"></a><span data-ttu-id="545f1-111">创建一个函数以重置位置</span><span class="sxs-lookup"><span data-stu-id="545f1-111">Create a function to reset location</span></span>

1.  <span data-ttu-id="545f1-112">打开“WhiteKing”  。</span><span class="sxs-lookup"><span data-stu-id="545f1-112">Open **WhiteKing**.</span></span> <span data-ttu-id="545f1-113">在“我的蓝图”  面板中，单击“函数”  部分旁的“+”按钮以创建新函数。</span><span class="sxs-lookup"><span data-stu-id="545f1-113">In the **My Blueprint** panel, click the “+” button next to the **Functions** section to create a new function.</span></span> <span data-ttu-id="545f1-114">将此函数命名为“Reset Location”。</span><span class="sxs-lookup"><span data-stu-id="545f1-114">Name this function “Reset Location”.</span></span> 

2.  <span data-ttu-id="545f1-115">在新创建的“Reset Location”  蓝图中，将执行引脚拖放到蓝图网格上的任意位置，以调用“SetActorRelativeTransform”  节点。</span><span class="sxs-lookup"><span data-stu-id="545f1-115">In your newly created **Reset Location** Blueprint, drag the execution pin and release anywhere on the Blueprint grid to call a **SetActorRelativeTransform** node.</span></span> <span data-ttu-id="545f1-116">此函数可设置 Actor 相对于其父级的变形（位置、旋转和缩放）。</span><span class="sxs-lookup"><span data-stu-id="545f1-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="545f1-117">我们将使用此函数来重置棋盘上国王的位置，即使棋盘已从其原始位置移动也无妨。</span><span class="sxs-lookup"><span data-stu-id="545f1-117">We’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> <span data-ttu-id="545f1-118">使用位置 X = -26，Y = 4，Z = 0 创建“做出变形”  节点，并将其连接到“新的相对变形”输入。</span><span class="sxs-lookup"><span data-stu-id="545f1-118">Create a **Make Transform** node with Location X = -26, Y = 4, Z = 0, and connect it to the New Relative Transform input.</span></span> 

![Reset Location 函数](images/unreal-uxt/5-function.PNG)

3.  <span data-ttu-id="545f1-120">编译并保存“WhiteKing”  。</span><span class="sxs-lookup"><span data-stu-id="545f1-120">Compile and Save **WhiteKing**.</span></span> <span data-ttu-id="545f1-121">返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="545f1-121">Return to the Main window.</span></span> 

## <a name="add-a-button"></a><span data-ttu-id="545f1-122">添加按钮</span><span class="sxs-lookup"><span data-stu-id="545f1-122">Add a button</span></span>

1.  <span data-ttu-id="545f1-123">在“蓝图”  文件夹中，创建使 SimpleButton 成为子类的新蓝图。</span><span class="sxs-lookup"><span data-stu-id="545f1-123">In your **Blueprints** folder, create a new Blueprint that subclasses SimpleButton.</span></span> <span data-ttu-id="545f1-124">SimpleButton 是一个 3D 按钮蓝图 Actor，作为 UX Tools 插件的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="545f1-124">SimpleButton is a 3D button Blueprint Actor that is provided as part of the UX Tools plugin.</span></span> <span data-ttu-id="545f1-125">将此按钮命名为“ResetButton”，然后双击以打开蓝图。</span><span class="sxs-lookup"><span data-stu-id="545f1-125">Name this button “ResetButton” and double click to open the Blueprint.</span></span> 

![从 SimpleButton 为新蓝图建立子类](images/unreal-uxt/5-subclass.PNG)

2.  <span data-ttu-id="545f1-127">在“组件”  面板中，单击“PressableButton(继承)”  。</span><span class="sxs-lookup"><span data-stu-id="545f1-127">In the **Components** panel, click on **PressableButton (Inherited)**.</span></span> <span data-ttu-id="545f1-128">在“详细信息”面板中滚动，直到看到“事件”  部分。</span><span class="sxs-lookup"><span data-stu-id="545f1-128">In the Details panel, scroll until you see the **Events** section.</span></span> <span data-ttu-id="545f1-129">单击“按钮按下时”  旁的绿色加号按钮 - 这将向事件图表添加“按钮按下时”  事件，按下按钮时将调用该事件。</span><span class="sxs-lookup"><span data-stu-id="545f1-129">Click the green plus button next to **On Button Pressed**- this will add an **On Button Pressed** event to the Event Graph, which will be called when the button is pressed.</span></span> <span data-ttu-id="545f1-130">在此，我们需要调用 WhiteKing 的“Reset Location”函数。</span><span class="sxs-lookup"><span data-stu-id="545f1-130">From here, we’ll want to call our WhiteKing’s Reset Location function.</span></span> <span data-ttu-id="545f1-131">为此，首先需要在我们的关卡中获取对 WhiteKing Actor 的引用。</span><span class="sxs-lookup"><span data-stu-id="545f1-131">To do this, we’ll first need to get a reference to the WhiteKing Actor in our Level.</span></span> 

3.  <span data-ttu-id="545f1-132">在“我的蓝图”  面板中，找到“变量”  部分，然后单击 +  按钮添加新变量。</span><span class="sxs-lookup"><span data-stu-id="545f1-132">In the **My Blueprint** panel, find the **Variables** section and click the **+** button to add a new variable.</span></span> <span data-ttu-id="545f1-133">将此变量命名为“WhiteKing”。</span><span class="sxs-lookup"><span data-stu-id="545f1-133">Name this variable “WhiteKing”.</span></span> <span data-ttu-id="545f1-134">在“详细信息”面板中，选择“变量类型”  旁的下拉列表，搜索“WhiteKing”，然后选择“对象引用”  。</span><span class="sxs-lookup"><span data-stu-id="545f1-134">In the Details panel, select the dropdown next to **Variable Type**, search for “WhiteKing”, and select the **Object Reference**.</span></span> <span data-ttu-id="545f1-135">最后，选中“实例可编辑”  旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="545f1-135">Finally, check the box next to **Instance Editable**.</span></span> <span data-ttu-id="545f1-136">这将允许从主关卡设置变量。</span><span class="sxs-lookup"><span data-stu-id="545f1-136">This will allow the variable to be set from the Main Level.</span></span> 

![创建变量](images/unreal-uxt/5-var.PNG)

4.  <span data-ttu-id="545f1-138">将 WhiteKing 变量从“我的蓝图”>“变量”  拖放到“简单按钮事件图表”中。</span><span class="sxs-lookup"><span data-stu-id="545f1-138">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Simple Button Event Graph.</span></span> <span data-ttu-id="545f1-139">选择“获取 WhiteKing”  。</span><span class="sxs-lookup"><span data-stu-id="545f1-139">Choose **Get WhiteKing**.</span></span> 

5.  <span data-ttu-id="545f1-140">拖动“WhiteKing”输出引脚并释放以放置新节点。</span><span class="sxs-lookup"><span data-stu-id="545f1-140">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="545f1-141">选择“Reset Location”  函数。</span><span class="sxs-lookup"><span data-stu-id="545f1-141">Select the **Reset Location** function.</span></span> <span data-ttu-id="545f1-142">最后，将传出执行引脚从“按钮按下时”  拖放到“重置位置”  上的传入执行引脚。</span><span class="sxs-lookup"><span data-stu-id="545f1-142">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="545f1-143">编译  和保存  ResetButton 蓝图，然后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="545f1-143">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![从“按下按钮时”调用“Reset Location”函数](images/unreal-uxt/5-callresetloc.PNG)

6.  <span data-ttu-id="545f1-145">将“SimpleButton”  拖到视口中，并将其位置设置为 X = 50，Y =-25，Z = 10。</span><span class="sxs-lookup"><span data-stu-id="545f1-145">Drag **SimpleButton** into the viewport and set its location to X = 50, Y = -25, Z = 10.</span></span> <span data-ttu-id="545f1-146">在“默认值”  下，将 WhiteKing 变量的值设置为“WhiteKing”  。</span><span class="sxs-lookup"><span data-stu-id="545f1-146">Under **Default**, set the value of the WhiteKing variable to **WhiteKing**.</span></span>

![设置变量](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="545f1-148">现在，你有了一个混合现实应用，其中包含可抓取的棋子和棋盘，以及一个功能齐全的按钮，该按钮将在按下时重置棋子的位置。</span><span class="sxs-lookup"><span data-stu-id="545f1-148">You now have a mixed reality app with a grabbable chess piece and board, as well as a fully functioning button that will reset the piece’s location when pressed.</span></span> <span data-ttu-id="545f1-149">可在 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 上找到到目前已完成的应用。</span><span class="sxs-lookup"><span data-stu-id="545f1-149">The completed app up to this point can be found on [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span></span> <span data-ttu-id="545f1-150">请随意阅读本教程以外的内容并设置这些棋子的其余部分，以便在用户按下按钮时重置整个棋盘。</span><span class="sxs-lookup"><span data-stu-id="545f1-150">Feel free to go beyond this tutorial and set up the remainder of the chess pieces, so that the entire board is reset when the user presses the button.</span></span>

![在视口中结束场景](images/unreal-uxt/5-endscene.PNG)

[<span data-ttu-id="545f1-152">下一节：6.打包并部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="545f1-152">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)