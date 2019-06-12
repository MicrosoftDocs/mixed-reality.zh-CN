---
title: 聊天室扫描可视化效果
description: 需要空间映射数据的应用程序依赖于设备要自动随着时间的推移收集这些数据，并跨会话作为用户与设备 active 探讨其环境。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，应用模式、 设计、 HoloLens、 聊天室扫描，空间映射，图面重建，网格
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829913"
---
# <a name="room-scan-visualization"></a>聊天室扫描可视化效果

需要空间映射数据的应用程序依赖于设备要自动随着时间的推移收集这些数据，并跨会话作为用户与设备 active 探讨其环境。 完整性和此数据的质量取决于多种因素，包括用户已经进行了数量、 探索以来经过多少时间和家具和门之类的对象是否具有移动设备扫描区域之后。

若要确保有用空间映射数据，应用程序开发人员有几个选项：
* 依赖于哪些有可能已收集了。 此数据最初可能不完整。
* 要求用户使用布隆手势获取 Windows Mixed reality 主页，然后浏览他们想要使用体验的区域。 他们可以使用以无线方式点击以确认所有必要的区域称为到设备。
* 构建他们自己的应用程序中自定义的浏览体验。

请注意，在这些情况下探索过程中收集的实际数据存储系统应用程序不需要执行此操作。

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
        <td>聊天室扫描可视化效果</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>构建自定义扫描体验

应用程序可能会决定分析空间映射数据丰富的经验来判断是否需要用户执行其他步骤来改进其完整性和质量的开头。 如果分析指示应该改进质量，开发人员应提供一个视觉对象用于指示对世界：
* 多少用户邻近范围中的总卷必须是体验的一部分
* 用户应发送到何处以提高数据

用户不知道是什么使"良好"扫描。 他们需要显示或告诉查找在被要求来评估扫描 – 展平、 从实际墙壁、 距离等。开发人员应实现反馈循环，包括扫描或探索阶段刷新空间映射数据。

在许多情况下，可能是最好地告知用户他们需要执行操作 （例如回顾上限，在查找家具），以获取必要的扫描质量。

## <a name="cached-versus-continuous-spatial-mapping"></a>缓存而不是连续空间映射

空间映射数据是数据源的应用可以使用的最大量权重。 为了避免性能问题，例如丢弃的帧或断断续续的情况，使用此数据时应谨慎。

Active 扫描体验期间可以有益或造成不利影响和开发人员将需要决定要使用的方法根据的体验。

### <a name="cached-spatial-mapping"></a>缓存空间的映射

在缓存空间映射的情况下应用程序通常将空间映射数据的快照，并体验的持续时间内使用此快照。

**优势**
* 减少开销，在系统上时体验到巨大的电源，散热运行前导和 cpu 性能的改善。
* 因为空间数据中的更改不中断的主要体验更简单实现。
* 将单个成本上的空间数据的物理特性、 图形和其他用途的任何后续处理一次。

**缺点**
* 缓存的数据不反映实际对象或人员的移动。 例如 应用程序可能会考虑门打开时实际立即关闭。
* 可能的其他应用程序内存以维护数据的缓存的版本。

理想的情形，此方法是在受控的环境或表顶部游戏。

### <a name="continuous-spatial-mapping"></a>连续空间映射

某些应用程序可能依赖于在继续扫描，以刷新空间映射的数据。

**优势**
* 不需要单独扫描或浏览体验提前在应用程序中生成。
* 尽管有一些延迟，游戏时，可以反映实际对象的移动。

**缺点**
* 在实现中的主要体验的更高版本复杂性。
* 潜在的图形或物理作为更改需要这些系统以增量方式引入的附加处理开销。
* 更高的能力、 温度和 CPU 的影响。

理想的情形，此方法是一个预期全息与移动对象，例如在地板上的驱动器可能想要正确地遇到具体取决于是否打开或关闭门 holographic 汽车进行交互。

## <a name="see-also"></a>请参阅
* [空间映射设计](spatial-mapping-design.md)
* [坐标系统](coordinate-systems.md)
* [空间音效设计](spatial-sound-design.md)
