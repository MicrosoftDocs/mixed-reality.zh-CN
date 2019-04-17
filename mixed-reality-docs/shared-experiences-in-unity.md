---
title: 在 Unity 中的共享的体验
description: 共享同一全息之间在 Unity 应用程序中的多个用户。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共享，定位点、 WorldAnchor、 MR 共享 250，WorldAnchorTransferBatch，SpatialPerception、 Azure、 Azure 空间的定位点，ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593062"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="2fb29-104">在 Unity 中的共享的体验</span><span class="sxs-lookup"><span data-stu-id="2fb29-104">Shared experiences in Unity</span></span>

<span data-ttu-id="2fb29-105">共享的体验是指多个用户，每个都有其自己的 HoloLens、 iOS 或 Android 设备，统称为查看或其定位在固定点在空间中的相同全息图与之交互。</span><span class="sxs-lookup"><span data-stu-id="2fb29-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="2fb29-106">这是通过共享空间定位点来实现。</span><span class="sxs-lookup"><span data-stu-id="2fb29-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="2fb29-107">Azure 空间定位点</span><span class="sxs-lookup"><span data-stu-id="2fb29-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="2fb29-108">可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>创建持久支持云的空间的定位点，该应用程序然后可以找到跨多个 HoloLens、 iOS 和 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="2fb29-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="2fb29-109">通过在多个设备之间共享公共空间定位点，每个用户可以看到呈现相对于同一物理位置中的锚点的内容。</span><span class="sxs-lookup"><span data-stu-id="2fb29-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="2fb29-110">这样实时共享体验。</span><span class="sxs-lookup"><span data-stu-id="2fb29-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="2fb29-111">此外可以使用<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空间的定位点</a>异步全息图暂留在 HoloLens、 iOS 和 Android 设备。</span><span class="sxs-lookup"><span data-stu-id="2fb29-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="2fb29-112">通过共享持久的云空间定位点，多个设备可以观察到相同的持久化全息图随着时间推移，即使这些设备不存在同时在一起。</span><span class="sxs-lookup"><span data-stu-id="2fb29-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="2fb29-113">若要开始构建在 Unity 中的共享的体验，请尝试出 5 分钟<a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">快速入门 Azure 空间的定位点 Unity</a>。</span><span class="sxs-lookup"><span data-stu-id="2fb29-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="2fb29-114">你可以在 Azure 空间的定位点与您使用启动并运行，然后<a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">创建并在 Unity 中定位的定位点</a>。</span><span class="sxs-lookup"><span data-stu-id="2fb29-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="2fb29-115">本地的定位点传输</span><span class="sxs-lookup"><span data-stu-id="2fb29-115">Local anchor transfers</span></span>

<span data-ttu-id="2fb29-116">在不能使用 Azure 空间的定位点，情况下[本地定位点传输](local-anchor-transfers-in-unity.md)允许一个 HoloLens 设备导出要导入第二个 HoloLens 设备的定位点。</span><span class="sxs-lookup"><span data-stu-id="2fb29-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="2fb29-117">请注意，此方法提供了比 Azure 空间的定位点，更不稳定的定位点回想一下，iOS 和 Android 设备不支持这种方法。</span><span class="sxs-lookup"><span data-stu-id="2fb29-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fb29-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="2fb29-118">See also</span></span>
* [<span data-ttu-id="2fb29-119">混合现实中的共享体验</span><span class="sxs-lookup"><span data-stu-id="2fb29-119">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="2fb29-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空间的定位点</a></span><span class="sxs-lookup"><span data-stu-id="2fb29-120"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="2fb29-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空间的定位点适用于 Unity SDK</a></span><span class="sxs-lookup"><span data-stu-id="2fb29-121"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>