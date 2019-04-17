---
title: 在 DirectX 可定位照相机
description: 介绍如何在 HoloLens 应用中使用的角度 (POV) 照相机。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens，可定位照相机、 的角度来看，POV unporoject、 媒体基础，MF，自定义接收器、 演练、 示例代码
ms.openlocfilehash: 374b61e3d9bb0e97d5f0c5c8e17a5c882a4ebcd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592402"
---
# <a name="locatable-camera-in-directx"></a><span data-ttu-id="1e09f-104">在 DirectX 可定位照相机</span><span class="sxs-lookup"><span data-stu-id="1e09f-104">Locatable camera in DirectX</span></span>

<span data-ttu-id="1e09f-105">本主题介绍如何设置[媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx)管道访问[照相机](locatable-camera.md)在 DirectX 应用中，包括将允许你查找映像的帧元数据，生成在现实生活中。</span><span class="sxs-lookup"><span data-stu-id="1e09f-105">This topic describes how to set up a [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx) pipeline to access the [camera](locatable-camera.md) in a DirectX app, including the frame metadata that will allow you to locate the images produced in the real world.</span></span>

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a><span data-ttu-id="1e09f-106">Windows 媒体捕获和 Media Foundation 开发：IMFAttributes</span><span class="sxs-lookup"><span data-stu-id="1e09f-106">Windows Media Capture and Media Foundation Development: IMFAttributes</span></span>

<span data-ttu-id="1e09f-107">每个图像帧[包括一个坐标系统](locatable-camera.md#images-with-coordinate-systems)，以及两个重要的转换。</span><span class="sxs-lookup"><span data-stu-id="1e09f-107">Each image frame [includes a coordinate system](locatable-camera.md#images-with-coordinate-systems) , as well as two important transforms.</span></span> <span data-ttu-id="1e09f-108">"视图"转换到相机，提供的坐标系统中的映射和从照相机"投影"映射至图像中的像素。</span><span class="sxs-lookup"><span data-stu-id="1e09f-108">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="1e09f-109">坐标系统和 2 个转换作为嵌入的元数据在通过媒体基础的每个图像帧[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="1e09f-109">The coordinate system and the 2 transforms are embedded as metadata in every image frame via Media Foundation's [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx).</span></span>

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a><span data-ttu-id="1e09f-110">示例用法： 读取具有 MF 自定义接收器的属性，并执行投影</span><span class="sxs-lookup"><span data-stu-id="1e09f-110">Sample usage of reading attributes with MF custom sink and doing projection</span></span>

<span data-ttu-id="1e09f-111">自定义的 MF 接收器流中 ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx))，则会[IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx)示例属性：</span><span class="sxs-lookup"><span data-stu-id="1e09f-111">In your custom MF Sink stream ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)), you will get [IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) with sample attributes:</span></span>

<span data-ttu-id="1e09f-112">必须为 WinRT 基于代码定义以下 MediaExtensions:</span><span class="sxs-lookup"><span data-stu-id="1e09f-112">The following MediaExtensions must be defined for WinRT based code:</span></span>

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

<span data-ttu-id="1e09f-113">不能从 WinRT Api 访问这些属性，但需要媒体扩展插件实现[IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) （适用于会有影响） 或[IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx)并[IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (自定义接收器）。</span><span class="sxs-lookup"><span data-stu-id="1e09f-113">You can't access these attributes from WinRT APIs, but requires Media Extension implementation of [IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx) (for Effect) or [IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx) and [IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (for Custom Sink).</span></span> <span data-ttu-id="1e09f-114">当处理此扩展中的示例可以在[IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx)或[IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)，可以查询像本示例这样的属性。</span><span class="sxs-lookup"><span data-stu-id="1e09f-114">When you process the sample in this extension either in [IMFTransform::ProcessInput()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::ProcessOutput()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx) or [IMFStreamSink::ProcessSample()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx), you can query attributes like this sample.</span></span>

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

<span data-ttu-id="1e09f-115">若要从照相机访问纹理，需要创建照相机帧纹理相同 D3D 设备。</span><span class="sxs-lookup"><span data-stu-id="1e09f-115">To access the texture from the camera, you need same D3D device which creates camera frame texture.</span></span> <span data-ttu-id="1e09f-116">此 D3D 设备处于[IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx)捕获管道中。</span><span class="sxs-lookup"><span data-stu-id="1e09f-116">This D3D device is in [IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx) in the capture pipeline.</span></span> <span data-ttu-id="1e09f-117">若要获得 DXGI 设备管理器可以使用捕获媒体[IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx)并[IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx)接口。</span><span class="sxs-lookup"><span data-stu-id="1e09f-117">To get the DXGI Device manager from Media Capture you can use [IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx) and [IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx) interfaces.</span></span>

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

<span data-ttu-id="1e09f-118">此外可以启用鼠标和键盘输入作为 Windows Mixed Reality 应用的可选输入方法。</span><span class="sxs-lookup"><span data-stu-id="1e09f-118">You can also enable mouse and keyboard input as optional input methods for your Windows Mixed Reality app.</span></span> <span data-ttu-id="1e09f-119">这也可以是一种很好的调试功能，用于设备，例如 HoloLens，并可能也适用于在附加至 Pc 的沉浸式耳机中运行的混合的现实应用中的用户输入。</span><span class="sxs-lookup"><span data-stu-id="1e09f-119">This can also be a great debugging feature for devices such as HoloLens, and may be desirable for user input in mixed reality apps running in immersive headsets attached to PCs.</span></span>
