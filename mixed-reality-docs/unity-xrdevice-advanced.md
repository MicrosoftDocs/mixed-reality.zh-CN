---
title: 在 Unity 中的混合的现实本机对象
description: 在 Unity 中有权访问全息版的基础本机对象。
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: unity 中，混合现实、 本机、 xrdevice、 spatialcoordinatesystem、 holographicframe、 holographiccamera、 ispatialcoordinatesystem、 iholographicframe、 iholographiccamera、 getnativeptr
ms.openlocfilehash: 76073f5b2adfdf27cfbb153f95bb3a533d02e196
ms.sourcegitcommit: d565a69a9320e736304372b3f010af1a4d286a62
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2019
ms.locfileid: "65942093"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="a96e4-104">在 Unity 中的混合的现实本机对象</span><span class="sxs-lookup"><span data-stu-id="a96e4-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="a96e4-105">[获取 HolographicSpace](getting-a-holographicspace.md)是每个混合现实应用执行前接收相机数据和呈现的帧。</span><span class="sxs-lookup"><span data-stu-id="a96e4-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="a96e4-106">在 Unity 中，该引擎负责的这些步骤为你处理 Holographic 对象并更新在内部作为其呈现循环的一部分。</span><span class="sxs-lookup"><span data-stu-id="a96e4-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="a96e4-107">但是，在高级方案中您可能需要有权访问基础本机对象，如<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>和当前<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>。</span><span class="sxs-lookup"><span data-stu-id="a96e4-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="a96e4-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a>是提供对这些本机对象的访问。</span><span class="sxs-lookup"><span data-stu-id="a96e4-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="a96e4-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="a96e4-109">XRDevice</span></span> 

<span data-ttu-id="a96e4-110">\**命名空间：\*\*\*UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="a96e4-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="a96e4-111">\**类型：\*\*\*XRDevice*</span><span class="sxs-lookup"><span data-stu-id="a96e4-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="a96e4-112">*XRDevice*类型，您可以获取对使用的基础本机对象的访问权限<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法。</span><span class="sxs-lookup"><span data-stu-id="a96e4-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="a96e4-113">GetNativePtr 返回之间不同的平台而异。</span><span class="sxs-lookup"><span data-stu-id="a96e4-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="a96e4-114">在通用 Windows 平台上，面向 Windows 混合现实 XR SDK 时，XRDevice.GetNativePtr 返回指向以下结构的指针 (IntPtr):</span><span class="sxs-lookup"><span data-stu-id="a96e4-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="a96e4-115">可以将其转换为 HolographicFrameNativeData 使用 Marshal.PtrToStructure 方法：</span><span class="sxs-lookup"><span data-stu-id="a96e4-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="a96e4-116">\***IHolographicCameraPtr**是 IntPtr 的长度等于 MaxNumberOfCameras 与作为 UnmanagedType.ByValArray 封送数组\*</span><span class="sxs-lookup"><span data-stu-id="a96e4-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="a96e4-117">使用 HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="a96e4-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="a96e4-118">更改本机对象通过 HolographicFrameNativeData 接收的状态可能会导致不可预知的行为和呈现项目，尤其是当 Unity 还原因有关的该相同的状态信息。</span><span class="sxs-lookup"><span data-stu-id="a96e4-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="a96e4-119">例如，不应调用 HolographicFrame.UpdateCurrentPrediction，否则 Unity 呈现该帧姿势预测将与姿势要求 Windows，这将减少在同步[全息图稳定性](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="a96e4-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="a96e4-120">需要用于呈现或调试目的，在本机插件访问本机接口时，可以使用来自 HolographicFrameNativeData 数据或C#代码。</span><span class="sxs-lookup"><span data-stu-id="a96e4-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="a96e4-121">下面是举例说明如何使用 HolographicFrameNativeData 获取 photon 时间的当前帧的预测。</span><span class="sxs-lookup"><span data-stu-id="a96e4-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="a96e4-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="a96e4-122">See Also</span></span>
* <span data-ttu-id="a96e4-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="a96e4-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="a96e4-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="a96e4-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="a96e4-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="a96e4-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="a96e4-126">在 DirectX 中渲染</span><span class="sxs-lookup"><span data-stu-id="a96e4-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
