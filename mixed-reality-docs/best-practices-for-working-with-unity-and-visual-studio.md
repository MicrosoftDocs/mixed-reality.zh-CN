---
title: 使用 Unity 和 Visual Studio 的最佳实践
description: 提示和技巧来简化使用 Unity 和 Visual Studio 中创建混合的现实应用程序的工作流。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 部署，unity 中，visual studio 中，HoloLens，沉浸式头戴式
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592863"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a><span data-ttu-id="b03e2-104">使用 Unity 和 Visual Studio 的最佳实践</span><span class="sxs-lookup"><span data-stu-id="b03e2-104">Best practices for working with Unity and Visual Studio</span></span>

<span data-ttu-id="b03e2-105">使用 Unity 创建的混合的现实应用程序的开发人员将需要 Unity 和 Visual Studio 生成应用程序包部署到 HoloLens 和/或沉浸式头戴式之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="b03e2-105">A developer creating a mixed reality application with Unity will need to switch between Unity and Visual Studio to build the application package that is deployed to HoloLens and/or an immersive headset.</span></span> <span data-ttu-id="b03e2-106">默认情况下的 Visual Studio 的两个实例是所需 （一个修改 Unity 脚本），另一个将部署到设备和调试。</span><span class="sxs-lookup"><span data-stu-id="b03e2-106">By default two instances of Visual Studio are required (one to modify Unity scripts and one to deploy to the device and debug).</span></span> <span data-ttu-id="b03e2-107">以下过程将允许使用单个 Visual Studio 实例的开发，可减少导出 Unity 项目的频率并改善了调试体验。</span><span class="sxs-lookup"><span data-stu-id="b03e2-107">The following procedure allows development using single Visual Studio instance, reduces the frequency of exporting Unity projects, and improves the debugging experience.</span></span>

## <a name="improving-iteration-time"></a><span data-ttu-id="b03e2-108">提高迭代时间</span><span class="sxs-lookup"><span data-stu-id="b03e2-108">Improving iteration time</span></span>

<span data-ttu-id="b03e2-109">常见的工作流问题在使用 Unity 和 Visual Studio 时遇到 Visual Studio 打开，并且需要不断地切换 Visual Studio 和 Unity 进行循环访问多个的窗口。</span><span class="sxs-lookup"><span data-stu-id="b03e2-109">A common workflow problem when working with Unity and Visual Studio is having multiple windows of Visual Studio open and the need to constantly switch between Visual Studio and Unity to iterate.</span></span>
1. <span data-ttu-id="b03e2-110">**Unity** -修改场景和导出 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="b03e2-110">**Unity** - for modifying the scene and exporting a Visual Studio solution</span></span>
2. <span data-ttu-id="b03e2-111">**Visual Studio (1)** -修改脚本</span><span class="sxs-lookup"><span data-stu-id="b03e2-111">**Visual Studio (1)** - for modifying scripts</span></span>
3. <span data-ttu-id="b03e2-112">**Visual Studio (2)** -对于构建和部署 Unity 导出到设备的 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="b03e2-112">**Visual Studio (2)** - for building and deploying the Unity exported Visual Studio solution to the device</span></span>

<span data-ttu-id="b03e2-113">幸运的是，是一种简化为单个实例的 Visual Studio 和 Unity 中频繁导出减少方法。</span><span class="sxs-lookup"><span data-stu-id="b03e2-113">Luckily, there's a way to streamline to a single instance of Visual Studio and cut down on frequent exports from Unity.</span></span>

<span data-ttu-id="b03e2-114">当[导出你的项目从 Unity](exporting-and-building-a-unity-visual-studio-solution.md)，检查**UnityC#项目**"文件 > 生成设置"菜单中的复选框。</span><span class="sxs-lookup"><span data-stu-id="b03e2-114">When [exporting your project from Unity](exporting-and-building-a-unity-visual-studio-solution.md), check the **Unity C# Projects** checkbox in the "File > Build Settings" menu.</span></span> <span data-ttu-id="b03e2-115">现在，从 Unity 导出该项目包含所有项目的C#脚本，并且具有以下几个好处：</span><span class="sxs-lookup"><span data-stu-id="b03e2-115">Now, the project you export from Unity includes all of your project's C# scripts and has several benefits:</span></span>
* <span data-ttu-id="b03e2-116">用于编写脚本和生成/部署你的项目使用 Visual Studio 的同一实例</span><span class="sxs-lookup"><span data-stu-id="b03e2-116">Use the same instance of Visual Studio for writing scripts and building/deploying your project</span></span>
* <span data-ttu-id="b03e2-117">仅当场景更改在 Unity 编辑器中; 从 Unity 导出更改的脚本的内容可以在 Visual Studio 中而无需重新导出。</span><span class="sxs-lookup"><span data-stu-id="b03e2-117">Export from Unity only when the scene is changed in the Unity Editor; changing the contents of scripts can be done in Visual Studio without re-exporting.</span></span>

<span data-ttu-id="b03e2-118">与**UnityC#项目**已启用，就需要打开的每个程序只有一个实例：</span><span class="sxs-lookup"><span data-stu-id="b03e2-118">With **Unity C# Projects** enabled, only one instance of each program need be opened:</span></span>
1. <span data-ttu-id="b03e2-119">**Unity** -修改场景和导出 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="b03e2-119">**Unity** - for modifying the scene and exporting a Visual Studio solution</span></span>
2. <span data-ttu-id="b03e2-120">**Visual Studio** -修改脚本，然后生成和部署 Unity 导出到设备的 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="b03e2-120">**Visual Studio** - for modifying scripts then building and deploying the Unity exported Visual Studio solution to the device</span></span>

## <a name="visual-studio-tools-for-unity"></a><span data-ttu-id="b03e2-121">Visual Studio Tools for Unity</span><span class="sxs-lookup"><span data-stu-id="b03e2-121">Visual Studio Tools for Unity</span></span>

<span data-ttu-id="b03e2-122">下载[Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)</span><span class="sxs-lookup"><span data-stu-id="b03e2-122">Download [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)</span></span>

<span data-ttu-id="b03e2-123">**Visual Studio Tools for Unity 的优点**</span><span class="sxs-lookup"><span data-stu-id="b03e2-123">**Benefits of Visual Studio Tools for Unity**</span></span>
* <span data-ttu-id="b03e2-124">调试 Unity 编辑器中播放模式下从 Visual Studio 通过放置断点，评估变量和复杂表达式。</span><span class="sxs-lookup"><span data-stu-id="b03e2-124">Debug Unity in-editor play mode from Visual Studio by putting breakpoints, evaluating variables and complex expressions.</span></span>
* <span data-ttu-id="b03e2-125">使用 Unity 项目资源管理器使用 Unity 显示的完全相同层次结构中查找您的脚本。</span><span class="sxs-lookup"><span data-stu-id="b03e2-125">Use the Unity Project Explorer to find your script with the exact same hierarchy that Unity displays.</span></span>
* <span data-ttu-id="b03e2-126">获取直接在 Visual Studio 的 Unity 控制台。</span><span class="sxs-lookup"><span data-stu-id="b03e2-126">Get the Unity console directly inside Visual Studio.</span></span>
* <span data-ttu-id="b03e2-127">使用向导来快速创建或导航到脚本。</span><span class="sxs-lookup"><span data-stu-id="b03e2-127">Use wizards to quickly create or navigate to scripts.</span></span>

## <a name="expose-c-class-variables-for-easy-tuning"></a><span data-ttu-id="b03e2-128">公开C#类的简单优化变量</span><span class="sxs-lookup"><span data-stu-id="b03e2-128">Expose C# class variables for easy tuning</span></span>

<span data-ttu-id="b03e2-129">有两种方法来公开类变量。</span><span class="sxs-lookup"><span data-stu-id="b03e2-129">There are two ways to expose class variables.</span></span> <span data-ttu-id="b03e2-130">执行此操作的建议的方法是将 [SerializeField] 属性添加到你的私有变量。</span><span class="sxs-lookup"><span data-stu-id="b03e2-130">The recommended way to do so is to add the [SerializeField] attribute to your private variables.</span></span> <span data-ttu-id="b03e2-131">这使他们能够访问在编辑器中但未以编程方式公开。</span><span class="sxs-lookup"><span data-stu-id="b03e2-131">This allows them to be accessed from the editor but not programatically exposed.</span></span>  <span data-ttu-id="b03e2-132">另一个选项是使C#类变量以将其公开编辑器 UI 中为 public。</span><span class="sxs-lookup"><span data-stu-id="b03e2-132">The other option is to make C# class variables public to expose them in the editor UI.</span></span> 

<span data-ttu-id="b03e2-133">这两种方法使其可以轻松地调整同时播放在编辑器的变量。</span><span class="sxs-lookup"><span data-stu-id="b03e2-133">Both approaches make it possible to easily tweak variables while playing in-editor.</span></span> <span data-ttu-id="b03e2-134">这是用于优化交互的机修工保养属性尤其有用。</span><span class="sxs-lookup"><span data-stu-id="b03e2-134">This is especially useful for tuning interaction mechanic properties.</span></span>

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a><span data-ttu-id="b03e2-135">Windows SDK 或 Unity 在升级后重新生成 UWP 的 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="b03e2-135">Regenerate UWP Visual Studio solutions after Windows SDK or Unity upgrade</span></span>

<span data-ttu-id="b03e2-136">UWP 的 Visual Studio 解决方案签入到源代码管理即可升级到新的 Windows SDK 或 Unity 引擎后过期。</span><span class="sxs-lookup"><span data-stu-id="b03e2-136">UWP Visual Studio solutions checked in to source control can get out-of-date after upgrading to a new Windows SDK or Unity engine.</span></span> <span data-ttu-id="b03e2-137">您可以解决此问题在升级后生成新的 UWP 解决方案从 Unity 中，然后将所有差异都合并到签入的解决方案。</span><span class="sxs-lookup"><span data-stu-id="b03e2-137">You can resolve this after the upgrade by building a new UWP solution from Unity, then merging any differences into the checked-in solution.</span></span>

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a><span data-ttu-id="b03e2-138">使用文本格式资产以便进行比较的内容更改</span><span class="sxs-lookup"><span data-stu-id="b03e2-138">Use text-format assets for easy comparison of content changes</span></span>

<span data-ttu-id="b03e2-139">将资产存储以文本格式，可以方便地查看 Visual Studio 中的内容更改差异。</span><span class="sxs-lookup"><span data-stu-id="b03e2-139">Storing assets in text format makes it easier to review content change diffs in Visual Studio.</span></span> <span data-ttu-id="b03e2-140">通过更改可以启用"编辑 > 项目设置 > 编辑器"中此**资产序列化**模式设置为**强制文本，**。</span><span class="sxs-lookup"><span data-stu-id="b03e2-140">You can enable this in "Edit > Project Settings > Editor" by changing **Asset Serialization** mode to **Force Text**.</span></span> <span data-ttu-id="b03e2-141">但是，合并文本资产文件的更改是易出错，不建议使用，因此，考虑在源代码管理系统中启用独占二进制方式签出。</span><span class="sxs-lookup"><span data-stu-id="b03e2-141">However, merging text asset file changes is error-prone and not recommended, so consider enabling exclusive binary checkouts in your source control system.</span></span>
