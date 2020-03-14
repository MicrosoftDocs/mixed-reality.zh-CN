---
title: 全息远程处理版本历史记录
description: HoloLens 2 上的全息远程处理的版本历史记录。
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens、远程处理、全息远程处理
ms.openlocfilehash: 62f54dbcf5327cdd5f13622704684a2cb0606d7d
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375654"
---
# <a name="holographic-remoting-version-history"></a>全息远程处理版本历史记录

> [!IMPORTANT]
> 本指南特定于 HoloLens 2 上的全息远程处理。

## 版本2.1.0 （2020年3月11日）<a name="v2.1.0"></a>
* 已将网络传输切换为使用[RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP。 安全连接现在使用[SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 。 请注意，[全息远程处理播放器](holographic-remoting-player.md)仍与所有以前版本的全息远程处理版本兼容。 若要从新的网络传输中获益，全息远程处理播放器和有问题的远程应用必须使用版本2.1.0。
* 添加了对[HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)的支持。 

## 版本2.0.20 （2020年2月2日）<a name="v2.0.20"></a>
* 修复了导致崩溃的各种 bug。

## 版本2.0.18 （2019年12月17日）<a name="v2.0.18"></a>
* 添加了对[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)的支持
* 修复了导致崩溃的各种 bug。
* 修复了一个 bug，HolographicCamera 需要 HolographicSpace CameraAdded 回调才能接受，并将其显示为 HoloraphicFrame 中的已添加照相机。

## 版本2.0.16 （2019年11月11日）<a name="2.0.16"></a>
* 修复了 QR 代码跟踪中的死锁。
* 修复了在主线程中阻止等待的 unhandeled 异常。

## 版本2.0.14 （2019年10月26日）<a name="v2.0.14"></a>
* 支持新的 PerceptionDevice Api （Windows 10 11 月2019更新）。
* 修复了阻止 SpatialGestureRecognizer 触发暂停手势事件的问题。
* 修复了使用 SpatialSurfaceObserver 时的线程处理问题。

## 版本2.0.12 （2019年10月18日）<a name="v2.0.12"></a>
* 修复了使用 NavigationRail （X/Y/Z）时 SpatialGestureRecognizer 中的崩溃。

## 版本 v2.0.10 （2019年10月10日）<a name="v2.0.10"></a>
* 修复了使用 VR 控制器的触发器按钮时出现故障。 全息远程处理并不完全支持控制器，如果与 HoloLens 2 配对，则仅触发器按钮和 Windows 按钮正常工作。

## 版本2.0.9 （2019年9月19日）<a name="v2.0.9"></a>
* 添加了对[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)的支持
* 添加了新的接口 ```IPlayerContext2``` （由 ```PlayerContext```实现），提供以下成员：
  - [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)属性。
* 已将 ```Failed_RemoteFrameTooOld``` 值添加到 ```BlitResult```
* 稳定性和可靠性改进

## 版本2.0.8 （2019年8月20日）<a name="v2.0.8"></a>

* 修复了使用[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2)作为参数调用[HolographicCameraRenderingParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer)时的崩溃。
* 稳定性和可靠性改进

## 版本2.0.7 （2019年7月26日）<a name="v2.0.7"></a>

* 适用于 HoloLens 2 的全息远程处理的第一个公共版本。

## <a name="see-also"></a>另请参阅
* [编写自定义全息远程处理播放器应用程序](holographic-remoting-create-player.md)
* [编写全息远程处理主机应用](holographic-remoting-create-host.md)
* [全息远程处理故障排除和限制](holographic-remoting-troubleshooting.md)
* [全息远程处理软件许可条款](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 隐私声明](https://go.microsoft.com/fwlink/?LinkId=521839)
