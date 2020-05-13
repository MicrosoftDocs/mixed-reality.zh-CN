---
title: OpenXR 入门
description: 开始使用 Windows Mixed Reality 和 HoloLens 2 耳机上的便携 OpenXR API 标准版。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR，Khronos，BasicXRApp，Windows Mixed Reality OpenXR 开发人员工具，DirectX，本机，本机应用，自定义引擎，中间件，入门，101，预览版扩展，OpenXR 运行时版本，系统状态
ms.openlocfilehash: b4cf91c7a7b5bd203a4fef43c7a988d3ff1e9b16
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228044"
---
# <a name="getting-started-with-openxr"></a>OpenXR 入门

可以使用 OpenXR 在 HoloLens 2 或 Windows Mixed Reality 上的 Windows Mixed 耳机上进行开发。  如果你无权访问耳机，则可以改用 HoloLens 2 模拟器或 Windows Mixed Reality 模拟器。

## <a name="getting-started-with-openxr-for-hololens-2"></a>针对 HoloLens 2 的 OpenXR 入门

开始开发适用于 HoloLens 2 的 OpenXR 应用程序：

1. 设置 HoloLens 2 或按照说明[安装最新版本的 hololens 2 模拟器](using-the-hololens-emulator.md)。  如果你的设备最近更新了其 OS，或者你使用的是最新的仿真程序映像，则应该已准备好 OpenXR 1.0。
1. 若要确保已获得最新的 OpenXR 运行时并提供所有[扩展](openxr.md#roadmap)，请在设备或模拟器中启动**应用商店**应用，打开右上方的菜单，单击 "**下载和更新**"，然后单击 "**获取更新**"。  这可确保 HoloLens 上的 OpenXR 运行时是最新的。  请注意，如果使用的是模拟器，则每次启动时都会重置模拟器映像，因此最好的做法是确保使用[最新版本的 HoloLens 2 模拟器映像](using-the-hololens-emulator.md)。

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>OpenXR for Windows Mixed Reality 耳机入门

开始为沉浸式 Windows Mixed Reality 耳机开发 OpenXR 应用程序：

1. 请确保至少运行 Windows 10 2019 更新（1903），这是 Windows Mixed Reality 最终用户运行 OpenXR 应用程序的最低要求。  如果你使用的是早期版本的 Windows 10，则可以使用<a href="https://www.microsoft.com/software-download/windows10" target="_blank">windows 10 更新助手</a>进行升级。
2. 设置 Windows Mixed Reality 耳机，或按照说明[启用 Windows Mixed reality 模拟器](using-the-windows-mixed-reality-simulator.md)。  设置 Windows Mixed Reality 时，混合现实门户会自动安装 Windows Mixed Reality OpenXR 运行时。  然后，Microsoft Store 会使运行时保持最新状态。
3. 通过从 "开始" 菜单启动混合现实门户，并单击 .。。菜单，然后选择 "设置 OpenXR"。<br>
![在混合现实门户中设置 OpenXR](images/mixed-reality-portal-set-up-openxr.png)

如果需要让 Windows Mixed Reality OpenXR 运行时再次激活，请重复步骤3。

> [!NOTE]
> 对于所有 Windows Mixed Reality 最终用户，Windows Mixed Reality OpenXR 运行时即将自动变为活动状态。

## <a name="getting-the-windows-mixed-reality-openxr-developer-tools"></a>获取 Windows Mixed Reality OpenXR 开发人员工具

若要尝试 Windows Mixed Reality OpenXR 运行时，可以安装<a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">混合现实 OpenXR 开发人员工具应用</a>。  此应用程序提供了演示 OpenXR 的各种功能的演示场景，同时提供了一个系统状态页，其中提供了有关活动运行时和当前耳机的关键信息。

如果使用模拟器，安装混合现实 OpenXR 开发人员工具的最简单方法是使用[Windows 设备门户](using-the-windows-device-portal.md)，通过导航到 "OpenXR" 页，然后单击 "开发人员功能" 下的 "安装" 按钮。 （这也适用于物理 HoloLens 2 设备）

![混合现实 OpenXR 开发人员工具应用](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>生成示例 OpenXR 应用

如果尚未安装，请务必安装 OpenXR 开发所需[的工具](install-the-tools.md)。

<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>项目演示了一个简单的 OpenXR 示例，其中包含两个 Visual Studio 项目文件，一个用于 Win32 桌面应用，另一个用于 UWP HoloLens 2 应用。  由于解决方案包含一个 HoloLens UWP 项目，因此需要在 Visual Studio 中安装[通用 Windows 平台开发工作负载](install-the-tools.md#installation-checklist)才能完全打开它。

请注意，虽然 Win32 和 UWP 项目文件是独立的，但由于打包和部署的不同，每个项目中的应用代码都是100%。

生成 OpenXR 的 Win32 桌面后。EXE，无论是 Windows Mixed Reality 耳机还是任何其他耳机，都可以在任何支持 OpenXR 的 desktop VR 平台上将它与 VR 耳机一起使用。

生成 OpenXR UWP 应用包后，可以将[该包部署](using-visual-studio.md)到 hololens 2 设备或 Hololens 2 仿真器。

## <a name="integrate-the-openxr-loader-into-a-project"></a>将 OpenXR 加载程序集成到项目中

若要开始在现有项目中使用 OpenXR，你将包含 OpenXR 加载程序。  加载程序在设备上发现活动的 OpenXR 运行时，并提供对它实现的核心函数和扩展函数的访问权限。

你可以从 Visual Studio 项目中[引用官方 OpenXR NuGet 包](#reference-official-openxr-nuget-package)，也可以包括 Khronos GitHub 存储库中[的官方 OpenXR 加载器源](#include-official-openxr-loader-source)。  这两种方法都可让你访问 OpenXR 1.0 核心功能，以及发布 `KHR` `EXT` 和 `MSFT` 扩展。

如果你有兴趣试用 `MSFT_preview` 扩展，可以在混合现实 GitHub 存储库[中复制预览版 OpenXR 标头](#using-preview-extensions)。

### <a name="reference-official-openxr-nuget-package"></a>引用官方 OpenXR NuGet 包

<a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR** NuGet 包</a>是引用预生成的 OpenXR 加载程序的最简单方法。在 Visual Studio c + + 解决方案中。  这样，你就可以访问 OpenXR 1.0 核心功能，还可以 `KHR` 发布 `EXT` 和 `MSFT` 扩展。

将 OpenXR NuGet 包引用添加到你的 Visual Studio c + + 解决方案：
1. 在**解决方案资源管理器**中，右键单击将使用 OpenXR 的项目，然后选择 "**管理 NuGet 包 ...**"。
1. 切换到 "**浏览**" 选项卡并搜索**OpenXR**。
1. 选择**OpenXR**包，然后在右侧的详细信息窗格中单击 "安装"。
1. 单击 "确定" 以接受对项目所做的更改。
1. 添加 `#include <openxr/openxr.h>` 到源文件，开始使用 OPENXR API。

若要查看 OpenXR API 的运行示例，请查看<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>示例应用。

### <a name="include-official-openxr-loader-source"></a>包括官方 OpenXR 加载程序源

如果你想要自己生成加载程序，例如，避免出现额外的加载程序。DLL，则可以将官方 Khronos OpenXR 加载器源提取到项目中。  这样，你就可以访问 OpenXR 1.0 核心功能，还可以 `KHR` 发布 `EXT` 和 `MSFT` 扩展。

若要开始操作，请按照<a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">GitHub 上的 Khronos OpenXR-SDK</a>存储库中的说明进行操作。  项目设置为使用 CMake 进行生成-如果使用的是 MSBuild，则需要将代码复制到自己的项目中。

## <a name="using-preview-extensions"></a>使用预览扩展

`MSFT_preview`[扩展路线图](openxr.md#roadmap)中列出的扩展是为了收集反馈而预览的实验性供应商扩展。  这些扩展仅适用于开发人员设备，并将在真正的扩展交付时删除。

如果你有兴趣试用可用 `MSFT_preview` 扩展，请执行以下步骤来更新你的项目：
1. 按照上述任一方法将 OpenXR 加载程序集成到项目中。
1. 将项目中的标准 OpenXR 标头替换为<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">GitHub 上混合现实 OpenXR 存储库的预览标头</a>。

然后在目标 HoloLens 2 或台式计算机上激活预览版扩展支持：
  1. 若要确保已获得最新的 OpenXR 运行时并提供所有[扩展](openxr.md#roadmap)，请从目标设备或模拟器中启动**应用商店**应用，打开右上方的菜单，单击 "**下载和更新**"，然后单击 "**获取更新**"。
  1. 在目标设备上启用 Windows 设备门户：
     * 如果目标设备是 HoloLens 2 设备，请按照目标设备上的[说明进行操作](using-the-windows-device-portal.md)。  请注意，这需要物理耳机，因为 HoloLens 2 模拟器中的已知问题将阻止下一步中的 UI 出现在模拟器中。
     * 如果目标设备是连接了沉浸式耳机外设的台式计算机，请<a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop#set-up-device-portal-on-windows-desktop" target="_blank">按照</a>目标台式计算机上的说明进行操作。
  1. 导航到左侧窗格中的 " **OpenXR** " 选项卡，并启用 "**使用最新预览版 OpenXR 运行时**"。  这将在你的设备上启用预览版扩展，并激活预览扩展。
  1. 确认[Windows Mixed Reality OpenXR 开发人员工具](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools)的 "**系统状态**" 选项卡上显示的**运行时版本**现在与计划尝试的预览扩展插件所需的版本相匹配。  如果是这样，则应在 "**扩展**" 列表中看到该扩展。  请注意，稳定扩展可用后，将删除其预览扩展。<br />
     ![混合现实 OpenXR 开发人员工具应用系统状态选项卡](images/mixed-reality-openxr-developer-tools-status.png)

请参阅<a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">混合现实 OpenXR</a>存储库，以了解这些预览版扩展的文档以及如何使用它们的示例。

## <a name="troubleshooting"></a>疑难解答

如果在使用 OpenXR 开发时遇到问题，请查看[故障排除提示](openxr-troubleshooting.md)。