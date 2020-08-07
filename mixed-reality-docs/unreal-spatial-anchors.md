---
title: Unreal 中的本地空间定位点
description: Unreal 中空间定位点使用指南
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 空间定位点
ms.openlocfilehash: b102d506b1d670291c3b97ca34d277e2597af043
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376041"
---
# <a name="local-spatial-anchors-in-unreal"></a>Unreal 中的本地空间定位点

## <a name="overview"></a>概述

空间定位点用于在应用程序会话之间保存真实世界空间中的全息影像。 这些是通过 Unreal 以 ARPin 的形式出现的，并保存在 HoloLens 定位点存储中以便在未来会话中加载。 当没有 Internet 连接时，本地定位点是理想的备用方案。

> [!IMPORTANT]
> 本地定位点存储在设备上，而 Azure 空间定位点存储在云中。 如果你想要使用 Azure 云服务来存储定位点，我们有一个文档可指导你如何集成 [Azure 空间定位点](unreal-azure-spatial-anchors.md)。 请注意，你可在同一项目中使用本地定位点和 Azure 定位点，不会发生冲突。

## <a name="checking-the-anchor-store"></a>检查定位点存储

在保存或加载定位点之前，需要检查定位点存储是否已准备就绪。  在定位点存储准备就绪之前，调用任何 HoloLens 定位点函数都不会成功。  

![空间定位点存储准备就绪](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a>保存定位点

一旦应用程序的一个组件需要固定到世界，它可以按照以下顺序保存到定位点存储： 

![空间定位点保存](images/unreal-spatialanchors-save.PNG)

细分如下：
1. 在已知位置生成 Actor。
2. 使用该位置和基于 Actor 的类的名称创建 ARPin。 
3. 将 Actor 添加到 ARPin并将引脚保存到 HoloLens 定位点存储。  
    * 选择的定位点名称必须是唯一的，因此在本示例中是当前时间戳。 

4. 如果定位点成功保存到定位点存储，则可以在 HoloLens 设备门户的“系统”>“映射管理器”>“设备上已保存的定位点文件”下检查定位点。 

## <a name="loading-anchors"></a>加载定位点

当应用程序启动时，可以使用以下蓝图将组件还原到其定位点位置：

![空间定位点加载](images/unreal-spatialanchors-load.PNG)

细分如下：
1. 循环访问定位点存储中的所有定位点。 
2. 按标识生成 Actor。
3. 将该 Actor 从定位点存储固定到 ARPin。  

    * 必须按标识生成 Actor，这一点很重要，因为定位点负责根据全息影像的保存位置在世界中重新定位全息影像。 因此，此处添加的任何变形都将增加定位点的偏移量。 

还将查询定位点 ID，以便根据定位点的保存名称来生成不同的 Actor。 

## <a name="removing-anchors"></a>删除定位点 

完成定位点后，可以使用“从 WMRAnchor 存储中删除 ARPin”和“从 WMRAnchor 存储中删除所有 ARPin”组件来清除单个定位点或整个定位点存储 。

![空间定位点删除](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> 请记住，空间定位点仍处于测试阶段，因此，请务必查看是否有更新的信息和功能。

## <a name="see-also"></a>另请参阅
* [Azure 空间定位点](unreal-azure-spatial-anchors.md)
* [空间定位点](spatial-anchors.md)
* [坐标系统](coordinate-systems.md)
