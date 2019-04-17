---
title: 呈现
description: 全息呈现后，应用可在用户，周围的世界中的精确位置绘制一张全息图是否精确地放置在现实世界中或已创建一个虚拟领域内。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 呈现、 全息图
ms.openlocfilehash: 9d87af1b445bc6f730dd02bd7bd7f3aefe7f53db
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593012"
---
# <a name="rendering"></a>呈现

全息呈现后，应用可在用户，周围的世界中的精确位置绘制一张全息图是否精确地放置在现实世界中或已创建一个虚拟领域内。 [全息](hologram.md)对象进行的声音和轻型这类，并呈现后，应用可添加光线。

## <a name="device-support"></a>设备支持

<table>
<tr>
<th>功能</th><th style="width:150px"><a href="hololens-hardware-details.md">HoloLens （第 1 代）</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">沉浸式耳机</a></th>
</tr><tr>
<td>项目名称</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="holographic-rendering"></a>全息呈现

全息呈现的关键在于了解是否呈现为透明 HoloLens，使用户可以查看物理世界和您全息组合在一起-显示或类似的 Windows Mixed Reality 沉浸式头戴式耳机，哪些块的不透明显示查看世界。

具有设备**透明显示**，如[HoloLens](hololens-hardware-details.md)，向环境添加光线。 黑色像素将完全透明的在更亮像素都将是越来越不透明。 因为显示灯添加从真实世界中的光照，甚至白色像素是半透明某种程度上。

立体呈现为你全息提供一个深度提示，而添加[接地效果](interaction-fundamentals.md)可以帮助用户是否有更轻松地哪些面一张全息图附近。 一种基础技术是附近的图面上添加发光围绕一张全息图，然后呈现针对此发光阴影。 这种方式，将显示在卷影以减去相应的环境中的光。 [空间声音](spatial-sound.md)可以是另一个非常重要的深度提示，让用户原因有关的距离和一张全息图的相对位置。

具有设备**不透明显示**，如[Windows Mixed Reality 沉浸式耳机](immersive-headset-hardware-details.md)，封闭世界。 黑色像素将为纯黑色，其他颜色将显示为该颜色给用户。 您的应用程序是负责呈现所有内容，用户将看到，因此，更多必须保持恒定的刷新速率，使用户拥有舒适的体验。

## <a name="predicted-rendering-parameters"></a>预测的呈现参数

混合现实耳机 （HoloLens 和沉浸式耳机） 持续跟踪的位置和方向相对于其周围环境的用户的头。 你的应用开始准备其下一帧时，系统可预测的用户的头将在将来帧将显示在显示器的准确时间。 根据此预测，则系统将计算要使用该框架的视图和投影转换。 你的应用程序**必须使用这些转换才能生成正确结果**; 如果未使用系统提供的转换，生成的映像将不符合现实生活中，从而导致用户不适。

请注意，来准确地预测新帧时将到达该显示，系统正在不断权衡您的应用程序呈现管道的有效的端到端延迟。 时系统会调整为呈现管道的长度，则可以通过保留尽可能短该管道进一步提高全息图稳定性。

使用高级的技术来增强对系统进行预测的应用程序可以重写系统视图和投影转换。 这些应用必须仍必须使用系统提供转换作为其自定义转换的基础以便生成有意义的结果。

## <a name="other-rendering-parameters"></a>其他呈现参数

呈现一个帧时, 系统将指定你的应用程序应在其中绘制的后台缓冲区视区。 此视区通常会比完整帧缓冲区的大小更小。 视区大小已由应用程序，呈现的帧后系统会放大图像以填充整个显示器。

为应用程序，会发现无法呈现所需的刷新速率[可以配置系统呈现参数](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)以减少内存压力和/或呈现成本，但代价是增加的像素别名。 后台缓冲区格式也会更改，这对于某些应用可以帮助提高内存带宽和像素吞吐量。

呈现截锥、 分辨率和帧速率为您的应用程序要求来呈现也可能会更改帧中的和可能的左侧和右侧的眼睛之间存在差异。 例如，当[混合现实捕获](mixed-reality-capture.md)(MRC) 处于活动状态并[照片/视频照相机视图配置](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)不是选择加入，可能使用较大的 FOV 或分辨率呈现一个关注。

对于任何给定帧，您的应用程序*必须*呈现使用视图转换、 投影转换和系统所提供的视区解决方法。 此外，你的应用程序必须永远不会假定任何呈现/view 参数保持固定帧帧中。 与 Unity 相似的引擎处理所有这些转换为您在自己的照相机对象，，以便您的用户和系统状态的物理移动，则始终考虑。 如果您的应用程序进一步允许虚拟世界 （例如，使用摇杆游戏板上） 通过用户的移动，可以添加一个父"装置"对象上方照相机移动它，从而导致照相机以反映这两个用户的虚拟和物理运动。 如果您的应用程序修改视图转换、 投影转换或由系统提供的视区维度，它必须通过调用相应通知系统[重写 API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)。

若要增强全息呈现的稳定性，您的应用程序应提供到 Windows 的每个帧用于渲染的深度缓冲区。 如果您的应用程序提供深度缓冲区，它应具有一致的深度值，并从照相机以米为单位表示的深度。 这使系统可以使用每像素的深度数据来更好地稳定内容，如果用户的头，该怎么办略有偏移量从预测的位置。 如果您不能提供深度缓冲区，应改为提供的焦点位置和正常，大部分内容定义剪切的平面。 如果提供了深度缓冲区和焦点平面，系统可能会使用两者。 具体而言，它可能有助于提供深度缓冲区和焦点时您的应用程序显示全息运动中包括速度向量。

有关所有低级别详细介绍，请参阅[DirectX 中呈现](rendering-in-directx.md)一文。

## <a name="holographic-cameras"></a>Holographic 照相机

Windows Mixed Reality 介绍的概念**holographic 照相机**。 Holographic 相机是类似于传统的照相机在 3D 图形文本中找到： 它们定义这两个外部 （位置和方向） 和内部相机属性 (ex： 字段的视图) 用于查看虚拟 3D 场景。 与传统的三维照相机，不同应用程序不在的位置、 方向和照相机的内部属性的控件中。 相反，位置和 holographic 照相机的方向隐式控制用户的移动。 用户的移动中继到通过视图转换在逐个框架的基础上的应用程序。 同样，照相机的内部属性定义的设备的已校准制作和中继通过投影转换帧。

一般情况下将对单个立体照相机呈现您的应用程序。 但是，可靠的渲染循环应支持多个摄像机，并且应该支持 mono 和立体照相机。 例如，系统可能会要求您的应用程序呈现从备用的角度来看，当用户激活等功能[混合现实捕获](mixed-reality-capture.md)(MRC)，具体取决于相关耳机的形状。 可以支持多个相机的应用获取它们[在选择加入](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)到[种类](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)相机它们可以支持。

## <a name="volume-rendering"></a>批量呈现

呈现医疗时 MRI 或工程 3D 中的卷[卷呈现](volume-rendering.md)通常使用的技术。 这些技术可以是混合现实中特别有趣的用户可以很自然地查看此类卷从密钥的角度，只需通过移动其头。

## <a name="supported-resolutions-on-hololens-1st-gen"></a>在 HoloLens 上支持的分辨率 （第 1 代）
> [!NOTE]
> 将传入到这篇文章在将来的更多更新。 [查看更新列表](release-notes-april-2018.md)

* 当前和最大受支持的分辨率是的属性[查看配置](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)。 默认情况下，HoloLens 设置到为 720p (1268 x 720)，最大分辨率。
* 最低受支持的视区大小为 720p，为 360 p (634 x 360) 的 50%。 在 HoloLens，这是为 0.5 ViewportScaleFactor。
* 任何低于 540 p 是**不建议这样做**由于 visual 下降，但可以用于标识 bottle necks 中像素的填充率。

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 上支持的分辨率

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。


## <a name="see-also"></a>请参阅
* [全息图稳定性](hologram-stability.md)
* [在 DirectX 中呈现](rendering-in-directx.md)