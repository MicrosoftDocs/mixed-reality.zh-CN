---
title: 共享中 DirectX 的空间定位点
description: 介绍如何同步两个 HoloLens 设备通过共享空间的定位点。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens，同步，空间定位点、 传输、 之多人游戏，视图、 方案、 演练、 示例代码中，Azure，Azure 空间的定位点，ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593060"
---
# <a name="shared-experiences-in-directx"></a>在 DirectX 中的共享的体验

共享的体验是指多个用户，每个都有其自己的 HoloLens、 iOS 或 Android 设备，统称为查看或其定位在固定点在空间中的相同全息图与之交互。 这是通过共享空间定位点来实现。

## <a name="azure-spatial-anchors"></a>Azure 空间定位点

可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>创建持久支持云的空间的定位点，该应用程序然后可以找到跨多个 HoloLens、 iOS 和 Android 设备。  通过在多个设备之间共享公共空间定位点，每个用户可以看到呈现相对于同一物理位置中的锚点的内容。  这样实时共享体验。

此外可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>异步全息图暂留在 HoloLens、 iOS 和 Android 设备。  通过共享持久的云空间定位点，多个设备可以观察到相同的持久化全息图随着时间推移，即使这些设备不存在同时在一起。

若要开始构建 HoloLens 应用程序中的共享的体验，请尝试出 5 分钟<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">快速入门 Azure 空间的定位点 HoloLens</a>。

你可以在 Azure 空间的定位点与您使用启动并运行，然后<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">创建并在 HoloLens 上找到的定位点</a>。  演练是可用于<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> ，使您能够共享的所有设备上的同一个定位点。

## <a name="local-anchor-transfers"></a>本地的定位点传输

在不能使用 Azure 空间的定位点，情况下[本地定位点传输](local-anchor-transfers-in-directx.md)允许一个 HoloLens 设备导出要导入第二个 HoloLens 设备的定位点。  请注意，此方法提供了比 Azure 空间的定位点，更不稳定的定位点回想一下，iOS 和 Android 设备不支持这种方法。

## <a name="see-also"></a>请参阅
* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure 空间的定位点 HoloLens 的 SDK</a>