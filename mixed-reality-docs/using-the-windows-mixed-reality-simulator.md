---
title: 使用 Windows Mixed Reality 模拟器
description: Windows Mixed Reality 模拟器，您可以测试混合的现实应用而无需 Windows Mixed Reality 沉浸式头戴式在 PC 上。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows 混合现实，模拟器中测试
ms.openlocfilehash: 782cab85f163edd2afc4251210b7596c73dcc8b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592746"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>使用 Windows Mixed Reality 模拟器

Windows Mixed Reality 模拟器，您可以测试混合的现实应用而无需 Windows Mixed Reality 沉浸式头戴式在 PC 上。 它是 Windows 10 创意者更新开始可用。 模拟器是类似于[HoloLens 模拟器](using-the-hololens-emulator.md)，但模拟器不使用虚拟机。 在会话中运行 Windows 10 桌面用户，就像它们会像使用沉浸式头戴式模拟器中运行的应用程序。 通常会在沉浸式头戴式传感器读取的人和环境输入改为模拟使用键盘、 鼠标或 Xbox 控制器。 应用程序无需修改即可运行在模拟器中，并不知道也不运行在沉浸式头戴式上。

## <a name="enabling-the-windows-mixed-reality-simulator"></a>启用 Windows Mixed Reality 模拟器

1. **启用开发人员模式**从设置-> 更新和安全-> 面向开发人员
2. 启动**混合现实门户**从桌面
3. 如果这是你第一次启动门户，你将需要安装程序体验
   1. 单击**开始**
   2. 单击**我同意**接受协议
   3. 单击 **（适用于开发人员） 设置为模拟**继续通过安装程序而无需物理设备
   4. 单击**设置**来确认你的选择
4. 单击**面向开发人员**混合现实门户左侧的按钮
5. 将模拟切换开关置于**上**
   * 这需要具有管理员权限，并且必须接受显示的用户帐户控制对话框

你现在应运行与模拟 ！

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>将应用部署到混合现实模拟器

模拟器在本地 PC 而无需虚拟机上运行，因为您只需部署到通用 Windows 应用**本地计算机**调试时。

## <a name="basic-simulator-input"></a>基本模拟器输入

控制模拟器是非常类似于许多常见的 3D 视频游戏并[HoloLens 模拟器](using-the-hololens-emulator.md)。 可以使用键盘、 鼠标或 Xbox 控制器是输入的选项。

你将定向戴上沉浸式头戴式模拟的用户的操作，从而控制模拟器。 你的操作将模拟的用户，并导致与应用程序就像在沉浸式头戴式之间的交互。
* **引导前滚，、 左和右**-使用 W，A、 S 和 D 键键盘，或在 Xbox 控制器上的左记忆棒。
* **查找、 下、 左、 左右**-单击并拖动鼠标、 键盘或 Xbox 控制器上的右记忆棒上使用箭头键。
* **按控制器上的操作按钮**-右键单击鼠标、 键盘上按 Enter 键或 Xbox 控制器上使用一个按钮。
* **主控制器上的按下按钮**-在键盘上按 Windows 键或 F2 键或 Xbox 控制器上按 B 按钮。
* **控制器移动滚动**-按住 Alt 键，请按住鼠标右键按钮和向上 / 向下拖动鼠标或 Xbox 控制器中按住正确的触发器和一个按钮并向上和向下移动右。

## <a name="tracked-controllers"></a>跟踪的控制器

混合现实模拟器可以模拟最多两个手持跟踪的动作控制器。 启用它们在混合现实门户中使用切换开关。 每个模拟的控制器具有：
* 在空间中的位置
* “主页”按钮
* “菜单”按钮
* 手柄按钮
* 触摸板

## <a name="see-also"></a>请参阅
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [高级混合的现实模拟器输入](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [在 Unity 中的空间映射](spatial-mapping-in-unity.md)
* [在 DirectX 空间映射](spatial-mapping-in-directx.md)
