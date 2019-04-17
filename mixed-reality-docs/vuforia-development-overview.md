---
title: 使用 Unity 使用 Vuforia
description: 利用 Vuforia 构建在 Unity 中的 Windows Mixed Reality 应用程序。
author: ChimeraScorn
ms.author: cwhite
ms.date: 03/21/2018
ms.topic: article
keywords: Vuforia，标记、 坐标、 参考框架跟踪
ms.openlocfilehash: 43a74989b931fee898af0aeae9e240303b2eef01
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/12/2019
ms.locfileid: "59592630"
---
# <a name="using-vuforia-engine-with-unity"></a>使用 Unity 使用 Vuforia 引擎

Vuforia 引擎到 HoloLens 可以让一个重要功能 – 能够连接 AR 体验添加到特定的映像和在环境中的对象。 此功能可用于覆盖引导式的分步说明，工业企业个机制之上或向物理产品或游戏中添加数字功能和体验。 

对于更大的灵活性开发 AR 遇到时 Vuforia 引擎提供了广泛的特征和目标。 我们最新功能，Vuforia 模型目标之一是商业和工业使用一项关键能力。 模型目标，应用程序来识别物理对象，例如计算机、 汽车或玩具和跟踪这些基于 CAD 或数字的三维模型。 有关工业用法，此功能可以提供程序集辅助角色和服务技术人员与 AR 工作的说明和工厂中的过程指导或 out 字段中。 

在 HoloLens 上运行的 Unity 中可以轻松地配置现有 Vuforia 引擎生成的应用程序适用于手机和平板电脑。 您甚至可以使用 Vuforia 引擎以使新 HoloLens 应用上升到如 Surface Pro 4 和 Surface Book 的 Windows 10 平板电脑。

## <a name="get-the-tools"></a>获取工具

[安装推荐的版本](install-the-tools.md)的 Visual Studio 和 Unity，然后配置 Unity 使用 Visual Studio 和首选的 IDE 和编译器。 

在安装 Unity 时，请务必安装"Windows 应用商店.NET 脚本编写后端"或"Windows 应用商店 IL2CPP 脚本编写后端"。 此外，请确保选择"Vuforia 增强现实支持"若要启用在 Unity 中 Vuforia 引擎。


## <a name="getting-started-with-vuforia-engine"></a>Vuforia 引擎入门

由于 Vuforia 引擎集成到 Unity 中，因此开发人员无需下载或安装任何额外的工具。 建议使用的版本是 unity 的目前在 2017.3，包含 Vuforia 引擎 7.0.57 的 LTS 流。 学习有关使用和 HoloLens Vuforia 引擎使用的效果最佳起始点[Vuforia 引擎 HoloLens 示例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)（Unity 资产商店中提供）。 此示例提供了完整的 HoloLens 项目包括预配置可以部署到 HoloLens 的场景。

在后台显示如何使用 Vuforia 映像目标来识别图像并针对它讨论了 HoloLens 体验中的数字内容。 使用 Unity 和 Vuforia 的较新版本的开发人员有权访问更新的示例包括 HoloLens 上显示的模型目标使用情况的场景。 您可以轻松地替换中在后台，尝试将其与 HoloLens 应用使用 Vuforia 引擎创建您自己的内容。


## <a name="configuring-a-vuforia-app-for-hololens"></a>配置用于 HoloLens 的 Vuforia 应用程序

对于 HoloLens 开发 Vuforia 引擎应用程序是从根本上与开发 Vuforia 引擎的其他设备的应用程序相同。 然后可以应用的生成设置和配置下面的部分中所述。 这就是启用对使用 HoloLens 空间映射和位置跟踪系统 Vuforia 引擎所需的一切。

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>生成并运行 HoloLens Vuforia 引擎示例
1.  下载[HoloLens 的 Vuforia 引擎示例](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553)从 Unity 资产商店
2.  将应用[建议能力和性能的 Unity 引擎选项](performance-recommendations-for-unity.md)
3.  将示例场景添加到生成中的场景。
4.  在文件中的"通用 Windows 平台"设置你的平台生成目标 > 生成设置。
5.  选择以下平台生成配置设置： 
   * 针对设备 = HoloLens
   * 生成类型 = D3D
   * SDK = 最新安装
   * Visual Studio 版本 = 最新安装
   * 生成并运行在 = 本地计算机
6.  定义的唯一**产品名称**，在**播放器设置**，作为在 HoloLens 上安装时应用的名称。
7.  检查**Vuforia 增强现实**并**支持的虚拟现实**中**播放器设置 > XR 设置**
8.  此外，在**XR 设置**，请确保"Windows Mixed Reality"添加到**虚拟现实 Sdk**列表
9.  检查在播放机设置中的以下功能 > 发布设置 
   * InternetClient
   * 网络摄像头
   * SpatialPerception-如果你想要使用面观察者 API
10. 选择要生成的 Visual Studio 项目生成
11. 从 Visual Studio 生成可执行文件并将其安装在 HoloLens 上

注意：从版本 7.2、 HoloLens Vuforia 引擎示例包括包括模型目标的示例用法的示例场景

## <a name="the-vuforia-developer-portal"></a>Vuforia 开发人员门户

开发人员希望创建自己 AR 遇到与 Vuforia 引擎，且我们 Vuforia 开发人员门户上应注册 HoloLens [developer.vuforia.com](https://developer.vuforia.com/)。 在门户中，开发人员有权访问[Vuforia 引擎论坛](https://developer.vuforia.com/forum)它们可以加入社区讨论，其中[库](https://library.vuforia.com/)与所有 Vuforia 引擎功能，以及深入文档[Vuforia 目标管理器](https://developer.vuforia.com/target-manager)用户可以在其中创建其自己的自定义目标。 开发人员还可以注册免费的开发人员许可证使用[Vuforia 许可证管理器](https://developer.vuforia.com/license-manager)。

## <a name="extended-tracking-with-vuforia"></a>使用 Vuforia 扩展的跟踪

[扩展跟踪](https://library.vuforia.com/articles/Training/Extended-Tracking)创建环境维护跟踪即使目标不再是视图中的映射。 它是 Vuforia 引擎执行的 HoloLens 的空间映射到对应。 在启用扩展的跟踪在目标上，启用该目标将传递给空间映射系统的姿势。 这样一来，目标可以存在于 Vuforia 引擎和 HoloLens 空间坐标系统，但不同时。

![Unity 设置窗口](images/vuforia-extendedtracking.png)<br>
*Unity 设置窗口*

**启用在目标上的扩展的跟踪**

Vuforia 引擎会将目标使用扩展的跟踪到 HoloLens 空间坐标系统的姿势自动转换。 这允许 HoloLens 接管跟踪，并将集成到空间映射的目标的环境并增加任何内容。 此过程发生 Vuforia 引擎和混合的现实中 Unity Api 之间，并且不需要由开发人员的任何编程-自动对其进行处理。

**下面是所发生的情况...**
1. Vuforia 的目标跟踪器识别目标
2. 然后初始化目标跟踪
3. 位置和旋转的目标被分析，以提供 HoloLens，若要使用的可靠姿势估计
4. Vuforia 将目标的姿势转换到 HoloLens 空间映射坐标空间
5. HoloLens 接管跟踪并停用 Vuforia 跟踪器

开发人员可以控制此过程中，通过禁用扩展的跟踪 TargetBehaviour 控制权返回给 Vuforia。

**注意：** 从 Vuforia 7.2 开始，扩展跟踪已无法再在每个目标的基础上。 相反，开发人员可以启用设备跟踪以便在场景中的所有目标上类似的功能。


## <a name="see-also"></a>请参阅
* [安装工具](install-the-tools.md)
* [坐标系统](coordinate-systems.md)
* [空间映射](spatial-mapping.md)
* [在 Unity 中的照相机](camera-in-unity.md)
* [导出和构建 Unity 的 Visual Studio 解决方案](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 文档：在 Unity 中的 Windows 10 开发](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia 文档：如何安装 Vuforia Unity 扩展](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia 文档：使用 Unity 中的 HoloLens 示例](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia 文档：在 Vuforia 扩展的跟踪](https://library.vuforia.com/articles/Training/Extended-Tracking)
