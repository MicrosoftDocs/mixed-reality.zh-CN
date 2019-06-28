---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 33f265c6333f12f7ec73ecb0c1e5730b168d4bde
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415908"
---
# <a name="connecting-multiple-users"></a>**将多个用户连接** 

在本课中，我们将了解如何将多个用户连接作为实时共享体验的一部分。 本课程结束时，你将能够打开多个设备上的应用程序并查看"虚拟形象"表示每个人员的联接 （表示球体的头像。） 

目标：

- 在应用程序中配置双关语
- 配置播放机
- 了解如何连接的共享体验中的多个用户

### <a name="instructions"></a>说明

1. 在资产中 > 资源 > 预设文件夹的项目面板的拖放"NetworkLobby"预设中的层次结构，如下图中所示。


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. 在展开 prefab"NetworkLobby"时，应会看到名为"NetworkRoom。"的子对象 使用它选择，请转到检查器面板并单击"添加组件"。 搜索"PhotonView"并添加该组件。

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 在层次结构中创建一个新的空游戏对象 （右键单击层次结构中并从上下文菜单中选择"空"）。 确保将位置设置为 x = 0，y = 0，z = 0，命名该对象，"PhotonUser。"

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 单击"添加组件"按钮并键入"泛型 Net Sync"并选择通用 Net 同步类。 类出现后，请单击"用户"复选框以将其打开。 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 再次单击"添加组件"，然后键入"Photon 视图"并选择下拉列表中显示的 Photon 视图类。

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 现在单击泛型 Net 同步类中的文件图标，然后拖放它到 Photon 视图的"观察到组件"字段。 ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. 接下来，我们想要创建球体来表示每个联接的共享的体验的人员。 右键单击刚创建的"PhotonUser"对象，转到"3D 对象"，然后单击"球体"。 这将创建球游戏对象作为 PhotonUser 对象的子级。

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 缩放 x 到球体 = 0.06，y = 0.06，ad z = 0.06。

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. 将"PhotonUser"游戏对象拖到项目面板中的"预设"文件夹。 然后，删除从场景。 我们现在已创建生成或实例化新供应商的共享体验时，将使用的预设。

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 注意： 确保游戏对象已成功复制到"prefabs"文件夹之前从层次结构中删除它。

10. （使用类似的步骤 3 的说明），在层次结构中创建一个新的对象并将其命名为"SharedPlayground。" 然后，单击"添加组件"并搜索"通用网络管理器"并单击它以添加泛型网络管理器组件。 将对象的位置更改为 x = 0，y = 0，并且 z = 0。

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>祝贺

上述所有步骤都均已完成，并生成过程后，按播放按钮并连接 HoloLens 2 时，你应看到球体移动时您四处移动 ！ 这将显示的任意用户的加入你的 Unity 项目 ！

[下一课：第 4 课 Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)

