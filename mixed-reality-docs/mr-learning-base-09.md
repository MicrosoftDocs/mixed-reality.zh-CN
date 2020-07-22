---
title: 入门教程 - 9. 使用语音命令
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: ed31c3b11497a0adc91b7ddc1c09b3fb4ca1c573
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304217"
---
# <a name="9-using-speech-commands"></a>9.使用语音命令

## <a name="overview"></a>概述

本教程将介绍如何创建语音命令，以及如何在全局范围内对其进行控制。 还将介绍如何控制需要用户查看控制语音命令的对象的本地语音命令。

## <a name="objectives"></a>目标

* 了解如何创建语音命令
* 了解如何在全局和本地控制语音命令

## <a name="ensuring-the-microphone-capability-is-enabled"></a>确保启用麦克风功能

在 Unity 菜单中，选择“混合现实工具包”>“实用工具”>“配置 Unity 项目”，打开“MRTK 项目配置器”窗口，然后在“UWP 功能”部分中，验证“启用麦克风功能”是否灰显   ：

![mr-learning-base](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> 在本系列教程开头配置 Unity 项目时，在[应用 MRTK 项目配置器设置](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings)指令期间，应该已经启用了麦克风功能。 但如果未启用此功能，请确保立即启用。

## <a name="creating-speech-commands"></a>创建语音命令

在“层次结构”窗口中选择“MixedRealityToolkit”对象，然后在“检查器”窗口中选择“MixedRealityToolkit”>“输入”选项卡，并执行以下步骤 ：

* 展开“语音”部分
* 克隆 DefaultMixedRealitySpeechCommandsProfile 并为其指定一个适当的名称，例如 GettingStarted_MixedRealitySpeechCommandsProfile
* 验证“启动行为”是否设置为“自动启动” 

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> 有关如何克隆 MRTK 配置文件的提示，可参阅[配置 MRTK 配置文件](mr-learning-base-03.md)中的说明。

在“语音”>“语音命令”部分，单击“+ 添加新的语音命令”按钮四次，以在现有语音命令列表种添加四个新的语音命令，然后在“关键字”字段中输入以下短语  ：

* 启用指示器
* 启用点击放置
* 启用边界框
* 禁用边界框

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> 如果计算机没有麦克风，可向语音命令分配一个 KeyCode，以便在按下相应的键时触发它们。

## <a name="controlling-speech-commands"></a>控制语音命令

在“项目”窗口中，导航到“资产” > “MRTK” > “SDK” > “功能” > “UX” > “预制件” > “工具提示”文件夹，以查找工具提示预制件      ：

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-1.png)

在“层次结构”窗口中，右键单击空白区域，然后选择“创建空白项”，将空对象添加到场景中。

将对象命名为 SpeechInputHandler_Global，然后在“检查器”窗口中，使用“添加组件”按钮添加 SpeechInputHandler 组件，并按如下所示对其进行配置  ：

* 取消选中“需要焦点”复选框，使用户无需查看带有 SpeechInputHandler 组件的对象即可触发语音命令 
* 从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-2.png)

在 SpeechInputHandler 组件上，单击小 + 图标三次，添加三个关键字元素：

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-3.png)

展开“元素 0”并按如下所示对其进行配置：

* 在“关键字”字段中，输入“启用指示器”，以引用在上一部分中创建的“启用指示器”语音命令 
* 单击 + 图标以添加事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 Indicator 对象 
* 从“无函数”下拉列表中，选择“GameObject” > “SetActive (bool)”将此函数设置为触发事件时要执行的操作  
* 选中参数复选框，让其处于选中状态

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-4.png)

展开“元素 1”并按如下所示对其进行配置：

* 在“关键字”字段中，输入“启用边界框”，以引用在上一部分中创建的“启用边界框”命令 
* 单击 + 图标以添加事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 
* 在“无函数”下拉列表中选择“BoundingBox” > “启用布尔”，以便在触发事件时更新此属性  
* 选中参数复选框，让其处于选中状态
* 单击小 + 图标以添加另一个事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 
* 在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  
* 选中参数复选框，让其处于选中状态

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-5.png)

展开“元素 2”并按如下所示对其进行配置：

* 在“关键字”字段中，输入“禁用边界框”，以引用在上一部分中创建的“禁用边界框”命令 
* 单击 + 图标以添加事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 
* 在“无函数”下拉列表中选择“BoundingBox” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已取消选中参数复选框
* 单击小 + 图标以添加另一个事件
* 从“层次结构”窗口中，向“无(对象)”字段分配 RoverExplorer 对象 
* 在“无函数”下拉列表中选择“ObjectManipulator” > “启用布尔”，以便在触发事件时更新此属性  
* 验证是否已取消选中参数复选框

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-6.png)

在“层次结构”窗口中依次选择“RoverExplorer”>“RoverAssembly”对象，然后在“检查器”窗口中，使用“添加组件”按钮添加“SpeechInputHandler”组件，并按如下所述配置该组件：  

* 验证是否已选中“需要焦点”复选框，使用户需要查看带有 SpeechInputHandler 组件的对象才可触发语音命令 
* 从“项目”窗口中，将“SpeechConfirmation Tooltip”预制件分配到“语音确认工具提示预制件”字段，以便在识别语音命令时显示此预制件 

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-7.png)

在 SpeechInputHandler 组件上，单击小 + 图标以添加关键字元素，展开新创建的元素，然后按如下所示对其进行配置：

* 在“关键字”字段中，输入“启用点击放置”，以引用在上一部分中创建的“启用点击放置”命令 
* 单击 + 图标以添加事件
* 从“层次结构”窗口中，将对象本身（即 RoverAssembly 对象）分配给“无(对象)”字段 
* 在“无函数”下拉列表中选择“TapToPlace” > “启用布尔”，以便在触发事件时更新此属性  
* 选中参数复选框，让其处于选中状态

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何创建语音命令，以及如何在全局范围内对其进行控制。 还了解了如何控制需要用户查看控制语音命令的对象的本地语音命令。

[入门教程](mr-learning-base-01.md)系列到此也就结束了。 通过这些教程，你成功使用 MRTK 从头构建了一个完整的混合现实体验。

接下来的 [Azure 空间定位点](mr-learning-asa-01.md)和[多用户功能教程](mr-learning-sharing-01.md)这两个教程系列将首先介绍如何将 Azure 空间定位点集成到你的项目中，以定位在现实世界中创建的漫游者探测器体验。 然后，将介绍如何将多用户功能添加到你的项目，以实时共享用户和对象的移动情况。
