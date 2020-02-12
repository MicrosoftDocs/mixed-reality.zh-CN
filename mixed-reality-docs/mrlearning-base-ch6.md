---
title: 入门教程-7。 创建农历模块示例应用程序
description: 在本课中，您将组合从前面的课程中学到的多个概念，以创建独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: b5b1bd0115822449bd6098f78cfc94d909169737
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129378"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. 创建农历模块示例应用程序
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

在本教程中，将多个概念与前面的课程结合起来，以创建独特的示例体验。 你将了解如何创建部件程序集应用程序，用户需要使用跟踪的手选取部件并尝试组装农历模块。 你将使用 pressable 按钮来打开和关闭放置提示、重置体验并将阴历模块启动到空间中！

在将来的教程中，你将继续根据此体验来构建，其中包括使用 Azure 空间锚点实现空间对齐的强大多用户用例。

## <a name="objectives"></a>目标

* 结合以前课程中的多个概念来创建一个独特的体验
* 了解如何切换对象
* 使用可按按钮触发复杂事件
* 使用刚体的物理特性和力量
* 探索如何使用工具提示

## <a name="lunar-module-parts-overview"></a>农历模块部件概述
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

在本部分中，你将创建一个简单的部件程序集质询，其中用户的目标是将位于表格上的五个部件分散到农历模块上的正确位置。

为实现此目的需要执行的主要步骤如下：

1. 将火箭启动器 prefab 添加到场景
2. 为所有部件启用对象操作
3. 添加和配置部件程序集演示（脚本）组件

> [!NOTE]
> 部分程序集演示（脚本）组件不是 MRTK 的一部分。 本教程提供了本教程的资产。

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. 将火箭启动器 prefab 添加到场景

在项目窗口中，导航到 "**资产**" > " **MRTK"。GettingStarted** > **Prototyping** > **RocketLauncher**文件夹中，将**RocketLauncher** prefab 拖到 "层次结构" 窗口中，将其添加到场景中，然后将其放置在合适的位置，例如：

* 转换位置 X = 1.5，Y =-0.4，Z = 0，因此它位于用户右侧 waist 高度
* 转换 X = 0，Y = 180，Z = 0，使用户体验的主要功能

![mrlearning](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. 为所有部件启用对象操作

在 "层次结构" 窗口中，找到 RocketLauncher > **LunarModuleParts**对象，然后选择所有**子对象**，添加**操作处理程序（脚本）** 组件和**近交互 Grabbable （脚本）** 组件，然后按如下所示配置操作处理程序（脚本）：

* 更改**两个**正在进行的操作类型以移动旋转，因而禁用缩放
* 取消选中 "**允许远端操作**" 复选框以仅允许近交互

![mrlearning](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> 若要获得有关如何实现对象操作的分步说明，请参阅[操作三维对象](mrlearning-base-ch4.md#manipulating-3d-objects)说明。

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. 添加和配置部件程序集演示（脚本）组件

在仍选择所有 LunarModuleParts 子对象的情况下，添加**音频源**组件，并按如下所示对其进行配置：

* 将合适的音频剪辑分配到**AudioClip**字段，例如 MRKT_Scale_Start
* 取消选中 "**在唤醒**状态下播放" 复选框，以便在加载场景时不会自动播放音频剪辑
* 更改**空间混合**为1以启用空间音频

![mrlearning](images/mrlearning-base/tutorial6-section1-step2-1.png)

所有 LunarModuleParts 子对象仍处于选中状态时，添加**部分程序集演示（脚本）** 组件：

![mrlearning](images/mrlearning-base/tutorial6-section1-step2-2.png)

在 "层次结构" 窗口中，选择 " **RoverEnclosure** " 对象，并按如下所示配置其**部件程序集演示（脚本）** 组件：

* 对于 "要**放置的对象**" 字段，分配对象本身，在本例中为**RoverEnclosure**对象
* 对于 "要**放置的位置**" 字段，分配相应的 PlacementHints 对象，在本例中为**RoverEnclosure_PlacementHints**对象
* 在 "**工具提示对象**" 字段中，分配相应的 ToolTipObject，在本例中为**RoverEnclosure_ToolTip**对象
* 在 "**音频源**" 字段中，分配对象本身，在本例中为**RoverEnclosure**对象

![mrlearning](images/mrlearning-base/tutorial6-section1-step2-3.png)

对每个其他 LunarModuleParts 子对象（例如 FuelTank、EnergyCell、DockingPortal 和 ExternalSensor）**重复**此操作。

如果你现在进入游戏模式并移动 "对象，使其靠近其位置"，你会注意到：

* 对象将会靠下并置于 LunarModule 对象下，使其成为农历模块的一部分
* 对象上的音频源将在对象的位置播放指定的音频剪辑
* 将隐藏相应的工具提示对象

![mrlearning](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> 有关如何使用编辑器内输入模拟的提醒，可参阅[使用编辑器内手写输入模拟](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)在[MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中测试场景指南。

## <a name="configuring-the-lunar-module"></a>配置登月舱

在本部分中，你将向火箭启动器应用程序添加其他功能，以便用户能够：

* 与农历模块交互
* 启动农历模块并在其启动时播放声音
* 重置应用程序，使农历模块和所有部件恢复到其原始位置
* 隐藏放置提示，使部件程序集质询更难。

为实现此目的需要执行的主要步骤如下：

1. 启用对象操作
2. 启用物理学
3. 添加音频源组件
4. 添加和配置 "启动农历模块（脚本）" 组件
5. 添加和配置切换放置提示（脚本）组件

> [!NOTE]
> 启动农历模块（脚本）组件和切换放置提示（脚本）组件不是 MRTK 的一部分。 本教程提供了本教程的资产。

### <a name="1-enable-object-manipulation"></a>1. 启用对象操作

在 "层次结构" 窗口中，选择 RocketLauncher > **LunarModule**对象，添加**操作处理程序（脚本）** 组件和**近交互 Grabbable （脚本）** 组件，然后配置操作处理程序（脚本），如下所示：

* 更改**两个**正在进行的操作类型以移动旋转，因而禁用缩放
* 取消选中 "**允许远端操作**" 复选框以仅允许近交互

![mrlearning](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. 启用物理学

在仍选择 RocketLauncher > **LunarModule**对象的情况下，添加一个刚体组件，然后按如下所示对其进行配置：

* 取消选中 "**使用重力**" 复选框，使农历模块不受引力的影响
* 选中 "**是运动**" 复选框，这样农历模块最初不会受到 physic 强制的影响

![mrlearning](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. 添加音频源组件

在仍选择 RocketLauncher > **LunarModule**对象的情况下，添加**音频源**组件，并按如下所示对其进行配置：

* 将**空间混合**更改为1以启用空间音频

![mrlearning](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. 添加和配置 "启动农历模块（脚本）" 组件

在仍选择 RocketLauncher > **LunarModule**对象的情况下，添加 "**启动农历模块（脚本）** " 组件，并按如下所示进行配置：

* 更改**主旨是**值，以使农历模块在启动时正常飞入，例如，到0.01

![mrlearning](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. 添加并配置切换放置提示（脚本）组件

在仍选择 RocketLauncher > **LunarModule**对象的情况下，添加**切换放置提示（脚本）** 组件，然后按如下所示对其进行配置：

* 将 "游戏对象数组**大小**" 属性设置为5
* 将每个**PlacementHints**对象的**子对象**分配到游戏对象数组中的一个**元素**字段：

![mrlearning](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>配置启动按钮

在 "层次结构" 窗口中，选择 "RocketLauncher >" 按钮 > **LaunchButton** "对象，然后在" **Pressable "按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，配置**LunarModule**对象以接收事件，并将**LaunchLunarModule**定义为要触发的操作：

![mrlearning](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> 有关如何实现事件的提醒，可参阅 "[手动跟踪手势" 和 "种不可交互" 按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)说明。

使用 RocketLauncher > 按钮 > **LaunchButton**对象，在**Pressable 按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，将**LunarModule**对象配置为接收事件，将**AudioSource**定义为要触发的操作，并将适当的音频剪辑分配给**音频剪辑**字段，例如 MRTK_Gem 音频剪辑：

![mrlearning](images/mrlearning-base/tutorial6-section3-step1-2.png)

使用 RocketLauncher > 按钮 > **LaunchButton**对象，在**Pressable 按钮（脚本）** 组件上，创建一个新的**Touch 结束（）** 事件，配置**LunarModule**对象以接收事件，并将**LaunchLunarModule**定义为要触发的操作：

![mrlearning](images/mrlearning-base/tutorial6-section3-step1-3.png)

如果你现在进入游戏模式并按下 "启动" 按钮，则会听到音频剪辑播放，如果你将 "启动" 按钮向下移动大约一秒钟或更长时间，你会看到农历模块启动到空间中：

![mrlearning](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>配置重置按钮

在 "层次结构" 窗口中，选择 "RocketLauncher >" 按钮 > **ResetButton** "对象，然后在" **Pressable "按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，配置**LunarModule**对象以接收事件，并将**LaunchLunarModule**定义为要触发的操作：

![mrlearning](images/mrlearning-base/tutorial6-section4-step1-1.png)

将 RocketLauncher > 按钮 > **ResetButton**对象保持为选中状态，在 " **Pressable" 按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，将**RocketLauncher**对象配置为接收事件，将**GameObject**定义为要触发的操作，并在 "消息" 字段中输入**BroadcastMessage** ：

![mrlearning](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> GameObject. BroadcastMessage 操作将 ResetPlacement 消息从 RocketLauncher 对象发送到其所有子对象。 在添加到所有 LunarModuleParts 子对象的部件程序集演示（脚本）组件中定义的 ResetPlacement 函数的任何子对象将调用重置该子对象的位置的 ResetPlacement 函数。

如果你现在进入游戏模式并按下 "重置" 按钮，你会听到播放的音频剪辑，并看到要在空间中启动的农历模块：

![mrlearning](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>配置放置提示按钮
<!-- TODO: Rename to 'Configuring the Hints button'-->

在 "层次结构" 窗口中，选择 "> RocketLauncher" 按钮 > **HintsButton**对象，然后在 " **Pressable" 按钮（脚本）** 组件上，创建一个新的**按钮按下（）** 事件，配置**LunarModule**对象以接收事件，并定义**TogglePlacementHints。 ToggleGameObjects**要触发的操作：

![mrlearning](images/mrlearning-base/tutorial6-section5-step1-1.png)

如果你现在进入游戏模式，你会注意到，默认情况下会禁用半透明的放置提示，但你可以通过按 "提示" 按钮打开和关闭它们：

![mrlearning](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>祝贺你

已完全配置此应用程序。 现在，你的应用程序允许用户完全组装农历模块，启动农历模块，切换提示，并重置应用程序以重新启动。
