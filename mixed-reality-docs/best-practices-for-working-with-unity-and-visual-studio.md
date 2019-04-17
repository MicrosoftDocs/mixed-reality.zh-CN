---
title: 使用 Unity 和 Visual Studio 的最佳实践
description: 提示和技巧来简化使用 Unity 和 Visual Studio 中创建混合的现实应用程序的工作流。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 部署，unity 中，visual studio 中，HoloLens，沉浸式头戴式
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592863"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>使用 Unity 和 Visual Studio 的最佳实践

使用 Unity 创建的混合的现实应用程序的开发人员将需要 Unity 和 Visual Studio 生成应用程序包部署到 HoloLens 和/或沉浸式头戴式之间进行切换。 默认情况下的 Visual Studio 的两个实例是所需 （一个修改 Unity 脚本），另一个将部署到设备和调试。 以下过程将允许使用单个 Visual Studio 实例的开发，可减少导出 Unity 项目的频率并改善了调试体验。

## <a name="improving-iteration-time"></a>提高迭代时间

常见的工作流问题在使用 Unity 和 Visual Studio 时遇到 Visual Studio 打开，并且需要不断地切换 Visual Studio 和 Unity 进行循环访问多个的窗口。
1. **Unity** -修改场景和导出 Visual Studio 解决方案
2. **Visual Studio (1)** -修改脚本
3. **Visual Studio (2)** -对于构建和部署 Unity 导出到设备的 Visual Studio 解决方案

幸运的是，是一种简化为单个实例的 Visual Studio 和 Unity 中频繁导出减少方法。

当[导出你的项目从 Unity](exporting-and-building-a-unity-visual-studio-solution.md)，检查**UnityC#项目**"文件 > 生成设置"菜单中的复选框。 现在，从 Unity 导出该项目包含所有项目的C#脚本，并且具有以下几个好处：
* 用于编写脚本和生成/部署你的项目使用 Visual Studio 的同一实例
* 仅当场景更改在 Unity 编辑器中; 从 Unity 导出更改的脚本的内容可以在 Visual Studio 中而无需重新导出。

与**UnityC#项目**已启用，就需要打开的每个程序只有一个实例：
1. **Unity** -修改场景和导出 Visual Studio 解决方案
2. **Visual Studio** -修改脚本，然后生成和部署 Unity 导出到设备的 Visual Studio 解决方案

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

下载[Visual Studio Tools for Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)

**Visual Studio Tools for Unity 的优点**
* 调试 Unity 编辑器中播放模式下从 Visual Studio 通过放置断点，评估变量和复杂表达式。
* 使用 Unity 项目资源管理器使用 Unity 显示的完全相同层次结构中查找您的脚本。
* 获取直接在 Visual Studio 的 Unity 控制台。
* 使用向导来快速创建或导航到脚本。

## <a name="expose-c-class-variables-for-easy-tuning"></a>公开C#类的简单优化变量

有两种方法来公开类变量。 执行此操作的建议的方法是将 [SerializeField] 属性添加到你的私有变量。 这使他们能够访问在编辑器中但未以编程方式公开。  另一个选项是使C#类变量以将其公开编辑器 UI 中为 public。 

这两种方法使其可以轻松地调整同时播放在编辑器的变量。 这是用于优化交互的机修工保养属性尤其有用。

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Windows SDK 或 Unity 在升级后重新生成 UWP 的 Visual Studio 解决方案

UWP 的 Visual Studio 解决方案签入到源代码管理即可升级到新的 Windows SDK 或 Unity 引擎后过期。 您可以解决此问题在升级后生成新的 UWP 解决方案从 Unity 中，然后将所有差异都合并到签入的解决方案。

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>使用文本格式资产以便进行比较的内容更改

将资产存储以文本格式，可以方便地查看 Visual Studio 中的内容更改差异。 通过更改可以启用"编辑 > 项目设置 > 编辑器"中此**资产序列化**模式设置为**强制文本，**。 但是，合并文本资产文件的更改是易出错，不建议使用，因此，考虑在源代码管理系统中启用独占二进制方式签出。
