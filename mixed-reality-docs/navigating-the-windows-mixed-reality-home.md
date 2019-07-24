---
title: 导航 Windows Mixed Reality 主页
description: HoloLens 和 Windows Mixed Reality 耳机共享了一个用于在环境中启动、放置和操作应用和3D 模型的模式 (无论是物理的还是数字的)。 了解如何在这两种设备类型上浏览 Windows Mixed Reality 主页。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: shell, os, 平台, cliff 房子, 房子, home, 环境, 开始, 开始菜单, 主页菜单, pin, 应用, 启动应用, 放置应用, 传送, 移动, 导航
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525173"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>导航 Windows Mixed Reality 主页

正如 Windows PC 体验从桌面开始一样, Windows Mixed Reality 从家里开始。 Windows Mixed Reality 主页利用我们原始的能力来理解并浏览三维位置。 通过 HoloLens, 你的家庭是你的物理空间。 使用沉浸式耳机, 您的家庭是一个虚拟位置。

你还可以使用 "开始" 菜单打开和放置应用和内容。 您可以使用混合现实内容和多个应用程序同时使用多个应用程序。 即使您重新启动设备, 您在家庭中放置的东西也会保留在那里。

## <a name="start-menu"></a>“开始”菜单

![Microsoft HoloLens 上的 "开始" 菜单](images/start-500px.png)

"开始" 菜单包括:
* 系统信息 (网络状态、电池百分比、当前时间和卷)
* Cortana (在沉浸式耳机上, 在 "开始" 磁贴上, 在 HoloLens 上, 在 "开始" 的顶部)
* 固定应用
* "所有应用" 按钮 (加号)
* [混合现实捕获](mixed-reality-capture.md)的照片和视频按钮

通过选择加号或减号按钮, 在固定应用程序和所有应用程序视图之间切换。 若要在 HoloLens 上打开 "开始" 菜单, 请使用布隆手势。 在沉浸式耳机上, 按下控制器上的 Windows 按钮。

## <a name="launching-apps"></a>正在启动应用

若要启动应用, 请在 "开始" 上选择它。 "开始" 菜单将消失, 应用将在放置模式下打开, 如2D 窗口或[3d 模型](implementing-3d-app-launchers.md)。

若要运行该应用, 你需要将其放在家里:
1. 使用[注视](gaze.md)或控制器将应用定位到所需的位置。 它将自动调整 (大小和位置) 以符合放置它的空间。
2. 使用 "空中点击" (HoloLens) 或 "选择" 按钮 (沉浸式耳机) 放置应用。 若要取消并返回 "开始" 菜单, 请使用布隆手势或 Windows 按钮。

可以使用[HOLOGRAPHICSPACE API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)将为桌面、移动或 Xbox 创建的[2d 应用](building-2d-apps.md)修改为作为混合现实沉浸式应用运行。 沉浸式应用使用户离开家里, 并进入沉浸式体验。 用户可以返回 home with 布隆手势 (HoloLens), 也可以通过在控制器 (沉浸式耳机) 上按 Windows 按钮。

还可以通过应用程序到应用程序 API 或通过 Cortana 来启动应用。

![Windows Mixed Reality 主页中的应用](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>移动和调整应用

选择应用栏上的 "**调整**" 以显示移动、缩放和旋转混合现实内容的控件。 完成后, 请选择 "**完成**"。

![调整模式下的存储石板 (蓝色帧)。 请注意, 应用栏 (顶部) 已更改为包含 "完成" 和 "删除" 按钮。](images/adjust-500px.png)

不同的应用可能在应用栏上有其他选项。 例如, Microsoft Edge 具有*滚动*、*拖动*和*缩放*选项。 

![在 HoloLens 上运行的2D 应用的应用栏](images/holobar-500px.png)

"**后退**" 按钮导航回到应用中以前查看过的屏幕。 当你到达已在应用中显示的体验开始时, 它将停止, 并且不会导航到其他应用。

## <a name="getting-around-your-home"></a>围绕你的家庭

使用**HoloLens**, 可以在物理空间间移动, 在家里移动。

使用**沉浸式耳机**, 你可以类似地在 playspace 中进行浏览, 在虚拟世界中的类似区域内移动。 若要在更远的距离间移动, 可以使用控制器上的操纵杆来几乎 "走到", 也可以使用*teleportation*立即跳转到更长的距离。

![Windows Mixed Reality 主页中的 Teleportation](images/teleportation-500px.png)

**若要传送:**
1. 打开 teleportation reticle。
   * 使用[运动控制器](motion-controllers.md): 向前按操纵杆并将其放在该位置。
   * 使用 Xbox 控制器: 向前按左操纵杆, 并将其放在该位置。
   * 使用鼠标: 按住右键单击鼠标按钮 (并在传送时使用滚轮来旋转要面对的方向)。
2. 将 reticle 放在要传送的位置。
   * 使用[运动控制器](motion-controllers.md): 倾斜控制器 (您在其上持有操纵杆) 以移动 reticle。
   * 使用 Xbox 控制器: 使用[注视](gaze.md)移动 reticle。
   * 使用鼠标: 移动鼠标移动 reticle。
3. 释放按钮以传送 reticle 的位置。

**到真正的 "行走:"**
* 使用[运动控制器](motion-controllers.md): 单击操纵杆并按下, 并在要 "走进" 方向上移动操纵杆。
* 使用 Xbox 控制器: 单击左侧操纵杆并按下, 并在要 "走" 方向上移动操纵杆。

## <a name="immersive-headset-input-support"></a>沉浸式耳机输入支持

[Windows Mixed reality 沉浸式耳机](immersive-headset-hardware-details.md)支持用于导航 Windows Mixed reality 主页的多种输入类型。 HoloLens 不支持用于导航的附件输入, 因为您可以物理方式浏览并查看您的环境。 但是, HoloLens 支持与应用进行交互的[输入](hardware-accessories.md)。

### <a name="motion-controllers"></a>运动控制器

最佳的 Windows Mixed reality 体验将使用 Windows Mixed Reality[运动控制器](motion-controllers.md), 该控制器仅使用耳机中的传感器支持6度自由跟踪-无需外部照相机或标记!

即将推出导航命令。

### <a name="gamepad"></a>游戏板
* **左操纵杆:**
  * 按住左操纵杆, 使[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle。
  * 向左、向右或向后移动操纵杆, 以较小的增量向左、向右或向后移动。
  * 单击左侧操纵杆并按下, 并按所需的方式移动操纵杆, 使其以[实际](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)的方向移动。
* 向左或向右点击**右操纵杆**, 以将你的方向旋转45度。
* 按下**按钮将**执行 "选择", 其作用类似于 "[空中点击](gestures.md#air-tap)" 手势。
* 按 "**指南**" 按钮将显示 "[开始" 菜单](navigating-the-windows-mixed-reality-home.md#start-menu), 并类似于 "[布隆](gestures.md#bloom)" 手势。
* 按**左和右触发器**可以放大和缩小要在家里交互的2d 桌面应用程序。

### <a name="keyboard-and-mouse"></a>键盘和鼠标

**注意：** 使用**Windows 键 + Y**在控制 PC 桌面和 Windows Mixed Reality 主页之间切换鼠标。

在 Windows Mixed Reality 主页中:
* 按住鼠标**左键**并执行选择操作, 其作用类似于 "[空中点击](gestures.md#air-tap)" 笔势。
* 按住**右键单击**鼠标按钮将打开[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle。
* 按键盘上的**Windows**键打开 "开始"[菜单](navigating-the-windows-mixed-reality-home.md#start-menu), 并与[布隆](gestures.md#bloom)手势类似。
* 当[gazing](gaze.md)在2d 桌面应用程序中时, 可以**单击**以选择,**右键单击**以打开上下文菜单, 然后使用滚轮滚动 (就像您的 PC 桌面上一样)。

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana)是 Windows Mixed Reality 的个人助手, 就像在电脑和手机上一样。 HoloLens 有内置麦克风, 但沉浸式耳机可能需要额外的硬件。 使用 Cortana 打开应用、重新启动设备、联机查找, 等等。 开发人员也可以选择将[Cortana 集成](https://dev.windows.com/cortana)到其体验中。

你还可以使用语音命令来浏览你的主页。 例如, 指向某个按钮 (使用 "[注视](gaze.md)" 或 "控制器", 具体取决于设备), 然后说 "选择"。 其他语音命令包括 "转到主页"、"放大"、"较小"、"关闭" 和 "面部我"。

## <a name="store-settings-and-system-apps"></a>存储、设置和系统应用

Windows Mixed Reality 包含许多内置应用, 例如:
* **Microsoft Store**获取应用和游戏
* 提交有关系统和系统应用的反馈的**反馈中心**
* 用于配置系统设置的**设置**([包括网络](connecting-to-wi-fi-on-hololens.md)和系统更新)
* **Microsoft Edge**浏览网站
* 查看并共享照片和视频的**照片**
* **校准**(仅限 HoloLens) 用于调整当前用户的 HoloLens 体验
* **学习手势**(HoloLens) 或**了解混合现实**(沉浸式耳机) 以了解如何使用你的设备
* **三维查看器**, 可在全球范围内装饰混合现实内容
* **混合现实门户**(桌面) 设置和管理沉浸式头戴式耳机并流式传输耳机上视图的实时预览, 供其他人查看。
* 观看360视频和最新电影和电视节目的**电影和电视**节目
* 所有虚拟助手需求的**Cortana**
* **桌面**(沉浸式耳机), 用于在沉浸式耳机中查看桌面监视器
* **文件资源管理器**访问设备上的文件和文件夹

## <a name="see-also"></a>请参阅
* [应用视图](app-views.md)
* [运动控制器](motion-controllers.md)
* [硬件配件](hardware-accessories.md)
* [HoloLens 的环境注意事项](environment-considerations-for-hololens.md)
* [实现三维应用启动器](implementing-3d-app-launchers.md)
* [创建用于 Windows Mixed Reality 主页的3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
