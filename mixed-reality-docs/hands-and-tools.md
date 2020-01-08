---
title: 双手和运动控制器
description: 双手和运动控制器交互概述
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合现实、动手、运动控制器、交互、设计
ms.openlocfilehash: 27d13316bbc4b3b40a1e617d73dd5487c05cb347
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334442"
---
# <a name="hands-and-motion-controllers"></a>双手和运动控制器
## <a name="scenarios"></a>场景
如果在阅读[交互概述](interaction-fundamentals.md)后选择采用此交互模型，这意味着您正在开发一个应用程序，要求用户使用两次手与全息世界交互。 您的应用程序将实现删除虚拟与物理之间边界的目标。

某些特定情况可能如下：
* 向信息工作者提供2D 虚拟屏幕和 UI 实用以显示和控制内容
* 为工厂程序集线提供第一行工作人员教程和指南
* 开发用于帮助和教育医疗专业人员的专业工具  
* 使用3D 虚拟对象装饰现实世界，或创建另一个世界 
* 使用现实世界作为背景创建基于位置的服务和游戏

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>双手和运动控制器情态

:::row:::
    :::column:::
       [用双手 ![直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsdirect-manipulationmdbr"></a>[使用手直接操作](direct-manipulation.md)<br>
       这是一种使用手的强大功能的模态，用户可以直接接触和操作全息影像。 通过利用日常经验并提供适当的视觉实用，用户可以使用相同的方法来操作现实世界对象，以便与虚拟对象进行交互。
    :::column-end:::
    :::column:::
       [手动 ![点和提交](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handspoint-and-commitmdbr"></a>[使用手指向和提交](point-and-commit.md)<br>
        这种模态使用户能够在远处与全息影像交互。 它使用户能够充分利用环境。 用户可以在任何位置放置全息影像，同时仍然可以从任意距离访问。 用于控制和操作2D 和3D 全息影像的心理模型和手势与直接操作的情况有关。
    :::column-end:::
    :::column:::
       [![运动控制器](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersmotion-controllersmdbr"></a>[运动控制器](motion-controllers.md)<br>
       运动控制器是通过在使用一种或两种手时跨大量距离提供精确交互来扩展用户的物理功能的工具。 这些硬件附件提供了许多常用交互的快捷方式，并为各种操作提供了 surefooted、tactile 的反馈。 目前，运动控制器仅适用于 Windows Mixed Reality （WMR）方案。 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>另请参阅
* [头部凝视并提交](gaze-and-commit.md)
* [头部凝视和停留](gaze-and-dwell.md)
* [使用手直接操作](direct-manipulation.md)
* [使用手指向和提交](point-and-commit.md)
* [免动手操作](hands-free.md)
