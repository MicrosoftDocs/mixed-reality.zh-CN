---
title: Unreal 中的流式传输
description: 从 Unreal 中流式传输到 HoloLens 2 的指南
author: suwu
ms.author: suwu
ms.date: 6/8/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 流式传输, 电脑, 全息应用远程处理, 全息远程处理播放器, 文档
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 78a019f5b74b254c1f32ec85dc639df47648555f
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84888908"
---
# <a name="streaming-in-unreal"></a>Unreal 中的流式传输

## <a name="overview"></a>概述
从电脑流式传输到 HoloLens 提供了两大优势： 
* 它使混合现实应用可以利用电脑的计算能力。 
* 它有助于加快开发迭代的时间。 

首先，需要将[全息远程处理播放器](holographic-remoting-player.md)下载到 HoloLens 设备。 这使你的应用能够从以下来源直接流式传输到 HoloLens 上的远程处理播放器：

* Unreal Engine 编辑器
* 打包的 Windows 可执行文件 

进行流式传输时，你可以访问几乎所有相同的 HoloLens 功能，就像你在设备上运行应用程序时一样。 这包括[手关节跟踪](unreal-hand-tracking.md)（如果使用的是 HoloLens 2）、[空间映射](unreal-spatial-mapping.md)和[空间定位点](unreal-spatial-anchors.md)，但此[限制列表](holographic-remoting-troubleshooting.md)上的功能除外。 

> [!NOTE]
> 流式传输的质量严重依赖于 wifi 网络的强度。

## <a name="device-support"></a>设备支持

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>源</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第 1 代</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>沉浸式头戴显示设备</strong></td>
    </tr>
     <tr>
        <td>Unreal 编辑器</td>
        <td>✔</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Windows 包</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>从 Unreal 编辑器进行流式传输

作为开发人员，你会发现从 Unreal 编辑器流式传输到 HoloLens 设备在测试时会提供很大的好处，也就是说，你无需再等待你的应用生成和部署完成后才尝试更新。

可以在“Unreal 入门”教程系列的最后一部分中找到有关[从 Unreal 编辑器进行流式传输](unreal-uxt-ch6.md#device-only-streaming)的详细说明。

## <a name="streaming-from-a-packaged-windows-executable"></a>从打包的 Windows 可执行文件进行流式传输

从 Unreal 4.25.1 开始，可以通过执行以下步骤将应用从打包的 Windows 可执行文件流式传输到 HoloLens 2 设备： 

1. 转到编辑器菜单中的“文件”>“包项目”>“Windows”。 
    * 选择要保存包的位置，然后单击“选择文件夹”。

2. 包生成完成后，请打开 HoloLens 2 上的“全息远程处理播放器”，并记下 IP 地址。 
3. 使“全息远程处理播放器”保持打开状态，然后使用命令行提示符执行以下操作： 
    * 将 cd 插入到保存包的本地目录。
    * 输入以下命令：```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```

> [!NOTE]
> 项目设置中的应用程序名称应自动用于创建 Windows 包。 如果名称因某些原因而有所不同，请在命令提示符下使用 Windows 可执行文件名称。

按 Enter 键，随即将看到应用程序开始进行流式传输了！

## <a name="see-also"></a>另请参阅
* [全息远程处理版本历史记录](holographic-remoting-version-history.md)
* [编写自定义全息远程处理播放器应用](holographic-remoting-create-player.md)
* [使用全息远程处理建立安全连接](holographic-remoting-secure-connection.md)
