---
title: 显示进度
description: 进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 控件、 ui 和 ux
ms.openlocfilehash: d62d86c690233f351b6c156c66eba33cb2687ea6
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813724"
---
# <a name="displaying-progress"></a>显示进度

进度控件将为用户提供关于正在处理运行时间较长的操作的反馈。 这意味着，在进度指示器可见，并且还可以根据所使用的指示器指示等待时长时，用户无法与该应用交互。

![在 HoloLens 进度环示例](images/HoloLens2_Loader.gif)<br>
*在 HoloLens 进度环示例*

## <a name="types-of-progress"></a>进度类型

请务必提供有关发生了什么情况的用户信息。 混合现实中的用户可以轻松地分心物理环境或对象如果您的应用程序不会不提供很好可视反馈。 对于需要几秒钟的情况下，更新此类加载数据时或场景，而是显示可视的指示器的好办法。 有两个选项向用户显示操作正在进行 –**进度栏**或**进度环**。

### <a name="progress-bar"></a>进度栏

![在 HoloLens 的进度栏示例](images/640px-progressbar.jpg)

进度栏显示的任务已完成的百分比。 它应在其持续时间已知 （确定），操作过程中，但其进度不应阻止与应用的用户的交互。

### <a name="progress-ring"></a>进度环

![在 HoloLens 进度环示例](images/640px-progressring.jpg)

采用进度环仅拥有不确定状态，并阻止任何进一步的用户交互，直到操作完成时，应使用。

### <a name="progress-with-a-custom-object"></a>与自定义对象的进度

![使用自定义网格示例中 HoloLens 进度](images/640px-progresscustom.jpg)

可以通过自定义您自己自定义的二维/三维对象将进度控件添加到你的应用的个性和品牌标识。

## <a name="best-practices"></a>最佳做法
* 紧密耦合[公告板或尾随](billboarding-and-tag-along.md)用于显示进度，因为用户可以轻松地将其头移到空白区域，并会丢失上下文。 您的应用程序可能看起来它已崩溃如果用户无法看到任何内容。 Billboarding 和尾随内置进度预设。
* 最好始终提供有关用户所发生的状态信息。 进度预设可提供各种视觉样式，包括提供状态的 Windows 标准的环式类型进度。 如果您希望的样式的进度以与你的应用的品牌保持一致，还可以通过将动画使用自定义的网格。

## <a name="see-also"></a>请参阅
* [进度脚本和混合现实工具包的预设](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [边界框](app-bar-and-bounding-box.md)
* [可交互对象](interactable-object.md)
* [对象集合](object-collection.md)
* [公告和尾随](billboarding-and-tag-along.md)
