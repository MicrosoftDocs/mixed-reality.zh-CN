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
# <a name="creating-a-holographic-directx-project"></a>创建全息版的 DirectX 项目

全息版的应用程序创建将为 HoloLens<a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">通用 Windows 平台 (UWP) 应用</a>。  如果面向桌面 Windows Mixed Reality 耳机，可以创建 UWP 应用或 Win32 应用程序。

DirectX 11 holographic UWP 应用模板非常类似于 DirectX 11 UWP 应用模板;它包括程序循环 （或"游戏循环"）， **DeviceResources**类来管理的 Direct3D 设备和上下文，并简化内容呈现器类。 它还具有<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>，就像任何其他 UWP 应用。

Mixed 的 reality 应用中，但是，有一些典型的 Direct3D 11 UWP 应用中不存在的额外功能。 Windows 全息版的应用程序模板是能够：
* 处理与 holographic 相机关联的 Direct3D 设备资源。
* 从系统中检索照相机后台缓冲区。
* 处理[注视](gaze.md)输入和识别简单[手势](gestures.md)。
* 进入全屏立体声呈现模式。

## <a name="how-do-i-get-started"></a>如何开始？

第一个[安装的工具](install-the-tools.md)，按照下载 Visual Studio 2017 的说明和 Microsoft HoloLens 仿真程序。 全息版的应用程序模板包含在与 Microsoft HoloLens 仿真程序相同的安装程序。 此外请确保在安装之前已选中选项以安装模板。

现在你已准备好创建你的 DirectX 11 Windows Mixed Reality 应用 ！ 请注意，若要删除示例内容，请注释掉**DRAW_SAMPLE_CONTENT**中的预处理器指令*pch.h*。

## <a name="creating-a-uwp-project"></a>创建 UWP 项目

后安装这些工具，您可以创建全息版的 DirectX UWP 项目。 若要创建新项目：
1. 启动**Visual Studio**。
2. 从**文件**菜单，依次指向**新建**，然后选择**项目**从上下文菜单。 **新的项目**对话框随即打开。
3. 展开**已安装**左侧展开**Visual C++** 语言节点。
4. 导航到**Windows 通用 > 全息**节点，然后选择**全息版的 DirectX 11 应用 (通用 Windows) (C++/WinRT)**。
   >[!IMPORTANT]
   >确保项目模板的名称，包括"(C++/WinRT)"。  如果没有，你已安装的全息版的项目模板的旧版本。  若要获取最新的项目模板中，[安装最新的 HoloLens 模拟器](using-the-hololens-emulator.md)。
5. 填写**名称**并**位置**文本框中，然后单击或点击**确定**。 创建全息版的应用程序项目。
6. 对于开发面向仅 HoloLens 2，请确保**目标版本**并**最低版本**设置为**Windows 10，版本 1903年**。  如果你面向 HoloLens （第 1 代） 或桌面 Windows Mixed Reality 耳机，您可以设置**最低版本**到**Windows 10，版本 1809年**相反，尽管这将需要一些<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">版本适应模式检查</a>时使用 HoloLens 2 的新功能，在代码中。

![全息版的应用程序项目模板在 Visual Studio 中的屏幕截图](images/holographic-directx-app-cpp-new-project.png)<br>
*在 Visual Studio 中的全息版的应用程序项目模板*

该模板会生成项目使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>，C + + 17 语言投影支持任何符合标准的 C + + 17 编译器的 Windows 运行时 api。  该项目演示如何创建世界锁定多维数据集，已将用户从两个指标。 用户可以[-敲击](gestures.md#air-tap)或按控制器将多维数据集放置在指定的用户的不同位置上的按钮[注视](gaze.md)。 可以修改此项目以创建任何混合的现实应用。

或者，可以创建新项目使用**可视化C#** 全息版的项目模板，根据 SharpDX。  如果你 holographicC#项目未启动的 Windows 全息版的应用程序模板中，将需要从 Windows Mixed Reality 复制 ms.fxcompile.targets 文件C#模板项目并导入此信息在你.csproj 文件为了编译 HLSL向项目添加的文件。

审阅[使用 Visual Studio 部署和调试](using-visual-studio.md)有关如何生成和部署到你 HoloLens、 PC 与附加，沉浸式设备或仿真程序的示例的信息。

下面的说明的余下部分假设你正在使用C++生成应用。

### <a name="uwp-app-entry-point"></a>UWP 应用程序入口点

在全息版的 UWP 应用启动**wWinMain** AppView.cpp 中的函数。 **WWinMain**函数创建的应用<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> ，并启动<a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a>使用它。

从**AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

从该点开始，AppView 类处理与 Windows 基本输入的事件、 CoreWindow 事件和消息传送，等的交互。 它还将创建由您的应用程序使用 HolographicSpace。

## <a name="creating-a-win32-project"></a>创建 Win32 项目

最简单的方法，若要开始构建的 Win32 全息版的项目是以适应<a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 示例</a>。

此 Win32 示例使用<a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>，C + + 17 语言投影支持任何符合标准的 C + + 17 编译器的 Windows 运行时 api。  该项目演示如何创建世界锁定多维数据集，已将用户从两个指标。 用户可以按控制器将多维数据集放置在指定的用户的不同位置上的按钮[注视](gaze.md)。 可以修改此项目以创建任何混合的现实应用。

### <a name="win32-app-entry-point"></a>Win32 应用程序入口点

Holographic Win32 应用程序启动**wWinMain** AppMain.cpp 中的函数。 **WWinMain**函数创建应用程序的 HWND，并启动其的消息循环。

从**AppMain.cpp**:

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

从该点开始，AppMain 类处理与基本的窗口消息和等等的交互。 它还将创建由您的应用程序使用 HolographicSpace。

## <a name="render-holographic-content"></a>呈现全息版的内容

项目的**内容**文件夹包含用于在呈现全息类[holographic 空间](getting-a-holographicspace.md)。 在模板中的默认全息图是已放置的用户的两个指标的旋转多维数据集。 在中实现时绘制此多维数据集**SpinningCubeRenderer.cpp**，其中包含这些密钥的方法：

|  方法  |  说明 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  加载着色器，并创建多维数据集网格。 | 
|  `PositionHologram` |  指定由提供的位置放置 hologram <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>。 | 
|  `Update` |  旋转多维数据集，并设置的模型矩阵。 | 
|  `Render` |  将帧使用顶点和像素着色器呈现。 | 

**着色器**子文件夹包含四个默认着色器实现：

|  着色器  |  说明 | 
|----------|----------|
|  `GeometryShader.hlsl` |  离开几何图形未修改的形式传递。 | 
|  `PixelShader.hlsl` |  通过颜色数据。 内插颜色数据并将其分配给在光栅化步骤像素。 | 
|  `VertexShader.hlsl` |  若要在 GPU 上执行顶点处理的简单着色器。 | 
|  `VPRTVertexShader.hlsl` |  若要针对 Windows Mixed Reality 立体声呈现进行了优化的 GPU 上执行顶点处理的简单着色器。 | 

`VertexShaderShared.hlsl` 包含常用代码之间共享`VertexShader.hlsl`和`VPRTVertexShader.hlsl`。

着色器编译时生成该项目，并且它们是在加载**SpinningCubeRenderer::CreateDeviceDependentResources**方法。

## <a name="interact-with-your-holograms"></a>在全息与之交互

在中处理用户输入**SpatialInputHandler**类，即被<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a>实例，并订阅<a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a>事件。 这使检测-敲击手势和其他空间的输入的事件。

## <a name="update-holographic-content"></a>全息版的更新内容

在游戏循环中，它默认情况下将实现在混合的现实应用更新**更新**中的方法`AppMain.cpp`。 **更新**方法更新场景对象，如旋转多维数据集，并返回<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>用于获取最新的视图和投影矩阵并呈现交换链的对象。

**呈现**中的方法`AppMain.cpp`采用<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> ，并将每个 holographic 照相机，根据当前的应用和空间定位状态在当前帧的呈现。

## <a name="see-also"></a>请参阅
* [获取 HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [在 DirectX 中呈现](rendering-in-directx.md)
* [使用 Visual Studio 部署和调试](using-visual-studio.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [全息版的 DirectX 应用中使用 XAML](using-xaml-with-holographic-directx-apps.md)
