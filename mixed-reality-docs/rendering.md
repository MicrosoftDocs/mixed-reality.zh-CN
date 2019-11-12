---
title: 渲染
description: 全息渲染使你的应用能够在世界各地的确切位置绘制一个全息影像，无论是精确放置在物理领域还是在你创建的虚拟领域内。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 呈现，全息影像
ms.openlocfilehash: 9c32d8ddf5a1fb9e9d991211756ba1306f4d3fa9
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926862"
---
# <a name="rendering"></a>渲染

全息渲染使你的应用程序可以在世界各地的确切位置中绘制一个全息影像，无论是精确地放置在物理世界中还是在创建的虚拟领域内。 [全息影像](hologram.md)是发出声音和光的对象。 呈现使应用程序能够添加光。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>具有</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens（第 1 代）</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>渲染</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>全息渲染

用于全息呈现的关键在于，知道您是要呈现到可让用户同时查看物理世界和您的影像的 "查看" 显示方式，还是显示一个不透明的显示，如 Windows Mixed Reality 沉浸式耳机，它们会阻止世界。

具有 "**查看**" 的设备显示，[例如，](hololens-hardware-details.md)将光线添加到世界。 黑色像素是完全透明的，而较亮的像素则越来越不透明。 由于显示器中的光线被添加到现实世界的灯光，因此白色像素有些半透明。

尽管 stereoscopic 呈现为你的全息影像提供了一个深度提示，但增加了[接地效果](interaction-fundamentals.md)可帮助用户更轻松地了解到全息图附近的图面。 一种接地方法是围绕附近图面上的全息图添加发光，然后针对此发光呈现阴影。 这样一来，您的阴影就会显得比环境少一些。 [空间音效](spatial-sound.md)是另一项非常重要的深度提示，使用户了解全息图的距离和相对位置。

显示不**透明**的设备，如[Windows Mixed Reality 沉浸式耳机](immersive-headset-hardware-details.md)，会阻止世界。 黑色像素为纯色，任何其他颜色将以该颜色显示给用户。 应用程序负责呈现用户看到的所有内容。 这使得更重要的是保持持续的刷新率，使用户有舒适的体验。

## <a name="predicted-rendering-parameters"></a>预测呈现参数

混合现实耳机（HoloLens 和沉浸式耳机）会持续跟踪用户的头相对于其周围的位置和方向。 当您的应用程序开始准备下一帧时，系统将预测用户在显示器上的未来的哪一段时间。 根据此预测，系统计算要用于该帧的视图和投影转换。 应用程序**必须使用这些转换才能生成正确的结果**;如果未使用系统提供的转换，则生成的映像将不会与真实环境保持一致，从而导致用户 discomfort。

请注意，为了准确预测新帧何时会到达显示器，系统会不断地测量应用程序渲染管道的端到端延迟。 当系统调整到您的渲染管道的长度时，您可以通过使该管道尽可能简短来改善全息影像的稳定性。

使用高级技术来增强系统预测的应用程序可能会覆盖系统视图和投影转换。 对于自定义转换，这些应用程序必须仍使用系统提供的转换才能产生有意义的结果。

## <a name="other-rendering-parameters"></a>其他呈现参数

呈现帧时，系统将指定应用程序应在其中进行绘制的后台缓冲区视区。 此视区通常小于帧缓冲区的完整大小。 无论视区大小如何，应用程序呈现帧后，系统会 upscales 图像以填充整个显示器。

对于自行找不到的应用程序，无法按所需的刷新速率进行呈现，[系统呈现参数可以配置](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)为减少内存压力，并以增加像素别名的成本呈现成本。 还可以更改后台缓冲区格式，对于某些应用，这可以帮助提高内存带宽和像素吞吐量。

呈现拆分器、分辨率和应用程序在其中呈现的帧速率可能也会随帧之间的变化而变化，并且可能会在左右眼睛之间有所不同。 例如，当[混合现实捕获](mixed-reality-capture.md)（MRC）处于活动状态，并且未选择 "[照片/视频相机" 视图配置](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)时，可以使用较大的 FOV 或分辨率来呈现一种眼睛。

对于任何给定的帧，应用*必须*使用系统提供的视图转换、投影转换和视区分辨率进行呈现。 此外，应用程序决不能假设任何呈现或视图参数都保持从帧到帧的固定。 类似于 Unity 的引擎会在其自己的相机对象中处理所有这些转换，以便始终遵循用户的物理移动和系统的状态。 如果你的应用程序允许用户（例如，在游戏板上使用操纵杆）虚拟移动用户，则可在相机上方添加一个父远程测试机组对象。 这将导致照相机反映用户的虚拟动作和物理动作。 如果你的应用程序修改系统提供的视图转换、投影转换或视区维度，则它必须通过调用相应的[重写 API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)来通知系统。

为了增强全息呈现的稳定性，你的应用程序应向 Windows 提供它用于呈现的深度缓冲区。 如果你的应用程序提供了深度缓冲区，则它应具有连贯的深度值，并以米为单位从相机中表示深度。 这使系统可以使用每像素深度数据来更好地实现稳定的内容，前提是用户的头与预测的位置有略微的偏移量。 如果无法提供深度缓冲区，则可以提供焦点，并定义一个用于剪切大部分内容的平面。 如果深度缓冲区和焦点平面都提供，则系统可能会同时使用这两者。 特别是，提供深度缓冲区和焦点（当应用程序显示动态影像时包含速度矢量）会很有帮助。

有关本主题的详细信息，请参阅[DirectX 文章中的呈现](rendering-in-directx.md)。

## <a name="holographic-cameras"></a>全息相机

Windows Mixed Reality 引入了**全息相机**的概念。 全息相机类似于3D 图形文本中的传统相机：它们同时定义外部（位置和方向）和内部照相机属性。 （例如：，视图字段用于查看虚拟三维场景。）与传统3D 相机不同，应用程序不会控制相机的位置、方向和内部属性。 而是通过用户的移动隐式控制全息相机的位置和方向。 用户的移动通过视图转换逐帧地中继到应用程序。 同样，照相机的内部属性由设备的校准光学，并通过投影转换按帧中继。

通常，应用程序将针对单个立体声相机进行呈现。 但是，可靠的呈现循环将支持多个照相机，同时支持 mono 和立体声相机。 例如，当用户激活[混合现实捕获](mixed-reality-capture.md)（MRC）等功能时，系统可能会要求你的应用程序从备用角度进行呈现，具体取决于相关耳机的形状。 可以支持多个照相机的应用[程序通过选择](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)他们可以支持的相机[类型](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)来获取它们。

## <a name="volume-rendering"></a>卷渲染

在三维中呈现医学面向 mri 或工程量时，通常使用[卷渲染](volume-rendering.md)技术。 这种方法在混合现实中尤其有趣，用户可以自然地从不同的角度观看此类卷，只需移动其头。

## <a name="supported-resolutions-on-hololens-1st-gen"></a>HoloLens 上支持的解决方法（第一代）
> [!NOTE]
> 即将推出更多更新。 [查看更新列表](release-notes-april-2018.md)

* 当前支持的最大分辨率为[视图配置](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)的属性。 默认情况下，默认情况下，HoloLens 设置为 "720p （1268x720）" 的最大分辨率。
* 支持的视区大小最低为720p 的50%，即360p （634x360）。 在 HoloLens 上，这是0.5 的 ViewportScaleFactor。
* 由于视觉降级，**不建议**使用小于540p 的任何内容，但可以使用它来标识以像素填充速率表示的瓶 necks。

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 上支持的解决方法

> [!NOTE]
> 即将[推出](news.md)特定于 HoloLens 2 的更多指导。


## <a name="see-also"></a>另请参阅
* [全息影像稳定性](hologram-stability.md)
* [在 DirectX 中渲染](rendering-in-directx.md)
