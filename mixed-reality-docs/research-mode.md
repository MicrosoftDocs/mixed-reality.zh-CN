---
title: HoloLens 研究模式
description: 使用 HoloLens 上的研究模式，应用程序可以访问关键设备传感器流（深度、环境跟踪和反射率）。
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
keywords: 研究模式，cv，rs4，计算机视觉，研究，HoloLens，HoloLens 2
ms.openlocfilehash: 62b82e3a36452d4b104bf04999e556ec19d2a5e3
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720393"
---
# <a name="hololens-research-mode"></a>HoloLens 研究模式

## <a name="overview"></a>概述

第一代 HoloLens 中引入了研究模式，可用于访问设备上的关键传感器，尤其适用于不适用于部署的研究应用程序。 你现在可以从以下输入收集数据：

* **可见的轻型环境跟踪相机**-系统用于 head 跟踪和地图构建。
* **深度相机**–在两种模式下运行：  
    + 用于[手动跟踪](interaction-fundamentals.md)的短期、高频率（30 FPS）近深度感知
    + 长整型抛出，[空间映射](spatial-mapping.md)使用的最深层度（1-5 FPS）
* **反射率的两个版本**： HoloLens 用于计算深度。 这些图像通过红外，并不受环境可见光的影响。

如果使用的是 HoloLens 2，还可以访问以下输入：

* **加速感应**程序–由系统用来确定沿 X、Y 和 Z 轴和重心的线性加速度。
* **Gyro** –系统用来确定旋转。
* **磁力仪**–系统用于估计绝对方向。

![研究模式应用屏幕截图](images/sensor-stream-viewer.jpg)<br>
*混合现实捕获测试应用程序，用于显示在研究模式下提供的八个传感器流*

> [!NOTE]
> 研究模式功能已添加为适用于 HoloLens 的[Windows 10 4 月2018更新](release-notes-april-2018.md)的一部分，在早期版本中不可用。

## <a name="usage"></a>使用情况

研究模式旨在使学术和工业研究人员了解计算机视觉和机器人的字段中的新想法。  它不适合企业环境中部署的应用程序，也不能通过 Microsoft Store 或其他分发渠道提供。

此外，Microsoft 不保证在未来的硬件或操作系统更新中将支持研究模式或等效的功能。 但是，这不会阻止你使用它来开发和测试新的观点！

## <a name="security-and-performance"></a>安全性和性能

请注意，在正常情况下，启用研究模式比使用 HoloLens 2 时使用的电池电量更多。 即使使用调研模式功能的应用程序没有运行，也是如此。  启用此模式还可以降低设备的整体安全性，因为应用程序可能会滥用传感器数据。  您可以在[HoloLens 安全常见问题](https://docs.microsoft.com/hololens/hololens-faq-security)中找到有关设备安全的详细信息。  


## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><strong>功能</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens 第一代</strong></a></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td>标题跟踪相机</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>IR 相机 & 深度</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>加速计</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>陀螺仪</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>磁力计</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> HoloLens 2 的研究模式支持预计在7月2020公开预览版中提供，并将包含上面列出的所有功能。 请返回获取详细信息。 

## <a name="enabling-research-mode"></a>启用研究模式

研究模式是开发人员模式的扩展。 在开始之前，需要启用设备的开发人员功能才能访问 "研究模式" 设置： 

* 打开 "**开始" 菜单 > 设置**"，然后选择"**更新**"。
* **为开发人员**选择并启用**开发人员模式**。
* 向下滚动并启用**设备门户**。

启用开发人员功能后，[连接到设备门户](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens)以启用研究模式功能。

在*HoloLens 第一代*：

* 在**设备门户**中转到 "**系统 > 研究模式**"。
* 选择 "**允许访问传感器流**"。
* 从页面顶部的**Power** menu 项重新启动设备。

重新启动设备后，通过**设备门户**加载的应用程序可以访问研究模式流。

![HoloLens 设备门户的研究模式选项卡](images/ResearchModeDevPortal.png)<br>
*HoloLens 设备门户中的研究模式窗口*

## <a name="using-sensor-data-in-your-apps"></a>在应用中使用传感器数据

*HoloLens 第一代*

应用程序可以访问传感器流数据，其方式与通过[媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197)访问照片和视频相机流的方式相同。 

适用于 HoloLens 开发的所有 Api 在研究模式下也可用。 具体而言，应用程序在每个传感器帧捕获时间确切地了解 HoloLens 在6DoF 空间的位置。

你可以找到有关如何访问各种研究模式流的示例应用程序、如何使用[内部函数和 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)，以及如何在[HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)存储库中记录流。

 > [!NOTE]
 > 此时，HoloLensForCV 示例在 HoloLens 2 上不起作用。

## <a name="known-issues"></a>已知问题

你可以使用 HoloLensForCV 存储库中的[问题跟踪](https://github.com/Microsoft/HololensForCV/issues)程序来遵循已知问题。

## <a name="see-also"></a>请参阅

* [Microsoft 媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 存储库](https://github.com/Microsoft/HoloLensForCV)
* [使用 Windows 设备门户](using-the-windows-device-portal.md)
