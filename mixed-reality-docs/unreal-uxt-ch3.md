---
title: 3. 设置混合现实项目
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 3 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840616"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="724ac-104">3.设置混合现实项目</span><span class="sxs-lookup"><span data-stu-id="724ac-104">3. Setting up your project for mixed reality</span></span>

<span data-ttu-id="724ac-105">本部分将指导你完成为混合现实开发配置应用的过程。</span><span class="sxs-lookup"><span data-stu-id="724ac-105">This section walks you through the process of configuring your app for mixed reality development.</span></span> 

## <a name="objectives"></a><span data-ttu-id="724ac-106">目标</span><span class="sxs-lookup"><span data-stu-id="724ac-106">Objectives</span></span>

* <span data-ttu-id="724ac-107">了解如何使用 ARSessionConfig、Pawn 和 GameMode 设置混合现实项目</span><span class="sxs-lookup"><span data-stu-id="724ac-107">Understand how to set up a mixed reality project with ARSessionConfig, Pawn, and GameMode</span></span>

## <a name="configure-the-session"></a><span data-ttu-id="724ac-108">配置会话</span><span class="sxs-lookup"><span data-stu-id="724ac-108">Configure the Session</span></span>

1. <span data-ttu-id="724ac-109">在“内容浏览器”中，导航回“内容”  文件夹。</span><span class="sxs-lookup"><span data-stu-id="724ac-109">In the Content Browser, navigate back to the **Content** folder.</span></span> <span data-ttu-id="724ac-110">单击“新增”>“杂项”>“数据资产”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-110">Click **Add New > Miscellaneous > Data Asset**.</span></span> 

2. <span data-ttu-id="724ac-111">选择“ARSessionConfig”  作为类，然后单击“选择”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-111">Pick **ARSessionConfig** as the class and click **Select**.</span></span> <span data-ttu-id="724ac-112">将资产命名为“ARSessionConfig”。</span><span class="sxs-lookup"><span data-stu-id="724ac-112">Name the asset “ARSessionConfig”.</span></span>

![创建数据资产](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="724ac-114">双击“ARSessionConfig”将其打开。</span><span class="sxs-lookup"><span data-stu-id="724ac-114">Double click ARSessionConfig to open it.</span></span> <span data-ttu-id="724ac-115">ARSessionConfig 数据资产包含许多有用的 AR 设置，包括空间映射和封闭。</span><span class="sxs-lookup"><span data-stu-id="724ac-115">An ARSessionConfig data asset contains a number of useful AR settings including spatial mapping and occlusion.</span></span> <span data-ttu-id="724ac-116">有关 ARSessionConfig 的更多详细信息，请查看有关 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html)的 Unreal Engine 文档。</span><span class="sxs-lookup"><span data-stu-id="724ac-116">For more details on ARSessionConfig, take a look at Unreal Engine’s documentation on [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span></span> <span data-ttu-id="724ac-117">对于象棋应用，不需要修改任何设置，只需点击“保存”  并返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="724ac-117">For our chess app, we won’t need to modify any settings, so just hit **Save** and return to the Main window.</span></span> 

![AR 会话配置](images/unreal-uxt/3-arsessionconfig.PNG)

4. <span data-ttu-id="724ac-119">在视区上方的工具栏上，单击“蓝图”>“打开关卡蓝图”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-119">On the toolbar above the viewport, click **Blueprints > Open Level Blueprint**.</span></span> <span data-ttu-id="724ac-120">关卡蓝图是一种特殊蓝图，用作关卡范围的全局事件图。</span><span class="sxs-lookup"><span data-stu-id="724ac-120">The Level Blueprint is a special Blueprint that acts as a level-wide global event graph.</span></span> <span data-ttu-id="724ac-121">我们将在此处启动 AR 会话，以便在关卡开头应用 AR 会话配置。</span><span class="sxs-lookup"><span data-stu-id="724ac-121">We’re going to start an AR session here, so that our AR session configuration is applied at the start of the level.</span></span>  

5. <span data-ttu-id="724ac-122">将执行节点拖离 Event BeginPlay  并释放。</span><span class="sxs-lookup"><span data-stu-id="724ac-122">Drag the execution node off **Event BeginPlay** and release.</span></span> <span data-ttu-id="724ac-123">搜索“启动 AR 会话”  节点。</span><span class="sxs-lookup"><span data-stu-id="724ac-123">Search for the **Start AR Session** node.</span></span> <span data-ttu-id="724ac-124">单击“会话配置”  ，然后选择新创建的“ARSessionConfig”  资产。</span><span class="sxs-lookup"><span data-stu-id="724ac-124">Click on **Session Config** and select your newly created **ARSessionConfig** asset.</span></span> <span data-ttu-id="724ac-125">点击“编译”  ，然后“保存”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-125">Hit **Compile**, then **Save**.</span></span> <span data-ttu-id="724ac-126">返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="724ac-126">Return to the Main window.</span></span>

![启动 AR 会话](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="724ac-128">创建 Pawn</span><span class="sxs-lookup"><span data-stu-id="724ac-128">Create a Pawn</span></span>

1.  <span data-ttu-id="724ac-129">在“内容”文件夹中，创建一个继承自 DefaultPawn  的新蓝图。</span><span class="sxs-lookup"><span data-stu-id="724ac-129">In the Content folder, create a new Blueprint that inherits from **DefaultPawn**.</span></span> <span data-ttu-id="724ac-130">在 Unreal 中，Pawn 表示游戏中的用户，在本例中为 HoloLens 2 体验。</span><span class="sxs-lookup"><span data-stu-id="724ac-130">In Unreal, a Pawn represents the user in the game, or in this case, the HoloLens 2 experience.</span></span> <span data-ttu-id="724ac-131">将新 Pawn 重命名为“MRPawn”，并双击“MRPawn”将其打开。</span><span class="sxs-lookup"><span data-stu-id="724ac-131">Rename your new Pawn “MRPawn” and double click on MRPawn to open it.</span></span> 

![创建从 DefaultPawn 继承的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

2.  <span data-ttu-id="724ac-133">默认情况下，Pawn 包含网格组件和碰撞组件，因为在大多数 Unreal 项目中，用户控制的 Pawn 是与其他组件碰撞的实体对象。</span><span class="sxs-lookup"><span data-stu-id="724ac-133">By default, the Pawn has a mesh component and a collision component, since in most Unreal projects, Pawns controlled by the user are solid objects that collides with other components.</span></span> <span data-ttu-id="724ac-134">在这种情况下，由于用户是 Pawn，我们希望能够穿过全息影像，而不会产生碰撞。</span><span class="sxs-lookup"><span data-stu-id="724ac-134">In this situation, since the user is the Pawn, we want to be able to pass through holograms without generating collisions.</span></span> <span data-ttu-id="724ac-135">在“组件”面板中，选择“CollisionComponent”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-135">In the Components panel, select the **CollisionComponent**.</span></span> <span data-ttu-id="724ac-136">在“详细信息”面板中，向下滚动到“碰撞”部分，并单击“碰撞预设”旁的下拉菜单。</span><span class="sxs-lookup"><span data-stu-id="724ac-136">In the Details panel, scroll down to the Collision section and click the dropdown next to Collision Presets.</span></span> <span data-ttu-id="724ac-137">将此值从“Pawn”更改为“NoCollision”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-137">Change this from Pawn to **NoCollision**.</span></span> <span data-ttu-id="724ac-138">对“MeshComponent”  执行相同操作。</span><span class="sxs-lookup"><span data-stu-id="724ac-138">Do the same for the **MeshComponent**.</span></span> <span data-ttu-id="724ac-139">编译  ，然后保存  蓝图。</span><span class="sxs-lookup"><span data-stu-id="724ac-139">**Compile**, then **Save** the Blueprint.</span></span> <span data-ttu-id="724ac-140">返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="724ac-140">Return to the Main window.</span></span> 

![调整 Pawn 的碰撞预设](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a><span data-ttu-id="724ac-142">创建游戏模式</span><span class="sxs-lookup"><span data-stu-id="724ac-142">Create a Game Mode</span></span>

1.  <span data-ttu-id="724ac-143">在内容浏览器的“内容”文件夹中，创建一个新的蓝图，其中包含父“游戏模式库”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-143">In the Content folder in the Content Browser, create a new Blueprint with the parent **Game Mode Base**.</span></span> <span data-ttu-id="724ac-144">将其命名为“MRGameMode”并双击以打开。</span><span class="sxs-lookup"><span data-stu-id="724ac-144">Name it MRGameMode and double click to open.</span></span> <span data-ttu-id="724ac-145">在 Unreal 中，游戏模式决定着游戏或体验的诸多设置，其中包括要使用的默认 Pawn。</span><span class="sxs-lookup"><span data-stu-id="724ac-145">In Unreal, the Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span> 

![内容浏览器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="724ac-147">在“详细信息”窗格中，查找“类”部分。</span><span class="sxs-lookup"><span data-stu-id="724ac-147">In the Details panel, locate the Classes section.</span></span> <span data-ttu-id="724ac-148">将默认 Pawn 类从“DefaultPawn”更改为刚创建的“MRPawn”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-148">Change the Default Pawn Class from DefaultPawn to the **MRPawn** you just created.</span></span> <span data-ttu-id="724ac-149">点击“编译”  ，然后“保存”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-149">Hit **Compile**, then **Save**.</span></span> <span data-ttu-id="724ac-150">返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="724ac-150">Return to the Main window.</span></span> 

![设置默认 Pawn 类](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="724ac-152">设置项目的最后一步是告诉 Unreal 默认为“MRGameMode”。</span><span class="sxs-lookup"><span data-stu-id="724ac-152">The last step in setting up your project is to tell Unreal to default to MRGameMode.</span></span> <span data-ttu-id="724ac-153">转到“编辑”>“项目设置”>“映射和模式”  （在“项目”中）部分。</span><span class="sxs-lookup"><span data-stu-id="724ac-153">Go to **Edit > Projects Settings > Maps & Modes** (in the Projects) section.</span></span> <span data-ttu-id="724ac-154">在“默认模式”部分，单击下拉列表，然后选择“MRGameMode”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-154">In the Default Modes section, click the dropdown and choose **MRGameMode**.</span></span> <span data-ttu-id="724ac-155">在下面的“默认映射”部分，将“EditorStartupMap”  和“GameDefaultMap”  都更改为“Main”  。</span><span class="sxs-lookup"><span data-stu-id="724ac-155">In the Default Maps section right below, change both the **EditorStartupMap** and the **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="724ac-156">这样，当你关闭并重新打开编辑器时，将默认选择主地图。</span><span class="sxs-lookup"><span data-stu-id="724ac-156">This way when you close the editor and reopen it, the Main map will be selected by default.</span></span> <span data-ttu-id="724ac-157">同样，当你玩游戏时，主地图为开始关卡。</span><span class="sxs-lookup"><span data-stu-id="724ac-157">Similarly, when you play the game, the Main map will be the level that is started.</span></span> 

![项目设置 - 映射和模式](images/unreal-uxt/3-mapsandmodes.PNG)

[<span data-ttu-id="724ac-159">下一节：4.使场景具有交互性</span><span class="sxs-lookup"><span data-stu-id="724ac-159">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)