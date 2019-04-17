---
title: 移植指南 Unity 的输入
description: 了解如何处理在 Unity 中的 Windows Mixed Reality 的输入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 输入、 unity、 移植
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592543"
---
# <a name="input-porting-guide-for-unity"></a>移植指南 Unity 的输入

可以移植到 Windows Mixed Reality 使用两种方法，跨多个平台，Unity 的常规 Input.GetButton/GetAxis Api 或特定于 Windows 的 XR 之一你输入的逻辑。WSA。输入产品/服务专为运动控制器和 HoloLens 手更丰富的数据的 Api。

## <a name="general-inputgetbuttongetaxis-apis"></a>常规 Input.GetButton/GetAxis Api

Unity 当前使用其常规 Input.GetButton/Input.GetAxis Api 公开的输入[Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)并[OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)。 如果您的应用程序已在使用这些 Api 的输入，这是以支持 Windows Mixed Reality 中的动作控制器的最简单路径： 只需重新映射按钮和轴中输入管理器。

有关详细信息，请参阅[Unity 按钮/轴映射表](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)并[常见的 Unity Api 概述](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。

## <a name="windows-specific-xrwsainput-apis"></a>Windows-specific XR.WSA.Input APIs

如果你的应用程序已生成的每个平台的自定义输入的逻辑，你可以选择使用特定于 Windows 的空间输入的 Api 下**UnityEngine.XR.WSA.Input**命名空间。 这允许您访问其他信息，如位置准确性或源类型，让你在 HoloLens 上告诉双手和控制器分离。

有关详细信息，请参阅[UnityEngine.XR.WSA.Input Api 概述](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。

## <a name="grip-pose-vs-pointing-pose"></a>与指针姿势手柄姿势

Windows Mixed Reality 支持不同的外形规格运动控制器，使用每个控制器设计各不相同，"转发"方向该应用的自然用户的手位置之间的关系应为使用指向呈现时控制器。

若要更好地表示这些控制器，有两种类型的可以为每个交互源调查的带来：

* **手柄姿势**，表示检测到的 HoloLens 手的形状的手掌或手掌持有运动控制器的位置。
    * 在沉浸式耳机，此姿势最适合用于呈现**用户的手**或**对象保存在用户的手中**，例如双刃剑或手段。
    * **抓住位置**:Palm 质心时保存在控制器正常情况下，调整左侧或右侧居中手柄内的位置。
    * **抓住方向的右轴**:完全打开您的手以形成平面 5 手指姿势，ray 的时您的手掌接触到正常 （从左 palm，向右 palm 从后向前）
    * **抓住正轴方向的**:当您关闭您的手部分 （就像按控制器），"forward"通过管通过非 thumb 手指点与射线。
    * **抓住方向沿轴向上**:权限隐含的权限和转发定义最多轴。
    * 您可以通过任一 Unity 跨供应商输入 API 访问手柄姿势 (**[XR。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation**) 或通过特定于 Windows 的 API (**sourceState.sourcePose.TryGetPosition/Rotation**，请求手柄姿势)。
* **指针姿势**，表示指向转发的控制器的提示。
    * 此姿势最习惯 raycast 时**指向 UI**时呈现控制器模型本身。
    * 目前，指针姿势目前仅通过特定于 Windows 的 API (**sourceState.sourcePose.TryGetPosition/Rotation**，请求指针姿势)。

这些姿势坐标都表示在 Unity 世界坐标。

## <a name="see-also"></a>请参阅
* [运动控制器](motion-controllers.md)
* [手势和 Unity 中的动作控制器](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植指南](porting-guides.md)
