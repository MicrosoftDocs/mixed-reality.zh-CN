---
title: Unreal 中的 HoloLens 摄像头
description: Unreal 中 HoloLens 摄像头使用指南
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 摄像头, 第三人称摄像头, MRC
ms.openlocfilehash: 9ef9ce27d161130c6b9f3aa6bb1dbc47d7608ad9
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840116"
---
# <a name="hololens-camera-in-unreal"></a>Unreal 中的 HoloLens 摄像头

## <a name="third-camera-mixed-reality-capture"></a>第三人称摄像头混合现实捕获

可以使用第三人称摄像头混合现实捕获 (MRC) 在 HoloLens 面板上从摄像头角度渲染混合现实捕获，而不是从目视纹理的角度。  这改进了真实世界与 MRC 视频中全息影像之间的映射。 

若要选择使用第三人称摄像头 MRC，请使用所需的视频尺寸调用 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera。 

![第三人称摄像头](images/unreal-camera-3rd.PNG)

然后，在 HoloLens 设备门户中录制一段 MRC 视频。 

## <a name="pv-camera"></a>PV 摄像头

还可以在运行时在游戏中获取网络摄像头纹理。  若要在 HoloLens 上获取网络摄像头纹理，首先确保在 Unreal 编辑器中的“项目设置”>“平台”>“HoloLens”>“功能”下选中“网络摄像头”功能。 

在运行时使用 StartCameraCapture 函数选择使用网络摄像头。  使用 StopCameraCapture 函数停止捕获。 

![摄像头开始/停止](images/unreal-camera-startstop.PNG)

若要渲染摄像头图像，首先要基于项目中的一个材质创建一个动态材质实例。  在此示例中，基于一种名为“PVCamMat”的材质。  将它设置为类型为“材质实例动态对象引用”的变量。  然后在场景中设置对象的材质，将摄像头素材渲染到这个新的动态材质实例，并启动一个计时器，用于将摄像头图像绑定到材质。 

![摄像头渲染](images/unreal-camera-render.PNG)

为此计时器创建新函数（在本例中为 MaterialTimer），并调用 GetARCameraImage 从网络摄像头获取纹理。  如果此纹理有效，请将着色器中的纹理参数设置为此图像。  否则，请重新启动材质计时器。 

![摄像头纹理](images/unreal-camera-texture.PNG)

材质应具有一个与 SetTextureParameterValue 中的名称相匹配的参数，该参数绑定到颜色项以便正确显示摄像头图像。 

![摄像头纹理](images/unreal-camera-material.PNG)

## <a name="see-also"></a>另请参阅
* [可定位相机](locatable-camera.md)
* [面向开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)
