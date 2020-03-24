---
title: 多用户功能教程 - 4. 与多个用户共享对象运动
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031250"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4.与多个用户共享对象运动

本教程介绍如何共享对象的运动，使共享会话的所有参与者可以展开协作并查看彼此的交互。 本课程基于[基础模块教程](mrlearning-base.md)中生成的月球探测器发射器。

## <a name="objectives"></a>目标

- 以 3D 模型的形式引入要共享的月球探测器发射器
- 将项目配置为共享 3D 模型的运动
- 了解如何生成基本的多用户协作应用程序

## <a name="instructions"></a>说明

1. 保存上一课程中创建的场景 (Ctrl+S)。 可将其命名为 HLSharedProjectMainPart4.unity，以便在需要时轻松找到它。

2. 在“项目”窗口中，双击“资产”->“脚本”文件夹中的“GenericNetSync”，在 Visual Studio 或所用的其他代码编辑器中将其打开。  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. 在第 34 和 38 行中，删除“//”以激活要在本课程中使用的工作台的代码。 接下来保存该文件。

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. 在“项目”窗口中，双击“资产”>“脚本”文件夹中的“PhotonRoom.cs”文件，在 Visual Studio 中将其打开。

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. 与在步骤 3 中一样，需要删除“//”以激活第 25、26 和 106 行中的代码。

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. 在“层次结构”视图中选择“NetworkRoom”对象。

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. 在“项目”视图中，导航到“资产”->“资源”->“预制件”。 首先，将 Table 预制件拖放到 PhotonRoom 类中的 Tableprefab 槽。 接下来，将 RocketLauncherCompleteVariantprefab 拖放到 PhotonRoom 类中的 Module Prefab 槽。

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >如果单击某个预制件对象并松开鼠标，检查器将切换到该对象。 单击每个对象并将其拖放到相应的槽，然后松开鼠标。

8. 单击 MixedRealityPlayspace 左侧的箭头，并将子游戏对象 MainCamera 下移到 SharedPlayground 预制件。 接下来，选择 MixedRealityPlayspace 预制件，然后按 Delete 键将其删除。

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >确保主相机和 SharedPlayground 位置均设置为 0,0,0。

9. 选择“SharedPlayground”对象，然后单击鼠标右键并选择“创建空对象”选项，以创建一个空游戏对象作为“SharedPlayground”游戏对象的子级。

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. 在层次结构中选择该新对象后，在“检查器”面板中将该对象的名称更改为 TableAnchor。 另外，单击“添加组件”并搜索 TableAnchor 组件。 选择该组件并将其添加到对象。

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. 在“项目”面板中的“预制件”文件夹内，将 Table 预制件拖放到刚刚创建的“TableAnchor”子对象中。

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a>祝贺

完成此过程后，找到登月舱。 此时，参与 Unity 项目的所有用户都可以四处移动月球探测器发射器。  所有运动都是同步的，因此每个用户都可以看到彼此的交互。 这些概念是全功能共享协作体验的构建基块。

尽管所有用户已作为共享体验的一部分进行连接，并且可以看到对象的相对运动，但应用程序仍然无法准确对齐头像和对象，因此本地用户无法在现实世界中的同一位置看到彼此和对象。 若要定位点定本地共享体验，每个设备都需要对物理环境有一个共识。 在本模块中，我们将使用下一课程中要实现的 [Azure 空间定位点](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) 来达到这种共识。

在继续学习下一课程之前，需要先完成 ASA 学习模块，其中介绍了 ASA 基础知识、Azure 帐户和资源的创建，以及在可将此模块集成到共享体验之前所需的其他构建基块。

[下一课：5.将 Azure 空间定位点集成到共享体验中](mrlearning-sharing(photon)-ch5.md)
