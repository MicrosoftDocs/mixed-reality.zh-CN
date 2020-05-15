---
title: 2. 初始化你的项目和第一个应用程序
description: 教程（介绍如何使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用）第 2 部分
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851571"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="4ddef-104">2.初始化你的项目和第一个应用程序</span><span class="sxs-lookup"><span data-stu-id="4ddef-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="4ddef-105">本部分介绍如何针对 HoloLens 2 创建新的 Unreal 应用程序。</span><span class="sxs-lookup"><span data-stu-id="4ddef-105">This section gets you started with creating a new Unreal application for HoloLens 2.</span></span> 

## <a name="objectives"></a><span data-ttu-id="4ddef-106">目标</span><span class="sxs-lookup"><span data-stu-id="4ddef-106">Objectives</span></span>

* <span data-ttu-id="4ddef-107">为 Hololens 开发配置 Unreal</span><span class="sxs-lookup"><span data-stu-id="4ddef-107">Configure Unreal for HoloLens development</span></span>
* <span data-ttu-id="4ddef-108">导入资产并设置场景</span><span class="sxs-lookup"><span data-stu-id="4ddef-108">Import assets and set up the scene</span></span>

## <a name="create-a-new-unreal-project"></a><span data-ttu-id="4ddef-109">创建新的 Unreal 项目</span><span class="sxs-lookup"><span data-stu-id="4ddef-109">Create a new Unreal project</span></span>

1. <span data-ttu-id="4ddef-110">启动 Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="4ddef-110">Launch Unreal Engine</span></span>

2. <span data-ttu-id="4ddef-111">在“新项目类别”  下，选择“游戏”  ，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4ddef-111">Under **New Project Categories**, select **Games** and click Next.</span></span> <span data-ttu-id="4ddef-112">选择“空白”  模板，然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="4ddef-112">Select a **Blank** Template and click Next.</span></span> 

![选择“空白”模板](images/unreal-uxt/2-template.PNG)

3. <span data-ttu-id="4ddef-114">在“项目设置”中，选择“C++、可缩放的 3D 或 2D、移动/平板电脑”  ，并选择“非初学者内容”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-114">In Project Settings, choose **C++, Scalable 3D or 2D, Mobile / Tablet**, and **No Starter Content**.</span></span> <span data-ttu-id="4ddef-115">选择项目的保存位置，然后单击“创建项目”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-115">Select a location for your project to be saved and click **Create Project**.</span></span> <span data-ttu-id="4ddef-116">这会在 Visual Studio 项目和 Unreal 编辑器中打开 C++ 文件。</span><span class="sxs-lookup"><span data-stu-id="4ddef-116">This will open up your C++ files in a Visual Studio project and the Unreal editor.</span></span> 

![初始项目设置](images/unreal-uxt/2-project-settings.PNG)

4. <span data-ttu-id="4ddef-118">在左上角，转到“编辑”>“插件”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-118">In the top left-hand corner, go to **Edit > Plugins**.</span></span> <span data-ttu-id="4ddef-119">在“增强现实”下，选中相应的复选框以启用“HoloLens”  插件。</span><span class="sxs-lookup"><span data-stu-id="4ddef-119">Under Augmented Reality, check the box to enable the **HoloLens** plugin.</span></span> <span data-ttu-id="4ddef-120">向下滚动到“虚拟现实”部分，并选中复选框以启用“Microsoft Windows 混合现实”  插件。</span><span class="sxs-lookup"><span data-stu-id="4ddef-120">Scroll down to the Virtual Reality section and check the box to enable the **Microsoft Windows Mixed Reality** plugin.</span></span> <span data-ttu-id="4ddef-121">这两个插件都是 HoloLens 2 开发所必需的。</span><span class="sxs-lookup"><span data-stu-id="4ddef-121">Both plugins are required for HoloLens 2 development.</span></span> <span data-ttu-id="4ddef-122">重新启动编辑器。</span><span class="sxs-lookup"><span data-stu-id="4ddef-122">Restart your editor.</span></span> 

![插件](images/unreal-uxt/2-plugins.PNG)

5. <span data-ttu-id="4ddef-124">在左上角，转到“文件”>“新关卡”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-124">In the top left-hand corner, go to **File > New Level**.</span></span> <span data-ttu-id="4ddef-125">选择“空关卡”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-125">Select **Empty Level**.</span></span> <span data-ttu-id="4ddef-126">视口中的默认场景现在应为空。</span><span class="sxs-lookup"><span data-stu-id="4ddef-126">The default scene in the viewport should now be empty.</span></span>

6. <span data-ttu-id="4ddef-127">从左侧的“模式”面板（位于“基本”选项卡中）拖放 PlayerStart。在右侧的“详细信息”面板中，将位置设置为 X = 0、Y = 0、Z = 0，以使用户在应用启动时从原点开始。</span><span class="sxs-lookup"><span data-stu-id="4ddef-127">Drag PlayerStart and drop PlayerStart from the Modes panel on the left, located in the Basic tab. In the Details panel on the right, set the location to X = 0, Y = 0, Z = 0 in order to have the user start at the origin when the app stars.</span></span>

![具有 PlayerStart 的视口](images/unreal-uxt/2-playerstart.PNG)

7. <span data-ttu-id="4ddef-129">将一个“立方体”  从“模式”面板的“基本”选项卡拖到视口中。</span><span class="sxs-lookup"><span data-stu-id="4ddef-129">Drag a **Cube** from the Basic tab of the Modes panel into the viewport.</span></span> <span data-ttu-id="4ddef-130">在“详细信息”面板中，将位置设置为 X = 50，Y = 0，Z = 0，以在开始时将立方体设置为距离玩家 50 cm。</span><span class="sxs-lookup"><span data-stu-id="4ddef-130">In the Details panel, set the location to X = 50, Y = 0, Z = 0 to set the cube to 50 cm away from the player at start time.</span></span> <span data-ttu-id="4ddef-131">由于默认立方体相当大，因此请将立方体的“比例”更改为 (0.2, 0.2, 0.2)。</span><span class="sxs-lookup"><span data-stu-id="4ddef-131">Since the default cube is quite large, change the Scale of the cube to (0.2, 0.2, 0.2).</span></span> 

8. <span data-ttu-id="4ddef-132">除非向场景添加光源，否则看不到立方体。</span><span class="sxs-lookup"><span data-stu-id="4ddef-132">You won’t be able to see the cube unless you add a light to your scene.</span></span> <span data-ttu-id="4ddef-133">切换到“模式”面板上的“光源”  选项卡，然后将“定向光源”  拖到场景的 PlayerStart 上方。</span><span class="sxs-lookup"><span data-stu-id="4ddef-133">Switch to the **Lights** tab on the Modes panel and drag a **Directional Light** into the scene, above the PlayerStart.</span></span>

![添加了光源的视口](images/unreal-uxt/2-light.PNG)

9.  <span data-ttu-id="4ddef-135">按工具栏上的“开始”  按钮，在视口中查看立方体！</span><span class="sxs-lookup"><span data-stu-id="4ddef-135">Press the **Play** button on the toolbar to see your cube in the viewport!</span></span> <span data-ttu-id="4ddef-136">按 Esc  停止关卡。</span><span class="sxs-lookup"><span data-stu-id="4ddef-136">Press **Esc** to stop the level.</span></span> 

![视口中的立方体](images/unreal-uxt/2-cube.PNG)

10. <span data-ttu-id="4ddef-138">保存关卡。</span><span class="sxs-lookup"><span data-stu-id="4ddef-138">Let’s save your level.</span></span> <span data-ttu-id="4ddef-139">在左上角，单击“文件”>“保存当前关卡”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-139">In the top left corner, click on **File > Save Current**.</span></span> <span data-ttu-id="4ddef-140">将关卡命名为“主关卡”，然后单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-140">Name your level "Main" and click **Save**.</span></span> 

## <a name="set-up-a-chess-scene"></a><span data-ttu-id="4ddef-141">设置象棋场景</span><span class="sxs-lookup"><span data-stu-id="4ddef-141">Set up a chess scene</span></span>

1. <span data-ttu-id="4ddef-142">在“内容浏览器”中，单击“新增”下的图标以显示源面板。</span><span class="sxs-lookup"><span data-stu-id="4ddef-142">In your Content Browser, click icon under Add New to show the sources panel.</span></span> <span data-ttu-id="4ddef-143">然后单击“新增”>“新文件夹”  并将文件夹命名为“ChessAssets”。</span><span class="sxs-lookup"><span data-stu-id="4ddef-143">Then click on **Add New > New Folder** and name the folder “ChessAssets”.</span></span> <span data-ttu-id="4ddef-144">双击此文件夹以在其中导航。</span><span class="sxs-lookup"><span data-stu-id="4ddef-144">Double-click this folder to navigate in.</span></span> <span data-ttu-id="4ddef-145">我们将在此处导入棋具的 3D 资产。</span><span class="sxs-lookup"><span data-stu-id="4ddef-145">This is where we’ll import the 3D assets for our chess set.</span></span>

![显示或隐藏源面板](images/unreal-uxt/2-showhidesources.PNG)

2. <span data-ttu-id="4ddef-147">从 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 下载资产的 zip 文件。</span><span class="sxs-lookup"><span data-stu-id="4ddef-147">Download the zip file of assets from [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).</span></span> <span data-ttu-id="4ddef-148">此文件包含棋盘和棋具的 3D 模型。</span><span class="sxs-lookup"><span data-stu-id="4ddef-148">This file contains the 3D models for a chess board and chess set.</span></span> <span data-ttu-id="4ddef-149">解压缩此文件。</span><span class="sxs-lookup"><span data-stu-id="4ddef-149">Unzip this file.</span></span>

3. <span data-ttu-id="4ddef-150">在“内容浏览器”的顶部，单击“导入”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-150">At the top of the Content Browser, click on **Import**.</span></span> <span data-ttu-id="4ddef-151">导航到刚解压缩的文件夹，并选择其中的所有项。</span><span class="sxs-lookup"><span data-stu-id="4ddef-151">Navigate to the folder that you just unzipped and select all the items within.</span></span> <span data-ttu-id="4ddef-152">此文件夹包含 FBX 文件，这些文件是棋盘和棋子的 3D 对象网格，还包含 TGA 文件，我们将使用这些纹理映射来创建棋盘和棋子的材质。</span><span class="sxs-lookup"><span data-stu-id="4ddef-152">This folder contains FBX files which are the 3D object meshes for our chess board and pieces, as well as TGA files which are the texture maps we’ll use to create materials for our board and pieces.</span></span> <span data-ttu-id="4ddef-153">单击“打开”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-153">Click **Open**.</span></span> 

4. <span data-ttu-id="4ddef-154">将弹出一个“FBX 导入选项”窗口。</span><span class="sxs-lookup"><span data-stu-id="4ddef-154">An FBX Import Options window will pop up.</span></span> <span data-ttu-id="4ddef-155">在“材质”  部分，将“材质导入方法”  更改为“不创建材质”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-155">In the **Material** section, change the **Material Import Method** to **Do Not Create Material**.</span></span> <span data-ttu-id="4ddef-156">然后，单击“全部导入”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-156">Then, click **Import All**.</span></span>

![导入 FBX 选项](images/unreal-uxt/2-nocreatemat.PNG)

5. <span data-ttu-id="4ddef-158">返回“内容”文件夹，创建名为“蓝图”  的新文件夹。</span><span class="sxs-lookup"><span data-stu-id="4ddef-158">Back in your Content folder, create a new folder called **Blueprints**.</span></span> <span data-ttu-id="4ddef-159">我们将在这里存储所有蓝图，这些蓝图为特殊资产，它们提供基于节点的接口来创建新类型的 Actor 和脚本级别事件。</span><span class="sxs-lookup"><span data-stu-id="4ddef-159">This is where we will store all our blueprints, which are special assets that provide a node-based interface to create new types of Actors and script level events.</span></span> 

6. <span data-ttu-id="4ddef-160">双击“蓝图”  文件夹以导航到内部，然后右键单击“内容浏览器”，并选择“蓝图类”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-160">Double click the **Blueprints** folder to navigate inside, then right click in your Content Browser and select **Blueprint Class**.</span></span> <span data-ttu-id="4ddef-161">单击“Actor”  并将新蓝图命名为“棋盘”。</span><span class="sxs-lookup"><span data-stu-id="4ddef-161">Click on **Actor** and name the new blueprint “Board”.</span></span> <span data-ttu-id="4ddef-162">双击“棋盘”将其打开。</span><span class="sxs-lookup"><span data-stu-id="4ddef-162">Double click Board to open it.</span></span> 

![选择蓝图的父类](images/unreal-uxt/2-bpparent.PNG)

![新棋盘蓝图](images/unreal-uxt/2-bpboard.PNG)

7. <span data-ttu-id="4ddef-165">在蓝图编辑器中，导航到“组件”面板，然后单击“添加组件”>“场景”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-165">In the Blueprint editor, navigate to the Components panel and click **Add Component > Scene**.</span></span> <span data-ttu-id="4ddef-166">将新创建的场景命名为“Root”，然后在 DefaultSceneRoot 上单击并拖动 Root。</span><span class="sxs-lookup"><span data-stu-id="4ddef-166">Name the newly created scene “Root”, and then click and drag Root over the DefaultSceneRoot.</span></span> <span data-ttu-id="4ddef-167">这将替换默认的场景 Root，并在视口中消除球面。</span><span class="sxs-lookup"><span data-stu-id="4ddef-167">This will replace the default scene root and get rid of the sphere in the viewport.</span></span> 

![替换 Root](images/unreal-uxt/2-root.PNG)

8. <span data-ttu-id="4ddef-169">再次单击“添加组件”  ，这一次请选择“静态网格”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-169">Click **Add Component** again, and this time choose **Static Mesh**.</span></span> <span data-ttu-id="4ddef-170">将新的静态网格命名为“SM_Board”。</span><span class="sxs-lookup"><span data-stu-id="4ddef-170">Name the new static mesh “SM_Board”.</span></span> 

![添加静态网格](images/unreal-uxt/2-sm-board.PNG)

9. <span data-ttu-id="4ddef-172">在“详细信息”  面板中，找到“静态网格”  部分，然后单击下拉列表。</span><span class="sxs-lookup"><span data-stu-id="4ddef-172">In the **Details** panel, locate the **Static Mesh** section and click the dropdown.</span></span> <span data-ttu-id="4ddef-173">选择“棋盘”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-173">Select **ChessBoard**.</span></span> 

![视口中的棋盘网格](images/unreal-uxt/2-sm-board-view.PNG)

10. <span data-ttu-id="4ddef-175">同样在“详细信息”  面板中，找到“材质”  部分，然后单击下拉列表。</span><span class="sxs-lookup"><span data-stu-id="4ddef-175">Still in the **Details** panel, locate the **Materials** section and click the dropdown.</span></span> <span data-ttu-id="4ddef-176">在“创建新资产”  下，选择“材质”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-176">Under **Create New Asset**, select **Material**.</span></span> <span data-ttu-id="4ddef-177">将此资产命名“M_ChessBoard”  ，并将其保存在“ChessAssets”  文件夹中。</span><span class="sxs-lookup"><span data-stu-id="4ddef-177">Name this asset **M_ChessBoard** and save it in the **ChessAssets** folder.</span></span> 

![创建新材质](images/unreal-uxt/2-newmat.PNG)

11. <span data-ttu-id="4ddef-179">双击“M_ChessBoard”下拉列表旁的方块，打开新创建的 M_ChessBoard 材质。</span><span class="sxs-lookup"><span data-stu-id="4ddef-179">Double click the square next to M_ChessBoard dropdown to open your newly created M_ChessBoard material.</span></span> <span data-ttu-id="4ddef-180">在“材质编辑器”中，单击右键并搜索“纹理示例”  节点。</span><span class="sxs-lookup"><span data-stu-id="4ddef-180">In the Material Editor, right click and search for the **Texture Sample** node.</span></span> <span data-ttu-id="4ddef-181">在“详细信息”  面板中的“材质表现纹理库”  部分下，单击下拉列表并选择“ChessBoard_Albedo”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-181">In the **Details** panel under the **Material Expression Texture Base** section, click the dropdown and select **ChessBoard_Albedo**.</span></span> <span data-ttu-id="4ddef-182">最后，将“RGB”  输出引脚拖至“M_ChessBoard”  的“基准颜色”引脚上。</span><span class="sxs-lookup"><span data-stu-id="4ddef-182">Finally, drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![设置基准颜色](images/unreal-uxt/2-boardalbedomat.PNG)

12. <span data-ttu-id="4ddef-184">重复同样的操作四次，将“ChessBoard_AO”  纹理示例链接到“环境遮蔽”  引脚，将“ChessBoard_Metal”  纹理示例链接到“金属”  引脚，将“ChessBoard_Normal”  纹理示例链接到“正常”  引脚，并将“ChessBoard_Rough”  纹理示例链接到“粗糙度”  引脚。</span><span class="sxs-lookup"><span data-stu-id="4ddef-184">Do the same four more times, linking the **ChessBoard_AO** Texture Sample to the **Ambient Occlusion** pin, the **ChessBoard_Metal** Texture Sample to the **Metallic** pin, the **ChessBoard_Normal** Texture Sample to the **Normal** pin, and the **ChessBoard_Rough** Texture Sample to the **Roughness** pin.</span></span> <span data-ttu-id="4ddef-185">单击 **“保存”** 。</span><span class="sxs-lookup"><span data-stu-id="4ddef-185">Click **Save**.</span></span> 

![连接剩余纹理](images/unreal-uxt/2-boardmat.PNG)

13. <span data-ttu-id="4ddef-187">返回到“棋盘”  蓝图。</span><span class="sxs-lookup"><span data-stu-id="4ddef-187">Return to your **Board** Blueprint.</span></span> <span data-ttu-id="4ddef-188">应会看到刚创建的材质已应用于蓝图。</span><span class="sxs-lookup"><span data-stu-id="4ddef-188">You should see that the material you just created has been applied to your Blueprint.</span></span> <span data-ttu-id="4ddef-189">将棋盘置于场景后，若要确保棋盘的大小和位置，请将棋盘的“比例”  更改为 (0.05, 0.05, 0.05)，将“旋转”  更改为 Z = 90。</span><span class="sxs-lookup"><span data-stu-id="4ddef-189">To ensure the board is at a reasonable size and position once we place it in our scene, change the **Scale** of the board to (0.05, 0.05, 0.05) and the **Rotation** to Z = 90.</span></span> <span data-ttu-id="4ddef-190">在顶部工具栏中，单击“编译”  ，然后单击“保存”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-190">In the toolbar at the top, click **Compile**, then **Save**.</span></span> <span data-ttu-id="4ddef-191">返回到主窗口。</span><span class="sxs-lookup"><span data-stu-id="4ddef-191">Return to your Main window.</span></span> 

![已应用材质的棋盘](images/unreal-uxt/2-chessboard.PNG)

14. <span data-ttu-id="4ddef-193">现在删除立方体，并将其替换为新创建的棋盘 Actor。</span><span class="sxs-lookup"><span data-stu-id="4ddef-193">Let’s now delete the cube and replace it with your newly created Board actor.</span></span> <span data-ttu-id="4ddef-194">在“世界大纲视图”  中，右键单击“立方体”>“编辑”>“删除”  。</span><span class="sxs-lookup"><span data-stu-id="4ddef-194">In the **World Outliner**, right click your **Cube > Edit > Delete**.</span></span> <span data-ttu-id="4ddef-195">将棋盘从“内容浏览器”拖到视口。</span><span class="sxs-lookup"><span data-stu-id="4ddef-195">Drag Board from your Content Browser into the viewport.</span></span> <span data-ttu-id="4ddef-196">将棋盘位置设置为 X = 80，Y = 0，Z =-20。</span><span class="sxs-lookup"><span data-stu-id="4ddef-196">Set the location of the board to X = 80, Y = 0, Z = -20.</span></span> 

15. <span data-ttu-id="4ddef-197">单击“开始”  按钮，查看你所处关卡中的新棋盘。</span><span class="sxs-lookup"><span data-stu-id="4ddef-197">Click the **Play** button to view your new board in your level.</span></span> <span data-ttu-id="4ddef-198">按 Esc  返回到编辑器。</span><span class="sxs-lookup"><span data-stu-id="4ddef-198">Press **Esc** to return to the editor.</span></span> 

16. <span data-ttu-id="4ddef-199">接下来，我们将按照与对棋盘所执行的相同步骤创建棋子，这次选择棋子的网格和材质：</span><span class="sxs-lookup"><span data-stu-id="4ddef-199">Now we’ll follow the same steps to create a chess piece as we did with the board, this time selecting the mesh and material for the chess piece:</span></span>

    <span data-ttu-id="4ddef-200">a) 在“内容浏览器”中导航到“蓝图”文件夹，然后创建一个 Actor 类型的新蓝图类。</span><span class="sxs-lookup"><span data-stu-id="4ddef-200">a) Navigate to the Blueprints folder in the Content Browser and create a new Blueprint class of type Actor.</span></span> <span data-ttu-id="4ddef-201">将此 Actor 命名为“WhiteKing”。</span><span class="sxs-lookup"><span data-stu-id="4ddef-201">Name this actor “WhiteKing”.</span></span>

    <span data-ttu-id="4ddef-202">b) 双击“WhiteKing”将其打开。</span><span class="sxs-lookup"><span data-stu-id="4ddef-202">b) Double click WhiteKing to open it.</span></span> <span data-ttu-id="4ddef-203">添加一个名为“Root”的新场景组件，并使用它来替换 DefaultSceneRoot。</span><span class="sxs-lookup"><span data-stu-id="4ddef-203">Add a new Scene component named “Root” and use it to replace DefaultSceneRoot.</span></span> 

    <span data-ttu-id="4ddef-204">c) 添加一个名为“SM_King”的新静态网格组件。</span><span class="sxs-lookup"><span data-stu-id="4ddef-204">c) Add a new Static Mesh component named “SM_King”.</span></span> <span data-ttu-id="4ddef-205">在“详细信息”面板中，将“静态网格”  设置为“Chess_King”  ，并将“材质”  设置为名为“M_ChessWhite”  的新材质。</span><span class="sxs-lookup"><span data-stu-id="4ddef-205">In the Details panel, set the **Static Mesh** to **Chess_King** and the **Material** to a new Material called **M_ChessWhite**.</span></span> 

    <span data-ttu-id="4ddef-206">d) 打开新“M_ChessWhite”  材质，并将相关纹理连接到相应的材质输入。</span><span class="sxs-lookup"><span data-stu-id="4ddef-206">d) Open the new **M_ChessWhite** Material and hook up the relevant textures to their corresponding material inputs.</span></span> 

    ![为国王（棋子）创建材质](images/unreal-uxt/2-chesskingmat.PNG)

    <span data-ttu-id="4ddef-208">e) 返回到“WhiteKing”  蓝图，将“比例”  更改为 (0.05, 0.05, 0.05)，将“旋转”  更改为 Z = 90。</span><span class="sxs-lookup"><span data-stu-id="4ddef-208">e) Back in your **WhiteKing** Blueprint, change the **Scale** to (0.05, 0.05, 0.05) and **Rotation** to Z = 90.</span></span>

    <span data-ttu-id="4ddef-209">f) 编译并保存蓝图，然后导航回主窗口。</span><span class="sxs-lookup"><span data-stu-id="4ddef-209">f) Compile and save your blueprint, then navigate back to your main window.</span></span> 

17. <span data-ttu-id="4ddef-210">将“WhiteKing”拖动到视口中。</span><span class="sxs-lookup"><span data-stu-id="4ddef-210">Drag WhiteKing into your viewport.</span></span> <span data-ttu-id="4ddef-211">在“世界大纲视图”  中，将“WhiteKing”拖到棋盘，以便 WhiteKing 成为棋盘的子元素。</span><span class="sxs-lookup"><span data-stu-id="4ddef-211">In the **World Outliner**, drag WhiteKing onto Board so that WhiteKing is now a child of Board.</span></span> 

![世界大纲视图](images/unreal-uxt/2-child.PNG)

18. <span data-ttu-id="4ddef-213">在“详细信息”  面板下的“变形”  部分，将 WhiteKing 的“位置”  设置为 X =-26，Y = 4，Z = 0</span><span class="sxs-lookup"><span data-stu-id="4ddef-213">In the **Details** panel under **Transform**, set the **Location** of WhiteKing to X = -26, Y = 4, Z = 0</span></span>

19. <span data-ttu-id="4ddef-214">单击“开始”  查看关卡。</span><span class="sxs-lookup"><span data-stu-id="4ddef-214">Click **Play** to see your level.</span></span> <span data-ttu-id="4ddef-215">按 Esc  退出。</span><span class="sxs-lookup"><span data-stu-id="4ddef-215">Press **Esc** to exit.</span></span> 

[<span data-ttu-id="4ddef-216">下一节：3.设置混合现实项目</span><span class="sxs-lookup"><span data-stu-id="4ddef-216">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)