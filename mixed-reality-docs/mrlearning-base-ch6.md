---
title: 入门教程 - 7. 创建登月舱示例应用程序
description: 本课程将结合以前课程中所介绍的多个概念来创建一个独特的示例体验。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031562"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7.创建登月舱示例应用程序
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

本教程结合前面课程中介绍的多个概念创建一个独特的示例体验。 其中将会介绍如何创建一个部件装配应用程序，其用户需要使用跟踪手来拾取部件并尝试装配登月舱。 你将使用可按按钮打开和关闭位置提示、重置体验，并将登月舱发射到太空！

在以后的教程中，你将继续基于此体验生成应用程序，包括强大的利用 Azure 空间定位点进行空间对齐的多用户用例。

## <a name="objectives"></a>目标

* 结合以前课程中的多个概念来创建一个独特的体验
* 了解如何切换对象
* 使用可按按钮触发复杂事件
* 使用刚体的物理特性和力量
* 探索如何使用工具提示

## <a name="lunar-module-parts-overview"></a>登月舱部件概述
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

在本部分，你将创建一个简单的部件装配质询方案，其中，用户的目标是将分散在台面上的五个部件定位在登月舱中的适当位置。

若要实现此目的，请执行以下主要步骤：

1. 将火箭发射器预制件添加到场景中
2. 为所有部件启用对象操作
3. 添加并配置“部件装配演示(脚本)”组件

> [!NOTE]
> MRTK 中未包含“部件装配演示(脚本)”组件。 本教程的资产中随附了该组件。

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1.将火箭发射器预制件添加到场景中

在“项目”窗口中导航到“资产” > “MRTK.Tutorials.GettingStarted” > “预制件” > “RocketLauncher”文件夹，将“RocketLauncher”预制件拖放到“层次结构”窗口以将其添加到场景中，然后将其定位在适当的位置，例如：     

* 变换位置 X = 1.5，Y = -0.4，Z = 0，使之位于用户右侧的腰部高度处
* 转换旋转 X = 0，Y = 180，Z = 0，使该体验的主要功能面对用户

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2.为所有部件启用对象操作

在“层次结构”窗口中找到“RocketLauncher”>“LunarModuleParts”对象，选择所有**子对象**，添加“操作处理程序(脚本)”组件和“近距交互可抓取对象(脚本)”组件，然后按如下所述配置“操作处理程序(脚本)”：   

* 取消选中“允许远距操作”复选框，以便仅允许近距交互 
* 将“双手操作类型”更改为“移动旋转”，以禁用缩放  

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> 有关如何实现对象操作的提示和分步说明，可参阅[操作 3D 对象](mrlearning-base-ch4.md#manipulating-3d-objects)中的说明。

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3.添加并配置“部件装配演示(脚本)”组件

在仍选中了所有 LunarModuleParts 子对象的情况下，添加“音频源”组件，然后按如下所述对其进行配置： 

* 将适当的音频剪辑（例如 MRKT_Scale_Start）分配到“AudioClip”字段 
* 取消选中“唤醒时播放”复选框，以便在加载场景时不会自动播放该音频剪辑 
* 将“空间混合”更改为 1，以启用空间音频 

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

在仍选中了所有 LunarModuleParts 子对象的情况下，添加“部件装配演示(脚本)”组件： 

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

在“层次结构”窗口中选择“RoverEnclosure”对象，并按如下所述配置其“部件装配演示(脚本)”组件：  

* 在“要定位的对象”字段中分配该对象**本身**，在本例中为 RoverEnclosure 对象 
* 在“定位位置”字段中分配相应的“PlacementHints”对象，在本例中为 RoverEnclosure_PlacementHint 对象  
* 在“工具提示对象”字段中分配相应的“ToolTip”对象，在本例中为 RoverEnclosure_ToolTip 对象  
* 在“音频源”字段中分配该对象**本身**，在本例中为 RoverEnclosure 对象 

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

针对其他每个 LunarModuleParts 子对象（即 FuelTank、EnergyCell、DockingPortal 和 ExternalSensor）**重复**上述步骤。

如果现在进入“游戏”模式，并使某个“要定位的对象”靠近其相应的“定位位置”，将会发现：

* 该对象将会卡入就位，并成为 LunarModule 对象下的父级，因此成了登月舱的部件
* 该对象上的音频源将在该对象的位置播放分配的音频剪辑
* 相应的工具提示对象将会隐藏

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> 有关如何使用编辑器中的输入模拟功能的提示，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的[使用编辑器中的手写输入模拟来测试场景](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)指南。

## <a name="configuring-the-lunar-module"></a>配置登月舱

在本部分，你将在火箭发射器应用程序中添加附加的功能，使用户能够：

* 与登月舱交互
* 将登月舱发射到太空，并在发射时播放声音
* 重置应用程序，使登月舱和所有部件复位到其原始位置
* 隐藏位置提示，使部件装配质询变得更困难。

若要实现此目的，请执行以下主要步骤：

1. 启用对象操作
2. 启用物理学
3. 添加“音频源”组件
4. 添加并配置“发射登月舱(脚本)”组件
5. 添加并配置“切换位置提示(脚本)”组件

> [!NOTE]
> MRTK 中未包含“发射登月舱(脚本)”组件和“切换位置提示(脚本)”组件。 本教程的资产中随附了这些组件。

### <a name="1-enable-object-manipulation"></a>1.启用对象操作

在“层次结构”窗口中选择“RocketLauncher”>“LunarModule”对象，添加“操作处理程序(脚本)”组件和“近距交互可抓取对象(脚本)”组件，然后按如下所述配置“操作处理程序(脚本)”：   

* 取消选中“允许远距操作”复选框，以便仅允许近距交互 
* 将“双手操作类型”更改为“移动旋转”，以禁用缩放 

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2.启用物理学

在仍选中了“RocketLauncher”>“LunarModule”对象的情况下，添加一个“刚体”组件，并按如下所述对其进行配置：  

* 取消选中“使用重力”复选框，使登月舱不受重力的影响 
* 选中“遵守运动力学”复选框，使登月舱最初不受物理作用力的影响 

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3.添加“音频源”组件

在仍选中了“RocketLauncher”>“LunarModule”对象的情况下，添加一个“音频源”组件，并按如下所述对其进行配置：  

* 将“空间混合”更改为 1，以启用空间音频 

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4.添加并配置“发射登月舱(脚本)”组件

在仍选中了“RocketLauncher”>“LunarModule”对象的情况下，添加“发射登月舱(脚本)”组件，并按如下所述对其进行配置：  

* 更改“推力”值（例如，更改为 0.01），使登月舱在发射后优雅飞行 

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5.添加并配置“切换位置提示(脚本)”组件

在仍选中了“RocketLauncher”>“LunarModule”对象的情况下，添加“切换位置提示(脚本)”组件，并按如下所述对其进行配置：  

* 将游戏对象数组“大小”属性设置为 5 
* 将“RocketLauncher”>“LunarModule”>“PlacementHints”对象的每个**子对象**分配到游戏对象数组中的“元素”字段：  

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>配置“发射”按钮

在“层次结构”窗口中选择“RocketLauncher”>“Buttons”>“LaunchButton”对象，然后在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“LunarModule”对象配置为接收该事件，然后将“LaunchLunarModule.StartThruster”定义为要触发的操作：    

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> 有关如何实现事件的提示，可参阅[手动跟踪手势和可交互按钮](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons)中的说明。

在仍选中了“RocketLauncher”>“Buttons”>“LaunchButton”对象的情况下，在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“LunarModule”对象配置为接收该事件，将“AudioSource.PlayOneShot”定义为要触发的操作，然后将适当的音频剪辑（例如 MRTK_Gem 音频剪辑）分配到“音频剪辑”字段：     

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

在仍选中了“RocketLauncher”>“Buttons”>“LaunchButton”对象的情况下，在“可按按钮(脚本)”组件中创建新的 **Touch End ()** 事件，将“LunarModule”对象配置为接收该事件，然后将“LaunchLunarModule.StopThruster”定义为要触发的操作：    

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

如果现在进入“游戏”模式并按下“发射”按钮，将会听到播放的音频剪辑；如果按住“发射”按钮一秒或更长时间，将会看到登月舱已发射到太空：

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>配置“重置”按钮

在“层次结构”窗口中选择“RocketLauncher”>“Buttons”>“ResetButton”对象，然后在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“LunarModule”对象配置为接收该事件，然后将“LaunchLunarModule.ResetModule”定义为要触发的操作：    

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

在仍选中了“RocketLauncher”>“Buttons”>“ResetButton”对象的情况下，在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“RocketLauncher”对象配置为接收该事件，将“GameObject.BroadcastMessage”定义为要触发的操作，然后在消息字段中输入 **ResetPlacement**：    

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> GameObject.BroadcastMessage 操作会将 ResetPlacement 消息从 RocketLauncher 对象发送到其所有子对象。 具有 ResetPlacement 函数（在添加到所有 LunarModuleParts 子对象的“部件装配演示(脚本)”组件中定义）的任何子对象将调用 ResetPlacement 函数，以重置该子对象的位置。

如果现在进入“游戏”模式，移动某些部件和/或发射登月舱，然后按“重置”按钮，则将看到这些部件和/或登月舱重置到其原始位置：

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>配置“位置提示”按钮
<!-- TODO: Rename to 'Configuring the Hints button'-->

在“层次结构”窗口中选择“RocketLauncher”>“Buttons”>“HintsButton”对象，然后在“可按按钮(脚本)”组件中创建新的 **Button Pressed ()** 事件，将“LunarModule”对象配置为接收该事件，然后将“TogglePlacementHints.ToggleGameObjects”定义为要触发的操作：    

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

如果现在进入“游戏”模式，将会看到，默认已禁用半透明的位置提示，但可以通过按“提示”按钮来打开和关闭提示：

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>祝贺

现已完全配置了此应用程序。 该应用程序将允许用户全面装配登月舱，发射登月舱，打开/关闭提示，以及重置应用程序以重新开始设置。
