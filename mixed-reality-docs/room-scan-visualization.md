---
title: 房间扫描可视化
description: 需要空间映射数据的应用程序依赖于设备在一段时间内和跨会话自动收集此数据, 因为用户浏览其环境中的设备处于活动状态。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 应用模式, 设计, HoloLens, 房间扫描, 空间映射, 表面重建, 网格
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829913"
---
# <a name="room-scan-visualization"></a>房间扫描可视化

需要空间映射数据的应用程序依赖于设备在一段时间内和跨会话自动收集此数据, 因为用户浏览其环境中的设备处于活动状态。 此数据的完整性和质量取决于多个因素, 包括用户的探索量、从浏览开始起经过的时间, 以及从设备扫描区域以来是否移动了家具和门等对象。

为了确保有用的空间映射数据, 应用程序开发人员有多种选择:
* 依赖于可能已收集的内容。 此数据最初可能是不完整的。
* 要求用户使用布隆手势进入 Windows Mixed Reality 主页, 并浏览他们希望用于体验的领域。 他们可以使用分流来确认设备是否知道所有必要的区域。
* 在自己的应用程序中生成自定义浏览体验。

请注意, 在所有这些情况下, 在浏览过程中收集的实际数据都由系统存储, 并且应用程序无需执行此操作。

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
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td>房间扫描可视化</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>构建自定义扫描体验

应用程序可以决定在体验开始时对空间映射数据进行分析, 判断他们是否希望用户执行额外的步骤来提高其完整性和质量。 如果分析表明质量应该提高, 开发人员应提供一种可视化对象, 使其在世界上叠加以指示:
* 用户附近的用户总数需要成为体验的一部分
* 用户应在何处着手改善数据

用户不知道什么是 "良好" 扫描。 如果要求评估扫描– flatness、与实际墙壁的距离等, 则需要显示或告知要查找的内容。开发人员应实现一个反馈循环, 其中包括在扫描或浏览阶段刷新空间映射数据。

在许多情况下, 最好告诉用户需要执行的操作 (例如, 查看家具上的天花板), 以便获得必要的扫描质量。

## <a name="cached-versus-continuous-spatial-mapping"></a>缓存与连续空间映射

空间映射数据是最繁重的数据源应用程序可以使用的数据源。 若要避免性能问题 (如丢弃的帧或断断续续), 应仔细地使用此数据。

体验过程中的活动扫描可能既有利也有不利, 开发人员需要根据经验决定要使用哪种方法。

### <a name="cached-spatial-mapping"></a>缓存空间映射

对于缓存空间映射, 应用程序通常会拍摄空间映射数据的快照, 并在体验期间使用此快照。

**优势**
* 降低了系统的系统开销, 同时体验运行, 从而提高了性能、散热和 cpu 性能。
* 由于空间数据中的更改不会中断, 因此更简单的主要体验实现。
* 对于物理学、图形和其他用途的任何 post 处理空间数据, 一次只需一次。

**弊端**
* 实际对象或人员的移动不会由缓存数据反映。 例如 应用程序可能会将门视为在实际关闭时打开。
* 可能会有更多的应用程序内存来维护数据的缓存版本。

此方法的一个很好的例子是受控环境或表顶级游戏。

### <a name="continuous-spatial-mapping"></a>连续空间映射

某些应用程序可能依赖于继续扫描以刷新空间映射数据。

**优势**
* 无需在应用程序中提前构建单独的扫描或浏览体验。
* 尽管有一些延迟, 但现实世界对象的移动可能会反映出来。

**弊端**
* 实现主要体验的复杂性更高。
* 由于需要以增量方式引入这些系统的更改, 因此, 对图形或物理的额外处理可能会造成开销。
* 高功率、热量和 CPU 影响。

此方法的一种很好的情况是, 全息影像应与移动对象进行交互, 例如, 地面上驱动器的全息汽车可能需要正确地从门中向下移动, 具体取决于它是打开还是关闭。

## <a name="see-also"></a>请参阅
* [空间映射设计](spatial-mapping-design.md)
* [坐标系统](coordinate-systems.md)
* [空间音效设计](spatial-sound-design.md)
