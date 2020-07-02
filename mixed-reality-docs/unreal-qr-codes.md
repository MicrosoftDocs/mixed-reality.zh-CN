---
title: Unreal 中的 QR 码
description: Unreal 中 QR 码使用指南
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, qr 码
ms.openlocfilehash: cf6c113f6bf4a13a96f46d6420a3093966455c3b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720383"
---
# <a name="qr-codes-in-unreal"></a>Unreal 中的 QR 码

## <a name="overview"></a>概述

HoloLens 2 可以使用网络摄像头查看世界空间中的 QR 码，这会在每个代码的实际位置使用坐标系统将其呈现为全息影像。  除了单个 QR 码，HoloLens 2 还可以在多个设备上的同一位置呈现全息影像，以创建共享体验。 请确保遵循将 QR 码添加到应用程序的最佳做法：

- 安静区域
- 照明和背景
- 大小、距离和角度位置

将 QR 码置于应用中时，请特别注意[环境注意事项](environment-considerations-for-hololens.md)。 有关每个主题的详细信息以及下载所需 NuGet 包的说明，请参阅主 [QR 码跟踪](qr-code-tracking.md)文档。 

## <a name="enabling-qr-detection"></a>启用 QR 检测
由于 HoloLens 2 需要使用网络摄像头来查看 QR 码，因此需要在项目设置中将其启用：
- 打开“编辑”>“项目设置”，滚动到“平台”部分，然后单击“HoloLens”。
    + 展开“功能”部分，选中“网络摄像头”。  

还需要通过[添加 ARSessionConfig 资产](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)来选择使用 QR 码跟踪。

## <a name="setting-up-a-tracked-image"></a>设置跟踪图像

QR 码通过 Unreal 的 AR 跟踪几何系统显示为跟踪图像。 若要实现此操作，需执行以下操作：
1. 创建蓝图，并添加“ARTrackableNotify”组件。

![QR AR 可跟踪通知](images/unreal-spatialmapping-artrackablenotify.PNG)

2. 选择“ARTrackableNotify”，然后在“详细信息”面板中展开“事件”部分。 

![QR 事件](images/unreal-spatialmapping-events.PNG)

3. 单击“关于添加跟踪几何”旁的 +，将节点添加到事件图中。
    - 可以在 [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 组件 API 中找到事件的完整列表。 

![QR 呈现示例](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a>使用跟踪图像
下图中的事件图显示了 OnUpdateTrackedImage 事件，该事件用于呈现 QR 码中心的一个点并输出其数据。 

![QR 呈现示例](images/unreal-qr-render.PNG)

以下是具体过程：
1. 首先，将跟踪图像转换为 ARTrackedQRCode，以检查当前更新的图像是否为 QR 码。  
2. 编码数据是从 QRCode 变量中检索的。 可以从 GetLocalToWorldTransform 位置获取左上方的 QR 码，并在 GetEstimateSize 中获取维度。 

还可以在代码中[获取 QR 码的坐标系统](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)。

## <a name="finding-the-unique-id"></a>查找唯一 ID
每个 QR 码都具有一个唯一的 GUID ID，可以通过以下方式查找：
- 拖放“作为 ARTracked QRCode”引脚并搜索“获取唯一 ID”。

![QR GUID](images/unreal-qr-guid.PNG)

QR 码幕后还有很多内容等待挖掘，因此体验之旅并没有就此结束。 请务必查看下面的链接，以了解更多详细信息。

## <a name="see-also"></a>另请参阅
* [空间映射](spatial-mapping.md)
* [全息影像](hologram.md)
* [坐标系统](coordinate-systems.md)