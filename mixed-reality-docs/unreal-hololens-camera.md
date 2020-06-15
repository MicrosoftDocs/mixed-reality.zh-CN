---
title: Unreal 中的 HoloLens 照片/视频摄像头
description: Unreal 中 HoloLens 照片/视频摄像头使用指南
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 混合现实, 开发, 功能, 文档, 指南, 全息影像, 摄像头, PV 摄像头, MRC
ms.openlocfilehash: 06ceb26d58fe60848e5e90360aa2e05984a901c5
ms.sourcegitcommit: f24ac845e184c2f90e8b15adab9addb913f5cb83
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84451332"
---
# <a name="hololens-photovideo-camera-in-unreal"></a>Unreal 中的 HoloLens 照片/视频摄像头

HoloLens 具有照片/视频 (PV) 摄像头，可用于混合现实捕获 (MRC)，应用还可以使用它来访问真实的视觉对象。

## <a name="render-from-the-pv-camera-for-mrc"></a>从 MRC 的 PV 摄像头渲染

> [!NOTE]
> 这需要 Unreal Engine 4.25 或更高版本。

系统和自定义 MRC 记录器通过将 PV 摄像头与沉浸式应用渲染的全息影像结合在一起，创建混合现实捕获。

默认情况下，混合现实捕获使用右眼的全息影像输出。 如果沉浸式应用选择[从 PV 摄像头进行渲染](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，则会改用它。 这改进了真实世界与 MRC 视频中全息影像之间的映射。

若要选择从 PV 摄像机进行渲染：

1. 调用 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera 
    * 使用“尺寸 X”和“尺寸 Y”值设置视频尺寸。 

![第三人称摄像头](images/unreal-camera-3rd.PNG)

然后，Unreal 将处理 MRC 要从 PV 摄像头的角度进行渲染的请求。

> [!NOTE]
> 仅当触发[混合现实捕获](mixed-reality-capture.md)时，才会要求应用从照片/视频摄像头的角度进行渲染。

## <a name="using-the-pv-camera"></a>使用 PV 摄像头

在游戏中，可以在运行时检索网络摄像头纹理，但需要在编辑器的“编辑 > 项目设置”中启用它：
1. 转到“平台 > HoloLens > 功能”，然后选中“网络摄像头”。 
    * 在运行时通过 StartCameraCapture 函数使用网络摄像头，通过 StopCameraCapture 函数停止录像。 

![摄像头开始/停止](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>渲染图像
渲染摄像头图像：
1. 基于项目中的材料创建动态材料实例，下方的屏幕截图将其命名为“PVCamMat”。  
2. 将动态材料实例设置为“材料实例动态对象引用”变量。  
3. 设置场景中的对象的材料，它会将摄像头源渲染到这个新的动态材料实例。
    * 启动计时器，用于将摄像头图像与材料绑定。 

![摄像头渲染](images/unreal-camera-render.PNG)

4. 为此计时器创建新函数（在本例中为 MaterialTimer），并调用 GetARCameraImage 从网络摄像头获取纹理。   
5. 如果此纹理有效，则将着色器中的纹理参数设置为此图像。  否则，请重新启动材质计时器。 

![摄像头纹理](images/unreal-camera-texture.PNG)

5. 请确保材料的参数与绑定到颜色条目的 SetTextureParameterValue 中的名称匹配， 否则将无法正确显示摄像头图像。

![摄像头纹理](images/unreal-camera-material.PNG)

## <a name="see-also"></a>另请参阅
* [可定位相机](locatable-camera.md)
* [面向开发人员的混合现实捕获](mixed-reality-capture-for-developers.md)
