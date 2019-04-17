---
title: MRTK 包
description: 本指南介绍了构成 Microsoft 混合现实 Toollkit 的包。
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality MRTK，组件，包
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592976"
---
# <a name="mrtk-packages"></a>MRTK 包

混合现实工具包 (MRTK) 是通过混合现实的硬件和平台提供支持，组件化的方式实现跨平台混合现实应用程序开发的包的集合。

有三种类别的 MRTK 包： 

* [Foundation](#foundation-packages)
* [扩展](#extension-packages)
* [Experimental](#experimental-packages)

## <a name="foundation-packages"></a>Foundation 包

混合现实工具包 Foundation 是使应用程序能够在混合现实平台上利用常用功能的包的组。 这些包发布并受 Microsoft 支持中源代码[mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) GitHub 上的分支。

![MRTK Foundation 包](images/mrtk-foundation.jpg)

*混合的现实工具包 Foundation 包*

MRTK Foundation 组成：

* [核心包](#core-package)
* [平台提供商](#platform-providers)
* [系统服务](#system-services)
* [功能资产](#feature-assets)

以下部分介绍类型的每个类别中的包。

### <a name="core-package"></a>核心包

核心包是_需_组件并且使所有 MRTK foundation 包作为依赖项。

MRTK Core 包包括：

* [公共接口、 类和数据类型](#common-interfaces-clases-and-data-types)
* [MixedRealityToolkit 场景组件](#mixedrealitytoolkit-scene-component)
* [MRTK 标准着色器](#mrtk-standard-shader)
* [Unity 输入提供程序](#unity-input-provider)
* [包管理](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a>公共接口、 类和数据类型

混合现实工具包核心包包含所有公共接口，类和所有其他组件使用的数据类型的定义。 强烈建议应用程序以独占方式通过定义的接口来实现跨平台兼容性的最高级别访问 MRTK 组件。

#### <a name="mixedrealitytoolkit-scene-component"></a>MixedRealityToolkit 场景组件

MixedRealityToolkit 场景组件是混合现实工具包的单一、 集中式资源管理器。 此组件将加载和管理的平台和服务模块的有效期并提供系统用于访问其配置设置的资源。 

#### <a name="mrtk-standard-shader"></a>MRTK 标准着色器

MRTK 标准着色器提供几乎所有 MRTK 所提供的材料的基础。 此着色器是极其灵活、 更优化的各种 MRTK 受支持的平台。 它是_高度_建议应用程序的材料使用 MRTK 标准着色器以获得最佳性能。

#### <a name="unity-input-provider"></a>Unity 输入提供程序

Unity 输入提供程序提供游戏控制器、 触摸屏和 3D 空间鼠标等常见的输入设备的访问权限。

#### <a name="package-management"></a>程序包管理

_即将发布_

混合现实工具包核心包提供发现和管理可选 foundation、 扩展和实验性 MRTK 包的支持。

### <a name="platform-providers"></a>平台提供商

MRTK 平台提供程序包是启用的混合现实目标混合现实硬件工具包和平台功能的组件。

支持的平台包括：

* [Windows Mixed Reality](#windows-mixed-reality)
* [OpenVR](#openvr)
* [Windows Voice](#windows-voice)

#### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Windows Mixed Reality 包为 Microsoft HoloLens 和 Windows 混合现实沉浸式设备提供支持。 包中包含完整的平台支持，包括：

* 目标的视线移动
* 笔势
* Windows 混合现实运动控制器
* 空间映射

#### <a name="openvr"></a>OpenVR

OpenVR 包提供了硬件和平台支持使用 OpenVR 平台的设备。

#### <a name="windows-voice"></a>Windows 语音

Windows 语音包为 Microsoft Windows 10 设备上的关键字识别和听写倾注功能提供支持。

### <a name="system-services"></a>系统服务

系统服务包中提供了核心平台服务。 这些程序包包含混合现实工具包的默认实现中定义的系统服务接口[core](#core-package)包。

MRTK foundation 包括以下系统服务：

* [边界系统](#boundary-system)
* [诊断系统](#diagnostic-system)
* [在输入的系统](#input-system)
* [空间感知系统](#spatial-awareness-system)
* [Teleport 系统](#teleport-system)

#### <a name="boundary-system"></a>边界系统

MRTK 边界系统提供了有关为虚拟现实数据 playspace。 在系统上为其用户已配置边界，系统可以提供 floor 平面、 矩形 playspace、 跟踪的区域和的详细信息。

#### <a name="diagnostic-system"></a>诊断系统

MRTK 诊断系统提供了您的应用程序体验中的实时性能数据。 在速览，你将能够查看帧速率、 处理器时间百分比和其他关键性能指标，如使用你的应用程序。

#### <a name="input-system"></a>在输入的系统

MRTK 输入系统使应用程序可以通过指定用户操作并将这些操作分配给最合适的按钮和目标控制器上的轴访问跨平台的方式的输入。

#### <a name="spatial-awareness-system"></a>空间感知系统

MRTK 空间感知系统使实际环境数据访问可以从 Microsoft HoloLens 等设备。

#### <a name="teleport-system"></a>Teleport 系统

MRTK Teleport 系统提供了虚拟现实 locomotion 支持。

### <a name="feature-assets"></a>功能资产

功能资产是作为 Unity 资产和脚本提供的相关功能的集合。 其中一些功能包括：

* 用户界面控件
* 标准资产
* more

## <a name="extension-packages"></a>扩展包

MRTK 扩展包是由 Microsoft 和社区编写的扩展和增强功能的混合现实工具包的包的集合。 扩展创建者将状态所需依赖项，请将标记为与混合现实工具包兼容包和提供许可，支持语句。

扩展包可能会提供新功能和新的平台支持。 随着时间推移，扩展可能，协助和批准的作者，迁移到 MRTK Foundation 此时它们将是发布，并且受 Microsoft 支持。

![MRTK 扩展包](images/mrtk-extensions.jpg)

*混合的现实工具包扩展包*

## <a name="experimental-packages"></a>实验性包

实验性包提供的功能对航班原型功能、 预发布版本和令人兴奋的新创意。 最实验性包的目标是尝试新事物，也可以衡量客户的兴趣。 很多，但并非所有实验性的包将扩展的形式重新发布原型制作和测试阶段完成之后。

![MRTK 实验性包](images/mrtk-experimental.jpg)

*混合的现实工具包实验性包*

## <a name="conclusion"></a>结束语

混合现实 Toolkit 软件包和程序包管理系统旨在启用简洁明了的方法，以便附加功能构建到你的体验而不需要不必要的组件要包含到项目。

随着时间推移，将添加并增强在混合现实 Toolkit 包管理支持。 如果有任何反馈，或者想要参与此计划，请访问[混合现实工具包项目](https://github.com/Microsoft/MixedRealityToolkit-Unity)GitHub 上。 

## <a name="see-also"></a>请参阅

* [MixedRealityToolkit-Unity (GitHub)](https://github.com/Microsoft/MixedRealityToolkit-Unity)

