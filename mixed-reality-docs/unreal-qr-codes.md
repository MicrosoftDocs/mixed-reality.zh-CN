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
# <a name="qr-codes-in-unreal"></a>Unreal 中的 QR 码

HoloLens 可以在世界空间中找到 QR 码，以便在现实世界中的已知位置呈现全息影像。  也可用于在同一位置的多个设备上呈现全息影像，以创建共享体验。 

若要在 HoloLens 上启用 QR 检测，请确保在“项目设置”>“平台”>“HoloLens”>“功能”下的 Unreal 编辑器中，选中“网络摄像头”功能。  

通过使用 StartARSession 函数启动 ARSession，来选择在 Unreal 中使用 QR 码跟踪。 

QR 码通过 Unreal 的 AR 跟踪几何系统显示为跟踪图像。  为此，请将“AR 可跟踪通知”组件添加到蓝图 Actor： 

![QR AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

然后，访问组件的详细信息，并单击待监视事件的绿色“+”按钮。  

![QR 事件](images/unreal-spatialmapping-events.PNG)

我们已在此订阅了 OnUpdateTrackedImage 以呈现 QR 码中心的一个点，并打印 QR 码的编码数据。 

![QR 呈现示例](images/unreal-qr-render.PNG)

首先，将跟踪图像转换为 ARTrackedQRCode，以验证当前更新的图像是否为 QR 码。  然后，可以通过 QRCode 变量检索编码数据。  可以从 GetLocalToWorldTransform 的位置检索 QR 码的左上角。  可通过 GetEstimateSize 检索维度。 

每个 QR 码还具有唯一的 GUID ID： 

![QR GUID](images/unreal-qr-guid.PNG)

## <a name="see-also"></a>另请参阅
* [QR 码跟踪](qr-code-tracking.md)
