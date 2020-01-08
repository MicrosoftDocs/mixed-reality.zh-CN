---
title: Azure 空间锚点教程-3。 显示 Azure 空间锚点反馈
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 19529cbfebd74938395545c329097d42b5af9ff9
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334401"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. 显示 Azure 空间锚点反馈

在本课程中，你将了解如何在使用 Azure 空间锚点时向用户提供有关定位点发现、事件和状态的反馈。

## <a name="objectives"></a>目标

* 了解如何设置显示当前 ASA 会话重要信息的 UI 面板

* 了解并探索 ASA SDK 向用户提供的反馈元素

## <a name="set-up-asa-feedback-ui-panel"></a>设置 ASA 反馈 UI 面板

1. 在本课中，我们未使用 "SaveAnchorToDisk" 和 "ShareAnchor" 按钮，因此，请选择两个按钮，并取消选中 "检查器" 面板中的复选框（如下所示）以隐藏这些按钮。

    ![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 创建指令面板。 首先右键单击 "说明" 按钮，将鼠标悬停在 "3D 对象" 上，然后选择 "textmeshpro"。

    ![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. 调整文本的规模和位置，使其与场景中的说明相匹配。 此外，请确保所有文本的对齐方式都居中。 然后从文本编辑器中删除示例文本，如下图中所示。

    ![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. 将 TextMeshPro 对象的名称更改为 "FeedbackPanel"。

    ![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. 确保在 ASA_feedback 层次结构中选择 "feedbackpanel" 文本，单击 "添加组件"，并通过搜索和选择定位反馈脚本来添加它。

    ![module2chapter3step8im](images/module2chapter3step8im.PNG)

6. 将 "feedbackPanel" 文本对象从 ASA_Feedback 层次结构拖到脚本下的空槽中，如下图所示。

    ![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>祝贺

在本课程中，我们学习了如何创建 UI 面板来显示 Azure 空间锚体验的当前状态，以便为用户提供实时反馈。
