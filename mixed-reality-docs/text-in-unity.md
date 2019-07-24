---
title: Unity 中的文本
description: '若要在 Unity 中显示文本, 可以使用两种类型的文本组件: UI 文本和三维文本网格。'
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, 设计, 控件, 字体, 版式, ui, ux
ms.openlocfilehash: f57b04c7d57219b7426793879004ef010d2b1ea8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415435"
---
# <a name="text-in-unity"></a>Unity 中的文本

文本是全息应用中最重要的组件之一。 若要在 Unity 中显示文本, 可使用三种类型的文本组件: UI 文本、三维文本网格和文本网格 Pro。 默认情况下, UI 文本和三维文本网格显示模糊并且太大。 需要调整几个变量, 以获取在 HoloLens 中具有可管理的大小的高质量文本。 通过在使用 UI 文本和3D 文本网格组件时应用缩放因子以获取适当的维度, 可以获得更好的呈现质量。

![如何获取明锐而漂亮的文本](images/hug-text-02-640px.png)<br>
*Unity 中的默认文本模糊*

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a>使用 Unity 的3D 文本 (文本网格) 和 UI 文本

Unity 假设添加到场景的所有新元素都是大小为1个 Unity 单元, 或 100% 的转换比例, 这将转换为在 HoloLens 上约1米。 对于字体, 默认情况下, 3D TextMesh 的边界框在大约1米的高度内进入。

![在 Unity 中使用字体](images/640px-hug-text-03.png)<br>
*默认 Unity 3D 文本 (文本网格) 占用1个的 Unity 单元*

<br>
大多数可视化设计器使用点来定义真实环境中的字体大小。 1米内有大约 2835 (2, 834.645666399962) 点。 根据点系统转换为1米和 Unity 的默认文本网格字体大小 13, 将13除以2835等于 0.0046 (0.004586111116) 的简单数学计算法为开始提供良好的标准缩放 (某些可能需要舍入到 0.005)。 在设计程序中, 将文本对象或容器缩放为这些值不仅会允许1:1 转换字体大小, 而且还可以提供标准, 以便您可以保持整个体验的一致性。

![具有不同字体大小的 Unity 3D 文本网格](images/Text_In_Unity_Measurements1.png)<br>
*Unity 3D 文本和 UI 文本的缩放值*

![具有不同字体大小的 Unity 3D 文本网格](images/hug-text-05-1000px.png)<br>
*包含优化值的 Unity 3D 文本网格*

<br>
将基于 UI 或画布的文本元素添加到场景时, 大小差异仍为大于。 这两种大小的差异大约为 1000%, 这会使基于 UI 的文本组件的缩放因子为 0.00046 (0.0004586111116 为精确) 或0.0005 作为舍入值。

![每个单位值具有不同动态像素的 Unity UI 文本](images/hug-text-04-1000px.png)<br>
*包含优化值的 Unity UI 文本*

<br>

>[!NOTE]
>任何字体的默认值都可能受该字体的纹理大小或字体导入到 Unity 的方式影响。 这些测试是根据 Unity 中默认的 Arial 字体以及另一个导入的字体来执行的。

## <a name="working-with-text-mesh-pro"></a>使用文本网格 Pro

通过 Unity 的文本网格 Pro, 可以保护文本呈现质量。 它支持简洁文本大纲, 而不考虑使用[.sdf (带符号距离字段)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)技术的距离。 使用上文用于3D 文本网格和 UI 文本的相同计算方法, 我们可以找到适当的缩放值以使用传统的排版点。 由于大小为36的默认3D 文本网格 Pro 字体显示 2.5 Unity 单元 (2.5 m) 的边界, 因此, 我们可以使用缩放值0.005 来使用点大小。 UI 菜单下的文本网格 Pro 的默认边界大小为25个 Unity 单元 (25m)。 这为缩放值提供了0.0005。

![具有不同字体大小的 Unity 3D 文本网格](images/Text_In_Unity_Measurements2.png)<br>
*Unity 3D 文本和 UI 文本的缩放值*

## <a name="recommended-text-size"></a>建议的文本大小
正如你所料, 在电脑或平板电脑设备上使用的类型大小 (通常介于12到32pt 之间) 看上去相当小, 距离为2米。 这取决于每种字体的特征, 但通常情况下, 建议的最小查看角度和清晰度的字体高度基于用户研究研究的0.35 °/12.21-13.97mm。 大约有35个 40pt, 其中包含上述缩放系数。 

对于 0.45 m (45cm) 的接近交互, 最小清晰字体的查看角度和高度为0.4 °-0.5 °/3.14 –3.9 毫米。 它大约为 9-12pt, 其中包含上述缩放系数。

![近和远交互范围](images/typography-distance-1000px.jpg)
内的近和远交互范围*内容*

### <a name="the-minimum-legible-font-size"></a>最小清晰字体大小
| 长途 | 查看角度 | 文本高度 | 字号 |
|---------|---------|---------|---------|
| 45cm (直接操作距离) | 0.4 °-0.5 ° | 3.14 –3.9 毫米 | 8.9-11.13 pt |
| 2m | 0.35 °0.4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>可读性更清晰的字号
| 长途 | 查看角度 | 文本高度 | 字号 |
|---------|---------|---------|---------|
| 45cm (直接操作距离) | 0.65 °0.8 ° | 5.1-6.3 毫米 | 14.47-17.8 pt |
| 2m | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |

Segoe UI (Windows 的默认字体) 在大多数情况下都适用。 不过, 请避免使用较小尺寸的轻型或半字形系列, 因为精简垂直笔划将振动, 并将降低清晰度。 具有足够笔划粗细的新式字体很好地运行。 例如, Arial 和 Arial 外观丰富多彩, 在 HoloLens 中以常规或粗体权重非常清晰。


![查看角度](images/Text_In_Unity_ViewingAngle.jpg)
*查看距离、角度和文本高度*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>用适当的尺寸锐化文本呈现质量

根据这些缩放因素, 我们已[使用 UI 文本和3D 文本网格创建了文本 prototyping](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)。 开发人员可以使用这些 prototyping 来获得清晰的文本和一致的字体大小。

![用适当的尺寸锐化文本呈现质量](images/hug-text-06-1000px.png)<br>
*用适当的尺寸锐化文本呈现质量*

## <a name="shader-with-occlusion-support"></a>具有封闭支持的着色器

Unity 的默认字体材料不支持封闭。 因此, 默认情况下, 你会看到对象后面的文本。 我们包含了一个[支持封闭的简单着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)。 下图显示了文本, 其中包含默认字体材料 (左侧) 和具有适当封闭 (右) 的文本。

![具有封闭支持的着色器](images/hug-text-07-1000px.png)<br>
*具有封闭支持的着色器*


## <a name="see-also"></a>请参阅
* [MRTK 中的文本 Prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [版式](typography.md)

 
