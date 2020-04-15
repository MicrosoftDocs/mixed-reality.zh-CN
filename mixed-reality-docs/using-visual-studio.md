---
title: 使用 Visual Studio 进行部署和调试
description: 了解如何使用 Visual Studio 生成、调试和部署适用于 HoloLens 与 Windows Mixed Reality 的应用。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, 混合现实, Mixed Reality, 调试, 部署
ms.openlocfilehash: 718635922196b9c044c6904ebab994e9e2a2ff1a
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277995"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>使用 Visual Studio 进行部署和调试

无论是要使用 DirectX 还是 Unity 来开发混合现实应用，都需要使用 Visual Studio 进行调试和部署。 本部分介绍以下操作：
* 通过 Visual Studio 将应用程序部署到 HoloLens 或 Windows Mixed Reality 沉浸式头戴显示设备。
* 使用 Visual Studio 中内置的 HoloLens 仿真器。
* 调试混合现实应用。

## <a name="prerequisites"></a>必备条件
1. 有关安装说明，请参阅[安装工具](install-the-tools.md)。
2. 在 Visual Studio 中创建新的通用 Windows 应用项目。  对于 HoloLens（第一代），请使用 Visual Studio 2017 或更高版本。  对于 HoloLens 2，请使用 Visual Studio 2019 16.2 或更高版本。 支持 C# 和 C++。 （或按说明[在 Unity 中创建应用](holograms-100.md)。）

## <a name="enabling-developer-mode"></a>启用开发人员模式

首先在设备上启用“开发人员模式”，使 Visual Studio 能够连接到该设备。 

### <a name="hololens"></a>HoloLens
1. 打开 HoloLens，然后戴上设备。
2. 执行[绽放](system-gesture.md#bloom)手势来启动主菜单。
3. 凝视“设置”磁贴，然后执行[隔空敲击](gaze-and-commit.md#composite-gestures)手势。  执行第二个空中点击，以便将该应用放入你的环境中。 在放置“设置”应用后，将启动该应用。
4. 选择“更新”  菜单项。
5. 选择“面向开发人员”  菜单项。
6. 启用“开发人员模式”  。 这样，就可以[将应用从 Visual Studio 部署到](using-visual-studio.md) HoloLens。
7. 可选：向下滚动，同时启用“设备门户”。  然后，也可以通过 Web 浏览器连接到 HoloLens 上的 [Windows 设备门户](using-the-windows-device-portal.md)。

### <a name="windows-pc"></a>Windows 电脑

如果使用已连接到电脑的 Windows Mixed Reality 头戴显示设备，则必须在电脑上启用“开发人员模式”。 
1. 转到“设置” 
2. 选择“更新和安全” 
3. 选择“面向开发人员” 
4. 启用“开发人员模式”，阅读所选设置的免责声明，然后单击“是”以接受更改。 

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>通过 Wi-Fi 部署应用 - HoloLens（第一代）
1. 为你的应用选择一个 **x86** 生成配置</br>
![Visual Studio 中的 x86 生成配置](images/x86setting.png)</br>
2. 在部署目标下拉菜单中选择“远程计算机” </br>
![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting.png)</br>
3. 对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。  对于 C# 项目，屏幕上会自动显示一个用于配置连接的对话框。
  a. 在“地址”或“计算机名”字段中输入设备的 IP 地址。   在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址，或者可以向 Cortana 提问“我的 IP 地址是什么？” 
  b. 将身份验证模式设置为“通用(未加密协议)” </br>
  ![Visual Studio 中的远程连接对话框](images/remotedeploy.png)</br>
4. 选择“调试”>“开始调试”以部署应用并开始调试 </br>
![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</br>
5. 首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。 按下面的说明**配对设备**。

## <a name="deploying-an-app-over-wi-fi---hololens-2"></a>通过 Wi-Fi 部署应用 - HoloLens 2
1. 为你的应用选择一个 **ARM** 或 **ARM64** 生成配置</br>
![Visual Studio 中的 ARM64 生成配置](images/arm64setting.png)</br>
2. 在部署目标下拉菜单中选择“远程计算机” </br>
![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting_arm64.png)</br>
3. 对于 C++ 和 JavaScript 项目，请转到“项目”>“属性”>“配置属性”>“调试”。  对于 C# 项目，屏幕上会自动显示一个用于配置连接的对话框。
  a. 在“地址”或“计算机名”字段中输入设备的 IP 地址。   在“设置”>“网络和 Internet”>“高级选项”下找到 HoloLens 的 IP 地址，或者可以向 Cortana 提问“我的 IP 地址是什么？” 
  b. 将身份验证模式设置为“通用(未加密协议)” </br>
  ![Visual Studio 中的远程连接对话框](images/remotedeploy.png)</br>
4. 选择“调试”>“开始调试”以部署应用并开始调试 </br>
![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</br>
5. 首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。 按下面的说明**配对设备**。

如果 HoloLens IP 地址已更改，你可以转到“项目”>“属性”>“配置属性”>“调试”来更改目标计算机的 IP 地址 

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>通过 USB 部署应用 - HoloLens（第一代）
1. 为你的应用选择一个 **x86** 生成配置</br>
![Visual Studio 中的 x86 生成配置](images/x86setting.png)</br>
2. 在部署目标下拉菜单中选择“设备” </br>
![Visual Studio 中的设备部署](images/buildsettingsusbdeploy.png)</br>
3. 选择“调试”>“开始调试”以部署应用并开始调试 </br>
![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</br>
4. 首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。 按下面的说明**配对设备**。

## <a name="deploying-an-app-over-usb---hololens-2"></a>通过 USB 部署应用 - HoloLens 2
1. 为你的应用选择一个 **ARM** 或 **ARM64** 生成配置</br>
![Visual Studio 中的 ARM64 生成配置](images/arm64setting.png)</br>
2. 在部署目标下拉菜单中选择“设备” </br>
![Visual Studio 中的设备部署](images/buildsettingsusbdeploy_arm64.png)</br>
3. 选择“调试”>“开始调试”以部署应用并开始调试 </br>
![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</br>
4. 首次将应用从电脑部署到 HoloLens 时，系统会提示输入 PIN。 按下面的说明**配对设备**。

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>将应用部署到本地电脑 - 沉浸式头戴显示设备

使用与电脑或 [Mixed Reality 仿真器](using-the-windows-mixed-reality-simulator.md)连接的 Windows Mixed Reality 沉浸式头戴显示设备时，请按这些说明操作。 在这种情况下，只需在本地电脑上部署并运行应用即可。
1. 为应用选择一种 **x86** 或 **x64** 生成配置
2. 在部署目标下拉菜单中选择“本地计算机” 
3. 选择“调试”>“开始调试”以部署应用并开始调试 

## <a name="pairing-your-device"></a>配对设备

首次将应用从 Visual Studio 部署到 HoloLens 时，系统会提示输入 PIN。 在 HoloLens 上启动“设置”应用，转到“更新”>“面向开发人员”并点击“配对”，以生成 PIN。   HoloLens 上会显示一个 PIN；请在 Visual Studio 中键入此 PIN。 配对完成后，在 HoloLens 上点击“完成”关闭对话框。  此电脑现已与 HoloLens 配对，接下来可以自动部署应用。 请针对用于将应用部署到 HoloLens 的每台后续电脑重复上述步骤。

若要取消 HoloLens 与所有已配对计算机的配对，请启动“设置”应用，转到“更新”>“面向开发人员”，然后点击“清除”。   

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>将应用部署到 HoloLens（第一代）仿真器
1. 请确保已 **[安装 HoloLens 仿真器](install-the-tools.md)** 。
2. 为应用选择一种 **x86** 生成配置。</br>
![Visual Studio 中的 x86 生成配置](images/x86setting.png)</br>
3. 在部署目标下拉菜单中选择“HoloLens 仿真器” </br>
![Visual Studio 中的仿真器目标](images/deployemulator.png)</br>
4. 选择“调试”>“开始调试”以部署应用并开始调试 </br>
![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</br>

## <a name="deploying-an-app-to-the-hololens-2-emulator"></a>将应用部署到 HoloLens 2 仿真器
1. 请确保已 **[安装 HoloLens 仿真器](install-the-tools.md)** 。
2. 为应用选择一种 **x86** 或 **x64** 生成配置。</br>
![Visual Studio 中的 x86 生成配置](images/x86setting.png)</br>
3. 在部署目标下拉菜单中选择“HoloLens 2 仿真器” </br>
![Visual Studio 中的仿真器目标](images/deployemulator2.png)</br>
4. 选择“调试”>“开始调试”以部署应用并开始调试 </br>
![在不调试的情况下在 Visual Studio 中启动](images/deploywithdebugging.png)</br>

## <a name="graphics-debugger-for-hololens-1st-gen"></a>适用于 HoloLens（第一代）的图形调试器

在编写和优化全息应用时，Visual Studio 图形诊断工具非常有用。 有关完整详细信息，请参阅 [MSDN 上的“Visual Studio 图形诊断”](https://msdn.microsoft.com/library/hh315751.aspx)。

**启动图形调试器**
1. 按上面的说明将目标指定为设备或仿真器
2. 转到“调试”>“图形”>“启动诊断” 
3. 首次在 HoloLens 上执行此操作时，可能会出现“拒绝访问”错误。 请重新启动 HoloLens 以使更新的权限生效，然后重试。

## <a name="profiling"></a>分析

使用 Visual Studio 分析工具可以分析应用的性能和资源使用情况。 这些工具包括用于优化 CPU、内存、图形和网络使用情况的工具。 有关完整详细信息，请参阅 [MSDN 上的“运行诊断工具但不调试”](https://msdn.microsoft.com/library/dn957936.aspx)。

**在 HoloLens 上启动分析工具**
1. 按上面的说明将目标指定为设备或仿真器
2. 转到“调试”>“启动诊断工具但不调试...” 
3. 选择要使用的工具
4. 单击“启动” 
5. 首次在 HoloLens 上执行此操作时，可能会出现“拒绝访问”错误。 请重新启动 HoloLens 以使更新的权限生效，然后重试。

## <a name="debugging-an-installed-or-running-app"></a>调试已安装的或正在运行的应用

可以使用 Visual Studio 来调试已安装的通用 Windows 应用，而无需从 Visual Studio 项目部署该应用。 若要调试已安装的应用包，或者要调试已运行的应用，此方法非常有用。
1. 转到“调试”->“其他调试目标”->“调试已安装的应用包” 
2. 为 HoloLens 选择“远程计算机”目标，或者为沉浸式头戴显示设备选择“本地计算机”。  
3. 输入设备的 **IP 地址**
4. 选择“通用”身份验证模式 
5. 窗口中会显示正在运行的和非活动的应用。 选择要调试的应用。
6. 选择要调试的代码类型（“托管”、“本机”、“混合”）
7. 单击“附加”或“开始”  

## <a name="see-also"></a>另请参阅
* [安装工具](install-the-tools.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [部署和调试通用 Windows 平台 (UWP) 应用](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [启用设备进行开发](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
