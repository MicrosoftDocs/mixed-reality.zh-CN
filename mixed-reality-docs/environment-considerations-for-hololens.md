---
title: HoloLens 的环境注意事项
description: 获取使用 HoloLens，优化您的眼睛和环境的设备时可能的最佳体验。
author: thetuvix
ms.author: msamples
ms.date: 02/24/2019
ms.topic: article
keywords: holographic 帧、 视角、 fov、 校正、 空格、 环境、 操作方法
ms.openlocfilehash: d5433dc923aeb70e3ae82e75c9358d3a569e8f83
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592244"
---
# <a name="environment-considerations-for-hololens"></a>HoloLens 的环境注意事项

HoloLens 混合与"真实"世界，holographic 全息置于周围的环境。 全息版应用窗口"挂起"墙上插座上、 holographic ballerina 旋转上桌面、 bunny 耳朵坐在您不知情的朋友头之上。 Holographic 世界时使用的沉浸式游戏或应用程序，将展开以填充周围的环境，但您将仍将能够查看并移动空间。

放置的全息将保持已放置它们，即使你关闭你的设备。 

以下是一些要记住的 holographic 世界的最佳体验。 请注意，HoloLens 设计要在室内个没有 tripping 危险的安全空间中使用。 不要驾驶或执行需要完全关注其他活动时使用它。

## <a name="spaces"></a>空格

HoloLens 了解你的空间以便它可以记住所在全息。 HoloLens 可以记住多个空格，专为加载正确的空间时将其打开。

### <a name="setting-up"></a>设置

HoloLens 可以映射，并请你空间最记住，如果你选择正确的环境。
* 使用空间足够浅色和足够的空间。 避免深色空间和包含大量深色、 时尚，或半透明应用层协议 （如镜像或瘦空气幕后） 的聊天室。
* 如果你想 HoloLens，若要了解一个空格，面临着它直接从大约一米消失。
* 避免使用很多移动对象的空间。 如果项已移动，并且你想 HoloLens，若要了解其新位置 （例如，您移动咖啡表到新位置），看，移动它。

### <a name="spatial-mapping"></a>空间映射

当你输入新的空间 （或加载一个现有） 时，您将看到空间进行传播的网格图形。 这意味着你的设备[映射周围的环境](spatial-mapping-design.md)。 如果您遇到放置全息的问题，请尝试遍历周围的空间，因此 HoloLens 可以将其映射更全面。 如果你 HoloLens 无法映射你的空间，或超出校准，您可以输入 Limited 模式。 在 Limited 模式下，你将无法将全息放在周围的环境。

### <a name="managing-your-spaces"></a>管理你的空间

到单个数据库中，本地存储 HoloLens 设备上已折叠的映射部分和不同的空间。  映射数据库具有访问权限仅提供到内部系统，而永远不会在设备的用户即使插入到 PC 和/或使用文件资源管理器应用，安全地存储。  启用 bitlocker 后，也被加密存储的映射数据。
全息放入不同的位置，而无需位置/全息之间的连接路径时存在的多个映射组件。  全息锚定在相同的映射部分内会被视为是"邻近"在当前的空间中存在是开发人员的 API 来导出一小部分的"当前空间"（当前已识别的映射组件的部分） 以实现共享全息图方案。  目前，没有机制可以下载整个数据库的所有已映射的空格。

#### <a name="wifi"></a>WLAN
已连接的 vs。不 –，只要启用 WiFi，映射数据将相关与 WiFi 指纹，即使未连接到实际 WiFi 网络/路由器。  这是路由器的因为的 MAC 地址和信号强度 （即 WiFi 指纹） 是路由器的可用的无需连接到它。  网络标识 (即 SSID，MAC 地址) 不会发送给 Microsoft 和所有引用都将在 HoloLens 本地的 WiFi。

已启用的 vs。禁用-HoloLens 将感测并记住空格，即使禁用了 WiFi，将传感器数据安全地存储时全息放置。  而无需 WiFi 信息中，空间和全息可能较慢随着需求的 HoloLens 比较 active 扫描所有全息图的定位点和映射节存储在设备上，以"relocalize"代码图的右侧部分在更高版本时，识别。

#### <a name="environment-management"></a>环境管理
有 2 个设置，它使用户能够"清理"全息和 HoloLens 忘记"空格"的原因。  它们存在于"全息和环境"在设置应用中，也会显示在"隐私"下，在设置应用的第二个设置。
1.  删除附近全息-通过选择此设置，HoloLens 会删除所有定位的全息和设备所在的位置的"当前的空间"的所有存储的映射数据。  新的映射部分将创建并后全息试放置在该相同的空间存储在该位置的数据库中。
2.  删除所有全息-HoloLens 通过选择此设置，将擦除所有地图数据和锚定全息空格的整个数据库中。  将重新发现没有全息和任何全息需要新放置再次存储在数据库中的地图部分。


## <a name="hologram-quality"></a>全息图质量

全息可以放置在整个环境 — 高、 低和所有周围 — 但您会看到它们[holographic 帧](holographic-frame.md)它位于你自己的前面。 若要获取最佳视图，请确保调整你的设备，以便您可以看到整个帧。 并欢迎您的环境中四处走动和探索 ！

为你[全息](hologram.md)去清晰、 明确且稳定，您 HoloLens 需要仅为您校准。 当首次设置你 HoloLens 时，您将指导完成此过程。 更高版本上，如果全息看起来不合适或遇到了很多错误，您可以进行调整。

### <a name="calibration"></a>校准

如果你全息看起来抖动或晃动，或者如果在遇到放置全息的问题，是第一件事要尝试[校准应用](calibration.md)。 如果您使用您 HoloLens 时遇到任何不适，还可以帮助此应用。

若要获取到校准应用，请转到设置 > 系统 > 实用程序。 选择打开校准并按照说明进行操作。

如果运行校准应用，但仍遇到问题的 hologram 质量或看到频繁的"跟踪丢失"消息，请尝试传感器优化应用程序。 转到设置 > 系统 > 实用程序，选择打开传感器优化，并按照说明进行操作。

如果其他人将使用你 HoloLens，它们应使该设备正确设置为它们首先运行校准应用。

## <a name="see-also"></a>请参阅
* [空间映射设计](spatial-mapping-design.md)
* [全息](hologram.md)
* [校准](calibration.md)
