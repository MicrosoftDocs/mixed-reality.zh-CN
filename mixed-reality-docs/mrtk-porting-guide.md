---
title: 让您的应用程序准备好使用 HoloLens 2
description: 面向开发人员在 HoloLens 上已有一个应用 （第 1 代） 和/或较旧 MRTK，并查找移植到 MRTK 版本 2 和 HoloLens 2。
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality 测试，MRTK、 MRTK 版本 2、 HoloLens 2
ms.openlocfilehash: 98fde1a597bcc20b14037176748258d35ef99ab9
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730870"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>让您现有的应用程序准备好使用 HoloLens 2

本指南专门用于帮助开发人员的 HoloLens 具有现有的 Unity 应用程序 （第 1 代） 端口他们新的 HoloLens 2 设备的应用程序。 有四个关键步骤移植 HoloLens （第 1 代） 到 HoloLens 2 Unity 应用程序。 以下各节将详细介绍每个阶段的信息。 

| 步骤 1 | 步骤 2 | 步骤 3 | 步骤 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio 徽标](images/visualstudio_logo.png) | ![Unity 徽标](images/unity_logo.png)| ![Unity 图标](images/hololens2_icon.jpg) | ![MRTK 徽标](images/MRTKIcon.jpg) |
| 下载最新的工具 | 更新 Unity 项目 | 针对 ARM 编译 | 将迁移到 MRTK v2

它是**强烈建议**，才能开始迁移过程，开发人员利用源代码管理，以保存自己的应用程序的原始状态的快照。 此外，建议向*保存*在过程中的不同位置的检查点状态。 它可以是非常有益的原始应用程序以在端口过程中用于通过并行比较的另一个 Unity 实例。 

> [!NOTE]
> 移植之前，请确保已安装用于 Windows Mixed Reality 开发最新工具。 对于大多数现有的 HoloLens 开发人员，这将主要涉及更新到最新的 Visual Studio 2017 并安装相应的 Windows SDK。 深入了解以下内容将进一步深入到不同的 Unity 版本和混合现实工具包版本 2。
>
> 有关详细信息，请参阅[安装的工具](install-the-tools.md)。

## <a name="migrate-project-to-latest-version-of-unity"></a>将项目迁移到最新版本的 Unity

如果使用 MRTK v2，Unity 2018 LTS 将不进行任何重大更改或 MRTK Unity 中的最佳的长期支持路径。  建议的 Unity 生成，每个上述"安装工具"是 Unity 2018.3，将成为 Unity 2018 的 LTS 版本。  此外，MRTK v2 将始终保证对 Unity 2018 LTS 的支持，但不是一定能保证每次迭代 Unity 支持 2019.x。 

若要帮助阐明 Unity 之间其他差异 2018.3.x 或 Unity 2019.1.x，下面的轮廓的权衡这两个版本之间的基数能够编译中 Unity 2019 ARM64 二者的主要区别。 

开发人员应评估任何[插件依赖项](https://docs.unity3d.com/Manual/Plugins.html)，当前在其项目和是否可以针对 ARM64 生成这些 Dll 中存在。 如果不能为 ARM64 生成硬依赖项插件，其中一个将需要利用 Unity 2018 LTS。


| Unity 2018.3.x | Unity 2019.1 + |
|----------|-------------------|
| ARM32 生成支持 | ARM32 和 ARM64 生成支持 |
| 稳定 LTS 生成版本 | Beta 稳定性 |
| [脚本编写的.NET 后端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)*不推荐使用* | [脚本编写的.NET 后端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)*删除* |
| UNET 网络*不推荐使用* | UNET 网络*删除* |

## <a name="update-sceneproject-settings-in-unity"></a>更新 Unity 中的场景/项目设置

更新了对 Unity 之后 2018.3.x 或 Unity 2019 + 中，建议更新在 Unity 中的设备上获得最佳结果的特定设置。 这些设置下的详细信息中所述**[推荐设置为 Unity](Recommended-settings-for-Unity.md)**。

应重新进行循环访问的[.NET 脚本的后端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)在 Unity 2018 中弃用并*删除*中 Unity 2019，因此，开发人员应考虑其项目切换到[IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。 

> [!NOTE]
> IL2CPP 脚本编写后端可以到 Visual Studio 从 Unity 导致生成时间较长，因此开发人员应设置为其开发人员计算机[优化 IL2CPP 生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)。

之后在迁移到更新的 Unity 版本后寻址任何重大更改，开发人员应生成和测试在 HoloLens 上的其当前应用程序 （第 1 代）。 此外，这是很好的点来创建和保存源代码管理的提交。 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>编译为 ARM 处理器的依赖项/插件

HoloLens （第 1 代） 在 x86 上执行应用程序时新 HoloLens 2 设备利用 ARM 处理器的处理器。 因此，现有的应用程序需要通过移植以支持 ARM。 如前文所述，Unity 2018 支持 Unity 2019 + 支持 ARM64 应用的编译时 ARM32 应用的编译。 用于 ARM64 的应用程序开发是通常首选，因为性能存在重大差异。 但是，这需要所有[插件依赖项](https://docs.unity3d.com/Manual/Plugins.html)还生成用于 ARM64。 

当前查看应用程序中的所有 DLL 依赖项。 如果不再需要依赖项，则最好从项目中删除它。 为所需的剩余插件，向你的 Unity 项目中引入各自 ARM32 或 ARM64 二进制文件。 

之后引入相关的 Dll 中的 Unity 生成的 Visual Studio 解决方案，然后编译 Visual Studio 来测试可以针对 ARM 处理器生成你的应用程序中的 ARM AppX。 它建议将保存在源代码管理解决方案中的提交此另一个点。 

## <a name="update-to-mrtk-version-2"></a>更新到 MRTK 版本 2

MRTK 版本 2 是基于 Unity 支持这两个 HoloLens 的新工具包 （第 1 代） 和 HoloLens 2 和其中的所有新的 HoloLens 2 功能已添加，如将交互，并眼睛跟踪。

### <a name="prepare-for-the-migration"></a>为迁移准备

之前引入的新[*.unitypackage 文件 MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)，建议清点**MRTK v1 与集成，1） 任何自定义生成代码**和**2） 任何自定义生成代码为输入的交互或 UX 组件**。 最常见和流行，以致 Mixed Reality 开发人员引入新 MRTK v2 冲突将涉及输入和交互。 因此，建议在开始阅读和理解[MRTK v2 输入的模型](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)。

最后，新 MRTK v2 已从脚本和场景中管理器对象模型转换到的配置和服务提供程序体系结构。 这将导致更简洁的场景层次结构和体系结构模型，但对于了解新的配置文件需要一个学习曲线。 因此，请阅读[混合现实工具包配置指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)以开始熟悉重要的设置和配置文件，以适应你的应用程序的需求。 

### <a name="perform-the-migration"></a>执行迁移

导入后 MRTK v2，Unity 项目将可能有许多与编译器相关的错误。 这通常是由于新命名空间的结构和新组件名称。 继续通过修改你对新的命名空间和组件的脚本来纠正这些错误。 

HTK/MRTK 和 MRTK 版本 2 之间的特定 API 差异的详细信息，请参阅迁移指南上[MRTK 版本 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)。

### <a name="best-practices"></a>最佳做法

- 更喜欢使用 MRTK 标准着色器
- 上一个重大工作一次更改类型 (例如：到 IMixedRealityFocusHandler IFocusable)
- 每次更改后测试并使用源代码管理
- 使用默认的 MRTK UX （按钮、 平板电脑等） 在可能的情况
- 尝试避免直接修改 MRTK 文件，请改为创建包装 MRTK 组件
    - 这将防止将来 MRTK ingestions 和更新
- 查看和探索 MRTK 中提供的示例场景 (尤其是*HandInteractionExamples.scene*)
- 而是重新生成基于画布的 UI 与四边形、 碰撞体和 TextMeshPro 文本

### <a name="testing-your-application"></a>测试应用程序

现在，MRTK 版本 2 中提供了 HoloLens 2 组件和功能在[RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1)，可以模拟直接在 Unity 中，手动交互，并针对用于手动交互和的眼跟踪的新 Api 进行开发。  HoloLens 2 设备需要创建更完美的体验，但至少一个可以开始学习工具和文档中。 此外，MRTK v2 支持在 HoloLens 上开发 （第 1 代） 和传统输入因此，模型如通过敲击选择仍在 HoloLens 上测试 （第 1 代） 设备。 

## <a name="updating-interaction-model-for-hololens-2"></a>HoloLens 2 更新交互模型

在应用程序移植并准备好 HoloLens 2 后，你现可考虑更新您的交互模型和全息图设计/的位置。
来自 HoloLens （第 1 代），应用可能具有的视线移动并提交交互模型，与全息相对较远而无法放入视图的字段。

若要更新您的应用程序设计为最适合 HoloLens 2 的步骤：
1.  MRTK 组件：每个预工作，如果添加 MRTK v2，有各种组件/利用的脚本已进行了设计和优化 HoloLens 2。

2.  交互模型：请考虑更新您的交互模型。  大多数情况下，我们建议从注视切换并提交到手中。  使用你通常要超出手臂达到的全息，切换到手将导致最交互指针大气并获取手势。
注意： 在无需手动交互模型是必需的如任务工作线程持有工具，并且没有这种情况下的特定设计指南的情况下。 

3.  全息图放置：后切换到手交互模型，请考虑更接近移动某些全息与用手，使用附近交互随取即行手势全息直接交互。  全息建议更接近直接获取，或进行交互的类型是较小的目标菜单、 控件、 按钮和较小全息适合 HoloLens 2 视图的字段时捕获并检查全息图。
<br>
每个应用程序和方案都不同，并且我们将继续进行优化和发布帖子设计指南的反馈基础并继续了解的情况。


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>从应用程序从 x86 移动到 ARM 的更多知识

- 可以生成一个 ARM appx 捆绑包，也可以直接向设备部署并运行它，直接 Unity 应用非常简单。
Unity 应用程序使用本机插件时，面临的挑战。  所有本机插件需要升级到 VS2017 和重新生成对于 ARM，以及 Unity 2019，ARM64。

- 一个应用，用于 Unity，AudioKinetic Wwise 插件，所使用的版本没有 UWP ARM 插件。 花费几天时间才能重新使用应用程序用于 ARM 的声音。

- 在其他情况下，UWP/ARM 插件可能不存在的应用程序所需的插件、 端口和 HoloLens 2 上运行的能力造成了阻碍。  可能需要插件提供商合作，以取消阻止，支持 ARM。

- 在着色器 minfloat （和变量，例如 min16float、 minint、 等） 的行为可能有所不同 HoloLen 2 比在 HoloLens 上 （第 1 代）。 具体而言，这些保证"至少指定将使用比特数"。 Intel/Nvidia Gpu 上这些很大程度上就被视为 32 位。 在 ARM，实际上遵循指定的位数。 这意味着，在实践中，这些数字可能具有较少精度/范围 HoloLens 2 上与在 HoloLens 上 （第 1 代）。

- _Asm 说明不会显示用于 ARM，这意味着使用 _asm 说明的任何代码必须重写。

- ARM 不支持 SIMD 指令集。 这意味着各种标头，例如 xmmintrin.h、 emmintrin.h、 tmmintrin.h 和 immintrin.h 不是在 ARM 上可用。

- 着色器编译器在 ARM 运行时期间的第一个绘图调用后的着色器已加载或着色器的内容依赖于已更改，不是在着色器加载时间。 对帧速率的影响可以是非常明显，具体取决于多少着色器需要进行编译。 这有不同的含义的着色器应如何处理/打包/更新以不同的方式上 HoloLens 2 vs HoloLens （第 1 代）。

## <a name="see-also"></a>请参阅
* [开始使用 MRTK 版本 2](mrtk-getting-started.md)
* [MRTK 版本 2 操作方法](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [安装工具](install-the-tools.md)
* [建议用于 Unity 的设置](recommended-settings-for-unity.md)
* [混合现实的了解性能](understanding-performance-for-mixed-reality.md)

