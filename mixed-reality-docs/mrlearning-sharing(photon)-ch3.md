---
title: 多用户功能教程-3。 连接多个用户
description: 完成本课程以了解如何在 HoloLens 2 应用程序中实现多用户共享体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: a6d1a269f45b4aaf7cbd8fea948ddcbdf0bf18e2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437734"
---
# <a name="3-connecting-multiple-users"></a>3. 连接多个用户

在本课程中，我们将了解如何将多个用户连接为实时共享体验的一部分。 在本课结束时，你将能够在多个设备上打开该应用程序，并查看每个加入人员的一个球表示的头像。 

目标

- 在应用程序中配置双关语
- 配置播放机
- 了解如何在共享体验中连接多个用户

## <a name="instructions"></a>说明

1. 在 "资产-> 资源-> Prototyping" 文件夹的 "项目" 面板中，将 NetworkLobby prefab 拖放到层次结构中，如下图所示。

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. 展开 "NetworkLobby" 时，会看到一个名为 "NetworkRoom" 的子对象。 选择 NetworkRoom 后，进入检查器面板，然后单击 "添加组件"。 搜索 PhotonView 并添加组件。

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 在层次结构中创建新的空游戏对象。 在层次结构中右键单击，然后从上下文菜单中选择 "空"。 确保将定位设置为 x = 0、y = 0、z = 0 并将对象命名为 PhotonUser。

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 单击 "添加组件"，然后键入 "通用网络同步"。选择 "通用" 网络同步类。 出现类时，单击 "用户" 复选框将其打开。 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 再次单击 "添加组件"，然后键入 "Photon 视图"。 选择显示在下拉列表中的 Photon 视图类。

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 单击一般 Net Sync 类的文件图标。 将其拖放到 Photon 视图的 "观察的组件" 字段。 

![module3chapter3updateStep6im .png](images/module3chapter3updateStep6im.png) 

7. 接下来，我们将创建一个球来表示加入共享经验的每个人。 右键单击刚创建的 PhotonUser 对象，向下滚动到 "3D 对象并单击球体"。 这会将一个球游戏对象创建为 PhotonUser 对象的子对象。

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 将球体缩小为 x = 0.06，y = 0.06，ad z = 0.06。

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. 将 PhotonUser 游戏对象拖到 "项目" 面板中的 "Prototyping" 文件夹，然后将其从场景中删除。 现在，你已创建了一个可在共享体验中生成或实例化新播放器时使用的 prefab。

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 注意：在从层次结构中删除游戏对象之前，请确保它已成功复制到 Prototyping 文件夹中。

10. 按照步骤3中的说明在层次结构中创建新的对象，并将其命名为 SharedPlayground。 然后，单击 "添加组件"，然后搜索 "通用网络管理器"。  再次单击它以添加通用网络管理器组件。 将对象的位置更改为 x = 0、y = 0，z = 0。

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>祝贺

完成上述所有步骤后，生成过程也已完成，按下 "播放" 按钮，然后连接 HoloLens 2。 当您移动头时，您应该会看到一个球四处移动。 这将显示加入 Unity 项目的任何用户！

[下一课： 4. 与多个用户共享对象移动](mrlearning-sharing(photon)-ch4.md)

