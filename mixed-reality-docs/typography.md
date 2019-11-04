---
title: 版式
description: 文本是在应用程序体验中提供信息的重要元素。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality，设计，样式，字体，版式，ui，ux
ms.openlocfilehash: 9664d355e941d800ac1ac862860fc5889b6b7686
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437418"
---
# <a name="typography"></a>版式

![HoloLens 中的版式示例](images/typography-cover.png)<br>


文本是在应用程序体验中提供信息的重要元素。 就像2D 屏幕上的版式一样，目标应清晰且易懂。 由于混合现实有三个维度，文本和整体用户体验甚至可能会受到更大影响。

当我们谈到3D 中的类型时，我们倾向于容量耗尽3D 文本。 除了某些标识设计和一些其他有限的应用程序，延伸文本往往会降低文本的可读性。 尽管我们正在设计3D 体验，但我们对类型使用2D，因为它更清晰且更易于阅读。

在 HoloLens 中，类型是使用基于附加颜色系统的轻型的影像构建的。 就像其他全息影像一样，可以将类型放在实际的环境中，在该环境中，可以从任何角度进行世界锁定和观察。 类型和环境之间的[视差](https://en.wikipedia.org/wiki/Parallax)效果也增加了体验的深度。

## <a name="typography-in-mixed-reality"></a>混合现实中的版式

混合现实中的版式规则与其他任何地方都没有什么不同。 物理世界和虚拟世界中的文本都需要更清晰且更易读。 文本可能位于墙上，或在物理对象上重叠。 它可以与数字用户界面一起浮动。 无论使用何种上下文，我们都将使用相同的印刷规则来进行读取和识别。

### <a name="create-clear-hierarchy"></a>创建清晰的层次结构

使用不同类型的大小和权重生成对比度和层次结构。 在整个应用程序体验中定义类型斜坡并遵循它将提供具有一致的信息层次结构的丰富用户体验。

![类型斜坡示例](images/typography-ramp-1000px.jpg)<br>
*定义类型斜坡，并在整个应用体验中执行*

### <a name="limit-your-fonts"></a>限制字体

避免在一个上下文中使用两个以上的不同字体系列。 这会破坏你的体验的协调和一致性，并使其难以使用信息。 在 HoloLens 中，由于信息是在物理环境上重叠的，因此使用太多字体样式会降低体验。 Segoe UI 是所有 Microsoft 数字设计的字体。 它在 Windows Mixed Reality shell 中一致地使用。 您可以从[Windows 设计工具包页](https://docs.microsoft.com/windows/uwp/design-downloads/)下载 Segoe UI 的字体文件。

[有关 Segoe UI 字样的详细信息](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>避免精简字体粗细

避免在42pt 下为类型大小使用光源或 semilight 字体粗细，因为精简垂直笔划将振动并降低清晰度。 具有足够笔划粗细的新式字体很好地运行。 例如，在使用常规或粗体权重时，Arial 和 Arial 非常清晰。

### <a name="color"></a>颜色

在 HoloLens 中，由于全息影像是使用加法光源系统构建的，因此白色文本非常清晰。 你可以在 "开始" 菜单和应用栏上找到白色文本的示例。 即使在不使用 HoloLens 的背面的情况下白色文本也能正常工作，复杂的物理背景也可能使类型难以阅读。 若要改善用户的注意力并将干扰从物理背景中降到最低，我们建议在黑色或彩色背面使用白色文本。

<br>


![建议在黑色或彩色背面使用白色文本。*在黑色或彩色背面](images/typography-whiteonblack2-1000px.jpg)
白色文本的示例。*
<br>

若要使用深色文本，您应该使用一个亮点，使其可供阅读。 在 "附加颜色系统" 中，黑色显示为透明。 这意味着，如果没有彩色的背面印版，将无法看到黑色文本。

:::row:::
    :::column:::
        ![黑色文本示例](images/typography-whiteonblack.png)<br>
        *白底黑白色文本的示例*<br>
    :::column-end:::
    :::column:::
        ![黑色文本示例](images/640px-typography-blackonwhite.jpg)<br>
        *系统应用中的黑色文本示例-存储和设置*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>建议的字体大小

正如你所料，在电脑或平板电脑设备上使用的类型大小（通常介于12到32pt 之间）看上去相当小，距离为2米。 这取决于每种字体的特征，但通常情况下，建议的最小查看角度和清晰度的字体高度基于用户研究研究的0.35 °/12.21-13.97mm。 与 Unity 页面的[文本中](text-in-unity.md)引入的缩放系数大约为 35-40pt。 

对于 0.45 m （45cm）的接近交互，最小清晰字体的查看角度和高度为0.4 °-0.5 °/3.14 –3.9 毫米。 这是关于在[Unity 文本中](text-in-unity.md)引入缩放系数的大约 9 12pt。

*在近和远交互范围](images/typography-distance-1000px.jpg)
内容*![近和远交互范围

### <a name="the-minimum-legible-font-size"></a>最小清晰字体大小
| 长途 | 查看角度 | 文本高度 | 字号 * * |
|---------|---------|---------|---------|
| 45cm （直接操作距离） | 0.4 °-0.5 ° | 3.14 –3.9 毫米 | 8.9-11.13 pt |
| 2m | 0.35 °0.4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>可读性更清晰的字号
| 长途 | 查看角度 | 文本高度 | 字号 * * |
|---------|---------|---------|---------|
| 45cm （直接操作距离） | 0.65 °0.8 ° | 5.1-6.3 毫米 | 14.47-17.8 pt |
| 2m | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |


Segoe UI （Windows 的默认字体）在大多数情况下都适用。 不过，请避免使用较小尺寸的轻型或半字形系列，因为精简垂直笔划将振动，并将降低清晰度。 具有足够笔划粗细的新式字体很好地运行。 例如，Arial 和 Arial 外观丰富多彩，在 HoloLens 中以常规或粗体权重非常清晰。

**有关 Unity 中文本大小计算的详细信息，请参阅[unity 中的文本](text-in-unity.md)**

![查看角度](images/Text_In_Unity_ViewingAngle.jpg)
*查看距离、角度和文本高度*

<br>

---

## <a name="resources"></a>资源

:::row:::
    :::column:::
    ### <a name="segoe-fontshttpsdownloadmicrosoftcomdownload1bc1bcf071a-78ee-4968-acbe-15461c274b61segoe20fonts20v1705zipbr"></a>[宋体](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    （Zip 文件）<br>
    ### <a name="hololens-fonthttpsdownloadmicrosoftcomdownload38d38d659e2-4b9c-413a-b2e7-1956181dc427hololens20fontzipbr"></a>[HoloLens 字体](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    （Zip 文件）<br>
    <br>
    *映像： HoloLens 字体提供 Windows Mixed Reality 中使用的符号字形。*
    :::column-end:::
        :::column:::
        ![HoloLens 字体提供 Windows Mixed Reality 中使用的符号字形](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="see-also"></a>另请参阅
* [Unity 中的文本](text-in-unity.md)
* [颜色、光线和材料](color,-light-and-materials.md)
