---
title: 多用户功能教程 - 3. 连接多个用户
description: 完成本课程可以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031230"
---
# <a name="3-connecting-multiple-users"></a>3.连接多个用户

本课程介绍如何将多个用户连接为实时共享体验的一部分。 在本课程结束时，你将可以在多个设备上打开应用程序，并查看每个参与该体验的人员的头像（以球体表示）。

## <a name="objectives"></a>目标

* 在应用程序中配置 PUN
* 配置播放器
* 了解如何在共享体验中连接多个用户

## <a name="instructions"></a>说明

1. 在“项目”面板的“资产”->“资源”->“预制件”文件夹中，将 NetworkLobby 预制件拖放到层次结构中，如下图所示。

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. 展开 NetworkLobby 时，会看到名为 NetworkRoom 的子对象。 选择 NetworkRoom 后，进入“检查器”面板，然后单击“添加组件”。 搜索 PhotonView 并添加该组件。

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 在层次结构中新建一个空游戏对象。 在层次结构中单击右键，然后从上下文菜单中选择“空”。 确保位置设置为 x=0，y=0，z=0，将对象命名为 PhotonUser。

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 单击“添加组件”并键入“通用网络同步”。选择“通用网络同步”类。 显示该类后，单击“用户”复选框将其启用。

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 再次单击“添加组件”并键入“Photon 视图”。 选择下拉列表中显示的“Photon 视图”类。

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 单击“通用网络同步”类对应的“文件”图标。 将此类拖放到“Photon 视图”的“观察到的组件”字段中。

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. 接下来，我们将创建一个球体来表示参与共享体验的每个人员。 右键单击刚刚创建的 PhotonUser 对象，向下滚动到“3D 对象”并单击“球体”。 这会创建一个球体游戏对象作为 PhotonUser 对象的子级。

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 将球体缩小为 x=0.06，y=0.06，z=0.06。

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. 将 PhotonUser 游戏对象拖放到“项目”面板中的“预制件”文件夹，然后将其从场景中删除。 现已创建一个预制件，在共享体验中生成或实例化新的玩家时，可以使用该预制件。

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    >在从层次结构中删除该游戏对象之前，请确保已将它成功复制到“预制件”文件夹中。

10. 根据步骤 3 中的说明在层次结构中创建一个新对象，并将其命名为 SharedPlayground。 然后单击“添加组件”并搜索“通用网络管理器”。  再次单击“添加组件”以添加“通用网络管理器”组件。 将对象位置更改为 x=0，y=0，z=0。

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a>祝贺

完成上述所有步骤后，生成过程也已完成。请按“播放”按钮并连接 HoloLens 2。 晃头时，将会看到一个球体也随着移动。 此球体表示参与 Unity 项目的任何用户！

[下一课：4.与多个用户共享对象移动](mrlearning-sharing(photon)-ch4.md)
