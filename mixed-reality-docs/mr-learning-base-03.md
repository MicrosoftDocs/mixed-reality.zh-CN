---
title: 入门教程 - 3. 配置 MRTK 配置文件
description: 本课程介绍如何使用混合现实工具包 (MRTK) 创建混合现实应用程序。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.localizationpriority: high
ms.openlocfilehash: d3381241bb1418fb0e1fb7e5d29d552a533faa32
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376639"
---
# <a name="3-configuring-the-mrtk-profiles"></a>3.配置 MRTK 配置文件

## <a name="overview"></a>概述

在本教程中，你将学习如何自定义和配置 MRTK 配置文件。

此特定示例将演示如何通过更改空间网格观察程序的设置来隐藏空间感知网格。 但是，可以按照相同的原则来自定义 MRTK 配置文件中的任何设置或值。

## <a name="objectives"></a>目标

* 了解如何自定义和配置 MRTK 配置文件
* 隐藏空间感知网格

## <a name="changing-the-spatial-awareness-display-option"></a>更改空间感知显示选项

隐藏空间感知网格所要执行的主要步骤如下：

1. 克隆默认的配置配置文件
2. 启用空间感知系统
3. 克隆默认的空间感知系统配置文件
4. 克隆默认的空间感知网格观察程序配置文件
5. 更改空间感知网格的可见性

> [!NOTE]
> 默认情况下，MRTK 配置文件不可编辑。 这是一些默认的配置文件模板，必须先克隆它们，然后才能对其进行编辑。 配置文件有多个嵌套层。 因此，在配置一个或多个设置时，常见的做法是克隆然后编辑多个配置文件。

### <a name="1-clone-the-default-configuration-profile"></a>1.克隆默认的配置配置文件

> [!NOTE]
> 配置配置文件是顶级配置文件。 因此，若要编辑任何其他配置文件，必须先克隆配置配置文件。

在“层次结构”窗口中，选择 MixedRealityToolkit 对象，然后在检查器窗口中将“MixedRealityToolkit”配置配置文件更改为“DefaultHoloLens2ConfigurationProfile”：

![mr-learning-base  ](images/mr-learning-base/base-03-section1-step1-1.png)

在仍选中了“MixedRealityToolkit”对象的情况下，在检查器窗口中单击“复制和自定义”按钮打开“克隆配置文件”窗口： 

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_HoloLens2ConfigurationProfile），然后单击“克隆”按钮，创建“DefaultHololens2ConfigurationProfile”的可编辑副本 ：

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

新建的配置配置文件现已分配为场景中的配置配置文件：

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

在 Unity 菜单中，选择“文件” > “保存”以保存场景。 

> [!TIP]
> 在学习整篇教程的过程中，请记得保存自己的工作。

### <a name="2-enable-the-spatial-awareness-system"></a>2.启用空间感知系统

在“层次结构”窗口中，选择 MixedRealityToolkit 对象，接下来在检查器窗口中，选择“空间感知”选项卡，然后选中“启用空间感知系统”复选框：  

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3.克隆默认的空间感知系统配置文件

在“空间感知”选项卡中，单击“克隆”按钮打开“克隆配置文件”窗口： 

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessSystemProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessSystemProfile”的可编辑副本 ：

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

新建的空间感知系统配置文件现已自动分配到你的配置配置文件：

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4.克隆默认的空间感知网格观察程序配置文件

在仍然选中了“空间感知”选项卡的情况下，展开“Windows Mixed Reality 空间网格观察程序”部分，然后单击“克隆”按钮打开“克隆配置文件”窗口：  

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

在“克隆配置文件”窗口中，输入合适的配置文件名（例如 GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile），然后单击“克隆”按钮，创建“DefaultMixedRealitySpatialAwarenessMeshObserverProfile”的可编辑副本 ：

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

新建的空间感知网格观察程序配置文件现已自动分配到你的空间感知系统配置文件：

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5.更改空间感知网格的可见性

在“空间网格观察程序设置”中，将“显示选项”更改为“遮挡”，使空间映射网格在隐藏状态下正常运行：  

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> 尽管空间映射网格不可见，但它依然存在且可正常运行。 例如，空间映射网格后面的任何全息影像（如真实墙壁后面的全息影像）将不可见。

你已了解如何修改 MRTK 配置文件中的设置。 可以看到，若要自定义 MRTK 设置，首先需要创建默认配置文件的副本。 由于默认配置文件不可编辑，因此，应始终保留这些配置文件，以便在还原为默认设置时参考。 若要详细了解 MRTK 配置文件及其体系结构，可参阅 [MRTK 文档门户](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)中的 [MRTK 配置文件配置指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)。

## <a name="congratulations"></a>祝贺

在本教程中，你学习了如何克隆、自定义和配置 MRTK 配置文件和设置。

[下一教程：4.定位场景中的对象](mr-learning-base-04.md)
