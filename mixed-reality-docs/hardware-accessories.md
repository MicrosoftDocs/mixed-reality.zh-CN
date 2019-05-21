---
title: 硬件附件
description: 介绍可用于 HoloLens 和 Windows Mixed Reality，以及如何设置它们的附件的类型。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 操作说明、 附件、 蓝牙、 bt、 控制器、 游戏板、 clicker、 xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592995"
---
# <a name="hardware-accessories"></a>硬件附件

Windows Mixed Reality 设备支持附件。 将配对到 HoloLens 使用蓝牙，虽然可以使用 Bluetooth 或 USB 进行配对支持对通过连接到 PC 沉浸式头戴式附件支持附件。

使用附件和 HoloLens 的两种常见方案是因为以无线方式的点击手势和虚拟键盘。 为此，两个最常见的附件都**HoloLens Clicker**并**蓝牙键盘**。 Microsoft HoloLens 包括蓝牙 4.1 广播并支持[HID 蓝牙](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29)并[蓝牙 GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29)配置文件。

Windows Mixed Reality 沉浸式耳机附件需要对超出的输入[注视](gaze.md)并[语音](voice-input.md)。 支持附件包括 **键盘和鼠标** ， **游戏手柄** ，并 **[动作控制器](motion-controllers.md)** 。

## <a name="pairing-bluetooth-accessories"></a>配对的蓝牙附件

使用 Microsoft HoloLens 外围 Bluetooth 的配对是类似于配对蓝牙外围设备与 Windows 10 桌面或移动设备：
1. 从开始菜单中，打开**设置**应用
2. 转到**设备**
3. 如果它处于关闭状态使用滑块开关，打开蓝牙无线
4. 将您的 Bluetooth 设备放在配对模式。 此值变化从设备到设备。 在大多数蓝牙设备上这可通过双击或按住一个或多个按钮。
5. 等待设备的蓝牙设备列表中显示的名称。 当它没有、 选择的设备然后选择**对**按钮。 如果您有很多您附近的蓝牙设备可能需要滚动到要看到想要对该设备的蓝牙设备列表的底部。
6. 如果配对使用蓝牙外围设备输入功能 (例如：蓝牙键盘），可能会显示一个 6 数字或 8 位数的 pin。 务必外围设备上键入该 pin，然后按 enter 与 Microsoft HoloLens 的完整配对。

## <a name="motion-controllers"></a>运动控制器

Windows Mixed Reality[动作控制器](motion-controllers.md)受沉浸式耳机，而不是 HoloLens。 这些控制器提供了在沉浸式头戴式耳机，这意味着无需安装在你的空间中的墙上的硬件中使用传感器在字段的视图中移动的精确且高度可响应的跟踪。 每个控制器特色几种方法的输入。

![Windows Mixed Reality 运动控制器](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

HoloLens Clicker 是专为 HoloLens 生成的第一个外围设备，包含与 HoloLens 开发版本。 HoloLens Clicker 允许用户单击，然后使用最少手动移动滚动以替换-敲击手势。 它不是所有的替代[手势](gestures.md)。 例如，[布隆](gestures.md#bloom)并[调整大小或移动](gestures.md#composite-gestures)手势使用手动作。 HoloLens clicker 是方向传感器设备使用简单的按钮。 它连接到使用蓝牙低能耗 (BTLE) HoloLens。

![HoloLens Clicker](images/hololens-clicker-500px.jpg)

若要选择[全息图](hologram.md)，注视，，然后单击。 此操作，clicker 的方向并不重要。 若要向下滚动或平移，单击并按住，然后向上/向下或左/向右旋转 Clicker。 在滚动时，可以实现与只需少量的 + /-15 ° 手腕旋转速度最快的速度。 移动的详细信息不会发生滚动任何速度更快。

有两个 Led Clicker 内：
* 白色 LED 指示设备是否配对 （闪烁） 或计费 （实体）
* 琥珀色 LED 指示该设备已 （闪烁） 的电池电量不足或已发生故障 （实体）

您可以预计 2 周或多个常规用途上完全充电 （即，在墙上充电器 2 到 3 个小时）。 当电池电量低，琥珀色 LED 将闪烁在 5 秒内 10 次，如果按下按钮或从睡眠状态唤醒。 琥珀色 LED 将更快地闪烁 5 秒时间段如果你 Clicker 处于电池电量严重不足模式。

## <a name="bluetooth-keyboards"></a>蓝牙键盘

英语语言 Qwerty 蓝牙键盘可以进行配对，并可以使用 holographic 键盘的任何位置使用。 获取质量键盘一个差异，因此我们建议[Microsoft 通用折叠式键盘](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001)或[Microsoft 设计器蓝牙桌面](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)。

## <a name="bluetooth-gamepads"></a>蓝牙游戏板

与应用程序和游戏，特别是启用游戏板支持，可以使用一个控制器。 游戏板不能用于控制 HoloLens 用户界面。

附带一个 S 的 Xbox 或作为附件 Xbox 一个 S 功能蓝牙连接，使他们能够与 HoloLens 和沉浸式耳机一起销售的 Xbox 无线控制器。 Xbox 无线控制器[必须更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)用于 HoloLens 之前。

其他不同品牌的蓝牙游戏板可能会使用 Windows Mixed Reality 设备，但支持将因应用程序而异。

## <a name="other-bluetooth-accessories"></a>其他蓝牙附件

只要外围设备支持蓝牙 HID 或 GATT 配置文件，它将能够与 HoloLens 配对。 除了键盘、 鼠标和 HoloLens Clicker 其他蓝牙 HID 和 GATT 设备可能需要的助手应用程序在 Microsoft HoloLens 上完全正常工作。

不支持外围设备包括：
* 不支持蓝牙音频配置文件中的外围设备。
* 蓝牙音频设备，例如发言人和耳机可能会出现在设置应用中，为可用，但不是支持要与 Microsoft HoloLens 用作音频终结点。
* 已启用蓝牙的手机和电脑不支持配对和用于文件传输。

## <a name="unpairing-a-bluetooth-peripheral"></a>取消配对蓝牙外围设备
1. 从开始菜单中，打开**设置**应用
2. 转到**设备**
3. 如果它处于关闭状态，打开蓝牙无线
4. 可用的蓝牙设备的列表中找到你的设备
5. 从列表中选择你的设备，然后选择**删除**按钮

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Microsoft HoloLens 上禁用蓝牙

这将关闭蓝牙无线射频组件并禁用所有 Microsoft HoloLens 上的蓝牙功能。
1. 从开始菜单中，打开**设置**应用
2. 转到**设备**
3. 将滑块开关 Bluetooth 的移动到 OFF 位置
