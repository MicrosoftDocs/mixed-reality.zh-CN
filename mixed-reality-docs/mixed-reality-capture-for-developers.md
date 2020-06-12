---
title: 面向开发人员的混合现实捕获
description: 适用于开发人员的混合现实捕获的最佳实践。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、照片、视频、捕获、照相机
ms.openlocfilehash: 1116e9a0923129aa2b18d838917eebf12adae694
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720413"
---
# <a name="mixed-reality-capture-for-developers"></a>面向开发人员的混合现实捕获

> [!NOTE]
> 有关适用于 HoloLens 2 的新 MRC 功能的指南，请参阅下面[的 PV 相机中的 Render](#render-from-the-pv-camera-opt-in) 。

由于用户随时都可以使用[混合现实捕获](mixed-reality-capture.md)（MRC）照片或视频，因此，在开发应用程序时，需要记住几个事项。 这包括在捕获 MRCs 时，可用于 MRC 视觉质量并响应系统更改的最佳实践。

开发人员还可以将混合现实捕获和插入无缝集成到其应用中。

HoloLens 上的 MRC （第一代）支持最多720p 的视频和照片，而在 HoloLens 2 上的 MRC 支持最大为1080p 和最大分辨率为4K 的视频。

## <a name="the-importance-of-quality-mrc"></a>质量 MRC 的重要性

混合现实捕获的照片和视频可能是用户对你的应用程序的第一次曝光。 是否在 Microsoft Store 页面上或从其他用户共享社交网络上的 MRCs 混合现实屏幕截图。 您可以使用 MRC 来演示您的应用程序、培训用户、鼓励用户共享其混合世界交互，以及进行用户研究和解决问题。

## <a name="how-mrc-impacts-your-app"></a>MRC 如何影响你的应用

### <a name="enabling-mrc-in-your-app"></a>在应用程序中启用 MRC

默认情况下，应用程序无需执行任何操作即可使用户接受混合的现实捕获。

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>在应用中为 MRC 启用改进的对齐方式

默认情况下，混合现实捕获结合了正确的眼睛和照片/视频（PV）相机。 这两个源使用当前运行的沉浸式应用设置的焦点组合在一起。

这意味着，在焦点平面外的全息影像也不会对齐（因为 PV 相机和右显示之间的物理距离）。

#### <a name="set-the-focus-point"></a>设置焦点

沉浸式应用（在 HoloLens 上）应将[焦点](focus-point-in-unity.md)设置为要将其稳定平面置于何处。 这确保了耳机和混合现实捕获中的最佳对齐。

如果未设置焦点，则 "稳定" 平面将默认为两米。

#### <a name="render-from-the-pv-camera-opt-in"></a>从 PV 相机呈现（选择加入）

HoloLens 2 添加了一种功能，使沉浸式应用能够在混合现实捕获运行时**从 PV 摄像机进行呈现**。 若要确保应用正确支持其他呈现，应用必须选择启用此功能。

PV 相机中的呈现功能与默认的 MRC 体验相比具有以下改进：
* 与您的物理环境和手之间（几乎交互）的全息图对齐方式应始终精确，而不是相对于在默认 MRC 中可能看到的距离以外的距离。
* 头戴式耳机不会受到影响，因为它不会用于呈现 MRC 输出的全息影像。

可以通过以下三个步骤，通过 PV 相机实现呈现：
1. 启用 PhotoVideoCamera HolographicViewConfiguration
2. 处理附加的 HolographicCamera 呈现
3. 通过此附加 HolographicCamera 正确验证着色器和代码呈现

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a>在 DirectX 中启用 PhotoVideoCamera HolographicViewConfiguration

若要选择从 PV 相机进行呈现，应用只需启用 PhotoVideoCamera 的[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)：
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>在 DirectX 中处理附加的 HolographicCamera 呈现

当应用程序有选择地从 PV 相机进行呈现且混合现实捕获开始时：
1. HolographicSpace 的 CameraAdded 事件将激发。 如果此时应用无法处理照相机，此事件可能会延迟。
2. 事件完成后（没有未完成的延迟），HolographicCamera 将在下一个 HolographicFrame 的 AddedCameras 列表中显示。

当混合现实捕获停止时（或者，如果应用在混合现实捕获正在运行时禁用视图配置）： HolographicCamera 将显示在下一个 HolographicFrame 的 RemovedCameras 列表中，并激发 HolographicSpace 的 CameraRemoved 事件。

已将[ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)属性添加到 HolographicCamera，以帮助标识相机所属的配置。

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a>在 Unity 中启用 PhotoVideoCamera HolographicViewConfiguration

> [!NOTE]
> 这需要**unity 2018.4.13 f1**、 **unity 2019.3.0 f1**或更高版本。

若要选择从 PV 相机进行呈现，请在使用[混合现实工具包](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)时，启用[Windows Mixed reality 相机设置](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html)提供程序并**从 PV 相机设置中检查渲染**。

如果使用的不是混合现实工具包，则可以使用组件[手动选择启用](#enable-the-photovideocamera-holographicviewconfiguration-in-directx)DirectX。

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>处理 Unity 中的其他 HolographicCamera 呈现

这是由 Unity 自动完成的。

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a>启用 Unreal 中的 PhotoVideoCamera HolographicViewConfiguration

> [!NOTE]
> 这需要**Unreal 引擎 4.25**或更高版本。

若要选择从 PV 摄像机进行呈现：

1. 调用**SetEnabledMixedRealityCamera**和**ResizeMixedRealityCamera**
    * 使用**Size X**和**size Y**值设置视频尺寸。

![第三人称摄像头](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a>在 Unreal 中处理附加的 HolographicCamera 呈现

这是由 Unreal 自动完成的。

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>验证着色器和代码支持其他相机

运行混合现实捕获，并检查是否存在异常对齐、缺少内容或性能问题。 根据需要更新着色器和代码。

如果某些场景无法支持向其他相机进行呈现，则可以在 PhotoVideoCamera 的 HolographicViewConfiguration 中禁用它。

### <a name="disabling-mrc-in-your-app"></a>在应用中禁用 MRC

#### <a name="2d-app"></a>2D 应用

当混合现实捕获正在运行时，2D 应用可以选择使其视觉内容遮盖：
* 与[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present)标志一起提供
* 用[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)标志创建应用的交换链
* 对于 Windows 10 2019 更新，设置 w 的[IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>沉浸式应用

沉浸式应用可通过以下方式选择将其视觉内容从混合现实捕获中排除：
* 设置 HolographicCameraRenderingParameter 的[IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled)以禁用其关联帧的混合现实捕获
* 将 HolographicCamera 的[IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled)设置为对其关联的全息相机禁用混合现实捕获

#### <a name="password-keyboard"></a>密码键盘

使用 Windows 10 的2019更新可能会在密码或 pin 键盘可见时，自动从混合现实捕获中排除可视内容。

### <a name="knowing-when-mrc-is-active"></a>了解 MRC 何时处于活动状态

应用程序可以使用[AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture)类来了解系统混合现实捕获的运行时间（对于音频或视频）。

>[!NOTE]
>如果混合现实捕获在设备上不可用，则 AppCapture 的[GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API 可以返回 null。 在应用暂停时取消注册 CapturingChanged 事件也很重要，否则可能会进入 "已阻止" 状态。

### <a name="best-practices-hololens-specific"></a>最佳做法（特定于 HoloLens）

对于开发人员而言，MRC 应该无需额外工作就能正常运行，但需要注意一些事项，以便为应用提供最佳混合现实体验。

**MRC 使用全息图的 alpha 通道与[相机](locatable-camera.md)图像混合**

最重要的步骤是确保您的应用程序清除为透明黑色，而不是清除为不透明的黑色。 在 Unity 中，这是默认情况下通过 MixedRealityToolkit 完成的，但是如果是在非 Unity 中进行开发，则可能需要更改一行。

如果你的应用未清除透明黑色，以下是你可能会在 MRC 中看到的一些项目：

**示例失败**：内容周围的黑色边缘（未能清除为透明黑色）

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

**示例失败**：全息图的整个背景场景显示为黑色。 将背景 alpha 值设置为1会导致黑色背景

![将背景 alpha 值设置为1会导致黑色背景](images/clearopaqueblack-300px.png)

**预期结果**：全息影像与真实世界正确地混合（如果清除为透明黑色，则为预期结果）

![清除为透明黑色时的预期结果](images/cleartransparentblack-300px.png)

**解决方案**：
* 将显示为不透明黑色的任何内容更改为 alpha 值0。
* 确保应用清除为透明黑色。
* Unity 默认为明文以使用 MixedRealityToolkit 自动清除，但如果它是非 Unity 应用，应修改与 ID3D11DeiceContext：： ClearRenderTargetView （）一起使用的颜色。 你需要确保清除透明黑色（0，0，0，0），而不是透明的黑色（0，0，0，1）。

你现在可以根据需要调整资产的 alpha 值，但通常不需要这样做。 大多数情况下，MRCs 将看起来不错。 MRC 假设预乘 alpha。 Alpha 值仅影响 MRC 捕获。

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>在 HoloLens 上启用了 MRC 时应发生的情况

以下各项适用于 HoloLens （第一代）和 HoloLens 2，除非另有说明：

* 系统会将应用程序限制为30Hz 呈现。 这会为 MRC 创建一些空间，使应用无需保留固定预算预留，同时还可与30fps
* 录制/流式处理 MRC 时，在设备上看到的全息图内容可能显示为 "火花"：文本可能会变得更难以阅读，而全息图边缘可能会更 jaggy （选择加入到**HoloLens 2**上的第三个照相机渲染可避免这种损害）
* 当应用程序启用了应用程序时，MRC 照片和视频将遵循应用程序的[重点点](focus-point-in-unity.md)，这将有助于确保全息影像精确定位。 对于视频，重点是平滑的，因此，如果焦点深度发生变化，全息影像可能会慢慢地发生缓慢偏移。 以不同于焦点的深度显示的全息影像可能与现实世界的偏移量相同（请参阅下面的示例，重点点设置为2米，而全息图位于1米）。

![2米的全息影像会完全注册到世界。 近距离或远距离的全息影像可能会略微偏移。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>在应用中集成 MRC 功能

混合现实应用可以从应用内启动 MRC 照片或视频捕获，而捕获的内容将在应用中提供，而不会存储到设备的 "照相机"。 您可以创建自定义的 MRC 记录器或利用内置的相机捕获 UI。 

### <a name="mrc-with-built-in-camera-ui"></a>带有内置照相机 UI 的 MRC

开发人员只需编写几行代码，即可使用*[相机捕获 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 获取用户捕获的混合现实照片或视频。

此 API 启动内置的 MRC 相机 UI，用户可以从中拍摄照片或视频，并将生成的捕获返回到应用。  如果你想要创建自己的照相机 UI，或者需要对捕获流进行较低级别的访问，则可以创建自定义混合现实记录。

### <a name="creating-a-custom-mrc-recorder"></a>创建自定义 MRC 记录器

尽管用户可以始终使用系统 MRC 捕获服务来触发照片或视频，但应用程序可能需要构建自定义相机应用程序，但在照相机流中包含全息影像，就像 MRC 一样。 这允许应用程序代表用户启动捕获、生成自定义录制 UI，或自定义 MRC 设置以命名几个示例。

**HoloStudio 使用 MRC 效果添加自定义 MRC 相机**

![HoloStudio 使用 MRC 效果添加自定义 MRC 相机](images/cameraiconholostudio-300px.jpg)

Unity 应用程序应看到属性[Locatable_camera_in_Unity](locatable-camera-in-unity.md) ，以启用全息影像。

其他应用程序可以通过使用[Windows 媒体捕获 api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture)控制相机并添加 MRC 视频和音频效果来包括静止图像和视频中的虚拟全息影像和应用程序音频，来实现此目的。

应用程序有两个选项可添加效果：
* 旧的 API： [MediaCapture. AddEffectAsync （）](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* 新的 Microsoft 推荐 API （返回对象，使其可以操作动态属性）： [AddVideoEffectAsync （）](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)  /  [MediaCapture. AddAudioEffectAsync （）](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) ，该应用程序需要应用程序创建自己的[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)和[IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)实现。 MediaCapture 有关示例用法，请参阅 MRC 效果示例。

>[!NOTE]
> Visual Studio 将无法识别 MixedRealityCapture 命名空间，但字符串仍然有效。

MRC 视频效果（**MixedRealityCapture. MixedRealityCaptureVideoEffect**）

|  属性名称  |  类型  |  默认值  |  描述 |
|----------|----------|----------|----------|
|  StreamType  |  UINT32 （[mediastreamtype.video](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType)）  |  1（VideoRecord）  |  描述此影响所使用的捕获流。 音频不可用。 |
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  用于在视频捕获中启用或禁用全息影像的标志。 |
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  用于在全息影像捕获期间启用或禁用录制指示器的标志。 |
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  用于启用或禁用由 HoloLens 跟踪器支持的视频稳定的标志。 |
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  设置视频抖动使用的历史帧数。 从电源和性能的角度来看，0从0到延迟，几乎是 "免费"。 对于最高质量，建议使用15个（成本为延迟和内存15帧）。 |
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 （HoloLens）1.0 （沉浸式耳机）  |  将范围从0.0 （完全透明）到1.0 的全局不透明度系数设置为 "完全不透明"。 |
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  用于启用或禁用在有显示受保护内容的 2d UWP 应用时返回空帧的标志。 如果此标志为 false，并且二维 UWP 应用显示受保护的内容，则在耳机和混合现实捕获中，二维 UWP 应用将替换为受保护的内容纹理。 |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  用于启用或禁用显示全息相机隐藏区域网格和相邻内容的标志。 |
| OutputSize | 大小 | 0, 0 | 在裁剪视频稳定性后设置所需的输出大小。 如果指定了0或指定了无效的输出大小，则选择默认裁剪大小。 |
| PreferredHologramPerspective | UINT32 | Windows 设备门户中的 "**从相机呈现**" 设置 | 用于指示应捕获的全息相机视图配置的枚举：0（显示）表示不要求应用从照片/视频相机进行渲染，1（PhotoVideoCamera）将要求应用从 photo/视频摄像机（如果应用支持它）呈现。 仅在 HoloLens 2 上受支持 |

>[!NOTE]
> 可以通过转到[混合现实捕获页面](using-the-windows-device-portal.md#mixed-reality-capture)并取消选中 "**从相机**中进行渲染"，在 Windows 设备门户中更改**PreferredHologramPerspective**的默认值。 设置默认为**1 （PhotoVideoCamera）**，但可以取消选中以将其设置为**0 （显示）**。
>
> 2020年6月更新之前， **PreferredHologramPerspective**的默认值为**0 （显示）** （Windows 全息，版本2004生成19041.1106 和 windows 全息，版本1903生成18362.1064）。

MRC 音频效果（**MixedRealityCapture. MixedRealityCaptureAudioEffect**）

| 属性名称 | 类型 | 默认值 | 描述 |
|----------|----------|----------|----------|
| MixerMode | UINT32 | 2（Mic 和系统音频） | 用于指示应使用的音频源的枚举：0（仅限 Mic 音频）、1（仅限系统音频）、2（麦克风和系统音频） |
| LoopbackGain | FLOAT | Windows 设备门户中的**应用音频增益**设置 | 适用于系统音频音量的增益。 范围为0.0 到5.0。 仅在 HoloLens 2 上受支持 |
| MicrophoneGain | FLOAT | Windows 设备门户中的**Mic 音频增益**设置 | 适用于麦克风音量的增益。 范围为0.0 到5.0。 仅在 HoloLens 2 上受支持 |

>[!NOTE]
> 可以通过转到[混合现实捕获页面](using-the-windows-device-portal.md#mixed-reality-capture)并调整其各自设置旁的滑块来更改 Windows 设备门户中**LoopbackGain**或**MicrophoneGain**的默认值。 这两个设置默认为**1.0**，但可以设置为**0.0**和**5.0**之间的任何值。
>
> 使用 Windows 设备门户配置默认增益值是使用2020年6月更新（Windows 全息版、版本2004内部版本19041.1106 和 Windows 全息版，版本1903生成18362.1064）添加的。

### <a name="simultaneous-mrc-limitations"></a>同时 MRC 限制

同时访问 MRC 的多个应用有一定的限制。

#### <a name="photovideo-camera-access"></a>照片/视频相机访问

照片/视频摄像机限制为可同时访问的进程数。 当某个进程录制视频或拍摄照片时，将无法获取照片/视频相机。 （这适用于混合现实捕获和标准照片/视频捕获）

使用 HoloLens 2，应用程序可以使用 MediaCaptureInitializationSettings 的[SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode)属性来指示他们希望在不需要对照片/视频摄像机进行独占控制的情况下运行 SharedReadOnly。 这样做意味着捕获的分辨率和帧速率将限制为其他应用已配置照相机提供的内容。

##### <a name="built-in-mrc-photovideo-camera-access"></a>内置的 MRC 照片/视频相机访问

内置于 Windows 10 的 MRC 功能（通过 Cortana、开始菜单、硬件快捷方式、Miracast、Windows 设备门户）：
* 默认情况下，将使用 ExclusiveControl 运行

但是，对每个要在共享模式下运行的子系统添加了支持：
* 如果应用请求 ExclusiveControl 访问照片/视频摄像机，内置的 MRC 会自动停止使用照片/视频相机，因此应用的请求将会成功。
* 如果在某个应用具有 ExclusiveControl 的情况下启动内置的 MRC，内置的 MRC 将在 SharedReadOnly 模式下运行

此共享模式功能有一些限制：
* 通过 Cortana、硬件快捷方式或 "开始" 菜单的照片：需要 Windows 10 2018 年4月更新版（或更高版本）
* 视频 via Cortana、硬件快捷方式或 "开始" 菜单：需要 Windows 10 2018 年4月更新版（或更高版本）
* 通过 Miracast 流式处理 MRC：需要 Windows 10 十月2018更新（或更高版本）
* 通过 Windows 设备门户或 HoloLens 随附应用的流式处理 MRC：需要 HoloLens 2

>[!NOTE]
> 当另一个应用正在使用照片/视频摄像机时，内置 MRC 相机 UI 的分辨率和帧速率可能会从其正常值中减少。

#### <a name="mrc-access"></a>MRC 访问

使用 Windows 10 4 2018 月版更新后，在多个应用程序中访问 MRC 流的情况不再受限制（不过，对 photo/视频摄像机的访问仍有限制）。

在 Windows 10 4 2018 月版更新之前，应用的自定义 MRC 记录器与系统 MRC （捕获照片、捕获视频或从 Windows 设备门户进行流式处理）互斥。

## <a name="see-also"></a>请参阅

* [混合现实捕获](mixed-reality-capture.md)
* [旁观视图](spectator-view.md)
* [Unity 开发概述](unity-development-overview.md)
* [Unreal 开发概述](unreal-development-overview.md)
