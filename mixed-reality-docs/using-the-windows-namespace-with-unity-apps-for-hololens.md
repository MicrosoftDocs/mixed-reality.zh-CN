---
title: 用于 HoloLens 的适用于 Unity 的 WinRT Api
description: 介绍如何在适用于 HoloLens 的 Unity 项目中使用 WinRT Api （Windows 命名空间）。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity，WinRT，windows mixed reality，API，演练
ms.openlocfilehash: 73764d191813f6dcae750e74ce3181af987c9e0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437241"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>用于 HoloLens 的适用于 Unity 的 WinRT Api

本页介绍如何在适用于 HoloLens 的 Unity 项目中使用 WinRT Api。

## <a name="mixed-reality-apis"></a>混合现实 Api

已在 .NET Standard 2.0 兼容的投影中提供 Windows SDK 的混合现实重点，你可以在不带预处理器指令的项目中使用。 这包括 Windows 中的大多数 Api 和 Windows UI 命名空间，并且可能会在将来扩展以包含其他 Api。 在编辑器中运行时，可以使用投影的 Api，这允许使用[播放模式](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)。 若要使用此投影，请对项目进行以下修改：

1) 使用[NuGet For Unity](https://github.com/GlitchEnzo/NuGetForUnity)添加对[MixedReality](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) nuget 包的引用。
2) `Microsoft.`的 `Windows` 命名空间的前缀引用：
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) 将本机指针强制转换替换 `FromNativePtr`：
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>有条件地包含 WinRT API 调用

或者，通过使用预处理器指令，可将 WinRT Api 用于通用 Windows 平台和 Xbox One 平台构建的 Unity 项目;在 Unity 脚本中编写的面向 WinRT Api 的任何代码必须仅有条件地包含在这些内部版本中。 

这可以通过 Unity 中的两个步骤完成：
1) API 兼容级别必须设置为 " **.net 4.6** " 或 "播放机设置" 中 **.NET Standard 2.0**
    - **编辑** > **项目设置** > **Player** > **配置** > **Api 兼容性级别**设置为 **.net 4.6**或 **.NET Standard 2.0**
2) 预处理器指令**ENABLE_WINMD_SUPPORT**必须围绕任何 WinRT 利用代码进行包装

以下代码片段来自 Unity 手动页，用于[脚本中C#的通用 WINDOWS 平台： WinRT API](https://docs.unity3d.com/Manual/windowsstore-scripts.html)。 在此示例中，将返回一个广告 ID，但只能在 UWP 和 Xbox one build 上生成：

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

双击 Unity 编辑器中的脚本时，默认情况下，该脚本将在编辑器项目中启动。 WinRT Api 将显示为 "未知"，因为 Visual Studio 项目未引用 Windows 运行时。 此外， **ENABLE_WINMD_SUPPORT**指令将是未定义的，并且在你将项目生成到 UWP Visual Studio 解决方案之前，将忽略任何 *#if*包装代码。

## <a name="see-also"></a>另请参阅
* [导出和构建 Unity Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 运行时支持 Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
