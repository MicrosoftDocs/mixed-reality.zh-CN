---
title: 建议用于 Unity 的设置
description: Unity 提供一些特定于混合现实的行为，这些行为可通过项目设置进行切换。
author: troy-ferrell
ms.author: trferrel
ms.date: 07/07/2020
ms.topic: article
keywords: unity，设置，混合现实
ms.openlocfilehash: d2cc79ba0818985795c49f8812d33eba77b92b74
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390114"
---
# <a name="recommended-settings-for-unity"></a>建议用于 Unity 的设置

Unity 提供了一组默认选项，这些选项通常是所有平台的平均事例。 但是，Unity 提供一些特定于混合现实的行为，这些行为可通过项目设置进行切换。

## <a name="performant-environment-set-up"></a>设置高性能环境

### <a name="low-quality-settings"></a>低质量设置

将环境的**Unity 质量设置**修改为**非常低**很重要。 这将有助于确保应用程序在适当的帧速率下运行之前。 这对于 HoloLens 开发极其重要。 若要在沉浸式耳机上进行开发，根据桌面的规格来支持 VR 体验，仍可在没有最低质量参数的情况下实现帧速率。

在 Unity 2019 LTS + 中，可以通过转到 "**编辑**  >  **项目设置**  >  **质量**" 并通过单击向下箭头到**非常低**质量级别来设置**默认值**，来设置项目的质量级别。

### <a name="lighting-settings"></a>照明设置

与质量场景设置相似，必须为混合现实应用程序设置最佳照明设置。 在 Unity 中，通常会对场景产生最大性能影响的照明设置是**实时全局照明**。 这可以通过以下方式关闭：在 "**窗口**  >  **渲染**  >  **照明**" "  >  **实时全局照明**" 下。

还有另一个照明设置，**融入全局照明**。 此设置可以提供沉浸式耳机上的高性能和直观的结果，但通常不适用于 HoloLens 开发。 **融入 Global Illumniation**仅针对静态 gameobject 进行计算，这通常是由于未知和不断变化的环境的性质，而在 HoloLens 场景中找不到。

有关详细信息，请阅读[Unity 的全局照明](https://docs.unity3d.com/Manual/GIIntro.html)。 

>[!NOTE]
> **实时全局照明**是**根据场景**设置的，因此，开发人员必须为其项目中的每个 Unity 场景保存此属性。

### <a name="single-pass-instancing-rendering-path"></a>单步实例呈现路径

在混合现实应用程序中，场景呈现两次，一次为用户提供一次。 与传统的3D 开发相比，这实际上会使需要计算的工作量加倍。 因此，请务必在 Unity 中选择最有效的呈现路径，以节省 CPU 和 GPU 时间。 单个传递实例呈现为混合现实应用优化了 Unity 呈现管道，因此建议为每个项目默认启用此设置。

在 Unity 项目中启用此功能

1)  打开“播放器 XR 设置”（转到“编辑” > “项目设置” > “播放器” > “XR 设置”）    
2) 从“立体渲染方法”下拉菜单中选择“单通道实例化”（必须选中“支持虚拟现实”复选框）  

有关此呈现方法的更多详细信息，请参阅 Unity 中的以下文章。

- [如何使用高级立体渲染最大化 AR 和 VR 的性能](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [单通道实例化](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> 如果开发人员的现有自定义着色器不是针对实例化编写的，则单通道实例化渲染会发生一个常见问题。 启用此功能后，开发人员可能会注意到，某些 GameObject 只在一只眼睛中呈现。 这是因为，关联的自定义着色器没有与实例化相关的适当属性。
>
> 请参阅 Unity 文章 [HoloLens 的 单通道立体渲染](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)来了解如何解决此问题

### <a name="enable-depth-buffer-sharing"></a>启用深度缓冲共享

若要从用户的感觉获得更好的全息图稳定性，建议启用 Unity 中的**深度缓冲区共享**属性。 通过启用，Unity 将使用 Windows Mixed Reality 平台共享你的应用程序生成的深度映射。 然后，该平台将能够更好地针对应用程序呈现的任何给定帧，更好地为场景优化全息图稳定性。

在 Unity 项目中启用此功能

1) 打开“播放器 XR 设置”（转到“编辑” > “项目设置” > “播放器” > “XR 设置”）    
2) 选中 "在**虚拟现实 sdk**Windows Mixed reality 扩展下**启用深度缓冲区共享**" 复选框  >  **Windows Mixed Reality** （必须选中 "**支持虚拟现实**" 复选框）

此外，建议在此面板中的 "**深度格式**" 设置下选择 " **16 位深度**"，尤其是对于 HoloLens 开发。 与24位相比，选择16位可显著减少带宽需求，因为需要移动/处理的数据量较少。

为了使 Windows Mixed Reality 平台优化全息影像稳定性，它依赖于深度缓冲区来精确并匹配屏幕上呈现的所有全息影像。 因此，在上进行深度缓冲共享时，在呈现颜色时，这一点非常重要，也就是呈现深度。 在 Unity 中，大多数不透明或 TransparentCutout 的材料将默认呈现深度，但透明和文本对象通常不会呈现深度，尽管这是依赖于着色器等。

如果使用[混合现实工具包标准着色器](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)来呈现透明对象的深度：

1) 选择使用 MRTK 标准着色器的透明材料，并打开检查器编辑器窗口
2) 选择深度缓冲区共享警告中的 "**立即修复**" 按钮。 也可以通过将**呈现模式**设置为 "**自定义**" 来手动执行此方法。然后将**模式**设置为**透明**，最后将 "**深度写入**" 设置为 **"开"**

> [!IMPORTANT]
> 在更改这些值时，开发人员应注意 Z 反击，同时还应注意相机的近/远平面设置。 当两个 gameobject 尝试呈现到相同的像素并由于深度缓冲区保真的限制（即 z 深度），Unity 无法识别哪个对象位于另一个对象之前。 开发人员将注意两个游戏对象之间的闪烁，因为它们会*抵抗*相同的 z 深度值。 这可以通过切换到24位深度格式来解决，因为每个对象的值的范围都要根据其 z 深度从相机计算。
>
> 不过，建议使用此方法，特别是在 HoloLens 开发环境中，可以改为将相机的近处和 far 面修改为较小的范围，并保留16位的深度格式。 Z 深度以非线性方式映射到沿近和远相机平面的值范围。 可以通过选择场景中的*主相机*和**检查器**下的 "检查 **&** 器" 来修改此项 从1000m 到100m 或其他 x 值等）

>[!IMPORTANT]
> 使用16位深度格式时， [Unity 不会创建模具缓冲区](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)。 因此，除非选择了将创建[8 位模具缓冲区](https://docs.unity3d.com/Manual/SL-Stencil.html)的24位深度格式，否则某些 Unity UI 效果和其他模具所需的效果将无法工作。

### <a name="building-for-il2cpp"></a>为 IL2CPP 生成

Unity 已弃用 .NET 脚本编写后端的支持，因此建议开发人员使用**IL2CPP**来实现 UWP visual studio build。 虽然这带来了不同的优点，但从 Unity for **IL2CPP**构建 visual studio 解决方案比旧的 .net 方法要慢得多。 因此，强烈建议遵循用于生成**IL2CPP**的最佳做法，以便在开发迭代时节省时间。

1) 每次将项目生成到同一个目录，以便在其中重复使用预先生成的文件，从而利用增量生成
2) 禁用项目 & 生成文件夹的反恶意软件扫描
   - 在 Windows 10 设置应用下打开**病毒 & 威胁防护**
   - 选择 "安全 **& 威胁防护设置**" 下的 "**管理设置**"
   - 选择 "**排除**" 部分下的 "**添加或删除排除**项"
   - 单击 "**添加排除**"，然后选择包含 Unity 项目代码和生成输出的文件夹
3) 使用 SSD 进行生成

有关详细信息，请阅读[IL2CPP 优化生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)。

> [!NOTE]
> 此外，设置[缓存服务器](https://docs.unity3d.com/Manual/CacheServer.html)可能会有所帮助，尤其是对于包含大量资产（不包括脚本文件）或不断变化的场景/资产的 Unity 项目而言。 打开项目时，Unity 会在开发人员计算机上将符合条件的资产存储为内部缓存格式。 必须重新导入项，因此，项在修改后会重新经过处理。 此过程可以执行一次，结果可保存在缓存服务器，因此可与其他开发人员共享以节省时间，无需让每个开发人员在本地重新导入新的更改。

## <a name="publishing-properties"></a>发布属性

### <a name="holographic-splash-screen"></a>全息初始屏幕

HoloLens 具有移动类 CPU 和 GPU，这意味着可能需要更长的时间来加载应用。 在应用程序加载时，用户只会看到黑色，因此他们可能会想知道发生了什么情况。 若要在加载过程中再次向它们，可添加全息初始屏幕。

若要切换全息初始屏幕：

1) 中转到 "**编辑**  >  **项目设置**  >  **播放器**" 页面
2) 单击 " **Windows 应用商店**" 选项卡并打开 "**初始图像**" 部分
3) 在 " **Windows 全息 > 全息闪屏" 映像**属性下应用所需的映像。
    - 切换 "**显示 Unity 初始屏幕**" 选项将启用或禁用 Unity 品牌初始屏幕。 如果没有 Unity Pro 许可证，则将始终显示 Unity 品牌初始屏幕。
    - 如果应用了**全息初始映像**，无论是启用还是禁用了 "显示 Unity 初始屏幕" 复选框，它都将始终显示。 只有具有 Unity Pro 许可证的开发人员才能指定自定义全息启动映像。

|  显示 Unity 初始屏幕  |  全息闪屏映像  |  行为 |
|----------|----------|----------|
|  启用  |  无  |  显示5秒的默认 Unity 初始屏幕或在加载应用之前，以较长者为准。 |
|  启用  |  自定义  |  显示自定义初始屏幕5秒或在加载应用之前，以较长者为准。 |
|  关闭  |  无  |  在加载应用之前显示透明的黑色（无）。 |
|  关闭  |  自定义  |  显示自定义初始屏幕5秒或在加载应用之前，以较长者为准。 |

有关详细信息，请阅读[Unity 初始屏幕文档](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html)。

### <a name="tracking-loss"></a>失跟

混合现实耳机依赖于查看它周围的环境，以构建[全球锁定的坐标系](coordinate-systems-in-unity.md)，使全息影像保持在位置。 当耳机无法在世界各地定位时，耳机被称为*丢失跟踪*。 在这些情况下，依赖于全球锁定坐标系的功能（如空间阶段、空间锚和空间映射）不起作用。

如果发生跟踪丢失，则 Unity 的默认行为是停止渲染全息影像，暂停[游戏循环](https://docs.unity3d.com/Manual/ExecutionOrder.html)，并显示一条跟踪丢失的通知，以使用户看起来更舒适。 还可以以跟踪丢失图像的形式提供自定义通知。 对于依赖于整个体验的跟踪的应用，足以让 Unity 完全处理此过程，直到重新获得跟踪。 开发人员可以在跟踪丢失期间提供要显示的自定义图像。

自定义跟踪丢失映像：

1) 中转到 "**编辑**  >  **项目设置**  >  **播放器**" 页面
2) 单击 " **Windows 应用商店**" 选项卡，并打开 "**初始图像**" 部分
3) 在 " **Windows 全息 > 跟踪丢失映像**" 属性下应用所需的映像。

#### <a name="opt-out-of-automatic-pause"></a>选择退出自动暂停

某些应用程序可能不需要跟踪（例如，[仅限打印的应用程序](coordinate-systems-in-unity.md)，例如360度视频查看器），或在跟踪丢失时可能需要继续处理。 在这些情况下，应用可以选择不丢失跟踪行为的默认值。 选择此项的开发人员负责隐藏/禁用任何不能在跟踪丢失方案中正确呈现的对象。 在大多数情况下，建议在这种情况下呈现的内容只是正文锁定的内容，并在主相机周围居中。

选择退出自动暂停行为：

1) 请参阅**编辑**  >  **项目设置**  >  **播放器**页面
2) 单击 " **Windows 应用商店**" 选项卡并打开 "**初始图像**" 部分
3) 修改 "**跟踪丢失时暂停" 和 "显示图像**" 复选框中的 Windows 全息 >。

#### <a name="tracking-loss-events"></a>跟踪丢失事件

若要在跟踪丢失时定义自定义行为，请处理全局[跟踪丢失事件](tracking-loss-in-unity.md)。

### <a name="capabilities"></a>功能

为了使应用程序能够利用特定功能，它必须在其清单中声明相应的功能。 清单声明可以在 Unity 中进行，因此它们包含在每个后续的项目导出中。

可以通过以下方式为混合现实应用程序启用功能：

1) 中转到 "**编辑**  >  **项目设置**  >  **播放器**" 页面
2) 单击 " **Windows 应用商店**" 选项卡，打开 "**发布设置**" 部分，并查找**功能**列表

为全息应用启用常用 Api 的适用功能包括：
<br>

|  功能  |  需要功能的 Api |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  网络摄像头  |  PhotoCapture 和 VideoCapture |
|  PicturesLibrary/VideosLibrary  |  PhotoCapture 或 VideoCapture （存储捕获的内容时） |
|  麦克风  |  VideoCapture （捕获音频时）、DictationRecognizer、GrammarRecognizer 和 KeywordRecognizer |
|  InternetClient  |  DictationRecognizer （和使用 Unity 探查器） |

## <a name="see-also"></a>另请参阅

* [Unity 开发概述](unity-development-overview.md)
* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
