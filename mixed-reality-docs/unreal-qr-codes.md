---
title: Unreal 中的 QR 码
description: Unreal 中 QR 码使用指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, qr 码
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342655"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="976b7-104">Unreal 中的 QR 码</span><span class="sxs-lookup"><span data-stu-id="976b7-104">QR codes in Unreal</span></span>

<span data-ttu-id="976b7-105">HoloLens 可以在世界空间中找到 QR 码，以便在现实世界中的已知位置呈现全息影像。</span><span class="sxs-lookup"><span data-stu-id="976b7-105">HoloLens can locate QR codes in world space to render holograms at known positions in the real world.</span></span>  <span data-ttu-id="976b7-106">也可用于在同一位置的多个设备上呈现全息影像，以创建共享体验。</span><span class="sxs-lookup"><span data-stu-id="976b7-106">This can also be used to render holograms on multiple devices in the same location to create a shared experience.</span></span> 

<span data-ttu-id="976b7-107">若要在 HoloLens 上启用 QR 检测，请确保在“项目设置”>“平台”>“HoloLens”>“功能”下的 Unreal 编辑器中，选中“网络摄像头”功能。</span><span class="sxs-lookup"><span data-stu-id="976b7-107">To enable QR detection on HoloLens, ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="976b7-108">通过使用 StartARSession 函数启动 ARSession，来选择在 Unreal 中使用 QR 码跟踪。</span><span class="sxs-lookup"><span data-stu-id="976b7-108">Opt into using QR code tracking in Unreal by starting an ARSession with the StartARSession function.</span></span> 

<span data-ttu-id="976b7-109">QR 码通过 Unreal 的 AR 跟踪几何系统显示为跟踪图像。</span><span class="sxs-lookup"><span data-stu-id="976b7-109">QR Codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span>  <span data-ttu-id="976b7-110">为此，请将“AR 可跟踪通知”组件添加到蓝图 Actor：</span><span class="sxs-lookup"><span data-stu-id="976b7-110">To use this, add an AR Trackable Notify component to a Blueprint actor:</span></span> 

![QR AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="976b7-112">然后，访问组件的详细信息，并单击待监视事件的绿色“+”按钮。</span><span class="sxs-lookup"><span data-stu-id="976b7-112">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span>  

![QR 事件](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="976b7-114">我们已在此订阅了 OnUpdateTrackedImage 以呈现 QR 码中心的一个点，并打印 QR 码的编码数据。</span><span class="sxs-lookup"><span data-stu-id="976b7-114">Here, we have subscribed to OnUpdateTrackedImage to render a point in the center of a QR Code and print the QR code’s encoded data.</span></span> 

![QR 呈现示例](images/unreal-qr-render.PNG)

<span data-ttu-id="976b7-116">首先，将跟踪图像转换为 ARTrackedQRCode，以验证当前更新的图像是否为 QR 码。</span><span class="sxs-lookup"><span data-stu-id="976b7-116">First cast the tracked image to an ARTrackedQRCode to verify that the current updated image is a QR code.</span></span>  <span data-ttu-id="976b7-117">然后，可以通过 QRCode 变量检索编码数据。</span><span class="sxs-lookup"><span data-stu-id="976b7-117">Then the encoded data can be retrieved with the QRCode variable.</span></span>  <span data-ttu-id="976b7-118">可以从 GetLocalToWorldTransform 的位置检索 QR 码的左上角。</span><span class="sxs-lookup"><span data-stu-id="976b7-118">The top-left of the QR code can be retrieved from the location of GetLocalToWorldTransform.</span></span>  <span data-ttu-id="976b7-119">可通过 GetEstimateSize 检索维度。</span><span class="sxs-lookup"><span data-stu-id="976b7-119">The dimensions can be retrieved with GetEstimateSize.</span></span> 

<span data-ttu-id="976b7-120">每个 QR 码还具有唯一的 GUID ID：</span><span class="sxs-lookup"><span data-stu-id="976b7-120">Every QR code also has a unique guid ID:</span></span> 

![QR GUID](images/unreal-qr-guid.PNG)

## <a name="see-also"></a><span data-ttu-id="976b7-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="976b7-122">See also</span></span>
* [<span data-ttu-id="976b7-123">QR 码跟踪</span><span class="sxs-lookup"><span data-stu-id="976b7-123">QR code tracking</span></span>](qr-code-tracking.md)
