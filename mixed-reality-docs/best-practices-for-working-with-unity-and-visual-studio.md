---
title: 使用 Unity 和 Visual Studio 的最佳实践
description: 用于简化使用 Unity 和 Visual Studio 创建混合现实应用程序的工作流的提示和技巧。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 部署, unity, visual studio, HoloLens, HoloLens 2, 沉浸式耳机
ms.openlocfilehash: b2c345a8cc9bddcbc447531eb5f6cdacc62f2e98
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522319"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>使用 Unity 和 Visual Studio 的最佳实践

使用 Unity 创建混合现实应用程序的开发人员需要在 Unity 和 Visual Studio 之间进行切换, 以生成部署到 HoloLens 和/或沉浸式耳机的应用程序包。 默认情况下, 需要 Visual Studio 的两个实例 (一个用于修改 Unity 脚本, 另一个用于部署到设备和调试)。 以下过程允许使用单个 Visual Studio 实例进行开发, 降低导出 Unity 项目的频率, 并改善调试体验。

## <a name="improving-iteration-time"></a>提高迭代时间

Unity 中的 .NET 脚本编写后端支持在 Unity 2018 中被弃用, 并且在 Unity 2019 + 中被删除。 因此, 建议切换到[IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。 但是, 这可能会导致从 Unity 到 Visual Studio 的生成时间变长。 为了提高迭代速度, 应设置其环境以获得最佳的编译结果。

1) 每次将项目生成到同一个目录, 以便在其中重复使用预先生成的文件, 从而利用增量生成
2) 禁用项目 & 生成文件夹的反恶意软件扫描
   - 在 Windows 10 设置应用下打开**病毒 & 威胁防护**
   - 选择 "安全 **& 威胁防护设置**" 下的 "**管理设置**"
   - 选择 "**排除**" 部分下的 "**添加或删除排除**项"
   - 单击 "**添加排除**", 然后选择包含 Unity 项目代码和生成输出的文件夹
3) 使用 SSD 进行生成

有关详细信息, 请阅读[IL2CPP 优化生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)。 此外, 请[在 IL2CPP 脚本后端上读取调试](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html)。

此外, 请考虑安装[ *UnityScriptAnalyzer* Visual Studio 扩展](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)。 此工具会分析你C#的 Unity 脚本, 以获取能够以更优化的方式编写的代码。

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

下载[Visual Studio Tools for Unity](https://docs.microsoft.com/en-us/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)

**Visual Studio Tools for Unity 的优点**
* 通过放置断点、计算变量和复杂表达式, 从 Visual Studio 调试 Unity 编辑器播放模式。
* 使用 Unity 项目资源管理器查找脚本, 该脚本具有 Unity 显示的完全相同的层次结构。
* 直接在 Visual Studio 中获取 Unity 控制台。
* 使用向导快速创建或导航到脚本。

## <a name="expose-c-class-variables-for-easy-tuning"></a>公开C#类变量以便轻松优化

可以通过两种方式公开类变量。 为此, 建议将 [SerializeField] 特性添加到专用变量。 这样, 便可以从编辑器访问这些方法, 但不能以编程方式公开。  另一种方法是使C#类变量公开, 以便在编辑器 UI 中公开它们。 

在编辑器中播放时, 这两种方法都可以轻松地调整变量。 这对于优化交互 mechanic 属性特别有用。

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Windows SDK 或 Unity 升级后重新生成 UWP Visual Studio 解决方案

签入到源代码管理中的 UWP Visual Studio 解决方案可以在升级到新的 Windows SDK 或 Unity 引擎之后过期。 可以在升级后通过从 Unity 构建新的 UWP 解决方案, 然后将任何差异合并到签入的解决方案中来解决此问题。

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>使用文本格式资产以便于比较内容更改

以文本格式存储资产使你可以更轻松地在 Visual Studio 中查看内容更改差异。 您可以通过更改**资产序列化**模式来**强制文本**, 在 "编辑 > 项目设置 > 编辑器" 中启用此项。 但是, 合并文本资产文件更改很容易出错, 不建议这样做, 因此请考虑在源代码管理系统中启用独占二进制文件签出。

## <a name="see-also"></a>请参阅
- [Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [优化 IL2CPP 的生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer*Visual Studio 扩展](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)