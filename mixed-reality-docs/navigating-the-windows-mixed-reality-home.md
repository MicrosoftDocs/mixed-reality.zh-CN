---
title: 导航 Windows Mixed Reality 主页
description: HoloLens 和 Windows 混合现实耳机共享一种用于启动、 放置，和操作应用程序和您的环境中的 3D 模型 （无论是物理还是数字） 的模式。 了解如何导航 Windows Mixed Reality 主页上这两种设备类型。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 命令行程序、 操作系统、 平台、 cliff 房屋房子、 主页、 环境、 开始、 开始菜单、 主菜单、 pin、 应用和启动应用，将应用程序，teleport、 移动、 导航
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593027"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>导航 Windows Mixed Reality 主页

就像 Windows PC 体验始于桌面、 Windows Mixed Reality 开头主页。 主 Windows Mixed Reality 利用理解和导航三维位置我们与生俱来的能力。 HoloLens，与您在家是物理空间。 沉浸式耳机，与您在家是一个虚拟位置。

您家也是在其中将使用开始菜单打开和放置应用程序和内容。 可以使用混合的现实内容填充您家并同时使用多个应用程序执行多任务。 在家中放置的内容继续保留在那里，即使您重新启动你的设备。

## <a name="start-menu"></a>“开始”菜单

![Microsoft HoloLens 上开始菜单](images/start-500px.png)

开始菜单包括：
* 系统信息 （网络状态、 电池百分比、 当前时间和卷）
* Cortana （沉浸式耳机，开始磁贴上; HoloLens，在顶部开始）
* 固定的应用
* 所有应用程序按钮 （加号）
* 照片和视频按钮[混合现实捕获](mixed-reality-capture.md)

通过选择加号或减号按钮，切换固定应用程序和所有应用之间视图。 若要打开在 HoloLens 上的开始菜单，请使用布隆手势。 在沉浸式头戴式耳机，在控制器上按 Windows 按钮。

## <a name="launching-apps"></a>启动应用程序

若要启动应用，选择在启动它。 开始菜单就会消失，并将在放置模式下，作为 2D 窗口中打开该应用程序或[三维模型](implementing-3d-app-launchers.md)。

若要运行该应用程序，你将需要然后将它放在您家中：
1. 使用你[注视](gaze.md)或控制器来定位应用程序所需的位置。 它将自动调整 （在大小和位置） 以符合其位置的空间。
2. 将使用敲击 (HoloLens) 或选择按钮 （沉浸式耳机） 此应用程序。 若要取消并移回开始菜单，请使用布隆手势或 Windows 按钮。

[2D 应用](building-2d-apps.md)，或创建的桌面、 移动、 Xbox 可进行修改以使用混合的现实沉浸式应用程序以运行[HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)。 沉浸式应用程序采用用户从主页和到的沉浸式体验。 使用布隆手势 (HoloLens) 或通过按其控制器 （沉浸式耳机） 上的 Windows 按钮，用户可开始返回。

此外可以通过应用应用 API 或通过 Cortana 启动应用。

![中的主 Windows Mixed Reality 应用](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>移动和调整应用程序

选择**调整**应用上栏以显示控制该移动的同时，小数位数和旋转的混合现实内容。 完成后，选择**完成**。

![调整模式 （蓝色帧） 中存储静态图像。 请注意应用栏 （顶端） 已更改为包括完成和删除按钮。](images/adjust-500px.png)

不同的应用程序可能在应用栏上的其他选项。 例如，具有 Microsoft Edge*滚动*，*拖动*，并*缩放*选项。 

![2D 上运行的应用 HoloLens 应用栏](images/holobar-500px.png)

**回**按钮导航回先前已查看屏幕的应用中。 它将停止您即将开始，已显示在应用中，并将导航到其他应用程序的体验。

## <a name="getting-around-your-home"></a>获取围绕你的主页

与**HoloLens**，可以逐步完成物理空间您家中移动。

与**沉浸式耳机**，您同样可以启动，然后在中您 playspace 虚拟世界中的类似区域内移动不同。 若要移动跨距离的增加，可用于摇杆在控制器上几乎遍历，也可以使用*teleportation*立即跳转距离的增加。

![中的主 Windows Mixed Reality Teleportation](images/teleportation-500px.png)

**到 teleport:**
1. 显示 teleportation 标线。
   * 使用[动作控制器](motion-controllers.md): 摇杆向前按住它在该位置。
   * 使用 Xbox 控制器： 前滚按下左的摇杆并保持它在该位置。
   * 使用鼠标： 按下右键单击鼠标按钮 (并使用鼠标滚轮旋转方向你想要面临时您 teleport)。
2. 将放置在要用于 teleport 标线。
   * 使用[动作控制器](motion-controllers.md)： 倾斜 （在其拿着摇杆前滚） 的控制器移动标线。
   * 使用 Xbox 控制器： 使用你[注视](gaze.md)移动标线。
   * 使用鼠标： 将鼠标移动标线移动。
3. 释放到 teleport 放置标线按钮。

**到几乎"引导:"**
* 使用[动作控制器](motion-controllers.md)： 单击向下该摇杆并保持状态，然后将摇杆移动方向你想要"引导"。
* 使用 Xbox 控制器： 单击向下的左的摇杆和保持状态，然后移摇杆方向你想要"引导"。

## <a name="immersive-headset-input-support"></a>沉浸式头戴式输入的支持

[Windows Mixed Reality 沉浸式耳机](immersive-headset-hardware-details.md)支持使用多个输入的类型进行导航的主 Windows Mixed Reality。 HoloLens 不用于导航，支持附件的输入，因为以物理方式奔波，请参阅您的环境。 但却提供了 HoloLens[支持输入](hardware-accessories.md)用来与应用交互。

### <a name="motion-controllers"></a>运动控制器

最佳 Windows Mixed Reality 体验不会与 Windows Mixed Reality[动作控制器](motion-controllers.md)在您的头戴式-没有外部照相机或所需的标记中使用只是传感器的支持 6-自由度跟踪 ！

即将推出的导航命令。

### <a name="gamepad"></a>游戏板
* **左的摇杆：**
  * 按下并保持左的摇杆向前弹出[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)标线。
  * 点击 left、 right 摇杆或备份继续向左、 右、 或小的增量备份。
  * 单击向下的左的摇杆和保持状态，然后到所需的方向移动摇杆[几乎遍历。](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* 点击**右摇杆**左或向右旋转所面临的 45 度的方向。
* 按下**A**按钮执行 select 和的行为类似于[敲击](gestures.md#air-tap)手势。
* 按下**指南**按钮将显示[开始菜单](navigating-the-windows-mixed-reality-home.md#start-menu)和的行为类似于[布隆](gestures.md#bloom)手势。
* 按下**左侧和右侧触发器**允许您放大和缩小，在家里的交互与 2D 桌面应用程序。

### <a name="keyboard-and-mouse"></a>键盘和鼠标

**注意：** 使用**Windows 键 + Y**切换之间控制你的电脑的桌面和 Windows Mixed Reality 主鼠标。

在主 Windows Mixed Reality:
* 按下**左键单击**鼠标按钮执行 select 和的行为类似于[敲击](gestures.md#air-tap)手势。
* 持有**右击**鼠标按钮将显示[teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)标线。
* 按下**Windows**引出了键盘上的键[开始菜单](navigating-the-windows-mixed-reality-home.md#start-menu)和的行为类似于[布隆](gestures.md#bloom)手势。
* 时[观望](gaze.md)在 2D 桌面应用中，你可以**左击**若要选择，**右键单击**打开上下文菜单，并使用**滚轮**滚动 （在你的电脑的桌面上就像一样）。

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) PC 和手机上就像是在 Windows Mixed Reality 应用个人助理。 HoloLens 有内置麦克风，但令人着迷的耳机可能需要额外的硬件。 使用 Cortana 以打开应用，重启设备，联机查找内容和的详细信息。 开发人员也可以选择[集成 Cortana](https://dev.windows.com/cortana)到其体验。

语音命令还可用于避免您家出现。 例如，指向上一个按钮 (使用[注视](gaze.md)或控制器，具体取决于设备)，说"Select"。 "转到主页"、"大，""较小，"其他语音命令，包括"关闭"和"面临着我。"

## <a name="store-settings-and-system-apps"></a>应用商店、 设置和系统应用

Windows Mixed Reality 有许多内置的应用程序，例如：
* **Microsoft Store**若要获取应用程序和游戏
* **反馈中心**要提交有关系统和系统应用程序的反馈
* **设置**配置系统设置 ([包括网络](connecting-to-wi-fi-on-hololens.md)和系统更新)
* **Microsoft Edge**浏览网站
* **照片**查看和共享的照片和视频
* **校准**(仅 HoloLens) 调整到当前用户的 HoloLens 体验
* **了解手势**(HoloLens) 或**了解混合现实**（沉浸式耳机），了解如何使用你的设备
* **三维查看器**来修饰混合的现实内容与您的世界
* **混合现实门户**（桌面），用于设置和管理您的沉浸式头戴式和流式处理在视图中的其他人看到耳机的实时预览。
* **电影和电视节目**对于查看 360 视频的最新电影和电视节目显示
* **Cortana**虽然虚拟助理的所有需要
* **桌面**（沉浸式耳机） 用于查看在沉浸式头戴式桌面监视器
* **文件资源管理器**访问文件和文件夹位于你的设备

## <a name="see-also"></a>请参阅
* [应用程序视图](app-views.md)
* [运动控制器](motion-controllers.md)
* [硬件附件](hardware-accessories.md)
* [HoloLens 的环境注意事项](environment-considerations-for-hololens.md)
* [实现的 3D 应用程序启动器](implementing-3d-app-launchers.md)
* [在 Windows Mixed Reality 主页中创建用于 3D 模型](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
