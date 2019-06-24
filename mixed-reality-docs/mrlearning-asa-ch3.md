---
title: MR 学习 ASA 模块 Azure HoloLens 2 上的空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 4aabb4a35efebdd893cbb248365e534abd60f684
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326522"
---
# <a name="displaying-azure-spatial-anchor-feedback"></a>显示 Azure 空间的定位点反馈

在本课中，您将了解如何使用 Azure 空间的定位点时为用户提供有关定位点发现、 事件和状态的反馈。

目标：

* 了解如何设置用户界面面板，用于显示当前的 ASA 会话有关的重要信息

* 了解和探索 ASA SDK 向用户提供的反馈元素

  

## <a name="instructions"></a>说明

### <a name="set-up-asa-feedback-ui-panel"></a>设置 ASA 反馈 UI 面板

1. 在本课中，我们不使用"SaveAnchorToDisk"和"ShareAnchor"按钮，因此选择这两个按钮和取消选中检查器面板中的复选框 （如下所示） 来隐藏这些按钮。
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 接下来，创建指令面板。 通过右键单击"说明"按钮启动、 悬停"3D 对象"，然后选择"textmeshpro-text。

   

   ![module2chapter3step2im](images/module2chapter3step2im.PNG)

   3. 调整规模和定位文本，以便它与您的场景中的说明进行操作相匹配。 此外，确保居中的所有文本的对齐方式。 然后从文本编辑器中，删除示例文本，如在下图中所示。


![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. 将 TextMeshPro 对象的名称更改为"FeedbackPanel。"
   
   ![module2chapter3step4im](images/module2chapter3step4im.PNG)
   
5. 在项目面板中，选择"资产"并右键单击，然后选择"显示在资源管理器"。
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

现在，单击[此处](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E)下载文件所需在接下来的几个步骤。

6. 资源管理器打开后，选择资产文件夹，然后"ASAmodulesAssets"文件夹，并将定位点反馈脚本和定位点模块脚本文件复制到文件夹。 
   

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> 注意： 如果你收到一个弹出窗口，询问您是否要覆盖旧或保留旧请确保选择覆盖。

7. 现在返回到资产文件夹。 然后，转到"AzureSpatialAnchorsPlugin"文件夹，然后示例文件夹，并最后 scripts 文件夹中，并将 Azure 空间的定位点演示包装器复制到该文件夹。 
   

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. 现在，将文件上传时，确保选中"feedbackpanel"文本，ASA_feedback 层次结构中并单击"添加组件"并通过为其搜索，然后选择它后它会显示添加定位点反馈脚本。 
   
   

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. 从 ASA_Feedback 层次结构拖动到空槽脚本下的"feedbackPanel"文本对象，如下图中所示。 
   

![module2chapter3step9im](images/module2chapter3step9im.PNG)

   

## <a name="congratulations"></a>祝贺

在本课程中，我们学习了如何创建一个用户界面面板，以显示向用户提供实时反馈的 Azure 空间定位体验的当前状态。


