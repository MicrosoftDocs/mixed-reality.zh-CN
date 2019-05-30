---
title: Unity 的推荐的设置
description: Unity 提供了一些特定于可通过项目设置切换状态的混合现实的行为。
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: unity、 设置、 混合的现实
ms.openlocfilehash: a26dbdb63c8bad9bb9659a6a3303c0b0ab418580
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270377"
---
# <a name="recommended-settings-for-unity"></a>Unity 的推荐的设置

Unity 提供了一组通常是所有平台的平均大小写的默认选项。 但是，Unity 提供了一些特定于可通过项目设置切换状态的混合现实的行为。

## <a name="performant-environment-set-up"></a>高性能环境设置

### <a name="low-quality-settings"></a>低质量设置

务必要修改**Unity 质量设置**为您的环境与**非常低**。 这将有助于确保应用程序正在以在相应帧速率。 这是用于 Hololens 开发非常重要。 沉浸式耳机，具体取决于增强 VR 体验中，在桌面的规格上进行开发一个仍可实现不带最低质量参数的帧速率。 

在 Unity 2018 LTS 及更高，可以通过设置项目的质量级别：

下**编辑** > **项目设置** > **质量**> 设置**默认**通过单击向下的箭头**非常低**质量级别

### <a name="lighting-settings"></a>照明设置

质量场景设置相似，它是必须设置为 Mixed Reality 应用程序的最佳照明设置。 在 Unity 中，将通常对性能影响最大场景的照明设置是**实时全局照明**。 这可以通过转关闭**窗口** > **呈现** > **照明设置** > **实时全局照明**。 

没有其他照明设置，**内嵌全局照明**。 此设置可以在沉浸式耳机提供高性能且直观地显著的结果，但通常是不适用于 HoloLens 开发。 **包含全局 Illumniation**仅针对静态 GameObjects 通常未找到了未知且不断变化的环境的性质的 HoloLens 场景中计算。

请阅读[Unity 中的全局照明](https://docs.unity3d.com/Manual/GIIntro.html)有关详细信息。 

>[!NOTE]
> **实时全局照明**设置**每个场景**并因此开发人员必须将此属性对于每个 Unity 场景保存在其项目中。 

### <a name="single-pass-instancing-rendering-path"></a>单个传递实例化呈现路径

在混合现实应用程序中场景两次，一次为呈现给用户的每只眼睛。 与传统的 3D 开发相比，这有效地增加一倍将进行计算所需的工作量。 因此，务必在 Unity 中要保存对 CPU 和 GPU 时间的两个选择最有效的呈现路径。 单个传递实例的呈现优化了混合现实应用 Unity 呈现管道并因此建议启用此设置默认情况下，每个项目。 

若要启用此功能在 Unity 项目中
1)  打开**播放器 XR 设置**(转到**编辑** > **项目设置** > **播放机** > **XR 设置**)
2) 选择**单个传递二次实例化**从**立体声呈现方法**下拉列表菜单 (**虚拟现实支持**必须选中复选框)

有关使用此方法时呈现更多详细信息从 Unity 阅读以下文章。
- [如何使用高级立体声呈现 AR 和 VR 性能最大化](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [单次传递实例化](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> 如果开发人员已具有没有为编写的现有自定义着色器，会发生与单个传递实例呈现一个常见的问题实例化。 启用此功能后, 开发人员可能会注意到某些 GameObjects 仅呈现一眼中。 这是因为关联的自定义着色器不具有适当的属性为实例化。
>
> 请参阅[单个传递立体声的呈现 HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)从 Unity 如何解决此问题

### <a name="enable-depth-buffer-sharing"></a>启用深度缓冲区共享

若要实现更好的 hologram 稳定性从用户的角度来看，它建议启用**深度缓冲区共享**Unity 中的属性。 通过启用该选项，Unity 将共享生成的应用程序与 Windows Mixed Reality 平台深度映射。 然后，平台将能够更好地优化全息图专门为您的场景的任何给定的框架呈现的应用程序的稳定性。

若要启用此功能在 Unity 项目中
1) 打开**播放器 XR 设置**(转到**编辑** > **项目设置** > **播放机** > **XR 设置**)
2) 选中的复选框**启用深度缓冲区共享**下**虚拟现实 Sdk** > **Windows Mixed Reality**扩展 (**虚拟现实支持**必须选中复选框)

此外，我们建议选择**16 位深度**下**深度格式**中此面板中，尤其是对于 Hololens 开发的设置。 因为将需要较少的数据移动/处理，选择 16 位相比 24 位将显著减少带宽要求。

>[!NOTE]
> 更改照相机的附近/远面设置这些值时，开发人员应注意的 Z 值争夺。 当两个 gameobjects 尝试呈现到同一像素和由于限制的保真度的深度缓冲区 （即 Z 值争夺时发生 z 深度），Unity 无法辩明哪个对象位于其他。 开发人员会注意到两个游戏对象在它们之间闪烁*打击*在同一 z 深度值。 可以通过切换到 24 位深度格式，因为会有更大范围的值来计算后从照相机其 z 深度的每个对象的要解决此问题。
>
> 但是，建议，特别是对于 Hololens 开发，若要修改照相机的附近和远改为平面范围更小和保留的 16 位深度设置的格式。 Z 深度非以线性方式映射到沿近和远照相机的值的范围的平面。 这可以通过选择修改*Main Camera*您的场景中并在**Inspector**，更改**近和远修剪平面**值，以减少它们的范围 （即 从 x 值为 1 亿或其他 1000 m，等等。）

### <a name="building-for-il2cpp"></a>为 IL2CPP 构建

Unity 已弃用支持脚本编写后端，因此建议开发人员可利用.NET **IL2CPP** visual studio 生成适用于其 UWP。 尽管这带来了各种优势，但从适用于 Unity 生成 visual studio 解决方案**Il2CPP**可以是比旧的.NET 方法慢明显偏离。 因此，强烈建议遵循最佳实践构建**IL2CPP**节省开发迭代时。

1) 利用通过构建你的项目到同一目录每次都重新使用的预建的文件那里增量生成
2) 禁用反恶意软件扫描，为你的项目和生成文件夹
   - 打开**病毒和威胁保护**下在 Windows 10 设置应用
   - 选择**管理设置**下**病毒和威胁保护设置**
   - 选择**添加或删除排除**下**排除**部分
   - 单击**添加一个排除项**，并选择该文件夹包含你的 Unity 项目代码并生成输出
3) 利用生成的 SSD

请阅读[优化生成时间 IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)的详细信息。

> [!NOTE]
> 此外，它可能会有所帮助安装程序[缓存服务器](https://docs.unity3d.com/Manual/CacheServer.html)，尤其是对于具有大量的 （不包括脚本文件） 的资产或不断的 Unity 项目更改场景/资产。 打开项目时，Unity 将符合要求的资产存储到开发人员计算机上的内部缓存格式。 必须重新导入并因此重新处理时修改项。 此过程可以执行一次和保存在缓存服务器，因此与其他开发人员节省时间，而不是处理重新导入新的本地更改的每个开发人员共享。

## <a name="publishing-properties"></a>发布属性

### <a name="holographic-splash-screen"></a>全息版的初始屏幕

HoloLens 具有移动类的 CPU 和 GPU，这意味着应用程序可能需要更长时间加载。 正在加载应用程序，而用户只需将看到黑色，并因此它们可能想知道这怎么回事。 若要确保它们在加载期间，可以添加全息版的初始屏幕。

若要切换全息版的初始屏幕：
1) 转到**编辑** > **项目设置** > **播放机**页
2) 单击**Windows 应用商店**选项卡并打开**初始图像**部分
3) 应用在你所需的映像**Windows Holographic > Holographic 初始图像**属性。
    - 切换**显示 Unity 初始屏幕**选项将启用或禁用 Unity 经过品牌打造的初始屏幕。 如果还没有一个 Unity Pro 许可证，将始终显示 Unity 品牌初始屏幕。
    - 如果**Holographic 初始图像**是应用，它将始终显示无论是否启用或禁用显示 Unity 初始屏幕复选框。 指定自定义 holographic 初始图像是仅供开发人员使用 Unity Pro 许可证。

|  显示 Unity 初始屏幕  |  Holographic 初始图像  |  行为 |
|----------|----------|----------|
|  开  |  无  |  显示默认的 Unity 初始屏幕的 5 秒内或应用程序加载之前，较长者为准。 | 
|  开  |  自定义  |  显示自定义初始屏幕的 5 秒内或应用程序加载之前，较长者为准。 | 
|  关闭  |  无  |  显示透明的黑色 (为 nothing)，直到加载应用程序。 | 
|  关闭  |  自定义  |  显示自定义初始屏幕的 5 秒内或应用程序加载之前，较长者为准。 | 

请阅读[Unity 的初始屏幕文档](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html)的详细信息。

### <a name="tracking-loss"></a>跟踪丢失

混合的现实耳机取决于出现在其构造周围环境[世界锁定坐标系](coordinate-systems-in-unity.md)，它允许全息保持不动。 找不到本身在世界耳机时，将耳机称其具有*丢失跟踪*。 在这些情况下，功能依赖于世界上锁定坐标系统，例如空间阶段、 空间的定位点和空间映射，请不起作用。

如果发生的跟踪丢失，Unity 的默认行为是停止呈现全息，暂停[游戏循环](http://docs.unity3d.com/Manual/ExecutionOrder.html)，并显示丢失通知，轻松跟踪遵循用户视线移动。 也可以在一个跟踪窗体中提供的自定义通知丢失映像。 对于依赖于跟踪其整体体验的应用程序，就足以让 Unity 处理这种情况完全之前重新获取跟踪。 开发人员可以提供要跟踪丢失过程中显示的自定义映像。 

若要自定义跟踪丢失的映像：
1) 转到**编辑** > **项目设置** > **播放机**页
2) 单击**Windows 应用商店**选项卡并打开**初始图像**部分
3) 应用在你所需的映像**Windows Holographic > 跟踪丢失映像**属性。

#### <a name="opt-out-of-automatic-pause"></a>选择退出自动暂停

某些应用可能不需要跟踪 (例如[仅方向应用](coordinate-systems-in-unity.md)360 度视频观看者等) 或可能需要继续处理不间断地跟踪时的都将丢失。 在这些情况下，应用可以选择禁用默认丢失跟踪行为。 选择此开发人员负责进行隐藏或禁用跟踪丢失方案中将无法正常呈现的任何对象。 在大多数情况下，建议使用，因为用例是正文锁定内容呈现的唯一内容以主相机中心。

若要选择退出自动暂停行为：
1) 转到**编辑** > **项目设置** > **播放机**页
2) 单击**Windows 应用商店**选项卡并打开**初始图像**部分
3) 修改**Windows Holographic > 上跟踪丢失暂停和显示图像**复选框。

#### <a name="tracking-loss-events"></a>跟踪丢失事件

若要定义自定义行为，跟踪丢失时，处理全局[跟踪丢失事件](tracking-loss-in-unity.md)。

### <a name="capabilities"></a>功能

若要充分利用特定功能的应用，它必须声明其清单中的相应功能。 可以在 Unity 中进行的清单的声明，以便将它们包括在每个后续项目导出。 

实现混合现实应用程序的可启动这些功能：
1) 转到**编辑** > **项目设置** > **播放机**页
2) 单击**Windows 应用商店**选项卡并打开**发布设置**部分，并查找**功能**列表

用于启用全息版的应用程序的常用的 Api 适用的功能包括：
<br>

|  功能  |  Api，需要功能 |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver | 
|  网络摄像头  |  PhotoCapture 和 VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture 或 VideoCapture，分别 （时存储捕获的内容） | 
|  麦克风  |  VideoCapture （时捕获音频）、 DictationRecognizer、 GrammarRecognizer 和 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer （并使用 Unity Profiler） | 

## <a name="see-also"></a>请参阅
* [Unity 开发概述](unity-development-overview.md)
* [混合现实的 Understaing 性能](understanding-performance-for-mixed-reality.md)
* [针对 Unity 的性能建议](performance-recommendations-for-unity.md)
