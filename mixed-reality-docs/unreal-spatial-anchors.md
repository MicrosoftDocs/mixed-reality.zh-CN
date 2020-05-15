---
title: Unreal 中的空间定位点
description: Unreal 中空间定位点使用指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间定位点
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840136"
---
# <a name="spatial-anchors-in-unreal"></a>Unreal 中的空间定位点

空间定位点用于在应用程序会话之间保持真实世界空间中的全息影像。  这是通过 Unreal 以 ARPin 的形式出现的，并保存在 HoloLens 定位点存储中以便在未来会话中加载。 

在保存或加载定位点之前，请先检查定位点存储是否已准备就绪。  在定位点存储准备就绪之前，尝试调用任何 HoloLens 定位点函数都不会成功。  

![空间定位点存储准备就绪](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a>保存定位点

一旦应用程序的一个组件需要固定到世界，它可以按照以下顺序保存到定位点存储： 

![空间定位点保存](images/unreal-spatialanchors-save.PNG)

在此，我们将在已知位置生成一个 Actor，使用该位置和基于 Actor 类的名称创建一个 ARPin，将 Actor 添加到 ARPin，然后将引脚保存到 HoloLens 定位点存储中。  选择的定位点名称必须是唯一的，因此在本示例中，我们将追加当前时间戳。  如果定位点成功保存到定位点存储，则可以在 HoloLens 设备门户的“系统”>“映射管理器”>“设备上已保存的定位点文件”下检查定位点。 

## <a name="load-anchors"></a>加载定位点

当应用程序启动时，可以调用以下蓝图将组件还原到其定位点位置：

![空间定位点加载](images/unreal-spatialanchors-load.PNG)

在本例中，我们循环访问定位点存储中的所有定位点，在标识处生成一个 Actor，并将该 Actor 从定位点存储固定到 ARPin。  必须按标识生成 Actor，这一点很重要，因为定位点负责根据全息影像的保存位置在世界中重新定位全息影像，因此，此处添加的任何变形都将增加定位点的偏移量。 

还将查询定位点 ID，以便根据定位点的保存名称来生成不同的 Actor。 

## <a name="remove-anchors"></a>删除定位点 

完成定位点操作后，可以清除整个定位点存储，也可以从定位点存储中删除单个定位点，这样它们就不会包含在未来会话中： 

![空间定位点删除](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a>另请参阅
* [空间定位点](spatial-anchors.md)
* [坐标系统](coordinate-systems.md)
