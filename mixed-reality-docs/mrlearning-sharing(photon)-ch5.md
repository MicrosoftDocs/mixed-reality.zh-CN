---
title: 多用户功能教程 - 5. 将 Azure 空间定位点集成到共享体验中
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031695"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5.将 Azure 空间定位点集成到共享体验中

本课程介绍如何将 Azure 空间定位点 (ASA) 集成到共享体验中。 如果共置在一起的多个设备的物理环境会锚定虚拟体验，使所有参与者在同一个物理位置看到对象，则 ASA 可让这些设备获得一个公用参照点。

## <a name="objectives"></a>目标

* 将 ASA 集成到共享体验，以在多个设备上实现对齐。
* 了解 ASA 在本地共享体验上下文中的基本工作原理。

## <a name="instructions"></a>说明

1. 选择“MixedRealityPlayspace”父对象下的“TableAnchor”预制件，并将其删除。

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. 在“项目”视图中转到“资产”->“资源”->“预制件”，将“TableAnchor”预制件拖放到“SharedPlayground”对象的顶部，使该预制件成为子级。

3. 展开“MixedRealityPlayspace”父对象、“TableAnchor”对象和“Buttons”对象。

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 现在，请在层次结构中选择“ShareAzureAnchorButton”，并将注意力转移到“检查器”面板。 向下滚动到下图所示的下拉菜单中，选择“AnchorModuleScript”，然后单击“ShareAnchorNetwork()”。

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. 选择“GetAzureAnchorButton”（参阅步骤 4），并将注意力重新转移到“检查器”面板。 向下滚动到下图所示的下拉菜单，选择“AnchorModuleScript”，单击“GetSharedAnchorNetwork()”，然后保存。

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. 重复步骤 4，将 StartAzureSession () 函数挂接到 StartAzureSessionButton。

7. 重复步骤 4，将 CreateAzureAnchor () 函数挂接到 CreateAzureAnchorButton，并确认 TableAnchor 对象是否已分配到该函数的“游戏对象”参数字段。

8. 按照[将场景连接到 Azure 资源](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource)中的说明添加 Azure 空间定位点服务凭据。

9. 若要测试共享模块，请单击“启动 Azure ASA 会话”按钮启动 Azure 空间定位点会话，然后单击“创建 Azure 定位点”按钮创建 Azure 定位点。 等待 Azure 定位点创建完成。 创建 Azure 定位点后，单击“共享 Azure 定位点”按钮从 HoloLens 共享创建的 Azure 定位点。

10. 若要在另一个 HoloLens 中接收共享的 Azure 定位点，请单击“启动 Azure ASA 会话”以启动并进入当前的 ASA 会话

11. 单击“获取 Azure 定位点”按钮以从另一个 HoloLens 获取共享的 Azure 定位点。

## <a name="congratulations"></a>祝贺

在本课程中，你已了解如何集成 Azure 中强大的新空间定位点功能，以在共享体验中对齐共置的设备！ 共享模块教程也到此结束。 我们已学会了如何设置新的 Photon 帐户、将 Photon 和 PUN 集成到新的 Unity 应用程序中、配置头像和共享的对象，并最终使用 ASA 来对齐多个参与者。
