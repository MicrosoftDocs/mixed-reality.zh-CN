---
title: 在 HoloLens 2 上学习 ASA 模块 Azure 空间锚的 MR
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b263d30905c5a1ba81bfb59ba6a49c7710c43869
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485745"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2.保存、检索和共享 Azure 空间锚

在本教程中, 我们将了解如何通过将定位信息保存到 HoloLens 2 的磁盘来跨多个应用会话保存 Azure 空间锚。 我们还将了解如何将此定位点信息共享到其他设备, 以实现多设备锚点对齐。

## <a name="objectives"></a>目标

* 了解如何保存和检索 HoloLens 2 本地磁盘中的 Azure 空间锚定信息, 以便在应用会话之间保持持久性

* 了解如何在多设备方案中的用户之间共享 Azure 空间锚点信息

## <a name="instructions"></a>说明

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>在应用会话之间保留 Azure 锚点-将定位点 ID 保存到磁盘

1. 搜索并将 SaveAnchorToDisk prefab 添加到场景中。 其中包括两个按钮, 一个按钮用于将所有可用的 Azure 定位 Id 保存到 HoloLens 2 磁盘, 另一个用于从磁盘检索任何 Id。

![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. 根据下面的说明配置每个按钮

   - 对于名为 SaveToDisk 的按钮, 在 "按下" 事件触发器和 On Click 事件触发器下创建一个新事件。 将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 SaveAzureAnchorIDToDisk () 方法。
   
     > 注意: 某些按钮可能会与场景中的其他按钮重叠。 随意调整按钮的定位。

![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)


   - 对于名为 GetFromDisk 的按钮, 在 "按下" 事件触发器和 On Click 事件触发器下创建一个新事件。 将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 LoadAzureAnchorIDsFromDisk () 方法。

3. 按照 Tutoiral 1 中的说明, 将更新后的应用程序生成到你的设备。 按下一课所述, 按 "创建 Azure 锚点" 按钮后, 现在可以通过按 "保存到磁盘" 按钮将 Azure 定位 ID 保存到磁盘。

4. 重新启动应用程序, 启动 Azure 会话, 按 "加载定位点 ID", 然后按 "查找 Azure 定位点", 找到与我们保存到磁盘的 ID 相关联的定位点。 整个场景现在应在您之前保存锚点的位置上对齐!

### <a name="share-azure-anchors-between-multiple-devices"></a>在多个设备之间共享 Azure 锚

在本部分中, 我们将了解如何在多个设备之间共享 Azure 锚 ID。 这将允许多个设备在 Azure 中查询相同的定位 ID, 以允许我们的定位全息影像和场景进行立体调整。 空间对齐 (在多个设备之间的同一物理位置查看相同的全息影像) 是 HoloLens 2 中的本地共享体验的关键所在。 可以通过多种方式在设备之间传输有关 azure Id 的信息, 包括 Azure 空间锚式共享体验教程中所述的方法 (TODO: 添加链接。)此示例使用简单的 web 服务在设备之间上传和下载定位点 Id。

1. 将 ShareAnchor prefab 添加到层次结构中。 此 prefab 将两个新按钮添加到场景中;一个用于上载定位点 ID 信息, 另一个用于下载定位点 ID 信息。 

![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. 根据下面的说明配置每个按钮

   - 对于名为 "SendSharedAnchor" 的按钮, 请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。 将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 ShareAnchor () 方法。

![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

   - 对于名为 "GetSharedAnchor" 的按钮, 请在 "按下" 事件触发器和 On Click 事件触发器下创建新事件。 将 ParentAnchor 对象拖到空字段, 然后从 ParentAnchor 对象的 ASAmoduleScript 组件分配 GetSharedAzureAnchor () 方法。

3. 按照[教程 1](mrlearning-base-ch1.md)中的说明进行操作。 将更新后的应用程序生成到你的设备。 按下一课中所述, 按 "创建 Azure 锚点" 按钮后, 现在可以通过按 "共享到其他设备" 按钮将 Azure 锚 ID 共享到其他设备。

   > 注意:选择父定位点并向下滚动到父定位点脚本。 确保你的公共共享 pin 是唯一的, 因此, 当你共享它时, 你知道自己正在共享。 可能有成千上万用户共享其 Azure 定位点, 因此这样做可以确保共享正确的 Azure 锚。

4. 如果有另一个 HoloLens 2 设备, 则启动该应用程序, 然后启动 Azure 会话。 按 "获取共享定位点 ID" 按钮, 然后按 "查找 Azure 定位点" 按钮, 找到与我们保存到磁盘的 ID 相关联的定位点。 整个场景现在应在其放置在另一个 HoloLens 2 设备上的位置对齐! 如果只有一个 HoloLens 2, 则仍可通过以下方式测试功能: 重新启动应用程序、启动 Azure 会话, 然后按 "获取共享定位点 ID" 按钮, 然后按 "查找 Azure 定位点" 按钮以找到与已保存到磁盘的 ID。 整个场景现在应在您之前保存锚点的位置上对齐!

## <a name="congratulations"></a>祝贺
在本课程中, 你学习了如何通过将 Azure 空间锚定 ID 保存到 HoloLens 2 上的本地磁盘, 在应用程序会话和应用程序重启之间保持 Azure 空间锚。 还了解了如何在多个设备之间共享 Azure 空间锚, 以实现基本的多用户静态全息图共享体验。

本文介绍如何在共享模块的最后一课中, 将 Azure 空间锚点作为完全交互式本地共享体验的一部分实现。 本地共享体验可能包括同步的3D 对象位置、旋转和缩放、每个用户的标识符以及共享应用程序状态等功能。 Azure 空间锚点为每个参与者提供一个公共锚, 使所有用户都能看到同一物理位置中的虚拟对象, 从而增强了这些共享方案。 这适用于各种设备平台, 包括 HoloLens、Android 和 iOS 设备。 若要了解如何开发共享体验, 请完成共享模块中的所有课程。

在下一课中, 我们将学习如何向用户提供实时反馈。 此反馈将包括有关定位点创建、环境理解质量以及 Azure 会话状态的信息。 如果没有反馈, 用户可能不知道某个定位点是否已成功上传到 Azure, 无论该环境的质量是否足以用于创建定位点或当前状态。

[下一课：3.显示 Azure 空间定位点反馈](mrlearning-asa-ch3.md)

