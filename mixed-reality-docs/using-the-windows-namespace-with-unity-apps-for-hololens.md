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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="08f3d-104">将 Windows 命名空间用于 HoloLens 的 Unity 应用</span><span class="sxs-lookup"><span data-stu-id="08f3d-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="08f3d-105">本页介绍如何在适用于 HoloLens 的 Unity 项目中使用 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="08f3d-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="08f3d-106">有条件地包含 WinRT API 调用</span><span class="sxs-lookup"><span data-stu-id="08f3d-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="08f3d-107">WinRT Api 可用于针对通用 Windows 平台和 Xbox one 平台构建的 Unity 项目;在 Unity 脚本中编写的面向 WinRT Api 的任何代码必须仅有条件地包含在这些内部版本中。</span><span class="sxs-lookup"><span data-stu-id="08f3d-107">WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="08f3d-108">这可以通过 Unity 中的两个步骤完成:</span><span class="sxs-lookup"><span data-stu-id="08f3d-108">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="08f3d-109">API 兼容级别必须设置为 " **.net 4.6** " 或 "播放机设置" 中 **.NET Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="08f3d-109">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="08f3d-110">**编辑** **项目设置**   播放器配置 Api 兼容级别到 .net 4.6 或 .NET Standard 2.0 >  >  >  > </span><span class="sxs-lookup"><span data-stu-id="08f3d-110">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="08f3d-111">预处理器指令**ENABLE_WINMD_SUPPORT**必须围绕任何 WinRT 利用代码进行包装</span><span class="sxs-lookup"><span data-stu-id="08f3d-111">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="08f3d-112">下面的代码片段来自[通用 Windows 平台的 Unity 手动页:脚本](http://docs.unity3d.com/Manual/windowsstore-scripts.html)中的C# WinRT API。</span><span class="sxs-lookup"><span data-stu-id="08f3d-112">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="08f3d-113">在此示例中, 将返回一个广告 ID, 但只能在 UWP 和 Xbox one build 上生成:</span><span class="sxs-lookup"><span data-stu-id="08f3d-113">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="08f3d-114">在 Unity C#项目中编辑脚本</span><span class="sxs-lookup"><span data-stu-id="08f3d-114">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="08f3d-115">双击 Unity 编辑器中的脚本时, 默认情况下, 该脚本将在编辑器项目中启动。</span><span class="sxs-lookup"><span data-stu-id="08f3d-115">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="08f3d-116">WinRT Api 将显示为 "未知", 因为 Visual Studio 项目未引用 Windows 运行时。</span><span class="sxs-lookup"><span data-stu-id="08f3d-116">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="08f3d-117">此外, **ENALBE_WINMD_SUPPORT**指令将是未定义的, 并且在你将项目生成到 UWP Visual Studio 解决方案之前, 将忽略任何 *#if*包装代码。</span><span class="sxs-lookup"><span data-stu-id="08f3d-117">Further, the **ENALBE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="08f3d-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="08f3d-118">See also</span></span>
* [<span data-ttu-id="08f3d-119">导出和构建 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="08f3d-119">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="08f3d-120">Windows 运行时支持 Unity</span><span class="sxs-lookup"><span data-stu-id="08f3d-120">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)