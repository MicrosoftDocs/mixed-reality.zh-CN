---
title: DirectX 中的定位照相机
description: 介绍如何在 HoloLens 应用中使用 view 点 (POV) 相机。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、定位相机、观点、POV、unporoject、媒体基础、MF、自定义接收器、演练、示例代码
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516866"
---
# <a name="locatable-camera-in-directx"></a><span data-ttu-id="bba34-104">DirectX 中的定位照相机</span><span class="sxs-lookup"><span data-stu-id="bba34-104">Locatable camera in DirectX</span></span>

<span data-ttu-id="bba34-105">本主题介绍如何设置[媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx)管道, 以便在 DirectX 应用中访问[照相机](locatable-camera.md), 其中包括允许你查找真实环境中生成的映像的帧元数据。</span><span class="sxs-lookup"><span data-stu-id="bba34-105">This topic describes how to set up a [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline to access the [camera](locatable-camera.md) in a DirectX app, including the frame metadata that will allow you to locate the images produced in the real world.</span></span>

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a><span data-ttu-id="bba34-106">Windows Media Capture 和媒体基础开发:IMFAttributes</span><span class="sxs-lookup"><span data-stu-id="bba34-106">Windows Media Capture and Media Foundation Development: IMFAttributes</span></span>

<span data-ttu-id="bba34-107">每个图像帧都[包含一个坐标系统](locatable-camera.md#images-with-coordinate-systems)以及两个重要转换。</span><span class="sxs-lookup"><span data-stu-id="bba34-107">Each image frame [includes a coordinate system](locatable-camera.md#images-with-coordinate-systems) , as well as two important transforms.</span></span> <span data-ttu-id="bba34-108">"视图" 变换将从提供的坐标系统映射到相机, 并将 "投影" 从相机映射到图像中的像素。</span><span class="sxs-lookup"><span data-stu-id="bba34-108">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="bba34-109">通过媒体基础的[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx), 坐标系统和2转换作为元数据嵌入到每个图像帧中。</span><span class="sxs-lookup"><span data-stu-id="bba34-109">The coordinate system and the 2 transforms are embedded as metadata in every image frame via Media Foundation's [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span></span>

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a><span data-ttu-id="bba34-110">使用 MF 自定义接收器读取属性和执行投影的示例用法</span><span class="sxs-lookup"><span data-stu-id="bba34-110">Sample usage of reading attributes with MF custom sink and doing projection</span></span>

<span data-ttu-id="bba34-111">在自定义 MF 接收器流 ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)) 中, 你将获得带有示例属性的[IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) :</span><span class="sxs-lookup"><span data-stu-id="bba34-111">In your custom MF Sink stream ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), you will get [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) with sample attributes:</span></span>

<span data-ttu-id="bba34-112">必须为基于 WinRT 的代码定义以下 MediaExtensions:</span><span class="sxs-lookup"><span data-stu-id="bba34-112">The following MediaExtensions must be defined for WinRT based code:</span></span>

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

<span data-ttu-id="bba34-113">不能从 WinRT Api 访问这些属性, 但需要[IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx)的媒体扩展实现 (效果) 或[IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx)和[IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (对于自定义接收器)。</span><span class="sxs-lookup"><span data-stu-id="bba34-113">You can't access these attributes from WinRT APIs, but requires Media Extension implementation of [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (for Effect) or [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) and [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (for Custom Sink).</span></span> <span data-ttu-id="bba34-114">处理此扩展中的示例时, 请在[IMFTransform::P rocessinput ()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::P rocessoutput ()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx)或[IMFStreamSink::P rocesssample ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)中处理此示例中的属性。</span><span class="sxs-lookup"><span data-stu-id="bba34-114">When you process the sample in this extension either in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) or [IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), you can query attributes like this sample.</span></span>

```
ComPtr<IUnknown> spUnknown;
ComPtr<Windows::Perception::Spatial::ISpatialCoordinateSystem> spSpatialCoordinateSystem;
ComPtr<Windows::Foundation::IReference<Windows::Foundation::Numerics::Matrix4x4>> spTransformRef;
Windows::Foundation::Numerics::Matrix4x4 worldToCameraMatrix;
Windows::Foundation::Numerics::Matrix4x4 viewMatrix;
Windows::Foundation::Numerics::Matrix4x4 projectionMatrix;
UINT32 cbBlobSize = 0;
hr = pSample->GetUnknown(MFSampleExtension_Spatial_CameraCoordinateSystem, IID_PPV_ARGS(&spUnknown));
if (SUCCEEDED(hr))
{
    hr = spUnknown.As(&spSpatialCoordinateSystem);
    if (FAILED(hr))
    {
        return hr;
    }
    hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraViewTransform,
                          (UINT8*)(&viewMatrix),
                          sizeof(viewMatrix),
                          &cbBlobSize);
    if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
    {
        hr = pSample->GetBlob(MFSampleExtension_Spatial_CameraProjectionTransform,
                              (UINT8*)(&projectionMatrix),
                              sizeof(projectionMatrix),
                              &cbBlobSize);
        if (SUCCEEDED(hr) && cbBlobSize == sizeof(Windows::Foundation::Numerics::Matrix4x4))
        {
            // Assume m_spCurrentCoordinateSystem is representing
            // world coordinate system application is using
            hr = m_spCurrentCoordinateSystem->TryGetTransformTo(spSpatialCoordinateSystem.Get(),
                                                                &spTransformRef);
            if (FAILED(hr))
            {
                return hr;
            }
            hr = spTransformRef->get_Value(&worldToCameraMatrix);
            if (FAILED(hr))
            {
                return hr;
            }
        }
    }
}
```

<span data-ttu-id="bba34-115">若要从相机访问纹理, 需要使用创建照相机帧纹理的相同 D3D 设备。</span><span class="sxs-lookup"><span data-stu-id="bba34-115">To access the texture from the camera, you need same D3D device which creates camera frame texture.</span></span> <span data-ttu-id="bba34-116">此 D3D 设备在捕获管道中的[IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx)中。</span><span class="sxs-lookup"><span data-stu-id="bba34-116">This D3D device is in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in the capture pipeline.</span></span> <span data-ttu-id="bba34-117">若要从媒体捕获获取 DXGI 设备管理器, 可以使用[IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx)和[IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx)接口。</span><span class="sxs-lookup"><span data-stu-id="bba34-117">To get the DXGI Device manager from Media Capture you can use [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) and [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.</span></span>

```
Microsoft::WRL::ComPtr<IAdvancedMediaCapture> spAdvancedMediaCapture;
Microsoft::WRL::ComPtr<IAdvancedMediaCaptureSettings> spAdvancedMediaCaptureSettings;
Microsoft::WRL::ComPtr<IMFDXGIDeviceManager> spDXGIDeviceManager;
// Assume mediaCapture is Windows::Media::Capture::MediaCapture and initialized
if (SUCCEEDED(((IUnknown *)(mediaCapture))->QueryInterface(IID_PPV_ARGS(&spAdvancedMediaCapture))))
{
    if (SUCCEEDED(spAdvancedMediaCapture->GetAdvancedMediaCaptureSettings(&spAdvancedMediaCaptureSettings)))
    {
        spAdvancedMediaCaptureSettings->GetDirectxDeviceManager(&spDXGIDeviceManager);
    }
}
```

<span data-ttu-id="bba34-118">你还可以启用鼠标和键盘输入作为 Windows Mixed Reality 应用的可选输入法。</span><span class="sxs-lookup"><span data-stu-id="bba34-118">You can also enable mouse and keyboard input as optional input methods for your Windows Mixed Reality app.</span></span> <span data-ttu-id="bba34-119">这也可能是适用于 HoloLens 的设备的一项很好的调试功能, 并且可能适用于连接到电脑的沉浸式耳机中运行的混合现实应用中的用户输入。</span><span class="sxs-lookup"><span data-stu-id="bba34-119">This can also be a great debugging feature for devices such as HoloLens, and may be desirable for user input in mixed reality apps running in immersive headsets attached to PCs.</span></span>
