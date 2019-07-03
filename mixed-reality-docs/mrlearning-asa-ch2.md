---
title: MR 学习 ASA 模块 Azure HoloLens 2 上的空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: f8a52660fe05b6ed4508321ed246b8e299b75bca
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523332"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2.保存、 检索和共享 Azure 空间的定位点

在本教程中，我们将了解如何在多个应用程序会话之间保存我们 Azure 空间的定位点，通过将我们定位点的信息保存到 HoloLens 2 的磁盘。 我们还将了解如何共享此定位点的信息对其他设备的多设备定位点对齐方式。

## <a name="objectives"></a>目标

* 了解如何保存和检索 Azure 空间的定位点信息从 HoloLens 2 本地磁盘，以便进行应用程序会话之间保留

* 了解如何在 Azure 空间的定位点之间共享信息的多设备方案中的用户

  

## <a name="instructions"></a>说明

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>保留应用程序会话的保存到磁盘的锚点 ID 之间的 Azure 定位点

1. 搜索并将 SaveAnchorToDisk 预设可添加到您的场景。 其中包括两个按钮、 一个按钮用于将任何可用的 Azure 定位标记 Id 保存到 HoloLens 2 磁盘，另一个用于从磁盘检索任何 Id。

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. 配置下面的说明根据每个按钮
   - 对于名为 SaveToDisk 按钮，创建新的事件下按下按钮事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 SaveAzureAnchorIDToDisk() 方法。
   
     > 注意： 某些按钮可能会出现重叠的场景中的其他按钮。 随意调整按钮的位置。
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - 对于名为 GetFromDisk 按钮，创建新的事件下按下按钮事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 LoadAzureAnchorIDsFromDisk() 方法。

3. 从 Tutoiral 1 以构建到你的设备更新的应用程序按照的说明。 按创建 Azure 定位点按钮之后, 就像在上一课中现在可以保存 Azure 锚点 ID 到磁盘按保存到磁盘按钮。

4. 重新启动该应用程序，启动 Azure 会话，按负载锚点 ID，然后按找到 Azure 定位点定位与我们保存到磁盘的 ID 相关联的定位点。 在整个场景现在应对齐到位，在位置定位点以前保存 ！

### <a name="share-azure-anchors-between-multiple-devices"></a>在多个设备之间共享 Azure 的定位点

在本部分中，我们将了解如何共享多个设备之间的 Azure 锚点 ID。 这将允许多个设备查询相同的锚点 ID，Azure 允许我们锚定的全息和场景论据在空间上对齐。 空间对齐方式 （请参阅在多个设备之间的相同物理位置相同的全息） 是 HoloLens 2 中的密钥到本地共享的体验。 有很多种传输设备，包括方法之间的相关 azure Id 中 Azure 空间的定位点的共享体验教程所述的信息 (TODO： 添加链接。)此示例使用简单的 web 服务上传和下载设备之间的定位标记 Id。

1. 将添加到你的层次结构 ShareAnchor 预设。 此预设可将两个新按钮添加到您的场景;一个用于上传锚点 ID 信息，另一个用于下载的定位点 ID 信息。 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. 配置下面的说明根据每个按钮

   - 对于名为 SendSharedAnchor，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 ShareAnchor() 方法。

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - 对于名为 GetSharedAnchor，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 GetSharedAzureAnchor() 方法。

3. 请按照中的说明[教程 1](mrlearning-base-ch1.md)。 若要构建到你的设备更新的应用程序。 按创建 Azure 定位点按钮之后, 就像在上一课中现在，您可能会共享 Azure 锚点 ID 与其他设备通过按共享到其他设备按钮。

   > 注意：选择父定位点和向下的滚动至父定位点脚本。 请确保公共共享 pin 是唯一的以便共享时，您知道它是你要共享。 可能有数千个用户共享其 Azure 的定位点，以便执行此操作将允许您以确保您要共享的正确 Azure 定位点。

4. 如果你有其他 HoloLens 2 设备，启动该应用程序，然后启动 Azure 会话。 按获取共享的锚点 ID 按钮，然后按找到 Azure 定位点按钮以找到与我们保存到磁盘的 ID 相关联的定位点。 在整个场景现在应对齐到位，放置在另一 HoloLens 2 台设备上查看 where ！ 如果你只有一个 HoloLens 2，您可能仍测试功能通过重新启动该应用程序，启动 Azure 会话，然后按"获取共享的锚点 ID"按钮，然后按找到 Azure 定位点按钮以找到定位点与相关联我们将保存到磁盘的 ID。 在整个场景现在应对齐到位，在位置定位点以前保存 ！

## <a name="congratulations"></a>祝贺
本课程中您学习了如何通过将 Azure 空间锚点 ID 保存到本地磁盘，在 HoloLens 2 上应用程序重新启动应用程序会话之间保留 Azure 空间的定位点。 您还学习了如何为用户提供基本的多用户、 静态全息图共享体验的多个设备之间共享 Azure 空间的定位点。

我们了解如何实现 Azure 空间的定位点在最后一课中的共享模块的完全交互式的本地共享体验的一部分。 本地共享体验可能包括功能，例如为每个用户已同步的三维对象位置、 旋转和缩放、 标识符和共享应用程序状态。 Azure 空间的定位点的每个参与者提供常见的定位点，可让所有用户看到的相同物理位置中的虚拟对象，从而增强了这些共享的方案。 这适用于一系列的设备平台，包括 HoloLens、 Android 和 iOS 设备。 若要了解如何开发共享的体验，完成共享模块中的所有课程。

在下一课中，我们将了解如何向用户提供实时反馈。 此反馈将包括有关定位点创建、 环境了解质量和 Azure 的会话的状态信息。 而无需反馈，用户可能不知道是否定位点已成功上的传到 Azure，环境的质量是否足以满足定位点创建过程中或当前状态。

[下一课：ASA 教程 3](mrlearning-asa-ch3.md)

