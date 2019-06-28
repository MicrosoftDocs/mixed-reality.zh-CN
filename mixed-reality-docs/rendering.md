---
title: 渲染
description: 全息呈现后，应用可在用户，周围的世界中的精确位置绘制一张全息图是否精确地放置在现实世界中或已创建一个虚拟领域内。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 呈现、 全息图
ms.openlocfilehash: 45713fd7a30fc55a799da7e89ef52aff8f7eec46
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415409"
---
# <a name="rendering"></a>渲染

全息呈现使应用程序可以在用户，周围的世界中的精确位置绘制一张全息图是否精确地放置在现实世界中或在已创建一个虚拟领域。 [全息](hologram.md)是由声音和光线的对象。 呈现可让你通过 applicaition 添加光线。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>渲染</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>全息呈现

全息呈现的关键在于了解是否呈现为透明，用户可以查看物理世界和您全息组合在一起-HoloLens 显示或阻止出 Windows Mixed Reality 沉浸式耳机等的不透明显示世界。

具有设备**透明显示**，例如[HoloLens](hololens-hardware-details.md)，向环境添加光线。 黑色像素是完全透明的而更亮像素都是越来越不透明。 因为显示灯添加从真实世界中的光照，白色像素是半透明某种程度上。

立体呈现为你全息提供一个深度提示，而添加[接地效果](interaction-fundamentals.md)可以帮助用户是否有更轻松地哪些面一张全息图附近。 一种基础技术是在附近面上，添加一张全息图围绕发光，然后呈现针对此发光阴影。 这样一来，在卷影显示以减去相应的环境中的光。 [空间声音](spatial-sound.md)是另一个非常重要的深度提示，让用户原因有关的距离和一张全息图的相对位置。

具有设备**不透明显示**，如[Windows Mixed Reality 沉浸式耳机](immersive-headset-hardware-details.md)，封闭世界。 黑色像素是纯黑色，其他颜色显示为该用户的颜色。 你的应用程序负责的呈现所有内容的用户会看到。 这使得维护恒定的刷新速率，使用户拥有舒适的体验更重要。

## <a name="predicted-rendering-parameters"></a>预测的呈现参数

混合现实耳机 （HoloLens 和沉浸式耳机） 持续跟踪的位置和方向相对于其周围环境的用户的头。 你的应用程序开始准备其下一帧时，系统可预测用户的头将位置在将来在确切帧在显示器显示的时间。 根据此预测，则系统将计算要使用该框架的视图和投影转换。 你的应用程序**必须使用这些转换才能生成正确结果**; 如果未使用系统提供的转换，生成的映像将不符合现实生活中，从而导致用户不适。

请注意，可准确地预测新帧时将到达该显示，系统正在不断权衡的应用程序的呈现管道有效的端到端延迟。 虽然系统调整以适应呈现管道的长度，可以通过保留尽可能短的管道来改进全息图稳定性。

使用高级的技术来增强对系统进行预测的应用程序可以重写系统视图和投影转换。 这些应用程序必须必须仍使用系统提供转换作为其自定义转换的基础以便生成有意义的结果。

## <a name="other-rendering-parameters"></a>其他呈现参数

当呈现帧，系统指定应在其中绘制您的应用程序在后台缓冲区视区。 此视区通常是小于帧缓冲区的完整大小。 视区大小由应用程序，呈现的帧后系统 upscales 图像以填充整个显示器。

为应用程序，会发现无法呈现所需的刷新速率[可以配置系统呈现参数](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)以减少内存压力和呈现成本，但代价是增加的像素别名。 后台缓冲区格式也会更改，这对于某些应用可以帮助提高内存带宽和像素吞吐量。

呈现截锥、 分辨率和帧速率为您的应用程序要求来呈现可能也会改变帧之间和左侧和右侧关注之间可能存在差异。 例如，当[混合现实捕获](mixed-reality-capture.md)(MRC) 处于活动状态并[照片/视频照相机视图配置](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)不是选择加入，可能使用较大的 FOV 或分辨率呈现一个关注。

对于任何给定帧，您的应用程序*必须*呈现使用视图转换、 投影转换和系统所提供的视区解决方法。 此外，你的应用程序必须永远不会假定任何呈现或视图参数保持固定帧帧中。 与 Unity 相似的引擎处理所有这些转换为你自己相机对象中，以便您的用户和系统状态的物理移动，则始终考虑。 如果你的应用程序允许虚拟世界 （例如，使用摇杆游戏板上） 通过用户的移动，可以添加父远程测试机组对象上方围绕移动的照相机。 这将导致照相机以反映同时用户的虚拟和物理运动。 如果你的应用程序修改视图转换、 投影转换或由系统提供的视区维度，它必须通过调用相应通知系统[重写 API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)。

若要增强全息呈现的稳定性，您的应用程序应提供到 Windows 的每个帧用于渲染的深度缓冲区。 如果您的应用程序提供深度缓冲区，它应具有一致的深度值，并从照相机以米为单位表示的深度。 这使系统可以使用每像素的深度数据来更好地稳定内容，如果用户的头，该怎么办略有偏移量从预测的位置。 如果您不能提供深度缓冲区，您可以提供焦点和正常，大部分内容定义剪切的平面。 如果提供了深度缓冲区和焦点平面，系统可能会同时使用。 具体而言，最好提供深度缓冲区和应用程序显示全息运动中时，包含速度向量的焦点。

请参阅[DirectX 中呈现](rendering-in-directx.md)一文，了解有关其主题的低级别详细信息。

## <a name="holographic-cameras"></a>Holographic 照相机

Windows Mixed Reality 介绍的概念**holographic 照相机**。 Holographic 相机是类似于传统的照相机在 3D 图形文本中找到： 它们定义这两个外部 （位置和方向） 和内部相机属性。 (例如:，使用字段的视图来查看虚拟 3D 场景。)与传统的三维照相机，不同应用程序不在的位置、 方向和照相机的内部属性的控件中。 相反，位置和 holographic 照相机的方向隐式控制用户的移动。 用户的移动中继到通过视图转换在逐个框架的基础上的应用程序。 同样，照相机的内部属性定义的设备的已校准制作和中继通过投影转换帧。

一般情况下你的应用程序将为单个立体照相机呈现。 但是，可靠的渲染循环将支持多个照相机，并且将支持 mono 和立体照相机。 例如，系统可能要求应用程序的呈现从备用的角度来看，当用户激活等功能[混合现实捕获](mixed-reality-capture.md)(MRC)，具体取决于相关耳机的形状。 应用程序都可以支持多个照相机获得它们[在选择加入](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)到[类型](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)相机它们可以支持。

## <a name="volume-rendering"></a>批量呈现

当呈现医疗 Mri 或工程 3D 中的卷[卷呈现](volume-rendering.md)通常使用的技术。 这些技术可以是混合现实中特别有趣的用户可以很自然地查看此类卷从密钥的角度，只需通过移动其头。

## <a name="supported-resolutions-on-hololens-1st-gen"></a>在 HoloLens 上支持的分辨率 （第 1 代）
> [!NOTE]
> 即将推出更多更新。 [查看更新列表](release-notes-april-2018.md)

* 当前和最大受支持的分辨率是的属性[查看配置](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)。 默认情况下，HoloLens 设置到为 720p (1268 x 720)，最大分辨率。
* 最低受支持的视区大小为 720p，为 360 p (634 x 360) 的 50%。 在 HoloLens，这是为 0.5 ViewportScaleFactor。
* 任何低于 540 p 是**不建议这样做**由于 visual 下降，但可以用于标识 bottle necks 中像素的填充率。

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 上支持的分辨率

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。


## <a name="see-also"></a>请参阅
* [全息影像稳定性](hologram-stability.md)
* [在 DirectX 中渲染](rendering-in-directx.md)
