---
title: 颜色、 光线和材料
description: 设计混合现实的内容需要仔细考虑的颜色、 照明和为每个视觉对象资产在您的体验中使用的材料。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，设计、 颜色、 光、 材料
ms.openlocfilehash: 3f8ee8edfe4cbbaf8a55b3c4a9125f752823be9c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592261"
---
# <a name="color-light-and-materials"></a>颜色、 光线和材料

设计混合现实的内容需要仔细考虑的颜色、 照明和为每个视觉对象资产在您的体验中使用的材料。 这些决策可能会因美观的目的，如使用光线和材料来设置风格的沉浸式环境和功能的目的，如使用警告用户即将发生的操作的显著颜色。 每个决策必须权衡的机会和体验的目标设备的约束。

下面是特定于沉浸式和全息耳机上呈现资产指导原则。 其中许多紧密绑定到其他技术领域，并可以中找到的相关主题的列表[另请参阅](color,-light-and-materials.md#see-also)本文末尾部分。

## <a name="rendering-on-immersive-vs-holographic-devices"></a>呈现在沉浸式与 holographic 的设备

在沉浸式耳机中呈现的内容将出现相比 holographic 耳机中呈现的内容时以可视方式不同。 时沉浸式耳机通常呈现内容非常类似如您所料 2D 屏幕上，例如 HoloLens 使用 holographic 耳机颜色连续的透明 RGB 显示到全息呈现。

始终需要时间来测试 holographic 耳机全息版体验。 外观的内容，即使它专为 holographic 的设备，生成将不同辅助监视器，快照上，在 spectator 视图中所示。 记住设备，测试的全息照明和观察从所有边 （以及从上方和下方） 警卫四处体验你的内容的呈现方式。 因为它是不太可能所有用户都将都共享假定默认情况下，以及一组不同的光照条件，则请确保在一系列的亮度设置在设备上进行测试。

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>在全息版的设备上呈现的基础知识
* **Holographic 的设备具有累加性显示**– 全息创建通过添加光线的光照真实世界 – 白色会下的户外小径，黑色时将显示为透明。
* **颜色的影响因用户的环境而异**– 在用户的房间内有许多不同的光照条件。 创建具有适当级别的对比度，以便于理解内容。
* **避免动态照明**– 全息统一亮起全息版体验中是最有效。 使用高级的动态照明将很可能超过移动着色器的功能。

## <a name="designing-with-color"></a>设计使用颜色

由于显示累加性的特性，某些颜色可以显示不同 holographic 显示器上。 某些颜色将会弹出照明环境中，而其他人则将显示为较少的有影响。 冷颜色往往 recede 到后台，而热颜色跳到前景。 在你浏览你的体验中的颜色，请考虑以下因素：
* **色域**-HoloLens 受益于使用"各种"概念上类似于 Adobe RGB 颜色。 因此，某些颜色可能会表现出不同的质量和设备中的表示形式。
* **Gamma** -的亮度和对比度呈现的图像将会沉浸式和全息版的设备之间有所不同。 这些设备差异通常会显示要增加或减少明亮的颜色和阴影，深色区域。
* **颜色分离**-也称为"颜色细分情况"或"色边"，分色最，通常会发生与移动全息 （包括游标） 时用户跟踪具有各自的对象。
* **颜色一致性**-通常全息呈现下的户外小径不足以使它们保持颜色一致，而不考虑背景。 大区域可能会变得污渍。 避免鲜亮的纯色颜色的大型区域。
* **呈现亮色**-白色显示机智过人和应谨慎使用。 大多数情况下，请考虑 R 235 G 235 B 235 周围的白色值。 大亮区域可能会导致用户不适。

**呈现暗色**

由于显示累加性的特性，深的颜色显示为透明。 可靠的黑色对象将显示在现实生活中没有什么不同。 请参阅下方的 Alpha 通道。 若要为提供的"black"外观，请尝试如 16,16,16 非常深的灰色 RGB 值。

![宽颜色域与正常](images/640px-widegamut.png)<br>
*宽颜色域与正常*

## <a name="technical-considerations"></a>技术注意事项
* **别名**-周密的别名，交错的数组或"楼梯步骤"在一张全息图几何图形的边缘可以满足现实世界。 使用具有很高的纹理可以担负此效果。 应映射的纹理，并已启用筛选功能。 请考虑淡出全息边缘或添加黑色的边缘周围创建边框对象的纹理。 在可能的情况，请避免精简的几何图形。
* **Alpha 通道**-您必须清除您完全透明的任何部件不呈现一张全息图的 alpha 通道。 使图像/视频从设备或使用 Spectator 视图时将 alpha 未定义的潜在顾客留给视觉瑕疵。
* **纹理柔化**-由于 light 是累加性 holographic 显示，最好是避免鲜亮的纯色颜色的大区域，因为它们通常不会生成预期的视觉效果。

## <a name="storytelling-with-light-and-color"></a>使用浅色和颜色的故事分享

浅色和颜色可帮助利用你全息更自然地出现在用户的环境以及产品/服务的指导，帮助用户。 全息版体验，请在你浏览照明和颜色考虑这些因素：
* **晕影**-要变深材料渐晕效果可以帮助缩小视图的字段中心上的用户的注意力。 这种效果会在用户的视线移动矢量从某些 radius 全息图的材料变暗。 请注意，这也是有效用户的查看从倾斜或匆匆角度全息时。
* **强调**-通过对比颜色亮度和照明吸引人们关注对象或个交互点。 故事分享中照明方法的更多详细信息，请参阅[像素 Cinematography-计算机图形中的光照方法](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)。

![使用的颜色以显示故事分享元素，如下所示在场景中从片段的强调。](images/640px-fragments.jpg)<br>
*使用的颜色以显示对于故事分享元素，如下所示从场景中强调[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)。*

## <a name="see-also"></a>请参阅
* [分色](hologram-stability.md#color-separation)
* [全息](hologram.md)
* [Microsoft 设计语言的颜色](https://www.microsoft.com/design/color)
* [通用 Windows 平台的颜色](https://docs.microsoft.com/windows/uwp/style/color)
