---
title: Azure 空间锚点教程-3。 显示 Azure 空间锚点反馈
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438413"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. 显示 Azure 空间锚点反馈

在本课程中，你将了解如何在使用 Azure 空间锚点时向用户提供有关定位点发现、事件和状态的反馈。

## <a name="objectives"></a>目标

* 了解如何设置显示当前 ASA 会话重要信息的 UI 面板

* 了解并探索 ASA SDK 向用户提供的反馈元素

## <a name="instructions"></a>说明

### <a name="set-up-asa-feedback-ui-panel"></a>设置 ASA 反馈 UI 面板

1. 在本课中，我们未使用 "SaveAnchorToDisk" 和 "ShareAnchor" 按钮，因此，请选择两个按钮，并取消选中 "检查器" 面板中的复选框（如下所示）以隐藏这些按钮。
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 创建指令面板。 首先右键单击 "说明" 按钮，将鼠标悬停在 "3D 对象" 上，然后选择 "textmeshpro"。

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. 调整文本的规模和位置，使其与场景中的说明相匹配。 此外，请确保所有文本的对齐方式都居中。 然后从文本编辑器中删除示例文本，如下图中所示。

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. 将 TextMeshPro 对象的名称更改为 "FeedbackPanel"。
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. 在 "项目" 面板中，选择 "资产" 并右键单击，然后选择 "在资源管理器中显示"。
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

单击[此处](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)下载接下来的几个步骤中所需的文件。

6. 资源管理器打开后，选择 "资产" 文件夹，然后选择 "ASAmodulesAssets" 文件夹，并将定位点反馈脚本和定位点模块脚本文件复制到该文件夹中。 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> 注意：如果您收到一条弹出消息，询问您是覆盖旧的还是保留旧的，请选择 "覆盖"。

7. 返回到 "资产" 文件夹。 然后，进入 "AzureSpatialAnchorsPlugin" 文件夹，后跟示例文件夹和脚本文件夹。 然后将 Azure 空间锚定包装器复制到该文件夹中。 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. 现在已上传文件，请确保在 ASA_feedback 层次结构中选择了 "feedbackpanel" 文本，单击 "添加组件"，并通过搜索和选择定位反馈脚本来添加它。 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. 将 "feedbackPanel" 文本对象从 ASA_Feedback 层次结构拖动到脚本下的空槽中，如下图所示。 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>祝贺

在本课程中，我们学习了如何创建 UI 面板来显示 Azure 空间锚体验的当前状态，以便为用户提供实时反馈。


