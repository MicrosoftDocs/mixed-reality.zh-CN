---
title: 面向开发人员混合现实捕获
description: 面向开发人员捕获混合现实的最佳做法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、 照片、 视频、 捕获、 照相机
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694365"
---
# <a name="mixed-reality-capture-for-developers"></a>面向开发人员混合现实捕获

> [注意 ！]请参阅[PV 照相机从呈现](#render-from-the-pv-camera-opt-in)下面有关 HoloLens 2 新 MRC 功能的指导。

因为用户可能需要花[混合现实捕获](mixed-reality-capture.md)(MRC) 照片或视频在任何时间，没有开发应用程序时应牢记的一些事项。 这包括 MRC 视觉质量和正在响应系统更改，而将其捕获 MRCs 的最佳实践。

开发人员可以也可无缝集成混合的现实捕获和插入到其应用程序。

MRC HoloLens （第一代） 上的支持视频和照片最多为 720p，虽然 MRC HoloLens 2 上的支持多达 1080p 和照片的视频最多有 4k 分辨率。

## <a name="the-importance-of-quality-mrc"></a>质量 MRC 的重要性

混合的现实捕获照片和视频可能是首次用户将拥有的应用程序。 是否为 Microsoft Store 页上或从其他用户在社交网络上共享 MRCs 的混合的现实屏幕截图。 使用 MRC 演示您的应用程序，对用户进行培训，鼓励用户共享其混合的世界交互，以及用户调查和解决问题。

## <a name="how-mrc-impacts-your-app"></a>MRC 如何影响您的应用程序

### <a name="enabling-mrc-in-your-app"></a>在应用中启用 MRC

默认情况下，不需要执行任何操作即可使用户能够执行混合的现实捕获应用程序。

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>启用应用程序中的改进了对齐方式 MRC

默认情况下，混合的现实捕获组合和照片/视频 (PV) 摄像机正确的人眼 holographic 输出。 使用由当前正在运行沉浸式应用程序设置的焦点位置组合这些两个源。

这意味着全息焦点平面外的不能也 （由于 PV 照相机和右侧显示之间的物理距离） 对齐。

#### <a name="set-the-focus-point"></a>设置焦点

（在 HoloLens) 的沉浸式应用程序应设置[关注点](focus-point-in-unity.md)，他们想要为其稳定平面。 这可确保这两个耳机和混合的现实捕获中最佳的对齐方式。

如果未设置焦点，稳定平面将默认为两个指标。

#### <a name="render-from-the-pv-camera-opt-in"></a>从 （选择中） 的 PV 照相机呈现

HoloLens 2 添加了沉浸式应用程序的功能**PV 照相机从呈现**混合的现实捕获正在运行时。 若要确保应用正确支持其他呈现器，则应用必须参加与此功能。

呈现从 PV 照相机产品/服务通过默认 MRC 体验了以下改进：
* 全息图对齐到你的物理环境和手 （适用于近交互） 应是准确的根本距离，而不是让在而不是关注点的距离的偏移量，正如您可能会看到默认 MRC 中。
* 不会损害耳机右侧的眼睛，因为不会使用它来呈现为 MRC 输出全息。

有三个步骤以启用从 PV 照相机呈现：
1. 启用 PhotoVideoCamera HolographicViewConfiguration
2. 处理其他 HolographicCamera 呈现器
3. 验证你的着色器和代码正确呈现此额外 HolographicCamera 从

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>启用 PhotoVideoCamera HolographicViewConfiguration

为选择加入的应用程序只是让 PhotoVideoCamera [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>处理其他 HolographicCamera 呈现 DirectX 中

当应用程序处于启用状态来呈现来自 PV 摄像机和混合的现实捕获开始：
1. HolographicSpace 的 CameraAdded 事件将激发。 如果应用程序不能在此时处理照相机可以推迟此事件。
2. 该事件已完成 （并有任何未完成延迟） 后 HolographicCamera 会在下一步 HolographicFrame AddedCameras 列表中。

混合的现实捕获将停止时 （或混合的现实捕获正在运行时，应用程序禁用视图配置）： HolographicCamera 会在下一步 HolographicFrame RemovedCameras 列表中，将 HolographicSpace CameraRemoved 事件激发。

一个[ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)属性已添加到 HolographicCamera 以帮助识别照相机所属的配置。

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>处理其他 HolographicCamera 呈现在 Unity 中

>[!NOTE]
> Unity 支持从 PV 照相机呈现在开发和不能使用，尚未。 当从 PV 照相机呈现支持 Unity 的版本可用时，将更新本文档。

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>验证着色器和代码支持其他照相机

运行混合的现实捕获并检查有不寻常的对齐方式、 缺少的内容或性能问题。 更新着色器和相应的代码。

如果有无法支持其他摄像头的呈现某些场景，可以在这些期间禁用 PhotoVideoCamera HolographicViewConfiguration。

### <a name="disabling-mrc-in-your-app"></a>应用程序中禁用 MRC

#### <a name="2d-app"></a>2D 应用

2D 应用程序可以选择让混合的现实捕获正在运行的被遮挡住其可视内容：
* 在与[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)标志
* 创建与应用程序的交换链[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)标志
* Windows 10 的可能 2019年更新设置 ApplicationView 的[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>沉浸式应用程序

沉浸式应用程序可以选择从通过混合的现实捕获中排除其可视内容：
* 设置的 HolographicCameraRenderingParameter [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)以禁用及其关联的帧的混合的现实捕获
* 设置的 HolographicCamera [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)以禁用其关联的 holographic 照相机的混合的现实捕获

#### <a name="password-keyboard"></a>密码键盘

Windows 10 的可能 2019年更新、 密码或 pin 键盘可见时自动从混合的现实捕获排除视觉内容。

### <a name="knowing-when-mrc-is-active"></a>了解当 MRC 处于活动状态

[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)类可以由应用程序了解混合现实捕获系统 （对于音频或视频） 的运行时。

>[!NOTE]
>AppCapture 的[GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可以返回 null，如果混合现实捕获不是设备上可用。 还有一点需要取消注册您的应用程序挂起时的 CapturingChanged 事件，否则 MRC 可能会进入阻止状态。

### <a name="best-practices-hololens-specific"></a>最佳做法 （特定于 HoloLens 的）

MRC 预期工作，而其他工作从开发人员，但有几个事项需要注意的以提供您的应用程序的最佳混合的现实捕获体验。

**MRC 使用全息图的 alpha 通道来与混合[照相机](locatable-camera.md)图像**

最重要的步骤是确保您的应用程序清除为透明黑色，而不是为不透明的黑色清除。 在 Unity 中，这是 MixedRealityToolkit 默认情况下，但如果你正在开发非 Unity 中，您可能需要进行更改的一行。

下面是一些你可能会在 MRC 中，如果您的应用程序不会清除为透明黑色的项目：

**示例故障**:黑色边缘周围的内容 （未能清除为透明黑色）

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**示例故障**:整个背景场景的全息图显示为黑色。 在黑色背景中设置背景 alpha 值为 1 的结果

![在黑色背景中设置背景 alpha 值为 1 的结果](images/clearopaqueblack-300px.png)

**预期结果**:全息显示正确混合与现实世界 （如果清除为透明黑色预期结果）

![如果清除为透明黑色的预期的结果](images/cleartransparentblack-300px.png)

**解决方案**：
* 更改任何内容都如何显示为不透明的黑色具有 alpha 值为 0。
* 请确保该应用程序正在清除为透明黑色。
* 若要清除此选项可自动清除 MixedRealityToolkit，但如果它是一个非 Unity 应用，应修改与 ID3D11DeiceContext::ClearRenderTargetView() 一起使用的颜色与 unity 默认值。 你想要确保清除为透明黑色 (0,0,0,0) 而不是不透明黑 (0,0,0,1)。

如果想要但通常不需要现在可以优化你的资产的 alpha 值。 大多数情况下，MRCs 看现成的很好。 MRC 假定预乘的 alpha。 Alpha 值只会影响 MRC 捕获。

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>在 HoloLens 上启用 MRC 时会发生什么

以下内容适用于 HoloLens （第一代） 和 HoloLens 2，除非另有说明：

* 系统将限制为 30 Hz 呈现应用程序。 这将创建一些空间用于 MRC 运行，因此应用程序不需要保留的常量预算保留并也匹配 30 fps MRC 视频记录帧速率
* 全息图内容眼里出正确的设备时可能会显示以"礼花绽放"流式处理记录/MRC： 文本可能会变得更难以阅读和全息图边缘可能会出现更锯齿状 (在选择加入第三照相机上呈现**HoloLens 2**可避免此入侵）
* MRC 照片和视频将遵守该应用程序[关注点](focus-point-in-unity.md)如果应用程序启用了它，这将有助于确保全息准确地定位。 对于视频，因此全息看起来似乎如果焦点深度发生了重大变化缓慢偏差到位平滑处理的焦点位置。 位于不同深度的焦点位置从全息可能在现实生活 （请参阅下面的示例，在 2 米设置焦点，但全息图定位在 1 米） 中显示偏移量。

![在 2 米全息会完全对公众已注册。 在关闭或远距离全息可能会有轻微偏移。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>将从您的应用程序中的 MRC 功能集成

混合的现实应用 MRC 照片或视频捕获从在应用中，可以启动和捕获的内容将无需存储提供给您的应用程序到设备的"本机照片。" 可以创建自定义 MRC 记录器或充分利用内置相机捕捉 UI。 

### <a name="mrc-with-built-in-camera-ui"></a>使用内置相机 UI MRC

开发人员可以使用 *[摄像头捕获 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 若要获取用户捕获混合的现实照片或视频只需几行代码。

此 API 启动内置 MRC 摄像头 UI，从该用户可以拍摄照片或视频，并返回结果捕获到您的应用程序。  如果你想要创建您自己摄像头 UI，或需要较低级别捕获对流的访问权限，则可以创建自定义的混合现实捕获记录器。

### <a name="creating-a-custom-mrc-recorder"></a>创建自定义 MRC 记录器

虽然用户始终可以触发照片或视频使用系统 MRC 捕获服务，应用程序可能想要生成自定义的相机应用程序，但就像 MRC 照相机流中包括全息。 这样，应用程序启动捕获代表用户、 生成自定义录制用户界面，或自定义 MRC 设置命名的几个示例。

**HoloStudio 添加自定义 MRC 照相机使用 MRC 效果**

![HoloStudio 添加自定义 MRC 照相机使用 MRC 效果](images/cameraiconholostudio-300px.jpg)

Unity 应用程序应会看到[Locatable_camera_in_Unity](locatable-camera-in-unity.md)要启用全息的属性。

其他应用程序可以执行此操作通过使用[Windows 媒体捕获 Api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)控制照相机并添加要在静止图像和视频中包含虚拟全息和应用程序音频 MRC 视频和音频效果。

应用程序具有两个选项来添加效果：
* 较旧的 API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* 新的 Microsoft 建议 API （返回一个对象，使其可以处理动态属性）：[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync)需要应用程序创建其自己实现[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)并[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)。 请参阅示例用法 MRC 效果示例。

>[!NOTE]
> Visual Studio 中，将不会识别 Windows.Media.MixedRealityCapture 命名空间，但字符串仍有效。

MRC 视频效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  属性名  |  type  |  Default Value  |  描述 | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  描述此效果用于捕获的流。 音频不可用。 | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  若要启用或禁用全息视频捕获中的标记。 | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  一个标志，用于启用或禁用在屏幕上的录制指示器全息图捕获过程。 | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  一个标志，用于启用或禁用由 HoloLens 跟踪程序提供支持的视频防抖动。 | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  设置历史帧数用于视频防抖动。 0 为 0 的延迟和几乎"免费"从能力和性能的角度来看。 15 （但代价是 15 帧的滞后时间和内存） 的最高质量的建议。 | 
|  GlobalOpacityCoefficient  |  浮点数  |  0.9 (HoloLens) 1.0 （沉浸式头戴式）  |  全局不透明度系数的全息图中设置范围从 0.0 （完全透明） 到 1.0 （完全不透明）。 | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  一个标志，用于启用或禁用 2d 的 UWP 应用显示受保护的内容是否返回一个空框架。 此标志为 false 和 2d UWP 应用时显示受保护的内容，2d 的 UWP 应用将替换为受保护内容纹理，这两个耳机和混合的现实捕获中。 |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  若要启用或禁用显示 holographic 照相机的隐藏的区域网格和相邻内容的标记。 |
| OutputSize | Size | 0, 0 | 有关视频防抖动裁剪后设置相应的输出大小。 如果指定 0 或无效的输出大小，则，选择默认裁剪大小。 |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | 枚举用于指示应捕获哪 holographic 照相机查看配置。 设置应用程序将不会要求从照片/视频照相机呈现的 0 （显示） 表示 |

MRC 音频效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>属性名</th>
<th>type</th>
<th>Default Value</th>
<th>描述</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0 :仅限 mic 音频</li>
<li>1 :仅系统音频</li>
<li>2 :Mic 和系统音频</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>同时 MRC 限制

有多个应用在同一时间访问 MRC 方面的某些限制。

#### <a name="photovideo-camera-access"></a>照片/视频照相机访问

照片/视频摄像机被限制为可以在同一时间访问它的进程数。 而在录制过程将失败视频或任何其他进程拍照获取照片/视频摄像机。 （适用于混合现实捕获和标准照片/视频捕获）

HoloLens 2 应用程序可以使用 MediaCaptureInitializationSettings 的[SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)属性以指示他们想要运行 SharedReadOnly，如果它们不需要照片/视频摄像机的独有控制。 解析和捕获的帧速率为这样做意味着将限制为其他应用已配置的内容提供照相机。

##### <a name="built-in-mrc-photovideo-camera-access"></a>内置 MRC 照片/视频照相机访问

MRC 功能内置于 Windows 10 （通过 Cortana，开始菜单，硬件快捷方式，Miracast、 Windows Device Portal）：
* 默认情况下将使用 ExclusiveControl 运行

但是，支持已添加到每个子系统在共享模式下操作：
* 如果应用程序请求 ExclusiveControl 访问照片/视频摄像机，内置 MRC 将自动停止使用照片/视频摄像机，因此应用程序的请求将成功
* 如果内置 MRC 已启动时应用具有 ExclusiveControl，内置 MRC 将在 SharedReadOnly 模式下运行

此共享的模式功能具有某些限制：
* 通过 Cortana、 硬件快捷方式或开始菜单的照片：需要 Windows 10 2018 年 4 月更新 （或更高版本）
* 通过 Cortana、 硬件快捷方式或开始菜单的视频：需要 Windows 10 2018 年 4 月更新 （或更高版本）
* 通过支持 Miracast 的流式处理 MRC:需要 Windows 10 2018 年 10 月更新 （或更高版本）
* 通过 Windows Device Portal 或通过 HoloLens 辅助应用程序，流式处理 MRC:需要 HoloLens 2

>[!NOTE]
> 另一个应用使用照片/视频照相机时，可能通过其正常值降低分辨率和帧速率的内置 MRC 相机 UI。

#### <a name="mrc-access"></a>MRC 访问

使用 Windows 10 2018 年 4 月更新，不再有多个应用程序访问 （但是，对照片/视频摄像机的访问权限仍有一些局限性） MRC 流周围的限制。

先前的 windows 10 2018 年 4 月更新，应用程序的自定义 MRC 记录器的互斥与系统 MRC （拍摄照片、 捕获视频，或从 Windows Device Portal 流式处理）。

## <a name="see-also"></a>请参阅
* [混合现实捕获](mixed-reality-capture.md)
* [旁观视图](spectator-view.md)
