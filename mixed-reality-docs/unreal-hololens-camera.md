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
# <a name="hololens-camera-in-unreal"></a><span data-ttu-id="4d1fc-104">Unreal 中的 HoloLens 摄像头</span><span class="sxs-lookup"><span data-stu-id="4d1fc-104">HoloLens Camera in Unreal</span></span>

## <a name="third-camera-mixed-reality-capture"></a><span data-ttu-id="4d1fc-105">第三人称摄像头混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="4d1fc-105">Third Camera Mixed Reality Capture</span></span>

<span data-ttu-id="4d1fc-106">可以使用第三人称摄像头混合现实捕获 (MRC) 在 HoloLens 面板上从摄像头角度渲染混合现实捕获，而不是从目视纹理的角度。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-106">Third camera Mixed Reality Capture (MRC) can be used to render a mixed reality capture from the perspective of the camera on the HoloLens visor, rather than the perspective of the eye textures.</span></span>  <span data-ttu-id="4d1fc-107">这改进了真实世界与 MRC 视频中全息影像之间的映射。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-107">This improves the mapping between the real world and the holograms in the MRC video.</span></span> 

<span data-ttu-id="4d1fc-108">若要选择使用第三人称摄像头 MRC，请使用所需的视频尺寸调用 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-108">To opt into using third camera MRC, call SetEnabledMixedRealityCamera and ResizeMixedRealityCamera with the desired video dimensions.</span></span> 

![第三人称摄像头](images/unreal-camera-3rd.PNG)

<span data-ttu-id="4d1fc-110">然后，在 HoloLens 设备门户中录制一段 MRC 视频。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-110">Then record an MRC video in the HoloLens device portal.</span></span> 

## <a name="pv-camera"></a><span data-ttu-id="4d1fc-111">PV 摄像头</span><span class="sxs-lookup"><span data-stu-id="4d1fc-111">PV Camera</span></span>

<span data-ttu-id="4d1fc-112">还可以在运行时在游戏中获取网络摄像头纹理。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-112">The webcam texture can also be retrieved in the game at runtime.</span></span>  <span data-ttu-id="4d1fc-113">若要在 HoloLens 上获取网络摄像头纹理，首先确保在 Unreal 编辑器中的“项目设置”>“平台”>“HoloLens”>“功能”下选中“网络摄像头”功能。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-113">To get the webcam texture on HoloLens, first ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> 

<span data-ttu-id="4d1fc-114">在运行时使用 StartCameraCapture 函数选择使用网络摄像头。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-114">Opt into using the webcam at runtime with the StartCameraCapture function.</span></span>  <span data-ttu-id="4d1fc-115">使用 StopCameraCapture 函数停止捕获。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-115">Stop capturing with the StopCameraCapture function.</span></span> 

![摄像头开始/停止](images/unreal-camera-startstop.PNG)

<span data-ttu-id="4d1fc-117">若要渲染摄像头图像，首先要基于项目中的一个材质创建一个动态材质实例。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-117">To render the camera image, first create a dynamic material instance based on a material in the project.</span></span>  <span data-ttu-id="4d1fc-118">在此示例中，基于一种名为“PVCamMat”的材质。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-118">In this case based on a material named PVCamMat.</span></span>  <span data-ttu-id="4d1fc-119">将它设置为类型为“材质实例动态对象引用”的变量。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-119">Set this to a variable with type Material Instance Dynamic Object Reference.</span></span>  <span data-ttu-id="4d1fc-120">然后在场景中设置对象的材质，将摄像头素材渲染到这个新的动态材质实例，并启动一个计时器，用于将摄像头图像绑定到材质。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-120">Then set the material of the object in the scene that will render the camera feed to this new dynamic material instance and start a timer that will be used to bind the camera image to the material.</span></span> 

![摄像头渲染](images/unreal-camera-render.PNG)

<span data-ttu-id="4d1fc-122">为此计时器创建新函数（在本例中为 MaterialTimer），并调用 GetARCameraImage 从网络摄像头获取纹理。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-122">Create a new function for this timer, in this case MaterialTimer, and call GetARCameraImage to get the texture from the webcam.</span></span>  <span data-ttu-id="4d1fc-123">如果此纹理有效，请将着色器中的纹理参数设置为此图像。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-123">If this texture is valid, set a texture parameter in the shader to this image.</span></span>  <span data-ttu-id="4d1fc-124">否则，请重新启动材质计时器。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-124">Otherwise, start the material timer again.</span></span> 

![摄像头纹理](images/unreal-camera-texture.PNG)

<span data-ttu-id="4d1fc-126">材质应具有一个与 SetTextureParameterValue 中的名称相匹配的参数，该参数绑定到颜色项以便正确显示摄像头图像。</span><span class="sxs-lookup"><span data-stu-id="4d1fc-126">The material should have a parameter matching the name in SetTextureParameterValue bound to a color entry to properly display the camera image.</span></span> 

![摄像头纹理](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="4d1fc-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d1fc-128">See also</span></span>
* [<span data-ttu-id="4d1fc-129">可定位相机</span><span class="sxs-lookup"><span data-stu-id="4d1fc-129">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="4d1fc-130">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="4d1fc-130">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
