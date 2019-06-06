---
title: 在 Unity 中的文本
description: 若要显示的文本在 Unity 中，有两种类型的文本组件可以使用-UI 文本和三维文本网格。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，用于控制字体、 版式、 ui、 用户体验
ms.openlocfilehash: a601ab5ab5168f286a0935ca06eeec13022e1eee
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692329"
---
# <a name="text-in-unity"></a>在 Unity 中的文本

文本是全息版应用中的最重要的组件之一。 若要显示的文本在 Unity 中，有三种类型的文本组件可以使用-UI 文本三维文本网格和文本 Mesh Pro。 默认情况下 UI 文本和三维文本网格显示模糊，太大。 您需要调整几个变量，以获得 sharp、 高质量的文本中 HoloLens 有合理的大小。 可以通过应用缩放因子来获取正确的尺寸，使用 UI 文本和三维文本网格组件时，获得更好地呈现质量。

![如何获得 sharp 和美观的文本](images/hug-text-02-640px.png)<br>
*在 Unity 中的模糊的默认文本*

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a>使用 Unity 的三维文字 （文本网格） 和 UI 文本

Unity 假定所有的新元素添加到场景中大小或可以转换为大约 1 米 HoloLens 上的 100%转换小数位数 1 Unity 单元。 在字体的情况下的边界框三维 TextMesh 有默认情况下在大约 1 米的高度。

![使用 Unity 中的字体](images/640px-hug-text-03.png)<br>
*默认 Unity 三维文字 (文本 Mesh) 占用 1 Unity 单元即 1 米*

<br>
大多数的可视化设计器使用点来定义在现实生活中的字体大小。 有大约 2835 (2,834.645666399962) 中 1 米的点。 根据点系统转换为 1 米以及 Unity 的默认文本 Mesh 字体大小的 13，13 除以 2835年等于 0.0046 (0.004586111116 确切地) 的简单数学开始提供合适的标准扩展 （一些可能想要为 0.005 舍入）。 缩放文本对象或对这些值的容器将仅允许 1 对 1 转换字体的大小在设计程序中，但还提供了一个标准，因此您可以在你的体验整个维护一致性。

![Unity 3D 文本网格使用不同的字体大小](images/Text_In_Unity_Measurements1.png)<br>
*Unity 3D 文本和 UI 文本的缩放值*

![Unity 3D 文本网格使用不同的字体大小](images/hug-text-05-1000px.png)<br>
*Unity 3D 文本网格使用优化的值*

<br>
当将用户界面或画布的基于的文本元素添加到场景中，大小不一致会仍然为更高版本。 两种大小的差异是大约 1000年%，这会基于 UI 文本组件到 0.00046 (0.0004586111116 确切地) 显示比例系数或 0.0005 的舍入值。

![每单位值的不同动态像素与 unity UI 文本](images/hug-text-04-1000px.png)<br>
*使用优化值的 unity UI 文本*

<br>

>[!NOTE]
>相应的字体的默认值可能会受到该字体或字体如何导入 Unity 的纹理大小。 这些测试已执行基于在 Unity 中，默认 Arial 字体，以及其他已导入的一种字体。

## <a name="working-with-text-mesh-pro"></a>使用文本 Mesh Pro

使用 Unity 的文本 Mesh Pro，可以保护的文本呈现质量。 它支持无论距离使用清晰的文本轮廓[SDF （签名距离字段）](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)技术。 使用相同的我们上面使用的三维文本网格和 UI 文本的计算方法，我们可以找到正确的缩放值，使用传统版式点。 由于默认三维网格 Pro 文本字体大小 36 所示的 2.5 Unity Unit(2.5m) 边界，我们可以使用缩放值 0.005 使用点大小。 文本 Mesh Pro UI 菜单下有边界的 25 Unity Unit(25m) 大小的默认值。 这样，我们 0.0005 的缩放值。

![Unity 3D 文本网格使用不同的字体大小](images/Text_In_Unity_Measurements2.png)<br>
*Unity 3D 文本和 UI 文本的缩放值*

## <a name="recommended-text-size"></a>建议的文本大小
正如您期望的我们使用一台 PC 或平板电脑设备 （通常为 12 – 32pt) 的类型大小相当小看 2 米的距离。 这取决于每个字体的特征但一般情况下查看角度和可读性较高的字体高度推荐的最小围绕 0.35°-0.4°/12.21-13.97mm 基于我们用户调查研究。 而是关于 35 40pt 与上面介绍的缩放因子。 

对于在 0.45m(45cm) 的近交互，最小清晰字体的视角和高度为 0.4 °-0.5 ° / 3.14 – 3.9 mm。 而是关于 9 12 磅与上面介绍的缩放因子。

![近和远的交互范围](images/typography-distance-1000px.jpg)
*内容在近和远的交互范围*

### <a name="the-minimum-legible-font-size"></a>最小清晰的字体大小
| 距离 | 视角 | 文本高度 | 字体大小 |
|---------|---------|---------|---------|
| 45 cm （直接操作距离） | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2m | 0.35°-0.4° | 12.21–13.97mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>轻松清晰的字体大小
| 距离 | 视角 | 文本高度 | 字体大小 |
|---------|---------|---------|---------|
| 45 cm （直接操作距离） | 0.65°-0.8° | 5.1-6.3mm | 14.47-17.8pt |
| 2m | 0.6°-0.75° | 20.9-26.2mm | 59.4-74.2pt |

Segoe UI （Windows 默认字体） 非常适合大多数情况。 但是，避免使用 light 或半浅色字体系列以小的尺寸，由于精简垂直笔画将振动，它将会降低以增强可读性。 最新版本，如果有足够笔画粗细能正常工作。 例如，Helvetica，Arial 查看丰富多彩和 HoloLens 中非常清晰的常规或加粗的权重。


![查看角度](images/Text_In_Unity_ViewingAngle.jpg)
*查看距离、 角度和文本的高度*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>尖锐文本呈现质量与正确的维度

根据这些缩放比例系数，我们创建了[UI 文本和三维文本 Mesh 文本预设](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)。 开发人员可以利用这些预设可以清晰的文本和一致的字体大小。

![尖锐文本呈现质量与正确的维度](images/hug-text-06-1000px.png)<br>
*尖锐文本呈现质量与正确的维度*

## <a name="shader-with-occlusion-support"></a>与封闭支持的着色器

Unity 的默认字体材料不支持的阻挡物。 因此，将默认情况下看到对象后面的文本。 我们包含了一个简单[支持是封闭的着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)。 下图显示了与默认字体材料 （左） 文本以及用正确的阻挡物 （右） 的文本。

![与封闭支持的着色器](images/hug-text-07-1000px.png)<br>
*与封闭支持的着色器*


## <a name="see-also"></a>请参阅
* [在 MRTK 文本预设](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [版式](typography.md)

 
