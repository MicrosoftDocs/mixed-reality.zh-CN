---
title: MR 学习的 HoloLens 2 共享模块
description: 完成此课程以了解如何实现 HoloLens 2 应用程序中的多用户共享的体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: 2a4ea599fd4887f30589c2d839be305d3dc8d1bd
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523191"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4.与多个用户共享对象移动

在本教程中，我们将了解如何共享对象的移动，以便共享会话的所有参与者都可以共同协作，并查看其他用户交互。 本课基于阴历作为的一部分而构建的启动器[基本模块教程](mrlearning-base.md)。

目标：

- 引入阴历启动器为三维模型来共享
- 将项目配置为共享的移动的三维模型。
- 了解如何生成基本的多用户协作应用程序

### <a name="instructions"></a>说明


1. 从上一课 (控制 + S) 保存场景。 您可以将其命名，HLSharedProjectMainPart4.unity，以便更轻松地找到所需的时。

2. 从项目窗口中，在资产中-> 脚本文件夹，双击 GenericNetSync 在 Visual Studio 或其曾经代码正在使用的编辑器中打开它。  ![](images/module3chapter4updatestep2.png)

3. 在行 34 和 38，删除 / / 若要激活的表，我们将在本课程中使用的代码。 接下来，将该文件。 ![](images/module3chapter4updatestep3.png)

4. 在项目窗口中，双击 PhotonRoom.cs 文件的资产中-> 若要在 Visual Studio 中打开脚本文件夹。 ![](images/module3chapter4updatestep4.png)

5. 就像在步骤 3 中，我们需要删除 / / 若要激活的 25、 26，以及 106 行处的代码。![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. 在层次结构视图中，选择 NetworkRoom 对象。![](images/module3chapter4updatestep6.png)

7. 在项目视图中，导航到资产-> 资源-> 预设。 首先，拖放表预设到 Tableprefab 槽 PhotonRoom 类上。 接下来拖放 LunarModule 预设到 PhotonRoom 类上的模块 Prefab 槽。 ![](images/module3chapter4updatestep7.png)

   注意：如果单击其中一个 prefab 对象和版本上，该检查器将切换到该对象。 单击、 拖动、 删除和发布到其相应的槽的每个对象。



8. 单击左侧的 MixedRealityPlayspace，箭头并将子游戏对象，MainCamera 向下移动到 SharedPlayground 预设。 接下来，删除预设可 MixedRealityPlayspace，删除、 选择预设，并在键盘上点击"删除"）。
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

注意：请确保主相机和 SharedPlayground 位置将设置为 0,0,0。

9. 创建新的游戏对象设置为子对象为 SharedPlayground 父对象以创建一个新的对象。 父对象中，右键单击并选择创建空白。 

10. 使用你的层次结构中选择的新对象，将对象的名称更改为 TableAnchor 检查器面板中。 此外，单击添加组件，搜索 TableAnchor 组件。 选择它并将其添加到该对象。 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 注意：设置定位到 x = 1，y = 0.55 和 z = 2。 此外，将旋转设置为 y = 90。 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. 现在从置入 Prefabs 文件夹中的项目面板中，将拖动表预设到刚创建的"TableAnchor"子对象。

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. 最后，DebugWindow 对象中更改为 80 和高度为 10 的宽度。

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>祝贺


完成此操作，加入你的 Unity 项目的所有用户可以都移动阴历启动器。 所有移动都同步，以便每个用户可以看到其他用户交互。 这些概念充当用于全功能、 共享的协作体验的基础构建块。 

虽然所有用户连接的共享体验的一部分，并且所见的相对移动的对象，该应用程序是仍无法准确地对齐虚拟形象和对象，以便本地用户看到彼此，并在物理内的同一位置中的对象世界。 若要定位到本地共享的体验，每个设备需要物理环境的了解。 在此模块中，我们将通过实现此目的使用[Azure 空间的定位点](<https://azure.microsoft.com/en-us/services/spatial-anchors/>)(ASA)，将在下一课中实现。

在继续之前为下一课中，我们将需要完成 ASA 学习模块涵盖 ASA 基础知识，需要 Azure 帐户和资源创建和其他基本建筑物块之前我们可以将此集成到我们的共享体验。

[下一课：第 5 课 Sharing(Photon)](mrlearning-sharing(photon)-ch5.md)

