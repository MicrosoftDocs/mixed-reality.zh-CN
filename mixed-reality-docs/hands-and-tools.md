---
title: 双手和动作控制器
description: 双手和动作控制器交互的概述
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 混合现实，手、 运动控制器、 交互，设计
ms.openlocfilehash: 583d284ee98b8ccbc0a9c2c8670551d0a7397074
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873997"
---
# <a name="hands-and-motion-controllers"></a>双手和动作控制器
## <a name="scenarios"></a>方案
如果选择读取后采用此交互模型[设计准则](interaction-fundamentals.md)，这意味着您在开发应用程序要求用户使用两只手进行与 holographic 世界交互。 你的应用程序要实现删除之间虚拟和物理边界的目标。

某些特定方案可能是：
* 提供信息工作人员 2D 虚拟屏幕和 Ui 用于显示和控制内容
* 提供第一个行辅助角色教程和工厂的程序集行中的指南
* 开发用于协助和培训医疗专业人员的专业工具  
* 使用 3D 虚拟对象来修饰现实世界，或若要创建第二个世界 
* 创建位置基于服务和作为背景中使用实际的游戏

## <a name="hands-and-motion-controllers-modalities"></a>双手和动作控制器模式
### <a name="direct-manipulation-near-hand-interactiondirect-manipulationmd"></a>[直接操作 （附近手动交互）](direct-manipulation.md)
这是利用的手，用户了支持的触摸和直接操作全息模态。 通过 leaveraging 日常生活体验和提供适当的可视化提示，用户就能够使用相同的方法来操作实际对象与虚拟的交互。   

### <a name="point-and-commit-far-hand-interactionpoint-and-commitmd"></a>[点和提交 （Far 手动交互）](point-and-commit.md)
此模式为用户提供超级全息距离与之交互的能力。 它使用户能够充分利用的周围的设置。 用户可以在任意位置全息和仍可以从任何距离访问它们。 心理模型和用于控制和操作 2D 和 3D 全息手势是高度与同步的直接操作。

### <a name="motion-controllersmotion-controllersmd"></a>[运动控制器](motion-controllers.md)
运动控制器是通过使用一个或两个指针时为单位的距离大范围内提供精确交互来扩展用户的物理功能的工具。 这些硬件附件提供了许多常用的交互，并提供 surefooted、 触觉反馈的各种操作的快捷方式。 目前，motion 控制器是仅适用于 WMR 方案。 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a>请参阅
* [视线移动和提交](gaze-and-commit.md)
* [直接操作 （附近手动交互）](direct-manipulation.md)
* [点和提交 （Far 手动交互）](point-and-commit.md)
* [Hands-free](hands-free.md)
* [设定凝视目标](gaze-targeting.md)
