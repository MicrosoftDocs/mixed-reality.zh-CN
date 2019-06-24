---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326656"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>同步共享对象移动

在本课中，我们将了解如何共享对象的移动，以便共享会话的所有参与者都可以共同协作，并查看其他用户交互。 本课基于阴历作为的一部分而构建的启动器[基本模块教程](mrlearning-base.md)。

目标：

- 作为要共享的三维模型导入已完成阴历启动器
- 将项目配置为共享的移动的三维模型。
- 了解如何生成基本的多用户协作应用程序

### <a name="instructions"></a>说明

1. 从上一课 （控制 + S） 保存场景。 您可能它命名为"HLSharedProjectMainPart4.unity"以便更轻松地找到时再需要它。

2. 删除"NetworkLobby"对象 （通过选择它并按 delete 键）。 此外，从第 2 课转到"预设"文件夹，然后从此处也删除"NetworkLobby"预设。

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. 导入新的自定义包 （例如，从第 2 课的步骤 2） 和导入[LunarModule.unitypackage](linkforModule1 lesson with the lunar module)和[NetworkLobbyReplacement.unitypackage。](linkforNetworklobbyreplacement package here)

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. 现在，在"预设"文件夹中，将新的"NetworkLobby"预设拖到层次结构。 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> 注意： 我们在前面的步骤中导入的两个包更新"NetworkLobby"预设。 它使您许多键入内容 ！

5. 现在，单击"MixedRealityPlayspace"左侧的箭头，并将子游戏对象"MainCamera"向下移动到"SharedPlayground"预设。 然后，删除 prefab"MixedRealityPlayspace"（若要删除，选择预设可在键盘上点击"删除"）。

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. 创建新的游戏对象作为子对象设置为"SharedPlayground"父对象 （若要创建新的对象，父对象中，右键单击并选择"创建空"）。
7. 与你的层次结构中选择的新对象，将对象的名称更改为"TableAnchor"检查器面板中。 此外，单击"添加组件"，搜索"TableAnchor"组件。 选择它并将其添加到该对象。

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 注意： 设置定位到 x = 1，y = 0.55 和 z = 2。 此外，将旋转设置为 y = 90。 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. 现在在项目面板中，在"预设"文件夹中，将"表"预设到刚创建的"TableAnchor"子对象。

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. 选择"NetworkRoom，""NetworkLobby"下的子对象，在层次结构，并单击"添加组件"，在检查器面板和"PhotonView"的搜索中，将脚本添加到"*NetworkRoom*"对象。

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. 最后，"DebugWindow"对象中更改为 80 和高度为 10 的宽度。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>祝贺

完成此操作，加入你的 Unity 项目的所有用户可以都移动阴历启动器。 所有移动都同步，以便每个用户可以看到其他用户交互。 这些概念充当用于全面共享的协作体验的基础构建块。 

虽然所有用户连接的共享体验的一部分，并且所见的相对移动的对象，该应用程序是仍无法准确地对齐虚拟形象和对象，以便本地用户看到彼此，并在物理内的同一位置中的对象世界。 若要定位到本地共享的体验，每个设备需要物理环境的了解。 在此模块中，我们将使用实现此目的[Azure 空间的定位点](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，这将在下一课中实现。

在继续之前为下一课中，我们将需要完成 ASA 学习模块，将介绍 ASA 基础知识，需要 Azure 帐户和资源创建和其他基本建筑物块之前我们可以将此集成到我们的共享体验。

[下一课：第 5 课 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)

