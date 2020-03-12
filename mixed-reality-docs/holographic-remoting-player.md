---
title: 全息远程处理播放器
description: 全息远程处理播放器是一种附属应用，用于连接到支持全息远程处理的 PC 应用和游戏。 使用 Wi-fi 连接，全息远程处理会实时地将 PC 中的全息内容流式处理到你的 Microsoft HoloLens。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: 88a9aa0bb058776a32016e51fc22bcb73f08ab85
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092373"
---
# <a name="holographic-remoting-player"></a>全息远程处理播放器

>[!IMPORTANT]
>HoloLens 2 的全息远程处理是一种主要版本更改。 [适用于 hololens 的远程应用程序 **（第一代）** ](add-holographic-remoting.md) **必须使用 NuGet** **包版本 1.x**和[ **hololens 2**的远程应用程序](holographic-remoting-create-host.md)必须使用1.x。 这意味着，为 HoloLens 2 编写的远程应用程序与 HoloLens （第一代）不兼容，反之亦然。

[全息远程处理播放器](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40)是一种附属应用，用于连接到支持全息远程处理的 PC 应用和游戏。 使用 Wi-fi 连接，全息远程处理会实时地将 PC 中的全息内容流式处理到你的 Microsoft HoloLens。

全息远程处理播放器只能与专门设计用于支持全息远程处理的 PC 应用程序一起使用。

全息远程处理播放器适用于 HoloLens （第一代）和 HoloLens 2。  支持通过 HoloLens 进行全息远程处理的 PC 应用需要更新，以支持与 HoloLens 2 的全息远程处理。 如果你对支持哪些版本有任何疑问，请与你的应用程序提供商联系。

## <a name="connecting-to-the-holographic-remoting-player"></a>连接到全息远程处理播放器

按照应用的说明连接到全息远程处理播放器。 你需要输入你的 HoloLens 设备的 IP 地址，你可以在远程处理播放机的主屏幕上看到该设备，如下所示：

![全息远程处理播放器](images/holographicremotingplayer.png)

看到主屏幕时，您将知道您没有连接到应用程序。

请注意，全息远程处理连接**未加密**。 你应始终在你信任的安全 Wi-fi 连接上使用全息远程处理。

## <a name="quality-and-performance"></a>质量和性能

经验的质量和性能会因三个因素而异：
* **正在运行的全息体验**-呈现高分辨率或高度详细内容的应用可能需要更快的 PC 或更快的无线连接。
* **你的电脑硬件**-你的电脑需要能够以60帧/秒的速度运行和编码全息体验。 对于图形卡，我们通常建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更高。 同样，你的特定体验可能需要更高或更低端的卡。
* **Wi-fi 连接**-你的全息体验通过 wi-fi 进行流式处理。 使用具有低拥塞的快速网络来最大程度地提高质量。 使用通过以太网电缆而不是 Wi-fi 连接的 PC，还可以提高质量。

## <a name="diagnostics"></a>诊断

若要测量连接的质量，请在全息远程处理播放机的主屏幕上说 **"启用诊断"** 。 启用诊断后，应用会显示在**HoloLens （第一代）** 上：

* **FPS** -远程处理播放机每秒接收和呈现的呈现帧的平均数目。 理想为 60 FPS。
* **滞后**时间-帧从电脑进入 HoloLens 所需的平均时间量。 越低越好。 这在很大程度上依赖于 Wi-fi 网络。

在**HoloLens 2**上，应用将向你显示：

![全息远程处理播放器诊断](images/holographicremotingplayer-diag.png)

* **Render** -远程处理播放机在上一秒内呈现的帧数。 请注意，这与通过网络到达的帧数量无关（请参阅**视频帧**）。 此外，将显示呈现的帧间最后一秒的平均/最大呈现增量时间（以毫秒为单位）。

* **视频帧**-将跳过显示的第一个数字视频帧，第二个显示的是视频帧，第三个是接收视频帧。 所有数字表示上一秒的计数。
    * ```Received frames``` 是在上一秒钟到达的视频帧的数目。 正常情况下，这应为60，但如果不是，则指示由于网络问题而导致的帧被丢弃，或者远程/远程端不生成具有预期速率的帧。
    * ```Reused frames``` 是在上一秒钟内多次使用的视频帧的计数。 例如，如果视频帧晚到达，播放机的呈现循环仍将呈现一个帧，但需要*重复*使用它已用于前一帧的视频帧。
    * ```Skipped frames``` 是播放机的呈现循环尚未使用的视频帧的计数。 例如，网络抖动可能会造成视频帧无法均匀地分布。 例如，如果有一些延迟，而另一些时间到达时，则在以60Hz 运行时，它们不会再出现16.66 毫秒的增量。 在播放机的呈现循环的两个刻度之间，可能会有多个帧到达。 在这种情况下，播放机将*跳过*一个或多个帧，因为应该始终显示最近收到的视频帧。

    >[!NOTE]
    >当网络抖动时，跳过和重复使用的帧通常是相同的。 相反，如果您只看到跳过的帧，则表明播放机不会达到其目标帧速率。 在这种情况下，应注意诊断问题时的最大渲染增量时间。

* **视频帧增量**-上一秒收到的视频帧之间的最小/最大增量。 当网络抖动导致的问题时，此数字通常与跳过/重复使用帧关联。
* **延迟**-上一秒的平均周转时间（以毫秒为单位）。 在此上下文中，"周转时间" 是指从 HoloLens 向远程/远程端发送姿势/传感器数据到远程/远程端的时间，直到在 HoloLens 显示器上显示该姿势/遥测数据的视频帧。
* **丢弃的视频帧**-上一秒内丢弃的视频帧的数量，自建立连接后被丢弃的视频帧的数目。 被丢弃的视频帧的主要原因是，视频帧未按顺序到达，出于此原因，需要将其丢弃，因为已经有一个新的。 这类似于*丢弃的帧*，但原因是远程堆栈中的较低级别。 丢弃的视频帧只需要很严重的网络条件。



在主屏幕上，可以说 **"禁用诊断"** 以关闭诊断。

## <a name="pc-system-requirements"></a>PC 系统要求
* 你的电脑**必须**运行 Windows 10 周年更新或更高版本。
* 建议使用 GeForce GTX 970 或 AMD Radeon R9 290 或更好的图形卡。
* 建议你通过以太网将电脑连接到网络，以减少无线跃点的数量。

## <a name="see-also"></a>另请参阅
* [HoloLens （第一代）：添加全息远程处理](add-holographic-remoting.md)
* [HoloLens 2：编写全息远程处理远程应用](holographic-remoting-create-host.md)
* [全息远程处理软件许可条款](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)
