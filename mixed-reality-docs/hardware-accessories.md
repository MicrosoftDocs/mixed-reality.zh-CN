---
title: 硬件附件
description: 描述可与 HoloLens 和 Windows Mixed Reality 一起使用的附件类型, 以及如何对其进行设置。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 操作说明, 附件, 蓝牙, bt, 控制器, 游戏板, clicker, xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526608"
---
# <a name="hardware-accessories"></a>硬件附件

Windows Mixed Reality 设备支持附件。 你将使用蓝牙将支持的附件与 HoloLens 配对, 同时, 你可以使用蓝牙或 USB 将受支持的附件通过其连接到的 PC 与沉浸式耳机配对。

使用 HoloLens 的附件的两种常见方案是, 使用 "air" 手势和虚拟键盘的替代方案。 为此, 最常见的两个附件是**HoloLens Clicker**和**蓝牙键盘**。 Microsoft HoloLens 包含蓝牙4.1 无线功能, 并支持[蓝牙 HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29)和[蓝牙 GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29)配置文件。

Windows Mixed Reality 沉浸式耳机需要用于输入的附件, 看看看[不到](gaze.md)[声音](voice-input.md)。 支持附件包括 **键盘和鼠标** ， **游戏手柄** ，并 **[动作控制器](motion-controllers.md)** 。

## <a name="pairing-bluetooth-accessories"></a>配对蓝牙附件

将蓝牙外设与 Microsoft HoloLens 配对类似于将蓝牙外围设备与 Windows 10 桌面或移动设备配对:
1. 从 "开始" 菜单中打开 "**设置**" 应用
2. 中转到**设备**
3. 如果蓝牙无线电设备处于关闭状态, 请使用滑块开关
4. 将蓝牙设备置于配对模式下。 这不同于设备。 在大多数 Bluetooth 设备上, 通过按住并按住一个或多个按钮来完成此操作。
5. 等待设备的名称显示在蓝牙设备列表中。 完成后, 选择设备, 然后选择 "**对**" 按钮。 如果附近有许多蓝牙设备, 可能需要滚动到蓝牙设备列表的底部, 才能查看正在尝试配对的设备。
6. 将蓝牙外设与输入功能配对时 (例如:蓝牙键盘), 可能会显示一个6位数或8位数的 pin 码。 请确保在外围设备上输入该 pin, 并按 enter 完成与 Microsoft HoloLens 的配对。

## <a name="motion-controllers"></a>运动控制器

沉浸式耳机支持 Windows Mixed Reality[运动控制器](motion-controllers.md), 但不支持 HoloLens。 这些控制器使用沉浸式头戴显示空间中的传感器提供精确而快速的移动性跟踪, 这意味着无需在空间中的墙壁上安装硬件。 每个控制器都具有几个输入方法。

![Windows Mixed Reality 运动控制器](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

HoloLens Clicker 是专门为 HoloLens 构建的第一个外围设备, 并随附于 HoloLens 开发版。 使用 HoloLens Clicker, 用户可以使用最小的手动运动来进行单击和滚动, 以代替空中点击手势。 它不是所有[手势](gestures.md)的替代方法。 例如,[布隆](gestures.md#bloom)和重[设大小或移动](gestures.md#composite-gestures)手势使用手运动。 HoloLens clicker 是一个带有简单按钮的方向传感器设备。 它使用蓝牙低功耗 (BTLE) 连接到 HoloLens。

![HoloLens Clicker](images/hololens-clicker-500px.jpg)

若要选择一个[全息](hologram.md)图, 请在其上注视, 然后单击。 对于此操作, clicker 的方向并不重要。 若要滚动或平移, 请单击并按住, 然后将 Clicker 向上/向下或向左/右旋转。 滚动时, 您的速度最快, 只需 +/-15 °的手腕旋转。 移动更多将无法更快地滚动。

Clicker 中有两个 Led:
* 白色 LED 指示设备是配对 (闪烁) 还是充电 (固态)
* 琥珀色 LED 表明设备电池电量低 (闪烁) 或发生故障 (固态)

您可以预计2周或更多的常规使用情况 (即, 墙壁充电器上2-3 小时)。 当电池电量不足时, 如果按下按钮或将其从睡眠状态唤醒, 则琥珀色 LED 将在5秒内闪烁10次。 如果 Clicker 处于电池电量严重不足的情况下, 琥珀色 LED 将在5秒内快闪烁一次。

## <a name="bluetooth-keyboards"></a>蓝牙键盘

使用简体中文的蓝牙键盘可以在任何可使用全息键盘的地方配对和使用。 获取质量键盘会产生差别, 因此建议使用[Microsoft 通用折叠键盘](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001)或[Microsoft Designer 蓝牙桌面](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)。

## <a name="bluetooth-gamepads"></a>蓝牙 gamepads

可以将控制器与专门启用游戏板支持的应用和游戏配合使用。 Gamepads 不能用于控制 HoloLens 用户界面。

Xbox one 随附的 xbox 无线控制器或作为 Xbox One 功能的 "销售" 功能的蓝牙连接, 使其能够与 HoloLens 和沉浸式耳机一起使用。 [必须先更新](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter)Xbox 无线控制器, 然后才能将其与 HoloLens 配合使用。

其他品牌的蓝牙 gamepads 可能适用于 Windows Mixed Reality 设备, 但支持会因应用程序而异。

## <a name="other-bluetooth-accessories"></a>其他蓝牙附件

只要外围设备支持蓝牙 HID 或 GATT 配置文件, 它就能够与 HoloLens 配对。 除键盘、鼠标和 HoloLens Clicker 以外的其他蓝牙 HID 和 GATT 设备可能需要 Microsoft HoloLens 上的配套应用程序才能完全正常运行。

不受支持的外设包括:
* 不支持蓝牙音频配置文件中的外围设备。
* 诸如扬声器和耳机等蓝牙音频设备可能会在 "设置" 应用程序中显示为可用, 但不支持将其与 Microsoft HoloLens 一起用作音频终结点。
* 支持蓝牙功能的手机和电脑不能配对并用于文件传输。

## <a name="unpairing-a-bluetooth-peripheral"></a>取消配对蓝牙外围设备
1. 从 "开始" 菜单中打开 "**设置**" 应用
2. 中转到**设备**
3. 如果蓝牙无线电已关闭, 请打开它
4. 在可用的蓝牙设备列表中找到你的设备
5. 从列表中选择你的设备, 然后选择 "**删除**" 按钮

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>在 Microsoft HoloLens 上禁用蓝牙

这会关闭蓝牙无线电的 RF 组件, 并在 Microsoft HoloLens 上禁用所有蓝牙功能。
1. 从 "开始" 菜单中打开 "**设置**" 应用
2. 中转到**设备**
3. 将蓝牙的滑块开关移动到关闭位置
