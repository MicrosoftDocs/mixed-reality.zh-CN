---
title: 创建全息版的 DirectX 项目
description: 说明如何创建基于 Windows Mixed Reality 应用模板的新全息版应用。
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全息版的应用程序、 新的应用、 UWP 应用、 模板应用、 全息、 新的项目、 演练、 下载示例代码
ms.openlocfilehash: 7d1ea0246cf823f74e68b4e67fbcfc275d081688
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2019
ms.locfileid: "59593067"
---
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="4c12c-104">创建全息版的 DirectX 项目</span><span class="sxs-lookup"><span data-stu-id="4c12c-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="4c12c-105">全息版的应用程序创建将为 HoloLens<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平台 (UWP) 应用</a>。</span><span class="sxs-lookup"><span data-stu-id="4c12c-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="4c12c-106">如果面向桌面 Windows Mixed Reality 耳机，可以创建 UWP 应用或 Win32 应用程序。</span><span class="sxs-lookup"><span data-stu-id="4c12c-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="4c12c-107">DirectX 11 holographic UWP 应用模板非常类似于 DirectX 11 UWP 应用模板;它包括程序循环 （或"游戏循环"）， **DeviceResources**类来管理的 Direct3D 设备和上下文，并简化内容呈现器类。</span><span class="sxs-lookup"><span data-stu-id="4c12c-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="4c12c-108">它还具有<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>，就像任何其他 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="4c12c-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="4c12c-109">Mixed 的 reality 应用中，但是，有一些典型的 Direct3D 11 UWP 应用中不存在的额外功能。</span><span class="sxs-lookup"><span data-stu-id="4c12c-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="4c12c-110">Windows 全息版的应用程序模板是能够：</span><span class="sxs-lookup"><span data-stu-id="4c12c-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="4c12c-111">处理与 holographic 相机关联的 Direct3D 设备资源。</span><span class="sxs-lookup"><span data-stu-id="4c12c-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="4c12c-112">从系统中检索照相机后台缓冲区。</span><span class="sxs-lookup"><span data-stu-id="4c12c-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="4c12c-113">处理[注视](gaze.md)输入和识别简单[手势](gestures.md)。</span><span class="sxs-lookup"><span data-stu-id="4c12c-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="4c12c-114">进入全屏立体声呈现模式。</span><span class="sxs-lookup"><span data-stu-id="4c12c-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="4c12c-115">如何开始？</span><span class="sxs-lookup"><span data-stu-id="4c12c-115">How do I get started?</span></span>

<span data-ttu-id="4c12c-116">第一个[安装的工具](install-the-tools.md)，按照下载 Visual Studio 2017 的说明和 Microsoft HoloLens 仿真程序。</span><span class="sxs-lookup"><span data-stu-id="4c12c-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2017 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="4c12c-117">全息版的应用程序模板包含在与 Microsoft HoloLens 仿真程序相同的安装程序。</span><span class="sxs-lookup"><span data-stu-id="4c12c-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="4c12c-118">此外请确保在安装之前已选中选项以安装模板。</span><span class="sxs-lookup"><span data-stu-id="4c12c-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="4c12c-119">现在你已准备好创建你的 DirectX 11 Windows Mixed Reality 应用 ！</span><span class="sxs-lookup"><span data-stu-id="4c12c-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="4c12c-120">请注意，若要删除示例内容，请注释掉**DRAW_SAMPLE_CONTENT**中的预处理器指令*pch.h*。</span><span class="sxs-lookup"><span data-stu-id="4c12c-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="4c12c-121">创建 UWP 项目</span><span class="sxs-lookup"><span data-stu-id="4c12c-121">Creating a UWP project</span></span>

<span data-ttu-id="4c12c-122">后安装这些工具，您可以创建全息版的 DirectX UWP 项目。</span><span class="sxs-lookup"><span data-stu-id="4c12c-122">Once the tools are installed you can then create a holographic DirectX UWP project.</span></span> <span data-ttu-id="4c12c-123">若要创建新项目：</span><span class="sxs-lookup"><span data-stu-id="4c12c-123">To create a new project:</span></span>
1. <span data-ttu-id="4c12c-124">启动**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="4c12c-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="4c12c-125">从**文件**菜单，依次指向**新建**，然后选择**项目**从上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="4c12c-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="4c12c-126">**新的项目**对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="4c12c-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="4c12c-127">展开**已安装**左侧展开**Visual C++** 语言节点。</span><span class="sxs-lookup"><span data-stu-id="4c12c-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="4c12c-128">导航到**Windows 通用 > 全息**节点，然后选择**全息版的 DirectX 11 应用 (通用 Windows) (C++/WinRT)**。</span><span class="sxs-lookup"><span data-stu-id="4c12c-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="4c12c-129">确保项目模板的名称，包括"(C++/WinRT)"。</span><span class="sxs-lookup"><span data-stu-id="4c12c-129">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="4c12c-130">如果没有，你已安装的全息版的项目模板的旧版本。</span><span class="sxs-lookup"><span data-stu-id="4c12c-130">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="4c12c-131">若要获取最新的项目模板中，[安装最新的 HoloLens 模拟器](using-the-hololens-emulator.md)。</span><span class="sxs-lookup"><span data-stu-id="4c12c-131">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="4c12c-132">填写**名称**并**位置**文本框中，然后单击或点击**确定**。</span><span class="sxs-lookup"><span data-stu-id="4c12c-132">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="4c12c-133">创建全息版的应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="4c12c-133">The holographic app project is created.</span></span>
6. <span data-ttu-id="4c12c-134">对于开发面向仅 HoloLens 2，请确保**目标版本**并**最低版本**设置为**Windows 10，版本 1903年**。</span><span class="sxs-lookup"><span data-stu-id="4c12c-134">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="4c12c-135">如果你面向 HoloLens （第 1 代） 或桌面 Windows Mixed Reality 耳机，您可以设置**最低版本**到**Windows 10，版本 1809年**相反，尽管这将需要一些<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本适应模式检查</a>时使用 HoloLens 2 的新功能，在代码中。</span><span class="sxs-lookup"><span data-stu-id="4c12c-135">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adapative checks</a> in your code when using new features of HoloLens 2.</span></span>

<span data-ttu-id="4c12c-136">![全息版的应用程序项目模板在 Visual Studio 中的屏幕截图](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="4c12c-136">![Screenshot of the holographic app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
<span data-ttu-id="4c12c-137">*在 Visual Studio 中的全息版的应用程序项目模板*</span><span class="sxs-lookup"><span data-stu-id="4c12c-137">*Holographic app project template in Visual Studio*</span></span>

<span data-ttu-id="4c12c-138">该模板会生成项目使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>，C + + 17 语言投影支持任何符合标准的 C + + 17 编译器的 Windows 运行时 api。</span><span class="sxs-lookup"><span data-stu-id="4c12c-138">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="4c12c-139">该项目演示如何创建世界锁定多维数据集，已将用户从两个指标。</span><span class="sxs-lookup"><span data-stu-id="4c12c-139">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="4c12c-140">用户可以[-敲击](gestures.md#air-tap)或按控制器将多维数据集放置在指定的用户的不同位置上的按钮[注视](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="4c12c-140">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="4c12c-141">可以修改此项目以创建任何混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="4c12c-141">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="4c12c-142">或者，可以创建新项目使用**可视化C#** 全息版的项目模板，根据 SharpDX。</span><span class="sxs-lookup"><span data-stu-id="4c12c-142">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="4c12c-143">如果你 holographicC#项目未启动的 Windows 全息版的应用程序模板中，将需要从 Windows Mixed Reality 复制 ms.fxcompile.targets 文件C#模板项目并导入此信息在你.csproj 文件为了编译 HLSL向项目添加的文件。</span><span class="sxs-lookup"><span data-stu-id="4c12c-143">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="4c12c-144">审阅[使用 Visual Studio 部署和调试](using-visual-studio.md)有关如何生成和部署到你 HoloLens、 PC 与附加，沉浸式设备或仿真程序的示例的信息。</span><span class="sxs-lookup"><span data-stu-id="4c12c-144">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="4c12c-145">下面的说明的余下部分假设你正在使用C++生成应用。</span><span class="sxs-lookup"><span data-stu-id="4c12c-145">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="4c12c-146">UWP 应用程序入口点</span><span class="sxs-lookup"><span data-stu-id="4c12c-146">UWP app entry point</span></span>

<span data-ttu-id="4c12c-147">在全息版的 UWP 应用启动**wWinMain** AppView.cpp 中的函数。</span><span class="sxs-lookup"><span data-stu-id="4c12c-147">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="4c12c-148">**WWinMain**函数创建的应用<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> ，并启动<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a>使用它。</span><span class="sxs-lookup"><span data-stu-id="4c12c-148">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="4c12c-149">从**AppView.cpp**:</span><span class="sxs-lookup"><span data-stu-id="4c12c-149">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="4c12c-150">从该点开始，AppView 类处理与 Windows 基本输入的事件、 CoreWindow 事件和消息传送，等的交互。</span><span class="sxs-lookup"><span data-stu-id="4c12c-150">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="4c12c-151">它还将创建由您的应用程序使用 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="4c12c-151">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="4c12c-152">创建 Win32 项目</span><span class="sxs-lookup"><span data-stu-id="4c12c-152">Creating a Win32 project</span></span>

<span data-ttu-id="4c12c-153">最简单的方法，若要开始构建的 Win32 全息版的项目是以适应<a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 示例</a>。</span><span class="sxs-lookup"><span data-stu-id="4c12c-153">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="4c12c-154">此 Win32 示例使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>，C + + 17 语言投影支持任何符合标准的 C + + 17 编译器的 Windows 运行时 api。</span><span class="sxs-lookup"><span data-stu-id="4c12c-154">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="4c12c-155">该项目演示如何创建世界锁定多维数据集，已将用户从两个指标。</span><span class="sxs-lookup"><span data-stu-id="4c12c-155">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="4c12c-156">用户可以按控制器将多维数据集放置在指定的用户的不同位置上的按钮[注视](gaze.md)。</span><span class="sxs-lookup"><span data-stu-id="4c12c-156">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="4c12c-157">可以修改此项目以创建任何混合的现实应用。</span><span class="sxs-lookup"><span data-stu-id="4c12c-157">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="4c12c-158">Win32 应用程序入口点</span><span class="sxs-lookup"><span data-stu-id="4c12c-158">Win32 app entry point</span></span>

<span data-ttu-id="4c12c-159">Holographic Win32 应用程序启动**wWinMain** AppMain.cpp 中的函数。</span><span class="sxs-lookup"><span data-stu-id="4c12c-159">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="4c12c-160">**WWinMain**函数创建应用程序的 HWND，并启动其的消息循环。</span><span class="sxs-lookup"><span data-stu-id="4c12c-160">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="4c12c-161">从**AppMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="4c12c-161">From **AppMain.cpp**:</span></span>

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

<span data-ttu-id="4c12c-162">从该点开始，AppMain 类处理与基本的窗口消息和等等的交互。</span><span class="sxs-lookup"><span data-stu-id="4c12c-162">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="4c12c-163">它还将创建由您的应用程序使用 HolographicSpace。</span><span class="sxs-lookup"><span data-stu-id="4c12c-163">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="4c12c-164">呈现全息版的内容</span><span class="sxs-lookup"><span data-stu-id="4c12c-164">Render holographic content</span></span>

<span data-ttu-id="4c12c-165">项目的**内容**文件夹包含用于在呈现全息类[holographic 空间](getting-a-holographicspace.md)。</span><span class="sxs-lookup"><span data-stu-id="4c12c-165">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="4c12c-166">在模板中的默认全息图是已放置的用户的两个指标的旋转多维数据集。</span><span class="sxs-lookup"><span data-stu-id="4c12c-166">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="4c12c-167">在中实现时绘制此多维数据集**SpinningCubeRenderer.cpp**，其中包含这些密钥的方法：</span><span class="sxs-lookup"><span data-stu-id="4c12c-167">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="4c12c-168">方法</span><span class="sxs-lookup"><span data-stu-id="4c12c-168">Method</span></span>  |  <span data-ttu-id="4c12c-169">说明</span><span class="sxs-lookup"><span data-stu-id="4c12c-169">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="4c12c-170">加载着色器，并创建多维数据集网格。</span><span class="sxs-lookup"><span data-stu-id="4c12c-170">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="4c12c-171">指定由提供的位置放置 hologram <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>。</span><span class="sxs-lookup"><span data-stu-id="4c12c-171">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="4c12c-172">旋转多维数据集，并设置的模型矩阵。</span><span class="sxs-lookup"><span data-stu-id="4c12c-172">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="4c12c-173">将帧使用顶点和像素着色器呈现。</span><span class="sxs-lookup"><span data-stu-id="4c12c-173">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="4c12c-174">**着色器**子文件夹包含四个默认着色器实现：</span><span class="sxs-lookup"><span data-stu-id="4c12c-174">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="4c12c-175">着色器</span><span class="sxs-lookup"><span data-stu-id="4c12c-175">Shader</span></span>  |  <span data-ttu-id="4c12c-176">说明</span><span class="sxs-lookup"><span data-stu-id="4c12c-176">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="4c12c-177">离开几何图形未修改的形式传递。</span><span class="sxs-lookup"><span data-stu-id="4c12c-177">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="4c12c-178">通过颜色数据。</span><span class="sxs-lookup"><span data-stu-id="4c12c-178">Passes through the color data.</span></span> <span data-ttu-id="4c12c-179">内插颜色数据并将其分配给在光栅化步骤像素。</span><span class="sxs-lookup"><span data-stu-id="4c12c-179">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="4c12c-180">若要在 GPU 上执行顶点处理的简单着色器。</span><span class="sxs-lookup"><span data-stu-id="4c12c-180">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="4c12c-181">若要针对 Windows Mixed Reality 立体声呈现进行了优化的 GPU 上执行顶点处理的简单着色器。</span><span class="sxs-lookup"><span data-stu-id="4c12c-181">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="4c12c-182">`VertexShaderShared.hlsl` 包含常用代码之间共享`VertexShader.hlsl`和`VPRTVertexShader.hlsl`。</span><span class="sxs-lookup"><span data-stu-id="4c12c-182">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="4c12c-183">着色器编译时生成该项目，并且它们是在加载**SpinningCubeRenderer::CreateDeviceDependentResources**方法。</span><span class="sxs-lookup"><span data-stu-id="4c12c-183">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="4c12c-184">在全息与之交互</span><span class="sxs-lookup"><span data-stu-id="4c12c-184">Interact with your holograms</span></span>

<span data-ttu-id="4c12c-185">在中处理用户输入**SpatialInputHandler**类，即被<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>实例，并订阅<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>事件。</span><span class="sxs-lookup"><span data-stu-id="4c12c-185">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="4c12c-186">这使检测-敲击手势和其他空间的输入的事件。</span><span class="sxs-lookup"><span data-stu-id="4c12c-186">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="4c12c-187">全息版的更新内容</span><span class="sxs-lookup"><span data-stu-id="4c12c-187">Update holographic content</span></span>

<span data-ttu-id="4c12c-188">在游戏循环中，它默认情况下将实现在混合的现实应用更新**更新**中的方法`AppMain.cpp`。</span><span class="sxs-lookup"><span data-stu-id="4c12c-188">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="4c12c-189">**更新**方法更新场景对象，如旋转多维数据集，并返回<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>用于获取最新的视图和投影矩阵并呈现交换链的对象。</span><span class="sxs-lookup"><span data-stu-id="4c12c-189">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="4c12c-190">**呈现**中的方法`AppMain.cpp`采用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> ，并将每个 holographic 照相机，根据当前的应用和空间定位状态在当前帧的呈现。</span><span class="sxs-lookup"><span data-stu-id="4c12c-190">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c12c-191">请参阅</span><span class="sxs-lookup"><span data-stu-id="4c12c-191">See also</span></span>
* [<span data-ttu-id="4c12c-192">获取 HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="4c12c-192">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="4c12c-193"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="4c12c-193"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="4c12c-194">在 DirectX 中呈现</span><span class="sxs-lookup"><span data-stu-id="4c12c-194">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="4c12c-195">使用 Visual Studio 部署和调试</span><span class="sxs-lookup"><span data-stu-id="4c12c-195">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="4c12c-196">使用 HoloLens 仿真器</span><span class="sxs-lookup"><span data-stu-id="4c12c-196">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="4c12c-197">全息版的 DirectX 应用中使用 XAML</span><span class="sxs-lookup"><span data-stu-id="4c12c-197">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)
