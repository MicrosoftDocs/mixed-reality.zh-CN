---
title: 适用于 Unity 的输入移植指南
description: 了解如何在 Unity 中处理 Windows Mixed Reality 的输入。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 输入、unity、移植
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515493"
---
# <a name="input-porting-guide-for-unity"></a>适用于 Unity 的输入移植指南

你可以使用以下两种方法之一将输入逻辑移植到 Windows Mixed Reality: Unity 的一般输入. GetButton/GetAxis Api, 跨越多个平台或特定于 Windows 的 XR。WSA.输入 Api, 专门为运动控制器和 HoloLens 提供更丰富的数据。

## <a name="general-inputgetbuttongetaxis-apis"></a>General GetButton/GetAxis Api

Unity 目前使用其常规输入. GetButton/GetAxis Api 来公开[OCULUS SDK](https://docs.unity3d.com/Manual/OculusControllers.html)和[OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)的输入。 如果你的应用程序已在使用这些 Api 进行输入, 则这是在 Windows Mixed Reality 中支持运动控制器的最简单途径: 只需重新映射输入管理器中的按钮和轴即可。

有关详细信息, 请参阅[Unity 按钮/轴映射表](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)和[常见 Unity api 的概述](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)。

## <a name="windows-specific-xrwsainput-apis"></a>Windows 特定的 XR。WSA.输入 Api

如果应用已为每个平台构建自定义输入逻辑, 则可以选择在**UnityEngine**命名空间下使用特定于 Windows 的空间输入 api。 这样, 你就可以访问其他信息 (如位置准确性或源类型), 从而让你能够在 HoloLens 上区分双手和控制器。

有关详细信息, 请参阅[UNITYENGINE XR api 概述](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)。

## <a name="grip-pose-vs-pointing-pose"></a>手柄姿势与指针姿势

Windows Mixed Reality 支持多种形式的运动控制器, 其中每个控制器的设计在用户的手位置和自然的 "前进" 方向上不同, 应用程序在呈现控制器.

为了更好地表示这些控制器, 可以针对每个交互源调查以下两种类型:

* **手柄姿势**, 表示由 HoloLens 检测到的掌托的位置, 或包含运动控制器的掌托的位置。
    * 在沉浸式耳机上, 这种姿势最适合用于呈现**用户的手**或**持有用户的对象**, 例如剑或机枪。
    * **手柄的位置**:直接按住控制器时, 掌上质心, 向左或向右调整以使其在手柄内居中。
    * **手柄方向的右轴**:当你完全打开手形成一个平面的5指形姿势时, 它是一种普通于手掌的光线 (从左到右, 从右手掌向后转送)
    * **手柄方向的正向轴**:部分合上时 (如同持有控制器一样), 通过非拇指指的电子管来指向 "转发" 的射线。
    * **手柄方向的上轴**:向右和向后定义隐含的上轴。
    * 可以通过 Unity 的跨供应商输入 API (XR) 访问抓握姿势 **[。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/轮换**), 或通过特定于 Windows 的 API (**SourceState sourcePose TryGetPosition/旋转**, 请求手柄姿势)。
* **指针姿势**, 表示控制器的末端。
    * 这种姿势最适用于在呈现控制器模型本身时**指向 UI**时进行 raycast。
    * 目前, 指针姿势仅通过特定于 Windows 的 API (**TryGetPosition/旋转**, 请求指针姿势) 来提供。

这些姿势坐标全部用 Unity 世界坐标表示。

## <a name="see-also"></a>请参阅
* [运动控制器](motion-controllers.md)
* [Unity 中的手势和运动控制器](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植指南](porting-guides.md)
