---
title: Unity 播放模式
description: 在 Unity 编辑器中使用播放模式，无需部署应用即可在设备上预览所做的更改。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、远程处理、全息远程处理、全息远程处理播放器
ms.openlocfilehash: 6164d7ae1bc2d9ac13135f17132aca089e63ecdf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438223"
---
# <a name="unity-play-mode"></a>Unity 播放模式

处理 Unity 项目的快速方法是使用 "播放模式"。 这会在你的电脑上以本地方式在 Unity 编辑器中运行你的应用程序。 Unity 使用全息远程处理提供一种在真实的 HoloLens 设备上快速预览内容的方式。 播放模式还可与附加到开发 PC 的 Windows Mixed Reality 耳机一起使用。

## <a name="unity-play-mode-with-holographic-remoting"></a>采用全息远程处理的 Unity 播放模式

通过全息远程处理，你可以在 HoloLens 上体验你的应用程序，而在你的电脑上运行 Unity 编辑器。 注视、手势、语音和空间映射输入将从你的 HoloLens 发送到你的电脑。 然后，将呈现的帧发送回 HoloLens。 这是一种快速调试应用程序的绝佳方式，无需生成和部署完整项目。
1. 在 HoloLens 上，中转到**Microsoft Store**并安装 **[全息远程处理播放器](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** 应用。
2. 在 HoloLens 上，启动**全息远程处理播放器**应用。
3. 在 Unity 中，单击 "**窗口**" 菜单，并选择 "**全息模拟**"。
4. 将**仿真模式**设置为**远程设备**。
5. 对于**远程计算机**，请输入 HOLOLENS 的 IP 地址。
6. 单击**连接**。 应会看到**连接状态**更改为 "**已连接**"，并且会在 HoloLens 中看到屏幕显示为空白。
7. 单击 "**播放**" 按钮以启动播放模式，并在 HoloLens 上体验应用。

全息远程处理需要快速的 PC 和 Wi-fi 连接。 有关完整详细信息，请参阅[全息远程处理播放器](holographic-remoting-player.md)。

为了获得最佳结果，请确保应用正确设置了[焦点](focus-point-in-unity.md)。 这有助于全息远程处理最好地使场景适应无线连接的延迟。

## <a name="see-also"></a>另请参阅
* [全息远程播放器](holographic-remoting-player.md)
