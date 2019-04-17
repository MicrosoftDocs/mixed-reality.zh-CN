---
title: 高级的 HoloLens 仿真程序和混合现实模拟器输入
description: 有关使用键盘、 鼠标和 X 附带的控制器来模拟输入内容的 HoloLens 仿真程序和 Windows Mixed Reality 模拟器的详细的说明。
author: ChimeraScorn
ms.author: cwhite
ms.date: 02/24/2018
ms.topic: article
keywords: HoloLens，仿真程序中，模拟，Windows 混合现实
ms.openlocfilehash: 59bea340a2ecdd2d65481c9ace4ab3f0bf15bc6f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59590164"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>高级的 HoloLens 仿真程序和混合现实模拟器输入

大多数仿真程序用户只需使用有关的基本输入的控件[HoloLens 模拟器](using-the-hololens-emulator.md#basic-emulator-input)或[Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md#basic-simulator-input)。 下面的详细信息适用于高级用户发现需要模拟更复杂类型的输入。

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。

## <a name="concepts"></a>概念

若要开始控制虚拟输入到 HoloLens 仿真程序和 Windows Mixed Reality 模拟器，你首先应了解几个概念。

动作是指控制和更改的位置和方向的场景中的某些内容。 对于目标可控制对象，动作控制使用旋转和平移 （运动） 沿三个轴。
* **偏航角**:打开左侧或右侧。
* **间距**:向上或向下打开。
* **回滚**:将鼠标移到并行。
* **X**:左或向右移动。
* **Y**:上移或下移。
* **Z**:向前或向后移动。

[手势](gestures.md)和动作控制器输入紧密映射到如何在物理设备：
* **操作**:这模拟按下 thumb 到食指或拉取操作按钮在控制器上的操作。 例如，操作输入可用于模拟-敲击手势，滚动到的内容，再按下并保持到。
* **[布隆](gestures.md#bloom)或主页**:若要返回到命令行程序以及执行系统操作使用控制器的主页按钮或 HoloLens 百花齐放手势。

手具有丰富 reprresentation HoloLens V2 中。  除了跟踪/未被跟踪，并可用于推动手势外，手现在具有一个明确的主干模型调整到其大小和公开给开发人员。  这带来了 20 跟踪的点上每个指针。  
* **联合**:一个给定跟踪手的形状的 20 个跟踪位置。 这将产生一个点是与之关联的 3d 空间。
* **会带来**:所有跟踪手的形状的连接的完整集合。 在此期间，这是 20 关节的集合。 

在此期间，我们不公开每个联合位置单独通过仿真程序用户界面的直接的控制。 但您将其设置通过模拟 API。 相反，我们有一组有用的代表性带来，仿真程序可用于切换。

此外可以控制模拟的传感器输入状态：
* **重置**:这将为其默认值来返回所有模拟的传感器。
* **跟踪**:循环浏览位置跟踪模式。 这包括：
  * **默认**：操作系统选择最佳的跟踪模式基于对系统进行的请求。
   * **方向**:强制仅限方向的跟踪，而不考虑对系统进行的请求。
   * **位置**:强制位置跟踪，而不考虑对系统进行的请求。

## <a name="types-of-input"></a>类型的输入

下表显示了每个类型如何的输入映射到键盘、 鼠标和 Xbox 控制器。 每个类型具有不同的映射，具体取决于的输入的控件模式;在本文档后面提供的输入的控件模式的详细信息。

|  |  键盘 |  鼠标 |  Xbox 控制器 | 
|----------|----------|----------|----------|
|  Yaw |  左 / 右箭头 |  向左 / 向右拖动 |  右摇杆左 / 右 | 
|  俯仰 |  向上/向下箭头 |  向上 / 向下拖动 |  右摇杆向上 / 向下 | 
|  Roll |  Q / E |  |  DPad 左 / 右 | 
|  X |  A / D |  |  左的摇杆左 / 右 | 
|  Y |  向上翻页/向下翻页 |  |  DPad 向上 / 向下 | 
|  Z |  W / S |  |  左的摇杆向上 / 向下 | 
|  操作 |  Enter 或空格键 |  右侧的按钮 |  一个按钮或任一触发器 | 
|  布隆 |  F2 或 Windows 键 （Windows 密钥仅适用于 HoloLens 仿真程序之前） |  |  B 按钮 | 
|  控制器手柄按钮 |  G (Windows Mixed Reality 仅模拟器) |  |  | 
|  控制器菜单按钮 |  M (Windows Mixed Reality 仅模拟器) |  |  | 
|  控制器触摸板进行触摸 |  U (Windows Mixed Reality 仅模拟器) |  |  | 
|  控制器触摸板，请按 |  P (Windows Mixed Reality 仅模拟器) |  |  | 
|  设置手动姿势 | 7、 8、 9 或 0 |  |  |
|  Reset |  Esc 键 |  |  “开始”按钮 | 
|  跟踪 |  T 或 F3 |  |  X 按钮 | 


注意：仅 Windows Mixed Reality 模拟器，在控制器按钮可以是已定位到一只手或另一个使用手形图标面向修饰符。

## <a name="targeting"></a>定位 

某些上述输入概念独立存在其自身。  操作、 布隆、 重置和跟踪是完整的概念、 不需要和不受影响的面向任何其他修饰符。  但是，剩余的概念可以应用于多个目标之一。 我们引入了方法来指定哪些适用命令应该应用到的目标。  在所有情况下，则可以通过 UI 或通过键盘，按下，该对象传递给 targtet 指定。  在某些情况下，还有可能直接指定与 xbox 控制器。 

下表描述为目标，以及每个激活的方法的选项。

| 对象 | 键盘修饰符 | 控制器修饰符 | 仿真程序 UI 修饰符 |
|----------|----------|----------|----------|
| 正文 | <default> | <default> | <default> |
| Head | 保留 H | <None available> | 在 UI 中的头图钉 |
| 左侧显示/控制器 | 左 Alt 按钮 | 左即时权限提升按钮 | 左侧显示图钉 | 
| 右侧/控制器 | 右侧的 Alt 按钮 | 右即时权限提升按钮 | 右侧图钉 |
| 眼睛 | 保留 Y | <No contoller modifier available> | 眼睛图钉 |
  
下表显示了每个目标修饰符如何映射每个核心移动输入概念

|  默认值 （主体） |  手动/控制器 (按住 alt / 承担) |  Head （按住 H）  |  眼睛 （按住 Y） |
|----------|----------|----------|----------|
|  Yaw |  左 / 右打开正文 |  左 / 右移动手 |  左 / 右打开头 | 关注的视线移动看起来左/右 |
|  俯仰 |  向上 / 向下打开头 |  手上移 / 下移 |  向上 / 向下打开头 | 关注的视线移动看起来向上/向下 | 
|  Roll |  左 / 右滚动头 |  |  左 / 右滚动头 | （无操作） |
|  X |  幻灯片正文左 / 右 |  左 / 右移动手/控制器 |  左 / 右打开头 | （无操作） |
|  Y |  向上 / 向下移动正文 |  手动/控制器上移 / 下移 |  向上 / 向下打开头 | （无操作） |
|  Z |  将正文向前 / 向后移动 |  将手动/控制器向前 / 向后移动 |  向上 / 向下打开头 | （无操作） |
 
注意：仅 Windows Mixed Reality 模拟器，在控制器按钮可以是已定位到一只手或另一个使用手形图标面向修饰符。 同样，在 HoloLens 只能在模拟器，明确的手姿势可以是已定位到一只手或其他使用手修饰符。 
 
## <a name="controlling-an-app"></a>控制应用

本文介绍了一整套的输入的类型和 HoloLens 仿真程序和 Windows Mixed Reality 模拟器中可用的输入的模式。 对于日常使用，建议使用以下一组控件：

|  操作 |  键盘和鼠标 |  控制器 | 
|----------|----------|----------|
|  正文 X |  A / D |  左的摇杆左 / 右 | 
|  正文 Y |  向上翻页/向下翻页 |  DPad 向上 / 向下 | 
|  正文 Z |  W / S |  左的摇杆向上 / 向下 | 
|  正文偏航 |  拖动鼠标左 / 右 |  右摇杆左 / 右 | 
|  Head 偏航角 |  H 并拖动鼠标向左 / 右 |  （在键盘） H + 右摇杆左 / 右 | 
|  Head 间距 |  向上 / 向下拖动鼠标 |  右摇杆向上 / 向下 | 
|  Head 回滚 |  Q / E |  DPad 左 / 右 | 
|  手 X |  按住 alt 并拖动鼠标向左 / 右 |  即时权限提升 + 右摇杆左 / 右 | 
|  手 Y |  按住 alt 并拖动鼠标向上 / 向下 |  即时权限提升 + 右摇杆向上 / 向下 | 
|  手 Z |  Alt + W / S |  即时权限提升 + 左的摇杆向上 / 向下 | 
|  操作 |  鼠标右按钮 |  触发器 | 
|  百花齐放 /home |  F2 或 Windows 键 （Windows 键是仅为 HoloLens 仿真程序） |  B 按钮 | 
|  Reset |  退出 |  “开始”按钮 | 
|  跟踪 |  T |  X 按钮 | 
|  滚动 |  Alt + 向右键鼠标按钮 + 向上 / 向下拖动鼠标 |  即时权限提升 + 触发器 + 右摇杆向上 / 向下 | 

## <a name="see-also"></a>请参阅
* [安装工具](install-the-tools.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [使用 Windows Mixed Reality 模拟器](using-the-windows-mixed-reality-simulator.md)
