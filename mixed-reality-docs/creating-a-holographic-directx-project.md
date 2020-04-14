---
title: 创建全息 DirectX 项目
description: 介绍如何基于 Windows Mixed Reality 应用模板创建新的全息应用。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality，全息应用，新应用，UWP 应用，模板应用，全息影像，新建项目，演练，下载，示例代码
ms.openlocfilehash: 30f2c630b2919fbc304dc96d13cab74e22ed4adc
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277915"
---
# <a name="creating-a-holographic-directx-project"></a>创建全息 DirectX 项目

为 HoloLens 创建的全息版应用将是<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平台（UWP）应用</a>。  如果面向桌面 Windows Mixed Reality 耳机，则可以创建 UWP 应用或 Win32 应用。

DirectX 11 全息 UWP 应用模板非常类似于 DirectX 11 UWP 应用模板;它包括一个程序循环（或 "游戏循环"）、用于管理 Direct3D 设备和上下文的**DeviceResources**类以及简化的内容呈现器类。 它还有<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>，就像其他任何 UWP 应用一样。

然而，混合现实应用有一些其他功能，这些功能在典型的 Direct3D UWP 应用中不存在。 Windows Mixed Reality 应用模板能够：
* 处理与全息相机关联的 Direct3D 设备资源。
* 检索系统中的相机后台缓冲区，或（如果是 Direct3D12），创建全息后台缓冲区资源并管理资源生存期。
* 处理[注视](gaze-and-commit.md)的输入，并识别简单的[手势](gaze-and-commit.md#composite-gestures)。
* 进入全屏立体声呈现模式。

## <a name="how-do-i-get-started"></a>如何开始？

按照下载 Visual Studio 2019 和 Windows Mixed Reality 应用模板中的说明，首先[安装这些工具](install-the-tools.md)。 混合现实应用模板在 Visual Studio marketplace 上可作为[web 下载](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)，或通过 VISUAL studio UI 安装为扩展。

现在，你已准备好创建 DirectX 11 Windows Mixed Reality 应用！ 请注意，若要删除示例内容，请在*pch*中注释掉**DRAW_SAMPLE_CONTENT**预处理器指令。

## <a name="creating-a-uwp-project"></a>创建 UWP 项目

安装这些[工具](install-the-tools.md)后，你可以创建一个全息 DirectX UWP 项目。

在 Visual Studio 2019 中创建新项目：
1. 启动**Visual Studio**。
2. 在右侧的 "**入门**" 部分中，选择 "**创建新项目**"。
3. 在 "**创建新项目**" 对话框的下拉菜单中，选择**C++** ""、" **Windows Mixed Reality**" 和 " **UWP**"。
4. 选择 "**全息 DirectX 11 应用（通用 Windows）C++（/WinRT）** "。
   在 Visual Studio 2019 中 ![全息C++的 DirectX 11/WinRT UWP 应用项目模板的屏幕截图](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Visual Studio 2019 C++中的全息 DirectX 11/WinRT UWP 应用项目模板*
   >[!IMPORTANT]
   >确保项目模板的名称包含 "（C++/WinRT）"。  如果没有，则已安装全息版项目模板。  若要获取最新的项目模板，请将[其安装](install-the-tools.md)为 Visual Studio 2019 的扩展。
5. 单击 **“下一步”** 。
5. 填写 "**项目名称**" 和 "**位置**" 文本框，然后单击或点击 "**创建**"。 创建全息应用项目。
6. 对于仅面向 HoloLens 2 的开发，请确保将**目标版本**和**最低版本**设置为**Windows 10，版本 1903**。  如果你还面向 HoloLens （第一代）或桌面 Windows Mixed Reality 耳机，你可以将**最低版本**设置为**Windows 10 版本 1809** ，但在使用 HoloLens 2 的新功能时，这将要求在代码中进行一些<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">自适应检查</a>。
   将 Windows 10 （版本1903）设置为目标和最低版本的 ![屏幕截图](images/new-uwp-project.png)<br>
   *将**Windows 10 （版本1903）** 设置为目标和最低版本*
   >[!IMPORTANT]
   >如果看不到**windows 10 （版本 1903** ）作为选项，则不会安装最新的 WINDOWS 10 SDK。  若要使此选项显示，请<a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安装10.0.18362.0 或更高版本的 Windows 10 SDK</a>。

在 Visual Studio 2017 中创建新项目：
1. 启动**Visual Studio**。
2. 在 "**文件**" 菜单上，指向 "**新建**"，然后从上下文菜单中选择 "**项目**"。 此时会打开“新建项目”对话框。
3. 展开左侧的 "**已安装**"，然后展开 "**可视C++** 语言" 节点。
4. 导航到**Windows 通用 > 全息**节点，然后选择 "**全息 DirectX 11 应用（通用 Windows）C++（/WinRT）** "。
   在 Visual Studio 2017 中 ![全息C++的 DirectX 11/WinRT UWP 应用项目模板的屏幕截图](images/holographic-directx-app-cpp-new-project.png)<br>
   *Visual Studio 2017 C++中的全息 DirectX 11/WinRT UWP 应用项目模板*
   >[!IMPORTANT]
   >确保项目模板的名称包含 "（C++/WinRT）"。  如果没有，则已安装全息版项目模板。  若要获取最新的项目模板，请将[其安装](install-the-tools.md)为 Visual Studio 2017 的扩展。
5. 填写 "**名称**" 和 "**位置**" 文本框，然后单击或点击 **"确定"** 。 创建全息应用项目。
6. 对于仅面向 HoloLens 2 的开发，请确保将**目标版本**和**最低版本**设置为**Windows 10，版本 1903**。  如果你还面向 HoloLens （第一代）或桌面 Windows Mixed Reality 耳机，你可以将**最低版本**设置为**Windows 10 版本 1809** ，但在使用 HoloLens 2 的新功能时，这将要求在代码中进行一些<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">自适应检查</a>。
   将 Windows 10 （版本1903）设置为目标和最低版本的 ![屏幕截图](images/new-uwp-project.png)<br>
   *将**Windows 10 （版本1903）** 设置为目标和最低版本*
   >[!IMPORTANT]
   >如果看不到**windows 10 （版本 1903** ）作为选项，则不会安装最新的 WINDOWS 10 SDK。  若要使此选项显示，请<a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">安装10.0.18362.0 或更高版本的 Windows 10 SDK</a>。

该模板使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>（一种 c + + 17 语言 Windows 运行时 api）生成一个项目，该项目支持任何符合标准的 c + + 17 编译器。  该项目演示了如何创建从用户进行了两计量的全球锁定的多维数据集。 用户[可以按](gaze-and-commit.md#composite-gestures)下或按下控制器上的按钮，将多维数据集置于用户[注视](gaze-and-commit.md)指定的不同位置。 可以修改此项目来创建任何混合现实应用。

或者，可以使用基于 SharpDX 的**Visual C#** 全息项目模板创建一个新项目。  如果你的C#全息项目未从 windows 全息应用程序模板开始，你将需要从 Windows Mixed Reality C#模板项目中复制 fxcompile 文件并将其导入到 .csproj 文件中，以便编译你添加到项目中的 HLSL 文件。 在 Visual Studio 的 Windows Mixed Reality 应用程序模板扩展中还提供了 Direct3D 12 模板。

请参阅[使用 Visual Studio 进行部署和调试](using-visual-studio.md)，获取有关如何生成和部署该示例并将其部署到 HoloLens、附加了沉浸式设备的 PC 或仿真程序的信息。

下面的说明将假设你使用C++来构建你的应用程序。

### <a name="uwp-app-entry-point"></a>UWP 应用入口点

全息 UWP 应用在 AppView 的**wWinMain**函数中启动。 **WWinMain**函数创建应用的<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> ，并通过它启动<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 。

从**AppView**：

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

从现在开始，AppView 类处理与 Windows 基本输入事件、CoreWindow 事件和消息等的交互。 它还将创建应用使用的 HolographicSpace。

## <a name="creating-a-win32-project"></a>创建 Win32 项目

开始构建 Win32 全息项目的最简单方法是修改<a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 示例</a>。

此 Win32 示例使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>，它是支持任何符合标准的 c + + 17 编译器的 Windows 运行时 api 的 c + + 17 语言投影。  该项目演示了如何创建从用户进行了两计量的全球锁定的多维数据集。 用户可以按控制器上的按钮，将多维数据集置于用户[注视](gaze-and-commit.md)指定的不同位置。 可以修改此项目来创建任何混合现实应用。

### <a name="win32-app-entry-point"></a>Win32 应用程序入口点

全息 Win32 应用程序在 AppMain 的**wWinMain**函数中启动。 **WWinMain**函数创建应用的 HWND 并启动其消息循环。

从**AppMain**：

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

从现在开始，AppMain 类处理与基本窗口消息的交互，等等。 它还将创建应用使用的 HolographicSpace。

## <a name="render-holographic-content"></a>呈现全息内容

项目的 "**内容**" 文件夹包含用于渲染[全息空间](getting-a-holographicspace.md)中全息影像的类。 模板中的默认全息图是一个旋转多维数据集，该多维数据集与用户相距两米。 绘制此多维数据集是在**SpinningCubeRenderer**中实现的，该方法具有以下关键方法：

|  方法  |  说明 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  加载着色器并创建多维数据集网格。 | 
|  `PositionHologram` |  将全息图置于所提供的<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>指定的位置。 | 
|  `Update` |  旋转多维数据集，并设置模型矩阵。 | 
|  `Render` |  使用顶点和像素着色器呈现一个帧。 | 

**着色**子文件夹包含四个默认着色器实现：

|  着色器  |  说明 | 
|----------|----------|
|  `GeometryShader.hlsl` |  不修改几何图形的传递。 | 
|  `PixelShader.hlsl` |  通过颜色数据。 在光栅化步骤中，将颜色数据插值并分配给一个像素。 | 
|  `VertexShader.hlsl` |  用于在 GPU 上执行顶点处理的简单着色器。 | 
|  `VPRTVertexShader.hlsl` |  用于在 GPU 上执行顶点处理的简单着色器，针对 Windows Mixed Reality 立体声渲染进行了优化。 | 

`VertexShaderShared.hlsl` 包含 `VertexShader.hlsl` 和 `VPRTVertexShader.hlsl`之间共享的通用代码。

注意： Direct3D 12 应用模板还包括 `ViewInstancingVertexShader.hlsl`。 此变体使用 D3D12 可选功能来更有效地呈现立体声图像。

着色器将在项目生成时进行编译，并在**SpinningCubeRenderer：： CreateDeviceDependentResources**方法中加载。

## <a name="interact-with-your-holograms"></a>与全息影像交互

用户输入在**SpatialInputHandler**类中处理，该类获取<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>实例并订阅<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>事件。 这将允许检测分流手势和其他空间输入事件。

## <a name="update-holographic-content"></a>更新全息内容

混合现实应用在游戏循环中更新，默认情况下，它在 `AppMain.cpp`的**Update**方法中实现。 **Update**方法更新场景对象，如旋转立方体，并返回一个<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>对象，该对象用于获取最新的视图和投影矩阵并显示交换链。

`AppMain.cpp` 中的**Render**方法采用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> ，并根据当前应用和空间定位状态将当前帧呈现到每个全息相机。

## <a name="notes"></a>注意

Windows Mixed Reality 应用模板现在支持启用了 Spectre 缓解标志（/Qspectre）的编译。 在编译启用了 Spectre 缓解功能的配置之前，请确保C++安装 Spectre 的 Microsoft Visual （MSVC）运行时库的版本。 若要安装可 Spectre 的C++库，请启动 Visual Studio 安装程序并选择 "**修改**"。 导航到**各个组件**并搜索 "spectre"。 选择与要为其编译 Spectre 的代码所需的目标平台和 MSVC 版本对应的框，然后单击 "**修改**" 开始安装。

## <a name="see-also"></a>另请参阅
* [获取 HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [在 DirectX 中渲染](rendering-in-directx.md)
* [使用 Visual Studio 进行部署和调试](using-visual-studio.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [将 XAML 与全息 DirectX 应用配合使用](using-xaml-with-holographic-directx-apps.md)
