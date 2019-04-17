---
title: 更新适用于混合现实的 2D UWP 应用
description: 本文概述了更新现有的 2D 通用 Windows 平台应用 HoloLens 和 Windows Mixed Reality 沉浸式耳机上运行。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 2D 应用程序中，UWP，平面应用，HoloLens，沉浸式耳机，应用程序模型返回按钮，应用程序栏、 dpi，分辨率，规模
ms.openlocfilehash: 35a2e7774a79e35893821467f7e9ef8c004efa20
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592422"
---
# <a name="updating-2d-uwp-apps-for-mixed-reality"></a>更新适用于混合现实的 2D UWP 应用

Windows Mixed Reality，用户若要查看全息，就好像它们是右周围，还是数字世界中。 就其核心而言，HoloLens 和桌面 Pc 将附加到的沉浸式头戴式附件是 Windows 10 设备;这意味着你能够以 2D 应用程序存储区中运行几乎所有通用 Windows 平台 (UWP) 应用。

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>创建适用于混合现实的 2D UWP 应用

2D 应用程序引入混合的现实耳机的第一步是获取应用程序作为标准 2D 应用程序在桌面监视器上运行。

### <a name="building-a-new-2d-uwp-app"></a>生成新的 2D UWP 应用

若要生成新的 2D 混合现实应用，只需生成标准 2D 通用 Windows 平台 (UWP) 应用。 需要对该应用，然后作为一台平板电脑运行混合现实中任何其他应用更改不。

若要开始构建 2D 的 UWP 应用，请查看[创建第一个应用](https://docs.microsoft.com/windows/uwp/get-started/your-first-app)一文。

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>现有的 2D 应用商店应用程序引入 UWP

如果在存储区中已有 2D 的 Windows 应用，必须首先确保它面向 Windows 10 通用 Windows 平台 (UWP)。 下面是所有潜在起始点今天你可能与应用商店应用程序：
<br>

|  起始点  |  AppX 清单平台目标  |  如何使此世界？ | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Silverlight 应用程序清单 |  [将迁移到 WinRT](https://msdn.microsoft.com/library/windows/apps/dn642486(v=vs.105).aspx) | 
|  Windows Phone 8.1 通用  |  8.1 不包括目标平台的 AppX 清单  |  [将您的应用程序迁移到通用 Windows 平台](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 应用商店 8  |  不包括目标平台的 8 AppX 清单  |  [将您的应用程序迁移到通用 Windows 平台](https://msdn.microsoft.com/library/mt148501.aspx) | 
|  Windows 应用商店 8.1 通用  |  8.1 不包括目标平台的 AppX 清单  |  [将您的应用程序迁移到通用 Windows 平台](https://msdn.microsoft.com/library/mt148501.aspx) | 

如果必须立即生成为 （"PC、 Mac 和 Linux 独立"生成目标） 的 Win32 应用程序的 2D Unity 应用，你可以通过改为切换到"通用 Windows 平台"生成目标的 Unity 面向混合的现实。

我们将讨论方法，可以限制您的应用程序特定于使用 Windows.Holographic 设备系列的 HoloLens[如下](#publish-and-maintain-your-universal-app)。

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>运行 Windows Mixed Reality 沉浸式头戴式 2D 应用

如果你已将 2D 应用部署到你要开发并且尝试在监视器上的桌面计算机，您已经准备好在沉浸式的桌面耳机中试用它 ！

只需转到开始菜单中混合的现实耳机，并从该处启动应用。 桌面外壳程序和全息版的 shell 都共享一组相同的 UWP 应用，并因此应用程序应从 Visual Studio 部署后存在。

## <a name="targeting-both-immersive-headsets-and-hololens"></a>面向沉浸式耳机和 HoloLens

祝贺你！ 你的应用现在使用 Windows 10 通用 Windows 平台 (UWP)。

您的应用程序现在是能够在今天的桌面、 移动、 Xbox、 Windows Mixed Reality 沉浸式耳机等 HoloLens，以及为未来的 Windows 设备的 Windows 设备上运行。 但是，若要实际针对所有这些设备，并将需要确保您的应用程序所面向的 Windows.Universal 设备系列。

### <a name="change-your-device-family-to-windowsuniversal"></a>更改您的设备系列为 Windows.Universal

现在让我们跳转到你的 AppX 清单以确保你的 Windows 10 UWP 应用可以在 HoloLens 上运行：
* 打开与应用程序的解决方案文件**Visual Studio**并导航到应用程序包清单
* 右键单击**Package.appxmanifest**文件位于你的解决方案，并转到**查看代码**<br>
  ![在解决方案资源管理器中的 package.appxmanifest](images/openappxmanifest-500px.png)<br>
* 请确保您的目标平台中的依赖项部分 Windows.Universal
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* 保存 ！

如果不为您的开发环境中使用 Visual Studio，则可以打开**AppXManifest.xml**中以确保您的目标所选的文本编辑器**Windows.Universal** *TargetDeviceFamily*。

### <a name="run-in-the-hololens-emulator"></a>HoloLens 的模拟器中运行

现在，你的 UWP 应用面向"Windows.Universal"，让我们构建您的应用程序，然后在运行[HoloLens 模拟器](using-the-hololens-emulator.md)。
* 请确保你拥有[安装了 HoloLens Emulator](install-the-tools.md)。
* 在 Visual Studio 中，选择**x86**生成应用的配置

  ![x86 生成 Visual Studio 中的配置](images/x86setting.png)<br>
* 选择**HoloLens 模拟器**部署目标下拉列表菜单中

  ![HoloLens 仿真程序中部署目标列表](images/deployemulator-500px.png)<br>
* 选择**调试 > 启动调试**来部署应用，并开始调试。
* 在仿真程序将启动并运行您的应用程序。
* 使用键盘、 鼠标和/或 Xbox 控制器，将您的应用程序放在世界上启动它。

  ![HoloLens 仿真器加载与 UWP 示例](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>后续步骤

此时，可能发生两项操作之一：
1. 您的应用程序将显示其初始并开始运行后放置在仿真程序中 ！ 太好了 ！
2. 或者请参阅 2D hologram 加载动画之后，加载将停止，将只看到您的应用程序在其初始屏幕。 这意味着出现了问题，这需要花费更多的调查以了解如何将应用迁移到混合现实中的时间。

若要获取到什么可能会导致你的 UWP 应用的底部，不能在 HoloLens 上启动，您需要调试。

### <a name="running-your-uwp-app-in-the-debugger"></a>在调试器中运行 UWP 应用

这些步骤将引导您完成调试 UWP 应用使用 Visual Studio 调试器。
* 如果尚未这样做，Visual Studio 中打开你的解决方案。 更改到目标**HoloLens 模拟器**和生成配置以进行**x86**。
* 选择**调试 > 启动调试**来部署应用，并开始调试。
* 在使用鼠标、 键盘或 Xbox 控制器世界中将此应用程序。
* Visual Studio 应立即在应用代码中某处中断。
  - 如果您的应用程序不会立即崩溃或进入调试器由于未经处理的错误，然后经过测试流程的应用程序以确保一切都运行，并且功能的核心功能。 您可能会看到错误，如 （正在处理的内部异常） 如下图所示。 若要确保不会错过影响您的应用程序体验的内部错误，运行通过自动的测试和单元测试，以确保一切按预期的行为。

![HoloLens 仿真器加载与 UWP 示例显示系统异常](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>更新你的 UI

现在，运行 UWP 应用的沉浸式耳机和/或作为 2D 全息图 HoloLens，接下来我们将确保它看起来美观。 下面是一些要考虑的事项：
* 到 853 x 480 有效像素，Windows Mixed Reality 将在固定的分辨率和 DPI 等同于运行 2D 的所有应用。 如果您的设计需要在此规模较大的优化，请考虑并查看设计以下指南来增强 HoloLens 和沉浸式耳机的体验。
* Windows Mixed Reality[不支持](app-model.md)2D 动态磁贴。 如果您的核心功能动态磁贴上显示信息，请考虑将该信息移回您的应用程序或探索[三维应用启动器上](3d-app-launcher-design-guidance.md)。

### <a name="2d-app-view-resolution-and-scale-factor"></a>2D 应用视图解析和缩放系数

![从响应式设计](images/scale-500px.png)

Windows 10 移动所有视觉对象设计从到的实际屏幕像素**有效像素**。 这意味着，开发人员设计它们遵循 Windows 10 人机接口指南 》 的有效像素的 UI 和 Windows 缩放可以确保这些有效像素的适当大小的设备，分辨率、 DPI，跨可用性等。请参阅此[MSDN 上的很好读](https://msdn.microsoft.com/library/windows/apps/Dn958435.aspx)了解详细信息以及此[生成演示文稿](http://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)。

即使使用独特的功能将应用放在您在为单位的距离范围内的世界，类似于电视的查看距离建议以产生最佳可读性和与的视线移动/手势的交互。 正因为如此，虚拟平板式混合现实在家中的将显示在你平面 UWP 视图：

**1280 x 720、 150 %dpi** （853 x 480 有效像素）

此解决方案具有以下优点：
* 有关为平板电脑或小桌面的相同信息密度将具有此有效像素布局。
* 它可匹配固定的 DPI 和适用于 Xbox One，启用无缝体验跨设备上运行的 UWP 应用的有效像素。
* 此大小看起来没问题，我们的世界中应用的距离范围内缩放时。

### <a name="2d-app-view-interface-design-best-practices"></a>2D 应用视图接口设计最佳实践

**执行操作：**
* 请按照[Windows 10 人机接口准则 (HIG)](https://dev.windows.com/design)样式、 字体大小和按钮大小。 HoloLens 将执行的工作以确保你的应用具有兼容的应用模式、 可读的文本大小和相应的命中的目标大小调整。
* 确保在 UI 如下所示的最佳做法[响应式设计](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx)查找最佳支持 HoloLen 的唯一分辨率和 DPI。
* 从 Windows 使用的"light"颜色主题建议。

**不要：**
* 在混合现实，以确保用户拥有入和移出耳机熟悉的体验时太显著更改你的 UI。

### <a name="understand-the-app-model"></a>了解应用程序模型

[应用程序模型](app-model.md)的混合的现实设计为使用混合现实主页，许多应用程序一起居住的位置。 将此视为混合的现实等效于在桌面上，其中同时运行许多 2D 应用程序。 这会影响应用程序生命周期、 磁贴，和您的应用程序的其他主要功能。

### <a name="app-bar-and-back-button"></a>应用程序栏和后退按钮

使用其内容的顶部应用栏进行修饰二维视图。 应用栏有两个点的特定于应用的个性化设置：

**标题：** 将显示*displayname*与应用程序实例相关联的磁贴

**后退按钮：** 将引发*[BackRequested](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.backrequested.aspx)* 时按下事件。 通过控制后退按钮可见性 *[SystemNavigationManager.AppViewBackButtonVisibility](https://msdn.microsoft.com/library/windows/apps/windows.ui.core.systemnavigationmanager.aspx)*。

![应用栏 2D 应用视图中的用户界面](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*应用栏 2D 应用视图中的用户界面*

### <a name="test-your-2d-apps-design"></a>测试 2D 应用程序的设计

请务必测试该应用，请确保该文本是可读，以，这些按钮为目标，整体应用看上去正确。 你可以[测试](testing-your-app-on-hololens.md)桌面耳机、 HoloLens、 一个仿真程序或解析设置为 1280 x 720 使用触控设备上@150%。

## <a name="new-input-possibilities"></a>新的输入的可能性

HoloLens 使用高级的深度传感器，请参阅世界，并查看用户。 这样，如高级的手势[布隆](gestures.md#bloom)并[air 点击](gestures.md#air-tap)。 此外启用功能强大的麦克风[语音体验](voice-input.md)。

与桌面耳机，用户可以使用 motion 控制器以指向应用程序并采取措施。 他们还可以使用游戏手柄，指向其的视线移动的对象。

Windows 将负责所有这种复杂性适用于 UWP 应用的转换您[注视](gaze.md)，手势，语音和动作的输入控制器[指针事件](https://msdn.microsoft.com/library/windows/apps/mt404610#pointer_events)抽象出输入的机制。 例如，用户可能已完成-敲击用其一只手或动作在控制器上，请求选择触发器但 2D 应用程序无需知道其中原来的位置输入-只看到 2D 触摸屏输入按下时，像触摸屏上。

此处是到 HoloLens 使 UWP 应用时，应了解的输入的高级概念/方案：
* [注视](gaze.md)变为悬停事件，以便在意外触发菜单、 浮出控件或其他用户界面元素，只需通过在应用周围观望弹出。
* 视线移动不精确的鼠标输入。 使用适当调整大小的 HoloLens，类似于触摸功能的移动应用程序的命中的目标。 应用的边缘附近的小元素是特别难，若要与之交互。
* 用户必须切换输入的法从滚动到拖动到两个指平移。 如果您的应用程序专为触摸输入，请考虑确保任何主要功能锁定后面两个指平移。 如果是这样，请考虑让像按钮一样，可以启动两个指平移的替代输入的机制。 例如，地图应用程序可以放大具有两个手指平移而减号的加号，，旋转按钮以模拟与次单击之间的相同的缩放交互。

[语音输入](voice-input.md)是混合的现实体验的关键部分。 我们已启用所有语音在 Windows 10 中使用耳机时增强 Cortana Api。

## <a name="publish-and-maintain-your-universal-app"></a>发布和维护通用应用

启动并运行您的应用程序后，到将应用打包[将其提交到 Microsoft Store](submitting-an-app-to-the-microsoft-store.md)。

## <a name="see-also"></a>请参阅
* [应用程序模型](app-model.md)
* [Gaze](gaze.md)
* [手势](gestures.md)
* [运动控制器](motion-controllers.md)
* [Voice](voice-input.md)
* [提交到 Microsoft Store 应用](submitting-an-app-to-the-microsoft-store.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
