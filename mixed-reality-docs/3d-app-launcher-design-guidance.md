---
title: 三维应用程序启动程序设计指南
description: 三维应用启动器是他们可以选择启动应用程序的用户的混合的现实房屋中的"物理"对象。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 三维应用程序启动程序、 沉浸式头戴式耳机、 实时的多维数据集
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590304"
---
# <a name="3d-app-launcher-design-guidance"></a>三维应用程序启动程序设计指南

放在 Windows Mixed Reality 沉浸式 (VR) 耳机上，输入的主页、 Windows Mixed Reality 可视化为房屋在由山脉和水包围 cliff (尽管您可以[选择其他环境，甚至创建您自己](add-custom-home-environments.md)). 在此空间内主页，用户可以随意排列和组织的三维对象和他们所关心任何需要的方式的应用。 一个**三维应用启动器**是在用户的"物理"对象的混合现实房屋，他们可以选择启动应用程序。

![示例：浮动鸟的 3D 应用程序启动器](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*浮动鸟的 3D 应用程序启动器示例 （虚构应用程序）*

## <a name="3d-app-launcher-creation-process"></a>三维应用程序启动器创建过程

有 3 个步骤创建的 3D 应用程序启动器：
1. 设计和 concepting （详见本文）
2. [建模和导出](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 将其集成到你的应用程序：
    * [UWP 应用](implementing-3d-app-launchers.md)
    * [Win32 应用](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>设计概念

### <a name="fantastic-yet-familiar"></a>太棒了，但熟悉

应用程序启动程序位于 Windows Mixed Reality 环境是一部分熟悉，一部分精巧/名工商管理学博士的办法。 最佳的启动器遵循这个世界中的规则。 将如何，您可以从你的应用，需要一个熟悉的、 有代表性的对象，但处理一些实际的现实的规则。 Magic 将导致。

### <a name="intuitive"></a>直观

当您查看应用程序启动程序时，其用途-若要启动你的应用-显然应该和不应造成任何混淆。 例如，请确保你启动器是您的应用程序不会混淆的一段 Cliff 住宅装潢明显足够的代表。 应用程序启动程序应邀请他人触摸/选择它。

![示例：全新注意三维应用程序启动程序](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*全新注意的 3D 应用程序启动器示例 （虚构应用程序）*

### <a name="home-scale"></a>家庭规模

三维应用启动器上实时 Cliff 住宅和其默认大小应意义与其他"物理"对象的空间中。 如果将应用启动器，说，房屋工厂或某些家具应感到在家里、 size-wise。 很好的起点是请参阅如何查看 30 三次方厘米，但请记住，用户可以缩放它向上或向下根据自己喜好。

### <a name="own-able"></a>可拥有的

应用程序启动程序应该感觉就像一个人会高兴能够在其空间中的对象。 它们将会几乎周围本身与这些内容，因此启动器应感觉像用户想法是不够理想，若要找出并保持附近。

![示例：太空式 Warp 的 3D 应用程序启动器](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*太空式 Warp 的 3D 应用程序启动器示例 （虚构应用程序）*

### <a name="recognizable"></a>可识别

三维应用程序启动程序应立即表达人员看不到"应用程序的品牌"。 如果应用程序中有一个星型字符或尤其是可识别的对象，我们建议使用它作为你的设计的重要组成部分。 在混合的现实情况下，对象将从用户比只是一个单独的徽标绘制更值得关注。 快速且明确，可识别对象进行通信的品牌。

### <a name="volumetric"></a>容量耗尽

您应用值得试用而不仅仅平面平面上将你的徽标和一周。 在启动程序应该感觉就像用户的空间中的令人兴奋、 3D、 物理对象。 一个不错的方法是假设您的应用程序将要 Macy 感恩节天入微中有一个气球。 问问自己，什么会真正 wow 人在其传入后在街？ 什么从所有的查看角度看很好？


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>很好的三维模型的提示

### <a name="best-practices"></a>最佳做法
* 在规划应用程序启动程序的维度，请给大约为 30 cm 多维数据集。 因此，1:1 对 1 的大小比率。
* 模型必须是 10,000 多边形。 [了解有关三角形计数和级别 (Lod) 的详细信息的详细信息](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 如有可能沉浸式头戴式上进行测试。
* 构建到模型的几何图形的详细信息，在可能的情况 – 不要依赖于纹理的详细信息。
* 生成"water 紧密"关闭几何图形。 未建模中没有漏洞。
* 在您的对象中使用自然的材料。 想象一下在现实生活中编写。
* 请确保您的模型读取在不同距离和大小。
* 当模型准备就绪，读取[导出资产准则](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)。

![具有细节纹理中的模型](images/20171013-143334-mixedreality-640px.jpg)<br>
*具有细节纹理中的模型*

### <a name="what-to-avoid"></a>要避免的问题
* 不要使用高对比度的详细信息或小忙的模式和纹理。
* 不要使用精简的几何图形 – 它不会工作在距离，并且别名错误。
* 不要让扩展模型的部分过多超出 1:1 对 1 的大小比率。 它将创建缩放问题。

![避免高对比度、 小忙模式](images/20171013-143603-mixedreality-640px.jpg)<br>
*避免高对比度、 小型、 忙模式*

## <a name="how-to-handle-type"></a>如何处理类型

### <a name="best-practices"></a>最佳做法
* 我们建议你的类型包括大约 1/3 的应用程序启动程序 （或多个）。 类型为可让人们了解应用启动器中这一事实，因此它很好的如果它是非常重大的启动是重点。
* 避免创建非常宽的类型 – 尝试使其保持范围内的应用启动器上核心维度 （增加或减少）。
* 平面类型可以起作用，但请注意，可能难以查看从特定的角度和在某些环境中。 您可以考虑将其放可靠对象或为帮助实现此其后的背景。
* 添加到你的类型的维度感觉很好以三维形式。 明暗度类型的方面一种不同的深颜色可帮助提高可读性。


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


**工作的类型颜色**
* 白色
* 黑色
* 半饱和的浅色

![工作的类型颜色。](images/20171016-112111-mixedreality-640px.jpg)<br>
*工作的类型颜色*

### <a name="what-to-avoid"></a>要避免的问题

**会造成问题的类型颜色**
* 中间色调
* 灰色
* 过度饱和的颜色或去除饱和度的颜色

![会造成问题的类型颜色。](images/20171016-112246-mixedreality-640px.jpg)<br>
*会造成问题的类型颜色*

## <a name="lighting"></a>照明

为应用程序启动程序照明来自 Cliff 房屋环境。 请确保在整个房屋的多个位置测试你启动程序，以便它看起来不错中光和阴影。 好消息是，如果已按照本文档中的其他设计指南，你启动器应该非常顺利 Cliff 房屋中大多数照明。

若要测试如何在各种系统正常运行的环境中查找你启动器可作为比较好 Studio 中，媒体文件室，任意位置外部的回阳台使用 （与在草坪具体区域）。 另一个很好的测试是将其放入半光和一半阴影并查看其外观。

![请确保您启动程序看起来不错中光和阴影。](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*请确保您启动程序看起来不错中光和阴影*

## <a name="texturing"></a>纹理

### <a name="authoring-your-textures"></a>创作你的纹理

在三维应用程序启动程序的最终格式将.glb 文件，它由使用 PBR （以物理方式基于呈现） 管道。 这可以是一个困难的过程-现在是如果你尚未采用技术艺术家的好时机。 如果你是勇敢 DIY-嗯，花费的时间[研究和了解 PBR 术语](http://wiki.polycount.com/wiki/PBR)发生了什么情况实质上在开始之前将帮助你避免常见错误。 

![示例：新的笔记应用程序](images/pbr-freshnote1-640px-500px.png)<br>
*全新注意的 3D 应用程序启动器示例 （虚构应用程序）*

**建议使用创作工具**

我们建议使用[物质刷](https://www.allegorithmic.com/products/substance-painter)通过 Allegorithmic 编写最终文件。 如果您不熟悉创作中物质刷，此处的 PBR 着色[教程](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)。

(或者[3D Coat](https://3dcoat.com/home/)， [Quixel 套件 2](https://quixel.se/suite2/)，或[Marmoset Toolbag](https://www.marmoset.co/toolbag/)也有效，如果您更熟悉使用其中一种。)

### <a name="best-practices"></a>最佳做法

* 如果您的应用启动器对象为 PBR 创作的则应很简单地将其转换为 Cliff 房屋环境。
* 我们的着色器应为裸机/粗糙度的工作流 – Unreal PBR 着色器关闭传真。
* 导出你的纹理保持[建议的纹理大小](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines)记住。
* 请确保生成您实时光线的对象，这意味着：
    * 避免甜的阴影 – 或绘制的阴影
    * 避免纹理中的生成的照明
    * 使用创作包 PBR 材料之一来获取正确的映射生成我们的着色器

## <a name="see-also"></a>请参阅

* [创建主混合现实中使用三维模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [实现的 3D 应用程序启动器 （UWP 应用）](implementing-3d-app-launchers.md)
* [实现的 3D 应用程序启动器 （Win32 应用）](implementing-3d-app-launchers-win32.md)
