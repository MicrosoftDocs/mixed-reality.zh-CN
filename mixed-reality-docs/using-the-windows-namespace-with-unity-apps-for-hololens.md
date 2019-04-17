---
title: 适用于 Unity 应用的 Windows 命名空间用于 HoloLens
description: 介绍了如何进行的 HoloLens 在 Unity 项目中使用的 WinRT Api。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity 中，WinRT，windows 混合的现实，API，演练
ms.openlocfilehash: ed65b5995d74c54057a49b878c1206d0f06394ca
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59591761"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="dfb59-104">适用于 Unity 应用的 Windows 命名空间用于 HoloLens</span><span class="sxs-lookup"><span data-stu-id="dfb59-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="dfb59-105">此页介绍了如何为 HoloLens 在 Unity 项目中使用的 WinRT Api。</span><span class="sxs-lookup"><span data-stu-id="dfb59-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="dfb59-106">有条件地包括 WinRT API 调用</span><span class="sxs-lookup"><span data-stu-id="dfb59-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="dfb59-107">仅将面向 Windows 8、 Windows 8.1 或通用 Windows 平台中; Unity 项目生成中使用 WinRT Api在 Unity 脚本中编写面向 WinRT Api 的任何代码必须是有条件地包括仅这些生成。</span><span class="sxs-lookup"><span data-stu-id="dfb59-107">WinRT APIs will only be used in Unity project builds that target Windows 8, Windows 8.1, or the Universal Windows Platform; any code that you write in Unity scripts that targets WinRT APIs must be conditionally included for only those builds.</span></span> <span data-ttu-id="dfb59-108">这是使用 netfx_core 两种或 WINDOWS_UWP 预处理器定义。</span><span class="sxs-lookup"><span data-stu-id="dfb59-108">This is done using the NETFX_CORE or WINDOWS_UWP preprocessor definitions.</span></span> <span data-ttu-id="dfb59-109">此规则适用于使用语句，以及其他代码。</span><span class="sxs-lookup"><span data-stu-id="dfb59-109">This rule applies to using statements, as well as other code.</span></span>

<span data-ttu-id="dfb59-110">以下代码片段是通过 Unity 手动页[通用 Windows 平台：中的 WinRT APIC#脚本](http://docs.unity3d.com/Manual/windowsstore-scripts.html)。</span><span class="sxs-lookup"><span data-stu-id="dfb59-110">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="dfb59-111">在此示例中，广告 ID 返回，但仅在 Windows 8.0 或更高的目标上的生成：</span><span class="sxs-lookup"><span data-stu-id="dfb59-111">In this example, an advertising ID is returned, but only on Windows 8.0 or higher target builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if NETFX_CORE
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="dfb59-112">编辑您在 Unity 中的脚本C#项目</span><span class="sxs-lookup"><span data-stu-id="dfb59-112">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="dfb59-113">当您双击在 Unity 编辑器中的脚本时，它将默认情况下启动您的脚本编辑器项目中。</span><span class="sxs-lookup"><span data-stu-id="dfb59-113">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="dfb59-114">WinRT Api 将显示为未知的两个原因：Netfx_core 两种未定义此环境中，并且该项目未引用 Windows 运行时。</span><span class="sxs-lookup"><span data-stu-id="dfb59-114">The WinRT APIs will appear to be unknown for two reasons: NETFX_CORE is not defined in this environment, and the project does not reference the Windows Runtime.</span></span> <span data-ttu-id="dfb59-115">如果您使用[建议使用导出和构建设置](exporting-and-building-a-unity-visual-studio-solution.md)，并改为编辑该项目中的脚本，它将定义 netfx_core 两种，还包括到 Windows 运行时; 使用此配置的引用就地，WinRT Api 将是可用于智能感知。</span><span class="sxs-lookup"><span data-stu-id="dfb59-115">If you use the [recommended export and built settings](exporting-and-building-a-unity-visual-studio-solution.md), and edit the scripts in that project instead, it will define NETFX_CORE and also include a reference to the Windows Runtime; with this configuration in place, WinRT APIs will be available for IntelliSense.</span></span>

<span data-ttu-id="dfb59-116">请注意，您的 UnityC#项目还可用于通过使用 F5 在 Visual Studio 中调试远程脚本调试。</span><span class="sxs-lookup"><span data-stu-id="dfb59-116">Note that your Unity C# project can also be used to debug through your scripts using F5 remote debugging in Visual Studio.</span></span> <span data-ttu-id="dfb59-117">如果您看不到使用第一次打开您的 Unity 的 IntelliSenseC#项目，请关闭该项目并重新打开它。</span><span class="sxs-lookup"><span data-stu-id="dfb59-117">If you do not see IntelliSense working the first time that you open your Unity C# project, close the project and re-open it.</span></span> <span data-ttu-id="dfb59-118">IntelliSense 应开始工作。</span><span class="sxs-lookup"><span data-stu-id="dfb59-118">IntelliSense should start working.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfb59-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="dfb59-119">See also</span></span>
* [<span data-ttu-id="dfb59-120">导出和构建 Unity 的 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="dfb59-120">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
