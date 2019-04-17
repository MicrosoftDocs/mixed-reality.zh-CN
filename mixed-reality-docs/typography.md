---
title: 版式
description: 文本是用于在您的应用体验中提供信息的重要元素。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 样式、 字体、 版式、 ui、 用户体验
ms.openlocfilehash: b4bac35cbc412ec7102748350c2f5c1e236c2f7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592649"
---
# <a name="typography"></a>版式

文本是用于在您的应用体验中提供信息的重要元素。 就像在二维屏幕上的版式，目标是清晰、 可读。 与混合现实的三维方面，还有机会来影响文本和整体用户体验更大的方式。

![HoloLens 中的版式示例](images/640px-typography-hero2.jpg)<br>
*HoloLens 中的版式示例*

当我们谈及以三维形式的类型时，我们往往认为拉伸、 容量耗尽三维文字。 除了一些标识设计和其他几个限制应用程序，拉伸的文本往往会降低文字的可读性。 尽管我们对于三维设计体验，我们使用 2D 类型因为它是更清晰、 更易于读取。

在 HoloLens，与使用基于累加性颜色系统上的光线全息构造类型。 就像其他全息类型可以放置在实际环境中它可以被锁定，从任意角度观察到的世界。 [视差](https://en.wikipedia.org/wiki/Parallax)类型和环境之间的效果还添加深度的体验。

## <a name="typography-in-mixed-reality"></a>混合现实中的版式

混合现实中的版式规则均与其他任何位置没有什么不同。 物理环境和虚拟世界中的文本必须是清晰可读。 文本可能是在墙上或在物理对象上叠加。 它无法浮点数字的用户接口。 而不考虑在上下文中，我们将应用用于读取和识别相同的版式规则。

### <a name="create-clear-hierarchy"></a>创建清晰的层次结构

通过使用不同类型的大小和权重对比度和层次结构生成。 定义类型负载增加并遵循它在整个应用程序体验将提供与一致信息层次结构的出色用户体验。

![类型负载增加示例](images/typography-ramp-1000px.jpg)<br>
*类型负载增加示例*

### <a name="limit-your-fonts"></a>限制您的字体

避免在单个上下文中使用超过两个不同的字体系列。 这将中断的协调性和您的体验的一致性，并使其难以使用的信息。 在 HoloLens，由于信息叠加基于物理环境中，使用太多的字体样式会降低体验。 Segoe UI 是所有 Microsoft 数字设计的字体。 它始终使用 Windows Mixed Reality shell 中。 您可以下载 Segoe UI 字体文件从[Windows 设计工具包页](https://docs.microsoft.com/windows/uwp/design-downloads/)。

[有关 Segoe UI 字样的详细信息](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>避免细的字体粗细

避免由于精简垂直笔画将振动，降低以增强可读性类型大小 42pt 下使用浅色或 semilight 字体粗细。 最新版本，如果有足够笔画粗细能正常工作。 例如，Helvetica，arial 字体是非常清晰 HoloLens 中使用常规或加粗的加权值。

### <a name="color"></a>颜色

在 HoloLens，因为全息构造具有累加性的照明系统，白色文本是高清晰。 您可以找到在开始菜单和应用栏上的白色文本的示例。 即使白色文本处理而背板无 HoloLens，复杂的物理背景可以使类型难以读取。 若要提高用户的焦点并从物理后台干扰降至最低，我们建议使用深色或返回彩色盘子上的白色文本。

<br>


![我们建议使用深色或带颜色的背板上的白色文本。](images/typography-whiteonblack2-1000px.jpg)

我们建议使用深色或带颜色的背板上的白色文本。

<br>


![黑色文本示例](images/640px-typography-textcolors.jpg)

若要使用深文本，应使用明亮的背板使它易读。 在加法颜色系统中，黑色被显示为透明效果。 这意味着你将无法再看到黑色文本而无需彩色后面板。

<br>


![黑色文本示例](images/640px-typography-blackonwhite.jpg)

你可以在应用商店或设置等的 UWP 应用中找到黑色文本的示例。

## <a name="recommended-font-size"></a>建议的字号

![两个指标是用于显示文本的最佳距离。](images/typography-distance-1000px.jpg)

两个指标是用于显示文本的最佳距离。

由于混合的现实涉及三维深度，并不总是易于进行通信的字体的大小。 用户的舒适的两个指标是放置全息的最佳距离。 我们可以使用此距离作为基础来找出最佳的字体大小。

正如您期望的我们使用一台 PC 或平板电脑设备 （通常为 12 – 32pt) 的类型大小相当小看 2 米的距离。 这取决于每个字体的特征，但一般情况下，而无需笔划振动可读性较高的建议的最小类型大小为大约 30 pt。 如果您的应用程序应使用在近距离，可以使用较小类型的大小。 **点大小基于 Unity 的三维文本网格和 UI 文本。有关详细的指标和缩放比例，请参阅[Unity 中的文本](text-in-unity.md)。**

## <a name="resources"></a>资源
* [Segoe 字体](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [HoloLens 字体](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![HoloLens 字体为您提供了在 Windows 混合现实中所使用的符号图标](images/300px-hololensmdl2symbols.jpg)

HoloLens 字体可在 Windows Mixed Reality 中使用的符号标志符号。

## <a name="see-also"></a>请参阅
* [在 Unity 中的文本](http://holodocsfuture/index.php?title=Text_in_Unity&action=edit&redlink=1)
* [颜色、 光线和材料](color,-light-and-materials.md)
