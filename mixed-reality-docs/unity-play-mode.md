---
title: Unity 游戏模式
description: 使用在 Unity 编辑器中播放模式下，若要预览设备上所做的更改，无需部署应用程序。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、 远程处理、 全息版的远程处理、 全息版的远程处理的播放机
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590159"
---
# <a name="unity-play-mode"></a>Unity 游戏模式

处理你的 Unity 项目的快捷方法是使用"播放模式"。 此应用程序在本地运行 Unity 编辑器中您的 PC 上。 Unity 使用 Holographic 远程处理提供预览真实的 HoloLens 设备中的内容的快速方法。

## <a name="unity-play-mode-with-holographic-remoting"></a>全息版的远程处理与 unity 游戏模式

使用 Holographic 远程处理，您可能会在 Unity 编辑器中运行你的 PC 上遇到 HoloLens，对应用程序。 提供注视、 手势、 语音和输入的空间映射在 HoloLens 从您的电脑发送。 呈现的帧然后发回给你 HoloLens 中。 这是快速而无需构建和部署完整的项目中调试您的应用程序的好办法。
1. 在你 HoloLens 上转到**Microsoft Store**并安装 **[Holographic 远程处理播放器](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
2. 在你 HoloLens 上启动**Holographic 远程处理的播放机**应用。
3. 在 Unity 中，转到**窗口**菜单，然后选择**Holographic 仿真**。
4. 设置**仿真模式**到**远程连接到设备**。
5. 有关**远程计算机**，输入你 HoloLens 的 IP 地址。
6. 单击“连接”。 应会看到**连接状态**更改为**已连接**，变为空白 HoloLens 中显示屏幕。
7. 单击**播放**按钮以开始播放模式下，并体验在 HoloLens 上的应用程序。

全息版的远程处理需要快速的 PC 和 Wi-fi 连接。 请参阅[Holographic 远程处理的播放机](holographic-remoting-player.md)有关完整详细信息。

为获得最佳结果，请确保正确设置你的应用[关注点](focus-point-in-unity.md)。 这有助于 Holographic 远程处理来最好地调整您的无线连接的延迟到您的场景。

## <a name="see-also"></a>请参阅
* [全息版的远程处理的播放机](holographic-remoting-player.md)
