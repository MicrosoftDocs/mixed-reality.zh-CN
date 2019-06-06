---
title: 版式
description: 文本是用于在您的应用体验中提供信息的重要元素。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 样式、 字体、 版式、 ui、 用户体验
ms.openlocfilehash: debf125a7f82ac79fe3ad776ba9c8c0b69396848
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692364"
---
# <a name="typography"></a>版式

文本是用于在您的应用体验中提供信息的重要元素。 就像在二维屏幕上的版式，目标是清晰、 可读。 与混合现实的三维方面，还有机会来影响文本和整体用户体验更大的方式。

![HoloLens 中的版式示例](images/typography-cover.png)<br>
*HoloLens 中的版式示例*

当我们谈及以三维形式的类型时，我们往往认为拉伸、 容量耗尽三维文字。 除了一些标识设计和其他几个限制应用程序，拉伸的文本往往会降低文字的可读性。 尽管我们对于三维设计体验，我们使用 2D 类型因为它是更清晰、 更易于读取。

在 HoloLens，与使用基于累加性颜色系统上的光线全息构造类型。 就像其他全息类型可以放置在实际环境中它可以被锁定，从任意角度观察到的世界。 [视差](https://en.wikipedia.org/wiki/Parallax)类型和环境之间的效果还添加深度的体验。

## <a name="typography-in-mixed-reality"></a>混合现实中的版式

混合现实中的版式规则均与其他任何位置没有什么不同。 物理环境和虚拟世界中的文本必须是清晰可读。 文本可能是在墙上或在物理对象上叠加。 它无法浮点数字的用户接口。 而不考虑在上下文中，我们将应用用于读取和识别相同的版式规则。

### <a name="create-clear-hierarchy"></a>创建清晰的层次结构

通过使用不同类型的大小和权重对比度和层次结构生成。 定义类型负载增加并遵循它在整个应用程序体验将提供与一致信息层次结构的出色用户体验。

![类型负载增加示例](images/typography-ramp-1000px.jpg)<br>
*定义类型负载增加并遵循它在整个应用程序体验*

### <a name="limit-your-fonts"></a>限制您的字体

避免在单个上下文中使用超过两个不同的字体系列。 这将中断的协调性和您的体验的一致性，并使其难以使用的信息。 在 HoloLens，由于信息叠加基于物理环境中，使用太多的字体样式会降低体验。 Segoe UI 是所有 Microsoft 数字设计的字体。 它始终使用 Windows Mixed Reality shell 中。 您可以下载 Segoe UI 字体文件从[Windows 设计工具包页](https://docs.microsoft.com/windows/uwp/design-downloads/)。

[有关 Segoe UI 字样的详细信息](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>避免细的字体粗细

避免由于精简垂直笔画将振动，降低以增强可读性类型大小 42pt 下使用浅色或 semilight 字体粗细。 最新版本，如果有足够笔画粗细能正常工作。 例如，Helvetica，arial 字体是非常清晰 HoloLens 中使用常规或加粗的加权值。

### <a name="color"></a>颜色

在 HoloLens，因为全息构造具有累加性的照明系统，白色文本是高清晰。 您可以找到在开始菜单和应用栏上的白色文本的示例。 即使白色文本处理而背板无 HoloLens，复杂的物理背景可以使类型难以读取。 若要提高用户的焦点并从物理后台干扰降至最低，我们建议使用深色或返回彩色盘子上的白色文本。

<br>


![我们建议使用深色或带颜色的背板上的白色文本。](images/typography-whiteonblack2-1000px.jpg)
*深色或带颜色的背板上的白色文本的示例。*
<br>

若要使用深文本，应使用明亮的背板使它易读。 在加法颜色系统中，黑色被显示为透明效果。 这意味着你将无法再看到黑色文本而无需彩色后面板。

![黑色文本示例](images/typography-whiteonblack.png)
<br>*背面的白色和黑色，白色文本的示例*


![黑色文本示例](images/640px-typography-blackonwhite.jpg)
<br>*系统应用程序-应用商店和设置中的黑色文本的示例*

## <a name="recommended-font-size"></a>建议的字号

正如您期望的我们使用一台 PC 或平板电脑设备 （通常为 12 – 32pt) 的类型大小相当小看 2 米的距离。 这取决于每个字体的特征但一般情况下查看角度和可读性较高的字体高度推荐的最小围绕 0.35°-0.4°/12.21-13.97mm 基于我们用户调查研究。 而是关于 35 40pt 与上面介绍的缩放因子。 

对于在 0.45m(45cm) 的近交互，最小清晰字体的视角和高度为 0.4 °-0.5 ° / 3.14 – 3.9 mm。 而是关于 9 12 磅与上面介绍的缩放因子。

![近和远的交互范围](images/typography-distance-1000px.jpg)
*内容在近和远的交互范围*

### <a name="the-minimum-legible-font-size"></a>最小清晰的字体大小
| 距离 | 视角 | 文本高度 | 字体大小 * * |
|---------|---------|---------|---------|
| 45 cm （直接操作距离） | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>轻松清晰的字体大小
| 距离 | 视角 | 文本高度 | 字体大小 * * |
|---------|---------|---------|---------|
| 45 cm （直接操作距离） | 0.65°-0.8° | 5.1-6.3mm | 14.47-17.8pt |
| 2m | 0.6°-0.75° | 20.9-26.2mm | 59.4-74.2pt |


Segoe UI （Windows 默认字体） 非常适合大多数情况。 但是，避免使用 light 或半浅色字体系列以小的尺寸，由于精简垂直笔画将振动，它将会降低以增强可读性。 最新版本，如果有足够笔画粗细能正常工作。 例如，Helvetica，Arial 查看丰富多彩和 HoloLens 中非常清晰的常规或加粗的权重。

* * 有关详细信息在 Unity 中计算的文本大小，请参阅页[Unity 中的文本](text-in-unity.md)

![查看角度](images/Text_In_Unity_ViewingAngle.jpg)
*查看距离、 角度和文本的高度*

## <a name="resources"></a>资源
* [Segoe 字体](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [HoloLens 字体](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![HoloLens 字体为您提供了在 Windows 混合现实中所使用的符号图标](images/300px-hololensmdl2symbols.jpg)
<br>*HoloLens 字体可在 Windows Mixed Reality 中使用的符号标志符号。*

## <a name="see-also"></a>请参阅
* [Unity 中的文本](text-in-unity.md)
* [颜色、光线和材料](color,-light-and-materials.md)
