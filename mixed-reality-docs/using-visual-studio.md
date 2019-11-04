---
title: 使用 Visual Studio 部署和调试
description: 如何使用 Visual Studio 为 HoloLens 和 Windows Mixed Reality 构建、调试和部署应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 10/24/2019
ms.topic: article
keywords: Visual Studio，HoloLens，混合现实，调试，部署
ms.openlocfilehash: 2b84183417a1bd4eaa90eef58bebe2b65966b933
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437291"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>使用 Visual Studio 部署和调试

无论是要使用 DirectX 还是 Unity 开发混合现实应用，都需要使用 Visual Studio 进行调试和部署。 在本部分中，你将学习：
* 如何通过 Visual Studio 将应用程序部署到 HoloLens 或 Windows Mixed Reality 沉浸式耳机。
* 如何使用内置于 Visual Studio 中的 HoloLens 仿真器。
* 如何调试混合现实应用。

## <a name="prerequisites"></a>必备条件
1. 有关安装说明，请参阅[安装工具](install-the-tools.md)。
2. 在 Visual Studio 中创建新的通用 Windows 应用程序项目。  对于 HoloLens （第一代），请使用 Visual Studio 2017 或更高版本。  对于 Hololens 2，请使用 Visual Studio 2019 16.2 或更高版本。 C#支持C++和。 （或按照说明[在 Unity 中创建应用程序](holograms-100.md)。）

## <a name="enabling-developer-mode"></a>启用开发人员模式

首先在你的设备上启用**开发人员模式**，以便 Visual Studio 能够连接到它。

### <a name="hololens"></a>HoloLens
1. 打开 HoloLens 并将其放在设备上。
2. 执行[绽放](system-gesture.md#bloom)手势来启动主菜单。
3. 查看 "**设置**" 磁贴，然后执行 "[空气分流](gaze-and-commit.md#composite-gestures)" 手势。 执行第二个空中点击，以便将该应用放入你的环境中。 在放置“设置”应用后，将启动该应用。
4. 选择“更新”菜单项。
5. 选择“面向开发人员”菜单项。
6. 启用“开发人员模式”。 这将允许你将[Visual Studio 中的应用部署](using-visual-studio.md)到 HoloLens。
7. 可选：向下滚动，同时启用**设备门户**。 这也允许从 web 浏览器连接到 HoloLens 上的[Windows 设备门户](using-the-windows-device-portal.md)。

### <a name="windows-pc"></a>Windows 电脑

如果你正在使用连接到电脑的 Windows Mixed Reality 耳机，则必须在电脑上启用**开发人员模式**。
1. 中转到 "**设置**"
2. 选择**更新和安全**
3. **为开发人员**选择
4. 启用**开发人员模式**，阅读所选设置的免责声明，并单击 "是" 接受更改。

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>通过 Wi-fi （第一代）部署应用
1. 在 Visual Studio 中为应用 ![x86 生成配置选择**x86**生成配置](images/x86setting.png)
2. 在 Visual Studio 中的 "部署目标" 下拉菜单中选择 "**远程计算机**" ![远程计算机部署目标](images/remotemachinesetting.png)
3. 对于C++和 JavaScript 项目，请在 " **> 配置属性" > 调试**中，参阅 "项目 > 属性"。 对于C#项目，会自动弹出一个对话框来配置连接。
  a. 在 "**地址**" 或 "**计算机名**" 字段中输入设备的 IP 地址。 在 "**设置" > 网络 & Internet > 高级选项**"下的" 设置 "下查找你的 HoloLens 上的 ip 地址，或者你可以询问 Cortana" 我的 IP 地址是什么？ "
  b. 在 Visual Studio 中将身份验证模式设置为**通用（未加密的协议）** ![远程连接对话框](images/remotedeploy.png)
4. 选择 "**调试" > "开始调试**" 以部署应用并启动调试![在 Visual Studio 中启动但不调试](images/deploywithdebugging.png)
5. 首次将应用程序从电脑部署到 HoloLens 时，系统将提示你输入 PIN。 按照以下步骤**配对设备**说明。

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>通过 Wi-fi 部署应用-HoloLens 2
1. 在 Visual Studio 中为应用 ![ARM64 生成配置选择**ARM**或**ARM64**生成配置](images/arm64setting.png)
2. 在 Visual Studio 中的 "部署目标" 下拉菜单中选择 "**远程计算机**" ![远程计算机部署目标](images/remotemachinesetting_arm64.png)
3. 对于C++和 JavaScript 项目，请在 " **> 配置属性" > 调试**中，参阅 "项目 > 属性"。 对于C#项目，会自动弹出一个对话框来配置连接。
  a. 在 "**地址**" 或 "**计算机名**" 字段中输入设备的 IP 地址。 在 "**设置" > 网络 & Internet > 高级选项**"下的" 设置 "下查找你的 HoloLens 上的 ip 地址，或者你可以询问 Cortana" 我的 IP 地址是什么？ "
  b. 在 Visual Studio 中将身份验证模式设置为**通用（未加密的协议）** ![远程连接对话框](images/remotedeploy.png)
4. 选择 "**调试" > "开始调试**" 以部署应用并启动调试![在 Visual Studio 中启动但不调试](images/deploywithdebugging.png)
5. 首次将应用程序从电脑部署到 HoloLens 时，系统将提示你输入 PIN。 按照以下步骤**配对设备**说明。

如果你的 HoloLens IP 地址发生更改，你可以通过转到项目 > 属性来更改目标计算机的 IP 地址 **> 配置属性 > 调试**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>通过 USB-HoloLens 部署应用（第一代）
1. 在 Visual Studio 中为应用 ![x86 生成配置选择**x86**生成配置](images/x86setting.png)
2. 在 "部署目标" 下拉菜单中选择 "**设备**"![Visual Studio 中的设备部署](images/buildsettingsusbdeploy.png)
3. 选择 "**调试" > "开始调试**" 以部署应用并启动调试![在 Visual Studio 中启动但不调试](images/deploywithdebugging.png)
4. 首次将应用程序从电脑部署到 HoloLens 时，系统将提示你输入 PIN。 按照以下步骤**配对设备**说明。

## <a name="deploying-an-app-over-usb---hololens-2"></a>通过 USB-HoloLens 2 部署应用
1. 在 Visual Studio 中为应用 ![ARM64 生成配置选择**ARM**或**ARM64**生成配置](images/arm64setting.png)
2. 在 "部署目标" 下拉菜单中选择 "**设备**"![Visual Studio 中的设备部署](images/buildsettingsusbdeploy_arm64.png)
3. 选择 "**调试" > "开始调试**" 以部署应用并启动调试![在 Visual Studio 中启动但不调试](images/deploywithdebugging.png)
4. 首次将应用程序从电脑部署到 HoloLens 时，系统将提示你输入 PIN。 按照以下步骤**配对设备**说明。

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>将应用部署到本地电脑-沉浸式耳机

使用连接到电脑或[混合现实模拟器](using-the-windows-mixed-reality-simulator.md)的 Windows Mixed Reality 沉浸式耳机时，请遵循这些说明。 在这些情况下，只需在本地 PC 上部署并运行应用。
1. 为应用选择**x86**或**x64**生成配置
2. 在 "部署目标" 下拉菜单中选择 "**本地计算机**"
3. 选择 "**调试" > "开始调试**" 以部署应用并启动调试

## <a name="pairing-your-device"></a>配对设备

首次将应用从 Visual Studio 部署到 HoloLens 时，系统将提示你输入 PIN。 在 HoloLens 上，通过启动 "设置" 应用生成 PIN，请前往**开发人员的更新 >** ，然后点击 "**对**"。 你的 HoloLens 上将显示一个 PIN;在 Visual Studio 中键入此 PIN。 配对完成后，在你的 HoloLens 上点击 "**完成**" 以关闭对话框。 这台电脑现在与 HoloLens 配对，你将能够自动部署应用。 对于用于将应用部署到 HoloLens 的每个后续计算机，请重复这些步骤。

若要从已配对的所有计算机取消预配 HoloLens，请启动 "**设置**" 应用，前往**开发人员更新 >** ，然后点击 "**清除**"。

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>将应用部署到 HoloLens （第一代）模拟器
1. 请确保已 **[安装 HoloLens 模拟器](install-the-tools.md)** 。
2. 选择应用的**x86**生成配置。
在 Visual Studio 中 ![x86 生成配置](images/x86setting.png)
3. 在 Visual Studio 中![模拟器目标 "的" 部署目标 "下拉菜单中选择" **HoloLens 模拟器**"](images/deployemulator.png)
4. 选择 "**调试" > "开始调试**" 以部署应用并启动调试![在 Visual Studio 中启动但不调试](images/deploywithdebugging.png)

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>将应用部署到 HoloLens 2 模拟器
1. 请确保已 **[安装 HoloLens 模拟器](install-the-tools.md)** 。
2. 为应用选择**x86**或**x64**生成配置。
在 Visual Studio 中 ![x86 生成配置](images/x86setting.png)
3. 在 Visual Studio 中![模拟器目标 "的" 部署目标 "下拉菜单中选择" **HoloLens 2 模拟器**"](images/deployemulator2.png)
4. 选择 "**调试" > "开始调试**" 以部署应用并启动调试![在 Visual Studio 中启动但不调试](images/deploywithdebugging.png)

## <a name="graphics-debugger-for-hololens-1st-gen"></a>用于 HoloLens 的图形调试器（第一代）

在编写和优化全息版应用程序时，Visual Studio 图形诊断工具非常有用。 有关完整的详细信息，请参阅[MSDN 上的 Visual Studio 图形诊断](https://msdn.microsoft.com/library/hh315751.aspx)。

**启动图形调试器**
1. 按照上面的说明来面向设备或模拟器
2. **开始诊断 >，请参阅调试 > 图形**
3. 使用 HoloLens 首次执行此操作时，可能会出现 "拒绝访问" 错误。 重新启动 HoloLens 以允许更新的权限生效，然后重试。

## <a name="profiling"></a>分析

Visual Studio 分析工具使你可以分析应用的性能和资源使用情况。 这包括用于优化 CPU、内存、图形和网络使用情况的工具。 有关完整详细信息，请参阅[在 MSDN 上运行诊断工具而不进行调试](https://msdn.microsoft.com/library/dn957936.aspx)。

**用 HoloLens 启动分析工具**
1. 按照上面的说明来面向设备或模拟器
2. 转向**调试 > 启动诊断工具而不调试 ...**
3. 选择要使用的工具
4. 单击 "**启动**"
5. 使用 HoloLens 首次执行此操作时，可能会出现 "拒绝访问" 错误。 重新启动 HoloLens 以允许更新的权限生效，然后重试。

## <a name="debugging-an-installed-or-running-app"></a>调试已安装或正在运行的应用

您可以使用 Visual Studio 调试安装的通用 Windows 应用程序，而无需从 Visual Studio 项目进行部署。 如果需要调试已安装的应用包，或者要调试已在运行的应用，则此方法非常有用。
1. 转向**调试-> 其他调试目标-> 调试安装的应用包**
2. 为 "沉浸式耳机" 选择 HoloLens 或**本地计算机**的**远程计算机**目标。
3. 输入设备的**IP 地址**
4. 选择**通用**身份验证模式
5. 此窗口显示正在运行和非活动的应用程序。 选择要调试的内容。
6. 选择要调试的代码类型（"托管"、"本机" 和 "混合"）
7. 单击 "**附加**" 或 "**启动**"

## <a name="see-also"></a>另请参阅
* [安装工具](install-the-tools.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [部署和调试通用 Windows 平台（UWP）应用](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [启用设备进行开发](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
