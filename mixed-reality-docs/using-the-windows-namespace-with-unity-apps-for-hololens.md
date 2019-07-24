---
title: 将 Windows 命名空间用于 HoloLens 的 Unity 应用
description: 说明如何在适用于 HoloLens 的 Unity 项目中使用 WinRT Api。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, 演练
ms.openlocfilehash: fd25548de8eeb3c8157a3f9de283dc5004ed1180
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548731"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>将 Windows 命名空间用于 HoloLens 的 Unity 应用

本页介绍如何在适用于 HoloLens 的 Unity 项目中使用 WinRT Api。

## <a name="conditionally-include-winrt-api-calls"></a>有条件地包含 WinRT API 调用

WinRT Api 可用于针对通用 Windows 平台和 Xbox one 平台构建的 Unity 项目;在 Unity 脚本中编写的面向 WinRT Api 的任何代码必须仅有条件地包含在这些内部版本中。 

这可以通过 Unity 中的两个步骤完成:
1) API 兼容级别必须设置为 " **.net 4.6** " 或 "播放机设置" 中 **.NET Standard 2.0**
    - **编辑** **项目设置**   播放器配置 Api 兼容级别到 .net 4.6 或 .NET Standard 2.0 >  >  >  > 
2) 预处理器指令**ENABLE_WINMD_SUPPORT**必须围绕任何 WinRT 利用代码进行包装

下面的代码片段来自[通用 Windows 平台的 Unity 手动页:脚本](http://docs.unity3d.com/Manual/windowsstore-scripts.html)中的C# WinRT API。 在此示例中, 将返回一个广告 ID, 但只能在 UWP 和 Xbox one build 上生成:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>在 Unity C#项目中编辑脚本

双击 Unity 编辑器中的脚本时, 默认情况下, 该脚本将在编辑器项目中启动。 WinRT Api 将显示为 "未知", 因为 Visual Studio 项目未引用 Windows 运行时。 此外, **ENALBE_WINMD_SUPPORT**指令将是未定义的, 并且在你将项目生成到 UWP Visual Studio 解决方案之前, 将忽略任何 *#if*包装代码。

## <a name="see-also"></a>请参阅
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 运行时支持 Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)