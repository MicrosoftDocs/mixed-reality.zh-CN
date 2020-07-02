---
title: 5. 添加按钮并重置棋子位置
description: 教程系列第 5 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 473f47884bbc492451007436f80e8d9762cf1ab7
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720253"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="bf184-104">5.添加按钮并重置棋子位置</span><span class="sxs-lookup"><span data-stu-id="bf184-104">5. Adding a button & resetting piece locations</span></span>


## <a name="overview"></a><span data-ttu-id="bf184-105">概述</span><span class="sxs-lookup"><span data-stu-id="bf184-105">Overview</span></span>

<span data-ttu-id="bf184-106">在上一个教程中，向棋盘的 Pawn 和操控器组件添加了手势交互 Actor，使它们具有交互性。</span><span class="sxs-lookup"><span data-stu-id="bf184-106">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="bf184-107">本部分将继续使用混合现实工具包 UX Tools 插件来构建象棋应用的功能。</span><span class="sxs-lookup"><span data-stu-id="bf184-107">In this section, you'll continue working with the Mixed Reality Toolkit UX Tools plugin by building out the features of your chess app.</span></span> <span data-ttu-id="bf184-108">其中包括创建新函数，以及了解如何在蓝图中获取对 Actor 的引用。</span><span class="sxs-lookup"><span data-stu-id="bf184-108">This includes creating a new function and learning how to get references to Actors in a Blueprint.</span></span> <span data-ttu-id="bf184-109">本部分结束时，你就可以打包混合现实应用，并将其部署到设备或仿真器中。</span><span class="sxs-lookup"><span data-stu-id="bf184-109">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="bf184-110">目标</span><span class="sxs-lookup"><span data-stu-id="bf184-110">Objectives</span></span>

* <span data-ttu-id="bf184-111">添加交互式按钮</span><span class="sxs-lookup"><span data-stu-id="bf184-111">Adding an interactive button</span></span>
* <span data-ttu-id="bf184-112">创建用于重置棋子位置的函数</span><span class="sxs-lookup"><span data-stu-id="bf184-112">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="bf184-113">连接按钮，以在按下时触发此函数</span><span class="sxs-lookup"><span data-stu-id="bf184-113">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="bf184-114">创建重置函数</span><span class="sxs-lookup"><span data-stu-id="bf184-114">Creating a reset function</span></span>
<span data-ttu-id="bf184-115">第一个任务是创建一个函数蓝图，来将象棋棋子重置到场景中的原始位置。</span><span class="sxs-lookup"><span data-stu-id="bf184-115">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span> 

1.  <span data-ttu-id="bf184-116">打开“WhiteKing”，单击“我的蓝图”中“函数”部分旁的“+”图标，将其命名为“重置位置”。    </span><span class="sxs-lookup"><span data-stu-id="bf184-116">Open **WhiteKing**, click the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span> 

2.  <span data-ttu-id="bf184-117">从蓝图网格拖动并释放“重置位置”的执行，以创建“SetActorRelativeTransform”节点。 </span><span class="sxs-lookup"><span data-stu-id="bf184-117">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span> 
    * <span data-ttu-id="bf184-118">此函数可设置 Actor 相对于其父级的变形（位置、旋转和缩放）。</span><span class="sxs-lookup"><span data-stu-id="bf184-118">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="bf184-119">将使用此函数来重置棋盘上国王的位置，即使棋盘已从其原始位置移动也无妨。</span><span class="sxs-lookup"><span data-stu-id="bf184-119">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> 
    
3. <span data-ttu-id="bf184-120">在事件图表中右击，选择“进行变形”，然后将其“位置”更改为“X = -26”、“Y = 4”和“Z = 0”。    </span><span class="sxs-lookup"><span data-stu-id="bf184-120">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="bf184-121">将其“返回值”连接到“SetActorRelativeTransform”中的“新相对变形”引脚。  </span><span class="sxs-lookup"><span data-stu-id="bf184-121">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span> 

![Reset Location 函数](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="bf184-123">编译并保存项目，然后返回到主窗口。 </span><span class="sxs-lookup"><span data-stu-id="bf184-123">**Compile** and **Save** the project before returning to the Main window.</span></span> 


## <a name="adding-a-button"></a><span data-ttu-id="bf184-124">添加按钮</span><span class="sxs-lookup"><span data-stu-id="bf184-124">Adding a button</span></span>
<span data-ttu-id="bf184-125">正确设置此函数后，接下来的任务是创建一个按钮，以在按它时触发函数。</span><span class="sxs-lookup"><span data-stu-id="bf184-125">Now that the function is setup correctly, your next task is to create a button that fires it off when touched.</span></span> 

1.  <span data-ttu-id="bf184-126">单击“添加新项 > 蓝图类”，展开“所有类”部分，然后搜索“SimpleButton“。  </span><span class="sxs-lookup"><span data-stu-id="bf184-126">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **SimpleButton**.</span></span> 
    * <span data-ttu-id="bf184-127">将其命名为“ResetButton”，然后双击以打开蓝图</span><span class="sxs-lookup"><span data-stu-id="bf184-127">Name it **ResetButton** and double click to open the Blueprint</span></span>

> [!NOTE]
> <span data-ttu-id="bf184-128">SimpleButton 是一个 3D 按钮蓝图 Actor，它是 UX Tools 插件的一部分。</span><span class="sxs-lookup"><span data-stu-id="bf184-128">**SimpleButton** is a 3D button Blueprint Actor that's part of the UX Tools plugin.</span></span> <span data-ttu-id="bf184-129">.</span><span class="sxs-lookup"><span data-stu-id="bf184-129">.</span></span> 

![从 SimpleButton 为新蓝图建立子类](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="bf184-131">从“组件”面板单击“可按按钮(继承)”，向下滚动“详细信息”面板至“事件”部分   。</span><span class="sxs-lookup"><span data-stu-id="bf184-131">Click **Pressable Button (Inherited)** from the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span> 
    * <span data-ttu-id="bf184-132">单击“按钮按下时”旁的绿色 + 按钮，向事件图表添加事件，按下按钮时将调用该事件。</span><span class="sxs-lookup"><span data-stu-id="bf184-132">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span> 
    
<span data-ttu-id="bf184-133">此时，需要调用“WhiteKing”的“重置位置”函数，这需要在关卡中引用“WhiteKing”Actor。  </span><span class="sxs-lookup"><span data-stu-id="bf184-133">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span> 

1.  <span data-ttu-id="bf184-134">滚动到“详细信息”面板中的“变量”部分，单击 + 按钮，将变量命名为“WhiteKing”。   </span><span class="sxs-lookup"><span data-stu-id="bf184-134">Scroll to the **Variables** section in the **Details** panel, click the **+** button and name the variable **WhiteKing**.</span></span> 
    * <span data-ttu-id="bf184-135">选择“变量类型”旁的下拉列表，搜索“WhiteKing”，然后选择“对象引用”。</span><span class="sxs-lookup"><span data-stu-id="bf184-135">Select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span> 
    * <span data-ttu-id="bf184-136">选中“实例可编辑”旁的复选框。</span><span class="sxs-lookup"><span data-stu-id="bf184-136">Check the box next to **Instance Editable**.</span></span> <span data-ttu-id="bf184-137">这将允许从主关卡设置变量。</span><span class="sxs-lookup"><span data-stu-id="bf184-137">This will allow the variable to be set from the Main Level.</span></span> 

![创建变量](images/unreal-uxt/5-var.PNG)

2.  <span data-ttu-id="bf184-139">将 WhiteKing 变量从“我的蓝图 > 变量”拖放到“‘重置’按钮事件图表”中，然后选择“获取 WhiteKing”。</span><span class="sxs-lookup"><span data-stu-id="bf184-139">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span> 

## <a name="firing-the-function"></a><span data-ttu-id="bf184-140">触发函数</span><span class="sxs-lookup"><span data-stu-id="bf184-140">Firing the function</span></span>
<span data-ttu-id="bf184-141">剩下的就是，在按下按钮时，正式触发重置函数。</span><span class="sxs-lookup"><span data-stu-id="bf184-141">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="bf184-142">拖动“WhiteKing”输出引脚并释放以放置新节点。</span><span class="sxs-lookup"><span data-stu-id="bf184-142">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="bf184-143">选择“Reset Location”函数。</span><span class="sxs-lookup"><span data-stu-id="bf184-143">Select the **Reset Location** function.</span></span> <span data-ttu-id="bf184-144">最后，将传出执行引脚从“按钮按下时”拖放到“重置位置”上的传入执行引脚。</span><span class="sxs-lookup"><span data-stu-id="bf184-144">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="bf184-145">编译和保存 ResetButton 蓝图，然后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="bf184-145">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![从“按下按钮时”调用“Reset Location”函数](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="bf184-147">将“ResetButton”拖到视口中，并将其位置设置为“X = 50”、“Y = -25”和“Z = 10”。  </span><span class="sxs-lookup"><span data-stu-id="bf184-147">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="bf184-148">在“默认值”下，将 WhiteKing 变量的值设置为“WhiteKing”。  </span><span class="sxs-lookup"><span data-stu-id="bf184-148">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![设置变量](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="bf184-150">运行应用，将象棋棋子移动到新位置，然后按粉色的大按钮来查看重置逻辑正在运行！</span><span class="sxs-lookup"><span data-stu-id="bf184-150">Run the app, move the chess piece to a new location, and press the big pink button to see the reset logic in action!</span></span>

<span data-ttu-id="bf184-151">现在，你有了一个混合现实应用，其中包含可与之交互的棋子和棋盘，以及一个功能齐全的按钮，该按钮将重置棋子的位置。</span><span class="sxs-lookup"><span data-stu-id="bf184-151">You now have a mixed reality app with a chess piece and board that you can interact with, as well as a fully functioning button that will reset the piece’s location.</span></span> <span data-ttu-id="bf184-152">可以在 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 存储库中找到目前完成的该应用程序。</span><span class="sxs-lookup"><span data-stu-id="bf184-152">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="bf184-153">请随意阅读本教程以外的内容并设置其余的棋子，以便在按下按钮时重置整个棋盘。</span><span class="sxs-lookup"><span data-stu-id="bf184-153">Feel free to go beyond this tutorial and set up the remainder of the chess pieces so that the entire board is reset when the button is pressed.</span></span>

![在视口中结束场景](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="bf184-155">你可以继续学习本教程的最后一部分，你将了解如何将应用正确打包并部署到设备或仿真器。</span><span class="sxs-lookup"><span data-stu-id="bf184-155">You're ready to move on to the final section of this tutorial where you'll learn how to correctly package and deploy the app to a device or emulator.</span></span>

[<span data-ttu-id="bf184-156">下一节：6.打包并部署到设备或仿真器</span><span class="sxs-lookup"><span data-stu-id="bf184-156">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
