---
title: DirectX 中共享的空间锚
description: 说明如何通过共享空间锚点来同步两个 HoloLens 设备。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 同步, 空间定位, 传输, 多人, 查看, 方案, 演练, 示例代码, Azure, Azure 空间锚, ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516887"
---
# <a name="shared-experiences-in-directx"></a>DirectX 中的共享体验

共享体验是指多个用户, 每个用户都有自己的 HoloLens、iOS 或 Android 设备, 共同查看位于某个空间固定点的同一全息图并与之进行交互。 这是通过空间定位点共享来实现的。

## <a name="azure-spatial-anchors"></a>Azure 空间定位点

你可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a>来创建支持云的持久空间锚点, 你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找。  通过在多个设备之间共享公用空间定位点, 每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。  这可实现实时共享体验。

还可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>在 HoloLens、iOS 和 Android 设备上实现异步全息影像持久性。  通过共享持久的云空间定位点，多个设备可以随着时间推移观察相同的持久全息影像，即使这些设备没有同时出现，也是如此。

若要开始在 HoloLens 应用中构建共享体验, 请尝试5分钟的<a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空间锚快速入门</a>。

启动并运行 Azure 空间锚点后, 可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">在 HoloLens 上创建和查找锚</a>。  演练也适用于<a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 和 iOS</a> , 使你能够在所有设备上共享相同的定位标记。

## <a name="local-anchor-transfers"></a>本地定位点传输

在不能使用 Azure 空间锚点的情况下,[本地定位点传输](local-anchor-transfers-in-directx.md)允许一台 hololens 设备导出要由第二个 hololens 设备导入的定位点。  请注意, 此方法提供的定位回调比 Azure 空间定位点更少, 并且不支持 iOS 和 Android 设备。

## <a name="see-also"></a>请参阅
* [混合现实中的共享体验](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">用于 HoloLens 的 Azure 空间锚点 SDK</a>