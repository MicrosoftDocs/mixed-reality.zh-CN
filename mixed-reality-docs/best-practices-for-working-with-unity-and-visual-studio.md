---
title: 使用 Unity 和 Visual Studio 的最佳实践
description: 用于简化使用 Unity 和 Visual Studio 创建混合现实应用程序的工作流的提示和技巧。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 部署，unity，visual studio，HoloLens，HoloLens 2，沉浸式耳机
ms.openlocfilehash: 88eaa69f1349e3303a93d9d634479d8265eb417c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926549"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="8d0f2-104">使用 Unity 和 Visual Studio 的最佳实践</span><span class="sxs-lookup"><span data-stu-id="8d0f2-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="8d0f2-105">使用 Unity 创建混合现实应用程序的开发人员需要在 Unity 和 Visual Studio 之间进行切换，以生成部署到 HoloLens 和/或沉浸式耳机的应用程序包。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-105">A developer creating a mixed reality application with Unity will need to switch between Unity and Visual Studio to build the application package that is deployed to HoloLens and/or an immersive headset.</span></span> <span data-ttu-id="8d0f2-106">默认情况下，需要 Visual Studio 的两个实例（一个用于修改 Unity 脚本，另一个用于部署到设备和调试）。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-106">By default two instances of Visual Studio are required (one to modify Unity scripts and one to deploy to the device and debug).</span></span> <span data-ttu-id="8d0f2-107">以下过程允许使用单个 Visual Studio 实例进行开发，降低导出 Unity 项目的频率，并改善调试体验。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-107">The following procedure allows development using single Visual Studio instance, reduces the frequency of exporting Unity projects, and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="8d0f2-108">提高迭代时间</span><span class="sxs-lookup"><span data-stu-id="8d0f2-108">Improving iteration time</span></span>

<span data-ttu-id="8d0f2-109">Unity 中的 .NET 脚本编写后端支持在 Unity 2018 中被弃用，并且在 Unity 2019 + 中被删除。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-109">Support for .NET scripting back-end in Unity is being deprecated in Unity 2018 and removed in Unity 2019+.</span></span> <span data-ttu-id="8d0f2-110">因此，建议切换到[IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-110">Thus, it is advised to switch to [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html).</span></span> <span data-ttu-id="8d0f2-111">但是，这可能会导致从 Unity 到 Visual Studio 的生成时间变长。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-111">However, this may incur longer build times from Unity to Visual Studio.</span></span> <span data-ttu-id="8d0f2-112">为了提高迭代速度，应设置其环境以获得最佳的编译结果。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-112">To improve for faster iteration, one should set up their environment for best compilation results.</span></span>

1) <span data-ttu-id="8d0f2-113">每次将项目生成到同一个目录，以便在其中重复使用预先生成的文件，从而利用增量生成</span><span class="sxs-lookup"><span data-stu-id="8d0f2-113">Leverage incremental building by building your project to the same directory every time, re-using the pre-built files there</span></span>
2) <span data-ttu-id="8d0f2-114">禁用项目 & 生成文件夹的反恶意软件扫描</span><span class="sxs-lookup"><span data-stu-id="8d0f2-114">Disable anti-malware software scans for your project & build folders</span></span>
   - <span data-ttu-id="8d0f2-115">在 Windows 10 设置应用下打开**病毒 & 威胁防护**</span><span class="sxs-lookup"><span data-stu-id="8d0f2-115">Open **Virus & threat protection** under your Windows 10 settings app</span></span>
   - <span data-ttu-id="8d0f2-116">选择 "安全 **& 威胁防护设置**" 下的 "**管理设置**"</span><span class="sxs-lookup"><span data-stu-id="8d0f2-116">Select **Manage Settings** under **Virus & threat protection settings**</span></span>
   - <span data-ttu-id="8d0f2-117">选择 "**排除**" 部分下的 "**添加或删除排除**项"</span><span class="sxs-lookup"><span data-stu-id="8d0f2-117">Select **Add or remove exclusions** under the **Exclusions** section</span></span>
   - <span data-ttu-id="8d0f2-118">单击 "**添加排除**"，然后选择包含 Unity 项目代码和生成输出的文件夹</span><span class="sxs-lookup"><span data-stu-id="8d0f2-118">Click **Add an exclusion** and select the folder contain your Unity project code and build outputs</span></span>
3) <span data-ttu-id="8d0f2-119">使用 SSD 进行生成</span><span class="sxs-lookup"><span data-stu-id="8d0f2-119">Utilize an SSD for building</span></span>

<span data-ttu-id="8d0f2-120">有关详细信息，请阅读[IL2CPP 优化生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-120">Please read [Optimizing Build Times for IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) for more info.</span></span> <span data-ttu-id="8d0f2-121">此外，请[在 IL2CPP 脚本后端上读取调试](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-121">Also please read [Debugging on IL2CPP Scripting Back-end](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).</span></span>

<span data-ttu-id="8d0f2-122">此外，请考虑安装[ *UnityScriptAnalyzer* Visual Studio 扩展](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-122">Further, consider installing the [*UnityScriptAnalyzer* Visual Studio extension](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer).</span></span> <span data-ttu-id="8d0f2-123">此工具会分析你C#的 Unity 脚本，以获取能够以更优化的方式编写的代码。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-123">This tool analyzes your Unity C# scripts for code that may be able to be written in a more optimized manner.</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="8d0f2-124">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="8d0f2-124">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="8d0f2-125">下载[Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)</span><span class="sxs-lookup"><span data-stu-id="8d0f2-125">Download [Visual Studio Tools for Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)</span></span>

<span data-ttu-id="8d0f2-126">**Visual Studio Tools for Unity 的优点**</span><span class="sxs-lookup"><span data-stu-id="8d0f2-126">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="8d0f2-127">通过放置断点、计算变量和复杂表达式，从 Visual Studio 调试 Unity 编辑器播放模式。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-127">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="8d0f2-128">使用 Unity 项目资源管理器查找脚本，该脚本具有 Unity 显示的完全相同的层次结构。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-128">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="8d0f2-129">直接在 Visual Studio 中获取 Unity 控制台。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-129">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="8d0f2-130">使用向导快速创建或导航到脚本。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-130">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="8d0f2-131">公开C#类变量以便轻松优化</span><span class="sxs-lookup"><span data-stu-id="8d0f2-131">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="8d0f2-132">可以通过两种方式公开类变量。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-132">There are two ways to expose class variables.</span></span> <span data-ttu-id="8d0f2-133">为此，建议将 [SerializeField] 特性添加到专用变量。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-133">The recommended way to do so is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="8d0f2-134">这样，便可以从编辑器访问这些方法，但不能以编程方式公开。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-134">This allows them to be accessed from the editor but not programmatically exposed.</span></span>  <span data-ttu-id="8d0f2-135">另一种方法是使C#类变量公开，以便在编辑器 UI 中公开它们。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-135">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="8d0f2-136">在编辑器中播放时，这两种方法都可以轻松地调整变量。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-136">Both approaches make it possible to easily tweak variables while playing in-editor.</span></span> <span data-ttu-id="8d0f2-137">这对于优化交互 mechanic 属性特别有用。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-137">This is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="8d0f2-138">Windows SDK 或 Unity 升级后重新生成 UWP Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="8d0f2-138">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="8d0f2-139">签入到源代码管理中的 UWP Visual Studio 解决方案可以在升级到新的 Windows SDK 或 Unity 引擎之后过期。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-139">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="8d0f2-140">可以在升级后通过从 Unity 构建新的 UWP 解决方案，然后将任何差异合并到签入的解决方案中来解决此问题。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-140">You can resolve this after the upgrade by building a new UWP solution from Unity, then merging any differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="8d0f2-141">使用文本格式资产以便于比较内容更改</span><span class="sxs-lookup"><span data-stu-id="8d0f2-141">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="8d0f2-142">以文本格式存储资产使你可以更轻松地在 Visual Studio 中查看内容更改差异。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-142">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="8d0f2-143">您可以通过更改**资产序列化**模式来**强制文本**，在 "编辑 > 项目设置 > 编辑器" 中启用此项。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-143">You can enable this in "Edit > Project Settings > Editor" by changing **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="8d0f2-144">但是，合并文本资产文件更改很容易出错，不建议这样做，因此请考虑在源代码管理系统中启用独占二进制文件签出。</span><span class="sxs-lookup"><span data-stu-id="8d0f2-144">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control system.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d0f2-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d0f2-145">See also</span></span>
- [<span data-ttu-id="8d0f2-146">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="8d0f2-146">Visual Studio Tools for Unity</span></span>](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [<span data-ttu-id="8d0f2-147">优化 IL2CPP 的生成时间</span><span class="sxs-lookup"><span data-stu-id="8d0f2-147">Optimizing Build Times for IL2CPP</span></span>](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [<span data-ttu-id="8d0f2-148">*UnityScriptAnalyzer*Visual Studio 扩展</span><span class="sxs-lookup"><span data-stu-id="8d0f2-148">*UnityScriptAnalyzer* Visual Studio extension</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)