---
title: 全息远程处理播放器
description: 全息远程处理播放器是一种附属应用, 用于连接到支持全息远程处理的 PC 应用和游戏。 使用 Wi-fi 连接, 全息远程处理会实时地将 PC 中的全息内容流式处理到你的 Microsoft HoloLens。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813717"
---
# <a name="holographic-remoting-player"></a>全息远程处理播放器

全息远程处理播放器是一种附属应用, 用于连接到支持全息远程处理的 PC 应用和游戏。 使用 Wi-fi 连接, 全息远程处理会实时地将 PC 中的全息内容流式处理到你的 Microsoft HoloLens。

全息远程处理播放器只能与专门设计用于支持全息远程处理的 PC 应用程序一起使用。

全息远程处理播放器适用于 HoloLens 和 HoloLens 2。  支持通过 HoloLens 进行全息远程处理的 PC 应用需要更新, 以支持 Remtoing 和 HoloLens 2 的全息版。  如果你对支持哪些版本有任何疑问, 请与你的应用程序提供商联系。

## <a name="connecting-to-the-holographic-remoting-player"></a>连接到全息远程处理播放器

按照应用的说明连接到全息远程处理播放器。 需要输入你的 HoloLens 设备的 IP 地址, 你可以在远程处理播放机的主屏幕上看到该设备, 如下所示:

![全息远程处理播放器](images/holographicremotingplayer.png)

看到主屏幕时, 您将知道您没有连接到应用程序。

请注意, 全息远程处理连接**未加密**。 你应始终在你信任的安全 Wi-fi 连接上使用全息远程处理。

## <a name="quality-and-performance"></a>质量和性能

经验的质量和性能会因三个因素而异:
* **正在运行的全息体验**-呈现高分辨率或高度详细内容的应用可能需要更快的 PC 或更快的无线连接。
* **你的电脑硬件**-你的电脑需要能够以60帧/秒的速度运行和编码全息体验。 对于图形卡, 我们通常建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更高。 同样, 你的特定体验可能需要更高或更低端的卡。
* **Wi-fi 连接**-你的全息体验通过 wi-fi 进行流式处理。 使用具有低拥塞的快速网络来最大程度地提高质量。 使用通过以太网电缆而不是 Wi-fi 连接的 PC, 还可以提高质量。

## <a name="diagnostics"></a>诊断

若要测量连接的质量, 请在全息远程处理播放机的主屏幕上说 **"启用诊断"** 。 启用诊断后, 应用会显示以下信息:
* **FPS** -远程处理播放机每秒接收和呈现的呈现帧的平均数目。 理想为 60 FPS。
* **滞后**时间-帧从电脑进入 HoloLens 所需的平均时间量。 越低越好。 这在很大程度上依赖于 Wi-fi 网络。

在主屏幕上, 可以说 **"禁用诊断"** 以关闭诊断。

## <a name="pc-system-requirements"></a>PC 系统要求
* 你的电脑**必须**运行 Windows 10 周年更新或更高版本。
* 建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更好的图形卡。
* 建议你通过以太网将电脑连接到网络, 以减少无线跃点的数量。

## <a name="see-also"></a>请参阅
* [全息远程软件许可条款](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)
