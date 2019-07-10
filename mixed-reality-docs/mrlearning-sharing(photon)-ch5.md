---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465205"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure 空间的定位点和分享的经验

在本课中，我们将了解如何将 Azure 空间的定位点 (ASA) 集成到我们的共享体验。 ASA 允许多个共置的设备具有常见的引用，如果其物理环境到定位点虚拟体验，以便所有参与者都看到同一个物理位置中的对象。

在继续之前本课程中，我们将需要完成 ASA 学习模块，将介绍 ASA 基础知识、 Azure 帐户和资源创建和其他基本建筑物块之前我们可以将 ASA 集成到我们的共享体验所需的。

目标：

- 将 ASA 集成到多设备对齐方式的共享体验
- 了解 ASA 本地共享体验的上下文中的工作原理的基础知识

### <a name="instructions"></a>说明

1. 从上一课 （控制 + S） 保存项目并将其命名"HLSharedProjectMainPart5.unity"以便更轻松地查找当你再次需要。

2. 选择 TableAnchor 预设可下方 MixedRealityPlayspace 父对象，并将其删除。

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  在项目视图转到资产-> 资源-> 预设，并将其拖之上 SharedPlayground 对象以使其成为子 TableAnchor 预设。
4.  展开 MixedRealityPlayspace 父对象、 TableAnchor 对象，并展开按钮对象。 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 现在在层次结构中，选择 ShareAzureAnchorButton，并移动到 Inaspector 面板关注。 向下滚动到，如下图所示的下拉列表菜单并选择 AnchorModuleScript 单击 ShareAnchorNetework()。

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. 选择 GetAzureAnchorButton （请参阅步骤 4），并将移回检查器面板关注。 向下滚动到，如下图所示的下拉列表菜单并选择 AnchorModuleScript，并单击 GetSharedAnchorNetwork()，并保存。

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>祝贺

本课程中您学习了如何将集成 Azure 的功能强大的新空间定位标记对齐归置的设备中的共享体验 ！ 本课程还得出结论共享模块。 配置虚拟形象和共享的对象，并最后对齐多个参与者使用 ASA，我们了解到如何设置新的 Photon 帐户，请将 Photon 和俏皮话集成到新的 Unity 应用程序。 
