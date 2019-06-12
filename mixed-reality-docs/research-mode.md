---
title: HoloLens 研究模式
description: 在 HoloLens 上使用研究模式下，应用程序可以访问关键的设备传感器数据流 （深度、 跟踪、 环境和 IR 反射率）。
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 研究模式、 cv、 rs4、 计算机视觉、 研究、 HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829933"
---
# <a name="hololens-research-mode"></a>HoloLens 研究模式

> [!NOTE]
> 此功能已添加的一部分[Windows 10 2018 年 4 月更新](release-notes-april-2018.md)HoloLens，为和早期版本上不可用。

研究模式是提供的设备应用程序访问密钥的传感器的 HoloLens 的新功能。 这些问题包括：
- 四个跟踪系统的映射生成和头跟踪使用的照相机的环境。
- 两个版本的深度相机数据 – 一个用于高频率 （每秒 30 帧） 附近深度检测通常用于在手动跟踪，，另一个用于较低频率 (表示 1 FPS) 远端的深度检测当前使用的空间映射
- HoloLens 用于计算深度，但自己权限内的有价值，因为这些映像是从 HoloLens 照明和合理的环境光线不会影响 IR 反射率流的两个版本。

![研究模式应用程序屏幕截图](images/sensor-stream-viewer.jpg)<br>
*显示在研究模式下提供八个传感器数据流的测试应用程序的混合的现实捕获*

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式耳机</strong></a></td>
    </tr>
     <tr>
        <td>信息检索模式</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>使用研究模式之前

研究模式也名为： 适用于学术和工业研究人员尝试使用计算机视觉和机器人的字段中的新创意。  研究模式不适合将整个企业内部署或可在 Microsoft Store 中的应用程序。 这样做的原因是设备的研究模式降低了你的安全性，并使用比正常操作的更多电量。 Microsoft 不提交到任何将来使用的设备上支持此模式。 因此，我们建议使用它来开发和测试新的想法;但是，您将不能广泛部署的应用程序使用研究模式或具有任何保证，它将继续在将来的硬件上工作。

## <a name="enabling-research-mode"></a>启用研究模式

研究模式是开发人员模式下的子模式。 首先需要启用开发人员模式下设置应用中的 (**设置 > 更新和安全 > 面向开发人员**):

1. 将设置为"使用开发人员功能"**上**
2. 将"启用设备门户"设置为**上**

然后使用连接到你 HoloLens，相同的 Wi-fi 网络的 web 浏览器导航到你 HoloLens 的 IP 地址 (通过获得**设置 > 网络和 Internet > Wi-fi > 硬件属性**)。 这是[设备门户](using-the-windows-device-portal.md)，并将在门户的"系统"部分中找到"研究模式"页：

![HoloLens 设备门户研究模式选项卡](images/ResearchModeDevPortal.png)<br>
*HoloLens 设备门户中的信息检索模式*

选择后**允许访问传感器数据流**，则将需要重新启动 HoloLens。 可以从位于页面顶部的"Power"菜单项下的设备门户来执行此操作。

后重新启动你的设备，通过设备门户已加载的应用程序应能够访问研究模式流。

## <a name="using-sensor-data-in-your-apps"></a>应用程序中使用传感器数据

应用程序可以通过打开访问传感器数据流式传输[Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)中完全相同的方式访问照片/视频照相机流的流。 

适用于 HoloLens 开发的所有 Api 都都可在研究模式时。 具体而言，应用程序可以知道准确地说，HoloLens 是 6DoF 空间中每个传感器帧捕获时间点。

显示访问各种研究模式流的方式、 如何使用内部函数和 extrinsics，以及如何记录流的示例应用程序均位于[HoloLensForCV GitHub 存储库](https://github.com/Microsoft/HoloLensForCV)。

## <a name="known-issues"></a>已知问题

请参阅[问题跟踪程序](https://github.com/Microsoft/HololensForCV/issues)HoloLensForCV 存储库中。

## <a name="see-also"></a>请参阅

* [Microsoft 媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 存储库](https://github.com/Microsoft/HoloLensForCV)
* [使用 Windows 设备门户](using-the-windows-device-portal.md)
