---
title: 导出和构建 Unity 的 Visual Studio 解决方案
description: 本文概述了从 Unity 导出你的混合的现实项目，以便您可以生成和部署在 Visual Studio 中。
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity 中，visual studio 中，导出、 构建、 部署
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592761"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a><span data-ttu-id="e975d-104">导出和构建 Unity 的 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="e975d-104">Exporting and building a Unity Visual Studio solution</span></span>

<span data-ttu-id="e975d-105">如果你不想在应用程序中使用系统键盘，我们的建议是使用*D3D*如你的应用程序会使用略有较少的内存，并可能稍快的启动时间。</span><span class="sxs-lookup"><span data-stu-id="e975d-105">If you don't intend on using the system keyboard in your application, our recommendation is to use *D3D* as your application will use slightly less memory and have a slightly faster launch time.</span></span> <span data-ttu-id="e975d-106">如果在项目中使用 TouchScreenKeyboard API 使用系统键盘，则需要将导出为*XAML*。</span><span class="sxs-lookup"><span data-stu-id="e975d-106">If you are using the TouchScreenKeyboard API in your project to use the system keyboard, you need to export as *XAML*.</span></span>

## <a name="how-to-export-from-unity"></a><span data-ttu-id="e975d-107">如何从 Unity 导出</span><span class="sxs-lookup"><span data-stu-id="e975d-107">How to export from Unity</span></span>

<span data-ttu-id="e975d-108">![Unity 生成设置](images/unitybuildsettings-300px.png)</span><span class="sxs-lookup"><span data-stu-id="e975d-108">![Unity build settings](images/unitybuildsettings-300px.png)</span></span><br>
<span data-ttu-id="e975d-109">*Unity 生成设置*</span><span class="sxs-lookup"><span data-stu-id="e975d-109">*Unity build settings*</span></span>

1. <span data-ttu-id="e975d-110">当你准备好从 Unity 导出你的项目，打开**文件**菜单，然后选择**生成设置...**</span><span class="sxs-lookup"><span data-stu-id="e975d-110">When you are ready to export your project from Unity, open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="e975d-111">单击**添加打开场景**将场景添加到生成。</span><span class="sxs-lookup"><span data-stu-id="e975d-111">Click **Add Open Scenes** to add your scene to the build.</span></span>
3. <span data-ttu-id="e975d-112">在中**生成设置**对话框中，选择以下选项可将 HoloLens 的导出：</span><span class="sxs-lookup"><span data-stu-id="e975d-112">In the **Build Settings** dialog, choose the following options to export for HoloLens:</span></span>
   * <span data-ttu-id="e975d-113">**平台：\*\**通用 Windows 平台*并确保选择**交换机平台\*\*为所选内容才会生效。</span><span class="sxs-lookup"><span data-stu-id="e975d-113">**Platform:** *Universal Windows Platform* and be sure to select **Switch Platform** for your selection to take effect.</span></span>
   * <span data-ttu-id="e975d-114">\**SDK:\*\*\*通用 10*。</span><span class="sxs-lookup"><span data-stu-id="e975d-114">**SDK:** *Universal 10*.</span></span>
   * <span data-ttu-id="e975d-115">\**UWP 生成类型：\*\*\*D3D*。</span><span class="sxs-lookup"><span data-stu-id="e975d-115">**UWP Build Type:** *D3D*.</span></span>
4. <span data-ttu-id="e975d-116">**可选**：**UnityC#项目：** 检查。</span><span class="sxs-lookup"><span data-stu-id="e975d-116">**Optional**: **Unity C# Projects:** Checked.</span></span>

>[!NOTE]
><span data-ttu-id="e975d-117">选中此复选框，您可以：</span><span class="sxs-lookup"><span data-stu-id="e975d-117">Checking this box allows you to:</span></span>
>* <span data-ttu-id="e975d-118">调试 Visual Studio 远程调试器中的应用。</span><span class="sxs-lookup"><span data-stu-id="e975d-118">Debug your app in the Visual Studio remote debugger.</span></span>
>* <span data-ttu-id="e975d-119">Unity 中编辑脚本C#项目时的 WinRT Api 使用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="e975d-119">Edit scripts in the Unity C# project while using IntelliSense for WinRT APIs.</span></span>

5. <span data-ttu-id="e975d-120">从**生成设置...** 窗口中，打开**播放器设置...**</span><span class="sxs-lookup"><span data-stu-id="e975d-120">From the **Build Settings...** window, open **Player Settings...**</span></span>
6. <span data-ttu-id="e975d-121">选择**通用 Windows 平台的设置**选项卡。</span><span class="sxs-lookup"><span data-stu-id="e975d-121">Select the **Settings for Universal Windows Platform** tab.</span></span>
7. <span data-ttu-id="e975d-122">展开**XR 设置**组。</span><span class="sxs-lookup"><span data-stu-id="e975d-122">Expand the **XR Settings** group.</span></span>
8. <span data-ttu-id="e975d-123">在**XR 设置**部分中，选择**受支持的虚拟现实**复选框以添加新**虚拟现实设备**列出并确认 **"Windows 混合Reality"** 被列为受支持的设备。</span><span class="sxs-lookup"><span data-stu-id="e975d-123">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list and confirm **"Windows Mixed Reality"** is listed as a supported device.</span></span>
9. <span data-ttu-id="e975d-124">返回到**生成设置**对话框。</span><span class="sxs-lookup"><span data-stu-id="e975d-124">Return to the **Build Settings** dialog.</span></span>
10. <span data-ttu-id="e975d-125">选择**生成**。</span><span class="sxs-lookup"><span data-stu-id="e975d-125">Select **Build**.</span></span>
11. <span data-ttu-id="e975d-126">在 Windows 资源管理器对话框中显示，创建一个新文件夹来保存 Unity 的生成输出。</span><span class="sxs-lookup"><span data-stu-id="e975d-126">In the Windows Explorer dialog that appears, create a new folder to hold Unity's build output.</span></span> <span data-ttu-id="e975d-127">通常情况下，我们命名的文件夹"应用"。</span><span class="sxs-lookup"><span data-stu-id="e975d-127">Generally, we name the folder "App".</span></span>
12. <span data-ttu-id="e975d-128">选择新创建的文件夹，然后单击**选择文件夹**。</span><span class="sxs-lookup"><span data-stu-id="e975d-128">Select the newly created folder and click **Select Folder**.</span></span>
13. <span data-ttu-id="e975d-129">Unity 已完成构建，Windows 资源管理器窗口将打开到项目根目录。</span><span class="sxs-lookup"><span data-stu-id="e975d-129">Once Unity has finished building, a Windows Explorer window will open to the project root directory.</span></span> <span data-ttu-id="e975d-130">导航到新创建的文件夹。</span><span class="sxs-lookup"><span data-stu-id="e975d-130">Navigate into the newly created folder.</span></span>
14. <span data-ttu-id="e975d-131">打开位于在此文件夹中生成 Visual Studio 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="e975d-131">Open the generated Visual Studio solution file located inside this folder.</span></span>

## <a name="when-to-re-export-from-unity"></a><span data-ttu-id="e975d-132">何时重新导出从 Unity</span><span class="sxs-lookup"><span data-stu-id="e975d-132">When to re-export from Unity</span></span>

<span data-ttu-id="e975d-133">检查"C#项目"复选框时从 Unity 导出您的应用程序创建 Visual Studio 解决方案，包括你的 Unity 脚本文件。</span><span class="sxs-lookup"><span data-stu-id="e975d-133">Checking the "C# Projects" checkbox when exporting your app from Unity creates a Visual Studio solution that includes all your Unity script files.</span></span> <span data-ttu-id="e975d-134">这使您循环访问您的脚本，而无需从 Unity 重新导出。</span><span class="sxs-lookup"><span data-stu-id="e975d-134">This allows you to iterate on your scripts without re-exporting from Unity.</span></span> <span data-ttu-id="e975d-135">但是，如果你想要对你不只需更改的脚本的内容的项目进行更改，你将需要从 Unity 重新导出。</span><span class="sxs-lookup"><span data-stu-id="e975d-135">However, if you want to make changes to your project that aren't just changing the contents of scripts, you will need to re-export from Unity.</span></span> <span data-ttu-id="e975d-136">有时您也需要重新导出从 Unity 的一些示例包括：</span><span class="sxs-lookup"><span data-stu-id="e975d-136">Some examples of times you need to re-export from Unity are:</span></span>
* <span data-ttu-id="e975d-137">添加或删除资产，在项目选项卡中。</span><span class="sxs-lookup"><span data-stu-id="e975d-137">You add or remove assets in the Project tab.</span></span>
* <span data-ttu-id="e975d-138">更改检查器选项卡中的任何值。</span><span class="sxs-lookup"><span data-stu-id="e975d-138">You change any value in the Inspector tab.</span></span>
* <span data-ttu-id="e975d-139">添加或从层次结构选项卡中删除对象。</span><span class="sxs-lookup"><span data-stu-id="e975d-139">You add or remove objects from the Hierarchy tab.</span></span>
* <span data-ttu-id="e975d-140">更改任何 Unity 项目设置</span><span class="sxs-lookup"><span data-stu-id="e975d-140">You change any Unity project settings</span></span>

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a><span data-ttu-id="e975d-141">生成和部署的 Unity 的 Visual Studio 解决方案</span><span class="sxs-lookup"><span data-stu-id="e975d-141">Building and deploying a Unity Visual Studio solution</span></span>

<span data-ttu-id="e975d-142">构建和部署应用程序的其余部分中会发生的情况[Visual Studio](using-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e975d-142">The remainder of building and deploying apps happens in [Visual Studio](using-visual-studio.md).</span></span> <span data-ttu-id="e975d-143">您需要指定 Unity 生成配置。</span><span class="sxs-lookup"><span data-stu-id="e975d-143">You will need to specify a Unity build configuration.</span></span> <span data-ttu-id="e975d-144">Unity 的命名约定可能不同于您在 Visual Studio 中通常用于：</span><span class="sxs-lookup"><span data-stu-id="e975d-144">Unity's naming conventions may differ from what you're usually used to in Visual Studio:</span></span>

|  <span data-ttu-id="e975d-145">配置</span><span class="sxs-lookup"><span data-stu-id="e975d-145">Configuration</span></span>  |  <span data-ttu-id="e975d-146">说明</span><span class="sxs-lookup"><span data-stu-id="e975d-146">Explanation</span></span> | 
|----------|----------|
|  <span data-ttu-id="e975d-147">调试</span><span class="sxs-lookup"><span data-stu-id="e975d-147">Debug</span></span>  |  <span data-ttu-id="e975d-148">启用了关闭的所有优化和探查器。</span><span class="sxs-lookup"><span data-stu-id="e975d-148">All optimizations off and the profiler is enabled.</span></span> <span data-ttu-id="e975d-149">用于调试脚本。</span><span class="sxs-lookup"><span data-stu-id="e975d-149">Used to debug scripts.</span></span> | 
|  <span data-ttu-id="e975d-150">主机</span><span class="sxs-lookup"><span data-stu-id="e975d-150">Master</span></span>  |  <span data-ttu-id="e975d-151">所有优化已都打开，并且禁用探查器。</span><span class="sxs-lookup"><span data-stu-id="e975d-151">All optimizations are turned on and the profiler is disabled.</span></span> <span data-ttu-id="e975d-152">用于将应用提交到应用商店。</span><span class="sxs-lookup"><span data-stu-id="e975d-152">Used to submit apps to the Store.</span></span> | 
|  <span data-ttu-id="e975d-153">发行版本</span><span class="sxs-lookup"><span data-stu-id="e975d-153">Release</span></span>  |  <span data-ttu-id="e975d-154">所有优化已都打开，并且已启用探查器。</span><span class="sxs-lookup"><span data-stu-id="e975d-154">All optimizations are turned on and the profiler is enabled.</span></span> <span data-ttu-id="e975d-155">用于评估应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="e975d-155">Used to evaluate app performance.</span></span> | 

<span data-ttu-id="e975d-156">请注意，上面的列表是将导致 Visual Studio 项目以生成所需的常见触发器的子集。</span><span class="sxs-lookup"><span data-stu-id="e975d-156">Note, the above list is a subset of the common triggers that will cause the Visual Studio project to need to be generated.</span></span> <span data-ttu-id="e975d-157">一般情况下，编辑从 Visual Studio 中的.cs 文件将不需要从在 Unity 中重新生成项目。</span><span class="sxs-lookup"><span data-stu-id="e975d-157">In general, editing .cs files from within Visual Studio will not require the project to be regenerated from within Unity.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e975d-158">疑难解答</span><span class="sxs-lookup"><span data-stu-id="e975d-158">Troubleshooting</span></span>

<span data-ttu-id="e975d-159">如果您发现无法识别对你的.cs 文件的编辑 Visual Studio 项目中，确保"UnityC#项目"从 Unity 的生成菜单生成 VS 项目时检查。</span><span class="sxs-lookup"><span data-stu-id="e975d-159">If you find that edits to your .cs files are not being recognized in your Visual Studio project, ensure that "Unity C# Projects" is checked when you generate the VS project from Unity's Build menu.</span></span>
