---
title: 多用户功能教程-5。 将 Azure 空间锚点集成到共享体验中
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: cb4645d197238d8712719625bf11eac0650a8246
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701871"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5.将 Azure 空间锚点集成到共享体验中

在本课程中, 我们将了解如何将 Azure 空间锚点 (ASA) 集成到我们的共享体验中。 如果其物理环境要锚定虚拟体验, 使多个归置的设备在其物理环境中能够看到相同的物理位置中的对象, 则可以使用这些设备。

在继续学习本课程之前, 我们需要完成 ASA 学习模块, 该模块将涵盖 ASA 基础知识、Azure 帐户和资源创建, 以及在我们可以将 ASA 集成到我们的共享体验之前所需的其他基本建筑物块。

目标

- 将 ASA 集成到多设备对齐的共享体验。
- 了解 ASA 在本地共享体验环境中的工作原理的基础知识。

### <a name="instructions"></a>说明

1. 保存上一课中的项目 (ctrl + S) 并将其命名为 "HLSharedProjectMainPart5", 以便在再次需要时更轻松地找到它。

2. 选择 MixedRealityPlayspace 父对象下的 TableAnchor prefab, 并将其删除。

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  在 "项目" 视图中, 中转到 "资产-> 资源-> Prototyping", 然后将 TableAnchor prefab 拖到 SharedPlayground 对象的顶部, 使其成为子对象。
4.  展开 MixedRealityPlayspace 父对象 TableAnchor 对象, 并同时展开 "按钮" 对象。 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 现在, 在层次结构中, 选择 "ShareAzureAnchorButton", 并将你的注意力转到 "Inaspector" 面板。 向下滚动到下图所示的下拉菜单中, 选择 "AnchorModuleScript", 然后单击 "ShareAnchorNetework" ()。

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. 选择 GetAzureAnchorButton (请参阅步骤 4), 并将你的注意力移回到检查器面板。 向下滚动到下图所示的下拉菜单中, 选择 "AnchorModuleScript", 并单击 "GetSharedAnchorNetwork" (), 然后单击 "保存"。

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. 若要测试共享模块, 请单击 "启动 azure ASA 会话" 按钮, 该按钮将启动 azure 空间锚点会话, 然后通过单击 "创建 Azure 锚点" 按钮创建 azure 定位点, 并等待 azure 锚点创建完成。 创建 azure 定位点后, 请单击 "共享 Azure 定位点" 按钮, 从 HoloLens 共享创建的 azure 定位点。

7. 若要在另一个 HoloLens 中接收共享的 azure 定位点, 请单击 "启动 Azure ASA 会话" 以启动并进入当前 ASA 会话, 然后单击 "获取 Azure 锚点" 按钮, 从另一个 HoloLens 获取共享的 azure 定位点。

   > 注意:各个按钮上对应操作的所有详细信息都将显示在调试窗口中。

## <a name="congratulations"></a>祝贺

在本课程中, 你学习了如何集成 Azure 强大的新空间锚点, 以便在共享体验中协调归置设备! 本课还将结束共享模块。 我们学习了如何设置新的 Photon 帐户, 将 Photon 和双关语集成到新的 Unity 应用程序中, 配置头像和 shared 对象, 并最终使用 ASA 协调多个参与者。 

