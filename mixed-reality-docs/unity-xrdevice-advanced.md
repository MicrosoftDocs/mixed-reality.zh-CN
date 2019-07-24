---
title: Unity 中的混合现实本机对象
description: 获取对 Unity 中的基础全息本机对象的访问权限。
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: unity, mixed reality, native, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942093"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Unity 中的混合现实本机对象

[获取 HolographicSpace](getting-a-holographicspace.md)是每个混合现实应用在开始接收相机数据和渲染帧之前所做的工作。 在 Unity 中, 引擎负责处理这些步骤, 并在内部处理全息对象和更新作为其呈现循环的一部分。

但是, 在高级方案中, 可能需要访问基础本机对象, 例如<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>和 current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>。 <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a>提供对这些本机对象的访问权限。

## <a name="xrdevice"></a>XRDevice 

**命名空间：** *UnityEngine.XR*<br>
**类型：** *XRDevice*

*XRDevice*类型允许使用<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法获取对基础本机对象的访问权限。 不同平台之间的 GetNativePtr 返回内容有所不同。 在通用 Windows 平台上, 当面向 Windows Mixed Reality XR SDK 时, XRDevice 将返回指针 (IntPtr) 到以下结构: 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
可以使用 Marshal.ptrtostructure 方法将其转换为 HolographicFrameNativeData:
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** 是 IntPtr 的长度等于 MaxNumberOfCameras 与作为 UnmanagedType.ByValArray 封送数组* 


### <a name="using-holographicframenativedata"></a>使用 HolographicFrameNativeData

> [!NOTE]
> 更改通过 HolographicFrameNativeData 接收的本机对象的状态可能会导致不可预知的行为和呈现项目, 特别是当 Unity 也导致相同状态时。  例如, 您不应调用 HolographicFrame. UpdateCurrentPrediction, 否则 Unity 呈现与该框架的姿势预测将与 Windows 所需的姿势不同步, 这将减少全息图的[稳定性](hologram-stability.md)。

如果在进行呈现或调试时需要访问本机接口, 则可以使用 HolographicFrameNativeData 中C#的数据。 

下面是如何使用 HolographicFrameNativeData 获取当前帧预测的 photon 时间的示例。 
```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a>请参阅
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [在 DirectX 中渲染](rendering-in-directx.md)
