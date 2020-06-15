---
title: 2. 初始化你的项目和第一个应用程序
description: 教程系列第 2 部分（共 6 部分）- 使用 Unreal Engine 4 和混合现实工具包 UX Tools 插件构建一款简单的象棋应用
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 教程, 入门, mrtk, uxt, UX Tools, 文档
ms.openlocfilehash: e8f03a87ec6b92e4c62cf3f88f519146254e7387
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330321"
---
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化你的项目和第一个应用程序

## <a name="overview"></a>概述

在第一个教程中，你将开始使用适用于 HoloLens 2 的新 Unreal 应用程序。 这包括添加 HoloLens 插件、创建和点亮关卡，并使用游戏板和棋子来填充它。 你会将预制的资产用于 3D 棋子和对象材质，因此不必担心要从头开始建模。 本教程结束时，有一个可用于混合现实的空白画布。

在继续之前，请确保满足[入门](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1)页中的所有先决条件。

## <a name="objectives"></a>目标
* 为 HoloLens 开发配置 Unreal 项目
* 导入资产和设置场景
* 使用蓝图创建 Actor 和脚本级别事件

## <a name="creating-a-new-unreal-project"></a>创建新的 Unreal 项目
首先需要一个待处理的项目。

1. 启动 Unreal Engine

2. 在“新项目类别”中选择“游戏”，然后单击“下一步”  。 

![选择游戏项目模板](images/unreal-uxt/2-gamestemplate.png)

3. 选择“空白”模板，然后单击“下一步” 。 

![选择“空白”模板](images/unreal-uxt/2-template.PNG)

4. 选择“C++”、“可缩放的 3D 或 2D”、“移动/平板电脑”和“非初学者内容”作为“项目设置”   。 
    * 选择一个保存位置，然后单击“创建项目”。 

![初始项目设置](images/unreal-uxt/2-project-settings.PNG)

项目应在 Unreal 编辑器中自动打开，这意味着你已准备好进入下一部分。

## <a name="enabling-required-plugins"></a>启用所需插件
在开始向场景添加对象之前，你需要启用两个插件。

1. 打开“编辑”>“插件”，并从内置选项列表中选择“增强现实”。 
    * 向下滚动到“HoloLens”并选中“已启用”。 

![启用 HoloLens 插件](images/unreal-uxt/2-plugins.PNG)

2. 从内置选项列表中选择“虚拟现实”。 
    * 向下滚动到“Microsoft Windows Mixed Reality”，选中“已启用”，然后重新启动编辑器。 

![启用 Windows Mixed Reality 插件](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> 这两个插件都是 HoloLens 2 开发所必需的。

完成此操作后，公司即可使用空关卡。

## <a name="creating-a-level"></a>创建关卡
下一个任务是创建具有可供参考和缩放的起点和立方体的简单玩家设置。

1. 选择“文件”>“新关卡”>“空关卡”。 视口中的默认场景现在应为空。

2. 从“模式”选项卡中选择“基本”，并将“PlayerStart”拖到场景中  。 
    * 在“详细信息”选项卡中，将“位置”设置为“X = 0”、“Y = 0”和“Z = 0”    。这会在应用启动时将用户设置到场景的中心。

![具有 PlayerStart 的视口](images/unreal-uxt/2-playerstart.PNG)

3. 将“立方体”从“基本”选项卡拖到场景中 。 
    * 将“位置”设置为“X = 50”、“Y = 0”和“Z = 0”   。 这会在启动时将立方体放在距离玩家 50 厘米的位置。 
    * 将“比例”更改为“X = 0.2”、“Y = 0.2”和“Z = 0.2”以缩小立方体   。 

除非向场景添加光源（这是测试场景前的最后一个任务），否则看不到立方体。

4. 切换到“模式”面板上的“光源”选项卡，然后将“定向光源”拖到场景中  。 将光源置于“PlayerStart”上方，以便可以看到该光源。

![添加了光源的视口](images/unreal-uxt/2-light.PNG)

5. 转到“文件”>“保存当前”，将关卡命名为“主”，然后单击“保存”  。 

设置场景后，按工具栏中的“开始”，以查看正在运行的立方体！ 完成工作后，按 Esc 停止应用程序。

![视口中的立方体](images/unreal-uxt/2-cube.PNG)

设置场景后，便可以开始在棋盘和棋子中进行添加以构成应用程序环境。

## <a name="importing-assets"></a>导入资产
场景目前看起来非常空，但通过将现成的资产导入到项目中，将解决此问题。

1. 下载并解压缩 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 资产文件夹。

2. 从“内容浏览器”中单击“新增”>“新建文件夹”，然后将其命名为“ChessAssets”  。 
    * 双击新文件夹 - 这是导入 3D 资产的位置。

![显示或隐藏源面板](images/unreal-uxt/2-showhidesources.PNG)

3. 从“内容浏览器”中单击“导入”，选择解压缩的资产文件夹中的所有项目，然后单击“打开”  。 
    * 此文件夹包含棋盘和棋子的 3D 对象网格（采用 FBX 格式）和用于材质的纹理映射（采用 TGA 格式）。  

4. 弹出“FBX 导入选项”窗口后，展开“材质”部分，并将“材质导入方法”更改为“不创建材质”  。
    * 单击“全部导入”。

![导入 FBX 选项](images/unreal-uxt/2-nocreatemat.PNG)

资产只需执行这些操作。 接下来的一组任务是使用蓝图创建应用程序的构建基块。

## <a name="adding-blueprints"></a>添加蓝图

1. 在“内容浏览器”中单击“新增”>“新建文件夹”，然后将其命名为“内容浏览器”  。 

> [!NOTE]
> 如果你不熟悉[蓝图](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)，这些蓝图为特殊资产，它们提供基于节点的接口来创建新类型的 Actor 和脚本级别事件。 

2. 双击“蓝图”文件夹，然后右键单击并选择“蓝图类”。         
    * 选择“Actor”并将蓝图命名为“棋盘”。 

![选择蓝图的父类](images/unreal-uxt/2-bpparent.PNG)

新的棋盘蓝图现在显示在“蓝图”文件夹中，如以下屏幕截图中所示 。 

![新棋盘蓝图](images/unreal-uxt/2-bpboard.PNG)

你已经准备好开始向创建的对象添加材质。

## <a name="working-with-materials"></a>使用材质
你创建的对象默认为灰色，这看上去太过普通。 向对象添加材质和网格是本教程中的最后一组任务。

1. 双击“棋盘”以打开蓝图编辑器。 

2. 从“组件”面板中单击“添加组件”>“场景”，并将其命名为“Root”  。 请注意，“Root”在下面的屏幕截图中显示为 DefaultSceneRoot 的子项 ：

![替换 Root](images/unreal-uxt/2-root-blueprint.PNG)


3. 单击“Root”并将其拖到 DefaultSceneRoot 中，以替换它并在视口中消除球面 。 

![替换 Root](images/unreal-uxt/2-root.PNG)


4. 从“组件”面板中单击“添加组件”>“静态网格”，并将其命名为“SM_Board”  。 它将在“Root”下显示为子对象。

![添加静态网格](images/unreal-uxt/2-sm-board.PNG)

4. 单击“SM_Board”，向下滚动到“详细信息”面板的“静态网格”部分，并从下拉列表中选择“棋盘”   。 

![视口中的棋盘网格](images/unreal-uxt/2-sm-board-view.PNG)

5.  继续在“详细信息”面板中，展开“材质”部分，然后从下拉列表中单击“新建资产”>“材质”  。 
    * 将材质命名为“M_ChessBoard”，并将其保存到“ChessAssets”文件夹中。 

![创建新材质](images/unreal-uxt/2-newmat.PNG)

6.  双击“M_ChessBoard”材质映像以打开材质编辑器。 

![打开材质编辑器](images/unreal-uxt/2-material-editor.PNG)

7. 在材质编辑器中，单击右键并搜索“纹理示例”。 
    * 在“详细信息”面板中展开“材质表现纹理库”部分，然后将“纹理”设置为“ChessBoard_Albedo”   。 
    * 将“RGB”输出引脚拖至“M_ChessBoard”的“基准颜色”引脚上。 

![设置基准颜色](images/unreal-uxt/2-boardalbedomat.PNG)

8.  重复上述步骤四次以再创建四个具有以下设置的“纹理示例”节点：
    * 将“纹理”设置为“ChessBoard_AO”，将“RGB”链接到“环境遮蔽”引脚   。
    * 将“纹理”设置为“ChessBoard_Metal”，将“RGB”链接到“金属”引脚   。 
    * 将“纹理”设置为“ChessBoard_Normal”，将“RGB”链接到“正常”引脚   。
    * 将“纹理”设置为“ChessBoard_Rough”，将“RGB”链接到“粗糙度”引脚   。 
    * 单击 **“保存”** 。 

![连接剩余纹理](images/unreal-uxt/2-boardmat.PNG)

在继续之前，请确保材质设置看起来类似于以上屏幕截图。

## <a name="populating-the-scene"></a>填充场景
如果返回到“棋盘”蓝图，将会看到已应用刚创建的材质。 只需设置场景即可！ 首先，更改以下属性，以确保在场景中放置棋盘时，它的大小和角度正确：
1.  将“比例”设置为“(0.05, 0.05, 0.05)”并将“Z 旋转”设置为“90”   。 
    * 单击顶部工具栏中的“编译”，然后单击“保存”并返回到主窗口。 

![已应用材质的棋盘](images/unreal-uxt/2-chessboard.PNG)

2.  右键单击“立方体”>“编辑”>“删除”并将“棋盘”从“内容浏览器”拖至视口中  。 
    * 将“位置”设置为“X = 80”、“Y = 0”和“Z = -20”   。 

3.  单击“开始”按钮，查看你所处关卡中的新棋盘。 按 Esc 返回到编辑器。 

现在，你将按照与棋盘相同的步骤创建棋子：

1. 转到“蓝图”文件夹，右键单击并选择“蓝图类”，然后选择“Actor”  。 将 Actor 命名为“WhiteKing”。

2. 双击“WhiteKing”以在蓝图编辑器中将其打开，单击“添加组件”>“场景”，并将其命名为“Root”  。 
    * 将“Root”拖放到 DefaultSceneRoot 中来替换它 。 

3. 单击“添加组件”>“静态网格”，并将其命名为“SM_King” 。 
    * 在“详细信息”面板中，将“静态网格”设置为“Chess_King”，并将“材质”设置为名为“M_ChessWhite”的新材质。 

4. 在材质编辑器中打开“M_ChessWhite”，并将以下“纹理示例”节点连接到以下各项：
    * 将“纹理”设置为“ChessWhite_AO”，将“RGB”链接到“环境遮蔽”引脚   。
    * 将“纹理”设置为“ChessWhite_Metal”，将“RGB”链接到“金属”引脚   。 
    * 将“纹理”设置为“ChessWhite_Normal”，将“RGB”链接到“正常”引脚   。
    * 将“纹理”设置为“ChessWhite_Rough”，将“RGB”链接到“粗糙度”引脚   。 
    * 单击 **“保存”** 。 

在继续之前，“M_ChessKing”材质应与下图类似。

![为国王（棋子）创建材质](images/unreal-uxt/2-chesskingmat.PNG)

即将完成，只需将新棋子添加到场景中即可： 

1. 打开“WhiteKing”蓝图，并将“比例”更改为“(0.05, 0.05, 0.05)”，将“Z 旋转”更改为“90”。
    * 编译并保存蓝图，然后返回到主窗口。 

2.  将“WhiteKing”拖到视口中，切换到“世界大纲视图”面板，将“WhiteKing”拖到“棋盘”上，使其成为子对象。

![世界大纲视图](images/unreal-uxt/2-child.PNG)

3.  在“详细信息”面板中的“变形”下，将 WhiteKing 的“位置”设置为“X = -26”、“Y = 4”、“Z = 0”      。

完成！ 单击“开始”以查看正在运行中的已填充关卡，并在准备好退出时按 Esc。 本教程介绍了很多创建简单项目的背景，但你的项目已准备好继续进行本系列的下一部分：设置混合现实。 

[下一节：3.设置混合现实项目](unreal-uxt-ch3.md)