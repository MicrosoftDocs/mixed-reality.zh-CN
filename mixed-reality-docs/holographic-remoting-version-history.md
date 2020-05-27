---
title: 全息远程处理版本历史记录
description: HoloLens 2 上的全息远程处理的版本历史记录。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: b128f91947fa8700502f7541cba23c726238a067
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866847"
---
# <a name="holographic-remoting-version-history"></a>全息远程处理版本历史记录

> [!IMPORTANT]
> 本指南特定于 HoloLens 2 上的全息远程处理。

## <a name="version-213-may-25-2020"></a>版本2.1.3 （5月25日，2020）<a name="v2.1.3"></a>
* 已更改[HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362)事件的行为。 在以前的版本中，**不**能保证添加的[HolographicCamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera?view=winrt-18362)在通过[HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createnextframe?view=winrt-18362#Windows_Graphics_Holographic_HolographicSpace_CreateNextFrame)创建下一帧时还具有有效的[HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) 。 从版本 2.1.3 [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362)中开始，将与来自全息远程处理程序的姿势数据同步，用户可能希望在添加照相机时，还会在下一帧上为该相机提供有效的[HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) 。
* 已将**禁用**添加到 DepthBufferStreamResolution，可用于通过 RemoteContext 禁用深度缓冲区流式处理。 请注意，如果使用的[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer?view=winrt-18362#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)将失败，并*E_ILLEGAL_METHOD_CALL*。
* 全息远程处理播放机的启动屏幕已重新设计，现在不会阻止用户视图。
* 稳定性和 buf 修复。

## <a name="version-212-april-5-2020"></a>版本2.1.2 （2020年4月5日）<a name="v2.1.2"></a>
* 修复了最新的全息远程处理播放器与使用小于2.1.0 的版本的远程应用之间的音频向后兼容性问题。
* 固定空间锚定问题，意外关闭了全息远程处理播放器。 此问题还会影响自定义播放机。

## <a name="version-211-march-20-2020"></a>版本2.1.1 （2020年3月20日）<a name="v2.1.1"></a>
* 修复了使用 AMD Gpu 时远程应用的视频编码问题。
* 全息远程处理播放器性能改进。

## <a name="version-210-march-11-2020"></a>版本2.1.0 （2020年3月11日）<a name="v2.1.0"></a>
* 已将网络传输切换为使用[RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP。 安全连接现在使用[SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 。 请注意，[全息远程处理播放器](holographic-remoting-player.md)仍与所有以前版本的全息远程处理版本兼容。 若要从新的网络传输中获益，全息远程处理播放器和有问题的远程应用必须使用版本2.1.0。
* 添加了对[HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)的支持。 

## <a name="version-2020-february-2-2020"></a>版本2.0.20 （2020年2月2日）<a name="v2.0.20"></a>
* 修复了导致崩溃的各种 bug。

## <a name="version-2018-december-17-2019"></a>版本2.0.18 （2019年12月17日）<a name="v2.0.18"></a>
* 添加了对[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)的支持
* 修复了导致崩溃的各种 bug。
* 修复了一个 bug，HolographicCamera 需要 HolographicSpace CameraAdded 回调才能接受，并将其显示为 HolographicFrame 中的已添加照相机。

## <a name="version-2016-november-11-2019"></a>版本2.0.16 （2019年11月11日）<a name="2.0.16"></a>
* 修复了 QR 代码跟踪中的死锁。
* 修复了在主线程中阻止等待的 unhandeled 异常。

## <a name="version-2014-october-26-2019"></a>版本2.0.14 （2019年10月26日）<a name="v2.0.14"></a>
* 支持新的 PerceptionDevice Api （Windows 10 11 月2019更新）。
* 修复了阻止 SpatialGestureRecognizer 触发暂停手势事件的问题。
* 修复了使用 SpatialSurfaceObserver 时的线程处理问题。

## <a name="version-2012-october-18-2019"></a>版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a>
* 修复了使用 NavigationRail （X/Y/Z）时 SpatialGestureRecognizer 中的崩溃。

## <a name="version-2010-october-10-2019"></a>版本 v2.0.10 （2019年10月10日）<a name="v2.0.10"></a>
* 修复了使用 VR 控制器的触发器按钮时出现故障。 全息远程处理并不完全支持控制器，如果与 HoloLens 2 配对，则仅触发器按钮和 Windows 按钮正常工作。

## <a name="version-209-september-19-2019"></a>版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a>
* 添加了对[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支持
* 添加了新接口 ```IPlayerContext2``` （由实现 ```PlayerContext``` ），提供以下成员：
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)属性。
* ```Failed_RemoteFrameTooOld```向添加值```BlitResult```
* 稳定性和可靠性改进

## <a name="version-208-august-20-2019"></a>版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a>

* 修复了使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)作为参数调用[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)时的崩溃。
* 稳定性和可靠性改进

## <a name="version-207-july-26-2019"></a>版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a>

* 适用于 HoloLens 2 的全息远程处理的第一个公共版本。

## <a name="see-also"></a>另请参阅
* [编写自定义全息远程处理播放器应用程序](holographic-remoting-create-player.md)
* [编写全息远程处理主机应用](holographic-remoting-create-host.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)
