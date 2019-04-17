---
title: 使用 Visual Studio 部署和调试
description: 如何生成、 调试和部署适用于 HoloLens 和使用 Visual Studio 的 Windows Mixed Reality 应用。
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Visual Studio、 HoloLens、 混合现实，调试部署
ms.openlocfilehash: 6bd47d7212d321791a11ff4db91c3e172c91f463
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592259"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>使用 Visual Studio 部署和调试

是否想要使用 DirectX 或 Unity 开发混合的现实应用，你将使用 Visual Studio 用于调试和部署。 在本部分中，您将了解：
* 如何向你 HoloLens 或 Windows Mixed Reality 沉浸式头戴式耳机通过 Visual Studio 部署应用程序。
* 如何使用内置于 Visual Studio 中的 HoloLens 仿真程序。
* 如何调试混合的现实应用。

## <a name="prerequisites"></a>先决条件
1. 请参阅[安装的工具](install-the-tools.md)有关安装说明。
2. 在 Visual Studio 2015 Update 1 或 Visual Studio 2017 中创建一个新的通用 Windows 应用程序项目。 C#C++，和 JavaScript 项目均受支持。 (或按照说明[在 Unity 中创建应用程序的生成](holograms-100.md)。)

## <a name="enabling-developer-mode"></a>启用开发人员模式

首先，启用**开发人员模式**以便 Visual Studio 可以连接到它在设备上。

### <a name="hololens"></a>HoloLens
1. 打开你 HoloLens 并放置在设备上。
2. 执行[绽放](gestures.md#bloom)手势来启动主菜单。
3. 注视**设置**磁贴，并执行[air 点击](gestures.md#air-tap)手势。 执行第二个空中点击，以便将该应用放入你的环境中。 在放置“设置”应用后，将启动该应用。
4. 选择“更新”菜单项。
5. 选择“面向开发人员”菜单项。
6. 启用“开发人员模式”。 这使您能够[从 Visual Studio 部署应用](using-visual-studio.md)到你 HoloLens。
7. 可选：向下滚动并且启用**设备门户**。 这将允许你连接到[Windows Device Portal](using-the-windows-device-portal.md)从 web 浏览器在 HoloLens 上。

### <a name="windows-pc"></a>Windows 电脑

如果您正在使用 Windows Mixed Reality 耳机连接到您的 PC，则必须启用**开发人员模式**在 PC 上。
1. 转到**设置**
2. 选择**更新和安全**
3. 选择**面向开发人员**
4. 启用**开发人员模式**，阅读免责声明为所选的设置，然后单击是以接受更改。

## <a name="deploying-an-app-over-wi-fi---hololens-1st-gen"></a>部署应用程序通过 Wi-fi-HoloLens （第 1 代）
1. 选择**x86**生成您的应用程序的配置![x86 生成 Visual Studio 中的配置](images/x86setting.png)
2. 选择**远程计算机**中的部署目标下拉列表菜单![Visual Studio 中的远程计算机部署目标](images/remotemachinesetting.png)
3. 有关C++和 JavaScript 项目，请转到**项目 > 属性 > 配置属性 > 调试**。 有关C#项目，会自动弹出对话框中将配置的连接。
  a. 输入你的设备中的 IP 地址**地址**或**计算机名称**字段。 在下，在 HoloLens 上找到的 IP 地址**设置 > 网络和 Internet > 高级选项**，或者可以要求 Cortana"什么是我的 IP 地址？"
  b. 将身份验证模式设置为**通用 （未加密的协议）**![Visual Studio 中的远程连接对话框](images/remotedeploy.png)
4. 选择**调试 > 启动调试**以将应用部署并开始调试![启动而无需 Visual Studio 中调试](images/deploynodebugging.png)
5. 第一次应用部署到你 HoloLens 从您的 PC，系统会提示输入 PIN。 请按照**配对设备**下面的说明。

如果你的 HoloLens IP 地址发生更改，你可以在目标计算机的 IP 地址通过转到**项目 > 属性 > 配置属性 > 调试**

## <a name="deploying-an-app-over-usb---hololens-1st-gen"></a>部署应用程序通过 USB-HoloLens （第 1 代）
1. 选择**x86**生成您的应用程序的配置![x86 生成 Visual Studio 中的配置](images/x86setting.png)
2. 选择**设备**中的部署目标下拉列表菜单![Visual Studio 中的设备部署](images/buildsettingsusbdeploy.png)
3. 选择**调试 > 启动调试**以将应用部署并开始调试![启动而无需 Visual Studio 中调试](images/deploynodebugging.png)
4. 第一次应用部署到你 HoloLens 从您的 PC，系统会提示输入 PIN。 请按照**配对设备**下面的说明。

## <a name="deploying-an-app-to-your-local-pc---immersive-headset"></a>将应用部署到你的本地 PC 的沉浸式头戴式

使用 Windows Mixed Reality 沉浸式头戴式耳机连接到您的 PC 时按照这些说明进行操作或[混合现实模拟器](using-the-windows-mixed-reality-simulator.md)。 在这些情况下，只需部署，并在本地计算机上运行你的应用。
1. 选择**x86**或**x64**生成应用的配置
2. 选择**本地计算机**部署目标下拉列表菜单中
3. 选择**调试 > 启动调试**来部署应用，并开始调试

## <a name="pairing-your-device---hololens-1st-gen"></a>配对设备-HoloLens （第 1 代）

首次部署到你 HoloLens，应用程序从 Visual Studio 系统会提示输入 PIN。 在 HoloLens 上生成通过启动设置应用的 PIN，请转到**更新 > 适用于开发人员**上点击**对**。 PIN 将显示在你 HoloLens;在 Visual Studio 中，键入此 PIN。 配对完毕后，点击**完成**关闭该对话框在 HoloLens 上。 这台电脑与 HoloLens 现在成对出现，您将能够将应用自动部署。 每个后续的 PC 的使用将应用部署到你 HoloLens 重复这些步骤。

取消对它已与，成对出现的所有计算机从你 HoloLens 启动**设置**应用程序中，转到**更新 > 适用于开发人员**上点击**清除**。

## <a name="deploying-an-app-to-the-hololens-1st-gen-emulator"></a>将应用部署到 HoloLens （第 1 代） 仿真程序
1. 请确保你拥有**[安装了 HoloLens Emulator](install-the-tools.md)**。
2. 选择**x86**生成应用的配置。
![x86 生成 Visual Studio 中的配置](images/x86setting.png)
3. 选择**HoloLens 模拟器**中的部署目标下拉列表菜单![模拟器在 Visual Studio 中的目标](images/deployemulator.png)
4. 选择**调试 > 启动调试**以将应用部署并开始调试![启动而无需 Visual Studio 中调试](images/deploynodebugging.png)

## <a name="graphics-debugger"></a>图形调试器

Visual Studio 图形诊断工具是非常有帮助时编写和优化全息版的应用程序。 请参阅[MSDN 上的 Visual Studio 图形诊断](https://msdn.microsoft.com/library/hh315751.aspx)有关完整详细信息。

**若要启动的图形调试器**
1. 按照上述说明针对某个设备或仿真程序
2. 转到**调试 > 图形 > 启动诊断**
3. 第一次使用 HoloLens，执行此操作可能会收到"拒绝访问"错误。 重新启动你 HoloLens 以允许更新的权限，才会生效，然后重试。

## <a name="profiling"></a>分析

Visual Studio 分析工具可以分析应用的性能和资源使用。 这包括优化 CPU、 内存、 图形和网络使用的工具。 请参阅[而不进行调试 MSDN 上运行诊断工具](https://msdn.microsoft.com/library/dn957936.aspx)有关完整详细信息。

**若要使用 HoloLens 启动分析工具**
1. 按照上述说明针对某个设备或仿真程序
2. 转到**调试 > 启动但不调试的诊断工具...**
3. 选择你想要使用的工具
4. 单击**开始**
5. 第一次使用 HoloLens，执行此操作可能会收到"拒绝访问"错误。 重新启动你 HoloLens 以允许更新的权限，才会生效，然后重试。

## <a name="debugging-an-installed-or-running-app"></a>调试已安装或正在运行的应用程序

可以使用 Visual Studio 进行调试而不从 Visual Studio 项目部署安装的通用 Windows 应用。 如果你想要调试已安装的应用包，或如果你想要调试的应用程序已在运行，这非常有用。
1. 转到**调试-> 其他调试目标-> 调试安装的应用包**
2. 选择**远程计算机**HoloLens 的目标或**本地计算机**的沉浸式耳机。
3. 输入你的设备的**IP 地址**
4. 选择**通用**身份验证模式
5. 该窗口显示正在运行和非活动应用程序。 选取一个你想要调试。
6. 选择要调试 （托管、 本机、 混合） 的代码类型
7. 单击**附加**或**开始**

## <a name="see-also"></a>请参阅
* [安装工具](install-the-tools.md)
* [使用 HoloLens 仿真器](using-the-hololens-emulator.md)
* [部署和调试通用 Windows 平台 (UWP) 应用](https://msdn.microsoft.com/library/windows/apps/xaml/mt613243.aspx)
* [启用设备进行开发](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
