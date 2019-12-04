---
title: Unreal 开发概述
description: 在 Unreal 中构建混合现实应用入门。
author: sw5813
ms.author: suwu
ms.date: 10/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, 流式传输, 远程处理, 混合现实, 开发, 入门, 新项目, 仿真器, 文档
ms.openlocfilehash: 96b0259e4ac567389f999d3a453fb68bb848b266
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491169"
---
# <a name="unreal-development-overview"></a>Unreal 开发概述

对 Unreal Engine 4 的混合现实支持现在为 Beta 版！ 如果不熟悉 Unreal 开发，不妨浏览一下 <a href="https://docs.unrealengine.com//GettingStarted/index.html" target="_blank">Unreal Engine 4 入门</a>页面。 如果你需要资产，Unreal 有一个包罗万象的<a href="https://www.unrealengine.com/marketplace//store" target="_blank">市场</a>。 

有了对 Unreal Engine 4 的基本了解以后，即可访问 Unreal Engine 文档站点上的 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/index.html" target="_blank">Microsoft HoloLens 开发</a>页面，了解如果构建应用并在 HoloLens 上运行它们。 若要与在 Unreal 中构建混合现实应用的社区人员交流心得，请务必访问 <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Unreal 混合现实论坛</a>。 可以在那里查找可能会遇到的问题的解决方案。

## <a name="installing-the-prerequisites"></a>安装必备组件

若要开始在 Unreal 中构建 HoloLens 2 应用，需要 [HoloLens 2 仿真器](using-the-hololens-emulator.md)或 HoloLens 头戴显示设备。 还需安装最新版 Visual Studio，其工作负荷和组件列在 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/Prerequisites/index.html" target="_blank">Unreal 的 HoloLens 2 必备组件</a>中。

## <a name="building-and-running-your-unreal-app"></a>构建并运行 Unreal 应用

首先，<a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/HowTo/PackageApp/index.html" target="_blank">将 HoloLens 2 应用打包</a>。 接下来，选择要将包部署到的位置：
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartEmulator/index.html" target="_blank">部署到 HoloLens 2 仿真器</a>
* <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartDevice/index.html" target="_blank">部署到 HoloLens 2 头戴显示设备</a>

## <a name="streaming-your-app-to-a-headset-via-the-holographic-remoting-player"></a>通过全息远程处理播放器将应用流式传输到头戴显示设备

将应用从桌面设备流式传输到 HoloLens 头戴显示设备上的全息远程处理播放器应用有两大好处： 
* 加快开发速度，这样就不需每次进行更改时都将应用重新打包并上传
* 充分利用桌面设备的功能，这样你就可以渲染尽可能多的多边形（只要桌面设备的 GPU 允许），不受头戴显示设备上提供的计算机的限制

若要开始流式传输，请参阅 <a href="https://docs.unrealengine.com//Platforms/AR/HoloLens2/QuickStartStreaming/index.html" target="_blank">HoloLens 2 流送快速入门</a>[]()。

## <a name="see-also"></a>另请参阅
* <a href="https://docs.unrealengine.com//Platforms/Mobile/Performance/index.html" target="_blank">移动设备的 Unreal 性能指南</a>
