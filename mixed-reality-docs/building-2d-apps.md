---
title: 更新混合现实的 2D UWP 应用
description: 本文概述了如何更新现有的2D 通用 Windows 平台应用, 以便在 HoloLens 和 Windows Mixed Reality 沉浸式耳机上运行。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 应用, UWP, 平面应用, HoloLens, 沉浸式耳机, 应用模型, 后退按钮, 应用栏, dpi, 分辨率, 缩放
ms.openlocfilehash: f9792a7e5fd9729bf9f5f632c699c74c58c10ddf
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414224"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>更新混合现实的 2D UWP 应用

Windows Mixed Reality 使用户能够在您的物理或数字世界中查看全息影像。 就核心而言, HoloLens 和桌面 Pc 都将沉浸式耳机配件附加到 Windows 10 设备;这意味着, 可以在应用商店中以2D 应用的形式运行几乎所有通用 Windows 平台 (UWP) 应用。

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>为混合现实创建 2D UWP 应用

向混合现实耳机引入2D 应用程序的第一步是在桌面监视器上将应用作为标准2D 应用运行。

### <a name="building-a-new-2d-uwp-app"></a>生成新的 2D UWP 应用

若要为混合现实构建新的2D 应用程序, 只需生成标准的2D 通用 Windows 平台 (UWP) 应用。 对于该应用程序, 无需进行其他应用程序更改, 就能在混合现实中以石板的形式运行。

若要开始生成二维 UWP 应用, 请参阅[创建第一个应用一](https://docs.microsoft.com/windows/uwp/get-started/your-first-app)文。

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>将现有2D 应用商店应用引入 UWP

如果存储中已有 2D Windows 应用, 则必须先确保它面向 Windows 10 通用 Windows 平台 (UWP)。 下面是你目前可以使用应用商店应用的所有潜在起点:
<br>

|  起点  |  AppX 清单平台目标  |  如何实现此通用？ | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight 应用程序清单 |  [迁移到 WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 通用  |  8.1 AppX 清单, 不包括平台目标  |  [将应用迁移到通用 Windows 平台](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 应用商店8  |  8个不包括平台目标的 AppX 清单  |  [将应用迁移到通用 Windows 平台](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 应用商店8.1 通用  |  8.1 AppX 清单, 不包括平台目标  |  [将应用迁移到通用 Windows 平台](https://msdn.microsoft.com/library/mt148501.aspx) | 

如果当前构建为 Win32 应用 ("PC, Mac & Linux 独立" 生成目标) 的 2D Unity 应用程序, 则可以通过将 Unity 切换到 "通用 Windows 平台" 生成目标来定位混合现实。

接下来, 我们将讨论如何使用[下面](#publish-and-maintain-your-universal-app)的 Windows 全息设备系列将应用专用于 HoloLens。

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>在 Windows Mixed Reality 沉浸式耳机中运行你的2D 应用

如果已将2D 应用部署到桌面计算机, 在该计算机上进行开发, 并在显示器上尝试使用它, 则已准备好在沉浸式桌面耳机中试用!

只需进入混合现实耳机内的 "开始" 菜单, 然后从此处启动应用即可。 桌面 shell 和全息 shell 共享同一组 UWP 应用, 因此, 从 Visual Studio 部署后, 应用应已存在。

## <a name="targeting-both-immersive-headsets-and-hololens"></a>面向沉浸式耳机和 HoloLens

祝贺你！ 应用现在正在使用 Windows 10 通用 Windows 平台 (UWP)。

现在, 你的应用程序能够在当前的 Windows 设备 (如桌面、移动、Xbox、Windows Mixed Reality 沉浸式耳机和 HoloLens) 上运行, 以及将来的 Windows 设备。 但是, 若要实际将所有这些设备作为目标, 需要确保应用面向 Windows 通用设备系列。

### <a name="change-your-device-family-to-windowsuniversal"></a>将设备系列改为 Windows 通用

现在, 让我们跳转到 AppX 清单, 确保 Windows 10 UWP 应用可在 HoloLens 上运行:
* 用**Visual Studio**打开应用的解决方案文件, 并导航到应用程序包清单
* 右键单击解决方案中的**appxmanifest.xml**文件, 然后单击 "**查看代码**"<br>
  ![解决方案资源管理器中的 appxmanifest.xml](images/openappxmanifest-500px.png)<br>
* 确保目标平台在 "依赖关系" 部分中为 "Windows 通用"。
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* 把!

如果不使用 Visual Studio 作为开发环境, 则可以在所选的文本编辑器中打开**appxmanifest.xml** , 以确保面向的是**Windows 通用** *y*。

### <a name="run-in-the-hololens-emulator"></a>在 HoloLens 模拟器中运行

现在, UWP 应用面向 "Windows 通用", 接下来让我们构建你的应用, 并在[HoloLens 模拟器](using-the-hololens-emulator.md)中运行它。
* 请确保已[安装 HoloLens 模拟器](install-the-tools.md)。
* 在 Visual Studio 中, 选择应用的**x86**生成配置

  ![Visual Studio 中的 x86 生成配置](images/x86setting.png)<br>
* 在 "部署目标" 下拉菜单中选择 " **HoloLens 模拟器**"

  ![部署目标列表中的 HoloLens 模拟器](images/deployemulator-500px.png)<br>
* 选择 "**调试" > "开始调试**" 以部署应用并启动调试。
* 模拟器将启动并运行您的应用程序。
* 使用键盘、鼠标和/或 Xbox 控制器, 将您的应用程序置于世界中以启动它。

  ![使用 UWP 示例加载的 HoloLens 模拟器](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>后续步骤

此时, 可能会出现以下两种情况之一:
1. 应用程序将显示它的初始, 并在将其放入模拟器后开始运行! 出色!
2. 或者, 在看到2D 全息图的加载动画后, 加载将停止, 您将在其初始屏幕上看到您的应用程序。 这意味着出现了问题, 并将进行更多调查, 以了解如何在混合现实中实现应用程序的生活。

若要了解可能导致 UWP 应用无法在 HoloLens 上启动的内容, 必须进行调试。

### <a name="running-your-uwp-app-in-the-debugger"></a>在调试器中运行 UWP 应用

这些步骤将指导你使用 Visual Studio 调试器调试 UWP 应用。
* 如果尚未执行此操作, 请在 Visual Studio 中打开解决方案。 将目标更改为**HoloLens 模拟器**, 将生成配置更改为**x86**。
* 选择 "**调试" > "开始调试**" 以部署应用并启动调试。
* 在世界上, 用鼠标、键盘或 Xbox 控制器放置应用程序。
* Visual Studio 现在应在应用代码中的某个位置中断。
  - 如果应用由于未处理的错误而不会立即崩溃或进入调试器, 请完成应用的核心功能测试, 以确保一切正常运行且正常运行。 你可能会看到如下所示的错误 (正在处理的内部异常)。 若要确保不会错过影响应用体验的内部错误, 请运行自动测试和单元测试, 以确保一切都按预期方式运行。

![使用 UWP 示例加载的 HoloLens 模拟器显示系统异常](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>更新用户界面

现在, UWP 应用运行在沉浸式耳机上,/或在作为二维全息图的情况下运行, 接下来我们要确保它看起来很漂亮。 下面是一些需要考虑的事项:
* Windows Mixed Reality 会按固定分辨率和 DPI (等同于853x480 有效像素) 运行所有2D 应用。 考虑设计是否需要优化此规模, 并查看下面的设计指南, 以改善在 HoloLens 和沉浸式耳机上的体验。
* Windows Mixed Reality[不支持](app-model.md)2d 动态磁贴。 如果你的核心功能显示了有关动态磁贴的信息, 请考虑将该信息移回你的应用程序或浏览[3d 应用程序启动器](3d-app-launcher-design-guidance.md)。

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D 应用视图分辨率和缩放比例

![从响应式设计](images/scale-500px.png)

Windows 10 将所有视觉对象设计从真实屏幕像素变为**有效像素**。 这意味着, 开发人员会按照 Windows 10 人体学接口指导原则为有效像素设计用户界面, 并确保这些有效像素的大小适用于跨设备、分辨率、DPI 等的可用性。有关详细信息, 请参阅[MSDN 上的这篇精彩阅读](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)[版本](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)。

即使有独特的功能可以将应用放在世界上的距离范围内, 也建议使用类似于电视的观看距离, 以获得最佳的可读性, 并与注视/手势交互。 因此, 混合现实中的虚拟石板会在以下位置显示平面 UWP 视图:

**1280x720, 150% DPI**(853x480 有效像素)

此分辨率具有几个优点:
* 这一有效的像素布局将与 tablet 或小型桌面具有相同的信息密度。
* 它与在 Xbox One 上运行的 UWP 应用的固定 DPI 和有效像素匹配, 实现跨设备的无缝体验。
* 当在世界各地的应用范围内扩展时, 此大小看起来很好。

### <a name="2d-app-view-interface-design-best-practices"></a>2D 应用视图界面设计最佳实践

**看**
* 遵循[Windows 10 人体学接口指导原则 (HIG)](https://dev.windows.com/design) , 了解样式、字号和按钮大小。 HoloLens 将执行工作以确保你的应用程序具有兼容的应用模式、可读文本大小和适当的命中目标大小调整。
* 确保你的 UI 遵循最佳做法, 以便在 HoloLen 的独特分辨率和 DPI 上最好地查看最佳[设计](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)。
* 使用 Windows 中的 "薄" 颜色主题建议。

**不要：**
* 在混合现实情况下, 使用户的 UI 变化太大, 以确保用户在耳机中体验和使用熟悉的体验。

### <a name="understand-the-app-model"></a>了解应用模型

混合现实的[应用模型](app-model.md)设计为使用混合现实宿主, 其中的多个应用一起提供。 请将此视为与桌面等效的混合现实, 其中你可以同时运行多个2D 应用。 这会影响应用程序的生命周期、磁贴和其他关键功能。

### <a name="app-bar-and-back-button"></a>应用栏和 "后退" 按钮

二维视图在其内容上方使用应用栏进行修饰。 应用程序栏有两个特定于应用的个性化设置:

**标题:** 显示与应用程序实例关联的磁贴的*displayname*

**后退按钮：** 将引发 *[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 时按下事件。 后退按钮可见性由 *[SystemNavigationManager. AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)* 控制。

![2D 应用视图中的应用程序栏 UI](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*2D 应用视图中的应用程序栏 UI*

### <a name="test-your-2d-apps-design"></a>测试您的2D 应用程序设计

务必要测试您的应用程序以确保文本是可读的, 这些按钮是不再的, 并且整个应用程序看起来是正确的。 可以在桌面耳机、HoloLens、模拟器或将分辨率设置为 1280x720 @150% 的触摸设备上进行[测试](testing-your-app-on-hololens.md)。

## <a name="new-input-possibilities"></a>新的输入可能性

HoloLens 使用高级深度传感器来查看世界并看到用户。 这样就可以实现先进的手势, 如[布隆](gestures.md#bloom)和[分流](gestures.md#air-tap)。 强大的麦克风还启用了[语音体验](voice-input.md)。

使用桌面耳机, 用户可以使用运动控制器指向应用并采取措施。 他们还可以使用游戏板, 将对象定位在其看板上。

Windows 负责处理 UWP 应用的所有复杂性, 将[注视](gaze.md)、手势、语音和运动控制器输入转换为抽象出输入机制的[指针事件](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)。 例如, 用户可能已在运动控制器上进行了一次轻点击, 或在运动控制器上拉取了 Select 触发器, 但2D 应用程序无需知道输入来自何处-它们只是在触摸屏上看到2D 触摸按下。

下面是你在将 UWP 应用引入 HoloLens 时应了解的高级概念/方案:
* [注视](gaze.md)悬停事件, 这可能会意外触发菜单、浮出控件或其他用户界面元素, 只需 gazing 围绕应用程序进行弹出。
* 看不到鼠标输入。 针对 HoloLens 使用适当大小的命中目标, 类似于触摸友好的移动应用程序。 接近应用边缘的小元素尤其难与交互。
* 用户必须将输入模式切换为从滚动到拖到两个手指平移。 如果你的应用程序是针对触控输入设计的, 请考虑确保没有任何主要功能被锁定在两个 finger 平移后。 如果是这样, 请考虑采用其他输入机制, 如可以启动两个 finger 平移的按钮。 例如, 地图应用可以使用两个手指平移进行缩放, 但具有一个加号、减号和旋转按钮, 可通过单击来模拟相同的缩放交互。

[语音输入](voice-input.md)是混合现实体验的关键部分。 使用耳机时, 我们已启用了 Windows 10 中所有的语音 Api。

## <a name="publish-and-maintain-your-universal-app"></a>发布和维护你的通用应用

应用启动并运行后, 打包应用以将[其提交到 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)。

## <a name="see-also"></a>请参阅
* [应用模型](app-model.md)
* [凝视](gaze.md)
* [姿态](gestures.md)
* [运动控制器](motion-controllers.md)
* [语音输入](voice-input.md)
* [将应用提交到 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
