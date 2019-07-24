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
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="277d7-104">Unity 中的混合现实本机对象</span><span class="sxs-lookup"><span data-stu-id="277d7-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="277d7-105">[获取 HolographicSpace](getting-a-holographicspace.md)是每个混合现实应用在开始接收相机数据和渲染帧之前所做的工作。</span><span class="sxs-lookup"><span data-stu-id="277d7-105">[Getting a HolographicSpace](getting-a-holographicspace.md) is what every Mixed Reality app does before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="277d7-106">在 Unity 中, 引擎负责处理这些步骤, 并在内部处理全息对象和更新作为其呈现循环的一部分。</span><span class="sxs-lookup"><span data-stu-id="277d7-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and updates internally as part of its render loop.</span></span>

<span data-ttu-id="277d7-107">但是, 在高级方案中, 可能需要访问基础本机对象, 例如<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>和 current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>。</span><span class="sxs-lookup"><span data-stu-id="277d7-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="277d7-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a>提供对这些本机对象的访问权限。</span><span class="sxs-lookup"><span data-stu-id="277d7-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="277d7-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="277d7-109">XRDevice</span></span> 

<span data-ttu-id="277d7-110">**命名空间：** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="277d7-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="277d7-111">**类型：** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="277d7-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="277d7-112">*XRDevice*类型允许使用<a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a>方法获取对基础本机对象的访问权限。</span><span class="sxs-lookup"><span data-stu-id="277d7-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="277d7-113">不同平台之间的 GetNativePtr 返回内容有所不同。</span><span class="sxs-lookup"><span data-stu-id="277d7-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="277d7-114">在通用 Windows 平台上, 当面向 Windows Mixed Reality XR SDK 时, XRDevice 将返回指针 (IntPtr) 到以下结构:</span><span class="sxs-lookup"><span data-stu-id="277d7-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

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
<span data-ttu-id="277d7-115">可以使用 Marshal.ptrtostructure 方法将其转换为 HolographicFrameNativeData:</span><span class="sxs-lookup"><span data-stu-id="277d7-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="277d7-116">***IHolographicCameraPtr** 是 IntPtr 的长度等于 MaxNumberOfCameras 与作为 UnmanagedType.ByValArray 封送数组*</span><span class="sxs-lookup"><span data-stu-id="277d7-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 


### <a name="using-holographicframenativedata"></a><span data-ttu-id="277d7-117">使用 HolographicFrameNativeData</span><span class="sxs-lookup"><span data-stu-id="277d7-117">Using HolographicFrameNativeData</span></span>

> [!NOTE]
> <span data-ttu-id="277d7-118">更改通过 HolographicFrameNativeData 接收的本机对象的状态可能会导致不可预知的行为和呈现项目, 特别是当 Unity 也导致相同状态时。</span><span class="sxs-lookup"><span data-stu-id="277d7-118">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="277d7-119">例如, 您不应调用 HolographicFrame. UpdateCurrentPrediction, 否则 Unity 呈现与该框架的姿势预测将与 Windows 所需的姿势不同步, 这将减少全息图的[稳定性](hologram-stability.md)。</span><span class="sxs-lookup"><span data-stu-id="277d7-119">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](hologram-stability.md).</span></span>

<span data-ttu-id="277d7-120">如果在进行呈现或调试时需要访问本机接口, 则可以使用 HolographicFrameNativeData 中C#的数据。</span><span class="sxs-lookup"><span data-stu-id="277d7-120">You can use data from HolographicFrameNativeData when access to native interfaces is required for rendering or debugging purposes, in your native plugins or C# code.</span></span> 

<span data-ttu-id="277d7-121">下面是如何使用 HolographicFrameNativeData 获取当前帧预测的 photon 时间的示例。</span><span class="sxs-lookup"><span data-stu-id="277d7-121">Here is an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 
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

## <a name="see-also"></a><span data-ttu-id="277d7-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="277d7-122">See Also</span></span>
* <span data-ttu-id="277d7-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="277d7-123"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="277d7-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="277d7-124"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="277d7-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="277d7-125"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="277d7-126">在 DirectX 中渲染</span><span class="sxs-lookup"><span data-stu-id="277d7-126">Rendering in DirectX</span></span>](rendering-in-directx.md)
