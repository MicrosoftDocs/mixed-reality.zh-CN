---
title: 导出和生成 Unity Visual Studio 解决方案
description: 本文概述如何从 Unity 导出混合现实项目, 以便可以在 Visual Studio 中生成和部署。
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity, visual studio, 导出, 生成, 部署
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525835"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a><span data-ttu-id="da92d-104">导出和生成 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="da92d-104">Exporting and building a Unity Visual Studio solution</span></span>

<span data-ttu-id="da92d-105">如果你不打算在应用程序中使用系统键盘, 我们建议使用*D3D* , 因为你的应用程序将使用略微少的内存, 并且启动时间更快。</span><span class="sxs-lookup"><span data-stu-id="da92d-105">If you don't intend on using the system keyboard in your application, our recommendation is to use *D3D* as your application will use slightly less memory and have a slightly faster launch time.</span></span> <span data-ttu-id="da92d-106">如果在项目中使用 TouchScreenKeyboard API 来使用系统键盘, 则需要导出为*XAML*。</span><span class="sxs-lookup"><span data-stu-id="da92d-106">If you are using the TouchScreenKeyboard API in your project to use the system keyboard, you need to export as *XAML*.</span></span>

## <a name="how-to-export-from-unity"></a><span data-ttu-id="da92d-107">如何从 Unity 导出</span><span class="sxs-lookup"><span data-stu-id="da92d-107">How to export from Unity</span></span>

<span data-ttu-id="da92d-108">![Unity 生成设置](images/unitybuildsettings-300px.png)</span><span class="sxs-lookup"><span data-stu-id="da92d-108">![Unity build settings](images/unitybuildsettings-300px.png)</span></span><br>
<span data-ttu-id="da92d-109">*Unity 生成设置*</span><span class="sxs-lookup"><span data-stu-id="da92d-109">*Unity build settings*</span></span>

1. <span data-ttu-id="da92d-110">如果已准备好从 Unity 导出项目, 请打开 "**文件**" 菜单, 然后选择 "**生成设置 ...** "</span><span class="sxs-lookup"><span data-stu-id="da92d-110">When you are ready to export your project from Unity, open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="da92d-111">单击 "**添加打开的场景**", 将场景添加到生成中。</span><span class="sxs-lookup"><span data-stu-id="da92d-111">Click **Add Open Scenes** to add your scene to the build.</span></span>
3. <span data-ttu-id="da92d-112">在 "**生成设置**" 对话框中, 选择以下要为 HoloLens 导出的选项:</span><span class="sxs-lookup"><span data-stu-id="da92d-112">In the **Build Settings** dialog, choose the following options to export for HoloLens:</span></span>
   * <span data-ttu-id="da92d-113">**平台** *通用 Windows 平台* 并确保选择 **交换机平台** 为所选内容才会生效。</span><span class="sxs-lookup"><span data-stu-id="da92d-113">**Platform:** *Universal Windows Platform* and be sure to select **Switch Platform** for your selection to take effect.</span></span>
   * <span data-ttu-id="da92d-114">**SDK:**  *通用 10*。</span><span class="sxs-lookup"><span data-stu-id="da92d-114">**SDK:** *Universal 10*.</span></span>
   * <span data-ttu-id="da92d-115">**UWP 生成类型：**  *D3D*。</span><span class="sxs-lookup"><span data-stu-id="da92d-115">**UWP Build Type:** *D3D*.</span></span>
4. <span data-ttu-id="da92d-116">**可选**：**Unity C#项目:** Checked.</span><span class="sxs-lookup"><span data-stu-id="da92d-116">**Optional**: **Unity C# Projects:** Checked.</span></span>

>[!NOTE]
><span data-ttu-id="da92d-117">选中此框后, 您可以:</span><span class="sxs-lookup"><span data-stu-id="da92d-117">Checking this box allows you to:</span></span>
>* <span data-ttu-id="da92d-118">在 Visual Studio 远程调试器中调试你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="da92d-118">Debug your app in the Visual Studio remote debugger.</span></span>
>* <span data-ttu-id="da92d-119">使用 IntelliSense for WinRT Api C#时编辑 Unity 项目中的脚本。</span><span class="sxs-lookup"><span data-stu-id="da92d-119">Edit scripts in the Unity C# project while using IntelliSense for WinRT APIs.</span></span>

5. <span data-ttu-id="da92d-120">从 "**生成设置 ...** " 窗口中, 打开 "**播放机设置 ...** "</span><span class="sxs-lookup"><span data-stu-id="da92d-120">From the **Build Settings...** window, open **Player Settings...**</span></span>
6. <span data-ttu-id="da92d-121">选择通用 Windows 平台 "选项卡的"**设置**"。</span><span class="sxs-lookup"><span data-stu-id="da92d-121">Select the **Settings for Universal Windows Platform** tab.</span></span>
7. <span data-ttu-id="da92d-122">展开 " **XR 设置**" 组。</span><span class="sxs-lookup"><span data-stu-id="da92d-122">Expand the **XR Settings** group.</span></span>
8. <span data-ttu-id="da92d-123">在 " **XR 设置**" 部分中, 选中 "**受支持的虚拟现实**" 复选框, 以添加新的**虚拟现实设备**列表, 并确认 **"Windows Mixed Reality"** 列为受支持的设备。</span><span class="sxs-lookup"><span data-stu-id="da92d-123">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list and confirm **"Windows Mixed Reality"** is listed as a supported device.</span></span>
9. <span data-ttu-id="da92d-124">返回到 "**生成设置**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="da92d-124">Return to the **Build Settings** dialog.</span></span>
10. <span data-ttu-id="da92d-125">选择 "**生成**"。</span><span class="sxs-lookup"><span data-stu-id="da92d-125">Select **Build**.</span></span>
11. <span data-ttu-id="da92d-126">在出现的 "Windows 资源管理器" 对话框中, 创建一个新文件夹来保存 Unity 的生成输出。</span><span class="sxs-lookup"><span data-stu-id="da92d-126">In the Windows Explorer dialog that appears, create a new folder to hold Unity's build output.</span></span> <span data-ttu-id="da92d-127">通常, 将文件夹命名为 "App"。</span><span class="sxs-lookup"><span data-stu-id="da92d-127">Generally, we name the folder "App".</span></span>
12. <span data-ttu-id="da92d-128">选择新创建的文件夹, 然后单击 "**选择文件夹**"。</span><span class="sxs-lookup"><span data-stu-id="da92d-128">Select the newly created folder and click **Select Folder**.</span></span>
13. <span data-ttu-id="da92d-129">Unity 完成生成后, 将打开项目根目录的 Windows 资源管理器窗口。</span><span class="sxs-lookup"><span data-stu-id="da92d-129">Once Unity has finished building, a Windows Explorer window will open to the project root directory.</span></span> <span data-ttu-id="da92d-130">导航到新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="da92d-130">Navigate into the newly created folder.</span></span>
14. <span data-ttu-id="da92d-131">打开位于此文件夹中的生成的 Visual Studio 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="da92d-131">Open the generated Visual Studio solution file located inside this folder.</span></span>

## <a name="when-to-re-export-from-unity"></a><span data-ttu-id="da92d-132">何时从 Unity 重新导出</span><span class="sxs-lookup"><span data-stu-id="da92d-132">When to re-export from Unity</span></span>

<span data-ttu-id="da92d-133">在从 UnityC#导出应用程序时选中 "项目" 复选框会创建一个包含所有 Unity 脚本文件的 Visual Studio 解决方案。</span><span class="sxs-lookup"><span data-stu-id="da92d-133">Checking the "C# Projects" checkbox when exporting your app from Unity creates a Visual Studio solution that includes all your Unity script files.</span></span> <span data-ttu-id="da92d-134">这允许您在不从 Unity 重新导出的情况下循环访问您的脚本。</span><span class="sxs-lookup"><span data-stu-id="da92d-134">This allows you to iterate on your scripts without re-exporting from Unity.</span></span> <span data-ttu-id="da92d-135">但是, 如果要更改不只是更改脚本内容的项目, 则需要从 Unity 重新导出。</span><span class="sxs-lookup"><span data-stu-id="da92d-135">However, if you want to make changes to your project that aren't just changing the contents of scripts, you will need to re-export from Unity.</span></span> <span data-ttu-id="da92d-136">需要从 Unity 重新导出的一些时间示例如下:</span><span class="sxs-lookup"><span data-stu-id="da92d-136">Some examples of times you need to re-export from Unity are:</span></span>
* <span data-ttu-id="da92d-137">您可以在 "项目" 选项卡中添加或删除资产。</span><span class="sxs-lookup"><span data-stu-id="da92d-137">You add or remove assets in the Project tab.</span></span>
* <span data-ttu-id="da92d-138">您可以在 "检查器" 选项卡中更改任何值。</span><span class="sxs-lookup"><span data-stu-id="da92d-138">You change any value in the Inspector tab.</span></span>
* <span data-ttu-id="da92d-139">您可以在 "层次结构" 选项卡中添加或删除对象。</span><span class="sxs-lookup"><span data-stu-id="da92d-139">You add or remove objects from the Hierarchy tab.</span></span>
* <span data-ttu-id="da92d-140">更改任何 Unity 项目设置</span><span class="sxs-lookup"><span data-stu-id="da92d-140">You change any Unity project settings</span></span>

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a><span data-ttu-id="da92d-141">生成和部署 Unity Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="da92d-141">Building and deploying a Unity Visual Studio solution</span></span>

<span data-ttu-id="da92d-142">在[Visual Studio](using-visual-studio.md)中生成和部署应用程序的其余部分。</span><span class="sxs-lookup"><span data-stu-id="da92d-142">The remainder of building and deploying apps happens in [Visual Studio](using-visual-studio.md).</span></span> <span data-ttu-id="da92d-143">你将需要指定 Unity 生成配置。</span><span class="sxs-lookup"><span data-stu-id="da92d-143">You will need to specify a Unity build configuration.</span></span> <span data-ttu-id="da92d-144">Unity 的命名约定可能不同于 Visual Studio 中通常使用的内容:</span><span class="sxs-lookup"><span data-stu-id="da92d-144">Unity's naming conventions may differ from what you're usually used to in Visual Studio:</span></span>

|  <span data-ttu-id="da92d-145">配置</span><span class="sxs-lookup"><span data-stu-id="da92d-145">Configuration</span></span>  |  <span data-ttu-id="da92d-146">说明</span><span class="sxs-lookup"><span data-stu-id="da92d-146">Explanation</span></span> | 
|----------|----------|
|  <span data-ttu-id="da92d-147">调试</span><span class="sxs-lookup"><span data-stu-id="da92d-147">Debug</span></span>  |  <span data-ttu-id="da92d-148">禁用所有优化, 并启用探查器。</span><span class="sxs-lookup"><span data-stu-id="da92d-148">All optimizations off and the profiler is enabled.</span></span> <span data-ttu-id="da92d-149">用于调试脚本。</span><span class="sxs-lookup"><span data-stu-id="da92d-149">Used to debug scripts.</span></span> | 
|  <span data-ttu-id="da92d-150">主机</span><span class="sxs-lookup"><span data-stu-id="da92d-150">Master</span></span>  |  <span data-ttu-id="da92d-151">启用所有优化并禁用探查器。</span><span class="sxs-lookup"><span data-stu-id="da92d-151">All optimizations are turned on and the profiler is disabled.</span></span> <span data-ttu-id="da92d-152">用于将应用提交到应用商店。</span><span class="sxs-lookup"><span data-stu-id="da92d-152">Used to submit apps to the Store.</span></span> | 
|  <span data-ttu-id="da92d-153">发行版本</span><span class="sxs-lookup"><span data-stu-id="da92d-153">Release</span></span>  |  <span data-ttu-id="da92d-154">启用所有优化, 并启用探查器。</span><span class="sxs-lookup"><span data-stu-id="da92d-154">All optimizations are turned on and the profiler is enabled.</span></span> <span data-ttu-id="da92d-155">用于评估应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="da92d-155">Used to evaluate app performance.</span></span> | 

<span data-ttu-id="da92d-156">请注意, 上面的列表是常见触发器的一个子集, 将导致需要生成 Visual Studio 项目。</span><span class="sxs-lookup"><span data-stu-id="da92d-156">Note, the above list is a subset of the common triggers that will cause the Visual Studio project to need to be generated.</span></span> <span data-ttu-id="da92d-157">通常, 在 Visual Studio 中编辑 .cs 文件不需要从 Unity 内重新生成项目。</span><span class="sxs-lookup"><span data-stu-id="da92d-157">In general, editing .cs files from within Visual Studio will not require the project to be regenerated from within Unity.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="da92d-158">疑难解答</span><span class="sxs-lookup"><span data-stu-id="da92d-158">Troubleshooting</span></span>

<span data-ttu-id="da92d-159">如果你发现你的 Visual Studio 项目中未识别对 .cs 文件的编辑, 请确保在从 Unity 的 " C#生成" 菜单生成 VS 项目时选中 "Unity 项目"。</span><span class="sxs-lookup"><span data-stu-id="da92d-159">If you find that edits to your .cs files are not being recognized in your Visual Studio project, ensure that "Unity C# Projects" is checked when you generate the VS project from Unity's Build menu.</span></span>
