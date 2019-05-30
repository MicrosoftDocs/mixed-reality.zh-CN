---
title: 全息版的远程处理的播放机
description: 全息版的远程处理播放器是连接到 PC 应用程序和游戏支持 Holographic 进行远程处理的配套应用程序。 全息版的远程处理从 PC 到在你 Microsoft HoloLens 的 holographic 内容流式处理实时使用 Wi-fi 连接。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，远程处理，Holographic 远程处理
ms.openlocfilehash: 24213444686dd2e5dbda4016dd551a8ead8f305a
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270314"
---
# <a name="holographic-remoting-player"></a>全息版的远程处理的播放机

全息版的远程处理播放器是连接到 PC 应用程序和游戏支持 Holographic 进行远程处理的配套应用程序。 全息版的远程处理从 PC 到在你 Microsoft HoloLens 的 holographic 内容流式处理实时使用 Wi-fi 连接。

Holographic 远程处理的播放机仅可用于专门为支持 Holographic 远程处理的电脑应用。

可用于 HoloLens 和 HoloLens 2 全息版的远程处理播放器。  支持与 HoloLens Holographic 远程处理的电脑应用需要更新以支持 Holographic Remtoing HoloLens 2。  请如果你有支持哪些版本的问题，联系您的应用程序提供程序。

## <a name="connecting-to-the-holographic-remoting-player"></a>连接到全息版的远程处理播放器

按照应用程序的说明连接到全息版的远程处理播放器。 你将需要输入你可以在远程处理播放机的主屏幕看到如下所示的 HoloLens 设备的 IP 地址：

![全息版的远程处理的播放机](images/holographicremotingplayer.png)

每当看到主屏幕时，您将知道您没有连接的应用程序。

请注意，holographic 远程处理连接是**不会加密**。 通过您信任的安全的 Wi-fi 连接，应始终使用 Holographic 远程处理。

## <a name="quality-and-performance"></a>质量和性能

质量和您的体验的性能取决于三个因素：
* **正在运行的 holographic 体验**-呈现高分辨率或特别详细内容的应用可能需要更快的 PC 或速度更快的无线连接。
* **你的电脑的硬件**-您的 PC 需要能够运行并将编码每秒 60 帧全息版的经验。 获取图形卡，我们通常建议 GeForce GTX 970 或 AMD Radeon R9 290 或更好。 同样，您特定的体验可能需要较高或较低端的卡。
* **你的 Wi-fi 连接**-holographic 体验进行流式处理通过 Wi-fi。 使用具有低拥塞快速网络最大程度提高质量。 使用通过以太网电缆连接的电脑，而不是 Wi-fi，还可以改善质量。

## <a name="diagnostics"></a>诊断

若要衡量您的连接的质量，说说 **"启用诊断"** Holographic 远程处理的播放机的主屏幕上时。 启用诊断后，该应用将显示你：
* **每秒帧数**-呈现的帧的平均数远程处理播放器是接收和每秒呈现。 理想的情况是 60 FPS。
* **延迟**-平均帧来从您的 PC 转到 HoloLens 所需的时间量。 越低越好。 这是很大程度上取决于你的 Wi-fi 网络。

在主屏幕上，可以说 **"禁用诊断"** 关闭诊断。

## <a name="pc-system-requirements"></a>PC 系统要求
* 您的 PC**必须**运行 Windows 10 周年更新或更高版本。
* 我们建议 GeForce GTX 970 或 AMD Radeon R9 290 或更好的图形卡。
* 我们建议将电脑连接到网络通过以太网以减少无线跃点数目。

## <a name="see-also"></a>请参阅
* [全息远程软件许可条款](microsoft-holographic-remoting-software-license-terms.md)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)
