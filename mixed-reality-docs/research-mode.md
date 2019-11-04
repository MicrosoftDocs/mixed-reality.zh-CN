---
title: HoloLens 研究模式
description: 使用 HoloLens 上的研究模式，应用程序可以访问关键设备传感器流（深度、环境跟踪和反射率）。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 研究模式，cv，rs4，计算机视觉，研究，HoloLens
ms.openlocfilehash: 307df0c226221422f13af09d8f4944c22ead3865
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438306"
---
# <a name="hololens-research-mode"></a>HoloLens 研究模式

> [!NOTE]
> 此功能添加为适用于 HoloLens 的[Windows 10 4 月2018更新](release-notes-april-2018.md)的一部分，在早期版本中不可用。

研究模式是一项新功能，它提供对设备上的关键传感器的应用程序访问。 这些地方包括：
- 系统用于地图生成和头跟踪的四个环境跟踪相机。
- 深度相机数据的两个版本–一种用于极接近深度的感应，通常用于跟踪，而另一种用于低频率（1-5 FPS）的深度感应，后者当前用于空间映射，
- 由 HoloLens 使用的两个版本的反射率流来计算深度，但其自身的价值是，因为这些映像是从

![研究模式应用屏幕截图](images/sensor-stream-viewer.jpg)<br>
*混合现实捕获测试应用程序，用于显示在研究模式下提供的八个传感器流*

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>具有</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>研究模式</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>使用研究模式之前

研究模式具有良好的名称：它旨在让学术和工业研究人员在计算机视觉和机器人的字段中试用新的观点。  研究模式不适用于将跨企业部署或在 Microsoft Store 中提供的应用程序。 这样做的原因是，研究模式降低了设备的安全性，消耗的电池电量比正常操作要大得多。 在将来的任何设备上，Microsoft 不会承诺支持此模式。 因此，我们建议你使用它来开发和测试新创意;但是，你将不能广泛地部署使用研究模式的应用程序，也不能保证它将继续在将来的硬件上工作。

## <a name="enabling-research-mode"></a>启用研究模式

研究模式是开发人员模式的子模式。 首先需要在 "设置" 应用中启用 "开发人员模式" （"**设置" > 为开发人员 & 安全 >** ）：

1. 将 "使用开发人员功能" 设置为 "**开**"
2. 将 "启用设备门户" 设置为**打开**

然后，使用连接到与你的 HoloLens 相同的 Wi-fi 网络的 web 浏览器，导航到你的 HoloLens 的 IP 地址（通过 "**设置" > 网络 & Internet > "wi-fi > 硬件" 属性**）。 这是[设备门户](using-the-windows-device-portal.md)，你会在门户的 "系统" 部分中找到 "调研模式" 页：

HoloLens 设备门户的 ![研究模式选项卡](images/ResearchModeDevPortal.png)<br>
*HoloLens 设备门户中的研究模式*

选择 "**允许访问传感器流**" 后，将需要重新启动 HoloLens。 可以从设备门户的页面顶部的 "电源" 菜单项下执行此操作。

重新启动设备后，通过设备门户加载的应用程序应能够访问研究模式流。

## <a name="using-sensor-data-in-your-apps"></a>在应用中使用传感器数据

应用程序可以通过打开[媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197)流来访问传感器流数据，其方式与访问照片/视频摄像机流的方式完全相同。 

在研究模式下，也可以使用适用于 HoloLens 开发的所有 Api。 具体而言，应用程序可以在每个传感器帧捕获时间精确地知道 HoloLens 在6DoF 空间的位置。

演示如何访问各种研究模式流的示例应用程序、如何使用内部函数和 extrinsics 以及如何记录流在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存储库中可用。

## <a name="known-issues"></a>已知问题

请参阅 HoloLensForCV 存储库中的[问题跟踪](https://github.com/Microsoft/HololensForCV/issues)程序。

## <a name="see-also"></a>另请参阅

* [Microsoft 媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 存储库](https://github.com/Microsoft/HoloLensForCV)
* [使用 Windows 设备门户](using-the-windows-device-portal.md)
