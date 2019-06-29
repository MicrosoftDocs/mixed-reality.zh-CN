---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465217"
---
# <a name="connecting-multiple-users"></a>**将多个用户连接** 

在本课中，我们将了解如何将多个用户连接作为实时共享体验的一部分。 本课程结束时，您可以打开多个设备上的应用程序，并查看虚拟形象，表示球体，联接每个人的表示形式。 

目标：

- 在应用程序中配置双关语
- 配置播放机
- 了解如何连接的共享体验中的多个用户

### <a name="instructions"></a>说明

1. 在资产中-> 资源-> 在项目面板中的置入 Prefabs 文件夹中，拖放 NetworkLobby 预设可在向层次结构中如下图所示。


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. 在展开 NetworkLobby 时，您将看到名为 NetworkRoom 的子对象。 选择 NetworkRoom，转到检查器面板中，并单击添加组件。 PhotonView 搜索并添加该组件。

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 在层次结构中创建一个新的空游戏对象。 在层次结构中，右键单击并从上下文菜单中选择为空。 确保将位置设置为 x = 0，y = 0，z = 0，PhotonUser 对象命名为。

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 单击添加组件，并键入泛型 Net 同步。选择泛型 Net 同步类。 出现此类后，单击用户复选框以将其打开。 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 同样，单击添加组件并键入 Photon 视图。 在下拉列表中选择出现的 Photon 视图类。

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 单击针对泛型 Net 同步类的文件图标。 拖放 Photon 视图的观察到组件字段中。 ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. 接下来，我们创建球体来表示每个联接的共享的体验的人员。 右键单击刚创建的 PhotonUser 对象和到 scrolldown"3D 对象，并单击球体。 这将创建球游戏对象作为 PhotonUser 对象的子级。

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 缩放 x 到球体 = 0.06，y = 0.06，ad z = 0.06。

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. 将 PhotonUser 游戏对象拖到项目面板中置入 Prefabs 文件夹，然后从场景中删除它。 我们现在已创建生成或实例化新供应商的共享体验时，可以使用预设。

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 注意： 确保游戏对象已成功复制到置入 Prefabs 文件夹之前从层次结构中删除它。

10. 步骤 3 中的说明在层次结构中创建一个新的对象并将其命名 SharedPlayground。 然后，单击添加组件和一般网络管理器中，搜索并单击它以添加泛型网络管理器组件。 将对象的位置更改为 x = 0，y = 0，并且 z = 0。

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>祝贺

上述所有步骤都均已完成，并在生成过程也是完成后，按播放按钮，并连接 HoloLens 2。 应会看到球体移动时您四处移动。 这将显示的任意用户的加入你的 Unity 项目 ！

[下一课：第 4 课 Sharing(Photon)](mrlearning-sharing(photon)-ch4.md)

