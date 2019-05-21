---
title: 面向开发人员混合现实捕获
description: 面向开发人员捕获混合现实的最佳做法。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、 照片、 视频、 捕获、 照相机
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591594"
---
# <a name="mixed-reality-capture-for-developers"></a>面向开发人员混合现实捕获

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。 

请参阅[应用程序中启用 MRC](#enabling-mrc-in-your-app)下面有关 HoloLens 2 新 MRC 功能的指导。

因为用户可能需要花[混合现实捕获](mixed-reality-capture.md)(MRC) 照片或视频在任何时间，没有开发应用程序时应牢记的一些事项。 这包括 MRC 视觉质量和正在响应系统更改，而将其捕获 MRCs 的最佳实践。

开发人员可以也可无缝集成混合的现实捕获和插入到其应用程序。

MRC HoloLens （第一代） 上的支持视频和照片最多为 720p，虽然 MRC HoloLens 2 上的支持多达 1080p 和照片的视频最多有 4k 分辨率。

## <a name="the-importance-of-quality-mrc"></a>质量 MRC 的重要性

混合的现实捕获照片和视频可能是首次用户将拥有的应用程序。 是否为 Microsoft Store 页上或从其他用户在社交网络上共享 MRCs 的混合的现实屏幕截图。 使用 MRC 演示您的应用程序，对用户进行培训，鼓励用户共享其混合的世界交互，以及用户调查和解决问题。

## <a name="how-mrc-impacts-your-app"></a>MRC 如何影响您的应用程序

### <a name="enabling-mrc-in-your-app"></a>在应用中启用 MRC

默认情况下，不需要执行任何操作即可使用户能够执行混合的现实捕获应用程序。 但是，由于 HoloLens 2 的设计会增加照片/视频 (PV) 摄像机和显示之间的距离，我们将引入了新选项，生成的 PV 照相机与对齐第三照相机渲染**HoloLens 2**。 

在选择加入第三照相机上呈现 HoloLens 2 产品/服务的以下改进对默认 MRC 体验：
* 全息图对齐方式为你的物理环境和手 （适用于近交互） 应是准确根本距离，而不是在距离而不让某一偏移量[关注点](focus-point-in-unity.md)正如您可能会看到默认 MRC 中。
* 不会损害耳机右侧的眼睛，因为不会使用它来呈现为 MRC 输出全息。

### <a name="disabling-mrc-in-your-app"></a>应用程序中禁用 MRC

当使用 2D 应用[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx)或[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx)若要显示受保护的内容正确配置交换链，应用程序的可视内容将是混合的现实捕获正在运行时，会自动被遮盖。

### <a name="knowing-when-mrc-is-active"></a>了解当 MRC 处于活动状态

[AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx)类可以由应用程序了解混合现实捕获系统 （对于音频或视频） 的运行时。

>[!NOTE]
>AppCapture 的[GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API 可以返回 null，如果混合现实捕获不是设备上可用。 还有一点需要取消注册您的应用程序挂起时的 CapturingChanged 事件，否则 MRC 可能会进入阻止状态。

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

其他应用程序可以执行此操作通过使用[Windows 媒体捕获 Api](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx)控制照相机并添加要在静止图像和视频中包含虚拟全息和应用程序音频 MRC 视频和音频效果。

应用程序具有两个选项来添加效果：
* 较旧的 API:[Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)
* 新的 Microsoft 建议 API （返回一个对象，使其可以处理动态属性）：[Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx)需要应用程序创建其自己实现[IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx)并[IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx)。 请参阅示例用法 MRC 效果示例。

（请注意，Visual Studio 中，将无法识别这些命名空间，但字符串仍有效）

MRC 视频效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  属性名  |  在任务栏的搜索框中键入  |  默认值  |  描述 | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))  |  1 (VideoRecord)  |  描述此效果用于捕获的流。 音频不可用。 | 
|  HologramCompositionEnabled  |  布尔值  |  TRUE  |  若要启用或禁用全息视频捕获中的标记。 | 
|  RecordingIndicatorEnabled  |  布尔值  |  TRUE  |  一个标志，用于启用或禁用在屏幕上的录制指示器全息图捕获过程。 | 
|  VideoStabilizationEnabled  |  布尔值  |  FALSE  |  一个标志，用于启用或禁用由 HoloLens 跟踪程序提供支持的视频防抖动。 | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  设置历史帧数用于视频防抖动。 0 为 0 的延迟和几乎"免费"从能力和性能的角度来看。 15 （但代价是 15 帧的滞后时间和内存） 的最高质量的建议。 | 
|  GlobalOpacityCoefficient  |  浮点数  |  0.9 (HoloLens) 1.0 （沉浸式头戴式）  |  全局不透明度系数的全息图中设置范围从 0.0 （完全透明） 到 1.0 （完全不透明）。 | 
|  BlankOnProtectedContent  |  布尔值  |  FALSE  |  一个标志，用于启用或禁用 2d 的 UWP 应用显示受保护的内容是否返回一个空框架。 此标志为 false 和 2d UWP 应用时显示受保护的内容，2d 的 UWP 应用将替换为受保护内容纹理，这两个耳机和混合的现实捕获中。 |
|  ShowHiddenMesh  |  布尔值  |  FALSE  |  若要启用或禁用显示 holographic 照相机的隐藏的区域网格和相邻内容的标记。 |

MRC 音频效果 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>属性名</th>
<th>在任务栏的搜索框中键入</th>
<th>默认值</th>
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

使用 Windows 10 2018 年 4 月更新，此限制不适用于如果内置 MRC 摄像头 UI 用于后应用已开始使用照片/视频照相机拍摄照片或视频。 在此情况下，解析和内置 MRC 摄像头 UI 帧速率可能会降低其正常值中。

使用 Windows 10 2018 年 10 月更新，此限制不适用于 Miracast 通过流式处理 MRC。

#### <a name="mrc-access"></a>MRC 访问

使用 Windows 10 2018 年 4 月更新，不再有多个应用程序访问 （但是，对照片/视频摄像机的访问权限仍有一些局限性） MRC 流周围的限制。

先前的 windows 10 2018 年 4 月更新，应用程序的自定义 MRC 记录器的互斥与系统 MRC （拍摄照片、 捕获视频，或从 Windows Device Portal 流式处理）。

## <a name="see-also"></a>请参阅
* [混合的现实捕获](mixed-reality-capture.md)
* [Spectator 视图](spectator-view.md)
