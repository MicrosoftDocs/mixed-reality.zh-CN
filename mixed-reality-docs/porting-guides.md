---
title: 移植指南
description: 介绍如何将现有沉浸式应用程序移植到 Windows Mixed Reality 的分步演练。
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: 端口，移植，unity，中间件，引擎，UWP，Win32
ms.openlocfilehash: ff97f843d6af62a5d49d7920abdf78fa4d1e46c9
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408195"
---
# <a name="porting-guides"></a>移植指南

## <a name="overview"></a>概述

Windows 10 包括对沉浸式和全息耳机的直接支持。 如果已为其他设备（如 Oculus Rift 或 HTC Naopak）生成内容，这些内容将依赖于操作系统的平台 API 之上的库。 将现有的 Win32 Unity VR 应用引入 Windows Mixed Reality 涉及到重定目标使用特定于供应商的 VR Sdk 到 Unity 的跨供应商 VR Api。


## <a name="porting-overview"></a>移植概述

在高级别上，迁移现有内容涉及以下步骤：
1. **请确保您的 PC 正在运行 Windows 10 秋季创意者更新（16299）。** 我们不再建议从有问必答向后跳环接收预览版，因为这些版本对于混合现实开发不是最稳定的。
2. **升级到最新版本的图形或游戏引擎。** 游戏引擎需要支持 Windows 10 SDK 版本10.0.15063.0 （发布于2017年4月）或更高版本。
3. **升级任何中间件、插件或组件。** 如果你的应用程序包含任何组件，则最好升级到最新版本。
4. **删除重复的 sdk 依赖项**。 根据你的内容面向哪个设备，你将需要删除或有条件地编译该 SDK （例如，SteamVR），以便可以改为面向 Windows Api。
5. **处理生成问题。** 此时，迁移练习特定于您的应用程序、您的引擎和您拥有的组件依赖项。

## <a name="common-porting-steps"></a>常见的移植步骤

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>常见步骤1：确保拥有正确的开发硬件

"[安装工具](install-the-tools.md#for-immersive-vr-headset-development)" 页将列出推荐的开发硬件。

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>常见步骤2：升级到 Windows 10 的最新航班

Windows Mixed Reality 平台仍处于积极开发阶段。 建议[加入 Windows 预览体验计划](https://insider.windows.com/)，以访问 "Windows 有问必答 Fast" 航班。
1. 安装[Windows 10 创意者更新](https://www.microsoft.com/software-download/windows10)
2. [加入](https://insider.windows.com/)Windows 预览体验计划。
3. 启用[开发人员模式](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. 通过 "**设置" > 更新 & 安全 "部分**，切换到[Windows 预览体验快速航班](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview)

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>常见步骤3：升级到最新版本的 Visual Studio
* 如果使用的是 Visual Studio，请升级到最新版本
* 请参阅 Visual Studio 2019 下[的安装工具](install-the-tools.md#installation-checklist)页面

### <a name="common-step-4-choose-the-correct-adapter"></a>常见步骤4：选择正确的适配器
* 在包含两个 Gpu 的笔记本系统中，[针对正确的适配器](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)。 这适用于 Unity 和本机 DirectX 应用，其中 ID3D11Device 是为其功能显式或隐式（媒体基础）创建的。

## <a name="unity-porting-guidance"></a>Unity 移植指南

### <a name="unity-step-1-review-the-common-porting-steps-listed-above"></a>Unity 步骤1：查看上面列出的常见移植步骤

查看上面列出的常见步骤，确保正确设置开发环境。 在步骤 #3 中，如果使用的是 Visual Studio，则应选择 "**使用 Unity 的游戏开发**" 工作负荷。 由于将在下一步中安装较新版本的 Unity，因此可以取消选中 "Unity 编辑器可选" 组件。

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity 步骤2：通过 Windows MR 支持升级到 Unity 的最新公共版本
1. 下载最新建议的具有混合现实支持[的 Unity 公共内部版本](install-the-tools.md)。
2. 在开始之前保存项目的副本
3. 如果你的项目是基于早期版本的 Unity 生成的，请查看 Unity 上提供的[文档](https://docs.unity3d.com/Manual/UpgradeGuides.html)。
4. 按照 Unity 站点上的[说明](https://docs.unity3d.com/Manual/APIUpdater.html)使用其自动 API 更新程序
5. 检查并查看你是否需要进行其他更改以使你的项目运行，并处理剩余的错误和警告。 

> [!Note] 
> 如果有依赖的中间件，请检查使用的是最新版本（下面的步骤3中的详细信息）。

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity 步骤3：将中间件升级到最新版本

对于任何 Unity 更新，都有可能需要更新游戏或应用程序所依赖的一个或多个中间件包。 此外，最新的中间件是最新的，最新的中间件会在整个移植过程中增加成功的可能性。

### <a name="unity-step-4-target-your-application-to-run-on-win32"></a>Unity 步骤4：将应用程序定位到在 Win32 上运行

从 Unity 应用程序内部：

* 导航到 "文件-> 生成设置"
* 选择 "PC、Mac、Linux 独立版"
* 将目标平台设置为 "Windows"
* 将体系结构设置为 "x86" 选择 "切换平台"

> [!NOTE] 
> 如果你的应用程序在特定于设备的服务上有任何依赖关系，例如，从流中进行匹配，则需要在此步骤中禁用它们。 你可以挂钩到 Windows 稍后提供的等效服务。

### <a name="unity-step-5-setup-your-windows-mixed-reality-hardware"></a>Unity 步骤5：设置 Windows Mixed Reality 硬件
1. 查看[沉浸式耳机安装程序](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)中的步骤
2. 了解如何[使用 Windows Mixed reality 模拟器](using-the-windows-mixed-reality-simulator.md)并[导航 windows mixed reality 主页](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-6-target-your-application-to-run-on-windows-mixed-reality"></a>Unity 步骤6：将应用程序设定为在 Windows Mixed Reality 上运行
1. 首先，必须将特定于特定的 VR SDK 的任何其他库支持删除或有条件地编译掉。 这些资产经常以与其他 VR Sdk （如 Windows Mixed Reality）不兼容的方式更改项目的设置和属性。
    * 例如，如果你的项目引用 SteamVR SDK，则需要将你的项目更新为，以改用支持 Windows Mixed Reality 和 SteamVR 的 Unity 公共 VR Api。
    * 即将推出其他用于有条件地排除其他 VR Sdk 的特定步骤。
2. 在 Unity 项目中，[面向 Windows 10 SDK](holograms-100.md#target-windows-10-sdk)
3. 对于每个场景，[设置照相机](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-7-use-the-stage-to-place-content-on-the-floor"></a>Unity 步骤7：使用舞台将内容放到地面上

您可以在各种[经验](coordinate-systems.md)范围内构建混合现实体验。

如果要移植**固定规模的体验**，必须确保将 Unity 设置为**静止**跟踪空间类型：

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

上述代码将设置 Unity 的世界坐标系统，以跟踪[固定的引用框架](coordinate-systems.md#spatial-coordinate-systems)。 在静止跟踪模式下，在打开应用程序时，位于面板默认位置（正向-Z）前面的编辑器中的内容将显示在用户的前方。 若要 recenter 用户的固定来源，可以调用 Unity 的[XR。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)方法。

如果迁移的是**大规模体验**或**房间规模体验**，将会相对于地面放置内容。 使用**[空间阶段](coordinate-systems.md#spatial-coordinate-systems)**（表示用户在首次运行期间设置的已定义的层级来源和可选房间边界）的原因。 对于这些体验，必须确保将 Unity 设置为**RoomScale**跟踪空间类型。 尽管 RoomScale 是默认值，但你需要对其进行显式设置，并确保返回 true，以便捕获用户将其计算机从其校准的房间离开的情况：

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

应用成功设置 RoomScale 跟踪空间类型后，放置在 y = 0 平面上的内容将显示在地面上。 位于（0，0，0）的原点将是用户在房间安装期间考验的特定位置，并以-Z 表示在安装过程中所面临的正向方向。

在脚本代码中，您可以对 UnityEngine 调用 TryGetGeometry 方法来获取边界多边形，并指定 "TrackedArea" 的边界类型。 如果用户定义了边界（返回顶点的列表），则可安全地向用户提供**房间规模的体验**，用户可在其中浏览你创建的场景。

当用户接近边界时，系统将自动渲染边界。 您的应用程序不需要使用此多边形来呈现边界本身。

有关详细信息，请参阅[Unity 页中的坐标系统](coordinate-systems-in-unity.md)。

某些应用程序使用矩形来约束其交互。 UWP API 或 Unity 中不直接支持检索最大的内接矩形。 链接到下面的示例代码演示了如何在跟踪边界内查找矩形。 它基于试探法，因此可能找不到最佳解决方案，但结果与预期一致。 可以优化算法中的参数，以在处理时间成本中查找更精确的结果。 该算法位于混合现实工具包的分叉中，该工具包使用 5.6 preview MRTP 版本的 Unity。 这不是公开提供的。 代码应可直接在2017.2 和更高版本的 Unity 中使用。 在不久的将来，会将代码移植到当前 MRTK。

[GitHub 上的代码的 zip 文件](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20)重要文件：
* 资产/HoloToolkit/阶段/脚本/StageManager-用法示例
* 资产/HoloToolkit/阶段/脚本/LargestRectangle-算法的实现
* 资产/HoloToolkit-Run-unittests/Editor/Stage/LargestRectangleTest-算法的普通测试

结果示例：

![结果示例](images/largestrectangle-400px.jpg)

算法基于 Daniel Smilkov：[多边形中的最大矩形](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)的博客

### <a name="unity-step-8-work-through-your-input-model"></a>Unity 步骤8：处理输入模型

每个面向现有 HMD 的游戏或应用程序都将具有一组可处理的输入，其所需的输入类型和体验所需的特定 Api 以及用于获取这些输入的特定 Api。 我们已经投入了大量努力，尽可能简单直接地利用 Windows Mixed Reality 中提供的输入。
1. 通读有关 Windows Mixed Reality 如何公开输入的详细信息，以及如何映射到你的应用程序可以执行的**[操作的详细](input-porting-guide-for-unity.md)** 信息。
2. 选择是要使用 Unity 的跨 VR-SDK 输入 API 还是 MR 专用输入 API。 当前，Unity VR 应用使用一般输入. GetButton/GetAxis Api 进行[Oculus 输入](https://docs.unity3d.com/Manual/OculusControllers.html)和[OpenVR 输入](https://docs.unity3d.com/Manual/OpenVRControllers.html)。 如果你的应用程序已使用这些用于运动控制器的 Api，这是最简单的路径，你只需在输入管理器中重新映射按钮和轴即可。
    * 您可以使用一般的 GetButton/GetAxis Api 或 MR 专用 UnityEngine. XR Api 来访问 Unity 中的运动控制器数据。. Api。 （以前在 Unity 5.6 的 UnityEngine 命名空间中）
    * 请参阅组合游戏板和运动控制器的[工具包中的示例](https://github.com/Microsoft/HoloToolkit-Unity/pull/572)。

### <a name="unity-step-9-performance-testing-and-tuning"></a>Unity 步骤9：性能测试和优化

Windows Mixed Reality 将在各种设备上可用，范围从高端游戏电脑到广泛市场主流 Pc。 根据你的目标市场，你的应用程序的可用计算和图形预算有很大的差异。 在此迁移过程中，你可能会利用高级 PC，并为应用提供大量的计算和图形预算。 如果你希望将应用程序提供给更广泛的受众，则应在[你想要面向的代表硬件](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)上测试和分析你的应用程序。

[Unity](https://docs.unity3d.com/Manual/Profiler.html)和[Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index)都包含性能探查器， [Microsoft](understanding-performance-for-mixed-reality.md)和[Intel](https://software.intel.com/articles/vr-content-developer-guide)发布有关性能分析和优化的指导原则。 在[了解混合现实的性能](understanding-performance-for-mixed-reality.md)方面，提供了有关性能的广泛讨论。 此外，针对[unity 的性能建议](performance-recommendations-for-unity.md)下的 unity 有特定的详细信息。

## <a name="see-also"></a>另请参阅
* [Unity 的输入移植指南](input-porting-guide-for-unity.md)
* [Windows Mixed Reality 最小电脑硬件兼容性指南](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [了解混合现实的性能](understanding-performance-for-mixed-reality.md)
* [Unity 性能建议](performance-recommendations-for-unity.md)
