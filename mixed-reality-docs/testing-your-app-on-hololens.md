---
title: HoloLens 上测试应用
description: 指南和建议以测试 HoloLens 应用
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens 测试
ms.openlocfilehash: 35e8eff230cdcd719952ad2633ec610c9a9a26a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591802"
---
# <a name="testing-your-app-on-hololens"></a>HoloLens 上测试应用

测试 HoloLens 应用程序都非常类似于测试 Windows 应用程序。 （功能、 互操作性、 性能、 安全性、 可靠性等），则应考虑所有常用的方面。 有，但是，一些区域需要特殊处理或注意未在电脑或手机应用通常观察到的详细信息。 全息版的应用需要在一组不同的环境中顺利运行。 它们还需要在所有时间维护性能和用户舒适。 本主题中详细介绍测试这些方面的指南。

## <a name="performance"></a>性能

全息版的应用需要在一组不同的环境中顺利运行。 它们还需要在所有时间维护性能和用户舒适。 性能至关重要，因此我们有一个专用于它的整个主题 Holographic 应用用户的体验。 请确保阅读并遵循[混合现实的了解性能](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>测试 3D 以三维形式
1. **尽可能在任意多个不同的空间中测试您的应用程序。** 请尝试在大房间、 小房间、 浴室、 厨房、 间卧室、 办公室，等等。此外考虑使用非标准功能，如非垂直墙、 波纹的墙、 非水平的上限不考虑聊天室。 它是工作的聊天室之间转换，当地面，经过走廊或楼梯？
2. **在不同的光照条件中测试您的应用程序。** 没有它正确响应不同的环境条件，例如照明、 黑色的图面、 镜像、 玻璃壁等透明/反射图面。
3. **在不同的动作条件中测试您的应用程序。** 放置在设备上，然后尝试各个方案中的动作的各种状态。 没有它正确响应到不同的移动或稳定状态？
4. **测试您的应用程序从不同角度的工作方式。** 如果必须锁定的世界全息图，如果你的用户将指导其背后怎么办？ 如果在用户和全息图之间这里开始，会发生什么情况？ 如果用户将查看从上方或下方的全息图？
5. **使用空间和音频提示。** 请确保您的应用程序使用它们来防止用户丢失。
6. **测试不同避免环境噪音级别应用。** 如果已实现语音命令，请尝试使用不同的避免环境噪音级别调用它们。
7. **测试存在对应的应用和现有**。 请确保测试从席位和现有位置。
8. **测试将应用程序从不同距离**。 可以 UI 元素读取和从距离遥远，与之交互？ 执行用户身上应用 react 你全息？
9. **测试你的应用针对常见的应用栏交互**。 所有应用磁贴和 2D 通用应用都具有[应用程序栏](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps)，可以控制如何在混合世界中放置该应用程序。 请确保单击删除正常终止应用程序进程并，2D 通用应用的上下文中支持后退按钮。 请尝试缩放和移动应用中[调整模式](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps)时处于活动状态，并挂起的应用磁贴时。

### <a name="environmental-test-matrix"></a>环境测试矩阵

![对于 HoloLens 应用开发的环境测试矩阵](images/environment-matrix-600px.png)

## <a name="comfort"></a>舒适
1. **修剪平面。** 将到哪里细心[全息呈现](hologram-stability.md#hologram-render-distances)。
2. **避免虚拟移动与实际磁头运动不一致。** 避免以不是代表用户的实际运动的一种移动照相机。 如果您的应用程序需要移动用户通过一个场景的动作更可预测、 最大程度减少加速，并让用户控制移动。
3. **请遵循全息图质量准则。** 实现的高性能应用程序[全息图质量指南](hologram-stability.md)不太可能导致用户不适。
4. **水平而不是垂直分布全息。** 强制用户花费扩展正在查找的时间段内或向下可能会导致在颈部疲劳。

## <a name="input"></a>Input

### <a name="gaze-and-gestures"></a>视线移动和手势

[注视](gaze.md)是基本窗体使用户能够在全息和环境为目标的 HoloLens 上输入。 以可视方式可以看到你的视线移动面向的基于光标所在的位置。 它很常见鼠标光标相关联的视线移动光标。

[手势](gestures.md)是如何与全息，如鼠标单击进行交互。 大多数情况下的鼠标和触摸行为是相同的但务必要理解和验证处于不同。

**验证您的应用程序具有不同的行为与鼠标和触摸屏输入时。** 这将确定不一致，并有助于设计决策，以使体验更加自然的用户。 例如，触发基于悬停时的操作。

> [!NOTE]
> 特定于 HoloLens 2 的更多指导[即将推出](index.md#news-and-notes)。

### <a name="custom-voice-commands"></a>自定义语音命令

[语音输入](voice-input.md)是一种自然交互。 用户体验可能会特别之处或令人困惑，具体取决于所选的命令和如何公开它们。 通常，不应作为自定义命令中使用系统语音命令，例如"Select"或"你好，小娜"。 下面是要考虑的几个要点：
1. **避免使用听起来相似的命令。** 这可能可以触发错误的命令。
2. **选择发音上丰富单词在可能的情况。** 这将最小化和/或避免 false 激活。

### <a name="peripherals"></a>外设

用户可以与通过对应用进行交互[外围设备](hardware-accessories.md)。 应用无需执行任何特殊操作即可利用该功能，但也有一些值得。
1. **验证自定义的交互。** 如您的应用程序的自定义键盘快捷方式。
2. **验证切换输入的类型。** 尝试使用多个输入的方法来完成一个任务，例如语音、 手势、 鼠标和键盘都在同一个方案。

## <a name="system-integration"></a>系统集成

### <a name="battery"></a>电池

没有连接以了解它如何快速耗尽电池电源的情况下测试应用程序。 通过查看电源 LED 读数，其中一个可以轻松了解电池状态。 ![指示电池电量的 LED 状态](images/batterypowerledindication-500px.png)

### <a name="power-state-transitions"></a>电源状态转换

按预期方式电源状态之间转换时，请验证关键方案的工作。 例如，仍会在应用程序继续在其原始位置？ 它是否正确地保留其状态？ 它会继续按预期方式工作？
1. **备用/恢复。** 若要进入待机状态，可以按并立即释放的电源按钮。 设备还将进入待机状态 3 分钟不活动后自动。 若要从待机状态恢复，可以按并立即释放的电源按钮。 如果连接或断开电源，还将恢复该设备。
2. **关闭 / 重新启动。** 关闭，请按住电源按钮持续为 6 秒。 若要重新启动，请按电源按钮。

### <a name="multi-app-scenarios"></a>多应用方案

尤其是如果您已实现后台任务，应用程序之间进行切换时验证应用程序的核心功能。 复制/粘贴和 Cortana 集成也是值得选择，在适用的情况。

## <a name="telemetry"></a>遥测

使用遥测数据和分析指导您。 将分析集成到您的应用程序将帮助你从 beta 版测试人员和最终用户获取有关您的应用程序的见解。 可以使用此数据，以帮助优化您的应用程序提交到存储区并为将来的更新之前。 有许多分析选项。 如果不能确定从何处着手，请查看[App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx)。

要考虑的问题：
1. 用户如何使用空间？
2. 如何为应用程序放置对象世界中可以检测到问题？
3. 多长时间上的应用程序的不同阶段要花？
4. 多长时间在应用程序要花？
5. 尝试的最常见的使用情况路径用户什么？
6. 用户已达到意外的状态和/或错误？

## <a name="emulator-and-simulated-input"></a>仿真程序和模拟的输入

[HoloLens 模拟器](using-the-hololens-emulator.md)是高效地测试各种模拟的用户特征和空格全息版应用程序的好办法。 下面是有关有效地使用模拟器来测试您的应用程序的一些建议：
1. **使用仿真程序的虚拟聊天室来展开您的测试。** 在仿真程序附带了一组可用于更多的环境中测试您的应用程序的虚拟聊天室。
2. **在仿真程序用于从所有的角度看看您的应用程序。** PageUp/PageDn 密钥将在模拟的用户更高或更短。
3. **测试与实际 HoloLens 应用。** HoloLens 仿真程序是一个很好的工具，可帮助您快速循环访问的应用程序和捕获新 bug，但请确保之前，您还测试物理 HoloLens 上提交至 Windows 应用商店。 这是确保性能和体验非常适合的真实硬件上非常重要。

## <a name="automated-testing-with-perception-simulation"></a>自动测试与 Perception 模拟

某些应用程序开发人员可能想要自动测试其应用程序。 可以使用简单的单元测试以外[perception 模拟](perception-simulation.md)HoloLens 来自动执行您的应用程序的人和世界输入中的堆栈。 Perception 模拟 API 可以发送模拟的输入到 HoloLens 仿真器或物理 HoloLens。

## <a name="windows-app-certification-kit"></a>Windows 应用认证工具包

若要为您的应用程序提供的最大限度地[Windows 应用商店中发布](submitting-an-app-to-the-microsoft-store.md)、 验证和本地测试，然后提交以进行认证。 如果你的应用面向 Windows.Holographic 设备系列[Windows 应用认证工具包](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx)将仅在您的 PC 上运行本地静态分析测试。 将在 HoloLens 上不运行任何测试。

## <a name="see-also"></a>请参阅
* [提交到 Windows 应用商店应用](submitting-an-app-to-the-microsoft-store.md)
