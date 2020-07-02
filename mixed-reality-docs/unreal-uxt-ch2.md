---
title: 2. 初始化你的项目和第一个应用程序
description: 教程系列第 2 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: 150fee721bb9cd72d287737aca4262bd87dccba8
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345727"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="8a951-104">2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="8a951-104">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="8a951-105">概述</span><span class="sxs-lookup"><span data-stu-id="8a951-105">Overview</span></span>

<span data-ttu-id="8a951-106">在第一个教程中，你将开始使用适用于 HoloLens 2 的新 Unreal 应用程序。</span><span class="sxs-lookup"><span data-stu-id="8a951-106">In this first tutorial, you'll get started with a new Unreal application for HoloLens 2.</span></span> <span data-ttu-id="8a951-107">这包括添加 HoloLens 插件、创建和点亮关卡，并使用游戏板和棋子来填充它。</span><span class="sxs-lookup"><span data-stu-id="8a951-107">This is going to include adding the HoloLens plugin, creating and lighting a level, and populating it with a game board and chess piece.</span></span> <span data-ttu-id="8a951-108">你会将预制的资产用于 3D 棋子和对象材质，因此不必担心要从头开始建模。</span><span class="sxs-lookup"><span data-stu-id="8a951-108">You'll be using pre-made assets for the 3D chess piece and object materials, so don't worry about modeling anything from scratch.</span></span> <span data-ttu-id="8a951-109">本教程结束时，有一个可用于混合现实的空白画布。</span><span class="sxs-lookup"><span data-stu-id="8a951-109">By the end of this tutorial you'll have a blank canvas that's ready for mixed reality.</span></span>

<span data-ttu-id="8a951-110">在继续之前，请确保满足[入门](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1)页面中的所有先决条件。</span><span class="sxs-lookup"><span data-stu-id="8a951-110">Before continuing, make sure you have all the prerequisites from the [Getting Started](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="8a951-111">目标</span><span class="sxs-lookup"><span data-stu-id="8a951-111">Objectives</span></span>
* <span data-ttu-id="8a951-112">为 HoloLens 开发配置 Unreal 项目</span><span class="sxs-lookup"><span data-stu-id="8a951-112">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="8a951-113">导入资产和设置场景</span><span class="sxs-lookup"><span data-stu-id="8a951-113">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="8a951-114">使用蓝图创建 Actor 和脚本级别事件</span><span class="sxs-lookup"><span data-stu-id="8a951-114">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="8a951-115">创建新的 Unreal 项目</span><span class="sxs-lookup"><span data-stu-id="8a951-115">Creating a new Unreal project</span></span>
<span data-ttu-id="8a951-116">首先需要一个待处理的项目。</span><span class="sxs-lookup"><span data-stu-id="8a951-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="8a951-117">如果这是你第一次为 HoloLens 创建 Unreal 应用，则需要从 Epic Launcher [下载支持文件](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app)。</span><span class="sxs-lookup"><span data-stu-id="8a951-117">If this is your first time creating an Unreal app for HoloLens, you'll need to [download supporting files](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) from the Epic Launcher.</span></span>

1. <span data-ttu-id="8a951-118">启动 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="8a951-118">Launch Unreal Engine</span></span>

2. <span data-ttu-id="8a951-119">在“新项目类别”中选择“游戏”，然后单击“下一步”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-119">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![选择游戏项目模板](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="8a951-121">选择“空白”模板，然后单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="8a951-121">Select the **Blank** Template and click **Next**.</span></span> 

![选择“空白”模板](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="8a951-123">选择“C++”、“可缩放的 3D 或 2D”、“移动/平板电脑”和“非初学者内容”作为“项目设置”   。</span><span class="sxs-lookup"><span data-stu-id="8a951-123">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**.</span></span> 
    * <span data-ttu-id="8a951-124">选择一个保存位置，然后单击“创建项目”。</span><span class="sxs-lookup"><span data-stu-id="8a951-124">Choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="8a951-125">为了生成 UX Tools 插件，必须选择 C++ 项目而不是 Blueprint 项目，你稍后将在第 4 节中对此进行设置。</span><span class="sxs-lookup"><span data-stu-id="8a951-125">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![初始项目设置](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="8a951-127">项目应在 Unreal 编辑器中自动打开，这意味着你已准备好进入下一部分。</span><span class="sxs-lookup"><span data-stu-id="8a951-127">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="8a951-128">启用所需插件</span><span class="sxs-lookup"><span data-stu-id="8a951-128">Enabling required plugins</span></span>
<span data-ttu-id="8a951-129">在开始向场景添加对象之前，你需要启用两个插件。</span><span class="sxs-lookup"><span data-stu-id="8a951-129">Before you start adding objects to the scene you'll need to enable two plugins.</span></span>

1. <span data-ttu-id="8a951-130">打开“编辑”>“插件”，并从内置选项列表中选择“增强现实”。</span><span class="sxs-lookup"><span data-stu-id="8a951-130">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="8a951-131">向下滚动到“HoloLens”并选中“已启用”。</span><span class="sxs-lookup"><span data-stu-id="8a951-131">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![启用 HoloLens 插件](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="8a951-133">从内置选项列表中选择“虚拟现实”。</span><span class="sxs-lookup"><span data-stu-id="8a951-133">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="8a951-134">向下滚动到“Microsoft Windows Mixed Reality”，选择“已启用”，然后重启编辑器 。</span><span class="sxs-lookup"><span data-stu-id="8a951-134">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![启用 Windows Mixed Reality 插件](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="8a951-136">这两个插件都是 HoloLens 2 开发所必需的。</span><span class="sxs-lookup"><span data-stu-id="8a951-136">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="8a951-137">完成此操作后，公司即可使用空关卡。</span><span class="sxs-lookup"><span data-stu-id="8a951-137">With that done your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="8a951-138">创建关卡</span><span class="sxs-lookup"><span data-stu-id="8a951-138">Creating a level</span></span>
<span data-ttu-id="8a951-139">下一个任务是创建具有可供参考和缩放的起点和立方体的简单玩家设置。</span><span class="sxs-lookup"><span data-stu-id="8a951-139">Your next task is to create a simple player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="8a951-140">选择“文件”>“新关卡”>“空关卡”。</span><span class="sxs-lookup"><span data-stu-id="8a951-140">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="8a951-141">视口中的默认场景现在应为空。</span><span class="sxs-lookup"><span data-stu-id="8a951-141">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="8a951-142">从“模式”选项卡中选择“基本”，并将“PlayerStart”拖到场景中  。</span><span class="sxs-lookup"><span data-stu-id="8a951-142">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="8a951-143">在“详细信息”选项卡中，将“位置”设置为“X = 0”、“Y = 0”和“Z = 0”    。这会在应用启动时将用户设置到场景的中心。</span><span class="sxs-lookup"><span data-stu-id="8a951-143">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab. This sets the user at the center of the scene when the app starts up.</span></span>

![具有 PlayerStart 的视口](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="8a951-145">将“立方体”从“基本”选项卡拖到场景中 。</span><span class="sxs-lookup"><span data-stu-id="8a951-145">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="8a951-146">将“位置”设置为“X = 50”、“Y = 0”和“Z = 0”   。</span><span class="sxs-lookup"><span data-stu-id="8a951-146">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="8a951-147">这会在启动时将立方体放在距离玩家 50 厘米的位置。</span><span class="sxs-lookup"><span data-stu-id="8a951-147">This positions the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="8a951-148">将“比例”更改为“X = 0.2”、“Y = 0.2”和“Z = 0.2”以缩小立方体   。</span><span class="sxs-lookup"><span data-stu-id="8a951-148">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="8a951-149">除非向场景添加光源（这是测试场景前的最后一个任务），否则看不到立方体。</span><span class="sxs-lookup"><span data-stu-id="8a951-149">You won’t be able to see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="8a951-150">切换到“模式”面板上的“光源”选项卡，然后将“定向光源”拖到场景中  。</span><span class="sxs-lookup"><span data-stu-id="8a951-150">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="8a951-151">将光源置于“PlayerStart”上方，以便可以看到该光源。</span><span class="sxs-lookup"><span data-stu-id="8a951-151">Position the light above **PlayerStart** so you can see it.</span></span>

![添加了光源的视口](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="8a951-153">转到“文件”>“保存当前”，将关卡命名为“主”，然后单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-153">Go to **File > Save Current**, name your level **Main**, and click **Save**.</span></span> 

<span data-ttu-id="8a951-154">设置场景后，按工具栏中的“开始”，以查看正在运行的立方体！</span><span class="sxs-lookup"><span data-stu-id="8a951-154">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="8a951-155">完成工作后，按 Esc 停止应用程序。</span><span class="sxs-lookup"><span data-stu-id="8a951-155">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![视口中的立方体](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="8a951-157">设置场景后，便可以开始在棋盘和棋子中进行添加以构成应用程序环境。</span><span class="sxs-lookup"><span data-stu-id="8a951-157">Now that the scene is setup, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="8a951-158">导入资产</span><span class="sxs-lookup"><span data-stu-id="8a951-158">Importing assets</span></span>
<span data-ttu-id="8a951-159">场景目前看起来非常空，但通过将现成的资产导入到项目中，将解决此问题。</span><span class="sxs-lookup"><span data-stu-id="8a951-159">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="8a951-160">下载并解压缩 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 资产文件夹。</span><span class="sxs-lookup"><span data-stu-id="8a951-160">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder.</span></span>

2. <span data-ttu-id="8a951-161">从“内容浏览器”中单击“新增”>“新建文件夹”，然后将其命名为“ChessAssets”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-161">Click **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="8a951-162">双击新文件夹 - 这是导入 3D 资产的位置。</span><span class="sxs-lookup"><span data-stu-id="8a951-162">Double-click the new folder - this is where you'll import the 3D assets.</span></span>

![显示或隐藏源面板](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="8a951-164">从“内容浏览器”中单击“导入”，选择解压缩的资产文件夹中的所有项目，然后单击“打开”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-164">Click **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="8a951-165">此文件夹包含棋盘和棋子的 3D 对象网格（采用 FBX 格式）和用于材质的纹理映射（采用 TGA 格式）。</span><span class="sxs-lookup"><span data-stu-id="8a951-165">This folder contains the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="8a951-166">弹出“FBX 导入选项”窗口后，展开“材质”部分，并将“材质导入方法”更改为“不创建材质”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-166">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="8a951-167">单击“全部导入”。</span><span class="sxs-lookup"><span data-stu-id="8a951-167">Click **Import All**.</span></span>

![导入 FBX 选项](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="8a951-169">资产只需执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="8a951-169">That's all you need to do for the assets.</span></span> <span data-ttu-id="8a951-170">接下来的一组任务是使用蓝图创建应用程序的构建基块。</span><span class="sxs-lookup"><span data-stu-id="8a951-170">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="8a951-171">添加蓝图</span><span class="sxs-lookup"><span data-stu-id="8a951-171">Adding blueprints</span></span>

1. <span data-ttu-id="8a951-172">在“内容浏览器”中单击“新增”>“新建文件夹”，然后将其命名为“内容浏览器”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-172">Click **Add New > New Folder** in the **Content Browser** and name it **Content Browser**.</span></span> 

> [!NOTE]
> <span data-ttu-id="8a951-173">如果你不熟悉[蓝图](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)，这些蓝图为特殊资产，它们提供基于节点的接口来创建新类型的 Actor 和脚本级别事件。</span><span class="sxs-lookup"><span data-stu-id="8a951-173">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="8a951-174">双击“蓝图”文件夹，然后右键单击并选择“蓝图类”。</span><span class="sxs-lookup"><span data-stu-id="8a951-174">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="8a951-175">选择“Actor”并将蓝图命名为“棋盘”。</span><span class="sxs-lookup"><span data-stu-id="8a951-175">Select **Actor** and name the blueprint **Board**.</span></span> 

![选择蓝图的父类](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="8a951-177">新的棋盘蓝图现在显示在“蓝图”文件夹中，如以下屏幕截图中所示 。</span><span class="sxs-lookup"><span data-stu-id="8a951-177">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![新棋盘蓝图](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="8a951-179">你已经准备好开始向创建的对象添加材质。</span><span class="sxs-lookup"><span data-stu-id="8a951-179">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="8a951-180">使用材质</span><span class="sxs-lookup"><span data-stu-id="8a951-180">Working with materials</span></span>
<span data-ttu-id="8a951-181">你创建的对象默认为灰色，这看上去太过普通。</span><span class="sxs-lookup"><span data-stu-id="8a951-181">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="8a951-182">向对象添加材质和网格是本教程中的最后一组任务。</span><span class="sxs-lookup"><span data-stu-id="8a951-182">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="8a951-183">双击“棋盘”以打开蓝图编辑器。</span><span class="sxs-lookup"><span data-stu-id="8a951-183">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="8a951-184">从“组件”面板中单击“添加组件”>“场景”，并将其命名为“Root”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-184">Click **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="8a951-185">请注意，“Root”在下面的屏幕截图中显示为 DefaultSceneRoot 的子项 ：</span><span class="sxs-lookup"><span data-stu-id="8a951-185">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![替换 Root](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="8a951-187">单击“Root”并将其拖到 DefaultSceneRoot 中，以替换它并在视口中消除球面 。</span><span class="sxs-lookup"><span data-stu-id="8a951-187">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![替换 Root](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="8a951-189">从“组件”面板中单击“添加组件”>“静态网格”，并将其命名为“SM_Board”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-189">Click **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="8a951-190">它将在“Root”下显示为子对象。</span><span class="sxs-lookup"><span data-stu-id="8a951-190">It will appear as a child object under **Root**.</span></span>

![添加静态网格](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="8a951-192">单击“SM_Board”，向下滚动到“详细信息”面板的“静态网格”部分，并从下拉列表中选择“棋盘”   。</span><span class="sxs-lookup"><span data-stu-id="8a951-192">Click **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![视口中的棋盘网格](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="8a951-194">继续在“详细信息”面板中，展开“材质”部分，然后从下拉列表中单击“新建资产”>“材质”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-194">Still in the **Details** panel, expand the **Materials** section and click **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="8a951-195">将材质命名为“M_ChessBoard”，并将其保存到“ChessAssets”文件夹中。</span><span class="sxs-lookup"><span data-stu-id="8a951-195">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![创建新材质](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="8a951-197">双击“M_ChessBoard”材质映像以打开材质编辑器。</span><span class="sxs-lookup"><span data-stu-id="8a951-197">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![打开材质编辑器](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="8a951-199">在材质编辑器中，单击右键并搜索“纹理示例”。</span><span class="sxs-lookup"><span data-stu-id="8a951-199">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="8a951-200">在“详细信息”面板中展开“材质表现纹理库”部分，然后将“纹理”设置为“ChessBoard_Albedo”   。</span><span class="sxs-lookup"><span data-stu-id="8a951-200">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="8a951-201">将“RGB”输出引脚拖至“M_ChessBoard”的“基准颜色”引脚上。</span><span class="sxs-lookup"><span data-stu-id="8a951-201">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![设置基准颜色](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="8a951-203">重复上述步骤四次以再创建四个具有以下设置的“纹理示例”节点：</span><span class="sxs-lookup"><span data-stu-id="8a951-203">Repeat the previous step four more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="8a951-204">将“纹理”设置为“ChessBoard_AO”，将“RGB”链接到“环境遮蔽”引脚   。</span><span class="sxs-lookup"><span data-stu-id="8a951-204">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="8a951-205">将“纹理”设置为“ChessBoard_Metal”，将“RGB”链接到“金属”引脚   。</span><span class="sxs-lookup"><span data-stu-id="8a951-205">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="8a951-206">将“纹理”设置为“ChessBoard_Normal”，将“RGB”链接到“正常”引脚   。</span><span class="sxs-lookup"><span data-stu-id="8a951-206">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="8a951-207">将“纹理”设置为“ChessBoard_Rough”，将“RGB”链接到“粗糙度”引脚   。</span><span class="sxs-lookup"><span data-stu-id="8a951-207">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="8a951-208">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="8a951-208">Click **Save**.</span></span> 

![连接剩余纹理](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="8a951-210">在继续之前，请确保材质设置看起来类似于以上屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="8a951-210">Make sure the your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="8a951-211">填充场景</span><span class="sxs-lookup"><span data-stu-id="8a951-211">Populating the scene</span></span>
<span data-ttu-id="8a951-212">如果返回到“棋盘”蓝图，将会看到已应用刚创建的材质。</span><span class="sxs-lookup"><span data-stu-id="8a951-212">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="8a951-213">只需设置场景即可！</span><span class="sxs-lookup"><span data-stu-id="8a951-213">All that's left is setting up the scene!</span></span> <span data-ttu-id="8a951-214">首先，更改以下属性，以确保在场景中放置棋盘时，它的大小和角度正确：</span><span class="sxs-lookup"><span data-stu-id="8a951-214">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="8a951-215">将“比例”设置为“(0.05, 0.05, 0.05)”并将“Z 旋转”设置为“90”   。</span><span class="sxs-lookup"><span data-stu-id="8a951-215">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="8a951-216">单击顶部工具栏中的“编译”，然后单击“保存”并返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="8a951-216">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![已应用材质的棋盘](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="8a951-218">右键单击“立方体”>“编辑”>“删除”并将“棋盘”从“内容浏览器”拖至视口中  。</span><span class="sxs-lookup"><span data-stu-id="8a951-218">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="8a951-219">将“位置”设置为“X = 80”、“Y = 0”和“Z = -20”   。</span><span class="sxs-lookup"><span data-stu-id="8a951-219">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="8a951-220">单击“开始”按钮，查看你所处关卡中的新棋盘。</span><span class="sxs-lookup"><span data-stu-id="8a951-220">Click the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="8a951-221">按 Esc 返回到编辑器。</span><span class="sxs-lookup"><span data-stu-id="8a951-221">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="8a951-222">现在，你将按照与棋盘相同的步骤创建棋子：</span><span class="sxs-lookup"><span data-stu-id="8a951-222">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="8a951-223">转到“蓝图”文件夹，右键单击并选择“蓝图类”，然后选择“Actor”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-223">Go to the **Blueprints** folder, right-click and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="8a951-224">将 Actor 命名为“WhiteKing”。</span><span class="sxs-lookup"><span data-stu-id="8a951-224">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="8a951-225">双击“WhiteKing”以在蓝图编辑器中将其打开，单击“添加组件”>“场景”，并将其命名为“Root”  。</span><span class="sxs-lookup"><span data-stu-id="8a951-225">Double click **WhiteKing** to open it in the Blueprint Editor, click **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="8a951-226">将“Root”拖放到 DefaultSceneRoot 中来替换它 。</span><span class="sxs-lookup"><span data-stu-id="8a951-226">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="8a951-227">单击“添加组件”>“静态网格”，并将其命名为“SM_King” 。</span><span class="sxs-lookup"><span data-stu-id="8a951-227">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="8a951-228">在“详细信息”面板中，将“静态网格”设置为“Chess_King”，并将“材质”设置为名为“M_ChessWhite”的新材质。</span><span class="sxs-lookup"><span data-stu-id="8a951-228">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="8a951-229">在材质编辑器中打开“M_ChessWhite”，并将以下“纹理示例”节点连接到以下各项：</span><span class="sxs-lookup"><span data-stu-id="8a951-229">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
    * <span data-ttu-id="8a951-230">将“纹理”设置为“ChessWhite_AO”，将“RGB”链接到“环境遮蔽”引脚   。</span><span class="sxs-lookup"><span data-stu-id="8a951-230">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="8a951-231">将“纹理”设置为“ChessWhite_Metal”，将“RGB”链接到“金属”引脚   。</span><span class="sxs-lookup"><span data-stu-id="8a951-231">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="8a951-232">将“纹理”设置为“ChessWhite_Normal”，将“RGB”链接到“正常”引脚   。</span><span class="sxs-lookup"><span data-stu-id="8a951-232">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="8a951-233">将“纹理”设置为“ChessWhite_Rough”，将“RGB”链接到“粗糙度”引脚   。</span><span class="sxs-lookup"><span data-stu-id="8a951-233">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="8a951-234">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="8a951-234">Click **Save**.</span></span> 

<span data-ttu-id="8a951-235">在继续之前，“M_ChessKing”材质应与下图类似。</span><span class="sxs-lookup"><span data-stu-id="8a951-235">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![为国王（棋子）创建材质](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="8a951-237">即将完成，只需将新棋子添加到场景中即可：</span><span class="sxs-lookup"><span data-stu-id="8a951-237">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="8a951-238">打开“WhiteKing”蓝图，并将“比例”更改为“(0.05, 0.05, 0.05)”，将“Z 旋转”更改为“90”。</span><span class="sxs-lookup"><span data-stu-id="8a951-238">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="8a951-239">编译并保存蓝图，然后返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="8a951-239">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="8a951-240">将“WhiteKing”拖到视口中，切换到“世界大纲视图”面板，将“WhiteKing”拖到“棋盘”上，使其成为子对象。</span><span class="sxs-lookup"><span data-stu-id="8a951-240">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![世界大纲视图](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="8a951-242">在“详细信息”面板中的“变形”下，将 WhiteKing 的“位置”设置为“X = -26”、“Y = 4”、“Z = 0”      。</span><span class="sxs-lookup"><span data-stu-id="8a951-242">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="8a951-243">完成！</span><span class="sxs-lookup"><span data-stu-id="8a951-243">That's a wrap!</span></span> <span data-ttu-id="8a951-244">单击“开始”以查看正在运行中的已填充关卡，并在准备好退出时按 Esc。</span><span class="sxs-lookup"><span data-stu-id="8a951-244">Click **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="8a951-245">本教程介绍了很多创建简单项目的背景，但你的项目已准备好继续进行本系列的下一部分：设置混合现实。</span><span class="sxs-lookup"><span data-stu-id="8a951-245">This tutorial covered a lot of ground creating a simple project, but your project is ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="8a951-246">下一节：3.设置混合现实项目</span><span class="sxs-lookup"><span data-stu-id="8a951-246">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)
