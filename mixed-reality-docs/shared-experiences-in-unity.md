---
title: Unity 中的共享体验
description: 在 Unity 应用程序的多个用户之间共享相同的全息影像。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共享、定位、WorldAnchor、MR 共享250、WorldAnchorTransferBatch、SpatialPerception、Azure、Azure 空间锚, ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516786"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="641f1-104">Unity 中的共享体验</span><span class="sxs-lookup"><span data-stu-id="641f1-104">Shared experiences in Unity</span></span>

<span data-ttu-id="641f1-105">共享体验是指多个用户, 每个用户都有自己的 HoloLens、iOS 或 Android 设备, 共同查看位于某个空间固定点的同一全息图并与之进行交互。</span><span class="sxs-lookup"><span data-stu-id="641f1-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="641f1-106">这是通过空间定位点共享来实现的。</span><span class="sxs-lookup"><span data-stu-id="641f1-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="641f1-107">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="641f1-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="641f1-108">你可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间锚点</a>来创建支持云的持久空间锚点, 你的应用可以在多个 HoloLens、IOS 和 Android 设备上查找。</span><span class="sxs-lookup"><span data-stu-id="641f1-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="641f1-109">通过在多个设备之间共享公用空间定位点, 每个用户都可以查看相对于同一物理位置中的定位点呈现的内容。</span><span class="sxs-lookup"><span data-stu-id="641f1-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="641f1-110">这可实现实时共享体验。</span><span class="sxs-lookup"><span data-stu-id="641f1-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="641f1-111">还可以使用 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间定位点</a>在 HoloLens、iOS 和 Android 设备上实现异步全息影像持久性。</span><span class="sxs-lookup"><span data-stu-id="641f1-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="641f1-112">通过共享持久的云空间定位点，多个设备可以随着时间推移观察相同的持久全息影像，即使这些设备没有同时出现，也是如此。</span><span class="sxs-lookup"><span data-stu-id="641f1-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="641f1-113">若要开始在 Unity 中构建共享体验, 请尝试执行5分钟的<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空间锚点 Unity 快速入门</a>。</span><span class="sxs-lookup"><span data-stu-id="641f1-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="641f1-114">启动并运行 Azure 空间锚点后, 便可以<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">在 Unity 中创建和定位锚</a>。</span><span class="sxs-lookup"><span data-stu-id="641f1-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="641f1-115">本地定位点传输</span><span class="sxs-lookup"><span data-stu-id="641f1-115">Local anchor transfers</span></span>

<span data-ttu-id="641f1-116">在不能使用 Azure 空间锚点的情况下,[本地定位点传输](local-anchor-transfers-in-unity.md)允许一台 hololens 设备导出要由第二个 hololens 设备导入的定位点。</span><span class="sxs-lookup"><span data-stu-id="641f1-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="641f1-117">请注意, 此方法提供的定位回调比 Azure 空间定位点更少, 并且不支持 iOS 和 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="641f1-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="641f1-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="641f1-118">See also</span></span>
* [<span data-ttu-id="641f1-119">混合现实中的共享体验</span><span class="sxs-lookup"><span data-stu-id="641f1-119">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="641f1-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间定位点</a></span><span class="sxs-lookup"><span data-stu-id="641f1-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="641f1-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">用于 Unity 的 Azure 空间定位点 SDK</a></span><span class="sxs-lookup"><span data-stu-id="641f1-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>