---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416008"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>同步共享对象移动

在本课中，我们将了解如何共享对象的移动，以便共享会话的所有参与者都可以共同协作，并查看其他用户交互。 本课基于阴历作为的一部分而构建的启动器[基本模块教程](mrlearning-base.md)。

目标：

- 引入阴历启动器为三维模型来共享
- 将项目配置为共享的移动的三维模型。
- 了解如何生成基本的多用户协作应用程序

### <a name="instructions"></a>说明

1. 从上一课 （控制 + S） 保存场景。 您可能它命名为"HLSharedProjectMainPart4.unity"以便更轻松地找到时再需要它。

2. 在资产中的项目窗口 > Scripts 文件夹中，双击 GenericNetSync 在 Visual Studio 或其曾经代码正在使用的编辑器中打开它。  ![](images/module3chapter4updatestep2.png)

3. 34 和 38 行，删除"/ /"的表，我们将在本课程中使用的激活代码。  然后保存该文件。 ![](images/module3chapter4updatestep3.png)

4. 在项目窗口中，双击 PhotonRoom.cs 文件的资产中 > 若要再次 Visual Studio 中打开脚本文件夹。 ![](images/module3chapter4updatestep4.png)

5. 就像在步骤的 3 中我们需要删除"/ /"来激活 25、 26，以及 106 行处的代码。![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. 在层次结构视图中，选择 NetworkRoom 对象。![](images/module3chapter4updatestep6.png)

7. 在项目视图中，导航到资产 > 资源 > 预设。 首先，拖放表预设到 PhotonRoom 类上的"Tableprefab"槽。 接下来拖放 LunarModule 预设到 PhotonRoom 类上的"模块 Prefab"槽。 ![](images/module3chapter4updatestep7.png)

   注意：如果单击其中一个 prefab 对象和版本上，该检查器将切换到该对象。 单击、 拖动、 放置和发布到其相应的槽的每个对象。



8. 现在，单击"MixedRealityPlayspace"左侧的箭头，并将子游戏对象"MainCamera"向下移动到"SharedPlayground"预设。 然后，删除 prefab"MixedRealityPlayspace"（若要删除，选择预设可在键盘上点击"删除"）。

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

注意：请确保主相机和 SharedPlayground 位置将设置为 0,0,0。

9. 创建新的游戏对象作为子对象设置为"SharedPlayground"父对象 （若要创建新的对象，父对象中，右键单击并选择"创建空"）。 

10. 与你的层次结构中选择的新对象，将对象的名称更改为"TableAnchor"检查器面板中。 此外，单击"添加组件"，搜索"TableAnchor"组件。 选择它并将其添加到该对象。 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 注意： 设置定位到 x = 1，y = 0.55 和 z = 2。 此外，将旋转设置为 y = 90。 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. 现在在项目面板中，在"预设"文件夹中，将"表"预设到刚创建的"TableAnchor"子对象。

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. 最后，"DebugWindow"对象中更改为 80 和高度为 10 的宽度。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>祝贺

完成此操作，加入你的 Unity 项目的所有用户可以都移动阴历启动器。 所有移动都同步，以便每个用户可以看到其他用户交互。 这些概念充当用于全面共享的协作体验的基础构建块。 

虽然所有用户连接的共享体验的一部分，并且所见的相对移动的对象，该应用程序是仍无法准确地对齐虚拟形象和对象，以便本地用户看到彼此，并在物理内的同一位置中的对象世界。 若要定位到本地共享的体验，每个设备需要物理环境的了解。 在此模块中，我们将使用实现此目的[Azure 空间的定位点](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，这将在下一课中实现。

在继续之前为下一课中，我们将需要完成 ASA 学习模块，将介绍 ASA 基础知识，需要 Azure 帐户和资源创建和其他基本建筑物块之前我们可以将此集成到我们的共享体验。

[下一课：第 5 课 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)

