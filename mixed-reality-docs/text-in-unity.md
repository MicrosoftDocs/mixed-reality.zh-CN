---
title: 在 Unity 中的文本
description: 若要显示的文本在 Unity 中，有两种类型的文本组件可以使用-UI 文本和三维文本网格。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计，用于控制字体、 版式、 ui、 用户体验
ms.openlocfilehash: 45037f27f68a19478fd56a6edc940fbe45ae7671
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326302"
---
# <a name="text-in-unity"></a>在 Unity 中的文本

文本是全息版应用中的最重要的组件之一。 若要显示的文本在 Unity 中，有两种类型的文本组件可以使用-UI 文本和三维文本网格。 默认情况下，它们显示模糊并且太大。 您需要调整几个变量，以获得 sharp、 高质量的文本中 HoloLens 有合理的大小。 可以通过应用缩放因子来获取正确的尺寸，使用 UI 文本和三维文本网格组件时，获得更好地呈现质量。

![如何获得 sharp 和美观的文本](images/hug-text-02-640px.png)<br>
*在 Unity 中的模糊的默认文本*

## <a name="working-with-fonts-in-unity"></a>使用 Unity 中的字体

Unity 假定所有的新元素添加到场景中大小或可以转换为大约 1 米 HoloLens 上的 100%转换小数位数 1 Unity 单元。 在字体的情况下的边界框三维 TextMesh 有默认情况下在大约 1 米的高度。

![使用 Unity 中的字体](images/640px-hug-text-03.png)<br>
*默认 Unity 文本占用 1 Unity 单元即 1 米*

<br>
大多数的可视化设计器使用点来定义在现实生活中的字体大小。 有大约 2835 (2,834.645666399962) 中 1 米的点。 根据点系统转换为 1 米以及 Unity 的默认文本 Mesh 字体大小的 13，13 除以 2835年等于 0.0046 (0.004586111116 确切地) 的简单数学开始提供合适的标准扩展 （一些可能想要为 0.005 舍入）。 缩放文本对象或对这些值的容器将仅允许 1 对 1 转换字体的大小在设计程序中，但还提供了一个标准，因此您可以维护整个应用程序或游戏的一致性。

![Unity 3D 文本网格使用不同的字体大小](images/hug-text-05-1000px.png)<br>
*Unity 3D 文本网格使用优化的值*

<br>
当将用户界面或画布的基于的文本元素添加到场景中，大小不一致会仍然为更高版本。 两种大小的差异是大约 1000年%，这会基于 UI 文本组件到 0.00046 (0.0004586111116 确切地) 显示比例系数或 0.0005 的舍入值。

![每单位值的不同动态像素与 unity UI 文本](images/hug-text-04-1000px.png)<br>
*使用优化值的 unity UI 文本*

<br>

>[!NOTE]
>相应的字体的默认值可能会受到该字体或字体如何导入 Unity 的纹理大小。 这些测试已执行基于在 Unity 中，默认 Arial 字体，以及其他已导入的一种字体。

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>尖锐文本呈现质量与正确的维度

根据这些缩放比例系数，我们创建了[UI 文本和三维文本 Mesh 文本预设](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)。 开发人员可以利用这些预设可以清晰的文本和一致的字体大小。

![尖锐文本呈现质量与正确的维度](images/hug-text-06-1000px.png)<br>
*尖锐文本呈现质量与正确的维度*

## <a name="shader-with-occlusion-support"></a>与封闭支持的着色器

Unity 的默认字体材料不支持的阻挡物。 因此，将默认情况下看到对象后面的文本。 我们包含了一个简单[支持是封闭的着色器](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders)。 下图显示了与默认字体材料 （左） 文本以及用正确的阻挡物 （右） 的文本。

![与封闭支持的着色器](images/hug-text-07-1000px.png)<br>
*与封闭支持的着色器*

## <a name="recommended-type-size"></a>建议的类型大小

正如您期望的我们使用一台 PC 或平板电脑设备 （通常为 12 – 32pt) 的类型大小相当小看 2 米的距离。 这取决于每个字体的特征，但一般情况下建议的最小类型大小以提高可读性而无需笔划振动是围绕 30pt，根据上面介绍的缩放因子。 如果您的应用程序应使用在近距离，可以使用较小类型的大小。 用于选择字体，Segoe UI （Windows 默认字体） 适用于大多数情况。 但是，避免使用 light 或半浅色字体类型大小小于 42pt 由于精简垂直笔画将振动，它将会降低以增强可读性。 最新版本，如果有足够笔画粗细能正常工作。 例如，Helvetica，Arial 查看丰富多彩和 HoloLens 中非常清晰的常规或加粗的权重。

![建议的类型大小](images/hug-text-08-1000px.png)<br>
*类型的负载增加示例*

## <a name="see-also"></a>请参阅

* [在 MixedRealityToolkit 文本预设](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [示例文本布局预设和场景](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [版式](typography.md)

 
