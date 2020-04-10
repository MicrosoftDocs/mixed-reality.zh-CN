---
title: 使用 Windows Mixed Reality 模拟器
description: 使用 Windows Mixed Reality 模拟器，无需 Windows Mixed Reality 沉浸式耳机即可在电脑上测试混合现实应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality，模拟器，测试
ms.openlocfilehash: 686cac4e9ab4b3354767e22cd87d37ffbb508dea
ms.sourcegitcommit: 37816514b8fe20669c487774b86e80ec08edcadf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2020
ms.locfileid: "81003293"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>使用 Windows Mixed Reality 模拟器

使用 Windows Mixed Reality 模拟器，无需 Windows Mixed Reality 沉浸式耳机即可在电脑上测试混合现实应用。 它从 Windows 10 创意者更新开始可用。 模拟器与[HoloLens 模拟器](using-the-hololens-emulator.md)类似，但模拟器不使用虚拟机。 在模拟器中运行的应用将在 Windows 10 桌面用户会话中运行，就像使用沉浸式耳机一样。 通常由沉浸式耳机上的传感器读取的人工和环境输入使用键盘、鼠标或 Xbox 控制器来模拟。 应用无需修改即可在模拟器中运行，并且不知道它们没有在沉浸式耳机上运行。

## <a name="enabling-the-windows-mixed-reality-simulator"></a>启用 Windows Mixed Reality 模拟器

1. **启用**开发人员模式-> 更新和安全性-为开发人员 >
2. 从桌面启动**混合现实门户**
3. 如果这是你第一次启动门户，则需要完成安装体验
   1. 单击 "**入门**"
   2. 单击 "**我同意**接受协议"
   3. 单击 "**设置" 进行模拟（适用于开发人员）** 以在不使用物理设备的情况下进行安装
   4. 单击 "**设置**" 以确认你的选择
4. 单击混合现实门户左侧的 "**开发人员**" 按钮
5. 将模拟切换开关切换到**打开**
   * 默认情况下，启用模拟将安装并启用左模拟的 DOF 控制器。  在 Windows 10 可能2019更新之前，安装模拟 6 DOF 控制器需要管理员权限。  必须接受 "用户帐户控制" 对话框（如果有）。

现在，你应该已运行模拟！

如果要在 "设置" 中禁用开发人员模式，则应首先在混合现实门户的 "**开发人员**" 部分中将模拟切换开关设置为 "**关闭**"。

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>将应用部署到混合现实模拟器

由于模拟器在没有虚拟机的情况下在本地 PC 上运行，因此，在调试时，只需将通用 Windows 应用程序部署到**本地计算机**上即可。

## <a name="basic-simulator-input"></a>基本模拟器输入

控制模拟器非常类似于许多常见的3D 视频游戏和[HoloLens 模拟器](using-the-hololens-emulator.md)。 可以使用键盘、鼠标或 Xbox 控制器提供输入。

可以通过定向模拟用户的操作，戴上沉浸式耳机来控制模拟器。 你的操作将移动模拟用户，并与应用进行交互，使其与沉浸式耳机上的响应相同。
* **前后左右走动** - 使用键盘上的 WASD 键，或 Xbox 控制器上的左摇杆。
* **上下左右注视** - 单击并拖动鼠标、使用键盘上的箭头键，或使用 Xbox 控制器上的右摇杆。
* **操作按钮按下控制器**-右键单击鼠标，按键盘上的 enter 键，或使用 Xbox 控制器上的按钮。
* **"主页" 按钮按下控制器**-按键盘上的 Windows 键或 F2 键，或按 Xbox 控制器上的 B 按钮。
* **用于滚动的控制器移动**-按住 Alt 键，按住鼠标右键，然后向上/向下拖动鼠标，或在 Xbox 控制器中按住右触发器并向下移动，并向下移动适当的按钮。

## <a name="tracked-controllers"></a>跟踪控制器

混合现实模拟器最多可以模拟两个手持跟踪的运动控制器。 在混合现实门户中使用切换开关启用它们。 每个模拟控制器都有：
* 位置和方向（空间）
* “主页”按钮
* “菜单”按钮
* 手柄按钮
* 触摸板
* 控制
* 电池电量水平

## <a name="see-also"></a>另请参阅
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [高级混合现实模拟器输入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Unity 中的空间映射](spatial-mapping-in-unity.md)
* [DirectX 中的空间映射](spatial-mapping-in-directx.md)
