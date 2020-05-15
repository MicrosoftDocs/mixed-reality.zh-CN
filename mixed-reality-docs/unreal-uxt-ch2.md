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
# <a name="2-initializing-your-project-and-first-application"></a>2.初始化你的项目和第一个应用程序

本部分介绍如何针对 HoloLens 2 创建新的 Unreal 应用程序。 

## <a name="objectives"></a>目标

* 为 Hololens 开发配置 Unreal
* 导入资产并设置场景

## <a name="create-a-new-unreal-project"></a>创建新的 Unreal 项目

1. 启动 Unreal Engine

2. 在“新项目类别”  下，选择“游戏”  ，然后单击“下一步”。 选择“空白”  模板，然后单击“下一步”。 

![选择“空白”模板](images/unreal-uxt/2-template.PNG)

3. 在“项目设置”中，选择“C++、可缩放的 3D 或 2D、移动/平板电脑”  ，并选择“非初学者内容”  。 选择项目的保存位置，然后单击“创建项目”  。 这会在 Visual Studio 项目和 Unreal 编辑器中打开 C++ 文件。 

![初始项目设置](images/unreal-uxt/2-project-settings.PNG)

4. 在左上角，转到“编辑”>“插件”  。 在“增强现实”下，选中相应的复选框以启用“HoloLens”  插件。 向下滚动到“虚拟现实”部分，并选中复选框以启用“Microsoft Windows 混合现实”  插件。 这两个插件都是 HoloLens 2 开发所必需的。 重新启动编辑器。 

![插件](images/unreal-uxt/2-plugins.PNG)

5. 在左上角，转到“文件”>“新关卡”  。 选择“空关卡”  。 视口中的默认场景现在应为空。

6. 从左侧的“模式”面板（位于“基本”选项卡中）拖放 PlayerStart。在右侧的“详细信息”面板中，将位置设置为 X = 0、Y = 0、Z = 0，以使用户在应用启动时从原点开始。

![具有 PlayerStart 的视口](images/unreal-uxt/2-playerstart.PNG)

7. 将一个“立方体”  从“模式”面板的“基本”选项卡拖到视口中。 在“详细信息”面板中，将位置设置为 X = 50，Y = 0，Z = 0，以在开始时将立方体设置为距离玩家 50 cm。 由于默认立方体相当大，因此请将立方体的“比例”更改为 (0.2, 0.2, 0.2)。 

8. 除非向场景添加光源，否则看不到立方体。 切换到“模式”面板上的“光源”  选项卡，然后将“定向光源”  拖到场景的 PlayerStart 上方。

![添加了光源的视口](images/unreal-uxt/2-light.PNG)

9.  按工具栏上的“开始”  按钮，在视口中查看立方体！ 按 Esc  停止关卡。 

![视口中的立方体](images/unreal-uxt/2-cube.PNG)

10. 保存关卡。 在左上角，单击“文件”>“保存当前关卡”  。 将关卡命名为“主关卡”，然后单击“保存”  。 

## <a name="set-up-a-chess-scene"></a>设置象棋场景

1. 在“内容浏览器”中，单击“新增”下的图标以显示源面板。 然后单击“新增”>“新文件夹”  并将文件夹命名为“ChessAssets”。 双击此文件夹以在其中导航。 我们将在此处导入棋具的 3D 资产。

![显示或隐藏源面板](images/unreal-uxt/2-showhidesources.PNG)

2. 从 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 下载资产的 zip 文件。 此文件包含棋盘和棋具的 3D 模型。 解压缩此文件。

3. 在“内容浏览器”的顶部，单击“导入”  。 导航到刚解压缩的文件夹，并选择其中的所有项。 此文件夹包含 FBX 文件，这些文件是棋盘和棋子的 3D 对象网格，还包含 TGA 文件，我们将使用这些纹理映射来创建棋盘和棋子的材质。 单击“打开”  。 

4. 将弹出一个“FBX 导入选项”窗口。 在“材质”  部分，将“材质导入方法”  更改为“不创建材质”  。 然后，单击“全部导入”  。

![导入 FBX 选项](images/unreal-uxt/2-nocreatemat.PNG)

5. 返回“内容”文件夹，创建名为“蓝图”  的新文件夹。 我们将在这里存储所有蓝图，这些蓝图为特殊资产，它们提供基于节点的接口来创建新类型的 Actor 和脚本级别事件。 

6. 双击“蓝图”  文件夹以导航到内部，然后右键单击“内容浏览器”，并选择“蓝图类”  。 单击“Actor”  并将新蓝图命名为“棋盘”。 双击“棋盘”将其打开。 

![选择蓝图的父类](images/unreal-uxt/2-bpparent.PNG)

![新棋盘蓝图](images/unreal-uxt/2-bpboard.PNG)

7. 在蓝图编辑器中，导航到“组件”面板，然后单击“添加组件”>“场景”  。 将新创建的场景命名为“Root”，然后在 DefaultSceneRoot 上单击并拖动 Root。 这将替换默认的场景 Root，并在视口中消除球面。 

![替换 Root](images/unreal-uxt/2-root.PNG)

8. 再次单击“添加组件”  ，这一次请选择“静态网格”  。 将新的静态网格命名为“SM_Board”。 

![添加静态网格](images/unreal-uxt/2-sm-board.PNG)

9. 在“详细信息”  面板中，找到“静态网格”  部分，然后单击下拉列表。 选择“棋盘”  。 

![视口中的棋盘网格](images/unreal-uxt/2-sm-board-view.PNG)

10. 同样在“详细信息”  面板中，找到“材质”  部分，然后单击下拉列表。 在“创建新资产”  下，选择“材质”  。 将此资产命名“M_ChessBoard”  ，并将其保存在“ChessAssets”  文件夹中。 

![创建新材质](images/unreal-uxt/2-newmat.PNG)

11. 双击“M_ChessBoard”下拉列表旁的方块，打开新创建的 M_ChessBoard 材质。 在“材质编辑器”中，单击右键并搜索“纹理示例”  节点。 在“详细信息”  面板中的“材质表现纹理库”  部分下，单击下拉列表并选择“ChessBoard_Albedo”  。 最后，将“RGB”  输出引脚拖至“M_ChessBoard”  的“基准颜色”引脚上。 

![设置基准颜色](images/unreal-uxt/2-boardalbedomat.PNG)

12. 重复同样的操作四次，将“ChessBoard_AO”  纹理示例链接到“环境遮蔽”  引脚，将“ChessBoard_Metal”  纹理示例链接到“金属”  引脚，将“ChessBoard_Normal”  纹理示例链接到“正常”  引脚，并将“ChessBoard_Rough”  纹理示例链接到“粗糙度”  引脚。 单击 **“保存”** 。 

![连接剩余纹理](images/unreal-uxt/2-boardmat.PNG)

13. 返回到“棋盘”  蓝图。 应会看到刚创建的材质已应用于蓝图。 将棋盘置于场景后，若要确保棋盘的大小和位置，请将棋盘的“比例”  更改为 (0.05, 0.05, 0.05)，将“旋转”  更改为 Z = 90。 在顶部工具栏中，单击“编译”  ，然后单击“保存”  。 返回到主窗口。 

![已应用材质的棋盘](images/unreal-uxt/2-chessboard.PNG)

14. 现在删除立方体，并将其替换为新创建的棋盘 Actor。 在“世界大纲视图”  中，右键单击“立方体”>“编辑”>“删除”  。 将棋盘从“内容浏览器”拖到视口。 将棋盘位置设置为 X = 80，Y = 0，Z =-20。 

15. 单击“开始”  按钮，查看你所处关卡中的新棋盘。 按 Esc  返回到编辑器。 

16. 接下来，我们将按照与对棋盘所执行的相同步骤创建棋子，这次选择棋子的网格和材质：

    a) 在“内容浏览器”中导航到“蓝图”文件夹，然后创建一个 Actor 类型的新蓝图类。 将此 Actor 命名为“WhiteKing”。

    b) 双击“WhiteKing”将其打开。 添加一个名为“Root”的新场景组件，并使用它来替换 DefaultSceneRoot。 

    c) 添加一个名为“SM_King”的新静态网格组件。 在“详细信息”面板中，将“静态网格”  设置为“Chess_King”  ，并将“材质”  设置为名为“M_ChessWhite”  的新材质。 

    d) 打开新“M_ChessWhite”  材质，并将相关纹理连接到相应的材质输入。 

    ![为国王（棋子）创建材质](images/unreal-uxt/2-chesskingmat.PNG)

    e) 返回到“WhiteKing”  蓝图，将“比例”  更改为 (0.05, 0.05, 0.05)，将“旋转”  更改为 Z = 90。

    f) 编译并保存蓝图，然后导航回主窗口。 

17. 将“WhiteKing”拖动到视口中。 在“世界大纲视图”  中，将“WhiteKing”拖到棋盘，以便 WhiteKing 成为棋盘的子元素。 

![世界大纲视图](images/unreal-uxt/2-child.PNG)

18. 在“详细信息”  面板下的“变形”  部分，将 WhiteKing 的“位置”  设置为 X =-26，Y = 4，Z = 0

19. 单击“开始”  查看关卡。 按 Esc  退出。 

[下一节：3.设置混合现实项目](unreal-uxt-ch3.md)