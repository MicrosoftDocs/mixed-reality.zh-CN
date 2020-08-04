---
layout: LandingPage
title: 混合现实云服务
description: 混合现实云服务资源。
author: hferrone
ms.author: v-haferr
ms.date: 06/5/2020
ms.topic: overview
ms.localizationpriority: high
keywords: 混合现实, 开发, 开发, HoloLens, 云服务
ms.openlocfilehash: 26c5f91eab2b39fbd809010ab0ac738d81dff854
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390214"
---
# <a name="cloud-services"></a>云服务

## <a name="overview"></a>概述

混合现实云服务（例如 Azure 远程渲染和 Azure 空间定位点）可帮助开发人员在各种平台上构建引人注目的沉浸式体验 。 借助这些服务，当你创建应用程序来进行 3D 训练、预测性设备维护和设计审查时，可在项目中集成空间感知 - 所有操作均在用户环境的上下文中进行。

此外，还有其他混合现实工具合集未包含的 Azure 服务也可轻松添加到你的现有项目中。 如果你要你针对 Unity 进行开发，本页底部列出了大量[教程](#standalone-services)助你入门。

## <a name="mixed-reality-services"></a>混合现实服务

### <a name="azure-remote-rendering"></a>Azure 远程渲染
[Azure 远程渲染](https://docs.microsoft.com/azure/remote-rendering) (ARR) 是一项服务，可用于实时渲染高度复杂的 3D 模型。 ARR 目前为公共预览版。 可将它添加到面向 HoloLens 2 或 Windows 桌面电脑的 Unity 或 Native C++ 项目中。

![Unity 展示应用中的 Azure 远程渲染示例](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure 空间定位点
[Azure 空间定位点](https://docs.microsoft.com/azure/spatial-anchors) (ASA) 是一项跨平台服务，可用于构建空间感知的混合现实应用程序。 借助 Azure 空间定位点，你可按真实世界的规模跨多台设备映射、保存和共享全息内容。

![Azure 空间定位点示例](images/persistence.gif)

可在多种环境中开发该服务，并将其部署到大量设备和平台上。 这样的话，它们自带列表上的可用平台不用进行这些操作：
* Unity for HoloLens
* Unity for iOS
* Unity for Android
* 本机 iOS
* 本机 Android
* 用于 HoloLens 的 C++/WinRT 和 DirectX
* Xamarin for iOS
* Xamarin for Android

## <a name="standalone-services"></a>独立服务
下面列出的独立服务不适用于混合现实，但在各种开发上下文中都很有用。 如果要在 Unity 中开发，其中的每项服务都可集成到你的新项目或现有项目中。

### <a name="device-support"></a>设备支持
<table>
    <tr>
        <td><strong>Azure 云服务</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens 第 1 代</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>沉浸式头戴显示设备</strong></a></td>
    </tr>
     <tr>
        <td><a href="mr-azure-301.md">语言翻译</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302.md">计算机视觉</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-302b.md">自定义视觉</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-303.md">跨设备通知</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-304.md">人脸识别</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-305.md">Functions 和存储</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-306.md">流式传输视频</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-307.md">机器学习</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-308.md">Functions 和存储</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-309.md">Application insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-310.md">对象检测</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="mr-azure-312.md">机器人集成</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>
