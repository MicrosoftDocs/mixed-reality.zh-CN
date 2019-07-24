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
# <a name="locatable-camera-in-directx"></a>DirectX 中的定位照相机

本主题介绍如何设置[媒体基础](https://msdn.microsoft.com/library/windows/desktop/ms694197(v=vs.85).aspx)管道, 以便在 DirectX 应用中访问[照相机](locatable-camera.md), 其中包括允许你查找真实环境中生成的映像的帧元数据。

## <a name="windows-media-capture-and-media-foundation-development-imfattributes"></a>Windows Media Capture 和媒体基础开发:IMFAttributes

每个图像帧都[包含一个坐标系统](locatable-camera.md#images-with-coordinate-systems)以及两个重要转换。 "视图" 变换将从提供的坐标系统映射到相机, 并将 "投影" 从相机映射到图像中的像素。 通过媒体基础的[IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx), 坐标系统和2转换作为元数据嵌入到每个图像帧中。

### <a name="sample-usage-of-reading-attributes-with-mf-custom-sink-and-doing-projection"></a>使用 MF 自定义接收器读取属性和执行投影的示例用法

在自定义 MF 接收器流 ([IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx)) 中, 你将获得带有示例属性的[IMFSample](https://msdn.microsoft.com/library/windows/desktop/ms702192(v=vs.85).aspx) :

必须为基于 WinRT 的代码定义以下 MediaExtensions:

```
EXTERN_GUID(MFSampleExtension_Spatial_CameraViewTransform, 0x4e251fa4, 0x830f, 0x4770, 0x85, 0x9a, 0x4b, 0x8d, 0x99, 0xaa, 0x80, 0x9b);
EXTERN_GUID(MFSampleExtension_Spatial_CameraCoordinateSystem, 0x9d13c82f, 0x2199, 0x4e67, 0x91, 0xcd, 0xd1, 0xa4, 0x18, 0x1f, 0x25, 0x34);
EXTERN_GUID(MFSampleExtension_Spatial_CameraProjectionTransform, 0x47f9fcb5, 0x2a02, 0x4f26, 0xa4, 0x77, 0x79, 0x2f, 0xdf, 0x95, 0x88, 0x6a);
```

不能从 WinRT Api 访问这些属性, 但需要[IMFTransform](https://msdn.microsoft.com/library/windows/desktop/ms696260(v=vs.85).aspx)的媒体扩展实现 (效果) 或[IMFMediaSink](https://msdn.microsoft.com/library/windows/desktop/ms694262(v=vs.85).aspx)和[IMFStreamSink](https://msdn.microsoft.com/library/windows/desktop/ms705657(v=vs.85).aspx) (对于自定义接收器)。 处理此扩展中的示例时, 请在[IMFTransform::P rocessinput ()](https://msdn.microsoft.com/library/windows/desktop/ms703131(v=vs.85).aspx)/[IMFTransform::P rocessoutput ()](https://msdn.microsoft.com/library/windows/desktop/ms704014(v=vs.85).aspx)或[IMFStreamSink::P rocesssample ()](https://msdn.microsoft.com/library/windows/desktop/ms696208(v=vs.85).aspx)中处理此示例中的属性。

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

若要从相机访问纹理, 需要使用创建照相机帧纹理的相同 D3D 设备。 此 D3D 设备在捕获管道中的[IMFDXGIDeviceManager](https://msdn.microsoft.com/library/windows/desktop/hh447906(v=vs.85).aspx)中。 若要从媒体捕获获取 DXGI 设备管理器, 可以使用[IAdvancedMediaCapture](https://msdn.microsoft.com/library/windows/desktop/hh802709(v=vs.85).aspx)和[IAdvancedMediaCaptureSettings](https://msdn.microsoft.com/library/windows/desktop/hh802712(v=vs.85).aspx)接口。

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

你还可以启用鼠标和键盘输入作为 Windows Mixed Reality 应用的可选输入法。 这也可能是适用于 HoloLens 的设备的一项很好的调试功能, 并且可能适用于连接到电脑的沉浸式耳机中运行的混合现实应用中的用户输入。
