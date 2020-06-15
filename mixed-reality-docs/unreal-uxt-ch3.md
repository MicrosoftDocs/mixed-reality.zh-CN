---
title: 3. 设置混合现实项目
description: 教程系列第 3 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: d22c3d8c9048f53171298642768877d7bcdcb972
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330277"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="3f6e2-104">3.设置混合现实项目</span><span class="sxs-lookup"><span data-stu-id="3f6e2-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="3f6e2-105">概述</span><span class="sxs-lookup"><span data-stu-id="3f6e2-105">Overview</span></span>

<span data-ttu-id="3f6e2-106">在上一个教程中设置了象棋应用项目。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="3f6e2-107">本部分将逐步介绍如何设置此应用，来进行混合现实开发，这意味着要添加 AR 会话。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="3f6e2-108">此任务将使用 ARSessionConfig 数据资产，其中包含大量有用的 AR 设置，如空间映射和遮挡。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="3f6e2-109">若要深入了解，请参阅 Unreal 引擎文档，其中包含有关 [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 资产和 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 类的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="3f6e2-110">目标</span><span class="sxs-lookup"><span data-stu-id="3f6e2-110">Objectives</span></span>
* <span data-ttu-id="3f6e2-111">使用 Unreal Engine 的 AR 设置</span><span class="sxs-lookup"><span data-stu-id="3f6e2-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="3f6e2-112">使用 ARSessionConfig 数据资产</span><span class="sxs-lookup"><span data-stu-id="3f6e2-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="3f6e2-113">设置 Pawn 和游戏模式</span><span class="sxs-lookup"><span data-stu-id="3f6e2-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="3f6e2-114">添加会话资产</span><span class="sxs-lookup"><span data-stu-id="3f6e2-114">Adding the session asset</span></span>
<span data-ttu-id="3f6e2-115">Unreal 中的 AR 会话无法自行发生。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="3f6e2-116">要使用会话，需要借助 ARSessionConfig 数据资产，这就是接下来的任务：</span><span class="sxs-lookup"><span data-stu-id="3f6e2-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="3f6e2-117">单击“内容浏览器”中的“添加新项 > 杂项 > 数据资产”。 </span><span class="sxs-lookup"><span data-stu-id="3f6e2-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="3f6e2-118">请确保自己处于根 Content 文件夹级别。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="3f6e2-119">选择“ARSessionConfig”，单击“选择”，然后将资产命名为“ARSessionConfig”。  </span><span class="sxs-lookup"><span data-stu-id="3f6e2-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![创建数据资产](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="3f6e2-121">双击“ARSessionConfig”将其打开，保留所有默认设置，点击“保存”。 </span><span class="sxs-lookup"><span data-stu-id="3f6e2-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="3f6e2-122">返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-122">Return to the Main window.</span></span> 

![AR 会话配置](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="3f6e2-124">完成此操作后，下一步是确保在关卡加载时 AR 会话会启动。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-124">With that done, your next step is to make sure that the AR session starts when the level loads.</span></span> <span data-ttu-id="3f6e2-125">幸运的是，Unreal 具有一种叫做“关卡蓝图”的特殊蓝图，它用作关卡范围的全局事件图。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="3f6e2-126">在关卡蓝图中连接 ARSessionConfig 资产，可确保游戏开始时 AR 会话将立即触发。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="3f6e2-127">从编辑器工具栏中单击“蓝图 > 打开关卡蓝图”：</span><span class="sxs-lookup"><span data-stu-id="3f6e2-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![打开关卡蓝图](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="3f6e2-129">将执行节点（左指箭头图标）拖离 Event BeginPlay 并释放。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="3f6e2-130">搜索“启动 AR 会话”并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-130">Search for the **Start AR Session** and hit enter.</span></span>  
    * <span data-ttu-id="3f6e2-131">单击“会话配置”下的“选择资产”下拉列表，然后选择“ARSessionConfig”资产。  </span><span class="sxs-lookup"><span data-stu-id="3f6e2-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 
    * <span data-ttu-id="3f6e2-132">点击“编译”和保存”，然后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-132">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![启动 AR 会话](images/unreal-uxt/3-start-ar-session.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="3f6e2-134">创建 Pawn</span><span class="sxs-lookup"><span data-stu-id="3f6e2-134">Create a Pawn</span></span>
<span data-ttu-id="3f6e2-135">此时，项目仍需要一个玩家对象。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-135">At this point, the project still needs a player object.</span></span> <span data-ttu-id="3f6e2-136">在 Unreal 中，Pawn 表示游戏中的用户，但在本例中它将代表 HoloLens 2 体验。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-136">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="3f6e2-137">在 Content 文件夹中单击“添加新项 > 蓝图类”，展开底部的“所有类”部分。  </span><span class="sxs-lookup"><span data-stu-id="3f6e2-137">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="3f6e2-138">搜索“DefaultPawn”，单击“选择”，然后双击此资产以打开它。 </span><span class="sxs-lookup"><span data-stu-id="3f6e2-138">Search for **DefaultPawn**, click **Select** and double-click the asset to open.</span></span> 

![创建从 DefaultPawn 继承的新 Pawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="3f6e2-140">默认情况下，Pawn 具有网格和碰撞组件。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-140">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="3f6e2-141">在大多数 Unreal 项目中，Pawn 都是可与其他组件碰撞的固体。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-141">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="3f6e2-142">在混合现实中 Pawn 与用户相同，因此需要能够在不发生碰撞的情况下传递全息影像。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-142">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="3f6e2-143">从“组件”面板中选择“CollisionComponent”，向下滚动到“详细信息”面板的“碰撞”部分。   </span><span class="sxs-lookup"><span data-stu-id="3f6e2-143">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="3f6e2-144">单击“碰撞预设”下拉列表，将值更改为“NoCollision”。 </span><span class="sxs-lookup"><span data-stu-id="3f6e2-144">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="3f6e2-145">对“MeshComponent”执行相同的操作，然后“编译”并“保存”蓝图。  </span><span class="sxs-lookup"><span data-stu-id="3f6e2-145">Do the same for the **MeshComponent**, then **Compile** and **Save** the Blueprint.</span></span> 

![调整 Pawn 的碰撞预设](images/unreal-uxt/3-nocollision.PNG)

<span data-ttu-id="3f6e2-147">从此处完成操作后，返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-147">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="3f6e2-148">创建游戏模式</span><span class="sxs-lookup"><span data-stu-id="3f6e2-148">Create a Game Mode</span></span>
<span data-ttu-id="3f6e2-149">混合现实设置的最后一个部分是游戏模式。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-149">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="3f6e2-150">游戏模式决定着游戏或体验的诸多设置，其中包括要使用的默认 Pawn。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-150">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="3f6e2-151">在 Content 文件夹中单击“添加新项 > 蓝图类”，展开底部的“所有类”部分。  </span><span class="sxs-lookup"><span data-stu-id="3f6e2-151">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="3f6e2-152">搜索“游戏模式基”，将其命名为“MRGameMode”并双击以打开。 </span><span class="sxs-lookup"><span data-stu-id="3f6e2-152">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![内容浏览器中的 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="3f6e2-154">转到“详细信息”面板中的“类”部分，将“默认 Pawn 类”更改为“MRPawn”。   。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-154">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="3f6e2-155">点击“编译”和保存”，然后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-155">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![设置默认 Pawn 类](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="3f6e2-157">选择“编辑 > 项目设置”，然后从左侧列表单击“地图和模式”。 </span><span class="sxs-lookup"><span data-stu-id="3f6e2-157">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="3f6e2-158">展开“默认模式”，将“默认游戏模式”更改为“MRGameMode”。  </span><span class="sxs-lookup"><span data-stu-id="3f6e2-158">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="3f6e2-159">展开“默认地图”，将“EditorStartupMap”和“GameDefaultMap”都设置为“主”。   </span><span class="sxs-lookup"><span data-stu-id="3f6e2-159">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="3f6e2-160">这样，当你关闭并重新打开编辑器或玩游戏时，将默认选择主地图。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-160">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![项目设置 - 映射和模式](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="3f6e2-162">针对混合现实全面设置此项目后，你可以继续学习下一个教程，开始将用户输入添加到场景中。</span><span class="sxs-lookup"><span data-stu-id="3f6e2-162">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="3f6e2-163">下一节：4.使场景具有交互性</span><span class="sxs-lookup"><span data-stu-id="3f6e2-163">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)