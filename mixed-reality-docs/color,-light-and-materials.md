---
title: 颜色、光线和材料
description: 为混合现实设计内容需要认真考虑你的体验中使用的每个视觉资产的颜色、照明和材料。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 设计, 颜色, 细, 材料
ms.openlocfilehash: bef0c8b63c109baa536e4192ce94919eb888faf2
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896511"
---
# <a name="color-light-and-materials"></a>颜色、光线和材料

为混合现实设计内容需要认真考虑你的体验中使用的每个视觉资产的颜色、照明和材料。 这些决策可用于美观目的, 如使用光线和材料来设置沉浸式环境的音调和功能, 如使用各种颜色来提醒用户即将发生的操作。 必须将每个决策与体验目标设备的机会和约束进行权衡。

下面是特定于在沉浸式耳机上呈现资产的准则。 其中的许多内容都与其他技术领域密切相关, 并且可在本文末尾的 "[另请参阅](color,-light-and-materials.md#see-also)" 一节中找到相关主题的列表。

## <a name="rendering-on-immersive-vs-holographic-devices"></a>在沉浸式与全息设备上渲染

与全息耳机中呈现的内容相比, 在沉浸式耳机中呈现的内容看起来会有所不同。 虽然沉浸式耳机通常会像在二维屏幕上一样呈现内容, 但使用彩色的全息耳机 (如 HoloLens) 可以呈现全息影像。

在全息耳机上, 请始终花时间测试您的全息体验。 即使是专门为全息设备构建内容, 内容的外观也会有所不同, 如辅助监视器、快照和 spectator 视图中所示。 请记住, 在设备上进行测试, 测试影像的照明, 并从所有面 (以及从上到下) 观察内容的方式。 请确保在设备上的一系列亮度设置中进行测试, 因为所有用户不太可能会共享假设的默认值, 以及不同的照明条件集。

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>全息设备上呈现的基本知识
* **全息设备具有累加性显示器**–通过向现实世界中的灯光添加光源来创建全息影像–白色将显示为明亮, 而黑色将显示为透明。
* **颜色影响因用户的环境而异**–用户房间内有很多不同的照明条件。 创建具有适当的对比度级别的内容, 以便清晰地提供帮助。
* **避免动态照明**–在全息体验中均匀发亮的全息影像是最有效的。 使用 "高级" 时, 动态照明可能会超出移动设备的功能。 需要动态照明时, 建议使用[混合现实工具包标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)。 

## <a name="designing-with-color"></a>用 color 设计

由于附加显示器的性质, 某些颜色在全息显示器上显示的颜色可能不同。 某些颜色将在照明环境中弹出, 而其他颜色显示的有影响力更少。 冷颜色通常会 recede 到背景中, 而热颜色会跳到前台。 在浏览经验时, 请考虑以下因素:
* 从一种颜色的 "宽范围" 中获益, 从概念上讲类似于 Adobe RGB。 因此, 某些颜色可能会在设备中表现出不同的质量和表示形式。
* **伽玛**-所呈现图像的亮度和对比度将因沉浸式和全息设备而异。 这些设备的差异经常会使颜色和阴影变暗, 更亮或更不亮。
* **颜色分离**-也称为 "color 细分情况" 或 "color fringing", 当用户跟踪对象的眼睛时, 最常发生颜色分离 (包括光标)。
* **颜色一致性**-通常, 全息影像呈现得非常明亮, 因此, 无论背景如何, 都可以保持颜色一致性。 大区域可能会变得 blotchy。 避免出现鲜艳、纯色的大型区域。
* **呈现浅色颜色**-白色显示非常明亮, 应慎用。 大多数情况下, 请考虑有关 R 235 G 235 B 235 的空白值。 较大的亮点可能导致用户 discomfort。

**呈现深色颜色**

由于加法显示的性质, 深色颜色显示为透明。 实心黑色对象将与现实环境中的显示效果完全不同。 请参阅下面的 Alpha 通道。 若要使显示 "黑色", 请尝试使用非常深的灰色 RGB 值, 如16、16、16。

![普通和广域色域](images/640px-widegamut.png)<br>
*普通和广域色域*

## <a name="technical-considerations"></a>技术注意事项
* "**别名**"-深思熟虑后得出的, 它是锯齿、锯齿或 "楼梯段" 的边缘与现实世界之间的边缘。 如果使用具有高细节的纹理, 则会加剧此效果。 应映射和筛选已启用纹理。 请考虑在对象周围创建黑色边缘边框, 以淡化全息影像边缘或添加纹理。 尽可能避免精简几何。
* **Alpha 通道**-对于没有渲染全息图的任何部分, 必须清除 alpha 通道, 使其完全透明。 在从设备或通过 Spectator 视图拍摄图像/视频时, 使 alpha 不确定会导致视觉对象。
* **纹理软化**-由于浅是全息显示屏中的加法, 因此最好避免较大的纯色区域, 因为它们通常不会产生预期的视觉效果。

## <a name="storytelling-with-light-and-color"></a>带有浅和颜色的故事分享

光源和颜色可帮助你在用户的环境中更自然地显示全息影像, 并为用户提供指导和帮助。 对于全息体验, 请在探索光照和颜色时考虑以下因素:
* **Vignetting** -"vignette" 效果用于加深材料, 有助于将用户的注意力集中在视图的中心。 这种效果会将全息图的材料从用户的注视向量变暗。 请注意, 当用户的视图从倾斜或 glancing 角度影像时, 这也是有效的。
* **强调**: 通过对比颜色、亮度和照明来吸引对象或交互点。 若要详细了解故事分享中的照明方法, 请参阅[像素 Cinematography-适用于计算机图形的照明方法](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)。

![使用 "颜色" 显示对故事分享元素的强调, 此处显示在片段的场景中。](images/640px-fragments.jpg)<br>
*使用 "颜色" 显示对故事分享元素的强调, 此处显示在[片段](https://www.microsoft.com/p/fragments/9nblggh5ggm8)的场景中。*

## <a name="see-also"></a>请参阅
* [颜色分离](hologram-stability.md#color-separation)
* [影像](hologram.md)
* [Microsoft 设计语言-颜色](https://www.microsoft.com/design/color)
* [通用 Windows 平台-颜色](https://docs.microsoft.com/windows/uwp/style/color)
