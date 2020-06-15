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
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="49cad-104">Unreal 中的 HoloLens 照片/视频摄像头</span><span class="sxs-lookup"><span data-stu-id="49cad-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="49cad-105">HoloLens 具有照片/视频 (PV) 摄像头，可用于混合现实捕获 (MRC)，应用还可以使用它来访问真实的视觉对象。</span><span class="sxs-lookup"><span data-stu-id="49cad-105">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="49cad-106">从 MRC 的 PV 摄像头渲染</span><span class="sxs-lookup"><span data-stu-id="49cad-106">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="49cad-107">这需要 Unreal Engine 4.25 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="49cad-107">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="49cad-108">系统和自定义 MRC 记录器通过将 PV 摄像头与沉浸式应用渲染的全息影像结合在一起，创建混合现实捕获。</span><span class="sxs-lookup"><span data-stu-id="49cad-108">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="49cad-109">默认情况下，混合现实捕获使用右眼的全息影像输出。</span><span class="sxs-lookup"><span data-stu-id="49cad-109">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="49cad-110">如果沉浸式应用选择[从 PV 摄像头进行渲染](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)，则会改用它。</span><span class="sxs-lookup"><span data-stu-id="49cad-110">If an immersive app chooses to [render from the PV Camera](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="49cad-111">这改进了真实世界与 MRC 视频中全息影像之间的映射。</span><span class="sxs-lookup"><span data-stu-id="49cad-111">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="49cad-112">若要选择从 PV 摄像机进行渲染：</span><span class="sxs-lookup"><span data-stu-id="49cad-112">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="49cad-113">调用 SetEnabledMixedRealityCamera 和 ResizeMixedRealityCamera </span><span class="sxs-lookup"><span data-stu-id="49cad-113">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="49cad-114">使用“尺寸 X”和“尺寸 Y”值设置视频尺寸。 </span><span class="sxs-lookup"><span data-stu-id="49cad-114">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第三人称摄像头](images/unreal-camera-3rd.PNG)

<span data-ttu-id="49cad-116">然后，Unreal 将处理 MRC 要从 PV 摄像头的角度进行渲染的请求。</span><span class="sxs-lookup"><span data-stu-id="49cad-116">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="49cad-117">仅当触发[混合现实捕获](mixed-reality-capture.md)时，才会要求应用从照片/视频摄像头的角度进行渲染。</span><span class="sxs-lookup"><span data-stu-id="49cad-117">Only when [Mixed Reality Capture](mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="49cad-118">使用 PV 摄像头</span><span class="sxs-lookup"><span data-stu-id="49cad-118">Using the PV Camera</span></span>

<span data-ttu-id="49cad-119">在游戏中，可以在运行时检索网络摄像头纹理，但需要在编辑器的“编辑 > 项目设置”中启用它：</span><span class="sxs-lookup"><span data-stu-id="49cad-119">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="49cad-120">转到“平台 > HoloLens > 功能”，然后选中“网络摄像头”。 </span><span class="sxs-lookup"><span data-stu-id="49cad-120">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="49cad-121">在运行时通过 StartCameraCapture 函数使用网络摄像头，通过 StopCameraCapture 函数停止录像。 </span><span class="sxs-lookup"><span data-stu-id="49cad-121">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![摄像头开始/停止](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="49cad-123">渲染图像</span><span class="sxs-lookup"><span data-stu-id="49cad-123">Rendering an image</span></span>
<span data-ttu-id="49cad-124">渲染摄像头图像：</span><span class="sxs-lookup"><span data-stu-id="49cad-124">To render the camera image:</span></span>
1. <span data-ttu-id="49cad-125">基于项目中的材料创建动态材料实例，下方的屏幕截图将其命名为“PVCamMat”。</span><span class="sxs-lookup"><span data-stu-id="49cad-125">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="49cad-126">将动态材料实例设置为“材料实例动态对象引用”变量。</span><span class="sxs-lookup"><span data-stu-id="49cad-126">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="49cad-127">设置场景中的对象的材料，它会将摄像头源渲染到这个新的动态材料实例。</span><span class="sxs-lookup"><span data-stu-id="49cad-127">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="49cad-128">启动计时器，用于将摄像头图像与材料绑定。</span><span class="sxs-lookup"><span data-stu-id="49cad-128">Start a timer that will be used to bind the camera image to the material.</span></span> 

![摄像头渲染](images/unreal-camera-render.PNG)

4. <span data-ttu-id="49cad-130">为此计时器创建新函数（在本例中为 MaterialTimer），并调用 GetARCameraImage 从网络摄像头获取纹理。 </span><span class="sxs-lookup"><span data-stu-id="49cad-130">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="49cad-131">如果此纹理有效，则将着色器中的纹理参数设置为此图像。</span><span class="sxs-lookup"><span data-stu-id="49cad-131">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="49cad-132">否则，请重新启动材质计时器。</span><span class="sxs-lookup"><span data-stu-id="49cad-132">Otherwise, start the material timer again.</span></span> 

![摄像头纹理](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="49cad-134">请确保材料的参数与绑定到颜色条目的 SetTextureParameterValue 中的名称匹配，</span><span class="sxs-lookup"><span data-stu-id="49cad-134">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="49cad-135">否则将无法正确显示摄像头图像。</span><span class="sxs-lookup"><span data-stu-id="49cad-135">Without this, the camera image can't be properly displayed.</span></span>

![摄像头纹理](images/unreal-camera-material.PNG)

## <a name="see-also"></a><span data-ttu-id="49cad-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49cad-137">See also</span></span>
* [<span data-ttu-id="49cad-138">可定位相机</span><span class="sxs-lookup"><span data-stu-id="49cad-138">Locatable camera</span></span>](locatable-camera.md)
* [<span data-ttu-id="49cad-139">面向开发人员的混合现实捕获</span><span class="sxs-lookup"><span data-stu-id="49cad-139">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
