---
title: 创建全息 DirectX 项目
description: 介绍如何基于 Windows Mixed Reality 应用模板创建新的全息应用。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 全息应用, 新应用, UWP 应用, 模板应用, 全息影像, 新建项目, 演练, 下载, 示例代码
ms.openlocfilehash: 24f217021cd448f19a744696de42f580f139f76f
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387614"
---
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="3f5a9-104">创建全息 DirectX 项目</span><span class="sxs-lookup"><span data-stu-id="3f5a9-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="3f5a9-105">为 HoloLens 创建的全息版应用将是<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平台 (UWP) 应用</a>。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="3f5a9-106">如果面向桌面 Windows Mixed Reality 耳机, 则可以创建 UWP 应用或 Win32 应用。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="3f5a9-107">DirectX 11 全息 UWP 应用模板非常类似于 DirectX 11 UWP 应用模板;它包括一个程序循环 (或 "游戏循环")、用于管理 Direct3D 设备和上下文的**DeviceResources**类以及简化的内容呈现器类。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="3f5a9-108">它还有<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, 就像其他任何 UWP 应用一样。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="3f5a9-109">然而, 混合现实应用有一些其他功能, 这些功能在典型的 Direct3D 11 UWP 应用中不存在。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="3f5a9-110">Windows 全息应用程序模板能够:</span><span class="sxs-lookup"><span data-stu-id="3f5a9-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="3f5a9-111">处理与全息相机关联的 Direct3D 设备资源。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="3f5a9-112">从系统检索相机后台缓冲区。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="3f5a9-113">处理[注视](gaze.md)的输入, 并识别简单的[手势](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="3f5a9-114">进入全屏立体声呈现模式。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="3f5a9-115">如何实现入门？</span><span class="sxs-lookup"><span data-stu-id="3f5a9-115">How do I get started?</span></span>

<span data-ttu-id="3f5a9-116">首先, 按照下载 Visual Studio 2019 和 Microsoft HoloLens 模拟器中的说明[安装这些工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2019 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="3f5a9-117">全息应用模板包含在与 Microsoft HoloLens 模拟器相同的安装程序中。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="3f5a9-118">还应确保在安装之前选择用于安装模板的选项。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="3f5a9-119">现在, 你已准备好创建 DirectX 11 Windows Mixed Reality 应用!</span><span class="sxs-lookup"><span data-stu-id="3f5a9-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="3f5a9-120">请注意, 若要删除示例内容, 请在*pch*中注释掉**DRAW_SAMPLE_CONTENT**预处理器指令。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="3f5a9-121">创建 UWP 项目</span><span class="sxs-lookup"><span data-stu-id="3f5a9-121">Creating a UWP project</span></span>

<span data-ttu-id="3f5a9-122">安装这些[工具](install-the-tools.md)后, 你可以创建一个全息 DirectX UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-122">Once the [tools are installed](install-the-tools.md) you can then create a holographic DirectX UWP project.</span></span>

<span data-ttu-id="3f5a9-123">创建新项目:</span><span class="sxs-lookup"><span data-stu-id="3f5a9-123">To create a new project:</span></span>
1. <span data-ttu-id="3f5a9-124">启动**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="3f5a9-125">在 "**文件**" 菜单上, 指向 "**新建**", 然后从上下文菜单中选择 "**项目**"。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="3f5a9-126">此时将打开 "**新建项目**" 对话框。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="3f5a9-127">展开左侧的 "**已安装**", 然后展开 "**可视C++** 语言" 节点。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="3f5a9-128">导航到**Windows 通用 > 全息**节点, 然后选择 "**全息 DirectX 11 应用 (通用 Windows)C++(/WinRT)** "。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="3f5a9-129">![Visual Studio 中的全息 DirectX C++11/WinRT UWP 应用项目模板的屏幕截图](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="3f5a9-129">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
   <span data-ttu-id="3f5a9-130">*Visual Studio 中C++的全息 DirectX 11/WinRT UWP 应用项目模板*</span><span class="sxs-lookup"><span data-stu-id="3f5a9-130">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="3f5a9-131">确保项目模板的名称包含 "(C++/WinRT)"。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-131">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="3f5a9-132">如果没有, 则已安装全息版项目模板。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-132">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="3f5a9-133">若要获取最新的项目模板, 请[安装最新的 HoloLens 模拟器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-133">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="3f5a9-134">填写 "**名称**" 和 "**位置**" 文本框, 然后单击或点击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-134">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="3f5a9-135">创建全息应用项目。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-135">The holographic app project is created.</span></span>
6. <span data-ttu-id="3f5a9-136">对于仅面向 HoloLens 2 的开发, 请确保将**目标版本**和**最低版本**设置为**Windows 10, 版本 1903**。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-136">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="3f5a9-137">如果你还面向 HoloLens (第一代) 或桌面 Windows Mixed Reality 耳机, 你可以将**最低版本**设置为**Windows 10 版本 1809** , 但在使用 new <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"></a>HoloLens 2 的功能。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-137">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="3f5a9-138">![将 Windows 10 (版本 1903) 设置为目标和最小版本的屏幕截图](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="3f5a9-138">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="3f5a9-139">*将 **Windows 10 (版本 1903)** 设置为目标和最低版本*</span><span class="sxs-lookup"><span data-stu-id="3f5a9-139">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="3f5a9-140">如果看不到**windows 10 (版本 1903** ) 作为选项, 则不会安装最新的 WINDOWS 10 SDK。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-140">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="3f5a9-141">若要使此选项显示, 请<a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">安装10.0.18362.0 或更高版本的 Windows 10 SDK</a>。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-141">To get this option to appear, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="3f5a9-142">该模板使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>(一种 c + + 17 语言 Windows 运行时 api) 生成一个项目, 该项目支持任何符合标准的 c + + 17 编译器。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-142">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="3f5a9-143">该项目演示了如何创建从用户进行了两计量的全球锁定的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-143">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="3f5a9-144">用户[可以按](gestures.md#air-tap)下或按下控制器上的按钮, 将多维数据集置于用户[注视](gaze.md)指定的不同位置。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-144">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="3f5a9-145">可以修改此项目来创建任何混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-145">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="3f5a9-146">或者, 可以使用基于 SharpDX 的**Visual C#** 全息项目模板创建一个新项目。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-146">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="3f5a9-147">如果你的C#全息项目未从 windows 全息应用程序模板开始, 你将需要从 Windows Mixed Reality C#模板项目复制 fxcompile 文件并将其导入到 .csproj 文件中, 以便编译 HLSL添加到项目中的文件。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-147">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="3f5a9-148">请参阅[使用 Visual Studio 进行部署和调试](using-visual-studio.md), 获取有关如何生成和部署该示例并将其部署到 HoloLens、附加了沉浸式设备的 PC 或仿真程序的信息。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-148">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="3f5a9-149">下面的说明将假设你使用C++来构建你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-149">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="3f5a9-150">UWP 应用入口点</span><span class="sxs-lookup"><span data-stu-id="3f5a9-150">UWP app entry point</span></span>

<span data-ttu-id="3f5a9-151">全息 UWP 应用在 AppView 的**wWinMain**函数中启动。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-151">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="3f5a9-152">**WWinMain**函数创建应用的<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> , 并通过它启动<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-152">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="3f5a9-153">从**AppView**:</span><span class="sxs-lookup"><span data-stu-id="3f5a9-153">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="3f5a9-154">从现在开始, AppView 类处理与 Windows 基本输入事件、CoreWindow 事件和消息等的交互。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-154">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="3f5a9-155">它还将创建应用使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-155">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="3f5a9-156">创建 Win32 项目</span><span class="sxs-lookup"><span data-stu-id="3f5a9-156">Creating a Win32 project</span></span>

<span data-ttu-id="3f5a9-157">开始构建 Win32 全息项目的最简单方法是修改<a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 示例</a>。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-157">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="3f5a9-158">此 Win32 示例使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, 它是支持任何符合标准的 c + + 17 编译器的 Windows 运行时 api 的 c + + 17 语言投影。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-158">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="3f5a9-159">该项目演示了如何创建从用户进行了两计量的全球锁定的多维数据集。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-159">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="3f5a9-160">用户可以按控制器上的按钮, 将多维数据集置于用户[注视](gaze.md)指定的不同位置。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-160">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="3f5a9-161">可以修改此项目来创建任何混合现实应用。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-161">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="3f5a9-162">Win32 应用程序入口点</span><span class="sxs-lookup"><span data-stu-id="3f5a9-162">Win32 app entry point</span></span>

<span data-ttu-id="3f5a9-163">全息 Win32 应用程序在 AppMain 的**wWinMain**函数中启动。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-163">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="3f5a9-164">**WWinMain**函数创建应用的 HWND 并启动其消息循环。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-164">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="3f5a9-165">从**AppMain**:</span><span class="sxs-lookup"><span data-stu-id="3f5a9-165">From **AppMain.cpp**:</span></span>

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

<span data-ttu-id="3f5a9-166">从现在开始, AppMain 类处理与基本窗口消息的交互, 等等。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-166">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="3f5a9-167">它还将创建应用使用的 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-167">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="3f5a9-168">呈现全息内容</span><span class="sxs-lookup"><span data-stu-id="3f5a9-168">Render holographic content</span></span>

<span data-ttu-id="3f5a9-169">项目的 "**内容**" 文件夹包含用于渲染[全息空间](getting-a-holographicspace.md)中全息影像的类。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-169">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="3f5a9-170">模板中的默认全息图是一个旋转多维数据集, 该多维数据集与用户相距两米。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-170">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="3f5a9-171">绘制此多维数据集是在**SpinningCubeRenderer**中实现的, 该方法具有以下关键方法:</span><span class="sxs-lookup"><span data-stu-id="3f5a9-171">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="3f5a9-172">方法</span><span class="sxs-lookup"><span data-stu-id="3f5a9-172">Method</span></span>  |  <span data-ttu-id="3f5a9-173">说明</span><span class="sxs-lookup"><span data-stu-id="3f5a9-173">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="3f5a9-174">加载着色器并创建多维数据集网格。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-174">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="3f5a9-175">将全息图置于所提供的<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>指定的位置。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-175">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="3f5a9-176">旋转多维数据集, 并设置模型矩阵。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-176">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="3f5a9-177">使用顶点和像素着色器呈现一个帧。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-177">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="3f5a9-178">**着色**子文件夹包含四个默认着色器实现:</span><span class="sxs-lookup"><span data-stu-id="3f5a9-178">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="3f5a9-179">着色器</span><span class="sxs-lookup"><span data-stu-id="3f5a9-179">Shader</span></span>  |  <span data-ttu-id="3f5a9-180">说明</span><span class="sxs-lookup"><span data-stu-id="3f5a9-180">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="3f5a9-181">不修改几何图形的传递。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-181">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="3f5a9-182">通过颜色数据。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-182">Passes through the color data.</span></span> <span data-ttu-id="3f5a9-183">在光栅化步骤中, 将颜色数据插值并分配给一个像素。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-183">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="3f5a9-184">用于在 GPU 上执行顶点处理的简单着色器。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-184">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="3f5a9-185">用于在 GPU 上执行顶点处理的简单着色器, 针对 Windows Mixed Reality 立体声渲染进行了优化。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-185">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="3f5a9-186">`VertexShaderShared.hlsl`包含在和`VertexShader.hlsl` `VPRTVertexShader.hlsl`之间共享的通用代码。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-186">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="3f5a9-187">着色器将在项目生成时进行编译, 并在**SpinningCubeRenderer:: CreateDeviceDependentResources**方法中加载。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-187">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="3f5a9-188">与全息影像交互</span><span class="sxs-lookup"><span data-stu-id="3f5a9-188">Interact with your holograms</span></span>

<span data-ttu-id="3f5a9-189">用户输入在**SpatialInputHandler**类中处理, 该类获取<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>实例并订阅<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>事件。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-189">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="3f5a9-190">这将允许检测分流手势和其他空间输入事件。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-190">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="3f5a9-191">更新全息内容</span><span class="sxs-lookup"><span data-stu-id="3f5a9-191">Update holographic content</span></span>

<span data-ttu-id="3f5a9-192">混合现实应用在游戏循环中更新, 默认情况下, 该循环在的**Update**方法`AppMain.cpp`中实现。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-192">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="3f5a9-193">**Update**方法更新场景对象, 如旋转立方体, 并返回一个<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>对象, 该对象用于获取最新的视图和投影矩阵并显示交换链。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-193">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="3f5a9-194">中 `AppMain.cpp`的 Render 方法采用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> , 并根据当前应用和空间定位状态将当前帧呈现到每个全息相机。</span><span class="sxs-lookup"><span data-stu-id="3f5a9-194">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f5a9-195">请参阅</span><span class="sxs-lookup"><span data-stu-id="3f5a9-195">See also</span></span>
* [<span data-ttu-id="3f5a9-196">获取 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="3f5a9-196">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="3f5a9-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="3f5a9-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="3f5a9-198">在 DirectX 中渲染</span><span class="sxs-lookup"><span data-stu-id="3f5a9-198">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="3f5a9-199">使用 Visual Studio 进行部署和调试</span><span class="sxs-lookup"><span data-stu-id="3f5a9-199">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="3f5a9-200">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="3f5a9-200">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="3f5a9-201">将 XAML 与全息 DirectX 应用配合使用</span><span class="sxs-lookup"><span data-stu-id="3f5a9-201">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)
